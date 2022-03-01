---
title: Desteklenen Microsoft 365 Defender API'ler
description: Desteklenen Microsoft 365 Defender API'ler
keywords: Microsoft 365 Defender API'ler, api
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.custom: api
ms.openlocfilehash: 1785186f778c489cb4a254fe39cc41921a4de86e
ms.sourcegitcommit: 6f3bc00a5cf25c48c61eb3835ac069e9f41dc4db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2022
ms.locfileid: "63014138"
---
# <a name="supported-microsoft-365-defender-apis"></a>Desteklenen Microsoft 365 Defender API'ler 

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- Microsoft 365 Defender

> [!IMPORTANT]
> Bazı bilgiler, ticari olarak piyasaya sürmeden önce önemli ölçüde değiştirilmiş olabilir, önceden satın alınan ürünle ilgilidir. Microsoft, burada sağlanan bilgilerle ilgili olarak açık veya zımni hiçbir garanti vermez.

## <a name="list-of-available-apis"></a>Kullanılabilir API'lerin listesi

Makale | Açıklama
-|-
[Gelişmiş Av API'si](api-advanced-hunting.md) | Gelişmiş Arama sorgularını çalıştırma.
[Olay API'leri](api-incident.md) | Diğer pratik görevlerle birlikte olayları listele ve güncelleştirin.
[Akış API'si](streaming-api.md) | Gerçek zamanlı etkinlikleri ve uyarıları tek bir veri akışında olduğu gibi gönderebilirsiniz.

### <a name="endpoint-uris"></a>Uç Nokta  URL'leri

Ana API'lerin her ikisi için de temel URI'dir: https://api.security.microsoft.com. Daha iyi bir performans için coğrafi konumunıza daha yakın bir sunucu kullanın:

- Amerika Birleşik Devletleri: api-us.security.microsoft.com
- Avrupa: api-eu.security.microsoft.com
- Birleşik Krallık: api-uk.security.microsoft.com

Belirteçler erişimle elde edilir https://api.security.microsoft.com.

Yol boyunca yer alan tüm `/api` [API'ler OData](/odata/overview) Protokolünü kullanır; örneğin, https://api.security.microsoft.com/api/incidents.

## <a name="related-articles"></a>İlgili makaleler

- [Microsoft 365 Defender API'lere genel bakış](api-overview.md)
- [Api'lere Microsoft 365 Defender erişme](api-access.md)
- [Akış API'si](../defender-endpoint/raw-data-export.md)
- [API sınırları ve lisanslama hakkında bilgi edinin](api-terms.md)
- [Hata kodlarını anlama](api-error-codes.md)
