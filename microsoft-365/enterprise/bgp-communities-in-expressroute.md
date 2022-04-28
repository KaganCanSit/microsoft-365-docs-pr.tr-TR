---
title: Office 365 senaryoları için ExpressRoute'ta BGP topluluklarını kullanma
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: Office 365 senaryoları için IP ön eklerinin sayısını ve gerekli bant genişliğini yönetmek üzere Azure ExpressRoute'ta BGP topluluklarını kullanmayı öğrenin.
ms.openlocfilehash: 3e7ec6373299741cc1d34c18cc6be5b9366f3de6
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65095784"
---
# <a name="using-bgp-communities-in-expressroute-for-office-365-scenarios"></a>Office 365 senaryoları için ExpressRoute'ta BGP topluluklarını kullanma

Azure ExpressRoute kullanarak Office 365 bağlanmak, Office 365 uç noktalarının dağıtıldığı ağları temsil eden belirli IP alt ağlarının BGP tanıtımlarını temel alır. Office 365 küresel doğası ve Office 365 oluşturan hizmetlerin sayısı nedeniyle, müşterilerin genellikle ağlarında kabul ettikleri reklamları yönetmeleri gerekir. IP alt ağlarının sayısını azaltma; BU makalenin geri kalanında IP ön ekleri olarak adlandırılan BGP ağ yönetimi terminolojisiyle uyumlu hale getirmek için müşteriler için aşağıdaki son hedeflere hizmet eder:
  
- **Kabul edilen tanıtılan IP ön eklerini yönetme - Yalnızca sınırlı sayıda IP ön ekini** destekleyen bir iç ağ altyapısına veya ağ taşıyıcısına sahip müşteriler ve sınırlı bir sayının üzerindeki ön ekleri kabul etmek için ücret alan bir ağ operatörüne sahip müşteriler, ağlarına önceden tanıtılan ön eklerin toplam sayısını değerlendirmek ve ExpressRoute için en uygun Office 365 uygulamaları seçmek ister.

- **Azure ExpressRoute bağlantı hattında gereken bant genişliği miktarını yönetme** - Müşteriler Office 365 hizmetlerinin bant genişliği zarfını ExpressRoute yolu ve İnternet yolu üzerinden denetlemek isteyebilir. Bu, müşterilerin ExpressRoute bant genişliğini Skype Kurumsal gibi belirli uygulamalar için ayırmasına ve kalan Office 365 uygulamalarını İnternet yolu üzerinden yönlendirmesine olanak tanır.

Müşterilere bu hedeflere yardımcı olmak için ExpressRoute üzerinden tanıtılan Office 365 IP ön ekleri, aşağıdaki örnekte gösterildiği gibi hizmete özgü BGP topluluk değerleriyle etiketlenir.
  
> [!NOTE]
> Diğer uygulamalarla ilişkili bazı ağ trafiğinin topluluk değerine eklenmesini beklemelisiniz. Bu, paylaşılan hizmetler ve veri merkezleriyle hizmet olarak genel bir Yazılım teklifi için beklenen davranıştır. Bu, ön ek sayısını ve/veya bant genişliğini yöneten yukarıdaki iki hedefle mümkün olduğunda en aza indirilmiştir.

|**Hizmet**|**BGP Community Değeri**|**Notlar**|
|:-----|:-----|:-----|
|Exchange Online\*  <br/> |12076:5010  <br/> |Exchange ve EOP hizmetlerini içerir\*  <br/> |
|SharePoint Online\*  <br/> |12076:5020  <br/> |SharePoint Online  <br/> |
|Skype Kurumsal\*  <br/> |12076:5030  <br/> |çevrimiçi & Microsoft Teams hizmetlerini Skype Kurumsal  <br/> |
|Diğer Office 365 hizmetleri\*  <br/> |12076:5100  <br/> |Azure Active Directory (Kimlik Doğrulama ve Dizin Eşitleme senaryoları) ve Office 365 Portal hizmetlerini içerir  <br/> |
|\*ExpressRoute'a dahil edilen hizmet senaryolarının kapsamı [Office 365 uç noktaları](./urls-and-ip-address-ranges.md) makalesinde belgelenmiştir.  <br/> \*\*Gelecekte ek hizmetler ve BGP topluluk değerleri eklenebilir. [BgP Topluluklarının geçerli listesine bakın](/azure/expressroute/expressroute-routing).  <br/> |

## <a name="what-are-the-most-common-scenarios-for-using-bgp-communities"></a>BGP topluluklarını kullanmaya yönelik en yaygın senaryolar nelerdir?

Müşteriler, Azure ExpressRoute aracılığıyla ağı tarafından kabul edilen IP ön eki gruplarını düzenlemek için BGP topluluklarını kullanabilir ve bu nedenle belirli Office 365 hizmetlerinin toplam IP ön ek sayısını ve beklenen bant genişliği zarfını etkileyebilir. Azure ExpressRoute veya BGP Toplulukları'nın kullanımından bağımsız olarak tüm Office 365 İnternet'e bağlı trafik gerektirdiğini anlamak önemlidir. Aşağıdaki üç senaryo, bu işlevselliğin en yaygın kullanımlarıdır.
  
### <a name="scenario-1-minimizing-the-number-of-office-365-ip-prefixes"></a>Senaryo 1: Office 365 IP ön eklerinin sayısını en aza indirme

Contoso Corporation, şu anda Exchange Online ve SharePoint Online için Office 365 kullanan 50.000 kişilik bir şirkettir. ExpressRoute gereksinimlerini gözden geçirirken Contoso, ağ cihazlarının birçok bölgesel konumda 100 ek yol girdisi üzerindeki yönlendirme tablosu boyutlarını işleyemediğini belirler. Contoso, ExpressRoute'un tüm Office 365 hizmetleri için tanıtacağı ip ön eklerinin toplam sayısını gözden geçirdi ve 100'ü aştığı sonucuna vardı. Contoso, 100 ek yol girdisinin altında kalmak için Office 365 için ExpressRoute kullanımını yalnızca ExpressRoute Microsoft eşlemesi aracılığıyla alınan SharePoint Çevrimiçi BGP topluluk değeri olan 12076:5020 olarak kapsamına alır.

|**KULLANıLAN BGP topluluk etiketi**|**Azure ExpressRoute üzerinden yönlendirilebilen işlevsellik**|**İnternet yolları gerekli**|
|:-----|:-----|:-----|
|SharePoint  <br/> (12076:5020)  <br/> |çevrimiçi &amp; OneDrive İş SharePoint  <br/> | DNS, CRL, &amp; CDN istekleri  <br/>  Azure ExpressRoute üzerinden özel olarak desteklenmeyen diğer tüm Office 365 hizmetleri  <br/>  Diğer tüm Microsoft bulut hizmetleri  <br/>  Office 365 portal, Office 365 kimlik doğrulaması, &amp; tarayıcıda Office  <br/>  Exchange Online, Exchange Online Protection ve Skype Kurumsal Online  <br/> |

> [!NOTE]
> Her hizmet için daha düşük ön ek sayıları elde etmek için hizmetler arasında en az miktarda çakışma devam eder. Bu beklenen davranıştır.
  
### <a name="scenario-2-scoping-expressroute-and-internal-bandwidth-use-to-some-office-365-services"></a>Senaryo 2: ExpressRoute ve iç bant genişliği kullanımının kapsamını bazı Office 365 hizmetlerinde belirleme

Dağıtılmış heterojen ağa sahip çok uluslu büyük bir kuruluş olan Fabrikam Inc, dahil olmak üzere birçok Office 365 hizmetinin abonesi; Exchange Online, SharePoint Online ve Skype Kurumsal Online. Fabrikam'ın iç yönlendirme altyapısı, yönlendirme tablolarındaki binlerce IP ön ekini işleyebilir; Ancak Fabrikam yalnızca ağ performansına en duyarlı Office 365 uygulamalar için ExpressRoute ve iç bant genişliği sağlamak ve diğer tüm Office 365 uygulamaları için mevcut İnternet bant genişliğini kullanmak istiyor.
  
Bu nedenle Fabrikam, Azure ExpressRoute bant genişliğini yalnızca ExpressRoute Microsoft eşlemesi aracılığıyla alınan Çevrimiçi BGP Community değeri olan 12076:5030 Skype Kurumsal kapsamına alır. Office 365 ile ilişkili kalan ağ trafiği İnternet çıkış noktalarını kullanmaya devam eder.

|**KULLANıLAN BGP topluluk etiketi**|**Azure ExpressRoute üzerinden yönlendirilebilen işlevsellik**|**İnternet yolları gerekli**|
|:-----|:-----|:-----|
|Skype Kurumsal  <br/> (12076:5030)  <br/> |Skype SIP sinyalleri, indirmeler, ses, video ve masaüstü paylaşımı  <br/> | DNS, CRL, &amp; CDN istekleri  <br/>  Azure ExpressRoute üzerinden özel olarak desteklenmeyen diğer tüm Office 365 hizmetleri  <br/>  Diğer tüm Microsoft bulut hizmetleri  <br/>  Office 365 portal, Office 365 kimlik doğrulaması, &amp; tarayıcıda Office  <br/>  telemetri Skype Kurumsal, Skype istemci hızlı ipuçları, genel anlık ileti bağlantısı  <br/>  çevrimiçi Exchange Online, Exchange Online Protection ve SharePoint  <br/> |

### <a name="scenario-3-scoping-azure-expressroute-for-office-365-services-only"></a>Senaryo 3: Yalnızca Office 365 hizmetleri için Azure ExpressRoute kapsamını belirleme

Woodgrove Bank, Office 365 de dahil olmak üzere çeşitli Microsoft bulut hizmetlerinin müşterisidir. Ağ kapasitesini ve tüketimini değerlendirdikten sonra Woodgrove Bank, desteklenen Office 365 hizmetleri için tercih edilen yol olarak Azure ExpressRoute'u dağıtmaya karar verir. Yönlendirme tabloları, tüm Office 365 IP ön eklerini ve sağladıkları Azure ExpressRoute bağlantı hatlarını tüm öngörülen bant genişliği ve gecikme süresi gereksinimlerini destekleyebilir.
  
Woodgrove Bank, Office 365 dışındaki Microsoft bulut hizmetleriyle ilişkili ağ trafiğinin kapsamını Office 365 için ExpressRoute kullanımını belirli BGP topluluk değerleriyle etiketlenmiş tüm IP ön eklerine Office 365 kapsama alır: 12076:5010, 12076:5020, 12076:5030, 12076:5100.

|**KULLANıLAN BGP topluluk etiketi**|**Azure ExpressRoute üzerinden yönlendirilebilen işlevsellik**|**İnternet yolları gerekli**|
|:-----|:-----|:-----|
|Exchange, Skype Kurumsal & Microsoft Teams, SharePoint, &amp; diğer hizmetler  <br/> (12076:5010, 12076:5020, 12076:5030, 12076:5100)  <br/> |&amp; Exchange Online Exchange Online Protection  <br/> çevrimiçi &amp; OneDrive İş SharePoint  <br/> Skype SIP sinyalleri, indirmeler, ses, video ve masaüstü paylaşımı  <br/> Office 365 portal, Office 365 kimlik doğrulaması, &amp; tarayıcıda Office  <br/> | DNS, CRL, &amp; CDN istekleri  <br/>  Azure ExpressRoute üzerinden özel olarak desteklenmeyen diğer tüm Office 365 hizmetleri  <br/>  Diğer tüm Microsoft bulut hizmetleri  <br/> |

## <a name="key-planning-considerations-to-using-bgp-communities"></a>BGP topluluklarını kullanma konusunda önemli planlama konuları

ExpressRoute'un müşteri ağı üzerinden tanıtılma ve yayılma şeklini etkilemek için BGP topluluklarından yararlanmayı seçen müşteriler aşağıdaki konuları dikkate almalıdır:
  
- Ağ tasarımınızda BGP topluluklarını kullanırken yol simetrinin hala korunduğundan emin olmak önemlidir. Bazı durumlarda BGP topluluklarının eklenmesi veya kaldırılması, simetrik yönlendirmenin bozuk olduğu ve simetrik yönlendirmeyi yeniden oluşturmak için yönlendirme yapılandırmanızın güncelleştirileceği bir durum oluşturabilir.

- Azure ExpressRoute'un kapsamını BGP topluluk değerleriyle belirleme, bir müşteri eylemidir. Microsoft, müşteri tarafından yapılandırılan kapsam belirlemeden bağımsız olarak eşleme ilişkisiyle ilişkili tüm IP ön eklerini tanıtacaktır.

- Azure ExpressRoute, müşteri tarafından atanan BGP topluluklarını temel alarak Microsoft'un ağında herhangi bir eylemi desteklemez.

- Office 365 tarafından kullanılan IP ön ekleri yalnızca hizmete özgü BGP topluluk değerleriyle işaretlenir, konuma özgü BGP toplulukları desteklenmez. Office 365 hizmetleri doğası gereği geneldir; kiracının konumuna veya Office 365 buluttaki verilere göre ön eklerin filtrelenmesi desteklenmez. Önerilen yaklaşım, istekte bulunduğu Office 365 hizmetinin IP adresinin fiziksel konumu ne olursa olsun, ağınızı kullanıcının ağ konumundan Microsoft genel ağına en kısa veya en çok tercih edilen ağ yolunu koordine etmek için yapılandırmaktır.

- Her BGP topluluk değerine dahil edilen IP ön ekleri, değerle ilişkilendirilmiş Office 365 uygulamasının IP adreslerini içeren bir alt ağı temsil eder. Bazı durumlarda, birden çok Office 365 uygulamanın bir alt ağ içinde IP adresleri vardır ve bu da birden fazla topluluk değerinde bir IP ön eki olmasıyla sonuçlanır. Bu durum nadiren de olsa ayırma parçalanması nedeniyle beklenen bir davranıştır ve ön ek sayısını veya bant genişliği yönetimi hedeflerini etkilemez. Müşterilerin, etkiyi en aza indirmek için BGP topluluklarından yararlanırken "gerekmeyenleri reddetmek" yerine "gerekenlere izin ver" yaklaşımını kullanmaları Office 365.

- BGP topluluklarının kullanılması, Office 365 kullanmak için gereken temel ağ bağlantısı gereksinimlerini veya yapılandırmasını değiştirmez. Office 365 erişmek isteyen müşterilerin İnternet'e erişebilmesi gerekir.

- Azure ExpressRoute'un kapsamını BGP topluluklarıyla belirleme, yalnızca iç ağınızın Microsoft eşleme ilişkisi üzerinden görebileceği yolları etkiler. Kapsamlı yönlendirmeyle birlikte PAC veya WPAD yapılandırması kullanımı gibi ek uygulama düzeyi yapılandırmaları yapmanız gerekebilir.

- Microsoft tarafından atanan BGP topluluklarını kullanmaya ek olarak müşteriler, iç yönlendirmeyi etkilemek için Azure ExpressRoute aracılığıyla öğrenilen IP ön eklerini Office 365 için kendi BGP topluluklarını atamayı seçebilir. Popüler bir kullanım örneği, belirli bir ExpressRoute eşleme konumu aracılığıyla öğrenilen tüm yollara konum tabanlı bir BGP topluluğu atamak ve ardından bu bilgileri müşteri ağında aşağı akış kullanarak Microsoft'un ağına en kısa veya en çok tercih edilen ağ yolunu koordine etmektir. müşteri tarafından atanan BGP topluluklarının Office 365 senaryolar için ExpressRoute ile kullanılması Microsoft denetimi veya görünürlüğü kapsamı dışındadır.

İşte geri dönmek için kullanabileceğiniz kısa bir bağlantı: [https://aka.ms/bgpexpressroute365]().
  
## <a name="related-topics"></a>İlgili Konular

[Office 365 ağ bağlantısını değerlendirme](assessing-network-connectivity.md)
  
[Office 365 için Azure ExpressRoute](azure-expressroute.md)
  
[Office 365 bağlantısı için ExpressRoute'u yönetme](managing-expressroute-for-connectivity.md)
  
[Office 365 için ExpressRoute ile Yönlendirme](routing-with-expressroute.md)
  
[Office 365 için ExpressRoute ile Ağ planlaması](network-planning-with-expressroute.md)
  
[Skype Kurumsal Online'da Medya Kalitesi ve Ağ Bağlantısı Performansı](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[Skype Kurumsal Online'da ExpressRoute ve QoS](https://support.office.com/article/20c654da-30ee-4e4f-a764-8b7d8844431d)
  
[ExpressRoute kullanarak çağrı akışı](https://support.office.com/article/413acb29-ad83-4393-9402-51d88e7561ab)
  
[Office 365 için ExpressRoute Uygulama](implementing-expressroute.md)
  
[BGP toplulukları için destek](/azure/expressroute/expressroute-routing)
  
[Temelleri ve performans geçmişini kullanarak performans ayarlamayı Office 365](performance-tuning-using-baselines-and-history.md)
  
[Office 365 için performans sorunlarını giderme planı](performance-troubleshooting-plan.md)
  
[Office 365 Eğitimi için Azure ExpressRoute](https://channel9.msdn.com/series/aer)