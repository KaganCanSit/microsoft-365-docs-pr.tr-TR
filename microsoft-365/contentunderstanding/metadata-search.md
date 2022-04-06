---
title: Microsoft SharePoint Syntex'ta belge kitaplıklarında meta veri SharePoint Syntex
ms.author: chucked
author: chuckedmonson
manager: pamgreen
ms.reviewer: kkameth
audience: admin
ms.topic: article
ms.prod: microsoft-365-enterprise
search.appverid: ''
ms.collection:
- enabler-strategic
- m365initiative-syntex
ms.localizationpriority: high
description: Gelişmiş meta veri aramanın nasıl kullanılal ve özel site sütunlarını ara kullanarak belge kitaplıklarında öğeleri SharePoint için özel site SharePoint Syntex.
ms.openlocfilehash: f010c6944fdcb05fcfe2c254274249b2dcabe99e
ms.sourcegitcommit: 33bc25167812b31c51cf096c728e3a5854e94f1c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/01/2022
ms.locfileid: "64595373"
---
# <a name="search-for-metadata-in-document-libraries-in-microsoft-sharepoint-syntex"></a>Microsoft SharePoint Syntex'ta belge kitaplıklarında meta veri SharePoint Syntex

Gelişmiş meta veri arama özelliği SharePoint Syntex belge kitaplıklarında belirli meta veri tabanlı SharePoint gerçekleştirmenizi sağlar. Yalnızca anahtar sözcükleri aramak yerine, belirli meta veri sütun değerlerine dayalı olarak daha hızlı ve daha hassas sorgular yapabilirsiniz.

Gelişmiş meta veri araması, belge kitaplığında yer alan dosyayı bulmak için belgeyle ilişkilendirilmiş meta SharePoint olanak sağlar. Bu özellik özellikle, belge en son ne zaman değiştirildiğinde, dosyayla ilişkilendirilmiş belirli bir kişi veya belirli bir dosya türü gibi aramak istediğiniz belirli bir bilginiz olduğunda kullanışlıdır.

> [!NOTE]
> Bu özellik yalnızca yazılım lisansı olan kullanıcılar SharePoint Syntex. 

## <a name="to-use-advanced-metadata-search"></a>Gelişmiş meta veri aramalarını kullanmak için

1. Bir SharePoint kitaplığından Bu kitaplıkta ara kutusunda, meta  veri arama simgesini seçin (![meta veri arama simgesinin ekran görüntüsü)..](../media/content-understanding/metadata-search-icon.png)

    ![Meta veri arama simgesinin vurgulu olduğu arama kutusunu gösteren belge kitaplığı sayfasının ekran görüntüsü.](../media/content-understanding/metadata-search-box.png)

2. Meta veri arama bölmesinde, bir veya birden çok arama alanında bulmak istediğiniz metni yazın veya parametreyi seçin.

    ![Meta veri arama bölmesini gösteren belge kitaplığı sayfasının ekran görüntüsü.](../media/content-understanding/metadata-search-pane.png)

   Şu anda aşağıdaki meta veri arama alanları kullanılabilir. Gelecekte daha fazla alan eklenecektir.

   |Alan    |Bu alanı kullanarak  |
   |---------|---------|
   |Anahtar Sözcükler |Meta verilerde veya belgenin tam metninde dize eşleşmesi araması. |
   |Dosya adı     |Kitaplıkta **Ad** sütununda arama.          |
   |Kişiler   |Kitaplıkta herhangi bir sütundaki kişilerde eşleşme arama.   |
   |Değiştirilme tarihi |Kitaplıkta Değiştirme Tarihi sütununda seçilen **tarih** aralığına göre arama.         |
   |Dosya türü     |Seçili dosya türüne (örneğin, Word belgesi veya PDF) göre arama.        |
   |İçerik türü  |Seçili içerik türüne göre arama. Bu seçenek yalnızca kitaplıda varsayılan olmayan içerik türü uygulanmışsa görüntülenir. Varsayılan içerik türleri belge *ve klasördür*.        |

3. Geçerli kitaplık görünümündeki özel site sütunlarını da arayabilirsiniz. Bu özellikle, kitaplık üzerinde çalışan bir modeliniz varsa kullanışlıdır çünkü meta veri ayıklar bilgileri otomatik olarak site sütunlarına oluşturur.  

    Aramanıza özel bir site sütunu eklemek için **Daha fazla seçenek** ekle'yi ve sonra site sütununu seçin.

    ![Meta veri arama bölmesindeki Daha fazla seçenek ekle menüsünün ekran görüntüsü.](../media/content-understanding/metadata-search-add-more-options.png)

    > [!NOTE]
    > Şu anda, yönetilen meta veri alanları veya çok satırlı metin alanları ekleme özelliği kullanılamaz. 

4. **Ara'ya seçin**. Meta veri aramanıza uygun belgeler, sonuçlar sayfasında gösterilir. 
