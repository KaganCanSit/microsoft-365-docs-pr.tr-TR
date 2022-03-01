---
title: Gelişmiş av şemasında DeviceTvmSecureConfigurationAssessmentKB tablosu
description: Gelişmiş av şemasının DeviceTvmSecureConfigurationAssessmentKB tablosunda Threat & Güvenlik Açığı Yönetimi tarafından değerlendirilen çeşitli güvenli yapılandırmalar hakkında bilgi edinebilirsiniz.
keywords: gelişmiş av, tehdit avı, siber tehdit avı, Microsoft 365 Defender, microsoft 365, m365, arama, sorgu, telemetri, şema başvurusu, kusto, tablo, sütun, veri türü, açıklama, tehdit & güvenlik açığı yönetimi, TVM, cihaz yönetimi, güvenlik yapılandırması, MITRE ATT&CK framework, bilgi tabanı, KB, DeviceTvmSecureConfigurationAssessmentKB
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: maccruz
author: schmurky
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: m365-security-compliance
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: 81f03a665a0c825388335c925cb908f3b931a918
ms.sourcegitcommit: 6dcc3b039e0f0b9bae17c386f14ed2b577b453a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/15/2021
ms.locfileid: "63019029"
---
# <a name="devicetvmsecureconfigurationassessmentkb"></a>DeviceTvmSecureConfigurationAssessmentKB

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:**
- Microsoft 365 Defender
- Uç Nokta için Microsoft Defender


Gelişmiş `DeviceTvmSecureConfigurationAssessmentKB` arama şemasında yer alan tablo, Tehdit Veya Güvenlik Açığı Yönetimi tarafından denetlenen [çeşitli & bilgileri içerir](/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt). Ayrıca risk bilgileri, ilgili endüstri karşılaştırmaları ve CK tekniklerini ve taktikleri için&MITRE ATT tekniklerini içerir.

Bu tablo olay veya kayıt geri dönmez. Döndürülen değerlendirmelerde güvenlik yapılandırmaları hakkında metin bilgilerini görüntülemek için bu tabloyu [DeviceTvmSecureConfigurationAssessment](advanced-hunting-devicetvmsecureconfigurationassessment-table.md) `ConfigurationId` tablosuna birleştirmenizi öneririz.

Örneğin, tabloyu sorgularken `DeviceTvmSecureConfigurationAssessment` , değerlendirme `ConfigurationDescription` sonuçlarında ortaya gelen güvenlik yapılandırmalarının görünümünü almak istemeyebilirsiniz. Bu tabloya katılarak kullanımı ve projesini kullanarak bu `DeviceTvmSecureConfigurationAssessment` bilgileri `ConfigurationId` görüyoruz `ConfigurationDescription`.

Gelişmiş av şemasında yer alan diğer tablolar hakkında bilgi için bkz. [gelişmiş av başvurusu](advanced-hunting-schema-tables.md).

| Sütun adı | Veri türü | Açıklama |
|-------------|-----------|-------------|
| `ConfigurationId` | `string` | Belirli bir yapılandırma için benzersiz tanımlayıcı |
| `ConfigurationImpact` | `string` | Yapılandırmanın etkisini genel yapılandırma puanına göre derecelendirildi (1-10) |
| `ConfigurationName` | `string` | Yapılandırmanın görünen adı |
| `ConfigurationDescription` | `string` | Yapılandırmanın açıklaması |
| `RiskDescription` | `string` | İlişkili riskin açıklaması |
| `ConfigurationCategory` | `string` | Yapılandırmanın ait olduğu kategori veya gruplama: Uygulama, işletim sistemi, Ağ, Hesaplar, Güvenlik denetimleri|
| `ConfigurationSubcategory` | `string` |Yapılandırmanın ait olduğu alt kategori veya alt grup. Bu özellik, birçok durumda belirli özellikleri veya özellikleri açıklar. |
| `ConfigurationBenchmarks` | `string` | Aynı veya benzer bir yapılandırmayı öneren sektör karşılaştırma karşılaştırmalarının listesi |
| `Tags` | `string` | Güvenlik yapılandırmasını tanımlamak veya kategorilere ayırmak için kullanılan çeşitli öznitelikleri temsil eden etiketler |
| `RemediationOptions` | `string` | İlişkili riskleri azaltmak veya ele almak için önerilen eylemler |

Tablodan uyumlu olmayan virüsten koruma yapılandırmalarına sahip cihazlara ilişkin bilgilerle birlikte, ilgili yapılandırma meta verilerini de vermek için bu örnek sorguyu `DeviceTvmSecureConfigurationAssessment` abilirsiniz:

```kusto
// Get information on devices with antivirus configurations issues
DeviceTvmSecureConfigurationAssessment
| where ConfigurationSubcategory == 'Antivirus' and IsApplicable == 1 and IsCompliant == 0
| join kind=leftouter (
    DeviceTvmSecureConfigurationAssessmentKB
    | project ConfigurationId, ConfigurationName, ConfigurationDescription, RiskDescription, Tags, ConfigurationImpact
) on ConfigurationId
| project DeviceName, OSPlatform, ConfigurationId, ConfigurationName, ConfigurationCategory, ConfigurationSubcategory, ConfigurationDescription, RiskDescription, ConfigurationImpact, Tags
```

## <a name="related-topics"></a>İlgili konular

- [Önceden tehdit avı](advanced-hunting-overview.md)
- [Sorgu dilini öğrenme](advanced-hunting-query-language.md)
- [Paylaşılan sorguları kullanma](advanced-hunting-shared-queries.md)
- [Cihazlar, e-postalar, uygulamalar ve kimlikler arasında iş avı](advanced-hunting-query-emails-devices.md)
- [Şemayı anlama](advanced-hunting-schema-tables.md)
- [Sorguyla ilgili en iyi yöntemleri uygulama](advanced-hunting-best-practices.md)
- [Tehdit Veya Güvenlik & Yönetimine Genel Bakış](/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt)