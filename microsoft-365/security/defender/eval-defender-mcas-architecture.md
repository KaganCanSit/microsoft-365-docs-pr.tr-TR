---
title: Mimari gereksinimlerini ve yapıyı gözden Microsoft Defender for Cloud Apps
description: Microsoft Defender for Cloud Apps diyagramlar, Microsoft 365 Defender ortamında pilot ortam oluşturmanıza yardımcı olacak mimariyi açıklar.
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
ms.openlocfilehash: 6547c1b269ede9385b384ca18fe6f2ca34d35109
ms.sourcegitcommit: 3b8e009ea1ce928505b8fc3b8926021fb91155f3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/28/2022
ms.locfileid: "64500331"
---
# <a name="review-architecture-requirements-and-key-concepts-for-microsoft-defender-for-cloud-apps"></a>Daha fazla bilgi için mimari gereksinimlerini ve temel Microsoft Defender for Cloud Apps


**Aşağıdakiler için geçerlidir:**

- Microsoft 365 Defender

Bu makale, [değerlendirme ortamının](eval-defender-mcas-overview.md) yanı sıra değerlendirme ortamını ayarlama işleminin 1/ 3 Microsoft Defender for Cloud Apps adımdır ve Microsoft 365 Defender. Bu işlem hakkında daha fazla bilgi için genel bakış [makalesine bakın](eval-defender-identity-overview.md).

Yapıyı etkinleştirmeden Microsoft Defender for Cloud Apps mimariyi anlıyoruz ve gereksinimleri karşılayana kadar emin olun. 

## <a name="understand-the-architecture"></a>Mimariyi anlama

Microsoft Defender for Cloud Apps bir bulut erişimi güvenlik aracıdır (CASB). CASB'ler, kullanıcılarınızı nerede bulunursa kullansın, nerede bulunursa kullansın, kuruluş kullanıcılarınız ve bulut kaynakları arasında gerçek zamanlı olarak aracı erişimi için kapı bekçisi davranır. Microsoft Defender for Cloud Apps, Microsoft güvenlik özellikleriyle (güvenlik özellikleri de içinde olmak üzere) yerel olarak Microsoft 365 Defender.

Uygulama Bulut için Defender, aşağıda gösterildiği gibi, organizasyon tarafından kullanılan bulut uygulamaları unmanaged and unprotected olur.

:::image type="content" source="../../media/defender/m365-defender-mcas-architecture-a.png" alt-text="Mimariye uygun Microsoft Defender for Cloud Apps" lightbox="../../media/defender/m365-defender-mcas-architecture-a.png":::

Çizimde:
- Kuruluş tarafından bulut uygulamalarının kullanımı takipsiz ve korumasız olur. 
- Bu kullanım, yönetilen bir kuruluşta yapılan korumaların dışındadır. 

#### <a name="discovering-cloud-apps"></a>Bulut uygulamalarını keşfetme

Bulut uygulamalarının kullanımını yönetmenin ilk adımı, hangi bulut uygulamalarının kurum tarafından kullanılanlarını keşfetmektir. Sonraki diyagramda, bulut keşfinin uygulama ve uygulamalarla nasıl çalıştığını Bulut için Defender yer almaktadır.

:::image type="content" source="../../media/defender/m365-defender-mcas-architecture-b.png" alt-text="Bulut keşifleri'Microsoft Defender for Cloud Apps mimari" lightbox="../../media/defender/m365-defender-mcas-architecture-b.png":::


Bu çizimde, ağ trafiğini izlemek ve kurum tarafından kullanılan bulut uygulamalarını keşfetmek için 2 yöntem vardır.
- C. Bulut Uygulama Bulma, e-Uç Nokta için Microsoft Defender ile tümleştirilmiştir. Uç nokta için Defender, bulut uygulamalarına ve hizmetlere IT tarafından yönetilen Windows 10 cihazlardan Windows 11 raporlar. 
- B. Ağa bağlı tüm cihazlarda kapsam için, Bulut için Defender Uygulamaları günlük toplayıcısı uç noktalardan veri toplamak için güvenlik duvarları ve diğer artımlara yüklenir. Bu veriler çözümleme için Bulut için Defender Uygulamalar'a gönderilir.

#### <a name="managing-cloud-apps"></a>Bulut uygulamalarını yönetme

Bulut uygulamalarını bu seçtikten ve bu uygulamaların organizasyonu tarafından nasıl kullanıla olduğunu çözümledikten sonra, seçtiğiniz bulut uygulamalarını yönetmeye başlayabilirsiniz. 

:::image type="content" source="../../media/defender/m365-defender-mcas-architecture-c.png" alt-text="Bulut uygulamalarını Microsoft Defender for Cloud Apps için mimari" lightbox="../../media/defender/m365-defender-mcas-architecture-c.png":::

Bu şekilde:
- Bazı uygulamalar kullanım için karşılandı. Bu sadelik uygulamaları yönetmeye başlangıç için basit bir yol.
- Uygulamaları uygulama bağlayıcıları ile bağlayarak daha görünürlüğü ve denetimi etkinleştirebilirsiniz. Uygulama bağlayıcıları, uygulama sağlayıcılarının API'lerini kullanır.


#### <a name="applying-session-controls-to-cloud-apps"></a>Bulut uygulamalarına oturum denetimleri uygulama

Microsoft Defender for Cloud Apps, depolamalı bulut uygulamalarına ara sunucu erişimi sağlayan bir ters ara sunucu hizmeti sunar. Bu sağlama, Bulut için Defender uygulamalarının yapılandırılan oturum denetimlerini uygulamalarını sağlar. 

:::image type="content" source="../../media/defender/m365-defender-mcas-architecture-d.png" alt-text="Proxy erişimi Microsoft Defender for Cloud Apps denetimi için mimari" lightbox="../../media/defender/m365-defender-mcas-architecture-d.png":::

Bu şekilde:
- Kullanıcılardan ve kuruluşlardan edinilen bulut uygulamalarına erişim, Bulut için Defender tarafından yönlendirildi.
- Bu ara sunucu erişimi oturum denetimlerinin uygulanmasına izin verir.
- Etkilenmemiş veya açıkça belirtlanmamış bulut uygulamaları etkilenmez.

Oturum denetimleri, bulut uygulamalarının organizasyonu tarafından nasıl kullanılacaklarına parametre uygulamanıza olanak sağlar. Örneğin, organizasyonunız Salesforce kullanıyorsa, salesforce'da yalnızca yönetilen cihazların kuruluş verilerinize erişmelerine izin veren bir oturum ilkesi yapılandırabilirsiniz. Daha basit bir örnek, daha sıkı ilkeler uygulamadan önce bu trafiğin riskini çözümlemenizi sağlayan, yönetimsiz cihazlardan gelen trafiği izlemek için bir ilke yapılandırmak olabilir.

#### <a name="integrating-with-azure-ad-with-conditional-access-app-control"></a>Koşullu Erişim Uygulama Denetimi ile Azure AD ile Tümleştirme

Çok faktörlü kimlik doğrulaması ve diğer koşullu erişim ilkelerini zorunlu kılınan Azure AD kiracınıza Zaten SaaS uygulamaları eklemış olabilirsiniz. Microsoft Defender for Cloud Apps, Azure AD ile yerel olarak tümleştirilmiştir. Tek gereken, Azure AD'de uygulamalar için Koşullu Erişim Uygulama Denetimi'Bulut için Defender yapılandırmaktır. Bu, yönetilen SaaS uygulamaları için ağ trafiğini ara sunucu olarak Bulut için Defender Uygulamaları aracılığıyla yönlendirerek Bulut için Defender Uygulamalarının bu trafiği izlemesi ve oturum denetimlerini uygulamasını sağlar. 

:::image type="content" source="../../media/defender/m365-defender-mcas-architecture-e.png" alt-text="Yeni - SaaS Microsoft Defender for Cloud Apps mimari" lightbox="../../media/defender/m365-defender-mcas-architecture-e.png":::

Bu şekilde:
- SaaS uygulamaları, Azure AD kiracısı ile tümleştirilmiştir. Bu tümleştirme, Azure AD'nin, çok faktörlü kimlik doğrulaması da içinde olmak üzere koşullu erişim ilkelerini zorunlu açmasını sağlar.
- SaaS uygulamalarının trafiğini Azure Active Directory uygulamalarına yönlendirecek bir ilke Bulut için Defender eklenir. İlke, bu ilkenin hangi SaaS uygulamalarına uygulanıyor olduğunu belirtir. Bu nedenle, Azure AD bu SaaS uygulamalarına uygulanacak tüm koşullu erişim ilkelerini zorunlu kılındikten sonra, Azure AD oturum trafiğini Uygulamalar Bulut için Defender yönlendiriyor.
- Bulut için Defender uygulamaları bu trafiği izler ve yöneticiler tarafından yapılandırılmış olan tüm oturum denetimi ilkelerini uygular. 

Azure AD'ye henüz eklenmiştir ve Bulut için Defender Uygulamaları kullanarak bulut uygulamalarını keşfeder ve kötülenmiştir. Bu bulut uygulamalarını Azure AD kiracınıza ekleyerek ve koşullu erişim kurallarınız kapsamını kullanarak Koşullu Erişim Uygulama Denetimi'nden faydalanabilirsiniz.

#### <a name="protecting-your-organization-from-hackers"></a>Organizasyonlarınızı korsanlardan koruma

Bulut için Defender uygulamaları kendi başına güçlü koruma sağlar. Öte yandan, Microsoft 365 Defender'in diğer özellikleriyle birlikte Bulut için Defender Uygulamalar paylaşılan sinyallere veri sağlar ve bu da (birlikte) saldırıları durdurmaya yardımcı olur.

Genel bakış ile bu değerlendirme ve pilot kılavuzuna kadar bu çizimi Microsoft 365 Defender değer. 

:::image type="content" source="../../media/defender/m365-defender-eval-threat-chain.png" alt-text="Microsoft 365 Defender tehdit zincirini nasıl durduracak" lightbox="../../media/defender/m365-defender-eval-threat-chain.png":::

Bu çizimin sağ tarafına odaklanmak Microsoft Defender for Cloud Apps olanaksız seyahat, kimlik bilgileri erişimi ve alışılmışın dışında indirme, dosya paylaşımı veya posta iletme etkinliği gibi anormal davranışlara sahip olur ve bu davranışları güvenlik ekibine raporlar. Bu nedenle Bulut için Defender Uygulamaları bilgisayar korsanlarının eşkenar hareketi ve hassas verilerin imhasını engellemeye yardımcı olur. Microsoft 356 Bulut için Defender tüm bileşenlerden gelen sinyalleri tüm saldırı anlatılarını sağlamak için birbiriyle bağlantılı olarak kontrol eder.

## <a name="understand-key-concepts"></a>Önemli kavramları anlama

Aşağıdaki tabloda, değerlendirme, yapılandırma ve dağıtımda önemli olan önemli kavramlar tanım Microsoft Defender for Cloud Apps.


|Kavram  |Açıklama |Daha fazla bilgi  |
|---------|---------|---------|
| Bulut için Defender Uygulamaları Panosu | Organizasyonunız hakkında en önemli bilgilere genel bir bakış sunar ve daha derin araştırma bağlantıları sunar.        | [Panoyla çalışma ](/cloud-app-security/daily-activities-to-protect-your-cloud-environment)       |
| Koşullu Erişim Uygulama Denetimi    | Azure AD'ye koşullu erişim ilkeleri vermek ve oturum denetimlerini seçmeli olarak zorunlu k olmak için Kimlik Sağlayıcınızla (IdP) tümleştirilmiş ara sunucu mimarisini tersine çevirebilirsiniz.        |  [Koşullu Erişim Uygulama Microsoft Defender for Cloud Apps ile uygulamaları koruma](/cloud-app-security/proxy-intro-aad)       |
|  Bulut Uygulama Kataloğu   | Bulut Uygulama Kataloğu, 80'den fazla risk faktörüne göre dereceli ve puanlandı 16.000'den fazla bulut uygulamasıyla dolu Microsoft kataloğunda, eksiksiz bir resim sunar.    |  [Uygulama risk puanları ile çalışma](/cloud-app-security/risk-score)       |
| Bulut Keşif Panosu    | Bulut Keşif trafik günlüklerinizi analiz eder ve bulut uygulamalarının organizasyonda nasıl kullanıldıklarına dair daha fazla fikir vermenin yanı sıra uyarılar ve risk düzeyleri vermek üzere tasarlanmıştır.     |  [Bulunan uygulamalarla çalışma   ](/cloud-app-security/discovered-apps)    |
|Bağlı Uygulamalar |Bulut için Defender Uygulamaları, Koşullu Uygulama Erişim Denetimlerimizi kullanarak Buluttan Bulut tümleştirmesi, API bağlayıcıları ve gerçek zamanlı erişim ve oturum denetimlerini kullanarak bağlı uygulamalar için  end-bitiş koruması sağlar. |[Bağlı uygulamaları koruma](/cloud-app-security/protect-connected-apps) |
| | | |

## <a name="review-architecture-requirements"></a>Mimari gereksinimleri gözden geçirin

### <a name="discovering-cloud-apps"></a>Bulut uygulamalarını keşfetme

Ortamınıza kullanılan bulut uygulamalarını keşfetmek için, aşağıdaki yöntemlerden birini veya her ikisini de uygulayabilirsiniz:

- Bulut Bulma ile tümleştirerek Bulut Bulma ile hızlı bir şekilde Uç Nokta için Microsoft Defender. Bu yerel tümleştirme, hem cihazlarınız hem de cihazlarınız arasında bulut trafiği Windows 11 ağ üzerinde ve Windows 10 veri toplamaya başlamanıza olanak tanır.
- Ağınıza bağlı tüm cihazlardan erişilen tüm bulut uygulamalarını keşfetmek için güvenlik duvarlarınız ve diğer Bulut için Defender uygulama günlüğü toplayıcısı dağıtın. Bu dağıtım uç noktalarından veri toplamanıza yardımcı olur ve bunları çözümleme için Bulut için Defender Uygulamalar'a gönderir. Bulut için Defender Uygulamalar, daha fazla özellik için bazı üçüncü taraf taraflarla yerel olarak tümleştirilmiştir.

Bu seçenekler [2. Adım'da yer almaktadır. Değerlendirme ortamını etkinleştirin](eval-defender-mcas-enable-eval.md). 

### <a name="applying-azure-ad-conditional-access-policies-to-cloud-apps"></a>Bulut uygulamalarına Azure AD Koşullu Erişim ilkeleri uygulama

Koşullu Erişim Uygulama Denetimi (bulut uygulamalarına Koşullu Erişim ilkeleri uygulayabilme özelliği) Azure AD ile tümleştirme gerektirir. Bu tümleştirme, Bulut için Defender Uygulamaları ile çalışmaya başlamanız için bir Bulut için Defender değildir. Bu, pilot aşamasında (3. Adım) denemeyi [denemeyi teşvik edecek bir adımdır. Pilot Microsoft Defender for Cloud Apps](eval-defender-mcas-pilot.md).

## <a name="siem-integration"></a>SIEM tümleştirmesi

Bağlantılı uygulamalardan Microsoft Defender for Cloud Apps ve etkinliklerin merkezi olarak izlenmesini sağlamak için, e-postanızı genel SIEM sunucunuzla veya Microsoft Sentinel ile tümleştirebilirsiniz. 

Ayrıca, Microsoft Sentinel'de Microsoft Sentinel'Microsoft Defender for Cloud Apps daha derin tümleştirme sağlayan bir kullanıcı bağlayıcısı da vardır. Bu düzenleme, bulut uygulamalarınızı görünürlüğü kazanmakla aynı zamanda siber tehditlere karşı mücadele etmek ve verilerinizin nasıl seyahatdiğini belirlemek için gelişmiş analiz elde etmek için de olanak sağlar.

- [Genel SIEM tümleştirmesi](/cloud-app-security/siem)
- [Bulut için Defender Apps'tan Microsoft Sentinel'e uyarılar ve Bulut Keşif günlükleri gönderme](/azure/sentinel/connect-cloud-app-security)

### <a name="next-steps"></a>Sonraki adımlar

Adım 2 / 3: [Değerlendirme ortamını belirli bir Microsoft Defender for Cloud Apps](eval-defender-mcas-enable-eval.md)

Değerlendirme görünümüne genel [bakış Microsoft Defender for Cloud Apps](eval-defender-mcas-overview.md)

Değerlendirme ve pilot uygulama için [genel bakış Microsoft 365 Defender](eval-overview.md)
