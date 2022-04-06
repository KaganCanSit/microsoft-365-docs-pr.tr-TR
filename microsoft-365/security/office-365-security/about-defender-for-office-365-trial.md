---
title: En son Office 365 için Microsoft Defender hakkında
f1.keywords: ''
ms.author: chrisda
author: chrisda
manager: dansimp
audience: Admin
ms.topic: overview
ms.prod: m365-security
ms.technology: mdo
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: ''
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
ms.custom:
- seo-marvel-apr2020
ROBOTS: NOINDEX, NOFOLLOW
description: Yöneticiler, yeni sürümün deneme modu hakkında bilgi Office 365 için Microsoft Defender
ms.openlocfilehash: f1bb280502908143171cbc7b08df7080d0040df2
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64477115"
---
# <a name="about-the-microsoft-defender-for-office-365-trial"></a>En son Office 365 için Microsoft Defender hakkında

> [!IMPORTANT]
> Kullanmaya başlayın kullanımı kolay Deneme çalışma kitabımız [ile hızlı bir şekilde Office 365 için Microsoft Defender](trial-playbook-defender-for-office-365.md). Bu çalışma kitabı, çalışma kitabıyla organizasyonlarınızı nasıl korumanız olduğunu göstererek ücretsiz denemenizi en iyi şekilde Office 365 için Microsoft Defender.

Office 365 için Microsoft Defender, e-posta iletileri, bağlantılar (URL'ler) ve işbirliği araçları tarafından tehditlere karşı organizasyonlarınızı korur. Office 365 için Defender şunları içerir:

- **Tehdit koruması ilkeleri**: Organizasyonunız için uygun koruma düzeyini ayarlamak üzere tehdit koruması ilkelerini tanımlayın.
- **Raporlar**: Kuruluş performansını izlemek için Office 365 için Defender raporları görüntüleniyor.
- **Tehdit soruşturması ve yanıt özellikleri**: Tehditleri araştırmak, anlamak, benzetmek ve engellemek için önde gelen araçları kullanın.
- **Otomatik araştırma ve yanıt özellikleri**: Zaman ve çabadan tasarruf etmek için araştırma ve tehditleri azaltmaya yönelik çabalar gerekir.

Ücretsiz Office 365 için Microsoft Defender deneme, plan 2'nin özelliklerini yalnızca birkaç tıklamayla ücretsiz Office 365 için Defender bir deneme yoludır. Bu üst düzey özellikler aşağıdaki tabloda açıklanmıştır:

|Özellik|Açıklama|
|---|---|
|[Kimlik avı önleme ilkelerde özel kullanım ayarları](set-up-anti-phishing-policies.md#exclusive-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365)|Kullanıcı kimliğe bürünme koruması, etki alanı kimliğe bürünme koruması, posta kutusu zekası ve gelişmiş kimlik avı eşiklerini alın.|
|[Kasa Ekleri Kaydetme](safe-attachments.md)|Yeni ve kötü amaçlı yazılımdan korunmak için denetimli bir detonation ortamında e-posta eklerini ve diğer dosyaları denetleme.|
|[Güvenli Bağlantılar](safe-links.md)|İlk incelemeyi geçmeyecek olan URL'lerin iyi hale getirildiklerinden emin olmak için tıklayma süresi denetimlerini gerçekleştirin.|
|[Tehdit İzleyicileri](threat-trackers.md)<sup>\*</sup>|Organizasyon etkileyen siber güvenlik sorunlarını tanımlamak için bilgilendirici widget'ları ve görünümleri kullanın.|
|[Tehdit Gezgini](threat-explorer.md)<sup>\*</sup>|E-postanıza yönelik tehditlerle ilgili gerçek zamanlı bilgilere Office 365 alın.|
|[Otomatik araştırma ve yanıt (AIR)](office-365-air.md)<sup>\*</sup>|Uyarılar tetiklendiğinde tehdit nesnelerini otomatik olarak bulun ve düzeltmek.|
|[Saldırı benzetimi eğitimi](attack-simulation-training.md)<sup>\*</sup>|Kullanıcılarınızı kimlik avı saldırılarını tanımları ve uygun bir şekilde yanıt vermeleri için eğitin.|
|[Kampanya Görünümleri](campaigns.md)<sup>\*</sup>|Büyük ölçekli kötü amaçlı e-posta etkinliğini araştırın ve yanıt verin.|
|[Özellik özelliklerini Office 365 için Defender raporlar](view-reports-for-mdo.md)|Tehdit koruması durumu, URL tehdit koruması, posta gecikme süresi ve daha fazlasını içeren raporları görüntüye ekleyin.|
|[Öncelik hesabı koruması](/microsoft-365/admin/setup/priority-accounts)<sup>\*</sup>|Öncelik hesabı olarak tanım kullanıcılarınız uyarılarda, raporlarda ve araştırmalarda etiketlenir ve böylece dikkatleri üzerinde dururlar. Ayrıca, Filtrelerde Öncelik etiketini de kullanabilirsiniz.|

<sup>\*</sup>Bu özellik Plan 2 Office 365 için Defender'ye özeldir.

## <a name="set-up-a-defender-for-office-365-trial"></a>Office 365 için Defender ayarlama

Deneme sürümü, kuruluşların bilgisayar özelliklerini kolayca ayarlamasını ve Office 365 için Defender olanak sağlar. Kurulum sırasında, Office 365 için Defender'e özel ilkeler (özellikle [de Kasa](safe-attachments.md) E-posta iletileri için ekler, [e-posta](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365) iletileri ve [Microsoft Teams için Kasa](safe-links.md) Bağlantıları ve kimlik avı önleme ilkelerinde kimliğe bürünme koruması) önceden ayarlanmış güvenlik için Standart şablonu kullanılarak uygulanır [ ilkelerine tabidir](preset-security-policies.md).

Varsayılan olarak, bu ilkeler kuruluş kapsamındaki tüm kullanıcılara yöneliktir, ancak deneme sürümü sırasında veya sonrasında, ilke atamayı belirli kullanıcılarla değiştirebilirsiniz.

> [!NOTE]
> Mevcut istenmeyen posta önleme ilkeleriniz, istenmeyen posta önleme ilkelerde yüksek  güveni olan istenmeyen posta kararlarını almak için İletiyi Gereksiz E-posta klasörüne taşı eylemiyle yapılandırılmış olabilir. Önceden tanımlı güvenlik ilkeleri için Standart şablonu, yüksek güven  istenmeyen posta için Karantina iletisi eylemini kullanır ve önceden ayarlanmış güvenlik ilkeleri her zaman özel istenmeyen posta önleme ilkeleri veya varsayılan istenmeyen posta önleme ilkesi önce uygulanır. Varsayılan, Standart ve Katı ayarları hakkında daha fazla bilgi için bkz. EOP ve Güvenlik için [önerilen Office 365 için Microsoft Defender.](recommended-settings-for-eop-and-office365.md)

Diğer iş yükleri de koruma için kullanılabilir (örneğin, [Kasa SharePoint, OneDrive, Microsoft Teams ve Kasa](mdo-for-spo-odb-and-teams.md) Uygulamaları için [Office 365 Ekleri](safe-links.md#safe-links-settings-for-office-365-apps).

Deneme sürümünün kurulumu sırasında Plan 2'ye özel Office 365 için Defender yanıt işlevselliği (örneğin, [AIR](office-365-air.md) ve [Threat Explorer](threat-explorer.md) tüm kuruluş için de ayarlanır). İlkenin tanınması gerekmez.

## <a name="licensing"></a>Lisanslama

Deneme kurulumu kapsamında, Office 365 için Defender lisansı kuruluşa otomatik olarak uygulanır. Lisanslar ilk 90 gün boyunca ücretsizdir.

Deneme için lisans kartı aşağıdaki bilgileri gösterir:

:::image type="content" source="../../media/mdo-trial-licensing-card.png" alt-text="Office 365 için Microsoft Defender denemesinde Lisans kartı" lightbox="../../media/mdo-trial-licensing-card.png":::

- **Kullanım türü** bölümü:
  - **Deneme**: Office 365 için Defender kullanabileceğiniz deneme sürümü lisanslarının sayısıdır.

    > [!NOTE]
    > Diğer konumlarda, kullanılabilir deneme lisansı sayınız için 300 değerinin 300 olduğunu da görebilirler. Bu değer yanlıştır (kuruluşta tam 300 kullanıcı olmadığı sürece). Sizin için kullanılabilir deneme lisansı sayısı, rastgele 300 değerine değil, organizasyon büyüklüğüne karşılık gelen lisans sayısıdır.

  - **Ücretli**: Lisanslarda ücretli Office 365 için Defender (varsa)

- **Kullanım** bölümü: Kullanıcılarınızı kaç kullanıcınız Office 365 için Defender kapsamında?
  - **Yalnızca & algılama**: Aşağıdaki senaryolara dahil olan toplam kullanıcı sayısı:
    - Deneme süresi boyunca, ilkelerin kapsamını belirli kullanıcılar için belirttiniz.
    - Kapsamları belirli kullanıcılara göre olan özel güvenlik açıkları vardır.
  - **Tam koruma**: Plan 2 özellikleri (AIR, Threat Explorer, Saldırı benzetim eğitimi Office 365 için Defender gibi) tarafından korunan toplam kullanıcı sayısı.

## <a name="permissions"></a>İzinler

Denemeyi başlatmak veya sona erdir olmak için, Genel Yönetici veya Güvenlik Yöneticisi  **rollerinin** bir üyesi Azure Active Directory. Ayrıntılar için bkz. [Yönetici rolleri hakkında](../../admin/add-users/about-admin-roles.md).

## <a name="additional-information"></a>Ek bilgiler

Denemeyi başladıktan sonra, değişikliklerin ve güncelleştirmelerin kullanılabilir olması 2 saat kadar sürebilir. Ayrıca yöneticilerin değişiklikleri görmek için oturum açması ve yeniden oturum açması gerekir.

## <a name="availability"></a>Kullanılabilirlik

Office 365 için Defender denemesi, belirli ölçütlere uyan ve mevcut Office 365 için Defender Plan 2 lisansları (aboneliklerine dahil veya bir eklenti olarak) olmayan müşterilere aşamalı olarak sunulmaktadır.

## <a name="terms-and-conditions"></a>Hüküm ve koşullar

Daha fazla bilgi için deneme [Office 365 için Microsoft Defender Koşulları'& bakın](defender-for-office-365-trial-terms-and-conditions.md).

## <a name="frequently-asked-questions"></a>Sık sorulan sorular

### <a name="q-how-do-i-extend-the-trial"></a>S: Nasıl yaparım? uzatmak mı?

A: Bkz. [Deneme sürenizi uzatma](/microsoft-365/commerce/try-or-buy-microsoft-365#extend-your-trial).

### <a name="q-what-happens-to-my-data-after-the-trial-expires"></a>S: Deneme süresi sona erdikten sonra verilerime ne olur?

A: Deneme süreniz sona erdikten sonra, 30 gün boyunca deneme verilerinize (daha önce sahip olmadığınız Office 365 için Defender özelliklerden gelen veriler) erişebilirsiniz. Bu 30 günlük sürenin ardından, yeni deneme sürümüyle Office 365 için Defender ilkeler ve veriler silinir.

### <a name="q-how-many-times-can-i-use-the-defender-for-office-365-trial-in-my-organization"></a>S: Kuruluşumda Office 365 için Defender kez kullanabilirim?

A: En fazla 2 kez. İlk denemenizin süresi dolsa, son kullanma tarihinden sonra en az 30 gün beklemeniz gerekir. Daha sonra tekrar deneme Office 365 için Defender gerekir. İkinci denemeden sonra, başka bir deneme sürümüne kaydolayamaz.

## <a name="learn-more-about-defender-for-office-365"></a>Daha fazla bilgi Office 365 için Defender

Office 365 için Defender kapsamlı bir özellik sunarak kuruluşların güvenliğini sağlamalarına yardımcı olur.

Ayrıca bu etkileşimli kılavuzda, Office 365 için Defender daha fazla [bilgi edinabilirsiniz](https://aka.ms/MS365D.InteractiveGuide).

:::image type="content" source="../../media/microsoft-defender-for-office-365.png" alt-text="The Office 365 için Microsoft Defender conceptual diagram" lightbox="../../media/microsoft-defender-for-office-365.png":::

### <a name="prevention"></a>Engelleme

Güçlü bir filtreleme yığını iş e-posta güvenliği, kimlik bilgisi kimlik avı, fidye yazılımı ve gelişmiş kötü amaçlı yazılım gibi çok çeşitli hacim tabanlı ve hedefli saldırılar engeller.

- [Kimlik avı önleme ilkeleri: Kimlik avı için özel Office 365 için Defender](set-up-anti-phishing-policies.md#exclusive-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365)
- [Kasa Ekleri Kaydetme](safe-attachments.md)
- [Güvenli Bağlantılar](safe-links.md)

### <a name="detection"></a>Algılama

Endüstri lideri AI kötü amaçlı ve şüpheli içerikleri algılar ve korumadan korunma için tasarlanmış kampanyaları tanımlamak için saldırı düzenlerini yakınlar.

- [Office 365 için Microsoft Defender'da Saldırı Kampanyası Görünümleri](campaigns.md)

### <a name="investigation-and-hunting"></a>Araştırma ve av

Güçlü deneyimler, tüm kullanıcılar genelindeki saldırıları izlemek için gelişmiş koruma özellikleriyle tehditleri belirlemeye, önceliklerini belirlemeye ve araştırmaya yardımcı Office 365.

- [Tehdit Gezgini ve Gerçek zamanlı algılamalar](threat-explorer.md)
- [Office 365 için Defender'da gerçek zamanlı Office 365 için Defender](view-reports-for-mdo.md)
- [Tehdit İzleyicileri - Yeni ve Dikkat çekici](threat-trackers.md)
- Microsoft 365 Defender [ile tümleştirme](../defender/microsoft-365-defender.md)

### <a name="response-and-remediation"></a>Yanıt ve düzeltme

Kapsamlı olay müdahalesi ve otomasyon özellikleri, güvenlik ekibinin verimliliği ve verimliliğini artırır.

- [Web'de otomatik araştırma ve yanıt (AIR) Office 365 için Microsoft Defender](office-365-air.md)

### <a name="awareness-and-training"></a>Farkındalık ve eğitim

Zengin benzetim ve eğitim özellikleriyle birlikte istemci uygulamaları içindeki tümleşik deneyimler kullanıcı farkındalığını geliştirmektedir.

- [Kullanmaya başlayın benzetimi eğitimlerini kullanma](attack-simulation-training-get-started.md)

### <a name="security-posture"></a>Güvenlik mezrası

Önerilen şablonlar ve yapılandırma içgörüleri müşterilerin güvenli bir şekilde alımalarını ve güvende kalmalarını sağlar.

- [EOP ve Office 365 için Microsoft Defender'da önceden ayarlanmış güvenlik ilkeleri](preset-security-policies.md)
- [EOP ve veritabanı koruma ilkeleri için yapılandırma çözümleyicisi Office 365 için Microsoft Defender](configuration-analyzer-for-security-policies.md).

## <a name="give-feedback"></a>Geri bildirim gönderin

Geri bildiriminiz, ortamınızı gelişmiş saldırılardan koruma konusunda daha iyi bir şekilde çalışmamıza yardımcı olur. Deneyimlerinizi ve ürün özelliklerinizi ve deneme sonuçlarınızı paylaşın.
