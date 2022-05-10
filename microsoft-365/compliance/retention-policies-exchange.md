---
title: Exchange için bekletme hakkında bilgi edinin
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
description: Bekletmenin Exchange için nasıl çalıştığını öğrenin.
ms.openlocfilehash: b49a21f5358bb8d4b25c1b164d30180f1fa265d9
ms.sourcegitcommit: 5c64002236561000c5bd63c71423e8099e803c2d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/09/2022
ms.locfileid: "65285956"
---
# <a name="learn-about-retention-for-exchange"></a>Exchange için bekletme hakkında bilgi edinin

>*[Güvenlik & uyumluluğu için lisanslama yönergelerini Microsoft 365](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Bu makaledeki bilgiler, Exchange özgü bilgiler içerdiğinden [Saklama hakkında bilgi edinin](retention.md) ekini ekler.  Diğer iş yükleri için bkz:

- [SharePoint ve OneDrive için bekletme hakkında bilgi edinin](retention-policies-sharepoint.md)
- [Microsoft Teams için bekletme hakkında bilgi edinin](retention-policies-teams.md)
- [Yammer için bekletme hakkında bilgi edinin](retention-policies-yammer.md)

## <a name="whats-included-for-retention-and-deletion"></a>Saklama ve silmeye dahil olanlar

Kullanıcı posta kutularından ve paylaşılan posta kutularından gelen aşağıdaki Exchange öğeleri bekletme ilkeleri ve bekletme etiketleri kullanılarak korunabilir ve silinebilir: Posta iletileri (alınan iletiler, taslaklar, gönderilmiş iletiler dahil) ekleri, bitiş tarihleri olan görevler ve notlar. 

Bitiş tarihi olan takvim öğeleri bekletme ilkeleri için desteklenir ancak bekletme etiketleri için desteklenmez.

Kişiler ve bitiş tarihi olmayan görevler ve takvim öğeleri desteklenmez.

Posta kutusunda depolanan Skype ve Teams iletileri gibi diğer öğeler, Exchange saklama ilkelerine veya etiketlerine dahil değildir. Bu öğelerin kendi bekletme ilkeleri vardır.

Bekletme ayarları uygulanmadan önce posta kutuları en az 10 MB veriye sahip olmalıdır ve bekletme etiketleri bu verilere yayımlanabilir.

## <a name="how-retention-works-for-exchange"></a>Bekletme Exchange için nasıl çalışır?

Hem posta kutusu hem de ortak klasör, öğeleri korumak için [Kurtarılabilir Öğeler klasörünü](/exchange/security-and-compliance/recoverable-items-folder/recoverable-items-folder) kullanır. Yalnızca eBulma izinleri atanmış kişiler başka bir kullanıcının Kurtarılabilir Öğeler klasöründeki öğeleri görüntüleyebilir.
  
Kullanıcı, Silinmiş Öğeler klasörü dışındaki bir klasördeki iletiyi sildiğinde, varsayılan olarak ileti Silinmiş Öğeler klasörüne taşınır. Ancak, kullanıcı herhangi bir klasördeki bir öğeyi geçici olarak silebilir (Shift+Delete), Silinmiş Öğeler klasörünü atlar ve öğeyi doğrudan Kurtarılabilir Öğeler klasörüne taşır.
  
Exchange verilerine bekletme ayarları uyguladığınızda, zamanlayıcı işi Kurtarılabilir Öğeler klasöründeki öğeleri düzenli aralıklarla değerlendirir. Öğeyi korumak için en az bir bekletme ilkesi veya bekletme etiketi kurallarıyla eşleşmiyorsa, Kurtarılabilir Öğeler klasöründen kalıcı olarak silinir (sabit olarak da adlandırılır).

> [!NOTE]
> [İlk saklama ilkesi](retention.md#the-principles-of-retention-or-what-takes-precedence) nedeniyle, aynı öğenin başka bir bekletme ilkesi veya saklama etiketi nedeniyle korunması gerekiyorsa veya yasal veya araştırma amaçlı olarak eBulma tutmaları altındaysa kalıcı silme işlemi her zaman askıya alınır.

Zamanlayıcı işinin çalışması yedi güne kadar sürebilir ve Exchange konumu en az 10 MB içermelidir.
  
Kullanıcı bir posta kutusu öğesinin konu, gövde, ekler, gönderenler ve alıcılar veya ileti için gönderilen veya alınan tarih gibi özelliklerini değiştirmeye çalıştığında, değişiklik işlenmeden önce özgün öğenin bir kopyası Kurtarılabilir Öğeler klasörüne kaydedilir. Bu eylem sonraki her değişiklik için gerçekleşir. Saklama süresinin sonunda Kurtarılabilir Öğeler klasöründeki kopyalar kalıcı olarak silinir.

bekletme ayarları Exchange içeriğe uygulandıktan sonra, içeriğin izlediği yollar bekletme ayarlarının tutulup silineceği, yalnızca korunacağı veya silineceği durumuna bağlıdır.

Bekletme ayarlarının saklanması ve silinmesi gerektiğinde:

![E-posta ve ortak klasörlerdeki bekletme akışının diyagramı.](../media/88f174cc-bbf4-4305-93d7-0515f496c8f9.png)

1. Öğe saklama süresi boyunca kullanıcı tarafından **değiştirildiyse veya kalıcı olarak silindiyse** (SHIFT+DELETE veya Silinmiş Öğeler'den silindiyse): Öğe Kurtarılabilir Öğeler klasörüne taşınır (veya düzenleme durumunda kopyalanır). Burada, bir zamanlayıcı işi düzenli aralıklarla çalışır ve bekletme süresi dolan öğeleri tanımlar ve bu öğeler saklama süresinin sona ermesinin ardından 14 gün içinde kalıcı olarak silinir. Varsayılan ayar 14 gün olsa da 30 güne kadar yapılandırılabilir.

2. Öğe bekletme süresi boyunca **değiştirilmez veya silinmezse**: Aynı işlem posta kutusundaki tüm klasörlerde düzenli aralıklarla çalıştırılır ve bekletme süresi dolan öğeleri tanımlar ve bu öğeler saklama süresinin sonundan sonraki 14 gün içinde kalıcı olarak silinir. Varsayılan ayar 14 gün olsa da 30 güne kadar yapılandırılabilir. 

Bekletme ayarları yalnızca saklama veya yalnızca silme olduğunda, içerik yolları saklama ve silme çeşitlemeleridir:

### <a name="content-paths-for-retain-only-retention-settings"></a>Yalnızca saklama saklama ayarları için içerik yolları

1. Öğe bekletme süresi boyunca **değiştirilir veya silinirse**: Kurtarılabilir Öğeler klasöründe özgün öğenin bir kopyası oluşturulur ve Kurtarılabilir Öğeler klasöründeki kopyanın süresi dolduktan sonraki 14 gün içinde kalıcı olarak silindiği saklama süresinin sonuna kadar saklanır. 

2. Saklama süresi boyunca **öğe değiştirilmez veya silinmezse**: Saklama süresinden önce ve sonra hiçbir şey olmaz; öğe özgün konumunda kalır.

### <a name="content-paths-for-delete-only-retention-settings"></a>Yalnızca silme bekletme ayarları için içerik yolları

1. Öğe yapılandırılan süre boyunca **silinmezse**: Bekletme ilkesinde yapılandırılan dönemin sonunda öğe Kurtarılabilir Öğeler klasörüne taşınır. 

2. Öğe yapılandırılan dönemde **silinirse**: Öğe hemen Kurtarılabilir Öğeler klasörüne taşınır. Kullanıcı öğeyi oradan silerse veya Kurtarılabilir Öğeler klasörünü boşaltırsa, öğe kalıcı olarak silinir. Aksi takdirde, öğe 14 gün boyunca Kurtarılabilir Öğeler klasöründe olduktan sonra kalıcı olarak silinir. 

## <a name="user-notification-of-expiry-date"></a>Süre sonu tarihi için kullanıcı bildirimi

diğer Microsoft 365 iş yükleri için bekletme ilkelerinin aksine, Exchange için bekletme ilkeleri, her e-posta iletisinin en üstünde öğe için en kısa süre sonu tarihine sahip bekletme ilkesinin adını ve bu öğenin hesaplanan süre sonu tarihini görüntüleyerek bir kullanıcı iletişim durumu gösterir. Bekletme ilkesi öğeleri silmezse (yalnızca saklama) kullanıcılar bu bildirimi görmez.

Bir e-posta iletisine bekletme etiketi uygulanırsa, bu etiketin adı ve karşılık gelen süre sonu tarihi her zaman görüntülenir ve posta kutusuna uygulanan bekletme ilkesindeki adı ve tarihi değiştirir.

Bu bağlamda, e-postanın silineceği süre sonu tarihinin, kullanıcıların e-posta iletisinin otomatik olarak Kurtarılabilir Öğeler klasörüne taşınmasını bekleyebileceği tarih olduğunu unutmayın (henüz yoksa). Kurtarılabilir Öğeler klasöründeki e-postalar kalıcı olarak silinmez, ancak saklamaya yönelik herhangi bir saklama ayarına tabi olmaları veya yasal veya araştırıcı nedenlerle eBulma kapsamında olmaları durumunda uyumluluk amacıyla orada kalırlar.

## <a name="when-a-user-leaves-the-organization"></a>Kullanıcı kuruluştan ayrıldığında 

Bir kullanıcı kuruluşunuzdan ayrılırsa ve kullanıcının posta kutusu bekletme ilkesine dahil edilirse, kullanıcının Microsoft 365 hesabı silindiğinde posta kutusu etkin olmayan bir posta kutusuna dönüşür. Etkin olmayan posta kutusunun içeriği, posta kutusu devre dışı bırakılmadan önce posta kutusuna yerleştirilen bekletme ilkesine tabidir ve içerik eBulma aramasında kullanılabilir. Daha fazla bilgi için bkz. [Exchange Online'da etkin olmayan posta kutuları](inactive-mailboxes-in-office-365.md).

Veriler kalıcı olarak silindiği veya saklama süresinin dolduğu için bekletme ayarları artık geçerli olmadığında, Exchange yöneticisi [artık etkin olmayan posta kutusunu silebilir](delete-an-inactive-mailbox.md). Bu senaryoda, etkin olmayan posta kutusu otomatik olarak silinmez.

## <a name="configuration-guidance"></a>Yapılandırma kılavuzu

Microsoft 365'de saklamayı yapılandırma konusunda yeniyseniz bkz. [Veri yaşam döngüsü yönetimiyle Kullanmaya başlayın](get-started-with-data-lifecycle-management.md).

Exchange için bir bekletme ilkesi veya bekletme etiketi yapılandırmaya hazırsanız aşağıdaki yönergelere bakın:
- [Bekletme ilkeleri oluşturma ve yapılandırma](create-retention-policies.md)
- [Bekletme etiketlerini yayımlama ve uygulamalarda uygulama](create-apply-retention-labels.md)
- [İçeriğe otomatik olarak bekletme etiketi uygulama](apply-retention-labels-automatically.md)
