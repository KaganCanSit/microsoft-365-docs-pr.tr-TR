---
title: eBulma arama sonuçlarını dışarı aktarıyorken PST dosyalarının boyutunu değiştirme
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: 10/12/2018
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MOE150
- MET150
ms.assetid: 04e9de2d-765b-457b-a98a-d0f60bfb13f2
description: eBulma arama sonuçlarını dışarı aktararak bilgisayarınıza indirilen PST dosyalarının varsayılan boyutunu değiştirebilirsiniz.
ms.openlocfilehash: b0376a423827df855af83375ddfae0e9803fd933
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62983607"
---
# <a name="change-the-size-of-pst-files-when-exporting-ediscovery-search-results"></a>eBulma arama sonuçlarını dışarı aktarıyorken PST dosyalarının boyutunu değiştirme

Farklı Microsoft eBulma araçlarından gelen eBulma aramalarının e-posta sonuçlarını dışarı aktaracak şekilde eBulma Dışarı Aktarma aracını kullanırsanız, dışarı aktarılana kadar bir PST dosyasının varsayılan boyutu 10 GB'dir. Bu varsayılan boyutu değiştirmek için, arama sonuçlarını dışarı Windows bilgisayarda Windows Defteri'ni düzenleyebilirsiniz. Bunu nedeni, PST dosyasının DVD, CD veya USB sürücüsü gibi çıkarılabilir bir medyaya sığmalarını sağlar. 
  
> [!NOTE]
> eBulma Dışarı Aktarma aracı, çalışma sayfalarındaki İçerik arama aracı kullanılırken arama sonuçlarını dışarı Microsoft 365 uyumluluk merkezi.
  
## <a name="create-a-registry-setting-to-change-the-size-of-pst-files-when-you-export-ediscovery-search-results"></a>eBulma arama sonuçlarını dışarı aktararak PST dosyalarının boyutunu değiştirmek için kayıt defteri ayarı oluşturma

eBulma aramalarının sonuçlarını dışarı aktarmada kullanabileceğiniz bilgisayarda aşağıdaki yordamı gerçekleştirin.
  
1. Açıksa eBulma Dışarı Aktarma aracını kapatın. 
    
2. .reg dosya adı son ekını kullanarak aşağıdaki metni bir Window kayıt defteri dosyasına kaydedin; örneğin, PstExportSize.reg. 
    
    ```text
    Windows Registry Editor Version 5.00
    [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Exchange\Client\eDiscovery\ExportTool]
    "PstSizeLimitInBytes"="1073741824"
    ```

    Yukarıdaki örnekte değer  `PstSizeLimitInBytes` 1.073.741.824 bayt veya yaklaşık 1 GB olarak ayarlanmıştır. Burada, ayar için bazı başka örnek değerler ve  `PstSizeLimitInBytes` hazır bulundurabilirsiniz. 
    
    |**GB (yaklaşık) olarak boyut**|**Bayt cinsinden boyut**|
    |:-----|:-----|
    |0,7 GB (700 MB)  <br/> |751619277  <br/> |
    |2 GB  <br/> |2147483648  <br/> |
    |4 GB  <br/> |4294967296  <br/> |
    |8 GB  <br/> |8589934592  <br/> |
   
3. Arama sonuçlarını `PstSizeLimitInBytes` dışarı aktarın ve sonra da dosyayı kaydetmek için, değeri PST dosyasının istenen boyut üst boyutuna ayarlayın. 
    
4. Windows Gezgini'nde, önceki adımlarda oluşturduğunuz .reg dosyasına tıklayın veya çift tıklayın.
    
5. Kullanıcı Erişimi Denetimi penceresinde, Kayıt Defteri **Düzenleyicisi'nin değişikliği** yapmalarına izin vermeleri için Evet'e tıklayın. 
    
6. Devam etmek istendiğinde Evet'e **tıklayın**.
    
    Kayıt Defteri Düzenleyicisi, ayarın kayıt defterine başarıyla eklenmiştir iletisi görüntüler.
    
7. Kayıt defteri ayarının değerini değiştirmek için 3 - 6. adımları yinelersiniz  `PstSizeLimitInBytes` . 
  
## <a name="frequently-asked-questions-about-changing-the-default-size-of-pst-files-when-you-export-ediscovery-search-results"></a>eBulma arama sonuçlarını dışarı aktararak PST dosyalarının varsayılan boyutunu değiştirme hakkında sık sorulan sorular

 **Varsayılan boyut neden 10 GB?**
  
Varsayılan boyut olarak 10 GB müşteri geri bildirimleri temel aldı; 10 GB, tek bir PST dosyasındaki en iyi içerik miktarıyla en düşük dosya bozulma ihtimali arasında iyi bir bakiyedir.
  
 **PST dosyalarının varsayılan boyutunu artırmalı mı yoksa azaltmalı musunuz?**
  
Müşteriler, arama sonuçlarının fiziksel olarak kendi kuruluşlarında başka konumlara gönderılabilen çıkarılabilir medyaya uyması için boyut sınırını azaltma eğilimindedir. 10 GB'den büyük PST dosyalarında bozulma sorunları olabileceğinden varsayılan boyutu artırmamanız önerilir.
  
 **Bunu hangi bilgisayarda yapmak istiyorum?**
  
eBulma Dışarı Aktarma aracını çalıştırdınız herhangi bir yerel bilgisayarda kayıt defteri ayarını değiştirebilirsiniz.
  
 **Bu ayarı değiştirdikten sonra bilgisayarı yeniden başlatmam gerekir mi?**
  
Hayır, bilgisayarı yeniden başlatmanız zorunda değil. Ancak, eBulma Dışarı Aktarma aracı çalışıyorsa, bu ayarı değiştirdikten sonra aracı kapatıp yeniden başlatmanız gerekir.
  
 **Var olan bir kayıt defteri anahtarı düzen mi yoksa yeni bir anahtar mı oluşturulur?**
  
Bu yordamda oluşturduğunuz .reg dosyasını ilk kez çalıştıracak yeni bir kayıt defteri anahtarı oluşturulur. Daha sonra, .reg düzenleme dosyasını her değiştirseniz ve yeniden çalıştırsanız bu ayar düzenlenmiş olur.
