---
title: Kullanıcılar için çok faktörlü kimlik doğrulamasını ayarlama
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: high
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
- AdminTemplateSet
- admindeeplinkMAC
- adminvideo
- business_assist
search.appverid:
- BCS160
- MET150
- MOE150
- BEA160
- GEA150
ms.assetid: 8f0454b2-f51a-4d9c-bcde-2c48e41621c6
description: Çok faktörlü kimlik doğrulamasını ayarlamayı öğrenin.
monikerRange: o365-worldwide
ms.openlocfilehash: 1279220ceb8de5c5fdb4361a258e2c2bfc1f7061
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/12/2022
ms.locfileid: "63026637"
---
# <a name="set-up-multifactor-authentication"></a>Çok faktörlü kimlik doğrulamasını ayarlama

Çok faktörlü kimlik doğrulaması, sizin ve çalışanlarının işlerinizi güvenlik altına almanın en kolay yollarından biri Microsoft 365 sağlamak için birden fazla yol sağlamanız gerektiğini belirtir. Çok faktörlü kimlik [doğrulamasını (MFA)](multi-factor-authentication-microsoft-365.md) anlamanıza ve Microsoft 365'daki desteğine bağlı olarak, şimdi bunu ayarlamanın ve kuruluşa açmanın zamanı geldi. 

> [!IMPORTANT]
> 21 Ekim 2019'dan sonra aboneliğinizi veya deneme sürümü satın aldıysanız ve oturum a giriş sırasında MFA istenirse [,](/azure/active-directory/fundamentals/concept-fundamentals-security-defaults) aboneliğiniz için güvenlik varsayılanları otomatik olarak etkinleştirilmiştir.

> [!TIP]
> Bu konudaki adımlarda yardıma ihtiyacınız varsa, [Microsoft küçük işletme uzmanıyla çalışmayı göz önünde bulundurabilirsiniz](https://go.microsoft.com/fwlink/?linkid=2186871). İş Yardımı ile, işe alımtan günlük kullanıma kadar işlerinizi büyüttükçe siz ve çalışanlarınız küçük işletme uzmanlarına 24 saat erişim elde ediyor.

## <a name="watch-turn-on-multifactor-authentication"></a>İzle: Çok faktörlü kimlik doğrulamasını açma

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE2MuO3?autoplay=false]

1. Microsoft 365 yönetim merkezi gidin<a href="https://admin.microsoft.com/ " target="_blank">https://admin.microsoft.com</a>.
1. Hepsini **Göster'i** seçin ve sonra yönetim **Azure Active Directory seçin**.
1. Varsayılan **Azure Active Directory**, **Özellikler**, **Güvenliği Yönet'i seçin**.
1. Güvenlik **varsayılanlarını etkinleştir'in altında** **Evet'i ve** ardından Kaydet'i **seçin**.

## <a name="before-you-begin"></a>Başlamadan önce

- MFA'nın yönetimi için Genel yönetici olmak gerekir. Daha fazla bilgi için bkz. [Yönetici rolleri hakkında](../add-users/about-admin-roles.md).
- Kullanıcı başına eski MFA'sı açıksa, Kullanıcı başına [eski MFA'yi kapatın](#turn-off-legacy-per-user-mfa).
- Windows cihazlarında Office 2013 istemcileri varsa, [Office 2013 istemcileri için Modern Kimlik Doğrulama'ya sahip olun](./enable-modern-authentication.md).
- Gelişmiş: Active Directory Federasyon Hizmetleri (AD FS) ile üçüncü taraf dizin hizmetleriniz varsa, Azure MFA Sunucusu'na ayarlayın. Daha [fazla bilgi için Azure AD Çok Faktörlü Kimlik Doğrulaması ve üçüncü taraf VPN çözümleriyle gelişmiş](/azure/active-directory/authentication/howto-mfaserver-nps-vpn) senaryolara bakın.

### <a name="turn-off-legacy-per-user-mfa"></a>Kullanıcı başına eski MFA'yi kapatma

Kullanıcı başına MFA'nın daha önce etkinleştirilmesi, Güvenlik varsayılanlarını etkinleştirmeden önce kapatmanız gerekir.

1. Gezinti Microsoft 365 yönetim merkezi Gezinti'de Kullanıcılar Etkin **Kullanıcılar'ı** \> **seçin**.
1. Etkin kullanıcılar **sayfasında** **Multi-factor authentication'ı seçin**.
1. Çok faktörlü kimlik doğrulaması sayfasında, her bir kullanıcıyı seçin ve Multi-Factor Authentication durumunu Devre Dışı olarak **ayarlayın**.

## <a name="turn-security-defaults-on-or-off"></a>Güvenlik varsayılanlarını açma veya kapatma

Çoğu kuruluş için, güvenlik varsayılanları iyi düzeyde ek oturum açma güvenliği sağlar. Daha fazla bilgi için bkz. [Güvenlik varsayılanları nedir?](/azure/active-directory/fundamentals/concept-fundamentals-security-defaults)

Aboneliğiniz yeniyse Güvenlik varsayılanları sizin için otomatik olarak zaten açık olabilir.

Azure portalında yer alan kullanıcı (Azure AD) için Özellikler bölmesinde Azure Active Directory varsayılanları etkinleştirebilirsiniz veya devre dışı bırakabilirsiniz.

1. Genel yönetici kimlik [Microsoft 365 yönetim merkezi](https://admin.microsoft.com) oturum açma.
2. Sol gezintide, Her Şeyi **Göster'i seçin** ve Yönetim **merkezleri'nin altında** **Geri Azure Active Directory**.
3. Yönetim merkezinde **Azure Active Directory Özellikler'i** **Azure Active Directory** \> **seçin**.
4. Sayfanın alt kısmında **Güvenlik varsayılanlarını yönet**’i seçin.
5. Güvenlik **varsayılanlarını** etkinleştirmek için Evet'i veya **güvenlik varsayılanlarını** devre dışı bırakmak için Hayır'ı seçin ve sonra da Kaydet'i **seçin**.

Temel Koşullu Erişim [ilkelerini kullanıyorsanız](/azure/active-directory/conditional-access/concept-baseline-protection), güvenlik varsayılanlarını kullanmadan önce bunları kapatmanız istenir.

1. Koşullu Erişim [- İlkeler sayfasına gidin](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ConditionalAccessBlade/Policies).
2. Geçerli temel ilkeden her birini seçin **ve** İlkeyi **etkinleştir'i Kapalı** olarak **ayarlayın**.
3. Özellikler - [Azure Active Directory sayfasına gidin](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/Properties).
4. Sayfanın alt kısmında **Güvenlik varsayılanlarını yönet**’i seçin.
5. Güvenlik **varsayılanlarını** etkinleştirmek için Evet'i, **güvenlik varsayılanlarını** devre dışı bırakmak için Hayır'ı ve ardından Kaydet'i **seçin**.

## <a name="use-conditional-access-policies"></a>Koşullu Erişim ilkelerini kullanma

Kuruma daha ayrıntılı oturum açma güvenliği  gerekirse, Koşullu Erişim ilkeleri size daha fazla denetim teklif ediyor olabilir. Koşullu Erişim, oturum açma olaylarına tepki veren ilkeler oluşturmanıza ve bu ilkeler tanımlamanıza olanak sağlar ve kullanıcıya uygulama veya hizmete erişim izni verilmeden önce ek eylemler ister.

> [!IMPORTANT]
> Koşullu Erişim ilkelerini etkinleştirmeden önce kullanıcı başına MFA ve Güvenlik varsayılanlarını kapatın.

Koşullu Erişim, satın alınan müşteriler veya Azure AD Premium P1 gibi bu lisansı içeren lisanslar (örneğin, Microsoft 365 İş Ekstra) Microsoft 365 E3. Daha fazla bilgi için bkz [. Koşullu Erişim ilkesi oluşturma](/azure/active-directory/authentication/tutorial-enable-azure-mfa).

Risk tabanlı koşullu erişim, Azure AD Premium P2 lisansı aracılığıyla veya bu lisansı içeren lisanslar (örneğin, Microsoft 365 E5. Daha fazla bilgi için [bkz. risk tabanlı Koşullu Erişim](/azure/active-directory/conditional-access/howto-conditional-access-policy-risk).

Azure AD P1 ve P2 hakkında daha fazla bilgi için bkz. [Azure Active Directory bakın](https://azure.microsoft.com/pricing/details/active-directory/).

### <a name="turn-on-modern-authentication-for-your-organization"></a>Organizasyonu için Modern kimlik doğrulamayı açma

Çoğu abonelik için modern kimlik doğrulama otomatik olarak açılır, ancak aboneliğinizi Ağustos 2017'den önce satın aldıysanız, büyük olasılıkla Çok Faktörlü Kimlik Doğrulaması gibi özelliklerin Windows istemcilerde çalışması için Modern Kimlik Doğrulama'ya Outlook.


1. Gezinti <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 yönetim merkezi</a>, Sol gezinti çubuğunda Kuruluş ayarlarını **Ayarlar** \> **seçin**.
2. Hizmetler **sekmesinin** altında Modern kimlik **doğrulama'yi** seçin ve **Modern kimlik doğrulama bölmesinde Modern** kimlik doğrulamayı **etkinleştir'in seçili olduğundan** emin olun. Değişiklikleri **kaydet'i seçin**.


## <a name="next-steps"></a>Sonraki adımlar

- [Ek doğrulama yöntemi için kaydolma](https://support.microsoft.com/office/ace1d096-61e5-449b-a875-58eb3d74de14)
- [Nedir: Multifactor Authentication](https://support.microsoft.com/help/4577374/what-is-multifactor-authentication)
- [Kayıt sonrasında oturum açma](https://support.microsoft.com/office/2b856342-170a-438e-9a4f-3c092394d3cb)
- [Ek doğrulama yöntemini değiştirme](https://support.microsoft.com/office/956ec8d0-7081-4518-a701-f8414cc20831)

## <a name="related-content"></a>İlgili içerik

[Çok faktörlü kimlik doğrulamasını](set-up-multi-factor-authentication.md) ayarlama (video)

[Telefonunuz için çok faktörlü kimlik doğrulamasını açma](https://support.microsoft.com/office/ace1d096-61e5-449b-a875-58eb3d74de14)
