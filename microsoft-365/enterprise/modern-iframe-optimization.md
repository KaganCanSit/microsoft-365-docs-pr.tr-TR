---
title: SharePoint Online modern ve klasik yayımlama sitesi sayfalarında iFrame'leri en iyi duruma getirme
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
description: SharePoint Online modern ve klasik yayımlama sitesi sayfalarında iFrame performansını iyileştirmeyi öğrenin.
ms.openlocfilehash: e38dd3922444228cdf54c8ef306fbbd9eafb81c4
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62984328"
---
# <a name="optimize-iframes-in-sharepoint-online-modern-and-classic-publishing-site-pages"></a>SharePoint Online modern ve klasik yayımlama sitesi sayfalarında iFrame'leri en iyi duruma getirme

iFrame'ler, videolar veya diğer medyalar gibi zengin içeriklerin önizlemesini görüntülemek için yararlı olabilir. Bununla birlikte, iFrame'ler SharePoint sitesi sayfasında ayrı bir sayfa yüklensin diye iFrame'e yüklenen içerik büyük resimler, videolar veya başka öğeler içerebilir ve bu da genel sayfa yükleme sürelerine katkıda bulunabilir ve bu içeriği sayfadan kontrol edebilirsiniz. Bu makale, sayfalarınıza iFrame'in kullanıcı gecikme süresini nasıl etkilediğini belirleme ve sık karşılaşılan sorunları düzeltme konularını anlamanıza yardımcı olur.

>[!NOTE]
>Çevrimiçi modern sitelerde performans SharePoint için bkz[. Modern modern site deneyiminde SharePoint.](/sharepoint/modern-experience-performance)

## <a name="use-the-page-diagnostics-for-sharepoint-tool-to-analyze-web-parts-using-iframes"></a>iFrame kullanarak web bölümlerini SharePoint için Sayfa Tanılama aracını kullanma

SharePoint için Sayfa Tanılama aracı, hem SharePointhttps://www.microsoft.com/edge) Online modern portalı hem de klasik yayımlama sitesi sayfalarını analizen yeni Microsoft Edge ve Chrome tarayıcıları için tarayıcı uzantısıdır. Bu araç, sayfanın tanımlanmış bir performans ölçütleri kümesine karşı nasıl bir performans performansına sahip olduğunu gösteren, analize tabi her sayfa için bir rapor sağlar. Yeni uygulama için Sayfa Tanılama aracını yüklemek ve SharePoint için, SharePoint [Online'da Sayfa Tanılama aracını kullanma sayfasını ziyaret edin](page-diagnostics-for-spo.md).

>[!NOTE]
>Sayfa Tanılama aracı yalnızca SharePoint Online için çalışır ve SharePoint sistem sayfasında kullanılamaz.

SharePoint için SharePoint Sayfa Tanılama aracıyla bir site sayfasını çözümlerken, Tanılama testleri bölmesinde iFrame içeren web bölümleri _hakkında bilgi_ görebilirsiniz. Taban çizgisi metrik, modern ve klasik sayfalar için aynıdır.

Olası sonuçlar şunlardır:

- **Dikkat (** kırmızı): Sayfada iFrame **kullanan üç** veya daha fazla web bölümü vardır
- **Geliştirme fırsatları** (sarı): Sayfada iFrame **kullanarak bir** veya iki web bölümü vardır
- **Herhangi bir işlem gerekmez** (yeşil): Sayfada iFrame kullanan hiçbir web bölümü yoktur

**iFrame kullanan Web** bölümleri sonuçların Geliştirme fırsatları veya Dikkat gerekiyor **)** bölümünde sonucu  algıladısa, iFrame içeren web bölümlerini görmek için sonucu tıklarsınız.

![Sayfa Tanılama aracı sonuçları.](../media/modern-portal-optimization/pagediag-iframe-yellow.png)

## <a name="remediate-iframe-performance-issues"></a>iFrame performans sorunlarını düzeltme

Hangi **web bölümlerinin iFrame** içerdiğini ve yavaş sayfa yükleme sürelerine katkıda bulunsa da olacağını belirlemek için, iFrame'leri kullanarak Web bölümlerini Sayfa Tanılama aracında algıladık.

iFrame'ler yapısal olarak yavaştır çünkü javascript, CSS ve çerçeve öğeleri gibi ilişkili tüm içerikler dahil olmak üzere ayrı bir dış sayfa yükleri olur ve bu da site sayfasının yükünü iki veya daha fazla faktörle artırır.

iFrame'in en iyi şekilde kullanımını sağlamak için aşağıdaki yönergeleri izleyin.

- Önizleme küçükse veya etkileşimli olmayan bir önizlemede mümkün olduğunda, iFrame yerine resimler kullanın.
- iFrame'ler kullanılmalıdırsa, bu sddeyi simge durumuna küçültin ve/veya görünüm görünümünün dışında hareket ettirin.
- Excel Word, Office ve PowerPoint gibi eklenmiş PowerPoint dosyaları etkileşimlidir, ancak yüklenmeleri yavaştır. Tüm belgeye bağlantı içeren resim küçük resimleri çoğunlukla daha iyi performans gösterir.
- Eklenmiş YouTube videoları ve Twitter akışları iFrame'te daha iyi performans gösterir, ancak bu tür eklemeleri hemen kullanın.
- Yalıtılmış web bölümleri mantıklı bir istisnadır, ancak görünüm görünümünde sayılarını ve yerleşimlerini en aza indirger.
- iFrame görünüm görünümünün dışında yer alıyorsa, iFrame'in görünümüne gelene kadar işlemeyi geciktirmek için _IntersectionObserver_ kullanmayı göz önünde bulundurabilirsiniz.

Performans sorunlarını düzeltmek için sayfa düzeltmeleri öncesinde, çözümleme sonuçlarında sayfa yükleme sürelerini not edin. Yeni sonucun taban çizgisi standardı içinde olup olmadığını görmek için düzeltmeden sonra aracı yeniden çalıştırın ve bir geliştirme olup olmadığını görmek için yeni sayfa yükleme süresine bakın.

![Sayfa yükleme süresi sonuçları.](../media/modern-portal-optimization/pagediag-page-load-time.png)

>[!NOTE]
>Sayfa yükleme süresi ağ yükü, günün saati ve diğer geçici koşullar gibi çeşitli faktörlere bağlı olarak değişiklik gösterebilir. Sonuçların ortalamasını alarken değişiklik yaparak sayfa yükleme sürelerini birkaç kez test edebilirsiniz.

## <a name="related-topics"></a>İlgili konular

[Çevrimiçi SharePoint performansını ayarlama](tune-sharepoint-online-performance.md)

[Performans Office 365 ayarlama](tune-microsoft-365-performance.md)

[Modern deneyimde SharePoint deneyimi](/sharepoint/modern-experience-performance)