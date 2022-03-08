---
title: Denetim günlüklerini gözden geçirme
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
description: Yönetilen Hizmet Sağlayıcıları (MSP) Microsoft 365 Lighthouse, denetim günlüklerinin nasıl gözden geçiril olduğunu öğrenin.
ms.openlocfilehash: e16f6eb83d1fdc9f5aea2fdc6463959cc07e5650
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63329453"
---
# <a name="review-audit-logs"></a>Denetim günlüklerini gözden geçirme

Microsoft 365 Lighthouse, Deniz Feneri veya diğer hizmetlerde değişiklik oluşturan denetim günlükleri Microsoft 365 içerir. Tüm denetim olaylarını oluşturabilir, düzenleyebilir, silebilir, atayabilirsiniz ve uzaktan eylemlerin hepsi gözden geçirebilirsiniz. Varsayılan olarak, tüm müşteriler için denetim etkinleştirilir. Devre dışı bırakılamaz.

## <a name="before-you-begin"></a>Başlamadan önce

Denetim günlüklerini görüntülemek için, aşağıdaki izinlerden birini gerekir:

- Azure Active Directory (Azure AD) rolü - İş ortağı kiracısı Genel Yöneticisi

- Microsoft İş Ortağı Merkezi rolü - Yönetici Temsilcisi

## <a name="review-audit-logs"></a>Denetim günlüklerini gözden geçirme

1. Deniz Feneri'nin sol gezinti bölmesinde Denetim **günlükleri'ni seçin**.

    > [!NOTE]
    > Yeni günlüklerin görmek 1 saat kadar zaman alabiliyor. En son değişiklikleri görmek için ilgili hizmete gidin.

2. Gerektiğinde aşağıdaki seçenekleri kullanarak günlükleri filtreleyebilirsiniz:

    - **Tarih aralığı** - Önceki ay, hafta veya gün.
    - **Kiracılar** - Kiracı etiketleri veya müşteri kiracı adları.
    - **Etkinlik** : Microsoft 365 karşılık gelen etkinlik türünü gösterir. Daha fazla bilgi için Etkinlikler [tablosuna](#activities) bakın.
    - **Başlatan** - Who başlatan.

3. İstek gövdesiyle birlikte tüm ayrıntıları görmek için listeden bir **günlük** seçin.

    Günlük verilerini virgülle ayrılmış değerler (veri) dosyasına dışarı .csv dışarı aktar'ı **seçin**.

## <a name="activities"></a>Etkinlikler

Aşağıdaki tabloda, Deniz Feneri denetim günlüklerinde yakalanan etkinlikler listelanır. Yeni eylemler oluşturulduktan sonra liste değişebilir. Hangi eylemin başlatıldığını görmek için denetim günlüğünde listelenen etkinliği kullanabilirsiniz.<br><br>

| Etkinlik adı | Deniz Feneri'nde alan | Başlatılan eylem | Hizmet etki edildi |
|--|--|--|--|
| **uygulama** veya **dağıtma** | Kiracılar | Dağıtım planı uygulama | Azure AD, Microsoft Endpoint Manager (MEM) |
| **assignTag** | Kiracılar | Müşteriden etiket uygulama | Deniz Feneri |
| **changeDeploymentStatus veya** **assign** | Kiracılar | Dağıtım planı için eylem planı durumunu güncelleştirme | Deniz Feneri |
| **managedTenantOperations** | Kiracılar | Dağıtım planıyla ilgili bilgileri görüntüleme | Azure AD |
| **offboardTenant** | Kiracılar | Müşteriyi devre dışı bırakma | Deniz Feneri |
| **resetTenantOnboardingStatus** | Kiracılar | Müşteriyi yeniden devre dışı bırakılır | Deniz Feneri |
| **tenantTags** | Kiracılar | Etiket oluşturma veya silme | Deniz Feneri |
| **tenantCustomizedInformation** | Kiracılar | Müşteri web sitesini veya iletişim bilgilerini oluşturma, güncelleştirme veya silme | Deniz Feneri |
| **unassignTag** | Kiracılar | Müşteriden etiket kaldırma | Deniz Feneri |
| **doğrulama** | Kiracılar | Dağıtım planını test etmek | Azure AD |
| **blockUserSignin** | Kullanıcılar | Oturum açma engelleme | Azure AD |
| **confirmUsersCompromised** | Kullanıcılar | Bir kullanıcının güvenliği ihlal edilmiş olduğunu onaylama | Azure AD |
| **dismissUsersRisk** | Kullanıcılar | Kullanıcı riskini yok sayma | Azure AD |
| **resetUserPassword** | Kullanıcılar | Parolayı sıfırlayın | Azure AD |
| **getConditionalAccessPolicies** | Kullanıcılar | MFA gerektiren CA ilkelerini görüntüleme | Azure AD |
| **getTenantIDToTenantNameMap** | Kullanıcılar | Kimlik arama | Azure AD |
| **getUsers** | Kullanıcılar | Kullanıcı arama | Azure AD |
| **getUsersWithoutMfa** | Kullanıcılar | MFA için kayıtlı olan kullanıcıları görüntüleme | Azure AD |
| **getSsprEnabledButNotRegisteredUsers** | Kullanıcılar | SSPR için kayıtlı olan kullanıcıları görüntüleme | Azure AD |
| **setCustomerSecurityDefaultsEnabledStatus** | Kullanıcılar | Çok faktörlü kimlik doğrulamasını (MFA) güvenlik varsayılanları ile etkinleştirme | Azure AD |
|**getCompliancePolicyInfo** | Cihazlar | İlkeyi görüntüleme | MEM
|**getDeviceCompliancePolicyStates** | Cihazlar | İlke durumları görüntüleme | MEM
|**getDeviceCompliancePolicySettingStates** | Cihazlar | Uyumlu olmayan ayarları görüntüleme | MEM
|**getDeviceCompliancePolicySettingStateSummaries** | Cihazlar | Uyumlu olmayan cihazları görüntüleme | MEM
|**getTenantsDeviceCompliancePolicies** | Cihazlar | İlkeleri karşılaştırma | MEM
| **Device'i yeniden başlatma** | Cihazlar | Yeniden başlatma | MEM |
| **syncDevice** | Cihazlar | Eşitleme | MEM |
| **rebootNow** | Tehdit yönetimi | Yeniden Başlatma | MEM |
| **reprovision** | Windows 365 | Sağlamayı yeniden dene | Windows 365 |
| **getDeviceUserInfo** | Tehdit yönetimi | Yönetilen cihaz kullanıcı bilgilerini görüntüleme  | MEM |
| **getManagedDevice**, **remoteActionAudits** veya **deviceActionResults** | Tehdit yönetimi | Yönetilen cihaz bilgilerini görüntüleme  | MEM |
| **windowsDefenderScanFull** | Tehdit yönetimi | Tam tarama | MEM |
| **windowsDefenderScan** | Tehdit yönetimi | Hızlı tarama | MEM |
| **windowsDefenderUpdateSignatures** | Tehdit yönetimi | Virüsten koruma yazılımını güncelleştirme | MEM |

## <a name="next-steps"></a>Sonraki adımlar

Daha fazla bilgiye ihtiyacınız varsa, daha fazla denetim Graph erişmek için Microsoft Graph API'sini kullanın. Daha fazla bilgi için bkz[. Kullanıcı API'sini kullanarak çok kiracılı yönetim Microsoft 365 Lighthouse genel bakış](/graph/managedtenants-concept-overview).

## <a name="related-content"></a>İlgili içerik

[Microsoft 365 Lighthouse SSS](m365-lighthouse-faq.yml) (makale)
