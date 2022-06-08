---
title: Microsoft 365 için VPN bölünmüş tüneli uygulama
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
description: Microsoft 365 için VPN bölünmüş tüneli uygulama
ms.openlocfilehash: 6b578b9b1801921644c6982c15c160bce5fbb4dd
ms.sourcegitcommit: 61bdfa84f2d6ce0b61ba5df39dcde58df6b3b59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2022
ms.locfileid: "65941096"
---
# <a name="implementing-vpn-split-tunneling-for-microsoft-365"></a>Microsoft 365 için VPN bölünmüş tüneli uygulama

>[!NOTE]
>Bu makale, uzak kullanıcılar için Microsoft 365 iyileştirmesini ele alan bir makale kümesinin parçasıdır.

>- Uzak kullanıcılar için Microsoft 365 bağlantısını iyileştirmek üzere VPN bölünmüş tünel kullanmaya genel bakış için bkz [. Genel Bakış: Microsoft 365 için VPN bölünmüş tünel oluşturma](microsoft-365-vpn-split-tunnel.md).
>- VPN bölünmüş tünel senaryolarının ayrıntılı listesi için bkz. [Microsoft 365 için yaygın VPN bölünmüş tünel senaryoları](microsoft-365-vpn-common-scenarios.md).
>- VPN bölünmüş tünel ortamlarında Teams medya trafiğinin güvenliğini sağlama yönergeleri için bkz. [VPN bölünmüş tüneli için Teams medya trafiğinin güvenliğini sağlama](microsoft-365-vpn-securing-teams.md).
>- VPN ortamlarında Stream ve canlı etkinlikleri yapılandırma hakkında bilgi için bkz. [VPN ortamlarında Akış ve canlı etkinlikler için dikkat edilmesi gereken özel noktalar](microsoft-365-vpn-stream-and-live-events.md).
>- Çin'deki kullanıcılar için Microsoft 365 dünya çapında kiracı performansını iyileştirme hakkında bilgi için bkz. [Çin kullanıcıları için Microsoft 365 performans iyileştirmesi](microsoft-365-networking-china.md).

Microsoft'un uzak çalışanın bağlantısını iyileştirmeye yönelik önerilen stratejisi, sorunları hızla azaltmaya ve birkaç basit adımla yüksek performans sağlamaya odaklanmıştır. Bu adımlar, performans sorunu olan VPN sunucularını atlayan birkaç tanımlı uç nokta için eski VPN yaklaşımını ayarlar. Şirket ağının çıkışında tüm trafiğin güvenliğini sağlama gereksinimini ortadan kaldırmak için farklı katmanlarda eşdeğer ve hatta üstün bir güvenlik modeli uygulanabilir. Çoğu durumda, bu işlem birkaç saat içinde etkili bir şekilde gerçekleştirilebilir ve gereksinimlere ve zamana göre diğer iş yüklerine ölçeklenebilir.

## <a name="implement-vpn-split-tunneling"></a>VPN bölünmüş tüneli uygulama

Bu makalede, MICROSOFT [365 için yaygın VPN bölünmüş tünel senaryolarında](microsoft-365-vpn-common-scenarios.md) VPN [bölünmüş tünel modeli #2](microsoft-365-vpn-common-scenarios.md#2-vpn-forced-tunnel-with-a-small-number-of-trusted-exceptions) adlı _birkaç güvenilir özel durumla VPN istemci mimarinizi VPN zorlamalı tünelden VPN zorlamalı tünele_ geçirmek için gereken basit adımları bulacaksınız.

Aşağıdaki diyagramda önerilen VPN bölünmüş tünel çözümünün nasıl çalıştığı gösterilmektedir:

![Bölünmüş tünel VPN çözümü ayrıntısı.](../media/vpn-split-tunneling/vpn-split-tunnel-example.png)

### <a name="1-identify-the-endpoints-to-optimize"></a>1. İyileştirecek uç noktaları belirleme

[Microsoft 365 URL'leri ve IP adresi aralıkları](urls-and-ip-address-ranges.md) makalesinde Microsoft, iyileştirmeniz gereken anahtar uç noktaları net bir şekilde tanımlar ve **en iyi duruma getir** olarak kategorilere ayırır. Şu anda yalnızca dört URL ve 20 IP alt ağı iyileştirilmelidir. Bu küçük uç nokta grubu, Teams medyası gibi gecikme süresine duyarlı uç noktalar da dahil olmak üzere Microsoft 365 hizmetine gelen trafik hacminin yaklaşık %70-%80'ini oluşturur. Temelde bu, özel olarak ilgilenmemiz gereken trafiktir ve aynı zamanda geleneksel ağ yolları ve VPN altyapısı üzerinde inanılmaz bir baskıya neden olacak trafiktir.

Bu kategorideki URL'ler aşağıdaki özelliklere sahiptir:

- Microsoft'un sahip olduğu ve yönetilen uç noktaları, Microsoft altyapısında barındırılıyor mu?
- IP'ler sağlandı mı?
- Düşük değişiklik oranı ve sayı olarak küçük kalması beklenir (şu anda 20 IP alt ağı)
- Bant genişliği ve/veya gecikme süresine duyarlıdır
- Ağdaki satır içi öğeler yerine hizmette gerekli güvenlik öğelerinin sağlanmasına sahip olabilir
- Microsoft 365 hizmetine yönelik trafik hacminin yaklaşık %70-80'ini oluşturur

Microsoft 365 uç noktaları ve bunların nasıl kategorilere ayrılması ve yönetildiği hakkında daha fazla bilgi için bkz. [Microsoft 365 uç noktalarını yönetme](managing-office-365-endpoints.md).

#### <a name="optimize-urls"></a>URL'leri iyileştirme

Geçerli İyileştirme URL'leri aşağıdaki tabloda bulunabilir. Çoğu durumda, url uç noktalarını ara sunucu yerine yalnızca uç noktaların doğrudan gönderilecek şekilde yapılandırıldığı bir [tarayıcı PAC dosyasında](managing-office-365-endpoints.md#use-a-pac-file-for-direct-routing-of-vital-office-365-traffic) kullanmanız gerekir.

| URL'leri iyileştirme | Bağlantı Noktası/Protokol | Amaç |
| --- | --- | --- |
| <https://outlook.office365.com> | TCP 443 | Bu, Outlook'un Exchange Online sunucusuna bağlanmak için kullandığı birincil URL'lerden biridir ve yüksek hacimli bant genişliği kullanımına ve bağlantı sayısına sahiptir. Anlık arama, diğer posta kutusu takvimleri, serbest/meşgul arama, kuralları ve uyarıları yönetme, Exchange çevrimiçi arşivi, giden kutusundan ayrılan e-postalar gibi çevrimiçi özellikler için düşük ağ gecikme süresi gereklidir. |
| <https://outlook.office.com> | TCP 443 | Bu URL, Outlook Online Web Access'in Exchange Online sunucusuna bağlanması için kullanılır ve ağ gecikme süresine duyarlıdır. SharePoint Online ile büyük dosya yükleme ve indirme için özellikle bağlantı gereklidir. |
| \<tenant\>https://.sharepoint.com | TCP 443 | Bu, SharePoint Online için birincil URL'dir ve yüksek bant genişliği kullanımına sahiptir. |
| \<tenant\>https://-my.sharepoint.com | TCP 443 | Bu, OneDrive İş için birincil URL'dir ve oneDrive İş Eşitleme aracından yüksek bant genişliği kullanımına ve büyük olasılıkla yüksek bağlantı sayımına sahiptir. |
| Teams Medya IP'leri (URL yok) | UDP 3478, 3479, 3480 ve 3481 | Geçiş Bulma ayırma ve gerçek zamanlı trafik. Bunlar Skype Kurumsal ve Microsoft Teams Medya trafiği (aramalar, toplantılar vb.) için kullanılan uç noktalardır. Çoğu uç nokta, Microsoft Teams istemcisi bir çağrı oluşturduğunda sağlanır (ve hizmet için listelenen gerekli IP'lerin içinde bulunur). En iyi medya kalitesi için UDP protokolünün kullanılması gerekir.   |

Yukarıdaki örneklerde **kiracı** , Microsoft 365 kiracı adınız ile değiştirilmelidir. Örneğin **, contoso.onmicrosoft.com** _contoso.sharepoint.com_ ve _contoso-my.sharepoint.com_ kullanır.

#### <a name="optimize-ip-address-ranges"></a>IP adresi aralıklarını iyileştirme

Bu uç noktaların karşılık gelen IP adresi aralıkları yazılırken aşağıdaki gibidir. Yapılandırmayı uygularken güncelleştirmeleri denetlemek için bu örnek, [Microsoft 365 IP ve URL web hizmeti](microsoft-365-ip-web-service.md) veya [URL/IP sayfası](urls-and-ip-address-ranges.md) [gibi bir betik](https://github.com/microsoft/Office365NetworkTools/tree/master/Scripts/Display%20URL-IPs-Ports%20per%20Category) kullanmanız ve bunu düzenli olarak yapmak için bir ilke koymanız **kesinlikle** tavsiye edilir.

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

Bu kritik uç noktaları belirlediğimize göre, bunları VPN tünelinden uzaklaştırmamız ve doğrudan hizmete bağlanmak için kullanıcının yerel İnternet bağlantısını kullanmalarına izin vermemiz gerekir. Bunun nasıl gerçekleştirildiği, kullanılan VPN ürününe ve makine platformuna bağlı olarak değişir, ancak çoğu VPN çözümü ilkenin bu mantığı uygulaması için bazı basit yapılandırmalara izin verir. VPN platformuna özgü bölünmüş tünel kılavuzu hakkında bilgi için bkz. [Yaygın VPN platformları için HOWTO kılavuzları](#howto-guides-for-common-vpn-platforms).

Çözümü el ile test etmek isterseniz, aşağıdaki PowerShell örneğini yürüterek çözüme yol tablosu düzeyinde öykünebilirsiniz. Bu örnek, yönlendirme tablosuna Teams Media IP alt ağlarının her biri için bir yol ekler. Teams medya performansını önce ve sonra test edebilir ve belirtilen uç noktaların yollarındaki farkı gözlemleyebilirsiniz.

#### <a name="example-add-teams-media-ip-subnets-into-the-route-table"></a>Örnek: Yönlendirme tablosuna Teams Media IP alt ağları ekleme

```powershell
$intIndex = "" # index of the interface connected to the internet
$gateway = "" # default gateway of that interface
$destPrefix = "52.120.0.0/14", "52.112.0.0/14", "13.107.64.0/18" # Teams Media endpoints
# Add routes to the route table
foreach ($prefix in $destPrefix) {New-NetRoute -DestinationPrefix $prefix -InterfaceIndex $intIndex -NextHop $gateway}
```

Yukarıdaki betikte _$intIndex_ , İnternet'e bağlı arabirimin dizinidir (PowerShell'de **get-netadapter** çalıştırarak bul; _ifIndex_ değerini arayın) ve _$gateway_ bu arabirimin varsayılan ağ geçididir (komut isteminde **ipconfig** çalıştırarak bul veya **(Get-NetIPConfiguration | Foreach IPv4DefaultGateway).** PowerShell'de NextHop).

Yolları ekledikten sonra, komut isteminde veya PowerShell'de **route print** komutunu çalıştırarak yol tablosunun doğru olduğunu onaylayabilirsiniz. Çıkış, eklediğiniz yolları içermeli ve arabirim dizinini (bu örnekte _22_ ) ve bu arabirimin ağ geçidini (bu örnekte _192.168.1.1_ ) göstermelidir:

![Yazdırma çıkışını yönlendirme.](../media/vpn-split-tunneling/vpn-route-print.png)

İyileştir _kategorisindeki tüm_ geçerli IP adresi aralıklarına yol eklemek için, geçerli IP alt ağlarını iyileştir [kümesinin Microsoft 365 IP ve URL web hizmetini](microsoft-365-ip-web-service.md) sorgulamak ve bunları yol tablosuna eklemek için aşağıdaki betik varyasyonunu kullanabilirsiniz.

#### <a name="example-add-all-optimize-subnets-into-the-route-table"></a>Örnek: Yol tablosuna tüm Optimize alt ağlarını ekleme

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

Yanlışlıkla yanlış parametrelere sahip yollar eklediyseniz veya yalnızca değişikliklerinizi geri döndürmek istiyorsanız, aşağıdaki komutla yeni eklediğiniz yolları kaldırabilirsiniz:

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

VPN istemcisi, **Optimize** IP'lerine giden trafiğin bu şekilde yönlendirilmesi için yapılandırılmalıdır. Bu, trafiğin Microsoft 365 hizmetlerini ve bağlantı uç noktalarını kullanıcılarınıza mümkün olduğunca yakın bir şekilde sunan [Azure Front Door gibi](https://azure.microsoft.com/blog/azure-front-door-service-is-now-generally-available/) Microsoft 365 Service Front Door gibi yerel Microsoft kaynaklarını kullanmasına olanak tanır. Bu, kullanıcılara dünyanın her yerine yüksek performans düzeyleri sunmamıza olanak tanır ve microsoft'un kullanıcılarınızın doğrudan çıkışına birkaç milisaniye içinde olan [dünya standartlarında küresel ağından](https://azure.microsoft.com/blog/how-microsoft-builds-its-fast-and-reliable-global-network/) tam olarak yararlanır.

## <a name="howto-guides-for-common-vpn-platforms"></a>Yaygın VPN platformları için HOWTO kılavuzları

Bu bölümde, bu alanda en yaygın iş ortaklarından gelen Microsoft 365 trafiği için bölünmüş tünel uygulamayla ilgili ayrıntılı kılavuzların bağlantıları sağlanır. Kullanılabilir hale geldikçe ek kılavuzlar ekleyeceğiz.

- **Windows 10 VPN istemcisi**: [Yerel Windows 10 VPN istemcisi ile uzak çalışanlar için Microsoft 365 trafiğini iyileştirme](/windows/security/identity-protection/vpn/vpn-office-365-optimization)
- **Cisco Anyconnect**: [Office365 için Anyconnect Split Tunnel'ı en iyi duruma getirme](https://www.cisco.com/c/en/us/support/docs/security/anyconnect-secure-mobility-client/215343-optimize-anyconnect-split-tunnel-for-off.html)
- **Palo Alto GlobalProtect**: [VPN Split Tunnel Exclude Access Route aracılığıyla Microsoft 365 Trafiğini İyileştirme](https://live.paloaltonetworks.com/t5/Prisma-Access-Articles/GlobalProtect-Optimizing-Office-365-Traffic/ta-p/319669)
- **F5 Networks BIG-IP APM**: [BIG-IP APM kullanırken VPN'ler aracılığıyla Uzaktan Erişimde Microsoft 365 trafiğini iyileştirme](https://devcentral.f5.com/s/articles/SSL-VPN-Split-Tunneling-and-Office-365)
- **Citrix Gateway**: [Office365 için Citrix Gateway VPN bölünmüş tüneli iyileştirme](https://docs.citrix.com/en-us/citrix-gateway/current-release/optimizing-citrix-gateway-vpn-split-tunnel-for-office365.html)
- **Pulse Secure**: [VPN Tunneling: Microsoft 365 uygulamalarını dışlamak için bölünmüş tünel yapılandırma](https://kb.pulsesecure.net/articles/Pulse_Secure_Article/KB44417)
- **Check Point VPN**: [Microsoft 365 ve diğer SaaS Uygulamaları için Bölünmüş Tünel'i yapılandırma](https://supportcenter.checkpoint.com/supportcenter/portal?eventSubmit_doGoviewsolutiondetails=&solutionid=sk167000)

## <a name="related-articles"></a>İlgili makaleler

[Genel bakış: Microsoft 365 için VPN bölünmüş tüneli](microsoft-365-vpn-split-tunnel.md)

[Microsoft 365 için yaygın VPN bölünmüş tünel senaryoları](microsoft-365-vpn-common-scenarios.md)

[VPN bölünmüş tüneli için Teams medya trafiğinin güvenliğini sağlama](microsoft-365-vpn-securing-teams.md)

[VPN ortamlarında Akış ve canlı etkinlikler için özel dikkat edilmesi gerekenler](microsoft-365-vpn-stream-and-live-events.md)

[Çin kullanıcıları için Microsoft 365 performans iyileştirmesi](microsoft-365-networking-china.md)

[Microsoft 365 Ağ Bağlantı İlkeleri](microsoft-365-network-connectivity-principles.md)

[Microsoft 365 ağ bağlantısını değerlendirme](assessing-network-connectivity.md)

[Microsoft 365 ağ ve performans ayarlama](network-planning-and-performance.md)

[Günümüzün benzersiz uzaktan çalışma senaryolarında modern güvenlik denetimleri elde etmek için güvenlik uzmanları ve BT için alternatif yollar (Microsoft Güvenlik Ekibi blogu)](https://www.microsoft.com/security/blog/2020/03/26/alternative-security-professionals-it-achieve-modern-security-controls-todays-unique-remote-work-scenarios/)

[Microsoft'ta VPN performansını geliştirme: Otomatik bağlantılara izin vermek için Windows 10 VPN profillerini kullanma](https://www.microsoft.com/itshowcase/enhancing-remote-access-in-windows-10-with-an-automatic-vpn-profile)

[VPN üzerinde çalıştırma: Microsoft uzak iş gücünü nasıl bağlı tutuyor?](https://www.microsoft.com/itshowcase/blog/running-on-vpn-how-microsoft-is-keeping-its-remote-workforce-connected/?elevate-lv)

[Microsoft küresel ağı](/azure/networking/microsoft-global-network)
