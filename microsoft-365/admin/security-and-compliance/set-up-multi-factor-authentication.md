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
description: Kuruluşunuz için çok faktörlü kimlik doğrulamasını ayarlamayı öğrenin.
monikerRange: o365-worldwide
ms.openlocfilehash: faac2f052b7c184a967f916cca433dfaef6866c7
ms.sourcegitcommit: db1e48af88995193f15bbd5962f5101a6088074b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/23/2022
ms.locfileid: "65637350"
---
# <a name="set-up-multifactor-authentication-for-microsoft-365"></a>Microsoft 365 için çok faktörlü kimlik doğrulamasını ayarlama

Çok faktörlü kimlik doğrulaması, sizin ve çalışanlarınızın işletmenizin güvenliğini sağlamanın en kolay yollarından biri Microsoft 365 oturum açmak için birden fazla yol sağlaması gerektiği anlamına gelir. [Çok faktörlü kimlik doğrulaması (MFA) anlayışınıza ve Microsoft 365 desteğine](multi-factor-authentication-microsoft-365.md) bağlı olarak, bunu ayarlamanın ve kuruluşunuza dağıtmanın zamanı geldi. 

> [!IMPORTANT]
> Aboneliğinizi veya deneme sürümünüzü 21 Ekim 2019'da satın aldıysanız ve oturum açtığınızda MFA istenirse, aboneliğiniz için [güvenlik varsayılanları](/azure/active-directory/fundamentals/concept-fundamentals-security-defaults) otomatik olarak etkinleştirilir.

> [!TIP]
> Bu konuda verilen adımlarla ilgili yardıma ihtiyacınız varsa[bir Microsoft küçük işletme uzmanıyla çalışmayı](https://go.microsoft.com/fwlink/?linkid=2186871) göz önünde bulundurun. İşletme Yardımı ile, işletmenizi büyütürken katılımdan gündelik kullanıma kadar her aşamada siz ve çalışanlarınız günün 24 saati küçük işletme uzmanlarına erişebilirsiniz.

## <a name="watch-turn-on-multifactor-authentication"></a>İzleyin: Çok faktörlü kimlik doğrulamasını açma

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE2MuO3?autoplay=false]

1. konumundaki Microsoft 365 yönetim merkezi <a href="https://admin.microsoft.com/ " target="_blank">https://admin.microsoft.com</a>gidin.
1. **Tümünü Göster'i** ve ardından **Azure Active Directory Yönetim Merkezi'ni** seçin.
1. **Azure Active Directory**, **Özellikler**, **Güvenlik varsayılanlarını yönet'i** seçin.
1. **Güvenlik varsayılanlarını etkinleştir'in** altında **Evet'i** ve ardından **Kaydet'i** seçin.

## <a name="before-you-begin"></a>Başlamadan önce

- MFA'yi yönetmek için Genel yönetici olmanız gerekir. Daha fazla bilgi için bkz. [Yönetici rolleri hakkında](../add-users/about-admin-roles.md).
- Eski kullanıcı başına MFA açıksa Kullanıcı [başına eski MFA'yı kapatın](#turn-off-legacy-per-user-mfa).
- Windows cihazlarda Office 2013 istemcileriniz varsa, [Office 2013 istemcileri için Modern Kimlik Doğrulaması'nı açın](./enable-modern-authentication.md).
- Gelişmiş: Active Directory Federasyon Hizmetleri (AD FS) (AD FS) içeren üçüncü taraf dizin hizmetleriniz varsa Azure MFA Sunucusu'nu ayarlayın. Daha fazla bilgi için [bkz. Azure AD Çok Faktörlü Kimlik Doğrulaması ve üçüncü taraf VPN çözümleriyle gelişmiş senaryolar](/azure/active-directory/authentication/howto-mfaserver-nps-vpn).

### <a name="turn-off-legacy-per-user-mfa"></a>Eski kullanıcı başına MFA'ları kapatma

Daha önce kullanıcı başına MFA'yı açtıysanız Güvenlik varsayılanlarını etkinleştirmeden önce kapatmanız gerekir.

1. Microsoft 365 yönetim merkezi sol gezinti bölmesinde **Kullanıcılar** \> **Etkin kullanıcılar'ı** seçin.
1. **Etkin kullanıcılar** sayfasında **Çok faktörlü kimlik doğrulaması'nı** seçin.
1. Çok faktörlü kimlik doğrulaması sayfasında her kullanıcıyı seçin ve Multi-Factor kimlik doğrulaması durumunu **Devre Dışı** olarak ayarlayın.

## <a name="turn-security-defaults-on-or-off"></a>Güvenlik varsayılanlarını açma veya kapatma

Çoğu kuruluş için Güvenlik varsayılanları iyi bir düzeyde ek oturum açma güvenliği sunar. Daha fazla bilgi için bkz. [Güvenlik varsayılanları nedir?](/azure/active-directory/fundamentals/concept-fundamentals-security-defaults)

Aboneliğiniz yeniyse Güvenlik varsayılanları sizin için zaten otomatik olarak açılmış olabilir.

Azure portal Azure Active Directory (Azure AD) için **Özellikler** bölmesinden güvenlik varsayılanlarını etkinleştirir veya devre dışı bırakırsınız.

1. Genel yönetici kimlik bilgileriyle [Microsoft 365 yönetim merkezi](https://admin.microsoft.com) oturum açın.
2. Sol gezinti bölmesinde **Tümünü Göster'i** seçin ve **Yönetim merkezleri'nin** altında **Azure Active Directory'ı** seçin.
3. **Azure Active Directory yönetim merkezinde** **Azure Active Directory** \> **Özellikler'i** seçin.
4. Sayfanın alt kısmında **Güvenlik varsayılanlarını yönet**’i seçin.
5. Güvenlik varsayılanlarını etkinleştirmek için **Evet'i** veya güvenlik varsayılanlarını devre dışı bırakmak için **Hayır'ı** ve ardından **Kaydet'i** seçin.

[Temel Koşullu Erişim ilkelerini](/azure/active-directory/conditional-access/concept-baseline-protection) kullandıysanız, güvenlik varsayılanlarını kullanmaya geçmeden önce bunları kapatmanız istenir.

1. [Koşullu Erişim - İlkeler sayfasına](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ConditionalAccessBlade/Policies) gidin.
2. **Açık** olan her temel ilkeyi seçin ve **İlkeyi etkinleştir** seçeneğini **Kapalı** olarak ayarlayın.
3. [Azure Active Directory - Özellikler sayfasına](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/Properties) gidin.
4. Sayfanın alt kısmında **Güvenlik varsayılanlarını yönet**’i seçin.
5. Güvenlik varsayılanlarını etkinleştirmek için **Evet'i** , güvenlik varsayılanlarını devre dışı bırakmak için **Hayır'ı** ve ardından **Kaydet'i** seçin.

## <a name="use-conditional-access-policies"></a>Koşullu Erişim ilkelerini kullanma

Kuruluşunuzun daha ayrıntılı oturum açma güvenlik gereksinimleri varsa, Koşullu Erişim ilkeleri size daha fazla denetim sunabilir. Koşullu Erişim, bir kullanıcıya uygulama veya hizmet erişimi verilmeden önce oturum açma olaylarına tepki veren ve ek eylemler isteyen ilkeler oluşturmanıza ve tanımlamanıza olanak tanır.

> [!IMPORTANT]
> Koşullu Erişim ilkelerini etkinleştirmeden önce hem kullanıcı başına MFA hem de Güvenlik varsayılanlarını kapatın.

Koşullu Erişim, Azure AD Premium P1 veya Microsoft 365 İş Ekstra ve Microsoft 365 E3 gibi bunu içeren lisansları satın alan müşteriler için kullanılabilir. Daha fazla bilgi için bkz. [Koşullu Erişim ilkesi oluşturma](/azure/active-directory/authentication/tutorial-enable-azure-mfa).

Risk tabanlı koşullu erişim, Azure AD Premium P2 lisansı veya Microsoft 365 E5 gibi bunu içeren lisanslar aracılığıyla kullanılabilir. Daha fazla bilgi için bkz. [Risk tabanlı Koşullu Erişim](/azure/active-directory/conditional-access/howto-conditional-access-policy-risk).

Azure AD P1 ve P2 hakkında daha fazla bilgi için bkz. [Azure Active Directory fiyatlandırması](https://azure.microsoft.com/pricing/details/active-directory/).

### <a name="turn-on-modern-authentication-for-your-organization"></a>Kuruluşunuz için Modern kimlik doğrulamasını açma

Çoğu abonelikte modern kimlik doğrulaması otomatik olarak açılır, ancak aboneliğinizi Ağustos 2017'den önce satın aldıysanız, Outlook gibi Windows istemcilerde çalışmak üzere Çok Faktörlü Kimlik Doğrulaması gibi özellikleri almak için Büyük olasılıkla Modern Kimlik Doğrulaması'nı açmanız gerekir.


1. <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 yönetim merkezi</a> sol gezinti bölmesinde **Kuruluş** **ayarları'nı Ayarlar** \> seçin.
2. **Hizmetler** sekmesinde **Modern kimlik doğrulaması'nı** seçin ve **Modern kimlik doğrulaması bölmesinde Modern kimlik** **doğrulamasını etkinleştir'in** seçili olduğundan emin olun. **Değişiklikleri kaydet'i** seçin.


## <a name="next-steps"></a>Sonraki adımlar

- [Ek doğrulama yöntemine kaydolma](https://support.microsoft.com/office/ace1d096-61e5-449b-a875-58eb3d74de14)
- [Nedir: Çok Faktörlü Kimlik Doğrulaması](https://support.microsoft.com/help/4577374/what-is-multifactor-authentication)
- [Kayıt sonrasında oturum açma](https://support.microsoft.com/office/2b856342-170a-438e-9a4f-3c092394d3cb)
- [Ek doğrulama yöntemlerini değiştirme](https://support.microsoft.com/office/956ec8d0-7081-4518-a701-f8414cc20831)

## <a name="related-content"></a>İlgili içerik

[Çok faktörlü kimlik doğrulamasını ayarlama](set-up-multi-factor-authentication.md) (video)

[Telefonunuz için çok faktörlü kimlik doğrulamasını açma](https://support.microsoft.com/office/ace1d096-61e5-449b-a875-58eb3d74de14)
