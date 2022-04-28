---
title: eBulmada tahmine dayalı kodlama (Premium) - Hızlı başlangıç
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
description: eBulma (Premium) içinde tahmine dayalı kodlama modülünü kullanmaya başlamayı öğrenin. Bu makale, araştırmanıza en uygun bir inceleme kümesindeki içeriği tanımlamak için tahmine dayalı kodlamayı kullanma işleminde size yol gösterir.
ms.openlocfilehash: ac8e31540fbe817b83b5fd0bdae2fadea7040b1a
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65100803"
---
# <a name="quick-start-predictive-coding-in-ediscovery-premium-preview"></a>Hızlı başlangıç: eBulmada tahmine dayalı kodlama (Premium) (önizleme)

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Bu makalede, Microsoft Purview eKeşif'te (Premium) tahmine dayalı kodlamayı kullanmak için hızlı bir başlangıç sunun. Tahmine dayalı kodlama modülü, araştırmanızla ilgili olmayan büyük hacimli olay içeriğini iptal etmenize yardımcı olmak için akıllı, makine öğrenmesi özelliklerini kullanır. Bu, gözden geçirme için en ilgili öğeleri önceliklendirmenize yardımcı olan kendi tahmine dayalı kodlama modellerinizi oluşturup eğiterek gerçekleştirilir.

Tahmine dayalı kodlama işlemine hızlı bir genel bakış aşağıda verilmiştir:

![Tahmin kodlaması için hızlı başlangıç işlemi.](..\media\PredictiveCodingQuickStartProcess.png)

Başlamak için, ilgili veya ilgili olmayan 50 öğeyi etiketleyerek bir model oluşturursunuz. Sistem daha sonra bu eğitimi kullanarak inceleme kümesindeki her öğeye tahmin puanlarını uygular. Bu, öğeleri tahmin puanına göre filtrelemenize olanak tanır ve bu sayede önce en ilgili (veya ilgili olmayan) öğeleri gözden geçirebilirsiniz. Modelleri daha yüksek doğruluk ve geri çağırma oranlarıyla eğitmek istiyorsanız, model sabit olana kadar sonraki eğitim turlarında öğeleri etiketlemeye devam edebilirsiniz. Model kararlı hale getirildikten sonra, gözden geçirecek öğelerin önceliklerini ayarlamak için son tahmin filtresini uygulayabilirsiniz.

Tahmine dayalı kodlamaya ayrıntılı bir genel bakış için bkz. [eBulmada tahmine dayalı kodlama hakkında bilgi edinme (Premium)](predictive-coding-overview.md).

## <a name="step-1-create-a-new-predictive-coding-model"></a>1. Adım: Yeni bir tahmine dayalı kodlama modeli oluşturma

İlk adım, gözden geçirme kümesinde yeni bir tahmine dayalı kodlama modeli oluşturmaktır

1. Microsoft Purview uyumluluk portalında bir eBulma (Premium) servis talebi açın ve ardından **Kümeleri gözden geçir** sekmesini seçin.

2. Bir gözden geçirme kümesi açın ve **ardından Analytics** >  **Tahmine dayalı kodlamayı yönet (önizleme)'** ye tıklayın.

   ![Tahmine dayalı kodlama sayfasına gitmek için gözden geçirme kümesindeki Çözümle açılan menüsüne tıklayın.](..\media\ManagePredictiveCoding.png)

3. **Tahmine dayalı kodlama modelleri (önizleme)** sayfasında **Yeni model'e** tıklayın.

4. Açılır sayfada model için bir ad ve isteğe bağlı bir açıklama yazın.

5. Modeli oluşturmak için **Kaydet'e** tıklayın.

   Sistemin modelinizi hazırlaması birkaç dakika sürer. Hazır olduktan sonra ilk eğitim turunu gerçekleştirebilirsiniz.

Daha ayrıntılı yönergeler için bkz. [Tahmine dayalı kodlama modeli oluşturma](predictive-coding-create-model.md).

## <a name="step-2-perform-the-first-training-round"></a>2. Adım: İlk eğitim turunu gerçekleştirme

Modeli oluşturduktan sonra, sonraki adım öğeleri ilgili veya uygun olmayan olarak etiketleyerek ilk eğitim turunu tamamlamaktır.

1. Gözden geçirme kümesini açın ve ardından **Analytics** >  **Tahmine dayalı kodlamayı yönet (önizleme)** seçeneğine tıklayın.

2. **Tahmine dayalı kodlama modelleri (önizleme)** sayfasında eğitmek istediğiniz modeli seçin.

3. **Genel Bakış** sekmesinde, 1. **Tur'un** altında **Sonraki eğitim turunu başlat'a** tıklayın.

   **Eğitim** sekmesi görüntülenir ve etiketlemeniz için 50 öğe içerir.

4. Her belgeyi gözden geçirin ve ardından okuma bölmesinin alt kısmındaki **İlgili** veya **İlgili değil** düğmesini seçerek etiketleyin.

   ![Her belgeyi ilgili olarak etiketle veya ilgili değil olarak etiketle.](..\media\TrainModel1.png)

5. 50 öğenin tümünü etiketledikten sonra **Son'a** tıklayın.

    Sistemin etiketlemenizden "öğrenmesi" ve modeli güncelleştirmesi birkaç dakika sürer. Bu işlem tamamlandığında, **Tahmine dayalı kodlama modelleri (önizleme)** sayfasında model için **Hazır** durumu görüntülenir.

Daha ayrıntılı yönergeler için bkz. [Tahmine dayalı kodlama modelini eğitin](predictive-coding-train-model.md).

## <a name="step-3-apply-the-prediction-score-filter-to-items-in-review-set"></a>3. Adım: Tahmin puanı filtresini gözden geçirme kümesindeki öğelere uygulama

Bir eğitim turu kiraladıktan sonra, tahmin puanı filtresini gözden geçirme kümesindeki öğelere uygulayabilirsiniz. Bu, modelin ilgili olarak tahminde bulunduğu veya ilgili olmadığı öğeleri gözden geçirmenize olanak tanır.   

1. Gözden geçirme kümesini açın.

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

Daha ayrıntılı yönergeler için bkz. [Gözden geçirme kümesine tahmin filtresi uygulama](predictive-coding-apply-prediction-filter.md).

## <a name="step-4-perform-more-training-rounds"></a>4. Adım: Daha fazla eğitim turu gerçekleştirme

Büyük olasılıkla, gözden geçirme kümesindeki ilgili ve ilgili olmayan öğeleri daha iyi tahmin etmek için modülü eğitmek için daha fazla eğitim turu gerçekleştirmeniz gerekir. Genel olarak, modeli gereksinimlerinizi karşılayacak kadar kararlı hale gelene kadar yeterince eğiteceksiniz.

Daha fazla bilgi için bkz. [Ek eğitim yuvarlamaları gerçekleştirme](predictive-coding-train-model.md#perform-additional-training-rounds)

## <a name="step-5-apply-the-final-prediction-score-filter-to-prioritize-review"></a>5. Adım: Gözden geçirmeyi önceliklendirmek için son tahmin puanı filtresini uygulama

Tüm eğitim turlarını tamamladıktan ve modeli kararlı hale getirdikten sonra ilgili ve ilgili olmayan öğelerin gözden geçirilmesine öncelik vermek için son tahmin puanını gözden geçirme kümesine uygulamak için 3. Adımdaki yönergeleri yineleyin.
