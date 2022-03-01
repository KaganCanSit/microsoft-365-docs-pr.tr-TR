---
title: Uygulama/Test kuralları
description: Uygulama/test karşıya yüklerken uyulecek kurallar
search.appverid: MET150
author: andreicsibi-msft
ms.author: ancsibi
manager: rshastri
audience: Software-Vendor
ms.topic: how-to
ms.date: 02/04/2022
ms.service: virtual-desktop
ms.localizationpriority: medium
ms.collection: TestBase-M365
ms.custom: ''
ms.reviewer: mapatel
f1.keywords: NOCSH
ms.openlocfilehash: cebf888d7a17d6d589888d529cea1731b666f562
ms.sourcegitcommit: 954c8af658adb270fe843991e048c6a30e86e77c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2022
ms.locfileid: "63016603"
---
# <a name="applicationtest-rules"></a>Uygulama/Test kuralları

Test Temel'de yer alan tüm uygulama ve testlerin aşağıdaki kurallara uyması gerekir:

## <a name="test-base-folders"></a>Temel klasörleri test edin 

Aşağıdaki klasörler Test Temel altyapısı tarafından kullanılır:
* %SYSTEMDRIVE%\USL
* %SYSTEMDRIVE%\EtlExport
* %SYSTEMDRIVE%\Ffmpeg
* %SYSTEMDRIVE%\Monitoring
* %SYSTEMDRIVE%\powershell-yaml
* %SYSTEMDRIVE%\ProcMon
* %SYSTEMDRIVE%\PSTools
* %SYSTEMDRIVE%\TokenProviderTool
* %SYSTEMDRIVE%\USLPowershellModules
* %SYSTEMDRIVE%\UtcUtil
* %SYSTEMDRIVE%\WPT
* %SYSTEMDRIVE%\WULogs

> [!IMPORTANT]
> **Aşağıdakilerin önüne geç:**
> * Bu klasörlerden herhangi bir işlem yürütülmesi engel engelleme. Uygulamanız kötü amaçlı yazılımdan koruma yazılımı ise, uygulama yüklemenizi bu klasörlerdeki tüm işlemlerin durdurulmalarına izin verecek şekilde yapılandırın.
> * Bu klasörlerin herhangi birini değiştirme.

## <a name="test-base-registry-keys"></a>Test Base kayıt defteri anahtarları

Uygulamalar/testler aşağıdakilerle ilgili kayıt defteri anahtarlarını silemez veya değiştirmez:
* Windows telemetri düzeyi
* TLS 1.2'yi kaldırma
