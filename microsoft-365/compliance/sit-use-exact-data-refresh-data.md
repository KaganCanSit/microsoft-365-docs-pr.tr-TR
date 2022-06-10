---
title: Hassas bilgi kaynağı tablo dosyasıyla tam olarak eşleşen verilerinizi yenileyin
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.date: ''
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Hassas bilgi kaynağı tablo dosyanızı yenileyin.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: a846f22b866b4b8adf75c44e55fde4b9d56b8ac4
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/10/2022
ms.locfileid: "66008855"
---
# <a name="refresh-your-exact-data-match-sensitive-information-source-table-file"></a>Hassas bilgi kaynağı tablo dosyasıyla tam olarak eşleşen verilerinizi yenileyin 

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Hassas bilgi veritabanınızı her 24 saat içinde en fazla 5 kez yenileyebilirsiniz. Hassas bilgi kaynağı tablonuzu yeniden oluşturmanız ve karşıya yüklemeniz gerekir.

1. Hassas verileri Microsoft Excel gibi bir uygulamaya yeniden aktarın ve dosyayı .csv, .tsv biçiminde veya kanal (|) sınırlandırılmış biçimde kaydedin. Dosyayı daha önce karma ve karşıya yüklerken kullandığınız dosya adını ve konumunu koruyun. Hassas verilerinizi dışarı aktarma ve doğru biçime alma ayrıntıları [için bkz. Tam veri eşleşmesi için kaynak verileri dışarı aktarma, hassas bilgi türüyle eşleşmektedir](sit-get-started-exact-data-match-export-data.md#export-source-data-for-exact-data-match-based-sensitive-information-type) .

      > [!NOTE]
      > Hassas bilgi kaynağı tablo dosyasının yapısında (alan adları) hiçbir değişiklik yoksa, verileri yenilerken veritabanı şema dosyanızda herhangi bir değişiklik yapmanız gerekmez. Ancak, değişiklik yapmanız gerekiyorsa veritabanı şemasını ve kural paketinizi uygun şekilde düzenlediğinizden emin olun. Bkz. Şemayı düzenleme veya kaldırma adımları için [tam veri eşleştirme şemanızı yönetme](sit-use-exact-data-manage-schema.md#manage-your-exact-data-match-schema) . EDM SIT/rule paketinizi düzenleme veya kaldırma adımları için bkz. [Hassas bilgi türü/kural paketiyle tam veri eşleştirmesi oluşturma](sit-get-started-exact-data-match-create-rule-package.md#create-exact-data-match-sensitive-information-typerule-package) .

2. Karma'daki yordamları kullanın [ve hassas bilgi tablonuzun kaynak dosyasını karşıya yüklemek üzere hassas bilgi türleriyle tam eşleşmesi için hassas](sit-get-started-exact-data-match-hash-upload.md#hash-and-upload-the-sensitive-information-source-table-for-exact-data-match-sensitive-information-types) bilgi kaynağı tablosunu karşıya yükleyin.

3. Karmayı otomatikleştirmek [ve hassas bilgi türleri yordamıyla tam veri eşleştirmesi için hassas bilgi kaynağı tablosunu karşıya yüklemek için](sit-get-started-exact-data-match-hash-upload.md#hash-and-upload-the-sensitive-information-source-table-for-exact-data-match-sensitive-information-types) [Görev Zamanlayıcı'yı](/windows/desktop/TaskSchd/task-scheduler-start-page) kullanabilirsiniz. Çeşitli yöntemler kullanarak görevleri zamanlayabilirsiniz:

   |Yöntem|Yapılması gerekenler|
   |---|---|
   |PowerShell|Bu makaledeki [ScheduledTasks](/powershell/module/scheduledtasks/) belgelerine ve [örnek PowerShell betiğine](#example-powershell-script-for-task-scheduler) bakın|
   |Görev Zamanlayıcı API'si|[Görev Zamanlayıcı](/windows/desktop/TaskSchd/using-the-task-scheduler) belgelerine bakın|
   |kullanıcı arabirimini Windows|Windows **, Başlat'a** tıklayın ve Görev Zamanlayıcı yazın. Ardından, sonuç listesinde **Görev Zamanlayıcı'ya** sağ tıklayın ve **Yönetici olarak çalıştır'ı** seçin.|

## <a name="example-powershell-script-for-task-scheduler"></a>Görev Zamanlayıcı için örnek PowerShell betiği

Bu bölüm, verileri karmalama ve karma verileri karşıya yükleme görevlerinizi zamanlamak için kullanabileceğiniz örnek bir PowerShell betiği içerir:

### <a name="schedule-hashing-and-upload-in-a-combined-step"></a>Karma oluşturma ve birleştirilmiş adımda karşıya yükleme zamanlama

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

### <a name="schedule-hashing-and-upload-as-separate-steps"></a>Karmayı zamanlama ve ayrı adımlar olarak karşıya yükleme

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
