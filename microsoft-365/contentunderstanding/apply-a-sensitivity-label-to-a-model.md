---
title: Microsoft SharePoint Syntex'da modele duyarlılık etiketi uygulama
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
description: SharePoint Syntex'da modele duyarlılık etiketi uygulamayı öğrenin.
ms.openlocfilehash: 4ab530fbd4a187f03617b01b6b9661332ad1a7d9
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/19/2022
ms.locfileid: "64945615"
---
# <a name="apply-a-sensitivity-label-to-a-model-in-microsoft-sharepoint-syntex"></a>Microsoft SharePoint Syntex'da modele duyarlılık etiketi uygulama

Microsoft SharePoint Syntex'da belge anlama modellerine kolayca [duyarlılık etiketi](../compliance/sensitivity-labels.md) uygulayabilirsiniz. Bu özellik henüz form işleme modellerinde kullanılamaz.

Duyarlılık etiketleri, modellerinizin tanımladığınız belgelere şifreleme uygulamanıza olanak tanır. Örneğin, modelinizin yalnızca belge kitaplığınıza yüklenen banka hesap numaralarını veya kredi kartı numaralarını içeren finansal belgeleri tanımlamasını değil, aynı zamanda bu içeriğe kimlerin erişebileceğini ve nasıl kullanılabileceğini kısıtlamak için şifreleme ayarlarıyla yapılandırılmış bir duyarlılık etiketi uygulamasını istiyorsunuz. SharePoint Syntex modelleri [etiket sırası](../compliance/apply-sensitivity-label-automatically.md#how-multiple-conditions-are-evaluated-when-they-apply-to-more-than-one-label) kurallarına uyar ve ayrıca kullanıcı tarafından dosyaya el ile uygulanmış olan mevcut bir etiketin üzerine yazılmaz. 

Modelinizin giriş sayfasındaki model ayarlarınızdan modelinize önceden var olan bir duyarlılık etiketi uygulayabilirsiniz. Etiket, model ayarlarından seçilebilmek için zaten yayımlanmış olmalıdır. Etiketler Word (.docx), PowerPoint (.pptx) ve Excel (.xlsx) için Office dosyalarına uygulanır. 

> [!Important]
> Duyarlılık etiketlerinin belge anlama modellerinize uygulanabilmek için, [bunların Microsoft Purview uyumluluk portalında oluşturulması ve yayımlanması](../admin/security-and-compliance/set-up-compliance.md) gerekir.

## <a name="add-a-sensitivity-label-to-a-document-understanding-model"></a>Belge anlama modeline duyarlılık etiketi ekleme

1. Model giriş sayfasında **Model ayarları'nı** seçin.

   ![Model ayarları seçeneğinin vurgulandığı Modeller sayfasının ekran görüntüsü.](../media/content-understanding/sensitivity-model-settings.png)

2. **Model ayarları** bölmesindeki **Uyumluluk** bölümünde **Duyarlılık etiketi** menüsünü seçerek modele uygulayabileceğiniz duyarlılık etiketlerinin listesini görebilirsiniz.

   ![Duyarlılık etiketi menüsünü gösteren Model ayarları bölmesinin ekran görüntüsü.](../media/content-understanding/sensitivity-model-settings-pane.png) 

3. Modele uygulamak istediğiniz duyarlılık etiketini seçin ve ardından **Kaydet'i** seçin.

Duyarlılık etiketini modelinize uyguladıktan sonra aşağıdakilere uygulayabilirsiniz:

- Yeni belge kitaplığı
- Modelin zaten uygulandığı belge kitaplığı
 
### <a name="apply-the-sensitivity-label-to-a-document-library-to-which-the-model-is-already-applied"></a>Duyarlılık etiketini modelin zaten uygulandığı belge kitaplığına uygulama

Belge anlama modeliniz bir belge kitaplığına zaten uygulanmışsa, duyarlılık etiketi güncelleştirmenizi belge kitaplığına uygulamak üzere eşitlemek için aşağıdakileri yapabilirsiniz:

1. Modelin giriş sayfasındaki **Bu modelle kitaplıklar** bölümünde duyarlılık etiketi güncelleştirmesini uygulamak istediğiniz belge kitaplığını seçin.

2. **Eşitle'yi** seçin.

   ![Eşitle seçeneğinin vurgulandığı bu model bölümüyle kitaplıkları gösteren ekran görüntüsü.](../media/content-understanding/sensitivity-libraries-sync.png)

Güncelleştirmeyi uyguladıktan ve modelinizle eşitledikten sonra, aşağıdaki adımları uygulayarak uygulandığını onaylayabilirsiniz:

1. İçerik merkezindeki **Bu modelle kitaplıklar** bölümünde, güncelleştirilmiş modelinizin uygulandığı kitaplığı seçin. 

2. Belge kitaplığı görünümünüzde, model özelliklerini denetlemek için bilgi simgesini seçin.

3. **Etkin modeller** listesinde güncelleştirilmiş modelinizi seçin.

4. **Duyarlılık etiketi** bölümünde, uygulanan duyarlılık etiketinin adını görürsünüz.

Belge kitaplığınızdaki modelinizin görünüm sayfasında yeni bir **Duyarlılık etiketi** sütunu görüntülenir. Modeliniz, içerik türüne ait olarak tanımladığı dosyaları sınıflandırır ve kitaplık görünümünde listelerken Duyarlılık **etiketi** sütunu, model aracılığıyla uygulanan duyarlılık etiketinin adını da görüntüler.

Örneğin, modelinizin tanımladığı tüm finansal belgelere de *Şifreleme* duyarlılığı etiketi uygulanır ve yetkisiz kişiler tarafından erişilmesini engeller. Yetkisiz bir kişi tarafından belge kitaplığından dosyaya erişmeye çalışılırsa, uygulanan duyarlılık etiketi nedeniyle dosyaya izin verilmediğini belirten bir hata görüntülenir.

<!---
## Add a sensitivity label to a form processing model

> [!Important]
> For sensitivity labels to be available to apply to your form processing model, they need to be [created and published in the Microsoft Purview compliance portal](../admin/security-and-compliance/set-up-compliance.md).

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

[Ayıklayıcı oluşturma](create-an-extractor.md)

[Document Understanding'e genel bakış](document-understanding-overview.md)
