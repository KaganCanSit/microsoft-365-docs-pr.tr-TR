---
title: eBulma'da tahmine dayalı kodlama modeli eğitin (Premium)
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
ms.openlocfilehash: 3335e437a659eab984943adda31abdb344908c1c
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/20/2022
ms.locfileid: "64997658"
---
# <a name="train-a-predictive-coding-model-preview"></a>Tahmine dayalı kodlama modeli eğit (önizleme)

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Microsoft Purview eKeşif'te (Premium) tahmine dayalı bir kodlama modeli oluşturduktan sonra, sonraki adım modeli inceleme kümenizdeki ilgili ve ilgili olmayan içerik konusunda eğitmek için ilk eğitim turunu gerçekleştirmektir. Eğitimin ilk turunu tamamladıktan sonra modelin ilgili ve ilgili olmayan içeriği tahmin etme becerisini geliştirmek için sonraki eğitim turlarını gerçekleştirebilirsiniz.

Tahmine dayalı kodlama iş akışını gözden geçirmek için bkz. [eBulma'da tahmine dayalı kodlama hakkında bilgi edinme (Premium)](predictive-coding-overview.md#the-predictive-coding-workflow)

## <a name="before-you-train-a-model"></a>Modeli eğitmeden önce

- Eğitim turu sırasında, belgedeki içeriğin ilgisine bağlı olarak öğeleri **İlgili** veya **İlgili değil** olarak etiketleyebilirsiniz. Kararınızı meta veri alanlarındaki değerlere dayandırmayın. Örneğin, e-posta iletileri veya Teams konuşmaları için etiketleme kararınızı ileti katılımcılarına dayandırmayın.

## <a name="train-a-model-for-the-first-time"></a>Modeli ilk kez eğitin

1. Microsoft Purview uyumluluk portalında bir eBulma (Premium) servis talebi açın ve ardından **Kümeleri gözden geçir** sekmesini seçin.

2. Bir gözden geçirme kümesi açın ve **ardından Analytics** >  **Tahmine dayalı kodlamayı yönet (önizleme)'** ye tıklayın.

3. **Tahmine dayalı kodlama modelleri (önizleme)** sayfasında eğitmek istediğiniz modeli seçin.

4. **Genel Bakış** sekmesinde, 1. **Tur'un** altında **Sonraki eğitim turunu başlat'a** tıklayın.

   **Eğitim** sekmesi görüntülenir ve etiketlemeniz için 50 öğe içerir.

5. Her belgeyi gözden geçirin ve ardından okuma bölmesinin alt kısmındaki **İlgili** veya **İlgili değil** düğmesini seçerek etiketleyin.

   ![Her belgeyi ilgili olarak etiketle veya ilgili değil olarak etiketle.](..\media\TrainModel1.png)

6. 50 öğenin tümünü etiketledikten sonra **Son'a** tıklayın.

    Sistemin etiketlemenizden "öğrenmesi" ve modeli güncelleştirmesi birkaç dakika sürer. Bu işlem tamamlandığında, **Tahmine dayalı kodlama modelleri (önizleme)** sayfasında model için **Hazır** durumu görüntülenir.

## <a name="perform-additional-training-rounds"></a>Ek eğitim yuvarlamaları gerçekleştirme

Eğitimin ilk turunu gerçekleştirdikten sonra, önceki bölümdeki adımları izleyerek sonraki eğitim yuvarlamalarını gerçekleştirebilirsiniz. Tek fark, **modele Genel Bakış** sekmesinde güncelleştirilecek eğitim turunun sayısıdır. Örneğin, ilk eğitim turunu gerçekleştirdikten sonra, eğitimin ikinci **turunu başlatmak için Sonraki eğitim turunu başlat'a** tıklayabilirsiniz. Ve böyle devam edin.

Her eğitim turu (hem devam eden hem de tamamlananlar) modelin **Eğitim** sekmesinde görüntülenir. Bir eğitim turu seçtiğinizde, yuvarlakla ilgili bilgi ve ölçümleri içeren bir açılır sayfa görüntülenir.

## <a name="what-happens-after-you-perform-a-training-round"></a>Eğitim turu gerçekleştirdikten sonra ne olur?

İlk eğitim turunu gerçekleştirdikten sonra, aşağıdaki işlemleri yapan bir iş başlatılır:

- Eğitim kümesindeki 40 öğeyi nasıl etiketlediğinize bağlı olarak, model etiketlemenizden öğrenir ve daha doğru olmak için kendisini güncelleştirir.

- Model daha sonra tüm gözden geçirme kümesindeki her öğeyi işler ve **0** (ilgili değil) ile **1** (ilgili) arasında bir tahmin puanı atar.

- Model, eğitim turu sırasında etiketlediğiniz denetim kümesindeki 10 öğeye bir tahmin puanı atar. Model, bu 10 öğenin tahmin puanını eğitim turu sırasında öğeye atadığınız gerçek etiketle karşılaştırır. Bu karşılaştırmaya bağlı olarak model, modelin tahmin performansını değerlendirmek için aşağıdaki sınıflandırmayı ( *Denetim kümesi karışıklık matrisi* olarak adlandırılır) tanımlar:

  <br>

  ****

  |Etiket|Model, öğenin ilgili olduğunu tahmin eder|Model öğenin ilgili olmadığını tahmin ediyor|
  |---|---|---|
  |**İlgili olarak gözden geçiren etiketleri öğesi**|Gerçek pozitif|Hatalı pozitif|
  |**Gözden geçiren etiketler öğesi uygun değil**|Hatalı negatif|Gerçek negatif|
  |

  Bu karşılaştırmalara bağlı olarak, model F puanı, duyarlık ve geri çağırma ölçümleri için değerler ve her biri için hata kenar boşluğu türetir. Bu model performans ölçümlerinin puanları, eğitim turu için açılır sayfada görüntülenir. Bu ölçümlerin açıklaması için bkz. [Tahmine dayalı kodlama başvurusu](predictive-coding-reference.md).

- Son olarak model, sonraki eğitim turu için kullanılacak sonraki 50 öğeyi belirler. Bu kez model, denetim kümesinden 20 öğe ve gözden geçirme kümesinden 30 yeni öğe seçebilir ve bunları bir sonraki tur için eğitim kümesi olarak belirleyebilir. Sonraki eğitim turu için örnekleme tekdüzen olarak örneklenmez. Model, tahminin belirsiz olduğu öğeleri seçmek için gözden geçirme kümesindeki öğelerin örnekleme seçimini iyileştirir ve bu da tahmin puanının 0,5 aralığında olduğu anlamına gelir. Bu işlem *taraflı seçim* olarak bilinir.

### <a name="what-happens-after-you-perform-subsequent-training-rounds"></a>Sonraki eğitim turlarını gerçekleştirdikten sonra ne olur?

Sonraki eğitim turlarını gerçekleştirdikten sonra (ilk eğitim turundan sonra), model aşağıdaki işlemleri yapar:

- Model, bu eğitim turunda eğitim kümesine uyguladığınız etiketlere göre güncelleştirilir.

- Sistem, modelin denetim kümesindeki öğelerdeki tahmin puanını değerlendirir ve puanın denetim kümesindeki öğeleri nasıl etiketlediğinizle uyumlu olup olmadığını denetler. Değerlendirme, tüm eğitim yuvarlamaları için denetim kümesindeki tüm etiketli öğelerde gerçekleştirilir. Bu değerlendirmenin sonuçları, modelin **Genel Bakış** sekmesindeki panoya eklenir.

- Güncelleştirilmiş model, gözden geçirme kümesindeki her öğeyi yeniden işler ve her öğeye güncelleştirilmiş bir tahmin puanı atar.

## <a name="next-steps"></a>Sonraki adımlar

İlk eğitim turunu gerçekleştirdikten sonra daha fazla eğitim turu gerçekleştirebilir veya modelin tahmin puanı filtresini gözden geçirme kümesine uygulayarak modelin ilgili olarak tahminde bulunduğu veya ilgili olmadığı öğeleri görüntüleyebilirsiniz. Daha fazla bilgi için bkz. [Gözden geçirme kümesine tahmin puanı filtresi uygulama](predictive-coding-apply-prediction-filter.md).
