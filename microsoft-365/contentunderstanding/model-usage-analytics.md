---
title: Modellerinizin Microsoft SharePoint Syntex'de nasıl kullanıldığını analiz etme
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
description: Belge anlama ve form işleme modellerinizin performansı hakkında daha fazla bilgi bulmayı öğrenin.
ms.openlocfilehash: 830a56ab4dd0145f1385d628405ee4287de19595
ms.sourcegitcommit: 6a981ca15bac84adbbed67341c89235029aad476
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2022
ms.locfileid: "65754764"
---
# <a name="analyze-how-your-models-are-used-in-microsoft-sharepoint-syntex"></a>Modellerinizin Microsoft SharePoint Syntex'de nasıl kullanıldığını analiz etme

</br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4GnhX]  

</br>


SharePoint Syntex içerik merkeziniz, içerik merkezinden yayımlanan modellerinizin nasıl kullanıldığı hakkında daha fazla bilgi sağlamak için model kullanım analizi sağlar. İçerik merkezinin <b>son 30 gün içinde modellerinizin performansı</b> bölümünde aşağıdaki grafiklerde ve listelerde sağlanan 30 günlük kullanım analizi verilerinin birleştirilmesi yer alır:

- Modele göre sınıflandırma
- Kitaplığa göre sınıflandırma
- Model kullanımı 

 ![Model analizi.](../media/content-understanding/model-analytics.png) </br>

### <a name="roll-up-of-model-usage-data-in-the-default-content-center"></a>Model kullanım verilerini varsayılan içerik merkezinden alma

SharePoint Syntex'da, kurulum sırasında varsayılan içerik merkezi oluşturulur. Gerektiğinde daha fazla içerik merkezi de oluşturulabilir. Örneğin, departmanlar modellerini oluşturmak ve yönetmek için kendi içerik merkezlerini oluşturabilir. 

Model kullanım analiziyle ilgili olarak şunları unutmayın:

- Varsayılan içerik merkeziniz, diğer içerik merkezlerinde oluşturulanlar da dahil olmak üzere kuruluşunuzdaki tüm içerik merkezleri ve modeller için model kullanım analizini gösterir. Bu, içerik yöneticilerine ve diğer paydaşlara şirket genelindeki içerik merkezlerini ve modellerini yönetmeleri ve denetlemeleri için merkezi bir portal sağlar.  
- Diğer içerik merkezleri yalnızca kendilerinde oluşturulmuş modeller için model kullanım analizini gösterir. Bu, içerik yöneticilerine yalnızca ilgilendikleri modeller için kullanım verileriyle ilgili içgörüler sağlar.


## <a name="classification-by-model"></a>Modele göre sınıflandırma

   ![Toplam model yüzdesi.](../media/content-understanding/total-model-percentage.png) </br>

**Modele göre sınıflandırma** pasta grafiği, hangi modellerin en çok dosyayı sınıflandırmış olduğunu gösterir. Yayımlanan her modeli, içerik merkezindeki tüm yayımlanan modeller tarafından işlenen toplam dosyaların yüzdesi olarak gösterir.

Her model, model tarafından başarıyla analiz edilen karşıya yüklenen dosyaların yüzdesi olan **Tamlık Oranı'nı** da gösterir. Düşük bir tamlık oranı, model veya analiz edilen dosyalarla ilgili sorunlar olduğu anlamına gelebilir.

## <a name="classification-by-library"></a>Kitaplığa göre sınıflandırma

   ![İşlenen dosyalar.](../media/content-understanding/files-processed-over-time.png) </br>

Kitaplık çubuğuna **göre sınıflandırma** grafiği, kuruluşunuzdaki içerik anlamanın etkinliğini belirlemenize yardımcı olur.  Her model için zaman içinde işlenen dosya sayısını göstermekle kalmaz, grafikte bir sütun seçerek modelin uygulandığı belge kitaplıklarını da gösterir.


## <a name="model-usage"></a>Model kullanımı

Model Kullanımı listesi, içerik merkezi aracılığıyla oluşturulan modeller için kullanım analizini gösterir.  

> [!NOTE]
> Varsayılan içerik merkezindeyseniz ve kuruluşunuzda ek içerik merkezleri varsa, model kullanım listesi içerik merkezine göre gruplandırılır.

Model kullanım listesindeki her model kullanım verilerini gösterir:

- Sınıflandırılmış öğe sayısı: Model tarafından işlenen dosyaların sayısı.
- Ortalama güvenilirlik puanı: Dosyalara karşı çalıştırıldığında modelin ortalama doğruluk puanı.
- Hedef liste URL'si: Modelin uygulandığı SharePoint belge kitaplığı.



## <a name="see-also"></a>Ayrıca bkz.
[Sınıflandırıcı oluştur](create-a-classifier.md)

[Ayıklayıcı oluştur](create-an-extractor.md)

[Document Understanding'e genel bakış](document-understanding-overview.md)

[Form işleme modeli oluştur](create-a-form-processing-model.md)  
