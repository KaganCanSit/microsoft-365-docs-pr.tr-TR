---
title: Müşteri için bekletme hakkında bilgi Yammer
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
description: İlkelere uygulanacak bekletme ilkeleri hakkında Yammer.
ms.openlocfilehash: 3759f39a9ef2067d9719d4cf83d73ee7b67ef125
ms.sourcegitcommit: 400ef9ac34247978e3de7ecc0b376c4abb6c99d8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/27/2022
ms.locfileid: "63010851"
---
# <a name="learn-about-retention-for-yammer"></a>Müşteri için bekletme hakkında bilgi Yammer

>*[Microsoft 365 uyumluluğu için lisans & kılavuzu.](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance)*

> [!NOTE]
> Bu özellik önizlemededir ve değişebilir.

Bu makaledeki bilgiler Bekletme hakkında bilgi [edin' makalesine](retention.md) özgü bilgiler olduğundan saklama hakkında bilgi Yammer.

Diğer iş yükleri için bkz:

- [E-SharePoint ve OneDrive](retention-policies-sharepoint.md)
- [Müşteri için bekletme hakkında bilgi Microsoft Teams](retention-policies-teams.md)
- [Müşteri için bekletme hakkında bilgi Exchange](retention-policies-exchange.md)

## <a name="whats-included-for-retention-and-deletion"></a>Bekletme ve silme işlemi için neler dahildir?

Yammer iletileri ve topluluk iletileri, Yammer için bekletme ilkeleri kullanılarak silinebilir ve bu iletilerde yer alan metinlere ek olarak uyumluluk nedenlerinden dolayı aşağıdaki öğeler de korunabilirsiniz: Köprü Metni bağlantıları ve diğer Yammer iletilerine bağlantılar.

> [!NOTE]
> Aşağıdaki bölümde de açıklanan şekilde, kullanıcı iletileri bireysel bir kullanıcı için özel iletiler ve bu kullanıcıyla ilişkilendirilmiş topluluk iletilerini içerir.

Kullanıcı iletileri konuşmada yer alan kişilerin tüm adlarını ve topluluk iletilerinin içinde topluluk adı ve ileti başlığı (varsa) yer alır.

Diğer kişilerden gelen ifade biçimine sahip tepkiler, diğer e-posta veya Yammer.

Dosya dosyalarıyla birlikte Yammer, bu dosyalar sizin için bekletme ilkelerine Yammer. Bu öğelerin kendi bekletme ilkeleri vardır.

## <a name="how-retention-works-with-yammer"></a>Bekletme, alanla birlikte Yammer

Bu bölümü kullanarak, uyumluluk gereksinimlerinizin arka uç depolama ve işlemlerle nasıl karşılandığından emin olun ve o anda Yammer uygulamasında görünen iletiler tarafından değil eBulma araçlarıyla doğrulanmalıdır.

Bir bekletme ilkesi kullanarak topluluk iletilerinden ve kullanıcı iletilerinden gelen verileri Yammer ve bu iletileri silebilirsiniz. Sahne gerisinde, Exchange kutuları bu iletilerden kopyalanan verileri depolamak için kullanılır. Kullanıcı iletileri Yammer iletilerinden veriler kullanıcı iletisine dahil edilen her kullanıcının posta kutusunda gizli bir klasörde depolanır ve topluluk iletileri için grup posta kutusunda da benzer bir gizli klasör kullanılır.

Topluluk iletilerinin kopyaları, kullanıcılardan @bahsed olduğunda veya kullanıcıya bir yanıt hakkında bildirim göndererek kullanıcı posta kutularının gizli klasöründe de depolanıyor olabilir. Bu iletiler bir topluluk iletisi olarak kaynaklasa da, kullanıcı iletilerine Yammer saklama ilkesi genellikle topluluk iletilerinin kopyalarını içerir. Sonuç olarak, kullanıcı iletileri özel iletiyle sınırlı değildir.

Bu gizli klasörler, kullanıcılar veya yöneticiler için doğrudan erişilebilir olacak şekilde tasarlanmasa da, uyumluluk yöneticilerinin eBulma araçlarıyla arama yapmak için depolayamları yerine verileri depolar.

> [!IMPORTANT]
> Topluluk iletilerinin kopyaları kullanıcı posta kutularında da depolanamay olduğundan, Yammer kullanıcı iletilerine bir silme eylemiyle birlikte bir bekletme ilkesi özgün topluluk iletisi Yammer uygulamasındaki kullanıcılar tarafından görülmeyebilir.
> 
> Bununla birlikte, özgün iletinin bir kopyası yine topluluk grubu posta kutusunun gizli klasöründe kullanılabilir ve uyumluluk amacıyla eKbulma aramaleriyle erişilebilir.

İletiler Exchange Yammer, yalnızca Yammer iletileri veya kullanıcı iletileri konumları için yapılandırılmış bir **bekletme** **Yammer** içerir.

> [!NOTE]
> Kullanıcı, Yammer verilerini bulunduran etkin bir bekletme ilkesinde yer alıyorsa ve siz de bu ilkeye dahil olan bir kullanıcının posta kutusunu silerseniz, Yammer verilerini korumak için, posta kutusu etkin olmayan posta kutusuna [dönüştürülür](inactive-mailboxes-in-office-365.md). Kullanıcının bu veri verilerini saklamanız Yammer, posta kutusunu smeden önce kullanıcı hesabını bekletme ilkesinden çıkarabilirsiniz.

İletiler için bir bekletme ilkesi Yammer, Exchange hizmetinin zamanlayıcı işi bu iletilerin depolandığı gizli klasördeki öğeleri düzenli Yammer olarak değerlendirir. Zamanlayıcı işinin çalışması yedi gün kadar sürer. Bu öğelerin bekletme süresi dolduğunda, kalıcı olarak silinmeden önce her kullanıcı veya grup posta kutusunda "geçici silinmiş" öğeleri depolamak için kullanılan gizli bir klasör olan SubstrateHolds klasörüne taşınır.

> [!IMPORTANT]
> İlk bekletme [ilkesinden](retention.md#the-principles-of-retention-or-what-takes-precedence) dolayı ve Yammer iletileri Exchange Online posta kutularında depolandığı için, posta kutusu başka bir bekletme ilkesinden etkileniyorsa (posta kutusuna uygulanan ilkeler de dahil olmak üzere) SubstrateHolds klasöründen kalıcı olarak silinmesi Exchange  konumu), mahkeme nedeniyle tutma, gecikme nedeniyle veya yasal veya soruşturma nedeniyle posta kutusuna eBulma tutma uygulanırsa.
>
> Posta kutusu geçerli bir tutma kapsamındayken, Yammer silinen iletiler Yammer'de görünmez ancak eKbulma ile keşfedilebilir olmaya devam eder.

İletilere yönelik bir bekletme ilkesi Yammer sonra, içeriğin gereklere bakıldığında, bekletme ilkesi tutma ve sonra silme, yalnızca koruma veya yalnızca silme arasında seçim yapmak gerekir.

Bekletme ilkesi korunarak silinecek olduğunda:

![İletiler için bekletme Yammer diyagramı.](../media/yammerretentionlifecycle.png)

Diyagramda iki yol için:

1. **Bekletme Yammer** bir kullanıcı tarafından düzenlenen veya silinen bir ileti varsa, özgün ileti hemen kopyalanır (düzenlenmişse) veya SubstrateHolds klasörüne taşınır (silinmişse). İleti, bekletme süresi dolana kadar orada depolanır ve sonra ileti hemen kalıcı olarak silinir.

2. **Düzenleme Yammer** bir ileti silinmezse ve geçerli iletiler için bekletme süresi dolduktan sonra ileti SubstrateHolds klasörüne taşınır. Bu işlem son kullanma tarihinden yedi gün sonraya kadar sürer. İleti SubstrateHolds klasöründe olduğunda, hemen kalıcı olarak silinir. 

> [!NOTE]
> SubstrateHolds klasöründeki iletiler eBulma araçlarıyla aranabilir. İletiler kalıcı olarak silinene kadar (SubstrateHolds klasöründe), eBulma araçlarıyla aranabilir durumda kalırlar.

Bekletme ilkesi yalnızca saklama veya yalnızca silme olduğunda, içeriğin yolları koruma ve silmenin bir çeşitletir.

### <a name="content-paths-for-retain-only-retention-policy"></a>Yalnızca bekletme ilkesi için içerik yolları

1. **Yeni Yammer** bir ileti düzenlenmiş veya silinmişse: Özgün iletinin bir kopyası SubstrateHolds klasöründe hemen oluşturulur ve bekletme süresi dolana kadar orada korunur. Daha sonra ileti SubstrateHolds klasöründen kalıcı olarak silinir.

2. **Yeni ileti Yammer**, bekletme süresi boyunca düzenlendikten sonra geçerli iletiler için değiştirilmez veya silinmezse: Bekletme süresi öncesinde ve sonrasında hiçbir şey olmaz; ileti özgün konumda kalır.

### <a name="content-paths-for-delete-only-retention-policy"></a>Yalnızca silme bekletme ilkesi için içerik yolları

1. **Yeni Yammer, bekletme** süresi boyunca silinmezse: Bekletme döneminin sonunda, ileti SubstrateHolds klasörüne taşınır. Bu işlem son kullanma tarihinden yedi gün sonraya kadar sürer. Daha sonra ileti SubstrateHolds klasöründen kalıcı olarak silinir.

2. **Bu Yammer kullanıcı tarafından** silinirse, öğe hemen SubstrateHolds klasörüne taşınır ve bu klasör hemen kalıcı olarak silinir.

#### <a name="example-flows-and-timings-for-retention-policies"></a>Bekletme ilkeleri için örnek akışlar ve zamanlamalar

Önceki bölümlerde açıklanan işlemlerin ve zamanlamaların aşağıdaki yapılandırmalara sahip bekletme ilkelerine nasıl uygulanıyor olduğunu görmek için aşağıdaki örnekleri kullanın:

- [Örnek 1: 7 yıl boyunca yalnızca koruma](#example-1-retain-only-for-7-years)
- [Örnek 2: 30 gün süreyle tutma ve silme](#example-2-retain-for-30-days-and-then-delete)
- [Örnek 3: 1 gün sonra yalnızca silme](#example-3-delete-only-after-1-day)

Kalıcı silmeye başvuran tüm örneklerde, bekletme ilkeleri [nedeniyle, ileti](retention.md#the-principles-of-retention-or-what-takes-precedence) öğeyi alıkoyacak başka bir bekletme ilkesine tabi olursa veya öğe eBulma bekletmeye tabi olursa bu eylem askıya alınır.

##### <a name="example-1-retain-only-for-7-years"></a>Örnek 1: 7 yıl boyunca yalnızca koruma

1. günde, bir kullanıcı yeni bir posta Yammer postası gönderdi.

5. gün, kullanıcı bu iletiyi düzenler.

30. günde kullanıcı geçerli iletiyi siler.

Bekletme sonuçları:

- Özgün ileti için:
    - 5. günde, ileti SubstrateHolds klasörüne kopyalanır ve 1. günden (bekletme süresi) itibaren en az 7 yıl boyunca eBulma araçlarıyla arama yapmak gerekir.

- Geçerli (düzenlenen) ileti için:
    - 30. günde, ileti SubstrateHolds klasörüne taşınır ve burada 1. günden (bekletme süresi) itibaren en az 7 yıl boyunca eBulma araçlarıyla arama yapmak için bu klasörde yer alır.

Kullanıcı belirtilen bekletme süresi sonrasında geçerli iletiyi silmemişse, ileti bekletme süresi içinde değil de SubstrateHolds klasörüne taşınır. Bununla birlikte, artık bekletme süresinin süresi dolsa da ileti en az 1 gün sonra ve normalde 1-7 gün içinde kalıcı olarak silinebilir.

##### <a name="example-2-retain-for-30-days-and-then-delete"></a>Örnek 2: 30 gün süreyle tutma ve silme

1. günde, bir kullanıcı yeni bir posta Yammer postası gönderdi.

10. gün içinde kullanıcı bu iletiyi düzenler.

Kullanıcı başka düzenlemeler de yapmaz ve iletiyi silemez.

Bekletme sonuçları:

- Özgün ileti için:
    - 10. günde ileti SubstrateHolds klasörüne kopyalanır ve eBulma araçlarıyla arama hala devam eder.
    - Bekletme döneminin sonunda (1. günden 30 gün sonra), ileti en az 1 gün içinde genellikle 1-7 gün içinde kalıcı olarak silinir ve eBulma aramalarında geri döndürülemez.

- Geçerli (düzenlenen) ileti için:
    - Bekletme döneminin sonunda (1. günden 30 gün sonra), ileti SubstrateHolds klasörüne taşınır ve 1-7 gün içinde bu klasörde yine eBulma araçlarıyla arama olabilir.
    - Daha sonra ileti, en az 1 gün içinde genellikle 1-7 gün içinde kalıcı olarak silinir ve eBulma aramalarında geri döndürülemez.

##### <a name="example-3-delete-only-after-1-day"></a>Örnek 3: 1 gün sonra yalnızca silme

> [!NOTE]
> Bu yapılandırma ve bekletme işlemlerinin 1-7 günlük kısa bir süre boyunca çalışma süresi nedeniyle, bu bölümde tipik zaman aralıkları içinde olan örnek zamanlamalar yer almaktadır.

1. günde, bir kullanıcı yeni bir posta Yammer postası gönderdi.

Kullanıcı iletiyi düzenlemez veya silemezse, örnek bekletme sonucu:

- 5. Gün (normalde 2. gün bekletme döneminin başlamasının ardından 1-7 gün sonrası):
    - İleti SubstrateHolds klasörüne taşınır ve eBulma araçlarıyla en az 1 gün boyunca orada kalır.

- 9. Gün (SubstrateHolds klasöründe en az 1 gün sonra genellikle 1-7 gün sonra):
    - İleti kalıcı olarak silinir ve eBulma aramalarına geri döndürülemez.

Bu örnekte de olduğu gibi, bir gün sonra iletileri silmek üzere bir bekletme ilkesi yapılandırabilirsiniz, ancak hizmet uyumlu bir silme işlemi sağlamak için birden çok işlemden geçiren bir işlemdir. Sonuç olarak, 1 günden sonra silme eylemi iletinin kalıcı olarak silinmesi 16 gün kadar sürebilir; böylece bu işlem artık eBulma aramalarında döndürülemez.

## <a name="messages-and-external-users"></a>İletiler ve dış kullanıcılar

Varsayılan olarak, kullanıcı iletilerine Yammer bekletme ilkesi, dış kullanıcılar için değil, kuruluşta olan tüm kullanıcılara uygulanır. Dahil edilen kullanıcılar için Düzenle seçeneğini kullanırsanız ve onların hesabını belirtirseniz **, dış** kullanıcılara bekletme ilkesi uygulayabilirsiniz.

Şu anda, Azure B2B konuk kullanıcıları desteklenem değildir.

## <a name="when-a-user-leaves-the-organization"></a>Bir kullanıcı kuruluşdan ayrıldığında 

Bir kullanıcı kuruluştan ayrılırsa ve Microsoft 365 hesabı silinirse, Yammer bekletmeye tabi olan kullanıcı iletileri etkin olmayan bir posta kutusunda depolanır. Bu iletiler, posta kutusu devre dışı kalmadan önce kullanıcıya yerleştirilen tüm bekletme ilkesine tabi kalır ve içerikler eBulma aramalarında kullanılabilir. Daha fazla bilgi için bkz[. Etkin olmayan posta kutuları Exchange Online](inactive-mailboxes-in-office-365.md). 

Kullanıcı dosya depolanmışsa, Yammer ve [klasörlerin](retention-policies-sharepoint.md#when-a-user-leaves-the-organization) eşdeğer bölümüne SharePoint OneDrive.

## <a name="limitations"></a>Sınırlamalar

Yammer bekletme ilkeleri şu anda önizlemededir ve bekletme işlevselliğini en iyi duruma getirme üzerinde sürekli olarak çalışıyoruz. Bu arada, topluluk iletilerini ve kullanıcı iletilerini göndermek üzere bekletmeyi Yammer sınırlamayı da içerir:

- Bu kullanıcı **iletileri konumu** Yammer **Düzenle'yi** seçerek konuk ve posta kutusu olmayan kullanıcıları görebilirler. Bekletme ilkeleri bu kullanıcılar için tasarlanmamalıdır, bu nedenle onları seçmemelisiniz.

## <a name="configuration-guidance"></a>Yapılandırma kılavuzu

Bekletmeyi yeni bir web günlüğünde yapılandırmaya Microsoft 365 [bkz. Bilgi yönetimiyle çalışmaya başlama](get-started-with-information-governance.md).

İlke için bir bekletme ilkesi yapılandırmaya hazırsanız, bkz. Yammer [ilkeleri oluşturma ve yapılandırma](create-retention-policies.md).