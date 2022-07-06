---
title: eBulma'da geçmiş sürümleri ayarlama (Premium)
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
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
description: SharePoint ve OneDrive'da depolanan belgelerin tüm sürümlerinden içerik toplamak için eBulma(Premium) içinde geçmiş sürümleri kullanın.
ms.openlocfilehash: 3706da8c9383dfdd3d6b41f309f8b84920648842
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66627745"
---
# <a name="set-up-historical-versions-in-ediscovery-premium-preview"></a>eBulma'da geçmiş sürümleri ayarlama (Premium) (önizleme)

eKeşif (Premium) içindeki geçmiş sürümler özelliği, kuruluşunuzdaki eBulma yöneticilerinin SharePoint Online ve OneDrive İş'da depolanan tüm belge sürümlerinde içerik aramasına ve toplamasına olanak tanır. Ardından bu içeriği analiz ve gözden geçirme için bir gözden geçirme kümesine ekleyebilirsiniz. Bu, aynı belgenin en son sürümü ilgili bilgileri içermese bile, bir belgenin olay veya araştırmayla ilgili olabilecek belirli bir sürümündeki içeriği bulmanıza ve gözden geçirmenize yardımcı olur.

eBulma'daki (Premium) geçmiş sürüm özelliğini desteklemek için, SharePoint yöneticilerinin kuruluşlarındaki sitelerde sürüm oluşturmayı etkinleştirmesi gerekir. Ardından, kullanıcılar SharePoint veya OneDrive'daki belgeleri değiştirdiğinde, belge kaydedildiğinde (veya otomatik kaydedildiğinde) örtük normal sürümler oluşturulur. SharePoint sürüm oluşturma, SharePoint öğelerinde (belgeler, olaylar ve görevler dahil) gerçekleştirilen etkinliğin izlenmesine olanak tanır. Bu sürüm oluşturma özelliği, yasal araştırmalarda kanıt sağlayabilecek bir denetim izi bırakır. Bir belgenin bu eski sürümleri, yasal bir konuda mahkeme keşfi sırasında hassas veya ilgili içeriğe sahip bu tür sürümleri paylaşması gerekebilecek kuruluş tarafından kullanılabilir.

Bir eBulma yöneticisi kuruluşun geçmiş sürümlerini açıp belirli SharePoint siteleri için etkinleştirdikten sonra, SharePoint içerik gönderme hizmeti etkinleştirilmiş sitelerdeki belgelerin tüm önemli ve ikincil sürümlerini tarar ve sonra bu sürümleri dizin oluşturma için gönderir. Gezinme ve dizin oluşturma işlemi tamamlandıktan sonra belgeler ve sürümleri eBulma araması için kullanılabilir. Belirli bir sürüme erişilebildiği sürece (sürüm geçmişine göre) bu sürüm eBulma (Premium) koleksiyonu aramasında bulunabilir.

## <a name="set-up-historical-versions"></a>Geçmiş sürümleri ayarlama

eKeşif'te (Premium) geçmiş sürümleri etkinleştirmek için kuruluşunuzun bu sürümü açıp belirli siteleri etkinleştirmesi gerekir; böylece söz konusu sitelerde depolanan belgelerin tüm sürümleri arama için dizinlenir. Geçmiş sürümler için eBulma 'yı (Premium) ayarlamadan önce SharePoint'te sürüm oluşturma desteğini etkinleştirmeniz gerekir.

### <a name="step-1-turn-on-versioning-in-sharepoint"></a>1. Adım: SharePoint'te sürüm oluşturmayı açma

İlk adım, belgenin tüm sürümlerinin korunması için SharePoint Online'da sürüm oluşturmayı açmaktır. Yönergeler için bkz. [SharePoint'te sürüm oluşturma](/microsoft-365/community/versioning-basics-best-practices).

### <a name="step-2-turn-on-historical-versions"></a>2. Adım: Geçmiş sürümleri açma

Bir sonraki adım, eBulma'da (Premium) geçmiş sürümleri açmaktır. Kuruluşunuzun geçmiş sürümlerini açmak için, bir kişinin genel yönetici veya eBulma Yöneticisi (eBulma Yöneticisi rol grubundaki eBulma Yöneticisi alt grubunun üyesi) olması gerekir. Geçmiş sürümler açıldıktan sonra tüm kuruluşunuz için geçerli olur.

> [!IMPORTANT]
> Geçmiş sürümleri etkinleştirdikten sonra, genel önizleme sırasında kapatamazsınız. Geçmiş sürümler genel kullanıma sunulduktan sonra kapatabilirsiniz.

1. Microsoft Purview uyumluluk portalı [, eBulma (Premium)](https://go.microsoft.com/fwlink/p/?linkid=2173764) seçeneğine gidin ve **ardından eBulma (Premium) ayarları'na** tıklayın.

   ![eBulma (Premium) ayarlarını seçin](..\media\HistoricalVersions1.png)

2. Ayarlar sayfasında **Geçmiş sürümler (önizleme)** sekmesini seçin ve geçmiş **sürümler kiracı denetimi** iki durumlu düğmesini açık konuma getirin.

   ![Geçmiş sürümleri etkinleştirmek için iki durumlu düğmeyi açma](..\media\HistoricalVersions2.png)

   Geçmiş sürümleri kapatamayacağınızı belirten bir uyarı görüntülenir. Daha önce belirtildiği gibi, özellik genel kullanıma sunulana kadar geçmiş sürümleri kapatamazsınız.

3. Geçmiş sürümleri açmak için **Evet'e** tıklayın.

### <a name="step-3-activate-sharepoint-sites"></a>3. Adım: SharePoint sitelerini etkinleştirme

Kuruluşunuz için geçmiş sürümleri etkinleştirdikten sonra, son adım SharePoint sitelerini geçmiş sürümleri destekleyecek şekilde etkinleştirmektir. Bir siteyi etkinleştirdiğinizde ( **Geçmiş sürümler** sekmesinde site listesine ekleyerek), site yeniden gezinilir ve bu sitede depolanan belgelerin tüm sürümleri arama için dizine eklenir.

> [!NOTE]
> Geçmiş sürümlerin genel önizlemesi sırasında kuruluş başına 100 site etkinleştirmesi sınırı vardır. Geçmiş sürümler için bir siteyi etkinleştirdiğinizde veya devre dışı bırakdığınızda etkinleştirme bu sınıra göre sayılır. Birden çok siteyi etkinleştirirseniz, her site tek bir etkinleştirme olarak sayılır. Etkinleştirmelerin toplam sayısı **Geçmiş sürümler** sekmesinde görüntülenir.

1. eBulma (Premium) **Ayarları** sayfasındaki **Geçmiş sürümler** sekmesinde, siteleri geçmiş sürümler için etkinleştirmek için **Etkinleştir'e** tıklayın.

   ![Geçmiş sürümlere yönelik siteleri etkinleştirmek için Etkinleştir'e tıklayın](..\media\HistoricalVersions3.png)  

   Kuruluşunuzdaki tüm SharePoint sitelerinin listesini içeren bir açılır sayfa görüntülenir.

2. Etkinleştirmek istediğiniz siteyi seçin ve ardından **etkinleştir'e** tıklayarak geçmiş sürümlerde etkinleştirin. Belirli bir siteyi aramak için arama kutusunu kullanabilirsiniz.

   Sitedeki belge sürümlerinin dizine alınacağını ve bu dizin oluşturma işleminin sürümlerin aranmaya hazır olması için biraz zaman alacağını belirten bir uyarı görüntülenir. Uyarı ayrıca seçilen sitenin geçmiş sürümlerini 30 gün boyunca devre dışı bırakamayacağınızı belirtir.

3. Siteyi geçmiş sürümler için etkinleştirmek için **Evet'e** tıklayın.

   ![Etkinleştirilmiş site ve site etkinleştirmelerinin sayısı görüntülenir](..\media\HistoricalVersions4.png)  

   Site, etkinleştirilmiş siteler listesine eklenir. Site etkinleştirmelerinin sayısını gösteren sayaç da güncelleştirilir.

4. Geçmiş sürümler için etkinleştirmek istediğiniz her site için önceki adımları yineleyin.

## <a name="frequently-asked-questions"></a>Sık sorulan sorular

**Bir taslak koleksiyonu gözden geçirme kümesine işlerken "tüm sürümleri toplama" seçeneğinin geçmiş sürümleri arasında ne fark vardır?**

Şu anda arama için belgelerin yalnızca en son sürümü dizine alınmış durumdadır. Başka bir deyişle, taslak koleksiyonu çalıştırdığınızda yalnızca belgelerin en son sürümleri aranabilir. Belge koleksiyon için anahtar sözcük sorgusuyla eşleşiyorsa, koleksiyon sonuçlarında döndürülür. Ancak, belgenin en son sürümü bir arama sorgusuyla eşleşmiyorsa, belgenin eski sürümleri anahtar sözcüğü içeriyorsa belge döndürülmez. Bu durumu hafifletmeye yardımcı olmak için eBulma (Premium), [bir koleksiyonu bir gözden geçirme kümesine işlerken](commit-draft-collection.md#commit-a-draft-collection-to-a-review-set) belgenin tüm sürümlerini toplamanıza olanak sağlar. Bu, anahtar sözcüğü içerebilecek eski sürümlerin gözden geçirme kümesine ekleneceğini gösterir.

Bir siteyi etkinleştirdiğinizde, belgenin tüm sürümleri (yalnızca son sürüm değil) arama için dizine eklendiğinden, geçmiş sürümler "tüm sürümleri toplama"dan farklı ve daha verimlidir. Sonuç olarak, belgenin eski bir sürümü arama sorgusuyla eşleşen bir anahtar sözcük içeriyorsa, koleksiyon tarafından döndürülür.

**Bir site için geçmiş sürümler etkinleştirildiğinde, sitenin performansını etkiler mi?**

Hayır. Site için geçmiş sürümler etkinleştirildikten sonra, sitenin performansı site etkinleştirilmeden önceki performansıyla aynı olur. Etkinleştirildikten sonra sitede gerçekleştirilen gezinme ve dizin oluşturma işlemleri daha yavaş bir hızda gerçekleşir ve yoğun olmayan saatlerde gerçekleştirilir. Bir site için geçmiş sürümlerin etkinleştirilmesi, sitedeki belgelerin tüm sürümlerini bulan ve ardından bu sürümleri dizine gönderen bir geri doldurma işlemi başlatır. Sitenin belge sürümlerinin sayısına bağlı olarak, bu doldurma işlemi hizmet durumunu etkileyebilir. Bu olası etkiyi aşağıdaki yollarla azaltmış olduk:

- Yoğun olmayan saatlerde bu sürümleri işlemek için elimizden geleni yapıyoruz.

- Belge sürümlerini en düşük öncelikli kuyruklarımızda işleriz ve bu da çoğu hizmet kaynağının kullanıcı değişikliklerine temsilci olarak atanmasını sağlar.

**Bir site etkinleştirildikten sonra, bu sitedeki belgelerin tüm geçmiş sürümleri dizine alınana ve eBulma araması için kullanılabilir duruma gelene kadar ne kadar beklemem gerekir?**

Bir sitenin belge sayısına ve belge başına ortalama sürüm sayısına bağlı olarak, site başına toplam dosya sayısını tahmin etmeye çalışırız. Buna bağlı olarak, dizin oluşturmanın ne kadar sürebileceğine ilişkin bir tahmin aşağıdaki gibidir:

`Number of versions / (Processing rate of 100,000 files per day ) + .5 days = Total number of days to process a site`

Sitedeki sürümlerin dizinlenmesi yoğun olmayan saatlerde çalışacak şekilde iyileştirildiğinden yarım gün arabelleğe eklenir.

Örneğin, bir sitenin toplam belge sayısı ve tüm sürümleri 150.000 ise sitenin geçmiş sürümleri için işlenmesi en az iki gün sürer:

`150,000 files/100,000 files per day + .5 days = 2 days`

**Geçmiş sürümler için sitelerin sık sık etkinleştirilmesi veya devre dışı bırakılması neden önerilmez?**

Önceden etkinleştirilmiş bir siteyi devre dışı bıraktığınızda bir temizleme işlemi tetikleniyor. Bu işlemin tamamlanması zaman alacaktır. Aynı site yeniden etkinleştirilirse, sitenin yeniden dizine alınması için geri doldurma işleminin yeniden çalıştırılması gerekir. Hem temizleme hem de geri doldurma işlemleri zaman ve yoğun kaynak kullanır. Bu nedenle, bir sitenin geçmiş sürümlerini tekrar tekrar etkinleştirmekten ve devre dışı bırakmaktan kaçınmak için hangi siteleri geçmiş sürüm için etkinleştirmek istediğinizi dikkatle düşünmenizi ve planlamanızı öneririz.
