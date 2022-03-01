---
title: Tanılama günlükleri
description: Sorun giderme sırasında cihazlardan toplanan günlükler ve bunların nasıl depolandığı
keywords: Microsoft Yönetilen Masaüstü, Microsoft 365, hizmet, belgeler
ms.service: m365-md
author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.author: tiaraquan
manager: dougeby
ms.topic: article
ms.openlocfilehash: 808ce2e426a0540c95195f26c9872f569e595715
ms.sourcegitcommit: 559df2c86a7822463ce0597140537bab260c746a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/15/2022
ms.locfileid: "63015300"
---
# <a name="diagnostic-logs"></a>Tanılama günlükleri

İster bir sorun ister hizmetimiz tarafından tanımlanan bir sorun bildirsin, kullanıcıdan müdahale olmadan cihazdan bazı tanılama günlüklerini toplamamız gerekiyor olabilir.

Kullanıcı tarafından oluşturulan hiçbir içeriği veya kullanıcı dizinlerinden bilgi toplamaz. Yalnızca cihaz sistem durumu ve durumuyla ilgili tanılama ve günlük verileri toplıyoruz.

Toplanan günlükler 28 gün boyunca depolanıyor ve sonra silinıyor. Veri işleme standartlarımıza uygun olarak bir cihazdan toplanan [günlük işlemlerini gerçekleştiriz](privacy-personal-data.md).

## <a name="data-collected"></a>Toplanan veriler

Aşağıdaki liste Microsoft Yönetilen Masaüstü'ne tanılama günlüklerini toplayan tüm klasörleri, olay günlüklerini, yürütülebilir dosyaları veya kayıt defteri konumlarını içerir. Toplanan gerçek veriler bu listenin bir alt kümesi olur ve tanımlanan soruna bağlıdır.

### <a name="registry-keys"></a>Kayıt defteri anahtarları

- HKLMSYSTEMCurrentControlSetServices\\\\\\
- HKLMSOFTWAREMicrosoftSurface\\\\\\
- HKLMSOFTWAREPoliciesMicrosoft\\\\\\\\ Windows\\ WindowsUpdate
- HKLMSYSTEMCurrentControlSetControlMUIUILanguages\\\\\\\\\\
- HKLMSoftwarePoliciesMicrosoftWindowsStore\\\\\\\\
- HKLMSoftwareMicrosoft\\\\\\ Windows\\ CurrentVersionWindowsStoreWindowsUpdate\\\\
- HKLMSOFTWAREMicrosoft\\\\\\ Windows NT\\ CurrentVersion
- HKLMSOFTWAREMicrosoft\\\\\\ Windows NT\\ CurrentVersion
- HKLMSOFTWAREMicrosoft\\\\\\ Windows\\ CurrentVersionAppModel\\
- HKLMSYSTEMCurrentControlSetControlFirmwareResources\\\\\\\\
- HKLMSOFTWAREMicrosoftWindowsSelfhost\\\\\\
- HKLMSOFTWAREMicrosoftWindowsUpdate\\\\\\
- HKLMSOFTWAREMicrosoft\\\\\\ Windows\\ CurrentVersionAppx\\
- HKLMSOFTWAREMicrosoft\\\\\\ Windows NT\\ CurrentVersionSuperfetch\\
- HKLMSYSTEMSetup\\\\
- HKLMSoftwareMicrosoftIntuneManagementExtension\\\\\\
- HKLMSOFTWAREMicrosoftSystemCertificatesAuthRoot\\\\\\\\
- HKLMSOFTWAREMicrosoft\\\\\\ Windows Gelişmiş Tehdit Koruması
- HKLMSOFTWAREMicrosoft\\\\\\ Windows\\ CurrentVersionAuthenticationLogonUI\\\\
- HKLMSOFTWAREMicrosoft\\\\\\ Windows\\ CurrentVersionInternet\\ Ayarlar
- HKLMSoftwareMicrosoft\\\\\\ Windows\\ CurrentVersionUninstall\\
- HKLMSoftwarePolicies\\\\
- HKLMSOFTWAREPoliciesMicrosoftCryptographyConfigurationSSL\\\\\\\\\\\\
- HKLMSOFTWAREPoliciesMicrosoft\\\\\\\\ Windows Gelişmiş Tehdit Koruması
- HKLMSOFTWAREWOW6432NodeMicrosoft\\\\\\\\ Windows\\ CurrentVersionUninstall\\
- HKLMSYSTEMCurrentControlSetControlSecurityProvidersSCHANNEL\\\\\\\\\\

### <a name="commands"></a>Komutlar

- %programfiles%\\windows defender\\mpcmdrun.exe -GetFiles
- %windir%\\system32\\certutil.exe -store
- %windir%\\system32\\certutil.exe -store -user my
- %windir%\\system32\\Dsregcmd.exe /status
- %windir%\\system32\\ipconfig.exe /all
- %windir%\\system32\\ipconfig.exe /displaydns
- %windir%\\system32\\mdmdiagnosticstool.exe
- %windir%\\system32\\msinfo32.exe report %temp%\\MDMDiagnosticsmsinfo32.log\\
- %windir%\\system32\\netsh.exe advfirewall show allprofiles
- %windir%\\system32\\netsh.exe advfirewall show global
- %windir%\\system32\\netsh.exe lan show profilleri
- %windir%\\system32\\netsh.exe winhttp show proxy
- %windir%\\system32\\netsh.exe wlan show profiles
- %windir%\\system32\\netsh.exe wlanreport göster
- %windir%\\system32\\ping.exe -n 50 localhost
- %windir%\\system32\\powercfg.exe/batteryreport /output %temp%\\MDMDiagnostics\\battery-report.html
- %windir%\\system32\\powercfg.exe /energy /output %temp%\\MDMDiagnostics\\energy-report.html
- bitsadmin /list /allusers /verbose
- fltMC.exe
- bcdedit /enum all /v
- manage-bde -kullanıcı- get
- Windows PowerShell komutları:
    - Get-appxpackage -allusers
    - Get-appxpackage -packagetype paketi
    - Get-Service wuauserv
    - Get-NetFirewallRule
    - Get-WmiObject -Class win32product\_
    - Get-ComputerInfo
    - Get-Service
    - Get-Process
    - Get-WmiObject Win32PnPSignedDriver\_

### <a name="event-logs"></a>Olay günlükleri

- Uygulama
- Microsoft-Windows-AppLocker/EXE ve DLL
- Microsoft-Windows-AppLocker/MSI ve Script
- Microsoft-Windows-AppLocker/Packaged app-Deployment
- Microsoft-Windows-AppLocker/Packaged app-Execution
- Microsoft-Windows-Bitlocker/Bitlocker Yönetimi
- Microsoft-Windows-SENSE/İşlem
- Microsoft-Windows-SenseIR/Operational
- Kurulum
- Sistem

### <a name="files"></a>Dosyalar

- %ProgramData%\\MicrosoftDiagnosticLogCSPCollectors.etl\\\\\\\*
- %ProgramData%\\MicrosoftIntuneManagementExtensionLogs\\\\\\\*.\*
- %ProgramData%\\Microsoft\\ Windows Defender\\ Support\\MpSupportFiles.cab
- %ProgramData%\\Microsoft\\ Windows\\ WlanReport\\wlan-report-latest.html
- %ProgramData%\\Microsoft\\ Windows\\ WlanReport -SourceFileName wlan-report-latest.html
- %windir%\\ccmlogs.log\\\*
- %windir%\\ccmsetuplogs.log\\\*
- %windir%\\logsCBScbs.log\\\\
- %windir%\\logsmeasuredboot\*\\.\*
- %windir%\\LogsWindowsUpdate.etl\\\*
- %windir%\\inf.log\\\*
- %windir%\\servicingsessions\\\\ActionList.xml
- %windir%\\servicingsessions\\\\Sessions.xml
- %windir%\\SoftwareDistributionDataStoreLogsedb.log\\\\\\
- %windir%\\SoftwareDistributionDataStoreDataStore.edb\\\\
- %windir%\\logsdismdism.log\\\\
- %SystemRoot%\\System32WinevtLogs\\\\\\
- %appdata%\\Microsoft\\ Teams\\ media-stack.blog\\\*
- %appdata%\\Microsoft\\ Teams\\ skylib.blog\\\*
- %appdata%\\Microsoft\\ Teams\\ media-stack.etl\\\*
- %appdata%\\Microsoft\\ Teams\\logs.txt
- %windir%\\Windows System32winevt\\\\\*.\\\*