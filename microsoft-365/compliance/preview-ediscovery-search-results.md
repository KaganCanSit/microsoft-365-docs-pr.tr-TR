---
title: eBulma aramasının sonuçlarını önizleme
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
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
description: Microsoft Purview uyumluluk portalı İçerik araması veya eBulma (Standart) araması tarafından döndürülen sonuçların örneğini önizleme.
ms.openlocfilehash: f369148c6f898c4150d0c86f898640f71ab367a0
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66628605"
---
# <a name="preview-ediscovery-search-results"></a>eKeşif arama sonuçlarını önizleme

İçerik araması veya Microsoft Purview eKeşif (Standart) servis talebiyle ilişkilendirilmiş bir arama çalıştırdıktan sonra, arama tarafından döndürülen sonuçların bir örneğini önizleyebilirsiniz. Arama sorgusu tarafından döndürülen öğelerin önizlemesini görüntülemek, aramanın umduğun sonuçları döndüreceğini veya arama sorgusunu değiştirip aramayı yeniden çalıştırmanız gerekip gerekmediğini belirlemenize yardımcı olabilir.

Arama tarafından döndürülen sonuçların örneğini önizlemek için:

1. Microsoft Purview uyumluluk portalı İçerik arama sayfasına veya eBulma (Standart) servis talebine gidin.

2. Açılır sayfayı görüntülemek için arama'yı seçin.

3. Açılır sayfanın alt kısmında **Örneği gözden geçir'e** tıklayın.

   ![Sonuçları önizlemek için açılır sayfada Örneği gözden geçir'e tıklayın.](../media/PreviewSearchResults1.png)

   Arama sonuçlarının bir örneğini içeren bir sayfa görüntülenir.

4. Okuma bölmesinde içeriğini görüntülemek için bir öğe seçin.

   ![Okuma bölmesinde öğeleri önizleme.](../media/PreviewSearchResults2.png)

   Önceki ekran görüntüsünde, öğeleri önİzlerken arama sorgusundaki anahtar sözcüklerin vurgulandığına dikkat edin.

## <a name="how-the-search-result-samples-are-selected"></a>Arama sonucu örnekleri nasıl seçilir?

Rastgele seçilen en fazla 1.000 öğe önizleme için kullanılabilir. Rastgele seçilmeye ek olarak, önizleme için kullanılabilen öğeler de aşağıdaki ölçütleri karşılamalıdır:

- Tek bir içerik konumundan (posta kutusu veya site) en fazla 100 öğe önizlenebilir. Bu, önizleme için 1.000'den az öğenin kullanılabilir olabileceği anlamına gelir. Örneğin, dört posta kutusunda arama yaparsanız ve arama 1.500 tahmini öğe döndürürse, her posta kutusundan yalnızca 100 öğe önizlenebileceği için önizleme için yalnızca 400 öğe kullanılabilir.

- Posta kutusu öğeleri için yalnızca e-posta iletileri önizleme için kullanılabilir. Görevler, takvim öğeleri ve kişiler gibi öğeler önizlenemez.

- Site öğeleri için yalnızca belgeler önizleme için kullanılabilir. Klasörler, listeler veya liste ekleri gibi öğeler önizlenemez.

## <a name="file-types-supported-when-previewing-search-results"></a>Arama sonuçlarının önizlemesi sırasında desteklenen dosya türleri

Desteklenen dosya türlerini önizleme bölmesinden önizleyebilirsiniz. Bir dosya türü desteklenmiyorsa, dosyanın bir kopyasını yerel bilgisayarınıza indirmeniz gerekir ( **Özgün öğeyi indir'e** tıklayarak). .aspx Web sayfaları için sayfanın URL'si eklenir, ancak sayfaya erişim izniniz olmayabilir. Dizine alınmamış öğeler önizleme için kullanılamaz.

Aşağıdaki dosya türleri desteklenir ve arama sonuçları bölmesinde önizlenebilir.
  
- .txt, .html, .mhtml

- Eml

- .doc, .docx, .docm

- .pptm, .pptx

- .pdf

Ayrıca, aşağıdaki dosya kapsayıcı türleri desteklenir. Kapsayıcıdaki dosyaların listesini önizleme bölmesinde görüntüleyebilirsiniz.
  
- .zip

- .gzip