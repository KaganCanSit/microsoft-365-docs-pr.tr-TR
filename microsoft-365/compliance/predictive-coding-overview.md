---
title: eBulma (Premium) (önizleme) için tahmine dayalı kodlama modülü
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
description: eBulma'daki (Premium) yeni tahmine dayalı kodlama modülü, bir inceleme kümesindeki öğeleri analiz etmek için makine öğrenmesini kullanarak olay veya araştırmanızla ilgili öğeleri tahmin eder.
ms.openlocfilehash: 3ea3d59aa2387b1a762e66fd11942ed96a6288a2
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66625049"
---
# <a name="learn-about-predictive-coding-in-ediscovery-premium-preview"></a>eBulma(Premium) (önizleme) içinde tahmine dayalı kodlama hakkında bilgi edinin

eBulma (Premium) içindeki tahmine dayalı kodlama modülü, inceleyecek içerik miktarını azaltmanıza yardımcı olmak için akıllı, makine öğrenmesi özelliklerini kullanır. Tahmine dayalı kodlama, büyük hacimli servis talebi içeriğini gözden geçirmek üzere önceliklendirebileceğiniz ilgili bir öğe kümesiyle azaltmanıza ve bunları iptal etmenize yardımcı olur. Bu, bir gözden geçirme kümesindeki en ilgili öğelerin gözden geçirilmesini önceliklendirmenize yardımcı olan kendi tahmine dayalı kodlama modellerinizi oluşturup eğiterek gerçekleştirilir.

Tahmine dayalı kodlama modülü, bir gözden geçirme kümesi içinde modeli yönetmenin karmaşıklığını kolaylaştırmak ve modelinizi eğitmek için yinelemeli bir yaklaşım sağlayarak eKeşif (Premium) içindeki makine öğrenmesi özellikleriyle daha hızlı çalışmaya başlamanızı sağlayacak şekilde tasarlanmıştır. Başlamak için bir model oluşturabilir, ilgili veya uygun olmayan en az 50 öğe etiketleyebilirsiniz. Sistem, inceleme kümesindeki her öğeye tahmin puanları uygulamak için bu eğitimi kullanır. Bu, öğeleri tahmin puanına göre filtrelemenize olanak tanır ve bu sayede önce en ilgili (veya ilgili olmayan) öğeleri gözden geçirebilirsiniz. Modelleri daha yüksek doğruluk ve geri çağırma oranlarıyla eğitmek istiyorsanız, model sabit olana kadar sonraki eğitim turlarında öğeleri etiketlemeye devam edebilirsiniz.  

## <a name="the-predictive-coding-workflow"></a>Tahmine dayalı kodlama iş akışı

Aşağıda tahmine dayalı kodlama iş akışının her adımına genel bir bakış ve açıklama bulabilirsiniz. Tahmine dayalı kodlama işleminin kavramlarının ve terminolojisinin daha ayrıntılı bir açıklaması için bkz. [Tahmine dayalı kodlama başvurusu](predictive-coding-reference.md).

![Tahmine dayalı kodlama iş akışı.](..\media\PredictiveCodingWorkflow.png)

1. **Gözden geçirme kümesinde yeni bir tahmine dayalı kodlama modeli oluşturun**. İlk adım, inceleme kümesinde yeni bir tahmine dayalı kodlama modeli oluşturmaktır. Model oluşturmak için inceleme kümesinde en az 2.000 öğe olmalıdır. Bir model oluşturduktan sonra, sistem *denetim kümesi* olarak kullanılacak öğe sayısını belirler. Denetim kümesi, eğitim sürecinde modelin öğelere atadığını tahmin puanlarını eğitim yuvarlamaları sırasında gerçekleştirdiğiniz etiketlemeyle değerlendirmek için kullanılır. Denetim kümesinin boyutu, gözden geçirme kümesindeki öğelerin sayısına ve model oluşturulurken ayarlanan hata değerlerinin güvenilirlik düzeyine ve kenar boşluğuna bağlıdır. Denetim kümesindeki öğeler hiçbir zaman değişmez ve kullanıcılara tanımlanamaz.

   Daha fazla bilgi için bkz. [Tahmine dayalı kodlama modeli oluşturma](predictive-coding-create-model.md).

2. **Öğeleri ilgili veya ilgili değil olarak etiketleyerek ilk eğitim turunu tamamlayın**. Sonraki adım, eğitimin ilk turunu başlatarak modeli eğitmektir. Bir eğitim turu başlattığınızda model, inceleme kümesinden *eğitim kümesi* olarak adlandırılan ek öğeleri rastgele seçer. Bu öğeler (hem denetim kümesinden hem de eğitim kümesinden) size sunulur, böylece her birini "ilgili" veya "ilgili değil" olarak etiketleyebilirsiniz. İlgi, belge meta verilerinin hiçbirini değil, öğedeki içeriği temel alır. Eğitim turunda etiketleme işlemini tamamladıktan sonra model, eğitim kümesindeki öğeleri nasıl etiketlediğinize göre "öğrenir". Bu eğitime bağlı olarak model, gözden geçirme kümesindeki öğeleri işler ve her birine bir tahmin puanı uygular.

   Daha fazla bilgi için bkz. [Tahmine dayalı kodlama modeli eğitme](predictive-coding-train-model.md).

3. **Tahmin puanı filtresini gözden geçirme kümesindeki öğelere uygulayın**. Önceki eğitim adımı tamamlandıktan sonra sonraki adım, modelin "en ilgili" olduğunu belirlediği öğeleri görüntülemek için gözden geçirmedeki öğelere tahmin puanı filtresi uygulamaktır (alternatif olarak, "ilgili olmayan öğeleri görüntülemek için bir tahmin filtresi de kullanabilirsiniz"). Tahmin filtresini uyguladığınızda, filtre uygulanacak tahmin puanları aralığını belirtirsiniz. Tahmin puanları aralığı **0** ile **1** arasında olur ve **0** "ilgili değildir" ve **1** ilgili olur. Genel olarak, tahmin puanı 0 ile **0,5** arasında olan öğeler "ilgili değil" olarak kabul edilir ve **tahmin puanları 0,5** ile **1** arasında olan öğeler ilgili kabul edilir.

   Daha fazla bilgi için bkz. [Gözden geçirme kümesine tahmin filtresi uygulama](predictive-coding-apply-prediction-filter.md).

4. **Model kararlı hale gelene kadar daha fazla eğitim turu gerçekleştirin**. Daha yüksek tahmin doğruluğuna ve daha yüksek geri çağırma hızlarına sahip bir model oluşturmak istiyorsanız ek eğitim turlarını gerçekleştirebilirsiniz. *Geri çağırma oranı* , modelin gerçekten ilgili olan öğeler (eğitim sırasında ilgili olarak işaretlediğiniz öğeler) arasında ilgili olduğu tahmin edilen öğelerin oranını ölçer. Geri çağırma oranı puanı **0** ile **1** arasında değişir. **1'e** yakın bir puan modelin daha ilgili öğeleri tanımlayacağını gösterir. Yeni bir eğitim turunda, yeni bir eğitim kümesindeki ek öğeleri etiketlersiniz. Bu eğitim turunu tamamladıktan sonra model, eğitim kümesindeki en son etiketleme öğelerinizden elde ettiğiniz yeni öğrenime göre güncelleştirilir. Model, gözden geçirme kümesindeki öğeleri yeniden işler ve yeni tahmin puanları uygular. Modeliniz kararlı hale gelene kadar eğitim turlarını gerçekleştirmeye devam edebilirsiniz. En son eğitim turundan sonraki değişim sıklığı %5'in altında olduğunda modelin kararlı olduğu kabul edilir. *Değişim sıklığı* , tahmin puanının eğitim yuvarlamaları arasında değiştiği bir gözden geçirme kümesindeki öğelerin yüzdesi olarak tanımlanır. Tahmine dayalı kodlama panosu, modelin kararlılığını değerlendirmenize yardımcı olan bilgileri ve istatistikleri görüntüler.

5. **Gözden geçirme önceliğini belirlemek üzere öğeleri gözden geçirmek için "son" tahmin puanı filtresini uygulayın**. Tüm eğitim turlarını tamamladıktan ve modeli dengeledikten sonra, son adım, ilgili ve ilgili olmayan öğelerin gözden geçirilmesine öncelik vermek için son tahmin puanını gözden geçirme kümesine uygulamaktır. Bu, 3. adımda gerçekleştirdiğiniz görevle aynıdır, ancak bu noktada model kararlıdır ve daha fazla eğitim turu çalıştırmayı planlamazsınız.
