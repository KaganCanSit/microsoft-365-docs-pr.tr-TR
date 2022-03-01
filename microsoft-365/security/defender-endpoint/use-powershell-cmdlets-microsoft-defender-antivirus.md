---
title: PowerShell cmdlet'lerini kullanarak bu cmdlet'leri yapılandırma ve Microsoft Defender Virüsten Koruma
description: Windows 10 ve Windows 11'de, taramaları çalıştırmak, Güvenlik zekası güncelleştirme ve ayarları değiştirmek için PowerShell cmdlet'lerini Microsoft Defender Virüsten Koruma.
keywords: scan, komut satırı, mpcmdrun, defender
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 10/18/2020
ms.reviewer: ''
manager: dansimp
ms.technology: mde
audience: ITPro
ms.topic: how-to
ms.collection: m365-security-compliance
ms.openlocfilehash: 075a475ef3135769e90362f441077b1638192e99
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2021
ms.locfileid: "62997484"
---
# <a name="use-powershell-cmdlets-to-configure-and-manage-microsoft-defender-antivirus"></a>PowerShell cmdlet'lerini kullanarak e-postalarınızı Microsoft Defender Virüsten Koruma

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)

PowerShell'i kullanarak çalışma sayfalarında çeşitli işlevler Windows Defender. PowerShell, komut istemine veya komut satırına benzer şekilde, özellikle sistem yönetimi için tasarlanmış görev tabanlı bir komut satırı kabuğu ve betik dilidir. Bu konuda daha fazla bilgi için [MSDN'de PowerShell hub'ını ziyaret edin](/previous-versions/msdn10/mt173057(v=msdn.10)).

Cmdlet'lerin, bunların işlevlerinin ve kullanılabilen parametrelerin listesi için [Defender Virüsten Koruma cmdlet'leri başlığına](/powershell/module/defender) bakın.

PowerShell cmdlet'leri en çok, yazılımı yapılandırmak için grafik kullanıcı arabirimine (GUI) güvenmeen Windows Server ortamlarında yararlıdır.

> [!NOTE]
> PowerShell cmdlet'leri, Microsoft Endpoint Configuration Manager, Grup İlkesi Yönetim Konsolu veya [Microsoft Defender Virüsten Koruma](/configmgr) Grup İlkesi [ADMX](https://www.microsoft.com/download/101445) şablonları gibi tam ağ ilkesi yönetim altyapısının yerine kullanılma kullanılmalıdır. [](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11))

PowerShell ile yapılan değişiklikler, değişikliklerin dağıtılacağı veya dağıtılacağı uç noktadaki yerel ayarları etkiler. Başka bir ifadeyle, Grup İlkesi, Grup Microsoft Endpoint Configuration Manager veya Microsoft Intune ilke dağıtımları PowerShell'de yapılan değişikliklerin üzerine yazabilirim.

Hangi [ayarların yerel olarak geçersiz kılınabilir ve yerel ilke geçersiz kılınabilir.](configure-local-policy-overrides-microsoft-defender-antivirus.md)

PowerShell genellikle klasörün altına yüklenir `%SystemRoot%\system32\WindowsPowerShell`.

## <a name="use-microsoft-defender-antivirus-powershell-cmdlets"></a>Microsoft Defender Virüsten Koruma PowerShell cmdlet'lerini kullanma

1. Arama Windows **powershell yazın**.
2. Arabirimi **Windows PowerShell** için sonuçlardan Diğer Seçenekler'i seçin.
3. PowerShell komutunu ve varsa parametreleri girin.

> [!NOTE]
> PowerShell'i yönetici modunda açmanız gerekir. Çalışma alanı içinde öğeye sağ tıklayın Başlat menüsü Yönetici olarak **çalıştır'a tıklayın ve** **izin** isteminde Evet'e tıklayın.

Cmdlet'lerden herhangi biri ile ilgili çevrimiçi yardımı açmak için şunları yazın:

```PowerShell
Get-Help <cmdlet> -Online
```

Yerel olarak önbelleğe `-online` alınmış yardım almak için parametreyi atlar.

## <a name="related-topics"></a>İlgili konular

- [Yönetim ve yapılandırma araçları için başvuru konuları](configuration-management-reference-microsoft-defender-antivirus.md)
- [Microsoft Defender Virüsten Koruma'da Windows 10](microsoft-defender-antivirus-in-windows-10.md)
- [Microsoft Defender Virüsten Koruma Cmdlet'leri](/powershell/module/defender)
