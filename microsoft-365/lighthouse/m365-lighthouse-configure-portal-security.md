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
ms.openlocfilehash: c40805267320488e79c774954fd8f6bd696449fa
ms.sourcegitcommit: 0ee2dabe402d44fecb6856af98a2ef7720d25189
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/09/2021
ms.locfileid: "63009306"
---
# <a name="configure-microsoft-365-lighthouse-portal-security"></a>Portal Microsoft 365 Lighthouse yapılandırma

> [!NOTE]
> Bu makalede açıklanan özellikler Önizleme'dedir, değişebilir ve yalnızca gereksinimleri karşılayacak iş ortakları tarafından [kullanılabilir](m365-lighthouse-requirements.md). Henüz oturum açmadıysanız Microsoft 365 Lighthouse için [kaydolma'ya Microsoft 365 Lighthouse](m365-lighthouse-sign-up.md).

Bir Yönetilen Hizmet Sağlayıcısı (MSP) kiracılarına temsilci erişim izinleri geldiğinde müşteri verilerine erişimi koruma bir siber güvenlik önceliğidir. Microsoft 365 Lighthouse, Deniz Feneri portalı güvenliğini yapılandırmanıza yardımcı olmak için gerekli ve isteğe bağlı özelliklerle birlikte gelir.

## <a name="set-up-multifactor-authentication-mfa"></a>Çok faktörlü kimlik doğrulamasını (MFA) ayarlama

Blog gönderisinde de [belirtildiği gibi Pa$$word önemli değildir](https://techcommunity.microsoft.com/t5/azure-active-directory-identity/your-pa-word-doesn-t-matter/ba-p/731984):

> "Parolanız önemli değil, ama MFA önemli. Çalışmalarımıza göre, MFA kullanırsanız hesabınız %99,9'dan daha az tehlikeye atılmış olur."

Kullanıcılar Deniz Feneri'ne ilk kez erişdiğinde, deniz feneri hesaplarının henüz yapılandırılmamışsa MFA'Microsoft 365 ayarlamaları istenir. Gerekli MFA kurulum adımı tamamlanana kadar kullanıcılar Deniz Feneri'ne eriş olmayacaktır. Kimlik doğrulama yöntemleri hakkında daha fazla bilgi edinmek için bkz. [Multifactor authentication Microsoft 365 oturum açma yönteminizi ayarlama](https://support.microsoft.com/office/ace1d096-61e5-449b-a875-58eb3d74de14).

## <a name="set-up-roles-to-manage-customer-tenants"></a>Müşteri kiracılarını yönetmek için rolleri ayarlama

Deniz Feneri'nde müşteri kiracı verilerine ve ayarlarına erişim, Bulut Çözüm Sağlayıcısı (CSP) programından Yönetici Aracısı ve Yardım masası Aracısı rollerine sınırlıdır.

[Azure AD –](https://portal.azure.com/#blade/Microsoft_AAD_IAM/GroupsManagementMenuBlade/AllGroups) Tüm Gruplar sayfasında güvenlik grubu üyeliklerini gözden geçirerek, iş ortağı kiracıda hangi kullanıcıların Yönetici Temsilcisi ve Yardım Masası Aracısı rollerine sahip olduğunu kontrol edebilirsiniz. Kullanıcılara CSP program rollerini ve diğer izinleri atamayı öğrenmek için bkz [. Kullanıcılara rol ve izin atama](/partner-center/permissions-overview). MSP olarak, müşteri kiracıları için temsilci erişim ayrıcalıklarınız yoksa, bunları nasıl edinebilirsiniz? Müşteri hizmetini veya aboneliğini yönetmek için izin alma makalesinde bunları nasıl [edinebilirsiniz](/partner-center/customers-revoke-admin-privileges)?

Aşağıdaki tabloda farklı Deniz Feneri sayfaları ve müşteri kiracı verilerini görüntülemek ve bu veriler üzerinde eylemde etmek için gereken izinler ve Yönetici Temsilcisi ile Yardım masası Aracısı rollerinin ayarları listelemektedir.<br><br>

| Deniz feneri sayfası | Yönetici Aracısı izinleri | Yardım masası Aracısı izinleri |
|--|--|--|
| Home | <ul><li>Hepsini görüntüle</li></ul> | <ul><li>Hepsini görüntüle</li></ul> |
| Kiracılar | <ul><li>Hepsini görüntüle</li><li>Müşteri kişilerini ve web sitesini güncelleştirme</li><li>Dağıtım planlarını görüntüleme ve uygulama</li></ul> | <ul><li>Hepsini görüntüle</li><li>Müşteri kişilerini ve web sitesini güncelleştirme</li><li>Dağıtım planlarını görüntüleme</li></ul> |
| Kullanıcılar | <ul><li>Hepsini görüntüle</li><li>Parolayı sıfırlayın</li><li>Oturum açma engelleme</li><li>MFA'yı etkinleştirme</li></ul> | <ul><li>Hepsini görüntüle</li><li>Parolayı sıfırlayın</li><li>Oturum açma engelleme</li></ul> |
| Cihazlar | <ul><li>Hepsini görüntüle</li></ul> | <ul><li>Hepsini görüntüle</li></ul> |
| Tehdit | <ul><li>Hepsini görüntüle</li><li>Hızlı taramayı çalıştırma</li><li>Tam taramayı çalıştır</li><li>Cihazı yeniden başlatma</li><li>Virüsten koruma yazılımını güncelleştirme</li></ul> | <ul><li>Hepsini görüntüle</li></ul> |
| Taban çizgisi | <ul><li>Hepsini görüntüle</li></ul> | <ul><li>Hepsini görüntüle</li></ul> |
| Hizmet durumu | <ul><li>Hepsini görüntüle*</li></ul> | <ul><li>Hepsini görüntüle*</li></ul> |

> [!NOTE]
> Şu anda, tabloda * ile işaretlenmiş eylemleri yapmak için, kullanıcıların şu özellik kümesine sahip iş ortağı kiracısında Azure AD rolüne sahip olmak da gerekir: **microsoft.office365.serviceHealth/allEntities/allTasks**. Azure AD rollerinin listesi için bkz. [Azure AD yerleşik rolleri](/azure/active-directory/roles/permissions-reference).

Yönetici Temsilcisi rolüyle ilişkili kapsamlı izinler göz verilirse, bir iş ortağı kiracısı kullanıcısını Yönetici [](/azure/active-directory/develop/secure-least-privileged-access) Aracısı ve Yardım masası Aracısı olarak atama konusunda en az ayrıcalıklı erişim ilkesine bağlı olarak çalışmanızı öneririz. Bunu yapmak için bir yol, gerekli iş ortağı kiracı kullanıcılarına Yardım masası Aracısı rolünü atamaktır. Bu, müşteri verilerini ve ayarlarını görüntülemelerini sağlar, ancak kapsamlı değişiklikler yapmalarını sağlar. Ardından gerektiğinde, kullanıcılara zaman kapsamına sahip bir Yönetici Temsilcisi rolü vermek için Azure AD Privileged Identity Management'nin (PIM) tam zamanlı erişim onay özelliklerini kullanın.

## <a name="set-up-azure-ad-privileged-identity-management-pim"></a>Azure AD Privileged Identity Management'i (PIM) ayarlama

MSP'ler, Azure AD Pİ'leri (PIM) kullanarak, güvenli bilgilere veya kaynaklara erişimi Privileged Identity Management mümkün olabilir. PIM, kötü niyetli bir kişinin yanlışlıkla hassas bir kaynağı etkilemesi için kaynaklara veya yetkili kullanıcılara erişim kazanma riskini azaltır. AYRıCA MSP'ler kullanıcılara, kaynaklara yalnızca bir defalık ayrıcalıklı erişim izni ve ayrıca erişimle belirlenen kullanıcıların ne yaptığını izleyebilir.

> [!NOTE]
> Azure AD PIM'nin kullanımı için Azure AD Premium P2 kiracıda kimlik lisansı gerekir.

Aşağıdaki adımlar, Azure AD PIM kullanarak iş ortağı kiracı kullanıcılarını zaman kapsamına sahip Yönetici Aracısı rollerine yükseltilmiştir:

1. Azure Active Directory'de rol atamak için grup oluşturma makalesinde [açıklandığı gibi rol atanabilir bir grup Azure Active Directory](/azure/active-directory/roles/groups-create-eligible).

2. [Azure AD – Tüm Gruplar'a](https://portal.azure.com/#blade/Microsoft_AAD_IAM/GroupsManagementMenuBlade/AllGroups) gidin ve yeni grubu Yönetici Aracıları grubuna üye olarak ekleyin.

3. Yeni gruba ayrıcalıklı erişimi ayarlamak için, Ayrıcalıklı erişim grupları için uygun [sahipler ve üyeler atama makalesinde açıklandığı gibi ayarlayın](/azure/active-directory/privileged-identity-management/groups-assign-member-owner).

Daha fazla bilgi edinmek için bkz[. Privileged Identity Management?](/azure/active-directory/privileged-identity-management/pim-configure)

## <a name="other-roles-and-permissions"></a>Diğer roller ve izinler

Aşağıdaki tabloda, iş ortağı kiracı rolleri ve bunların ilişkili izinleri listeledir.<br><br>

| İş ortağı kiracı rolleri | İş ortağı kiracısı içinde izinler |
|--|--|
| İş ortağı kiracısı Genel Yöneticisi | <ul><li>Deniz Feneri'ne Microsoft 365 yönetim merkezi.</li><li>İlk çalıştırma deneyimi sırasında iş ortağı sözleşme değişikliklerini kabul edin.</li><li>Kiracılar sayfasında müşteri kiracılarını görüntüleme.</li><li>Kiracıyı etkinleştirme ve devre dışı bırakma.</li><li>Müşteri kişilerini ve web sitesini güncelleştirin.</li><li>Etiketleri oluşturun, güncelleştirin ve silin.</li><li>Etiketleri müşteri kiracısına atayın ve kaldırın.</li></ul> |
| En az bir iş ortağı kiracısı yöneticisi<br> Aşağıdaki özellik kümesiyle atanan Azure AD rolü:<br> **microsoft.office365.supportTickets/allEntities/allTasks**<br> (Azure AD rollerinin listesi için bkz. [Azure AD yerleşik rolleri](/azure/active-directory/roles/permissions-reference).) | <ul><li>Deniz feneri servis istekleri oluşturun.</li></ul> |


## <a name="related-content"></a>İlgili içerik

[Genel bakış Microsoft 365 Lighthouse](m365-lighthouse-overview.md) (makale)\
[Microsoft 365 Lighthouse](m365-lighthouse-sign-up.md) (makale)\ için kaydolma
[Microsoft 365 Lighthouse SSS](m365-lighthouse-faq.yml) (makale)