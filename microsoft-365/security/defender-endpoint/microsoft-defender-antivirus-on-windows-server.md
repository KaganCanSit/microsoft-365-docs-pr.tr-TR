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
ms.reviewer: pahuijbr, shwjha
manager: dansimp
ms.technology: mde
ms.topic: article
ms.date: 01/26/2022
ms.collection:
- M365-security-compliance
- m365initiative-defender-endpoint
ms.openlocfilehash: 0ea2184720467b3756b5cde8c8973e8952d5b50c
ms.sourcegitcommit: aac7e002ec6e10a41baa2d0bd38614b0ed471a70
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/27/2022
ms.locfileid: "63010000"
---
# <a name="microsoft-defender-antivirus-on-windows-server"></a>Microsoft Defender Virüsten Koruma Server'da Windows'i seçin

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Microsoft Defender Virüsten Koruma, Windows Server'ın aşağıdaki sürümlerinde/sürümlerinde kullanılabilir:

- Windows Server 2022
- Windows Server 2019
- Windows Server, sürüm 1803 veya sonrası
- Windows Server 2016
- Windows Server 2012 R2 (Uç Nokta için Microsoft Defender gerekir)

Bazı durumlarda Microsoft Defender Virüsten Koruma koruma altyapısı *Endpoint Protection*, ancak koruma altyapısı aynıdır. Windows 10 ve Windows 11'de işlevler, yapılandırma ve yönetim [büyük ölçüde Microsoft Defender Virüsten Koruma](microsoft-defender-antivirus-windows.md) aynı olsa da, Windows Server'da birkaç önemli farklılık vardır:

- Sunucu Windows, [otomatik dışlamalar](configure-server-exclusions-microsoft-defender-antivirus.md) tanımlı Sunucu Rolünüz temel alarak uygulanır.

- Windows Server'da, Microsoft dışı bir virüsten koruma/kötü amaçlı yazılımdan koruma çözümü çalıştırdıysanız, Microsoft Defender Virüsten Koruma edilgen moduna veya devre dışı moduna otomatik olarak girmiyor. Bununla birlikte, edilgen veya devre Microsoft Defender Virüsten Koruma modunu el ile ayarlayın.

## <a name="setting-up-microsoft-defender-antivirus-on-windows-server"></a>Windows Server'da Microsoft Defender Virüsten Koruma ayarlama

Sunucu platformunda e-Microsoft Defender Virüsten Koruma ayarlama ve çalıştırma işlemi birkaç adım içerir:

1. [Arabirimi etkinleştirin](#enable-the-user-interface-on-windows-server).
2. [Yükleme Microsoft Defender Virüsten Koruma](#install-microsoft-defender-antivirus-on-windows-server).
3. [Microsoft Defender Virüsten Koruma çalıştığını doğrulayın](#verify-microsoft-defender-antivirus-is-running).
4. [Kötü amaçlı yazılımlardan koruma Güvenlik zekası'nızı güncelleştirin](#update-antimalware-security-intelligence).
5. (Gerekirse) [Örnekleri gönderin](#submit-samples).
6. (Gerekirse) [Otomatik dışlamaları yapılandırma](#configure-automatic-exclusions).
7. (Yalnızca gerekirse) Windows [Sunucusunu pasif moduna ayarlayın](#passive-mode-and-windows-server).

## <a name="enable-the-user-interface-on-windows-server"></a>Windows Server'da kullanıcı arabirimini etkinleştirme

Varsayılan olarak, Microsoft Defender Virüsten Koruma Sunucu'da Windows işlevseldir. Bazen, kullanıcı arabirimi (GUI) varsayılan olarak yüklenir ancak GUI gerekli değildir. PowerShell'i, Grup İlkesi'i veya diğer yöntemleri kullanarak Microsoft Defender Virüsten Koruma.

GUI sunucunuzda yüklü değilse ve bunu yüklemek için Rol ve Özellik Ekle sihirbazı veya PowerShell cmdlet'leri kullanılabilir.

> [!NOTE]
> Bu seçenek R2'de Windows Server 2012 kullanılamaz. Daha fazla bilgi için bkz [. Uç Nokta için Microsoft Defender'ı yükleme seçenekleri](configure-server-endpoints.md#options-to-install-the-microsoft-defender-for-endpoint-packages).

### <a name="turn-on-the-gui-using-the-add-roles-and-features-wizard"></a>Rol ve Özellik Ekleme Sihirbazı'nı kullanarak GUI'yi açma

1. Rol [ve Özellik Ekleme Sihirbazı'nı kullanarak rolleri,](/windows-server/administration/server-manager/install-or-uninstall-roles-role-services-or-features#install-roles-role-services-and-features-by-using-the-add-roles-and-features-wizard) rol hizmetlerini ve özellikleri yükleme ve Rol ve **Özellik Ekleme Sihirbazı'nı kullanma.**

2. Sihirbazın Özellikler **adımına geldiğinde**, Özellikler'in **altında Windows Defender** **GUI for Windows Defender** seçin.

   Başka Windows Server 2016, **Rol ve Özellik Ekleme Sihirbazı** şöyle görünüyor:

   ![Rol ve özellik sihirbazında GUI for Windows Defender ekleyin.](images/server-add-gui.png)

   Windows Server 2019 ve Windows Server 2022'de Rol ve **Özellik Ekleme Sihirbazı** benzer.

### <a name="turn-on-the-gui-using-powershell"></a>PowerShell kullanarak GUI'i açma

Aşağıdaki PowerShell cmdlet'i arabirimi etkinleştirir:

```powershell
Install-WindowsFeature -Name Windows-Defender-GUI
```

## <a name="install-microsoft-defender-antivirus-on-windows-server"></a>Windows Server'Microsoft Defender Virüsten Koruma yükleme

Windows Server'da Microsoft Defender Virüsten Koruma ya da yeniden yüklemeniz gerekirse, Rol ve Özellik Ekleme Sihirbazı'nı veya PowerShell'i **kullanarak bunuabilirsiniz**.

### <a name="use-the-add-roles-and-features-wizard-to-install-microsoft-defender-antivirus"></a>Rol ve Özellik Ekleme Sihirbazı'nı kullanarak Microsoft Defender Virüsten Koruma

1. Bu [makaleye bakın](/windows-server/administration/server-manager/install-or-uninstall-roles-role-services-or-features#install-roles-role-services-and-features-by-using-the-add-roles-and-features-wizard) ve Rol ve **Özellik Ekleme Sihirbazı'nı kullanın**.

2. Sihirbazın Özellikler **adımına** geldiğinde, Özellikler Microsoft Defender Virüsten Koruma seçin. Ayrıca, Kullanıcı için **GUI Windows Defender** seçin.

### <a name="use-powershell-to-install-microsoft-defender-antivirus"></a>Microsoft Defender Virüsten Koruma'i yüklemek için PowerShell kullanma

Bu cmdlet'i PowerShell Microsoft Defender Virüsten Koruma için aşağıdaki cmdlet'i çalıştırın:

```powershell
Install-WindowsFeature -Name Windows-Defender
```

Yazılım altyapısına dahil edilen kötü amaçlı yazılımlardan Microsoft Defender Virüsten Koruma iletileri, Microsoft Defender Virüsten Koruma [içinde bulunabilir](troubleshoot-microsoft-defender-antivirus.md).

## <a name="verify-microsoft-defender-antivirus-is-running"></a>Microsoft Defender Virüsten Koruma çalıştığını doğrulama

Microsoft Defender Virüsten Koruma yüklendikten sonra, bir sonraki adımınız dosyanın çalıştığını doğrulamak olur. Windows Server uç noktanız üzerinde aşağıdaki PowerShell cmdlet'ini çalıştırın:

```powershell
Get-Service -Name windefend
```

Güvenlik duvarı korumasının açık olduğunu doğrulamak için aşağıdaki PowerShell cmdlet'ini çalıştırın:

```powershell
Get-Service -Name mpssvc
```

PowerShell'e alternatif olarak, komut istemini kullanarak komutun çalıştığını Microsoft Defender Virüsten Koruma kullanabilirsiniz. Bunu yapmak için, komut isteminde aşağıdaki komutu çalıştırın:

```console
sc query Windefend
```

Komut`sc query`, hizmetle ilgili Microsoft Defender Virüsten Koruma döndürür. Microsoft Defender Virüsten Koruma çalışıyor olduğunda, değer `STATE` görüntülenir`RUNNING`.

Çalıştır olmayan tüm hizmetleri görüntülemek için aşağıdaki PowerShell cmdlet'ini çalıştırın:

```console
sc query state= all
```

## <a name="update-antimalware-security-intelligence"></a>Kötü amaçlı yazılımlardan korumayı güncelleştirme Güvenlik zekası

Güncelleştirilmiş kötü amaçlı yazılımlardan koruma güvenlik zekası almak için, güncelleştirme Windows çalışıyor olması gerekir. Windows Server Update Services (WSUS) gibi bir güncelleştirme yönetim hizmeti kullanıyorsanız, Microsoft Defender Virüsten Koruma Security Intelligence güncelleştirmelerinin yönettiniz bilgisayarlar için onaylandıktan emin olun.

Varsayılan olarak, Windows Update Windows Server 2019 veya Windows Server 2022 veya Windows Server 2016'de güncelleştirmeleri otomatik olarak indirmez ve Windows Server 2016. Aşağıdaki yöntemlerden birini kullanarak bu yapılandırmayı değiştirebilirsiniz:

<br/><br/>

| Yöntem | Açıklama |
|---|---|
| **Windows Denetim Masası'nda** Güncelleştirme | **Güncelleştirmeleri otomatik olarak** yükleme, güvenlik zekası güncelleştirmeleri de dahil olmak üzere tüm güncelleştirmelerin Windows Defender olarak yüklenir. <br/><br/> **Güncelleştirmeleri indirmeme izin ver, ancak** bunları yüklememe izin Windows Defender Güvenlik zekası güncelleştirmelerini otomatik olarak indirip yüklemelerine izin ver, ancak diğer güncelleştirmeler otomatik olarak yüklenmez. |
| **Grup İlkesi** | Grup İlkesi'Windows bulunan ayarları kullanarak, şu yolu kullanarak ayarları değiştirebilir ve yönetebilirsiniz: Yönetim Şablonları **\Windows Bileşenleri\Windows Güncelleştirmesi\** Otomatik Güncelleştirmeleri Yapılandır |
| **AUOptions kayıt** defteri anahtarı | Aşağıdaki iki değer, Güncelleştirme'Windows Güvenlik Zekası güncelleştirmelerini otomatik olarak indirmesine ve yüklemesine izin verir: <br/><br/> **4** -  **Güncelleştirmeleri otomatik olarak yükleyin**. Bu değer, güvenlik zekası güncelleştirmeleri de dahil olmak üzere tüm güncelleştirmelerin Windows Defender sonucu verir. <br/><br/> **3** -  **Güncelleştirmeleri indirin, ancak yük isteyip seçmeme izin ver**. Bu değer güvenlik Windows Defender güncelleştirmelerini indirme ve yükleme izin verir, ancak diğer güncelleştirmeler otomatik olarak yüklenmez. |

Kötü amaçlı yazılıma karşı korumanın korunmasını sağlamak için aşağıdaki hizmetleri etkinleştirmenizi öneririz:

- Windows Hata Bildirimi hizmeti
- Windows Güncelleştirme hizmeti

Aşağıdaki tabloda, bağlı hizmetler ve Microsoft Defender Virüsten Koruma hizmetleri listelemektedir.

<br/><br/>


| Hizmet Adı | Dosya Konumu | Açıklama |
|---|---|---|
| Windows Defender Hizmeti (WinDefend) | `C:\Program Files\Windows Defender\MsMpEng.exe` | Her zaman Microsoft Defender Virüsten Koruma olan ana hizmettir.|
| Windows Hata Bildirimi Hizmeti (Wersvc) | `C:\WINDOWS\System32\svchost.exe -k WerSvcGroup` | Bu hizmet hata raporlarını Microsoft'a geri gönderir. |
| Windows Defender Duvarı (MpsSvc) | `C:\WINDOWS\system32\svchost.exe -k LocalServiceNoNetwork` | Güvenlik Duvarı hizmetini Windows Defender bırakmanız önerilir. |
| Windows Güncelleştirmesi (Wuauserv) | `C:\WINDOWS\system32\svchost.exe -k netsvcs`| Windows Zekası güncelleştirmelerini ve kötü amaçlı yazılımdan koruma altyapısı güncelleştirmelerini almak için güncelleştirme gerekiyor |

## <a name="submit-samples"></a>Örnek gönderme

Örnek gönderme, Microsoft'un kötü amaçlı olabilecek yazılım örnekleri toplamasına olanak sağlar. Devam ve güncel koruma sağlamak için, Microsoft araştırmacısı şüpheli etkinlikleri çözümlemek ve güncelleştirilmiş kötü amaçlı yazılımlardan koruma sağlamak için bu örnekleri kullanır. Program yürütülebilir dosyalarını toplar, örneğin .exe dosyaları ve yürütülebilir .dll toplar. Belgeler ve PDF dosyaları gibi kişisel veri içeren Microsoft Word toplamaya çalışmamız mümkün değildir.

### <a name="submit-a-file"></a>Dosya gönderme

1. Gönderme kılavuzunu [gözden geçirme](/windows/security/threat-protection/intelligence/submission-guide).
2. Örnek gönderim [portalını ziyaret](https://www.microsoft.com/wdsi/filesubmission) edin ve dosyanızı gönderin.

### <a name="enable-automatic-sample-submission"></a>Otomatik örnek gönderimi etkinleştirme

Otomatik örnek gönderimi etkinleştirmek için, Windows PowerShell konsolu başlatın ve **SubmitSamplesConsent** değer verilerini aşağıdaki ayarlardan birini kullanarak ayarlayın:

<br/><br/>

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

Windows Server'da birincil virüsten koruma çözümünüz olarak Microsoft dışı bir virüsten koruma ürünü kullanıyorsanız, Microsoft Defender Virüsten Koruma veya devre dışı moduna ayarla olasınız.

Daha fazla bilgi için bkz[. Microsoft Defender Virüsten Koruma Server'Windows yükleme](microsoft-defender-antivirus-on-windows-server.md#install-microsoft-defender-antivirus-on-windows-server).


### <a name="set-microsoft-defender-antivirus-to-passive-mode-using-a-registry-key"></a>Kayıt Microsoft Defender Virüsten Koruma kullanarak pasif moduna ayarlama

Aşağıdaki kayıt Microsoft Defender Virüsten Koruma edilgen moduna geçer ve bunu pasif moduna:
- Yol: `HKLM\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection`
- Ad: `ForceDefenderPassiveMode`
- Tür: `REG_DWORD`
- Değer: `1`

### <a name="disable-microsoft-defender-antivirus-using-the-remove-roles-and-features-wizard"></a>Rol Microsoft Defender Virüsten Koruma Özellikleri Kaldır sihirbazını kullanarak görevleri devre dışı bırakma

1. Rolleri [, Rol Hizmetlerini veya Özellikleri Yükleme veya Kaldırma'ya bakın](/windows-server/administration/server-manager/install-or-uninstall-roles-role-services-or-features#remove-roles-role-services-and-features-by-using-the-remove-roles-and-features-wizard) ve Rol **ve Özellik Kaldırma Sihirbazı'nı kullanın**.

2. Sihirbazın Özellikler **adımına** geldiğinde, Özellikler'e Windows Defender **seçeneğinin temizlerini** seçin.

    Kullanıcı Özellikleri **Windows Defender** tek başına **Windows Defender**, kullanıcı arabirimi için **GUI seçeneğini kaldırmanız Windows Defender**.

    Microsoft Defender Virüsten Koruma kullanıcı arabirimi olmadan da normal çalışır, ancak çekirdek Kaynak Özellikleri özelliğini devre dışı bıraksanız kullanıcı **arabirimi Windows Defender** etkinleştirilmez.

### <a name="turn-off-the-microsoft-defender-antivirus-user-interface-using-powershell"></a>PowerShell kullanarak Microsoft Defender Virüsten Koruma arabirimini kapatma

GUI'ye Microsoft Defender Virüsten Koruma için aşağıdaki PowerShell cmdlet'ini kullanın:

```powershell
Uninstall-WindowsFeature -Name Windows-Defender-GUI
```

### <a name="are-you-using-windows-server-2012-r2-or-windows-server-2016"></a>Windows Server 2012 R2 veya Windows Server 2016?

Artık R2 ve Microsoft Defender Virüsten Koruma üzerinde pasif modunda Windows Server 2012 çalıştır Windows Server 2016 abilirsiniz. Daha fazla bilgi için bkz [. Uç Nokta için Microsoft Defender'ı yükleme seçenekleri](configure-server-endpoints.md#options-to-install-the-microsoft-defender-for-endpoint-packages).

<br/><br/>

| Yordam | Açıklama |
|---|---|
| Grup İlkesi Microsoft Defender Virüsten Koruma'i devre dışı bırakma | Yerel Grup İlkesi Düzenleyicisi'nizin Yönetim Şablonu  > **Windows Bileşen** >  >  Endpoint Protection **Disable Endpoint Protection** seçeneğine gidin ve **sonra EnabledOK'u** >  **seçin**. |
| Kayıt Microsoft Defender Virüsten Koruma anahtarını kullanarak e-postayı devre dışı bırakma | [DisableAntiCcaware](/windows-hardware/customize/desktop/unattend/security-malware-windows-defender-disableantispyware) kayıt defteri anahtarını kullanmak için, seçeneğine `HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Defender`gidin ve adlı bir DWORD girdisi ayarlayın veya oluşturun`DisableAntiSpyware`. Değerini (kayıt defteri `1` anahtarının değerini doğru olarak ayarlar) *ayarlayın*. |
| PowerShell Microsoft Defender Virüsten Koruma'i devre dışı bırakma | Aşağıdaki PowerShell cmdlet'ini kullanın: `Set-MpPreference -DisableRealtimeMonitoring $true` |
| PowerShell Microsoft Defender Virüsten Koruma kaldırma | Aşağıdaki PowerShell cmdlet'ini kullanın: `Uninstall-WindowsFeature -Name Windows-Defender` |


## <a name="see-also"></a>Ayrıca bkz.

- [Microsoft Defender Virüsten Koruma'da Windows](microsoft-defender-antivirus-windows.md)
- [Microsoft Defender Virüsten Koruma uyumluluğu](microsoft-defender-antivirus-compatibility.md)
