---
title: Uyumluluk merkezinde İçerik arama ve Çekirdek eKbulma sınırları
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
description: İçerik arama ve Temel eKbulma özellikleri için sonuçların nasıl etkili olduğunu Microsoft 365 uyumluluk merkezi.
ms.openlocfilehash: ad72dfa1d599a908a56b3b6530433ccb5ed23df4
ms.sourcegitcommit: 46456ca009c9d50622e57e24269be74986184654
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/22/2022
ms.locfileid: "63715960"
---
# <a name="limits-for-ediscovery-search"></a>eBulma araması için sınırlar

eBulma arama araçlarına, çalışma sayfalarında çeşitli Microsoft 365 uyumluluk merkezi. Buna, İçerik arama sayfasında **yapılan** aramalar ve **Core eKovery** sayfasındaki bir eBulma durumuyla ilişkili aramalar da dahildir. Bu sınırlar, kuruluşlara sağlanan hizmetlerin durumunu ve kalitesini korumaya yardımcı olur. Ayrıca, e-posta iletileri dizini oluşturma ve arama için Exchange Online de vardır. eBulma aramaları veya e-posta dizin oluşturma sınırlarını değiştiremezsiniz, ancak eBulma aramalarını planlar, çalıştırma ve sorun giderme adımlarında bu sınırları göz önünde bulundurabilirsiniz.

Yeni Araç Aracı ile ilgili Advanced eDiscovery için bkz. Alan [Advanced eDiscovery](limits-ediscovery20.md)

## <a name="search-limits"></a>Arama sınırları

Aşağıdaki tabloda, çalışma sayfalarında içerik arama aracını kullanırken Microsoft 365 uyumluluk merkezi Çekirdek eKbulma durumuyla ilişkili aramalar için arama sınırları listeledir.

<br>

****

|Sınırın açıklaması|Sınır|
|---|---|
|Tek bir aramada aranacak posta kutusu veya site sayısı üst sayısı|Sınır yok <sup>1</sup>|
|En fazla, kurum içinde aynı anda çalıştırabilirsiniz.|30|
|Aynı anda çalıştır yalnızca kuruluş çapında en fazla arama sayısı.|3|
|Tek bir kullanıcının aynı anda başlat olduğu en fazla arama sayısı. Bu sınır büyük olasılıkla, kullanıcı Güvenlik ve Uyumluluk Merkezi PowerShell'in **Get-ComplianceSearch \|Start-ComplianceSearch** komutunu kullanarak birden çok arama başlatmaya çalıştığında & olur.|10|
|İçerik Arama sonuçlarının önizlemesi sırasında önizleme sayfasında kullanıcı posta kutusu başına en fazla öğe sayısı.|100|
|Tüm kullanıcı posta kutularında bulunan ve arama sonuçlarının önizlemesi sırasında büyük olasılıkla önizleme sayfasında görüntülen muhtemel öğe sayısı üst sayısı. En yeni öğeler görüntülenir.|1.000 <sup>2</sup>|
|Arama sonuçları için önizlemede 2013'e kadar olan kullanıcı posta kutusu sayısı üst sayısı. Arama sorgusuyla eşleşen içerik içeren 1000'den fazla posta kutusu varsa, önizleme için yalnızca en çok arama sonuçlarına sahip ilk 1000 posta kutusu kullanılabilir.|1,000|
|Arama sonuçlarının önizlemesi sırasında SharePoint ve OneDrive İş sitelerinde bulunan en fazla öğe sayısı. En yeni öğeler görüntülenir.|200|
|Arama sonuçları için önizlemede SharePoint ve OneDrive İş site sayısı üst sayısı. Arama sorgusuyla eşleşen içerik içeren toplam 200'den fazla site varsa, önizleme için yalnızca en çok arama sonucu içeren ilk 200 site kullanılabilir.|200|
|İçerik arama sonuçlarının önizlemesi sırasında önizleme sayfasında görüntülenen ortak klasör posta kutusu başına en fazla öğe sayısı.|100|
|İçerik arama sonuçlarının önizlemesi sırasında önizleme sayfasında görüntülenen tüm ortak klasör posta kutularında bulunan en fazla öğe sayısı.|200|
|Arama sonuçları için önizlemede 2013 ortak klasör posta kutusu sayısı üst). Arama sorgusuyla eşleşen içerik içeren 500'den fazla ortak klasör posta kutusu varsa, önizleme için yalnızca en çok arama sonuçlarına sahip ilk 500 ortak klasör posta kutusu kullanılabilir.|500|
|Önizleme sayfasında görüntülenen öğe boyutu için üst boyut.|10.000.000 bayt (yaklaşık 9,5 MB)|
|Arama sorgusu için karakter sayısı üst sayısı (işleçler ve koşullar dahil) <p> **Not:** Bu sınır, sorgu genişletildikten sonra etkili olur ve anahtar sözcük sorgusundan gelen karakterleri, kullanıcıya uygulanan tüm arama izinleri filtrelerini ve tüm site konumlarının URL'lerini içerir. Bu, sorgunun anahtar sözcüklerin her biri için genişletilecek olduğu anlamına gelir. Örneğin, bir arama sorgusunda 15 anahtar sözcük ve ek parametre ve koşullar varsa, sorgu 15 kez, sorgunun diğer parametreleri ve koşullarıyla birlikte 15 kez genişletilir. Dolayısıyla, arama sorgusunun karakter sayısı sınırın altında olsa da, bu sınırı aşmaya katkı sağlayacak genişletilmiş sorgudur.|**Posta kutuları:** 10.000. <p> **Siteler:** Tüm sitelerde 4.000 veya 20 siteyi ararken 2.000 adet. <sup>3</sup>|
|Arama sorgusunda tam bir tümcecik aramak için ön ek joker karakteri kullanırken veya ön ek joker karakteri ve **NEAR** Boole işleci kullanırken döndürülen en fazla değişken sayısı.|10.000 <sup>4</sup>|
|Ön ek joker karakterleri için en az alfa karakteri sayısı; örneğin, `time*`, `one*`veya `set*`.|3|
|"Arama ve temizleme" eylemi yaparak ( **New-ComplianceSearchAction -Temizleme** komutunu kullanarak) bir aramadaki öğeleri silebilirsiniz. Temizleme eylemini yerine kendi aramanız için bu sınırdan daha fazla kaynak posta kutusu varsa, temizleme eylemi başarısız olur. Arama ve temizleme hakkında daha fazla bilgi için bkz. [Kurumda e-posta iletilerini arama ve silme](search-for-and-delete-messages-in-your-organization.md).|50,000|
|Öğeleri dışarı aktarabilirsiniz ve aramada en fazla konum sayısı. Dışarı aktarıyorsanız aramanın bu sınırdan daha fazla konumu varsa, dışarı aktarma başarısız olur. Daha fazla bilgi için bkz [. İçerik arama sonuçlarını dışarı aktarma](export-search-results.md).|100,000|

> [!NOTE]
> <sup>1</sup> Tek bir aramada sınırsız sayıda posta kutusu arayabilirsiniz, ancak aynı veri kaynağında eBulma Dışarı Aktarma Aracı'nı kullanarak dışarı aktarmış arama sonuçlarını en çok 100.000 posta kutusundan Microsoft 365 uyumluluk merkezi.
>
> <sup>2</sup> Önizleme sayfasının amacı, sonuçların sınırlı bir örneğini göstermektir. Binlerce sonuçla yapılan muazzam aramalar için bile önizleme sayfasında gösterilen öğelerin sayısı ve çoğunlukla olası en fazla 1000 değerden çok daha az olabilir. Tüm arama sonuçlarını görmek için, sonuçları dışarı aktarmanız gerekir.
>
> <sup>3</sup> Arama SharePoint konumlarda OneDrive İş, arama yapılan sitelerin URL'lerinde yer alan karakterler bu sınıra göre sayılır.
>
> <sup>4</sup> Tümceciksiz sorgular için (çift tırnak işareti kullanmayan bir anahtar sözcük değeri) özel bir ön ek dizini kullanıruz. Bu bize bir sözcüğün belgede oluştuğuni ama belgenin içinde bulunduğu yeri değil, belge içinde yer alan yeri gösterir. Bir tümcecik sorgusu yapmak için (çift tırnak işaretleri içeren bir anahtar sözcük değeri), tümceciğin sözcükleri için belge içindeki konumu karşılaştırmamız gerekir. Bu, tümcecik sorguları için ön ek dizinini kullanalememız anlamına gelir. Bu durumda, sorguyu, ön ekin genişletilen tüm olası sözcüklerle dahili olarak genişleteceğiz; örneğin, `"time*"` 'a genişlet olabilir `"time OR timer OR times OR timex OR timeboxed OR ..."`. 10.000, sözcüğün sorguyla eşleşen belge sayısıyla değil, genişletilen değişken sayısı üst sayısıdır. Tümcecik olmayan terimler için üst sınır yoktur.

## <a name="search-times"></a>Arama saatleri

Microsoft, tüm kuruluşların yaptığı aramalar için performans bilgilerini toplar. Arama sorgusunun karmaşıklığı arama sürelerini etkileyebilir, ancak aramaların ne kadar süreyle devamyeceğini etkileyen en büyük faktör, arama yapılan posta kutularının sayısıdır. Microsoft, arama süreleri için Bir Hizmet Düzeyi Sözleşmesi sağlamasa da, aşağıdaki tabloda, aramada yer alan posta kutularının sayısına göre koleksiyon aramalarının ortalama arama süreleri listelemektedir.

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

Aşağıdaki tabloda, içerik arama sonuçları dışarı aktarıldı ancak sınırlar listele. Bu sınırlar, Core eKovery durumundan içerik dışarı aktarabilirsiniz.

<br>

****

|Sınırın açıklaması|Sınır|
|---|---|
|Tek bir aramadan dışarı aktarılabilir en fazla veri miktarı  <p> **Not:** Arama sonuçları 2 TB'dan büyükse, arama sonuçlarının toplam boyutunu azaltmak için tarih aralıklarını veya diğer filtre türlerini kullanmayı göz önünde bulundurabilirsiniz.|2 TB|
|Bir kuruluş için en fazla bir günde dışarı aktar <p> **Not:** Bu sınır, UTC ile her gün 12:00'de sıfırlanır|2 TB|
|En fazla eşzamanlı dışarı aktarma, kuruluş içinde aynı anda çalıştırabilirsiniz <p> **Not:** Yalnızca Rapor **dışarı aktarma** sayısı, kurum için toplam eşzamanlı dışarı aktarma sayılarını çalıştırma. Her biri 3 kullanıcı dışarı aktarma işlemi yapıyorsa, yalnızca bir kullanıcı dışarı aktarma işlemi yapılabilir. Rapor veya arama sonuçları dışarı aktarsa bile, biri tamamlanana kadar başka dışarı aktarma işlemi gerçekleştirilamaz.|10|
|Tek bir kullanıcı için en fazla dışarı aktarma aynı anda çalıştırabilirsiniz|3|
|eBulma Dışarı Aktarma Aracı kullanılarak indirilebilen arama sonuçları için en fazla posta kutusu sayısı|100,000|
|Dışarı aktarıla en fazla PST dosyası boyutu <p> **Not:** Kullanıcının posta kutusunun arama sonuçları 10 GB'tan büyükse, posta kutusunun arama sonuçları iki (veya daha fazla) ayrı PST dosyasına dışarı aktar edilir. Tüm arama sonuçlarını tek bir PST dosyasında dışarı aktarmayı seçerseniz, arama sonuçlarının toplam boyutu 10 GB'tan büyükse PST dosyası ek PST dosyalarına bu dosya olarak depolamanız gerekir. Bu varsayılan boyutu değiştirmek için, arama sonuçlarını dışarı Windows bilgisayarda Windows Defteri'ni düzenleyebilirsiniz. Bkz [. eBulma arama sonuçlarını dışarı aktararak PST dosyalarının boyutunu değiştirme](change-the-size-of-pst-files-when-exporting-results.md). Tek bir posta kutusunun içeriği 10 GB'tan fazla olmadığı sürece, belirli bir posta kutusunun arama sonuçları birden çok PST dosyasına bölünmez. Arama sonuçlarını, tüm iletileri tek bir klasörde yer alan ve arama sonuçlarının 10 GB'tan büyük olduğu için tek bir PST dosyasında dışarı aktarmayı seçtiysiniz ve arama sonuçları hala kronolojik sırada düzenleniyor ve bu nedenle gönderilen tarihe göre ek PST dosyalarına toslar.|10 GB|
|Posta kutuları ve sitelerden gelen arama sonuçlarının Microsoft tarafından sağlanan bir Azure depolama Depolama oranı.|Saatte en fazla 2 GB|

## <a name="indexing-limits-for-email-messages"></a>E-posta iletileri için dizin sınırları

Aşağıdaki tabloda, içerik aramanın sonuçlarında e-posta iletisinin dizine alınmayacak öğe veya kısmen dizine alınmış bir öğe olarak döndürülebilir olmasıyla sonuçlandıracak dizin oluşturma sınırları açık almaktadır.

<br>

****

|Dizin oluşturma sınırı|En büyük değer|Açıklama|
|---|---|---|
|En büyük ek boyutu|150 MB|Dizin oluşturma için ayrıştıracak en büyük e-posta eki boyutu. Bu sınırdan büyük olan hiçbir ek dizin oluşturma için ayrıştırılamaz ve ekin olduğu ileti kısmen dizine alındı olarak işaretlenir. <p> **Not:** Ayrıştırma, dizin oluşturma hizmetinin ekten metni ayıklar, noktalama işaretleri ve boşluklar gibi gereksiz karakterleri kaldıran ve sonra metni, daha sonra dizinde depolanan sözcüklere bölen (belirteç oluşturma adı verilen bir işlemde) süreçtir.|
|En fazla ek sayısı|250|Dizin oluşturma için ayrıştıracak e-posta iletisine eklenen dosya sayısı üst sayısı. Bir iletide 250'den fazla ek varsa, ilk 250 ek ayrıştırıldı ve dizine alındı; ileti, ayrıştırnmış olan başka ekler de olduğundan kısmen dizine alındı olarak işaretlenir.|
|En fazla ek derinliği|30|Ayrıştırıla en fazla iç içe ek sayısı. Örneğin, e-posta iletisine eklenmiş başka bir ileti varsa ve bu iletide de ek olarak bir Word belgesi varsa, Word belgesi ve ekli ileti dizine alır. İç içe 30 eke kadar bu davranış devam eder.|
|En fazla ekli resim sayısı|0|E-posta iletisine eklenmiş olan resim ayrıştırıcı tarafından atlanır ve dizine alınmz.|
|Öğeyi ayrıştırmak için harcanan en fazla zaman|30 saniye|Bir öğeyi dizin oluşturma için ayrıştırmak için en fazla 30 saniye harcandı. Ayrıştırma süresi 30 saniyeyi aşarsa, öğe kısmen dizine alındı olarak işaretlenir.|
|En fazla ayrıştırıcı çıktısı|2 milyon karakter|Ayrıştırıcıdan gelen metin çıktılarından dizine alan en yüksek miktardır. Örneğin, ayrıştırıcı bir belgeden 8 milyon karakter ayıklamışsa, yalnızca ilk 2 milyon karakter dizine alındı.|
|En fazla ek açıklama belirteci|2 milyon|E-posta iletisi dizine alınca, her söz ek açıklamayla birlikte bu sözcüğün nasıl dizine alın olacağını belirten farklı işleme yönergeleri ek açıklamalır. Her işleme yönergeleri kümesine ek açıklama belirteci denir. Bir e-posta iletisinde Office 365 kalitesini korumak için, bir e-posta iletisinde 2 milyon ek açıklama belirteci sınırı vardır.|
|Dizinde en büyük gövde boyutu|67 milyon karakter|E-posta iletisi gövdesiyle tüm eklerinin toplam karakter sayısı. E-posta iletisi dizine alınca, iletinin gövdesinde ve tüm eklerde yer alan metnin hepsi tek bir dizede bir biri haline gönderilir. Dizine alan bu dizenin boyut üst değeri 67 milyon karakterdir.|
|Gövdede en fazla benzersiz belirteç sayısı|1 milyon|Daha önce de açıklandığı gibi, belirteçler içerikten metnin ayıklanır, noktalama işaretleriyle boşlukların kaldırılması ve dizinde depolanan sözcüklere (belirteç adı verilen sözcüklere) bölünmesi sonucu elde edilir. Örneğin, tümcecik `"cat, mouse, bird, dog, dog"` 5 belirteç içerir. Ama bunların yalnızca 4'ü benzersiz belirteçtir. E-posta iletisi başına 1 milyon benzersiz belirteç sınırı vardır ve bu sınır dizinin rastgele belirteçlerle çok fazla fazla şey oluşturmasını engellemeye yardımcı olur.|
|||

## <a name="more-information"></a>Daha fazla bilgi

İçerik aramanın farklı yönleriyle (içerik dizini oluşturma gibi) ilgili ek sınırlar vardır. Bu sınırlar hakkında daha fazla bilgi için aşağıdaki konu başlıklarına bakın:

- [İçerik Arama'da kısmen dizine alan öğeler](partially-indexed-items-in-content-search.md)

- [eBulma'da kısmen dizine alan öğeleri inceleme](investigating-partially-indexed-items-in-ediscovery.md)

- [SharePoint Online için arama sınırları](/sharepoint/search-limits)

İçerik aramaları hakkında bilgi için bkz:

- [web'de içerik Microsoft 365](content-search.md)

- [Core eKovery durumunda içerik arama](search-for-content-in-core-ediscovery.md)

- [İçerik arama için anahtar sözcük sorguları ve arama koşulları](keyword-queries-and-search-conditions.md)

Core eDiscovery ve Advanced eDiscovery ilgili olay sınırları için bkz:

- [Çekirdek eKbulma sınırlamaları](limits-core-ediscovery.md)

- [Alan Advanced eDiscovery](limits-ediscovery20.md)
