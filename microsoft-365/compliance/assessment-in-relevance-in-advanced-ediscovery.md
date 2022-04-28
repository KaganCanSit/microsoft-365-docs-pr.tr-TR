---
title: eBulma'da İlgi Değerlendirmeyi Anlama (Premium)
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
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
description: Microsoft Purview eKeşif'te (Premium) İlgi eğitimi sırasındaki sorunların zenginliğini belirlemede Değerlendirme aşamasına ve rolüne genel bir bakış edinin.
ROBOTS: NOINDEX, NOFOLLOW
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 3bfd6087bbcade2c7e4d9afdcda0f47bbea6f53d
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65096126"
---
# <a name="assessment-in-the-relevance-module-in-ediscovery-premium"></a>eBulma'daki İlgi modülünde değerlendirme (Premium)

[!include[Purview banner](../includes/purview-rebrand-banner.md)]
  
Microsoft Purview eBulma (Premium), örneğin tanımlanan sorunlar ve bir servis talebi için içeri aktarılan veriler için erken değerlendirmeyi etkinleştirir. eBulma (Premium), uzmanın benimsenen bir yaklaşım hakkında karar vermesine ve bu kararları belge gözden geçirme projesine uygulamasına olanak tanır.
  
## <a name="understanding-assessment"></a>Değerlendirmeyi anlama

Değerlendirme bölümünde uzman, sorunların zenginliğini belirlemek ve eğitim sonuçlarını yansıtan istatistikler üretmek için kullanılan en az 500 dosyadan oluşan rastgele bir kümeyi inceler. Değerlendirme, eBulma (Premium) İlgisinin doğru istatistikler sağlamasına ve eğitim sürecinde dengelenme noktasını etkili bir şekilde belirlemesine yardımcı olacak istatistiksel bir düzeye ulaşmak için yeterli ilgili dosya bulunduğunda başarılı olur. 
  
Değerlendirme kümesindeki ilgili dosya sayısı ne kadar yüksek olursa, istatistikler ve kararlılık algoritmasının etkinliği de o kadar doğru olur. Değerlendirme dosyalarındaki ilgili dosyaların sayısı sorunun zenginliğine bağlıdır. Zenginlik, kümedeki ilgili dosyaların bir sorunla ilgili tahmini yüzdesidir. Daha yüksek zenginliğe sahip sorunlar, daha düşük zenginliğe sahip sorunlardan daha hızlı bir şekilde daha fazla sayıda ilgili dosyaya ulaşır. Son derece düşük zenginliğe sahip sorunlar (örneğin, %2 veya daha az), önemli sayıda İlgili dosyaya ulaşmak için çok büyük bir değerlendirme kümesi gerektirir.
  
Eğitim sırasında ve Batch hesaplaması sonrasında İzle ve Karar Ver sekmelerinde sunulan istatistikler, farklı gözden geçirme kümeleri için geri çağırma tahminlerini içerir. İstatistiklerde, bir örnek kümesini (bu örnekte değerlendirme dosyaları) temel alan tahminler hatanın kenar boşluğu ve bu hata kenar boşluğunun güvenilirlik düzeyini içerir. Örneğin, %80'in tahmini geri çağırması % 95 güvenilirlik düzeyiyle artı veya eksi %5 hata marjı olabilir. Bu, tahmini geri çağırmanın aslında %75-%85 olduğu ve bu tahminin %95 güvene sahip olduğu anlamına gelir. Değerlendirme kümesi ne kadar büyük olursa hatanın kenar boşluğu küçülür ve istatistikler daha doğru olur. 
  
Uzman 500 dosyadan oluşan bir ilk değerlendirme kümesini gözden geçirmesinin ardından İlgi, geri çağırma değerlerinin geçerli hata marjını belirleyebilir. İlgi ayrıca değerlendirme kümesini iyileştirmek için ulaşılacak varsayılan hata kenar boşluğu önerecektir. İşte birkaç örnek:
  
- Değerlendirme kümesi zaten artı veya eksi %10 hata marjı verdiyse, İlgi eğitime geçmenizi önerir (ek değerlendirme incelemesi gerekmez). 

- Değerlendirme kümesi artı veya eksi %13 hata marjı verdiyse, İlgi daha küçük bir kenar boşluğuna ulaşmak için başka bir değerlendirme dosyası kümesinin gözden geçirilmesini önerebilir. 

- Zenginlik son derece düşükse, hatanın kenar boşluğu büyük olsa bile İlgi değerlendirmesinin durdurulmasını önerebilir (istatistikler pratik olmaz), çünkü hatanın yararlı bir kenar boşluğuna ulaşmak için gereken değerlendirme kümesi çok büyük.

Her sorunun kendi zenginliği, geçerli hata marjı ve sonuç olarak tahmini ek değerlendirme dosyası sayısı vardır. Sonraki değerlendirme kümesi, en fazla dosya sayısına (tek bir kümede 1.000'e kadar) göre oluşturulur.
  
İlgi önerilerini kabul edebilir veya hatanın geçerli kenar boşluğunu ihtiyaçlarınıza göre ayarlayabilirsiniz. Hatanın varsayılan geçerli kenar boşluğu, %75'e eşit veya daha yüksek geri çağırma için belirlenir.
  
> [!NOTE]
> Değerlendirme aşaması, bir sorunun genişletilmiş görünümündeki **İlgi \> İzleme** sekmesinde, sorun başına **Değerlendirme** onay kutusunu ve ardından "tüm sorunlar" için temizlenerek atlanabilir. Sonuç olarak, bu sorunla ilgili istatistikler olmayacaktır. **Değerlendirme** onay kutusunun temizlenmesi yalnızca değerlendirme gerçekleştirilmeden önce yapılabilir. Bir durumda birden çok sorun olduğunda, değerlendirme yalnızca her sorun için onay kutusu temizlenmişse atlanır.
