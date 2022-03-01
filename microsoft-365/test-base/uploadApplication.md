---
title: Upload paketinizi geri istiyorum
description: Uygulama, ikili dosyalar ve bağımlılıkları Test Temel'e yükleme
search.appverid: MET150
author: mansipatel-usl
ms.author: rshastri
manager: rshastri
audience: Software-Vendor
ms.topic: troubleshooting
ms.date: 07/06/2021
ms.service: virtual-desktop
ms.localizationpriority: medium
ms.collection: TestBase-M365
ms.custom: ''
ms.reviewer: mapatel
f1.keywords: NOCSH
ms.openlocfilehash: 99b25757b3f7b0b3d4fcd43f97bab2ac303de6fa
ms.sourcegitcommit: b1a2b09edbcfcc62ff3f1ecf5bd8adb1afa344c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2021
ms.locfileid: "63019140"
---
# <a name="step-2-uploading-a-package"></a>2. Adım: Paket Yükleme

Test Temel portalı sayfasında, aşağıda gösterildiği **gibi Upload gezinti** çubuğundaki yeni paket seçeneğine gidin:

:::image type="content" alt-text="Upload bir paket." source="Media/Upload-New-Package.png" lightbox="Media/Upload-New-Package.png":::

Oraya vardikten sonra, aşağıdaki adımları takip edin ve yeni bir paket yükleyin.

## <a name="enter-details-for-your-package"></a>Paketinizin ayrıntılarını girin

Test ayrıntıları sekmesinde, paketinizin adını, sürümünü ve diğer ayrıntılarını istediğiniz gibi yazın.

**Kutudan Çıkma ve** **İşlevsel sınama** bu pano üzerinden yapılabilir.

Aşağıdaki adımlar, paket ayrıntılarınızı doldurmayla ilgili bir kılavuz sağlar:

1. Alana paketinizin verilmesi için gereken adı `Package name` girin.

    > [!NOTE]
    > Girilen paket adı ve sürüm bileşimi, kurum içinde benzersiz olmalıdır. Bu, aşağıda gösterildiği gibi onay işareti tarafından doğrulanır.

    - Bir paketin adını yeniden kullanmak seçerseniz sürüm numarası benzersiz olmalıdır (başka bir ifadeyle, söz konusu adı taşıyan pakette hiç kullanılmamalıdır).

    - Paket adı + sürüm birleşimi benzersizlik denetimine geçemediyse, "Bu paket sürümüyle paketle zaten var" iletisini içeren bir *hata iletisi alırsınız*.

    :::image type="content" alt-text="Paket yönergelerini karşıya yükleme görüntüsü." source="Media/Instructions.png":::

2. "Paket sürümü" alanına bir sürüm girin.

    :::image type="content" alt-text="Paket sürümü." source="Media/ApplicationVersion.png":::

3. Bu pakette çalıştırmak istediğiniz test türünü seçin.

    Hazır **(OOB)** testi, paketinizi *yükleme,* *başlatma*, *kapatma* *ve* kaldırma işlemi gerçekleştirir. Yüklemeden sonra, tek bir kaldırma çalıştırılamadan önce başlatma-kapatma yordamı 30 kez tekrarlanır.

    Bu OOB testi, tüm standart derlemeleri karşılaştıracak şekilde paketiniz üzerinde standart Windows sağlar.

    **İşlevsel test**, karşıya yüklenen test betiklerinizi paketinize yürütür. Betikler karşıya yükleme sırasına göre çalıştırılıyor ve belirli bir betikte başarısız olmak izleyen betiklerin yürütülmesini durduracak.

    > [!NOTE]
    > **Tüm** betikler en çok 80 dakika süreyle çalıştırın.

4. Işletim sistemi güncelleştirme türünü seçin.

    - 'Güvenlik güncelleştirmeleri', paketinizin yayın öncesi aylık güvenlik güncelleştirmeleri için artımlı churn'lara Windows olanak sağlar.
    - 'Özellik güncelleştirmeleri', paketinizin Windows Insider Programı'nın yayın öncesi iki yıllık özellik güncelleştirmeleri derlemelerine karşı Windows sağlar.
    <!---
    Change to the correct picture
    -->
    :::image type="content" alt-text="işletim sistemi güncelleştirme türü." source="Media/OSUpdateType.png":::

5. Güvenlik güncelleştirmesi testlerinin işletim sistemi sürümünü seçin.

    Çoklu seçim açılan listesinden, paketinizin yük Windows işletim sistemi sürümünü seçin.

    - Paketinizi yalnızca İstemci işletim Windows karşı test etmek için, menüden Windows istemci işletim sistemi sürümlerini seçin.
    - Paketinizi yalnızca Windows Server işletim sistemleriyle test etmek için, menü listesinden Windows Server OS sürümlerini seçin.
    - Paketinizi sunucu İstemcisi Windows Windows Server işletim sistemlerine karşı test etmek için, menü listesinden tüm geçerli işletim sistemlerini seçin.

    > [!NOTE]
    > Paketinizi hem Sunucu hem de İstemci OS'ları ile test etmek için, paketin uyumlu olduğundan ve her iki işletim sistemi üzerinde de çalıştırılaya kadar

    :::image type="content" alt-text="Bir işletim sistemi sürümü seçme." source="Media/OSVersion.png":::
    <!---
    Change to the correct picture
    -->

6. Özellik güncelleştirme testleri için seçenekleri belirleyin:

    - "Insider Kanalını Seç" seçeneği üzerinde paketlerinizin `Windows Insider Program Channel` test edilecek derleme olarak bunu seçin.

      Şu anda Insider Beta Kanalında yayınlanan derlemeleri kullanıyoruz.

    - "Insight için işletim sistemi temeli seçin" seçeneğinde, test Windows karşılaştırırken taban çizgisi olarak kullanılacak işletim sistemi sürümünü seçin.

    > [!NOTE]
    > Şu anda Sunucu işletim sistemi için özellik güncelleştirme testlerini DESTEKLEMİYİZ
    <!---
    Note to actual note format for markdown
    -->
    <!---
    Change to the correct picture
    -->
    :::image type="content" alt-text="Özellik güncelleştirmesi testi." source="Media/FeatureUpdate.png":::

7. Tamamlanmış bir Test ayrıntıları sayfası şöyle görünür:

    :::image type="content" alt-text="Test ayrıntılarını görüntüleme." source="Media/TestDetails.png":::

## <a name="next-steps"></a>Sonraki adımlar

Sonraki makalemiz, Ikili dosyaları hizmetimize yükleme makalemizi kapsar.

> [!div class="nextstepaction"]
> [Sonraki adım](binaries.md)

<!---
Add button for next page
-->
