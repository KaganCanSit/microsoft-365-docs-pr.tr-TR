---
title: SharePoint Online'da performansı geliştirmek için İçerik Sorgusu Web Bölümü yerine İçerik Arama Web Bölümü kullanma
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: İçerik Sorgusu Web Bölümü'nü SharePoint Server 2013 ve SharePoint Online'daki İçerik Arama Web Bölümü ile değiştirerek performansı artırmayı öğrenin.
ms.openlocfilehash: 45b43b3071ca39c67283ac70ab92b20e2fc7e21a
ms.sourcegitcommit: 349f0f54b0397cdd7d8fbb9ef07f1b6654a32d6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/20/2022
ms.locfileid: "65621993"
---
# <a name="using-content-search-web-part-instead-of-content-query-web-part-to-improve-performance-in-sharepoint-online"></a>SharePoint Online'da performansı geliştirmek için İçerik Sorgusu Web Bölümü yerine İçerik Arama Web Bölümü kullanma

Bu makalede, İçerik Sorgusu Web Bölümü'nü SharePoint Server 2013 ve SharePoint Online'daki İçerik Arama Web Bölümü ile değiştirerek performansın nasıl artırıldığı açıklanır.
  
SharePoint Server 2013 ve SharePoint Online'ın en güçlü yeni özelliklerinden biri İçerik Arama Web Bölümü'dür (CSWP). Bu Web Bölümü, kullanıcıya gösterilen sonuçları hızla almak için arama dizinini kullanır. Kullanıcılarınız için performansı geliştirmek için sayfalarınızdaki İçerik Sorgusu Web Bölümü (CQWP) yerine İçerik Arama Web Bölümü'nü kullanın.
  
İçerik Sorgusu Web Bölümü üzerinde İçerik Arama Web Bölümü kullanmak, SharePoint Online'da neredeyse her zaman daha iyi sayfa yükleme performansına neden olur. Doğru sorguyu almak için biraz ek yapılandırma vardır, ancak ödüller iyileştirilmiş performans ve daha mutlu kullanıcılardır.
  
## <a name="comparing-the-performance-gain-you-get-from-using-content-search-web-part-instead-of-content-query-web-part"></a>İçerik Sorgusu Web Bölümü yerine İçerik Arama Web Bölümü'nü kullanarak elde ettiğiniz performans kazancını karşılaştırma

Aşağıdaki örneklerde, İçerik Sorgusu Web Bölümü yerine İçerik Arama Web Bölümü kullandığınızda alabileceğiniz göreli performans kazançları gösterilir. Karmaşık bir site yapısı ve geniş içerik sorguları ile etkileri daha belirgindir.
  
Bu örnek site aşağıdaki özelliklere sahiptir:
  
- 8 alt site düzeyi.
    
- Özel bir "meyve" içerik türü kullanan listeler.
    
- Web Bölümünde içerik sorgusu geniştir ve içerik türü "fruit" olan tüm öğeleri döndürür.
    
- Örnek, 8 site genelinde yalnızca 50 öğe kullanır. Daha fazla içeriğe sahip siteler için efektler daha da belirgin olacaktır.
    
İçerik Sorgusu Web Bölümü sonuçlarının ekran görüntüsü aşağıdadır.
  
![Web bölümü için içerik sorgusunu gösteren grafik.](../media/b3d41f20-dfe5-46ed-9c0a-31057e82de33.png)
  
Internet Explorer'da, yanıt üst bilgisinin ayrıntılarına bakmak için F12 geliştirici araçlarının **Ağ** sekmesini kullanın. Aşağıdaki ekran görüntüsünde, bu sayfa yüklemesinin **SPRequestDuration** değeri 924 milisaniyedir. 
  
![924 istek süresini gösteren ekran görüntüsü.](../media/343571f2-a249-4de2-bc11-2cee93498aea.png)
  
 **SPRequestDuration** , sayfayı hazırlamak için sunucuda yapılan çalışma miktarını gösterir. Arama Web Bölümleri İçerik ile Sorgu Web Bölümleri İçeriği değiştirmek, sayfayı işlemek için gereken süreyi önemli ölçüde azaltır. Buna karşılık, eşdeğer bir İçerik Arama Web Bölümü olan ve aynı sayıda sonuç döndüren bir sayfanın **SPRequestDuration** değeri bu ekran görüntüsünde gösterildiği gibi 106 milisaniyedir: 
  
![İstek Süresi 106'nın gösterildiği ekran görüntüsü.](../media/b46387ac-660d-4e5e-a11c-cc430e912962.png)
  
## <a name="adding-a-content-search-web-part-in-sharepoint-online"></a>SharePoint Online'da İçerik Arama Web Bölümü Ekleme

İçerik Arama Web Bölümü eklemek, normal İçerik Sorgusu Web Bölümüne benzer. SharePoint'da *İçerik Arama Web Bölümü* Yapılandırma bölümündeki "[İçerik Arama Web Bölümü](https://support.office.com/article/Configure-a-Content-Search-Web-Part-in-SharePoint-0dc16de1-dbe4-462b-babb-bf8338c36c9a) Ekleme" bölümüne bakın.
  
## <a name="creating-the-right-search-query-for-your-content-search-web-part"></a>İçerik Arama Web Bölümünüz için doğru arama sorgusunu oluşturma

İçerik Arama Web Bölümü ekledikten sonra, aramayı daraltabilir ve istediğiniz öğeleri döndürebilirsiniz. Bunun nasıl yapılacağına ilişkin ayrıntılı yönergeler için, *SharePoint'da İçerik Arama Web Bölümü Yapılandırma bölümündeki "İçerik Arama Web Bölümünde gelişmiş sorgu yapılandırarak içeriği görüntüleme"* bölümüne [](https://support.office.com/article/Configure-a-Content-Search-Web-Part-in-SharePoint-0dc16de1-dbe4-462b-babb-bf8338c36c9a)bakın.
  
## <a name="query-building-and-testing-tool"></a>Sorgu oluşturma ve test aracı

Karmaşık sorgular oluşturmaya ve test etmeye yönelik bir araç için bkz. Codeplex'te [Arama Sorgusu Aracı](https://sp2013searchtool.codeplex.com/) . 
  

