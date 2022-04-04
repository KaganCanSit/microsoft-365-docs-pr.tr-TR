---
title: Konuk ve dış kullanıcı B2B erişimine izin veren kimlik ve cihaz erişim ilkeleri - Microsoft 365 erişimi için | Microsoft Docs
description: Konukların ve dış kullanıcıların erişimini korumak için önerilen Koşullu Erişim ve ilgili ilkeleri açıklar.
ms.prod: m365-security
ms.topic: article
ms.author: dansimp
author: dansimp
audience: Admin
manager: Laurawi
f1.keywords:
- NOCSH
ms.reviewer: martincoetzer
ms.custom:
- it-pro
- goldenconfig
ms.collection:
- M365-identity-device-management
- M365-security-compliance
- m365solution-identitydevice
- m365solution-scenario
ms.technology: mdo
ms.openlocfilehash: 28b389292ed733318e5796a1be3ed9c11d2df462
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64466619"
---
# <a name="policies-for-allowing-guest-access-and-b2b-external-user-access"></a>Konuk erişimine izin veren ilkeler ve B2B dış kullanıcı erişimi

Bu makalede, Azure Active Directory (Azure AD) İş-İş (B2B) hesabı olan konuklara ve dış kullanıcılara erişim izni vermek için önerilen Sıfır Güven kimlik ve cihaz erişimi ilkelerini ayarlama konuları açıklanmıştır. Bu kılavuz, ortak kimlik [ve cihaz erişim ilkelerine yöneliktir](identity-access-policies.md).

Bu öneriler korumanın başlangıç noktası **katmanına uygulanacak** şekilde tasarlanmıştır. Ancak önerileri, kurumsal ve özel güvenlik korumasına yönelik özel **ihtiyaçlarınıza göre** **de ayarlayabilirsiniz** .

B2B hesaplarının Azure AD kiracınız ile kimlik doğrulaması yapma yolu sağlamak, bu hesapların tüm ortamınıza erişmesini sağlamaz. B2B kullanıcıları ve onların hesapları, Koşullu Erişim ilkesiyle paylaşılan dosyalar gibi hizmetlere ve kaynaklara erişim sağlar.

## <a name="updating-the-common-policies-to-allow-and-protect-guests-and-external-user-access"></a>Konuklara ve dış kullanıcı erişimine izin vermek ve onları korumak için genel ilkeleri güncelleştirme

Bu diyagramda, B2B konuk ve dış kullanıcı erişimi için ortak kimlik ve cihaz erişimi ilkeleri arasında hangi ilkelerin ekli veya güncelleştiriliyor olduğu görünür.

:::image type="content" source="../../media/microsoft-365-policies-configurations/identity-access-ruleset-guest.png" alt-text="Konuk erişimini korumak için ilke güncelleştirmelerinin özeti" lightbox="../../media/microsoft-365-policies-configurations/identity-access-ruleset-guest.png":::

Aşağıdaki tabloda, oluşturmanız ve güncelleştirmeniz gereken ilkeler listelemektedir. Ortak ilkeler, Ortak kimlik ve cihaz erişimi ilkeleri [makalesinde yer alan ilişkili yapılandırma yönergelerine](identity-access-policies.md) bağlantı sağlar.

|Koruma düzeyi|İlkeler|Daha fazla bilgi|
|---|---|---|
|**Başlangıç noktası**|[Konuklar ve dış kullanıcılar için her zaman MFA gerektirme](identity-access-policies.md#require-mfa-based-on-sign-in-risk)|Bu yeni ilkeyi oluşturun ve yapılandıryın: <ul><li>**Ödevler ve > Dahil > için** Kullanıcıları ve grupları seç'i ve ardından Tüm konuk ve **dış kullanıcılar'ı seçin**.</li><li>**Ödevler ve > Oturum >** için, çok faktörlü kimlik doğrulamasını (MFA) her zaman zorunlu tutulacak şekilde tüm seçenekleri işaretsiz bırakın.</li></ul>|
||[Oturum açma riski orta veya yüksek olduğunda MFA  *gerektirme*](identity-access-policies.md#require-mfa-based-on-sign-in-risk)|Konukları ve dış kullanıcıları dışlamak için bu ilkeyi değiştirebilirsiniz.|

Koşullu Erişim ilkelerine konukları ve dış kullanıcıları dahil etmek veya dış kullanıcıları dahil etmek için, **Ödevler > Kullanıcılar ve gruplar >'de** **Tüm konuk** ve dış **kullanıcılar'a göz seçin**.

:::image type="content" source="../../media/microsoft-365-policies-configurations/identity-access-exclude-guests-ui.png" alt-text="Konuklar ve dış kullanıcılar hariç tutulan denetimler" lightbox="../../media/microsoft-365-policies-configurations/identity-access-exclude-guests-ui.png":::

## <a name="more-information"></a>Daha fazla bilgi

### <a name="guests-and-external-user-access-with-microsoft-teams"></a>Konuk ve dış kullanıcı erişimi için Microsoft Teams

Microsoft Teams kullanıcıları tanımlar:

- **Konuk erişiminde** , bir ekibin üyesi olarak eklenilen ve ekibin iletişim ve kaynaklarına erişimi olan bir Azure AD B2B hesabı kullanılabilir.

- **Dış erişim** , B2B hesabı olmayan dış kullanıcılara özeldir. Dış kullanıcı erişimi davetleri, aramaları, sohbetleri ve toplantıları içerir, ancak ekip üyeliğini ve ekibin kaynaklarına erişimi içermez.

Daha fazla bilgi için bkz. [Ekipler için konuk ve dış kullanıcı erişimi karşılaştırması](/microsoftteams/communicate-with-users-from-other-organizations#compare-external-and-guest-access).

Sohbetler, gruplar ve dosyaların güvenliğini sağlama hakkında daha fazla Teams için bkz. Sohbetlerin, grupların [ve dosyaların güvenliğini Teams ilke önerileri](teams-access-policies.md).

### <a name="require-mfa-always-for-guest-and-external-users"></a>Konuk ve dış kullanıcılar için her zaman MFA gerektir

Bu ilke, konukların ev kiracılarında MFA için kaydedilmiş olup olmadığına bakılmaksızın kiracınıza MFA'da kaydolmalarını ister. Kiracınıza kaynaklara erişirken, konukların ve dış kullanıcıların her istekte MFA kullanmaları gerekir.

### <a name="excluding-guests-and-external-users-from-risk-based-mfa"></a>Konuklar ve dış kullanıcıları risk tabanlı MFA'dan dışlama

Kuruluşlar Azure AD Kimlik Koruması kullanan B2B kullanıcıları için risk tabanlı ilkeleri zorunlu ksasa da, giriş dizinlerinde var olan kimliklerinden dolayı kaynak dizininde B2B işbirliği kullanıcıları için Azure AD Kimlik Koruması'nın uygulanmasında sınırlamalar vardır. Bu sınırlamalar nedeniyle, Microsoft konukları risk tabanlı MFA ilkelerinin dışında değerlendirmenizi önermektedir ve bu kullanıcıların her zaman MFA kullanmalarını gerektirir.

Daha fazla bilgi için [B2B işbirliği kullanıcıları için Kimlik Koruması sınırlamaları' belgesine bakın](/azure/active-directory/identity-protection/concept-identity-protection-b2b#limitations-of-identity-protection-for-b2b-collaboration-users).

### <a name="excluding-guests-and-external-users-from-device-management"></a>Konuklar ve dış kullanıcılar cihaz yönetiminden dışlama

Bir cihazı yalnızca bir kuruluş yönetebilir. Konukları ve dış kullanıcıları cihaz uyumluluğu gerektiren ilkelerden çıkaramazsanız, bu ilkeler bu kullanıcıları engelleyebilir.

## <a name="next-step"></a>Sonraki adım

:::image type="content" source="../../media/microsoft-365-policies-configurations/identity-device-access-steps-next-step-4.png" alt-text="Bulut uygulamaları Microsoft 365 için ilkeler Microsoft Defender for Cloud Apps" lightbox="../../media/microsoft-365-policies-configurations/identity-device-access-steps-next-step-4.png":::

Koşullu Erişim ilkelerini aşağıdakiler için yapılandırma:

- [Microsoft Teams](teams-access-policies.md)
- [Exchange Online](secure-email-recommended-policies.md)
- [SharePoint](sharepoint-file-access-policies.md)
- [Bulut Uygulamaları için Microsoft Defender](mcas-saas-access-policies.md)
 
