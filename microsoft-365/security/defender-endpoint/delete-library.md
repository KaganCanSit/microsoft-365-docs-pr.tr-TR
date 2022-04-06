---
title: Canlı yanıt kitaplığından dosya silme
description: Canlı yanıt kitaplığından dosya silmeyi öğrenin.
keywords: api'ler, grafik api'leri, desteklenen api'ler, kitaplıktan silme
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
ms.openlocfilehash: 23625c8b7160d604df5f3a8b1b1387fc31027acf
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/17/2022
ms.locfileid: "63705562"
---
#  <a name="delete-a-file-from-the-live-response-library"></a>Canlı yanıt kitaplığından dosya silme  

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2146631)

[!include[Prerelease information](../../includes/prerelease.md)]

>Uç Nokta için Microsoft Defender'ı mı deneyimliysiniz? [Ücretsiz deneme için kaydol'](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink) 

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>API açıklaması

Canlı yanıt kitaplığından bir dosya silin.

## <a name="limitations"></a>Sınırlamalar

1.  Bu API için fiyat sınırlamaları, dakikada 100 çağrı ve saatte 1500 çağrıdır.

## <a name="permissions"></a>İzinler

Bu API'yi çağrı yapmak için aşağıdaki izinlerden biri gerekir. İzinleri seçme de dahil olmak üzere daha fazla bilgi edinmek için bkz [. Başlama](apis-intro.md).

| İzin türü                    | İzin     | İzin görünen adı        |
|------------------------------------|----------------|--------------------------------|
| Uygulama                        | Library.Manage | Canlı yanıt kitaplığını yönetme |
| Temsilcili (iş veya okul hesabı) | Library.Manage | Canlı yanıt kitaplığını yönetme |

## <a name="http-request"></a>HTTP isteği

DELETE https://api.securitycenter.microsoft.com/api/libraryfiles/{fileName}

## <a name="request-headers"></a>Üstbilgi isteği

| Name            | Tür   | Açıklama               |
|-----------------|--------|---------------------------|
| Yetkilendirme   | Dize | Taşıyıcı\<token>\. Gerekli. |

## <a name="request-body"></a>İstek gövdesi

Boş

## <a name="response"></a>Yanıt

-   Dosya kitaplıkta varsa ve başarıyla silindi 204 İçerik Yok.

-   Belirtilen dosya adı bulunamadı 404 Bulunamadı.

## <a name="example"></a>Örnek

İstek

burada isteğin bir örneği ve sağlanmaktadır.

```HTTP
DELETE https://api.securitycenter.microsoft.com/api/libraryfiles/script1.ps1
```

## <a name="related-topic"></a>İlgili konu
- [Canlı yanıt çalıştır](run-live-response.md) 