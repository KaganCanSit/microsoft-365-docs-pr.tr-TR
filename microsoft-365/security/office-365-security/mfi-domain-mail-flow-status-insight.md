---
title: Posta akışı panosunda en üst etki alanı posta akışı durumu içgörü
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
audience: ITPro
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.localizationpriority: medium
ms.assetid: ''
ms.custom:
- seo-marvel-apr2020
description: Yöneticiler, MX kayıtlarıyla ilgili posta akışı sorunlarını gidermek için Güvenlik & ve Uyumluluk Merkezi'nde Posta akışı panosunda En üst etki alanı posta akışı durumu içgörüsini kullanmayı öğrenebilirler.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 1a22589ece98e497c55d61d29256b2480a2f55d3
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2022
ms.locfileid: "63679730"
---
# <a name="top-domain-mail-flow-status-insight-in-the-security--compliance-center"></a>Güvenlik ve Uyumluluk Merkezi'nde en üstteki etki & durumu içgörü

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Geçerli olduğu yer:**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [1. plan Office 365 plan 2 için Microsoft Defender](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Güvenlik **ve Uyumluluk Merkezi'nin** Posta akışı panosundaki En üst etki [alanı posta akışı](https://protection.office.com) durumu &, size kuruluşun geçerli posta akışı durumunu verir.[](mail-flow-insights-v2.md)

Bu içgörü, posta akışı sorunları yaşayan etki alanlarını tanımlamanıza ve ***gidermenize yardımcı*** olur. Örneğin, etki alanının süresi sona erdiğinde veya etki alanında yanlış bir MX kaydı olduğundan etki alanı dış e-posta alınamıyor.

![Güvenlik ve Uyumluluk Merkezi'nde Posta akışı panosunda en üst & durumu widget'ı.](../../media/mfi-top-domain-mail-flow-status-widget.png)

Widget'ta **Ayrıntıları görüntüle'ye** tıklarken, her bir etki alanının durumuyla ilgili daha fazla ayrıntı gösteren bir Etki Alanı durumu açılır öğesi görüntülenir:

- **Etki alanı**
- **Önceki MX kaydı**
- **Geçerli MX kaydı**
- **E-posta alma durumu**
- **Etki** alanı durumu: Yeşil onay işareti, geçerli MX kaydının (widget'a tıklarken) kayıtta yer alan değerle eş olduğunu ve etki alanının son iki saat içinde e-posta aldığına işaret ediyor.

  Kırmızı X, MX kaydının değiştirdiğini ve etki alanının son 6 saat içinde hiç e-posta ala olmadığını gösterir. Bu, büyük olasılıkla etki alan adınızın süresinin dolmuş olduğunu veya MX kaydının yanlış güncelleştirilmiş olduğunu gösterir. Etki alanının süresinin dolmuş olup olduğunu veya etki alanının MX kaydının yanlış olduğunu görmek için etki alanı kayıt şirketinizi veya DNS barındırma hizmetinizi kontrol edin.

Daha fazla etki **alanıyla ilgili aynı** bilgileri görmek için Daha fazla görüntüle'ye tıkabilirsiniz.

![En üst etki alanı posta akışı durumu içgörüsinde Ayrıntılar uçarak çıkış.](../../media/mfi-top-domain-mail-flow-status-view-details.png)

## <a name="see-also"></a>Ayrıca bkz.

Posta akışı panosunda yer alan diğer içgörüler hakkında bilgi için, Güvenlik ve Uyumluluk Merkezi'nde [Posta & bakın](mail-flow-insights-v2.md).
