---
title: Koleksiyon istatistikleri ve raporları
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
ms.reviewer: nickrob
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
description: Taslak koleksiyonları ve koleksiyonlar için, Advanced eDiscovery'de gözden geçirme kümesi için kaydedilmiş olan istatistiklere ve raporlara erişmeyi ve raporları kullanmayı Advanced eDiscovery.
ms.openlocfilehash: a520bd3f05e7729a1a36101d4be334d984b39739
ms.sourcegitcommit: bb493f12701f6d6ee7d5e64b541adb87470bc7bc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/18/2022
ms.locfileid: "63015506"
---
# <a name="collection-statistics-and-reports-in-advanced-ediscovery"></a>Koleksiyon istatistikleri ve rapor Advanced eDiscovery

Taslak koleksiyonu oluşturduklardan sonra, alınan öğelerle ilgili istatistikleri (arama ölçütleriyle ve arama sorgusu tarafından döndürülen öğe sayısıyla en çok eşleşmeyi içeren içerik konumları gibi) görüntüebilirsiniz. Sonuçların bir alt kümesini de öniz görebilirsiniz.

Daha fazla incelemek istediğiniz belge kümesi tanımlendiğinde, arama sonuçlarını toplamak ve işlemesi için bir gözden geçirme kümesine  eklersiniz.

## <a name="statistics-and-reports-for-draft-collections"></a>Taslak koleksiyonlar için istatistikler ve raporlar

Bu bölümde, taslak koleksiyonları için kullanılabilen istatistikler açık bulunmaktadır. Bu istatistikler, bir taslak **koleksiyonunun** açılır sayfasındaki Arama istatistikleri sekmesinde yer almaktadır.

### <a name="collection-estimates"></a>Koleksiyon tahminleri

Bu bölümde, koleksiyon tarafından döndürülen tahmini öğelerin grafik bir özeti görüntülenir. Bu, koleksiyonun arama ölçütlerine uyan öğelerin sayısını gösterir. Bu bilgiler, koleksiyon tarafından döndürülen tahmini öğe sayısı hakkında size bir fikir verir.

![Taslak koleksiyon için koleksiyon tahminleri.](../media/AeDCollectionEstimates.png)

- **Konumlara göre tahmini öğeler**: Koleksiyon tarafından döndürülen tahmini öğelerin toplam sayısı. Posta kutularında ve sitelerde bulunan belirli sayıda öğe de görüntülenir.

- **İsabet sayısı ile tahmini** konumlar: Koleksiyon tarafından döndürülen öğelerin bulunduğu içerik konumlarının toplam sayısı. Belirli sayıda posta kutusu ve site konumu da görüntülenir.

- **Konuma göre veri hacmi (MB)**: Koleksiyon tarafından döndürülen tahmini tüm öğelerin toplam boyutu. Ayrıca, posta kutusu öğelerinin ve site öğelerinin belirli boyutu da görüntülenir.

### <a name="condition-report"></a>Koşul raporu

Bu bölümde, koleksiyon arama sorgusuyla ilgili istatistikler ve arama sorgusunun farklı bölümleriyle eşan tahmini öğelerin sayısı görüntülenir. Arama sorgusunun her bileşenine uygun öğe sayısını çözümlemek için bu istatistikleri kullanabilirsiniz. Bu, koleksiyonun arama ölçütlerini daraltmanıza ve gerekirse koleksiyonun kapsamını daraltmanıza yardımcı olabilir.

- **Konum türü**: Sorgu istatistiklerinin uygulan bulunduğu içerik konumu türü. Posta kutusunun **Exchange** kutusu konumunu, posta kutusunun değeri ise **SharePoint** bir site konumunu gösterir.

- **Bölüm**: Arama sorgusunun istatistik bölümü uygulanabilir. **Birincil** , tüm arama sorgusunu gösterir. **Anahtar** sözcük, satırdaki istatistiklerin belirli bir anahtar sözcük için olduğunu gösterir. Koleksiyondaki arama sorgusu için anahtar sözcük listesi kullanırsanız, sorgunun her bileşeniyle ilgili istatistikler bu tabloya eklenir.

- **Koşul**: İlgili satırda görüntülenen istatistiklerin döndürülen taslak koleksiyonu için çalıştır gösterilen arama sorgusunun gerçek bileşeni (anahtar sözcük veya koşul).

- **Hits içeren konumlar**: Koşul sütununda listelenen birincil veya anahtar sözcük sorgusuyla eşananlı öğeler içeren içerik konumlarının (Konum türü sütunu tarafından belirtilen **)** sayısı.

- **Öğeler**: Koşul sütununda listelenen sorguyla aynı olan öğelerin sayısı (belirtilen içerik **konumdan)** Daha önce de belirtildiği gibi, bir öğede arama yapılan birden çok anahtar sözcük örneği varsa, bu sütunda yalnızca bir kez sayılır.

- **Boyut (MB)**: Bulunan (belirtilen içerik konumda) bulunan ve Koşul sütunundaki arama sorgusuyla eşanan tüm öğelerin **toplam** boyutu.

### <a name="top-locations"></a>En üst konumlar

Bu bölümde, koleksiyonun en çok döndürülen öğeleriyle birlikte belirli içerik konumlarının istatistikleri görüntülenir.

- Konum adının adı (posta kutularının e-posta adresi ve sitelerin URL'si).

- Konum türü (posta kutusu veya site).

- Koleksiyonun döndürülen içerik konumdaki tahmini öğe sayısı.

- Her içerik konumuyla ilgili tahmini öğelerin toplam boyutu.

## <a name="statistics-and-reports-for-committed-collections"></a>Kabul edilen koleksiyonlar için istatistikler ve raporlar

Bu bölümde, koleksiyonu gözden geçirme kümesine kaydettikten sonra kullanılabilir istatistikler (gözden geçirme kümesine eklenen gerçek öğe sayısı da içinde olmak üzere) açıklenmiştir. Bu istatistikler (yükleme kümesi bilgilerine ek olarak), vakaya eklenen içerikle ilgili geçmiş bilgileri sağlar.

Koleksiyonu bir gözden geçirme kümesine işlerken, kabul edilen bağlantının açılır sayfasında aşağıdaki sekmeler görüntülenir. Bu sekmelerin her biri, koleksiyon hakkında farklı türde bilgiler içerir.

![Kaydedilmiş koleksiyonun açılır sayfasındaki sekmeler.](../media/CommittedCollectionFlyoutPage.png)

### <a name="collection-contents"></a>Koleksiyon içeriği

Özet sekmesinin **bu** bölümü, koleksiyondaki veri kaynaklarından toplanan ve gözden geçirme kümesine eklenen öğelerle ilgili istatistikleri ve diğer bilgileri içerir.

- **Toplam ayıklanan öğeler**. Gözden geçirme kümesine eklenen toplam öğe sayısı. Bu sayı, gözden geçirme kümesine eklenen üst öğelerin ve alt öğelerin toplamını gösterir.

  > [!TIP]
  > İmleci, toplam üst veya alt öğe sayısını görüntülemek için üst veya alt öğe çubuklarının üzerine gelin.

- **Üst öğeler**. Gözden geçirme kümesine eklenen öğeleri toplamak için kullanılan koleksiyon tarafından döndürülen öğe sayısı. Bu sayı, Koleksiyon parametreleri bölümünde gösterilen tahmini öğe sayısına karşılık gelir (ve **buna eşittir** ). Gözden geçirme kümesine eklenen öğeleri toplamak için kullanılan koleksiyonu bilgilerini toplayan üst öğelerin sayısı.
 
   Bir üst öğe birden çok alt öğe içerebilir. Örneğin, e-posta iletisi ekli bir dosya içeriyorsa veya bulut eki varsa, üst öğedir. Bu durumda, bulut ekin ekli dosyası veya hedef dosyası alt öğe olarak kabul edilir. Koleksiyonu işlerken, üst öğeler ve buna karşılık gelen tüm alt öğeler (ekli dosyalar ve bulut ekleri gibi) gözden geçirmeye tek tek öğeler veya dosyalar olarak ayarlanır.

- **Alt öğeler.** Gözden geçirme kümesine eklenen alt öğe sayısı. Gözden geçirmeye yalnızca dosya ekleri ve bulut ekleri olan alt öğeler tek tek dosyalar olarak eklenir. E-posta imzaları ve resimler gibi diğer alt öğe türleri. üst öğeden ayıklanır ve alt öğeden herhangi bir metni ayıklamak için Optik Karakter Tanıma (OCR) tarafından işlenir. Bu tür alt öğelerden ayıklanan metin daha sonra, gözden geçirme kümesinde görüntüley eklensin ve üst öğeye eklenir. Alt öğeleri ayrı bir dosya olarak kümedeki gözden geçirme kümesine eklememenizi, Advanced eDiscovery gözden geçirme kümesinde yer alma olasılığı bulunan öğelerin sayısını sınır ekleyerek gözden geçirme işlemini kolaylaştırmanıza yardımcı olur.

- **Benzersiz öğeler**. Gözden geçirme kümesine eklenen benzersiz öğe sayısı. Benzersiz öğeler gözden geçirme kümesine benzersizdir. Gözden geçirme kümesinde daha önce hiç öğe yoktu, çünkü ilk koleksiyon yeni bir gözden geçirme kümesine ekli olduğunda tüm öğeler benzersizdir.

- **Tanımlanan yinelenen öğeler**. Aynı öğe gözden geçirme kümesinde zaten var olduğundan, koleksiyondaki gözden geçirme kümesine eklenmedi. Yinelenen öğelerle ilgili istatistikler, bir taslak koleksiyonundan gelen tahmini öğe sayısıyla gözden geçirme kümesine eklenen gerçek öğe sayısı arasındaki farkları açıklamaya yardımcı olabilir.

### <a name="indexing"></a>Dizin oluşturma

Kabul **edilen bir** gözden geçirme kümesi **özet** sekmesinde Dizin Oluşturma bölümü, gözden geçirme kümesine eklenen öğeler hakkında dizin oluşturma bilgilerini içerir.

**Yeni dizine alındı öğeleri**. Gözden geçirme kümesine eklenmeden önce yeni dizine alınan öğelerin sayısı. Yeni dizine alınan öğelere örnek olarak üst öğeden alınan ve gözden geçirme kümesine eklenmeden önce dizine alınan alt öğeler örnek olarak verilmiştir. Ayrıca, özel veri kaynaklarında yer olmayan öğeler ve durumdaki Veri kaynakları sekmesinde listelenen özel ve özel olmayan içerik konumları, gözden geçirme eklenmeden önce dizine eklenir. Örneğin, yeni dizine alınan öğeler ek konumlardan toplanan öğeleri içerebilir.

**Dizine alındı öğeleri güncelleştirildi**. Başarıyla dizine alınarak gözden geçirme kümesine eklenen kısmen dizine eklenen öğelerin sayısı. Bu istatistikler, koleksiyonu gözden geçirme kümesine kabul edilirken başarıyla dizine alınan özel ve özel olmayan içerik konumlarından kısmen dizine alınan öğeleri gösterir.

**Dizin oluşturma hataları**. Gözden geçirme kümesine eklenmeden önce dizine eklenemediklerine kısmen dizine eklenen öğelerin sayısı. Bu öğelerin hata düzeltmesi gerekli olabilir.

### <a name="collection-parameters"></a>Koleksiyon parametreleri

Bu bölümde, gözden geçirme kümesine eklenen öğeleri toplamak için kullanılan koleksiyon bilgileri görüntülenir. Bu sekmede, Arama istatistikleri sekmesindeki bilgilere **benzer bilgiler** görüntülenir. Bu bölümde, koleksiyon tarafından kullanılan arama sorgusunun hızlı bir tutturma vuruşu, arama yapılan içerik konumları ve tahmini koleksiyon sonuçları yer almaktadır. Daha önce de belirtildiği gibi, bu bölümdeki tahmini öğelerin sayısı Koleksiyon içeriği bölümünde gösterilen üst öğe **sayısına eşit** olabilir.

### <a name="search-statistics-tab"></a>Arama istatistikleri sekmesi

Arama istatistikleri sekmesinde **görüntülenen istatistikler** , bir taslak koleksiyonunun son çalıştırıı olan istatistiklerle aynıdır. Koleksiyon tahminleri, koşul raporu ve en üst konumlar buna dahildir. Bu bilgiler, geçmiş başvuru için taslak koleksiyonundan korunur ve gözden geçirme kümesi için kabul edilen gerçek koleksiyonla karşılaştırılamaz.

## <a name="differences-between-draft-collection-estimates-and-the-actual-committed-collection"></a>Taslak koleksiyon tahminleri ile gerçek kabul edilen koleksiyon arasındaki farklar

Bir taslak koleksiyonunu çalıştırarak, koleksiyon ölçütlerine uyan öğe sayısını (ve bunların toplam boyutunu) tahmin etmek, Özet sekmesinde ve Arama istatistikleri sekmesinin Koleksiyon  tahminleri **bölümünde** görüntülenir. Taslak koleksiyonunu gözden geçirme kümesine kaydettikten sonra, gözden geçirme kümesine eklenen gerçek öğe sayısı (ve bunların toplam boyutu) genellikle tahminlerden farklıdır. Çoğu durumda, gözden geçirme kümesine, taslak koleksiyonundan tahmin edilenden daha fazla öğe eklenir. Aşağıdaki listede, bu farkların en yaygın nedenleri ve bunları tanımlama ipuçları açık almaktadır:

- **Alt öğeler.** Üst öğelerinden ayıklanan ve tek tek dosyalar olarak eklenen alt öğeler (dosya ekleri ve bulut ekleri gibi). Alt öğe sayısı, gözden geçirme kümesine gerçekten eklenen öğe sayısını artırabilir. Genel olarak, kabul edilen koleksiyonun Özet sekmesindeki Koleksiyon  içeriği bölümünde tanımlanan üst öğe  sayısı, taslak koleksiyonundan gelen tahmini öğelerin sayısına eşit olması gerekir.

- **Yinelenen öğeler**. Taslak koleksiyonundan, önceki bir koleksiyonda yer alan ve gözden geçirme kümesine önceden eklenmiş olan öğeler eklenmez. Daha önce de belirtildiği gibi, koleksiyondaki yinelenen öğelerin sayısı Özet **sekmesinin Koleksiyon** içeriği **bölümünde** görüntülenir.

- **Koleksiyon yapılandırma seçenekleri**. Taslak koleksiyonunu gözden geçirme kümesine işlerken, konuşma dizilerini, bulut eklerini ve belge sürümlerini dahil etme seçeneğiniz vardır. Gözden geçirme kümesine eklenen bu öğelerden herhangi biri taslak koleksiyonunun tahminlerine dahil değildir. Bunlar yalnızca koleksiyonu işlerken tanımlanır ve toplanır. Bu seçeneklerin seçimi büyük olasılıkla gözden geçirme kümesine eklenen öğe sayısını artıracaktır. 

    Örneğin, belge sürümlerinin SharePoint sürümleri taslak koleksiyonunun tahminlerine dahil değildir. Ancak bir taslak koleksiyonu işlerken tüm belge sürümlerini ekleme seçeneğini eklerseniz, gözden geçirme kümesine eklenen öğelerin gerçek sayısı (ve toplam boyutu) artar.

    Bu seçenekler hakkında daha fazla bilgi için bkz [. Taslak koleksiyonunu gözden geçirme kümesine kaydetme](commit-draft-collection.md#commit-a-draft-collection-to-a-review-set-in-advanced-ediscovery). 

Burada, bir taslak koleksiyonundan elde edilen tahmini sonuçların, gerçek kabul edilen sonuçlardan farklı olması için de başka nedenler ve açık bir şekilde açık bir şekilde açıklandı.

- **Taslak koleksiyonlarda sonuçların tahmin edilen yolu**. Taslak koleksiyon tarafından döndürülen arama sonuçlarının tahmini, koleksiyon sorgu ölçütlerine uyan öğelerin tahminini (ve gerçek sayısını değil) ifade etmektir. E-posta öğelerinin tahminini derlemek için, bu veritabanından arama ölçütlerine uyan ileti kimliklerinin Exchange istenmektedir. Ancak koleksiyonu bir gözden geçirme kümesine işlerken, koleksiyon yeniden çalıştırılamaz ve gerçek iletiler Exchange alınır. Dolayısıyla, bu farklar, tahmini öğe sayısının ve gerçek öğe sayısının nasıl belirleneceği nedeniyle ortaya çıkan sonuçlar olabilir.

- **Taslak koleksiyonları tahmin ve yürütme zamanı arasında gerçekleşecek değişiklikler**. Taslak koleksiyonunu bir gözden geçirme kümesine işlerken, arama yeniden çalıştırarak arama dizininde arama ölçütlerine uyan en son öğeleri toplar. Taslak koleksiyonunun en son çalıştırılan zaman ile taslak koleksiyonunun gözden geçirme kümesi için kabul edilen zaman arasında arama ölçütlerine uyan başka öğeler de oluşturulmuş, gönderilmiş veya silinmiş olabilir. Taslak koleksiyon sonuçları onaylandıklarında arama dizininde yer alan öğelerin koleksiyonları işlemeden önce bir veri kaynağından temizn dolayı artık orada olmadığı tahmin ediliyor olabilir. Bu sorunu azaltmak için bir yol, koleksiyon için bir tarih aralığı belirtmektir. Bir diğer yol da, içerik konumlarını yerinde tutmak ve bu şekilde öğelerin korunmasını ve temiz olamamaktır.

- **Bağımsız olmayan öğeler**. Taslak koleksiyon tüm Exchange posta kutularında veya tüm SharePoint sitelerinde arama içeriyorsa, gözden geçirme kümesine yalnızca içerik konumlarından gelen ve koleksiyon ölçütlerine uyan öğeler içeren ya da eklenmemiş öğeler eklenir. Başka bir deyişle, bir posta kutusunda veya sitede hiç sonuç bulunamazsa, bu posta kutusu veya sitedeki ya da sitedeki tekinde eklenmemiş öğeler gözden geçirme kümesine eklenmez. Bununla birlikte, tüm içerik konumlarından (koleksiyon sorgusuyla eşleşmeen öğeler içermeseler bile) içeremeyen öğeler, tahmini koleksiyon sonuçlarına dahil edilir.

    Alternatif olarak, taslak koleksiyonunda belirli içerik konumları (bu, taslak koleksiyonu sihirbazının Ek konumlar sayfasında belirtilen belirli posta kutuları veya  siteler) varsa, aramada belirtilen içerik konumlarından tekinde alınmamış öğeler (koleksiyon ölçütleri tarafından dışlanmamış) dışarı aktarılacaktır. Bu durumda, tahmini olarak, dizili olmayan öğelerin sayısı ve gözden geçirme kümesine eklenen ya da eklenmemiş öğelerin sayısı aynı olur.
