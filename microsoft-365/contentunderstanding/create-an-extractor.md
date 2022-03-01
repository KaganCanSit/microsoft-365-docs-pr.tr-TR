---
title: Microsoft SharePoint Syntex
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
description: Microsoft SharePoint Syntex'de nasıl ayıklaıcı oluştur SharePoint Syntex.
ms.openlocfilehash: 1d0aebf610897d07d051ba9e5f3e218dd582bbad
ms.sourcegitcommit: 966344e1aa442a4d10a0fb05f56badd38c833bb2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/19/2022
ms.locfileid: "63015562"
---
# <a name="create-an-extractor-in-microsoft-sharepoint-syntex"></a>Microsoft SharePoint Syntex'de ayıklaıcı oluşturma


<br/>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4CL2G]

<br/> 

Belirli belge türlerinin kimliğini ve sınıflandırmayı otomatikleştirmek için sınıflandırıcı modeli oluşturmadan önce veya oluşturduktan sonra, isteğe bağlı olarak bu belgelerden belirli bilgileri almak için modelinize ayıklayıcılar eklemeyi seçebilirsiniz. Örneğin, modelinizin yalnızca belge kitaplığınıza eklenen tüm Sözleşme Yenileme belgelerini  tanımlaması değil, her belgenin Hizmet Başlangıç tarihini de belge kitaplığında bir  sütun değeri olarak görüntülemesini istiyor olabilirsiniz.

Belge içinde ayıklamak istediğiniz her varlık için bir ayıklaıcı oluşturmanız gerekir. Örneğimizde, model tarafından tanımlanan **** herContract   **Renewaldocument** içinService Start  Date belgeyi ayıklamak we want to extract.  **TümContract Renewaldocuments**  belge kitaplığında, her belgenin Hizmet Başlangıç tarihi değerini gösteren bir sütunla bir görünüm görmek istiyoruz. 

> [!NOTE]
> Bir ayıklayıcı oluşturmak için, daha önce karşıya yüklediğiniz aynı dosyaları sınıflandırıcıyı eğitmek için kullanırsiniz. 

## <a name="name-your-extractor"></a>Ayıklayanın adını yazın

1. Model giriş sayfasında, Ayıklar oluştur ve **eğitim ayıkla kutucuğunda** Eğitim **ayıkla'ya tıklayın**.

2. Yeni **varlık ayıklaıcı ekranında** , Yeni ayıklaıcı adı **alanına ayıklaıcının adını** yazın. Örneğin, her Sözleşme **Yenileme belgelerinden** hizmet başlangıç tarihini ayıklamak için bu adı Hizmet Başlangıç Tarihi olarak yazın. Daha önce oluşturulmuş bir sütunu (örneğin, yönetilen bir meta veri sütunu) yeniden kullanabilirsiniz.

    Varsayılan olarak, sütun türü Tek **satır metindir**. Sütun türünü değiştirmek için Gelişmiş **ayarlarS** >  sütun türü'ne tıklayın ve sonra da kullanmak istediğiniz türü seçin.

    ![Sütun türü seçeneğini gösteren Yeni varlık ayıkla panelinin Gelişmiş ayarlar bölümünün ekran görüntüsü.](../media/content-understanding/advanced-settings-column-type.png) 

    > [!NOTE]
    > Sütun türü Tek satır metin olan **ayıklayıcılar için** en yüksek karakter sınırı 255'tir. Sınırı aşan tüm karakterler kesilir.

3. Bitir bittiğinde Oluştur'a **tıklayın**.

## <a name="add-a-label"></a>Etiket ekleme

Sonraki adım, örnek eğitim dosyalarında ayıklamak istediğiniz varlığı etiketlemektir.

Ayıklaıcıyı oluşturmak, ayıklayıcı sayfasını açar. Burada, örnek dosyalarınızın listesini ve listede ilk dosyanın görüntüleyicide görüntülendiğinden emin olun.

1. Görüntüleyiciden, dosyalardan ayıklamak istediğiniz verileri seçin. Örneğin, Başlangıç Hizmet Tarihini ayıklamak istediğiniz *zaman ilk* dosyada (Pazartesi *, 14 Ekim 2019) tarih değerini vurgularsınız*. ve ardından **Kaydet'e tıklayın**.  Etiketli örnekler listesinde, Etiket sütununu altında dosyadaki **değerin görüntüleniyor olması** gerekir.
2. Otomatik **olarak kaydetmek** ve listede bir sonraki dosyayı görüntüleyicide açmak için Sonraki dosya'ya tıklayın. Ya da **Kaydet'i** seçin ve Etiketli örnekler **listesinden başka bir dosya** seçin.
3. Görüntüleyicide, 1. ve 2. adımları yinelayın, ardından etiketi beş dosyanın hepsinde kaydedene kadar tekrarlayın.

    ![Gelişmiş ayarlar'a tıklayın.](../media/content-understanding/select-service-start-date.png) 

 
Beş dosya etiketlenin ardından, eğitime devam etme konusunda sizi bilgilendiren bir bildirim başlığı görüntülenir. Daha fazla belge etiketlemeyi seçebilir veya eğitime ilerleyebilirsiniz. 

### <a name="use-find-to-search-your-file"></a>Dosyanızı aramak için Bul'ı kullanma

Bul özelliğini **kullanarak** belgenize etiket almak istediğiniz bir varlık arayabilirsiniz.

   ![Dosyada bulur.](../media/content-understanding/find-feature.png) 

Büyük bir belgede arama ediyorsanız veya belgede varlığın birden çok örneği varsa, Bul özelliği yararlı olur. Birden çok örnek bulursanız, etiket olarak görüntüleyicide ilgili konuma gitmek için arama sonuçlarında ihtiyacınız olan örneği seçin.


## <a name="add-an-explanation"></a>Açıklama ekleme

Örneğimizde, varlık biçiminin kendisine ve örnek belgelerde var olan çeşitlemelere ilişkin ipucu sağlayan bir açıklama oluşturlerimiz olacak. Örneğin, tarih değeri aşağıdakiler gibi çeşitli biçimlerde olabilir:
- 10/14/2019
- 14 Ekim 2019
- 14 Ekim 2019 Pazartesi
 

Hizmet Başlangıç Tarihini *belirlemeye yardımcı olmak* için desen açıklaması oluşturabilirsiniz.

1. Açıklama bölümünde Yeni'yi **seçin** ve bir ad yazın (örneğin, *Tarih*).
2. Tür için Desen **listesi'ne tıklayın**.
3. Değer için, örnek dosyalarda görünecekleri tarih çeşitlelesiniz. Örneğin, 00.00.0000 olarak görünen tarih biçimleriniz varsa, belgelerinize görünen çeşitlemeleri girin; örneğin:
    - 0/0/0000
    - 0/00/0000
    - 00/0/0000
    - 00/00/0000
4. **Kaydet**'i seçin.

> [!NOTE]
> Açıklama türleri hakkında daha fazla bilgi edinmek için bkz. [Açıklama türleri](./explanation-types-overview.md).  


### <a name="use-the-explanation-library"></a>Açıklama kitaplığını kullanma

Tarih gibi öğeler için açıklamalar oluştururken, açıklama kitaplığını kullanmak tüm çeşitlemeleri el ile girmekten daha kolaydır.[](./explanation-types-overview.md) Açıklama kitaplığı, önceden yapılmış bir tümcecik ve desen açıklamaları kümesidir. Kitaplık, tarihler, telefon numaraları, posta kodları ve daha birçok ortak tümcecik veya desen listesi için tüm biçimleri sağlar. 

Hizmet Başlangıç *Tarihi örneğinde* , açıklama kitaplığında Tarih'in önceden yerleşik açıklamasını *kullanmak daha* verimli olur:

1. Açıklama bölümünde **Yeni'yi** ve **ardından** Açıklama **kitaplığından'ı seçin**.
2. Açıklama kitaplığından Tarih'i **seçin**. Tanınan tüm tarih çeşitlemelerini görüntüabilirsiniz.
3. **Ekle**'yi seçin.

    ![Açıklama kitaplığı.](../media/content-understanding/explanation-library.png) 

4. Açıklama **oluştur sayfasında** , açıklama *kitaplığından* gelen tarih bilgileri alanları otomatik olarak doldurur. **Kaydet**'i seçin.

    ![Tarih.](../media/content-understanding/date-explanation-library.png) 

## <a name="train-the-model"></a>Modeli eğitin 

Açıklamanızı kaydetme eğitiminize başlar. Modeliniz etiketli örnek dosyalardan verileri ayıklamak için yeterli bilgiye sahipse, Her dosyayı Eşleşme etiketiyle etiketlenmiş olarak **gösterirsiniz**.  

![Eşleşme.](../media/content-understanding/match2.png) 

Açıklamanın ayıklamak istediğiniz verileri bulmak için yeterli bilgisi yoksa, her dosya Eşleşmez olarak **etiketlenmiş olur**. Eşleşmeyen dosyalara **tıklar ve** eşleşmeyen nedenler hakkında daha fazla bilgi edinebilirsiniz.


## <a name="add-another-explanation"></a>Başka bir açıklama ekleme

Eşleşmeyenler genellikle, sağladığımız açıklamanın etiketli dosyalarımız ile hizmet başlangıç tarihi değerini ayıklamak için yeterli bilgi sağlamamış olduğuna ilişkin bir göstergedir. Belgeyi düzenlemeniz veya başka bir açıklama eklemeniz gerekir.

Örneğimiz için, Hizmet Başlangıç metin *dizesinin her zaman gerçek* değerin önünde olduğunu fark etmiş oluruz. Hizmet Başlangıç Tarihini belirlemeye yardımcı olmak için bir tümcecik açıklaması oluşturmanız gerekir.

1. Açıklama bölümünde Yeni'yi **seçin** ve bir ad yazın (örneğin, Önek *Dizesi*).
2. Tür için Tümcecik **listesi'ne tıklayın**.
3. Hizmet *Başlangıç Tarihini değer* olarak kullanın.
4. **Kaydet**'i seçin.

    ![Önek dizesi.](../media/content-understanding/prefix-string.png) 

## <a name="train-the-model-again"></a>Modeli yeniden eğitin

Açıklama kaydederek eğitim, bu kez örnekteki her iki açıklamayı da kullanarak yeniden başlatılır. Modeliniz etiketli örnek dosyalardan verileri ayıklamak için yeterli bilgiye sahipse, Her dosyayı Match etiketli olarak **görüyorsunuz**. 

Etiketli dosyalarınıza yeniden  bir Eşleşme eşleşmesi alırsanız, büyük olasılıkla modele belge türünü belirlemek için daha fazla bilgi sağlamak veya mevcut dosyalarda değişiklik yapmak için başka bir açıklama oluşturmanız gerekir.

## <a name="test-your-model"></a>Modelinizi test etmek

Etiketli örnek dosyalarınız için bir eşleşme alırsanız, artık modelinizi diğer etiketsiz örnek dosyalar üzerinde test edersiniz. Bu isteğe bağlıdır, ancak modeli daha önce kullanmadan önce fitness'i veya hazırlığı değerlendirmek için, modeli daha önce kullanmamış olduğu dosyalar üzerinde test etmek için yararlı bir adımdır.

1. Model giriş sayfasından Sına **sekmesine** tıklayın.  Bu, modeli etiketsiz örnek dosyalarınız üzerinde çalıştırır.
2. Test **dosyaları listesinde** , örnek dosyalarınız modelin ihtiyacınız olan bilgileri ayıklayana kadar mümkün olup olduğunu gösterecek şekilde görüntülenir. Belgelerinizi belirlemede sınıflandırıcının ne kadar etkili olduğunu belirlemenize yardımcı olması için bu bilgileri kullanın.

    ![Dosyalarınızı test etmek için.](../media/content-understanding/test-filies-extractor.png) 

## <a name="see-also"></a>Ayrıca Bkz
[Sınıflandırıcı oluşturma](create-a-classifier.md)

[Açıklama türleri](explanation-types-overview.md)

[Ayıklaıcı oluştururken terim deposu taksonomilerinden faydalanma](leverage-term-store-taxonomy.md)

[Belge Anlama'ya genel bakış](document-understanding-overview.md)

[Model uygulama](apply-a-model.md) 

[SharePoint Syntex Modu](accessibility-mode.md)
