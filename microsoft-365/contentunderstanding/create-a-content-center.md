---
title: Microsoft SharePoint Syntex'de içerik merkezi oluşturma
ms.author: chucked
author: chuckedmonson
manager: pamgreen
ms.reviewer: ssquires
audience: admin
ms.topic: article
ms.prod: microsoft-365-enterprise
search.appverid: ''
ms.custom: admindeeplinkSPO
ms.collection:
- enabler-strategic
- m365initiative-syntex
ms.localizationpriority: medium
description: Microsoft SharePoint Syntex'da içerik merkezi oluşturmayı öğrenin.
ms.openlocfilehash: c630bba8bafad8bcbf9749e7a4d08ae1e86f4d68
ms.sourcegitcommit: 23e186b46b27a6a4863f507a52a11105afae9726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/15/2022
ms.locfileid: "64882230"
---
# <a name="create-a-content-center-in-microsoft-sharepoint-syntex"></a>Microsoft SharePoint Syntex'de içerik merkezi oluşturma


</br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4CPSF]

</br>

Belge anlama modelleri oluşturmak ve yönetmek için önce bir içerik merkezi gerekir. İçerik merkezi model oluşturma arabirimidir ve ayrıca hangi belge kitaplıklarına yayımlanan modellerin uygulandığı hakkında bilgi içerir.

   ![Bir belge kitaplığı seçin.](../media/content-understanding/content-center-page.png)

[Kurulum](set-up-content-understanding.md) sırasında varsayılan bir içerik merkezi oluşturursunuz. Ancak SharePoint yöneticisi gerektiğinde ek merkezler oluşturmayı da seçebilir. Tüm model etkinliklerinin toplanmasını istediğiniz ortamlar için tek bir içerik merkezi uygun olsa da, kuruluşunuzdaki birden çok departman için, modelleri için farklı gereksinimlere ve izin gereksinimlerine sahip olabilecek ek merkezleriniz olmasını isteyebilirsiniz.

Ayrıca, SharePoint Syntex denemek istiyorsanız, lisans satın almadan bu makaledeki yönergeleri kullanarak bir içerik merkezi oluşturabilirsiniz. Lisanssız kullanıcılar belge anlama modelleri oluşturabilir ancak bunları belge kitaplığına uygulayamaz.

> [!NOTE]
> [Microsoft 365 Multi-Geo ortamında](../enterprise/microsoft-365-multi-geo.md), merkezi konumunuzda tek bir varsayılan içerik merkeziniz varsa, yalnızca bu konumdan model etkinliğinin bir toplu işlemini sağlayabilirsiniz. Şu anda Multi-Geo ortamında grup sınırları boyunca model etkinliğinin bir toplu işlemini alamazsınız. 

## <a name="create-a-content-center"></a>İçerik merkezi oluşturma

bir SharePoint yöneticisi, yönetim merkezi sitesi sağlama paneli aracılığıyla [başka bir SharePoint sitesi oluşturmak](/sharepoint/create-site-collection) gibi bir içerik merkezi sitesi oluşturabilir.

Yeni bir içerik merkezi oluşturmak için:

1. Microsoft 365 yönetim merkezi <a href="https://go.microsoft.com/fwlink/?linkid=2185220" target="_blank">**etkin siteler** > SharePoint yönetim merkezine</a> gidin.

2. **Etkin Siteler** sayfasında **Oluştur'a** tıklayın ve **ardından Diğer seçenekler'i** seçin.

3. **Şablon seçin** menüsünde **İçerik Merkezi'ni** seçin.

4. Yeni site için bir **Site Adı**, **Birincil yönetici** ve bir **Dil** sağlayın.</br>

   > [!NOTE] 
   > Kullanılabilir dillerden herhangi birinde işlenecek bir içerik merkezi sitesi seçebilirsiniz, ancak şu anda modellerin yalnızca İngilizce dosyalar için oluşturulabileceğini unutmayın. Ayrıca, diğer site şablonları gibi varsayılan site dilinin de site oluşturulduktan sonra düzenlenemez olduğunu unutmayın.

5. **Bitti'yi** seçin.
 
bir içerik merkezi sitesi oluşturduktan sonra, SharePoint yönetim merkezindeki <a href="https://go.microsoft.com/fwlink/?linkid=2185220" target="_blank">**Etkin sitelerde**</a> listelendiğini görürsünüz. 

### <a name="give-access-to-additional-users"></a>Ek kullanıcılara erişim verme
 
Siteyi oluşturduktan sonra, standart [SharePoint site izinleri modeli](/sharepoint/modern-experience-sharing-permissions) aracılığıyla ek kullanıcılara siteye erişim verebilirsiniz.

### <a name="roll-up-of-models-in-the-default-content-center"></a>Varsayılan içerik merkezinde modellerin toplu olarak alınması

SharePoint Syntex'da, kurulum sırasında oluşturulan ilk *içerik merkezi varsayılan içerik merkezidir*. Sonraki içerik merkezleri oluşturulursa, modelleri varsayılan içerik merkezi görünümünde gösterilir.

![Varsayılan içerik merkezindeki Model kitaplığının ekran görüntüsü.](../media/content-understanding/model-library-default-content-center.png)

Varsayılan içerik merkezi görünümündeki **Modeller** kitaplığı, oluşturulan modelleri içerik merkezine göre gruplandırarak oluşturulan tüm belge anlama modellerinin ve form işleme modellerinin özet görünümünü oluşturur.

> [!NOTE]
> Belirlenen varsayılan içerik merkezini değiştiremezsiniz. Her zaman kurulum sırasında oluşturulan ilk içerik merkezidir. 

## <a name="see-also"></a>Ayrıca bkz.

[Sınıflandırıcı oluşturma](create-a-classifier.md)

[Ayıklayıcı oluşturma](create-an-extractor.md)

[İçerik merkezi oluşturma](create-a-content-center.md)

[Belge anlamaya genel bakış](document-understanding-overview.md)

[Form işleme modeli oluşturma](create-a-form-processing-model.md)

[Model uygulama](apply-a-model.md)