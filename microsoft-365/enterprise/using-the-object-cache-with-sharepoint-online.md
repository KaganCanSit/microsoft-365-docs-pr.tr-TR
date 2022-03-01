---
title: SharePoint Online ile nesne SharePoint kullanma
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: Bu makalede, şirket içi SharePoint Server 2013'te nesne önbelleğini kullanma ile SharePoint açıklanmıştır.
ms.openlocfilehash: c763ebb1603ade7fdc98f7728fb03697c5e7425c
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2022
ms.locfileid: "63015179"
---
# <a name="using-the-object-cache-with-sharepoint-online"></a>SharePoint Online ile nesne SharePoint kullanma

Bu makalede, şirket içi SharePoint Server 2013'te nesne önbelleğini kullanma ile SharePoint açıklanmıştır.
  
SharePoint Online dağıtımında nesne önbelleğine güvenmek önemli ölçüde olumsuz etkiyi gösterir. SharePoint Online'da nesne önbelleğine herhangi bir bağımlılık, sayfanıza olan güvenilirliği azaltır. 
  
## <a name="how-the-sharepoint-online-and-sharepoint-server-2013-object-cache-works"></a>SharePoint Online ve SharePoint Server 2013 nesne önbelleği nasıl çalışır?

SharePoint Server 2013 şirket içinde barındırıldı olduğunda, müşterinin nesne önbelleğini barındıran özel ön uç web sunucuları vardır. Bu, önbelleğin tek bir müşteriye özel olduğu ve nesne önbelleği için kullanılabilir ve ayrılmış bellek miktarıyla sınırlı olduğu anlamına gelir. Şirket içi senaryosunda tek bir müşteriye hizmet verili olduğundan, normalde ön uç web sunucularında aynı sitelere tekrar tekrar istekte bulunan kullanıcılar olur. Bu, önbelleğin hızla dolu olması ve liste sorgu sonuçlarıyla dolu kalması ve kullanıcı SharePoint düzenli olarak istekte SharePoint nesne seçmesi anlamına gelir.
  
![Trafiği ve şirket içi ön uç web sunucularına yüklerini gösterir.](../media/a0d38b36-4909-4abb-8d4e-4930814bb3de.png)
  
Sonuç olarak, kullanıcı bir sayfayı ikinci kez ziyaret ettiylerinde, sayfa yükleme süresi geliştirildi. Aynı sayfanın en az dört kez yüklerinin ardından, sayfa tüm ön uç web sunucularında önbelleğe alınmış olur.
  
Buna karşılık, SharePoint Online'da birçok başka sunucu ve aynı zamanda birçok site daha vardır. Her kullanıcı, önbelleği doldurul olmayan farklı bir ön uç web sunucusuna bağlanabilirsiniz. Belki de, bir sunucu için önbellek doldurulmasa da, bu ön uç web sunucusunun bir sonraki kullanıcısı farklı bir siteden bir sayfa ister. Öte yandan, bir sonraki kullanıcı önceki ziyaretinde istekte bulunsa bile, önbelleğinde bu sayfayı olmayan farklı bir ön uç web sunucusuyla yük dengelemesi olur. Bu son durumda, önbelleğe alma işleminin kullanıcılara hiçbir yardımı olmaz.
  
Aşağıdaki şekilde, her nokta kullanıcının istekte bulunduğu bir sayfayı ve bunun önbelleğe alınmış yeri temsil eder. Farklı renkler SaaS altyapısını paylaşarak kullanan farklı müşterileri temsil eder.
  
![SharePoint Online'da nesne önbelleğinin sonuçlarını gösterir.](../media/25d04011-ef83-4cb7-9e04-a6ed490f63c3.png)
  
Diyagramdan da gördüğünüz gibi, herhangi bir kullanıcının sayfayı önbelleğine alınmış sürümüyle sunucuya basma şansı düşük olabilir. Aynı zamanda, işlem hacminin çok büyük olması ve sunucuların birçok site arasında paylaşılıyor olması nedeniyle, önbellek için kullanılabilir yalnızca çok fazla alan olduğu için önbellek uzun süre devam etmemektedir.
  
Tüm bu nedenlerden dolayı, kullanıcıların önbelleğe alınmış nesneleri almalarına güvenmek, SharePoint Online'da kaliteli bir kullanıcı deneyimi ve sayfa yükleme süreleri sağlamak için etkili bir yol değildir.
  
## <a name="if-we-cant-rely-on-the-object-cache-to-improve-performance-in-sharepoint-online-what-do-we-use-instead"></a>SharePoint Online'da performansı geliştirmek için nesne önbelleğine güvene SharePoint, bunun yerine ne kullanabiliriz?

SharePoint Online'da önbelleğe güvenme olmamanız gerektiği için, nesne önbelleği kullanan özelleştirmeler için SharePoint tasarım yaklaşımlarını değerlendirin. Bu da, kullanıcılara iyi sonuçlar elde etmek için performans sorunlarında nesne önbelleğine dayandırmayacak yaklaşımları kullanmak anlamına gelir. Bu makale, bu serinin diğer bazı makalesinde açıklanmıştır:
  
- [SharePoint Online için gezinti seçenekleri](navigation-options-for-sharepoint-online.md)
    
- [SharePoint Online'da SharePoint ve büyütme](minification-and-bundling-in-sharepoint-online.md)
    
- [CDN Online ile Office 365 Content Delivery Network (CDN) SharePoint kullanma](use-microsoft-365-cdn-with-spo.md)
    
- [SharePoint Online'da resimleri ve JavaScript'i SharePoint geciktirme](delay-loading-images-and-javascript-in-sharepoint-online.md)
    