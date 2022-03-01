---
title: Windows Server'da Microsoft Defender Virüsten Koruma dışlamaları yapılandırma
ms.reviewer: pahuijbr
manager: dansimp
description: Windows Server, sunucu rolüne bağlı olarak otomatik dışlamalar içerir. Ayrıca, özel dışlamalar da  eklemek gerekir.
keywords: dışlamalar, sunucu, otomatik dışlamalar, otomatik, özel, taramalar, Microsoft Defender Virüsten Koruma
ms.prod: m365-security
ms.technology: mde
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.topic: article
ms.custom: nextgen
ms.date: 02/04/2022
ms.collection: M365-security-compliance
ms.openlocfilehash: 442172afc9caf5dbd2af8c91cda531494fabd05d
ms.sourcegitcommit: 954c8af658adb270fe843991e048c6a30e86e77c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2022
ms.locfileid: "63016483"
---
# <a name="configure-microsoft-defender-antivirus-exclusions-on-windows-server"></a>Windows Server'da Microsoft Defender Virüsten Koruma dışlamaları yapılandırma


**Aşağıdakiler için geçerlidir:**

- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Microsoft Defender Virüsten Koruma

Microsoft Defender Virüsten Koruma Windows Server 2016 Windows Server 2019 sizi belirtilen sunucu rolünüz tanımlandığı şekilde belirli dışlamalara otomatik olarak kaydeder. Bu dışlamalar, Windows Güvenliği uygulamasında gösterilen standart [dışlama listelerinde görünmez](microsoft-defender-security-center-antivirus.md).

Sunucu rolü tanımlı otomatik dışlamalara ek olarak, özel dışlamalar ekleyebilir veya kaldırabilirsiniz. Bunu yapmak için şu makalelere bakın:
- [Dosya adı, uzantı ve klasör konumu temel alarak dışlamaları yapılandırma ve doğrulama](configure-extension-file-exclusions-microsoft-defender-antivirus.md)
- [İşlemler tarafından açılan dosyalar için dışlamaları yapılandırma ve doğrulama](configure-process-opened-file-exclusions-microsoft-defender-antivirus.md)

## <a name="a-few-points-to-keep-in-mind"></a>Gözlerde tutma gereken birkaç nokta

Aşağıdaki önemli noktaları unutmayın:

- Özel dışlamalar, otomatik dışlamalara göre önceliklidir.
- Otomatik dışlamalar yalnızca Gerçek zamanlı koruma (RTP) tarama için geçerlidir. Tam, hızlı veya isteğe bağlı tarama sırasında otomatik dışlamalara devam etmek mümkün değildir.
- Özel ve yinelenen dışlamalar otomatik dışlamalarla çakışmaz.
- Microsoft Defender Virüsten Koruma, bilgisayarınızda hangi rollerin yüklü olduğunu belirlemek için Dağıtım Resmi Servis ve Yönetimi (DISM) araçlarını kullanır.
- Windows Server 2012 R2'de Microsoft Defender Virüsten Koruma özellik olarak kullanılamaz. Bu sunucuları Uç Nokta için Defender'a işe ayarlarken, Windows Defender Virüsten Koruma ayarları yüklenir ve işletim sistemi dosyaları için varsayılan dışlamalar uygulanır. Bununla birlikte, sunucu rollerinin (aşağıda belirtilen) dışlamaları otomatik olarak geçerli olmaz ve bu dışlamaları uygun şekilde yapılandırmanız gerekir. Daha fazla bilgi edinmek için bkz[. Windows uç nokta hizmeti için Microsoft Defender'a ek sunucu ekleme](configure-server-endpoints.md).

Bu makalede, 2013 veya sonraki Microsoft Defender Virüsten Koruma özel Windows Server 2016 genel bir bakış sağlar.

Dış Microsoft Defender Virüsten Koruma çok daha sonraki bir Windows Server 2016 yerleşik olduğundan, işletim sistemi dosyaları ve sunucu rollerinin dışlamaları otomatik olarak olur. Bununla birlikte, özel dışlamaları tanımlayabilirsiniz. Ayrıca gerekirse otomatik dışlamaları devre dışı  olduğu gibi tercih de oluşturabilirsiniz.

Bu makale aşağıdaki bölümleri içerir:

<br/><br/>

|Bölüm|Açıklama|
|---|---|
|[Özel ya da sonraki Windows Server 2016 otomatik dışlamalar](#automatic-exclusions-on-windows-server-2016-or-later)|İki ana dışlama türü açıklanmış ve otomatik dışlamaların ayrıntılı bir listesini içerir|
|[Otomatik dışlamaları devre dışı bırakma](#opting-out-of-automatic-exclusions)|Otomatik dışlamaların nasıl iptal edileceklerini açıklayan önemli noktalar ve yordamlar içerir|
|[Özel dışlamaları tanımlama](#defining-custom-exclusions)|Özel dışlamaları tanımlamak için nasıl yapılanma bilgilerine bağlantılar sağlar|

## <a name="automatic-exclusions-on-windows-server-2016-or-later"></a>Özel ya da sonraki Windows Server 2016 otomatik dışlamalar

Dışlama Windows Server 2016 sonra, aşağıdaki dışlamaları tanımlamanız gerekir:

- İşletim sistemi dosyaları
- Sunucu rolleri ve sunucu rolleri aracılığıyla eklenen dosyalar

Yerleşik Microsoft Defender Virüsten Koruma olduğundan, çalışma sayfalarındaki veya sonraki işletim sistemi dosyalarında dışlama Windows Server 2016 gerektirmez. Buna ek olarak, Windows Server 2016 veya sonraki bir sürümü çalıştırarak bir rol yüklerken, Microsoft Defender Virüsten Koruma sunucu rolü için otomatik dışlamalar ve rolü yüklerken eklenen tüm dosyalar için de otomatik dışlamalar içerir.

İşletim sistemi dışlamaları ve sunucu rolü dışlamaları, Windows Güvenliği uygulamasında gösterilen standart [dışlama listelerinde görünmez](microsoft-defender-security-center-antivirus.md).

> [!NOTE]
> Sunucu rollerinin ve işletim sistemi dosyalarının otomatik dışlamaları, dışlamalar Windows Server 2012. R2'de çalışan sunucularınız Uç nokta için Defender Windows Server 2012 a varsa otomatik dışlamalar uygulanabilir. (Bkz[. Windows uç nokta hizmeti için Microsoft Defender'a ek sunucu ekleme](configure-server-endpoints.md).)


### <a name="the-list-of-automatic-exclusions"></a>Otomatik dışlamalar listesi

Aşağıdaki bölümler, otomatik dışlamalar dosya yolları ve dosya türleriyle birlikte teslim edilen dışlamaları içerir.

#### <a name="default-exclusions-for-all-roles"></a>Tüm roller için varsayılan dışlamalar

Bu bölümde Windows Server 2016, Windows Server 2022 ve Windows tüm roller için varsayılan dışlamalar liste almaktadır.

> [!NOTE]
> Varsayılan konumlar bu makalede listelenen konumlardan farklı olabilir.

##### <a name="windows-tempedb-files"></a>Windows "temp.edb" dosyalarını yükleme

- `%windir%\SoftwareDistribution\Datastore\*\tmp.edb`
- `%ProgramData%\Microsoft\Search\Data\Applications\Windows\windows.edb`

##### <a name="windows-update-files-or-automatic-update-files"></a>Windows güncelleştirme veya Otomatik Güncelleştirme dosyaları

- `%windir%\SoftwareDistribution\Datastore\*\Datastore.edb`
- `%windir%\SoftwareDistribution\Datastore\*\edb.chk`
- `%windir%\SoftwareDistribution\Datastore\*\edb\*.log`
- `%windir%\SoftwareDistribution\Datastore\*\Edb\*.jrs`
- `%windir%\SoftwareDistribution\Datastore\*\Res\*.log`

##### <a name="windows-security-files"></a>Windows Güvenliği dosya yükleme

- `%windir%\Security\database\*.chk`
- `%windir%\Security\database\*.edb`
- `%windir%\Security\database\*.jrs`
- `%windir%\Security\database\*.log`
- `%windir%\Security\database\*.sdb`

##### <a name="group-policy-files"></a>Grup İlkesi dosyaları

- `%allusersprofile%\NTUser.pol`
- `%SystemRoot%\System32\GroupPolicy\Machine\registry.pol`
- `%SystemRoot%\System32\GroupPolicy\User\registry.pol`

##### <a name="wins-files"></a>WINS dosyaları

- `%systemroot%\System32\Wins\*\*.chk`
- `%systemroot%\System32\Wins\*\*.log`
- `%systemroot%\System32\Wins\*\*.mdb`
- `%systemroot%\System32\LogFiles\`
- `%systemroot%\SysWow64\LogFiles\`

##### <a name="file-replication-service-frs-exclusions"></a>Dosya Çoğaltma Hizmeti (FRS) dışlamaları

- Dosya Çoğaltma Hizmeti (FRS) çalışma klasöründeki dosyalar. FRS çalışma klasörü kayıt defteri anahtarında belirtilir `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\NtFrs\Parameters\Working Directory`

  - `%windir%\Ntfrs\jet\sys\*\edb.chk`
  - `%windir%\Ntfrs\jet\*\Ntfrs.jdb`
  - `%windir%\Ntfrs\jet\log\*\*.log`

- FRS Veritabanı günlük dosyaları. FRS Veritabanı günlük dosyası klasörü kayıt defteri anahtarında belirtilir `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\Ntfrs\Parameters\DB Log File Directory`

  - `%windir%\Ntfrs\*\Edb\*.log`

- FRS hazırlama klasörü. Kayıt defteri anahtarında hazırlama klasörü belirtilir `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\NtFrs\Parameters\Replica Sets\GUID\Replica Set Stage`

  - `%systemroot%\Sysvol\*\Ntfrs_cmp*\`

- FRS ön yükleme klasörü. Bu klasör klasör tarafından belirtilmiştir `Replica_root\DO_NOT_REMOVE_NtFrs_PreInstall_Directory`

  - `%systemroot%\SYSVOL\domain\DO_NOT_REMOVE_NtFrs_PreInstall_Directory\*\Ntfrs*\`

- Dağıtılmış Dosya Sistemi Çoğaltması (BUR) veritabanı ve çalışma klasörleri. Bu klasörler kayıt defteri anahtarıyla belirtilir `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\DFSR\Parameters\Replication Groups\GUID\Replica Set Configuration File`

  > [!NOTE]
  > Özel konumlar için bkz. [Otomatik dışlamaları devre dışı bırakma](#opting-out-of-automatic-exclusions).

  - `%systemdrive%\System Volume Information\DFSR\$db_normal$`
  - `%systemdrive%\System Volume Information\DFSR\FileIDTable_*`
  - `%systemdrive%\System Volume Information\DFSR\SimilarityTable_*`
  - `%systemdrive%\System Volume Information\DFSR\*.XML`
  - `%systemdrive%\System Volume Information\DFSR\$db_dirty$`
  - `%systemdrive%\System Volume Information\DFSR\$db_clean$`
  - `%systemdrive%\System Volume Information\DFSR\$db_lostl$`
  - `%systemdrive%\System Volume Information\DFSR\Dfsr.db`
  - `%systemdrive%\System Volume Information\DFSR\*.frx`
  - `%systemdrive%\System Volume Information\DFSR\*.log`
  - `%systemdrive%\System Volume Information\DFSR\Fsr*.jrs`
  - `%systemdrive%\System Volume Information\DFSR\Tmp.edb`

##### <a name="process-exclusions"></a>İşlem dışlamaları

- `%systemroot%\System32\dfsr.exe`
- `%systemroot%\System32\dfsrs.exe`

##### <a name="hyper-v-exclusions"></a>Hyper-V dışlamaları

Aşağıdaki tabloda, Hyper-V rolünü yükleyen dosya türü dışlamaları, klasör dışlamaları ve süreç dışlamaları otomatik olarak teslim edilir.

<br><br/>

|Dışlama türü|Specifics|
|---|---|
|Dosya türleri|`*.vhd` <br/> `*.vhdx` <br/> `*.avhd` <br/> `*.avhdx` <br/> `*.vsv` <br/> `*.iso` <br/> `*.rct` <br/> `*.vmcx` <br/> `*.vmrs`|
|Klasörler|`%ProgramData%\Microsoft\Windows\Hyper-V` <br/> `%ProgramFiles%\Hyper-V` <br/> `%SystemDrive%\ProgramData\Microsoft\Windows\Hyper-V\Snapshots` <br/> `%Public%\Documents\Hyper-V\Virtual Hard Disks`|
|İşlemler|`%systemroot%\System32\Vmms.exe` <br/> `%systemroot%\System32\Vmwp.exe`|

##### <a name="sysvol-files"></a>SYSVOL dosyaları

- `%systemroot%\Sysvol\Domain\*.adm`
- `%systemroot%\Sysvol\Domain\*.admx`
- `%systemroot%\Sysvol\Domain\*.adml`
- `%systemroot%\Sysvol\Domain\Registry.pol`
- `%systemroot%\Sysvol\Domain\*.aas`
- `%systemroot%\Sysvol\Domain\*.inf`
- `%systemroot%\Sysvol\Domain\*Scripts.ini`
- `%systemroot%\Sysvol\Domain\*.ins`
- `%systemroot%\Sysvol\Domain\Oscfilter.ini`


#### <a name="active-directory-exclusions"></a>Active Directory dışlamaları

Bu bölümde, Active Directory Etki Alanı Hizmetleri'ne (AD DS) yüklemeniz sırasında otomatik olarak teslim edilen dışlamalar listelenir.

##### <a name="ntds-database-files"></a>NTDS veritabanı dosyaları

Veritabanı dosyaları kayıt defteri anahtarında belirtilir `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\NTDS\Parameters\DSA Database File`

- `%windir%\Ntds\ntds.dit`
- `%windir%\Ntds\ntds.pat`

##### <a name="the-ad-ds-transaction-log-files"></a>AD DS işlem günlüğü dosyaları

İşlem günlüğü dosyaları kayıt defteri anahtarında belirtilir `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\NTDS\Parameters\Database Log Files Path`

- `%windir%\Ntds\EDB*.log`
- `%windir%\Ntds\Res*.log`
- `%windir%\Ntds\Edb*.jrs`
- `%windir%\Ntds\Ntds*.pat`
- `%windir%\Ntds\TEMP.edb`

##### <a name="the-ntds-working-folder"></a>NTDS çalışma klasörü

Bu klasör kayıt defteri anahtarında belirtilir `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\NTDS\Parameters\DSA Working Directory`

- `%windir%\Ntds\Temp.edb`
- `%windir%\Ntds\Edb.chk`

##### <a name="process-exclusions-for-ad-ds-and-ad-ds-related-support-files"></a>AD DS ve AD DS ile ilgili destek dosyaları için süreç dışlamaları

- `%systemroot%\System32\ntfrs.exe`
- `%systemroot%\System32\lsass.exe`

#### <a name="dhcp-server-exclusions"></a>BUDT Sunucu dışlamaları

Bu bölümde, THE THE SERVER rolünü yüklemenizle otomatik olarak teslim edilen dışlamalar listelenir. WM Server dosya konumları, kayıt defteri anahtarında *DatabasePath*, *WmLogFilePath* ve *BackupDatabasePath* parametreleriyle belirtilir `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\DHCPServer\Parameters`

- `%systemroot%\System32\DHCP\*\*.mdb`
- `%systemroot%\System32\DHCP\*\*.pat`
- `%systemroot%\System32\DHCP\*\*.log`
- `%systemroot%\System32\DHCP\*\*.chk`
- `%systemroot%\System32\DHCP\*\*.edb`

#### <a name="dns-server-exclusions"></a>DNS Sunucusu dışlamaları

Bu bölümde, DNS Sunucusu rolünü yüklemenize göre otomatik olarak teslim edilen dosya ve klasör dışlamaları ve süreç dışlamaları listelenir.

##### <a name="file-and-folder-exclusions-for-the-dns-server-role"></a>DNS Sunucusu rolü için dosya ve klasör dışlamaları

- `%systemroot%\System32\Dns\*\*.log`
- `%systemroot%\System32\Dns\*\*.dns`
- `%systemroot%\System32\Dns\*\*.scc`
- `%systemroot%\System32\Dns\*\BOOT`

##### <a name="process-exclusions-for-the-dns-server-role"></a>DNS Sunucusu rolü için süreç dışlamaları

- `%systemroot%\System32\dns.exe`

#### <a name="file-and-storage-services-exclusions"></a>Dosya ve Depolama Hizmetleri dışlamaları

Bu bölümde, Dosya ve Özel Hizmetler rolünü yük olduğunda otomatik olarak teslim edilen dosya ve klasör Depolama listelenir. Aşağıda listelenen dışlamalar, Kümeleme rolü için dışlamaları içermemektedir.

- `%SystemDrive%\ClusterStorage`
- `%clusterserviceaccount%\Local Settings\Temp`
- `%SystemDrive%\mscs`

#### <a name="print-server-exclusions"></a>Print Server dışlamaları

Bu bölümde, Print Server rolünü yüklemenize göre otomatik olarak teslim edilen dosya türü dışlamaları, klasör dışlamaları ve süreç dışlamaları listelenir.

##### <a name="file-type-exclusions"></a>Dosya türü dışlamaları

- `*.shd`
- `*.spl`

##### <a name="folder-exclusions"></a>Klasör dışlamaları

Bu klasör kayıt defteri anahtarında belirtilir `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Print\Printers\DefaultSpoolDirectory`

- `%system32%\spool\printers\*`

##### <a name="process-exclusions"></a>İşlem dışlamaları

- `spoolsv.exe`

#### <a name="web-server-exclusions"></a>Web Server dışlamaları

Bu bölümde, Web Server rolünü yüklemenize göre otomatik olarak teslim edilen klasör dışlamaları ve süreç dışlamaları listelenir.

##### <a name="folder-exclusions"></a>Klasör dışlamaları

- `%SystemRoot%\IIS Temporary Compressed Files`
- `%SystemDrive%\inetpub\temp\IIS Temporary Compressed Files`
- `%SystemDrive%\inetpub\temp\ASP Compiled Templates`
- `%systemDrive%\inetpub\logs`
- `%systemDrive%\inetpub\wwwroot`

##### <a name="process-exclusions"></a>İşlem dışlamaları

- `%SystemRoot%\system32\inetsrv\w3wp.exe`
- `%SystemRoot%\SysWOW64\inetsrv\w3wp.exe`
- `%SystemDrive%\PHP5433\php-cgi.exe`

##### <a name="turning-off-scanning-of-files-in-the-sysvolsysvol-folder-or-the-sysvol_dfsrsysvol-folder"></a>Sysvol\Sysvol klasöründe veya Sysvol klasöründeki veya SYSVOL_DFSR\Sysvol klasöründe dosya taramayı kapatma

Veya klasörün ve tüm `Sysvol\Sysvol` alt `SYSVOL_DFSR\Sysvol` klasörlerin geçerli konumu, çoğaltma kümesi kökünün dosya sistemi yenidenparse hedefidir. Ve `Sysvol\Sysvol` klasörler `SYSVOL_DFSR\Sysvol` varsayılan olarak aşağıdaki konumları kullanır:

- `%systemroot%\Sysvol\Domain`
- `%systemroot%\Sysvol_DFSR\Domain`

Şu anda etkin olan yola `SYSVOL` NETLOGON paylaşımı başvurur ve aşağıdaki alt anahtarda SysVol değer adı tarafından belirlen olabilir: `HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Services\Netlogon\Parameters`

Aşağıdaki dosyaları bu klasörden ve tüm alt klasörlerinden dışla:

- `*.adm`
- `*.admx`
- `*.adml`
- `Registry.pol`
- `Registry.tmp`
- `*.aas`
- `*.inf`
- `Scripts.ini`
- `*.ins`
- `Oscfilter.ini`

#### <a name="windows-server-update-services-exclusions"></a>Windows Server Update Services dışlamaları

Bu bölümde, sunucu Sunucu Güncelleştirme Hizmetleri (WSUS) rolünü Windows olarak teslim edilen klasör dışlamaları listelenir. WSUS klasörü kayıt defteri anahtarında belirtilir `HKEY_LOCAL_MACHINE\Software\Microsoft\Update Services\Server\Setup`

- `%systemroot%\WSUS\WSUSContent`
- `%systemroot%\WSUS\UpdateServicesDBFiles`
- `%systemroot%\SoftwareDistribution\Datastore`
- `%systemroot%\SoftwareDistribution\Download`

## <a name="opting-out-of-automatic-exclusions"></a>Otomatik dışlamaları devre dışı bırakma

Daha Windows Server 2016 sonra, Güvenlik zekası güncelleştirmeleri tarafından teslim edilen önceden tanımlanmış dışlamalar yalnızca bir rol veya özelliğin varsayılan yollarını dışarıda bırakmaktadır. Özel bir yola rol veya özellik yüklemiş veya dışlama kümelerini el ile kontrol etmek istiyorsanız, Security Intelligence güncelleştirmelerinde teslim edilen otomatik dışlamaları devre dışı bırakmayı tercih edin. Ama, teslim edilen dışlamaların otomatik olarak en iyi duruma Windows Server 2016 unutmayın. [Dışlama Öneriler tanımlamadan önce dışlamaları](configure-exclusions-microsoft-defender-antivirus.md#recommendations-for-defining-exclusions) tanımlama hakkında daha fazla bilgi için bkz.

> [!WARNING]
> Otomatik dışlamaları devre dışı bırakma, performansı olumsuz etkileyebilir veya verilerin bozulmasına neden olabilir. Otomatik olarak teslim edilen dışlamalar Windows Server 2016, Windows Server 2019 ve Windows Server 2022 rolleri için en iyi duruma getirilmiş.

Önceden tanımlı dışlamalar yalnızca varsayılan yolları dışla **olduğundan,** NTDS ve SYSVOL klasörlerini özgün yoldan farklı bir başka sürücüye veya yola taşısanız *,* dışlamaları el ile eklemeniz gerekir. Bkz [. Klasör adı veya dosya uzantısına göre dışlama listesini yapılandırma](configure-extension-file-exclusions-microsoft-defender-antivirus.md#configure-the-list-of-exclusions-based-on-folder-name-or-file-extension).

Grup İlkesi, PowerShell cmdlet'leri ve WMI ile otomatik dışlama listelerini devre dışı abilirsiniz.

### <a name="use-group-policy-to-disable-the-auto-exclusions-list-on-windows-server-2016-windows-server-2019-and-windows-server-2022"></a>Windows Server 2016, Windows Server 2022 ve Windows'da otomatik dışlamalar listesini devre dışı bırakmak için Grup İlkesi kullanma

1. Grup İlkesi yönetim bilgisayarınızda Grup İlkesi [Yönetim Konsolu'nu açın](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc725752(v=ws.11)). Yapılandırmak istediğiniz Grup İlkesi Nesnesi'ne sağ tıklayın ve Düzenle'yi **seçin**.

2. Grup İlkesi **Yönetim Düzenleyicisi'nde Bilgisayar** **yapılandırması'ne gidin ve** Yönetim **şablonları'ı seçin**.

3. Dışlamalar'da **bileşenleri Windows için** \> **Microsoft Defender Virüsten Koruma** \> **genişletin**.

4. Otomatik **Dışlamaları Kapat'a çift** tıklayın ve seçeneği Etkin olarak **ayarlayın**. Sonra **Tamam**’ı seçin.

### <a name="use-powershell-cmdlets-to-disable-the-auto-exclusions-list-on-windows-server"></a>Windows Server'da otomatik dışlamalar listesini devre dışı bırakmak için PowerShell cmdlet'lerini kullanma

Aşağıdaki cmdlet'leri kullanın:

```PowerShell
Set-MpPreference -DisableAutoExclusions $true
```

Daha fazla bilgi edinmek için aşağıdaki kaynaklara bakın:

- [PowerShell cmdlet'lerini kullanarak bu cmdlet'leri Microsoft Defender Virüsten Koruma](use-powershell-cmdlets-microsoft-defender-antivirus.md).
- [PowerShell'i Microsoft Defender Virüsten Koruma](/powershell/module/defender/).

### <a name="use-windows-management-instruction-wmi-to-disable-the-auto-exclusions-list-on-windows-server"></a>Windows Windows Server'da otomatik dışlamalar listesini devre dışı bırakmak için Dışlama Yönetimi Yönergesi'Windows kullanma

Aşağıdaki **özellikler** için [sınıf MSFT_MpPreference](/previous-versions/windows/desktop/defender/msft-mppreference) Set yöntemini kullanın:

```WMI
DisableAutoExclusions
```

Daha fazla bilgi ve izin verilen parametreler için aşağıdakilere bakın:

- [Windows Defender WMIv2 API'leri](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal)

## <a name="defining-custom-exclusions"></a>Özel dışlamaları tanımlama

Gerekirse, özel dışlamaları ekleyebilir veya kaldırsanız bile. Bunu yapmak için aşağıdaki makalelere bakın:

- [Dosya adı, uzantı ve klasör konumu temel alarak dışlamaları yapılandırma ve doğrulama](configure-extension-file-exclusions-microsoft-defender-antivirus.md)
- [İşlemler tarafından açılan dosyalar için dışlamaları yapılandırma ve doğrulama](configure-process-opened-file-exclusions-microsoft-defender-antivirus.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Taramalar için dışlamaları yapılandırma Microsoft Defender Virüsten Koruma doğrulama](configure-exclusions-microsoft-defender-antivirus.md)
- [Dosya adı, uzantı ve klasör konumu temel alarak dışlamaları yapılandırma ve doğrulama](configure-extension-file-exclusions-microsoft-defender-antivirus.md)
- [İşlemler tarafından açılan dosyalar için dışlamaları yapılandırma ve doğrulama](configure-process-opened-file-exclusions-microsoft-defender-antivirus.md)
- [Dışlamaları tanımlarken kaçınılması gereken yaygın hatalar](common-exclusion-mistakes-microsoft-defender-antivirus.md)
- [Bu taramaları ve düzeltmeleri sonucunda Microsoft Defender Virüsten Koruma, başlatma ve gözden geçirme](customize-run-review-remediate-scans-microsoft-defender-antivirus.md)
- [Microsoft Defender Virüsten Koruma'da Windows 10](microsoft-defender-antivirus-in-windows-10.md)
