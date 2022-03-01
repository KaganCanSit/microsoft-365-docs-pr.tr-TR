---
title: Bulut Uygulamaları için Microsoft Defender'ın mimari gereksinimlerini ve yapısını gözden geçirme
description: Bulut Uygulamaları için Microsoft Defender teknik diyagramları, Microsoft 365 Defender ortamında pilot ortam oluşturmanıza yardımcı olacak mimariyi açıklar.
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: bcarter
author: brendacarter
ms.date: 07/09/2021
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-scenario
- m365solution-evalutatemtp
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: ed36974ae0f32ebc29360ee1039e93c12b2d85c5
ms.sourcegitcommit: 6f3bc00a5cf25c48c61eb3835ac069e9f41dc4db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2022
ms.locfileid: "63014140"
---
# <a name="review-architecture-requirements-and-key-concepts-for-microsoft-defender-for-cloud-apps"></a>Bulut Uygulamaları için Microsoft Defender'da mimari gereksinimlerini ve temel kavramları gözden geçirin


**Aşağıdakiler için geçerlidir:**

- Microsoft 365 Defender

Bu makale, Bulut Uygulamaları için Microsoft Defender değerlendirme ortamını ayarlama işleminin [1/ 3](eval-defender-mcas-overview.md). adımıdır. Bu makale, Microsoft 365 Defender. Bu işlem hakkında daha fazla bilgi için genel bakış [makalesine bakın](eval-defender-identity-overview.md).

Bulut Uygulamaları için Microsoft Defender'ı etkinleştirmeden önce mimariyi anlıyoruz ve gereksinimleri karşılaya hazır olduğundan emin olun. 

## <a name="understand-the-architecture"></a>Mimariyi anlama

Bulut Uygulamaları için Microsoft Defender bir bulut erişim güvenlik aracıcısıdır (CASB). CASB'ler, kullanıcılarınızı nerede bulunursa kullansın, nerede bulunursa kullansın, kuruluş kullanıcılarınız ve bulut kaynakları arasında gerçek zamanlı olarak aracı erişimi için kapı bekçisi davranır. Bulut Uygulamaları için Microsoft Defender, Microsoft güvenlik özellikleriyle yerel olarak tümleştirilmiştir; örneğin, Microsoft 365 Defender.

Bulut Uygulamaları için Defender olmadan, aşağıda gösterildiği gibi, organizasyon tarafından kullanılan bulut uygulamaları unmanaged ve unprotected olur.

![Bulut Uygulamaları için Microsoft Defender mimarisi.](../../media/defender/m365-defender-mcas-architecture-a.png)

Çizimde:
- Kuruluş tarafından bulut uygulamalarının kullanımı takipsiz ve korumasız olur. 
- Bu kullanım, yönetilen bir kuruluşta yapılan korumaların dışındadır. 

#### <a name="discovering-cloud-apps"></a>Bulut uygulamalarını keşfetme

Bulut uygulamalarının kullanımını yönetmenin ilk adımı, hangi bulut uygulamalarının kurum tarafından kullanılanlarını keşfetmektir. Sonraki diyagramda bulut keşif çalışmaları Bulut Uygulamaları için Defender ile nasıl çalıştığını gösterir.

![Bulut Uygulamaları için Microsoft Defender mimarisi - Bulut keşif.](../../media/defender/m365-defender-mcas-architecture-b.png)

Bu çizimde, ağ trafiğini izlemek ve kurum tarafından kullanılan bulut uygulamalarını keşfetmek için 2 yöntem vardır.
- C. Bulut Uygulama Bulma, yerel olarak Uç Nokta için Microsoft Defender ile tümleştirilmiştir. Uç nokta için Defender, bulut uygulamalarına ve hizmetlere IT tarafından yönetilen Windows 10 11 Windows tarafından erişilebilen raporlar. 
- B. Ağa bağlı tüm cihazlarda kapsam için Bulut Uygulamaları için Defender günlük toplayıcısı, uç noktalardan veri toplamak için güvenlik duvarları ve diğer artımlara yüklenir. Bu veriler çözümleme için Bulut Uygulamaları için Defender'a gönderilir.

#### <a name="managing-cloud-apps"></a>Bulut uygulamalarını yönetme

Bulut uygulamalarını budikten ve bunların organizasyon tarafından nasıl kullanıldıktan sonra davranışını çözümledikten sonra, seçtiğiniz bulut uygulamalarını yönetmeye başlayabilirsiniz. 

![Bulut Uygulamaları için Microsoft Defender Mimarisi - Bulut uygulamalarını yönetme.](../../media/defender/m365-defender-mcas-architecture-c.png)

Bu şekilde:
- Bazı uygulamalar kullanım için karşılandı. Bu, uygulamaları yönetmeye başlangıç yapmak için basit bir yol sağlar.
- Uygulamaları uygulama bağlayıcıları ile bağlayarak daha görünürlüğü ve denetimi etkinleştirebilirsiniz. Uygulama bağlayıcıları, uygulama sağlayıcılarının API'lerini kullanır.


#### <a name="applying-session-controls-to-cloud-apps"></a>Bulut uygulamalarına oturum denetimleri uygulama

Bulut Uygulamaları için Microsoft Defender, depolamalı bulut uygulamalarına ara sunucu erişimi sağlayan bir ters ara sunucu olarak hizmet vermektedir. Bu, Bulut Uygulamaları için Defender'ın yapılandırılan oturum denetimlerini uygulamasına olanak sağlar. 

![Bulut Uygulamaları için Microsoft Defender Mimarisi - Ara Sunucu erişimi oturum denetimi.](../../media/defender/m365-defender-mcas-architecture-d.png)

Bu şekilde:
- Kullanıcılardan ve organizasyonlu cihazlardan uzak bulut uygulamalarına erişim, Bulut Uygulamaları için Defender aracılığıyla yönlendirildi.
- Bu ara sunucu erişimi oturum denetimlerinin uygulanmasına izin verir.
- Etkilenmemiş veya açıkça belirtlanmamış bulut uygulamaları etkilenmez.

Oturum denetimleri, bulut uygulamalarının organizasyonu tarafından nasıl kullanılacaklarına parametre uygulamanıza olanak sağlar. Örneğin, organizasyonunız Salesforce kullanıyorsa, salesforce'ta yalnızca yönetilen cihazların kuruluş verilerinize erişmelerine izin veren bir oturum ilkesi yapılandırabilirsiniz. Daha basit bir örnek, daha sıkı ilkeler uygulamadan önce bu trafiğin riskini çözümlemenizi sağlayan, yönetimsiz cihazlardan gelen trafiği izlemek için bir ilke yapılandırmak olabilir.

#### <a name="integrating-with-azure-ad-with-conditional-access-app-control"></a>Koşullu Erişim Uygulama Denetimi ile Azure AD ile Tümleştirme

Çok faktörlü kimlik doğrulaması ve diğer koşullu erişim ilkelerini zorunlu kılınan Azure AD kiracınıza Zaten SaaS uygulamaları eklemış olabilirsiniz. Bulut Uygulamaları için Microsoft Defender, Azure AD ile yerel olarak tümleştirilmiştir. Tek gereken, Azure AD'de Bulut Uygulamaları için Defender'daki Koşullu Erişim Uygulama Denetimi'nin kullanımını yapacak bir ilke yapılandırmaktır. Bu, yönetilen SaaS uygulamaları için ağ trafiğini, ara sunucu olarak Bulut Uygulamaları için Defender aracılığıyla yönlendirerek Bulut Uygulamaları için Defender'ın bu trafiği izlemesini ve oturum denetimlerini uygulamasını sağlar. 

![Bulut Uygulamaları için Microsoft Defender Mimarisi - SaaS uygulamaları.](../../media/defender/m365-defender-mcas-architecture-e.png)

Bu şekilde:
- SaaS uygulamaları, Azure AD kiracısı ile tümleştirilmiştir. Bu, Azure AD'nin çok faktörlü kimlik doğrulaması da içinde olmak üzere koşullu erişim ilkelerini zorunlu açmasını sağlar.
- SaaS uygulamalarına yönelik Azure Active Directory Bulut Uygulamaları için Defender'a bir ilke eklenmiştir. İlke, bu ilkenin hangi SaaS uygulamalarına uygulanıyor olduğunu belirtir. Sonuç olarak, Azure AD bu SaaS uygulamalarına uygulanacak tüm koşullu erişim ilkelerini zorunlu kapattıktan sonra, Azure AD daha sonra Bulut Uygulamaları için Defender aracılığıyla oturum trafiğini yönlendiriyor (yanızca).
- Bulut Uygulamaları için Defender bu trafiği izler ve yöneticiler tarafından yapılandırılmış olan tüm oturum denetimi ilkelerini uygular. 

Azure AD'ye eklenmiştir bulut uygulamaları için Defender'ı kullanarak bulut uygulamaları keşfeder ve kötülenmiştir. Bu bulut uygulamalarını Azure AD kiracınıza ekleyerek ve koşullu erişim kurallarınız kapsamını kullanarak Koşullu Erişim Uygulama Denetimi'nden faydalanabilirsiniz.

#### <a name="protecting-your-organization-from-hackers"></a>Organizasyonlarınızı korsanlardan koruma

Bulut Uygulamaları için Defender kendi başına güçlü koruma sağlar. Bununla birlikte, bulut uygulamalarının diğer özellikleriyle birlikte Microsoft 365 Defender bulut uygulamaları için Defender paylaşılan sinyallere veri sağlar ve bu da saldırıları durdurmaya yardımcı olur.

Genel bakış ile bu değerlendirme ve pilot kılavuzuna kadar bu çizimi Microsoft 365 Defender değer. 

![Bu Microsoft 365 Defender tehdit zincirini nasıl durduracak?](../../media/defender/m365-defender-eval-threat-chain.png)

Bu çizimin sağ tarafına odaklanan Bulut Uygulamaları için Microsoft Defender, olanaksız seyahat, kimlik bilgileri erişimi ve olağandışı indirme, dosya paylaşımı veya posta iletme etkinliği gibi anormal davranışlar fark ediyor ve bunları güvenlik ekibine raporlar. Sonuç olarak, Bulut Uygulamaları için Defender bilgisayar korsanlarının eşkenar hareketi ve hassas verilerin imhasını engellemeye yardımcı olur. Bulut için Microsoft 356 Defender, tüm saldırı hikayesini sağlamak için tüm bileşenlerden gelen sinyalleri birbiriyle bağlantılı olarak sağlar.

## <a name="understand-key-concepts"></a>Önemli kavramları anlama

Aşağıdaki tabloda, Bulut Uygulamaları için Microsoft Defender'ı değerlendirirken, yapılandırarak ve dağıtırken anlamanız gereken önemli kavramlar tanımlandı.


|Kavram  |Açıklama |Daha fazla bilgi  |
|---------|---------|---------|
| Bulut Uygulamaları panosu için Defender | Organizasyonunız hakkında en önemli bilgilere genel bir bakış sunar ve daha derin araştırma bağlantıları sunar.        | [Panoyla çalışma ](/cloud-app-security/daily-activities-to-protect-your-cloud-environment)       |
| Koşullu Erişim Uygulama Denetimi    | Azure AD'ye koşullu erişim ilkeleri vermek ve oturum denetimlerini seçmeli olarak zorunlu k olmak için Kimlik Sağlayıcınızla (IdP) tümleştirilmiş ara sunucu mimarisini tersine çevirebilirsiniz.        |  [Bulut Uygulamaları için Microsoft Defender Ile Uygulamaları Koruma Koşullu Erişim Uygulama Denetimi](/cloud-app-security/proxy-intro-aad)       |
|  Bulut Uygulama Kataloğu   | Bulut Uygulama Kataloğu, 80'den fazla risk faktörüne göre dereceli ve puanlandı 16.000'den fazla bulut uygulamasıyla dolu Microsoft kataloğunda, eksiksiz bir resim sunar.    |  [Uygulama risk puanları ile çalışma](/cloud-app-security/risk-score)       |
| Bulut Keşif Panosu    | Bulut Keşif trafik günlüklerinizi analiz eder ve bulut uygulamalarının organizasyonda nasıl kullanıldıklarına dair daha fazla fikir vermenin yanı sıra uyarılar ve risk düzeyleri vermek üzere tasarlanmıştır.     |  [Bulunan uygulamalarla çalışma   ](/cloud-app-security/discovered-apps)    |
|Bağlı Uygulamalar |Bulut Uygulamaları için Defender, Buluttan Bulut tümleştirmesi, API bağlayıcıları ve Koşullu Uygulama Erişim Denetimlerimizin yararlanarak gerçek zamanlı erişim ve oturum denetimlerini kullanarak bağlı uygulamalar için çıtaya kadar koruma sağlar. |[Bağlı uygulamaları koruma](/cloud-app-security/protect-connected-apps) |
| | | |

## <a name="review-architecture-requirements"></a>Mimari gereksinimlerini gözden geçirme

### <a name="discovering-cloud-apps"></a>Bulut uygulamalarını keşfetme

Ortamınıza kullanılan bulut uygulamalarını keşfetmek için, aşağıdakilerin birini veya her ikisini de yapabilirsiniz:

- Uç Nokta için Microsoft Defender ile tümleştirerek Bulut Bulma ile hızla hareket edin. Bu yerel tümleştirme, 11 ve Windows 10 cihazlarınız arasında ağ üzerinde ve ağdan bulut trafiği Windows veri toplamaya başlamanıza olanak tanır.
- Ağınıza bağlı tüm cihazlardan erişilen tüm bulut uygulamalarını bulmak için güvenlik duvarlarınız ve diğer yardımcı sunucularda Bulut Uygulamaları için Defender günlük toplayıcısı dağıtın. Bu işlem uç noktalarından verileri toplar ve çözümleme için Bulut Uygulamaları için Defender'a gönderir. Bulut Uygulamaları için Defender, daha fazla özellik için bazı üçüncü taraf taraflarla yerel olarak tümleştirilmiştir.

Bu seçenekler [2. Adım'da yer almaktadır. Değerlendirme ortamını etkinleştirin](eval-defender-mcas-enable-eval.md). 

### <a name="applying-azure-ad-conditional-access-policies-to-cloud-apps"></a>Bulut uygulamalarına Azure AD Koşullu Erişim ilkeleri uygulama

Koşullu Erişim Uygulama Denetimi (bulut uygulamalarına Koşullu Erişim ilkeleri uygulayabilme özelliği) Azure AD ile tümleştirme gerektirir. Bu, Bulut Uygulamaları için Defender'ı başlatmanız için bir zorunluluk değildir. Bu, pilot aşamasında (3. Adım) denemeyi [denemeyi teşvik edecek bir adımdır. Bulut Uygulamaları için Microsoft Defender'ı Pilot Edin](eval-defender-mcas-pilot.md).

## <a name="siem-integration"></a>SIEM tümleştirmesi

Bulut Uygulamaları için Microsoft Defender'ı genel SIEM sunucunuzla veya Microsoft Sentinel ile tümleştirin ve bağlı uygulamalardan gelen uyarıları ve etkinlikleri merkezi olarak izlemesini sebilirsiniz. 

Ayrıca, Microsoft Sentinel'de Microsoft Sentinel ile daha derin tümleştirme sağlayan bir Bulut Uygulamaları için Microsoft Defender bağlayıcısı vardır. Bu, bulut uygulamalarınızı görünürlüğü kazanmakla aynı zamanda siber tehditleri tanımlamak ve buna karşı mücadele etmek, verilerinizin nasıl seyahatdiğini belirlemek için gelişmiş analiz elde etmek için de olanak sağlar.

- [Genel SIEM tümleştirmesi](/cloud-app-security/siem)
- [Bulut Uygulamaları için Defender'dan Microsoft Sentinel'e uyarılar ve Bulut Keşif günlükleri gönderme](/azure/sentinel/connect-cloud-app-security)

### <a name="next-steps"></a>Sonraki adımlar

Adım 2 / 3: [Bulut Uygulamaları için Microsoft Defender için değerlendirme ortamını etkinleştirme](eval-defender-mcas-enable-eval.md)

Bulut Uygulamaları için [Microsoft Defender'ı Değerlendirme'ye genel bakış](eval-defender-mcas-overview.md)

Değerlendirme ve pilot uygulama için [genel bakış Microsoft 365 Defender](eval-overview.md)
