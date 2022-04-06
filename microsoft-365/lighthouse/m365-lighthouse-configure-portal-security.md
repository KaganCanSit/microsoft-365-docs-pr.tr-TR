---
title: Portal Microsoft 365 Lighthouse yapılandırma
f1.keywords: CSH
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
description: Yönetilen Hizmet Sağlayıcıları (MSP) Microsoft 365 Lighthouse, portal güvenliğini yapılandırmayı öğrenin.
ms.openlocfilehash: 4d12755ca1b02988dff3f5ba6be6dd0d8da172ad
ms.sourcegitcommit: 33bc25167812b31c51cf096c728e3a5854e94f1c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/01/2022
ms.locfileid: "64594762"
---
# <a name="configure-microsoft-365-lighthouse-portal-security"></a>Portal Microsoft 365 Lighthouse yapılandırma

Bir Yönetilen Hizmet Sağlayıcısı (MSP) kiracılarına temsilci erişim izinleri geldiğinde müşteri verilerine erişimi koruma bir siber güvenlik önceliğidir. Microsoft 365 Lighthouse, Deniz Feneri portalı güvenliğini yapılandırmanıza yardımcı olmak için gerekli ve isteğe bağlı özelliklerle birlikte gelir. Lighthouse'a erişmek için önce Çok Faktörlü Kimlik Doğrulaması (MFA) özelliği etkinleştirilmiş belirli roller ayarlay gerekir. İsterseniz Azure AD E-posta (PIM) Privileged Identity Management Koşullu Erişim'i de kurabilirsiniz.

## <a name="set-up-multifactor-authentication-mfa"></a>Çok faktörlü kimlik doğrulamasını (MFA) ayarlama

Blog gönderisinde de [belirtildiği gibi Pa$$word önemli değildir](https://techcommunity.microsoft.com/t5/azure-active-directory-identity/your-pa-word-doesn-t-matter/ba-p/731984):

> "Parolanız önemli değil, ama MFA önemli. Çalışmalarımıza göre, MFA kullanırsanız hesabınız %99,9'dan daha az tehlikeye atılmış olur."

Kullanıcılar Deniz Feneri'ne ilk kez erişdiğinde, deniz feneri hesaplarının henüz yapılandırılmamışsa MFA'Microsoft 365 ayarlamaları istenir. Gerekli MFA kurulum adımı tamamlanana kadar kullanıcılar Deniz Feneri'ne eriş olmayacaktır. Kimlik doğrulama yöntemleri hakkında daha fazla bilgi edinmek için bkz. [Multifactor authentication Microsoft 365 oturum açma yönteminizi ayarlama](https://support.microsoft.com/office/ace1d096-61e5-449b-a875-58eb3d74de14).

## <a name="set-up-role-based-access-control"></a>Rol tabanlı erişim denetimi ayarlama

Rol tabanlı erişim denetimi (RBAC), kullanıcı rollerine dayalı olarak kaynaklara veya bilgilere erişim sağlar. Deniz Feneri'nde müşteri kiracı verilerine ve ayarlarına erişim, genel programdan (CSP) Bulut Çözümü Sağlayıcısı rollerle sınırlıdır. Deniz Feneri'nde RBAC rolleri ayarlamak için, kullanıcılara ayrıntılı atamalar uygulamak için Ayrıntılı Temsilcili Yönetici Ayrıcalıkları (GDAP) kullanmanız önerilir. Kiracının başarılı bir şekilde eklemesi için temsili Yönetici Ayrıcalıkları (DAP) yine gereklidir, ancak yalnızca GDAP müşterileri yakın zamanda DAP'ye bağımlılık olmadan eklemede abilecektir. DAP ve GDAP bir müşteri için birlikte olduğunda GDAP izinleri öncelikli olur. 

GDAP'yi çalışmaya başlamak için bkz. [GDAP'de izinlere Microsoft 365 Lighthouse](m365-lighthouse-overview-of-permissions.md).

MSP teknisyenleri Ayrıca Yönetici Temsilcisi veya Yardım masası Aracısı rollerini Temsilci Yönetici Ayrıcalıkları (DAP) aracılığıyla kullanarak Deniz Feneri'ne de erişebilirler.

Deniz Feneri'nde müşteriyle ilgili olmayan kiracı eylemleri için (örneğin, işe alma, müşteriyi devre dışı bırakma/yeniden etkinleştirme, etiketleri yönetme, günlükleri gözden geçirme), MSP teknisyenlerinin iş ortağı kiracısında atanmış bir rolü olması gerekir. Önceki makalenin bağlantı ayrıntılarında, Deniz Feneri'nde roller ve bunların izinleri yer almıştır.

## <a name="set-up-azure-ad-privileged-identity-management-pim"></a>Azure AD Privileged Identity Management'i (PIM) ayarlama

MSP'ler, PIM kullanarak bilgilerin ve kaynakların güvenliğini sağlamak için yüksek ayrıcalık rolüne sahip olan kişi sayısını en aza indirgeyebilirsiniz. PIM, kötü niyetli bir kişinin yanlışlıkla hassas bir kaynağı etkilemesi için kaynaklara veya yetkili kullanıcılara erişim kazanma riskini azaltır. AYRıCA MSP'ler, kullanıcılara kaynaklara erişmeleri, kapsamlı değişiklikler yapmaları ve ayrıca erişimleri ile belirlenen kullanıcıların ne yaptığını izlemeleri için yalnızca bir defalık yüksek ayrıcalık rolleri verebilir. 

> [!NOTE]
> Azure AD PIM'nin kullanımı için Azure AD Premium P2 kiracıda kimlik lisansı gerekir.

Aşağıdaki adımlar, PIM kullanarak iş ortağı kiracı kullanıcılarını zaman kapsamına daha yüksek ayrıcalık rollerine yükseltilmiştir:

1. Azure Active Directory'de rol atamak için grup oluşturma makalesinde [açıklandığı gibi rol atanabilir bir grup Azure Active Directory](/azure/active-directory/roles/groups-create-eligible).

2. [Azure AD – Tüm](https://portal.azure.com/#blade/Microsoft_AAD_IAM/GroupsManagementMenuBlade/AllGroups) Gruplar'a gidin ve yeni grubu yüksek ayrıcalık rolleri için bir güvenlik grubunun üyesi olarak ekleyin (örneğin, DAP için Yönetici Aracıları güvenlik grubu veya GDAP rolleri için benzer bir güvenlik grubu).

3. Yeni gruba ayrıcalıklı erişimi ayarlamak için, Ayrıcalıklı erişim grupları için uygun [sahipler ve üyeler atama makalesinde açıklandığı gibi ayarlayın](/azure/active-directory/privileged-identity-management/groups-assign-member-owner).

PIM hakkında daha fazla bilgi edinmek için bkz[. PRIVILEGED IDENTITY MANAGEMENT?](/azure/active-directory/privileged-identity-management/pim-configure)

## <a name="set-up-risk-based-azure-ad-conditional-access"></a>Risk tabanlı Azure AD Koşullu Erişimi ayarlama

MSP'ler, personel üyelerinin MFA kullanarak ve riskli bir kullanıcı olarak algılandığında (sızdırılmış kimlik bilgileri veya Azure AD tehdit zekası başına) parolalarını değiştirerek kimliklerini kanıtlamaları için risk tabanlı Koşullu Erişim kullanabilir. Ayrıca, kullanıcıların riskli bir oturum açma olarak algılandığında tanıdık bir konumdan veya kayıtlı cihazdan da oturum açması gerekir. Diğer riskli davranışlar, kötü amaçlı veya anonim IP adreslerinden ya da atyptik veya olanaksız bir seyahat konumdan oturum açma, anormal bir belirteç kullanma, parolalarını kullanma veya alışılmışın dışında başka oturum açma davranışını sergiler. Kullanıcının risk düzeyine bağlı olarak, MSP'ler oturum açma sırasında erişimi engellemeyi de seçebilir. Riskler hakkında daha fazla bilgi edinmek için bkz [. Risk nedir?](/azure/active-directory/identity-protection/concept-identity-protection-risks) 

> [!NOTE]
> Koşullu Erişim için iş Azure AD Premium P2 bir lisans gerekir. Koşullu Erişimi ayarlamak için bkz. [Koşullu Erişimi Azure Active Directory yapılandırma](/appcenter/general/configuring-aad-conditional-access).

## <a name="related-content"></a>İlgili içerik

[Parola sıfırlama izinleri](/azure/active-directory/roles/permissions-reference#password-reset-permissions) (makale)\
[Sistem Gereksinimleri Microsoft 365 Lighthouse](m365-lighthouse-requirements.md) (makale)\
[Genel bakış Microsoft 365 Lighthouse](m365-lighthouse-overview.md) (makale)\
[Microsoft 365 Lighthouse](m365-lighthouse-sign-up.md) (makale)\ için kaydolma
[Microsoft 365 Lighthouse SSS](m365-lighthouse-faq.yml) (makale)