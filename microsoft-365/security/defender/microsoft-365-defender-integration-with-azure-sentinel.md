---
title: Microsoft 365 Defender Sentinel ile tümleştirme
description: Olay ve olaylar için SIEM olarak Microsoft Sentinel Microsoft 365 Defender i kullanın.
keywords: olaylar, uyarılar, araştırma, çözümleme, yanıt, korelasyon, saldırı, makineler, cihazlar, kullanıcılar, kimlikler, kimlik, posta kutusu, e-posta, 365, microsoft, m365
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: josephd
author: JoeDavies-MSFT
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
ms.openlocfilehash: 0c00ecdde6f94d7737cb4dc8d503b83469821fb5
ms.sourcegitcommit: 6f3bc00a5cf25c48c61eb3835ac069e9f41dc4db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2022
ms.locfileid: "63014157"
---
# <a name="microsoft-365-defender-integration-with-microsoft-sentinel"></a>Microsoft 365 Defender Sentinel ile tümleştirme

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- Microsoft 365 Defender

Microsoft Microsoft 365 Defender (önizleme) için Dosya Bağlayıcısı tüm olay ve Microsoft 365 Defender bilgilerini Microsoft Sentinel'e gönderir ve olayları eşitlenmiş durumda tutar. 

Bağlayıcıyı bir kez Microsoft 365 Defender&mdash; ilgili tüm uyarıları, varlıkları ve Uç Nokta için Microsoft Defender, Kimlik için Microsoft Defender, Office 365 için Microsoft Defender ve Bulut Uygulamaları için Microsoft Defender'dan&mdash; alınan ilgili bilgileri içeren olayları içerir güvenlik bilgileri ve olay yönetimi (SIEM) verileri olarak Microsoft Sentinel'e akışını sağlar ve Microsoft Sentinel ile triyak ve olay yanıtı gerçekleştirmenizi sağlayan bağlam sağlar. 

Microsoft Sentinel'de olduğu gibi, olaylar Microsoft 365 Defender ile iki yönlü eşitlenmiş olarak kalır ve böylece olay soruşturması ve yanıt için Azure portalında hem Microsoft 365 Defender portalının hem de Microsoft Sentinel'in avantajlarından yararlanmanıza olanak sağlar.

Microsoft Sentinel'i Microsoft 365 Defender (4 dakika) tümleştirmeyle ilgili bu kısa genel bakış videosunu izleyin.

<br>

>[!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWFIRo]


Bu, şu şekilde çalışır.

:::image type="content" source="../../media/microsoft-365-defender-integration-with-azure-sentinel/microsoft-365-defender-integration-with-azure-sentinel.png" alt-text="Microsoft Sentinel ile Microsoft 365 Defender veri akışı ve paylaşımı.":::

## <a name="next-steps"></a>Sonraki adımlar

1. [Microsoft Sentinel ile Microsoft 365 Defender daha iyi anlaşılmasını sağlar](/azure/sentinel/microsoft-365-defender-sentinel-integration).
2. [Bağlan Microsoft Sentinel'Microsoft 365 Defender verileri de içerir](/azure/sentinel/connect-microsoft-365-defender).

## <a name="see-also"></a>Ayrıca bkz.

- [Microsoft 365 Defender'daki olaylara genel Microsoft 365 Defender](incidents-overview.md)
- [Microsoft Sentinel ile olayları araştırma](/azure/sentinel/tutorial-investigate-cases)
