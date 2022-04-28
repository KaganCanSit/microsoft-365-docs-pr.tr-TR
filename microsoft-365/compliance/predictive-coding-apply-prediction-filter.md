---
title: Tahmin puanı filtresini gözden geçirme kümesine uygulama
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
ms.reviewer: jefwan
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection: M365-security-compliance
description: Tahmine dayalı kodlama modelinin ilgili veya ilgili olmadığı tahmin edilen öğeleri görüntülemek için tahmin puanı filtresi kullanın.
ms.openlocfilehash: 64abac8b9f53baa9afb869d77296089544919fea
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65096622"
---
# <a name="apply-a-prediction-score-filter-to-a-review-set-preview"></a>Gözden geçirme kümesine tahmin puanı filtresi uygulama (önizleme)

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Microsoft Purview eKeşif'te (Premium) tahmine dayalı bir kodlama modeli oluşturduktan ve kararlı olduğu noktaya eğittikte, modelin belirlediği gözden geçirme kümesi öğelerini görüntülemek için tahmin puanı filtresini uygulayabilirsiniz (veya uygun değildir). Bir model oluşturduğunuzda, buna karşılık gelen tahmin puanı filtresi de oluşturulur. Bu filtreyi, belirtilen aralık içinde tahmin puanı atanmış öğeleri görüntülemek için kullanabilirsiniz. Genel olarak, **modelin** tahminde bulunduğu öğelere 0 ile **0,5** arasındaki tahmin puanları atanmamaktadır. **0,5** ile **1,0** arasında tahmin puanları atanan öğeler, modelin tahminde bulunduğu öğelerdir.

Tahmin puanı filtresini kullanmanın iki yolu şunlardır:

- Modelin tahminde bulunduğu bir gözden geçirme kümesindeki öğelerin gözden geçirilmesinin önceliğini belirleyin.

- Modelin tahminde bulunduğu gözden geçirme kümesindeki Cull öğeleri ilgili değildir. Alternatif olarak, ilgili olmayan öğelerin gözden geçirilmesinin önceliklerini değiştirmek için tahmin puanı filtresini kullanabilirsiniz.

## <a name="before-you-apply-a-prediction-score-filter"></a>Tahmin puanı filtresi uygulamadan önce

- Karşılık gelen tahmin puanı filtresinin oluşturulması için tahmine dayalı bir kodlama modeli oluşturun.

- Eğitim turlarından herhangi birinin ardından bir tahmin puanı filtresi uygulayabilirsiniz. Ancak, tahmin puanı filtresini kullanmadan önce birkaç tur yaptıktan sonra veya model kararlı olana kadar beklemek isteyebilirsiniz.

## <a name="apply-a-prediction-score-filter"></a>Tahmin puanı filtresi uygulama

1. Microsoft Purview uyumluluk portalında eBulma (Premium) servis talebini açın, **Gözden geçirme kümeleri** sekmesini seçin ve gözden geçirme kümesini açın.

   ![Filtreler açılır sayfasını görüntülemek için Filtreler'e tıklayın.](..\media\PredictionScoreFilter0.png)   

   Önceden yüklenmiş varsayılan filtreler, gözden geçirme kümesi sayfasının en üstünde görüntülenir. Bunları **Herhangi biri** olarak bırakabilirsiniz.

2. **Filtreler** açılır sayfasını görüntülemek için **Filtreler'e** tıklayın.

3. Bir filtre kümesini görüntülemek için **Analiz & tahmine dayalı kodlama** bölümünü genişletin.

      ![Analiz & tahmine dayalı kodlama bölümündeki tahmin puanı filtresi.](..\media\PredictionScoreFilter1.png)

   Tahmin puanı filtreleri için adlandırma kuralı **Tahmin puanı (model adı)** şeklindedir. Örneğin, **Model A** adlı modelin tahmin puanı filtre adı **Tahmin puanı (Model A) şeklindedir**.

4. Kullanmak istediğiniz tahmin puanı filtresini seçin ve **bitti'ye** tıklayın.

5. Gözden geçirme kümesi sayfasında, tahmin puanı filtresinin açılan menüsüne tıklayın ve tahmin puanı aralığı için en düşük ve en yüksek değerleri yazın. Örneğin, aşağıdaki ekran görüntüsünde **0,5** ile **1,0** arasında bir tahmin puanı aralığı gösterilmektedir.

   ![Tahmin puanı filtresi için en düşük ve en yüksek değerler.](..\media\PredictionScoreFilter2.png)

6. Filtreyi gözden geçirme kümesine otomatik olarak uygulamak için filtrenin dışına tıklayın.

  Belirttiğiniz aralık içinde tahmin puanına sahip belgelerin listesi gözden geçirme kümesi sayfasında görüntülenir. 

  > [!TIP]
  > Belgeye atanan gerçek tahmin puanını görüntülemek için, okuma **bölmesindeKi Meta Veri** sekmesine tıklayabilirsiniz. Gözden geçirme kümesindeki tüm modellerin tahmin puanları **RelevanceScores** meta veri özelliğinde görüntülenir.

## <a name="more-information"></a>Daha fazla bilgi

- Filtreleri kullanma hakkında daha fazla bilgi için bkz. [Gözden geçirme kümesindeki içeriği sorgulama ve filtreleme](review-set-search.md).
