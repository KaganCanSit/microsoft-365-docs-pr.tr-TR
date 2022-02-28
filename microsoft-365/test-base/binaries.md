---
title: Upload Ikili Dosyalar
description: M365 için Test Temel'i kullanmaya başlama
search.appverid: MET150
author: mansipatel-usl
ms.author: mapatel
manager: rshastri
audience: Software-Vendor
ms.topic: how-to
ms.date: 07/06/2021
ms.service: virtual-desktop
ms.localizationpriority: medium
ms.collection: TestBase-M365
ms.custom: ''
ms.reviewer: mapatel
f1.keywords: NOCSH
ms.openlocfilehash: 200da9ca73bc666f3f11fc3fda95493d2c0954fb
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62985342"
---
# <a name="step-3-upload-your-binaries-dependencies-and-scripts"></a>3. Adım: Upload dosyalarınız, bağımlılıklarınızı ve betiklerinizi yönetme

Bu sekmede, test paketinizi çalıştırmak için kullanılan ikili dosyaları, bağımlılıkları ve betikleri içeren tek bir zip paketi karşıya yüklersiniz.

> [!NOTE]
> Zip paketinin boyutu en az 10 MB ve en çok 2 GB arasında olmalıdır.

## <a name="upload-package-zip-file"></a>Upload paketi zip dosyası

:::image type="content" alt-text="Upload ikili işlerinizi geri dönüşümle depolar." source="Media/AddBinaries.png":::

  - Karşıya yüklenen bağımlılıklar test çerçeveleri, betik altyapıları veya uygulamanızı veya test durumlarınızı çalıştırmak için erişilen verileri içerebilir. Örneğin, tarayıcı tabanlı testleri çalıştırmanıza yardımcı olmak için Selenium'u ve bir web sürücüsü yükleyicisini karşıya yükleyebilirsiniz.
  - Komut dosyası etkinliklerinizin modüler olmasını sağlamak en iyisidir. 
    - Betik `Install` yalnızca yükleme işlemlerini gerçekleştirir.
    - Betik `Launch` yalnızca uygulamayı başlatıyor.
    - Betik `Close` yalnızca uygulamayı kapatır.
    - İsteğe bağlı `Uninstall` betik yalnızca uygulamayı kaldırır.

**Portal şu anda yalnızca PowerShell betiklerini destekler.**


## <a name="next-steps"></a>Sonraki adımlar 

4. Adım: Test Görevlerinizi ayarlama makalesine gitmek **için sonraki makaleye geçin**.
> [!div class="nextstepaction"]
> [Geri Git](uploadApplication.md)
> [!div class="nextstepaction"]
> [Sonraki adım](testtask.md)

