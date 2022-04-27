---
title: çevrimiçi modern portal site sınırlarını SharePoint
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: SharePoint Online'daki modern siteler için çağrıları SharePoint ve dış uç noktalarla sınırlama gibi performans önerileri hakkında bilgi edinin.
ms.openlocfilehash: a0163cd808ce3eb25da8d1c94fb27ed9d238d75a
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65091159"
---
# <a name="sharepoint-online-modern-portal-site-limits"></a>çevrimiçi modern portal site sınırlarını SharePoint

Bu makale, SharePoint Online'daki modern portal siteleri için performans önerileri sağlar. Modern portal sitesi performansını iyileştirmek ve yaygın performans sorunlarından kaçınmak için bu makaledeki yönergeleri kullanın.

## <a name="performance-considerations-for-modern-portal-sites"></a>Modern portal siteleri için performansla ilgili dikkat edilmesi gerekenler

Performans iyileştirme açısından, modern portal sitelerini benzersiz hale getiren birkaç özellik vardır. SharePoint Online'da işbirliği ve portal siteleri arasındaki temel fark ölçektir. Portal sitelerinin genellikle işbirliği sitelerinden daha fazla sayıda kullanıcıya daha fazla sayfa görünümü sunması beklenir ve büyük olasılıkla daha fazla statik içerik ve daha az düzenlenebilir kaynak içerir. Ayrıca, modern sitelerin mimarisi klasik sitelerden farklıdır, bu nedenle sayfaları işleme ve kod yürütmeyle ilgili işlemlerin çoğu sunucu yerine istemcide gerçekleşir.

Modern portal siteleri için performans iyileştirme öncelikle birkaç genel hedefe odaklanır:

- Her site sayfasının bileşenlerinin toplam boyutunu küçültme
- Görüntüler, stil sayfaları ve betikler gibi yaygın statik dosyaların barındırılması yükünü CDN
- Çağrıları SharePoint ve dış uç noktalarla yalnızca gerekli olanlarla sınırlayın
- Aynı içerik için yinelenen isteklerden kaçının

Bu makaledeki yönergelerin çoğu, SharePoint Online çağrılarını en aza indirmeye ve iyileştirmeye odaklanır. Bir sayfa her yüklendiğinde yinelenen çağrılar yapmak, kullanıcılar için performansı etkiler, bu nedenle bilgiler değişmese bile hizmetten her seferinde alınır. Bu nedenle, SharePoint istekleri tüm kullanıcılar için ortak olan çağrılar veya her bir kullanıcı için gereken çağrılar olarak kategorilere ayırılabilir. Kullanıcı deneyimini iyileştirmek için bu iki çağrı kategorisinin sonuçları önbelleğe alınmalıdır.

>[!NOTE]
>SharePoint Çevrimiçi site sayfalarında belirli performans ölçümlerini analiz etmek için başlangıç noktası olarak SharePoint [için Sayfa Tanılama aracını](./page-diagnostics-for-spo.md) kullanın.

## <a name="modern-portal-site-limits-and-recommendations"></a>Modern portal sitesi sınırları ve önerileri

|**Sınırı**|**Önerilen en büyük değer**|**Notlar**|
|:-----|:-----|:-----|:-----|
|Sayfalar ve haber öğeleri  <br/> |Site başına 5.000  <br/> |Modern bir portal sitesindeki sayfa ve haber öğelerinin sayısını 5.000'in altına sınırlamanızı öneririz.  <br/> |
|Sayfadaki web bölümleri  <br/> |Sayfa başına 20  <br/> |Hem kullanıma kullanıma uygun Microsoft web bölümleri hem de özel web bölümleri dahil olmak üzere sayfa başına toplam 20 veya daha az web bölümü kullanmanızı öneririz. <br/> Daha fazla bilgi için bkz[. SharePoint Çevrimiçi modern site sayfalarında web bölümü performansını iyileştirme](modern-web-part-optimization.md).  <br/> |
|Sayfadaki dinamik web bölümleri  <br/> |Sayfa başına 4  <br/> |En son verileri getirmek için SharePoint için bir veya daha fazla sorgu oluşturan dinamik web bölümleri sayfa başına 4 ile sınırlanmalıdır. _Haber_ web bölümü, dinamik bir web bölümüne örnektir. <br/> Daha fazla bilgi için bkz[. SharePoint Çevrimiçi modern site sayfalarında web bölümü performansını iyileştirme](modern-web-part-optimization.md).    <br/> |
|Güvenlik grupları  <br/> |Site başına 20  <br/> |Güvenlik gruplarının sayısı, modern portal sitelerindeki birçok sorgunun ölçeğini etkiler. Güvenlik grubu sayısını, site başına 20'den fazla olmayan mümkün olduğunca küçük bir kümeyle sınırlamanızı öneririz.  <br/> |
|Site gezintisindeki öğeler  <br/> |Site başına 100  <br/> |Site gezintisine 100'den az öğe eklemenizi ve kullanıma uygun gezinti denetimlerini kullanmanızı öneririz.  <br/> Daha fazla bilgi için bkz. [SharePoint Çevrimiçi modern site sayfalarında sayfa kalınlığını iyileştirme](modern-page-weight-optimization.md). <br/> |
|En büyük görüntü boyutu  <br/> |Görüntü başına 300 Kb  <br/> |Görüntülerin boyutunu 300 kb veya daha küçük olarak sınırlamanızı ve görüntüleri, stil sayfalarını ve betikleri barındırmak için bir CDN kullanmanızı öneririz. <br/>Daha fazla bilgi için bkz. [SharePoint Online modern site sayfalarında görüntüleri iyileştirme](modern-image-optimization.md) ve [SharePoint Online ile Office 365 Content Delivery Network (CDN) kullanma](use-microsoft-365-cdn-with-spo.md).  <br/> |
|Düzenleme haklarına sahip kullanıcılar  <br/> |Site başına 200 kullanıcı  <br/> |SharePoint portal siteleri, içeriği görüntülemek ve kullanmak için iyileştirilmiştir. Düzenleme izinleri ek denetimler indirdiğinden ve bu nedenle bu kullanıcılar için daha yavaş çalıştığından, portaldaki düzenleme izinleri kısıtlı bir kullanıcı grubuyla sınırlandırılmalıdır. Bu nedenle, düzenleme izinlerine sahip çok fazla sayıda kullanıcı genel deneyimi etkiler. <br/> |
|Üçüncü taraf iFrame'ler  <br/> |Sayfa başına 2  <br/> |iFrame'ler javascript, CSS ve çerçeve öğeleri gibi tüm ilişkili içerikler de dahil olmak üzere ayrı bir dış sayfa yüklediklerinden tahmin edilemeyen yavaştır. iFrame'leri kullanmanız gerekiyorsa, bunların sayısını sayfa başına 2 veya daha azla sınırlayın.<br/> Daha fazla bilgi için bkz. [SharePoint Online modern ve klasik yayımlama sitesi sayfalarında iFrame'leri iyileştirme](modern-iframe-optimization.md). <br/> |
|UPA hizmetine yapılan çağrılar  <br/> |Saat başına kullanıcı başına 1  <br/> |UPA (Kullanıcı Profili Uygulaması) hizmetine _istek başına_ çağrı yapmamanızı öneririz. Kullanıcı bilgilerini sorgulamak için [Microsoft Graph API](/graph/call-api) ve [PageContext](/javascript/api/sp-page-context/pagecontext) kullanılabilir.  <br/> UPA hizmet çağrısı gerekiyorsa, gerektiğinde tek bir çağrı yapın ve ardından bilgileri aynı oturumda yeniden kullanmak üzere önbelleğe alın. |
|Taksonomi hizmetine çağrılar  <br/> |Kullanıcı başına saatte 5  <br/> |Taksonomi hizmetine _istek başına_ çağrı yapmamanızı öneririz. Taksonomi hizmeti çağrıları gerekiyorsa, bilgileri aynı oturumda yeniden kullanmak üzere önbelleğe alın. <br/> Daha fazla bilgi için bkz. [SharePoint Çevrimiçi modern ve klasik yayımlama sitesi sayfalarında sayfa çağrılarını iyileştirme](modern-page-call-optimization.md). <br/> |

## <a name="related-topics"></a>İlgili konular

[İyi durumda bir SharePoint portalı oluşturma](/sharepoint/portal-health)

[çevrimiçi SharePoint performansını ayarlama](tune-sharepoint-online-performance.md)

[Office 365 performansını ayarlama](tune-microsoft-365-performance.md)

[çevrimiçi sınırları SharePoint](/office365/servicedescriptions/sharepoint-online-service-description/sharepoint-online-limits)

[Modern SharePoint deneyiminde performans](/sharepoint/modern-experience-performance)

[SharePoint Online portalları için performans kılavuzu](/sharepoint/dev/solution-guidance/portal-performance)
