---
title: Office 365 için ExpressRoute ile Yönlendirme
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: Bu makalede, Office 365 ile kullanılmak üzere Azure ExpressRoute yönlendirme gereksinimleri, bağlantı hatları ve yönlendirme etki alanları hakkında bilgi edinin.
ms.openlocfilehash: c63e3ae14c9b369265622f17c2e542818620aa3e
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65092921"
---
# <a name="routing-with-expressroute-for-office-365"></a>Office 365 için ExpressRoute ile Yönlendirme

*Bu makale hem Microsoft 365 Kurumsal hem de Office 365 Kurumsal için geçerlidir.*

Azure ExpressRoute kullanarak trafiği Office 365 yönlendirmeyi düzgün bir şekilde anlamak için, temel [ExpressRoute yönlendirme gereksinimlerini](/azure/expressroute/expressroute-routing) ve [ExpressRoute bağlantı hatlarını ve yönlendirme etki alanlarını](/azure/expressroute/expressroute-circuit-peerings) iyice kavramanız gerekir. Bunlar, Office 365 müşterilerin kullanacağı ExpressRoute'u kullanmaya yönelik temelleri ortaya koyuyor.
  
Yukarıdaki makalelerde anlamanız gereken bazı önemli öğeler şunlardır:
  
- ExpressRoute bağlantı hatları belirli fiziksel altyapıyla eşlenmez, ancak Microsoft ve sizin adına bir eşleme sağlayıcısı tarafından tek bir eşleme konumunda yapılan mantıksal bir bağlantıdır.

- ExpressRoute bağlantı hattı ile müşteri anahtarı arasında 1:1 eşlemesi vardır.

- Her bağlantı hattı iki bağımsız eşleme ilişkilerini destekleyebilir (Azure Özel eşleme ve Microsoft eşlemesi); Office 365 Için Microsoft eşlemesi gerekir.

- Her bağlantı hattı, tüm eşleme ilişkileri arasında paylaşılan sabit bir bant genişliğine sahiptir.

- ExpressRoute bağlantı hattı için kullanılacak tüm genel IPv4 adresleri ve genel AS numaraları, size ait olduğu veya yalnızca adres aralığının sahibi tarafından size atandığı doğrulanmalıdır.

- Sanal ExpressRoute bağlantı hatları genel olarak yedeklidir ve standart BGP yönlendirme uygulamalarını izler. Bu nedenle etkin/etkin bir yapılandırmada sağlayıcınıza çıkış başına iki fiziksel devre öneririz.

Desteklenen hizmetler, maliyetler ve yapılandırma ayrıntıları hakkında daha fazla bilgi için [SSS sayfasına](/azure/expressroute/expressroute-faqs) bakın. Microsoft eşleme desteği sunan bağlantı sağlayıcıları listesi hakkında bilgi için [ExpressRoute konumları makalesine](/azure/expressroute/expressroute-locations) bakın. Ayrıca, kavramları daha ayrıntılı bir şekilde açıklamaya yardımcı olmak için Channel 9'da Office 365 Eğitim serisi için 10 bölümlü bir [Azure ExpressRoute](https://channel9.msdn.com/series/aer) kaydettik.
  
## <a name="ensuring-route-symmetry"></a>Rota simetrisini sağlama

Office 365 ön uç sunucularına hem İnternet'te hem de ExpressRoute'ta erişilebilir. Bu sunucular, her ikisi de kullanılabilir olduğunda ExpressRoute bağlantı hatları üzerinden şirket içine geri yönlendirmeyi tercih eder. Bu nedenle, ağınızdan gelen trafik İnternet bağlantı hatlarınız üzerinden yönlendirmeyi tercih ederse rota asimetrisi olasılığı vardır. Durum bilgisi olan paket incelemesi gerçekleştiren cihazlar, takip edilen giden paketlerden farklı bir yol izleyen dönüş trafiğini engelleyebileceğinden, asimetrik yollar bir sorundur.
  
İnternet üzerinden veya ExpressRoute üzerinden Office 365 bağlantı başlatmanıza bakılmaksızın, kaynak genel olarak yönlendirilebilir bir adres olmalıdır. Birçok müşteri doğrudan Microsoft ile eşlendiğinde, müşteriler arasında yinelemenin mümkün olduğu özel adreslere sahip olmak mümkün değildir.
  
Aşağıda, Office 365'dan şirket içi ağınıza iletişimin başlatılacağı senaryolar yer alır. Ağ tasarımınızı basitleştirmek için aşağıdakileri İnternet yolu üzerinden yönlendirmenizi öneririz.
  
- Exchange Online kiracıdan şirket içi konağa gönderilen posta veya SharePoint Online'dan şirket içi konağa gönderilen SharePoint Çevrimiçi Posta gibi SMTP hizmetleri. SMTP protokolü, Microsoft'un ağı içinde ExpressRoute bağlantı hatları üzerinden paylaşılan yol ön eklerinden daha geniş bir şekilde kullanılır ve ExpressRoute üzerinden şirket içi SMTP sunucularının reklamı bu diğer hizmetlerde hatalara neden olur.

- Oturum açmak için parola doğrulaması sırasında ADFS.

- [Karma dağıtımları Exchange Server](/exchange/exchange-hybrid).

- [Federasyon karma arama SharePoint](/SharePoint/hybrid/display-hybrid-federated-search-results-in-sharepoint-online).

- [karma BCS SharePoint](/SharePoint/hybrid/deploy-a-business-connectivity-services-hybrid-solution).

- [Karma](/skypeforbusiness/hybrid/plan-hybrid-connectivity?bc=%2fSkypeForBusiness%2fbreadcrumb%2ftoc.json&toc=%2fSkypeForBusiness%2ftoc.json) ve/veya [Skype Kurumsal federasyonu Skype Kurumsal](/office365/servicedescriptions/skype-for-business-online-service-description/skype-for-business-online-features).

- [Bulut Bağlayıcısı'nı Skype Kurumsal](/skypeforbusiness/skype-for-business-hybrid-solutions/plan-your-phone-system-cloud-pbx-solution/plan-skype-for-business-cloud-connector-edition).

Microsoft'un bu çift yönlü trafik akışları için ağınıza geri yönlendirebilmesi için BGP'nin şirket içi cihazlarınıza yönlendirmeleri Microsoft ile paylaşılmalıdır. ExpressRoute üzerinden Yol ön eklerini Microsoft'a tanıttığınızda şu en iyi yöntemleri izlemeniz gerekir:

1) Aynı genel IP Adresi yol ön ekini genel İnternet'e ve ExpressRoute üzerinden tanıtmayın. ExpressRoute üzerinden Microsoft'a yönelik IP BGP Yol Ön Eki tanıtımlarının İnternet'e tanıtılmayan bir aralıktan olması önerilir. Kullanılabilir IP Adresi alanı nedeniyle bunu başarmak mümkün değilse, ExpressRoute üzerinden herhangi bir İnternet bağlantı hattından daha belirli bir aralığı tanıtmanızı sağlamak önemlidir.

2) ExpressRoute bağlantı hattı başına ayrı NAT IP havuzları kullanın ve İnternet bağlantı hatlarınızdan ayırın.

3) Microsoft'a tanıtılan tüm yollar, yalnızca ExpressRoute üzerinden ağınıza tanıtılan yolların değil, Microsoft'un ağındaki herhangi bir sunucudan gelen ağ trafiğini çeker. Rotaları yalnızca yönlendirme senaryolarının tanımlandığı ve ekibiniz tarafından iyi anlaşıldığı sunuculara tanıtın. Ağınızdan birden çok ExpressRoute bağlantı hattının her birinde ayrı IP Adresi yol ön eklerini tanıtın.
  
## <a name="deciding-which-applications-and-features-route-over-expressroute"></a>Hangi uygulamaların ve özelliklerin ExpressRoute üzerinden yönlendirildiğine karar verme

Microsoft eşleme yönlendirme etki alanını kullanarak bir eşleme ilişkisi yapılandırdığınızda ve uygun erişim için onaylandığında, ExpressRoute üzerinden sağlanan tüm PaaS ve SaaS hizmetlerini görebilirsiniz. ExpressRoute için tasarlanan Office 365 hizmetleri [BGP toplulukları](./bgp-communities-in-expressroute.md) veya [yol filtreleri](/azure/expressroute/how-to-routefilter-portal) ile yönetilebilir.
  
Microsoft eşlemesi kullanılarak kullanılabilen Office 365 özelliklerinin her biri uygulama türüne ve FQDN'ye göre [Office 365 uç noktaları makalesinde](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2) listelenmiştir. Tablolarda FQDN kullanmanın nedeni, müşterilerin PAC dosyalarını veya diğer ara sunucu yapılandırmalarını kullanarak trafiği yönetmesine izin vermektir. PAC dosyaları gibi [Office 365 uç noktalarını yönetme](./managing-office-365-endpoints.md) kılavuzumuza bakın.
  
Bazı durumlarda, bir veya daha fazla alt FQDN'nin üst düzey joker karakter etki alanından farklı şekilde tanıtıldığı bir joker etki alanı kullandık. Bu durum genellikle joker karakter ExpressRoute ve İnternet'e tanıtılan sunucuların uzun bir listesini temsil ederken, hedeflerin küçük bir alt kümesi yalnızca İnternet'e veya tersine tanıtılır. Farklılıkların nerede olduğunu anlamak için aşağıdaki tablolara bakın.
  
Bu tabloda, hem İnternet'e hem de Azure ExpressRoute'a tanıtılan joker karakter FQDN'lerinin yanı sıra yalnızca İnternet'e tanıtılan alt FQDN'ler görüntülenir.

|**ExpressRoute ve İnternet bağlantı hatlarına tanıtılan joker etki alanı**|**Yalnızca İnternet bağlantı hatlarına tanıtılan alt FQDN**|
|:-----|:-----|
|\*.microsoftonline.com  <br/> |click.email.microsoftonline.com  <br/> portal.microsoftonline.com  <br/> provisioningapi.microsoftonline.com  <br/> adminwebservice.microsoftonline.com  <br/> |
|\*.officeapps.live.com  <br/> |nexusRules.officeapps.live.com  <br/> nexus.officeapps.live.com  <br/> odc.officeapps.live.com  <br/> odc.officeapps.live.com  <br/> cdn.odc.officeapps.live.com  <br/> ols.officeapps.live.com  <br/> ocsredir.officeapps.live.com  <br/> ocws.officeapps.live.com  <br/> ocsa.officeapps.live.com  <br/> |

PAC dosyaları genellikle ExpressRoute tarafından tanıtılan uç noktalara doğrudan bağlantı hattına ve diğer tüm ağ isteklerine ağ istekleri göndermek için tasarlanmıştır. Bunun gibi bir PAC dosyası yapılandırıyorsanız PAC dosyanızı aşağıdaki sırayla yazın:
  
1. PAC dosyanızın üst kısmındaki yukarıdaki tabloda yer alan ikinci sütundaki alt FQDN'leri ekleyin ve trafiği ara sunucunuza gönderin. [Office 365 uç noktalarını yönetme](./managing-office-365-endpoints.md) makalemizde kullanabileceğiniz örnek bir PAC dosyası oluşturduk.

2. Trafiği doğrudan ExpressRoute bağlantı hattınıza göndererek ilk bölümün altındaki [bu makalede](./urls-and-ip-address-ranges.md) ExpressRoute'a tanıtılan tüm FQDN'leri ekleyin.

3. Trafiği ara sunucunuza göndererek bu iki girdinin altına diğer ağ uç noktalarını veya kuralları ekleyin.

Bu tabloda, yalnızca Azure ExpressRoute ve İnternet bağlantı hatlarına tanıtılan alt FQDN'lerin yanı sıra İnternet bağlantı hatlarına tanıtılan joker etki alanları görüntülenir. Yukarıdaki PAC dosyanız için, aşağıdaki tabloda yer alan 2. sütundaki FQDN'ler başvurulan bağlantıda ExpressRoute'a tanıtılıyor olarak listelenir ve bu da dosyadaki ikinci girdi grubuna dahil edilecekleri anlamına gelir.

|**Yalnızca İnternet bağlantı hatlarına tanıtılan joker etki alanı**|**ExpressRoute ve İnternet bağlantı hatlarına tanıtılan alt FQDN**|
|:-----|:-----|
|\*.office.com  <br/> |\*.outlook.office.com  <br/> home.office.com  <br/> outlook.office.com  <br/> portal.office.com  <br/> www.office.com  <br/> |
|\*.office.net  <br/> |agent.office.net  <br/> |
|\*.office365.com  <br/> |outlook.office365.com  <br/> smtp.office365.com  <br/> |
|\*.outlook.com  <br/> |\*.protection.outlook.com  <br/> \*.mail.protection.outlook.com  <br/> autodiscover-\<tenant\>.outlook.com  <br/> |
|\*.windows.net  <br/> |login.windows.net  <br/> |

## <a name="routing-office-365-traffic-over-the-internet-and-expressroute"></a>İnternet ve ExpressRoute üzerinden trafik Office 365 yönlendirme

Seçtiğiniz Office 365 uygulamasına yönlendirmek için bir dizi önemli faktörü belirlemeniz gerekir.
  
1. Uygulamanın ne kadar bant genişliği gerektireceği. Mevcut kullanımı örneklemek, kuruluşunuzda bunu belirlemek için tek güvenilir yöntemdir.

2. Ağ trafiğinin ağınızdan ayrılmasını istediğiniz çıkış konumları. Office 365 bağlantı için ağ gecikme süresini en aza indirmeyi planlamanız gerekir, bu da performansı etkiler. Skype Kurumsal gerçek zamanlı ses ve video kullandığından, düşük ağ gecikme süresine duyarlıdır.

3. Ağ konumlarınızın tümünün veya bir alt kümesinin ExpressRoute kullanmasını istiyorsanız.

4. Seçtiğiniz ağ sağlayıcısının ExpressRoute'u hangi konumlardan sunduğu.

Bu soruların yanıtlarını belirledikten sonra bant genişliği ve konum gereksinimlerini karşılayan bir ExpressRoute bağlantı hattı sağlayabilirsiniz. Daha fazla ağ planlama yardımı için [Office 365 ağ ayarlama kılavuzuna](./network-planning-and-performance.md) ve [Microsoft'un ağ performansı planlamasını nasıl işlediğine ilişkin örnek olay incelemesine](https://aka.ms/tunemsit) bakın.
  
### <a name="example-1-single-geographic-location"></a>Örnek 1: Tek coğrafi konum
  
Bu örnek, tek bir coğrafi konumu olan Trey Research adlı kurgusal bir şirket için bir senaryodur.
  
Trey Research çalışanlarının yalnızca, güvenlik departmanının şirket ağı ile ISS'leri arasında yer alan giden proxy çiftinde açıkça izin verdiği internet üzerindeki hizmetlere ve web sitelerine bağlanmasına izin verilir.
  
Trey Research, Office 365 için Azure ExpressRoute kullanmayı planlıyor ve içerik teslim ağlarına yönelik trafik gibi bazı trafiğin Office 365 bağlantı için ExpressRoute üzerinden yönlendirilemeyeceğini algılar. Tüm trafik zaten varsayılan olarak ara sunucu cihazlarına yönlendirdiğinden, bu istekler daha önce olduğu gibi çalışmaya devam eder. Trey Research, Azure ExpressRoute yönlendirme gereksinimlerini karşılayabileceklerini belirledikten sonra bir bağlantı hattı oluşturmaya, yönlendirmeyi yapılandırmaya ve yeni ExpressRoute bağlantı hattını bir sanal ağa bağlamaya devam eder. Temel Azure ExpressRoute yapılandırması gerçekleştikten sonra Trey Research, Office 365 bağlantıları için trafiği müşteriye özgü verilerle doğrudan ExpressRoute üzerinden yönlendirmek için [yayımladığımız #2 PAC dosyasını](./managing-office-365-endpoints.md) kullanır.
  
Aşağıdaki diyagramda gösterildiği gibi Trey Research, yönlendirme ve giden ara sunucu yapılandırma değişikliklerinin bir bileşimini kullanarak Office 365 trafiği İnternet üzerinden yönlendirme gereksinimini ve ExpressRoute üzerinden trafiğin bir alt kümesini karşılayabilmiştir.
  
1. [2. PAC dosyasını](./managing-office-365-endpoints.md) kullanarak trafiği Office 365 için Azure ExpressRoute için ayrı bir İnternet çıkış noktası üzerinden yönlendirmek üzere yayımlıyoruz.

2. İstemciler Trey Research'ün proxy'lerine doğru varsayılan bir yol ile yapılandırılır.

Bu örnek senaryoda Trey Research bir giden ara sunucu cihazı kullanıyor. Benzer şekilde, Office 365 için Azure ExpressRoute kullanmayan müşteriler, iyi bilinen yüksek hacimli uç noktaları hedefleyen trafiği inceleme maliyetine göre trafiği yönlendirmek için bu tekniği kullanmak isteyebilir.
  
Exchange Online, SharePoint Online ve Skype Kurumsal Online için en yüksek hacimli FQDN'ler şunlardır:
  
![ExpressRoute müşteri uç ağı.](../media/dab8cc42-b1d6-46d6-b2f6-d70f9e16d5ea.png)
  
- outlook.office365.com, outlook.office.com

- \<tenant-name\>.sharepoint.com, \<tenant-name\>-my.sharepoint.com, \<tenant-name\>-\<app\>.sharepoint.com

- \*TCP olmayan trafiğin IP aralıklarıyla birlikte .Lync.com

- \*broadcast.officeapps.live.com, \*excel.officeapps.live.com, \*onenote.officeapps.live.com, \*powerpoint.officeapps.live.com, \*view.officeapps.live.com, \*visio.officeapps.live.com, \*word-edit.officeapps.live.com, \*word-view.officeapps.live.com, office.live.com

[Windows 8'da ara sunucu ayarlarını dağıtma ve yönetme ve Office 365](/archive/blogs/deploymentguys/windows-8-supporting-proxy-services-with-static-configurations-web-hosted-pac-files-and-domain-policy-configured-proxy) [proxy'niz tarafından kısıtlanmamasını sağlama](https://blogs.technet.com/b/onthewire/archive/2014/03/28/ensuring-your-office-365-network-connection-isn-t-throttled-by-your-proxy.aspx) hakkında daha fazla bilgi edinin.
  
Tek bir ExpressRoute bağlantı hattıyla Trey Research için yüksek kullanılabilirlik yoktur. Trey'in ExpressRoute bağlantısına hizmet veren yedekli uç cihaz çiftinin başarısız olması durumunda yük devredecek fazladan bir ExpressRoute bağlantı hattı yoktur. İnternet'e yük devretmek için el ile yeniden yapılandırma ve bazı durumlarda yeni IP adresleri gerekeceği için Trey Research bu durumda kalır. Trey yüksek kullanılabilirlik eklemek istiyorsa, en basit çözüm her konum için fazladan ExpressRoute bağlantı hatları eklemek ve devreleri etkin/etkin bir şekilde yapılandırmaktır.
  
## <a name="routing-expressroute-for-office-365-with-multiple-locations"></a>Birden çok konuma sahip Office 365 için ExpressRoute'u yönlendirme

Son senaryo, trafiği ExpressRoute üzerinden yönlendirmek Office 365 daha karmaşık yönlendirme mimarisinin temelini oluşturur. Konum sayısından, söz konusu konumların bulunduğu kıta sayısından, ExpressRoute bağlantı hatlarının sayısından vb. bağımsız olarak, trafiğin bir kısmını İnternet'e ve bazı trafiği ExpressRoute üzerinden yönlendirebilmek gerekir.
  
Birden çok coğrafyada birden çok konumu olan müşteriler için yanıtlanması gereken ek sorular şunlardır:
  
1. Her konumda bir ExpressRoute bağlantı hattına ihtiyacınız var mı? Skype Kurumsal Online kullanıyorsanız veya SharePoint Online veya Exchange Online için gecikme duyarlılığıyla ilgileniyorsanız, her konumda yedekli bir çift etkin/etkin ExpressRoute devresi önerilir. Daha fazla ayrıntı için medya kalitesi ve ağ bağlantısı Skype Kurumsal kılavuzuna bakın.

2. ExpressRoute bağlantı hattı belirli bir bölgede kullanılamıyorsa, hedeflenen trafiğin Office 365 nasıl yönlendirilmesi gerekir?

3. Çok sayıda küçük konumu olan ağlarda trafiği birleştirmek için tercih edilen yöntem hangisidir?

Bunların her biri, kendi ağınızı ve Microsoft'un sunduğu seçenekleri değerlendirmenizi gerektiren benzersiz bir zorluk sunar.

|**Dikkate**|**Değerlendirilecek ağ bileşenleri**|
|:-----|:-----|
|Birden fazla konumdaki bağlantı hatları  <br/> |Etkin/etkin bir şekilde yapılandırılmış en az iki bağlantı hattı öneririz.  <br/> Maliyet, gecikme süresi ve bant genişliği gereksinimleri karşılaştırılmalıdır.  <br/> Birden çok bağlantı hattıyla yönlendirmeyi yönetmek için BGP yol maliyetini, PAC dosyalarını ve NAT'yi kullanın.  <br/> |
|ExpressRoute bağlantı hattı olmayan konumlardan yönlendirme  <br/> |Office 365 isteğini başlatan kişiye yakın çıkış ve DNS çözümlemesi öneririz.  <br/> DNS iletme, uzak ofislerin uygun uç noktayı bulmasına izin vermek için kullanılabilir.  <br/> Uzak ofisteki istemcilerin ExpressRoute bağlantı hattına erişim sağlayan bir yolu olmalıdır.  <br/> |
|Küçük ofis birleştirme  <br/> |Kullanılabilir bant genişliği ve veri kullanımı dikkatle karşılaştırılmalıdır.  <br/> |

> [!NOTE]
> Microsoft, rota fiziksel konumdan bağımsız olarak kullanılabiliyorsa İnternet üzerinden ExpressRoute'u tercih edecektir.
  
Bu noktaların her biri, her benzersiz ağ için dikkate alınmalıdır. Aşağıda bir örnek verilmiştir.
  
### <a name="example-2-multi-geographic-locations"></a>Örnek 2: Çok coğrafi konumlar
  
Bu örnek, birden çok coğrafi konumu olan 'Humongous Insurance' adlı kurgusal bir şirket için bir senaryodur.
  
Humongous Insurance coğrafi olarak dünyanın her yerinde ofislerle dağılır. Office 365 trafiğinin çoğunu doğrudan ağ bağlantılarında tutmak için Office 365 için Azure ExpressRoute uygulamak istiyorlar. Humongous Insurance'ın iki kıtada daha ofisleri vardır. ExpressRoute'un uygun olmadığı uzak ofisteki çalışanların ExpressRoute bağlantısını kullanmak için birincil tesislerden birine veya her ikisine geri dönmeleri gerekir.
  
Yol gösteren ilke, bir Microsoft veri merkezine giden Office 365 trafiği mümkün olan en kısa sürede almaktır. Bu örnekte Humongous Insurance, uzak ofislerinin mümkün olan en kısa sürede herhangi bir bağlantı üzerinden Microsoft veri merkezine ulaşmak için İnternet üzerinden mi yoksa uzak ofislerinin bir ExpressRoute bağlantısı üzerinden Microsoft veri merkezine en kısa sürede ulaşmak için bir iç ağ üzerinden mi yönlendirilmesi gerektiğine karar vermelidir.
  
Microsoft'un veri merkezleri, ağları ve uygulama mimarisi, küresel olarak farklı iletişimleri almak ve mümkün olan en verimli şekilde hizmet vermek için tasarlanmıştır. Bu, dünyanın en büyük ağlarından biridir. Müşteri ağlarında gerekenden daha uzun süre kalan Office 365 hedefleyen istekler bu mimariden yararlanamaz.
  
Humongous Insurance'ın durumunda, ExpressRoute üzerinden kullanmayı amaçladıkları uygulamalara bağlı olarak devam etmelidir. Örneğin, Skype Kurumsal Online müşterisiyse veya dış Skype Kurumsal Çevrimiçi toplantılara bağlanırken ExpressRoute bağlantısını kullanmayı planlıyorsa, Skype Kurumsal Çevrimiçi medya kalitesi ve ağ bağlantısı kılavuzunda önerilen tasarım, üçüncü konum için ek bir ExpressRoute bağlantı hattı sağlamaktır. Bu, ağ açısından daha pahalı olabilir; Ancak, microsoft veri merkezine teslim etmeden önce isteklerin bir kıtadan diğerine yönlendirilmesi, çevrimiçi toplantılar ve iletişimler Skype Kurumsal sırasında kötü veya kullanılamaz bir deneyime neden olabilir.
  
Humongous Insurance Skype Kurumsal Online'ı hiçbir şekilde kullanmıyorsa veya herhangi bir şekilde kullanmayı planlamıyorsa, Office 365 hedeflenen ağ trafiğini ExpressRoute bağlantısı olan bir kıtaya yönlendirmek mümkün olabilir ancak gereksiz gecikmeye veya TCP tıkanıklığına neden olabilir. Her iki durumda da, Office 365 bağlı olan içerik teslim ağlarından yararlanmak için İnternet'e yönelik trafiği yerel sitede İnternet'e yönlendirmek önerilir.
  
![ExpressRoute çok coğrafyalı.](../media/98fdd883-2c5a-4df7-844b-bd28cd0b9f50.png)
  
Humongous Insurance çok coğrafyalı stratejisini planlarken, devre boyutu, devre sayısı, yük devretme vb. konusunda dikkate alınması gereken birçok şey vardır.
  
ExpressRoute'un birden çok bölgenin devreyi kullanmaya çalıştığı tek bir konumda olmasıyla, Humongous Insurance uzak ofisten Office 365 bağlantıların en yakın merkezdeki Office 365 veri merkezine gönderildiğinden ve merkezin konumu tarafından alındığından emin olmak istiyor. Humongous Insurance bunu yapmak için, genel merkez İnternet çıkış noktasına en yakın Office 365 ortamıyla uygun bağlantıyı kurmak için gereken gidiş dönüş ve DNS aramalarının sayısını azaltmak için DNS iletme uygular. Bu, istemcinin yerel bir ön uç sunucusunu çözümlemesini önler ve kişinin bağlandığı Front-End sunucusunun Humongous Insurance'ın Microsoft ile eşlendiği genel merkeze yakın olmasını sağlar. [Etki Alanı Adı için Koşullu İletici Atamayı](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc794735(v=ws.10)) da öğrenebilirsiniz.
  
Bu senaryoda, uzak ofisten gelen trafik Kuzey Amerika Office 365 ön uç altyapısını çözümleyebilir ve Office 365 uygulamasının mimarisine göre arka uç sunucularına bağlanmak için Office 365 kullanır. Örneğin, Exchange Online bağlantıyı Kuzey Amerika sonlandıracak ve bu ön uç sunucuları kiracının bulunduğu her yerde arka uç posta kutusu sunucusuna bağlanacak. Tüm hizmetler, tek noktaya yayın ve herhangi bir noktaya yayın hedeflerinden oluşan geniş bir dağıtılmış ön kapı hizmetine sahiptir.
  
Humongous'un birden çok kıtada büyük ofisleri varsa, Skype Kurumsal Online gibi hassas uygulamaların gecikme süresini azaltmak için bölge başına en az iki etkin/etkin devre önerilir. Tüm ofisler tek bir kıtada yer alıyorsa veya gerçek zamanlı işbirliği kullanmıyorsa, birleştirilmiş veya dağıtılmış çıkış noktasına sahip olmak müşteriye özel bir karardır. Birden çok devre kullanılabilir olduğunda BGP yönlendirmesi, tek bir bağlantı hattının kullanılamaz duruma gelmesi durumunda yük devretmeyi güvence altına alır.
  
Örnek [yönlendirme yapılandırmaları](/azure/expressroute/expressroute-config-samples-routing) ve [https://azure.microsoft.com/documentation/articles/expressroute-config-samples-nat/](/azure/expressroute/expressroute-config-samples-nat)hakkında daha fazla bilgi edinin.
  
## <a name="selective-routing-with-expressroute"></a>ExpressRoute ile seçmeli yönlendirme

ExpressRoute ile seçmeli yönlendirme, test etme, ExpressRoute'u bir kullanıcı alt kümesine aktarma gibi çeşitli nedenlerle gerekebilir. Müşterilerin ExpressRoute üzerinden Office 365 ağ trafiğini seçmeli olarak yönlendirmek için kullanabileceği çeşitli araçlar vardır:
  
1. **Yol filtreleme/ayrıştırma** - BGP yollarının ExpressRoute üzerinden alt ağlarınızın veya yönlendiricilerinizin bir alt kümesine Office 365 izin verir. Bu, müşteri ağ kesimine veya fiziksel ofis konumuna göre seçmeli olarak yönlendirir. Bu, Office 365 için ExpressRoute'un aşamalı dağıtımında yaygındır ve BGP cihazlarınızda yapılandırılır.

2. **PAC dosyaları/URL'leri** - belirli FQDN'ler için Office 365 hedeflenen ağ trafiğini belirli bir yola yönlendirme. Bu, [PAC dosya dağıtımı](./managing-office-365-endpoints.md) tarafından tanımlanan istemci bilgisayara göre seçmeli olarak yönlendirir.

3. **Yol filtreleme** -  [Yol filtreleri](/azure/expressroute/how-to-routefilter-portal), Microsoft eşlemesi aracılığıyla desteklenen hizmetlerin bir alt kümesini kullanmanın bir yoludur.

4. **BGP toplulukları** - [BGP topluluk etiketlerine](./bgp-communities-in-expressroute.md) göre filtreleme, müşterinin ExpressRoute'u hangi Office 365 uygulamalarının ve hangilerinin İnternet'ten geçeceğini belirlemesine olanak tanır.

İşte geri dönmek için kullanabileceğiniz kısa bir bağlantı: [https://aka.ms/erorouting]()
  
## <a name="related-topics"></a>İlgili Konular

[Office 365 ağ bağlantısını değerlendirme](assessing-network-connectivity.md)
  
[Office 365 için Azure ExpressRoute](azure-expressroute.md)
  
[Office 365 bağlantısı için ExpressRoute'u yönetme](managing-expressroute-for-connectivity.md)
  
[Office 365 için ExpressRoute ile Ağ planlaması](network-planning-with-expressroute.md)
  
[Office 365 için ExpressRoute Uygulama](implementing-expressroute.md)
  
[Skype Kurumsal Online'da Medya Kalitesi ve Ağ Bağlantısı Performansı](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[Ağınızı Skype Kurumsal Online için iyileştirme](https://support.office.com/article/b363bdca-b00d-4150-96c3-ec7eab5a8a43)
  
[Skype Kurumsal Online'da ExpressRoute ve QoS](https://support.office.com/article/20c654da-30ee-4e4f-a764-8b7d8844431d)
  
[ExpressRoute kullanarak çağrı akışı](https://support.office.com/article/413acb29-ad83-4393-9402-51d88e7561ab)
  
[Office 365 senaryoları için ExpressRoute'ta BGP topluluklarını kullanma](bgp-communities-in-expressroute.md)
  
[Temelleri ve performans geçmişini kullanarak performans ayarlamayı Office 365](performance-tuning-using-baselines-and-history.md)
  
[Office 365 için performans sorunlarını giderme planı](performance-troubleshooting-plan.md)
  
[Office 365 URL'leri ve IP adresi aralıkları](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)
  
[ağ ve performans ayarlamayı Office 365](network-planning-and-performance.md)
