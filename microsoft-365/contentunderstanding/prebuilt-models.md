---
title: Microsoft Web Sitesinde faturalardan veya faturalardan bilgileri ayıklamak için önceden oluşturulmuş bir model SharePoint Syntex
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
description: Önceden oluşturulmuş bir modeli nasıl oluşturacaklarını ve yapılandıracaklarını öğrenmek için SharePoint Syntex.
ms.openlocfilehash: 7867fe197fd53e6095f51869fc5aaad18af9157b
ms.sourcegitcommit: cdb90f28e59f36966f8751fa8ba352d233317fc1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2022
ms.locfileid: "63401056"
---
# <a name="use-a-prebuilt-model-to-extract-info-from-invoices-or-receipts-in-microsoft-sharepoint-syntex"></a>Microsoft Web Sitesinde faturalardan veya faturalardan bilgileri ayıklamak için önceden oluşturulmuş bir model SharePoint Syntex

Önceden oluşturulmuş modeller belgeleri ve belgelerde yer alan yapılandırılmış bilgileri tanıyacak şekilde kısıtlanmıştır. Sıfırdan yeni bir özel model oluşturmak yerine, var olan bir kısıtlanmış modelin üzerinde kuruma uygun belirli alanlar eklemek için bu modeli iterebilirsiniz. 

Şu anda, önceden oluşturulmuş iki model vardır: fatura ve makbuz.

- Önceden *oluşturulmuş fatura modeli,* satış faturalarından önemli bilgileri analiz eder ve ayıklar. API, faturaları çeşitli biçimlerde analiz eder ve müşteri [](/azure/applied-ai-services/form-recognizer/concept-invoice#field-extraction) adı, fatura adresi, son tarih ve ödeme tutarı gibi önemli fatura bilgilerini ayıklar.

- Önceden *oluşturulmuş alındı modeli,* satış bilgilerinden önemli bilgileri analiz eder ve ayıklar. API basılı ve el yazısıyla alınan faturaları analiz eder ve satıcı [](/azure/applied-ai-services/form-recognizer/concept-receipt#field-extraction) adı, satıcı telefon numarası, işlem tarihi, vergi ve işlem toplamı gibi önemli makbuz bilgilerini ayıklar.

Önceden oluşturulmuş ek modeller gelecek sürümlerde kullanılabilir olacaktır.

## <a name="create-a-prebuilt-model"></a>Önceden oluşturulmuş bir model oluşturma

Belgeleri önceden sınıflandıracak şekilde önceden oluşturulmuş bir model oluşturmak için bu SharePoint Syntex.

1. Modeller **sayfasında Model** **oluştur'a tıklayın**.

    ![Model oluştur düğmesinin görüntü olduğu Modeller sayfasının ekran görüntüsü.](../media/content-understanding/prebuilt-create-model-button.png) 

2. Model **oluştur panelindeki** **Ad alanına** modelin adını yazın.

    ![Kullanılabilir model türlerini gösteren Yeni belge anlama model panelinin ekran görüntüsü.](../media/content-understanding/prebuilt-create-panel.png) 

3. Model **türü bölümünde** , önceden oluşturulmuş modellerden birini seçin:
   - **Önceden fatura işleme**
   - **Alındı bilgisi önceden işlendi**

   Önceden oluşturulmuş bir model yerine geleneksel, kısıtlanmamış bir belge anlama modeli oluşturmak için Özel belge **anlama'ya tıklayın**.

4. İçerik türünü değiştirmek veya bekletme etiketi eklemek için Gelişmiş **ayarlar'ı seçin**.

    > [!NOTE]
    > Duyarlılık etiketleri şu anda önceden oluşturulmuş modeller için kullanılamaz.

5. **Oluştur**’u seçin. Model, Modeller **kitaplığına kaydedilir** .

## <a name="add-a-file-to-analyze"></a>Çözümlemek için dosya ekleme

1. Modeller **sayfasında** , Çözüm için **dosya ekle bölümünde Dosya** **ekle'yi seçin**.

    ![Çözüm için dosya ekle bölümünü gösteren yeni modeller sayfasının ekran görüntüsü.](../media/content-understanding/prebuilt-add-file-to-analyze.png) 

2. Model **analiz etmek için dosyalar sayfasında** , kullanmak **istediğiniz dosyayı** bulmak için Ekle'yi seçin.

    ![Ekle düğmesinin görüntü olduğu model sayfasını analiz etmek için dosyalar sayfasının ekran görüntüsü.](../media/content-understanding/prebuilt-add-file-button.png) 

3. Eğitim **dosyaları kitaplığından dosya ekle sayfasında dosyayı** seçin ve sonra da Ekle'yi **seçin**.

    ![Eğitim dosyaları kitaplığı sayfasından Dosya ekle sayfasının ekran görüntüsü.](../media/content-understanding/prebuilt-add-file-from-training-library.png) 

6. Model analiz **etmek için dosyalar sayfasında Sonraki'yi** **seçin**.

## <a name="select-extractors-for-your-model"></a>Modeliniz için ayıklaıcıları seçme

Ayıklanan ayrıntıları sayfasında, sağ tarafta belge alanı ve sol tarafta **Ayıklar** paneli gösterilir. **Ayıklar** paneli, belgede tanımlanan ayıklaıcıların listesini gösterir.

   ![Ayıklaıcı ayrıntıları sayfasının ve Ayıkla panelinin ekran görüntüsü.](../media/content-understanding/prebuilt-extractor-details-page.png) 

Belge alanında yeşil renkle vurgulanan varlık alanları, dosya çözümlandığında model tarafından algılanan öğelerdir. Ayıklanan bir varlık seçince, vurgulanan alan mavi olarak değişir. Sonradan varlığı dahil etmek yermeyecek şekilde karar verirsiniz, vurgulanan alan gri olarak değişir. Vurgular, seçtiğiniz ayıklayanların geçerli durumunu görmelerini kolaylaştırır.

> [!TIP]
> Varlık alanlarını okumak üzere gerekirse yakınlaştırmak veya uzaklaştırmak için farenizin veya belge alanı altındaki denetimlerin kaydırma tekerleğini kullanabilirsiniz.

### <a name="select-an-extractor-entity"></a>Bir ayıklayıcı varlık seçme

Tercihlerinize bağlı olarak, belge alanında veya Ayıklar **panelinden** bir ayıklaıcı seçebilirsiniz.
 
- Belge alanından bir ayıklaıcı seçmek için varlık alanını seçin.

    ![Varlık alanı seçmeyi gösteren belge alanını gösteren ekran görüntüsü.](../media/content-understanding/prebuilt-document-area-select-field.png) 

- Ayıklar panelinden bir **ayıklaıcı** seçmek için varlık adının sağ onay kutusunu seçin.

    ![Bir varlık alanı seçmeyi gösteren Ayıklar panelinin ekran görüntüsü.](../media/content-understanding/prebuilt-extractors-panel-select-field.png) 

Bir ayıklaıcıyı **işaretlendiğinde, belge alanında** bir Ayıkla seçici seç? kutusu görüntülenir. Kutuda ayıklaıcı adı, özgün değer ve bunu bir ayıklaıcı olarak seçme seçeneği görüntülenir. Sayılar veya tarihler gibi belirli veri türlerinde ayıklanan bir değer de gösterir.

   ![Ayıkla ayrıntıları sayfasındaki Ayıkla seçici seç kutusunun ekran görüntüsü.](../media/content-understanding/prebuilt-select-distractor-box.png) 

Özgün değer, aslında belge içinde yer alan değerdir. Ayıklanan değer, sütunda sütuna yazıldığı SharePoint. Model kitaplı kitaplara uygulandığında, belgeye nasıl bakacaklarını belirtmek için sütun biçimlendirmesini kullanabilirsiniz.

Kullanmak istediğiniz diğer ayıklaıcıları seçmeye devam eder. Ayrıca, bu model yapılandırmasını çözümlemek için başka dosyalar da ebilirsiniz.

## <a name="rename-an-extractor"></a>Ayıklayı yeniden adlandırma

Bir ayıklayı model giriş sayfasından veya Ayıklar panelinden **yeniden adlandırabilirsiniz** . Model kitaplı kitaplara uygulandığında sütun adları olarak kullanılacak olması nedeniyle seçilen ayıkıcıları yeniden adlandırabilirsiniz.

Model giriş sayfasından bir ayıklaıcıyı yeniden adlandırmak için:

1. Ayıklar **bölümünde,** yeniden adlandırmak istediğiniz ayıklaıcıyı seçin ve sonra da Yeniden Adlandır'ı **seçin**.

    ![Yeniden Adlandır seçeneğinin vurgulu olduğu Ayıklayanlar bölümünün ekran görüntüsü.](../media/content-understanding/prebuilt-model-page-rename-extractor.png) 

2. Varlık **ayıkla ayıkla panelinde** ayıklaıcının yeni adını girin ve Yeniden Adlandır'ı **seçin**.

Ayıklar panelinden bir ayıklayı **yeniden adlandırmak** için:

1. Yeniden adlandırmak istediğiniz ayıkla'ya ve sonra Yeniden Adlandır'a **tıklayın**.

    ![Ayıklayanın nasıl yeniden adlandırıl olduğunu gösteren Ayıkla panelinin ekran görüntüsü.](../media/content-understanding/prebuilt-extractors-panel-rename-field.png) 

2. **Ayıklaıcıyı yeniden adlandır** kutusuna ayıklaıcının yeni adını girin ve Yeniden Adlandır'ı **seçin**.

## <a name="apply-the-model"></a>Modeli uygulama

- Değişiklikleri kaydetmek ve model giriş sayfasına dönmek için, Ayıklar **panelinde Kaydet'i** seçin **ve çıkın**.

- Modeli kitaplara uygulamaya hazırsanız, belge alanında Sonraki'yi **seçin**. Kitaplık **ekle panelinde** modeli eklemek istediğiniz kitaplığı seçin ve sonra da Ekle'yi **seçin**.

> [!TIP]
> Belge kitaplığında görünümü, kendi ihtiyaçlarınıza veya tercihlerinize uyacak şekilde değiştirebilirsiniz. Daha fazla bilgi için bkz [. Belge kitaplığında görünümü değiştirme](apply-a-model.md#change-the-view-in-a-document-library).

## <a name="see-also"></a>Ayrıca bkz.

[Belge anlama modeli uygulama](apply-a-model.md)