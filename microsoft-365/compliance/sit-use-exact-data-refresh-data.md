---
title: Tam veri duyarlıksız bilgi kaynak tablo dosyanızı yenileme
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.date: ''
localization_priority: Normal
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Hassas bilgi kaynağı tablo dosyanızı yenileyin.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 14ef2997da92e0f902fd757a3cbff2735fdeada5
ms.sourcegitcommit: 966344e1aa442a4d10a0fb05f56badd38c833bb2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/19/2022
ms.locfileid: "63015567"
---
# <a name="refresh-your-exact-data-match-sensitive-information-source-table-file"></a>Hassas bilgiler kaynak tablo dosyasıyla tam olarak eşlene verilerinizi yenileme 

Hassas bilgi veritabanınızı her 24 saatte bir 5 kez yenileyin. Hassas bilgi kaynağı tabloyu yeniden yüklemek ve yeniden yüklemek zorundasınız.

1. Hassas verileri Microsoft Excel gibi bir uygulamaya yeniden aktarın ve dosyayı .csv, .tsv biçiminde veya boru (|) ayrılmış biçimde kaydedin. Daha önce karmata bulundurarak dosyayı karşıya yüklerken, aynı dosya adını ve konumunu kullanın. Hassas verilerinizi [dışarı aktarma ve doğru](sit-get-started-exact-data-match-export-data.md#export-source-data-for-exact-data-match-based-sensitive-information-type) biçime dönüştürmeyle ilgili ayrıntılar için Bkz. Temel alınan hassas bilgi türüyle tam olarak eşleşiyor veri için kaynak verileri dışarı aktarma.

      > [!NOTE]
      > Hassas bilgi kaynağı tablo dosyasının yapısında (alan adları) hiçbir değişiklik yoksa, verileri yenilerken veritabanı şema dosyanız üzerinde herhangi bir değişiklik yapmak zorunda olmazsınız. Ancak değişiklik yapmak zorundaysanız, veritabanı şemasını ve kural paketinizi buna uygun şekilde düzenlemeyi de sağlarsınız. Bir [şemayı düzenleme veya kaldırma adımları için](sit-use-exact-data-manage-schema.md#manage-your-exact-data-match-schema) bkz. Tam veri eşleşme şemanızı yönetme. EDM SIT/rule paketinizi düzenleme veya kaldırma adımları için bkz. Hassas bilgi [türüne/](sit-get-started-exact-data-match-create-rule-package.md#create-exact-data-match-sensitive-information-typerule-package) kural paketine tam olarak uygun veri oluşturma.

2. Karma'daki [yordamları kullanın ve hassas bilgiler tablosu kaynak](sit-get-started-exact-data-match-hash-upload.md#hash-and-upload-the-sensitive-information-source-table-for-exact-data-match-sensitive-information-types) dosyanızı karşıya yüklemek üzere hassas bilgiler kaynağı tablosuna hassas bilgilerle tam olarak uygun olan bilgiler için kaynak tabloyu karşıya yükleyin.

2. Görev [Zamanlayıcı'yı kullanarak Karma'yı](/windows/desktop/TaskSchd/task-scheduler-start-page) otomatik hale yükleyebilir ve hassas bilgi türleri yordamı için hassas bilgi kaynağı tablosuna [tam olarak uygun olan bilgileri karşıya yükleyebilirsiniz](sit-get-started-exact-data-match-hash-upload.md#hash-and-upload-the-sensitive-information-source-table-for-exact-data-match-sensitive-information-types) . Çeşitli yöntemler kullanarak görevleri zamanabilirsiniz:

   |Yöntem|Ne yapmalı?|
   |---|---|
   |Windows PowerShell|Bu makalede [scheduledTasks belgelerine](/powershell/module/scheduledtasks/) [ve örnek PowerShell](#example-powershell-script-for-task-scheduler) betiğine bakın|
   |Görev Zamanlayıcı API'si|Görev Zamanlayıcı [belgelerine](/windows/desktop/TaskSchd/using-the-task-scheduler) bakın|
   |Windows arabirimi|Görev Windows'de **Başlat'a** tıklayın ve Görev Zamanlayıcı yazın. Ardından sonuç listesinde Görev Zamanlayıcı'ya **sağ tıklayın ve** Yönetici olarak **çalıştır'ı seçin**.|

### <a name="example-powershell-script-for-task-scheduler"></a>Görev Zamanlayıcı için Örnek PowerShell betiği 

Bu bölümde, verilerinize karma oluşturma ve karma veri yükleme görevlerini zamanlamayı gerçekleştirmek için kullanabileceğiniz örnek bir PowerShell betiği yer almaktadır:

#### <a name="schedule-hashing-and-upload-in-a-combined-step"></a>Karma sağlama ve karşıya yükleme adımlarını birleştirilmiş bir adımda zamanlama

```powershell
param(\[string\]$dataStoreName,\[string\]$fileLocation)
\# Assuming current user is also the user context to run the task
$user = "$env:USERDOMAIN\\$env:USERNAME"
$edminstallpath = 'C:\\Program Files\\Microsoft\\EdmUploadAgent\\'
$edmuploader = $edminstallpath + 'EdmUploadAgent.exe'
$csvext = '.csv'
$schemaext = '.xml'
\# Assuming file name is same as data store name and file is in .csv format
$dataFile = "$fileLocation\\$dataStoreName$csvext"
\# Assuming location to store hash file is same as the location of csv file
$hashLocation = $fileLocation
\# Assuming Schema file name is same as data store name
$schemaFile = "$fileLocation\\$dataStoreName$schemaext"
$uploadDataArgs = '/UploadData /DataStoreName ' + $dataStoreName + ' /DataFile ' + $dataFile + ' /HashLocation' + $hashLocation + ' /Schema ' + $schemaFile
\# Set up actions associated with the task
$actions = @()
$actions += New-ScheduledTaskAction -Execute $edmuploader -Argument $uploadDataArgs -WorkingDirectory $edminstallpath
\# Set up trigger for the task
$trigger = New-ScheduledTaskTrigger -Weekly -DaysOfWeek Sunday -At 2am
\# Set up task settings
$principal = New-ScheduledTaskPrincipal -UserId $user -LogonType S4U -RunLevel Highest
$settings = New-ScheduledTaskSettingsSet -RunOnlyIfNetworkAvailable -StartWhenAvailable -WakeToRun
\# Create the scheduled task
$scheduledTask = New-ScheduledTask -Action $actions -Principal $principal -Trigger $trigger -Settings $settings
\# Get credentials to run the task
$creds = Get-Credential -UserName $user -Message "Enter credentials to run the task"
$password=\[Runtime.InteropServices.Marshal\]::PtrToStringAuto(\[Runtime.InteropServices.Marshal\]::SecureStringToBSTR($creds.Password))
\# Register the scheduled task
$taskName = 'EDMUpload\_' + $dataStoreName
Register-ScheduledTask -TaskName $taskName -InputObject $scheduledTask -User $user -Password $password
```

#### <a name="schedule-hashing-and-upload-as-separate-steps"></a>Karma sağlama ve karşıya yükleme adımlarını ayrı adımlar olarak zamanlama

```powershell
param(\[string\]$dataStoreName,\[string\]$fileLocation)
\# Assuming current user is also the user context to run the task
$user = "$env:USERDOMAIN\\$env:USERNAME"
$edminstallpath = 'C:\\Program Files\\Microsoft\\EdmUploadAgent\\'
$edmuploader = $edminstallpath + 'EdmUploadAgent.exe'
$csvext = '.csv'
$edmext = '.EdmHash'
$schemaext = '.xml'
\# Assuming file name is same as data store name and file is in .csv format
$dataFile = "$fileLocation\\$dataStoreName$csvext"
$hashFile = "$fileLocation\\$dataStoreName$edmext"
\# Assuming Schema file name is same as data store name
$schemaFile = "$fileLocation\\$dataStoreName$schemaext "

\# Assuming location to store hash file is same as the location of csv file
$hashLocation = $fileLocation
$createHashArgs = '/CreateHash' + ' /DataFile ' + $dataFile + ' /HashLocation ' + $hashLocation + ' /Schema ' + $schemaFile
$uploadHashArgs = '/UploadHash /DataStoreName ' + $dataStoreName + ' /HashFile ' + $hashFile
\# Set up actions associated with the task
$actions = @()
$actions += New-ScheduledTaskAction -Execute $edmuploader -Argument $createHashArgs -WorkingDirectory $edminstallpath
$actions += New-ScheduledTaskAction -Execute $edmuploader -Argument $uploadHashArgs -WorkingDirectory $edminstallpath
\# Set up trigger for the task
$trigger = New-ScheduledTaskTrigger -Weekly -DaysOfWeek Sunday -At 2am
\# Set up task settings
$principal = New-ScheduledTaskPrincipal -UserId $user -LogonType S4U -RunLevel Highest
$settings = New-ScheduledTaskSettingsSet -RunOnlyIfNetworkAvailable -StartWhenAvailable -WakeToRun
\# Create the scheduled task
$scheduledTask = New-ScheduledTask -Action $actions -Principal $principal -Trigger $trigger -Settings $settings
\# Get credentials to run the task
$creds = Get-Credential -UserName $user -Message "Enter credentials to run the task"
$password=\[Runtime.InteropServices.Marshal\]::PtrToStringAuto(\[Runtime.InteropServices.Marshal\]::SecureStringToBSTR($creds.Password))
\# Register the scheduled task
$taskName = 'EDMUpload\_' + $dataStoreName
Register-ScheduledTask -TaskName $taskName -InputObject $scheduledTask -User $user -Password $password
```
