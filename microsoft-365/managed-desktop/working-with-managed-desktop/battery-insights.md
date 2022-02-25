---
title: Pil içgörüleri
description: Öngörülen pil ömrü ve en üst düzey güç tüketicileri ile ilgili verileri gösteren bir rapor
keywords: Microsoft Yönetilen Masaüstü, Microsoft 365, hizmet, belgeler
ms.service: m365-md
author: jaimeo
ms.localizationpriority: normal
ms.collection: M365-modern-desktop
ms.author: jaimeo
manager: laurawi
ms.topic: article
audience: Admin
ms.openlocfilehash: 32ab3a984d5ab46aac26989518cd3e570082d688
ms.sourcegitcommit: cebbdd393dcfd93ff43a1ab66ad70115853f83e7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/03/2021
ms.locfileid: "62959645"
---
# <a name="battery-insights"></a>Pil içgörüleri
Bu görünüm, Microsoft Yönetilen Masaüstü cihazlarınız için güç, pil ve uygulama kullanımı ölçümleri sağlar. Bu amaçla, bir uygulama çalışıyorsa ve odakta ise "kullanımda" olarak kabul edilir.

Kullanım verilerini görüntülemek için Pil **sekmesini** seçin.

![Pil bölmesi: Sol üstte cihaz modeli başına pil ömrü, sağ üstte en yüksek enerji tüketicileri (uygulama tarafından) ve içgörüler tablosu altta öngörüler var. Sağ üst kısımda bulunan Belgeler bağlantısı](../../media/insights_battery.png)

## <a name="predicted-battery-life"></a>Öngörülen pil ömrü

Öngörülen **pil ömrü alanında** , cihazlarınız için, cihaz modeline göre düzenlenmiş beklenen pil ömrü için tahminler sağlaruz.

> [!NOTE]
> Bu veriler, Microsoft Yönetilen Masaüstü dağıtımında yer alan ve aynı zamanda verileri raporlamakta olan <em></em> cihazların rastgele bir seçiminden gelen örnekleme enerji kullanımından, kullanım süresinden ve pil kapasitesinden türetilen bilgilerdir.

Tablo, öngörülen pil ömrü (saat içinde), diğer Microsoft Yönetilen Masaüstü dağıtımlarında aynı modeller için ortalama pil ömrü ve bu verileri ortamınıza bildiren cihazların sayısını sağlar. Sütun başlıklarını seçerek verileri sırala.



## <a name="top-energy-consumers"></a>En enerji tüketicileri

En **enerji tüketicileri alanında** , ortamınıza en fazla enerjiyi miliWatt saat (mWh) cinsinden tüketen uygulamaları bulabilirsiniz. Gösterilen uygulamalar, sol tarafta bulunan Tahmini pil ömrü bölümünde **belirli bir cihaza** göre gösterilir. Örneğin, Microsoft Surface Book 2 cihaz için uygulama başına tüketimini görmek için pil ömrü alanında bu satırı seçin. Herhangi bir model seçmezsiniz, gösterilen uygulama tüketimi verileri toplu olarak verilerimiz olan tüm uygulamalara göre hazır olur.

 Her uygulama için renkli kesimler, uygulamanın enerji kullanımını şu kategoriler arasında dağılımını gösterir:

- CPU
- Görüntü
- Ağ
- Diğer

"Diğer", disk etkinliği, mobil geniş bant kullanımı ve iç direncin kaybolan enerji gibi çeşitli kaynaklar tarafından enerji tüketimini içerebilir. 

Sağ üstteki menüyü kullanarak bu görünümü yalnızca ön plan uygulamalarını, arka plan uygulamalarını veya her ikisini birden gösterecek şekilde filtre yapabilirsiniz. Ön plan uygulamaları, fareyle bir şey seçme gibi son 28 gün içinde kullanıcı etkileşimi olan uygulamalardır.

## <a name="insights"></a>Analizler

En **Analizler** alanı, CPU ve ağ kategorilerinde en çok tüketen üç enerji tüketicisini gösterir. Bu öğeler, tüm Microsoft Tarafından Yönetilen Masaüstü dağıtımları ile karşılaştırıldığında ortalamadan daha yüksek enerji tüketiliyor. Görüntü kaynağını göster yok, çünkü cihaz kullanım süresine ve ekran parlaklığı ayarlarına büyük ölçüde bağlıdır. 

Daha fazla bilgi için **Ayrıntılar sütunundaki** listeleri seçin.

## <a name="battery-optimization"></a>Pil iyileştirme

Windows 10, Microsoft [Yönetilen Masaüstü cihazlarında](https://support.microsoft.com/help/20443/windows-10-battery-saving-tips) güç kullanımını geliştirmek ve pil ömrünü artırmak için sayısız cihaz ayarı sunar. Bu ayarlardan bazıları diğer Windows yardımcı olabilir, bu nedenle aynı zamanda kuruluşta cihazın rolü gibi diğer etmenleri de dikkate alacaktır. Windows desteği, bu pil tasarrufu [ipuçlarının bir listesini sağlar](https://support.microsoft.com/help/20443/windows-10-battery-saving-tips).

Kullanıcılar, yönetici yükseltmesine veya desteğine gerek kalmadan bazı ayarları kendi başına değiştirebilir. Diğer ayarlar için, kuruluşun IT yöneticisinden destek gerekir.
