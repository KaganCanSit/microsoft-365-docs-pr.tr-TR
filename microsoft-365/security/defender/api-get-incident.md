---
title: Olay API'sini edinin
description: Olay get incidents API'sini kullanarak tek bir olayla ilgili bilgi Microsoft 365 Defender.
keywords: api'ler, grafik api'leri, desteklenen api'ler, get, file, hash
search.product: eADQiWindows 10XVcnh
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
ms.openlocfilehash: 8861dc3752d2c4cc798bc83475f6a51f8245191a
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62983616"
---
# <a name="get-incident-information-api"></a>Olay bilgileri API'sini edinin

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Microsoft Defender'ı mı deneyimliysiniz? [Ücretsiz deneme için kaydol'](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>API açıklaması

Belirli bir olayı kimliğiyle alınan

## <a name="limitations"></a>Sınırlamalar

1. Bu API için fiyat sınırlamaları, dakikada 100 çağrı ve saatte 1500 çağrıdır.

## <a name="permissions"></a>İzinler

Bu API'yi çağrı yapmak için aşağıdaki izinlerden biri gerekir.

İzin türü|İzin|İzin görünen adı
---|---|---
Uygulama|Olay.Okuma.All|'Tüm Olayları Oku'
Uygulama|Incident.ReadWrite.All|'Tüm Olayları okuma ve yazma'
Temsilcili (iş veya okul hesabı)|Olay.Okuma|'Olayları Oku'
Temsilcili (iş veya okul hesabı)|Olay.Okuma|'Olayları okuma ve yazma'

> [!NOTE]
>
> Kullanıcı kimlik bilgilerini kullanarak belirteç elde edilirken:
>
> - Kullanıcının en azından şu rol iznine sahip olması gerekir: 'Verileri Görüntüle'
> - Yanıt yalnızca kullanıcının açık olduğu olayları içerir

## <a name="http-request"></a>HTTP isteği

```console
GET .../api/incidents/{id}
```

## <a name="request-headers"></a>Üstbilgi isteği

Name|Tür|Açıklama
---|---|---
Yetkilendirme|Dize|Taşıyıcı {token}. **Gerekli**.

## <a name="request-body"></a>İstek gövdesi

Boş

## <a name="response"></a>Yanıt

Başarılı olursa, bu yöntem 200 Tamam'ı ve yanıt gövdesinin olay varlığı döndürür.
Belirtilen kimlikle ilgili olay bulunamadı - 404 Bulunamadı.

## <a name="example"></a>Örnek

### <a name="request"></a>İstek

burada isteğin bir örneği ve sağlanmaktadır.

```http
GET https://api.security.microsoft.com/api/incidents/{id}
```
