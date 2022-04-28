---
title: Taslak koleksiyon oluşturma
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
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
description: Taslak koleksiyon, eBulma (Premium) durumunda, koleksiyonun arama sorgusuyla eşleşen bir arama tahmini döndüren bir eBulma (Premium) durumundaki gözaltı ve gözetim dışı veri kaynaklarının eBulma aramasıdır. Sonuçları gözden geçirme kümesine işlemeden önce arama istatistiklerini gözden geçirebilir, öğelerin örneklemesini önizleyebilir ve koleksiyonu düzeltip yeniden çalıştırabilirsiniz.
ms.openlocfilehash: 50fb63658541c07a312a502dbbe7d68a26467d14
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65096104"
---
# <a name="create-a-draft-collection-in-ediscovery-premium"></a>eBulma'da taslak koleksiyon oluşturma (Premium)

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Olay için koruyucuları ve koruyucu olmayan veri kaynaklarını belirledikten sonra, ilgili bir belge kümesini belirlemeye ve bulmaya hazır olursunuz. Bunu, veri kaynaklarında ilgili içerik aramak için Koleksiyonlar aracını kullanarak yaparsınız. Bunu, belirtilen veri kaynaklarında arama ölçütlerinizle eşleşen içerik arayan bir koleksiyon oluşturarak yaparsınız. Öğelerin bulunduğuna ilişkin bir tahmin olan *bir taslak koleksiyon* oluşturma seçeneğiniz vardır veya öğeleri otomatik olarak bir gözden geçirme kümesine ekleyen bir koleksiyon oluşturabilirsiniz. Taslak koleksiyon oluşturduğunuzda, bulunan öğelerin toplam sayısı ve boyutu, bulundukları farklı veri kaynakları ve arama sorgusuyla ilgili istatistikler gibi arama sorgusuyla eşleşen tahmini sonuçlar hakkındaki bilgileri görüntüleyebilirsiniz. Koleksiyon tarafından döndürülen öğelerin bir örneğini de önizleyebilirsiniz. Bu istatistikleri kullanarak arama sorgusunu değiştirebilir ve sonuçlarınızı daraltmak için taslak koleksiyonu yeniden çalıştırabilirsiniz. Koleksiyon sonuçlarından memnun olduğunuzda, koleksiyonu bir gözden geçirme kümesine işleyebilirsiniz. Bir taslak koleksiyonu işlediğiniz zaman, koleksiyon tarafından döndürülen öğeler gözden geçirme, analiz ve dışarı aktarma için bir gözden geçirme kümesine eklenir.

## <a name="before-you-create-a-draft-collection"></a>Taslak koleksiyon oluşturmadan önce

- Taslak koleksiyon oluşturmadan önce servis talebine koruyucular ve gözetimsiz veri kaynakları ekleyin. Taslak koleksiyon oluştururken veri kaynaklarını seçebilmeniz için bu gereklidir. Daha fazla bilgi için bkz.:

  - [Bir vakaya yediemin ekleme](add-custodians-to-case.md)

  - [Bir vakaya yediemin olmayan veri kaynakları ekleme](non-custodial-data-sources.md)

- Bir taslak koleksiyonda servis talebiyle ilgili olabilecek içerik için ek veri kaynaklarını (servis talebine koruyucu veya gözetimsiz konum olarak eklenmemiş olanlar) arayabilirsiniz. Bu veri kaynakları posta kutularını, SharePoint siteleri ve Teams içerebilir. Bu durum sizin durumunuz için geçerliyse, bunları koleksiyona ekleyebilmek için bu veri kaynaklarının listesini derleyin.

## <a name="create-a-draft-collection"></a>Taslak koleksiyon oluşturma

1. Microsoft Purview uyumluluk portalında eBulma (Premium) servis talebini açın ve **koleksiyonlar** sekmesini seçin.

2. **Koleksiyonlar** sayfasında Yeni **koleksiyonStandard koleksiyonu'nu** >  seçin.

3. Koleksiyon için bir ad (gerekli) ve açıklama (isteğe bağlı) yazın. Koleksiyon oluşturulduktan sonra adı değiştiremezsiniz, ancak açıklamayı değiştirebilirsiniz.

4. **Koruyucu veri kaynakları** sayfasında, içerik toplamak üzere koruyucu veri kaynaklarını tanımlamak için aşağıdakilerden birini yapın:

   - Servis talebine eklenen belirli **koruyucuları** aramak için Koruyucuları seç'e tıklayın. Bu seçeneği kullanırsanız, servis talebi koruyucularının listesi görüntülenir. Bir veya daha fazla koruyucu seçin. Koruyucuları seçip ekledikten sonra, her koruyucuyu aramak için belirli veri kaynaklarını da seçebilirsiniz. Görüntülenen bu veri kaynakları, koruyucu olaya eklendiğinde belirtildi.

   - Servis talebine eklenen tüm koruyucuları aramak için **Tümünü seç** iki durumlu düğmesine tıklayın. Bu seçeneği belirlediğinizde, tüm koruyucular için tüm veri kaynakları aranıyor.

5. **Gözetimsiz veri kaynakları** sayfasında, içerik toplamak üzere gözetimsiz veri kaynaklarını belirlemek için aşağıdakilerden birini yapın:

   - Olaya eklenen belirli **gözetim dışı veri kaynaklarını** seçmek için Gözetim dışı veri kaynaklarını seç'e tıklayın. Bu seçeneği kullanırsanız, veri kaynaklarının listesi görüntülenir. Bu veri kaynaklarından birini veya daha fazlasını seçin.

   - Olaya eklenen gözetimsiz tüm veri kaynaklarını seçmek için **Tümünü seç** iki durumlu düğmesine tıklayın.

6. **Ek veri kaynakları** sayfasında, koleksiyonun bir parçası olarak aranacak diğer posta kutularını ve siteleri seçebilirsiniz. Bu tür veri kaynakları, olayda koruyucu veya gözetimsiz veri konumu olarak eklenmemiştir. Ek veri kaynaklarında arama yaparken iki seçeneğiniz de vardır:

   - Belirli bir hizmetin tüm içerik konumlarında arama yapmak için (posta kutuları, Exchange SharePoint ve OneDrive siteleri veya ortak klasörler Exchange) **Durum** sütununda karşılık gelen **Tümünü seç** iki durumlu düğmesini tıklatın. Bu seçenek, seçili hizmetteki tüm içerik konumlarında arama yapacaktır.

   - Bir hizmetin belirli içerik konumunu aramak için **, Durum** sütununda karşılık gelen **Tümünü seç** iki durumlu düğmesine tıklayın ve ardından Belirli içerik konumlarında arama yapmak için **Kullanıcılar, gruplar veya ekipler** (Exchange posta kutuları için) veya Siteleri **seçin** (SharePoint ve OneDrive siteleri) seçeneğine tıklayın.

7. **Koşullar** sayfasında, önceki sihirbaz sayfalarında tanımladığınız veri kaynaklarından öğeleri toplamak için kullanılan arama sorgusunu oluşturabilirsiniz. Anahtar sözcükleri, property:value çiftlerini arayabilir veya anahtar sözcük listesi kullanabilirsiniz. Koleksiyonun kapsamını daraltmak için çeşitli arama koşulları da ekleyebilirsiniz. Daha fazla bilgi için bkz. [Koleksiyonlar için arama sorguları oluşturma](building-search-queries.md).

8. **Taslak olarak kaydet veya gözden geçirme kümesine ekle** sayfasında **Koleksiyonu taslak olarak kaydet'i** seçin.

   > [!NOTE]
   > Bu sayfadaki diğer seçenek öğeleri toplamanıza ve doğrudan bir gözden geçirme kümesine eklemenize olanak tanır. Koleksiyon sonuçlarının istatistiklerini gözden geçirebileceğiniz ve bir örneğin önizlemesini görüntüleyebileceğiniz bir taslak koleksiyon oluşturmak yerine, bu seçenek bu işlemi atlar ve koleksiyonu otomatik olarak bir gözden geçirme kümesine ekler. Koleksiyonu bir gözden geçirme kümesine eklemek için ikinci seçeneği belirlerseniz, Microsoft Teams ve Yammer sohbet konuşma yazışmalarının tamamını toplama ve bulut eklerini (modern ekler olarak da adlandırılır) toplama gibi yapılandırabileceğiniz ek *ayarlara* sahip olursunuz. Bu ayarlar hakkında daha fazla bilgi için bkz [. Taslak koleksiyonu gözden geçirme kümesine işleme](commit-draft-collection.md).

9. **Koleksiyonunuzu gözden geçirin** sayfasında, önceki sayfalarda yapılandırdığınız koleksiyon ayarlarını gözden geçirebilir ve güncelleştirebilirsiniz.

   - **Özet** sekmesi: Koleksiyonun adını ve açıklamasını, koleksiyon arama ölçütlerini, ek veri konumlarını ve koleksiyon türünü gözden geçirin ve değiştirin.

   - **Kaynaklar** sekmesi: Koleksiyonun koruyucu ve gözetimsiz veri kaynaklarını gözden geçirin ve değiştirin.

10. Taslak koleksiyonu oluşturmak için **Gönder'e** tıklayın. Koleksiyonun oluşturulduğunu onaylayan bir sayfa görüntülenir.

## <a name="what-happens-after-you-create-a-draft-collection"></a>Taslak koleksiyon oluşturduktan sonra ne olur?

Bir taslak koleksiyon oluşturduktan sonra, bu koleksiyon örnekte **Koleksiyonlar** sayfasında listelenir ve durum, devam ettiğini gösterir. **Arama önizlemesi ve tahminleri hazırlama** adlı bir iş de oluşturulur ve servis talebindeki **İşler** sayfasında görüntülenir.

Taslak toplama işlemi sırasında eBulma (Premium), koleksiyonda belirttiğiniz arama ölçütlerini ve veri kaynaklarını kullanarak bir arama tahmini gerçekleştirir. eBulma (Premium) ayrıca önizlemede görüntüleyebileceğiniz öğelerin örneklemesini de hazırlar. Koleksiyon tamamlandığında, **Koleksiyon** sayfasındaki aşağıdaki sütunlar ve karşılık gelen değerler güncelleştirilir:

![Taslak koleksiyonun durum durumları.](../media/DraftCollectionStatus.png)

- **Durum**: Koleksiyonun durumunu ve türünü gösterir. **Tahmini** değeri, taslak koleksiyonun tamamlandığını gösterir. Aynı değer, koleksiyonun bir taslak koleksiyon olduğunu ve bir gözden geçirme kümesine eklenmediğini de gösterir. **Durum** **sütunundaki Committed** değeri, koleksiyonun bir gözden geçirme kümesine eklendiğini gösterir.

- **Tahmin durumu**: Tahmini arama sonuçlarının durumunu ve arama tahminlerinin ve istatistiklerinin gözden geçirilme için hazır olup olmadığını gösterir. **Başarılı** değeri, taslak koleksiyonun sonuçlarının gözden geçirmeye hazır olduğunu gösterir. Bir taslak koleksiyonu ilk kez gönderdikten sonra, koleksiyonun hala çalıştığını belirtmek için **Devam Ediyor** değeri görüntülenir

- **Önizleme durumu**: Önizlemesini görüntüleyebileceğiniz örnek öğelerin durumunu gösterir. **Başarılı** değeri, öğelerin önizleme için hazır olduğunu gösterir. Bir taslak koleksiyonu ilk kez gönderdikten sonra, koleksiyonun çalışmaya devam ettiğini göstermek için **Devam Ediyor** değeri görüntülenir.

## <a name="next-steps-after-a-draft-collection-is-complete"></a>Taslak koleksiyon tamamlandıktan sonraki adımlar

Taslak koleksiyonu başarıyla tamamlandıktan sonra çeşitli görevleri gerçekleştirebilirsiniz. Bu görevlerin çoğunu gerçekleştirmek için **Koleksiyonlar** sekmesine gidip taslak koleksiyonun adına tıklayarak açılır sayfayı görüntülemeniz gerekir.

![Taslak koleksiyon için açılır sayfa.](../media/DraftCollectionFlyoutPage.png)

Koleksiyon açılır sayfasından yapabileceklerinin listesi aşağıdadır:

- Koleksiyon hakkındaki özet bilgileri ve koleksiyon tarafından döndürülen tahmini arama sonuçlarını görüntülemek için **Özet** sekmesini seçin. Bu toplam öğe sayısını ve tahmini arama sonuçlarının boyutunu, arama sonuçlarını içeren posta kutularının ve sitelerin sayısını ve koleksiyonun kapsamını bulmak için kullanılan arama koşullarını (kullanılıyorsa) içerir.

- **Koleksiyonda arama yapılan koruyucuların** ve gözetim dışı veri kaynaklarının) listesini görüntülemek için Veri kaynakları sekmesini seçin. Arama yapılan ek içerik konumları **Özet** sekmesindeki **Konumlar** altında listelenir.

- Koleksiyonla ilgili istatistikleri görüntülemek için **İstatistikleri ara** sekmesini seçin. Bu, her hizmette bulunan öğelerin toplam sayısını ve boyutunu (örneğin, posta kutuları veya SharePoint siteleri Exchange) ve koleksiyon tarafından kullanılan arama sorgusunun farklı bileşenleri tarafından döndürülen öğe sayısıyla ilgili istatistikleri görüntüleyen bir koşul raporu içerir. Daha fazla bilgi için bkz [. Koleksiyon istatistikleri ve raporları](collection-statistics-reports.md).

- Koleksiyon tarafından döndürülen öğelerin bir örneğini önizlemek için **Örneği gözden geçir** 'e (açılır sayfanın en altında yer alır) tıklayın.

- Taslak koleksiyonu bir gözden geçirme kümesine işleyin (**ActionsEdit** >  **koleksiyonu'na** tıklayarak). Bu, koleksiyonu yeniden çalıştırdığınız (geçerli ayarları kullanarak) ve koleksiyon tarafından döndürülen öğeleri bir gözden geçirme kümesine eklediğiniz anlamına gelir. Daha önce açıklandığı gibi, koleksiyonu bir gözden geçirme kümesine eklediğinizde ek ayarları da yapılandırabilirsiniz (konuşma yazışması ve bulut tabanlı ekler gibi). Daha fazla bilgi ve adım adım yönergeler için bkz. [Taslak koleksiyonu gözden geçirme kümesine işleme](commit-draft-collection.md).

## <a name="manage-a-draft-collection"></a>Taslak koleksiyonu yönetme

Çeşitli yönetim görevlerini gerçekleştirmek için taslak koleksiyonun açılır sayfasındaki **Eylemler** menüsündeki seçenekleri kullanabilirsiniz.

![Taslak koleksiyonu için Eylemler menüsündeki seçenekler.](../media/DraftCollectionActionsMenu.png)

Yönetim seçeneklerinin açıklamaları aşağıdadır.

- **Koleksiyonu düzenle**: Taslak koleksiyonun ayarlarını değiştirin. Değişiklik yaptıktan sonra koleksiyonu yeniden çalıştırabilir, arama tahminlerini ve istatistiklerini güncelleştirebilirsiniz. Daha önce açıklandığı gibi, bu seçeneği bir taslak koleksiyonu gözden geçirme kümesine işlemek için kullanırsınız.  

- **Koleksiyonu silme**: Taslak koleksiyonu silme. Taslak koleksiyon bir gözden geçirme kümesine işlendikten sonra silinemez.

- **Tahminleri yenileme: Arama tahminlerini** ve istatistikleri güncelleştirmek için taslak koleksiyonda belirtilen sorguyu (veri kaynaklarına karşı) yeniden çalıştırın.

- **Rapor olarak dışarı aktar**: Taslak koleksiyon hakkındaki bilgileri yerel bilgisayarınıza indirebileceğiniz bir CSV dosyasına aktarır. Dışarı aktarma raporu aşağıdaki bilgileri içerir:

  - Taslak koleksiyondaki arama sorgusuyla eşleşen öğeleri içeren her içerik konumunun kimliği. Bu konumlar genellikle posta kutuları veya sitelerdir.
  
  - Her içerik konumundaki toplam öğe sayısı.
  
  - Her içerik konumundaki öğelerin toplam boyutu (bayt cinsinden).

  - İçerik konumunun bulunduğu hizmet (Exchange veya SharePoint gibi).

- **Koleksiyonu kopyalama**: Mevcut bir koleksiyondaki ayarları kopyalayarak yeni bir taslak koleksiyon oluşturun. Yeni koleksiyon için farklı bir ad kullanmanız gerekir. Yeni koleksiyonu göndermeden önce ayarları değiştirme seçeneğiniz de vardır. Siz gönderdikten sonra arama sorgusu çalıştırılır ve yeni tahminler ve istatistikler oluşturulur. hızlı bir şekilde ek taslak koleksiyon oluşturmak ve ardından özgün koleksiyondaki bilgileri korurken seçili ayarları gerektiği gibi değiştirmek için iyi bir yoldur. Bu, benzer iki koleksiyonun sonuçlarını kolayca karşılaştırmanıza da olanak tanır.

> [!NOTE]
> Taslak koleksiyon bir gözden geçirme kümesine işlendikten sonra, yalnızca koleksiyonu kopyalayıp raporu dışarı aktarabilirsiniz.
