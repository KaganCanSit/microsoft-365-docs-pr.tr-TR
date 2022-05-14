---
title: İçerik Arama'da kısmen dizine alınan öğeler
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
ms.date: 05/13/2022
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
description: Microsoft Purview uyumluluk portalı çalıştırdığınız bir eBulma aramasında ekleyebileceğiniz Exchange ve SharePoint eklenmemiş öğeler hakkında bilgi edinin.
ms.openlocfilehash: 0efb96f8d36868f182476a0eb7b0087beb3134f9
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2022
ms.locfileid: "65417050"
---
# <a name="partially-indexed-items-in-ediscovery"></a>eBulma'da kısmen dizine alınan öğeler

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Microsoft Purview uyumluluk portalı çalıştırdığınız Microsoft Purview eBulma araması, arama çalıştırdığınızda tahmini arama sonuçlarına otomatik olarak kısmen dizinlenmiş öğeler ekler. Kısmen dizine alınan öğeler, SharePoint ve OneDrive İş sitelerindeki posta kutusu öğeleri ve belgeleri Exchange ve herhangi bir nedenle arama için tamamen dizine eklenmedi. Exchange'da, kısmen dizine alınan bir öğe genellikle bir e-posta iletisine eklenmiş bir dosya (dizine alınamaz dosya türünde) içerir. eBulma araması çalıştırdığınızda öğelerin arama için dizine alınamamalarının ve kısmen dizine alınan öğeler olarak döndürüllerinin diğer nedenlerinden bazıları şunlardır:
  
- Dosya türü tanınmadı veya dizin oluşturma için desteklenmiyor.

- İletilerde açılabilen ekli bir dosya vardır; Bu, kısmen dizine alınan e-posta öğelerinin en yaygın nedenidir.

- Dosya türü dizin oluşturma için desteklenir, ancak belirli bir dosya için dizin oluşturma hatası oluştu.

- E-posta iletisine çok fazla dosya iliştirildi.

- E-posta iletisine eklenmiş bir dosya çok büyük.

- Dosya Microsoft dışı teknolojilerle şifrelenir.

- Dosya parola korumalıdır.

> [!NOTE]
> Çoğu kuruluşun içeriği birime göre %1'den az, kısmen dizinlenmiş boyuta göre ise %12'den azı vardır. Birim ve boyut arasındaki farkın nedeni, büyük dosyaların tamamen dizine alınamaz içerik içerme olasılığının daha yüksek olmasıdır.
  
Yasal araştırmalarda kuruluşunuzun kısmen dizine alınan öğeleri gözden geçirmesi gerekebilir. Ayrıca, arama sonuçlarını yerel bir bilgisayara aktarırken veya sonuçları eBulma (Premium) ile analiz için hazırlarken kısmen dizine alınan öğeler eklenip eklenmeyeceğini de belirtebilirsiniz. Daha fazla bilgi için bkz [. eBulma'da kısmen dizine alınan öğeleri araştırma](investigating-partially-indexed-items-in-ediscovery.md).
  
## <a name="file-types-not-indexed-for-search"></a>Dosya türleri arama için dizine alınmadı

Bit Eşlem veya MP3 dosyaları gibi bazı dosya türleri dizine alınabilecek içerik içermez. Sonuç olarak, Exchange ve SharePoint arama dizin sunucuları bu tür dosyalarda tam metin dizini oluşturma gerçekleştirmez. Bu dosya türleri desteklenmeyen dosya türleri olarak kabul edilir. Tam metin dizini oluşturmanın varsayılan olarak veya yönetici tarafından devre dışı bırakıldığı dosya türleri de vardır. Desteklenmeyen ve devre dışı bırakılan dosya türleri İçerik Aramalarında dizine alınmamış öğeler olarak etiketlenir. Daha önce belirtildiği gibi, bir arama çalıştırdığınızda, arama sonuçlarını yerel bir bilgisayara aktardığınızda veya arama sonuçlarını eBulma (Premium) için hazırladığınızda, kısmen dizine alınmış öğeler arama sonuçları kümesine eklenebilir.
  
Desteklenen ve devre dışı bırakılan dosya biçimlerinin listesi için aşağıdaki konulara bakın:
  
-  -  Exchange [Search tarafından dizinlenen Exchange Dosya biçimleri](/exchange/file-formats-indexed-by-exchange-search-exchange-2013-help)

-  -  Exchange [Get-SearchDocumentFormat](/powershell/module/exchange/get-searchdocumentformat)

-  -  SharePoint [Default gezinilen dosya adı uzantıları ve SharePoint ayrıştırılmış dosya türleri](/SharePoint/technical-reference/default-crawled-file-name-extensions-and-parsed-file-types)
  
## <a name="messages-and-documents-with-partially-indexed-file-types-can-be-returned-in-search-results"></a>Kısmen dizinlenmiş dosya türlerine sahip iletiler ve belgeler arama sonuçlarında döndürülebilir

Kısmen dizinlenmiş dosya eki olan veya kısmen dizine alınan her SharePoint belge otomatik olarak kısmen dizinlenmiş öğe olarak döndürülmüyor. Bunun nedeni, e-posta iletilerindeki **Konu** özelliği ve belgelerin **Başlık** veya **Yazar** özellikleri gibi diğer ileti veya belge özelliklerinin dizine alınması ve aranmaya uygun olmasıdır. Örneğin, "financial" için anahtar sözcük araması, söz konusu anahtar sözcük bir e-posta iletisinin konusunda veya belgenin dosya adında veya başlığında görünüyorsa, kısmen dizinlenmiş dosya eki olan öğeleri döndürür. Ancak, anahtar sözcük yalnızca dosyanın gövdesinde görünüyorsa, ileti veya belge kısmen dizinlenmiş bir öğe olarak döndürülür.
  
Benzer şekilde, dizine alınan ve aranabilen diğer ileti veya belge özellikleri arama ölçütleriyle eşleştiğinde, kısmen dizine eklenmiş dosya ekleri ve kısmen dizinlenmiş dosya türüne sahip belgeler arama sonuçlarına eklenir. Arama için dizine alınan ileti özellikleri arasında gönderilen ve alınan tarihler, gönderen ve alıcı, ekin dosya adı ve ileti gövdesindeki metin bulunur. Arama için dizine alınan belge özellikleri, oluşturulan ve değiştirilen tarihleri içerir. Bu nedenle, ileti eki kısmen dizinlenmiş bir öğe olsa da, diğer iletinin veya belge özelliklerinin değeri arama ölçütleri ile eşleşiyorsa ileti normal arama sonuçlarına eklenir.
  
Uyumluluk portalında eBulma araçlarını kullanarak arayabileceğiniz e-posta ve belge özelliklerinin listesi için bkz. [eBulma için anahtar sözcük sorguları ve arama koşulları](keyword-queries-and-search-conditions.md).
  
> [!NOTE]
> Posta kutusu öğesi dizine alınmamış bir klasörden dizine alınmamış bir klasöre taşınırsa, öğenin dizinini kaldırmak için bir bayrak ayarlanır ve öğe dizinden kaldırılır ve aranamaz. Daha sonra, aynı öğe dizine alınan bir klasöre geri taşınırsa, bayrak sıfırlanmaz. Bu, öğenin dizine alınmamış ve aranamaz kalacağı anlamına gelir.

## <a name="partially-indexed-items-included-in-the-search-results"></a>Arama sonuçlarına dahil edilen kısmen dizinlenmiş öğeler

Kuruluşunuzun ne olduğunu, ne içerdiğini ve belirli bir araştırmayla ilgili olup olmadığını belirlemek için kısmen dizinlenmiş öğeleri tanımlaması ve bu öğeler üzerinde ek analiz gerçekleştirmesi gerekebilir. Daha önce açıklandığı gibi, arama yapılan içerik konumlarındaki kısmen dizine alınan öğeler otomatik olarak tahmini arama sonuçlarına eklenir. Arama sonuçlarını dışarı aktarırken veya arama sonuçlarını eBulma (Premium) için hazırlarken bu kısmen dizinlenmiş öğeleri dahil etme seçeneğiniz vardır.
  
Kısmen dizine alınan öğeler hakkında aşağıdakileri göz önünde bulundurun:
  
- Bir eBulma araması çalıştırdığınızda, kısmen dizine alınmış Exchange öğelerinin (arama sorgusu tarafından döndürülen) toplam sayısı ve boyutu açılır sayfadaki arama istatistiklerinde görüntülenir ve **dizinlenmemiş öğeler olarak etiketlenir**. Açılır sayfada görüntülenen kısmen dizinlenmiş öğelerle ilgili istatistikler, SharePoint sitelerde veya OneDrive hesaplarında kısmen dizine alınan öğeleri içermez.

- Sonuçları dışarı aktardığınız arama belirli içerik konumlarında veya kuruluşunuzdaki tüm içerik konumlarında yapılan bir aramaysa, yalnızca içerik konumlarından arama ölçütlerine uyan öğeleri içeren dizine alınmamış öğeler dışarı aktarılır. Başka bir deyişle, bir posta kutusunda veya sitede arama sonucu bulunamazsa, bu posta kutusu veya sitedeki dizine alınmamış öğeler dışarı aktarılmaz. Bunun nedeni, kuruluştaki birçok konumdan kısmen dizine alınan öğeleri dışarı aktarmanın dışarı aktarma hataları olasılığını artırabileceği ve arama sonuçlarını dışarı aktarmak ve indirmek için gereken süreyi artırabileceğidir.

    Aramanın tüm içerik konumlarından kısmen dizinlenmiş öğeleri dışarı aktarmak için, aramayı tüm öğeleri döndürecek şekilde yapılandırın (arama sorgusundan anahtar sözcükleri kaldırarak) ve ardından arama sonuçlarını dışarı aktardığınızda (**Yalnızca tanınmayan biçime sahip olan, şifrelenen veya Çıkış seçenekleri altında başka nedenlerle dizine eklenemeyen öğeler'e** tıklayarak) yalnızca kısmen dizine alınan öğeleri dışarı aktarın.

- Arama sonuçlarına tüm posta kutusu öğelerini eklemeyi seçerseniz veya arama sorgusu herhangi bir anahtar sözcük belirtmezse veya yalnızca bir tarih aralığı belirtirse, kısmen dizine alınmış öğeler kısmen dizinlenmiş öğeleri içeren PST dosyasına kopyalanamayabilir. Bunun nedeni, kısmen dizine alınan öğeler de dahil olmak üzere tüm öğelerin otomatik olarak normal arama sonuçlarına dahil edilmesidir.

- Kısmen dizine alınan öğeler önizleme için kullanılamaz. Arama tarafından döndürülen kısmen dizine alınan öğeleri görüntülemek için arama sonuçlarını dışarı aktarmanız gerekir.

   Buna ek olarak, arama sonuçlarını dışarı aktardığınızda ve dışarı aktarmaya kısmen dizinlenmiş öğeler eklediğinizde, SharePoint öğelerden kısmen dizine alınan öğeler **Gezinilemez** adlı bir klasöre aktarılır. Kısmen dizinlenmiş Exchange öğelerini dışarı aktardığınızda, kısmen dizine alınan öğelerin arama sorgusuyla eşleşip eşleşmediğine ve dışarı aktarma ayarlarının yapılandırmasına bağlı olarak bunlar farklı şekilde dışarı aktarılır. 

- Aşağıdaki tabloda, dizine alınan ve kısmen dizine alınan öğelerin dışarı aktarma davranışı ve her birinin farklı dışarı aktarma yapılandırma ayarlarına dahil edilip edilmediği gösterilir.

  |**Yapılandırmayı dışarı aktarma**|**Arama sorgusuyla eşleşen dizine alınan öğeler**|**Arama sorgusuyla eşleşen kısmen dizine alınan öğeler**|**Arama sorgusuyla eşleşmeyen kısmen dizine alınan öğeler**|
  |:-----|:-----|:-----|:-----|
  |Yalnızca dizine alınan öğeleri dışarı aktarma  <br/> |Verilen<br/> |Dışarı aktarıldı (dışarı aktarılan dizine alınan öğelere dahildir)<br/>  |Dışarı aktarılmadı <br/>|
  |Yalnızca kısmen dizine alınan öğeleri dışarı aktarma  <br/> |Dışarı aktarılmadı  <br/> |Dışarı aktarıldı (kısmen dizinlenmiş öğeler olarak)<br/> |Dışarı aktarıldı (kısmen dizinlenmiş öğeler olarak)|
  |Dizine alınan ve kısmen dizine alınan öğeleri dışarı aktarma  <br/> |Verilen<br/> |Dışarı aktarıldı (dışarı aktarılan dizine alınan öğelere dahildir)<br/>  |Dışarı aktarıldı (kısmen dizinlenmiş öğeler olarak)<br/>|
  ||||
  
## <a name="workaround-for-using-a-date-range-to-exclude-partially-indexed-items"></a>Kısmen dizine alınmış öğeleri dışlamak için tarih aralığı kullanmak için geçici çözüm

İçerik arama ve Microsoft Purview eBulma (Standart) bölümünde, kısmen dizine alınmış öğelerin arama sorgusu tarafından döndürülmekten dışlanması için tarih aralığını kullanamazsınız. Başka bir deyişle, bir tarih aralığının dışında kalan kısmen dizinlenmiş öğeler, arama istatistiklerine kısmen dizinlenmiş öğeler olarak ve kısmen dizinlenmiş öğeleri dışarı aktardığınızda da dahil edilir. eBulma'da (Premium), arama sorgusunda bir tarih aralığı kullanarak kısmen dizine alınmış öğeleri dışlayabilirsiniz.

Bu sınırlama için geçici bir çözüm olarak aşağıdaki yordamı öneririz.

1. Gereksinimlerinizi karşılayan ve istenen sonuçları döndüren bir arama sorgusu kullanarak arama oluşturun ve çalıştırın.

2. 1. adımdaki aramanın sonuçlarını dışarı aktarın, ancak dışarı aktarma işlemine kısmen dizine alınan öğeleri eklemeyin. Bunu yapmak için, **Tanınmayan biçime sahip olanlar hariç tüm öğeler şifrelenir veya başka nedenlerle dizine eklenmemiş** olan tüm öğeler dışarı aktarma seçeneğini belirleyebilirsiniz. <sup>1</sup>

   ![Çıkış seçeneklerini dışarı aktarın.](../media/ExportOutputOptions.png)

3. 1. adımda kullandığınız aynı arama sorgusunu (ve aynı konumları arar) kullanan ikinci bir arama oluşturun ve çalıştırın. **AND** işlecini kullanarak özgün sorguya aşağıdaki yan tümceyi ekleyin:

   ```text
   <original query> AND ((IndexingErrorCode>0 OR IndexingErrorCode<0) AND sent:date1..date2)
   ```

   Bu yan tümcenin eklenmesi, özgün arama sorgunuzla eşleşen ve belirli bir tarih aralığında yer alan kısmen dizinlenmiş öğeler döndürür. <sup>2</sup>

4. 3. adımdaki aramanın sonuçlarını dışarı aktarın ve bu kez dışarı aktarma işlemine kısmen dizine alınan öğeleri ekleyin. Bunu yapmak için, **tanınmayan biçime sahip olanlar da dahil olmak üzere Tüm öğeler şifrelenir veya diğer nedenlerle dışarı aktarma seçeneği dizine eklenmez** .

   > [!NOTE]
   > <sup>1</sup> 2. adımın çıkışı yalnızca dizine alınan öğelerin dışarı aktarılmasıyla sonuçlanır.<br/>
   > <sup>2</sup> 3. adımda kullanılan koşul yalnızca belirtilen tarih aralığındaki dizin oluşturma hatalarına sahip öğeleri tanımlar. Tamamen dizine alınan hiçbir öğe döndürmez. Bu, 4. adımda dışarı aktarılan öğelerin yalnızca tarih aralığında yer alan dizinlenmemiş öğeleri içerdiği anlamına gelir. Dışarı aktarma işlemi dizine alınan öğeleri içermez. Sonuç olarak, 2. ve 4. adımın birleşik çıkışı, belirtilen tarih aralığındaki tüm dizinlenmiş ve dizinlenmemiş öğeleri içerir.

3. adımda oluşturduğunuz ikinci aramayı ve karşılık gelen dışarı aktarmayı kullanarak özgün arama sorgunuzla eşleşen kısmen dizine alınan öğeleri görüntüleyin ve öğrenin. İkinci aramadan dışarı aktarma işlemi, gerekirse bunları gözden geçirebilmeniz için dışarı aktarılan kısmen dizine alınan tüm öğeleri de içerir.

> [!TIP]
> Önceki yordamda, gerçek arama sonuçlarını dışarı aktarabilir veya yalnızca bir raporu dışarı aktarabilirsiniz.

## <a name="indexing-limits-for-messages"></a>İletiler için dizin oluşturma sınırları

Aşağıdaki tabloda, e-posta iletisinin Microsoft 365'daki bir eBulma aramasında kısmen dizinlenmiş bir öğe olarak döndürülüp döndürülebileceği dizin oluşturma sınırları açıklanmaktadır.
  
SharePoint belgeler için dizin oluşturma sınırlarının listesi için bkz[. SharePoint Online için arama sınırları](/sharepoint/search-limits).
  
|**Dizin oluşturma sınırı**|**En büyük değer**|**Açıklama**|
|:-----|:-----|:-----|
|En büyük ek boyutu (Excel dosyaları hariç)  <br/> |150 MB  <br/> |Dizin oluşturma için ayrıştırılacak bir e-posta ekinin en büyük boyutu. Bu sınırdan daha büyük olan ekler dizin oluşturma için ayrıştırılamaz ve eki içeren ileti kısmen dizinlenmiş olarak işaretlenir.  <br/><br/> **Not:** Ayrıştırma, dizin oluşturma hizmetinin ekten metin ayıkladığı, noktalama işaretleri ve boşluklar gibi gereksiz karakterleri kaldırdığı ve ardından metni daha sonra dizinde depolanan sözcüklere (belirteç oluşturma adı verilen bir işlemde) böldüğü işlemdir.           |
|en büyük Excel dosya boyutu  <br/> |4 MB  <br/> |Bir sitede bulunan veya dizin oluşturma için ayrıştırılacak bir e-posta iletisine eklenmiş bir Excel dosyasının en büyük boyutu. Bu sınırdan daha büyük Excel dosyalar ayrıştırılmaz ve dosya eki içeren ileti veya e-posta dizinlenmemiş olarak işaretlenir.  <br/> |
|En fazla ek sayısı  <br/> |250  <br/> |Dizin oluşturma için ayrıştırılacak bir e-posta iletisine eklenen dosya sayısı üst sınırı. İletinin 250'den fazla eki varsa, ilk 250 ek ayrıştırılır ve dizine eklenir ve ayrıştırılmamış ekleri olduğundan ileti kısmen dizinlenmiş olarak işaretlenir.  <br/> |
|En fazla ek derinliği  <br/> |30  <br/> |Ayrıştırılan iç içe ek sayısı üst sınırı. Örneğin, e-posta iletisine başka bir ileti ekliyse ve ekli iletide ekli bir Word belgesi varsa, Word belgesi ve ekli ileti dizine eklenir. Bu davranış en fazla 30 iç içe ek için devam eder.  <br/> |
|Ekli görüntü sayısı üst sınırı  <br/> |0  <br/> |E-posta iletisine eklenmiş bir resim ayrıştırıcı tarafından atlanır ve dizine eklenmez.  <br/> |
|Öğe ayrıştırma için harcanan en uzun süre  <br/> |30 saniye  <br/> |Bir öğeyi dizin oluşturmak için ayrıştırma için en fazla 30 saniye harcanıyor. Ayrıştırma süresi 30 saniyeyi aşarsa, öğe kısmen dizinlenmiş olarak işaretlenir.  <br/> |
|En fazla ayrıştırıcı çıkışı  <br/> |2 milyon karakter  <br/> |Dizine alınan ayrıştırıcıdan elde edilen en fazla metin çıkışı miktarı. Örneğin, ayrıştırıcı bir belgeden 8 milyon karakter ayıkladıysa, yalnızca ilk 2 milyon karakter dizine eklenir.  <br/> |
|En fazla ek açıklama belirteci  <br/> |2 milyon  <br/> |Bir e-posta iletisi dizine alındığında, her sözcük, söz konusu sözcüğün nasıl dizinleneceğini belirten farklı işleme yönergeleriyle ek açıklama ekler. Her işleme yönergeleri kümesi ek açıklama belirteci olarak adlandırılır. Office 365'da hizmet kalitesini korumak için e-posta iletisi için 2 milyon ek açıklama belirteci sınırı vardır.  <br/> |
|Dizindeki en büyük gövde boyutu  <br/> |67 milyon karakter  <br/> |E-posta iletisinin gövdesindeki toplam karakter sayısı ve tüm ekleri. Bir e-posta iletisi dizine alındığında, iletinin gövdesindeki ve tüm eklerdeki tüm metinler tek bir dizede birleştirilir. Dizine alınan bu dizenin en büyük boyutu 67 milyon karakterdir.  <br/> |
|Gövdedeki en büyük benzersiz belirteç sayısı  <br/> |1 milyon  <br/> |Daha önce açıklandığı gibi belirteçler, içerikten metin ayıklamanın, noktalama işaretlerini ve boşlukları kaldırmanın ve ardından dizinde depolanan sözcüklere (belirteç olarak adlandırılır) bölünmesinin sonucu olur. Örneğin, tümcecik  `"cat, mouse, bird, dog, dog"` 5 belirteç içerir. Ancak bunların yalnızca 4'ünün benzersiz belirteçleri vardır. E-posta iletisi başına 1 milyon benzersiz belirteç sınırı vardır ve bu da dizinin rastgele belirteçlerle fazla büyük olmasını önlemeye yardımcı olur.  <br/> |
||||

## <a name="more-information-about-partially-indexed-items"></a>Kısmen dizine alınan öğeler hakkında daha fazla bilgi

- Daha önce belirtildiği gibi, ileti ve belge özellikleri ve meta verileri dizine alındığından, bu anahtar sözcük dizine alınan meta verilerde görünürse bir anahtar sözcük araması sonuç döndürebilir. Ancak, anahtar sözcük yalnızca desteklenmeyen bir dosya türüne sahip bir öğenin içeriğinde görünüyorsa, aynı anahtar sözcük araması aynı öğeyi döndürmeyebilir. Bu durumda, öğe kısmen dizinlenmiş bir öğe olarak döndürülür.

- Arama sonuçlarına arama sorgusu ölçütleriyle eşleştiğinden kısmen dizinlenmiş bir öğe dahil edilirse, tahmini arama istatistiklerine kısmen dizinlenmiş bir öğe olarak dahil edilmeyecektir. Ayrıca, arama sonuçlarını dışarı aktardığınızda kısmen dizine alınan öğelere dahil edilmeyecektir.

- Dizin oluşturma için bir dosya türü desteklense ve dizine alınsa da, bir dosyanın kısmen dizinlenmiş bir öğe olarak döndürülmesine neden olacak dizin oluşturma veya arama hataları olabilir. Örneğin, büyük bir Excel dosyasında arama kısmen başarılı olabilir (ilk 4 MB dizine eklendiğinden), ancak dosya boyutu sınırı aşıldığından başarısız olabilir. Bu durumda, arama sonuçlarıyla birlikte ve kısmen dizinlenmiş bir öğe olarak aynı dosya döndürülür.

- [Microsoft şifreleme teknolojileriyle](encryption.md) şifrelenen ve arama ölçütleriyle eşleşen bir e-posta iletisine eklenen dosyalar önizlemeye eklenebilir ve dışarı aktarıldığında şifresi çözülür. Şu anda, Microsoft şifreleme teknolojileriyle şifrelenmiş (ve SharePoint veya OneDrive İş içinde depolanan) dosyalar kısmen dizine alınır. 

   > [!NOTE]
   > Duyarlılık etiketleri kullanılarak şifrelenen dosyaların şifresi çözülmez.

- S/MIME ile şifrelenen e-posta iletileri kısmen dizine eklenir. Bu, dosya ekleri olan veya olmayan şifrelenmiş iletileri içerir.

- Azure Rights Management kullanılarak korunan e-posta iletileri dizine alınır ve arama sorgusuyla eşleşiyorsa arama sonuçlarına eklenir. Hak korumalı e-posta iletilerinin şifresi çözülür ve önizlenebilir ve dışarı aktarılabilir. Bu işlev, varsayılan olarak eBulma Yöneticisi rol grubuna atanan RMS Şifre Çözme rolüne atanmanızı gerektirir.

- eBulma olayıyla ilişkili sorgu tabanlı bir ayrı tutma oluşturursanız, kısmen dizine alınan tüm öğeler beklemeye alınır. Bu, ayrı tutma için arama sorgusu ölçütleri ile eşleşmeyen kısmen dizine alınan öğeleri içerir. Sorgu tabanlı eBulma tutmaları oluşturma hakkında daha fazla bilgi için bkz. [eBulma ayrı tutması oluşturma](create-ediscovery-holds.md).

## <a name="see-also"></a>Ayrıca bkz.

[eBulma'da kısmen dizine alınan öğeleri araştırma](investigating-partially-indexed-items-in-ediscovery.md)
