---
title: Teams için bekletme hakkında bilgi edinin
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
description: Microsoft Teams için geçerli olan bekletme ilkeleri hakkında bilgi edinin.
ms.openlocfilehash: 68e69f198dfd79c1da210cd8d87144471d83abb7
ms.sourcegitcommit: 5c64002236561000c5bd63c71423e8099e803c2d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/09/2022
ms.locfileid: "65285978"
---
# <a name="learn-about-retention-for-microsoft-teams"></a>Microsoft Teams için bekletme hakkında bilgi edinin

>*[Güvenlik & uyumluluğu için lisanslama yönergelerini Microsoft 365](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

> [!NOTE]
> Teams'da sohbetlerinizin veya iletilerinizin bir bekletme ilkesi tarafından silindiğini belirten bir ileti görüyorsanız bkz. [Bekletme ilkeleriyle ilgili iletileri Teams](https://support.microsoft.com/office/teams-messages-about-retention-policies-c151fa2f-1558-4cf9-8e51-854e925b483b).
> 
> Bu sayfadaki bilgiler, bu bekletme ilkelerini yöneten BT yöneticilerine yöneliktir.

Bu makaledeki bilgiler, Microsoft Teams iletilere özgü bilgiler içerdiğinden [Bekletme hakkında bilgi edinin'i](retention.md) destekler.

Diğer iş yükleri için bkz:

- [SharePoint ve OneDrive için bekletme hakkında bilgi edinin](retention-policies-sharepoint.md)
- [Yammer için bekletme hakkında bilgi edinin](retention-policies-yammer.md)
- [Exchange için bekletme hakkında bilgi edinin](retention-policies-exchange.md)

## <a name="whats-included-for-retention-and-deletion"></a>Saklama ve silmeye dahil olanlar

> [!NOTE]
> Bekletme ilkeleri artık şu anda önizleme aşamasında olan [paylaşılan kanalları](/MicrosoftTeams/shared-channels) destekliyor. Paylaşılan kanallar, saklama ayarlarını üst kanaldan devralır.

Teams sohbet iletileri, kanal iletileri ve özel kanal iletileri, Teams saklama ilkeleri kullanılarak silinebilir ve iletilerdeki metinlere ek olarak, uyumluluk nedenleriyle aşağıdaki öğeler korunabilir: Eklenmiş resimler, tablolar, köprü metni bağlantıları, diğer Teams iletilerine ve dosyalarına bağlantılar ve [kart içeriği](/microsoftteams/platform/task-modules-and-cards/what-are-cards). Sohbet iletileri ve özel kanal iletileri konuşmadaki kişilerin tüm adlarını, kanal iletileri ise ekip adını ve ileti başlığını (varsa) içerir. 

Teams için bekletme ilkelerini kullandığınızda kod parçacıkları, Teams mobil istemciden kaydedilen sesli notlar, küçük resimler, duyuru görüntüleri ve ifade biçiminde diğer kişilerden gelen tepkiler korunmaz.

Teams ile kullandığınız e-postalar ve dosyalar Teams saklama ilkelerine dahil değildir. Bu öğelerin kendi bekletme ilkeleri vardır.

## <a name="how-retention-works-with-microsoft-teams"></a>Bekletme Microsoft Teams ile nasıl çalışır?

Uyumluluk gereksinimlerinizin arka uç depolama ve işlemleri tarafından nasıl karşılandığını ve şu anda Teams uygulamasında görünen iletiler yerine eBulma araçları tarafından doğrulanması gerektiğini anlamak için bu bölümü kullanın.

Teams'da sohbetlerden ve kanal iletilerinden verileri saklamak ve bu sohbetleri ve iletileri silmek için bekletme ilkesi kullanabilirsiniz. Arka planda, bu iletilerden kopyalanan verileri depolamak için Exchange posta kutuları kullanılır. Teams sohbetlerdeki veriler, sohbete dahil edilen her kullanıcının posta kutusunda gizli bir klasörde depolanır ve Teams kanal iletileri için grup posta kutusundaki benzer bir gizli klasör kullanılır. Bu gizli klasörler kullanıcılar veya yöneticiler tarafından doğrudan erişilebilir olacak şekilde tasarlanmamıştır, bunun yerine uyumluluk yöneticilerinin eBulma araçlarıyla arayabileceği verileri depolar.

Bu posta kutuları, RecipientTypeDetails özniteliklerine göre listelenir:

- **UserMailbox**: Bu posta kutuları, bulut tabanlı Teams kullanıcıları için ileti verilerini depolar.
- **MailUser**: Bu posta kutuları [, şirket içi Teams kullanıcıları](search-cloud-based-mailboxes-for-on-premises-users.md) için ileti verilerini depolar.
- **GroupMailbox**: Bu posta kutuları Teams standart kanal için ileti verilerini depolar.
- **SubstrateGroup**: Bu posta kutuları paylaşılan Teams kanal için ileti verilerini depolar.

Teams konferans odaları için kullanılan RoomMailbox gibi diğer posta kutusu türleri, Teams bekletme ilkeleri için desteklenmez.

Teams, tüm iletiler (sohbetler ve kanal iletileri) için birincil depolama alanı olarak Azure destekli bir sohbet hizmeti kullanır. Uyumluluk nedeniyle Teams iletileri silmeniz gerekiyorsa, Teams bekletme ilkeleri iletilerin oluşturulduğu zaman temelinde belirli bir süre sonra silinebilir. İletiler daha sonra uyumluluk işlemleri için depolandıkları Exchange posta kutularından ve temel alınan Azure destekli sohbet hizmeti tarafından kullanılan birincil depolama alanından kalıcı olarak silinir. Temel alınan mimari hakkında daha fazla bilgi için Microsoft Teams [ve](/MicrosoftTeams/security-compliance-overview) özellikle [de Information Protection Mimarisi](/MicrosoftTeams/security-compliance-overview#information-protection-architecture) bölümünde güvenlik ve uyumluluk bölümüne bakın.

Teams sohbetlerden ve kanal iletilerinden gelen bu veriler posta kutularında depolansa da, **Teams kanal iletileri** ve **Teams sohbet konumları** için bir bekletme ilkesi yapılandırmanız gerekir. Teams sohbetler ve kanal iletileri, Exchange kullanıcı veya grup posta kutuları için yapılandırılmış bekletme ilkelerine dahil değildir. Benzer şekilde, Teams saklama ilkeleri depolanan diğer e-posta öğelerini etkilemez.

Bir kullanıcı sohbete eklenirse, kendisiyle paylaşılan tüm iletilerin bir kopyası posta kutusuna gönderilir. Bu iletilerin oluşturulma tarihi yeni kullanıcı için değişmez ve tüm kullanıcılar için aynı kalır.

> [!NOTE]
> Bir kullanıcı, Teams iletileri koruyan etkin bir bekletme ilkesine dahil edilirse ve bu ilkeye dahil edilen bir kullanıcının posta kutusunu silerseniz, posta kutusu Teams verilerini korumak için [etkin olmayan bir posta kutusuna](inactive-mailboxes-in-office-365.md) dönüştürülür. Kullanıcı için bu Teams verilerini saklamanız gerekmiyorsa, kullanıcı hesabını bekletme ilkesinden hariç tutun ve posta kutusunu silmeden önce [bu değişikliğin geçerli olmasını bekleyin](create-retention-policies.md#how-long-it-takes-for-retention-policies-to-take-effect).

Sohbet ve kanal iletileri için bekletme ilkesi yapılandırıldıktan sonra, Exchange hizmetinden bir zamanlayıcı işi, bu Teams iletilerinin depolandığı gizli posta kutusu klasöründeki öğeleri düzenli aralıklarla değerlendirir. Zamanlayıcı işinin çalışması genellikle 1-7 gün sürer. Bu öğelerin saklama süresi dolduğunda, kalıcı olarak silinmeden önce "geçici olarak silinen" öğeleri depolamak için her kullanıcı veya grup posta kutusunda bulunan başka bir gizli klasör olan SubstrateHolds klasörüne taşınırlar. 

İletiler en az 1 gün boyunca SubstrateHolds klasöründe kalır ve silinmeye uygunsa zamanlayıcı işi bir sonraki çalıştırılışında bunları kalıcı olarak siler.

> [!IMPORTANT]
> [İlk bekletme ilkesi](retention.md#the-principles-of-retention-or-what-takes-precedence) nedeniyle ve Teams sohbet ve kanal iletileri Exchange Online posta kutularında depolandığından, posta kutusu başka bir bekletme ilkesinden etkileniyorsa (Exchange uygulanan ilkeler dahil) SubstrateHolds klasöründen kalıcı silme işlemi her zaman askıya alınır  konum), dava tutma, bekletmeyi geciktirme veya posta kutusuna yasal veya araştırıcı nedenlerle eBulma ayrılığı uygulanıp uygulanmaması.
>
> Posta kutusu geçerli bir ayrı tutmada yer alırken, silinen Teams sohbet ve kanal iletileri artık Teams uygulamasında görünmez, ancak eBulma ile bulunabilir olmaya devam eder.

Sohbet ve kanal iletileri için bekletme ilkesi yapılandırıldıktan sonra, içeriğin izlediği yollar bekletme ilkesinin tutulup silineceği, yalnızca korunacak veya yalnızca silineceği durumlarına bağlıdır.

Bekletme ilkesi korunup silinecekse:

![Teams sohbet ve kanal iletileri için bekletme akışı diyagramı.](../media/teamsretentionlifecycle.png)

Diyagramdaki iki yol için:

1. Bekletme süresi boyunca **bir sohbet veya kanal iletisi bir kullanıcı tarafından düzenlenir veya silinirse**, özgün ileti kopyalanır (düzenlenirse) veya SubstrateHolds klasörüne taşınır (silinirse). İleti en az 1 gün boyunca orada depolanır. Bekletme süresi dolduğunda, zamanlayıcı işi bir sonraki çalıştırıldığında (genellikle 1-7 gün arasında) ileti kalıcı olarak silinir.

2. **Bir sohbet veya kanal iletisi kullanıcı tarafından silinmezse** ve düzenleme sonrasında geçerli iletiler için, saklama süresi dolduktan sonra ileti SubstrateHolds klasörüne taşınır. Bu eylem genellikle bitiş tarihinden itibaren 1-7 gün arasında sürer. İleti SubstrateHolds klasöründe olduğunda, en az 1 gün boyunca orada depolanır ve zamanlayıcı işi bir sonraki çalıştırıldığında (genellikle 1-7 gün arasında) ileti kalıcı olarak silinir. 

> [!NOTE]
> Gizli klasörler de dahil olmak üzere posta kutularında depolanan iletiler eKeşif araçları tarafından aranabilir. İletiler SubstrateHolds klasöründen kalıcı olarak silinene kadar eBulma araçları tarafından aranabilir durumda kalır.

Bekletme süresinin süresi dolduğunda ve bir iletiyi SubstrateHolds klasörüne taşıdığında, arka uç Azure sohbet hizmetine bir silme işlemi iletilir ve bu işlem aynı işlemi Teams istemci uygulamasına geçirir. Bu iletişim veya önbelleğe almadaki gecikmeler, kullanıcıların kısa bir süre boyunca bu iletileri Teams uygulamasında görmeye devam etmelerini açıklayabilir.

Azure sohbet hizmetinin bekletme ilkesi nedeniyle silme komutu aldığı bu senaryoda, Teams istemci uygulamasındaki ilgili ileti konuşmadaki tüm kullanıcılar için silinir. Bu kullanıcılardan bazıları başka bir kuruluştan olabilir, saklama süresi daha uzun olan bir bekletme ilkesine sahip olabilir veya bu kullanıcılara hiçbir bekletme ilkesi atanmamış olabilir. Bu kullanıcılar için, iletilerin kopyaları posta kutularında depolanmaya devam eder ve iletiler başka bir bekletme ilkesi tarafından kalıcı olarak silinene kadar eBulma için aranabilir durumda kalır.

> [!IMPORTANT]
> Teams uygulamasında görünen iletiler, uyumluluk gereksinimleri için tutulup tutulmadıklarını veya kalıcı olarak silinip silinmediklerinin doğru bir yansıması değildir.

Bekletme ilkesi yalnızca saklama veya yalnızca silme olduğunda, içeriğin yolları saklama ve silme çeşitlemeleridir.

### <a name="content-paths-for-retain-only-retention-policy"></a>Yalnızca saklama bekletme ilkesi için içerik yolları

1. Bekletme süresi boyunca **bir sohbet veya kanal iletisi bir kullanıcı tarafından düzenlenir veya silinirse**: Özgün ileti kopyalanır (düzenlenirse) veya SubstrateHolds klasörüne taşınır (silinirse) ve en az 1 gün boyunca orada tutulur. Bekletme ilkesi sonsuza kadar korunacak şekilde yapılandırılmışsa, öğe orada kalır. Bekletme ilkesinin bekletme süresi için bir bitiş tarihi varsa ve süresi dolarsa, zamanlayıcı işi bir sonraki çalıştırıldığında (genellikle 1-7 gün arasında) ileti kalıcı olarak silinir.

2. **Sohbet veya kanal iletisi bir kullanıcı tarafından değiştirilmez veya silinmezse** ve bekletme süresi boyunca düzenlemeden sonra geçerli iletiler için: Bekletme süresinden önce ve sonra hiçbir şey olmaz; ileti özgün konumunda kalır.

### <a name="content-paths-for-delete-only-retention-policy"></a>Yalnızca silme bekletme ilkesi için içerik yolları

1. **Sohbet veya kanal iletisi** saklama süresi boyunca bir kullanıcı tarafından düzenlenir veya silinirse: Özgün ileti kopyalanır (düzenlenirse) veya SubstrateHolds klasörüne taşınır (silinirse). İleti en az 1 gün boyunca orada tutulur ve zamanlayıcı işi bir sonraki çalıştırıldığında (genellikle 1-7 gün arasında) kalıcı olarak silinir.

2. Bekletme süresi boyunca **bir sohbet veya kanal iletisi kullanıcı tarafından silinmezse**: Saklama süresinin sonunda ileti SubstrateHolds klasörüne taşınır. Bu eylem genellikle bitiş tarihinden itibaren 1-7 gün arasında sürer. İleti en az 1 gün boyunca orada tutulur ve zamanlayıcı işi bir sonraki çalıştırıldığında (genellikle 1-7 gün arasında) kalıcı olarak silinir.

#### <a name="example-flows-and-timings-for-retention-policies"></a>Bekletme ilkeleri için örnek akışlar ve zamanlamalar

Önceki bölümlerde açıklanan işlemlerin ve zamanlamaların aşağıdaki yapılandırmalara sahip bekletme ilkelerine nasıl uygulandığını görmek için aşağıdaki örnekleri kullanın:

- [Örnek 1: 7 yıl boyunca yalnızca saklama](#example-1-retain-only-for-7-years)
- [Örnek 2: 30 gün boyunca saklama ve ardından silme](#example-2-retain-for-30-days-and-then-delete)
- [Örnek 3: 1 gün sonra yalnızca silme](#example-3-delete-only-after-1-day)

Kalıcı silmeye başvuran tüm örneklerde, [saklama ilkeleri](retention.md#the-principles-of-retention-or-what-takes-precedence) nedeniyle, iletinin öğeyi tutmak için başka bir bekletme ilkesine tabi olması veya eBulma ayrı tutmaya tabi olması durumunda bu eylem askıya alınır.

##### <a name="example-1-retain-only-for-7-years"></a>Örnek 1: 7 yıl boyunca yalnızca saklama

1. günde, kullanıcı bir sohbet veya kanal iletisi oluşturur.

5. günde kullanıcı bu iletiyi düzenler.

30. günde kullanıcı geçerli iletiyi siler.

Bekletme sonuçları:

- Özgün ileti için:
    - 5. günde, ileti SubstrateHolds klasörüne kopyalanır ve burada eBulma araçlarıyla 1. günden itibaren en az 7 yıl boyunca (saklama süresi) aranabilir.

- Geçerli (düzenlenmiş) ileti için:
    - 30. günde, ileti SubstrateHolds klasörüne taşınır ve burada eBulma araçlarıyla 1. günden itibaren en az 7 yıl boyunca (saklama süresi) aranabilir.

Kullanıcı belirtilen saklama süresinden sonra geçerli iletiyi silmişse, saklama süresi yerine yine de SubstrateHolds klasörüne taşınır. Ancak, artık saklama süresi doldu, ileti en az 1 gün sonra ve daha sonra genellikle 1-7 gün içinde kalıcı olarak silinir.

##### <a name="example-2-retain-for-30-days-and-then-delete"></a>Örnek 2: 30 gün boyunca saklama ve ardından silme

1. günde, kullanıcı bir sohbet veya kanal iletisi oluşturur.

10. günde kullanıcı bu iletiyi düzenler.

Kullanıcı başka düzenlemeler yapmaz ve iletiyi silmez.

Bekletme sonuçları:

- Özgün ileti için:
    - 10. günde, ileti SubstrateHolds klasörüne kopyalanır ve burada eBulma araçlarıyla aranabilir.
    - Saklama süresinin sonunda (1. günden itibaren 30 gün), ileti genellikle en az 1 gün sonra 1-7 gün içinde kalıcı olarak silinir ve ardından eBulma aramalarıyla döndürülemez.

- Geçerli (düzenlenmiş) ileti için:
    - Saklama süresinin sonunda (1. günden itibaren 30 gün), ileti genellikle 1-7 gün içinde SubstrateHolds klasörüne taşınır ve burada eBulma araçlarıyla aranabilir.
    - İleti daha sonra genellikle en az 1 gün sonra 1-7 gün içinde kalıcı olarak silinir ve ardından eBulma aramalarıyla döndürülemez.

##### <a name="example-3-delete-only-after-1-day"></a>Örnek 3: 1 gün sonra yalnızca silme

> [!NOTE]
> Bu yapılandırmanın kısa bir günlük süresi ve 1-7 günlük bir süre içinde çalışan bekletme işlemleri nedeniyle, bu bölümde tipik zaman aralıkları içinde yer alan örnek zamanlamalar gösterilir.

1. günde, kullanıcı bir sohbet veya kanal iletisi oluşturur.

Kullanıcı iletiyi düzenlemez veya silmezse örnek bekletme sonucu:

- 5. gün (genellikle 2. günde saklama süresinin başlamasından 1-7 gün sonra):
    - İleti SubstrateHolds klasörüne taşınır ve eBulma araçlarıyla aranabileceği en az 1 gün boyunca orada kalır.

- 9. gün (genellikle SubstrateHolds klasöründe en az 1 gün sonra 1-7 gün):
    - İleti kalıcı olarak silinir ve eBulma aramalarıyla döndürülemez.

Bu örnekte gösterildiği gibi, yalnızca bir gün sonra iletileri silmek için bir bekletme ilkesi yapılandırabilirsiniz ancak hizmet, uyumlu bir silme işlemi sağlamak için birden çok işlemden geçer. Sonuç olarak, 1 gün sonra gerçekleştirilen silme eylemi, eBulma aramalarında artık döndürülmemesi için iletinin kalıcı olarak silinmesi 16 gün sürebilir.

## <a name="skype-for-business-and-teams-interop-chats"></a>birlikte çalışma sohbetlerini Skype Kurumsal ve Teams

Skype Kurumsal sohbet Teams geldiğinde, Teams sohbet yazışmasında bir ileti olur ve uygun posta kutusuna gönderilir. Teams bekletme ilkeleri, Teams iş parçacığından gelen bu iletilere uygulanır. 

Ancak, konuşma geçmişi Skype Kurumsal için ve Skype Kurumsal istemci tarafından geçmişin bir posta kutusuna kaydedildiği açıksa, bu sohbet verileri bir Teams bekletme ilkesi tarafından işlenmez. Bu içerik için Skype Kurumsal için yapılandırılmış bir bekletme ilkesi kullanın.

## <a name="meetings-and-external-users"></a>Toplantılar ve dış kullanıcılar

Kanal toplantı iletileri kanal iletileriyle aynı şekilde depolanır, bu nedenle bu veriler için bekletme ilkenizi yapılandırırken **kanal iletilerinin konumunu Teams** seçin.

Hazırlıksız ve zamanlanmış toplantı iletileri grup sohbeti iletileriyle aynı şekilde depolanır, bu nedenle bu veriler için bekletme ilkenizi yapılandırırken **Teams sohbetler** konumunu seçin.

Kuruluşunuzun barındır olduğu bir toplantıya dış kullanıcılar dahil edildiğinde:

- Dış kullanıcı kiracınızda bir konuk hesabı kullanarak katılırsa, toplantıdan gelen iletiler hem kullanıcılarınızın posta kutusunda hem de konuk hesabına verilen gölge posta kutusunda depolanır. Ancak, saklama ilkeleri, konumun tamamı için bir bekletme ilkesine dahil olarak bildirilse de (bazen "kuruluş genelinde ilke" olarak da bilinir) gölge posta kutuları için desteklenmez.

- Dış kullanıcı başka bir Microsoft 365 kuruluştaki bir hesabı kullanarak katılırsa, bekletme ilkeleriniz bu kullanıcının başka bir kiracıdaki posta kutusunda depolandığından iletileri silemez. Ancak aynı toplantı için bekletme ilkeleriniz kullanıcılarınız için iletileri silebilir.

## <a name="when-a-user-leaves-the-organization"></a>Kullanıcı kuruluştan ayrıldığında 

Exchange Online'de posta kutusu olan bir kullanıcı kuruluşunuzdan ayrılırsa ve Microsoft 365 hesabı silinirse, bekletmeye tabi olan sohbet iletileri etkin olmayan bir posta kutusunda depolanır. Sohbet iletileri, posta kutusu devre dışı bırakılmadan önce kullanıcıya yerleştirilen bekletme ilkesine tabi kalır ve içerik eBulma aramasında kullanılabilir. Daha fazla bilgi için bkz. [Exchange Online'da etkin olmayan posta kutuları](inactive-mailboxes-in-office-365.md). 

Kullanıcı Teams'da herhangi bir dosya depoladıysa, SharePoint ve OneDrive için [eşdeğer bölüme](retention-policies-sharepoint.md#when-a-user-leaves-the-organization) bakın.

## <a name="configuration-guidance"></a>Yapılandırma kılavuzu

Microsoft 365'de saklamayı yapılandırma konusunda yeniyseniz bkz. [Veri yaşam döngüsü yönetimiyle Kullanmaya başlayın](get-started-with-data-lifecycle-management.md).

Teams için bekletme ilkesi yapılandırmaya hazırsanız bkz. [Bekletme ilkeleri oluşturma ve yapılandırma](create-retention-policies.md).
