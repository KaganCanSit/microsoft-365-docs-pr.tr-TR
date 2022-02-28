---
title: Akış Microsoft 365 Defender etkinlikleri
description: Etkinlik Hub'ları Microsoft 365 Defender Azure depolama hesabına Gelişmiş Av etkinliklerini akışı için nasıl yapılandırabilirsiniz hakkında bilgi edinin
keywords: ham veri dışarı aktarma, akış API'si, API, Etkinlik hub'ları, Azure depolama, depolama hesabı, Gelişmiş Koruma, ham veri paylaşımı
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
ms.openlocfilehash: c6c3cedffb1b827d441d37cc8beb53b20f3521f2
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62985006"
---
# <a name="streaming-api"></a>Akış API'si

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

[!include[Prerelease information](../../includes/prerelease.md)]

## <a name="stream-advanced-hunting-events-to-event-hubs-andor-azure-storage-account"></a>Etkinlik Hub'ları ve/veya Azure depolama hesabına Gelişmiş Av etkinliklerini akışla izleyin.

Microsoft 365 Defender Gelişmiş Ekinlik aracılığıyla Etkinlik Hub'ları ve/veya [](/azure/event-hubs/) Azure depolama hesabına etkinlik [akışını destekler](/azure/event-hubs/).[](../defender/advanced-hunting-overview.md)

Akış API'si Microsoft 365 Defender daha fazla bilgi için [videoya bakın](https://www.microsoft.com/en-us/videoplayer/embed/RE4r4ga).

## <a name="in-this-section"></a>Bu bölümde

Konu | Açıklama
:---|:---
[Etkinlikleri Azure Etkinlik Hub'lara akışı](streaming-api-event-hub.md)| Kiracınıza akış API'sini etkinleştirme ve Etkinlik Hub'larında Gelişmiş Microsoft 365 Defender akışı için bu API'yi yapılandırma hakkında bilgi edinin.[](../defender/advanced-hunting-overview.md)
[Etkinlikleri Azure depolama hesabınıza akışla uygulama](streaming-api-storage.md)| Kiracınıza akış API'sini etkinleştirme ve Azure depolama hesabınıza Gelişmiş Microsoft 365 Defender akışı için aboneliği yapılandırma hakkında bilgi [](advanced-hunting-overview.md) edinin.
[Desteklenen olay türleri](supported-event-types.md) | Akış API'sinde hangi Gelişmiş Av etkinlik türlerini desteklediğini öğrenin.


## <a name="related-topics"></a>İlgili konular
- [Gelişmiş Ava Genel Bakış](../defender/advanced-hunting-overview.md)
- [Azure Olay Hub'ları belgeleri](/azure/event-hubs/)
- [Azure Depolama Hesabı belgeleri](/azure/storage/common/storage-account-overview)
