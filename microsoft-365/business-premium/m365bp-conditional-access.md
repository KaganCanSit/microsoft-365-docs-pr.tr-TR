---
title: Güvenlik varsayılanları ve Koşullu Erişim
f1.keywords:
- NOCSH
ms.author: deniseb
author: denisebmsft
manager: dansimp
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: high
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
ms.openlocfilehash: af9b19dcf33f1b79d4057662cf759ace27aec38f
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65095278"
---
# <a name="security-defaults-and-multi-factor-authentication"></a>Güvenlik varsayılanları ve çok faktörlü kimlik doğrulaması

Microsoft 365 İş Ekstra, önceden yapılandırılmış güvenlik ayarlarıyla şirketinizin kullanıcı hesaplarını korumaya yardımcı olmak için tasarlanmıştır. Bu ayarlar, tüm yöneticileriniz ve kullanıcı hesaplarınız için çok faktörlü kimlik doğrulamasını (MFA) etkinleştirmeyi içerir. Çoğu kuruluş için güvenlik varsayılanları iyi bir oturum açma güvenliği düzeyi sunar.

Güvenlik varsayılanları ve uyguladıkları ilkeler hakkında daha fazla bilgi için bkz. [Güvenlik varsayılanları nedir?](/azure/active-directory/fundamentals/concept-fundamentals-security-defaults)

Bu makalede aşağıdakiler hakkında bilgi sağlanır:

- [Güvenlik varsayılanları](#security-defaults) (çoğu işletme için uygundur)
- [Koşullu Erişim](#conditional-access) (daha sıkı güvenlik gereksinimleri olan işletmeler için)

> [!NOTE]
> Koşullu Erişim ilkelerini kullanıyorsanız, güvenlik varsayılanlarını kullanmadan önce bunları kapatmanız gerekir. Güvenlik varsayılanlarını veya Koşullu Erişim ilkelerini kullanabilirsiniz, ancak ikisini de aynı anda kullanamazsınız.

## <a name="security-defaults"></a>Güvenlik varsayılanları

Güvenlik varsayılanları, şirketinizin kullanıcı hesaplarını baştan korumaya yardımcı olmak için tasarlanmıştır. Güvenlik varsayılanları etkinleştirildiğinde, şirketinizin güvenliğini sağlamaya yardımcı olan güvenli varsayılan ayarlar sağlar:

- Tüm kullanıcıların ve yöneticilerin Microsoft Authenticator uygulamasını kullanarak MFA'ya kaydolmasını gerektirme.
- MFA'ya sahip zorlayıcı kullanıcılar, çoğunlukla yeni bir cihazda veya uygulamada gösterildiğinde, ancak daha çok kritik roller ve görevler için.
- MFA yapabilen eski kimlik doğrulama istemcilerinden kimlik doğrulamasını devre dışı bırakma.
- Her oturum açtıklarında fazladan kimlik doğrulaması gerektirerek yöneticileri koruma.

MFA, şirketinizin güvenliğini sağlamanın önemli bir ilk adımıdır ve güvenlik varsayılanları MFA'nın uygulanmasını kolaylaştırır. Aboneliğiniz 22 Ekim 2019 veya sonrasında oluşturulduysa, güvenlik varsayılanları sizin için otomatik olarak etkinleştirilmiş olabilir, onaylamak için&mdash; ayarlarınızı denetlemeniz gerekir.

> [!TIP]
> Güvenlik varsayılanları ve uyguladıkları ilkeler hakkında daha fazla bilgi için bkz. [Güvenlik varsayılanları nedir?](/azure/active-directory/fundamentals/concept-fundamentals-security-defaults)

### <a name="to-enable-security-defaults-or-confirm-theyre-already-enabled"></a>Güvenlik varsayılanlarını etkinleştirmek (veya zaten etkin olduklarını onaylamak) için

1. güvenlik yöneticisi, Koşullu Erişim yöneticisi veya Genel yönetici kimlik bilgileriyle <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 yönetim merkezi</a> oturum açın.

2. Sol bölmede **Tümünü Göster'i** seçin ve ardından **Yönetim merkezleri'nin** altında **Azure Active Directory'ı** seçin.

3. **Azure Active Directory yönetim merkezinin** sol bölmesinde **Azure Active Directory'ı** seçin.

4. Panonun sol menüsündeki **Yönet** bölümünde **Özellikler'i** seçin.

    :::image type="content" source="../media/m365-campaigns-conditional-access/azure-ad-properties.png" alt-text="Özellikler menü öğesinin konumunu gösteren Azure Active Directory yönetim merkezinin ekran görüntüsü.":::

5. **Özellikler** sayfasının en altında **Güvenlik varsayılanlarını yönet'i** seçin.

6. Sağ bölmede **Güvenlik varsayılanlarını etkinleştir** ayarını görürsünüz. **Evet** seçiliyse, güvenlik varsayılanları zaten etkindir ve başka bir eylem gerekmez. Güvenlik varsayılanları şu anda etkin değilse, etkinleştirmek için **Evet'i** ve ardından **Kaydet'i** seçin.

## <a name="conditional-access"></a>Koşullu Erişim

> [!NOTE]
> Güvenlik varsayılanlarını kullanıyorsanız Koşullu Erişim'i kullanmadan önce bunları kapatmanız gerekir. Güvenlik varsayılanlarını veya Koşullu Erişim ilkelerini kullanabilirsiniz, ancak ikisini de aynı anda kullanamazsınız.

Şirketinizin veya işletmenizin karmaşık güvenlik gereksinimleri varsa veya güvenlik ilkeleriniz üzerinde daha ayrıntılı denetime ihtiyacınız varsa, benzer veya daha yüksek bir güvenlik duruşu elde etmek için güvenlik varsayılanları yerine Koşullu Erişim'i kullanmayı düşünmelisiniz.

Koşullu Erişim, oturum açma olaylarına tepki veren ve kullanıcıya uygulama veya hizmete erişim verilmeden önce ek eylemler isteyen ilkeler oluşturmanıza ve tanımlamanıza olanak tanır. Koşullu Erişim ilkeleri ayrıntılı ve belirli olabilir, kullanıcıları her yerde ve her zaman üretken olmaya teşvik edebilir, aynı zamanda kuruluşunuzu koruyabilir.

Güvenlik varsayılanları tüm müşteriler tarafından kullanılabilirken Koşullu Erişim aşağıdaki planlardan birini gerektirir:

- Azure Active Directory Premium P1 veya P2
- Microsoft 365 Business Premium
- Microsoft 365 E3 veya E5
- Enterprise Mobility & Security E3 veya E5

İlkeleri yapılandırmak için Koşullu Erişim kullanmak istiyorsanız aşağıdaki adım adım kılavuzlara bakın:

- [Yöneticiler için MFA gerektir](/azure/active-directory/conditional-access/howto-conditional-access-policy-admin-mfa)
- [Azure yönetimi için MFA gerektirme](/azure/active-directory/conditional-access/howto-conditional-access-policy-azure-management)
- [Eski kimlik doğrulamasını engelle](/azure/active-directory/conditional-access/howto-conditional-access-policy-block-legacy)
- [Tüm kullanıcılar için MFA gerektir](/azure/active-directory/conditional-access/howto-conditional-access-policy-all-users-mfa)
- [Azure AD MFA kaydını gerektir](/azure/active-directory/identity-protection/howto-identity-protection-configure-mfa-policy) - Azure Active Directory Premium P2 parçası olan Azure AD Kimlik Koruması gerektirir

Koşullu Erişim hakkında daha fazla bilgi edinmek için bkz. [Koşullu Erişim nedir?](/azure/active-directory/conditional-access/overview) Koşullu Erişim ilkeleri oluşturma hakkında daha fazla bilgi için bkz. [Koşullu Erişim ilkesi oluşturma](/azure/active-directory/authentication/tutorial-enable-azure-mfa#create-a-conditional-access-policy).

> [!NOTE]
> Koşullu Erişim sağlayan bir planınız veya lisansınız varsa ancak henüz herhangi bir Koşullu Erişim ilkesi oluşturmadıysanız, güvenlik varsayılanlarını kullanabilirsiniz. Ancak, Koşullu Erişim ilkelerini kullanabilmeniz için önce güvenlik varsayılanlarını kapatmanız gerekir.

## <a name="next-objective"></a>Sonraki hedef

[Kötü amaçlı yazılımlara ve diğer tehditlere karşı korumanın](m365bp-increase-protection.md) yollarını ayarlayın.

