---
title: SharePoint Online'da görüntülerin ve JavaScript'in yüklenmesini geciktirme
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: Görüntülerin ve temel olmayan JavaScript'in yüklenmesini geciktirmek için JavaScript kullanarak SharePoint Çevrimiçi sayfaların yükleme süresini nasıl azaltacağınızı öğrenin.
ms.openlocfilehash: af75b3ede1136894bea0a7f4c00cc9498d194fe3
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65101303"
---
# <a name="delay-loading-images-and-javascript-in-sharepoint-online"></a>SharePoint Online'da görüntülerin ve JavaScript'in yüklenmesini geciktirme

Bu makalede, görüntülerin yüklenmesini geciktirmek için JavaScript kullanarak ve sayfa yüklenene kadar gerekli olmayan JavaScript'i yüklemeyi bekleyerek SharePoint Çevrimiçi sayfaların yükleme süresini nasıl azaltabileceğiniz açıklanır.
  
Görüntüler SharePoint Online'da sayfa yükleme hızlarını olumsuz etkileyebilir. Varsayılan olarak, çoğu modern İnternet tarayıcısı html sayfası yüklenirken görüntüleri önceden getirir. Bu, kullanıcı aşağı kaydırana kadar görüntüler ekranda görünmüyorsa sayfanın gereksiz şekilde yavaş yüklenmesine neden olabilir. Görüntüler, tarayıcının sayfanın görünür bölümünü yüklemesini engelleyebilir. Bu sorunu geçici olarak çözmek için javascript kullanarak önce görüntüleri yüklemeyi atlayabilirsiniz. Ayrıca, temel olmayan JavaScript'i yüklemek SharePoint sayfalarınızda indirme sürelerini de yavaşlatabilir. Bu konuda, SharePoint Online'da JavaScript ile sayfa yükleme sürelerini iyileştirmek için kullanabileceğiniz bazı yöntemler açıklanmaktadır.
  
## <a name="improve-page-load-times-by-delaying-image-loading-in-sharepoint-online-pages-by-using-javascript"></a>JavaScript kullanarak SharePoint Çevrimiçi sayfalarda görüntü yüklemesini geciktirerek sayfa yükleme sürelerini iyileştirme

Bir web tarayıcısının görüntüleri önceden getirmesini önlemek için JavaScript kullanabilirsiniz. Bu, genel belge işlemeyi hızlandırır. Bunu yapmak için src özniteliğinin değerini etiketinden \<img\> kaldırır ve şunun gibi bir veri özniteliğindeki bir dosyanın yoluyla değiştirirsiniz: data-src. Örneğin:
  
```html
<img src="" data-src="/sites/NavigationBySearch/_catalogs/masterpage/media/microsoft-white-8.jpg" />
```

Bu yöntemi kullanarak tarayıcı görüntüleri hemen indirmez. Görüntü zaten görünüm penceresindeyse, JavaScript tarayıcıya url'yi veri özniteliğinden almasını ve src özniteliğinin değeri olarak eklemesini söyler. Görüntü yalnızca kullanıcı kaydırdıkça yüklenir ve görüntüye gelir.
  
Bunların tümünü gerçekleştirmek için JavaScript kullanmanız gerekir.
  
Bir metin dosyasında, bir öğenin tarayıcının kullanıcı tarafından görünen bölümünde olup olmadığını denetlemek için **isElementInViewport()** işlevini tanımlayın.
  
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

Ardından **, loadItemsInView()** işlevinde **isElementInViewport**() kullanın. **loadItemsInView()** işlevi, tarayıcının kullanıcı tarafından görülebilen bölümünde yer alan data-src özniteliği için bir değere sahip tüm görüntüleri yükler. Metin dosyasına aşağıdaki işlevi ekleyin:
  
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

Son olarak, aşağıdaki örnekte gösterildiği gibi **window.onscroll()** içinden **loadItemsInView**() öğesini çağırın. Bu, görünüm penceresindeki tüm görüntülerin kullanıcının ihtiyaç duyduğu şekilde yüklenmesini sağlar, ancak daha önce yüklenmez. Metin dosyasına aşağıdakileri ekleyin:
  
```javascript
//Example of calling loadItemsInView() from within window.onscroll()
$(window).on("scroll", function () {
    loadItemsInView();
});

```

SharePoint Online için, #s4 çalışma alanı \<div\> etiketindeki kaydırma olayına aşağıdaki işlevi eklemeniz gerekir. Bunun nedeni, şeridin sayfanın en üstüne bağlı kalmasını sağlamak için pencere olaylarının geçersiz kılınmasıdır.
  
```javascript
//Keep the ribbon at the top of the page
$('#s4-workspace').on("scroll", function () {
    loadItemsInView();
});
```

Metin dosyasını .js uzantısıyla javascript dosyası olarak kaydedin, örneğin delayLoadImages.js.
  
delayLoadImages.js yazmayı tamamladıktan sonra, dosyanın içeriğini SharePoint Online'daki bir ana sayfaya ekleyebilirsiniz. Bunu, ana sayfadaki üst bilgiye bir betik bağlantısı ekleyerek yaparsınız. Ana sayfaya eklendikten sonra JavaScript, SharePoint Online sitenizdeki bu ana sayfa düzenini kullanan tüm sayfalara uygulanır. Alternatif olarak, bunu sitenizin yalnızca bir sayfasında kullanmak istiyorsanız, JavaScript'i sayfaya eklemek için betik düzenleyicisi Web Bölümünü kullanın. Daha fazla bilgi için şu konulara bakın:
  
- [Nasıl yapılır: SharePoint 2013'te bir siteye ana sayfa uygulama](/sharepoint/dev/general-development/how-to-apply-a-master-page-to-a-site-in-sharepoint)

- [Nasıl yapılır: SharePoint 2013'te sayfa düzeni oluşturma](/sharepoint/dev/general-development/how-to-create-a-page-layout-in-sharepoint)

### <a name="example-referencing-the-javascript-delayloadimagesjs-file-from-a-master-page-in-sharepoint-online"></a>Örnek: SharePoint Online'da ana sayfadan JavaScript delayLoadImages.js dosyasına başvurma
  
Bunun çalışması için ana sayfada jQuery'ye de başvurmanız gerekir. Aşağıdaki örnekte, ilk sayfa yüklemesinde yalnızca bir görüntünün yüklendiğini ancak sayfada birkaç resim daha olduğunu görebilirsiniz.
  
![Sayfaya yüklenen bir görüntüyü gösteren ekran görüntüsü.](../media/3d177ddb-67e5-43a7-b327-c9f9566ca937.png)
  
Aşağıdaki ekran görüntüsünde, görüntüye kaydırıldıktan sonra indirilen görüntülerin geri kalanı gösterilmektedir.
  
![Sayfaya yüklenen birkaç görüntüyü gösteren ekran görüntüsü.](../media/95eb2b14-f6a1-4eac-a5cb-96097e49514c.png)
  
JavaScript kullanarak görüntü yüklemesini geciktirme, performansı artırmada etkili bir teknik olabilir; Ancak, teknik genel bir web sitesine uygulanırsa, arama motorları görüntüleri düzenli olarak biçimlendirilmiş bir görüntüde gezindikleri gibi gezinemez. Görüntüdeki meta veriler sayfa yüklenene kadar orada olmadığından bu durum arama motorlarının derecelendirmelerini etkileyebilir. Arama motoru gezginleri yalnızca HTML'yi okur ve bu nedenle resimleri sayfada içerik olarak görmez. Görüntüler, arama sonuçlarında sayfaları sıralamak için kullanılan faktörlerden biridir. Bunun geçici bir yolu, resimleriniz için giriş metni kullanmaktır.
  
## <a name="github-code-sample-injecting-javascript-to-improve-performance"></a>GitHub kod örneği: Performansı artırmak için JavaScript ekleme

GitHub'de sağlanan [JavaScript ekleme](https://go.microsoft.com/fwlink/p/?LinkId=524759) makalesini ve kod örneğini kaçırmayın.
  
## <a name="see-also"></a>Ayrıca bkz.

[Office 2013 ve Kurumlar için Microsoft 365 Uygulamaları'da desteklenen tarayıcılar](https://support.office.com/article/57342811-0dc4-4316-b773-20082ced8a82)
  
[Nasıl yapılır: SharePoint 2013'te bir siteye ana sayfa uygulama](/sharepoint/dev/general-development/how-to-apply-a-master-page-to-a-site-in-sharepoint)
  
[Nasıl yapılır: SharePoint 2013'te sayfa düzeni oluşturma](/sharepoint/dev/general-development/how-to-create-a-page-layout-in-sharepoint)