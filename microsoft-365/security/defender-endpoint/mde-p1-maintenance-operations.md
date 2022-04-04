---
title: Plan 1 Uç Nokta için Microsoft Defender i yönetme
description: Uç Nokta Plan 1 için Defender'ı koruma ve güncelleştirme. Ayarları yönetin, güncelleştirmeleri alın ve hatalı pozitif/negatif sonuçlardan haberdar olun.
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: ITPro
ms.topic: overview
ms.date: 01/03/2022
ms.prod: m365-security
ms.technology: mdep1
ms.localizationpriority: medium
ms.reviewer: inbadian
f1.keywords: NOCSH
ms.collection: M365-security-compliance
ms.openlocfilehash: 5217cf3f8b61c4e5bc24dfc205fb78c5bde5a3b5
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64466641"
---
# <a name="manage-microsoft-defender-for-endpoint-plan-1"></a>Plan 1 Uç Nokta için Microsoft Defender i yönetme

**Geçerli olduğu yer:**
- [Uç Nokta için Microsoft Defender Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Siz kuruluşta Uç Nokta Planı 1 için Defender'ı kullanacı olarak, güvenlik çözümünüz korumanız için güvenlik ekibinin bazı adımlarını atabilirsiniz. Güvenlik ekipleriniz bakım ve işlemler planınızı bir araya geldiklerinden, en azından aşağıdaki etkinlikleri dahil etmek için emin olun:

- [Güvenlik zekası ve ürün güncelleştirmelerini yönetme](#manage-security-intelligence-and-product-updates)
- [İnce ayar ve Uç Nokta için Defender'ı ayarlama](#fine-tune-and-adjust-defender-for-endpoint)
- [Hatalı pozitif/negatifleri adresle](#address-false-positivesnegatives)

## <a name="manage-security-intelligence-and-product-updates"></a>Güvenlik zekası ve ürün güncelleştirmelerini yönetme

Yeni Microsoft Defender Virüsten Koruma yazılıma ve saldırı tekniklerine karşı koruma açısından, güncel tutmak çok önemlidir. Microsoft, güvenlik zekası, virüsten koruma ve kötü amaçlı yazılımlardan koruma için düzenli güncelleştirmeler yayımlar. Güncelleştirmeler iki kategoriye ayrılır: 

- Güvenlik zekası güncelleştirmeleri
- Ürün güncelleştirmeleri 

Güvenlik zekası ve ürün güncelleştirmelerinizi yönetmek için bkz. Microsoft Defender Virüsten Koruma [güncelleştirmeleri yönetme ve taban çizgilerini uygulama](manage-updates-baselines-microsoft-defender-antivirus.md).

## <a name="fine-tune-and-adjust-defender-for-endpoint"></a>İnce ayar ve Uç Nokta için Defender'ı ayarlama

Uç Nokta için Defender size çok fazla esneklik ve yapılandırma seçeneği sunar. Ayarlarınızı, kuruluşun ihtiyaçlarına uyacak şekilde ayarlayabilir ve ince ayar yapabilirsiniz. Örneğin, uç nokta güvenlik ayarlarınızı Microsoft Endpoint Manager, grup ilkesi ve diğer yöntemleri kullanabilirsiniz. 

Daha fazla bilgi edinmek için bkz. [Uç Nokta için Defender'ı Yönetme](manage-mde-post-migration.md).

## <a name="address-false-positivesnegatives"></a>Hatalı pozitif/negatifleri adresle

Hatalı pozitif bir yapı, aslında bir tehdit olmayan, kötü amaçlı olarak algılanan dosya veya işlem gibi bir yapıdır. Yanlış negatiflik, aslında tehdit olarak algılanmadı olsa da var olan bir varlıktır. Uç nokta için Defender dahil olmak üzere herhangi bir uç nokta koruma çözümünde hatalı pozitif/negatif sonuçlar oluşabilir. Bununla birlikte, aşağıdaki resimde gösterilen gibi bu tür sorunları ele almak ve çözüme ince ayar yapmak için atılması gereken adımlar vardır:

:::image type="content" source="../../media/defender-endpoint/false-positives-overview.png" alt-text="Hatalı pozitif ve negatif sonuçlar sürecine genel bakış" lightbox="../../media/defender-endpoint/false-positives-overview.png":::

Uç nokta için Defender'da hatalı pozitif/negatif sonuçlar görüyorsanız bkz. Hatalı pozitif[/negatifleri](defender-endpoint-false-positives-negatives.md) adrese Uç Nokta için Microsoft Defender.

## <a name="next-steps"></a>Sonraki adımlar

- [Uç Nokta için Microsoft Defender'daki Uç Nokta için Microsoft Defender](whats-new-in-microsoft-defender-endpoint.md)