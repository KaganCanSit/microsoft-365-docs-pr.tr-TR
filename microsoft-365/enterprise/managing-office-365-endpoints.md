---
title: Office 365 uç noktalarını yönetme
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 05/18/2022
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom:
- Adm_O365_Setup
- seo-marvel-apr2020
search.appverid: MOE150
ms.assetid: 99cab9d4-ef59-4207-9f2b-3728eb46bf9a
description: Office 365 uç noktalarının kurumsal kuruluşunuz ağ mimarinizle çalışması için nasıl yönetileceğini öğrenin.
ms.openlocfilehash: 68b778ac695c0b37b55dfe84414f72551d10ce68
ms.sourcegitcommit: 60970cf8a2cb451011c423d797dfb77925394f89
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2022
ms.locfileid: "65587478"
---
# <a name="managing-office-365-endpoints"></a>Office 365 uç noktalarını yönetme

Birden çok ofis konumu ve bağlantı WAN'ı olan çoğu kuruluş, Office 365 ağ bağlantısı için yapılandırmaya ihtiyaç duyar. Tüm güvenilen Office 365 ağ isteklerini doğrudan güvenlik duvarınız üzerinden göndererek ve tüm ek paket düzeyinde incelemeyi veya işlemeyi atlayarak ağınızı iyileştirebilirsiniz. Bu, gecikme süresini ve çevre kapasitesi gereksinimlerinizi azaltır. Office 365 ağ trafiğini belirlemek, kullanıcılarınız için en iyi performansı sağlamanın ilk adımıdır. Daha fazla bilgi için bkz. [Ağ Bağlantı İlkeleri Office 365](microsoft-365-network-connectivity-principles.md).

Microsoft, Office 365 [IP Adresi ve URL Web Hizmeti kullanarak Office 365](microsoft-365-ip-web-service.md) ağ uç noktalarına ve bu uç noktalarda devam eden değişikliklere erişmenizi önerir.

Önemli Office 365 ağ trafiğini nasıl yönettiğinize bakılmaksızın, Office 365 İnternet bağlantısı gerektirir. Bağlantının gerekli olduğu diğer ağ uç noktaları[, Office 365 IP Adresi ve URL Web hizmetine dahil olmayan ek uç noktalar](additional-office365-ip-addresses-and-urls.md) bölümünde listelenir.

Office 365 ağ uç noktalarını nasıl kullanacağınız, kuruluşunuzun ağ mimarisine bağlıdır. Bu makalede, kurumsal ağ mimarilerinin Office 365 IP adresleri ve URL'lerle tümleştirebileceği çeşitli yollar özetlenmektedir. Güvenecek ağ isteklerini seçmenin en kolay yolu, ofis konumlarınızın her birinde otomatik Office 365 yapılandırmasını destekleyen SD-WAN cihazlarını kullanmaktır.

## <a name="sd-wan-for-local-branch-egress-of-vital-office-365-network-traffic"></a>Önemli Office 365 ağ trafiğinin yerel dal çıkışı için SD-WAN

Her şube ofisi konumunda, uç nokta kategorisini iyileştir veya İyileştir ve İzin Ver kategorilerine Office 365 yönelik trafiği doğrudan Microsoft'un ağına yönlendirmek üzere yapılandırılmış bir SD-WAN cihazı sağlayabilirsiniz. Şirket içi veri merkezi trafiği, genel İnternet web siteleri trafiği ve Office 365 Varsayılan kategori uç noktalarına giden trafik gibi diğer ağ trafiği, daha önemli bir ağ çevrenize sahip olduğunuz başka bir konuma gönderilir.

Microsoft, otomatik yapılandırmayı etkinleştirmek için SD-WAN sağlayıcılarıyla birlikte çalışmaktadır. Daha fazla bilgi için bkz. [Office 365 Ağ İş Ortağı Programı](microsoft-365-networking-partner-program.md).

<a name="pacfiles"> </a>
## <a name="use-a-pac-file-for-direct-routing-of-vital-office-365-traffic"></a>Önemli Office 365 trafiğinin doğrudan yönlendirilmesi için PAC dosyası kullanma

Office 365 ile ilişkilendirilmiş ancak IP adresi olmayan ağ isteklerini yönetmek için PAC veya WPAD dosyalarını kullanın. Ara sunucu veya çevre cihazı aracılığıyla gönderilen tipik ağ istekleri gecikme süresini artırır. SSL Break ve Inspect en büyük gecikme süresini oluştururken, ara sunucu kimlik doğrulaması ve saygınlık araması gibi diğer hizmetler düşük performansa ve kötü bir kullanıcı deneyimine neden olabilir. Ayrıca, bu çevre ağ cihazlarının tüm ağ bağlantı isteklerini işlemek için yeterli kapasiteye ihtiyacı vardır. Doğrudan Office 365 ağ istekleri için ara sunucu veya denetim cihazlarınızı atlamanızı öneririz.
  
[PowerShell Galerisi Get-PacFile](https://www.powershellgallery.com/packages/Get-PacFile), Office 365 IP Adresi ve URL Web hizmetinden en son ağ uç noktalarını okuyan ve örnek bir PAC dosyası oluşturan bir PowerShell betiğidir. Betiği, mevcut PAC dosya yönetiminizle tümleştirileceği şekilde değiştirebilirsiniz.

> [!NOTE]
> Office 365 uç noktalarına doğrudan bağlantının güvenlik ve performans konuları hakkında daha fazla bilgi için bkz. [Ağ Bağlantısı İlkeleri'ni Office 365](microsoft-365-network-connectivity-principles.md).

![Güvenlik duvarları ve ara sunucular aracılığıyla Office 365 bağlanma.](../media/34d402f3-f502-42a0-8156-24a7c4273fa5.png)

**Şekil 1 - Basit kurumsal ağ çevresi**

PAC dosyası, Şekil 1'de 1. noktada web tarayıcılarına dağıtılır. Önemli Office 365 ağ trafiğinin doğrudan çıkışı için bir PAC dosyası kullanırken, ağ çevre güvenlik duvarınızdaki bu URL'lerin arkasındaki IP adreslerine de bağlantıya izin vermeniz gerekir. Bu, PAC dosyasında belirtilen aynı Office 365 uç nokta kategorileri için IP adresleri getirilerek ve bu adreslere göre güvenlik duvarı ACL'leri oluşturularak yapılır. Güvenlik duvarı Şekil 1'de 3. noktadır.

Ayrıca, Kategori uç noktalarını en iyi duruma getirme için yalnızca doğrudan yönlendirme yapmayı seçerseniz, daha fazla işlemeyi atlamak için ara sunucuya gönderdiğiniz tüm gerekli İzin ver kategori uç noktalarının ara sunucuda listelenmesi gerekir. Örneğin, SSL kesmesi ve İnceleme ve Proxy Kimlik Doğrulaması hem İyileştir hem de kategori uç noktalarına izin ver ile uyumlu değildir. Şekil 1'de ara sunucu 2. noktadır.

Yaygın yapılandırma, ara sunucuya isabet eden Office 365 ağ trafiği için hedef IP adresleri için ara sunucudan giden tüm trafiği işlemeden izin vermektir. SSL Kesme ve İnceleme ile ilgili sorunlar hakkında bilgi için bkz. [Office 365 trafiğinde üçüncü taraf ağ cihazlarını veya çözümlerini kullanma](https://support.microsoft.com/help/2690045/using-third-party-network-devices-or-solutions-with-office-365).

Get-PacFile betiğinin oluşturacağı iki tür PAC dosyası vardır.

| Tür | Açıklama |
|:-----|:-----|
|**1** <br/> |Uç nokta trafiğini en iyi duruma getir'i doğrudan ve diğer her şeyi proxy sunucusuna gönderin. <br/> |
|**2** <br/> |İyileştir ve Uç nokta trafiğine izin ver'i doğrudan ve diğer her şeyi ara sunucuya gönderin. Bu tür, Office 365 trafiği için desteklenen tüm ExpressRoute'u ExpressRoute ağ kesimlerine ve diğer her şeyi ara sunucuya göndermek için de kullanılabilir. <br/> |

PowerShell betiğini çağırmanın basit bir örneği aşağıda verilmiştir:

```powershell
Get-PacFile -ClientRequestId b10c5ed1-bad1-445f-b386-b919946339a7
```

Betike geçirebileceğiniz birçok parametre vardır:

| Parametre | Açıklama |
|:-----|:-----|
|**ClientRequestId** <br/> |Bu gereklidir ve çağrıyı yapan istemci makinesini temsil eden web hizmetine geçirilen bir GUID'dir. <br/> |
|**Örnek** <br/> |Varsayılan olarak Worldwide olarak gösterilen Office 365 hizmet örneği. Bu, web hizmetine de geçirilir. <br/> |
|**TenantName** <br/> |Office 365 kiracı adınız. Web hizmetine geçirilir ve bazı Office 365 URL'lerde değiştirilebilir parametre olarak kullanılır. <br/> |
|**Tür** <br/> |Oluşturmak istediğiniz ara sunucu PAC dosyasının türü. <br/> |

Ek parametrelerle PowerShell betiğini çağırmanın başka bir örneği aşağıda verilmiştir:

```powershell
Get-PacFile -Type 2 -Instance Worldwide -TenantName Contoso -ClientRequestId b10c5ed1-bad1-445f-b386-b919946339a7
```

## <a name="proxy-server-bypass-processing-of-office-365-network-traffic"></a>Office 365 ağ trafiğinin proxy sunucusu atlama işlemi

PAC dosyalarının doğrudan giden trafik için kullanılmadığı durumlarda, proxy sunucunuzu yapılandırarak ağ çevrenizdeki işlemeyi atlamak istersiniz. Bazı ara sunucu satıcıları[, Office 365 Ağ İş Ortağı Programı](microsoft-365-networking-partner-program.md) açıklandığı gibi bunun otomatik yapılandırmasını etkinleştirdi.

Bunu el ile yapıyorsanız, Office 365 IP Adresi ve URL Web Hizmeti'nden İyileştirme ve İzin Ver uç nokta kategorisi verilerini almanız ve proxy sunucunuzu bunlar için işlemeyi atlayacak şekilde yapılandırmanız gerekir. İyileştirme ve İzin Ver kategori uç noktaları için SSL Kesme ve İnceleme ve Ara Sunucu Kimlik Doğrulamasından kaçınmak önemlidir.
  
<a name="bkmk_changes"> </a>
## <a name="change-management-for-office-365-ip-addresses-and-urls"></a>Office 365 IP adresleri ve URL'ler için değişiklik yönetimi

Ağ çevreniz için uygun yapılandırmayı seçmeye ek olarak, Office 365 uç noktaları için bir değişiklik yönetimi süreci benimsemeniz de önemlidir. Bu uç noktalar düzenli olarak değişir ve değişiklikleri yönetmezseniz, yeni bir IP adresi veya URL eklendikten sonra kullanıcılar engellenmiş veya düşük performansla sonuçlanabilir.

Office 365 IP adreslerinde ve URL'lerde yapılan değişiklikler genellikle her ayın son gününe yakın yayımlanır. Bazen işletimsel, destek veya güvenlik gereksinimleri nedeniyle bu zamanlamanın dışında bir değişiklik yayımlanır.

BIR IP adresi veya URL eklendiği için işlem yapmanızı gerektiren bir değişiklik yayımlandığında, değişikliği yayımladığımızdan bu uç noktada bir Office 365 hizmeti olana kadar 30 gün bildirim almayı beklemeniz gerekir. Bu, Geçerlilik Tarihi olarak yansıtılır. Bu bildirim dönemini hedeflesek de operasyonel, destek veya güvenlik gereksinimleri nedeniyle her zaman mümkün olmayabilir. Kaldırılan IP adresleri veya URL'ler veya daha az önemli değişiklikler gibi bağlantıyı korumak için hemen eylem gerektirmeyen değişiklikler, önceden bildirim içermez. Bu örneklerde Geçerlilik Tarihi sağlanamaz. Hangi bildirimin sağlandığına bakılmaksızın, her değişiklik için beklenen hizmet etkin tarihini listeleyeceğiz.

### <a name="change-notification-using-the-web-service"></a>Web Hizmeti'ni kullanarak bildirimi değiştirme

Değişiklik bildirimi almak için Office 365 IP Adresi ve URL Web Hizmeti'ni kullanabilirsiniz. Office 365 bağlanmak için kullandığınız uç noktaların sürümünü denetlemek için **/version** web yöntemini saatte bir çağırmanızı öneririz. Bu sürüm kullanımdaki sürümle karşılaştırıldığında değişirse, **/endpoints** web yönteminden en son uç nokta verilerini almanız ve isteğe bağlı olarak **/changes** web yönteminden farkları almanız gerekir. Bulduğunuz sürümde herhangi bir değişiklik yapılmadıysa **/endpoints** veya **/changes** web yöntemlerini çağırmak gerekli değildir.

Daha fazla bilgi için bkz. [OFFICE 365 IP Adresi ve URL Web Hizmeti](microsoft-365-ip-web-service.md).

### <a name="change-notification-using-rss-feeds"></a>RSS akışlarını kullanarak bildirimi değiştirme

Office 365 IP Adresi ve URL Web Hizmeti, Outlook abone olabileceğiniz bir RSS akışı sağlar. IP adresleri ve URL'ler için Office 365 hizmet örneğine özgü sayfaların her birinde RSS URL'lerinin bağlantıları vardır. Daha fazla bilgi için bkz. [OFFICE 365 IP Adresi ve URL Web Hizmeti](microsoft-365-ip-web-service.md).

### <a name="change-notification-and-approval-review-using-power-automate"></a>Power Automate kullanarak bildirim ve onay incelemesini değiştirme

Her ay gelen ağ uç noktası değişiklikleri için el ile işlemeye ihtiyaç duyabileceğinizi anlıyoruz. Power Automate kullanarak sizi e-postayla bilgilendiren ve isteğe bağlı olarak Office 365 ağ uç noktalarının değişiklikleri olduğunda değişiklikler için bir onay işlemi çalıştıran bir akış oluşturabilirsiniz. Gözden geçirme tamamlandıktan sonra akışın değişiklikleri otomatik olarak güvenlik duvarınıza ve ara sunucu yönetim ekibinize e-postayla göndermesini sağlayabilirsiniz.

Power Automate örneği ve şablonu hakkında bilgi için bkz. [Office 365 IP adreslerinde ve URL'lerde yapılan değişiklikler için e-posta almak için Power Automate kullanma](https://techcommunity.microsoft.com/t5/Office-365-Networking/Use-Microsoft-Flow-to-receive-an-email-for-changes-to-Office-365/td-p/240651).
  
<a name="FAQ"> </a>
## <a name="office-365-network-endpoints-faq"></a>ağ uç noktalarını Office 365 hakkında SSS

Office 365 ağ bağlantısı hakkında sık sorulan bu sorulara bakın.
  
### <a name="how-do-i-submit-a-question"></a>Soru göndermek Nasıl yaparım??

Makalenin yararlı olup olmadığını belirtmek için alttaki bağlantıya tıklayın ve ek sorular gönderin. Geri bildirimleri izler ve buradaki soruları en sık sorulanlarla güncelleştiririz.
  
### <a name="how-do-i-determine-the-location-of-my-tenant"></a>Kiracımın konumunu belirlemek Nasıl yaparım??

 **Kiracı konumu** en iyi [veri merkezi haritamız](./o365-data-locations.md) kullanılarak belirlenir.
  
### <a name="am-i-peering-appropriately-with-microsoft"></a>Microsoft ile uygun şekilde eşleme yapıyorum mu?

 **Eşleme konumları** [Microsoft ile eşleme](https://www.microsoft.com/peering) konusunda daha ayrıntılı olarak açıklanmıştır.
  
Küresel olarak 2500'den fazla ISS eşleme ilişkisi ve 70'in üzerinde iletişim noktası ile ağınızdan bizim ağımıza sorunsuz bir şekilde erişim sağlamanız gerekir. ISS'nizin eşleme ilişkisinin en uygun olduğundan emin olmak için birkaç dakika harcamanın bir zararı olmaz. Aşağıda ağımıza yönelik iyi ve iyi olmayan eşleme izinlerinin [birkaç örneği](/archive/blogs/onthewire/__guidance) verilmiştir.
  
<a name="bkmk_MissingIP"> </a>
### <a name="i-see-network-requests-to-ip-addresses-not-on-the-published-list-do-i-need-to-provide-access-to-them"></a>Yayımlanan listede olmayan IP adreslerine yönelik ağ istekleri görüyorum, bunlara erişim sağlamam gerekiyor mu?

Yalnızca doğrudan yönlendirmeniz gereken Office 365 sunucuları için IP adresleri sağlarız. Bu, ağ isteklerini göreceğiniz tüm IP adreslerinin kapsamlı bir listesi değildir. Microsoft'a ve üçüncü tarafa ait, yayımdan kaldırılmış IP adreslerine yönelik ağ isteklerini görürsünüz. Bu IP adresleri dinamik olarak oluşturulur veya değiştiklerinde zamanında fark edilmesini önleyecek şekilde yönetilir. Güvenlik duvarınız bu ağ istekleri için FQDN'leri temel alarak erişime izin veremiyorsa, istekleri yönetmek için pac veya WPAD dosyası kullanın.
  
Daha fazla bilgi edinmek istediğiniz Office 365 ilişkilendirilmiş bir IP'ye mi bakın?
  
1. IP adresinin [IPv4](https://www.ipaddressguide.com/cidr) veya [IPv6](https://www.ipaddressguide.com/ipv6-cidr) için bunlar gibi bir CIDR hesaplayıcısı kullanarak daha büyük bir yayımlanmış aralığa eklenip eklenmediğini denetleyin. Örneğin, 40.96.0.0/13, 40.96'nın 40.103 ile eşleşmediği halde 40.103.0.1 IP Adresini içerir.
2. [Whois sorgusuyla](https://dnsquery.org/) IP'nin iş ortağına ait olup olmadığını görün. Microsoft'un sahip olduğu bir şirket içi iş ortağı olabilir. Birçok iş ortağı ağ uç noktası, IP adreslerinin yayımlanmadığı _varsayılan_ kategoriye ait olarak listelenir.
3. IP adresi Office 365 veya bağımlılığın parçası olmayabilir. Office 365 ağ uç noktası yayımlama, tüm Microsoft ağ uç noktalarını içermez.
4. Sertifikayı denetleyin. Bir tarayıcıyla  *HTTPS://\<IP_ADDRESS\>* kullanarak IP adresine bağlanın ve IP adresiyle ilişkili etki alanlarını anlamak için sertifikada listelenen etki alanlarını denetleyin. Office 365 IP adresleri listesinde değil de Microsoft'a ait bir IP adresiyse, IP adresi büyük olasılıkla MSOCDN.NET veya yayımlanmış IP bilgisi olmayan başka bir Microsoft etki alanı gibi bir Microsoft *CDN* ile ilişkilendirilir. Sertifikadaki etki alanının IP adresini listelediğimiz bir etki alanı olduğunu fark ederseniz lütfen bize bildirin.

<a name="bkmk_cname"> </a>
### <a name="some-office-365-urls-point-to-cname-records-instead-of-a-records-in-the-dns-what-do-i-have-to-do-with-the-cname-records"></a>Bazı Office 365 URL'leri, DNS'deki A kayıtları yerine CNAME kayıtlarını işaret eder. CNAME kayıtlarıyla ne yapmam gerekiyor?

İstemci bilgisayarların bir bulut hizmetine bağlanmak için bir veya daha fazla IP adresi içeren bir DNS A veya AAAA kaydına ihtiyacı vardır. Office 365 dahil edilen bazı URL'ler A veya AAAA kayıtları yerine CNAME kayıtlarını gösterir. Bu CNAME kayıtları aracıdır ve zincirde birkaç tane olabilir. Her zaman bir IP Adresi için A veya AAAA kaydına çözümlenir. Örneğin, sonunda IP adresi _IP_1_ çözümlenen aşağıdaki DNS kaydı serisini göz önünde bulundurun:

```console
serviceA.office.com -> CNAME: serviceA.domainA.com -> CNAME: serviceA.domainB.com -> A: IP_1
```

Bu CNAME yeniden yönlendirmeleri DNS'nin normal bir parçasıdır ve istemci bilgisayar için saydam ve ara sunuculara saydamdır. Bunlar yük dengeleme, içerik teslim ağları, yüksek kullanılabilirlik ve hizmet olayı azaltma için kullanılır. Microsoft aracı CNAME kayıtlarını yayımlamaz, bunlar herhangi bir zamanda değiştirilebilir ve bunları proxy sunucunuzda izin verilen şekilde yapılandırmanız gerekmez.

Ara sunucu, yukarıdaki örnekte serviceA.office.com olan ilk URL'yi doğrular ve bu URL Office 365 yayımlamaya dahil edilir. Proxy sunucusu, bu URL'nin DNS çözümlemesini bir IP Adresine gönderir ve IP_1 geri alır. Aracı CNAME yeniden yönlendirme kayıtlarını doğrulamaz.

Sabit kodlanmış yapılandırmalar veya dolaylı Office 365 FQDN'leri temel alan bir izin listesi kullanılması önerilmez, Microsoft tarafından desteklenmez ve müşteri bağlantı sorunlarına neden olduğu bilinmektedir. CNAME yeniden yönlendirmesini engelleyen veya Office 365 DNS girişlerini yanlış çözümleyen DNS çözümleri, DNS özyineleme etkinleştirilmiş DNS ileticileri aracılığıyla veya DNS kök ipuçlarını kullanarak çözülebilir. Birçok üçüncü taraf ağ çevre ürünü, önerilen Office 365 uç noktasını [Office 365 IP Adresi ve URL Web hizmetini](microsoft-365-ip-web-service.md) kullanarak yapılandırmalarına izin verilenler listesi eklemek için yerel olarak tümleştirir.

<a name="bkmk_akamai"> </a>
### <a name="why-do-i-see-names-such-as-nsatcnet-or-akadnsnet-in-the-microsoft-domain-names"></a>Microsoft etki alanı adlarında neden nsatc.net veya akadns.net gibi adlar görüyorum?

Office 365 ve diğer Microsoft hizmetleri, Office 365 deneyiminizi geliştirmek için Akamai ve MarkMonitor gibi çeşitli üçüncü taraf hizmetleri kullanır. Size mümkün olan en iyi deneyimi vermeye devam etmek için gelecekte bu hizmetleri değiştirebiliriz. Üçüncü taraf etki alanları, CDN gibi içeriği barındırabilir veya coğrafi trafik yönetimi hizmeti gibi bir hizmeti barındırabilir. Şu anda kullanımda olan hizmetlerden bazıları şunlardır:
  
*.nsatc.net içeren\** istekler gördüğünüzde [MarkMonitor](https://www.markmonitor.com/) kullanımdadır. Bu hizmet, kötü amaçlı davranışlara karşı koruma sağlamak için etki alanı adı koruması ve izleme sağlar.
  
*.exacttarget.com isteklerini\** gördüğünüzde [ExactTarget](https://www.marketingcloud.com/) kullanımda olur. Bu hizmet, kötü amaçlı davranışlara karşı e-posta bağlantısı yönetimi ve izleme sağlar.
  
Aşağıdaki FQDN'lerden birini içeren istekler gördüğünüzde [Akamai](https://www.akamai.com/) kullanılır. Bu hizmet coğrafi DNS ve içerik teslim ağı hizmetleri sunar.
  
```console
*.akadns.net
*.akam.net
*.akamai.com
*.akamai.net
*.akamaiedge.net
*.akamaihd.net
*.akamaized.net
*.edgekey.net
*.edgesuite.net
```

<a name="bkmk_thirdparty"> </a>
### <a name="i-have-to-have-the-minimum-connectivity-possible-for-office-365"></a>Office 365 için mümkün olan en düşük bağlantıya sahip olmak zorundayım

Office 365 İnternet üzerinden çalışması için oluşturulmuş bir hizmet paketi olduğundan, güvenilirlik ve kullanılabilirlik vaatleri birçok standart İnternet hizmetini temel alır. Örneğin, DNS, CRL ve CDN gibi standart internet hizmetlerinin Office 365 kullanılabilmesi için aynı modern internet hizmetlerinin çoğuna ulaşılabilmesi gerektiği gibi erişilebilir olması gerekir.

Office 365 paketi ana hizmet alanlarına ayrılmıştır. Bunlar bağlantı için seçmeli olarak etkinleştirilebilir ve herkes için bir bağımlılık olan ve her zaman gerekli olan ortak bir alan vardır.

| Hizmet Alanı | Açıklama |
|:-----|:-----|
|**Exchange** <br/> |Exchange Online ve Exchange Online Protection <br/> |
|**SharePoint** <br/> |SharePoint Online ve OneDrive İş <br/> |
|**Skype Kurumsal Çevrimiçi ve Microsoft Teams** <br/> |Skype Kurumsal ve Microsoft Teams <br/> |
|**Ortak** <br/> |Office 365 Pro Plus, tarayıcıda Office, Azure AD ve diğer ortak ağ uç noktaları <br/> |

Temel internet hizmetlerine ek olarak, yalnızca işlevselliği tümleştirmek için kullanılan üçüncü taraf hizmetler vardır. Bunlar tümleştirme için gerekli olsa da, Office 365 uç noktaları makalesinde isteğe bağlı olarak işaretlenir ve bu da uç nokta erişilebilir olmadığında hizmetin temel işlevselliğinin çalışmaya devam edeceği anlamına gelir. Gerekli olan tüm ağ uç noktalarının gerekli özniteliği true olarak ayarlanır. İsteğe bağlı herhangi bir ağ uç noktası gerekli özniteliği false olarak ayarlanır ve notes özniteliği, bağlantı engellenirse beklemeniz gereken eksik işlevselliği ayrıntılı olarak açıklar.
  
Office 365 kullanmaya çalışıyorsanız ve üçüncü taraf hizmetlere erişilemiyorsa, [bu makalede gerekli veya isteğe bağlı olarak işaretlenmiş tüm FQDN'lere ara sunucu ve güvenlik duvarı üzerinden izin verildiğinden emin olmak](urls-and-ip-address-ranges.md) istersiniz.
  
<a name="bkmk_consumer"> </a>
### <a name="how-do-i-block-access-to-microsofts-consumer-services"></a>Microsoft'un tüketici hizmetlerine erişimi Nasıl yaparım? engelleyemiyor musunuz?

Kiracı kısıtlamaları özelliği artık OneDrive, Hotmail ve Xbox.com gibi tüm Microsoft tüketici uygulamalarının (MSA uygulamaları) kullanımını engellemeyi destekliyor. Bu, login.live.com uç noktası için ayrı bir üst bilgi kullanır. Diğer ayrıntılar için bkz. [SaaS bulut uygulamalarına erişimi yönetmek için kiracı kısıtlamalarını kullanma](/azure/active-directory/manage-apps/tenant-restrictions#blocking-consumer-applications).

<a name="bkmk_IPOnlyFirewall"> </a>
### <a name="my-firewall-requires-ip-addresses-and-cannot-process-urls-how-do-i-configure-it-for-office-365"></a>Güvenlik duvarım IP Adresleri gerektiriyor ve URL'leri işleyemiyor. Nasıl yaparım? Office 365 için yapılandırılır?

Office 365 tüm gerekli ağ uç noktalarının IP adreslerini sağlamaz. Bazıları yalnızca URL'ler olarak sağlanır ve varsayılan olarak kategorilere ayrılır. Varsayılan kategoride yer alan ve gerekli olan URL'lere ara sunucu üzerinden izin verilmelidir. Proxy sunucunuz yoksa, kullanıcıların bir web tarayıcısının adres çubuğuna yazdığı URL'ler için web isteklerini nasıl yapılandırdığınıza bakın; kullanıcı da bir IP adresi sağlamaz. IP adresleri sağlamayan Office 365 varsayılan kategori URL'leri de aynı şekilde yapılandırılmalıdır.

## <a name="related-topics"></a>İlgili konular

[Office 365 IP Adresi ve URL Web hizmeti](microsoft-365-ip-web-service.md)

[Veri Merkezi IP Aralıklarını Microsoft Azure](https://www.microsoft.com/download/details.aspx?id=41653)
  
[Microsoft Genel IP Alanı](https://www.microsoft.com/download/details.aspx?id=53602)
  
[Microsoft Intune için ağ altyapısı gereksinimleri](/intune/get-started/network-infrastructure-requirements-for-microsoft-intune)
  
[ExpressRoute ve Power BI](https://powerbi.microsoft.com/documentation/powerbi-admin-power-bi-expressroute/)
  
[Office 365 URL'leri ve IP adresi aralıkları](urls-and-ip-address-ranges.md)
  
[Office 365 bağlantısı için ExpressRoute'u yönetme](managing-expressroute-for-connectivity.md)
  
[Office 365 Ağ Bağlantı İlkeleri](microsoft-365-network-connectivity-principles.md)
