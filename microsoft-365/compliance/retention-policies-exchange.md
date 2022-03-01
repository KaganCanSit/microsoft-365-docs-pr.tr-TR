---
title: Müşteri için bekletme hakkında bilgi Exchange
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MET150
description: Bekletmenin nasıl çalıştığını öğrenin Exchange.
ms.openlocfilehash: f92df4bd25ddeff44472865c9ae221014050afaa
ms.sourcegitcommit: 400ef9ac34247978e3de7ecc0b376c4abb6c99d8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/27/2022
ms.locfileid: "63009982"
---
# <a name="learn-about-retention-for-exchange"></a>Müşteri için bekletme hakkında bilgi Exchange

Bu makaledeki bilgiler Bekletme hakkında bilgi [edinebilirsiniz](retention.md) çünkü saklama hakkında bilgi edinmek için Exchange.  Diğer iş yükleri için bkz:

- [E-SharePoint ve OneDrive](retention-policies-sharepoint.md)
- [Müşteri için bekletme hakkında bilgi Microsoft Teams](retention-policies-teams.md)
- [Müşteri için bekletme hakkında bilgi Yammer](retention-policies-yammer.md)

## <a name="whats-included-for-retention-and-deletion"></a>Bekletme ve silme işlemi için neler dahildir?

Aşağıdaki Exchange posta kutularına ve paylaşılan posta kutularına gelen öğeler, bekletme ilkeleri ve bekletme etiketleri kullanılarak korunarak silinebilir: Ekleri olan posta iletileri (alınan iletiler, taslaklar, gönderilmiş iletiler dahil), bitiş tarihi ve notları olan görevler. 

Bitiş tarihi olan takvim öğeleri bekletme ilkeleri için destekler, ancak bekletme etiketlerini desteklemez.

Kişiler ve bitiş tarihine sahip olmadığınız görevler ve takvim öğeleri desteklanmaz.

Posta kutusunda depolanan diğer öğeler, örneğin Skype Teams iletileri bekletme ilkelerine veya etiketlerine dahil Exchange. Bu öğelerin kendi bekletme ilkeleri vardır.

## <a name="how-retention-works-for-exchange"></a>Müşteri için bekletme nasıl Exchange

Öğeleri tutmak için hem posta kutusu hem de [ortak klasör Kurtarılabilir Öğeler](/exchange/security-and-compliance/recoverable-items-folder/recoverable-items-folder) klasörünü kullanır. Yalnızca eBulma izinleri atanmış olan kişiler, başka bir kullanıcının Kurtarılabilir Öğeler klasöründeki öğeleri ilebilir.
  
Kullanıcı Silinmiş Öğeler klasörü dışında bir klasörde bir iletiyi sdiğinde, ileti varsayılan olarak Silinmiş Öğeler klasörüne taşınır. Bununla birlikte, kullanıcı Silinmiş Öğeler klasörünü atlayan ve öğeyi doğrudan Kurtarılabilir Öğeler klasörüne taşırken herhangi bir klasörde öğeyi yumuşak olarak silebilir (Shift+Delete).
  
Bu verilere bekletme ayarları Exchange, bir süreölçer işi Kurtarılabilir Öğeler klasöründeki öğeleri düzenli olarak değerlendirir. Bir öğe, en az bir bekletme ilkesi veya bekletme etiketinin kurallarına uymazsa, Kurtarılabilir Öğeler klasöründen kalıcı olarak silinir (kalıcı olarak da denir).

> [!NOTE]
> İlk bekletme ilkesi [nedeniyle, aynı](retention.md#the-principles-of-retention-or-what-takes-precedence) öğenin başka bir bekletme ilkesi veya bekletme etiketi nedeniyle korunması gerekirse ya da yasal veya yatırımlı nedenlerle eBulma bekletme kapsamında ise kalıcı silme işlemi her zaman askıya alınır.

Zamanlayıcı işinin çalışması yedi gün kadar zaman içerebilir ve Exchange en az 10 MB olmalıdır.
  
Kullanıcı bir ileti için konu, gövde, ekler, gönderenler ve alıcılar gibi posta kutusu öğesinin özelliklerini değiştirmeye çalışırsa, değişiklik kabul edilene kadar özgün öğenin bir kopyası Kurtarılabilir Öğeler klasörüne kaydedilir. Bu eylem sonraki her değişiklik için gerçekleşir. Bekletme döneminin sonunda, Kurtarılabilir Öğeler klasöründeki kopyalar kalıcı olarak silinir.

İçerikte bekletme ayarları Exchange, içeriğin yollarını bekletme ayarlarının alıkoyma ve silme, yalnızca koruma veya yalnızca silme durumuna bağlı olarak değiştirmesi gerekir.

Bekletme ayarları korunarak silinecek olduğunda:

![E-posta ve ortak klasörlerdeki bekletme akışının diyagramı.](../media/88f174cc-bbf4-4305-93d7-0515f496c8f9.png)

1. **Öğe** , bekletme süresince kullanıcı tarafından değiştirildi veya kalıcı olarak silindiğinde (SHIFT+DELETE veya Silinmiş Öğeler'den silindi): Öğe, düzenleme durumunda kopyalanabilir Öğeler klasörüne taşınır (veya kopyalanır). Burada, bir süreölçer işi düzenli olarak çalışır ve bekletme süresi dolmuş olan öğeleri tanımlar ve bu öğeler, bekletme süresinin sonundan sonra 14 gün içinde kalıcı olarak silinir. Varsayılan ayar 14 gündür, ancak en çok 30 gün yapılandırabilirsiniz.

2.  Öğe bekletme süresi boyunca değiştirilmez veya silinmezse: Aynı işlem düzenli aralıklarla posta kutusunun tüm klasörlerinde çalışır ve bekletme süresi dolmuş olan öğeleri tanımlar ve bu öğeler, bekletme süresinin sonundan sonra 14 gün içinde kalıcı olarak silinir. Varsayılan ayar 14 gündür, ancak en çok 30 gün yapılandırabilirsiniz. 

Bekletme ayarları yalnızca koruma veya yalnızca silme olduğunda, içerik yolları koruma ve silme çeşitlemeleridir:

### <a name="content-paths-for-retain-only-retention-settings"></a>Yalnızca bekletme ayarları için içerik yolları

1.  Öğe bekletme süresi boyunca değiştirilir veya silinirse: Özgün öğenin bir kopyası Kurtarılabilir Öğeler klasöründe oluşturulur ve bekletme döneminin sonuna kadar korunur. Kurtarılabilir Öğeler klasöründeki kopya, öğenin süresi dolduktan sonra 14 gün içinde kalıcı olarak silindiğinde, bekletme süresinin sonuna kadar korunur. 

2. **Öğe bekletme süresi boyunca değiştirilmez veya silinmezse** : Bekletme süresi öncesinde ve sonrasında hiçbir şey olmaz; öğe özgün konumda kalır.

### <a name="content-paths-for-delete-only-retention-settings"></a>Yalnızca silme bekletme ayarları için içerik yolları

1. **Öğe yapılandırılmış dönem boyunca** silinmezse: Bekletme ilkesinde, yapılandırılmış dönemin sonunda, öğe Kurtarılabilir Öğeler klasörüne taşınır. 

2. **Yapılandırılan dönem içinde** öğe silinirse: Öğe hemen Kurtarılabilir Öğeler klasörüne taşınır. Kullanıcı öğeyi buradan silerse veya Kurtarılabilir Öğeler klasörünü boşaltmışsa, öğe kalıcı olarak silinir. Aksi takdirde, 14 gün süreyle Kurtarılabilir Öğeler klasöründe bulunduktan sonra öğe kalıcı olarak silinir. 

## <a name="user-notification-of-expiry-date"></a>Son kullanma tarihi için kullanıcı bildirimi

Exchange için bekletme ilkeleri diğer Microsoft 365 iş yüklerinin bekletme ilkelerden farklı olarak, her e-posta iletinin en üstünde görüntüleyerek öğe için son kullanma tarihi en kısa olan bekletme ilkesi adını ve bu öğenin hesaplanmış son kullanma tarihini görüntüleyerek bir kullanıcı iletişim durumuna sahip olur. Bekletme ilkesi öğeleri silemezse (yalnızca bekletme) kullanıcılar bu bildirimi görmez.

E-posta iletisine bir bekletme etiketi uygulanmışsa, söz konusu etiketin adı ve buna karşılık gelen son kullanma tarihi her zaman görüntülenir ve posta kutusuna uygulanan tüm bekletme ilkesinden gelen ad ve tarihin yerini alır.

Unutmayın; bu bağlamda, e-postanın silindiği tarihin son kullanma tarihi, kullanıcıların e-posta iletisine otomatik olarak Kurtarılabilir Öğeler klasörüne taşınmasını bekleyebiliyor olmasıdır (henüz orada değilse). Kurtarılabilir Öğeler klasöründeki e-postalar kalıcı olarak silinmez, ancak herhangi bir bekletme ayarına tabi olur ve uyumluluk nedeniyle orada kalırlar ya da yasal veya soruşturma nedeniyle eBulma kapsamında kalırlar.

## <a name="when-a-user-leaves-the-organization"></a>Bir kullanıcı kuruluşdan ayrıldığında 

Kullanıcı kuruluştan ayrılırsa ve kullanıcının posta kutusu bekletme ilkesine dahil edilirse, kullanıcının hesabı silindiğinde posta kutusu devre Microsoft 365 posta kutusu olur. Etkin olmayan posta kutusunun içeriği, etkin olmayan posta kutusu öncesinde posta kutusuna yerleştirilen her bekletme ilkesine tabi olur ve içerikler eBulma aramalarında kullanılabilir. Daha fazla bilgi için bkz[. Etkin olmayan posta kutuları Exchange Online](inactive-mailboxes-in-office-365.md).

Veriler kalıcı olarak silindiğinde veya bekletme süresi sona erdiğinde artık bekletme ayarları Exchange yönetici artık etkin olmayan posta [kutusunu silebilir](delete-an-inactive-mailbox.md). Bu senaryoda, etkin olmayan posta kutusu otomatik olarak silinmez.

## <a name="configuration-guidance"></a>Yapılandırma kılavuzu

Bekletmeyi yeni bir web günlüğünde yapılandırmaya Microsoft 365 [bkz. Bilgi yönetimiyle çalışmaya başlama](get-started-with-information-governance.md).

E-posta için bir bekletme ilkesi veya bekletme etiketi yapılandırmaya Exchange, aşağıdaki yönergelere bakın:
- [Bekletme ilkeleri oluşturma ve yapılandırma](create-retention-policies.md)
- [Bekletme etiketleri oluşturma ve bunları uygulamalarda uygulama](create-apply-retention-labels.md)
- [İçeriği otomatik olarak bekletme etiketi uygulama](apply-retention-labels-automatically.md)