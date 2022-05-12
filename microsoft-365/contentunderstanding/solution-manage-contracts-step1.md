---
title: Adım 1. Sözleşme dosyalarını tanımlamak ve verileri ayıklamak için SharePoint Syntex kullanma
ms.author: chucked
author: chuckedmonson
manager: pamgreen
ms.reviewer: ssquires
audience: admin
ms.topic: article
ms.date: ''
ms.prod: microsoft-365-enterprise
search.appverid: ''
ms.localizationpriority: medium
ROBOTS: ''
description: Microsoft 365 çözümü kullanarak sözleşme dosyalarını tanımlamak ve verileri ayıklamak için SharePoint Syntex kullanmayı öğrenin.
ms.openlocfilehash: 7d2874260ce7a307aa42c67ba571104ed4c4da87
ms.sourcegitcommit: 344a254ca268a2f65cf199d9158a47e08861ffa5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2022
ms.locfileid: "65368099"
---
# <a name="step-1-use-sharepoint-syntex-to-identify-contract-files-and-extract-data"></a>Adım 1. Sözleşme dosyalarını tanımlamak ve verileri ayıklamak için SharePoint Syntex kullanma

Kuruluşunuzun, aldığınız birçok dosyadaki tüm sözleşme belgelerini tanımlamak ve sınıflandırmak için bir yönteme ihtiyacı vardır. Ayrıca, tanımlanan sözleşme dosyalarının her birinde (örneğin, *İstemci*, *Yüklenici* ve *Ücret tutarı*) birkaç önemli öğeyi hızla görüntüleyebilmek istiyorsunuz. Bunu [yapmak için SharePoint Syntex](index.md) kullanarak belge anlama modeli oluşturabilir ve belge kitaplığına uygulayabilirsiniz.

## <a name="overview-of-the-process"></a>İşleme genel bakış

[Belge anlama](document-understanding-overview.md) , dosya sınıflandırmasını ve bilgilerin ayıklamasını otomatikleştirmek için yapay zeka (AI) modellerini kullanır. Belge anlama modelleri, ihtiyacınız olan bilgilerin sözleşmeler gibi tablo veya formlarda yer almadığı yapılandırılmamış ve yarı yapılandırılmış belgelerden bilgi ayıklamada da idealdir. 

Belge anlama modelleri, hem örnek dosyalar içeren bir model eğittiğinizde hem de modeli belge kitaplığındaki dosyalara karşı çalıştırdığınızda PDF'leri, görüntüleri ve TIFF dosyalarını taramak için Optik Karakter Tanıma (OCR) teknolojisini kullanır.

1. İlk olarak, modeli tanımlamaya çalıştığınız içerik türüne (sözleşme) özgü özellikleri aramak için "eğitmek" için kullanabileceğiniz en az beş örnek dosya bulmanız gerekir. 

2. SharePoint Syntex kullanarak yeni bir belge anlama modeli oluşturun. Örnek dosyalarınızı kullanarak [bir sınıflandırıcı oluşturmanız](create-a-classifier.md) gerekir. Sınıflandırıcıyı örnek dosyalarınızla eğiterek, şirketinizin sözleşmelerinde göreceğiniz özelliklere özgü özellikleri aramayı öğretirsiniz. Örneğin, sözleşmelerinizdeki *Hizmet Sözleşmesi*, *Sözleşme Koşulları* ve *Tazminat* gibi belirli dizeleri arayan [bir "açıklama" oluşturun](create-a-classifier.md#create-an-explanation). Hatta belgenin belirli bölümlerinde veya diğer dizelerin yanında bulunan bu dizeleri aramak için açıklamanızı eğitebilirsiniz. Sınıflandırıcınızı ihtiyaç duyduğu bilgilerle eğittiğinizi düşündüğünüzde, modelinizin ne kadar verimli olduğunu görmek için örnek bir örnek dosya kümesi üzerinde test edebilirsiniz. Test ettikten sonra, gerekirse açıklamalarınızı daha verimli hale getirmek için açıklamalarınızda değişiklik yapmayı seçebilirsiniz. 

3. Modelinizde, her sözleşmeden belirli veri parçalarını çekmek için [bir ayıklayıcı oluşturabilirsiniz](create-an-extractor.md) . Örneğin, her sözleşme için en çok endişelendiğiniz bilgiler müşterinin kim olduğu, yüklenicinin adı ve toplam maliyettir.

4. Modelinizi başarıyla oluşturduktan sonra [SharePoint belge kitaplığına uygulayın](apply-a-model.md). Belgeleri belge kitaplığına yüklerken, belge anlama modeliniz çalışır ve modelinizde tanımladığınız sözleşme içerik türüyle eşleşen tüm dosyaları tanımlar ve sınıflandırır. Sözleşme olarak sınıflandırılan tüm dosyalar özel kitaplık görünümünde görüntülenir. Dosyalar, ayıklayıcınızda tanımladığınız her sözleşmedeki değerleri de görüntüler.

   ![Belge kitaplığındaki sözleşmeler.](../media/content-understanding/doc-lib-solution.png)

5. Sözleşmeleriniz için bekletme veya güvenlik gereksinimleriniz varsa, modelinizi kullanarak belirli bir süre boyunca sözleşmelerinizin silinmesini engelleyecek bir [bekletme etiketi](apply-a-retention-label-to-a-model.md) veya [duyarlılık etiketi](apply-a-sensitivity-label-to-a-model.md) uygulayabilir veya sözleşmelere kimlerin erişebileceğini kısıtlayabilirsiniz.

## <a name="steps-to-create-and-train-your-model"></a>Modelinizi oluşturma ve eğitmeye yönelik adımlar

> [!NOTE]
> Bu adımlar için [, Sözleşme Yönetimi Çözümü Varlıkları deposundaki](https://github.com/pnp/syntex-samples/tree/main/scenario%20samples/Contracts%20Management) örnek dosyaları kullanabilirsiniz. Bu depodaki örnekler hem belge anlama modeli dosyalarını hem de modeli eğitmek için kullanılan dosyaları içerir.

### <a name="create-a-contract-model"></a>Sözleşme modeli oluşturma

İlk adım, Sözleşme modelinizi oluşturmaktır.

1. İçerik **merkezinden Yeni'yi** ve ardından **Model oluştur'u** seçin.

2. **Yeni belge anlama modeli** bölmesindeki **Ad** alanına modelin adını yazın. Bu sözleşme yönetimi çözümü için modeli *Sözleşme* olarak adlandırabilirsiniz.

4. **Oluştur**'u seçin. Bu, model için bir giriş sayfası oluşturur.</br>

    ![Sözleşme giriş sayfasının ekran görüntüsü.](../media/content-understanding/models-contract-home-page.png)


### <a name="train-your-model-to-classify-a-type-of-file"></a>Bir dosya türünü sınıflandırmak için modelinizi eğitin

#### <a name="add-example-files-for-your-model"></a>Modeliniz için örnek dosyalar ekleme

Sözleşme belgesi olan en az beş örnek dosya ve sözleşme belgesi olmayan bir örnek dosya (örneğin, çalışma bildirimi) eklemeniz gerekir. 

1. **Modeller > Sözleşme** sayfasında **, Anahtar eylemleriEkle** >  **örnek dosyalar'ın** altında **Dosya ekle'yi** seçin.

   ![Örnek dosya ekle seçeneğinin vurgulandığı Sözleşmeler sayfasını gösteren ekran görüntüsü.](../media/content-understanding/key-actions-add-example-files.png)

2. **Modelinizin örnek dosyalarını seçin** sayfasında Sözleşme klasörünü açın, kullanmak istediğiniz dosyaları seçin ve ardından **Ekle'yi** seçin. Orada örnek dosyalarınız yoksa, eklemek **için Upload'ı** seçin.

#### <a name="label-the-files-as-positive-or-negative-examples"></a>Dosyaları pozitif veya negatif örnekler olarak etiketleme

1. **Modeller > Sözleşme** sayfasında **, Anahtar eylemleri** >  **Dosyaları sınıflandırma ve eğitimi çalıştırma** altında **Sınıflandırıcıyı eğit'i** seçin.

   ![Dosyaları sınıflandır ve eğitim çalıştır seçeneğinin vurgulandığı Sözleşmeler sayfasını gösteren ekran görüntüsü.](../media/content-understanding/key-actions-classify-files.png)

2. **Models > Contract > Contract sınıflandırıcısı** sayfasında, ilk örnek dosyanın üst kısmındaki görüntüleyicide, dosyanın oluşturduğunuz Sözleşme modelinin bir örneği olup olmadığını soran bir metin görürsünüz. Olumlu bir örnekse **Evet'i** seçin. Negatif bir örnekse **Hayır'ı** seçin.

3. Soldaki **Etiketli örnekler** listesinden örnek olarak kullanmak istediğiniz diğer dosyaları seçin ve bunları etiketleyin. 

    ![Sınıflandırıcı giriş sayfası.](../media/content-understanding/models-contract-classifier.png) 

#### <a name="add-at-least-one-explanation-to-train-the-classifier"></a>Sınıflandırıcıyı eğitmek için en az bir açıklama ekleyin 

1. **Modeller > Sözleşme > Sözleşme sınıflandırıcısı** sayfasında **Eğit** sekmesini seçin.

2. **Eğitilen dosyalar** bölümünde, daha önce etiketlediğiniz örnek dosyaların listesini görürsünüz. Görüntüleyicide görüntülemek için listeden pozitif dosyalardan birini seçin.

3. **Açıklamalar** bölümünde **Yeni'yi** ve ardından **Boş'ı** seçin.

4. **Açıklama oluştur** sayfasında:

    a. **Ad** alanına açıklamanın adını ("Anlaşma" gibi) yazın.

    b. **Açıklama türü** alanında, metin dizesi eklediğiniz için **Tümcecik listesi'ni** seçin.

    c. **Tümcecik liste** kutusuna dizeyi ("SÖZLEŞME" gibi) yazın. Dizenin büyük **/küçük harfe duyarlı olması gerekiyorsa Büyük/** küçük harfe duyarlı seçeneğini belirleyebilirsiniz.

    d. **Kaydet ve eğit'i** seçin.

    ![Açıklama oluştur panelinin ekran görüntüsü.](../media/content-understanding/contract-classifier-create-explanation.png) 

#### <a name="test-your-model"></a>Modelinizi test etme

Sözleşme modelinizi daha önce görmediği örnek dosyalarda test edebilirsiniz. Bu isteğe bağlıdır, ancak yararlı bir en iyi uygulama olabilir.

1. **Modeller > Sözleşme > Sözleşme sınıflandırıcısı** sayfasında **Test** sekmesini seçin. Bu, modeli etiketlenmemiş örnek dosyalarınızda çalıştırır.

2. **Test Dosyaları** listesinde, örnek dosyalarınız görüntülenir ve modelin bunların pozitif mi yoksa negatif mi olacağını tahmin edip etmediğini gösterir. Sınıflandırıcınızın belgelerinizi tanımlamadaki etkinliğini saptamaya yardımcı olması için bu bilgileri kullanın.

    ![Metin Dosyaları listesindeki etiketsiz dosyaların ekran görüntüsü.](../media/content-understanding/test-on-files.png) 

3. İşiniz bittiğinde **Eğitimden Çık'ı** seçin.

### <a name="create-and-train-an-extractor"></a>Ayıklayıcı oluşturma ve eğitma

1. **Modeller > Sözleşme** sayfasında **, Önemli eylemler** >  **Ayıklayıcı oluştur ve eğit'in** altında **Ayıklayıcı oluştur'u** seçin.

   ![Ayıklayıcı oluştur ve eğit seçeneğinin vurgulandığı Sözleşmeler sayfasını gösteren ekran görüntüsü.](../media/content-understanding/key-actions-create-extractors.png)

2. **Yeni varlık ayıklayıcısı** panelindeki **Yeni ad** alanına ayıklayıcınızın adını yazın. Örneğin, her sözleşmeden *istemcinin* adını ayıklamak istiyorsanız İstemci olarak adlandırın.

3. İşiniz bittiğinde **Oluştur'u** seçin.

#### <a name="label-the-entity-you-want-to-extract"></a>Ayıklamak istediğiniz varlığı etiketleme

Ayıklayıcıyı oluşturduğunuzda ayıklayıcı sayfası açılır. Burada, listedeki ilk dosyanın görüntüleyicide görüntülendiği örnek dosyalarınızın listesini görürsünüz.

![İstemci ayıklayıcısı Etiketli örnekler sayfasının ekran görüntüsü.](../media/content-understanding/client-extractor-labeled-examples.png) 

Varlığı etiketlemek için:

1. Görüntüleyiciden, dosyalardan ayıklamak istediğiniz verileri seçin. Örneğin, *İstemci'yi* ayıklamak istiyorsanız, ilk dosyadaki istemci değerini vurgularsınız (bu örnekte, *Best For You Organics*) ve ardından **Kaydet'i** seçersiniz. **Etiketlenmiş örnekler** listesinde, **Etiket** sütununun altında dosyasındaki değerin görüntülendiğini görürsünüz.

2. Otomatik kaydetmek için **sonraki dosya'ya** tıklayın ve görüntüleyicideki listede bir sonraki dosyayı açın. Ya da **Kaydet'i** ve ardından **Etiketli örnekler** listesinden başka bir dosya seçin.

3. Görüntüleyicide, 1. ve 2. adımları yineleyin, ardından etiketi tüm dosyalara kaydedene kadar yineleyin.

Dosyaları etiketledikten sonra eğitime geçmenizi bildiren bir bildirim başlığı görüntülenir. Daha fazla belgeyi etiketlemeyi veya eğitime ilerlemeyi seçebilirsiniz.

#### <a name="add-an-explanation"></a>Açıklama ekleme

Varlık biçiminin kendisi ve örnek dosyalarda sahip olabileceği çeşitlemeler hakkında ipucu sağlayan bir açıklama oluşturabilirsiniz. Örneğin, tarih değeri aşağıdakiler gibi birçok farklı biçimde olabilir:

- 10/14/2019
- 14 Ekim 2019, Cumartesi
- 14 Ekim 2019 Pazartesi

*Sözleşme Başlangıç Tarihi'ni* tanımlamaya yardımcı olmak için bir desen açıklaması oluşturabilirsiniz.

1. **Açıklamalar** bölümünde **Yeni'yi** ve ardından **Boş'ı** seçin.

2. **Açıklama oluştur** sayfasında:

    a. **Ad** alanına açıklamanın adını yazın (*Tarih* gibi).

    b. **Açıklama türü** alanında **Desen listesi'ni** seçin.

    c. **Değer** alanında, örnek dosyalarda göründükleri şekilde tarih çeşitlemesi sağlayın. Örneğin, 00.00.0000 olarak görünen tarih biçimleriniz varsa, belgelerinizde görünen çeşitlemeleri girersiniz, örneğin:

    - 0/0/0000
    - 0/00/0000
    - 00/0/0000
    - 00/00/0000

4. **Kaydet ve eğit'i** seçin.

#### <a name="test-your-model-again"></a>Modelinizi yeniden test etme

Sözleşme modelinizi daha önce görmediği örnek dosyalarda test edebilirsiniz. Bu isteğe bağlıdır, ancak yararlı bir en iyi uygulama olabilir.

1. **Modeller > Sözleşme > Sözleşme sınıflandırıcısı** sayfasında **Test** sekmesini seçin. Bu, modeli etiketlenmemiş örnek dosyalarınızda çalıştırır.

2. **Test dosyaları** listesinde örnek dosyalarınız görüntülenir ve modelin ihtiyacınız olan bilgileri ayıklayıp ayıklayamadığı gösterilir. Sınıflandırıcınızın belgelerinizi tanımlamadaki etkinliğini saptamaya yardımcı olması için bu bilgileri kullanın.

3. İşiniz bittiğinde **Eğitimden Çık'ı** seçin.

### <a name="apply-your-model-to-a-document-library"></a>Modelinizi belge kitaplığına uygulama

Modelinizi bir SharePoint belge kitaplığına uygulamak için:

1. **Modeller > Sözleşme** sayfasında **, Anahtar** **eylemleriUygulamalara** >  model **uygulama'nın altında Modeli uygula'yı** seçin.

   ![Modeli kitaplıklara uygula seçeneğinin vurgulandığı Sözleşmeler sayfasını gösteren ekran görüntüsü.](../media/content-understanding/key-actions-apply-model.png)

2. **Sözleşme Ekle** panelinde, modeli uygulamak istediğiniz belge kitaplığını içeren SharePoint sitesini seçin. Site listede gösterilmiyorsa, bulmak için arama kutusunu kullanın. **Ekle**'yi seçin.

    > [!NOTE]
    > Modeli uyguladığınız belge kitaplığında *Listeyi Yönet* izinlerine veya *Düzenleme* haklarına sahip olmanız gerekir.

3. Siteyi seçtikten sonra modeli uygulamak istediğiniz belge kitaplığını seçin.

4. Model bir içerik türüyle ilişkilendirildiğinden, kitaplığa uyguladığınızda, ayıkladığınız etiketlerin sütun olarak gösterildiği içerik türünü ve görünümünü ekler. Bu görünüm kitaplığın varsayılan görünümüdür, ancak isteğe bağlı olarak **Gelişmiş ayarlar'ı** seçip **Bu yeni görünümü varsayılan olarak ayarla** onay kutusunu temizleyerek varsayılan görünüm olmamasını seçebilirsiniz.

5. Modeli kitaplığa uygulamak için **Ekle'yi** seçin.

6. **Modeller > Sözleşmesi** sayfasının **Bu modele sahip kitaplıklar** bölümünde, listelenen SharePoint sitesinin URL'sini görürsünüz.

    ![Bu modele sahip Kitaplıklar bölümünü gösteren Sözleşme giriş sayfasının ekran görüntüsü.](../media/content-understanding/contract-libraries-with-this-model.png)

7. **Ayarlar** >  **Library ayarları** altında:

   - **Durum** adlı bir sütun ekleyin ve sütun türü olarak **Seçim'i** seçin.
   - **Gözden geçirme**, **Onaylandı** ve **Reddedildi** değerlerini uygulayın.

Modeli belge kitaplığına uyguladıktan sonra, belgeleri siteye yüklemeye başlayabilir ve sonuçları görebilirsiniz.

## <a name="next-step"></a>Sonraki adım

[2. Adım. Sözleşme yönetimi kanalınızı oluşturmak için Microsoft Teams kullanma](solution-manage-contracts-step2.md)
