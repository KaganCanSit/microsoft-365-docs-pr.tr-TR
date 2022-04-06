---
title: Posta akış haritası
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
description: Yöneticiler, posta akışlarını bağlayıcılar üzerinden ve bağlayıcılar olmadan görselleştirmek ve izlemek için Güvenlik & Uyumluluk Merkezi'nin Posta akış panosunda Posta akış haritasını kullanmayı öğrenebilirler.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: bd8df34c9484b7a2b8aa2bdd57d160e22f71d247
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64473815"
---
# <a name="mail-flow-map-in-the-security--compliance-center"></a>Güvenlik ve Uyumluluk Merkezi'nde posta & haritası

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Geçerli olduğu yer:**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Office 365 için Microsoft Defender plan 1 ve plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Güvenlik **ve Uyumluluk Merkezi'nin** [Posta akış panosunda](mail-flow-insights-v2.md) yer alan Posta [akış &](https://protection.office.com) , postanın organizasyonunız aracılığıyla nasıl akmaya neden olduğuyla ilgili bilgi verir. Bu bilgileri kullanarak desenleri öğrenebilir, her şeyi tanımlayabilir ve oluşan sorunları düzeltebilirsiniz.

:::image type="content" source="../../media/mfi-mail-flow-map-widget.png" alt-text="Güvenlik ve Uyumluluk Merkezi'nin Posta akış panosunda Posta akış & widget'ı" lightbox="../../media/mfi-mail-flow-map-widget.png":::

Varsayılan olarak, widget Sankey diyagramı olarak bilinen bir grafikte önceki günün posta akışı *desenini* gösterir. Sol oku kullanabilirsiniz ![.](../../media/scc-left-arrow.png) ve sağ oka ![sağ ok](../../media/scc-right-arrow.png) tuşlarına basın. Her farklı renk, posta akışını farklı bir gelen veya giden bağlayıcı (veya bağlayıcılar olmadan) üzerinden gösterir. Belirli bir rengin üzerine gelindiğinde, bu tür bir bağlayıcı için ileti sayısı görüntülenir.

## <a name="report-view-for-the-mail-flow-map"></a>Posta akış haritası için rapor görünümü

Posta akış haritası **widget'ine** tıklamak sizi **Posta akış haritası raporuna** götürmenizi sağlar.

Aşağıdaki grafikler rapor görünümünde kullanılabilir:

- **Aşağıdakiler için verileri göster:** Genel bakış: Bu temel olarak widget'ın daha büyük bir görünümüdir. Belirli bir rengin üzerine gelindiğinde, bu tür bir bağlayıcı için ileti sayısı görüntülenir.

    :::image type="content" source="../../media/mfi-mail-flow-map-report-overview.png" alt-text="Posta akış haritası raporunda Genel Bakış görünümü" lightbox="../../media/mfi-mail-flow-map-report-overview.png":::

- **Aşağıdakiler için verileri göster: Ayrıntı**: Bu görünümde bağlayıcılar ve hedef etki alanlarıyla ilgili ayrıntılar gösterir. En üst düzey gönderen ve alıcı etki alanları listelenir ve geri kalanı Diğer'e **konr.** Belirli bir renk ve bölümün üzerine gelindiğinde ileti sayısı görüntülenir.

    :::image type="content" source="../../media/mfi-mail-flow-map-report-detail.png" alt-text="Posta akış haritası raporunda Ayrıntı görünümü" lightbox="../../media/mfi-mail-flow-map-report-detail.png":::

Rapor görünümünde **Filtreler'e** tıklarsanız, Başlangıç tarihi ve Bitiş tarihi **ile bir tarih** aralığı **belirtebilirsiniz**.

Belirli bir tarih aralığına yönelik raporu bir veya birden çok alıcıya e-postayla göndermek için İndirme **isteği'ne tıklayın**.

Uygunsa, Posta akış haritasının altında ilgili içgörüler gösterilir (örneğin, Olası posta [döngüsü içgörülerini düzelt).](mfi-mail-loop-insight.md)

## <a name="details-table-view-for-the-mail-flow-map"></a>Posta akış haritası için Ayrıntılar tablosu görünümü

Rapor görünümünde **Ayrıntıları görüntüle tablosu'ne** tıklarsanız, aşağıdaki bilgiler gösterilir:

- **Tarih**
- **Kategori**
- **Bağlayıcı / Üçüncü taraf hizmet sağlayıcısı**
- **Gönderen/Alıcı etki alanı**
- **İleti sayısı**

Ayrıntılar tablosu **görünümünde Filtreler'e** tıklarsanız, Başlangıç tarihi ve Bitiş tarihi ile bir **tarih** aralığı **belirtebilirsiniz**.

Bir satır seçersiniz, uçarak çıkışta benzer ayrıntılar gösterilir:

:::image type="content" source="../../media/mfi-mail-flow-map-view-details-table-details.png" alt-text="Posta akış haritasında ayrıntılar tablosundan Ayrıntılar çıktısı" lightbox="../../media/mfi-mail-flow-map-view-details-table-details.png":::

Belirli bir tarih aralığına yönelik raporu bir veya birden çok alıcıya e-postayla göndermek için İndirme **isteği'ne tıklayın**.

Raporlar görünümüne geri dönmek için Raporu **görüntüle'yi tıklatın**.

## <a name="see-also"></a>Ayrıca bkz.

Posta akışı panosunda yer alan diğer içgörüler hakkında bilgi için, Güvenlik ve Uyumluluk Merkezi'nde [Posta & bakın](mail-flow-insights-v2.md).
