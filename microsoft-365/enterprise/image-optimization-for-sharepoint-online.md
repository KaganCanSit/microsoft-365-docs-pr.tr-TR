---
title: SharePoint Online klasik yayımlama siteleri için görüntü iyileştirme
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: SharePoint Online klasik yayımlama sitelerde görüntü performansını iyileştirmek için yorum ve sprite'ları nasıl kullanabileceğinizi öğrenin.
ms.openlocfilehash: fe3c698dda06559bf6e104650b6b8bb8d81172fa
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62988733"
---
# <a name="image-optimization-for-sharepoint-online-classic-publishing-sites"></a>SharePoint Online klasik yayımlama siteleri için görüntü iyileştirme

Web sayfasının yükleme hızı resimler, HTML, JavaScript ve CSS dahil olmak üzere sayfanın işleniyor olması için gereken tüm bileşenlerin birleştirilmiş boyutuna bağlıdır. Resimler, sitenizi daha çekici hale etkili hale etmek için harika bir yol sağlar, ancak boyutları performansı etkileyebilir. Resimlerinizi sıkıştırma ve yeniden boyutlandırma ile en iyi duruma getirerek ve küçük resimleri kullanarak çok büyük resimlerin etkilerini kaydırabilirsiniz. Görüntü SharePoint kullanarak, tek bir büyük resim yükleyebilir ve yeniden yüklemek yerine yeniden kullanılmasına olanak sağlayan resmin görüntü bölümlerini karşıya yükleyebilirsiniz.

>[!NOTE]
>Bu konu modern portal SharePoint değil, Çevrimiçi klasik yayımlama siteleri için geçerlidir. Çevrimiçi modern portal sitelerinde resim iyileştirme SharePoint için bkz. [SharePoint Online modern portal sayfalarında resimleri iyileştirme](modern-image-optimization.md).
  
## <a name="using-sprites-to-speed-up-image-loading"></a>Görüntü yüklemesini hızlandırmak için hareket hareketlemeleri kullanma

![Spcommon'un ekran görüntüsü.](../media/cc5cdee1-8e54-4537-9a8a-8854f4ee849f.png)

Bir resim sprite daha birçok küçük resim içerir. CSS kullanarak, mutlak konumlandırmanın bulunduğu sayfanın belirli bir bölümünde görüntülemek için bileşik resmin bir bölümünü seçersiniz. Temel olarak, birden çok resmi yüklemeden tek bir görüntüyü sayfada hareket ettirin ve sprite resminin gerekli bölümü son kullanıcıya gösterildiği küçük bir pencerede resmin küçük bir kısmını görünür hale gelirsiniz. SharePoint Online, bu dosyada çeşitli simgelerini görüntülemek için sprite spcommon.png kullanır.

Burada ele neler var:
- Resim sıkıştırma
- Görüntü iyileştirme
- SharePoint görüntüditionları
   
Bu da performansı artırabilir, çünkü birkaç resim yerine yalnızca bir resim indirir ve sonra bu resmi önbelleğe alın ve yeniden kullanın. Birden çok resim yerine tek bir resim görüntüye sahip olarak resim önbelleğe alınmasa bile, bu yöntem sunucuya yapılan toplam HTTP istekleri sayısını azaltır ve bu da sayfa yükleme sürelerini azaltır. Bu aslında bir görüntündling biçimidir. Yukarıdaki örnekte gösterildiği gibi, simgeler gibi resimler çok sık değiş değişiyorsa, bu SharePoint bir tekniktir. Web [Essentials'ta](https://vswebessentials.com/) bu hedefe kolayca ulaşmak için üçüncü taraf, açık kaynaklı, topluluk tabanlı bir Microsoft Visual Studio. Daha fazla bilgi için bkz[. SharePoint Online'da büyütme ve büyütme](./minification-and-bundling-in-sharepoint-online.md).
  
## <a name="using-image-compression-and-optimization-to-speed-up-page-loading"></a>Sayfa yüklemesini hızlandırmak için resim sıkıştırma ve iyileştirmeyi kullanma

Resim sıkıştırma ve iyileştirme, siteniz üzerinde kullanılan resimlerin dosya boyutunu azaltmayı içerir. Bir resmin boyutunu azaltmanın en iyi tekniği, resmi, sitede görüntülenecek en büyük boyutta olacak şekilde yeniden boyutlandırmaktır. Görüntü asla görüntülenmayacak kadar büyük bir resim sahibi olmak, mantıklı bir anlam ifade etmiyor. Bir resim düzenleyicisi kullanarak resimlerin doğru boyutlarda olduğundan emin olmak, sayfa boyutunu azaltmanın hızlı ve kolay bir yoludur.
  
Resimler doğru boyutta olduktan sonra, bir sonraki adım bu resimlerin sıkıştırmasını iyileştirmektır. Sıkıştırma ve iyileştirme için, Fotoğraf Galerisi ve üçüncü taraf araçları dahil olmak üzere çeşitli araçlar vardır. Sıkıştırmayla ilgili en önemli nokta, dosya boyutunu, kalitede son kullanıcılar tarafından fark edilemez bir azalma olmadan mümkün olduğunca azaltmaktır. İyi görüntüye sahip olacaklarını garanti etmek için, sıkıştırılan dosyalarınızı yüksek tanımlı bir ekranda test etmek gerekir.
  
## <a name="speed-up-page-downloads-by-using-sharepoint-image-renditions"></a>Görüntüdition'leri kullanarak SharePoint indirmelerini hızlandırın

Görüntü yorumları, SharePoint Online'da önceden tanımlanmış resim boyutlarına göre resimlerin farklı sürümlerinin hizmet veren bir özelliğidir. Bu, özellikle sitede kullanıcı tarafından oluşturulan resim içerikleri veya CSS tarafından sabitlenmiş resim boyutları (genişlik ve yükseklik gibi) olduğunda önemlidir. Bir resim CSS tarafından sabitlenmiş olsa bile tam çözünürlüklü resim yüklenir. Bu durumda, görüntü yorumlarını kullanarak dosya boyutu azaltabilirsiniz.
  
> [!NOTE]
> Yorumlar yalnızca yayımlama etkinleştirildiğinde SharePoint tarafından kullanılabilir. Site Yayımlama'nın altında yayımlamayı etkinleştirebilirsiniz Ayarlar \> Site Ayarlar \> Sunucu Yayımlama'SharePoint \> yönetebilirsiniz. Aksi halde bu seçenek görünmez.
  
Görüntü yorumlarını yeniden boyutlandırmak, genişlik veya yükseklik olarak tanımladığınız en küçük boyutu alıp diğer boyutun kilitli en boy oranına göre otomatik olarak yeniden boyutlandırılmak üzere resmi yeniden boyutlandırarak çalışır. Varsayılan olarak, görüntüyü kalan boyutlara göre ortadan kırptır. Örneğin, 100px genişlik ve 50px genişliğinde bir yorum tanımlarsanız ve özgün resminiz 1000px genişliğinde ve 800px yüksekse, 800px boyutu şimdi 50px olacak şekilde yeniden boyutlandırılır ve 1000px boyutu (şimdi 62,5px olarak) resmin merkezinden kırpılır.
  
Adımlar oldukça basittir ancak görüntülerde, yorum kullanılamaysa da, görüntüleri eklemeden önce SharePoint bu sitede olması gerekir. Buna ek olarak, SharePoint Server Yayımlama Altyapısı (Site Koleksiyonu Düzeyi) ve SharePoint Server Yayımlama (Site Düzeyi) özelliklerini de açık bulundurabilirsiniz.
  
### <a name="add-an-image-rendition-to-speed-up-page-loading"></a>Sayfa yüklemesini hızlandırmak için görüntü yorum ekleyin
  
1. Bu yordamı gerçekleştiren kullanıcı hesabının, site koleksiyonunun en üst düzey sitesi üzerinde en azından Tasarım izinlerine sahip olduğunu ve sitenin bir web sayfasında yayımlanmaktadır.

2. Web tarayıcısında, yayımlama site koleksiyonunun en üst düzey sitesine gidin.

3. Yeni **Ayarlar** seçin.

4. **Site Ayarlar**, **Görünüm ve** Görünüm bölümünde, yerleşik görüntü yorumlarını görebilirsiniz.

    İlk gelen yorumlardan birini kullanabilir veya yeni bir **tane oluşturmak için Görüntü Yorumlarını** seçebilirsiniz.

    ![Görüntü Yorum'un ekran görüntüsü.](../media/eaae0d53-657d-47ef-b687-65c5167eae4d.PNG)
  
5. Görüntü **Yorumlarını sayfasında Yeni** öğe **ekle'yi seçin**.

    ![Yeni Öğe Ekle'nin ekran görüntüsü.](../media/8cede22e-52bf-4d9d-99cb-162f2f6ce92b.PNG)
  
6. Yeni **Görüntü Yorum sayfasında** , Ad **kutusuna** yorum için bir ad girin.

7. Genişlik **ve Yükseklik** **metin** kutularına, yorum için genişliği ve yüksekliği piksel cinsinden girin ve Kaydet'i **seçin**.

    ![Görüntü Yorum Adı'nın ekran görüntüsü.](../media/5a6119ed-c163-40df-a4db-ec629d15607d.PNG)
  
## <a name="custom-cropping-with-image-renditions"></a>Görüntüditions ile özel kırpma

Varsayılan olarak, görüntünün merkezinden bir görüntü yorumlu oluşturulur. Görüntünün kullanmak istediğiniz bölümünü göreerek, tek tek resimlerin görüntü yorumlarını ayarlayabilirsiniz. Resimleri her yorumda ayrı ayrı kırpabilirsiniz. Resimleri kırpmak, her bir yorumda görüntünün bir sürümünü oluşturmak SharePoint blob önbelleğini kullanarak resimlerin daha hızlı yüklenmesini sağlar. Bu şekilde, resim yalnızca bir kez yeniden boyutlandırılır ve bundan sonra son kullanıcılara birden çok kez yardımcı olmaya hazır olduğundan sunucu yüklemesi azalır. Görüntü yorumlarını kırpma hakkında daha fazla bilgi için bkz [. Görüntü yorumlarını kırpma](/sharepoint/dev/general-development/sharepoint-design-manager-device-channels).
