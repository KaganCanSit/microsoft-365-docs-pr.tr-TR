---
title: PowerShell API Kılavuzu ile Gelişmiş Av
ms.reviewer: ''
description: Uç Nokta API'leri için birkaç Microsoft Defender sorgularken bu kod örneklerini kullanın.
keywords: api'ler, desteklenen api'ler, gelişmiş av, sorgu
search.product: eADQiWindows 10XVcnh
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
ms.date: 09/24/2018
ms.technology: mde
ms.custom: api
ms.openlocfilehash: 6b1f501b942512500c11c7f9fe1e9308d67706e9
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2021
ms.locfileid: "62998173"
---
# <a name="microsoft-defender-for-endpoint-apis-using-powershell"></a>PowerShell kullanan Uç Nokta API'leri için Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:** 
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)

> Uç Nokta için Microsoft Defender'ı mı deneyimliysiniz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

> Uç Nokta için Microsoft Defender'ı mı deneyimliysiniz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-enablesiem-abovefoldlink)

Uç Nokta için Microsoft Defender'dan birden çok API kullanan tam senaryo.

Bu bölümde, PowerShell örneklerini 
- Belirteç alma 
- Uç nokta için Microsoft Defender'daki en son uyarıları almak üzere belirteç kullanma
- Her uyarı için, uyarının orta veya yüksek önceliğe sahip olması ve hala devam ediyor olması durumda cihazın kaç kez şüpheli URL'ye bağlı olduğunu kontrol edin.

**Önkoşul**: Önce [bir uygulama oluşturmanız gerekir](apis-intro.md).

## <a name="preparation-instructions"></a>Hazırlık yönergeleri

- PowerShell penceresini açın.
- İlkeniz PowerShell komutlarını çalıştırmanıza izin vermiyorsa, aşağıdaki komutu çalıştırabilirsiniz:
  ```
  Set-ExecutionPolicy -ExecutionPolicy Bypass
  ```

Daha fazla bilgi için bkz. [PowerShell belgeleri](/powershell/module/microsoft.powershell.security/set-executionpolicy)

## <a name="get-token"></a>Belirteç al

Aşağıdakini çalıştırın:

- $tenantId: Sorguyu çalıştırmak istediğiniz adına kiracının kimliği (sorgu bu kiracının verileri üzerinde çalıştır)
- $appId: AAD App'inizin kimliği (uygulamanın Uç Nokta için Defender'da 'Gelişmiş sorguları çalıştırma' izni olmalıdır)
- $appSecret: Azure AD uygulamanın sırrı

- $suspiciousUrl: URL


```
$tenantId = '00000000-0000-0000-0000-000000000000' # Paste your own tenant ID here
$appId = '11111111-1111-1111-1111-111111111111' # Paste your own app ID here
$appSecret = '22222222-2222-2222-2222-222222222222' # Paste your own app secret here
$suspiciousUrl = 'www.suspiciousUrl.com' # Paste your own URL here

$resourceAppIdUri = 'https://securitycenter.onmicrosoft.com/windowsatpservice'
$oAuthUri = "https://login.microsoftonline.com/$TenantId/oauth2/token"
$authBody = [Ordered] @{
    resource = "$resourceAppIdUri"
    client_id = "$appId"
    client_secret = "$appSecret"
    grant_type = 'client_credentials'
}
$authResponse = Invoke-RestMethod -Method Post -Uri $oAuthUri -Body $authBody -ErrorAction Stop
$aadToken = $authResponse.access_token


#Get latest alert
$alertUrl = "https://api.securitycenter.microsoft.com/api/alerts?`$top=10"
$headers = @{ 
    'Content-Type' = 'application/json'
    Accept = 'application/json'
    Authorization = "Bearer $aadToken" 
}
$alertResponse = Invoke-WebRequest -Method Get -Uri $alertUrl -Headers $headers -ErrorAction Stop
$alerts =  ($alertResponse | ConvertFrom-Json).value

$machinesToInvestigate = New-Object System.Collections.ArrayList

Foreach($alert in $alerts)
{
    #echo $alert.id $alert.machineId    $alert.severity $alert.status

    $isSevereAlert = $alert.severity -in 'Medium', 'High'
    $isOpenAlert = $alert.status -in 'InProgress', 'New'
    if($isOpenAlert -and $isSevereAlert)
    {
        if (-not $machinesToInvestigate.Contains($alert.machineId))
        {
            $machinesToInvestigate.Add($alert.machineId) > $null
        }
    }
}

$commaSeparatedMachines = '"{0}"' -f ($machinesToInvestigate -join '","')

$query = "NetworkCommunicationEvents
| where MachineId in ($commaSeparatedMachines)
| where RemoteUrl  == `"$suspiciousUrl`"
| summarize ConnectionsCount = count() by MachineId"

$queryUrl = "https://api.securitycenter.microsoft.com/api/advancedqueries/run"

$queryBody = ConvertTo-Json -InputObject @{ 'Query' = $query }
$queryResponse = Invoke-WebRequest -Method Post -Uri $queryUrl -Headers $headers -Body $queryBody -ErrorAction Stop
$response =  ($queryResponse | ConvertFrom-Json).Results
$response
```


## <a name="see-also"></a>Ayrıca bkz.
- [Uç Nokta API'leri için Microsoft Defender](apis-intro.md)
- [Gelişmiş Av API'si](run-advanced-query-api.md)
- [Python Kullanarak Gelişmiş Av](run-advanced-query-sample-python.md)
