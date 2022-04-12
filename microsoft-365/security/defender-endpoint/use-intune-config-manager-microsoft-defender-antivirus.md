---
title: Microsoft Endpoint Manager kullanarak Microsoft Defender Virüsten Koruma yapılandırma
description: Microsoft Defender Virüsten Koruma ve Endpoint Protection yapılandırmak için Microsoft Endpoint Manager ve Microsoft Intune kullanma
keywords: scep, intune, uç nokta koruması, yapılandırma
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 12/16/2021
ms.reviewer: phuijbr, oogunrinde
manager: dansimp
ms.technology: mde
audience: ITPro
ms.topic: how-to
ms.collection: m365-security-compliance
ms.openlocfilehash: b25e57ee28ae0ef3f219a9adda1ff3f860d063db
ms.sourcegitcommit: 4f56b4b034267b28c7dd165e78ecfb4b5390087d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/12/2022
ms.locfileid: "64789304"
---
# <a name="use-microsoft-endpoint-manager-to-configure-and-manage-microsoft-defender-antivirus"></a>Microsoft Defender Virüsten Koruma yapılandırmak ve yönetmek için Microsoft Endpoint Manager kullanma

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Şunlar için geçerlidir:**

- [Pertahanan Microsoft untuk Titik Akhir Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- Microsoft Defender Virüsten Koruma

**Platform**
- Windows

[Microsoft Endpoint Manager kullanarak Microsoft Defender Virüsten Koruma](/mem/endpoint-manager-overview) taramaları yapılandırabilirsiniz. [Microsoft Intune](/mem/intune/fundamentals/what-is-intune) ve [Configuration Manager](/mem/configmgr/core/understand/introduction) artık Endpoint Manager bir parçasıdır.

## <a name="configure-microsoft-defender-antivirus-scans-in-endpoint-manager"></a>Endpoint Manager'da Microsoft Defender Virüsten Koruma taramaları yapılandırma

1. Microsoft Endpoint Manager yönetim merkezine ()[https://endpoint.microsoft.com](https://endpoint.microsoft.com) gidin ve oturum açın.

2. **Endpoint Security'ye** gidin.

3. **Yönet'in** altında **Virüsten Koruma'yı** seçin.

4. Microsoft Defender Virüsten Koruma ilkenizi seçin.

5. **Yönet'in** altında **Özellikler'i** seçin.

6. **Yapılandırma ayarları'nın** yanında **Düzenle'yi** seçin.

   > [!IMPORTANT]
   > AllowOnAccessProtection ve AllowIntrusionPreventionSystem virüsten koruma ayarları resmi olarak kullanım dışı bırakılmıştır ve bu nedenle yapılandırılamaz. 

7. **Tarama** bölümünü genişletin ve tarama ayarlarınızı gözden geçirin veya düzenleyin.

8. **Gözden Geçir ve kaydet'i** seçin.

> [!TIP]
> Yardıma mı ihtiyacınız var? Bkz. [Microsoft Intune'de uç nokta güvenliğini yönetme](/mem/intune/protect/endpoint-security).

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

- [Yönetim ve yapılandırma araçları için başvuru makaleleri](configuration-management-reference-microsoft-defender-antivirus.md)
- [Windows 10'da Microsoft Defender Virüsten Koruma](microsoft-defender-antivirus-in-windows-10.md)
