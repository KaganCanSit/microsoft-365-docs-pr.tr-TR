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
ms.openlocfilehash: e1cbdd156306d7cc2ee41fd85baadb1fa51cf1ac
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2021
ms.locfileid: "63008103"
---
# <a name="schedule-antivirus-scans-using-powershell"></a>PowerShell kullanarak virüsten koruma taramaları zamanlama

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)

Bu makalede, PowerShell cmdlet'lerini kullanarak zamanlanmış taramaları nasıl yapılandırabilirsiniz? Taramaları zamanlama ve tarama türleri hakkında daha fazla bilgi edinmek için bkz. Zamanlanmış hızlı veya [tam tarama Microsoft Defender Virüsten Koruma yapılandırma](schedule-antivirus-scans.md). 

## <a name="use-powershell-cmdlets-to-schedule-scans"></a>Taramaları zamanlaması için PowerShell cmdlet'lerini kullanma

Aşağıdaki cmdlet'leri kullanın:

```PowerShell
Set-MpPreference -ScanParameters
Set-MpPreference -ScanScheduleDay
Set-MpPreference -ScanScheduleTime
Set-MpPreference -RandomizeScheduleTaskTimes

```

Daha fazla bilgi için [PowerShell cmdlet'lerini](use-powershell-cmdlets-microsoft-defender-antivirus.md) kullanarak Microsoft Defender Virüsten Koruma'ı yapılandırma ve çalıştırma ve PowerShell'i Microsoft Defender Virüsten Koruma.[](/powershell/module/defender/)

## <a name="powershell-cmdlets-for-scheduling-scans-when-an-endpoint-is-not-in-use"></a>Uç nokta kullanımdaki bir yer değilken taramaları zamanlamayı planlamak için PowerShell cmdlet'leri

Aşağıdaki cmdlet'leri kullanın:

```PowerShell
Set-MpPreference -ScanOnlyIfIdleEnabled
```

Daha fazla bilgi için bkz[. PowerShell cmdlet'lerini kullanarak PowerShell cmdlet'lerini](use-powershell-cmdlets-microsoft-defender-antivirus.md) yapılandırma ve Microsoft Defender Virüsten Koruma [Defender Virüsten Koruma cmdlet'lerini yapılandırma](/powershell/module/defender/).

> [!NOTE]
> Uç noktaların kullanım içinde olmadığınız zamanlarda taramalar zamanlarken, taramalar CPU azaltma yapılandırmasına uygun değildir ve taramayı mümkün olan en hızlı şekilde tamamlamak için mevcut kaynaklardan tam olarak yararlanacak.

## <a name="powershell-cmdlets-for-scheduling-scans-to-complete-remediation"></a>Düzeltmeyi tamamlamak için taramaları zamanlamayı planlayan PowerShell cmdlet'leri

Aşağıdaki cmdlet'leri kullanın:

```PowerShell
Set-MpPreference -RemediationScheduleDay
Set-MpPreference -RemediationScheduleTime
```

[PowerShell cmdlet'lerini kullanarak PowerShell cmdlet'lerini](use-powershell-cmdlets-microsoft-defender-antivirus.md) yapılandırma ve çalıştırma hakkında daha fazla bilgi Microsoft Defender Virüsten Koruma [Defender Virüsten Koruma cmdlet'lerini](/powershell/module/defender/) Microsoft Defender Virüsten Koruma.

## <a name="powershell-cmdlets-for-scheduling-daily-scans"></a>Günlük taramaları zamanlaması için PowerShell cmdlet'leri

Aşağıdaki cmdlet'leri kullanın:

```PowerShell
Set-MpPreference -ScanScheduleQuickScanTime
```

Microsoft Defender Virüsten Koruma ile PowerShell'in nasıl kullanıldığı hakkında daha fazla bilgi için bkz. Microsoft Defender Virüsten Koruma [ve Defender Virüsten Koruma cmdlet'lerini](/powershell/module/defender/) yapılandırmak ve çalıştırmak için [PowerShell cmdlet'lerini](use-powershell-cmdlets-microsoft-defender-antivirus.md) kullanma.
