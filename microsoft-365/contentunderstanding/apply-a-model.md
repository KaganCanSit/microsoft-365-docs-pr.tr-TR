---
title: Microsoft SharePoint Syntex'da belge anlama modeli uygulama
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
description: Microsoft SharePoint Syntex'da yayımlanmış bir modelin SharePoint belge kitaplığına nasıl uygulanacağını öğrenin.
ms.openlocfilehash: 6be3a1b0badaecf1196545c313adcce51f3d2b55
ms.sourcegitcommit: 46e796c6b76a01516c48977335bbf5076ca74a06
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2022
ms.locfileid: "64738468"
---
# <a name="apply-a-document-understanding-model-in-microsoft-sharepoint-syntex"></a>Microsoft SharePoint Syntex'da belge anlama modeli uygulama

</br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4CSoL]

</br>

Belge anlama modelinizi yayımladıktan sonra, Microsoft 365 kiracınızdaki bir veya daha fazla SharePoint belge kitaplığına uygulayabilirsiniz.

> [!NOTE]
> Modeli yalnızca erişiminiz olan belge kitaplıklarına uygulayabilirsiniz.


## <a name="apply-your-model-to-a-document-library"></a>Modelinizi belge kitaplığına uygulama

Modelinizi bir SharePoint belge kitaplığına uygulamak için:

1. Model giriş sayfasındaki **Modeli kitaplıklara uygula** kutucuğunda **Modeli uygula'yı** seçin. Ya da **Modelin uygulandığı yer** bölümünde **+Kitaplık ekle'yi** seçin.

    ![Kitaplık ekle seçeneğinin vurgulandığı Modelin uygulandığı yer bölümünün ekran görüntüsü.](../media/content-understanding/apply-to-library.png)

2. Ardından modeli uygulamak istediğiniz belge kitaplığını içeren SharePoint sitesini seçebilirsiniz. Site listede gösterilmiyorsa, bulmak için arama kutusunu kullanın.

    ![Bir site seçin.](../media/content-understanding/site-search.png)

    > [!NOTE]
    > Modeli uyguladığınız belge kitaplığında *Listeyi Yönet* izinlerine veya *Düzenleme* haklarına sahip olmanız gerekir.

3. Siteyi seçtikten sonra, modeli uygulamak istediğiniz belge kitaplığını seçin. Örnekte Contoso *Servis Talebi İzleme* sitesinden *Belgeler* belge kitaplığını seçin.

    ![Bir belge kitaplığı seçin.](../media/content-understanding/select-doc-library.png)

4. Model bir içerik türüyle ilişkilendirildiğinden, kitaplığa uyguladığınızda içerik türünü ekler ve ayıkladığınız etiketler sütun olarak gösterilen varsayılan görünümü güncelleştirir. Ancak, isteğe bağlı olarak geçerli kitaplık görünümünü korumayı veya model bilgileri ve dosya küçük resimleriyle yeni bir görünüm kullanmayı seçmek için **Gelişmiş ayarlar'ı** seçebilirsiniz. Geçerli kitaplık görünümünü korumayı seçerseniz, model bilgilerine sahip yeni görünümler kitaplığın görünüm menüsünde yine kullanılabilir.

    ![Kitaplık görünümlerini gösteren Gelişmiş ayarların ekran görüntüsü.](../media/content-understanding/library-view.png)

    Daha fazla bilgi için bu [makalenin devamında belge kitaplığındaki görünümü değiştirme](#change-the-view-in-a-document-library) bölümüne bakın.

5. Modeli kitaplığa uygulamak için **Ekle'yi** seçin.

6. Modelin giriş sayfasındaki **Modelin uygulandığı yer** bölümünde, listelenen SharePoint sitesinin adını görmeniz gerekir.

7. Belge kitaplığınıza gidin ve modelin belge kitaplığı görünümünde olduğunuzdan emin olun. **AutomateView** **document understanding models (Belgeleri** >  anlama modellerini görüntüle) öğesini seçin.

8. **Modelleri gözden geçir ve yenilerini uygula** sayfasında, belge kitaplığına uygulanan modelleri görmek için **Uygulanan** sekmesini seçin.

    ![Uygulanan sekmesinin seçili olduğunu ve uygulanan modelleri gösteren ekran görüntüsü.](../media/content-understanding/applied-models.png) 

9. Modelin açıklaması, modeli yayımlayan kişi ve modelin sınıflandırdığı dosyalara bekletme veya duyarlılık etiketleri uygulayıp uygulamadığı gibi model hakkındaki bilgileri görmek için Model **ayrıntılarını görüntüle'yi** seçin.

Modeli belge kitaplığına uyguladıktan sonra, belgeleri siteye yüklemeye başlayabilir ve sonuçları görebilirsiniz.

Model, modelin ilişkili içerik türüne sahip tüm dosya ve klasörleri tanımlar ve bunları görünümünüzde listeler. Modelinizde ayıklayıcı varsa, görünümde her dosya veya klasörden ayıkladığınız verilerin sütunları görüntülenir.

> [!NOTE]
> Aynı kitaplığa iki veya daha fazla belge anlama modeli uygulanırsa, karşıya yüklenen dosya en yüksek ortalama güvenilirlik puanına sahip model kullanılarak sınıflandırılır. Ayıklanan varlıklar yalnızca uygulanan modelden olacaktır. <br><br>Aynı kitaplığa özel form işleme modeli ve belge anlama modeli uygulanırsa, dosya belge anlama modeli ve bu model için eğitilen ayıklayıcılar kullanılarak sınıflandırılır. Form işleme modeliyle eşleşen boş sütunlar varsa, bu ayıklanan değerler kullanılarak sütunlar doldurulur.

## <a name="sync-changes-to-one-or-more-libraries"></a>Değişiklikleri bir veya daha fazla kitaplıkla eşitleme

Bir modeli birden çok belge kitaplığına yayımladığınızda ve ardından bir ayıklayıcı ekleme veya kaldırma gibi modeli güncelleştirdiğinizde, güncelleştirmeyi modelin uygulandığı tüm kitaplıklara göndermeniz gerekir.

Değişiklikleri tüm uygulanan kitaplıklara eşitlemek için:

1. Model giriş sayfasındaki **Modelin uygulandığı yer** bölümünde **Tümünü eşitle'yi** seçin.

    ![Modelin uygulandığı yer bölümünü ve Tümünü eşitle düğmesinin vurgulandığı ekran görüntüsü.](../media/content-understanding/sync-all-button.png) 

Değişiklikleri bir veya yalnızca seçili kitaplıklara eşitlemek için:

1. Model giriş sayfasındaki **Modelin uygulandığı yer** bölümünde, değişiklikleri uygulamak istediğiniz kitaplığı veya kitaplıkları seçin.

2. **Eşitle'yi** seçin.

    ![Modelin uygulandığı yer bölümünü ve Eşitle düğmesinin vurgulandığı ekran görüntüsü.](../media/content-understanding/sync-button.png) 

## <a name="apply-the-model-to-files-and-folder-content-already-in-the-document-library"></a>Modeli belge kitaplığında zaten bulunan dosyalara ve klasör içeriğine uygulama

Uygulanan bir model, uygulandıktan sonra belge kitaplığına yüklenen tüm dosyaları ve klasör içeriğini işlerken, modeli uygulamadan önce belge kitaplığında zaten var olan dosyalarda ve klasör içeriğinde çalıştırmak için aşağıdakileri de yapabilirsiniz:

1. Belge kitaplığınızda, modeliniz tarafından işlenmesini istediğiniz dosya ve klasörleri seçin.

2. Dosya ve klasörlerinizi seçtikten sonra, belge kitaplığı şeridinde **Sınıflandır ve ayıkla** görüntülenir. **Sınıflandır ve ayıkla'yı** seçin.

      ![Sınıflandır ve ayıkla seçeneğini gösteren ekran görüntüsü.](../media/content-understanding/extract-classify.png) 

3. Seçtiğiniz dosya ve klasörler işlenecek kuyruğa eklenir.

    > [!NOTE]
    > Sınıflandırmanın ne kadar sürebileceğini belirten bir ileti alırsınız. Yalnızca dosyaları seçtiyseniz sınıflandırma 30 dakika kadar sürebilir. Bir veya daha fazla klasör seçtiyseniz sınıflandırma 24 saat kadar sürebilir.

### <a name="classification-date-field"></a>Sınıflandırma Tarihi alanı

Belge kitaplığına SharePoint Syntex belge anlama modeli (veya form işleme modeli) uygulandığında, **Sınıflandırma Tarihi** alanı kitaplık şemasına eklenir. Varsayılan olarak, bu alan boş olur. Ancak, belgeler bir model tarafından işlendiğinde ve sınıflandırıldığında, bu alan tamamlanma tarih-saat damgasıyla güncelleştirilir. 

   ![Sınıflandırma Tarihi sütununu gösteren belge kitaplığının ekran görüntüsü.](../media/content-understanding/class-date-column.png) 

**Sınıflandırma Tarihi** alanı, bir model bir dosya veya klasörün içeriğini işlemeyi bitirdikten ve **Sınıflandırma Tarihi** alanını güncelleştirdikten sonra bir Power Automate akışı çalıştırmak için bir dosya [**içerik anlama modeli tetikleyicisi tarafından sınıflandırıldığında**](/connectors/sharepointonline/#when-a-file-is-classified-by-a-content-understanding-model) tarafından kullanılır.

   ![Flow tetikleyici.](../media/content-understanding/trigger.png)

Bir **dosya bir içerik anlama modeli tarafından sınıflandırıldığında** tetikleyicisi, dosya veya klasörden ayıklanan bilgileri kullanarak akış başlatmak için kullanılabilir.

Örneğin, bir model **Sınıflandırma Tarihi** ile damgalandığında, kullanıcılara SharePoint belge kitaplığındaki bir model tarafından yeni bir dosyanın işlendiğini ve sınıflandırıldığını bildirmek için SharePoint Syntex **dosya akışını işledikten sonra e-posta gönder'i** kullanabilirsiniz.

Akışı çalıştırmak için:

1. Bir dosya seçin ve ardından **Tümleştir** >  **Power Automate** >  **Akış oluştur'u** seçin.

2. **Akış oluştur** panelinde, **SharePoint Syntex bir dosyayı işledikten sonra e-posta gönder'i** seçin.

    ![Akış oluştur panelini ve akış seçeneğinin vurgulandığı ekran görüntüsü.](../media/content-understanding/integrate-create-flow.png) 

## <a name="change-the-view-in-a-document-library"></a>Belge kitaplığındaki görünümü değiştirme

[!INCLUDE [Change the view in a document library](../includes/change-library-view.md)]

## <a name="see-also"></a>Ayrıca Bkz

[Sınıflandırıcı oluşturma](create-a-classifier.md)

[Ayıklayıcı oluşturma](create-an-extractor.md)

[Document Understanding'e genel bakış](document-understanding-overview.md)
