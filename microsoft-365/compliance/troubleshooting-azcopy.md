---
title: E-postada AzCopy sorunlarını Advanced eDiscovery
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: troubleshooting
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: ''
description: Microsoft Azure AzCopy'de hatalı düzeltme için Office 365 olmayan verileri yüklerken hata Advanced eDiscovery.
ms.custom:
- seo-marvel-mar2020
- seo-marvel-apr2020
ms.openlocfilehash: 45f82482f92e740383eca774671f1abd55535675
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62984685"
---
# <a name="troubleshoot-azcopy-in-advanced-ediscovery"></a>E-postada AzCopy sorunlarını Advanced eDiscovery

Advanced eDiscovery'te Microsoft 365 olmayan veriler veya belgeler hata düzeltmesi için yüklenirken, kullanıcı arabirimi karşıya yüklemek istediğiniz dosyaların depolandığı konumu ve dosyaların karşıya yük hatta Azure depolama konumunu içeren parametreler içeren bir Azure AzCopy komutu sağlar. Belgelerinizi karşıya yüklemek için, bu komutu kopyalayıp yerel bilgisayarınızda komut isteminde çalıştırın.  Aşağıdaki ekran görüntüsünde AzCopy komutunun bir örneği yer aldı:

![Upload olmayan Microsoft 365.](../media/46ba68f6-af11-4e70-bb91-5fc7973516e3.png)

Çoğunlukla, sağlanan komut siz çalıştıracak şekilde çalışır. Bununla birlikte, görüntülenen komutun başarıyla çalıştırılamayacak durumlar olabilir. Bunun birkaç olası nedeni vardır.

## <a name="the-supported-version-of-azcopy-isnt-installed-on-the-local-computer"></a>AzCopy'nin desteklenen sürümü yerel bilgisayarda yüklü değil

Şu anda, azCopy v8.1'i Microsoft 365 olmayan verileri Advanced eDiscovery. AzCopy v8.1 Upload ekran görüntüsünde  gösterilen AzCopy komutu, Upload dosyalar sayfasında gösterilen bir hata döndürür. Bu sürümü yüklemek için bkz. [Dosya üzerinde AzCopy v8.1 ile veri Windows](/previous-versions/azure/storage/storage-use-azcopy).

## <a name="azcopy-isnt-installed-on-the-local-computer-or-its-not-installed-in-the-default-location"></a>AzCopy yerel bilgisayara yüklü değil veya varsayılan konumda yüklü değil

AzCopy yüklü değilse veya varsayılan yükleme konumu ( `%ProgramFiles(x86)%`yani) dışında bir konuma yüklendiyse, AzCopy komutunu çalıştırmanız sırasında aşağıdaki hatayı alabilirsiniz:

> Sistem belirtilen yolu bulamıyor.

AzCopy yerel bilgisayarda yüklü değilse yükleme bilgilerini Çalışma [tarihindeki AzCopy v8.1 ile aktarma bağlantılarında Windows](/previous-versions/azure/storage/storage-use-azcopy). Varsayılan konuma yüklemeniz gerekir.

AzCopy yüklüyse, ancak varsayılan konumdan farklı bir konuma yüklenmişse, komutu kopyalayıp bir metin dosyasına yapıştırabilirsiniz ve ardından yolu AzCopy'nin yüklü olduğu konuma değiştirebilirsiniz. Örneğin, Azcopy 'da yer alıyorsa `%ProgramFiles%`, komutun ilk kısmını 'dan değiştirebilirsiniz `%ProgramFiles(x86)%\Microsoft SDKs\Azure\AzCopy.exe` `%ProgramFiles%\Microsoft SDKs\Azure\AzCopy`. Bu değişikliği yaptıktan sonra, metin dosyasından kopyalayın ve komut istemiyle çalıştırın.

> [!TIP]
> AzCopy başka bir konuma ve ardından varsayılan yükleme konumuna yüklüyse, bunu kaldırıp varsayılan konuma yeniden yüklemeyi göz önünde bulundurabilirsiniz. Bu, gelecekte bu sorunu önlemeye yardımcı olur.