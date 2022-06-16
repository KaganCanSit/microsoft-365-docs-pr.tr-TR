---
title: Microsoft Defender Virüsten Koruma özelliklerini yapılandırın
description: Intune, Microsoft Endpoint Configuration Manager, grup ilkesi ve PowerShell ile Microsoft Defender Virüsten Koruma özellikleri yapılandırabilirsiniz.
keywords: Microsoft Defender Virüsten Koruma, kötü amaçlı yazılımdan koruma, güvenlik, defender, yapılandırma, yapılandırma, Config Manager, Microsoft Endpoint Configuration Manager, SCCM, Intune, MDM, mobil cihaz yönetimi, GP, grup ilkesi, PowerShell
ms.prod: m365-security
ms.technology: mde
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.topic: article
ms.custom: nextgen
ms.reviewer: ''
manager: dansimp
ms.collection: M365-security-compliance
ms.openlocfilehash: 8271f6d0fcc58ce5a7e1ce08f6034a8a90afab48
ms.sourcegitcommit: 18bc521a88b7b521bccb0e69d02deac764218087
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/16/2022
ms.locfileid: "66115465"
---
# <a name="configure-microsoft-defender-antivirus-features"></a>Microsoft Defender Virüsten Koruma özelliklerini yapılandırın


**Şunlar için geçerlidir:**

- [Uç Nokta için Microsoft Defender Planı 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- Microsoft Defender Virüsten Koruma

**Platform**
- Windows

Microsoft Defender Virüsten Koruma çeşitli araçlarla yapılandırabilirsiniz, örneğin:

- Microsoft Endpoint Manager (Microsoft Intune ve Microsoft Endpoint Configuration Manager içerir)
- Grup İlkesi
- PowerShell cmdlet'leri
- Windows Yönetim Araçları (WMI)
- [Kiracı ekleme](/mem/configmgr/tenant-attach/)

Aşağıdaki geniş özellik kategorileri yapılandırılabilir:

- Bulut tabanlı koruma. Bkz[. Bulut tabanlı koruma ve Microsoft Defender Virüsten Koruma](cloud-protection-microsoft-defender-antivirus.md)

- Davranışsal, buluşsal ve makine öğrenmesi tabanlı koruma da dahil olmak üzere her zaman açık gerçek zamanlı koruma. Bkz [. Davranışsal, buluşsal ve gerçek zamanlı korumayı yapılandırma](configure-protection-features-microsoft-defender-antivirus.md).

- Son kullanıcıların tek tek uç noktalarda istemciyle etkileşim kurma şekli. Aşağıdaki kaynaklara bakın:
  - [Kullanıcıların Microsoft Defender Virüsten Koruma kullanıcı arabirimini görmesini veya bu arabirimle etkileşim kurmasını engelleme](prevent-end-user-interaction-microsoft-defender-antivirus.md)
  - [Kullanıcıların Microsoft Defender Virüsten Koruma ilke ayarlarını yerel olarak değiştirmesini engelleme veya izin verme](configure-local-policy-overrides-microsoft-defender-antivirus.md)

> [!TIP]
> [Yönetim ve yapılandırma araçları için Başvuru konularını](configuration-management-reference-microsoft-defender-antivirus.md) gözden geçirin.
> Diğer platformlar için Antivirüs ile ilgili bilgi arıyorsanız bkz:
> - [MacOS'ta Uç Nokta için Microsoft Defender tercihlerini ayarlayın](mac-preferences.md)
> - [Mac'te Uç Nokta için Microsoft Defender](microsoft-defender-endpoint-mac.md)
> - [Intune için Microsoft Defender için macOS Virüsten Koruma ilke ayarları](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Linux'ta Uç Nokta için Microsoft Defender tercihlerini ayarlayın](linux-preferences.md)
> - [Linux'ta Uç Nokta için Microsoft Defender](microsoft-defender-endpoint-linux.md)
> - [Android özelliklerinde Uç Nokta için Defender’ı yapılandırın](android-configure.md)
> - [iOS özelliklerinde Uç Nokta için Microsoft Defender’ı yapılandırın](ios-configure-features.md)
