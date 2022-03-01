---
title: Posta akışı raporlarını Raporlar panosunda görüntüleme
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: how-to
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.assetid: ''
ms.collection:
- M365-security-compliance
description: Yöneticiler, Güvenlik ve Uyumluluk Merkezi'nin Raporlar panosunda yer alan posta akışı & bilgi edinebilirsiniz.
ms.custom: ''
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: c72e1b82a7e6336510c3b997d077c544f4169aea
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2022
ms.locfileid: "63034265"
---
# <a name="view-mail-flow-reports-in-the-reports-dashboard-in-security--compliance-center"></a>Güvenlik ve Uyumluluk Merkezi'nde Raporlar panosunda posta & görüntüleme

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Geçerli olduğu yer:**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [1. plan Office 365 plan 2 için Microsoft Defender](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

> [!NOTE]
>
> Bu makaledeki raporların büyük bölümü Microsoft 365 Defender portalında veya Exchange yönetim merkezinde (EAC) yer almaktadır. Daha fazla bilgi için, aşağıdaki konulara bakın:
>
> - [Yeni Yönetim Merkezi'nde posta Exchange raporları](/exchange/monitoring/mail-flow-reports/mail-flow-reports)
> - [Portalda e-posta Microsoft 365 Defender görüntüleme](view-email-security-reports.md)

Güvenlik & ve Uyumluluk Merkezi'nin Posta akışı panosunda yer [](mail-flow-insights-v2.md) alan posta akışı raporlarına ek olarak, raporlarınızı ve kuruluşlarınızı izlemenizi sağlamak için Raporlar panosunda çeşitli ek posta Microsoft 365 vardır.

Gerekli izinlere [sahipsiniz,](#what-permissions-are-needed-to-view-these-reports) Bu raporları, Raporlar Panosu'& Güvenlik ve Uyumluluk Merkezi'nde <https://protection.office.com> **görüntüleyebilirsiniz**\>. Doğrudan Raporlar panosuna gitmek için, 'i açın <https://protection.office.com/insightdashboard>.

![Güvenlik ve Uyumluluk Merkezi'& Raporlar panosu.](../../media/6b213d34-adbb-44af-8549-be9a7e2db087.png)

## <a name="connector-report"></a>Bağlayıcı raporu

> [!NOTE]
> Bu raporun yerini, **EAC'de Gelen** iletiler raporu **ve Giden iletiler** raporu aldı. Daha fazla bilgi için bkz [. Yeni EAC'de Gelen iletiler ve Giden iletiler raporları](/exchange/monitoring/mail-flow-reports/mfr-inbound-messages-and-outbound-messages-reports).

## <a name="exchange-transport-rule-report"></a>Exchange Aktarım Kuralı raporu

> [!NOTE]
> Yeni **Exchange Aktarım Kuralı raporu**, artık EAC'de kullanılabilir. Daha fazla bilgi için bkz[. Exchange EAC'de aktarım kuralı raporunu düzenleme](/exchange/monitoring/mail-flow-reports/mfr-exchange-transport-rule-report).

## <a name="forwarding-report"></a>Rapor iletme

> [!NOTE]
> Yönlendirme **raporu artık** EAC'de kullanılabilir. Daha fazla bilgi için bkz [. Yeni EAC'de otomatik iletili iletiler raporu](/exchange/monitoring/mail-flow-reports/mfr-auto-forwarded-messages-report).

## <a name="mailflow-status-report"></a>Posta akışı durum raporu

Posta **Akışı durum raporu,** kenarda izin verilen veya engellenen [e-posta](#sent-and-received-email-report) hakkında ek bilgiler içeren Gönderilmiş ve alınan e-posta raporuna benzer. Bu, kenar koruma bilgileri içeren tek rapor olup, hizmete Exchange Online Protection (EOP) tarafından değerlendirme için izin verilmeden önce ne kadar e-postanın engellenmiş olduğunu gösterir. Bir ileti beş alıcıya gönderilirse, bunun tek bir ileti değil beş farklı ileti olarak sayılacağınızı anlamanız önemlidir.

Raporu görüntülemek için Güvenlik ve Uyumluluk [Merkezi'& açın](https://protection.office.com), Raporlar Panosu'ne **gidin** \> ve **Posta Akışı durum raporu'seçin**. Doğrudan Posta akışı durum **raporuna gitmek için**, 'i açın <https://security.microsoft.com/reports/mailflowStatusReport>.

![Raporlar panosunda Posta Akışı durumu raporu widget'ı.](../../media/scc-mail-flow-status-report-widget.png)

> [!NOTE]
> Güvenlik Ve Uyumluluk Merkezi'nde (& protection.office.com) bu raporun widget'ını tıklatmak sizi portalda (Microsoft 365 Defender) raporun tamam security.microsoft.com. Rapor hakkında ayrıntılı bilgi için bkz. [Posta Akışı durum raporu](view-email-security-reports.md#mailflow-status-report).

## <a name="sent-and-received-email-report"></a>Gönderilmiş ve alınan e-posta raporu

> [!NOTE]
> Bu raporun yerini Posta Akışı [durum raporu aldı](#mailflow-status-report).

## <a name="top-senders-and-recipients-report"></a>En çok gönderenler ve alıcılar raporu

En **Çok gönderenler** ve alıcılar, eOP tarafından algılanan iletiler için en yüksek alıcıların yanı sıra en çok gelen iletilerin yanı sıra koruma özellikleri için de EOP ve Defender Office 365 gösterir.

Raporu görüntülemek için Güvenlik ve Uyumluluk & '<https://protection.office.com> \> ı açın, Raporlar Panosu'ne gidin ve En çok **gönderenler ve alıcılar'ı seçin**. Doğrudan rapora gitmek için aşağıdaki URL'lerden birini açın:

- Office 365 için Defender:<https://protection.office.com/TopSenderRecipientsATP>
- EOP: <https://protection.office.com/TopSenderRecipients>

![Raporlar panosunda en çok gönderenler ve alıcılar widget'ı.](../../media/scc-top-senders-and-recipients-widget.png)

> [!NOTE]
> Güvenlik ve Uyumluluk Merkezi'nde bu raporun widget'ine & sizi bir Web Sitesi protection.office.com, sayfa içeriği Microsoft 365 Defender alır. Rapor hakkında ayrıntılı bilgi için bkz [. En çok gönderenler ve alıcılar raporu](view-email-security-reports.md#top-senders-and-recipients-report).

## <a name="what-permissions-are-needed-to-view-these-reports"></a>Bu raporları görüntülemek için hangi izinler gereklidir?

Bu makalede açıklanan raporları görüntülemek ve kullanmak için Güvenlik ve Uyumluluk Merkezi'nde aşağıdaki rol gruplarından birinin üyesi & gerekir:

- **Kuruluş Yönetimi**
- **Güvenlik Yöneticisi**
- **Güvenlik Okuyucu**
- **Genel Okuyucu**

Daha fazla bilgi için Güvenlik [ve Uyumluluk Merkezi'& bakın](permissions-in-the-security-and-compliance-center.md).

> [!NOTE]
> Kullanıcılar Uyumluluk Merkezi'Azure Active Directory ilgili uyumluluk rolüne Microsoft 365 yönetim merkezi, kullanıcılara Güvenlik & Uyumluluk Merkezi'nde gerekli izinleri ve Microsoft 365. Daha fazla bilgi için bkz. [Yönetici rolleri hakkında](../../admin/add-users/about-admin-roles.md).

## <a name="related-topics"></a>İlgili konular

[Güvenlik ve Uyumluluk Merkezi'nde akıllı & öngörüler](reports-and-insights-in-security-and-compliance.md)

[Güvenlik ve Uyumluluk Merkezi'nde & öngörüleri](mail-flow-insights-v2.md)

[Güvenlik ve Uyumluluk Merkezi'nde e-& raporları görüntüleme](view-email-security-reports.md)

[Microsoft Defender for Office 365](view-reports-for-mdo.md)
