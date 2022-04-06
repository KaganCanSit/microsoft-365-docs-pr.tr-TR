---
title: Posta akışı panosunda posta akışı içgörüleri
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
audience: ITPro
ms.topic: overview
ms.collection: M365-security-compliance
ms.localizationpriority: medium
ms.assetid: beb6acaa-6016-4d54-ba7e-3d6d035e2b46
description: Yöneticiler, Güvenlik ve Uyumluluk Merkezi'nin Posta akışı panosunda bulunan içgörüler ve & bilgi edinebilirsiniz.
ms.custom: seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: b5cc3eba5807838b0a797f606d8a6aa3c152f60c
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64476477"
---
# <a name="mail-flow-insights-in-the-security--compliance-center"></a>Güvenlik ve Uyumluluk Merkezi'nde & öngörüleri

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Geçerli olduğu yer:**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Office 365 için Microsoft Defender plan 1 ve plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Yöneticiler, eğilimleri, içgörüleri keşfetmek ve kuruluşların posta akışıyla ilgili sorunları düzeltmek için Güvenlik ve Uyumluluk Merkezi'nde Posta akışı panosu & kullanabilir.

:::image type="content" source="../../media/mail-flow-dashboard-v2.png" alt-text="Güvenlik ve Uyumluluk Merkezi'nde posta & panosu" lightbox="../../media/mail-flow-dashboard-v2.png":::

Kullanılabilir içgörüler:

- [Otomatik iletili iletiler içgörü](mfi-auto-forwarded-messages-report.md)

- [Olası posta döngüsü içgörülerini düzeltme1](mfi-mail-loop-insight.md)<sup></sup>

- [Yavaş posta akışı kurallarını düzeltme içgörü1](mfi-slow-mail-flow-rules-insight.md)<sup></sup>

- [Posta akış haritası](mfi-mail-flow-map-report.md)

- [E-posta ile iletili yeni etki alanları içgörü2](mfi-new-domains-being-forwarded-email.md)<sup></sup>

- [E-postayı iletirken yeni kullanıcılar içgörü2](mfi-new-users-forwarding-email.md)<sup></sup>

- [Kabul edilmeyen etki alanı raporu](mfi-non-accepted-domain-report.md)

- [Teslim olmayan rapor](mfi-non-delivery-report.md)

- [Giden ve gelen posta akışıyla ilgili içgörü](mfi-outbound-and-inbound-mail-flow.md)

- [Kuyruklar içgörü](mfi-queue-alerts-and-queues.md)

- [SMTP Kimlik Doğrulaması istemcileri içgörü ve raporu](mfi-smtp-auth-clients-report.md)

- [En üst etki alanı posta akışı durumu içgörü](mfi-domain-mail-flow-status-insight.md)

<sup>1</sup> Bu içgörü **,** Posta akışı panosunun Sizin için önerilenler alanında ancak sorun algılandığında görüntülenir. Aksi takdirde, onu görmeyin.

<sup>2</sup> Bu içgörü Posta akışı panosunda görünmez, ancak sorun algılandığında Rapor iletme sayfasında görünür[](view-mail-flow-reports.md#forwarding-report). Aksi takdirde, onu görmeyin.

## <a name="permissions-required-to-view-the-mail-flow-dashboard"></a>Posta akışı panosunun görüntülemek için gereken izinler

Posta akışı panosu, aşağıdaki rol gruplarının üyeleri tarafından kullanılabilir:

- **Güvenlik Ve** Uyumluluk Merkezi'& Kuruluş Yönetimi (genel yöneticiler).

- **[Exchange Yönetici'Azure Active Directory](/azure/active-directory/roles/permissions-reference#exchange-administrator)**.

- **Güvenlik ve Uyumluluk** Merkezi'nde MailFlow &. Hesap aynı zamanda Kuruluş Yönetimi veya Yönetici rol gruplarının üyesi Exchange yoksa, aşağıdaki sorunları göz önünde bulundurabilirsiniz:
  - Kullanıcının, doğrudan güvenlik ve Uyumluluk Merkezi'&'nde oturum açması gerekir <https://protection.office.com>.
  - Kullanıcının Posta akışı panosu üzerinde yalnızca salt okunur izni olur.
  - Kullanıcının diğer kullanıcılara erişimi Microsoft 365 yönetim merkezi.

İzinler hakkında daha fazla bilgi için, Güvenlik ve Uyumluluk [&'nde](permissions-in-the-security-and-compliance-center.md) İzinler ve Kullanıcılara Güvenlik ve [Uyumluluk Merkezi'& verin.](grant-access-to-the-security-and-compliance-center.md)

## <a name="where-to-find-the-mail-flow-dashboard"></a>Posta akışı panosu nerede bulur?

Güvenlik ve Uyumluluk & 'ı açın, <https://protection.office.com>**Posta akışı'nda genişletin ve** Pano'ya **seçin**.

Doğrudan Posta akışı panosuna gitmek için, 'i açın <https://protection.office.com/mailflow/dashboard>.