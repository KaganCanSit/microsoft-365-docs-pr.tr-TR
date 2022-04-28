---
title: SharePoint Çevrimiçi modern site sayfalarında görüntüleri iyileştirme
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: SharePoint Online modern site sayfalarında resimleri iyileştirmek için SharePoint Online'daki araçları kullanmayı öğrenin.
ms.openlocfilehash: 102555e25e48af19432a26e6e2a0cb17c78044b3
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65093843"
---
# <a name="optimize-images-in-sharepoint-online-modern-site-pages"></a>SharePoint Çevrimiçi modern site sayfalarında görüntüleri iyileştirme

Bu makale, SharePoint Çevrimiçi modern site sayfalarında resimleri nasıl iyileştirebileceğinizi anlamanıza yardımcı olur.

Klasik yayımlama sitelerindeki görüntüleri iyileştirme hakkında bilgi için bkz. [SharePoint Online için görüntü iyileştirme](image-optimization-for-sharepoint-online.md)...

>[!NOTE]
>SharePoint Çevrimiçi modern portallardaki performans hakkında daha fazla bilgi için bkz. [Modern SharePoint deneyiminde performans](/sharepoint/modern-experience-performance).

## <a name="use-the-page-diagnostics-for-sharepoint-tool-to-analyze-image-optimization"></a>Görüntü iyileştirmeyi analiz etmek için SharePoint için Sayfa Tanılama aracını kullanma

SharePoint için Sayfa Tanılama aracı, hem SharePoint Çevrimiçi modern portalı hem de klasik yayımlama sitesi sayfalarını analiz eden yeni Microsoft Edge (https://www.microsoft.com/edge) ve Chrome tarayıcıları) için bir tarayıcı uzantısıdır. Araç, analiz edilen her sayfa için sayfanın tanımlı bir performans ölçütleri kümesine göre nasıl performans gösterdiğini gösteren bir rapor sağlar. SharePoint için Sayfa Tanılama aracını yüklemek ve hakkında bilgi edinmek için [SharePoint Online için Sayfa Tanılama aracını kullanma](page-diagnostics-for-spo.md) sayfasını ziyaret edin.

>[!NOTE]
>Sayfa Tanılama aracı yalnızca SharePoint Online için çalışır ve SharePoint sistem sayfasında kullanılamaz.

SharePoint için Sayfa Tanılama aracıyla SharePoint modern bir siteyi analiz ettiğinizde, _Tanılama testleri_ bölmesinde büyük görüntüler hakkındaki bilgileri görebilirsiniz.

Olası sonuçlar şunlardır:

- **Dikkat gerekiyor** (kırmızı): Sayfada boyutu 300 KB'ın üzerinde **bir veya daha fazla** resim var
- **Eylem gerekmez** (yeşil): Sayfada boyutu 300 KB'ın üzerinde resim yok

**Algılanan Büyük görüntüler** sonucu sonuçların **Dikkat gerekli** bölümünde görünüyorsa, ek ayrıntıları görmek için sonuda tıklayabilirsiniz.

![Sayfa Tanılama aracı sonuçları.](../media/modern-portal-optimization/pagediag-large-images.png)

## <a name="remediate-large-image-issues"></a>Büyük görüntü sorunlarını düzeltme

Bir sayfada boyutu 300 KB'ın üzerinde görüntüler varsa, hangi görüntülerin çok büyük olduğunu görmek için **Algılanan büyük resimler** sonucunu seçin. Modern SharePoint Çevrimiçi sayfalarında, tarayıcı penceresinin boyutuna ve istemci monitörün çözünürlüğüne bağlı olarak görüntülerin işlemeleri otomatik olarak sağlanır ve boyutlandırılır. SharePoint Online'a yüklemeden önce resimleri her zaman web kullanımı için iyileştirmeniz gerekir. Çok büyük görüntülerin boyutu ve çözünürlüğü otomatik olarak azaltılır ve bu da beklenmeyen işleme özelliklerine neden olabilir.

Performans sorunlarını düzeltmek için sayfa düzeltmeleri yapmadan önce, çözümleme sonuçlarında sayfa yükleme süresini not edin. Yeni sonucun temel standart içinde olup olmadığını görmek için düzeltmenizden sonra aracı yeniden çalıştırın ve bir iyileştirme olup olmadığını görmek için yeni sayfa yükleme süresini denetleyin.

![Sayfa yükleme süresi sonuçları.](../media/modern-portal-optimization/pagediag-page-load-time.png)

>[!NOTE]
>Sayfa yükleme süresi, ağ yükü, günün saati ve diğer geçici koşullar gibi çeşitli faktörlere bağlı olarak farklılık gösterebilir. Sonuçları ortalamanıza yardımcı olacak değişiklikler yapmadan önce ve sonra sayfa yükleme süresini birkaç kez test etmelisiniz.

## <a name="related-topics"></a>İlgili konular

[çevrimiçi SharePoint performansını ayarlama](tune-sharepoint-online-performance.md)

[Office 365 performansını ayarlama](tune-microsoft-365-performance.md)

[Modern SharePoint deneyiminde performans](/sharepoint/modern-experience-performance)

[İçerik teslim ağları](content-delivery-networks.md)

[SharePoint Online ile Office 365 Content Delivery Network (CDN) kullanma](use-microsoft-365-cdn-with-spo.md)