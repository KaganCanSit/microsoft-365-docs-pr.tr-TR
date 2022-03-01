---
title: Microsoft SharePoint Syntex'da bir modele duyarlılık SharePoint Syntex
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
description: Bir veya daha fazla bilgi için bir modele duyarlılık SharePoint Syntex.
ms.openlocfilehash: 624b441084b418d2bcfc3ab6b623da0f5a969fe8
ms.sourcegitcommit: b6ab10ba95e4b986065c51179ead3810cc1e2a85
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/15/2021
ms.locfileid: "63018851"
---
# <a name="apply-a-sensitivity-label-to-a-model-in-microsoft-sharepoint-syntex"></a>Microsoft SharePoint Syntex'da bir modele duyarlılık SharePoint Syntex

Microsoft SharePoint Syntex'de modelleri [anlamak](../compliance/sensitivity-labels.md) için belgeye kolayca duyarlılık SharePoint Syntex. Bu özellik henüz form işleme modellerinde kullanılamaz.

Duyarlılık etiketleri modellerinizi tanımları olan belgelere şifreleme uygulamanıza izin sağlar. Örneğin, modelinizin yalnızca belge kitaplığınıza yüklenen banka hesabı numaraları veya kredi kartı numaraları içeren mali belgeleri tanımlamanın yanı sıra, bu içeriğe kimlerin eriş erişeceklerini ve nasıl kullanılamayacaklarını kısıtlamak için şifreleme ayarlarıyla yapılandırılmış bir duyarlılık etiketi de uygulamanızı istiyor olun. SharePoint Syntex uygun etiket [düzeni kurallarına](../compliance/apply-sensitivity-label-automatically.md#how-multiple-conditions-are-evaluated-when-they-apply-to-more-than-one-label) uymaz ve ayrıca kullanıcı tarafından dosyaya el ile uygulanan mevcut bir etiketin üzerine yazılmaz. 

Modelinizin giriş sayfasındaki model ayarları aracılığıyla modelinize önceden var olan bir duyarlılık etiketi uygulayabilirsiniz. Model ayarlarından seçilk için etiketin zaten yayımlanmış olması gerekir.

> [!Important]
> Duyarlılık etiketlerinin belgenize uygulanarak modelleri anlaması için, etiketlerin Uyumluluk Merkezi'nde [oluşturularak Microsoft 365 yayımlanır](../admin/security-and-compliance/set-up-compliance.md).

## <a name="add-a-sensitivity-label-to-a-document-understanding-model"></a>Belge anlama modeline duyarlılık etiketi ekleme

1. Model giriş sayfasında Model **ayarları'ı seçin**.

   ![Model ayarları seçeneğinin vurgulu olduğu Modeller sayfasının ekran görüntüsü.](../media/content-understanding/sensitivity-model-settings.png)

2. **Model ayarları** bölmesindeki **Uyumluluk** bölümünde Duyarlılık etiketi menüsünü seçerek modele uygulayabilecek duyarlılık etiketlerinin listesini görüntüleyin.

   ![Duyarlılık etiketi menüsünü gösteren Model ayarları bölmesinin ekran görüntüsü.](../media/content-understanding/sensitivity-model-settings-pane.png) 

3. Modele uygulamak istediğiniz duyarlılık etiketini seçin ve ardından Kaydet'i **seçin**.

Duyarlılık etiketini modelinize kaydettikten sonra, aşağıdakilere uygulayabilirsiniz:

- Yeni belge kitaplığı
- Modelin zaten uygulandığı belge kitaplığı
 
### <a name="apply-the-sensitivity-label-to-a-document-library-to-which-the-model-is-already-applied"></a>Duyarlılık etiketini modelin zaten uygulandığı belge kitaplığına uygulama

Belge anlama modeliniz bir belge kitaplığına zaten uygulanmışsa, duyarlılık etiket güncelleştirmenizi belge kitaplığına uygulamak için şunları yapabilirsiniz:

1. Model giriş sayfasında, Bu **modele** sahip kitaplıklar bölümünde, duyarlılık etiketi güncelleştirmesini uygulamak istediğiniz belge kitaplığını seçin.

2. **Eşitle'yi seçin**.

   ![Bu modelin vurgulu olduğu Kitaplıklar bölümünü gösteren ekran görüntüsü.](../media/content-understanding/sensitivity-libraries-sync.png)

Güncelleştirmeyi uyguladıktan ve modelinize eşitledikten sonra, aşağıdaki adımları gerçekleştirerek bunun uygulandığını onaylayın:

1. İçerik merkezinde, Bu **modelin uygulandığı kitaplıklar** bölümünde, güncelleştirilmiş modelinizin uygulandığı kitaplığı seçin. 

2. Belge kitaplığı görünümde, model özelliklerini kontrol etmek için bilgi simgesini seçin.

3. Etkin **modeller listesinde** güncelleştirilmiş modelinizi seçin.

4. Duyarlılık **etiketi bölümünde** , uygulanan duyarlılık etiketinin adını bulabilirsiniz.

Modelinizin belge kitaplığınıza gelen görünüm sayfasında yeni bir **Duyarlılık etiketi** sütunu görüntülenir. Modeliniz, içerik türüne ait olarak tanımları dosyaları sınıflandırarak kitaplık görünümünde listelese, Duyarlılık etiketi sütunu  model üzerinden duyarlılık etiketinin adını da gösterir.

Örneğin, modelinizin tanımları olan tüm mali belgelere bu belgelere  Şifreleme duyarlılık etiketi de uygulanarak, yetkisiz kişiler tarafından erişilmalarını önlenir. Yetkisiz bir kişi tarafından belge kitaplığından dosyaya erişim girişimi yapılırsa, duyarlılık etiketi uygulandığından buna izin verilme olmadığını söyleyen bir hata görüntülenir.

<!---
## Add a sensitivity label to a form processing model

> [!Important]
> For sensitivity labels to be available to apply to your form processing model, they need to be [created and published in the Microsoft 365 Compliance Center](../admin/security-and-compliance/set-up-compliance.md).

You can either apply a sensitivity label to a form processing model when you are creating a model, or apply it to an existing model.

### Add a sensitivity label when you create a form processing model

1. When you [create a new form processing model](create-a-form-processing-model.md), select **Advanced settings**.

2. In **Advanced settings**, in the **Sensitivity label** section, select the menu and then select the sensitivity label you want to apply to the model.

3.  After you've completed your remaining model settings, select **Create** to build your model.

### Add a sensitivity label to an existing form processing model

You can add a sensitivity label to an existing form processing model in different ways:

- Through the **Automate** menu in the document library
- Through the **Active model** settings in the document library 

#### Add a sensitivity label to an existing form processing model through the Automate menu

You can add a sensitivity label to an existing form processing model that you own through the **Automate** menu in the document library in which the model is applied.

1. In your document library to which the form processing model is applied, select the **Automate** menu, select **AI Builder**, and then select **View form processing model details**.

2. On the **Model details** pane, in the **Sensitivity label** section, select the sensitivity label you want to apply. Then select **Save**.

#### Add a sensitivity label to an existing form processing model in the active model settings

You can add a sensitivity label to an existing form processing model that you own through the **Active model** settings in the document library in which the model is applied.

1. In the SharePoint document library in which the model is applied, select the **View active models** icon, and then select **View active models**.

2. In **Active models**, select the form processing model to which you want to apply the sensitivity label.

3. On the **Model details** pane, in the **Sensitivity label** section, select the sensitivity label you want to apply. Then select **Save**.

   > [!NOTE]
   > You must be the model owner for the **Model settings** pane to be editable. 
--->

## <a name="see-also"></a>Ayrıca bkz.

[Bekletme etiketi uygulama](apply-a-retention-label-to-a-model.md)

[Sınıflandırıcı oluşturma](create-a-classifier.md)

[Ayıklaıcı oluşturma](create-an-extractor.md)

[Belge Anlama'ya genel bakış](document-understanding-overview.md)
