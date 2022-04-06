---
title: Office 365 için Microsoft Defender playbook'larını deneme
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: Admin
ms.topic: conceptual
ms.collection: m365-security-compliance
ms.localizationpriority: high
ROBOTS: NOINDEX, NOFOLLOW
ms.prod: m365-security
search.appverid:
- MOE150
- MET150
description: Office 365 için Microsoft Defender deneme sürümü oynatma kitabı.
ms.openlocfilehash: 1e943cc36d7a8787a41e16d61b15fe9e2eea129c
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64474893"
---
# <a name="trial-playbook-microsoft-defender-for-office-365"></a>Deneme playbook'ları: Office 365 için Microsoft Defender

Office 365 için Microsoft Defender deneme sürümüne hoş geldiniz. Bu çalışma kitabı, her bir çalışma kitabıyla organizasyonlarınızı nasıl koruyacaklarını öğreterek 90 günlük ücretsiz denemenizi en iyi şekilde Office 365 için Defender. Microsoft önerilerini kullanarak, güvenlik ilkelerini tanımlamanıza Office 365 için Defender organizasyona yönelik tehditleri çözümlemenize ve saldırılara yanıt vermenize nasıl yardımcı olduğunu öğrenirsiniz.

:::image type="content" source="../../media/mdo-trial-playbook-what-is-mdo.png" alt-text="Veri bileşenlerinin tüm bileşenlerinin grafik Office 365 için Microsoft Defender" lightbox="../../media/mdo-trial-playbook-what-is-mdo.png":::

Bu eylemler, 90 günlük denemeniz boyunca deneyecek önemli özelliklerle ilgili Microsoft Defender ekibinin önerileridir.

## <a name="step-1-getting-started"></a>1. Adım: Başlarken

### <a name="start-your-microsoft-defender-for-office-365-trial"></a>Office 365 için Microsoft Defender denemenizi başlatma

Denemeyi başlattıktan ve kurulum işlemini tamamlandıktan sonra, değişikliklerin yürürlüğe girdikten sonra 2 saat kadar sürebilir.

Ortamınıza Önceden belirlenmiş güvenlik [ilkelerini otomatik](preset-security-policies.md) olarak yapılandırıldı. Bu ilkeler, çoğu kullanıcı için uygun olan bir taban çizgisi koruma profilini temsil ediyor. Standart koruma şunları içerir:

- Kasa kurulum Kasa kiracının tamamı veya kullanıcı alt kümesi kapsamındaki Ekleri ve Kimlik Avını Önleme ilkelerini içerir.
- Uygulama, SharePoint, OneDrive Office ve güvenlik koruması Microsoft Teams.

Daha fazla bilgi edinmek için bu videoyu izleyin: [Yeni - YouTube'daki Kasa bağlantılar ile Office 365 için Microsoft Defender bağlantılara karşı koruma.](https://www.youtube.com/watch?v=vhIJ1Veq36Y&list=PL3ZTgFEc7LystRja2GnDeUFqk44k7-KXf&index=9)

### <a name="enable-users-to-report-suspicious-content"></a>Kullanıcıların şüpheli içeriği bildirmelerini etkinleştirme

Office 365 için Defender, kullanıcıların iletileri güvenlik ekiplerine bildirmesini ve yöneticilerin çözümleme için Microsoft'a ileti göndermesini sağlar.

- Rapor [İletisi eklentisini veya Rapor Kimlik Avı eklentisini dağıtın](enable-the-report-message-add-in.md).
- Hatalı pozitif ve yanlış [negatifleri rapor etmek için iş akışı oluşturma](report-false-positives-and-false-negatives.md).
- Gönderiler [portalını kullanın](admin-submission.md).

Daha fazla bilgi edinmek için bu videoyu izleyin: Analiz için ileti göndermek üzere [Gönderiler portalını kullanmayı öğrenin - YouTube](https://www.youtube.com/watch?v=ta5S09Yz6Ks&ab_channel=MicrosoftSecurit).

### <a name="review-reports-to-understand-the-threat-landscape"></a>Tehdit ortamını anlamak için raporları gözden geçirme

Ortamınız hakkında daha fazla Office 365 için Defender için raporlama özelliklerini kullanabilirsiniz.

- Tehdit koruması durumu raporuyla e-postada ve işbirliği [araçlarında alınan tehditleri an edin](view-email-security-reports.md#threat-protection-status-report).
- Posta Akışı durum raporuyla [tehditlerin nerede engellenmiş olduğunu bakın](view-email-security-reports.md#mailflow-status-report).
- [Kullanıcılar tarafından](view-reports-for-mdo.md#url-protection-report) görüntülenen veya sistem tarafından engellenen bağlantıları gözden geçirebilirsiniz.

:::image type="content" source="../../media/mdo-trial-playbook-reporting.png" alt-text="E-& portalında işbirliği Microsoft 365 Defender gönderme" lightbox="../../media/mdo-trial-playbook-reporting.png":::

## <a name="step-2-intermediate-steps"></a>2. Adım: Ara adımlar

### <a name="prioritize-focus-on-your-most-targeted-users"></a>En çok hedefli kullanıcılarınıza odaklanma önceliklerini belirleme

Hedefli ve en görünür kullanıcılarınızı, bu kullanıcıların güvende olduğundan emin olmak için iş akışınızı önceliklendirmenize yardımcı olan Office 365 için Defender'te Öncelik Hesabı Koruması ile koruyun.

- En çok hedefli veya en görünür kullanıcılarınızı belirleme.
- [Bu kullanıcıları öncelik](../../admin/setup/priority-accounts.md#add-priority-accounts-from-the-setup-page) hesapları olarak etiketle.
- Portal genelinde öncelik hesabına yönelik tehditleri takip edin.

Daha fazla bilgi edinmek için bu videoyu izleyin: [Office 365 için Microsoft Defender - YouTube'da öncelik hesaplarını koruma](https://www.youtube.com/watch?v=tqnj0TlzQcI&list=PL3ZTgFEc7LystRja2GnDeUFqk44k7-KXf&index=11).

:::image type="content" source="../../media/mdo-trial-playbook-alerts.png" alt-text="Microsoft 365 Defender portalında Uyarılar" lightbox="../../media/mdo-trial-playbook-alerts.png":::

### <a name="avoid-costly-breaches-by-preventing-user-compromise"></a>Kullanıcıların güvenliğini önleerek yüksek maliyetli ihlallerden kaçınma

Olası tehdit konusunda uyarı alma ve saldırganların ortamınıza daha fazla erişim kazanmasını önlemek için bu tehditlerin etkisini otomatik olarak sınırlandırma.

- Güvenliği [tehlikeye atılmış kullanıcı uyarılarını gözden geçirme](address-compromised-users-quickly.md#compromised-user-alerts).
- [Güvenliği ihlal edilmiş kullanıcıları](address-compromised-users-quickly.md) araştırarak ve yanıtlayın.

:::image type="content" source="../../media/mdo-trial-playbook-investigation.png" alt-text="Güvenliği ihlal edilmiş kullanıcıları araştırma" lightbox="../../media/mdo-trial-playbook-investigation.png":::

Daha fazla bilgi edinmek için bu videoyu izleyin: [YouTube ile güvenlik ödünlerini Office 365 için Microsoft Defender ve yanıt verin](https://www.youtube.com/watch?v=Pc7y3a-wdR0&list=PL3ZTgFEc7LystRja2GnDeUFqk44k7-KXf&index=5).

### <a name="use-threat-explorer-to-investigate-malicious-email"></a>Kötü amaçlı e-postaları araştırmak için Threat Explorer'ı kullanma

Office 365 için Defender, kuruluşta kişilerin risk altında yer almalarını sağlayan etkinlikleri araştırmanıza ve organizasyonlarınızı korumak için harekete çalışmanıza olanak sağlar. Tehdit Gezgini'ni veya [(gerçek zamanlı algılamaları) kullanarak bunuabilirsiniz](threat-explorer.md).

- [Teslim edilen şüpheli e-postaları bulma](investigate-malicious-email-that-was-delivered.md#find-suspicious-email-that-was-delivered): İletileri bulun ve silin, kötü amaçlı e-posta gönderenin IP adresini bulun veya daha fazla araştırma için bir olay başlatabilirsiniz.
- [Teslim eylemlerini ve konumlarını kontrol](investigate-malicious-email-that-was-delivered.md#check-the-delivery-action-and-location) edin: Bu denetim, sorun e-posta iletilerinin konumunu size haber sağlar.
- [E-postanızı zaman çizelgenizi görüntüleme](investigate-malicious-email-that-was-delivered.md#view-the-timeline-of-your-email): Güvenlik işlemleri ekibiniz için kolayca arama yapmanız.

### <a name="see-campaigns-targeting-your-organization"></a>Organizasyonlarınızı hedef alan kampanyalara bakın

Office 365 için Defender'ta Kampanya Görünümleri ile, organizasyonlarınızı hedef alan saldırı kampanyaları ve bu kampanyaların kullanıcılarınız üzerindeki etkisinin görünümünü sunan Kampanya Görünümleri ile daha büyük resme bakın.

- [Kullanıcılarınızı](campaigns.md#what-is-a-campaign) hedef alan kampanyalar tanımlayabilirsiniz.
- [Saldırının kapsamını](campaigns.md#campaign-views-in-the-microsoft-365-defender-portal) görselleştirin.
- [Bu iletilerle kullanıcı](campaigns.md#campaign-details) etkileşimi izleme.

  :::image type="content" source="../../media/mdo-trial-playbook-campaign-details.png" alt-text="Portalda Kampanya Microsoft 365 Defender." lightbox="../../media/mdo-trial-playbook-campaign-details.png":::

Daha fazla bilgi edinmek için bu videoyu izleyin: kampanya [görünümleri Office 365 için Microsoft Defender YouTube](https://www.youtube.com/watch?v=DvqzzYKu7cQ&list=PL3ZTgFEc7LystRja2GnDeUFqk44k7-KXf&index=14).

### <a name="use-automation-to-remediate-risks"></a>Riskleri düzeltmek için otomasyon kullanın

Tehditleri gözden geçirmek, önceliklerini belirlemek ve tehditlere yanıt vermek için Otomatik araştırma ve yanıt (AIR) kullanarak verimli bir şekilde yanıt verin.

- [Araştırma playbooks](automated-investigation-response-office.md) hakkında daha fazla bilgi edinmek için.
- [Araştırmanın ayrıntılarını ve](email-analysis-investigations.md) sonuçlarını görüntüleme.
- Düzeltme [eylemlerini onayarak tehditleri ortadan kaldırabilirsiniz](air-remediation-actions.md).

:::image type="content" source="../../media/mdo-trial-playbook-investigation-results.png" alt-text="İnceleme sonuçları" lightbox="../../media/mdo-trial-playbook-investigation-results.png":::

## <a name="step-3-advanced-content"></a>3. Adım: Gelişmiş içerik

### <a name="dive-deep-into-data-with-query-based-hunting"></a>Sorgu tabanlı dalın ile verilerin derinlerine dalın

Özel algılama kuralları yazmak, ortamınıza önceden olayları incelemek ve tehdit göstergeleri bulmak için Gelişmiş av kullanın. Ortamınıza ham verileri keşfedin.

- [Özel algılama kuralları oluşturma](../defender/advanced-hunting-overview.md#get-started-with-advanced-hunting).
- [Başkaları tarafından oluşturulan paylaşılan](../defender/advanced-hunting-shared-queries.md) sorgulara erişin.

Daha fazla bilgi edinmek için bu videoyu izleyin: Microsoft 365 Defender [- YouTube ile tehdit avı](https://www.youtube.com/watch?v=l3OmH4U6XAs&list=PL3ZTgFEc7Lyt1O81TZol31YXve4e6lyQu&index=4).

### <a name="train-users-to-spot-threats-by-simulating-attacks"></a>Saldırılar ile tehditlerini tespit etmek için kullanıcıları eğitin

Yeni bir yıl içinde Saldırı benzetimi eğitimi ile kullanıcılarınıza tehditleri belirlemeleri ve şüpheli iletileri bildirmeleri için doğru bilgi Office 365 için Defender.

- [Korumasız kullanıcıları tanımlamak](attack-simulation-training.md) için gerçekçi tehditleri taklit edebilir.
- [Benzetim](attack-simulation-training.md#assign-training) sonuçlarına dayalı olarak kullanıcılara eğitim attayabilirsiniz.
- [Benzetimler](attack-simulation-training-insights.md) ve eğitim tamamlamayla kuruluş ilerlemesini takip et.

  :::image type="content" source="../../media/mdo-trial-playbook-attack-simulation-training-results.png" alt-text="Microsoft 365 Defender portalında saldırı benzetimi eğitim öngörüleri" lightbox="../../media/mdo-trial-playbook-attack-simulation-training-results.png":::

## <a name="additional-resources"></a>Ek kaynaklar

- **Etkileşimli kılavuz**: Nasıl olduğunu Office 365 için Defender? Nasıl [başla ilgili olduğunu](https://mslearn.cloudguides.com/guides/Safeguard%20your%20organization%20with%20Microsoft%20Defender%20for%20Office%20365) anlamak için etkileşimli kılavuzu gözden geçirin.
- **Microsoft belgeleri**: Belgelerinizin nasıl çalıştığını ve Office 365 için Defender için en iyi nasıl uygulayacağı hakkında ayrıntılı bilgi edinebilirsiniz. [Belgeler'i ziyaret edin](overview.md).
- **Neler dahildir: Ürün** katmanına göre listelenen Office 365-posta güvenlik özelliklerinin tam listesi için Özellik Matrisi'ne [tıklayın](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description#feature-availability).
- **Neden Office 365 için Defender**: Veri [Office 365 için Defender sayfasında](https://query.prod.cms.rt.microsoft.com/cms/api/am/binary/RE4FCiy) müşterilerin Microsoft'u seçmesi için 10 neden vardır.
