---
title: Paketinizi karşıya yükleyin
description: Uygulamanızı, ikili dosyalarını ve bağımlılıklarını Test Temeli'ne yükleme
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
ms.openlocfilehash: 9ee299c0972ed4e286e5a660f5082dd5632167e4
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/19/2022
ms.locfileid: "64934279"
---
# <a name="upload-your-test-base-package-zip"></a>Test Temeli paketinizi (Zip) Upload 

Test Temeli portalı sayfasında, aşağıda gösterildiği gibi sol gezinti **çubuğundaki yeni paket Upload** seçeneğine gidin:

:::image type="content" alt-text="Yeni bir paket Upload." source="Media/Upload-New-Package.png" lightbox="Media/Upload-New-Package.png":::

Oraya vardıktan sonra, yeni bir paketi karşıya yüklemek için aşağıdaki adımları izleyin.

## <a name="enter-details-for-your-package"></a>Paketinizin ayrıntılarını girin

Test ayrıntıları sekmesinde, paketinizin adını, sürümünü ve diğer ayrıntıları istediğiniz şekilde yazın.

**Kullanıma Uygun** ve **İşlevsel testler** bu pano aracılığıyla yapılabilir.

Aşağıdaki adımlar, paket ayrıntılarınızı doldurma hakkında bir kılavuz sağlar:

1. Paketinize `Package name` verilecek adı alanına girin.

    > [!NOTE]
    > Girilen paket adı ve sürüm bileşimi kuruluşunuzda benzersiz olmalıdır. Bu, aşağıda gösterildiği gibi onay işaretiyle doğrulanır.

    - Bir paketin adını yeniden kullanmak isterseniz, sürüm numarası benzersiz olmalıdır (yani, hiçbir zaman bu adı taşıyan bir paketle kullanılmamıştır).

    - Paket adı + sürüm birleşimi benzersizlik denetimini geçmezse *, "Bu paket sürümüyle paket zaten var"* hata iletisini görürsünüz.

    :::image type="content" alt-text="Paket yönergelerini karşıya yükleme resmi." source="Media/Instructions.png":::

2. "Paket sürümü" alanına bir sürüm girin.

    :::image type="content" alt-text="Paket sürümü." source="Media/ApplicationVersion.png":::

3. Bu pakette çalıştırmak istediğiniz test türünü seçin.

    Kullanıma **Açık (OOB)** testi paketinizi *yükleme*, *başlatma*, *kapatma* ve *kaldırma* işlemlerini gerçekleştirir. Yüklemeden sonra başlatma-kapatma yordamı, tek bir kaldırma çalıştırılmadan önce 30 kez yinelenir.

    Bu OOB testi, Windows derlemeleri karşılaştırmak için paketinizde standart telemetri sağlar.

    **İşlevsel test**, paketinizde karşıya yüklenen test betiklerinizi yürütür. Betikler karşıya yükleme sırasında çalıştırılır ve belirli bir betikteki bir hata, izleyen betiklerin yürütülmesini durdurur.

    > [!NOTE]
    > **Tüm** betikler en fazla 80 dakika boyunca çalışır.

4. İşletim sistemi güncelleştirme türünü seçin.

    - 'Güvenlik güncelleştirmeleri', paketinizin Windows yayın öncesi aylık güvenlik güncelleştirmelerinin artımlı değişim sıklığına göre test edilmesine olanak tanır.
    - 'Özellik güncelleştirmeleri', paketinizin Windows Insider Programı'ndan Windows yayın öncesi iki yıllık özellik güncelleştirmeleri derlemelerine karşı test edilmesine olanak tanır.
    <!---
    Change to the correct picture
    -->
    :::image type="content" alt-text="İşletim sistemi güncelleştirme türü." source="Media/OSUpdateType.png":::

5. Güvenlik güncelleştirme testleri için işletim sistemi sürümlerini seçin.

    Çoklu seçim açılan listesinde paketinizin yükleneceği Windows işletim sistemi sürümlerini seçin.

    - Paketinizi yalnızca Windows İstemci işletim sistemlerinde test etmek için menü listesinden uygun Windows İstemci işletim sistemi sürümlerini seçin.
    - Paketinizi yalnızca Windows Server işletim sistemlerinde test etmek için menü listesinden uygun Windows Sunucu işletim sistemi sürümlerini seçin.
    - Paketinizi Windows İstemci ve Windows Sunucusu işletim sistemlerine karşı test etmek için menü listesinden tüm geçerli işletim sistemlerini seçin.

    > [!NOTE]
    > Paketinizi hem Sunucu hem de İstemci işletim sistemiyle test etmek isterseniz lütfen paketin uyumlu olduğundan ve her iki işletim sisteminde de çalıştırılabilir olduğundan emin olun

    :::image type="content" alt-text="İşletim sistemi sürümünü seçme." source="Media/OSVersion.png":::
    <!---
    Change to the correct picture
    -->

6. Özellik güncelleştirme testleri için seçenekleri belirleyin:

    - "Insider Kanalını Seçin" seçeneğinde `Windows Insider Program Channel` paketlerinizin test edilmesi gereken derleme olarak öğesini seçin.

      Şu anda Insider Beta Kanalında sunulan derlemeleri kullanıyoruz.

    - "İçgörüler için işletim sistemi temelini seçin" seçeneğinde, test sonuçlarınızı karşılaştırmak için temel olarak kullanılacak Windows işletim sistemi sürümünü seçin.

    > [!NOTE]
    > Şu anda Sunucu işletim sistemi için özellik güncelleştirme testlerini DESTEKLEMEYİZ
    <!---
    Note to actual note format for markdown
    -->
    <!---
    Change to the correct picture
    -->
    :::image type="content" alt-text="Özellik güncelleştirme testi." source="Media/FeatureUpdate.png":::

7. Tamamlanmış bir Test ayrıntıları sayfası şöyle görünmelidir:

    :::image type="content" alt-text="Test ayrıntılarını görüntüleme." source="Media/TestDetails.png":::

## <a name="next-steps"></a>Sonraki adımlar

Sonraki makalemizde İkili Dosyalarınızı hizmetimize yükleme konusu yer alır.

> [!div class="nextstepaction"]
> [Sonraki adım](binaries.md)

<!---
Add button for next page
-->
