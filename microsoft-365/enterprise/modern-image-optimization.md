---
title: SharePoint Online modern site sayfalarında resimleri iyileştirme
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
ms.custom:
- Adm_O365
- seo-marvel-apr2020
ms.reviewer: sstewart
search.appverid:
- MET150
description: SharePoint Online modern site sayfalarındaki resimleri iyileştirmek için SharePoint Online'da bulunan SharePoint araçları kullanmayı öğrenin.
ms.openlocfilehash: 85280dfc903c56c89308c50fa94979fd98b2003c
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62984019"
---
# <a name="optimize-images-in-sharepoint-online-modern-site-pages"></a>SharePoint Online modern site sayfalarında resimleri iyileştirme

Bu makale, SharePoint Online modern site sayfalarında resimleri SharePoint anlamanıza yardımcı olur.

Klasik yayımlama sitelerinde resimleri iyileştirme hakkında bilgi için bkz. [SharePoint Online için görüntü iyileştirme](image-optimization-for-sharepoint-online.md).

>[!NOTE]
>Çevrimiçi modern portallarda performans SharePoint için bkz[. Modern modern portalda SharePoint.](/sharepoint/modern-experience-performance)

## <a name="use-the-page-diagnostics-for-sharepoint-tool-to-analyze-image-optimization"></a>Resim iyileştirmeyi çözümlemek için SharePoint Tanılama aracını kullanma

SharePoint için Sayfa Tanılama aracı, hem SharePointhttps://www.microsoft.com/edge) Online modern portalı hem de klasik yayımlama sitesi sayfalarını analizen yeni Microsoft Edge ve Chrome tarayıcıları için tarayıcı uzantısıdır. Bu araç, sayfanın tanımlanmış bir performans ölçütleri kümesine karşı nasıl bir performans performansına sahip olduğunu gösteren, analize tabi her sayfa için bir rapor sağlar. Yeni uygulama için Sayfa Tanılama aracını yüklemek ve SharePoint için, SharePoint [Online'da Sayfa Tanılama aracını kullanma sayfasını ziyaret edin](page-diagnostics-for-spo.md).

>[!NOTE]
>Sayfa Tanılama aracı yalnızca SharePoint Online için çalışır ve SharePoint sistem sayfasında kullanılamaz.

Yeni bir modern siteyi SharePoint Tanılama aracıyla modern bir siteyi SharePoint, büyük resimlerle ilgili bilgileri Tanılama _testleri bölmesinde_ görebilirsiniz.

Olası sonuçlar şunlardır:

- **Dikkat (** kırmızı): Sayfa boyutu 300 **KB'ın** üzerinde olan bir veya daha fazla resim içeriyor
- **Herhangi bir işlem gerekmez** (yeşil): Sayfa boyutu 300 KB'yi geçen hiç resim içeriyor

Algılanan **büyük resimler sonucu sonuçların** Dikkat gerekiyor bölümünde görünüyorsa, ek ayrıntıları görmek için sonucu tıkabilirsiniz.

![Sayfa Tanılama aracı sonuçları.](../media/modern-portal-optimization/pagediag-large-images.png)

## <a name="remediate-large-image-issues"></a>Büyük resim sorunlarını düzeltme

Bir sayfa boyutu 300 KB'nin üzerinde olan resimler içeriyorsa, hangi  resimlerin fazla büyük olduğunu görmek için Algılanan büyük resimler sonucu seçin. Modern SharePoint Online sayfalarında, görüntü yorumları tarayıcı penceresinin boyutuna ve istemci monitör çözünürlüğüne bağlı olarak otomatik olarak sağlanır ve boyutlandırılır. SharePoint Online'a yüklemeden önce resimleri web kullanımı için her SharePoint gerekir. Çok büyük resimlerin boyutu ve çözünürlüğü otomatik olarak azaltılır ve bu da beklenmedik işleme özelliklerine neden olabilir.

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