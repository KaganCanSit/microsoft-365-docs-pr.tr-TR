---
title: eBulma'da tahmine dayalı kodlama modeli oluşturma (Premium)
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
description: eBulma'da (Premium) tahmine dayalı kodlama modeli oluşturmayı öğrenin. Bu, bir inceleme kümesindeki ilgili ve ilgili olmayan içeriği belirlemenize yardımcı olmak için eBulma(Premium) içindeki makine öğrenmesi özelliklerini kullanmanın ilk adımıdır.
ms.openlocfilehash: f5636defbd4bc004a4732ff1d956f8b879daea2d
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/20/2022
ms.locfileid: "64994050"
---
# <a name="create-a-predictive-coding-model-preview"></a>Tahmine dayalı kodlama modeli oluşturma (önizleme)

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

eBulma'da (Premium) tahmine dayalı kodlamanın makine öğrenmesi özelliklerini kullanmanın ilk adımı, tahmine dayalı bir kodlama modeli oluşturmaktır. Modeli oluşturduktan sonra, bir inceleme kümesindeki ilgili ve ilgili olmayan içeriği tanımlamayı eğitebilirsiniz.

Tahmine dayalı kodlama iş akışını gözden geçirmek için bkz. [eBulma'da tahmine dayalı kodlama hakkında bilgi edinme (Premium)](predictive-coding-overview.md#the-predictive-coding-workflow)

## <a name="before-you-create-a-model"></a>Model oluşturmadan önce

- Tahmine dayalı kodlama modeli oluşturmak için bir inceleme kümesinde en az 2.000 öğe olmalıdır.

- Model oluşturmadan önce tüm koleksiyonları gözden geçirme kümesine işlemeyi unutmayın. Model oluşturulduktan sonra bir gözden geçirme kümesine eklenen öğeler işlenmez ve model tarafından oluşturulan bir tahmin puanı atanır.

- Gözden geçirme kümesindeki metin içermeyen öğeler model tarafından işlenmez veya bir tahmin puanı atanamaz. Metin içeren öğeler denetim kümesine veya eğitim kümesine eklenir.

## <a name="create-a-model"></a>Model oluşturma

1. Microsoft Purview uyumluluk portalında bir eBulma (Premium) servis talebi açın ve ardından **Kümeleri gözden geçir** sekmesini seçin.

2. Bir gözden geçirme kümesi açın ve **ardından Analytics** >  **Tahmine dayalı kodlamayı yönet (önizleme)'** ye tıklayın.

   ![Tahmine dayalı kodlama sayfasına gitmek için gözden geçirme kümesindeki Çözümle açılan menüsüne tıklayın.](..\media\ManagePredictiveCoding.png)

3. **Tahmine dayalı kodlama modelleri (önizleme)** sayfasında **Yeni model'e** tıklayın.

4. Açılır sayfada model için bir ad ve isteğe bağlı bir açıklama yazın.

5. İsteğe bağlı olarak, hatanın güvenilirlik düzeyi ve kenar boşluğuyla ilgili gelişmiş ayarları yapılandırabilirsiniz (açılır sayfada **Gelişmiş seçenekler'e** tıklayarak). Bu ayarlar, denetim kümesine dahil edilen öğelerin sayısını etkiler. *Denetim kümesi*, modelin eğitim yuvarlamaları sırasında gerçekleştirdiğiniz etiketlemeyle öğelere atadığını tahmin puanlarını değerlendirmek için eğitim işlemi sırasında kullanılır. Kuruluşunuzda belge gözden geçirme için güvenilirlik düzeyi ve hata marjı hakkında yönergeler varsa, bunları uygun kutularda belirtin. Aksi takdirde varsayılan ayarları kullanın.

6. Modeli oluşturmak için **Kaydet'e** tıklayın.

   Sistemin modelinizi hazırlaması birkaç dakika sürer. Hazır olduktan sonra ilk eğitim turunu gerçekleştirebilirsiniz.

## <a name="what-happens-after-you-create-a-model"></a>Model oluşturduktan sonra ne olur?

Modeli oluşturduktan sonra, modelin oluşturulması ve hazırlanması sırasında arka planda aşağıdaki işlemler gerçekleşir:

- Sistem, denetim kümesi için öğe sayısını hesaplar. Bu boyut, gözden geçirme kümesindeki öğelerin sayısına, güvenilirlik düzeyine ve hatanın kenar boşluğuna yönelik ayarları temel alır. Denetim kümesi öğeleri rastgele seçilir ve denetim kümesi öğeleri olarak belirlenir. Sistem, eğitimin ilk turunda denetim kümesinden 10 öğe içerir.

- Sistem, ilk eğitim turu için eğitim kümesine dahil edilecek gözden geçirme kümesinden rastgele 40 öğe seçer. Bu nedenle, eğitimin ilk turu etiketleme için 50 öğe içerir: eğitim kümesinden 40 öğe ve denetim kümesinden 10 öğe.

## <a name="next-steps"></a>Sonraki adımlar

Bir gözden geçirme kümesi için model oluşturduktan sonra, sonraki adım araştırmanızla ilgili içeriği tanımlamak üzere modeli "öğretmek" için eğitim yuvarlamaları gerçekleştirmektir. Daha fazla bilgi için bkz. [Tahmine dayalı kodlama modeli eğitme](predictive-coding-train-model.md).
