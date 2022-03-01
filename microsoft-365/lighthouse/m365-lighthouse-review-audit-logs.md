---
title: Denetim günlüklerini gözden geçirme
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
description: Yönetilen Hizmet Sağlayıcıları (MSP) Microsoft 365 Lighthouse, denetim günlüklerinin nasıl gözden geçiril olduğunu öğrenin.
ms.openlocfilehash: 69eb057c0b6a7daf835ec613b7d386e1a7fbfbaa
ms.sourcegitcommit: 6e43aeff217afe97876137b1ead8df26db6e9937
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/16/2022
ms.locfileid: "63015314"
---
# <a name="review-audit-logs"></a>Denetim günlüklerini gözden geçirme

> [!NOTE]
> Bu makalede açıklanan özellikler Önizleme'dedir, değişebilir ve yalnızca gereksinimleri karşılayacak iş ortakları tarafından [kullanılabilir](m365-lighthouse-requirements.md). Henüz oturum açmadıysanız Microsoft 365 Lighthouse için [kaydolma'ya Microsoft 365 Lighthouse](m365-lighthouse-sign-up.md).

Microsoft 365 Lighthouse, Deniz Feneri veya diğer hizmetlerde değişiklik oluşturan denetim günlükleri Microsoft 365 içerir. Tüm denetim olaylarını oluşturabilir, düzenleyebilir, silebilir, atayabilirsiniz ve uzaktan eylemlerin hepsi gözden geçirebilirsiniz. Varsayılan olarak, tüm müşteriler için denetim etkinleştirilir. Devre dışı bırakılamaz.

## <a name="before-you-begin"></a>Başlamadan önce

Denetim günlüklerini görüntülemek için, aşağıdaki izinlerden birini gerekir:

- Azure Active Directory (Azure AD) rolü - İş ortağı kiracısı Genel Yöneticisi

- Microsoft İş Ortağı Merkezi rolü - Yönetici temsilcisi

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
| **uygula** | Kiracılar | Dağıtım planı uygulama | Azure AD, Microsoft Endpoint Manager (MEM) |
| **assignTag** | Kiracılar | Müşteriden etiket uygulama | Deniz Feneri |
| **changeDeploymentStatus** | Kiracılar | Dağıtım planı için eylem planı durumu | Deniz Feneri |
| **offboardTenant** | Kiracılar | Müşteriyi devre dışı bırakma | Deniz Feneri |
| **resetTenantOnboardingStatus** | Kiracılar | Müşteriyi yeniden devre dışı bırakılır | Deniz Feneri |
| **tenantTags** | Kiracılar | Etiket oluşturma veya silme | Deniz Feneri |
| **tenantCustomizedInformation** | Kiracılar | Müşteri web sitesini veya iletişim bilgilerini oluşturma, güncelleştirme veya silme | Deniz Feneri |
| **unassignTag** | Kiracılar | Müşteriden etiket kaldırma | Deniz Feneri |
| **blockUserSignin** | Kullanıcılar | Oturum açma engelleme | Azure AD |
| **confirmUsersCompromised** | Kullanıcılar | Bir kullanıcının güvenliği ihlal edilmiş olduğunu onaylama | Azure AD |
| **dismissUsersRisk** | Kullanıcılar | Kullanıcı riskini yok sayma | Azure AD |
| **resetUserPassword** | Kullanıcılar | Parolayı sıfırlayın | Azure AD |
| **setCustomerSecurityDefaultsEnabledStatus** | Kullanıcılar | Çok faktörlü kimlik doğrulamasını (MFA) güvenlik varsayılanları ile etkinleştirme | Azure AD |
| **Device'i yeniden başlatma** | Cihazlar | Yeniden başlatma | MEM |
| **syncDevice** | Cihazlar | Eşitleme | MEM |
| **rebootNow** | Tehdit yönetimi | Yeniden Başlatma | MEM |
| **reprovision** | Windows 365 | Sağlamayı yeniden dene | Windows 365 |
| **windowsDefenderScanFull** | Tehdit yönetimi | Tam tarama | MEM |
| **windowsDefenderScan** | Tehdit yönetimi | Hızlı tarama | MEM |
| **windowsDefenderUpdateSignatures** | Tehdit yönetimi | Virüsten koruma yazılımını güncelleştirme | MEM |

## <a name="next-steps"></a>Sonraki adımlar

Daha fazla bilgiye ihtiyacınız varsa, daha fazla denetim Graph erişmek için Microsoft Graph API'sini kullanın. Daha fazla bilgi için bkz[. Kullanıcı API'sini kullanarak çok kiracılı yönetim Microsoft 365 Lighthouse genel bakış](/graph/managedtenants-concept-overview).

## <a name="related-content"></a>İlgili içerik

[Microsoft 365 Lighthouse SSS](m365-lighthouse-faq.yml) (makale)
