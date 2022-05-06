---
title: PowerShell API'siyle Gelişmiş Avcılık Temelleri
ms.reviewer: ''
description: PowerShell kullanarak Uç Nokta için Microsoft Defender API'sini sorgulamanın temellerini öğrenin.
keywords: api'ler, desteklenen API'ler, gelişmiş avcılık, sorgu
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
MS.technology: mde
ms.custom: api
ms.openlocfilehash: fc0cae0ff8c45f4c32213130773e3c118d779ed6
ms.sourcegitcommit: 292de1a7e5ecc2e9e6187126aebba6d3b9416dff
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/06/2022
ms.locfileid: "65243150"
---
# <a name="advanced-hunting-using-powershell"></a>PowerShell ile Gelişmiş Av

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Şunlar için geçerlidir:** 
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

> Uç Nokta için Microsoft Defender mı yaşamak istiyorsunuz? [Ücretsiz deneme için kaydolun.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

PowerShell kullanarak gelişmiş sorgular çalıştırma, bkz. [Gelişmiş Tehdit Avcılığı API'si](run-advanced-query-api.md).

Bu bölümde, bir belirteci almak için PowerShell örneklerini paylaşacağız ve bunu kullanarak sorgu çalıştıracağız.

## <a name="before-you-begin"></a>Başlamadan önce
Önce [bir uygulama oluşturmanız](apis-intro.md) gerekir.

## <a name="preparation-instructions"></a>Hazırlık yönergeleri

- Bir PowerShell penceresi açın.

- İlkeniz PowerShell komutlarını çalıştırmanıza izin vermiyorsa aşağıdaki komutu çalıştırabilirsiniz:

  ```powershell
  Set-ExecutionPolicy -ExecutionPolicy Bypass
  ```

Daha fazla bilgi için bkz. [PowerShell belgeleri](/powershell/module/microsoft.powershell.security/set-executionpolicy)

## <a name="get-token"></a>Belirteci alma

- Aşağıdakileri çalıştırın:

```powershell
$tenantId = '00000000-0000-0000-0000-000000000000' # Paste your own tenant ID here
$appId = '11111111-1111-1111-1111-111111111111' # Paste your own app ID here
$appSecret = '22222222-2222-2222-2222-222222222222' # Paste your own app secret here

$resourceAppIdUri = 'https://api.securitycenter.microsoft.com'
$oAuthUri = "https://login.microsoftonline.com/$TenantId/oauth2/token"
$body = [Ordered] @{
    resource = "$resourceAppIdUri"
    client_id = "$appId"
    client_secret = "$appSecret"
    grant_type = 'client_credentials'
}
$response = Invoke-RestMethod -Method Post -Uri $oAuthUri -Body $body -ErrorAction Stop
$aadToken = $response.access_token
```

Nerede
- $tenantId: Sorguyu çalıştırmak istediğiniz kiracının kimliği (yani, sorgu bu kiracının verileri üzerinde çalıştırılır)
- $appId: Azure AD uygulamanızın kimliği (uygulamanın Uç Nokta için Defender'da 'Gelişmiş sorguları çalıştırma' izni olmalıdır)
- $appSecret: Azure AD uygulamanızın gizli dizisi

## <a name="run-query"></a>Sorguyu çalıştırma

Aşağıdaki sorguyu çalıştırın:

```powershell
$query = 'DeviceRegistryEvents | limit 10' # Paste your own query here

$url = "https://api.securitycenter.microsoft.com/api/advancedqueries/run"
$headers = @{ 
    'Content-Type' = 'application/json'
    Accept = 'application/json'
    Authorization = "Bearer $aadToken" 
}
$body = ConvertTo-Json -InputObject @{ 'Query' = $query }
$webResponse = Invoke-WebRequest -Method Post -Uri $url -Headers $headers -Body $body -ErrorAction Stop
$response =  $webResponse | ConvertFrom-Json
$results = $response.Results
$schema = $response.Schema
```

- $results sorgunuzun sonuçlarını içerir
- $schema sorgunuzun sonuçlarının şemasını içerir

### <a name="complex-queries"></a>Karmaşık sorgular

Karmaşık sorgular (veya çok satırlı sorgular) çalıştırmak istiyorsanız, sorgunuzu bir dosyaya kaydedin ve yukarıdaki örnekteki ilk satır yerine aşağıdaki komutu çalıştırın:

```powershell
$query = [IO.File]::ReadAllText("C:\myQuery.txt"); # Replace with the path to your file
```

## <a name="work-with-query-results"></a>Sorgu sonuçlarıyla çalışın

Artık sorgu sonuçlarını kullanabilirsiniz.

Sorgunun sonuçlarını dosya file1.csv CSV biçiminde çıkarmak için aşağıdaki komutu çalıştırın:

```powershell
$results | ConvertTo-Csv -NoTypeInformation | Set-Content file1.csv
```

Sorgunun sonuçlarını file1.json dosyasında JSON biçiminde çıkarmak için aşağıdaki komutu çalıştırın:

```powershell
$results | ConvertTo-Json | Set-Content file1.json
```


## <a name="related-topic"></a>İlgili konu
- [api'leri Uç Nokta için Microsoft Defender](apis-intro.md)
- [Gelişmiş Avcılık API'si](run-advanced-query-api.md)
- [Python ile Gelişmiş Avcılık](run-advanced-query-sample-python.md)
