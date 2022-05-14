---
title: Microsoft Defender Virüsten Koruma’yı dağıtın ve etkinleştirin
description: Microsoft Intune, Microsoft Endpoint Configuration Manager, grup ilkesi, PowerShell cmdlet'leri veya WMI ile uç noktalarınızın korunması için Microsoft Defender Virüsten Koruma dağıtın.
keywords: dağıtma, etkinleştirme, Microsoft Defender Virüsten Koruma
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
ms.topic: conceptual
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.collection: m365-security-compliance
ms.openlocfilehash: f3ab5a838945121a9c46a5448dbaec7bfa06b4c5
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2022
ms.locfileid: "65419076"
---
# <a name="deploy-and-enable-microsoft-defender-antivirus"></a>Microsoft Defender Virüsten Koruma’yı dağıtın ve etkinleştirin

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Şunlar için geçerlidir:**

- [Uç Nokta için Microsoft Defender Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Microsoft Defender Virüsten Koruma

**Platform**
- Windows

Kullandığınız yönetim aracına bağlı olarak, Microsoft Defender Virüsten Koruma korumasını özel olarak etkinleştirmeniz veya yapılandırmanız gerekebilir. 

Microsoft Intune, Microsoft Endpoint Configuration Manager ile korumayı etkinleştirme yönergeleri için [Microsoft Defender Virüsten Koruma dağıtma, yönetme ve raporlama başlığı altında](deploy-manage-report-microsoft-defender-antivirus.md#ref2) yer alan tabloya bakın. grup ilkesi, Active Directory, Microsoft Azure, PowerShell cmdlet'leri ve Windows Yönetim Yönergesi (WMI).

Bazı senaryolar, Sanal Masaüstü Altyapısı (VDI) ortamları gibi Microsoft Defender Virüsten Koruma korumayı başarıyla dağıtma veya yapılandırma konusunda daha fazla kılavuz gerektirir.

Bu bölümdeki diğer makale, [VDI veya Uzak Masaüstü Hizmetleri (RDS) ortamındaki sanal makinelerde (VM) Microsoft Defender Virüsten Koruma ayarlamak](deployment-vdi-microsoft-defender-antivirus.md) için uçtan uca öneriler ve en iyi yöntemleri sağlar.

## <a name="related-articles"></a>İlgili makaleler

- [Windows 10'da Microsoft Defender Virüsten Koruma](microsoft-defender-antivirus-in-windows-10.md)
- [Microsoft Defender Virüsten Koruma güncelleştirmeleri dağıtma, yönetme ve raporlama](deploy-manage-report-microsoft-defender-antivirus.md)
- [Sanal Masaüstü Altyapısı (VDI) ortamında Microsoft Defender Virüsten Koruma için dağıtım klavuzu](deployment-vdi-microsoft-defender-antivirus.md)

> [!TIP]
> Diğer platformlar için Virüsten Koruma ile ilgili bilgileri arıyorsanız bkz:
> - [MacOS'ta Uç Nokta için Microsoft Defender tercihlerini ayarlayın](mac-preferences.md)
> - [Mac'te Uç Nokta için Microsoft Defender](microsoft-defender-endpoint-mac.md)
> - [Intune için Microsoft Defender için macOS Virüsten Koruma ilke ayarları](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Linux'ta Uç Nokta için Microsoft Defender tercihlerini ayarlayın](linux-preferences.md)
> - [Linux'ta Uç Nokta için Microsoft Defender](microsoft-defender-endpoint-linux.md)
> - [Android özelliklerinde Uç Nokta için Defender’ı yapılandırın](android-configure.md)
> - [iOS özelliklerinde Uç Nokta için Microsoft Defender’ı yapılandırın](ios-configure-features.md)