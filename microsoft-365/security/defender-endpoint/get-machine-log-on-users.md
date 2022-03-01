---
title: Makine oturum açma kullanıcıları API'sini edinin
description: Uç Nokta için Microsoft Defender'da bir cihazda oturum açmış kullanıcılar koleksiyonunu almak için Makine oturum açma kullanıcılarını alma API'sini nasıl kullanabileceğinizi öğrenin.
keywords: api'ler, grafik api'leri, desteklenen api'ler, al, cihaz, oturum aç, kullanıcılar
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
ms.openlocfilehash: 1c8635e7037f72830584d09d229891822a2e1f52
ms.sourcegitcommit: 2716cb48cc6127f6b851d177af23f276fb07bfc9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/13/2021
ms.locfileid: "63018837"
---
# <a name="get-machine-logon-users-api"></a>Makine oturum açma kullanıcıları API'sini edinin

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:** 
- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)

> Uç Nokta için Microsoft Defender'ı mı deneyimliysiniz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]


## <a name="api-description"></a>API açıklaması
Belirli bir cihazda oturum açmış kullanıcıların bir koleksiyonunu verir.

## <a name="limitations"></a>Sınırlamalar
1. Yapılandırılmış bekletme sürenize göre en son güncelleştirilen uyarılarda sorgu kullanabilirsiniz.
2. Bu API için fiyat sınırlamaları, dakikada 100 çağrı ve saatte 1500 çağrıdır.

## <a name="permissions"></a>İzinler

Bu API'yi çağrı yapmak için aşağıdaki izinlerden biri gerekir. İzinleri seçme de dahil olmak üzere daha fazla bilgi edinmek için bkz. Uç Nokta API'leri için [Microsoft Defender'ı kullanma](apis-intro.md)

İzin türü|İzin|İzin görünen adı
:---|:---|:---
Uygulama |User.Read.All |'Kullanıcı profillerini oku'
Temsilcili (iş veya okul hesabı) | User.Read.All | 'Kullanıcı profillerini oku'

> [!NOTE]
> Kullanıcı kimlik bilgilerini kullanarak belirteç elde edilirken:
>
> - Kullanıcının en azından şu rol iznine sahip olması gerekir: 'Verileri Görüntüle'. Daha fazla bilgi için bkz [. Rol oluşturma ve yönetme](user-roles.md).
> - Yanıt, cihaz grubu ayarlarına göre cihaz kullanıcı tarafından görülebilirse kullanıcıları içerir. Daha fazla bilgi için bkz [. Cihaz grupları oluşturma ve yönetme](machine-groups.md).

## <a name="http-request"></a>HTTP isteği

```http
GET /api/machines/{id}/logonusers
```

## <a name="request-headers"></a>Üstbilgi isteği

Name|Tür|Açıklama
:---|:---|:---
Yetkilendirme | Dize | Taşıyıcı {token}. **Gerekli**.

## <a name="request-body"></a>İstek gövdesi

Boş

## <a name="response"></a>Yanıt

Başarılı ve cihaz varsa - Gövdede kullanıcı varlıklarının listesiyle birlikte 200 Tamam.[](user.md) Cihaz bulunamadı - 404 Bulunamadı.

## <a name="example"></a>Örnek

### <a name="request"></a>İstek

burada isteğin bir örneği ve sağlanmaktadır.

```http
GET https://api.securitycenter.microsoft.com/api/machines/1e5bc9d7e413ddd7902c2932e418702b84d0cc07/logonusers
```

### <a name="response"></a>Yanıt

Yanıtın bir örneği:

```http
HTTP/1.1 200 OK
Content-type: application/json
{
    "@odata.context": "https://api.securitycenter.microsoft.com/api/$metadata#Users",
    "value": [
        {
            "id": "contoso\\user1",
            "accountName": "user1",
            "accountDomain": "contoso",
            "firstSeen": "2019-12-18T08:02:54Z",
            "lastSeen": "2020-01-06T08:01:48Z",
            "logonTypes": "Interactive",
            "isDomainAdmin": true,
            "isOnlyNetworkUser": false
        },
        ...
    ]
}
```
