---
title: Cihaz grubuna göre açık kalma puanı listesi
description: Cihaz grubuna göre pozlama puanları listesini verir.
keywords: api'ler, grafik api'leri, desteklenen api'ler, almak, pozlama puanı, cihaz grubu, cihaz grubu pozlama puanı
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
author: dansimp
ms.author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
MS.technology: mde
ms.custom: api
ms.openlocfilehash: ba046d35b6cf93754fc1daf3d2b211d69e6c27d8
ms.sourcegitcommit: 348f3998a029a876a9dcc031f808e9e350804f22
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2021
ms.locfileid: "62996545"
---
# <a name="list-exposure-score-by-device-group"></a>Cihaz grubuna göre açık kalma puanı listesi

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Defender'ı deneyimli yapmak mı istiyor musunuz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

[!include[Prerelease information](../../includes/prerelease.md)]

Her makine grubu için pozlama puanını sağlar.

## <a name="permissions"></a>İzinler

Bu API'yi çağrı yapmak için aşağıdaki izinlerden biri gerekir. İzinleri seçme de dahil olmak üzere daha fazla bilgi edinmek için bkz. Uç Nokta API'leri için [Microsoft Defender'ı kullanma](apis-intro.md)

İzin türü|İzin|İzin görünen adı
---|---|---
Uygulama|Puan.Okuma.All|'Tehdit ve Güvenlik Açığı Yönetimi puanı'
Temsilcili (iş veya okul hesabı)|Puan.Okuma|'Tehdit ve Güvenlik Açığı Yönetimi puanı'

## <a name="http-request"></a>HTTP isteği

```http
GET /api/exposureScore/ByMachineGroups
```

## <a name="request-headers"></a>Üstbilgi isteği

Name|Tür|Açıklama
---|---|---
|Yetkilendirme|Dize|Taşıyıcı {token}. **Gerekli**.

## <a name="request-body"></a>İstek gövdesi

Boş

## <a name="response"></a>Yanıt

Başarılı olursa, bu yöntem yanıt gövdesinde cihaz grubu verileri başına pozlama puanının listesiyle 200 Tamam döndürür.

## <a name="example"></a>Örnek

### <a name="example-request"></a>Örnek istek

burada isteğin bir örneği ve sağlanmaktadır.

```http
GET https://api.securitycenter.microsoft.com/api/exposureScore/ByMachineGroups
```

### <a name="example-response"></a>Örnek yanıt

Yanıtın bir örneği:

```json
{
    "@odata.context": "https://api.securitycenter.microsoft.com/api/$metadata#ExposureScore",
    "value": [
        {
            "time": "2019-12-03T09:51:28.214338Z",
            "score": 41.38041766305988,
            "rbacGroupName": "GroupOne"
        },
        {
            "time": "2019-12-03T09:51:28.2143399Z",
            "score": 37.403726933165366,
            "rbacGroupName": "GroupTwo"
        }
        ...
    ]
}
```

## <a name="related-topics"></a>İlgili konular

- [Risk Tabanlı Tehdit & Güvenlik Açığı Yönetimi](/microsoft-365/security/defender-endpoint/next-gen-threat-and-vuln-mgt)
- [Tehdit & Güvenlik Açığının etkilenme puanı](/microsoft-365/security/defender-endpoint/tvm-exposure-score)
