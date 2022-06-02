---
title: Analizler ve raporlar Saldırı simülasyonu eğitimi
ms.author: chrisda
author: chrisda
manager: dansimp
audience: ITPro
ms.topic: conceptual
ms.prod: m365-security
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
ms.custom: ''
description: Yöneticiler, Microsoft 365 Defender portalında Saldırı simülasyonu eğitiminin kullanıcıları nasıl etkilediğini öğrenebilir ve simülasyon ve eğitim sonuçlarından içgörüler elde edebilir.
ms.technology: mdo
ms.openlocfilehash: fb08de05e0a1f31187fc4dd045d0f1ce45db2aea
ms.sourcegitcommit: a7cd723fd62b4b0aae9c2c2df04ead3c28180084
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2022
ms.locfileid: "65839378"
---
# <a name="insights-and-reports-for-attack-simulation-training-in-defender-for-office-365"></a>Office 365 için Defender'da Saldırı simülasyonu eğitimi için Analizler ve raporlar

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

[Office 365 için Microsoft Defender plan 2](defender-for-office-365.md) **için geçerlidir**

Office Plan 2 veya Microsoft 365 E5 için Microsoft Defender'da saldırı simülasyonu eğitimi bölümünde, Microsoft simülasyonların ve ilgili eğitimlerin sonuçlarından içgörüler ve raporlar sağlar. Bu bilgiler, kullanıcılarınızın tehdit hazırlığı ilerleme durumu ve kullanıcılarınızı gelecekteki saldırılara daha iyi hazırlamak için önerilen sonraki adımlar hakkında bilgi sahibi olmanıza yardımcı olur.

Analizler ve raporlar, Microsoft 365 Defender portalındaki Saldırı simülasyonu eğitimi bölümünde aşağıdaki konumlarda bulunabilir:

- **Genel Bakış** sekmesi.
- **Simülasyonlar** sekmesinde simülasyon ayrıntıları.

Bu makalenin geri kalanında kullanılabilir bilgiler açıklanmaktadır.

Saldırı simülasyonu eğitimi hakkında başlangıç bilgileri için bkz. [Saldırı simülasyonu eğitimini kullanarak Kullanmaya başlayın](attack-simulation-training-get-started.md).

## <a name="insights-and-reports-on-the-overview-tab-of-attack-simulation-training"></a>Saldırı simülasyonu eğitiminin Genel Bakış sekmesinde Analizler ve raporlar

**Genel Bakış** sekmesine gitmek için adresinden Microsoft 365 Defender portalını <https://security.microsoft.com>açın & işbirliği \> **Saldırı benzetimi eğitimi'ne** **e-posta gönderin** ve **Genel Bakış** sekmesinin seçili olduğunu doğrulayın (varsayılandır). **Doğrudan Saldırı simülasyonu eğitim** sayfasındaki **Genel Bakış** sekmesine gitmek için kullanın<https://security.microsoft.com/attacksimulator?viewid=overview>.

Bu bölümün geri kalanında, Saldırı simülasyonu eğitiminin **Genel Bakış** sekmesinde bulunan bilgiler açıklanmaktadır.

### <a name="recent-simulations-card"></a>Son simülasyonlar kartı

**Genel Bakış** sekmesindeki **Son simülasyonlar** kartı, kuruluşunuzda oluşturduğunuz veya çalıştırdığınız son üç simülasyonu gösterir.

Ayrıntıları görüntülemek için bir simülasyon seçebilirsiniz.

**Tüm simülasyonları görüntüle'yi** seçtiğinizde **Simülasyonlar** sekmesine gidin.

**Benzetimi başlat'ı seçtiğinizde simülasyon** oluşturma sihirbazı başlatılır. Daha fazla bilgi için bkz. [Office 365 için Defender'de kimlik avı saldırısı benzetimi](attack-simulation-training.md) yapma.

:::image type="content" source="../../media/attack-sim-training-overview-recent-simulations-card.png" alt-text="Microsoft 365 Defender portalındaki Saldırı simülasyonu eğitimi'nin Genel Bakış sekmesindeki Son simülasyonlar kartı" lightbox="../../media/attack-sim-training-overview-recent-simulations-card.png":::

### <a name="behavior-impact-on-compromise-rate-card"></a>Risk oranı kartı üzerindeki davranış etkisi

**Genel Bakış** sekmesindeki **Risk oranı kartı üzerindeki Davranış etkisi**, kullanıcılarınızın simülasyonlarınıza Microsoft 365 geçmiş verilere kıyasla nasıl yanıt verdiğini gösterir. Bu içgörüleri, aynı kullanıcı gruplarına karşı birden çok simülasyon çalıştırarak kullanıcıların tehdit hazırlığındaki ilerleme durumunu izlemek için kullanabilirsiniz.

Grafik verilerinin kendisi aşağıdaki bilgileri gösterir:

- **Tahmin edilen risk oranı**<sup>\*</sup>: Diğer tüm Microsoft 365 kuruluşlarda aynı yük türünü kullanan Saldırı simülasyonu eğitim simülasyonları için ortalama risk oranı.
- **Gerçek risk oranı**<sup>\*</sup>: Simülasyona düşen kullanıcıların gerçek yüzdesi.

Grafikte bir veri noktasının üzerine geldiğinizde gerçek yüzde değerleri gösterilir.

Kartta aşağıdaki özet bilgiler de gösterilir:

- **kullanıcılar kimlik avına daha az duyarlıdır**: Sanal saldırının tehlikeye atıldığı gerçek kullanıcı sayısı ile tahmin edilen risk oranı arasındaki fark. Bu sayıda kullanıcının gelecekte benzer saldırılardan etkilenme olasılığı daha düşüktür.
- **x%, tahmin edilen orandan daha iyi**: Kullanıcıların tahmin edilen risk oranına karşılık genel olarak nasıl yaptığını gösterir.

:::image type="content" source="../../media/attack-sim-training-overview-behavior-impact-card.png" alt-text="Microsoft 365 Defender portalındaki Saldırı benzetimi eğitimi'nin Genel Bakış sekmesindeki Risk oranı kartı üzerindeki Davranış etkisi" lightbox="../../media/attack-sim-training-overview-behavior-impact-card.png":::

Daha ayrıntılı bir rapor görmek için **Simülasyonları ve eğitim etkinliği raporunu görüntüle'ye** tıklayın. Bu rapor bu [makalenin ilerleyen bölümlerinde](#training-efficacy-tab-for-the-attack-simulation-report) açıklanmıştır.

### <a name="simulation-coverage-card"></a>Simülasyon kapsamı kartı

**Genel Bakış** sekmesindeki **Simülasyon kapsamı** kartı, kuruluşunuzda simülasyon (**Simülasyon kullanıcıları**) alan ve simülasyon almamış kullanıcıların (**Simülasyonu yapılmış olmayan kullanıcılar**) yüzdesini gösterir. Her kategorideki gerçek kullanıcı sayısını görmek için grafikteki bir bölümün üzerine gelebilirsiniz.

**Simülasyonu olmayan kullanıcılar için simülasyonu başlat'ı** seçtiğinizde, simülasyonu almayan kullanıcıların **Hedef kullanıcı** sayfasında otomatik olarak seçildiği simülasyon oluşturma sihirbazı başlatılır. Daha fazla bilgi için bkz. [Office 365 için Defender'de kimlik avı saldırısı benzetimi](attack-simulation-training.md) yapma.

**Simülasyon kapsamı raporunu görüntüle'yi** seçtiğinizde [Saldırı simülasyonu raporunun Kullanıcı kapsamı sekmesine](#user-coverage-tab-for-the-attack-simulation-report) gidin.

:::image type="content" source="../../media/attack-sim-training-overview-sim-coverage-card.png" alt-text="Microsoft 365 Defender portalındaki Saldırı simülasyonu eğitimi'nin Genel Bakış sekmesindeki Simülasyon kapsamı kartı" lightbox="../../media/attack-sim-training-overview-sim-coverage-card.png":::

### <a name="training-completion-card"></a>Eğitim tamamlama kartı

**Genel Bakış** sekmesindeki **Eğitim tamamlama** kartı, simülasyonların sonuçlarına göre eğitim alan kullanıcıların yüzdelerini aşağıdaki kategorilerde düzenler:

- **Tamamlandı**
- **Devam ediyor**
- **Eksik**

Her kategorideki gerçek kullanıcı sayısını görmek için grafikteki bir bölümün üzerine gelebilirsiniz.

**Eğitim tamamlanma raporunu görüntüle'yi** seçtiğinizde [, Saldırı simülasyonu raporunun Eğitim tamamlama sekmesine](#training-completion-tab-for-the-attack-simulation-report) gidin.

### <a name="repeat-offenders-card"></a>Tekrarlayanlar kartı

**Genel Bakış** sekmesindeki **Tekrarlayan suçlular** kartı, tekrarlayan suçlular hakkındaki bilgileri gösterir. _Yinelenen bir suçlu_, ardışık simülasyonlarla gizliliği tehlikeye giren bir kullanıcıdır. Varsayılan ardışık simülasyon sayısı ikidir, ancak konumundaki Saldırı benzetimi eğitiminin <https://security.microsoft.com/attacksimulator?viewid=setting>**Ayarlar** sekmesindeki değeri değiştirebilirsiniz.

Grafik, yinelenen suçlu verilerini [simülasyon türüne](attack-simulation-training.md#select-a-social-engineering-technique) göre düzenler:

- **Tüm**
- **Kötü amaçlı yazılım eki**
- **Kötü amaçlı yazılım bağlantısı**
- **Kimlik bilgisi toplama**
- **Eklerdeki bağlantı**
- **Sürücüye göre URL**

**Yinelenen suçlu raporunu görüntüle'yi** seçtiğinizde [Saldırı benzetimi raporu için Tekrarlayanlar sekmesine](#repeat-offenders-tab-for-the-attack-simulation-report) gidin.

### <a name="recommendations-card"></a>Öneriler kartı

**Genel Bakış** sekmesindeki **Öneriler** kartı, farklı simülasyon türlerinin çalıştırılmasını önerir.

**Başlat'ı** seçtiğinizde simülasyon oluşturma sihirbazı, Teknik **seç** sayfasında belirtilen simülasyon türü otomatik olarak seçilir. Daha fazla bilgi için bkz. [Office 365 için Defender'de kimlik avı saldırısı benzetimi](attack-simulation-training.md) yapma.

:::image type="content" source="../../media/attack-sim-training-overview-recommendations-card.png" alt-text="Microsoft 365 Defender portalındaki Saldırı simülasyonu eğitimi'nin Genel Bakış sekmesindeki Öneriler kartı" lightbox="../../media/attack-sim-training-overview-recommendations-card.png":::

### <a name="attack-simulation-report"></a>Saldırı simülasyonu raporu

Görünüm'e tıklayarak **Genel Bakış** sekmesinden **Saldırı benzetimi raporunu** açabilirsiniz **...** bu makalede açıklanan kartların çoğunda bulunan rapor düğmeleri. Doğrudan rapora gitmek için <https://security.microsoft.com/attacksimulationreport>

#### <a name="training-efficacy-tab-for-the-attack-simulation-report"></a>Saldırı benzetimi raporu için eğitim etkinliği sekmesi

**Saldırı benzetimi raporu** sayfasında Eğitim **etkinliği** sekmesi varsayılan olarak seçilidir. Bu sekme, **risk oranı üzerindeki davranış etkisi** kartında sağlanan bilgilerin aynısını simülasyondan ek bağlamla sağlar.

:::image type="content" source="../../media/attack-sim-report-training-efficacy-view.png" alt-text="Microsoft 365 Defender portalındaki Saldırı benzetimi raporundaki Eğitim etkinliği sekmesi" lightbox="../../media/attack-sim-report-training-efficacy-view.png":::

Grafikte **Tahmin edilen risk oranı** ve **Gerçek risk altındaki hız** gösterilir. Grafikteki bir bölümün üzerine geldiğinizde, için gerçek yüzde değerleri gösterilir.

Grafiğin altındaki ayrıntılar tablosu aşağıdaki bilgileri gösterir:

- **Simülasyon adı**
- **Simülasyon tekniği**
- **Simülasyon taktikleri**
- **Tahmin edilen risk oranı**
- **Gerçek risk altındaki oran**
- **Hedeflenen toplam kullanıcı sayısı**
- **Tıklanan kullanıcıların sayısı**

Kullanılabilir bir sütun üst bilgisine tıklayarak sonuçları sıralayabilirsiniz.

Gösterilen sütunları kaldırmak için **Sütunları özelleştir'e** tıklayın. İşiniz bittiğinde **Uygula'ya** tıklayın.

Sonuçları **Benzetim adına** veya **Benzetim Tekniğine** göre filtrelemek için Arama simgesi](../../media/m365-cc-sc-search-icon.png) **Arama** kutusunu kullanın![. Joker karakterler desteklenmez.

Dışarı Aktar simgesine ![tıklarsanız.](../../media/m365-cc-sc-download-icon.png) **Raporu dışarı aktar** düğmesi, rapor oluşturma ilerleme durumu tamamlanma yüzdesi olarak gösterilir. Açılan iletişim kutusunda, .csv dosyasını açmayı seçebilir, .csv dosyasını kaydedebilir ve seçimi anımsayabilirsiniz.

#### <a name="user-coverage-tab-for-the-attack-simulation-report"></a>Saldırı benzetimi raporu için kullanıcı kapsamı sekmesi

:::image type="content" source="../../media/attack-sim-report-user-coverage-view.png" alt-text="Microsoft 365 Defender portalındaki Saldırı benzetimi raporundaki Kullanıcı kapsamı sekmesi" lightbox="../../media/attack-sim-report-user-coverage-view.png":::

**Kullanıcı kapsamı** sekmesinde grafik, **Sanal kullanıcılar ve Simülasyon** **olmayan kullanıcılar'ı** gösterir. Grafikte bir veri noktasının üzerine geldiğinizde gerçek değerler gösterilir.

Grafiğin altındaki ayrıntılar tablosu aşağıdaki bilgileri gösterir:

- **Kullanıcı Adı**
- **E-posta adresi**
- **Simülasyona dahil**
- **Son benzetimin tarihi**
- **Son simülasyon sonucu**
- **Tıklanan sayısı**
- **Gizliliği ihlal edilenlerin sayısı**

Kullanılabilir bir sütun üst bilgisine tıklayarak sonuçları sıralayabilirsiniz.

Gösterilen sütunları kaldırmak için **Sütunları özelleştir'e** tıklayın. İşiniz bittiğinde **Uygula'ya** tıklayın.

Sonuçları **Kullanıcı Adı** veya **E-posta adresine** göre filtrelemek için Arama simgesi](../../media/m365-cc-sc-search-icon.png) **Arama** kutusunu kullanın![. Joker karakterler desteklenmez.

Dışarı Aktar simgesine ![tıklarsanız.](../../media/m365-cc-sc-download-icon.png) **Raporu dışarı aktar** düğmesi, rapor oluşturma ilerleme durumu tamamlanma yüzdesi olarak gösterilir. Açılan iletişim kutusunda, .csv dosyasını açmayı seçebilir, .csv dosyasını kaydedebilir ve seçimi anımsayabilirsiniz.

#### <a name="training-completion-tab-for-the-attack-simulation-report"></a>Saldırı benzetimi raporu için eğitim tamamlama sekmesi

:::image type="content" source="../../media/attack-sim-report-training-completion-view.png" alt-text="Microsoft 365 Defender portalındaki Saldırı benzetimi raporundaki Eğitim tamamlama sekmesi" lightbox="../../media/attack-sim-report-training-completion-view.png":::

**Eğitim tamamlama** sekmesinde, grafik **Tamamlandı**, **Devam Ediyor** ve **Tamamlanmamış** benzetimi sayısını gösterir. Grafikteki bir bölümün üzerine geldiğinizde gerçek değerler gösterilir.

Grafiğin altındaki ayrıntılar tablosu aşağıdaki bilgileri gösterir:

- **Kullanıcı Adı**
- **E-posta adresi**
- **Simülasyona dahil**
- **Son benzetimin tarihi**
- **Son simülasyon sonucu**
- **En son tamamlanan eğitimin adı**
- **Tamamlanma tarihi**
- **Tüm eğitimler**

Kullanılabilir bir sütun üst bilgisine tıklayarak sonuçları sıralayabilirsiniz.

Gösterilen sütunları kaldırmak için **Sütunları özelleştir'e** tıklayın. İşiniz bittiğinde **Uygula'ya** tıklayın.

Filtre simgesine tıklayın ![.](../../media/m365-cc-sc-filter-icon.png) **Grafik** ve ayrıntılar tablosunu aşağıdaki değerlerden birine veya daha fazlasına göre filtrelemek için filtreleyin:

- **Tamamlandı**
- **Devam ediyor**
- **Tüm**

Filtreleri yapılandırmayı bitirdiğinizde **Uygula**, **İptal veya** **Filtreleri temizle'ye** tıklayın.

Sonuçları **Kullanıcı Adı** veya **E-posta adresine** göre filtrelemek için Arama simgesi](../../media/m365-cc-sc-search-icon.png) **Arama** kutusunu kullanın![. Joker karakterler desteklenmez.

Dışarı Aktar simgesine ![tıklarsanız.](../../media/m365-cc-sc-download-icon.png) **Raporu dışarı aktar** düğmesi, rapor oluşturma ilerleme durumu tamamlanma yüzdesi olarak gösterilir. Açılan iletişim kutusunda, .csv dosyasını açmayı seçebilir, .csv dosyasını kaydedebilir ve seçimi anımsayabilirsiniz.

#### <a name="repeat-offenders-tab-for-the-attack-simulation-report"></a>Saldırı benzetimi raporu için yinele suçlular sekmesi

:::image type="content" source="../../media/attack-sim-report-repeat-offenders-view.png" alt-text="Microsoft 365 Defender portalındaki Saldırı benzetimi raporundaki Yinele suçlular sekmesi" lightbox="../../media/attack-sim-report-repeat-offenders-view.png":::

_Yinelenen bir suçlu_, ardışık simülasyonlarla gizliliği tehlikeye giren bir kullanıcıdır. Varsayılan ardışık simülasyon sayısı ikidir, ancak konumundaki Saldırı benzetimi eğitiminin <https://security.microsoft.com/attacksimulator?viewid=setting>**Ayarlar** sekmesindeki değeri değiştirebilirsiniz.

**Yinele suçlular** sekmesinde grafik, yinelenen suçlu verilerini [simülasyon türüne](attack-simulation-training.md#select-a-social-engineering-technique) göre düzenler:

- **Tüm**
- **Kimlik bilgisi toplama**
- **Kötü amaçlı yazılım eki**
- **Ekteki bağlantı**
- **Kötü amaçlı yazılım bağlantısı**
- **Sürücüye göre URL**

Grafikte bir veri noktasının üzerine geldiğinizde gerçek değerler gösterilir.

Grafiğin altındaki ayrıntılar tablosu aşağıdaki bilgileri gösterir:

- **Kullanıcı**
- **Yineleme sayısı**
- **Simülasyon türleri**
- **Simülasyon**

Kullanılabilir bir sütun üst bilgisine tıklayarak sonuçları sıralayabilirsiniz.

Gösterilen sütunları kaldırmak için **Sütunları özelleştir'e** tıklayın. İşiniz bittiğinde **Uygula'ya** tıklayın.

Filtre simgesine tıklayın ![.](../../media/m365-cc-sc-filter-icon.png) **Grafik** ve ayrıntılar tablosunu simülasyon türü değerlerinin bir kısmına veya tümüne göre filtrelemek için filtreleyin:

- **Kimlik bilgisi toplama**
- **Kötü amaçlı yazılım eki**
- **Ekteki bağlantı**
- **Kötü amaçlı yazılım bağlantısı**
- **Sürücüye göre URL**

Filtreleri yapılandırmayı bitirdiğinizde **Uygula**, **İptal veya** **Filtreleri temizle'ye** tıklayın.

Sonuçları sütun değerlerinden herhangi birine göre filtrelemek için Arama simgesi](../../media/m365-cc-sc-search-icon.png) **Arama** kutusunu kullanın![. Joker karakterler desteklenmez.

Dışarı Aktar simgesine ![tıklarsanız.](../../media/m365-cc-sc-download-icon.png) **Raporu dışarı aktar** düğmesi, rapor oluşturma ilerleme durumu tamamlanma yüzdesi olarak gösterilir. Açılan iletişim kutusunda, .csv dosyasını açmayı seçebilir, .csv dosyasını kaydedebilir ve seçimi anımsayabilirsiniz.

## <a name="insights-and-reports-in-the-simulation-details-of-attack-simulation-training"></a>Saldırı simülasyonu eğitiminin simülasyon ayrıntılarında Analizler ve raporlar

**Simülasyonlar** sekmesine gitmek için adresinden Microsoft 365 Defender portalını <https://security.microsoft.com>açın **, e-posta & işbirliği** \> **Saldırı benzetimi eğitimi'ne** gidin ve **Simülasyonlar** sekmesini seçin. **Doğrudan Saldırı simülasyonu eğitim** sayfasındaki **Simülasyonlar** sekmesine gitmek için kullanın<https://security.microsoft.com/attacksimulator?viewid=simulations>.

Listeden bir simülasyon seçtiğinizde ayrıntılar sayfası açılır. Bu sayfa, görmeyi beklediğiniz simülasyonun yapılandırma ayarlarını (durum, başlatma tarihi, kullanılan yük vb.) içerir.

Bu bölümün geri kalanında simülasyon ayrıntıları sayfasında bulunan içgörüler ve raporlar açıklanmaktadır.

### <a name="simulation-impact-section"></a>Simülasyon etkisi bölümü

Simülasyon ayrıntıları sayfasındaki **Simülasyon etkisi** bölümünde, simülasyon tarafından kaç kullanıcının tamamen kandırıldığı ve simülasyondaki toplam kullanıcı sayısı gösterilir. Gösterilen bilgiler simülasyon türüne göre değişir. Örneğin:

- Bağlantılar: **Kimlik bilgileri girildi** ve **Kimlik bilgileri girilmedi**.

  :::image type="content" source="../../media/attack-sim-training-sim-details-sim-impact-links.png" alt-text="Bağlantıyla ilgili simülasyon ayrıntıları için Simülasyon etkisi bölümü" lightbox="../../media/attack-sim-training-sim-details-sim-impact-links.png":::

- Ekler: **Ek açıldı** ve **Ek açılmadı**.

  :::image type="content" source="../../media/attack-sim-training-sim-details-sim-impact-attachments.png" alt-text="Ekle ilgili simülasyon ayrıntıları için Simülasyon etkisi bölümü" lightbox="../../media/attack-sim-training-sim-details-sim-impact-attachments.png":::

Grafikteki bir bölümün üzerine geldiğinizde, her kategori için gerçek sayılar gösterilir.

### <a name="all-user-activity-section"></a>Tüm kullanıcı etkinliği bölümü

Simülasyon ayrıntıları sayfasındaki **Tüm kullanıcı etkinliği** bölümünde simülasyonun olası sonuçları için sayılar gösterilir. Gösterilen bilgiler simülasyon türüne göre değişir. Örneğin:

- **SuccessfullyDeliveredEmail**
- **ReportedEmail**: Simülasyon iletisini kaç kullanıcı şüpheli olarak bildirdi?
- Bağlantı:
  - **EmailLinkClicked**: Simülasyon iletisindeki bağlantıya kaç kullanıcı tıkladı?
  - **CredSupplied**: Bağlantıya tıkladıktan sonra, kimlik bilgilerini sağlayan kullanıcı sayısı.

    :::image type="content" source="../../media/attack-sim-training-sim-details-all-user-activity-links.png" alt-text="Bağlantıyla ilgili simülasyon ayrıntıları için Tüm kullanıcı etkinliği bölümü" lightbox="../../media/attack-sim-training-sim-details-all-user-activity-links.png":::

- Ekleri:
  - **AttachmentOpened**: Simülasyon iletisinde eki açan kullanıcı sayısı.

    :::image type="content" source="../../media/attack-sim-training-sim-details-all-user-activity-attachments.png" alt-text="Ekle ilgili simülasyon ayrıntıları için Tüm kullanıcı etkinliği bölümü" lightbox="../../media/attack-sim-training-sim-details-all-user-activity-attachments.png":::

### <a name="training-completion-section"></a>Eğitim tamamlama bölümü

Simülasyon ayrıntıları sayfasındaki **Eğitim tamamlama** bölümünde simülasyon için gereken eğitimler ve eğitimleri kaç kullanıcının tamamlamış olduğu gösterilir.

:::image type="content" source="../../media/attack-sim-training-sim-details-training-completed.png" alt-text="Ekle ilgili simülasyon ayrıntıları için Eğitim tamamlama bölümü" lightbox="../../media/attack-sim-training-sim-details-training-completed.png":::

## <a name="recommended-actions-section"></a>Önerilen eylemler bölümü

Simülasyon ayrıntıları sayfasındaki **Önerilen eylemler** bölümünde [, Microsoft Güvenli Puanı'ndan](../defender/microsoft-secure-score.md) gelen öneri eylemleri ve eylemin Güvenli Puanınız üzerindeki etkisi gösterilir. Bu öneriler simülasyonda kullanılan yükü temel alır ve kullanıcılarınızın ve ortamınızın korunmasına yardımcı olur. Listeden bir **İyileştirme eylemini** seçtiğinizde, önerilen eylemi uygulamak için sizi konuma götürür.

:::image type="content" source="../../media/attack-sim-training-sim-details-recommended-actions.png" alt-text="Saldırı simülasyonu eğitimiyle ilgili Öneri eylemleri bölümü" lightbox="../../media/attack-sim-training-sim-details-recommended-actions.png":::

## <a name="related-links"></a>İlgili Bağlantılar

[Saldırı simülasyonu eğitimini kullanmaya başlama](attack-simulation-training-get-started.md)

[Kimlik avı saldırısı simülasyonu oluşturma](attack-simulation-training.md)

[kişilerinizi eğitme amacıyla yük oluşturma](attack-simulation-training-payloads.md#create-payloads)
