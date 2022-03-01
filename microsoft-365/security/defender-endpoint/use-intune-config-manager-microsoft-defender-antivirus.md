---
title: E-Microsoft Defender Virüsten Koruma kullanarak Microsoft Endpoint Manager
description: Microsoft Endpoint Manager ve Microsoft Intune'i yapılandırmak için Microsoft Defender Virüsten Koruma ve Endpoint Protection
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
ms.openlocfilehash: 1eb126481cc9872c42906e0311d1c771da44c693
ms.sourcegitcommit: 282f3a58b8e11615b3e53328e6b89a6ac52008e9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/17/2021
ms.locfileid: "63019056"
---
# <a name="use-microsoft-endpoint-manager-to-configure-and-manage-microsoft-defender-antivirus"></a>Microsoft Endpoint Manager'i yapılandırmak ve yönetmek için Microsoft Defender Virüsten Koruma

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:**

- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)

[Microsoft Endpoint Manager'i](/mem/endpoint-manager-overview) kullanarak taramaları Microsoft Defender Virüsten Koruma kullanabilirsiniz. [Microsoft Intune](/mem/intune/fundamentals/what-is-intune) [Yapılandırma Yöneticisi artık](/mem/configmgr/core/understand/introduction) yapılandırmanın bir Endpoint Manager.

## <a name="configure-microsoft-defender-antivirus-scans-in-endpoint-manager"></a>Microsoft Defender Virüsten Koruma'da taramaları Endpoint Manager

1. Yönetim merkezine Microsoft Endpoint Manager ()[https://endpoint.microsoft.com](https://endpoint.microsoft.com) ve oturum açma.

2. Uç Nokta **Güvenliği'ne gidin**.

3. **Yönet'in altında** Virüsten **Koruma'ya seçin**.

4. İlke Microsoft Defender Virüsten Koruma seçin.

5. **Yönet'in** altında **Özellikler'i seçin**.

6. Yapılandırma **ayarları'nın yanında** Düzenle'yi **seçin**.

   > [!IMPORTANT]
   > AllowOnAccessProtection ve AllowIntrusionPreventionSystem virüsten koruma ayarları resmi olarak kullanımdan kullanım dışı bırakılamaz ve bu şekilde yapılandırılamaz. 

7. Tarama bölümünü **genişletin** ve tarama ayarlarınızı gözden geçirin veya düzenleyin.

8. Gözden Geçir **+ kaydet'i seçin**.

> [!TIP]
> Yardıma mı ihtiyacınız var? Bkz[. Güvenlik nedeniyle uç nokta Microsoft Intune](/mem/intune/protect/endpoint-security).

## <a name="related-articles"></a>İlgili makaleler

- [Yönetim ve yapılandırma araçlarına başvuru makaleleri](configuration-management-reference-microsoft-defender-antivirus.md)
- [Microsoft Defender Virüsten Koruma'da Windows 10](microsoft-defender-antivirus-in-windows-10.md)
