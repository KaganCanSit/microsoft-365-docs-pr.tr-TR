---
title: Windows Server'da Microsoft Defender Virüsten Koruma
description: Windows Server 2016, Windows Server 2019 ve Windows Server 2022'de Microsoft Defender Virüsten Koruma etkinleştirmeyi ve yapılandırmayı öğrenin.
keywords: windows defender, server, scep, system center endpoint protection, server 2016, current branch, server 2012
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
ms.openlocfilehash: b93595375982e3ed61d1ac94ae410575b0d72307
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2022
ms.locfileid: "64666998"
---
# <a name="microsoft-defender-antivirus-on-windows-server"></a>Windows Server'da Microsoft Defender Virüsten Koruma

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Şunlar için geçerlidir:**
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Microsoft Defender Virüsten Koruma, Windows Server'ın aşağıdaki sürümlerinde/sürümlerinde kullanılabilir:

- Windows Server 2022
- Windows Server 2019
- Windows Server, sürüm 1803 veya üzeri
- Windows Server 2016
- Windows Server 2012 R2 (Uç Nokta için Microsoft Defender gerektirir)

## <a name="setting-up-microsoft-defender-antivirus-on-windows-server"></a>Windows Sunucusu'nda Microsoft Defender Virüsten Koruma ayarlama

Windows Sunucusu'nda Microsoft Defender Virüsten Koruma ayarlama ve çalıştırma işlemi aşağıdaki adımları içerir:

1. [Arabirimi etkinleştirin](#enable-the-user-interface-on-windows-server).
2. [Microsoft Defender Virüsten Koruma yükleyin](#install-microsoft-defender-antivirus-on-windows-server).
3. [Microsoft Defender Virüsten Koruma çalıştığını doğrulayın](#verify-microsoft-defender-antivirus-is-running).
4. [Kötü amaçlı yazılımdan koruma güvenlik zekanızı güncelleştirin](#update-antimalware-security-intelligence).
5. (Gerektiğinde) [Örnekleri gönderin](#submit-samples).
6. (Gerektiğinde) [Otomatik dışlamaları yapılandırın](#configure-automatic-exclusions).
7. (Yalnızca gerekirse) [Windows Sunucusu'nu pasif moda](#passive-mode-and-windows-server) ayarlayın.

## <a name="enable-the-user-interface-on-windows-server"></a>Windows Sunucusu'nda kullanıcı arabirimini etkinleştirme

> [!IMPORTANT]
> Windows Server 2012 R2 kullanıyorsanız bkz. [Uç Nokta için Microsoft Defender yükleme seçenekleri](configure-server-endpoints.md#options-to-install-the-microsoft-defender-for-endpoint-packages).

Varsayılan olarak, Microsoft Defender Virüsten Koruma Windows Sunucusu'nda yüklü ve işlevseldir. Bazen kullanıcı arabirimi (GUI) varsayılan olarak yüklenir. GUI gerekli değildir; Microsoft Defender Virüsten Koruma yönetmek için PowerShell, grup ilkesi veya diğer yöntemleri kullanabilirsiniz. Ancak, birçok kuruluş Microsoft Defender Virüsten Koruma için GUI kullanmayı tercih eder. GUI'yi yüklemek için aşağıdaki tabloda yer alan yordamlardan birini kullanın:

| Yordam | Yapılması gerekenler |
|:---|:---|
| Rol ve Özellik Ekleme Sihirbazı'nı kullanarak GUI'yi açma | 1. Rol [ve Özellik Ekleme Sihirbazı'nı kullanarak rolleri, rol hizmetlerini ve özellikleri yükleme](/windows-server/administration/server-manager/install-or-uninstall-roles-role-services-or-features#install-roles-role-services-and-features-by-using-the-add-roles-and-features-wizard) ve **Rol ve Özellik Ekleme Sihirbazı'nı** kullanma bölümüne bakın. <br/><br/>2. Sihirbazın **Özellikler** adımına gittiğiniz zaman, **Windows Defender Özellikler'in** altında **Windows Defender için GUI** seçeneğini belirleyin. |
| PowerShell kullanarak GUI'yi açma | 1. Windows Sunucunuzda Windows PowerShell yönetici olarak açın. <br/><br/>2. Aşağıdaki PowerShell cmdlet'ini çalıştırın: `Install-WindowsFeature -Name Windows-Defender-GUI` |

## <a name="install-microsoft-defender-antivirus-on-windows-server"></a>Windows Server'a Microsoft Defender Virüsten Koruma yükleme

Windows Server'da Microsoft Defender Virüsten Koruma yüklemeniz veya yeniden yüklemeniz gerekiyorsa, aşağıdaki tabloda yer alan yordamlardan birini kullanın:

| Yordam | Yapılması gerekenler |
|:---|:---|
| Microsoft Defender Virüsten Koruma yüklemek için Rol ve Özellik Ekleme Sihirbazı'nı kullanma | 1. Rolleri [, Rol Hizmetlerini veya Özellikleri Yükleme veya Kaldırma](/windows-server/administration/server-manager/install-or-uninstall-roles-role-services-or-features#install-roles-role-services-and-features-by-using-the-add-roles-and-features-wizard) bölümüne bakın ve **Rol ve Özellik Ekleme Sihirbazı'nı** kullanın. <br/><br/>2. Sihirbazın **Özellikler** adımına gittiğiniz zaman Microsoft Defender Virüsten Koruma seçeneğini belirleyin. Ayrıca **Windows Defender için GUI** seçeneğini belirleyin. |
| Microsoft Defender Virüsten Koruma yüklemek için PowerShell kullanma | 1. Windows Sunucunuzda Windows PowerShell yönetici olarak açın. <br/><br/>2. Aşağıdaki PowerShell cmdlet'ini çalıştırın: `Install-WindowsFeature -Name Windows-Defender` |

> [!NOTE]
> Microsoft Defender Virüsten Koruma ile birlikte gelen kötü amaçlı yazılımdan koruma altyapısı için olay iletileri [Microsoft Defender Virüsten Koruma Olayları'nda](troubleshoot-microsoft-defender-antivirus.md) bulunabilir.

## <a name="verify-microsoft-defender-antivirus-is-running"></a>Microsoft Defender Virüsten Koruma çalıştığını doğrulama

Microsoft Defender Virüsten Koruma yükledikten (veya yeniden yükledikten) sonra, sonraki adımınız çalıştığını doğrulamaktır. Aşağıdaki tablodaki PowerShell cmdlet'lerini kullanın:

| Yordam | PowerShell cmdlet'i |
|:---|:---|
| Microsoft Defender Virüsten Koruma çalıştığını doğrulayın | `Get-Service -Name windefend` |
| Güvenlik duvarı korumasının açık olduğunu doğrulayın | `Get-Service -Name mpssvc` |

PowerShell'e alternatif olarak Komut İstemi'ni kullanarak Microsoft Defender Virüsten Koruma çalıştığını doğrulayabilirsiniz. Bunu yapmak için bir komut isteminden aşağıdaki komutu çalıştırın:

```cmd
sc query Windefend
```

komut, `sc query` Microsoft Defender Virüsten Koruma hizmeti hakkındaki bilgileri döndürür. Microsoft Defender Virüsten Koruma çalışırken `STATE` değeri görüntülenir`RUNNING`.

Çalışmayan tüm hizmetleri görüntülemek için aşağıdaki PowerShell cmdlet'ini çalıştırın:

```cmd
sc query state= all
```

## <a name="update-antimalware-security-intelligence"></a>Kötü amaçlı yazılımdan koruma güvenlik bilgilerini güncelleştirme

Normal güvenlik bilgileri güncelleştirmelerinizi almak için Windows Update hizmetinin çalışıyor olması gerekir. Windows Sunucu Güncelleştirme Hizmetleri (WSUS) gibi bir güncelleştirme yönetimi hizmeti kullanıyorsanız, yönettiğiniz bilgisayarlar için Microsoft Defender Virüsten Koruma Güvenlik bilgileri güncelleştirmelerinin onaylandığından emin olun.

varsayılan olarak, Windows Update güncelleştirmeleri Windows Server 2019 veya Windows Server 2022 veya Windows Server 2016'a otomatik olarak indirmez ve yüklemez. Aşağıdaki yöntemlerden birini kullanarak bu yapılandırmayı değiştirebilirsiniz:

| Yöntem | Açıklama |
|---|---|
| **Denetim Masası'da** Windows Update | **Güncelleştirmeleri otomatik olarak yükleme**, Windows Defender Güvenlik bilgileri güncelleştirmeleri de dahil olmak üzere tüm güncelleştirmelerin otomatik olarak yüklenmesine neden olur. <br/><br/> **Güncelleştirmeleri indir ama yüklenip yüklenmeyeceğini seçmeme izin ver**, Windows Defender Güvenlik bilgileri güncelleştirmelerini otomatik olarak indirip yüklemesine izin verir, ancak diğer güncelleştirmeler otomatik olarak yüklenmez. |
| **Grup İlkesi** | grup ilkesi'da bulunan ayarları kullanarak Windows Update ayarlayabilir ve yönetebilirsiniz: **Yönetim Şablonları\Windows Components\Windows Update\Otomatik Güncelleştirmeleri Yapılandır** |
| **AUOptions** kayıt defteri anahtarı | Aşağıdaki iki değer Windows Update Güvenlik bilgileri güncelleştirmelerini otomatik olarak indirip yüklemesine olanak sağlar: <br/><br/> **4** -  **Güncelleştirmeleri otomatik olarak yükleyin**. Bu değer, Windows Defender Güvenlik bilgileri güncelleştirmeleri de dahil olmak üzere tüm güncelleştirmelerin otomatik olarak yüklenmesine neden olur. <br/><br/> **3** -  **Güncelleştirmeleri indirin ama yüklenip yüklenmeyeceğini ben seçeyim**. Bu değer, Windows Defender Güvenlik bilgileri güncelleştirmelerini otomatik olarak indirip yüklemesine olanak tanır, ancak diğer güncelleştirmeler otomatik olarak yüklenmez. |

Kötü amaçlı yazılımdan korumanın korunmasını sağlamak için aşağıdaki hizmetleri etkinleştirin:

- Windows Hata Bildirimi hizmeti
- Windows Update hizmeti

Aşağıdaki tabloda Microsoft Defender Virüsten Koruma hizmetleri ve bağımlı hizmetler listelenmektedir.

| Hizmet Adı | Dosya Konumu | Açıklama |
|---|---|---|
| Windows Defender Hizmeti (WinDefend) | `C:\Program Files\Windows Defender\MsMpEng.exe` | Bu, her zaman çalışması gereken ana Microsoft Defender Virüsten Koruma hizmetidir.|
| Windows Hata Bildirimi Hizmeti (Wersvc) | `C:\WINDOWS\System32\svchost.exe -k WerSvcGroup` | Bu hizmet hata raporlarını Microsoft'a geri gönderir. |
| Windows Defender Güvenlik Duvarı (MpsSvc) | `C:\WINDOWS\system32\svchost.exe -k LocalServiceNoNetwork` | Windows Defender Güvenlik Duvarı hizmetini etkin tutmanızı öneririz. |
| Windows Update (Wuauserv) | `C:\WINDOWS\system32\svchost.exe -k netsvcs`| Güvenlik bilgileri güncelleştirmelerini ve kötü amaçlı yazılımdan koruma altyapısı güncelleştirmelerini almak için Windows Update gereklidir |

## <a name="submit-samples"></a>Örnekleri gönderme

Örnek gönderim, Microsoft'un kötü amaçlı olabilecek yazılım örneklerini toplamasına olanak tanır. Microsoft araştırmacıları, sürekli ve güncel koruma sağlamaya yardımcı olmak için bu örnekleri kullanarak şüpheli etkinlikleri analiz eder ve güncelleştirilmiş kötü amaçlı yazılımdan koruma güvenlik bilgileri üretir. .exe dosyaları ve .dll dosyaları gibi program yürütülebilir dosyalarını toplarız. Microsoft Word belgeler ve PDF dosyaları gibi kişisel veriler içeren dosyaları toplamayız.

### <a name="submit-a-file"></a>Dosya gönderme

1. [Gönderme kılavuzunu](/windows/security/threat-protection/intelligence/submission-guide) gözden geçirin.

2. [Örnek gönderim portalını](https://www.microsoft.com/wdsi/filesubmission) ziyaret edin ve dosyanızı gönderin.

### <a name="enable-automatic-sample-submission"></a>Otomatik örnek göndermeyi etkinleştirme

Otomatik örnek gönderimini etkinleştirmek için yönetici olarak bir Windows PowerShell konsolu başlatın ve **SubmitSamplesConsent** değer verilerini aşağıdaki ayarlardan birine göre ayarlayın:

|Ayar|Açıklama|
|---|---|
| **0** -  **Her zaman iste** | Microsoft Defender Virüsten Koruma hizmeti, tüm gerekli dosyaların gönderilmesini onaylamanızı ister. Bu, Microsoft Defender Virüsten Koruma için varsayılan ayardır, ancak Windows Server 2016 veya 2019 veya Windows Server 2022'de GUI olmadan yapılan yüklemeler için önerilmez. |
| **1**  -  **Güvenli örnekleri otomatik olarak gönderme** | Microsoft Defender Virüsten Koruma hizmeti "güvenli" olarak işaretlenmiş tüm dosyaları gönderir ve dosyaların geri kalanını ister. |
| **2** -  **Hiçbir zaman gönderme** | Microsoft Defender Virüsten Koruma hizmeti soru sormaz ve hiçbir dosya göndermez. |
| **3** -  **Tüm örnekleri otomatik olarak gönderme** | Microsoft Defender Virüsten Koruma hizmeti, onay istemi olmadan tüm dosyaları gönderir. |

> [!NOTE]
> Bu seçenek Windows Server 2012 R2 için kullanılamaz. 

## <a name="configure-automatic-exclusions"></a>Otomatik dışlamaları yapılandırma

Güvenlik ve performansın sağlanmasına yardımcı olmak için, Windows Server 2016 veya 2019 veya Windows Server 2022'de Microsoft Defender Virüsten Koruma kullanırken yüklediğiniz rollere ve özelliklere göre belirli dışlamalar otomatik olarak eklenir.

Bkz[. Windows Server'da Microsoft Defender Virüsten Koruma'de dışlamaları yapılandırma](configure-server-exclusions-microsoft-defender-antivirus.md).

## <a name="passive-mode-and-windows-server"></a>Pasif mod ve Windows Sunucusu

Windows Server'da birincil virüsten koruma çözümünüz olarak Microsoft dışı bir virüsten koruma ürünü kullanıyorsanız, Microsoft Defender Virüsten Koruma pasif moda veya devre dışı moduna ayarlamanız gerekir. Windows Sunucusu uç noktanız Uç Nokta için Microsoft Defender ekliyse, Microsoft Defender Virüsten Koruma pasif moda ayarlayabilirsiniz. Uç Nokta için Microsoft Defender kullanmıyorsanız, Microsoft Defender Virüsten Koruma devre dışı moduna ayarlayın. 

> [!TIP]
> Bkz. [diğer güvenlik ürünleriyle uyumluluk Microsoft Defender Virüsten Koruma](microsoft-defender-antivirus-compatibility.md).

Aşağıdaki tabloda, Microsoft Defender Virüsten Koruma pasif moda ayarlama, Microsoft Defender Virüsten Koruma devre dışı bırakma ve Microsoft Defender Virüsten Koruma kaldırma yöntemleri açıklanmaktadır:

| Yordam | Açıklama |
|---|---|
| Kayıt defteri anahtarı kullanarak Microsoft Defender Virüsten Koruma pasif moda ayarlama | ForceDefenderPassiveMode kayıt defteri anahtarını aşağıdaki gibi ayarlayın: <br/>- Yol: `HKLM\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection` <br/>- Ad: `ForceDefenderPassiveMode` <br/>- Tür: `REG_DWORD` <br/>- Değer: `1` |
| PowerShell kullanarak Microsoft Defender Virüsten Koruma kullanıcı arabirimini kapatma | Windows PowerShell yönetici olarak açın ve aşağıdaki PowerShell cmdlet'ini çalıştırın:`Uninstall-WindowsFeature -Name Windows-Defender-GUI`
| PowerShell kullanarak Microsoft Defender Virüsten Koruma devre dışı bırakma | Aşağıdaki PowerShell cmdlet'ini kullanın: `Set-MpPreference -DisableRealtimeMonitoring $true` |
| Rol ve Özellik Kaldırma sihirbazını kullanarak Microsoft Defender Virüsten Koruma devre dışı bırakma | Bkz. [Rolleri, Rol Hizmetlerini veya Özellikleri Yükleme veya Kaldırma](/windows-server/administration/server-manager/install-or-uninstall-roles-role-services-or-features#remove-roles-role-services-and-features-by-using-the-remove-roles-and-features-wizard) ve **Rolleri ve Özellikleri Kaldırma Sihirbazı'nı** kullanma. <br/><br/>Sihirbazın **Özellikler** adımına gittiğiniz zaman **Windows Defender Özellikler** seçeneğini temizleyin. <br/><br/> Windows Defender **Özellikleri** bölümünde **Windows Defender** tek başına temizlerseniz, **Windows Defender için** arabirim seçeneği GUI'sini kaldırmanız istenir.<br/><br/>Microsoft Defender Virüsten Koruma kullanıcı arabirimi olmadan normal şekilde çalışmaya devam eder, ancak çekirdek **Windows Defender** özelliğini devre dışı bırakırsanız kullanıcı arabirimi etkinleştirilemiyor. |
| PowerShell kullanarak Microsoft Defender Virüsten Koruma kaldırma | Aşağıdaki PowerShell cmdlet'ini kullanın: `Uninstall-WindowsFeature -Name Windows-Defender` |
| grup ilkesi kullanarak Microsoft Defender Virüsten Koruma devre dışı bırakma | Yerel grup ilkesi Düzenleyicinizde **Yönetim Şablonu** >  **Windows Bileşeni** >  **Endpoint Protection** >  **Disable Endpoint Protection'na** gidin ve **EnabledOK'yi** >  seçin. |

### <a name="are-you-using-windows-server-2012-r2-or-windows-server-2016"></a>Windows Server 2012 R2 mi yoksa Windows Server 2016 mi kullanıyorsunuz?

Windows Sunucunuz Uç Nokta için Microsoft Defender'a ekliyse artık Microsoft Defender Virüsten Koruma Windows Server 2012 R2'de pasif modda çalıştırabilirsiniz ve Windows Server 2016. Aşağıdaki makalelere bakın:

- [Uç Nokta için Microsoft Defender yükleme seçenekleri](configure-server-endpoints.md#options-to-install-the-microsoft-defender-for-endpoint-packages)

- [Microsoft Defender Virüsten Koruma diğer güvenlik ürünleriyle uyumluluk](microsoft-defender-antivirus-compatibility.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Windows’da Microsoft Defender Virüsten Koruma](microsoft-defender-antivirus-windows.md)

