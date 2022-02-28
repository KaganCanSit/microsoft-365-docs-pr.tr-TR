---
title: SharePoint Online modern portal sitesi sınırları
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 10/9/2019
audience: Admin
ms.topic: interactive-tutorial
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Strat_O365_Enterprise
- SPO_Content
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
search.appverid:
- MET150
description: SharePoint Online'da modern siteler için, aramaları SharePoint uç noktalarıyla sınırlama gibi performans önerileri hakkında bilgi alın.
ms.openlocfilehash: 6d09af30f5bdc8866b44047771060ced86362565
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62988785"
---
# <a name="sharepoint-online-modern-portal-site-limits"></a>SharePoint Online modern portal sitesi sınırları

Bu makale, SharePoint Online'daki modern portal siteleri için performans önerileri sağlar. Modern portal sitesi performansını iyileştirmek ve sık karşılaşılan performans sorunlarından kaçınmak için bu makaledeki yönergeleri kullanın.

## <a name="performance-considerations-for-modern-portal-sites"></a>Modern portal sitelerinde performansla ilgili dikkat edilmesi gereken noktalar

Performans iyileştirme açısından, modern portal sitelerini benzersiz hale gelen birkaç özellik vardır. SharePoint Online'da işbirliği ve portal siteleri arasındaki temel fark ölçektir. Portal sitelerinin genel olarak işbirliği sitelerine göre daha fazla sayıda kullanıcıya daha fazla sayfa görüntülemesi beklendiği gibi, daha fazla statik içerik ve daha az düzenlenebilir kaynak içermesi de gerekir. Buna ek olarak, modern sitelerin mimarisi klasik sitelerden farklıdır. Burada sayfaları işleme ve kodu yürütme işlemlerinin çoğu sunucu yerine istemcide  sürer.

Modern portal siteleri için performans iyileştirme öncelikle birkaç genel amaca odaklanıyor:

- Her site sayfasının bileşenlerinin toplam boyutunu azaltma
- Resimler, stil sayfaları ve betikler gibi yaygın statik dosyaların barındırma yükünü CDN
- Çağrıyı yalnızca SharePoint uç noktalarıyla ve dış uç noktalarla sınırlandırma
- Aynı içerik için yinelenen isteklerden kaçınma

Bu makaledeki yönergelerin birçoğu, SharePoint Online'a yapılan çağrıları en aza indirmeye ve iyileştirmeye SharePoint odaklanmaktadır. Bir sayfa her yüklendiğinde yinelenen aramalar yapmak, bilgiler değişmemiş olsa bile hizmetten alına kadar kullanıcıların performansını etkiler. Bu nedenle, gelen istekler SharePoint kullanıcıların ortak olduğu aramalar veya her bir kullanıcı için gerekli aramalar olarak kategorilere ayırabilirsiniz. Kullanıcı deneyimini en iyi duruma getirmek için bu iki arama kategorisinin sonuçları önbelleğe alınarak elde etmek gerekir.

>[!NOTE]
>Çevrimiçi site [sayfalarındaki belirli SharePoint](./page-diagnostics-for-spo.md) ölçümlerini çözümlemek için başlangıç noktası olarak Sayfa Tanılama SharePoint kullanın.

## <a name="modern-portal-site-limits-and-recommendations"></a>Modern portal sitesi sınırları ve önerileri

|**Sınır**|**En fazla önerilen değer**|**Notlar**|
|:-----|:-----|:-----|:-----|
|Sayfalar ve haber öğeleri  <br/> |Site başına 5.000  <br/> |Modern bir portal sitesinde bulunan sayfa ve haber öğelerinin sayısını 5.000'in altına sınırlamanız önerilir.  <br/> |
|Sayfada Web bölümleri  <br/> |Sayfa başına 20  <br/> |Sayfa başına 20 veya daha az sayıda toplam web bölümü kullanmanızı öneririz. Bu, hem ilk kullanmayan Microsoft web bölümleri hem de özel web bölümleri de dahil. <br/> Daha fazla bilgi için bkz. [SharePoint Online modern site sayfalarında web bölümü performansını iyileştirme](modern-web-part-optimization.md).  <br/> |
|Sayfada dinamik web bölümleri  <br/> |Sayfa başına 4  <br/> |En son verileri getirmek için bir veya daha fazla SharePoint sorgular alan dinamik web bölümleri, sayfa başına 4 ile sınırlandırılamaz. _Haberler web_ bölümü, dinamik web bölümü örneğidir. <br/> Daha fazla bilgi için bkz. [SharePoint Online modern site sayfalarında web bölümü performansını iyileştirme](modern-web-part-optimization.md).    <br/> |
|Güvenlik grupları  <br/> |Site başına 20  <br/> |Modern portal sitelerinde, güvenlik gruplarının sayısı birçok sorgunun ölçeğini etkiler. Güvenlik gruplarının sayısını mümkün olduğunca küçük bir kümeyle (site başına 20'den fazla değil) sınırlamanız önerilir.  <br/> |
|Site gezintisinde öğeler  <br/> |Site başına 100  <br/> |Site gezintilerine 100'den az öğe eklemenizi ve ilk kullanımdaki gezinti denetimlerini kullanmanizi öneririz.  <br/> Daha fazla bilgi için bkz. [SharePoint Online modern site sayfalarında sayfa ağırlıklarını en iyi duruma getirme](modern-page-weight-optimization.md). <br/> |
|En büyük resim boyutu  <br/> |Resim başına 300 Kb  <br/> |Resimlerin boyutunu 300 kb/sn veya daha küçük bir boyutla sınırlamayı ve resimleri, stil CDN betikleri barındırmak için yeni bir resim kullanmalarını öneririz. <br/>Daha fazla bilgi için bkz. [SharePoint Online modern site](modern-image-optimization.md) sayfalarında resimleri iyileştirme ve Office 365 Content Delivery Network Online ile [CDN'SharePoint kullanma](use-microsoft-365-cdn-with-spo.md).  <br/> |
|Düzenleme hakları olan kullanıcılar  <br/> |Site başına 200 kullanıcı  <br/> |SharePoint portalı siteleri içeriği görüntülemek ve tüketmek için en iyi duruma getirilmiş sitedir. Düzenleme izinleri ek denetimleri indirecek ve bu nedenle bu kullanıcılar için daha yavaş gerçekleştirecek olduğundan portalda düzenleme izinleri kısıtlanmış bir kullanıcı grubuyla sınırlı olmalı. Bu nedenle, düzenleme izinleri olan çok fazla kullanıcı genel deneyimi etkiler. <br/> |
|Üçüncü taraf iFrame'ler  <br/> |Sayfa başına 2  <br/> |iFrame'ler javascript, CSS ve çerçeve öğeleri gibi ilişkili tüm içerikler de içinde olmak üzere ayrı bir dış sayfa yükleyemleri nedeniyle ne olacağı önceden kestirilemez yavaştır. iFrame kullanmak zorundasanız, sayfa başına bu sayı 2 veya daha az olacak şekilde sınırlandırabilirsiniz.<br/> Daha fazla bilgi için bkz. [SharePoint Online modern ve klasik yayımlama sitesi sayfalarında iFrame'leri iyileştirme](modern-iframe-optimization.md). <br/> |
|UPA hizmetine yapılan aramalar  <br/> |Saatte bir kullanıcı başına 1  <br/> |UPA (Kullanıcı Profili _Uygulaması_ ) hizmetine yapılan istek başına çağrı yapmamanizi öneririz. Kullanıcı [Graph sorgulamak için Microsoft Metin API'si](/graph/call-api) ve [PageContext](/javascript/api/sp-page-context/pagecontext) kullanılabilir.  <br/> UPA hizmet çağrısı gerekiyorsa, gerektiğinde tek bir arama yapmak ve ardından bilgileri aynı oturumda yeniden kullanmak üzere önbelleğe alın. |
|Taksonomi hizmetine yapılan aramalar  <br/> |Saatte 5 kullanıcı başına  <br/> |Taksonomi _hizmetine istek başına_ çağrı yapmamanizi öneririz. Taksonomi hizmeti çağrıları gerekiyorsa, bilgileri aynı oturumda yeniden kullanmak üzere önbelleğe alın. <br/> Daha fazla bilgi için bkz. [SharePoint Online modern ve klasik yayımlama sitesi sayfalarında sayfa aramalarını en iyi duruma getirme](modern-page-call-optimization.md). <br/> |

## <a name="related-topics"></a>İlgili konular

[Sağlıklı bir yaşam SharePoint oluşturma](/sharepoint/portal-health)

[Çevrimiçi SharePoint performansını ayarlama](tune-sharepoint-online-performance.md)

[Performans Office 365 ayarlama](tune-microsoft-365-performance.md)

[SharePoint Online sınırları](/office365/servicedescriptions/sharepoint-online-service-description/sharepoint-online-limits)

[Modern deneyimde SharePoint deneyimi](/sharepoint/modern-experience-performance)

[Çevrimiçi portallarda SharePoint kılavuzu](/sharepoint/dev/solution-guidance/portal-performance)
