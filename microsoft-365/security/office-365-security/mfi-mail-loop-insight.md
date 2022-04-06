---
title: Olası posta döngüsü içgörülerini düzeltme
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
audience: ITPro
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.localizationpriority: medium
ms.assetid: cb801985-3c89-4979-9c18-17829a4cb563
ms.custom:
- seo-marvel-apr2020
description: Yöneticiler, kuruluşlarına posta döngülerini tanımlamak ve düzeltmek için Güvenlik & ve Uyumluluk Merkezi'nde Posta akışı panosunda Olası posta döngüsü düzeltme içgörüsini kullanmayı öğrenebilirler.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 5a74e7cc623dffd6bae6451f7488d8f630b607b2
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64469151"
---
# <a name="fix-possible-mail-loop-insight-in-the-security--compliance-center"></a>Güvenlik ve Uyumluluk Merkezi'nde olası posta döngüsü & çözme

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Geçerli olduğu yer:**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Office 365 için Microsoft Defender plan 1 ve plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Posta döngüleri hatalıdır çünkü:

- Sistem kaynaklarını kullanırlar.
- Bunlar, kurumnizin posta toplu kotasını tüketir.
- Bunlar, özgün ileti gönderenlere karmaşık teslim edililmeyen raporlar (NDR'ler veya geri dönen iletiler olarak da bilinir) gönderir.

Güvenlik **ve** Uyumluluk Merkezi'nde Posta akışı panosunun Sizin için önerilenler alanında [](mail-flow-insights-v2.md) yer alan Olası posta döngüsü [](https://protection.office.com) düzeltme içgörüyü, kurumda bir posta döngüsü algılandığında size bu durumu haber &.

Bu içgörü ancak koşul algılandığında görüntülenir (posta döngüleri yoksa, içgörüyü görmezsiniz).

:::image type="content" source="../../media/mfi-fix-possible-mail-loop.png" alt-text="Posta akışı panosunun Sizin için önerilenler alanında Yer alan Yavaş posta akışı kurallarını düzelt içgörü" lightbox="../../media/mfi-fix-possible-mail-loop.png":::

Widget'ta **Ayrıntıları görüntüle'ye** tıklarken, daha fazla bilgiyle birlikte bir açılır pencere açılır:

- **Etki alanı**
- **İleti sayısı**: Döngüden etkilenen **ileti örneğine** [dair ileti](message-trace-scc.md) izleme sonuçlarını görmek için Örnek iletileri görüntüle'yi tıklatın.
- **Etki alanı** türü" Örneğin, Yetkili veya Yetkili Değil.
- **MX kaydı**: Etki alanının MX **kaydının** **ana** bilgisayarı (Posta sunucusu) ve Öncelik değerleri.
- **Loop ve** **Nasıl** düzeltebilirim: En yaygın posta döngüsü senaryolarını belirleyecek ve döngüyü düzeltmek için önerilen eylemleri sağlarız.

:::image type="content" source="../../media/mfi-fix-possible-mail-loop-details.png" alt-text="Olası posta döngüsü düzeltme içgörüseğinde Ayrıntıları görüntüle'ye tık olduktan sonra görüntülenen Ayrıntılar açılır görünümü" lightbox="../../media/mfi-fix-possible-mail-loop-details.png":::

## <a name="see-also"></a>Ayrıca bkz.

Posta akışı panosunda yer alan diğer içgörüler hakkında bilgi için, Güvenlik ve Uyumluluk Merkezi'nde [Posta & bakın](mail-flow-insights-v2.md).
