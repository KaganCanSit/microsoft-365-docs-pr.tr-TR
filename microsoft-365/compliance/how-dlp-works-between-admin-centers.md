---
title: DLP, Güvenlik & Uyumluluk Merkezi & Exchange yönetim merkezi ile nasıl çalışır?
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
ms.collection:
- M365-security-compliance
ms.localizationpriority: medium
search.appverid:
- MOE150
- MET150
ms.assetid: a7e4342a-a0a1-4b43-b166-3d7eecf5d2fd
description: Güvenlik & Uyumluluk Merkezi'ndeki DLP'nin Exchange yönetim merkezinde DLP ve posta akışı kuralları (aktarım kuralları) ile nasıl çalıştığını öğrenin.
ms.custom:
- seo-marvel-apr2020
- admindeeplinkEXCHANGE
ms.openlocfilehash: 0c5c6288ed9e3c1f536e7a221a270bad9663cf6b
ms.sourcegitcommit: 6a981ca15bac84adbbed67341c89235029aad476
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2022
ms.locfileid: "65753418"
---
# <a name="how-dlp-works-between-the-compliance-center-and-exchange-admin-center"></a>Uyumluluk Merkezi ile Exchange yönetim merkezi arasında DLP nasıl çalışır?

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Microsoft Purview'da iki farklı yönetim merkezinde bir veri kaybı önleme (DLP) ilkesi oluşturabilirsiniz:
  
- **Microsoft Purview uyumluluk portalı**, SharePoint, OneDrive, Exchange, Teams ve şimdi uç nokta cihazlarında içeriğin korunmasına yardımcı olmak için tek bir DLP ilkesi oluşturabilirsiniz. Burada bir DLP ilkesi oluşturmanızı öneririz. Daha fazla bilgi için bkz. [Veri Kaybı Önleme başvurusu](data-loss-prevention-policies.md).
    
- <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange yönetim merkezinde</a>, içeriği yalnızca Exchange korumaya yardımcı olacak bir DLP ilkesi oluşturabilirsiniz. Bu ilke Exchange posta akışı kurallarını (taşıma kuralları olarak da bilinir) kullanabilir, bu nedenle e-postayı işlemeye özgü daha fazla seçeneği vardır. Daha fazla bilgi için [Exchange yönetim merkezinde DLP](/exchange/security-and-compliance/data-loss-prevention/data-loss-prevention) bölümüne bakın.
    
Bu yönetim merkezlerinde oluşturulan DLP ilkeleri yan yana çalışır. Bu makalede nasıl yapıldığını açıklanmaktadır.
  
![Güvenlik ve Uyumluluk Merkezi ve Exchange yönetim merkezinde DLP sayfaları.](../media/d3eaa7e7-3b16-457b-bd9c-26707f7b584f.png)
  
## <a name="how-dlp-in-the-security--compliance-center-works-with-dlp-and-mail-flow-rules-in-the-exchange-admin-center"></a>Güvenlik & Uyumluluk Merkezi'ndeki DLP, Exchange yönetim merkezindeki DLP ve posta akışı kurallarıyla nasıl çalışır?

Güvenlik & Uyumluluk Merkezi'nde bir DLP ilkesi oluşturduktan sonra, ilke ilkeye dahil edilen tüm konumlara dağıtılır. İlke Exchange Online içeriyorsa, ilke orada eşitlenir ve <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange yönetim merkezinde</a> oluşturulan bir DLP ilkesiyle tam olarak aynı şekilde uygulanır. 
  
Exchange yönetim merkezinde DLP ilkeleri oluşturduysanız, bu ilkeler Güvenlik & Uyumluluk Merkezi'nde oluşturduğunuz tüm e-posta ilkeleriyle birlikte çalışmaya devam eder. Ancak Exchange yönetim merkezinde oluşturulan kuralların öncelikli olduğunu unutmayın. Tüm Exchange posta akışı kuralları önce işlenir ve ardından Güvenlik & Uyumluluk Merkezi'nden DLP kuralları işlenir.
  
Şu anlama gelir:
  
- Exchange posta akışı kuralları tarafından engellenen iletiler, Güvenlik & Uyumluluk Merkezi'nde oluşturulan DLP kuralları tarafından taranamaz.
- Exchange posta akışı kuralları tarafından karantinaya alınan iletiler veya DLP'ye başlamadan önce çalıştırılan diğer filtreler DLP tarafından taranmayacak. 
- Exchange posta akışı kuralı, bir iletiyi Güvenlik & Uyumluluk Merkezi'nde dış kullanıcılar ekleme gibi bir DLP ilkesiyle eşleşmesine neden olacak şekilde değiştirirse, DLP kuralları bunu algılar ve ilkeyi gerektiği gibi uygular.
    
Ayrıca, "işlemeyi durdur" eylemini kullanan Exchange posta akışı kurallarının Güvenlik & Uyumluluk Merkezi'nde DLP kurallarının işlenmesini etkilemediğini unutmayın; bunlar yine de işlenecektir.
  
## <a name="policy-tips-in-the-security--compliance-center-vs-the-exchange-admin-center"></a>Güvenlik & Uyumluluk Merkezi ile Exchange yönetim merkezinde ilke ipuçları

İlke ipuçları<a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">, Exchange yönetim merkezinde</a> oluşturulan DLP ilkeleri ve posta akışı kurallarıyla veya Güvenlik & Uyumluluk Merkezi'nde oluşturulan DLP ilkeleriyle çalışabilir, ancak ikisini birden çalışmaz. Bunun nedeni, bu ilkelerin farklı konumlarda depolanmasıdır, ancak ilke ipuçları yalnızca tek bir konumdan çizim yapabilir.
  
Exchange yönetim merkezinde ilke ipuçlarını yapılandırdıysanız, Güvenlik & Uyumluluk Merkezi'nde yapılandırdığınız ilke ipuçları, Exchange yönetim merkezindeki ipuçlarını kapatana kadar Web üzerinde Outlook ve Outlook 2013 ve sonraki sürümlerde kullanıcılara gösterilmez. Bu, güvenlik & Uyumluluk Merkezi'ne geçiş yapmayı seçene kadar geçerli Exchange posta akışı kurallarınızın çalışmaya devam etmesini sağlar.
  
>[!Note]
>İlke ipuçları yalnızca tek bir konumdan çizim yapabilir ancak hem Güvenlik & Uyumluluk Merkezi'nde hem de Exchange yönetim merkezinde DLP ilkelerini kullanıyor olsanız bile e-posta bildirimleri her zaman gönderilir.
