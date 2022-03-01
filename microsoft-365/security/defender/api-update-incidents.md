---
title: Olay API'sini güncelleştir
description: Microsoft 365 Defender API kullanarak olayları Microsoft 365 Defender öğrenin
keywords: güncelleştirme, API, olay
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
ms.openlocfilehash: 447a4b5eb3f4eb521e7cc3bd2df23a42f16d2ef1
ms.sourcegitcommit: 6f3bc00a5cf25c48c61eb3835ac069e9f41dc4db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2022
ms.locfileid: "63014155"
---
# <a name="update-incidents-api"></a>Olayları güncelleştirme API'si

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**

- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> [!IMPORTANT]
> Bazı bilgiler, ticari olarak piyasaya sürmeden önce önemli ölçüde değiştirilmiş olabilir, önceden satın alınan ürünle ilgilidir. Microsoft, burada sağlanan bilgilerle ilgili olarak açık veya zımni hiçbir garanti vermez.

## <a name="api-description"></a>API açıklaması

Var olan olayın özelliklerini güncelleştirme. En iyi özellikler: `status`, `determination`, `classification`, `assignedTo`ve `tags``comments`.

### <a name="quotas-resource-allocation-and-other-constraints"></a>Kotalar, kaynak ayırma ve diğer kısıtlamalar

1. Azaltma eşiğine gelmeden önce, dakikada 50 veya saatte 1500 çağrı yapmalarını sebilirsiniz.
2. Özelliği yalnızca `determination` TruePositive `classification` olarak ayarlanmışsa ayarlayabilirsiniz.

İsteğiniz kısıtlandı ise, bir yanıt kodu `429` döner. Yanıt gövdesi, yeni arama yapmaya baş İlke süreyi belirtecek.

## <a name="permissions"></a>İzinler

Bu API'yi çağrı yapmak için aşağıdaki izinlerden biri gerekir. İzinleri seçme de dahil olmak üzere daha fazla bilgi için bkz. Microsoft 365 Defender [erişme](api-access.md).

İzin türü|İzin|İzin görünen adı
---|---|---
Uygulama|Incident.ReadWrite.All|Tüm olayları okuma ve yazma
Temsilcili (iş veya okul hesabı)|Olay.Okuma|Olayları okuma ve yazma

> [!NOTE]
> Kullanıcı kimlik bilgilerini kullanarak belirteç edinilende, kullanıcının portalda olayı güncelleştirme izni olması gerekir.

## <a name="http-request"></a>HTTP isteği

```HTTP
PATCH /api/incidents/{id}
```

## <a name="request-headers"></a>Üstbilgi isteği

Name|Tür|Açıklama
---|---|---
Yetkilendirme|Dize|Taşıyıcı {token}. **Gerekli**.
İçerik Türü|Dize|application/json. **Gerekli**.

## <a name="request-body"></a>İstek gövdesi

İstek gövdesinde güncelleştirilacak alanlar için değerleri girin. İlgili değerlerde yapılan değişiklikler nedeniyle yeniden hesaplanması gerektirlenmedikçe, istek gövdesine dahil olmayan mevcut özelliklerde yer alan değerleri korunur. En iyi performans için, değişmemiş olan mevcut değerleri atla should.

Özellik|Tür|Açıklama
---|---|---
durum|Enum|Olayın geçerli durumunu belirtir. Olası değerler: `Active`, `Resolved`ve `Redirected`.
atanan|dize|Olayın sahibi.
sınıflandırma|Enum|Olayın belirtimi. Olası değerler: `Unknown`, `FalsePositive`, . `TruePositive`
karartma|Enum|Olayın belirlenmesini belirtir. Olası değerler şöyledir: `NotAvailable`, `Malware``Apt`, `SecurityPersonnel`, `SecurityTesting`, `UnwantedSoftware`. `Other`
etiketler|dize Listesi|Olay etiketlerinin listesi.
açıklama|dize|Olayla eklenecek açıklama.

## <a name="response"></a>Yanıt

Başarılı olursa, bu yöntem döndürür `200 OK`. Yanıt gövdesi, güncelleştirilmiş özelliklere sahip olay varlığı içerir. Belirtilen kimliğin bulunduğu bir olay bulunamasa, yöntem döndürür `404 Not Found`.

## <a name="example"></a>Örnek

### <a name="request-example"></a>İstek örneği

burada isteğin bir örneği ve sağlanmaktadır.

```HTTP
 PATCH https://api.security.microsoft.com/api/incidents/{id}
```

### <a name="response-example"></a>Yanıt örneği

```json
{
    "status": "Resolved",
    "assignedTo": "secop2@contoso.com",
    "classification": "TruePositive",
    "determination": "Malware",
    "tags": ["Yossi's playground", "Don't mess with the Zohan"],
    "comments": [
          {
              "comment": "pen testing",
              "createdBy": "secop2@contoso.com",
              "createdTime": "2021-05-02T09:34:21.5519738Z"
          },
          {
              "comment": "valid incident",
              "createdBy": "secop2@contoso.comt",
              "createdTime": "2021-05-02T09:36:27.6652581Z"
          }
      ]
}
```

## <a name="related-articles"></a>İlgili makaleler

- [Api'lere Microsoft 365 Defender erişme](api-access.md)
- [API sınırları ve lisanslama hakkında bilgi edinin](api-terms.md)
- [Hata kodlarını anlama](api-error-codes.md)
- [Olay API'leri](api-incident.md)
- [Olayları listele](api-list-incidents.md)
- [Olaylara genel bakış](incidents-overview.md)
