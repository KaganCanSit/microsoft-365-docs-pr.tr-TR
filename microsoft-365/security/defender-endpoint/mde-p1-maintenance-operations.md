---
title: Uç Nokta için Microsoft Defender Plan 1'i yönetme
description: Uç Nokta Planı 1 için Defender'ı koruyun ve güncelleştirin. Ayarları yönetin, güncelleştirmeleri alın ve hatalı pozitif sonuçları/negatifleri ele alın.
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
ms.openlocfilehash: 417dd33eed846e45453464e63ff403374ce224dc
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2022
ms.locfileid: "64667416"
---
# <a name="manage-microsoft-defender-for-endpoint-plan-1"></a>Uç Nokta için Microsoft Defender Plan 1'i yönetme

**Uygulandığı öğe**
- [Uç Nokta için Microsoft Defender Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Kuruluşunuzda Endpoint Plan 1 için Defender'ı kullandığınızda, güvenlik ekibiniz güvenlik çözümünüzü korumak için belirli adımları izleyebilir. Güvenlik ekibiniz bakım ve operasyon planınızı bir araya getirirken en azından aşağıdaki etkinlikleri eklediğinizden emin olun:

- [Güvenlik zekası ve ürün güncelleştirmelerini yönetme](#manage-security-intelligence-and-product-updates)
- [Uç Nokta için Defender'da ince ayar yapma ve ayarlama](#fine-tune-and-adjust-defender-for-endpoint)
- [Hatalı pozitifleri/negatifleri ele al](#address-false-positivesnegatives)

## <a name="manage-security-intelligence-and-product-updates"></a>Güvenlik zekası ve ürün güncelleştirmelerini yönetme

Microsoft Defender Virüsten Koruma güncel tutmak, yeni kötü amaçlı yazılımlara ve saldırı tekniklerine karşı koruma açısından kritik öneme sahiptir. Microsoft, güvenlik bilgileri, virüsten koruma ve kötü amaçlı yazılımdan koruma için düzenli güncelleştirmeler yayınlar. Güncelleştirmeler iki kategoriye ayrılır: 

- Güvenlik bilgileri güncelleştirmeleri
- Ürün güncelleştirmeleri 

Güvenlik bilgileri ve ürün güncelleştirmelerinizi yönetmek için bkz. [Microsoft Defender Virüsten Koruma güncelleştirmelerini yönetme ve temelleri uygulama](manage-updates-baselines-microsoft-defender-antivirus.md).

## <a name="fine-tune-and-adjust-defender-for-endpoint"></a>Uç Nokta için Defender'da ince ayar yapma ve ayarlama

Uç Nokta için Defender size çok fazla esneklik ve yapılandırma seçeneği sunar. Ayarlarınızı kuruluşunuzun gereksinimlerine uyacak şekilde ayarlayabilir ve hassas ayarlar yapabilirsiniz. Örneğin, uç nokta güvenlik ayarlarınızı yönetmek için Microsoft Endpoint Manager, grup ilkesi ve diğer yöntemleri kullanabilirsiniz. 

Daha fazla bilgi için bkz. [Uç Nokta için Defender'ı yönetme](manage-mde-post-migration.md).

## <a name="address-false-positivesnegatives"></a>Hatalı pozitifleri/negatifleri ele al

Hatalı pozitif, aslında bir tehdit olmasa da kötü amaçlı olarak algılanan dosya veya işlem gibi bir yapıttır. Hatalı negatif, aslında bir tehdit olarak algılanmamış bir varlıktır. Uç Nokta için Defender da dahil olmak üzere herhangi bir uç nokta koruma çözümünde hatalı pozitif/negatifler oluşabilir. Bununla birlikte, aşağıdaki görüntüde gösterildiği gibi bu tür sorunları gidermek ve çözümünüzde ince ayar yapmak için izleyebileceğiniz adımlar vardır:

:::image type="content" source="../../media/defender-endpoint/false-positives-overview.png" alt-text="Hatalı pozitifler ve negatifler sürecine genel bakış" lightbox="../../media/defender-endpoint/false-positives-overview.png":::

Uç Nokta için Defender'da hatalı pozitifler/negatifler görüyorsanız bkz. [Uç Nokta için Microsoft Defender hatalı pozitifleri/negatifleri adresle](defender-endpoint-false-positives-negatives.md).

## <a name="next-steps"></a>Sonraki adımlar

- [Uç Nokta için Microsoft Defender'deki yeniliklere göz atın](whats-new-in-microsoft-defender-endpoint.md)