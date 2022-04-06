---
title: Bildirilen iletiler için yönetici incelemesi
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
audience: Admin
ms.topic: how-to
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
ms.custom: ''
description: Bildirilen iletileri gözden geçirmeyi ve kullanıcılarınıza geri bildirim yapmayı öğrenin.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 44476e7a8ad3bad9b21e82a9528593ceb350257d
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64470911"
---
# <a name="admin-review-for-reported-messages"></a>Bildirilen iletiler için yönetici incelemesi

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Geçerli olduğu yer:**
- [Office 365 için Microsoft Defender plan 1 ve plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Microsoft 365 kutusu ve Exchange Online kutusu olan Office 365 için Microsoft Defender, yöneticiler bildirilen iletileri gözden geçirmelerinin ardından artık şablonlı iletileri son kullanıcılara geri gönderebilir. Şablonlar, organizasyonunız için özelleştirilebilir ve yöneticinizin kararına bağlı olarak da özelleştirilebilir.

Bu özellik kullanıcılarınıza geri bildirim vermek üzere tasarlanmıştır, ancak sistem içerisinde ileti kararlarını değiştirmez. Microsoft'un filtrelerini güncelleştirmesini ve geliştirmesini yardımcı olmak için, Yönetici gönderimini kullanarak çözümleme için [ileti göndermeniz gerekir](admin-submission.md).

İleti yalnızca, hatalı pozitif veya yanlış negatif olarak bildiriliyorsa, sonuçları gözden geçirme sonuçlarını işaretp [bildirebilirsiniz](report-false-positives-and-false-negatives.md).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Başlamadan önce bilmeniz gerekenler

- Microsoft 365 Defender portalını açın<https://security.microsoft.com>. Doğrudan Gönderiler **sayfasına gitmek için** kullanın <https://security.microsoft.com/reportsubmission>.

- Kullanıcı gönderimlerinin yapılandırmasını değiştirmek için, aşağıdaki rol gruplarından birinin üyesi olmak gerekir:
  - Web Portalı'nın Kuruluş Yönetimi [Microsoft 365 Defender.](permissions-microsoft-365-security-center.md)
  - Kuruluş Yönetimi ([Exchange Online](/Exchange/permissions-exo/permissions-exo#role-groups).

- Exchange Online PowerShell'e de erişiminiz vardır. Kullanmaya istediğiniz hesabın PowerShell'de Exchange Online erişimi yoksa, Etki alanınıza bir e-posta adresi belirtin *hatasını alırsınız*. PowerShell'de erişimi etkinleştirme veya devre dışı Exchange Online daha fazla bilgi için aşağıdaki konulara bakın:
  - [Exchange Online PowerShell'e erişimi etkinleştirme veya devre dışı bırakma](/powershell/exchange/disable-access-to-exchange-online-powershell)
  - [Web'de İstemci Erişimi Exchange Online](/exchange/clients-and-mobile-in-exchange-online/client-access-rules/client-access-rules)

## <a name="notify-users-from-within-the-portal"></a>Kullanıcıları portalın içinde bilgilendirin

1. Microsoft 365 Defender portalında, E-posta <https://security.microsoft.com>ve **işbirliği** Gönderileri'nin **Gönderiler &** \> **gidin**. Doğrudan Gönderiler **sayfasına gitmek için** kullanın <https://security.microsoft.com/reportsubmission>.

2. Kullanıcı **tarafından bildirilen iletiler'e** tıklayın, ardından işaretlemek ve bildirmek istediğiniz iletiyi seçin.

3. Farklı işaretle **ve bildir açılan liste'yi** seçin ve ardından Tehdit **bulunamadı, Kimlik** Avı **veya Gereksiz'i** **seçin**.

   > [!div class="mx-imgBorder"]
   > :::image type="content" source="../../media/admin-review-send-message-from-portal.png" alt-text="Kullanıcı tarafından bildirilen iletilerin görüntülandığı sayfa" lightbox="../../media/admin-review-send-message-from-portal.png":::

Bildirilen ileti hatalı pozitif veya yanlış negatif olarak işaretlenir ve portaldan iletiyi bildiren kullanıcıya otomatik olarak bir e-posta gönderilir.

## <a name="customize-the-messages-used-to-notify-users"></a>Kullanıcıları bilgilendirmede kullanılan iletileri özelleştirme

1. Microsoft 365 Defender portalında, <https://security.microsoft.com>E-posta ve İşbirliği İlkeleri  **sayfasındaki Kullanıcı** gönderimleri sayfasına & \> Kuralları Tehdit ilkeleri  **&** \>  \>, Kullanıcı Diğer bölümünde ileti **ayarlarını** bildirdi. Doğrudan Kullanıcı gönderimleri **sayfasına gitmek için** , kullanın <https://security.microsoft.com/userSubmissionsReportMessage>.

2. Kullanıcı gönderimleri sayfasında, gönderenin görünen adını belirtmek isterseniz, Yönetici inceleme sonuçları için **e-posta** bildirimleri bölümünde Office 365 e-posta adresini belirtin kutusunu işaretleyin ve kullanmak istediğiniz adı girin. E-posta adresi, e-Outlook ve tüm yanıtlar bu adrese gider.

3. Şablonlardan herhangi birini özelleştirmek için sayfanın en altındaki **E-posta** bildirimini özelleştir'e tıklayın. Açılan açılır listede yalnızca şunları özelleştirebilirsiniz:

    - Kimlik Avı
    - Gereksiz
    - Tehdit bulunamadı
    - Alt Bilgi

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="../../media/admin-review-customize-message.png" alt-text="Özelleştirme onayı iletisi sayfası" lightbox="../../media/admin-review-customize-message.png":::

4. Bitirdiğinizde, **Kaydet**'i tıklatın. Bu değerleri temizlemek için, **Kullanıcı gönderimleri** **sayfasında At'a** tıklayın.
