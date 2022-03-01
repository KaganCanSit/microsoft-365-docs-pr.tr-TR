---
title: Python API Kılavuzu ile Gelişmiş Av
ms.reviewer: ''
description: Örneklerle birlikte Python kullanarak Uç Nokta API'si için Microsoft Defender'ı kullanarak sorgu yapmayı öğrenin.
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
ms.openlocfilehash: 73be2b3c2aa40bb88ac6ccff60eec5cb7f55338c
ms.sourcegitcommit: 348f3998a029a876a9dcc031f808e9e350804f22
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2021
ms.locfileid: "62996507"
---
# <a name="advanced-hunting-using-python"></a>Python Kullanarak Gelişmiş Av

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:** 
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)

> Uç Nokta için Microsoft Defender'ı mı deneyimliysiniz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

Python kullanarak gelişmiş sorguları çalıştırma, bkz. [Gelişmiş Av API'si](run-advanced-query-api.md).

Bu bölümde, bir belirteç almak ve bunu sorgu çalıştırmak için kullanmak için Python örneklerini paylaşırız.

> **Önkoşul**: Önce [bir uygulama oluşturmanız gerekir](apis-intro.md).

## <a name="get-token"></a>Belirteç al

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

burada

- tenantId: Sorguyu çalıştırmak istediğiniz adına kiracının kimliği (başka bir ifadeyle, sorgu bu kiracının verileri üzerinde çalıştır)
- appId: Azure AD uygulamanın kimliği (uygulamanın Uç Nokta için Microsoft Defender'da 'Gelişmiş sorguları çalıştırma' izni olmalıdır)
- appSecret: Azure AD uygulamanın sırrı

## <a name="run-query"></a>Sorguyu çalıştır

 Aşağıdaki sorguyu çalıştırın:

```python
query = 'RegistryEvents | limit 10' # Paste your own query here

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

- şema, sorgunun sonuçlarının şemasını içerir
- sonuçlar, sorgunun sonuçlarını içerir

### <a name="complex-queries"></a>Karmaşık sorgular

Karmaşık sorguları (veya çok satırlı sorguları) çalıştırmak için, sorguyu bir dosyaya kaydedin ve yukarıdaki örnekteki ilk satır yerine aşağıdaki komutu çalıştırın:

```python
queryFile = open("D:\\Temp\\myQuery.txt", 'r') # Replace with the path to your file
query = queryFile.read()
queryFile.close()
```

## <a name="work-with-query-results"></a>Sorgu sonuçlarıyla çalışma

Artık sorgu sonuçlarını kullanabilirsiniz.

Sonuçların üzerinden yapmak için aşağıdakini uygulayın:

```python
for result in results:
    print(result) # Prints the whole result
    print(result["EventTime"]) # Prints only the property 'EventTime' from the result
```

Sorgunun sonuçlarını dosya biçiminde CSV biçiminde elde etmek file1.csv şunları yapabilirsiniz:

```python
import csv

outputFile = open("D:\\Temp\\file1.csv", 'w')
output = csv.writer(outputFile)
output.writerow(results[0].keys())
for result in results:
    output.writerow(result.values())

outputFile.close()
```

Dosya1.json dosyasında sorgunun sonuçlarının JSON biçiminde çıktısını almak için, aşağıdakini uygulayın:

```python
outputFile = open("D:\\Temp\\file1.json", 'w')
json.dump(results, outputFile)
outputFile.close()
```

## <a name="related-topic"></a>İlgili konu

- [Uç Nokta API'leri için Microsoft Defender](apis-intro.md)
- [Gelişmiş Av API'si](run-advanced-query-api.md)
- [PowerShell kullanarak Gelişmiş Av](run-advanced-query-sample-powershell.md)
