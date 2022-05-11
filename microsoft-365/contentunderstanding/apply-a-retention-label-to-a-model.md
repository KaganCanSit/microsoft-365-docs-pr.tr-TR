---
title: SharePoint Syntex'da modele bekletme etiketi uygulama
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
description: SharePoint Syntex'da bir modele bekletme etiketi uygulamayı öğrenin.
ms.openlocfilehash: 362b370fa34193e66802e9b0d2c5788785ea92c5
ms.sourcegitcommit: 2d870e06e87b10d9e8ec7a7a8381353bc3bc59c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/11/2022
ms.locfileid: "65349796"
---
# <a name="apply-a-retention-label-to-a-model-in-sharepoint-syntex"></a>SharePoint Syntex'da modele bekletme etiketi uygulama

</br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4GydO]  

</br>

Microsoft SharePoint Syntex'da modele kolayca [bekletme etiketi](../compliance/retention.md) uygulayabilirsiniz. Bunu hem belge anlama hem de form işleme modelleri için yapabilirsiniz.

Bekletme etiketleri, modellerinizin tanımladığınız belgelere bekletme ayarları uygulamanıza olanak tanır.  Örneğin, modelinizin yalnızca belge kitaplığınıza yüklenen *Sigorta bildirimi* belgelerini tanımlamasını değil, aynı zamanda bu belgelerin belirtilen süre boyunca belge kitaplığından silinememesi için (örneğin, sonraki beş ay) onlara bir *İş* saklama etiketi uygulamasını istiyorsunuz.

Modelinizin giriş sayfasındaki model ayarlarınızdan modelinize önceden var olan bir bekletme etiketi uygulayabilirsiniz. 

> [!Important]
> Bekletme etiketlerinin belge anlama modellerinize uygulanabilmek için Microsoft Purview uyumluluk portalı [oluşturulması](../compliance/file-plan-manager.md#create-retention-labels) ve [yayımlanması](../compliance/create-apply-retention-labels.md#how-to-publish-retention-labels) gerekir.

## <a name="to-add-a-retention-label-to-a-document-understanding-model"></a>Belge anlama modeline bekletme etiketi eklemek için

1. Model giriş sayfasında **Model ayarları'nı** seçin.</br>
2. **Model ayarları'ndaki** **Güvenlik ve uyumluluk** bölümünde **Bekletme etiketi** menüsünü seçerek modele uygulayacağınız bekletme etiketlerinin listesini görebilirsiniz.</br>
 ![Bekletme etiketi menüsü.](../media/content-understanding/retention-labels-menu.png)</br> 
3. Modele uygulamak istediğiniz bekletme etiketini seçin ve ardından **Kaydet'i** seçin.</br>

Bekletme etiketini modelinize uyguladıktan sonra şunun için uygulayabilirsiniz:
- Yeni belge kitaplığı
- Modelin zaten uygulandığı belge kitaplığı
 
## <a name="apply-the-retention-label-to-a-document-library-to-which-the-model-is-already-applied"></a>Bekletme etiketini modelin zaten uygulandığı belge kitaplığına uygulama

Belge anlama modeliniz bir belge kitaplığına zaten uygulanmışsa, bekletme etiketi güncelleştirmenizi belge kitaplığına uygulamak üzere eşitlemek için aşağıdakileri yapabilirsiniz:</br>

1. Modelinizin giriş sayfasındaki **Bu modelle kitaplıklar** bölümünde, bekletme etiketi güncelleştirmesini uygulamak istediğiniz belge kitaplığını seçin. </br> 
2. **Eşitle'yi** seçin. </br>
 ![Eşitleme modeli.](../media/content-understanding/sync-model.png)</br> 


Güncelleştirmeyi uyguladıktan ve modelinizle eşitledikten sonra, aşağıdakileri yaparak uygulandığını onaylayabilirsiniz:

1. İçerik merkezindeki **Bu modelle kitaplıklar** bölümünde, güncelleştirilmiş modelinizin uygulandığı kitaplığa tıklayın. </br>
2. Belge kitaplığı görünümünüzde, model özelliklerini denetlemek için bilgi simgesini seçin.</br>  
3. **Etkin modeller** listesinde güncelleştirilmiş modelinizi seçin.</br>
4. **Bekletme etiketi** bölümünde, uygulanan bekletme etiketinin adını görürsünüz.</br>


Belge kitaplığınızdaki modelinizin görünüm sayfasında yeni bir **Bekletme etiketi** sütunu görüntülenir.  Modeliniz, tanımladığı dosyaları içerik türüne ait olarak sınıflandırır ve kitaplık görünümünde listelerken, Bekletme etiketi sütunu model aracılığıyla uygulanan bekletme etiketinin adını da görüntüler.


Örneğin, modelinizin belirlediği tüm *Sigorta bildirimi* belgelerinde de *İş* saklama etiketi uygulanır ve bu da belge kitaplığından beş ay boyunca silinmesini önler. Dosyayı belge kitaplığından silme girişiminde bulunulması durumunda, uygulanan bekletme etiketi nedeniyle dosyaya izin verilmediğini belirten bir hata görüntülenir.

## <a name="to-add-a-retention-label-to-a-form-processing-model"></a>Form işleme modeline bekletme etiketi eklemek için

> [!Important]
> Bekletme etiketlerinin form işleme modelinize uygulanabilmek için Microsoft Purview uyumluluk portalı [oluşturulması](../compliance/file-plan-manager.md#create-retention-labels) ve [yayımlanması](../compliance/create-apply-retention-labels.md#how-to-publish-retention-labels) gerekir.

Bir model oluştururken form işleme modeline bekletme etiketi uygulayabilir veya var olan bir modele uygulayabilirsiniz.

### <a name="to-add-a-retention-label-when-you-create-a-form-processing-model"></a>Form işleme modeli oluştururken bekletme etiketi eklemek için

1. [Yeni bir form işleme modeli oluştururken](./create-a-form-processing-model.md) <b>Gelişmiş ayarlar'ı seçin.</b>
2. <b>Gelişmiş ayarlar'daki</b> <b>Bekletme etiketi</b> bölümünde menüyü ve ardından modele uygulamak istediğiniz bekletme etiketini seçin.</b>

 
     ![Yeni bir form işleme modeline ekleyin.](../media/content-understanding/retention-label-forms.png)</br>

3.  Kalan model ayarlarınızı tamamladıktan sonra modelinizi oluşturmak için <b>Oluştur'u</b> seçin.

### <a name="to-add-a-retention-label-to-an-existing-form-processing-model"></a>Mevcut form işleme modeline bekletme etiketi eklemek için

Mevcut form işleme modeline bekletme etiketi eklemek için farklı yöntemler kullanabilirsiniz:
- Belge kitaplığındaki Otomatikleştir menüsü aracılığıyla
- Belge kitaplığındaki Etkin model ayarları aracılığıyla 


#### <a name="to-add-a-retention-label-to-an-existing-form-processing-model-through-the-automate-menu"></a>Otomatikleştir menüsü aracılığıyla mevcut form işleme modeline bekletme etiketi eklemek için

Sahip olduğunuz mevcut form işleme modeline, modelin uygulandığı belge kitaplığındaki Otomatikleştir menüsü aracılığıyla bekletme etiketi ekleyebilirsiniz.


1. Form işleme modelinin uygulandığı belge kitaplığınızda <b>Otomatikleştir</b> menüsünü, <b>AI Builder'ı</b> ve ardından <b>Form işleme modeli ayrıntılarını görüntüle'yi</b> seçin.

   ![Otomatikleştir menüsü.](../media/content-understanding/automate-menu.png)</br>

2. Model ayrıntılarındaki <b>Bekletme Etiketi</b> bölümünde, uygulamak istediğiniz bekletme etiketini seçin.  Ardından <b>Kaydet'i</b> seçin.

     ![Varolan bir form işleme modeline ekleyin.](../media/content-understanding/retention-label-model-details.png)</br> 

#### <a name="to-add-a-retention-label-to-an-existing-form-processing-model-in-the-active-model-settings"></a>Etkin model ayarlarında mevcut form işleme modeline bekletme etiketi eklemek için

Sahip olduğunuz mevcut form işleme modeline, modelin uygulandığı belge kitaplığındaki Etkin model ayarları aracılığıyla bekletme etiketi ekleyebilirsiniz.

1. Modelin uygulandığı SharePoint belge kitaplığında <b>Etkin modelleri görüntüle</b> simgesini ve ardından <b>Etkin modelleri görüntüle'yi</b> seçin.</b>

   ![Etkin modelleri görüntüleme.](../media/content-understanding/info-du.png)</br> 

2. <b>Etkin modeller'de</b>, bekletme etiketini uygulamak istediğiniz form işleme modelini seçin.

     ![Model ayrıntıları.](../media/content-understanding/retention-label-model-details.png)</br> 


3. Model ayrıntılarındaki <b>Bekletme Etiketi</b> bölümünde, uygulamak istediğiniz bekletme etiketini seçin.  Ardından <b>Kaydet'i</b> seçin.

> [!NOTE]
> Model ayarları bölmesinin düzenlenebilir olması için model sahibi olmanız gerekir. 


## <a name="see-also"></a>Ayrıca bkz.

[Sınıflandırıcı oluşturma](create-a-classifier.md)

[Ayıklayıcı oluşturma](create-an-extractor.md)

[Document Understanding'e genel bakış](document-understanding-overview.md)
