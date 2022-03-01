---
title: Yaygın Microsoft 365 Defender REST API hata kodları
description: REST API hata kodlarıyla ilgili Microsoft 365 Defender hakkında bilgi edinin
keywords: api, hata, kodlar, yaygın hatalar, Microsoft 365 Defender api hata kodları
search.product: eADQiWindows 10XVcnh
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
ms.collection: M365-security-compliance
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.custom: api
ms.openlocfilehash: 499ab1722b2754e893361784f7ff1ce257ceb58b
ms.sourcegitcommit: 6f3bc00a5cf25c48c61eb3835ac069e9f41dc4db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2022
ms.locfileid: "63014173"
---
# <a name="common-microsoft-365-defender-rest-api-error-codes"></a>Yaygın Microsoft 365 Defender REST API hata kodları

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**

- Microsoft 365 Defender

> [!IMPORTANT]
> Bazı bilgiler, ticari olarak piyasaya sürmeden önce önemli ölçüde değiştirilmiş olabilir, önceden satın alınan ürünle ilgilidir. Microsoft, burada sağlanan bilgilerle ilgili olarak açık veya zımni hiçbir garanti vermez.

Hata kodları, bu API'lerden herhangi biri üzerinde bir Microsoft 365 Defender döndürülebilirsiniz. Her hata yanıtı, sorunu çözmeye yardımcı olacak bir hata iletisi içerir. Tablo bölümündeki hata iletisi sütunu bazı örnek iletiler sağlar. Gerçek iletilerin içeriği, yanıtı tetikleyen faktörlere bağlı olarak değişir. Değişken içerik tabloda köşeli ayraçlarla belirtilmiştir.

## <a name="error-codes"></a>Hata kodları

Hata kodu | HTTP durum kodu | İleti
-|-|-
BadRequest | BadRequest (400) | Genel Hatalı İstek hata iletisi.
ODataError | BadRequest (400) | Geçersiz OData URI sorgusu \<the specific error is specified\>.
InvalidInput | BadRequest (400) | Geçersiz giriş \<the invalid input\>.
InvalidRequest YerDiyak | BadRequest (400) | Geçersiz istek gövdesi.
InvalidHashValue | BadRequest (400) | Karma değeri \<the invalid hash\> geçersiz.
InvalidDomainName | BadRequest (400) | Etki alanı \<the invalid domain\> adı geçersiz.
InvalidIpAddress | BadRequest (400) | IP adresi \<the invalid IP\> geçersiz.
InvalidUrl | BadRequest (400) | URL \<the invalid URL\> geçersiz.
MaximumBatchSizeExceeded | BadRequest (400) | En büyük toplu işlem boyutu aşıldı. Alındı: \<batch size received\>, izin verildi: {batch size allowed}.
MissingRequiredParameter | BadRequest (400) | Parametre \<the missing parameter\> eksik.
OsPlatformNotSupported | BadRequest (400) | Bu eylem \<the client OS Platform\> için işletim sistemi platformu desteklenmiyor.
ClientVersionNotSupported | BadRequest (400) | \<The requested action\> istemci sürümünde ve üstünde \<supported client version\> de desteklemektedir.
Yetkisiz | Yetkisiz (401) | Yetkisiz <br /><br />*Not: Genellikle geçersiz veya süresi dolmuş bir yetkilendirme başlığından kaynaklanır.*
Yasak | Yasak (403) | Yasak <br /><br />*Not: Geçerli belirteç ancak eylem için yeterli izin yok*.
DisabledFeature | Yasak (403) | Kiracı özelliği etkinleştirilmedi.
DisallowedOperation | Yasak (403) | \<the disallowed operation and the reason\>.
Bulundu | Bulunamadı (404) | Genel Bulunamadı hata iletisi.
ResourceNotFound | Bulunamadı (404) | Kaynak \<the requested resource\> bulunamadı.
InternalServerError | İç Sunucu Hatası (500) | *Not: Hata iletisi yok, işlemi yeniden deneyin veya çözümlenmezse [Microsoft'a](../../admin/get-help-support.md) ulaşın*

## <a name="examples"></a>Örnekler

```json
{
    "error": {
        "code": "ResourceNotFound",
        "message": "Machine 123123123 was not found",
        "target": "43f4cb08-8fac-4b65-9db1-745c2ae65f3a"
    }
}
```

```json
{
    "error": {
        "code": "InvalidRequestBody",
        "message": "Request body is incorrect",
        "target": "1fa66c0f-18bd-4133-b378-36d76f3a2ba0"
    }
}
```

## <a name="body-parameters"></a>Gövde parametreleri

> [!IMPORTANT]
> Gövde parametreleri büyük/harfe duyarlıdır.

*InvalidRequest İçeren* veya *MissingRequiredParameter* hatasıyla karşılaştınız, bu hataya yazım hatası neden olabilir. API belgelerini gözden geçirme ve gönderilen parametrelerin ilgili örnekle eşleni kontrol edin.

## <a name="tracking-id"></a>İzleme Kimliği

Her hata yanıtı, izlenme için benzersiz bir kimlik parametresi içerir. Bu parametrenin özellik adı *hedeftir*. Hatayla ilgili olarak bize başvurarak bu kimliği eklemek sorunun temel nedenini bulmamıza yardımcı olur.

## <a name="related-articles"></a>İlgili makaleler

- [Microsoft 365 Defender API'lere genel bakış](api-overview.md)
- [Desteklenen Microsoft 365 Defender API'ler](api-supported.md)
- [Api'lere Microsoft 365 Defender erişme](api-access.md)
- [API sınırları ve lisanslama hakkında bilgi edinin](api-terms.md)
