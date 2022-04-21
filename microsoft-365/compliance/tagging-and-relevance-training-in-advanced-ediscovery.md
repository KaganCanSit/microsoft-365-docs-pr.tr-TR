---
title: eBulma'da etiketleme ve İlgi eğitimi (Premium)
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
description: eBulma'nın İlgi eğitim aşamasında (Premium) 40 dosyadan oluşan bir eğitim örneğini etiketleme ve bunlarla çalışma adımlarını öğrenin.
ms.openlocfilehash: 9078bf36e1434cad0362c4584b5c61fd49e86c14
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/20/2022
ms.locfileid: "64996690"
---
# <a name="tagging-and-relevance-training-in-ediscovery-premium"></a>eBulma'da etiketleme ve İlgi eğitimi (Premium)

[!include[Purview banner](../includes/purview-rebrand-banner.md)]
  
Bu makalede, Microsoft Purview eKeşif'te (Premium) İlgi eğitim modülüyle çalışma yordamı açıklanmaktadır.
  
Değerlendirme eBulma(Premium) içinde tamamlandıktan ve İlgi eğitim aşamasına girdikten sonra, etiketleme için Etiket sekmesine 40 dosyadan oluşan bir eğitim örneği getirilir.
  
## <a name="performing-relevance-training"></a>İlgi eğitimi gerçekleştirme

1. **\> İlgi Etiketi** sekmesinde, etiketleme bölmesi varsayılan olarak sol bölmede görüntülenir ve örnek dosyalar birer birer etiketleme için görüntülenir.

    ![İlgi Etiketi paneli.](../media/0cf19ab4-b427-4a7f-8749-0f4ed9afaf58.png)
  
    **Etiket** sekmesinde dosyanın görünen adı gösterilir. Bu yol, e-posta konusu, başlık veya kullanıcı tanımlı ad olabilir. Kimlik, dosya yolu veya metin yolu, dosyanın yoluna sağ tıklayarak kopyalanabilir.

    **Etiket** sekmesi etiketleme istatistikleri, dosya örnek numarasını (sol bölmenin en üstünde), o anda görüntülenen dosyanın örnekteki toplam dosya sayısı (sağ bölmenin altı) ve siz dosyaları etiketledikçe değişen örnekteki etiketli dosyaların geçerli toplam sayısını (sol bölmenin alt kısmı) gösterir. Bu, Değerlendirme, Eğitim, Yakalama veya Test'te yapılan tüm İlgi etiketlemeleri için geçerlidir.

    Açıklamaların, etiketlerin ve aile dosyalarının varlığını gösteren simgeler, dosya görünümünde dosyanın üzerindeki bir çubukta görüntülenir.

2. Aşağıdaki tabloda gösterildiği gibi, dosyanın servis talebi sorunuyla alakasını belirleyin ve Etiketleme seçeneği simgesi düğmelerini veya klavye kısayollarını kullanarak dosyayı etiketleyin:

   |**Etiketleme seçeneği**|**Açıklama**|**Klavye kısayolu**|**Toplu etiketleme klavye kısayolu (birden çok sorun için)**|
   |-----|-----|-----|-----|
   |R  <br/> |Ilgili  <br/> |Z  <br/> |`Shift + Z`  <br/> |
   |NR  <br/> |İlgili değil  <br/> |X  <br/> |`Shift + X`  <br/> |
   |Atlamak  <br/> |Atlamak  <br/> |C  <br/> |`Shift + A`  <br/> |
   |||||

   - Dosya için birden çok sorun olduğunda, bir sorunu etiketledikten sonra seçim bir sonraki soruna (varsa) taşınır.  

   - Anahtar sözcükler vurgulanırken Yönetici veya Servis Talebi yöneticisi tarafından tanımlanan anahtar sözcükler (İlgi kurulumu \> Vurgulanan anahtar sözcükler), etiketleme sırasında ilgili dosyaların tanımlanmasına yardımcı olmak için görüntülenir (belirtilen renklerde). Bir anahtar sözcüğün çift alt çizgisi varsa, anahtar sözcüğün açıklamasıyla bir araç ipucu görüntülemek için bu anahtar sözcük tıklatılabilir.

     İsteğe bağlı olarak, **Etiket** sekmesinde **Etiket ayarları'na** tıklayarak aşağıdaki seçenekleri ayarlayın:

      ![İlgi Etiketi ayarları.](../media/533e89fa-7eb4-409e-ab07-f5aab9296dd8.png)
  
   - **Toplu etiket**: Seçili dosyanın etiketini tüm sorunlar (geçersiz kılmalar zaten etiketlenmiş sorunlar) için ayarlamak üzere **Tümü'ne** tıklayarak veya etiketi kalan etiketlenmemiş sorunlara uygulamak üzere **Geri kalanı'nı** seçerek bir dosya için birden çok sorun atamak için bu seçeneği kullanın. Seçilen seçenek, söz konusu kullanıcı tarafından değiştirilene kadar bu kullanıcının tüm servis talepleri için geçerli kalır (ayar, kullanıcının tüm servis talepleri için kullanıcı başınadır).

   - **Otomatik etiket**: Bir dosyayla ilgili diğer sorunları tek bir İlgili etiketlemeden sonra uygun değil olarak ayarlamak için bu onay kutusunu seçin.

   - **Otomatik ilerleme**: Son veya yalnızca etiketlenmemiş sorunu etiketlerken görüntülenen dosya seçimini bir sonraki dosyaya taşımak için bu onay kutusunu seçin.

    Atlanan dosyalar İlgi eğitimi ve İlgi puanlama amacıyla dikkate alınmaz.

3. Bir dosyayla ilişkili serbest metin açıklamaları, sol bölme açılan listesindeki **Açıklama** seçeneği aracılığıyla görüntülenebilir ve düzenlenebilir. (isteğe bağlı)

4. Etiketleme yönergeleri, sol bölme açılan listesinde **Etiketleme yönergeleri** seçeneği seçilerek görüntülenebilir.

5. Listedeki tüm dosyaları etiketlemeyi bitirdikten ve sonuçları hesaplamaya hazır olduktan sonra **Hesapla'ya** tıklayın. **İzle** sekmesi görüntülenir.  

## <a name="working-with-the-sample-files-list"></a>Örnek dosyalar listesiyle çalışma

Örnek dosyalar listesi, eğitim örneğindeki dosyaların listesini görüntülemenizi ve bir veya daha fazla dosya üzerinde çeşitli eylemler gerçekleştirmenizi sağlar.  \> İlgi **Etiketi** sekmesinde, **Örnek dosyalar** sol bölmesinde Değerlendirme, Eğitim, Yakalama ve Tutarsızlık işlemleriyle işlenmeye yönelik örnek dosyaların listesi görüntülenir.
  
1. **İlgi \> Etiketi** sekmesinde, sol bölmedeki örnek dosyalar açılan listesini seçin. Örnek dosyalar sol bölmede listelenir.

    ![İlgi Etiketi örnek dosyalar listesi.](../media/fd058bdd-645a-4af1-a1eb-bff08581cb18.png)
  
2. **Örnek** veya **Dosya** kutularına numarasını girerek veya seçerek belirli bir örnek veya dosya numarasını seçin.

   - **Etiket** sekmesinde görüntülenen dosya listesinin sol sütununda bir dosya dizisi numarası listelenir. Üst bilgi tıklanarak dosyaların özgün görüntülenen sırası özgün sırasına döner.

   - Bir dosya satırına tıklanması, içeriğini sağ bölmede görüntüler.

   - Alt menü çubuğu seçeneklerini kullanarak geçerli örnekteki dosyalar arasında gezinin. Ayrıca, gezinti klavye kısayolları da kullanılabilir:
  
     - Örnekteki ilk dosyaya gitmek için: `Shift + Ctrl + <`

     - Örnekte önceki dosyaya gitmek için: `Shift + <`

     - Örnekteki bir sonraki dosyaya gitmek için: `Shift + >`

     - Örnekteki son dosyaya gitmek için: `Shift + Ctrl + >`
