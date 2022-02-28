---
title: Verilerde tahmine dayalı Advanced eDiscovery - Hızlı başlangıç
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
description: Advanced eDiscovery'da tahmine dayalı kodlama modülünü kullanmaya Advanced eDiscovery. Bu makale, araştırmanıza en uygun gözden geçirme kümesinde içeriği tanımlamak için tahmine dayalı kodlama kullanma işleminin  uç sürecinde size yol sağlar.
ms.openlocfilehash: 38607459057ff06a2ce74364b752130467deaddd
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62986729"
---
# <a name="quick-start-predictive-coding-in-advanced-ediscovery-preview"></a>Hızlı başlangıç: Advanced eDiscovery (önizleme)

Bu makalede, Advanced eDiscovery'de tahmine dayalı kodlama kullanmak için hızlı bir başlangıç Advanced eDiscovery. Advanced eDiscovery'daki tahmine dayalı kodlama modülü, gözden geçir edilecek içerik miktarını azaltmanıza yardımcı olmak için Advanced eDiscovery'daki akıllı makine öğrenme özelliklerini kullanır. Tahmine dayalı kodlama, büyük hacimli büyük hacimli olay içeriğini gözden geçirme için önceliklerini alacağız ve uygun bir öğe kümesine azaltmanıza yardımcı olur. Bu, gözden geçirme kümesinde en uygun öğelerin gözden geçirme önceliklerini belirlemeye yardımcı olacak kendi tahmine dayalı kodlama modellerinizi oluşturarak ve bu modelleri eğiterek  başarabilirsiniz.

İşte tahmine dayalı kodlama işlemiyle ilgili hızlı bir genel bakış:

![Tahmin kodlaması için hızlı başlangıç işlemi.](..\media\PredictiveCodingQuickStartProcess.png)

Çalışmaya başlamak için, ilgili veya ilgili değil en az 50 öğe olarak etiketlenmiş bir model oluşturabilirsiniz. Daha sonra sistem, tahmin puanlarını gözden geçirme kümesinde her öğeye uygulamak için bu eğitimi kullanır. Bu, öğeleri önce en uygun (veya ilgili olmayan) öğeleri gözden geçirmenizi sağlayan tahmin puanına göre filtrelemenizi sağlar. Daha yüksek ücret oranına ve geri çekme oranlarına sahip modelleri eğitmek için, sonraki eğitim turlarında öğeleri model model modellerine kadar etiketlemeye devam edersiniz. Model yazdırıldıktan sonra, gözden geçirilirken öğelere önceliklerini belirlemek için son tahmin filtresini uygulayabilirsiniz.

Tahmine dayalı kodlamaya ayrıntılı bir genel bakış için bkz[. Veri kodlarında tahmine dayalı Advanced eDiscovery](predictive-coding-overview.md).

## <a name="step-1-create-a-new-predictive-coding-model"></a>1. Adım: Yeni bir tahmine dayalı kodlama modeli oluşturma

İlk adım, gözden geçirme kümesinde yeni bir tahmine dayalı kodlama modeli oluşturmaktır

1. Görünüm Microsoft 365 uyumluluk merkezi bir büyük/Advanced eDiscovery sonra Gözden Geçir **kümeleri sekmesini** seçin.

2. Gözden geçirme kümesi açın ve ardından **AnalyticsManive** >  **coding (önizleme) öğesini tıklatın**.

   ![Gözden Geçirme kümesinde Çözümle açılan menüsüne tıklar ve Tahmine Dayalı kodlama sayfasına gider.](..\media\ManagePredictiveCoding.png)

3. Tahmine **dayalı kodlama modelleri (önizleme) sayfasında** Yeni **model'e tıklayın**.

4. Uçarak çıkış sayfasında, model için bir ad ve isteğe bağlı bir açıklama yazın.

5. Modeli **oluşturmak için** Kaydet'e tıklayın.

   Sistemin modelinizi hazırlaması birkaç dakika sürer. Hazır olduktan sonra, ilk eğitim turlarını gerçekleştirin.

Daha ayrıntılı yönergeler için bkz [. Tahmine dayalı kodlama modeli oluşturma](predictive-coding-create-model.md).

## <a name="step-2-perform-the-first-training-round"></a>2. Adım: İlk eğitim turını gerçekleştirme

Modeli oluşturdukta, sıradaki adım öğeleri ilgili veya ilgili değil olarak etiketleerek ilk eğitim turlarını tamamlamaktır.

1. Gözden geçirme kümesi açın ve ardından **AnalyticsManive** >  **coding (önizleme) öğesini tıklatın**.

2. Tahmine **dayalı kodlama modelleri (önizleme) sayfasında** , eğitmek istediğiniz modeli seçin.

3. Genel Bakış **sekmesindeki** **1. Tur'ın altında** Sonraki eğitim **turu başlat'a tıklayın**.

   Eğitim **sekmesi** görüntülenir ve etiketlemek için size 50 öğe içerir.

4. Her belgeyi gözden geçirin **ve ardından** etiketlemek **için okuma** bölmesinin en altındaki Uygun veya İlgili değil düğmesini seçin.

   ![Her belgeyi uygun veya uygun değil olarak etiketle.](..\media\TrainModel1.png)

5. 50 öğenin hepsini etiketledikten sonra, Son'a **tıklayın**.

    Sistemin etiketlemeden "öğrenmesi" ve modeli güncelleştirmesi birkaç dakika sürer. Bu işlem tamamlandığında, Tahmine Dayalı kodlama modelleri  (önizleme) sayfasında model **için Hazır durumu** görüntülenir.

Daha ayrıntılı yönergeler için bkz [. Tahmine dayalı bir kodlama modeli eğitin](predictive-coding-train-model.md).

## <a name="step-3-apply-the-prediction-score-filter-to-items-in-review-set"></a>3. Adım: Gözden geçirme kümesinde öğelere tahmin puanı filtresini uygulama

Bir eğitim turda finansal kiralama işlemi gerçekleştirdikten sonra, tahmin puanı filtresini gözden geçirme kümesinde öğelere uygulayabilirsiniz. Bu, modelin uygun veya ilgili değil olarak öngördüğü öğeleri gözden geçirmenizi sağlar.   

1. Gözden geçirme kümesi açın.

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

Daha ayrıntılı yönergeler için bkz [. Gözden geçirme kümesine tahmin filtresi uygulama](predictive-coding-apply-prediction-filter.md).

## <a name="step-4-perform-more-training-rounds"></a>4. Adım: Daha fazla eğitim turu gerçekleştirme

Büyük olasılıkla, modülü gözden geçirme kümesinde ilgili ve ilgili olmayan öğeleri daha iyi tahmin edecek şekilde eğitmek için daha fazla eğitim turu gerçekleştirmeniz gerekir. Genel olarak, modeli gereksinimlerinizi karşılayacak kadar eğitecek kadar eğitersiniz.

Daha fazla bilgi için bkz [. Ek eğitim yuvarlaları gerçekleştirme](predictive-coding-train-model.md#perform-additional-training-rounds)

## <a name="step-5-apply-the-final-prediction-score-filter-to-prioritize-review"></a>5. Adım: Gözden geçirme önceliklerini belirlemek için son tahmin puanı filtresini uygulama

Tüm eğitim turlarını ve modeli tamamladikten sonra ilgili ve ilgili olmayan öğelerin gözden geçirme önceliklerini belirlemek için, 3. Adımdaki yönergeleri yinele ve gözden geçirme kümesine son tahmin puanı uygulayın.
