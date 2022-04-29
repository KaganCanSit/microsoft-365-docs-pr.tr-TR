---
title: Yavaş posta akışı kuralları içgörüsünü düzeltme
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.localizationpriority: medium
ms.assetid: 37125cdb-715d-42d0-b669-1a8efa140813
ms.custom:
- seo-marvel-apr2020
description: Yöneticiler, kuruluşlarındaki verimli olmayan veya bozuk posta akışı kurallarını (taşıma kuralları olarak da bilinir) tanımlamak ve düzeltmek için Güvenlik & Uyumluluk Merkezi'ndeki Yavaş posta akışı kurallarını düzeltme içgörülerini kullanmayı öğrenebilir.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 650389529f2a5d811f71b7c3f755d93e7e734d81
ms.sourcegitcommit: fdd0294e6cda916392ee66f5a1d2a235fb7272f8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/29/2022
ms.locfileid: "65128750"
---
# <a name="fix-slow-mail-flow-rules-insight-in-the-security--compliance-center"></a>Güvenlik & Uyumluluk Merkezi'nde yavaş posta akışı kuralları içgörülerini düzeltme

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Uygulandığı öğe**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Office 365 için Microsoft Defender plan 1 ve plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Verimli olmayan posta akışı kuralları (taşıma kuralları olarak da bilinir) kuruluşunuzda posta akışı gecikmelerine yol açabilir. Bu içgörü, kuruluşunuzun posta akışını etkileyen posta akışı kurallarını raporlar. Bu tür kurallara örnek olarak şunlar verilebilir:

- Büyük gruplar için **Is öğesini** kullanan koşullar.
- Karmaşık normal ifade (regex) desen eşleştirmesi kullanan koşullar.
- Eklerde içerik denetimini kullanan koşullar.

[Güvenlik & Uyumluluk Merkezi'ndeki](https://protection.office.com) [Posta akışı panosunun](mail-flow-insights-v2.md) **Sizin için önerilir** alanındaki **Yavaş posta akışı kurallarını düzeltme** içgörüleri, posta akışı kuralının tamamlanmasının çok uzun sürmesi halinde size bildirir.

Bu içgörü yalnızca koşul algılandıktan sonra görünür (posta döngüleriniz yoksa içgörüleri görmezsiniz).

Bu bildirimi, posta akışı gecikmelerini azaltmaya yardımcı olmak üzere posta akışı kurallarını belirlemenize ve bunlara ince ayar yapmaya yardımcı olması için kullanabilirsiniz.

:::image type="content" source="../../media/mfi-fix-slow-mail-flow-rules.png" alt-text="Posta akışı panosunun Sizin için önerilen alanındaki Yavaş posta akışı kurallarını düzeltme içgörüleri" lightbox="../../media/mfi-fix-slow-mail-flow-rules.png":::

Pencere öğesinde **Ayrıntıları görüntüle'ye** tıkladığınızda, daha fazla bilgi içeren bir açılır pencere görüntülenir:

- **Kural**: Kuralın tüm koşullarını, özel durumlarını ve eylemlerini görmek için özetin üzerine gelebilirsiniz. Özete tıklayarak Exchange yönetim merkezinde (EAC) <https://admin.exchange.microsoft.com/#/transportrules>kuralı düzenleyebilirsiniz.
- **Değerlendirilen ileti sayısı**: Kuraldan etkilenen **iletilerin bir** örneğinin [ileti izleme](message-trace-scc.md) sonuçlarını görmek için Örnek iletileri görüntüle'ye tıklayabilirsiniz.
- **Her ileti için harcanan ortalama süre**
- **İletide harcanan ortanca süre**: Üst yarısını alt yarıdaki verilerden ayıran orta değerdir.

:::image type="content" source="../../media/mfi-fix-slow-mail-flow-rules-details.png" alt-text="Yavaş posta akışı kurallarını düzeltme içgörüsüsünde Ayrıntıları görüntüle'ye tıkladıktan sonra görüntülenen Ayrıntılar açılır öğesi" lightbox="../../media/mfi-fix-slow-mail-flow-rules-details.png":::

Posta akışı kurallarındaki koşullar ve özel durumlar hakkında daha fazla bilgi için bkz. [Exchange Online'da Posta akışı kuralı koşulları ve özel durumlar (koşullar).](/Exchange/security-and-compliance/mail-flow-rules/conditions-and-exceptions)

## <a name="see-also"></a>Ayrıca bkz.

Posta akışı panosundaki diğer içgörüler hakkında bilgi için [Bkz. Güvenlik & Uyumluluk Merkezi'ndeki Posta akışı içgörüleri](mail-flow-insights-v2.md).
