---
title: Microsoft 365 için çok faktörlü kimlik doğrulaması
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
- okr_smb
- AdminTemplateSet
- admindeeplinkMAC
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 043807b2-21db-4d5c-b430-c8a6dee0e6ba
ROBOTS: NOINDEX, NOFOLLOW
description: Çok faktörlü kimlik doğrulaması (MFA) hem güçlü olması gereken bir parola hem de ek bir doğrulama yöntemi kullanır.
ms.openlocfilehash: f939b187fc81381dae4959fdf14280bc839dadb0
ms.sourcegitcommit: a8fbaf4b441b5325004f7a2dacd9429ec9d80534
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/26/2022
ms.locfileid: "65739881"
---
# <a name="multifactor-authentication-for-microsoft-365"></a>Microsoft 365 için çok faktörlü kimlik doğrulaması

Parolalar, bir bilgisayarda veya çevrimiçi hizmette oturum açma kimliğini doğrulamanın en yaygın yöntemidir, ancak aynı zamanda en savunmasız olanlardır. Kişiler kolay parolalar seçebilir ve farklı bilgisayarlara ve hizmetlere birden çok oturum açma için aynı parolaları kullanabilir.

Oturum açma işlemleri için ek bir güvenlik düzeyi sağlamak için, hem güçlü olması gereken parolayı hem de aşağıdakileri temel alan ek bir doğrulama yöntemini kullanan çok faktörlü kimlik doğrulamasını (MFA) kullanmanız gerekir:

- Akıllı telefon gibi kolayca çoğaltılması kolay olmayan bir şey.
- Parmak izleriniz, yüzünüz veya diğer biyometrik öznitelikleriniz gibi benzersiz ve biyolojik olarak sahip olduğunuz bir şey.

Ek doğrulama yöntemi, kullanıcının parolası doğrulanana kadar kullanılmaz. MFA ile güçlü bir kullanıcı parolası tehlikeye girse bile, saldırganın oturum açma işlemini tamamlamak için akıllı telefonunuz veya parmak iziniz yoktur.

## <a name="mfa-support-in-microsoft-365"></a>Microsoft 365'de MFA desteği

Varsayılan olarak, hem Microsoft 365 hem de Office 365 aşağıdakileri kullanan kullanıcı hesapları için MFA'yı destekler:

- Kullanıcının doğrulama kodu yazmasını gerektiren bir telefona gönderilen kısa mesaj.
- Bir telefon görüşmesi.
- Microsoft Authenticator akıllı telefon uygulaması.

Her iki durumda da MFA oturum açma işlemi ek doğrulama için "sizinle birlikte kolayca çoğaltılamaz bir şey" yöntemini kullanır. Microsoft 365 ve Office 365 için MFA'yı etkinleştirmenin birden çok yolu vardır:

- Güvenlik varsayılanlarıyla
- Koşullu Erişim ilkeleriyle
- Her kullanıcı hesabı için (önerilmez)

Bu yollar Microsoft 365 planınıza bağlıdır.

|Plan|Öneri|Müşteri türü|
|---|---|---|
|Tüm Microsoft 365 planları|Tüm kullanıcı hesapları için MFA gerektiren güvenlik varsayılanlarını kullanın. <p> Kullanıcı başına MFA'yı tek tek kullanıcı hesaplarında da yapılandırabilirsiniz, ancak bu önerilmez.|Küçük işletme|
|Microsoft 365 Business Premium <p> Microsoft 365 E3 <p> P1 lisanslarını Azure Active Directory (Azure AD) Premium|Grup üyeliğine, uygulamalara veya diğer ölçütlere göre kullanıcı hesapları için MFA gerektirmek için [güvenlik varsayılanlarını veya Koşullu Erişim ilkelerini](/microsoft-365/business-premium/m365bp-conditional-access) kullanın.|Küçük işletmeden kuruluşa|
|Microsoft 365 E5 <p> lisansları Azure AD Premium P2|Oturum açma risk ölçütlerine göre MFA gerektirmek için Azure AD Kimlik Koruması kullanın.|Enterprise|
||||

### <a name="security-defaults"></a>Güvenlik varsayılanları

Güvenlik varsayılanları, 21 Ekim 2019'da oluşturulan Microsoft 365 ve Office 365 ücretli veya deneme abonelikleri için yeni bir özelliktir. Bu aboneliklerin güvenlik varsayılanları açıktır ve bunlar:

- Tüm kullanıcılarınızın Microsoft Authenticator uygulamasıyla MFA kullanmasını gerektirir.
- Eski kimlik doğrulamasını engeller.

Kullanıcıların, güvenlik varsayılanları etkinleştirildikten sonra ilk kez oturum açtıktan sonra başlayan akıllı telefonlarından Microsoft Authenticator uygulamasına MFA'ya kaydolmaları için 14 günü vardır. 14 gün geçtikten sonra, MFA kaydı tamamlanana kadar kullanıcı oturum açamaz.

Güvenlik varsayılanları, tüm kuruluşların kullanıcı oturum açma için varsayılan olarak etkin olan temel bir güvenlik düzeyine sahip olmasını sağlar. Koşullu Erişim ilkeleriyle MFA'nın lehine güvenlik varsayılanlarını devre dışı bırakabilirsiniz.

Azure portal Azure AD için **Özellikler** bölmesinden güvenlik varsayılanlarını etkinleştirir veya devre dışı bırakırsınız.

![Dizin özellikleri sayfasının resmi.](../../media/multi-factor-authentication-microsoft-365/security-defaults-mfa.png)

Güvenlik varsayılanlarını herhangi bir Microsoft 365 planıyla kullanabilirsiniz.

Daha fazla bilgi için güvenlik [varsayılanlarına genel bakış konusuna](/azure/active-directory/fundamentals/concept-fundamentals-security-defaults) bakın.

### <a name="conditional-access-policies"></a>Koşullu Erişim ilkeleri

Koşullu Erişim ilkeleri, oturum açmaların değerlendirildiği ve izin verilen koşulları belirten bir dizi kuraldır. Örneğin, şunları belirten bir Koşullu Erişim ilkesi oluşturabilirsiniz:

- Kullanıcı hesabı adı Exchange, kullanıcı, parola, güvenlik, SharePoint veya genel yönetici rollerine atanmış kullanıcılar için bir grubun üyesiyse, erişime izin vermeden önce MFA gerektirir.

Bu ilke, bu yönetici rollerinden atanan veya atanmayan tek tek kullanıcı hesaplarını MFA için yapılandırmaya çalışmak yerine grup üyeliğine göre MFA'yı zorunlu kılmasını sağlar.

Koşullu Erişim ilkelerini, belirli uygulamalar için MFA gerektirme veya oturum açma işleminin Windows 10 çalıştıran dizüstü bilgisayarınız gibi uyumlu bir cihazdan yapılması gibi daha gelişmiş özellikler için de kullanabilirsiniz.

Koşullu Erişim ilkelerini, Azure portal Azure AD için **Güvenlik** bölmesinden yapılandırabilirsiniz.

![Koşullu Erişim menü seçeneğinin resmi.](../../media/multi-factor-authentication-microsoft-365/conditional-access-mfa.png)

Koşullu Erişim ilkelerini aşağıdakilerle kullanabilirsiniz:

- Microsoft 365 Business Premium
- Microsoft 365 E3 ve E5
- lisansları Azure AD Premium P1 ve Azure AD Premium P2

Microsoft 365 İş Ekstra sahip küçük işletmeler için aşağıdaki adımlarla Koşullu Erişim ilkelerini kolayca kullanabilirsiniz:

1. MFA gerektiren kullanıcı hesaplarını içeren bir grup oluşturun.
2. **Genel yöneticiler için MFA gerektir** ilkesini etkinleştirin.
3. Şu ayarlarla grup tabanlı bir Koşullu Erişim ilkesi oluşturun:
    - Atamalar > Kullanıcılar ve gruplar: Yukarıdaki 1. Adımdaki grubunuzun adı.
    - Bulut uygulamaları veya eylemleri > atamalar: Tüm bulut uygulamaları.
    - Erişim denetimleri > Erişim izni verme > Erişim izni verme > Çok faktörlü kimlik doğrulaması gerektir.
4. İlkeyi etkinleştirin.
5. Yukarıdaki 1. Adımda oluşturulan gruba bir kullanıcı hesabı ekleyin ve test edin.
6. Ek kullanıcı hesapları için MFA gerektirmek için bunları 1. Adım'da oluşturulan gruba ekleyin.

Bu Koşullu Erişim ilkesi, MFA gereksinimini kullanıcılarınıza kendi hızınızda dağıtmanıza olanak tanır.

Kuruluşlar, aşağıdaki ilkeleri yapılandırmak için [Ortak Koşullu Erişim ilkelerini](/azure/active-directory/conditional-access/concept-conditional-access-policy-common) kullanmalıdır:

- [Yöneticiler için MFA gerektir](/azure/active-directory/conditional-access/howto-conditional-access-policy-admin-mfa)
- [Tüm kullanıcılar için MFA gerektir](/azure/active-directory/conditional-access/howto-conditional-access-policy-all-users-mfa)
- [Eski kimlik doğrulamasını engelle](/azure/active-directory/conditional-access/howto-conditional-access-policy-block-legacy)

Daha fazla bilgi için bkz. [Koşullu Erişim'e genel bakış](/azure/active-directory/conditional-access/overview).

### <a name="azure-ad-identity-protection"></a>Azure AD Kimlik Koruması

Azure AD Kimlik Koruması ile, [oturum açma riski orta veya yüksek olduğunda MFA gerektirmek](../../security/office-365-security/identity-access-policies.md#require-mfa-based-on-sign-in-risk) için ek bir Koşullu Erişim ilkesi oluşturabilirsiniz.

Azure AD Kimlik Koruması ve risk tabanlı Koşullu Erişim ilkelerini aşağıdakilerle kullanabilirsiniz:

- Microsoft 365 E5
- lisansları Azure AD Premium P2

Daha fazla bilgi için Azure AD [Kimlik Koruması'nın bu genel bakışına](/azure/active-directory/identity-protection/overview-identity-protection) bakın.

### <a name="legacy-per-user-mfa-not-recommended"></a>Eski kullanıcı başına MFA (önerilmez)

Kullanıcı hesabı oturum açma işlemlerinizde MFA gerektirmek için güvenlik varsayılanlarını veya Koşullu Erişim ilkelerini kullanıyor olmanız gerekir. Bununla birlikte, bunlardan biri kullanılamıyorsa, Microsoft herhangi bir boyut aboneliği için yönetici rolüne sahip kullanıcı hesapları (özellikle genel yönetici rolü) için MFA'yı kesinlikle önerir.

Microsoft 365 yönetim merkezi <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">**Etkin kullanıcılar**</a> bölmesinden tek tek kullanıcı hesapları için MFA'yı etkinleştirirsiniz.

![Etkin kullanıcılar sayfasındaki Çok faktörlü kimlik doğrulama seçeneğinin resmi.](../../media/multi-factor-authentication-microsoft-365/per-user-mfa.png)

Etkinleştirildikten sonra, kullanıcı bir sonraki oturum açtığında MFA'ya kaydolması ve ek doğrulama yöntemini seçip test etmeleri istenir.

### <a name="using-these-methods-together"></a>Bu yöntemleri birlikte kullanma

Bu tabloda güvenlik varsayılanları, Koşullu Erişim ilkeleri ve kullanıcı başına hesap ayarlarıyla MFA'yı etkinleştirmenin sonuçları gösterilir.

|*Öğe*|Etkin|Devre dışı|İkincil kimlik doğrulama yöntemi|
|---|---|---|---|
|**Güvenlik varsayılanları**|Koşullu Erişim ilkeleri kullanılamaz|Koşullu Erişim ilkelerini kullanabilir|Microsoft Authenticator uygulaması|
|**Koşullu Erişim ilkeleri**|Etkinse, güvenlik varsayılanlarını etkinleştiremezsiniz|Tümü devre dışı bırakılırsa, güvenlik varsayılanlarını etkinleştirebilirsiniz|MFA kaydı sırasında kullanıcı tarafından belirtilen|
|**Eski kullanıcı başına MFA (önerilmez)**|Her oturum açmada MFA gerektiren güvenlik varsayılanlarını ve Koşullu Erişim ilkelerini geçersiz kılar|Güvenlik varsayılanları ve Koşullu Erişim ilkeleri tarafından geçersiz kılınıyor|MFA kaydı sırasında kullanıcı tarafından belirtilen|
||||

Güvenlik varsayılanları etkinse, tüm yeni kullanıcılardan bir sonraki oturum açmalarında MFA kaydı ve Microsoft Authenticator uygulamasının kullanımı istenir.

## <a name="ways-to-manage-mfa-settings"></a>MFA ayarlarını yönetmenin yolları

MFA ayarlarını yönetmenin iki yolu vardır.

Azure portal şunları yapabilirsiniz:

- Güvenlik varsayılanlarını etkinleştirme ve devre dışı bırakma
- Koşullu Erişim ilkelerini yapılandırma

Microsoft 365 yönetim merkezi kullanıcı ve hizmet başına <a href="https://go.microsoft.com/fwlink/p/?linkid=2169174" target="_blank">MFA ayarlarını</a> yapılandırabilirsiniz.

## <a name="next-steps"></a>Sonraki adımlar

[Microsoft 365 için MFA'yı ayarlama](set-up-multi-factor-authentication.md)

## <a name="related-content"></a>İlgili içerik

[Çok faktörlü kimlik doğrulamasını açma](set-up-multi-factor-authentication.md) (video)\
[Telefonunuz için çok faktörlü kimlik doğrulamasını açma](https://support.microsoft.com/office/ace1d096-61e5-449b-a875-58eb3d74de14) (video)