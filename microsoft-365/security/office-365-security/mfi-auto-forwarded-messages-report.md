---
title: Otomatik iletilen iletiler içgörüsü
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
audience: ITPro
ms.topic: conceptual
ms.localizationpriority: medium
ms.assetid: b5543faa-44fa-44c5-8180-fb835e7e452d
description: Yöneticiler, Güvenlik & Uyumluluk Merkezi'ndeki Posta akışı panosunda Otomatik iletilen iletiler raporu hakkında bilgi edinebilir.
ms.technology: mdo
ms.prod: m365-security
ms.collection: M365-security-compliance
ms.openlocfilehash: 2f102f4fbea558f0972fbd4f3e8f4a4bea257bf4
ms.sourcegitcommit: fdd0294e6cda916392ee66f5a1d2a235fb7272f8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/29/2022
ms.locfileid: "65131052"
---
# <a name="auto-forwarded-messages-insight-in-the-security--compliance-center"></a>Güvenlik & Uyumluluk Merkezi'nde otomatik iletilen iletiler içgörüleri

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Uygulandığı öğe**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Office 365 için Microsoft Defender plan 1 ve plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

[Güvenlik & Uyumluluk Merkezi'ndeki](https://protection.office.com) [Posta akışı panosundaki](mail-flow-insights-v2.md) **Otomatik iletilen iletiler** içgörüleri, kuruluşunuzdan dış etki alanlarındaki alıcılara otomatik olarak iletilen iletiler hakkındaki bilgileri görüntüler.

:::image type="content" source="../../media/mfi-auto-forwarded-messages.png" alt-text="Güvenlik & Uyumluluk Merkezi'nde otomatik iletilen iletiler olarak adlandırılan pencere öğesi" lightbox="../../media/mfi-auto-forwarded-messages.png":::

## <a name="auto-forwarded-messages-details"></a>Otomatik iletilen ileti ayrıntıları

Pencere öğesindeki ileti sayısına tıkladığınızda, otomatik iletilen iletiler hakkında daha fazla bilgi gösteren bir açılır pencere bölmesi görüntülenir:

- yöntemleri **ileterek otomatik iletilen iletiler**:

  - **Posta akışı kurallarına göre**
  - **Gelen Kutusu kurallarına göre**
  - **SMTP iletme ile**: Bu yöntem, yöneticilerin posta kutusu için [e-posta iletmeyi](/Exchange/recipients-in-exchange-online/manage-user-mailboxes/configure-email-forwarding) yapılandırma başlığı altında açıklandığı gibi posta kutusunda yapılandırabilecekleri otomatik iletmeyi gösterir.
  - Daha fazla ayrıntı için [İletme raporunun](view-mail-flow-reports.md#forwarding-report) bağlantısı.

- **Etki alanları ve kullanıcılara göre otomatik iletilen iletiler**:

  - **İletilen ilk 5 etki alanı**
  - **Yeni etki alanları (geçen hafta)**
  - **İlk 5 iletme kullanıcısı**
  - **Yeni kullanıcılar (geçen hafta)**
  - Daha fazla ayrıntı için [İletme değişiklikleri raporunun](mfi-new-users-forwarding-email.md#forwarding-modifications-report) bağlantısı.

:::image type="content" source="../../media/mfi-auto-forwarded-messages-details.png" alt-text="Güvenlik & Uyumluluk Merkezi'ndeki Otomatik iletilen iletiler pencere öğesi" lightbox="../../media/mfi-auto-forwarded-messages-details.png":::

## <a name="insights"></a>Analizler

Rapor verilerine göre iki içgörü oluşturulur:

- [E-postayı ileten yeni kullanıcılar](mfi-new-users-forwarding-email.md)
- [E-postayla iletilen yeni etki alanları](mfi-new-domains-being-forwarded-email.md)

## <a name="see-also"></a>Ayrıca bkz.

Posta akışı panosundaki diğer içgörüler hakkında bilgi için [Bkz. Güvenlik & Uyumluluk Merkezi'ndeki Posta akışı içgörüleri](mail-flow-insights-v2.md).
