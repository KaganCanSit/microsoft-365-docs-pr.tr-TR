---
title: Yammer için bekletme hakkında bilgi edinin
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
description: Yammer için geçerli olan bekletme ilkeleri hakkında bilgi edinin.
ms.openlocfilehash: d2703947d2cebc5818793362e55b8eae9cec2ed8
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66639632"
---
# <a name="learn-about-retention-for-yammer"></a>Yammer için bekletme hakkında bilgi edinin

>*[Güvenlik & uyumluluğu için Microsoft 365 lisanslama kılavuzu](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

Bu makaledeki bilgiler, Yammer'a özgü bilgiler içerdiğinden [Bekletme hakkında bilgi edinin'e](retention.md) ek olarak ek olarak verilmiştir.

Diğer iş yükleri için bkz:

- [SharePoint ve OneDrive için bekletme hakkında bilgi edinin](retention-policies-sharepoint.md)
- [Microsoft Teams için bekletme hakkında bilgi edinin](retention-policies-teams.md)
- [Exchange için bekletme hakkında bilgi edinin](retention-policies-exchange.md)

## <a name="whats-included-for-retention-and-deletion"></a>Saklama ve silmeye dahil olanlar

Yammer kullanıcı iletileri ve topluluk iletileri Yammer için bekletme ilkeleri kullanılarak silinebilir ve bu iletilerdeki metne ek olarak, uyumluluk nedenleriyle aşağıdaki öğeler korunabilir: Köprü metni bağlantıları ve diğer Yammer iletilerine bağlantılar.

> [!NOTE]
> Aşağıdaki bölümde açıklandığı gibi, kullanıcı iletileri tek bir kullanıcı için özel iletiler ve bu kullanıcıyla ilişkilendirilmiş tüm topluluk iletilerini içerir.

Kullanıcı iletileri konuşmadaki kişilerin tüm adlarını, topluluk iletileri ise topluluk adını ve ileti başlığını (varsa) içerir.

Yammer için bekletme ilkelerini kullandığınızda ifade biçimindeki diğer kişilerden gelen tepkiler korunmaz.

Yammer ile kullandığınız dosyalar Yammer için bekletme ilkelerine dahil değildir. Bu öğelerin kendi bekletme ilkeleri vardır.

## <a name="how-retention-works-with-yammer"></a>Yammer ile bekletme nasıl çalışır?

Uyumluluk gereksinimlerinizin arka uç depolama ve işlemleri tarafından nasıl karşılandığını ve yammer uygulamasında şu anda görünen iletiler yerine eBulma araçları tarafından doğrulanması gerektiğini anlamak için bu bölümü kullanın.

Yammer'da topluluk iletilerinden ve kullanıcı iletilerinden verileri saklamak ve bu iletileri silmek için bekletme ilkesi kullanabilirsiniz. Arka planda Exchange posta kutuları, bu iletilerden kopyalanan verileri depolamak için kullanılır. Yammer kullanıcı iletilerindeki veriler, kullanıcı iletisine dahil edilen her kullanıcının posta kutusunda gizli bir klasörde depolanır ve topluluk iletileri için grup posta kutusundaki benzer bir gizli klasör kullanılır.

Topluluk iletilerinin kopyaları, kullanıcılardan @ bahsettiklerinde veya kullanıcıya bir yanıtı bildirdiklerinde kullanıcı posta kutularının gizli klasöründe de depolanabilir. Bu iletiler bir topluluk iletisi olarak başlasa da, Yammer kullanıcı iletileri için bir bekletme ilkesi genellikle topluluk iletilerinin kopyalarını içerir. Sonuç olarak, kullanıcı iletileri özel iletiyle sınırlı değildir.

Bu gizli klasörler, kullanıcılar veya yöneticiler tarafından doğrudan erişilebilir olacak şekilde tasarlanmamıştır, bunun yerine uyumluluk yöneticilerinin eBulma araçlarıyla arayabileceği verileri depolar.

Exchange'de depolanmış olsalar bile, Yammer iletileri yalnızca **Yammer topluluk iletileri** veya **Yammer kullanıcı iletileri** konumları için yapılandırılmış bir bekletme ilkesine dahil edilir.

> [!NOTE]
> Bir kullanıcı Yammer verilerini koruyan etkin bir bekletme ilkesine dahil edilirse ve bu ilkeye dahil edilen bir kullanıcının posta kutusunu silerseniz, Yammer verilerini korumak için posta kutusu [etkin olmayan posta kutusuna](inactive-mailboxes-in-office-365.md) dönüştürülür. Kullanıcı için bu Yammer verilerini saklamanız gerekmiyorsa, posta kutusunu silmeden önce kullanıcı hesabını bekletme ilkesinden hariç tutun.

Yammer iletileri için bir bekletme ilkesi yapılandırıldıktan sonra, Exchange hizmetinden bir zamanlayıcı işi bu Yammer iletilerinin depolandığı gizli klasördeki öğeleri düzenli aralıklarla değerlendirir. Zamanlayıcı işinin çalıştırılması yedi güne kadar sürer. Bu öğelerin saklama süresi dolduğunda, kalıcı olarak silinmeden önce "geçici olarak silinen" öğeleri depolamak için her kullanıcı veya grup posta kutusunda yer alan gizli bir klasör olan SubstrateHolds klasörüne taşınırlar.

> [!IMPORTANT]
> [İlk saklama ilkesi](retention.md#the-principles-of-retention-or-what-takes-precedence) nedeniyle ve Yammer iletileri Exchange Online posta kutularında depolandığından, posta kutusu aynı konum, Dava Bekletme, gecikme bekletmesi için başka bir Yammer bekletme ilkesinden etkileniyorsa veya posta kutusuna yasal veya araştırıcı nedenlerle eBulma ayrılığı uygulandığında SubstrateHolds klasöründen kalıcı silme işlemi her zaman askıya alınır.
>
> Posta kutusu geçerli bir ayrı tutmaya dahil edilmiş olsa da, silinen Yammer iletileri artık Yammer'da görünmez, ancak eBulma ile bulunabilir olmaya devam eder.

Yammer iletileri için bir bekletme ilkesi yapılandırıldıktan sonra, içeriğin izlediği yollar, bekletme ilkesinin tutulup silineceği, yalnızca korunup tutulmayacağı veya yalnızca silineceği durumuna bağlıdır.

Bekletme ilkesi korunup silinecekse:

![Yammer iletileri için bekletme akışı diyagramı.](../media/yammerretentionlifecycle.png)

Diyagramdaki iki yol için:

1. Yammer iletisi saklama süresi boyunca kullanıcı tarafından **düzenlenir veya silinirse**, özgün ileti hemen kopyalanır (düzenlenirse) veya SubstrateHolds klasörüne taşınır (silinirse). İleti, saklama süresi dolana kadar orada depolanır ve ardından ileti hemen kalıcı olarak silinir.

2. **Yammer iletisi silinmezse** ve düzenleme sonrasında geçerli iletiler için, saklama süresi dolduktan sonra ileti SubstrateHolds klasörüne taşınır. Bu eylem, bitiş tarihinden itibaren yedi güne kadar sürer. İleti SubstrateHolds klasöründe olduğunda, hemen kalıcı olarak silinir. 

> [!NOTE]
> SubstrateHolds klasöründeki iletiler eBulma araçları tarafından aranabilir. İletiler SubstrateHolds klasöründen kalıcı olarak silinene kadar eBulma araçları tarafından aranabilir durumda kalır.

Bekletme süresinin süresi dolduğunda ve bir iletiyi SubstrateHolds klasörüne taşıdığında, Yammer hizmetine bir silme işlemi iletilir ve bu işlem aynı işlemi Yammer istemci uygulamasına geçirir. Bu iletişim veya önbelleğe almadaki gecikmeler, kullanıcıların kısa bir süre boyunca yammer uygulamasında bu iletileri görmeye devam etmelerini açıklayabilir.

Yammer hizmetinin bekletme ilkesi nedeniyle silme komutu aldığı bu senaryoda, Yammer uygulamasındaki ilgili ileti konuşmadaki tüm kullanıcılar için silinir. Bu kullanıcılardan bazıları başka bir kuruluştan olabilir, saklama süresi daha uzun olan bir bekletme ilkesine sahip olabilir veya bu kullanıcılara hiçbir bekletme ilkesi atanmamış olabilir. Bu kullanıcılar için, iletilerin kopyaları posta kutularında depolanmaya devam eder ve iletiler başka bir bekletme ilkesi tarafından kalıcı olarak silinene kadar eBulma için aranabilir durumda kalır.

> [!IMPORTANT]
> Yammer uygulamasında görünen iletiler, uyumluluk gereksinimleri için tutulup tutulmadıklarını veya kalıcı olarak silinip silinmediklerinin doğru bir yansıması değildir.

Bekletme ilkesi yalnızca saklama veya yalnızca silme olduğunda, içeriğin yolları saklama ve silme çeşitlemeleridir.

### <a name="content-paths-for-retain-only-retention-policy"></a>Yalnızca saklama bekletme ilkesi için içerik yolları

1. **Yammer iletisi düzenlenir veya silinirse**: Özgün iletinin bir kopyası SubstrateHolds klasöründe hemen oluşturulur ve saklama süresi dolana kadar orada tutulur. Ardından ileti SubstrateHolds klasöründen hemen kalıcı olarak silinir.

2. **Yammer iletisi değiştirilmez veya silinmezse** ve bekletme süresi boyunca düzenlemeden sonra geçerli iletiler için: Bekletme süresinden önce ve sonra hiçbir şey olmaz; ileti özgün konumunda kalır.

### <a name="content-paths-for-delete-only-retention-policy"></a>Yalnızca silme bekletme ilkesi için içerik yolları

1. Yammer iletisi saklama süresi boyunca **silinmezse**: Saklama süresinin sonunda, ileti SubstrateHolds klasörüne taşınır. Bu eylem, bitiş tarihinden itibaren yedi güne kadar sürer. Ardından ileti SubstrateHolds klasöründen hemen kalıcı olarak silinir.

2. Yammer iletisi bu süre boyunca **kullanıcı tarafından silinirse**, öğe hemen kalıcı olarak silindiği SubstrateHolds klasörüne taşınır.

#### <a name="example-flows-and-timings-for-retention-policies"></a>Bekletme ilkeleri için örnek akışlar ve zamanlamalar

Önceki bölümlerde açıklanan işlemlerin ve zamanlamaların aşağıdaki yapılandırmalara sahip bekletme ilkelerine nasıl uygulandığını görmek için aşağıdaki örnekleri kullanın:

- [Örnek 1: 7 yıl boyunca yalnızca saklama](#example-1-retain-only-for-7-years)
- [Örnek 2: 30 gün boyunca saklama ve ardından silme](#example-2-retain-for-30-days-and-then-delete)
- [Örnek 3: 1 gün sonra yalnızca silme](#example-3-delete-only-after-1-day)

Kalıcı silmeye başvuran tüm örneklerde saklama [ilkeleri](retention.md#the-principles-of-retention-or-what-takes-precedence) nedeniyle, iletinin öğeyi tutmak için başka bir bekletme ilkesine tabi olması veya eBulma saklamaya tabi olması durumunda bu eylem askıya alınır.

##### <a name="example-1-retain-only-for-7-years"></a>Örnek 1: 7 yıl boyunca yalnızca saklama

1. günde, kullanıcı yeni bir Yammer iletisi postalar.

5. günde kullanıcı bu iletiyi düzenler.

30. günde kullanıcı geçerli iletiyi siler.

Bekletme sonuçları:

- Özgün ileti için:
    - 5. günde, ileti SubstrateHolds klasörüne kopyalanır ve burada eBulma araçlarıyla 1. günden itibaren en az 7 yıl boyunca (saklama süresi) aranabilir.

- Geçerli (düzenlenmiş) ileti için:
    - 30. günde, ileti SubstrateHolds klasörüne taşınır ve burada eBulma araçlarıyla 1. günden itibaren en az 7 yıl boyunca (saklama süresi) aranabilir.

Kullanıcı belirtilen saklama süresinden sonra geçerli iletiyi silmişse, saklama süresi yerine yine de SubstrateHolds klasörüne taşınır. Ancak, artık saklama süresi doldu, ileti en az 1 gün sonra ve daha sonra genellikle 1-7 gün içinde kalıcı olarak silinir.

##### <a name="example-2-retain-for-30-days-and-then-delete"></a>Örnek 2: 30 gün boyunca saklama ve ardından silme

1. günde, kullanıcı yeni bir Yammer iletisi postalar.

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

1. günde, kullanıcı yeni bir Yammer iletisi postalar.

Kullanıcı iletiyi düzenlemez veya silmezse örnek bekletme sonucu:

- 5. gün (genellikle 2. günde saklama süresinin başlamasından 1-7 gün sonra):
    - İleti SubstrateHolds klasörüne taşınır ve eBulma araçlarıyla aranabileceği en az 1 gün boyunca orada kalır.

- 9. gün (genellikle SubstrateHolds klasöründe en az 1 gün sonra 1-7 gün):
    - İleti kalıcı olarak silinir ve eBulma aramalarıyla döndürülemez.

Bu örnekte gösterildiği gibi, yalnızca bir gün sonra iletileri silmek için bir bekletme ilkesi yapılandırabilirsiniz ancak hizmet, uyumlu bir silme işlemi sağlamak için birden çok işlemden geçer. Sonuç olarak, 1 gün sonra gerçekleştirilen silme eylemi, eBulma aramalarında artık döndürülmemesi için iletinin kalıcı olarak silinmesi 16 gün sürebilir.

## <a name="messages-and-external-users"></a>İletiler ve dış kullanıcılar

Varsayılan olarak, Yammer kullanıcı iletileri için bir bekletme ilkesi kuruluşunuzdaki tüm kullanıcılar için geçerlidir, ancak dış kullanıcılar için geçerli değildir. Dahil edilen kullanıcılar için **Düzenle** seçeneğini kullanıyorsanız dış kullanıcılara bekletme ilkesi uygulayabilir ve bu kullanıcıların hesabını belirtebilirsiniz.

Şu anda Azure B2B konuk kullanıcıları desteklenmez.

## <a name="when-a-user-leaves-the-organization"></a>Kullanıcı kuruluştan ayrıldığında 

Bir kullanıcı kuruluşunuzdan ayrılırsa ve Microsoft 365 hesabı silinirse, bekletmeye tabi olan Yammer kullanıcı iletileri etkin olmayan bir posta kutusunda depolanır. Bu iletiler, posta kutusu devre dışı bırakılmadan önce kullanıcıya yerleştirilen bekletme ilkesine tabi kalır ve içerik eBulma aramasında kullanılabilir. Daha fazla bilgi için bkz [. Etkin olmayan posta kutuları hakkında bilgi edinin](inactive-mailboxes-in-office-365.md).

Kullanıcı Yammer'da herhangi bir dosya depoladıysa SharePoint ve OneDrive için [eşdeğer bölüme](retention-policies-sharepoint.md#when-a-user-leaves-the-organization) bakın.

## <a name="limitations"></a>Sınırlamalar

Yammer topluluk iletileri ve kullanıcı iletileri için bekletme kullandığınızda aşağıdaki sınırlamalara dikkat edin:

- **Yammer kullanıcı iletileri** konumu için **Düzenle'yi** seçtiğinizde, konukları ve posta kutusu olmayan kullanıcıları görebilirsiniz. Bekletme ilkeleri bu kullanıcılar için tasarlanmamıştır, bu nedenle bunları seçmeyin.

## <a name="configuration-guidance"></a>Yapılandırma kılavuzu

Microsoft 365'te saklamayı yapılandırmaya yeni başladıysanız bkz. [Veri yaşam döngüsü yönetimini kullanmaya başlama](get-started-with-data-lifecycle-management.md).

Yammer için bir bekletme ilkesi yapılandırmaya hazırsanız bkz. [Bekletme ilkeleri oluşturma ve yapılandırma](create-retention-policies.md).
