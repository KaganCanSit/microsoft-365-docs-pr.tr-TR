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
description: Microsoft SharePoint Syntex'da sınıflandırıcı oluşturmayı öğrenin.
ms.openlocfilehash: 6c47d2fe2f7f2b67533587f0956281c2b577dbe0
ms.sourcegitcommit: 23e186b46b27a6a4863f507a52a11105afae9726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/15/2022
ms.locfileid: "64882384"
---
# <a name="create-a-classifier-in-microsoft-sharepoint-syntex"></a>Microsoft SharePoint Syntex'de sınıflandırıcı oluşturma


</br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4CL0R]  

</br>

Sınıflandırıcı, belge türünün tanımlanmasını ve sınıflandırmasını otomatikleştirmek için kullanabileceğiniz bir model türüdür. Örneğin, aşağıdaki çizimde gösterildiği gibi, belge kitaplığınıza eklenen tüm *Sözleşme Yenileme* belgelerini tanımlamak isteyebilirsiniz.

![Sözleşme Yenileme belgesi.](../media/content-understanding/contract-renewal.png)

Sınıflandırıcı oluşturmak, modelle ilişkilendirilecek yeni bir [SharePoint içerik türü](/sharepoint/governance/content-type-and-workflow-planning#content-type-overview) oluşturmanıza olanak tanır.

Sınıflandırıcıyı oluştururken modeli tanımlamak için *açıklamalar* oluşturmanız gerekir. Bu, bu belge türünü tutarlı bir şekilde bulmayı beklediğiniz ortak verileri not etmenizi sağlar. 

Modelinizi aynı içerik türüne sahip dosyaları tanımlamak üzere "eğitmek" için belge türü örneklerini ("örnek dosyalar") kullanın.

Sınıflandırıcı oluşturmak için şunları yapmanız gerekir:
1. Modelinize bir ad verin.
2. Örnek dosyalarınızı ekleyin.
3. Örnek dosyalarınızı etiketle.
4. Bir açıklama oluşturun.
5. Modelinizi test edin.

> [!NOTE]
> Modeliniz belge türlerini tanımlamak ve sınıflandırmak için bir sınıflandırıcı kullanıyor olsa da, model tarafından tanımlanan her dosyadan belirli bilgi parçalarını çekmeyi de seçebilirsiniz. Bunu yapmak için modelinize eklenecek bir **ayıklayıcı** oluşturabilirsiniz. Bkz. [Ayıklayıcı oluşturma](create-an-extractor.md).

## <a name="name-your-model"></a>Modelinizi adlandır

Modelinizi oluşturmanın ilk adımı, modelinize bir ad vermektir:

1. İçerik **merkezinden Yeni'yi** ve ardından **Model oluştur'u** seçin.
2. **Yeni belge anlama modeli** bölmesindeki **Ad** alanına modelin adını yazın. Örneğin, sözleşme yenileme belgelerini tanımlamak istiyorsanız modeli *Sözleşme Yenileme* olarak adlandırabilirsiniz.
3. **Oluştur**'u seçin. Bu, model için bir giriş sayfası oluşturur.</br>

    ![Sınıflandırıcı modeli giriş sayfası.](../media/content-understanding/model-home.png)

Model oluşturduğunuzda, yeni bir site içerik türü de oluşturursunuz. İçerik türü, ortak özelliklere sahip bir belge kategorisini temsil eder ve söz konusu içerik için bir sütun veya meta veri özellikleri koleksiyonunu paylaşır. SharePoint içerik türleri [İçerik türleri galerisi](https://support.microsoft.com/office/create-or-customize-a-site-content-type-27eb6551-9867-4201-a819-620c5658a60f) aracılığıyla yönetilir. Bu örnekte, modeli oluşturduğunuzda yeni bir *Sözleşme Yenileme* içerik türü oluşturacaksınız.

Bu modeli, şemasını kullanmak üzere SharePoint <a href="https://go.microsoft.com/fwlink/?linkid=2185074" target="_blank">İçerik türü galerisindeki</a> mevcut bir kurumsal içerik türüyle eşlemek istiyorsanız **Gelişmiş ayarlar'ı** seçin. Enterprise içerik türleri, SharePoint yönetim merkezindeki İçerik Türü Hub'ında depolanır ve kiracıdaki tüm sitelere dağıtılır. Tanımlama ve sınıflandırma konusunda yardımcı olması için şemasından yararlanmak için mevcut bir içerik türünü kullanabilirsiniz ancak modelinizi yine de tanımlamış olduğu dosyalardan bilgi ayıklamak için eğitmeniz gerektiğini unutmayın.</br>

![Gelişmiş ayarlar.](../media/content-understanding/advanced-settings.png)

## <a name="add-your-example-files"></a>Örnek dosyalarınızı ekleme

Modelin giriş sayfasında, modeli belge türünüzü tanımlayacak şekilde eğitmek için ihtiyacınız olacak örnek dosyalarınızı ekleyin. </br>
</br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4D0iX] 

</br>

> [!NOTE]
> Hem sınıflandırıcı hem de [ayıklayıcı eğitimi](create-an-extractor.md) için aynı dosyaları kullanmanız gerekir. Her zaman daha sonra daha fazlasını ekleme seçeneğiniz vardır, ancak genellikle tam bir örnek dosya kümesi eklersiniz. Modelinizi eğitmek için bazılarını etiketleyip kalan etiketsiz olanları test ederek model uygunluklarını değerlendirin. 

Eğitim kümeniz için hem olumlu hem de olumsuz örnekler kullanmak istiyorsunuz:
- Pozitif örnek: Belge türünü temsil eden belgeler. Bunlar her zaman bu tür belgelerde yer alan dizeleri ve bilgileri içerir.
- Negatif örnek: Sınıflandırmak istediğiniz belgeyi temsil etmeyen diğer tüm belgeler. 

Modelinizi eğitmek için en az beş pozitif örnek ve en az bir negatif örnek kullandığınızdan emin olun.  Eğitim işleminden sonra modelinizi test etmek için eklerini oluşturmak istiyorsunuz.

Örnek dosyalar eklemek için:

1. Model giriş sayfasındaki **Örnek dosya ekle** kutucuğunda **Dosya ekle'ye** tıklayın.
2. **Modelinizin örnek dosyalarını seçin** sayfasında, içerik merkezindeki Eğitim dosyaları kitaplığından örnek dosyalarınızı seçin. Bunları henüz oraya yüklemediyseniz, eğitim dosyaları kitaplığına kopyalamak için **Upload** tıklayarak şimdi karşıya yüklemeyi seçin.
3. Modeli eğitmek için kullanılacak örnek dosyalarınızı seçtikten sonra **Ekle'ye** tıklayın.

    ![Örnek dosyaları seçin.](../media/content-understanding/select-sample.png) 

## <a name="label-your-example-files"></a>Örnek dosyalarınızı etiketleme

Örnek dosyalarınızı ekledikten sonra, bunları pozitif veya negatif örnekler olarak etiketlemeniz gerekir.

1. Model giriş sayfasındaki **Dosyaları sınıflandır ve eğitim çalıştır** kutucuğunda **Sınıflandırıcıyı eğit'e** tıklayın.
   Bu, örnek dosyalarınızın listesini gösteren etiket sayfasını görüntüler ve ilk dosya görüntüleyicide görünür.
2. İlk örnek dosyanın en üstündeki görüntüleyicide, dosyanın yeni oluşturduğunuz modelin bir örneği olup olmadığını soran bir metin görmeniz gerekir. Olumlu bir örnekse **Evet'i** seçin. Negatif bir örnekse **Hayır'ı** seçin.
3. Soldaki **Etiketli örnekler** listesinden örnek olarak kullanmak istediğiniz ek dosyaları seçin ve bunları etiketleyin. 

    ![Sınıflandırıcı giriş sayfası.](../media/content-understanding/classifier-home-page.png) 


> [!NOTE]
> Etiket en az beş olumlu örnek. Ayrıca en az bir negatif örneği etiketlemeniz gerekir. 

## <a name="create-an-explanation"></a>Açıklama oluşturma

Sonraki adım, Eğit sayfasında bir açıklama oluşturmanızdır. Açıklama, modelin belgeyi nasıl tanıyacaklarını anlamasına yardımcı olur. Örneğin, Sözleşme Yenileme belgeleri her zaman *ek açıklama isteği* metin dizesi içerir.

> [!Note]
> Ayıklayıcılarla kullanıldığında, belgeden ayıklamak istediğiniz dizeyi bir açıklama tanımlar. 

Açıklama oluşturmak için:

1. Modelin giriş sayfasında Eğit sekmesini seçerek **Eğit** sayfasına gidin.
2. Eğitme sayfasındaki **Eğitilen dosyalar** bölümünde daha önce etiketlediğiniz örnek dosyaların listesini görmeniz gerekir. Listeden pozitif dosyalardan birini seçtiğinizde, bu dosya görüntüleyicide görüntülenir.
3. Açıklama bölümünde **Yeni'yi** ve ardından **Boş'ı** seçin.
4. **Açıklama oluştur** sayfasında:</br>
    a. **Adı** yazın (örneğin, "Açıklama Bloğu").</br>
    b. **Tür'e** tıklayın. Örnek için, metin dizesi eklediğinizden **Tümcecik listesi'ni** seçin.</br>
    c. **Buraya yazın** kutusuna dizeyi yazın. Örnek için "Ek açıklama isteği" ekleyin. Dizenin büyük **/küçük harfe duyarlı olması gerekiyorsa Büyük/** küçük harfe duyarlı seçeneğini belirleyebilirsiniz.</br>
    d. **Kaydet**'e tıklayın.

    ![Açıklama oluşturun.](../media/content-understanding/explanation.png) 
    
5. İçerik merkezi artık oluşturduğunuz açıklamanın, etiketlenmiş diğer örnek dosyaları doğru şekilde tanımlayacak kadar eksiksiz olup olmadığını pozitif ve negatif örnekler olarak denetler. **Eğitilen dosyalar** bölümünde, sonuçları görmek için eğitim tamamlandıktan sonra **Değerlendirme** sütununu denetleyin. Oluşturduğunuz açıklamalar pozitif veya negatif olarak etiketlediğiniz açıklamalarla eşleşecek kadar yeterliyse dosyalar **Match** değerini gösterir.

    ![Değeri eşleştirin.](../media/content-understanding/match.png) 

    Etiketli **dosyalarda Uyuşmazlık** alırsanız, belge türünü tanımlamak için modele daha fazla bilgi sağlamak için ek bir açıklama oluşturmanız gerekebilir. Bu durumda, uyuşmazlık neden oluştuğu hakkında daha fazla bilgi edinmek için dosyaya tıklayın.

Bir ayıklayıcı eğitildikten sonra, bu eğitilen ayıklayıcı açıklama olarak kullanılabilir. **Açıklamalar** bölümünde, bu bir **Model başvurusu** olarak gösterilir.

![Model başvurusu türünü gösteren Açıklamalar bölümünün ekran görüntüsü.](../media/content-understanding/explanations-model-reference.png)

## <a name="test-your-model"></a>Modelinizi test etme

Etiketli örnek dosyalarınızda bir eşleşme aldıysanız, artık modelinizi modelin daha önce görmediği etiketlenmemiş kalan örnek dosyalarınızda test edebilirsiniz. Bu isteğe bağlıdır, ancak modeli kullanmadan önce modelin daha önce görmediği dosyalarda test ederek "uygunluk" veya hazır olma durumunu değerlendirmek için kullanışlı bir adımdır.

1. Model giriş sayfasında **Test** sekmesini seçin. Bu, modeli etiketlenmemiş örnek dosyalarınızda çalıştırır.
2. **Test dosyaları** listesinde, örnek dosyalarınız görüntülenir ve modelin bunların pozitif mi yoksa negatif mi olacağını tahmin edip etmediğini gösterir. Sınıflandırıcınızın belgelerinizi tanımlamadaki etkinliğini saptamaya yardımcı olması için bu bilgileri kullanın.

    ![Etiketlenmemiş dosyaların testi.](../media/content-understanding/test-on-files.png) 

## <a name="see-also"></a>Ayrıca bkz.

[Ayıklayıcı oluşturma](create-an-extractor.md)

[Document Understanding'e genel bakış](document-understanding-overview.md)

[Açıklama türleri](explanation-types-overview.md)

[Model uygulama](apply-a-model.md) 

[erişilebilirlik modunu SharePoint Syntex](accessibility-mode.md)