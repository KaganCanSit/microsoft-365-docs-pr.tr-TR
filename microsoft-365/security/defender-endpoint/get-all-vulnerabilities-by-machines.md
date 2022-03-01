---
title: Makine ve yazılımla tüm güvenlik açıklarını elde edersiniz
description: Makine ve Yazılım tarafından kuruluşu etkileyen tüm güvenlik açıklarının listesini alma
keywords: api'ler, grafik api'si, desteklenen api'ler, get, güvenlik açığı bilgileri, Uç nokta tvm api için Microsoft Defender
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
ms.openlocfilehash: 45c29a70f97c681e6236f4327fed8e344d9dc8ac
ms.sourcegitcommit: 348f3998a029a876a9dcc031f808e9e350804f22
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2021
ms.locfileid: "62996546"
---
# <a name="list-vulnerabilities-by-machine-and-software"></a>Makine ve yazılıma göre güvenlik açıklarını listele

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Microsoft Defender'ı mı deneyimliysiniz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

Makine ve yazılım başına kuruluşu etkileyen tüm güvenlik [açıklarının listesini](machine.md) [sağlar](software.md).

- Güvenlik açığı bir KB düzeltmesi varsa, yanıtta görünür.
- [OData V4 sorgularını destekler](https://www.odata.org/documentation/).
- OData'nın `$filter` sorgusu şunları destekler: `id`, `cveId`, `machineId`, `fixingKbId`, `productName`, `productVersion`ve `severity``productVendor` özellikleri.
<br>```$stop``` maksimum değeri 10.000
<br>```$skip```

> [!TIP]
> Bu API, veri tümleştirme [için Power BI API'tir](api-power-bi.md).

## <a name="permissions"></a>İzinler

Bu API'yi çağrı yapmak için aşağıdaki izinlerden biri gerekir. İzinleri seçme de dahil olmak üzere daha fazla bilgi edinmek için bkz [. Uç nokta API'leri için Microsoft Defender'ı](apis-intro.md) kullanma.

İzin türü|İzin|İzin görünen adı
:---|:---|:---
Uygulama|Güvenlik Açığı.Read.All|'Tehdit ve Güvenlik Açığı Yönetimi güvenlik açığı bilgileri'
Temsilcili (iş veya okul hesabı)|Güvenlik Açığı.Okuma|'Tehdit ve Güvenlik Açığı Yönetimi güvenlik açığı bilgileri'

## <a name="http-request"></a>HTTP isteği

```http
GET /api/vulnerabilities/machinesVulnerabilities
```

## <a name="request-headers"></a>Üstbilgi isteği

Name|Tür|Açıklama
:---|:---|:---
Yetkilendirme|Dize|Taşıyıcı {token}. **Gerekli**.

## <a name="request-body"></a>İstek gövdesi

Boş

## <a name="response"></a>Yanıt

Başarılı olursa, bu yöntem gövdede güvenlik açıkları listesiyle birlikte 200 Tamam döndürür.

## <a name="example"></a>Örnek

### <a name="request-example"></a>İstek örneği

burada isteğin bir örneği ve sağlanmaktadır.

```http
GET https://api.securitycenter.microsoft.com/api/vulnerabilities/machinesVulnerabilities
```

### <a name="response-example"></a>Yanıt örneği

Yanıtın bir örneği:

```json
{
    "@odata.context": "https://api.securitycenter.microsoft.com/api/$metadata#Collection(microsoft.windowsDefenderATP.api.PublicAssetVulnerabilityDto)",
    "value": [
        {
            "id": "5afa3afc92a7c63d4b70129e0a6f33f63a427e21-_-CVE-2020-6494-_-microsoft-_-edge_chromium-based-_-81.0.416.77-_-",
            "cveId": "CVE-2020-6494",
            "machineId": "5afa3afc92a7c63d4b70129e0a6f33f63a427e21",
            "fixingKbId": null,
            "productName": "edge_chromium-based",
            "productVendor": "microsoft",
            "productVersion": "81.0.416.77",
            "severity": "Low"
        },
        {
            "id": "7a704e17d1c2977c0e7b665fb18ae6e1fe7f3283-_-CVE-2016-3348-_-microsoft-_-windows_server_2012_r2-_-6.3.9600.19728-_-3185911",
            "cveId": "CVE-2016-3348",
            "machineId": "7a704e17d1c2977c0e7b665fb18ae6e1fe7f3283",
            "fixingKbId": "3185911",
            "productName": "windows_server_2012_r2",
            "productVendor": "microsoft",
            "productVersion": "6.3.9600.19728",
            "severity": "Low"
        },
        ...
    ]

}
```

## <a name="see-also"></a>Ayrıca bkz.

- [Risk tabanlı Tehdit ve Güvenlik Açığı Yönetimi](/microsoft-365/security/defender-endpoint/next-gen-threat-and-vuln-mgt)
- [Organizasyon güvenlik açıkları](/microsoft-365/security/defender-endpoint/tvm-weaknesses)
