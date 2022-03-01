---
title: VPN bölmeli bölme Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 1/28/2022
audience: Admin
ms.article: conceptual
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
ms.openlocfilehash: 59414e32f187dc4e8354dc0c20228a4222fa2754
ms.sourcegitcommit: af73b93a904ce8604be319e8dc7cadaf65d50534
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/31/2022
ms.locfileid: "63010083"
---
# <a name="implementing-vpn-split-tunneling-for-microsoft-365"></a>VPN bölmeli bölme Microsoft 365

>[!NOTE]
>Bu makale, uzak kullanıcılar için iyileştirmeyi Microsoft 365 makale kümelerinin bir bölümüdir.

>- Uzak kullanıcılar için Microsoft 365 bağlantısını en iyi duruma getirmek için VPN bölünmüş şifreleme kullanma hakkında genel bir bakış için bkz[.](microsoft-365-vpn-split-tunnel.md) Genel Bakış: Vpn bölünmüş Microsoft 365.
>- Çin'deki kullanıcılar için Microsoft 365 kiracı performansını iyileştirme hakkında bilgi için bkz. [Microsoft 365 için performans iyileştirme.](microsoft-365-networking-china.md)

Kuruluşlar uzun zamandır, kullanıcılarına uzak deneyimleri desteklemek için VPN'ler kullanıyor. Temel iş yükleri şirket içinde kalırken, uzak kullanıcıların şirket kaynaklarına erişmesi için birincil yöntem, şirket ağının veri merkezi aracılığıyla yönlendirilen uzak istemciden VPN'tir. Kuruluşlar bu bağlantıları korumak için VPN yolları boyunca ağ güvenlik çözümlerinin katmanlarını oluşturmaz. Bu güvenlik, iç altyapıyı korumak ve trafiği VPN'ye yeniden yönlendirerek ve sonra da şirket içi İnternet çevresi üzerinden dışarı doğru yönlendirerek dış web sitelerini mobil taramayı korumak için yerleşik olarak kullanılır. VPN'ler, ağ çevreleri ve ilişkili güvenlik altyapısı genellikle amaca yönelik olarak yerleşik ve tanımlı bir trafik hacmi için ölçeklendirildi; bunlar genellikle çoğu bağlantı şirket ağının içinde ve büyük bir çoğu da iç ağ sınırları içinde kalıyor.

Bir süredir, uzak kullanıcı cihazından gelen tüm bağlantıların şirket içi ağa geri yönlendirdiği VPN modelleri (zorlamalı kaza olarak _bilinir), uzak_ kullanıcıların eş zamanlı ölçeği normal olduğu ve VPN'den çapraz geçen trafik hacminin düşük olduğu sürece büyük ölçüde sürdürülebilirdi.  Bazı müşteriler, uygulamaları şirket çevresi içinden genel SaaS bulutlarına taşındıktan sonra bile VPN zorlamasını status quo olarak kullanmaya devam etti.

Dağıtılmış ve performansa duyarlı bulut uygulamalarına bağlanmak için zorlamalı VPN'lerin kullanımı alt bir uygulamadır, ancak güvenlik durumu güvenliğinin korunması için bazı kuruluşlar bunu kabul eder. Bu senaryoya örnek bir diyagram aşağıdan görülebilir:

![VPN Tunnel bölün.](../media/vpn-split-tunneling/enterprise-network-traditional.png)

Birçok müşteri ağ trafiği desenlerinin önemli bir değişimini raporlamaktadır ve bu sorun yıllar boyunca büyüyen bir sorundur. Şirket içinde kalmak için kullanılan trafik artık dış bulut uç noktalarına bağlanır. Birçok Microsoft müşterisi, daha önce ağ trafiğinin yaklaşık %80'inin bir iç kaynakta (yukarıdaki diyagramda noktalı çizgiyle gösterildiği) olduğunu bildirmiştir. 2020'de bu sayı, büyük iş yüklerini buluta kaydırıldıklarında artık %20 veya daha düşüktür; bu eğilimler diğer kuruluşlarda az görülen bir eğilim değildir. Bulut yolculuğu ilerledikçe yukarıdaki model giderek zahmetli ve zahmetsiz hale gelir ve kuruluşun ilk bulut dünyasında çevik olması önlenebilir hale gelir.

Dünya çapında COVID-19 krizi bu sorunu acil düzeltme gerektirecek şekilde artan bir sorundur. Kurumsal IT üzerinde, ev dışından üretkenliği muazzam bir ölçekte desteklemek için çalışan güvenliğinin sağlanmasıyla ilgili talepler üretmektedir. Microsoft 365 müşterilerin bu talebi karşılamalarına yardımcı olmak için iyi bir konumdadır, ancak evden çalışan kullanıcıların yüksek eşzamanlılığı nedeniyle zorunlu VPN ve şirket içi ağ çevrelerine yönlendirilen çok büyük miktarda Microsoft 365 trafiği, doygunluğa neden olur ve VPN altyapısını kapasitenin dışında çalıştırır. Bu yeni gerçeklikte, Microsoft 365'e erişmek için VPN kullanmak artık yalnızca bir performans taadı değildir; yalnızca Microsoft 365'ı değil, aynı zamanda vpn'in çalışması için güvenmek zorunda olduğu kritik iş işlemlerini de etkileyen sıkı bir duvardır.

Microsoft, kendi hizmetlerimizden bu sorunlara etkili ve modern çözümler sunmak ve endüstrinin en iyi uygulamasıyla uyumlu olmak için uzun süredir müşterilerle ve daha geniş bir endüstriyle birlikte çalışıyor. [Yeni Hizmet Hizmeti'Microsoft 365](./microsoft-365-network-connectivity-principles.md) bağlantı ilkeleri, kuruluşun bağlantı üzerinde güvenlik ve denetime sahip çalışmasına olanak sağlarken, uzak kullanıcılar için etkili bir şekilde çalışacak şekilde tasarlanmıştır. Bu çözümler sınırlı çalışmayla da hızlı bir şekilde uygulanarak, yine de yukarıda belirtilen sorunlar üzerinde önemli olumlu bir etki elde edildi.

Uzak çalışanın bağlantısını en iyi duruma getirme konusunda Microsoft'un önerilen stratejisi, hızlı şekilde risk azaltmaya ve birkaç basit adımla yüksek performans sağlamaya odaklanmaktadır. Bu adımlar, performans sorunu olan VPN sunucularını atlayan birkaç tanımlı uç nokta için eski VPN yaklaşımını ayarlar. Şirket ağının çıkışta tüm trafiğin güvenliğini sağlama ihtiyacını ortadan kaldırmak için eşdeğer ve hatta üstün bir güvenlik modeli farklı katmanlara uygulanabilir. Çoğu durumda, bu durum etkili bir şekilde saatler içinde elde edilebilir ve gereksinimler talep ve zaman izin verdiyse diğer iş yükleri için ölçeklendirilebilir.

## <a name="common-vpn-scenarios"></a>Genel VPN senaryoları

Aşağıdaki listede, kurumsal ortamlarda görülen en yaygın VPN senaryolarını görebilirsiniz. Çoğu müşteri geleneksel olarak model 1'i (VPN Zorlamalı Vpn Tunnel). Bu bölüm, görece az çabayla elde edilebilir olan ve ağ performansıyla kullanıcı deneyiminin inanılmaz avantajları olan **Model 2'ye** hızlı ve güvenli bir şekilde geçiş içinde size yardımcı olur.

| Model | Açıklama |
| --- | --- |
| [1. VPN Zorunlu Tunnel](#1-vpn-forced-tunnel) | Trafiğin %100'ü şirket içi, İnternet ve tüm O365/M365 gibi VPN trafiğine gidiyor |
| [2. VPN Zorlanan Tunnel birkaç özel durumla](#2-vpn-forced-tunnel-with-a-small-number-of-trusted-exceptions) | VPN hattı varsayılan olarak kullanılır (varsayılan rota noktaları VPN'ye), ve doğrudan gitme izni verilen birkaç önemli muaf senaryo |
| [3. VPN Zorunlu Tunnel özel durumlar dışında](#3-vpn-forced-tunnel-with-broad-exceptions) | VPN hattı varsayılan olarak kullanılır (varsayılan rota noktaları VPN'ye), doğrudan yönlendiri izin verilen çok özel durumlar (tüm Microsoft 365, Tüm Salesforce, Tüm Yakınlaştırma) |
| [4. VPN Seçmeli Tunnel](#4-vpn-selective-tunnel) | VPN yolu yalnızca Corpnet tabanlı hizmetler için kullanılır. Varsayılan rota (İnternet ve tüm İnternet tabanlı hizmetler) doğrudan gider. |
| [5. VPN yok](#5-no-vpn) | #2'nin çeşitlemesi. Eski VPN yerine tüm corpnet hizmetleri modern güvenlik yaklaşımları (Zscaler ZPA, Azure Active Directory (Azure AD) Proxy/MCAS gibi) aracılığıyla yayımlanır. |

### <a name="1-vpn-forced-tunnel"></a>1. VPN Zorunlu Tunnel

Kurumsal müşterilerin çoğu için en yaygın başlangıç senaryosu. Zorlamalı bir VPN kullanılır, bu da uç nokta şirket ağı içinde olsun ya da yer alınsın trafiğin %100'musunuz şirket ağına yönlendirildi anlamına gelir. İnternet'e Microsoft 365 veya İnternet'e gözatma gibi dış (İnternet) bağlı tüm trafik, sonrasında şirket içi güvenlik donanımının (örneğin, şirket içi güvenlik donanımı) geri sabitlenmiş olmasıdır. Geçerli karnede uzaktan çalışan kullanıcıların neredeyse %100'olduğu bu model dolayısıyla VPN altyapısına yüksek yük koyar ve büyük olasılıkla tüm şirket trafiğinin performansını önemli ölçüde azaltır ve dolayısıyla kuruluş kriz durumlarında etkili bir şekilde çalışmaya devam etmektedir.

![VPN Zorunlu Tunnel model 1.](../media/vpn-split-tunneling/vpn-model-1.png)

### <a name="2-vpn-forced-tunnel-with-a-small-number-of-trusted-exceptions"></a>2. VPN Tunnel çok az sayıda güvenilen özel durum ile zorunlu vpn

Bir işletmenin şu kuruluş kapsamında çalışması çok daha verimlidir. Bu model, yüksek yüke ve gecikme süresine duyarlı az sayıda denetimli ve tanımlanmış uç noktaların VPN taraklarını atlayarak doğrudan Microsoft 365 sağlar. Bu, yüklenen hizmetlerin performansını önemli ölçüde artırır ve VPN altyapısının yükünü de azaltır; böylelikle, kaynaklar için daha düşük içerikle çalışması için yine de gereken öğelerin çalışmasına olanak sağlar. Bu makalenin çok sayıda pozitif sonuçla hızlı bir şekilde basit ve tanımlı eylemlere izin verirken geçişte yardımcı olmaya odaklanan bu modeldir.

![Bölünmüş Tunnel VPN modeli 2.](../media/vpn-split-tunneling/vpn-model-2.png)

### <a name="3-vpn-forced-tunnel-with-broad-exceptions"></a>3. VPN Zorunlu Tunnel özel durumlar dışında

Model 2'nin kapsamını genişleten. Yalnızca küçük bir tanımlı uç nokta grubunu doğrudan göndermek yerine, bunun yerine tüm trafiği doğrudan Microsoft 365 SalesForce gibi güvenilir hizmetlere gönderir. Bu da şirket VPN altyapısının yükünü daha da azaltır ve tanımlanan hizmetlerin performansını iyiler. Bu modelin uygulanabililiğini değerlendirmek ve uygulamak için daha fazla zaman gerektir, bu büyük olasılıkla iki model başarılı bir şekilde tamam olduktan sonra ileri bir tarihte tekrarlayan bir adımdır.

![Bölünmüş Tunnel VPN modeli 3.](../media/vpn-split-tunneling/vpn-model-3.png)

### <a name="4-vpn-selective-tunnel"></a>4. VPN seçmeli Tunnel

Üçüncü modeli tersine çevirerek yalnızca şirket IP adresi olması olarak tanımlanan trafiğin VPN trafiğine iner ve İnternet yolu diğer her şey için varsayılan yol olur. Bu model, bu modeli güvenli bir şekilde uygulayabilecek [Sıfır](https://www.microsoft.com/security/zero-trust?rtc=1) Güven yolunda kuruluşun iyi bir şekilde yola sahip olması gerekir. Bu modelin veya böyle bir çeşitlemenin, zaman içinde daha fazla hizmet şirket ağına ve buluta taşınacak şekilde gerekli varsayılan ayar olacağını dikkate alın.

Microsoft bu modeli dahili olarak kullanır. Microsoft'un VPN bölünmüş bölme uygulaması hakkında daha fazla bilgiyi VPN'de çalıştırma: Microsoft uzaktan iş gücü bağlantısını [nasıl bağlı tutarak devam ediyor makalesinde bulabilirsiniz](https://www.microsoft.com/itshowcase/blog/running-on-vpn-how-microsoft-is-keeping-its-remote-workforce-connected/?elevate-lv).

![Bölünmüş Tunnel VPN modeli 4.](../media/vpn-split-tunneling/vpn-model-4.png)

### <a name="5-no-vpn"></a>5. VPN yok

Model numarası 2'nin daha gelişmiş bir sürümü; böylece tüm iç hizmetler, Azure AD Proxy, Bulut Uygulamaları için Defender, Zscaler ZPA, vb. modern bir güvenlik yaklaşımı veya SDWAN çözümü aracılığıyla yayımlanır.

![Bölünmüş Tunnel VPN modeli 5.](../media/vpn-split-tunneling/vpn-model-5.png)

## <a name="implement-vpn-split-tunneling"></a>VPN bölünmüş bilgisayar bölmeleri uygulama

Bu bölümde, VPN istemci mimarinizi BIR VPN zorlamalı basamaktan birkaç güvenilen özel durumla _VPN_ zorlamalı basamaklara geçirmek için gereken basit adımları, Ortak [VPN](#common-vpn-scenarios) senaryolarında VPN bölünmüş basamak [modeli #2](#2-vpn-forced-tunnel-with-a-small-number-of-trusted-exceptions) bulabilirsiniz.

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
| Teams IP'leri ekleyin (URL yok) | UDP 3478, 3479, 3480 ve 3481 | Geçiş Bulma ayırma ve gerçek zamanlı trafik (3478), Ses (3479), Video (3480) ve Video Ekran Paylaşımı (3481). Bunlar, Medya trafiği (Skype Kurumsal Microsoft Teams, toplantılar vb.) için kullanılan uç noktalardır. Uç noktaların çoğu, Microsoft Teams istemci bir çağrı kurduğunda (ve hizmet için listelenen gerekli IP'ler içinde yer alır) olduğunda sağlanır. En iyi medya kalitesi için UDP protokolünün kullanımı gereklidir.   |

Yukarıdaki örneklerde, **kiracı** sizin kiracı adınızla değiştir Microsoft 365 gerekir. Örneğin, **contoso.onmicrosoft.com'i** _contoso.sharepoint.com_ _ve contoso-my.sharepoint.com_.

#### <a name="optimize-ip-address-ranges"></a>IP adresi aralıklarını en iyi duruma getirme

Bu uç noktaların karşılık gelen IP adresi aralıklarını yazma zamanında aşağıdaki gibidir. Bu örnekteki  gibi bir betik, [Microsoft 365 IP ve URL web](microsoft-365-ip-web-service.md) hizmeti veya [URL/IP](urls-and-ip-address-ranges.md) sayfası gibi bir komut dosyası kullanarak yapılandırmayı uygularken güncelleştirmeleri denetlemeniz ve bunu düzenli olarak yapmak üzere bir ilke koymanız kesinlikle önerilir.[](https://github.com/microsoft/Office365NetworkTools/tree/master/Scripts/Display%20URL-IPs-Ports%20per%20Category)

```
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

## <a name="configuring-and-securing-teams-media-traffic"></a>Medya trafiğini yapılandırma Teams güvenlik altına alma

Bazı yöneticiler, bölünmüş bir bölme modeli kullanarak arama akışlarının Teams ve bağlantıların güvenliği nasıl sağlandı hakkında daha ayrıntılı bilgi gerekli olabilir.

### <a name="configuration"></a>Yapılandırma

Hem çağrılar hem de toplantılar için, Teams medyası için gerekli IP alt ağlarını yol tablosunda doğru olarak iyi duruma getirmekse, Teams hangi yerel arabirimin belirli bir hedef için kullanması gereken yönlendirmeye karşılık geldiğinde[,](/windows/win32/api/iphlpapi/nf-iphlpapi-getbestroute) yukarıda listelenen Microsoft IP bloklarında Microsoft hedefleri için yerel arabirim döndürülür.

Bazı VPN istemci yazılımları URL'ye göre yönlendirme işlemeye izin verir. Bununla birlikte Teams medya trafiğinin URL'si yoktur, bu nedenle bu trafik için yönlendirmenin denetimi IP alt ağları kullanılarak yapılması gerekir.

Bazı senaryolarda, genellikle istemci Teams ilgili olmayan medya trafiği yerine doğru yönlendirmeler olsa bile VPN trafiğine çapraz geçişlere neden olur. Bu senaryoyla karşılaşırsanız, IP alt ağlarının veya VPN'nin Teams bağlantı noktalarını engellemek için güvenlik duvarı kuralı kullanmak yeterlidir.

>[!IMPORTANT]
>Medya trafiğinin Teams VPN senaryolarında istenen yöntem ile yönlendirilebilir olduğundan emin olmak için, lütfen kullanıcıların Microsoft Teams **1.3.00.13565** veya daha yeni bir sürüm çalıştır çalıştırya olduğundan emin olun. Bu sürüm, istemcinin kullanılabilir ağ yollarını algılaması ile ilgili geliştirmeler içerir.

Trafiğin sinyali HTTPS üzerinden yapılır, medya trafiği kadar gecikmeye duyarlı değildir ve URL/IP verisinde İzin Ver olarak  işaretlenir ve böylece istenirse VPN istemcisi üzerinden güvenli bir şekilde yönlendirilebilir.

>[!NOTE]
>Microsoft Edge **96 ve üzeri**, eşler arası trafik için VPN bölünmüş şifrelemeyi de destekler. Bu da, örneğin müşterilerin Edge'de web istemcilerinde VPN bölünmüş Teams avantajından yararlanabilecekleri anlamına gelir. Edge'de çalışan web siteleri için ayarlamak isteyen müşteriler, Edge [WebRtcRespectOsRoutingTableEnabled](/deployedge/microsoft-edge-policies#webrtcrespectosroutingtableenabled) İlkesini etkinleştirmenin ek adımlarını atarak bunu elde edebilirsiniz.

### <a name="security"></a>Güvenlik

Bölünmüş bölmelerden kaçınmak için yaygın bir bağımsız değişken, örneğin böyle yapmak için daha az güvenlidir VPN hattından geç yapmayan trafikler VPN şemalarına uygulanan şifreleme düzeninden yararlanmayacaktır ve bu nedenle daha az güvenli olur.

Bunun ana bağımsız değişkeni, medya trafiğinin RTP trafiğine gizlilik, kimlik doğrulama ve saldırı koruması sağlayan bir Real-Time Aktarım Protokolü (RTP) profili olan Güvenli Real-Time Aktarım Protokolü _(SRTP_) aracılığıyla zaten şifrelenmiş durumdadır. SRTP'nin kendisi, TLS güvenli sinyal kanalı üzerinden yapılan rastgele oluşturulmuş bir oturum anahtarına dayandır. Bu, bu güvenlik kılavuzunda çok [ayrıntılı olarak ele almaktadır](/skypeforbusiness/optimizing-your-network/security-guide-for-skype-for-business-online), ancak ilgili birincil bölüm medya şifrelemedir.

Medya trafiği, güvenli bir rastgele sayı oluşturucu tarafından oluşturulan ve sinyal TLS kanalı kullanılarak değişten bir oturum anahtarı kullanan SRTP kullanılarak şifrelenir. Buna ek olarak, Ara Sunucu ile bir sonraki iç atlama arasında her iki yönde de akan medya da SRTP kullanılarak şifrelenir.

Skype Kurumsal Online, NAT (TURN) çevresinde Geçişleri Kullanarak Çapraz Geçiş üzerinden medya geçişlerine güvenli erişim için kullanıcı adı/_parolalar üretir_. Medya geçişleri, kullanıcı adını/parolayı TLS güvenliği olan bir SIP kanalı üzerinden değiştirmektedir. İstemciyi şirket ağına bağlamak için VPN yolu kullansanız bile trafiğin hizmete ulaşmak için şirket ağına ulaşacak şekilde SRTP biçimine akmaya devam ediyor olması gerekir.

Teams _NAT (STUN)_ amplification saldırılarının ses veya Oturum Çapraz Yardımcı Programları gibi yaygın güvenlik endişelerini nasıl azaltmakta olduğuyla ilgili bilgiler [, Uygulamacılar için 5.1](/openspecs/office_protocols/ms-ice2/69525351-8c68-4864-b8a6-04bfbc87785c) GüvenlikLe ilgili Dikkate Alınacak Noktalar'da bulunabilir.

Ayrıca, uzak çalışma senaryolarında modern güvenlik denetimleri hakkında bilgi edinebilirsiniz. Bunun için, güvenlik uzmanları ve BT'nin günümüzün benzersiz uzaktan çalışma senaryolarında modern güvenlik denetimlerine ulaşmanın alternatif yolları [(Microsoft Güvenlik Ekibi blogu)](https://www.microsoft.com/security/blog/2020/03/26/alternative-security-professionals-it-achieve-modern-security-controls-todays-unique-remote-work-scenarios/)'nda da okuyabilirsiniz.

### <a name="testing"></a>Test

İlke tamam olduktan sonra, İlke'nin beklendiği gibi çalıştığını onaylamanız gerekir. Yolu yerel İnternet bağlantısını kullanmak için doğru olarak ayarlanmış olan birden çok test yolu vardır:

- Yukarıda [Microsoft 365 izleme yollarını](https://aka.ms/netonboard) da dahil olmak üzere sizin için bağlantı testleri çalıştıracak olan hızlı bağlantı testini çalıştırın. Ayrıca bu araçta, ek içgörüler de sağlayacak ŞEKILDE VPN testleri ekliyoruz.

- Bölünmüş yolun **kapsamı** içindeki bir uç noktasına giden basit bir izleme yolu, alınan yolu gösterse, örneğin:

  ```powershell
  tracert worldaz.tr.teams.microsoft.com
  ```

  Ardından, yerel ISS üzerinden bu uç noktaya giden ve bölünmüş bölme için yapılandırmış Teams aralıklarında bir IP'ye çözümlemesi gereken bir yol görüyorsanız.

- Wireshark gibi bir aracı kullanarak ağ yakalaması alma. Arama sırasında UDP'ye göre filtre uygulama ve En İyi Duruma Getirme aralığında **IP'ye** Teams gerekir. Bu trafik için VPN trafiği kullanılıyorsa, medya trafiği izlemede görünmez.

### <a name="additional-support-logs"></a>Ek destek günlükleri

Sorun gidermek için daha fazla veriye ihtiyacınız varsa veya Microsoft desteğinden yardım bekliyorsanız, aşağıdaki bilgileri almak çözüm bulma işleminizi hızlandırabilirsiniz. Microsoft desteğinin **TSS Windows CMD tabanlı evrensel** Sorun Betik araçları, ilgili günlükleri basit bir şekilde toplamanıza yardımcı olabilir. Araç ve kullanım yönergelerini burada bulunabilir <https://aka.ms/TssTools>.

## <a name="how-to-optimize-stream--live-events"></a>Stream'i Canlı Etkinlikler & İyileştirin

Microsoft 365 Canlı Etkinlikler trafiği (bu, Teams tarafından üretilen canlı etkinliklere katılanları ve Teams, Stream veya Yammer aracılığıyla dış kodlayıcıyla üretilenleri içerir) ve isteğe bağlı Stream trafiği şu anda hizmet için [URL/IP](urls-and-ip-address-ranges.md) listesinde Varsayılan yerine En İyi Duruma getirmek için kategorilere ayrılmıştır.  Bu uç noktalar, diğer hizmetler **tarafından** da kullanılmaktadır ve CDN'lerde barındırıldıkları için Varsayılan olarak kategorilere ayrılmıştır. Müşteriler genel olarak bu trafik türüne ara sunucu olmayı ve bunlar gibi uç noktalarda normalde yapılan güvenlik öğelerini uygulamayı tercih eder.

Birçok müşteri VPN altyapısı üzerinden yüksek hacimli ve gecikmeli trafiği yönlendirmek yerine kullanıcılarını doğrudan yerel İnternet bağlantılarından Stream/Live Events'e bağlamak için gereken URL/IP verilerini istedi. Normalde, hem ayrılmış ad alanları hem de uç noktalar için doğru IP bilgileri olmadan mümkün değildir ve varsayılan olarak kategorilere ayrılmış Microsoft 365 uç noktaları için **sağ değildir**.

Zorlamalı bir VPN kullanan istemcilerden Stream/Live Events hizmetine doğrudan bağlantı sağlamak için aşağıdaki adımları kullanın. Bu çözüm, müşterilere evden çalışma senaryolarından dolayı yüksek ağ trafiği varken CANLı Etkinlikler trafiğini VPN üzerinden yönlendirmeyi önleme seçeneği sağlamak üzere tasarlanmıştır. Mümkünse, hizmete denetimli bir proxy aracılığıyla erişmeniz önerilir.

>[!NOTE]
>Bu çözümün kullanımı, sağlanan IP adreslerine çözüm olmayan ve dolayısıyla VPN'den çapraz geçiş yapılan hizmet öğeleri olabilir, ancak akış verileri gibi yüksek hacimli trafiklerin toplu olması gerekir. Canlı Etkinlikler/Akış kapsamının dışında bu yüklemeyle karşılaşan başka öğeler de olabilir, ancak doğrudan gitmeden önce hem FQDN'ye hem de IP eşleşmesini karşılamaları gerektiği  için bunlar sınırlı olacaktır.

>[!IMPORTANT]
>Müşterilere Canlı Etkinlikler için performans artışı üzerinden VPN'i atlayan daha fazla trafik gönderme riskini değerlendirmeleri önerilir.

Canlı Etkinlikler ve Akış için zorunlu Teams özel durumu uygulamak için aşağıdaki adımlar uygulanmalıdır:

### <a name="1-configure-external-dns-resolution"></a>1. Dış DNS çözümlemelerini yapılandırma

İstemcilerin IP adreslerinde aşağıdaki ana bilgisayar adlarının çözümlensin diye harici, tekrarlayan DNS çözümlemesi kullanılabilir olması gerekir.

- \*.azureedge.net
- \*.media.azure.net
- \*.bmc.cdn.office.net

**\*.azureedge.net** Stream olayları için kullanılır (Microsoft Stream'de canlı akış için kodlayıcıları yapılandırma [- Microsoft Stream | Microsoft Docs](/stream/live-encoder-setup)).

**\*.media.azure.net** **ve\* .bmc.cdn.office.net**, Teams istemcisinde zamanlanan Teams tarafından üretilen Canlı Etkinlikler (Hızlı Başlangıç etkinlikleri, RTMP-In desteklenen etkinlikler [Yol Haritası Kimliği 84960]) için kullanılır.

 Bu uç noktaların bazıları Stream/Live Events dışındaki diğer öğelerle paylaşılır, VPN çözümünüzde (IP yerine FQDN'de çalışıyor olması gibi) teknik olarak mümkün olsa bile VPN yüklemesini yapılandırmak için yalnızca bu FQDN'leri kullanmak iyi değildir.

FQDN'ler VPN yapılandırmasında gerekli değildir, yalnızca ILGILI trafiği doğrudan göndermek üzere IP'lerle birlikte PAC dosyalarında kullanılabilir.

### <a name="2-implement-pac-file-changes-where-required"></a>2. PAC dosyası değişikliklerini uygulama (gerektiğinde)

VPN'deyken trafiği ara sunucu üzerinden yönlendiren PAC dosyası kullanan kuruluşlarda, bu normalde FQDN'ler kullanılarak elde edilir. Bununla birlikte, Stream/Live Events'de, **\*** sağlanan ana bilgisayar adları .azureedge.net gibi joker karakterler içerir ve bu aynı zamanda tam IP listeleri sağlamak mümkün olmayan diğer öğeleri de kapsar. Dolayısıyla, istek tek başına DNS joker karakteri eşleşmesini temel alarak doğrudan gönderilirse, 3. Adımda isteğin doğrudan yolu üzerinden hiçbir yönlendirme yoksa bu uç noktalara giden [trafik engellenir](#3-configure-routing-on-the-vpn-to-enable-direct-egress).

Bu sorunu çözmek için, aşağıdaki IP'leri sağ çözebiliriz ve bunları örnek bir PAC dosyasında [1](#1-configure-external-dns-resolution) . Adım'daki ana bilgisayar adlarla birlikte kullanabiliriz. PAC dosyası, URL'nin Stream/Live Events için kullanılanlarla eş olup eşleşmesi ve eş olup eşleşmesinin ardından, DNS aramalarından döndürülen IP'nin hizmet için sağlananlarla eş olup eşleşmesi için de kontrol yapar. Her _iki_ eşleşme de aynı olursa, trafik doğrudan yönlendirildi. Öğeden biri (FQDN/IP) eş eş olmuyorsa trafik ara sunucuya gönderilir. Sonuç olarak, yapılandırma hem IP hem de tanımlanmış ad alanlarının kapsamı dışında IP'ye çözüm olarak her şeyin VPN üzerinden proxy'den normalde çapraz geçiş yapmasını sağlar.

#### <a name="gathering-the-current-lists-of-cdn-endpoints"></a>Uç Noktaların geçerli CDN toplama

Canlı Etkinlikler, en CDN, kalite ve güvenlik için müşterilere akış sağlamak için birden fazla kullanıcı sağlayıcısı kullanır. Şu anda hem Microsoft'Azure CDN hem de Verizon'dan gelen e-postaların her ikisi de kullanılır. Zamanla bu durum bölgesel kullanılabilirlik gibi durumlar nedeniyle değiştirilebilir. Bu makale, IP aralıklarında güncel bilgi alamama olanak sağlayan bir kaynaktır.

Microsoft'tan Azure CDN için listeyi Azure IP Aralıkları ve Hizmet Etiketlerini İndir [( Resmi Microsoft İndirme](https://www.microsoft.com/download/details.aspx?id=56519) Merkezi'nden Genel Bulut - JSON hizmet etiketi *AzureFrontdoor.Frontend* için özel olarak bakmanız gerekir; *addressPrefixes*, IPv4/IPv6 alt ağlarını gösterir. Zaman içinde IP'ler değişebilir, ancak hizmet etiket listesi her zaman kullanımdan önce güncelleştirilir.

Verizon (Edgecast) [https://docs.microsoft.com/rest/api/cdn/edge-nodes/list](/rest/api/cdn/edge-nodes/list) Azure CDN için kapsamlı bir liste bulmak için (Dene'ye **tıklayın) -** **Premium\_ Verizon** bölümüne özel olarak bakabilirsiniz. Bu API'nin tüm Edgecast IP'lerini (origin ve Anycast) gösterir. Şu anda API'nin kaynak ile Anycast arasındaki farkı ayırt etme mekanizması yok.

Bunu bir PAC dosyasında uygulamak için, FQDN aracılığıyla Microsoft 365 Trafiği doğrudan en iyi duruma getirme (önerilen en iyi yöntem) ve kritik Stream/Live Events trafiğini doğrudan FQDN ve döndürülen IP adresinin bir bileşimiyle gönderen aşağıdaki örneği kullanabilirsiniz. _Contoso_ yer tutucu adı, kiracınız adına göre düzenlenemez; burada _Contoso_ yer tutucu contoso.onmicrosoft.com

##### <a name="example-pac-file"></a>Örnek PAC dosyası

PAC dosyalarını oluşturma örneği:

1. Aşağıdaki betiği yerel sabit diske kaydedtik olarak _Get-TLEPacFile.ps1_.
1. [Verizon URL'sine](/rest/api/cdn/edge-nodes/list#code-try-0) gidin ve sonuçta elde edilen JSON'u indirin (bunu cdnedgenodes.json gibi bir dosyaya yapıştırın)
1. Dosyayı betikle aynı klasöre koyma.
1. PowerShell penceresinde aşağıdaki komutu çalıştırın. SPO URL'leri için kiracı adını başka bir adla değiştirebilirsiniz. Bu, Tür 2'dir, dolayısıyla **En İyi Duruma** **Getirme** ve İzin Ver (1 türü yalnızca En İyi Duruma Getirme'dir).

   ```powershell
   .\Get-TLEPacFile.ps1 -Instance Worldwide -Type 2 -TenantName <contoso> -CdnEdgeNodesFilePath .\cdnedgenodes.json -FilePath TLE.pac
   ```

5. TLE.pac dosyası tüm ad alanlarını ve IPv4/IPv6'ları içerir.

###### <a name="get-tlepacfileps1"></a>Get-TLEPacFile.ps1

```powershell
# Copyright (c) Microsoft Corporation. All rights reserved.
# Licensed under the MIT License.

<#PSScriptInfo

.VERSION 1.0.4

.AUTHOR Microsoft Corporation

.GUID 7f692977-e76c-4582-97d5-9989850a2529

.COMPANYNAME Microsoft

.COPYRIGHT
Copyright (c) Microsoft Corporation. All rights reserved.
Licensed under the MIT License.

.TAGS PAC Microsoft Microsoft365 365

.LICENSEURI

.PROJECTURI http://aka.ms/ipurlws

.ICONURI

.EXTERNALMODULEDEPENDENCIES

.REQUIREDSCRIPTS

.EXTERNALSCRIPTDEPENDENCIES

.RELEASENOTES

#>

<#

.SYNOPSIS

Create a PAC file for Microsoft 365 prioritized connectivity

.DESCRIPTION

This script will access updated information to create a PAC file to prioritize Microsoft 365 Urls for
better access to the service. This script will allow you to create different types of files depending
on how traffic needs to be prioritized.

.PARAMETER Instance

The service instance inside Microsoft 365.

.PARAMETER ClientRequestId

The client request id to connect to the web service to query up to date Urls.

.PARAMETER DirectProxySettings

The direct proxy settings for priority traffic.

.PARAMETER DefaultProxySettings

The default proxy settings for non priority traffic.

.PARAMETER Type

The type of prioritization to give. Valid values are 1 and 2, which are 2 different modes of operation.
Type 1 will send Optimize traffic to the direct route. Type 2 will send Optimize and Allow traffic to
the direct route.

.PARAMETER Lowercase

Flag this to include lowercase transformation into the PAC file for the host name matching.

.PARAMETER TenantName

The tenant name to replace wildcard Urls in the webservice.

.PARAMETER ServiceAreas

The service areas to filter endpoints by in the webservice.

.PARAMETER FilePath

The file to print the content to.

.EXAMPLE

Get-TLEPacFile.ps1 -ClientRequestId b10c5ed1-bad1-445f-b386-b919946339a7 -DefaultProxySettings "PROXY 4.4.4.4:70" -FilePath type1.pac

.EXAMPLE

Get-TLEPacFile.ps1 -ClientRequestId b10c5ed1-bad1-445f-b386-b919946339a7 -Instance China -Type 2 -DefaultProxySettings "PROXY 4.4.4.4:70" -FilePath type2.pac

.EXAMPLE

Get-TLEPacFile.ps1 -ClientRequestId b10c5ed1-bad1-445f-b386-b919946339a7 -Instance WorldWide -Lowercase -TenantName tenantName -ServiceAreas Sharepoint

#>

#Requires -Version 2

[CmdletBinding(SupportsShouldProcess=$True)]
Param (
    [Parameter(Mandatory = $false)]
    [ValidateSet('Worldwide', 'Germany', 'China', 'USGovDoD', 'USGovGCCHigh')]
    [String] $Instance = "Worldwide",

    [Parameter(Mandatory = $false)]
    [ValidateNotNullOrEmpty()]
    [guid] $ClientRequestId = [Guid]::NewGuid().Guid,

    [Parameter(Mandatory = $false)]
    [ValidateNotNullOrEmpty()]
    [String] $DirectProxySettings = 'DIRECT',

    [Parameter(Mandatory = $false)]
    [ValidateNotNullOrEmpty()]
    [String] $DefaultProxySettings = 'PROXY 10.10.10.10:8080',

    [Parameter(Mandatory = $false)]
    [ValidateRange(1, 2)]
    [int] $Type = 1,

    [Parameter(Mandatory = $false)]
    [switch] $Lowercase = $false,

    [Parameter(Mandatory = $false)]
    [ValidateNotNullOrEmpty()]
    [string] $TenantName,

    [Parameter(Mandatory = $false)]
    [ValidateSet('Exchange', 'SharePoint', 'Common', 'Skype')]
    [string[]] $ServiceAreas,

    [Parameter(Mandatory = $false)]
    [ValidateNotNullOrEmpty()]
    [string] $FilePath,

    [Parameter(Mandatory = $false)]
    [ValidateNotNullOrEmpty()]
    [string] $CdnEdgeNodesFilePath
)

##################################################################################################################
### Global constants
##################################################################################################################

$baseServiceUrl = "https://endpoints.office.com/endpoints/$Instance/?ClientRequestId={$ClientRequestId}"
$directProxyVarName = "direct"
$defaultProxyVarName = "proxyServer"
$bl = "`r`n"

##################################################################################################################
### Functions to create PAC files
##################################################################################################################

function Get-PacClauses
{
    param(
        [Parameter(Mandatory = $false)]
        [string[]] $Urls,

        [Parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String] $ReturnVarName
    )

    if (!$Urls)
    {
        return ""
    }

    $clauses =  (($Urls | ForEach-Object { "shExpMatch(host, `"$_`")" }) -Join "$bl        || ")

@"
    if($clauses)
    {
        return $ReturnVarName;
    }
"@
}

function Get-PacString
{
    param(
        [Parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [array[]] $MapVarUrls
    )

@"
// This PAC file will provide proxy config to Microsoft 365 services
//  using data from the public web service for all endpoints
function FindProxyForURL(url, host)
{
    var $directProxyVarName = "$DirectProxySettings";
    var $defaultProxyVarName = "$DefaultProxySettings";

$( if ($Lowercase) { "    host = host.toLowerCase();" })

$( ($MapVarUrls | ForEach-Object { Get-PACClauses -ReturnVarName $_.Item1 -Urls $_.Item2 }) -Join "$bl$bl" )

$( if (!$ServiceAreas -or $ServiceAreas.Contains('Skype')) { Get-TLEPacConfiguration })

    return $defaultProxyVarName;
}
"@ -replace "($bl){3,}","$bl$bl" # Collapse more than one blank line in the PAC file so it looks better.
}

##################################################################################################################
### Functions to get and filter endpoints
##################################################################################################################

function Get-TLEPacConfiguration {
    param ()
    $PreBlock = @"
    // Don't Proxy Teams Live Events traffic

    if(shExpMatch(host, "*.azureedge.net")
    || shExpMatch(host, "*.bmc.cdn.office.net")
    || shExpMatch(host, "*.media.azure.net"))
    {
        var resolved_ip = dnsResolveEx(host);

"@
    $TLESb = New-Object 'System.Text.StringBuilder'
    $TLESb.Append($PreBlock) | Out-Null

    if (![string]::IsNullOrEmpty($CdnEdgeNodesFilePath) -and (Test-Path -Path $CdnEdgeNodesFilePath)) {
        $CdnData = Get-Content -Path $CdnEdgeNodesFilePath -Raw -ErrorAction SilentlyContinue | ConvertFrom-Json | Select-Object -ExpandProperty value | 
            Where-Object { $_.name -eq 'Premium_Verizon'} | Select-Object -First 1 -ExpandProperty properties | 
            Select-Object -ExpandProperty ipAddressGroups
        $CdnData | Select-Object -ExpandProperty ipv4Addresses | ForEach-Object {
            if ($TLESb.Length -eq $PreBlock.Length) {
                $TLESb.Append("        if(") | Out-Null
            }
            else {
                $TLESb.AppendLine() | Out-Null
                $TLESb.Append("        || ") | Out-Null
            }
            $TLESb.Append("isInNetEx(resolved_ip, `"$($_.BaseIpAddress)/$($_.prefixLength)`")") | Out-Null
        }
        $CdnData | Select-Object -ExpandProperty ipv6Addresses | ForEach-Object {
            if ($TLESb.Length -eq $PreBlock.Length) {
                $TLESb.Append("        if(") | Out-Null
            }
            else {
                $TLESb.AppendLine() | Out-Null
                $TLESb.Append("        || ") | Out-Null
            }
            $TLESb.Append("isInNetEx(resolved_ip, `"$($_.BaseIpAddress)/$($_.prefixLength)`")") | Out-Null
        }
    }
    $AzureIPsUrl = Invoke-WebRequest -Uri "https://www.microsoft.com/en-us/download/confirmation.aspx?id=56519" -UseBasicParsing -ErrorAction SilentlyContinue  | 
            Select-Object -ExpandProperty Links | Select-Object -ExpandProperty href | 
            Where-Object { $_.EndsWith('.json') -and $_ -match 'ServiceTags' } | Select-Object -First 1
    if ($AzureIPsUrl) {
        Invoke-RestMethod -Uri $AzureIPsUrl -ErrorAction SilentlyContinue | Select-Object -ExpandProperty values | 
            Where-Object { $_.name -eq 'AzureFrontDoor.Frontend' } | Select-Object -First 1 -ExpandProperty properties |
            Select-Object -ExpandProperty addressPrefixes | ForEach-Object {
                if ($TLESb.Length -eq $PreBlock.Length) {
                    $TLESb.Append("        if(") | Out-Null
                }
                else {
                    $TLESb.AppendLine() | Out-Null
                    $TLESb.Append("        || ") | Out-Null
                }
                $TLESb.Append("isInNetEx(resolved_ip, `"$_`")") | Out-Null
            }
    }
    if ($TLESb.Length -gt $PreBlock.Length) {
        $TLESb.AppendLine(")") | Out-Null
        $TLESb.AppendLine("        {") | Out-Null
        $TLESb.AppendLine("            return $directProxyVarName;") | Out-Null
        $TLESb.AppendLine("        }") | Out-Null
    }
    else {
        $TLESb.AppendLine("        // no addresses found for service via script") | Out-Null
    }
    $TLESb.AppendLine("    }") | Out-Null
    return $TLESb.ToString()
}

function Get-Regex
{
    param(
        [Parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [string] $Fqdn
    )

    return "^" + $Fqdn.Replace(".", "\.").Replace("*", ".*").Replace("?", ".?") + "$"
}

function Match-RegexList
{
    param(
        [Parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [string] $ToMatch,

        [Parameter(Mandatory = $false)]
        [string[]] $MatchList
    )

    if (!$MatchList)
    {
        return $false
    }
    foreach ($regex in $MatchList)
    {
        if ($regex -ne $ToMatch -and $ToMatch -match (Get-Regex $regex))
        {
            return $true
        }
    }
    return $false
}

function Get-Endpoints
{
    $url = $baseServiceUrl
    if ($TenantName)
    {
        $url += "&TenantName=$TenantName"
    }
    if ($ServiceAreas)
    {
        $url += "&ServiceAreas=" + ($ServiceAreas -Join ",")
    }
    return Invoke-RestMethod -Uri $url
}

function Get-Urls
{
    param(
        [Parameter(Mandatory = $false)]
        [psobject[]] $Endpoints
    )

    if ($Endpoints)
    {
        return $Endpoints | Where-Object { $_.urls } | ForEach-Object { $_.urls } | Sort-Object -Unique
    }
    return @()
}

function Get-UrlVarTuple
{
    param(
        [Parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [string] $VarName,

        [Parameter(Mandatory = $false)]
        [string[]] $Urls
    )
    return New-Object 'Tuple[string,string[]]'($VarName, $Urls)
}

function Get-MapVarUrls
{
    Write-Verbose "Retrieving all endpoints for instance $Instance from web service."
    $Endpoints = Get-Endpoints

    if ($Type -eq 1)
    {
        $directUrls = Get-Urls ($Endpoints | Where-Object { $_.category -eq "Optimize" })
        $nonDirectPriorityUrls = Get-Urls ($Endpoints | Where-Object { $_.category -ne "Optimize" }) | Where-Object { Match-RegexList $_ $directUrls }
        return @(
            Get-UrlVarTuple -VarName $defaultProxyVarName -Urls $nonDirectPriorityUrls
            Get-UrlVarTuple -VarName $directProxyVarName -Urls $directUrls
        )
    }
    elseif ($Type -eq 2)
    {
        $directUrls = Get-Urls ($Endpoints | Where-Object { $_.category -in @("Optimize", "Allow")})
        $nonDirectPriorityUrls = Get-Urls ($Endpoints | Where-Object { $_.category -notin @("Optimize", "Allow") }) | Where-Object { Match-RegexList $_ $directUrls }
        return @(
            Get-UrlVarTuple -VarName $defaultProxyVarName -Urls $nonDirectPriorityUrls
            Get-UrlVarTuple -VarName $directProxyVarName -Urls $directUrls
        )
    }
}

##################################################################################################################
### Main script
##################################################################################################################

$content = Get-PacString (Get-MapVarUrls)

if ($FilePath)
{
    $content | Out-File -FilePath $FilePath -Encoding ascii
}
else
{
    $content
}
```

Betik, **AzurefrontDoor.Frontend'ın** indirme [URL'sini](https://www.microsoft.com/download/details.aspx?id=56519) ve anahtarlarını temel alarak Azure listesini otomatik olarak ayrıştıracaktır, dolayısıyla onu el ile almak gerekmez.

Bir kez daha, yalnızca FQDN'leri kullanarak VPN yüklemesi gerçekleştirmeniz tavsiye edilir; hem FQDN'leri hem de işlevde IP adreslerini kullanmak, bu yüklemenin Canlı Etkinlikler/Akış da dahil sınırlı bir uç nokta kümesi için kullanımının kapsamının açıklarını sağlar. İşlevin yapılandırılmış olması, FQDN'ler için, istemci tarafından doğrudan listelenenlerle eşleşen bir DNS araması yapılmasına, yani kalan ad alanlarının DNS çözümlemesi değişmeden kalır.

Canlı Etkinlikler ve Akışla ilgili uç noktaların yükleme riskini sınırlamak isterseniz, **\*bu** riskin büyük bir çoğunun bulunduğu yapılandırmadan .azureedge.net etki alanını kaldırabilirsiniz çünkü bu, tüm Azure CDN müşterileri için kullanılan paylaşılan bir etki alanıdır. Bunun dezavantajı, dış kodlayıcı kullanan her olayın en iyi duruma tabi olmayacak olmasıdır, ancak bu kod içinde üretilen/düzenlenen Teams olur.

### <a name="3-configure-routing-on-the-vpn-to-enable-direct-egress"></a>3. Doğrudan çıkışı etkinleştirmek için VPN'de yönlendirmeyi yapılandırma

Son adım, trafiğin VPN'ye zorunlu geçiş yoluyla gönderilmeyeceğiden emin olmak için **geçerli CDN** Uç Noktaları listelerini VPN yapılandırmasına toplama konusunda açıklanan Canlı Etkinlik IP'leri için doğrudan bir yönlendirme eklemektir. Microsoft 365 uç noktaları için bunun nasıl gerçekleştirileceği hakkında ayrıntılı bilgi [VPN](#implement-vpn-split-tunneling) bölünmüş geçiş uygulama bölümünde bulunabilir ve işlem bu belgede listelenen Stream/Live Events IP'leri için tam olarak aynıdır.

VPN yapılandırması için yalnızca IP'ler (FQDN'ler değil) CDN Uç [noktaları](#gathering-the-current-lists-of-cdn-endpoints) toplama bağlantısında kullanılacaktır.

### <a name="stream--live-events-optimization-faq"></a>Canlı Etkinlikleri & İyileştirme hakkında SSS

#### <a name="will-this-send-all-my-traffic-to-the-service-direct"></a>Bu tüm trafiğimi doğrudan hizmete gönderecek mi?

Hayır, bu işlem Canlı Etkinlik veya Video akışı için gecikmeye duyarlı akış trafiğini doğrudan gönderir, diğer tüm trafik yayımlanmış IP'lere çözüm vermezse VPN bağlantısını kullanmaya devam eder.

#### <a name="do-i-need-to-use-the-ipv6-addresses"></a>IPv6 Adreslerini kullanmam gerekir mi?

Hayır, bağlantı yalnızca gerekli olduğu zaman IPv4 olabilir.

#### <a name="why-are-these-ips-not-published-in-the-microsoft-365-urlip-service"></a>Bu IP'ler neden URL/IP Microsoft 365 yayımlanmaz?

Microsoft'un, müşterilerin uç nokta kategorisine göre güvenli ve en iyi yönlendirmeyi uygulamak için bilgileri güvenilir bir şekilde kullanamalarını sağlamak için hizmette yer alan bilgilerin biçimi ve türüyle ilgili sıkı denetimler vardır.

Varsayılan **uç** nokta kategorisinin çeşitli nedenlerle sağlanan IP bilgileri yoktur (Varsayılan uç noktalar Microsoft'un denetimi dışında olabilir, çok sık değişebilir veya diğer öğelerle paylaşılan bloklar içinde olabilir). Bu nedenle, Varsayılan uç noktalar normal web trafiği gibi denetimli bir ara sunucuya FQDN yoluyla gönderilmek üzere tasarlanmıştır.

Bu durumda, yukarıdaki uç noktalar Canlı Etkinlikler veya Akış dışında Microsoft tarafından denetlenen olmayan öğeler tarafından kullanılmaktadır ve dolayısıyla trafik doğrudan gönderilmesi, bu IP'lere çözüm olan başka her şeyi de istemciden gönderme anlamına da gelecektir. Microsoft, küresel krizin benzersiz doğası gereği ve müşterilerimizin kısa vadeli  ihtiyaçlarını karşılamak için yukarıdaki bilgileri, müşterilerin uygun olduğunu göre kullanmaları için sağlanmıştır.

Microsoft, Live Events uç noktalarını gelecekte uç nokta kategorilerine dahil etmelerine izin verecek şekilde yeniden yapılandırmak için çalışıyor.

#### <a name="do-i-only-need-to-allow-access-to-these-ips"></a>Yalnızca bu IP'lere erişim izni vermem gerekir mi?

Hayır, HIZMETIN çalışması için URL/IP hizmetinin Gerekli olarak işaretlenmiş [uç noktalarına](urls-and-ip-address-ranges.md) erişim çok önemlidir. Ayrıca, Stream için işaretlenmiş isteğe bağlı uç noktalar (ID 41-45) gereklidir.

#### <a name="what-scenarios-will-this-advice-cover"></a>Bu öneri hangi senaryoları kapsıyor?

1. Teams Uygulaması'nın içinde üretilen canlı Teams.
2. Stream'de barındırılan içeriği görüntüleme
3. Dış cihaz (kodlayıcı) tarafından üretilen etkinlikler

#### <a name="does-this-advice-cover-presenter-traffic"></a>Bu öneri sunucu trafiğini kapsıyor mu?

Bu, yukarıda belirtilen tavsiyenin yalnızca hizmeti tüketenler için olduğunu ifade ederiz. Teams'den sunum yapmak, VPN bölmesini uygulama bölümünde açıklanan ayrıntılı VPN yükleme önerisini kullanarak URL/IP hizmeti satırı 11'de listelenen URL/IP hizmeti satır 11'de işaretlenmiş UDP uç noktalarını en iyi duruma getirmek için sunucu trafiğinin [akışını görebilir.](#implement-vpn-split-tunneling)

#### <a name="does-this-configuration-risk-traffic-other-than-live-events-amp-stream-being-sent-direct"></a>Bu yapılandırmada Canlı Etkinlikler Akışı dışında bir trafiğin doğrudan &amp; gönderilme riski var mı?

Evet, hizmetin bazı öğeleri için kullanılan paylaşılan FQDN'lerden dolayı bu kaçınılmazdır. Bu trafik genelde inceleme uygulayabilecek bir şirket ara sunucusu aracılığıyla gönderilir. VPN bölme senaryosunda, hem FQDN'ler hem de IP'ler kullanılarak bu risk en düşük kapsamda olacak, ancak yine de mevcut olacaktır. Müşteriler yükleme yapılandırmasından .azureedge.net etki alanını kaldırabilir ve bu riski minimum düzeyde azaltabilirsiniz ancak bu, Stream tarafından desteklenen Canlı Etkinlikler 'in (Teams zamanlanmış, dış kodlayıcı olayları, Teams Yammer zamanlanmış dış kodlayıcı olaylarında üretilen Yammer olayları ve Stream'den zamanlanmış veya isteğe bağlı olarak görüntüleme) yüklemesini kaldırır.**\*** Bu şekilde zamanlanan ve Teams etkinlikler etkilenmez.

## <a name="howto-guides-for-common-vpn-platforms"></a>Yaygın VPN platformları için HOWTO kılavuzları

Bu bölümde, bu  boşluğun en yaygın ortaklarından gelen trafiğin Microsoft 365 bölmek için ayrıntılı kılavuzların bağlantıları yer almaktadır. Kullanılabilir hale geldiyken başka kılavuzlar da eklemiz.

- **Windows 10 VPN istemcisi**: [Yerel VPN Microsoft 365 çalışanlara](/windows/security/identity-protection/vpn/vpn-office-365-optimization) yönelik trafiği en iyi Windows 10 getirme
- **Cisco Anyconnect**: [Anyconnect Bölünmüş Bağlantı'Tunnel Office365 için en iyi duruma getirme](https://www.cisco.com/c/en/us/support/docs/security/anyconnect-secure-mobility-client/215343-optimize-anyconnect-split-tunnel-for-off.html)
- **Palo Alto GlobalProtect**: [VPN Bölünmüş Microsoft 365 ile Trafiği En Tunnel Rotası'nın Dışında Tut](https://live.paloaltonetworks.com/t5/Prisma-Access-Articles/GlobalProtect-Optimizing-Office-365-Traffic/ta-p/319669)
- **F5 Networks BIG-IP APM**: [BIG-IP APM kullanırken](https://devcentral.f5.com/s/articles/SSL-VPN-Split-Tunneling-and-Office-365) MICROSOFT 365 VPN'ler aracılığıyla Uzak Erişim'de trafiği en iyi duruma getirme
- **Citrix Ağ Geçidi**: [Office365 için Citrix Gateway VPN bölünmüş geçidini en iyi duruma getirme](https://docs.citrix.com/citrix-gateway/13/optimizing-citrix-gateway-vpn-split-tunnel-for-office365.html)
- **Pulse Güvenli**: [VPN Titreşimi: Bölünmüş titreşimi yapılandırarak tüm Microsoft 365 yapılandırma](https://kb.pulsesecure.net/articles/Pulse_Secure_Article/KB44417)
- **Kontrol Noktası VPN**:[Diğer SaaS Uygulamaları için Tunnel Bölünmüş Microsoft 365 yapılandırma](https://supportcenter.checkpoint.com/supportcenter/portal?eventSubmit_doGoviewsolutiondetails=&solutionid=sk167000)

## <a name="vpn-split-tunneling-faq"></a>VPN Bölme Bölme SSS

Microsoft Güvenlik Ekibi, günümüzün benzersiz uzaktan çalışma senaryolarında modern güvenlik denetimleri elde etmek için güvenlik uzmanları ve BT'nin modern güvenlik denetimlerine ulaşmak için alternatif yollar yayımladığı blog gönderisinde, güvenlik uzmanlarının ve [BT'nin](https://www.microsoft.com/security/blog/2020/03/26/alternative-security-professionals-it-achieve-modern-security-controls-todays-unique-remote-work-scenarios/) günümüzün benzersiz uzaktan çalışma senaryolarında modern güvenlik denetimlerini elde etmenin önemli yollarını özetler. Buna ek olarak, bu konuda sık sorulan müşteri sorularının ve yanıtlarının bazıları aşağıda verilmiştir.

### <a name="how-do-i-stop-users-accessing-other-tenants-i-do-not-trust-where-they-could-exfiltrate-data"></a>Kullanıcıların diğer kiracılara erişimini nasıl durdurabilirim? Güvenim yok, ama verileri bu kullanıcılardan kesebilirler?

Yanıtı kiracı kısıtlamaları [adı verilen bir özelliktir](/azure/active-directory/manage-apps/tenant-restrictions). Kimlik doğrulama trafiği yüksek hacimde değildir ve özellikle gecikmeye duyarlı değildir, bu nedenle özelliğin uygulandığı şirket içi ara sunucuya VPN çözümü aracılığıyla gönderebilirsiniz. Burada, güvenilir kiracıların izin verme listesi korunur ve istemci güvenilir olmayan bir kiracıya belirteç almak için çalışırsa, ara sunucu yalnızca isteği reddettir. Kiracı güvenilirse, kullanıcının doğru kimlik bilgilerine ve haklara sahip olduğu bir belirteçe erişilebilir.

Dolayısıyla kullanıcı söz konusu kiracıya erişmek için geçerli bir belirteç olmadan yukarıdaki İşaretli uç noktaları en iyi duruma getirme bağlantısına TCP/UDP bağlantısı alsa da, oturum açamaz ve hiçbir veriye erişamaz/verileri taşıyamaz.

### <a name="does-this-model-allow-access-to-consumer-services-such-as-personal-onedrive-accounts"></a>Bu model kişisel kişisel hesap hesapları gibi tüketici hizmetlerine OneDrive olanak sağlar mı?

Hayır, değil, Microsoft 365 uç noktaları tüketici hizmetleriyle (örnek olarak Onedrive.live.com) aynı değildir, dolayısıyla bölünmüş bölme kullanıcının doğrudan tüketici hizmetlerine erişmesine izin vermez. Tüketici uç noktalarına yönelik trafik VPN trafiğini kullanmaya devam edecektir ve var olan ilkeler de uygulanır.

### <a name="how-do-i-apply-dlp-and-protect-my-sensitive-data-when-the-traffic-no-longer-flows-through-my-on-premises-solution"></a>Trafik artık şirket içi çözümümde akmasa da DLP'i nasıl uygulayabilirim ve hassas verilerimi nasıl koruyabilirim?

Hassas bilgilerin yanlışlıkla açıklanmasına yardımcı olmak için Microsoft 365 çok zengin bir [araç kümesi vardır](../compliance/information-protection.md). Uygunsuz şekilde depolanan veya paylaşılan hassas [bilgileri algılamak](../compliance/dlp-learn-about-dlp.md) için Teams ve SharePoint DLP özelliklerini kullanabilirsiniz. Uzaktan çalışma stratejinizin bir parçası kendi cihazınızı getirme (BYOD) ilkesi içeriyorsa, hassas verilerin kullanıcıların kişisel cihazlarına indirilsini önlemek için uygulama tabanlı Koşullu Erişim'i kullanabilirsiniz [](/azure/active-directory/conditional-access/app-based-conditional-access)

### <a name="how-do-i-evaluate-and-maintain-control-of-the-users-authentication-when-they-are-connecting-directly"></a>Doğrudan bağlanıyorken kullanıcının kimlik doğrulamasını nasıl değerlendirir ve denetimlerini sürdürürim?

Q1'de belirtilen kiracı kısıtlamaları özelliğine ek [olarak, kimlik](/azure/active-directory/conditional-access/overview) doğrulama isteğinin riskini dinamik olarak değerlendirmek ve uygun şekilde ifade etmek için koşullu erişim ilkeleri de uygulanabilir. Microsoft zaman içinde [Sıfır Güven modelinin](https://www.microsoft.com/security/zero-trust?rtc=1) uygulanmasını önermektedir ve mobil ve ilk bulutta denetimi korumak için Azure AD koşullu erişim ilkelerini kullanabiliriz. Koşullu erişim ilkeleri, kimlik doğrulama isteğinin başarılı olup olmadığı konusunda gerçek zamanlı olarak karar vermede kullanılabilir. Örneğin:

- Cihaz, bilinen/güvenilen/Etki Alanı katılmış cihaz mı?
- IP – Kimlik doğrulama isteği bilinen bir şirket IP adresinden mi geliyor? Yoksa güven güvenmemiz gereken bir ülkede mi?
- Uygulama – Kullanıcı bu uygulamayı kullanma yetkisine sahip mi?

Bundan sonra onaylama, MFA'ya yönelik kimlik doğrulamayı tetikleme veya bu ilkelere dayalı kimlik doğrulamayı engelleme gibi ilkeler tetikl olabilir.

### <a name="how-do-i-protect-against-viruses-and-malware"></a>Virüslere ve kötü amaçlı yazılımlara nasıl koruma yapabilirim?

Ayrıca, Microsoft 365 bu belgede ana hatlarıyla açıklanan, hizmetin kendi içinde yer alan çeşitli katmanlarda en iyi duruma getirme uç noktaları için [de koruma sağlar](/office365/Enterprise/office-365-malware-and-ransomware-protection). Burada da olduğu gibi, bu güvenlik öğelerini, protokolleri/trafiği tam olarak anlamayan cihazlarla uyumlu olarak yerine hizmette sağlamak çok daha verimlidir. Varsayılan olarak, SharePoint Online [bilinen kötü amaçlı yazılım için dosya karşıya yüklemelerini](../security/office-365-security/virus-detection-in-spo.md) otomatik olarak tarar

Yukarıda listelenen Exchange uç noktaları için, [Exchange Online Protection](/office365/servicedescriptions/exchange-online-protection-service-description/exchange-online-protection-service-description) ve [Microsoft 365 için Microsoft Defender](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description) hizmette trafiğin güvenliğini sağlama konusunda mükemmel bir iş yapar.

### <a name="can-i-send-more-than-just-the-optimize-traffic-direct"></a>Trafiği doğrudan en iyi duruma getirme hakkında daha fazla şey gönderebilir miyim?

En iyi duruma getirmek **için en iyi** duruma getirme uç noktalarına öncelik ver verilmesi gerekir, bu da düşük bir çalışma düzeyi için en yüksek avantaj sağlar. Öte yandan isterseniz, hizmetin çalışması için İşaretli uç noktalara izin ver gerekir ve gerekirse  kullanılan uç noktalar için IP adresleri sağlanır.

Ayrıca, genel web'e gözatma için merkezi güvenlik, denetim ve şirket ilkesi uygulaması sağlayan güvenli _web_ ağ geçitleri olarak adlandırılan bulut tabanlı ara sunucu/güvenlik çözümleri sunan çeşitli satıcılar da vardır. Bu çözümler yüksek düzeyde kullanılabilir, performansı yüksekse ve kullanıcıya yakın bulut tabanlı bir konumdan güvenli İnternet erişimi sağlayarak kullanıcılarınıza yakın bir konumda sağlandısa, bu çözümler ilk bulutta işe kullanılabilir. Bu işlem, genel göz atma trafiği için VPN/şirket ağına göz atma ihtiyacını ortadan kaldırır ve yine de merkezi güvenlik denetimine izin verir.

Ancak bu çözümler yerine hiç gönderilmese bile Microsoft, Trafiğin Microsoft 365 olarak en iyi duruma getirmenin doğrudan hizmete gönderilmelerini kesinlikle önermektedir.

Azure Sanal Ağına doğrudan erişim izni vermeyle ilgili kılavuz için bkz. [Azure VPN Ağ Geçidi Noktadan siteye kullanılarak uzaktan çalışma](/azure/vpn-gateway/work-remotely-support).

### <a name="why-is-port-80-required-is-traffic-sent-in-the-clear"></a>Bağlantı noktası 80 neden gereklidir? Trafik temiz olarak gönderilir mi?

Bağlantı noktası 80 yalnızca bağlantı noktası 443 oturumuna yeniden yönlendirme gibi şeyler için kullanılır, müşteri verileri gönderilmez veya bağlantı noktası 80 üzerinden erişilebilir olmaz. [Şifreleme](../compliance/encryption.md), toplu taşımadaki ve kalan verilerin ana hatlarını Microsoft 365 türleri ve medya trafiğini korumak için [](/microsoftteams/microsoft-teams-online-call-flows#types-of-traffic) SRTP'yi nasıl Teams ana hatlarıyla gösterir.

### <a name="does-this-advice-apply-to-users-in-china-using-a-worldwide-instance-of-microsoft-365"></a>Bu öneri dünya çapında bir örnek kullanan Çin'deki kullanıcılar için geçerli Microsoft 365?

**Hayır**, yok. Yukarıdaki tavsiyeye bir uyarı, Dünya çapında bir örnekle bağlantılı olan ÇÇY'de yer alan kullanıcılardır ve bu Microsoft 365. Bölgede çapraz ağ tıkanıklığı sık ortaya çıkma nedeniyle, doğrudan İnternet çıkış performansı değişken olabilir. Bölgedeki çoğu müşteri, trafiği şirket ağına getirmek için VPN kullanarak çalışır ve en iyi duruma getirilmiş bir yol üzerinden ülke dışına çıkışa benzer şekilde yetkili MPLS devrelerini kullanır. Bu durum, Çin kullanıcılarına performans iyileştirme [Microsoft 365 ilgili makalede daha ayrıntılı olarak açıklanmıştır](microsoft-365-networking-china.md).

### <a name="does-split-tunnel-configuration-work-for-teams-running-in-a-browser"></a>Bölünmüş yapılandırma yapılandırması bir tarayıcıda Teams için çalışıyor mu?

Evet, uyarılarla birlikte. en Teams işlevleri, Şu tarayıcılar için istemci [al'da listelenen tarayıcılarda Microsoft Teams](/microsoftteams/get-clients#web-client).

Buna ek Microsoft Edge **96** ve üzeri, Edge [WebRtcRespectOsRoutingTableEnabled](/deployedge/microsoft-edge-policies#webrtcrespectosroutingtableenabled) ilkesi etkinleştirerek eşler arası trafik için VPN bölünmüş trafiği destekler. Şu anda, diğer tarayıcılar eşler arası trafik için VPN bölünmüş eşlemeyi desteklemeyebilirsiniz.

## <a name="related-articles"></a>İlgili makaleler

[Genel bakış: VPN bölme bölme Microsoft 365](microsoft-365-vpn-split-tunnel.md)

[Microsoft 365 kullanıcıları için performans iyileştirmeyi iyileştirme](microsoft-365-networking-china.md)

[Günümüzün benzersiz uzaktan çalışma senaryolarında güvenlik uzmanlarının ve BT'nin modern güvenlik denetimlerini elde etmenin alternatif yolları (Microsoft Güvenlik Ekibi blogu)](https://www.microsoft.com/security/blog/2020/03/26/alternative-security-professionals-it-achieve-modern-security-controls-todays-unique-remote-work-scenarios/)

[Microsoft'ta VPN performansını geliştirme: otomatik Windows 10 izin vermek için VPN profillerini kullanma](https://www.microsoft.com/itshowcase/enhancing-remote-access-in-windows-10-with-an-automatic-vpn-profile)

[VPN ile çalışma: Microsoft uzaktan iş gücüne nasıl bağlı tutarak](https://www.microsoft.com/itshowcase/blog/running-on-vpn-how-microsoft-is-keeping-its-remote-workforce-connected/?elevate-lv)

[Microsoft 365 Ağ Bağlantısı İlkeleri](microsoft-365-network-connectivity-principles.md)

[Ağ Microsoft 365 değerlendirme](assessing-network-connectivity.md)

[Microsoft 365 ve performans ayarını yapılandırma](network-planning-and-performance.md)
