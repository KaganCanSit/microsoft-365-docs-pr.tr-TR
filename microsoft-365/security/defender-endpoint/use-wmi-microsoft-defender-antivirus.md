---
title: WMI ile Microsoft Defender Virüsten Koruma yapılandırma
description: Pertahanan Microsoft untuk Titik Akhir'da ayarları almak, değiştirmek ve güncelleştirmek için WMI betiklerini kullanarak Microsoft Defender Virüsten Koruma yapılandırmayı ve yönetmeyi öğrenin.
keywords: wmi, betikler, windows yönetim araçları, yapılandırma
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
ms.openlocfilehash: a525deb526f61f8500f42cc918380fdfa9c52861
ms.sourcegitcommit: 4f56b4b034267b28c7dd165e78ecfb4b5390087d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/12/2022
ms.locfileid: "64787654"
---
# <a name="use-windows-management-instrumentation-wmi-to-configure-and-manage-microsoft-defender-antivirus"></a>Microsoft Defender Virüsten Koruma yapılandırmak ve yönetmek için Windows Yönetim Araçları'nın (WMI) kullanılması

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Şunlar için geçerlidir:**
- [Pertahanan Microsoft untuk Titik Akhir Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- Microsoft Defender Virüsten Koruma

**Platform**
- Windows

Windows Yönetim Araçları (WMI), ayarları almanıza, değiştirmenize ve güncelleştirmenize olanak tanıyan bir betik oluşturma arabirimidir.

WMI hakkında daha fazla bilgi için [Bkz. Microsoft Developer Network System Administration library](/windows/win32/wmisdk/wmi-start-page).

Microsoft Defender Virüsten Koruma, grup ilkesi ve diğer yönetim araçlarıyla aynı işlevlerin çoğunu gerçekleştirmek için kullanılabilecek bir dizi belirli WMI sınıfına sahiptir. Sınıfların çoğu [Bulut için Defender PowerShell cmdlet'lerine](use-powershell-cmdlets-microsoft-defender-antivirus.md) benzer.

[MSDN Windows Defender WMIv2 Sağlayıcısı başvuru kitaplığı](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal), Microsoft Defender Virüsten Koruma için kullanılabilir WMI sınıflarını listeler ve örnek betikler içerir.

WMI ile yapılan değişiklikler, değişikliklerin dağıtıldığı veya yapıldığı uç noktadaki yerel ayarları etkiler. Bu, ilkenin grup ilkesi, Microsoft Endpoint Configuration Manager veya Microsoft Intune dağıtımlarının WMI ile yapılan değişikliklerin üzerine yazabileceği anlamına gelir. 

[Yerel ilke geçersiz kılmaları ile hangi ayarların yerel olarak geçersiz kılınabileceğini yapılandırabilirsiniz](configure-local-policy-overrides-microsoft-defender-antivirus.md).

> [!TIP]
> Diğer platformlar için Virüsten Koruma ile ilgili bilgileri arıyorsanız bkz:
> - [macOS'ta Pertahanan Microsoft untuk Titik Akhir tercihlerini ayarlama](mac-preferences.md)
> - [Mac'te Uç Nokta için Microsoft Defender](microsoft-defender-endpoint-mac.md)
> - [Intune için Microsoft Defender Virüsten Koruma macOS Virüsten Koruma ilkesi ayarları](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Linux'ta Pertahanan Microsoft untuk Titik Akhir tercihlerini ayarlama](linux-preferences.md)
> - [Linux'ta Uç Nokta için Microsoft Defender](microsoft-defender-endpoint-linux.md)
> - [Android'de Uç Nokta için Defender özelliklerini yapılandırma](android-configure.md)
> - [iOS özelliklerinde Pertahanan Microsoft untuk Titik Akhir yapılandırma](ios-configure-features.md)

## <a name="related-topics"></a>İlgili konular

- [Yönetim ve yapılandırma araçları için başvuru konuları](configuration-management-reference-microsoft-defender-antivirus.md)
- [Windows 10'da Microsoft Defender Virüsten Koruma](microsoft-defender-antivirus-in-windows-10.md)
