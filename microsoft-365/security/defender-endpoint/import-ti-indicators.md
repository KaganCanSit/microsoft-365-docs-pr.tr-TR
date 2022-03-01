---
title: Göstergeler API'sini İçeri Aktarma
description: Uç Nokta için Microsoft Defender'da Gösterge API'si toplu işlemini içeri aktarmayı öğrenin.
keywords: api'ler, desteklenen api'ler, gönder, ti, gösterge, güncelleştirme
ms.prod: w10
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
ms.custom: api
ms.openlocfilehash: 7306489e537e583055e037ce9d8ce04add248844
ms.sourcegitcommit: c11d4a2b9cb891ba22e16a96cb9d6389f6482459
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2021
ms.locfileid: "62997170"
---
# <a name="import-indicators-api"></a>Göstergeler API'sini İçeri Aktarma

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:** 
- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)

>Uç Nokta için Microsoft Defender'ı mı deneyimliysiniz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>API açıklaması

Gösterge varlıklarını toplu olarak yorumlar [veya güncelleştirmeler](ti-indicator.md) .

IP'ler için CIDR'ye dikkatilemez.

## <a name="limitations"></a>Sınırlamalar

1. Bu API için fiyat sınırlamaları dakikada 30 çağrıdır.
2. Kiracı başına 15.000 etkin [Gösterge sınırı](ti-indicator.md) vardır.
3. Bir API çağrısı için en fazla toplu iş boyutu 500'tir.

## <a name="permissions"></a>İzinler

Bu API'yi çağrı yapmak için aşağıdaki izinlerden biri gerekir. İzinleri seçme de dahil olmak üzere daha fazla bilgi edinmek için bkz [. Başlama](apis-intro.md)

İzin türü|İzin|İzin görünen adı
:---|:---|:---
Uygulama|Ti.ReadWrite|'Okuma ve yazma Göstergeleri'
Uygulama|Ti.ReadWrite.All|'Tüm Göstergeleri okuma ve yazma'
Temsilcili (iş veya okul hesabı)|Ti.ReadWrite|'Okuma ve yazma Göstergeleri'

## <a name="http-request"></a>HTTP isteği

```http
POST https://api.securitycenter.microsoft.com/api/indicators/import
```

## <a name="request-headers"></a>Üstbilgi isteği

Name|Tür|Açıklama
:---|:---|:---
Yetkilendirme|Dize|Taşıyıcı {token}. **Gerekli**.
İçerik Türü|dize|application/json. **Gerekli**.

## <a name="request-body"></a>İstek gövdesi

İstek gövdesinde, aşağıdaki parametreleri olan bir JSON nesnesi girin:

Parametre|Tür|Açıklama
:---|:---|:---
Göstergeler|Liste<[Göstergesi](ti-indicator.md)>|Gösterge [Listesi](ti-indicator.md). **Gerekli**

## <a name="response"></a>Yanıt

- Başarılı olursa, bu yöntem her göstergeye göre içeri aktarma sonuçları listesiyle 200 - Tamam yanıt kodu döndürür. Aşağıdaki örnek.
- Başarılı değilse: Bu yöntem 400 - Kötü İstek olarak geri döner. Hatalı istek genellikle yanlış gövdeyi gösterir.

## <a name="example"></a>Örnek

### <a name="request-example"></a>İstek örneği

burada isteğin bir örneği ve sağlanmaktadır.

```http
POST https://api.securitycenter.microsoft.com/api/indicators/import
```

```json
{
    "Indicators":
    [
        {
            "indicatorValue": "220e7d15b011d7fac48f2bd61114db1022197f7f",
            "indicatorType": "FileSha1",
            "title": "demo",
            "application": "demo-test",
            "expirationTime": "2021-12-12T00:00:00Z",
            "action": "Alert",
            "severity": "Informational",
            "description": "demo2",
            "recommendedActions": "nothing",
            "rbacGroupNames": ["group1", "group2"]
        },
        {
            "indicatorValue": "2233223322332233223322332233223322332233223322332233223322332222",
            "indicatorType": "FileSha256",
            "title": "demo2",
            "application": "demo-test2",
            "expirationTime": "2021-12-12T00:00:00Z",
            "action": "Alert",
            "severity": "Medium",
            "description": "demo2",
            "recommendedActions": "nothing",
            "rbacGroupNames": []
        }
    ]
}
```

### <a name="response-example"></a>Yanıt örneği

Yanıtın bir örneği:

```json
{
    "value": [
        {
            "id": "2841",
            "indicator": "220e7d15b011d7fac48f2bd61114db1022197f7f",
            "isFailed": false,
            "failureReason": null
        },
        {
            "id": "2842",
            "indicator": "2233223322332233223322332233223322332233223322332233223322332222",
            "isFailed": false,
            "failureReason": null
        }
    ]
}
```

## <a name="related-topic"></a>İlgili konu

- [Göstergeleri yönetme](manage-indicators.md)
