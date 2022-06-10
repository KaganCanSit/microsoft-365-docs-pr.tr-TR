---
title: Microsoft 365 Lighthouse'de denetim günlüklerini gözden geçirme
f1.keywords: CSH
ms.author: sharik
author: SKjerland
manager: scotv
ms-reviewer: vivkuma
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
description: Microsoft 365 Lighthouse kullanan Yönetilen Hizmet Sağlayıcıları (MSP) için denetim günlüklerini gözden geçirmeyi öğrenin.
ms.openlocfilehash: a357d6d4383fb967b09d1ce3dc1be68d7fd2ca4f
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/10/2022
ms.locfileid: "66017520"
---
# <a name="review-audit-logs-in-microsoft-365-lighthouse"></a>Microsoft 365 Lighthouse'de denetim günlüklerini gözden geçirme

Microsoft 365 Lighthouse denetim günlükleri Lighthouse veya diğer Microsoft 365 hizmetlerinde değişiklik oluşturan eylemleri kaydeder. Oluştur, düzenle, sil, ata ve uzak eylemlerin tümü gözden geçirebileceğiniz denetim olayları oluşturur. Varsayılan olarak, denetim tüm müşteriler için etkindir. Devre dışı bırakılamaz.

## <a name="before-you-begin"></a>Başlamadan önce

Denetim günlüklerini görüntülemek için aşağıdaki izinlerden birine sahip olmanız gerekir:

- Azure Active Directory (Azure AD) rolü - İş ortağı kiracısının Genel Yöneticisi

- Microsoft İş Ortağı Merkezi rolü - Yönetici Aracısı

## <a name="review-audit-logs"></a>Denetim günlüklerini gözden geçirme

1. Lighthouse'un sol gezinti bölmesinde **Denetim günlükleri'ni** seçin.

    > [!NOTE]
    > Yeni günlüklerin görülmesi 1 saat kadar sürebilir. En son değişiklikleri görmek için ilgili hizmete gidin.

2. Aşağıdaki seçenekleri kullanarak günlükleri gerektiği gibi filtreleyin:

    - **Tarih aralığı** - Önceki ay, hafta veya gün.
    - **Kiracılar** - Kiracı etiketleri veya müşteri kiracı adları.
    - **Etkinlik** - gerçekleştirilen eyleme karşılık gelen etkinlik türü Microsoft 365. Daha fazla bilgi için [Etkinlikler](#activities) tablosuna bakın.
    - **Tarafından başlatıldı** - eylemi Who başlattı.

3. **İstek** gövdesi de dahil olmak üzere tüm ayrıntıları görmek için listeden bir günlük seçin.

    Günlük verilerini virgülle ayrılmış değerler (.csv) dosyasına aktarmak için **Dışarı Aktar'ı** seçin.

## <a name="activities"></a>Faaliyetleri

Aşağıdaki tabloda Lighthouse denetim günlüklerinde yakalanan etkinlikler listelenir. Yeni eylemler oluşturulduktan sonra liste değiştirilebilir. Hangi eylemin başlatıldığını görmek için denetim günlüğünde listelenen etkinliği kullanabilirsiniz.<br><br>

| Etkinlik adı | Lighthouse'da alan | Eylem başlatıldı | Hizmet etkilendi |
|--|--|--|--|
| **uygulama** veya **dağıtma** | Kiracı | Dağıtım planı uygulama | Azure AD, Microsoft Endpoint Manager (MEM) |
| **assignTag** | Kiracı | Müşteriden etiket uygulama | Lighthouse |
| **changeDeploymentStatus** veya **assign** | Kiracı | Dağıtım planı için eylem planı durumunu güncelleştirme | Lighthouse |
| **managedTenantOperations** | Kiracı | Dağıtım planıyla ilgili bilgileri görüntüleme | Azure AD |
| **offboardTenant** | Kiracı | Müşteriyi devre dışı bırakma | Lighthouse |
| **resetTenantOnboardingStatus** | Kiracı | Müşteriyi yeniden etkinleştirme | Lighthouse |
| **tenantTags** | Kiracı | Etiket oluşturma veya silme | Lighthouse |
| **tenantCustomizedInformation** | Kiracı | Müşteri web sitesi veya iletişim bilgilerini oluşturma, güncelleştirme veya silme | Lighthouse |
| **unassignTag** | Kiracı | Müşteriden etiket kaldırma | Lighthouse |
| **Doğrulamak** | Kiracı | Dağıtım planını test edin | Azure AD |
| **blockUserSignin** | Kullanıcılar | Oturum açmayı engelle | Azure AD |
| **confirmUsersCompromised** | Kullanıcılar | Bir kullanıcının gizliliğinin tehlikeye girdiğini onaylama | Azure AD |
| **dismissUsersRisk** | Kullanıcılar | Kullanıcı riskini kapatma | Azure AD |
| **resetUserPassword** | Kullanıcılar | Parolayı sıfırlayın | Azure AD |
| **getConditionalAccessPolicies** | Kullanıcılar | MFA gerektiren CA ilkelerini görüntüleme | Azure AD |
| **getTenantIDToTenantNameMap** | Kullanıcılar | Kimlikleri arama | Azure AD |
| **getUsers** | Kullanıcılar | Kullanıcı arama | Azure AD |
| **getUsersWithoutMfa** | Kullanıcılar | MFA için kayıtlı olmayan kullanıcıları görüntüleme | Azure AD |
| **getSsprEnabledButNotRegisteredUsers** | Kullanıcılar | SSPR için kayıtlı olmayan kullanıcıları görüntüleme | Azure AD |
| **setCustomerSecurityDefaultsEnabledStatus** | Kullanıcılar | Güvenlik varsayılanlarıyla çok faktörlü kimlik doğrulamasını (MFA) etkinleştirme | Azure AD |
|**getCompliancePolicyInfo** | Aygıtları | İlke görüntüleme | MEM
|**getDeviceCompliancePolicyStates** | Aygıtları | İlke durumlarını görüntüleme | MEM
|**getDeviceCompliancePolicySettingStates** | Aygıtları | Uyumlu olmayan ayarları görüntüleme | MEM
|**getDeviceCompliancePolicySettingStateSummaries** | Aygıtları | Uyumlu olmayan cihazları görüntüleme | MEM
|**getTenantsDeviceCompliancePolicies** | Aygıtları | İlkeleri karşılaştırma | MEM
| **restartCihaz** | Aygıtları | Yeniden başlatma | MEM |
| **syncDevice** | Aygıtları | Eşitleme | MEM |
| **rebootNow** | Tehdit yönetimi | Yeni -den başlatma | MEM |
| **yeniden sağlama** | Windows 365 | Sağlamayı yeniden deneyin | Windows 365 |
| **getDeviceUserInfo** | Tehdit yönetimi | Yönetilen cihaz kullanıcı bilgilerini görüntüleme  | MEM |
| **getManagedDevice**, **remoteActionAudits** veya **deviceActionResults** | Tehdit yönetimi | Yönetilen cihaz bilgilerini görüntüleme  | MEM |
| **windowsDefenderScanFull** | Tehdit yönetimi | Tam tarama | MEM |
| **windowsDefenderScan** | Tehdit yönetimi | Hızlı tarama | MEM |
| **windowsDefenderUpdateSignatures** | Tehdit yönetimi | Virüsten korumayı güncelleştirme | MEM |

## <a name="next-steps"></a>Sonraki adımlar

Gerekirse daha fazla denetim olayına erişmek için Microsoft Graph API kullanın. Daha fazla bilgi için bkz. [Microsoft 365 Lighthouse API'sini kullanarak çok kiracılı yönetime genel bakış](/graph/managedtenants-concept-overview).

## <a name="related-content"></a>İlgili içerik

[Microsoft 365 Lighthouse SSS](m365-lighthouse-faq.yml) (makale)\
[Microsoft 365 Lighthouse'de Azure Active Directory rollerinizi görüntüleme](m365-lighthouse-view-your-roles.md) (makale)