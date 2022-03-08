---
title: Makine eylem API'sini iptal etme
description: Daha önce başlatılan bir makine eylemini iptal etmeyi öğrenin
keywords: api'ler, grafik api'leri,
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
ms.collection: m365-security-compliance
ms.topic: article
MS.technology: mde
ms.custom: api
ms.openlocfilehash: fc4191043e19df7fea4f350d85acd78d2eca1551
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63322919"
---
# <a name="cancel-machine-action-api"></a>Makine eylem API'sini iptal etme

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2146631)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2146631)

[!include[Prerelease information](../../includes/prerelease.md)]

> Uç Nokta için Microsoft Defender'ı mı deneyimliysiniz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>API açıklaması

Henüz son durumda (tamamlandı, iptal edildi, başarısız) başlatmış olan makine eylemini iptal etme.

## <a name="limitations"></a>Sınırlamalar

1. Bu API için fiyat sınırlamaları, dakikada 100 çağrı ve saatte 1500 çağrıdır.

## <a name="permissions"></a>İzinler

Bu API'yi çağrı yapmak için aşağıdaki izinlerden biri gerekir. İzinleri seçme de dahil olmak üzere daha fazla bilgi edinmek için bkz [. Başlama](apis-intro.md).

|İzin türü|İzin|İzin görünen adı|
|---|---|---|
|Uygulama|Machine.CollectForensics <br> Makine.Yalıt <br> Machine.RestrictExecution <br> Makine.Tarama <br> Makine.Offboard <br> Machine.StopAndQuarantine <br> Machine.LiveResponse|Bilgi toplama <br>Makinesi yalıt<br>Kod yürütmeyi kısıtlama<br>  Makine tarama<br>  Offboard makinesi<br> Durdurma ve Karantina<br> Belirli bir makinede canlı yanıt çalıştırma|
|Temsilcili (iş veya okul hesabı)|Machine.CollectForensics<br> Makine.Yalıt  <br>Machine.RestrictExecution<br> Makine.Tarama<br> Makine.Offboard<br> Machine.StopAndQuarantineMachine.LiveResponse|Bilgi toplama<br> Makinesi yalıt<br>  Kod yürütmeyi kısıtlama<br> Makine tarama<br>Offboard makinesi<br> Durdurma ve Karantina<br> Belirli bir makinede canlı yanıt çalıştırma|

## <a name="http-request"></a>HTTP isteği

```http
POST https://api.securitycenter.microsoft.com/api/machineactions/<machineactionid>/cancel
```

## <a name="request-headers"></a>Üstbilgi isteği

|Name|Tür|Açıklama|
|---|---|---|
|Yetkilendirme|Dize|Taşıyıcı {token}. Gerekli.|
|İçerik Türü|dize|application/json. Gerekli.|

## <a name="request-body"></a>İstek gövdesi

|Parametre|Tür|Açıklama|
|---|---|---|
|Açıklama ekleme|Dize|İptal eylemiyle ilişkilendirmek için açıklama.|

## <a name="response"></a>Yanıt

Başarılı olursa, bu yöntem bir Makine Eylemi varlığıyla 200, Tamam yanıt kodunu döndürür. Belirtilen kimlikle makine eylem varlığı bulunamadı - 404 Bulunamadı.

## <a name="example"></a>Örnek

### <a name="request"></a>İstek

burada isteğin bir örneği ve sağlanmaktadır.

```HTTP
POST
https://api.securitycenter.microsoft.com/api/machineactions/988cc94e-7a8f-4b28-ab65-54970c5d5018/cancel
```

```JSON
{
    "Comment": "Machine action was canceled by automation"
}
```

## <a name="related-topic"></a>İlgili konu

- [Makine eylem API'sini edinin](get-machineaction-object.md)
