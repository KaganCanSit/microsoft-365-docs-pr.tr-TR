---
title: Varsayılan DLP ilkesini kullanmaya başlama
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MOE150
- MET150
ms.assetid: e0ada764-6422-4b44-9472-513bed04837b
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: Kuruluşunuzun varsayılan veri kaybı önleme (DLP) ilkesini iyileştirmek için raporu kullanmayı öğrenin.
ms.openlocfilehash: d47568f009745edaa8205ce65b4de9b481f58139
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66641504"
---
# <a name="get-started-with-the-default-dlp-policy"></a>Varsayılan DLP ilkesini kullanmaya başlama

İlk Microsoft Purview Veri Kaybı Önleme (DLP) ilkenizi oluşturmadan önce, DLP hassas bilgilerinizin varsayılan ilkeyle korunmasına yardımcı olur. Bu varsayılan ilke ve önerisi (aşağıda gösterilmiştir) kuruluşunuzun dışındaki biriyle e-posta veya kredi kartı numarası içeren belgeler paylaşıldığında sizi bilgilendirerek hassas içeriğinizin güvenliğini sağlamaya yardımcı olur. Bu öneriyi Microsoft Purview uyumluluk portalı **Giriş** sayfasında görürsünüz. 
  
Bu pencere öğesini kullanarak ne zaman ve ne kadar hassas bilginin paylaşıldığını hızlı bir şekilde görüntüleyebilir ve ardından varsayılan DLP ilkesini yalnızca bir veya iki tıklamayla daraltabilirsiniz. Ayrıca, varsayılan DLP ilkesini istediğiniz zaman tamamen özelleştirilebilir olduğundan düzenleyebilirsiniz. Öneriyi ilk başta görmüyorsanız, **Sizin için önerilen** bölümünün altındaki **+Daha Fazla'ya** tıklamayı deneyin. 
  
![Paylaşılan içeriği daha fazla koru adlı pencere öğesi.](../media/2bae6dbc-cc92-4f35-b54c-c36e60226b5b.png)
  
## <a name="view-the-report-and-refine-the-default-dlp-policy"></a>Raporu görüntüleme ve varsayılan DLP ilkesini iyileştirme

Pencere öğesi, kullanıcıların hassas bilgileri kuruluşunuzun dışındaki kişilerle paylaştığını gösterdiğinde alt kısımdaki **DLP ilkesini iyileştir'i** seçin. 
  
Ayrıntılı rapor, son 30 gün içinde kredi kartı numaralarını içeren içeriğin ne zaman ve ne kadar paylaşıldığını gösterir. Kural eşleşmelerinin pencere öğesinde gösterilmesinin 48 saat kadar sürebileceğini unutmayın.
  
Hassas bilgilerin korunmasına yardımcı olmak için varsayılan DLP ilkesi:
  
- Exchange, SharePoint ve OneDrive'da en az bir kredi kartı numarası içeren içeriğin kuruluşunuzun dışındaki kişilerle paylaşıldığını algılar.
    
- İlke ipucunu gösterir ve bu hassas bilgileri kuruluşunuz dışındaki kişilerle paylaşmaya çalışan kullanıcılara bir e-posta bildirimi gönderir. Bu seçenekler hakkında daha fazla bilgi için bkz. [DLP ilkeleri için e-posta bildirimleri gönderme ve ilke ipuçlarını gösterme](use-notifications-and-policy-tips.md).
    
- İçeriği kuruluşunuzun dışındaki kişilerle paylaşan kişiler ve ne zaman yaptıkları gibi öğeleri izleyebilebilmeniz için ayrıntılı etkinlik raporları oluşturur. Bu bilgileri görmek için [DLP raporlarını](view-the-dlp-reports.md) ve [denetim günlüğü verilerini](search-the-audit-log-in-security-and-compliance.md) **(etkinlik****DLP'sini**)  =  kullanabilirsiniz.
    
Varsayılan DLP ilkesini hızlı bir şekilde daraltmak için bu ilkeye sahip olmasını seçebilirsiniz:
  
- Kullanıcılar bu hassas bilgileri kuruluşunuzun dışındaki kişilerle paylaştığında size bir olay raporu e-postası gönderir.
    
- E-posta olayı raporuna başka kullanıcılar ekleyin.
    
- Hassas bilgileri içeren içeriğe erişimi engelleyin, ancak kullanıcının gerektiğinde geçersiz kılıp paylaşmasına veya göndermesine izin verin.
    
Olay raporları veya erişimi kısıtlama hakkında daha fazla bilgi için bkz. [Veri kaybı önleme başvurusu](data-loss-prevention-policies.md).
  
Bu seçenekleri daha sonra değiştirmek isterseniz, varsayılan DLP ilkesini istediğiniz zaman düzenleyebilirsiniz. Sonraki bölüme bakın.
  
![Paylaşılan içeriği daha fazla koru adlı pencere öğesi ayarları.](../media/dad30a84-2715-4c0a-a5c5-44d85492363e.png)
  
## <a name="edit-the-default-dlp-policy"></a>Varsayılan DLP ilkesini düzenleme

Bu ilke **Varsayılan DLP ilkesi** olarak adlandırılır ve Microsoft Purview uyumluluk portalı **İlke** sayfasındaki **Veri kaybı önleme** altında görünür. 
  
Bu ilke, sıfırdan oluşturduğunuz tüm DLP ilkeleriyle aynı şekilde tamamen özelleştirilebilir. Ayrıca, kullanıcılarınızın artık ilke ipuçlarını veya e-posta bildirimlerini almaması için ilkeyi kapatabilir veya silebilirsiniz.
  
![Varsayılan DLP ilkesi adlı DLP ilkesi.](../media/260731e8-4d57-4c98-abec-07b052ec48d5.png)
  
## <a name="when-the-widget-does-and-does-not-appear"></a>Pencere öğesi göründüğünde ve görünmediğinde

**Paylaşılan içeriği daha fazla koru** adlı pencere öğesi, Microsoft Purview uyumluluk portalı **Giriş** sayfasının **Sizin için önerilir** bölümünde görünür. 
  
Bu pencere öğesi yalnızca aşağıdaki durumlarda görünür:
  
- Microsoft Purview uyumluluk portalı veya Exchange yönetim merkezinde veri kaybı önleme ilkesi yoktur. Bu pencere öğesi DLP'yi kullanmaya başlamanıza yardımcı olmak için tasarlanmıştır, bu nedenle DLP ilkeleriniz varsa görüntülenmez.
    
- Son 30 gün içinde en az bir kredi kartı içeren içerik kuruluşunuzun dışındaki biriyle paylaşılmıştır.
    
Kural eşleşmelerinin pencere öğesinin kullanımına sunulmasının 48 saat kadar sürebileceğini unutmayın. Bu nedenle dışarıdan paylaşılan hassas bilgiler algılandıktan sonra önerinin görünmesi iki güne kadar sürebilir.
  
Son olarak, varsayılan DLP ilkesini daraltmak için pencere öğesini kullandıktan sonra pencere öğesi **Giriş** sayfasından kaybolur. 
  

