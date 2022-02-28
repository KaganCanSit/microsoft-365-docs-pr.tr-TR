---
title: Microsoft SharePoint Syntex'ta belge anlama modeli kullanım SharePoint Syntex
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
description: Belge anlama modeli için kullanım analizini nasıl bulup kullanabileceğiniz hakkında bilgi edinin.
ms.openlocfilehash: 3dd77f760f70812045841ab56afbb13b02044d91
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62988127"
---
# <a name="document-understanding-model-usage-analytics-in-microsoft-sharepoint-syntex"></a>Microsoft SharePoint Syntex'ta belge anlama modeli kullanım SharePoint Syntex

</br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4GnhX]  

</br>


SharePoint Syntex merkeziniz, içerik merkezinden yayımlanmış modellerinizi nasıl kullandığı hakkında daha fazla bilgi sağlamak için model kullanım analizi sağlar. İçerik <b>merkezinin son 30</b> gün içinde modellerinin performansı, aşağıdaki grafik ve listelerde sağlanan 30 günlük kullanım analizi verilerini içerir:

- Modele göre sınıflandırma
- Kitaplı sınıflandırma
- Model kullanımı 

 ![Model analizi.](../media/content-understanding/model-analytics.png) </br>

### <a name="roll-up-of-model-usage-data-in-the-default-content-center"></a>Varsayılan içerik merkezinde model kullanım verilerini toplama

Varsayılan SharePoint Syntex, kurulum sırasında varsayılan içerik merkezi oluşturulur. Gerektiğinde başka içerik merkezleri de oluşturulabilir. Örneğin, departmanlar modellerini oluşturmak ve yönetmek için kendi içerik merkezleri oluşturabilir. 

Model kullanım analiziyle ilgili olarak, şunları unutmayın:

- Varsayılan içerik merkeziniz, ek içerik merkezlerinde oluşturulanlar da dahil olmak üzere, kuruluş dahil olmak üzere tüm içerik merkezleri ve modelleri için model kullanım çözümlemelerini gösterir. Bu, içerik yöneticilerine ve diğer proje katılımcılarına şirket genelinde içerik merkezlerini ve modellerini yönetmek ve denetlemek için merkezi bir portal sağlar.  
- Diğer içerik merkezleri yalnızca içinde oluşturulan modeller için model kullanım çözümlemelerini gösterir. Bu, içerik yöneticilerine yalnızca ilgili modellerin kullanım verileriyle ilgili içgörüler sağlar.


## <a name="classification-by-model"></a>Modele göre sınıflandırma

   ![Toplam model yüzdesi.](../media/content-understanding/total-model-percentage.png) </br>

Model **pastası modeline göre** sınıflandırma grafiği, en çok dosya sınıflandırılmış modelleri görüntüler. Yayımlanmış her modeli, içerik merkezinde tüm yayımlanan modeller tarafından işlenen toplam dosyaların yüzdesi olarak gösterir.

Ayrıca her model, **karşıya yüklenen dosyaların** model tarafından başarıyla analiz edilen yüzdesini Tamlık Oranı olarak gösterir. Düşük tamlık oranı, model veya analize alınan dosyalarla ilgili sorunlar olduğu anlamına gelir.

## <a name="classification-by-library"></a>Kitaplı sınıflandırma

   ![İşlenen dosyalar.](../media/content-understanding/files-processed-over-time.png) </br>

Kitaplık **çubuğuna göre sınıflandırma** çubuğu grafiği, kuruluş içinde içeriğin daha etkili anlaşılmasını belirlemenize yardımcı olur.  Size yalnızca her model için zaman içinde işlenen dosyaların sayısını değil, grafikte bir sütun seçerek de modelin uygulandığı belge kitaplıklarını gösterir.


## <a name="model-usage"></a>Model kullanımı

Model Kullanımı listesinde, içerik merkezi aracılığıyla oluşturulan modellerin kullanım çözümlemeleri görüntülenir.  

> [!NOTE]
> Varsayılan içerik merkezindeysiniz ve kuruluş içinde ek içerik merkezleriniz varsa, model kullanım listesi içerik merkezine göre gruplanacak.

Model kullanım listesinde yer alan her modelde kullanım verileri görüntülenir:

- Sınıflandırılmış öğe sayısı: Model tarafından işlenen dosya sayısı.
- Ortalama güven puanı: Dosyalar üzerinde çalıştırlarda modelin ortalama doğruluk puanı.
- Hedef liste URL'si: SharePoint uygulandığı belge kitaplığının adı.



## <a name="see-also"></a>Ayrıca Bkz
[Sınıflandırıcı oluşturma](create-a-classifier.md)

[Ayıklaıcı oluşturma](create-an-extractor.md)

[Belge Anlama'ya genel bakış](document-understanding-overview.md)

[Form işleme modeli oluşturma](create-a-form-processing-model.md)  
