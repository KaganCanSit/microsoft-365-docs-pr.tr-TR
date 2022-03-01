---
title: Microsoft Defender Virüsten Koruma yapılandırma
description: Intune, Microsoft Defender Virüsten Koruma, Grup İlkesi ve PowerShell Microsoft Endpoint Configuration Manager özellikleri yapılandırabilirsiniz.
keywords: Microsoft Defender Virüsten Koruma, kötü amaçlı yazılımdan koruma, güvenlik, defender, yapılandırma, yapılandırma, Yapılandırma Yöneticisi, Microsoft Endpoint Configuration Manager, SCCM, Intune, MDM, mobil cihaz yönetimi, GP, grup ilkesi, PowerShell
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
ms.date: 10/14/2021
ms.reviewer: ''
manager: dansimp
ms.collection: M365-security-compliance
ms.openlocfilehash: 183fedefbbb56411674ff80a9feedc507cff0530
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2022
ms.locfileid: "63015222"
---
# <a name="configure-microsoft-defender-antivirus-features"></a>Microsoft Defender Virüsten Koruma yapılandırma


**Aşağıdakiler için geçerlidir:**

- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

E-Microsoft Defender Virüsten Koruma aşağıdakiler gibi bazı araçlarla yapılandırabilirsiniz:

- Microsoft Endpoint Manager (e-Microsoft Intune ve Microsoft Endpoint Configuration Manager)
- Grup İlkesi
- PowerShell cmdlet'leri
- Windows Yönetim Aracı (WMI)
- [Kiracı ekleme](/mem/configmgr/tenant-attach/)

Aşağıdaki kapsamlı özellik kategorileri yalnabilir:

- Bulut teslimi koruma. Bkz[. Buluta teslim edilen koruma ve Microsoft Defender Virüsten Koruma](cloud-protection-microsoft-defender-antivirus.md)

- Davranışsal, heuristic ve makine öğrenme tabanlı koruma da dahil olmak üzere, her zaman gerçek zamanlı koruma. Bkz [. Davranışsal, heuristic ve gerçek zamanlı korumayı yapılandırma](configure-protection-features-microsoft-defender-antivirus.md).

- Son kullanıcıların tek tek uç noktalar üzerinde istemciyle etkileşim kurması. Aşağıdaki kaynaklara bakın:
  - [Kullanıcıların kullanıcı arabirimini görmelerini veya Microsoft Defender Virüsten Koruma engelleme](prevent-end-user-interaction-microsoft-defender-antivirus.md)
  - [Kullanıcıların yerel olarak ilke ayarlarını değiştirmesini Microsoft Defender Virüsten Koruma veya izin verme](configure-local-policy-overrides-microsoft-defender-antivirus.md)

> [!TIP]
> Yönetim [ve yapılandırma araçları için başvuru konularını gözden geçirme](configuration-management-reference-microsoft-defender-antivirus.md).
