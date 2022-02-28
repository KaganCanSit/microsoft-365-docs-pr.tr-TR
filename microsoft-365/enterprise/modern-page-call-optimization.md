---
title: SharePoint Online modern ve klasik yayımlama sitesi sayfalarında sayfa aramalarını en iyi duruma getirme
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 03/11/2020
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- SPO_Content
f1.keywords:
- CSH
ms.custom: Adm_O365
ms.reviewer: sstewart
search.appverid:
- MET150
description: SharePoint Online'da, çağrı sayısını SharePoint Online hizmeti uç noktalarıyla sınırlandırarak modern ve klasik yayımlama sitesi sayfalarını nasıl en SharePoint öğrenin.
ms.openlocfilehash: 298e928f339d82f472f73e22998b8762461cc209
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62988625"
---
# <a name="optimize-page-calls-in-sharepoint-online-modern-and-classic-publishing-site-pages"></a>SharePoint Online modern ve klasik yayımlama sitesi sayfalarında sayfa aramalarını en iyi duruma getirme

Çevrimiçi SharePoint klasik yayımlama sitelerinin her ikisi de özellikler ve CDN'lerden veri yük SharePoint bağlantılar içerir. Bir sayfa tarafından ne kadar çok çağrı yapılırsa, sayfanın yüklenmesi o kadar uzun sürer. Bu, son kullanıcının **gecikme süresini veya EUPL'i** **algıladığı olarak bilinir**.

Bu makale, modern ve klasik yayımlama sitesi sayfalarından dış uç noktalara yapılan çağrıların sayısını ve etkisini belirlemenin ve son kullanıcının gecikme süresini algıladığı etkiyi sınırlamayı anlamanıza yardımcı olur.

>[!NOTE]
>Çevrimiçi modern portallarda performans SharePoint için bkz[. Modern modern portalda SharePoint.](/sharepoint/modern-experience-performance)

## <a name="use-the-page-diagnostics-for-sharepoint-tool-to-analyze-page-calls"></a>Sayfa aramalarını çözümlemek için SharePoint Tanılama aracını kullanma

SharePoint için Sayfa Tanılama aracı, hem SharePointhttps://www.microsoft.com/edge) Online modern portalı hem de klasik yayımlama sitesi sayfalarını analizen yeni Microsoft Edge ve Chrome tarayıcıları için tarayıcı uzantısıdır. Bu araç, sayfanın tanımlanmış bir performans ölçütleri kümesine karşı nasıl bir performans performansına sahip olduğunu gösteren, analize tabi her sayfa için bir rapor sağlar. Yeni uygulama için Sayfa Tanılama aracını yüklemek ve SharePoint için, SharePoint [Online'da Sayfa Tanılama aracını kullanma sayfasını ziyaret edin](page-diagnostics-for-spo.md).

>[!NOTE]
>Sayfa Tanılama aracı yalnızca SharePoint Online için çalışır ve SharePoint sistem sayfasında kullanılamaz.

SharePoint için Sayfa Tanılama aracıyla bir SharePoint sitesi sayfasını çözümleyebilirsiniz; Dış aramalar hakkında bilgileri Tanılama testleri bölmesindeki SharePoint istekleri _sonucunda_ görebilirsiniz. Site sayfasında arama taban çizgisi sayısından daha az arama varsa, çizgi yeşil, sayfa taban çizgisi numarasını aşıyorsa kırmızı görüntülenir. Taban çizgisi numarası, modern ve klasik sayfalar için farklıdır, çünkü klasik site sayfalarında HTTP1.1 ve modern sayfalar HTTP2.0 kullanır:

- Modern site sayfalarında **25'den fazla arama** içermesi gerekir
- Klasik yayımlama sayfalarında **6'dan fazla arama** içermesi gerekir

Olası sonuçlar şunlardır:

- **Dikkat (** kırmızı): Sayfa, temel çağrı sayısını aşıyor
- **Herhangi bir işlem** gerekmez (yeşil): Sayfa, temel arama sayısından daha az arama içeriyor

Bu **kısmı** SharePoint İstekler sonucu Dikkat gerekiyor bölümünde görünüyorsa, sayfada  toplam arama sayısı ve URL'lerin listesi gibi ayrıntılar için sonucu tıkleyebilirsiniz.

![Sonuçların SharePoint istekler.](../media/modern-portal-optimization/pagediag-requests.png)

## <a name="remediate-performance-issues-related-to-too-many-calls-on-a-page"></a>Bir sayfada çok fazla çağrıyla ilgili performans sorunlarını düzeltme

Bir sayfada çok fazla çağrı varsa, yinelenen çağrılar, toplu olarak iş yapılan aramalar veya önbelleğe **alınmış** veri dönüşecek aramalar olup olmadığını belirlemek için SharePoint'ye istekler sonuçları'nın URL'leri listesini kullanabilirsiniz.

**REST aramalarını toplu olarak çalıştırmak** performans yükünü azaltmaya yardımcı olabilir. API arama toplu işlemi hakkında daha fazla bilgi için bkz [. REST API'leriyle toplu işlem istekleri yapma](/sharepoint/dev/sp-add-ins/make-batch-requests-with-the-rest-apis).

API **aramalarının** sonuçlarını depolamak için önbellek kullanmak, istemcinin sonraki her sayfa yüklemesi için ek çağrı yapmak yerine önbelleğe alınmış verileri kullanmasına izin vererek, sıcak bir isteğin performansını geliştirebilir. İş gereksinimine bağlı olarak bu çözüme yaklaşımda birçok yol vardır. Normalde veriler tüm kullanıcılar için aynı olacaksa, [_Azure YenidenDis_](https://azure.microsoft.com/services/cache/) önbelleği gibi bir orta katman önbelleğe alma hizmeti kullanmak, kullanıcıların verileri doğrudan SPO'dan değil de önbellek hizmetlerinden istenecek olması nedeniyle, bir sitede API trafiğini önemli ölçüde azaltmaya yönelik harika bir seçenektir. Yalnızca orta katmanın önbelleğini yenilemek için gereken SPO çağrılarıdır. Veriler tek tek kullanıcı temelinde dalgalanma olacaksa, en iyisi LocalStorage ve hatta Tanımlama Bilgisi gibi bir istemci tarafı önbelleği uygulamak olabilir. Bu işlem, aynı kullanıcı tarafından önbellek süresi boyunca daha sonra yapılan sonraki istekleri eleyerek arama hacmini azaltmaya devam eder, ancak ayrılmış bir önbellek hizmetine göre daha az verimli olur. PnP, LocalStorage'i çok az ek geliştirmeyle birlikte kullanabileceğiniz şekilde olanak sağlar.

Performans sorunlarını düzeltmek için sayfa düzeltmeleri öncesinde, çözümleme sonuçlarında sayfa yükleme sürelerini not edin. Yeni sonucun taban çizgisi standardı içinde olup olmadığını görmek için düzeltmeden sonra aracı yeniden çalıştırın ve bir geliştirme olup olmadığını görmek için yeni sayfa yükleme süresine bakın.

![Sayfa yükleme süresi sonuçları.](../media/modern-portal-optimization/pagediag-page-load-time.png)

>[!NOTE]
>Sayfa yükleme süresi ağ yükü, günün saati ve diğer geçici koşullar gibi çeşitli faktörlere bağlı olarak değişiklik gösterebilir. Sonuçların ortalamasını alarken değişiklik yaparak sayfa yükleme sürelerini birkaç kez test edebilirsiniz.

## <a name="related-topics"></a>İlgili konular

[Çevrimiçi SharePoint performansını ayarlama](tune-sharepoint-online-performance.md)

[Performans Office 365 ayarlama](tune-microsoft-365-performance.md)

[Modern deneyimde SharePoint deneyimi](/sharepoint/modern-experience-performance)

[İçerik teslim ağları](content-delivery-networks.md)

[CDN Online ile Office 365 Content Delivery Network (CDN) SharePoint kullanma](use-microsoft-365-cdn-with-spo.md)