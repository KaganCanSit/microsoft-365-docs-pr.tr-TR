---
title: SharePoint Online ile nesne önbelleğini kullanma
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 4/20/2015
audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Ent_O365
- SPO_Content
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- SPO160
- MET150
ms.assetid: 38bc9c14-3826-449c-beb6-b1003bcbeaaf
description: Bu makalede, SharePoint Server 2013 şirket içi ve SharePoint Online'da nesne önbelleğini kullanma arasındaki fark açıklanmaktadır.
ms.openlocfilehash: db0a150927bc3a2078d4dc0ca7491471b7973f2d
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65077794"
---
# <a name="using-the-object-cache-with-sharepoint-online"></a>SharePoint Online ile nesne önbelleğini kullanma

Bu makalede, SharePoint Server 2013 şirket içi ve SharePoint Online'da nesne önbelleğini kullanma arasındaki fark açıklanmaktadır.
  
SharePoint Online dağıtımında nesne önbelleğine güvenmenin önemli bir olumsuz etkisi vardır. SharePoint Online'daki nesne önbelleğine bağımlılık, sayfanızın güvenilirliğini azaltır. 
  
## <a name="how-the-sharepoint-online-and-sharepoint-server-2013-object-cache-works"></a>SharePoint Online ve SharePoint Server 2013 nesne önbelleği nasıl çalışır?

SharePoint Server 2013 şirket içinde barındırıldığında, müşterinin nesne önbelleğini barındıran özel ön uç web sunucuları vardır. Bu, önbelleğin tek bir müşteriye ayrılmış olduğu ve yalnızca kullanılabilir ve nesne önbelleğine ayrılan bellek miktarıyla sınırlı olduğu anlamına gelir. Şirket içi senaryoda yalnızca bir müşteriye hizmet sunulduğundan, ön uç web sunucularında genellikle kullanıcılar aynı sitelere tekrar tekrar istekte bulunur. Bu, önbelleğin hızla dolduğunu ve kullanıcılarınızın düzenli olarak istediği liste sorgusu sonuçları ve SharePoint nesneleriyle dolu kaldığı anlamına gelir.
  
![Şirket içi ön uç web sunucularına trafiği ve yükü gösterir.](../media/a0d38b36-4909-4abb-8d4e-4930814bb3de.png)
  
Sonuç olarak, kullanıcı bir sayfayı ikinci kez ziyaret eder ve sayfa yükleme süresi iyileştirir. Aynı sayfanın en az dört yükünden sonra, sayfa tüm ön uç web sunucularında önbelleğe alınır.
  
Buna karşılık, SharePoint Online'da çok daha fazla sunucu ve çok daha fazla site vardır. Her kullanıcı, önbelleği doldurulmayan farklı bir ön uç web sunucusuna bağlanabilir. Ya da önbellek bir sunucu için doldurulabilir, ancak bu ön uç web sunucusunun sonraki kullanıcısı farklı bir siteden sayfa ister. Öte yandan, sonraki kullanıcı önceki ziyaretinde olduğu gibi aynı sayfayı istese bile, önbelleğinde bu sayfa olmayan farklı bir ön uç web sunucusuna yük dengelemesi yapılır. Bu son durumda önbelleğe alma işlemi kullanıcılara hiç yardımcı olmaz.
  
Aşağıdaki şekilde, her nokta kullanıcının istediği ve önbelleğe aldığı bir sayfayı temsil eder. Farklı renkler, SaaS altyapısını paylaşılan olarak kullanan farklı müşterileri temsil eder.
  
![SharePoint Online'da nesne önbelleğe alma sonuçlarını gösterir.](../media/25d04011-ef83-4cb7-9e04-a6ed490f63c3.png)
  
Diyagramda görebileceğiniz gibi, belirli bir kullanıcının sayfalarının önbelleğe alınmış sürümüyle bir sunucuya çarpma olasılığı düşüktür. Ayrıca, büyük aktarım hızı ve sunucuların birçok site arasında paylaşılması nedeniyle önbellek, önbelleğe alma için yalnızca çok fazla alan olduğundan uzun sürmez.
  
Tüm bu nedenlerden dolayı, kullanıcıların önbelleğe alınmış nesneler almasına güvenmek, SharePoint Online'da kaliteli bir kullanıcı deneyimi ve sayfa yükleme süreleri sağlamanın etkili bir yolu değildir.
  
## <a name="if-we-cant-rely-on-the-object-cache-to-improve-performance-in-sharepoint-online-what-do-we-use-instead"></a>SharePoint Online'da performansı artırmak için nesne önbelleğine güvenemezsek bunun yerine ne kullanırız?

SharePoint Online'da önbelleğe alma özelliğini kullanmamanız gerektiğinden, nesne önbelleğini kullanan SharePoint özelleştirmeleri için alternatif tasarım yaklaşımlarını değerlendirmeniz gerekir. Bu, kullanıcılar için iyi sonuçlar elde etmek için nesne önbelleğe almayı kullanmayan performans sorunlarına yönelik yaklaşımların kullanılması anlamına gelir. Bu, bu serideki diğer makalelerden bazılarında açıklanmıştır ve şunları içerir:
  
- [SharePoint Online için gezinti seçenekleri](navigation-options-for-sharepoint-online.md)
    
- [SharePoint Online'da küçültme ve paketleme](minification-and-bundling-in-sharepoint-online.md)
    
- [SharePoint Online ile Office 365 Content Delivery Network (CDN) kullanma](use-microsoft-365-cdn-with-spo.md)
    
- [SharePoint Online'da görüntülerin ve JavaScript'in yüklenmesini geciktirme](delay-loading-images-and-javascript-in-sharepoint-online.md)
    