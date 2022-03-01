---
title: Test görevlerinizi ayarlama
description: Test görevlerinizi ayarlama
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
ms.openlocfilehash: 8255cadfa77dec222527c79caf4d8737abfe2b8c
ms.sourcegitcommit: 954c8af658adb270fe843991e048c6a30e86e77c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2022
ms.locfileid: "63016523"
---
# <a name="step-4-the-tasks-tab"></a>4. Adım: Görevler sekmesi

Görevler sekmesinde, test betiklerinizi ikililer sekmesi altında karşıya yüklediğiniz zip klasöründe bulunan yolları sağlamanız beklenir.

  - **SınamaDan Önce Betikleri:** Betiklerinizi yükleme, başlatma, kapatma ve kaldırma ile ilgili göreli yolları yazın. Ayrıca, yükleme betiği için ek ayarları da seçebilirsiniz.
  - **İşlevsel Sınama Betikleri:** Karşıya yüklenen her işlevsel test betiğine göreli yolu yazın. Bu düğme kullanılarak başka işlevsel test betikleri eklenebilir ```Add Script``` . En az bir (1) betik gerekir ve en çok sekiz (8) işlevsel test betiği  eklersiniz. 
  
    Betikler listelendik sırayla çalıştırın. Belirli bir betikte bir hata, izleyen betiklerin yürütülmesini durdurur.
    Ayrıca sağlanan her betik için ek ayarlar seçme seçeneğiniz de vardır.

## <a name="set-script-path"></a>Komut dosyası yolunu ayarlama

![Test görevinin resmi.](Media/testtask.png)

Klasör yapısında göreli yol sağlama örneği aşağıda verilmiştir:

_**Zip_file_uploaded**_
~~~
├── file1.exe

├── ScriptX.ps1

├── folder1

│   ├── file3.exe

│   ├── script.ps1
~~~
  - **ScriptX.ps1** bunu olurdu. _ScriptX.ps1_ yol olarak seçin.
  - **Script.ps1** göreli yol _olarak klasör1/script.ps1_ olabilir.


## <a name="next-steps"></a>Sonraki adımlar

Sonraki makaledeki Test Seçenekleri sekmesinin ayrıntılarını görüntüleme 
> [!div class="nextstepaction"]
> [Sonraki adım](testoptions.md)
