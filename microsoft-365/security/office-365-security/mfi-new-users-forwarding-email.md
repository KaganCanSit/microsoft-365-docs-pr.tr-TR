---
title: E-posta içgörülerini iletir yeni kullanıcılar
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
audience: ITPro
ms.topic: conceptual
ms.localizationpriority: medium
ms.assetid: ''
description: Yöneticiler, kuruluşlarına gelen kullanıcıların iletileri yeni etki alanlarına ne zaman ileteceklerini araştırmak için Güvenlik & Uyumluluk Merkezi'nde E-posta iletme yeni kullanıcılar içgörülerini nasıl kullanabileceğini öğrenebilir.
ms.technology: mdo
ms.prod: m365-security
ms.collection: M365-security-compliance
ms.openlocfilehash: 7e7f97f2f246be609db813f1d42ef6aed6a152a9
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64470273"
---
# <a name="new-users-forwarding-email-insight-in-the-security--compliance-center"></a>Güvenlik ve Uyumluluk Merkezi'nde e-posta içgörülerini & kullanıcılar

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Geçerli olduğu yer:**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Office 365 için Microsoft Defender plan 1 ve plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Kuruluşta yeni kullanıcı hesapları aniden e-posta iletilerini dış etki alanlarına iletmeye başlaması şüphelidir.

Güvenlik **ve Uyumluluk Merkezi'nde** yeni oluşturulan e-posta & içgörü, kurum içinde yeni oluşturulan kullanıcıların iletileri dış etki alanlarına iletecekleri konusunda size bilgi verir.[](https://protection.office.com) Bu koşul, güvenliği tehlikeye atılmış yönetici hesaplarının yeni kullanıcıları oluşturmak için kullanılmış olduğunu gösteriyor olabilir. Hesapların ele geçirildiklerine şüpheleniyorsanız bkz. Güvenliği tehlikeye [atılmış bir e-posta hesabını yanıtla.](responding-to-a-compromised-email-account.md)

Bu içgörü ancak sorun algılandığında ve Rapor [iletildi sayfasında görüntülenir](view-mail-flow-reports.md#forwarding-report) .

:::image type="content" source="../../media/mfi-new-users-forwarding-email.png" alt-text="E-postayı iletirken Yeni kullanıcılar içgörü" lightbox="../../media/mfi-new-users-forwarding-email.png":::

Widget'a tıklarsanız, bu makalenin devamlarında açıklandığı gibi Değişiklikleri iletme raporunun bağlantısı da içinde olmak üzere, iletili iletiler hakkında [](#forwarding-modifications-report) daha fazla ayrıntıyı bulmanız için bir açılır pencere öğesi görüntülenir.

:::image type="content" source="../../media/mfi-new-users-forwarding-email-details.png" alt-text="E-postayı ileten Yeni kullanıcılar içgörüne tık olduktan sonra görüntülenen Ayrıntılar açılır" lightbox="../../media/mfi-new-users-forwarding-email-details.png":::

Ayrıca, En iyi öngörüler ve öneriler **alanında (** \> Raporlar Panosu veya ) Hepsini görüntüle'ye **tıklarken** & bu ayrıntılar sayfasına **da bakabilirsiniz**<https://protection.office.com/insightdashboard>.

Sonraki bölümde açıklandığı **gibi Değişiklikleri iletme raporuna** gitmek için, Öngörüyle ilişkilendirilmiş raporu gör bağlantısına tıkabilirsiniz.

## <a name="forwarding-modifications-report"></a>Değişiklikleri iletme raporu

Değişiklikleri **iletme raporu, kurumda** otomatik olarak iletilen iletiler hakkında ayrıntıları gösterir:

- İletileri dış etki alanlarına iletirken yeni oluşturulan hesaplar.
- İletileri, kuruluşta yer alan diğer gönderenler tarafından hiç ilet iletilerin ilet iş aynı zaman ilet iş aynı anda ilet iş aynı anda veya dışında bir etki alanına iletilen hesaplardadır.

Bu tür iletiler bir güvenlik veya uyumluluk riski oluştursa da ele geçirildiklerine işaret ediyor olabilir.

Rapor 90 gün içinde geçerli olan verileri içerir. Varsayılan olarak, rapor son 7 gün verilerini gösterir.

Bu rapor, Posta akışı [panosunda veya Raporlar panosunda](mail-flow-insights-v2.md) doğrudan [kullanılamaz](view-mail-flow-reports.md). E-posta **içgörülerini ileten** Yeni kullanıcılar'daki  Bilgiyle ilişkili raporu gör bağlantısına tıklamaya ek olarak, şu bilgileri kullanarak rapora ulaşabilirsiniz:

- Yeni etki **alanları iletir ve e-posta** ile ilgili içgörü ile [ilgili ayrıntılarda Forwarding notifications report bağlantısına tıklayın](mfi-new-domains-being-forwarded-email.md).
- Açma <https://protection.office.com/reportv2?id=MailFlowNewForwarding>.

### <a name="report-view-for-the-forwarding-modifications-report"></a>Değişiklikleri iletme raporu için rapor görünümü

Aşağıdaki grafikler rapor görünümünde kullanılabilir:

- **Şu kullanıcılar için verileri göster: Yeni iletme kullanıcıları**:

    :::image type="content" source="../../media/forwarding-modifications-report-new-forwarding-users.png" alt-text="Değişiklikleri iletme raporunda Yeni iletme kullanıcıları görünümü" lightbox="../../media/forwarding-modifications-report-new-forwarding-users.png":::

- **Şu için verileri göster: Yeni iletme etki alanları**:

    :::image type="content" source="../../media/forwarding-modifications-report-new-forwarded-domains.png" alt-text="Değişiklikleri iletme raporu'daki Yeni iletili etki alanları görünümü" lightbox="../../media/forwarding-modifications-report-new-forwarded-domains.png":::

Rapor görünümünde **Filtreler'e** tıklarsanız, Başlangıç tarihi ve Bitiş tarihi **ile bir tarih** aralığı **belirtebilirsiniz**.

### <a name="details-table-view-for-the-forwarding-modifications-report"></a>Değişiklikleri iletme raporu için Ayrıntılar tablosu görünümü

Ayrıntıları görüntüle **tablosu'nun üzerine** tıklarsanız, gösterilen bilgiler üzerinde şu bilgilere bakabilirsiniz:

- **Şu kullanıcılar için verileri göster: Yeni iletme kullanıcıları**:

  - **Ad**: Gönderenin e-posta adresi.
  - **Yönlendirme türü**
  - **Alıcı adresi**
  - **Ayrıntılar**
  - **Sayı**
  - **İlk iletme tarihi**

- **Şu için verileri göster: Yeni iletme etki alanları**:

  - **Ad**: Gönderenin e-posta etki alanı.
  - **Yönlendirme türü**
  - **Alıcı adresi**
  - **Ayrıntılar**
  - **Sayı**
  - **İlk iletme tarihi**

Ayrıntılar tablosu **görünümünde Filtreler'e** tıklarsanız, Başlangıç tarihi ve Bitiş tarihi ile bir **tarih** aralığı **belirtebilirsiniz**.

Tablodan bir satır seçersiniz, aşağıdaki **bilgilerle** birlikte Ayrıntılar açılır öğesini görünür:

- **Ad**: Bu, gönderenin e-posta adresidir (Verileri göster **:** Yeni iletme kullanıcıları görünümü) veya gönderenin e-posta etki alanı (Verileri göster **:** Yeni iletme etki alanları görünümü).
- **Yönlendirme türü**
- **Alıcı**
- **Ayrıntılar**
- **Sayı**
- **Başlangıç tarihi**
- **Öneri**: Buradan, bağlantıyı tıklayarak kullanıcının yönetim Microsoft 365 yönetim merkezi.

  :::image type="content" source="../../media/mfi-forwarding-modifications-report-new-forwarding-users-view-details-table-details.png" alt-text="Yeni iletme kullanıcıları görünümünün Ayrıntılar tablosundan Değişiklikleri iletme raporu" lightbox="../../media/mfi-forwarding-modifications-report-new-forwarding-users-view-details-table-details.png":::

Raporlar görünümüne geri dönmek için Raporu **görüntüle'yi tıklatın**.

## <a name="related-topics"></a>İlgili konular

Posta akışı panosunda yer alan diğer içgörüler hakkında bilgi için, Güvenlik ve Uyumluluk Merkezi'nde [Posta & bakın](mail-flow-insights-v2.md).
