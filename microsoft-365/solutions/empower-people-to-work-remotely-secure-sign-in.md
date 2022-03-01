---
title: Adım 1. MFA ile karma çalışanların oturum açma güvenliğini artırma
f1.keywords:
- NOCSH
author: JoeDavies-MSFT
ms.author: josephd
manager: dansimp
audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- Strat_O365_Enterprise
- remotework
- m365solution-remotework
- m365solution-scenario
ms.custom: ''
description: Karma çalışanlarının çok faktörlü kimlik doğrulamasıyla (MFA) oturum açmasını gerekli olarak kullanın.
ms.openlocfilehash: c5c63716ecbd29ba393ee7601e99a1f52b4c3768
ms.sourcegitcommit: 6c57f1e90339d5a95c9e7875599dac9d3e032c3a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/04/2022
ms.locfileid: "63014402"
---
# <a name="step-1-increase-sign-in-security-for-hybrid-workers-with-mfa"></a>Adım 1. MFA ile karma çalışanların oturum açma güvenliğini artırma

Karma çalışanlarının oturum açma güvenliğini artırmak için, Multi-Factor Authentication(MFA) kullanın. MFA, kullanıcı oturum açma hesaplarının kullanıcı hesabı parolasının ötesinde başka bir doğrulamaya tabi olması gerekir. Kötü niyetli bir kullanıcı bir kullanıcı hesabı parolası belirlerse bile, erişim izni verilmeden önce akıllı telefona gönderilen SMS gibi ek bir doğrulamayı yanıtlayabiliyor olması gerekir.

![Doğru parolanın yanı sıra ek doğrulama da başarılı bir oturum açma işlemiyle sonuç verir.](../media/empower-people-to-work-remotely/remote-workers-mfa.png)

Karma çalışanlar ve özellikle de yöneticiler dahil olmak üzere tüm kullanıcılar için Microsoft kesinlikle MFA'nın önerilerini sağlar.

Kullanıcılarının kendi planlarınızı temel alarak MFA kullanmalarını gerektiren üç Microsoft 365 vardır.

|Plan  |Öneri  |
|---------|---------|
|Tüm Microsoft 365 planları (Azure AD Premium P1 P2 lisansı olmadan)     |[Azure AD'de güvenlik varsayılanlarını etkinleştirin](/azure/active-directory/fundamentals/concept-fundamentals-security-defaults). Azure AD'de güvenlik varsayılanları, kullanıcılar ve yöneticiler için MFA içerir.   |
|Microsoft 365 E3 (Azure AD Premium P1 içerir)     | Aşağıdaki [ilkeleri yapılandırmak için Ortak](/azure/active-directory/conditional-access/concept-conditional-access-policy-common) Koşullu Erişim ilkelerini kullanın: <br>- [Yöneticiler için MFA gerektirme](/azure/active-directory/conditional-access/howto-conditional-access-policy-admin-mfa) <br>- [Tüm kullanıcılar için MFA gerektirme](/azure/active-directory/conditional-access/howto-conditional-access-policy-all-users-mfa) <br> - [Eski kimlik doğrulamayı engelle](/azure/active-directory/conditional-access/howto-conditional-access-policy-block-legacy)       |
|Microsoft 365 E5 (Azure AD Premium P2 içerir)     | Azure AD Kimlik Koruması'ndan yararlanmak için, bu ilkeleri oluşturarak Microsoft'un önerilen Koşullu [Erişim ve ilgili](../security/office-365-security/identity-access-policies.md) ilkeler setlerini uygulamaya başlayabilirsiniz:<br> - [Oturum açma riski orta veya yüksek olduğunda MFA gerektirme](../security/office-365-security/identity-access-policies.md#require-mfa-based-on-sign-in-risk) <br>- [Modern kimlik doğrulamasını desteklemez istemcileri engelleme](../security/office-365-security/identity-access-policies.md#block-clients-that-dont-support-multi-factor)<br>- [Yüksek riskli kullanıcıların parolayı değiştirmesi gerekir](../security/office-365-security/identity-access-policies.md#high-risk-users-must-change-password)       |
| | |

## <a name="security-defaults"></a>Güvenlik varsayılanları

Güvenlik varsayılanları, 21 Ekim 2019'dan Microsoft 365 sonra Office 365 veya deneme abonelikleri için yeni bir özelliktir. Bu aboneliklerin güvenlik varsayılanları açıktır ve bu da kullanıcılarının tüm kullanıcılarının ***Microsoft Authenticator gerektirir***.
 
Kullanıcıların, güvenlik varsayılanları etkinleştirildikten sonra ilk kez oturum açmalarından başlanacak olan Microsoft Authenticator uygulamasıyla MFA'ya kaydolmaları için 14 günü vardır. 14 gün sonra, MFA kaydı tamamlanana kadar kullanıcı oturum açmaz.

Güvenlik varsayılanları, tüm kuruluşların, kullanıcı oturum açma için varsayılan olarak etkinleştiren temel güvenlik düzeyine sahip olmasını sağlar. Koşullu Erişim ilkeleri veya tek tek hesaplar için MFA'nın tercihi olarak güvenlik varsayılanlarını devre dışı abilirsiniz.

Daha fazla bilgi için bu güvenlik [varsayılanlarına genel bakış bilgilerine bakın](/azure/active-directory/fundamentals/concept-fundamentals-security-defaults).

## <a name="conditional-access-policies"></a>Koşullu Erişim ilkeleri

Koşullu Erişim ilkeleri, oturum açmaların değerlendirilmesini ve izin verilen koşulları belirten bir dizi kuraldır. Örneğin, şöyle bir Koşullu Erişim ilkesi oluşturabilirsiniz:

- Kullanıcı hesabı adı Exchange, kullanıcı, parola, güvenlik, SharePoint veya genel yönetici rollerine atanan kullanıcılar için bir grubun üyesiyse, erişime izin vermeden önce MFA'ya gerek vardır.

Bu ilke, bu yönetici rollerine atanan veya atanmamış durumdayken MFA için tek tek kullanıcı hesaplarını yapılandırmaya çalışma yerine, grup üyeliğini temel alarak MFA gerektirmenizi sağlar.

Koşullu Windows Erişim ilkelerini, oturum açmanın 11 veya 10 veya 10 çalıştıran dizüstü bilgisayarınız gibi uyumlu bir cihazdan yapılması gerektirme gibi daha gelişmiş özellikler için de kullanabilirsiniz.

Koşullu Erişim için Azure AD Premium P1 ve E5 ile birlikte Microsoft 365 E3 lisansları gerekir.

Daha fazla bilgi için Koşullu [Erişim'e genel bakış bilgilerine bakın](/azure/active-directory/conditional-access/overview).

## <a name="azure-ad-identity-protection-support"></a>Azure AD Identity Protection desteği

Azure AD Kimlik Koruması ile, aşağıdakilerle ilgili ek bir Koşullu Erişim ilkesi oluşturabilirsiniz:

- Oturum açma riski orta veya yüksek olarak belirleniyorsa, MFA gerektirir.

Azure AD Kimlik Koruması için Azure AD Premium P2 lisansları gerekir ve bu lisanslar Microsoft 365 E5.

Daha fazla bilgi için bkz [. Risk Tabanlı Koşullu Erişim](/azure/active-directory/conditional-access/howto-conditional-access-policy-risk#require-mfa-medium-or-high-sign-in-risk-users).

Azure AD Identity Protection ile, kullanıcılarının MFA'ya kaydolmasını gerektiren bir ilke de oluşturabilirsiniz. Daha fazla bilgi için bkz [. Azure AD Multi-Factor Authentication kayıt ilkesi yapılandırma](/azure/active-directory/identity-protection/howto-identity-protection-configure-mfa-policy)


## <a name="using-these-methods-together"></a>Bu yöntemleri birlikte kullanma

Şunları unutmayın:

- Hiçbir Koşullu Erişim ilkeniz etkinleştirilmişse, güvenlik varsayılanlarını etkinleştiresiniz.
- Güvenlik varsayılanlarını etkinleştirdiyseniz hiçbir Koşullu Erişim ilkelerini etkinleştiresiniz.

Güvenlik varsayılanları etkinse, tüm yeni kullanıcılardan MFA kaydı ve Microsoft Authenticator istenir. 

Bu tabloda, güvenlik varsayılanları ve Koşullu Erişim ilkeleriyle MFA'nın etkinleştirilmesi sonuçları gösterir.

| Yöntem | Etkin | Devre dışı | Ek kimlik doğrulama yöntemi |
|:-------|:-----|:-------|:-------|
| **Güvenlik varsayılanları**  | Koşullu Erişim ilkeleri kullanama | Koşullu Erişim ilkelerini kullanabilir | Microsoft Authenticator uygulaması |
| **Koşullu Erişim ilkeleri** | Etkinse, güvenlik varsayılanlarını etkinleştiresiniz | Tüm devre dışı bırakılmışsa güvenlik varsayılanlarını etkinleştir  | Kullanıcı MFA kaydı sırasında belirtir  |
||||

## <a name="let-your-users-reset-their-own-passwords"></a>Kullanıcılarının kendi parolalarını sıfırlamasına izin verme

Self-Service Sıfırlama (SSPR) özelliği, kullanıcıların IT personelini etkilemeden kendi parolalarını sıfırlamalarına olanak sağlar. Kullanıcılar, parolalarını herhangi bir zamanda ve herhangi bir yerde hızlı bir şekilde sıfırlar. Daha fazla bilgi için bkz [. Azure AD kendi kendine parola sıfırlama dağıtımını planlama](/azure/active-directory/authentication/howto-sspr-deployment).

## <a name="sign-in-to-saas-apps-with-azure-ad"></a>Azure AD ile SaaS uygulamalarına oturum açma

Kullanıcılara bulut kimlik doğrulaması sağlamanın yanı sıra, ister şirket içi olsun, Microsoft bulutlarında veya başka bir bulutta tüm uygulamalarınızı güvenlik altına almak için Azure AD merkezi bir yol da olabilir. [Uygulamalarınızı Azure AD ile](/azure/active-directory/manage-apps/plan-an-application-integration) tümleştirerek, karma çalışanların ihtiyaçları olan uygulamaları bulmalarını ve güvenli bir şekilde oturum açmalarını kolaylaştırabilirsiniz.

## <a name="admin-technical-resources-for-mfa-and-identity"></a>MFA ve kimlik için yönetici teknik kaynakları

- [Azure AD'nizin uzaktan çalışmaları etkinleştirmenize yardımcı olduğu en önemli 5 yol](https://techcommunity.microsoft.com/t5/azure-active-directory-identity/top-5-ways-your-azure-ad-can-help-you-enable-remote-work/ba-p/1144691)
- [Kimlikler için kimlik Microsoft 365](../enterprise/deploy-identity-solution-overview.md)
- [Azure Academy Azure AD eğitim videoları](https://www.youtube.com/watch?v=pN8o0owHfI0&list=PL-V4YVm6AmwUFpC3rXr2i2piRQ708q_ia)

## <a name="results-of-step-1"></a>Adım 1'in sonuçları

MFA'nın dağıtımı sonrasında kullanıcılarınız:

- Oturum açmalarda MFA'nın kullanımı gereklidir.
- MFA kayıt işlemini tamamladınız ve tüm oturum açma işlemleri için MFA kullanıyorsanız.
- SSPR kullanarak kendi parolalarını sıfırlayabilirsiniz.

## <a name="next-step"></a>Sonraki adım

[![2. Adım: Şirket içi uygulamalara ve hizmetlere uzaktan erişim sağlama.](../media/empower-people-to-work-remotely/remote-workers-step-grid-2.png)](empower-people-to-work-remotely-remote-access.md)

Şirket içi [uygulama ve hizmetlere](empower-people-to-work-remotely-remote-access.md) uzaktan erişim sağlamak için 2. Adımdan devam edin.