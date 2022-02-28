---
title: Kullanıcı Office 365 yönetme
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: Kurumsal kuruluş ağ mimarisiyle Office 365 uç noktalarını yönetmeyi öğrenin.
ms.openlocfilehash: 96aa778316fcaa5994d408c869e8566e465a07d1
ms.sourcegitcommit: da11ffdf7a09490313dfc603355799f80b0c60f9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/26/2021
ms.locfileid: "62988849"
---
# <a name="managing-office-365-endpoints"></a>Kullanıcı Office 365 yönetme

Birden fazla ofis konumu olan ve WAN'a bağlanan çoğu kuruluşta, ağ bağlantısının yapılandırmasını Office 365 gerekir. Tüm güvenilen ağ isteklerini, ek paket düzeyindeki tüm Office 365 veya işlemeyi atlayarak, doğrudan güvenlik duvarınız üzerinden göndererek anızı en iyi duruma getirme. Bu işlem gecikme süresini ve çevre kapasite gereksinimlerinizi azaltır. Ağ Office 365 belirlemek kullanıcılarınız için en iyi performansı sağlamanın ilk adımıdır. Daha fazla bilgi için bkz[. Office 365 İlkeleri](microsoft-365-network-connectivity-principles.md).

Microsoft, yeni IP Adresi Office 365 URL Web Hizmeti'yi kullanarak ağ uç noktalarına Office 365 devam eden [değişikliklere erişmenizi öneririz](microsoft-365-ip-web-service.md).

Önemli ağ trafiğini nasıl yönetirken Office 365 bakılmaksızın, İnternet Office 365 gerektirir. Bağlantının gerekli olduğu diğer ağ uç noktaları Bu IP Adresi ve [URL Web hizmetine dahil Office 365 uç noktalar listelenmiştir](additional-office365-ip-addresses-and-urls.md).

Ağ uç noktalarının Office 365 kullanımı, kurumsal kuruluş ağ mimarinize bağlıdır. Bu makalede, kurumsal ağ mimarileriyle IP adreslerinin ve URL'lerin tümleştiri Office 365 yolları ana hatlarıyla açıklanmıştır. Hangi ağ isteklerine güveneceklerini seçmenin en kolay yolu, ofis konumlarının her birsinde otomatik ağ yapılandırmasını destekleyen SD-WAN Office 365 kullanmaktır.

## <a name="sd-wan-for-local-branch-egress-of-vital-office-365-network-traffic"></a>Önemli ağ trafiğinin yerel şube çıkışları için SD-WAN Office 365 çıkış

Her şubenin farklı konumlarında, trafiği uç nokta en iyi duruma Office 365 için yönlendirecek şekilde yapılandırılmış bir SD-WAN cihazı veya Kategorileri en iyi duruma getirme ve İzin ver kategorilerini doğrudan Microsoft'un ağına yönlendirebilirsiniz. Şirket içi veri merkezi trafiği, genel İnternet web siteleri trafiği ve Office 365 varsayılan kategori uç noktalarına yönelik trafik, daha önemli bir ağ çevreniz olan başka bir konuma gönderilir.

Microsoft, otomatik yapılandırmayı etkinleştirmek için SD-WAN sağlayıcılarıyla birlikte çalışıyor. Daha fazla bilgi için bkz. [Office 365 Ağ İş Ortağı Programı](microsoft-365-networking-partner-program.md).

<a name="pacfiles"> </a>
## <a name="use-a-pac-file-for-direct-routing-of-vital-office-365-traffic"></a>Önemli ve önemli trafiğin doğrudan yönlendiri için PAC Office 365 kullanma

PAC veya WPAD dosyalarını kullanarak, bir IP adresiyle ilişkilendirilmiş Office 365 ağ isteklerini yönetin. Ara sunucu veya çevre cihazı aracılığıyla gönderilen tipik ağ istekleri gecikme süresini artırmaktadır. SSL Kesme ve Denetleme en uzun gecikmeyi oluştururken, ara sunucu kimlik doğrulaması ve saygınlık araması gibi diğer hizmetler performansta kötü performansa ve kötü bir kullanıcı deneyimine neden olabilir. Buna ek olarak, bu çevre ağı cihazlarının tüm ağ bağlantısı isteklerini işlemesi için yeterli kapasite gerekir. Ağ istekleriyle ilgili doğrudan erişim için ara sunucu veya Office 365 atlamanızı öneririz.
  
[PowerShell Galerisi Get-PacFile](https://www.powershellgallery.com/packages/Get-PacFile), Office 365 IP Adresi ve URL Web hizmetinin en son ağ uç noktalarını okur ve örnek bir PAC dosyası oluşturan bir PowerShell betiğidir. Betiği, var olan PAC dosya yönetiminiz ile tümleştirin şekilde değiştirebilirsiniz.

![Güvenlik duvarları Office 365 ya da sunucu üzerinden bağlantı.](../media/34d402f3-f502-42a0-8156-24a7c4273fa5.png)

**Şekil 1 - Basit kurumsal ağ çevresi**

PAC dosyası, Şekil 1'in 1. noktasında web tarayıcılarına dağıtılır. Önemli bir ağ trafiğinin doğrudan çıkışını sağlayan bir PAC dosyası Office 365, ayrıca ağ çevre güvenlik duvarınızda bu URL'lerin arkasında yer alan IP adreslerine bağlantıya izin vermeniz gerekir. Bu, PAC dosyasında belirtilen aynı uç nokta Office 365 IP adresleri getirerek ve bu adreslere dayalı güvenlik duvarı ACL'leri oluşturarak yapılır. Şekil 1'de güvenlik duvarı 3. noktadadır.

Ayrıca, Yalnızca En İyi Duruma Getirme kategori uç noktaları için doğrudan yönlendirmeyi seçerseniz, gerekli tüm kategori uç noktalarının ara sunucuya gönderilebilir olması için, ilerideki işlemleri atlamak için ara sunucuda listelenmiş olması gerekir. Örneğin, SSL sonu ve Denetle ve Proxy Kimlik Doğrulaması, hem En İyi Duruma Getirme hem de İzin Ver kategori uç noktalarıyla uyumlu değildir. Proxy sunucusu Şekil 1'de 2. noktadadır.

Yaygın yapılandırma, ara sunucuya isabet alan ağ trafiğinin hedef IP adresleri için ara sunucudan gelen tüm giden trafiğin Office 365 izin verir. SSL Kesme ve Denetleme ile ilgili sorunlar hakkında bilgi için bkz. Trafiğin herhangi bir yerindeki üçüncü taraf [ağ cihazlarını veya Office 365 kullanma](https://support.microsoft.com/help/2690045/using-third-party-network-devices-or-solutions-with-office-365).

Bu betikte oluşturulacak iki Get-PacFile PAC dosyası vardır.

| Tür | Açıklama |
|:-----|:-----|
|**1** <br/> |Uç nokta trafiğini doğrudan ve diğer her şeyi ara sunucuya gönderin. <br/> |
|**2** <br/> |Uç nokta trafiğini doğrudan ve diğer her şeyi ara sunucuya En İyi Duruma Getirme ve İzin Ver'i gönderin. Bu tür, tüm desteklenen ExpressRoute trafiğini ExpressRoute ağ kesimlerine Office 365 diğer her şeyi ara sunucuya göndermek için de kullanılabilir. <br/> |

PowerShell betiğine çağrı yapmak için basit bir örnek şu şekildedir:

```powershell
Get-PacFile -ClientRequestId b10c5ed1-bad1-445f-b386-b919946339a7
```

Betiğin geçeceği birçok parametre vardır:

| Parametre | Açıklama |
|:-----|:-----|
|**ClientRequestId** <br/> |Bu gereklidir ve arama yapan istemci makinesi temsil eden web hizmetine geçirilen bir GUID'dir. <br/> |
|**Örnek** <br/> |Varsayılan Office 365 Dünya Çapında olan varsayılan hizmet örneğidir. Bu ayrıca web hizmetine de geçirr. <br/> |
|**TenantName** <br/> |Kiracı Office 365 adınız. Web hizmetine geçirilebilir ve bazı önemli URL'lerde değiştirilebilir Office 365 kullanılır. <br/> |
|**Tür** <br/> |Oluşturmak istediğiniz ara sunucu PAC dosyasının türü. <br/> |

Burada, ek parametrelerle PowerShell betiği çağrısının başka bir örneği ve almaktadır:

```powershell
Get-PacFile -Type 2 -Instance Worldwide -TenantName Contoso -ClientRequestId b10c5ed1-bad1-445f-b386-b919946339a7
```

## <a name="proxy-server-bypass-processing-of-office-365-network-traffic"></a>Ağ trafiği için ara sunucu Office 365'i atlama

Doğrudan giden trafik için PAC dosyaları kullanılmazken, yine de ara sunucuyu yapılandırarak ağ çevrenize işlemeyi atlamak istiyor olursanız. Bazı ara sunucu satıcıları, aşağıdaki adreslerde açıklandığı gibi bunun otomatik yapılandırmasını [Office 365 Ağ İş Ortağı Programı](microsoft-365-networking-partner-program.md).

Bunu el ile yapıyorsanız, grup IP Adresi ve URL Web Hizmeti'ne En İyi Duruma Getirme ve İzin Ver uç nokta kategorisi verilerini Office 365 VE PROXY sunucuyu bunlar için işlemeyi at edecek şekilde yapılandırmanız gerekir. En İyi Duruma Getirme ve İzin Ver kategori uç noktaları için SSL Sonu, Denetle ve Ara Sunucu Kimlik Doğrulaması'nın önüne geçebilirsiniz.
  
<a name="bkmk_changes"> </a>
## <a name="change-management-for-office-365-ip-addresses-and-urls"></a>IP adreslerini ve URL'leri Office 365 yönetimi

Ağ çevreniz için uygun yapılandırmayı seçmeye ek olarak, belirli uç noktaları kullanmak için bir değişiklik yönetim süreci Office 365 önemlidir. Bu uç noktalar düzenli olarak değişir ve değişiklikleri yönetmiyorsanız, yeni bir IP adresi veya URL eklendikten sonra engellenen veya performansı kötü olan kullanıcılarla sonuçlanmaz.

IP adreslerinde Office 365 URL'lerde genellikle her ayın son günü yakın bir yerde yayımlanır. Bazen işlem, destek veya güvenlik gereksinimleri nedeniyle zamanlamanın dışında bir değişiklik yayımlanır.

BIR IP adresi veya URL ekli olduğu için işlemnizi gerektiren bir değişiklik yayımlanırsa, bu uç noktada bir Office 365 hizmeti gelene kadar değişikliği yayımlayıncaya kadar 30 gün uyarı alırsınız. Bu, Geçerli Tarih olarak yansıtıldı. Bu bildirim dönemini hedeflese de, işlem, destek veya güvenlik gereksinimleri nedeniyle bu her zaman mümkün olamıyor olabilir. Kaldırılan IP adresleri veya URL'ler gibi hemen bir işlem gerektirmeyen değişiklikler veya daha az önemli değişiklikler, önceden bildirim içermez. Bu gibi örneklerde, Herhangi bir Geçerli Tarih sağlanacaktır. Hangi bildirimin sağlanmıştır, her değişiklikte hizmet için beklenen etkin tarihi listelemektedir.

### <a name="change-notification-using-the-web-service"></a>Web Hizmeti'i kullanarak bildirimi değiştirme

Değişiklik bildirimini almak Office 365 IP Adresi ve URL Web Hizmeti'ne gönderebilirsiniz. Office 365'e bağlanmak için kullanmakta olduğu uç noktaların sürümünü kontrol etmek için **saatte bir /version** web yöntemini Office 365. Bu sürüm kullanımda olan sürümle karşılaştırıldığında değişirse, **/endpoints** web yönteminden en son uç nokta verilerini allı ve isteğe bağlı olarak **/changes** web yönteminden farkları alırnız. Bulunan sürümde herhangi bir değişiklik yoksa **/endpoints** veya **/changes** web yöntemlerini çağırmanız gerekmez.

Daha fazla bilgi için IP [Office 365 URL Web Hizmeti'ne bakın](microsoft-365-ip-web-service.md).

### <a name="change-notification-using-rss-feeds"></a>RSS akışlarını kullanarak bildirimi değiştirme

Site Office 365 URL Adresi ve URL Web Hizmeti, web sitesinde abone olyabilirsiniz bir RSS akışı Outlook. IP adresleri ve URL'ler için, Office 365 örneğine özgü sayfalarda RSS URL'lerinin bağlantıları vardır. Daha fazla bilgi için IP [Office 365 URL Web Hizmeti'ne bakın](microsoft-365-ip-web-service.md).

### <a name="change-notification-and-approval-review-using-power-automate"></a>Onay bildirimini ve onay incelemesini değiştir'i Power Automate

Yine de her ay ortaya gelen ağ uç noktası değişiklikleri için el ile işleme gerektir olabileceğini anlıyoruz. Power Automate'i kullanarak size e-postayla haber veren bir akış oluşturabilir ve isteğe bağlı olarak ağ uç noktalarının değişiklikleri olduğunda değişiklikler Office 365 onay işlemini çalıştırabilirsiniz. Gözden geçirme tamamlandıktan sonra, akışın değişiklikleri güvenlik duvarınıza ve ara sunucu yönetim ekibine otomatik olarak e-postayla göndermesini sebilirsiniz.

Örnek ve şablon Power Automate bilgi için bkz. IP adreslerinde ve [URL'lerde Power Automate e-posta Office 365 e-posta alma](https://techcommunity.microsoft.com/t5/Office-365-Networking/Use-Microsoft-Flow-to-receive-an-email-for-changes-to-Office-365/td-p/240651).
  
<a name="FAQ"> </a>
## <a name="office-365-network-endpoints-faq"></a>Office 365 uç noktaları hakkında SSS

Ağ bağlantınız hakkında sık sorulan Office 365 bakın.
  
### <a name="how-do-i-submit-a-question"></a>Nasıl soru gönderim?

Makalenin yardımcı olup olmadığını belirtmek için en alttaki bağlantıya tıklayın ve başka sorular gönderin. Geri bildirimleri takip ediyor ve buradaki soruları en sık sorulan sorularla güncelleştir alıyoruz.
  
### <a name="how-do-i-determine-the-location-of-my-tenant"></a>Kiracının konumunu nasıl belirlerim?

 **Kiracı konumu** en iyi şekilde veri merkezi [haritamız kullanılarak belirlenir](./o365-data-locations.md).
  
### <a name="am-i-peering-appropriately-with-microsoft"></a>Microsoft ile uygun şekilde eşleme var mı?

 **Eşleme konumları,** Microsoft'la eşleme konusunda [daha ayrıntılı olarak açıklanmıştır](https://www.microsoft.com/peering).
  
Tüm dünyada 2500'den fazla ISS eşleme ilişkisi ve 70 bulunma noktasıyla, ağınızı bizim ağımıza sorunsuz bir şekilde ağın içinde ağın geçebilirsiniz. IsS'nizin eşleme ilişkisinin en iyi durumda olduğundan emin olmak için birkaç dakikanızı harcamanız zararı [olmaz, burada](/archive/blogs/onthewire/__guidance) ağımıza uygun, iyi ve iyi bir eşliği olan eldu bilgilerinden birkaç örnek verilmiştir.
  
<a name="bkmk_MissingIP"> </a>
### <a name="i-see-network-requests-to-ip-addresses-not-on-the-published-list-do-i-need-to-provide-access-to-them"></a>Yayımlanan listede yer alan IP adreslerine yapılan ağ istekleri görüyorum, bu adreslere erişim sağlamam gerekiyor mu?

Yalnızca doğrudan yönlendirmesi gereken Office 365 IP adresleri sağlaruz. Bu, ağ isteklerini göreceğiniz tüm IP adreslerinin kapsamlı bir listesi değildir. Microsoft'a ve üçüncü taraflara ait yayımlanmamış IP adreslerine yapılan ağ istekleriyle ilgili istekler vardır. Bu IP adresleri dinamik olarak oluşturulur veya değiştiklerinde zamanında bildirim verilmesini önleyen bir şekilde yönetilir. Güvenlik duvarınız bu ağ istekleri için FQDN'lere dayalı olarak erişime izin veramıyorsa, istekleri yönetmek için bir PAC veya WPAD dosyası kullanın.
  
Hakkında daha fazla bilgi Office 365 IP görüyor musunuz?
  
1. IP adresinin yayımlanmış daha geniş bir aralıkta yer alan BIR CIDR hesaplayıcısı kullanarak ( [örneğin, IPv4 veya IPv6](https://www.ipaddressguide.com/cidr) için [) olup olmadığını kontrol edin](https://www.ipaddressguide.com/ipv6-cidr). Örneğin 40.96.0.0/13, 40.96 ile eşleşmese de 40.103 IP Adresi 40.103.0.1'i içerir.
2. Bir whois sorgusuyla IP'nin bir iş ortağına [ait olup bakın](https://dnsquery.org/). Microsoft'a ait bir şirket içi iş ortağı olabilir. Birçok iş ortağı ağı uç noktası, IP adreslerinin _yayımlanmayacak_ varsayılan kategoriye ait olarak listelenir.
3. IP adresi, bu IP adresinin bir Office 365 veya bağımlılığın parçası olabilir. Office 365 uç noktası yayımlama, Microsoft ağ uç noktalarının hepsini içermez.
4. Sertifikayı kontrol edin. Tarayıcıyla, IP adresine bağlanmak için HTTPS://*\<IP_ADDRESS\>*'i kullanın ve IP adresiyle hangi etki alanlarının ilişkilendiril olduğunu anlamak için sertifikada listelenen etki alanlarını kontrol edin. Bu Microsoft'a ait bir IP adresi ise ve Office 365 IP adresleri listesinde yer alıyorsa, IP adresi büyük olasılıkla yayımlanmış IP bilgileri olmayan CDN gibi bir Microsoft *MSOCDN.NET CDN veya başka* bir Microsoft etki alanıyla ilişkilendirildi. Sertifikada etki alanının IP adresini listelediz talebimizi ifade eden bir etki alanı olduğunu bulursanız, lütfen bize yazın.

<a name="bkmk_cname"> </a>
### <a name="some-office-365-urls-point-to-cname-records-instead-of-a-records-in-the-dns-what-do-i-have-to-do-with-the-cname-records"></a>Bazı Office 365 URL'ler DNS'te A kayıtları yerine CNAME kayıtlarını işaret ettir. CNAME kayıtlarıyla ne yapabilirim?

İstemci bilgisayarların bir bulut hizmetine bağlanmak için bir veya birden çok IP adresi (es) içeren bir DNS A veya AAAA kayıt t)şapkası olması gerekir. Bir dosyada yer alan bazı URL Office 365 A veya AAAA kayıtları yerine CNAME kayıtlarını gösterir. Bu CNAME kayıtları aracıdır ve zincirde birkaç kayıt olabilir. Her zaman BIR IP Adresi için A veya AAAA kaydına çözüm bu kayıt çözümleyiciler. Örneğin, IP adresi bilgi dizisini sonuç olarak çözen aşağıdaki DNS _IP_1:_

```console
serviceA.office.com -> CNAME: serviceA.domainA.com -> CNAME: serviceA.domainB.com -> A: IP_1
```

Bu CNAME yönlendirmeleri DNS'nin normal bir parçasıdır ve istemci bilgisayarda saydam, proxy sunucularında saydamdır. Yük dengeleme, içerik teslim ağları, yüksek kullanılabilirlik ve hizmet olayı azaltma için kullanılırlar. Microsoft aracı CNAME kayıtlarını yayımlamaz, her zaman  değişiklik gösterir ve bunları ara sunucunuzda izin verilen şekilde yapılandırmanız gerekmemektedir.

Proxy sunucusu, yukarıdaki örnekte yer alan ilk URL'yi serviceA.office.com ve bu URL de yayında Office 365. Ara sunucu, bir IP Adresine bu URL'nin DNS çözümlemesini talep ediyor ve yanıt IP_1. Aracı CNAME yeniden yönlendirme kayıtlarını doğrulamaz.

Sabit kodlu yapılandırmalar veya dolaylı FQDN'Office 365 lere dayalı bir izin listesi kullanılması önerilmez, Microsoft tarafından desteklmemektedir ve bu yapılandırmaların müşteri bağlantı sorunlarına neden olduğu bilinmektedir. CNAME yeniden yönlendirmesini engellayan veya DNS girdilerini yanlış olarak çözen DNS çözümleri Office 365 DNS ileticileri aracılığıyla, DNS yeniden iletme etkinleştirildiğinde veya DNS kök ipuçları kullanılarak çözülebilir. Birçok üçüncü taraf ağ çevre ürünü, Office 365 IP Adresi ve URL Web hizmetini kullanarak yapılandırmalarına bir izin listesi eklemek için önerilen Office 365 uç noktasını [yerel olarak tümleştirin](microsoft-365-ip-web-service.md).

<a name="bkmk_akamai"> </a>
### <a name="why-do-i-see-names-such-as-nsatcnet-or-akadnsnet-in-the-microsoft-domain-names"></a>Microsoft etki alanı adlarında nsatc.net veya akadns.net adları neden görüyorum?

Office 365 diğer Microsoft hizmetleri bu deneyimi iyileştirmek için Akamai ve MarkMonitor gibi çeşitli üçüncü taraf hizmetlerini Office 365 kullanır. Size mümkün olan en iyi deneyimi vermeye devam etmek için, gelecekte bu hizmetleri değiştirebiliriz. Üçüncü taraf etki alanları posta hizmetleri gibi CDN veya coğrafi trafik yönetim hizmeti gibi bir hizmet barındırıyor olabilir. Şu anda kullanmakta olan hizmetlerden bazıları şunlardır:
  
.nsatc.net içeren istekler gördüğünüzde [MarkMonitor](https://www.markmonitor.com/) *\*kullanımdadır*. Bu hizmet kötü amaçlı davranışlara karşı korumak için etki alanı koruma ve izleme sağlar.
  
.exacttarget.com'e gelen istekleri gördüğünüzde *\**[ExactTarget](https://www.marketingcloud.com/) exacttarget.com. Bu hizmet kötü amaçlı davranışlara karşı e-posta bağlantısı yönetimi ve izleme sağlar.
  
Aşağıdaki FQDN'lerden birini içeren istekler gördüğünüzde [Akamai](https://www.akamai.com/) kullanımdadır. Bu hizmet coğrafi DNS ve içerik teslim ağı hizmetleri sunar.
  
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
### <a name="i-have-to-have-the-minimum-connectivity-possible-for-office-365"></a>E-Office 365 için mümkün olan en düşük Office 365

Aynı Office 365 İnternet üzerinden işlev yapmak için yerleşik bir hizmet paketi olduğu gibi, güvenilirlik ve kullanılabilirlik konusunda verilen sözler birçok standart İnternet hizmetlerinin kullanılabilir olduğu konusundadır. Örneğin, aynı modern İnternet hizmetlerinin çoğunu kullanmak için olduğu gibi, Office 365 ve CDN'ler gibi standart İnternet hizmetlerinin de kullanılabilir olması gerekir.

En Office 365 paketi ana hizmet alanlarına göre bozulmuştır. Bunlar bağlantı için seçmeli olarak etkinleştirilebilir ve herkes için bir bağımlılık olan ve her zaman gereken Ortak bir alan vardır.

| Hizmet Alanı | Açıklama |
|:-----|:-----|
|**Exchange** <br/> |Exchange Online ve Exchange Online Protection <br/> |
|**SharePoint** <br/> |SharePoint Online ve OneDrive İş <br/> |
|**Skype Kurumsal Online ve Microsoft Teams** <br/> |Skype Kurumsal ve Microsoft Teams <br/> |
|**Ortak** <br/> |Office 365 Pro, Office, Azure AD ve diğer yaygın ağ uç noktalarında kullanılabilir <br/> |

Temel İnternet hizmetlerinin yanı sıra, yalnızca işlevselliği tümleştirin için kullanılan üçüncü taraf hizmetleri de vardır. Tümleştirme için bunlar gerekli olmakla birlikte, Office 365 uç noktaları makalesinde isteğe bağlı olarak işaretlenir ve bu da uç nokta erişilebilir değilse hizmetin temel işlevselliğinin çalışmaya devam edeceğini gösterir. Gerekli olan tüm ağ uç noktalarında, gerekli öznitelik true olarak ayarlanır. İsteğe bağlı olan tüm ağ uç noktalarında false olarak ayarlanmış gerekli öznitelik vardır ve notlar özniteliği, bağlantı engellenirse beklemenız gereken eksik işlevselliği ayrıntılarıyla gösterir.
  
Office 365 kullanmaya çalışıyor ve üçüncü taraf hizmetlerinin erişilebilir olmadığını bulmaya çalışıyorsanız, bu makalede gerekli olarak işaretlenmiş tüm [FQDN'lere ara](urls-and-ip-address-ranges.md) sunucu ve güvenlik duvarı üzerinden izin verili olduğundan emin olun.
  
<a name="bkmk_consumer"> </a>
### <a name="how-do-i-block-access-to-microsofts-consumer-services"></a>Microsoft'un tüketici hizmetlerine erişimi nasıl engelleyebilirim?

Kiracı kısıtlamaları özelliği artık OneDrive, Hotmail ve Xbox.com gibi tüm Microsoft tüketici uygulamalarının (MSA uygulamaları) kullanımını engellemeyi destekler. Bu, login.live.com uç noktası için ayrı login.live.com kullanır. Daha fazla ayrıntı için bkz [. SaaS bulut uygulamalarına erişimi yönetmek için kiracı kısıtlamalarını kullanma](/azure/active-directory/manage-apps/tenant-restrictions#blocking-consumer-applications).

<a name="bkmk_IPOnlyFirewall"> </a>
### <a name="my-firewall-requires-ip-addresses-and-cannot-process-urls-how-do-i-configure-it-for-office-365"></a>Güvenlik duvarım IP Adresleri gerektirir ve URL'leri işleyememektedir. Bunu iş için nasıl Office 365?

Office 365 tüm gerekli ağ uç noktalarının IP adreslerini sağlamaz. Bazıları yalnızca URL olarak sağlanır ve varsayılan olarak kategorilere ayrılmıştır. Gereken varsayılan kategorideki URL'lere ara sunucu üzerinden izin ver gerekir. Proxy sunucunuz yoksa, kullanıcıların bir web tarayıcısının adres çubuğuna yazarak URL'ler için nasıl web istekleri yapılandırmış olduğunu nasıl yapılandırmış olduğunuz; kullanıcı da bir IP adresi sağlamaz. IP Office 365 sağ yapmayan varsayılan kategori URL'leri de aynı şekilde yapılandırıldı.

## <a name="related-topics"></a>İlgili konular

[Office 365 IP Adresi ve URL Web hizmeti](microsoft-365-ip-web-service.md)

[Microsoft Azure Merkezi IP Aralıkları](https://www.microsoft.com/download/details.aspx?id=41653)
  
[Microsoft Genel IP Alanı](https://www.microsoft.com/download/details.aspx?id=53602)
  
[Altyapı hizmetleri için ağ Microsoft Intune](/intune/get-started/network-infrastructure-requirements-for-microsoft-intune)
  
[ExpressRoute ve Power BI](https://powerbi.microsoft.com/documentation/powerbi-admin-power-bi-expressroute/)
  
[Office 365 URL'leri ve IP adresi aralıkları](urls-and-ip-address-ranges.md)
  
[Daha fazla bağlantı için ExpressRoute Office 365 yönetme](managing-expressroute-for-connectivity.md)
  
[Office 365 Bağlantısı İlkeleri](microsoft-365-network-connectivity-principles.md)
