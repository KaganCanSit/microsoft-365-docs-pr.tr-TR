---
title: Dışlamaları tanımlarken kaçınılması gereken yaygın hatalar
description: Microsoft Defender Virüsten Koruma taramaları için dışlamaları tanımlarken yaygın hatalardan kaçının.
keywords: dışlamalar, dosyalar, uzantı, dosya türü, klasör adı, dosya adı, taramalar
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.topic: article
ms.date: 06/16/2022
ms.collection: M365-security-compliance
ms.openlocfilehash: 99d59c2027d3b34ad5c9c19444a51dd08cc22276
ms.sourcegitcommit: 997eb64f80da99b1099daba62994c722bbb25d72
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/16/2022
ms.locfileid: "66128668"
---
# <a name="common-mistakes-to-avoid-when-defining-exclusions"></a>Dışlamaları tanımlarken kaçınılması gereken yaygın hatalar

**Şunlar için geçerlidir:**
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Uç Nokta için Microsoft Defender Planı 1
- Microsoft Defender Virüsten Koruma 

**Platform**

- Windows
- macOS
- Linux

> [!IMPORTANT]
> **Dışlamaları dikkatli bir şekilde ekleyin**. Microsoft Defender Virüsten Koruma taramaları için dışlamalar, cihazlar için koruma düzeyini azaltır.

Microsoft Defender Virüsten Koruma taramasını istemediğiniz öğeler için bir dışlama listesi tanımlayabilirsiniz. Ancak, dışlanan öğeler cihazınızı savunmasız hale getiren tehditler içerebilir. Bu makalede, dışlamaları tanımlarken kaçınmanız gereken bazı yaygın hatalar açıklanmaktadır.

Dışlama listelerinizi tanımlamadan önce [dışlamaları tanımlamaya yönelik Öneriler](configure-exclusions-microsoft-defender-antivirus.md#recommendations-for-defining-exclusions) bölümüne bakın.

## <a name="excluding-certain-trusted-items"></a>Belirli güvenilen öğeleri dışlama

Bazı dosyaların, dosya türlerinin, klasörlerin veya işlemlerin kötü amaçlı olmamasına güvenseniz bile taramanın dışında tutulmaması gerekir.

Aşağıdaki bölümlerde listelenen klasör konumları, dosya uzantıları ve işlemler için dışlamalar tanımlamayın:

- [Klasör konumları](#folder-locations)
- [Dosya uzantıları](#file-extensions)
- [Süreç](#processes)

### <a name="folder-locations"></a>Klasör konumları

> [!IMPORTANT]
> Bazı klasörler, kötü amaçlı dosyaların bırakılacağı klasörler olduğundan taramaların dışında tutulmamalıdır.

Genel olarak, aşağıdaki klasör konumları için dışlama tanımlamayın:

- `%systemdrive%`
- `C:`, `C:\`veya `C:\*`
- `%ProgramFiles%\Java` Veya `C:\Program Files\Java`
- `%ProgramFiles%\Contoso\`, `C:\Program Files\Contoso\`, `%ProgramFiles(x86)%\Contoso\`veya `C:\Program Files (x86)\Contoso\`
- `C:\Temp`, `C:\Temp\`veya `C:\Temp\*`
- `C:\Users\` Veya `C:\Users\*`
- `C:\Users\<UserProfileName>\AppData\Local\Temp\`veya .`C:\Users\<UserProfileName>\AppData\LocalLow\Temp\` **SharePoint için aşağıdaki önemli özel durumları not edin: SharePoint** [dosya düzeyinde virüsten korumayı](https://support.microsoft.com/office/certain-folders-may-have-to-be-excluded-from-antivirus-scanning-when-you-use-file-level-antivirus-software-in-sharepoint-01cbc532-a24e-4bba-8d67-0b1ed733a3d9) **hariç tutun** `C:\Users\ServiceAccount\AppData\Local\Temp` veya `C:\Users\Default\AppData\Local\Temp` kullandığınızda.
- `%Windir%\Prefetch`, `C:\Windows\Prefetch`, `C:\Windows\Prefetch\`veya `C:\Windows\Prefetch\*`
- `%Windir%\System32\Spool` Veya `C:\Windows\System32\Spool`
- `C:\Windows\System32\CatRoot2`
- `%Windir%\Temp`, `C:\Windows\Temp`, `C:\Windows\Temp\`veya `C:\Windows\Temp\*`

#### <a name="linux-and-macos-platforms"></a>Linux ve macOS Platformları

Genel olarak, aşağıdaki klasör konumları için dışlama tanımlamayın:

- `/`
- `/bin` Veya `/sbin`
- `/usr/lib`

### <a name="file-extensions"></a>Dosya uzantıları

> [!IMPORTANT]
> Bazı dosya uzantıları, bir saldırıda kullanılan dosya türleri olabileceğinden dışlanmamalıdır.

Genel olarak, aşağıdaki dosya uzantıları için dışlama tanımlamayın:

- `.7z`
- `.bat`
- `.bin`
- `.cab`
- `.cmd`
- `.com`
- `.cpl`
- `.dll`
- `.exe`
- `.fla`
- `.gif`
- `.gz`
- `.hta`
- `.inf`
- `.java`
- `.jar`
- `.job`
- `.jpeg`
- `.jpg`
- `.js`
- `.ko` Veya `.ko.gz`
- `.msi`
- `.ocx`
- `.png`
- `.ps1`
- `.py`
- `.rar`
- `.reg`
- `.scr`
- `.sys`
- `.tar`
- `.tmp`
- `.url`
- `.vbe`
- `.vbs`
- `.wsf`
- `.zip`

### <a name="processes"></a>Süreç

> [!IMPORTANT]
> Bazı işlemler saldırılar sırasında kullanıldığından dışlanmamalıdır.

Genel olarak, aşağıdaki işlemler için dışlama tanımlamayın:

- `AcroRd32.exe`
- `addinprocess.exe`
- `addinprocess32.exe`
- `addinutil.exe`
- `bash.exe`
- `bginfo.exe`
- `bitsadmin.exe`
- `cdb.exe`
- `csi.exe`
- `dbghost.exe`
- `dbgsvc.exe`
- `dnx.exe`
- `dotnet.exe`
- `excel.exe`
- `fsi.exe`
- `fsiAnyCpu.exe`
- `iexplore.exe`
- `java.exe`
- `kd.exe`
- `lxssmanager.dll`
- `msbuild.exe`
- `mshta.exe`
- `ntkd.exe`
- `ntsd.exe`
- `outlook.exe`
- `psexec.exe`
- `powerpnt.exe`
- `powershell.exe`
- `rcsi.exe`
- `svchost.exe`
- `schtasks.exe`
- `system.management.automation.dll`
- `windbg.exe`
- `winword.exe`
- `wmic.exe`
- `wuauclt.exe`

> [!NOTE]
> , `.jpg`, `.jpeg`gibi `.gif`dosya türlerini hariç tutabilirsiniz veya `.png` ortamınızda güvenlik açıklarını işlemek için katı bir güncelleştirme ilkesine sahip modern, güncel bir yazılım varsa bunu hariç tutabilirsiniz.

#### <a name="linux-and-macos-platforms"></a>Linux ve macOS Platformları

Genel olarak, aşağıdaki işlemler için dışlama tanımlamayın:

- `bash`
- `java`
- `python` Ve `python3`
- `sh`
- `zsh`

## <a name="using-just-the-file-name-in-the-exclusion-list"></a>Dışlama listesindeki yalnızca dosya adını kullanma

Kötü amaçlı yazılım, güvendiğiniz ve taramanın dışında tutmak istediğiniz dosyayla aynı ada sahip olabilir. Bu nedenle, olası kötü amaçlı yazılımları taramanın dışında tutmaktan kaçınmak için, yalnızca dosya adını kullanmak yerine dışlamak istediğiniz dosyanın tam yolunu kullanın. Örneğin, taramanın dışında `Filename.exe` tutmak istiyorsanız, dosyasının tam yolunu kullanın, örneğin `C:\program files\contoso\Filename.exe`.

## <a name="using-a-single-exclusion-list-for-multiple-server-workloads"></a>Birden çok sunucu iş yükü için tek bir dışlama listesi kullanma

Birden çok sunucu iş yükü için dışlamaları tanımlamak için tek bir dışlama listesi kullanmayın. Farklı uygulama veya hizmet iş yükleri için dışlamaları birden çok dışlama listesi olarak bölün. Örneğin, IIS Sunucusu iş yükünüz için dışlama listesi, SQL Server iş yükünüz için dışlama listesinden farklı olmalıdır.

## <a name="using-incorrect-environment-variables-as-wildcards-in-the-file-name-and-folder-path-or-extension-exclusion-lists"></a>Dosya adı ve klasör yolu veya uzantı dışlama listelerinde joker karakter olarak yanlış ortam değişkenlerini kullanma

Microsoft Defender Virüsten Koruma Hizmeti, LocalSystem hesabını kullanarak sistem bağlamında çalışır. Bu, bilgileri kullanıcı ortam değişkeninden değil sistem ortam değişkeninden aldığı anlamına gelir. Dışlama listelerinde ortam değişkenlerinin joker karakter olarak kullanılması, sistem değişkenleriyle ve NT AUTHORITY\SYSTEM hesabı olarak çalışan işlemler için geçerli olanlarla sınırlıdır. Bu nedenle, Microsoft Defender Virüsten Koruma klasör ve işlem dışlamaları eklerken joker karakter olarak kullanıcı ortamı değişkenlerini kullanmayın. [Sistem ortamı değişkenlerinin tam listesi için Sistem ortamı değişkenleri](configure-extension-file-exclusions-microsoft-defender-antivirus.md#system-environment-variables) altındaki tabloya bakın.

Dışlama listelerinde joker karakterleri kullanma hakkında bilgi için bkz. [Dosya adı ve klasör yolu veya uzantı dışlama listelerinde](configure-extension-file-exclusions-microsoft-defender-antivirus.md#use-wildcards-in-the-file-name-and-folder-path-or-extension-exclusion-lists) joker karakterler kullanma.

> [!TIP]
> Diğer platformlar için Antivirüs ile ilgili bilgi arıyorsanız bkz:
> - [MacOS'ta Uç Nokta için Microsoft Defender tercihlerini ayarlayın](mac-preferences.md)
> - [Mac'te Uç Nokta için Microsoft Defender](microsoft-defender-endpoint-mac.md)
> - [Intune için Microsoft Defender için macOS Virüsten Koruma ilke ayarları](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Linux'ta Uç Nokta için Microsoft Defender tercihlerini ayarlayın](linux-preferences.md)
> - [Linux'ta Uç Nokta için Microsoft Defender](microsoft-defender-endpoint-linux.md)
> - [Android özelliklerinde Uç Nokta için Defender’ı yapılandırın](android-configure.md)
> - [iOS özelliklerinde Uç Nokta için Microsoft Defender’ı yapılandırın](ios-configure-features.md)
