---
title: Posta akışı panosunda kabul edilmeyen etki alanı raporu
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
description: Yöneticiler, gönderenin etki alanının Microsoft 365'de yapılandırılmamış olduğu şirket içi kuruluştan gelen iletileri izlemek için Güvenlik & Uyumluluk Merkezi'nde Posta akışı panosunda Kabul edilmeyen etki alanı raporunu kullanmayı Microsoft 365.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 8f16dfbafa12080058cd1784120e4bc2157e0cff
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64470845"
---
# <a name="non-accepted-domain-report-in-the-security--compliance-center"></a>Güvenlik ve Uyumluluk Merkezi'nde kabul edilmeyen & raporu

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Geçerli olduğu yer:**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Office 365 için Microsoft Defender plan 1 ve plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Güvenlik [&](https://protection.office.com) Uyumluluk Merkezi'nin Posta akışı panosunda kabul edilmeyen etki alanı raporu, şirket içi **e-posta** kuruluştan gelen ve gönderenin etki alanının Microsoft 365 kuruluşu içinde kabul edilen bir etki alanı olarak yapılandırılmamış iletileri hakkında bilgi görüntüler.[](mail-flow-insights-v2.md)

Microsoft 365 kötü amaçlı iletilerin amacını kanıtlamak için verimiz varsa bu iletileri kısıtlayabiliriz. Bu nedenle, neler olduğunu anlamanız ve sorunu çözmenız önemlidir.

:::image type="content" source="../../media/mfi-non-accepted-domain-report-widget.png" alt-text="Güvenlik ve Uyumluluk Merkezi'nin Posta akışı panosunda kabul edilmeyen etki & widget'ı" lightbox="../../media/mfi-non-accepted-domain-report-widget.png":::

## <a name="report-view-for-the-non-accepted-domain-report"></a>Kabul edilmeyen etki alanı raporu için rapor görünümü

Kabul edilmeyen etki **alanı pencere öğesinde** grafiği tıklatmak sizi Kabul **edilmeyen etki alanı raporuna götürmenizi** sağlar.

Varsayılan olarak, etkilenen tüm bağlayıcıların etkinliği gösterilir. Aşağıdaki için verileri **göster'e** tıklarsanız, açılan listeden belirli bir bağlayıcıyı seçin.

Grafikte bir veri noktasının (gün) üzerine gelindiğinde bağlayıcının toplam ileti sayısını görmenizi sağlar.

:::image type="content" source="../../media/mfi-non-accepted-domain-report-overview-view.png" alt-text="Kabul edilmeyen etki alanı raporu rapora göre Rapor görünümü" lightbox="../../media/mfi-non-accepted-domain-report-overview-view.png":::

## <a name="details-table-view-for-the-non-accepted-domain-report"></a>Kabul edilmeyen etki alanı raporu için ayrıntılar tablosu görünümü

Rapor görünümünde **Ayrıntıları görüntüle tablosu'ne** tıklarsanız, aşağıdaki bilgiler gösterilir:

- **Tarih**
- **Gelen bağlayıcısı adı**
- **Gönderen etki alanı**
- **İleti sayısı**
- **Örnek iletiler**: Etkilenen iletilerden bir örneğin ileti kimlikleri.

Ayrıntılar tablosu **görünümünde Filtreler'e** tıklarsanız, Başlangıç tarihi ve Bitiş tarihi ile bir **tarih** aralığı **belirtebilirsiniz**.

Belirli bir tarih aralığına yönelik raporu bir veya birden çok alıcıya e-postayla göndermek için İndirme **isteği'ne tıklayın**.

Tabloda bir satır seçin; aşağıdaki bilgilerle birlikte bir açılır sayfa görüntülenir:

- **Tarih**
- **Gelen bağlayıcısı adı**
- **Gönderen etki alanı**
- **İleti sayısı**
- **Örnek iletiler**: Etkilenen **iletilerden bir örneğine** dair [ileti izleme sonuçlarını görmek](message-trace-scc.md) için Örnek iletileri görüntüle'ye tıkabilirsiniz.

:::image type="content" source="../../media/mfi-non-accepted-domain-report-details-flyout.png" alt-text="Kabul edilmeyen etki alanı raporunda Ayrıntılar tablosu görünümünde bir satır seçdikten sonra Ayrıntılar uçarak çıkış" lightbox="../../media/mfi-non-accepted-domain-report-details-flyout.png":::

Raporlar görünümüne geri dönmek için Raporu **görüntüle'yi tıklatın**.

## <a name="related-topics"></a>İlgili konular

Posta akışı panosunda yer alan diğer içgörüler hakkında bilgi için, Güvenlik ve Uyumluluk Merkezi'nde [Posta & bakın](mail-flow-insights-v2.md).
