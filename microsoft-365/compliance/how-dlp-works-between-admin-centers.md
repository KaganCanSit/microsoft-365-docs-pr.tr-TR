---
title: DLP, Güvenlik ve Uyumluluk & yönetim & Exchange nasıl çalışır?
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
description: Güvenlik ve Uyumluluk Merkezi'& DLP'nin, genel yönetim merkezinde DLP ve posta akış kuralları (aktarım kuralları) ile Exchange öğrenin.
ms.custom:
- seo-marvel-apr2020
- admindeeplinkEXCHANGE
ms.openlocfilehash: 90706b3dad55ff84d274656673f9a60dbd71e35f
ms.sourcegitcommit: b1066b2a798568afdea9c09401d52fa38fe93546
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/13/2021
ms.locfileid: "63018817"
---
# <a name="how-dlp-works-between-the-microsoft-365-compliance-center-and-exchange-admin-center"></a>DLP, Uyumluluk Merkezi ile Microsoft 365 merkezi arasında Exchange çalışır

Genel Microsoft 365, iki farklı yönetim merkezinde veri kaybı önleme (DLP) ilkesi oluşturabilirsiniz:
  
- Uyumluluk **Microsoft 365 Merkezi'nde**, SharePoint, OneDrive, Exchange, Teams ve şimdi Uç Nokta Cihazları'nın içeriğinin korunmasına yardımcı olmak için tek bir DLP ilkesi oluşturabilirsiniz. Burada bir DLP ilkesi oluşturmanızı öneririz. Daha fazla bilgi için bkz. [Veri Kaybı Önleme başvurusu](data-loss-prevention-policies.md).
    
- Exchange <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">yönetim merkezinde</a>, yalnızca iş yerizken içeriğin korunmasına yardımcı olmak için bir DLP Exchange. Bu ilke, posta Exchange kuralları (aktarım kuralları olarak da bilinir) kullanabilir ve dolayısıyla e-postayı işlemeye özgü daha fazla seçeneği vardır. Daha fazla bilgi için bkz. [Exchange merkezinde DLP](/exchange/security-and-compliance/data-loss-prevention/data-loss-prevention).
    
Bu yönetim merkezlerinde oluşturulan DLP yasaları yan yana çalışır; bu konuda nasıl olduğu açıklanmıştır.
  
![Güvenlik ve Uyumluluk Merkezi'nde ve Yönetim Merkezi'Exchange DLP sayfaları.](../media/d3eaa7e7-3b16-457b-bd9c-26707f7b584f.png)
  
## <a name="how-dlp-in-the-security--compliance-center-works-with-dlp-and-mail-flow-rules-in-the-exchange-admin-center"></a>Güvenlik ve Uyumluluk Merkezi'& DLP'nin genel yönetim merkezinde DLP ve posta Exchange çalışma

Güvenlik ve Uyumluluk Merkezi'nde bir DLP ilkesi & sonra, ilke ilkeye dahil olan tüm konumlara dağıtılır. İlke güvenlik Exchange Online, orada eşitler ve tam olarak aynı şekilde, yönetim merkezinde oluşturulan DLP <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">ilkesiyle Exchange uygulanır</a>. 
  
DLP ilkelerini Exchange yönetim merkezinde oluşturduysanız, bu ilkeler Güvenlik ve Uyumluluk Merkezi'nde oluşturduğunuz e-postayla ilgili tüm ilkelerle & çalışmaya devam eder. Ancak yönetim merkezinde oluşturulan kuralların Exchange olduğunu unutmayın. Tüm Exchange posta akışı kuralları işlenir ve ardından Güvenlik ve Uyumluluk Merkezi'& DLP kuralları işlenir.
  
Bu, şu anlama gelir:
  
- Posta akış kuralları tarafından Exchange iletiler Güvenlik ve Uyumluluk Merkezi'nde oluşturulmuş DLP kuralları tarafından & değil.

- Posta akış kuralları veya Exchange filtreler tarafından karantinaya alınan iletiler DLP'den önce çalıştırıldı ve DLP tarafından taranmayacak.
    
- Exchange posta akışı kuralı bir iletiyi, dış kullanıcıları ekleme gibi Güvenlik & Uyumluluk Merkezi'nde DLP ilkesiyle eşleşmesine neden olacak şekilde değiştiren bir ileti varsa, DLP kuralları bunu algılar ve ilkeyi gereken şekilde zorlar.
    
Ayrıca Exchange "işlenmesini durdur" eylemsini kullanan posta akışı kurallarının, Güvenlik ve Uyumluluk Merkezi'nde DLP kurallarının işlenmesini etkilemeyeceğini& yine de işleneceklerini unutmayın.
  
## <a name="policy-tips-in-the-security--compliance-center-vs-the-exchange-admin-center"></a>Güvenlik ve Uyumluluk Merkezi& ilke ipuçları ile Exchange merkezi

İlke ipuçları, Exchange yönetim merkezinde oluşturulmuş DLP ilkeleri ve posta akışı kurallarıyla <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank"></a>ya da Güvenlik ve Uyumluluk Merkezi'nde oluşturulmuş DLP ilkeleriyle & birlikte çalışabilirsiniz. Çünkü, bu ilkeler farklı konumlarda depolanır, ancak ilke ipuçları yalnızca tek bir konumdan çizebilirsiniz.
  
Exchange yönetim merkezinde ilke ipuçlarını yapılandırdısanız, Exchange yönetim merkezinde ipuçlarını kapatana kadar Güvenlik & Uyumluluk Merkezi'nde yapılandırılan tüm ilke ipuçları Web üzerinde Outlook ve Outlook 201 Exchange 3 ve sonraki sayfalarındaki kullanıcılara görünmez. Bu, siz Güvenlik Exchange Uyumluluk Merkezi'ne geçmeyi seçene kadar geçerli posta akışı kuralları & sağlar.
  
İlke ipuçlarının yalnızca tek bir konumdan çizilmesine rağmen, hem Güvenlik & hem de Uyumluluk Merkezi'nde hem de Exchange yönetim merkezinde DLP ilkeleri kullanıyorsanız bile, e-posta bildirimlerinin her zaman gönderildiğini unutmayın.
