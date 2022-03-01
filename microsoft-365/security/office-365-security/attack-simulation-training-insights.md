---
title: Analizler benzetim eğitimi ve raporları
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
description: Yöneticiler, uygulama portalında Saldırı benzetimi eğitiminin kullanıcıları nasıl etkilediğini Microsoft 365 Defender benzetim ve eğitim sonuçlardan içgörüler elde eder.
ms.technology: mdo
ms.openlocfilehash: c06cea01fcc7bb8fdc9c869fe8117f85eb627685
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2022
ms.locfileid: "63021808"
---
# <a name="insights-and-reports-for-attack-simulation-training-in-defender-for-office-365"></a>Analizler için Defender'daki Saldırı benzetimi eğitimi hakkında daha fazla Office 365

 [Office 365 için Microsoft Defender plan 2 için geçerlidir](defender-for-office-365.md)

Microsoft, Plan 2 veya Office için Microsoft Defender'daki Saldırı benzetim eğitimi Microsoft 365 E5, benzetimlerin ve ilgili eğitimlerin sonuçlarından öngörüler ve raporlar sağlar. Bu bilgiler, kullanıcılarınızı tehdit hazırlığı ilerleme durumu hakkında bilgi sahibi olmanızı sağlar ve kullanıcılarınızı gelecekteki saldırılara daha iyi hazırlamak için önerilen sonraki adımlar konusunda bilgi sahibi olur.

Analizler raporlarına aşağıdaki konumlarda, Web portalında Saldırı benzetimi eğitimi Microsoft 365 Defender vardır:

- Genel **Bakış** sekmesi.
- Benzetimler sekmesinde **benzetim** ayrıntıları.

Bu makalenin kalan kalanında kullanılabilir bilgiler açıklanmıştır.

Saldırı benzetimi eğitimi hakkında bilgi almak için bkz. [Saldırı benzetimi eğitimlerini kullanmaya başlama](attack-simulation-training-get-started.md).

## <a name="insights-and-reports-on-the-overview-tab-of-attack-simulation-training"></a>Analizler benzetim eğitimine genel bakış sekmesindeki rapor ve raporlar

Genel Bakış sekmesine  gitmek için, Microsoft 365 Defender portalını <https://security.microsoft.com>açın, E-posta **&** \> işbirliği **Saldırı** benzetim eğitimi'ne gidin ve Genel Bakış sekmesinin seçili olduğunu  doğrulayın (varsayılandır). Saldırı benzetimi eğitim **sayfasındaki** Genel Bakış **sekmesine doğrudan gitmek** için kullanın <https://security.microsoft.com/attacksimulator?viewid=overview>.

Bu bölümün kalan bölümünde, Saldırı benzetim eğitimi'nin **Genel Bakış** sekmesinde bulunan bilgiler açıklanır.

### <a name="recent-simulations-card"></a>En son benzetimler kartı

Genel **Bakış sekmesindeki** Son **benzetimler** kartı, oluşturduğunuz veya kuruluşta çalıştırılan son üç benzetimi gösterir.

Ayrıntıları görüntülemek için bir benzetim seçin.

Tüm **benzetimleri görüntüle'yi seçmek** sizi Benzetimler **sekmesine** alır.

Benzetim **başlat'ı seçmek** benzetim oluşturma sihirbazını başlatır. Daha fazla bilgi için bkz[. Daha fazla bilgi için bkz. Kimlik avı saldırısının benzetimini Office 365](attack-simulation-training.md).

![Hızlı Erişim portalının Saldırı benzetim eğitimi'nin Genel Bakış sekmesindeki son Microsoft 365 Defender kartı.](../../media/attack-sim-training-overview-recent-simulations-card.png)

### <a name="behavior-impact-on-compromise-rate-card"></a>Güvenlik oranı kartı üzerindeki davranış etkisi

Genel **Bakış sekmesindeki** güvenlik oranı kartı üzerindeki Davranış  etkisi, kullanıcılarının benzetimlerinize yanıt verme biçimlerini, geçmiş Microsoft 365. Bu içgörüleri, aynı kullanıcı gruplarına karşı çeşitli benzetimler çalıştırarak kullanıcıların tehdit hazırlığı ilerlemesini izlemek için kullanabilirsiniz.

Grafik verilerinde aşağıdaki bilgiler görüntülenir:

- **Öngörülen güvenlik oranı**<sup>\*</sup>: Diğer tüm Microsoft 365 genelinde aynı yük türünü kullanan Saldırı benzetim eğitimi benzetimleri için ortalama güvenlik oranı.
- **Gerçek güvenlik oranı**<sup>\*</sup>: Benzetime uygun kullanıcıların gerçek yüzdesini.

Grafikte bir veri noktasının üzerine gelindiğinde, gerçek yüzde değerleri gösterilir.

Kartta aşağıdaki özet bilgiler de gösterilir:

- **kimlik avına karşı daha az** duyarlı kullanıcı: Sanal saldırıyla tehlikeye atılmış gerçek kullanıcı sayısı ile öngörülen güvenlik ödün oranı arasındaki fark. Gelecekte benzer saldırılar tarafından bu sayıda kullanıcının güvenliği ihlal edilmiş olma olasılığı daha düşük olacaktır.
- **x%tahmini orandan daha iyi**: Kullanıcıların öngörülen güvenlik oranının aksine genel olarak ne yaptığını gösterir.

![Güvenlik portalında yer alan Saldırı benzetimi eğitimi'nin Genel Bakış sekmesindeki güvenlik oranı kartı üzerindeki Microsoft 365 Defender.](../../media/attack-sim-training-overview-behavior-impact-card.png)

Daha ayrıntılı bir rapor görmek için Benzetimleri **ve eğitim ayrıntılı raporunu görüntüle'ye tıklayın**. Bu rapor, bu [makalenin ilerleyen sayfalarında açıklanmıştır](#training-efficacy-tab-for-the-attack-simulation-report).

### <a name="simulation-coverage-card"></a>Benzetim kapsam kartı

Genel **Bakış sekmesindeki** Benzetim  kapsam kartı, bir benzetim **(** Benzetim kullanıcı) alan ve benzetim (benzetimsiz kullanıcılar) alan kullanıcıların yüzdesini **gösterir.** Grafikte bir bölümün üzerine gelerek her kategorideki gerçek kullanıcı sayısını bulabilirsiniz.

Benzetimi **olmayan kullanıcılar için** benzetimi başlat'ı seçmek Benzetim oluşturma sihirbazını başlatır ve bu sihirbazda benzetimi almayan kullanıcılar Hedef kullanıcı sayfasında otomatik **olarak** seçilir. Daha fazla bilgi için bkz[. Daha fazla bilgi için bkz. Kimlik avı saldırısının benzetimini Office 365](attack-simulation-training.md).

Benzetim **kapsam raporunu görüntüle'yi** seçmek Sizi Saldırı [benzetimi raporu için Kullanıcı kapsamı sekmesine alır](#user-coverage-tab-for-the-attack-simulation-report).

![Microsoft 365 Defender portalında, Saldırı benzetimi eğitimi'nin Genel Microsoft 365 Defender kartı.](../../media/attack-sim-training-overview-sim-coverage-card.png)

### <a name="training-completion-card"></a>Eğitim tamamlama kartı

Genel **Bakış sekmesindeki** **Eğitim tamamlanma** kartı, benzetimlerin sonuçlarına bağlı olarak eğitim alan kullanıcıların yüzdelerini aşağıdaki kategorilerde düzenlemeyi sağlar:

- **Tamamlandı**
- **Devam ediyor**
- **Eksik**

Grafikte bir bölümün üzerine gelerek her kategorideki gerçek kullanıcı sayısını bulabilirsiniz.

Eğitim tamamlama **raporunu görüntüle'yi seçmek** sizi Saldırı [benzetimi raporunun Eğitim tamamlama sekmesine alır](#training-completion-tab-for-the-attack-simulation-report).

### <a name="repeat-offenders-card"></a>Yinelemeli kartı yineleme

Genel **Bakış sekmesindeki** **Yinelemelilerin kartı** , yinelemeli hakkında bilgileri gösterir. _Tekrarlı bir yineleme_, ardışık benzetimler ile tehlikeye atılmış bir kullanıcıdır. Varsayılan ardışık benzetim sayısı ikidir, ancak saldırı benzetimi eğitimi'nin Ayarlar sekmesindeki  değeri değiştirebilirsiniz<https://security.microsoft.com/attacksimulator?viewid=setting>.

Grafik, yinelemeli verileri benzetim [türüne göre organize eder](attack-simulation-training.md#select-a-social-engineering-technique):

- **Hepsi**
- **Kötü amaçlı yazılım eki**
- **Kötü amaçlı yazılım bağlantısı**
- **Kimlik bilgileri toplama**
- **Eklerde bağlantı**
- **Sürücüye göre URL**

Yineleme raporunu **görüntüle'yi seçmek sizi** Saldırı benzetimi raporu [için Yinele sekmesine alır.](#repeat-offenders-tab-for-the-attack-simulation-report)

### <a name="recommendations-card"></a>Öneriler kartı

Genel **Öneriler** sekmesindeki **genel bakış kartı**, çalıştıracak farklı benzetim türleri önerir.

Başlat seçildiğinde **benzetim** oluşturma sihirbazı başlatılır ve Seçme tekniği sayfasında belirtilen benzetim türü otomatik **olarak** seçilir. Daha fazla bilgi için bkz[. Daha fazla bilgi için bkz. Kimlik avı saldırısının benzetimini Office 365](attack-simulation-training.md).

![Öneriler portalında Saldırı benzetim eğitimi'nin Genel Bakış Microsoft 365 Defender tıklayın.](../../media/attack-sim-training-overview-recommendations-card.png)

### <a name="attack-simulation-report"></a>Saldırı benzetimi raporu

Saldırı benzetimi **raporunu Görünüm** ... üzerine **tıklayarak Genel Bakış** sekmesinden **açabilirsiniz. bu** makalede açıklanan kartların çoğunda kullanılabilen rapor düğmeleri. Doğrudan rapora gitmek için <https://security.microsoft.com/attacksimulationreport>

#### <a name="training-efficacy-tab-for-the-attack-simulation-report"></a>Saldırı benzetimi raporu için eğitim etkinliği sekmesi

Saldırı **benzetimi raporu** sayfasında, **Eğitim sanal sekmesi** varsayılan olarak seçilidir. Bu sekme, benzetimin kendisinde ek bağlam olacak şekilde, güvenlik oranı kartı üzerindeki davranış etkisi konusunda mevcut olan aynı bilgileri sağlar.

![Microsoft 365 Defender portalında Saldırı benzetim raporu'nın eğitim Microsoft 365 Defender sekmesi.](../../media/attack-sim-report-training-efficacy-view.png)

Grafikte Öngörülen güvenlik **ödün oranı ve Fiili** güvenliği **ihlal oranı görüntülenir**. Grafikte bir bölümün üzerine gelindiğinde, gerçek yüzde değerleri gösterilir.

Grafiğin altındaki ayrıntılar tablosu aşağıdaki bilgileri gösterir:

- **Benzetim adı**
- **Benzetim tekniği**
- **Benzetim taktikleri**
- **Güvenliği ihlal edilen oran**
- **Fiili güvenliği tehlikeye atılmış oran**
- **Hedefli toplam kullanıcı sayısı**
- **Tıklı kullanıcı sayısı**

Kullanılabilir bir sütun başlığına tıklayarak sonuçları sıraabilirsiniz.

Gösterilen **sütunları kaldırmak** için Sütunları özelleştir'e tıklayın. Bitirdikten sonra Uygula'ya **tıklayın**.

Sonuçları ![Benzetim adı](../../media/m365-cc-sc-search-icon.png) **veya** Benzetim Tekniği'ne göre filtrelemek **için Arama simgesi** Arama **kutusunu kullanın**. Joker karakterler desteklenmiyor.

Dışarı Aktar simgesine ![tıklarsanız.](../../media/m365-cc-sc-download-icon.png) **Raporu dışarı** aktar düğmesi, rapor oluşturma ilerleme durumu tamamlandı yüzdesi olarak gösterilir. Açılan iletişim kutusunda, .csv dosyayı açmayı, .csv seçimi anımsayın.

#### <a name="user-coverage-tab-for-the-attack-simulation-report"></a>Saldırı benzetimi raporu için kullanıcı kapsamı sekmesi

![Uygulama portalında yer alan Saldırı benzetimi raporunun kullanıcı Microsoft 365 Defender sekmesi.](../../media/attack-sim-report-user-coverage-view.png)

Kullanıcı **kapsamı sekmesinde** , grafikTemli kullanıcılar ve **Benzetimi** olmayan **kullanıcılar görüntülenir**. Grafikte bir veri noktasının üzerine gelindiğinde, gerçek değerler gösterilir.

Grafiğin altındaki ayrıntılar tablosu aşağıdaki bilgileri gösterir:

- **Kullanıcı Adı**
- **E-posta adresi**
- **Benzetime dahil**
- **Son benzetim tarihi**
- **Son benzetim sonucu**
- **Tık sayısını**
- **Güvenliği ihlal edilmiş sayı**

Kullanılabilir bir sütun başlığına tıklayarak sonuçları sıraabilirsiniz.

Gösterilen **sütunları kaldırmak** için Sütunları özelleştir'e tıklayın. Bitirdikten sonra Uygula'ya **tıklayın**.

Sonuçları ![Kullanıcı adı veya](../../media/m365-cc-sc-search-icon.png) **E-posta** adresine göre filtrelemek **için Ara simgesi** Arama **kutusunu kullanın**. Joker karakterler desteklenmiyor.

Dışarı Aktar simgesine ![tıklarsanız.](../../media/m365-cc-sc-download-icon.png) **Raporu dışarı** aktar düğmesi, rapor oluşturma ilerleme durumu tamamlandı yüzdesi olarak gösterilir. Açılan iletişim kutusunda, .csv dosyayı açmayı, .csv seçimi anımsayın.

#### <a name="training-completion-tab-for-the-attack-simulation-report"></a>Saldırı benzetimi raporu için eğitim tamamlama sekmesi

![Proje portalında Saldırı benzetimi raporunun Eğitim Microsoft 365 Defender sekmesi.](../../media/attack-sim-report-training-completion-view.png)

Eğitim **tamamlanma sekmesindeki** grafikte **Tamamlanan, Sürüyor** ve **Tamamlanmamış** **benzetimlerin sayısı** görüntülenir. Grafikte bir bölümün üzerine gelindiğinde, gerçek değerler gösterilir.

Grafiğin altındaki ayrıntılar tablosu aşağıdaki bilgileri gösterir:

- **Kullanıcı Adı**
- **E-posta adresi**
- **Benzetime dahil**
- **Son benzetim tarihi**
- **Son benzetim sonucu**
- **Tamamlanan en son eğitimin adı**
- **Tamamlanma tarihi**
- **Tüm eğitimler**

Kullanılabilir bir sütun başlığına tıklayarak sonuçları sıraabilirsiniz.

Gösterilen **sütunları kaldırmak** için Sütunları özelleştir'e tıklayın. Bitirdikten sonra Uygula'ya **tıklayın**.

Filtre simgesine ![tıklayın.](../../media/m365-cc-sc-filter-icon.png) **Grafik** ve ayrıntılar tablosuna aşağıdaki değerlerden bir veya daha fazlasını filtreleyenin:

- **Tamamlandı**
- **Devam ediyor**
- **Hepsi**

Filtreleri yapılandırmayı bitirdikten sonra, Filtreleri Uygula, İptal **et** **veya Temizle'yi** **tıklatın**.

Sonuçları ![Kullanıcı adı veya](../../media/m365-cc-sc-search-icon.png) **E-posta** adresine göre filtrelemek **için Ara simgesi** Arama **kutusunu kullanın**. Joker karakterler desteklenmiyor.

Dışarı Aktar simgesine ![tıklarsanız.](../../media/m365-cc-sc-download-icon.png) **Raporu dışarı** aktar düğmesi, rapor oluşturma ilerleme durumu tamamlandı yüzdesi olarak gösterilir. Açılan iletişim kutusunda, .csv dosyayı açmayı, .csv seçimi anımsayın.

#### <a name="repeat-offenders-tab-for-the-attack-simulation-report"></a>Saldırı benzetimi raporu için yinelemeli sekme

![Microsoft 365 Defender portalında Saldırı benzetimi raporunun yinelemesi sekmesini tekrarlayın.](../../media/attack-sim-report-repeat-offenders-view.png)

_Tekrarlı bir yineleme_, ardışık benzetimler ile tehlikeye atılmış bir kullanıcıdır. Varsayılan ardışık benzetim sayısı ikidir, ancak saldırı benzetimi eğitimi'nin Ayarlar sekmesindeki  değeri değiştirebilirsiniz<https://security.microsoft.com/attacksimulator?viewid=setting>.

**Yinelemelileri yinele** sekmesinde grafik, yinelemeli verileri benzetim türüne [göre organize eder](attack-simulation-training.md#select-a-social-engineering-technique):

- **Hepsi**
- **Kimlik bilgileri toplama**
- **Kötü amaçlı yazılım eki**
- **Ekin içinde bağlantı**
- **Kötü amaçlı yazılım bağlantısı**
- **Sürücüye göre URL**

Grafikte bir veri noktasının üzerine gelindiğinde, gerçek değerler gösterilir.

Grafiğin altındaki ayrıntılar tablosu aşağıdaki bilgileri gösterir:

- **Kullanıcı**
- **Tekrar sayma**
- **Benzetim türleri**
- **Benzetimler**

Kullanılabilir bir sütun başlığına tıklayarak sonuçları sıraabilirsiniz.

Gösterilen **sütunları kaldırmak** için Sütunları özelleştir'e tıklayın. Bitirdikten sonra Uygula'ya **tıklayın**.

Filtre simgesine ![tıklayın.](../../media/m365-cc-sc-filter-icon.png) **Grafiği** ve ayrıntılar tabloyu benzetim türü değerlerinin bir veya birkaç türüne göre filtrelemek için filtre kullanın:

- **Kimlik bilgileri toplama**
- **Kötü amaçlı yazılım eki**
- **Ekin içinde bağlantı**
- **Kötü amaçlı yazılım bağlantısı**
- **Sürücüye göre URL**

Filtreleri yapılandırmayı bitirdikten sonra, Filtreleri Uygula, İptal **et** **veya Temizle'yi** **tıklatın**.

Sonuçları ![herhangi bir](../../media/m365-cc-sc-search-icon.png) **sütun** değerine göre filtrelemek için Ara simgesi Arama kutusunu kullanın. Joker karakterler desteklenmiyor.

Dışarı Aktar simgesine ![tıklarsanız.](../../media/m365-cc-sc-download-icon.png) **Raporu dışarı** aktar düğmesi, rapor oluşturma ilerleme durumu tamamlandı yüzdesi olarak gösterilir. Açılan iletişim kutusunda, .csv dosyayı açmayı, .csv seçimi anımsayın.

## <a name="insights-and-reports-in-the-simulation-details-of-attack-simulation-training"></a>Analizler benzetimi eğitimiyle ilgili benzetim ayrıntılarında yer alan rapor ve raporlar

Benzetimler **sekmesine gitmek** için, Microsoft 365 Defender portalına <https://security.microsoft.com>gidin, E-posta **&** \> **Saldırı** benzetim eğitimi'ne gidin ve **Benzetimler sekmesini** seçin. Doğrudan Saldırı benzetimi **eğitim sayfasındaki** **Benzetimler sekmesine gitmek** için kullanın<https://security.microsoft.com/attacksimulator?viewid=simulations>.

Listeden bir benzetim seçinca, ayrıntılar sayfası açılır. Bu sayfa, görmeyi beklediğiniz benzetimin yapılandırma ayarlarını (durum, başlatma tarihi, kullanılan yükleme, vb.) içerir.

Bu bölümün kalan bölümünde, benzetim ayrıntıları sayfasında bulunan içgörüler ve raporlar açık bulunmaktadır.

### <a name="simulation-impact-section"></a>Benzetim etkisi bölümü

**Benzetim ayrıntıları** sayfasındaki Benzetim etkisi bölümü, benzetim tarafından kaç kullanıcının tamamen püf noktası olduğunu ve benzetimde yer alan toplam kullanıcı sayısını gösterir. Gösterilen bilgiler benzetim türüne göre değişir. Örneğin:

- Bağlantılar: **Kimlik bilgileri girildi** **ve Kimlik bilgileri girildi**.

  ![Bağlantıyla ilgili benzetim ayrıntıları için benzetim etkisi bölümü.](../../media/attack-sim-training-sim-details-sim-impact-links.png)

- Ekler: **Ek açıldı** **ve Ek açılmadı**.

  ![Eklerle ilgili benzetim ayrıntıları için benzetim etkisi bölümü.](../../media/attack-sim-training-sim-details-sim-impact-attachments.png)

Grafikte bir bölümün üzerine gelindiğinde, her kategorinin gerçek sayıları gösterilir.

### <a name="all-user-activity-section"></a>Tüm kullanıcı etkinliği bölümü

**Benzetim ayrıntıları sayfasındaki** Tüm kullanıcı etkinliği bölümü, benzetimin olası sonuçları için sayıları gösterir. Gösterilen bilgiler benzetim türüne göre değişir. Örneğin:

- **SuccessfullyDeliveredEmail**
- **BildirilenEmail**: Benzetim mesajını şüpheli olarak kaç kullanıcı bildirdi?
- Bağlantılar:
  - **EmailLinkClicked**: Benzetim mesajında bağlantıya kaç kullanıcı tıklamış?
  - **CredSupplied**: Bağlantıya tıklandıktan sonra, kaç kullanıcının kimlik bilgilerini sağladığını.

    ![Bağlantıyla ilgili benzetim ayrıntıları için tüm kullanıcı etkinliği bölümü.](../../media/attack-sim-training-sim-details-all-user-activity-links.png)

- Ekler:
  - **Ek Açıldı**: Benzetim iletisinde eki açan kullanıcı sayısı.

    ![Eklerle ilgili benzetim ayrıntıları için tüm kullanıcı etkinliği bölümü.](../../media/attack-sim-training-sim-details-all-user-activity-attachments.png)

### <a name="training-completion-section"></a>Eğitim tamamlama bölümü

**Benzetim ayrıntıları** sayfasındaki Eğitim tamamlanma bölümü, benzetim için gereken eğitimleri ve kaç kullanıcının eğitimleri tamamlamış olduğunu gösterir.

![Ekle ilgili benzetim ayrıntıları için eğitim tamamlama bölümü.](../../media/attack-sim-training-sim-details-training-completed.png)

## <a name="recommended-actions-section"></a>Önerilen eylemler bölümü

**Benzetim ayrıntıları sayfasındaki** Önerilen eylemler bölümü [, Microsoft Güvenli](../defender/microsoft-secure-score.md) Puanı'nın öneri eylemlerini ve eylemin Güvenli Puanınıza etkisini gösterir. Bu öneriler benzetimde kullanılan yüke dayalıdır ve kullanıcılarınızı ve ortamınızı korumaya yardımcı olur. Listeden bir **Geliştirme eylemi** seçerek önerilen eylemi uygulayanın bulunduğu konuma varabilirsiniz.

![Saldırı benzetimi eğitimi'nin Öneri eylemleri bölümü.](../../media/attack-sim-training-sim-details-recommended-actions.png)

## <a name="related-links"></a>İlgili Bağlantılar

[Saldırı benzetimi eğitimlerini kullanmaya başlama](attack-simulation-training-get-started.md)

[Kimlik avı saldırı benzetimi oluşturma](attack-simulation-training.md)

[kişilerinizi eğitim için yük oluşturma](attack-simulation-training-payloads.md)
