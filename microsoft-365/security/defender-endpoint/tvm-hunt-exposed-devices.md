---
title: Açığa çıkarılan cihazlar için tek bir şey avı
description: Güvenlik yöneticilerine Tehdit ve Güvenlik Açığı Yönetimi, IT yöneticilerine ve SecOps'ların birlikte çalışmalarına yardımcı olmak için nasıl kullanıla kullanıcılar tarafından kullanıla bir yardım olduğunu öğrenin.
keywords: Uç nokta-tvm senaryoları için Microsoft Defender, Uç Nokta için Microsoft Defender, tvm, tvm senaryoları, tehdit & güvenlik açığının etkilenme süresini azaltma, tehdit ve güvenlik açığını azaltma, güvenlik yapılandırmasını geliştirme, Cihazlar için Microsoft Güvenli Puanını artırma, & Cihazlar için Microsoft Güvenli Puan, Cihazlar için Microsoft Güvenli Puanı, etkilenme puanı, güvenlik denetimleri
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365initiative-defender-endpoint
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 40544ab3879acd026d7f327e63d02bdb79d00d83
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2021
ms.locfileid: "62997518"
---
# <a name="hunt-for-exposed-devices---threat-and-vulnerability-management"></a>Açığa çıkarılan cihazlar için tek Tehdit ve Güvenlik Açığı Yönetimi

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**

- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Tehdit ve güvenlik açığı yönetimi](next-gen-threat-and-vuln-mgt.md)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Microsoft Defender'ı mı deneyimliysiniz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-portaloverview-abovefoldlink)

## <a name="use-advanced-hunting-to-find-devices-with-vulnerabilities"></a>Güvenlik açıkları olan cihazları bulmak için gelişmiş avı kullanma

Gelişmiş av, 30 günlük ham verileri keşfetmenizi sağlayan sorgu tabanlı bir tehdit arama aracıdır. Tehdit göstergelerini ve varlıklarını bulmak için ağ'daki olayları önceden inceebilirsiniz. Verilere esnek erişim, hem bilinen hem de potansiyel tehditlere karşı kısıtlanmamış arama sağlar. [Gelişmiş av hakkında daha fazla bilgi](advanced-hunting-overview.md)

### <a name="schema-tables"></a>Şema tabloları

- [DeviceTvmSoftwareInventory](advanced-hunting-devicetvmsoftwareinventory-table.md) - Cihazlarında yüklü yazılımların sürüm bilgileri ve destek sonu durumu da dahil olmak üzere envanteri.

- [DeviceTvmSoftwareErabilities](advanced-hunting-devicetvmsoftwarevulnerabilities-table.md) - Cihazlarda bulunan yazılım güvenlik açıkları ve her güvenlik açığını gideren kullanılabilir güvenlik güncelleştirmeleri listesi.

- [DeviceTvmSoftware Söz dizimiKB - Exploit kodunun](advanced-hunting-devicetvmsoftwarevulnerabilitieskb-table.md) genel kullanıma açık olup olmadığı da dahil olmak üzere, herkesin açık açıkları hakkında bilgi bankası.

- [DeviceTvmSecureConfigurationAssessment](advanced-hunting-devicetvmsecureconfigurationassessment-table.md) - Threat güvenlik açığı yönetimi, cihazlar için çeşitli güvenlik yapılandırmalarının durumunu gösteren değerlendirme olaylarını kontrol eder.

- [DeviceTvmSecureConfigurationAssessmentKB](advanced-hunting-devicetvmsecureconfigurationassessmentkb-table.md) - Threat & Güvenlik Açığı Yönetimi tarafından cihazları değerlendirmek için kullanılan çeşitli güvenlik yapılandırmaları hakkında bilgi bankası; çeşitli standartlara ve karşılaştırmalara eşlemeler içerir

## <a name="check-which-devices-are-involved-in-high-severity-alerts"></a>Yüksek önem düzeyi uyarıları için hangi cihazların yer alan cihazlara dahil olduğunu denetleme

1. Yeni **portalda** \> **sol gezinti** bölmesinden Gelişmiş av Microsoft 365 Defender gidin.

2. Sütun adlarını tanımanız için TVM gelişmiş av şemaları'na kadar aşağı kaydırın.

3. Aşağıdaki sorguları girin:

    ```kusto
    // Search for devices with High active alerts or Critical CVE public exploit
    let DeviceWithHighAlerts = AlertInfo
    | where Severity == "High"
    | project Timestamp, AlertId, Title, ServiceSource, Severity
    | join kind=inner (AlertEvidence | where EntityType == "Machine" | project AlertId, DeviceId, DeviceName) on AlertId
    | summarize HighSevAlerts = dcount(AlertId) by DeviceId;
    let DeviceWithCriticalCve = DeviceTvmSoftwareVulnerabilities
    | join kind=inner(DeviceTvmSoftwareVulnerabilitiesKB) on CveId
    | where IsExploitAvailable == 1 and CvssScore >= 7
    | summarize NumOfVulnerabilities=dcount(CveId),
    DeviceName=any(DeviceName) by DeviceId;
    DeviceWithCriticalCve
    | join kind=inner DeviceWithHighAlerts on DeviceId
    | project DeviceId, DeviceName, NumOfVulnerabilities, HighSevAlerts
    ```

## <a name="related-topics"></a>İlgili konular

- [Tehdit ve güvenlik açığı yönetimi genel bakış](next-gen-threat-and-vuln-mgt.md)
- [Güvenlik önerileri](tvm-security-recommendation.md)
- [API'ler](next-gen-threat-and-vuln-mgt.md#apis)
- [Daha fazla rol için Tehdit ve Güvenlik Açığı Yönetimi yapılandırma](user-roles.md#create-roles-and-assign-the-role-to-an-azure-active-directory-group)
- [Gelişmiş ava genel bakış](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-overview)
- [Tüm gelişmiş av tabloları](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-schema-reference.md)
