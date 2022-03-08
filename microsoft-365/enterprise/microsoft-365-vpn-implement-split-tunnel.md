---
title: VPN bölmeli bölme Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 3/3/2022
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- remotework
f1.keywords:
- NOCSH
description: VPN bölme bölmeleri uygulama Microsoft 365
ms.openlocfilehash: ee8c0929682370d581c9d1b5c738d682d3f91a01
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63320445"
---
# <a name="implementing-vpn-split-tunneling-for-microsoft-365"></a>VPN bölmeli bölme Microsoft 365

>[!NOTE]
>Bu makale, uzak kullanıcılar için iyileştirmeyi Microsoft 365 makale kümelerinin bir bölümüdir.

>- Uzak kullanıcılar için Microsoft 365 bağlantısını en iyi duruma getirmek için VPN bölünmüş şifreleme kullanma hakkında genel bir bakış için bkz[.](microsoft-365-vpn-split-tunnel.md) Genel Bakış: Vpn bölünmüş Microsoft 365.
>- VPN bölünmüş bölme senaryolarının ayrıntılı listesi için bkz. Daha fazla bilgi için bkz. Genel [VPN bölünmüş Microsoft 365](microsoft-365-vpn-common-scenarios.md).
>- VPN bölünmüş trafiğinde Teams trafiğinin güvenliğini sağlama kılavuzu için bkz. VPN bölünmüş trafiği için Teams trafiğinin güvenliğini [sağlama](microsoft-365-vpn-securing-teams.md).
>- VPN ortamlarında Stream ve canlı etkinlikleri yapılandırma hakkında bilgi için bkz. VPN ortamlarında akış ve canlı etkinlikler [için dikkat edilmesi gereken noktalar](microsoft-365-vpn-stream-and-live-events.md).
>- Çin'deki kullanıcılar için Microsoft 365 kiracı performansını iyileştirme hakkında bilgi için bkz. [Microsoft 365 için performans iyileştirme.](microsoft-365-networking-china.md)

Uzak çalışanın bağlantısını en iyi duruma getirme konusunda Microsoft'un önerilen stratejisi, hızlı şekilde risk azaltmaya ve birkaç basit adımla yüksek performans sağlamaya odaklanmaktadır. Bu adımlar, performans sorunu olan VPN sunucularını atlayan birkaç tanımlı uç nokta için eski VPN yaklaşımını ayarlar. Şirket ağının çıkışta tüm trafiğin güvenliğini sağlama ihtiyacını ortadan kaldırmak için eşdeğer ve hatta üstün bir güvenlik modeli farklı katmanlara uygulanabilir. Çoğu durumda, bu durum etkili bir şekilde saatler içinde elde edilebilir ve gereksinimler talep ve zaman izin verdiyse diğer iş yükleri için ölçeklendirilebilir.

## <a name="implement-vpn-split-tunneling"></a>VPN bölünmüş bilgisayar bölmeleri uygulama

Bu makalede, VPN istemci mimarinizi BIR VPN zorlamalı basamaktan birkaç güvenilen özel durumla _VPN_ zorlamalı basamaklara geçirmek için gereken basit adımları, Microsoft 365 için Ortak [VPN](microsoft-365-vpn-common-scenarios.md) bölme bölme senaryolarında VPN bölünmüş basamaklama modeli [#2](microsoft-365-vpn-common-scenarios.md#2-vpn-forced-tunnel-with-a-small-number-of-trusted-exceptions) bulabilirsiniz.

Aşağıdaki diyagramda önerilen VPN bölünmüş erişim çözümü nasıl çalışır gösterilmiştir:

![Bölünmüş VPN çözümü ayrıntısı.](../media/vpn-split-tunneling/vpn-split-tunnel-example.png)

### <a name="1-identify-the-endpoints-to-optimize"></a>1. İyileştirilen uç noktaları belirleme

Aşağıdaki Microsoft 365 [URL'ler ve IP](urls-and-ip-address-ranges.md) adresi aralıkları makalesinde, Microsoft en iyi duruma getirmek için ihtiyacınız olan önemli uç noktaları açıkça tanımlar ve bunları En İyi Duruma Getirme olarak kategorilere **ayırabilir**. Şu anda en iyi duruma getirilmiş yalnızca dört URL ve 20 IP alt ağı vardır. Bu küçük uç nokta grubu, Microsoft 365 medyası için olanlar gibi gecikmeye duyarlı uç noktalar da dahil olmak üzere Microsoft 365 hizmetine gelen trafik hacminin yaklaşık %70 - %80 Teams hesaplarıdır. Temel olarak bu, özel bir şekilde ilgilenmemiz gereken trafiktir; aynı zamanda geleneksel ağ yollarına ve VPN altyapısına inanılmaz bir baskı bırakılacak trafiktir.

Bu kategorideki URL'ler aşağıdaki özelliklere sahiptir:

- Microsoft'un sahip olduğu ve yönetilen uç noktaları Microsoft altyapısında barındırılan mı
- IP'ler sağlanıyor mu?
- Düşük değişiklik oranına sahip olması ve sayı olarak az kalması beklenir (şu anda 20 IP alt ağı)
- Bant genişliği ve/veya gecikmeye duyarlıdır
- Ağ üzerinde satır içi yerine hizmette gerekli güvenlik öğelerini sağlanıyor olabilir
- Hizmet hizmetine gelen trafik hacminin yaklaşık %70-80'i Microsoft 365 hesaba Microsoft 365

Uç noktaların nasıl Microsoft 365 kategorilere ayrılmış ve yönetilleri hakkında daha fazla bilgi için bkz. [Microsoft 365 yönetme](managing-office-365-endpoints.md).

#### <a name="optimize-urls"></a>URL'leri en iyi duruma getirme

Geçerli İyileştir URL'leri aşağıdaki tabloda bulunabilir. Çoğu durumda, uç noktaların proxy yerine doğrudan gönderilmek üzere yapılandırıldığında tarayıcı [PAC](managing-office-365-endpoints.md#use-a-pac-file-for-direct-routing-of-vital-office-365-traffic) dosyasında yalnızca URL uç noktalarını kullanasınız.

| URL'leri en iyi duruma getirme | Bağlantı Noktası/Protokol | Amaç |
| --- | --- | --- |
| <https://outlook.office365.com> | TCP 443 | Bu, Outlook sunucusuna bağlanmak için kullandığı ve yüksek bant genişliği Exchange Online ve bağlantı sayısı olan birincil URL'lerdendir. Hızlı arama, diğer posta kutusu takvimleri, serbest /meşgul araması, kuralları ve uyarıları yönetme, çevrimiçi arşivi Exchange, giden kutusu ayrılan e-postalar gibi çevrimiçi özellikler için düşük ağ gecikme süresi gerekir. |
| <https://outlook.office.com> | TCP 443 | Bu URL, Outlook sunucuya bağlanmak için Exchange Online Çevrimiçi Web Erişimi'ne Exchange Online ve ağ gecikme süresine duyarlıdır. özellikle SharePoint Online ile büyük dosya yükleme ve indirme için bağlantı gereklidir. |
| \<tenant\>https://.sharepoint.com | TCP 443 | Bu, SharePoint Online'ın birincil URL'si ve yüksek bant genişliği kullanımına sahiptir. |
| \<tenant\>https://-my.sharepoint.com | TCP 443 | Bu, E-posta eşitlemesi OneDrive İş birincil URL'dir ve yüksek bant genişliği kullanımına ve OneDrive İş sayısına sahiptir. |
| Teams IP'leri ekleyin (URL yok) | UDP 3478, 3479, 3480 ve 3481 | Geçiş Bulma ayırma ve gerçek zamanlı trafik. Bunlar, Medya trafiği (Skype Kurumsal Microsoft Teams, toplantılar vb.) için kullanılan uç noktalardır. Uç noktaların çoğu, Microsoft Teams istemci bir çağrı kurduğunda (ve hizmet için listelenen gerekli IP'ler içinde yer alır) olduğunda sağlanır. En iyi medya kalitesi için UDP protokolünün kullanımı gereklidir.   |

Yukarıdaki örneklerde, **kiracı** sizin kiracı adınızla değiştir Microsoft 365 gerekir. Örneğin, **contoso.onmicrosoft.com'i** _contoso.sharepoint.com_ _ve contoso-my.sharepoint.com_.

#### <a name="optimize-ip-address-ranges"></a>IP adresi aralıklarını en iyi duruma getirme

Bu uç noktaların karşılık gelen IP adresi aralıklarını yazma zamanında aşağıdaki gibidir. Bu örnekteki  gibi bir betik, [Microsoft 365 IP ve URL web](microsoft-365-ip-web-service.md) hizmeti veya [URL/IP](urls-and-ip-address-ranges.md) sayfası gibi bir komut dosyası kullanarak yapılandırmayı uygularken güncelleştirmeleri denetlemeniz ve bunu düzenli olarak yapmak üzere bir ilke koymanız kesinlikle önerilir.[](https://github.com/microsoft/Office365NetworkTools/tree/master/Scripts/Display%20URL-IPs-Ports%20per%20Category)

```markdown
104.146.128.0/17
13.107.128.0/22
13.107.136.0/22
13.107.18.10/31
13.107.6.152/31
13.107.64.0/18
131.253.33.215/32
132.245.0.0/16
150.171.32.0/22
150.171.40.0/22
204.79.197.215/32
23.103.160.0/20
40.104.0.0/15
40.108.128.0/17
40.96.0.0/13
52.104.0.0/14
52.112.0.0/14
52.96.0.0/14
52.120.0.0/14
```

### <a name="2-optimize-access-to-these-endpoints-via-the-vpn"></a>2. VPN aracılığıyla bu uç noktalara erişimi en iyi duruma getirme

Artık bu kritik uç noktaları belirlediklerine göre, vpn hedeflerinden yönlendirmemiz ve doğrudan hizmete bağlanmak için kullanıcının yerel İnternet bağlantısını kullanmasına izin vermemiz gerekiyor. Bu özelliğin nasıl yerine uygulanıyor olduğu, kullanılan VPN ürünü ve makine platformuna bağlı olarak değişir, ancak çoğu VPN çözümü bu mantığın uygulamaya yönelik bazı basit ilke yapılandırmasına olanak sağlar. Bilgi VPN platformuna özgü bölünmüş galeri kılavuzları için bkz. [Yaygın VPN platformları için HOWTO kılavuzları](#howto-guides-for-common-vpn-platforms).

Çözümü el ile test etmek isterseniz, aşağıdaki PowerShell örneğini çalıştırarak çözümü yönlendirme tablosu düzeyinde taklit edebilirsiniz. Bu örnek, yönlendirme tablosuna Medya IP Teams her biri için bir yol ekler. Medya Teams öncesi ve sonrası için test etmek ve belirtilen uç noktaların yönlendirmeleri arasındaki farkı gözlemlemek için kullanabilirsiniz.

#### <a name="example-add-teams-media-ip-subnets-into-the-route-table"></a>Örnek: Teams tablosuna Medya IP alt ağları ekleme

```powershell
$intIndex = "" # index of the interface connected to the internet
$gateway = "" # default gateway of that interface
$destPrefix = "52.120.0.0/14", "52.112.0.0/14", "13.107.64.0/18" # Teams Media endpoints
# Add routes to the route table
foreach ($prefix in $destPrefix) {New-NetRoute -DestinationPrefix $prefix -InterfaceIndex $intIndex -NextHop $gateway}
```

Yukarıdaki betikte, _$intIndex_ İnternet'e bağlı arabirimin dizinidir (PowerShell'de **get-netadapter** çalıştırarak bulma; _ifIndex'in_ değerini arama) ve _$gateway_ , o arabirimin varsayılan ağ geçididir (bir komut isteminde **ipconfig** çalıştırarak bulma veya **(Get-NetIPConfiguration | Foreach IPv4DefaultGateway). NextHop** in PowerShell).

Yolları eklediktan sonra, komut isteminde veya PowerShell'de yönlendirme yazdırmayı çalıştırarak yönlendirme  tablosu için doğru olduğunu onaylayın. Çıkış, arabirim dizinini (bu örnekte _22_ ) ve bu arabirimin ağ geçidini (bu örnekte _192.168.1.1_ ) gösteren, sizin ekleytİk yolları içerir:

![Yazdırma çıkışını yönlendirme.](../media/vpn-split-tunneling/vpn-route-print.png)

en iyi duruma getirme kategorisinde  tüm geçerli IP adresi aralıkları için yönlendirmeler eklemek için, aşağıdaki betik çeşitlesini kullanarak geçerli IP alt ağlarını en iyi duruma getirmek ve bunları yönlendirme tablosuna eklemek üzere [Microsoft 365 IP ve URL web](microsoft-365-ip-web-service.md) hizmetini sorgularsınız.

#### <a name="example-add-all-optimize-subnets-into-the-route-table"></a>Örnek: Tüm İyileştir alt ağlarını yönlendirme tablosuna ekleme

```powershell
$intIndex = "" # index of the interface connected to the internet
$gateway = "" # default gateway of that interface
# Query the web service for IPs in the Optimize category
$ep = Invoke-RestMethod ("https://endpoints.office.com/endpoints/worldwide?clientrequestid=" + ([GUID]::NewGuid()).Guid)
# Output only IPv4 Optimize IPs to $optimizeIps
$destPrefix = $ep | where {$_.category -eq "Optimize"} | Select-Object -ExpandProperty ips | Where-Object { $_ -like '*.*' }
# Add routes to the route table
foreach ($prefix in $destPrefix) {New-NetRoute -DestinationPrefix $prefix -InterfaceIndex $intIndex -NextHop $gateway}
```

Yanlışlıkla yanlış parametrelerle yönlendirmeler eklediyseniz veya yalnızca değişikliklerinizi geri dönmek isterseniz, az önce ekley istediğiniz yolları aşağıdaki komutla kaldırabilirsiniz:

```powershell
foreach ($prefix in $destPrefix) {Remove-NetRoute -DestinationPrefix $prefix -InterfaceIndex $intIndex -NextHop $gateway}
```

<!--- remmed until we add more reliable interface selection logic
#### Example script to add Teams Media subnets to the route table

```powershell
$adapter = get-netadapter | ? {$_.Status -eq "Up"}
$adapterIndex = $adapter.ifIndex
$gateway = (Get-NetIPConfiguration | Foreach IPv4DefaultGateway).NextHop

$destPrefix = "52.120.0.0/14", "52.112.0.0/14", "13.107.64.0/18"
foreach ($prefix in $destPrefix) {New-NetRoute -DestinationPrefix $prefix -InterfaceIndex $intIndex -NextHop $gateway}
```
-->

VPN istemcisi, En İyi DURUMA GETIRME IP'lerine giden trafiğin bu şekilde yönlendirneceği şekilde yapılandırıldı. Böylece trafik, kullanıcınıza mümkün olduğunca yakın Microsoft 365 hizmetleri ve bağlantı uç noktaları sağlayan [Azure Ön](https://azure.microsoft.com/blog/azure-front-door-service-is-now-generally-available/) Kapı gibi Microsoft 365 Hizmet Ön Kapı gibi yerel Microsoft kaynaklarını kullanmalarını sağlar. Bu, kullanıcıların dünyanın neresinde olursa olsunlar kullanıcılara yüksek performans düzeyleri sunmamıza olanak sağlar ve kullanıcılarının doğrudan çıkışını birkaç milisaniye içinde olan [Microsoft'un](https://azure.microsoft.com/blog/how-microsoft-builds-its-fast-and-reliable-global-network/) dünya sınıfı global ağına tam avantaj sağlar.

## <a name="howto-guides-for-common-vpn-platforms"></a>Yaygın VPN platformları için HOWTO kılavuzları

Bu bölümde, bu  boşluğun en yaygın ortaklarından gelen trafiğin Microsoft 365 bölmek için ayrıntılı kılavuzların bağlantıları yer almaktadır. Kullanılabilir hale geldiyken başka kılavuzlar da eklemiz.

- **Windows 10 VPN istemcisi**: [Yerel VPN Microsoft 365 çalışanlara](/windows/security/identity-protection/vpn/vpn-office-365-optimization) yönelik trafiği en iyi Windows 10 getirme
- **Cisco Anyconnect**: [Anyconnect Bölünmüş Bağlantı'Tunnel Office365 için en iyi duruma getirme](https://www.cisco.com/c/en/us/support/docs/security/anyconnect-secure-mobility-client/215343-optimize-anyconnect-split-tunnel-for-off.html)
- **Palo Alto GlobalProtect**: [VPN Bölünmüş Microsoft 365 ile Trafiği En Tunnel Rotası'nın Dışında Tut](https://live.paloaltonetworks.com/t5/Prisma-Access-Articles/GlobalProtect-Optimizing-Office-365-Traffic/ta-p/319669)
- **F5 Networks BIG-IP APM**: [BIG-IP APM kullanırken](https://devcentral.f5.com/s/articles/SSL-VPN-Split-Tunneling-and-Office-365) MICROSOFT 365 VPN'ler aracılığıyla Uzak Erişim'de trafiği en iyi duruma getirme
- **Citrix Ağ Geçidi**: [Office365 için Citrix Gateway VPN bölünmüş geçidini en iyi duruma getirme](https://docs.citrix.com/citrix-gateway/13/optimizing-citrix-gateway-vpn-split-tunnel-for-office365.html)
- **Pulse Güvenli**: [VPN Titreşimi: Bölünmüş titreşimi yapılandırarak tüm Microsoft 365 yapılandırma](https://kb.pulsesecure.net/articles/Pulse_Secure_Article/KB44417)
- **Kontrol Noktası VPN**:[Diğer SaaS Uygulamaları için Tunnel Bölünmüş Microsoft 365 yapılandırma](https://supportcenter.checkpoint.com/supportcenter/portal?eventSubmit_doGoviewsolutiondetails=&solutionid=sk167000)

## <a name="related-articles"></a>İlgili makaleler

[Genel bakış: VPN bölme bölme Microsoft 365](microsoft-365-vpn-split-tunnel.md)

[Kullanıcılar için yaygın VPN bölme bölme Microsoft 365](microsoft-365-vpn-common-scenarios.md)

[VPN bölünmüş Teams için medya trafiğinin güvenliğini sağlama](microsoft-365-vpn-securing-teams.md)

[VPN ortamlarında Stream ve canlı etkinlikler için dikkat edilmesi gereken noktalar](microsoft-365-vpn-stream-and-live-events.md)

[Microsoft 365 kullanıcıları için performans iyileştirmeyi iyileştirme](microsoft-365-networking-china.md)

[Microsoft 365 Ağ Bağlantısı İlkeleri](microsoft-365-network-connectivity-principles.md)

[Ağ Microsoft 365 değerlendirme](assessing-network-connectivity.md)

[Microsoft 365 ve performans ayarını yapılandırma](network-planning-and-performance.md)

[Günümüzün benzersiz uzaktan çalışma senaryolarında güvenlik uzmanlarının ve BT'nin modern güvenlik denetimlerini elde etmenin alternatif yolları (Microsoft Güvenlik Ekibi blogu)](https://www.microsoft.com/security/blog/2020/03/26/alternative-security-professionals-it-achieve-modern-security-controls-todays-unique-remote-work-scenarios/)

[Microsoft'ta VPN performansını geliştirme: otomatik Windows 10 izin vermek için VPN profillerini kullanma](https://www.microsoft.com/itshowcase/enhancing-remote-access-in-windows-10-with-an-automatic-vpn-profile)

[VPN ile çalışma: Microsoft uzaktan iş gücüne nasıl bağlı tutarak](https://www.microsoft.com/itshowcase/blog/running-on-vpn-how-microsoft-is-keeping-its-remote-workforce-connected/?elevate-lv)

[Microsoft genel ağı](/azure/networking/microsoft-global-network)
