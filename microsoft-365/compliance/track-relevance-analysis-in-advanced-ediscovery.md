---
title: İlgi Derecesi çözümlemesi Advanced eDiscovery
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
titleSuffix: Office 365
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MOE150
- MET150
ms.assetid: 3ab1e2c3-28cf-4bf5-b0a8-c0222f32bdf5
ROBOTS: NOINDEX, NOFOLLOW
description: İlgi Düzeyi eğitim durumunu görüntülemeyi ve yorumlamayı ve bu konu ile ilgili olay sorunlarına Advanced eDiscovery.
ms.openlocfilehash: 7a2786a727fd233b6617779bae95a26c1b62644e
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62984686"
---
# <a name="track-relevance-analysis-in-advanced-ediscovery"></a>İlgi Derecesi çözümlemesi Advanced eDiscovery
  
İlgi Advanced eDiscovery sekmesinde, İlgi Düzeyi İzle sekmesi Etiket sekmesinde gerçekleştirilen İlgi Düzeyi eğitimi'nin hesaplanan geçerliliğini görüntüler ve İlgi Düzeyi'ne uygun eğitim sürecinde atlanacak bir sonraki adımı gösterir. 
  
## <a name="tracking-relevance-training-status"></a>İlgi Düzeyi eğitim durumunu izleme

1. Aşağıdaki Sorun adı iletişim kutusunun aşağıdaki örneğinde gösterildiği gibi, olay sorunları için uygun uygunluk **Izleme'de aşağıdaki** ayrıntıları görüntüleyebilirsiniz.

   - **Değerlendirme**: Bu ilerleme göstergesi, Bu noktaya gerçekleştirilen İlgi Düzeyi eğitimi'nin hata marjı açısından değerlendirme hedefini ne derece elde etmiş olduğunu gösterir. İlgi Düzeyi eğitim sonuçlarının zenginliği de görüntülenir.

   - **Eğitim**: Bu renk kodlu ilerleme göstergesi ve araç ipucu, İlgi Düzeyi eğitim sonuçları kararlılığını ve her bir sorun için etiketlenmiş Uygunlik eğitimi örneklerinin sayısını gösteren bir sayısal ölçek gösterir. Uzman, iteratif İlgi Eğitim sürecinin ilerlemesini izler. 
  
   - **Toplu işlem** hesaplama: Bu ilerleme göstergesi, Toplu işlem hesaplamanın tamamlanması hakkında bilgi sağlar.
  
   - **Sonraki adım**: Gerçekleştirilecek bir sonraki adım önerilerini görüntüler. 
  
    Örnekte, bir sorun için başarıyla tamamlanmış bir Değerlendirme gösterilir; bu, tamamlanan renk ilerleme göstergesiyle ve onay işaretiyle gösterilir. Etiketleme devam ediyor, ancak durum hala kararsız olarak kabul ediliyor (araç ipucunda kararlılık durumu da gösteriliyor). Sonraki adım öneri "Eğitim"dir. 
  
    ![İlgi Düzeyi Eğitimi izleme adım 1.](../media/a00fe607-680a-48eb-9d61-4565319f7ab6.png)
  
    Genişletilmiş görünüm, ek bilgileri ve seçenekleri görüntüler. Görüntülenen geçerli hata kenar boşluğu, var olan (zaten etiketlenmiş) değerlendirme dosyalarına göre değerlendirmenin geçerli durumuna göre geri çekmenin hata kenar boşluğu olur.
  
    > [!NOTE]
    >  Değerlendirme aşaması, her sorun için Değerlendirme onay kutusu ve sonra  da "tüm sorunlar" için temiz temiz kullanarak atlanır. Ancak bunun sonucunda, bu sorunun istatistikleri olmayacaktır. > Onay kutusunu **temizlemek** yalnızca değerlendirme yapılmadan önce yapılabilir. Bir olayda birden çok sorun varsa, değerlendirme yalnızca her soruna ilişkin onay kutusu temiz olursa atlanır 
  
    Değerlendirme ilk örnek dosya kümesiyle tamamlanmazsa, daha fazla dosya etiketlemede bir sonraki adım değerlendirme olabilir.
  
    İlgi **Düzeyi** **İzle'de**\> eğitim ilerleme göstergesi ve araç ipucu, kararlılıka ulaşmak için gereken tahmini ek örneklerin sayısını gösteriyor. Bu tahmin, gereken ek eğitim için bir kılavuz sağlar.
  
    ![İlgi Düzeyi Eğitimi izleme.](../media/98dbc3f5-5238-4d73-9f88-1aa4d77ea729.png)
  
2. Etiketlemeyi bitirin ve eğitime devam etmek için ihtiyacınız varsa Eğitim'e **tıklayın**. Ek eğitim için yüklenen dosya kümesinden başka bir örnek dosya kümesi oluşturulur. Ardından, daha fazla dosya etiketlemek ve eğitmek için Etiket sekmesine geri döndürülürsiniz.

### <a name="reaching-stable-training-levels"></a>Kararlı eğitim düzeylerine ulaşıyor

Değerlendirme dosyaları kararlı bir eğitim düzeyi elde edildikten sonra, Advanced eDiscovery hesaplama için hazır olur.
  
> [!NOTE]
> Genellikle, üç kararlı eğitim örnek olayından sonra bir sonraki adım "Toplu hesaplama" adımıdır. Örneğin, önceki örneklerden dosya etiketlemede veya çekirdek dosyalarının ekli olduğu olaylarda özel durumlar olabilir. 
  
### <a name="performing-batch-calculation"></a>Toplu işlem hesaplaması gerçekleştirme

Toplu hesaplama, eğitim başarıyla tamamlandıktan sonraki adım olarak yürütülür (ilerleme çubuğu tarafından kararlı bir eğitim durumu gösterildiğinde, araç ipucunda bir onay işareti ve kararlı durum.) Toplu hesaplama, dosyaların ilgi derecesini değerlendirmek ve İlgi Düzeyi puanları atamak için Uygunluk eğitimi sırasında alınan bilgileri tüm dosya popülasyonu için uygular.
  
Birden fazla sorun olduğunda, her sorun için Toplu işlem hesaplaması yapılır. Toplu işlem hesaplaması sırasında, dosyaların hepsi işlenirken ilerleme durumu izlenir. 
  
Burada, bu noktada ek bir ilgi düzeyi eğitimi gerek olmadığını belirten "Yok" adımı önerilir. Bir sonraki aşama İlgi **DüzeyiNe Göre Karar \> sekmesidir** . 
  
Toplu işlem hesaplaması sonrasında yeni dosyaları içeri yüklemek için yönetici içeri aktarılan dosyaları yeni bir yüke ekleyebilir.
  
> [!NOTE]
> Toplu işlem **hesaplaması sırasında** İptal'e tıklarsanız, işlem zaten yürütülen işlemi kaydeder. Toplu işlem hesaplamayı yeniden çalıştırdığınızda, işlem en son yürütülen noktadan devam eder. 
  
### <a name="assessing-tagging-consistency"></a>Etiketleme tutarlılığını değerlendirme

Dosya etiketlemede tutarsızlıklar varsa çözümlemeyi etkileyebilir. Sonuçlar Advanced eDiscovery veya tutarlılık tam olarak emin olmadığı zaman, tutarlılık işleminin en iyi sonucu verir. Olası tutarsız etiketlenmiş dosyaların listesi döndürülür ve bunlar gerektiğinde gözden geçirip yeniden etiketlenir.
  
> [!NOTE]
> Yedi veya daha fazla eğitim değerlendirmeyi yuvarlattıktan sonra,  \>  \>  \> etiketleme tutarlılığı uygun ilgi derecesini Sorunu İzle **Ayrıntılı sonuçları Eğitim ilerleme durumu'nda** \> **22223'te 2013'te 2013'te** 2013'te 2013 Eğitimin tutarlılığı 24 saat ve 24 saat daha kısa bir süre içinde 2 Bu gözden geçirme, bir defada tek bir sorun için yapılır.
  
1. İlgi **Düzeyi İzle'de\>**, sorunun satırına genişletin.
  
2. Sonraki adımın sağ **tarafından Değiştir'e** **tıklayın**.
  
3. **Tutarsızlıkları sonraki adım seçeneği olarak,** yedi **eğitim örnekten** sonra etiketle'yi seçin ve Tamam'a **tıklayın**.
  
4. **Etiket tutarsızlıkları'ı seçin**. **Etiket sekmesi** açılır ve gerekirse yeniden etiketle ilgili tutarsızlıkların listesi görüntülenir.
  
5. Değişiklikleri **göndermek için** Hesapla'ya tıklayın. Tutarsızlıkları etiketlemeden sonraki adım "Eğitim" adımıdır. 
  
## <a name="viewing-and-using-relevance-results"></a>İlgi Derecesi sonuçlarını görüntüleme ve kullanma

İlgi **Düzeyi İzle sekmesinde\>**, sorunun satırına genişletin ve Ayrıntılı sonuçlar'ın yanında **Görünüm'e** **tıklayın**. Ayrıntılı sonuçlar bölmeleri, aşağıda gösterildiği ve açıklandığı gibi görüntülenir.
  
![İlgi düzeyi eğitimi ayrıntılı sonuçları.](../media/495c04a9-ed1e-4355-8cab-c14270ca2bbb.png)
  
### <a name="tagging-summary"></a>Etiketleme özeti

 Aşağıda gösterilen örnekte Etiketleme özeti, Değerlendirme, Eğitim ve Yakalama dosyası etiketleme işlemlerinin her biri için toplamları görüntüler.
  
![İlgi Alanı Etiketleme özetini takip etme.](../media/0ec906fc-bc84-4245-a964-fb3ca37891db.png)
  
### <a name="keywords"></a>Anahtar Sözcükler

Anahtar sözcük, bir dosyanın uygun olup olmadığının önemli bir göstergesi olarak tanım Advanced eDiscovery bir dosyada benzersiz bir dize, sözcük, tümcecik veya sözcük dizisidir. "Ekle" sütun listesi, uygun olarak etiketlenen dosyalarda anahtar sözcük ve ağırlıkları, "Dışla" sütunlarında ise Uygun değil olarak etiketlenen dosyalarda anahtar sözcükler ve ağırlıklar listelenir.
  
Advanced eDiscovery veya pozitif anahtar sözcük ağırlık değerlerini atar. Ağırlık ne kadar yüksekse, anahtar sözcüğün göründüğü bir dosyaya Toplu işlem hesaplama sırasında daha yüksek bir İlgi Puanı atanma olasılığı da o kadar yüksektir.
  
En Advanced eDiscovery listesi, dosya gözden geçirme işleminin herhangi bir noktasında uzman tarafından yapılan bir listeyi tamamlayıcı bir liste veya dolaylı bir sanity denetimi olarak kullanılabilir.
  
### <a name="training-progress"></a>Eğitim ilerleme durumu

Eğitim **İlerleme Durumu** bölmesi, aşağıdaki örnekte gösterildiği gibi bir eğitim ilerleme durumu grafiği ve kalite göstergesi görüntüsü içerir.
  
![İlgi Düzeyi Eğitimin ilerlemesini izleme.](../media/8a5089f5-a162-4246-ae09-bc1921859860.png)
  
**Eğitim kalitesi göstergesi**: Etiketleme tutarlılığının derecelendirmelerini aşağıdaki gibi görüntüler:
  
- **İyi**: Dosyalar tutarlı olarak etiketlenir. (Görüntülenen yeşil ışık)
  
- **Orta**: Bazı dosyalar tutarsız etiketlenmiş olabilir. (Görüntülenen sarı ışık)

- **Uyarı**: Birçok dosya tutarsız etiketlenmiş olabilir. (Kırmızı ışık görüntülenir)

**Eğitim ilerleme grafiği**: F-measure değeriyle karşılaştırıldığında, birçok İlgi düzeyi eğitim döngüsü sonrasında ilgi düzeyi eğitim kararlılığının derecesini gösterir. Grafik boyunca soldan sağa doğru ilerlerken, uygunluk aralığı daralarak ve ilgi düzeyi eğitim sonuçları en iyi duruma geldiğinde kararlılığı belirlemek için F ölçümüyle birlikte Advanced eDiscovery Uygunluk düzeyi ile kullanılır.
  
> [!NOTE]
> İlgi derecesi, Geri Çekme'nin Duyarlılık için iki kat fazla ağırlık aldığı F2 ölçüstü olan F2'yi kullanır. Yüksek zenginlik (%25'in üzerinde) olan durumlar için uygunluğu F1 (1:1 oranı) kullanır. F-measure oranı, Uygunluk Ayarı **Gelişmiş ayarları'nın içinde** \> **yatıtılabilirsiniz**.
  
### <a name="batch-calculation-results"></a>Toplu işlem hesaplama sonuçları

Toplu **işlem hesaplama** sonuçları bölmesi, ilgi derecesi için puanlandı sayısını aşağıdaki gibi içerir: 
  
- **Başarılı**
  
- **Boş**: Metin eklemez, örneğin yalnızca boşluklar/sekmeler
  
- **Başarısız**: Aşırı boyuttan dolayı veya okunamadı
  
- **Yoksayılan**: Aşırı boyuttan dolayı
  
- **Anlamsız: Anlamsız** metinler içerir veya bu konuyla ilgili hiçbir özellik yoktur
  
> [!NOTE]
> Boş, Başarısız, Yoksayılan veyaBulan -1 ilgi puanı alır.
  
### <a name="training-statistics"></a>Eğitim istatistikleri

Eğitim **istatistikleri bölmesinde**, ilgi düzeyi eğitimi sonucunda elde Advanced eDiscovery istatistikleri ve grafikleri görüntüler. 
  
![İlgi Düzeyi Eğitim istatistiklerini izleme.](../media/9a07740e-20d3-49fb-b9b9-84265e0a1836.png)
  
Bu görünümde aşağıdakiler gösterir:
  
- **Gözden geçirme-geri çekme** oranı: Varsayımsal olarak doğrusal bir gözden geçirmede, sonuçların Ilgi Dereceleri'ne göre karşılaştırılması. Gözden geçirme kümesi boyut kümesine göre geri çekme tahmin ediliyor.
  
- **Parametreler**: Tüm vakanın dosya popülasyonına göre gözden geçirme kümesiyle ilgili kümülatif hesaplanan istatistikler.
  
- **Gözden** Geçir: Bu kesme kesmeye dayalı olarak gözden geçirilecek dosyaların yüzdesi.
  
- **Geri** Çekme: Gözden geçirme kümesinde İlgili dosyaların yüzdesi. 
  
- **İlgi düzeyi puanına** göre dağılım: Solda koyu gri görünen dosyalar, kesmeoff puanının altında yer almaktadır. Araç ipucu, İlgi Derecesini ve toplam dosyalara göre ayarlanmış gözden geçirme dosyasındaki dosyaların ilgili yüzdesini görüntüler.
