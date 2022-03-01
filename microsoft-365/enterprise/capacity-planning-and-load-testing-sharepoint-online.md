---
title: SharePoint Online’da kapasite planlaması ve yük testi
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 04/10/2019
audience: Admin
ms.topic: conceptual
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
ms.assetid: c932bd9b-fb9a-47ab-a330-6979d03688c0
description: Bu makalede, izin verilmediğini ve geleneksel yükleme testlerini gerçekleştirmeden SharePoint Online'a nasıl dağıtım ver verildiği açıklanmıştır.
ms.openlocfilehash: 8792c59ef96ef97cc36d0908100fd9ebb330857a
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2022
ms.locfileid: "63015184"
---
# <a name="capacity-planning-and-load-testing-sharepoint-online"></a>SharePoint Online’da kapasite planlaması ve yük testi
Bu makalede, SharePoint Online'da yükleme testine izin verilmediğiniden geleneksel yükleme testine gerek kalmadan SharePoint açıklanmıştır. SharePoint Online bir bulut hizmetidir ve hizmet üzerindeki yükleme özellikleri, hizmet durumu ve genel yük dengesi Microsoft tarafından yönetilir.
  
Sitenizi başlatma başarılarından emin olmak için en iyi yaklaşım, portal lansmanında plan üzerinde vurgulanan temel ilkelere, uygulamalara ve [önerilere uymanızdır](planportallaunchroll-out.md).

## <a name="overview-of-how-sharepoint-online-performs-capacity-planning"></a>SharePoint Online'ın Kapasite planlamasının nasıl gerçekleştirdiğine genel bakış 
SharePoint Online'ın şirket içi dağıtımdan yararlanmanın en büyük avantajlarından biri, bulutun esnekliği ve dağıtılmış bölgelerdeki kullanıcılar için iyileştirmelerdir. Büyük ölçekli ortamımız milyonlarca kullanıcıya günlük olarak hizmet olacak şekilde ayarlanmıştır; dolayısıyla gruplarla denge kurarak ve genişleterek kapasiteyi etkili bir şekilde işlememiz önemlidir.
  
Büyüme, herhangi bir grupta yer alan herhangi bir kiracı için çoğunlukla öngörülemez durumdayken, toplam istek toplamı zamanla öngörülebilir olur. SharePoint Online'da büyüme eğilimlerini tanımarak, gelecekteki genişletmeyi planlayacağız.
  
Her grup için kapasiteyi verimli bir şekilde kullanmak ve beklenmedik büyümeyle başa çık sağlamak için, hizmetin çeşitli öğelerini izleyen ve izleyen otomasyon kaynakmız vardır. Ana ölçümlerden biri CPU yüküdir ve ön uç sunucularını ölçeklendirmek için sinyal olarak kullanılır. Buna ek olarak, SQL ortamları zaman içinde yük ve gelişmeye göre ölçeklendirilecek ve aşamalarla dalgalara göre doğru dağılımı sağlayan bir aşama [/](planportallaunchroll-out.md)dalga yaklaşımı öneririz. 

Kapasite, sürekli olarak daha fazla donanım eklemekten çok daha fazlasıdır, ancak aynı zamanda geçerli yükleme isteklerine hizmet olduğundan emin olmak için bu kapasiteyi yönetmeyi ve denetlemeyi de içerir. Müşterilerin en iyi deneyime sahip olduğundan emin olmak için önerilen yönergeleri izlemelerini öneririz. Ayrıca, hizmette "kötü amaçlı" davranışa izin verme vermemiz için azaltma düzenleri ve denetimlerimiz olduğu anlamına da gelir. Tüm "kötü" davranışlar bilerek yapmasa da, bu davranışın etkisini sınırlayın. Azaltma ve bundan kaçınma hakkında daha fazla bilgi için, kısıtlamaya neden olan [kısıtlamayı önleme kılavuz makalesini gözden](/sharepoint/dev/general-development/how-to-avoid-getting-throttled-or-blocked-in-sharepoint-online) geçirebilirsiniz.

## <a name="why-you-cannot-load-test-sharepoint-online"></a>Test e-SharePoint Online'SharePoint yükleyemedik
Şirket içi ortamlarda, yükleme testi ölçek varsayımı doğrulamak ve sonuçta bir sunucu grubunun en son noktasını bulmak için kullanılır; yük ile doygunlukla doldurarak. 

SharePoint Online ile, ölçeğin görece akıcı olduğundan, belirli küçük ayarlara dayalı olarak yük yüklerini, azaltmaları ve denetimleri ayarlay olduğundan işleri farklı bir şekilde yapacağız. Bu kadar büyük ölçekli çok kiracılı bir ortam olması dolayısıyla tüm yükleme testlerini otomatik olarak azaltmamız için aynı grup içinde tüm kiracıları korumamız gerekir. Öte yandan test yükleme girişimi yapıyorsanız, kısıtlamanın yanı sıra sizi yanıltmaya da neden olabilecek sonuçlar alırsınız, çünkü bugün test ettiyniz grup test penceresinde veya test sonrası saatleri içinde ölçek değişiklikleri gerçekleştirecek olduğundan, ölçek ve grup dengeleme eylemleri düzenli olarak gerçekleştirilir.

Test sonuçlarını bir hizmet SharePoint yerine, önerilen uygulamaları takip etmeye ve sağlıklı bir [portal oluşturma,](/sharepoint/portal-health) başlatma ve koruma yönergelerini takip etmeye odaklanın.