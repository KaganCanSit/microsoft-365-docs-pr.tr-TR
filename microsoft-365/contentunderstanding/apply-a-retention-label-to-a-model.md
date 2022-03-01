---
title: SharePoint Syntex'da bir modele bekletme SharePoint Syntex
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
description: yeni bir e-SharePoint Syntex'de modele bekletme SharePoint Syntex.
ms.openlocfilehash: 112b48af5e07d09faab61bd656c5629b449d9a1c
ms.sourcegitcommit: 400ef9ac34247978e3de7ecc0b376c4abb6c99d8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/27/2022
ms.locfileid: "63010879"
---
# <a name="apply-a-retention-label-to-a-model-in-sharepoint-syntex"></a>SharePoint Syntex'da bir modele bekletme SharePoint Syntex

</br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4GydO]  

</br>


Microsoft web sitesinde bir [modele](../compliance/retention.md) kolayca bekletme etiketi SharePoint Syntex. Bunu hem belge anlama hem de form işleme modelleri için yapabilirsiniz.

Bekletme etiketleri, modellerinizi tanımları olan belgelere bekletme ayarları uygulamanıza izin sağlar.  Örneğin, modelinizin yalnızca belge kitaplığınıza yüklenen Sigorta bildirimi belgelerini  tanımlamasını değil, ayrıca bu belgeler belirtilen süre boyunca (örneğin, sonraki beş ay)  belge kitaplığından silinemez.

Modelinizin giriş sayfasındaki model ayarları aracılığıyla modelinize önceden var olan bir bekletme etiketi uygulayabilirsiniz. 

> [!Important]
> Bekletme etiketlerinin belgenize uygulanabilecek anlama modellerinin olması için, etiketlerin belge kitaplığında [](../compliance/file-plan-manager.md#create-retention-labels) [oluşturularak](../compliance/create-apply-retention-labels.md#how-to-publish-retention-labels) Microsoft 365 uyumluluk merkezi.

## <a name="to-add-a-retention-label-to-a-document-understanding-model"></a>Belge anlama modeline bekletme etiketi eklemek için

1. Model giriş sayfasında Model **ayarları'ı seçin**.</br>
2. **Model ayarları'nın** **Güvenlik** ve uyumluluk bölümünde, modele uygulayabilecek  bekletme etiketlerinin listesini görmek için Bekletme etiketi menüsünü seçin.</br>
 ![Bekletme etiketi menüsü.](../media/content-understanding/retention-labels-menu.png)</br> 
3. Modele uygulamak istediğiniz bekletme etiketini seçin ve ardından Kaydet'i **seçin**.</br>

Bekletme etiketini modelinize kaydettikten sonra, aşağıdakilere uygulayabilirsiniz:
- Yeni belge kitaplığı
- Modelin zaten uygulandığı belge kitaplığı
 
## <a name="apply-the-retention-label-to-a-document-library-to-which-the-model-is-already-applied"></a>Bekletme etiketini modelin zaten uygulandığı belge kitaplığına uygulama

Belge anlama modeliniz bir belge kitaplığına zaten uygulanmışsa, bekletme etiketi güncelleştirmenizi belge kitaplığına uygulamak için şunları yapabilirsiniz:</br>

1. Model giriş sayfasında, Bu **modelin** olduğu kitaplıklar bölümünde, bekletme etiketi güncelleştirmesini uygulamak istediğiniz belge kitaplığını seçin. </br> 
2. **Eşitle'yi seçin**. </br>
 ![Eşitleme modeli.](../media/content-understanding/sync-model.png)</br> 


Güncelleştirmeyi uyguladıktan ve modelinize eşitledikten sonra, aşağıdaki işlemi yaparak bunun uygulandığını onaylayın:

1. İçerik merkezinde, Bu **modelin** uygulandığı kitaplıklar bölümünde, güncelleştirilmiş modelinizin uygulandığı kitaplıma tıklayın. </br>
2. Belge kitaplığı görünümde, model özelliklerini kontrol etmek için bilgi simgesini seçin.</br>  
3. Etkin **modeller listesinde** güncelleştirilmiş modelinizi seçin.</br>
4. Bekletme **etiketi bölümünde** , uygulanan bekletme etiketinin adını göreceğiz.</br>


Modelinizin belge kitaplığınıza gelen görünüm sayfasında yeni bir **Bekletme etiketi** sütunu görüntülenir.  Modeliniz, ait olduğu içerik türüne ait olarak tanımları dosyaları sınıflandırarak kitaplık görünümünde listeleye kadar, Bekletme etiketi sütunu model üzerinden etikete uygulanmış olan bekletme etiketinin adını da gösterir.


Örneğin, *modelin tanımları* olan tüm Sigorta bildirimi belgelerine İş bekletme etiketi  de uygulanır ve bu şekilde beş ay süreyle belge kitaplığından silinmeleri önlenmiş olur. Belge kitaplığından dosyayı silebilir bir girişimde bulunsa, uygulanan bekletme etiketi nedeniyle dosyaya izin verilme olmadığını söyleyen bir hata görüntülenir.

## <a name="to-add-a-retention-label-to-a-form-processing-model"></a>Form işleme modeline bekletme etiketi eklemek için

> [!Important]
> Bekletme etiketlerinin form işleme modelinize uygulanabilecek olması için, etiketlerin oluşturması ve yazdırması [](../compliance/file-plan-manager.md#create-retention-labels) Microsoft 365 uyumluluk merkezi.[](../compliance/create-apply-retention-labels.md#how-to-publish-retention-labels)

Bir model oluştururken bir form işleme modeline bekletme etiketi uygulayabilir veya bunu var olan bir modele uygulayabilirsiniz.

### <a name="to-add-a-retention-label-when-you-create-a-form-processing-model"></a>Form işleme modeli  oluşturma sırasında bekletme etiketi eklemek için

1. Yeni bir [form işleme modeli oluştururken Gelişmiş ayarlar'ı](./create-a-form-processing-model.md) <b>seçin.</b>
2. Gelişmiş <b>ayarlar'da</b>, <b>Bekletme etiketi</b> bölümünde, menüyü seçin ve sonra modele uygulamak istediğiniz bekletme etiketini seçin.</b>

 
     ![Yeni form işleme modeline ekleyin.](../media/content-understanding/retention-label-forms.png)</br>

3.  Kalan model ayarlarınızı tamamlandıktan sonra modelinizi oluşturmak için <b>Oluştur'a</b> tıklayın.

### <a name="to-add-a-retention-label-to-an-existing-form-processing-model"></a>Mevcut form işleme modeline bekletme etiketi eklemek için

Mevcut form işleme modeline farklı şekillerde bekletme etiketi  ekleyebilirsiniz:
- Belge kitaplığında Otomatikleştir menüsü aracılığıyla
- Belge kitaplığında Etkin model ayarları aracılığıyla 


#### <a name="to-add-a-retention-label-to-an-existing-form-processing-model-through-the-automate-menu"></a>Var olan form işleme modeline Otomatikleştir menüsü aracılığıyla bekletme etiketi eklemek için

Modelin uygulandığı belge kitaplığında Otomatikleştir menüsü aracılığıyla sahip olduğunuz mevcut form işleme modeline bir bekletme etiketi ekleyebilirsiniz.


1. Form işleme modelinin uygulandığı belge kitaplığında Otomatik başlat menüsünü seçin, <b>AI Oluşturucusu'nu</b> seçin ve sonra da Form işleme modeli ayrıntılarını <b>görüntüle'yi seçin</b>.<b></b>

   ![Menüyü otomatikleştir'i seçin.](../media/content-understanding/automate-menu.png)</br>

2. Model ayrıntılarında, <b>Bekletme Etiketi bölümünde</b> , uygulamak istediğiniz bekletme etiketini seçin.  Ardından <b>Kaydet'i seçin</b>.

     ![Varolan bir form işleme modeline ekleme.](../media/content-understanding/retention-label-model-details.png)</br> 

#### <a name="to-add-a-retention-label-to-an-existing-form-processing-model-in-the-active-model-settings"></a>Etkin model ayarlarında mevcut form işleme modeline bekletme etiketi eklemek için

Modelin uygulandığı belge kitaplığında Etkin model ayarlarıyla sahip olduğunuz mevcut form işleme modeline bekletme etiketi ekleyebilirsiniz.

1. Modelin SharePoint olan belge kitaplığında, Etkin modelleri görüntüle simgesini seçin <b>ve ardından Etkin</b> modelleri <b>görüntüle'yi seçin</b>.</b>

   ![Etkin modelleri görüntüleme.](../media/content-understanding/info-du.png)</br> 

2. Etkin <b>modellerde</b>, bekletme etiketini uygulamak istediğiniz form işleme modelini seçin.

     ![Model ayrıntıları.](../media/content-understanding/retention-label-model-details.png)</br> 


3. Model ayrıntılarında, <b>Bekletme Etiketi bölümünde</b> , uygulamak istediğiniz bekletme etiketini seçin.  Ardından <b>Kaydet'i seçin</b>.

> [!NOTE]
> Düzenlenebilir olması için model ayarları bölmesinin model sahibi siz olun. 


## <a name="see-also"></a>Ayrıca Bkz
[Sınıflandırıcı oluşturma](create-a-classifier.md)

[Ayıklaıcı oluşturma](create-an-extractor.md)

[Belge Anlama'ya genel bakış](document-understanding-overview.md)
