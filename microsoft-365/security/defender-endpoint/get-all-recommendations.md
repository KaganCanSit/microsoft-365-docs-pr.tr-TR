---
title: Tüm önerileri listele
description: Kuruluşu etkileyen tüm güvenlik önerilerinin listesini sağlar.
keywords: api'ler, grafik api'si, desteklenen api'ler, get, güvenlik önerileri, Uç nokta tvm api için Microsoft Defender, Tehdit ve Güvenlik Açığı Yönetimi, Tehdit ve Güvenlik Açığı Yönetimi api
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
ms.openlocfilehash: 727b20e6784016aac423a74c6b564fa96d6f5733
ms.sourcegitcommit: 348f3998a029a876a9dcc031f808e9e350804f22
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2021
ms.locfileid: "62996562"
---
# <a name="list-all-recommendations"></a>Tüm önerileri listele

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


> Uç Nokta için Microsoft Defender'ı mı deneyimliysiniz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

[!include[Prerelease information](../../includes/prerelease.md)]

Kuruluşu etkileyen tüm güvenlik önerilerinin listesini sağlar.


## <a name="api-description"></a>API açıklaması

Kuruluşu etkileyen tüm güvenlik önerileriyle ilgili bilgileri döndürür.

*URL:* GET:/api/recommendations
<br>[OData V4 sorgularını destekler](https://www.odata.org/documentation/).
<br>OData'da desteklenen işleçler:
<br>```$filter```on: ```id```, , ```vendor``````productName```, ```recommendedVersion```, ```recommendationCategory``````subCategory```, ```severityScore```, ```remediationType```, ```recommendedProgram```, ```recommendedVendor```ve ```status``` özellikler.
<br>```$top``` maksimum değeri 10.000' olur.
<br>```$skip```.
<br>Uç Nokta için [Microsoft Defender ile OData sorguları ile ilgili örneklere bakın](exposed-apis-odata-samples.md).

## <a name="permissions"></a>İzinler

Bu API'yi çağrı yapmak için aşağıdaki izinlerden biri gerekir. İzinleri seçme de dahil olmak üzere daha fazla bilgi edinmek için bkz [. Uç nokta API'leri için Microsoft Defender'ı](apis-intro.md) kullanma.

İzin türü|İzin|İzin görünen adı
:---|:---|:---
Uygulama|SecurityRecommendation.Read.All|'Tehdit ve Güvenlik Açığı Yönetimi güvenlik öneri bilgileri'
Temsilcili (iş veya okul hesabı)|SecurityRecommendation.Read |'Tehdit ve Güvenlik Açığı Yönetimi güvenlik öneri bilgileri'

## <a name="http-request"></a>HTTP isteği

```http
GET /api/recommendations
```

## <a name="request-headers"></a>Üstbilgi isteği

Name|Tür|Açıklama
:---|:---|:---
Yetkilendirme|Dize|Taşıyıcı {token}. **Gerekli**.

## <a name="request-body"></a>İstek gövdesi

Boş

## <a name="response"></a>Yanıt

Başarılı olursa, bu yöntem gövdede güvenlik önerileri listesiyle birlikte 200 Tamam döndürür.

## <a name="example"></a>Örnek

### <a name="request"></a>İstek

burada isteğin bir örneği ve sağlanmaktadır.

```http
GET https://api.securitycenter.microsoft.com/api/recommendations
```

### <a name="response"></a>Yanıt

Yanıtın bir örneği:

```json
{
    "@odata.context": "https://api.securitycenter.microsoft.com/api/$metadata#Recommendations",
    "value": [
        {
            "id": "va-_-microsoft-_-windows_10" "va-_-microsoft-_-windows_11",
            "productName": "windows_10" "Windows_11",
            "recommendationName": "Update Windows 10" "Update Windows 11",
            "weaknesses": 397,
            "vendor": "microsoft",
            "recommendedVersion": "",
            "recommendationCategory": "Application",
            "subCategory": "",
            "severityScore": 0,
            "publicExploit": true,
            "activeAlert": false,
            "associatedThreats": [
                "3098b8ef-23b1-46b3-aed4-499e1928f9ed",
                "40c189d5-0330-4654-a816-e48c2b7f9c4b",
                "4b0c9702-9b6c-4ca2-9d02-1556869f56f8",
                "e8fc2121-3cf3-4dd2-9ea0-87d7e1d2b29d",
                "94b6e94b-0c1d-4817-ac06-c3b8639be3ab"
            ],
            "remediationType": "Update",
            "status": "Active",
            "configScoreImpact": 0,
            "exposureImpact": 7.674418604651163,
            "totalMachineCount": 37,
            "exposedMachinesCount": 7,
            "nonProductivityImpactedAssets": 0,
            "relatedComponent": "Windows 10" "Windows 11"
        }
        ...
     ]
}
```

## <a name="see-also"></a>Ayrıca bkz.

- [Risk Tabanlı Tehdit & Güvenlik Açığı Yönetimi](/microsoft-365/security/defender-endpoint/next-gen-threat-and-vuln-mgt)
- [Tehdit & Güvenlik Açığı güvenlik önerisi](/microsoft-365/security/defender-endpoint/tvm-security-recommendation)
