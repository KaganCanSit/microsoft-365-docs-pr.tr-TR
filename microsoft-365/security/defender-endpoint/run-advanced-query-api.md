---
title: Gelişmiş Av API'si
ms.reviewer: ''
description: Uç nokta için Microsoft Defender'da gelişmiş sorgular çalıştırmak için gelişmiş av API'sini kullanmayı öğrenin. Sınırlamalar hakkında bilgi edinin ve bir örnek bakın.
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
ms.openlocfilehash: 2e5898c0227128c099c7f0fe1ca99a6d9c8001ef
ms.sourcegitcommit: c11d4a2b9cb891ba22e16a96cb9d6389f6482459
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2021
ms.locfileid: "62997124"
---
# <a name="advanced-hunting-api"></a>Gelişmiş av API'si

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:** 
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)

> Uç Nokta için Microsoft Defender'ı mı deneyimliysiniz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="limitations"></a>Sınırlamalar

1. Sorguyu yalnızca son 30 gün içinde çalıştırabilirsiniz.

2. Sonuçlar en çok 100.000 satır içerir.

3. Kiracı başına yürütme sayısı sınırlıdır:
   - API çağrıları: Dakikada 45 çağrıya kadar, saatte 1500 çağrıya kadar.
   - Yürütme süresi: Her saat için 10 dakika çalışma süresi ve günde 3 çalışma saati.

4. Tek bir isteğin en yüksek yürütme süresi 10 dakikadır.

5. 429 yanıtı istek sayısına veya CPU'ya göre kota sınırına ulaşacak sınırı temsil edecek. Hangi sınıra ulaşıldı olduğunu anlamak için yanıt gövdesini okuyun.

6. Tek bir isteğin en büyük sorgu sonucu boyutu 124 MB'yi aşmaz. Aşılırsa, HTTP 400 Hatalı İstek ve "Sorgu yürütme izin verilen sonuç boyutunu aştı. Sonuçların miktarını sınırlaarak sorguyu en iyi duruma getirmek ve yeniden denemek" görüntülenir.

## <a name="permissions"></a>İzinler

Bu API'yi çağrı yapmak için aşağıdaki izinlerden biri gerekir. İzinleri seçme de dahil olmak üzere daha fazla bilgi edinmek için bkz. Uç Nokta API'leri için [Microsoft Defender'ı kullanma](apis-intro.md)

İzin türü|İzin|İzin görünen adı
:---|:---|:---
Uygulama|AdvancedQuery.Read.All|'Gelişmiş sorguları çalıştır'
Temsilcili (iş veya okul hesabı)|AdvancedQuery.Read|'Gelişmiş sorguları çalıştır'

> [!NOTE]
> Kullanıcı kimlik bilgilerini kullanarak belirteç elde edilirken:
>
> - Kullanıcının 'Verileri Görüntüle' AD rolüne sahip olması gerekir
> - Kullanıcının, cihaz grubu ayarlarına göre cihaza erişimi olması gerekir (Daha fazla bilgi için bkz. Cihaz [gruplarını oluşturma](machine-groups.md) ve yönetme)

## <a name="http-request"></a>HTTP isteği

```http
POST https://api.securitycenter.microsoft.com/api/advancedqueries/run
```

## <a name="request-headers"></a>Üstbilgi isteği

Üst bilgi|Değer
:---|:---
Yetkilendirme|Taşıyıcı {token}. **Gerekli**.
İçerik Türü|application/json

## <a name="request-body"></a>İstek gövdesi

İstek gövdesinde, aşağıdaki parametreleri olan bir JSON nesnesi girin:

Parametre|Tür|Açıklama
:---|:---|:---
Sorgu|Metin|Çalıştıracak sorgu. **Gerekli**.

## <a name="response"></a>Yanıt

Bu yöntem başarılı olursa, yanıt gövdesinde 200 _Tamam ve QueryResponse_ nesnesi döndürür.

## <a name="example"></a>Örnek

### <a name="request-example"></a>İstek örneği

burada isteğin bir örneği ve sağlanmaktadır.

```http
POST https://api.securitycenter.microsoft.com/api/advancedqueries/run
```

```json
{
    "Query":"DeviceProcessEvents
|where InitiatingProcessFileName =~ 'powershell.exe'
|where ProcessCommandLine contains 'appdata'
|project Timestamp, FileName, InitiatingProcessFileName, DeviceId
|limit 2"
}
```

### <a name="response-example"></a>Yanıt örneği

Yanıtın bir örneği:

> [!NOTE]
> Burada gösterilen yanıt nesnesi kısalma için kesilmiş olabilir. Tüm özellikler gerçek bir aramadan döndürülür.

```json
{
    "Schema": [
        {
            "Name": "Timestamp",
            "Type": "DateTime"
        },
        {
            "Name": "FileName",
            "Type": "String"
        },
        {
            "Name": "InitiatingProcessFileName",
            "Type": "String"
        },
        {
            "Name": "DeviceId",
            "Type": "String"
        }
    ],
    "Results": [
        {
            "Timestamp": "2020-02-05T01:10:26.2648757Z",
            "FileName": "csc.exe",
            "InitiatingProcessFileName": "powershell.exe",
            "DeviceId": "10cbf9182d4e95660362f65cfa67c7731f62fdb3"
        },
        {
            "Timestamp": "2020-02-05T01:10:26.5614772Z",
            "FileName": "csc.exe",
            "InitiatingProcessFileName": "powershell.exe",
            "DeviceId": "10cbf9182d4e95660362f65cfa67c7731f62fdb3"
        }
    ]
}
```

## <a name="related-topics"></a>İlgili konular

- [Uç Nokta API'leri için Microsoft Defender'a giriş](apis-intro.md)
- [Portaldan Gelişmiş Av](advanced-hunting-query-language.md)
- [PowerShell kullanarak Gelişmiş Av](run-advanced-query-sample-powershell.md)
