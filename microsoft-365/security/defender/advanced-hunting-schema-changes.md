---
title: Microsoft 365 Defender gelişmiş tehdit avcılığı şemasındaki değişiklikleri adlandırma
description: Gelişmiş tehdit avcılığı şemasındaki değişiklikleri tabloları ve sütunları adlandırmayı izleme ve gözden geçirme
keywords: gelişmiş tehdit avcılığı, tehdit avcılığı, siber tehdit avcılığı, Microsoft 365 Defender, microsoft 365, m365, arama, sorgu, telemetri, şema başvurusu, kusto, tablo, veri, adlandırma değişiklikleri, yeniden adlandırma
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
ms.openlocfilehash: 4e58bb3d8c8cc7c507c4136abcabeb7e42b6827d
ms.sourcegitcommit: 1ef176c79a0e6dbb51834fe30807409d4e94847c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/19/2021
ms.locfileid: "64731515"
---
# <a name="advanced-hunting-schema---naming-changes"></a>Gelişmiş tehdit avcılığı şeması - Adlandırma değişiklikleri

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Şunlar için geçerlidir:**
- Microsoft 365 Defender

[!INCLUDE [Prerelease information](../includes/prerelease.md)]

[Gelişmiş tehdit avcılığı şeması](advanced-hunting-schema-tables.md) düzenli olarak güncelleştirilerek yeni tablolar ve sütunlar eklenir. Bazı durumlarda, mevcut sütun adları kullanıcı deneyimini geliştirmek için yeniden adlandırılır veya değiştirilir. Sorgularınızı etkileyebilecek adlandırma değişikliklerini gözden geçirmek için bu makaleye bakın.

Adlandırma değişiklikleri, özel algılama kuralları tarafından kullanılan sorgular da dahil olmak üzere Bulut için Defender kaydedilen sorgulara otomatik olarak uygulanır. Bu sorguları el ile güncelleştirmeniz gerekmez. Ancak, aşağıdaki sorguları güncelleştirmeniz gerekir:
- API kullanılarak çalıştırılacak sorgular
- Bulut için Defender dışında başka bir yere kaydedilen sorgular

## <a name="december-2020"></a>Aralık 2020

| Tablo adı | Özgün sütun adı | Yeni sütun adı | Değişiklik nedeni
|--|--|--|--|
| [EmailEvents](advanced-hunting-emailevents-table.md) | `FinalEmailAction` | `EmailAction` | Müşteri geri bildirimi |
| [EmailEvents](advanced-hunting-emailevents-table.md) | `FinalEmailActionPolicy` | `EmailActionPolicy` | Müşteri geri bildirimi |
| [EmailEvents](advanced-hunting-emailevents-table.md) | `FinalEmailActionPolicyGuid` | `EmailActionPolicyGuid` | Müşteri geri bildirimi |

## <a name="january-2021"></a>Ocak 2021

| Sütun adı | Özgün değer adı | Yeni değer adı | Değişiklik nedeni
|--|--|--|--|
| `DetectionSource` | Bulut Uygulamaları için Defender | Bulut Uygulamaları için Microsoft Defender | Rebranding |
| `DetectionSource` | WindowsDefenderAtp| EDR| Rebranding |
| `DetectionSource` | WindowsDefenderAv | Antivirus | Rebranding |
| `DetectionSource` | WindowsDefenderSmartScreen |  Smartscreen | Rebranding |
| `DetectionSource` | CustomerTI | Özel TI | Rebranding |
| `DetectionSource` | OfficeATP | Office 365 için Microsoft Defender | Rebranding |
| `DetectionSource` | MTP | Microsoft 365 Defender | Rebranding |
| `DetectionSource` | AzureATP | Kimlik için Microsoft Defender | Rebranding |
| `DetectionSource` | CustomDetection | Özel algılama | Rebranding |
| `DetectionSource` | AutomatedInvestigation |Otomatik araştırma | Rebranding |
| `DetectionSource` | ThreatExperts | Microsoft Tehdit Uzmanları | Rebranding |
| `DetectionSource` | 3. taraf TI | 3. Taraf algılayıcıları | Rebranding |
| `ServiceSource` | Microsoft Defender ATP| Uç Nokta için Microsoft Defender | Rebranding |
|`ServiceSource` |Microsoft Tehdit Koruması | Microsoft 365 Defender | Rebranding |
| `ServiceSource` | ATP'Office 365 |Office 365 için Microsoft Defender | Rebranding |
| `ServiceSource` |Azure ATP |Kimlik için Microsoft Defender | Rebranding |

`DetectionSource`[, AlertInfo](advanced-hunting-alertinfo-table.md) tablosunda kullanılabilir. `ServiceSource`[, AlertEvidence](advanced-hunting-alertevidence-table.md) ve [AlertInfo](advanced-hunting-alertinfo-table.md) tablolarında kullanılabilir. 

## <a name="february-2021"></a>Şubat 2021

1. [EmailAttachmentInfo](advanced-hunting-emailattachmentinfo-table.md) ve [EmailEvents tablolarında](advanced-hunting-emailevents-table.md) `MalwareFilterVerdict`ve `PhishFilterVerdict` sütunları sütunla `ThreatTypes` değiştirilmiştir. `MalwareDetectionMethod` ve `PhishDetectionMethod` sütunları da sütunla `DetectionMethods` değiştirildi. Bu akış, yeni sütunların altında daha fazla bilgi sağlamamıza olanak tanır. Eşleme aşağıda verilmiştir.

    | Tablo adı | Özgün sütun adı | Yeni sütun adı | Değişiklik nedeni
    |--|--|--|--|
    | `EmailAttachmentInfo` | `MalwareDetectionMethod` <br> `PhishDetectionMethod` | `DetectionMethods` | Daha fazla algılama yöntemi ekleyin |
    | `EmailAttachmentInfo`  | `MalwareFilterVerdict` <br>`PhishFilterVerdict` | `ThreatTypes` | Daha fazla tehdit türü ekleyin |
    | `EmailEvents` | `MalwareDetectionMethod` <br> `PhishDetectionMethod` | `DetectionMethods` | Daha fazla algılama yöntemi ekleyin |
    | `EmailEvents` | `MalwareFilterVerdict` <br>`PhishFilterVerdict` | `ThreatTypes` | Daha fazla tehdit türü ekleyin |


2. `EmailAttachmentInfo` ve `EmailEvents` tablolarında, `ThreatNames` e-posta tehdidi hakkında daha fazla bilgi vermek için sütun eklenmiştir. Bu sütun İstenmeyen Posta veya Kimlik Avı gibi değerler içerir.

3. [DeviceInfo](advanced-hunting-deviceinfo-table.md) tablosunda sütun, `DeviceObjectId` müşteri geri bildirimlerine göre sütunla `AadDeviceId` değiştirildi.

4. [DeviceEvents](advanced-hunting-deviceevents-table.md) tablosunda, eylemin açıklamasını daha iyi yansıtacak şekilde birkaç ActionType adı değiştirildi. Değişikliklerin ayrıntılarına aşağıdan ulaşabilirsiniz.

    | Tablo adı | Özgün ActionType adı | Yeni ActionType adı | Değişiklik nedeni
    |--|--|--|--|
    | `DeviceEvents` | `DlpPocPrintJob` | `FilePrinted` | Müşteri geri bildirimi |
    | `DeviceEvents` | `UsbDriveMount` | `UsbDriveMounted` | Müşteri geri bildirimi |
    | `DeviceEvents` | `UsbDriveUnmount` | `UsbDriveUnmounted` | Müşteri geri bildirimi |
    | `DeviceEvents` | `WriteProcessMemoryApiCall` | `WriteToLsassProcessMemory` | Müşteri geri bildirimi |

## <a name="march-2021"></a>Mart 2021

Tablo `DeviceTvmSoftwareInventoryVulnerabilities` kullanım dışı bırakıldı. yerine ve `DeviceTvmSoftwareVulnerabilities` tabloları yer `DeviceTvmSoftwareInventory` alır.

## <a name="may-2021"></a>Mayıs 2021

Tablo `AppFileEvents` kullanım dışı bırakıldı. Tablo, `CloudAppEvents` bulut hizmetlerindeki `AppFileEvents` diğer etkinliklerle birlikte tabloda yer alan bilgileri içerir.

## <a name="related-topics"></a>İlgili konular
- [Gelişmiş avcılığa genel bakış](advanced-hunting-overview.md)
- [Şemayı anlayın](advanced-hunting-schema-tables.md)
