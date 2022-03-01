---
title: Adım 1. İlk olayınızı önceliklendirin ve çözümlenin
description: Olayda ilk olayınızı önce değerlendirme ve çözümlemeye Microsoft 365 Defender.
keywords: olaylar, uyarılar, araştırma, korelasyon, saldırı, makineler, cihazlar, kullanıcılar, kimlikler, kimlik, posta kutusu, e-posta, 365, microsoft, m365, olay yanıtı, siber saldırı
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: josephd
author: JoeDavies-MSFT
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.openlocfilehash: 3854c8891f1cc5175c87b9842d9c30b3164a6f46
ms.sourcegitcommit: bb493f12701f6d6ee7d5e64b541adb87470bc7bc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/18/2022
ms.locfileid: "63015509"
---
# <a name="step-1-triage-and-analyze-your-first-incident"></a>Adım 1. İlk olayınızı önceliklendirin ve çözümlenin

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- Microsoft 365 Defender

Kuruluşun standartlarına göre güvenlik önlemleri kurmak, uygulamak ve korumak için zaman harcayan siz olun, güvenlik risklerini ve tehditleri hızla tanımlamanıza yardımcı olacak güvenlik çözümleri kurabilirsiniz. Microsoft 365 Defender, zamanında karar vermek için ihtiyacınız olan bilgileri bu tek bölmeli deneyimiyle olayları algılamaya, öncelerine atamaya ve araştırmaya olanak sağlar.

Bir güvenlik olayı algılandığında, Microsoft 365 Defender önceliklerini belirlemeli veya önceliklerini belirlemeli ayrıntılı bilgi sunar. Önceliklendirmeyi belirleydikten sonra, analistler enerjilerini onlara atanan vakaları araştırmaya odaklar.

## <a name="detection-by-microsoft-365-defender"></a>Algılama: Microsoft 365 Defender

Microsoft 365 Defender, kötü amaçlı etkinliğin tümc bir resmini ve bağlamını oluşturmak için algılama kaynağı olarak birden çok Microsoft güvenlik platformlarından uyarı ve olay alır. Olası algılama kaynakları bunlardır:

- [Uç Nokta için Microsoft Defender](../defender-endpoint/microsoft-defender-endpoint.md), Microsoft Defender uç noktada algılama ve yanıtlama EDR virüsten koruma ve Microsoft Security Graph kullanarak bulut özellikli gelişmiş tehdit koruması kullanan bir Graph. Uç Nokta için Defender, koruma, ihlal sonrası algılama, otomatik soruşturma ve yanıt için birleşik bir platformdur. Uç noktaları siber tehditlerden korur, gelişmiş saldırılar ve veri ihlallerini algılar, güvenlik olaylarını otomatik haleler ve güvenlik posturesını iyiler.
- [Identity için Microsoft Defender](/defender-for-identity/what-is) , şirket içi Active Directory Etki Alanı Hizmetleri'nizi (AD DS) kullanarak gelişmiş tehditleri, güvenliği tehlikeye atılmış kimlikleri ve kuruluşa yönlendirilen kötü amaçlı insider eylemlerini belirlemek, algılamak ve araştırmak üzere sinyaller kullanan bulut tabanlı bir güvenlik çözümüdür.
- [Bulut Uygulamaları için Microsoft Defender](/cloud-app-security/) , kurumsal kullanıcılarınız ve onların kullanmakta olduğu bulut kaynakları arasında, kullanıcılarınızı nerede bulunursa kullansın, araca gerçek zamanlı olarak erişim için kapı bekçisi gibi davranır.
- [Microsoft Defender For Office 365](../office-365-security/overview.md), e-posta iletisinde, bağlantılarda (URL'ler) ve işbirliği araçlarında kötü amaçlı tehditlere karşı kuruluşu korur.
- [Azure Güvenlik Merkezi](/azure/security-center/security-center-introduction) , veri merkezlerinizin güvenlik yönetimini güçlendiren ve buluttaki ve şirket içi karma iş yükleriniz arasında gelişmiş tehdit koruması sağlayan birleşik bir altyapı güvenlik yönetim sistemidir.


Daha Microsoft 365 Defender[, olaylar](incidents-overview.md) bu farklı algılama kaynaklarından alınan birbiriyle ilişkili uyarılar tarafından tanımlanır. Kaynakları bir araya geçirmek veya birden çok uyarıyı ilgili olaylarda ayırt etmek yerine, hemen bir araya Microsoft 365 Defender sıraya başlayabilirsiniz. Bu sayede uç noktalar, kimlikler, e-posta ve uygulamalar genelinde olayları verimli bir şekilde öncelik durumuna getirir ve saldırıdan zararları azaltabilirsiniz.

## <a name="triage-your-incidents"></a>Olaylarınızı önceliklerini düzeltin

Olay müdahalesi Microsoft 365 Defender in önerilen öncelik belirleme yöntemini kullanarak olay listesini önceliklendirdiğiniz zaman başlar. Triyanak, olaylara önem veya aciliyet düzeyi atamak anlamına gelir ve bundan sonra hangi sırayla inceleneceklerini belirler.

Önem Derecesi + Etki = Öncelik formülüyle Microsoft 365 Defender hangi olayın önceliklendirmesi olduğunu belirlemek için yararlı bir *örnek kılavuz*.

- **Önem derecesi**, güvenlik bileşenleri ve Microsoft 365 Defender bileşenleri tarafından belirlenen düzeydir.
- **Etkisi** kuruluş tarafından belirlenir ve genel olarak bununla sınırlı değildir; etkilenen kullanıcıların, cihazların, hizmetlerin bir eşik sayısını (veya bunun bir bileşimini) ve hatta uyarı türünü içerir.

Ardından analistler, kuruluş tarafından ayarlanmış Öncelik **ölçütlerine** göre incelemeler başlatılır.

Olay önceliklendirme, kuruluşa bağlı olarak değişiklik gösterebilir. NIST, olayın işlevsel ve bilgilendirme amaçlı etkisini ve kurtarılabilirliği de dikkate alarak öneride bulundu.

Aşağıda, dikkate alı bir önceleme yaklaşımının tek bir yaklaşımı vardır:

1. Öncelik [durumu başlatmak](incidents-overview.md) için olaylar sayfasına gidin. Burada, kurumlarınızı etkileyen olayları listeleyebileceksiniz. Varsayılan olarak, en yakın olaydan en eski olaya doğru düzenlenmiştir. Buradan, her olayın önem derecesini, kategorisini, etkin uyarı sayısını ve diğer varlıkları gösteren farklı sütunlar da görebilirsiniz. Sütun kümelerini özelleştirilebilir ve sütun adını seçerek olay kuyruğuna göre bu sütunlardan bazılarında sıralayabilirsiniz. Ayrıca, olay kuyruğuna kendi ihtiyaçlarına göre filtre de ebilirsiniz. Kullanılabilir filtrelerin tam listesi için bkz. [Olayları önceliklendirme](incident-queue.md#available-filters).

   :::image type="content" source="../../media/first-incident-analyze/first-incident-analyze-queue.png" alt-text="Olay sırası örneği.":::

    Bu olay kümesi için önceliklendirme uygulamanın bir örneği, daha fazla kullanıcı ve cihazı etkilenen olayları önceliklendirmektir. Bu örnekte, 6769 numaralı olayı önceliklendirmeniz gerekir çünkü en fazla varlık sayısını etkilemektedir: 7 cihaz, 6 kullanıcı ve 2 posta kutusu. Ayrıca, olay kimlik tabanlı bir uyarıyı ve olası kimlik bilgilerini hırsızlığı gösteren Kimlik için Microsoft Defender'dan gelen uyarıları içeriyor gibi görünüyor.

   :::image type="content" source="../../media/first-incident-analyze/first-incident-analyze-high-impact.png" alt-text="Çok etkili bir olay örneği.":::

2. Ayrıntıları gözden geçirmek için olay adının yanındaki daireyi seçin. Sağ tarafta, üç ayını daha fazla yardımcı olacak ek bilgiler içeren bir yan bölme görüntülenir.

   :::image type="content" source="../../media/first-incident-analyze/first-incident-analyze-incident-flyout.png" alt-text="Olay yan bölmesi örneği.":::

   Örneğin, saldırganin kullandığı [MİTRE ATT&CK'de](https://attack.mitre.org/) olayın kategorilerine göre kullanılan saldırgan taktiklerine bakarak, saldırgan çalınmış kimlik bilgilerini kullandığı, komut ve denetim kurduğu, eşkenar hareketi gerçekleştirilen ve bazı verileri içeri aktardığı için bu olayı önceliklendirmeye karar ve atabilirsiniz. Bu, saldırganin zaten ağın derinlerine gittiğini ve gizli bilgileri çalınmış olduğunu gösteriyor.

   Buna ek olarak, organizasyonunız Sıfır Güven çerçevesi uygulamamışsa, kimlik bilgileri erişimini öncelik belirlemeye değecek önemli bir güvenlik ihlali olarak düşünebileceksiniz.

   Yan bölmeyi aşağı kaydırarak, etkiyi etkileyen varlıkları (kullanıcılar, cihazlar ve posta kutuları gibi) görebilirsiniz. Her cihazın ve etkilenen posta kutularının sahiplerinin etkilenme düzeyini kontrol edebilirsiniz.

   :::image type="content" source="../../media/first-incident-analyze/first-incident-analyze-incident-flyout-details.png" alt-text="Olay yan bölmesi ayrıntıları örneği.":::

3. Yan bölmenin daha aşağı doğru ilişkilendirilmiş uyarılarını bulabilirsiniz. Microsoft 365 Defender, bu uyarıların tek bir olayla bağıntısını zaten gerçekleştirerek saldırıyı düzeltmeye zaman ve kaynak tasarrufu sağlar. Uyarılar şüphelidir ve dolayısıyla muhtemelen bir ağ üzerinde bir saldırgan varlığını öneren kötü amaçlı sistem olaylarıdır.

   Bu örnekte, tek tek 87 uyarının tek bir güvenlik olayına parçası olduğu belirlendi. Saldırının nasıl oynaması olduğunu hızlıca görmek için tüm uyarıları görüntüabilirsiniz.

   :::image type="content" source="../../media/first-incident-analyze/first-incident-analyze-incident-flyout-alerts.png" alt-text="Olay yan bölmesinde uyarı örneği.":::

## <a name="analyze-your-first-incident"></a>İlk olayınızı çözümleme

Uyarıları çevreleyen bağlamı anlamak da aynı derecede önemlidir. Genelde uyarı tek bir bağımsız etkinlik değildir. Aynı anda oluşturulmuş, komutlar ve eylemler zinciri vardır. Bu nedenle, uyarıların bağlamını anlamak için şüpheli varlığın ilk ve son etkinliklerini cihaz zaman çizelgeleri içinde aramanız gerekir.

Verileri okumanın ve çözümlemenin birden çok yolu vardır Microsoft 365 Defender ancak analistlerin son hedefi olayları mümkün olan en hızlı şekilde yanıtlamaktır. Bu Microsoft 365 Defender sektör lideri otomatik araştırma ve yanıt özelliği aracılığıyla Ortalama Düzeltme Zamanı'nda [(MTTR)](https://www.microsoft.com/security/blog/2020/05/04/lessons-learned-microsoft-soc-part-3c/) önemli ölçüde azalma slaslasa da, her zaman el ile çözümleme gerektiren durumlar vardır.[](m365d-autoir.md)

İşte bir örnek:

1. Öncelik öncelik belirlendiktan sonra, olayın adını seçerek ayrıntılı bir çözümleme başlatarak başlayabilirsiniz. Bu sayfada, çözümlemeye **yardımcı olmak için verilerin** sekmelerde görüntülendiğinde Olay Özeti görüntülenir. Uyarılar **sekmesinin** altında uyarı türü görüntülenir. Analistler her uyarıya tıklar ve ilgili algılama kaynağının ayrıntıya iner.

    :::image type="content" source="../../media/first-incident-analyze/first-incident-analyze-summary-tab.png" alt-text="Olayın Özet sekmesi örneği.":::

    Her algılama kaynağının hangi etki alanını kapsa hakkında hızlı bir kılavuz için, bu [makalenin](#detection-by-microsoft-365-defender) Algıla bölümünü gözden geçirebilirsiniz.

2. Daha **ayrıntılı bir** araştırma ve çözümleme yapmak için Uyarılar sekmesinde özet olarak algılama kaynağına dönebilirsiniz. Örneğin algılama kaynağı olarak Bulut Uygulamaları için Microsoft Defender ile Kötü Amaçlı Yazılım Algılaması'nın seçlanması, analisti buna karşılık gelen uyarı sayfasına alır.

    :::image type="content" source="../../media/first-incident-analyze/first-incident-analyze-select-alert.png" alt-text="Olay uyarısı seçme örneği.":::

    :::image type="content" source="../../media/first-incident-analyze/first-incident-analyze-link-to-mcas.png" alt-text="Bulut Uygulamaları için Microsoft Defender'da ilgili sayfa örneği.":::

3. Örneğimizi daha fazla araştırmak için sayfanın en altına kaydırarak Etkilenen **kullanıcılar'a bakın**. Kötü amaçlı yazılım algılamayı çevreleyen etkinliği ve bağlamı görmek için Annette Hill'in kullanıcı sayfasını seçin.

    :::image type="content" source="../../media/first-incident-analyze/first-incident-analyze-user-page.png" alt-text="Kullanıcı sayfası örneği.":::

4. Kullanıcı sayfasında, TOR ağı IP Adresi uyarından gelen Riskli Oturum Açma ile başlayan olayların *kronolojik bir listesi* vardır. Bir etkinliğin şüpheliliği, kuruluşun işlerini nasıl yürüttüklerine bağlı olarak, çoğu durumda kullanıcıların kurumsal bir ortamda anonim olarak Web'de gezinmelerine olanak sağlayan bir ağ olan Onion Yönlendirici'nin (TOR) kullanımı pek olası ve gereksiz olabilir.

    :::image type="content" source="../../media/first-incident-analyze/first-incident-analyze-user-event-list.png" alt-text="Kullanıcının olaylarının kronolojik listesi örneği.":::

5. Etkinlikle ilgili daha fazla bilgi almak için her uyarı seçilebilir. Örneğin, **Tor IP Adresi uyarılarından** Etkinlik seçerek bu uyarının kendi sayfasına yol açabilirsiniz. Annette Bir Office 365 Yöneticisidir, yani ayrıcalıkları yükseltilmiştir ve kaynak olayı gizli bilgilere erişime yol etmiş olabilir.

    :::image type="content" source="../../media/first-incident-analyze/first-incident-analyze-mcas-alert.png" alt-text="Bulut Uygulamaları için Microsoft Defender uyarı ayrıntıları örneği.":::

6. Diğer uyarıları seçerek saldırının tam bir resmini çeksiniz.

## <a name="next-step"></a>Sonraki adım

[![2. Adım: Olayları düzeltmeyi öğrenin.](../../media/first-incident-overview/first-incident-path-step2.png)](first-incident-remediate.md)

Olayları [düzeltmeyi öğrenin](first-incident-remediate.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Olaylara genel bakış](incidents-overview.md)
- [Olayları araştırma](investigate-incidents.md)
- [Olayları yönetme](manage-incidents.md)
