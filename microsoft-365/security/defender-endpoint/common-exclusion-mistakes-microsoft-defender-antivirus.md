---
title: Dışlamaları tanımlarken kaçınılması gereken yaygın hatalar
description: Dışlamalar ve taramalar için dışlamalar tanımlarken sık Microsoft Defender Virüsten Koruma kaçının.
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
ms.date: 10/19/2021
ms.collection: M365-security-compliance
ms.openlocfilehash: 73234fd929406da475455baf21fbbf463216c660
ms.sourcegitcommit: 2b9d40e888ff2f2b3385e2a90b50d719bba1e653
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/25/2021
ms.locfileid: "62996991"
---
# <a name="common-mistakes-to-avoid-when-defining-exclusions"></a>Dışlamaları tanımlarken kaçınılması gereken yaygın hatalar

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Taramak istediğiniz öğeler için dışlama listesi Microsoft Defender Virüsten Koruma tanımlayabilirsiniz. Bu tür dışarıda bırakılan öğeler cihazınızı zayıf hale zoracak tehditlere neden olabilir. Bu makalede, dışlamaları tanımlarken kaçınılması gereken bazı yaygın hatalar açıklanmıştır.

Dışlama listelerinizi tanımlamadan önce [dışlamaları Öneriler aşağıdaki seçeneklere bakın](configure-exclusions-microsoft-defender-antivirus.md#recommendations-for-defining-exclusions).

## <a name="excluding-certain-trusted-items"></a>Belirli güvenilen öğeleri dışlama

Bazı dosyalar, dosya türleri, klasörler veya işlemler kötü amaçlı olmayacak şekilde güvense bile tarama dışında tutulmaz.

Aşağıdaki bölümlerde listelenen klasör konumlarında, dosya uzantılarında ve süreçlerde dışlamalar tanımlamayın:
- Klasör konumları
- Dosya uzantıları
- İşlemler

### <a name="folder-locations"></a>Klasör konumları

Genelde aşağıdaki klasör konumları için dışlamalar tanımlamayın:

`%systemdrive%`

`C:`

`C:\`

`C:\*`

`%ProgramFiles%\Java`

`C:\Program Files\Java`

`%ProgramFiles%\Contoso\`

`C:\Program Files\Contoso\`

`%ProgramFiles(x86)%\Contoso\`

`C:\Program Files (x86)\Contoso\`

`C:\Temp`

`C:\Temp\`

`C:\Temp\*`

`C:\Users\`

`C:\Users\*`

`C:\Users\<UserProfileName>\AppData\Local\Temp\`**Şu özel durumu not SharePoint**: `C:\Users\ServiceAccount\AppData\Local\Temp` SharePoint'te dosya düzeyinde [virüsten koruma kullanıyorsanız, hariç SharePoint](https://support.microsoft.com/office/certain-folders-may-have-to-be-excluded-from-antivirus-scanning-when-you-use-file-level-antivirus-software-in-sharepoint-01cbc532-a24e-4bba-8d67-0b1ed733a3d9).

`C:\Users\<UserProfileName>\AppData\LocalLow\Temp\`**Şu özel durumu not SharePoint**: `C:\Users\Default\AppData\Local\Temp` SharePoint'te dosya düzeyinde [virüsten koruma kullanıyorsanız, hariç SharePoint](https://support.microsoft.com/office/certain-folders-may-have-to-be-excluded-from-antivirus-scanning-when-you-use-file-level-antivirus-software-in-sharepoint-01cbc532-a24e-4bba-8d67-0b1ed733a3d9).

`%Windir%\Prefetch`

`C:\Windows\Prefetch`

`C:\Windows\Prefetch\`

`C:\Windows\Prefetch\*`

`%Windir%\System32\Spool`

`C:\Windows\System32\Spool`

`C:\Windows\System32\CatRoot2`
`%Windir%\Temp`

`C:\Windows\Temp`

`C:\Windows\Temp\`

`C:\Windows\Temp\*`

#### <a name="linux-and-macos-platforms"></a>Linux ve macOS Platformları

`/`

`/bin`

`/sbin`

`/usr/lib`


### <a name="file-extensions"></a>Dosya uzantıları

Genelde aşağıdaki dosya uzantıları için dışlamalar tanımlamayın:

`.7z`

`.bat`

`.bin`

`.cab`

`.cmd`

`.com`

`.cpl`

`.dll`

`.exe`

`.fla`

`.gif`

`.gz`

`.hta`

`.inf`

`.java`

`.jar`

`.job`

`.jpeg`

`.jpg`

`.js`

`.ko`

`.ko.gz`

`.msi`

`.ocx`

`.png`

`.ps1`

`.py`

`.rar`

`.reg`

`.scr`

`.sys`

`.tar`

`.tmp`

`.url`

`.vbe`

`.vbs`

`.wsf`

`.zip`

### <a name="processes"></a>İşlemler

Genelde aşağıdaki işlemler için dışlamalar tanımlamayın:

`AcroRd32.exe`

`bitsadmin.exe`

`excel.exe`

`iexplore.exe`

`java.exe`

`outlook.exe`

`psexec.exe`

`powerpnt.exe`

`powershell.exe`

`schtasks.exe`

`svchost.exe`

`wmic.exe`

`winword.exe`

`wuauclt.exe`

`addinprocess.exe`

`addinprocess32.exe`

`addinutil.exe`

`bash.exe`

`bginfo.exe`

`cdb.exe`

`csi.exe`

`dbghost.exe`

`dbgsvc.exe`

`dnx.exe`

`dotnet.exe`

`fsi.exe`

`fsiAnyCpu.exe`

`kd.exe`

`ntkd.exe`

`lxssmanager.dll`

`msbuild.exe`

`mshta.exe`

`ntsd.exe`

`rcsi.exe`

`system.management.automation.dll`

`windbg.exe`

#### <a name="linux-and-macos-platforms"></a>Linux ve macOS Platformları

`bash`

`sh`

`python` ve `python3`

`java`

`zsh`

> [!NOTE]
> , veya `.jpeg``.png` gibi dosya türlerini `.gif``.jpg`dışarıda tutabilirsiniz veya ortamınız güvenlik açıklarını işlemek için sıkı bir güncelleştirme ilkesine sahip modern, güncel bir yazılıma sahipse bunu dışarıda tutabilirsiniz.

## <a name="using-just-the-file-name-in-the-exclusion-list"></a>Dışlama listesinde yalnızca dosya adını kullanma

Kötü amaçlı yazılım, güvenilen ve tarama dışında tutmak istediğiniz dosyayla aynı adıya sahip olabilir. Bu nedenle, olası kötü amaçlı yazılım taramalarını dışlamamak için, yalnızca dosya adını kullanmak yerine, hariç tutmak istediğiniz dosyanın tam yollarından kullanın. Örneğin, taramanın dışında tutmak `Filename.exe` istemiyorsanız, dosyanın tam yolunu, örneğin: `C:\program files\contoso\Filename.exe`kullanın.

## <a name="using-a-single-exclusion-list-for-multiple-server-workloads"></a>Birden çok sunucu iş yükü için tek bir dışlama listesi kullanma

Birden çok sunucu iş yükünün dışlamalarını tanımlamak için tek bir dışlama listesi kullanma. Farklı uygulama veya hizmet iş yükleri için dışlamaları birden çok dışlama listesinde bölün. Örneğin, IIS Server iş yükünün dışlama listesi, iş yükünüz için dışlama SQL Server gerekir.

## <a name="using-incorrect-environment-variables-as-wildcards-in-the-file-name-and-folder-path-or-extension-exclusion-lists"></a>Dosya adı ve klasör yolu veya uzantı dışlama listelerinde joker karakter olarak yanlış ortam değişkenleri kullanma

Microsoft Defender Virüsten Koruma Hizmeti, sistem bağlamında LocalSystem hesabını kullanarak çalışır; bu da, kullanıcı ortam değişkenlerinden değil sistem ortamı değişkeninden bilgi alır. Dışlama listelerinde ortam değişkenlerinin joker karakter olarak kullanımı sistem değişkenleriyle ve NT AUTHORITY\SYSTEM hesabı olarak çalışan işlemler için geçerli olanlar ile sınırlıdır. Bu nedenle, yeni klasör ve işlem dışlamaları eklerken kullanıcı Microsoft Defender Virüsten Koruma değişkenlerini joker karakter olarak kullanmayın. Sistem ortamı [değişkenlerinin tam listesi için](configure-extension-file-exclusions-microsoft-defender-antivirus.md#system-environment-variables) Sistem ortamı değişkenleri altındaki tabloya bakın.

[Dışlama listelerinde joker karakterleri](configure-extension-file-exclusions-microsoft-defender-antivirus.md#use-wildcards-in-the-file-name-and-folder-path-or-extension-exclusion-lists) kullanma hakkında bilgi için bkz. Dosya adı ve klasör yolu veya uzantı dışlama listelerinde joker karakter kullanma.
