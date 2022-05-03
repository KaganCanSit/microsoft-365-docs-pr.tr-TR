---
title: Python API'siyle Gelişmiş Avcılık Kılavuzu
ms.reviewer: ''
description: Örneklerle python kullanarak Uç Nokta için Microsoft Defender API'sini kullanarak sorgulamayı öğrenin.
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
ms.openlocfilehash: 99fc848088725f7b28d91eebc78327c688059de8
ms.sourcegitcommit: f30616b90b382409f53a056b7a6c8be078e6866f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2022
ms.locfileid: "65174769"
---
# <a name="advanced-hunting-using-python"></a>Python ile Gelişmiş Avcılık

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Şunlar için geçerlidir:** 
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

> Uç Nokta için Microsoft Defender mı yaşamak istiyorsunuz? [Ücretsiz deneme için kaydolun.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

Python kullanarak gelişmiş sorgular çalıştırma, bkz. [Gelişmiş Tehdit Avcılığı API'si](run-advanced-query-api.md).

Bu bölümde python örneklerini paylaşarak bir belirteci alıp sorgu çalıştırmak için kullanacağız.

> **Önkoşul**: Önce [bir uygulama oluşturmanız](apis-intro.md) gerekir.

## <a name="get-token"></a>Belirteci alma

- Aşağıdaki komutları çalıştırın:

```python
import json
import urllib.request
import urllib.parse

tenantId = '00000000-0000-0000-0000-000000000000' # Paste your own tenant ID here
appId = '11111111-1111-1111-1111-111111111111' # Paste your own app ID here
appSecret = '22222222-2222-2222-2222-222222222222' # Paste your own app secret here

url = "https://login.microsoftonline.com/%s/oauth2/token" % (tenantId)

resourceAppIdUri = 'https://api.securitycenter.microsoft.com'

body = {
    'resource' : resourceAppIdUri,
    'client_id' : appId,
    'client_secret' : appSecret,
    'grant_type' : 'client_credentials'
}

data = urllib.parse.urlencode(body).encode("utf-8")

req = urllib.request.Request(url, data)
response = urllib.request.urlopen(req)
jsonResponse = json.loads(response.read())
aadToken = jsonResponse["access_token"]
```

Nerede

- tenantId: Sorguyu çalıştırmak istediğiniz kiracının kimliği (yani, sorgu bu kiracının verileri üzerinde çalıştırılır)
- appId: Azure AD uygulamanızın kimliği (uygulamanın Uç Nokta için Microsoft Defender için 'Gelişmiş sorguları çalıştırma' izni olmalıdır)
- appSecret: Azure AD uygulamanızın gizli dizisi

## <a name="run-query"></a>Sorguyu çalıştırma

 Aşağıdaki sorguyu çalıştırın:

```python
query = 'DeviceRegistryEvents | limit 10' # Paste your own query here

url = "https://api.securitycenter.microsoft.com/api/advancedqueries/run"
headers = { 
    'Content-Type' : 'application/json',
    'Accept' : 'application/json',
    'Authorization' : "Bearer " + aadToken
}

data = json.dumps({ 'Query' : query }).encode("utf-8")

req = urllib.request.Request(url, data, headers)
response = urllib.request.urlopen(req)
jsonResponse = json.loads(response.read())
schema = jsonResponse["Schema"]
results = jsonResponse["Results"]
```

- schema, sorgunuzun sonuçlarının şemasını içerir
- sonuçlar sorgunuzun sonuçlarını içerir

### <a name="complex-queries"></a>Karmaşık sorgular

Karmaşık sorgular (veya çok satırlı sorgular) çalıştırmak istiyorsanız, sorgunuzu bir dosyaya kaydedin ve yukarıdaki örnekteki ilk satır yerine aşağıdaki komutu çalıştırın:

```python
queryFile = open("D:\\Temp\\myQuery.txt", 'r') # Replace with the path to your file
query = queryFile.read()
queryFile.close()
```

## <a name="work-with-query-results"></a>Sorgu sonuçlarıyla çalışın

Artık sorgu sonuçlarını kullanabilirsiniz.

Sonuçları yinelemek için aşağıdakileri yapın:

```python
for result in results:
    print(result) # Prints the whole result
    print(result["EventTime"]) # Prints only the property 'EventTime' from the result
```

Sorgu sonuçlarını dosya file1.csv CSV biçiminde çıkarmak için aşağıdakileri yapın:

```python
import csv

outputFile = open("D:\\Temp\\file1.csv", 'w')
output = csv.writer(outputFile)
output.writerow(results[0].keys())
for result in results:
    output.writerow(result.values())

outputFile.close()
```

Sorgunun sonuçlarını file1.json dosyasında JSON biçiminde çıkarmak için aşağıdakileri yapın:

```python
outputFile = open("D:\\Temp\\file1.json", 'w')
json.dump(results, outputFile)
outputFile.close()
```

## <a name="related-topic"></a>İlgili konu

- [api'leri Uç Nokta için Microsoft Defender](apis-intro.md)
- [Gelişmiş Avcılık API'si](run-advanced-query-api.md)
- [PowerShell ile Gelişmiş Av](run-advanced-query-sample-powershell.md)
