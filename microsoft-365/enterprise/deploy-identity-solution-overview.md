---
title: Daha fazla bilgi için kimlik altyapınızı Microsoft 365
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection:
- M365-identity-device-management
- Strat_O365_Enterprise
- m365initiative-coredeploy
- m365solution-m365-identity
- m365solution-scenario
- m365solution-overview
ms.custom:
- intro-overview
description: Daha fazla bilgi için kimlik altyapınızı Microsoft 365.
ms.openlocfilehash: 77dbb7c5c38e2ecd8d8ef5ae71044565c2ae6b20
ms.sourcegitcommit: 954c8af658adb270fe843991e048c6a30e86e77c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2022
ms.locfileid: "63016605"
---
# <a name="deploy-your-identity-infrastructure-for-microsoft-365"></a>Daha fazla bilgi için kimlik altyapınızı Microsoft 365

Kurumsal Microsoft 365'de, iyi planlanmış ve yürütülen bir kimlik altyapısı, üretkenlik iş yüklerinize ve bu iş yüklerine erişimi yalnızca kimliği doğrulanmış kullanıcılar ve cihazlara erişimi kısıtlama dahil olmak üzere daha güçlü bir güvenlik yolunun önünü kılar. Kimlikler için güvenlik Sıfır Güveni dağıtımının önemli bir öğesidir; bu dağıtımda hem şirket içinde hem de buluttaki kaynaklara erişme girişimleri kimlik doğrulaması ve yetkilendirilmiştir.

Kurumsal her bir Microsoft 365 kimlik özellikleri, Azure Active Directory (Azure AD), şirket içi ve bulut tabanlı bileşenlerin rolü ve en yaygın kimlik doğrulama yapılandırmaları hakkında bilgi için Kimlik Altyapısı [posteri'ne bakın](../downloads/m365e-identity-infra.pdf).

[![Kimlik Altyapısı posteri.](../downloads/m365e-identity-infra.png)](../downloads/m365e-identity-infra.pdf)

Kurumsal kimlik kavramları ve yapılandırmaları hızla takip etmek için bu iki sayfalık posteri Microsoft 365 gözden geçirin.

Bu [posteri indirebilir ve](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/m365e-identity-infra.pdf) mektup, yasal veya tabloid (11 x 17) biçiminde yazdırabilirsiniz.

Bu çözüm, sıfır güveni olan dağıtım yığınını Microsoft 365 adımdır.

![En Microsoft 365 Sıfır Güven dağıtım yığını](../media/deploy-identity-solution-overview/zero-trust-deployment-stack.png)

Daha fazla bilgi için Sıfır Güven [Microsoft 365 planına bakın](/microsoft-365/security/microsoft-365-zero-trust).

## <a name="whats-in-this-solution"></a>Bu çözümde neler var?

Bu çözüm, çalışanlarınıza erişim ve kimlik tabanlı saldırılara karşı koruma sağlamak Microsoft 365 kiracınız için bir kimlik altyapısının dağıtımında size yol sunar.

![Daha fazla bilgi için kimlik altyapınızı Microsoft 365](../media/deploy-identity-solution-overview/deploy-identity-solution-overview.png)

Bu çözümde adımlar şöyledir:

1. [Kimlik modelinizi belirleme.](deploy-identity-solution-identity-model.md)
2. [Ayrıcalıklı Microsoft 365 hesaplarınızı koruyun.](protect-your-global-administrator-accounts.md)
3. [Kullanıcı Microsoft 365 hesaplarınızı koruyun.](microsoft-365-secure-sign-in.md)
4. [Kimlik modelinizi dağıtın.](cloud-only-identities.md)

Bu çözüm Sıfır Güven'in temel [ilkelerini destekler](https://www.microsoft.com/security/business/zero-trust/):

- **Açık bir şekilde doğrulama:** Her zaman kullanılabilir tüm veri noktalarına göre kimlik doğrulama ve yetkilendirme.
- **En az ayrıcalık erişimini kullanın:** Kullanıcı erişimini Just-In-Time ve Just-Enough-Access (JIT/JEA), risk tabanlı uyarlanabilir ilkeler ve veri koruması ile sınırlandırın.
- **İhlal varsayalım:** Yarıçap yarıçapını ve segment erişimini en aza indirgeyin. Ender şifrelemeyi doğrulayın ve görünürlük elde etmek, tehdit algılamayı geliştirmek ve savunmayı geliştirmek için çözümlemeleri kullanın.

Kuruluşun güvenlik duvarının arkasında bulunan her şeye güvenen alışılmış intranet erişiminden farklı olarak, Sıfır Güven her oturum açma ve erişime, kuruluş güvenlik duvarının arkasında ya da İnternet'te bulunan denetimsiz bir ağdan geliyor gibi davranır. Sıfır Güven ağ, altyapı, kimlikler, uç noktalar, uygulamalar ve veriler için koruma gerektirir.

## <a name="microsoft-365-capabilities-and-features"></a>Microsoft 365 özellikleri ve özellikleri hakkında

Azure AD, kiracınız için tam kimlik yönetimi ve güvenlik Microsoft 365 sağlar.

|Özellik veya özellik|Açıklama|Lisanslama|
|---|---|---|
|[Çok faktörlü kimlik doğrulaması (MFA)](/azure/active-directory/authentication/concept-mfa-howitworks)|MFA, kullanıcıların iki tür doğrulama (kullanıcı parolası, ayrıca Microsoft Authenticator uygulamasından gelen bildirim veya telefon görüşmesi gibi) sağlamasını gerektirir. MFA, çalınmış kimlik bilgilerinin ortamınıza erişmek için kullanılma riskini büyük ölçüde azaltır. Microsoft 365, MFA tabanlı oturum açmalarda Azure AD Multi-Factor Authentication hizmetini kullanır.|Microsoft 365 E3 E5|
|[Koşullu Erişim](/azure/active-directory/conditional-access/overview)|Azure AD, kullanıcının oturum açma koşullarını değerlendirir ve izin verilen erişimi belirlemek için Koşullu Erişim ilkelerini kullanır. Örneğin, bu kılavuzda size hassas verilere erişim için cihaz uyumluluğu gerektirmeye yönelik bir Koşullu Erişim ilkesi oluşturma hakkında bilgi sağlarız. Bu, bilgisayar korsanı ve çalınmış kimlik bilgileriyle hassas verilerinize erişme riskini önemli ölçüde azaltır. Ayrıca cihazlar hassas verileri de korur, çünkü cihazlar sistem durumu ve güvenlik için belirli gereksinimleri karşılamalıdır.|Microsoft 365 E3 E5|
|[Azure AD grupları](/azure/active-directory/fundamentals/active-directory-manage-groups)|Koşullu Erişim ilkeleri, Intune ile cihaz yönetimi, hatta kuruluşta dosyaların ve sitelerin izinleri bile atamayı kullanıcı hesaplarına veya Azure AD gruplarına dayandırıyor. Uygulamakta olduğu koruma düzeylerine karşılık gelen Azure AD grupları oluşturmanızı öneririz. Örneğin, üst düzey personeliniz korsanlar için büyük olasılıkla daha yüksek değerli hedeflere sahip. Bu nedenle, bu çalışanların kullanıcı hesaplarını bir Azure AD grubuna eklemek ve bu grubu, erişim için daha yüksek bir koruma düzeyi uygulayan Koşullu Erişim ilkelerine ve diğer ilkelere atamak anlamlıdır.|Microsoft 365 E3 E5|
|[Azure AD Identity Protection](/azure/active-directory/identity-protection/overview)|Kuruluş kimliklerini etkileyen olası güvenlik açıklarını algılamanıza olanak sağlar ve otomatik düzeltme ilkesi düşük, orta ve yüksek oturum açma riski ile kullanıcı risklerini yapılandırabilir. Bu kılavuz, çok faktörlü kimlik doğrulamasına Koşullu Erişim ilkeleri uygulamak için bu risk değerlendirmesini temel almaktadır. Bu kılavuzda ayrıca, kullanıcıların hesapları için yüksek riskli etkinlik algılandığında parolalarını değiştirmelerini gerektiren bir Koşullu Erişim ilkesi de yerlanır.|Microsoft 365 E5, Microsoft 365 E3 E5 Güvenlik eklenti, EMS E5 veya diğer kullanıcı Azure AD Premium P2 seçin|
|[Kendi kendine parola sıfırlama (SSPR)](/azure/active-directory/authentication/concept-sspr-howitworks)|Yöneticinin denetiminde olduğu birden çok kimlik doğrulama yönteminin doğrulamasını sağlayarak, kullanıcılarınızı parolalarını güvenli bir şekilde ve yardım masası müdahalesi olmadan sıfırlamasına izin verme.|Microsoft 365 E3 E5|
|[Azure AD parola koruması](/azure/active-directory/authentication/concept-password-ban-bad)|Bilinen zayıf parolaları, değişkenlerini ve zayıf olan organizasyona özgü ek zayıf terimlerini algıla ve engelle. Varsayılan genel yasaklanmış parola listeleri, Bir Azure AD kiracısı'nın tüm kullanıcılarına otomatik olarak uygulanır. Özel bir yasaklanan parola listesinde ek girişler tanımlayabilirsiniz. Kullanıcılar parolalarını değiştirse veya sıfırlasa, güçlü parolaların kullanımını zorunlu yapmak için bu yasaklanmış parola listeleri denetlenir.|Microsoft 365 E3 E5|
|

## <a name="next-steps"></a>Sonraki adımlar

Kiracınız için kimlik modeli ve kimlik doğrulama altyapısını dağıtmak Microsoft 365 kullanın:

1. [Bulut kimlik modelinizi belirleme.](deploy-identity-solution-identity-model.md)
2. [Ayrıcalıklı Microsoft 365 hesaplarınızı koruyun.](protect-your-global-administrator-accounts.md)
3. [Kullanıcı Microsoft 365 hesaplarınızı koruyun.](microsoft-365-secure-sign-in.md)
4. Bulut kimliği modelinizi dağıtma: [Yalnızca bulut veya](cloud-only-identities.md) [karma](prepare-for-directory-synchronization.md).

[![Kiracınız için hangi kimlik modelini Microsoft 365 belirleme](../media/deploy-identity-solution-overview/identity-solution-identity-model.png)](deploy-identity-solution-identity-model.md)
  
## <a name="additional-microsoft-cloud-identity-resources"></a>Ek Microsoft bulut kimlik kaynakları

### <a name="manage"></a>Yönetme

Microsoft bulut kimliği dağıtımınızı yönetmek için bkz:

- [Kullanıcı hesapları](manage-microsoft-365-accounts.md)
- [Lisanslar](assign-licenses-to-user-accounts.md)
- [Parolalar](manage-microsoft-365-passwords.md)
- [Gruplar](manage-microsoft-365-groups.md)
- [İdare](manage-microsoft-365-identity-governance.md)
- [Dizin eşitlemesi](view-directory-synchronization-status.md)

### <a name="how-microsoft-does-identity-for-microsoft-365"></a>Microsoft'un kimlik Microsoft 365

Microsoft'un KIMLIKleri nasıl [yöneteceklerini ve güvenli erişimi nasıl yöneteceklerini öğrenin](https://www.microsoft.com/en-us/itshowcase/managing-user-identities-and-secure-access-at-microsoft).

>[!Note]
>Bu IT Vitrini kaynağı yalnızca İngilizce olarak kullanılabilir.
>

### <a name="how-contoso-did-identity-for-microsoft-365"></a>Contoso'nın kimliklerini nasıl Microsoft 365

Kurgusal ama çok uluslu bir kuruluşun bulut hizmetleri için karma bir kimlik altyapısı dağıtımına Microsoft 365, [bkz. Contoso Corporation için Identity](contoso-identity.md).

<!--

## Plan

To plan for your identity implementation:

- [Understand the different identity models](about-microsoft-365-identity.md)
- [Plan for hybrid identity and directory synchronization](plan-for-directory-synchronization.md)

## Deploy

To deploy your identity implementation:

- [Protect your global administrator accounts](protect-your-global-administrator-accounts.md)
- [Configure and use cloud-only identities](cloud-only-identities.md)
- [Configure and use hybrid identities](prepare-for-directory-synchronization.md)
- [Set up directory synchronization](set-up-directory-synchronization.md)
- If needed, deploy [hybrid identity scenarios](hybrid-solutions.md)

### Identity and device access recommendations

To help ensure a secure and productive workforce, Microsoft provides a set of recommendations for [identity and device access](../security/office-365-security/microsoft-365-policies-configurations.md). For identity, use the recommendations and settings in these articles:

- [Prerequisites](../security/office-365-security/identity-access-prerequisites.md)
- [Common identity and device access policies](../security/office-365-security/identity-access-policies.md)

--> 
