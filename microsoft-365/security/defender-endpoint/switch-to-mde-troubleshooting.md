---
title: E-Uç Nokta için Microsoft Defender'a geçişte karşılaşılan sorunları giderme
description: Geçiş yapmaya geçiş yapma ile ilgili sorunları gidermeyi Uç Nokta için Microsoft Defender.
keywords: geçiş, windows defender, gelişmiş uç nokta koruması, virüsten koruma, kötü amaçlı yazılımdan koruma, pasif modu, etkin mod, sorun giderme
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: deniseb
author: denisebmsft
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365solution-scenario
- M365-security-compliance
ms.topic: conceptual
ms.custom: migrationguides
ms.date: 03/28/2022
ms.reviewer: jesquive, chventou, jonix, chriggs, owtho
ms.technology: mde
ms.openlocfilehash: 30218ea9b3b5ecbec20fdbc3364546d25c80bcab
ms.sourcegitcommit: bcbcbd4ddc72ad2fed629619d23fac5827d072bf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/29/2022
ms.locfileid: "64507524"
---
# <a name="troubleshooting-issues-when-switching-to-microsoft-defender-for-endpoint"></a>E-Uç Nokta için Microsoft Defender'a geçişte karşılaşılan sorunları giderme

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta için Microsoft Defender Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Uç Nokta için Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

Bu makalede, Microsoft olmayan bir uç nokta koruma çözümünden Kimlik Koruması çözümüne geçişte sorun yaşayan güvenlik yöneticilerine sorun giderme Uç Nokta için Microsoft Defender.

## <a name="microsoft-defender-antivirus-is-getting-uninstalled-on-windows-server"></a>Microsoft Defender Virüsten Koruma Server'da Windows kaldırıyor

Uç nokta için Defender'a geçişte, etkin modda Microsoft dışı virüsten koruma/kötü amaçlı yazılımlardan koruma ile başlarsınız. Kurulum işleminin bir parçası olarak, pasif Microsoft Defender Virüsten Koruma olarak yapılandırabilirsiniz. Bazen, Microsoft dışı virüsten koruma/kötü amaçlı yazılımlardan koruma çözümünüz Microsoft Defender Virüsten Koruma server'da Windows olabilir. Aslında, Microsoft Defender Virüsten Koruma Server'dan kaldırılmış gibi Windows.

Bu sorunu çözmek için aşağıdaki adımları izleyin:

1. [DisableAntiCcaware kayıt defteri anahtarını false olarak ayarlayın](#set-the-disableantispyware-registry-key-to-false).
2. [Dışlama Uç Nokta için Microsoft Defender dışlama listesi ekleme](#add-microsoft-defender-for-endpoint-to-the-exclusion-list).
3. [Pasif modunu Microsoft Defender Virüsten Koruma moduna el ile ayarlayın](#set-microsoft-defender-antivirus-to-passive-mode-manually).

### <a name="set-the-disableantispyware-registry-key-to-false"></a>DisableAntiCcaware kayıt defteri anahtarını false olarak ayarlama

[Geçmişte DisableAntiCcaware](/windows-hardware/customize/desktop/unattend/security-malware-windows-defender-disableantispyware) kayıt defteri anahtarı, mcAfee, Microsoft Defender Virüsten Koruma gibi başka bir virüsten koruma ürününü devre dışı bırakmak ve dağıtmak için kullanılmıştır. **Genelde, Windows** cihazlarınıza ve uç noktalarınıza bu kayıt defteri anahtarınız sahip olmazsınız;  `DisableAntiSpyware` ancak, yapılandırmadınız varsa, değerini false olarak ayarlamak için şu şekilde ayarlanır:

1. Windows Server aygıtınızda Kayıt Defteri Düzenleyicisi'ni açın.

2. `HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Defender`'a gidin.

3. Bu klasörde **DisableAntiWordsware** adlı bir DWORD girdisi bakın.
   - Bu girdiyi görmüyorsanız hazırsanız.
   - **DisableAnti Birware görüyorsanız**, 4. adıma geçin.

4. DisableAntiWordsware DWORD'e sağ tıklayın ve değiştir'i **seçin**.

5. Değeri olarak ayarlayın `0`. (Bu eylem kayıt defteri anahtarının değerini *false olarak ayarlar*.)

> [!TIP]
> Bu kayıt defteri anahtarı hakkında daha fazla bilgi edinmek için [bkz. DisableAntiAntiWare](/windows-hardware/customize/desktop/unattend/security-malware-windows-defender-disableantispyware).

### <a name="add-microsoft-defender-for-endpoint-to-the-exclusion-list"></a>Dışlama Uç Nokta için Microsoft Defender kişi ekleme

Uç Nokta için Defender'ın bazı dışlamaları, Microsoft dışı uç nokta koruma çözümünüz içinde tanımlanmış olmalıdır. Aşağıdaki dışlamaları eklemeye emin olun:

`C:\Program Files\Windows Defender Advanced Threat Protection\MsSense.exe`

`C:\Program Files\Windows Defender Advanced Threat Protection\SenseCncProxy.exe`

`C:\Program Files\Windows Defender Advanced Threat Protection\SenseSampleUploader.exe`

`C:\Program Files\Windows Defender Advanced Threat Protection\SenseIR.exe`

`C:\Program Files\Windows Defender Advanced Threat Protection\SenseCM.exe`

### <a name="set-microsoft-defender-antivirus-to-passive-mode-manually"></a>El ile Microsoft Defender Virüsten Koruma modunu pasif moduna ayarlama

Windows Server 2019, Windows Server, sürüm 1803 veya daha yenisi, Windows Server 2016 veya Windows Server 2012 R2'de, Microsoft Defender Virüsten Koruma pasif moduna el ile ayarlamalısınız. Bu eylem, sunucuda birden çok virüsten koruma ürünü yüklü olması nedeniyle oluşan sorunları önlemeye yardımcı olur. PowerShell, Microsoft Defender Virüsten Koruma defteri anahtarı veya kayıt defteri anahtarı kullanarak grup ilkesi modunu pasif moduna grup ilkesi.

Aşağıdaki kayıt Microsoft Defender Virüsten Koruma edilgen moduna geçer ve bunu pasif moduna:

Yol: `HKLM\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection`

Ad: `ForceDefenderPassiveMode`

Tür: `REG_DWORD`

Değer: `1`

> [!NOTE]
> Pasif modunun Windows Server 2016 ve R2 Windows Server 2012 uç noktalarında çalışması için, bu uç noktaların Yerleşik sunucularda bulunan yönergeler kullanılarak [Windows gerekir](configure-server-endpoints.md#windows-server-2012-r2-and-windows-server-2016).

Daha fazla bilgi için bkz[. Microsoft Defender Virüsten Koruma Server'Windows yükleme](microsoft-defender-antivirus-on-windows-server.md).

## <a name="microsoft-defender-antivirus-seems-to-be-stuck-in-passive-mode"></a>Microsoft Defender Virüsten Koruma pasif modunda takılmış gibi görünüyor

Pasif Microsoft Defender Virüsten Koruma takılıp kalmışsa, aşağıdaki adımları kullanarak bunu el ile etkin moda ayarlayın:

1. Windows Defteri Düzenleyicisi'ni yönetici olarak açın.

2. `Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection` adresine gidin.

3. olarak adlandırılan bir **REG_DWORD** ayarlayın veya tanımlayın `ForceDefenderPassiveMode`ve değerini olarak ayarlayın `0`.

4. Cihazı yeniden başlatın.

> [!IMPORTANT]
> Bu yordamı uygulamanın ardından etkin moda Microsoft Defender Virüsten Koruma konusunda hala sorun yaşıyorsanız, de destek [ile iletişime geçin](../../admin/get-help-support.md).

## <a name="i-am-having-trouble-re-enabling-microsoft-defender-antivirus-on-windows-server-2016"></a>E-postada e-Microsoft Defender Virüsten Koruma yeniden etkinleştirmede sorun Windows Server 2016

Microsoft'a yönelik olmayan bir virüsten koruma/kötü amaçlı yazılımdan koruma çözümü kullanıyorsanız, Windows Server 2016 mevcut çözümünüz devre dışı bırakılamaz Microsoft Defender Virüsten Koruma programdan kaldırılabilir. Kötü Amaçlı Yazılımdan Koruma[ ve Command-Line Yardımcı Programı'nı](command-line-arguments-microsoft-defender-antivirus.md) kullanarak, Microsoft Defender Virüsten Koruma yeniden Windows Server 2016.

1. Sunucu üzerinde yerel bir yönetici olarak Komut İstemi'ne açın.

2. Aşağıdaki konumu çalıştırın: `MpCmdRun.exe -wdenable`

3. Cihazı yeniden başlatın.

## <a name="see-also"></a>Ayrıca bkz.

- [Microsoft Defender Virüsten Koruma güvenlik ürünleriyle uyumluluk sorunları](microsoft-defender-antivirus-compatibility.md)

- [Uç Nokta için Defender'da Windows cihazlar için ekleme araçları ve yöntemleri](configure-endpoints.md) 
