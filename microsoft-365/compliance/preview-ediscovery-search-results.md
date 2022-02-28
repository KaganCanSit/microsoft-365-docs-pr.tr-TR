---
title: eBulma arama sonuçlarını önizleme
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- Strat_O365_IP
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MED150
- MET150
ms.custom:
- seo-marvel-apr2020
description: İçerik arama veya Temel eKbulma araması tarafından döndürülen sonuçların bir örneğinin önizlemesini Microsoft 365 uyumluluk merkezi.
ms.openlocfilehash: af0811d0c442d6f064fd336d4261d1f7b2337dc8
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62985164"
---
# <a name="preview-ediscovery-search-results"></a>eBulma arama sonuçlarını önizleme

İçerik aramalarını veya Core eK bulma durumuyla ilişkilendirilmiş bir aramayı çalıştırdikten sonra, arama tarafından döndürülen sonuçların bir örneğine önizlemede bakabilirsiniz. Arama sorgusu tarafından döndürülen öğelerin önizlemesi, aramanın umarız sonuçları döndür olup olmadığını veya arama sorgusunu değiştirerek yeniden çalıştırmanızı gerektir olup olmadığını belirlemenize yardımcı olabilir.

Arama tarafından döndürülen sonuç örneğini önizlemek için:

1. İçerik Microsoft 365 uyumluluk merkezi arama sayfasına veya Core eKovery durumuna gidin.

2. Uçarak çıkış sayfasını görüntülemek için ara'ya tıklayın.

3. Uç uç sayfasının en altında, Örneği gözden **geçir'e tıklayın**.

   ![Sonuçları önizlemek için, uç sayfada Örneği gözden geçir'e tıklayın.](../media/PreviewSearchResults1.png)

   Arama sonuçlarından bir örnek içeren bir sayfa görüntülenir.

4. Okuma bölmesinde içeriğini görüntülemek için bir öğe seçin.

   ![Okuma bölmesinde öğeleri önizleme.](../media/PreviewSearchResults2.png)

   Önceki ekran görüntüsünde, öğeleri önizlemede görüntülerken arama sorgusundan gelen anahtar sözcüklerin vurgulanmış olduğunu görebilirsiniz.

## <a name="how-the-search-result-samples-are-selected"></a>Arama sonucu örnekleri nasıl seçilir?

Önizleme için rastgele en çok 1.000 öğe kullanılabilir. Rastgele seçilecek öğelere ek olarak, önizleme için kullanılabilen öğeler de aşağıdaki ölçütlere uygun olması gerekir:

- Tek bir içerik konumdan (posta kutusu veya site) en çok 100 öğe öniz kullanılabilir. Bu, önizleme için 1.000'den az öğenin kullanılabilir olabileceği anlamına gelir. Örneğin, dört posta kutusunda arama yaptıysanız ve arama 1.500 tahmini öğe döndürürse, her posta kutusundan yalnızca 100 öğe önizlemede görüntü oladur, önizleme için yalnızca 400 öğe kullanılabilir.

- Posta kutusu öğeleri için önizleme yalnızca e-posta iletileri kullanılabilir. Görevler, takvim öğeleri ve kişiler gibi öğeler önizlemede görüntüz.

- Site öğeleri için, önizleme için yalnızca belgeler kullanılabilir. Klasörler, listeler veya liste ekleri gibi öğeler önizlemede görüntüz.

## <a name="file-types-supported-when-previewing-search-results"></a>Arama sonuçlarının önizlemesi görüntülenirken desteklenen dosya türleri

Desteklenen dosya türlerini önizleme bölmesinde görüntüleyebilirsiniz. Bir dosya türü desteklenmiyorsa, (Özgün öğeyi indir'e tıklayarak) dosyanın bir kopyasını yerel **bilgisayarınıza indirmeniz gerekir**. .aspx Web sayfalarında, sayfaya erişim izinlerine sahip olamayabilirsiniz, ancak sayfanın URL'si dahil edilir. Eksiz öğeler önizleme için kullanılamaz.

Aşağıdaki dosya türleri de kullanılabilir ve arama sonuçları bölmesinde önizlemede ekleyebilirsiniz.
  
- .txt, .html, .mhtml

- .eml

- .doc, .docx, .docm

- .pptm, .pptx

- .pdf

Ayrıca, aşağıdaki dosya kapsayıcı türleri de destek vardır. Dosyaların listesini önizleme bölmesindeki kapsayıcıda görüntüleyebilirsiniz.
  
- .zip

- .gzip