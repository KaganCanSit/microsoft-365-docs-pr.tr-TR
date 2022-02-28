---
title: Arama sorgunuza hataları denetleme
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MOE150
- MET150
ms.assetid: 88898874-e262-4c5c-b6d2-4e697497fc74
ms.custom: seo-marvel-apr2020
description: Aramanızı çalıştırmadan önce, eBulma aramalarında anahtar sözcük sorgunuzda hataları ve yazım hatalarını nasıl algılayabilirsiniz.
ms.openlocfilehash: c820b72ea54e338d4f2fde475568bf2b1c22ba3b
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62984028"
---
# <a name="check-your-search-query-for-errors"></a>Arama sorgunuza hataları denetleme
  
İçerik arama ve Core eKbulma için arama sorgularında bizim kontrol edeceğimiz desteklenmeyen karakterlerin listesi burada ve ve şekildedir. Desteklenmeyen karakterler çoğunlukla gizlidir ve genellikle bir arama hatasına neden olur veya desteklenmeyen sonuçlar döndürür.
  
- **Akıllı tırnak işaretleri** - Akıllı tek ve çift tırnak işaretleri (kıvrımlı tırnak olarak da denir) destek gösterilmez. Arama sorgusunda yalnızca düz tırnak işaretleri kullanılabilir. 

- **Yazdırılamaz ve denetim karakterleri** - Yazdırılamaz ve denetim karakterleri alfasayısal karakter gibi yazılı bir simgeyi temsil etmez. Yazdırılamaz ve denetim karakterlerine örnek olarak, metni biçimlendiren veya metin satırlarını ayıran karakterler örnek olarak verilmiştir. 

- **Soldan sağa** ve sağdan sola işaretler - Bu işaretler soldan sağa dillerin (İngilizce ve İspanyolca gibi) ve sağdan sola dillerin (Arapça ve İbranice gibi) metin yönünü belirtmek için kullanılan denetim karakterleridir.

- **Küçük harf Boole** işleçleri - Arama sorgusunda **AND**, **OR** ve **NOT** gibi bir Boole işleci kullanıyorsanız, büyük harfle çalışması gerekir. Bir sorguda yazım hatası olup denetlememiz, küçük harf işleçleri kullan olsa bile sorgu söz dizimi sıklıkla Boole işlecinin kullanılıyor olduğunu gösterir; örneğin,  `(WordA or WordB) and (WordC or WordD)`.

## <a name="what-happens-if-a-query-has-an-unsupported-character"></a>Sorguda desteklenmeyen bir karakter varsa ne olur?

Sorgunuzda desteklenmeyen karakterler bulunursa, desteklenmeyen karakterler bulundu diyen bir uyarı iletisi görüntülenir ve alternatif bir seçenek önerir. Ardından, özgün sorguyu tutma veya bunu önerilen gözden geçirilmiş sorguyla değiştirme seçeneğiniz vardır.

Burada, önceki ekran görüntüsünde arama sorgusunda yazım hataları olup denetimi'ne tıklanmanız sonrasında görüntülenen uyarı iletisi örneği ve açık bir şekilde ve açıklanmalı. Özgün sorguda akıllı tırnaklar ve küçük harf Boole işleçleri kullanıldı.
  
![Sorgunuz için önerilen bir düzeltme ile bir uyarı iletisi görüntülenir.](../media/23214b30-8e52-412c-bd80-63fb1b3ed52d.png)
  
## <a name="how-to-prevent-unsupported-characters-in-your-search-queries"></a>Arama sorgularında desteklenmeyen karakterleri önleme

Sorguyu veya sorgunun bölümlerini başka uygulamalardan (Microsoft Word veya Microsoft Excel gibi) kopyalayıp İçerik Arama'nın sorgu sayfasındaki anahtar sözcük kutusuna yapıştırarak, desteklenmeyen karakterler genellikle bir sorguya eklenir. Desteklenmeyen karakterleri önlemenin en iyi yolu, sorguyu anahtar sözcük kutusuna yazmaktır. Word'den veya başka bir Excel kopyalayıp, Microsoft Not Defteri gibi düz bir metin düzenleyicisine Not Defteri. Metin dosyasını kaydedin ve Kodlama **açılan listesindeNSI'yi** seçin. Bu işlem tüm biçimlendirmeyi ve desteklenmeyen karakterleri kaldırır. Ardından, sorguyu metin dosyasından kopyalayıp anahtar sözcük sorgu kutusuna yapıştırabilirsiniz.
