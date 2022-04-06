---
title: Önerilen Teams ilkeleri - Microsoft 365 ilkeleri için | Microsoft Docs
description: Microsoft'un iletişim ve dosya erişiminin güvenliğini sağlama hakkında Teams ilkelerini açıklar.
author: MicrosoftHeidi
manager: serdars
ms.prod: m365-security
ms.topic: article
audience: Admin
f1.keywords:
- NOCSH
ms.author: heidip
ms.date: 09/30/2020
ms.reviewer: anmorgan
ms.custom:
- it-pro
- goldenconfig
ms.collection:
- M365-identity-device-management
- M365-security-compliance
- m365solution-identitydevice
- m365solution-scenario
ms.technology: mdo
ms.openlocfilehash: b659853d9323b4a1503cd75cff66a83cbd06e85e
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2022
ms.locfileid: "63682911"
---
# <a name="policy-recommendations-for-securing-teams-chats-groups-and-files"></a>Sohbet, grup ve Teams güvenliğini sağlamak için ilke önerileri

Bu makalede, sohbetler, gruplar ve dosyalar ve takvimler gibi içerikleri korumak Microsoft Teams önerilen Sıfır Güven kimliği ve cihaz erişimi ilkelerinin nasıl uygulanıyor? Bu kılavuz, ortak kimlik [ve cihaz erişim ilkelerine](identity-access-policies.md) ve özel ek bilgilerle birlikte Teams bilgi içerir. Bu Teams diğer ürünlerimizle tümleştiri olduğundan, bu sitelerin ve [](sharepoint-file-access-policies.md) dosyaların güvenliğini SharePoint için ilke önerileri ve e-postanın güvenliğini sağlamak için İlke [önerilerine de bakın](secure-email-recommended-policies.md).

Bu öneriler, şu üç farklı güvenlik ve koruma katmanına dayalıdır Teams, şu şekilde ihtiyaçlarına göre uygulanabilir: başlangıç noktası, kurumsal ve özel güvenlik. Kimlik ve cihaz erişimi yapılandırmalarında, bu güvenlik katmanları ve bu öneriler tarafından başvurulan önerilen ilkeler hakkında [daha fazla bilgi edinebilirsiniz](microsoft-365-policies-configurations.md).

Bu makalede, dağıtıma Teams öneriler, kuruluş dışındaki kullanıcılar dahil olmak üzere belirli kimlik doğrulama durumlarını kapsayacak şekilde yer almaktadır. Eksiksiz bir güvenlik deneyimi için bu yönergeleri takip edin.

## <a name="getting-started-with-teams-before-other-dependent-services"></a>Diğer bağımlı Teams önce Diğer hizmetlerle çalışmaya başlama

Hızlı bir şekilde çalışmaya baş etmek için bağımlı hizmetleri etkinleştirmeniz Microsoft Teams. Bu hizmetlerin hepsi "yalnızca iş" olarak çalışır. Bununla birlikte, hizmetle ilgili aşağıdaki öğeleri yönetmeye hazır olmak gerekir:

- Microsoft 365 grupları
- SharePoint sitelerini ziyaret edin
- OneDrive İş
- Exchange kutularını geri alın
- Videoları ve Planner planlarını akışla izleyin (bu hizmetler etkinleştirilmişse)

## <a name="updating-common-policies-to-include-teams"></a>Ortak ilkeleri, yenilerini de içerecek şekilde Teams

Bir çalışma diyagramında sohbeti, grupları ve Teams korumak için, aşağıdaki diyagramda ortak kimlik ve cihaz erişim ilkelerinden güncelleştirilen ilkeler gösteriliyor. Her ilkenin güncelleştirileceği ilke için, Teams ve bağımlı hizmetlerin bulut uygulamaları atamaya dahil olduğundan emin olun.

:::image type="content" source="../../media/microsoft-365-policies-configurations/identity-access-ruleset-teams.png" alt-text="E-posta ve bağımlı hizmetlere erişimi Teams ilke güncelleştirmelerinin özeti." lightbox="../../media/microsoft-365-policies-configurations/identity-access-ruleset-teams.png":::

Bu hizmetler, aşağıdakiler için bulut uygulamalarının atamaya dahil gerçekleştirilen bağımlı Teams:

- Microsoft Teams
- SharePoint ve OneDrive İş
- Exchange Online
- Skype Kurumsal Çevrimiçi
- Microsoft Stream (toplantı kayıtları)
- Microsoft Planner (Planner görevleri ve plan verileri)

Bu tabloda, yeni geçirilmesi gereken ilkeler ve ortak kimlik ve cihaz erişimi ilkelerinde yer alan ve [](identity-access-policies.md)tüm Office uygulamaları için daha geniş bir ilke ayarlanmış olan ilkeler listelemektedir.

|Koruma düzeyi|İlkeler|Uygulama hakkında daha Teams bilgi|
|---|---|---|
|**Başlangıç noktası**|[Oturum açma riski orta veya yüksek olduğunda MFA  *gerektirme*](identity-access-policies.md#require-mfa-based-on-sign-in-risk)|Her Teams ve bağımlı hizmetlerin uygulama listesine ek olduğundan emin olun. Teams göz önünde bulundurabilirsiniz. Konuk Erişimi ve Dış Erişim kurallarına da sahipse, bu makalenin devamlarında bu kurallar hakkında daha fazla bilgi bulabilirsiniz.|
||[Modern kimlik doğrulamasını desteklemez istemcileri engelleme](identity-access-policies.md#block-clients-that-dont-support-multi-factor)|Bulut Teams diğer hizmetleri ve bağımlı hizmetleri de atamaya dahil edin.|
||[Yüksek riskli kullanıcıların parolayı değiştirmesi gerekir](identity-access-policies.md#high-risk-users-must-change-password)|Yüksek Teams etkinlik algılandığında, oturum alıkan kullanıcıların parolalarını değiştirmelerini zorunda zorundalar. Her Teams ve bağımlı hizmetlerin uygulama listesine ek olduğundan emin olun.|
||[UYGULAMA veri koruma ilkelerini uygulama](identity-access-policies.md#apply-app-data-protection-policies)|Her Teams ve bağımlı hizmetlerin uygulama listesine ek olduğundan emin olun. Her platform için ilkeyi güncelleştirin (iOS, Android, Windows).|
|**Enterprise**|[Oturum açma riski düşük, orta veya *yüksek olduğunda* MFA  *gerektirme*](identity-access-policies.md#require-mfa-based-on-sign-in-risk)|Teams göz önünde bulundurabilirsiniz. Konuk Erişimi ve Dış Erişim kurallarına da sahipse, bu makalenin devamlarında bu kurallar hakkında daha fazla bilgi bulabilirsiniz. Bu Teams hizmetleri ve bağımlı hizmetleri dahil etmek.|
||[Cihaz uyumluluk ilkelerini tanımlama](identity-access-policies.md#define-device-compliance-policies)|Bu Teams hizmetleri ve bağımlı hizmetleri dahil etmek.|
||[Uyumlu bilgisayar ve *mobil cihaz* gerektirme](identity-access-policies.md#require-compliant-pcs-and-mobile-devices)|Bu Teams hizmetleri ve bağımlı hizmetleri dahil etmek.|
|**Özel güvenlik**|[*Her* zaman MFA gerektir](identity-access-policies.md#require-mfa-based-on-sign-in-risk)|Kullanıcı kimliğine bakılmaksızın, MFA organizasyonu tarafından kullanılır. Bu Teams hizmetleri ve bağımlı hizmetleri dahil etmek. |

## <a name="teams-dependent-services-architecture"></a>Teams bağlı hizmet mimarisi

Başvuru için, aşağıdaki diyagramda güven güven Teams gösterilen hizmetler yer almaktadır. Daha fazla bilgi ve çizim için bkz[. MICROSOFT TEAMS mimarlar için Microsoft 365 hizmetleriyle ilgili üretkenlik hizmetleri](../../solutions/productivity-illustrations.md).

:::image type="content" source="../../media/microsoft-365-policies-configurations/identity-access-logical-architecture-teams.png" alt-text="Diyagram ve Teams, SharePoint OneDrive İş bağımlılıkları gösteren Exchange." lightbox="../../media/microsoft-365-policies-configurations/identity-access-logical-architecture-teams.png":::

## <a name="guest-and-external-access-for-teams"></a>Konuk ve dış erişim Teams

Microsoft Teams, aşağıdaki erişim türlerini tanımlar:

- **Konuk erişimi** , bir ekibin üyesi olarak eklenilen ve ekibin iletişim ve kaynaklarına tüm izinlere sahip olan konuk veya dış kullanıcı için Azure AD B2B hesabı kullanır.

- **Dış erişim** , Azure AD B2B hesabı olan bir dış kullanıcıya yöneliktir. Dış erişim davetleri ve aramalara, sohbetlere ve toplantılara katılımı içerebilir, ancak ekip üyeliğini ve ekibin kaynaklarına erişimi içermez.

Koşullu Erişim ilkeleri yalnızca Teams Azure AD B2B hesabı olduğundan konuk erişimi için geçerlidir.

<!--
In Azure AD, guest and external users are the same. The user type for both of these is Guest. Guest users are B2B users. Microsoft Teams differentiates between guest users and external users in the app. While it's important to understand how each of these are treated in Teams, both types of users are B2B users in Azure AD and the recommended policies for B2B users apply to both.

-->

Azure AD B2B hesabı olan konuk ve dış kullanıcılara erişim izni vermeyle ilgili önerilen ilkeler için bkz. Konuk ve dış [B2B](identity-access-policies-guest-access.md) hesabı erişimine izin verme ilkeleri.

### <a name="guest-access-in-teams"></a>Web'de konuk Teams

yöneticiler, işletmeniz veya kuruluş içinde yer alan kullanıcılara yönelik ilkelere ek olarak, kullanıcı temelinde, işletmeniz veya kuruluş dışından kişilerin Teams kaynaklarına erişmesine ve grup konuşmaları, sohbet ve toplantılar gibi içerikler için şirket içi kişilerle etkileşim kurmasına izin vermesine olanak siliyor olabilir.

Konuk erişimi ve bunu nasıl uygulayıla ilgili daha fazla bilgi için bkz[. Teams erişme.](/microsoftteams/guest-access)

### <a name="external-access-in-teams"></a>Dış erişim Teams

Dış erişim bazen konuk erişimiyle karıştırılır, bu nedenle bu iki iç erişim mekanizmasının farklı erişim türleri olduğu açıkça ifade etmek önemlidir.

Dış erişim, tüm dış Teams kullanan kullanıcıların aynı etki alanında kullanıcılarınıza özel olarak toplantı bulma, arama, sohbet ve toplantı ayarlama Teams. Teams dış erişimi kuruluş düzeyinde yapılandıran yöneticiler vardır. Daha fazla bilgi için bkz[. Dış erişimi Microsoft Teams](/microsoftteams/manage-external-access).

Dış erişim kullanıcıları, konuk erişimi yoluyla eklenen kişilerden daha az erişime ve işleve sahip olur. Örneğin, dış erişim kullanıcıları şirket içi kullanıcılarınız ile sohbet edip diğer Teams kanallarına, dosyalara ve diğer kaynaklara erişamaz.

Dış erişim, Azure AD B2B kullanıcı hesaplarını kullanmaz ve dolayısıyla Koşullu Erişim ilkelerini kullanmaz.

## <a name="teams-policies"></a>Teams ilkeleri

Yukarıda listelenen ortak ilkelerin dışında, çeşitli Teams yönetmek üzere yapılandırılan ve özel ilkeler Teams vardır.

### <a name="teams-and-channels-policies"></a>Teams ve kanal ilkeleri

Teams kanalları, Microsoft Teams'de yaygın olarak kullanılan iki öğedir ve ekipleri ve kanalları kullanırken kullanıcıların neler yapasa da neler yapa bir şeyi yapamalarını denetlemeye yönelik ilkeler koyabilirsiniz. Bir genel ekip oluştursanız da, kuruluşta 5000 veya daha az kullanıcı varsa, kurumsal gereklerle belirli amaçlarla daha küçük ekipler ve kanallara sahip olmak size yardımcı olabilir.

Varsayılan ilkenin değiştirilmesi veya özel ilke oluşturulması önerilir. İlkelerinizi yönetme hakkında daha fazla bilgi edinmek için şu bağlantıdan edinebilirsiniz[: Microsoft Teams](/microsoftteams/teams-policies).

### <a name="messaging-policies"></a>Mesajlaşma ilkeleri

Mesajlaşma veya sohbet, varsayılan genel ilkeler veya özel ilkeler aracılığıyla da yönetilebilir ve bu da kullanıcılarının, birbirleriyle kuruma uygun şekilde iletişim kurmalarına yardımcı olabilir. Bu bilgiler, [Teams'de mesajlaşma ilkelerini yönetme altında Teams](/microsoftteams/messaging-policies-in-teams).

### <a name="meeting-policies"></a>Toplantı ilkeleri

Her toplantı Teams ilkeler planlamadan ve uygulanmadan hiçbir tartışma Teams tamamlanır. Toplantılar, kişilerin aynı anda birçok Teams resmi olarak to arayanı, sunarak, toplantıyla ilgili içeriği paylaşmasına olanak sağlayan temel bir bileşendir. Toplantıların çevresinde kurum için doğru ilkelerin ayarının olması çok önemlidir.

Daha fazla bilgi için, toplantı [ilkelerini tek bir Teams](/microsoftteams/meeting-policies-in-teams).

### <a name="app-permission-policies"></a>Uygulama izin ilkeleri

Teams, uygulamaları kanal veya kişisel sohbet gibi çeşitli yerlerde kullanmanızı da sağlar. Hangi uygulamaların ek gerek kullanılay, hem de güvenli, içerik açısından zengin bir ortamı korumak için ilkelere sahip olmak temel öneme sahiptir.

Uygulama İzin İlkeleri hakkında daha fazla bilgi için, [Microsoft Teams.](/microsoftteams/teams-app-permission-policies)

## <a name="next-steps"></a>Sonraki adımlar

![4. Adım: Bulut Microsoft 365 için ilkeler.](../../media/microsoft-365-policies-configurations/identity-device-access-steps-next-step-4.png)

Koşullu Erişim ilkelerini aşağıdakiler için yapılandırma:

- [Exchange Online](secure-email-recommended-policies.md)
- [SharePoint](sharepoint-file-access-policies.md)