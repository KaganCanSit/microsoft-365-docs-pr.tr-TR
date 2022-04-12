---
title: PowerShell kullanarak virüsten koruma taramaları zamanlama
description: PowerShell kullanarak virüsten koruma taramaları zamanlama
keywords: hızlı tarama, tam tarama, virüsten koruma, zamanlama, PowerShell
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 10/18/2021
ms.reviewer: pauhijbr, ksarens
manager: dansimp
ms.technology: mde
ms.topic: how-to
ms.collection: M365-security-compliance
ms.openlocfilehash: 8961428acee5d166b0cdad4982aa5f9ed48020af
ms.sourcegitcommit: 4f56b4b034267b28c7dd165e78ecfb4b5390087d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/12/2022
ms.locfileid: "64788842"
---
# <a name="schedule-antivirus-scans-using-powershell"></a>PowerShell kullanarak virüsten koruma taramaları zamanlama

**Şunlar için geçerlidir:**
- [Pertahanan Microsoft untuk Titik Akhir Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- Microsoft Defender Virüsten Koruma

**Platform**
- Windows

Bu makalede, PowerShell cmdlet'lerini kullanarak zamanlanmış taramaların nasıl yapılandırıldığı açıklanır. Taramaları zamanlama ve tarama türleri hakkında daha fazla bilgi edinmek için bkz[. Zamanlanmış hızlı veya tam Microsoft Defender Virüsten Koruma taramalarını yapılandırma](schedule-antivirus-scans.md). 

## <a name="use-powershell-cmdlets-to-schedule-scans"></a>Taramaları zamanlamak için PowerShell cmdlet'lerini kullanma

Aşağıdaki cmdlet'leri kullanın:

```PowerShell
Set-MpPreference -ScanParameters
Set-MpPreference -ScanScheduleDay
Set-MpPreference -ScanScheduleTime
Set-MpPreference -RandomizeScheduleTaskTimes

```

Daha fazla bilgi için bkz. [Microsoft Defender Virüsten Koruma yapılandırmak ve çalıştırmak için PowerShell cmdlet'lerini kullanma ve Microsoft Defender Virüsten Koruma](use-powershell-cmdlets-microsoft-defender-antivirus.md) ile PowerShell'i kullanma hakkında daha fazla bilgi için [Defender Virüsten Koruma cmdlet'leri](/powershell/module/defender/).

## <a name="powershell-cmdlets-for-scheduling-scans-when-an-endpoint-is-not-in-use"></a>Bir uç nokta kullanımda olmadığında taramaları zamanlamak için PowerShell cmdlet'leri

Aşağıdaki cmdlet'leri kullanın:

```PowerShell
Set-MpPreference -ScanOnlyIfIdleEnabled
```

Daha fazla bilgi için bkz. Microsoft Defender Virüsten Koruma ve [Defender Virüsten Koruma cmdlet'lerini](/powershell/module/defender/) [yapılandırmak ve çalıştırmak için PowerShell](use-powershell-cmdlets-microsoft-defender-antivirus.md) cmdlet'lerini kullanma.

> [!NOTE]
> Uç noktaların kullanımda olmadığı zamanlar için taramalar zamanladığınızda, taramalar CPU azaltma yapılandırmasına uygun değildir ve taramayı mümkün olan en hızlı şekilde tamamlamak için kullanılabilir kaynaklardan tam olarak yararlanır.

## <a name="powershell-cmdlets-for-scheduling-scans-to-complete-remediation"></a>Düzeltmeyi tamamlamak için taramaları zamanlamak için PowerShell cmdlet'leri

Aşağıdaki cmdlet'leri kullanın:

```PowerShell
Set-MpPreference -RemediationScheduleDay
Set-MpPreference -RemediationScheduleTime
```

[PowerShell'i Microsoft Defender Virüsten Koruma](use-powershell-cmdlets-microsoft-defender-antivirus.md) ile kullanma hakkında daha fazla bilgi için bkz. Microsoft Defender Virüsten Koruma yapılandırmak ve çalıştırmak için PowerShell [cmdlet'lerini kullanma ve Defender Virüsten Koruma cmdlet'leri](/powershell/module/defender/).

## <a name="powershell-cmdlets-for-scheduling-daily-scans"></a>Günlük taramaları zamanlamak için PowerShell cmdlet'leri

Aşağıdaki cmdlet'leri kullanın:

```PowerShell
Set-MpPreference -ScanScheduleQuickScanTime
```

PowerShell'i Microsoft Defender Virüsten Koruma ile kullanma hakkında daha fazla bilgi için bkz. Microsoft Defender Virüsten Koruma ve [Defender Virüsten Koruma cmdlet'lerini](/powershell/module/defender/) [yapılandırmak ve çalıştırmak için PowerShell](use-powershell-cmdlets-microsoft-defender-antivirus.md) cmdlet'lerini kullanma.

> [!TIP]
> Diğer platformlar için Virüsten Koruma ile ilgili bilgileri arıyorsanız bkz:
> - [macOS'ta Pertahanan Microsoft untuk Titik Akhir tercihlerini ayarlama](mac-preferences.md)
> - [Mac'te Uç Nokta için Microsoft Defender](microsoft-defender-endpoint-mac.md)
> - [Intune için Microsoft Defender Virüsten Koruma macOS Virüsten Koruma ilkesi ayarları](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Linux'ta Pertahanan Microsoft untuk Titik Akhir tercihlerini ayarlama](linux-preferences.md)
> - [Linux'ta Uç Nokta için Microsoft Defender](microsoft-defender-endpoint-linux.md)
> - [Android'de Uç Nokta için Defender özelliklerini yapılandırma](android-configure.md)
> - [iOS özelliklerinde Pertahanan Microsoft untuk Titik Akhir yapılandırma](ios-configure-features.md)