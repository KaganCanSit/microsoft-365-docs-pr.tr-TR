---
title: Adım 3. Kimlikleri koruma
author: JoeDavies-MSFT
f1.keywords:
- NOCSH
ms.author: josephd
manager: dansimp
audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- Strat_O365_Enterprise
- ransomware
- m365solution-ransomware
ms.custom: seo-marvel-jun2020
keywords: fidye yazılımı, insan tarafından işletilen fidye yazılımı, insan tarafından işletilen fidye yazılımı, HumOR, extortion saldırısı, fidye yazılımı saldırı, şifreleme, cryptovirology, sıfır güven
description: Kullanıcı kaynaklarınızı fidye yazılımı saldırılarından korumak için güvenli oturum açma Microsoft 365 Koşullu Erişim'i kullanın.
ms.openlocfilehash: 57fad156a4e7b97d3029c224059041d692224ed2
ms.sourcegitcommit: 23a90ed17cddf3b0db8d4084c8424f0fabd7b1de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/17/2022
ms.locfileid: "63015444"
---
# <a name="step-3-protect-identities"></a>Adım 3. Kimlikleri koruma

Genelde daha büyük bir fidye yazılımı saldırılarının ilk aşaması olan kimlik bilgileri güvenliğinden korumak için aşağıdaki bölümleri kullanın.

## <a name="increase-sign-in-security"></a>Oturum açma güvenliğini artırma

[Azure Active Directory'da](/azure/active-directory/authentication/howto-authentication-passwordless-deployment) (Azure AD) kullanıcı hesapları için Azure Active Directory kimlik doğrulaması kullanın.

Parolasız kimlik doğrulamaya geçiş sırasında, parola kimlik doğrulaması kullanan kullanıcı hesapları için şu en iyi yöntemleri kullanın:

- Azure AD Parola Koruması ile zayıf ve özel olarak [bilinen parolaları engelin](/azure/active-directory/authentication/concept-password-ban-bad).
- Azure AD Parola Koruması ile şirket içi Active Directory Etki Alanı Hizmetlerinize [(AD DS) bilinen zayıf ve özel parolaların engellenmesini uzatın](/azure/active-directory/authentication/concept-password-ban-bad-on-premises).
- Kendi Kendine Parola Sıfırlama [(SSPR)](/azure/active-directory/authentication/concept-sspr-howitworks) ile kullanıcılarınızı kendi parolalarını değiştirmelerine izin verme.

Ardından, Ortak kimlik [ve cihaz erişimi ilkelerini kullanın](/microsoft-365/security/office-365-security/identity-access-policies). Bu ilkeler, bulut hizmetleriyle ilgili hizmetlere Microsoft 365 daha yüksek güvenlik sağlar. 

Kullanıcı oturum açma bilgileri için bu ilkeler şunlardır:

- Öncelik hesapları (hemen) için [çok faktörlü](/microsoft-365/admin/setup/priority-accounts) kimlik doğrulaması (MFA) gerekir ve sonunda tüm kullanıcı hesapları kullanılır.
- MFA kullanmak için yüksek riskli oturum açma işlemleri gerektiren.
- Parolalarını değiştirmek için yüksek riskli oturum açmaları olan kullanıcıları gerektirme.

## <a name="prevent-privilege-escalation"></a>Ayrıcalık yükseltmeyi önleme

Şu en iyi yöntemleri kullanın:

- En az ayrıcalık [ilkesi uygulama](/windows-server/identity/ad-ds/plan/security-best-practices/implementing-least-privilege-administrative-models) ve oturum açma parolalarını kullanmaya devam eden [](#increase-sign-in-security) bu kullanıcı hesapları için oturum açma güvenliğini artırma konusunda açıklandığı gibi parola koruması kullanma. 
- Etki alanı genelinde yönetici düzeyinde hizmet hesaplarının kullanımından kaçının. 
- Uzak Erişim Truvaları (RAT) ve diğer istenmeyen uygulamaların yüklemesini sınırlamak için yerel yönetim ayrıcalıklarını kısıtla.
- Yönetim portallarına erişime izin vermeden önce, kullanıcıların ve iş istasyonlarının güvenlerini açıkça doğrulamak için Azure AD Koşullu Erişim'i kullanın. Azure [portalı için](/azure/active-directory/conditional-access/howto-conditional-access-policy-azure-management) bu örneğine bakın.
- Yerel Yönetici parola yönetimini etkinleştirin.
- Üst düzeyde ayrıcalıklı hesapların oturum açma ve kimlik bilgilerini ortaya çıkarma yerini belirleme. Yüksek derecede ayrıcalıklı hesaplar iş istasyonlarında mevcut olmayacaktır.
- Parolaların ve kimlik bilgilerinin yerel depolamasını devre dışı bırak.

## <a name="impact-on-users-and-change-management"></a>Kullanıcılar üzerindeki etkisi ve değişiklik yönetimi

Organizasyon'daki kullanıcıları şulardan haberdar etmek gerekir:

- Daha güçlü parolalar için yeni gereksinimler.
- MFA'nın gerekli kullanımı ve MFA ikincil kimlik doğrulama yöntemi kaydı gibi oturum açma süreçlerde yapılan değişiklikler.
- SSPR ile parola bakımı kullanımı. Örneğin, parola sıfırlama için yardım masasına artık çağrı yok.
- Risk altında olduğu belirlenen oturum açmalarda MFA'nın veya parola değişikliğinin gerekli olması isteniyor.

## <a name="resulting-configuration"></a>Sonuçta elde edilen yapılandırma

İşte, 1.ve 3. adımlar için kiracınız için fidye yazılımı koruması.

![3. Adım'dan Microsoft 365 kiracınız için fidye yazılımı koruması](../media/ransomware-protection-microsoft-365/ransomware-protection-microsoft-365-architecture-step3.png)

## <a name="next-step"></a>Sonraki adım

[![Yazılımla fidye yazılımı koruması için 4. Microsoft 365](../media/ransomware-protection-microsoft-365/ransomware-protection-microsoft-365-step4.png)](ransomware-protection-microsoft-365-devices.md)

Kiracınıza [cihazları (uç](ransomware-protection-microsoft-365-devices.md) noktalar) korumak için 4. Adım Microsoft 365 devam edin. 
