---
title: Posta akışı panosunda teslim olmayan rapor
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
description: Yöneticiler, teslim edilemedi raporlarında (NDR'ler veya geri dönen iletiler olarak da bilinir) en sık karşılaşılan hata kodlarını izlemek için Güvenlik & Uyumluluk Merkezi'nde Posta akışı panosunda Teslim edilemedi ayrıntıları raporunu kullanmayı öğrenebilir.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: bc408f6bb28b11e77c49755b888c44e0ea4d9f57
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64473749"
---
# <a name="non-delivery-report-in-the-security--compliance-center"></a>Güvenlik ve Uyumluluk Merkezi'nde teslim & değil

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Geçerli olduğu yer:**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Office 365 için Microsoft Defender plan 1 ve plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

**Güvenlik** [&](https://protection.office.com) Uyumluluk Merkezi'nin Posta [](mail-flow-insights-v2.md) akışı panosunda, teslim edilemedi raporlarında (NDR'ler veya geri dönen iletiler olarak da bilinir) en çok karşılaşılan hata kodları yer alır. Bu rapor NDR'lerin ayrıntılarını gösterir; böylelikle e-posta teslim sorunlarını giderebilirsiniz.

:::image type="content" source="../../media/mfi-non-delivery-report-widget.png" alt-text="Güvenlik ve Uyumluluk Merkezi'nin Posta akışı panosunda Teslim & widget'ı" lightbox="../../media/mfi-non-delivery-report-widget.png":::

## <a name="report-view-for-the-non-delivery-report"></a>Teslim olmayan rapor için rapor görünümü

Teslim değil **raporu widget'ine tıklamak** sizi Teslim **değil raporuna götürmenizi sağlar**.

Varsayılan olarak, tüm hata kodları etkinliği gösterilir. Aşağıdaki için **verileri göster'e** tıklarsanız, açılan listeden belirli bir hata kodu seçin.

Grafikte belirli bir günün belirli bir rengin (hata kodu) üzerine gelindiğinde hatanın toplam ileti sayısını alırsınız.

:::image type="content" source="../../media/mfi-non-delivery-report-overview-view.png" alt-text="Kabul edilmeyen etki alanı raporu rapora göre Rapor görünümü" lightbox="../../media/mfi-non-delivery-report-overview-view.png":::

## <a name="details-table-view-for-the-non-delivery-report"></a>Teslim değil raporu için Ayrıntılar tablosu görünümü

Rapor görünümünde **Ayrıntıları görüntüle tablosu'ne** tıklarsanız, aşağıdaki bilgiler gösterilir:

- **Tarih**
- **Teslim olmayan rapor kodu**
- **Sayı**
- **Örnek iletiler**: Etkilenen iletilerden bir örneğin ileti kimlikleri.

Ayrıntılar tablosu **görünümünde Filtreler'e** tıklarsanız, Başlangıç tarihi ve Bitiş tarihi ile bir **tarih** aralığı **belirtebilirsiniz**.

Belirli bir tarih aralığına yönelik raporu bir veya birden çok alıcıya e-postayla göndermek için İndirme **isteği'ne tıklayın**.

Tabloda bir satır seçin; aşağıdaki bilgilerle birlikte bir açılır sayfa görüntülenir:

- **Tarih**
- **Teslim olmayan rapor kodu**: Belirli hata kodunun nedenleri ve çözümleri hakkında daha fazla bilgi almak için bağlantıya tık kullanabilirsiniz.
- **Sayı**
- **Örnek iletiler**: Etkilenen **iletilerden bir örneğine** dair [ileti izleme sonuçlarını görmek](message-trace-scc.md) için Örnek iletileri görüntüle'ye tıkabilirsiniz.


:::image type="content" source="../../media/mfi-non-delivery-report-details-flyout.png" alt-text="Teslim değil raporunda Ayrıntılar tablosu görünümünde bir satır seçdikten sonra Ayrıntılar uçarak çıkış" lightbox="../../media/mfi-non-delivery-report-details-flyout.png":::

## <a name="related-topics"></a>İlgili konular

Posta akışı panosunda yer alan diğer içgörüler hakkında bilgi için, Güvenlik ve Uyumluluk Merkezi'nde [Posta & bakın](mail-flow-insights-v2.md).
