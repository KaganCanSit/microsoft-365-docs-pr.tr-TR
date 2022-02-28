---
title: SharePoint Online'da performansı iyileştirmek için İçerik Sorgusu Web Bölümü yerine İçerik Arama Web Bölümü'SharePoint kullanma
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 4/20/2015
audience: Admin
ms.topic: article
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
- MET150
- SPO160
ms.assetid: e8ce6b72-745b-464a-85c7-cbf6eb53391b
description: SharePoint Server 2013 ve SharePoint Online'da İçerik Sorgusu Web Bölümü yerine İçerik Sorgusu Web Bölümü'SharePoint öğrenin.
ms.openlocfilehash: d41983a5771e42d357ae4d2adb5864e2a74fdd57
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62988740"
---
# <a name="using-content-search-web-part-instead-of-content-query-web-part-to-improve-performance-in-sharepoint-online"></a>SharePoint Online'da performansı iyileştirmek için İçerik Sorgusu Web Bölümü yerine İçerik Arama Web Bölümü'SharePoint kullanma

Bu makalede, SharePoint Server 2013 ve SharePoint Online'da İçerik Sorgusu Web Bölümü yerine İçerik Sorgusu Web Bölümü'ne geçerek performansın nasıl SharePoint açıklanmıştır.
  
SharePoint Server 2013 ve SharePoint Online'ın en güçlü yeni özelliklerinden biri İçerik Arama Web Bölümü'lerdir (CSWP). Bu Web Bölümü, sonuçları hızla almak için arama dizinini kullanır ve bunlar kullanıcıya gösterilir. Sayfalarınıza İçerik Sorgusu Web Bölümü (CQWP) yerine İçerik Arama Web Bölümü'ne bakarak kullanıcılarınıza daha iyi performans gösterebilirsiniz.
  
İçerik Sorgusu Web Bölümü yerine İçerik Arama Web Bölümü kullanmak, hemen her zaman SharePoint Online'da sayfa yükleme performansının önemli oranda SharePoint olur. Doğru sorguyu elde etmek için birkaç ek yapılandırma gerekir, ancak bunun ödülleri, gelişmiş performansa ve daha mutlu kullanıcılara neden olur.
  
## <a name="comparing-the-performance-gain-you-get-from-using-content-search-web-part-instead-of-content-query-web-part"></a>İçerik Sorgusu Web Bölümü yerine İçerik Arama Web Bölümü'ne kullanarak elde etmek için elde etmek

Aşağıdaki örnekler, İçerik Sorgusu Web Bölümü yerine İçerik Arama Web Bölümü'ni kullanarak elde kullanabileceğiniz göreceli performans kazançlarını gösterir. Site yapısı karmaşık olduğu ve çok geniş içerik sorgularında bu etki daha belirgin olur.
  
Bu örnek site aşağıdaki özelliklere sahiptir:
  
- 8 alt site düzeyi.
    
- Özel bir "meyve" içerik türü kullanan listeler.
    
- Web Bölümünde, tüm öğeler "meyve" içerik türüyle döndüren içerik sorgusu geniştir.
    
- Bu örnekte, 8 sitenin genelinde yalnızca 50 öğe kullanılır. Daha fazla içeriğe sahip sitelerde bu etki daha belirgin olur.
    
İçerik Sorgusu Web Bölümü sonuçlarının ekran görüntülerini burada bulabilirsiniz.
  
![Web bölümü için içerik sorgusunu gösteren grafik.](../media/b3d41f20-dfe5-46ed-9c0a-31057e82de33.png)
  
Internet Explorer'da, **yanıt** üst bilgisinde ayrıntılara bakmak için F12 geliştirici araçlarının Ağ sekmesini kullanın. Aşağıdaki ekran görüntüsinde, bu sayfa yüklemesi için **SPRequestDuration** değeri 924 milisaniyedir. 
  
![Screenshot showing request duration of 924.](../media/343571f2-a249-4de2-bc11-2cee93498aea.png)
  
 **SPRequestDuration** , sayfanın hazırlanması için sunucuda yapılan iş miktarını gösterir. İçerik Sorgusuyla İçerik Web Bölümleri Arama özelliğiyle geçiş Web Bölümleri, sayfanın işleme süresini önemli ölçüde azaltır. Buna karşılık, aşağıdaki ekran görüntüsinde gösterildiği gibi eşdeğer bir İçerik Arama Web Bölümü'ne sahip olan ve aynı sayıda sonuç döndüren bir sayfanın **SPRequestDuration** değeri 106 milisaniyedir. 
  
![106'nın Süre İsteği Süresini gösteren ekran görüntü.](../media/b46387ac-660d-4e5e-a11c-cc430e912962.png)
  
## <a name="adding-a-content-search-web-part-in-sharepoint-online"></a>SharePoint Online'da İçerik Arama Web Bölümü ekleme

İçerik Arama Web Bölümü ekleme, normal İçerik Sorgusu Web Bölümü eklemeye çok benzer. web sitesinde *İçerik Arama Web Bölümünü yapılandırma bölümündeki "*[İçerik Arama Web Bölümü Ekleme" SharePoint](https://support.office.com/article/Configure-a-Content-Search-Web-Part-in-SharePoint-0dc16de1-dbe4-462b-babb-bf8338c36c9a).
  
## <a name="creating-the-right-search-query-for-your-content-search-web-part"></a>İçerik Arama Web Bölümünüz için doğru arama sorgusunu oluşturma

İçerik Arama Web Bölümü eklediktan sonra, aramanızı daraltarak istediğiniz öğeleri geri getirebilirsiniz. Bunun nasıl konuyla ilgili ayrıntılı yönergeleri için, SharePoint'de İçerik Arama *Web* Bölümünü Yapılandırma bölümündeki "İçerik Arama Web Bölümünde gelişmiş bir sorgu yapılandırarak [içerik görüntüleme" bölümüne SharePoint](https://support.office.com/article/Configure-a-Content-Search-Web-Part-in-SharePoint-0dc16de1-dbe4-462b-babb-bf8338c36c9a).
  
## <a name="query-building-and-testing-tool"></a>Sorgu oluşturma ve test aracı

Karmaşık sorgular oluşturmak ve test etmek için bir araç olarak [Codeplex'in Search Query Tool'a](https://sp2013searchtool.codeplex.com/) bakın. 
  

