---
title: DeviceTvmSoftwareSerabilitiesKB gelişmiş av şemasında tablosu
description: DeviceTvmSoftware 'de Threat & Güvenlik Açığı Yönetimi tarafından İz alan yazılım güvenlik açıkları hakkında bilgi edinebilirsinizBildirimlerKB tablosu gelişmiş av şeması.
keywords: gelişmiş av, tehdit avı, siber tehdit avı, Microsoft 365 Defender, Microsoft 365, m365, arama, sorgu, telemetri, şema, başvuru, kusto, tablo, sütun, veri türü, açıklama, tehdit & güvenlik açığı yönetimi, TVM, cihaz yönetimi, yazılım, envanter, güvenlik açıkları, YERKarak Kimliği, CVSS, DeviceTvmSoftwareNeritiesKB
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
ms.openlocfilehash: 545e2a3ba12924d364facda14a7a564ead212f30
ms.sourcegitcommit: 6dcc3b039e0f0b9bae17c386f14ed2b577b453a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/15/2021
ms.locfileid: "63018997"
---
# <a name="devicetvmsoftwarevulnerabilitieskb"></a>DeviceTvmSoftware BirikabilitiesKB

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:**
- Microsoft 365 Defender
- Uç Nokta için Microsoft Defender



Gelişmiş `DeviceTvmSoftwareVulnerabilitiesKB` arama şemasında yer alan tablo, Tehdit Güvenlik Açığı [Yönetimi'nin](/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt) cihazları değerlendiren & açıkları listesini içerir. Tablodan bilgi dönüşen sorgular oluşturmak için bu başvuruyu kullanın.

Gelişmiş av şemasında yer alan diğer tablolar hakkında bilgi için bkz. [gelişmiş av başvurusu](advanced-hunting-schema-tables.md).

| Sütun adı | Veri türü | Açıklama |
|-------------|-----------|-------------|
| `CveId` | `string` | Ortak Güvenlik Açıkları ve SALDıRıLAR (YERKIL) sistemi altındaki güvenlik açığına atanan benzersiz tanımlayıcı |
| `CvssScore` | `string` | Ortak Güvenlik Açığı Puanlama Sistemi (CVSS) kapsamındaki güvenlik açığına atanan önem derecesi puanı |
| `IsExploitAvailable` | `boolean` | Güvenlik açığı için açıktan yararlanma kodunun genel kullanıma açık olup olmadığını gösterir |
| `VulnerabilitySeverityLevel` | `string` | CVSS puanı ve tehdit ortamını etkileyen dinamik etmenlere dayalı olarak güvenlik açığına atanan önem düzeyi |
| `LastModifiedTime` | `datetime` | Öğenin veya ilgili meta verilerin son değiştirilme tarihi ve saati |
| `PublishedDate` | `datetime` | Güvenlik açığının genele açıklanması |
| `VulnerabilityDescription` | `string` | Güvenlik açığının ve ilişkili risklerin açıklaması |
| `AffectedSoftware` | `string` | Güvenlik açığı tarafından etkilenen tüm yazılım ürünlerinin listesi |

## <a name="related-topics"></a>İlgili konular

- [Önceden tehdit avı](advanced-hunting-overview.md)
- [Sorgu dilini öğrenme](advanced-hunting-query-language.md)
- [Paylaşılan sorguları kullanma](advanced-hunting-shared-queries.md)
- [Cihazlar, e-postalar, uygulamalar ve kimlikler arasında iş avı](advanced-hunting-query-emails-devices.md)
- [Şemayı anlama](advanced-hunting-schema-tables.md)
- [Sorguyla ilgili en iyi yöntemleri uygulama](advanced-hunting-best-practices.md)
- [Tehdit Veya Güvenlik & Yönetimine Genel Bakış](/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt)