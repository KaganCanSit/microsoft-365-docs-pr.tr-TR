---
title: Liste Soruşturmaları API'si
description: Araştırma koleksiyonuna almak üzere ilgili çağrılar oluşturmak için bu API'yi kullanın
keywords: api'ler, grafik api'leri, desteklenen api'ler, Araştırma koleksiyonu
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
ms.openlocfilehash: f5a37d8cbbaeca3dd14c51e1d5c6adcefabf2db8
ms.sourcegitcommit: c11d4a2b9cb891ba22e16a96cb9d6389f6482459
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2021
ms.locfileid: "62996454"
---
# <a name="list-investigations-api"></a>Liste Soruşturmaları API'si

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Microsoft Defender'ı mı deneyimliysiniz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>API açıklaması

Bir Araştırma koleksiyonunu [alınır](investigation.md).

[OData V4 sorgularını destekler](https://www.odata.org/documentation/).

OData'nın `$filter` sorgusu şu şekilde destekler: `startTime`, `id`, ve `state``machineId` `triggeringAlertId` özellikleri.
<br>```$stop``` maksimum değeri 10.000
<br>```$skip```

Uç Nokta için [Microsoft Defender ile OData sorguları ile ilgili örneklere bakın](exposed-apis-odata-samples.md)

## <a name="limitations"></a>Sınırlamalar

1. En büyük sayfa boyutu 10.000'tir.
2. Bu API için fiyat sınırlamaları, dakikada 100 çağrı ve saatte 1500 çağrıdır.

## <a name="permissions"></a>İzinler

Bu API'yi çağrı yapmak için aşağıdaki izinlerden biri gerekir. İzinleri seçme de dahil olmak üzere daha fazla bilgi edinmek için bkz. Uç Nokta API'leri için [Microsoft Defender'ı kullanma](apis-intro.md)

İzin türü|İzin|İzin görünen adı
:---|:---|:---
Uygulama|Alert.Read.All|'Tüm uyarıları oku'
Uygulama|Alert.ReadWrite.All|'Tüm uyarıları okuma ve yazma'
Temsilcili (iş veya okul hesabı)|Alert.Read|'Uyarıları oku'
Temsilcili (iş veya okul hesabı)|Alert.ReadWrite|'Okuma ve yazma uyarıları'

> [!NOTE]
> Kullanıcı kimlik bilgilerini kullanarak belirteç elde edilirken:
>
> - Kullanıcının en azından şu rol iznine sahip olması gerekir: 'Verileri Görüntüle' (Daha fazla bilgi için bkz [. Rol](user-roles.md) oluşturma ve yönetme)

## <a name="http-request"></a>HTTP isteği

```http
GET https://api.securitycenter.microsoft.com/api/investigations
```

## <a name="request-headers"></a>Üstbilgi isteği

Name|Tür|Açıklama
:---|:---|:---
Yetkilendirme|Dize|Taşıyıcı {token}. **Gerekli**.

## <a name="request-body"></a>İstek gövdesi

Boş

## <a name="response"></a>Yanıt

Başarılı olursa, bu yöntem Araştırma varlıkları koleksiyonuyla birlikte 200, Tamam [yanıt kodu](investigation.md) döndürür.

## <a name="example"></a>Örnek

### <a name="request-example"></a>İstek örneği

Tüm soruşturmaları almak için bir istek örneği şöyledir:

```http
GET https://api.securitycenter.microsoft.com/api/investigations
```

### <a name="response-example"></a>Yanıt örneği

Yanıtın örneği:

```json
{
    "@odata.context": "https://api.securitycenter.microsoft.com/api/$metadata#Investigations",
    "value": [
        {
            "id": "63017",
            "startTime": "2020-01-06T14:11:34Z",
            "endTime": null,
            "state": "Running",
            "cancelledBy": null,
            "statusDetails": null,
            "machineId": "a69a22debe5f274d8765ea3c368d00762e057b30",
            "computerDnsName": "desktop-gtrcon0",
            "triggeringAlertId": "da637139166940871892_-598649278"
        }
        ...
    ]
}
```
