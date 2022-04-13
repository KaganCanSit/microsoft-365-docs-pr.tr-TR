---
title: Microsoft 365 İş Ekstra için güvenlik varsayılanlarını açma
f1.keywords:
- NOCSH
ms.author: sharik
author: SKjerland
manager: scotv
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Adm_O365
- M365-subscription-management
- M365-identity-device-management
- M365-Campaigns
- m365solution-smb
ms.custom:
- Adm_O365
- MiniMaven
- MSB365
search.appverid:
- BCS160
- MET150
- MOE150
description: Güvenlik varsayılanlarının, Microsoft 365 İş Ekstra için önceden yapılandırılmış güvenlik ayarları sağlayarak kuruluşunuzun kimlikle ilgili saldırılara karşı korunmasına nasıl yardımcı olabileceğini öğrenin.
ms.openlocfilehash: 58477da3d44844c763dff95d35fc71753afc7ce2
ms.sourcegitcommit: 195e4734d9a6e8e72bd355ee9f8bca1f18577615
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/13/2022
ms.locfileid: "64824520"
---
# <a name="turn-on-security-defaults-for-microsoft-365-business-premium"></a>Microsoft 365 İş Ekstra için güvenlik varsayılanlarını açma

Güvenlik varsayılanları, Microsoft'un kuruluşunuz adına yönettiği önceden yapılandırılmış güvenlik ayarları sağlayarak kuruluşunuzu kimlikle ilgili saldırılara karşı korumaya yardımcı olur. Bu ayarlar, tüm yöneticiler ve kullanıcı hesapları için çok faktörlü kimlik doğrulamasını (MFA) etkinleştirmeyi içerir. Çoğu kuruluş için güvenlik varsayılanları iyi bir düzeyde ek oturum açma güvenliği sunar.

Güvenlik varsayılanları ve uyguladıkları ilkeler hakkında daha fazla bilgi için bkz. [Güvenlik varsayılanları nedir?](/azure/active-directory/fundamentals/concept-fundamentals-security-defaults)

Aboneliğiniz 22 Ekim 2019 veya sonrasında oluşturulduysa, güvenlik varsayılanları sizin için otomatik olarak etkinleştirilmiş olabilir, onaylamak için&mdash; ayarlarınızı denetlemeniz gerekir.

Azure Active Directory 'nizde (Azure AD) güvenlik varsayılanlarını etkinleştirmek veya bunların zaten etkin olup olmadığını denetlemek için:

1. güvenlik yöneticisi, Koşullu Erişim yöneticisi veya Genel yönetici kimlik bilgileriyle <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 yönetim merkezi</a> oturum açın.

2. Sol bölmede **Tümünü Göster'i** seçin ve ardından **Yönetim merkezleri'nin** altında **Azure Active Directory'ı** seçin.

3. **Azure Active Directory yönetim merkezinin** sol bölmesinde **Azure Active Directory'ı** seçin.

4. Panonun sol menüsündeki **Yönet** bölümünde **Özellikler'i** seçin.

    :::image type="content" source="../media/m365-campaigns-conditional-access/azure-ad-properties.png" alt-text="Özellikler menü öğesinin konumunu gösteren Azure Active Directory yönetim merkezinin ekran görüntüsü.":::

5. **Özellikler** sayfasının en altında **Güvenlik varsayılanlarını yönet'i** seçin.

6. Sağ bölmede **Güvenlik varsayılanlarını etkinleştir** ayarını görürsünüz. **Evet** seçiliyse, güvenlik varsayılanları zaten etkindir ve başka bir eylem gerekmez. Güvenlik varsayılanları şu anda etkin değilse, etkinleştirmek için **Evet'i** ve ardından **Kaydet'i** seçin.

> [!NOTE]
> Koşullu Erişim ilkelerini kullanıyorsanız, güvenlik varsayılanlarını kullanmadan önce bunları kapatmanız gerekir.
>
> Güvenlik varsayılanlarını veya Koşullu Erişim ilkelerini kullanabilirsiniz, ancak ikisini de aynı anda kullanamazsınız.

## <a name="consider-using-conditional-access"></a>Koşullu Erişim kullanmayı göz önünde bulundurun

Kuruluşunuzun karmaşık güvenlik gereksinimleri varsa veya güvenlik ilkeleriniz üzerinde daha ayrıntılı denetime ihtiyacınız varsa, benzer veya daha yüksek bir güvenlik duruşu elde etmek için güvenlik varsayılanları yerine Koşullu Erişim'i kullanmayı düşünmelisiniz. 

Koşullu Erişim, oturum açma olaylarına tepki veren ve kullanıcıya uygulama veya hizmete erişim verilmeden önce ek eylemler isteyen ilkeler oluşturmanıza ve tanımlamanıza olanak tanır. Koşullu Erişim ilkeleri ayrıntılı ve belirli olabilir, kullanıcıları her yerde ve her zaman üretken olmaya teşvik edebilir, aynı zamanda kuruluşunuzu koruyabilir.

Güvenlik varsayılanları tüm müşteriler tarafından kullanılabilirken Koşullu Erişim aşağıdaki planlardan biri için lisans gerektirir:

- Azure Active Directory Premium P1 veya P2
- Microsoft 365 Business Premium
- Microsoft 365 E3 veya E5
- Enterprise Mobility & Security E3 veya E5

Koşullu Erişim'i kullanarak güvenlik varsayılanları tarafından etkinleştirilen ilkelerle eşdeğer ilkeler yapılandırmak istiyorsanız aşağıdaki adım adım kılavuzlara göz atın:

- [Yöneticiler için MFA gerektir](/azure/active-directory/conditional-access/howto-conditional-access-policy-admin-mfa)

- [Azure yönetimi için MFA gerektirme](/azure/active-directory/conditional-access/howto-conditional-access-policy-azure-management)

- [Eski kimlik doğrulamasını engelle](/azure/active-directory/conditional-access/howto-conditional-access-policy-block-legacy)

- [Tüm kullanıcılar için MFA gerektir](/azure/active-directory/conditional-access/howto-conditional-access-policy-all-users-mfa)

- [Azure AD MFA kaydını gerektir](/azure/active-directory/identity-protection/howto-identity-protection-configure-mfa-policy) - Azure Active Directory Premium P2 parçası olan Azure AD Kimlik Koruması gerektirir

Koşullu Erişim hakkında daha fazla bilgi edinmek için bkz. [Koşullu Erişim nedir?](/azure/active-directory/conditional-access/overview) Koşullu Erişim ilkeleri oluşturma hakkında daha fazla bilgi için bkz. [Koşullu Erişim ilkesi oluşturma](/azure/active-directory/authentication/tutorial-enable-azure-mfa#create-a-conditional-access-policy).

> [!NOTE]
> Koşullu Erişim sağlayan bir planınız veya lisansınız varsa ancak henüz herhangi bir Koşullu Erişim ilkesi oluşturmadıysanız, güvenlik varsayılanlarını kullanabilirsiniz. Ancak, Koşullu Erişim ilkelerini kullanabilmeniz için önce güvenlik varsayılanlarını kapatmanız gerekir.
