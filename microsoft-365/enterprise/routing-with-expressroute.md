---
title: Posta için ExpressRoute ile yönlendirme Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/3/2019
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: e1da26c6-2d39-4379-af6f-4da213218408
description: Bu makalede, iş yerleriyle birlikte kullanmak üzere Azure ExpressRoute yönlendirme gereksinimleri, devreleri ve yönlendirme etki Office 365.
ms.openlocfilehash: d6fab2dd9a7e7519eb1f56cebccaf345685cc0cd
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2022
ms.locfileid: "63019536"
---
# <a name="routing-with-expressroute-for-office-365"></a>Posta için ExpressRoute ile yönlendirme Office 365

*Bu makale hem son hem de Microsoft 365 Kurumsal hem de Office 365 Kurumsal.*

Trafiği Azure ExpressRoute kullanarak Office 365 yönlendirmeyi doğru anlamak için, çekirdek [ExpressRoute yönlendirme gereksinimlerini, ExpressRoute](/azure/expressroute/expressroute-routing) devrelerini ve yönlendirme etki alanlarını tam olarak [kavramanız gerekir](/azure/expressroute/expressroute-circuit-peerings). Bunlar, müşterilerin güven duyduğu ExpressRoute'u Office 365 temelleri ortaya koymaktadır.
  
Yukarıdaki makalelerde anlamamız gereken önemli öğelerden bazıları şunlardır:
  
- ExpressRoute devreleri belirli bir fiziksel altyapıya eşlenmemiştir, ancak Microsoft ve sizin adına bir eşleme sağlayıcısı tarafından tek bir eşleme konumda yapılan mantıksal bağlantıdır.

- ExpressRoute devresi ile müşterinin s-key arasında 1'e 1 eşleme vardır.

- Her devre iki bağımsız eşleme ilişkisini destekleye (Azure Özel eşliği ve Microsoft eşliği); Office 365 için Microsoft eşliği gerekir.

- Her devrenin, tüm eşleme ilişkileri arasında paylaşılan sabit bir bant genişliği vardır.

- ExpressRoute devresi için kullanılacak tüm genel IPv4 adresleri ve genel AS numaralarının size ait olduğu veya adres aralığının sahibi tarafından özel olarak size atandığı doğrulanması gerekir.

- Sanal ExpressRoute devreleri genel olarak yedeklidir ve standart BGP yönlendirme uygulamalarından sonra gelir. İşte bu nedenle, etkin/etkin bir yapılandırmada sağlayıcınıza çıkış başına iki fiziksel devre öneririz.

Desteklenen hizmetler [, maliyetler](/azure/expressroute/expressroute-faqs) ve yapılandırma ayrıntıları hakkında daha fazla bilgi için SSS sayfasına bakın. Microsoft [eşliği desteği sunan bağlantı sağlayıcılarının](/azure/expressroute/expressroute-locations) listesi hakkında bilgi için ExpressRoute konumları makalesine bakın. Kavramları daha kapsamlı açıklamaya yardımcı olmak için, Kanal 9'da yer alan Office 365 bölüm Azure [ExpressRoute](https://channel9.msdn.com/series/aer) eğitim serisi kaydettik.
  
## <a name="ensuring-route-symmetry"></a>Yönlendirme simetrisini sağlama

En Office 365 uç sunucularına hem İnternet hem de ExpressRoute'ta erişilebilir. Bu sunucular, her ikisi de kullanılabilir olduğunda ExpressRoute devreleri üzerinden şirket içi yönlendirmeyi tercih eder. Bu nedenle, ağdan gelen trafik İnternet devreleri üzerinden yönlendirmeyi tercih ederse, yönlendirme asimetrisi olabilir. Asimetrik yönlendirmeler soruna neden olur, çünkü durumli paket incelemesi yapan cihazlar giden paketlerden farklı bir yol izleyen dönüş trafiğini engelleyebilir.
  
İnternet veya ExpressRoute üzerinden Office 365 başlatmanızdan bağımsız olarak, kaynağın genel olarak yönlendirilebilir bir adres olması gerekir. Microsoft'la doğrudan eşliği olan çok sayıda müşteri için, müşteriler arasında yinelemenin mümkün olduğu özel adreslerin olması uygun değildir.
  
Aşağıda, şirket içi ağla Office 365 başlatıldığı senaryolar ve almaktadırlar. Ağ tasarımınızı basitleştirmek için, aşağıdakini İnternet yolu üzerinden yönlendirmenizi öneririz.
  
- Exchange Online SharePoint Online'dan şirket içi ana bilgisayar veya SharePoint Online'dan şirket içi ana bilgisayara gönderilen SharePoint Çevrimiçi Posta'ya posta gibi SMTP hizmetleri. SMTP protokolü, Microsoft'un ağı içinde ExpressRoute devreleri üzerinden paylaşılan yönlendirme ön ekleri ve ExpressRoute üzerinden şirket içi SMTP sunucularının reklamını yapmak, bu diğer hizmetlerde hatalara neden olur.

- Parola doğrulaması sırasında oturum açma için ADFS.

- [Exchange Server dağıtımları yapılandırma](/exchange/exchange-hybrid).

- [SharePoint karma arama sonuçları.](/SharePoint/hybrid/display-hybrid-federated-search-results-in-sharepoint-online)

- [SharePoint BCS.](/SharePoint/hybrid/deploy-a-business-connectivity-services-hybrid-solution)

- [Skype Kurumsal ve](/skypeforbusiness/hybrid/plan-hybrid-connectivity?bc=%2fSkypeForBusiness%2fbreadcrumb%2ftoc.json&toc=%2fSkypeForBusiness%2ftoc.json)/veya karma [Skype Kurumsal olabilir](/office365/servicedescriptions/skype-for-business-online-service-description/skype-for-business-online-features).

- [Skype Kurumsal Cloud Connector' seçin](/skypeforbusiness/skype-for-business-hybrid-solutions/plan-your-phone-system-cloud-pbx-solution/plan-skype-for-business-cloud-connector-edition).

Microsoft'un bu iki yönlü trafik akışlarında ağınıza geri yönlendirmesi için, şirket içi cihazlarınıza BGP yönlendirmeleri Microsoft'la paylaşılıyor olmalıdır. ExpressRoute üzerinden Microsoft'a yönlendirme ön ekleri tanıtıyorken, şu en iyi yöntemleri izleyebilirsiniz:

1) Aynı genel IP Adresi yönlendirme ön ekını genel İnternet'e ve ExpressRoute üzerinden tanıtma. ExpressRoute üzerinden Microsoft'a yapılan IP BGP Yol Öneki tanıtımları, İnternet'e hiç tanıt yer alan bir aralıktan önerilmez. Kullanılabilir IP Adresi alanı nedeniyle bunu yapmak mümkün yoksa, ExpressRoute üzerinden İnternet devrelerine göre daha belirli bir aralığı tanıtıyorsanız çok önemlidir.

2) ExpressRoute devresi başına ayrı NAT IP havuzlarını ve İnternet devrelerinize ayrı kullanın.

3) Microsoft'a tanıtılacak tüm yollar, yalnızca ExpressRoute üzerinden ağınıza tanıtılacak yönlendirmelerin değil, Microsoft'un ağının tüm sunucularından gelen ağ trafiğini çekecek. Yönlendirme senaryolarının tanımlandığı ve takımınız tarafından iyi anlaşılmış olduğu sunuculara yönlendirme yönlendirmeleri tanıtabilirsiniz. Ağdan birden çok ExpressRoute bağlantı hattına ayrı IP Adresi yönlendirme ön ekleri tanıtabilirsiniz.
  
## <a name="deciding-which-applications-and-features-route-over-expressroute"></a>Hangi uygulama ve özelliklerin ExpressRoute üzerinden yönlendir olmadığına karar verme

Microsoft eşleme yönlendirme etki alanını kullanarak eşleme ilişkisini yapılandırıyorsanız ve uygun erişim için onaylandırıldığında, ExpressRoute üzerinden kullanılabilen tüm PaaS ve SaaS hizmetlerini görebilirsiniz. ExpressRoute Office 365 tasarlanmış her hizmet [BGP toplulukları veya rota filtreleriyle](./bgp-communities-in-expressroute.md) [yönetilebilir](/azure/expressroute/how-to-routefilter-portal).
  
Microsoft eşliği kullanılarak Office 365 her eşleme özelliği, [Office 365](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2) uç noktaları makalesinde uygulama türüne ve FQDN'ye göre listelenir. Tablolarda FQDN'yi kullanmanın nedeni müşterilerin PAC dosyalarını veya diğer ara sunucu yapılandırmalarını kullanarak trafiği yönetmesine izin vermektir; PAC dosyaları gibi [](./managing-office-365-endpoints.md) uç noktaları Office 365 yönetme kılavuzumuza bakın.
  
Bazı durumlarda, bir veya birden çok alt FQDN'nin daha üst düzey joker etki alanına göre farklı tanıtıldı olduğu bir joker etki alanı kullandık. Bu çoğunlukla, joker karakterin hepsi ExpressRoute'a ve İnternet'e tanıt kullanılan uzun bir sunucu listesini temsil ederken, hedeflerin küçük bir alt kümesi yalnızca İnternet'e veya tersine tanıtıldı olduğunda olur. Farklılıkların yerini anlamak için aşağıdaki tablolara bakın.
  
Bu tabloda hem İnternet'e hem de Azure ExpressRoute'a tanıt kullanılan joker karakterli FQDN'lerin yanı sıra, yalnızca İnternet'e tanıtan alt FQDN'ler de görüntülenir.

|**ExpressRoute ve İnternet devrelere tanıtıldı joker etki alanı**|**Yalnızca İnternet devrelere tanıtan alt FQDN**|
|:-----|:-----|
|\*.microsoftonline.com  <br/> |click.email.microsoftonline.com  <br/> portal.microsoftonline.com  <br/> provisioningapi.microsoftonline.com  <br/> adminwebservice.microsoftonline.com  <br/> |
|\*.officeapps.live.com  <br/> |nexusRules.officeapps.live.com  <br/> nexus.officeapps.live.com  <br/> odc.officeapps.live.com  <br/> odc.officeapps.live.com  <br/> cdn.odc.officeapps.live.com  <br/> ols.officeapps.live.com  <br/> ocsredir.officeapps.live.com  <br/> ocws.officeapps.live.com  <br/> ocsa.officeapps.live.com  <br/> |

PAC dosyaları çoğunlukla, ExpressRoute'a tanıtilen uç noktalara yönelik ağ isteklerini doğrudan devreye ve diğer tüm ağ isteklerini ara sunucuya göndermek için kullanılır. Bunun gibi bir PAC dosyası yapılandırıyorsanız, PAC dosyanızı aşağıdaki sırada oluşturabilirsiniz:
  
1. Yukarıdaki tablonun 2. sütununda yer alan alt FQDN'leri PAC dosyanın üst kısmında yer alan ve trafiğin ara sunucuya doğru gönderilmesini sağlar. OFFICE 365 uç noktalarını yönetme makalemizde kullanabileceğiniz [örnek PAC dosyası sizin için hazırlanmıştır](./managing-office-365-endpoints.md).

2. Bu makalenin ilk bölümünün altında, ExpressRoute'a tanıtılacak şekilde [](./urls-and-ip-address-ranges.md) işaretlenmiş tüm FQDN'leri dahil edin; trafik doğrudan ExpressRoute devrenize gönderilebilir.

3. Diğer tüm ağ uç noktalarını veya kuralları bu iki girdinin altına dahil edin; trafik ara sunucuya doğru gönderilir.

Bu tabloda, yalnızca İnternet devrelere tanıtan joker karakterli etki alanlarının yanı sıra, Azure ExpressRoute ve İnternet devrelere tanıtan alt FQDN'ler de görüntülenir. Yukarıdaki PAC dosyanız için, aşağıdaki tablonun 2. sütunundaki FQDN'ler başvuru bağlantısında ExpressRoute'a tanıtıyor olarak listelenir; bu da, dosyadaki ikinci girdi grubuna dahil edilecekleri anlamına gelir.

|**Yalnızca İnternet devrelere tanıtıldı joker etki alanı**|**ExpressRoute ve İnternet devrelere tanıtilen alt FQDN**|
|:-----|:-----|
|\*.office.com  <br/> |\*.outlook.office.com  <br/> home.office.com  <br/> outlook.office.com  <br/> portal.office.com  <br/> www.office.com  <br/> |
|\*.office.net  <br/> |agent.office.net  <br/> |
|\*.office365.com  <br/> |outlook.office365.com  <br/> smtp.office365.com  <br/> |
|\*.outlook.com  <br/> |\*.protection.outlook.com  <br/> \*.mail.protection.outlook.com  <br/> autodiscover-\<tenant\>.outlook.com  <br/> |
|\*.windows.net  <br/> |login.windows.net  <br/> |

## <a name="routing-office-365-traffic-over-the-internet-and-expressroute"></a>İnternet Office 365 ExpressRoute üzerinden trafiği yönlendirme

Seçtiğiniz bir Office 365 yönlendirmek için, bir dizi önemli faktörü belirlemeniz gerekir.
  
1. Uygulamaya ne kadar bant genişliği gerekir? Mevcut kullanımı örneklemek, bunu kurumda belirlemek için tek güvenilir yöntemdir.

2. Ağ trafiğinin ağınızı hangi çıkış konumlarından ayrılmalarını istediğiniz. Ağ bağlantısının ağ gecikmesini en aza indirecek şekilde planla Office 365 çünkü bu performansı etkiler. Bu Skype Kurumsal ve video kullandığı için ağ gecikme süresine karşı duyarlıdır.

3. Ağ konumlarının hepsi veya bir alt kümesinin ExpressRoute'u kullanmalarını istiyorsanız.

4. Seçtiğiniz ağ sağlayıcısı ExpressRoute'u hangi konumlardan sunuyor?

Bu soruların yanıtlarını belirlerken, bant genişliği ve konum gereksinimlerini karşılayacak bir ExpressRoute devresi sabilirsiniz. Ağ planlamasıyla ilgili daha fazla yardım [Office 365 ayarlama](./network-planning-and-performance.md) kılavuzuna ve Microsoft'un ağ performans planlamasını nasıl işle ilgili [örnek olay incelemeye bakın](https://aka.ms/tunemsit).
  
### <a name="example-1-single-geographic-location"></a>Örnek 1: Tek coğrafi konum
  
Bu örnek, tek coğrafi konumu olan Trey Research adlı kurgusal bir şirketin senaryosudur.
  
Trey Research çalışanları İnternet'te yalnızca, güvenlik departmanının şirket ağıyla ISS'leri arasında yer alan giden ara sunucu çiftine açıkça izin veren hizmetlere ve web sitelerine bağlanmasına izin verilir.
  
Trey Research, Office 365 için Azure ExpressRoute kullanmayı planlıyor ve içerik teslim ağları gibi bazı trafiğin bu trafiğin bu bağlantı için ExpressRoute üzerinden yönlendirilene Office 365 tanır. Tüm trafik varsayılan olarak ara sunucu cihazlarına yönlendirildiklerine göre, bu istekler daha önce olduğu gibi çalışmaya devam edecektir. Trey Research, Azure ExpressRoute yönlendirme gereksinimlerini karşılay olduklarını belirlendikten sonra bir devre oluşturmak, yönlendirmeyi yapılandırmak ve yeni ExpressRoute devresini bir sanal ağa bağlamaya devam eder. Temel Azure ExpressRoute yapılandırması bir kez yapılandırmasını tamamlanın, Trey Research, müşteriye özgü verilerle trafiği kendi bağlantılarına yönelik doğrudan ExpressRoute üzerinden yönlendirmek için yayımlamız [#2 PAC](./managing-office-365-endpoints.md) Office 365 kullanır.
  
Aşağıdaki diyagramda da gösterildiği gibi, Trey Research yönlendirme ve giden ara sunucu yapılandırma değişikliklerinin bir bileşimini kullanarak trafiğin İnternet üzerinden Office 365 ve trafiğin bir alt kümesini de ExpressRoute üzerinden yönlendirme  gereksinimini karşılar.
  
1. [#2 PAC dosyasını kullanarak, trafiği](./managing-office-365-endpoints.md) farklı bir İnternet çıkış noktası üzerinden yönlendirerek bu kullanıcı için Azure ExpressRoute'u Office 365.

2. İstemciler Trey Research ara sunucularına yönelik varsayılan bir yönlendirmeyle yapılandırılır.

Bu örnek senaryoda Trey Research giden ara sunucu cihazı kullanıyor. Benzer şekilde, Office 365 için Azure ExpressRoute kullanmayan müşteriler, iyi bilinen yüksek hacimli uç noktaları isteyen trafiği inceleme maliyetine bağlı olarak trafiği bu tekniği kullanmak ister.
  
Exchange Online, SharePoint Online ve Skype Kurumsal Online için en yüksek hacimli FQDN'ler:
  
![ExpressRoute müşteri kenar ağı.](../media/dab8cc42-b1d6-46d6-b2f6-d70f9e16d5ea.png)
  
- outlook.office365.com, outlook.office.com

- \<tenant-name\>.sharepoint.com, \<tenant-name\>-my.sharepoint.com, \<tenant-name\>-\<app\>.sharepoint.com

- \*TCP Lync.com için IP aralıkları ile birlikte .Lync.com

- \*broadcast.officeapps.live.com, \*excel.officeapps.live.com, \*onenote.officeapps.live.com, \*powerpoint.officeapps.live.com, view.officeapps.live.com, \*visio.officeapps.live.com, \*word-edit.officeapps.live.com, \*\*word-view.officeapps.live.com, office.live.com

Aynı adreste [proxy ayarlarının dağıtımı ve](/archive/blogs/deploymentguys/windows-8-supporting-proxy-services-with-static-configurations-web-hosted-pac-files-and-domain-policy-configured-proxy) Windows 8 hakkında daha fazla bilgi Office 365 [proxy'niz](https://blogs.technet.com/b/onthewire/archive/2014/03/28/ensuring-your-office-365-network-connection-isn-t-throttled-by-your-proxy.aspx) tarafından kısıtilamamanızı sağlama.
  
Tek bir ExpressRoute devresinde, Trey Research için yüksek kullanılabilirlik söz olmaz. Trey'in ExpressRoute bağlantısına hizmet eden yedekli uç cihaz çiftinin başarısız olması durumunda, yük devretmek için fazladan bir ExpressRoute devresi olmaz. Bu da Trey Research'e karşı bir durumla karşıtlık içindedir çünkü İnternet'e başarısız olmak için el ile yeniden yapılandırma ve bazı durumlarda yeni IP adresleri gerekir. Trey yüksek kullanılabilirlik eklemek istiyorsa, en basit çözüm her konum için fazladan ExpressRoute devreleri eklemek ve devreleri etkin/etkin bir şekilde yapılandırmaktır.
  
## <a name="routing-expressroute-for-office-365-with-multiple-locations"></a>Birden çok konumu olan Office 365 için ExpressRoute'u yönlendirme

Son senaryo olan yönlendirme Office 365 ExpressRoute üzerinden yönlendirme, daha bile karmaşık bir yönlendirme mimarisine temel sağlar. Konumların sayısına, bu konumların bulunduğu kıtaların sayısına, ExpressRoute devrelerinin sayısına, bu şekilde devam eden bir trafiğin İnternet'e, bir de Trafiğin ExpressRoute üzerinden yönlendirilene kadar olması gerekir.
  
Birden çok coğrafyada birden çok konumu olan müşterilerin yanıtlaması gereken ek sorular:
  
1. Her konumda bir ExpressRoute devresi gerekli mi? Skype Kurumsal Online kullanıyorsanız veya SharePoint Online veya Exchange Online'un gecikme duyarlılığı konusunda endişeleniyorsanız her konumda yedekli bir çift etkin/etkin ExpressRoute devresi kullanılması önerilir. Daha fazla Skype Kurumsal için en iyi medya kalitesi ve ağ bağlantısı kılavuzuna bakın.

2. Belirli bir bölgede ExpressRoute devresi yoksa, hangi Office 365 yönlendirilebilir?

3. Çok sayıda küçük konumu olan ağlarda, trafiği birleştirme için tercih edilen yöntem nedir?

Bunların her biri, kendi ağına karar ve Microsoft'tan kullanılabilen seçenekleri değerlendirmenizi gerektiren benzersiz bir zorluk sağlar.

|**Dikkate Alınacak Nokta**|**Değerlendirilecek ağ bileşenleri**|
|:-----|:-----|
|Birden fazla konumda yer alan devreler  <br/> |Etkin/etkin bir şekilde yapılandırılmış en az iki devre öneririz.  <br/> Maliyet, gecikme süresi ve bant genişliği gereksinimlerini karşılaştırmanız gerekir.  <br/> Birden çok devreyle yönlendirmeyi yönetmek için BGP yönlendirme maliyetini, PAC dosyalarını ve NAT'yi kullanın.  <br/> |
|ExpressRoute devresi olmayan konumlardan yönlendirme  <br/> |Bu istekleri başlatan kişiye yakın bir çıkış ve DNS çözümlemesi Office 365.  <br/> Uzak ofislerin uygun uç noktayı bulmasını sağlayan DNS iletme kullanılabilir.  <br/> Uzak ofisteki istemcilerin, ExpressRoute devrelerine erişim sağlayan bir yönlendirmesi olması gerekir.  <br/> |
|Küçük ofis konsolidasyonu  <br/> |Kullanılabilir bant genişliği ve veri kullanımı dikkatle karşılaştırilmelidir.  <br/> |

> [!NOTE]
> Fiziksel konuma bakılmaksızın yönlendirme varsa, Microsoft İnternet yerine ExpressRoute'u tercih eder.
  
Benzersiz her ağ için, bu noktalar dikkate alınmalıdır. Aşağıda bir örnek verilmiştir.
  
### <a name="example-2-multi-geographic-locations"></a>Örnek 2: Birden çok coğrafi konum
  
Bu örnek, birden çok coğrafi konumu olan 'Humongous Insurance' adlı kurgusal bir şirketin senaryosudur.
  
Humongous Insurance'ın coğrafi olarak dünyanın her yanında ofisleri vardır. Azure ExpressRoute'u doğrudan ağ bağlantılarında Office 365 tutmak Office 365 için Azure ExpressRoute'u uygulamak istiyor. Humongous Insurance'ın ek olarak iki kıtada daha ofisleri vardır. ExpressRoute'un uygun olduğu uzak ofisteki çalışanların, ExpressRoute bağlantısını kullanmak için birincil tesislerden birini veya her ikisini birden geri yönlendirmesi gerekir.
  
Temel ilke, Office 365 kadar hızlı şekilde bir Microsoft veri merkezinden veri merkezi elde etmektir. Bu örnekte, Humongous Insurance'ın uzak ofislerinin Microsoft veri merkezlerine mümkün olan en hızlı şekilde herhangi bir bağlantıyla İnternet üzerinden mi yönlendir olduğuna yoksa uzak ofislerinin Microsoft veri merkezine gitmek için mümkün olan en hızlı şekilde bir ExpressRoute bağlantısıyla İnternet üzerinden mi yönlendireceğizlerine karar vermeleri gerekir.
  
Microsoft'un veri merkezleri, ağları ve uygulama mimarisi küresel olarak birbirinden ayrı iletişimleri alacak ve onlara mümkün olan en verimli yolla hizmet verecek şekilde tasarlanmıştır. Bu, dünyanın en büyük ağlarından biridir. Müşteri ağlarında Office 365 gerekenden daha uzun süre kalan müşteri hizmetleri için geçerli olan istekler, bu mimariden yararlanamaz.
  
Humongous Insurance'ın durumuna göre, ExpressRoute üzerinden kullanmayı planlandığı uygulamalara bağlı olarak ilerlemeleri gerekir. Örneğin, bu müşteriler bir Skype Kurumsal Online müşterisiyse veya dış Skype Kurumsal Online toplantılarına bağlanırken ExpressRoute bağlantısını kullanmayı planlıyorsanız, Skype Kurumsal Online medya kalitesi ve ağ bağlantısı kılavuzunda önerilen tasarım, üçüncü konum için ek bir ExpressRoute devresi sağlamaktır. Bu, ağ açısından daha pahalı olabilir; Bununla birlikte, istekleri Microsoft veri merkezi'ne teslimden önce bir kıtadan diğerine yönlendirme, Çevrimiçi toplantılar ve iletişimler sırasında Skype Kurumsal veya kullanılamaz bir deneyime neden olabilir.
  
Humongous Insurance Skype Kurumsal Online'ı kullanmayacaksa veya herhangi bir şekilde kullanmayı planlamayacaksa, Office 365'u da ExpressRoute bağlantısıyla kıtaya geri yönlendirmek uygun olabilir, ancak gereksiz gecikmeye veya TCP tıkanıkğına neden olabilir. Her iki durumda da, güvendiğiniz içerik teslim ağlarının avantajını elde etmek için İnternet'i yönlendirme trafiğinin yerel sitede İnternet Office 365 kullanılması önerilir.
  
![Birden çok coğrafi coğrafi olan ExpressRoute.](../media/98fdd883-2c5a-4df7-844b-bd28cd0b9f50.png)
  
Humongous Insurance birden çok coğrafi alanlı stratejisini planladığını düşünse de, devrenin boyutu, devre sayısı ve yük devretme gibi dikkate alınacak birçok şey vardır.
  
ExpressRoute tek konumda olurken ve devreyi kullanmaya çalışan birden çok bölge varsa, Humongous Insurance uzak ofisten Office 365'e bağlantıların genel merkeze en yakın Office 365 veri merkezine gönderildiğinden ve genel merkez tarafından alın sağlamak istiyor. Humongous Insurance bunu yapmak üzere, genel merkezin İnternet çıkış noktasına en yakın Office 365 ortamıyla uygun bağlantıyı kurmak için gereken gidiş/dönüş ve DNS araması sayısını azaltmayı sağlar. Bu, istemcinin yerel bir ön uç sunucusunu çözmesini ve kişinin Humongous Insurance'ın Microsoft'la eşliği olan yönetim merkezine yakın olması için Front-End sunucusunun bağlandığından sağlar. Ayrıca, Etki Alanı Adı [için Koşullu İteci Atamayı da öğrenebilirsiniz](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc794735(v=ws.10)).
  
Bu senaryoda, uzak ofisten gelen trafik Kuzey Amerika'daki Office 365 ön uç altyapısını çözüme kavuşturabilir ve Office 365 uygulamasının mimarisine uygun olarak arka uç sunuculara bağlanmak için Office 365 kullanabilir. Örneğin, Exchange Online Amerika'da bağlantıyı sonlandırabilir ve bu ön uç sunucuları kiracının bulunduğu her yerde arka uç posta kutusu sunucusuna bağlanabilir. Tüm hizmetler, çok dağıtılmış bir ön kapı hizmeti, unicast ve her türlücast hedeflerinden oluşur.
  
Humongous'un birden çok kıtada büyük ofisleri varsa, Skype Kurumsal Online gibi hassas uygulamalarda gecikmeyi azaltmak için bölge başına en az iki etkin/etkin devre kullanılması önerilir. Ofislerin hepsi tek bir kıtada bulunuyorsa veya gerçek zamanlı işbirliği kullanılıyorsa, birleştirilmiş veya dağıtılmış bir çıkış noktasına sahip olmak müşteriye özel bir karardır. Birden çok devre kullanılabilir olduğunda, herhangi bir devre kullanılamaz duruma geldiğinde BGP yönlendirmesi yük devretmeyi sağlar.
  
Örnek yönlendirme yapılandırmaları ve hakkında [daha fazla bilgi](/azure/expressroute/expressroute-config-samples-routing) alın [https://azure.microsoft.com/documentation/articles/expressroute-config-samples-nat/](/azure/expressroute/expressroute-config-samples-nat).
  
## <a name="selective-routing-with-expressroute"></a>ExpressRoute ile seçmeli yönlendirme

Test etme ve ExpressRoute'u kullanıcıların bir alt kümesine uygulama gibi çeşitli nedenlerle, ExpressRoute ile seçmeli yönlendirme gerekli olabilir. Müşterilerin ağ trafiğini ExpressRoute üzerinden seçmeli olarak Office 365 kullanabileceği çeşitli araçlar vardır:
  
1. **Yönlendirme filtreleme/ayrım**- BGP'nin ExpressRoute üzerinden alt ağların veya yönlendiricilerin bir alt kümesiyle bağlantı Office 365 yönlendirmelerine olanak sağlar. Bu seçim, müşteri ağı kesimine veya fiziksel ofis konumuna göre seçmeli olarak yol gösterir. Bu, EXPRESSRoute'un BGP cihazlarınız için kademeli olarak Office 365 yaygın bir uygulamadır ve yapılandırılmıştır.

2. **PAC dosyaları/URL'ler** - Office 365 FQDN'ler için belirli bir yola yönlendiren hedef ağ trafiğini yönlendirme. Bu seçim, PAC dosyası dağıtımında tanımlandık şekilde istemci bilgisayara [göre seçmeli olarak yollar](./managing-office-365-endpoints.md).

3. **Yönlendirme filtreleme** -  [Yönlendirme filtreleri](/azure/expressroute/how-to-routefilter-portal), Microsoft eşliği aracılığıyla desteklenen hizmetlerin bir alt kümesini kullanmanın bir yolu olur.

4. **BGP toplulukları** - [BG Office 365 P](./bgp-communities-in-expressroute.md) topluluk etiketlerine göre filtreleme, müşterinin hangi uygulamanın ExpressRoute'tan ve hangi uygulamaların ExpressRoute'tan ve hangi uygulamaların İnternet'den çapraz geçişden geçeceklerini belirlemesini sağlar.

İşte geri dönmek için kullanabileceğiniz kısa bir bağlantı: [https://aka.ms/erorouting]()
  
## <a name="related-topics"></a>İlgili Konular

[Ağ Office 365 değerlendirme](assessing-network-connectivity.md)
  
[Office 365 için Azure ExpressRoute](azure-expressroute.md)
  
[Daha fazla bağlantı için ExpressRoute Office 365 yönetme](managing-expressroute-for-connectivity.md)
  
[ExpressRoute ile ağ planlama Office 365](network-planning-with-expressroute.md)
  
[Proje için ExpressRoute'u Office 365](implementing-expressroute.md)
  
[Skype Kurumsal Online'da Medya Kalitesi ve Ağ Bağlantısı Performansı](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[Skype Kurumsal Online için a Skype Kurumsal iyileştirme](https://support.office.com/article/b363bdca-b00d-4150-96c3-ec7eab5a8a43)
  
[Skype Kurumsal Online'da ExpressRoute ve QoS](https://support.office.com/article/20c654da-30ee-4e4f-a764-8b7d8844431d)
  
[ExpressRoute kullanarak arama akışı](https://support.office.com/article/413acb29-ad83-4393-9402-51d88e7561ab)
  
[Daha fazla senaryo için ExpressRoute'ta BGP Office 365 kullanma](bgp-communities-in-expressroute.md)
  
[Office 365 ve performans geçmişini kullanarak performans ayarlamayı ayarlama](performance-tuning-using-baselines-and-history.md)
  
[Destek için performans sorunlarını giderme Office 365](performance-troubleshooting-plan.md)
  
[Office 365 URL'leri ve IP adresi aralıkları](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)
  
[Office 365 ve performans ayarını yapılandırma](network-planning-and-performance.md)
