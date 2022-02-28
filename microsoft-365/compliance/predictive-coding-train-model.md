---
title: Advanced eDiscovery'da tahmine dayalı kodlama modelini Advanced eDiscovery
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
description: ''
ms.openlocfilehash: b5f1a958696dad84ac2bedec8f1ab7d23dfa6428
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62988185"
---
# <a name="train-a-predictive-coding-model-preview"></a>Tahmine dayalı kodlama modelini eğit (önizleme)

Advanced eDiscovery'da tahmine dayalı bir kodlama modeli oluşturdukktan sonra, sonraki adım modeli gözden geçirme kümenizin ilgili ve ilgili olmayan içerikleri hakkında eğitmek için ilk eğitim turını gerçekleştirmektir. Eğitimin ilk turda tamamlandıktan sonra, modelin ilgili ve ilgili olmayan içeriği tahmin etme becerisini geliştirmek için sonraki eğitim turlarını gerçekleştirebilirsiniz.

Tahmine dayalı kodlama iş akışını gözden geçirmek için bkz[. Veri kodlarında tahmine dayalı Advanced eDiscovery](predictive-coding-overview.md#the-predictive-coding-workflow)

## <a name="before-you-train-a-model"></a>Modeli eğitmeden önce

- Eğitim turu sırasında, öğeleri belgedeki **içeriğin uygun** **olduğunu temel** alarak Uygun veya Uygun değil olarak etiket ekleyin. Meta veri alanlarındaki değerlere karar verme. Örneğin, e-posta iletileri Teams konuşmalar için, etiket kararınızı ileti katılımcılarına temel vermez.

## <a name="train-a-model-for-the-first-time"></a>Bir modeli ilk kez eğitin

1. Görünüm Microsoft 365 uyumluluk merkezi bir büyük/Advanced eDiscovery sonra Gözden Geçir **kümeleri sekmesini** seçin.

2. Gözden geçirme kümesi açın ve ardından **AnalyticsManive** >  **coding (önizleme) öğesini tıklatın**.

3. Tahmine **dayalı kodlama modelleri (önizleme) sayfasında** , eğitmek istediğiniz modeli seçin.

4. Genel Bakış **sekmesindeki** **1. Tur'ın altında** Sonraki eğitim **turu başlat'a tıklayın**.

   Eğitim **sekmesi** görüntülenir ve etiketlemek için size 50 öğe içerir.

5. Her belgeyi gözden geçirin **ve ardından** etiketlemek **için okuma** bölmesinin en altındaki Uygun veya İlgili değil düğmesini seçin.

   ![Her belgeyi uygun veya uygun değil olarak etiketle.](..\media\TrainModel1.png)

6. 50 öğenin hepsini etiketledikten sonra, Son'a **tıklayın**.

    Sistemin etiketlemeden "öğrenmesi" ve modeli güncelleştirmesi birkaç dakika sürer. Bu işlem tamamlandığında, Tahmine Dayalı kodlama modelleri  (önizleme) sayfasında model **için Hazır durumu** görüntülenir.

## <a name="perform-additional-training-rounds"></a>Ek eğitim yuvarlaları gerçekleştirme

Eğitimin ilk turlarını gerçekleştirdikten sonra, önceki bölümde yer alan adımları takiperek sonraki eğitim turlarını gerçekleştirebilirsiniz. Tek fark, modele Genel Bakış sekmesindeki eğitim turlarının sayısı **güncelleştirilecek** . Örneğin, ilk eğitim turlarını gerçekleştirdikten sonra Sonraki eğitim turlarını **başlat'a tıklar** ve eğitimin ikinci turda başlayabilirsiniz. Böyle devam.

Her eğitim turu (hem devam eden hem de tamamlandı olanlar) modelin **Eğitim** sekmesinde görüntülenir. Bir eğitim turu seçin; yuvarlak için bilgiler ve ölçümler ile bir çıkış sayfası görüntülenir.

## <a name="what-happens-after-you-perform-a-training-round"></a>Bir eğitim turu gerçekleştirdikten sonra ne olur?

İlk eğitim turlarını gerçekleştirdikten sonra, aşağıdaki işleri yapacak bir iş başlatıldı:

- Eğitim kümesinde 40 öğeyi nasıl etiketle ilgili olduğunu temel alarak, model etiketlemenizi öğrenir ve daha doğru olması için kendisini günceller.

- Daha sonra model, tüm gözden geçirme kümesinde her öğeyi işler ve **0** (ilgili değil) ile **1** (uygun) arasında bir tahmin puanı atar.

- Model, denetim kümesinde eğitim turu sırasında etiketley istediğiniz 10 öğeye bir tahmin puanı atar. Model, bu 10 öğenin tahmin puanlarını, eğitim turu sırasında öğeye atadığı gerçek etiketle karşıtır. Bu karşılaştırmaya dayanarak, model modelin tahmin performansını değerlendirmek için aşağıdaki sınıflandırmayı (Denetim kümesi *karışıklığı* matrisi olarak adlandırılan) tanımlar:

  <br>

  ****

  |Etiket|Model, öğenin uygun olduğunu öngörür|Model, öğenin uygun olmadığını öngörür|
  |---|---|---|
  |**Gözden geçiren öğeyi uygun olarak etiketler**|Doğru pozitif|Hatalı pozitif sonuç|
  |**Gözden geçiren öğeyi uygun değil olarak etiketler**|Yanlış negatif|Doğru negatif|
  |

  Bu karşılaştırmalara bağlı olarak, model F-puanı, duyarlılık ve geri çekme ölçümleri için değerleri ve her birinin hata marjını türetir. Bu model performans ölçümlerinin puanları, eğitim dönüş sayfasının bir çıkış sayfasında görüntülenir. Bu ölçümlerin açıklaması için bkz. [Tahmine dayalı kodlama başvurusu](predictive-coding-reference.md).

- Son olarak, model sonraki eğitim turu için kullanılacak sonraki 50 öğeyi belirler. Bu kez model, denetim kümesinden 20 öğe ve gözden geçirme kümesinden 30 yeni öğe seçerek sonraki tur için eğitim kümesi olarak bu öğeleri atıyor olabilir. Sonraki eğitim turu için örnekleme, tek tip olarak örneklanmaz. Model, gözden geçirme kümesinden öğe örnekleme seçimini, tahminin belirsiz olduğu öğeleri seçecek şekilde en iyi duruma gelir; bu da, tahmin puanının 0,5 aralığında olduğu anlamına gelir. Bu işlem, *sapmalı seçim olarak bilinir*.

### <a name="what-happens-after-you-perform-subsequent-training-rounds"></a>Sonraki eğitim turlarını gerçekleştirdikten sonra ne olur?

Sonraki eğitim turlarını gerçekleştirdikten sonra (ilk eğitim turdan sonra), model şunları yapar:

- Model, bu eğitim turunda eğitim kümesine uyguladık etiketleri temel alarak güncelleştirilir.

- Sistem, denetim kümesinde yer alan öğeler üzerinde modelin tahmin puanını değerlendirir ve puanın denetim kümesinde öğeleri etiketlenene göre hizalı olup olmadığını kontrol edin. Değerlendirme, tüm eğitim turlarında denetim kümesinden etiketlenmiş tüm öğeler üzerinde gerçekleştirilir. Bu değerlendirmenin sonuçları, modelin Genel Bakış **sekmesindeki** panoya dahil edildi.

- Güncelleştirilmiş model, gözden geçirme kümesinde her öğeyi yeniden inceler ve her öğeye güncelleştirilmiş bir tahmin puanı atar.

## <a name="next-steps"></a>Sonraki adımlar

İlk eğitim turünü gerçekleştirdikten sonra, daha fazla eğitim turu gerçekleştirebilir veya modelin uygun veya ilgili değil olarak tahmin edilen öğeleri görüntülemek üzere, modelin tahmin puanı filtresini gözden geçirme kümesine uygulayabilirsiniz. Daha fazla bilgi için bkz [. Gözden geçirme kümesine tahmin puanı filtresi uygulama](predictive-coding-apply-prediction-filter.md).
