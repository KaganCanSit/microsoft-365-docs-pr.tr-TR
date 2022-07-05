---
title: Microsoft SharePoint Syntex'de form işleme modeli oluşturma
ms.author: chucked
author: chuckedmonson
manager: pamgreen
ms.reviewer: ssquires
audience: admin
ms.topic: article
ms.prod: microsoft-365-enterprise
search.appverid: ''
ms.collection:
- enabler-strategic
- m365initiative-syntex
ms.custom: admindeeplinkSPO
ms.localizationpriority: medium
description: SharePoint Syntex'de form işleme modeli oluşturmayı öğrenin.
ms.openlocfilehash: b44dc34b2b57c75f5fefea074cd74fa0b686bcaa
ms.sourcegitcommit: 44ece87e3e0c0c851dfc1e77211ac3e5e4a5b973
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/05/2022
ms.locfileid: "66617226"
---
# <a name="create-a-form-processing-model-in-microsoft-sharepoint-syntex"></a>Microsoft SharePoint Syntex'de form işleme modeli oluşturma

</br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4GnhN]  

</br>

Microsoft Power Apps'teki bir özellik olan [AI Builder'ı](/ai-builder/overview) kullanma SharePoint Syntex kullanıcılar doğrudan bir SharePoint belge kitaplığından [form işleme modeli](form-processing-overview.md) oluşturabilir. 

Form işleme modeli oluşturmak aşağıdaki adımları içerir:

 - [1. Adım: Form işleme modeli oluşturma](create-a-form-processing-model.md#step-1-create-a-form-processing-model)
 - [2. Adım: Belgeleri ekleme ve analiz etme](create-a-form-processing-model.md#step-2-add-and-analyze-documents)
 - [3. Adım: Alanları ve tabloları etiketleme](create-a-form-processing-model.md#step-3-tag-fields-and-tables)
 - [4. Adım: Modelinizi eğitin ve yayımlayın](create-a-form-processing-model.md#step-4-train-and-publish-your-model)
 - [5. Adım: Modelinizi kullanma](create-a-form-processing-model.md#step-5-use-your-model)

## <a name="requirements"></a>Gereksinimler

Yalnızca etkin olduğu SharePoint belge kitaplıklarında form işleme modeli oluşturabilirsiniz. Form işleme etkinleştirildiyse, belge kitaplığınızdaki **Formları işlemek için AI Builder'ı** >  **Otomatik hale** > **getir Model oluştur** menüsünü görebilirsiniz. Belge kitaplığınızda işlemenin etkinleştirilmesi gerekiyorsa SharePoint yöneticinize başvurmanız gerekir.

![AI Builder modelini gösteren ekran görüntüsü.](../media/content-understanding/create-ai-builder-model2.png)

## <a name="step-1-create-a-form-processing-model"></a>1. Adım: Form işleme modeli oluşturma

Form işleme modeli oluşturmanın ilk adımı modeli adlandırmak, yeni içerik türünü tanımlamak ve bunun için yeni bir belge kitaplığı görünümü oluşturmaktır.

1. Belge kitaplığından **Otomatikleştir** menüsünü seçin, **AI Builder'ı** ve ardından **Formları işlemek için model oluştur'u** seçin.

    ![Otomatikleştir menüsünü ve Formları işlemek için model oluştur seçeneğini gösteren ekran görüntüsü.](../media/content-understanding/create-ai-builder-model2.png)

2. **Formları işlemek için model oluştur** panelindeki **Ad** alanına modeliniz için bir ad yazın (örneğin, *Satın Alma Siparişleri*).

    ![Formları işlemek için model oluşturma panelini gösteren ekran görüntüsü.](../media/content-understanding/new-form-model2.png) 

3. Artık, SharePoint belge kitaplığındaki faturalar veya vergi belgeleri gibi benzer bir düzeni paylaşan yapılandırılmış dosyalar *koleksiyonundan* bilgileri otomatik olarak ayıklayabilir ve kaydedebilirsiniz. Bu, tek bir modelde birkaç model oluşturmanıza ve belirli tablo öğesi bilgilerini ayıklamanıza olanak tanır.

   Koleksiyon adı, modelin uygulandığı belge kitaplığındaki ayrılmış bir sütuna kaydedilir ve bu da aynı model tarafından işlenen farklı dosya düzenlerini ayırt etmenizi sağlar.

   Ayrıca, ayıklanan tablo bilgileri belirtilen bir listeye kaydedilir ve kolay görüntüleme veya ek iş süreci otomasyonu için karşıya yüklenen dosyayla ilişkilendirilir.

   Tablo bilgilerini ilişkili bir listeye ayıklamak için:<br><br>

     1. **Tablolardan bilgi ayıklasın mı?** bölümünde **Evet'i** seçin.

      ![Formları işlemek için model oluşturma panelindeki Tablolardan bilgi ayıklama bölümünü gösteren ekran görüntüsü.](../media/content-understanding/extract-info-from-tables.png) 

     2. **Tablo bilgilerini nereye kaydetmemiz gerekiyor?** bölümünde:
 
        - **Yeni liste** 'yi (varsayılan ayar) seçerseniz **, Yeni liste adı** kutusunda otomatik olarak önerilen bir ad sağlanır. İsterseniz adı değiştirebilirsiniz. Listeyi site gezintisinde göstermek istiyorsanız Site **gezintisinde göster** onay kutusunu seçin.

        - **Var olan bir liste'yi** seçerseniz, **Seçili liste** kutusunda kullanmak istediğiniz listeyi seçin.

4. Form işleme modeli oluşturduğunuzda, yeni bir SharePoint içerik türü oluşturursunuz. SharePoint içerik türü, ortak özelliklere sahip bir belge kategorisini temsil eder ve söz konusu içerik için sütun veya meta veri özellikleri koleksiyonunu paylaşır. SharePoint içerik türleri <a href="https://go.microsoft.com/fwlink/?linkid=2185219" target="_blank">SharePoint yönetim merkezi</a> üzerinden yönetilir.

   Bu modeli SharePoint içerik türleri galerisindeki mevcut bir içerik türüyle eşlemek için **Gelişmiş ayarlar'ı** seçin.

    ![Formları işlemek için model oluşturma panelinde gelişmiş ayarları gösteren ekran görüntüsü.](../media/content-understanding/new-form-model-advanced-settings.png) 

   1. <a href="https://go.microsoft.com/fwlink/?linkid=2185074" target="_blank">İçerik türü galerisinde</a> yeni bir içerik türü oluşturmayı veya var olan bir içerik türünü kullanmayı seçin. 

   2. Mevcut bir içerik türünü kullanmak için **Birini seçin'i** seçin ve listeden bir içerik türü seçin.

   3. Modeliniz, ayıkladığınız veriler için belge kitaplığınızda yeni bir görünüm oluşturur. Varsayılan görünüm olmasını istemiyorsanız, **bu modelin Kitaplık görünümünde** Görünümü **varsayılan olarak ayarla** onay kutusunu temizleyin.

   4. Dosyalarınıza bekletme etiketi uygulamak için **Bekletme etiketi** bölümünde kullanmak istediğiniz bekletme etiketini seçin.

5. **Oluştur**’u seçin.

## <a name="step-2-add-and-analyze-documents"></a>2. Adım: Belgeleri ekleme ve analiz etme

Yeni form işleme modelinizi oluşturduktan sonra tarayıcınız yeni bir Power Apps AI Builder form işleme modeli sayfası açar. Bu sayfada, örnek belgelerinizi ekleyebilir ve çözümleyebilirsiniz. 

> [!NOTE]
> Kullanılacak örnek dosyaları aradığınızda, [form işleme modeli giriş belgesi gereksinimlerine ve iyileştirme ipuçlarına](/ai-builder/form-processing-model-requirements) bakın. 
 
1. İlk olarak modelinize ayıklamayı öğretmek istediğiniz alanları ve tabloları **Ayıklamak için bilgi seçin sayfasında tanımlarsınız** . Ayrıntılı adımlar için bkz. [Ayıklanması gereken alanları ve tabloları tanımlama](/ai-builder/create-form-processing-model#define-fields-and-tables-to-extract). 

2.  Modelinizin işlemesini istediğiniz kadar belge düzeni koleksiyonu oluşturabilirsiniz. Ayrıntılı adımlar için bkz. [Belgeleri koleksiyonlara göre gruplandırma](/ai-builder/create-form-processing-model#group-documents-by-collections). 

3. Koleksiyonlarınızı oluşturduktan ve her birine örnek dosyaları ekledikten sonra, AI Builder karşıya yüklenen belgeleri inceleyerek alanları ve tabloları algılar. Bu işlem genellikle birkaç dakika sürer. Analiz tamamlandığında, belgeleri etiketlemeye devam edebilirsiniz.

## <a name="step-3-tag-fields-and-tables"></a>3. Adım: Alanları ve tabloları etiketleme

Modele ayıklamak istediğiniz alanları ve tablo verilerini anlamasını öğretmek için belgeleri etiketlemeniz gerekir. Ayrıntılı adımlar için bkz. [Belgeleri etiketleme](/ai-builder/create-form-processing-model#tag-documents).

## <a name="step-4-train-and-publish-your-model"></a>4. Adım: Modelinizi eğitin ve yayımlayın

1. Modelinizi oluşturup eğittikkten sonra yayımlamaya ve SharePoint'te kullanmaya hazır olursunuz. Ayrıntılı adımlar için bkz. [Form işleme modelinizi eğitin ve yayımlayın](/ai-builder/form-processing-train). 

2. Model yayımlandıktan sonra **Modeli kullan'ı** ve ardından **Akış oluştur'u** seçin. Bu, SharePoint belge kitaplığınızda çalıştırabilen ve modelde tanımlanan alanları ayıklayan bir Power Automate akışı oluşturur.

    ![AI Builder'da Akış oluştur panelini gösteren ekran görüntüsü.](../media/content-understanding/ai-builder-create-a-flow-1.png)
 
3. Tamamlandığında şu iletiyi görürsünüz: *Akışınız başarıyla oluşturuldu*.

4. Belge kitaplığının modelinizle güncelleştirildiğini görmek için **SharePoint'e Git** düğmesini seçin.

## <a name="step-5-use-your-model"></a>5. Adım: Modelinizi kullanma

1. Belge kitaplığı modeli görünümünde, seçtiğiniz alanların artık sütun olarak görüntülendiğine dikkat edin.

    ![Belge kitaplığı modeli uygulandı.](../media/content-understanding/doc-lib-view.png)

2. **Belgeler'in** yanındaki bilgi bağlantısının bu belge kitaplığına form işleme modelinin uygulandığına dikkat edin.

    ![Bilgi düğmesi.](../media/content-understanding/info-button.png)  

3. Dosyaları belge kitaplığınıza yükleyin. Modelin içerik türü olarak tanımlamış olduğu tüm dosyalar, görünümünüzdeki dosyaları listeler ve ayıklanan verileri sütunlarda görüntüler.

    ![Yapılır.](../media/content-understanding/doc-lib-done.png) 

> [!NOTE]
> Aynı kitaplığa özel form işleme modeli ve belge anlama modeli uygulanırsa, dosya belge anlama modeli ve bu model için eğitilen ayıklayıcılar kullanılarak sınıflandırılır. Form işleme modeliyle eşleşen boş sütunlar varsa, bu ayıklanan değerler kullanılarak sütunlar doldurulur.

### <a name="use-flows-to-extract-information"></a>Bilgileri ayıklamak için akışları kullanma

Bir form işleme modelinin uygulandığı kitaplıkta seçili bir dosyayı veya dosya toplu işlemini işlemek için iki akış kullanılabilir.

- **Form işleme modeline sahip bir görüntüden veya PDF dosyasından bilgi ayıklama — Form işleme modeli** çalıştırarak seçili görüntüden veya PDF dosyasından metin ayıklamak için kullanın. Tek seferde tek bir seçili dosyayı destekler ve yalnızca PDF dosyalarını ve görüntü dosyalarını (PNG, JPG ve JPEG) destekler. Akışı çalıştırmak için bir dosya seçin ve ardından **Bilgileri ayıklamayı** **otomatikleştir'i** >  seçin.

    ![Bilgileri ayıkla seçeneğinin vurgulandığı Otomatikleştir menüsünü gösteren ekran görüntüsü.](../media/content-understanding/automate-extract-info.png)  

- **Form işleme modeline sahip dosyalardan bilgi ayıklama** — Bir grup dosyadan bilgi okumak ve ayıklamak için form işleme modelleriyle kullanın. Aynı anda en fazla 5.000 SharePoint dosyasını işler. Bu akışı çalıştırdığınızda ayarlayabileceğiniz bazı parametreler vardır. Şunları yapabilirsiniz:

    - Önceden işlenen dosyaların dahil edilip edilmeyeceğini seçin (varsayılan ayar, önceden işlenen dosyaları dahil etmek değildir).
    - İşlenmek üzere dosya sayısını seçin (varsayılan değer 100 dosyadır).
    - Dosyaların işlenme sırasını belirtin (seçenekler dosya kimliğine, dosya adına, dosya oluşturma zamanına veya son değiştirme zamanına göredir).
    - Düzenin nasıl sıralanmasını istediğinizi belirtin (artan veya azalan düzen).

    ![Parametre seçeneklerinin vurgulandığı Akışı çalıştır panelini gösteren ekran görüntüsü.](../media/content-understanding/run-flow-panel.png)  
    
> [!NOTE]
> **Form işleme modeli akışına sahip bir görüntüden veya PDF dosyasından bilgi ayıkla**, bir form işleme modeliyle ilişkilendirilmiş bir kitaplık için otomatik olarak kullanılabilir. **Form işleme modeline sahip dosyalardan bilgi ayıkla** akışı, gerekirse kitaplığa eklenmesi gereken bir şablondur.

### <a name="classification-date-field"></a>Sınıflandırma Tarihi alanı

Belge kitaplığına bir SharePoint Syntex form işleme modeli (veya belge anlama modeli) uygulandığında, **Sınıflandırma Tarihi** alanı kitaplık şemasına eklenir. Varsayılan olarak, bu alan boş olur. Ancak, belgeler bir model tarafından işlendiğinde ve sınıflandırıldığında, bu alan tamamlanma tarih-saat damgasıyla güncelleştirilir. 

Model **Sınıflandırma Tarihi** ile damgalandığında, Kullanıcılara SharePoint belge kitaplığındaki bir model tarafından yeni bir dosyanın işlendiğini ve sınıflandırıldığını bildirmek için **SharePoint Syntex dosya akışını işledikten sonra e-posta gönder'i** kullanabilirsiniz.

Akışı çalıştırmak için:

1. Bir dosya seçin ve ardından **Power Automate'i tümleştir** >  >  **Akış oluştur'u** seçin.

2. **Akış oluştur** panelinde, **SharePoint Syntex bir dosyayı işledikten sonra e-posta gönder'i** seçin.

    ![Akış oluştur panelini ve akış seçeneğinin vurgulandığı ekran görüntüsü.](../media/content-understanding/integrate-create-flow.png) 

## <a name="see-also"></a>Ayrıca bkz.
  
[Power Automate belgeleri](/power-automate/)

[Eğitim: AI Builder ile iş performansını geliştirme](/learn/paths/improve-business-performance-ai-builder/?source=learn)
