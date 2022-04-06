---
title: Kimlik için Microsoft Defender'de bildirimleri Microsoft 365 Defender
description: E-postada Kimlik için Microsoft Defender ayarlamayı Microsoft 365 Defender.
ms.date: 05/20/2021
ms.topic: how-to
author: dcurwin
ms.author: dacurwin
ms.service: microsoft-defender-for-identity
ms.custom: admindeeplinkDEFENDER
manager: raynew
ms.collection: M365-security-compliance
ms.openlocfilehash: 89ed7ae50bf89c28bde81ea02e8905d0056ede53
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64470933"
---
# <a name="defender-for-identity-notifications-in-microsoft-365-defender"></a>Microsoft 365 Defender'ta Kimlik bildirimleri için Defender

**Aşağıdakiler için geçerlidir:**

- Microsoft 365 Defender
- Kimlik için Microsoft Defender

Bu makalede, e-posta [Kimlik için Microsoft Defender nasıl](/defender-for-identity) çalış [olduğu Microsoft 365 Defender](/microsoft-365/security/defender/overview-security-center).

> [!IMPORTANT]
> Kimlik Doğrulama ve Doğrulama Microsoft 365 Defender bir parçası olarak, kimlik için Defender portalında yer alan konumlarından bazı seçenekler ve ayrıntılar değiştirilmiştir. Hem tanıdık hem de yeni özellikleri nerede bulamıyorum? bulmak için lütfen aşağıdaki ayrıntıları okuyun.

## <a name="health-issues-notifications"></a>Sağlık sorunları bildirimleri

Diğer Microsoft 365 Defender Kimlik için Defender'da sağlık sorunlarıyla ilgili e-posta bildirimleri için alıcı  ekleyebilirsiniz.

1. Daha <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a>, Kimlikler'Ayarlar'e **gidin**.

  :::image type="content" source="../../media/defender-identity/settings-identities.png" alt-text="Ad sütunundaki Kimlikler seçeneği" lightbox="../../media/defender-identity/settings-identities.png":::


1. Durum **sorunları bildirimleri'ne seçin**.

1. Alıcının e-posta adresini girin. **Ekle**'yi seçin.

   :::image type="content" source="../../media/defender-identity/health-email-recipient.png" alt-text="Durum sorunları bildirimleri alt menüsü öğesi" lightbox="../../media/defender-identity/health-email-recipient.png":::

1. Kimlik için Defender bir sistem durumu sorunu algılarsa, alıcılar ayrıntıları içeren bir e-posta bildirimi alırlar.

   :::image type="content" source="../../media/defender-identity/health-email.png" alt-text="Sağlık sorunu e-postası" lightbox="../../media/defender-identity/health-email.png":::

    > [!NOTE]
    > E-posta, sorun hakkında ayrıntılı bilgi için iki bağlantı sağlar. **MDI** Durum Merkezi'ne veya **M365D'de yeni Durum Merkezi'ne gidebilirsiniz**.

## <a name="alert-notifications"></a>Uyarı bildirimleri

Bu Microsoft 365 Defender, algılanan uyarıların e-posta bildirimleri için alıcı  eklersiniz.

1. Daha <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a>, Kimlikler'Ayarlar'e **gidin**.

   :::image type="content" source="../../media/defender-identity/settings-identities.png" alt-text="Kimlikler seçeneği" lightbox="../../media/defender-identity/settings-identities.png":::

1. Uyarı **bildirimleri'ne seçin**.

1. Alıcının e-posta adresini girin. **Ekle**'yi seçin.

   :::image type="content" source="../../media/defender-identity/alert-email-recipient.png" alt-text="Uyarı bildirimleri alt menüsü öğesi" lightbox="../../media/defender-identity/alert-email-recipient.png":::

## <a name="syslog-notifications"></a>Syslog bildirimleri

Kimlik için Defender, Syslog sunucunuza aday bir algılayıcı aracılığıyla güvenlik ve sistem durumu uyarıları göndererek şüpheli etkinlikler algılayana kadar sizi bilgilendirir.

> [!NOTE]
> Identity için Defender for Identity'i Microsoft Sentinel ile tümleştirmeyi öğrenmek için bkz[. Microsoft Sentinel Microsoft 365 Defender tümleştirmesi](/azure/sentinel/microsoft-365-defender-sentinel-integration).

1. Daha <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a>, Kimlikler'Ayarlar'e **gidin**.

   :::image type="content" source="../../media/defender-identity/settings-identities.png" alt-text="Ad sütununda Kimlikler seçeneği" lightbox="../../media/defender-identity/settings-identities.png":::

1. **Syslog bildirimleri'ne seçin**.

1. Syslog bildirimini etkinleştirmek için **Syslog hizmetini açık** konuma **getirin** .

   :::image type="content" source="../../media/defender-identity/syslog-service.png" alt-text="2010/2003'e kadar açık olan Syslog hizmeti seçeneği" lightbox="../../media/defender-identity/syslog-service.png":::

1. Hizmeti **yapılandır'ı seçin**. Syslog hizmetinin ayrıntılarını girebilirsiniz bir bölme açılır.

   :::image type="content" source="../../media/defender-identity/syslog-sensor.png" alt-text="Syslog hizmet ayrıntılarını girmek istediğiniz sayfa" lightbox="../../media/defender-identity/syslog-sensor.png":::

1. Aşağıdaki ayrıntıları girin:

    - **Algılayıcı** - Açılan listeden uyarıları gönderecek algılayıcıyı seçin.
    - **Hizmet uç noktası** **ve Bağlantı** Noktası - syslog sunucusu için IP adresini veya tam etki alanı adını (FQDN) girin ve bağlantı noktası numarasını belirtin. Yalnızca bir Syslog uç noktası yapılandırebilirsiniz.
    - **Aktarım** - Aktarım **protokolünü** (TCP veya UDP) seçin.
    - **Biçim** - Biçimi seçin (RFC 3164 veya RFC 5424).

1. Test **SIEM bildirimi gönder'i** seçin ve Syslog altyapısı çözümde iletinin alınmıştır.

1. **Kaydet**'i seçin.

1. Syslog hizmetini yapılandırdıktan sonra **Syslog** sunucunuza hangi tür bildirimlerin (uyarı veya sistem durumu sorunları) gönder)olduğunu seçebilirsiniz.

   :::image type="content" source="../../media/defender-identity/syslog-configured.png" alt-text="Syslog hizmeti yapılandırılmış seçeneği işaretli" lightbox="../../media/defender-identity/syslog-configured.png":::

## <a name="see-also"></a>Ayrıca bkz.

- [Kimlik güvenlik uyarıları için Defender'ı yönetme](manage-security-alerts.md)
