---
title: Advanced eDiscovery'de etiketleme ve ilgi Advanced eDiscovery
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
ms.assetid: 8576cc86-d51b-4285-b54b-67184714cc62
ROBOTS: NOINDEX, NOFOLLOW
description: İlgi Düzeyi eğitim aşamasında etiketle ilgili adımları öğrenin ve sonra 40 dosyalık eğitim örneğiyle Advanced eDiscovery.
ms.openlocfilehash: c21ec89896dbd67bd348abd317d1389f8e105fda
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62988159"
---
# <a name="tagging-and-relevance-training-in-advanced-ediscovery"></a>Advanced eDiscovery'de etiketleme ve ilgi Advanced eDiscovery
  
Bu makalede, Advanced eDiscovery'te uygun ilgi düzeyi eğitim modülüyle çalışma Advanced eDiscovery.
  
Advanced eDiscovery'de Değerlendirme tamamlandıktan ve İlgi Düzeyi eğitim aşamasına girersiniz, etiketleme için Etiket sekmesine 40 dosyalık bir eğitim örneği konur.
  
## <a name="performing-relevance-training"></a>İlgi Düzeyi eğitimi gerçekleştirme

1. İlgi **Düzeyi Etiketi \> sekmesinde** , sol bölmede Varsayılan olarak Etiketleme bölmesi görüntülenir ve örnek dosyalar, etiketleme için tek tek görüntülenir.

    ![İlgi Düzeyi Etiketi paneli.](../media/0cf19ab4-b427-4a7f-8749-0f4ed9afaf58.png)
  
    Etiket **sekmesinde** , dosyanın görünen adı gösterilir. Bu yol, e-posta konusu, başlık veya kullanıcı tanımlı ad olabilir. Kimlik, dosya yolu veya metin yolu, dosyanın yoluna sağ tıklanır ve kopyalanır.

    **Etiket sekmesi** etiketleme istatistikleri, dosya örnek numarasını (sol bölmenin en üstünde), görüntülenmiş durumdaki dosyanın toplam dosyasındaki (sağ bölmenin altı) sayısını ve örnekteki etiketlenmiş dosyaların geçerli toplam sayısını (sol bölmenin en altında) gösterir; siz dosyaları etiketleye devam ettiyken bu numaralar değişir. Bu, Değerlendirme, Eğitim, Yakalama veya Test'te yapılan ilgi düzeyi etiketlemesi için geçerlidir.

    Açıklama, etiket ve aile dosyalarının varlığını belirten simgeler dosyanın üzerindeki çubukta görüntülenir.

2. Aşağıdaki tabloda gösterildiği gibi, dosyanın olayla ilgili uygun olup olmadığını belirleyin ve Etiketleme seçeneği simgesi düğmelerini veya klavye kısayollarını kullanarak dosyayı etiketleme:

   |**Etiketleme seçeneği**|**Açıklama**|**Klavye kısayolu**|**Klavye kısayolunu toplu etiketleme (birden çok sorun için)**|
   |-----|-----|-----|-----|
   |R  <br/> |İlgili  <br/> |Z  <br/> |`Shift + Z`  <br/> |
   |NR  <br/> |Uygun değil  <br/> |X  <br/> |`Shift + X`  <br/> |
   |Atla  <br/> |Atla  <br/> |C  <br/> |`Shift + A`  <br/> |
   |||||

   - Bir dosyada birden çok sorun olduğunda, bir sorunu etiketledikten sonra seçim bir sonraki soruna (varsa) taşınır.  

   - Yönetici veya Olay Yöneticisi tarafından anahtar sözcükleri vurgularken tanımlanan anahtar sözcükler ( \> İlgi Düzeyi Ayarı Vurgulanan anahtar sözcükler), etiketleme sırasında ilgili dosyaları tanımlamanıza yardımcı olmak için (belirtilen renklerle) görüntülenir. Anahtar sözcüğün altı çift çizili ise, anahtar sözcüğün açıklamasının yer alan bir araç ipucu görüntülemek için tık olabilir.

     İsteğe bağlı olarak, **aşağıdaki** seçenekleri ayarlamak **için Etiket sekmesinde** Etiket ayarları'ne tıklayın:

      ![İlgi Düzeyi Etiketi ayarları.](../media/533e89fa-7eb4-409e-ab07-f5aab9296dd8.png)
  
   - **Toplu etiket**: Seçili dosyanın etiketini tüm sorunlar için ayarlamak üzere (zaten etiketlenmiş  sorunları geçersiz kılar) Veya Etiketi kalan etiketsiz sorunlara uygulamak için Gerisini seçerek bir dosyaya birden çok sorun atamak için  bu seçeneği kullanın. Seçili seçenek, o kullanıcı tarafından değiştirilene kadar bu kullanıcının tüm durumlarda (ayar tüm kullanıcının olaylarında kullanıcı başınadır) açık kalır.

   - **Otomatik etiket**: Bir dosyayla ilgili diğer sorunları tek bir uygun etiketlemeden sonra uygun değil olarak ayarlamak için bu onay kutusunu seçin.

   - **Otomatik ilerlet**: Son veya yalnızca etiketsiz sorunu etiketlerken görüntülenen dosya seçimini bir sonraki dosyaya taşımak için bu onay kutusunu seçin.

    Atlanan dosyalar, İlgi Düzeyi eğitimi ve İlgi Düzeyi puanlama amacıyla kabul edilemez.

3. Dosyayla ilişkilendirilmiş serbest metin açıklamalar, sol bölme açılan listesinde **Açıklama** seçeneği aracılığıyla ılamaz ve düzenlenebilir. (isteğe bağlı)

4. Etiketleme yönergeleri, sol bölme açılan listesinde Etiketleme **yönergeleri seçeneği** seçerek ekleyebilirsiniz.

5. Listede tüm dosyaları etiketlemeyi bitirdikten ve sonuçları hesaplamaya hazır olduktan sonra, Hesapla'ya **tıklayın**. **İzle sekmesi** görüntülenir.  

## <a name="working-with-the-sample-files-list"></a>Örnek dosyalar listesiyle çalışma

Örnek dosyalar listesi, eğitim örneğinde yer alan dosyaların listesini görüntülemeye ve bir veya birden çok dosya üzerinde çeşitli eylemler gerçekleştirmeye olanak sağlar. İlgi **Düzeyi Etiketi** \> **sekmesinde**, Örnek dosyalar sol  bölmesinde Değerlendirme, Eğitim, Yakalama ve Tutarsızlık işlemleriyle işlemeyle ilgili örnek dosyaların listesi görüntülenir.
  
1. İlgi **Düzeyi Etiketi \> sekmesinde** , sol bölmede örnek dosyalar açılan listesini seçin. Örnek dosyalar sol bölmede listelenir.

    ![İlgi Düzeyi Etiketi örnek dosyalar listesi.](../media/fd058bdd-645a-4af1-a1eb-bff08581cb18.png)
  
2. Örnek veya Dosya kutularına numarasını girerek veya seçerek, belirli bir örnek **veya dosya** **numarası** seçin.

   - Etiket sekmesinde, görüntülenen dosya listesinin sol sütununda bir dosya sırası **numarası** listelenir. Üst bilgi tıklatlendiğinde dosyaların özgün görüntülenme sırası özgün sırasına döner.

   - Bir dosya satırına tık tıklatsanız bu satırın içeriği sağ bölmede görüntülenir.

   - Alt menü çubuğu seçeneklerini kullanarak geçerli örnekteki dosyalar arasında gezinebilirsiniz. Bunlara ek olarak, gezinti klavye kısayolları da kullanılabilir:
  
     - Örnekteki ilk dosyaya gitmek için: `Shift + Ctrl + <`

     - Örnekteki önceki dosyaya gitmek için: `Shift + <`

     - Örnekteki bir sonraki dosyaya gitmek için: `Shift + >`

     - Örnekteki son dosyaya gitmek için: `Shift + Ctrl + >`
