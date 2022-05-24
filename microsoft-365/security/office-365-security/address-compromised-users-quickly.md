---
title: Güvenliği aşılmış kullanıcı hesaplarını otomatik araştırma ve yanıtla ele alın
keywords: AIR, autoIR, Uç Nokta için Microsoft Defender, otomatik, araştırma, yanıt, düzeltme, tehditler, gelişmiş, tehdit, koruma, güvenliği aşıldı
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
description: Office 365 için Microsoft Defender Plan 2'de otomatik araştırma ve yanıt özellikleriyle güvenliği aşılmış kullanıcı hesaplarını algılama ve ele alma sürecini nasıl hızlandıracağınızı öğrenin.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 8628f1952f37f43a66daccb5f0792097ce798c31
ms.sourcegitcommit: 725a92b0b1555572b306b285a0e7a7614d34e5e5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/24/2022
ms.locfileid: "65649053"
---
# <a name="address-compromised-user-accounts-with-automated-investigation-and-response"></a>Güvenliği aşılmış kullanıcı hesaplarını otomatik araştırma ve yanıtla ele alın

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Uygulandığı öğe**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Office 365 için Microsoft Defender plan 1 ve plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

[Office 365 için Microsoft Defender Plan 2](defender-for-office-365.md#microsoft-defender-for-office-365-plan-1-and-plan-2) güçlü [otomatik araştırma ve yanıt](office-365-air.md) (AIR) özellikleri içerir. Bu tür özellikler, güvenlik operasyonları ekibinize tehditlerle ilgili çok fazla zaman ve çaba tasarrufu sağlayabilir. Microsoft, güvenlik özelliklerini geliştirmeye devam ediyor. Kısa süre önce, AIR özellikleri güvenliği aşılmış bir kullanıcı güvenliği playbook'u (şu anda önizleme aşamasında) içerecek şekilde geliştirildi. Güvenliği aşılmış kullanıcı güvenliği playbook'u hakkında daha fazla bilgi edinmek için bu makaleyi okuyun. Ayrıca ek ayrıntılar [için kullanıcı güvenliğinin aşılması ve ihlal kapsamını Office 365 için Microsoft Defender sınırlamak için süreyi algılama ve yanıtlama süresini hızlandırma](https://techcommunity.microsoft.com/t5/Security-Privacy-and-Compliance/Speed-up-time-to-detect-and-respond-to-user-compromise-and-limit/ba-p/977053) blog gönderisine bakın.

![Güvenliği aşılmış bir kullanıcı için otomatik araştırma.](/microsoft-365/media/office365atp-compduserinvestigation.jpg)

Güvenliği aşılmış kullanıcı güvenliği playbook'u, kuruluşunuzun güvenlik ekibinin şunları yapmalarına olanak tanır:

- Güvenliği aşılmış kullanıcı hesaplarının algılanması hızlandırılır;
- Bir hesabın güvenliği aşıldığında ihlalin kapsamını sınırlamak; Ve
- Güvenliği aşılmış kullanıcılara daha etkili ve verimli bir şekilde yanıt verin.

## <a name="compromised-user-alerts"></a>Güvenliği aşılmış kullanıcı uyarıları

Bir kullanıcı hesabının güvenliği aşıldığında, atipik veya anormal davranışlar oluşur. Örneğin, kimlik avı ve istenmeyen posta iletileri güvenilen bir kullanıcı hesabından dahili olarak gönderilebilir. Office 365 için Defender, Office 365 içindeki e-posta düzenlerinde ve işbirliği etkinliğinde bu tür anomalileri algılayabilir. Bu durumda uyarılar tetiklenir ve tehdit azaltma işlemi başlar.

Örneğin, şüpheli e-posta gönderme nedeniyle tetiklenen bir uyarı aşağıda verilmişti:

![Şüpheli e-posta gönderme nedeniyle tetiklenen uyarı.](/microsoft-365/media/office365atp-suspiciousemailsendalert.jpg)

Aşağıda, bir kullanıcı için gönderme sınırına ulaşıldığında tetiklenen bir uyarı örneği verilmişti:

![Gönderme sınırına ulaşılarak tetiklenen uyarı.](/microsoft-365/media/office365atp-sendinglimitreached.jpg)

## <a name="investigate-and-respond-to-a-compromised-user"></a>Güvenliği aşılmış bir kullanıcıyı araştırma ve yanıtlama

Bir kullanıcı hesabının güvenliği aşıldığında uyarılar tetiklenir. Bazı durumlarda bu kullanıcı hesabı engellenir ve sorun kuruluşunuzun güvenlik operasyonları ekibi tarafından çözülene kadar başka e-posta iletileri göndermesi engellenir. Diğer durumlarda, güvenlik ekibinizin gerçekleştirmesi gereken önerilen eylemlere neden olabilecek otomatik bir araştırma başlar.

- [Kısıtlanmış kullanıcıları görüntüleme ve araştırma](#view-and-investigate-restricted-users)

- [Otomatik araştırmalarla ilgili ayrıntıları görüntüleme](#view-details-about-automated-investigations)

> [!IMPORTANT]
> Aşağıdaki görevleri gerçekleştirmek için uygun izinlere sahip olmanız gerekir. Bkz [. AIR özelliklerini kullanmak için gerekli izinler](office-365-air.md#required-permissions-to-use-air-capabilities).

Otomatik Araştırma ve Yanıt (AIR) ve güvenliği aşılmış kullanıcı uyarılarını kullanarak Office 365 için Microsoft Defender kullanıcı güvenliğinin aşıldığını nasıl algılayıp yanıtlayabileceğinizi öğrenmek için bu kısa videoyu izleyin.
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWAl83]

### <a name="view-and-investigate-restricted-users"></a>Kısıtlanmış kullanıcıları görüntüleme ve araştırma

Kısıtlı kullanıcılar listesine gitmek için birkaç seçeneğiniz vardır. Örneğin, Microsoft 365 Defender portalında **E-posta & işbirliği** \> **Kısıtlı Kullanıcıları** **Gözden Geçir'e** \> gidebilirsiniz. Aşağıdaki yordam, tetiklenmiş olabilecek çeşitli uyarı türlerini görmenin iyi bir yolu olan **Uyarılar** panosunu kullanarak gezintiyi açıklar.

1. adresinden Microsoft 365 Defender portalını <https://security.microsoft.com> açın ve **Olaylar & Uyarılar'a** \> gidin. Veya doğrudan **Uyarılar** sayfasına gitmek için kullanın <https://security.microsoft.com/alerts>.

2. **Uyarılar** sayfasında, sonuçları zaman aralığına göre filtreleyin ve **Kullanıcı adlı ilkenin e-posta göndermesi kısıtlandı**.

   :::image type="content" source="../../media/m365-sc-alerts-page-with-restricted-user.png" alt-text="kısıtlı kullanıcılar için filtrelenmiş Microsoft 365 Defender portalındaki Uyarılar sayfası" lightbox="../../media/m365-sc-alerts-page-with-restricted-user.png":::

3. Adı tıklatarak girdiyi seçerseniz, gözden geçirmeniz için ek ayrıntılar içeren **e-posta göndermesi kısıtlanmış bir Kullanıcı** sayfası açılır. **Uyarıyı yönet** düğmesinin yanında Diğer seçenekler simgesine tıklayabilirsiniz![.](../../media/m365-cc-sc-more-actions-icon.png) **Diğer seçenekler'i** seçip **Kısıtlanmış kullanıcı ayrıntılarını görüntüle'yi** seçerek **Kısıtlanmış kullanıcıları** [serbest bırakabileceğiniz Kısıtlı kullanıcılar](removing-user-from-restricted-users-portal-after-spam.md) sayfasına gidin.

  :::image type="content" source="../../media/m365-sc-alerts-user-restricted-from-sending-email-page.png" alt-text="Kullanıcının e-posta göndermesi kısıtlandı sayfası" lightbox="../../media/m365-sc-alerts-user-restricted-from-sending-email-page.png":::

### <a name="view-details-about-automated-investigations"></a>Otomatik araştırmalarla ilgili ayrıntıları görüntüleme

Otomatik bir araştırma başladığında ayrıntılarını ve sonuçlarını Güvenlik & Uyumluluk Merkezi'nde görebilirsiniz. **Tehdit yönetimi** \> **Araştırmaları'na** gidin ve ayrıntılarını görüntülemek için bir araştırma seçin.

Daha fazla bilgi için bkz. [Araştırmanın ayrıntılarını görüntüleme](air-view-investigation-results.md).

## <a name="keep-the-following-points-in-mind"></a>Aşağıdaki noktaları göz önünde bulundurun

- **Uyarılarınızdan haberdar olun**. Bildiğiniz gibi, bir uzlaşma ne kadar uzun süre algılanmazsa, kuruluşunuz, müşterileriniz ve iş ortaklarınız için geniş çapta etki ve maliyet potansiyeli o kadar büyük olur. Erken algılama ve zamanında yanıt, tehditleri azaltmak için ve özellikle de bir kullanıcının hesabının gizliliği tehlikeye atıldığında kritik önem taşır.

- **Otomasyon, güvenlik operasyonları ekibinize yardımcı olur ancak yerini almaz**. Otomatik araştırma ve yanıt özellikleri güvenliği aşılmış bir kullanıcıyı erken zamanda algılayabilir, ancak güvenlik operasyonları ekibinizin büyük olasılıkla bazı araştırma ve düzeltme işlemleriyle uğraşması ve yapması gerekir. Bu konuda yardıma mı ihtiyacınız var? Bkz. [Eylemleri gözden geçirme ve onaylama](air-review-approve-pending-completed-actions.md).

- **Tek göstergeniz olarak şüpheli oturum açma uyarısına güvenmeyin**. Bir kullanıcı hesabının güvenliği aşıldığında, şüpheli bir oturum açma uyarısı tetikleyebilir veya tetiklemeyebilir. Bazen bir hesabın güvenliği aşıldıktan sonra gerçekleşen ve uyarıyı tetikleyen etkinlikler dizisidir. Uyarılar hakkında daha fazla bilgi edinmek ister misiniz? Bkz [. Uyarı ilkeleri](../../compliance/alert-policies.md).

## <a name="next-steps"></a>Sonraki adımlar

- [AIR özelliklerini kullanmak için gerekli izinleri gözden geçirin](office-365-air.md#required-permissions-to-use-air-capabilities)

- [Office 365'da kötü amaçlı e-posta bulma ve araştırma](investigate-malicious-email-that-was-delivered.md)

- [Uç Nokta için Microsoft Defender'da AIR hakkında bilgi edinin](/windows/security/threat-protection/microsoft-defender-atp/automated-investigations)

- [Yakında sunulacakları görmek için Microsoft 365 Yol Haritası'nı ziyaret edin](https://www.microsoft.com/microsoft-365/roadmap?filters=)
