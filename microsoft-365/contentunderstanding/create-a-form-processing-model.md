---
title: Microsoft SharePoint Syntex'da form işleme modeli oluşturma
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
ms.localizationpriority: medium
description: aynı dosyada form işleme modeli SharePoint Syntex.
ms.openlocfilehash: b6ccede1de62fbba0e111eb7d9d805b4998e9652
ms.sourcegitcommit: 6c57f1e90339d5a95c9e7875599dac9d3e032c3a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/04/2022
ms.locfileid: "63016435"
---
# <a name="create-a-form-processing-model-in-microsoft-sharepoint-syntex"></a>Microsoft SharePoint Syntex'da form işleme modeli oluşturma

</br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4GnhN]  

</br>

Microsoft Power Apps' da bir özellik olan [AI Builder](/ai-builder/overview) SharePoint Syntex kullanarak, kullanıcılar doğrudan SharePoint belge kitaplığından form işleme [](form-processing-overview.md) modeli oluşturabilir. 

Form işleme modeli oluşturma işlemi aşağıdaki adımları içerir:

 - [1. Adım: Form işleme modeli oluşturma](create-a-form-processing-model.md#step-1-create-a-form-processing-model)
 - [2. Adım: Belgeleri ekleme ve çözümleme](create-a-form-processing-model.md#step-2-add-and-analyze-documents)
 - [3. Adım: Alanları ve tabloları etiketleme](create-a-form-processing-model.md#step-3-tag-fields-and-tables)
 - [4. Adım: Modelinizi eğitin ve yayımlayın](create-a-form-processing-model.md#step-4-train-and-publish-your-model)
 - [5. Adım: Modelinizi kullanma](create-a-form-processing-model.md#step-5-use-your-model)

## <a name="requirements"></a>Gereksinimler

Form işleme modelini yalnızca etkinleştirilmiş SharePoint kitaplıklarında oluşturabilirsiniz. Form işleme etkinleştirildiyse, Belge kitaplığınız içinde Formları işleme için **bir model** oluşturma **AutomateAI** >  **Builder'ın** >  bunu yapabilirsiniz. Belge kitaplığında işlemenin etkinleştirilmesi gerekirse, sistem yöneticinize SharePoint gerekir.

 ![AI Oluşturucu modelini gösteren ekran görüntüsü.](../media/content-understanding/create-ai-builder-model2.png)

## <a name="step-1-create-a-form-processing-model"></a>1. Adım: Form işleme modeli oluşturma

Form işleme modeli oluşturmanın ilk adımı, modeli isimlerini, yeni içerik türünü tanımlamak ve bunun için yeni bir belge kitaplığı görünümü oluşturmaktır.

1. Belge kitaplığından Otomatik başlat menüsünü seçin, **AI Oluşturucusu'nu** seçin ve ardından formları **işlemesi için model oluştur'a tıklayın**.

    ![Otomatikleştir menüsünü ve Formları işlemeye model oluştur seçeneğini gösteren ekran görüntüsü.](../media/content-understanding/create-ai-builder-model2.png)

2. Formlar **için işlem yapmak için model** oluştur panelinde, **Ad** alanına modeliniz için bir ad yazın ( *örneğin, Satın* Alma Siparişleri).

    ![Formlar için model oluştur panelini gösteren ekran görüntüsü.](../media/content-understanding/new-form-model2.png) 

3. Artık, faturalar veya vergi belgeleri gibi benzer bir  düzeni paylaşan yapılandırılmış dosyalar koleksiyonundan, bir belge kitaplığında yer alan bilgileri otomatik olarak ayık SharePoint kaydedebilirsiniz. Bu, birkaç modeli tek bir model olarak oluşturma ve belirli tablo öğesi bilgilerini ayıklamana olanak sağlar.

   Koleksiyon adı, modelin uygulandığı belge kitaplığında ayrılmış bir sütuna kaydedilir ve bu da aynı model tarafından işlenen farklı dosya düzenlerini ayırt etmek için size olanak sağlar.

   Buna ek olarak, ayıklanan tablo bilgileri belirtilen bir listeye kaydedilir ve daha kolay görüntülemek veya ek iş süreci otomasyonu için karşıya yüklenen dosyayla ilişkilendirilır.

   Tablo bilgilerini ilişkili listeye ayıklamak için:<br><br>

     1. Tablolardan **bilgi ayıkla? bölümünde** Evet'i **seçin**.

      ![Formları işlemeye model oluşturma panelinde Tablolardan bilgi ayıklama bölümünü gösteren ekran görüntüsü.](../media/content-understanding/extract-info-from-tables.png) 

     2. Tablo **bilgilerini nereye kaydetmemiz gerekir? bölümünde** :
 
        - Yeni bir **liste (varsayılan ayar** ) seçeneğini kullanırsanız, Yeni liste adı kutusunda otomatik **olarak önerilen bir ad** sağlanır. 20102'de, istediğiniz zaman adı değiştirebilirsiniz. Listeyi site gezintisinde göstermek için, Site gezintisinde **göster onay** kutusunu seçin.

        - Varolan bir **liste'yi** seçerseniz **, Seçili liste** kutusunda kullanmak istediğiniz listeyi seçin.

4. Form işleme modeli  oluşturma işlemi sırasında, yeni bir içerik SharePoint oluşturmanız gerekir. İçerik SharePoint türü, ortak özelliklere sahip olan ve bu belirli içerik için sütun veya meta veri özellikleri koleksiyonunu paylaşan bir belge kategorisini temsil eder. SharePoint türleri yönetim merkezinden SharePoint yönetilir.

   Bu modeli, İçerik Türleri galerisinde var olan bir içerik SharePoint eşlemek için Gelişmiş **ayarlar'ı seçin**.

    ![Formlar için model oluştur panelinde Gelişmiş ayarları gösteren ekran görüntüsü.](../media/content-understanding/new-form-model-advanced-settings.png) 

   1. İçerik **türü bölümünde** , yeni içerik türü oluşturmak mı yoksa var olan içerik türünü kullanmak mı istediğinize karar seçin. 

   2. Var olan bir içerik türünü kullanmak için Birini **seç'i** seçin ve sonra da listeden bir içerik türü seçin.

   3. Modeliniz, ayıklanan verileriniz için belge kitaplığında yeni bir görünüm oluşturur. Varsayılan görünüm olarak ayarlamak istemiyorsanız, Bu **modelin** Kitaplık görünümünde, Görünümü varsayılan olarak **ayarla onay kutusunu** temizleyin.

   4. Dosyalarınıza bekletme etiketi uygulamak için, Bekletme etiketi bölümünde,  kullanmak istediğiniz bekletme etiketini seçin.

5. **Oluştur**’u seçin.

## <a name="step-2-add-and-analyze-documents"></a>2. Adım: Belgeleri ekleme ve çözümleme

Yeni form işleme modelinizi oluşturduktaktan sonra, tarayıcınız yeni bir AI Builder Power Apps işleme modeli sayfası açar. Bu sayfada örnek belgelerinizi ekleyebilir ve çözümleyebilirsiniz. 

> [!NOTE]
> Kullanmak istediğiniz örnek dosyaları bu dosyalar için bkz. form işleme [modeli giriş belgesi gereksinimleri ve iyileştirme ipuçları](/ai-builder/form-processing-model-requirements). 
 
1. Önce, Ayıklamak istediğiniz bilgileri seçin sayfasında modelinize ayıklamak istediğiniz **alanları ve tabloları tanımlarsiniz** . Ayrıntılı adımlar için bkz. [Ayıklayılacak alanları ve tabloları tanımlama](/ai-builder/create-form-processing-model#define-fields-and-tables-to-extract). 

2.  Modelinizin işlemesinde istediğiniz kadar çok belge düzeni koleksiyonu oluşturabilirsiniz. Ayrıntılı adımlar için bkz. [Belgeleri koleksiyonlara göre grupla](/ai-builder/create-form-processing-model#group-documents-by-collections). 

3. Koleksiyonlarınızı oluşturduklardan ve her biri için örnek dosyaları ekledikten sonra, AI Builder karşıya yüklenen belgeleri inceler ve alanları ve tabloları algılar. Bu genellikle birkaç dakika sürer. Çözümleme tamamlandığında, belgeleri etiketlemeye devam edebilirsiniz.

## <a name="step-3-tag-fields-and-tables"></a>3. Adım: Alanları ve tabloları etiketleme

Modele, ayıklamak istediğiniz alanları ve tablo verilerini an öğretecek şekilde belgeleri etiketlemeniz gerekir. Ayrıntılı adımlar için bkz. [Belgeleri etiketleme](/ai-builder/create-form-processing-model#tag-documents).

## <a name="step-4-train-and-publish-your-model"></a>4. Adım: Modelinizi eğitin ve yayımlayın

1. Modelinizi oluşturduk ve eğitdikten sonra, modelinizi yayımlamaya ve aynı anda SharePoint. Ayrıntılı adımlar için bkz [. Form işleme modelinizi eğitin ve yayımlayın](/ai-builder/form-processing-train). 

2. Model yayımlandıktan sonra Modeli **kullan'ı ve ardından** Akış oluştur'ı **seçin**. Bu, Power Automate kitaplığında çalıştırabilirsiniz SharePoint ve modelde tanımlanan alanları ayıklar.

    ![Akış oluşturma panelini gösteren AI Builder ekran görüntüsü.](../media/content-understanding/ai-builder-create-a-flow.png)
 
3. Tamamlandığında, şu iletiyi görüntülersiniz: *Akışınız başarıyla oluşturuldu*.

    ![AI Builder'da akışı gösteren ekran görüntüsü başarıyla oluşturuldu.](../media/content-understanding/ai-builder-flow-created.png)

4. Belge **kitaplığının modelinize uygun SharePoint** için Belge Kitaplığına Git düğmesini seçin.

## <a name="step-5-use-your-model"></a>5. Adım: Modelinizi kullanma

1. Belge kitaplığı modeli görünümünde, seçtiğiniz alanların artık sütunlar olarak görüntüleniyor olduğunu fark edin.

    ![Uygulanan belge kitaplığı modeli.](../media/content-understanding/doc-lib-view.png)

2. Belgeler notlarının yanındaki bilgi **bağlantısında** , form işleme modelinin bu belge kitaplığına uygulandığına dikkat edin.

    ![Bilgi düğmesi.](../media/content-understanding/info-button.png)  

3. Upload kitaplığınıza dosya ekleyin. Modelin içerik türü olarak tanımları tüm dosyalar, sizin görünümde dosyaları listeler ve ayıklanan verileri sütunlarda görüntüler.

    ![Bitti.](../media/content-understanding/doc-lib-done.png) 

> [!NOTE]
> Aynı kitaplı kitaplara özel form işleme modeli ve belge anlama modeli uygulanmışsa, dosya, belge anlama modeli ve bu model için eğitimli ayıklama modellerini kullanarak sınıflandırılır. Form işleme modeliyle eşleşmeye devam eden boş sütunlar varsa, sütunlar bu ayıklanan değerler kullanılarak doldurulur.

### <a name="use-flows-to-extract-information"></a>Bilgileri ayıklamak için akışları kullanma

Form işleme modelinin uygulandığı bir kitaplıkta seçilen dosyayı veya toplu dosyaları işleme için iki akış vardır.

- **Form işleme modeli olan bir resim veya PDF** dosyasından bilgi ayıklama — Form işleme modelini çalıştırarak seçili resim veya PDF dosyasından metin ayıklamak için kullanın. Bir defada tek bir seçili dosyayı destekler ve yalnızca PDF dosyalarıyla resim dosyalarını (PNG, JPG ve JPEG) destekler. Akışı çalıştırmak için bir dosya seçin ve ardından **AutomateExtract** >  info öğesini seçin.

    ![Bilgileri ayıkla seçeneğinin vurgulu olduğu Otomatikleştir menüsünü gösteren ekran görüntüsü.](../media/content-understanding/automate-extract-info.png)  

- **Form işleme modeliyle dosyalardan bilgi ayıklama** — Bir grup dosyadan alınan bilgileri okumak ve ayıklamak için form işleme modelleriyle kullanın. Bir defada en çok 5.000 SharePoint dosya işler. Bu akışı çalıştıracakken, ayar ola bir dizi parametre vardır. Şunları yapabilirsiniz:

    - Daha önce işlenen dosyaların eklenerek ek gerekip gerekmeyeceklerini seçin (varsayılan değer daha önce işlenen dosyaları dahil etmek değildir).
    - İşlem için dosya sayısını seçin (varsayılan değer 100 dosyadır).
    - Dosyaların hangi sırayla iş gördüğünü belirtin (seçenekler dosya kimliğine, dosya adına, dosya oluşturulma saate veya son değiştirme saate göre).
    - Düzenin nasıl sıralanmış (artan veya azalan düzen) olduğunu belirtin.

    ![Parametre seçeneklerinin vurgulu olduğu Akış çalıştır panelini gösteren ekran görüntüsü.](../media/content-understanding/run-flow-panel.png)  

### <a name="classification-date-field"></a>Sınıflandırma Tarihi alanı

Belge kitaplığına SharePoint Syntex bir form işleme modeli (veya belge anlama modeli) uygulandığında, Sınıflandırma Tarihi alanı kitaplık şemasına dahil  edilir. Varsayılan olarak, bu alan boştur. Bununla birlikte, belgeler bir modele göre işlendiğinde ve sınıflandırılmışsa, bu alan bir tamamlanma tarih-zaman damgasıyla güncelleştirilir. 

Bir modeli Sınıflandırma Tarihi ile damgalandıktan **sonra,** SharePoint Syntex dosya akışını işledikten sonra, **kullanıcılara** yeni bir dosyanın SharePoint belge kitaplığında bir model tarafından işlendiğinden ve sınıflandırılmış olduğunu bildirmek için E-posta gönder'i kullanabilirsiniz.

Akışı çalıştırmak için:

1. Bir dosya seçin ve sonra **Tümleştir'i seçin** >  **Power Automate** >  **Akış seçin**.

2. Akış oluştur **panelinde, Bir** dosyayı **işledikten sonra e-SharePoint Syntex e-posta gönder'i seçin**.

    ![Akış paneli ve akış oluştur seçeneğinin vurgulu olduğunu gösteren ekran görüntüsü.](../media/content-understanding/integrate-create-flow.png) 

## <a name="see-also"></a>Ayrıca Bkz
  
[Power Automate belgeleri](/power-automate/)

[Eğitim: AI Builder ile iş performansını geliştirme](/learn/paths/improve-business-performance-ai-builder/?source=learn)