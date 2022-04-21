---
title: Uyumluluk merkezinde İçerik arama ve eBulma (Standart) sınırları
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: 78fe3147-1979-4c41-83bb-aeccf244368d
description: Microsoft Purview uyumluluk portalında İçerik arama ve eBulma (Standart) özellikleri için geçerli olan sınırlar hakkında bilgi edinin.
ms.openlocfilehash: 8cba04c7ed3257d5a168d7754b2964eb4aa97b0d
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/20/2022
ms.locfileid: "64999068"
---
# <a name="limits-for-ediscovery-search"></a>eBulma arama sınırları

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Microsoft Purview uyumluluk portalında eBulma arama araçlarına çeşitli sınırlar uygulanır. Buna **İçerik arama** sayfasında çalıştırılacak aramalar ve eBulma **(Standart)** sayfasında eBulma olayıyla ilişkili aramalar dahildir. Bu sınırlar, kuruluşlara sağlanan hizmetlerin durumunu ve kalitesini korumaya yardımcı olur. Arama için Exchange Online'da e-posta iletilerinin dizinlenmesiyle ilgili sınırlar da vardır. eBulma aramalarının veya e-posta dizin oluşturmanın sınırlarını değiştiremezsiniz, ancak eBulma aramalarını planlarken, çalıştırırken ve sorun giderirken bu sınırları dikkate alabilmeniz için bunları bilmeniz gerekir.

Microsoft Purview eBulma (Premium) aracıyla ilgili sınırlar için bkz. [eBulmadaki sınırlar (Premium)](limits-ediscovery20.md)

## <a name="search-limits"></a>Arama sınırları

Aşağıdaki tabloda, uyumluluk portalında içerik arama aracı kullanılırken ve Bir Microsoft Purview eKeşif (Standart) olayıyla ilişkili aramalar için arama sınırları listelenir.

<br>

****

|Sınırın açıklaması|Sınırı|
|---|---|
|Tek bir aramada aranabilecek en fazla posta kutusu veya site sayısı|Sınır <sup>1</sup> yok|
|Kuruluşunuzda aynı anda çalışabilecek en fazla arama sayısı.|30|
|Aynı anda çalıştırılabilen kuruluş genelindeki arama sayısı üst sınırı.|3|
|Tek bir kullanıcının aynı anda başlatabileceği en fazla arama sayısı. Bu sınır, büyük olasılıkla kullanıcı Güvenlik & Uyumluluk Merkezi PowerShell'de **Get-ComplianceSearch \|Start-ComplianceSearch** komutunu kullanarak birden çok arama başlatmaya çalıştığında isabet alır.|10|
|İçerik Arama sonuçlarının önizlemesini görüntülerken önizleme sayfasında görüntülenen kullanıcı posta kutusu başına en fazla öğe sayısı.|100|
|Arama sonuçlarının önizlemesini görüntülerken önizleme sayfasında görüntülenebilen tüm kullanıcı posta kutularında bulunan en fazla öğe sayısı. En yeni öğeler görüntülenir.|1.000 <sup>2</sup>|
|Arama sonuçları için önizlenebilen en fazla kullanıcı posta kutusu sayısı. Arama sorgusuyla eşleşen içerik içeren 1000'den fazla posta kutusu varsa, yalnızca en fazla arama sonucuna sahip ilk 1000 posta kutusu önizleme için kullanılabilir.|1,000|
|Arama sonuçlarının önizlemesini görüntülerken önizleme sayfasında görüntülenen SharePoint ve OneDrive İş sitelerinde bulunan en fazla öğe sayısı. En yeni öğeler görüntülenir.|200|
|Arama sonuçları için önizlenebilen en fazla site sayısı (SharePoint ve OneDrive İş). Arama sorgusuyla eşleşen içerik içeren toplam 200'den fazla site varsa, yalnızca en çok arama sonucuna sahip ilk 200 site önizleme için kullanılabilir.|200|
|İçerik arama sonuçlarının önizlemesini görüntülerken önizleme sayfasında görüntülenen ortak klasör posta kutusu başına en fazla öğe sayısı.|100|
|İçerik arama sonuçlarının önizlemesini görüntülerken önizleme sayfasında görüntülenen tüm ortak klasör posta kutularında bulunan en fazla öğe sayısı.|200|
|Arama sonuçları için önizlenebilen en fazla ortak klasör posta kutusu sayısı. Arama sorgusuyla eşleşen içerik içeren 500'den fazla ortak klasör posta kutusu varsa, yalnızca en çok arama sonucuna sahip ilk 500 ortak klasör posta kutusu önizleme için kullanılabilir.|500|
|Önizleme sayfasında görüntülenebilen bir öğenin en büyük boyutu.|10.000.000 bayt (yaklaşık 9,5 MB)|
|Arama sorgusu (işleçler ve koşullar dahil) için en fazla karakter sayısı. <p> **Not:** Bu sınır, sorgu genişletildikten ve anahtar sözcük sorgusundan karakterler, kullanıcıya uygulanan arama izinleri filtreleri ve tüm site konumlarının URL'lerini ekledikten sonra geçerlilik kazanır. Bu, sorgunun anahtar sözcüklerin her birine göre genişletileceği anlamına gelir. Örneğin, bir arama sorgusunda 15 anahtar sözcük ve ek parametre ve koşullar varsa, sorgu her birinde sorgudaki diğer parametreler ve koşullarla birlikte 15 kez genişletir. Bu nedenle, arama sorgusundaki karakter sayısı sınırın altında olsa da, bu sınırın aşılmasında katkıda bulunabilecek genişletilmiş sorgu olabilir.|**Posta kutuları:** 10.000. <p> **Siteler:** Tüm sitelerde arama yaparken 4.000 veya en fazla 20 site ararken 2.000. <sup>3</sup>|
|Bir arama sorgusunda tam bir tümceciği aramak için ön ek joker karakteri kullanılırken veya ön ek joker karakteri ve **NEAR** Boole işleci kullanılırken döndürülen en fazla değişken sayısı.|10.000 <sup>4</sup>|
|Ön ek joker karakterleri için en az alfa karakteri sayısı; örneğin, `time*`, `one*`veya `set*`.|3|
|"Arama ve temizleme" eylemini yaparak ( **New-ComplianceSearchAction -Purge** komutunu kullanarak) içindeki öğeleri silebileceğiniz en fazla posta kutusu sayısı. Temizleme eylemini yaptığınız aramada bu sınırdan daha fazla kaynak posta kutusu varsa temizleme eylemi başarısız olur. Arama ve temizleme hakkında daha fazla bilgi için bkz. [Kuruluşunuzda e-posta iletilerini arama ve silme](search-for-and-delete-messages-in-your-organization.md).|50,000|
|Aramada öğeleri dışarı aktarabileceğiniz en fazla konum sayısı. Dışarı aktardığınız aramanın bu sınırdan daha fazla konumu varsa dışarı aktarma işlemi başarısız olur. Daha fazla bilgi için bkz. [İçerik arama sonuçlarını dışarı aktarma](export-search-results.md).|100,000|

> [!NOTE]
> <sup>1</sup> Tek bir aramada sınırsız sayıda posta kutusunda arama yapabilirsiniz ancak dışarı aktarılan arama sonuçlarını yalnızca en fazla 100.000 posta kutusundan uyumluluk portalındaki eBulma Dışarı Aktarma Aracı'nı kullanarak indirebilirsiniz.
>
> <sup>2</sup> Önizleme sayfasının amacı, sonuçların sınırlı bir örneğini göstermektir. Binlerce sonuç içeren çok büyük aramalar için bile önizleme sayfasında gösterilen öğelerin sayısı 1000'in mümkün olan en yüksek değerinden çok daha az olabilir ve genellikle de olacaktır. Arama sonuçlarının tamamını görmek için sonuçları dışarı aktarmanız gerekir.
>
> <sup>3</sup> SharePoint ve OneDrive İş konumları ararken, aranmakta olan sitelerin URL'lerindeki karakterler bu sınıra göre sayılır.
>
> <sup>4</sup> Tümcecik olmayan sorgular için (çift tırnak işareti kullanmayan bir anahtar sözcük değeri) özel bir ön ek dizini kullanırız. Bu, bir sözcüğün belgede olduğunu, ancak belgede nerede olduğunu söylemediğini bildirir. Tümcecik sorgusu yapmak için (çift tırnak işaretli bir anahtar sözcük değeri), tümcecikteki sözcüklerin belge içindeki konumunu karşılaştırmamız gerekir. Başka bir deyişle, tümcecik sorguları için ön ek dizinini kullanamayız. Bu durumda, ön ekin genişletilmesi olası tüm sözcüklerle sorguyu dahili olarak genişletiriz; örneğin, `"time*"` öğesini olarak `"time OR timer OR times OR timex OR timeboxed OR ..."`genişletebilir. 10.000, sorguyla eşleşen belge sayısı değil, sözcüğün genişletebileceği en fazla değişken sayısıdır. Tümcecik olmayan terimler için üst sınır yoktur.

## <a name="search-times"></a>Arama süreleri

Microsoft, tüm kuruluşlar tarafından çalıştırılan aramalar için performans bilgileri toplar. Arama sorgusunun karmaşıklığı arama sürelerini etkileyebilir ancak aramaların ne kadar sürdüğünü etkileyen en büyük faktör, arama yapılan posta kutularının sayısıdır. Microsoft arama süreleri için bir Hizmet Düzeyi Sözleşmesi sağlamasa da, aşağıdaki tabloda aramaya dahil edilen posta kutularının sayısına göre koleksiyon aramaları için ortalama arama süreleri listelenmiştir.

<br>

****

|Posta kutusu sayısı|Ortalama arama süresi|
|---|---|
|100|30 saniye|
|1,000|45 saniye|
|10,000|4 dakika|
|25,000|10 dakika|
|50,000|20 dakika|
|100,000|25 dakika|

## <a name="export-limits"></a>Dışarı aktarma sınırları

Aşağıdaki tabloda, bir içerik aramasının sonuçları dışarı aktarılırken sınırlar listelenir. Bu sınırlar, eBulma (Standart) durumundan içerik dışarı aktardığınızda da geçerlidir.

<br>

****

|Sınırın açıklaması|Sınırı|
|---|---|
|Tek bir aramadan dışarı aktarılabilir maksimum veri miktarı  <p> **Not:** Arama sonuçları 2 TB'tan büyükse, arama sonuçlarının toplam boyutunu küçültmek için tarih aralıklarını veya diğer filtre türlerini kullanmayı göz önünde bulundurun.|2TB|
|Bir kuruluşun tek bir günde dışarı aktarabileceği maksimum değer <p> **Not:** Bu sınır her gün saat 12:00 UTC'de sıfırlanır|2TB|
|Kuruluşunuzda aynı anda kullanılabilecek en fazla eşzamanlı dışarı aktarma <p> **Not:** Yalnızca **Rapor** Çalıştırma, kuruluşunuz için toplam eşzamanlı dışarı aktarma sayısına karşılık gelen dışarı aktarma sayısını gösterir. Üç kullanıcı her biri 3 dışarı aktarma gerçekleştiriyorsa, yalnızca bir dışarı aktarma işlemi daha gerçekleştirilebilir. Bir raporu veya arama sonuçlarını dışarı aktarırken, tamamlanana kadar başka dışarı aktarma gerçekleştirilemez.|10|
|Tek bir kullanıcının herhangi bir anda çalıştırabileceği maksimum dışarı aktarma sayısı|3|
|eBulma Dışarı Aktarma Aracı kullanılarak indirilebilen arama sonuçları için en fazla posta kutusu sayısı|100,000|
|Dışarı aktarılabilir PST dosyasının boyutu üst sınırı <p> **Not:** Kullanıcının posta kutusundan gelen arama sonuçları 10 GB'tan büyükse, posta kutusunun arama sonuçları iki (veya daha fazla) ayrı PST dosyasında dışarı aktarılır. Tüm arama sonuçlarını tek bir PST dosyasında dışarı aktarmayı seçerseniz, arama sonuçlarının toplam boyutu 10 GB'tan büyükse PST dosyası ek PST dosyalarına aktarılır. Bu varsayılan boyutu değiştirmek istiyorsanız, arama sonuçlarını dışarı aktarmak için kullandığınız bilgisayarda Windows Kayıt Defteri'ni düzenleyebilirsiniz. Bkz. [eBulma arama sonuçlarını dışarı aktarırken PST dosyalarının boyutunu değiştirme](change-the-size-of-pst-files-when-exporting-results.md). Belirli bir posta kutusunun arama sonuçları, tek bir posta kutusunun içeriği 10 GB'tan fazla olmadığı sürece birden çok PST dosyası arasında bölünemez. Arama sonuçlarını tek bir klasördeki tüm iletileri içeren bir PST dosyasında dışarı aktarmayı seçtiyseniz ve arama sonuçları 10 GB'tan büyükse, öğeler yine kronolojik sırayla düzenlenir, bu nedenle gönderilmiş tarihe göre ek PST dosyalarına aktarılırlar.|10 GB|
|Posta kutularından ve sitelerden gelen arama sonuçlarının Microsoft tarafından sağlanan bir Azure Depolama konumuna yüklenme oranı.|Saatte en fazla 2 GB|

## <a name="indexing-limits-for-email-messages"></a>E-posta iletileri için dizin oluşturma sınırları

Aşağıdaki tabloda, bir e-posta iletisinin dizine alınmamış bir öğe veya içerik aramasının sonuçlarında kısmen dizine alınmış bir öğe olarak döndürülmesine neden olabilecek dizin oluşturma sınırları açıklanmaktadır.

<br>

****

|Dizin oluşturma sınırı|En büyük değer|Açıklama|
|---|---|---|
|En büyük ek boyutu|150 MB|Dizin oluşturma için ayrıştırılacak bir e-posta ekinin en büyük boyutu. Bu sınırdan daha büyük olan ekler dizin oluşturma için ayrıştırılamaz ve eki içeren ileti kısmen dizinlenmiş olarak işaretlenir. <p> **Not:** Ayrıştırma, dizin oluşturma hizmetinin ekten metin ayıkladığı, noktalama işaretleri ve boşluklar gibi gereksiz karakterleri kaldırdığı ve ardından metni daha sonra dizinde depolanan sözcüklere (belirteç oluşturma adı verilen bir işlemde) böldüğü işlemdir.|
|En fazla ek sayısı|250|Dizin oluşturma için ayrıştırılacak bir e-posta iletisine eklenen dosya sayısı üst sınırı. İletinin 250'den fazla eki varsa, ilk 250 ek ayrıştırılır ve dizine eklenir ve ayrıştırılmamış ekleri olduğundan ileti kısmen dizinlenmiş olarak işaretlenir.|
|En fazla ek derinliği|30|Ayrıştırılan iç içe ek sayısı üst sınırı. Örneğin, e-posta iletisine başka bir ileti ekliyse ve ekli iletide ekli bir Word belgesi varsa, Word belgesi ve ekli ileti dizine eklenir. Bu davranış en fazla 30 iç içe ek için devam eder.|
|Ekli görüntü sayısı üst sınırı|0|E-posta iletisine eklenmiş bir resim ayrıştırıcı tarafından atlanır ve dizine eklenmez.|
|Öğe ayrıştırma için harcanan en uzun süre|30 saniye|Bir öğeyi dizin oluşturmak için ayrıştırma için en fazla 30 saniye harcanıyor. Ayrıştırma süresi 30 saniyeyi aşarsa, öğe kısmen dizinlenmiş olarak işaretlenir.|
|En fazla ayrıştırıcı çıkışı|2 milyon karakter|Dizine alınan ayrıştırıcıdan elde edilen en fazla metin çıkışı miktarı. Örneğin, ayrıştırıcı bir belgeden 8 milyon karakter ayıkladıysa, yalnızca ilk 2 milyon karakter dizine eklenir.|
|En fazla ek açıklama belirteci|2 milyon|Bir e-posta iletisi dizine alındığında, her sözcük, söz konusu sözcüğün nasıl dizinleneceğini belirten farklı işleme yönergeleriyle ek açıklama ekler. Her işleme yönergeleri kümesi ek açıklama belirteci olarak adlandırılır. Office 365'da hizmet kalitesini korumak için e-posta iletisi için 2 milyon ek açıklama belirteci sınırı vardır.|
|Dizindeki en büyük gövde boyutu|67 milyon karakter|E-posta iletisinin gövdesindeki toplam karakter sayısı ve tüm ekleri. Bir e-posta iletisi dizine alındığında, iletinin gövdesindeki ve tüm eklerdeki tüm metinler tek bir dizede birleştirilir. Dizine alınan bu dizenin en büyük boyutu 67 milyon karakterdir.|
|Gövdedeki en büyük benzersiz belirteç sayısı|1 milyon|Daha önce açıklandığı gibi belirteçler, içerikten metin ayıklamanın, noktalama işaretlerini ve boşlukları kaldırmanın ve ardından dizinde depolanan sözcüklere (belirteç olarak adlandırılır) bölünmesinin sonucu olur. Örneğin, tümcecik `"cat, mouse, bird, dog, dog"` 5 belirteç içerir. Ancak bunların yalnızca 4'ünün benzersiz belirteçleri vardır. E-posta iletisi başına 1 milyon benzersiz belirteç sınırı vardır ve bu da dizinin rastgele belirteçlerle fazla büyük olmasını önlemeye yardımcı olur.|
|||

## <a name="more-information"></a>Daha fazla bilgi

İçerik aramanın içerik dizini oluşturma gibi farklı yönleriyle ilgili ek sınırlar vardır. Bu sınırlar hakkında daha fazla bilgi için aşağıdaki konulara bakın:

- [İçerik Arama'da kısmen dizine alınan öğeler](partially-indexed-items-in-content-search.md)

- [eBulma'da kısmen dizine alınan öğeleri araştırma](investigating-partially-indexed-items-in-ediscovery.md)

- [SharePoint Online için arama sınırları](/sharepoint/search-limits)

İçerik aramaları hakkında bilgi için bkz:

- [Microsoft 365'da içerik arama](content-search.md)

- [eBulma (Standart) durumunda içerik arama](search-for-content-in-core-ediscovery.md)

- [İçerik arama için anahtar sözcük sorguları ve arama koşulları](keyword-queries-and-search-conditions.md)

eBulma (Standart) ve eBulma (Premium) ile ilgili durum sınırları için bkz:

- [eBulma sınırları (Standart)](limits-core-ediscovery.md)

- [eBulma sınırları (Premium)](limits-ediscovery20.md)
