---
title: eBulma'da İlgi analizini izleme (Premium)
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
description: eBulma'daki (Premium) durum sorunları için İlgi eğitim durumunu ve sonuçlarını görüntülemeyi ve yorumlamayı öğrenin.
ms.openlocfilehash: 53f1fa12849651cd01172a320eaa014614634e92
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/19/2022
ms.locfileid: "64935532"
---
# <a name="track-relevance-analysis-in-ediscovery-premium"></a>eBulma'da İlgi analizini izleme (Premium)
  
Microsoft Purview eBulma'da (Premium), İlgi İzleme sekmesi Etiket sekmesinde gerçekleştirilen İlgi eğitiminin hesaplanmış geçerliliğini görüntüler ve İlgi alanındaki yinelemeli eğitim sürecinde atılması gereken sonraki adımı gösterir. 
  
## <a name="tracking-relevance-training-status"></a>İlgi eğitim durumunu izleme

1. Aşağıdaki **Sorun adı** iletişim kutusunun aşağıdaki örneğinde gösterildiği gibi, servis talebi sorunları için İlgi İzleme bölümünde aşağıdaki ayrıntıları görüntüleyin.

   - **Değerlendirme**: Bu ilerleme göstergesi, bu noktaya kadar gerçekleştirilen İlgi eğitiminin hata marjı açısından değerlendirme hedefine ne derece ulaştığını gösterir. İlgi eğitim sonuçlarının zenginliği de görüntülenir.

   - **Eğitim**: Bu renk kodlu ilerleme göstergesi ve araç ipucu, İlgi eğitimi sonuçlarının kararlılığını ve her sorun için etiketlenen İlgi eğitimi örneklerinin sayısını gösteren sayısal ölçeği gösterir. Uzman, yinelemeli İlgi eğitim sürecinin ilerleme durumunu izler. 
  
   - **Toplu işlem hesaplaması**: Bu ilerleme göstergesi Batch hesaplamasının tamamlanması hakkında bilgi sağlar.
  
   - **Sonraki adım**: Gerçekleştirilecek bir sonraki adım için öneriyi görüntüler. 
  
    Örnekte, tamamlanmış renk ilerleme göstergesi ve onay işaretiyle gösterilen, bir sorun için başarıyla tamamlanmış bir Değerlendirme gösterilir. Etiketleme devam ediyor, ancak durum hala kararsız olarak kabul ediliyor (kararlılık durumu bir araç ipucunda da gösterilir). Sonraki adım önerisi "Eğitim"dir. 
  
    ![İlgi Eğitimi izleme adımı 1.](../media/a00fe607-680a-48eb-9d61-4565319f7ab6.png)
  
    Genişletilmiş görünümde ek bilgiler ve seçenekler görüntülenir. Görüntülenen geçerli hata kenar boşluğu, mevcut (zaten etiketli) değerlendirme dosyaları göz önüne alındığında, geçerli değerlendirme durumunda geri çağırmanın hata kenar boşluğudur.
  
    > [!NOTE]
    >  Değerlendirme aşaması, sorun başına **Değerlendirme** onay kutusu ve ardından "tüm sorunlar" için temizlenerek atlanabilir. Ancak sonuç olarak, bu sorun için istatistik olmayacaktır. > **Değerlendirme** onay kutusunun temizlenmesi yalnızca değerlendirme gerçekleştirilmeden önce yapılabilir. Bir durumda birden çok sorun olduğunda, değerlendirme yalnızca her sorun için onay kutusu temizlenmişse atlanır 
  
    Değerlendirme ilk örnek dosya kümesiyle tamamlanmadığında, daha fazla dosya etiketlemek için değerlendirme bir sonraki adım olabilir.
  
    **İlgi** \> **İzleme** bölümünde eğitim ilerleme durumu göstergesi ve araç ipucu, kararlılığı sağlamak için gereken ek örneklerin tahmini sayısını gösterir. Bu tahmin, gereken ek eğitim için bir kılavuz sağlar.
  
    ![İlgi Eğitimi izleme.](../media/98dbc3f5-5238-4d73-9f88-1aa4d77ea729.png)
  
2. Etiketlemeyi bitirdiğinizde ve eğitime devam etmeniz gerekiyorsa **Eğitim'e** tıklayın. Ek eğitim için yüklenen dosya kümesinden başka bir örnek dosya kümesi oluşturulur. Daha sonra daha fazla dosyayı etiketlemek ve eğitmek için Etiket sekmesine dönersiniz.

### <a name="reaching-stable-training-levels"></a>Kararlı eğitim düzeylerine ulaşma

Değerlendirme dosyaları kararlı bir eğitim düzeyine ulaştıktan sonra, eBulma (Premium) Batch hesaplaması için hazırdır.
  
> [!NOTE]
> Genellikle üç kararlı eğitim örneğinden sonra bir sonraki adım "Batch hesaplaması"dır. Örneğin, önceki örneklerden dosyaların etiketlenmesinde değişiklikler olduğunda veya çekirdek dosyalar eklendiğinde özel durumlar olabilir. 
  
### <a name="performing-batch-calculation"></a>Batch hesaplaması gerçekleştirme

Toplu hesaplama, eğitim başarıyla tamamlandıktan sonraki adım olarak yürütülür (ilerleme çubuğu tarafından kararlı bir eğitim durumu gösterildiğinde, araç ipucunda bir onay işareti ve kararlı durum.) Toplu hesaplama, İlgi eğitimi sırasında elde edilen bilgileri tüm dosya popülasyonu için, dosyaların ilgi düzeyini değerlendirmek ve İlgi puanlarını atamak için uygular.
  
Birden fazla sorun olduğunda, sorun başına Batch hesaplaması yapılır. Batch hesaplaması sırasında, tüm dosyalar işlenirken ilerleme durumu izlenir. 
  
Burada, önerilen bir sonraki adım ,bu noktada ek yinelemeli İlgi eğitimine gerek olmadığını belirten "Yok" adımıdır. Sonraki aşama İlgi Kararı sekmesidir **\>**. 
  
Batch hesaplaması sonrasında yeni dosyaları içeri aktarmak istiyorsanız, yönetici içeri aktarılan dosyaları yeni bir yüke ekleyebilir.
  
> [!NOTE]
> Batch hesaplaması sırasında **İptal'e** tıklarsanız, işlem zaten yürütülmüş olanları kaydeder. Batch hesaplamasını yeniden çalıştırırsanız, işlem son yürütülen noktadan devam eder. 
  
### <a name="assessing-tagging-consistency"></a>Etiketleme tutarlılığını değerlendirme

Dosya etiketlemede tutarsızlıklar varsa, bu çözümlemeyi etkileyebilir. Sonuçlar en uygun olmadığında veya tutarlılık şüpheli olduğunda eBulma (Premium) etiketleme tutarlılığı işlemi kullanılabilir. Tutarsız olarak etiketlenmiş olabilecek dosyaların listesi döndürülür ve gerektiğinde bunlar gözden geçirilip yeniden etiketlenebilir.
  
> [!NOTE]
> Değerlendirmeden sonra yedi veya daha fazla eğitim turu sonrasında etiketleme tutarlılığı İlgi **İzleme** \> **Sorunu** \> **Ayrıntılı sonuçları** \> **Eğitim ilerleme durumu** **bölümünde** \> görüntülenebilir. Bu inceleme bir kerede bir sorun için yapılır.
  
1. **İlgi \> İzleme** bölümünde bir sorunun satırını genişletin.
  
2. **Sonraki adımın** sağındaki **Değiştir'e** tıklayın.
  
3. Yedi eğitim örneğinden sonra **Sonraki adım** seçeneği olarak **Etiket tutarsızlıkları'nı** seçin ve **Tamam'a** tıklayın.
  
4. **Tutarsızlıkları etiketle'yi** seçin. **Etiket** sekmesi açılır ve gerektiğinde yeniden etiketlenmesi gereken tutarsızlıkların listesi görüntülenir.
  
5. Değişiklikleri göndermek için **Hesapla'ya** tıklayın. Tutarsızlıkları etiketlemeden sonraki adım "Eğitim"dir. 
  
## <a name="viewing-and-using-relevance-results"></a>İlgi sonuçlarını görüntüleme ve kullanma

**İlgi \> İzleme** sekmesinde, sorunun satırını genişletin ve **Ayrıntılı sonuçlar'ın** yanındaki **Görünüm'e** tıklayın. Ayrıntılı sonuçlar bölmeleri aşağıda gösterildiği ve açıklandığı gibi görüntülenir.
  
![İlgi eğitimi ayrıntılı sonuçları.](../media/495c04a9-ed1e-4355-8cab-c14270ca2bbb.png)
  
### <a name="tagging-summary"></a>Etiketleme özeti

 Aşağıda gösterilen örnekte Etiketleme **özeti** Değerlendirme, Eğitim ve Yakalama dosyası etiketleme işlemlerinin her birine ait toplamları görüntüler.
  
![İlgi İzleme etiketleme özeti.](../media/0ec906fc-bc84-4245-a964-fb3ca37891db.png)
  
### <a name="keywords"></a>Anahtar kelime -ler

Anahtar sözcük, bir dosyanın ilgili olup olmadığının önemli bir göstergesi olarak eBulma (Premium) tarafından tanımlanan bir dosyadaki benzersiz bir dize, sözcük, tümcecik veya sözcük dizisidir. "Dahil Et" sütunları, İlgili olarak etiketlenen dosyalardaki anahtar sözcük ve ağırlıklar, "Hariç Tut" sütunları ise uygun değil olarak etiketlenen dosyalarda anahtar sözcükleri ve ağırlıkları listeler.
  
eBulma (Premium) negatif veya pozitif anahtar sözcük ağırlık değerleri atar. Ağırlık ne kadar yüksek olursa, Batch hesaplaması sırasında anahtar sözcüğün görüntülendiği bir dosyaya daha yüksek bir İlgi puanı atanma olasılığı o kadar yüksek olur.
  
EBulma (Premium) anahtar sözcük listesi, bir uzman tarafından oluşturulan bir listeyi tamamlamak veya dosya gözden geçirme sürecinin herhangi bir noktasında dolaylı bir akıl sağlığı denetimi olarak kullanılabilir.
  
### <a name="training-progress"></a>Eğitim ilerleme durumu

**Eğitim İlerleme Durumu** bölmesi, aşağıdaki örnekte gösterildiği gibi bir eğitim ilerleme durumu grafiği ve kalite göstergesi görüntüsü içerir.
  
![İlgi Eğitimin ilerleme durumunu izleme.](../media/8a5089f5-a162-4246-ae09-bc1921859860.png)
  
**Eğitim kalitesi göstergesi**: Etiketleme tutarlılığının derecelendirmesini aşağıdaki gibi görüntüler:
  
- **İyi**: Dosyalar tutarlı olarak etiketlenir. (Yeşil ışık görüntüleniyor)
  
- **Orta**: Bazı dosyalar tutarsız olarak etiketlenebilir. (Sarı ışık görüntülenir)

- **Uyarı**: Birçok dosya tutarsız olarak etiketlenebilir. (Kırmızı ışık görüntüleniyor)

**Eğitim ilerleme durumu grafiği**: F ölçüsü değerine kıyasla birçok İlgi eğitim döngüsünden sonra İlgi eğitimi kararlılığının derecesini gösterir. Grafikte soldan sağa doğru ilerlerken güvenilirlik aralığı daralıyor ve F ölçüsüyle birlikte eBulma (Premium) İlgi ile birlikte, İlgi eğitim sonuçlarının ne zaman iyileştirileceğini belirlemek için kararlılığı belirlemek için kullanılıyor.
  
> [!NOTE]
> İlgi, Yakalama işlevinin Duyarlık'ın iki katı ağırlık aldığı F2 ölçümünü kullanır. Yüksek zenginliğe (%25'in üzerinde) sahip durumlarda İlgi F1 (1:1 oran) kullanır. F ölçüsü oranı İlgi **kurulumu** \> **Gelişmiş ayarlar** bölümünde yapılandırılabilir.
  
### <a name="batch-calculation-results"></a>Toplu hesaplama sonuçları

**Batch hesaplama sonuçları** bölmesi, İlgi için puanlanan dosya sayısını aşağıda gösterildiği gibi içerir: 
  
- **Başarı**
  
- **Boş**: Metin içermez; örneğin, yalnızca boşluklar/sekmeler
  
- **Başarısız**: Aşırı boyut nedeniyle veya okunamadı
  
- **Yoksayıldı**: Aşırı boyut nedeniyle
  
- **Nebulous**: Anlamsız metinler içeriyor veya sorunla ilgili özellik içermiyor
  
> [!NOTE]
> Boş, Başarısız, Yoksayıldı veya Nebulous, -1 İlgi puanı alır.
  
### <a name="training-statistics"></a>Eğitim istatistikleri

**Eğitim istatistikleri** bölmesi, eBulma (Premium) İlgi eğitiminin sonuçlarını temel alan istatistikleri ve grafikleri görüntüler. 
  
![İlgi Eğitim istatistiklerini izleme.](../media/9a07740e-20d3-49fb-b9b9-84265e0a1836.png)
  
Bu görünümde aşağıdakiler gösterilir:
  
- **Gözden geçirme-geri çağırma oranı**: Varsayımsal olarak doğrusal bir incelemede sonuçların İlgi puanlarına göre karşılaştırması. Gözden geçirme kümesi boyut kümesine göre geri çağırma tahminidir.
  
- **Parametreler**: Tüm servis talebi için dosya popülasyonuyla ilgili olarak gözden geçirme kümesiyle ilgili toplu hesaplanan istatistikler.
  
- **Gözden Geçir**: Bu kesmeye göre gözden geçirilecek dosyaların yüzdesi.
  
- **Geri çağırma**: Gözden geçirme kümesindeki İlgili dosyaların yüzdesi. 
  
- **İlgi puanına göre dağılım**: Soldaki koyu gri ekrandaki dosyalar kesme puanının altındadır. Araç ipucu, toplam dosyayla ilişkili olarak, inceleme dosyasındaki ilgi puanını ve ilgili dosya yüzdesini görüntüler.
