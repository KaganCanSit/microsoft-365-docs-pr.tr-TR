---
title: Advanced eDiscovery için tahmine dayalı kodlama modülü (önizleme)
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
description: Advanced eDiscovery'daki yeni tahmine dayalı kodlama modülü, inceleme kümesinde öğeleri çözümlemek için makine öğrenmesini kullanır ve olay veya araştırmanız için hangi öğelerin gerekli olduğunu tahmin eder.
ms.openlocfilehash: 60f0fc2f53c8bfbde2a4a1d5cccb4eb678f7c33e
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62985165"
---
# <a name="learn-about-predictive-coding-in-advanced-ediscovery-preview"></a>Advanced eDiscovery (önizleme) içinde tahmine dayalı kodlama hakkında bilgi

Advanced eDiscovery'daki tahmine dayalı kodlama modülü, gözden geçir edilecek içerik miktarını azaltmanıza yardımcı olmak için akıllı makine öğrenme özelliklerini kullanır. Tahmine dayalı kodlama, büyük hacimli büyük hacimli olay içeriğini gözden geçirme için önceliklerini alacağız ve uygun bir öğe kümesine azaltmanıza yardımcı olur. Bu, gözden geçirme kümesinde en uygun öğelerin gözden geçirme önceliklerini belirlemeye yardımcı olacak kendi tahmine dayalı kodlama modellerinizi oluşturarak ve bu modelleri eğiterek  başarabilirsiniz.

Tahmine dayalı kodlama modülü, gözden geçirme kümesi içinde modeli yönetmenin karmaşıklığını kolaylaştırmaya ve Advanced eDiscovery'te makine öğrenme özellikleriyle daha hızlı çalışmaya başlayabilmek için modelinizi eğitime iteratif bir yaklaşım sağlamak için tasarlanmıştır. Çalışmaya başlamak için, ilgili veya ilgili değil en az 50 öğe olarak etiketlenmiş bir model oluşturabilirsiniz. Sistem, tahmin puanlarını gözden geçirme kümesinde her öğeye uygulamak için bu eğitimi kullanır. Bu, öğeleri önce en uygun (veya ilgili olmayan) öğeleri gözden geçirmenizi sağlayan tahmin puanına göre filtrelemenizi sağlar. Daha yüksek ücret oranına ve geri çekme oranlarına sahip modelleri eğitmek için, sonraki eğitim turlarında öğeleri model model modellerine kadar etiketlemeye devam edersiniz.  

## <a name="the-predictive-coding-workflow"></a>Tahmine dayalı kodlama iş akışı

Burada, her adıma tahmine dayalı kodlama iş akışının genel bir bakış ve açıklaması ve açıkları ve ve açıklamaları ve ve bunların bir özeti yer vardır. Tahmine dayalı kodlama işleminin kavramları ve terminolojisi hakkında daha ayrıntılı bir açıklama için bkz. [Tahmine dayalı kodlama başvurusu](predictive-coding-reference.md).

![Tahmine dayalı kodlama iş akışı.](..\media\PredictiveCodingWorkflow.png)

1. **Gözden geçirme kümesinde yeni bir tahmine dayalı kodlama modeli oluşturun**. İlk adım, gözden geçirme kümesinde yeni bir tahmine dayalı kodlama modeli oluşturmaktır. Bir model oluşturmak için gözden geçirme kümesinde en az 2.000 öğe olması gerekir. Siz modeli oluşturduklardan sonra, sistem denetim kümesi olarak kullanmak istediğiniz öğe sayısını *belirler*. Denetim kümesi, eğitim sürecinde, model tarafından öğelere atadığınız tahmin puanlarını, eğitim yuvarlaları sırasında gerçekleştirdığınız etiketle değerlendirmek için kullanılır. Denetim kümesi boyutu, gözden geçirme kümesinde yer alan öğelerin sayısına, modeli oluştururken ayarlanmış hata değerlerinin güven düzeyine ve kenar boşluğu değerlerine göre oluşturulur. Denetim kümesinde yer alan öğeler hiçbir zaman değişmez ve kullanıcılara tanınmaz.

   Daha fazla bilgi için bkz [. Tahmine dayalı kodlama modeli oluşturma](predictive-coding-create-model.md).

2. **Öğeleri ilgili veya ilgili değil olarak etiketleerek ilk eğitim turlarını tamamlama**. Sonraki adım, eğitimin ilk turını başlatarak modeli eğitmektir. Bir eğitim turu başlatabilirsiniz, model gözden geçirme kümesinden eğitim kümesi adı verilen ek öğeleri *rastgele seçer*. Bu öğeler (hem denetim kümesinden hem de eğitim kümesinden) size sunu, böylece her birini "ilgili" veya "ilgili değil" olarak etiketlebilirsiniz. İlgi düzeyi, belge meta verilerini değil öğenin içeriğine dayalıdır. Eğitim turunda etiketleme işlemini tamamladikten sonra, model, eğitim kümesinde öğeleri nasıl etiketle ilgili olduğunu temel alarak "öğrenir". Bu eğitim temel alarak, model gözden geçirme kümesinde öğeleri işler ve her bir öğeye bir tahmin puanı uygulamaz.

   Daha fazla bilgi için bkz [. Tahmine dayalı bir kodlama modelini eğitin](predictive-coding-train-model.md).

3. **Gözden geçirme kümesinde öğelere tahmin puanı filtresini uygulama**. Önceki eğitim adımı tamamlandıktan sonra, sonraki adım, modelin "en uygun" olarak belirlediği öğeleri görüntülemek üzere gözden geçirmedeki öğelere tahmin puanı filtresi uygulamaktır (alternatif olarak, "uygun değil" olan öğeleri görüntülemek için de tahmin filtresi kullanabilirsiniz). Tahmin filtresini uygulamak için, filtre uygulamak için bir tahmin puanları aralığı belirtirsiniz. Tahmin puanları aralığı **0** ile **1** arasında olur ve **0** "uygun değil" ve **1** uygun olur. Genelde, tahmin puanları **0 ile** **0,5** arasında olan öğeler "uygun değildir" kabul edilir ve tahmin puanları **0,5** ile **1** arasında olan öğeler uygun kabul edilir.

   Daha fazla bilgi için bkz [. Gözden geçirme kümesine tahmin filtresi uygulama](predictive-coding-apply-prediction-filter.md).

4. **Model çalışma saatlerine kadar daha fazla eğitim turu gerçekleştirin**. Tahminde daha yüksek doğrulukta ve artmış geri çekme oranlarına sahip bir model oluşturmak için ek eğitim yuvarlaları gerçekleştirebilirsiniz. *Geri çekme* oranı, modelin tahmin edilen öğelerin gerçekten ilgili öğeler (eğitim sırasında ilgili olarak işaretledikleri) arasında uygun olduğunu ölçür. Geri çekme oranı puanı **0 ile** **1 arasında değişiyor**. **1'e yakın bir** puan, modelin daha ilgili öğeleri belirleyeceklerini gösterir. Yeni bir eğitim turunda, yeni eğitim kümesine ek öğeleri etiketlirsiniz. Bu eğitim turlarını tamamlandıktan sonra model, eğitim kümesinde en son etiket öğelerinizi temel alan yeni öğrenme temel alarak güncelleştirilir. Model, gözden geçirme kümesinde öğeleri yeniden işler ve yeni tahmin puanlarını uygulanır. Modeliniz devam edene kadar eğitim turları gerçekleştirmeye devam edersiniz. En son eğitim turundan sonra churn oranı %5'in altında olduğunda bir model geri alınmaktadır. *Churn hızı* , eğitim yuvarlaları arasında tahmin puanının değiştmiş olduğu bir gözden geçirme kümesinde öğelerin yüzdesi olarak tanımlanır. Tahmine dayalı kodlama panosu, bir modelin kararlılığını değerlendirmeye yardımcı olacak bilgileri ve istatistikleri görüntüler.

5. **Gözden geçirme önceliklerini belirlemek için ayarlanmış öğeleri gözden geçirmek için "son" tahmin puanı filtresini uygulama**. Tüm eğitim turlarını tamamlar ve modeli tamamlarken, son adım, ilgili ve ilgili olmayan öğelerin gözden geçirme önceliklerini belirlemek için gözden geçirme kümesine son tahmin puanını uygulamaktır. Bu, 3. adımda gerçekleştir planla aynı görevdir, ancak bu noktada model kararlıdır ve daha fazla eğitim turu çalıştırmayı planlayamıyoruz.
