---
title: Uç Nokta API hataları için yaygın Microsoft Defender
description: Açıklamaları olan Uç Nokta API hataları için yaygın Microsoft Defender listesi.
keywords: API'ler, Uç Nokta API için Microsoft Defender, hatalar, sorun giderme
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
ms.openlocfilehash: d960091409a71fd23e52a098ae3d8164c7df5aef
ms.sourcegitcommit: c11d4a2b9cb891ba22e16a96cb9d6389f6482459
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2021
ms.locfileid: "62996469"
---
# <a name="common-rest-api-error-codes"></a>Yaygın REST API hata kodları



[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


* Aşağıdaki tabloda listelenen hata kodları, Uç Nokta API'leri için herhangi bir Microsoft Defender üzerinde bir işlem tarafından döndürülebilirsiniz.
* Hata koduna ek olarak, her hata yanıtı sorunu çözmeye yardımcı olan bir hata iletisi içerir.
* İleti, değiştirilebilir ücretsiz bir metindir.
* Sayfanın en altında, yanıt örneklerini bulabilirsiniz.

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)


> Uç Nokta için Defender'ı deneyimli yapmak mı istiyor musunuz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

Hata kodu|HTTP durum kodu|İleti
---|---|---
BadRequest|BadRequest (400)|Genel Hatalı İstek hata iletisi.
ODataError|BadRequest (400)|Geçersiz OData URI sorgusu (belirli bir hata belirtilmiştir).
InvalidInput|BadRequest (400)|Geçersiz giriş {geçersiz giriş}.
InvalidRequest YerDiyak|BadRequest (400)|Geçersiz istek gövdesi.
InvalidHashValue|BadRequest (400)|Karma değeri {geçersiz karma} geçersiz.
InvalidDomainName|BadRequest (400)|Etki alanı adı {geçersiz etki alanı}.
InvalidIpAddress|BadRequest (400)|IP adresi {geçersiz IP} geçersiz.
InvalidUrl|BadRequest (400)|URL {geçersiz URL} geçersiz.
MaximumBatchSizeExceeded|BadRequest (400)|En büyük toplu işlem boyutu aşıldı. Alındı: {batch size received}, izin verildi: {batch size allowed}.
MissingRequiredParameter|BadRequest (400)|{the missing parameter} parametresi eksik.
OsPlatformNotSupported|BadRequest (400)|Bu eylem için işletim sistemi Platformu {the client OS Platform} desteklenmiyor.
ClientVersionNotSupported|BadRequest (400)|{İstenen eylem}, {desteklenen istemci sürümü} ve üzeri sürümler istemci sürümünde de desteklenmiyor.
Yetkisiz|Yetkisiz (401)|Yetkisiz (geçersiz veya süresi dolmuş yetkilendirme üst bilgisi).
Yasak|Yasak (403)|Yasak (geçerli belirteç ancak eylem için yetersiz izin).
DisabledFeature|Yasak (403)|Kiracı özelliği etkinleştirilmedi.
DisallowedOperation|Yasak (403)|{izin verilmeyen işlem ve neden}.
Bulundu|Bulunamadı (404)|Genel Bulunamadı hata iletisi.
ResourceNotFound|Bulunamadı (404)|Kaynak {istenen kaynak} bulunamadı.
InternalServerError|İç Sunucu Hatası (500)|(Hata iletisi yok, işlemi yeniden deneyin)
TooManyRequests|Çok Fazla İstek Var (429)|Yanıt, istek sayısına veya CPU'ya göre kota sınırına ulaşır.

## <a name="body-parameters-are-case-sensitive"></a>Gövde parametreleri büyük/harfe duyarlıdır

Gönderilen gövde parametreleri şu anda büyük/harfe duyarlıdır.

**InvalidRequest YerAlt** veya **MissingRequiredParameter** hatalarına neden oluyorsanız, bu hata yanlış parametre büyük veya küçük harften kaynaklanıyor olabilir.

API belgeleri sayfasını gözden geçirin ve gönderilen parametrelerin ilgili örnekle eş olup ola eşleşmesini kontrol edin.

## <a name="correlation-request-id"></a>Bağıntı isteği kimliği

Her hata yanıtı, izlenme için benzersiz bir kimlik parametresi içerir.

Bu parametrenin özellik adı "hedef"tir.

Hatayla ilgili olarak bize başvurarak bu kimliği eklemek sorunun temel nedenini bulmaya yardımcı olacaktır.

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
