---
title: Otomatik soruşturma ve yanıtla güvenliği tehlikeye kullanıcı hesaplarını ele
keywords: AIR, autoIR, Uç Nokta için Microsoft Defender, otomatik, araştırma, yanıt, düzeltme, tehdit, gelişmiş, tehdit, koruma, güvenliği ihlal
ms.author: deniseb
author: denisebmsft
manager: dansimp
audience: ITPro
ms.topic: article
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.collection: M365-security-compliance
ms.custom: ''
ms.date: 06/10/2021
description: Plan 2 için Microsoft Defender'da otomatik soruşturma ve yanıt özellikleriyle güvenliği tehlikeye atılmış kullanıcı hesaplarını algılama ve ele Office 365 işlemi nasıl hızlandıracaklarını öğrenin.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: cbc3c6c8a81d59bebbd5272e13e0f96de2257623
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2022
ms.locfileid: "63028454"
---
# <a name="address-compromised-user-accounts-with-automated-investigation-and-response"></a>Otomatik soruşturma ve yanıtla güvenliği tehlikeye kullanıcı hesaplarını ele

**Geçerli olduğu yer:**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [1. plan Office 365 plan 2 için Microsoft Defender](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)


Uygulama [için Microsoft Defender Office 365 Plan 2](defender-for-office-365.md#microsoft-defender-for-office-365-plan-1-and-plan-2) güçlü [otomatik soruşturma ve yanıt](office-365-air.md) (AIR) özellikleri içerir. Bu tür özellikler güvenlik işlemleri ekibinizi tehditlere karşı çok zaman ve çabadan tasarruf sağlar. Microsoft, güvenlik özelliklerini geliştirmeye devam etmektedir. Kısa süre önce, güvenliği tehlikeye atılmış bir kullanıcı güvenlik çalışma kitabını (şu anda önizlemede) içerecek şekilde AIR özellikleri geliştirilmişti. Güvenliği tehlikeye atılmış kullanıcı güvenliği playbook'ları hakkında daha fazla bilgi edinmek için bu makaleyi okuyun. Ayrıca, diğer ayrıntılar [için Microsoft Defender](https://techcommunity.microsoft.com/t5/Security-Privacy-and-Compliance/Speed-up-time-to-detect-and-respond-to-user-compromise-and-limit/ba-p/977053) ile kullanıcının güvenliğini algılamak ve buna yanıt vermek ve ihlal kapsamını sınırlamak için sürenizi hızlandırın blog gönderisini Office 365 bakın.

![Güvenliği tehlikeye atılmış bir kullanıcı için otomatik araştırma.](/microsoft-365/media/office365atp-compduserinvestigation.jpg)

Güvenliği tehlikeye atılmış kullanıcı güvenliği playbook'ları, kuruluş güvenlik ekibinin şunlarılar için olanak sağlar:

- Güvenliği ihlal edilmiş kullanıcı hesaplarını algılamayı hızlandırın;
- Bir hesabın güvenliği aşılmış durumdayken ihlal kapsamını sınırlandırma; ve
- Güvenliği tehlikeye atılmış kullanıcılara daha etkili ve verimli bir şekilde yanıt verin.

## <a name="compromised-user-alerts"></a>Güvenliği ihlal edilmiş kullanıcı uyarıları

Bir kullanıcı hesabının güvenliği ihlal edilmiş durumdayken, atipik veya anormal davranışlar oluşur. Örneğin, kimlik avı ve istenmeyen posta iletileri güvenilir bir kullanıcı hesabından dahili olarak gönderebilirsiniz. Kullanıcı için Defender Office 365 e-posta düzenleri ve iş birliği etkinlikleri içinde bu tür etkinlikleri Office 365. Böyle bir durumda, uyarılar tetiklenir ve tehdit azaltma işlemi başlar.

Örneğin, şüpheli e-posta göndermesi nedeniyle tetiklenen bir uyarı var:

![Şüpheli e-posta gönderme nedeniyle tetiklenen uyarı.](/microsoft-365/media/office365atp-suspiciousemailsendalert.jpg)

Kullanıcıya gönderme sınırına ulaşlendiğinde tetiklenen uyarı örneği:

![Gönderme sınırına ulaşarak tetiklenen uyarı.](/microsoft-365/media/office365atp-sendinglimitreached.jpg)

## <a name="investigate-and-respond-to-a-compromised-user"></a>Güvenliği tehlikeye atılmış bir kullanıcıyı araştırma ve yanıtlama

Bir kullanıcı hesabının güvenliği ihlal edilmiş durumdayken uyarılar tetiklenir. Bazı durumlarda da, bu kullanıcı hesabı engellenir ve sorun çözülene kadar kuruluşun güvenlik işlemleri ekibi tarafından başka e-posta iletileri gönderilmesi engellenir. Diğer durumlarda, otomatik bir araştırma başlar ve bu da güvenlik ekibinin gerçekleştirsin önerilen eylemlere neden olabilir.

- [Kısıtlanmış kullanıcıları görüntüleme ve araştırma](#view-and-investigate-restricted-users)

- [Otomatik soruşturmalar hakkında ayrıntıları görüntüleme](#view-details-about-automated-investigations)

> [!IMPORTANT]
> Aşağıdaki görevleri gerçekleştirmek için uygun izinlere sahip olmak gerekir. Bkz [. AIR özelliklerini kullanmak için gerekli izinler](office-365-air.md#required-permissions-to-use-air-capabilities).

### <a name="view-and-investigate-restricted-users"></a>Kısıtlanmış kullanıcıları görüntüleme ve araştırma

Kısıtlanmış kullanıcılar listesine gezinmek için birkaç seçeneğiniz vardır. Örneğin, Microsoft 365 Defender portalında E-posta ve işbirliği Gözden **Geçirme &'ye** \>  \> **gidebilirsiniz**. Aşağıdaki yordamda, tetiklenen **çeşitli uyarıları** görmenin iyi bir yolu olan Uyarılar panosu kullanılarak gezinti açıklandı.

1. Microsoft 365 Defender portalını açın ve <https://security.microsoft.com> Olaylar veya **Uyarı &** \> **gidin**. Ya da doğrudan Uyarılar sayfasına **gitmek için** kullanın <https://security.microsoft.com/alerts>.

2. Uyarılar **sayfasında,** sonuçları süreye göre filtreleyebilirsiniz ve Kullanıcı'nın e-posta **göndermesini kısıtla ilkesi vardır**.

   ![Portalda kısıtlı kullanıcılar için Microsoft 365 Defender Uyarılar sayfası.](../../media/m365-sc-alerts-page-with-restricted-user.png)

3. Adı tıklatarak girdiyi seçersanız, **gözden geçirmeniz** için ek ayrıntılar içeren, e-posta göndermesi kısıtlanmış bir Kullanıcı sayfası açılır. Uyarıyı yönet **düğmesinin** yanında Diğer seçenekler simgesine ![tıklayabilirsiniz.](../../media/m365-cc-sc-more-actions-icon.png) **Diğer seçenekler'i** **seçin ve ardından** Kısıtlanmış kullanıcı ayrıntılarını görüntüle'yi  seçerek kısıtlanmış kullanıcıları [serbest bırakabilirsiniz](removing-user-from-restricted-users-portal-after-spam.md).

   ![Kullanıcı, Uyarılar merkezinden e-posta gönderme sayfasını kısıtlar.](../../media/m365-sc-alerts-user-restricted-from-sending-email-page.png)

### <a name="view-details-about-automated-investigations"></a>Otomatik soruşturmalar hakkında ayrıntıları görüntüleme

Otomatik bir araştırma başladığı zaman, ayrıntıları ve sonuçlarını Güvenlik ve Uyumluluk Merkezi'& bakabilirsiniz. Tehdit yönetimi **Soruşturmalar'a** \> **gidin** ve ayrıntılarını görüntülemek için bir araştırma seçin.

Daha fazla bilgi edinmek için bkz [. Araştırmanın ayrıntılarını görüntüleme](air-view-investigation-results.md).

## <a name="keep-the-following-points-in-mind"></a>Aşağıdaki noktaları unutmayın

- **Uyarılarınızı takipte kalın**. Bildiğiniz gibi, bir ödün algılanmazsa, kuruluş, müşteriler ve iş ortaklarınız üzerindeki etkisi ve maliyeti o kadar büyük olur. Erken algılama ve zamanında yanıt, tehditleri azaltmak ve özellikle de kullanıcının hesabının güvenliği ihlal edilmiş durumdayken çok önemlidir.

- **Otomasyon yardımı yapar, ancak güvenlik işlemleri ekibinizin yerini değiştirmez**. Otomatik soruşturma ve yanıt özellikleri güvenliği tehlikeye atılmış bir kullanıcıyı önceden algılanabilir, ancak güvenlik işlemleri ekibinin büyük olasılıkla etkileşim kurması, üzerinde biraz araştırma ve düzeltmesi olması gerekir. Bu konuda biraz yardım mı gerekiyor? Bkz [. Eylemleri gözden geçirme ve onaylama](air-review-approve-pending-completed-actions.md).

- **Tek göstergeniz olarak şüpheli oturum açma uyarılarına güvenmeyin**. Bir kullanıcı hesabının güvenliği ihlal edilmiş durumdayken, şüpheli oturum açma uyarısı atilebilir veya tetikleyemilebilir. Bazen bir hesabın güvenliği ihlal edildikten sonra oluşan ve uyarıyı tetikleyen bir dizi etkinliktir. Uyarılar hakkında daha fazla bilgi almak ister misiniz? Uyarı [ilkeleri'ne bakın](../../compliance/alert-policies.md).

## <a name="next-steps"></a>Sonraki adımlar

- [AIR özelliklerini kullanmak için gerekli izinleri gözden geçirme](office-365-air.md#required-permissions-to-use-air-capabilities)

- [E-postaları e-posta içinde bulma ve Office 365](investigate-malicious-email-that-was-delivered.md)

- [Uç nokta için Microsoft Defender'da AIR hakkında bilgi](/windows/security/threat-protection/microsoft-defender-atp/automated-investigations)

- [Yakında nelerin Microsoft 365 bilgi için Yol Haritası'nın yeni bir yolunu ziyaret edin ve kısa bir süre içinde size yol haritasında yer alan bir yol haritası ile ilgili bilgi edinin](https://www.microsoft.com/microsoft-365/roadmap?filters=)