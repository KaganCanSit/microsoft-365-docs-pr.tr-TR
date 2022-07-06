---
title: Koleksiyon istatistikleri ve raporları
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
ms.reviewer: nickrob
manager: laurawi
ms.date: 04/08/2022
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Microsoft Purview eKeşif (Premium) içinde bir gözden geçirme kümesine kaydedilmiş taslak koleksiyonlar ve koleksiyonlar için istatistiklere ve raporlara erişmeyi ve bunları kullanmayı öğrenin.
ms.openlocfilehash: 1f9047a047e5c2c4abd01f0cac39ab6cb97e27da
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66626853"
---
# <a name="collection-statistics-and-reports-in-microsoft-purview-ediscovery-premium"></a>Microsoft Purview eKeşif'de toplama istatistikleri ve raporları (Premium)

Taslak koleksiyonu oluşturduktan sonra, arama ölçütleriyle eşleşen en çok öğeyi içeren içerik konumları ve arama sorgusu tarafından döndürülen öğe sayısı gibi alınan öğelerle ilgili istatistikleri görüntüleyebilirsiniz. Sonuçların bir alt kümesini de önizleyebilirsiniz.

Daha fazla incelemek istediğiniz belge kümesini tanımladığınızda, arama sonuçlarını toplamak ve işlemek üzere bir gözden geçirme kümesine ekleyebilirsiniz.

## <a name="statistics-and-reports-for-draft-collections"></a>Taslak koleksiyonlar için istatistikler ve raporlar

Bu bölümde taslak koleksiyonlar için kullanılabilen istatistikler açıklanmaktadır. Bu istatistikler, taslak koleksiyonun açılır sayfasındaki **Arama istatistikleri** sekmesinde bulunur.

### <a name="collection-estimates"></a>Toplama tahminleri

Bu bölümde, koleksiyon tarafından döndürülen tahmini öğelerin grafik özeti görüntülenir. Bu, koleksiyonun arama ölçütlerine uyan öğe sayısını gösterir. Bu bilgiler, koleksiyon tarafından döndürülen tahmini öğe sayısı hakkında size bir fikir verir.

![Taslak koleksiyon için koleksiyon tahminleri.](../media/AeDCollectionEstimates.png)

- **Konumlara göre tahmini öğeler**: Koleksiyon tarafından döndürülen tahmini öğelerin toplam sayısı. Posta kutularında bulunan ve sitelerde bulunan belirli öğe sayısı da görüntülenir.

- **İsabetli tahmini konumlar**: Koleksiyon tarafından döndürülen öğeleri içeren içerik konumlarının toplam sayısı. Belirli sayıda posta kutusu ve site konumu da görüntülenir.

- **Konuma göre veri hacmi (MB cinsinden):** Koleksiyon tarafından döndürülen tüm tahmini öğelerin toplam boyutu. Posta kutusu öğelerinin ve site öğelerinin belirli boyutu da görüntülenir.

### <a name="condition-report"></a>Koşul raporu

Bu bölümde, koleksiyon arama sorgusu ve arama sorgusunun farklı bölümleriyle eşleşen tahmini öğe sayısıyla ilgili istatistikler görüntülenir. Arama sorgusunun her bileşeniyle eşleşen öğe sayısını analiz etmek için bu istatistikleri kullanabilirsiniz. Bu, koleksiyonun arama ölçütlerini iyileştirmenize ve gerekirse koleksiyonun kapsamını daraltmanıza yardımcı olabilir.

- **Konum türü**: Sorgu istatistiklerinin uygulanabilecek içerik konumu türü. **Exchange** değeri bir posta kutusu konumunu gösterir; **SharePoint** değeri site konumunu gösterir.

- **Bölüm**: arama sorgusunun istatistikler için geçerli olan bölümü. **Birincil** , arama sorgusunun tamamını gösterir. **Anahtar sözcük** , satırdaki istatistiklerin belirli bir anahtar sözcük için olduğunu gösterir. Koleksiyondaki arama sorgusu için bir anahtar sözcük listesi kullanırsanız, sorgunun her bileşenine ilişkin istatistikler bu tabloya eklenir.

- **Koşul**: Karşılık gelen satırda görüntülenen istatistikleri döndüren taslak koleksiyon için çalıştırılan arama sorgusunun gerçek bileşeni (anahtar sözcük veya koşul).

- **İsabetli konumlar**: **Koşul** sütununda listelenen birincil veya anahtar sözcük sorgusuyla eşleşen öğeleri içeren içerik konumlarının sayısı (**Konum türü** sütunu tarafından belirtilir).

- **Öğeler**: **Koşul** sütununda listelenen sorguyla eşleşen öğe sayısı (belirtilen içerik konumundan). Daha önce açıklandığı gibi, bir öğe aranmakta olan bir anahtar sözcüğün birden çok örneğini içeriyorsa, bu sütunda yalnızca bir kez sayılır.

- **Boyut (MB)**: **Koşul** sütunundaki arama sorgusuyla eşleşen bulunan tüm öğelerin (belirtilen içerik konumunda) toplam boyutu.

### <a name="top-locations"></a>En iyi konumlar

Bu bölümde, koleksiyon tarafından döndürülen en çok öğeye sahip belirli içerik konumlarıyla ilgili istatistikler görüntülenir.

- Konum adının adı (posta kutularının e-posta adresi ve sitelerin URL'si).

- Konum türü (posta kutusu veya site).

- Koleksiyon tarafından döndürülen içerik konumundaki tahmini öğe sayısı.

- Her içerik konumundaki tahmini öğelerin toplam boyutu.

## <a name="statistics-and-reports-for-committed-collections"></a>Taahhüt edilen koleksiyonlar için istatistikler ve raporlar

Bu bölümde, gözden geçirme kümesine eklenen öğelerin gerçek sayısı da dahil olmak üzere bir koleksiyonu bir gözden geçirme kümesine işledikten sonra kullanılabilen istatistikler açıklanmaktadır. Bu istatistikler (yük kümesi bilgilerine ek olarak), servis talebine eklenen içerikle ilgili geçmiş bilgileri sağlar.

Bir koleksiyonu bir gözden geçirme kümesine işledikten sonra, kaydedilen bağlantının açılır sayfasında aşağıdaki sekmeler görüntülenir. Bu sekmelerin her biri koleksiyon hakkında farklı türde bilgiler içerir.

![Kaydedilmiş koleksiyonun açılır sayfasındaki sekmeler.](../media/CommittedCollectionFlyoutPage.png)

### <a name="collection-contents"></a>Koleksiyon içeriği

**Özet** sekmesinin bu bölümü, koleksiyondaki veri kaynaklarından toplanan ve gözden geçirme kümesine eklenen öğelerle ilgili istatistikleri ve diğer bilgileri içerir.

- **Ayıklanan öğelerin toplamı**. Gözden geçirme kümesine eklenen toplam öğe sayısı. Bu sayı, gözden geçirme kümesine eklenen üst öğelerin ve alt öğelerin toplamını gösterir.

  > [!TIP]
  > Toplam üst veya alt öğe sayısını görüntülemek için imleci üst veya alt öğe çubuklarının üzerine getirin.

- **Üst öğeler**. Gözden geçirme kümesine eklenen öğeleri toplamak için kullanılan koleksiyon tarafından döndürülen öğe sayısı. Bu sayı **, Koleksiyon parametreleri** bölümünde görüntülenen tahmini öğe sayısına karşılık gelir (ve eşittir). Gözden geçirme kümesine eklenen öğeleri toplamak için kullanılan bilgileri topladığı üst öğe sayısı.
 
   Üst öğe birden çok alt öğe içerebilir. Örneğin, e-posta iletisi ekli bir dosya içeriyorsa veya bir bulut eki varsa üst öğedir. Bu durumda, ekli dosya veya bulut ekinin hedef dosyası bir alt öğe olarak kabul edilir. Bir koleksiyonu işlediğiniz zaman, üst öğeler ve buna karşılık gelen tüm alt öğeler (ekli dosyalar ve bulut ekleri gibi) gözden geçirme kümesine tek tek öğeler veya dosyalar olarak eklenir.

- **Alt öğeler**. Gözden geçirme kümesine eklenen alt öğe sayısı. Gözden geçirme kümesine yalnızca dosya ekleri ve bulut ekleri olan alt öğeler tek tek dosyalar olarak eklenir. E-posta imzaları ve resimler gibi diğer alt öğe türleri bir üst öğeden ayıklanır ve ardından Optik Karakter Tanıma (OCR) tarafından alt öğeden herhangi bir metni ayıklamak için işlenir. Bu tür alt öğelerden ayıklanan metin, gözden geçirme kümesinde görüntüleyebilmeniz için üst öğeye eklenir. eKeşif (Premium), gözden geçirme kümesine alt öğeleri ayrı bir dosya olarak eklemeyerek, gözden geçirme kümesindeki potansiyel olarak önemsiz öğe sayısını sınırlayarak gözden geçirme sürecini kolaylaştırmaya yardımcı olur.

- **Benzersiz öğeler**. Gözden geçirme kümesine eklenen benzersiz öğelerin sayısı. Benzersiz öğeler gözden geçirme kümesine özeldir. İlk koleksiyon yeni bir gözden geçirme kümesine eklendiğinde tüm öğeler benzersizdir çünkü gözden geçirme kümesinde önceki öğeler yoktu.

- **Yinelenen öğeler belirlendi**. Aynı öğe gözden geçirme kümesinde zaten var olduğundan, koleksiyondaki gözden geçirme kümesine eklenmemiş öğe sayısı. Yinelenen öğelerle ilgili istatistikler, taslak koleksiyondaki tahmini öğe sayısı ile gözden geçirme kümesine eklenen öğelerin gerçek sayısı arasındaki farkları açıklamaya yardımcı olabilir.

### <a name="indexing"></a>Dizin

Kaydedilmiş bir gözden geçirme kümesinin **Özet** sekmesindeki **Dizin oluşturma** bölümü, gözden geçirme kümesine eklenen öğeler hakkında dizin bilgileri içerir.

**Yeni dizine alınan öğeler**. Gözden geçirme kümesine eklenmeden önce yeni dizine alınan öğelerin sayısı. Yeni dizine alınan öğeye örnek olarak üst öğeden ayıklanan ve gözden geçirme kümesine eklenmeden önce dizine alınan alt öğeler verilebilir. Ayrıca, olaydaki **Veri kaynakları** sekmesinde listelenen gözaltı veri kaynaklarında ve gözetimsiz içerik konumlarında yer almayan öğeler, gözden geçirme sürecine eklenmeden önce dizine eklenir. Örneğin, yeni dizine alınan öğeler ek konumlardan toplanan öğeleri içerebilir.

**Dizine alınan öğeler güncelleştirildi**. Başarıyla dizine alınan ve gözden geçirme kümesine eklenen kısmen dizinlenmiş öğelerin sayısı. Bu istatistik, koleksiyon gözden geçirme kümesine işlendiğinde başarıyla dizine alınan, koruyucu ve gözetimsiz içerik **konumlarından** kısmen dizine alınan öğeleri gösterir.

**Dizin oluşturma hataları**. Kısmen dizine alınan ve gözden geçirme kümesine eklenmeden önce dizine alınamayan öğelerin sayısı. Bu öğeler hata düzeltmesi gerektirebilir.

### <a name="collection-parameters"></a>Koleksiyon parametreleri

Bu bölümde, gözden geçirme kümesine eklenen öğeleri toplamak için kullanılan koleksiyon bilgileri görüntülenir. Bu sekme, **Arama istatistikleri** sekmesindeki bilgilere benzer bilgiler görüntüler. Bu bölüm, koleksiyon tarafından kullanılan arama sorgusunun, aranan içerik konumlarının ve tahmini koleksiyon sonuçlarının hızlı bir anlık görüntüsünü sağlar. Daha önce açıklandığı gibi, bu bölümdeki tahmini öğe sayısı **Koleksiyon içeriği** bölümünde gösterilen üst öğe sayısına eşit olacaktır.

### <a name="search-statistics-tab"></a>Arama istatistikleri sekmesi

**Arama istatistikleri** sekmesinde görüntülenen istatistikler, taslak koleksiyonun son çalıştırıldığı zamana ait istatistiklerle aynıdır. Buna koleksiyon tahminleri, koşul raporu ve en üst konumlar dahildir. Bu bilgiler, geçmiş başvurusu için taslak koleksiyondan korunur ve gözden geçirme kümesine kaydedilmiş olan gerçek koleksiyonla karşılaştırılabilir.

## <a name="differences-between-draft-collection-estimates-and-the-actual-committed-collection"></a>Taslak koleksiyon tahminleri ile gerçek taahhüt edilen koleksiyon arasındaki farklar

Bir taslak koleksiyonu çalıştırdığınızda, koleksiyon ölçütlerini karşılayan öğe sayısı (ve toplam boyutu) tahmini **Özet** sekmesinde ve **Arama istatistikleri** sekmesinin **Koleksiyon tahminleri** bölümünde görüntülenir. Taslak koleksiyonu bir gözden geçirme kümesine işledikten sonra, gözden geçirme kümesinin eklediği gerçek öğe sayısı (ve toplam boyutları) genellikle tahminlerden farklıdır. Çoğu durumda, gözden geçirme kümesine taslak koleksiyondan tahmin edilenden daha fazla öğe eklenir. Aşağıdaki listede, bu farklılıkların en yaygın nedenleri ve bunları tanımlama ipuçları açıklanmaktadır:

- **Alt öğeler**. Üst öğelerinden ayıklanan ve tek tek dosyalar olarak eklenen alt öğeler (dosya ekleri ve bulut ekleri gibi). Alt öğe sayısı, gerçekten gözden geçirme kümesine eklenen öğelerin sayısını artırabilir. Genel olarak, taahhüt edilen koleksiyonun **Özet** sekmesindeki **Koleksiyon içeriği** bölümünde tanımlanan üst öğe sayısı, taslak koleksiyondaki tahmini öğe sayısına eşit olmalıdır.

- **Yinelenen öğeler**. Önceki bir koleksiyonda gözden geçirme kümesine eklenmiş olan taslak koleksiyondaki öğeler eklenmez. Daha önce açıklandığı gibi, koleksiyondaki yinelenen öğelerin sayısı **Özet** sekmesinin **Koleksiyon içeriği** bölümünde görüntülenir.

- **Koleksiyon yapılandırma seçenekleri**. Taslak koleksiyonu bir gözden geçirme kümesine işlerken konuşma yazışmalarını, bulut eklerini ve belge sürümlerini dahil etme seçeneğiniz vardır. Gözden geçirme kümesine eklenen bu öğelerden hiçbiri taslak koleksiyonun tahminlerine dahil değildir. Bunlar yalnızca koleksiyonu işlediğiniz zaman tanımlanır ve toplanır. Bu seçeneklerin seçilmesi büyük olasılıkla gözden geçirme kümesine eklenen öğe sayısını artırır. 

    Örneğin, taslak koleksiyon için tahmine SharePoint belgelerinin birden çok sürümü dahil değildir. Ancak bir taslak koleksiyonu işlerken tüm belge sürümlerini dahil etme seçeneğini belirlerseniz, gözden geçirme kümesine eklenen öğelerin gerçek sayısı (ve toplam boyutu) artar.

    Bu seçenekler hakkında daha fazla bilgi için bkz [. Taslak koleksiyonu gözden geçirme kümesine işleme](commit-draft-collection.md#commit-a-draft-collection-to-a-review-set-in-ediscovery-premium).

Taslak koleksiyondaki tahmini sonuçların gerçek taahhüt edilen sonuçlardan farklı olmasının diğer nedenleri aşağıdadır.

- **Taslak koleksiyonlarda sonuçların tahmini yöntemi**. Taslak koleksiyon tarafından döndürülen arama sonuçlarının tahmini, koleksiyon sorgu ölçütlerini karşılayan öğelerin tahminidir (gerçek sayı değil). E-posta öğelerinin tahminini derlemek için, Exchange veritabanından arama ölçütlerini karşılayan ileti kimliklerinin listesi istenir. Ancak, koleksiyonu bir gözden geçirme kümesine işlediğiniz zaman, koleksiyon yeniden çalıştırılır ve gerçek iletiler Exchange veritabanından alınır. Bu nedenle, tahmini öğe sayısı ve gerçek öğe sayısının nasıl belirlendiği nedeniyle farklılıklar ortaya çıkabilir.

- **Taslak koleksiyonları tahmin etme ve işleme zamanları arasında gerçekleşen değişiklikler**. Bir gözden geçirme kümesine taslak koleksiyon işlediğinizde, arama dizininde arama ölçütlerine uyan en son öğeleri toplamak için arama yeniden çalıştırılır. Taslak koleksiyonun son çalıştırıldığı zaman ile taslak koleksiyonun bir gözden geçirme kümesine kabul edildiği zaman arasında arama ölçütlerini karşılayan ek öğeler oluşturulmuş, gönderilmiş veya silinmiş olabilir. Ayrıca, taslak koleksiyon sonuçları tahmin edildiğinde arama dizininde yer alan öğelerin, koleksiyonu işlemeden önce bir veri kaynağından temizlendikleri için artık orada olmaması da mümkündür. Bu sorunu azaltmanın bir yolu, koleksiyon için bir tarih aralığı belirtmektir. Bir diğer yol da öğelerin korunması ve temizlenememeleri için içerik konumlarına ayrı tutmaktır.

- **Dizine alınmamış öğeler**. Taslak koleksiyon tüm Exchange posta kutularını veya tüm SharePoint sitelerini aramayı içeriyorsa, yalnızca koleksiyon ölçütlerine uyan öğeleri içeren içerik konumlarından dizine alınmamış öğeler gözden geçirme kümesine eklenir. Başka bir deyişle, bir posta kutusunda veya sitede sonuç bulunamazsa, bu posta kutusu veya sitedeki dizine alınmamış öğeler gözden geçirme kümesine eklenmez. Ancak, tüm içerik konumlarındaki dizine alınmamış öğeler (koleksiyon sorgusuyla eşleşen öğeler içermeyen öğeler bile) tahmini koleksiyon sonuçlarına dahil edilir.

    Alternatif olarak, taslak koleksiyonda belirli içerik konumları varsa (yani taslak koleksiyon sihirbazındaki **Ek konumlar** sayfasında belirtilen belirli posta kutuları veya siteler), aramada belirtilen içerik konumlarından dizine alınmamış öğeler (koleksiyon ölçütleri tarafından hariç tutulmaz) dışarı aktarılır. Bu durumda, tahmini dizinlenmemiş öğe sayısı ve gözden geçirme kümesine eklenen dizinlenmemiş öğe sayısı aynı olmalıdır.
