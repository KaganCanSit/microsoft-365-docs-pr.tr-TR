---
title: Microsoft SharePoint Syntex belge kitaplıklarında meta verileri arama
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
description: SharePoint Syntex kullanarak SharePoint belge kitaplıklarındaki öğeleri bulmak için gelişmiş meta veri aramasını kullanmayı ve özel site sütunlarını aramayı öğrenin.
ms.openlocfilehash: 50b9ef7ff6fe7942266ec59f8d5ad81e0dfbecd4
ms.sourcegitcommit: 872ab0b6a225c20274916e07ed4cc4944be9509a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/25/2022
ms.locfileid: "65679581"
---
# <a name="search-for-metadata-in-document-libraries-in-microsoft-sharepoint-syntex"></a>Microsoft SharePoint Syntex belge kitaplıklarında meta verileri arama

SharePoint Syntex'daki gelişmiş meta veri arama özelliği, SharePoint belge kitaplıklarında belirli meta veri tabanlı sorgular gerçekleştirmenizi sağlar. Yalnızca anahtar sözcükleri aramak yerine belirli meta veri sütunu değerlerine göre daha hızlı ve daha hassas sorgular yapabilirsiniz.

Gelişmiş meta veri araması, dosyayı SharePoint belge kitaplığında bulmanıza yardımcı olmak için belgeyle ilişkilendirilmiş meta verileri kullanmanıza olanak tanır. Bu özellik, belgenin en son ne zaman değiştirildiği, dosyayla ilişkilendirilmiş belirli bir kişi veya belirli bir dosya türü gibi aramak istediğiniz belirli bir bilgi parçasına sahip olduğunuzda özellikle kullanışlıdır.

> [!NOTE]
> Bu özellik yalnızca SharePoint Syntex lisansına sahip kullanıcılar için kullanılabilir. 

## <a name="to-use-advanced-metadata-search"></a>Gelişmiş meta veri aramasını kullanmak için

1. SharePoint belge kitaplığındaki **Bu kitaplıkta ara** kutusunda meta veri arama simgesini (![Meta veri arama simgesinin](../media/content-understanding/metadata-search-icon.png) ekran görüntüsü) seçin.

    ![Meta veri arama simgesinin vurgulandığı arama kutusunu gösteren belge kitaplığı sayfasının ekran görüntüsü.](../media/content-understanding/metadata-search-box.png)

2. Meta veri arama bölmesinde, metni yazın veya arama alanlarından birinde veya daha fazlasında bulmak istediğiniz parametreyi seçin.

    ![Meta veri arama bölmesini gösteren belge kitaplığı sayfasının ekran görüntüsü.](../media/content-understanding/metadata-search-pane.png)

   Aşağıdaki meta veri arama alanları şu anda kullanılabilir. Gelecekte daha fazla alan eklenecektir.

   |Alan    |Bu alanı  |
   |---------|---------|
   |Anahtar kelime -ler |Meta verilerde veya belgenin tam metninde bir dize eşleşmesi arayın. |
   |Dosya adı     |Kitaplıktaki **Ad** sütununda arama.          |
   |Insanlar   |Kitaplıktaki herhangi bir sütundaki kişilerde eşleşme arayın.   |
   |Değiştirme tarihi |Kitaplıktaki **Değiştirilmiş** sütununda seçili tarih aralığına göre arama.         |
   |Dosya türü     |Seçili dosya türüne göre arama (örneğin, Word belgesi veya PDF).        |
   |İçerik türü  |Seçili içerik türüne göre arama. Bu seçenek yalnızca kitaplığa varsayılan olmayan bir içerik türü uygulanmışsa görünür. Varsayılan içerik türleri *belge* ve *klasör* türlerindendir.        |

3. Geçerli kitaplık görünümündeki özel site sütunlarını da arayabilirsiniz. Meta veri ayıklayıcıları bilgileri otomatik olarak site sütunlarına dolduracağından, kitaplıkta çalışan bir modeliniz varsa bu özellikle yararlıdır.  

    Aramanıza özel bir site sütunu eklemek için **Daha fazla seçenek ekle'yi** ve ardından site sütununun adını seçin.

    ![Meta veri arama bölmesindeki Daha fazla seçenek ekle menüsünün ekran görüntüsü.](../media/content-understanding/metadata-search-add-more-options.png)

4. **Ara'yı** seçin. Meta veri aramanızla eşleşen belgeler sonuçlar sayfasında gösterilir. 
