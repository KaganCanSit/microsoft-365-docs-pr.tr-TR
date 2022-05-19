---
title: Ayıklayıcı oluşturma Microsoft SharePoint Syntex
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
description: Microsoft SharePoint Syntex'da ayıklayıcı oluşturmayı öğrenin.
ms.openlocfilehash: 5be59cc7b99d64ceceb08bc400eeb0c44e3de1a8
ms.sourcegitcommit: e624221597480295b799d56568c4f6f56d40b41d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2022
ms.locfileid: "65535492"
---
# <a name="create-an-extractor-in-microsoft-sharepoint-syntex"></a>Microsoft SharePoint Syntex'de ayıklayıcı oluşturma


<br/>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4CL2G]

<br/>

Belirli belge türlerini tanımlamayı ve sınıflandırmayı otomatikleştirmek için bir sınıflandırıcı modeli oluşturmadan önce veya sonra, isteğe bağlı olarak modelinize ayıklayıcılar ekleyerek bu belgelerden belirli bilgileri çekmeyi seçebilirsiniz. Örneğin, modelinizin yalnızca belge kitaplığınıza eklenen tüm *Sözleşme Yenileme* belgelerini tanımlamasını değil, aynı zamanda her belgenin *Hizmet Başlangıç tarihini* belge kitaplığında sütun değeri olarak görüntülemesini de isteyebilirsiniz.

Belgede ayıklamak istediğiniz her varlık için bir ayıklayıcı oluşturmanız gerekir. Örneğimizde, model tarafından tanımlanan her **Sözleşme Yenileme** belgesi için **Hizmet Başlangıç Tarihi'ni** ayıklamak istiyoruz. Tüm **Sözleşme Yenileme** belgelerinin belge kitaplığında, her belgenin **Hizmet Başlangıç** tarihi değerini gösteren bir sütunla birlikte bir görünüm görebilmek istiyoruz.

> [!NOTE]
> Ayıklayıcı oluşturmak için sınıflandırıcıyı eğitmek için daha önce karşıya yüklediğiniz dosyaları kullanırsınız.

## <a name="name-your-extractor"></a>Ayıklayıcınızı adlandırma

1. Model giriş sayfasındaki **Ayıklayıcı oluştur ve eğit** kutucuğunda **Ayıklayıcıyı eğit'i** seçin.

2. **Yeni varlık ayıklayıcısı** ekranında, **Yeni ayıklayıcı adı alanına ayıklayıcınızın adını** yazın. Örneğin, her Sözleşme Yenileme belgesinden hizmet başlangıç tarihini ayıklamak istiyorsanız Hizmet Başlangıç **Tarihi** olarak adlandırın. Daha önce oluşturulmuş bir sütunu (örneğin, yönetilen meta veri sütunu) yeniden de kullanabilirsiniz.

    Varsayılan olarak, sütun türü **Tek satırlık metindir**. Sütun türünü değiştirmek istiyorsanız **Gelişmiş ayarlarSütun** >  **türü'nü** seçin ve ardından kullanmak istediğiniz türü seçin.

    ![Sütun türü seçeneğini gösteren Yeni varlık ayıklayıcı panelinin Gelişmiş ayarlar bölümünün ekran görüntüsü.](../media/content-understanding/advanced-settings-column-type.png)

    > [!NOTE]
    > **Tek satırlık metin** sütun türüne sahip ayıklayıcılar için en fazla karakter sınırı 255'tir. Sınırı aşan yazdığınız tüm karakterler kesilir.

3. İşiniz bittiğinde **Oluştur'u** seçin.

## <a name="add-a-label"></a>Etiket ekleme

Sonraki adım, örnek eğitim dosyalarınızda ayıklamak istediğiniz varlığı etiketlemektir.

Ayıklayıcı oluşturulurken ayıklayıcı sayfası açılır. Burada, listedeki ilk dosyanın görüntüleyicide görüntülendiği örnek dosyalarınızın listesini görürsünüz.

1. Görüntüleyiciden, dosyalardan ayıklamak istediğiniz verileri seçin. Örneğin, *Başlangıç Hizmeti Tarihi'ni* ayıklamak istiyorsanız, ilk dosyadaki tarih değerini vurgularsınız (*Pazartesi, 14 Ekim 2019*). ve ardından **Kaydet'i** seçin. Etiketlenmiş örnekler listesinde, **Etiket** sütununun altındaki dosyadan değerin görüntülendiğini görmeniz gerekir.
2. Otomatik kaydetmek için **sonraki dosya'ya** tıklayın ve görüntüleyicideki listede bir sonraki dosyayı açın. Alternatif olarak **Kaydet'i** ve ardından **Etiketli örnekler** listesinden başka bir dosya seçin.
3. Görüntüleyicide 1. ve 2. adımları yineleyin, ardından etiketi beş dosyaya da kaydedene kadar yineleyin.

    ![Gelişmiş ayarlar.](../media/content-understanding/select-service-start-date.png)

Beş dosyayı etiketledikten sonra, eğitime geçmenizi bildiren bir bildirim başlığı görüntülenir. Daha fazla belge etiketlemeyi veya eğitime ilerlemeyi seçebilirsiniz.

### <a name="use-find-to-search-your-file"></a>Dosyanızda arama yapmak için Bul'u kullanma

Belgenizde etiketlemek istediğiniz bir varlığı aramak için **Bul** özelliğini kullanabilirsiniz.

   ![Dosyada bul.](../media/content-understanding/find-feature.png)

Büyük bir belgeyi arıyorsanız veya belgede varlığın birden çok örneği varsa Bul özelliği kullanışlıdır. Birden çok örnek bulursanız, arama sonuçlarında ihtiyacınız olan örneği seçerek görüntüleyicide bu konuma gidip etiketleyebilirsiniz.

## <a name="add-an-explanation"></a>Açıklama ekleme

Örneğimizde, varlık biçiminin kendisi ve örnek belgelerde sahip olabileceği çeşitlemeler hakkında ipucu sağlayan bir açıklama oluşturacağız. Örneğin, tarih değeri aşağıdakiler gibi çeşitli biçimlerde olabilir:

- 10/14/2019
- 14 Ekim 2019, Cumartesi
- 14 Ekim 2019 Pazartesi

*Hizmet Başlangıç Tarihi'ni* tanımlamaya yardımcı olmak için bir desen açıklaması oluşturabilirsiniz.

1. Açıklama bölümünde **Yeni'yi** seçin ve bir ad (örneğin, *Tarih*) yazın.
2. Tür için **Desen listesi'ne** tıklayın.
3. Değer için, örnek dosyalarda göründükleri şekilde tarih çeşitlemesi sağlayın. Örneğin, 00.00.0000 olarak görünen tarih biçimleriniz varsa, belgelerinizde görünen çeşitlemeleri girersiniz, örneğin:
    - 0/0/0000
    - 0/00/0000
    - 00/0/0000
    - 00/00/0000
4. **Kaydet**'i seçin.

> [!NOTE]
> Açıklama türleri hakkında daha fazla bilgi için bkz. [Açıklama türleri](./explanation-types-overview.md).

### <a name="use-the-explanation-library"></a>Açıklama kitaplığını kullanma

Tarihler gibi öğeler için açıklama oluşturmak için açıklama [kitaplığını kullanmak](./explanation-types-overview.md) , tüm varyasyonları el ile girmekten daha kolaydır. Açıklama kitaplığı, önceden oluşturulmuş bir tümcecik ve desen açıklamaları kümesidir. Kitaplık, tarihler, telefon numaraları, posta kodları ve diğerleri gibi ortak tümcecik veya desen listeleri için tüm biçimleri sağlamaya çalışır.

*Hizmet Başlangıç Tarihi* örneği için, açıklama kitaplığında *Date* için önceden oluşturulmuş açıklamayı kullanmak daha verimlidir:

1. **Açıklama bölümünde** **Yeni'yi** ve ardından **Açıklama kitaplığından'ı** seçin.
2. Açıklama kitaplığından **Tarih'i** seçin. Tanınan tüm tarih çeşitlemelerini görüntüleyebilirsiniz.
3. **Ekle**'yi seçin.

    ![Açıklama kitaplığı.](../media/content-understanding/explanation-library.png)

4. **Açıklama oluştur** sayfasında, açıklama kitaplığındaki *Tarih* bilgileri alanları otomatik olarak doldurur. **Kaydet**'i seçin.

    ![Tarih.](../media/content-understanding/date-explanation-library.png)

## <a name="train-the-model"></a>Modeli eğitin

Açıklamanızı kaydetmek eğitimi başlatır. Modelinizde etiketlenmiş örnek dosyalarınızdan verileri ayıklamak için yeterli bilgi varsa, her dosyayı **Eşleştir** ile etiketlenmiş olarak görürsünüz.

![Maç.](../media/content-understanding/match2.png)

Açıklama, ayıklamak istediğiniz verileri bulmak için yeterli bilgiye sahip değilse, her dosya **Uyumsuz** olarak etiketlenir. **Eşleşmeyen** dosyalar'ı seçerek neden uyuşmazlık olduğu hakkında daha fazla bilgi edinebilirsiniz.

## <a name="add-another-explanation"></a>Başka bir açıklama ekleme

Genellikle uyuşmazlık, sağladığımız açıklamanın hizmet başlangıç tarihi değerini etiketli dosyalarımızla eşleşecek şekilde ayıklamak için yeterli bilgi sağlamadığının göstergesidir. Düzenlemeniz veya başka bir açıklama eklemeniz gerekebilir.

Örneğimizde, her zaman başlangıç *hizmeti tarihi metin dizesinin* gerçek değerden önce olduğuna dikkat edin. Hizmet Başlangıç Tarihi'ni tanımlamaya yardımcı olmak için bir tümcecik açıklaması oluşturmanız gerekir.

1. Açıklama bölümünde **Yeni'yi** seçin ve bir ad yazın (örneğin, *Ön Ek Dizesi*).
2. Tür için **Tümcecik listesi'ni** seçin.
3. Değer olarak *Hizmet Başlangıç Tarihi'ni* kullanın.
4. **Kaydet**'i seçin.

    ![Ön ek dizesi.](../media/content-understanding/prefix-string.png)

## <a name="train-the-model-again"></a>Modeli yeniden eğitin

Açıklamanın kaydedilmesi eğitimi yeniden başlatır ve bu kez örnekteki her iki açıklamayı da kullanır. Modelinizde etiketlenmiş örnek dosyalardan verileri ayıklamak için yeterli bilgi varsa, her dosyayı **Eşleştir** ile etiketlenmiş olarak görürsünüz.

Etiketli dosyalarınızda yeniden **Uyuşmazlık** alırsanız, modele belge türünü tanımlamak için daha fazla bilgi sağlamak için başka bir açıklama oluşturmanız veya mevcut dosyalarınızda değişiklik yapmayı göz önünde bulundurmanız gerekebilir.

## <a name="test-your-model"></a>Modelinizi test etme

Etiketli örnek dosyalarınızda bir eşleşme alırsanız, artık modelinizi etiketlenmemiş kalan örnek dosyalarda test edebilirsiniz. Bu adım isteğe bağlıdır, ancak modeli kullanmadan önce modelin daha önce görmediği dosyalarda test ederek "uygunluk" veya hazır olma durumunu değerlendirmek için kullanışlıdır.

1. Model giriş sayfasında **Test** sekmesini seçin.  Bu işlem, modeli etiketlenmemiş örnek dosyalarınızda çalıştırır.

2. **Test dosyaları** listesinde, örnek dosyalarınız modelin ihtiyacınız olan bilgileri ayıklayıp ayıklayamayacağını göstermek için görüntülenir. Sınıflandırıcınızın belgelerinizi tanımlamadaki etkinliğini saptamaya yardımcı olması için bu bilgileri kullanın.

    ![Dosyalarınızda test edin.](../media/content-understanding/test-filies-extractor.png)

## <a name="further-refine-an-extractor"></a>Ayıklayıcıyı daha fazla daraltma

Yinelenen varlıklarınız varsa ve yalnızca bir değeri veya belirli sayıda değeri ayıklamak istiyorsanız, nasıl işleneceğini belirtmek için bir kural ayarlayabilirsiniz. Ayıklanan bilgileri daraltacak bir kural eklemek için şu adımları izleyin:

1. Model giriş sayfasındaki **Varlık ayıklayıcıları** bölümünde, daraltmak istediğiniz ayıklayıcıyı seçin ve ardından **Ayıklanan bilgileri iyileştir'i** seçin.

    ![Ayıklanan bilgileri iyileştir seçeneğinin vurgulandığı Varlık ayıklayıcıları bölümünün ekran görüntüsü.](../media/content-understanding/refine-extracted-info.png)

2. **Ayıklanan bilgileri daralt** sayfasında aşağıdaki kurallardan birini seçin:

    - İlk değerlerden birini veya daha fazlasını tutma
    - Son değerlerden birini veya daha fazlasını tutma
    - Yinelenen değerleri kaldırma
    - İlk satırlardan birini veya daha fazlasını tutma
    - Son satırlardan birini veya daha fazlasını tutma

    ![Kural seçeneklerini gösteren Ayıklanan bilgileri daralt sayfasının ekran görüntüsü.](../media/content-understanding/refine-extracted-info-page.png)

3. Kullanmak istediğiniz satır veya değer sayısını girin ve **İyileştir'i** seçin.

4. Çizgi veya değer sayısını değiştirerek bir kuralı düzenlemek istiyorsanız, düzenlemek istediğiniz ayıklayıcıyı seçin, **Ayıklanan bilgileri daralt'ı** seçin, sayıyı değiştirin ve **kaydet'i** seçin.

5. Ayıklayıcıyı test ettiğinizde, iyileştirmeyi **Test Dosyaları** listesinin **İyileştirme sonucu** sütununda görebilirsiniz.

    ![İyileştirme sonucu sütununu gösteren Test Dosyaları listesi.](../media/content-understanding/test-filies-extractor-2.png)

6. Ayıklayıcıdaki bir iyileştirme kuralını silmek istiyorsanız, kuralı kaldırmak istediğiniz ayıklayıcıyı seçin, **Ayıklanan bilgileri daralt'ı** ve ardından **Sil'i** seçin.

## <a name="see-also"></a>Ayrıca bkz.

[Sınıflandırıcı oluştur](create-a-classifier.md)

[Açıklama türleri](explanation-types-overview.md)

[Ayıklayıcı oluştururken terim deposu taksonomisini kullan](leverage-term-store-taxonomy.md)

[Document Understanding'e genel bakış](document-understanding-overview.md)

[Model uygulama](apply-a-model.md)

[erişilebilirlik modunu SharePoint Syntex](accessibility-mode.md)
