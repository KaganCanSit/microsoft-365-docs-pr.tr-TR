---
title: Taslak koleksiyonunu gözden geçirme kümesine kaydetme
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
ms.reviewer: nickrob
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Taslak koleksiyonu oluşturduk ve bu koleksiyonu aynı şekilde tamamladikten sonra, bunu bir gözden geçirme kümesine ataktan. Bir taslak koleksiyonu işlerken, toplanan öğeler bu durumda gözden geçirmek için eklenir. Toplanan öğeler gözden geçirme kümesine alındıktan sonra bunları analiz edip gözden geçirebilirsiniz ve dışarı aktarabilirsiniz.
ms.openlocfilehash: d74d1b062101973d2d3cb055700c59a2d25c0d14
ms.sourcegitcommit: bb493f12701f6d6ee7d5e64b541adb87470bc7bc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/18/2022
ms.locfileid: "63015503"
---
# <a name="commit-a-draft-collection-to-a-review-set-in-advanced-ediscovery"></a>Taslak koleksiyonunu Gözden Geçirme Kümesi'ne Advanced eDiscovery

Taslak koleksiyonda toplanmış olan öğelerden memnunsanız ve bunları çözümlemeye, etiketlemeye ve gözden geçirmeye hazırsanız, olaydaki bir gözden geçirme kümesine koleksiyon  eklemeye hazır olursanız. Taslak koleksiyonunu gözden geçirme kümesine işlerken, toplanan öğeler bu koleksiyonun özgün içerik konumlarından Microsoft 365 gözden geçirme kümesine kopyalanır. Gözden geçirme kümesi, Microsoft tarafından sağlanan ve Microsoft Depolama bir konumtur.

## <a name="commit-a-draft-collection-to-a-review-set"></a>Taslak koleksiyonunu gözden geçirme kümesine kaydetme

1. Koleksiyon Microsoft 365 uyumluluk merkezi büyük/küçük Advanced eDiscovery açın ve ardından Koleksiyonlar sekmesini seçerek olayda yer alan koleksiyonların listesini görüntüleyin.

   ![Bir vakada yer alan koleksiyonların listesi.](../media/CommitDraftCollections1.png)

   > [!TIP]
   > Durum sütunundaki `Estimated` **bir değer** , gözden geçirme kümesine eklen hazır taslak koleksiyonlarını tanımlar. Bir koleksiyonun `Committed` gözden geçirme kümesine önceden eklenmiş olduğunu gösterir.

2. Koleksiyonlar **sayfasında** , gözden geçirme kümesine işlemek istediğiniz taslak koleksiyonunu seçin.

3. Uç uç sayfasının en altında **ActionsEdit** **koleksiyonu** >  öğesini seçin.

4. Koleksiyonu düzenleme sihirbazında, Taslağı **kaydet veya** topla **sayfası görüntülenene kadar Sonraki'ne** tıklayın.

5. Aşağıdaki ayarları yapılandırma:

   1. Gözden geçirmek **için Öğeleri topla ve ekle'yi seçin**.

   2. Koleksiyonu yeni bir gözden geçirme kümesine mi (koleksiyonu gönderdikten sonra oluşturulmuş) yoksa var olan bir gözden geçirme kümesine mi ekley istediğinize karar verin. Bu bölümü, kararınıza bağlı olarak tamamlamanız gerekir.

   3. Ek koleksiyon ayarlarını yapılandırma:

      ![Ek koleksiyon ayarlarını yapılandırma.](../media/AeDAdditionalCollectionSettings.png).

       a. **Teams ve Yammer:** Koleksiyona, arama sorgusu tarafından döndürülen sohbet öğelerini içeren konuşma dizilerini koleksiyona eklemek için bu seçeneği belirtin. Bu, arama ölçütlerine uyan öğeler içeren sohbet görüşmenin yeniden var olduğu anlamına gelir. Bu, gidip konuşmanın bağlamında sohbet öğelerini gözden geçirmenizi sağlar. Daha fazla bilgi için bkz[. Advanced eDiscovery'de konuşma Advanced eDiscovery](conversation-review-sets.md).

       b. **Bulut ekleri**: Koleksiyon sonuçları gözden geçirme kümesine ekli olduğunda modern ekleri veya bağlı dosyaları eklemek için bu seçeneği belirtin. Bu, modern ekin veya bağlı dosyanın hedef dosyasının gözden geçirme kümesine ekli olduğu anlamına gelir.

       > [!NOTE]
       > Yeni harf biçimi kullanılarak oluşturulmuş Teams ileti Yammer ileti ve bulut eklerini bağlama göre toplamak için iki seçenek varsayılan olarak seçilidir (ve gri gösterilir). Daha fazla bilgi için bkz [. Yeni vaka biçimini kullanma](advanced-ediscovery-new-case-format.md).

       c. **Kısmen dizine alınan öğeler**: Ek veri kaynaklarından kısmen dizine alınan öğeleri gözden geçirme kümesine eklemek için bu seçeneği belirtin. Koleksiyonda arama yapılan ek veri kaynakları varsa (koleksiyonlar sihirbazının Ek konumlar sayfasında belirtilen şekilde), bu konumlardan gözden geçirme kümesine eklemek istediğiniz kısmen dizine alınan öğeler olabilir. Özel ve özel olmayan veri kaynaklarının normalde kısmen dizine alınan öğeleri yok. Bunun nedeni, Gelişmiş dizin oluşturma işleminin, bir vakaya özel ve özel olmayan veri kaynakları ekli olduğunda öğeleri yeniden dizine oluşturmasıdır. Ayrıca, kısmen dizine eklenen öğelerin sayısı, gözden geçirme kümesine eklenen öğelerin sayısını da artıracaktır. <p> Gözden geçirme kümesine kısmen dizine eklenen öğelerden sonra, bu öğeleri özel olarak görüntülemek için filtre uygulayabilirsiniz. Daha fazla bilgi için bkz [. Kısmen dizine alınan öğeleri filtreleme](review-set-search.md#filter-partially-indexed-items)

      d. **SharePoint sürümü**: Koleksiyonda sürüm sınırları ve arama parametrelerine göre bir SharePoint belgesinin tüm sürümlerinin koleksiyonunu etkinleştirmek için bu seçeneği belirtin. Bu seçeneğin seçimi, gözden geçirme kümesine eklenen öğelerin boyutunu önemli ölçüde artırır. Belge sürümleri gözden geçirme kümesine eklendikten sonra, 

   4. Gözden geçirme kümesine eklemek istediğiniz koleksiyonun ölçeğini tanımlamak için ayarları yapılandırma:

      - **Tüm koleksiyon sonuçlarını ekleme**: Koleksiyonun arama ölçütlerine uyan tüm öğeleri gözden geçirme kümesine eklemek için bu seçeneği belirtin.

      - **Koleksiyon sonuçlarından bir örnek ekleme**: Tüm sonuçları eklemek yerine, gözden geçirme kümesine koleksiyon sonuçlarından bir örnek eklemek için bu seçeneği belirtin. Bu seçeneği belirtirseniz, Örnek parametreleri **düzenle'ye** tıklayın ve aşağıdaki seçeneklerden birini belirtin:

         - **Güvene dayalı** örnek: Koleksiyondaki öğeler gözden geçirme kümesine eklenir ve bu öğeler ayarlandır koleksiyonunun istatistiksel parametreleri tarafından belirlenir. Sonuçları örneklemek için normalde bir güven düzeyi ve aralık kullanıyorsanız, bunları açılan kutularda belirtin. Aksi takdirde, varsayılan ayarları kullanın.

         - **Rastgele örnek**: Koleksiyondaki öğeler, arama tarafından döndürülen toplam öğe sayısının belirtilen yüzdesinin rastgele seçimine bağlı olarak gözden geçirme kümesine eklenir.

6. Koleksiyonunızı **gözden geçirme** sayfasında, önceki sayfada yapılandırılan koleksiyon ayarlarını gözden geçirebilirsiniz. Değiştirmek **için** Düzenle'ye tıklayın.

7. Taslak **koleksiyonunu oluşturmak** için Gönder'e tıklayın. Koleksiyonun oluşturulmuş olduğunu onaylayan bir sayfa görüntülenir.

## <a name="what-happens-after-you-commit-a-draft-collection"></a>Taslak koleksiyonu işlerken ne olur?

Taslak koleksiyonunu gözden geçirme kümesine işlerken, aşağıdaki şeyler olur:

- Koleksiyonu işlemek için yeni bir gözden geçirme kümesi oluşturduysanız, gözden geçirme kümesi oluşturulur ve olayda **Gözden Geçir** kümeleri sekmesinde görüntülenir. Yeni gözden geçirme kümesi durumu **Hazır'dır**. Bu durum değeri, gözden geçirme kümesi oluşturulmuş anlamına gelir; koleksiyonun gözden geçirme kümesine eklenmiştir. Koleksiyondaki öğeleri gözden geçirme kümesine ekleme durumu Koleksiyonlar **sekmesinde** görüntülenir.

- Koleksiyon arama sorgusu yeniden çalıştırın. Bu, gözden geçirme kümesine kopyalanan gerçek arama sonuçlarının, koleksiyon araması en son çalıştırılamazken döndürülen tahmini sonuçlardan farklı olduğu anlamına gelir.

- Arama sonuçlarıdaki tüm öğeler canlı hizmette orijinal veri kaynağından kopyalanır ve Microsoft bulutunda güvenli bir Azure Depolama konuma kopyalanır.

- Koleksiyonu bir SharePoint gözden OneDrive göndermeniz, arama sonuçlarında döndürülen şifrelenmiş e-posta iletilerinin şifreleri ve şifreleri çözülmüş belge ve dosya eklidir. Gözden geçirme kümesinde şifresi çözülen dosyaları gözden geçirebilirsiniz ve sorgularsiniz. Daha fazla bilgi için bkz[. eK bulma Microsoft 365 Şifre Çözme.](ediscovery-decryption.md)

- Optik karakter tanıma (OCR) işlevi görüntülerden metin ayıklar ve resim metnini gözden geçirme kümesine eklenen içerikle birlikte içerir. Daha fazla bilgi için, bu [makaledeki Optik karakter](#optical-character-recognition) tanıma bölümüne bakın.

- Kaydetme başarıyla tamamlandıktan sonra, Koleksiyonlar sekmesindeki durum **sütununu** değeri olarak değiştirilir `Committed`.

## <a name="optical-character-recognition"></a>Optik karakter tanıma

Koleksiyonu bir gözden geçirme kümesine işlerken, Advanced eDiscovery'daki optik karakter tanıma (OCR) işlevi görüntülerden metinleri otomatik olarak ayıklar ve resim metnini gözden geçirme kümesine eklenen içeriği içerir. Ayıklanan metni gözden geçirme kümesinde, seçili resim dosyasının Metin görüntüleyicisinde görüntüleyebilirsiniz. Bu, resimlerde metin üzerinde daha fazla gözden geçirme ve çözümleme yürütmenizi sağlar. OCR kayıp dosyalar, e-posta ekleri ve ekli resimler için destekler. OCR tarafından desteklenen resim dosyası biçimlerinin listesi için bkz. OCR'de [desteklenen dosya Advanced eDiscovery](supported-filetypes-ediscovery20.md#image).

Yeni bir hesapta oluşturttğuz her olay için OCR işlevini Advanced eDiscovery. Daha fazla bilgi için bkz [. Arama ve çözümleme ayarlarını yapılandırma](configure-search-and-analytics-settings-in-advanced-ediscovery.md#optical-character-recognition-ocr).
