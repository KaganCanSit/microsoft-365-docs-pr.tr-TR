---
title: Microsoft 365 Lighthouse'de çok faktörlü kimlik doğrulamasını yönetme
f1.keywords: NOCSH
ms.author: sharik
author: SKjerland
manager: scotv
audience: Admin
ms.topic: article
ms.prod: microsoft-365-lighthouse
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolio
- M365-Lighthouse
search.appverid: MET150
description: Microsoft 365 Lighthouse kullanan Yönetilen Hizmet Sağlayıcıları (MSP) için çok faktörlü kimlik doğrulamasını yönetmeyi öğrenin.
ms.openlocfilehash: 53f1b0fa9a477ae74b48c96f76f9b2523fe45c10
ms.sourcegitcommit: 339d2c2ffea06726f69429f73c1113c649f37b18
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2022
ms.locfileid: "65023205"
---
# <a name="manage-multifactor-authentication-in-microsoft-365-lighthouse"></a>Microsoft 365 Lighthouse'de çok faktörlü kimlik doğrulamasını yönetme

Azure Active Directory (Azure AD) Multi-Factor Authentication (MFA), veri ve uygulamalara erişimi korumaya yardımcı olur ve ikinci bir kimlik doğrulama biçimi kullanarak başka bir güvenlik katmanı sağlar. Çok Faktörlü Kimlik Doğrulaması sekmesi, kiracılarınız genelinde MFA etkinleştirmesinin durumu hakkında ayrıntılı bilgi sağlar. MFA gerektiren Koşullu Erişim ilkelerinin zaten yapılandırıldığı ve MFA için henüz hangi kullanıcıların kaydolmadığı da dahil olmak üzere bu kiracıyla ilgili daha fazla ayrıntı görmek için listeden herhangi bir kiracıyı seçin.

Microsoft, küçük ve orta ölçekli işletme (SMB) müşterileri için [güvenlik varsayılanlarının](/azure/active-directory/fundamentals/concept-fundamentals-security-defaults) en düşük düzeyde etkinleştirilmesini önerir. Daha karmaşık senaryolar için [Koşullu Erişim'i](/azure/active-directory/conditional-access/overview) kullanarak belirli ilkeleri yapılandırabilirsiniz.

## <a name="before-you-begin"></a>Başlamadan önce

Kiracı listede görünmeden önce aşağıdaki koşulların karşılanması gerekir:

- Müşteri kiracısının her kullanıcı için bir Azure AD Premium lisansı olmalıdır. MFA'yı destekleyen lisanslar hakkında daha fazla bilgi için bkz. [Azure AD Multi-Factor Authentication için özellikler ve lisanslar](/azure/active-directory/authentication/concept-mfa-licensing).

- Müşteri kiracısının Microsoft 365 Lighthouse içinde etkin olması gerekir. Kiracının etkin olup olmadığını belirlemeyi öğrenmek için bkz. [Microsoft 365 Lighthouse kiracı listesine genel bakış](/microsoft-365/lighthouse/m365-lighthouse-tenant-list-overview).

## <a name="enable-mfa-for-a-tenant"></a>Kiracı için MFA'yı etkinleştirme

1. Lighthouse'un sol gezinti bölmesinde **Kullanıcılar'ı** seçin.

2. **Çok Faktörlü Kimlik Doğrulaması** sekmesini seçin.

3. Kiracı listesinden bir kiracı seçerek ayrıntılar bölmesini açın.

4. **MFA etkinleştirme** sekmesinde, **Güvenlik varsayılanlarıyla MFA'nın altında Güvenlik Varsayılanlarını** **Etkinleştir'i** seçin.

5. **Değişiklikleri kaydet'i** seçin.

Koşullu Erişim aracılığıyla MFA'yı etkinleştirmek için bkz [. Öğretici: Azure AD Multi-Factor Authentication ile kullanıcı oturum açma olaylarının güvenliğini](/azure/active-directory/authentication/tutorial-enable-azure-mfa) sağlama.

## <a name="notify-users-who-arent-registered-for-mfa"></a>MFA'ya kayıtlı olmayan kullanıcılara bildirme

1. Lighthouse'un sol gezinti bölmesinde **Kullanıcılar'ı** seçin.

2. **Çok Faktörlü Kimlik Doğrulaması** sekmesini seçin.

3. Kiracı listesinden bir kiracı seçerek ayrıntılar bölmesini açın.

4. **MFA için kayıtlı olmayan kullanıcı** sekmesinde, bildirmek istediğiniz kullanıcıları seçin.

5. **E-posta oluştur'u** seçin.

Lighthouse varsayılan e-posta istemcinizi açar ve MFA'ya kaydolma yönergeleriyle birlikte e-posta iletisini önceden doldurulur. Seçilen tüm kullanıcılar Gizli satırına eklenir. Kullanıcılara tek tek e-posta göndermeyi tercih ederseniz, kullanıcı adının yanındaki e-posta simgesini seçebilirsiniz.

Farklı bir e-posta hesabı kullanmak istiyorsanız, kullanıcı listesini bir dosyaya aktarabilirsiniz. Ayrıca, şirketinizin markasıyla özelleştirebileceğiniz örnek e-posta şablonlarını da indirebilirsiniz.

## <a name="next-steps"></a>Sonraki adımlar

MFA etkinleştirildikten sonra Azure Active Directory (Azure AD) self servis parola sıfırlamayı etkinleştirebilirsiniz. Bu özellik, kullanıcılara yönetici veya yardım masası katılımı olmadan parolalarını değiştirme veya sıfırlama olanağı sağlar. Daha fazla bilgi için bkz. [Microsoft 365 Lighthouse'de self servis parola sıfırlamayı yönetme](m365-lighthouse-manage-sspr.md).

## <a name="related-content"></a>İlgili içerik

[Azure Active Directory Multi-Factor Authentication dağıtımı planlama](/azure/active-directory/authentication/howto-mfa-getstarted) (makale)\
[Güvenlik varsayılanları nedir?](/azure/active-directory/fundamentals/concept-fundamentals-security-defaults) (makale)\
[Koşullu Erişim Nedir?](/azure/active-directory/conditional-access/overview) (makale)\
[Kullanıcıları kullanıcı başına MFA'dan Koşullu Erişim'e dönüştürmeyi öğrenin](/azure/active-directory/authentication/howto-mfa-getstarted#convert-users-from-per-user-mfa-to-conditional-access-based-mfa) (makale)
