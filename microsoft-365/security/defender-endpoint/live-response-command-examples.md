---
title: Canlı yanıt komut örnekleri
description: Uç Nokta için Microsoft Defender için temel veya gelişmiş canlı yanıt komutlarını çalıştırmayı öğrenin ve bunların nasıl kullanıldığına ilişkin örneklere bakın.
keywords: örnek, command, cli, remote, shell, connection, live, response, real-time, command, script, remediate, hunt, export, log, drop, download, file
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 77a1bd5c9234b7a38266be55825726e683557eb4
ms.sourcegitcommit: 35f167725bec5fd4fe131781a53d96b060cf232d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/03/2022
ms.locfileid: "65872397"
---
# <a name="live-response-command-examples"></a>Canlı yanıt komut örnekleri

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Şunlar için geçerlidir:**
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç nokta için Defender'i deneyimlemek ister misiniz? [Ücretsiz deneme için kaydolun.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)

Canlı yanıtta kullanılan yaygın komutlar hakkında bilgi edinin ve bunların normalde nasıl kullanıldığına ilişkin örneklere bakın.

Sahip olduğunuz role bağlı olarak, temel veya gelişmiş canlı yanıt komutlarını çalıştırabilirsiniz. Temel ve gelişmiş komutlar hakkında daha fazla bilgi için bkz [. Canlı yanıt kullanarak cihazlarda varlıkları araştırma](live-response.md).

## `analyze`

```console
# Analyze the file malware.txt
analyze file c:\Users\user\Desktop\malware.txt
```

```console
# Analyze the process by PID
analyze process 1234
```

## `connections`

```console
# List active connections in json format using parameter name
connections -output json
```

```console
# List active connections in json format without parameter name
connections json
```

## `dir`

```console
# List files and sub-folders in the current folder (by default it will show relative paths [-relative_path])
dir
```

```console
# List files and sub-folders in the current folder, with their full path
dir -full_path
```

```console
# List files and sub-folders in a specific folder
dir C:\Users\user\Desktop\
```

```console
# List files and subfolders in the current folder in json format
dir -output json
```

## `fileinfo`

```console
# Display information about a file
fileinfo C:\Windows\notepad.exe
```

## `findfile`

```console
# Find file by name
findfile test.txt
```

## `getfile`

```console
# Download a file from a machine
getfile c:\Users\user\Desktop\work.txt
```

```console
# Download a file from a machine, automatically run prerequisite commands
getfile c:\Users\user\Desktop\work.txt -auto
```

> [!NOTE]
>
> Aşağıdaki dosya türleri Canlı Yanıt içinden bu komut kullanılarak *indirilemez* :
>
> - [Nokta dosyalarını yeniden ayrıştırma](/windows-hardware/drivers/ifs/reparse-points)
> - [Seyrek dosyalar](/windows-server/administration/windows-commands/fsutil-sparse)
> - Boş dosyalar
> - Sanal dosyalar veya yerel olarak tam olarak mevcut olmayan dosyalar
>
> Bu *dosya türleri* [PowerShell](/powershell/scripting/overview) tarafından desteklenir.
>
> Canlı Yanıt'ın içinden bu komutu kullanırken sorun yaşıyorsanız alternatif olarak PowerShell'i kullanın.

## `library`

```console
# List files in the library
library
```

```console
# Delete a file from the library
library delete script.ps1
```

## `processes`

```console
# Show all processes
processes
```

```console
# Get process by pid
processes 123
```

```console
# Get process by pid with argument name
processes -pid 123
```

```console
# Get process by name
processes -name notepad.exe
```

## `putfile`

```console
# Upload file from library
putfile get-process-by-name.ps1
```

```console
# Upload file from library, overwrite file if it exists
putfile get-process-by-name.ps1 -overwrite
```

```console
# Upload file from library, keep it on the machine after a restart
putfile get-process-by-name.ps1 -keep
```

## `registry`

```console
# Show information about the values in a registry key
registry HKEY_CURRENT_USER\Console
```

```console
# Show information about a specific registry value (the double backslash \\ indicates a registry value versus key)
registry HKEY_CURRENT_USER\Console\\ScreenBufferSize
```


## `remediate`

```console
# Remediate file in specific path
remediate file c:\Users\user\Desktop\malware.exe
```

```console
# Remediate process with specific PID
remediate process 7960
```

```console
# Remediate a registry value (the double backslash \\ indicates a registry value versus key)
remediate registry HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Run\\SPStartup
```

```console
# See list of all remediated entities
remediate list
```

## `run`

```console
# Run PowerShell script from the library without arguments
run script.ps1
```

```console
# Run PowerShell script from the library with arguments
run get-process-by-name.ps1 -parameters "-processName Registry"
```

> [!NOTE]
>
> '**run**' veya '**getfile**' gibi uzun süre çalışan komutlar için, arka planda bu eylemi gerçekleştirmek için komutun sonundaki '**&**' simgesini kullanmak isteyebilirsiniz.
> Bu, '**fg**' temel komutunu kullanmayı bitirdiğinizde makineyi araştırmaya devam edip arka plan [komutuna](live-response.md#basic-commands) dönmenizi sağlar.

## `scheduledtask`

```console
# Get all scheduled tasks
scheduledtasks
```

```console
# Get specific scheduled task by location and name
scheduledtasks Microsoft\Windows\Subscription\LicenseAcquisition
```

```console
# Get specific scheduled task by location and name with spacing
scheduledtasks "Microsoft\Configuration Manager\Configuration Manager Health Evaluation"
```

## `undo`

```console
# Restore remediated registry
undo registry HKEY_CURRENT_USER\Console\ScreenBufferSize
```

```console
# Restore remediated scheduledtask
undo scheduledtask Microsoft\Windows\Subscription\LicenseAcquisition
```

```console
# Restore remediated file
undo file c:\Users\user\Desktop\malware.exe
```
