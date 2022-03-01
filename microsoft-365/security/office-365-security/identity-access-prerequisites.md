---
title: Kimlik ve cihaz erişim ilkelerinin uygulanması için önkoşullar çalışması - Microsoft 365 erişimi için | Microsoft Docs
description: Bu makalede, Sıfır Güven kimliği ve cihaz erişimi ilkeleri ile yapılandırmalarını kullanmak için karşılamanız gereken önkoşullar açıklanmıştır.
ms.author: josephd
author: JoeDavies-MSFT
manager: dansimp
ms.prod: m365-security
ms.topic: article
audience: Admin
f1.keywords:
- NOCSH
ms.reviewer: martincoetzer
ms.custom:
- it-pro
- goldenconfig
ms.collection:
- M365-identity-device-management
- M365-security-compliance
- m365solution-identitydevice
- m365solution-scenario
ms.technology: mdo
ms.openlocfilehash: ba9694be615f0c669ed0b9c319909551ccf02315
ms.sourcegitcommit: aac7e002ec6e10a41baa2d0bd38614b0ed471a70
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/27/2022
ms.locfileid: "63009991"
---
# <a name="prerequisite-work-for-implementing-zero-trust-identity-and-device-access-policies"></a>Sıfır Güven kimliği ve cihaz erişim ilkelerinin uygulanması için önkoşul çalışma

Bu makalede yöneticilerin önerilen Sıfır Güven kimliği ve cihaz erişimi ilkelerini kullanmak ve Koşullu Erişim'i kullanmak için karşılamaları gereken önkoşullar açıklanmıştır. Ayrıca, en iyi çoklu oturum açma (SSO) deneyimi için istemci platformlarını yapılandırmak için önerilen varsayılanlar da ele almaktadır.

## <a name="prerequisites"></a>Önkoşullar

Önerilen Sıfır Güven kimliği ve cihaz erişimi ilkelerini kullanmadan önce, önkoşulları karşılaması gerekir. Gereksinimler, listelenen çeşitli kimlik doğrulama modellerinde farklıdır:

- Yalnızca bulut
- Karma parola eşitlemesi (PHS) kimlik doğrulamasıyla karma
- Geçişli kimlik doğrulaması (PTA) ile karma
- Federasyon

Aşağıdaki tabloda, not edildi dışındaki tüm kimlik modellerine uygulanacak önkoşul özellikleri ve bunların yapılandırması ayrıntılarıyla açıklandı.

|Yapılandırma|Özel Durumlar|Lisanslama|
|---|:---:|---|
|[PHS'yi yapılandırma](/azure/active-directory/hybrid/how-to-connect-password-hash-synchronization).  Sızdırılan kimlik bilgilerini algılamak ve risk tabanlı Koşullu Erişim için bu kimlik bilgilerini algılayan bu özelliğin etkinleştirilmesi gerekir. **Not:** Bu, kurumda federasyon kimlik doğrulaması kullanıp kullanmamasa da gereklidir.|Yalnızca bulut|Microsoft 365 E3 E5|
|[Kullanıcıların kuruluş ağınıza bağlı kuruluş](/azure/active-directory/connect/active-directory-aadconnect-sso) cihazlarında yer alan kullanıcılara otomatik olarak oturum açmaları için sorunsuz çoklu oturum açma özelliği etkinleştirin.|Yalnızca bulut ve federasyon|Microsoft 365 E3 E5|
|[Adlandırılmış konumları yapılandırma](/azure/active-directory/reports-monitoring/quickstart-configure-named-locations). Azure AD Identity Protection, bir risk puanı oluşturmak için kullanılabilir tüm oturum verilerini toplar ve analiz eder. Azure AD adlı konumlar yapılandırmasında, ağınız için kuruma yönelik genel IP aralıklarını belirtmenizi öneririz. Bu aralıklardan gelen trafiğe daha düşük risk puanı verilir ve kuruluş ortamının dışından gelen trafik daha yüksek risk puanı verilir.||Microsoft 365 E3 E5|
|[Tüm kullanıcıları self servis parola sıfırlama (SSPR) ve Multifactor Authentication (MFA) için kaydettirin](/azure/active-directory/authentication/concept-registration-mfa-sspr-converged). Kullanıcıları azure ad Multifactor Authentication için daha önce kaydetmenizi öneririz. Azure AD Kimlik Koruması, ek güvenlik doğrulaması gerçekleştirmek için Azure AD Multifactor Authentication'ın kullanır. Buna ek olarak, en iyi oturum açma deneyimi için kullanıcıların [Microsoft Authenticator Microsoft Şirket Portalı](/azure/active-directory/user-help/microsoft-authenticator-app-how-to) uygulamasını cihazlarına yüklemelerini öneririz. Bunlar her platforma uygun uygulama mağazasından yüklenir.||Microsoft 365 E3 E5|
|[Etki alanına katılmış bilgisayarlarda otomatik cihaz Windows etkinleştirin](/azure/active-directory/active-directory-conditional-access-automatic-device-registration-setup). Koşullu Erişim, uygulamalara bağlanan cihazların etki alanına katılmış veya uyumlu olduğundan emin olur. Bu hizmeti diğer bilgisayarlarda Windows için cihazın Azure AD'ye kaydedilmiş olması gerekir.  Bu makalede, otomatik cihaz kaydının nasıl yapılandırıldığından emin olun.|Yalnızca bulut|Microsoft 365 E3 E5|
|**Destek ekibinizi hazırlayın**. MFA'da tamamlayamaz kullanıcılar için bir plan hazır bulundurabilirsiniz. Bu, dışlama grubunu bir ilke grubuna eklemek veya onlar için yeni MFA bilgilerini kaydetmek olabilir. Bu güvenlik duyarlı değişikliklerden herhangi birini yapmadan önce, asıl kullanıcının isteği tamam olduğundan emin olmak gerekir. Onay için kullanıcı yöneticilerinin yardımcı olması etkili bir adımdır.||Microsoft 365 E3 E5|
|[Şirket içi AD'ye parola geri yazma ayarlarını yapılandırma](/azure/active-directory/active-directory-passwords-getting-started). Parola geri yazma, Azure AD'nin yüksek riskli bir hesap güvenliği algılandığında kullanıcıların şirket içi parolalarını değiştirmesini gerektirmesini sağlar. Azure AD Bağlan'i kullanarak bu özelliği iki şekilden birini kullanarak etkinleştirebilirsiniz: Azure AD Bağlan kurulumunun isteğe bağlı özellikler ekranında Parola Geri Yazma özelliğini etkinleştirin veya parolayı Windows PowerShell.|Yalnızca bulut|Microsoft 365 E3 E5|
|[Azure AD parola korumasını yapılandırma](/azure/active-directory/authentication/concept-password-ban-bad). Azure AD Parola Koruması bilinen zayıf parolaları ve değişkenlerini algılar ve engeller; ayrıca, organizasyonuma özgü ek zayıf terimleri de engelleyebilir. Varsayılan genel yasaklanmış parola listeleri, Bir Azure AD kiracısı'nın tüm kullanıcılarına otomatik olarak uygulanır. Özel bir yasaklanan parola listesinde ek girişler tanımlayabilirsiniz. Kullanıcılar parolalarını değiştirse veya sıfırlasa, güçlü parolaların kullanımını zorunlu yapmak için bu yasaklanmış parola listeleri denetlenir.||Microsoft 365 E3 E5|
|[Kimlik Azure Active Directory'yi etkinleştirin](/azure/active-directory/identity-protection/overview-identity-protection). Azure AD Identity Protection, kuruluş kimliklerini etkileyen olası güvenlik açıklarını algılamanıza ve düşük, orta ve yüksek oturum açma riski ile kullanıcı riski olan otomatik bir düzeltme ilkesi yapılandırmanıza olanak sağlar.||Microsoft 365 E5 E5 Microsoft 365 E3 ile iş veya güvenlik ekleme|
|**Exchange Online** Online [için ve](/Exchange/clients-and-mobile-in-exchange-online/enable-or-disable-modern-authentication-in-exchange-online) [Skype Kurumsal'da modern kimlik doğrulamayı etkinleştirin](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx). Modern kimlik doğrulaması, MFA'nın kullanımı için önkoşuldur. Modern kimlik doğrulama Office 2016 ve 2019 istemcileri, posta SharePoint için varsayılan OneDrive İş.||Microsoft 365 E3 E5|
|Azure AD [için sürekli erişim](microsoft-365-continuous-access-evaluation.md) değerlendirmesini etkinleştirin. Sürekli erişim değerlendirme, etkin kullanıcı oturumlarını önceden sonlandırılır ve gerçek zamanlı olarak kiracı ilkesi değişikliklerini zorlar.||Microsoft 365 E3 E5|
|

## <a name="recommended-client-configurations"></a>Önerilen istemci yapılandırmaları

Bu bölümde, kullanıcılarınıza en iyi SSO deneyimini ve Koşullu Erişim için teknik önkoşulları sağlamanızı öneririz olan varsayılan platform istemci yapılandırmaları açık bulunmaktadır.

### <a name="windows-devices"></a>Windows cihazları

Azure hem Windows hem de Azure AD Windows 10 en rahat SSO deneyimini sağlamak üzere tasarlayali olduğu için Azure'un 11 ya da Windows 10 sürümü (sürüm 2004 veya sonrası) sürümünü öneririz. İş veya okul tarafından verilen cihazların Azure AD'ye doğrudan katılacağı şekilde ya da kuruluşun şirket içi AD etki alanı katılmasını kullanıyorsa, bu cihazların otomatik olarak yapılandırılması ve [Azure AD'ye](/azure/active-directory/active-directory-conditional-access-automatic-device-registration-setup) sessiz kaydolması gerekir.

BYOD cihaz Windows, kullanıcılar İş veya **okul hesabı ekle'yi kullanabilir**. Windows 11 veya Windows 10 cihazlarında Google Chrome tarayıcı kullanıcılarının, kullanıcılarının aynı sorunsuz oturum açma deneyimini elde etmek için bir [](https://chrome.google.com/webstore/detail/windows-10-accounts/ppnbnpeolgkicgegkbkbjmhlideopiji?utm_source=chrome-app-launcher-info-dialog) uzantı yüklemeleri Microsoft Edge unutmayın. Ayrıca, kurumda etki alanına katılmış Windows 8 veya 8.1 cihazları varsa, microsoft çalışma alanına katılmayan bilgisayarlar için Microsoft workplace Windows 10 yükleyebilirsiniz. [Cihazları Azure AD'ye kaydetmek](https://www.microsoft.com/download/details.aspx?id=53554) için paketi indirin.

### <a name="ios-devices"></a>iOS cihazları

Koşullu Erişim veya [Microsoft Authenticator](/azure/multi-factor-authentication/end-user/microsoft-authenticator-app-how-to) MFA ilkelerini dağıtmadan önce Microsoft Authenticator uygulaması kullanıcı cihazlarına yüklemenizi öneririz. En azından, kullanıcıların cihazlarını iş veya okul hesabı ekleyerek Azure AD'ye kaydetmeleri istenmiş veya Intune şirket portalı uygulamasını yükerek cihazı yönetime kaydetmeleri istenmiş olduğunda uygulamanın yüklenmiş olması gerekir. Bu, yapılandırılmış Koşullu Erişim ilkesine bağlıdır.

### <a name="android-devices"></a>Android cihazları

Koşullu Erişim ilkeleri [dağıtıldıktan Intune Şirket Portalı bazı](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal&hl=en) kimlik doğrulama [girişimlerinde gerektiğinde](/azure/multi-factor-authentication/end-user/microsoft-authenticator-app-how-to) kullanıcıların Intune Şirket Portalı'i ve Microsoft Authenticator uygulamasını yüklemelerini öneririz. Uygulama yüklemesi sonrasında, kullanıcıların Azure AD'ye kaydolmaları veya cihazlarını Intune'a kaydetmeleri istenebilirsiniz. Bu, yapılandırılmış Koşullu Erişim ilkesine bağlıdır.

Ayrıca, kuruluşa ait cihazların, posta hesaplarının Intune MDM ilkesi tarafından yönetillerine ve korunmasına izin vermek üzere İş veya Samsung Knox için Android'i destekleyen OEM'lerde ve sürümlerinde standart hale getirildiklerini öneririz.

### <a name="recommended-email-clients"></a>Önerilen e-posta istemcileri

Aşağıdaki e-posta istemcileri modern kimlik doğrulamayı ve Koşullu Erişimi destekler.

|Ortam|İstemci|Sürüm/Notlar|
|---|---|---|
|**Windows**|Outlook|2019, 2016, 2013 <p> [Modern kimlik doğrulamayı etkinleştirme](../../admin/security-and-compliance/enable-modern-authentication.md) <p> [Gerekli güncelleştirmeler](https://support.office.com/article/Outlook-Updates-472c2322-23a4-4014-8f02-bbc09ad62213)|
|**iOS**|iOS Outlook için yeni bir ifade|[En yeni](https://itunes.apple.com/us/app/microsoft-outlook-email-and-calendar/id951937596?mt=8)|
|**Android**|Android için Outlook'i|[En yeni](https://play.google.com/store/apps/details?id=com.microsoft.office.outlook&hl=en)|
|**macOS**|Outlook|2019 ve 2016|
|**Linux**|Desteklenmiyor||
|

### <a name="recommended-client-platforms-when-securing-documents"></a>Belgelerin güvenliğini sağlarken önerilen istemci platformları

Güvenli belgeler ilkesi uygulandığında aşağıdaki istemcilerin kullanılması önerilir.

|Ortam|Word/Excel/PowerPoint|OneNote|OneDrive Uygulaması|SharePoint Uygulaması|[OneDrive eşitleme istemcisi](/onedrive/enable-conditional-access)|
|---|---|---|---|---|---|
|Windows 11 veya Windows 10|Destekleniyor|Destekleniyor|Yok|Yok|Destekleniyor|
|Windows 8.1|Destekleniyor|Destekleniyor|Yok|Yok|Destekleniyor|
|Android|Destekleniyor|Destekleniyor|Destekleniyor|Destekleniyor|Yok|
|iOS|Destekleniyor|Destekleniyor|Destekleniyor|Destekleniyor|Yok|
|macOS|Destekleniyor|Destekleniyor|Yok|Yok|Desteklenmiyor|
|Linux|Desteklenmiyor|Desteklenmiyor|Desteklenmiyor|Desteklenmiyor|Desteklenmiyor|
|

### <a name="microsoft-365-client-support"></a>Microsoft 365 desteği

Destek hizmetleriyle ilgili müşteri Microsoft 365 için aşağıdaki makalelere bakın:

- [Microsoft 365 Uygulaması Desteği - Koşullu Erişim](../../enterprise/microsoft-365-client-support-conditional-access.md)
- [Microsoft 365 İstemci Uygulaması Desteği - Çok faktörlü kimlik doğrulaması](../../enterprise/microsoft-365-client-support-multi-factor-authentication.md)

## <a name="protecting-administrator-accounts"></a>Yönetici hesaplarını koruma

El Microsoft 365 E3 E5 veya ayrı Azure AD Premium P1 P2 lisansları için, el ile oluşturulmuş Koşullu Erişim ilkesi olan yönetici hesapları için MFA'ya gerektirebilirsiniz. Ayrıntılar [için bkz. Koşullu Erişim: Yöneticiler için MFA](/azure/active-directory/conditional-access/howto-conditional-access-policy-admin-mfa) gerektirme.

Koşullu Erişim Microsoft 365 veya Office 365 sürümleri için, tüm hesaplarda MFA gerektiren güvenlik varsayılanlarını etkinleştirebilirsiniz.[](/azure/active-directory/fundamentals/concept-fundamentals-security-defaults)

Bazı ek önerilerimiz var:

- Kalıcı [yönetim Privileged Identity Management](/azure/active-directory/privileged-identity-management/pim-getting-started) sayısını azaltmak için Azure AD Privileged Identity Management yönetim hesaplarını kullanın.
- [Kurumlarınızı hassas verilere ayakta](../../compliance/privileged-access-management-overview.md) erişim veya kritik yapılandırma ayarlarına erişimle birlikte, mevcut ayrıcalıklı yönetici hesaplarının kullanamalarına karşı korumak için ayrıcalıklı erişim yönetimini kullanın.
- Yalnızca yönetim için yönetici rollerine atanan [Microsoft 365 hesapları oluşturun ve](../../admin/add-users/about-admin-roles.md) *kullanın*. Yöneticilerin normal yönetim dışı kullanım için kendi kullanıcı hesapları olması ve yalnızca rolleriyle veya iş işlevleriyle ilişkilendirilmiş bir görevi tamamlamak için gerekli olması gerektiğinde yönetim hesabı kullanmaları gerekir.
- Azure [AD'de](/azure/active-directory/admin-roles-best-practices) ayrıcalıklı hesapların güvenliğini sağlamak için en iyi yöntemleri izleyin.

## <a name="next-step"></a>Sonraki adım

[![2. Adım: Ortak Sıfır Güven kimliğini yapılandırma ve Koşullu Erişim ilkelerine erişme.](../../media/microsoft-365-policies-configurations/identity-device-access-steps-next-step-2.png)](identity-access-policies.md)

[Ortak Sıfır Güven kimliğini ve cihaz erişim ilkelerini yapılandırma](identity-access-policies.md)