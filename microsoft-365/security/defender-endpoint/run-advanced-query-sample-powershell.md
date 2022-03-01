---
title: PowerShell API Temel Bilgileri ile Gelişmiş Av
ms.reviewer: ''
description: PowerShell kullanarak Uç Nokta API'si için Microsoft Defender'ı sorgulamayla ilgili temel bilgileri öğrenin.
keywords: api'ler, desteklenen api'ler, gelişmiş av, sorgu
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
ms.openlocfilehash: 5de8778f1da44f8a9453616dc1e3b6f2af948397
ms.sourcegitcommit: 348f3998a029a876a9dcc031f808e9e350804f22
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2021
ms.locfileid: "62996508"
---
# <a name="advanced-hunting-using-powershell"></a>PowerShell kullanarak Gelişmiş Av

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:** 
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)

> Uç Nokta için Microsoft Defender'ı mı deneyimliysiniz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

PowerShell kullanarak gelişmiş sorguları çalıştırma için bkz. [Gelişmiş Av API'si](run-advanced-query-api.md).

Bu bölümde, belirteç almak ve bunu sorgu çalıştırmak için kullanmak üzere PowerShell örneklerini paylaşıyoruz.

## <a name="before-you-begin"></a>Başlamadan önce
Önce bir uygulama [oluşturmanız gerekir](apis-intro.md).

## <a name="preparation-instructions"></a>Hazırlık yönergeleri

- PowerShell penceresini açın.

- İlkeniz PowerShell komutlarını çalıştırmanıza izin vermiyorsa, aşağıdaki komutu çalıştırabilirsiniz:

  ```powershell
  Set-ExecutionPolicy -ExecutionPolicy Bypass
  ```

Daha fazla bilgi için bkz. [PowerShell belgeleri](/powershell/module/microsoft.powershell.security/set-executionpolicy)

## <a name="get-token"></a>Belirteç al

- Aşağıdakini çalıştırın:

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

burada
- $tenantId: Sorguyu çalıştırmak istediğiniz adına kiracının kimliği (başka bir ifadeyle, sorgu bu kiracının verileri üzerinde çalıştır)
- $appId: Azure AD uygulamanın kimliği (uygulamanın Uç Nokta için Defender'da "Gelişmiş sorguları çalıştırma" izni olmalıdır)
- $appSecret: Azure AD uygulamanın sırrı

## <a name="run-query"></a>Sorguyu çalıştır

Aşağıdaki sorguyu çalıştırın:

```powershell
$query = 'RegistryEvents | limit 10' # Paste your own query here

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

- $results sorgunun sonuçlarını içerir
- $schema sorgunun sonuçlarının şemasını içerir

### <a name="complex-queries"></a>Karmaşık sorgular

Karmaşık sorguları (veya çok satırlı sorguları) çalıştırmak için, sorguyu bir dosyaya kaydedin ve yukarıdaki örnekteki ilk satır yerine aşağıdaki komutu çalıştırın:

```powershell
$query = [IO.File]::ReadAllText("C:\myQuery.txt"); # Replace with the path to your file
```

## <a name="work-with-query-results"></a>Sorgu sonuçlarıyla çalışma

Artık sorgu sonuçlarını kullanabilirsiniz.

Dosya biçiminde sorgunun sonuçlarını CSV biçiminde file1.csv, aşağıdaki komutu çalıştırın:

```powershell
$results | ConvertTo-Csv -NoTypeInformation | Set-Content file1.csv
```

Dosya1.json dosyasında sorgunun sonuçlarının JSON biçiminde çıktısını almak için, aşağıdaki komutu çalıştırın:

```powershell
$results | ConvertTo-Json | Set-Content file1.json
```


## <a name="related-topic"></a>İlgili konu
- [Uç Nokta API'leri için Microsoft Defender](apis-intro.md)
- [Gelişmiş Av API'si](run-advanced-query-api.md)
- [Python Kullanarak Gelişmiş Av](run-advanced-query-sample-python.md)
