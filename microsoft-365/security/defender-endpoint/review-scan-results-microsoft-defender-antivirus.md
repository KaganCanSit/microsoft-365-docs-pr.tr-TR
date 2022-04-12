---
title: Microsoft Defender Virüsten Koruma taramalarının sonuçlarını gözden geçirin
description: Microsoft Endpoint Configuration Manager, Microsoft Intune veya Windows Güvenliği uygulamasını kullanarak taramaların sonuçlarını gözden geçirin
keywords: tarama sonuçları, düzeltme, tam tarama, hızlı tarama
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 10/18/2021
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.topic: article
ms.collection: M365-security-compliance
ms.openlocfilehash: 9ffe10560bb36c8fc1311061510f35396934e3b8
ms.sourcegitcommit: 4f56b4b034267b28c7dd165e78ecfb4b5390087d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/12/2022
ms.locfileid: "64790646"
---
# <a name="review-microsoft-defender-antivirus-scan-results"></a>Tarama sonuçlarını Microsoft Defender Virüsten Koruma gözden geçirme

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Şunlar için geçerlidir:**
- [Pertahanan Microsoft untuk Titik Akhir Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Microsoft Defender Virüsten Koruma

**Platform**
- Windows

bir Microsoft Defender Virüsten Koruma taraması tamamlandıktan sonra, [ister isteğe bağlı](run-scan-microsoft-defender-antivirus.md) ister [zamanlanmış bir tarama](scheduled-catch-up-scans-microsoft-defender-antivirus.md) olsun, sonuçlar kaydedilir ve sonuçları görüntüleyebilirsiniz. 


## <a name="use-configuration-manager-to-review-scan-results"></a>Tarama sonuçlarını gözden geçirmek için Configuration Manager kullanma

Bkz[. Endpoint Protection durumunu izleme](/configmgr/protect/deploy-use/monitor-endpoint-protection).

## <a name="use-powershell-cmdlets-to-review-scan-results"></a>Tarama sonuçlarını gözden geçirmek için PowerShell cmdlet'lerini kullanma

Aşağıdaki cmdlet uç noktadaki her algılamayı döndürür. Aynı tehdidin birden çok algılaması varsa her algılama, her algılamanın zamanına göre ayrı olarak listelenir:

```PowerShell
Get-MpThreatDetection
```

:::image type="content" source="../../media/wdav-get-mpthreatdetection.png" alt-text="PowerShell cmdlet'leri ve çıkışları" lightbox="../../media/wdav-get-mpthreatdetection.png":::

Çıkışı yalnızca belirli bir tehdit için algılamaları gösterecek şekilde sınırlamayı belirtebilirsiniz `-ThreatID` .

Tehdit algılamalarını listelemek, ancak aynı tehdidin algılamalarını tek bir öğede birleştirmek istiyorsanız, aşağıdaki cmdlet'i kullanabilirsiniz:

```PowerShell
Get-MpThreat
```

:::image type="content" source="../../media/wdav-get-mpthreat.png" alt-text="PowerShell kodu" lightbox="../../media/wdav-get-mpthreat.png":::

[PowerShell'i Microsoft Defender Virüsten Koruma](use-powershell-cmdlets-microsoft-defender-antivirus.md) ile kullanma hakkında daha fazla bilgi için bkz. Microsoft Defender Virüsten Koruma yapılandırmak ve çalıştırmak için PowerShell [cmdlet'lerini kullanma ve Defender Virüsten Koruma cmdlet'leri](/powershell/module/defender/).

## <a name="use-windows-management-instruction-wmi-to-review-scan-results"></a>Tarama sonuçlarını gözden geçirmek için Windows Yönetim Yönergesi'ni (WMI) kullanma

[**MSFT_MpThreat** ve **MSFT_MpThreatDetection** sınıflarının **Get** yöntemini](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal) kullanın.

> [!TIP]
> Diğer platformlar için Virüsten Koruma ile ilgili bilgileri arıyorsanız bkz:
> - [macOS'ta Pertahanan Microsoft untuk Titik Akhir tercihlerini ayarlama](mac-preferences.md)
> - [Mac'te Uç Nokta için Microsoft Defender](microsoft-defender-endpoint-mac.md)
> - [Intune için Microsoft Defender Virüsten Koruma macOS Virüsten Koruma ilkesi ayarları](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Linux'ta Pertahanan Microsoft untuk Titik Akhir tercihlerini ayarlama](linux-preferences.md)
> - [Linux'ta Uç Nokta için Microsoft Defender](microsoft-defender-endpoint-linux.md)
> - [Android'de Uç Nokta için Defender özelliklerini yapılandırma](android-configure.md)
> - [iOS özelliklerinde Pertahanan Microsoft untuk Titik Akhir yapılandırma](ios-configure-features.md)


## <a name="related-articles"></a>İlgili makaleler

- [Microsoft Defender Virüsten Koruma taramalarının ve düzeltmelerinin sonuçlarını özelleştirme, başlatma ve gözden geçirme](customize-run-review-remediate-scans-microsoft-defender-antivirus.md)
- [Windows 10'da Microsoft Defender Virüsten Koruma](microsoft-defender-antivirus-in-windows-10.md)
