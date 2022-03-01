---
title: YERKİ-KB harita API'si edinin
description: Uç Nokta için Microsoft Defender'da CVE'leri KB'lere ve YERMİ'lere eşlemek için KULLANIM-KB eşleme API'sini nasıl kullanabileceğinizi öğrenin.
keywords: api'ler, grafik api'leri, desteklenen api'ler, get, ap, kb
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: leonidzh
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ROBOTS: NOINDEX
ms.technology: mde
ms.custom: api
ms.openlocfilehash: d0672804d0d2a8221480fe76e4237114a88f4cfb
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2021
ms.locfileid: "62997532"
---
# <a name="get-cve-kb-map-api"></a>YERKİ-KB harita API'si edinin

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Microsoft Defender'ı mı deneyimliysiniz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!Include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!Include[Improve request performance](../../includes/improve-request-performance.md)]

CV'lerin haritasını KBs'lere ve YERMİ ayrıntılarına geriler.

## <a name="permissions"></a>İzinler

Kullanıcı için okuma izinleri gerekir.

## <a name="http-request"></a>HTTP isteği

```http
GET /testwdatppreview/cvekbmap
```

## <a name="request-headers"></a>Üstbilgi isteği

Üst bilgi|Değer
:---|:---
Yetkilendirme|Taşıyıcı {token}. **Gerekli**.
İçerik türü|application/json

## <a name="request-body"></a>İstek gövdesi

Boş

## <a name="response"></a>Yanıt

Başarılı ve harita varsa - 200 Tamam.

## <a name="example"></a>Örnek

### <a name="request-example"></a>İstek örneği

İsteğin örneği:

```http
GET https://graph.microsoft.com/testwdatppreview/CveKbMap
```

### <a name="response-example"></a>Yanıt örneği

İşte yanıtın bir örneği:

```json
{
    "@odata.context":"https://graph.microsoft.com/testwdatppreview/$metadata#CveKbMap",
    "@odata.count": 4168,
    "value": [
        {
            "cveKbId": "CVE-2015-2482-3097617",
            "cveId": "CVE-2015-2482",
            "kbId":"3097617",
            "title": "Cumulative Security Update for Internet Explorer",
            "severity": "Critical"
        },
    ...
}
```
