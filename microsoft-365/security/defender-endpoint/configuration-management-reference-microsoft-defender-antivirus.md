---
title: İşletme Microsoft Defender Virüsten Koruma işlerinizi yönetme
description: Microsoft Defender AV'ı yönetmek için Grup İlkesi, Configuration Manager, PowerShell, WMI, Intune ve komut çizgilerini kullanmayı öğrenin
keywords: grup ilkesi, gpo, config manager, sccm, scep, powershell, wmi, intune, defender, virüsten koruma, kötü amaçlı yazılımdan koruma, güvenlik, koruma
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
ms.openlocfilehash: 4c73936bd32381988a03ad527a83847497eab71d
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2021
ms.locfileid: "62997549"
---
# <a name="manage-microsoft-defender-antivirus-in-your-business"></a>İşletme Microsoft Defender Virüsten Koruma işlerinizi yönetme

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:**

- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- Microsoft Defender Virüsten Koruma

Aşağıdaki araçlarla e-Microsoft Defender Virüsten Koruma yönetebilirsiniz ve yapılandırabilirsiniz:

- [Microsoft Intune](/mem/intune/protect/endpoint-security-antivirus-policy) (şimdi işin bir Microsoft Endpoint Manager)
- [Microsoft Endpoint Configuration Manager](/mem/configmgr/protect/deploy-use/endpoint-protection-configure) (şimdi işin bir Microsoft Endpoint Manager)
- [Grup İlkesi](./use-group-policy-microsoft-defender-antivirus.md)
- [PowerShell cmdlet'leri](./use-powershell-cmdlets-microsoft-defender-antivirus.md)
- [Windows Yönetim Aracı (WMI)](./use-wmi-microsoft-defender-antivirus.md)
- [Microsoft Kötü Amaçlı Yazılımdan Koruma Komut Satırı Yardımcı](./command-line-arguments-microsoft-defender-antivirus.md) Programı (yazılım yardımcı *mpcmdrun.exe* da adlandırılır)

Aşağıdaki makalelerde, çalışmalarınızı yönetmek ve yapılandırmak üzere bu araçların kullanımına ilişkin ayrıntılı bilgi, Microsoft Defender Virüsten Koruma.

|Makale|Açıklama|
|:---|:---|
|[Microsoft Defender Virüsten Koruma ve Microsoft Intune ile Microsoft Endpoint Configuration Manager](use-intune-config-manager-microsoft-defender-antivirus.md)|Birden çok uygulamayı dağıtmak, yönetmek, rapor etmek ve yapılandırmak için Intune ve Configuration Manager'ı kullanma Microsoft Defender Virüsten Koruma|
|[Grup Microsoft Defender Virüsten Koruma ayarlarıyla grup ayarlarını yönetme](use-group-policy-microsoft-defender-antivirus.md)|ADMX şablonlarında bulunan tüm Grup İlkesi ayarlarının listesi|
|[PowerShell cmdlet'leriyle Microsoft Defender Virüsten Koruma yönetme](use-powershell-cmdlets-microsoft-defender-antivirus.md)|PowerShell cmdlet'lerini kullanarak tüm cmdlet'leri ve izin verilen parametrelerin belgelerinin Microsoft Defender Virüsten Koruma yönergeler|
|[Yönetim Microsoft Defender Virüsten Koruma (WMI) Windows araçlarıyla iş yönetimi](use-wmi-microsoft-defender-antivirus.md)|WMIv2 API'lerine (tüm sınıflar, yöntemler ve özellikler dahil) Microsoft Defender Virüsten Koruma'i yönetmek için WMI'ya ilişkin yönergeler ve belgelerin bağlantıları|
|[Komut Microsoft Defender Virüsten Koruma aracıyla MpCmdRun.exe'i yönetme](command-line-arguments-microsoft-defender-antivirus.md)|Yönergeleri yönetmek ve kullanmak için ayrılmış komut satırı aracını Microsoft Defender Virüsten Koruma|
