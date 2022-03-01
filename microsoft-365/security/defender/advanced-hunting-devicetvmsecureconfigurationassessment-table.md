---
title: Gelişmiş av şemasında DeviceTvmSecureConfigurationAssessment tablosu
description: Gelişmiş av şemasının DeviceTvmSecureConfigurationAssessment tablosunda güvenlik değerlendirme olayları hakkında bilgi edinebilirsiniz. Bu olaylar cihaz bilgileri, güvenlik yapılandırma ayrıntıları, etki ve uyumluluk bilgilerini sağlar.
keywords: gelişmiş av, tehdit avı, siber tehdit avı, Microsoft 365 Defender, Microsoft 365, m365, arama, sorgu, telemetri, şema başvurusu, kusto, tablo, sütun, veri türü, açıklama, tehdit & güvenlik açığı yönetimi, TVM, cihaz yönetimi, güvenlik yapılandırması, DeviceTvmSecureConfigurationAssessment
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
ms.openlocfilehash: 43f44458cde7d466d1097034e7bcc9d0e3072745
ms.sourcegitcommit: 6dcc3b039e0f0b9bae17c386f14ed2b577b453a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/15/2021
ms.locfileid: "63018895"
---
# <a name="devicetvmsecureconfigurationassessment"></a>DeviceTvmSecureConfigurationAssessment

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:**
- Microsoft 365 Defender
- Uç Nokta için Microsoft Defender


Tablodaki her satırda `DeviceTvmSecureConfigurationAssessment` , Tehdit Veya Güvenlik Açığı Yönetimi'nin belirli bir güvenlik [& etkinliği yer alır](/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt). En son değerlendirme sonuçlarını kontrol etmek ve cihazların uyumlu olup olmadığını belirlemek için bu başvuruya bakın.

Bu tabloyu [DeviceTvmSecureConfigurationAssessmentKB](advanced-hunting-devicetvmsecureconfigurationassessmentkb-table.md) `ConfigurationId` tablosuyla birleşebilirsiniz; böylelikle, örneğin, `ConfigurationDescription` `DeviceTvmSecureConfigurationAssessmentKB` tablonun sütunundaki yapılandırmanın metin açıklamasını yapılandırma değerlendirme sonuçlarında görüntüebilirsiniz.

Gelişmiş av şemasında yer alan diğer tablolar hakkında bilgi için bkz. [gelişmiş av başvurusu](advanced-hunting-schema-tables.md).

| Sütun adı | Veri türü | Açıklama |
|-------------|-----------|-------------|
| `DeviceId` | `string` | Hizmette cihaz için benzersiz tanımlayıcı |
| `DeviceName` | `string` | Cihazın tam etki alanı adı (FQDN) |
| `OSPlatform` | `string` | Cihazda çalışan işletim sisteminin platformu. Windows 11, Windows 10 ve Windows 7 gibi, aynı aile içindeki çeşitlemeler de dahil olmak üzere belirli işletim sistemlerini gösterir.|
| `Timestamp` | `datetime` | Kaydın oluşturulma tarihi ve saati |
| `ConfigurationId` | `string` | Belirli bir yapılandırma için benzersiz tanımlayıcı |
| `ConfigurationCategory` | `string` | Yapılandırmanın ait olduğu kategori veya gruplama: Uygulama, işletim sistemi, Ağ, Hesaplar, Güvenlik denetimleri |
| `ConfigurationSubcategory` | `string` | Yapılandırmanın ait olduğu alt kategori veya alt grup. Çoğu durumda, dize belirli özellikleri veya özellikleri açıklar. |
| `ConfigurationImpact` | `string` | Yapılandırmanın etkisini genel yapılandırma puanına göre derecelendirildi (1-10) |
| `IsCompliant` | `boolean` | Yapılandırmanın veya ilkenin düzgün yapılandırıldığından emin olun |
| `IsApplicable` | `boolean` | Yapılandırmanın veya ilkenin cihaz için geçerli olup olmadığını gösterir |
| `Context` | `string` | Yapılandırma veya ilke hakkında ek bağlamsal bilgiler |
| `IsExpectedUserImpact` | `boolean` | Yapılandırma veya ilke uygulandığında kullanıcı etkisinin olup olmadığını gösterir |

Tablodan ilgili yapılandırma meta verileriyle birlikte, uyumlu olmayan virüsten koruma yapılandırmaları içeren cihazlara ilişkin bilgileri vermek için bu örnek sorguyu `DeviceTvmSecureConfigurationAssessmentKB` abilirsiniz:

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