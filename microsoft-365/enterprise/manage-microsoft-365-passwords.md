---
title: Kullanıcı Microsoft 365 parolalarını yönetme
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
audience: Admin
ms.topic: overview
ms.prod: office-online-server
ms.localizationpriority: medium
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-mar2020
ms.collection:
- Ent_O365
- M365-subscription-management
search.appverid:
- MET150
- MOE150
- MED150
- BCS160
ms.assetid: 98ca5b3f-f720-4d8e-91be-fe656548a25a
description: Kullanıcı hesabı parolalarını Microsoft 365 yönetmeyi öğrenin.
ms.openlocfilehash: 6a0d4298f3d6c46ab067795bccf01123605ce1aa
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62977671"
---
# <a name="manage-microsoft-365-user-account-passwords"></a>Kullanıcı Microsoft 365 parolalarını yönetme

*Bu makale hem son hem de Microsoft 365 Kurumsal hem de Office 365 Kurumsal.*

Kullanıcı Microsoft 365 parolalarını, kimlik yapılandırmanıza bağlı olarak farklı şekillerde yönetebilirsiniz. Kullanıcı hesaplarını etki alanı [dizininde, Active Directory Microsoft 365 yönetim merkezi](/admin) Hizmetleri'nde (AD DS) veya Azure Active Directory (Azure AD) yönetim merkezinden yönetebilirsiniz.

## <a name="plan-for-where-and-how-you-will-manage-your-user-account-passwords"></a>Kullanıcı hesabı parolalarınızı nerede ve nasıl yöneteceklerinizi planlama

Kullanıcı hesaplarınızı nasıl ve nerede yönetebilirsiniz, kullanıcı hesaplarınız için kullanmak istediğiniz kimlik modeline Microsoft 365. Bu iki model yalnızca bulut ve karmadır.
  
### <a name="cloud-only"></a>Yalnızca bulut

Kullanıcı hesabı parolalarını şu hesaplarda yönetirsiniz:

- [Microsoft 365 yönetim merkezi](/admin)
- Azure AD yönetim merkezi
    
### <a name="hybrid"></a>Karma

Karma kimlikle, parolalar AD DS'de depolanır, dolayısıyla kullanıcı hesabı parolalarını yönetmek için şirket içi AD DS araçlarını kullanasınız. Azure AD'nin, zaten karma olarak bulunan bir sürümünü AD DS'de depolarken Parola Karma Eşitlemesi (PHS) kullansanız bile, sizin ve kullanıcılarının parolalarını AD DS'de yönetmeniz gerekir.

Parola [geri yazma ile](#pw_writeback), kullanıcılarınız Azure AD aracılığıyla AD DS parolalarını değiştirebilir.

## <a name="prevent-bad-passwords"></a>Hatalı parolaları önleme

Tüm kullanıcılarınız, kullanıcı [hesabı parolalarını oluşturmak için Microsoft'un](https://www.microsoft.com/research/publication/password-guidance) parola kılavuzlarını kullanıyor olması gerekir.

Kullanıcıların kolayca belirlenecek bir parola oluşturmasını önlemek için, hem genel yasaklanan parola listesini hem de belirttiğiniz isteğe bağlı özel bir yasaklanmış parola listesini kullanan Azure AD parola korumasını kullanın. Örneğin, aşağıdakiler gibi, organizasyona özel terimleri belirtsiniz:

- Marka adları
- Ürün adları
- Konumlar (örneğin, şirket genel merkezi)
- Şirkete özel iç terimler
- Belirli bir şirket anlamı olan kısaltmalar

Bulutta ve şirket içi [](/azure/active-directory/authentication/concept-password-ban-bad) [AD DS'niz için hatalı parolaları yasaklamanız gerekir](/azure/active-directory/authentication/concept-password-ban-bad-on-premises).

## <a name="simplify-user-sign-in"></a>Kullanıcı oturum açma işlemini basitleştirme

Azure AD Sorunsuz Çoklu Sign-On (Azure AD Sorunsuz SSO), PHS ve Pass-Through Kimlik Doğrulaması (PTA) ile birlikte çalışır ve kullanıcılarının, parolalarını yazmaları gerekmeden Azure AD kullanıcı hesaplarını kullanan hizmetlerde oturum açmalarına ve çoğu durumda kullanıcı adları olur. Bu, kimlik federasyon sunucuları gibi ek şirket içi bileşenlere gerek kalmadan kullanıcılarınızı Office 365 gibi bulut tabanlı uygulamalara daha kolay erişim sağlar.

Azure AD Sorunsuz SSO'yi Azure AD Sorunsuz SSO Bağlan yapılandırabilirsiniz. [Azure AD Sorunsuz SSO'nun yapılandırılması için yönergelere bakın](/azure/active-directory/connect/active-directory-aadconnect-sso-quick-start).

<a name="pw_writeback"></a>
## <a name="simplify-password-updates-to-ad-ds"></a>AD DS parola güncelleştirmelerini basitleştirme

Parola geri yazma ile, kullanıcıların parolalarını Azure AD aracılığıyla sıfırlamalarına izin ve ardından bu parolaların AD DS'ye çoğaltılmasına izin veebilirsiniz. Kullanıcıların parolalarını güncelleştirmek için şirket içi AD DS'lerine erişmeleri gerekmektedir. Bu, şirket içi ağa uzaktan erişim bağlantısı olmayan dolaşım veya uzak kullanıcılar için değerlidir.

Azure AD Kimlik Koruması'nın özelliklerini tam olarak kullanmak için, örneğin kullanıcıların algılanan yüksek bir hesap güvenliği riski olduğunda şirket içi parolalarını değiştirmelerini zorunlu kabilmek için parola geri yazması gerekir.

Ek bilgi ve yapılandırma yönergeleri için bkz. [Parola geri yazma ile Azure AD SSPR](/azure/active-directory/active-directory-passwords-writeback).

>[!Note]
>En iyi deneyimi ve yayımlanan yeni Bağlan sağlamak için Azure AD Bağlan'ın en son sürümüne yükseltin. Daha fazla bilgi için bkz[. Azure AD'nin özel yüklemesi Bağlan](/azure/active-directory/connect/active-directory-aadconnect-get-started-custom).
>

## <a name="simplify-password-resets"></a>Parola sıfırlamalarını basitleştirme

Self servis parola sıfırlama (SSPR), kullanıcıların parolalarını veya hesaplarını sıfırlamalarına veya kilidini açmalarına olanak sağlar. Kötüye kullanımı veya kötüye kullanımı önlemek için, kullanıcıların sisteme erişimini takip eden ayrıntılı raporlamayı ve bildirimleri kullanabilirsiniz. Parola sıfırlamalarını [dağıtmadan önce](#pw_writeback) parola geri yazmayı etkinleştirmeniz gerekir.

Parola [sıfırlamayı kullanma yönergelerine bakın](/azure/active-directory/authentication/howto-sspr-deployment).