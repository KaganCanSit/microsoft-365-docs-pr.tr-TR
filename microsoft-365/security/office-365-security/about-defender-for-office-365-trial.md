---
title: Office 365 için Microsoft Defender deneme sürümü hakkında
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
description: Yöneticiler Office 365 için Microsoft Defender deneme modu hakkında bilgi edinebilir
ms.openlocfilehash: 086ea200b6f8519c487622d02ba2d2fc8347f68a
ms.sourcegitcommit: bc35c7826e3403f259725ac72cca5bafd36aa56a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2022
ms.locfileid: "66554213"
---
# <a name="about-the-microsoft-defender-for-office-365-trial"></a>Office 365 için Microsoft Defender deneme sürümü hakkında

> [!IMPORTANT]
> [Office 365 için Microsoft Defender için kullanımı kolay Deneme playbook'umuz](trial-playbook-defender-for-office-365.md) ile hızlı bir şekilde çalışmaya başlayın. Bu playbook, Office 365 için Microsoft Defender ile kuruluşunuzu nasıl koruyacağınızı göstererek ücretsiz denemenizden en iyi şekilde yararlanabilirsiniz.

Office 365 için Microsoft Defender, kuruluşunuzu e-posta iletileri, bağlantılar (URL'ler) ve işbirliği araçları tarafından ortaya konan kötü amaçlı tehditlere karşı korur. Office 365 için Defender şunları içerir:

- **Tehdit koruma ilkeleri**: Kuruluşunuz için uygun koruma düzeyini ayarlamak için tehdit koruma ilkeleri tanımlayın.
- **Raporlar**: Kuruluşunuzdaki Office 365 için Defender performansını izlemek için gerçek zamanlı raporları görüntüleyin.
- **Tehdit araştırma ve yanıt özellikleri: Tehditleri** araştırmak, anlamak, benzetimini yapmak ve önlemek için önde gelen araçları kullanın.
- **Otomatik araştırma ve yanıt özellikleri: Tehditleri** araştırmak ve azaltmak için zaman ve çabadan tasarruf edin.

Office 365 için Microsoft Defender deneme sürümü, Office 365 için Defender Plan 2'nin özelliklerini yalnızca birkaç tıklamayla ücretsiz olarak denemenin kolay bir yoludur. Bu üst düzey özellikler aşağıdaki tabloda açıklanmıştır:

|Özellik|Açıklama|
|---|---|
|[Kimlik avı önleme ilkelerindeki özel ayarlar](set-up-anti-phishing-policies.md#exclusive-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365)|Kullanıcı kimliğe bürünme koruması, etki alanı kimliğe bürünme koruması, posta kutusu zekası ve gelişmiş kimlik avı eşikleri alın.|
|[Güvenli Ekleri Kaydetme](safe-attachments.md)|Yeni ve kaçınıcı kötü amaçlı yazılımları yakalamak için denetimli bir patlama ortamında e-posta eklerini ve diğer dosyaları inceleyin.|
|[Güvenli Bağlantılar](safe-links.md)|İlk incelemeden geçmiş olabilecek URL'lerin silahlanmadığından emin olmak için tıklama zamanı denetimleri gerçekleştirin.|
|[Tehdit İzleyicileri](threat-trackers.md)<sup>\*</sup>|Kuruluşunuzu etkileyebilecek siber güvenlik sorunlarını belirlemek için bilgilendirici pencere öğelerini ve görünümleri kullanın.|
|[Tehdit Gezgini](threat-explorer.md)<sup>\*</sup>|Office 365 e-postanızdaki tehditler hakkında neredeyse gerçek zamanlı bilgilerle avlayın.|
|[Otomatik araştırma ve yanıt (AIR)](office-365-air.md)<sup>\*</sup>|Uyarılar tetiklendiğinde tehdit nesnelerini otomatik olarak bulun ve düzeltin.|
|[Saldırı simülasyonu eğitimi](attack-simulation-training.md)<sup>\*</sup>|Kullanıcılarınızı kimlik avı saldırılarını tanımlayacak ve uygun şekilde yanıt verecek şekilde eğitin.|
|[Kampanya Görünümleri](campaigns.md)<sup>\*</sup>|Büyük ölçekli kötü amaçlı e-posta etkinliğini araştırın ve yanıtlayın.|
|[Office 365 için Defender özellikleri kullanan raporlar](view-reports-for-mdo.md)|Tehdit koruması durumu, URL tehdit koruması, posta gecikme süresi ve daha fazlası dahil olmak üzere raporları görüntüleyin.|
|[Öncelik hesabı koruması](/microsoft-365/admin/setup/priority-accounts)<sup>\*</sup>|Öncelik hesapları olarak tanımladığınız kullanıcılar dikkat çekmeleri için uyarılarda, raporlarda ve araştırmalarda etiketlenir. Filtrelerde Öncelik etiketini de kullanabilirsiniz.|

<sup>\*</sup>Bu özellik, Office 365 için Defender Plan 2'ye özeldir.

## <a name="set-up-a-defender-for-office-365-trial"></a>Office 365 için Defender deneme sürümü ayarlama

Deneme, kuruluşların Office 365 için Defender özelliklerini kolayca ayarlamasına ve yapılandırmasına olanak tanır. Kurulum sırasında, Office 365 için Defender özel ilkeler (özellikle, [e-posta iletileri için Güvenli Ekler](safe-attachments.md), [e-posta iletileri ve Microsoft Teams için Güvenli Bağlantılar ve](safe-links.md) [kimlik avı önleme ilkelerinde kimliğe bürünme koruması](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365)) [önceden ayarlanmış güvenlik ilkeleri](preset-security-policies.md) için Standart şablon kullanılarak uygulanır.

Varsayılan olarak, bu ilkelerin kapsamı kuruluştaki tüm kullanıcılara yöneliktir, ancak denemenin kurulumu sırasında veya sonrasında ilke atamasını belirli kullanıcılarla değiştirebilirsiniz.

> [!NOTE]
> Mevcut istenmeyen posta önleme ilkeleriniz, istenmeyen posta önleme ilkelerinde yüksek güvenilirlikli istenmeyen posta kararı için **iletiyi Gereksiz E-posta klasörüne taşı** eylemiyle yapılandırılmış olabilir. Önceden ayarlanmış güvenlik ilkeleri için Standart şablon, yüksek güvenilirlikli istenmeyen postalar için **Karantina iletisi eylemini** kullanır ve önceden ayarlanmış güvenlik ilkeleri her zaman özel istenmeyen posta önleme ilkeleri veya varsayılan istenmeyen posta önleme ilkesinden önce uygulanır. Varsayılan, Standart ve Katı ayarlar hakkında daha fazla bilgi için bkz. [EOP ve Office 365 için Microsoft Defender güvenliği için önerilen ayarlar](recommended-settings-for-eop-and-office365.md).

Diğer iş yükleri de koruma için kullanılabilir (örneğin, [SharePoint, OneDrive ve Microsoft Teams için Güvenli Ekler](mdo-for-spo-odb-and-teams.md) ve [desteklenen Office 365 uygulamaları için Güvenli Bağlantılar](safe-links.md#safe-links-settings-for-office-365-apps)).

Deneme sürümünün kurulumu sırasında, Office 365 için Defender Plan 2'ye özel yanıt işlevselliği (örneğin, [AIR](office-365-air.md) ve [Tehdit Gezgini](threat-explorer.md) de kuruluşun tamamı için ayarlanır. İlke kapsamını belirlemeye gerek yoktur.

## <a name="licensing"></a>Lisanslama

Deneme kurulumu kapsamında Office 365 için Defender lisansları kuruluşa otomatik olarak uygulanır. Lisanslar ilk 90 gün boyunca ücretsizdir.

Deneme sürümü için lisans kartı aşağıdaki bilgileri gösterir:

:::image type="content" source="../../media/mdo-trial-licensing-card.png" alt-text="Office 365 için Microsoft Defender deneme sürümünde lisans kartı" lightbox="../../media/mdo-trial-licensing-card.png":::

- **Kullanım türü** bölümü:
  - **Deneme**: Kullanabileceğiniz deneme Office 365 için Defender lisanslarının sayısı.

    > [!NOTE]
    > Diğer konumlarda, kullanılabilir deneme lisanslarınızın sayısı için 300 değerini görebilirsiniz. Bu değer yanlıştır (kuruluşunuzun tam olarak 300 kullanıcısı olmadığı sürece). Kullanabileceğiniz deneme lisansı sayısı, rastgele 300 değerine değil kuruluşunuzun boyutuna karşılık gelir.

  - **Ücretli**: Ücretli Office 365 için Defender lisanslarının sayısı (varsa).

- **Kullanım** bölümü: Kullanıcılarınızın kaçı Office 365 için Defender ilkeleri kapsamındadır.
  - **Yalnızca algılama & yanıtı**: Aşağıdaki senaryolara dahil edilen toplam kullanıcı sayısı:
    - Deneme süresince ilkelerin kapsamını belirli kullanıcılara belirttiniz.
    - Kapsamı belirli kullanıcılara göre belirlenmiş özel ilkeleriniz vardır.
  - **Tam koruma**: Office 365 için Defender Plan 2 özellikleri (AIR, Tehdit Gezgini, Saldırı simülasyonu eğitimi vb.) tarafından korunan toplam kullanıcı sayısı.

Fiyatlandırma bilgileri için bkz. [Office 365 için Microsoft Defender](https://www.microsoft.com/security/business/siem-and-xdr/microsoft-defender-office-365).

## <a name="permissions"></a>İzinler

Denemeyi başlatmak veya sonlandırmak için Azure Active Directory'de **Genel Yönetici** veya **Güvenlik Yöneticisi** rollerinin üyesi olmanız gerekir. Ayrıntılar için bkz. [Yönetici rolleri hakkında](../../admin/add-users/about-admin-roles.md).

## <a name="additional-information"></a>Ek bilgiler

Deneme sürümünü başlattıktan sonra değişikliklerin ve güncelleştirmelerin kullanılabilir olması 2 saat kadar sürebilir. Ayrıca yöneticilerin değişiklikleri görmek için oturumu kapatıp yeniden oturum açması gerekir.

## <a name="availability"></a>Kullanılabilirlik

Office 365 için Defender deneme sürümü, belirli ölçütleri karşılayan ve mevcut Office 365 için Defender Plan 2 lisansları olmayan (aboneliklerine veya eklenti olarak dahil) mevcut müşterilere aşamalı olarak sunulur.

## <a name="terms-and-conditions"></a>Hüküm ve koşullar

Daha fazla bilgi için bkz[. Office 365 için Microsoft Defender Deneme Koşulları & Koşulları](defender-for-office-365-trial-terms-and-conditions.md).

## <a name="frequently-asked-questions"></a>Sık sorulan sorular

### <a name="q-how-do-i-extend-the-trial"></a>S: Deneme süresini uzatmak Nasıl yaparım??

Y: Bkz. [Deneme sürenizi uzatma](/microsoft-365/commerce/try-or-buy-microsoft-365#extend-your-trial).

### <a name="q-what-happens-to-my-data-after-the-trial-expires"></a>S: Deneme süresi dolduktan sonra verilerime ne olur?

Y: Deneme süreniz dolduktan sonra, deneme verilerinize (daha önce sahip olmadığınız Office 365 için Defender özelliklerden gelen veriler) 30 gün boyunca erişebilirsiniz. Bu 30 günlük süreden sonra, Office 365 için Defender deneme sürümüyle ilişkili tüm ilkeler ve veriler silinir.

### <a name="q-how-many-times-can-i-use-the-defender-for-office-365-trial-in-my-organization"></a>S: Kuruluşumda Office 365 için Defender deneme sürümünü kaç kez kullanabilirim?

Y: En fazla 2 kez. İlk deneme süreniz dolarsa, Office 365 için Defender deneme sürümüne yeniden kaydolmak için son kullanma tarihinden sonra en az 30 gün beklemeniz gerekir. İkinci denemenizden sonra başka bir deneme sürümüne kaydolamazsınız.

## <a name="learn-more-about-defender-for-office-365"></a>Office 365 için Defender hakkında daha fazla bilgi edinin

Office 365 için Defender, kuruluşların kapsamlı bir yetenekler sunarak kuruluşlarının güvenliğini sağlamalarına yardımcı olur.

Ayrıca bu [etkileşimli kılavuzda](https://aka.ms/MS365D.InteractiveGuide) Office 365 için Defender hakkında daha fazla bilgi edinebilirsiniz.

:::image type="content" source="../../media/microsoft-defender-for-office-365.png" alt-text="Office 365 için Microsoft Defender kavramsal diyagramı" lightbox="../../media/microsoft-defender-for-office-365.png":::

### <a name="prevention"></a>Önleme

Sağlam bir filtreleme yığını, iş e-posta güvenliğinin aşılması, kimlik bilgisi kimlik avı, fidye yazılımı ve gelişmiş kötü amaçlı yazılım gibi çok çeşitli birim tabanlı ve hedefli saldırıları önler.

- [Kimlik avı önleme ilkeleri: Office 365 için Defender'de özel kullanım ayarları](set-up-anti-phishing-policies.md#exclusive-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365)
- [Güvenli Ekleri Kaydetme](safe-attachments.md)
- [Güvenli Bağlantılar](safe-links.md)

### <a name="detection"></a>Algılama

Sektör lideri yapay zeka kötü amaçlı ve şüpheli içerikleri algılar ve korumayı azaltmak için tasarlanmış kampanyaları belirlemek için saldırı düzenlerini ilişkilendirir.

- [Office 365 için Microsoft Defender'da Saldırı Kampanyası Görünümleri](campaigns.md)

### <a name="investigation-and-hunting"></a>Araştırma ve avcılık

Güçlü deneyimler, Office 365 genelinde saldırıları izlemek için gelişmiş tehdit avcılığı özellikleriyle tehditleri belirlemeye, önceliklendirmeye ve araştırmaya yardımcı olur.

- [Tehdit Gezgini ve Gerçek zamanlı algılamalar](threat-explorer.md)
- [Office 365 için Defender'da gerçek zamanlı raporlar](view-reports-for-mdo.md)
- [Tehdit İzleyicileri - Yeni ve Dikkat Çekici](threat-trackers.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md) ile tümleştirme

### <a name="response-and-remediation"></a>Yanıt ve düzeltme

Kapsamlı olay yanıtı ve otomasyon özellikleri, güvenlik ekibinizin etkinliğini ve verimliliğini artırır.

- [Office 365 için Microsoft Defender'de otomatik araştırma ve yanıt (AIR)](office-365-air.md)

### <a name="awareness-and-training"></a>Farkındalık ve eğitim

İstemci uygulamalarındaki tümleşik deneyimlerle birlikte zengin simülasyon ve eğitim özellikleri, kullanıcı farkındalığı oluşturur.

- [Saldırı simülasyonu eğitimini kullanmaya başlama](attack-simulation-training-get-started.md)

### <a name="security-posture"></a>Güvenlik duruşu

Önerilen şablonlar ve yapılandırma içgörüleri, müşterilerin güvenliğini sağlamalarına ve güvende kalmalarına yardımcı olur.

- [EOP ve Office 365 için Microsoft Defender'da önceden ayarlanmış güvenlik ilkeleri](preset-security-policies.md)
- [EOP ve Office 365 için Microsoft Defender koruma ilkeleri için yapılandırma çözümleyicisi](configuration-analyzer-for-security-policies.md).

## <a name="give-feedback"></a>Geri bildirimde bulunmak

Geri bildiriminiz, ortamınızı gelişmiş saldırılara karşı koruma konusunda daha iyi olmamıza yardımcı olur. Ürün özellikleri ve deneme sonuçlarıyla ilgili deneyiminizi ve izlenimlerinizi paylaşın.
