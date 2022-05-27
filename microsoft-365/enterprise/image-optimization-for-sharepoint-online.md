---
title: SharePoint Çevrimiçi klasik yayımlama siteleri için görüntü iyileştirme
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 9/18/2019
audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Ent_O365
- SPO_Content
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- SPO160
- MET150
ms.assetid: c7edb02a-fdab-4f91-9a20-cba01dad28ef
description: SharePoint Online klasik yayımlama sitelerinizde görüntü performansını artırmak için işlemeleri ve sprite'leri kullanmayı öğrenin.
ms.openlocfilehash: 39d0e4c26339ecf70c922636f82dcef82dd4b13e
ms.sourcegitcommit: 6a981ca15bac84adbbed67341c89235029aad476
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2022
ms.locfileid: "65754432"
---
# <a name="image-optimization-for-sharepoint-online-classic-publishing-sites"></a>SharePoint Çevrimiçi klasik yayımlama siteleri için görüntü iyileştirme

Bir web sayfasının yükleme hızı, görüntüler, HTML, JavaScript ve CSS dahil olmak üzere sayfayı işlemek için gereken tüm bileşenlerin birleşik boyutuna bağlıdır. Resimler sitenizi daha çekici hale getirmek için harika bir yoldur, ancak boyutları performansı etkileyebilir. Resimlerinizi sıkıştırma ve yeniden boyutlandırma ile iyileştirerek ve sprite kullanarak büyük görüntülerin etkilerini kaydırabilirsiniz. SharePoint görüntü işlemelerini kullanarak tek bir büyük görüntüyü karşıya yükleyebilir ve görüntünün bölümlerini görüntüleyerek yeniden yüklenmek yerine yeniden kullanılmasını sağlayabilirsiniz.

>[!NOTE]
>Bu konu, modern portal siteleri için değil SharePoint Çevrimiçi klasik yayımlama siteleri için geçerlidir. SharePoint Çevrimiçi modern portal sitelerinde görüntü iyileştirme hakkında bilgi için bkz. [SharePoint Çevrimiçi modern portal sayfalarında görüntüleri iyileştirme](modern-image-optimization.md).
  
## <a name="using-sprites-to-speed-up-image-loading"></a>Görüntü yüklemeyi hızlandırmak için sprite kullanma

![Spcommon'un ekran görüntüsü.](../media/cc5cdee1-8e54-4537-9a8a-8854f4ee849f.png)

Görüntü sprite çok daha küçük görüntüler içerir. CSS kullanarak, sayfanın belirli bir bölümünde mutlak konumlandırmayla görüntülenecek bileşik görüntünün bir bölümünü seçersiniz. Temel olarak, birden çok görüntü yüklemek yerine tek bir görüntüyü sayfanın çevresine taşırsınız ve bu görüntünün küçük bir kısmını sprite görüntüsünün gerekli bölümünün son kullanıcıya gösterildiği küçük bir pencerede görünür hale getirirsiniz. SharePoint Online, sprite spcommon.png dosyasında çeşitli simgelerini görüntülemek için sprite kullanır.

Burada ele alınanlar:
- Görüntü sıkıştırma
- Görüntü iyileştirme
- görüntü işlemelerini SharePoint
   
Bu, performansı artırabilir çünkü birkaç resim yerine yalnızca bir görüntü indirirsiniz ve ardından bu görüntüyü önbelleğe alır ve yeniden kullanabilirsiniz. Görüntü önbelleğe alınmasa bile, birden çok görüntü yerine tek bir görüntüye sahip olmak, bu yöntem sunucuya yapılan toplam HTTP isteği sayısını azaltır ve bu da sayfa yükleme sürelerini azaltır. Bu gerçekten bir görüntü paketleme biçimidir. Bu, yukarıda sağlanan SharePoint örnekte gösterildiği gibi resimler, örneğin simgeler gibi sık sık değişmiyorsa kullanışlı bir tekniktir. Bunu Microsoft Visual Studio kolayca başarmak için üçüncü taraf, açık kaynak, topluluk tabanlı bir proje olan [Web Essentials'ın](https://vswebessentials.com/) nasıl kullanılacağını görebilirsiniz. Daha fazla bilgi için bkz[. SharePoint Online'da küçültme ve paketleme](./minification-and-bundling-in-sharepoint-online.md).
  
## <a name="using-image-compression-and-optimization-to-speed-up-page-loading"></a>Sayfa yüklemeyi hızlandırmak için görüntü sıkıştırma ve iyileştirme kullanma

Görüntü sıkıştırma ve iyileştirme, sitenizde kullandığınız görüntülerin dosya boyutunu küçültmektir. Genellikle, görüntünün boyutunu küçültmek için en iyi teknik, görüntüyü sitede görüntülenecek en büyük boyuta yeniden boyutlandırmaktır. Görüntü görüntülenmeyecek kadar büyük bir görüntüye sahip olmanın bir anlamı yoktur. Resim düzenleyicisi kullanarak resimlerin doğru boyutlarda olduğundan emin olmak, sayfanızın boyutunu küçültmenin hızlı ve kolay bir yoludur.
  
Görüntüler doğru boyuta ulaştığında, bir sonraki adım bu görüntülerin sıkıştırmasını iyileştirmektir. Sıkıştırma ve iyileştirme için kullanılabilecek Fotoğraf Galerisi ve üçüncü taraf araçları da dahil olmak üzere çeşitli araçlar vardır. Sıkıştırmanın anahtarı, son kullanıcılar için ayırt edilebilir kaliteyi kaybetmeden dosya boyutunu mümkün olduğunca azaltmaktır. Sıkıştırılmış dosyalarınızın iyi görünmeye devam etmesini sağlamak için sıkıştırılmış dosyalarınızı yüksek tanımlı bir ekranda test ettiğinizden emin olun.
  
## <a name="speed-up-page-downloads-by-using-sharepoint-image-renditions"></a>SharePoint görüntü işlemelerini kullanarak sayfa indirmelerini hızlandırma

Görüntü işlemeleri, SharePoint Online'da önceden tanımlanmış görüntü boyutlarına göre farklı görüntü sürümleri sunmanızı sağlayan bir özelliktir. Bu özellikle kullanıcı tarafından oluşturulan görüntü içeriği olduğunda veya genişlik ve yükseklik gibi görüntü boyutları sitedeki CSS tarafından sabitlendiğinde önemlidir. Bir görüntü CSS tarafından düzeltildi olsa bile tam çözünürlüklü görüntü yüklenmeye devam eder. Bu durumda, görüntü işlemeleri kullanılarak dosya boyutu azaltılabilir.
  
> [!NOTE]
> İşlemeler yalnızca yayımlama etkinleştirildiğinde SharePoint için kullanılabilir. Ayarlar Site Ayarlar \> \> Site özelliklerini \> yönetme SharePoint Sunucu Yayımlama altında yayımlamayı etkinleştirebilirsiniz. Aksi takdirde seçenek gösterilmez.
  
Görüntü işleme boyutlandırması, tanımladığınız en küçük boyutu (genişlik veya yükseklik) alarak ve ardından diğer boyutun kilitli en boy oranına göre otomatik olarak yeniden boyutlandırılarak çalışır. Varsayılan olarak, görüntüyü merkezden kalan boyutlara göre kırpacaktır. Örneğin, 100 piksel genişliğinde ve 50 piksel yüksekliğinde bir işleme tanımlarsanız ve özgün görüntünüz 1000 piksel genişliğinde ve 800px yüksekliğindeyse, 800px boyutu artık 50px olacak ve 1000 piksel boyutu (şimdi 62,5px) görüntünün ortasından kırpılacak şekilde yeniden boyutlandırılır.
  
Adımlar oldukça basittir ancak görüntülerin işlemeleri kullanması için görüntüleri eklemeden önce işlemelerin SharePoint sitede olması gerekir. Ayrıca, SharePoint Sunucu Yayımlama Altyapısı (Site Koleksiyonu Düzeyi) ve SharePoint Sunucu Yayımlama (Site Düzeyi) özelliklerinin de açık olması gerekir.
  
### <a name="add-an-image-rendition-to-speed-up-page-loading"></a>Sayfa yüklemeyi hızlandırmak için görüntü işlemesi ekleme
  
1. Bu yordamı gerçekleştiren kullanıcı hesabının, site koleksiyonunun en üst düzey sitesinde en azından Tasarım izinlerine sahip olduğunu ve sitenin bir web sayfasında yayımlandığını doğrulayın.

2. Web tarayıcısında yayımlama sitesi koleksiyonunun en üst düzey sitesine gidin.

3. **Ayarlar** simgesini seçin.

4. **Site Ayarlar** sayfasındaki **Görünüm ve His** bölümünde yerleşik görüntü işlemelerini görürsünüz.

    Yeni bir tane oluşturmak için kullanıma yönelik işlemeleri kullanabilir veya **Görüntü İşlemeleri'ni** seçebilirsiniz.

    ![Görüntü İşleme'nin ekran görüntüsü.](../media/eaae0d53-657d-47ef-b687-65c5167eae4d.PNG)
  
5. **Görüntü İşlemeleri** sayfasında **Yeni öğe ekle'yi** seçin.

    ![Yeni Öğe Ekle'nin ekran görüntüsü.](../media/8cede22e-52bf-4d9d-99cb-162f2f6ce92b.PNG)
  
6. **Yeni Görüntü İşleme** sayfasındaki **Ad** kutusuna işleme için bir ad girin.

7. **Genişlik** ve **Yükseklik** metin kutularına, işlemenin genişliğini ve yüksekliğini piksel cinsinden girin ve **kaydet'i** seçin.

    ![Görüntü İşleme Adı'nın ekran görüntüsü.](../media/5a6119ed-c163-40df-a4db-ec629d15607d.PNG)
  
## <a name="custom-cropping-with-image-renditions"></a>Görüntü işlemeleri ile özel kırpma

Varsayılan olarak, görüntünün ortasından bir görüntü işlemesi oluşturulur. Resmin kullanmak istediğiniz bölümünü kırparak tek tek görüntüler için görüntü işlemesini ayarlayabilirsiniz. Görüntüleri işleme göre ayrı ayrı kırpabilirsiniz. Görüntüleri kırpmak, her işleme için görüntünün bir sürümünü oluşturmak üzere SharePoint blob önbelleğini kullanarak sayfa yüklemeyi hızlandırır. Bu şekilde, görüntü yalnızca bir kez yeniden boyutlandırıldığı ve son kullanıcılara birden çok kez hizmet etmeye hazır olduğu için sunucu yükü azaltılır. Görüntü işlemesini kırpma hakkında daha fazla bilgi için bkz [. Görüntü işlemesini kırpma](/sharepoint/dev/general-development/sharepoint-design-manager-device-channels).
