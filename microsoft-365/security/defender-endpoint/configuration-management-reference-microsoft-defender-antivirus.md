---
title: İşletmenizdeki Microsoft Defender Virüsten Koruma yönetme
description: Microsoft Defender AV'yi yönetmek için grup ilkesi, Configuration Manager, PowerShell, WMI, Intune ve komut satırını kullanmayı öğrenin
keywords: grup ilkesi, gpo, yapılandırma yöneticisi, sccm, scep, powershell, wmi, intune, defender, virüsten koruma, kötü amaçlı yazılımdan koruma, güvenlik, koruma
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
ms.openlocfilehash: 760c3b7ca646b02813b5d14086f5d94fc9aec72c
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2022
ms.locfileid: "65418664"
---
# <a name="manage-microsoft-defender-antivirus-in-your-business"></a>İşletmenizdeki Microsoft Defender Virüsten Koruma yönetme

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Şunlar için geçerlidir:**

- [Uç Nokta için Microsoft Defender Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- Microsoft Defender Virüsten Koruma

**Platform**
- Windows

aşağıdaki araçlarla Microsoft Defender Virüsten Koruma yönetebilir ve yapılandırabilirsiniz:

- [Microsoft Intune](/mem/intune/protect/endpoint-security-antivirus-policy) (şimdi Microsoft Endpoint Manager parçası)
- [Microsoft Endpoint Configuration Manager](/mem/configmgr/protect/deploy-use/endpoint-protection-configure) (artık Microsoft Endpoint Manager parçası)
- [Grup İlkesi](./use-group-policy-microsoft-defender-antivirus.md)
- [PowerShell cmdlet'leri](./use-powershell-cmdlets-microsoft-defender-antivirus.md)
- [Windows Yönetim Araçları (WMI)](./use-wmi-microsoft-defender-antivirus.md)
- [Microsoft Kötü Amaçlı Yazılımdan Koruma Komut Satırı Yardımcı Programı](./command-line-arguments-microsoft-defender-antivirus.md) (*mpcmdrun.exe* yardımcı programı olarak adlandırılır)

Aşağıdaki makaleler, Microsoft Defender Virüsten Koruma yönetmek ve yapılandırmak için bu araçları kullanmaya yönelik daha fazla bilgi, bağlantı ve kaynak sağlar.

|Makale|Açıklama|
|:---|:---|
|[Microsoft Intune ve Microsoft Endpoint Configuration Manager ile Microsoft Defender Virüsten Koruma yönetme](use-intune-config-manager-microsoft-defender-antivirus.md)|Microsoft Defender Virüsten Koruma dağıtmak, yönetmek, raporlamak ve yapılandırmak için Intune ve Configuration Manager kullanma hakkında bilgi|
|[grup ilkesi ayarlarıyla Microsoft Defender Virüsten Koruma yönetme](use-group-policy-microsoft-defender-antivirus.md)|ADMX şablonlarında bulunan tüm grup ilkesi ayarlarının listesi|
|[PowerShell cmdlet'leriyle Microsoft Defender Virüsten Koruma yönetme](use-powershell-cmdlets-microsoft-defender-antivirus.md)|Microsoft Defender Virüsten Koruma yönetmek için PowerShell cmdlet'lerini kullanma yönergelerinin yanı sıra tüm cmdlet'ler ve izin verilen parametreler için belgelere bağlantılar|
|[Windows Yönetim Araçları (WMI) ile Microsoft Defender Virüsten Koruma yönetme](use-wmi-microsoft-defender-antivirus.md)|Microsoft Defender Virüsten Koruma yönetmek için WMI kullanma yönergelerinin yanı sıra WMIv2 API'lerinin belgelerine bağlantılar (tüm sınıflar, yöntemler ve özellikler dahil)|
|[MpCmdRun.exe komut satırı aracıyla Microsoft Defender Virüsten Koruma yönetme](command-line-arguments-microsoft-defender-antivirus.md)|Microsoft Defender Virüsten Koruma yönetmek ve kullanmak için ayrılmış komut satırı aracını kullanma yönergeleri|

> [!TIP]
> Diğer platformlar için Virüsten Koruma ile ilgili bilgileri arıyorsanız bkz:
> - [MacOS'ta Uç Nokta için Microsoft Defender tercihlerini ayarlayın](mac-preferences.md)
> - [Mac'te Uç Nokta için Microsoft Defender](microsoft-defender-endpoint-mac.md)
> - [Intune için Microsoft Defender için macOS Virüsten Koruma ilke ayarları](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Linux'ta Uç Nokta için Microsoft Defender tercihlerini ayarlayın](linux-preferences.md)
> - [Linux'ta Uç Nokta için Microsoft Defender](microsoft-defender-endpoint-linux.md)
> - [Android özelliklerinde Uç Nokta için Defender’ı yapılandırın](android-configure.md)
> - [iOS özelliklerinde Uç Nokta için Microsoft Defender’ı yapılandırın](ios-configure-features.md)