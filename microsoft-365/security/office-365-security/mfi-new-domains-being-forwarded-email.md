---
title: Yeni alan adları yönlendiriliyor e-posta içgörüsü
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
audience: ITPro
ms.topic: conceptual
ms.localizationpriority: medium
ms.assetid: ''
description: Yöneticiler, Güvenlik & Uyumluluk Merkezi'ndeki Posta akışı panosunda yeni etki alanlarının iletilen e-posta içgörülerini kullanarak kullanıcılarının hiç iletilmemiş dış etki alanlarına ne zaman ileti ilettiğini araştırabilir.
ms.technology: mdo
ms.prod: m365-security
ms.collection: M365-security-compliance
ms.openlocfilehash: 1dbcf83d234611af1d209d83191cee24f5bee579
ms.sourcegitcommit: 45bc65972d4007b2aa7760d4457a0d2699f81926
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/20/2022
ms.locfileid: "64974355"
---
# <a name="new-domains-being-forwarded-email-insight-in-the-security--compliance-center"></a>Güvenlik & Uyumluluk Merkezi'nde iletilen yeni etki alanları e-posta içgörüleri

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Uygulandığı öğe**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Office 365 için Microsoft Defender plan 1 ve plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

E-posta iletilerini belirli etki alanlarındaki dış alıcılara iletmek için geçerli iş nedenleri vardır. Ancak, kuruluşunuzdaki kullanıcılar aniden iletileri kuruluşunuzdaki hiç kimsenin ileti iletmediği bir etki alanına (yeni bir etki alanı) iletmeye başladığında şüphelidir.

Bu koşul, kullanıcı hesaplarının gizliliğinin tehlikeye girdiğini gösterebilir. Hesapların gizliliğinin ihlal edildiğini düşünüyorsanız, bkz. [Güvenliği aşılmış bir e-posta hesabını yanıtlama](responding-to-a-compromised-email-account.md).

[Güvenlik & Uyumluluk Merkezi'nde](https://protection.office.com) **iletilen Yeni etki alanları e-posta** içgörüleri, kuruluşunuzdaki kullanıcılar iletileri yeni etki alanlarına iletirken size bildirir.

Bu içgörü yalnızca sorun algılandığında ve [İletme raporu](view-mail-flow-reports.md#forwarding-report) sayfasında görüntülenir.

:::image type="content" source="../../media/mfi-new-domains-being-forwarded.png" alt-text="İletilen Yeni etki alanları e-posta içgörüleri" lightbox="../../media/mfi-new-domains-being-forwarded.png":::

Pencere öğesine tıkladığınızda, iletilen iletiler hakkında daha fazla ayrıntı bulabileceğiniz ve [İletme raporuna](view-mail-flow-reports.md#forwarding-report) bir bağlantı da dahil olmak üzere bir açılır pencere açılır öğesi görüntülenir.

:::image type="content" source="../../media/mfi-new-domains-being-forwarded-details.png" alt-text="Yeni etki alanları iletiliyor e-posta içgörülerine tıkladıktan sonra görüntülenen Ayrıntılar açılır öğesi" lightbox="../../media/mfi-new-domains-being-forwarded-details.png":::

Ayrıca, (**Raporlar** \> **Panosu** veya <https://protection.office.com/insightdashboard>) üzerindeki **En iyi içgörüler & öneriler** alanında **Tümünü görüntüle'ye** tıkladıktan sonra içgörüleri seçtiğinizde de bu ayrıntılar sayfasına ulaşabilirsiniz.

Dış etki alanlarına otomatik ileti iletmeyi önlemek için, dış etki alanlarının bazıları veya tümü için bir uzak etki alanı yapılandırın. Daha fazla bilgi için bkz. [Exchange Online'de uzak etki alanlarını yönetme](/Exchange/mail-flow-best-practices/remote-domains/manage-remote-domains).

## <a name="related-topics"></a>İlgili konular

Posta akışı panosundaki diğer içgörüler hakkında bilgi için [Bkz. Güvenlik & Uyumluluk Merkezi'ndeki Posta akışı içgörüleri](mail-flow-insights-v2.md).
