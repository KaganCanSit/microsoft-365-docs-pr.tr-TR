---
title: Yeni sürümlerde geçmiş sürümleri Advanced eDiscovery
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
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: ''
description: Advanced eDiscovery ve Advanced eDiscovery belgelerde depolanan tüm belge sürümlerinden içerik toplamak için SharePoint geçmiş OneDrive.
ms.openlocfilehash: 5ecbb9c9216482223ce756aed5742e25a3b851a1
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2022
ms.locfileid: "63028427"
---
# <a name="set-up-historical-versions-in-advanced-ediscovery-preview"></a>Yeni sürümlerde geçmiş sürümleri Advanced eDiscovery (önizleme)

Advanced eDiscovery'daki geçmiş sürümler özelliği, eBulma yöneticilerinin SharePoint Online'da depolanan belgelerin tüm sürümlerinde içerik aramalarına ve toplamalarına olanak OneDrive İş. Ardından, bu içeriği çözümleme ve gözden geçirme için bir gözden geçirme kümesine  eklersiniz. Bu, aynı belgenin en son sürümü ilgili bilgileri içermese bile, belgenin bir olay veya soruşturmayla ilgili olabilir belirli bir sürümünden içerik bulup gözden geçirmenizi sağlar.

Kuruluşta geçmiş sürüm özelliğinin destek Advanced eDiscovery için SharePoint yöneticilerinin, kuruluşlarında siteler için sürümleri etkinleştirmesi gerekir. Ardından, kullanıcılar belgelerde veya SharePoint OneDrive, belge kaydedili (veya otomatik kaydedili) zaman, örtülü normal sürümler oluşturulur. SharePoint sürümü oluşturma, belirli öğeler (belgeler, olaylar ve görevler SharePoint) üzerinde gerçekleştirilen etkinliğin izlemeye olanak sağlar. Bu sürüm özelliği, yasal soruşturmalarda kanıt sağ sağlayacak bir denetim izi bırakır. Bir belgenin bu eski sürümleri kuruluş tarafından kullanılabilir ve hukuk davaları sırasında hassas veya ilgili içerikleri olan bu sürümleri paylaşmaları gerekebilir.

eBulma yöneticisi kuruluş için geçmiş sürümleri etkinleştirip belirli SharePoint sitelerinde etkinleştirdikten sonra, SharePoint içeriği anında gönderme hizmeti etkinleştirilmiş sitelerde bulunan belgelerin tüm ana ve ikincil sürümlerinde geziniyor ve ardından bu sürümleri dizin oluşturma için gönderiyor. Gezinme ve dizin oluşturma işlemi tamamlandıktan sonra, eBulma araması için belgeler ve sürümleri kullanılabilir. Belirli bir sürüme erişilebilir olduğu sürece (sürüm geçmişine göre), bu sürüm bir koleksiyon Advanced eDiscovery aranabilir.

## <a name="set-up-historical-versions"></a>Geçmiş sürümleri ayarlama

Office 365'te Advanced eDiscovery geçmiş sürümlerini etkinleştirmek için, kuruluşlarının bu özelliği etkinleştirmesi ve ardından belirli siteleri etkinleştirmesi gerekir; böylece bu sitelerde depolanan belgelerin tüm sürümleri arama için dizine kaydedilir. Geçmiş sürümler için Advanced eDiscovery ayarlamadan önce, geçmiş sürümler için sürümler için sürüm SharePoint.

### <a name="step-1-turn-on-versioning-in-sharepoint"></a>1. Adım: SharePoint'de sürüm SharePoint

İlk adım, bir belgenin tüm sürümlerinin korunması için SharePoint Online'da sürüm oluşturmanın açmaktır. Yönergeler için bkz. [SharePoint'de Sürüm SharePoint](/microsoft-365/community/versioning-basics-best-practices).

### <a name="step-2-turn-on-historical-versions"></a>2. Adım: Geçmiş sürümleri açma

Sonraki adım, bu sürümlerde geçmiş sürümleri Advanced eDiscovery. Kuruluşun geçmiş sürümlerini açmak için, bir kişinin genel yönetici veya eBulma Yöneticisi (eBulma Yöneticisi rol grubunda eBulma Yöneticisi alt grubunun üyesi) olması gerekir. Geçmiş sürümler açık olduktan sonra, tüm kuruluş için geçerli olur.

> [!IMPORTANT]
> Geçmiş sürümleri paylaştıktan sonra, genel önizleme sırasında bunu kapata sıralayam. Geçmiş sürümler genel kullanılabilirlik için yayın geçirildikten sonra bu özelliği kapatabileceksiniz.

1. Sayfa Microsoft 365 uyumluluk merkezi, [Ayarlar'a Advanced eDiscovery](https://go.microsoft.com/fwlink/p/?linkid=2173764) ve Ayarları **Değiştir'Advanced eDiscovery tıklayın**.

   ![Advanced eDiscovery seçin](..\media\HistoricalVersions1.png)

2. Geçmiş **Ayarlar**, Geçmiş sürümleri **(önizleme)** sekmesini seçin ve geçmiş sürümleri kiracı **denetimi iki** durumlu düğmesi açık olarak ayarlayın.

   ![Geçmiş sürümleri etkinleştirmek için iki durumlu düğmeyi açma](..\media\HistoricalVersions2.png)

   Geçmiş sürümleri kapatamayabileceksiniz uyarı görüntülenir. Daha önce de belirtildiği gibi, özellik genel kullanılabilirlik için yayımlanana kadar geçmiş sürümleri kapatabilirsiniz.

3. Geçmiş **sürümleri** açmak için Evet'i tıklatın.

### <a name="step-3-activate-sharepoint-sites"></a>3. Adım: SharePoint etkinleştirme

Siz kuruluş için geçmiş sürümleri etkinleştirdikten sonra, son adım geçmiş sürümleri desteklemek SharePoint siteleri etkinleştirmektir. Bir siteyi etkinleştirerek (Geçmiş sürümleri sekmesindeki sitelerin listesine ekleyerek), site  yeniden kıvrıldı ve arama için bu sitede depolanan belgelerin tüm sürümleri dizine kaydedilir.

> [!NOTE]
> Geçmiş sürümlerin genel önizlemesi sırasında kuruluş başına 100 site etkinleştirmesi sınırlaması vardır. Bir siteyi geçmiş sürümler için her etkinleştirileştirmeniz veya devre dışı bırakmanız sırasında etkinleştirme bu sınırda sayılır. Birden çok siteyi etkinleştirirsiniz, her site tek bir etkinleştirme olarak sayılır. Toplam etkinleştirme sayısı Geçmiş sürümleri **sekmesinde** görüntülenir.

1. Geçmiş sürümleri **sekmesinin** Geçmiş sürümleri sekmesinde Advanced eDiscovery **Ayarlar** **etkinleştir'e** tıklayın.

   ![Geçmiş sürümlerde siteleri etkinleştirmek için Etkinleştir'e tıklayın](..\media\HistoricalVersions3.png)  

   Tüm site sitelerinin listesini içeren, bir SharePoint sayfası görüntülenir.

2. Etkinleştirmek istediğiniz siteyi seçin ve geçmiş sürümlerde **etkinleştirmek** için Etkinleştir'e tıklayın. Belirli bir siteyi aramak için arama kutusunu kullanabilirsiniz.

   Site'nin belge sürümlerinin dizine a olacağını ve bu dizin oluşturma işleminin sürümlerde arama yapmaya hazır olması için biraz zaman gerek olacağını söyleyen bir uyarı görüntülenir. Ayrıca uyarıda, seçili site için geçmiş sürümleri 30 gün boyunca devre dışı bırakılamayacak da uyarısı yer almaktadır.

3. **Siteyi geçmiş** sürümlerde etkinleştirmek için Evet'i tıklatın.

   ![Etkinleştirilmiş site ve site etkinleştirme sayısı görüntülenir](..\media\HistoricalVersions4.png)  

   Site, etkinleştirilen siteler listesine eklenir. Site etkinleştirme sayısını gösteren sayaç da güncelleştirilir.

4. Geçmiş sürümler için etkinleştirmek istediğiniz her site için önceki adımları yineler.

## <a name="frequently-asked-questions"></a>Sık sorulan sorular

**Taslak koleksiyonunu gözden geçirme kümesine işlerken geçmiş sürümlerin "tüm sürümleri toplama" seçeneği arasında ne fark vardır?**

Şu anda, arama için yalnızca belgelerin en son sürümü dizine alındı. Bu, bir taslak koleksiyonunu çalıştırarak yalnızca son belge sürümlerinde aramanın olduğu anlamına gelir. Bir belge koleksiyonun anahtar sözcük sorgusuyla eşlerise, sonuç olarak döndürülür. Öte yandan, belgenin en son sürümü bir arama sorgusuyla eşlştir, belgenin daha eski sürümleri anahtar sözcüğü içeriyorsa belge döndürülür. Bu durumu azaltmak için, Advanced eDiscovery bir gözden geçirme kümesine koleksiyon işlerken belgenin tüm sürümlerini [toplamanıza yardımcı olur](commit-draft-collection.md#commit-a-draft-collection-to-a-review-set). Bu, anahtar sözcüğü içeren tüm eski sürümler gözden geçirme kümesine eklenecektir.

Geçmiş sürümler, "tüm sürümleri toplama" özelliğinden farklıdır ve "tüm sürümleri toplama" yerine daha verimlidir çünkü bir siteyi etkinleştirirken, arama için belgenin tüm sürümleri (yalnızca son sürümü değil) dizine alındı. Sonuçta, belgenin daha eski bir sürümünde arama sorgusuyla eşleşen bir anahtar sözcük varsa, bu anahtar sözcük koleksiyon tarafından döndürülür.

**Geçmiş sürümleri bir site için etkinleştirildiğinde, bu sitenin performansını etkiler mi?**

Hayır. Geçmiş sürümleri bir site için etkinleştirildikten sonra, sitenin performansı site etkinleştirilmeden öncekiyle aynı olur. Site etkinleştirildikten sonra sitede gerçekleştirilen gezinme ve dizin oluşturma işlemleri daha yavaş bir oranda gerçekleştirilir ve yoğun olmayan saatlerde yapılır. Bir sitenin geçmiş sürümlerinin etkinleştirilmesi, siteden tüm belge sürümlerini bulan ve sonra bu sürümleri dizine gönderen bir doldurma işlemiyle tamamlar. Sitenin belge sürümlerinin sayısına bağlı olarak, bu doldurma işlemi hizmet durumunu etkileyebilirsiniz. Şu şekillerde bu olası etkinin etkisini azaltıldı:

- Bu sürümleri yoğun olmayan saatlerde işlemeye elimizden gelenin en iyisini gösteriyoruz.

- Çoğu hizmet kaynağına kullanıcı değişiklikleri temsilciliği sağlayan en düşük öncelikli sıralarımız içinde belge sürümlerini işlemeye devam ediyoruz.

**Site etkinleştirildikten sonra bu sitenin tüm geçmiş sürümlerinin hepsi dizine alınana ve eBulma araması için kullanılabilene kadar ne kadar beklemem gerekir?**

Sitenin belge sayısına ve belge başına ortalama sürüm sayısına bağlı olarak, site başına toplam dosya sayısını tahmin etmeye çalışabiliyoruz. Buna bağlı olarak, dizin oluşturmanın ne kadar sürecesi olduğunu tahmin eden aşağıdakiler yer alır:

`Number of versions / (Processing rate of 100,000 files per day ) + .5 days = Total number of days to process a site`

Site'de sürümlerin dizin oluşturması yoğun olmayan saatlerde çalıştıracak şekilde iyileştirilmiş olduğundan yarım gün ara bellek olarak eklenir.

Örneğin, sitenin toplam belge sayısı ve tüm sürümleri 150.000 ise, geçmiş sürümlerin siteyi işlemesi en az iki gün sürer:

`150,000 files/100,000 files per day + .5 days = 2 days`

**Geçmiş sürümlerde siteleri sık sık etkinleştirmeniz veya devre dışı bırakmanız neden önerilmez?**

Daha önce etkinleştirilen bir siteyi devre dışı bırakıldığında temizleme işlemi tetiklenir. Bu sürecin tamamlanması biraz zaman alır. Aynı site yeniden etkinleştirilirse, siteyi yeniden yeniden depolama işleminin yeniden etkinleştirilmesi gerekir. Hem temizleme hem de geri doldurma işlemleri zaman ve kaynak kullanımı yoğun olur. Bu nedenle, bir sitenin geçmiş sürümlerini tekrar tekrar etkinleştirmeyi ve devre dışı bırakmayı önlemek için, geçmiş sürümler için hangi siteleri etkinleştirmek istediğiniz dikkatle değerlendirmenizi ve planlamanızı öneririz.
