---
title: Cihazları öneriye göre listele
description: Güvenlik önerisiyle ilişkilendirilmiş cihazların listesini verir.
keywords: api'ler, grafik api'leri, desteklenen api'ler, güvenlik önerisini al, korumasız cihazlar, Tehdit ve Güvenlik Açığı Yönetimi, Tehdit ve Güvenlik Açığı Yönetimi api
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dolmont
author: DulceMontemayor
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
MS.technology: mde
ms.custom: api
ms.openlocfilehash: b30c558c2e202000145c89e9ab5a122d0dbe6283
ms.sourcegitcommit: 348f3998a029a876a9dcc031f808e9e350804f22
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2021
ms.locfileid: "62996538"
---
# <a name="list-devices-by-recommendation"></a>Cihazları öneriye göre listele

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)

> Uç Nokta için Defender'ı deneyimli yapmak mı istiyor musunuz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

[!include[Prerelease information](../../includes/prerelease.md)]

Güvenlik önerisiyle ilişkilendirilmiş cihazların listesini verir.

## <a name="permissions"></a>İzinler

Bu API'yi çağrı yapmak için aşağıdaki izinlerden biri gerekir. İzinleri seçme de dahil olmak üzere daha fazla bilgi edinmek için bkz [. Uç nokta API'leri için Microsoft Defender'ı](apis-intro.md) kullanma.

İzin türü|İzin|İzin görünen adı
:---|:---|:---
Uygulama|SecurityRecommendation.Read.All|'Tehdit ve Güvenlik Açığı Yönetimi güvenlik öneri bilgileri'
Temsilcili (iş veya okul hesabı)|SecurityRecommendation.Read|'Tehdit ve Güvenlik Açığı Yönetimi güvenlik öneri bilgileri'

## <a name="http-request"></a>HTTP isteği

```http
GET /api/recommendations/{id}/machineReferences
```

## <a name="request-headers"></a>Üstbilgi isteği

Name|Tür|Açıklama
:---|:---|:---
Yetkilendirme|Dize|Taşıyıcı {token}. **Gerekli**.

## <a name="request-body"></a>İstek gövdesi

Boş

## <a name="response"></a>Yanıt

Başarılı olursa, bu yöntem güvenlik önerisiyle ilişkilendirilmiş cihazların listesiyle birlikte 200 Tamam döndürür.

## <a name="example"></a>Örnek

### <a name="request-example"></a>İstek örneği

burada isteğin bir örneği ve sağlanmaktadır.

```http
GET https://api.securitycenter.microsoft.com/api/recommendations/va-_-google-_-chrome/machineReferences
```

### <a name="response-example"></a>Yanıt örneği

Yanıtın bir örneği:

```json
{
    "@odata.context": "https://api.securitycenter.microsoft.com/api/$metadata#MachineReferences",
    "value": [
        {
            "id": "e058770379bc199a9c179ce52a23e16fd44fd2ee",
            "computerDnsName": "niw_pc",
            "osPlatform": "Windows10" "Windows11",
            "rbacGroupName": "GroupTwo"
        }
        ...
    ]
}
```

## <a name="related-topics"></a>İlgili konular

- [Risk Tabanlı Tehdit & Güvenlik Açığı Yönetimi](/microsoft-365/security/defender-endpoint/next-gen-threat-and-vuln-mgt)
- [Tehdit & Güvenlik Açığı güvenlik önerisi](/microsoft-365/security/defender-endpoint/tvm-security-recommendation)
