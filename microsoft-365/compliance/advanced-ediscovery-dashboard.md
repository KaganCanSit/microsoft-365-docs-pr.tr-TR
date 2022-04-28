---
title: Gözden geçirme kümeleri için eBulma (Premium) panosu
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
ms.date: 04/05/2022
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: ''
description: Gözden geçirme stratejinizi geliştirmenize yardımcı olacak eğilimleri veya önemli istatistikleri belirlemek üzere corpus'unuzu hızla analiz etmek üzere gözden geçirme kümeleri için Microsoft Purview eBulma (Premium) panosunu kullanın.
ms.openlocfilehash: 00d4c6648d74fdf459965ed410dd43c73e698c23
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65097876"
---
# <a name="ediscovery-premium-dashboard-for-review-sets"></a>Gözden geçirme kümeleri için eBulma (Premium) panosu

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Microsoft Purview eKeşif 'te (Premium) bazı durumlarda, gözden geçirilmesi gereken çok sayıda belgeniz ve e-posta iletileriniz olabilir. Gözden geçirme işlemine başlamadan önce, gözden geçirme stratejinizi geliştirmenize yardımcı olacak eğilimleri veya önemli istatistikleri belirlemek için corpus'unuzu hızla analiz etmek isteyebilirsiniz. Bunu yapmak için, corpus'unuzu hızla analiz etmek üzere gözden geçirme kümeleri için eBulma (Premium) panosunu kullanabilirsiniz.

## <a name="step-1-create-a-widget-on-the-review-set-dashboard"></a>1. Adım: Gözden geçirme kümesi panosunda pencere öğesi oluşturma

1. Microsoft Purview uyumluluk portalında, kuruluşunuzdaki servis taleplerinin listesini görüntülemek için **eBulma > eBulma (Premium)** bölümüne gidin.
  
2. Mevcut bir servis talebini seçin.
  
3. **Gözden Geçir Kümesi** sekmesine tıklayın ve bir gözden geçirme kümesi seçin.
  
4. **Tek tek sonuçlar** açılan listesinde **Profil görünümünde ara'ya** tıklayın. 

   ![DashbordPivot.](../media/dashboardpivot.png)

   **Arama profili görünümü** sayfası görüntülenir; bu sayfayı ilk kez görüntülüyorsanız, üç varsayılan pencere öğesi görüntülenir.

   ![Pano.](../media/dashboardonly.png)
  
5. **Yeni pencere öğesine** tıklayın ve aşağıdaki öğelerden birini seçin:

   ![Yeni pencere öğesi açılan listesi.](../media/NewWidgetDropdownBox.png)

   - **Kitaplıktan seçim yapın:** Varsayılan pencere öğesi kitaplığını görüntüler. Bir pencere öğesine tıklayın ve ardından **Ekle'ye** tıklayarak **Arama profili görünümü** sayfasındaki pencere öğelerine ekleyin.
  
   - **Özel pencere öğesi oluşturma:** Özel pencere öğesi ayarlamak için kullanabileceğiniz bir açılır sayfa görüntüler. 

6. Özel bir pencere öğesi oluşturmak için Pencere **öğesi ekle** açılır sayfasında aşağıdakileri yapın:

   ![Pencere Öğesi Oluştur'u seçin.](../media/addwidget.png)

    a. Pencere öğesi başlık çubuğunda görüntülenen pencere öğesi için bir ad yazın. Bir pencere öğesini adlandırmak gereklidir, ancak pencere öğesi verilerini tanımlamak yararlı olur.

    b. **Özet seç** açılan listesinde pencere öğesi verileri için kullanılacak bir özellik seçin. Bu listedeki öğeler, gözden geçirme kümesindeki öğelerin aranabilir özellikleridir. Bu özelliklerin açıklaması için bkz[. eBulma'da (Premium) belge meta veri alanları](document-metadata-fields-in-Advanced-eDiscovery.md). Pencere öğesinin özet seçenekleri, bu konunun **Aranabilir alan adı** sütununda listelenir.

    c. Seçili özet özelliğindeki verileri görüntülemek için bir grafik türü seçin.

  6. Özel pencere öğesini oluşturmak ve **Arama profili görünümü** sayfasında görüntülemek için **Ekle'ye** tıklayın.

## <a name="step-2-create-a-review-set-search-query"></a>2. Adım: Gözden geçirme kümesi arama sorgusu oluşturma

1. Pencere öğesi başlık çubuğunda **...** öğesine tıklayın ve ardından **Koşulu uygula'ya** tıklayın.

   ![Pano.](../media/searchprofilehome.png)

2. Açılır sayfada, pencere öğesi anahtarı veya pencere öğesi grafiğindeki bir öğeye tıklayarak filtre oluşturun.

   ![CreateFilter.](../media/applyconditionfilter.png)

3. Diğer pencere öğeleri birden çok pencere öğesi için 1-2 arası adımları yineleyin. 

4. İşiniz bittiğinde, koşullarınızı gözden geçirme kümesi için yeni bir arama sorgusu olarak kaydetmek için Sorgu **olarak kaydet'e** tıklayın.

   ![Sorgu.](../media/savequery.png)

5. Arama sonuçları **görünümüne dönmek için Arama profili** görünümünü kapatın.

   Herhangi bir görsel filtre oluşturduysanız, sonuçta elde edilen sorgu görüntülenen arama sonuçlarına uygulanır ve 4. adımda kaydettiğiniz arama sorgusu **Kaydedilen sorgular** altında görüntülenir. Gözden geçirme kümesi sorguları hakkında daha fazla bilgi için bkz. [Gözden geçirme kümesindeki verileri sorgulama](review-set-search.md).
