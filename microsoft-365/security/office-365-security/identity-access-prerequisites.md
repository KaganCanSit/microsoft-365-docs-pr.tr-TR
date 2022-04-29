---
title: Kimlik ve cihaz erişim ilkelerini uygulamak için önkoşul çalışması - kurumsal | için Microsoft 365 Microsoft Docs
description: Bu makalede, Sıfır Güven kimlik ve cihaz erişim ilkelerini ve yapılandırmalarını kullanmak için karşılamanız gereken önkoşullar açıklanmaktadır.
ms.author: dansimp
author: dansimp
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
ms.openlocfilehash: 2c2902e7e61428d9c60423f83ed637d6d22a0570
ms.sourcegitcommit: fdd0294e6cda916392ee66f5a1d2a235fb7272f8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/29/2022
ms.locfileid: "65131250"
---
# <a name="prerequisite-work-for-implementing-zero-trust-identity-and-device-access-policies"></a>Sıfır Güven kimlik ve cihaz erişim ilkelerini uygulamak için önkoşul çalışması

Bu makalede, yöneticilerin önerilen Sıfır Güven kimlik ve cihaz erişim ilkelerini kullanmak ve Koşullu Erişim kullanmak için karşılaması gereken önkoşullar açıklanmaktadır. Ayrıca, istemci platformlarını en iyi çoklu oturum açma (SSO) deneyimi için yapılandırmak için önerilen varsayılanları da açıklar.

## <a name="prerequisites"></a>Önkoşullar

Önerilen Sıfır Güven kimlik ve cihaz erişim ilkelerini kullanmadan önce kuruluşunuzun önkoşulları karşılaması gerekir. Gereksinimler, listelenen çeşitli kimlik ve kimlik doğrulama modelleri için farklıdır:

- Yalnızca bulut
- Parola karması eşitleme (PHS) kimlik doğrulaması ile karma
- Doğrudan kimlik doğrulaması (PTA) ile karma
- Federe

Aşağıdaki tabloda, belirtilen durumlar dışında tüm kimlik modelleri için geçerli olan önkoşul özellikleri ve yapılandırmaları ayrıntılı olarak anlatılır.

|Yapılandırma|Özel durum|Lisanslama|
|---|:---:|---|
|[PHS'yi yapılandırın](/azure/active-directory/hybrid/how-to-connect-password-hash-synchronization).  Bu, sızdırılan kimlik bilgilerini algılamak ve risk tabanlı Koşullu Erişim için bunlar üzerinde işlem yapmak için etkinleştirilmelidir. **Not:** Kuruluşunuzun federasyon kimlik doğrulaması kullanıp kullanmadığına bakılmaksızın bu gereklidir.|Yalnızca bulut|Microsoft 365 E3 veya E5|
|Kullanıcıların kuruluş ağınıza bağlı kuruluş cihazlarındayken otomatik olarak oturum açması için [sorunsuz çoklu oturum açmayı etkinleştirin](/azure/active-directory/connect/active-directory-aadconnect-sso).|Yalnızca bulutta ve federasyonda|Microsoft 365 E3 veya E5|
|[Adlandırılmış konumları yapılandırın](/azure/active-directory/reports-monitoring/quickstart-configure-named-locations). Azure AD Kimlik Koruması, bir risk puanı oluşturmak için tüm kullanılabilir oturum verilerini toplar ve analiz eder. Kuruluşunuzun ağınız için genel IP aralıklarını Azure AD adlandırılmış konumlar yapılandırmasında belirtmenizi öneririz. Bu aralıklardan gelen trafiğe düşük risk puanı, kuruluş ortamı dışından gelen trafiğe ise daha yüksek bir risk puanı verilir.||Microsoft 365 E3 veya E5|
|[Tüm kullanıcıları self servis parola sıfırlama (SSPR) ve çok faktörlü kimlik doğrulaması (MFA) için kaydedin](/azure/active-directory/authentication/concept-registration-mfa-sspr-converged). Kullanıcıları önceden Azure AD Çok Faktörlü Kimlik Doğrulamasına kaydetmenizi öneririz. Azure AD Kimlik Koruması, ek güvenlik doğrulaması gerçekleştirmek için Azure AD Çok Faktörlü Kimlik Doğrulamasını kullanır. Ayrıca, en iyi oturum açma deneyimi için kullanıcıların [cihazlarına Microsoft Authenticator uygulamasını](/azure/active-directory/user-help/microsoft-authenticator-app-how-to) ve Microsoft Şirket Portalı uygulamasını yüklemelerini öneririz. Bunlar her platform için uygulama mağazasından yüklenebilir.||Microsoft 365 E3 veya E5|
|[Etki alanına katılmış Windows bilgisayarların otomatik cihaz kaydını etkinleştirin](/azure/active-directory/active-directory-conditional-access-automatic-device-registration-setup). Koşullu Erişim, uygulamalara bağlanan cihazların etki alanına katılmış veya uyumlu olduğundan emin olur. Bunu Windows bilgisayarlarda desteklemek için cihazın Azure AD'a kayıtlı olması gerekir.  Bu makalede otomatik cihaz kaydının nasıl yapılandırılacağı açıklanır.|Yalnızca bulut|Microsoft 365 E3 veya E5|
|**Destek ekibinizi hazırlayın**. MFA'yı tamamlayamayan kullanıcılar için bir planınız var. Bu, bunları bir ilke dışlama grubuna eklemek veya bunlar için yeni MFA bilgileri kaydetmek olabilir. Bu güvenlik açısından hassas değişikliklerden birini yapmadan önce, isteği gerçek kullanıcının gerçekleştirdiğinden emin olmanız gerekir. Kullanıcıların yöneticilerinin onay konusunda yardımcı olmasını gerektirmek etkili bir adımdır.||Microsoft 365 E3 veya E5|
|[Şirket içi AD'ye parola geri yazmayı yapılandırın](/azure/active-directory/active-directory-passwords-getting-started). Parola geri yazma, Azure AD yüksek riskli hesap güvenliği ihlalleri algılandığında kullanıcıların şirket içi parolalarını değiştirmelerini gerektirmesini sağlar. Azure AD Bağlan kullanarak bu özelliği iki yoldan biriyle etkinleştirebilirsiniz: Azure AD Bağlan kurulumun isteğe bağlı özellikler ekranında **Parola Geri Yazma'yı** etkinleştirin veya Windows PowerShell aracılığıyla etkinleştirin.|Yalnızca bulut|Microsoft 365 E3 veya E5|
|[Azure AD parola korumasını yapılandırın](/azure/active-directory/authentication/concept-password-ban-bad). Azure AD Parola Koruması bilinen zayıf parolaları ve bunların çeşitlemelerini algılar ve engeller ve ayrıca kuruluşunuza özgü ek zayıf terimleri engelleyebilir. Varsayılan genel yasaklanmış parola listeleri, Azure AD kiracıdaki tüm kullanıcılara otomatik olarak uygulanır. Özel yasaklanmış parola listesinde ek girdiler tanımlayabilirsiniz. Kullanıcılar parolalarını değiştirdiğinde veya sıfırladığında, bu yasaklanmış parola listeleri güçlü parolaların kullanımını zorunlu kılmak için denetlenir.||Microsoft 365 E3 veya E5|
|[Azure Active Directory Kimlik Koruması'nı etkinleştirin](/azure/active-directory/identity-protection/overview-identity-protection). Azure AD Kimlik Koruması, kuruluşunuzun kimliklerini etkileyen olası güvenlik açıklarını algılamanıza ve otomatik düzeltme ilkesini düşük, orta ve yüksek oturum açma riski ile kullanıcı riskine yapılandırmanıza olanak tanır.||E5 Güvenliği eklentisiyle Microsoft 365 E5 veya Microsoft 365 E3|
|[Exchange Online ve Skype Kurumsal](/Exchange/clients-and-mobile-in-exchange-online/enable-or-disable-modern-authentication-in-exchange-online) [Online](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx) için **modern kimlik doğrulamasını etkinleştirin**. Modern kimlik doğrulaması, MFA'nın kullanılması için bir önkoşuldur. Modern kimlik doğrulaması Office 2016 ve 2019 istemcileri, SharePoint ve OneDrive İş için varsayılan olarak etkindir.||Microsoft 365 E3 veya E5|
|Azure AD için [sürekli erişim değerlendirmesini etkinleştirin](microsoft-365-continuous-access-evaluation.md). Sürekli erişim değerlendirmesi etkin kullanıcı oturumlarını proaktif olarak sonlandırır ve kiracı ilkesi değişikliklerini neredeyse gerçek zamanlı olarak uygular.||Microsoft 365 E3 veya E5|

## <a name="recommended-client-configurations"></a>Önerilen istemci yapılandırmaları

Bu bölümde, kullanıcılarınıza en iyi SSO deneyimini ve Koşullu Erişim için teknik önkoşulları sağlamanızı önerdiğimiz varsayılan platform istemci yapılandırmaları açıklanmaktadır.

### <a name="windows-devices"></a>cihazları Windows

Azure hem şirket içi hem de Azure AD için mümkün olan en sorunsuz SSO deneyimini sağlamak üzere tasarlandığından Windows 11 veya Windows 10 (sürüm 2004 veya üzeri) öneririz. İş veya okul tarafından verilen cihazlar Azure AD doğrudan katılmak üzere yapılandırılmalıdır veya kuruluş şirket içi AD etki alanına katılmayı kullanıyorsa, bu cihazlar [Azure AD otomatik ve sessiz bir şekilde kaydedilecek şekilde yapılandırılmalıdır](/azure/active-directory/active-directory-conditional-access-automatic-device-registration-setup).

KCG Windows cihazlarda kullanıcılar **İş veya okul hesabı ekle'yi** kullanabilir. Windows 11 veya Windows 10 cihazlarda Google Chrome tarayıcısı kullanıcılarının, Microsoft Edge kullanıcılarla aynı sorunsuz oturum açma deneyimini elde etmek için [bir uzantı yüklemeleri](https://chrome.google.com/webstore/detail/windows-10-accounts/ppnbnpeolgkicgegkbkbjmhlideopiji?utm_source=chrome-app-launcher-info-dialog) gerektiğini unutmayın. Ayrıca, kuruluşunuzun etki alanına katılmış Windows 8 veya 8.1 cihazları varsa, Windows 10 olmayan bilgisayarlar için Microsoft Workplace Join'i yükleyebilirsiniz. Cihazları Azure AD [kaydetmek için paketi indirin](https://www.microsoft.com/download/details.aspx?id=53554).

### <a name="ios-devices"></a>iOS cihazları

Koşullu Erişim veya MFA ilkelerini dağıtmadan önce [Microsoft Authenticator uygulamasını](/azure/multi-factor-authentication/end-user/microsoft-authenticator-app-how-to) kullanıcı cihazlarına yüklemenizi öneririz. Kullanıcılardan iş veya okul hesabı ekleyerek cihazlarını Azure AD kaydetmeleri istendiğinde veya cihazlarını yönetime kaydetmek için Intune şirket portalı uygulamasını yüklediklerinde uygulama en azından yüklenmelidir. Bu, yapılandırılmış Koşullu Erişim ilkesine bağlıdır.

### <a name="android-devices"></a>Android cihazlar

Koşullu Erişim ilkeleri dağıtılmadan önce veya belirli kimlik doğrulama girişimleri sırasında gerektiğinde kullanıcıların [Intune Şirket Portalı uygulamasını](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal&hl=en) ve [Microsoft Authenticator uygulamasını](/azure/multi-factor-authentication/end-user/microsoft-authenticator-app-how-to) yüklemelerini öneririz. Uygulama yükledikten sonra kullanıcılardan Azure AD'a kaydolmaları veya cihazlarını Intune kaydetmeleri istenebilir. Bu, yapılandırılmış Koşullu Erişim ilkesine bağlıdır.

Ayrıca, kuruluşa ait cihazların posta hesaplarına izin vermek, Intune MDM ilkesi tarafından yönetilmeye ve korunmaya izin vermek için Android for Work veya Samsung Knox'u destekleyen OEM'lerde ve sürümlerde standartlaştırılmalarını öneririz.

### <a name="recommended-email-clients"></a>Önerilen e-posta istemcileri

Aşağıdaki e-posta istemcileri modern kimlik doğrulamasını ve Koşullu Erişimi destekler.

|Ortam|İstemci|Sürüm/Notlar|
|---|---|---|
|**Windows**|Outlook|2019, 2016, 2013 <p> [Modern kimlik doğrulamasını etkinleştirme](../../admin/security-and-compliance/enable-modern-authentication.md) <p> [Gerekli güncelleştirmeler](https://support.office.com/article/Outlook-Updates-472c2322-23a4-4014-8f02-bbc09ad62213)|
|**iOS**|iOS için Outlook|[Son](https://itunes.apple.com/us/app/microsoft-outlook-email-and-calendar/id951937596?mt=8)|
|**Android**|Android için Outlook|[Son](https://play.google.com/store/apps/details?id=com.microsoft.office.outlook&hl=en)|
|**macOS**|Outlook|2019 ve 2016|
|**Linux**|Desteklenmiyor||

### <a name="recommended-client-platforms-when-securing-documents"></a>Belgelerin güvenliğini sağlarken önerilen istemci platformları

Güvenli belge ilkesi uygulandığında aşağıdaki istemciler önerilir.

|Ortam|Word/Excel/PowerPoint|OneNote|OneDrive Uygulaması|SharePoint Uygulaması|[OneDrive eşitleme istemcisi](/onedrive/enable-conditional-access)|
|---|---|---|---|---|---|
|Windows 11 veya Windows 10|Destekleniyor|Destekleniyor|Yok|Yok|Destekleniyor|
|Windows 8.1|Destekleniyor|Destekleniyor|Yok|Yok|Destekleniyor|
|Android|Destekleniyor|Destekleniyor|Destekleniyor|Destekleniyor|Yok|
|iOS|Destekleniyor|Destekleniyor|Destekleniyor|Destekleniyor|Yok|
|macOS|Destekleniyor|Destekleniyor|Yok|Yok|Desteklenmiyor|
|Linux|Desteklenmiyor|Desteklenmiyor|Desteklenmiyor|Desteklenmiyor|Desteklenmiyor|

### <a name="microsoft-365-client-support"></a>İstemci desteğini Microsoft 365

Microsoft 365'da istemci desteği hakkında daha fazla bilgi için aşağıdaki makalelere bakın:

- [Microsoft 365 İstemci Uygulaması Desteği - Koşullu Erişim](../../enterprise/microsoft-365-client-support-conditional-access.md)
- [Microsoft 365 İstemci Uygulaması Desteği - Çok faktörlü kimlik doğrulaması](../../enterprise/microsoft-365-client-support-multi-factor-authentication.md)

## <a name="protecting-administrator-accounts"></a>Yönetici hesaplarını koruma

Microsoft 365 E3 veya E5 için ya da ayrı Azure AD Premium P1 veya P2 lisanslarıyla, el ile oluşturulmuş koşullu erişim ilkesine sahip yönetici hesapları için MFA gerektirebilirsiniz. Ayrıntılar için bkz [. Koşullu Erişim: Yöneticiler için MFA gerektirme](/azure/active-directory/conditional-access/howto-conditional-access-policy-admin-mfa) .

Koşullu Erişimi desteklemeyen Microsoft 365 veya Office 365 sürümlerinde, tüm hesaplar için MFA gerektirmek üzere [güvenlik varsayılanlarını](/azure/active-directory/fundamentals/concept-fundamentals-security-defaults) etkinleştirebilirsiniz.

Bazı ek öneriler şunlardır:

- Kalıcı yönetim hesaplarının sayısını azaltmak için [Azure AD Privileged Identity Management](/azure/active-directory/privileged-identity-management/pim-getting-started) kullanın.
- Kuruluşunuzu hassas verilere veya kritik yapılandırma ayarlarına erişimi olan mevcut ayrıcalıklı yönetici hesaplarını kullanabilecek ihlallere karşı korumak için [ayrıcalıklı erişim yönetimini kullanın](../../compliance/privileged-access-management-overview.md).
- *Yalnızca yönetim için* [yönetici rolleri Microsoft 365](../../admin/add-users/about-admin-roles.md) atanan ayrı hesaplar oluşturun ve kullanın. Yöneticilerin düzenli yönetim dışı kullanım için kendi kullanıcı hesapları olmalıdır ve yalnızca rol veya iş işleviyle ilişkili bir görevi tamamlamak için gerektiğinde bir yönetim hesabı kullanmalıdır.
- Azure AD'da ayrıcalıklı hesapların güvenliğini sağlamak için [en iyi yöntemleri](/azure/active-directory/admin-roles-best-practices) izleyin.

## <a name="next-step"></a>Sonraki adım

[![2. Adım: Ortak Sıfır Güven kimliğini yapılandırın ve Koşullu Erişim ilkelerine erişin.](../../media/microsoft-365-policies-configurations/identity-device-access-steps-next-step-2.png#lightbox)](identity-access-policies.md)

[Ortak Sıfır Güven kimlik ve cihaz erişim ilkelerini yapılandırma](identity-access-policies.md)
