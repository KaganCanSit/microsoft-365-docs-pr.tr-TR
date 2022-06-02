---
title: Güvenlik önerileri al
description: Belirli bir cihaz kimliğiyle ilgili güvenlik önerileri koleksiyonunu alır.
keywords: apis, graph api, desteklenen API'ler, get, list, file, information, security recommendation per device, threat & güvenlik açığı yönetimi API, Uç Nokta için Microsoft Defender tvm api
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
ms.openlocfilehash: ebe07abd4e7f87e7abfe4d4a8ccd131e20dc4958
ms.sourcegitcommit: a7cd723fd62b4b0aae9c2c2df04ead3c28180084
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2022
ms.locfileid: "65839722"
---
# <a name="get-security-recommendations"></a>Güvenlik önerileri al

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Şunlar için geçerlidir:** 

- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender Güvenlik Açığı Yönetimi](../defender-vulnerability-management/index.yml)

> Uç nokta için Defender'i deneyimlemek ister misiniz? [Ücretsiz deneme için kaydolun.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

[!include[Prerelease information](../../includes/prerelease.md)]

Belirli bir cihaz kimliğiyle ilgili güvenlik önerileri koleksiyonunu alır.

## <a name="permissions"></a>İzinler

Bu API'yi çağırmak için aşağıdaki izinlerden biri gereklidir. İzinlerin nasıl seçileceği de dahil olmak üzere daha fazla bilgi edinmek için bkz[. Uç Nokta için Microsoft Defender API'leri kullanma](apis-intro.md)

İzin türü|Izni|İzin görünen adı
:---|:---|:---
Uygulama|SecurityRecommendation.Read.All|'Tehdit ve Güvenlik Açığı Yönetimi güvenlik öneri bilgilerini okuyun'
Temsilci (iş veya okul hesabı)|SecurityRecommendation.Read|'Tehdit ve Güvenlik Açığı Yönetimi güvenlik öneri bilgilerini okuyun'

## <a name="http-request"></a>HTTP isteği

```http
GET /api/machines/{machineId}/recommendations
```

## <a name="request-headers"></a>İstek üst bilgileri

Name|Tür|Açıklama
:---|:---|:---
Yetkilendirme|Dize|Taşıyıcı {token}. **Gerekli**.

## <a name="request-body"></a>İstek gövdesi

Boş

## <a name="response"></a>Yanıt

Başarılı olursa, bu yöntem gövdedeki güvenlik önerileriyle birlikte 200 Tamam döndürür.

## <a name="example"></a>Örnek

### <a name="request-example"></a>İstek örneği

burada isteğin bir örneği verilmiştir.

```http
GET https://api.securitycenter.microsoft.com/api/machines/ac233fa6208e1579620bf44207c4006ed7cc4501/recommendations
```

### <a name="response-example"></a>Yanıt örneği

Yanıtın bir örneği aşağıda verilmiştir.

```json
{
    "@odata.context": "https://api.securitycenter.microsoft.com/api/$metadata#Recommendations",
    "value": [
        {
            "id": "va-_-git-scm-_-git",
            "productName": "git",
            "recommendationName": "Update Git to version 2.24.1.2",
            "weaknesses": 3,
            "vendor": "git-scm",
            "recommendedVersion": "2.24.1.2",
            "recommendationCategory": "Application",
            "subCategory": "",
            "severityScore": 0,
            "publicExploit": false,
            "activeAlert": false,
            "associatedThreats": [],
            "remediationType": "Update",
            "status": "Active",
            "configScoreImpact": 0,
            "exposureImpact": 0,
            "totalMachineCount": 0,
            "exposedMachinesCount": 1,
            "nonProductivityImpactedAssets": 0,
            "relatedComponent": "Git"
        },
...
}
```

## <a name="related-topics"></a>İlgili konular

- [Risk Tabanlı Tehdit & Güvenlik Açığı Yönetimi](/microsoft-365/security/defender-endpoint/next-gen-threat-and-vuln-mgt)
- [Tehdit & Güvenlik Açığı güvenlik önerisi](/microsoft-365/security/defender-endpoint/tvm-security-recommendation)
