---
title: Microsoft Defender Virüsten Koruma Server'da Windows'i seçin
description: Windows Server 2016, Windows Server 2019 ve Microsoft Defender Virüsten Koruma Server 2022'de Windows ve yapılandırmayı öğrenin.
keywords: windows Defender, sunucu, scep, sistem merkezi uç nokta koruması, sunucu 2016, geçerli dalı, sunucu 2012
ms.pagetype: security
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.reviewer: pahuijbr
manager: dansimp
ms.technology: mde
ms.topic: article
ms.date: 04/01/2022
ms.collection:
- M365-security-compliance
- m365initiative-defender-endpoint
ms.openlocfilehash: 412033e274cce22b9350292c612b91ef6e34e209
ms.sourcegitcommit: adea59259a5900cad5de29ddf46d1ca9e9e1c82f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/04/2022
ms.locfileid: "64634855"
---
# <a name="microsoft-defender-antivirus-on-windows-server"></a>Microsoft Defender Virüsten Koruma Server'da Windows'i seçin

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Şunlar için geçerlidir:**
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Microsoft Defender Virüsten Koruma, Windows Server'ın aşağıdaki sürümlerinde/sürümlerinde kullanılabilir:

- Windows Server 2022
- Windows Server 2019
- Windows Server, sürüm 1803 veya sonrası
- Windows Server 2016
- Windows Server 2012 R2 (Gerekli Uç Nokta için Microsoft Defender)

## <a name="setting-up-microsoft-defender-antivirus-on-windows-server"></a>Windows Server'da Microsoft Defender Virüsten Koruma ayarlama

Windows Server'da Microsoft Defender Virüsten Koruma kurma ve çalıştırma işlemi aşağıdaki adımları içerir:

1. [Arabirimi etkinleştirin](#enable-the-user-interface-on-windows-server).
2. [Yükleme Microsoft Defender Virüsten Koruma](#install-microsoft-defender-antivirus-on-windows-server).
3. [Microsoft Defender Virüsten Koruma çalıştığını doğrulayın](#verify-microsoft-defender-antivirus-is-running).
4. [Kötü amaçlı yazılımlardan koruma Güvenlik zekası'nızı güncelleştirin](#update-antimalware-security-intelligence).
5. (Gerekirse) [Örnekleri gönderin](#submit-samples).
6. (Gerekirse) [Otomatik dışlamaları yapılandırma](#configure-automatic-exclusions).
7. (Yalnızca gerekirse) Windows [Sunucusunu pasif moduna ayarlayın](#passive-mode-and-windows-server).

## <a name="enable-the-user-interface-on-windows-server"></a>Windows Server'da kullanıcı arabirimini etkinleştirme

> [!IMPORTANT]
> Windows Server 2012 R2 kullanıyorsanız, bkz. Yükleme [seçeneklerini Uç Nokta için Microsoft Defender](configure-server-endpoints.md#options-to-install-the-microsoft-defender-for-endpoint-packages).

Varsayılan olarak, Microsoft Defender Virüsten Koruma Sunucu'da Windows işlevseldir. Bazen, kullanıcı arabirimi (GUI) varsayılan olarak yüklenir. GUI gerekli değildir; veri yönetimi için PowerShell, grup ilkesi yöntemleri veya başka yöntemler Microsoft Defender Virüsten Koruma. Bununla birlikte, birçok kuruluş gui'yi iş için Microsoft Defender Virüsten Koruma. GUI'yi yüklemek için aşağıdaki tabloda yer alan yordamlardan birini kullanın:

| Yordam | Ne yapmalı? |
|:---|:---|
| Rol ve Özellik Ekleme Sihirbazı'nı kullanarak GUI'yi açma | 1. Rol [ve Özellik Ekleme Sihirbazı'nı](/windows-server/administration/server-manager/install-or-uninstall-roles-role-services-or-features#install-roles-role-services-and-features-by-using-the-add-roles-and-features-wizard) kullanarak rolleri, rol hizmetlerini ve özellikleri yükleme ve Rol ve Özellik **Ekleme Sihirbazı'nı kullanma**. <br/><br/>2. Sihirbazın Özellikler adımına **geldiğinde**, Özellikler'in **Windows Defender altında** GUI **for Windows Defender** seçin. |
| PowerShell kullanarak GUI'i açma | 1. Windows Sunucunuzda, Windows PowerShell olarak açın. <br/><br/>2. Aşağıdaki PowerShell cmdlet'ini çalıştırın: `Install-WindowsFeature -Name Windows-Defender-GUI` |

## <a name="install-microsoft-defender-antivirus-on-windows-server"></a>Windows Server'Microsoft Defender Virüsten Koruma yükleme

Windows Server'da Microsoft Defender Virüsten Koruma veya yeniden yüklemeniz gerekirse, aşağıdaki tabloda yer alan yordamlardan birini kullanın:

| Yordam | Ne yapmalı? |
|:---|:---|
| Rol ve Özellik Ekleme Sihirbazı'nı kullanarak Microsoft Defender Virüsten Koruma | 1. Rolleri [, Rol Hizmetlerini veya Özellikleri Yükleme veya Kaldırma'ya bakın ve](/windows-server/administration/server-manager/install-or-uninstall-roles-role-services-or-features#install-roles-role-services-and-features-by-using-the-add-roles-and-features-wizard) Rol **ve Özellik Ekleme Sihirbazı'nı kullanın**. <br/><br/>2. Sihirbazın Özellikler **adımına** geldiğinde, Özellikler adımına Microsoft Defender Virüsten Koruma seçin. Ayrıca, Kullanıcı için **GUI Windows Defender** seçin. |
| Microsoft Defender Virüsten Koruma'i yüklemek için PowerShell kullanma | 1. Windows Sunucunuzda, Windows PowerShell olarak açın. <br/><br/>2. Aşağıdaki PowerShell cmdlet'ini çalıştırın: `Install-WindowsFeature -Name Windows-Defender` |

> [!NOTE]
> Yazılım altyapısına dahil edilen kötü amaçlı yazılımlardan Microsoft Defender Virüsten Koruma iletileri, Microsoft Defender Virüsten Koruma [içinde bulunabilir](troubleshoot-microsoft-defender-antivirus.md).

## <a name="verify-microsoft-defender-antivirus-is-running"></a>Microsoft Defender Virüsten Koruma çalıştığını doğrulama

E-postanızı yükledikten (veya yeniden yükledikten) Microsoft Defender Virüsten Koruma, bir sonraki adımınız çalıştığını doğrulamak olur. Aşağıdaki tabloda yer alan PowerShell cmdlet'lerini kullanın:

| Yordam | PowerShell cmdlet'i |
|:---|:---|
| Microsoft Defender Virüsten Koruma çalıştığını doğrulama | `Get-Service -Name windefend` |
| Güvenlik duvarı korumasının açık olduğunu doğrulama | `Get-Service -Name mpssvc` |

PowerShell'e alternatif olarak, komut istemini kullanarak komutun çalıştığını Microsoft Defender Virüsten Koruma kullanabilirsiniz. Bunu yapmak için, komut isteminde aşağıdaki komutu çalıştırın:

```cmd
sc query Windefend
```

Komut`sc query`, hizmetle ilgili Microsoft Defender Virüsten Koruma döndürür. Microsoft Defender Virüsten Koruma çalışıyor olduğunda, değer `STATE` görüntülenir`RUNNING`.

Çalıştır olmayan tüm hizmetleri görüntülemek için aşağıdaki PowerShell cmdlet'ini çalıştırın:

```cmd
sc query state= all
```

## <a name="update-antimalware-security-intelligence"></a>Kötü amaçlı yazılımlardan korumayı güncelleştirme Güvenlik zekası

Normal güvenlik zekası güncelleştirmelerinizi almak için Windows Update hizmet çalışıyor olması gerekir. Windows Server Update Services (WSUS) gibi bir güncelleştirme yönetim hizmeti kullanıyorsanız, Microsoft Defender Virüsten Koruma Security Intelligence güncelleştirmelerinin yönettiniz bilgisayarlar için onaylandıktan emin olun.

Varsayılan olarak, Windows Update Güncelleştirmeleri Windows Server 2019 veya Windows Server 2022 veya başka bir Windows Server 2016. Aşağıdaki yöntemlerden birini kullanarak bu yapılandırmayı değiştirebilirsiniz:

| Yöntem | Açıklama |
|---|---|
| **Windows Update'da** Denetim Masası | **Güncelleştirmeleri otomatik olarak** yükleme, güvenlik zekası güncelleştirmeleri de dahil olmak üzere tüm güncelleştirmelerin Windows Defender olarak yüklenir. <br/><br/> **Güncelleştirmeleri indirmeme izin ver, ancak** bunları yüklememe izin Windows Defender Güvenlik zekası güncelleştirmelerini otomatik olarak indirip yüklemelerine izin ver, ancak diğer güncelleştirmeler otomatik olarak yüklenmez. |
| **Grup İlkesi** | grup ilkesi'te bulunan ayarları kullanarak Windows Update'i şu şekilde ayar oluşturabilir ve yönetebilirsiniz: Yönetim Şablonları **\Windows Bileşenleri\Windows Update\** Otomatik Güncelleştirmeleri Yapılandırma |
| **AUOptions kayıt** defteri anahtarı | Aşağıdaki iki değer, Güvenlik Windows Update güncelleştirmelerini otomatik olarak indirmesine ve yüklemesine izin verir: <br/><br/> **4** -  **Güncelleştirmeleri otomatik olarak yükleyin**. Bu değer, güvenlik zekası güncelleştirmeleri de dahil olmak üzere tüm güncelleştirmelerin Windows Defender sonucu verir. <br/><br/> **3** -  **Güncelleştirmeleri indirin, ancak yük isteyip seçmeme izin ver**. Bu değer güvenlik Windows Defender güncelleştirmelerini indirme ve yükleme izin verir, ancak diğer güncelleştirmeler otomatik olarak yüklenmez. |

Kötü amaçlı yazılıma karşı korumanın korun olduğundan emin olmak için aşağıdaki hizmetleri etkinleştirin:

- Windows Hata Bildirimi hizmeti
- Windows Update hizmeti

Aşağıdaki tabloda, bağlı hizmetler ve Microsoft Defender Virüsten Koruma hizmetleri listelemektedir.

| Hizmet Adı | Dosya Konumu | Açıklama |
|---|---|---|
| Windows Defender Hizmeti (WinDefend) | `C:\Program Files\Windows Defender\MsMpEng.exe` | Bu, her Microsoft Defender Virüsten Koruma çalışan ana hizmettir.|
| Windows Hata Bildirimi Hizmeti (Wersvc) | `C:\WINDOWS\System32\svchost.exe -k WerSvcGroup` | Bu hizmet hata raporlarını Microsoft'a geri gönderir. |
| Windows Defender Duvarı (MpsSvc) | `C:\WINDOWS\system32\svchost.exe -k LocalServiceNoNetwork` | Güvenlik Duvarı hizmetinin Windows Defender durumda tutmanız önerilir. |
| Windows Update (Wuauserv) | `C:\WINDOWS\system32\svchost.exe -k netsvcs`| Windows Update zekası güncelleştirmelerini ve kötü amaçlı yazılımdan koruma altyapısı güncelleştirmelerini almak için bu gerekli güncelleştirmeler |

## <a name="submit-samples"></a>Örnek gönderme

Örnek gönderme, Microsoft'un kötü amaçlı olabilecek yazılım örnekleri toplamasına olanak sağlar. Devam ve güncel koruma sağlamak için, Microsoft araştırmacısı şüpheli etkinlikleri çözümlemek ve güncelleştirilmiş kötü amaçlı yazılımlardan koruma sağlamak için bu örnekleri kullanır. Program yürütülebilir dosyalarını toplar, örneğin .exe dosyaları ve yürütülebilir .dll toplar. Belgeler ve PDF dosyaları gibi kişisel veri içeren Microsoft Word toplamaya çalışmamız mümkün değildir.

### <a name="submit-a-file"></a>Dosya gönderme

1. Gönderme kılavuzunu [gözden geçirme](/windows/security/threat-protection/intelligence/submission-guide).

2. Örnek gönderim [portalını ziyaret](https://www.microsoft.com/wdsi/filesubmission) edin ve dosyanızı gönderin.

### <a name="enable-automatic-sample-submission"></a>Otomatik örnek gönderimi etkinleştirme

Otomatik örnek gönderimi etkinleştirmek için, Windows PowerShell konsolu başlatın ve **SubmitSamplesConsent** değer verilerini aşağıdaki ayarlardan birini kullanarak ayarlayın:

|Ayar|Açıklama|
|---|---|
| **0** -  **Her zaman sor** | Bu Microsoft Defender Virüsten Koruma, tüm gerekli dosyaların gönderimi onaylamanızı sağlar. bu, Microsoft Defender Virüsten Koruma için varsayılan ayardır ancak GUI olmadan Windows Server 2016 veya 2019 ya da Windows Server 2022 yüklemeleri için önerilmez. |
| **1**  -  **Güvenli örnekleri otomatik olarak gönderme** | Dosya Microsoft Defender Virüsten Koruma "güvenli" olarak işaretlenmiş tüm dosyaları gönderir ve dosyaların kalanının geri kalanının istendiğinde. |
| **2** -  **Hiçbir zaman gönderme** | Microsoft Defender Virüsten Koruma hizmeti istem veya dosya göndermez. |
| **3** -  **Tüm örnekleri otomatik olarak gönderme** | Aşağıdaki Microsoft Defender Virüsten Koruma, tüm dosyaları onay istemi olmadan gönderir. |

> [!NOTE]
> Bu seçenek R2'de Windows Server 2012 kullanılamaz. 

## <a name="configure-automatic-exclusions"></a>Otomatik dışlamaları yapılandırma

Güvenlik ve performansı sağlamaya yardımcı olmak için, bazı dışlamalar Windows Server 2016 veya 2019 ya da Windows Server 2022'de Microsoft Defender Virüsten Koruma'i kullanırken yüklemiş olduğunuz rollere ve özelliklere bağlı olarak otomatik olarak eklenir.

Bkz[. Windows Server'da Microsoft Defender Virüsten Koruma dışlamaları yapılandırma](configure-server-exclusions-microsoft-defender-antivirus.md).

## <a name="passive-mode-and-windows-server"></a>Pasif modu ve Windows Sunucusu

Windows Server'da birincil virüsten koruma çözümünüz olarak Microsoft dışı bir virüsten koruma ürünü kullanıyorsanız, Microsoft Defender Virüsten Koruma veya devre dışı moduna ayarla olasınız. Windows Server uç noktanız Uç Nokta için Microsoft Defender varsa, Microsoft Defender Virüsten Koruma moduna Microsoft Defender Virüsten Koruma için ayarlamanızı sağlar. E-posta Uç Nokta için Microsoft Defender, Microsoft Defender Virüsten Koruma moduna ayarlayın. 

> [!TIP]
> Diğer [Microsoft Defender Virüsten Koruma ürünleriyle uyumluluk sorunlarına bakın](microsoft-defender-antivirus-compatibility.md).

Aşağıdaki tabloda, pasif moduna Microsoft Defender Virüsten Koruma, pasif modunu devre dışı bırakma ve Microsoft Defender Virüsten Koruma kaldırma yöntemleri Microsoft Defender Virüsten Koruma:

| Yordam | Açıklama |
|---|---|
| Kayıt Microsoft Defender Virüsten Koruma kullanarak pasif moduna ayarlama | ForceDefenderPassiveMode kayıt defteri anahtarını aşağıdaki gibi ayarlayın: <br/>- Yol: `HKLM\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection` <br/>- Ad: `ForceDefenderPassiveMode` <br/>- Tür: `REG_DWORD` <br/>- Değer: `1` |
| PowerShell kullanarak Microsoft Defender Virüsten Koruma arabirimini kapatma | Windows PowerShell yönetici olarak açın ve aşağıdaki PowerShell cmdlet'ini çalıştırın:`Uninstall-WindowsFeature -Name Windows-Defender-GUI`
| PowerShell Microsoft Defender Virüsten Koruma'i devre dışı bırakma | Aşağıdaki PowerShell cmdlet'ini kullanın: `Set-MpPreference -DisableRealtimeMonitoring $true` |
| Rol Microsoft Defender Virüsten Koruma Özellikleri Kaldır sihirbazını kullanarak görevleri devre dışı bırakma | Rolleri [, Rol Hizmetlerini veya Özellikleri Yükleme veya Kaldırma'ya bakın](/windows-server/administration/server-manager/install-or-uninstall-roles-role-services-or-features#remove-roles-role-services-and-features-by-using-the-remove-roles-and-features-wizard) ve Rol **ve Özellik Kaldırma Sihirbazı'nı kullanın**. <br/><br/>Sihirbazın Özellikler **adımına** geldiğinde, Özellikler'e Windows Defender **seçeneğinin temizlerini** seçin. <br/><br/> Kullanıcı Özellikleri **Windows Defender** tek başına **Windows Defender**, kullanıcı arabirimi için **GUI seçeneğini kaldırmanız Windows Defender**.<br/><br/>Microsoft Defender Virüsten Koruma kullanıcı arabirimi olmadan da normal çalışır, ancak çekirdek Kaynak Özellikleri özelliğini devre dışı bıraksanız kullanıcı **arabirimi Windows Defender** etkinleştirilmez. |
| PowerShell Microsoft Defender Virüsten Koruma kaldırma | Aşağıdaki PowerShell cmdlet'ini kullanın: `Uninstall-WindowsFeature -Name Windows-Defender` |
| E-Microsoft Defender Virüsten Koruma'i kullanarak devre dışı grup ilkesi | Yerel Sistem Grup ilkesi Düzenleyicisi'nde Yönetim  >  Şablonu **Windows** Bileşen **Endpoint Protection** >  >  **Disable Endpoint Protection'ı** seçin ve **sonra da EnabledOK'u** >  **seçin**. |

### <a name="are-you-using-windows-server-2012-r2-or-windows-server-2016"></a>Windows Server 2012 R2 veya Windows Server 2016?

Windows Sunucunuz Uç Nokta için Microsoft Defender'e Uç Nokta için Microsoft Defender, artık R2'de Microsoft Defender Virüsten Koruma edilgen modda Windows Server 2012 çalıştırabilirsiniz ve Windows Server 2016. Aşağıdaki makalelere bakın:

- [Uç Nokta için Microsoft Defender'i yükleme Uç Nokta için Microsoft Defender](configure-server-endpoints.md#options-to-install-the-microsoft-defender-for-endpoint-packages)

- [Microsoft Defender Virüsten Koruma güvenlik ürünleriyle uyumluluk sorunları](microsoft-defender-antivirus-compatibility.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Windows’da Microsoft Defender Virüsten Koruma](microsoft-defender-antivirus-windows.md)

