---
title: Uç Nokta için Microsoft Defender geçiş yaparken karşılaşılan sorunları giderme
description: Uç Nokta için Microsoft Defender geçiş yaptığınızda sorunları gidermeyi öğrenin.
keywords: geçiş, windows defender, gelişmiş uç nokta koruması, virüsten koruma, kötü amaçlı yazılımdan koruma, pasif mod, etkin mod, sorun giderme
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
ms.date: 05/20/2022
ms.reviewer: jesquive, chventou, jonix, chriggs, owtho
ms.technology: mde
ms.openlocfilehash: 9a1a95c927c4f659510c587d2bbc81ad4b9c1264
ms.sourcegitcommit: 349f0f54b0397cdd7d8fbb9ef07f1b6654a32d6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/20/2022
ms.locfileid: "65621648"
---
# <a name="troubleshooting-issues-when-switching-to-microsoft-defender-for-endpoint"></a>Uç Nokta için Microsoft Defender geçiş yaparken karşılaşılan sorunları giderme

**Şunlar için geçerlidir:**
- [Uç Nokta için Microsoft Defender Planı 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

Bu makalede, Microsoft dışı uç nokta koruma çözümünden Uç Nokta için Microsoft Defender geçiş yaparken sorun yaşayan güvenlik yöneticileri için sorun giderme bilgileri sağlanır.

## <a name="microsoft-defender-antivirus-is-getting-uninstalled-on-windows-server"></a>Microsoft Defender Virüsten Koruma Windows Sunucusu'nda kaldırılıyor

Uç Nokta için Defender'a geçiş yaptığınızda, etkin modda Microsoft dışı virüsten koruma/kötü amaçlı yazılımdan koruma ile başlarsınız. Kurulum işleminin bir parçası olarak Microsoft Defender Virüsten Koruma pasif modda yapılandırabilirsiniz. Bazen Microsoft dışı virüsten koruma/kötü amaçlı yazılımdan koruma çözümünüz Microsoft Defender Virüsten Koruma Windows Sunucusunda çalışmasını engelleyebilir. Aslında, Microsoft Defender Virüsten Koruma Windows Sunucusundan kaldırılmış gibi görünebilir.

Bu sorunu çözmek için aşağıdaki adımları uygulayın:

1. [Dışlama listesine Uç Nokta için Microsoft Defender ekleyin](#add-microsoft-defender-for-endpoint-to-the-exclusion-list).
2. [Microsoft Defender Virüsten Koruma pasif moda el ile ayarlayın](#set-microsoft-defender-antivirus-to-passive-mode-manually).

### <a name="add-microsoft-defender-for-endpoint-to-the-exclusion-list"></a>Dışlama listesine Uç Nokta için Microsoft Defender ekleme

Uç Nokta için Defender'a yönelik belirli dışlamalar, mevcut Microsoft dışı uç nokta koruma çözümünüzde tanımlanmalıdır. Aşağıdaki dışlamaları eklediğinizden emin olun:

`C:\Program Files\Windows Defender Advanced Threat Protection\MsSense.exe`

`C:\Program Files\Windows Defender Advanced Threat Protection\SenseCncProxy.exe`

`C:\Program Files\Windows Defender Advanced Threat Protection\SenseSampleUploader.exe`

`C:\Program Files\Windows Defender Advanced Threat Protection\SenseIR.exe`

`C:\Program Files\Windows Defender Advanced Threat Protection\SenseCM.exe`

### <a name="set-microsoft-defender-antivirus-to-passive-mode-manually"></a>Microsoft Defender Virüsten Koruma pasif moda el ile ayarlama

Windows Server 2019, Windows Server, sürüm 1803 veya üzeri, Windows Server 2016 veya Windows Server 2012 R2'de, Microsoft Defender Virüsten Koruma pasif moda el ile ayarlamanız gerekir. Bu eylem, bir sunucuda birden çok virüsten koruma ürününün yüklü olmasından kaynaklanan sorunları önlemeye yardımcı olur. PowerShell, grup ilkesi veya kayıt defteri anahtarı kullanarak Microsoft Defender Virüsten Koruma pasif moda ayarlayabilirsiniz.

Aşağıdaki kayıt defteri anahtarını ayarlayarak Microsoft Defender Virüsten Koruma pasif moda ayarlayabilirsiniz:

Yolu: `HKLM\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection`

Ad: `ForceDefenderPassiveMode`

Türü: `REG_DWORD`

Değer: `1`

> [!NOTE]
> Pasif modun Windows Server 2016 ve Windows Server 2012 R2 çalıştıran uç noktalarda çalışması için, bu uç noktaların [Windows sunucularında](configure-server-endpoints.md#windows-server-2012-r2-and-windows-server-2016) ekleme yönergeleri kullanılarak eklenmelidir.

Daha fazla bilgi için bkz. [Windows'da Microsoft Defender Virüsten Koruma](microsoft-defender-antivirus-windows.md).

## <a name="microsoft-defender-antivirus-seems-to-be-stuck-in-passive-mode"></a>Microsoft Defender Virüsten Koruma pasif modda takılmış gibi görünüyor

Microsoft Defender Virüsten Koruma pasif modda takılırsa, şu adımları izleyerek bunu el ile etkin moda ayarlayın:

1. Windows cihazınızda Kayıt Defteri Düzenleyicisi'ni yönetici olarak açın.

2. `Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection` adresine gidin.

3. adlı `ForceDefenderPassiveMode`**bir REG_DWORD** girdisi ayarlayın veya tanımlayın ve değerini olarak `0`ayarlayın.

4. Cihazı yeniden başlatın.

> [!IMPORTANT]
> Bu yordamı takip ettikten sonra Microsoft Defender Virüsten Koruma etkin moda ayarlama konusunda sorun yaşamaya devam ediyorsanız [desteğe başvurun](../../admin/get-help-support.md).

## <a name="i-am-having-trouble-re-enabling-microsoft-defender-antivirus-on-windows-server-2016"></a>Windows Server 2016'da Microsoft Defender Virüsten Koruma yeniden etkinleştirme konusunda sorun yaşıyorum

Windows Server 2016'da Microsoft dışı bir virüsten koruma/kötü amaçlı yazılımdan koruma çözümü kullanıyorsanız, mevcut çözümünüzün devre dışı bırakılması veya kaldırılması için Microsoft Defender Virüsten Koruma gerekmiş olabilir. Windows Server 2016 Microsoft Defender Virüsten Koruma yeniden etkinleştirmek için[ Kötü Amaçlı Yazılımdan Koruma Command-Line Yardımcı Programı'nı](command-line-arguments-microsoft-defender-antivirus.md) kullanabilirsiniz.

1. Sunucuda yerel yönetici olarak Komut İstemi'ni açın.

2. Aşağıdaki komutu çalıştırın: `MpCmdRun.exe -wdenable`

3. Cihazı yeniden başlatın.

## <a name="see-also"></a>Ayrıca bkz.

- [Microsoft Defender Virüsten Koruma diğer güvenlik ürünleriyle uyumluluk](microsoft-defender-antivirus-compatibility.md)

- [Uç Nokta için Defender'da Windows cihazlar için ekleme araçları ve yöntemleri](configure-endpoints.md) 
