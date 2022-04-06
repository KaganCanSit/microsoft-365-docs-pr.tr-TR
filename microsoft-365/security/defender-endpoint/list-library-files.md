---
title: Liste kitaplığı dosyaları
description: Canlı yanıt kitaplığı dosyalarını listeleyebilirsiniz.
keywords: api'ler, grafik api'leri, desteklenen api'ler, almak, cihazlar
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
ms.topic: reference
MS.technology: mde
ms.custom: api
ms.openlocfilehash: 9c9bf11856cf518a1cd387b88a3b70dc4a34cc91
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/17/2022
ms.locfileid: "63705582"
---
#  <a name="list-library-files"></a>Liste kitaplığı dosyaları 

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Geçerli olduğu yer: Uç** [Nokta için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)

[!include[Prerelease information](../../includes/prerelease.md)]

- Uç Nokta için Microsoft Defender'ı mı deneyimliysiniz? [Ücretsiz deneme için kaydol'](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink) 

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>API açıklaması

Canlı yanıt kitaplığı dosyalarını listele.

## <a name="limitations"></a>Sınırlamalar

1.  Bu API için fiyat sınırlamaları, dakikada 100 çağrı ve saatte 1500 çağrıdır.

## <a name="permissions"></a>İzinler

Bu API'yi çağrı yapmak için aşağıdaki izinlerden biri gerekir. İzinleri seçme de dahil olmak üzere daha fazla bilgi edinmek için bkz [. Başlama](apis-intro.md).

|İzin türü                       |      İzin          |  İzin görünen adı | 
|-----------------|--------|---------------------------|  
| Uygulama                        | Library.Manage | Canlı yanıt kitaplığını yönetme |
| Temsilcili (iş veya okul hesabı) | Library.Manage | Canlı yanıt kitaplığını yönetme |

## <a name="http-request"></a>HTTP isteği

```HTTP
GET https://api.securitycenter.microsoft.com/api/libraryfiles
```

## <a name="request-headers"></a>Üstbilgi isteği

| Name         |      Tür                     | Açıklama
|-----------------|--------|---------------------------|
| Yetkilendirme   | Dize | Taşıyıcı {token}. Gerekli. |

## <a name="request-body"></a>İstek gövdesi
Boş

## <a name="response"></a>Yanıt 
Başarılı olursa, bu yöntem canlı yanıt kitaplığı dosya varlıkları koleksiyonuyla birlikte 200 - Tamam yanıt kodu döndürür.

## <a name="example"></a>Örnek

**İstek**

Tüm canlı yanıt kitaplığı dosyalarını alan bir isteğin örneği:

```HTTP
GET https://api.securitycenter.microsoft.com/api/libraryfiles
```

## <a name="response-example"></a>Yanıt örneği

Yanıtın bir örneği:

```JSON
HTTP/1.1 200 Ok
Content-type: application/json
{
"\@odata.context": "https://api.securitycenter.microsoft.com
/api/\$metadata\#LibraryFiles",
"value": [
    {
    "fileName": "script1.ps1",
    "sha256": "6e212a0db618507c44e4ec8ee7499dfef7e5767e5f8d31144df3b96fd1145caf",
    "description": null,
    "creationTime": "2019-10-24T10:54:23.2009016Z",
    "lastUpdatedTime": "2019-10-24T10:54:23.2009016Z",
    "createdBy": "admin",
    "hasParameters": true,
    "parametersDescription": "test"
    },
    {
    "fileName": "script.sh",
    "sha256": "d0f3e3b0641dbf88ee39c822516e81a909d1d06d22341dd9b1f12aa5e5c027a2",
    "description": null,
    "creationTime": "2018-10-24T11:15:35.3688259Z",
    "lastUpdatedTime": "2018-10-24T11:15:35.3688259Z",
    "createdBy": "username",
    "hasParameters": false
    },
    {
    "fileName": "memdump.exe",
    "sha256": "fa70b87730290c0d30fe255d1dfb65de82f96286ebfeeb1d88ed3cc831329825",
    "description": "Process memory dump",
    "creationTime": "2018-10-24T10:54:23.2009016Z",
    "lastUpdatedTime": "2018-10-24T10:54:23.2009016Z",
    "createdBy": "admin",
    "hasParameters": false
    }
]
}
```


## <a name="related-topic"></a>İlgili konu
- [Canlı yanıt çalıştır](run-live-response.md) 