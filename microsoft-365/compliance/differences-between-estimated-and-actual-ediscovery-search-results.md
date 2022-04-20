---
title: Tahmini ve gerçek eBulma arama sonuçları
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
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- SPO160
- MOE150
- MET150
ms.assetid: 8f20ca4f-a908-46ec-99e6-9890d269ecf2
description: Office 365'deki eBulma araçlarıyla yapılan aramalarda tahmini ve gerçek arama sonuçlarının neden farklılık gösterebileceğini anlayın.
ms.openlocfilehash: a71b246b71e7b3cca3ef361510042b6292c36c8b
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/20/2022
ms.locfileid: "64993962"
---
# <a name="differences-between-estimated-and-actual-ediscovery-search-results"></a>Tahmini ve gerçek eBulma arama sonuçları arasındaki farklar

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Bu makale, aşağıdaki Microsoft 365 eBulma araçlarından birini kullanarak çalıştırabileceğiniz aramalar için geçerlidir: 

- İçerik arama
- eKeşif (Standart)

Bir eBulma araması çalıştırdığınızda, kullanmakta olduğunuz araç arama ölçütleriyle eşleşen öğe sayısına (ve toplam boyutuna) ilişkin bir tahmin döndürür. Örneğin, Microsoft Purview uyumluluk portalında bir arama çalıştırdığınızda, seçilen aramanın açılır sayfasında tahmini arama sonuçları görüntülenir.
  
![Arama açılır sayfasında görüntülenen sonuçların tahmini.](../media/EstimatedSearchResults1.png)
  
Bu, sonuçları yerel bir bilgisayara ve arama sonuçlarıyla birlikte indirilen Dışarı Aktarma Özeti raporunda dışarı aktardığınızda eBulma Dışarı Aktarma Aracı'nda görüntülenen toplam boyut ve öğe sayısıyla aynı tahmindir.
  
**eBulma Dışarı Aktarma aracındaki tahmini sonuçlar**

![eBulma Dışarı Aktarma aracında tahmini sonuçlar.](../media/d34312a5-0ee6-49aa-9460-7ea0015a6e66.png)
  
**Dışarı Aktarma Özeti raporundaki tahmini sonuçlar**

![Tahmini arama sonuçları Dışarı Aktarma Özeti raporuna eklenir.](../media/44b579da-86c2-4f33-81b5-84d604003eda.png)
  
Ancak, Dışarı Aktarma Özeti raporunun önceki ekran görüntüsünde fark ettiğiniz gibi, indirilen gerçek arama sonuçlarının boyutu ve sayısı tahmini arama sonuçlarının boyutundan ve sayısından farklıdır.
  
![Tahmini ve indirilen arama sonuçları arasındaki fark.](../media/84aef318-230f-430d-9d9e-02f21342d364.png)
  
Bu farklılıkların bazı nedenleri şunlardır:
  
- **Sonuçların tahmin şekli**. Arama sonuçlarının tahmini, arama sorgusu ölçütlerini karşılayan öğelerin tahminidir (gerçek sayı değil). Exchange öğelerinin tahminini derlemek için, kullandığınız eBulma aracı tarafından Exchange veritabanından arama ölçütlerine uyan ileti kimliklerinin listesi istenir. Ancak arama sonuçlarını dışarı aktardığınızda, arama yeniden çalıştırılır ve gerçek iletiler Exchange veritabanından alınır. Dolayısıyla bu farklar, tahmini öğe sayısı ve gerçek öğe sayısının nasıl belirlendiği nedeniyle ortaya çıkabilir.

- **Arama sonuçlarını tahmin etme ve dışarı aktarma zamanı arasında gerçekleşen değişiklikler**. Arama sonuçlarını dışarı aktardığınızda, arama dizininde arama ölçütlerine uyan en son öğeleri toplamak için arama yeniden başlatılır. Tahmini arama sonuçlarının toplandığı zaman ile arama sonuçlarının dışarı aktarıldığı zaman arasında arama ölçütlerini karşılayan ek öğeler oluşturulmuş, gönderilmiş veya alınmış olabilir. Arama sonuçları dışarı aktarılmadan önce içerik konumundan temizlendikleri için arama sonuçları tahmin edildiğinde arama dizininde yer alan öğelerin artık orada olmaması da mümkündür. Bu sorunu azaltmanın bir yolu, eBulma araması için bir tarih aralığı belirtmektir. Bir diğer yol da öğelerin korunması ve temizlenememeleri için içerik konumlarına ayrı tutmaktır.

   Tahmini ve dışarı aktarılan arama sonuçları arasındaki farklara neden olabilecek diğer sorunlar şunlardır:

  - Tarih sorgusu kullanılırken öğelerde artış. Bunun nedeni genellikle aşağıdaki iki nedendir:

  - sürüm oluşturma SharePoint tutun. Bir belge, beklemedeki bir siteden silinirse ve belge sürümü oluşturma etkinleştirilirse, silinen belgenin tüm sürümleri korunur.

  - Takvim öğeleri. İletileri kabul edin ve reddedin; yinelenen toplantılar otomatik olarak eski tarihlerle arka planda yeni öğeler oluşturmaya devam eder.

  - Ayrı tutmalarla, aynı öğenin kullanıcının birincil posta kutusunda ve arşiv posta kutusunda korunduğu durumlar olabilir. Kullanıcı bir öğeyi arşivine el ile taşırsa bu durum oluşabilir.

  - Bir ayrı tutma uygulandığında bile nadir olsa da, yerleşik takvim öğelerinin bakımı (kullanıcı tarafından düzenlenemez, ancak birçok arama sonucuna dahil edilir) zaman zaman kaldırılabilir. Takvim öğelerinin bu düzenli olarak kaldırılması, dışarı aktarılan öğe sayısı azalacaktır.

- **Dizine alınmamış öğeler**. Arama için dizine alınmamış öğeler, tahmini ve gerçek arama sonuçları arasında farklılıklara neden olabilir. Arama sonuçlarını dışarı aktarırken dizine alınmamış öğeler ekleyebilirsiniz. Arama sonuçlarını dışarı aktarırken dizine alınmamış öğeler eklerseniz, dışarı aktarılan daha fazla öğe olabilir. Bu, tahmini ve dışarı aktarılan arama sonuçları arasında farka neden olur.

    İçerik arama aracını kullanırken, arama sonuçlarını dışarı aktarırken dizine alınmamış öğeleri ekleme seçeneğiniz vardır. Arama tarafından döndürülen dizinlenmemiş öğelerin sayısı, diğer tahmini arama sonuçlarıyla birlikte açılır sayfada listelenir. Dizine alınmamış öğeler, tahmini arama sonuçlarının toplam boyutuna da dahil edilir. Arama sonuçlarını dışarı aktardığınızda, dizinlenmemiş öğeleri dahil etme veya eklememe seçeneğiniz vardır. Bu seçenekleri nasıl yapılandırdığınız, tahmini ve indirilen gerçek arama sonuçları arasında farklara neden olabilir.

- **Tüm içerik konumlarını içeren bir İçerik aramasının sonuçlarını dışarı aktarma**. Sonuçları dışarı aktardığınız arama kuruluşunuzdaki tüm içerik konumlarında yapılan bir aramaysa, yalnızca arama ölçütlerine uyan öğeleri içeren içerik konumlarındaki dizine alınmamış öğeler dışarı aktarılır. Başka bir deyişle, bir posta kutusunda veya sitede arama sonucu bulunamazsa, bu posta kutusu veya sitedeki dizine alınmamış öğeler dışarı aktarılmaz. Ancak, tüm içerik konumlarındaki dizine alınmamış öğeler (arama sorgusuyla eşleşen öğeler içermeyen öğeler bile) tahmini arama sonuçlarına eklenir.

    Alternatif olarak, dahil edilen belirli içerik konumlarından sonuçları dışarı aktardığınız arama, aramada belirtilen tüm içerik konumlarından dizine alınmamış öğeler (arama ölçütleri tarafından dışlanmayan) dışarı aktarılır. Bu durumda, tahmini dizinlenmemiş öğe sayısı ve dışarı aktarılan dizinlenmemiş öğe sayısı aynı olmalıdır.

    Dizine alınmamış öğelerin kuruluştaki her konumdan dışarı aktarılmamasının nedeni, dışarı aktarma hataları olasılığını artırıp arama sonuçlarını dışarı aktarmak ve indirmek için gereken süreyi artırabileceğidir.

- **SharePoint ve OneDrive arama tahminlerine dahil olmayan dizine alınmamış öğeler**. SharePoint sitelerden ve OneDrive İş hesaplarından dizine alınmamış öğeler tahmini arama sonuçlarına dahil edilmez. Bunun nedeni, SharePoint dizininin dizine eklenmemiş öğeler için veri içermemesidir. Arama tahminlerine yalnızca posta kutularından dizine alınmamış öğeler eklenir. Ancak, arama sonuçlarını dışarı aktarırken dizine alınmamış öğeler eklerseniz, SharePoint ve OneDrive dizine alınmamış öğeler dahil edilir ve bu da aslında dışarı aktarılan öğelerin sayısını artırır. Bu, tahmini sonuçlar (SharePoint ve OneDrive sitelerindeki dizinlenmemiş öğeleri içermez) ile indirilen gerçek öğeler arasında farklara neden olur. Dizine alınmamış öğeleri yalnızca arama ölçütleriyle eşleşen öğeleri içeren içerik konumlarından dışarı aktarma kuralı bu durumda da geçerlidir.

- **SharePoint ve OneDrive belge sürümleri**. SharePoint siteleri ve OneDrive hesapları ararken, tahmini arama sonuçları sayısına belgenin birden çok sürümü dahil değildir. Ancak arama sonuçlarını dışarı aktarırken tüm belge sürümlerini dahil etme seçeneğiniz vardır. Arama sonuçlarını dışarı aktarırken belge sürümlerini eklerseniz, dışarı aktarılan öğelerin gerçek sayısı (ve toplam boyutu) artırılır.

- **klasörleri SharePoint**. SharePoint'daki klasörler arama sorgusuyla eşleşiyorsa (örneğin tarihe göre arama), arama tahmini son değiştirme tarihi aralığına sahip klasörlerin sayısını içerir (ancak bu klasörlerdeki öğeler dahil değildir). Arama sonuçlarını dışarı aktardığınızda, klasördeki öğeler dışarı aktarılır, ancak gerçek klasör dışarı aktarılamaz. Sonuç, dışarı aktarılan öğelerin sayısının tahmini arama sonuçlarının sayısından daha fazla olmasıdır. Klasör boşsa, gerçek klasör dışarı aktarılmadığından dışarı aktarılan gerçek arama sonuçlarının sayısı bir öğe azaltılır.

   > [!NOTE]
   > Sorgu tabanlı arama çalıştırırken, sorguya aşağıdaki koşulu ekleyerek SharePoint klasörleri hariç tutabilirsiniz: `NOT(ContentType:folder)`.

- **SharePoint listeleri**. SharePoint listesinin adı bir arama sorgusuyla eşleşiyorsa, arama tahmini listedeki tüm öğelerin sayısını içerir. Arama sonuçlarını dışarı aktardığınızda, liste (ve liste öğeleri) tek bir CSV dosyası olarak dışarı aktarılır. Bu, gerçekten dışarı aktarılan öğelerin gerçek sayısını azaltır. Listede ekler varsa, ekler ayrı belgeler olarak dışarı aktarılır ve bu da dışarı aktarılan öğelerin sayısını artırır.

   > [!NOTE]
   > Sorgu tabanlı arama çalıştırırken, sorguya aşağıdaki koşulu ekleyerek SharePoint listeleri dışlayabilirsiniz: `NOT(ContentType:list)`.

- **Ham dosya biçimleri ve dışarı aktarılan dosya biçimleri**. Exchange öğeler için, arama sonuçlarının tahmini boyutu ham Exchange ileti boyutları kullanılarak hesaplanır. Ancak, e-posta iletileri bir PST dosyasında veya tek tek iletiler olarak (EML dosyaları olarak biçimlendirilir) dışarı aktarılır. Bu dışarı aktarma seçeneklerinin her ikisi de ham Exchange iletilerinden farklı bir dosya biçimi kullanır ve bu da dışarı aktarılan toplam dosya boyutunun tahmini dosya boyutundan farklı olmasına neden olur.

- **Dışarı aktarma sırasında Exchange öğelerinin yinelenenlerini kaldırma**. Exchange öğeler için yinelenenleri kaldırma, dışarı aktarılan öğelerin sayısını azaltır. Arama sonuçlarını dışarı aktarırken yinelenenleri kaldırma seçeneğiniz vardır. Exchange iletilerde, bu ileti birden çok posta kutusunda bulunabilse bile iletinin yalnızca tek bir örneğinin dışarı aktarılacağı anlamına gelir. Tahmini arama sonuçları bir iletinin her örneğini içerir. Dolayısıyla, arama sonuçlarını dışarı aktarırken yinelenenleri kaldırma seçeneğini belirlerseniz, dışarı aktarılan öğelerin gerçek sayısı tahmini öğe sayısından çok daha az olabilir.

Arama sonuçları raporu (Results.csv dosyası) her yinelenen ileti için bir girdi içerir ve yinelenen iletinin bulunduğu kaynak posta kutusunu tanımlar. Bu, yinelenen ileti içeren tüm posta kutularını belirlemenize yardımcı olur.

> [!NOTE]
> Arama sonuçlarını dışarı aktarırken veya yalnızca raporları indirirken **Şifrelenmiş veya tanınmayan biçime sahip öğeleri dahil et** seçeneğini belirtmezseniz, dizin hata raporları indirilir ancak hiçbir girdileri yoktur. Bu, dizin oluşturma hatası olmadığı anlamına gelmez. Yalnızca, dizine alınmamış öğelerin dışarı aktarmaya dahil edilmediğini gösterir.
