---
title: İçerik Arama'da ve diğer eBulma araçlarında kısmen dizine alınan öğeler
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
f1_keywords:
- ms.o365.cc.UnindexedItemsLearnMore
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- SPO160
- MOE150
- MET150
ms.assetid: d1691de4-ca0d-446f-a0d0-373a4fc8487b
description: Takvim ve takvim Exchange SharePoint, çalışma SharePoint bir eBul Microsoft 365 uyumluluk merkezi ma aramalarına ekyebilirsiniz.
ms.openlocfilehash: b1adfaab1008cdfa9e7893273feaba38a71e85ac
ms.sourcegitcommit: bb493f12701f6d6ee7d5e64b541adb87470bc7bc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/18/2022
ms.locfileid: "63015486"
---
# <a name="partially-indexed-items-in-ediscovery"></a>eBulma'da kısmen dizine alan öğeler

Arama sonuçlarından çalıştırmış Microsoft 365 uyumluluk merkezi, bir arama Microsoft 365 uyumluluk merkezi tahmin edilen arama sonuçlarına kısmen dizine alan öğeleri otomatik olarak dahil eder. Kısmen dizine alınan Exchange, SharePoint ve OneDrive İş sitelerinden posta kutusu öğeleriyle belgelerine, bazı nedenlerden dolayı arama için tamamen dizine alınmmış değil. Dizin Exchange kısmen dizine alan bir öğe normalde e-posta iletisine eklenmiş bir dosya (dizine alınamıyor dosya türünde) içerir. Burada, arama için öğelerin dizine alamama ve eBulma aramalarını çalıştırmanızı kısmen dizine alan öğeler olarak döndürül nedenleri ve bunların başka nedenleri vardır:
  
- Dosya türü dizin oluşturma için tanınmıyor veya desteklenmiyor.

- İletilerin resim dosyaları gibi açılamıyor bir ekli dosyası vardır; kısmen dizine alınmış e-posta öğelerinin en yaygın nedeni bu olur.

- Dosya türü dizin oluşturma için destekle birlikte, belirli bir dosya için dizin oluşturma hatası oluştu.

- E-posta iletisine eklenmiş çok fazla dosya var.

- E-posta iletisine eklenen dosya çok büyük.

- Dosya, Microsoft olmayan teknolojilerle şifrelenir.

- Dosya parola korumalıdır.

> [!NOTE]
> Çoğu kuruluş içerik hacmine göre %1'den aza, kısmen dizine alan boyuta göre %12'den küçük içeriğe sahip olur. Ses düzeyi ile boyut arasındaki farkın nedeni, daha büyük dosyaların tamamen dizine alamayacak içerik içerik olasılığı daha yüksek olmasıdır.
  
Yasal soruşturmalar için, kuruluşta kısmen dizine alınan öğeleri gözden geçirmesi gerekebilir. Ayrıca, arama sonuçlarını yerel bir bilgisayara dışarı aktarıyorsanız veya sonuçları çözümleme için hazırlarken kısmen dizine alan öğelerin ek isteyip Advanced eDiscovery. Daha fazla bilgi için bkz [. eBulma'da kısmen dizine alınan öğeleri araştırma](investigating-partially-indexed-items-in-ediscovery.md).
  
## <a name="file-types-not-indexed-for-search"></a>Arama için dizine alındı dosya türleri

Bit eşlem veya MP3 dosyaları gibi bazı dosya türleri dizine alanın içerik içermez. Sonuç olarak, Exchange ve SharePoint dosyalarında tam metin dizin oluşturma işlemi gerçekleştirmezler. Bu tür dosyaların desteklenmeyen dosya türleri olduğu kabul edilir. Ayrıca, varsayılan olarak veya yönetici tarafından tam metin dizininin devre dışı bırakılmıştır. Desteklenmeyen ve devre dışı bırakılmış dosya türleri İçerik Aramalarında dizine eksiz öğeler olarak etiketlenmiş. Daha önce de belirtildiği gibi, bir arama çalıştırılan, arama sonuçlarını yerel bir bilgisayara dışarı aktaran veya arama sonuçlarını hazırlarken kısmen dizine alan öğeler, arama sonuçları kümesine Advanced eDiscovery.
  
Desteklenen ve devre dışı bırakılmış dosya biçimlerinin listesi için aşağıdaki konulara bakın:
  
-  -  Exchange [Search tarafından dizine alan Exchange biçimleri](/exchange/file-formats-indexed-by-exchange-search-exchange-2013-help)

-  -  Exchange [Get-SearchDocumentFormat](/powershell/module/exchange/get-searchdocumentformat)

-  -  SharePoint [Default'da gezinilen dosya adı uzantılarını ve ayrıştırıldı dosya türlerini SharePoint](/SharePoint/technical-reference/default-crawled-file-name-extensions-and-parsed-file-types)
  
## <a name="messages-and-documents-with-partially-indexed-file-types-can-be-returned-in-search-results"></a>Kısmen dizine alındı dosya türlerine sahip iletiler ve belgeler arama sonuçlarında döndürül olabilir

Kısmen dizine ekli dosya eki olan veya kısmen dizine alan her e-SharePoint belge, otomatik olarak kısmen dizine alınmış bir öğe olarak döndürülür. Çünkü e-posta iletilerde Konu özelliği ve belgelerin Başlık veya **Yazar** özellikleri dizine alınarak aranma  özelliği kullanılabilir. Örneğin, "financial" anahtar sözcüğü araması, bu anahtar sözcük bir e-posta iletisi konu başlığında ya da bir belgenin dosya adı veya başlığında görünürse, kısmen dizine alındı dosyası ekli öğeleri geri alır. Öte yandan, anahtar sözcük yalnızca dosyanın gövdesinde görünüyorsa, ileti veya belge kısmen dizinelenmiş bir öğe olarak döndürülür.
  
Benzer şekilde, kısmen dizine alınan dosya ekleri olan iletiler ve kısmen dizine alınan dosya türünün belgeleri, dizine alınan ve aranabilir olan diğer ileti veya belge özellikleri arama ölçütlerine uygun olduğunda, arama sonuçlarına dahil edilir. Arama için dizine alınan ileti özellikleri arasında gönderme ve alındı tarihleri, gönderen ve alıcı, ekin dosya adı ve ileti gövdesine metin yer alır. Arama için dizine alan belge özellikleri, oluşturulma ve değiştirilme tarihlerini içerir. Dolayısıyla, ileti eki kısmen dizine alınan bir öğe olsa bile, diğer iletinin veya belge özelliklerinin değeri arama ölçütleriyle eş görünüyorsa ileti normal arama sonuçlarına dahil edilir.
  
EBulma araçlarını kullanarak arayabilirsiniz e-posta ve belge özelliklerinin listesi için Microsoft 365 uyumluluk merkezi bkz. eBulma için anahtar sözcük sorguları ve arama [koşulları](keyword-queries-and-search-conditions.md).
  
> [!NOTE]
> Posta kutusu öğesi dizine alınmış klasörden dizine alınmış bir klasörden taşınırsa, öğenin dizinini kaldıracak şekilde bir bayrak ayarlanır ve öğe dizinden kaldırılır ve aranamaz. Daha sonra aynı öğe yeniden dizine alan bir klasöre taşınırsa, bayrak sıfırlanmaz. Bu, öğenin satırsız kalacak ve aranamaz durumda olduğu anlamına gelir.

## <a name="partially-indexed-items-included-in-the-search-results"></a>Arama sonuçlarına kısmen dizine alan öğeler

Kuruluşta ne olduğunu, ne içerdiğini ve belirli bir araştırmayla ilgili olup olmadığını belirlemek üzere kısmen dizine alan öğeleri tanımlamak ve bunlar üzerinde ek çözümlemeler yapmak gerekebilir. Daha önce de belirtildiği gibi, arama yapılan içerik konumlarında kısmen dizine alan öğeler, tahmini arama sonuçlarına otomatik olarak eklenir. Arama sonuçlarını dışarı aktarıyorsanız veya arama sonuçlarını hazırlarken kısmen dizine alan bu öğeleri Advanced eDiscovery.
  
Kısmen dizine alan öğelerle ilgili olarak aşağıdakini unutmayın:
  
- eBulma aramanızı çalıştırarak, kısmen dizine alan Exchange öğelerinin (arama sorgusu tarafından döndürülen) toplam sayısı ve boyutu, çıkış sayfasındaki arama istatistiklerinde görüntülenir ve dizine eksiz öğeler olarak **etiketli olur**. Uç öğe sayfasında görüntülenen kısmen dizine alınan öğelerle ilgili istatistikler, özel sitelerde veya SharePoint hesaplarında kısmen dizine OneDrive içermemektedir.

- Sonuçları dışarı aktarıyorsanız arama, belirli içerik konumlarında veya organizasyondaki tüm içerik konumlarında yapılan bir arama ise, yalnızca içerik konumlarından gelen ve arama ölçütleriyle eşleşmesi gereken öğeler içeren, tek tek sayfalık olmayan öğeler dışarı aktarıldı. Başka bir deyişle, bir posta kutusunda veya sitede hiç arama sonucu bulunamıyorsa, bu posta kutusu veya sitedeki tek hiçbirinde olmayan öğeler dışarı aktar olmaz. Bunun nedeni, kuruluşta birçok konumdan kısmen dizine alındı olarak dizine alan öğelerin dışarı aktarma işlemi, dışarı aktarma hataları olasılığını artırabilir ve arama sonuçlarını dışarı aktarma ve indirme için gereken zamanı artıracaktır.

    Kısmen dizine alınan öğeleri aramanın tüm içerik konumlarından dışarı aktarma için, aramanızı tüm öğeleri sonuç olarak geri dönecek şekilde yapılandırın (arama sorgusundan tüm anahtar sözcükleri kaldırarak) ve ardından arama sonuçlarını dışarı aktarıldığında yalnızca kısmen dizine alınan öğeleri dışarı aktarın (Yalnızca tanınmayan biçime sahip öğeler'e tıklayarak **,** Çıktı seçenekleri'nin altında şifrelenmiş veya dizine eklenmemiş diğer nedenlerden **dolayı).**

- Arama sonuçlarına tüm posta kutusu öğelerini dahil etme seçeneğini kullanırsanız veya arama sorgusu hiçbir anahtar sözcük belirtmezseniz veya yalnızca bir tarih aralığı belirtirse, kısmen dizine alınan öğeler kısmen dizine alınan öğeleri içeren PST dosyasına kopyalanamaz. Bunun nedeni, kısmen dizine alınan öğeler de dahil olmak üzere tüm öğelerin normal arama sonuçlarına otomatik olarak dahil olmasıdır.

- Kısmen dizine alan öğeler önizleme için kullanılamaz. Arama tarafından döndürülen kısmen dizine alındı öğeleri görüntülemek için arama sonuçlarını dışarı aktarmalısiniz.

   Buna ek olarak, arama sonuçlarını dışarı aktarıyor ve dışarı aktarmada kısmen dizine alan öğeler de dahil SharePoint dizine alan öğeler, "**Uncrawlable" adlı bir klasöre dışarı aktarılabilir**. Kısmen dizine sahip öğeleri Exchange, kısmen dizine alan öğelerin arama sorgusuyla ve dışarı aktarma ayarlarının yapılandırmasıyla eşleşmese de bunlar farklı şekilde dışarı aktarıldı. 

- Aşağıdaki tablo, dizinli ve kısmen dizine alan öğelerin dışarı aktarma davranışını ve her öğenin farklı dışarı aktarma yapılandırma ayarlarına ekli olup olmadığını gösterir.

  |**Yapılandırmayı dışarı aktarma**|**Arama sorgusuyla eşan dizine alındı**|**Arama sorgusuyla eşan, kısmen dizine alan öğeler**|**Arama sorgusuyla eşleşmeen kısmen dizine alındı**|
  |:-----|:-----|:-----|:-----|
  |Yalnızca dizine alındı öğeleri dışarı aktarma  <br/> |Dışarı aktarıldı<br/> |Dışarı aktarıldı (dışarı aktaran dizine sahip öğelerle birlikte)<br/>  |Dışarı aktarıldı <br/>|
  |Yalnızca kısmen dizine alan öğeleri dışarı aktarma  <br/> |Dışarı aktarıldı  <br/> |Dışarı aktarıldı (kısmen dizine alındı olarak)<br/> |Dışarı aktarıldı (kısmen dizine alındı olarak)|
  |Dizine alındı ve kısmen dizine alındı öğeleri dışarı aktarma  <br/> |Dışarı aktarıldı<br/> |Dışarı aktarıldı (dışarı aktaran dizine sahip öğelerle birlikte)<br/>  |Dışarı aktarıldı (kısmen dizine alındı olarak)<br/>|
  ||||
  
## <a name="workaround-for-using-a-date-range-to-exclude-partially-indexed-items"></a>Kısmen dizine alınmamış öğeleri dışarıda tutmak için tarih aralığı kullanmak için geçici çözüm

İçerik arama ve Çekirdek eKbulma'da, kısmen dizine alan öğelerin arama sorgusu tarafından döndürülerek hariç tutulacak şekilde tarih aralığını kullanamayabilirsiniz. Başka bir deyişle, tarih aralığının dışından düşen kısmen dizine alınan öğeler, arama istatistiklerine kısmen dizine alınan öğeler olarak ve kısmen dizine alınan öğeleri dışarı aktarıyor olun. Bu Advanced eDiscovery, arama sorgusunda tarih aralığı kullanarak kısmen dizine alan öğeleri hariç tutabilirsiniz.

Bu sınırlamaya geçici bir çözüm olarak aşağıdaki yordamı öneririz.

1. Gereksinimlerinizi karşılayacak ve istenen sonuçları döndüren bir arama sorgusu kullanarak arama oluşturun ve çalıştırın.

2. 1. adımda arama sonuçlarını dışarı aktarın, ancak dışarı aktarmaya kısmen dizine ekli öğeleri dahil etme. Bunu yapmak için, tanınmayan biçime sahip olanlar, şifrelenmiş veya dizine henüz dizine almamış olanlar hariç olmak üzere Tüm **öğeler'i** seçmeniz gerekir. <sup>1</sup>

   ![Çıkış seçeneklerini dışarı aktarma.](../media/ExportOutputOptions.png)

3. 1. adımda aynı arama sorgusunu kullanan (ve aynı konumlarda aramalar) kullanan ikinci bir arama oluşturun ve çalıştırın. AND işlecini kullanarak aşağıdaki yan tümceyi özgün **sorguya** ekler:

   ```text
   <original query> AND ((IndexingErrorCode>0 OR IndexingErrorCode<0) AND sent:date1..date2)
   ```

   Bu yan tümce ek getirerek, özgün arama sorgunuzla ve belirli bir tarih aralığı içinde yer alan kısmen dizine alındı öğeleri döner. <sup>2</sup>

4. 3. adımda arama sonuçlarını dışarı aktarın ve bu kez dışarı aktarmada kısmen dizine alındı öğeleri içerir. Bunu yapmak için, Tanınmayan biçime sahip olanlar, şifrelenmiş veya dizine henüz dizine almamış olanlar da dahil olmak üzere tüm öğeler öğesini seçerek dışarı **aktarma seçeneğini** belirtin.

   > [!NOTE]
   > <sup>1</sup> 2. adımın çıkışı yalnızca dizine alındı öğeleri dışarı aktarmayla sonuç verir.<br/>
   > <sup>2</sup> 3. adımda kullanılan koşul yalnızca belirtilen tarih aralığı içinde olan dizin oluşturma hatalarına sahip öğeleri tanımlar. Tümüyle dizine alınan hiçbir öğe geri dönmez. Bu, 4. adımda dışarı aktar geçen öğelerin yalnızca tarih aralığı içinde yer alan, tekinde olmayan öğeleri içermesi anlamına gelir. Dışarı aktarma, dizine alındı öğeleri içermez. Sonuç olarak, 2. ve 4. adımın birleştirilmiş çıktısı, belirtilen tarih aralığı içinde bulunan dizine alındı ve dizine eksiz tüm öğeleri içerir.

İlk arama sorgunuzla kısmen dizine oluşturulmuş öğeleri görüntülemek ve anlamak için, 3. adımda oluşturduğunuz ikinci arama ve karşılık gelen dışarı aktarmayı kullanın. İkinci aramadan dışarı aktarma, gerekirse gözden geçirebilirsiniz ve böylece dışarı aktarmış kısmen dizine alınmış tüm öğeleri de içerir.

> [!TIP]
> Önceki yordamda, gerçek arama sonuçlarını dışarı aktarabilirsiniz veya yalnızca raporu dışarı aktarabilirsiniz.

## <a name="indexing-limits-for-messages"></a>İletiler için dizin oluşturma sınırları

Aşağıdaki tabloda, e-posta iletisinin, Microsoft 365'te eBulma aramada kısmen dizine alınmış bir öğe olarak döndürülebilir olmasıyla sonuçlandıracak dizin oluşturma sınırları Microsoft 365.
  
Belgeleriniz için dizin oluşturma sınırlarının listesi SharePoint bkz[. SharePoint Online için arama sınırları](/sharepoint/search-limits).
  
|**Dizin oluşturma sınırı**|**En büyük değer**|**Açıklama**|
|:-----|:-----|:-----|
|En fazla ek boyutu (dosyalar Excel)  <br/> |150 MB  <br/> |Dizin oluşturma için ayrıştıracak en büyük e-posta eki boyutu. Bu sınırdan büyük olan hiçbir ek dizin oluşturma için ayrıştırılamaz ve ekin olduğu ileti kısmen dizine alındı olarak işaretlenir.  <br/><br/> **Not:** Ayrıştırma, dizin oluşturma hizmetinin ekten metni ayıklar, noktalama işaretleri ve boşluklar gibi gereksiz karakterleri kaldıran ve sonra metni, daha sonra dizinde depolanan sözcüklere bölen (belirteç oluşturma adı verilen bir işlemde) süreçtir.           |
|En fazla Excel boyutu  <br/> |4 MB  <br/> |Bir sitede yer alan Excel e-posta iletisine eklenen ve dizin oluşturma için ayrıştıracak bir dosya boyutu için üst boyut. Bu Excel büyük olan hiçbir dosya ayrıştırımayacak ve dosya veya ekin olduğu e-posta iletisi, ekinde olmayan olarak işaretlenir.  <br/> |
|En fazla ek sayısı  <br/> |250  <br/> |Dizin oluşturma için ayrıştıracak e-posta iletisine eklenen dosya sayısı üst sayısı. Bir iletide 250'den fazla ek varsa, ilk 250 ek ayrıştırıldı ve dizine alındı; ileti, ayrıştırnmış olan başka ekler de olduğundan kısmen dizine alındı olarak işaretlenir.  <br/> |
|En fazla ek derinliği  <br/> |30  <br/> |Ayrıştırıla en fazla iç içe ek sayısı. Örneğin, e-posta iletisine eklenmiş başka bir ileti varsa ve bu iletide de ek olarak bir Word belgesi varsa, Word belgesi ve ekli ileti dizine alır. İç içe 30 eke kadar bu davranış devam eder.  <br/> |
|En fazla ekli resim sayısı  <br/> |0  <br/> |E-posta iletisine eklenmiş olan resim ayrıştırıcı tarafından atlanır ve dizine alınmz.  <br/> |
|Öğeyi ayrıştırmak için harcanan en fazla zaman  <br/> |30 saniye  <br/> |Bir öğeyi dizin oluşturma için ayrıştırmak için en fazla 30 saniye harcandı. Ayrıştırma süresi 30 saniyeyi aşarsa, öğe kısmen dizine alındı olarak işaretlenir.  <br/> |
|En fazla ayrıştırıcı çıktısı  <br/> |2 milyon karakter  <br/> |Ayrıştırıcıdan gelen metin çıktılarından dizine alan en yüksek miktardır. Örneğin, ayrıştırıcı bir belgeden 8 milyon karakter ayıklamışsa, yalnızca ilk 2 milyon karakter dizine alındı.  <br/> |
|En fazla ek açıklama belirteci  <br/> |2 milyon  <br/> |E-posta iletisi dizine alınca, her söz ek açıklamayla birlikte bu sözcüğün nasıl dizine alın olacağını belirten farklı işleme yönergeleri ek açıklamalır. Her işleme yönergeleri kümesine ek açıklama belirteci denir. Bir e-posta iletisinde Office 365 kalitesini korumak için, bir e-posta iletisinde 2 milyon ek açıklama belirteci sınırı vardır.  <br/> |
|Dizinde en büyük gövde boyutu  <br/> |67 milyon karakter  <br/> |E-posta iletisi gövdesiyle tüm eklerinin toplam karakter sayısı. E-posta iletisi dizine alınca, iletinin gövdesinde ve tüm eklerde yer alan metnin hepsi tek bir dizede bir biri haline gönderilir. Dizine alan bu dizenin boyut üst değeri 67 milyon karakterdir.  <br/> |
|Gövdede en fazla benzersiz belirteç sayısı  <br/> |1 milyon  <br/> |Daha önce de açıklandığı gibi, belirteçler içerikten metnin ayıklanır, noktalama işaretleriyle boşlukların kaldırılması ve dizinde depolanan sözcüklere (belirteç adı verilen sözcüklere) bölünmesi sonucu elde edilir. Örneğin, tümcecik  `"cat, mouse, bird, dog, dog"` 5 belirteç içerir. Ama bunların yalnızca 4'ü benzersiz belirteçtir. E-posta iletisi başına 1 milyon benzersiz belirteç sınırı vardır ve bu sınır dizinin rastgele belirteçlerle çok fazla fazla şey oluşturmasını engellemeye yardımcı olur.  <br/> |
||||

## <a name="more-information-about-partially-indexed-items"></a>Kısmen dizine alınan öğeler hakkında daha fazla bilgi

- Daha önce de belirtildiği gibi, ileti ve belge özellikleri ve meta verileri dizine alındıklarından, bir anahtar sözcük araması dizine alındı meta verilerinde bu anahtar sözcük görünürse sonuç verir. Öte yandan, anahtar sözcük yalnızca desteklenmeyen dosya türüne sahip bir öğenin içeriğinde görünüyorsa, aynı anahtar sözcük araması aynı öğeyi geri dönmez. Bu durumda, öğe kısmen dizine alan bir öğe olarak döndürülür.

- Arama sorgusu ölçütleriyle eşleşmesi nedeniyle kısmen dizine alan bir öğe arama sonuçlarına dahil edilirse, bu öğe, tahmini arama istatistiklerinde kısmen dizine alan bir öğe olarak dahil edilir. Ayrıca, arama sonuçlarını dışarı aktararak kısmen dizine alan öğelere dahil de değildir.

- Bir dosya türü dizin oluşturma için desteklese ve dizine alındı olsa da, bir dosyanın kısmen dizine alındı öğesi olarak döndürül olmasına neden olacak dizin oluşturma veya arama hataları olabilir. Örneğin, büyük bir Excel arama işlemi kısmen başarılı olabilir (ilk 4 MB dizine alındı), ancak dosya boyutu sınırı aşılırken başarısız olabilir. Bu durumda, aynı dosyanın arama sonuçlarıyla birlikte kısmen dizine alındı öğesi olarak döndürül olması mümkündür.

- Microsoft şifreleme teknolojileriyle [şifrelenen ve](encryption.md) bir aramanın ölçütlerine uyan bir e-posta iletisine eklenen dosyalar önizlemede 2'sinde önizlenir ve dışarı aktarıldıklarında şifreleri çözüler. Şu anda Microsoft şifreleme teknolojileriyle şifrelenmiş dosyalar (ve SharePoint veya OneDrive İş) kısmen dizine kaydedilir.

- S/MIME ile şifrelenmiş e-posta iletileri kısmen dizine alır. Bu, dosya ekleri olan veya olmayan şifreli iletileri içerir.

- Azure Hak Yönetimi kullanılarak korunan e-posta iletileri dizine alır ve arama sorgusuyla eşlerise arama sonuçlarına dahil edilir. Hak korunan e-posta iletilerinin şifresi çözülmüş olur ve önizlemesi 2'ye sısır ve dışarı aktarabilirsiniz. Bu işlev için, eBulma Yöneticisi rol grubuna varsayılan olarak atanan RMS Şifre Çözme rolüne atanmış olması gerekir.

- eBulma durumuyla ilişkilendirilmiş sorgu tabanlı bir tutma oluşturursanız, kısmen dizine alınan tüm öğeler ayrı tutunr. Bu, tutma için arama sorgu ölçütleriyle eşleşmeen kısmen dizine alındı öğeleri içerir. Sorgu tabanlı eK bulma tutmaları oluşturma hakkında daha fazla bilgi için bkz [. eBulma tutma oluşturma](create-ediscovery-holds.md).

## <a name="see-also"></a>Ayrıca bkz.

[eBulma'da kısmen dizine alan öğeleri inceleme](investigating-partially-indexed-items-in-ediscovery.md)
