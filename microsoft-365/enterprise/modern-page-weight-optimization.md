---
title: SharePoint Online modern site sayfalarında sayfa SharePoint en iyi duruma getirme
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
description: SharePoint Online modern site sayfalarında sayfa ağırlıklarını iyileştirmek için Sayfa Tanılama aracını kullanmayı öğrenin.
ms.openlocfilehash: 2c7221befc89fd0385b3e96a31fc7721f012628d
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62988742"
---
# <a name="optimize-page-weight-in-sharepoint-online-modern-site-pages"></a>SharePoint Online modern site sayfalarında sayfa SharePoint en iyi duruma getirme

SharePoint Online modern site sayfaları, gezinti/komut çubuklarının altındaki içerik alanında bulunan ve sayfanın çerçevesini oluşturan diğer HTML kodu dahil olmak üzere sayfanın sayfa içeriğini işlemek için gereken serileştirilmiş kod içerir. Sayfa ağırlık bu HTML kodunun ölçümüdür ve en iyi sayfa yükleme sürelerini sağlamak için sınırlı olması gerekir.

Bu makale, modern site sayfalarınıza sayfa ağırlıklarını azaltmayı anlamanıza yardımcı olur.

>[!NOTE]
>Çevrimiçi modern portallarda performans SharePoint için bkz[. Modern modern portalda SharePoint.](/sharepoint/modern-experience-performance)

## <a name="use-the-page-diagnostics-for-sharepoint-tool-to-analyze-page-weight"></a>Sayfa ağırlıklarını çözümlemek için SharePoint Tanılama aracını kullanma

SharePoint için Sayfa Tanılama aracı, hem SharePointhttps://www.microsoft.com/edge) Online modern portalı hem de klasik yayımlama sitesi sayfalarını analizen yeni Microsoft Edge ve Chrome tarayıcıları için tarayıcı uzantısıdır. Bu araç, sayfanın tanımlanmış bir performans ölçütleri kümesine karşı nasıl bir performans performansına sahip olduğunu gösteren, analize tabi her sayfa için bir rapor sağlar. Yeni uygulama için Sayfa Tanılama aracını yüklemek ve SharePoint için, SharePoint [Online'da Sayfa Tanılama aracını kullanma sayfasını ziyaret edin](page-diagnostics-for-spo.md).

>[!NOTE]
>Sayfa Tanılama aracı yalnızca SharePoint Online için çalışır ve SharePoint sistem sayfasında kullanılamaz.

SharePoint için Sayfa Tanılama aracıyla bir SharePoint site sayfasını çözümleyebilirsiniz; Tanılama testleri bölmesinin **500 KB'ın** altındaki Sayfa ağırlıkları altında sayfa _hakkında bilgileri_ görebilirsiniz. Sayfa kalınlığı taban çizgisi değerinin altında olursa sonuç yeşil, sayfa kalınlığı taban çizgisi değerini aşıyorsa kırmızı görüntülenir.

Olası sonuçlar şunlardır:

- **Dikkat (** kırmızı): Sayfa kalınlığı 500 KB'yi aşıyor
- **Herhangi bir işlem gerekmez** (yeşil): Sayfa ağırlığı 500 KB'ın altında

**500 KB'nin altındaki** Sayfa ağırlık dikkat gerekiyor bölümünde görünüyorsa, ayrıntılar için sonucu tıkleyebilirsiniz.

![Sonuçların SharePoint istekler.](../media/modern-portal-optimization/pagediag-page-weight.png)

## <a name="remediate-page-weight-issues"></a>Sayfa ağırlık sorunlarını düzeltme

Sayfa kalınlığı 500 KB'yi aşıyorsa, web bölümlerinin sayısını azaltarak ve sayfa içeriğini uygun derecede sınırlandırarak genel sayfa yükleme süresini geliştirebilirsiniz.

Sayfa ağırlıklarını azaltmaya yönelik genel kılavuzlar:

- Sayfa içeriğini makul bir miktarla sınırlandırma ve ilgili içerik için birden çok sayfa kullanma.
- Büyük özellik çantaları olan web bölümlerinin kullanımını en aza indirme.
- Mümkün olduğunda etkileşimli olmayan toplama görünümlerini kullanın.
- Resimleri doğru boyutlandırarak, sıkıştırılmış görüntü biçimlerini kullanarak ve bir resimden indirilmalarından emin olarak görüntü boyutlarını en CDN.

Sayfa ağırlıklarını sınırlamaya yönelik ek kılavuzu aşağıdaki makalede bulabilirsiniz:

- [Çalışma sayfasında sayfa performansını SharePoint](/sharepoint/dev/general-development/optimize-page-performance-in-sharepoint)

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