---
title: Otomatik iletili iletiler içgörü
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
audience: ITPro
ms.topic: conceptual
ms.localizationpriority: medium
ms.assetid: b5543faa-44fa-44c5-8180-fb835e7e452d
description: Yöneticiler, Otomatik iletili iletiler raporu hakkında Bilgi edinmek için Güvenlik ve Uyumluluk Merkezi'nin Posta & edinebilirsiniz.
ms.technology: mdo
ms.prod: m365-security
ms.collection: M365-security-compliance
ms.openlocfilehash: 4603e7d895c847513a41dc52764070f970a50d15
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64476389"
---
# <a name="auto-forwarded-messages-insight-in-the-security--compliance-center"></a>Güvenlik ve Uyumluluk Merkezi'nde otomatik iletili & içgörü

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Geçerli olduğu yer:**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Office 365 için Microsoft Defender plan 1 ve plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Güvenlik [](mail-flow-insights-v2.md) [& ve](https://protection.office.com) **Uyumluluk Merkezi'nin** Posta akışı panosunda yer alan Otomatik İletiler iletileri içgörüsi, kuruluştan dış etki alanlarındaki alıcılara otomatik olarak iletilene iletiler hakkında bilgi görüntüler.

:::image type="content" source="../../media/mfi-auto-forwarded-messages.png" alt-text="Güvenlik ve Uyumluluk Merkezi'nde otomatik olarak iletili & widget'tır" lightbox="../../media/mfi-auto-forwarded-messages.png":::

## <a name="auto-forwarded-messages-details"></a>Otomatik iletili ileti ayrıntıları

Widget'ta iletilerin sayısına tıklarsanız, otomatik iletili iletiler hakkında daha fazla bilgi gösteren bir açılır pencere görüntülenir:

- **İletileri iletme yöntemleriyle otomatik olarak iletilebilirsiniz**:

  - **Posta akış kurallarına göre**
  - **Gelen Kutusu kurallarına göre**
  - **SMTP iletmeyle: Bu** yöntem, yöneticilerin bir posta kutusunda bir posta kutusu için e-posta iletmeyi yapılandırma konusunda açıklandığı şekilde [yapılandırebilecekleri otomatik iletmeyi gösterir](/Exchange/recipients-in-exchange-online/manage-user-mailboxes/configure-email-forwarding).
  - Daha ayrıntılı bilgi için [Rapor iletme](view-mail-flow-reports.md#forwarding-report) bağlantısı.

- **Etki alanları ve kullanıcılar tarafından otomatik iletilene iletiler**:

  - **İlk 5 etki alanına iletildi**
  - **Yeni etki alanları (geçen hafta)**
  - **İlk 5 kullanıcı iletme**
  - **Yeni kullanıcılar (geçen hafta)**
  - Daha ayrıntılı bilgi [için Değişiklikleri iletme raporunun](mfi-new-users-forwarding-email.md#forwarding-modifications-report) bağlantısı.

:::image type="content" source="../../media/mfi-auto-forwarded-messages-details.png" alt-text="Güvenlik ve Uyumluluk Merkezi'nde Otomatik iletili & widget'ı" lightbox="../../media/mfi-auto-forwarded-messages-details.png":::

## <a name="insights"></a>Analizler

Rapor verileri temel alınarak iki içgörü oluşturulur:

- [E-postayı iletir yeni kullanıcılar](mfi-new-users-forwarding-email.md)
- [E-posta ile iletili yeni etki alanları](mfi-new-domains-being-forwarded-email.md)

## <a name="see-also"></a>Ayrıca bkz.

Posta akışı panosunda yer alan diğer içgörüler hakkında bilgi için, Güvenlik ve Uyumluluk Merkezi'nde [Posta & bakın](mail-flow-insights-v2.md).