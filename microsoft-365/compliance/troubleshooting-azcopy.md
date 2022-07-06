---
title: eBulma'da AzCopy sorunlarını giderme (Premium)
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
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
description: eBulma (Premium) içinde hata düzeltme için Office 365 olmayan verileri yüklerken Azure AzCopy hatalarını giderme.
ms.custom:
- seo-marvel-mar2020
- seo-marvel-apr2020
ms.openlocfilehash: 3a74dd5f2a341e9a99cbfc82cfb12900bae42491
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66641152"
---
# <a name="troubleshoot-azcopy-in-ediscovery-premium"></a>eBulma'da AzCopy sorunlarını giderme (Premium)

Microsoft Purview eKeşif(Premium) içinde hata düzeltme için Microsoft 365 dışı verileri veya belgeleri yüklerken, kullanıcı arabirimi karşıya yüklemek istediğiniz dosyaların depolandığı konumu ve dosyaların yüklendiği Azure depolama konumunu içeren parametreleri içeren bir Azure AzCopy komutu sağlar. Belgelerinizi karşıya yüklemek için bu komutu kopyalayıp yerel bilgisayarınızda bir Komut İstemi'nde çalıştırırsınız.  Aşağıdaki ekran görüntüsünde AzCopy komutunun bir örneği gösterilmektedir:

![Microsoft olmayan 365 dosyalarını karşıya yükleyin.](../media/46ba68f6-af11-4e70-bb91-5fc7973516e3.png)

Genellikle sağlanan komut çalıştırdığınızda çalışır. Ancak, görüntülenen komutun başarıyla çalışmadığı durumlar olabilir. İşte birkaç olası neden.

## <a name="the-supported-version-of-azcopy-isnt-installed-on-the-local-computer"></a>AzCopy'nin desteklenen sürümü yerel bilgisayarda yüklü değil

Şu anda, eKeşif(Premium) içinde Microsoft 365 dışı verileri yüklemek için AzCopy v8.1 kullanmanız gerekir. Önceki ekran görüntüsünde gösterilen **Dosyaları karşıya yükle** sayfasında görüntülenen AzCopy komutu, AzCopy v8.1 kullanmıyorsanız bir hata döndürür. Bu sürümü yüklemek için bkz. [Windows'da AzCopy v8.1 ile veri aktarma](/previous-versions/azure/storage/storage-use-azcopy).

## <a name="azcopy-isnt-installed-on-the-local-computer-or-its-not-installed-in-the-default-location"></a>AzCopy yerel bilgisayarda yüklü değil veya varsayılan konumda yüklü değil

AzCopy yüklü değilse veya varsayılan yükleme konumundan (yani) farklı bir konuma yüklüyse `%ProgramFiles(x86)%`, AzCopy komutunu çalıştırdığınızda aşağıdaki hatayı alabilirsiniz:

> Sistem belirtilen yolu bulamıyor.

Yerel bilgisayarda AzCopy yüklü değilse, [Yükleme bilgilerini Windows'da AzCopy v8.1 ile veri aktarma bölümünde](/previous-versions/azure/storage/storage-use-azcopy) bulabilirsiniz. Varsayılan konuma yüklediğinizden emin olun.

AzCopy yüklüyse ancak varsayılan konumdan farklı bir konuma yüklenmişse, komutu kopyalayabilir, bir metin dosyasına yapıştırabilir ve ardından AzCopy'nin yüklü olduğu konumun yolunu değiştirebilirsiniz. Örneğin, Azcopy içinde `%ProgramFiles%`bulunuyorsa, komutun `%ProgramFiles(x86)%\Microsoft SDKs\Azure\AzCopy.exe` `%ProgramFiles%\Microsoft SDKs\Azure\AzCopy`ilk bölümünü olarak değiştirebilirsiniz. Bu değişikliği yaptıktan sonra, metin dosyasından kopyalayın ve komut istemini çalıştırın.

> [!TIP]
> AzCopy, varsayılan yükleme konumundan başka bir konuma yüklenmişse, kaldırmayı ve ardından varsayılan konuma yeniden yüklemeyi göz önünde bulundurun. Bu, gelecekte bu sorunun önlenmesine yardımcı olacaktır.