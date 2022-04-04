---
title: Microsoft 365 Defender'ın Microsoft Sentinel ile tümleştirmesi
description: Olay ve olaylar için SIEM olarak Microsoft Sentinel Microsoft 365 Defender i kullanın.
keywords: olaylar, uyarılar, araştırma, çözümleme, yanıt, korelasyon, saldırı, makineler, cihazlar, kullanıcılar, kimlikler, kimlik, posta kutusu, e-posta, 365, microsoft, m365
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.openlocfilehash: 75aea706cdcb65752b673d32ccff968209ba74b7
ms.sourcegitcommit: 3b8e009ea1ce928505b8fc3b8926021fb91155f3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/28/2022
ms.locfileid: "64499473"
---
# <a name="microsoft-365-defender-integration-with-microsoft-sentinel"></a>Microsoft 365 Defender'ın Microsoft Sentinel ile tümleştirmesi

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- Microsoft 365 Defender

Microsoft Microsoft 365 Defender (önizleme) için Dosya Bağlayıcısı tüm olay ve Microsoft 365 Defender bilgilerini Microsoft Sentinel'e gönderir ve olayları eşitlenmiş durumda tutar. 

Bağlayıcıyı bir kez Microsoft 365 Defender ilgili&mdash; tüm uyarıları, varlıkları ve ilgili bilgileri içeren Uç Nokta için Microsoft Defender, Kimlik için Microsoft Defender, Office 365 için Microsoft Defender ve Microsoft Defender for Cloud Apps Microsoft Sentinel'e&mdash; güvenlik bilgileri ve olay yönetimi (SIEM) verileri olarak akışı sağlar ve Microsoft Sentinel ile triyaklık ve olay yanıtı gerçekleştirmenizi sağlayan bağlam sağlar. 

Microsoft Sentinel'de olduğu gibi, olaylar Microsoft 365 Defender'la iki yönlü eşitlenmiş olarak kalır ve böylece olay araştırma ve yanıt için Microsoft 365 Defender portalında hem de Azure portal'te Microsoft Sentinel'in avantajlarından yararlanmanıza olanak sağlar.

Microsoft Sentinel'i Microsoft 365 Defender (4 dakika) tümleştirmeyle ilgili bu kısa genel bakış videosunu izleyin.

<br>

>[!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWFIRo]


Bu, şu şekilde çalışır.

:::image type="content" source="../../media/microsoft-365-defender-integration-with-azure-sentinel/microsoft-365-defender-integration-with-azure-sentinel.png" alt-text="Web sitesi ve Microsoft Sentinel portalları Microsoft 365 Defender veri akışı ve paylaşımı" lightbox="../../media/microsoft-365-defender-integration-with-azure-sentinel/microsoft-365-defender-integration-with-azure-sentinel.png":::

## <a name="next-steps"></a>Sonraki adımlar

1. [Microsoft Sentinel ile Microsoft 365 Defender daha iyi anlaşılmasını sağlar](/azure/sentinel/microsoft-365-defender-sentinel-integration).
2. [Bağlan Microsoft Sentinel'Microsoft 365 Defender verileri de içerir](/azure/sentinel/connect-microsoft-365-defender).

## <a name="see-also"></a>Ayrıca bkz.

- [Microsoft 365 Defender'daki olaylara genel Microsoft 365 Defender](incidents-overview.md)
- [Microsoft Sentinel ile olayları araştırma](/azure/sentinel/tutorial-investigate-cases)
