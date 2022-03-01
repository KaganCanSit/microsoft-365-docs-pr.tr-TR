---
title: Yönetim Aracı'Windows kullanarak virüsten koruma taramaları zamanlama
description: WMI kullanarak virüsten koruma taramaları zamanlama
keywords: hızlı tarama, tam tarama, WMI, zamanlama, virüsten koruma
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
ms.openlocfilehash: be22e59f6d2be30ead354099f2cc168868959752
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2021
ms.locfileid: "63008088"
---
# <a name="schedule-antivirus-scans-using-windows-management-instrumentation-wmi"></a>Yönetim Aracı'Windows (WMI) kullanarak virüsten koruma taramaları zamanlama

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)

Bu makalede, WMI kullanarak zamanlanmış taramaları yapılandırma işlemi açıklanmıştır. Taramaları zamanlama ve tarama türleri hakkında daha fazla bilgi edinmek için bkz. Zamanlanmış hızlı veya [tam tarama Microsoft Defender Virüsten Koruma yapılandırma](schedule-antivirus-scans.md). 

## <a name="use-windows-management-instruction-wmi-to-schedule-scans"></a>Taramaları Windows için YÖNETIM Yönergesi(WMI) kullanma

Aşağıdaki [**özellikler** için sınıf **MSFT_MpPreference**](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) Set yöntemini kullanın:

```WMI
ScanParameters
ScanScheduleDay
ScanScheduleTime
RandomizeScheduleTaskTimes
```

Daha fazla bilgi ve izin verilen parametreler için [WMIv2 API'Windows Defender bakın](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal)

## <a name="wmi-for-scheduling-scans-when-an-endpoint-is-not-in-use"></a>Uç nokta kullanım içinde değilken taramaları zamanlaması için WMI

Aşağıdaki [özellikler için sınıf MSFT_MpPreference Set](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) yöntemini kullanın:

```WMI
ScanOnlyIfIdleEnabled
```

API'ler ve izin verilen parametreler hakkında daha fazla bilgi için bkz[. WINDOWS DEFENDER WMIv2 API'leri](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal).

> [!NOTE]
> Uç noktaların kullanım içinde olmadığınız zamanlarda taramalar zamanlarken, taramalar CPU azaltma yapılandırmasına uygun değildir ve taramayı mümkün olan en hızlı şekilde tamamlamak için mevcut kaynaklardan tam olarak yararlanacak.


## <a name="wmi-for-scheduling-scans-to-complete-remediation"></a>Düzeltmeyi tamamlamak için taramaları zamanlayarak WMI

Aşağıdaki [**özellikler** için sınıf **MSFT_MpPreference**](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) Set yöntemini kullanın:

```WMI
RemediationScheduleDay
RemediationScheduleTime
```

Daha fazla bilgi ve izin verilen parametreler için [WMIv2 API'Windows Defender bakın](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal).

## <a name="wmi-for-scheduling-daily-scans"></a>GÜNLÜK taramaları zamanlayarak WMI

Aşağıdaki [**özellikler** için sınıf **MSFT_MpPreference**](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) Set yöntemini kullanın:

```WMI
ScanScheduleQuickScanTime
```

Daha fazla bilgi ve izin verilen parametreler için [WMIv2 API'Windows Defender bakın](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal).

