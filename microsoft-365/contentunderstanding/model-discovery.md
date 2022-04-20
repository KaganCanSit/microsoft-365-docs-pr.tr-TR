---
title: Microsoft SharePoint Syntex'de modelleri yayımlama ve bulma
ms.author: chucked
author: chuckedmonson
manager: pamgreen
audience: admin
ms.reviewer: ssquires
ms.topic: article
ms.prod: microsoft-365-enterprise
search.appverid: ''
ms.collection:
- enabler-strategic
- m365initiative-syntex
ms.localizationpriority: medium
description: Eğitilen modelleri diğer kullanıcıların kullanımına sunmayı ve Microsoft SharePoint Syntex'da diğer eğitilmiş modelleri uygulamayı öğrenin.
ms.openlocfilehash: 758f6886af6606c57c50c5c4c88e35f7aeeaefe4
ms.sourcegitcommit: dc415d784226c77549ba246601f34324c4f94e73
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/19/2022
ms.locfileid: "64916281"
---
# <a name="publish-and-discover-models-in-microsoft-sharepoint-syntex"></a>Microsoft SharePoint Syntex'de modelleri yayımlama ve bulma

Eğitilen belge anlama modellerinizi doğrudan SharePoint belge kitaplığından başkalarının görüntülemesini ve kullanmasını sağlayabilirsiniz. 

Ayrıca, kuruluşunuzdaki diğer kişiler tarafından oluşturulan diğer içerik merkezlerinde de eğitilen modelleri bulabilir ve değerlendirebilirsiniz. Dosyalarınızı sınıflandırmak veya dosyalardan belirli bilgileri ayıklamak için en kullanışlı modeli seçin. 

> [!NOTE]
> Bu özellik, form işleme modelleri için henüz kullanılamıyor.

## <a name="make-your-model-discoverable-to-others"></a>Modelinizi başkaları için bulunabilir hale getirme

Eğitilen modelinizi başkalarının kullanımına açmak için:

1. Modelinizin **Modeller** sayfasında **Model ayarları'nı** seçin.

2. **Model ayarları** panelinde, **Bu modelin kullanılabildiği siteler** bölümünde **Düzenle'yi** seçin.

3. Bu noktada, **Bu modelin kullanılabilir olduğu siteleri seçin** paneli, yönetici olup olmamanıza bağlı olarak farklı olacaktır. 

    SharePoint yöneticisiyseniz bu görünümü görürsünüz.

    ![Bu modelin kullanılabilir olduğu siteleri seçin panelinin ekran görüntüsü, modelin diğer kullanıcılar için kullanılabilir olmasını istediğiniz yerin seçeneklerini gösterir.](../media/content-understanding/select-sites.png)

    - **Hiçbir sitede kullanılamaz** – Model başkalarının kullanımına sunulmaz.
    - **Tüm siteler** – Model, başkalarının kullanması için içerik türü galerisinde kullanılabilir.
    - **Yalnızca seçili siteler** – Modelin hangi sitede veya hangi sitelerde kullanılabilir olacağını seçebilirsiniz. Arama yapmak ve modelin uygulanmasını istediğiniz siteleri seçmek için metin kutusuna tıklayın. Yalnızca erişiminiz olan siteleri görürsünüz.

    SharePoint yöneticisi *değilseniz* bu görünümü görürsünüz.

    ![Yalnızca birkaç kullanılabilir siteye sahip son kullanıcılara yönelik seçenekleri gösteren Bu modelin kullanılabilir olduğu siteleri seçin panelinin ekran görüntüsü.](../media/content-understanding/select-site-user.png)

    Yalnızca zaten erişiminiz olan belirli sitelere kullanılabilirlik ekleyebilir veya kaldırabilirsiniz.

4. Modelin diğer kullanıcıların uygulaması için kullanılabilir olmasını istediğiniz siteleri seçin ve ardından **Kaydet'i** seçin.

## <a name="discover-other-trained-models"></a>Diğer eğitilmiş modelleri keşfedin

İçeriğinize uygun olabilecek eğitilmiş modelleri bulmak için:

1. Modelinizin belge kitaplığında **AutomateView** >  **document understanding modellerini** seçin.

2. **Modelleri gözden geçir ve yenilerini uygula** sayfasında, uygulanan modelleri ve belge kitaplığınıza uygulanabilecek modelleri gözden geçirebilirsiniz.

    ![Uygulanan ve Kullanılabilir sekmelerini gösteren Modelleri gözden geçir ve yenilerini uygula sayfasının ekran görüntüsü.](../media/content-understanding/review-models-apply-new-ones.png)

   - **Uygulanan** sekmesinde kitaplığınıza uygulanmış olan modellere bakın. Modelle ilgili açıklama, ayıklayıcılar ve diğer ayarlar gibi bilgileri görmek için Model **ayrıntılarını görüntüle'yi** seçin.
   
   - **Kullanılabilir** sekmesinde kitaplığınıza uygulanabilecek eğitilmiş modellere bakın.


### <a name="apply-a-trained-model-to-your-library"></a>Kitaplığınıza eğitilmiş model uygulama

En uygun modelleri bulmanıza yardımcı olmak için eğitilen modelleri içeriğinize göre değerlendirebilirsiniz. Kitaplığınıza uygulamak istediğiniz modeli seçmek için:

1. **Modelleri gözden geçir ve yenilerini uygula** sayfasında **Kullanılabilir** sekmesini seçerek listedeki modelleri gözden geçirin.

    ![Kullanılabilir sekmesinde modelleri gösteren Modelleri gözden geçir ve yenilerini uygula sayfasının ekran görüntüsü.](../media/content-understanding/available-models-to-apply.png)

2. Size en iyi sonuçları sunacağını düşündüğünüz modeli seçin, **Model ayrıntılarını görüntüle'yi** ve ardından **Kitaplığa uygula'yı** seçin.

### <a name="get-a-recommendation-for-a-trained-model"></a>Eğitilmiş model için öneri alma

Dosyalarınıza en uygun modelin hangisi olduğundan emin değilseniz bir öneri isteyebilirsiniz. Öneriniz en fazla 10 model içerebilir.

1. **Modelleri gözden geçir ve yenilerini uygula** sayfasında **Kullanılabilir** sekmesini seçin.

2. İlk kutucukta **Öneri al'ı** seçin.

    ![Kullanılabilir sekmesindeki Öneri al seçeneğini gösteren Modelleri gözden geçir ve yenilerini uygula sayfasının ekran görüntüsü.](../media/content-understanding/get-recommendation.png)

3. **Analiz için bir veya daha fazla model seçin** sayfasında, en uygun olabileceğini düşündüğünüz modelleri seçin ve ardından **İleri'yi** seçin.

    ![İki modelin seçili olduğu önerilen modelleri gösteren Bir veya daha fazla model seçin sayfasının ekran görüntüsü.](../media/content-understanding/recommendation-results.png)

4. **Analiz edilecek bir dosya seçin** sayfasında, kitaplığınızda depolanacak aynı veya benzer türde bir dosya seçin. Ardından **Seç'i** seçin.

    ![Tek bir dosyanın seçili olduğu kullanılabilir dosyaları gösteren Analiz etmek için bir dosya seçin sayfasının ekran görüntüsü.](../media/content-understanding/file-to-analyze.png)

5. **Sonuçları gözden geçirin ve bir model seçin** sayfasında, **Önerimiz** altında önerilen dosyayı görürsünüz. Önerilen modeli uygulamanız gerekmez. Daha uygun olduğunu düşünüyorsanız başka bir model uygulamayı seçebilirsiniz.

    ![Sonuçları gözden geçir ve önerilen modelleri gösteren bir model seç sayfasının ekran görüntüsü.](../media/content-understanding/review-results.png)

6. Size en iyi sonuçları sunacağını düşündüğünüz model için **Model ayrıntılarını görüntüle'yi** ve ardından **Kitaplığa uygula'yı** seçin.

7. Seçili dosyayı temel alan önerilen model yoksa, geri dönüp başka bir dosya seçebilir veya farklı modeller seçebilirsiniz.

### <a name="remove-an-applied-model"></a>Uygulanan modeli kaldırma

Uygulanan modeli belge kitaplığınızdan kaldırmak için:

1. **Modelleri gözden geçir ve yenilerini uygula** sayfasında **, Uygulanan** sekmesinde kitaplığınıza uygulanmış olan modellere bakın.

2. Kaldırmak istediğiniz modelde **Model ayrıntılarını görüntüle'yi** ve ardından **Kitaplıktan kaldır'ı** seçin.


## <a name="see-also"></a>Ayrıca bkz.

[Belge anlama modeli uygulama](apply-a-model.md)

[Belge anlamaya genel bakış](document-understanding-overview.md)
