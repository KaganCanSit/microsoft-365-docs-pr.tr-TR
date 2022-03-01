---
title: Uç nokta olayı için Microsoft Defender'ı stream
description: Etkinlik Hub'ları veya Azure depolama hesabına Gelişmiş Av etkinliklerini akışı için Uç nokta için Microsoft Defender'ı yapılandırmayı öğrenin
keywords: ham veri dışarı aktarma, akış API'si, API, Etkinlik hub'ları, Azure depolama, depolama hesabı, Gelişmiş Koruma, ham veri paylaşımı
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
ms.custom: api
ms.openlocfilehash: 94a815a6fc734c8e8e310a17f2e73931f4ffab5c
ms.sourcegitcommit: 348f3998a029a876a9dcc031f808e9e350804f22
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2021
ms.locfileid: "62996494"
---
# <a name="raw-data-streaming-api"></a>Ham Veri Akışı API'si

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)

> Uç Nokta için Defender'ı deneyimli yapmak mı istiyor musunuz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-configuresiem-abovefoldlink)

## <a name="stream-advanced-hunting-events-to-event-hubs-andor-azure-storage-account"></a>Etkinlik Hub'ları ve/veya Azure depolama hesabına Gelişmiş Av etkinliklerini akışla izle

Uç Nokta için Microsoft Defender, Etkinlik Hub'ları [](../defender/advanced-hunting-overview.md) ve/veya Azure [](/azure/event-hubs/) depolama hesabına Gelişmiş Avla aracılığıyla kullanılabilen [akış olaylarını destekler](/azure/storage/common/storage-account-overview).

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4r4ga]

## <a name="in-this-section"></a>Bu bölümde

Konu|Açıklama
:---|:---
[Uç nokta olaylarının Microsoft Defender'ı Azure Olay Hub'lara akışı](raw-data-export-event-hub.md)|Kiracınıza akış API'sini etkinleştirme hakkında bilgi edinin ve Gelişmiş Av'ı Etkinlik Hub'lara akışla akışı yapmak için Uç Nokta için [Defender'ı](advanced-hunting-overview.md) yapılandırmayı öğrenin.
[Azure depolama hesabınıza Uç nokta olayları için Stream Defender](raw-data-export-storage.md)|Kiracınıza akış API'sini etkinleştirme hakkında bilgi edinin ve Azure depolama hesabınıza Gelişmiş Ekinlik [](advanced-hunting-overview.md) akışı yapmak için Uç Nokta için Defender'ı yapılandırın.

## <a name="related-topics"></a>İlgili konular

- [Gelişmiş Ava Genel Bakış](advanced-hunting-overview.md)
- [Azure Olay Hub'ları belgeleri](/azure/event-hubs/)
- [Azure Depolama Hesabı belgeleri](/azure/storage/common/storage-account-overview)