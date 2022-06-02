---
title: Güvenlik temelleri değerlendirme yapılandırmaları
description: "\"Tehdit ve Güvenlik Açığı Yönetimi\" verileri çeken güvenlik temelleri değerlendirme yapılandırmaları hakkında bilgi sağlar. Farklı veri türlerini almak için farklı API çağrıları vardır. Genel olarak, her API çağrısı kuruluşunuzdaki cihazlar için gerekli verileri içerir."
keywords: api, API'ler, dışarı aktarma değerlendirmesi, cihaz değerlendirmesi başına, makine değerlendirmesi başına, güvenlik açığı değerlendirmesi raporu, cihaz güvenlik açığı değerlendirmesi, cihaz güvenlik açığı raporu, güvenli yapılandırma değerlendirmesi, güvenli yapılandırma raporu, yazılım güvenlik açıkları değerlendirmesi, yazılım güvenlik açığı raporu, makineye göre güvenlik açığı raporu,
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: siosulli
author: siosulli
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.custom: api
ms.openlocfilehash: cef91fd3aabb8d857abe8386933c986d62953c42
ms.sourcegitcommit: a7cd723fd62b4b0aae9c2c2df04ead3c28180084
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2022
ms.locfileid: "65839343"
---
# <a name="list-security-baselines-assessment-configurations"></a>Güvenlik temelleri değerlendirme yapılandırmalarını listeleyin

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Şunlar için geçerlidir:**

- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender Güvenlik Açığı Yönetimi](../defender-vulnerability-management/index.yml)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Microsoft Defender Güvenlik Açığı Yönetimi mı yaşamak istiyorsunuz? [Ücretsiz deneme için kaydolun.- Güncelleştirme](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-portaloverview-abovefoldlink)

## <a name="1-get-all-security-baselines-assessment-configurations"></a>1. Tüm güvenlik temelleri değerlendirme yapılandırmalarını alma

Bu API, tüm kullanılabilir karşılaştırmalar için tüm olası güvenlik temelleri değerlendirme yapılandırmalarının ve ayarlarının listesini alır.

### <a name="11-parameters"></a>1.1 Parametreler

- OData V4 sorgularını destekler
- OData tarafından desteklenen işleçler:
  - `$filter` on: `id`, `category`, `name`, `CCE`
  - `$top` maksimum değeri 10.000 olan
  - `$skip`

### <a name="12-http-request"></a>1.2 HTTP isteği

```http
GET /api/baselineConfigurations 
```

### <a name="13-request-headers"></a>1.3 İstek üst bilgileri

Name|Tür|Açıklama
:---|:---|:---
Yetkilendirme|Dize|Taşıyıcı {token}. **Gerekli**.

### <a name="14-response"></a>1.4 Yanıt

Başarılı olursa, bu yöntem gövdedeki temel yapılandırmaların listesiyle 200 Tamam döndürür.

### <a name="15-properties"></a>1.5 Özellikleri

|Özellik | Tür | Açıklama |
|:---|:---|:---|
|Kimlik | Dize | Temel karşılaştırmadaki belirli yapılandırma için benzersiz tanımlayıcı.
|Adı | Dize | Yapılandırma adı karşılaştırmada görünür.
|Açıklama | Dize | Karşılaştırmada göründüğü gibi yapılandırma açıklaması.
|Kategori | Dize | Karşılaştırmada göründüğü gibi yapılandırma kategorisi.
|complianceLevel|Dize|Bu yapılandırmanın göründüğü karşılaştırmanın uyumluluk düzeyi.
|`cce`|Int|Karşılaştırmada göründüğü gibi bu yapılandırmanın CCE'si.
|Mantığı |Dize|Bu yapılandırmanın karşılaştırmada göründüğü rasyonalite. STIG karşılaştırması için bu yapılandırma için bu sağlanmaz.

## <a name="16-example"></a>1.6 Örnek

### <a name="151-request-example"></a>1.5.1 İstek örneği

```http
GET https://api.securitycenter.microsoft.com/api/baselineConfigurations
```

### <a name="162-response-example"></a>1.6.2 Yanıt örneği

```json
{
    "@odata.context": " https://api-df.securitycenter.microsoft.com/api/$metadata#BaselineConfigurations ", 
    "value": [
        {
            "id": "1.1.8", 
            "name": "(L1) Ensure 'Allow importing of payment info' is set to 'Disabled'",
            "description": "<p xmlns:xhtml=\"http://www.w3.org/1999/xhtml\">This policy setting controls whether users are able to import payment information from another browser into Microsoft Edge as well as whether payment information is imported on first use.</p>",
            "category": "Microsoft Edge",
            "complianceLevels": [
                "Level 1 (L1) - Corporate/Enterprise Environment (general use)",
                "Level 2 (L2) - High Security/Sensitive Data Environment (limited functionality)"
            ],
            "cce": "",
            "rationale": "<p xmlns:xhtml=\"http://www.w3.org/1999/xhtml\">Having payment information automatically imported or allowing users to import payment data from another browser into Microsoft Edge could allow for sensitive data to be imported into Edge.</p>",
            "remediation": "<div xmlns:xhtml=\"http://www.w3.org/1999/xhtml\">\r\n  <p>\r\n    <p>\r\nTo establish the recommended configuration via GP, set the following UI path to                 <span class=\"inline_block\">Disabled</span></p>\r\n    <code class=\"code_block\">Computer Configuration\\Policies\\Administrative Templates\\Microsoft Edge\\Allow importing of payment info\r\n</code>\r\n    <p>\r\n      <strong>Note:</strong>\r\n This Group Policy path may not exist by default. It is provided by the Group Policy template                 <span class=\"inline_block\">MSEdge.admx/adml</span>\r\n that can be downloaded from Microsoft                 <a href=\"https://www.microsoft.com/en-us/edge/business/download\">here</a>\r\n.              </p>\r\n    <p class=\"bold\">Impact:</p>\r\n    <p>\r\n      <p>Users will be unable to perform a payment information import from other browsers into Microsoft Edge.</p>\r\n    </p>\r\n  </p>\r\n</div>",
            "benchmarkName": "CIS"
"recommendedValue": [ 
                "Equals '0'" 
            ], 
            "source": [ 
                "hkey_local_machine\\software\\policies\\microsoft\\windows\\eventlog\\security\\retention" 
            ]
        }, 
    ] 
} 
```

## <a name="see-also"></a>Ayrıca bkz.

- [Güvenlik temelleri değerlendirmesini dışarı aktar](export-security-baseline-assessment.md)
- [Güvenlik temelleri değerlendirme profillerini alma](get-security-baselines-assessment-profiles.md)
