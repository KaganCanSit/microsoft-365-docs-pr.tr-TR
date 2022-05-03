---
title: PowerShell API'siyle Gelişmiş Avcılık Kılavuzu
ms.reviewer: ''
description: Çeşitli Uç Nokta için Microsoft Defender API'lerini sorgulayarak bu kod örneklerini kullanın.
keywords: api'ler, desteklenen API'ler, gelişmiş avcılık, sorgu
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
ms.date: 04/27/2022
ms.technology: mde
ms.custom: api
ms.openlocfilehash: c23bf15a188527b2b4c24270fbc1312537da4154
ms.sourcegitcommit: f30616b90b382409f53a056b7a6c8be078e6866f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2022
ms.locfileid: "65174887"
---
# <a name="microsoft-defender-for-endpoint-apis-using-powershell"></a>PowerShell kullanarak API'leri Uç Nokta için Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Şunlar için geçerlidir:** 
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [İş için Microsoft Defender](../defender-business/index.yml)

> [!IMPORTANT]
> Gelişmiş avcılık özellikleri İş için Defender'a dahil değildir. Bkz[. İş için Microsoft Defender Uç Nokta için Microsoft Defender Planları 1 ve 2 ile karşılaştırma](../defender-business/compare-mdb-m365-plans.md#compare-microsoft-defender-for-business-to-microsoft-defender-for-endpoint-plans-1-and-2).

> Uç Nokta için Microsoft Defender mı yaşamak istiyorsunuz? [Ücretsiz deneme için kaydolun.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

> Uç Nokta için Microsoft Defender mı yaşamak istiyorsunuz? [Ücretsiz deneme için kaydolun.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-enablesiem-abovefoldlink)

Uç Nokta için Microsoft Defender birden çok API'nin kullanıldığı tam senaryo.

Bu bölümde PowerShell örneklerini 
- Belirteç alma 
- Uç Nokta için Microsoft Defender'da en son uyarıları almak için belirteci kullanma
- Her uyarı için, uyarı orta veya yüksek öncelikliyse ve hala devam ediyorsa cihazın şüpheli URL'ye kaç kez bağlandığını denetleyin.

**Önkoşul**: Önce [bir uygulama oluşturmanız](apis-intro.md) gerekir.

## <a name="preparation-instructions"></a>Hazırlık yönergeleri

- Bir PowerShell penceresi açın.
- İlkeniz PowerShell komutlarını çalıştırmanıza izin vermiyorsa aşağıdaki komutu çalıştırabilirsiniz:
  ```
  Set-ExecutionPolicy -ExecutionPolicy Bypass
  ```

Daha fazla bilgi için bkz. [PowerShell belgeleri](/powershell/module/microsoft.powershell.security/set-executionpolicy)

## <a name="get-token"></a>Belirteci alma

Aşağıdaki komutu çalıştırın:

- $tenantId: Sorguyu çalıştırmak istediğiniz kiracının adına kimliği (örneğin, sorgu bu kiracının verilerinde çalıştırılır)
- $appId: AAD uygulamanızın kimliği (uygulamanın Uç Nokta için Defender'da 'Gelişmiş sorguları çalıştırma' izni olmalıdır)
- $appSecret: Azure AD uygulamanızın gizli dizisi

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
- [api'leri Uç Nokta için Microsoft Defender](apis-intro.md)
- [Gelişmiş Avcılık API'si](run-advanced-query-api.md)
- [Python ile Gelişmiş Avcılık](run-advanced-query-sample-python.md)
