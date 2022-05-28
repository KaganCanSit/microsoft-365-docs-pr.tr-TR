---
title: eKeşif (Premium) sınırları
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
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
description: Microsoft 365'da eBulma (Premium) çözümü için geçerli olan durum sınırları, dizin oluşturma sınırları ve arama sınırları hakkında bilgi edinin.
ms.openlocfilehash: 5b83cd578b8975dd0185fb2902357c2f0c201043
ms.sourcegitcommit: 38a18b0195d99222c2c6da0c80838d24b5f66b97
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/28/2022
ms.locfileid: "65772708"
---
# <a name="limits-in-ediscovery-premium"></a>eBulma sınırları (Premium)

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Bu makalede, Microsoft 365'daki Microsoft Purview eBulma (Premium) çözümündeki sınırlar açıklanmaktadır.

## <a name="case-and-review-set-limits"></a>Servis talebi ve gözden geçirme belirlenen sınırlar

Aşağıdaki tabloda, eBulma (Premium) içindeki servis taleplerinin ve gözden geçirme kümelerinin sınırları listeleniyor.

|Sınırın açıklaması|Sınırı|
|---|---|
|Bir servis talebine eklenebilen toplam belge sayısı (bir servis talebindeki tüm inceleme kümeleri için).|3 milyon|
|Yük kümesi başına toplam dosya boyutu. Bu, Office 365 olmayanların bir gözden geçirme kümesine yüklenmesini içerir.|300 GB|
|Kuruluştaki tüm gözden geçirme kümelerine günlük yüklenen toplam veri miktarı.<br/>|2TB|
|Olay başına en fazla yük kümesi sayısı.|200|
|Servis talebi başına en fazla gözden geçirme kümesi sayısı.|20|
|Servis talebi başına en fazla etiket grubu sayısı.|1,000|
|Servis talebi başına en fazla benzersiz etiket sayısı.|1.000<sup>1</sup>|
|Bir gözden geçirme kümesine içerik eklemek için kuruluşunuzdaki en fazla eşzamanlı iş. Bu işler **Gözden geçirme kümesine veri ekleme** olarak adlandırılır ve bir durumda **İşler** sekmesinde görüntülenir.|10<sup>2</sup>|
|Kullanıcı başına bir gözden geçirme kümesine içerik eklemek için en fazla eşzamanlı iş. Bu işler **Gözden geçirme kümesine veri ekleme** olarak adlandırılır ve bir durumda **İşler** sekmesinde görüntülenir.|3|

## <a name="hold-limits"></a>Ayrı tutma sınırları

Aşağıdaki tabloda, eBulma (Premium) olayıyla ilişkili tutma sınırları listeleniyor.

| Sınırın açıklaması | Sınırı |
|:-----|:-----|
|Bir kuruluş için en fazla saklama ilkesi sayısı. Bu sınır, Microsoft Purview eBulma (Standart) ve Microsoft Purview eBulma (Premium) durumlarında birleştirilmiş saklama ilkeleri toplamını içerir. <br/> |10.000<sup>3</sup>  <br/> |
|Tek bir servis talebi ayrı tutmadaki en fazla posta kutusu sayısı. Bu sınır, kullanıcı posta kutularının toplamını ve Microsoft 365 Grupları, Microsoft Teams ve Yammer Grupları ile ilişkili posta kutularını içerir. <br/> |1,000  <br/> |
|Tek bir servis talebi saklamadaki en fazla site sayısı. Bu sınır, OneDrive İş sitelerin, SharePoint sitelerin ve Microsoft 365 Grupları, Microsoft Teams ve Yammer Grupları ile ilişkili sitelerin toplamını içerir.  <br/> |100  <br/> |

## <a name="indexing-limits"></a>Dizin oluşturma sınırları

Aşağıdaki tabloda, eBulma (Premium) içindeki dizin oluşturma sınırları listeleniyor.

|Sınırın açıklaması|Sınırı|
|---|---|
|Tek bir dosyadan ayıklanan en fazla karakter sayısı.|10 milyon<sup>4</sup>|
|Tek bir dosyanın en büyük boyutu.|150 MB<sup>4</sup>|
|Belgedeki katıştırılmış öğe derinliği üst sınırı.|25<sup>4</sup>|
|Optik Karakter Tanıma (OCR) tarafından işlenen dosyaların maksimum boyutu.|24 MB<sup>4</sup> <br/> |
|En yüksek gelişmiş dizin oluşturma aktarım hızı | Saatte 2 GB |

## <a name="search-limits"></a>Arama sınırları

Bu bölümde açıklanan sınırlar, bir servis talebi için veri toplamak için **Aramalar** sekmesindeki arama aracının kullanılmasıyla ilgilidir. Daha fazla bilgi için bkz. [eBulma'da (Premium) bir servis talebi için veri toplama](collecting-data-for-ediscovery.md).

|Sınırın açıklaması|Sınırı|
|---|---|
|Tek bir aramada aranabilecek en fazla posta kutusu veya site sayısı.|Sınır yok|
|Aynı anda çalışabilecek en fazla arama sayısı.|Sınır yok|
|Tek bir kullanıcının aynı anda başlatabileceği en fazla arama sayısı.|10|
|Arama sorgusu için karakter sayısı üst sınırı (işleçler ve koşullar dahil).|10.000<sup>5</sup>|
|SharePoint ve OneDrive İş siteleri için arama sorgusu için en fazla karakter sayısı (işleçler ve koşullar dahil).|10,000<br>Joker Karakterli 4.000<sup>5</sup>|
|Ön ek joker karakterleri için en az alfa karakteri sayısı; örneğin, **one\**_ veya _* set\***.|3|
|Tam bir tümceciği aramak için ön ek joker karakteri kullanılırken veya ön ek joker karakteri ve **NEAR** Boole işleci kullanılırken döndürülen maksimum değişken sayısı.|10.000<sup>6</sup>|
|Aramalar için önizleme sayfasında görüntülenen kullanıcı posta kutusu başına en fazla öğe sayısı. En yeni öğeler görüntülenir.|100|
|Aramalar için önizleme sayfasında görüntülenen tüm posta kutularından en fazla öğe sayısı.|1,000|
|Arama sonuçları için önizlenebilen en fazla posta kutusu sayısı.  Arama sorgusuyla eşleşen öğeleri içeren 1.000'den fazla posta kutusu varsa, yalnızca en çok sonuç içeren ilk 1.000 posta kutusu önizleme için kullanılabilir.|1,000|
|Aramalar için önizleme sayfasında görüntülenen SharePoint ve OneDrive İş sitelerindeki en fazla öğe sayısı. En yeni öğeler görüntülenir.|200|
|Arama sonuçları için önizlenebilen en fazla SharePoint ve OneDrive İş sitesi sayısı. Arama sorgusuyla eşleşen öğeler içeren 200'den fazla site varsa, önizleme için yalnızca en çok sonuç içeren ilk 200 site kullanılabilir.|200|
|Aramalar için önizleme sayfasında görüntülenen ortak klasör posta kutusu başına en fazla öğe sayısı.|100|
|Aramalar için önizleme sayfasında görüntülenen tüm ortak klasör posta kutusu öğelerinde bulunan öğe sayısı üst sınırı.|200|
|Arama sonuçları için önizlenebilen en fazla ortak klasör posta kutusu sayısı. Arama sorgusuyla eşleşen öğeleri içeren 500'den fazla ortak klasör posta kutusu varsa, yalnızca en çok sonuç içeren ilk 500 posta kutusu önizleme için kullanılabilir.|500|
|Taslak koleksiyonun örnek sayfasında görüntülenebilen bir öğenin en büyük boyutu.|10.000.000 bayt (yaklaşık 9,5 MB)|

## <a name="search-times"></a>Arama süreleri

Microsoft, tüm kuruluşlar tarafından çalıştırılan aramalar için performans bilgileri toplar. Arama sorgusunun karmaşıklığı arama sürelerini etkileyebilir ancak aramaların ne kadar sürdüğünü etkileyen en büyük faktör, arama yapılan posta kutularının sayısıdır. Microsoft arama süreleri için bir Hizmet Düzeyi Sözleşmesi sağlamasa da, aşağıdaki tabloda aramaya dahil edilen posta kutularının sayısına göre koleksiyon aramaları için ortalama arama süreleri listelenmiştir.
  
|Posta kutusu sayısı|Ortalama arama süresi|
|---|---|
|100|30 saniye|
|1,000|45 saniye|
|10,000|4 dakika|
|25,000|10 dakika|
|50,000|20 dakika|
|100,000|25 dakika|

## <a name="viewer-limits"></a>Görüntüleyici sınırları

|Sınırın açıklaması|Sınırı|
|---|---|
|Yerel görüntüleyicide görüntülenebilen Excel dosyasının en büyük boyutu.|4 MB|

## <a name="export-limits---final-export-out-of-review-set"></a>Dışarı aktarma sınırları - Gözden Geçirme Kümesinden son dışarı aktarma

Bu bölümde açıklanan sınırlar, belgeleri gözden geçirme kümesinin dışına dışarı aktarmayla ilgilidir.

|Sınırın açıklaması|Sınırı|
|---|---|
|Tek bir dışarı aktarmanın en büyük boyutu.|5 milyon belge veya 500 GB (hangisi daha küçükse)|
|Gözden geçirme kümesi başına en fazla eşzamanlı dışarı aktarma.|1|

## <a name="review-set-download-limits"></a>İndirme sınırlarını ayarlama bölümünü gözden geçirin

|Sınırın açıklaması|Sınırı|
|---|---|
|Bir gözden geçirme kümesinden indirilen toplam dosya boyutu veya en fazla belge sayısı.|3 MB veya 50 belge<sup>7</sup>|


## <a name="reference-notes"></a>Başvuru notları
<sup>1</sup> Bu, bir durumda oluşturabileceğiniz en fazla etiket sayısıdır. Bu sınır, etiketlenebilir belge sayısıyla ilgili değildir.

<sup>2</sup> Bu sınır, diğer eBulma araçlarındaki içerik dışarı aktarıldığında paylaşılır. Bu, İçerik arama ve eBulma (Standart) içindeki eşzamanlı dışarı aktarma işlemlerinin (ve eBulma'daki (Premium)) kümeleri gözden geçirmek için içerik eklemenin bu sınıra göre uygulandığı anlamına gelir.

<sup>3</sup> Tek bir ayrı tutma ilkesinde 1.000'den fazla posta kutusunu veya 100'den fazla siteyi beklemeye aldığınızda, sistem saklamayı gerektiği gibi otomatik olarak ölçeklendirir. Bu, sistemin veri konumlarını tek bir ayrı tutma ilkesine eklemek yerine otomatik olarak birden çok ayrı tutma ilkesine ekleyeceği anlamına gelir. Ancak, kuruluş başına 10.000 servis talebi saklama ilkesi sınırı hala geçerlidir.

<sup>4</sup> Tek bir dosya sınırını aşan tüm öğeler işleme hatası olarak gösterilir.

<sup>5</sup> SharePoint ve OneDrive İş konumları ararken, aranan sitelerin URL'lerindeki karakterler bu sınıra göre sayılır. Toplam karakter sayısı şunlardan oluşur:

  - Hem Kullanıcılar hem de Filtreler alanlarındaki tüm karakterler.
  - Kullanıcıya uygulanan tüm arama izinleri filtreleri.
  - Aramadaki ExchangeLocation, PublicFolderLocation, SharPointLocation, ExchangeLocationExclusion, PublicFolderLocationExclusion, SharePointLocationExclusion ve OneDriveLocationExclusion gibi konum özelliklerinden karakterler. Örneğin, aramadaki tüm SharePoint siteleri ve OneDrive hesapları dahil olmak üzere, hem SharePointLocation hem de OneDriveLocation alanında "ALL" sözcüğü görüneceğinden altı karakter olarak sayılır.

<sup>6</sup> Tümcecik olmayan sorgular için (çift tırnak işareti kullanmayan bir anahtar sözcük değeri) özel bir ön ek dizini kullanırız. Bu, bir sözcüğün belgede olduğunu, ancak belgede nerede olduğunu söylemediğini bildirir. Tümcecik sorgusu yapmak için (çift tırnak işaretli bir anahtar sözcük değeri), tümcecikteki sözcüklerin belge içindeki konumunu karşılaştırmamız gerekir. Başka bir deyişle, tümcecik sorguları için ön ek dizinini kullanamayız. Bu durumda, ön ekin genişletilmesi olası tüm sözcüklerle sorguyu dahili olarak genişletiriz; örneğin,  **time\**_ _*"time VEYA timer OR times YA DA timex OR timeboxed OR ..." olarak genişletilebilir**. 10.000 sınırı, sorguyla eşleşen belge sayısı değil, sözcüğün genişletebileceği en fazla değişken sayısıdır. Tümcecik olmayan terimler için üst sınır yoktur.

<sup>7</sup> eBulma (Premium) koleksiyonlarını depolayan Azure Bloblarının kullanım süresi bir yıldır. Bir yıl önce oluşturulan koleksiyonlara artık erişilemeyebilir.
 
<sup>8</sup> Bu sınır, seçilen belgeleri bir gözden geçirme kümesinden indirmek için geçerlidir. Bir gözden geçirme kümesinden belgeleri dışarı aktarmak için geçerli değildir. Belgeleri indirme ve dışarı aktarma hakkında daha fazla bilgi için bkz. [EBulma'da büyük/küçük harf verilerini dışarı aktarma (Premium)](exporting-data-ediscover20.md).
