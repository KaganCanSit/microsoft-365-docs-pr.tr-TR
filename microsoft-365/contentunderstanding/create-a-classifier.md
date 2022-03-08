---
title: Microsoft SharePoint Syntex'de sınıflandırıcı oluşturma
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
description: Microsoft SharePoint Syntex'da sınıflandırıcının nasıl oluşturul SharePoint Syntex.
ms.openlocfilehash: 5e9be6065e0328a412e73680a0200ea7929c8011
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63324879"
---
# <a name="create-a-classifier-in-microsoft-sharepoint-syntex"></a>Microsoft SharePoint Syntex'de sınıflandırıcı oluşturma


</br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4CL0R]  

</br>

Sınıflandırıcı, belge türünü tanımlama ve sınıflandırmayı otomatikleştirmek için kullanabileceğiniz bir tür modeldir. Örneğin, aşağıdaki çizimde *gösterildiği gibi,* belge kitaplığınıza eklenen tüm Sözleşme Yenileme belgelerini tanımlamak istiyor olabilir.

![Sözleşme Yenileme belgesi.](../media/content-understanding/contract-renewal.png)

Sınıflandırıcı oluşturmak, modelle ilişkili SharePoint [yeni bir](/sharepoint/governance/content-type-and-workflow-planning#content-type-overview) sınıf türü oluşturmanıza olanak sağlar.

Sınıflandırıcıyı oluştururken, modeli tanımlamak *için açıklamalar* oluşturmanız gerekir. Bu, bu belge türünü tutarlı bir şekilde bulmayı beklediğiniz yaygın verileri not alamana olanak sağlar. 

Aynı içerik türüne sahip dosyaları tanımlamak üzere modelinizi "eğitmek" için belge türü örneklerini ("örnek dosyalar") kullanın.

Sınıflandırıcı oluşturmak için şunları gerekir:
1. Modelinizi adlayın.
2. Örnek dosyalarınızı ekleyin.
3. Örnek dosyalarınızı etiketlenin.
4. Açıklama oluşturma.
5. Modelinizi test etmek.

> [!NOTE]
> Modeliniz belge türlerini tanımlamak ve sınıflandırmak için bir sınıflandırıcı kullandığında, model tarafından tanımlanan her dosyadan belirli bilgi parçalarını çekmeyi de seçebilirsiniz. Bunu yapmak için **modelinize bir ayıklaıcı** ekleyin. Bkz [. Ayıklaıcı oluşturma](create-an-extractor.md).

## <a name="name-your-model"></a>Modelinizi adla

Modelinizi oluşturmanın ilk adımı, modelinize bir ad vermektir:

1. İçerik merkezinde Yeni'yi **ve ardından** Model **oluştur'a seçin**.
2. Yeni **belge anlama modeli bölmesindeki** **Ad alanına** modelin adını yazın. Örneğin, sözleşme yenileme belgelerini tanımlamak istiyorsanız, Modeli Sözleşme Yenileme olarak *anabilirsiniz*.
3. **Oluştur**'u seçin. Bu işlem model için bir giriş sayfası oluşturur.</br>

    ![Sınıflandırıcı modeli giriş sayfası.](../media/content-understanding/model-home.png)

Bir model oluştururken, aynı zamanda yeni bir site içerik türü de oluşturuyor oluruz. İçerik türü, ortak özelliklere sahip olan ve bu belirli içerik için sütun veya meta veri özellikleri koleksiyonunu paylaşan bir belge kategorisini temsil eder. SharePoint türleri İçerik Türleri galerisi [aracılığıyla yönetilir](https://support.microsoft.com/office/create-or-customize-a-site-content-type-27eb6551-9867-4201-a819-620c5658a60f). Bu örnek için, modeli oluştururken yeni bir Sözleşme Yenileme içerik *türü oluşturuyoruz* .

Bu **modeli,** şemasını kullanmak üzere İçerik Türü galerisinde var olan bir kurumsal içerik türüyle <a href="https://go.microsoft.com/fwlink/?linkid=2185074" target="_blank">eşlemek</a> SharePoint Gelişmiş ayarlar'ı seçin. Enterprise türleri İçerik Türü Merkezi'nde, SharePoint yönetim merkezinde depolanır ve kiracının tüm sitelerine dağıtımda kullanılır. Tanımlama ve sınıflandırmaya yardımcı olmak üzere şemasından yararlanan mevcut bir içerik türünü kullansanız da modelinizi tanımları olan dosyalardan bilgi ayıklayması için eğitin.</br>

![Gelişmiş ayarlar'a tıklayın.](../media/content-understanding/advanced-settings.png)

## <a name="add-your-example-files"></a>Örnek dosyalarınızı ekleme

Model giriş sayfasında, modeli belge türlerinizi tanımlamaya yardımcı olmak için ihtiyacınız olacak örnek dosyalarınızı ekleyin. </br>
</br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4D0iX] 

</br>

> [!NOTE]
> Hem sınıflandırıcı hem de ayıklayıcı eğitimi için [aynı dosyaları kullanabilirsiniz](create-an-extractor.md). Daha sonra her zaman daha fazla ekleme seçeneğiniz olur, ancak normalde eksiksiz bir örnek dosya kümesi eklersiniz. Modellerinizi eğitmek için bazı modellerinizi etiketlenin ve model uygunluğu değerlendirmesini yapmak için kalan etiketsizleri test edin. 

Eğitim kümeniz için, hem pozitif hem de negatif örnekler kullanın:
- Pozitif örnek: Belge türünü temsil eden belgeler. Bunlar her zaman bu belge türünde olacak dizeler ve bilgiler içerir.
- Negatif örnek: Sınıflandırmak istediğiniz belgeyi temsil etmeyen diğer tüm belge. 

Modelinizi eğitmek için en az beş pozitif ve en az bir negatif örnek kullanın.  Eğitim sürecinden sonra modelinizi test etmek için eklerini oluşturmak istiyor.

Örnek dosyalar eklemek için:

1. Model giriş sayfasındaki Örnek dosyalar ekle **kutucuğunun Dosya** **ekle'ye tıklayın**.
2. **Modeliniz için örnek dosyaları seçin sayfasında**, içerik merkezinde bulunan Eğitim dosyaları kitaplığından örnek dosyalarınızı seçin. Daha önce oraya yüklemedıysanız, Eğitim dosyaları kitaplığına kopyalamak için Upload'e  tıklayarak bunları şimdi karşıya yükleyebilirsiniz.
3. Modeli eğitmek için örnek dosyalarınızı seçdikten sonra Ekle'ye **tıklayın**.

    ![Örnek dosyaları seçin.](../media/content-understanding/select-sample.png) 

## <a name="label-your-example-files"></a>Örnek dosyalarınızı etiketleme

Örnek dosyalarınızı ekledikten sonra, bunları pozitif veya negatif örnekler olarak etiketlemeniz gerekir.

1. Model giriş sayfasında, Dosyaları sınıflandır **ve eğitim kutucuğunu çalıştırın,** Sınıflandırıcıyı **eğit'e tıklayın**.
   Bu, örnek dosyalarınızın listesini gösteren etiket sayfasını görüntüler ve ilk dosya görüntüleyicide görünür durumda olur.
2. İlk örnek dosyanın en üstünde yer alan görüntüleyicide, dosyanın az önce oluşturduğunuz modele örnek olup olduğunu soran bir metin görüyor olun. Bu pozitif bir örnekse Evet'i **seçin**. Bu negatif bir örnekse Hayır'ı **seçin**.
3. Sol **tarafta etiketli** örnekler listesinde, örnek olarak kullanmak istediğiniz ek dosyaları seçin ve bunları etiketlenin. 

    ![Sınıflandırıcı giriş sayfası.](../media/content-understanding/classifier-home-page.png) 


> [!NOTE]
> Etikete en az beş pozitif örnek. En az bir negatif örneği de etiketlemelisiniz. 

## <a name="create-an-explanation"></a>Açıklama oluşturma

Sonraki adım, Tren sayfasında bir açıklama oluşturmanızdır. Açıklama, modelin belgeyi nasıl tanıyacaklarını anlamalarına yardımcı olur. Örneğin, Sözleşme Yenileme belgesinde her zaman ek açıklama *metin dizesi için bir İstek* yer alır.

> [!Note]
> Ayıklar ile birlikte kullanılırken, bir açıklama belgeden ayıklamak istediğiniz dizeyi tanımlar. 

Açıklama oluşturmak için:

1. Model giriş sayfasında, Tren **sayfasına gitmek** için Tren sekmesini seçin.
2. Eğitim sayfasındaki Eğitim dosyaları **bölümünde** , daha önce etiketlemiş olduğunuz örnek dosyaların listesini görebilirsiniz. Listeden pozitif dosyalardan birini seçin ve görüntüleyicide görüntülenir.
3. Açıklama bölümünde Yeni'yi ve **ardından** Boş'a **tıklayın**.
4. Açıklama **oluştur sayfasında** :</br>
    a. Ad **yazın (** örneğin, "Açıklama Bloğu").</br>
    b. **Tür'leri seçin**. Örnek için Tümcecik **listesi'ne tıklayın** (bir metin dizesi ekleyin).</br>
    c. Buraya **yazın kutusuna** dizeyi yazın. Örnek için "Ek açıklama talebi" ekleyin. Dizenin büyük **/büyük/harfe** duyarlı olması gerekirse Büyük/harfe duyarlı'ı seçin.</br>
    d. **Kaydet**'e tıklayın.

    ![Açıklama oluşturma.](../media/content-understanding/explanation.png) 
    
5. İçerik merkezi artık, oluşturduğunuz açıklamanın, kalan etiketlenmiş örnek dosyaları doğru tanımlanacak kadar eksiksiz olup olmadığını denetler ve bu şekilde pozitif ve negatif örneklerdir. Eğitim **tamamlandıktan sonra** Eğitim dosyaları **bölümünde** Değerlendirme sütununu kontrol edin ve sonuçları bulun. Oluşturduğunuz açıklamalar pozitif veya **negatif** olarak etiketleni aynı değere yettiyse dosyalar Eşleşme değerini gösterir.

    ![Değer eşle.](../media/content-understanding/match.png) 

    Etiketli **dosyalarda bir Eşleşme** eşleşmesi alırsanız, belge türünü tanımlamak için modele daha fazla bilgi sağlamak için ek bir açıklama oluşturmanız gerekir. Bu durumda, eşleşmeyen bilgilerin neden olduğu hakkında daha fazla bilgi almak için dosyaya tıklayın.

Bir ayıklayı eğitime tamamlanın, o eğitimli ayıklaıcı açıklama olarak kullanılabilir. Açıklamalar **bölümünde** , bu bir Model başvurusu olarak **gösterilir**.

![Model başvurusu türünü gösteren Açıklamalar bölümünün ekran görüntüsü.](../media/content-understanding/explanations-model-reference.png)

## <a name="test-your-model"></a>Modelinizi test etmek

Etiketli örnek dosyalarınız için bir eşleşme aldısanız, artık modelinizi daha önce hiç görene kadar etiketsiz kalan örnek dosyalarınız üzerinde test edin. Bu isteğe bağlıdır, ancak modeli daha önce kullanmadan önce fitness'i veya hazırlığı değerlendirmek için, modeli daha önce kullanmamış olduğu dosyalar üzerinde test etmek için yararlı bir adımdır.

1. Model giriş sayfasından Test **sekmesini** seçin. Bu, modeli etiketsiz örnek dosyalarınız üzerinde çalıştırır.
2. **Sına dosyaları listesinde**, örnek dosyalarınız görüntülenir ve modelin bunları pozitif veya negatif olarak tahmin verip öngördüğü gösterilir. Belgelerinizi belirlemede sınıflandırıcının ne kadar etkili olduğunu belirlemenize yardımcı olması için bu bilgileri kullanın.

    ![Etiketsiz dosyalar testi.](../media/content-understanding/test-on-files.png) 

## <a name="see-also"></a>Ayrıca Bkz
[Ayıklaıcı oluşturma](create-an-extractor.md)

[Belge Anlama'ya genel bakış](document-understanding-overview.md)

[Açıklama türleri](explanation-types-overview.md)

[Model uygulama](apply-a-model.md) 

[SharePoint Syntex Modu](accessibility-mode.md)