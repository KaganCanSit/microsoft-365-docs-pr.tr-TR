---
title: Microsoft SharePoint Syntex'de faturalardan veya makbuzlardan bilgi ayıklamak için önceden oluşturulmuş bir model kullanma
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
description: SharePoint Syntex'da önceden oluşturulmuş bir model oluşturmayı ve yapılandırmayı öğrenin.
ms.openlocfilehash: f3b262ca94e0bfc6886a2ce84ae614569c584bf1
ms.sourcegitcommit: 46e796c6b76a01516c48977335bbf5076ca74a06
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2022
ms.locfileid: "64738419"
---
# <a name="use-a-prebuilt-model-to-extract-info-from-invoices-or-receipts-in-microsoft-sharepoint-syntex"></a>Microsoft SharePoint Syntex'de faturalardan veya makbuzlardan bilgi ayıklamak için önceden oluşturulmuş bir model kullanma

Önceden oluşturulmuş modeller, belgeleri ve belgelerdeki yapılandırılmış bilgileri tanımak için önceden eğitilir. Sıfırdan yeni bir özel model oluşturmak yerine, kuruluşunuzun gereksinimlerine uygun belirli alanlar eklemek için önceden eğitilmiş mevcut bir modeli yineleyebilirsiniz. 

Şu anda önceden oluşturulmuş iki model vardır: fatura ve makbuz.

- *Fatura önceden oluşturulmuş modeli*, satış faturalarından önemli bilgileri analiz eder ve ayıklar. API faturaları çeşitli biçimlerde analiz eder ve müşteri adı, faturalama adresi, son tarih ve son ödeme tutarı gibi [önemli fatura bilgilerini ayıklar](/azure/applied-ai-services/form-recognizer/concept-invoice#field-extraction) .

- Önceden *oluşturulmuş makbuz modeli* , satış makbuzlarından önemli bilgileri analiz eder ve ayıklar. API basılı ve el yazısı makbuzları analiz eder ve satıcı adı, satıcı telefon numarası, işlem tarihi, vergi ve işlem toplamı gibi [önemli makbuz bilgilerini ayıklar](/azure/applied-ai-services/form-recognizer/concept-receipt#field-extraction) .

Önceden oluşturulmuş ek modeller gelecek sürümlerde kullanıma sunulacaktır.

## <a name="create-a-prebuilt-model"></a>Önceden oluşturulmuş bir model oluşturma

Belgeleri SharePoint Syntex'de sınıflandırmak üzere önceden oluşturulmuş bir model oluşturmak için bu adımları izleyin.

1. **Modeller** sayfasında **Model oluştur'u** seçin.

    ![Model oluştur düğmesini gösteren Modeller sayfasının ekran görüntüsü.](../media/content-understanding/prebuilt-create-model-button.png) 

2. **Model oluştur** panelinin **Ad** alanına modelin adını yazın.

    ![Kullanılabilir model türlerini gösteren Yeni belge anlama modeli panelinin ekran görüntüsü.](../media/content-understanding/prebuilt-create-panel.png) 

3. **Model türü** bölümünde, önceden oluşturulmuş modellerden birini seçin:
   - **Fatura işleme önceden oluşturulmuş**
   - **Makbuz işleme önceden oluşturulmuş**

   Önceden oluşturulmuş bir model yerine geleneksel, eğitilmemiş bir belge anlama modeli oluşturmak istiyorsanız **Özel belge anlama'yı** seçin.

4. İçerik türünü değiştirmek veya bekletme etiketi eklemek istiyorsanız **Gelişmiş ayarlar'ı** seçin.

    > [!NOTE]
    > Duyarlılık etiketleri şu anda önceden oluşturulmuş modeller için kullanılamaz.

5. **Oluştur**’u seçin. Model **Modeller** kitaplığına kaydedilir.

## <a name="add-a-file-to-analyze"></a>Analiz etmek için dosya ekleme

1. **Modeller** sayfasındaki **Analiz için dosya ekle** bölümünde **Dosya ekle'yi** seçin.

    ![Analiz etmek için dosya ekle bölümünü gösteren yeni modeller sayfasının ekran görüntüsü.](../media/content-understanding/prebuilt-add-file-to-analyze.png) 

2. **Modeli analiz etmek için dosyalar** sayfasında, kullanmak istediğiniz dosyayı bulmak için **Ekle'yi** seçin.

    ![Model analiz etmek için Dosyalar sayfasının Ekle düğmesini gösteren ekran görüntüsü.](../media/content-understanding/prebuilt-add-file-button.png) 

3. **Eğitim dosyaları kitaplığından dosya ekle** sayfasında dosyayı seçin ve ardından **Ekle'yi** seçin.

    ![Eğitim dosyaları kitaplığından dosya ekle sayfasının ekran görüntüsü.](../media/content-understanding/prebuilt-add-file-from-training-library.png) 

6. **Modeli analiz etmek için dosyalar** sayfasında **İleri'yi** seçin.

## <a name="select-extractors-for-your-model"></a>Modeliniz için ayıklayıcıları seçme

Ayıklayıcı ayrıntıları sayfasında, sağ tarafta belge alanını ve sol tarafta **Ayıklayıcılar** panelini görürsünüz. **Ayıklayıcılar** paneli, belgede tanımlanan ayıklayıcıların listesini gösterir.

   ![Ayıklayıcı ayrıntıları sayfasının ve Ayıklayıcı panelinin ekran görüntüsü.](../media/content-understanding/prebuilt-extractor-details-page.png) 

Belge alanında yeşil renkle vurgulanan varlık alanları, dosyayı analiz ederken model tarafından algılanan öğelerdir. Ayıklamak için bir varlık seçtiğinizde, vurgulanan alan maviye dönüşür. Daha sonra varlığı eklememeye karar verirseniz, vurgulanan alan griye dönüşür. Vurgular, seçtiğiniz ayıklayıcıların geçerli durumunu görmeyi kolaylaştırır.

> [!TIP]
> Varlık alanlarını okumak için gerektiğinde yakınlaştırmak veya uzaklaştırmak için farenizdeki kaydırma tekerleğini veya belge alanının altındaki denetimleri kullanabilirsiniz.

### <a name="select-an-extractor-entity"></a>Ayıklayıcı varlığı seçme

Tercihinize bağlı olarak, belge alanından veya **Ayıklayıcılar** panelinden bir ayıklayıcı seçebilirsiniz.
 
- Belge alanından bir ayıklayıcı seçmek için varlık alanını seçin.

    ![Varlık alanının nasıl seçiliyor olduğunu gösteren belge alanının ekran görüntüsü.](../media/content-understanding/prebuilt-document-area-select-field.png) 

- **Ayıklayıcılar** panelinden bir ayıklayıcı seçmek için varlık adının sağındaki onay kutusunu seçin.

    ![Varlık alanı seçmeyi gösteren Ayıklayıcılar panelinin ekran görüntüsü.](../media/content-understanding/prebuilt-extractors-panel-select-field.png) 

Bir ayıklayıcı seçtiğinizde, belge alanında **Ayıklayıcı seç?** kutusu görüntülenir. Kutu, ayıklayıcı adını, özgün değeri ve ayıklayıcı olarak seçme seçeneğini gösterir. Sayılar veya tarihler gibi belirli veri türleri için ayıklanan bir değer de gösterilir.

   ![Ayıklayıcı ayrıntıları sayfasındaki Ayıklayıcı seç kutusunun ekran görüntüsü.](../media/content-understanding/prebuilt-select-distractor-box.png) 

Özgün değer, belgedeki değerdir. Ayıklanan değer, SharePoint sütununda yazılacak değerdir. Model bir kitaplığa uygulandığında, belgede nasıl görünmesini istediğinizi belirtmek için sütun biçimlendirmesini kullanabilirsiniz.

Kullanmak istediğiniz ek ayıklayıcıları seçmeye devam edin. Bu model yapılandırması için analiz etmek üzere başka dosyalar da ekleyebilirsiniz.

## <a name="rename-an-extractor"></a>Ayıklayıcıyı yeniden adlandırma

Ayıklayıcıyı model giriş sayfasından veya **Ayıklayıcılar** panelinden yeniden adlandırabilirsiniz. Model kitaplığa uygulandığında bu adlar sütun adları olarak kullanılacağından, seçili ayıklayıcıları yeniden adlandırmayı düşünebilirsiniz.

Model giriş sayfasından ayıklayıcıyı yeniden adlandırmak için:

1. **Ayıklayıcılar** bölümünde, yeniden adlandırmak istediğiniz ayıklayıcıyı ve ardından **Yeniden Adlandır'ı** seçin.

    ![Yeniden Adlandır seçeneğinin vurgulandığı Ayıklayıcılar bölümünün ekran görüntüsü.](../media/content-understanding/prebuilt-model-page-rename-extractor.png) 

2. **Varlığı ayıklayıcıyı yeniden adlandır** panelinde ayıklayıcının yeni adını girin ve Yeniden **Adlandır'ı** seçin.

**Ayıklayıcılar** panelinden ayıklayıcıyı yeniden adlandırmak için:

1. Yeniden adlandırmak istediğiniz ayıklayıcıyı ve ardından **Yeniden Adlandır'ı** seçin.

    ![Ayıklayıcıyı yeniden adlandırmayı gösteren Ayıklayıcılar panelinin ekran görüntüsü.](../media/content-understanding/prebuilt-extractors-panel-rename-field.png) 

2. **Ayıklayıcıyı yeniden adlandır** kutusuna ayıklayıcının yeni adını girin ve yeniden **adlandır'ı** seçin.

## <a name="apply-the-model"></a>Modeli uygulama

- Değişiklikleri kaydetmek ve model giriş sayfasına dönmek için **Ayıklayıcılar** panelinde **Kaydet ve çık'ı** seçin.

- Modeli kitaplığa uygulamaya hazırsanız belge alanında **İleri'yi** seçin. **Kitaplığa ekle** panelinde, modeli eklemek istediğiniz kitaplığı seçin ve ardından **Ekle'yi** seçin.

## <a name="change-the-view-in-a-document-library"></a>Belge kitaplığındaki görünümü değiştirme

[!INCLUDE [Change the view in a document library](../includes/change-library-view.md)]

