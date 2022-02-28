---
title: Taslak koleksiyonu oluşturma
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
ms.reviewer: nickrob
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Taslak koleksiyonu, koleksiyonun arama sorgusuyla eşleşen bir arama tahminini döndüren bir Advanced eDiscovery durumundaki özel ve özel olmayan veri kaynaklarının eBulma aramasıdır. Arama istatistiklerini gözden geçirebilirsiniz, öğelerin örneklemesini önizler ve sonuçları gözden geçirme kümesine işlemeden önce koleksiyonu düzeltebilirsiniz ve yeniden çalıştırabilirsiniz.
ms.openlocfilehash: 5a65bc97f44b2b5bf32f57f52000e66d68dc428a
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62988600"
---
# <a name="create-a-draft-collection-in-advanced-ediscovery"></a>Web'de taslak Advanced eDiscovery

Dava için koruyucuları ve koruyucu olmayan veri kaynaklarını tanımdikten sonra, uygun olan bir dizi belgeyi tanımlamaya ve bulmaya hazır olursanız. Bunu yapmak için Koleksiyonlar aracını kullanarak veri kaynaklarında ilgili içeriği arayabilirsiniz. Bunu, belirtilen veri kaynaklarında arama ölçütlerinize uyan içerikler için arama yapacak bir koleksiyon oluşturarak yapar. Öğelerin bulunduğu tahminini alan *bir* taslak koleksiyonu oluşturma seçeneğiniz vardır veya öğeleri gözden geçirme kümesine otomatik olarak ekleyen bir koleksiyon oluşturabilirsiniz. Bir taslak koleksiyonu  oluştururken, bulunan öğelerin toplam sayısı ve boyutu, bunların bulunduğu farklı veri kaynakları ve arama sorgusuyla ilgili istatistikler gibi, arama sorgusuyla eşan tahmini sonuçlar hakkında bilgi edinebilirsiniz. Koleksiyon tarafından döndürülen öğelerden bir örneğinin önizlemesini de görüntüebilirsiniz. Bu istatistikleri kullanarak, arama sorgusunu değiştirebilir ve sonuçlarınızı daraltmak için taslak koleksiyonunu yeniden çalıştırabilirsiniz. Koleksiyon sonuçlarından memnun olduktan sonra, koleksiyonu bir gözden geçirme kümesine işlersiniz. Taslak koleksiyonu işlerken, koleksiyon tarafından döndürülen öğeler gözden geçirme, çözümleme ve dışarı aktarma için bir gözden geçirme kümesine eklenir.

## <a name="before-you-create-a-draft-collection"></a>Taslak koleksiyonu oluşturmadan önce

- Taslak koleksiyonu oluşturmadan önce vakaya koruyucular ve özel olmayan veri kaynakları ekleyin. Taslak koleksiyonu 2013'e kadar olan bu nedenle, veri kaynaklarını seçebilirsiniz. Daha fazla bilgi için bkz.:

  - [Vakaya koruyucular ekleme](add-custodians-to-case.md)

  - [Vakaya özel olmayan veri kaynakları ekleme](non-custodial-data-sources.md)

- Olayla ilgili olması gereken içerikler için bir taslak koleksiyonunda ek veri kaynaklarında (bu vakaya özel veya özel olmayan konumlar olarak ekli veya özel olmayan konumlar) aramaabilirsiniz. Bu veri kaynakları posta kutularını, SharePoint sitelerini ve posta kutularını Teams. Bu durum vakanız için geçerli bir durumsa, bu veri kaynaklarının listesini derle böylelikle bunları koleksiyona ekleyebilirsiniz.

## <a name="create-a-draft-collection"></a>Taslak koleksiyonu oluşturma

1. Görünüm Microsoft 365 uyumluluk merkezi büyük/Advanced eDiscovery açın ve Koleksiyonlar **sekmesini** seçin.

2. Koleksiyonlar **sayfasında New** **collectionStandard** >  **collection'ı seçin**.

3. Koleksiyon için bir ad (gerekli) ve açıklama (isteğe bağlı) yazın. Koleksiyon oluşturulduktan sonra adı değiştiremezsiniz, ancak açıklamayı değiştirebilirsiniz.

4. **Custodial veri kaynakları** sayfasında, içerik toplamak için koruyucu veri kaynaklarını tanımlamak için aşağıdaki şeylerden birini yapın:

   - **Vakaya eklenmiş belirli koruyucuları** aramak için Koruyucu seç'e tıklayın. Bu seçeneği kullanırsanız, koruyucuların listesi görüntülenir. Bir veya daha fazla koruyucu seçin. Koruyucuları seçerek ekledikten sonra, her bir koruyucu için arama yapmak için belirli veri kaynaklarını da kullanabilirsiniz. Görüntülenen bu veri kaynakları, koruyucu eklendiğinde belirtilmiştir.

   - Vakaya **eklenmiş olan** tüm koruyucuları aramak için Tüm koruyucuları seç iki durumlu düğmesini tıklatın. Bu seçeneği tercih ettiyseniz, tüm koruyucular için tüm veri kaynakları aranır.

5. Özel **olmayan veri** kaynakları sayfasında, içerik toplamak için özel olmayan veri kaynaklarını tanımlamak için aşağıdaki işlerden birini yapın:

   - **Vakaya eklenmiş belirli özel olmayan veri** kaynaklarını seçmek için Özel olmayan veri kaynakları seç'e tıklayın. Bu seçeneği kullanırsanız, veri kaynaklarının listesi görüntülenir. Bu veri kaynaklarından birini veya daha fazlasını seçin.

   - Vakaya **eklenmiş,** özel olmayan tüm veri kaynaklarını seçmek için Tüm seç iki durumlu düğmesini tıklatın.

6. Ek **veri kaynakları sayfasında** , koleksiyonun bir parçası olarak arama yapmak için diğer posta kutularını ve siteleri seçin. Bu veri kaynağı türleri, bu durumda özel veya özel olmayan veri konumları olarak eklenmedi. Ayrıca, ek veri kaynaklarını ararken iki seçeneğiniz vardır:

   - Belirli bir hizmete (Exchange posta kutuları, SharePoint OneDrive siteleri veya Exchange ortak klasörler) yönelik tüm içerik konumlarında arama yapmak için, Durum sütununda ilgili Tüm seç iki durumlu **düğmesini tıklatın.**  Bu seçenek, seçili hizmette tüm içerik konumlarında aramanızı sağlar.

   - Hizmet için belirli içerik konumlarında arama yapmak için, Durum sütununda  karşılık gelen Her şeyi seç iki  durumlu düğmesini tıklatın ve ardından belirli içerik konumlarında arama yapmak için Kullanıcılar **,** gruplar veya ekipler (Exchange posta kutuları için) veya Siteleri seçin (SharePoint ve OneDrive siteleri) seçeneğine tıklayın.

7. Koşullar **sayfasında** , önceki sihirbaz sayfalarında tanımlanıyor olan veri kaynaklarından öğe toplamak için kullanılan arama sorgusunu oluşturabilirsiniz. Anahtar sözcükler, özellik:değer çiftleri için arama veya anahtar sözcük listesi kullanabilirsiniz. Koleksiyonun kapsamını daraltmak için çeşitli arama koşulları da  ekleyin. Daha fazla bilgi için bkz [. Koleksiyonlar için arama sorguları oluşturma](building-search-queries.md).

8. Taslak olarak **kaydet veya gözden geçirmek için ekle set sayfasında Koleksiyonu** taslak **olarak kaydet'i seçin**.

   > [!NOTE]
   > Bu sayfada yer alan diğer seçenek öğeleri toplamanıza ve bunları doğrudan bir gözden geçirme kümesine eklemenize olanak sağlar. Koleksiyon sonuçlarının bir örneğine ilişkin istatistikleri gözden geçirebilirsiniz ve bunun için önizlemede görüntülemek için bir taslak koleksiyonu oluşturmak yerine, bu seçenek bu işlemi atlar ve koleksiyonu otomatik olarak gözden geçirme kümesine ekler. Koleksiyonu bir gözden geçirme kümesine eklemek için ikinci seçeneği kullanırsanız, Microsoft Teams ve Yammer'da sohbet görüşme dizilerini bütün olarak toplama ve bulut ekleri (*modern* ekler olarak da denir) toplama gibi yapılandıracak ek ayarlarınız olur. Bu ayarlar hakkında daha fazla bilgi için bkz [. Taslak koleksiyonunu gözden geçirme kümesine kaydetme](commit-draft-collection.md).

9. Koleksiyonunızı **gözden geçirme** sayfasında, önceki sayfalarda yapılandırılan koleksiyon ayarlarını gözden geçirebilirsiniz ve güncelleştirebilirsiniz.

   - **Özet** sekmesi: Koleksiyonun adını ve açıklamasını, koleksiyon arama ölçütlerini, ek veri konumlarını ve koleksiyon türünü gözden geçirerek değiştirebilirsiniz.

   - **Kaynaklar** sekmesi: Koleksiyonun özel ve özel olmayan veri kaynaklarını gözden geçirme ve değiştirme.

10. Taslak **koleksiyonunu oluşturmak** için Gönder'e tıklayın. Koleksiyonun oluşturulmuş olduğunu onaylayan bir sayfa görüntülenir.

## <a name="what-happens-after-you-create-a-draft-collection"></a>Taslak koleksiyonu oluşturdukta ne olur?

Siz bir taslak koleksiyonu oluşturdukta, bu **olayda Koleksiyonlar** sayfasında listelenir ve durum, bunun devam ediyor olduğunu gösterir. Arama **önizlemesi ve tahminleri hazırlama adlı** bir iş de oluşturulur ve **davanın İşleri** sayfasında görüntülenir.

Taslak koleksiyon işlemi sırasında, Advanced eDiscovery koleksiyonda belirttiğiniz arama ölçütlerini ve veri kaynaklarını kullanarak bir arama tahmini gerçekleştirir. Advanced eDiscovery, önizlemede görüntüleyerek, öğelerden örneklemeler hazırlar. Koleksiyon tamamlandığında, Koleksiyon sayfasındaki aşağıdaki sütunlar ve karşılık **gelen değerler** güncelleştirilir:

![Taslak koleksiyonu için durum durumları.](../media/DraftCollectionStatus.png)

- **Durum**: Koleksiyonun durumunu ve türünü gösterir. Tahmini bir **değer,** taslak koleksiyonunun tamamlandıktan sonra olduğunu gösterir. Aynı değer koleksiyonun bir taslak koleksiyonu olduğunu ve gözden geçirme kümesine eklenmemiş olduğunu da gösterir. Durum sütununda **kabul edilen** **değeri koleksiyonun** bir gözden geçirme kümesine ekli olduğunu gösterir.

- **Tahmin durumu**: Tahmini arama sonuçlarının durumunu ve arama tahminleri ile istatistiklerinin gözden geçirimaya hazır olup olmadığını gösterir. Başarılı değeri **, taslak** koleksiyonunun sonuçlarını gözden geçirme için hazır olduğunu gösterir. Bir taslak koleksiyonunu ilk kez gönderdikten sonra koleksiyonun hala  çalışıyor olduğunu göstermek için Sürüyor değeri görüntülenir

- **Önizleme durumu**: Önizlemede görüntü bizim için önemli olan örnek öğelerin durumunu gösterir. Başarılı değeri **, öğelerin** önizleme için hazır olduğunu gösterir. Bir taslak koleksiyonunu ilk kez gönderdikten sonra koleksiyonun hala  çalışıyor olduğunu göstermek için Sürüyor değeri görüntülenir.

## <a name="next-steps-after-a-draft-collection-is-complete"></a>Taslak koleksiyonu tamamlandıktan sonraki adımlar

Taslak koleksiyonu başarıyla tamamlandıktan sonra, çeşitli görevleri gerçekleştirebilirsiniz. Bu görevlerin çoğunu gerçekleştirmek için, Koleksiyonlar sekmesine gidip açılır sayfayı görüntülemek üzere taslak koleksiyonunun adına tıklamanız gerekir.

![Taslak koleksiyonu için uç uçarak çıkış sayfası.](../media/DraftCollectionFlyoutPage.png)

Koleksiyon uç sayfasıyla şunları yapacaksınız:

- Koleksiyon hakkında **özet** bilgileri ve koleksiyonun geri döndürülen tahmini arama sonuçlarını görüntülemek için Özet sekmesini seçin. Bu, toplam öğe sayısını ve tahmini arama sonuçlarının boyutunu, arama sonuçlarını içeren posta kutularının ve sitelerin sayısını ve koleksiyonun kapsamını bulmak için kullanılan arama koşullarını (kullanılmışsa) içerir.

- Koleksiyonda **arama yapılan** koruyucuların ve özel olmayan veri kaynaklarının listesini görüntülemek için Veri kaynakları sekmesini seçin. Arama yapılan ek içerik konumları, Özet sekmesinde **Konumlar** **altında listelenir** .

- Koleksiyonla **ilgili istatistikleri** görüntülemek için Arama istatistikleri sekmesini seçin. Bu, her hizmette bulunan öğelerin toplam sayısını ve boyutunu (örneğin, Exchange posta kutuları veya SharePoint siteleri) ve koleksiyon tarafından kullanılan arama sorgusunun farklı bileşenleri tarafından döndürülen öğelerin sayısıyla ilgili istatistikleri görüntüleyen bir koşul raporunu içerir. Daha fazla bilgi için bkz [. Koleksiyon istatistikleri ve raporları](collection-statistics-reports.md).

- **Koleksiyonun geri** döndürülen öğelerinin bir örneğini önizlemek için, Örneği gözden geçir (uçtaki sayfanın en altında yer alan) tıklatın.

- Taslak koleksiyonunu gözden geçirme kümesine işlemek (**ActionsEdit koleksiyonu'ne** >  tıklayarak). Bu, koleksiyonu yeniden çalıştırmanıza (geçerli ayarları kullanarak) ve koleksiyon tarafından döndürülen öğeleri gözden geçirme kümesine eklemeniz anlamına gelir. Daha önce de açıklanmıştır; koleksiyonu bir gözden geçirme kümesine eklerken ek ayarları da (konuşma parçacığı ve bulut tabanlı ekler gibi) yapılandırabilirsiniz. Daha fazla bilgi ve adım adım yönergeler için bkz. [Taslak koleksiyonunu gözden geçirme kümesine kaydetme](commit-draft-collection.md).

## <a name="manage-a-draft-collection"></a>Taslak koleksiyonunu yönetme

Çeşitli yönetim görevlerini gerçekleştirmek için **, taslak** koleksiyonunun açılır sayfasındaki Eylemler menüsündeki seçenekleri kullanabilirsiniz.

![Taslak koleksiyonu için Eylemler menüsündeki seçenekler.](../media/DraftCollectionActionsMenu.png)

Yönetim seçeneklerinin açıklamaları şunlardır.

- **Koleksiyonu düzenle**: Taslak koleksiyonunun ayarlarını değiştirin. Değişikliklerden sonra koleksiyonu yeniden çalıştırarak, arama tahminlerini ve istatistiklerini güncelleştirin. Daha önce de belirtildiği gibi, taslak koleksiyonunu gözden geçirme kümesine işlemek için bu seçeneği kullanırsanız.  

- **Koleksiyonu silme**: Taslak koleksiyonunu silme. Taslak koleksiyon bir gözden geçirme kümesi olarak kabul edildikten sonra silinemez.

- **Yenileme tahminleri**: Arama tahminlerini ve istatistikleri güncelleştirmek için, sorguyu (veri kaynakları üzerinde) taslak koleksiyonunda belirtilen şekilde yeniden çalıştırma.

- **Rapor olarak dışarı** aktarma: Taslak koleksiyonuyla ilgili bilgileri, yerel bilgisayarınıza indirebilirsiniz bir CSV dosyasına dışarı aktarır. Dışarı aktarma raporu aşağıdaki bilgileri içerir:

  - Taslak koleksiyondaki arama sorgusuyla eşleşmeye sahip öğeleri içeren her içerik konumunun kimliği. Bu konumlar genellikle posta kutuları veya sitelerdir.
  
  - Her içerik konumunun toplam öğe sayısı.
  
  - Her içerik konumudaki öğelerin toplam boyutu (bayt cinsinden).

  - İçerik konumunun bulunduğu Exchange (Exchange veya SharePoint gibi) hizmet.

- **Koleksiyonu kopyalama**: Var olan koleksiyondan ayarları kopyalayıp yeni bir taslak koleksiyonu oluşturun. Yeni koleksiyon için farklı bir ad kullan gerekir. Ayrıca, yeni koleksiyonu göndermeden önce ayarları değiştirme seçeneğiniz de vardır. Sorguyu gönderdikten sonra, arama sorgusu çalıştırın; yeni tahminler ve istatistikler oluşturulur. Bu, hızla ek taslak koleksiyonu oluşturmanın ve özgün koleksiyonda bilgileri koruyarak gerekli olduğunda seçili ayarları değiştirmenin iyi bir yoludur. Böylece, benzer iki koleksiyonun sonuçlarını kolayca karşılaştırabilirsiniz.

> [!NOTE]
> Taslak koleksiyonu gözden geçirme kümesine kabul edildikten sonra, koleksiyonu yalnızca kopyalayıp bir raporu dışarı aktarabilirsiniz.
