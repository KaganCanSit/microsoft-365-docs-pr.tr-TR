---
title: Adım 1. İlk olayınızı önceliklendirme ve analiz etme
description: Microsoft 365 Defender'deki ilk olayınızın analizini önceliklendirme ve analize başlama.
keywords: olaylar, uyarılar, araştırma, bağıntı, saldırı, makineler, cihazlar, kullanıcılar, kimlikler, kimlik, posta kutusu, e-posta, 365, Microsoft, m365, olay yanıtı, siber saldırı
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
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
ms.openlocfilehash: c58bc4eb30c819ae0cbc1654173e8d9dc4ecb7a7
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2022
ms.locfileid: "64664930"
---
# <a name="step-1-triage-and-analyze-your-first-incident"></a>Adım 1. İlk olayınızı önceliklendirme ve analiz etme

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Şunlar için geçerlidir:**
- Microsoft 365 Defender

Kuruluşun standartlarına göre güvenlik önlemleri oluşturmak, uygulamak ve korumak için biraz zaman harcarken, güvenlik risklerini ve tehditlerini hızla belirlemenize yardımcı olacak güvenlik çözümleri ayarlayabilirsiniz. Microsoft 365 Defender, zamanında karar almak için ihtiyacınız olan bilgileri bulabileceğiniz tek bölmeli deneyimiyle olayları algılamanıza, önceliklendirmenize ve araştırmanıza olanak tanır.

Güvenlik olayı algılandığında, Microsoft 365 Defender bir olayı veya olayları diğerlerine göre önceliklendirmeniz veya önceliklendirmeniz gereken ayrıntıları sunar. Analistler öncelik belirlemeyi belirledikten sonra enerjilerini kendilerine atanan vakaları araştırmaya odaklayabilir.

## <a name="detection-by-microsoft-365-defender"></a>Microsoft 365 Defender göre algılama

Microsoft 365 Defender, tümsel bir resim ve kötü amaçlı etkinlik bağlamı oluşturmak için algılama kaynakları olarak birden çok Microsoft güvenlik platformundan uyarılar ve olaylar alır. Olası algılama kaynakları şunlardır:

- [Uç Nokta için Microsoft Defender](../defender-endpoint/microsoft-defender-endpoint.md), Microsoft Defender virüsten koruma ve Microsoft Security Graph kullanarak bulut özellikli gelişmiş tehdit koruması kullanan bir uç noktada algılama ve yanıtlama çözümüdür (EDR). Uç Nokta için Defender, önleyici koruma, ihlal sonrası algılama, otomatik araştırma ve yanıt için birleşik bir platformdur. Uç noktaları siber tehditlere karşı korur, gelişmiş saldırıları ve veri ihlallerini algılar, güvenlik olaylarını otomatikleştirir ve güvenlik duruşunu geliştirir.
- [Kimlik için Microsoft Defender](/defender-for-identity/what-is), şirket içi Active Directory Etki Alanı Hizmetleri (AD DS) sinyallerinizi kullanarak gelişmiş tehditleri, güvenliği aşılmış kimlikleri ve kuruluşunuza yönelik kötü amaçlı insider eylemlerini tanımlamak, algılamak ve araştırmak için kullanılan bulut tabanlı bir güvenlik çözümüdür.
- [Microsoft Defender for Cloud Apps](/cloud-app-security/), kullanıcılarınızın bulunduğu her yerde ve kullandıkları cihazdan bağımsız olarak, kurumsal kullanıcılarınız ve kullandıkları bulut kaynakları arasında gerçek zamanlı olarak erişime aracılık etmek için bir ağ geçidi denetleyicisi görevi görür.
- [Office 365 için Microsoft Defender](../office-365-security/overview.md), kuruluşunuzu e-posta iletileri, bağlantılar (URL'ler) ve işbirliği araçlarındaki kötü amaçlı tehditlere karşı korur.
- [Azure Güvenlik Merkezi](/azure/security-center/security-center-introduction), veri merkezlerinizin güvenlik duruşunu güçlendiren ve buluttaki ve şirket içindeki hibrit iş yükleriniz genelinde gelişmiş tehdit koruması sağlayan birleşik bir altyapı güvenlik yönetim sistemidir.


Microsoft 365 Defender'de olaylar, bu [](incidents-overview.md) farklı algılama kaynaklarından gelen uyarılar ilişkilendirilerek tanımlanır. Kaynakları bir araya getirmek veya birden çok uyarıyı ilgili olaylara ayırmak yerine, hemen Microsoft 365 Defender olay kuyruğuyla başlayabilirsiniz. Bu yaklaşım, uç noktalar, kimlikler, e-posta ve uygulamalar arasında olayları verimli bir şekilde önceliklendirmenize ve saldırıdan kaynaklanan hasarı azaltmanıza olanak tanır.

## <a name="triage-your-incidents"></a>Olaylarınızı önceliklendirme

Microsoft 365 Defender'de olay yanıtı, kuruluşunuzun önerilen önceliklendirme yöntemini kullanarak olay listesini önceliklendirdiğinizde başlar. Önceliklendirmek, olaylara bir önem veya aciliyet düzeyi atamak anlamına gelir ve bu da araştırılacakları sırayı belirler.

Microsoft 365 Defender hangi olayın önceliğini belirlemeye yönelik yararlı bir örnek kılavuz şu formülle özetlenebilir: *Önem Derecesi + Etki = Öncelik*.

- **Önem derecesi**, Microsoft 365 Defender ve tümleşik güvenlik bileşenleri tarafından belirlenen düzeydir.
- **Etki** kuruluş tarafından belirlenir ve genellikle etkilenen kullanıcıların, cihazların, hizmetlerin (veya bunların birleşiminin) eşik sayısını ve hatta uyarı türünü içerir ancak bunlarla sınırlı değildir.

Analistler daha sonra kuruluş tarafından belirlenen **Öncelik** ölçütlerine göre araştırma başlatır.

Olay öncelik belirlemesi kuruluşa bağlı olarak değişebilir. NIST ayrıca olayın işlevsel ve bilgilendirici etkisinin ve kurtarılabilirliğin dikkate alınmasını önerir.

Önceliklendirmeye bir yaklaşım aşağıda açıklanmıştır:

1. Önceliklendirmeyi başlatmak için [olaylar](incidents-overview.md) sayfasına gidin. Burada kuruluşunuzu etkileyen olayların listesini görebilirsiniz. Varsayılan olarak, bunlar en son olaydan en eski olaya düzenlenir. Buradan, her olay için önem derecesini, kategorisini, etkin uyarı sayısını ve etkilenen varlıkları ve diğer varlıkları gösteren farklı sütunlar da görebilirsiniz. Sütun kümesini özelleştirebilir ve sütun adını seçerek olay kuyruğunun bu sütunlardan bazılarını sıralayabilirsiniz. Olay kuyruğuna gereksinimlerinize göre de filtreleyebilirsiniz. Kullanılabilir filtrelerin tam listesi için bkz. [Olayları önceliklendirme](incident-queue.md#available-filters).

   :::image type="content" source="../../media/first-incident-analyze/first-incident-analyze-queue.png" alt-text="Microsoft 365 güvenlik portalındaki olaylar" lightbox="../../media/first-incident-analyze/first-incident-analyze-queue.png":::

    Bu olay kümesi için önceliklendirme gerçekleştirmenin bir örneği, daha fazla kullanıcıyı ve cihazı etkileyen olayların önceliklerini belirlemektir. Bu örnekte, en fazla sayıda varlığı etkilediği için olay kimliği 6769'a öncelik vekleyebilirsiniz: yedi cihaz, altı kullanıcı ve iki posta kutusu. Ayrıca olay, kimlik tabanlı bir uyarıyı ve olası kimlik bilgisi hırsızlığını gösteren Kimlik için Microsoft Defender uyarıları içeriyor gibi görünür.

   :::image type="content" source="../../media/first-incident-analyze/first-incident-analyze-high-impact.png" alt-text="Microsoft 365 güvenlik portalında yüksek etkili bir olayın örneğini gösteren Olaylar** sayfası" lightbox="../../media/first-incident-analyze/first-incident-analyze-high-impact.png":::

2. Ayrıntıları gözden geçirmek için olay adının yanındaki daireyi seçin. Sağ tarafta, önceliklendirmenize daha fazla yardımcı olabilecek ek bilgiler içeren bir yan bölme görüntülenir.

   :::image type="content" source="../../media/first-incident-analyze/first-incident-analyze-incident-flyout.png" alt-text="Microsoft 365 güvenlik portalında olay tarafı bölmesinin örneğini gösteren Olaylar sayfası" lightbox="../../media/first-incident-analyze/first-incident-analyze-incident-flyout.png":::

   Örneğin, saldırganın olay kategorilerine göre hangi [MITRE ATT&CK](https://attack.mitre.org/) taktiklerini kullandığına bakarak, saldırgan çalınan kimlik bilgilerini kullandığı, komut ve denetim oluşturduğu, yanal hareket gerçekleştirdiği ve bazı verileri dışarı çıkardığı için bu olaya öncelik vekleyebilirsiniz. Bu eylemler, saldırganın ağın derinliklerine indiğini ve muhtemelen gizli bilgileri çaldığını gösteriyor.

   Ayrıca, kuruluşunuz Sıfır Güven çerçevesini uygulamışsa kimlik bilgileri erişimini öncelik belirlemeye değer önemli bir güvenlik ihlali olarak düşünebilirsiniz.

   Yan bölmede aşağı kaydırdığınızda kullanıcılar, cihazlar ve posta kutuları gibi etkilenen belirli varlıkları görürsünüz. Her cihazın maruz kalma düzeyini ve etkilenen posta kutularının sahiplerini de kontrol edebilirsiniz.

   :::image type="content" source="../../media/first-incident-analyze/first-incident-analyze-incident-flyout-details.png" alt-text="Olay tarafı bölmesi ayrıntıları" lightbox="../../media/first-incident-analyze/first-incident-analyze-incident-flyout-details.png":::

3. Yan bölmenin daha aşağısında ilişkili uyarıları bulabilirsiniz. Microsoft 365 Defender, belirtilen uyarıların tek bir olayla bağıntısını zaten gerçekleştirerek saldırıyı düzeltmek için daha iyi zaman ve kaynak harcamanızı sağlar. Uyarılar şüphelidir ve bu nedenle ağ üzerinde bir saldırganın varlığını öneren kötü amaçlı sistem olaylarıdır.

   Bu örnekte 87 ayrı uyarının bir güvenlik olayının parçası olduğu belirlendi. Saldırının nasıl oynandığı hakkında hızlı bir görünüm elde etmek için tüm uyarıları görüntüleyebilirsiniz.

   :::image type="content" source="../../media/first-incident-analyze/first-incident-analyze-incident-flyout-alerts.png" alt-text="Microsoft 365 güvenlik portalındaki bir olay tarafı bölmesindeki uyarılar" lightbox="../../media/first-incident-analyze/first-incident-analyze-incident-flyout-alerts.png":::

## <a name="analyze-your-first-incident"></a>İlk olayınızı analiz etme

Uyarıları çevreleyen bağlamı anlamak da aynı derecede önemlidir. Genellikle bir uyarı tek bir bağımsız olay değildir. Aynı anda gerçekleşmemiş olabilecek oluşturulan işlemler, komutlar ve eylemler zinciri vardır. Bu nedenle, uyarıların bağlamını anlamak için analistin cihaz zaman çizelgelerinde şüpheli varlığın ilk ve son etkinliklerini araması gerekir.

Microsoft 365 Defender kullanarak verileri okumanın ve analiz etmenin birden çok yolu vardır, ancak analistlerin nihai hedefi olaylara mümkün olan en hızlı şekilde yanıt vermektir. Microsoft 365 Defender, sektör lideri [otomatik araştırma ve yanıt](m365d-autoir.md) özelliği aracılığıyla Ortalama [Düzeltme Süresi'ni (MTTR)](https://www.microsoft.com/security/blog/2020/05/04/lessons-learned-microsoft-soc-part-3c/) önemli ölçüde azaltabilir ancak her zaman el ile analiz gerektiren durumlar vardır.

İşte bir örnek:

1. Öncelik belirleme önceliği belirlendikten sonra analist, olay adını seçerek ayrıntılı bir analiz başlatır. Bu sayfada verilerin analize yardımcı olması için sekmelerde görüntülendiği **Olay Özeti** açılır. **Uyarılar** sekmesinin altında uyarı türleri görüntülenir. Analistler ilgili algılama kaynağında detaya gitmek için her uyarıya tıklayabilir.

    :::image type="content" source="../../media/first-incident-analyze/first-incident-analyze-summary-tab.png" alt-text="Bir olayın Özet sekmesi" lightbox="../../media/first-incident-analyze/first-incident-analyze-summary-tab.png":::

    Her algılama kaynağının hangi etki alanını kapsadığı hakkında hızlı bir kılavuz için bu makalenin [Algıla](#detection-by-microsoft-365-defender) bölümünü gözden geçirin.

2. **Uyarılar** sekmesinde, daha ayrıntılı bir araştırma ve analiz gerçekleştirmek için algılama kaynağına dönebilirsiniz. Örneğin, algılama kaynağı olarak Microsoft Defender for Cloud Apps ile Kötü Amaçlı Yazılım Algılama'yı seçmek analisti ilgili uyarı sayfasına götürür.

    :::image type="content" source="../../media/first-incident-analyze/first-incident-analyze-select-alert.png" alt-text="Bir olay uyarısı seçme örneğini gösteren Olaylar sayfası." lightbox="../../media/first-incident-analyze/first-incident-analyze-select-alert.png":::

    :::image type="content" source="../../media/first-incident-analyze/first-incident-analyze-link-to-mcas.png" alt-text="Microsoft Defender for Cloud Apps karşılık gelen bir sayfa" lightbox="../../media/first-incident-analyze/first-incident-analyze-link-to-mcas.png":::

3. Örneğimizi daha fazla araştırmak için sayfanın en altına kaydırarak **etkilenen Kullanıcılar'ı** görüntüleyin. Kötü amaçlı yazılım algılamayı çevreleyen etkinliği ve bağlamı görmek için Annette Hill'in kullanıcı sayfasını seçin.

    :::image type="content" source="../../media/first-incident-analyze/first-incident-analyze-user-page.png" alt-text="Kullanıcı sayfası" lightbox="../../media/first-incident-analyze/first-incident-analyze-user-page.png":::

4. Kullanıcı sayfasında, *TOR ağ IP Adresi uyarısından Riskli Oturum Açma* ile başlayarak olaylar kronolojik olarak listelenir. Bir etkinliğin kuşkululuğu, kuruluşun işini nasıl yürüttüğüne bağlı olsa da, çoğu durumda kullanıcıların kurumsal ortamda anonim olarak web'e göz atmasına olanak tanıyan bir ağ olan Onion Router'ın (TOR) kullanımı, normal çevrimiçi işlemler için oldukça düşük olasılıklı ve gereksiz olarak değerlendirilebilir.

    :::image type="content" source="../../media/first-incident-analyze/first-incident-analyze-user-event-list.png" alt-text="Kullanıcının olaylarının kronolojik listesi" lightbox="../../media/first-incident-analyze/first-incident-analyze-user-event-list.png":::

5. Etkinlik hakkında daha fazla bilgi edinmek için her uyarı seçilebilir. Örneğin, **Bir Tor IP Adresi uyarısından Etkinlik'i** seçtiğinizde bu uyarının kendi sayfasına gidersiniz. Annette, yükseltilmiş ayrıcalıkları ve kaynak olayın gizli bilgilere erişmeye yol açmış olabileceğini belirten bir Office 365 Yöneticisidir.

    :::image type="content" source="../../media/first-incident-analyze/first-incident-analyze-mcas-alert.png" alt-text="Microsoft Defender for Cloud Apps için uyarı ayrıntıları" lightbox="../../media/first-incident-analyze/first-incident-analyze-mcas-alert.png" :::

6. Diğer uyarıları seçerek saldırının tam bir resmini alabilirsiniz.

## <a name="next-step"></a>Sonraki adım

:::image type="content" source="../../media/first-incident-overview/first-incident-path-step2.png" alt-text="İlk olayınıza yanıt verme sayfasındaki Düzelt seçeneği" lightbox="../../media/first-incident-overview/first-incident-path-step2.png":::

[Olayları](first-incident-remediate.md) düzeltmeyi öğrenin.

## <a name="see-also"></a>Ayrıca bkz.

- [Olaylara genel bakış](incidents-overview.md)
- [Olayları araştırın](investigate-incidents.md)
- [Olayları yönetin](manage-incidents.md)
