---
title: Advanced eDiscovery'da tahmine dayalı kodlama modeli Advanced eDiscovery
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
description: Advanced eDiscovery'te tahmine dayalı kodlama modelinin nasıl oluşturul Advanced eDiscovery. Bu, bir gözden geçirme kümesinde ilgili ve ilgili Advanced eDiscovery olmayan içerikleri tanımlamanıza yardımcı olmak için, makine öğrenme özelliklerini kullanmanın ilk adımıdır.
ms.openlocfilehash: 4366c5779aaca6973f5a2c0cc526086d0742d069
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62985699"
---
# <a name="create-a-predictive-coding-model-preview"></a>Tahmine dayalı kodlama modeli (önizleme) oluşturma

Advanced eDiscovery'ta tahmine dayalı kodlamanın makine öğrenme özelliklerini kullanmanın ilk adımı, öngörülebilir bir kodlama modeli oluşturmaktır. Modeli oluşturdukktan sonra, bir gözden geçirme kümesinde ilgili ve ilgili olmayan içerikleri belirlemesi için eğitebilirsiniz.

Tahmine dayalı kodlama iş akışını gözden geçirmek için bkz[. Veri kodlarında tahmine dayalı Advanced eDiscovery](predictive-coding-overview.md#the-predictive-coding-workflow)

## <a name="before-you-create-a-model"></a>Model oluşturmadan önce

- Tahmini kodlama modeli oluşturmak için, gözden geçirme kümesinde en az 2.000 öğe olması gerekir.

- Modeli oluşturmadan önce tüm koleksiyonları gözden geçirme kümesine kaydetmeye emin olun. Model oluşturulduktan sonra gözden geçirme kümesine eklenen öğeler işlenmez ve model tarafından oluşturulan bir tahmin puanı atanır.

- Gözden geçirme kümesinde metin olmayan hiçbir öğe model tarafından işlenmez veya tahmin puanı atanamaz. Metin bulunan öğeler denetim kümesine veya eğitim kümesine dahil edilir.

## <a name="create-a-model"></a>Model oluşturma

1. Görünüm Microsoft 365 uyumluluk merkezi bir büyük/Advanced eDiscovery sonra Gözden Geçir **kümeleri sekmesini** seçin.

2. Gözden geçirme kümesi açın ve ardından **AnalyticsManive** >  **coding (önizleme) öğesini tıklatın**.

   ![Gözden Geçirme kümesinde Çözümle açılan menüsüne tıklar ve Tahmine Dayalı kodlama sayfasına gider.](..\media\ManagePredictiveCoding.png)

3. Tahmine **dayalı kodlama modelleri (önizleme) sayfasında** Yeni **model'e tıklayın**.

4. Uçarak çıkış sayfasında, model için bir ad ve isteğe bağlı bir açıklama yazın.

5. İsteğe bağlı olarak, hatanın güven düzeyi ve kenar  boşluğuyla ilgili gelişmiş ayarları yapılandırabilirsiniz (uç sayfada Gelişmiş seçenekler'e tıklayarak). Bu ayarlar, denetim kümesine dahil edilen öğe sayısını etkiler. Denetim *kümesi,* eğitim sürecinde, model tarafından öğelere atadığınız tahmin puanlarını, eğitim yuvarlaları sırasında gerçekleştirdığınız etiketle değerlendirmek için kullanılır. Kuruluşta belge incelemesi için güven düzeyi ve hata kenar boşluğu yönergeleri varsa, bunları uygun kutularda belirtin. Aksi takdirde, varsayılan ayarları kullanın.

6. Modeli **oluşturmak için** Kaydet'e tıklayın.

   Sistemin modelinizi hazırlaması birkaç dakika sürer. Hazır olduktan sonra, ilk eğitim turlarını gerçekleştirin.

## <a name="what-happens-after-you-create-a-model"></a>Bir model oluşturdukta ne olur?

Siz bir model oluşturdukta, modelin oluşturulması ve hazırlığı sırasında arka planda aşağıdaki şeyler gerçekleşir:

- Sistem, denetim kümesi için öğelerin sayısını hesaplar. Bu boyut, gözden geçirme kümesinde yer alan öğelerin sayısıyla güven düzeyiyle hata kenar boşluğu ayarlarını temel alır. Denetim kümesi öğeleri rastgele seçilir ve denetim kümesi öğeleri olarak ayarlanır. Sistem, eğitimin ilk turunda denetim kümesinden 10 öğe içerir.

- Sistem, ilk eğitim turu için eğitim kümesine dahil etmek için gözden geçirme kümesinden rastgele 40 öğe seçer. Bu nedenle, eğitimin ilk turu etiketle ilgili 50 öğe içerir: eğitim kümesinden 40 öğe ve denetim kümesinden 10 öğe.

## <a name="next-steps"></a>Sonraki adımlar

Gözden geçirme kümesi için bir model oluşturduktaktan sonraki adım, araştırmanıza uygun içeriği tanımlamak için modele "ders vermek" için eğitim yuvarlar. Daha fazla bilgi için bkz [. Tahmine dayalı bir kodlama modelini eğitin](predictive-coding-train-model.md).
