---
title: Cihaz zaman çizelgesinde kullanılan teknikler
description: Zaman çizelgesinde cihaz zaman çizelgesini Uç Nokta için Microsoft Defender
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
ms.openlocfilehash: d724b7663bd4484c630e97362eb5766490e1fa8e
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64465915"
---
# <a name="techniques-in-the-device-timeline"></a>Cihaz zaman çizelgesinde kullanılan teknikler

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta için Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)

Belirli bir cihazda olan olayları çözümerek araştırmalarda daha fazla içgörü elde edebilirsiniz. İlk olarak, Cihazlar listesinde ilgi istediğiniz cihazı [seçin](machines-view-overview.md). Cihaz sayfasında, cihazda meydana gelen **tüm olayları** görüntülemek için Zaman Çizelgesi sekmesini seçin.

## <a name="understand-techniques-in-the-timeline"></a>Zaman çizelgesinin tekniklerini anlama

> [!IMPORTANT]
> Bazı bilgiler, genel önizlemede yer alan ve ticari olarak piyasaya sürmeden önce önemli ölçüde değiştirilmiş olan, önceden değiştirilebilir bir ürün özelliğiyle ilgilidir. Microsoft, burada sağlanan bilgilerle ilgili olarak açık veya zımni hiçbir garanti vermez.

Teknikler **Uç Nokta için Microsoft Defender, etkinlik** zaman çizelgesinde ek bir veri türü olur. Teknikler, CK tekniklerini veya [alt tekniklerini kullanarak MITRE ATT&etkinliklerle](https://attack.mitre.org/) ilgili daha fazla içgörü sağlar.

Bu özellik analistlerin bir cihazda gözlemlenen etkinlikleri anlarına yardımcı olarak araştırma deneyimini basitler. Analistler bundan sonra daha fazla araştırma yapmak için karar verir.

Genel önizleme için, Teknikler varsayılan olarak kullanılabilir ve cihazın zaman çizelgesi görüntü olduğunda etkinliklerle birlikte gösterilir.

:::image type="content" source="images/device-timeline-2.png" alt-text="Cihaz zaman çizelgesinde Teknikler" lightbox="images/device-timeline-2.png":::

Teknikler kalın metinle vurgulanır ve solda mavi bir simgeyle gösterilir. Buna karşılık gelen MITRE ATT&CK Kimliği ve teknik adı da Ek bilgi altında etiket olarak görünür.

Teknikler için Arama ve Dışarı Aktarma seçenekleri de kullanılabilir.

## <a name="investigate-using-the-side-pane"></a>Yan bölmeyi kullanarak araştırma

İlgili yan bölmesini açmak için bir Teknik seçin. Burada, CK tekniklerini, taktiklerini ve açıklamalarını&ATT tekniklerini ve öngörüleri görebilirsiniz.

İlgili ATT *tekniklerini açmak* için ilgili ATT&CK tekniği sayfasını seçin. Bu sayfa hakkında daha fazla bilgi bulabilirsiniz.

Sağlarda mavi bir simge gördüğünüzde, varlığın ayrıntılarını kopyaabilirsiniz. Örneğin, ilgili bir dosyanın SHA1'ini kopyalamak için mavi sayfa simgesini seçin.

:::image type="content" source="images/techniques-side-pane-clickable.png" alt-text="Varlık ayrıntılarının kopyaları" lightbox="images/techniques-side-pane-clickable.png":::

Komut satırları için de aynı şeyi yapabiliriz.

:::image type="content" source="images/techniques-side-pane-command.png" alt-text="Komut satırı kopyalama seçeneği" lightbox="images/techniques-side-pane-command.png":::

## <a name="investigate-related-events"></a>İlgili olayları araştırma

Seçilen Teknik [ile ilgili etkinlikleri](advanced-hunting-overview.md) bulmak üzere gelişmiş av kullanmak için İlgili etkinlikler için **Tekni'yi seçin**. Bu, Teknik ile ilgili olayları bulmak için bir sorgunun olduğu gelişmiş arama sayfasına doğru ilerler.

:::image type="content" source="images/techniques-hunt-for-related-events.png" alt-text="İlgili etkinlikler için hunt seçeneği" lightbox="images/techniques-hunt-for-related-events.png":::

> [!NOTE]
> Bir Teknik yan **bölmesindeki İlgili etkinlikler** için Tekni düğmesini kullanarak sorgulama, tanımlanan teknikle ilgili tüm olayları görüntüler, ancak Sorgu sonuçlarına Teknik'in kendisini eklemez.

## <a name="customize-your-device-timeline"></a>Cihazınızın zaman çizelgesini özelleştirme

Cihaz zaman çizelgesinin sağ üst tarafında, zaman çizelgesinde yer alan olay ve teknik sayısını sınırlamak için bir tarih aralığı seçebilirsiniz.

Hangi sütunların açığa çıkar özelleştirebileceğinizi özelleştirebilirsiniz. Ayrıca, bayraklı olaylar için veri türüne veya olay grubuna göre de filtre uygulamanız gerekir.

### <a name="choose-columns-to-expose"></a>Açığa çıkarmak istediğiniz sütunları seçin

Sütunları seç düğmesini seçerek zaman çizelgesinde hangi sütunların açık **olduğunu seçebilirsiniz** .

:::image type="content" source="images/filter-customize-columns.png" alt-text="Sütunları özelleştirebileceğiniz bölme" lightbox="images/filter-customize-columns.png":::


Buradan, hangi bilgilerin dahil etmek için ayara ayarlan hazır olduğunu seçin.

### <a name="filter-to-view-techniques-or-events-only"></a>Yalnızca teknikleri veya olayları görüntülemek için filtre uygulama

Yalnızca etkinlikleri veya teknikleri görüntülemek için cihaz zaman çizelgesinden **Filtreler'i** seçin ve görüntülemek için tercih ettiğiniz Veri türünü seçin.

:::image type="content" source="images/device-timeline-filters.png" alt-text="Filtreler bölmesi" lightbox="images/device-timeline-filters.png":::

## <a name="see-also"></a>Ayrıca bkz.

- [Cihazlar listesini görüntüleme ve düzenleme](machines-view-overview.md)
- [Uç Nokta için Microsoft Defender zaman çizelgesi olay bayraklarını ekleme](device-timeline-event-flag.md)
