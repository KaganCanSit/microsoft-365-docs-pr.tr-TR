---
title: Cihaz zaman çizelgesinde kullanılan teknikler
description: Uç nokta için Microsoft Defender'da cihaz zaman çizelgesini anlama
keywords: cihaz zaman çizelgesi, uç nokta, MITRE, MITRE ATT&CK, teknikler, taktikler
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: maccruz
author: schmurky
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 897a8691bc7cbc3c03adcbf5befc2a2da8b12294
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2021
ms.locfileid: "62998203"
---
# <a name="techniques-in-the-device-timeline"></a>Cihaz zaman çizelgesinde kullanılan teknikler

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)

Belirli bir cihazda olan olayları çözümerek araştırmalarda daha fazla içgörü elde edebilirsiniz. İlk olarak, Cihazlar listesinde ilgi istediğiniz cihazı [seçin](machines-view-overview.md). Cihaz sayfasında, cihazda meydana gelen **tüm olayları** görüntülemek için Zaman Çizelgesi sekmesini seçin.

## <a name="understand-techniques-in-the-timeline"></a>Zaman çizelgesinin tekniklerini anlama

> [!IMPORTANT]
> Bazı bilgiler, genel önizlemede yer alan ve ticari olarak piyasaya sürmeden önce önemli ölçüde değiştirilmiş olan, önceden değiştirilebilir bir ürün özelliğiyle ilgilidir. Microsoft, burada sağlanan bilgilerle ilgili olarak açık veya zımni hiçbir garanti vermez.

Uç Nokta için Microsoft **Defender'da** Teknikler, olay zaman çizelgesinde ek bir veri türü olur. Teknikler, CK tekniklerini veya [alt tekniklerini kullanarak MITRE ATT&etkinliklerle](https://attack.mitre.org/) ilgili daha fazla içgörü sağlar.

Bu özellik analistlerin bir cihazda gözlemlenen etkinlikleri anlarına yardımcı olarak araştırma deneyimini basitler. Analistler bundan sonra daha fazla araştırma yapmak için karar verir.

Genel önizleme için, Teknikler varsayılan olarak kullanılabilir ve cihazın zaman çizelgesi görüntü olduğunda etkinliklerle birlikte gösterilir.

![Cihaz zaman çizelgesi ekran görüntüsü teknikleri.](images/device-timeline-2.png)

Teknikler kalın metinle vurgulanır ve solda mavi bir simgeyle gösterilir. Buna karşılık gelen MITRE ATT&CK Kimliği ve teknik adı da Ek bilgi altında etiket olarak görünür.

Teknikler için Arama ve Dışarı Aktarma seçenekleri de kullanılabilir.

## <a name="investigate-using-the-side-pane"></a>Yan bölmeyi kullanarak araştırma

İlgili yan bölmesini açmak için bir Teknik seçin. Burada, CK tekniklerini, taktiklerini ve açıklamalarını&ATT tekniklerini ve öngörüleri görebilirsiniz.

İlgili ATT *tekniklerini açmak* için ilgili ATT&CK tekniği sayfasını seçin. Bu sayfa hakkında daha fazla bilgi bulabilirsiniz.

Sağlarda mavi bir simge gördüğünüzde, varlığın ayrıntılarını kopyaabilirsiniz. Örneğin, ilgili bir dosyanın SHA1'ini kopyalamak için mavi sayfa simgesini seçin.

![Varlık ayrıntılarını kopyalama.](images/techniques-side-pane-clickable.png)

Komut satırları için de aynı şeyi yapabiliriz.

![Komut satırı kopyalama.](images/techniques-side-pane-command.png)

## <a name="investigate-related-events"></a>İlgili olayları araştırma

Seçilen Teknik [ile ilgili etkinlikleri](advanced-hunting-overview.md) bulmak üzere gelişmiş av kullanmak için İlgili etkinlikler için **Tekni'yi seçin**. Bu, Teknik ile ilgili olayları bulmak için bir sorgunun olduğu gelişmiş arama sayfasına doğru ilerler.

![İlgili etkinliklerin haberlerini takipte olun.](images/techniques-hunt-for-related-events.png)

> [!NOTE]
> Bir Teknik yan **bölmesindeki İlgili etkinlikler** için Tekni düğmesini kullanarak sorgulama, tanımlanan teknikle ilgili tüm olayları görüntüler, ancak Sorgu sonuçlarına Teknik'in kendisini eklemez.

## <a name="customize-your-device-timeline"></a>Cihazınızın zaman çizelgesini özelleştirme

Cihaz zaman çizelgesinin sağ üst tarafında, zaman çizelgesinde yer alan olay ve teknik sayısını sınırlamak için bir tarih aralığı seçebilirsiniz.

Hangi sütunların açığa çıkar özelleştirebileceğinizi özelleştirebilirsiniz. Ayrıca, bayraklı olaylar için veri türüne veya olay grubuna göre de filtre uygulamanız gerekir.

### <a name="choose-columns-to-expose"></a>Açığa çıkarmak istediğiniz sütunları seçin

Sütunları seç düğmesini seçerek zaman çizelgesinde hangi sütunların açık **olduğunu seçebilirsiniz** .

![Sütunları özelleştirin.](images/filter-customize-columns.png)

Buradan, hangi bilgilerin dahil etmek için ayara ayarlan hazır olduğunu seçin.

### <a name="filter-to-view-techniques-or-events-only"></a>Yalnızca teknikleri veya olayları görüntülemek için filtre uygulama

Yalnızca etkinlikleri veya teknikleri görüntülemek için cihaz zaman çizelgesinden **Filtreler'i** seçin ve görüntülemek için tercih ettiğiniz Veri türünü seçin.

![Filtreler ekran görüntüsü.](images/device-timeline-filters.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Cihazlar listesini görüntüleme ve düzenleme](machines-view-overview.md)
- [Uç nokta cihaz zaman çizelgesi olay bayrakları için Microsoft Defender](device-timeline-event-flag.md)
