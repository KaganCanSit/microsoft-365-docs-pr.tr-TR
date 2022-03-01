---
title: Microsoft SharePoint Syntex'da belge anlama modeli SharePoint Syntex
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
description: Microsoft SharePoint Syntex'te yayımlanmış bir modeli SharePoint kitaplığına nasıl uygulamanız SharePoint Syntex.
ms.openlocfilehash: 0edb87faacc3518179b8bd1a4d41d7e3834394c3
ms.sourcegitcommit: 9f0e84835121ce6228fdc69182c24be7ad1cb20e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/18/2022
ms.locfileid: "63015463"
---
# <a name="apply-a-document-understanding-model-in-microsoft-sharepoint-syntex"></a>Microsoft SharePoint Syntex'da belge anlama modeli SharePoint Syntex

</br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4CSoL]

</br>

Belge anlama modelinizi yayımlandıktan sonra, bir veya birden çok kiracı SharePoint belge kitaplıklarına Microsoft 365.

> [!NOTE]
> Modeli yalnızca erişiminiz olan belge kitaplıklarına uygulayabilirsiniz.


## <a name="apply-your-model-to-a-document-library"></a>Modelinizi belge kitaplığına uygulama

Modelinizi belge kitaplığına SharePoint için:

1. Model giriş sayfasında, Modeli kitaplıklara **uygula kutucuğunun Modeli** **uygula'ya tıklayın**. Ya da Modelin **uygulandığı yer bölümünde** **+Kitaplık ekle'yi seçin**.

    ![Kitaplık ekle seçeneğinin vurgulu olduğu Modelin uygulandığı yer bölümünün ekran görüntüsü.](../media/content-understanding/apply-to-library.png)

2. Ardından, modelin SharePoint istediğiniz belge kitaplığını içeren çalışma alanı sitesini seçin. Site listede göster yoksa, bulmak için arama kutusunu kullanın.

    ![Bir site seçin.](../media/content-understanding/site-search.png)

    > [!NOTE]
    > Modeli *uygulamakta olduğu belge* *kitaplığında* Liste Yönetme izinlerine veya Düzenleme haklarına sahip olmak gerekir.

3. Siteyi seçdikten sonra, modeli uygulamak istediğiniz belge kitaplığını seçin. Örnekte, Contoso Örnek Olay *İzleme sitesinden* *Belgeler belge kitaplığını* seçin.

    ![Bir belge kitaplığı seçin.](../media/content-understanding/select-doc-library.png)

4. Model bir içerik türüyle ilişkili olduğundan, bunu kitaplı kitaplara uygulayan içerik türü ekler ve varsayılan görünümü sütun olarak göstererek ayıklamış etiketleriyle güncelleştirer. Bununla birlikte, isteğe **bağlı** olarak geçerli kitaplık görünümünü korumayı veya model bilgileri ve dosya küçük resimleriyle yeni bir görünüm kullanmayı seçmek için Gelişmiş ayarlar'ı seçebilirsiniz. Geçerli kitaplık görünümünü korumayı seçerseniz, model bilgileri bulunan yeni görünümler kitaplığın görünüm menüsü altında yine kullanılabilir.

    ![Kitaplık görünümlerini gösteren Gelişmiş ayarların ekran görüntüsü.](../media/content-understanding/library-view.png)

    Daha fazla bilgi için, [bu makalenin devam devamsında Belge kitaplığında](#change-the-view-in-a-document-library) görünümü değiştirme makalesine bakın.

5. Modeli **kitaplı** kitaplıya uygulamak için Ekle'yi seçin.

6. Model giriş sayfasında, **Modelin** uygulandığı yer bölümünde, listelenen ilk sitenin SharePoint görebilirsiniz.

7. Belge kitaplığınıza gidin ve modelin belge kitaplığı görünümünde olduğundan emin olun. Modelleri **anlama belgesini otomatik** >  **görüntüleme'yi seçin**.

8. Modelleri **gözden geçir ve yenilerini uygula sayfasında** , **belge kitaplığına** uygulanan modelleri görmek için Uygulanmış sekmesini seçin.

    ![Uygulamalı sekmesinin seçili olduğunu ve uygulanan modelleri gösteren ekran görüntüsü.](../media/content-understanding/applied-models.png) 

9. **Modelin açıklaması**, modeli yayım yapan model ve modelin sınıfladığı dosyalara bekletme veya duyarlılık etiketleri uygulamaması gibi bir modelle ilgili bilgileri görmek için Model ayrıntılarını görüntüle'yi seçin.

Modeli belge kitaplığına uygulamaya başladıktan sonra, belgeleri siteye yüklemeye başlayabilir ve sonuçları bulabilirsiniz.

Model, modelin ilişkili içerik türüne sahip tüm dosya ve klasörleri tanımlar ve bunları sizin görünümde listeler. Modelde ayıkıcılar varsa, görünümde her dosya veya klasörden ayıklayırsınız verilerin sütunları görüntülenir.

> [!NOTE]
> Aynı kitaplı kitaplara iki veya daha fazla belge anlama modeli uygulanırsa, karşıya yüklenen dosya en yüksek ortalama güven puanına sahip model kullanılarak sınıflandırılır. Ayıklanan varlıklar yalnızca uygulanan modelden olur. <br><br>Aynı kitaplı kitaplara özel form işleme modeli ve belge anlama modeli uygulanmışsa, dosya, belge anlama modeli ve bu model için eğitimli ayıklama modellerini kullanarak sınıflandırılır. Form işleme modeliyle eşleşmeye devam eden boş sütunlar varsa, sütunlar bu ayıklanan değerler kullanılarak doldurulur.

## <a name="sync-changes-to-one-or-more-libraries"></a>Değişiklikleri bir veya daha fazla kitaplıkta eşitleme

Bir modeli birden çok belge kitaplığında yayımlar ve sonra bir ayıklayan ekleme veya kaldırma gibi modeli güncelleştirerek, güncelleştirmeyi modelin uygulanmış olduğu tüm kitaplıklara basmanız gerekir.

Uygulanan tüm kitaplıklarda yapılan değişiklikleri eşitlemek için:

1. Model giriş sayfasında, Modelin **uygulandığı yer bölümünde, Eşitle'yi** **seçin**.

    ![Modelin uygulandığı yer bölümünü ve Tüm eşitleme düğmesinin vurgulu olduğunu gösteren ekran görüntüsü.](../media/content-understanding/sync-all-button.png) 

Değişiklikleri tek veya yalnızca seçili kitaplıklara eşitlemek için:

1. Model giriş sayfasındaki **Modelin uygulandığı** yer bölümünde, değişiklikleri uygulamak istediğiniz kitaplığı veya kitaplıkları seçin.

2. **Eşitle'yi seçin**.

    ![Modelin uygulandığı yer bölümünü ve Eşitle düğmesinin vurgulu olduğunu gösteren ekran görüntüsü.](../media/content-understanding/sync-button.png) 

## <a name="apply-the-model-to-files-and-folder-content-already-in-the-document-library"></a>Modeli zaten belge kitaplığında yer alan dosyalara ve klasör içeriğine uygulama

Uygulanan model, uygulandıktan sonra belge kitaplığına yüklenen tüm dosyaları ve klasör içeriğini işleye devam ederken, modelin uygulanmadan önce belge kitaplığında zaten var olan dosya ve klasör içeriği üzerinde çalıştırmak için şunları da yapabilirsiniz:

1. Belge kitaplığında, modeliniz tarafından işlenmesini istediğiniz dosyaları ve klasörleri seçin.

2. Dosyalarınızı ve klasörlerinizi seçdikten sonra, **belge kitaplığı şeridinde** Sınıflandır ve ayıkla görünür. **Sınıflandır ve ayıkla'ya seçin**.

      ![Sınıflandır ve ayıkla seçeneğini gösteren ekran görüntüsü.](../media/content-understanding/extract-classify.png) 

3. Seçtiğiniz dosya ve klasörler işlenecek sıraya eklenir.

    > [!NOTE]
    > Sınıflandırmanın ne kadar süreyle olabileceğini belirten bir ileti alırsınız. Yalnızca dosyaları seçtiysanız, sınıflandırma işlemi 30 dakika kadar sürebilir. Bir veya daha fazla klasör seçtiysiniz, sınıflandırma işlemi 24 saat kadar sürebilir.

### <a name="classification-date-field"></a>Sınıflandırma Tarihi alanı

Belge kitaplığına SharePoint Syntex anlama modeli (veya form işleme modeli) uygulanmışsa, Sınıflandırma Tarihi alanı kitaplık şemasına dahil edilir. Varsayılan olarak, bu alan boştur. Bununla birlikte, belgeler bir modele göre işlendiğinde ve sınıflandırılmışsa, bu alan bir tamamlanma tarih-zaman damgasıyla güncelleştirilir. 

   ![Sınıflandırma Tarihi sütununu gösteren belge kitaplığının ekran görüntüsü.](../media/content-understanding/class-date-column.png) 

Sınıflandırma **Tarihi** alanı, bir dosyanın veya [](/connectors/sharepointonline/#when-a-file-is-classified-by-a-content-understanding-model) klasörün içeriğinin işlenmesi tamamlandığında ve Sınıflandırma Tarihi alanını güncelleştirildikten sonra Power Automate akışı çalıştırmak için İçerik anlama modeli tetikleyicisi tarafından sınıflandırılabilir.

   ![Flow tetiğe.](../media/content-understanding/trigger.png)

Bundan **sonra, dosya bir içerik anlama modeli** tetikleyicisi tarafından sınıflandırılmışsa, dosyadan veya klasörden ayıklanan bilgileri kullanarak akışı başlatmak için kullanılabilir.

Örneğin, bir modele Sınıflandırma Tarihi damgası verili **olduğunda,** **SharePoint Syntex** dosya akışını işledikten sonra, kullanıcılara yeni bir dosyanın SharePoint belge kitaplığında bir model tarafından işlendiğinden ve sınıflandırılmış olduğunu bildirmek için E-posta gönder'i kullanabilirsiniz.

Akışı çalıştırmak için:

1. Bir dosya seçin ve sonra **Tümleştir'i seçin** >  **Power Automate** >  **Akış seçin**.

2. Akış oluştur **panelinde, Bir** dosyayı **işledikten sonra e-SharePoint Syntex e-posta gönder'i seçin**.

    ![Akış paneli ve akış oluştur seçeneğinin vurgulu olduğunu gösteren ekran görüntüsü.](../media/content-understanding/integrate-create-flow.png) 

## <a name="change-the-view-in-a-document-library"></a>Belge kitaplığında görünümü değiştirme

Bilgileri belge kitaplığında nasıl gördüğünüzi görmenin birçok SharePoint vardır. Belge kitaplığında görünümü, kendi ihtiyaçlarınıza veya tercihlerinize uyacak şekilde değiştirebilirsiniz.

Kitaplık sayfasındaki görünümü değiştirmek için, seçenekleri görüntülemek üzere görünüm açılan menüsünü seçin ve sonra da kullanmak istediğiniz görünümü seçin.

   ![Görünüm seçeneklerini gösteren görünüm açılan menüsünün ekran görüntüsü.](../media/content-understanding/document-library-view-menu.png) 

Örneğin, listeden **Kutucuklar'ı** seçersiniz, sayfa gösterildiği gibi görüntülenir.

   ![Kutucuklar görünümünü gösteren belge kitaplığının ekran görüntüsü.](../media/content-understanding/document-library-tiles-view.png) 

**Kutucuklar** görünümü, kullanıcı tarafından oluşturulan en çok sekiz alan görüntüler. Sekizden az varsa, sistem tarafından oluşturulan en çok dört alan gösterilir: Duyarlılık (varsa), Bekletme (varsa), İçerik türü, Değiştirme tarihi, Değiştiren ve Sınıflandırma tarihi.

Geçerli görünümü düzenlemek için, görünüm açılan menüsünde Geçerli görünümü **düzenle'yi seçin**.

## <a name="see-also"></a>Ayrıca Bkz

[Sınıflandırıcı oluşturma](create-a-classifier.md)

[Ayıklaıcı oluşturma](create-an-extractor.md)

[Belge Anlama'ya genel bakış](document-understanding-overview.md)
