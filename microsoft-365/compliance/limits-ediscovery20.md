---
title: Advanced eDiscovery sınırları
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.custom:
- seo-marvel-apr2020
description: Bu konuda, çözümle ilgili çözüm için yürürlüğe girecek olay sınırları, dizin oluşturma Advanced eDiscovery ve arama Microsoft 365.
ms.openlocfilehash: c07d53766a0542ebf9fd7753a211a305515e8444
ms.sourcegitcommit: df1ad7118c4a95a310a4f17124322a6ae6ace26f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/11/2021
ms.locfileid: "62988792"
---
# <a name="limits-in-advanced-ediscovery"></a>Alan Advanced eDiscovery

Bu makalede, Microsoft 365'de Advanced eDiscovery çözüm Microsoft 365.

## <a name="case-and-review-set-limits"></a>Vaka ve gözden geçirme kümesi sınırları

Aşağıdaki tabloda, çalışma sayfalarındaki vakaların ve gözden geçirme kümelarının sınırları Advanced eDiscovery.

| Sınırın açıklaması | Sınır |
|:-----|:-----|
|Vakaya eklenecek toplam belge sayısı (bir vakadaki tüm gözden geçirme kümeleri için).  <br/> |3 milyon <br/> |
|Yükleme kümesi başına toplam dosya boyutu. Bu, gözden geçirme kümesine Office 365 olmayanların yüklenmesini içerir.  <br/> |300 GB <br/> |
|Kuruluşta her gün tüm gözden geçirme kümelerine yüklenen toplam veri miktarı.<br/> |2 TB <br/> |
|Vaka başına en fazla yükleme kümesi sayısı.  <br/> |200 <br/> |
|Vaka başına en fazla gözden geçirme kümesi sayısı.  <br/> |20 <br/> |
|Vaka başına etiket grubu sayısı üst sayısı.  <br/> |1,000 |
|Vaka başına en fazla benzersiz etiket sayısı. <br/> |1.0006<sup></sup> |
|Gözden geçirme kümesine içerik eklemek için, organizasyonda eş zamanlı iş sayısı üst sayısı. Bu işler Gözden **geçirme kümesine veri ekleme olarak** adlandırılmıştır ve **bir davanın İşleri** sekmesinde görüntülenir.| <sup>104</sup> |
|Kullanıcı başına gözden geçirme kümesine içerik eklemek için eş zamanlı iş sayısı üst sayısı. Bu işler Gözden **geçirme kümesine veri ekleme olarak** adlandırılmıştır ve **bir davanın İşleri** sekmesinde görüntülenir. | 3 |
|||

## <a name="hold-limits"></a>Tutma sınırları

Aşağıdaki tabloda, bir davayla ilişkilendirilmiş askıya Advanced eDiscovery listele.

| Sınırın açıklaması | Sınır |
|:-----|:-----|
|Bir kuruluş için en fazla büyük büyük//veya daha fazla 12/sn. Bu sınır, Core eDiscovery ve Advanced eDiscovery durumlarda birleştirilmiş Advanced eDiscovery içerir. <br/> |10,000  <br/> |
|Tek bir durumdaki posta kutusu sayısı üst sayısı. Bu sınır, birleştirilmiş toplam kullanıcı posta kutusu ve Kullanıcı Grupları, Posta Microsoft 365, Posta Kutusu Microsoft Teams posta Yammer içerir. <br/> |1,000  <br/> |
|Tek bir vakada en fazla site sayısı. Bu sınır, birleştirilmiş toplam OneDrive İş sitesi, SharePoint sitesi ve Microsoft 365 Grupları, Site Grupları, Microsoft Teams ve Yammer içerir.  <br/> |100  <br/> |

## <a name="indexing-limits"></a>Dizin oluşturma sınırları

Aşağıdaki tabloda, çalışma sayfalarında dizin oluşturma Advanced eDiscovery.

| Sınırın açıklaması | Sınır |
|:-----|:-----|
|Tek bir dosyadan ayıklanan en fazla karakter sayısı.  <br/> |10 <sup>milyon1</sup> <br/> |
|Tek bir dosyanın boyut üst boyutu.   <br/> |150 <sup>MB1</sup> <br/> |
|Belgeye en fazla katıştırılmış öğe derinliği.  <br/> |<sup>251</sup> <br/> |
|Optik Karakter Tanıma (OCR) tarafından işlenen dosyaların boyut üst sayısı.  <br/> |24 <sup>MB1</sup> <br/>  
|||

## <a name="search-limits"></a>Arama sınırları

Bu bölümde açıklanan sınırlar, Aramalar sekmesindeki arama aracını kullanarak **vakaya** ilişkin verileri toplamakla ilgilidir. Daha fazla bilgi için bkz[. Olayla ilgili verileri toplama Advanced eDiscovery](collecting-data-for-ediscovery.md).

| Sınırın açıklaması | Sınır |
|:-----|:-----|
|Tek bir aramada aranacak posta kutusu veya site sayısı üst sayısı. |Sınır yok|
|Aynı anda çalıştıracak en fazla arama sayısı. |Sınır yok |
|Tek bir kullanıcının aynı anda başlat birden çok arama başlatması için en fazla sayı. |10 | 
|Arama sorgusu için karakter sayısı üst sayısı (işleçler ve koşullar dahil). |10.0002<sup></sup>|
|Siteler ve sitelerde (işleçler ve koşullar dahil) SharePoint OneDrive İş için arama sorgusu karakter sayısı üst sayısı. |10,000<br>4.000 Joker <sup>Karakter2</sup>|
|Ön ek joker karakterleri için en az alfa karakteri sayısı; örneğin, **one\**_ veya _* set\***.|3 |  
|Tam bir tümcecik aramak için ön ek joker karakteri kullanırken veya bir önek joker karakteri ve **NEAR** Boole işleci kullanırken döndürülen en fazla değişken. |10.0003<sup></sup>|
|Aramaların önizleme sayfasında görüntülenen kullanıcı posta kutusu başına en fazla öğe sayısı. En yeni öğeler görüntülenir. |100|
|Aramalar için önizleme sayfasında görüntülenen tüm posta kutularından en fazla öğe sayısı.|1,000|
|Arama sonuçları için önizlemede 2013 posta kutusu sayısı üst araması.  Arama sorgusuyla eşleşmeye uygun öğeler içeren 1.000'den fazla posta kutusu varsa önizleme için yalnızca en çok sonuçları içeren ilk 1.000 posta kutusu kullanılabilir.|1,000|
|Arama önizleme sayfasında görüntülenen SharePoint ve OneDrive İş en fazla öğe sayısı. En yeni öğeler görüntülenir. |200|
|Arama sonuçları için SharePoint OneDrive İş site sayısı ve en fazla OneDrive İş site sayısı. Arama sorgusuyla eşleşmeye sahip öğeler içeren 200'den fazla site varsa, önizleme için yalnızca en çok sonuçları içeren ilk 200 site kullanılabilir.|200|
|Aramaların önizleme sayfasında görüntülenen ortak klasör posta kutusu başına en fazla öğe sayısı. |100|
|Tüm ortak klasör posta kutusu öğelerinde bulunan ve arama önizleme sayfasında görüntülenen en fazla öğe sayısı. |200|
|Arama sonuçları için önizlemede 2013'e kadar olan ortak klasör posta kutusu sayısı. Arama sorgusuyla eşleşmeye çalışan öğeler içeren 500'den fazla ortak klasör posta kutusu varsa, önizleme için yalnızca en çok sonuçları içeren ilk 500 posta kutusu kullanılabilir.|500|
|||

## <a name="search-times"></a>Arama saatleri

Microsoft, tüm kuruluşların yaptığı aramalar için performans bilgilerini toplar. Arama sorgusunun karmaşıklığı arama sürelerini etkileyebilir, ancak aramaların ne kadar süreyle devamyeceğini etkileyen en büyük faktör, arama yapılan posta kutularının sayısıdır. Microsoft, arama süreleri için Bir Hizmet Düzeyi Sözleşmesi sağlamasa da, aşağıdaki tabloda, aramada yer alan posta kutularının sayısına göre koleksiyon aramalarının ortalama arama süreleri listelemektedir.
  
  | Posta kutusu sayısı | Ortalama arama süresi |
  |:-----|:-----|
  |100  <br/> |30 saniye  <br/> |
  |1,000  <br/> |45 saniye  <br/> |
  |10,000  <br/> |4 dakika  <br/> |
  |25,000  <br/> |10 dakika  <br/> |
  |50,000  <br/> |20 dakika  <br/> |
  |100,000  <br/> |25 dakika  <br/> |
  |||

## <a name="viewer-limits"></a>Görüntüleyici sınırları

| Sınırın açıklaması | Sınır |
|:-----|:-----|
|Yerel görüntüleyicide Excel dosya boyutu üst sayısı.  <br/> |4 MB  <br/> |
|||

## <a name="export-limits---final-export-out-of-review-set"></a>Dışarı aktarma sınırları - Gözden Geçirme Kümesi'nin son dışarı aktarması

Bu bölümde açıklanan sınırlar, gözden geçirme kümesi dışında belge dışarı aktarmayla ilgilidir.

| Sınırın açıklaması | Sınır |
|:-----|:-----|
|Tek bir dışarı aktarma için en büyük boyut.|5 milyon belge veya 500 GB (hangisi daha küçükse)|
|Gözden geçirme kümesi başına en yüksek eşzamanlı dışarı aktarma. | 1 |
|||

## <a name="review-set-download-limits"></a>ayarlanmış indirme sınırlarını gözden geçirme

| Sınırın açıklaması | Sınır |
|:-----|:-----|
|Gözden geçirme kümesinden indirilen toplam dosya boyutu veya en fazla belge sayısı.  <br/> |3 MB veya 50 <sup>belge5</sup>|
|||

<br/>
<br/>

> [!NOTE]
> <sup>1</sup> Tek dosya sınırını aşan her öğe işleme hatası olarak karşıda gelir.
>
> <sup>2</sup> Farklı SharePoint konumlarda OneDrive İş, arama yapılan sitelerin URL'lerinde bu sınıra göre karakterler sayılır. Toplam karakter sayısı aşağıdakilerden oluşur:<br>
> - Hem Kullanıcılar hem de Filtreler alanlarındaki tüm karakterler.
> - Kullanıcıya uygun olan tüm arama izinleri filtreleri.
> - Aramada herhangi bir konum özelliğinden karakterler; ExchangeLocation,PublicFolderLocation,SharePointLocation,ExchangeLocationExclusion,PublicFolderLocationExclusion,SharePointLocationExclusion, OneDriveLocationExclusion içerir.
>   Örneğin, hem SharePointLocation SharePoint OneDrive OneDriveLocation alanı için "ALL" sözcüğü görüntüılacağı için, aramada tüm SharePoint siteleri ve OneDrive hesapları da altı karakter olarak sayılır.
>
> <sup>3</sup> Tümceciksiz sorgular için (çift tırnak işareti kullanmayan bir anahtar sözcük değeri) özel bir ön ek dizini kullanıruz. Bu bize bir sözcüğün belgede oluştuğuni ama belgenin içinde bulunduğu yeri değil, belge içinde yer alan yeri gösterir. Bir tümcecik sorgusu yapmak için (çift tırnak işaretleri içeren bir anahtar sözcük değeri), tümceciğin sözcükleri için belge içindeki konumu karşılaştırmamız gerekir. Bu, tümcecik sorguları için ön ek dizinini kullanalememız anlamına gelir. Bu durumda, sorguyu, ön ekin genişletilen tüm olası sözcüklerle dahili olarak genişleteceğiz; örneğin, **time *_* _\*"time OR timer OR times OR timex OR timeboxed OR ..." değerine kadar genişler**. 10.000 sayısı üst sınırı, sözcüğün sorguyla eşleşen belge sayısıyla değil, genişletilen değişken sayısı üst sınırıdır. Tümcecik olmayan terimler için üst sınır yoktur.
>
> <sup>4</sup> Bu sınır, diğer eBulma araçlarında dışarı içerik aktarmayla paylaşılır. Bu, İçerik arama ve Çekirdek eBulma'daki eş zamanlı dışarı aktarmaların (ve Advanced eDiscovery'de gözden geçirme kümelerine içerik eklemenin) hepsi bu sınıra karşı uygulandığı anlamına gelir.
>
> <sup>5</sup> Bu sınır, seçili belgeleri gözden geçirme kümesinden indirmek için geçerlidir. Gözden geçirme kümesinden belgeleri dışarı aktarma için bu geçerli değildir. Belgeleri indirme ve dışarı aktarma hakkında daha fazla bilgi için bkz. Örnek olay [verilerini Advanced eDiscovery](exporting-data-ediscover20.md).
>
> <sup>6</sup> Bu, olayda oluşturabilirsiniz en fazla etiket sayısıdır. Bu sınır, etiketlenen belge sayısıyla ilgili değildir.
>
