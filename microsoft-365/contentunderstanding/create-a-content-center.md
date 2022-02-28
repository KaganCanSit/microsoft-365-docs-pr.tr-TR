---
title: Microsoft SharePoint Syntex'da içerik merkezi oluşturma
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
description: Microsoft SharePoint Syntex'da içerik merkezi oluşturma hakkında bilgi SharePoint Syntex.
ms.openlocfilehash: e44ed9433562bdfe8da471bd08c4711bc405b92d
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62988592"
---
# <a name="create-a-content-center-in-microsoft-sharepoint-syntex"></a>Microsoft SharePoint Syntex'da içerik merkezi oluşturma


</br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4CPSF]

</br>

Belge anlama modellerini oluşturmak ve yönetmek için, önce bir içerik merkezine ihtiyacınız vardır. İçerik merkezi, model oluşturma arabirimidir ve ayrıca yayımlanmış modellerin hangi belge kitaplıklarına uygulandığı hakkında bilgi içerir.

   ![Bir belge kitaplığı seçin.](../media/content-understanding/content-center-page.png)

Kurulum sırasında varsayılan bir içerik merkezi [oluşturabilirsiniz](set-up-content-understanding.md). Ancak bir SharePoint yöneticisi gerektiğinde ek merkezler de oluşturabilir. Tek bir içerik merkezi tüm model etkinliğinin biriktirimini istediğiniz ortamlar için uygun olabilir, ancak modelleriyle ilgili farklı ihtiyaçları ve izin gereksinimleri olan, kurum içindeki birden çok bölüm için ek merkezleriniz olabilir.

Buna ek olarak, bu içeriği SharePoint Syntex lisans satın almadan bu makaledeki yönergeleri kullanarak bir içerik merkezi oluşturabilirsiniz. Lisanssız kullanıcılar belge anlama modelleri oluşturabilir, ancak bunları belge kitaplığına uygulayamaz.

> [!NOTE]
> Bir [Microsoft 365 Multi-Geo](../enterprise/microsoft-365-multi-geo.md) ortamında, merkezi konumunuz içinde tek bir varsayılan içerik merkeziniz varsa, modelin yalnızca o konumdan bir yuvarlanma etkinliği sebilirsiniz. Multi-Geo ortamında, şu anda grup sınırları genelinde model etkinliğinin bir rulosu alayamamaktadır. 

## <a name="create-a-content-center"></a>İçerik merkezi oluşturma

Bir SharePoint yöneticisi, yönetim merkezi site hazırlama paneli aracılığıyla herhangi bir SharePoint sitesi oluşturacaktır gibi bir içerik merkezi sitesi oluşturabilir.[](/sharepoint/create-site-collection)

Yeni içerik merkezi oluşturmak için:

1. Microsoft 365 yönetim merkezi Yönetim Merkezi Etkin [SharePoint **sayfasına** gidin](https://admin.microsoft.com/sharepoint?page=siteManagement&modern=true).

2. Etkin Siteler **sayfasında Oluştur'a** **tıklayın ve** Diğer seçenekler'i **seçin**.

3. Şablon **seçin menüsünde İçerik** **Merkezi'ne tıklayın**.

4. Yeni site için bir Site Adı, **Birincil** yönetici **ve** Dil **girin**.</br>

   > [!NOTE] 
   > Kullanılabilir dillerden herhangi birini işlemek için bir içerik merkezi sitesi seçin, ancak şu anda modellerin yalnızca İngilizce dosyalar için oluşturulana dikkat edin. Site oluşturulduktan sonra, diğer site şablonları gibi varsayılan site dilinin de düzenlenemez olduğunu unutmayın.

5. **Bitti'yi seçin**.
 
İçerik merkezi sitesi oluşturdukta, bu sitenin Yönetim **Merkezi'nin** Etkin siteler SharePoint görünür. 

### <a name="give-access-to-additional-users"></a>Ek kullanıcılara erişim verme
 
Siteyi oluşturdukktan sonra, ek kullanıcılara standart site izinleri modeli üzerinden [SharePoint veebilirsiniz](/sharepoint/modern-experience-sharing-permissions).

### <a name="roll-up-of-models-in-the-default-content-center"></a>Varsayılan içerik merkezinde modellerin yuvarlanma

İçerik SharePoint Syntex, kurulum sırasında oluşturulan ilk içerik merkezi varsayılan *içerik merkezidir*. Sonraki içerik merkezleri oluşturulduktan sonra, modelleri varsayılan içerik merkezi görünümünde gösterilir.

![Varsayılan içerik merkezinde Model kitaplığının ekran görüntüsü.](../media/content-understanding/model-library-default-content-center.png)

Varsayılan **içerik** merkezi görünümündeki Modeller kitaplığı, oluşturulmuş modelleri ve form işleme modellerini anlamayla ilgili tüm belgenin özet görünümü için içerik merkezine göre oluşturulmuş modelleri gruplar.

> [!NOTE]
> Belirlenen varsayılan içerik merkezini değiştiremezsiniz. Her zaman, kurulum sırasında oluşturulan ilk içerik merkezidir. 

## <a name="see-also"></a>Ayrıca Bkz
[Sınıflandırıcı oluşturma](create-a-classifier.md)

[Ayıklaıcı oluşturma](create-an-extractor.md)

[İçerik merkezi oluşturma](create-a-content-center.md)

[Belgeyi anlamaya genel bakış](document-understanding-overview.md)

[Form işleme modeli oluşturma](create-a-form-processing-model.md)

[Model uygulama](apply-a-model.md)