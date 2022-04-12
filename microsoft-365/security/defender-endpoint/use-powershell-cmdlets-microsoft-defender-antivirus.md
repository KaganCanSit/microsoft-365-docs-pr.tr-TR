---
title: Microsoft Defender Virüsten Koruma yapılandırmak ve çalıştırmak için PowerShell cmdlet'lerini kullanma
description: Windows 10 ve Windows 11'da tarama çalıştırmak, Güvenlik zekasını güncelleştirmek ve Microsoft Defender Virüsten Koruma ayarlarını değiştirmek için PowerShell cmdlet'lerini kullanabilirsiniz.
keywords: tarama, komut satırı, mpcmdrun, defender
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
ms.openlocfilehash: 1cd19ff6010badd7386e937dfddb4420e76335b0
ms.sourcegitcommit: 4f56b4b034267b28c7dd165e78ecfb4b5390087d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/12/2022
ms.locfileid: "64790338"
---
# <a name="use-powershell-cmdlets-to-configure-and-manage-microsoft-defender-antivirus"></a>Microsoft Defender Virüsten Koruma yapılandırmak ve yönetmek için PowerShell cmdlet'lerini kullanma

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Şunlar için geçerlidir:**
- [Pertahanan Microsoft untuk Titik Akhir Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- Microsoft Defender Virüsten Koruma

**Platform**
- Windows

PowerShell'i kullanarak Windows Defender'da çeşitli işlevler gerçekleştirebilirsiniz. Komut istemine veya komut satırına benzer şekilde PowerShell, özellikle sistem yönetimi için tasarlanmış görev tabanlı bir komut satırı kabuğu ve betik dilidir. Msdn'deki [PowerShell hub'ında](/previous-versions/msdn10/mt173057(v=msdn.10)) bu konuda daha fazla bilgi edinebilirsiniz.

Cmdlet'lerin, işlevlerinin ve kullanılabilir parametrelerin listesi için [Defender Virüsten Koruma cmdlet'leri](/powershell/module/defender) konusuna bakın.

PowerShell cmdlet'leri, yazılımı yapılandırmak için grafik kullanıcı arabirimine (GUI) güvenmeyen Windows Sunucu ortamlarında en kullanışlıdır.

> [!NOTE]
> PowerShell cmdlet'leri [Microsoft Endpoint Configuration Manager, grup ilkesi](/configmgr) [Yönetim Konsolu](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)) veya Microsoft Defender Virüsten Koruma gibi tam ağ ilkesi yönetim altyapısının yerine kullanılmamalıdır [ ADMX şablonlarını grup ilkesi](https://www.microsoft.com/download/101445).

PowerShell ile yapılan değişiklikler, değişikliklerin dağıtıldığı veya yapıldığı uç noktadaki yerel ayarları etkiler. Bu, grup ilkesi, Microsoft Endpoint Configuration Manager veya Microsoft Intune ile ilke dağıtımlarının PowerShell ile yapılan değişikliklerin üzerine yazabileceği anlamına gelir.

[Yerel ilke geçersiz kılmaları ile hangi ayarların yerel olarak geçersiz kılınabileceğini yapılandırabilirsiniz](configure-local-policy-overrides-microsoft-defender-antivirus.md).

PowerShell genellikle klasörünün `%SystemRoot%\system32\WindowsPowerShell`altına yüklenir.

## <a name="use-microsoft-defender-antivirus-powershell-cmdlets"></a>Microsoft Defender Virüsten Koruma PowerShell cmdlet'lerini kullanma

1. Windows arama çubuğuna **powershell** yazın.
2. Arabirimi açmak için sonuçlardan **Windows PowerShell** seçin.
3. PowerShell komutunu ve tüm parametreleri girin.

> [!NOTE]
> PowerShell'i yönetici modunda açmanız gerekebilir. Başlat menüsü öğeye sağ tıklayın, **Yönetici olarak çalıştır'a** tıklayın ve izin isteminde **Evet'e** tıklayın.

Cmdlet'lerden herhangi biri için çevrimiçi yardım açmak için aşağıdakileri yazın:

```PowerShell
Get-Help <cmdlet> -Online
```

Yerel olarak önbelleğe `-online` alınmış yardım almak için parametresini atlar.

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
- [Microsoft Defender Virüsten Koruma Cmdlet'leri](/powershell/module/defender)
