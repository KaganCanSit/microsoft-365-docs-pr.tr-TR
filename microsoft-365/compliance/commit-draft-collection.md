---
title: Bir inceleme setine taslak koleksiyon atama
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
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
description: Taslak koleksiyonu oluşturup yineledikten sonra, bir gözden geçirme kümesine işleyebilirsiniz. Taslak koleksiyonu işlediğinizde, toplanan öğeler servis talebindeki gözden geçirme kümesine eklenir. Toplanan öğeler gözden geçirme kümesinde yer aldıktan sonra bunları analiz edebilir, gözden geçirebilir ve dışarı aktarabilirsiniz.
ms.openlocfilehash: e635489383026df0d8097a300eb49178dcffb6b5
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66632717"
---
# <a name="commit-a-draft-collection-to-a-review-set-in-ediscovery-premium"></a>Taslak koleksiyonu eBulma'da (Premium) bir gözden geçirme kümesine işleme

Taslak koleksiyonda topladığınız öğelerden memnun olduğunuzda ve bunları analiz etmeye, etiketlemeye ve gözden geçirmeye hazır olduğunuzda, bu durumda bir gözden geçirme kümesine koleksiyon ekleyebilirsiniz. Taslak koleksiyonu bir gözden geçirme kümesine işlediğinizde, toplanan öğeler Microsoft 365'teki özgün içerik konumundan bir gözden geçirme kümesine kopyalanır. Gözden geçirme kümesi, Microsoft bulutunda Microsoft tarafından sağlanan güvenli bir Azure Depolama konumudur.

## <a name="commit-a-draft-collection-to-a-review-set"></a>Bir inceleme setine taslak koleksiyon atama

1. Microsoft Purview uyumluluk portalı Microsoft Purview eKeşif (Premium) servis talebini açın ve ardından koleksiyonların listesini görüntülemek için **Koleksiyonlar** sekmesini seçin.

   ![Bir durumdaki koleksiyonların listesi.](../media/CommitDraftCollections1.png)

   > [!TIP]
   > **Durum** sütunundaki değeri`Estimated`, gözden geçirme kümesine eklenebilen taslak koleksiyonları tanımlar. durumu `Committed` , bir koleksiyonun bir gözden geçirme kümesine zaten eklendiğini gösterir.

2. **Koleksiyonlar** sayfasında, gözden geçirme kümesine işlemek istediğiniz taslak koleksiyonu seçin.

3. Açılır sayfanın en altında **Eylemler** > **Koleksiyonu düzenle'yi** seçin.

4. Koleksiyonu düzenleme sihirbazında, **Taslağı kaydet veya topla** sayfası görüntülenene kadar **İleri'ye** tıklayın.

5. Aşağıdaki ayarları yapılandırın:

   1. **Öğeleri topla'yı seçin ve gözden geçirme kümesine ekleyin**.

   2. Koleksiyonu yeni bir gözden geçirme kümesine mi (siz koleksiyonu gönderdikten sonra oluşturulur) yoksa mevcut bir gözden geçirme kümesine mi ekleyeceğinize karar verin. Kararınıza bağlı olarak bu bölümü tamamlayın.

   3. Ek koleksiyon ayarlarını yapılandırın:

      ![Ek koleksiyon ayarlarını yapılandırın.](../media/AeDAdditionalCollectionSettings.png).

       a. **Teams ve Yammer iletileri**: Koleksiyondaki arama sorgusu tarafından döndürülen sohbet öğelerini içeren konuşma yazışmalarını koleksiyona eklemek için bu seçeneği belirleyin. Bu, arama ölçütlerine uyan öğeleri içeren sohbet konuşmasının yeniden yapılandırıldığını gösterir. Bu, sohbet öğelerini ileri geri konuşma bağlamında gözden geçirmenizi sağlar. Daha fazla bilgi için bkz. [eBulma'da konuşma yazışması oluşturma (Premium)](conversation-review-sets.md).

       b. **Bulut ekleri**: Koleksiyon sonuçları gözden geçirme kümesine eklendiğinde modern ekleri veya bağlı dosyaları dahil etmek için bu seçeneği belirleyin. Bu, modern bir ekin veya bağlı dosyanın hedef dosyasının gözden geçirme kümesine eklendiği anlamına gelir.

       > [!NOTE]
       > Bağlamsal Teams ve Yammer iletilerini ve bulut eklerini toplamaya yönelik iki seçenek, yeni servis talebi biçimi kullanılarak oluşturulan durumlar için varsayılan olarak seçilidir (ve gri görünür). Daha fazla bilgi için bkz. [Yeni durum biçimini kullanma](advanced-ediscovery-new-case-format.md).

       c. **Kısmen dizinlenmiş öğeler**: Gözden geçirme kümesine ek veri kaynaklarından kısmen dizinlenmiş öğeler eklemek için bu seçeneği belirleyin. Koleksiyon ek veri kaynakları aradıysa (koleksiyonlar sihirbazındaki **Ek konumlar** sayfasında belirtildiği gibi), bu konumlardan gözden geçirme kümesine eklemek istediğiniz kısmen dizine alınan öğeler olabilir. Gözetim ve gözetim dışı veri kaynakları genellikle kısmen dizine alınan öğelere sahip değildir. Bunun nedeni, Bir servis talebine gözetim ve gözetim dışı veri kaynakları eklendiğinde Gelişmiş dizin oluşturma işleminin öğeleri yeniden dizine eklemesidir. Ayrıca, kısmen dizinlenmiş öğeler eklemek, gözden geçirme kümesine eklenen öğe sayısını artırır. <p> Kısmen dizinlenmiş öğeler gözden geçirme kümesine eklendikten sonra, bu öğeleri özellikle görüntülemek için bir filtre uygulayabilirsiniz. Daha fazla bilgi için bkz [. Kısmen dizinlenmiş öğeleri filtreleme](review-set-search.md#filter-partially-indexed-items)

      d. **SharePoint sürümleri**: Koleksiyonun sürüm sınırları ve arama parametrelerine göre bir SharePoint belgesinin tüm sürümlerinin toplanmasını etkinleştirmek için bu seçeneği belirleyin. Bu seçeneğin belirtilmesi, gözden geçirme kümesine eklenen öğelerin boyutunu önemli ölçüde artırır. Belge sürümleri gözden geçirme kümesine eklendikten sonra, 

   4. Gözden geçirme kümesine eklenecek koleksiyonun ölçeğini tanımlamak için ayarları yapılandırın:

      - **Tüm koleksiyon sonuçlarını ekle**: Koleksiyonun arama ölçütlerine uyan tüm öğeleri gözden geçirme kümesine eklemek için bu seçeneği belirleyin.

      - **Koleksiyon sonuçlarından bir örnek ekleyin**: Tüm sonuçları eklemek yerine koleksiyon sonuçlarının bir örneğini gözden geçirme kümesine eklemek için bu seçeneği belirleyin. Bu seçeneği belirlerseniz **Örnek parametreleri düzenle'ye** tıklayın ve aşağıdaki seçeneklerden birini belirleyin:

         - **Güvene dayalı örnek**: Koleksiyondaki öğeler gözden geçirme kümesine eklenir, ayarladığınız istatistiksel parametreler tarafından belirlenir. Sonuçları örnekleme sırasında genellikle bir güvenilirlik düzeyi ve aralık kullanıyorsanız, bunları açılan kutularda belirtin. Aksi takdirde varsayılan ayarları kullanın.

         - **Rastgele örnek**: Koleksiyondaki öğeler, arama tarafından döndürülen toplam öğe sayısının belirtilen yüzdesinin rastgele seçimine göre gözden geçirme kümesine eklenir.

6. **Koleksiyonunuzu gözden geçirin** sayfasında, önceki sayfada yapılandırdığınız koleksiyon ayarlarını gözden geçirebilirsiniz. Değiştirmek istiyorsanız **Düzenle'ye** tıklayın.

7. Taslak koleksiyonu oluşturmak için **Gönder'e** tıklayın. Koleksiyonun oluşturulduğunu onaylayan bir sayfa görüntülenir.

## <a name="what-happens-after-you-commit-a-draft-collection"></a>Taslak koleksiyon işledikten sonra ne olur?

Bir gözden geçirme kümesine taslak koleksiyon işlediğiniz zaman aşağıdaki işlemler gerçekleşir:

- Koleksiyonun işleneceği yeni bir gözden geçirme kümesi oluşturduysanız, inceleme kümesi oluşturulur ve bu durumda **Gözden geçirme kümeleri** sekmesinde görüntülenir. Yeni gözden geçirme kümesinin durumu **Hazır'dır**. Bu durum değeri, gözden geçirme kümesinin oluşturulduğu anlamına gelir; bu, koleksiyonun gözden geçirme kümesine eklendiği anlamına gelmez. Koleksiyondaki öğeleri gözden geçirme kümesine ekleme durumu **Koleksiyonlar** sekmesinde görüntülenir.

- Koleksiyon arama sorgusu yeniden çalıştırılır. Bu, gözden geçirme kümesine kopyalanan gerçek arama sonuçlarının koleksiyon araması son çalıştırıldığında döndürülen tahmini sonuçlardan farklı olabileceği anlamına gelir.

- Arama sonuçlarındaki tüm öğeler canlı hizmetteki özgün veri kaynağından kopyalanır ve Microsoft bulutunda güvenli bir Azure Depolama konumuna kopyalanır.

- Şifrelenmiş SharePoint ve OneDrive belgeleri ile arama sonuçlarında döndürülen e-posta iletilerinin eklendiği şifrelenmiş dosyaların şifresi, koleksiyonu bir gözden geçirme kümesine kaydettiğinizde çözülür. Şifresi çözülen dosyaları gözden geçirip gözden geçirme kümesinde sorgulayabilirsiniz. Daha fazla bilgi için bkz [. Microsoft 365 eKeşif araçlarında şifre çözme](ediscovery-decryption.md).

- Optik karakter tanıma (OCR) işlevi görüntülerden metin ayıklar ve bir inceleme kümesine eklenen içeriği içeren görüntü metnini içerir. Daha fazla bilgi için bu makaledeki [Optik karakter tanıma](#optical-character-recognition) bölümüne bakın.

- İşleme başarıyla tamamlandıktan sonra **Koleksiyonlar** sekmesindeki durum sütununun değeri olarak `Committed`değiştirilir.

## <a name="optical-character-recognition"></a>Optik karakter tanıma

Bir koleksiyonu bir gözden geçirme kümesine işlediğinizde, eKeşif (Premium) içindeki optik karakter tanıma (OCR) işlevi görüntülerden otomatik olarak metin ayıklar ve bir gözden geçirme kümesine eklenen içeriği içeren görüntü metnini içerir. Ayıklanan metni, gözden geçirme kümesindeki seçili görüntü dosyasının Metin görüntüleyicisinde görüntüleyebilirsiniz. Bu sayede görüntülerdeki metinler üzerinde daha fazla inceleme ve analiz gerçekleştirebilirsiniz. OCR gevşek dosyalar, e-posta ekleri ve ekli görüntüler için desteklenir. OCR için desteklenen görüntü dosyası biçimlerinin listesi için bkz. [eBulma'da desteklenen dosya türleri (Premium)](supported-filetypes-ediscovery20.md#image).

eBulma'da (Premium) oluşturduğunuz her servis talebi için OCR işlevselliğini etkinleştirmeniz gerekir. Daha fazla bilgi için bkz. [Arama ve analiz ayarlarını yapılandırma](configure-search-and-analytics-settings-in-advanced-ediscovery.md#optical-character-recognition-ocr).
