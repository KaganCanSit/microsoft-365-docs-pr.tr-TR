---
title: Uzantı, ad veya konuma göre dışlamaları yapılandırma ve doğrulama
description: Dosyaları, dosya uzantılarına, dosya adlarına veya konumlarına göre Microsoft Defender Virüsten Koruma taramalarının dışında tutun.
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
ms.collection: M365-security-compliance
ms.openlocfilehash: 7b1614738b17d7f3cf78a6bfabb84f85196d42ff
ms.sourcegitcommit: 35f167725bec5fd4fe131781a53d96b060cf232d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/03/2022
ms.locfileid: "65873258"
---
# <a name="configure-and-validate-exclusions-based-on-file-extension-and-folder-location"></a>Dosya uzantısına ve klasör konumuna göre dışlamaları yapılandırma ve doğrulama

**Şunlar için geçerlidir:**

- [Uç Nokta için Microsoft Defender Planı 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Microsoft Defender Virüsten Koruma

**Platform**
- Windows

[Zamanlanmış taramalar](schedule-antivirus-scans.md), [isteğe bağlı](run-scan-microsoft-defender-antivirus.md) taramalar ve [her zaman açık, gerçek zamanlı koruma ve izleme](configure-real-time-protection-microsoft-defender-antivirus.md) için geçerli olan Microsoft Defender Virüsten Koruma için dışlamalar tanımlayabilirsiniz. **Genel olarak, dışlamaları uygulamanız gerekmez**. Dışlamaları uygulamanız gerekiyorsa, çeşitli türlerden birini seçebilirsiniz:

- Dosya uzantılarına ve klasör konumlarına dayalı dışlamalar (bu makalede açıklanmıştır)
- [İşlemler tarafından açılan dosyalar için dışlamalar](configure-process-opened-file-exclusions-microsoft-defender-antivirus.md)

> [!IMPORTANT]
> Microsoft Defender Virüsten Koruma dışlamalar[, saldırı yüzeyi azaltma (ASR) kuralları](/microsoft-365/security/defender-endpoint/attack-surface-reduction) ve [denetimli klasör erişimi](/microsoft-365/security/defender-endpoint/controlled-folders) gibi diğer Uç Nokta için Microsoft Defender özellikleri için geçerli değildir. Bu makalede açıklanan yöntemleri kullanarak dışladığınız dosyalar yine de EDR uyarıları ve diğer algılamaları tetikleyebilir.
> Dosyaları geniş kapsamlı bir şekilde dışlamak için bunları Uç Nokta için Microsoft Defender [özel göstergelerine](/microsoft-365/security/defender-endpoint/manage-indicators) ekleyin.

## <a name="before-you-begin"></a>Başlamadan önce

[Dışlama listelerinizi tanımlamadan önce dışlamaları tanımlamak için](configure-exclusions-microsoft-defender-antivirus.md) bkz. Öneriler.

## <a name="exclusion-lists"></a>Dışlama listeleri

Bazı dosyaları Microsoft Defender Virüsten Koruma taramaların dışında tutmak için dışlama listelerinizi değiştirirsiniz. Microsoft Defender Virüsten Koruma, kuruluş yönetiminde, veritabanı yönetiminde ve diğer kurumsal senaryolarda ve durumlarda kullanılanlar gibi bilinen işletim sistemi davranışlarına ve tipik yönetim dosyalarına dayalı birçok otomatik dışlama içerir.

> [!NOTE]
> Dışlamalar, İstenmeyebilecek Uygulamalar (PUA) algılamaları için de geçerlidir.
>
> Otomatik dışlamalar yalnızca Windows Server 2016 ve üzeri için geçerlidir. Bu dışlamalar Windows Güvenliği uygulamasında ve PowerShell'de görünmez.

Aşağıdaki tabloda dosya uzantısına ve klasör konumuna göre bazı dışlama örnekleri listelemektedir.

|Dışlama|Örnekler|Dışlama listesi|
|---|---|---|
|Belirli bir uzantıya sahip herhangi bir dosya|Belirtilen uzantıya sahip tüm dosyalar, makinenin herhangi bir yerinde. <p> Geçerli söz dizimi: `.test` ve `test`|Uzantı dışlamaları|
|Belirli bir klasör altındaki herhangi bir dosya|Klasörün altındaki `c:\test\sample` tüm dosyalar|Dosya ve klasör dışlamaları|
|Belirli bir klasördeki belirli bir dosya|Yalnızca dosya `c:\sample\sample.test`|Dosya ve klasör dışlamaları|
|Belirli bir işlem|Yürütülebilir dosya `c:\test\process.exe`|Dosya ve klasör dışlamaları|

## <a name="characteristics-of-exclusion-lists"></a>Dışlama listelerinin özellikleri

- Alt klasör yeniden ayrıştırma noktası olmadığı sürece, klasör dışlamaları söz konusu klasörün altındaki tüm dosya ve klasörlere uygulanır. Yeniden ayrıştırma noktası alt klasörleri ayrı ayrı dışlanmalıdır.
- Bir yol veya klasör tanımlanmamışsa, dosya uzantıları tanımlı uzantıya sahip herhangi bir dosya adına uygulanır.

## <a name="important-notes-about-exclusions-based-on-file-extensions-and-folder-locations"></a>Dosya uzantılarına ve klasör konumlarına göre dışlamalar hakkında önemli notlar

- Yıldız işareti (\*) gibi joker karakterlerin kullanılması, dışlama kurallarının yorumlanma şeklini değiştirir. Joker karakterlerin nasıl çalıştığı hakkında önemli bilgiler için [Dosya adı ve klasör yolunda joker karakterler kullanma veya uzantı dışlama listeleri](#use-wildcards-in-the-file-name-and-folder-path-or-extension-exclusion-lists) bölümüne bakın.

- Eşlenen ağ sürücülerini dışlama. Gerçek ağ yolunu belirtin.

- Microsoft Defender Virüsten Koruma hizmeti başlatıldıktan sonra oluşturulan ve dışlama listesine eklenen yeniden ayrıştırma noktaları olan klasörler eklenmez. Yeni yeniden ayrıştırma noktalarının geçerli bir dışlama hedefi olarak tanınması için hizmeti yeniden başlatın (Windows yeniden başlatın).

- Dışlamalar [zamanlanmış taramalar](scheduled-catch-up-scans-microsoft-defender-antivirus.md), [isteğe bağlı taramalar](run-scan-microsoft-defender-antivirus.md) ve [gerçek zamanlı koruma](configure-real-time-protection-microsoft-defender-antivirus.md) için geçerlidir ancak Uç Nokta için Defender genelinde geçerli değildir. Uç Nokta için Defender'da dışlamaları tanımlamak için [özel göstergeler](manage-indicators.md) kullanın.

- Varsayılan olarak, listelerde yapılan yerel değişiklikler (PowerShell ve WMI ile yapılan değişiklikler de dahil olmak üzere yönetici ayrıcalıklarına sahip kullanıcılar tarafından), grup ilkesi, Configuration Manager veya Intune tarafından tanımlandığı (ve dağıtıldığı) listelerle birleştirilir. çakışmalar olduğunda grup ilkesi listeleri önceliklidir. Ayrıca, grup ilkesi ile yapılan dışlama listesi değişiklikleri [Windows Güvenliği uygulamasında](microsoft-defender-security-center-antivirus.md) görünür.

- Yerel değişikliklerin yönetilen dağıtım ayarlarını geçersiz kılmasını sağlamak için yerel [ve genel olarak tanımlanmış dışlama listelerinin nasıl birleştirildiğini yapılandırın](configure-local-policy-overrides-microsoft-defender-antivirus.md#merge-lists).

## <a name="configure-the-list-of-exclusions-based-on-folder-name-or-file-extension"></a>Dışlama listesini klasör adına veya dosya uzantısına göre yapılandırma

Microsoft Defender Virüsten Koruma için dışlamaları tanımlamak için çeşitli yöntemler arasından seçim yapabilirsiniz.

### <a name="use-intune-to-configure-file-name-folder-or-file-extension-exclusions"></a>Dosya adı, klasör veya dosya uzantısı dışlamalarını yapılandırmak için Intune kullanma

Aşağıdaki makalelere bakın:

- [Microsoft Intune'de cihaz kısıtlama ayarlarını yapılandırma](/intune/device-restrictions-configure)
- [Intune'da Windows 10 için cihaz kısıtlama ayarlarını Microsoft Defender Virüsten Koruma](/intune/device-restrictions-windows-10#microsoft-defender-antivirus)

### <a name="use-configuration-manager-to-configure-file-name-folder-or-file-extension-exclusions"></a>Dosya adı, klasör veya dosya uzantısı dışlamalarını yapılandırmak için Configuration Manager kullanma

Microsoft Endpoint Manager (geçerli dal) yapılandırma ayrıntıları için bkz[. Kötü amaçlı yazılımdan koruma ilkeleri oluşturma ve dağıtma: Dışlama ayarları](/configmgr/protect/deploy-use/endpoint-antimalware-policies#exclusion-settings).

### <a name="use-group-policy-to-configure-folder-or-file-extension-exclusions"></a>Klasör veya dosya uzantısı dışlamalarını yapılandırmak için grup ilkesi kullanma

> [!NOTE]
> Bir dosyanın tam yolunu belirtirseniz, yalnızca bu dosya dışlanır. Dışlamada bir klasör tanımlanmışsa, bu klasörün altındaki tüm dosyalar ve alt dizinler dışlanır.

1. grup ilkesi yönetim bilgisayarınızda [grup ilkesi Yönetim Konsolu'nu](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)) açın, yapılandırmak istediğiniz grup ilkesi Nesnesine sağ tıklayın ve **Düzenle'yi** seçin.

2. **Grup İlkesi Yönetimi Düzenleyicisi**'nde **Bilgisayar yapılandırması**'na gidin ve **Yönetim şablonları**'nı seçin.

3. **Dışlamalar Windows Defender Virüsten Koruma bileşenleri** \> **Windows** \> için ağacı genişletin.

4. Düzenlemek için **Yol Dışlamaları** ayarını açın ve dışlamalarınızı ekleyin.

    1. Seçeneği **Etkin** olarak ayarlayın.
    2. **Seçenekler** bölümünde **Göster'i** seçin.
    3. **Her klasörü Değer adı** sütununun altında kendi satırında belirtin.
    4. Bir dosya belirtiyorsanız, sürücü harfi, klasör yolu, dosya adı ve uzantı da dahil olmak üzere dosyanın tam yolunu girdiğinizden emin olun.
    5. **Değer** sütununa **0** girin.

5. **Tamam**'ı seçin.

6. Düzenleme için **Uzantı Dışlamaları** ayarını açın ve dışlamalarınızı ekleyin.

    1. Seçeneği **Etkin** olarak ayarlayın.
    2. **Seçenekler** bölümünde **Göster'i** seçin.
    3. Her dosya uzantısını **Değer adı** sütununun altına kendi satırına girin.
    4. **Değer** sütununa **0** girin.

7. **Tamam**'ı seçin.

<a id="ps"></a>

### <a name="use-powershell-cmdlets-to-configure-file-name-folder-or-file-extension-exclusions"></a>Dosya adı, klasör veya dosya uzantısı dışlamalarını yapılandırmak için PowerShell cmdlet'lerini kullanma

Uzantıya, konuma veya dosya adına göre dosyalar için dışlama eklemek veya kaldırmak için PowerShell kullanmak için üç cmdlet'in ve uygun dışlama listesi parametresinin kullanılması gerekir. Cmdlet'lerin tümü [Defender modülündedir](/powershell/module/defender/).

Cmdlet'lerin biçimi aşağıdaki gibidir:

```PowerShell
<cmdlet> -<exclusion list> "<item>"
```

Aşağıdaki tabloda, PowerShell cmdlet'inin `<cmdlet>` bölümünde kullanabileceğiniz cmdlet'ler listelenir:

|Yapılandırma eylemi|PowerShell cmdlet'i|
|:---|:---|
|Listeyi oluşturma veya üzerine yazma|`Set-MpPreference`|
|Listeye ekle|`Add-MpPreference`|
|Öğeyi listeden kaldırma|`Remove-MpPreference`|

Aşağıdaki tabloda, PowerShell cmdlet'inin `<exclusion list>` bölümünde kullanabileceğiniz değerler listelenir:

|Dışlama türü|PowerShell parametresi|
|---|---|
|Belirtilen dosya uzantısına sahip tüm dosyalar|`-ExclusionExtension`|
|Klasör altındaki tüm dosyalar (alt dizinlerdeki dosyalar dahil) veya belirli bir dosya|`-ExclusionPath`|

> [!IMPORTANT]
> veya `Add-MpPreference`ile `Set-MpPreference` bir liste oluşturduysanız, cmdlet'ini `Set-MpPreference` yeniden kullanmak varolan listenin üzerine yazar.

Örneğin, aşağıdaki kod parçacığı Microsoft Defender Virüsten Koruma taramalarının dosya uzantısına sahip herhangi bir dosyayı dışlamasına `.test` neden olabilir:

```PowerShell
Add-MpPreference -ExclusionExtension ".test"
```

> [!TIP]
> Daha fazla bilgi için bkz. Microsoft Defender Virüsten Koruma ve [Defender Virüsten Koruma cmdlet'lerini](/powershell/module/defender/) [yapılandırmak ve çalıştırmak için PowerShell](use-powershell-cmdlets-microsoft-defender-antivirus.md) cmdlet'lerini kullanma.

### <a name="use-windows-management-instrumentation-wmi-to-configure-file-name-folder-or-file-extension-exclusions"></a>Dosya adı, klasör veya dosya uzantısı dışlamalarını yapılandırmak için Windows Yönetim Araçları'nı (WMI) kullanın

Aşağıdaki özellikler için [MSFT_MpPreference sınıfının Set, Add ve Remove yöntemlerini](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) kullanın:

```WMI
ExclusionExtension
ExclusionPath
```

**Ayarla**, **Ekle** ve **Kaldır'ın** kullanılması, PowerShell'deki karşılıklarına benzer: `Set-MpPreference`, `Add-MpPreference`, ve `Remove-MpPreference`.

> [!TIP]
> Daha fazla bilgi için bkz. [Windows Defender WMIv2 API'leri](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal).

<a id="man-tools"></a>

### <a name="use-the-windows-security-app-to-configure-file-name-folder-or-file-extension-exclusions"></a>Dosya adı, klasör veya dosya uzantısı dışlamalarını yapılandırmak için Windows Güvenliği uygulamasını kullanın

Yönergeler için bkz. [Windows Güvenliği uygulamasında dışlama ekleme](microsoft-defender-security-center-antivirus.md).

<a id="wildcards"></a>

## <a name="use-wildcards-in-the-file-name-and-folder-path-or-extension-exclusion-lists"></a>Dosya adı ve klasör yolu veya uzantı dışlama listelerinde joker karakterler kullanın

Dosya adı veya klasör yolu dışlama listesindeki öğeleri tanımlarken joker karakter olarak yıldız `*`işareti , soru işareti `?`veya ortam değişkenlerini (örneğin `%ALLUSERSPROFILE%`) kullanabilirsiniz. Bu joker karakterlerin yorumlandıkları yöntem, diğer uygulama ve dillerdeki normal kullanımlarından farklıdır. Belirli sınırlamalarını anlamak için bu bölümü okuduğunuzdan emin olun.

> [!IMPORTANT]
> Bu joker karakterler için önemli sınırlamalar ve kullanım senaryoları vardır:
> - Ortam değişkeni kullanımı, makine değişkenleriyle ve NT AUTHORITY\SYSTEM hesabı olarak çalışan işlemler için geçerlidir.
> - Giriş başına en fazla altı joker karakter kullanabilirsiniz.
> - Sürücü harfi yerine joker karakter kullanamazsınız.
> - Bir klasör dışlamadaki yıldız `*` işareti, tek bir klasör için yerinde durur. Birden çok örneğini `\*\` kullanarak belirtilmemiş adlara sahip birden çok iç içe klasör belirtin.
> - Şu anda, Microsoft Endpoint Configuration Manager joker karakterleri (veya `?`gibi`*`) desteklemez.
    
Aşağıdaki tabloda joker karakterlerin nasıl kullanılabildiği açıklanır ve bazı örnekler sağlanır.

|Joker|Örnekler|
|---|---|
|`*` (yıldız işareti) <p> **Dosya adı ve dosya uzantısı eklemelerinde**, yıldız işareti herhangi bir sayıda karakterin yerini alır ve yalnızca bağımsız değişkende tanımlanan son klasördeki dosyalara uygulanır. <p> **Klasör dışlamalarında** yıldız işareti tek bir klasörün yerini alır. Birden çok `*` iç içe klasörü belirtmek için klasör eğik çizgileriyle `\` birden çok kullanın. Joker karakterli ve adlandırılmış klasörlerin sayısı eşleştirildikten sonra tüm alt klasörler de eklenir.|`C:\MyData\*.txt` Içerir `C:\MyData\notes.txt` <p> `C:\somepath\*\Data` içindeki herhangi bir dosyayı `C:\somepath\Archives\Data` ve alt klasörlerini ve `C:\somepath\Authorized\Data` alt klasörlerini içerir <p> `C:\Serv\*\*\Backup` içindeki `C:\Serv\Primary\Denied\Backup` herhangi bir dosyayı ve alt klasörlerini ve `C:\Serv\Secondary\Allowed\Backup` alt klasörlerini içerir|
|`?` (soru işareti)  <p> **Dosya adı ve dosya uzantısı eklemelerinde**, soru işareti tek bir karakterin yerini alır ve yalnızca bağımsız değişkende tanımlanan son klasördeki dosyalara uygulanır. <p> **Klasör dışlamalarında**, soru işareti bir klasör adındaki tek bir karakterin yerini alır. Joker karakterli ve adlandırılmış klasörlerin sayısı eşleştirildikten sonra tüm alt klasörler de eklenir.|`C:\MyData\my?.zip` Içerir `C:\MyData\my1.zip` <p> `C:\somepath\?\Data` içindeki herhangi bir dosyayı `C:\somepath\P\Data` ve alt klasörlerini içerir  <p> `C:\somepath\test0?\Data` içindeki herhangi bir dosyayı `C:\somepath\test01\Data` ve alt klasörlerini içerebilir|
|Ortam değişkenleri <p> Tanımlı değişken, dışlama değerlendirildiğinde bir yol olarak doldurulur.|`%ALLUSERSPROFILE%\CustomLogFiles` şunları içerir: `C:\ProgramData\CustomLogFiles\Folder1\file1.txt`|

> [!IMPORTANT]
> Bir dosya dışlama bağımsız değişkenini klasör dışlama bağımsız değişkeniyle karıştırırsanız, kurallar eşleşen klasörde dosya bağımsız değişkeni eşleşmesinde durur ve hiçbir alt klasörde dosya eşleşmelerini aramaz.
> Örneğin, klasörlerde `c:\data\final\marked` "tarih" ile başlayan tüm dosyaları ve `c:\data\review\marked` kural bağımsız değişkenini `c:\data\*\marked\date*`kullanarak dışlayabilirsiniz.
> Ancak bu bağımsız değişken, veya `c:\data\review\marked`altındaki `c:\data\final\marked` alt klasörlerdeki hiçbir dosyayla eşleşmez.

<a id="review"></a>

### <a name="system-environment-variables"></a>Sistem ortamı değişkenleri

Aşağıdaki tabloda sistem hesabı ortam değişkenleri listelenip açıklanmaktadır.

|Bu sistem ortamı değişkeni...|Buna yeniden yönlendirir|
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

## <a name="review-the-list-of-exclusions"></a>Dışlama listesini gözden geçirin

Aşağıdaki yöntemlerden birini kullanarak dışlama listesindeki öğeleri alabilirsiniz:

- [Intune](/mem/intune/fundamentals/deployment-guide-intune-setup)
- [Microsoft Uç Noktası Yapılandırma Yöneticisi](/configmgr/protect/deploy-use/endpoint-antimalware-policies)
- [MpCmdRun](command-line-arguments-microsoft-defender-antivirus.md)
- [PowerShell](/powershell/module/defender)
- [Windows Güvenliği uygulaması](microsoft-defender-security-center-antivirus.md)

> [!IMPORTANT]
> grup ilkesi ile yapılan dışlama listesi değişiklikleri [Windows Güvenliği uygulamasındaki](microsoft-defender-security-center-antivirus.md) listelerde **gösterilir**.
> Windows Güvenliği uygulamasında yapılan değişiklikler grup ilkesi listelerinde **gösterilmez**.

PowerShell kullanıyorsanız, listeyi iki yolla alabilirsiniz:

- Tüm Microsoft Defender Virüsten Koruma tercihlerinin durumunu alın. Her liste ayrı satırlarda görüntülenir, ancak her liste içindeki öğeler aynı satırda birleştirilir.
- Tüm tercihlerin durumunu bir değişkene yazın ve bu değişkeni yalnızca ilgilendiğiniz listeyi çağırmak için kullanın. her kullanımı `Add-MpPreference` yeni bir satıra yazılır.

### <a name="validate-the-exclusion-list-by-using-mpcmdrun"></a>MpCmdRun kullanarak dışlama listesini doğrulama

mpcmdrun.exeayrılmış [komut satırı aracıyla ](./command-line-arguments-microsoft-defender-antivirus.md)dışlamaları denetlemek için aşağıdaki komutu kullanın:

```console
Start, CMD (Run as admin)
cd "%programdata%\microsoft\windows defender\platform"
cd 4.18.2111-5.0 (Where 4.18.2111-5.0 is this month's Microsoft Defender Antivirus "Platform Update".)
MpCmdRun.exe -CheckExclusion -path <path>
```

> [!NOTE]
> MpCmdRun ile dışlamaların denetlenmesi için MICROSOFT DEFENDER VIRÜSTEN KORUMA CAMP sürüm 4.18.2111-5.0 (Aralık 2021'de yayımlandı) veya üzeri gerekir.

### <a name="review-the-list-of-exclusions-alongside-all-other-microsoft-defender-antivirus-preferences-by-using-powershell"></a>PowerShell kullanarak diğer tüm Microsoft Defender Virüsten Koruma tercihlerinin yanı sıra dışlama listesini gözden geçirin

Aşağıdaki cmdlet'i kullanın:

```PowerShell
Get-MpPreference
```

Aşağıdaki örnekte, listede yer alan `ExclusionExtension` öğeler vurgulanır:

:::image type="content" source="../../media/wdav-powershell-get-exclusions-variable.png" alt-text="Get-MpPreference için PowerShell çıkışı" lightbox="../../media/wdav-powershell-get-exclusions-variable.png":::

Daha fazla bilgi için bkz. Microsoft Defender Virüsten Koruma ve [Defender Virüsten Koruma cmdlet'lerini](/powershell/module/defender/) [yapılandırmak ve çalıştırmak için PowerShell](use-powershell-cmdlets-microsoft-defender-antivirus.md) cmdlet'lerini kullanma.

### <a name="retrieve-a-specific-exclusions-list-by-using-powershell"></a>PowerShell kullanarak belirli bir dışlama listesini alma

Aşağıdaki kod parçacığını kullanın (her satırı ayrı bir komut olarak girin); **WDAVprefs** değerini değişkeni adlandırmak istediğiniz etiketle değiştirin:

```PowerShell
$WDAVprefs = Get-MpPreference
$WDAVprefs.ExclusionExtension
$WDAVprefs.ExclusionPath
```

Aşağıdaki örnekte, liste cmdlet'in `Add-MpPreference` her kullanımı için yeni satırlara ayrılmıştır:

:::image type="content" source="../../media/wdav-powershell-get-exclusions-variable.png" alt-text="Yalnızca dışlama listesindeki girişleri gösteren PowerShell çıkışı" lightbox="../../media/wdav-powershell-get-exclusions-variable.png":::

Daha fazla bilgi için bkz. Microsoft Defender Virüsten Koruma ve [Defender Virüsten Koruma cmdlet'lerini](/powershell/module/defender/) [yapılandırmak ve çalıştırmak için PowerShell](use-powershell-cmdlets-microsoft-defender-antivirus.md) cmdlet'lerini kullanma.

<a id="validate"></a>

## <a name="validate-exclusions-lists-with-the-eicar-test-file"></a>EICAR test dosyasıyla dışlama listelerini doğrulama

Bir test dosyasını indirmek için cmdlet veya .NET WebClient sınıfıyla `Invoke-WebRequest` PowerShell kullanarak dışlama listelerinizin çalıştığını doğrulayabilirsiniz.

Aşağıdaki PowerShell kod parçacığında öğesini dışlama kurallarınıza uygun bir dosyayla değiştirin `test.txt` . Örneğin, uzantıyı `.testing` dışladıysanız değerini ile `test.testing`değiştirin`test.txt`. Bir yolu test ediyorsanız, cmdlet'ini bu yol içinde çalıştırdığınızdan emin olun.

```PowerShell
Invoke-WebRequest "http://www.eicar.org/download/eicar.com.txt" -OutFile "test.txt"
```

Microsoft Defender Virüsten Koruma kötü amaçlı yazılım bildiriyorsa kural çalışmıyor demektir. Kötü amaçlı yazılım raporu yoksa ve indirilen dosya varsa, dışlama çalışıyor demektir. İçeriğin [EICAR test dosyası web sitesinde](http://www.eicar.org/86-0-Intended-use.html) açıklananla aynı olduğunu onaylamak için dosyayı açabilirsiniz.

Test dosyasını indirmek için .NET WebClient sınıfını çağıran aşağıdaki PowerShell kodunu da kullanabilirsiniz; cmdlet'inde `Invoke-WebRequest` olduğu gibi değerini doğrulamakta olduğunuz kurala uygun bir dosyayla değiştirin `c:\test.txt` :

```PowerShell
$client = new-object System.Net.WebClient
$client.DownloadFile("http://www.eicar.org/download/eicar.com.txt","c:\test.txt")
```

İnternet erişiminiz yoksa, aşağıdaki PowerShell komutuyla EICAR dizesini yeni bir metin dosyasına yazarak kendi EICAR test dosyanızı oluşturabilirsiniz:

```PowerShell
[io.file]::WriteAllText("test.txt",'X5O!P%@AP[4\PZX54(P^)7CC)7}$EICAR-STANDARD-ANTIVIRUS-TEST-FILE!$H+H*')
```

Ayrıca, dizeyi boş bir metin dosyasına kopyalayabilir ve dosya adıyla veya dışlamaya çalıştığınız klasöre kaydetmeye çalışabilirsiniz.

> [!TIP]
> Diğer platformlar için Antivirüs ile ilgili bilgi arıyorsanız bkz:
> - [MacOS'ta Uç Nokta için Microsoft Defender tercihlerini ayarlayın](mac-preferences.md)
> - [Mac'te Uç Nokta için Microsoft Defender](microsoft-defender-endpoint-mac.md)
> - [Intune için Microsoft Defender için macOS Virüsten Koruma ilke ayarları](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Linux'ta Uç Nokta için Microsoft Defender tercihlerini ayarlayın](linux-preferences.md)
> - [Linux'ta Uç Nokta için Microsoft Defender](microsoft-defender-endpoint-linux.md)
> - [Android özelliklerinde Uç Nokta için Defender’ı yapılandırın](android-configure.md)
> - [iOS özelliklerinde Uç Nokta için Microsoft Defender’ı yapılandırın](ios-configure-features.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Microsoft Defender Virüsten Koruma taramalarında dışlamaları yapılandırma ve doğrulama](configure-exclusions-microsoft-defender-antivirus.md)
- [İşlemler tarafından açılan dosyalar için dışlamaları yapılandırma ve doğrulama](configure-process-opened-file-exclusions-microsoft-defender-antivirus.md)
- [Windows Sunucusu'nda Microsoft Defender Virüsten Koruma dışlamalarını yapılandırma](configure-server-exclusions-microsoft-defender-antivirus.md)
- [Dışlamaları tanımlarken kaçınılması gereken yaygın hatalar](common-exclusion-mistakes-microsoft-defender-antivirus.md)
