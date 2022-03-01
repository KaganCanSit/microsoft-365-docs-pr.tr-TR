---
title: Canlı yanıt komut örnekleri
description: Uç Nokta için Microsoft Defender'da temel veya gelişmiş canlı yanıt komutlarını çalıştırmayı öğrenin ve bunların nasıl kullanıldıklarına yönelik örneklere bakın.
keywords: example, command, cli, remote, shell, connection, live, response, real-time, command, script, remediate, hunt, export, log, drop, download, file
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
ms.openlocfilehash: c91c0c5afc449d2e8fdfc415fae83fcc2c913c6a
ms.sourcegitcommit: 6f3bc00a5cf25c48c61eb3835ac069e9f41dc4db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2022
ms.locfileid: "63010740"
---
# <a name="live-response-command-examples"></a>Canlı yanıt komut örnekleri

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Defender'ı deneyimli yapmak mı istiyor musunuz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)

Canlı yanıtta kullanılan yaygın komutlar hakkında bilgi edinmek ve bunların normalde nasıl kullanıldıklarına örneklere bakın.

Sahip olduğunuz role bağlı olarak, temel veya gelişmiş canlı yanıt komutlarını çalıştırabilirsiniz. Temel ve gelişmiş komutlar hakkında daha fazla bilgi için bkz [. Canlı yanıt kullanan cihazlarda varlıkları araştırma](live-response.md).

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
> Aşağıdaki dosya türleri, *Canlı* Yanıt'ın içinde yer alan bu komut kullanılarak indir kullanılamaz:
>
> - [Nokta dosyalarını yenidenpar](/windows/desktop/fileio/reparse-points/)
> - [Dosyaları seyrek olarak dosyala](/windows/desktop/fileio/sparse-files/)
> - Boş dosyalar
> - Sanal dosyalar veya yerel olarak tam olarak mevcut olmadığınız dosyalar
>
> Bu dosya *türleri* [PowerShell tarafından desteklenen bir dosyadır](/powershell/scripting/overview).
>
> Bu komutu Live Response'ın içinde kullanmada sorun yaşarsanız, alternatif olarak PowerShell'i kullanın.

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
# Show information about a specific registry value
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
> **'Çalıştır**' veya '**getfile**' gibi uzun süre çalışan komutlar için, komutun sonundaki '**&**' simgesini kullanarak bu eylemi arka planda gerçekleştirebilirsiniz.
> Böylece, 'fg' temel komutu kullanılarak yapılması gereken makine üzerinde çalışmaya ve arka plan **komutuna** [dönebilirsiniz](live-response.md#basic-commands).

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
