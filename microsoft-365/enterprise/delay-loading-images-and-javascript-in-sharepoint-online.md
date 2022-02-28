---
title: SharePoint Online'da resimleri ve JavaScript'i SharePoint geciktirme
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/3/2019
audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Ent_O365
- SPO_Content
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
search.appverid:
- SPO160
- MET150
ms.assetid: 74d327e5-755f-4135-b9a5-7b79578c1bf9
description: Resimlerin ve temel olmayan JavaScript'in yüklenmesini geciktirmek için JavaScript kullanarak SharePoint Online sayfalarının yüklenme sürelerini azaltmayı öğrenin.
ms.openlocfilehash: 6b8eb479ae33b47081e33e45338c02d46f36e055
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62986720"
---
# <a name="delay-loading-images-and-javascript-in-sharepoint-online"></a>SharePoint Online'da resimleri ve JavaScript'i SharePoint geciktirme

Bu makalede, SharePoint Online sayfalarında resimlerin yüklenmesini geciktirmek için JavaScript kullanarak ve ayrıca temel öneme sahip olmayan JavaScript'in sayfa yüklenene kadar yüklenmesini bekletirerek, bu sayfaların yüklenme sürelerini nasıl azaltabilirsiniz? açıklanmıştır.
  
SharePoint Online'da resimler sayfa yükleme hızlarını olumsuz etkileyebilir. Varsayılan olarak, modern İnternet tarayıcılarının çoğu HTML sayfasını yüklerken resimleri önceden getirir. Bu durum, resimler ekranda görünmüyorsa kullanıcı aşağı kaydırana kadar sayfanın gereksiz bir yavaşlık içinde yüklemesi için neden olabilir. Resimler tarayıcının sayfanın görünür bölümünü yüklemesini engelleyebilir. Bu sorunu çözmek için, JavaScript kullanarak önce resimlerin yüklenmesini atlayabilirsiniz. Ayrıca, temel öneme sahip olmayan JavaScript'in yüklenmesi de SharePoint yavaşlatabilirsiniz. Bu konuda, SharePoint Online'da JavaScript ile sayfa yükleme sürelerini geliştirmek için kullanabileceğiniz bazı yöntemler açıklanmıştır.
  
## <a name="improve-page-load-times-by-delaying-image-loading-in-sharepoint-online-pages-by-using-javascript"></a>JavaScript kullanarak SharePoint Online sayfalarında resim yüklemesini geciktirerek sayfa yükleme sürelerini geliştirme

Web tarayıcısının resimleri önceden getirmesini önlemek için JavaScript kullanabilirsiniz. Bu, bir bütün olarak belge işlemeyi hızlandırır. Bunu yapmak için, etiketten src \<img\> özniteliğinin değerini kaldırır ve onun yerine bir veri özniteliğinde (data-src gibi) bir dosya yolu kullanılır. Örneğin:
  
```html
<img src="" data-src="/sites/NavigationBySearch/_catalogs/masterpage/media/microsoft-white-8.jpg" />
```

Bu yöntem kullanarak, tarayıcı resimleri hemen indirmez. Resim zaten görünüm penceresinde ise, JavaScript tarayıcıya veri özniteliğinden URL'yi almasını ve bunu src özniteliğinin değeri olarak eklemesini söyler. Resim ancak kullanıcı sayfayı kaydırarak görüntüye geldiğinde yüklenir.
  
Bunların hepsini yapmak için JavaScript kullan gerekir.
  
Bir metin dosyasında, öğenin tarayıcıda kullanıcı tarafından görülebilecek bir bölümde olup olmadığını kontrol etmek için **isElementInViewport()** işlevini tanımlayın.
  
```javascript
function isElementInViewport(el) {
  if (!el)
    return false;
  var rect = el.getBoundingClientRect();
  return (
    rect.top >= 0 &amp;&amp;
    rect.left >= 0 &amp;&amp;
    rect.bottom <= (window.innerHeight || document.documentElement.clientHeight) &amp;&amp;
    rect.right <= (window.innerWidth || document.documentElement.clientWidth)
  );
}
```

Ardından, **loadItemsInView()** işlevinde **isElementInViewport() işlevini** kullanın. **loadItemsInView()** işlevi, tarayıcıda kullanıcının görüntülebilen bir bölümünde yer alan ve data-src özniteliğinde değere sahip olan tüm resimleri yükletir. Metin dosyasına aşağıdaki işlevi ekleyin:
  
```javascript
function loadItemsInView() {
  //Select elements by the row id.
  $("#row [data-src]").each(function () {
      var isVisible = isElementInViewport(this);
      if (isVisible) {
          if ($(this).attr("src") == undefined) {
              $(this).attr("src", $(this).data("src"));
          }
      }
  });
}
```

Son olarak, aşağıdaki örnekte gösterildiği gibi **window.onscroll() işlevinin** içinde **loadItemsInView()** çağrısı yapın. Bu, görünüm görünümündeki tüm resimlerin, kullanıcıya gereken zamanda değil, yüklenirken tam olarak bundan sonra yüklenmelerini sağlar. Metin dosyasına aşağıdakini ekleyin:
  
```javascript
//Example of calling loadItemsInView() from within window.onscroll()
$(window).on("scroll", function () {
    loadItemsInView();
});

```

SharePoint Online için, #s4-workspace etiketinde kaydırma olayına aşağıdaki #s4 gerekir\<div\>. Bunun nedeni, şeridin sayfanın en üstünde kalmasını sağlamak için pencere olaylarının geçersiz kılınmasıdır.
  
```javascript
//Keep the ribbon at the top of the page
$('#s4-workspace').on("scroll", function () {
    loadItemsInView();
});
```

Metin dosyasını uzantısı JavaScript dosyası olarak kaydedin .js, örneğin delayLoadImages.js.
  
delayLoadImages.js Online'da dosyanın içeriğini bir ana sayfaya SharePoint. Bunu yapmak için, ana sayfada üst bilgiye bir betik bağlantısı eklersiniz. Ana sayfaya uygulandıktan sonra, JavaScript SharePoint Online siteniz içinde bu ana sayfa düzenini kullanan tüm sayfalara uygulanır. Alternatif olarak, bunu sitenizin tek bir sayfasında kullanmayı planlasanız, sayfaya JavaScript'i eklemek için betik düzenleyicisi Web Bölümünü kullanın. Daha fazla bilgi için şu konulara bakın:
  
- [Nasıl yapılır: SharePoint 2013'te siteye ana sayfa uygulama](/sharepoint/dev/general-development/how-to-apply-a-master-page-to-a-site-in-sharepoint)

- [SharePoint 2013'te sayfa düzeni oluşturma](/sharepoint/dev/general-development/how-to-create-a-page-layout-in-sharepoint)

### <a name="example-referencing-the-javascript-delayloadimagesjs-file-from-a-master-page-in-sharepoint-online"></a>Örnek: SharePoint Online'da delayLoadImages.js sayfasından JavaScript dosyası başvuru
  
Bu düzenin çalışması için, ana sayfada jQuery'ye de başvurabilirsiniz. Aşağıdaki örnekte, sayfada birkaç resim daha vardır, ancak ilk sayfa yüklemesinde yalnızca bir resmin yükleniyor olduğunu görebilirsiniz.
  
![Bir resmin sayfaya yükleniyor olduğunu gösteren ekran görüntüsü.](../media/3d177ddb-67e5-43a7-b327-c9f9566ca937.png)
  
Aşağıdaki ekran görüntüsünde, kalan resimler ekranı kaydırarak görüntüye indirildikten sonra bunlarda indirilir.
  
![Sayfaya yüklenen birkaç resmi gösteren ekran görüntüsü.](../media/95eb2b14-f6a1-4eac-a5cb-96097e49514c.png)
  
Performansı artırmaya yönelik etkili bir teknik olan JavaScript kullanarak resim yüklemesini geciktirme; Bununla birlikte, teknik bir genel web sitesinde uygulanırsa, arama motorları resimlerde, normal uzatlı resimlerde olduğu gibi gezinememektedir. Bu durum arama motorlarında sıralamaları etkileyebilir, çünkü resmin kendi meta verileri, sayfa yüklenirken gerçekten orada olmaz. Arama motoru gezginleri yalnızca HTML'yi okur ve bu nedenle resimleri sayfada içerik olarak görmez. Resimler, arama sonuçlarında sayfaları dereceli yapmak için kullanılan faktörlerdendir. Bu işe giriş niteliğindeki bir yol, resimleriniz için giriş metinlerini kullanmaktır.
  
## <a name="github-code-sample-injecting-javascript-to-improve-performance"></a>GitHub kodu örneği: Performansı artırmak için JavaScript ekleme

Bu makalede verilen JavaScript eklemesi makalesi [ve kod](https://go.microsoft.com/fwlink/p/?LinkId=524759) örneğini GitHub.
  
## <a name="see-also"></a>Ayrıca bkz.

[Office 2013 ve Kurumlar için Microsoft 365 Uygulamaları'de desteklenen tarayıcılar](https://support.office.com/article/57342811-0dc4-4316-b773-20082ced8a82)
  
[Nasıl yapılır: SharePoint 2013'te siteye ana sayfa uygulama](/sharepoint/dev/general-development/how-to-apply-a-master-page-to-a-site-in-sharepoint)
  
[SharePoint 2013'te sayfa düzeni oluşturma](/sharepoint/dev/general-development/how-to-create-a-page-layout-in-sharepoint)