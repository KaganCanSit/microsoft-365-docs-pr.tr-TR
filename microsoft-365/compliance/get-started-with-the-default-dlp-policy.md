---
title: Varsayılan DLP ilkesiyle çalışmaya başlama
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
description: Rapor kullanarak, kurumnizin varsayılan veri kaybı önleme (DLP) politikasını nasıl geliştirebilirsiniz?
ms.openlocfilehash: 0e63648f78fd5adf2b0a354fa1a26abae4561ba8
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62988100"
---
# <a name="get-started-with-the-default-dlp-policy"></a>Varsayılan DLP ilkesiyle çalışmaya başlama

İlk veri kaybı önleme (DLP) ilkenizi oluşturmadan önce, DLP hassas verilerinizi varsayılan bir ilkeyle korumaya yardımcı olur. Bu varsayılan ilke ve önerisi (aşağıda gösterilen) e-posta veya kredi kartı numarası içeren belgelerin kuruluş dışındaki biriyle paylaşılıyor olması konusunda sizi bilgilendirerek hassas içeriğinizin güvenliğini sağlar. Bu öneriyi Güvenlik Uyumluluk **Merkezi'nin** Giriş sayfasında &amp; görebilirsiniz. 
  
Ne zaman ve ne kadar hassas bilgi paylaşıldı diye hızlıca görmek ve ardından bir veya iki tıklamayla varsayılan DLP ilkesinde geliştirme yapmak için bu widget'ı kullanabilirsiniz. Ayrıca, tümüyle özelleştirilebilir olduğundan, varsayılan DLP ilkesini istediğiniz zaman düzenleyebilirsiniz. İlk başta öneriyi görmüyorsanız Sizin için önerilenler bölümünün **altındaki +Diğer'e** **tıklamayı deneyin** . 
  
![Paylaşılan içeriği daha fazla koruma adlı widget.](../media/2bae6dbc-cc92-4f35-b54c-c36e60226b5b.png)
  
## <a name="view-the-report-and-refine-the-default-dlp-policy"></a>Raporu görüntüleme ve varsayılan DLP İlkesini geliştirme

Widget size kullanıcıların hassas bilgileri kuruluş dışındaki kullanıcılarla paylaştığını gösterirken, altta **DLP İlkesini geliştir'i** seçin. 
  
Ayrıntılı rapor, son 30 gün içinde kredi kartı numaraları içeren içeriğin ne zaman ve ne kadarlık bir şekilde paylaşılıyor olduğunu gösterir. Kural eşleşmeleri widget'sinde 48 saate kadar sürebilir.
  
Hassas bilgilerin korunmasına yardımcı olmak için varsayılan DLP ilkesi:
  
- En az bir kredi Exchange SharePoint kredi kartı numarası içeren OneDrive, telefon numarası ve faturalarında yer alan içeriğin kuruluş dışındakilerle paylaşılıyor olduğunu algılar.
    
- Bir ilke ipucu gösterir ve bu hassas bilgileri kuruluş dışındaki kullanıcılarla paylaşmayı denen kullanıcılara bir e-posta bildirimi gönderir. Bu seçenekler hakkında daha fazla bilgi için bkz. [E-posta bildirimleri gönderme ve DLP ilkeleriyle ilgili ilke ipuçlarını gösterme](use-notifications-and-policy-tips.md).
    
- Ayrıntılı etkinlik raporları üretir, böylece içeriğin kim tarafından ve ne zaman kuruluş dışındakilerle paylaşılıyor olduğu gibi etkinlikleri izleyebilirsiniz. Bu bilgileri görmek [için DLP raporlarını](view-the-dlp-reports.md) [ve denetim günlüğü](search-the-audit-log-in-security-and-compliance.md) verilerini (**burada ActivityDLP** = ) kullanabilirsiniz.
    
Varsayılan DLP ilkesini hızla geliştirmek için, ilkenin sahip olacağını seçebilirsiniz:
  
- Kullanıcılar bu hassas bilgileri kuruluş dışındaki kullanıcılarla paylaştığında, size bir olay raporu e-postası gönderin.
    
- E-posta olayı raporuna başka kullanıcılar ekleyin.
    
- Hassas bilgiler içeren içeriğe erişimi engelin, ancak kullanıcının gerekirse içeriği geçersiz k olmasına ve paylaşmasına veya göndermesine izin verme.
    
Olay raporları veya erişimi kısıtlama hakkında daha fazla bilgi için bkz. [Veri kaybı önleme başvurusu](data-loss-prevention-policies.md).
  
Bu seçenekleri daha sonra değiştirmek için, varsayılan DLP İlkesini istediğiniz zaman düzenleyebilirsiniz; sonraki bölüme bakın.
  
![Ayarlar paylaşılan içeriği daha fazla koruma adlı widget'a tıklayın.](../media/dad30a84-2715-4c0a-a5c5-44d85492363e.png)
  
## <a name="edit-the-default-dlp-policy"></a>Varsayılan DLP ilkesi düzenleme

Bu ilke Varsayılan **DLP ilkesi olarak adlandırılmıştır** ve Güvenlik  Uyumluluk Merkezi'nin **İlke sayfasında Veri** kaybını önleme altında &amp; görünür. 
  
Bu ilke tümüyle özelleştirilebilir ve aynı sıfırdan kendi oluşturmanıza neden olan tüm DLP ilkelerinden aynıdır. Ayrıca, kullanıcılarınız artık ilke ipuçları veya e-posta bildirimleri almamalarını için ilkeyi kapatabilirsiniz veya silebilirsiniz.
  
![Varsayılan DLP ilkesi adlı DLP ilkesi.](../media/260731e8-4d57-4c98-abec-07b052ec48d5.png)
  
## <a name="when-the-widget-does-and-does-not-appear"></a>Pencere öğesi bunu yapar ve görünmezse

Paylaşılan içeriği **daha fazla koruma adlı** widget, Güvenlik Uyumluluk  Merkezi'nin **Giriş sayfasının Sizin** için önerilenler &amp; bölümünde görünür. 
  
Bu widget yalnızca şu olduğunda görüntülenir:
  
- Güvenlik Uyumluluk Merkezi'nde veya Yönetim Merkezi'nde &amp; veri Exchange ilkeleri yoktur. Bu widget, DLP'ye başlamanıza yardımcı olmak için tasarlanmıştır, dolayısıyla zaten DLP ilkeleriniz varsa bu pencere öğesi görünmez.
    
- Son 30 gün içinde en az bir kredi kartının bulunduğu içerik, kuruluş dışındaki biriyle paylaşıldı.
    
Kural eşleşmelerini widget'ın kullanılabilir olması 48 saate kadar sürebilir; dolayısıyla dışarıdan paylaşılan hassas bilgiler algılandığında önerinin görünmesi iki gün kadar sürebilir.
  
Son olarak, varsayılan DLP ilkesi geliştirmek için widget'ı kullandıktan sonra, widget Giriş **sayfasından kaybolur** . 
  

