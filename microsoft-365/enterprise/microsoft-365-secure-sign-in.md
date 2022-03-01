---
title: '3. Adım: Microsoft 365 hesaplarınızı koruma'
f1.keywords:
- NOCSH
author: kelleyvice-msft
ms.author: kvice
manager: laurawi
ms.date: 09/30/2020
audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- Strat_O365_Enterprise
- m365initiative-coredeploy
ms.custom: ''
description: Kullanıcılarının çok faktörlü kimlik doğrulaması (MFA) ve diğer özelliklerle güvenli bir şekilde oturum açmasını gerekli hale geldi.
ms.openlocfilehash: c144b374ecc49128e11635c034f3b4b76020eafd
ms.sourcegitcommit: 6c57f1e90339d5a95c9e7875599dac9d3e032c3a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/04/2022
ms.locfileid: "63016475"
---
# <a name="step-3-protect-your-microsoft-365-user-accounts"></a>3. Adım: Microsoft 365 hesaplarınızı koruma

Kullanıcı oturum açmalarının güvenliğini artırmak için:

- Windows Hello Kurumsal'i kullanma
- Parola Azure Active Directory (Azure AD) Parola Koruması kullanma
- Çok faktörlü kimlik doğrulamasını (MFA) kullanma
- Kimlik ve cihaz erişimi yapılandırmalarını dağıtma
- Azure AD Kimlik Koruması ile kimlik bilgilerinin tehlikeye atlarına karşı koruma

## <a name="windows-hello-for-business"></a>Windows Hello Kurumsal

Windows Hello Kurumsal'da Windows 10 Enterprise, Windows cihazında oturum açmada, parolaları güçlü iki faktörlü kimlik Windows değiştirir. Bu iki etmen bir cihaza bağlı olan yeni bir kullanıcı kimlik bilgileri türü ve bir biyometrik veya PIN'tir.

Daha fazla bilgi için bkz[. Windows Hello Genel Bakış](/windows/security/identity-protection/hello-for-business/hello-overview).


## <a name="azure-ad-password-protection"></a>Azure AD Parola Koruması

Azure AD Parola Koruması, bilinen zayıf parolaları ve değişkenlerini algılar ve engeller; ayrıca, organizasyonuma özgü ek zayıf terimleri de engelleyebilir. Varsayılan genel yasaklanmış parola listeleri, Bir Azure AD kiracısı'nın tüm kullanıcılarına otomatik olarak uygulanır. Özel bir yasaklanan parola listesinde ek girişler tanımlayabilirsiniz. Kullanıcılar parolalarını değiştirse veya sıfırlasa, güçlü parolaların kullanımını zorunlu yapmak için bu yasaklanmış parola listeleri denetlenir.

Daha fazla bilgi için bkz [. Azure AD parola korumasını yapılandırma](/azure/active-directory/authentication/concept-password-ban-bad).

## <a name="mfa"></a>MFA

MFA, kullanıcı oturum açma hesaplarının kullanıcı hesabı parolasının ötesinde başka bir doğrulamaya tabi olması gerekir. Kötü niyetli bir kullanıcı bir kullanıcı hesabı parolası belirlerse bile, erişim izni verilmeden önce akıllı telefona gönderilen SMS gibi ek bir doğrulamayı yanıtlayabiliyor olması gerekir.

![Doğru parolanın yanı sıra ek doğrulama da başarılı bir oturum açma işlemiyle sonuç verir.](../media/empower-people-to-work-remotely/remote-workers-mfa.png)

MFA kullanmanın ilk adımı, ayrıcalıklı [hesaplar](protect-your-global-administrator-accounts.md) olarak da bilinen tüm yönetici hesapları için bunu gerektirmektir. Microsoft, bu ilk adımın ötesinde tüm kullanıcılar için MFA'ya izinler de sağlar.

Kullanıcılarının kendi planlarınızı temel alarak MFA kullanmalarını gerektiren üç Microsoft 365 vardır.

| Plan | Öneri |
|---------|---------|
|Tüm Microsoft 365 planları (Azure AD Premium P1 P2 lisansı olmadan)     |[Azure AD'de güvenlik varsayılanlarını etkinleştirin](/azure/active-directory/fundamentals/concept-fundamentals-security-defaults). Azure AD'de güvenlik varsayılanları, kullanıcılar ve yöneticiler için MFA içerir.   |
|Microsoft 365 E3 (Azure AD Premium P1 içerir)     | Aşağıdaki ilkeleri [yapılandırmak için yaygın Koşullu](/azure/active-directory/conditional-access/concept-conditional-access-policy-common) Erişim ilkelerini kullanın: <br>- [Yöneticiler için MFA gerektirme](/azure/active-directory/conditional-access/howto-conditional-access-policy-admin-mfa) <br>- [Tüm kullanıcılar için MFA gerektirme](/azure/active-directory/conditional-access/howto-conditional-access-policy-all-users-mfa) <br> - [Eski kimlik doğrulamayı engelle](/azure/active-directory/conditional-access/howto-conditional-access-policy-block-legacy)       |
|Microsoft 365 E5 (Azure AD Premium P2 içerir)     | Azure AD Kimlik Koruması'ndan yararlanmak için, bu iki ilke oluşturarak Microsoft'un önerilen Koşullu Erişim ve ilgili ilkeler setlerini uygulamaya başlayabilirsiniz:<br> - [Oturum açma riski orta veya yüksek olduğunda MFA gerektirme](/azure/active-directory/conditional-access/howto-conditional-access-policy-risk) <br>- [Yüksek riskli kullanıcıların parolayı değiştirmesi gerekir](/azure/active-directory/conditional-access/howto-conditional-access-policy-risk-user)       |
| | |

### <a name="security-defaults"></a>Güvenlik varsayılanları

Güvenlik varsayılanları, 21 Ekim 2019'dan Microsoft 365 sonra Office 365 veya deneme abonelikleri için yeni bir özelliktir. Bu aboneliklerin güvenlik varsayılanları açıktır ve bu da kullanıcılarının tüm kullanıcılarının ***Microsoft Authenticator gerektirir***.
 
Kullanıcıların, güvenlik varsayılanları etkinleştirildikten sonra ilk kez oturum açmalarından başlanacak olan Microsoft Authenticator uygulamasıyla MFA'ya kaydolmaları için 14 günü vardır. 14 gün sonra, MFA kaydı tamamlanana kadar kullanıcı oturum açmaz.

Güvenlik varsayılanları, tüm kuruluşların, kullanıcı oturum açma için varsayılan olarak etkinleştiren temel güvenlik düzeyine sahip olmasını sağlar. Koşullu Erişim ilkeleri veya tek tek hesaplar için MFA'nın tercihi olarak güvenlik varsayılanlarını devre dışı abilirsiniz.

Daha fazla bilgi için güvenlik [varsayılanlarına genel bakış bilgilerine bakın](/azure/active-directory/fundamentals/concept-fundamentals-security-defaults).

### <a name="conditional-access-policies"></a>Koşullu Erişim ilkeleri

Koşullu Erişim ilkeleri, oturum açmaların değerlendirilmesini ve erişim verilmesini belirten koşulları belirten bir dizi kuraldır. Örneğin, şöyle bir Koşullu Erişim ilkesi oluşturabilirsiniz:

- Kullanıcı hesabı adı Exchange, kullanıcı, parola, güvenlik, SharePoint, Exchange yöneticisi, **SharePoint yöneticisi** veya Genel yönetici rollerine atanan kullanıcılar için **bir** grubun üyesiyseniz, erişime izin vermeden önce MFA gerektirir.

Bu ilke, bu yönetici rollerine atanan veya atanmamış durumdayken MFA için tek tek kullanıcı hesaplarını yapılandırmaya çalışma yerine, grup üyeliğini temel alarak MFA gerektirmenizi sağlar.

Ayrıca, oturum açmanın dizüstü bilgisayarınız gibi uyumlu bir cihazdan yapılması gerektirme gibi daha gelişmiş özellikler için Koşullu Erişim ilkelerini Windows 10.

Koşullu Erişim için Azure AD Premium P1 ve E5 ile birlikte Microsoft 365 E3 lisansları gerekir.

Daha fazla bilgi için Koşullu [Erişim'e genel bakış bilgilerine bakın](/azure/active-directory/conditional-access/overview).

### <a name="using-these-methods-together"></a>Bu yöntemleri birlikte kullanma

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

## <a name="zero-trust-identity-and-device-access-configurations"></a>Sıfır Güven kimliği ve cihaz erişimi yapılandırmaları

Sıfır Güven kimliği ve cihaz erişimi ayarları ve ilkeleri, belirli bir erişim isteğinin verili olup olmadığını ve hangi koşullar altında ver verilmesi gerektiğini belirleyen Koşullu Erişim, Intune ve Azure AD Kimlik Koruması ilkeleriyle birleştirilmiş, önkoşul özellikleri ve ayarları önerilir. Bu belirleme, oturum açma kullanıcının hesabına, kullanılan cihaza, kullanıcının erişim için kullandığı uygulamaya, erişim isteğinin bulunduğu konuma ve isteğin risklerinin değerlendirmesine dayalıdır. Bu özellik, kritik kaynaklarınıza yalnızca onaylı kullanıcıların ve cihazların erişmelerini sağlamaya yardımcı olur.

>[!Note]
>Azure AD Kimlik Koruması için Azure AD Premium P2 lisansları gerekir ve bu lisanslar Microsoft 365 E5.
>

Kimlik ve cihaz erişim ilkeleri üç katmanda kullanılacak şekilde tanımlanır: 

- Taban çizgisi koruması, uygulamalarınıza ve verilerinize erişen kimlikleriniz ve cihazlarınız için en düşük güvenlik düzeyidir.
- Hassas koruma, belirli veriler için ek güvenlik sağlar. Kimlikler ve cihazlar daha yüksek güvenlik ve cihaz sistem durumu gereksinimlerine tabi olur.
- Çok düzenlemeye tabi veya sınıflandırılmış verilerin olduğu ortamların koruması, genellikle üst düzeyde sınıflandırılmış, ticari sırlar içeren veya veri düzenlemelerine tabi olan az miktarda veriye yöneliktir. Kimlikler ve cihazlar çok daha yüksek düzeyde güvenlik ve cihaz sistem durumu gereksinimlerine tabi olur. 

Bu katmanlar ve bunlara karşılık gelen yapılandırmalar verileriniz, kimlikleriniz ve cihazlarınız arasında tutarlı koruma düzeyleri sağlar.

Microsoft; güvenlik, güvenlik özellikleri ve güvenlik özellikleri için belirli ayarlar da dahil olmak üzere, kuruluşta Sıfır Güveni kimliği ve cihaz erişim ilkelerinin yapılandırılmasını Microsoft Teams Exchange Online SharePoint. Daha fazla bilgi için bkz. [Sıfır Güven kimliği ve cihaz erişimi yapılandırmaları](../security/office-365-security/microsoft-365-policies-configurations.md).

## <a name="azure-ad-identity-protection"></a>Azure AD Identity Protection

Bu bölümde, kimlik bilgilerinin güvenliği tehlikeye atıldığında bir saldırganın, kuruluşun bulut hizmetlerine ve verilerine erişim elde etmek için kullanıcının hesap adını ve parolasını belirlemesi gereken ilkeler yapılandırmayı öğrenirsiniz. Azure AD Identity Protection, bir saldırganın kullanıcı hesabının kimlik bilgilerinden ödün vermesini önlemeye yardımcı olmak için çeşitli yollar sağlar.

Azure AD Kimlik Koruması ile şunları kullanabilirsiniz:

|Özellik|Açıklama|
|:---------|:---------|
| Kuruluş kimlikleri olası güvenlik açıklarını belirleme ve bu güvenlik açıklarını belirleme | Azure AD, makine öğrenimi aracılığıyla oturum açma ve oturum açma sonrası etkinlikleri gibi şüpheli etkinlikleri algılar. Azure AD Kimlik Koruması, bu verileri kullanarak sorunları değerlendirmeye ve önlem almaya yardımcı olan raporlar ve uyarılar üretir.|
|Kuruluş kimlikleriyle ilgili şüpheli eylemleri algılama ve bunları otomatik olarak yanıtlama|Belirli bir risk düzeyine ulaşıldığında algılanan sorunları otomatik olarak yanıtlayan risk tabanlı ilkeleri yapılandırabilirsiniz. Bu ilkeler, Azure AD ve Microsoft Intune tarafından sağlanan diğer Koşullu Erişim denetimlerine ek olarak, erişimi otomatik olarak engelleyebilir veya parola sıfırlamaları gibi düzeltme eylemleri gerçekleştirerek sonraki oturum açma işlemleri için Azure AD Multi-Factor Authentication'ın gerekli olduğunu gösterir. |
| Şüpheli olayları araştırma ve bunları yönetim eylemleriyle çözme | Güvenlik olayıyla ilgili bilgileri kullanarak risk olaylarını araştırebilirsiniz. Temel iş akışları, soruşturmaları izlemek ve parola sıfırlaması gibi düzeltme eylemleri başlatmak için kullanılabilir. |
|||

[Azure AD Kimlik Koruması hakkında daha fazla bilgi edinin](/azure/active-directory/identity-protection/overview-identity-protection).

[Azure AD Identity Protection'i etkinleştirme adımlarına bakın](/azure/active-directory/identity-protection/howto-identity-protection-configure-risk-policies).

## <a name="admin-technical-resources-for-mfa-and-secure-sign-ins"></a>MFA ve güvenli oturum açmalar için yönetici teknik kaynakları

- [Microsoft 365 için MFA](../admin/security-and-compliance/multi-factor-authentication-microsoft-365.md)
- [Dağıtım kimliği Microsoft 365](deploy-identity-solution-overview.md)
- [Azure Academy Azure AD eğitim videoları](https://www.youtube.com/watch?v=pN8o0owHfI0&list=PL-V4YVm6AmwUFpC3rXr2i2piRQ708q_ia)
- [Azure AD Multi-Factor Authentication kayıt ilkesi yapılandırma](/azure/active-directory/identity-protection/howto-identity-protection-configure-mfa-policy)
- [Kimlik ve cihaz erişimi yapılandırmaları](../security/office-365-security/microsoft-365-policies-configurations.md)

## <a name="next-step"></a>Sonraki adım

![Kimlik modelinizi dağıtma](../media/deploy-identity-solution-overview/deploy-identity-solution-identity-infrastructure.png)

4. Adım ile devam edin ve seçilen kimlik modelinize dayalı kimlik altyapısını dağıtın:

- [Yalnızca bulut kimliği](cloud-only-identities.md)
- [Karma kimlik](prepare-for-directory-synchronization.md)
