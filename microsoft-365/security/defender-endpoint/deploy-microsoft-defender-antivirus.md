---
title: Dağıtım ve etkinleştirme Microsoft Defender Virüsten Koruma
description: Microsoft Defender Virüsten Koruma, Microsoft Endpoint Configuration Manager, PowerShell cmdlet'Microsoft Intune leri veya WMI ile uç noktalarınızı korumak için Microsoft Endpoint Configuration Manager'yi dağıtın.
keywords: dağıtma, etkinleştirme, devre dışı Microsoft Defender Virüsten Koruma
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
ms.openlocfilehash: 9baa4fe5318bf21d73b3c79e719895fb9c492ea7
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2021
ms.locfileid: "62998045"
---
# <a name="deploy-and-enable-microsoft-defender-antivirus"></a>Dağıtım ve etkinleştirme Microsoft Defender Virüsten Koruma

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:**

- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Kullandığınız yönetim aracına bağlı olarak, güvenlik korumasını özel olarak etkinleştirmeniz veya Microsoft Defender Virüsten Koruma gerekir. 

Microsoft Intune[, Microsoft Endpoint Configuration Manager,](deploy-manage-report-microsoft-defender-antivirus.md#ref2) Group Policy, Active Directory ile korumayı etkinleştirme yönergeleri için, Microsoft Defender Virüsten Koruma, yönetme ve rapor Microsoft Intune'daki tabloya bakın. Microsoft Azure, PowerShell cmdlet'leri ve WINDOWS Yönergesi'ne (WMI) sahip olur.

Bazı senaryolar, Sanal Masaüstü Altyapısı (VDI) ortamları gibi veri korumasını Microsoft Defender Virüsten Koruma başarıyla dağıtma veya yapılandırma konusunda Sanal Masaüstü Altyapısı kılavuz gerektirir.

Bu bölümün kalan makalesinde, VDI veya Uzak Masaüstü Hizmetleri [(RDS) ortamında sanal makinelerde (VMs)](deployment-vdi-microsoft-defender-antivirus.md) Microsoft Defender Virüsten Koruma uç öneriler ve en iyi yöntemler yer almaktadır.

## <a name="related-articles"></a>İlgili makaleler

- [Microsoft Defender Virüsten Koruma'da Windows 10](microsoft-defender-antivirus-in-windows-10.md)
- [Güncelleştirmeleri ve raporu diğer ağlarda dağıtma Microsoft Defender Virüsten Koruma](deploy-manage-report-microsoft-defender-antivirus.md)
- [Sanal masaüstü Microsoft Defender Virüsten Koruma (VDI) ortamında dağıtım kılavuzu](deployment-vdi-microsoft-defender-antivirus.md)