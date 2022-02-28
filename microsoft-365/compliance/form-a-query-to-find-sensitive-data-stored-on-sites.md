---
title: Sitelerde depolanan hassas verileri bulmak için sorgu oluşturma
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: 6/29/2018
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.collection:
- M365-security-compliance
- SPO_Content
ms.localizationpriority: medium
search.appverid:
- MOE150
- MET150
description: Kiracınız genelinde hassas veriler içeren belgeleri keşfetmek için SharePoint Online'da veri kaybı önleme (DLP) önlemeyi kullanın.
ms.openlocfilehash: af1ca8f28f80d58c0f366e1a002181e23db3d552
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62985700"
---
# <a name="form-a-query-to-find-sensitive-data-stored-on-sites"></a>Sitelerde depolanan hassas verileri bulmak için sorgu oluşturma

Kullanıcılar genellikle kredi kartı numaraları, sosyal güvenlik numaraları veya kişisel gibi hassas verileri sitelerinde depolar ve zamanla bu durum kuruluşun önemli veri kaybı risklerine neden olabilir. Sitelerde depolanan belgeler (OneDrive İş siteleri de dahil) kuruluşun dışındaki ve bilgilere erişimi olmaması gereken kişilerle paylaşılıyor olabilir. SharePoint Online'da veri kaybı önleme (DLP) ile kiracınız genelinde hassas veriler içeren belgeleri keşfedebilirsiniz. Belgeleri keşfettikten sonra, verileri korumak için belge sahipleriyle birlikte çalışabilirsiniz. Bu konu başlığı, hassas verileri aramak için sorgu oluşturmanızı sağlar.

> [!NOTE]
> Elektronik bulma veya eBulma ve DLP, Çevrimiçi [Plan 2'de SharePoint premium özelliklerdir](https://go.microsoft.com/fwlink/?LinkId=510080).

## <a name="forming-a-basic-dlp-query"></a>Temel DLP sorgusu oluşturma

Temel bir DLP sorgusunu üç parçadan oluşur: SensitiveType, say aralığı ve güven aralığı. Aşağıdaki grafikte de gösterildiği gibi **, SensitiveType:"\<type\>"** gereklidir ve her ikisi de isteğe **|\<count range\>** **|\<confidence range\>** bağlıdır.

![Gerekli ve isteğe bağlı olarak ayrılmış örnek sorgu.](../media/DLP-query-example-text.png)

### <a name="sensitive-type---required"></a>Hassas tür - gerekli

Peki her bölüm nedir? SharePoint DLP sorgularını `SensitiveType:"` oluşturmak için normalde özellik ve stokta kullanılan hassas bilgi türlerinden bir bilgi türü adı [kullanılır ve](/Exchange/what-the-sensitive-information-types-in-exchange-look-for-exchange-2013-help)`"` sonunda bir . Ayrıca, organizasyonunız için oluşturduğunuz [özel hassas bilgi](create-a-custom-sensitive-information-type.md) türünün adını da kullanabilirsiniz. Örneğin, kredi kartı numaralarını içeren belgeleri arıyor olabilir. Böyle bir örnekte, şu biçimi kullanırsiniz:  `SensitiveType:"Credit Card Number"`. Sayı aralığı veya güven aralığı dahil olmadığınız için sorgu, kredi kartı numarasının algılandığından dolayı her belgeyi döndürür. Bu, çalıştırabilirsiniz en basit sorgudur ve en çok sonucu döndürür. Hassas tür yazım ve aralığının önemli olduğunu unutmayın.

### <a name="ranges---optional"></a>Aralıklar - isteğe bağlı

Sonraki iki parçanın ikisi de aralıktır; bu nedenle, bir aralığın nasıl göründüğünü hemen incele bakalım. Bir SharePoint DLP sorgularında, temel aralık iki noktayla ayrılmış olarak iki sayıyla temsil edilen bir aralıktır ve şöyledir: `[number]..[number]`. Örneğin kullanılırsa  `10..20` , bu aralık 10 ile 20 arasında sayıları yakalar. Bu konuda birçok farklı aralık bileşimi vardır ve bunların birkaçı ele almaktadır.

Şimdi, sorguya bir sayı aralığı ek olarız. Bir belgenin sorgu sonuçlarına dahil olmadan önce içermesi gereken hassas bilgilerin yine olay sayısını tanımlamak için sayı aralığını kullanabilirsiniz. Örneğin, sorgunun yalnızca tam olarak beş kredi kartı numarası içeren belgeleri geri iadesini istiyorsanız, bunu kullanın:  `SensitiveType:"Credit Card Number|5"`. Sayı aralığı, yüksek riskli dereceler alan belgeleri tanımlamanıza da yardımcı olabilir. Örneğin, kuruluşlarınız beş veya daha fazla kredi kartı numarasına sahip belgeleri yüksek riskli olarak değerlendirebilirsiniz. Bu ölçüte uyan belgeleri bulmak için şu sorguyu kullanabilirsiniz:  `SensitiveType:"Credit Card Number|5.."`. Alternatif olarak, şu sorguyu kullanarak beş veya daha az kredi kartı numarası olan belgeleri bulabilirsiniz:  `SensitiveType:"Credit Card Number|..5"`.

#### <a name="confidence-range"></a>Güven aralığı

Son olarak, güven aralığı algılanan hassas türün aslında bir eşleşme olduğu güven düzeyidir. Güven aralığı değerleri, aralığı saymakla benzer şekilde çalışır. Bir sayı aralığı olmadan sorguyu formunuz olabilir. Örneğin, güven aralığı yüzde 85 veya daha yüksek olduğu sürece herhangi bir sayıda kredi kartı numarası olan belgeleri aramak için şu sorguyu kullanabilirsiniz:  `SensitiveType:"Credit Card Number|*|85.."`.

> [!IMPORTANT]
> Yıldız işareti ( ), herhangi bir `*` değerin işe yarar olduğu anlamına gelir bir joker karakterdir. Joker karakteri ( `*` ) say aralığında veya güven aralığında kullanabilirsiniz, ancak hassas bir tür içinde kullanabilirsiniz.

### <a name="additional-query-properties-and-search-operators-available-in-the-ediscovery-center"></a>eBulma Merkezi'nde kullanılabilen ek sorgu özellikleri ve arama işleçleri

DLP, SharePoint bir zaman çerçevesi içinde taranan dosyaları aramanıza yardımcı olan LastSensitiveContentScan özelliğini de içerir. Özellikle ilgili sorgu örnekleri  `LastSensitiveContentScan` için bir sonraki [bölümdeki Karmaşık sorgu](#examples-of-complex-queries) örneklerine bakın.

Sorgu oluşturmak için DLP'ye özgü özelliklerin yanı sıra, eKbulma arama özellikleri SharePoint veya gibi standart özellikleri de kullanabilirsiniz `Author` `FileExtension`. Karmaşık sorgular oluşturmak için işleçleri kullanabilirsiniz. Kullanılabilir özellikler ve işleçlerin listesi için, eBulma blog gönderisi ile Arama Özelliklerini ve [İşleçleri Kullanma'ya](/archive/blogs/quentin/using-search-properties-and-operators-with-ediscovery) bakın.

## <a name="examples-of-complex-queries"></a>Karmaşık sorgu örnekleri

Aşağıdaki örneklerde farklı hassas türler, özellikler ve işleçler kullanarak, tam olarak bulmak üzere sorgularınızı nasıl daraltabilirsiniz?

<br>

****

|Sorgu|Açıklama|
|---|---|
|`SensitiveType:"International Banking Account Number (IBAN)"`|Uzun olduğundan ad garip görünebilir, ancak bu hassas türün doğru adıdır. Hassas bilgi türlerinden stokta tam adları [kullanmaya emin olun](/Exchange/what-the-sensitive-information-types-in-exchange-look-for-exchange-2013-help). Ayrıca, organizasyonunız için oluşturduğunuz [özel hassas bilgi](create-a-custom-sensitive-information-type.md) türünün adını da kullanabilirsiniz.|
|`SensitiveType:"Credit Card Number|1..4294967295|1..100"`|Bu, hassas "Kredi Kartı Numarası" türüyle en az bir eşleşmesi olan belgeleri döndürür. Her aralığın değerleri ilgili en küçük ve en yüksek değerlerdir. Bu sorguyu yazmanın daha basit bir  `SensitiveType:"Credit Card Number"`yolu vardır, peki bu nasıl eğlenceli?|
|`SensitiveType:"Credit Card Number|5..25" AND LastSensitiveContentScan:"8/11/2018..8/13/2018"`|Bu, 11 Ağustos 2018'den 13 Ağustos 2018'e kadar taranmış 5-25 kredi kartı numarası olan belgeleri döndürür.|
|`SensitiveType:"Credit Card Number|5..25" AND LastSensitiveContentScan:"8/11/2018..8/13/2018" NOT FileExtension:XLSX`|Bu, 11 Ağustos 2018'den 13 Ağustos 2018'e kadar taranmış 5-25 kredi kartı numarası olan belgeleri döndürür. XLSX uzantısına sahip dosyalar sorgu sonuçlarına dahil değildir.  `FileExtension` bir sorguya ek birçok özelliktir. Daha fazla bilgi için bkz [. eBulma ile Arama Özelliklerini ve İşleçleri kullanma](/archive/blogs/quentin/using-search-properties-and-operators-with-ediscovery).|
|`SensitiveType:"Credit Card Number" OR SensitiveType:"U.S. Social Security Number (SSN)"`|Bu, kredi kartı numarası veya sosyal güvenlik numarası içeren belgeleri döndürür.|
|

## <a name="examples-of-queries-to-avoid"></a>Kaçınılması gereken sorgu örnekleri

Tüm sorgular eşit değildir. Aşağıdaki tabloda, SharePoint'de DLP ile çalışmayan SharePoint örnekler verilmiştir.

<br>

****

|Desteklenmeyen sorgu|Neden|
|---|---|
|`SensitiveType:"Credit Card Number|.."`|En az bir sayı eklemeniz gerekir.|
|`SensitiveType:"NotARule"`|"NotARule" geçerli bir hassas tür adı değildir. DLP sorgularında [yalnızca hassas bilgi türlerinde](/Exchange/what-the-sensitive-information-types-in-exchange-look-for-exchange-2013-help) stok işi olan adlar.|
|`SensitiveType:"Credit Card Number|0"`|Sıfır, aralıkta en küçük değer veya en büyük değer olarak geçerli değildir.|
|`SensitiveType:"Credit Card Number"`|Görmek zor olabilir, ancak "Kredi" ile "Kart" arasında sorguyu geçersiz kılan fazladan boşluklar vardır. Hassas bilgi türlerinden stokta tam [olarak hassas tür adları kullanın](/Exchange/what-the-sensitive-information-types-in-exchange-look-for-exchange-2013-help).|
|`SensitiveType:"Credit Card Number|1. .3"`|İki noktalı bölüm bir boşlukla ayrılmaması gerekir.|
|`SensitiveType:"Credit Card Number| |1..|80.."`|Çok fazla boru sınırlayıcı () var\|. Bunun yerine şu biçimi izleyin: `SensitiveType: "Credit Card Number|1..|80.."`|
|`SensitiveType:"Credit Card Number|1..|80..101"`|Güven değerleri bir yüzdeyi temsil etme nedeniyle, bunlar 100'den fazla olabilir. Bunun yerine 1 ile 100 arasında bir sayı seçin.|
|

## <a name="for-more-information"></a>Daha fazla bilgi için

- [Hassas bilgi türü varlık tanımları](sensitive-information-type-entity-definitions.md)
- [İçerik Arama çalıştırma](content-search.md)
- [İçerik Arama için Anahtar Sözcük sorguları ve arama koşulları](keyword-queries-and-search-conditions.md)
