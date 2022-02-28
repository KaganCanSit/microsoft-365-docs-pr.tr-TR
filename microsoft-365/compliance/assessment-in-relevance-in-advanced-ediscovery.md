---
title: Değerlendirmeyi İlgi Düzeyi düzeyine Advanced eDiscovery
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
titleSuffix: Office 365
ms.date: ''
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MOE150
- MET150
ms.assetid: 1d33d4fb-91ed-41c0-b72e-5a26eca3a2a7
description: Değerlendirme aşamasına ve bu aşamanın, Microsoft 365 Advanced eDiscovery'te ilgi düzeyi eğitimi sırasında sorunların zenginliğini belirlemeyle ilgili rolüne Microsoft 365 Advanced eDiscovery.
ROBOTS: NOINDEX, NOFOLLOW
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 80ec4f0c362ff403f45123bf837e82c5d2f6ed7e
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62985171"
---
# <a name="assessment-in-the-relevance-module-in-advanced-ediscovery"></a>Advanced eDiscovery'daki İlgi Düzeyi modülünde değerlendirme
  
Advanced eDiscovery, örneğin tanımlanan sorunlar ve vaka için alınan veriler için erken değerlendirmeyi sağlar. Advanced eDiscovery, uzmana benimsenmiş bir yaklaşım hakkında karar verme ve bu kararları belge gözden geçirme projesine uygulama konusunda olanak sağlar.
  
## <a name="understanding-assessment"></a>Değerlendirmeyi anlama

Değerlendirme'de, uzman sorunların zenginliğini belirlemek ve eğitim sonuçlarını yansıtan istatistikler üretmek için kullanılan en az 500 dosyalık rastgele bir kümeyi gözden kullanır. Uygun dosyaların doğru istatistikler sağlamak ve eğitim sürecinde sabitleme noktasını etkili bir şekilde belirlemek için Advanced eDiscovery Uygunluk düzeyine ulaşmalarına yardımcı olacak istatistiksel bir düzeye ulaşacak şekilde değerlendirme başarılı olur. 
  
Değerlendirme kümesinde ilgili dosyaların sayısı ne kadar fazlasa, kararlılık algoritmasının istatistikleri ve etkinliği o kadar doğru olur. Değerlendirme dosyaları içindeki ilgili dosyaların sayısı sorunun zenginliğine bağlıdır. Zenginlik, küme içinde bir konuyla ilgili dosyaların tahmini yüzde değeridir. Daha yüksek zenginlik sorunları, daha düşük zenginlik sorunlarına göre daha hızlı bir şekilde ilgili dosya sayısına ulaşacak. Aşırı düşük zenginlik sorunları (örneğin, %2 veya daha az) önemli sayıda İlgili dosyaya ulaşmak için çok büyük bir değerlendirme kümesi gerekir.
  
Eğitim sırasında ve Toplu hesaplamanın ardından Takip Et ve Kararla sekmelerinde sunulan istatistikler, farklı gözden geçirme kümeleri için geri çekme tahminlerini içerir. İstatistiklerde, örnek bir kümeyi temel alan tahminler (bu örnekte değerlendirme dosyaları) hata kenar boşluklarını ve bu hata marjının güven düzeyini içerir. Örneğin, tahmini %80 geri çekmede %95 güven düzeyine sahip artı veya eksi %5 hata marjı olabilir. Bu, tahmini geri çekmenin gerçekte %75-%85 olduğu ve tahminde %95 güven olduğu anlamına gelir. Değerlendirme kümesi ne kadar büyük olursa, hata kenar boşluğu daha küçük olur ve istatistikler daha doğru olur. 
  
Uzman 500 dosyalık bir ilk değerlendirme değerlendirmesini gözden kullandıktan sonra, İlgi Düzeyi geri çekme değerlerinin geçerli hata kenar boşluğu değerini belirler. İlgi derecesi, değerlendirme kümesi en iyi duruma getirmek için varsayılan hata kenar boşluğu da önerecek. İşte birkaç örnek:
  
- Değerlendirme kümesi zaten %artı veya eksi %10 hata marjı verdiyse, İlgi Düzeyi eğitime devam etmek önerecek (ek değerlendirme incelemesi gerekmez). 

- Değerlendirme kümesi %artı veya eksi %13 hata marjı verdiyse, İlgi Düzeyi daha küçük bir kenar boşluğuna ulaşmak için başka bir değerlendirme dosyaları kümesi gözden geçirmeyi önerebilirsiniz. 

- Zenginlik son derece düşükse, İlgi Düzeyi hata marjı büyük olsa bile değerlendirmeyi durdurmayı önerse (istatistikler pratik değildir), çünkü değerlendirme kümesi kullanışlı bir hata kenar boşluğuna ulaşmak için çok büyük olduğundan.

Her sorunun kendi zenginliği, geçerli hata marjı ve bunun sonucunda da tahmini ek değerlendirme dosyası sayısı vardır. Sonraki değerlendirme kümesi en fazla dosya sayısına (tek bir kümede en çok 1.000 dosya) göre oluşturulur.
  
İlgi Düzeyi önerilerini kabul veya geçerli hata kenar boşluklarını ihtiyaçlarına göre ayarlayabilirsiniz. Varsayılan geçerli hata kenar boşluğu geri çekme için %75'e eşit veya daha yüksek olarak belirlenir.
  
> [!NOTE]
> Değerlendirme aşaması, sorunun **\>** genişletilmiş görünümünde yer alan İlgi Alanı Izleme sekmesinde, sorun başına Değerlendirme onay kutusu ve sonra da "tüm sorunlar" için  temiz kullanarak atlanır. Sonuç olarak, bu sorun için hiçbir istatistik olmaz. Değerlendirme onay **kutusu** temiz yalnızca değerlendirme yapılmadan önce yapılabilir. Bir olayda birden çok sorun varsa, değerlendirme yalnızca her sorunda onay kutusu temiz temiz olursa atlanır.
