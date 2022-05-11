---
title: Windows Sunucusu'nda Microsoft Defender Virüsten Koruma dışlamalarını yapılandırma
ms.reviewer: pahuijbr
manager: dansimp
description: Windows Sunucusu, sunucu rolüne göre otomatik dışlamalar içerir. Özel dışlamalar da ekleyebilirsiniz.
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
ms.collection: M365-security-compliance
ms.openlocfilehash: 890be814be75c303aa42feb5cb7a16cb4f5c3bd9
ms.sourcegitcommit: 7dc7e9fd76adf848f941919f86ca25eecc704015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/11/2022
ms.locfileid: "65320650"
---
# <a name="configure-microsoft-defender-antivirus-exclusions-on-windows-server"></a>Windows Sunucusu'nda Microsoft Defender Virüsten Koruma dışlamalarını yapılandırma


**Şunlar için geçerlidir:**

- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Microsoft Defender Virüsten Koruma

**Platform**
- Windows

Windows Server 2016 ve Windows Server 2019'da Microsoft Defender Virüsten Koruma, belirttiğiniz sunucu rolü tarafından tanımlandığı gibi sizi otomatik olarak belirli dışlamalara kaydeder. Bu dışlamalar[, Windows Güvenliği uygulamasında](microsoft-defender-security-center-antivirus.md) gösterilen standart dışlama listelerinde görünmez.

Sunucu rol tanımlı otomatik dışlamalara ek olarak, özel dışlamalar ekleyebilir veya kaldırabilirsiniz. Bunu yapmak için şu makalelere bakın:
- [Dosya adı, uzantı ve klasör konumuna göre dışlamaları yapılandırma ve doğrulama](configure-extension-file-exclusions-microsoft-defender-antivirus.md)
- [İşlemler tarafından açılan dosyalar için dışlamaları yapılandırma ve doğrulama](configure-process-opened-file-exclusions-microsoft-defender-antivirus.md)

## <a name="a-few-points-to-keep-in-mind"></a>Akılda tutulması gereken birkaç nokta

- Özel dışlamalar otomatik dışlamalardan önceliklidir.
- Otomatik dışlamalar yalnızca [gerçek zamanlı koruma (RTP)](configure-protection-features-microsoft-defender-antivirus.md) tarama için geçerlidir. 
- Otomatik dışlamalar [tam, hızlı veya isteğe bağlı tarama](schedule-antivirus-scans.md#quick-scan-full-scan-and-custom-scan) sırasında kabul edilmez.
- Özel ve yinelenen dışlamalar otomatik dışlamalarla çakışmaz.
- Microsoft Defender Virüsten Koruma, bilgisayarınızda hangi rollerin yüklü olduğunu belirlemek için Dağıtım Görüntüsü Bakımı ve Yönetimi (DISM) araçlarını kullanır.
- İşletim sistemine dahil olmayan yazılımlar için uygun dışlamalar ayarlanmalıdır.
- Windows Server 2012 R2, yüklenebilir bir özellik olarak Microsoft Defender Virüsten Koruma sahip değildir. Bu sunucuları Uç Nokta için Defender'a eklediğinizde, Windows Defender Virüsten Koruma yüklersiniz ve işletim sistemi dosyaları için varsayılan dışlamalar uygulanır. Ancak, sunucu rolleri için dışlamalar (aşağıda belirtildiği gibi) otomatik olarak uygulanmaz ve bu dışlamaları uygun şekilde yapılandırmanız gerekir. Daha fazla bilgi için bkz. [Windows sunucularını Uç Nokta için Microsoft Defender hizmetine ekleme](configure-server-endpoints.md).

Bu makalede, Windows Server 2016 veya sonraki sürümlerde Microsoft Defender Virüsten Koruma için dışlamalara genel bir bakış sağlanır.

Microsoft Defender Virüsten Koruma Windows Server 2016 ve sonraki sürümlerde yerleşik olduğundan, işletim sistemi dosyaları ve sunucu rolleri için dışlamalar otomatik olarak gerçekleşir. Ancak özel dışlamalar tanımlayabilirsiniz. Gerekirse otomatik dışlamaları da geri çevirebilirsiniz.

Bu makale aşağıdaki bölümleri içerir:

|Bölüm|Açıklama|
|---|---|
|[Windows Server 2016 veya sonraki sürümlerde otomatik dışlamalar](#automatic-exclusions-on-windows-server-2016-or-later)|İki ana otomatik dışlama türünü açıklar ve otomatik dışlamaların ayrıntılı bir listesini içerir|
|[Otomatik dışlamaları geri çevirme](#opting-out-of-automatic-exclusions)|Otomatik dışlamaları geri çevirmeyi açıklayan önemli noktalar ve yordamlar içerir|
|[Özel dışlamaları tanımlama](#defining-custom-exclusions)|Özel dışlamaları tanımlamaya yönelik nasıl yapılır bilgilerine bağlantılar sağlar|

## <a name="automatic-exclusions-on-windows-server-2016-or-later"></a>Windows Server 2016 veya sonraki sürümlerde otomatik dışlamalar

Windows Server 2016 veya sonraki sürümlerde aşağıdaki dışlamaları tanımlamanız gerekmez:

- İşletim sistemi dosyaları
- Sunucu rolleri ve sunucu rolleri aracılığıyla eklenen tüm dosyalar

Microsoft Defender Virüsten Koruma yerleşik olduğundan, Windows Server 2016 veya sonraki sürümlerde işletim sistemi dosyaları için dışlama gerektirmez. Ayrıca, Windows Server 2016 veya üzerini çalıştırıp bir rol yüklediğinizde, Microsoft Defender Virüsten Koruma sunucu rolü için otomatik dışlamaları ve rolü yüklerken eklenen dosyaları içerir.

İşletim sistemi dışlamaları ve sunucu rolü dışlamaları[, Windows Güvenliği uygulamasında](microsoft-defender-security-center-antivirus.md) gösterilen standart dışlama listelerinde görünmez.

> [!NOTE]
> Sunucu rolleri ve işletim sistemi dosyaları için otomatik dışlamalar Windows Server 2012 için geçerli değildir. R2 Windows Server 2012 çalıştıran sunucularınız Uç Nokta için Defender'a eklendiyse otomatik dışlamalar uygulanabilir. (Bkz[. Windows sunucularını Uç Nokta için Microsoft Defender hizmetine ekleme](configure-server-endpoints.md).)


### <a name="the-list-of-automatic-exclusions"></a>Otomatik dışlamaların listesi

Aşağıdaki bölümlerde, otomatik dışlama dosya yolları ve dosya türleriyle birlikte sunulan dışlamalar yer alır.

#### <a name="default-exclusions-for-all-roles"></a>Tüm roller için varsayılan dışlamalar

Bu bölümde Windows Server 2016, Windows Server 2019 ve Windows Server 2022'deki tüm roller için varsayılan dışlamalar listelenmiştir.

> [!IMPORTANT]
> - Varsayılan konumlar, bu makalede açıklanan konumlardan farklı olabilir.
> - Windows özelliği veya sunucu rolü olarak dahil olmayan yazılımlar için dışlamalar ayarlamak için yazılım üreticisinin belgelerine bakın.

##### <a name="windows-tempedb-files"></a>"temp.edb" dosyalarını Windows

- `%windir%\SoftwareDistribution\Datastore\*\tmp.edb`
- `%ProgramData%\Microsoft\Search\Data\Applications\Windows\windows.edb`

##### <a name="windows-update-files-or-automatic-update-files"></a>dosyaları veya Otomatik Güncelleştirme dosyalarını Windows Update

- `%windir%\SoftwareDistribution\Datastore\*\Datastore.edb`
- `%windir%\SoftwareDistribution\Datastore\*\edb.chk`
- `%windir%\SoftwareDistribution\Datastore\*\edb\*.log`
- `%windir%\SoftwareDistribution\Datastore\*\Edb\*.jrs`
- `%windir%\SoftwareDistribution\Datastore\*\Res\*.log`

##### <a name="windows-security-files"></a>dosyaları Windows Güvenliği

- `%windir%\Security\database\*.chk`
- `%windir%\Security\database\*.edb`
- `%windir%\Security\database\*.jrs`
- `%windir%\Security\database\*.log`
- `%windir%\Security\database\*.sdb`

##### <a name="group-policy-files"></a>dosyaları grup ilkesi

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

- FRS hazırlama klasörü. Hazırlama klasörü kayıt defteri anahtarında belirtilir `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\NtFrs\Parameters\Replica Sets\GUID\Replica Set Stage`

  - `%systemroot%\Sysvol\*\Ntfrs_cmp*\`

- FRS önyükleme klasörü. Bu klasör, klasör tarafından belirtilir `Replica_root\DO_NOT_REMOVE_NtFrs_PreInstall_Directory`

  - `%systemroot%\SYSVOL\domain\DO_NOT_REMOVE_NtFrs_PreInstall_Directory\*\Ntfrs*\`

- Dağıtılmış Dosya Sistemi Çoğaltma (DFSR) veritabanı ve çalışma klasörleri. Bu klasörler kayıt defteri anahtarı tarafından belirtilir `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\DFSR\Parameters\Replication Groups\GUID\Replica Set Configuration File`

  > [!NOTE]
  > Özel konumlar için bkz. [Otomatik dışlamaları geri çevirme](#opting-out-of-automatic-exclusions).

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

Aşağıdaki tabloda, Hyper-V rolünü yüklediğinizde otomatik olarak teslim edilen dosya türü dışlamaları, klasör dışlamaları ve işlem dışlamaları listelenmiştir.

|Dışlama türü|Özellikleri|
|---|---|
|Dosya türleri|`*.vhd` <br/> `*.vhdx` <br/> `*.avhd` <br/> `*.avhdx` <br/> `*.vsv` <br/> `*.iso` <br/> `*.rct` <br/> `*.vmcx` <br/> `*.vmrs`|
|Klasörler|`%ProgramData%\Microsoft\Windows\Hyper-V` <br/> `%ProgramFiles%\Hyper-V` <br/> `%SystemDrive%\ProgramData\Microsoft\Windows\Hyper-V\Snapshots` <br/> `%Public%\Documents\Hyper-V\Virtual Hard Disks`|
|Süreç|`%systemroot%\System32\Vmms.exe` <br/> `%systemroot%\System32\Vmwp.exe`|

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

Bu bölümde, Active Directory Domain Services (AD DS) yüklediğinizde otomatik olarak teslim edilen dışlamalar listelenir.

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

##### <a name="process-exclusions-for-ad-ds-and-ad-ds-related-support-files"></a>AD DS ve AD DS ile ilgili destek dosyaları için işlem dışlamaları

- `%systemroot%\System32\ntfrs.exe`
- `%systemroot%\System32\lsass.exe`

#### <a name="dhcp-server-exclusions"></a>DHCP Sunucusu dışlamaları

Bu bölümde, DHCP Sunucusu rolünü yüklediğinizde otomatik olarak teslim edilen dışlamalar listelenir. DHCP Sunucusu dosya konumları kayıt defteri anahtarındaki *DatabasePath*, *DhcpLogFilePath* ve *BackupDatabasePath* parametreleri tarafından belirtilir `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\DHCPServer\Parameters`

- `%systemroot%\System32\DHCP\*\*.mdb`
- `%systemroot%\System32\DHCP\*\*.pat`
- `%systemroot%\System32\DHCP\*\*.log`
- `%systemroot%\System32\DHCP\*\*.chk`
- `%systemroot%\System32\DHCP\*\*.edb`

#### <a name="dns-server-exclusions"></a>DNS Sunucusu dışlamaları

Bu bölümde, DNS Sunucusu rolünü yüklediğinizde otomatik olarak teslim edilen dosya ve klasör dışlamaları ve işlem dışlamaları listelenir.

##### <a name="file-and-folder-exclusions-for-the-dns-server-role"></a>DNS Sunucusu rolü için dosya ve klasör dışlamaları

- `%systemroot%\System32\Dns\*\*.log`
- `%systemroot%\System32\Dns\*\*.dns`
- `%systemroot%\System32\Dns\*\*.scc`
- `%systemroot%\System32\Dns\*\BOOT`

##### <a name="process-exclusions-for-the-dns-server-role"></a>DNS Sunucusu rolü için işlem dışlamaları

- `%systemroot%\System32\dns.exe`

#### <a name="file-and-storage-services-exclusions"></a>Dosya ve Depolama Hizmetleri dışlamaları

Bu bölümde, Dosya ve Depolama Hizmetleri rolünü yüklediğinizde otomatik olarak teslim edilen dosya ve klasör dışlamaları listelenir. Aşağıda listelenen dışlamalar Kümeleme rolü için dışlamalar içermez.

- `%SystemDrive%\ClusterStorage`
- `%clusterserviceaccount%\Local Settings\Temp`
- `%SystemDrive%\mscs`

#### <a name="print-server-exclusions"></a>Yazdırma Sunucusu dışlamaları

Bu bölümde, Yazdırma Sunucusu rolünü yüklediğinizde otomatik olarak teslim edilen dosya türü dışlamaları, klasör dışlamaları ve işlem dışlamaları listelenir.

##### <a name="file-type-exclusions"></a>Dosya türü dışlamaları

- `*.shd`
- `*.spl`

##### <a name="folder-exclusions"></a>Klasör dışlamaları

Bu klasör kayıt defteri anahtarında belirtilir `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Print\Printers\DefaultSpoolDirectory`

- `%system32%\spool\printers\*`

##### <a name="process-exclusions"></a>İşlem dışlamaları

- `spoolsv.exe`

#### <a name="web-server-exclusions"></a>Web Sunucusu dışlamaları

Bu bölümde, Web Sunucusu rolünü yüklediğinizde otomatik olarak teslim edilen klasör dışlamaları ve işlem dışlamaları listelenir.

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

##### <a name="turning-off-scanning-of-files-in-the-sysvolsysvol-folder-or-the-sysvol_dfsrsysvol-folder"></a>Sysvol\Sysvol klasöründeki veya SYSVOL_DFSR\Sysvol klasöründeki dosyaların taranmalarını kapatma

veya `SYSVOL_DFSR\Sysvol` klasörünün `Sysvol\Sysvol` ve tüm alt klasörlerin geçerli konumu, çoğaltma kümesi kökünün dosya sistemi yeniden ayrıştırma hedefidir. `Sysvol\Sysvol` ve `SYSVOL_DFSR\Sysvol` klasörleri varsayılan olarak aşağıdaki konumları kullanır:

- `%systemroot%\Sysvol\Domain`
- `%systemroot%\Sysvol_DFSR\Domain`

Şu anda etkin `SYSVOL` olan yola NETLOGON paylaşımı tarafından başvurulur ve aşağıdaki alt anahtardaki SysVol değer adıyla belirlenebilir: `HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Services\Netlogon\Parameters`

Aşağıdaki dosyaları bu klasörden ve tüm alt klasörlerinden hariç tutun:

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

Bu bölümde, Windows Server Update Services (WSUS) rolünü yüklediğinizde otomatik olarak teslim edilen klasör dışlamaları listelenir. WSUS klasörü kayıt defteri anahtarında belirtilir `HKEY_LOCAL_MACHINE\Software\Microsoft\Update Services\Server\Setup`

- `%systemroot%\WSUS\WSUSContent`
- `%systemroot%\WSUS\UpdateServicesDBFiles`
- `%systemroot%\SoftwareDistribution\Datastore`
- `%systemroot%\SoftwareDistribution\Download`

## <a name="opting-out-of-automatic-exclusions"></a>Otomatik dışlamaları geri çevirme

Windows Server 2016 ve sonraki sürümlerde, Güvenlik bilgileri güncelleştirmeleri tarafından sunulan önceden tanımlanmış dışlamalar yalnızca bir rol veya özellik için varsayılan yolları dışlar. Özel bir yola bir rol veya özellik yüklediyseniz veya dışlama kümesini el ile denetlemek istiyorsanız, Güvenlik bilgileri güncelleştirmelerinde sunulan otomatik dışlamaları geri çevirdiğinizden emin olun. Ancak otomatik olarak sunulan dışlamaların Windows Server 2016 ve üzeri için iyileştirildiğini unutmayın. [Dışlama listelerinizi tanımlamadan önce dışlamaları tanımlamak için](configure-exclusions-microsoft-defender-antivirus.md#recommendations-for-defining-exclusions) bkz. Öneriler.

> [!WARNING]
> Otomatik dışlamaları geri çevirmek performansı olumsuz etkileyebilir veya veri bozulmasına neden olabilir. Otomatik olarak sunulan dışlamalar Windows Server 2016, Windows Server 2019 ve Windows Server 2022 rolleri için iyileştirilmiştir.

Önceden tanımlanmış dışlamalar yalnızca **varsayılan yolları** dışladığından, NTDS ve SYSVOL klasörlerini *özgün yoldan farklı* bir sürücüye veya yola taşırsanız, dışlamaları el ile eklemeniz gerekir. Bkz [. Klasör adına veya dosya uzantısına göre dışlama listesini yapılandırma](configure-extension-file-exclusions-microsoft-defender-antivirus.md#configure-the-list-of-exclusions-based-on-folder-name-or-file-extension).

otomatik dışlama listelerini grup ilkesi, PowerShell cmdlet'leri ve WMI ile devre dışı bırakabilirsiniz.

### <a name="use-group-policy-to-disable-the-auto-exclusions-list-on-windows-server-2016-windows-server-2019-and-windows-server-2022"></a>Windows Server 2016, Windows Server 2019 ve Windows Server 2022'de otomatik dışlama listesini devre dışı bırakmak için grup ilkesi kullanın

1. grup ilkesi yönetim bilgisayarınızda [grup ilkesi Yönetim Konsolu'nu](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc725752(v=ws.11)) açın. Yapılandırmak istediğiniz grup ilkesi Nesnesine sağ tıklayın ve **düzenle'yi** seçin.

2. **grup ilkesi Yönetim Düzenleyicisi'nde** **Bilgisayar yapılandırması'na** gidin ve ardından **Yönetim şablonları'nı** seçin.

3. **Dışlamalar Microsoft Defender Virüsten Koruma bileşenleri** \> **Windows** \> için ağacı genişletin.

4. **Otomatik Dışlamaları Kapat'a** çift tıklayın ve seçeneği **Etkin** olarak ayarlayın. Sonra **Tamam**’ı seçin.

### <a name="use-powershell-cmdlets-to-disable-the-auto-exclusions-list-on-windows-server"></a>Windows Sunucusu'nda otomatik dışlama listesini devre dışı bırakmak için PowerShell cmdlet'lerini kullanma

Aşağıdaki cmdlet'leri kullanın:

```PowerShell
Set-MpPreference -DisableAutoExclusions $true
```

Daha fazla bilgi edinmek için aşağıdaki kaynaklara bakın:

- [Microsoft Defender Virüsten Koruma yapılandırmak ve çalıştırmak için PowerShell cmdlet'lerini kullanın](use-powershell-cmdlets-microsoft-defender-antivirus.md).
- [PowerShell'i Microsoft Defender Virüsten Koruma ile kullanın](/powershell/module/defender/).

### <a name="use-windows-management-instruction-wmi-to-disable-the-auto-exclusions-list-on-windows-server"></a>Windows Sunucusu'nda otomatik dışlama listesini devre dışı bırakmak için Windows Yönetim Yönergesi'ni (WMI) kullanın

Aşağıdaki özellikler için [MSFT_MpPreference](/previous-versions/windows/desktop/defender/msft-mppreference) sınıfının **Set** yöntemini kullanın:

```WMI
DisableAutoExclusions
```

Daha fazla bilgi ve izin verilen parametreler için aşağıdakilere bakın:

- [WMIv2 API'lerini Windows Defender](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal)

## <a name="defining-custom-exclusions"></a>Özel dışlamaları tanımlama

Gerekirse özel dışlamalar ekleyebilir veya kaldırabilirsiniz. Bunu yapmak için aşağıdaki makalelere bakın:

- [Dosya adı, uzantı ve klasör konumuna göre dışlamaları yapılandırma ve doğrulama](configure-extension-file-exclusions-microsoft-defender-antivirus.md)
- [İşlemler tarafından açılan dosyalar için dışlamaları yapılandırma ve doğrulama](configure-process-opened-file-exclusions-microsoft-defender-antivirus.md)

> [!TIP]
> Diğer platformlar için Virüsten Koruma ile ilgili bilgi edinmek isterseniz, bkz:
> - [MacOS'ta Uç Nokta için Microsoft Defender tercihlerini ayarlayın](mac-preferences.md)
> - [Mac'te Uç Nokta için Microsoft Defender](microsoft-defender-endpoint-mac.md)
> - [Intune için Microsoft Defender için macOS Virüsten Koruma ilke ayarları](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Linux'ta Uç Nokta için Microsoft Defender tercihlerini ayarlayın](linux-preferences.md)
> - [Linux'ta Uç Nokta için Microsoft Defender](microsoft-defender-endpoint-linux.md)
> - [Android özelliklerinde Uç Nokta için Defender’ı yapılandırın](android-configure.md)
> - [iOS özelliklerinde Uç Nokta için Microsoft Defender’ı yapılandırın](ios-configure-features.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Microsoft Defender Virüsten Koruma taramaları için dışlamaları yapılandırma ve doğrulama](configure-exclusions-microsoft-defender-antivirus.md)
- [Dosya adı, uzantı ve klasör konumuna göre dışlamaları yapılandırma ve doğrulama](configure-extension-file-exclusions-microsoft-defender-antivirus.md)
- [İşlemler tarafından açılan dosyalar için dışlamaları yapılandırma ve doğrulama](configure-process-opened-file-exclusions-microsoft-defender-antivirus.md)
- [Dışlamaları tanımlarken kaçınılması gereken yaygın hatalar](common-exclusion-mistakes-microsoft-defender-antivirus.md)
- [Microsoft Defender Virüsten Koruma taramalarının ve düzeltmelerinin sonuçlarını özelleştirme, başlatma ve gözden geçirme](customize-run-review-remediate-scans-microsoft-defender-antivirus.md)
- [Windows 10'da Microsoft Defender Virüsten Koruma](microsoft-defender-antivirus-in-windows-10.md)
