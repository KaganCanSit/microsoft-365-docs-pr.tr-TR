---
title: Daha fazla senaryo için ExpressRoute'ta BGP Office 365 kullanma
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 6/26/2018
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Ent_O365
- SPO_Content
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 9ac4d7d4-d9f8-40a8-8c78-2a6d7fe96099
description: Bu senaryolarda IP ön eklerinin sayısını ve gerekli bant genişliğini yönetmek için Azure ExpressRoute'ta BGP topluluklarını Office 365 öğrenin.
ms.openlocfilehash: afcbbbebda8dcc7c9425831b44f0d95f0eca5a18
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62986693"
---
# <a name="using-bgp-communities-in-expressroute-for-office-365-scenarios"></a>Daha fazla senaryo için ExpressRoute'ta BGP Office 365 kullanma

Azure ExpressRoute Office 365 bağlantıda, uç noktaların dağıtıldı olduğu ağları temsil eden belirli IP alt ağlarının BGP tanıtımları temel Office 365 bağlanır. Her iki sitenin genel doğası gereği Office 365 ve Office 365 hizmet sayısı nedeniyle, müşterilerin çoğunlukla ağlarında kabul edilen tanıtımları yönetmeleri gerekir. IP alt ağlarının sayısını azaltma; BGP ağ yönetim terminolojisine uyum sağlamak için, bu makalenin kalan kısmında IP ön ekleri olarak adlandırılan bu, müşteriler için aşağıdaki son hedefleri karşılar:
  
- Kabul edilen tanıtıldı IP ön eklerinin sayısını yönetme - Yalnızca sınırlı sayıda **IP** ön eksini destekleyen bir iç ağ altyapısı veya ağ taşıyıcısı olan müşteriler ve ağ taşıyıcısı sınırlı bir sayın üstündeki ön ekleri kabul etmek için ücret alan müşteriler, ağlarına zaten tanıtmış olan ön eklerin toplam sayısını değerlendirmek ve ExpressRoute için en uygun Office 365 uygulamalarını seçmek ister.

- **Azure ExpressRoute** bağlantı hattında gereken bant genişliği miktarını yönetme - Müşteriler İnternet yolu ile ExpressRoute yolu üzerinden Office 365 hizmetlerinin bant genişliği zarfını kontrol etmek ister. Bu, müşterilerin ExpressRoute bant genişliğini İnternet yolu üzerinden Skype Kurumsal ve diğer Office 365 uygulamalara yönlendirmesine olanak sağlar.

Müşterilerin bu hedeflere ulaş Office 365 yardımcı olmak için, ExpressRoute üzerinden tanıt gösterilen IP ön ekleri, aşağıdaki örnekte gösterildiği gibi hizmete özgü BGP topluluk değerleriyle etiketlenir.
  
> [!NOTE]
> Diğer uygulamalarla ilişkilendirilmiş ağ trafiğinin bir yandan topluluk değerine dahil olmasını bekleyebilirsiniz. Bu, paylaşılan hizmetleri ve veri merkezleri olan genel Hizmet Olarak Yazılım tekliflerinde beklenen bir davranıştır. Yukarıdaki iki hedef, yani ön ek sayısını ve/veya bant genişliğini yönetme hedefleri hedeflerken bu mümkün olduğunca en aza indirildi.

|**Hizmet**|**BGP Community Değeri**|**Notlar**|
|:-----|:-----|:-----|
|Exchange Online\*  <br/> |12076:5010  <br/> |EOP Exchange hizmetleri içerir\*  <br/> |
|SharePoint Online\*  <br/> |12076:5020  <br/> |SharePoint Online  <br/> |
|Skype Kurumsal\*  <br/> |12076:5030  <br/> |Skype Kurumsal Online & Microsoft Teams hizmetleri  <br/> |
|Diğer Office 365 hizmetleri\*  <br/> |12076:5100  <br/> |Portal Azure Active Directory yanı sıra kimlik doğrulama ve Dizin Eşitleme senaryoları Office 365 içerir  <br/> |
|\*ExpressRoute'ta yer alan hizmet senaryolarının kapsamı, hızlı uç [Office 365 belgelanmıştır](./urls-and-ip-address-ranges.md).  <br/> \*\*Gelecekte başka hizmetler ve BGP topluluk değerleri eklenebilir. [BGP Topluluklarının geçerli listesine bakın](/azure/expressroute/expressroute-routing).  <br/> |

## <a name="what-are-the-most-common-scenarios-for-using-bgp-communities"></a>BGP topluluklarını kullanmaya en yaygın senaryolar hangileridir?

Müşteriler, Azure ExpressRoute aracılığıyla ağı tarafından kabul edilen IP ön eki gruplarını düzenlemek için BGP topluluklarını kullanabilir; böylelikle, bazı Office 365 hizmetlerinin toplam IP ön ek sayısını ve beklenen bant genişliği zarfını etkileyen. Azure ExpressRoute veya BGP Topluluklarının Office 365 ne olursa olsun tüm kullanıcıların İnternet'e bağlı trafik gerektireceklerini anlamanız önemlidir. Aşağıdaki üç senaryo, bu işlevselliğin en yaygın kullanımlarıdır.
  
### <a name="scenario-1-minimizing-the-number-of-office-365-ip-prefixes"></a>Senaryo 1: IP ön eklerinin Office 365 en aza indirme

Contoso Corporation, şu anda Exchange Online ve SharePoint Online için Office 365 kullanan 50.000 kişilik bir şirkettir. Contoso ExpressRoute gereksinimlerini gözden geçirerek, birçok bölgesel konumda ağ cihazlarının ek 100 yönlendirme girdisi üzerindeki yönlendirme tablosu boyutlarını işleyene olmadığını saptadı. Contoso, ExpressRoute'un tüm IP ön ekleri kümesine tanıt amaçlı toplam IP Office 365 gözden geçirildi ve bunun 100'den fazla olduğu sonucuna varıldı. Ek 100 yönlendirme girdisini altında kalmak için, Contoso Office 365 için ExpressRoute kullanımının kapsamını, ExpressRoute Microsoft eşliği aracılığıyla alınan SharePoint Online BGP topluluk değeri 12076:5020'yi kullanarak kapsam dışında bırakmıştır.

|**Kullanılan BGP topluluk etiketi**|**Azure ExpressRoute üzerinden yönlendirilebilir işlevsellik**|**Gereken İnternet yolları**|
|:-----|:-----|:-----|
|SharePoint  <br/> (12076:5020)  <br/> |SharePoint Online OneDrive İş &amp;  <br/> | DNS, CRL, &amp; CDN istekleri  <br/>  Azure ExpressRoute Office 365 desteklenen diğer tüm hizmetler  <br/>  Diğer tüm Microsoft bulut hizmetleri  <br/>  Office 365 portalında, Office 365 doğrulamada &amp; Office tarayıcıda oturum açın  <br/>  Exchange Online, Exchange Online Protection ve Skype Kurumsal Online  <br/> |

> [!NOTE]
> Her hizmette daha az ön ek sayısına ulaşmak için, hizmetler arasında çok az miktarda çakışma kalıcı olacaktır. Bu beklenen davranıştır.
  
### <a name="scenario-2-scoping-expressroute-and-internal-bandwidth-use-to-some-office-365-services"></a>2. Senaryo: ExpressRoute ve iç bant genişliği kullanımlarını, bazı Office 365 hizmetleriyle sınırlama

Dağıtılmış heterojen bir ağa sahip, çok uluslu büyük bir kuruluş olan Fabrikam Inc, şu hizmetlere Office 365 abonesidir: Exchange Online, SharePoint Online ve Skype Kurumsal Online'a. Fabrikam'ın iç yönlendirme altyapısı yönlendirme tablolarında binlerce IP ön ekini işebilir; Öte yandan Fabrikam, ağ performansı konusunda en hassas olan Office 365 uygulamalarına yalnızca ExpressRoute ve iç bant genişliği sağlamayı ve diğer tüm İnternet bant genişliğini diğer tüm Office 365 kullanmak istiyor.
  
Bu nedenle, Fabrikam Azure ExpressRoute bant genişliğinin kapsamını yalnızca ExpressRoute Microsoft eşliği aracılığıyla alınan Skype Kurumsal Online BGP Community değeri 12076:5030 olacak şekilde kapsamlar. İnternet'e Office 365 kalan ağ trafiği, İnternet çıkış noktalarını kullanmaya devam eder.

|**Kullanılan BGP topluluk etiketi**|**Azure ExpressRoute üzerinden yönlendirilebilir işlevsellik**|**Gereken İnternet yolları**|
|:-----|:-----|:-----|
|Skype Kurumsal  <br/> (12076:5030)  <br/> |Skype, indirmeler, ses, video ve masaüstü paylaşımı ile ilgili daha fazla bilgi  <br/> | DNS, CRL, &amp; CDN istekleri  <br/>  Azure ExpressRoute Office 365 desteklenen diğer tüm hizmetler  <br/>  Diğer tüm Microsoft bulut hizmetleri  <br/>  Office 365 portalında, Office 365 doğrulamada &amp; Office tarayıcıda oturum açın  <br/>  Skype Kurumsal, istemci Skype ipuçlarını, genel IM bağlantısını kontrol edin  <br/>  Exchange Online, Exchange Online Protection ve SharePoint Online  <br/> |

### <a name="scenario-3-scoping-azure-expressroute-for-office-365-services-only"></a>3. Senaryo: Azure ExpressRoute'un Office 365 içincocoping

Woodgrove Bank, çeşitli Microsoft bulut hizmetlerinin müşterisi ve Office 365. Ağ kapasitesini ve tüketimini değerlendirdikten sonra Woodgrove Bank desteklenen hizmetlerde tercih edilen yol olarak Azure ExpressRoute'un dağıtımına Office 365 karar verdi. Yönlendirme tabloları, tüm projelendirme bant genişliği Office 365 IP ön eklerinin tam listesini destekleyenin ve onların sağlamaları gereken Azure ExpressRoute bağlantı hatlarını destekler.
  
Office 365 dışında Microsoft bulut hizmetleriyle ilişkilendirilmiş ağ trafiğinin sağlanması için, Woodgrove Bank Office 365 için ExpressRoute'un Office 365 12076:5010, 12076:5020, 12076:5030, 12076:5030, 12076:5100 ile etiketlenmiş tüm IP ön ekleri için kapsamını genişletmektedir.

|**Kullanılan BGP topluluk etiketi**|**Azure ExpressRoute üzerinden yönlendirilebilir işlevsellik**|**Gereken İnternet yolları**|
|:-----|:-----|:-----|
|Exchange, Skype Kurumsal & Microsoft Teams, SharePoint, &amp; diğer hizmetler  <br/> (12076:5010, 12076:5020, 12076:5030, 12076:5100)  <br/> |&amp; Exchange Online Exchange Online Protection  <br/> SharePoint Online OneDrive İş &amp;  <br/> Skype, indirmeler, ses, video ve masaüstü paylaşımı ile ilgili daha fazla bilgi  <br/> Office 365 portalında, Office 365 doğrulamada &amp; Office tarayıcıda oturum açın  <br/> | DNS, CRL, &amp; CDN istekleri  <br/>  Azure ExpressRoute Office 365 desteklenen diğer tüm hizmetler  <br/>  Diğer tüm Microsoft bulut hizmetleri  <br/> |

## <a name="key-planning-considerations-to-using-bgp-communities"></a>BGP topluluklarını kullanırken planlamada dikkate alınacak önemli noktalar

ExpressRoute'un müşteri ağına tanıtilma ve yayılma yöntemine etki etmek için BGP topluluklarından yararlanmayı seçen müşteriler, aşağıdaki dikkate almaları gerekir:
  
- Ağ tasarımında BGP topluluklarını kullanırken, yönlendirme simetrisini korumak önemlidir. Bazı durumlarda, BGP topluluklarının eklenmesi veya kaldırılması simetrik yönlendirmenin bozuk olduğu bir durum oluşturabilir ve simetrik yönlendirmeyi yeniden oluşturmak için yönlendirme yapılandırmanız güncelleştirilmiş olabilir.

- Azure ExpressRoute'un tanınması BGP topluluk değerleriyle bir müşteri eylemidir. Microsoft, müşteri tarafından yapılandırılan kapsamdan bağımsız olarak, eşleme ilişkisiyle ilişkilendirilmiş tüm IP ön eklerini tanıtacak.

- Azure ExpressRoute, müşterinin atadığı BGP topluluklarına bağlı olarak Microsoft'un ağın hiçbir eylemlerini desteklemez.

- E-Office 365 kullanılan IP ön ekleri yalnızca hizmete özgü BGP topluluk değerleriyle işaretlenir; konuma özgü BGP toplulukları desteklemez. Office 365, doğaları gereği genel hizmetlerdir; kiracının konumu veya Office 365 verileri temel alarak ön ekleri filtrelemek desteklenmiyor. Önerilen yaklaşım, istekte bulunduğu Office 365 hizmetinin IP adresinin fiziksel konumu ne olursa olsun, ağın kullanıcının ağ bulunduğu konumdan Microsoft genel ağına en kısa veya en çok tercih edilen ağ yolunu koordine edecek şekilde yapılandırmaktır.

- Her BGP topluluk değerinde yer alan IP ön ekleri, değerle ilişkilendirilmiş olan Office 365 ip adreslerini içeren alt ağı temsil ediyor. Bazı durumlarda, alt ağ içinde birden Office 365 IP adresleri bulunur ve sonuçta birden çok topluluk değerinde var olan bir IP ön eki vardır. Bu, ayırma parçalanması nedeniyle nadiren de olsa beklenen bir durumdur ve ön ek sayısını veya bant genişliği yönetim hedeflerini etkilemez. Etkiyi en aza indirmek üzere, müşterilerin BGP topluluklardan yararlanmaları durumunda "gerek gerekmesi gerekenleri reddetme" yerine "gerekenlere izin verme" yaklaşımını kullanmaya teşvik Office 365 teşvik edildi.

- BGP topluluklarını kullanmak, temel ağ bağlantısı gereksinimlerini veya bu gereksinimleri kullanmak için gereken yapılandırmayı Office 365. İnternet'e Office 365 müşterilerin yine İnternet'e erişimi olması gerekir.

- Azure ExpressRoute'uncoteunu BGP toplulukları ile olmak, yalnızca iç ağın Microsoft eşleme ilişkisi üzerinden göreceği yönlendirmeleri etkiler. Kapsamı kapsamına alınan yönlendirmeyle birlikte, PAC veya WPAD yapılandırmasının kullanımı gibi ek uygulama düzeyi yapılandırmaları da yapmaya ihtiyacınız olabilir.

- Microsoft tarafından atanan BGP topluluklarını kullanmaya ek olarak, müşteriler iç yönlendirmeyi etkilemek için Azure ExpressRoute aracılığıyla öğrenilen IP ön eklerine Office 365 KENDI BGP topluluklarını da atamayı seçebilirler. Yaygın bir kullanım durumu, verilen her ExpressRoute eşleme konumu aracılığıyla öğrenilen tüm yönlendirmelere BGP topluluğuna dayalı bir konum atamak ve ardından Microsoft'un ağına giden en kısa veya en çok tercih edilen ağ yolunu koordine etmek için bu bilgiyi aşağı akışla müşteri ağına kullanmaktır. Müşteri tarafından atanan BGP topluluklarının proje senaryoları için ExpressRoute ile Office 365 kullanımı, Microsoft'un denetim veya görünürlük kapsamı dışındadır.

İşte geri dönmek için kullanabileceğiniz kısa bir bağlantı: [https://aka.ms/bgpexpressroute365]().
  
## <a name="related-topics"></a>İlgili Konular

[Ağ Office 365 değerlendirme](assessing-network-connectivity.md)
  
[Office 365 için Azure ExpressRoute](azure-expressroute.md)
  
[Daha fazla bağlantı için ExpressRoute Office 365 yönetme](managing-expressroute-for-connectivity.md)
  
[Posta için ExpressRoute ile yönlendirme Office 365](routing-with-expressroute.md)
  
[ExpressRoute ile ağ planlama Office 365](network-planning-with-expressroute.md)
  
[Skype Kurumsal Online'da Medya Kalitesi ve Ağ Bağlantısı Performansı](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[Skype Kurumsal Online'da ExpressRoute ve QoS](https://support.office.com/article/20c654da-30ee-4e4f-a764-8b7d8844431d)
  
[ExpressRoute kullanarak arama akışı](https://support.office.com/article/413acb29-ad83-4393-9402-51d88e7561ab)
  
[Proje için ExpressRoute'u Office 365](implementing-expressroute.md)
  
[BGP toplulukları için destek](/azure/expressroute/expressroute-routing)
  
[Office 365 ve performans geçmişini kullanarak performans ayarlamayı ayarlama](performance-tuning-using-baselines-and-history.md)
  
[Destek için performans sorunlarını giderme Office 365](performance-troubleshooting-plan.md)
  
[Office 365 için Azure ExpressRoute Eğitimi](https://channel9.msdn.com/series/aer)