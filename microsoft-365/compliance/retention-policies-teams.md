---
title: Müşteri için bekletme hakkında bilgi Teams
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
description: Bu ilkelere uygulanacak bekletme ilkeleri hakkında Microsoft Teams.
ms.openlocfilehash: f2b3b5a61eabbffc50da34b14baa20e025b8da0f
ms.sourcegitcommit: a4729532278de62f80f2160825d446f6ecd36995
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/31/2022
ms.locfileid: "64568532"
---
# <a name="learn-about-retention-for-microsoft-teams"></a>Müşteri için bekletme hakkında bilgi Microsoft Teams

>*[Microsoft 365 uyumluluğu için lisans & kılavuzu.](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance)*

> [!NOTE]
> Bir e-postada sohbet Teams iletilerinizin bekletme ilkesi tarafından silinmiş olduğunu haber verdiyseniz, bkz. [Bekletme ilkeleri Teams iletileri gönderme](https://support.microsoft.com/office/teams-messages-about-retention-policies-c151fa2f-1558-4cf9-8e51-854e925b483b).
> 
> Bu sayfada bilgiler, bu bekletme ilkelerini yöneten IT yöneticilerine yöneliktir.

Bu makaledeki bilgiler Bekletme hakkında bilgi [edinebilirsiniz](retention.md), çünkü bu iletileri saklamaya özgü Microsoft Teams vardır.

Diğer iş yükleri için bkz:

- [E-SharePoint ve OneDrive](retention-policies-sharepoint.md)
- [Müşteri için bekletme hakkında bilgi Yammer](retention-policies-yammer.md)
- [Müşteri için bekletme hakkında bilgi Exchange](retention-policies-exchange.md)

## <a name="whats-included-for-retention-and-deletion"></a>Bekletme ve silme işlemi için neler dahildir?

> [!NOTE]
> Bekletme ilkeleri artık [önizlemede olan](/MicrosoftTeams/shared-channels) paylaşılan kanalları desteklemektedir. Tüm paylaşılan kanallar, bekletme ayarlarını üst kanaldan devralır.

Teams sohbetleri, kanal iletileri ve özel kanal iletileri Teams için bekletme ilkeleri kullanılarak silinebilir ve uyumluluk nedenlerinden dolayı aşağıdaki öğeler de korunabilirsiniz: Eklenmiş resimler, tablolar, köprü metni bağlantıları, diğer Teams iletilerine ve dosyalarına bağlantılar ve kart [içeriği.](/microsoftteams/platform/task-modules-and-cards/what-are-cards) Sohbet iletileri ve özel kanal iletileri görüşmede yer alan kişilerin tüm adlarını, kanal iletileri ise ekip adını ve ileti başlığını (varsa) içerir. 

Kod parçacıkları, Teams mobil istemcisinden kayıtlı sesli notlar, küçük resimler, duyuru resimleri ve ifade şeklinde diğer kişi ifadeleri gelen tepkiler, Teams için bekletme ilkeleri kullanılırken korunur.

E-postalar ve birlikte Teams dosyalar bu dosyalarda yer alan e-postalar sizin için bekletme Teams. Bu öğelerin kendi bekletme ilkeleri vardır.

## <a name="how-retention-works-with-microsoft-teams"></a>Bekletme, alanla birlikte Microsoft Teams

Bu bölümü kullanarak, uyumluluk gereksinimlerinizin arka uç depolama ve işlemlerle nasıl karşılandığından emin olun ve o anda Teams uygulamasında görünen iletiler tarafından değil eBulma araçları tarafından doğrulanmalıdır.

Bir bekletme ilkesi kullanarak bir e-postada sohbetlerden ve kanal iletilerinden Teams bu sohbetleri ve iletileri silebilirsiniz. Sahne gerisinde, Exchange kutuları bu iletilerden kopyalanan verileri depolamak için kullanılır. Sohbetler Teams, sohbette yer alan her kullanıcının posta kutusunda gizli bir klasörde depolanır ve grup posta kutusunda da benzer bir gizli klasör kanal iletileri Teams kullanılır. Bu gizli klasörler, kullanıcılar veya yöneticiler için doğrudan erişilebilir olacak şekilde tasarlanmasa da, uyumluluk yöneticilerinin eBulma araçlarıyla arama yapmak için depolayamları yerine verileri depolar.

Bu posta kutuları RecipientTypeDetails özniteliğine göre listelenir:

- **UserMailbox**: Bu posta kutuları, bulut tabanlı kullanıcıların ileti verilerini Teams depolar.
- **MailUser**: Bu posta kutuları, şirket içi kullanıcıların ileti [Teams depolar](search-cloud-based-mailboxes-for-on-premises-users.md).
- **GroupMailbox**: Bu posta kutuları, standart kanalların ileti Teams depolar.
- **Alt Grup Grubu: Bu** posta kutuları, paylaşılan kanalların ileti Teams depolar.

Konferans odalarında kullanılan RoomMailbox gibi diğer posta kutusu Teams, bekletme ilkeleri Teams desteklemez.

Teams, tüm iletiler (sohbetler ve kanal iletileri) için birincil depolama alanı olarak Azure destekli bir sohbet hizmetini kullanır. Uyumluluk nedenlerinden dolayı Teams iletileri silmeniz gerekirse, Teams için bekletme ilkeleri, oluşturulduklarına bağlı olarak belirtilen bir sürenin ardından iletileri silebilir. İletiler, uyumluluk işlemleri için Exchange ilgili posta kutularından ve Azure destekli temel sohbet hizmeti tarafından kullanılan birincil depolamadan kalıcı olarak silinir. Temel mimari hakkında daha fazla bilgi için Temel mimari [hakkında](/MicrosoftTeams/security-compliance-overview) daha fazla bilgi için Microsoft Teams Uyumluluk ve Uyumluluk [Information Protection](/MicrosoftTeams/security-compliance-overview#information-protection-architecture) bakın.

Bu veriler Teams sohbetlerden ve kanal iletilerinden gelen veriler posta kutularında depolanıyor olsa da, bu kanal iletilerinin ve kanal iletilerinin konumlarını nasıl Teams için **Teams** yapılandırmanız gerekir. Teams sohbetler ve kanal iletileri, kullanıcı veya grup posta kutuları için Exchange ilkelere dahil değildir. Benzer şekilde, e-posta Teams saklama ilkeleri de depolanan diğer e-posta öğelerini etkilemez.

Kullanıcı sohbete eklenirse, bu kullanıcıyla paylaşılan tüm iletilerin bir kopyası posta kutusuna eklenir. Bu iletilerin oluşturulma tarihi yeni kullanıcı için değişmez ve tüm kullanıcılar için aynı kalır.

> [!NOTE]
> Kullanıcı, Teams iletilerini alıkoyan etkin bir bekletme ilkesinde yer alıyorsa ve bu ilkeye dahil olan bir kullanıcının posta kutusunu silerseniz, posta kutusu etkin olmayan bir posta kutusuna dönüştürülür ve bu durumda Teams [](inactive-mailboxes-in-office-365.md) korunur. Kullanıcının bu veri verilerini saklamanız Teams, bekletme ilkesinden kullanıcı hesabını dışlayın ve posta kutusunu smeden önce bu değişikliğin geçerliksini bekleyin.[](create-retention-policies.md#how-long-it-takes-for-retention-policies-to-take-effect)

Sohbet ve kanal iletileri için bir bekletme ilkesi yapılandırıldığında, Exchange hizmetinin zamanlayıcı işi bu iletilerin depolandığı gizli posta kutusu klasöründeki Teams düzenli olarak değerlendirir. Zamanlayıcı işinin çalışması normalde 1-7 gün sürer. Bu öğelerin bekletme süresi dolduğunda, kalıcı olarak silinmeden önce her kullanıcı veya grup posta kutusunda "geçici silinmiş" öğeleri depolamak için kullanılan başka bir gizli klasör olan SubstrateHolds klasörüne taşınır. 

İletiler en az 1 gün boyunca SubstrateHolds klasöründe kalır ve bu süreölçer işi bir sonraki kez çalıştırıca bunları kalıcı olarak siler.

> [!IMPORTANT]
> İlk bekletme [ilkesinden](retention.md#the-principles-of-retention-or-what-takes-precedence) dolayı ve Teams sohbet ve kanal iletileri Exchange Online posta kutularında depolandığı için, posta kutusu başka bir bekletme ilkesinden etkileniyorsa (posta kutusuna uygulanan ilkeler de dahil olmak üzere) SubstrateHolds klasöründen kalıcı olarak silinmesi Exchange  konumu), mahkeme nedeniyle tutma, gecikme nedeniyle veya yasal veya soruşturma nedeniyle posta kutusuna eBulma tutma uygulanırsa.
>
> Posta kutusu geçerli bir tutma kapsamındayken, Teams silinen sohbet ve kanal iletileri Teams uygulamasında görünmez ancak eKbulma ile keşfedilebilir olmaya devam eder.

Bir bekletme ilkesi sohbet ve kanal iletileri için yapılandırıldığında, içeriğin gereklere bakıldığında, bekletme ilkesi için bekletme ve ardından silme, yalnızca koruma veya yalnızca silme gibi nedenler geçerli olur.

Bekletme ilkesi korunarak silinecek olduğunda:

![Sohbet ve kanal iletileri için Teams akışı diyagramı.](../media/teamsretentionlifecycle.png)

Diyagramda iki yol için:

1. **Bir sohbet** veya kanal iletisi, bekletme süresince kullanıcı tarafından düzenlenmiş veya silinmişse, özgün ileti SubstrateHolds klasörüne kopyalanır (düzenlenmişse) veya taşınır (silinmişse). İleti en az 1 gün boyunca orada depolanır. Bekletme süresi sona erdiğinde, zamanlayıcı işinin bir sonraki çalıştırısı (normalde 1-7 gün arasında) bu ileti kalıcı olarak silinir.

2. **Bir sohbet veya kanal** iletisi kullanıcı tarafından silinmezse ve düzenleme sonrasında geçerli iletiler için bekletme süresi dolduktan sonra ileti SubstrateHolds klasörüne taşınır. Bu işlem genellikle son kullanma tarihinden 1-7 gün arasında sürer. İleti SubstrateHolds klasöründe olduğunda, en az 1 gün süreyle orada depolanır ve zamanlayıcı işinin bir sonraki çalıştır mesajını (normalde 1-7 gün arasında) kalıcı olarak silinir. 

> [!NOTE]
> Gizli klasörler dahil olmak üzere posta kutularında depolanan iletiler eBulma araçlarıyla aranabilir. İletiler SubstrateHolds klasöründen kalıcı olarak silinene kadar, eBulma araçları tarafından aranabilir durumda kalırlar.

Bekletme süresi dolduğunda ve bir iletiyi SubstrateHolds klasörüne taşırken, bir silme işlemi Arka uç Azure sohbet hizmetine iletilebilir ve bu da aynı işlemi Teams istemci uygulamasına taşır. Bu iletişim veya önbelleğe almadaki gecikmeler, kısa bir süre için kullanıcılar Teams uygulamaları içinde bu iletileri görmeye devam eder.

Azure sohbet hizmetinin bir bekletme ilkesi nedeniyle bir silme komutu aldığı bu senaryoda, Teams istemci uygulamasındaki ilgili ileti konuşmanın tüm kullanıcıları için silinir. Bu kullanıcılardan bazıları başka bir kuruluştan olabilir, bekletme süresi daha uzun olan veya bu kullanıcılara atanmış bekletme ilkesi yok olabilir. Bu kullanıcılar için, iletilerin kopyaları yine posta kutularında depolanır ve başka bir bekletme ilkesi tarafından kalıcı olarak silinene kadar eKbulma için aranabilir durumda kalır.

> [!IMPORTANT]
> İletiler, Teams gereksinimleri için korunsa da kalıcı olarak silinse de doğru bir yansıma değildir.

Bekletme ilkesi yalnızca saklama veya yalnızca silme olduğunda, içeriğin yolları koruma ve silmenin bir çeşitletir.

### <a name="content-paths-for-retain-only-retention-policy"></a>Yalnızca bekletme ilkesi için içerik yolları

1.  Bir sohbet veya kanal iletisi, bekletme süresince kullanıcı tarafından düzenlenmiş veya silinmişse: Özgün ileti SubstrateHolds klasörüne kopyalanır (düzenlenmişse) veya taşınır (silinirse) ve en az 1 gün boyunca orada korunur. Bekletme ilkesi sonsuza kadar korunacak şekilde yapılandırılmışsa, öğe orada kalır. Bekletme ilkesi, bekletme süresi için bir bitiş tarihine sahipse ve süresi dolsa, süreölçer işini bir sonraki çalıştıracak sefer (normalde 1-7 gün arasında) ileti kalıcı olarak silinir.

2. **Sohbet veya kanal iletisi, bekletme** süresi boyunca kullanıcı tarafından değiştirilmez veya silinmez ya da mevcut iletiler için silinmezse: Bekletme süresi öncesinde ve sonrasında hiçbir şey olmaz; İleti özgün konumda kalır.

### <a name="content-paths-for-delete-only-retention-policy"></a>Yalnızca silme bekletme ilkesi için içerik yolları

1. **Sohbet veya kanal** iletisi, bekletme süresince bir kullanıcı tarafından düzenlenmiş veya silinmişse: Orijinal ileti SubstrateHolds klasörüne kopyalanır (düzenlenmişse) veya taşınır (silinmişse). İleti en az 1 gün boyunca orada korunur ve zamanlayıcı işini bir sonraki çalıştıracak sefer (normalde 1-7 gün arasında) kalıcı olarak silinir.

2. **Bir sohbet veya kanal** iletisi, bekletme süresi boyunca kullanıcı tarafından silinmezse: Bekletme döneminin sonunda ileti SubstrateHolds klasörüne taşınır. Bu işlem genellikle son kullanma tarihinden 1-7 gün arasında sürer. İleti en az 1 gün boyunca orada korunur ve zamanlayıcı işini bir sonraki çalıştıracak sefer (normalde 1-7 gün arasında) kalıcı olarak silinir.

#### <a name="example-flows-and-timings-for-retention-policies"></a>Bekletme ilkeleri için örnek akışlar ve zamanlamalar

Önceki bölümlerde açıklanan işlemlerin ve zamanlamaların aşağıdaki yapılandırmalara sahip bekletme ilkelerine nasıl uygulanıyor olduğunu görmek için aşağıdaki örnekleri kullanın:

- [Örnek 1: 7 yıl boyunca yalnızca koruma](#example-1-retain-only-for-7-years)
- [Örnek 2: 30 gün süreyle tutma ve silme](#example-2-retain-for-30-days-and-then-delete)
- [Örnek 3: 1 gün sonra yalnızca silme](#example-3-delete-only-after-1-day)

Kalıcı silmeye başvuran tüm örneklerde, bekletme ilkeleri [nedeniyle, ileti](retention.md#the-principles-of-retention-or-what-takes-precedence) öğeyi alıkoyacak başka bir bekletme ilkesine tabi olursa veya öğe eBulma bekletmeye tabi olursa bu eylem askıya alınır.

##### <a name="example-1-retain-only-for-7-years"></a>Örnek 1: 7 yıl boyunca yalnızca koruma

1. gün içinde kullanıcı bir sohbet veya kanal iletisi oluşturur.

5. gün, kullanıcı bu iletiyi düzenler.

30. günde kullanıcı geçerli iletiyi siler.

Bekletme sonuçları:

- Özgün ileti için:
    - 5. günde, ileti SubstrateHolds klasörüne kopyalanır ve 1. günden (bekletme süresi) itibaren en az 7 yıl boyunca eBulma araçlarıyla arama yapmak gerekir.

- Geçerli (düzenlenen) ileti için:
    - 30. günde, ileti SubstrateHolds klasörüne taşınır ve burada 1. günden (bekletme süresi) itibaren en az 7 yıl boyunca eBulma araçlarıyla arama yapmak için bu klasörde yer alır.

Kullanıcı belirtilen bekletme süresi sonrasında geçerli iletiyi silmemişse, ileti bekletme süresi içinde değil de SubstrateHolds klasörüne taşınır. Bununla birlikte, artık bekletme süresinin süresi dolsa da ileti en az 1 gün sonra ve normalde 1-7 gün içinde kalıcı olarak silinebilir.

##### <a name="example-2-retain-for-30-days-and-then-delete"></a>Örnek 2: 30 gün süreyle tutma ve silme

1. gün içinde kullanıcı bir sohbet veya kanal iletisi oluşturur.

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

1. gün içinde kullanıcı bir sohbet veya kanal iletisi oluşturur.

Kullanıcı iletiyi düzenlemez veya silemezse, örnek bekletme sonucu:

- 5. Gün (normalde 2. gün bekletme döneminin başlamasının ardından 1-7 gün sonrası):
    - İleti SubstrateHolds klasörüne taşınır ve eBulma araçlarıyla en az 1 gün boyunca orada kalır.

- 9. Gün (SubstrateHolds klasöründe en az 1 gün sonra genellikle 1-7 gün sonra):
    - İleti kalıcı olarak silinir ve eBulma aramalarına geri döndürülemez.

Bu örnekte de olduğu gibi, bir gün sonra iletileri silmek üzere bir bekletme ilkesi yapılandırabilirsiniz, ancak hizmet uyumlu bir silme işlemi sağlamak için birden çok işlemden geçiren bir işlemdir. Sonuç olarak, 1 günden sonra silme eylemi iletinin kalıcı olarak silinmesi 16 gün kadar sürebilir; böylece bu işlem artık eBulma aramalarında döndürülemez.

## <a name="skype-for-business-and-teams-interop-chats"></a>Skype Kurumsal birlikte Teams sohbetleri hazırlama ve birlikte çalışma

Sohbet Skype Kurumsal sohbet Teams, sohbet ileti dizisinde Teams bir iletiye dönüşer ve uygun posta kutusuna alın alır. Teams bekletme ilkeleri, ilk ileti dizisinde yer alan Teams uygulanır. 

Öte yandan, Skype Kurumsal için ve Skype Kurumsal istemcisi tarafında konuşma geçmişi bir posta kutusuna kayded ediliyorsa, bu sohbet verileri Teams bekletme ilkesi tarafından işlemez. Bu içerik için, bu içerik için yapılandırılmış bir bekletme Skype Kurumsal.

## <a name="meetings-and-external-users"></a>Toplantılar ve dış kullanıcılar

Kanal toplantı iletileri, kanal iletileriyle aynı şekilde depolanır; dolayısıyla bekletme **ilkenizi yapılandırarak bu Teams** ilgili kanal iletileri konumunu seçin.

Plansız ve zamanlanmış toplantı iletileri, grup sohbeti iletileriyle aynı şekilde depolanır; dolayısıyla bekletme ilkenizi yapılandırarak bu veriler Teams  sohbetler konumunu seçin.

Dış kullanıcılar, kuruluşun barındır olduğu bir toplantıya dahil edildiklerde:

- Bir dış kullanıcı kiracınıza konuk hesabı kullanarak katılırsa, toplantıdan gelen tüm iletiler hem kullanıcı posta kutunuzda hem de konuk hesabına verilen gölge posta kutusunda depolanır. Bununla birlikte, bekletme ilkeleri tüm konumun bekletme ilkesine dahil olarak bildiriliyor olsalar da (bazen "kuruluş genelinde ilke" olarak da bilinir) gölge posta kutularında desteklanmaz.

- Bir dış kullanıcı başka bir Microsoft 365 kuruluşun hesabı kullanarak katılırsa, bekletme ilkeleriniz bu kullanıcının iletilerini silemez çünkü bunlar o kullanıcının posta kutusunda başka bir kiracıda depolanır. Bununla birlikte aynı toplantıda, bekletme ilkeleriniz kullanıcılarınız için iletileri silebilir.

## <a name="when-a-user-leaves-the-organization"></a>Bir kullanıcı kuruluşdan ayrıldığında 

Exchange Online'da posta kutusu olan bir kullanıcı kuruluştan ayrılırsa ve Microsoft 365 hesabı silinirse, bekletmeye tabi sohbet iletileri etkin olmayan bir posta kutusunda depolanır. Sohbet iletileri, posta kutusu devre dışı olmadan önce kullanıcıya yerleştirilen tüm bekletme ilkesine tabi kalır ve içerikler eBulma aramalarında kullanılabilir. Daha fazla bilgi için bkz[. Etkin olmayan posta kutuları Exchange Online](inactive-mailboxes-in-office-365.md). 

Kullanıcı dosya depolanmışsa, Teams ve [klasörlerin](retention-policies-sharepoint.md#when-a-user-leaves-the-organization) eşdeğer bölümüne SharePoint OneDrive.

## <a name="configuration-guidance"></a>Yapılandırma kılavuzu

Bekletmeyi yeni bir web günlüğünde yapılandırmaya Microsoft 365 bkz[. Kullanmaya başlayın yönetimiyle birlikte düzenleme](get-started-with-information-governance.md).

İlke için bekletme ilkesi yapılandırmaya hazırsanız, bkz. Teams [oluşturma ve yapılandırma](create-retention-policies.md).