---
title: kimlik altyapınızı Microsoft 365 için dağıtma
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: kimlik altyapınızı Microsoft 365 için dağıtın.
ms.openlocfilehash: 6128daa59bfece9403953e041f258d87ef6a7413
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65092965"
---
# <a name="deploy-your-identity-infrastructure-for-microsoft-365"></a>kimlik altyapınızı Microsoft 365 için dağıtma

Microsoft 365 kurumsal olarak iyi planlanmış ve yürütülen bir kimlik altyapısı, üretkenlik iş yüklerinize ve verilerine erişimi yalnızca kimliği doğrulanmış kullanıcılar ve cihazlarla kısıtlama da dahil olmak üzere daha güçlü bir güvenliğin önünü açar. Kimlikler için güvenlik, hem şirket içindeki hem de buluttaki kaynaklara erişmeye yönelik tüm girişimlerin kimliğinin doğrulandığı ve yetkilendirildiği Sıfır Güven dağıtımının önemli bir öğesidir.

Kuruluş için her Microsoft 365 kimlik özellikleri, Azure Active Directory (Azure AD), şirket içi ve bulut tabanlı bileşenlerin rolü ve en yaygın kimlik doğrulama yapılandırmaları hakkında bilgi için [Kimlik Altyapısı posteri'ne](../downloads/m365e-identity-infra.pdf) bakın.

[![Kimlik Altyapısı posteri.](../downloads/m365e-identity-infra.png)](../downloads/m365e-identity-infra.pdf)

Kuruluş için Microsoft 365 kimlik kavramlarını ve yapılandırmalarını hızla geliştirme amacıyla bu iki sayfalık posteri gözden geçirin.

[Bu posteri indirebilir](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/m365e-identity-infra.pdf) ve mektup, yasal veya tabloid (11 x 17) biçiminde yazdırabilirsiniz.

Bu çözüm, Microsoft 365 Sıfır Güven dağıtım yığınını oluşturmanın ilk adımıdır.

![Microsoft 365 Sıfır Güven dağıtım yığını](../media/deploy-identity-solution-overview/zero-trust-deployment-stack.png)

Daha fazla bilgi için [bkz. Microsoft 365 Sıfır Güven dağıtım planı](/microsoft-365/security/microsoft-365-zero-trust).

## <a name="whats-in-this-solution"></a>Bu çözümde neler var?

Bu çözüm, çalışanlarınıza erişim ve kimlik tabanlı saldırılara karşı koruma sağlamak üzere Microsoft 365 kiracınız için bir kimlik altyapısı dağıtımında size yol gösterir.

![kimlik altyapınızı Microsoft 365 için dağıtma](../media/deploy-identity-solution-overview/deploy-identity-solution-overview.png)

Bu çözümdeki adımlar şunlardır:

1. [Kimlik modelinizi belirleyin.](deploy-identity-solution-identity-model.md)
2. [Microsoft 365 ayrıcalıklı hesaplarınızı koruyun.](protect-your-global-administrator-accounts.md)
3. [Microsoft 365 kullanıcı hesaplarınızı koruyun.](microsoft-365-secure-sign-in.md)
4. [Kimlik modelinizi dağıtın.](cloud-only-identities.md)

Bu çözüm[, Sıfır Güven](https://www.microsoft.com/security/business/zero-trust/) temel ilkelerini destekler:

- **Açıkça doğrula:** Kullanılabilir tüm veri noktalarına göre her zaman kimlik doğrulaması ve yetkilendirme.
- **En az ayrıcalık erişimi kullanın:** Tam Zamanında ve Yeterli Erişim (JIT/JEA), risk tabanlı uyarlamalı ilkeler ve veri koruması ile kullanıcı erişimini sınırlayın.
- **İhlal olduğunu varsay:** Patlama yarıçapı ve segment erişimini en aza indirin. Uçtan uca şifrelemeyi doğrulayın ve görünürlük elde etmek, tehdit algılamayı yönlendirmek ve savunmaları geliştirmek için analizi kullanın.

Bir kuruluşun güvenlik duvarının arkasındaki her şeye güvenen geleneksel intranet erişiminin aksine, Sıfır Güven her oturum açma ve erişimi kuruluş güvenlik duvarının arkasında veya İnternet'te olduğu gibi denetimsiz bir ağdan geliyormuş gibi davranır. Sıfır Güven ağ, altyapı, kimlikler, uç noktalar, uygulamalar ve veriler için koruma gerektirir.

## <a name="microsoft-365-capabilities-and-features"></a>Microsoft 365 özellikleri ve özellikleri

Azure AD, Microsoft 365 kiracınız için eksiksiz bir kimlik yönetimi ve güvenlik özellikleri paketi sağlar.

|Yetenek veya özellik|Açıklama|Lisanslama|
|---|---|---|
|[Çok faktörlü kimlik doğrulaması (MFA)](/azure/active-directory/authentication/concept-mfa-howitworks)|MFA, kullanıcıların kullanıcı parolası ve Microsoft Authenticator uygulamasından gelen bildirim veya telefon görüşmesi gibi iki doğrulama biçimi sağlamasını gerektirir. MFA, çalınan kimlik bilgilerinin ortamınıza erişmek için kullanılabilmesi riskini büyük ölçüde azaltır. Microsoft 365, MFA tabanlı oturum açma işlemleri için Azure AD Multi-Factor Authentication hizmetini kullanır.|Microsoft 365 E3 veya E5|
|[Koşullu Erişim](/azure/active-directory/conditional-access/overview)|Azure AD, kullanıcı oturum açma koşullarını değerlendirir ve izin verilen erişimi belirlemek için Koşullu Erişim ilkelerini kullanır. Örneğin, bu kılavuzda hassas verilere erişim için cihaz uyumluluğu gerektiren bir Koşullu Erişim ilkesinin nasıl oluşturulacağını gösteririz. Bu, kendi cihazına ve çalınan kimlik bilgilerine sahip bir korsanın hassas verilerinize erişme riskini büyük ölçüde azaltır. Ayrıca cihazlardaki hassas verileri de korur çünkü cihazların sistem durumu ve güvenliği için belirli gereksinimleri karşılaması gerekir.|Microsoft 365 E3 veya E5|
|[Azure AD grupları](/azure/active-directory/fundamentals/active-directory-manage-groups)|Koşullu Erişim ilkeleri, Intune ile cihaz yönetimi ve hatta kuruluşunuzdaki dosya ve sitelere yönelik izinler, kullanıcı hesaplarına veya Azure AD gruplarına atamayı kullanır. Uyguladığınız koruma düzeylerine karşılık gelen Azure AD grupları oluşturmanızı öneririz. Örneğin, yönetici personeliniz korsanlar için büyük olasılıkla daha yüksek değer hedefleridir. Bu nedenle, bu çalışanların kullanıcı hesaplarını bir Azure AD grubuna eklemek ve bu grubu Koşullu Erişim ilkelerine ve erişim için daha yüksek bir koruma düzeyini zorlayan diğer ilkelere atamak mantıklıdır.|Microsoft 365 E3 veya E5|
|[Azure AD Kimlik Koruması](/azure/active-directory/identity-protection/overview)|Kuruluşunuzun kimliklerini etkileyen olası güvenlik açıklarını algılamanıza ve otomatik düzeltme ilkesini düşük, orta ve yüksek oturum açma riski ile kullanıcı riski olarak yapılandırmanıza olanak tanır. Bu kılavuz, çok faktörlü kimlik doğrulaması için Koşullu Erişim ilkelerini uygulamak için bu risk değerlendirmesine dayanır. Bu kılavuz, hesaplarında yüksek riskli etkinlik algılandığında kullanıcıların parolalarını değiştirmelerini gerektiren bir Koşullu Erişim ilkesi de içerir.|Microsoft 365 E5, E5 Güvenlik eklentisi, EMS E5 veya Azure AD Premium P2 lisanslarıyla Microsoft 365 E3|
|[Kendi kendine parola sıfırlama (SSPR)](/azure/active-directory/authentication/concept-sspr-howitworks)|Yöneticinin denetleyebileceği birden çok kimlik doğrulama yönteminin doğrulanmasını sağlayarak kullanıcılarınızın parolalarını güvenli bir şekilde ve yardım masası müdahalesi olmadan sıfırlamasına izin verin.|Microsoft 365 E3 veya E5|
|[Azure AD parola koruması](/azure/active-directory/authentication/concept-password-ban-bad)|Bilinen zayıf parolaları ve bunların değişkenlerini ve kuruluşunuza özgü ek zayıf terimleri algılayın ve engelleyin. Varsayılan genel yasaklanmış parola listeleri, Bir Azure AD kiracısında tüm kullanıcılara otomatik olarak uygulanır. Özel yasaklanmış parola listesinde ek girdiler tanımlayabilirsiniz. Kullanıcılar parolalarını değiştirdiğinde veya sıfırladığında, bu yasaklanmış parola listeleri güçlü parolaların kullanımını zorunlu kılmak için denetlenir.|Microsoft 365 E3 veya E5|
|

## <a name="next-steps"></a>Sonraki adımlar

Microsoft 365 kiracınız için kimlik modeli ve kimlik doğrulama altyapısı dağıtmak için şu adımları kullanın:

1. [Bulut kimliği modelinizi belirleyin.](deploy-identity-solution-identity-model.md)
2. [Microsoft 365 ayrıcalıklı hesaplarınızı koruyun.](protect-your-global-administrator-accounts.md)
3. [Microsoft 365 kullanıcı hesaplarınızı koruyun.](microsoft-365-secure-sign-in.md)
4. Bulut kimlik modelinizi dağıtın: [yalnızca bulut](cloud-only-identities.md) veya [karma](prepare-for-directory-synchronization.md).

[![Microsoft 365 kiracınız için kullanılacak kimlik modelini belirleme](../media/deploy-identity-solution-overview/identity-solution-identity-model.png)](deploy-identity-solution-identity-model.md)
  
## <a name="additional-microsoft-cloud-identity-resources"></a>Ek Microsoft bulut kimliği kaynakları

### <a name="manage"></a>Yönetme

Microsoft bulut kimliği dağıtımınızı yönetmek için bkz:

- [Kullanıcı hesapları](manage-microsoft-365-accounts.md)
- [Lisanslar](assign-licenses-to-user-accounts.md)
- [Parolalar](manage-microsoft-365-passwords.md)
- [Gruplar](manage-microsoft-365-groups.md)
- [İdare](manage-microsoft-365-identity-governance.md)
- [Dizin eşitleme](view-directory-synchronization-status.md)

### <a name="how-microsoft-does-identity-for-microsoft-365"></a>Microsoft Microsoft 365 için kimlik oluşturma

Microsoft'taki BT uzmanlarının [kimlikleri ve güvenli erişimi nasıl yönettiğini](https://www.microsoft.com/en-us/itshowcase/managing-user-identities-and-secure-access-at-microsoft) öğrenin.

>[!Note]
>Bu BT Vitrini kaynağı yalnızca İngilizce olarak kullanılabilir.
>

### <a name="how-contoso-did-identity-for-microsoft-365"></a>Contoso Microsoft 365 için nasıl kimlik yaptı?

Kurgusal ama temsili çok uluslu bir kuruluşun Microsoft 365 bulut hizmetleri için hibrit kimlik altyapısını nasıl dağıttığını gösteren bir örnek için bkz. [Contoso Corporation için kimlik](contoso-identity.md).

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
