---
title: Tarama sonuçlarını Microsoft Defender Virüsten Koruma gözden geçirme
description: Microsoft Endpoint Configuration Manager, Microsoft Intune veya Windows Güvenliği uygulamasını kullanarak taramaların sonuçlarını gözden geçirme
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
ms.openlocfilehash: 79c435618f03a8bdbd69638c66b728597cd63cab
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2021
ms.locfileid: "62998222"
---
# <a name="review-microsoft-defender-antivirus-scan-results"></a>Tarama Microsoft Defender Virüsten Koruma gözden geçirme

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Bir Microsoft Defender Virüsten Koruma isteğe bağlı veya zamanlanmış tarama olabilir, bu tamamlandıktan [](run-scan-microsoft-defender-antivirus.md) sonra sonuçlar kaydedilir ve [](scheduled-catch-up-scans-microsoft-defender-antivirus.md)sonuçları görüntüabilirsiniz. 


## <a name="use-configuration-manager-to-review-scan-results"></a>Tarama sonuçlarını gözden geçirmek için Yapılandırma Yöneticisi'ni kullanma

Bu [durumun nasıl iz Endpoint Protection bakın](/configmgr/protect/deploy-use/monitor-endpoint-protection).

## <a name="use-powershell-cmdlets-to-review-scan-results"></a>Tarama sonuçlarını gözden geçirmek için PowerShell cmdlet'lerini kullanma

Aşağıdaki cmdlet, uç noktayla ilgili her algılamayı geri dönecektir. Aynı tehdidin birden çok algılaması varsa, her algılama, her algılamanın zamanı temel alınarak ayrı listelenir:

```PowerShell
Get-MpThreatDetection
```

:::image type="content" source="../../media/wdav-get-mpthreatdetection.png" alt-text="PowerShell cmdlet'leri ve çıktılarının ekran görüntüsü.":::

Çıkışı yalnızca belirli `-ThreatID` bir tehdit için algılamaları gösterecek şekilde sınırlandırma belirtsiniz.

Tehdit algılamalarını listeleyen ancak aynı tehdit algılamalarını tek bir öğe olarak birleştirmek için aşağıdaki cmdlet'i kullanabilirsiniz:

```PowerShell
Get-MpThreat
```

:::image type="content" source="../../media/wdav-get-mpthreat.png" alt-text="PowerShell kodu.":::

[PowerShell cmdlet'lerini kullanarak PowerShell cmdlet'lerini](use-powershell-cmdlets-microsoft-defender-antivirus.md) yapılandırma ve çalıştırma hakkında daha fazla bilgi Microsoft Defender Virüsten Koruma [Defender Virüsten Koruma cmdlet'lerini](/powershell/module/defender/) Microsoft Defender Virüsten Koruma.

## <a name="use-windows-management-instruction-wmi-to-review-scan-results"></a>Tarama Windows gözden geçirmek için YÖNETIM Yönergesini (WMI) kullanma

Sınıf [**için ve** sınıf MSFT_MpThreat **Get MSFT_MpThreatDetection**](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal) kullanın.


## <a name="related-articles"></a>İlgili makaleler

- [Bu taramaları ve düzeltmeleri sonucunda Microsoft Defender Virüsten Koruma, başlatma ve gözden geçirme](customize-run-review-remediate-scans-microsoft-defender-antivirus.md)
- [Microsoft Defender Virüsten Koruma'da Windows 10](microsoft-defender-antivirus-in-windows-10.md)
