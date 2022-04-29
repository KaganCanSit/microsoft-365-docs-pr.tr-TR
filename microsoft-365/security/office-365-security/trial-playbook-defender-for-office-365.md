---
title: Office 365 için Microsoft Defender deneme playbook'u
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
description: Office 365 için Microsoft Defender çözümleri deneme playbook'u.
ms.openlocfilehash: f23c45d117735997c219278621be7f314602cd8f
ms.sourcegitcommit: fdd0294e6cda916392ee66f5a1d2a235fb7272f8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/29/2022
ms.locfileid: "65130702"
---
# <a name="trial-playbook-microsoft-defender-for-office-365"></a>Deneme playbook'u: Office 365 için Microsoft Defender

Office 365 için Microsoft Defender deneme playbook'una hoş geldiniz. Bu playbook, Office 365 için Defender ile kuruluşunuzu nasıl koruyacağınızı öğreterek 90 günlük ücretsiz denemenizden en iyi şekilde yararlanabilirsiniz. Microsoft önerilerini kullanarak Office 365 için Defender koruma ilkeleri tanımlamanıza, kuruluşunuza yönelik tehditleri analiz etmeye ve saldırılara yanıt vermenize nasıl yardımcı olabileceğini öğreneceksiniz.

:::image type="content" source="../../media/mdo-trial-playbook-what-is-mdo.png" alt-text="Office 365 için Microsoft Defender tüm bileşenlerinin grafik gösterimi." lightbox="../../media/mdo-trial-playbook-what-is-mdo.png":::

Bu eylemler, Microsoft Defender ekibinin 90 günlük denemenizde deneyebileceğiniz temel özelliklerle ilgili önerileridir.

## <a name="step-1-getting-started"></a>1. Adım: Başlarken

### <a name="start-your-microsoft-defender-for-office-365-trial"></a>Office 365 için Microsoft Defender denemenizi başlatın

Denemeyi başlattıktan ve kurulum işlemini tamamladıktan sonra değişikliklerin geçerli olması 2 saat kadar sürebilir.

Ortamınızda [Önceden Ayarlanmış güvenlik ilkelerini](preset-security-policies.md) otomatik olarak yapılandırdık. Bu ilkeler, çoğu kullanıcı için uygun bir temel koruma profilini temsil eder. Standart koruma şunları içerir:

- Kasa Bağlantılar, Kasa Ekler ve kimlik avı önleme ilkeleri, deneme kurulum işlemi sırasında seçmiş olabileceğiniz tüm kiracı veya kullanıcı alt kümesi kapsamındadır.
- Kasa SharePoint, OneDrive ve Microsoft Teams için Ekler koruması.
- Kasa Desteklenen Office 365 uygulamaları için bağlantılar koruması.

Daha fazla bilgi edinmek için bu videoyu izleyin: [Office 365 için Microsoft Defender - YouTube'da Kasa Bağlantıları ile kötü amaçlı bağlantılara karşı koruma](https://www.youtube.com/watch?v=vhIJ1Veq36Y&list=PL3ZTgFEc7LystRja2GnDeUFqk44k7-KXf&index=9).

### <a name="enable-users-to-report-suspicious-content"></a>Kullanıcıların şüpheli içeriği bildirmesini sağlama

Office 365 için Defender, kullanıcıların güvenlik ekiplerine ileti bildirmesine olanak tanır ve yöneticilerin analiz için Microsoft'a ileti göndermesine olanak tanır.

- [Rapor İletisi eklentisini veya Rapor Kimlik Avı eklentisini dağıtın](enable-the-report-message-add-in.md).
- [Hatalı pozitifleri ve hatalı negatifleri raporlamak](report-false-positives-and-false-negatives.md) için bir iş akışı oluşturun.
- [Gönderimler portalını](admin-submission.md) kullanın.

Daha fazla bilgi edinmek için bu videoyu izleyin: [Analiz için ileti göndermek için Gönderimler portalını kullanmayı öğrenin - YouTube](https://www.youtube.com/watch?v=ta5S09Yz6Ks&ab_channel=MicrosoftSecurit).

### <a name="review-reports-to-understand-the-threat-landscape"></a>Tehdit ortamını anlamak için raporları gözden geçirin

Ortamınız hakkında daha fazla bilgi edinmek için Office 365 için Defender'deki raporlama özelliklerini kullanın.

- [Tehdit koruması durum raporuyla](view-email-security-reports.md#threat-protection-status-report) e-posta ve işbirliği araçlarına alınan tehditleri anlayın.
- [Posta akışı durum raporuyla](view-email-security-reports.md#mailflow-status-report) tehditlerin nerede engellendiğini görün.
- Kullanıcılar tarafından görüntülenen veya sistem tarafından engellenen [bağlantıları gözden geçirin](view-reports-for-mdo.md#url-protection-report).

:::image type="content" source="../../media/mdo-trial-playbook-reporting.png" alt-text="e-posta & işbirliği raporları Microsoft 365 Defender portalında." lightbox="../../media/mdo-trial-playbook-reporting.png":::

## <a name="step-2-intermediate-steps"></a>2. Adım: Ara adımlar

### <a name="prioritize-focus-on-your-most-targeted-users"></a>Odağı en çok hedeflenen kullanıcılarınıza önceliklendirme

Office 365 için Defender'da Öncelik Hesabı Koruması ile en çok hedeflenen ve en görünür kullanıcılarınızı koruyun. Bu, bu kullanıcıların güvende olduğundan emin olmak için iş akışınızı önceliklendirmenize yardımcı olur.

- En çok hedeflenen veya en görünür kullanıcılarınızı belirleyin.
- [Bu kullanıcıları](../../admin/setup/priority-accounts.md#add-priority-accounts-from-the-setup-page) öncelik hesapları olarak etiketleyin.
- Portal genelinde öncelik hesabına yönelik tehditleri izleyin.

Daha fazla bilgi edinmek için bu videoyu izleyin: [Office 365 için Microsoft Defender 'de öncelik hesaplarını koruma - YouTube](https://www.youtube.com/watch?v=tqnj0TlzQcI&list=PL3ZTgFEc7LystRja2GnDeUFqk44k7-KXf&index=11).

:::image type="content" source="../../media/mdo-trial-playbook-alerts.png" alt-text="Microsoft 365 Defender portalındaki Uyarılar." lightbox="../../media/mdo-trial-playbook-alerts.png":::

### <a name="avoid-costly-breaches-by-preventing-user-compromise"></a>Kullanıcı güvenliğinin aşılmasını önleyerek yüksek maliyetli ihlallerden kaçının

Olası risklere karşı uyarı alın ve saldırganların ortamınıza daha derin erişim elde etmesini önlemek için bu tehditlerin etkisini otomatik olarak sınırlayın.

- [Güvenliği aşılmış kullanıcı uyarılarını](address-compromised-users-quickly.md#compromised-user-alerts) gözden geçirin.
- Güvenliği aşılmış kullanıcıları [araştırın ve yanıt verin](address-compromised-users-quickly.md).

:::image type="content" source="../../media/mdo-trial-playbook-investigation.png" alt-text="Güvenliği aşılmış kullanıcıları araştırma." lightbox="../../media/mdo-trial-playbook-investigation.png":::

Daha fazla bilgi edinmek için bu videoyu izleyin: [Office 365 için Microsoft Defender - YouTube'da güvenliği aşmayı algılama ve yanıtlama](https://www.youtube.com/watch?v=Pc7y3a-wdR0&list=PL3ZTgFEc7LystRja2GnDeUFqk44k7-KXf&index=5).

### <a name="use-threat-explorer-to-investigate-malicious-email"></a>Kötü amaçlı e-postayı araştırmak için Tehdit Gezgini'ni kullanma

Office 365 için Defender, kuruluşunuzdaki kişileri riske atacak etkinlikleri araştırmanıza ve kuruluşunuzu korumak için eylem gerçekleştirmenize olanak tanır. Bunu [Tehdit Gezgini'ne](threat-explorer.md) kullanarak yapabilirsiniz.

- [Teslim edilen şüpheli e-postayı bulma](investigate-malicious-email-that-was-delivered.md#find-suspicious-email-that-was-delivered): İletileri bulun ve silin, kötü amaçlı e-posta gönderenin IP adresini tanımlayın veya daha fazla araştırma için bir olay başlatın.
- [Teslim eylemini ve konumunu denetleyin](investigate-malicious-email-that-was-delivered.md#check-the-delivery-action-and-location): Bu denetim, sorunlu e-posta iletilerinin konumunu öğrenmenizi sağlar.
- [E-postanızın zaman çizelgesini görüntüleyin](investigate-malicious-email-that-was-delivered.md#view-the-timeline-of-your-email): Yalnızca güvenlik operasyonları ekibiniz için avlanma.

### <a name="see-campaigns-targeting-your-organization"></a>Kuruluşunuzu hedefleyen kampanyaları görme

Kuruluşunuzu hedef alan saldırı kampanyalarının ve bunların kullanıcılarınız üzerindeki etkisinin bir görünümünü sunan Office 365 için Defender'de Kampanya Görünümleri ile daha büyük resme bakın.

- Kullanıcılarınızı hedefleyen [kampanyaları belirleyin](campaigns.md#what-is-a-campaign).
- [Saldırının kapsamını görselleştirin](campaigns.md#campaign-views-in-the-microsoft-365-defender-portal) .
- Bu iletilerle [kullanıcı etkileşimlerini izleyin](campaigns.md#campaign-details).

  :::image type="content" source="../../media/mdo-trial-playbook-campaign-details.png" alt-text="Microsoft 365 Defender portalındaki Kampanya ayrıntıları." lightbox="../../media/mdo-trial-playbook-campaign-details.png":::

Daha fazla bilgi edinmek için bu videoyu izleyin: [Office 365 için Microsoft Defender Kampanya Görünümleri - YouTube](https://www.youtube.com/watch?v=DvqzzYKu7cQ&list=PL3ZTgFEc7LystRja2GnDeUFqk44k7-KXf&index=14).

### <a name="use-automation-to-remediate-risks"></a>Riskleri düzeltmek için otomasyonu kullanma

Tehditleri gözden geçirmek, önceliklendirmek ve yanıtlamak için Otomatik araştırma ve yanıt (AIR) kullanarak verimli bir şekilde yanıt verin.

- Araştırma playbook'ları hakkında [daha fazla bilgi edinin](automated-investigation-response-office.md).
- [Araştırmanın ayrıntılarını ve sonuçlarını görüntüleyin](email-analysis-investigations.md) .
- [Düzeltme eylemlerini onaylayarak](air-remediation-actions.md) tehditleri ortadan kaldırın.

:::image type="content" source="../../media/mdo-trial-playbook-investigation-results.png" alt-text="Araştırma sonuçları." lightbox="../../media/mdo-trial-playbook-investigation-results.png":::

## <a name="step-3-advanced-content"></a>3. Adım: Gelişmiş içerik

### <a name="dive-deep-into-data-with-query-based-hunting"></a>Sorgu tabanlı avcılık ile verileri derinlemesine inceleme

Özel algılama kuralları yazmak, ortamınızdaki olayları proaktif olarak incelemek ve tehdit göstergelerini bulmak için Gelişmiş tehdit avcılığı kullanın. Ortamınızdaki ham verileri keşfedin.

- [Özel algılama kuralları oluşturun](../defender/advanced-hunting-overview.md#get-started-with-advanced-hunting).
- Başkaları tarafından oluşturulan [paylaşılan sorgulara erişin](../defender/advanced-hunting-shared-queries.md).

Daha fazla bilgi edinmek için bu videoyu izleyin: [Microsoft 365 Defender ile tehdit avcılığı - YouTube](https://www.youtube.com/watch?v=l3OmH4U6XAs&list=PL3ZTgFEc7Lyt1O81TZol31YXve4e6lyQu&index=4).

### <a name="train-users-to-spot-threats-by-simulating-attacks"></a>Saldırıların benzetimlerini yaparak kullanıcıları tehditleri tespit etmeye eğitin

Office 365 için Defender'daki Saldırı simülasyonu eğitimiyle tehditleri tanımlamak ve şüpheli iletileri bildirmek için kullanıcılarınızı doğru bilgiyle donatın.

- Savunmasız kullanıcıları tanımlamak için [gerçekçi tehditlerin benzetimini](attack-simulation-training.md) yapmak.
- Simülasyon sonuçlarına göre kullanıcılara [eğitim atayın](attack-simulation-training.md#assign-training).
- Simülasyonlar ve eğitim tamamlama aşamasında kuruluşunuzun [ilerleme durumunu izleyin](attack-simulation-training-insights.md).

  :::image type="content" source="../../media/mdo-trial-playbook-attack-simulation-training-results.png" alt-text="Microsoft 365 Defender portalındaki saldırı simülasyonu eğitim içgörüleri." lightbox="../../media/mdo-trial-playbook-attack-simulation-training-results.png":::

## <a name="additional-resources"></a>Ek kaynaklar

- **Etkileşimli kılavuz**: Office 365 için Defender aşina değil misiniz? Nasıl başlayabileceğinizi anlamak için [etkileşimli kılavuzu](https://mslearn.cloudguides.com/guides/Safeguard%20your%20organization%20with%20Microsoft%20Defender%20for%20Office%20365) gözden geçirin.
- **Microsoft belgeleri**: Office 365 için Defender nasıl çalıştığı ve kuruluşunuz için bunu en iyi şekilde nasıl uygulayacakları hakkında ayrıntılı bilgi edinin. [Docs'u](overview.md) ziyaret edin.
- **Dahil olanlar**: Ürün katmanı tarafından listelenen Office 365 e-posta güvenlik özelliklerinin tam listesi için [Özellik Matrisi'ni](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description#feature-availability) görüntüleyin.
- **Neden Office 365 için Defender**: [Office 365 için Defender Veri Sayfası](https://query.prod.cms.rt.microsoft.com/cms/api/am/binary/RE4FCiy), müşterilerin Microsoft'u seçmesinin en önemli 10 nedenini gösterir.
