---
title: Bir inceleme setine taslak koleksiyon atama
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
description: Taslak koleksiyonu oluşturup yineledikten sonra, bir gözden geçirme kümesine işleyebilirsiniz. Taslak koleksiyonu işlediğinizde, toplanan öğeler servis talebindeki gözden geçirme kümesine eklenir. Toplanan öğeler gözden geçirme kümesinde yer aldıktan sonra bunları analiz edebilir, gözden geçirebilir ve dışarı aktarabilirsiniz.
ms.openlocfilehash: 5637d97020d7fb086914a6debdaffc8050772828
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/19/2022
ms.locfileid: "64940301"
---
# <a name="commit-a-draft-collection-to-a-review-set-in-ediscovery-premium"></a>Taslak koleksiyonu eBulma'da (Premium) bir gözden geçirme kümesine işleme

Taslak koleksiyonda topladığınız öğelerden memnun olduğunuzda ve bunları analiz etmeye, etiketlemeye ve gözden geçirmeye hazır olduğunuzda, bu durumda bir gözden geçirme kümesine koleksiyon ekleyebilirsiniz. Bir gözden geçirme kümesine taslak koleksiyon işlediğinizde, toplanan öğeler Microsoft 365'daki özgün içerik konumlarından bir gözden geçirme kümesine kopyalanır. Gözden geçirme kümesi, Microsoft tarafından sağlanan güvenli bir Azure Depolama Microsoft bulutu konumudur.

## <a name="commit-a-draft-collection-to-a-review-set"></a>Bir inceleme setine taslak koleksiyon atama

1. Microsoft Purview uyumluluk portalında Microsoft Purview eKeşif (Premium) servis talebini açın ve ardından koleksiyonların bir listesini görüntülemek için **Koleksiyonlar** sekmesini seçin.

   ![Bir durumdaki koleksiyonların listesi.](../media/CommitDraftCollections1.png)

   > [!TIP]
   > **Durum** sütunundaki değeri`Estimated`, gözden geçirme kümesine eklenebilen taslak koleksiyonları tanımlar. durumu `Committed` , bir koleksiyonun bir gözden geçirme kümesine zaten eklendiğini gösterir.

2. **Koleksiyonlar** sayfasında, gözden geçirme kümesine işlemek istediğiniz taslak koleksiyonu seçin.

3. Açılır sayfanın alt kısmında **Eylemler** >  **Koleksiyonu düzenle'yi** seçin.

4. Koleksiyonu düzenleme sihirbazında, **Taslağı kaydet veya topla** sayfası görüntülenene kadar **İleri'ye** tıklayın.

5. Aşağıdaki ayarları yapılandırın:

   1. **Öğeleri topla'yı seçin ve gözden geçirme kümesine ekleyin**.

   2. Koleksiyonu yeni bir gözden geçirme kümesine mi (siz koleksiyonu gönderdikten sonra oluşturulur) yoksa mevcut bir gözden geçirme kümesine mi ekleyeceğinize karar verin. Kararınıza bağlı olarak bu bölümü tamamlayın.

   3. Ek koleksiyon ayarlarını yapılandırın:

      ![Ek koleksiyon ayarlarını yapılandırın.](../media/AeDAdditionalCollectionSettings.png).

       a. **İletileri Teams ve Yammer**: Koleksiyondaki arama sorgusu tarafından döndürülen sohbet öğelerini içeren koleksiyona konuşma yazışmaları eklemek için bu seçeneği belirleyin. Bu, arama ölçütlerine uyan öğeleri içeren sohbet konuşmasının yeniden yapılandırıldığını gösterir. Bu, sohbet öğelerini ileri geri konuşma bağlamında gözden geçirmenizi sağlar. Daha fazla bilgi için bkz[. eBulmada konuşma yazışması (Premium)](conversation-review-sets.md).

       b. **Bulut ekleri**: Koleksiyon sonuçları gözden geçirme kümesine eklendiğinde modern ekleri veya bağlı dosyaları dahil etmek için bu seçeneği belirleyin. Bu, modern bir ekin veya bağlı dosyanın hedef dosyasının gözden geçirme kümesine eklendiği anlamına gelir.

       > [!NOTE]
       > Bağlamsal Teams ve Yammer iletileri ve bulut eklerini toplamaya yönelik iki seçenek, yeni büyük/küçük harf biçimi kullanılarak oluşturulan durumlar için varsayılan olarak seçilidir (ve gri gösterilir). Daha fazla bilgi için bkz. [Yeni durum biçimini kullanma](advanced-ediscovery-new-case-format.md).

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

- Şifrelenmiş SharePoint ve OneDrive belgeleri ve arama sonuçlarında döndürülen e-posta iletileri eklenmiş şifrelenmiş dosyaların şifresi, koleksiyonu bir gözden geçirme kümesine işlediğinizde çözülür. Şifresi çözülen dosyaları gözden geçirip gözden geçirme kümesinde sorgulayabilirsiniz. Daha fazla bilgi için bkz[. Microsoft 365 eBulma araçlarında şifre çözme](ediscovery-decryption.md).

- Optik karakter tanıma (OCR) işlevi görüntülerden metin ayıklar ve bir inceleme kümesine eklenen içeriği içeren görüntü metnini içerir. Daha fazla bilgi için bu makaledeki [Optik karakter tanıma](#optical-character-recognition) bölümüne bakın.

- İşleme başarıyla tamamlandıktan sonra **Koleksiyonlar** sekmesindeki durum sütununun değeri olarak `Committed`değiştirilir.

## <a name="optical-character-recognition"></a>Optik karakter tanıma

Bir koleksiyonu bir gözden geçirme kümesine işlediğinizde, eBulma'daki (Premium) optik karakter tanıma (OCR) işlevi görüntülerden otomatik olarak metin ayıklar ve bir gözden geçirme kümesine eklenen içeriği içeren görüntü metnini içerir. Ayıklanan metni, gözden geçirme kümesindeki seçili görüntü dosyasının Metin görüntüleyicisinde görüntüleyebilirsiniz. Bu sayede görüntülerdeki metinler üzerinde daha fazla inceleme ve analiz gerçekleştirebilirsiniz. OCR gevşek dosyalar, e-posta ekleri ve ekli görüntüler için desteklenir. OCR için desteklenen görüntü dosyası biçimlerinin listesi için bkz. [eBulma'da desteklenen dosya türleri (Premium)](supported-filetypes-ediscovery20.md#image).

eBulma'da (Premium) oluşturduğunuz her servis talebi için OCR işlevselliğini etkinleştirmeniz gerekir. Daha fazla bilgi için bkz. [Arama ve analiz ayarlarını yapılandırma](configure-search-and-analytics-settings-in-advanced-ediscovery.md#optical-character-recognition-ocr).
