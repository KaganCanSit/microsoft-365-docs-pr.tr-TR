---
title: E-posta ile iletili yeni etki alanları içgörü
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
audience: ITPro
ms.topic: conceptual
ms.localizationpriority: medium
ms.assetid: ''
description: Yöneticiler, kullanıcılarının iletileri daha önce iletilen dış etki alanlarına ne zaman ileteceklerini araştırmak için Güvenlik & Uyumluluk Merkezi'nde Posta akışı panosunda yeni etki alanlarının iletilen e-posta ile ilgili içgörülerini nasıl kullanacaklarını öğrenebilirler.
ms.technology: mdo
ms.prod: m365-security
ms.collection: M365-security-compliance
ms.openlocfilehash: e23d63a519bf69f94ce4990d8851d673826dcb5c
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64475091"
---
# <a name="new-domains-being-forwarded-email-insight-in-the-security--compliance-center"></a>Güvenlik ve Uyumluluk Merkezi'nde e-posta ile iletili yeni & bilgileri

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Geçerli olduğu yer:**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Office 365 için Microsoft Defender plan 1 ve plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

E-posta iletilerini belirli etki alanlarındaki dış alıcılara iletmenin geçerli iş nedenleri vardır. Ancak, organizasyonu kullananlar aniden iletileri kuruluş içinde hiç kimsenin iletileri iletmemiştir (yeni bir etki alanına) iletmemiştir ve bu durum şüphelidir.

Bu koşul kullanıcı hesaplarının güvenliği ihlal edilmiş olduğunu gösteriyor olabilir. Hesapların ele geçirildiklerine şüpheleniyorsanız bkz. Güvenliği tehlikeye [atılmış bir e-posta hesabını yanıtla.](responding-to-a-compromised-email-account.md)

Güvenlik **ve Uyumluluk Merkezi'nde** E-posta ile iletili yeni [etki alanları](https://protection.office.com) &, organizasyonu kullanan kullanıcılar iletileri yeni etki alanlarına ileteceklerini size haber verir.

Bu içgörü ancak sorun algılandığında ve Rapor [iletildi sayfasında görüntülenir](view-mail-flow-reports.md#forwarding-report) .

:::image type="content" source="../../media/mfi-new-domains-being-forwarded.png" alt-text="E-posta ile iletili yeni etki alanları içgörü" lightbox="../../media/mfi-new-domains-being-forwarded.png":::


Widget'a tıklarsanız, iletili iletiler hakkında daha fazla ayrıntıya ulaşabilirsiniz ve bu açılır pencere öğesi, İletim raporuna [bir bağlantı içerir](view-mail-flow-reports.md#forwarding-report).

:::image type="content" source="../../media/mfi-new-domains-being-forwarded-details.png" alt-text="Yeni etki alanları iletildi e-posta içgörüne tıklandıktan sonra görüntülenen Ayrıntılar açılır" lightbox="../../media/mfi-new-domains-being-forwarded-details.png":::

Ayrıca, En iyi öngörüler ve öneriler **alanında (** \> Raporlar Panosu veya ) Hepsini görüntüle'ye **tıklarken** & bu ayrıntılar sayfasına **da bakabilirsiniz**<https://protection.office.com/insightdashboard>.

Dış etki alanlarına otomatik ileti iletmeyi önlemek için, dış etki alanlarının bir bazıları veya bazıları için uzak etki alanı yapılandırabilirsiniz. Daha fazla bilgi için bkz[. Exchange Online'da uzak etki alanlarını yönetme](/Exchange/mail-flow-best-practices/remote-domains/manage-remote-domains).

## <a name="related-topics"></a>İlgili konular

Posta akışı panosunda yer alan diğer içgörüler hakkında bilgi için, Güvenlik ve Uyumluluk Merkezi'nde [Posta & bakın](mail-flow-insights-v2.md).