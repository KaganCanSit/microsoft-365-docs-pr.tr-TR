---
title: Arama sorgunuzda hata olup olmadığını kontrol etme
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
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
description: Aramayı çalıştırmadan önce eBulma aramaları için anahtar sözcük sorgunuzdaki hataları ve yazım hatalarını algılamayı öğrenin.
ms.openlocfilehash: 477017c14807be7d17496e9f418cf22ba6137563
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66638774"
---
# <a name="check-your-search-query-for-errors"></a>Arama sorgunuzda hata olup olmadığını kontrol etme
  
İçerik arama ve Microsoft Purview eKeşif (Standart) için arama sorgularında denetlediğimiz desteklenmeyen karakterlerin listesi aşağıdadır. Desteklenmeyen karakterler genellikle gizlenir ve genellikle bir arama hatasına neden olur veya istenmeyen sonuçlar döndürür.
  
- **Akıllı tırnak işaretleri** - Akıllı tek ve çift tırnak işaretleri (kıvrımlı tırnak olarak da adlandırılır) desteklenmez. Arama sorgusunda yalnızca düz tırnak işaretleri kullanılabilir. 

- **Yazdırılamayan ve denetim karakterleri** - Yazdırılamayan ve denetim karakterleri, alfasayısal karakter gibi yazılı bir simgeyi temsil etmez. Yazdırılamayan karakterlere ve denetim karakterlerine örnek olarak, metni biçimlendiren karakterler veya ayrı metin satırları verilebilir. 

- **Soldan sağa ve sağdan sola işaretler** - Bu işaretler, soldan sağa dillerin (İngilizce ve İspanyolca gibi) ve sağdan sola dillerin (Arapça ve İbranice gibi) metin yönünü belirtmek için kullanılan denetim karakterleridir.

- **Küçük HarfLi Boole işleçleri** - Bir arama sorgusunda **AND**, **OR** ve **NOT** gibi bir Boole işleci kullanıyorsanız, büyük harfle yazılmalıdır. Bir sorguda yazım hatası olup olmadığını denetlediğimizde, sorgu söz dizimi genellikle küçük harf işleçleri kullanılsa bile Boole işlecinin kullanıldığını gösterir; örneğin,  `(WordA or WordB) and (WordC or WordD)`.

## <a name="what-happens-if-a-query-has-an-unsupported-character"></a>Sorgu desteklenmeyen bir karaktere sahipse ne olur?

Sorgunuzda desteklenmeyen karakterler bulunursa desteklenmeyen karakterlerin bulunduğunu belirten ve alternatif bir seçenek öneren bir uyarı iletisi görüntülenir. Ardından özgün sorguyu tutma veya önerilen düzeltilmiş sorguyla değiştirme seçeneğiniz vardır.

Önceki ekran görüntüsünde **Arama sorgusunun yazım hatalarını denetle'ye** tıkladıktan sonra görüntülenen uyarı iletisinin bir örneği aşağıda verilmiş. Özgün sorgunun akıllı tırnak işaretleri ve küçük harf Boole işleçleri kullandığını unutmayın.
  
![Sorgunuz için önerilen düzeltmeyle birlikte bir uyarı iletisi görüntülenir.](../media/23214b30-8e52-412c-bd80-63fb1b3ed52d.png)
  
## <a name="how-to-prevent-unsupported-characters-in-your-search-queries"></a>Arama sorgularınızda desteklenmeyen karakterleri önleme

Desteklenmeyen karakterler genellikle sorguyu veya sorgunun bölümlerini diğer uygulamalardan (Microsoft Word veya Microsoft Excel gibi) kopyalayıp İçerik Arama'nın sorgu sayfasındaki anahtar sözcük kutusuna yapıştırdığınızda sorguya eklenir. Desteklenmeyen karakterleri önlemenin en iyi yolu, sorguyu anahtar sözcük kutusuna yazmaktır. Ya da Word veya Excel'den bir sorgu kopyalayıp Microsoft Not Defteri gibi düz bir metin düzenleyicisine yapıştırabilirsiniz. Metin dosyasını kaydedin ve **Kodlama** açılan listesinde **ANSI'yi** seçin. Bu, tüm biçimlendirmeleri ve desteklenmeyen karakterleri kaldırır. Ardından sorguyu kopyalayıp metin dosyasından anahtar sözcük sorgu kutusuna yapıştırabilirsiniz.
