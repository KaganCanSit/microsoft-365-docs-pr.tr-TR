---
title: Advanced eDiscovery kümeleri için pano
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: ''
description: gözden geçirme Advanced eDiscovery geliştirmenize yardımcı olacak eğilimleri veya önemli istatistikleri tanımlamak üzere corpus'larınızı hızla çözümlemek için gözden geçirme kümelerinde yer alan en iyi panoyu kullanın.
ms.openlocfilehash: b7bc487e95c2dbae1a65aaad94face6bee19d39b
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62984697"
---
# <a name="advanced-ediscovery-dashboard-for-review-sets"></a>Advanced eDiscovery kümeleri için pano

Bazı durumlarda Advanced eDiscovery, gözden geçirmeniz gereken büyük miktarda belge ve e-posta iletiniz olabilir. Gözden geçirme işlemini başlatmadan önce, inceleme stratejinizi geliştirmenize yardımcı olacak eğilimleri veya önemli istatistikleri belirlemek için corpus'larınızı hızla çözümlemek istiyor olabilir. Bunu yapmak için, corpus'larınızı Advanced eDiscovery analiz etmek üzere gözden geçirme kümelerini görüntülemek üzere En Son Panosu'Advanced eDiscovery kullanabilirsiniz.

## <a name="step-1-create-a-widget-on-the-review-set-dashboard"></a>1. Adım: Gözden geçirme kümesi panosunda widget oluşturma

1. Aşağıdaki Microsoft 365 uyumluluk merkezi, **eBulma** > Advanced eDiscovery'ne gidip kurumuzla ilgili vakaların listesini görüntüleniyor.
  
2. Mevcut bir vakayı seçin.
  
3. Gözden Geçirme **Kümesi sekmesine** tıklayın ve gözden geçirme kümesi seçin.
  
4. Tek tek **sonuçlar açılan** listesinde Profil görünümü **ara'ya tıklayın**. 

   ![DashbordPivot.](../media/dashboardpivot.png)

   Profil **arama görünümü** sayfası görüntülenir; bu sayfayı ilk kez görüntülendiğinde üç varsayılan widget görüntülenir.

   ![Pano.](../media/dashboardonly.png)
  
5. Yeni **widget'a** tıklayın ve aşağıdaki öğelerden birini seçin:

   ![Yeni pencere öğesi açılan listesi.](../media/NewWidgetDropdownBox.png)

   - **Kitaplıktan seçim:** Varsayılan widget kitaplığını görüntüler. Bir widget'a tıklar ve **ardından Ekle'ye** tıklar ve bunu Ara profil görünümü sayfasındaki **widget'lara eklersiniz** .
  
   - **Özel pencere öğesi oluşturma:** Özel pencere öğesi ayarlamak için kullanabileceğiniz bir çıkış sayfası görüntüler. 

6. Özel pencere öğesi oluşturmak için, Widget ekle **uç öğesi sayfasında** şunları yapın:

   ![Pencere Öğesi Oluştur'a tıklayın.](../media/addwidget.png)

    a. Widget başlık çubuğunda görüntülenen widget için bir ad yazın. Widget'ı adlandırmak gerekir, ancak widget verilerini tanımlamak yararlı olur.

    b. Widget verileri için **kullanılacak Özet seç** açılan listesinden bir özellik seçin. Bu listede yer alan öğeler, gözden geçirme kümesinde yer alan öğeler için aranabilir özelliklerdir. Bu özelliklerin açıklaması için bkz. Veri [kaynağında meta veri Advanced eDiscovery](document-metadata-fields-in-Advanced-eDiscovery.md). Widget'ın özet seçenekleri bu konunun **Aranabilir alan adı** sütununda listelenir.

    c. Seçili özet özelliğinden verileri görüntülemek için bir grafik türü seçin.

  6. Özel **widget'ı** oluşturmak ve bu pencere öğesini Arama profili görünümü **sayfasında görüntülemek için Ekle'ye** tıklayın.

## <a name="step-2-create-a-review-set-search-query"></a>2. Adım: Gözden geçirme kümesi arama sorgusu oluşturma

1. Widget **başlık** çubuğunda ... öğesini ve sonra koşul **uygula'yı tıklatın**.

   ![Pano.](../media/searchprofilehome.png)

2. Çıkış sayfasında, filtre oluşturmak için widget tuşu veya widget grafiğindeki bir öğeye tıklayın.

   ![Filtre Oluştur.](../media/applyconditionfilter.png)

3. 1-2 adımlarını birden çok widget için diğer widget'lar için yinelayın. 

4. Bitir bittiğinde, koşullarınızı gözden **geçirme kümesi için** yeni bir arama sorgusu olarak kaydetmek için Sorgu olarak kaydet'e tıklayın.

   ![Sorgu.](../media/savequery.png)

5. Arama sonuçları **görünümüne dönmek** için Profil arama görünümünü kapatın.

   Herhangi bir görsel filtre oluşturduysanız, görüntülenen arama sonuçlarına sonuç sorgusu uygulanır ve 4. adımda kaydedilen arama sorgusu Kaydedilmiş **sorgular altında görüntülenir**. Gözden geçirme kümesi sorguları hakkında daha fazla bilgi için bkz [. Gözden geçirme kümesinde verileri sorgulama](review-set-search.md).
