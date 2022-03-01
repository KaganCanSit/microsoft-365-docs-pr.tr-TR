---
title: WMI ile Microsoft Defender Virüsten Koruma yapılandırma
description: Uç Nokta için Microsoft Defender'da AYARLARı Microsoft Defender Virüsten Koruma, değiştirmek ve güncelleştirmek için WMI betiklerini kullanarak bu dosyaları yapılandırmayı ve yönetmeyi öğrenin.
keywords: wmi, betikler, windows yönetimi araçları, yapılandırma
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 10/18/2018
ms.reviewer: ''
manager: dansimp
ms.technology: mde
audience: ITPro
ms.topic: how-to
ms.collection: m365-security-compliance
ms.openlocfilehash: c8057a971576d5511440ac009acd6eab55b302e9
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2021
ms.locfileid: "62997556"
---
# <a name="use-windows-management-instrumentation-wmi-to-configure-and-manage-microsoft-defender-antivirus"></a>Araç Windows (WMI) kullanarak araçları yapılandırma ve yönetme Microsoft Defender Virüsten Koruma

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)

Windows Yönetimi Aracı (WMI) ayarlarını alamanız, değiştirmenize ve güncelleştirmenize olanak sağlayan bir komut dosyası arabirimidir.

[Microsoft Developer Network System Administration kitaplığında WMI hakkında daha fazla bilgi edinebilirsiniz](/windows/win32/wmisdk/wmi-start-page).

Microsoft Defender Virüsten Koruma Grup İlkesi ve diğer yönetim araçlarıyla aynı işlevlerin çoğunu gerçekleştirmek için  kullanılabilir olan bir dizi belirli WMI sınıfı vardır. Sınıfların çoğu, [Cloud PowerShell cmdlet'leri için Defender'a benzer](use-powershell-cmdlets-microsoft-defender-antivirus.md).

[MSDN Windows Defender WMIv2 Sağlayıcısı başvuru](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal) kitaplığı, Microsoft Defender Virüsten Koruma için kullanılabilir WMI sınıflarını listeler ve örnek betikler içerir.

WMI ile yapılan değişiklikler, değişikliklerin dağıtılacağı veya dağıtılacağı uç nokta üzerinde yerel ayarları etkiler. Başka bir ifadeyle, Grup İlkesi, Grup İlkesi veya Microsoft Endpoint Configuration Manager ilke Microsoft Intune WMI ile yapılan değişikliklerin üzerine yazabilirsiniz. 

Hangi [ayarların yerel olarak geçersiz kılınabilir ve yerel ilke geçersiz kılınabilir.](configure-local-policy-overrides-microsoft-defender-antivirus.md)

## <a name="related-topics"></a>İlgili konular

- [Yönetim ve yapılandırma araçları için başvuru konuları](configuration-management-reference-microsoft-defender-antivirus.md)
- [Microsoft Defender Virüsten Koruma'da Windows 10](microsoft-defender-antivirus-in-windows-10.md)
