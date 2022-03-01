---
title: ExpressRoute ile ağ planlama Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 2/14/2018
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 103208f1-e788-4601-aa45-504f896511cd
description: Bu makalede, İş için Azure ExpressRoute hakkında bilgi Office 365 ve Ağ planlama için nasıl kullanacağız?
ms.openlocfilehash: d411d44ffe08da684b3cbca9a9449c4d04126a39
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2022
ms.locfileid: "63019516"
---
# <a name="network-planning-with-expressroute-for-office-365"></a>ExpressRoute ile ağ planlama Office 365

*Bu makale hem son hem de Microsoft 365 Kurumsal hem de Office 365 Kurumsal.*

Dış Kullanıcılar için ExpressRoute Office 365 ağınız ve Microsoft'un veri merkezleri arasında katman 3 bağlantısı sağlar. Devreler, bağlantı hatlarının ön uç sunucularının Kenarlık Ağ Geçidi Protokolü (BGP) yönlendirme Office 365 tanıtımlarını kullanır. Şirket içi cihazlarınız açısından, cihazlarınız İnternet'e doğru TCP/IP yolunu seçmeleri gereken Office 365, Azure ExpressRoute İnternet'in alternatifi olarak görülür.
  
Azure ExpressRoute, Microsoft'un veri merkezlerinde yer alan belirli bir dizi desteklenen özellik ve Office 365 doğrudan bir yol ekler. Azure ExpressRoute, Microsoft veri merkezleriyle veya etki alanı ad çözümlemesi gibi temel İnternet hizmetleriyle İnternet bağlantısının yerini vermez. Azure ExpressRoute ve İnternet devreleri güvenli ve yedekli olması gerekir.
  
Aşağıdaki tabloda, İnternet ile Azure ExpressRoute bağlantıları arasındaki bağlantı sayısı arasındaki bazı farklar, çalışma Office 365.

|**Ağ planlama farklılıkları**|**İnternet ağ bağlantısı**|**ExpressRoute ağ bağlantısı**|
|:-----|:-----|:-----|
| Gerekli İnternet hizmetlerine erişim;  <br/>  DNS ad çözümlemesi  <br/>  Sertifika iptal doğrulaması  <br/>  İçerik Teslim Ağları (CDN)  <br/> |Evet  <br/> |Microsoft'a ait DNS ve/veya CDN istekleri ExpressRoute ağına sahip olabilir.  <br/> |
| Şu Office 365 hizmetlere erişim;  <br/>  Exchange Online  <br/>  SharePoint Online  <br/>  Skype Kurumsal Çevrimiçi  <br/>  Office tarayıcıda yeniden kullanma  <br/>  Office 365 Portalı ve Kimlik Doğrulaması  <br/> |Evet, tüm uygulamalar ve özellikler  <br/> |Evet, [belirli uygulamalar ve özellikler](./urls-and-ip-address-ranges.md) <br/> |
|Çevrede şirket içi güvenlik.  <br/> |Evet  <br/> |Evet  <br/> |
|Yüksek kullanılabilirlik planlaması.  <br/> |Alternatif İnternet ağ bağlantısı üzerinden başarısız olun  <br/> |Alternatif ExpressRoute bağlantısına yük devretme  <br/> |
|Öngörülebilir bir ağ profiliyle doğrudan bağlantı.  <br/> |Hayır  <br/> |Evet  <br/> |
|IPv6 bağlantısı.  <br/> |Evet  <br/> |Evet  <br/> |

Daha fazla ağ planlama kılavuzu için aşağıdaki başlıkları genişletin. Ayrıca, daha derine inen bir Eğitim serisi için 10 bölüm [Office 365 Azure ExpressRoute](https://channel9.msdn.com/series/aer) kaydettik.

## <a name="existing-azure-expressroute-customers"></a>Mevcut Azure ExpressRoute müşterileri

Mevcut Azure ExpressRoute devresini kullanıyorsanız ve bu devre üzerinden Office 365 bağlantısı eklemek istiyorsanız, devrelerin sayısına, çıkış konumlarının ve devrelerin boyutuna bakarak bunların Office 365 kullanımınıza uygun olduğundan emin olun. Çoğu müşteri fazladan bant genişliği gerektirir ve çok sayıda da daha fazla devre gerektirir.
  
Mevcut Azure ExpressRoute devreleri Office 365 erişimi [etkinleştirmek için,](/azure/expressroute/how-to-routefilter-portal) yol filtrelerini yapılandırarak yol filtrelerini Office 365 erişilebilir olmasını sekleyebilirsiniz.
  
Azure ExpressRoute aboneliği müşteri odaklıdır; bu da aboneliklerin müşterilere bağlı olduğu anlamına gelir. Müşteri olarak, birden çok Azure ExpressRoute devreniz olabilir ve bu devreler üzerinden birçok Microsoft bulut kaynağına erişebilirsiniz. Örneğin, bir çift yedekli Azure ExpressRoute devresi üzerinden Azure tarafından barındırılan bir sanal makineye, Office 365 test kiracısına ve Office 365 üretim kiracısına erişmeyi seçebilirsiniz.
  
Bu tabloda, devreleri üzerinden uygulamaya koyabilirsiniz iki eşleme ilişkisi türü özetler.

|**Eşleme ilişkisi**|**Azure Özel**|**Microsoft**|
|:-----|:-----|:-----|
|**Hizmetler** <br/> |IaaS: Azure Sanal Makineleri  <br/> |PaaS: Azure genel hizmetleri  <br/> SaaS: Office 365  <br/> Saas: Dynamics 365  <br/> |
|Bağlantının başlatı**** <br/> |Müşteriden Microsoft'a  <br/> Microsoft'u Müşteriden Müşteriye  <br/> |Müşteriden Microsoft'a  <br/> Microsoft'u Müşteriden Müşteriye  <br/> |
|**QoS desteği** <br/> |QoS Yok  <br/> |<sup>QoS1</sup> <br/> |

<sup>1 </sup> QoS şu Skype Kurumsal anda destekle almaktadır.
  
## <a name="bandwidth-planning-for-azure-expressroute"></a>Azure ExpressRoute için bant genişliği planlaması

Her Office 365 müşterisi, her konumdaki kişi sayısına, her Office 365 uygulamasında ne kadar etkin olduklarının yanı sıra şirket içi veya karma donanımın kullanımı ve ağ güvenlik yapılandırmaları gibi diğer faktörlere bağlı olarak benzersiz bant genişliği gereksinimlerine sahiptir.
  
Bant genişliğinin çok az olması tıkanıklığı, verilerin yeniden iletir ve öngörülemeyen gecikmelere neden olur. Bant genişliğinin çok fazla olması gereksiz bir maliyete neden olur. Mevcut bir ağ üzerinde, bant genişliği çoğunlukla devrede bulunan yüzde olarak kullanılabilir oda miktarı olarak adlandırılır. Yüzde 10 olması büyük olasılıkla tıkanıklığı ve %80 olması genellikle gereksiz maliyet anlamına gelir. Tipik hedef hedef ayırmalar %20 ile %50 arasındadır.
  
Doğru bant genişliği düzeyini bulmak için, en iyi mekanizma mevcut ağ kullanımınızı test etmektir. Her ağ yapılandırması ve uygulamaları bazı şekillerde benzersiz olduğu için, kullanımı ve ihtiyacı doğru ölçmenin tek yolu bu olmalıdır. Ölçümlerken ağ gereksinimlerini anlamak için toplam bant genişliği tüketimine, gecikme süresine ve TCP tıkanıklığına özellikle dikkat etmek gerekir.
  
Tüm ağ uygulamalarını içeren tahmini bir taban çizgisiniz olduktan sonra, gerçek kullanımı belirlemek için kuruluş genelinde farklı kişi profillerini oluşturan küçük bir grupla pilot Office 365 ve her ofis konumu için gereken bant genişliği miktarını tahmin etmek için bu iki ölçümü kullanın. Testinde bulunan gecikme süresi veya TCP tıkanıklığı sorunları varsa, Office 365 kullanan kişilerin çıkışını daha yakına taşımanız veya SSL şifre çözme/denetim gibi yoğun ağ taramasını kaldırmanız gerekir.
  
Önerilen ağ işleme türüyle ilgili tüm önerilerimiz hem ExpressRoute hem de İnternet devreleri için geçerlidir. Aynı şey performans ayarlama sitemizde bulunan diğer [kılavuzlar için de aynısı olur](./network-planning-and-performance.md).
  
## <a name="applying-security-controls-to-azure-expressroute-for-office-365-scenarios"></a>Daha fazla bilgi için Azure ExpressRoute'a güvenlik Office 365 uygulama

Azure ExpressRoute bağlantısının güvenliğini sağlama, İnternet bağlantısının güvenliğini sağlama ile aynı ilkelerle başlar. Birçok müşteri, şirket içi ağlarını Kendi Microsoft bulutlarına ve diğer Microsoft bulutlarına bağlarken ExpressRoute yolu boyunca ağ Office 365 denetimleri dağıtmayı tercih eder. Bu denetimler güvenlik duvarları, uygulama aracıları, veri sızıntısını önleme, izinsiz giriş algılaması önleme, izinsiz giriş önleme sistemleri gibi özellikleri içerebilir. Birçok durumda, müşteriler şirket içinden başlatılan Microsoft'a olan trafiğe ve Microsoft'tan başlatılan trafikle müşterinin şirket içi ağına gelen trafiğe ve şirket içinden başlatılan ve genel bir İnternet hedefine olan trafik için farklı denetim düzeyleri uygulamaz.
  
Aşağıda, güvenliği dağıtmayı seçtiğiniz [ExpressRoute bağlantı modeliyle tümleştirmeye örnek](/azure/expressroute/expressroute-connectivity-models) olarak birkaç örnek verilmiştir.

|**ExpressRoute tümleştirme seçeneği**|**Ağ güvenliği çevre modeli**|
|:-----|:-----|
|Bulut değişiminde birlikte konumlandı  <br/> |ExpressRoute bağlantısının kurul olduğu birlikte yükleme tesisinde yeni güvenlik/çevre altyapısını yükleyin veya mevcut altyapıyı kullanın.  <br/> Birlikte yükleme tesisini yalnızca yönlendirme/bağlantı amacıyla kullanın ve birlikte yükleme tesisinden gelen bağlantıları şirket içi güvenlik/çevre altyapısına taşıyın.  <br/> |
|Noktadan Noktaya Ethernet  <br/> |Noktadan Noktaya ExpressRoute bağlantısını mevcut şirket içi güvenlik/çevre altyapısı konumuyla sonlandırın.  <br/> ExpressRoute yoluna özgü yeni bir güvenlik/çevre altyapısı yükleyin ve Noktadan Noktaya bağlantıyı orada sonlandırın.  <br/> |
|Any-to-Any IPVPN  <br/> |Bağlantıda expressRoute için kullanılan IPVPN'e çıkış yapılan tüm konumlarda mevcut bir şirket içi güvenlik/çevre altyapısını Office 365 kullanın.  <br/> ExpressRoute'ta güvenlik/çevre Office 365 üzere belirlenmiş belirli şirket içi konumlara expressRoute için kullanılan IPVPN'de geri tarak.  <br/> |

Bazı hizmet sağlayıcılar, Azure ExpressRoute ile tümleştirme çözümlerinin bir parçası olarak yönetilen güvenlik/çevre işlevselliği de sunar.
  
Çevre bağlantıları için ExpressRoute'da kullanılan ağ/güvenlik çevresi seçeneklerinin topolojide yerleşimi dikkate alınırken, Office 365 noktalar şunlardır:
  
- Ağ/güvenlik denetimlerinin derinliği ve türü, kullanıcı deneyiminin performansını ve Office 365 etkileyebilir.

- Giden (şirket içi\> Microsoft) ve gelen (Microsoft şirket\> içi) [etkinleştirildiyse] akışların farklı gereksinimleri olabilir. Bunlar büyük olasılıkla genel İnternet hedeflere giden bağlantılardan farklıdır.

- Office 365 ister İnternet üzerinden ExpressRoute aracılığıyla yönlendirildi olsun, bağlantı noktası/protokoller ve gerekli IP alt ağlarının gereksinimleri Office 365 aynıdır.

- Kullanıcıyla Office 365 hizmeti arasındaki  uç  uç ağı müşterinin ağ/güvenlik denetimlerinin topolojik yerleşimi belirler ve ağ gecikmesi ve tıkanıklığı üzerinde önemli bir etki sağlar.

- Müşterilerin güvenlik/çevre topolojilerini yedekli çalışma, yüksek kullanılabilirlik ve olağanüstü durum kurtarma için en iyi yöntemlere uygun olarak Office 365 için ExpressRoute ile birlikte kullanmaları önerilir.

Burada, farklı Azure ExpressRoute bağlantı seçeneklerini yukarıda ele alan çevre güvenlik modelleriyle karşılaştıran bir Woodgrove Bank örneği ve bulunmaktadır.
  
### <a name="example-1-securing-azure-expressroute"></a>Örnek 1: Azure ExpressRoute'un güvenliğini sağlama
  
Woodgrove Bank, Azure ExpressRoute'u uygulamaya konur ve [Office 365 için ExpressRoute](routing-with-expressroute.md) ile yönlendirmeye yönelik en iyi mimariyi planladikten sonra, bant genişliği gereksinimlerini anlamak için yukarıdaki kılavuzu kullandıktan sonra, çevrenin güvenliğini sağlamak için en iyi yöntemi belirler.
  
Woodgrove gibi birkaç kıtada konumları olan çok uluslu bir kuruluş için, güvenliğin tüm çevrelere yayılması gerekir. Woodgrove için en iyi bağlantı seçeneği, her kıtada çalışanlarının ihtiyaçlarına hizmet sağlamak için dünyanın her yanında çeşitli eşleme konumlarıyla çok noktalı bir bağlantıdır. Her kıtanın içinde yedekli Azure ExpressRoute devreleri vardır ve güvenlik bunların tamama yayılmak gerekir.
  
Woodgrove'un mevcut altyapısı güvenilirdir ve ek çalışmayla başa çıkabilir; bunun sonucunda, Woodgrove Bank Azure ExpressRoute ve İnternet çevre güvenliği için altyapıyı kullanabilir. Durum böyle olmasaydı, Woodgrove mevcut donanımlarına destek olmak veya farklı bir bağlantı türü işlemek için daha fazla donanım satın almak seçebilirdi.
  
## <a name="high-availability-and-failover-with-azure-expressroute"></a>Azure ExpressRoute ile yüksek kullanılabilirlik ve yük devretme
<a name="BKMK_high-availability"> </a>

ExpressRoute ile birlikte her çıkıştan ExpressRoute sağlayıcınıza en az iki etkin devre sağlanmasını öneririz. Burası, müşterilerin hatalarla sık karşılaşılan bir yeridir ve bir çift etkin/etkin ExpressRoute devresi hazırarak bunu kolayca önlayabilirsiniz. Birçok etkin/etkin İnternet devresi de önerilmez, çünkü Office 365 devreleri yalnızca İnternet üzerinden kullanılabilir.
  
Ağ'ın çıkış noktasının içinde, kişilerin kullanılabilirliği algıladığı konusunda önemli bir rol oynarken, diğer birçok cihaz ve devre vardır. Bağlantı senaryolarının bu bölümleri ExpressRoute veya Office 365 SLA'larının kapsamına değildir, ancak  uç hizmet kullanılabilirliği açısından, kurumuz kişilerin algıladığı  uç hizmetlerde önemli bir rol oynar.
  
Etki alanı kullanan ve bu Office 365 çalışanlara odaklanın; bileşenlerden herhangi bir hata hizmeti kullanan kişilerin deneyimini etkiliyorsa, etkilenen toplam kişi yüzdesini sınırlamanın yollarını bakın. Yük devretme modunun faaliyeti karmaşıksa, kişilerin kurtarma için uzun süreyle sahip olduğunu düşünün ve işlem için basit ve otomatik yük devretme modları olup bakmaz.
  
Ağ, ağ, Office 365 ExpressRoute ve ExpressRoute sağlayıcınızın hepsi farklı kullanılabilirlik düzeylerine sahiptir.
  
### <a name="service-availability"></a>Hizmet Kullanılabilirliği
  
- Office 365 hizmetleri, tek tek hizmetlerin çalışma süresi ve kullanılabilirlik [](/office365/servicedescriptions/office-365-platform-service-description/service-level-agreement)ölçümlerini de içeren iyi tanımlanmış hizmet düzeyi sözleşmelerinin kapsamındadır. Bu tür Office 365 hizmet kullanılabilirlik düzeylerini koruyabilmenin bir nedeni, tek tek bileşenlerin genel Microsoft ağına bağlı olarak birçok Microsoft veri merkezi arasında sorunsuz bir şekilde yük devretmesini sağlamaktır. Bu yük devretme, veri merkezinden ve ağdan birden çok İnternet çıkış noktasına genişletilen ve hizmeti kullanan kişiler açısından sorunsuz yük devretmeye olanak sağlar.

- ExpressRoute, Microsoft Network Edge ile ExpressRoute sağlayıcısı veya iş ortağı altyapısı arasında, tek tek ayrılmış devrelerde [%99,9 kullanılabilirlik SLA](https://azure.microsoft.com/support/legal/sla/expressroute/v1_0/) sağlar. Bu hizmet düzeyleri, her eşleme konumu için yedekli Microsoft donanımıyla ağ sağlayıcısı donanımı arasında [](/azure/expressroute/expressroute-introduction) iki bağımsız bağlantıdan oluşan ExpressRoute devre düzeyinde uygulanır.

### <a name="provider-availability"></a>Sağlayıcı Kullanılabilirliği
  
- Microsoft'un hizmet düzeyi düzenlemeleri ExpressRoute sağlayıcınızda veya iş ortağında durur. Bu, kullanılabilirlik düzeyinizi etkileecek seçimlerin ilk olduğu yerdir. Her Microsoft eşleme alanında, ExpressRoute sağlayıcınızın ağ çevreniz ile sağlayıcılarınız arasındaki bağlantıda sunduğu mimari, kullanılabilirlik ve güvenlik özelliklerini yakından değerlendirmeniz gerekir. Yedekli çalışma, eşleme donanımı ve taşıyıcının sağladığı WAN devrelerinin yanı sıra NAT hizmetleri veya yönetilen güvenlik duvarları gibi fazladan değer ek hizmetlerin hem mantıksal hem de fiziksel yönlerine çok dikkat olun.

### <a name="designing-your-availability-plan"></a>Kullanılabilirlik planınızı tasarlama
  
Sizin için  uç-uç bağlantı senaryolarınız için yüksek kullanılabilirlik ve kullanım yüksekliğini planlamanızı ve tasarlamanızı Office 365. Bir tasarım;
  
- Hem İnternet hem de ExpressRoute devreleri dahil tek bir hata noktası yoktur.

- En çok beklenen hata modlarında etkilenen kişi sayısını ve bu etkinin süresini en aza indirme.

- En çok beklenen hata modlarından basit, yinelenebilir ve otomatik kurtarma işlemi için en iyi duruma getirilebilir.

- Yedekli yollar aracılığıyla, önemli bir performans düşüşü olmaksızın ağ trafiğinize ve işlevselliğinize tüm talepleri destekleme.

Bağlantı senaryolarınız, birden çok bağımsız ve etkin ağ yolu için en iyi duruma getirilmiş bir ağ topolojisi Office 365. Bu, yalnızca tek bir cihaz veya donanım düzeyinde yedekli çalışma için iyileştirilmiş bir topolojiden daha iyi bir  uç-bitiş kullanılabilirliği sağlar.
  
> [!TIP]
> Kullanıcılarınız birden çok kıtaya veya coğrafi bölgeye dağıtılıyorsa ve bu konumlardan her biri yedekli WAN devreleri üzerinden tek bir ExpressRoute devresi bulunan tek bir şirket içi konuma bağlanıyorsa, kullanıcılarınız farklı bölgeleri en yakın eşleme yerine bağlayan bağımsız ExpressRoute devreleri içeren bir ağ topolojisi tasarımına göre  end-uç hizmet kullanılabilirliğini daha az deneyimle deneyimler.
  
Her devrenin farklı coğrafi eşleme konumuyla bağlanıyor olması için en az iki ExpressRoute devresi sağlanmasını öneririz. Kişilerin diğer hizmetler için ExpressRoute bağlantısını kullanmaları gereken her bölge için bu etkin etkin devre çiftini Office 365 gerekir. Bu sayede her bölgenin, veri merkezi veya eşleme konumu gibi önemli bir konumda olağanüstü bir durumla karşıtlı kalmalarına olanak sağlar. Bunları etkin/etkin olarak yapılandırmak, son kullanıcı trafiğinin birden çok ağ yolu arasında dağıtılmasını sağlar. Bu, cihaz veya ağ donanımı kesintileri sırasında etkilenen kişi kapsamını azaltır.
  
Yedek olarak İnternet'in olduğu tek bir ExpressRoute devresi kullanmamanızı öneririz.
  
### <a name="example-2-failover-and-high-availability"></a>Örnek 2: Yük Devretme ve Yüksek Kullanılabilirlik
  
Woodgrove Bank'in birden çok coğrafi bölgeli tasarımı yönlendirme, bant genişliği ve güvenlik gözden geçirildi ve şimdi de yüksek kullanılabilirlik gözden geçirmesi gerekiyor. Woodgrove, yüksek kullanılabilirliği üç kategoriyi kapsaıyor; dayanıklılık, güvenilirlik ve yedekli çalışma.
  
Resilicy Woodgrove'un hatalardan hızla geri kurtarmalarını sağlar. Güvenilirlik, Woodgrove'un sistem için tutarlı bir sonuç sunmalarını sağlar. Yedekli çalışma, Woodgrove'un bir veya birden çok yansıtılmış altyapı örnekleri arasında geçişe olanak sağlar.
  
Her kenar yapılandırması içinde, Woodgrove'un yedekli Güvenlik Duvarları, Aracılar ve Kimlikler vardır. Kuzey Amerika için, Woodgrove Dallas veri merkezinde bir uç yapılandırmaya ve Virginia veri merkezinde de bir diğer uç yapılandırmaya sahip. Her konumdaki yedekli donanım, o konuma yedekli donanım sağlar.
  
Woodgrove Bank'in ağ yapılandırması birkaç temel ilkeye dayalıdır:
  
- Her coğrafi bölgede, birden çok Azure ExpressRoute devresi vardır.

- Bir bölgedeki her devre, o bölge içindeki ağ trafiğinin hepsini destekleyebilirsiniz.

- Yönlendirme; kullanılabilirlik ve konum gibi konumlara bağlı olarak yollardan birini veya diğerini açıkça tercih eder.

- Azure ExpressRoute devreleri arasında yük devretme, Woodgrove'un herhangi bir ek yapılandırma veya eyleme gerek kalmadan otomatik olarak yapılır.

- İnternet devreleri arasında yük devretme, Woodgrove'un herhangi bir ek yapılandırma veya eyleme gerek kalmadan otomatik olarak yapılır.

Fiziksel ve sanal düzeyde yedekli çalışma ile bu yapılandırmada, Woodgrove Bank güvenilir bir yolla yerel dayanıklılık, bölgesel dayanıklılık ve küresel dayanıklılık sunabilecektir. Woodgrove, hem bölge başına tek Azure ExpressRoute devresini hem de İnternet'e başarısız olma olasılığını değerlendirdikten sonra bu yapılandırmayı seçmiştir.
  
Woodgrove bölge başına birden fazla Azure ExpressRoute devresi alamasa da, Kuzey Amerika'da kaynaklanan trafiğin Asya Pasifik'te Azure ExpressRoute devrelerine yönlendirılması kabul edilemez bir gecikme düzeyi ekler ve gereken DNS iletici yapılandırması da karmaşıklığı ekler.
  
Yedek yapılandırma olarak İnternet'in kullanılması önerilmez. Bu Woodgrove'un güvenilirlik ilkesine aykırıdır ve sonuçta bağlantının kullanımı tutarsız bir deneyime neden olur. Buna ek olarak, yapılandırılmış olan BGP tanıtımları, NAT yapılandırması, DNS yapılandırması ve ara sunucu yapılandırması dikkate alınarak başarısız olması için el ile yapılandırma gerekebilir. Bu ek yük devretme karmaşıklığı, kurtarma ve ilgili adımları tanılama ve sorun giderme becerilerini azaltır.
  
Trafik yönetimini planlama ve uygulama veya Azure ExpressRoute hakkında hala sorularınız mı var? Ağ ve performans [kılavuzumuzla Azure](./network-planning-and-performance.md) [ExpressRoute SSS'nin kalan bölümünü okuyun](/azure/expressroute/expressroute-faqs).
  
## <a name="working-with-azure-expressroute-providers"></a>Azure ExpressRoute sağlayıcılarıyla çalışma
<a name="BKMK_high-availability"> </a>

Bant genişliğiniz, gecikme süresi, güvenlik ve yüksek kullanılabilirlik planlamanıza bağlı olarak devrelerin konumlarını seçin. En iyi konumları bir kez biliyorktan sonra, devreleri yerlerinin bölgeye [göre geçerli sağlayıcı listesini gözden geçirmek istediğinize emin oluruz](/azure/expressroute/expressroute-locations).
  
Noktadan noktaya, çok noktalı veya barındırılan en iyi bağlantı seçeneklerini seçmek için sağlayıcınız veya sağlayıcılarınız ile birlikte çalışabilirsiniz. Bant genişliği ve diğer yedekli bileşenler yönlendirme ve yüksek kullanılabilirlik tasarımınızı desteklemektedir.
  
İşte geri dönmek için kullanabileceğiniz kısa bir bağlantı: [https://aka.ms/planningexpressroute365]()
  
## <a name="related-topics"></a>İlgili Konular
<a name="BKMK_high-availability"> </a>

[Ağ Office 365 değerlendirme](assessing-network-connectivity.md)
  
[Office 365 için Azure ExpressRoute](azure-expressroute.md)
  
[Daha fazla bağlantı için ExpressRoute Office 365 yönetme](managing-expressroute-for-connectivity.md)
  
[Posta için ExpressRoute ile yönlendirme Office 365](routing-with-expressroute.md)
  
[Proje için ExpressRoute'u Office 365](implementing-expressroute.md)
  
[Daha fazla senaryo için ExpressRoute'ta BGP Office 365 kullanma](bgp-communities-in-expressroute.md)
  
[Skype Kurumsal Online'da Medya Kalitesi ve Ağ Bağlantısı Performansı](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[Skype Kurumsal Online için a Skype Kurumsal iyileştirme](https://support.office.com/article/b363bdca-b00d-4150-96c3-ec7eab5a8a43)
  
[Skype Kurumsal Online'da ExpressRoute ve QoS](https://support.office.com/article/20c654da-30ee-4e4f-a764-8b7d8844431d)
  
[ExpressRoute kullanarak arama akışı](https://support.office.com/article/413acb29-ad83-4393-9402-51d88e7561ab)
  
[Office 365 ve performans geçmişini kullanarak performans ayarlamayı ayarlama](performance-tuning-using-baselines-and-history.md)
  
[Destek için performans sorunlarını giderme Office 365](performance-troubleshooting-plan.md)
  
[Office 365 URL'leri ve IP adresi aralıkları](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)
  
[Office 365 ve performans ayarını yapılandırma](network-planning-and-performance.md)
  
[Office 365 uç noktaları hakkında SSS](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)