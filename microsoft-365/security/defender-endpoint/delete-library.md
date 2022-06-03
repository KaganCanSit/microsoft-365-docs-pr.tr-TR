---
title: Canlı yanıt kitaplığından dosya silme
description: Canlı yanıt kitaplığından bir dosyayı silmeyi öğrenin.
keywords: api'ler, graf api'leri, desteklenen API'ler, kitaplıktan silme
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
ms.openlocfilehash: 97a2a2152a60ff542cb946c4283fe3f26c4b9c8e
ms.sourcegitcommit: 35f167725bec5fd4fe131781a53d96b060cf232d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/03/2022
ms.locfileid: "65874140"
---
#  <a name="delete-a-file-from-the-live-response-library"></a>Canlı yanıt kitaplığından dosya silme  

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Şunlar için geçerlidir:**
- [Uç Nokta için Microsoft Defender](/microsoft-365/security/defender-endpoint/microsoft-defender-endpoint)

[!include[Prerelease information](../../includes/prerelease.md)]

>Uç Nokta için Microsoft Defender mı yaşamak istiyorsunuz? [Ücretsiz deneme için kaydolun.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink) 

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>API açıklaması

Canlı yanıt kitaplığından bir dosyayı silin.

## <a name="limitations"></a>Sınırlamalar

1.  Bu API için hız sınırlamaları dakikada 100 çağrı ve saatte 1500 çağrıdır.

## <a name="permissions"></a>İzinler

Bu API'yi çağırmak için aşağıdaki izinlerden biri gereklidir. İzinlerin nasıl seçileceği de dahil olmak üzere daha fazla bilgi için bkz. [Kullanmaya başlayın](apis-intro.md).

| İzin türü                    | Izni     | İzin görünen adı        |
|------------------------------------|----------------|--------------------------------|
| Uygulama                        | Library.Manage | Canlı yanıt kitaplığını yönetme |
| Temsilci (iş veya okul hesabı) | Library.Manage | Canlı yanıt kitaplığını yönetme |

## <a name="http-request"></a>HTTP isteği

SİLMEK https://api.securitycenter.microsoft.com/api/libraryfiles/{fileName}

## <a name="request-headers"></a>İstek üst bilgileri

| Name            | Tür   | Açıklama               |
|-----------------|--------|---------------------------|
| Yetkilendirme   | Dize | Taşıyıcı\<token>\. Gerekli. |

## <a name="request-body"></a>İstek gövdesi

Boş

## <a name="response"></a>Yanıt

-   Kitaplıkta dosya varsa ve başarıyla silindiyse 204 İçerik Yok.

-   Belirtilen dosya adı bulunamadıysa 404 Bulunamadı.

## <a name="example"></a>Örnek

Istek

burada isteğin bir örneği verilmiştir.

```HTTP
DELETE https://api.securitycenter.microsoft.com/api/libraryfiles/script1.ps1
```

## <a name="related-topic"></a>İlgili konu
- [Canlı yanıt çalıştır](run-live-response.md) 