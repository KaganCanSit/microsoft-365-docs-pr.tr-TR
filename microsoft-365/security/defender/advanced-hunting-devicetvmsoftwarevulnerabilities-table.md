---
title: DeviceTvmSoftwareErabilities tablosu gelişmiş av şemasında
description: Cihazlarda bulunan yazılım güvenlik açıkları ve DeviceTvmSoftware'daki her bir güvenlik açığına yönelik kullanılabilir güvenlik güncelleştirmeleri listesi hakkında bilgi alın. Gelişmiş av şemasının Güvenlik tablolarına bakın.
keywords: gelişmiş av, tehdit avı, siber tehdit avı, Microsoft 365 Defender, Microsoft 365, m365, arama, sorgu, telemetri, şema başvurusu, kusto, tablo, sütun, veri türü, açıklama, tehdit & güvenlik açığı yönetimi, TVM, cihaz yönetimi, yazılım, envanter, güvenlik açıkları, YERİnEKULLANİş Kimliği, OS DeviceTvmSoftwareInventoryNerabilities
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
ms.openlocfilehash: a6588134ba2cdf166a465998cd0b1a4fd7134dbb
ms.sourcegitcommit: 6dcc3b039e0f0b9bae17c386f14ed2b577b453a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/15/2021
ms.locfileid: "63019023"
---
# <a name="devicetvmsoftwarevulnerabilities"></a>DeviceTvmSoftwareErabilities

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:**
- Microsoft 365 Defender
- Uç Nokta için Microsoft Defender

>[!IMPORTANT]
> Bazı bilgiler, ticari olarak piyasaya sürmeden önce önemli ölçüde değiştirilmiş olabilir ve yayın öncesi bir ürünle ilgilidir. Microsoft, burada sağlanan bilgilerle ilgili olarak açık veya zımni hiçbir garanti vermez.

Gelişmiş `DeviceTvmSoftwareVulnerabilities` arama şemasında yer alan tablo, yüklü [yazılım &](/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt) güvenlik açıkları için Tehdit Alanı Güvenlik Açığı Yönetimi listesini içerir. Bu tablo işletim sistemi bilgilerini, CD'leri ve güvenlik açığı önem düzeyi bilgilerini de içerir. Örneğin bu tabloyu, yazılımlarında ciddi güvenlik açıkları olan cihazların katıldığı olayları yakalamak için kullanabilirsiniz. Tablodan bilgi dönüşen sorgular oluşturmak için bu başvuruyu kullanın.

>[!NOTE]
> `DeviceTvmSoftwareVulnerabilities` Tablo`DeviceTvmSoftwareInventory`, ve tabloların yerini `DeviceTvmSoftwareInventoryVulnerabilities` alır. Birlikte, ilk iki tablo, iş etkinliklerinizi bilgilendirmeye veya korumasız cihazları güvenlik açığı yönetimi için kullanabileceğiniz daha fazla sütun içerir.

Gelişmiş av şemasında yer alan diğer tablolar hakkında bilgi için bkz. [gelişmiş av başvurusu](advanced-hunting-schema-tables.md).

| Sütun adı | Veri türü | Açıklama |
|-------------|-----------|-------------|
| `DeviceId` | `string` | Hizmette makine için benzersiz tanımlayıcı |
| `DeviceName` | `string` | Makinenin tam etki alanı adı (FQDN) |
| `OSPlatform` | `string` | Makinede çalışan işletim sisteminin platformu. Windows 11, Windows 10 ve Windows 7 gibi, aynı aile içindeki çeşitlemeler de dahil olmak üzere belirli işletim sistemlerini gösterir. |
| `OSVersion` | `string` | Makinede çalışan işletim sisteminin sürümü |
| `OSArchitecture` | `string` | Makinede çalışan işletim sisteminin mimarisi |
| `SoftwareVendor` | `string` | Yazılım yayıncının adı |
| `SoftwareName` | `string` | Yazılım ürününün adı |
| `SoftwareVersion` | `string` | Yazılım ürününün sürüm numarası |
| `CveId` | `string` | Ortak Güvenlik Açıkları ve SALDıRıLAR (YERKIL) sistemi altındaki güvenlik açığına atanan benzersiz tanımlayıcı |
| `VulnerabilitySeverityLevel` | `string` | CVSS puanı ve tehdit ortamını etkileyen dinamik etmenlere dayalı olarak güvenlik açığına atanan önem düzeyi |
| `RecommendedSecurityUpdate` | `string` | Yazılım yayıncısı tarafından güvenlik açığı için sağlanan güvenlik güncelleştirmelerinin adı veya açıklaması |
| `RecommendedSecurityUpdateId` | `string` | İlgili kılavuz veya bilgi bankası (KB) makalelerine yönelik geçerli güvenlik güncelleştirmelerinin veya tanımlayıcının tanımlayıcısı |



## <a name="related-topics"></a>İlgili konular

- [Önceden tehdit avı](advanced-hunting-overview.md)
- [Sorgu dilini öğrenme](advanced-hunting-query-language.md)
- [Paylaşılan sorguları kullanma](advanced-hunting-shared-queries.md)
- [Cihazlar, e-postalar, uygulamalar ve kimlikler arasında iş avı](advanced-hunting-query-emails-devices.md)
- [Şemayı anlama](advanced-hunting-schema-tables.md)
- [Sorguyla ilgili en iyi yöntemleri uygulama](advanced-hunting-best-practices.md)
- [Tehdit Veya Güvenlik & Yönetimine Genel Bakış](/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt)