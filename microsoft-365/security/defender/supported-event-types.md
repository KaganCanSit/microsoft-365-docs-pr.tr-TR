---
title: Olay Akışı API'sinde desteklenen Microsoft 365 Defender akış olayı türleri
description: Akış API'sinde hangi akış olay türlerinin (tablolar) desteklendiği hakkında bilgi edinin
keywords: ham veri dışarı aktarma, Akış API'si, API, Olay hub'ları, Azure depolama, depolama hesabı, Tehdit Avcılığı, ham veri paylaşımı
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
ms.openlocfilehash: 4f6f098c9d2ec09a777110955b8acb1663e102ed
ms.sourcegitcommit: f181e110cdb983788a86f30d5bb018e53c83e64d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/13/2022
ms.locfileid: "66057861"
---
# <a name="supported-microsoft-365-defender-streaming-event-types-in-event-streaming-api"></a>Olay akışı API Microsoft 365 Defender sinde olay akış türleri desteklenir

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Şunlar için geçerlidir:**
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

[!include[Prerelease information](../../includes/prerelease.md)]


Olay Akışı API'si, daha fazla olay türünü destekleyecek şekilde sürekli genişletiliyor. Şu anda genel önizleme aşamasında olan veya henüz desteklenmeyen Hangi Avcılık tablolarının genel kullanıma sunulduğu hakkında bilgi edinin. 
**Yeni - E-posta olay türleri/tabloları artık GA**

## <a name="hunting-tables-support-status-in-event-streaming-api"></a>Olay Akışı API'sinde tehdit avcılığı tabloları destek durumu

Aşağıdaki tablo yalnızca akış API'sinde desteklenen tabloların listesini içerir ve tüm AH şeması dahil değildir. API'nin tam listesi için bkz. [Şema tablolarını öğrenme](advanced-hunting-schema-tables.md#learn-the-schema-tables).

| Tablo adı | Durum<br>(Ticari) | GCC | yüksek GCC | Dod |
|----|----|----|----|----|
| **[AlertEvidence](advanced-hunting-alertevidence-table.md)** | GA | GA | GA | GA |
| **[AlertInfo](advanced-hunting-alertinfo-table.md)** | GA | GA | GA | GA |
| **[DeviceEvents](advanced-hunting-deviceevents-table.md)** |GA | GA | GA | GA |
| **[DeviceFileCertificateInfo](advanced-hunting-DeviceFileCertificateInfo-table.md)** |GA | GA | GA | GA |
| **[DeviceFileEvents](advanced-hunting-devicefileevents-table.md)** | GA | GA | GA | GA |
| **[DeviceImageLoadEvents](advanced-hunting-deviceimageloadevents-table.md)** | GA | GA | GA | GA |
| **[DeviceInfo](advanced-hunting-deviceinfo-table.md)** | GA | GA | GA | GA |
| **[DeviceLogonEvents](advanced-hunting-devicelogonevents-table.md)** | GA | GA | GA | GA |
| **[DeviceNetworkEvents](advanced-hunting-devicenetworkevents-table.md)** |GA | GA | GA | GA |
| **[DeviceNetworkInfo](advanced-hunting-devicenetworkinfo-table.md)** | GA | GA | GA | GA |
| **[DeviceProcessEvents](advanced-hunting-deviceprocessevents-table.md)** | GA | GA | GA | GA |
| **[DeviceRegistryEvents](advanced-hunting-deviceregistryevents-table.md)** | GA | GA | GA | GA |
| **[EmailAttachmentInfo](advanced-hunting-emailattachmentinfo-table.md)** | GA |![Hayır](../defender-endpoint/images/svg/check-no.svg)|![Hayır](../defender-endpoint/images/svg/check-no.svg)|![Hayır](../defender-endpoint/images/svg/check-no.svg)|
| **[EmailEvents](advanced-hunting-emailevents-table.md)** | GA |![Hayır](../defender-endpoint/images/svg/check-no.svg)|![Hayır](../defender-endpoint/images/svg/check-no.svg)|![Hayır](../defender-endpoint/images/svg/check-no.svg)|
| **[EmailPostDeliveryEvents](advanced-hunting-emailpostdeliveryevents-table.md)** | GA |![Hayır](../defender-endpoint/images/svg/check-no.svg)|![Hayır](../defender-endpoint/images/svg/check-no.svg)|![Hayır](../defender-endpoint/images/svg/check-no.svg)|
| **[EmailUrlInfo](advanced-hunting-emailurlinfo-table.md)** | GA |![Hayır](../defender-endpoint/images/svg/check-no.svg)|![Hayır](../defender-endpoint/images/svg/check-no.svg)|![Hayır](../defender-endpoint/images/svg/check-no.svg)|
| **[IdentityLogonEvents](advanced-hunting-identitylogonevents-table.md)**|GA|![Hayır](../defender-endpoint/images/svg/check-no.svg)|![Hayır](../defender-endpoint/images/svg/check-no.svg)|![Hayır](../defender-endpoint/images/svg/check-no.svg)|
| **[IdentityQueryEvents](advanced-hunting-identityqueryevents-table.md)**|GA|![Hayır](../defender-endpoint/images/svg/check-no.svg)|![Hayır](../defender-endpoint/images/svg/check-no.svg)|![Hayır](../defender-endpoint/images/svg/check-no.svg)|
| **[IdentityDirectoryEvents](advanced-hunting-identitydirectoryevents-table.md)**|GA|![Hayır](../defender-endpoint/images/svg/check-no.svg)|![Hayır](../defender-endpoint/images/svg/check-no.svg)|![Hayır](../defender-endpoint/images/svg/check-no.svg)|
| **[CloudAppEvents](advanced-hunting-cloudappevents-table.md)**|GA|![Hayır](../defender-endpoint/images/svg/check-no.svg)|![Hayır](../defender-endpoint/images/svg/check-no.svg)|![Hayır](../defender-endpoint/images/svg/check-no.svg)|
