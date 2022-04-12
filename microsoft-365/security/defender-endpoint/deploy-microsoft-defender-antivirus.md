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
ms.openlocfilehash: fe84fa4df958ea42304531defc4810edf332b3a3
ms.sourcegitcommit: 4f56b4b034267b28c7dd165e78ecfb4b5390087d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/12/2022
ms.locfileid: "64790536"
---
# <a name="deploy-and-enable-microsoft-defender-antivirus"></a>Microsoft Defender Virüsten Koruma’yı dağıtın ve etkinleştirin

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Şunlar için geçerlidir:**

- [Pertahanan Microsoft untuk Titik Akhir Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
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
> - [macOS'ta Pertahanan Microsoft untuk Titik Akhir tercihlerini ayarlama](mac-preferences.md)
> - [Mac'te Uç Nokta için Microsoft Defender](microsoft-defender-endpoint-mac.md)
> - [Intune için Microsoft Defender Virüsten Koruma macOS Virüsten Koruma ilkesi ayarları](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Linux'ta Pertahanan Microsoft untuk Titik Akhir tercihlerini ayarlama](linux-preferences.md)
> - [Linux'ta Uç Nokta için Microsoft Defender](microsoft-defender-endpoint-linux.md)
> - [Android'de Uç Nokta için Defender özelliklerini yapılandırma](android-configure.md)
> - [iOS özelliklerinde Pertahanan Microsoft untuk Titik Akhir yapılandırma](ios-configure-features.md)