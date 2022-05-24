---
title: Standart kiracı yapılandırmalarını dağıtmak için Microsoft 365 Lighthouse temellerini kullanmaya genel bakış
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
description: Microsoft 365 Lighthouse kullanan Yönetilen Hizmet Sağlayıcıları (MSP) için standart kiracı yapılandırmalarını dağıtmak için temelleri kullanma hakkında bilgi edinin.
ms.openlocfilehash: 11b8c5ad9adafa4cd6afb6bb4cd19861118e447c
ms.sourcegitcommit: 725a92b0b1555572b306b285a0e7a7614d34e5e5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/24/2022
ms.locfileid: "65647699"
---
# <a name="overview-of-using-microsoft-365-lighthouse-baselines-to-deploy-standard-tenant-configurations"></a>Standart kiracı yapılandırmalarını dağıtmak için Microsoft 365 Lighthouse temellerini kullanmaya genel bakış 

Microsoft 365 Lighthouse temelleri, birden çok müşteri kiracısı arasında Microsoft 365 güvenlik ayarlarını yönetmeniz için yinelenebilir ve ölçeklenebilir bir yol sağlar. Temeller, kiracılarınızın kullanıcılarını, cihazlarını ve verilerini güvenli tutan temel güvenlik ilkelerini ve uyumluluk standartlarını dağıtan standart kiracı yapılandırmaları sağlar.

Varsayılan temeli ve dağıtım adımlarını Lighthouse'un içinden görüntüleyebilirsiniz. Kiracıya taban çizgisi uygulamak için sol gezinti bölmesinde **Kiracılar'ı** seçin ve ardından bir kiracı seçin. Ardından dağıtıma başlamak için **Dağıtım planları** sekmesine gidin.

## <a name="lighthouse-baseline"></a>Deniz feneri temeli

Lighthouse temel yapılandırmaları, tüm yönetilen kiracıların güvenli ve uyumlu olduğundan emin olmak için tasarlanmıştır. Tüm **kiracılar** için geçerli olan varsayılan temeli görüntülemek için sol gezinti bölmesinden Temeller'i seçin.  Varsayılan taban çizgisine dahil edilen dağıtım adımlarını görüntülemek için **Temeli görüntüle'yi** seçerek varsayılan temel sayfasını açın. Dağıtım ayrıntılarını ve kullanıcı etkisini görüntülemek için dağıtım adımlarından herhangi birini seçin.

:::image type="content" source="../media/m365-lighthouse-deploy-baselines/default-baseline-page.png" alt-text="Varsayılan temel sayfasının ekran görüntüsü.":::

### <a name="default-lighthouse-configurations"></a>Varsayılan Lighthouse yapılandırmaları

| Temel yapılandırma | Açıklama |
|--|--|
| Yöneticiler için MFA gerektir | Tüm yöneticiler için çok faktörlü kimlik doğrulaması gerektiren bir Koşullu Erişim ilkesi. Tüm bulut uygulamaları için gereklidir. Bu temel hakkında daha fazla bilgi için bkz [. Koşullu Erişim: Tüm yöneticiler için MFA gerektirme](/azure/active-directory/conditional-access/howto-conditional-access-policy-admin-mfa).|
| Son kullanıcılar için MFA gerektir | Tüm kullanıcılar için çok faktörlü kimlik doğrulaması gerektiren bir Koşullu Erişim ilkesi.  Tüm bulut uygulamaları için gereklidir. Bu temel hakkında daha fazla bilgi için bkz [. Koşullu Erişim: Tüm kullanıcılar için MFA gerektirme](/azure/active-directory/conditional-access/howto-conditional-access-policy-all-users-mfa). |
| Eski kimlik doğrulamasını engelle | Eski istemci kimlik doğrulamasını engelleyen bir Koşullu Erişim ilkesi. Bu temel hakkında daha fazla bilgi için bkz[. Koşullu Erişim ile Azure AD için eski kimlik doğrulamasını engelleme](/azure/active-directory/conditional-access/block-legacy-authentication).|
| Cihaz kaydını ayarlama | Kiracı cihazlarınızın Microsoft Endpoint Manager kaydolmasına izin vermek için cihaz kaydı. Bu, Azure Active Directory ve Microsoft Endpoint Manager arasında Otomatik Kayıt ayarlanarak yapılır. Bu temel hakkında daha fazla bilgi için bkz. [Windows cihazlar için kaydı ayarlama](/mem/intune/enrollment/windows-enroll). |
| kurulum Exchange Online Protection ve Office 365 için Microsoft Defender | Önerilen istenmeyen posta önleme, kötü amaçlı yazılımdan koruma, kimlik avı önleme, güvenli bağlantılar ve güvenli ek ilkelerini kiracılarınıza Exchange Online posta kutularına uygulama ilkesi. |
| Windows 10 ve üzeri için Microsoft Defender Virüsten Koruma yapılandırma | Önceden yapılandırılmış Microsoft Defender Virüsten Koruma ayarlarına sahip Windows cihazlar için bir cihaz yapılandırma profili. Bu temel hakkında daha fazla bilgi için bkz[. Intune'da Uç Nokta için Microsoft Defender yapılandırma](/mem/intune/protect/advanced-threat-protection-configure).|
| Windows 10 ve üzeri için Microsoft Defender Güvenlik Duvarı yapılandırma | İstenmeyen ve yetkisiz ağ trafiğini engelleyerek cihazların güvenliğini sağlamaya yardımcı olan bir güvenlik duvarı ilkesi. Bu temel hakkında daha fazla bilgi için bkz. [Windows Defender Güvenlik Duvarı yapılandırmaya yönelik en iyi yöntemler](/windows/security/threat-protection/windows-firewall/best-practices-configuring).  |
| Windows 10 ve üzeri için cihaz uyumluluk ilkesi yapılandırma | Temel uyumluluk gereksinimlerini karşılamak için önceden yapılandırılmış ayarlara sahip bir Windows cihaz ilkesi. Bu temel hakkında daha fazla bilgi için bkz[. Koşullu Erişim: Uyumlu veya karma Azure AD birleştirilmiş cihaz gerektirme](/azure/active-directory/conditional-access/howto-conditional-access-policy-compliant-device). |

## <a name="deployment-plans"></a>Dağıtım Planları

Her etkin kiracının, Microsoft 365 Lighthouse temelden dağıtım adımlarını içeren bir dağıtım planı vardır. Kiracının dağıtım planına erişmek için **Kiracılar** sayfasındaki listeden etkin bir kiracı seçin ve ardından **Dağıtım Planı** sekmesini seçin.

:::image type="content" source="../media/m365-lighthouse-deploy-baselines/deployment-plan-tab.png" alt-text="Dağıtım Planı sekmesinin ekran görüntüsü.":::

Dağıtım Planı sekmesi aşağıdaki bilgileri içerir:


|Sütun  |Açıklama  |
|---------|---------|
|Dağıtım adımı     |  Dağıtım adımının açıklaması.       |
|Durum     |Dağıtım adımının durumu.         |
|Temel     |Dağıtım adımının türetildiği temel.         |
|Kategori     | Dağıtım adımının Cihazları, Kimliği veya Verileri yönetmeyle ilişkili olup olmadığı.        |
|Son güncelleştirme    | Dağıtım adımının son güncelleştirildiği tarih.        |


Dağıtım Planı sekmesi aşağıdaki seçenekleri de içerir:

- **Ihracat:** Dağıtım adımı verilerini virgülle ayrılmış Excel değerler (.csv) dosyasına aktarmak için seçin.
- **Yenileme:** En güncel dağıtım adımı verilerini almak için öğesini seçin.
- **Arama:** Listede belirli bir dağıtım adımını hızla bulmak için anahtar sözcükler girin.

## <a name="deployment-steps-and-processes"></a>Dağıtım adımları ve işlemleri

Her kiracının dağıtım planı, Microsoft 365 Lighthouse temelden dağıtım adımlarını içerir. Her dağıtım adımı, tamamlanması gereken bir veya daha fazla işlem içerir. Yeni bir kiracı etkin hale geldiğinde, dağıtım adımları ve işlemleriyle ilişkili dağıtım etkinliklerini tamamlamanız gerekir.

Her dağıtım adımı için aşağıdaki eylemleri gerçekleştirebilirsiniz:

|Eylem  |Açıklama  |
|---------|---------|
| Paylaşma    |  Dağıtım Adımı'nın içeriğinin bir bağlantı veya e-posta ile paylaşılabilmesini sağlar.    |
| Gözden geçirme ve dağıtma    |  Kullanıcının şunları etkinleştirmesini sağlar: <ul><li>Desteklendiğinde, ayarları kiracıya dağıtmadan dağıtım adımındaki yapılandırma ayarlarını mevcut ilkelerdeki ayarlarla karşılaştırın.<br>Aşağıdaki dağıtım adımları karşılaştırmayı destekler:</br><ul><li>Windows 10 ve üzeri için cihaz uyumluluk ilkesi yapılandırma</li><li>Son kullanıcılar için MFA gerektir</li><li>Yöneticiler için MFA gerektir</li><li>Eski kimlik doğrulamasını engelle</li></ul></li> <li>Yapılandırma ayarlarını kiracıya dağıtın.</li></ul>**Not:** Ayarları kiracıya dağıtmadan karşılaştırma özelliğini desteklemeyen adımlar, yapılandırma ayarlarını gözden geçirmenize ve dağıtmanıza olanak tanır.|
| Eylem planı durumunu güncelleştirme    |  Kullanıcının dağıtım adımı için eylem planının durumunu bildirmesini sağlar.      |

## <a name="related-content"></a>İlgili içerik

[Microsoft 365 Lighthouse temellerini dağıtma](m365-lighthouse-deploy-baselines.md) (makale)\
[Yaygın Koşullu Erişim ilkeleri](/azure/active-directory/conditional-access/concept-conditional-access-policy-common) (makale)\
[Microsoft 365 Lighthouse SSS](m365-lighthouse-faq.yml) (makale)
