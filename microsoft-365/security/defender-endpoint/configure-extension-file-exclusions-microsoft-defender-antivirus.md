---
title: Uzantı, ad veya konuma dayalı olarak dışlamaları yapılandırma ve doğrulama
description: Dosyaları, Microsoft Defender Virüsten Koruma uzantısına, dosya adına veya konumlarına göre taramalar dışında tutabilirsiniz.
keywords: dışlamalar, dosyalar, uzantı, dosya türü, klasör adı, dosya adı, taramalar
ms.prod: m365-security
ms.technology: mde
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.topic: article
ms.custom: nextgen
ms.reviewer: ''
manager: dansimp
ms.date: 12/17/2021
ms.collection: M365-security-compliance
ms.openlocfilehash: 616dde760ab24d12efe5c4621a1ee1829cb1798f
ms.sourcegitcommit: 59b1b0abfde30a8f2d8210b696aac3dc9183544e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/18/2021
ms.locfileid: "63019108"
---
# <a name="configure-and-validate-exclusions-based-on-file-extension-and-folder-location"></a>Dosya uzantısını ve klasör konumunu temel alarak dışlamaları yapılandırma ve doğrulama

**Aşağıdakiler için geçerlidir:**

- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Microsoft Defender Virüsten Koruma

Zamanlanmış taramalar Microsoft Defender Virüsten Koruma isteğe bağlı taramalar [ve her](schedule-antivirus-scans.md) zaman [açık, gerçek](run-scan-microsoft-defender-antivirus.md) zamanlı koruma ve izleme için geçerli olan [dışlamalar tanımlayabilirsiniz](configure-real-time-protection-microsoft-defender-antivirus.md). **Genel olarak, dışlamaları uygulama gerekmedilir**. Dışlamaları uygulama gerekirse, birkaç farklı türde seçim kullanabilirsiniz:

- Dosya uzantılarına ve klasör konumlarına dayalı dışlamalar (bu makalede açıklanmıştır)
- [İşlemler tarafından açılan dosyaların dışlamaları](configure-process-opened-file-exclusions-microsoft-defender-antivirus.md)

> [!IMPORTANT]
> Microsoft Defender Virüsten Koruma dışlamalar; [uç noktada algılama ve yanıtlama (EDR)](/microsoft-365/security/defender-endpoint/overview-endpoint-detection-response), saldırı yüzeyini azaltma [(ASR)](/microsoft-365/security/defender-endpoint/attack-surface-reduction) kuralları ve denetimli klasör erişimi gibi diğer Uç Nokta özellikleri için Microsoft Defender için geçerli [değildir](/microsoft-365/security/defender-endpoint/controlled-folders). Bu makalede açıklanan yöntemleri kullanarak dışlayın dosyalar yine de uyarı uyarılarını EDR algılamaları tetikler.
> Dosyaları genel olarak dışlamak için, bunları Uç nokta özel göstergeleri için Microsoft [Defender'a ekleyin](/microsoft-365/security/defender-endpoint/manage-indicators).

## <a name="before-you-begin"></a>Başlamadan önce...

[Dışlama Öneriler tanımlamadan önce dışlamaları](configure-exclusions-microsoft-defender-antivirus.md) tanımlama hakkında daha fazla bilgi için bkz.

## <a name="exclusion-lists"></a>Dışlama listeleri

Bazı dosyaları taramaların dışında Microsoft Defender Virüsten Koruma, dışlama listelerinizi değiştirirsiniz. Microsoft Defender Virüsten Koruma, bilinen işletim sistemi davranışlarına ve kurumsal yönetim, veritabanı yönetimi ve diğer kurumsal senaryo ve durumlarda kullanılanlar gibi tipik yönetim dosyalarına dayalı birçok otomatik dışlama içerir.

> [!NOTE]
> Dışlamalar, İstenmeyen Olabilecek Uygulamalar (PUA) algılamaları için de geçerlidir.
>
> Otomatik dışlamalar yalnızca dışlamalar Windows Server 2016 sonrası için geçerlidir. Bu dışlamalar Windows Güvenliği PowerShell'de görünmez.

Aşağıdaki tabloda, dosya uzantısına ve klasör konumuna bağlı olarak bazı dışlama örnekleri listerilmiştir. 
<br/><br/>

|Dışlama|Örnekler|Dışlama listesi|
|---|---|---|
|Belirli bir uzantıya sahip herhangi bir dosya|Belirtilen uzantıya sahip tüm dosyalar, makinenin herhangi bir yerinde. <p> Geçerli söz dizimi: `.test` ve `test`|Uzantı dışlamaları|
|Belirli bir klasörün altındaki herhangi bir dosya|Klasörün altındaki tüm `c:\test\sample` dosyalar|Dosya ve klasör dışlamaları|
|Belirli bir klasördeki belirli bir dosya|Yalnızca dosya `c:\sample\sample.test`|Dosya ve klasör dışlamaları|
|Belirli bir işlem|Yürütülebilir dosya `c:\test\process.exe`|Dosya ve klasör dışlamaları|

## <a name="characteristics-of-exclusion-lists"></a>Dışlama listelerinin özellikleri

- Alt klasör bir yeniden dosya noktası olmadığı sürece, klasör dışlamaları bu klasörün altındaki tüm dosyalara ve klasörlere uygulanır. Yeniden nokta alt klasörleri ayrı ayrı hariç tutulmalıdır.
- Dosya uzantıları, bir yol veya klasör tanımlanmamışsa, tanımlı uzantıya sahip herhangi bir dosya adına uygulanır.

## <a name="important-notes-about-exclusions-based-on-file-extensions-and-folder-locations"></a>Dosya uzantılarına ve klasör konumlarına dayalı dışlamalar hakkında önemli notlar

- Yıldız işareti (\*) gibi joker karakterler kullanmak dışlama kurallarının yorumlanma şeklinde değişiklik sağlar. Joker [karakterlerin nasıl olduğuyla ilgili önemli bilgiler](#use-wildcards-in-the-file-name-and-folder-path-or-extension-exclusion-lists) için, Dosya adı ve klasör yolu veya uzantı dışlama listelerinde joker karakter kullanma bölümüne bakın.

- Eşlenmiş ağ sürücülerini dışlamama. Gerçek ağ yolunu belirtin.

- Dışlama hizmeti başladıktan ve dışlama listesine Microsoft Defender Virüsten Koruma yeniden eklenenler olan klasörler dahil edilir. Yeni yeniden başlatma noktalarının geçerli bir dışlama hedefi olarak tanınması için hizmeti yeniden başlatın (Windows yeniden başlatarak).

- Dışlamalar [zamanlanmış taramalar, isteğe](scheduled-catch-up-scans-microsoft-defender-antivirus.md) bağlı [taramalar](run-scan-microsoft-defender-antivirus.md) ve [gerçek](configure-real-time-protection-microsoft-defender-antivirus.md) zamanlı koruma için geçerlidir, ancak Uç Nokta için Defender'da geçerli değildir. Uç nokta için Defender'da dışlamalar tanımlamak için özel [göstergeleri kullanın](manage-indicators.md).

- Varsayılan olarak, listelerde yapılan yerel değişiklikler (PowerShell ve WMI ile yapılan değişiklikler dahil olmak üzere yönetici ayrıcalıklarına sahip kullanıcılar tarafından), Grup İlkesi, Yapılandırma Yöneticisi veya Intune tarafından tanımlandığı (ve dağıtıldı) listelerle birleştirilir. Grup İlkesi listeleri çakışma olduğunda öncelik alır. Ek olarak, Grup İlkesi ile yapılan dışlama listesi değişiklikleri de Windows Güvenliği [görünür](microsoft-defender-security-center-antivirus.md).

- Yerel değişikliklerin yönetilen dağıtım ayarlarını geçersiz k olmasına izin vermek için, [yerel ve genel tanımlı dışlama listelerinin nasıl birleştiril olduğunu yapılandırabilirsiniz](configure-local-policy-overrides-microsoft-defender-antivirus.md#merge-lists).

## <a name="configure-the-list-of-exclusions-based-on-folder-name-or-file-extension"></a>Klasör adına veya dosya uzantısına göre dışlama listesini yapılandırma

Dışlamaları tanımlamak için çeşitli yöntemlerden birini Microsoft Defender Virüsten Koruma.

### <a name="use-intune-to-configure-file-name-folder-or-file-extension-exclusions"></a>Dosya adı, klasör veya dosya uzantısı dışlamalarını yapılandırmak için Intune kullanma

Aşağıdaki makalelere bakın:

- [Mobil cihazda cihaz kısıtlama ayarlarını Microsoft Intune](/intune/device-restrictions-configure)
- [Microsoft Defender Virüsten Koruma Intune'da Windows 10 kısıtlama ayarlarını değiştirme](/intune/device-restrictions-windows-10#microsoft-defender-antivirus)

### <a name="use-configuration-manager-to-configure-file-name-folder-or-file-extension-exclusions"></a>Dosya adı, klasör veya dosya uzantısı dışlamalarını yapılandırmak için Yapılandırma Yöneticisi'ni kullanma

Bkz[. Kötü amaçlı yazılım önleme ilkeleri oluşturma ve dağıtma:](/configmgr/protect/deploy-use/endpoint-antimalware-policies#exclusion-settings) Kimlik bilgilerini yapılandırmayla ilgili ayrıntılar için Microsoft Endpoint Manager ayarları.

### <a name="use-group-policy-to-configure-folder-or-file-extension-exclusions"></a>Klasör veya dosya uzantısı dışlamalarını yapılandırmak için Grup İlkesi kullanma

> [!NOTE]
> Dosya için tam yol belirtirsiniz, yalnızca o dosya dışlar. Dışlamada bir klasör tanımlanmışsa, o klasörün altındaki tüm dosyalar ve alt yönler dışlar.

1. Grup İlkesi yönetim bilgisayarınızda Grup İlkesi Yönetim [Konsolu'nu](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)) açın, yapılandırmak istediğiniz Grup İlkesi Nesnesine sağ tıklayın ve Düzenle'yi **seçin**.

2. Grup İlkesi **Yönetim Düzenleyicisi'nde Bilgisayar** **yapılandırması'ne gidin ve** Yönetim **şablonları'ı seçin**.

3. Dışlamalar'da **bileşenleri Windows için** \> **Microsoft Defender Virüsten Koruma** \> **genişletin**.

4. Düzenlemek için **Yol Dışlamaları** ayarını açın ve dışlamalarınızı ekleyin.
    1. Seçeneği Etkin olarak **ayarlayın**.
    2. Seçenekler bölümünün **altında** Göster'i **seçin**.
    3. Her klasörü, Değer adı sütununu altında kendi **satırına** belirtin.
    4. Dosya belirtirken, dosyanın sürücü harfi, klasör yolu, dosya adı ve uzantıyla birlikte tam bir yol girmeye emin olun. 
    5. Değer **sütununa 0** **girin.**

5. **Tamam**'ı seçin.

6. Düzenlemek için **Uzantı Dışlamaları** ayarını açın ve dışlamalarınızı ekleyin.
    1. Seçeneği Etkin olarak **ayarlayın**.
    2. Seçenekler bölümünün **altında** Göster'i **seçin**.
    3. Her dosya uzantısını, Değer adı sütununu altına kendi **satırına** girin.
    4. Değer **sütununa 0** **girin.**

7. **Tamam**'ı seçin.

<a id="ps"></a>

### <a name="use-powershell-cmdlets-to-configure-file-name-folder-or-file-extension-exclusions"></a>Dosya adı, klasör veya dosya uzantısı dışlamalarını yapılandırmak için PowerShell cmdlet'lerini kullanma

Uzantıya, konuma veya dosya adına dayalı olarak dosyaların dışlamalarını eklemek veya kaldırmak için PowerShell kullanmak için üç cmdlet'in ve uygun dışlama listesi parametresinin birleşimi gerekir. Cmdlet'lerin hepsi [Defender modülündedir](/powershell/module/defender/).

Cmdlet'lerin biçimi aşağıdaki gibidir:

```PowerShell
<cmdlet> -<exclusion list> "<item>"
```

Aşağıdaki tabloda, PowerShell cmdlet'inin `<cmdlet>` bir bölümünde kullanabileceğiniz cmdlet'ler listelemektedir:

<br/><br/>

|Yapılandırma eylemi|PowerShell cmdlet'i|
|:---|:---|
|Listeyi oluşturma veya üzerine yazma|`Set-MpPreference`|
|Listeye ekleme|`Add-MpPreference`|
|Listeden öğe kaldırma|`Remove-MpPreference`|

Aşağıdaki tabloda, PowerShell cmdlet'inin `<exclusion list>` bölümünde kullanabileceğiniz değerler listelemektedir:

<br/><br/>

|Dışlama türü|PowerShell parametresi|
|---|---|
|Belirtilen dosya uzantısına sahip tüm dosyalar|`-ExclusionExtension`|
|Klasör altındaki tüm dosyalar (alt yönler içinde dosyalar dahil) veya belirli bir dosya|`-ExclusionPath`|

> [!IMPORTANT]
> with veya ile bir liste oluşturduysanız `Set-MpPreference` `Add-MpPreference`, `Set-MpPreference` cmdlet'i yeniden kullanarak varolan listenin üzerine yazabilirsiniz.

Örneğin, aşağıdaki kod parçacığı dosya uzantısına Microsoft Defender Virüsten Koruma herhangi bir dosyayı hariç tutmak için bu kod parçacığını taramalara neden `.test` olabilir:

```PowerShell
Add-MpPreference -ExclusionExtension ".test"
```

> [!TIP]
> Daha fazla bilgi için bkz[. PowerShell cmdlet'lerini kullanarak PowerShell cmdlet'lerini](use-powershell-cmdlets-microsoft-defender-antivirus.md) yapılandırma ve Microsoft Defender Virüsten Koruma [Defender Virüsten Koruma cmdlet'lerini yapılandırma](/powershell/module/defender/).

### <a name="use-windows-management-instrumentation-wmi-to-configure-file-name-folder-or-file-extension-exclusions"></a>Dosya Windows, klasör veya dosya uzantısı dışlamalarını yapılandırmak için Yönetim Aracı'Windows (WMI) kullanma

Aşağıdaki [özellikler için sınıf sınıfınıza göre Ayarla, MSFT_MpPreference](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) ve Kaldır yöntemlerini kullanın:

```WMI
ExclusionExtension
ExclusionPath
```

**Ayarla,** **Ekle ve** Kaldır **komutlarını kullanmak**, PowerShell'daki benzerleridir: `Set-MpPreference`, ve `Add-MpPreference``Remove-MpPreference`.

> [!TIP]
> Daha fazla bilgi için [WMIv2 API'lerini Windows Defender bkz](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal).

<a id="man-tools"></a>

### <a name="use-the-windows-security-app-to-configure-file-name-folder-or-file-extension-exclusions"></a>Dosya adı, Windows Güvenliği veya dosya uzantısı dışlamalarını yapılandırmak için Windows Güvenliği uygulamasını kullanma

Yönergeler [için bkz. Windows Güvenliği Dışlamalar](microsoft-defender-security-center-antivirus.md) ekleme.

<a id="wildcards"></a>

## <a name="use-wildcards-in-the-file-name-and-folder-path-or-extension-exclusion-lists"></a>Dosya adı ve klasör yolu veya uzantı dışlama listelerinde joker karakter kullanma

Dosya adı veya klasör `*``?`yolu dışlama listesinde öğe tanımlarken joker karakter olarak yıldız , soru işareti veya ortam değişkenleri (`%ALLUSERSPROFILE%`örneğin) kullanabilirsiniz. Bu joker karakterlerin yorumlanması, diğer uygulama ve dillerdeki normal kullanımlarından farklıdır. Sınırlamaları anlamak için bu bölümü okuduğundan emin olun.

> [!IMPORTANT]
> Bu joker karakterler için önemli sınırlamalar ve kullanım senaryoları vardır:
>
> - Ortam değişken kullanımı makine değişkenleriyle ve NT AUTHORITY\SYSTEM hesabı olarak çalışan işlemler için geçerli olanlar ile sınırlıdır.
> - Sürücü harfi yerine joker karakter kullanılamaz.
> - Klasör dışlamada `*` bir yıldız işareti, tek bir klasör için geçerli durumdadır. Belirtilmemiş adlarla `\*\` birden çok iç içe klasör göstermek için birden çok örnek kullanın.
> - Şu anda Microsoft Endpoint Configuration Manager karakterleri (veya gibi) desteklemez `*` `?`.
    
Aşağıdaki tabloda joker karakterlerin nasıl kullanıl kullandığı açık olmakta ve bazı örnekler verilmiştir.

<br/><br/>

|Joker karakter|Örnekler|
|---|---|
|`*` (yıldız işareti) <p> Dosya **adı ve dosya uzantısı eklemelerde**, yıldız işareti istediğiniz sayıda karakterin yerini almaktadır ve yalnızca bağımsız değişkende tanımlanan son klasördeki dosyalara uygulanır. <p> Klasör **dışlamalarında**, yıldız işareti tek bir klasörün yerini almaktadır. Birden çok `*` iç içe klasörü göstermek için `\` eğik çizgilerle birden çok klasör kullanın. Joker karakterli ve adlandırılmış klasörlerin sayısı eşleştirildikten sonra, tüm alt klasörler de dahil edilir.|`C:\MyData\*.txt` şunları içerir: `C:\MyData\notes.txt` <p> `C:\somepath\*\Data` tüm dosyaları, `C:\somepath\Archives\Data` alt klasörlerini ve `C:\somepath\Authorized\Data` onun alt klasörlerini içerir <p> `C:\Serv\*\*\Backup` tüm dosyaları, `C:\Serv\Primary\Denied\Backup` alt klasörlerini ve `C:\Serv\Secondary\Allowed\Backup` alt klasörlerini içerir|
|`?` (soru işareti)  <p> Dosya **adı ve dosya uzantısı eklemelerde**, soru işareti tek bir karakterin yerini alır ve yalnızca bağımsız değişkende tanımlanan son klasördeki dosyalara uygulanır. <p> Klasör **dışlamalarında**, soru işareti klasör adı içinde tek bir karakterin yerini almaktadır. Joker karakterli ve adlandırılmış klasörlerin sayısı eşleştirildikten sonra, tüm alt klasörler de dahil edilir.|`C:\MyData\my?.zip` şunları içerir: `C:\MyData\my1.zip` <p> `C:\somepath\?\Data` tüm dosyaları ve `C:\somepath\P\Data` alt klasörlerini içerir  <p> `C:\somepath\test0?\Data` alt klasörleri içinde herhangi `C:\somepath\test01\Data` bir dosyayı içerebilir|
|Ortam değişkenleri <p> Dışlama değerlendirilirken tanımlı değişken yol olarak doldurulur.|`%ALLUSERSPROFILE%\CustomLogFiles` içerebilir `C:\ProgramData\CustomLogFiles\Folder1\file1.txt`|

> [!IMPORTANT]
> Dosya dışlama bağımsız değişkenlerini klasör dışlama bağımsız değişkeniyle karıştırırsanız, kurallar eşleşen klasördeki dosya bağımsız değişkeni eşleşmesinde durur ve alt klasörlerde dosya eşleşmelerini aramaz.
>
> Örneğin, klasörlerde ve kural bağımsız değişkenlerini kullanarak "tarih" `c:\data\final\marked` `c:\data\review\marked` ile başlamaya başlanan tüm dosyaları hariç tutabilirsiniz `c:\data\*\marked\date*`.
>
> Bununla birlikte, bu bağımsız değişken veya altındaki alt klasörlerde yer alan hiçbir dosyayla eşleşmez `c:\data\final\marked` `c:\data\review\marked`.

<a id="review"></a>

### <a name="system-environment-variables"></a>Sistem ortamı değişkenleri

Aşağıdaki tabloda, sistem hesabı ortamı değişkenlerini listeler ve açıklar.

<br/><br/>

|Bu sistem ortamı değişkeni...|Buna yönlendirmeler|
|---|---|
|`%APPDATA%`|`C:\Users\UserName.DomainName\AppData\Roaming`|
|`%APPDATA%\Microsoft\Internet Explorer\Quick Launch`|`C:\Windows\System32\config\systemprofile\AppData\Roaming\Microsoft\Internet Explorer\Quick Launch`|
|`%APPDATA%\Microsoft\Windows\Start Menu`|`C:\Windows\System32\config\systemprofile\AppData\Roaming\Microsoft\Windows\Start Menu`|
|`%APPDATA%\Microsoft\Windows\Start Menu\Programs`|`C:\Windows\System32\config\systemprofile\AppData\Roaming\Microsoft\Windows\Start Menu\Programs`|
|`%LOCALAPPDATA%`|`C:\Windows\System32\config\systemprofile\AppData\Local`|
|`%ProgramData%`|`C:\ProgramData`|
|`%ProgramFiles%`|`C:\Program Files`|
|`%ProgramFiles%\Common Files`|`C:\Program Files\Common Files`|
|`%ProgramFiles%\Windows Sidebar\Gadgets`|`C:\Program Files\Windows Sidebar\Gadgets`|
|`%ProgramFiles%\Common Files`|`C:\Program Files\Common Files`|
|`%ProgramFiles(x86)%`|`C:\Program Files (x86)`|
|`%ProgramFiles(x86)%\Common Files`|`C:\Program Files (x86)\Common Files`|
|`%SystemDrive%`|`C:`|
|`%SystemDrive%\Program Files`|`C:\Program Files`|
|`%SystemDrive%\Program Files (x86)`|`C:\Program Files (x86)`|
|`%SystemDrive%\Users`|`C:\Users`|
|`%SystemDrive%\Users\Public`|`C:\Users\Public`|
|`%SystemRoot%`|`C:\Windows`|
|`%windir%`|`C:\Windows`|
|`%windir%\Fonts`|`C:\Windows\Fonts`|
|`%windir%\Resources`|`C:\Windows\Resources`|
|`%windir%\resources\0409`|`C:\Windows\resources\0409`|
|`%windir%\system32`|`C:\Windows\System32`|
|`%ALLUSERSPROFILE%`|`C:\ProgramData`|
|`%ALLUSERSPROFILE%\Application Data`|`C:\ProgramData\Application Data`|
|`%ALLUSERSPROFILE%\Documents`|`C:\ProgramData\Documents`|
|`%ALLUSERSPROFILE%\Documents\My Music\Sample Music`|`C:\ProgramData\Documents\My Music\Sample Music`|
|`%ALLUSERSPROFILE%\Documents\My Music`|`C:\ProgramData\Documents\My Music`|
|`%ALLUSERSPROFILE%\Documents\My Pictures`|`C:\ProgramData\Documents\My Pictures`|
|`%ALLUSERSPROFILE%\Documents\My Pictures\Sample Pictures`|`C:\ProgramData\Documents\My Pictures\Sample Pictures`|
|`%ALLUSERSPROFILE%\Documents\My Videos`|`C:\ProgramData\Documents\My Videos`|
|`%ALLUSERSPROFILE%\Microsoft\Windows\DeviceMetadataStore`|`C:\ProgramData\Microsoft\Windows\DeviceMetadataStore`|
|`%ALLUSERSPROFILE%\Microsoft\Windows\GameExplorer`|`C:\ProgramData\Microsoft\Windows\GameExplorer`|
|`%ALLUSERSPROFILE%\Microsoft\Windows\Ringtones`|`C:\ProgramData\Microsoft\Windows\Ringtones`|
|`%ALLUSERSPROFILE%\Microsoft\Windows\Start Menu`|`C:\ProgramData\Microsoft\Windows\Start Menu`|
|`%ALLUSERSPROFILE%\Microsoft\Windows\Start Menu\Programs`|`C:\ProgramData\Microsoft\Windows\Start Menu\Programs`|
|`%ALLUSERSPROFILE%\Microsoft\Windows\Start Menu\Programs\Administrative Tools`|`C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Administrative Tools`|
|`%ALLUSERSPROFILE%\Microsoft\Windows\Start Menu\Programs\StartUp`|`C:\ProgramData\Microsoft\Windows\Start Menu\Programs\StartUp`|
|`%ALLUSERSPROFILE%\Microsoft\Windows\Templates`|`C:\ProgramData\Microsoft\Windows\Templates`|
|`%ALLUSERSPROFILE%\Start Menu`|`C:\ProgramData\Start Menu`|
|`%ALLUSERSPROFILE%\Start Menu\Programs`| `C:\ProgramData\Start Menu\Programs`|
|`%ALLUSERSPROFILE%\Start Menu\Programs\Administrative Tools`|`C:\ProgramData\Start Menu\Programs\Administrative Tools`|
|`%ALLUSERSPROFILE%\Templates`|`C:\ProgramData\Templates`|
|`%LOCALAPPDATA%\Microsoft\Windows\ConnectedSearch\Templates`|`C:\Windows\System32\config\systemprofile\AppData\Local\Microsoft\Windows\ConnectedSearch\Templates`|
|`%LOCALAPPDATA%\Microsoft\Windows\History`|`C:\Windows\System32\config\systemprofile\AppData\Local\Microsoft\Windows\History`|
|`%PUBLIC%`|`C:\Users\Public`|
|`%PUBLIC%\AccountPictures`|`C:\Users\Public\AccountPictures`|
|`%PUBLIC%\Desktop`|`C:\Users\Public\Desktop`|
|`%PUBLIC%\Documents`|`C:\Users\Public\Documents`|
|`%PUBLIC%\Downloads`|`C:\Users\Public\Downloads`|
|`%PUBLIC%\Music\Sample Music`|`C:\Users\Public\Music\Sample Music`|
|`%PUBLIC%\Music\Sample Playlists`|`C:\Users\Public\Music\Sample Playlists`|
|`%PUBLIC%\Pictures\Sample Pictures`|`C:\Users\Public\Pictures\Sample Pictures`|
|`%PUBLIC%\RecordedTV.library-ms`|`C:\Users\Public\RecordedTV.library-ms`|
|`%PUBLIC%\Videos`|`C:\Users\Public\Videos`|
|`%PUBLIC%\Videos\Sample Videos`|`C:\Users\Public\Videos\Sample Videos`|
|`%USERPROFILE%`|`C:\Users\UserName`|
|`%USERPROFILE%\AppData\Local`|`C:\Users\UserName\AppData\Local`|
|`%USERPROFILE%\AppData\LocalLow`|`C:\Users\UserName\AppData\LocalLow`|
|`%USERPROFILE%\AppData\Roaming`|`C:\Users\UserName\AppData\Roaming`|

## <a name="review-the-list-of-exclusions"></a>Dışlama listesini gözden geçirme

Aşağıdaki yöntemlerden birini kullanarak dışlama listesinde öğeleri tutabilirsiniz:

- [Intune](/intune/deploy-use/help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune)
- [Microsoft Uç Noktası Yapılandırma Yöneticisi](/configmgr/protect/deploy-use/endpoint-antimalware-policies)
- MpCmdRun
- PowerShell
- [Windows Güvenliği uygulaması](microsoft-defender-security-center-antivirus.md)

> [!IMPORTANT]
> Grup İlkesi ile yapılan dışlama **listesi değişiklikleri,** grup ilkesi uygulamasındaki [Windows Güvenliği görünür](microsoft-defender-security-center-antivirus.md).
>
> Grup İlkesi Windows Güvenliği **yapılan değişiklikler Grup İlkesi** listelerinde gösterlanmaz.

PowerShell kullanıyorsanız, listeyi iki şekilde geri aekleyebilirsiniz:

- Tüm kullanıcı tercihlerinin Microsoft Defender Virüsten Koruma alın. Her liste ayrı satırlarda görüntülenir, ancak liste içindeki öğeler aynı satırda bir araya eklenir.
- Tüm tercihlerin durumunu bir değişkene yazın ve yalnızca ilgilendiğiniz listeyi aramak için bu değişkeni kullanın. Kullanım her `Add-MpPreference` yeni satıra yazılır.

### <a name="validate-the-exclusion-list-by-using-mpcmdrun"></a>MpCmdRun kullanarak dışlama listesini doğrulama

Özel kullanım çizgi aracıyla [dışlamaları mpcmdrun.exe](./command-line-arguments-microsoft-defender-antivirus.md), aşağıdaki komutu kullanın:

```console
Start, CMD (Run as admin)
cd "%programdata%\microsoft\windows defender\platform"
cd 4.18.2111-5.0 (Where 4.18.2111-5.0 is this month's Microsoft Defender Antivirus "Platform Update".)
MpCmdRun.exe -CheckExclusion -path <path>
```

> [!NOTE]
> MpCmdRun ile özel durumların denetlenması için Microsoft Defender Virüsten Koruma CAMP sürüm 4.18.2111-5.0 (Aralık 2021'de yayınlandı) ve sonraki sürümler gerekir.

### <a name="review-the-list-of-exclusions-alongside-all-other-microsoft-defender-antivirus-preferences-by-using-powershell"></a>PowerShell kullanarak diğer tüm dışlamalar ve diğer Microsoft Defender Virüsten Koruma dışlamalar listesini gözden geçirme

Aşağıdaki cmdlet'i kullanın:

```PowerShell
Get-MpPreference
```

Aşağıdaki örnekte, listede yer alan öğeler `ExclusionExtension` vurgulanır:

:::image type="content" source="../../media/wdav-powershell-get-exclusions-variable.png" alt-text="Get-MpPreference için PowerShell çıkışı.":::

Daha fazla bilgi için bkz[. PowerShell cmdlet'lerini kullanarak PowerShell cmdlet'lerini](use-powershell-cmdlets-microsoft-defender-antivirus.md) yapılandırma ve Microsoft Defender Virüsten Koruma [Defender Virüsten Koruma cmdlet'lerini yapılandırma](/powershell/module/defender/).

### <a name="retrieve-a-specific-exclusions-list-by-using-powershell"></a>PowerShell kullanarak belirli bir dışlamalar listesini alma

Aşağıdaki kod parçacığını kullanın (her satırı ayrı bir komut olarak girin); **WDAVprefs yerine** değişkeni isim etmek istediğiniz etiketle değiştirin:

```PowerShell
$WDAVprefs = Get-MpPreference
$WDAVprefs.ExclusionExtension
$WDAVprefs.ExclusionPath
```

Aşağıdaki örnekte, cmdlet'in her kullanımı için liste yeni satırlara `Add-MpPreference` ayrılır:

:::image type="content" source="../../media/wdav-powershell-get-exclusions-variable.png" alt-text="Yalnızca dışlama listesinde girdileri gösteren PowerShell çıkışı.":::

Daha fazla bilgi için bkz[. PowerShell cmdlet'lerini kullanarak PowerShell cmdlet'lerini](use-powershell-cmdlets-microsoft-defender-antivirus.md) yapılandırma ve Microsoft Defender Virüsten Koruma [Defender Virüsten Koruma cmdlet'lerini yapılandırma](/powershell/module/defender/).

<a id="validate"></a>

## <a name="validate-exclusions-lists-with-the-eicar-test-file"></a>EICAR test dosyasıyla dışlama listelerini doğrulama

Dışlama listenizin çalıştığını doğrulamak için PowerShell'i `Invoke-WebRequest` cmdlet veya .NET WebClient sınıfıyla birlikte kullanarak test dosyasını indirebilirsiniz.

Aşağıdaki PowerShell parçacığında, dışlama `test.txt` kurallarınıza uygun bir dosyayla değiştirin. Örneğin, uzantıyı dışladıysanız `.testing` ile değiştirin `test.txt` `test.testing`. Bir yolu test ediyorsanız, cmdlet'i bu yol içinde çalıştırmayı sağlar.

```PowerShell
Invoke-WebRequest "http://www.eicar.org/download/eicar.com.txt" -OutFile "test.txt"
```

Bir Microsoft Defender Virüsten Koruma kötü amaçlı yazılım raporlarsa kural çalışmıyor olur. Kötü amaçlı yazılım raporu yoksa ve indirilen dosya varsa, dışlama çalışıyor olur. İçeriğin [EICAR test](http://www.eicar.org/86-0-Intended-use.html) dosyası web sitesinde açıklananla aynı olduğunu onaylamak için dosyayı açabilirsiniz.

Test dosyasını indirmek için .NET WebClient `Invoke-WebRequest` sınıfını çağıran aşağıdaki PowerShell kodunu (cmdlet'iyle olduğu gibi) kullanabilir ve `c:\test.txt` geçerli olan kurala uygun bir dosyayla değiştirebilirsiniz:

```PowerShell
$client = new-object System.Net.WebClient
$client.DownloadFile("http://www.eicar.org/download/eicar.com.txt","c:\test.txt")
```

İnternet erişiminiz yoksa, EICAR dizesini aşağıdaki PowerShell komutuyla yeni bir metin dosyasına yazarak kendi EICAR test dosyanızı oluşturabilirsiniz:

```PowerShell
[io.file]::WriteAllText("test.txt",'X5O!P%@AP[4\PZX54(P^)7CC)7}$EICAR-STANDARD-ANTIVIRUS-TEST-FILE!$H+H*')
```

Ayrıca, dizeyi boş bir metin dosyasına kopyalayıp dosya adıyla veya hariç tutmak istediğiniz klasöre kaydetmeyi bırakabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Taramalarda dışlamaları yapılandırma Microsoft Defender Virüsten Koruma doğrulama](configure-exclusions-microsoft-defender-antivirus.md)
- [İşlemler tarafından açılan dosyalar için dışlamaları yapılandırma ve doğrulama](configure-process-opened-file-exclusions-microsoft-defender-antivirus.md)
- [Windows Server'da Microsoft Defender Virüsten Koruma dışlamaları yapılandırma](configure-server-exclusions-microsoft-defender-antivirus.md)
- [Dışlamaları tanımlarken kaçınılması gereken yaygın hatalar](common-exclusion-mistakes-microsoft-defender-antivirus.md)
