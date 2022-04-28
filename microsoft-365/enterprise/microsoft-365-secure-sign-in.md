---
title: '3. Adım: Microsoft 365 kullanıcı hesaplarınızı koruma'
f1.keywords:
- NOCSH
author: kelleyvice-msft
ms.author: kvice
manager: scotv
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
description: Kullanıcılarınızın çok faktörlü kimlik doğrulaması (MFA) ve diğer özelliklerle güvenli bir şekilde oturum açmasını zorunlu kılar.
ms.openlocfilehash: 4566b2c8c73ce258899e1de6ef621715092e50a5
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65090285"
---
# <a name="step-3-protect-your-microsoft-365-user-accounts"></a>3. Adım: Microsoft 365 kullanıcı hesaplarınızı koruma

Kullanıcı oturum açma bilgilerinin güvenliğini artırmak için:

- İş İçin Windows Hello kullanma
- Azure Active Directory (Azure AD) Parola Koruması kullanma
- Çok faktörlü kimlik doğrulamasını (MFA) kullanma
- Kimlik ve cihaz erişim yapılandırmalarını dağıtma
- Azure AD Kimlik Koruması ile kimlik bilgilerinin tehlikeye atılmasına karşı koruma

## <a name="windows-hello-for-business"></a>İş İçin Windows Hello

Windows 10 Enterprise'da İş İçin Windows Hello, Windows cihazda oturum açarken parolaları güçlü iki faktörlü kimlik doğrulamasıyla değiştirir. İki faktör, bir cihaza ve biyometrik veya PIN'e bağlı yeni bir kullanıcı kimlik bilgisi türüdür.

Daha fazla bilgi için bkz. [İş İçin Windows Hello Genel Bakış](/windows/security/identity-protection/hello-for-business/hello-overview).


## <a name="azure-ad-password-protection"></a>Azure AD Parola Koruması

Azure AD Parola Koruması bilinen zayıf parolaları ve bunların değişkenlerini algılar ve engeller ve ayrıca kuruluşunuza özgü ek zayıf terimleri engelleyebilir. Varsayılan genel yasaklanmış parola listeleri, Bir Azure AD kiracısında tüm kullanıcılara otomatik olarak uygulanır. Özel yasaklanmış parola listesinde ek girdiler tanımlayabilirsiniz. Kullanıcılar parolalarını değiştirdiğinde veya sıfırladığında, bu yasaklanmış parola listeleri güçlü parolaların kullanımını zorunlu kılmak için denetlenir.

Daha fazla bilgi için bkz. [Azure AD parola korumasını yapılandırma](/azure/active-directory/authentication/concept-password-ban-bad).

## <a name="mfa"></a>MFA

MFA, kullanıcı oturum açma işlemleri için kullanıcı hesabı parolasının ötesinde ek bir doğrulamaya tabi olmasını gerektirir. Kötü amaçlı bir kullanıcı bir kullanıcı hesabı parolası belirlese bile, erişim verilmeden önce akıllı telefona gönderilen kısa mesaj gibi ek bir doğrulamaya yanıt verebilmelidir.

![Doğru parolanın yanı sıra ek doğrulama başarılı bir oturum açma işlemiyle sonuçlanmıştır.](../media/empower-people-to-work-remotely/remote-workers-mfa.png)

MFA'yı kullanmanın ilk adımı, ayrıcalıklı hesaplar olarak da bilinen [tüm yönetici hesapları için gerekli olmasını sağlamaktır](protect-your-global-administrator-accounts.md). Microsoft, bu ilk adımın ötesinde tüm kullanıcılar için MFA'yı önerir.

Kullanıcılarınızın Microsoft 365 planınıza göre MFA kullanmasını gerektirmenin üç yolu vardır.

| Plan | Öneri |
|---------|---------|
|Tüm Microsoft 365 planları (Azure AD Premium P1 veya P2 lisansları olmadan)     |[Azure AD'de güvenlik varsayılanlarını etkinleştirin](/azure/active-directory/fundamentals/concept-fundamentals-security-defaults). Azure AD'deki güvenlik varsayılanları, kullanıcılar ve yöneticiler için MFA içerir.   |
|Microsoft 365 E3 (Azure AD Premium P1 lisansları içerir)     | Aşağıdaki ilkeleri yapılandırmak için [yaygın Koşullu Erişim ilkelerini](/azure/active-directory/conditional-access/concept-conditional-access-policy-common) kullanın: <br>- [Yöneticiler için MFA gerektir](/azure/active-directory/conditional-access/howto-conditional-access-policy-admin-mfa) <br>- [Tüm kullanıcılar için MFA gerektir](/azure/active-directory/conditional-access/howto-conditional-access-policy-all-users-mfa) <br> - [Eski kimlik doğrulamasını engelle](/azure/active-directory/conditional-access/howto-conditional-access-policy-block-legacy)       |
|Microsoft 365 E5 (Azure AD Premium P2 lisansları içerir)     | Azure AD Kimlik Koruması'nın avantajlarından yararlanarak, şu iki ilkeyi oluşturarak Microsoft'un önerilen Koşullu Erişim ve ilgili ilkeler kümesini uygulamaya başlayın:<br> - [Oturum açma riski orta veya yüksek olduğunda MFA gerektirme](/azure/active-directory/conditional-access/howto-conditional-access-policy-risk) <br>- [Yüksek riskli kullanıcıların parola değiştirmesi gerekir](/azure/active-directory/conditional-access/howto-conditional-access-policy-risk-user)       |
| | |

### <a name="security-defaults"></a>Güvenlik varsayılanları

Güvenlik varsayılanları, 21 Ekim 2019'da oluşturulan Microsoft 365 ve Office 365 ücretli veya deneme abonelikleri için yeni bir özelliktir. Bu aboneliklerde güvenlik varsayılanları açıktır ve ***bu da tüm kullanıcılarınızın Microsoft Authenticator uygulamasıyla MFA kullanmasını gerektirir***.
 
Kullanıcıların, güvenlik varsayılanları etkinleştirildikten sonra ilk kez oturum açtıktan sonra başlayan akıllı telefonlarından Microsoft Authenticator uygulamasına MFA'ya kaydolmaları için 14 günü vardır. 14 gün geçtikten sonra, MFA kaydı tamamlanana kadar kullanıcı oturum açamaz.

Güvenlik varsayılanları, tüm kuruluşların kullanıcı oturum açma için varsayılan olarak etkin olan temel bir güvenlik düzeyine sahip olmasını sağlar. Koşullu Erişim ilkeleriyle veya tek tek hesaplar için MFA'nın lehine güvenlik varsayılanlarını devre dışı bırakabilirsiniz.

Daha fazla bilgi için bkz. [Güvenlik varsayılanlarına genel bakış](/azure/active-directory/fundamentals/concept-fundamentals-security-defaults).

### <a name="conditional-access-policies"></a>Koşullu Erişim ilkeleri

Koşullu Erişim ilkeleri, oturum açmaların değerlendirildiği ve erişimin verildiği koşulları belirten bir dizi kuraldır. Örneğin, şunları belirten bir Koşullu Erişim ilkesi oluşturabilirsiniz:

- Kullanıcı hesabı adı Exchange, kullanıcı, parola, güvenlik, SharePoint, Exchange yöneticisi, **SharePoint yöneticisi** veya **Genel yönetici** rolleri atanmış kullanıcılar için bir grubun üyesiyse, erişime izin vermeden önce MFA'yı gerektirir.

Bu ilke, bu yönetici rollerinden atandığında veya atanmadığında MFA için tek tek kullanıcı hesaplarını yapılandırmaya çalışmak yerine grup üyeliğine göre MFA'yı zorunlu kılmasını sağlar.

Oturum açma işleminin Windows 10 çalıştıran dizüstü bilgisayarınız gibi uyumlu bir cihazdan yapılmasını gerektirme gibi daha gelişmiş özellikler için Koşullu Erişim ilkelerini de kullanabilirsiniz.

Koşullu Erişim, Microsoft 365 E3 ve E5 ile birlikte gelen Azure AD Premium P1 lisansları gerektirir.

Daha fazla bilgi için bkz. [Koşullu Erişim'e genel bakış](/azure/active-directory/conditional-access/overview).

### <a name="using-these-methods-together"></a>Bu yöntemleri birlikte kullanma

Aşağıdakileri unutmayın:

- Koşullu Erişim ilkeleri etkinse güvenlik varsayılanlarını etkinleştiremezsiniz.
- Güvenlik varsayılanları etkinse koşullu erişim ilkelerini etkinleştiremezsiniz.

Güvenlik varsayılanları etkinse, tüm yeni kullanıcılardan MFA kaydı ve Microsoft Authenticator uygulamasının kullanımı istenir. 

Bu tabloda, MFA'nın güvenlik varsayılanları ve Koşullu Erişim ilkeleriyle etkinleştirilmesinin sonuçları gösterilir.

| Yöntem | Etkin | Devre dışı | Ek kimlik doğrulama yöntemi |
|:-------|:-----|:-------|:-------|
| **Güvenlik varsayılanları**  | Koşullu Erişim ilkeleri kullanılamaz | Koşullu Erişim ilkelerini kullanabilir | Microsoft Authenticator uygulaması |
| **Koşullu Erişim ilkeleri** | Etkinse, güvenlik varsayılanlarını etkinleştiremezsiniz | Tümü devre dışı bırakılırsa, güvenlik varsayılanlarını etkinleştirebilirsiniz  | Kullanıcı MFA kaydı sırasında belirtir  |
||||

## <a name="zero-trust-identity-and-device-access-configurations"></a>Sıfır Güven kimlik ve cihaz erişimi yapılandırmaları

Sıfır Güven kimlik ve cihaz erişim ayarları ve ilkeleri, koşullu erişim, Intune ve Belirli bir erişim isteğinin verilip verilmeyeceğini ve hangi koşullar altında verilmesi gerektiğini belirleyen Azure AD Kimlik Koruması ilkeleriyle birlikte önkoşul özellikleri ve bunların ayarları önerilir. Bu belirleme, oturum açma işleminin kullanıcı hesabına, kullanılan cihaza, kullanıcının erişim için kullandığı uygulamaya, erişim isteğinin yapıldığı konuma ve istek riskinin değerlendirmesine dayanır. Bu özellik, kritik kaynaklarınıza yalnızca onaylı kullanıcıların ve cihazların erişebilmesini sağlamaya yardımcı olur.

>[!Note]
>Azure AD Kimlik Koruması, Microsoft 365 E5 dahil Azure AD Premium P2 lisansları gerektirir.
>

Kimlik ve cihaz erişim ilkeleri üç katmanda kullanılacak şekilde tanımlanır: 

- Temel koruma, uygulamalarınıza ve verilerinize erişen kimlikleriniz ve cihazlarınız için en düşük güvenlik düzeyidir.
- Hassas koruma, belirli veriler için ek güvenlik sağlar. Kimlikler ve cihazlar daha yüksek düzeyde güvenlik ve cihaz durumu gereksinimlerine tabidir.
- Yüksek oranda düzenlenmiş veya sınıflandırılmış verilere sahip ortamlar için koruma, genellikle yüksek oranda sınıflandırılmış, ticari gizli diziler içeren veya veri düzenlemelerine tabi olan küçük miktarlardaki verilere yöneliktir. Kimlikler ve cihazlar çok daha yüksek güvenlik ve cihaz durumu gereksinimlerine tabidir. 

Bu katmanlar ve bunlara karşılık gelen yapılandırmalar verileriniz, kimlikleriniz ve cihazlarınız arasında tutarlı koruma düzeyleri sağlar.

Microsoft, Microsoft Teams, Exchange Online ve SharePoint için belirli ayarlar dahil olmak üzere kuruluşunuzda Sıfır Güven kimlik ve cihaz erişim ilkelerini yapılandırmanızı ve dağıtmanızı kesinlikle önerir. Daha fazla bilgi için bkz. [kimlik ve cihaz erişim yapılandırmalarını Sıfır Güven](../security/office-365-security/microsoft-365-policies-configurations.md).

## <a name="azure-ad-identity-protection"></a>Azure AD Kimlik Koruması

Bu bölümde, bir saldırganın bir kuruluşun bulut hizmetlerine ve verilerine erişim kazanmak için kullanıcının hesap adını ve parolasını belirlediği kimlik bilgileri güvenliğinin aşılmasına karşı koruma sağlayan ilkeleri yapılandırmayı öğreneceksiniz. Azure AD Kimlik Koruması, bir saldırganın kullanıcı hesabının kimlik bilgilerini tehlikeye atmasını önlemeye yardımcı olmak için çeşitli yollar sağlar.

Azure AD Kimlik Koruması ile şunları yapabilirsiniz:

|Yeteneği|Açıklama|
|:---------|:---------|
| Kuruluşunuzun kimliklerindeki olası güvenlik açıklarını belirleme ve giderme | Azure AD, oturum açma işlemleri ve oturum açma sonrası etkinlikleri gibi anomalileri ve şüpheli etkinlikleri algılamak için makine öğrenmesini kullanır. Azure AD Identity Protection bu verileri kullanarak sorunları değerlendirmenize ve işlem yapmanıza yardımcı olacak raporlar ve uyarılar oluşturur.|
|Kuruluşunuzun kimlikleri ile ilgili şüpheli eylemleri algılama ve bunları otomatik olarak yanıtlama|Belirtilen risk düzeyine ulaşıldığında algılanan sorunlara otomatik olarak yanıt veren risk tabanlı ilkeler yapılandırabilirsiniz. Bu ilkeler, Azure AD ve Microsoft Intune tarafından sağlanan diğer Koşullu Erişim denetimlerine ek olarak erişimi otomatik olarak engelleyebilir veya parola sıfırlamaları ve sonraki oturum açma işlemleri için Azure AD Multi-Factor Authentication gerektirme gibi düzeltici eylemler gerçekleştirebilir. |
| Şüpheli olayları araştırma ve yönetim eylemleriyle çözme | Güvenlik olayı hakkındaki bilgileri kullanarak risk olaylarını araştırabilirsiniz. Araştırmaları izlemek ve parola sıfırlama gibi düzeltme eylemleri başlatmak için temel iş akışları kullanılabilir. |
|||

[Bkz. Azure AD Kimlik Koruması hakkında daha fazla bilgi](/azure/active-directory/identity-protection/overview-identity-protection).

[Azure AD Kimlik Koruması'nı etkinleştirme adımlarına](/azure/active-directory/identity-protection/howto-identity-protection-configure-risk-policies) bakın.

## <a name="admin-technical-resources-for-mfa-and-secure-sign-ins"></a>MFA ve güvenli oturum açma işlemleri için yönetici teknik kaynakları

- [Microsoft 365 için MFA](../admin/security-and-compliance/multi-factor-authentication-microsoft-365.md)
- [Microsoft 365 için kimlik dağıtma](deploy-identity-solution-overview.md)
- [Azure Academy Azure AD eğitim videoları](https://www.youtube.com/watch?v=pN8o0owHfI0&list=PL-V4YVm6AmwUFpC3rXr2i2piRQ708q_ia)
- [Azure AD Multi-Factor Authentication kayıt ilkesini yapılandırma](/azure/active-directory/identity-protection/howto-identity-protection-configure-mfa-policy)
- [Kimlik ve cihaz erişimi yapılandırmaları](../security/office-365-security/microsoft-365-policies-configurations.md)

## <a name="next-step"></a>Sonraki adım

![Kimlik modelinizi dağıtma](../media/deploy-identity-solution-overview/deploy-identity-solution-identity-infrastructure.png)

Seçtiğiniz kimlik modeline göre kimlik altyapısını dağıtmak için 4. Adımla devam edin:

- [Yalnızca bulut kimliği](cloud-only-identities.md)
- [Karma kimlik](prepare-for-directory-synchronization.md)
