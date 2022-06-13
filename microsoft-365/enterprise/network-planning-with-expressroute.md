---
title: Office 365 için ExpressRoute ile Ağ planlaması
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: Bu makalede, Office 365 için Azure ExpressRoute hakkında bilgi edinecek ve ağ planlaması için nasıl kullanacağınızı öğreneceksiniz.
ms.openlocfilehash: 59fa69a58bedf6babf2cf277a627d42293487ab1
ms.sourcegitcommit: a7c1acfb3d2cbba913e32493b16ebd8cbfeee456
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/13/2022
ms.locfileid: "66042924"
---
# <a name="network-planning-with-expressroute-for-office-365"></a>Office 365 için ExpressRoute ile Ağ planlaması

*Bu makale hem Microsoft 365 Kurumsal hem de Office 365 Kurumsal için geçerlidir.*

Office 365 için ExpressRoute, ağınızla Microsoft'un veri merkezleri arasında katman 3 bağlantısı sağlar. Devreler, Office 365 ön uç sunucularının Sınır Ağ Geçidi Protokolü (BGP) yol tanıtımlarını kullanır. Şirket içi cihazlarınız açısından bakıldığında, Office 365 için doğru TCP/IP yolunu seçmeleri gerektiğinde, Azure ExpressRoute İnternet'e alternatif olarak görülür.
  
Azure ExpressRoute, Microsoft'un veri merkezlerindeki Office 365 sunucuları tarafından sunulan belirli bir desteklenen özellik ve hizmet kümesine doğrudan bir yol ekler. Azure ExpressRoute, Microsoft veri merkezlerine İnternet bağlantısının veya etki alanı adı çözümlemesi gibi temel İnternet hizmetlerinin yerini almaz. Azure ExpressRoute ve İnternet bağlantı hatlarınız güvenli ve yedekli olmalıdır.
  
Aşağıdaki tabloda, Office 365 bağlamında İnternet ile Azure ExpressRoute bağlantıları arasındaki birkaç fark vurgulanır.

|**Ağ planlamadaki farklar**|**İnternet ağ bağlantısı**|**ExpressRoute ağ bağlantısı**|
|:-----|:-----|:-----|
| Gerekli internet hizmetlerine erişim;  <br/>  DNS ad çözümlemesi  <br/>  Sertifika iptal doğrulaması  <br/>  İçerik Teslim Ağları (CDN'ler)  <br/> |Evet  <br/> |Microsoft'a ait DNS ve/veya CDN altyapısına yönelik istekler ExpressRoute ağını kullanabilir.  <br/> |
| Office 365 hizmetlerine erişim;  <br/>  Exchange Online  <br/>  SharePoint Online  <br/>  Skype Kurumsal Çevrimiçi  <br/>  Tarayıcıda Office  <br/>  Office 365 Portalı ve Kimlik Doğrulaması  <br/> |Evet, tüm uygulamalar ve özellikler  <br/> |Evet, [belirli uygulamalar ve özellikler](./urls-and-ip-address-ranges.md) <br/> |
|Çevrede şirket içi güvenlik.  <br/> |Evet  <br/> |Evet  <br/> |
|Yüksek kullanılabilirlik planlaması.  <br/> |Alternatif bir İnternet ağ bağlantısına yük devretme  <br/> |Alternatif bir ExpressRoute bağlantısına yük devretme  <br/> |
|Tahmin edilebilir bir ağ profiliyle doğrudan bağlantı.  <br/> |Hayır  <br/> |Evet  <br/> |
|IPv6 bağlantısı.  <br/> |Evet  <br/> |Evet  <br/> |

Daha fazla ağ planlama kılavuzu için aşağıdaki başlıkları genişletin.

## <a name="existing-azure-expressroute-customers"></a>Mevcut Azure ExpressRoute müşterileri

Mevcut bir Azure ExpressRoute bağlantı hattı kullanıyorsanız ve bu bağlantı hattı üzerinden Office 365 bağlantı hattı eklemek istiyorsanız, Office 365 kullanımınızın gereksinimlerini karşıladığından emin olmak için devrelerin sayısına, çıkış konumlarına ve bağlantı hatlarının boyutuna bakmanız gerekir. Müşterilerin çoğu fazladan bant genişliğine ve çoğu daha fazla bağlantı hattına ihtiyaç duyar.
  
Mevcut Azure ExpressRoute bağlantı hatlarınız üzerinden Office 365 erişimi etkinleştirmek için, Office 365 hizmetlerinin erişilebilir olduğundan emin olmak için [yol filtrelerini yapılandırın](/azure/expressroute/how-to-routefilter-portal).
  
Azure ExpressRoute aboneliği müşteri odaklıdır ve bu da aboneliklerin müşterilere bağlı olduğu anlamına gelir. Müşteri olarak birden çok Azure ExpressRoute bağlantı hattınız olabilir ve bu bağlantı hatları üzerinden birçok Microsoft bulut kaynağına erişebilirsiniz. Örneğin, azure tarafından barındırılan bir sanal makineye, Office 365 test kiracısına ve bir Office 365 üretim kiracısına bir çift yedekli Azure ExpressRoute bağlantı hattı üzerinden erişmeyi seçebilirsiniz.
  
Bu tabloda, devreleriniz üzerinde uygulamayı seçebileceğiniz iki tür eşleme ilişkisi özetlenmiştir.

|**Eşleme ilişkisi**|**Azure Özel**|**Microsoft**|
|:-----|:-----|:-----|
|**Hizmetleri** <br/> |IaaS: Azure Sanal Makineler  <br/> |PaaS: Azure genel hizmetleri  <br/> SaaS: Office 365  <br/> SaaS: Dynamics 365  <br/> |
|Bağlantı başlatma*** <br/> |Müşteriden Microsoft'a  <br/> Microsoft'ta Müşteri  <br/> |Müşteriden Microsoft'a  <br/> Microsoft'ta Müşteri  <br/> |
|**QoS desteği** <br/> |QoS yok  <br/> |QoS<sup>1</sup> <br/> |

<sup>1 </sup> QoS yalnızca şu anda Skype Kurumsal destekler.
  
## <a name="bandwidth-planning-for-azure-expressroute"></a>Azure ExpressRoute için bant genişliği planlaması

Her Office 365 müşterinin her konumdaki kişi sayısına, her Office 365 uygulamasında ne kadar etkin olduklarına ve şirket içi veya hibrit ekipman kullanımı ve ağ güvenlik yapılandırmaları gibi diğer faktörlere bağlı olarak benzersiz bant genişliği gereksinimleri vardır.
  
Bant genişliğinin çok az olması tıkanıklık, verilerin yeniden iletimleri ve öngörülemeyen gecikmelere neden olur. Çok fazla bant genişliğine sahip olmak gereksiz maliyete neden olur. Mevcut bir ağda bant genişliği genellikle bağlantı hattındaki kullanılabilir oda miktarı açısından yüzde olarak adlandırılır. %10 tuvalete sahip olmak büyük olasılıkla tıkanıklıklara neden olur ve %80'lik bir oda olması genellikle gereksiz maliyet anlamına gelir. Tipik oda başı hedef ayırmaları %20 ile %50 arasındadır.
  
Doğru bant genişliği düzeyini bulmak için en iyi mekanizma mevcut ağ tüketiminizi test etmektir. Her ağ yapılandırması ve uygulaması bazı yönlerden benzersiz olduğundan, gerçek bir kullanım ve ihtiyaç ölçüsü almanın tek yolu budur. Ölçüm yaparken ağ gereksinimlerinizi anlamak için toplam bant genişliği tüketimine, gecikme süresine ve TCP tıkanıklığına dikkat etmek istersiniz.
  
Tüm ağ uygulamalarını içeren tahmini bir temele sahip olduğunuzda, gerçek kullanımı belirlemek için kuruluşunuzdaki farklı kişi profillerini içeren küçük bir grupla pilot Office 365 ve her ofis konumu için gereken bant genişliği miktarını tahmin etmek için iki ölçümü kullanın. Testinizde herhangi bir gecikme süresi veya TCP tıkanıklığı sorunu varsa, Office 365 kullanarak çıkışı kişilere yaklaştırmanız veya SSL şifre çözme/denetleme gibi yoğun ağ taramasını kaldırmanız gerekebilir.
  
Önerilen ağ işleme türüyle ilgili tüm önerilerimiz hem ExpressRoute hem de İnternet bağlantı hatları için geçerlidir. Aynı durum [, performans ayarlama sitemizdeki](./network-planning-and-performance.md) yönergelerin geri kalanı için de geçerlidir.
  
## <a name="applying-security-controls-to-azure-expressroute-for-office-365-scenarios"></a>Office 365 senaryoları için Azure ExpressRoute'a güvenlik denetimleri uygulama

Azure ExpressRoute bağlantısının güvenliğini sağlamak, İnternet bağlantısının güvenliğini sağlamakla aynı ilkelerle başlar. Birçok müşteri, şirket içi ağlarını Office 365 ve diğer Microsoft bulutlarına bağlayan ExpressRoute yolu boyunca ağ ve çevre denetimleri dağıtmayı tercih eder. Bu denetimler güvenlik duvarları, uygulama proxy'leri, veri sızıntısını önleme, izinsiz giriş algılama, izinsiz girişi önleme sistemleri vb. içerebilir. Çoğu durumda müşteriler şirket içinden Microsoft'a giden trafiğe, Microsoft'tan müşteri şirket içi ağına giden trafikle şirket içi ortamdan genel bir İnternet hedefine giden trafik arasında farklı denetim düzeyleri uygular.
  
Dağıtımı seçtiğiniz [ExpressRoute bağlantı modeliyle](/azure/expressroute/expressroute-connectivity-models) güvenliği tümleştirmeye yönelik birkaç örnek aşağıda verilmiştir.

|**ExpressRoute tümleştirme seçeneği**|**Ağ güvenliği çevre modeli**|
|:-----|:-----|
|Bulut değişiminde birlikte bulunma  <br/> |ExpressRoute bağlantısının kurulduğu ortak konum tesisinde yeni bir güvenlik/çevre altyapısı yükleyin veya mevcut güvenlik/çevre altyapısını kullanın.  <br/> Birlikte bulundurma tesisini yalnızca yönlendirme/ara bağlantı amaçları için kullanın ve birlikte bulundurma tesisinden şirket içi güvenlik/çevre altyapısına geri taşıma bağlantıları.  <br/> |
|Noktadan Noktaya Ethernet  <br/> |Mevcut şirket içi güvenlik/çevre altyapısı konumunda Noktadan Noktaya ExpressRoute bağlantısını sonlandırın.  <br/> ExpressRoute yoluna özgü yeni güvenlik/çevre altyapısı yükleyin ve noktadan noktaya bağlantıyı orada sonlandırın.  <br/> |
|Herhangi bir IPVPN'e  <br/> |Office 365 bağlantısı için ExpressRoute için kullanılan IPVPN'e çıkış yapılan tüm konumlarda mevcut bir şirket içi güvenlik/çevre altyapısı kullanın.  <br/> Güvenlik/çevre görevi görecek şekilde belirlenen belirli şirket içi konumlara Office 365 için ExpressRoute için kullanılan IPVPN'i saça sabitle.  <br/> |

Bazı hizmet sağlayıcıları, Azure ExpressRoute ile tümleştirme çözümlerinin bir parçası olarak yönetilen güvenlik/çevre işlevleri de sunar.
  
Office 365 bağlantıları için ExpressRoute için kullanılan ağ/güvenlik çevre seçeneklerinin topoloji yerleşimi göz önünde bulundurulduğunda, aşağıda dikkat edilmesi gereken ek noktalar bulunmaktadır
  
- Derinlik ve tür ağ/güvenlik denetimleri, Office 365 kullanıcı deneyiminin performansını ve ölçeklenebilirliğini etkileyebilir.

- Giden (şirket içi-Microsoft\>) ve gelen (microsoft-şirket\> içi) akışların [etkinse] akışları farklı gereksinimlere sahip olabilir. Bunlar büyük olasılıkla genel İnternet hedeflerine giden hedeflerden farklıdır.

- trafiğin Office 365 için ExpressRoute üzerinden veya İnternet üzerinden yönlendirilmesi fark etmeksizin bağlantı noktaları/protokoller ve gerekli IP alt ağları için Office 365 gereksinimleri aynıdır.

- Müşteri ağı/güvenlik denetimlerinin topolojik yerleşimi, kullanıcı ve Office 365 hizmeti arasındaki nihai uçtan uca ağı belirler ve ağ gecikmesi ve tıkanıklığı üzerinde önemli bir etkiye sahip olabilir.

- Müşterilerin, yedeklilik, yüksek kullanılabilirlik ve olağanüstü durum kurtarma için en iyi yöntemlere uygun olarak Office 365 için ExpressRoute ile kullanılacak güvenlik/çevre topolojilerini tasarlamaları teşvik edilir.

Aşağıda, yukarıda açıklanan çevre güvenlik modelleri ile farklı Azure ExpressRoute bağlantı seçeneklerini karşılaştıran bir Contoso örneği verilmiştir.
  
### <a name="example-1-securing-azure-expressroute"></a>Örnek 1: Azure ExpressRoute güvenliğini sağlama
  
Contoso, Azure ExpressRoute'u uygulamayı düşünüyor ve [Office 365 için ExpressRoute ile Yönlendirme için](routing-with-expressroute.md) en uygun mimariyi planladıktan sonra ve bant genişliği gereksinimlerini anlamak için yukarıdaki kılavuzu kullandıktan sonra çevresini korumak için en iyi yöntemi belirler.
  
Birden çok kıtada konumları olan çok uluslu bir kuruluş olan Contoso için güvenliğin tüm çevrelere yayılması gerekir. Contoso için en uygun bağlantı seçeneği, her kıtadaki çalışanlarının ihtiyaçlarına hizmet etmek için dünyanın dört bir yanındaki birden çok eşleme konumuyla çok noktalı bir bağlantıdır. Her kıtada, kıta içindeki yedekli Azure ExpressRoute bağlantı hatları vardır ve güvenlik bunların tümüne yayılmalıdır.
  
Contoso'nun mevcut altyapısı güvenilirdir ve ek işleri gerçekleştirebilir. Bunun sonucunda Contoso, Azure ExpressRoute ve internet çevre güvenliği için altyapıyı kullanabilir. Böyle bir durum söz konusu değilse Contoso, mevcut ekipmanlarını desteklemek veya farklı bir bağlantı türünü işlemek için daha fazla ekipman satın almayı seçebilir.
  
## <a name="high-availability-and-failover-with-azure-expressroute"></a>Azure ExpressRoute ile yüksek kullanılabilirlik ve yük devretme
<a name="BKMK_high-availability"> </a>

ExpressRoute ile her çıkıştan ExpressRoute sağlayıcınıza en az iki etkin bağlantı hattı sağlamanızı öneririz. Burası, müşteriler için hatalar gördüğümüz en yaygın yerdir ve bir çift etkin/etkin ExpressRoute bağlantı hattı sağlayarak bunu kolayca önleyebilirsiniz. Ayrıca, birçok Office 365 hizmeti yalnızca İnternet üzerinden kullanılabilir olduğundan en az iki etkin/etkin İnternet bağlantı hattı öneririz.
  
Ağınızın çıkış noktasının içinde, kişilerin kullanılabilirliği nasıl algıladıklarında kritik bir rol oynayan diğer birçok cihaz ve bağlantı hattı vardır. Bağlantı senaryolarınızın bu bölümleri ExpressRoute veya Office 365 SLA'ları kapsamında değildir, ancak kuruluşunuzdaki kişiler tarafından algılanan uçtan uca hizmet kullanılabilirliği açısından kritik bir rol oynar.
  
Office 365 kullanan ve çalıştıran kişilere odaklanın. Herhangi bir bileşenin başarısız olması kişilerin hizmeti kullanma deneyimini etkileyecekse, etkilenen kişilerin toplam yüzdesini sınırlamanın yollarını arayın. Bir yük devretme modu operasyonel olarak karmaşıksa, insanların kurtarma için uzun süre yaşadığı deneyimi göz önünde bulundurun ve operasyonel olarak basit ve otomatik yük devretme modlarını arayın.
  
Ağınızın dışında, Office 365, ExpressRoute ve ExpressRoute sağlayıcınızın tümü farklı kullanılabilirlik düzeylerine sahiptir.
  
### <a name="service-availability"></a>Hizmet Kullanılabilirliği
  
- Office 365 hizmetleri, tek tek hizmetler için çalışma süresi ve kullanılabilirlik ölçümlerini içeren iyi tanımlanmış [hizmet düzeyi sözleşmeleri](/office365/servicedescriptions/office-365-platform-service-description/service-level-agreement) kapsamındadır. Office 365 bu kadar yüksek hizmet kullanılabilirlik düzeylerini koruyabilmesinin bir nedeni, tek tek bileşenlerin genel Microsoft ağını kullanarak birçok Microsoft veri merkezi arasında sorunsuz bir şekilde yük devretme yapabilmesidir. Bu yük devretme, veri merkezinden ve ağdan birden çok İnternet çıkış noktasına genişletir ve hizmeti kullanan kişilerin perspektifinden sorunsuz bir şekilde yük devretmeyi etkinleştirir.

- ExpressRoute, Microsoft Network Edge ile ExpressRoute sağlayıcısı veya iş ortağı altyapısı arasındaki ayrı ayrılmış devrelerde [%99,9 kullanılabilirlik SLA'sı sağlar](https://azure.microsoft.com/support/legal/sla/expressroute/v1_0/) . Bu hizmet düzeyleri, her eşleme konumunda yedekli Microsoft ekipmanı ile ağ sağlayıcısı ekipmanı arasında [iki bağımsız bağlantıdan](/azure/expressroute/expressroute-introduction) oluşan ExpressRoute bağlantı hattı düzeyinde uygulanır.

### <a name="provider-availability"></a>Sağlayıcı Kullanılabilirliği
  
- Microsoft'un hizmet düzeyi düzenlemeleri ExpressRoute sağlayıcınızda veya iş ortağınızda durduruluyor. Burası aynı zamanda kullanılabilirlik düzeyinizi etkileyecek seçimler yapabileceğiniz ilk yerdir. ExpressRoute sağlayıcınızın ağ çevreniz ile her Microsoft eşleme konumundaki sağlayıcılarınız arasında sunduğu mimari, kullanılabilirlik ve dayanıklılık özelliklerini yakından değerlendirmeniz gerekir. Yedeklilik, eşleme ekipmanı, taşıyıcı tarafından sağlanan WAN devreleri ve nat hizmetleri veya yönetilen güvenlik duvarları gibi ek değer ekleme hizmetlerinin hem mantıksal hem de fiziksel yönlerine çok dikkat edin.

### <a name="designing-your-availability-plan"></a>Kullanılabilirlik planınızı tasarlama
  
Office 365 için uçtan uca bağlantı senaryolarınızda yüksek kullanılabilirlik ve dayanıklılık planlamanızı ve tasarlamanızı kesinlikle öneririz. Tasarım şunları içermelidir:
  
- Hem İnternet hem de ExpressRoute bağlantı hatları dahil olmak üzere tek bir hata noktası yoktur.

- En çok beklenen hata modları için etkilenen kişi sayısını ve bu etkinin süresini en aza indirme.

- En çok beklenen hata modlarından basit, tekrarlanabilir ve otomatik kurtarma işlemi için iyileştirme.

- Önemli bir düşüş olmadan, yedekli yollar aracılığıyla ağ trafiğinizin ve işlevselliğinizin tüm taleplerini destekleme.

Bağlantı senaryolarınız, Office 365 için birden çok bağımsız ve etkin ağ yolu için iyileştirilmiş bir ağ topolojisi içermelidir. Bu, yalnızca tek tek cihaz veya ekipman düzeyinde yedeklilik için iyileştirilmiş bir topolojiden daha iyi bir uçtan uca kullanılabilirlik sağlar.
  
> [!TIP]
> Kullanıcılarınız birden çok kıtaya veya coğrafi bölgeye dağıtılmışsa ve bu konumların her biri yedekLI WAN bağlantı hatları üzerinden tek bir ExpressRoute bağlantı hattının bulunduğu tek bir şirket içi konuma bağlanırsa, kullanıcılarınız farklı bölgeleri en yakın eşleme konumuna bağlayan bağımsız ExpressRoute bağlantı hatları içeren ağ topolojisi tasarımından daha az uçtan uca hizmet kullanılabilirliğiyle karşılaşır.
  
Her bağlantı hattının farklı bir coğrafi eşleme konumuna bağlanmasıyla en az iki ExpressRoute bağlantı hattı sağlamanızı öneririz. Kişilerin Office 365 hizmetleri için ExpressRoute bağlantısını kullanacağı her bölge için bu etkin-etkin bağlantı hattı çiftini sağlamalısınız. Bu, her bölgenin veri merkezi veya eşleme konumu gibi önemli bir konumu etkileyen bir olağanüstü durum sırasında bağlı kalmasını sağlar. Bunları içinde etkin/etkin olarak yapılandırmak, son kullanıcı trafiğinin birden çok ağ yoluna dağıtılmasını sağlar. Bu, cihaz veya ağ ekipmanı kesintileri sırasında etkilenen kişilerin kapsamını azaltır.
  
Yedek olarak İnternet ile tek bir ExpressRoute bağlantı hattı kullanmanızı önermeyiz.
  
### <a name="example-2-failover-and-high-availability"></a>Örnek 2: Yük Devretme ve Yüksek Kullanılabilirlik
  
Contoso'nun çok coğrafi tasarımında yönlendirme, bant genişliği, güvenlik gözden geçirildi ve şimdi yüksek kullanılabilirlik gözden geçirmesi gerekiyor. Contoso üç kategoriyi kapsayan yüksek kullanılabilirlik hakkında düşünür; dayanıklılık, güvenilirlik ve yedeklilik.
  
Dayanıklılık, Contoso'nın hatalardan hızlı bir şekilde kurtulmasını sağlar. Güvenilirlik, Contoso'nın sistem içinde tutarlı bir sonuç sunmasını sağlar. Yedeklilik, Contoso'nun bir veya daha fazla yansıtılmış altyapı örneği arasında geçiş yapmasını sağlar.
  
Her uç yapılandırmasında Contoso'nun yedekli Güvenlik Duvarları, Proxy'leri ve IDS'si vardır. Kuzey Amerika için Contoso'nun Dallas veri merkezinde bir uç yapılandırması ve Virginia veri merkezinde başka bir uç yapılandırması vardır. Her konumdaki yedekli ekipman, bu konuma dayanıklılık sağlar.
  
Contoso'daki ağ yapılandırması birkaç temel ilkeye göre oluşturulur:
  
- Her coğrafi bölgede birden çok Azure ExpressRoute bağlantı hattı vardır.

- Bir bölgedeki her bağlantı hattı, o bölgedeki tüm ağ trafiğini destekleyebilir.

- Yönlendirme, kullanılabilirliğe, konuma vb. bağlı olarak bir yolu veya diğer yolu açıkça tercih eder.

- Azure ExpressRoute bağlantı hatları arasında yük devretme, Contoso tarafından ek yapılandırma veya eylem gerekmeden otomatik olarak gerçekleşir.

- İnternet devreleri arasında yük devretme, Contoso tarafından ek yapılandırma veya eylem gerekmeden otomatik olarak gerçekleşir.

Bu yapılandırmada, fiziksel ve sanal düzeyde yedeklilik ile Contoso, güvenilir bir şekilde yerel dayanıklılık, bölgesel dayanıklılık ve küresel dayanıklılık sunabilir. Contoso, bölge başına tek bir Azure ExpressRoute bağlantı hattını ve İnternet'e yük devretme olasılığını değerlendirdikten sonra bu yapılandırmayı seçti.
  
Contoso bölge başına birden çok Azure ExpressRoute bağlantı hattına sahip olamadıysa, Kuzey Amerika kaynaklı trafiğin Asya Pasifik'teki Azure ExpressRoute bağlantı hattına yönlendirilmesi kabul edilemez bir gecikme düzeyi ekler ve gerekli DNS ileticisi yapılandırması karmaşıklık ekler.
  
İnternet'i yedekleme yapılandırması olarak kullanmak önerilmez. Bu, Contoso'nun güvenilirlik ilkesini bozarak bağlantıyı kullanma konusunda tutarsız bir deneyime neden olur. Ayrıca yapılandırılan BGP tanıtımları, NAT yapılandırması, DNS yapılandırması ve ara sunucu yapılandırması dikkate alınarak el ile yapılandırmanın yük devretmesi gerekir. Bu ek yük devretme karmaşıklığı kurtarma süresini artırır ve ilgili adımları tanılama ve sorun giderme becerilerini azaltır.
  
Trafik yönetimini veya Azure ExpressRoute'u planlama ve uygulama hakkında hala sorularınız mı var? [Ağ ve performans kılavuzumuzun](./network-planning-and-performance.md) geri kalanını veya [Azure ExpressRoute SSS](/azure/expressroute/expressroute-faqs) bölümünü okuyun.
  
## <a name="working-with-azure-expressroute-providers"></a>Azure ExpressRoute sağlayıcılarıyla çalışma
<a name="BKMK_high-availability"> </a>

Bant genişliği, gecikme süresi, güvenlik ve yüksek kullanılabilirlik planlamanıza göre bağlantı hatlarınızın konumlarını seçin. En uygun konumları öğrendiğiniz zaman, bağlantı hatlarının [bölgeye göre geçerli sağlayıcı listesini gözden geçirmesini](/azure/expressroute/expressroute-locations) istersiniz.
  
En iyi bağlantı seçeneklerini, noktadan noktaya, çok noktaya veya barındırılan seçenekleri seçmek için sağlayıcınız veya sağlayıcılarınızla birlikte çalışın. Bant genişliği ve diğer yedekli bileşenler yönlendirme ve yüksek kullanılabilirlik tasarımınızı desteklediği sürece bağlantı seçeneklerini karıştırıp eşleştirebileceğinizi unutmayın.
  
İşte geri dönmek için kullanabileceğiniz kısa bir bağlantı: [https://aka.ms/planningexpressroute365]()
  
## <a name="related-topics"></a>İlgili Konular
<a name="BKMK_high-availability"> </a>

[Office 365 ağ bağlantısını değerlendirme](assessing-network-connectivity.md)
  
[Office 365 için Azure ExpressRoute](azure-expressroute.md)
  
[Office 365 bağlantısı için ExpressRoute'u yönetme](managing-expressroute-for-connectivity.md)
  
[Office 365 için ExpressRoute ile Yönlendirme](routing-with-expressroute.md)
  
[Office 365 için ExpressRoute Uygulama](implementing-expressroute.md)
  
[Office 365 senaryoları için ExpressRoute'ta BGP topluluklarını kullanma](bgp-communities-in-expressroute.md)
  
[Skype Kurumsal Online'da Medya Kalitesi ve Ağ Bağlantısı Performansı](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[Ağınızı Skype Kurumsal Online için iyileştirme](https://support.office.com/article/b363bdca-b00d-4150-96c3-ec7eab5a8a43)
  
[Skype Kurumsal Online'da ExpressRoute ve QoS](https://support.office.com/article/20c654da-30ee-4e4f-a764-8b7d8844431d)
  
[ExpressRoute kullanarak çağrı akışı](https://support.office.com/article/413acb29-ad83-4393-9402-51d88e7561ab)
  
[Temelleri ve performans geçmişini kullanarak performans ayarlamayı Office 365](performance-tuning-using-baselines-and-history.md)
  
[Office 365 için performans sorunlarını giderme planı](performance-troubleshooting-plan.md)
  
[Office 365 URL'leri ve IP adresi aralıkları](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)
  
[ağ ve performans ayarlamayı Office 365](network-planning-and-performance.md)
  
[Office 365 uç noktaları hakkında SSS](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)