---
title: Multifactor authentication for Microsoft 365
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
description: Çok faktörlü kimlik doğrulaması (MFA), güçlü olması gereken bir parola ve ek bir doğrulama yöntemi kullanır.
ms.openlocfilehash: 460de9426dfb249da17d5df79becaca725ee36ed
ms.sourcegitcommit: b1066b2a798568afdea9c09401d52fa38fe93546
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/13/2021
ms.locfileid: "63018783"
---
# <a name="multifactor-authentication-for-microsoft-365"></a>Multifactor authentication for Microsoft 365

Parolalar, bilgisayarda veya çevrimiçi hizmette oturum açma kimlik doğrulamanın en yaygın yöntemidir, ancak aynı zamanda en korumasız durumdadır. Kişiler kolay parolalar seçebilir ve farklı bilgisayarlar ve hizmetlere birden çok oturum açmada aynı parolaları kullanabilirler.

Oturum açmalarda ek güvenlik düzeyi sağlamak için, hem güçlü olması gereken bir parola hem de şu temel alınan ek doğrulama yöntemini kullanan Çok Faktörlü Kimlik Doğrulaması (MFA) kullan gerekir:

- Sahip olduğunuz ve kolayca çoğaltılmış bir akıllı telefon gibi bir şey.
- Benzersiz ve fiziksel olarak sahip olduğunuz parmak izi, yüz tanıma veya diğer biyometrik öznitelik gibi bir şey.

Kullanıcının parolası doğrulandıktan sonra, ek doğrulama yöntemi yer almaz. MFA ile, güçlü bir kullanıcı parolası ihlal edilmiş olsa bile, saldırganın oturum açma işlemini tamamlamak için akıllı telefonunuz veya parmak iziniz olmaz.

## <a name="mfa-support-in-microsoft-365"></a>Microsoft 365'de MFA Microsoft 365

Varsayılan olarak, hem Microsoft 365 hem Office 365 hesapları için MFA'ya destek olur:

- Telefona gönderilen ve kullanıcının doğrulama kodunu yazması gereken bir kısa mesaj.
- Bir telefon görüşmesi.
- Akıllı Microsoft Authenticator uygulaması.

Her iki durumda da, MFA oturum açma işlemi, ek doğrulama için "sahip olduğunuz ve kolayca çoğaltılmış değil" yöntemini kullanıyor. Birden çok şekilde MFA'yi kendi iş ve iş Microsoft 365 Office 365:

- Güvenlik varsayılanları ile
- Koşullu Erişim ilkeleriyle
- Tek tek her kullanıcı hesabı için (önerilmez)

Bu yollar plan planınıza Microsoft 365 vardır.

|Plan|Öneri|Müşteri türü|
|---|---|---|
|Tüm Microsoft 365 planları|Tüm kullanıcı hesapları için MFA gerektiren güvenlik varsayılanlarını kullanın. <p> Tek tek kullanıcı hesapları için de kullanıcı başına MFA yapılandırabilirsiniz, ancak bu önerilmez.|Küçük işletme|
|Microsoft 365 Business Premium <p> Microsoft 365 E3 <p> Azure Active Directory (Azure AD) Premium P1 lisansları|Grup üyeliği, uygulamalar veya diğer ölçütlere dayalı olarak kullanıcı hesapları için MFA gerektiren Koşullu Erişim ilkelerini kullanın.|Küçük işletmeden kuruluşa|
|Microsoft 365 E5 <p> Azure AD Premium P2 lisansları|Oturum açma riski ölçütlerine göre MFA gerektirmek için Azure AD Identity Protection'i kullanın.|Enterprise|
||||

### <a name="security-defaults"></a>Güvenlik varsayılanları

Güvenlik varsayılanları, 21 Ekim 2019'dan Microsoft 365 sonra Office 365 veya deneme abonelikleri için yeni bir özelliktir. Bu aboneliklerin güvenlik varsayılanları açıktır ve bu da:

- Tüm kullanıcılarının Microsoft Authenticator uygulamasıyla MFA'Microsoft Authenticator gerektirir.
- Eski kimlik doğrulamasını engeller.

Kullanıcıların, güvenlik varsayılanları etkinleştirildikten sonra ilk kez oturum açmalarından başlanacak olan Microsoft Authenticator uygulamasıyla MFA'ya kaydolmaları için 14 günü vardır. 14 gün sonra, MFA kaydı tamamlanana kadar kullanıcı oturum açmaz.

Güvenlik varsayılanları, tüm kuruluşların, kullanıcı oturum açma için varsayılan olarak etkinleştiren temel güvenlik düzeyine sahip olmasını sağlar. Koşullu Erişim ilkeleriyle MFA'nın tercihi olarak güvenlik varsayılanlarını devre dışı  devre dışı  olabilirsiniz.

Azure portalda, Azure AD için Özellikler bölmesinde **güvenlik** varsayılanlarını etkinleştirir veya devre dışı bırakabilirsiniz.

![Dizin özellikleri sayfasının resmi.](../../media/multi-factor-authentication-microsoft-365/security-defaults-mfa.png)

Herhangi bir plan için güvenlik varsayılanlarını Microsoft 365 kullanabilirsiniz.

Daha fazla bilgi için bu güvenlik [varsayılanlarına genel bakış bilgilerine bakın](/azure/active-directory/fundamentals/concept-fundamentals-security-defaults).

### <a name="conditional-access-policies"></a>Koşullu Erişim ilkeleri

Koşullu Erişim ilkeleri, oturum açmaların değerlendirilmesini ve izin verilen koşulları belirten bir dizi kuraldır. Örneğin, şöyle bir Koşullu Erişim ilkesi oluşturabilirsiniz:

- Kullanıcı hesabı adı Exchange, kullanıcı, parola, güvenlik, SharePoint veya genel yönetici rollerine atanan kullanıcılar için bir grubun üyesiyse, erişime izin vermeden önce MFA'ya gerek vardır.

Bu ilke, bu yönetici rollerine atanan veya atanmamış durumdayken MFA için tek tek kullanıcı hesaplarını yapılandırmaya çalışma yerine, grup üyeliğini temel alarak MFA gerektirmenizi sağlar.

Belirli uygulamalar için MFA gerektirme veya oturum açmanın dizüstü bilgisayarınız gibi uyumlu bir cihazdan yapılması gibi daha gelişmiş özellikler için Koşullu Erişim ilkelerini de Windows 10.

Azure portalda Azure AD **için Güvenlik** bölmesinden Koşullu Erişim ilkelerini yapılandırabilirsiniz.

![Koşullu Erişim için menü seçeneğinin resmi.](../../media/multi-factor-authentication-microsoft-365/conditional-access-mfa.png)

Koşullu Erişim ilkelerini aşağıdakilerle kullanabilirsiniz:

- Microsoft 365 Business Premium
- Microsoft 365 E3 ve E5
- Azure AD Premium P1 ve Azure AD Premium P2 lisansları

Koşullu Erişim ilkeleri olan Microsoft 365 İş Ekstra işletmeler için, aşağıdaki adımları kullanarak Koşullu Erişim ilkelerini kolayca kullanabilirsiniz:

1. MFA gerektiren kullanıcı hesaplarını içeren bir grup oluşturun.
2. Genel yöneticiler **için MFA gerektir politikasını** etkinleştirin.
3. Şu ayarlarla grup tabanlı bir Koşullu Erişim ilkesi oluşturun:
    - Ödevler > grupların adı: Yukarıdaki 1. Adımda yer alan grubu adı.
    - Ödevler > uygulamaları veya eylemleri: Tüm bulut uygulamaları.
    - Çok faktörlü > için > Izni ver> için erişim denetimleri.
4. İlkeyi etkinleştirin.
5. Yukarıdaki 1. Adımda oluşturulan gruba bir kullanıcı hesabı ekleyin ve test edin.
6. Başka kullanıcı hesapları için MFA gerektirmek için, onları 1. Adımda oluşturulan gruba ekleyin.

Bu Koşullu Erişim ilkesi, MFA gereksinimini kullanıcılarınıza kendi hızınıza göre uygulamanıza olanak sağlar.

Kuruluşlar, aşağıdaki [ilkeleri yapılandırmak için Ortak](/azure/active-directory/conditional-access/concept-conditional-access-policy-common) Koşullu Erişim ilkelerini kullanmalıdır:

- [Yöneticiler için MFA gerektirme](/azure/active-directory/conditional-access/howto-conditional-access-policy-admin-mfa)
- [Tüm kullanıcılar için MFA gerektirme](/azure/active-directory/conditional-access/howto-conditional-access-policy-all-users-mfa)
- [Eski kimlik doğrulamayı engelle](/azure/active-directory/conditional-access/howto-conditional-access-policy-block-legacy)

Daha fazla bilgi için Koşullu [Erişim'e genel bakış bilgilerine bakın](/azure/active-directory/conditional-access/overview).

### <a name="azure-ad-identity-protection"></a>Azure AD Identity Protection

Azure AD Kimlik Koruması ile, oturum açma riski orta veya yüksek olduğunda [MFA gerektirecek ek bir Koşullu Erişim ilkesi oluşturabilirsiniz](../../security/office-365-security/identity-access-policies.md#require-mfa-based-on-sign-in-risk).

Azure AD Kimlik Koruması ve risk tabanlı Koşullu Erişim ilkelerini aşağıdakilerle kullanabilirsiniz:

- Microsoft 365 E5
- Azure AD Premium P2 lisansları

Daha fazla bilgi için bkz. [Azure AD Identity Protection'a genel bakış](/azure/active-directory/identity-protection/overview-identity-protection).

### <a name="legacy-per-user-mfa-not-recommended"></a>Kullanıcı başına eski MFA (önerilmez)

Kullanıcı hesabı oturum açmaları için MFA gerektirmeye yönelik güvenlik varsayılanları veya Koşullu Erişim ilkeleri kullansanız iyi olur. Bununla birlikte, bu hesaplardan herhangi biri kullanılamazsa, Microsoft herhangi bir boyut aboneliği için, yönetici rollerine sahip olan kullanıcı hesapları (özellikle de genel yönetici rolü) için MFA'nın kullanılması önerilir.

Etki alanı bölmesinin Etkin kullanıcılar bölmesinden tek tek <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">**kullanıcı hesapları için**</a> MFA'Microsoft 365 yönetim merkezi.

![Etkin kullanıcılar sayfasındaki Multi factor authentication seçeneğinin resmi.](../../media/multi-factor-authentication-microsoft-365/per-user-mfa.png)

Etkinleştirildikten sonra, kullanıcı bir sonraki oturum a oturumda MFA'ya kaydolması ve ek doğrulama yöntemini seçmesi ve sınaması istenir.

### <a name="using-these-methods-together"></a>Bu yöntemleri birlikte kullanma

Bu tabloda, güvenlik varsayılanları, Koşullu Erişim ilkeleri ve kullanıcı başına hesap ayarlarıyla MFA'nın etkinleştirilmesi sonuçları gösterir.

|*Öğe*|Etkin|Devre dışı|İkincil kimlik doğrulama yöntemi|
|---|---|---|---|
|**Güvenlik varsayılanları**|Koşullu Erişim ilkeleri kullanama|Koşullu Erişim ilkelerini kullanabilir|Microsoft Authenticator uygulaması|
|**Koşullu Erişim ilkeleri**|Etkinse, güvenlik varsayılanlarını etkinleştiresiniz|Tüm devre dışı bırakılmışsa güvenlik varsayılanlarını etkinleştir|MFA kaydı sırasında kullanıcı tarafından belirtilmiş|
|**Kullanıcı başına eski MFA (önerilmez)**|Her oturum açmada MFA gerektiren güvenlik varsayılanlarını ve Koşullu Erişim ilkelerini geçersiz kılar|Güvenlik varsayılanlarını ve Koşullu Erişim ilkelerini geçersiz kılma|MFA kaydı sırasında kullanıcı tarafından belirtilmiş|
||||

Güvenlik varsayılanları etkinse, tüm yeni kullanıcılardan MFA kaydı ve bir sonraki oturum açmalarında Microsoft Authenticator uygulamasının kullanımı istenir.

## <a name="ways-to-manage-mfa-settings"></a>MFA ayarlarını yönetme yolları

MFA ayarlarını yönetmenin iki yolu vardır.

Azure portalında şunları kullanabilirsiniz:

- Güvenlik varsayılanlarını etkinleştirme ve devre dışı bırakma
- Koşullu Erişim ilkelerini yapılandırma

Aşağıdaki Microsoft 365 yönetim merkezi, kullanıcı ve hizmet MFA ayarlarını tek tek <a href="https://go.microsoft.com/fwlink/p/?linkid=2169174" target="_blank">yapılandırabilirsiniz</a>.

## <a name="next-steps"></a>Sonraki adımlar

[MFA'ya iş Microsoft 365](set-up-multi-factor-authentication.md)

## <a name="related-content"></a>İlgili içerik

[Çok faktörlü kimlik doğrulamasını](set-up-multi-factor-authentication.md) açma (video)\
[Telefonunuz için çok faktörlü kimlik doğrulamasını açma](https://support.microsoft.com/office/ace1d096-61e5-449b-a875-58eb3d74de14) (video)