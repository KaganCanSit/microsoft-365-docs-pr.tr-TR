---
title: Tahmine dayalı kodlama referansı
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
description: ''
ms.openlocfilehash: da8ea6f996735edb91b7191bbcf90df02e134428
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65091489"
---
# <a name="predictive-coding-reference-preview"></a>Tahmine dayalı kodlama başvurusu (önizleme)

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Bu makalede, Microsoft Purview eKeşif'teki (Premium) tahmine dayalı kodlama aracının temel kavramları ve ölçümleri açıklanmaktadır. Makaledeki bölümler alfabetik sırada listelenmiştir.

## <a name="confidence-level"></a>Güvenilirlik düzeyi

Güvenilirlik düzeyi, tahmine dayalı bir kodlama modeli oluşturduğunuzda gelişmiş bir ayardır. Modelin performans ölçümlerinin (örneğin, zenginlik, duyarlık ve geri çekme), modelin inceleme kümesindeki öğelere atadığı tahmin puanlarının gerçek değerlerini temsil eden belirli bir aralıkta (model için tanımlanan hata kenar boşluğu belirlenir) olduğunu tanımlar. Güvenilirlik düzeyi ve hata kenar boşluğu değerleri, denetim kümesine kaç öğenin dahil olduğunu belirlemeye de yardımcı olur. Güvenilirlik düzeyi için varsayılan değer %0,95 veya %95'tir.

## <a name="control-set"></a>Denetim kümesi

Denetim kümesi, tahmine dayalı kodlama modelinin eğitim sürecinde kullanılır. Denetim kümesi, modelin öğelere atadığını tahmin puanlarını eğitim yuvarlamaları sırasında gerçekleştirdiğiniz etiketlemeyle değerlendirmektir. Denetim kümesinin boyutu, gözden geçirme kümesindeki öğelerin sayısına ve model oluşturulurken ayarlanan hata değerlerinin güvenilirlik düzeyine ve kenar boşluğuna bağlıdır. Denetim kümesindeki öğeler hiçbir zaman değişmez ve kullanıcılara tanımlanamaz. Denetim kümesindeki toplam öğe sayısı, eğitim turu için açılır sayfada görüntülenir.

## <a name="control-set-confusion-matrix"></a>Denetim kümesi karışıklık matrisi

Bir eğitim turunu tamamladıktan sonra model, denetim kümesindeki eğitim turu sırasında etiketlediğiniz 10 öğeye bir tahmin puanı atar. Model, bu 10 öğenin tahmin puanını eğitim turu sırasında öğeye atadığınız gerçek etiketle karşılaştırır. Bu karşılaştırmaya bağlı olarak model, modelin tahmin performansını değerlendirmek için aşağıdaki sınıflandırmaları tanımlar:

<br>

****

|Etiket|Model, öğenin ilgili olduğunu tahmin eder|Model öğenin ilgili olmadığını tahmin ediyor|
|---|---|---|
|**İlgili olarak gözden geçiren etiketleri öğesi**|Gerçek pozitif|Hatalı pozitif|
|**Gözden geçiren etiketler öğesi uygun değil**|Hatalı negatif|Gerçek negatif|
|

Bu karşılaştırmalara bağlı olarak, model F puanı, duyarlık ve geri çağırma ölçümleri için değerler ve her biri için hata kenar boşluğu türetir. Matristen gelen karışıklık türlerinin her birinin sayısı, eğitim turu için açılır sayfada görüntülenir.

## <a name="f-score"></a>F puanı

F puanı, duyarlık ve geri çağırma ölçümlerinin puanlarının ağırlıklı ortalamasıdır.  Bu ölçümün puan aralığı **0** ile **1** arasındadır. **1'e** yakın bir puan modelin ilgili öğeleri daha doğru algılayacağını gösterir. F puanı ölçümü model panosunda ve her eğitim turu için açılır sayfada görüntülenir.

## <a name="margin-of-error"></a>Hata kenar boşluğu

Tahmine dayalı kodlama modu oluşturduğunuzda hatanın kenar boşluğu gelişmiş bir ayardır. Denetim kümenizdeki öğelerin rastgele örneklemesinden türetilen performans ölçümlerindeki hata derecesini (örneğin, zenginlik, duyarlık ve geri çağırma) belirtir. Hatanın daha düşük bir kenar boşluğu, modelin performans ölçümlerinin daha küçük bir aralık içinde olmasını sağlamak için daha büyük bir denetim kümesi gerektirir. Hata ve güvenilirlik düzeyinin kenar boşluğu değerleri, denetim kümesine kaç öğenin dahil olduğunu belirlemeye de yardımcı olur. Hata kenar boşluğu için varsayılan değer 0,05 veya %5'tir.

## <a name="model-stability"></a>Model kararlılığı

Model kararlılığı, modelin inceleme kümesindeki bir belgenin ilgili olup olmadığını doğru bir şekilde tahmin etme özelliğini gösterir. Model kararsız olduğunda modelin kararlılığını eklemek için daha fazla eğitim turu gerçekleştirilmesi gerekebilir. Model kararlı olduğunda, başka eğitim turu yapılması gerekmeyebilir. Model panosu, modelin kararlılığının geçerli durumunu gösterir. Model kararlı olduğunda performans ölçümleri güvenilirlik düzeyi ve hata marjı ayarlarıyla eşleşen bir düzeye ulaşmıştır.

## <a name="overturn-rate"></a>Ters devir oranı

Ters çevrilmiş oran, tahmin puanının eğitim yuvarlamaları arasında değiştiği gözden geçirme kümesindeki öğelerin yüzdesidir. Ters dönmüş oranı %5'in altında olduğunda model kararlı olarak kabul edilir. Ters dönüş oranı ölçümü model panosunda ve her eğitim turu için açılır sayfada görüntülenir. İlk eğitim turunun ters dönüş oranı sıfırdır çünkü ters döndürülecek önceki bir tahmin puanı yoktur.

## <a name="precision"></a>Hassasiyet

Duyarlık ölçümü, modelin tahmin edilen ilgili öğeler arasında gerçekten ilgili olan öğelerin oranını ölçer. Bu, denetimdeki öğelerin, etiketin gözden geçiren tarafından ilgili olduğu ve model tarafından uygun olarak tahmin edildiği durumlarda ayarlandığı anlamına gelir. Bu ölçümün puan aralığı **0** ile **1** arasındadır. **1'e** yakın bir puan, modelin daha az ilgili olmayan öğe tanımlayacağını gösterir. Duyarlık ölçümü model panosunda ve her eğitim turu için açılır sayfada görüntülenir.

## <a name="prediction-score"></a>Tahmin puanı

Bu, bir modelin gözden geçirme kümesindeki her belgeye atayabilecekleri puandır. Puan, modelin eğitim turlarından öğrenmesine kıyasla belgenin ilgi düzeyini temel alır. Genel olarak, tahmin puanı 0 ile **0,5** arasında olan öğeler ilgili değildir ve **tahmin puanı 0,5** ile **1** arasında olan öğeler ilgili kabul edilir. Tahmin puanı bir belge meta veri alanında yer alır. Bir tahmin filtresi kullanarak, belirtilen tahmin aralığındaki bir gözden geçirme kümesindeki öğeleri görüntüleyebilirsiniz.

## <a name="recall"></a>Hatırla

Geri çağırma ölçümü, modelin tahmin edilen öğelerin gerçekten ilgili öğeler arasında ilgili olduğu oranını ölçer. Bu, modelin ilgili olduğu tahmin edilen denetim kümesindeki öğelerin de gözden geçiren tarafından ilgili olarak etiketlendiği anlamına gelir. Bu ölçümün puan aralığı **0** ile **1** arasındadır. **1'e** yakın bir puan, modelin ilgili öğelerin daha büyük bir bölümünü tanımlayacağını gösterir. Geri çağırma ölçümü model panosunda ve her eğitim turu için açılır sayfada görüntülenir.

## <a name="review-set"></a>Gözden geçirme kümesi

Gözden geçirme kümesi, tahmine dayalı kodlama modelinin kapsamını sağlar. Gözden geçirme kümesi için yeni bir model oluşturduğunuzda, denetim kümesi ve eğitim kümeleri için öğeler gözden geçirme kümesinden seçilir. Model tahmin puanları atadığında, bu puanları gözden geçirmedeki öğeleri atar. Tahmine dayalı bir kodlama modeli oluşturmadan önce tüm öğeleri gözden geçirme kümesine eklemeniz gerekir. Model oluşturduktan sonra öğe eklerseniz, bu öğelere tahmin puanı atanmayacaktır.

## <a name="richness"></a>Zenginlik

Zenginlik ölçümü, modelin ilgili olarak tahminde bulunan gözden geçirme kümesi öğelerinin yüzdesini ölçer. Bu ölçümün puan aralığı **0** ile **1** arasındadır. Zenginlik ölçümü model panosunda görüntülenir.

## <a name="sampled-items"></a>Örneklenen öğeler

*Örneklenen öğeler* terimi, tahmine dayalı bir kodlama modeli oluşturduğunuzda seçilen ve denetim kümesiyle ilişkili bir gözden geçirme kümesindeki (metin içeren) öğelerin rastgele örneğine başvurudur. Her eğitim turu için rastgele bir öğe örneği de seçilir. Bir modelin denetim kümesi için seçilen öğeler hiçbir zaman aynı model için bir eğitim kümesine dahil olmaz. Tersi de geçerlidir: eğitim kümesi öğeleri hiçbir zaman denetim kümesine dahil değildir.

## <a name="training-set"></a>Eğitim kümesi

Model, gözden geçirme kümesindeki öğeleri rastgele seçer ve bunları bir eğitim kümesine ekler. Eğitim turu sırasında, eğitim kümesindeki öğeler (denetim kümesindeki öğelere ek olarak) size sunulur, böylece her birini "ilgili" veya "ilgili değil" olarak etiketleyebilirsiniz. Bu etiketleme veya "eğitim" işlemi, modelin incelemedeki hangi öğelerin ilgili olup olmadığını tahmin etmeyi öğrenmesine yardımcı olur. Her eğitim turu gerçekleştirdiğinizde model gözden geçirmeden daha fazla öğe seçer ve bunları bu eğitim turu için eğitim kümesine ekler. Denetim kümesindeki öğeler hiçbir zaman eğitim kümesi için seçilmez.
