---
title: Çok faktörlü kimlik doğrulamasını yönetme
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
description: Çok Faktörlü Kimlik Doğrulaması kullanılarak Yönetilen Hizmet Microsoft 365 Lighthouse(MSP)'ler için, çok faktörlü kimlik doğrulamasını yönetmeyi öğrenin.
ms.openlocfilehash: 4587dffbe45eacaf62c49d0c84aeef86455980e1
ms.sourcegitcommit: 3140e2866de36d57a27d27f70d47e8167c9cc907
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2021
ms.locfileid: "62988834"
---
# <a name="manage-multifactor-authentication"></a>Çok faktörlü kimlik doğrulamasını yönetme

> [!NOTE]
> Bu makalede açıklanan özellikler Önizleme'dedir, değişebilir ve yalnızca gereksinimleri karşılayacak iş ortakları tarafından [kullanılabilir](m365-lighthouse-requirements.md). Henüz oturum açmadıysanız Microsoft 365 Lighthouse için [kaydolma'ya Microsoft 365 Lighthouse](m365-lighthouse-sign-up.md).

Azure Active Directory (Azure AD) Multi-Factor Authentication (MFA), ikinci bir kimlik doğrulama biçimi kullanarak veri ve uygulamalara erişimi korumaya, başka bir güvenlik katmanı sağlar. Çok Faktörlü Kimlik Doğrulaması sekmesi kiracılar arasında MFA etkinleştirmesi durumu hakkında ayrıntılı bilgi sağlar. MFA gerektiren hangi Koşullu Erişim ilkelerinin zaten yapılandırılmış olduğu ve hangi kullanıcıların henüz MFA için kayıtlı olmadığını da içeren diğer ayrıntıları görmek için listeden herhangi bir kiracıyı seçin.

Küçük ve orta ölçekli işletme (SMB) müşterileri için Microsoft, güvenlik varsayılanlarını en az [olarak](/azure/active-directory/fundamentals/concept-fundamentals-security-defaults) etkinleştirmenizi öneririz. Daha karmaşık senaryolarda, belirli ilkeleri yapılandırmak [için Koşullu Erişim'i](/azure/active-directory/conditional-access/overview) kullanabilirsiniz.

## <a name="before-you-begin"></a>Başlamadan önce

Kiracının listede görünmesi için aşağıdaki koşulların karşı görünmesi gerekir:

- Müşteri kiracısı, her kullanıcı Azure AD Premium lisansına sahip olması gerekir. Hangi lisansların MFA'ya destek olduğu hakkında daha fazla bilgi için bkz. [Azure AD Multi-Factor Authentication için özellikler ve lisanslar](/azure/active-directory/authentication/concept-mfa-licensing).

- Müşteri kiracısı, kiracı kiracı içinde Microsoft 365 Lighthouse. Kiracının etkin olup olmadığını belirlemeyi öğrenmek için bkz. [Kiracı listesine Microsoft 365 Lighthouse genel bakış](/microsoft-365/lighthouse/m365-lighthouse-tenant-list-overview).

## <a name="enable-mfa-for-a-tenant"></a>Kiracı için MFA'yi etkinleştirme

1. Deniz Feneri'nin sol gezinti bölmesinde Kullanıcılar'ı **seçin**.

2. Multifactor **Authentication sekmesini** seçin.

3. Kiracı listesinden, ayrıntılar bölmesini açmak için bir kiracı seçin.

4. **MFA etkinleştirme sekmesindeki Güvenlik** varsayılanları **ile MFA'nın altında Güvenlik** **Varsayılanlarını Etkinleştir'i seçin**.

5. Değişiklikleri **kaydet'i seçin**.

Koşullu Erişim aracılığıyla MFA'yi etkinleştirmek için bkz [. Öğretici: Azure AD Multi-Factor Authentication ile kullanıcı oturum açma olaylarının güvenliğini sağlama](/azure/active-directory/authentication/tutorial-enable-azure-mfa).

## <a name="notify-users-who-arent-registered-for-mfa"></a>MFA için kayıtlı olmayan kullanıcıları bilgilendirme

1. Deniz Feneri'nin sol bölmesinde Kullanıcılar'ı **seçin**.

2. Multifactor **Authentication sekmesini** seçin.

3. Kiracı listesinden, ayrıntılar bölmesini açmak için bir kiracı seçin.

4. **MFA için kayıtlı değil kullanıcı** sekmesinde, bildirmek istediğiniz kullanıcıları seçin.

5. **E-posta oluştur'a seçin**.

Deniz Feneri varsayılan e-posta istemcinizi açar ve E-posta iletisiyle MFA'ya kaydolma yönergelerini önceden doldurmaya devam ediyor. Seçilen tüm kullanıcılar Gizli satırına dahil edilir. Tek tek kullanıcılara e-posta göndermeyi tercih ediyorsanız, kullanıcı adı'nın yanındaki e-posta simgesini seçin.

Farklı bir e-posta hesabı kullanmak için, kullanıcı listesini bir dosyaya aktarabilirsiniz. Ayrıca, şirketi markalamayla özelleştirebileceğiniz örnek e-posta şablonları da indirebilirsiniz.

## <a name="next-steps"></a>Sonraki adımlar

MFA etkinleştirildikten sonra, Azure Active Directory (Azure AD) self servis parola sıfırlamayı etkinleştirebilirsiniz. Bu özellik kullanıcılara yönetici veya yardım masası katılımı yoksa parolalarını değiştirme veya sıfırlama olanağı verir. Daha fazla bilgi için bkz [. Kendi kendine parola sıfırlamayı yönetme](m365-lighthouse-manage-sspr.md).

## <a name="related-content"></a>İlgili içerik

[Çok Faktörlü Azure Active Directory dağıtımı planlama](/azure/active-directory/authentication/howto-mfa-getstarted) (makale)\
[Güvenlik varsayılanları nedir?](/azure/active-directory/fundamentals/concept-fundamentals-security-defaults) (article)\
[Koşullu Erişim Nedir?](/azure/active-directory/conditional-access/overview) (article)\
[Kullanıcıları kullanıcı başına MFA'dan Koşullu Erişim'e dönüştürmeyi öğrenin](/azure/active-directory/authentication/howto-mfa-getstarted#convert-users-from-per-user-mfa-to-conditional-access-based-mfa) (makale)
