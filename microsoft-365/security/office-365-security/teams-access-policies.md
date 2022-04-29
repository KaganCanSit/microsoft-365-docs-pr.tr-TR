---
title: Önerilen Teams ilkeleri - Kurumsal | için Microsoft 365 Microsoft Docs
description: Teams iletişiminin ve dosya erişiminin güvenliğini sağlama hakkında Microsoft önerilerine yönelik ilkeleri açıklar.
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
ms.openlocfilehash: 25f70d3ccdf11daa6a52d16b66d612c04ab8876a
ms.sourcegitcommit: fdd0294e6cda916392ee66f5a1d2a235fb7272f8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/29/2022
ms.locfileid: "65131184"
---
# <a name="policy-recommendations-for-securing-teams-chats-groups-and-files"></a>Teams sohbetlerinin, gruplarının ve dosyalarının güvenliğini sağlamaya yönelik ilke önerileri

Bu makalede, Microsoft Teams sohbetlerini, gruplarını ve dosyalar ve takvimler gibi içerikleri korumak için önerilen Sıfır Güven kimlik ve cihaz erişim ilkelerinin nasıl uygulandığı açıklanmaktadır. Bu kılavuz, Teams'e özgü ek bilgilerle [birlikte ortak kimlik ve cihaz erişim ilkelerine](identity-access-policies.md) dayalıdır. Teams diğer ürünlerimizle tümleştirdiğinden bkz. [SharePoint sitelerini ve dosyalarını güvenli hale getirmek için ilke önerileri ve](sharepoint-file-access-policies.md) [e-postanın güvenliğini sağlamaya yönelik ilke önerileri](secure-email-recommended-policies.md).

Bu öneriler, Teams için gereksinimlerinizin ayrıntı düzeyine göre uygulanabilen üç farklı güvenlik ve koruma katmanını temel alır: başlangıç noktası, kuruluş ve özel güvenlik. [Kimlik ve cihaz erişim yapılandırmalarında](microsoft-365-policies-configurations.md) bu güvenlik katmanları ve bu öneriler tarafından başvurulan önerilen ilkeler hakkında daha fazla bilgi edinebilirsiniz.

Kuruluşunuz dışındaki kullanıcılar da dahil olmak üzere belirli kimlik doğrulama koşullarını ele almak için bu makalede Teams dağıtımına özgü daha fazla öneri yer alır. Eksiksiz bir güvenlik deneyimi için bu kılavuzu izlemeniz gerekir.

## <a name="getting-started-with-teams-before-other-dependent-services"></a>Diğer bağımlı hizmetlerden önce Teams'i kullanmaya başlama

Microsoft Teams'i kullanmaya başlamak için bağımlı hizmetleri etkinleştirmeniz gerekmez. Bu hizmetlerin tümü "yalnızca çalışır". Ancak, hizmetle ilgili aşağıdaki öğeleri yönetmeye hazırlıklı olmanız gerekir:

- Microsoft 365 grupları
- SharePoint ekip siteleri
- OneDrive İş
- Exchange posta kutuları
- Video akışı ve Planner planları (bu hizmetler etkinse)

## <a name="updating-common-policies-to-include-teams"></a>Sık kullanılan ilkeleri Teams'i içerecek şekilde güncelleştirme

Teams'de sohbeti, grupları ve içeriği korumak için, aşağıdaki diyagramda ortak kimlik ve cihaz erişim ilkelerinden hangi ilkelerin güncelleştirildiği gösterilmektedir. Her ilkenin güncelleştirilmesini sağlamak için Teams'in ve bağımlı hizmetlerin bulut uygulamalarının atamasına dahil olduğundan emin olun.

:::image type="content" source="../../media/microsoft-365-policies-configurations/identity-access-ruleset-teams.png" alt-text="Teams'e ve bağlı hizmetlerine erişimin korunmasına yönelik ilke güncelleştirmelerinin özeti" lightbox="../../media/microsoft-365-policies-configurations/identity-access-ruleset-teams.png":::

Bu hizmetler, Teams için bulut uygulamalarının atamasına dahil etmek üzere bağımlı hizmetlerdir:

- Microsoft Teams
- SharePoint ve OneDrive İş
- Exchange Online
- Skype Kurumsal Çevrimiçi
- Microsoft Stream (toplantı kayıtları)
- Microsoft Planner (Planner görevleri ve plan verileri)

Bu tabloda, yeniden ziyaret edilmesi gereken ilkeler listelenir ve tüm Office uygulamaları için daha geniş bir ilke kümesine sahip olan [ortak kimlik ve cihaz erişim ilkelerindeki](identity-access-policies.md) her ilkeye bağlantı sağlanır.

|Koruma düzeyi|İlkeler|Teams uygulaması için daha fazla bilgi|
|---|---|---|
|**Başlangıç noktası**|[Oturum açma riski *orta* veya *yüksek* olduğunda MFA gerektirme](identity-access-policies.md#require-mfa-based-on-sign-in-risk)|Teams ve bağımlı hizmetlerin uygulama listesine eklendiğinden emin olun. Teams'in de dikkate alınması gereken Konuk Erişimi ve Dış Erişim kuralları vardır. Bu kuralları daha sonra bu makalenin devamında öğreneceksiniz.|
||[Modern kimlik doğrulamayı desteklemeyen istemcileri engelleme](identity-access-policies.md#block-clients-that-dont-support-multi-factor)|Bulut uygulamalarının atanma aşamasına Teams'i ve bağımlı hizmetleri dahil edin.|
||[Yüksek riskli kullanıcıların parola değiştirmesi gerekir](identity-access-policies.md#high-risk-users-must-change-password)|Teams kullanıcılarını, hesapları için yüksek riskli etkinlik algılanırsa oturum açarken parolalarını değiştirmeye zorlar. Teams ve bağımlı hizmetlerin uygulama listesine eklendiğinden emin olun.|
||[APP veri koruma ilkelerini uygulama](identity-access-policies.md#apply-app-data-protection-policies)|Teams ve bağımlı hizmetlerin uygulama listesine eklendiğinden emin olun. Her platform (iOS, Android, Windows) için ilkeyi güncelleştirin.|
|**Enterprise**|[Oturum açma riski *düşük*, *orta* veya *yüksek* olduğunda MFA gerektirme](identity-access-policies.md#require-mfa-based-on-sign-in-risk)|Teams'in de dikkate alınması gereken Konuk Erişimi ve Dış Erişim kuralları vardır. Bu kuralları daha sonra bu makalenin devamında öğreneceksiniz. Teams'i ve bağımlı hizmetleri bu ilkeye dahil edin.|
||[Cihaz uyumluluk ilkelerini tanımlama](identity-access-policies.md#define-device-compliance-policies)|Teams'i ve bağımlı hizmetleri bu ilkeye dahil edin.|
||[Uyumlu bilgisayarlar *ve* mobil cihazlar gerektirme](identity-access-policies.md#require-compliant-pcs-and-mobile-devices)|Teams'i ve bağımlı hizmetleri bu ilkeye dahil edin.|
|**Özel güvenlik**|[*Her zaman* MFA iste](identity-access-policies.md#require-mfa-based-on-sign-in-risk)|Kullanıcı kimliği ne olursa olsun, MFA kuruluşunuz tarafından kullanılır. Teams'i ve bağımlı hizmetleri bu ilkeye dahil edin. |

## <a name="teams-dependent-services-architecture"></a>Teams'e bağımlı hizmetler mimarisi

Başvuru için aşağıdaki diyagramda Teams'in bağlı olduğu hizmetler gösterilmektedir. Daha fazla bilgi ve çizim için bkz. [BT mimarları için Microsoft 365'te Microsoft Teams ve ilgili üretkenlik hizmetleri](../../solutions/productivity-illustrations.md).

:::image type="content" source="../../media/microsoft-365-policies-configurations/identity-access-logical-architecture-teams.png" alt-text="SharePoint, OneDrive İş ve Exchange'de Teams bağımlılıklarını gösteren diyagram" lightbox="../../media/microsoft-365-policies-configurations/identity-access-logical-architecture-teams.png":::

## <a name="guest-and-external-access-for-teams"></a>Teams için konuk ve dış erişim

Microsoft Teams aşağıdaki erişim türlerini tanımlar:

- **Konuk erişimi** , bir ekibin üyesi olarak eklenebilen ve ekibin iletişimine ve kaynaklarına tüm izinlere sahip olan bir konuk veya dış kullanıcı için Azure AD B2B hesabı kullanır.

- **Dış erişim** , Azure AD B2B hesabı olmayan bir dış kullanıcıya yöneliktir. Dış erişim davetleri ve aramalara, sohbetlere ve toplantılara katılmayı içerebilir, ancak ekip üyeliğini ve ekibin kaynaklarına erişimi içermez.

Koşullu Erişim ilkeleri yalnızca Teams'deki konuk erişimi için geçerlidir çünkü buna karşılık gelen bir Azure AD B2B hesabı vardır.

<!--
In Azure AD, guest and external users are the same. The user type for both of these is Guest. Guest users are B2B users. Microsoft Teams differentiates between guest users and external users in the app. While it's important to understand how each of these are treated in Teams, both types of users are B2B users in Azure AD and the recommended policies for B2B users apply to both.

-->

Azure AD B2B hesabı olan konuk ve dış kullanıcılara erişim izni vermek [için önerilen ilkeler için bkz. Konuk ve dış B2B hesabı erişimine izin verme ilkeleri](identity-access-policies-guest-access.md).

### <a name="guest-access-in-teams"></a>Teams'de konuk erişimi

İşletmenizin veya kuruluşunuzun içindeki kullanıcılara yönelik ilkelere ek olarak, yöneticiler, işletmenizin veya kuruluşunuzun dışındaki kişilerin Teams kaynaklarına erişmesine ve grup konuşmaları, sohbet ve toplantılar gibi konularda şirket içi kişilerle etkileşim kurmasına izin vermek için konuk erişimini etkinleştirebilir.

Konuk erişimi ve bunu uygulama hakkında daha fazla bilgi için bkz.  [Teams konuk erişimi](/microsoftteams/guest-access).

### <a name="external-access-in-teams"></a>Teams'de dış erişim

Dış erişim bazen konuk erişimiyle karıştırılır, bu nedenle bu iki iç olmayan erişim mekanizmasının farklı erişim türleri olduğunu net bir şekilde belirtmek önemlidir.

Dış erişim, bir dış etki alanının tamamından Teams kullanıcılarının Teams'de kullanıcılarınızla toplantılar bulmasını, aramasını, sohbet etmesini ve ayarlamasını sağlamanın bir yoludur. Teams yöneticileri kuruluş düzeyinde dış erişimi yapılandırabilir. Daha fazla bilgi için bkz. [Microsoft Teams'de dış erişimi yönetme](/microsoftteams/manage-external-access).

Dış erişim kullanıcıları, konuk erişimi aracılığıyla eklenen bir kişiye göre daha az erişime ve işlevselliğe sahiptir. Örneğin, dış erişim kullanıcıları Teams ile iç kullanıcılarınızla sohbet edebilir ancak ekip kanallarına, dosyalarına veya diğer kaynaklara erişemez.

Dış erişim, Azure AD B2B kullanıcı hesaplarını kullanmaz ve bu nedenle Koşullu Erişim ilkelerini kullanmaz.

## <a name="teams-policies"></a>Teams ilkeleri

Yukarıda listelenen yaygın ilkelerin dışında, çeşitli Teams işlevlerini yönetmek için yapılandırılabilir ve yapılandırılması gereken Teams'e özgü ilkeler vardır.

### <a name="teams-and-channels-policies"></a>Ekipler ve kanal ilkeleri

Teams ve kanallar, Microsoft Teams'de yaygın olarak kullanılan iki öğedir ve ekipleri ve kanalları kullanırken kullanıcıların neler yapabileceğini ve yapamayacağını denetlemek için kullanabileceğiniz ilkeler vardır. Küresel bir ekip oluşturabilirsiniz ancak kuruluşunuzda 5000 veya daha az kullanıcı varsa, kuruluşunuzun ihtiyaçlarına uygun olarak belirli amaçlarla daha küçük ekiplere ve kanallara sahip olmak yararlı olabilir.

Varsayılan ilkenin değiştirilmesi veya özel ilkeler oluşturulması önerilir ve ilkelerinizi yönetme hakkında daha fazla bilgiyi şu bağlantıdan öğrenebilirsiniz: [Microsoft Teams'de ekip ilkelerini yönetme](/microsoftteams/teams-policies).

### <a name="messaging-policies"></a>Mesajlaşma ilkeleri

Mesajlaşma veya sohbet, varsayılan genel ilke veya özel ilkeler aracılığıyla da yönetilebilir ve bu, kullanıcılarınızın kuruluşunuza uygun bir şekilde birbirleriyle iletişim kurmasını sağlayabilir. Bu bilgiler [Teams'de mesajlaşma ilkelerini yönetme](/microsoftteams/messaging-policies-in-teams) bölümünde gözden geçirilebilir.

### <a name="meeting-policies"></a>Toplantı ilkeleri

Teams toplantıları çevresinde ilkeler planlamadan ve uygulamadan Teams hakkında hiçbir tartışma tamamlanamaz. Toplantılar, Teams'in temel bileşenlerinden biridir. Bu sayede kişiler aynı anda birçok kullanıcıyla resmi olarak tanışıp sunular ve toplantıyla ilgili içerikleri paylaşabilir. Toplantılar etrafında kuruluşunuz için doğru ilkelerin ayarlanması çok önemlidir.

Daha fazla bilgi için [Teams'de toplantı ilkelerini yönetme makalesini](/microsoftteams/meeting-policies-in-teams) gözden geçirin.

### <a name="app-permission-policies"></a>Uygulama izin ilkeleri

Teams ayrıca uygulamaları kanallar veya kişisel sohbetler gibi çeşitli yerlerde kullanmanıza olanak tanır. Hangi uygulamaların eklenip kullanılabileceğini ve nerede kullanılabileceğini belirten ilkelere sahip olmak, aynı zamanda güvenli içerik açısından zengin bir ortamın korunması için çok önemlidir.

Uygulama İzin İlkeleri hakkında daha fazla bilgi için [Bkz. Microsoft Teams'de uygulama izin ilkelerini yönetme](/microsoftteams/teams-app-permission-policies).

## <a name="next-steps"></a>Sonraki adımlar

:::image type="content" source="../../media/microsoft-365-policies-configurations/identity-device-access-steps-next-step-4.png" alt-text="4. Adım: Microsoft 365 bulut uygulamaları için ilkeler" lightbox="../../media/microsoft-365-policies-configurations/identity-device-access-steps-next-step-4.png":::

Koşullu Erişim ilkelerini yapılandırma:

- [Exchange Online](secure-email-recommended-policies.md)
- [SharePoint](sharepoint-file-access-policies.md)
