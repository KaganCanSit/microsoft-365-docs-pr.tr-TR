---
title: Gözden geçirme kümesinde öğelere tahmin puanı filtresi uygulama
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
ms.reviewer: jefwan
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection: M365-security-compliance
description: Tahmin puanı filtresi kullanarak, uygun veya ilgili değil olarak öngörülen tahmini bir kodlama modeli olan öğeleri görüntüler.
ms.openlocfilehash: 04d0881e36c28a70df58a1aa7b054c641dfeeb2a
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62988095"
---
# <a name="apply-a-prediction-score-filter-to-a-review-set-preview"></a>Gözden geçirme kümesine tahmin puanı filtresi uygulama (önizleme)

Advanced eDiscovery'te tahmine dayalı bir kodlama modeli oluşturduk ve bu modeli kararlı olduğu noktaya eğitdikten sonra, modelin ilgili (veya ilgili değil) olduğunu belirlediği gözden geçirme kümesi öğelerini görüntülemek için tahmin puanı filtresini uygulayabilirsiniz. Bir model oluşturulduğunda, buna karşılık gelen bir tahmin puanı filtresi de oluşturulur. Belirtilen aralık içinde bir tahmin puanı atanmış olan öğeleri görüntülemek için bu filtreyi kullanabilirsiniz. Genel olarak, tahmin puanları 0 ile **0,5** arasında, modelin uygun olmadığını tahmin edilen öğelere atanır. Atanmış tahmin puanları atanan öğeler **0,5** ile **1,0** arasında, modelin tahmin edenin uygun olduğu öğelerdir.

Tahmin puanı filtresini iki şekilde kullanabilirsiniz:

- Modelin uygun öngörüldüğü bir gözden geçirme kümesinde öğelerin gözden geçirme önceliklerini belirleme.

- Modelin tahmin edilen gözden geçirme kümesinden gelenull öğeler uygun değildir. Alternatif olarak, ilgili olmayan öğelerin gözden geçirme önceliklerini belirlemek için tahmin puanı filtresini kullanabilirsiniz.

## <a name="before-you-apply-a-prediction-score-filter"></a>Tahmin puanı filtresi uygulamadan önce

- Karşılık gelen bir tahmin puanı filtresi oluşturulacak şekilde tahmine dayalı bir kodlama modeli oluşturun.

- Herhangi bir eğitim turuna göre tahmin puanı filtresi uygulayabilirsiniz. Ancak, tahmin puanı filtresini kullanmadan önce birkaç tur atana kadar veya model kararlı olana kadar beklemek de istiyor olabilir.

## <a name="apply-a-prediction-score-filter"></a>Tahmin puanı filtresi uygulama

1. Gözden Microsoft 365 uyumluluk merkezi büyük/Advanced eDiscovery açın, Gözden Geçir **kümeleri** sekmesini seçin ve sonra da gözden geçirme kümesini açın.

   ![Filtreler uç sayfası görüntülemek için Filtreler'e tıklayın.](..\media\PredictionScoreFilter0.png)   

   Önceden yüklenmiş olan varsayılan filtreler gözden geçirme kümesi sayfasının en üstünde görüntülenir. Bu kümeyi Herhangi biri olarak **bırakın**.

2. Filtreler **uç** sayfası görüntülemek **için Filtreler'e** tıklayın.

3. Bir filtre **& görüntülemek için Çözümleme** ve tahmine dayalı kodlama bölümünü genişletin.

      ![Çözümleme verileri ve tahmine dayalı & tahmin puanı filtresi.](..\media\PredictionScoreFilter1.png)

   Tahmin puanı filtreleri için adlandırma kuralı Tahmin **puanıdır (model adı).**. Örneğin, Model **A** adlı bir modelin tahmin puanı filtre adı, Tahmin puanı **(Model A) olur**.

4. Kullanmak istediğiniz tahmin puanı filtresini seçin ve ardından Bitti'ye **tıklayın**.

5. Gözden geçirme kümesi sayfasında, tahmin puanı filtresi açılan kutusuna tıklayın ve tahmin puanı aralığı için en küçük ve en büyük değerleri yazın. Örneğin, aşağıdaki ekran görüntüsünde **0,5** ile **1,0 arasındaki bir tahmin puanı aralığı görüntü).**

   ![Tahmin puanı filtresi için en küçük ve en büyük değerler.](..\media\PredictionScoreFilter2.png)

6. Filtreyi gözden geçirme kümesine otomatik olarak uygulamak için filtrenin dışına tıklayın.

  Gözden geçirme kümesi sayfasında, belirttiğiniz aralık içinde tahmin puanına sahip belgelerin listesi görüntülenir. 

  > [!TIP]
  > Bir belgeye gerçek tahmin puanı atamayı görüntülemek için, okuma bölmesinde **Meta** Veri sekmesini tıklatın. gözden geçirme kümesinde tüm modellerin tahmin puanları İlgi Puanı **meta veri özelliğinde** görüntülenir.

## <a name="more-information"></a>Daha fazla bilgi

- Filtreleri kullanma hakkında daha fazla bilgi için bkz [. Gözden geçirme kümesinde içeriği sorgulama ve filtreleme](review-set-search.md).
