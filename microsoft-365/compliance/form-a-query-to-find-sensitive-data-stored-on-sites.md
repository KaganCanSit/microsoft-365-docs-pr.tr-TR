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
description: Kiracınız genelinde hassas veriler içeren belgeleri bulmak için SharePoint Online'da veri kaybı önlemeyi (DLP) kullanın.
ms.openlocfilehash: 1bb3ed0286f719f9ea9210b4952044081213914f
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66638333"
---
# <a name="form-a-query-to-find-sensitive-data-stored-on-sites"></a>Sitelerde depolanan hassas verileri bulmak için sorgu oluşturma

Kullanıcılar genellikle sitelerinde kredi kartı numaraları, sosyal güvenlik numaraları veya kişisel gibi hassas verileri depolar ve zaman içinde bu durum bir kuruluşu önemli veri kaybı riskine maruz bırakabilir. OneDrive İş siteler de dahil olmak üzere sitelerde depolanan belgeler, kuruluş dışındaki kişilerle paylaşılabilir ve bu kişiler bilgilere erişemez. SharePoint Online'da Microsoft Purview Veri Kaybı Önleme (DLP) ile kiracınızın tamamında hassas veriler içeren belgeleri bulabilirsiniz. Belgeleri keşfettikten sonra, verileri korumak için belge sahipleriyle çalışabilirsiniz. Bu konu, hassas verileri aramak için bir sorgu oluşturmanıza yardımcı olabilir.

> [!NOTE]
> Elektronik bulma veya eBulma ve DLP, [SharePoint Online Plan 2](https://go.microsoft.com/fwlink/?LinkId=510080) gerektiren premium özelliklerdir.

## <a name="forming-a-basic-dlp-query"></a>Temel bir DLP sorgusu oluşturma

Temel bir DLP sorgusunu oluşturan üç bölüm vardır: SensitiveType, sayı aralığı ve güvenilirlik aralığı. Aşağıdaki grafikte gösterildiği gibi **, SensitiveType:"\<type\>"** gereklidir ve her ikisi de **|\<count range\>** **|\<confidence range\>** isteğe bağlıdır.

![Gerekli ve isteğe bağlı olarak bölünmüş örnek sorgu.](../media/DLP-query-example-text.png)

### <a name="sensitive-type---required"></a>Hassas tür - gerekli

Her bir parça nedir? SharePoint DLP sorguları genellikle özelliğiyle  `SensitiveType:"` ve [hassas bilgi türleri envanterinden bir bilgi türü](/Exchange/what-the-sensitive-information-types-in-exchange-look-for-exchange-2013-help) adıyla başlar ve ile  `"`biter. Kuruluşunuz için oluşturduğunuz [özel bir hassas bilgi türünün](create-a-custom-sensitive-information-type.md) adını da kullanabilirsiniz. Örneğin, kredi kartı numaraları içeren belgeleri arıyor olabilirsiniz. Böyle bir örnekte şu biçimi kullanırsınız:  `SensitiveType:"Credit Card Number"`. Sayım aralığı veya güvenilirlik aralığı eklemediğiniz için, sorgu kredi kartı numarasının algılandığı her belgeyi döndürür. Bu, çalıştırabileceğiniz en basit sorgudur ve en çok sonucu döndürür. Hassas türün yazım ve aralıklarının önemli olduğunu unutmayın.

### <a name="ranges---optional"></a>Aralıklar - isteğe bağlı

Sonraki iki parçanın ikisi de aralıktır, bu nedenle bir aralığın nasıl göründüğünü hızlıca inceleyelim. SharePoint DLP sorgularında, temel bir aralık iki noktayla ayrılmış iki sayıyla temsil edilir ve şöyle görünür:  `[number]..[number]`. Örneğin, kullanılırsa  `10..20` , bu aralık 10 ile 20 arasında sayılar yakalar. Bu konu başlığı altında birçok farklı aralık bileşimi ve birkaçı ele alınmıştır.

Şimdi sorguya bir sayı aralığı ekleyelim. Bir belgenin sorgu sonuçlarına eklenmeden önce içermesi gereken hassas bilgilerin oluşum sayısını tanımlamak için sayı aralığını kullanabilirsiniz. Örneğin, sorgunuzun yalnızca tam olarak beş kredi kartı numarası içeren belgeleri döndürmesini istiyorsanız şunu kullanın:  `SensitiveType:"Credit Card Number|5"`. Sayı aralığı, yüksek derecede risk oluşturan belgeleri belirlemenize de yardımcı olabilir. Örneğin, kuruluşunuz beş veya daha fazla kredi kartı numarasına sahip belgeleri yüksek riskli olarak değerlendirebilir. Bu ölçüte uyan belgeleri bulmak için şu sorguyu kullanabilirsiniz:  `SensitiveType:"Credit Card Number|5.."`. Alternatif olarak, şu sorguyu kullanarak beş veya daha az kredi kartı numarasına sahip belgeleri bulabilirsiniz:  `SensitiveType:"Credit Card Number|..5"`.

#### <a name="confidence-range"></a>Güvenilirlik aralığı

Son olarak, güvenilirlik aralığı algılanan hassas türün aslında bir eşleşme olduğu güven düzeyidir. Güvenilirlik aralığı değerleri, sayı aralığına benzer şekilde çalışır. Sayı aralığı eklemeden sorgu oluşturabilirsiniz. Örneğin, güven aralığı yüzde 85 veya daha yüksek olduğu sürece herhangi bir sayıda kredi kartı numarasına sahip belgeleri aramak için şu sorguyu kullanabilirsiniz:  `SensitiveType:"Credit Card Number|*|85.."`.

> [!IMPORTANT]
> Yıldız işareti ( `*` ), herhangi bir değerin çalıştığı anlamına gelen bir joker karakterdir. Joker karakterini ( `*` ) sayı aralığında veya güvenilirlik aralığında kullanabilirsiniz, ancak hassas bir türde kullanamazsınız.

### <a name="additional-query-properties-and-search-operators-available-in-the-ediscovery-center"></a>eBulma Merkezi'nde kullanılabilen ek sorgu özellikleri ve arama işleçleri

SharePoint'teki DLP, belirli bir zaman çerçevesi içinde taranan dosyaları aramanıza yardımcı olabilecek LastSensitiveContentScan özelliğini de tanıtır. özelliğine  `LastSensitiveContentScan` sahip sorgu örnekleri için sonraki bölümdeki [Karmaşık sorgu örnekleri](#examples-of-complex-queries) bölümüne bakın.

Sorgu oluşturmak için yalnızca DLP'ye özgü özellikleri değil, aynı zamanda veya `FileExtension`gibi `Author` standart SharePoint eKeşif arama özelliklerini de kullanabilirsiniz. Karmaşık sorgular oluşturmak için işleçleri kullanabilirsiniz. Kullanılabilir özelliklerin ve işleçlerin listesi için [eBulma ile Arama Özelliklerini ve İşleçlerini Kullanma blog gönderisine](/archive/blogs/quentin/using-search-properties-and-operators-with-ediscovery) bakın.

## <a name="examples-of-complex-queries"></a>Karmaşık sorgu örnekleri

Aşağıdaki örneklerde, tam olarak aradığınızı bulmak için sorgularınızı nasıl iyileştirebileceğinizi göstermek için farklı hassas türler, özellikler ve işleçler kullanılır.

<br>

****

|Sorgu|Açıklama|
|---|---|
|`SensitiveType:"International Banking Account Number (IBAN)"`|Ad çok uzun olduğundan garip görünebilir, ancak bu hassas tür için doğru addır. [Hassas bilgi türleri envanterinden](/Exchange/what-the-sensitive-information-types-in-exchange-look-for-exchange-2013-help) tam adları kullandığınızdan emin olun. Kuruluşunuz için oluşturduğunuz [özel bir hassas bilgi türünün](create-a-custom-sensitive-information-type.md) adını da kullanabilirsiniz.|
|`SensitiveType:"Credit Card Number|1..4294967295|1..100"`|Bu, "Kredi Kartı Numarası" hassas türüyle en az bir eşleşmesi olan belgeleri döndürür. Her aralığın değerleri ilgili en düşük ve en yüksek değerlerdir. Bu sorguyu yazmanın daha basit bir yoludur  `SensitiveType:"Credit Card Number"`, ancak bunun eğlencesi nerededir?|
|`SensitiveType:"Credit Card Number|5..25" AND LastSensitiveContentScan:"8/11/2018..8/13/2018"`|Bu, 11 Ağustos 2018 ile 13 Ağustos 2018 tarihleri arasında taranan 5-25 kredi kartı numarasına sahip belgeleri döndürür.|
|`SensitiveType:"Credit Card Number|5..25" AND LastSensitiveContentScan:"8/11/2018..8/13/2018" NOT FileExtension:XLSX`|Bu, 11 Ağustos 2018 ile 13 Ağustos 2018 tarihleri arasında taranan 5-25 kredi kartı numarasına sahip belgeleri döndürür. XLSX uzantısına sahip dosyalar sorgu sonuçlarına dahil değildir.  `FileExtension` sorguya ekleyebileceğiniz birçok özellik arasında yer alır. Daha fazla bilgi için bkz. [Arama Özelliklerini ve İşleçlerini eBulma ile Kullanma](/archive/blogs/quentin/using-search-properties-and-operators-with-ediscovery).|
|`SensitiveType:"Credit Card Number" OR SensitiveType:"U.S. Social Security Number (SSN)"`|Bu, kredi kartı numarası veya sosyal güvenlik numarası içeren belgeleri döndürür.|
|

## <a name="examples-of-queries-to-avoid"></a>Kaçınılması gereken sorgu örnekleri

Tüm sorgular eşit oluşturulmaz. Aşağıdaki tabloda, SharePoint'te DLP ile çalışmayan sorgu örnekleri verilmiştir ve bunun nedeni açıklanmaktadır.

<br>

****

|Desteklenmeyen sorgu|Neden|
|---|---|
|`SensitiveType:"Credit Card Number|.."`|En az bir sayı eklemeniz gerekir.|
|`SensitiveType:"NotARule"`|"NotARule" geçerli bir hassas tür adı değil. DLP sorgularında yalnızca [hassas bilgi türü envanterindeki](/Exchange/what-the-sensitive-information-types-in-exchange-look-for-exchange-2013-help) adlar çalışır.|
|`SensitiveType:"Credit Card Number|0"`|Sıfır, bir aralıktaki en düşük değer veya en büyük değer olarak geçerli değildir.|
|`SensitiveType:"Credit Card Number"`|Bunu görmek zor olabilir, ancak "Kredi" ile "Kart" arasında sorguyu geçersiz kılan fazladan boşluk vardır. Hassas [bilgi türleri envanterinden tam olarak hassas tür](/Exchange/what-the-sensitive-information-types-in-exchange-look-for-exchange-2013-help) adları kullanın.|
|`SensitiveType:"Credit Card Number|1. .3"`|İki dönemli bölüm boşlukla ayrılmamalıdır.|
|`SensitiveType:"Credit Card Number| |1..|80.."`|Çok fazla boru sınırlayıcısı (\|) var. Bunun yerine şu biçimi izleyin: `SensitiveType: "Credit Card Number|1..|80.."`|
|`SensitiveType:"Credit Card Number|1..|80..101"`|Güvenilirlik değerleri bir yüzdeyi temsil ettiğinden 100'ü aşamaz. Bunun yerine 1 ile 100 arasında bir sayı seçin.|
|

## <a name="for-more-information"></a>Daha fazla bilgi için

- [Hassas bilgi türü varlık tanımları](sensitive-information-type-entity-definitions.md)
- [İçerik Araması Çalıştırma](content-search.md)
- [İçerik Arama için anahtar sözcük sorguları ve arama koşulları](keyword-queries-and-search-conditions.md)
