---
title: Uç Nokta için Microsoft Defender zaman çizelgesi olay bayraklarını ekleme
description: Cihaz Uç Nokta için Microsoft Defender çizelgesi olay bayraklarını kullanarak
keywords: Uç nokta cihaz zaman çizelgesi için Defender, olay bayrakları
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 44292893249872c1c4b8dc3b4f66d10085fb0a2b
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64471197"
---
# <a name="microsoft-defender-for-endpoint-device-timeline-event-flags"></a>Uç Nokta için Microsoft Defender zaman çizelgesi olay bayraklarını ekleme

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta için Microsoft Defender Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta için Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Defender'ı deneyimli yapmak mı istiyor musunuz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

Uç nokta cihaz zaman çizelgesi için Defender'daki olay bayrakları, olası saldırıları araştırmanız sırasında belirli olayları filtrelemenize ve düzenlemenize yardımcı olur.

Uç nokta cihazı için Defender zaman çizelgesi, cihazda gözlemlenen olayların ve ilişkili uyarıların kronolojik görünümünü sağlar. Bu olay listesi, cihazda gözlemlenen olay, dosya ve IP adresleri üzerinde tam görünürlük sağlar. Liste bazen uzun olabilir. Cihaz zaman çizelgesi olay bayrakları, ilgili olabilir olayları izlemenizi sağlar.

Bir cihaz zaman çizelgesinin üzerinden geçtikten sonra, bayrakla bayrakla etiketledikten sonra belirli olayları sıra olabilir, filtre yer ve dışarı aktarabilirsiniz.

Cihaz zaman çizelgesinde gezinirken belirli olayları arayabilir ve filtre görebilirsiniz. Etkinlik bayraklarını ayarlamak için:

- En önemli olayları vurgulama
- Derine dalın gerektiren etkinlikleri işaretleme
- Temiz ihlal zaman çizelgesini ekleme

## <a name="flag-an-event"></a>Etkinliğe bayrak uygulama

1. Bayrakla bayrakla görmek istediğiniz olayı bulma

2. Bayrak sütununda bayrak simgesine tıklayın. 

:::image type="content" source="images/device-flags.png" alt-text="Cihaz zaman çizelgesi bayrağı" lightbox="images/device-flags.png":::

## <a name="view-flagged-events"></a>Bayraklı etkinlikleri görüntüleme

1. Zaman çizelgesi Filtreleri **bölümünde** Bayraklı **olayları etkinleştirin**.
2. **Uygula**'ya tıklayın. Yalnızca bayraklı olaylar görüntülenir.

Saat çubuğuna tıklayarak ek filtreler uygulayabilirsiniz. Bu yalnızca bayraklı etkinlik öncesi olayları gösterir.  

:::image type="content" source="images/device-flag-filter.png" alt-text="Filtrenin açık olduğu cihaz zaman çizelgesi bayrağı" lightbox="images/device-flag-filter.png":::