---
title: Cihazın güvenli puanını al
description: Kuruluş cihazı güvenli puanı verir.
keywords: api'ler, grafik api'leri, desteklenen api'ler, get, alerts, recent
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
author: dansimp
ms.author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
MS.technology: mde
ms.custom: api
ms.openlocfilehash: 69385a5a1da4b9e91084b4fc524334956c2d8403
ms.sourcegitcommit: 348f3998a029a876a9dcc031f808e9e350804f22
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2021
ms.locfileid: "62996480"
---
# <a name="get-device-secure-score"></a>Cihazın güvenli puanını al

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Microsoft Defender'ı mı deneyimliysiniz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

Cihazlar için [Microsoft Güvenli Puanınızı verir](tvm-microsoft-secure-score-devices.md). Cihazlar için daha yüksek bir Microsoft Güvenli Puanı, uç noktaların siber güvenlik tehdit saldırılarına karşı daha güvenilir olduğu anlamına gelir.

## <a name="permissions"></a>İzinler

Bu API'yi çağrı yapmak için aşağıdaki izinlerden biri gerekir. İzinleri seçme de dahil olmak üzere daha fazla bilgi edinmek için bkz [. Uç nokta API'leri için Microsoft Defender'ı](apis-intro.md) kullanma.

İzin türü|İzin|İzin görünen adı
:---|:---|:---
Uygulama|Puan.Okuma.All|'Tehdit ve Güvenlik Açığı Yönetimi puanı'
Temsilcili (iş veya okul hesabı)|Puan.Okuma|'Tehdit ve Güvenlik Açığı Yönetimi puanı'

## <a name="http-request"></a>HTTP isteği

```http
GET /api/configurationScore
```

## <a name="request-headers"></a>Üstbilgi isteği

Name|Tür|Açıklama
:---|:---|:---
Yetkilendirme|Dize|Taşıyıcı {token}. **Gerekli**.

## <a name="request-body"></a>İstek gövdesi

Boş

## <a name="response"></a>Yanıt

Bu yöntem başarılı olursa, cihaz yanıt gövdesinde güvenli puan verileriyle birlikte 200 Tamam döndürür.

## <a name="example"></a>Örnek

### <a name="request-example"></a>İstek örneği

burada isteğin bir örneği ve sağlanmaktadır.

```http
GET https://api.securitycenter.microsoft.com/api/configurationScore
```

### <a name="response-example"></a>Yanıt örneği

Yanıtın bir örneği:

> [!NOTE]
> Burada gösterilen yanıt listesi kısalma için kesilmiş olabilir.

```json
{
    "@odata.context": "https://api.securitycenter.microsoft.com/api/$metadata#ConfigurationScore/$entity",
    "time": "2019-12-03T09:15:58.1665846Z",
    "score": 340
}
```

## <a name="see-also"></a>Ayrıca bkz.

- [Uç Nokta için Microsoft Defender ile OData sorguları](exposed-apis-odata-samples.md)
