---
title: Microsoft 365 Defender Akışı API'sinde desteklenen veri akışı olay türleri
description: Akış API'si tarafından hangi akış olay türlerinin (tabloları) destekle ilgili bilgi edinin
keywords: ham veri dışarı aktarma, Akış API'si, API, Etkinlik hub'ları, Azure depolama, depolama hesabı, Koruma, ham veri paylaşımı
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: e8264ccb9e3181f6b58a6206417eb2b842bec6e7
ms.sourcegitcommit: 317fab13e84b2867087a6ba0a593313ecf43bbed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2021
ms.locfileid: "62988812"
---
# <a name="supported-microsoft-365-defender-streaming-event-types-in-event-streaming-api"></a>Olay Microsoft 365 Defender API'sinde akış olay türleri için destek

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

[!include[Prerelease information](../../includes/prerelease.md)]


Olay Akışı API'si daha fazla olay türü desteklemek için sürekli genişletiliyor. Şu anda genel önizlemede olan veya henüz desteklememiş olan hangi Tablo tablolarını genel olarak kullanılabilir olduğunu öğrenin. 
**Yeni - E-posta olay türleri/tabloları artık GA oldu**

## <a name="hunting-tables-support-status-in-event-streaming-api"></a>Etkinlik Akışı API'sinde tablo desteği durumu

Aşağıdaki tablo yalnızca akış API'sinde desteklenen tabloların listesini içerir ve tüm AH şemasını içermez. API'nin tam listesi için bkz [. Şema tablolarını öğrenme](advanced-hunting-schema-tables.md#learn-the-schema-tables).


| Tablo adı | Durum |
|------------|-------------|
| **[AlertEvidence](advanced-hunting-alertevidence-table.md)** | GA |
| **[UyarıBilgileri](advanced-hunting-alertinfo-table.md)** | GA  |
| **[DeviceEvents](advanced-hunting-deviceevents-table.md)** |GA |
| **[DeviceFileCertificateInfo](advanced-hunting-DeviceFileCertificateInfo-table.md)** |GA |
| **[DeviceFileEvents](advanced-hunting-devicefileevents-table.md)** | GA |
| **[DeviceImageLoadEvents](advanced-hunting-deviceimageloadevents-table.md)** | GA |
| **[CihazBilgileri](advanced-hunting-deviceinfo-table.md)** | GA |
| **[DeviceLogonEvents](advanced-hunting-devicelogonevents-table.md)** | GA |
| **[DeviceNetworkEvents](advanced-hunting-devicenetworkevents-table.md)** |GA |
| **[DeviceNetworkInfo](advanced-hunting-devicenetworkinfo-table.md)** | GA |
| **[DeviceProcessEvents](advanced-hunting-deviceprocessevents-table.md)** | GA |
| **[DeviceRegistryEvents](advanced-hunting-deviceregistryevents-table.md)** | GA |
| **[EmailAttachmentInfo](advanced-hunting-emailattachmentinfo-table.md)** | GA |
| **[EmailEvents](advanced-hunting-emailevents-table.md)** | GA |
| **[EmailPostDeliveryEvents](advanced-hunting-emailpostdeliveryevents-table.md)** | GA |
| **[EmailUrlInfo](advanced-hunting-emailurlinfo-table.md)** | GA |


