---
title: Tahmine dayalı kodlama başvurusu
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
ms.openlocfilehash: ff681793a86d9953088c2c4da65553e1d2c54d22
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62985697"
---
# <a name="predictive-coding-reference-preview"></a>Tahmine dayalı kodlama başvurusu (önizleme)

Bu makalede, Advanced eDiscovery'de tahmine dayalı kodlama aracının temel kavramları ve Advanced eDiscovery. Makalenin bölümleri alfabetik sırada listelenmiştir.

## <a name="confidence-level"></a>Güven düzeyi

Tahmine dayalı bir kodlama modeli seniz, güven düzeyi gelişmiş bir ayardır. Modelin performans ölçümlerinin (örneğin, zenginlik, duyarlılık ve geri çekme) belirtilen bir aralığın (model için tanımlanan hata kenar boşluğuna göre), tahmindeki doğru değerleri temsil eden ve tahminin gözden geçirme kümesinde yer alan öğelere atadığınız modeli puanladığı değerini tanımlar. Hatanın güven düzeyi ve kenar boşluğu değerleri de denetim kümesine kaç öğenin dahil olduğunu belirlemeye yardımcı olur. Güven düzeyi için varsayılan değer 0,95 veya %95'tir.

## <a name="control-set"></a>Denetim kümesi

Bir denetim kümesi, tahmine dayalı bir kodlama modelinin eğitim işlemi sırasında kullanılır. Denetim kümesi, modelin öğelere atadığınız tahmin puanlarını, eğitim yuvarlaları sırasında gerçekleştirdığınız etiketle değerlendirmektir. Denetim kümesi boyutu, gözden geçirme kümesinde yer alan öğelerin sayısına, modeli oluştururken ayarlanmış hata değerlerinin güven düzeyine ve kenar boşluğu değerlerine göre oluşturulur. Denetim kümesinde yer alan öğeler hiçbir zaman değişmez ve kullanıcılara tanınmaz. Denetim kümesinde toplam öğe sayısı, eğitim turu için uç uç sayfada görüntülenir.

## <a name="control-set-confusion-matrix"></a>Denetim kümesi karışıklığı matrisi

Siz eğitim turlarını tamamlandıktan sonra, model denetim kümesinde eğitim turu sırasında etiketledikten 10 öğeye bir tahmin puanı atar. Model, bu 10 öğenin tahmin puanlarını, eğitim turu sırasında öğeye atadığı gerçek etiketle karşıtır. Bu karşılaştırmaya dayanarak, model modelin tahmin performansını değerlendirmek için aşağıdaki sınıflandırmaları tanımlar:

<br>

****

|Etiket|Model, öğenin uygun olduğunu öngörür|Model, öğenin uygun olmadığını öngörür|
|---|---|---|
|**Gözden geçiren öğeyi uygun olarak etiketler**|Doğru pozitif|Hatalı pozitif sonuç|
|**Gözden geçiren öğeyi uygun değil olarak etiketler**|Yanlış negatif|Doğru negatif|
|

Bu karşılaştırmalara bağlı olarak, model F-puanı, duyarlılık ve geri çekme ölçümleri için değerleri ve her birinin hata marjını türetir. Bir eğitim turu için, matriste yer alan karışıklık türlerinden her biri, uç uç sayfada görüntülenir.

## <a name="f-score"></a>F-score

F-score, duyarlılık ve geri çekme ölçümlerine göre puanların ağırlıklı ortalamasıdır.  Bu ölçümün puan aralığı **0** ile **1 arasındadır**. **1'e yakın bir** puan, modelin ilgili öğeleri daha doğru algılaytır olduğunu gösterir. F-score metriği model panosunda ve her eğitim turu için uç uç sayfada görüntülenir.

## <a name="margin-of-error"></a>Hata kenar boşluğu

Hatanın kenar boşluğu, tahmine dayalı bir kodlama modu mazsanız gelişmiş bir ayardır. Denetim kümenizin rastgele örneklemesinden türetilen performans ölçümleri (örneğin, zenginlik, duyarlılık ve geri çekme) hata derecesini belirtir. Hatanın alt kenar boşluğu, modelin performans ölçümlerinin daha küçük bir aralıkta olduğundan emin olmak için daha büyük bir denetim kümesi gerektirir. Hata ve güven düzeyi kenar boşluğu değerleri de denetim kümesine kaç öğenin dahil olduğunu belirlemeye yardımcı olur. Hata kenar boşluğu için varsayılan değer 0,05 veya %5'tir.

## <a name="model-stability"></a>Model kararlılığı

Model kararlılığı, modelin gözden geçirme kümesinde yer alan bir belgenin uygun olup olmadığını doğru bir şekilde tahmin etme becerisini gösterir. Model kararsız olduğunda, modelin kararlılığını içerecek şekilde daha fazla eğitim yuvarlaması gerçekleştiriliyor olabilir. Model kararlı olduğunda daha fazla eğitim yuvarlatma işlemi gerçekleştirile gerekmektedir. Model panosu, modelin kararlılığının geçerli durumunu gösterir. Bir model kararlı olduğunda, performans ölçümleri hatanın güven düzeyi ve kenar boşluğu ayarlarına uygun bir düzeye ulaştı.

## <a name="overturn-rate"></a>Overturn rate

Overturn oranı, gözden geçirme kümesinde, tahmin puanının eğitim yuvarlaları arasında değişte olduğu yüzdedir. Bir model, overturn oranı %5'in altında olduğunda kararlı kabul edilir. Overturn rate metric is displayed on the model dashboard and on the flyout page for each training round. İlk eğitim tur için geri dönüş oranı sıfırdır çünkü, daha önce üzerinde overturn yapmak için bir tahmin puanı sıfırdır.

## <a name="precision"></a>Duyarlılık

Duyarlılık ölçümü, modelin tahmin edilen öğeler arasında aslında uygun olan öğelerin oranını ölçür. Bu, denetim kümesinde bulunan öğelerin gözden geçiren ve model tarafından uygun olarak tahmin edilen etiket olduğu anlamına gelir. Bu ölçümün puan aralığı **0** ile **1 arasındadır**. **1'e yakın bir** puan, modelin daha az ilgili olmayan öğe tanımlaytır olduğunu gösterir. Duyarlılık ölçümü model panosunda ve her eğitim turu için uç uç sayfada görüntülenir.

## <a name="prediction-score"></a>Tahmin puanı

Bu, bir modelin gözden geçirme kümesinde her belgeye atadığınız puandır. Puan, modelin eğitim turlarında edinilen eğitimle karşılaştırıldığında belgenin ilgi düzeyine göredir. Genelde, tahmin puanları **0 ile** **0,5** arasında olan öğeler uygun kabul edilir ve tahmin puanları **0,5** ile **1** arasında olan öğeler uygun kabul edilir. Tahmin puanı bir belge meta veri alanında yer eder. Belirtilen tahmin aralığı içinde yer alan bir gözden geçirme kümesinde öğeleri görüntülemek için tahmin filtresi kullanabilirsiniz.

## <a name="recall"></a>Geri Çekme

Geri çekme metrik, modelin tahmin edilen öğeler arasında gerçekten ilgili olduğu orneklerini ölçür. Bu, denetim kümesinde öngörülen modelin uygun olduğu öğeler için gözden geçiren kişi tarafından da etiketlenmiş olduğu anlamına gelir. Bu ölçümün puan aralığı **0** ile **1 arasındadır**. **1'e yakın bir** puan, modelin ilgili öğelerin daha büyük bir kısmını belirleyeceklerini gösterir. Geri çekme ölçümü model panosunda ve her eğitim turu için uç uç sayfada görüntülenir.

## <a name="review-set"></a>Gözden Geçirme kümesi

Gözden geçirme kümesi öngörülebilir kodlama modelinin kapsamını sağlar. Gözden geçirme kümesi için yeni bir model  oluşturmada, denetim kümesi ve eğitim kümelerinin öğeleri gözden geçirme kümesinden seçilir. Model, tahmin puanlarını ata olduğunda, bu puanları gözden geçirmedeki öğeleri atar. Tahmine dayalı bir kodlama modeli oluşturmadan önce, tüm öğeleri gözden geçirme kümesine eklemeniz gerekir. Bir model oluşturduklardan sonra öğe eklersiniz, bu öğelere tahmin puanı atanmaz.

## <a name="richness"></a>Zenginlik

Zenginlik metrik, modelin uygun olarak tahmin edilen gözden geçirme kümesi öğelerinin yüzdesini ölçür. Bu ölçümün puan aralığı **0** ile **1 arasındadır**. Zenginlik metriği model panosunda görüntülenir.

## <a name="sampled-items"></a>Örnekli öğeler

Örnek alınan *öğeler terimi* , bir gözden geçirme kümesinde (metin içeren) rastgele bir öğe örneğine başvurur; bu örnek, tahmine dayalı bir kodlama modeli oluşturmak için seçilen ve denetim kümesiyle ilişkilendirilmiş olur. Her eğitim turu için rastgele bir öğe örneği de seçilir. Bir modelin denetim kümesi için seçilen öğeler, hiçbir zaman aynı modele uygun eğitim kümesine dahil edilir. Bu durum da şu şekildedir: eğitim kümesi öğeleri hiçbir zaman denetim kümesine dahil değildir.

## <a name="training-set"></a>Eğitim kümesi

Model, gözden geçirme kümesinden öğeleri rastgele seçer ve bunları eğitim kümesine ekler. Eğitim turu sırasında, denetim kümesinden gelen öğelere ek olarak, her birini "ilgili" veya "ilgili değil" olarak etiketlemek için eğitim kümesinden gelen öğeler de size sunulacaktır. Bu etiketleme veya "eğitim" süreci, modelin gözden geçirmedeki hangi öğelerin ilgili veya ilgili olmadığını tahmin etmeyi öğrenmesinde yardımcı olur. Her eğitim turu gerçekleştirşiniz, model gözden geçirmeden daha fazla öğe seçer ve bunları bu eğitim turuna yönelik eğitim kümesine ekler. Denetim kümesinden gelen öğeler hiçbir zaman eğitim kümesi için seçilmez.
