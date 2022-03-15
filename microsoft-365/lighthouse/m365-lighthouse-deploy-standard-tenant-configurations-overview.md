---
title: Standart kiracı yapılandırmalarını dağıtmak için taban çizgilerini kullanmaya genel bakış
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
description: Standart Hizmet Sağlayıcıları (MSP) kullanarak Yönetilen Microsoft 365 Lighthouse için, standart kiracı yapılandırmalarını dağıtmak için taban çizgilerini kullanma hakkında bilgi öğrenin.
ms.openlocfilehash: 643bb962277d30caf8ea067b9276a5986af8914f
ms.sourcegitcommit: 8423f47fce3905a48db9daefe69c21c841da43a0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2022
ms.locfileid: "63504518"
---
# <a name="overview-of-using-baselines-to-deploy-standard-tenant-configurations"></a>Standart kiracı yapılandırmalarını dağıtmak için taban çizgilerini kullanmaya genel bakış 

Microsoft 365 Lighthouse temel, birden çok müşteri kiracısı genelinde güvenlik ayarlarını yönetebilirsiniz Microsoft 365 ve ölçeklendirilebilir bir yol sağlar. Taban çizgisi, kiracıların kullanıcılarını, cihazlarını ve verilerini güvende tutmak için temel güvenlik ilkelerini ve uyumluluk standartlarını dağıtan standart kiracı yapılandırmaları sağlar.

Deniz Feneri'nin içinde varsayılan taban çizgisini ve bu temelin dağıtım adımlarını görüntüebilirsiniz. Bir kiracıya taban çizgisi uygulamak için, sol gezinti **bölmesinde Kiracılar'ı** seçin ve sonra da bir kiracı seçin. Ardından, dağıtımı başlamak **için Dağıtım** planları sekmesine gidin.

## <a name="lighthouse-baseline"></a>Deniz feneri taban çizgisi

Deniz feneri taban çizgisi yapılandırmaları, yönetilen tüm kiracıların güvenli ve uyumlu olduğundan emin olmak için tasarlanmıştır. Tüm **kiracılara** uygulanan varsayılan temeli görüntülemek için sol gezinti bölmesinde Taban Çizgisi'ni seçin.  Varsayılan taban çizgisine dahil edilen dağıtım adımlarını görüntülemek için, **Temeli** görüntüle'yi seçerek varsayılan taban çizgisi sayfasını açın. Dağıtım ayrıntılarını ve kullanıcı etkisini görüntülemek için herhangi bir dağıtım adımlarını seçin.

:::image type="content" source="../media/m365-lighthouse-deploy-baselines/default-baseline-page.png" alt-text="Varsayılan taban çizgisi sayfasının ekran görüntüsü.":::

### <a name="default-lighthouse-configurations"></a>Varsayılan Deniz Feneri yapılandırmaları

| Temel yapılandırma | Açıklama |
|--|--|
| Yöneticiler için MFA gerektirme | Tüm yöneticiler için çok faktörlü kimlik doğrulaması gerektiren bir Koşullu Erişim ilkesi. Tüm bulut uygulamaları için gereklidir. Bu taban çizgisi hakkında daha fazla bilgi için bkz. [Koşullu Erişim: Tüm yöneticiler için MFA gerektirme](/azure/active-directory/conditional-access/howto-conditional-access-policy-admin-mfa).|
| Son kullanıcılar için MFA gerektirme | Tüm kullanıcılar için çok faktörlü kimlik doğrulaması gerektiren bir Koşullu Erişim ilkesi.  Tüm bulut uygulamaları için gereklidir. Bu taban çizgisi hakkında daha fazla bilgi için bkz. [Koşullu Erişim: Tüm kullanıcılar için MFA gerektirme](/azure/active-directory/conditional-access/howto-conditional-access-policy-all-users-mfa). |
| Eski kimlik doğrulamayı engelle | Eski istemci kimlik doğrulamasını engellemek için koşullu Erişim ilkesi. Bu taban çizgisi hakkında daha fazla bilgi için bkz. Koşullu [Erişimle Azure AD'nin eski kimlik doğrulamasını engelleme](/azure/active-directory/conditional-access/block-legacy-authentication).|
| Cihaz kaydı ayarlama | Kiracı cihazlarınızı postanıza kaydolmasına izin vermek için cihaz Microsoft Endpoint Manager. Bu, Azure Active Directory ile Microsoft Endpoint Manager arasında Otomatik Kayıt Azure Active Directory. Bu taban çizgisi hakkında daha fazla bilgi için bkz[. Birden fazla Windows ayarlama](/mem/intune/enrollment/windows-enroll). |
| Microsoft Defender Virüsten Koruma ve sonraki Windows 10 yapılandırma | Önceden yapılandırılmış sistem ayarlarına Windows cihazlar için cihaz yapılandırma Microsoft Defender Virüsten Koruma. Bu taban çizgisi hakkında daha fazla bilgi için bkz. [Intune'da Uç Nokta için Microsoft Defender'ı yapılandırma](/mem/intune/protect/advanced-threat-protection-configure).|
| Güvenlik Duvarı'nı güvenlik Windows 10 yapılandırma | İstenmeyen ve yetkisiz ağ trafiğini engelleyen cihazların güvenliğini sağlamak için güvenlik duvarı ilkesi. Bu taban çizgisi hakkında daha fazla bilgi için bkz[. Güvenlik Duvarı'nı yapılandırmaya Windows Defender yöntemleri](/windows/security/threat-protection/windows-firewall/best-practices-configuring).  |
| Uyumluluk ve sonrası için cihaz Windows 10 ilkesi yapılandırma | Temel Windows gereksinimlerini karşılamak için önceden yapılandırılmış ayarları olan en iyi cihaz ilkesi. Bu taban çizgisi hakkında daha fazla bilgi için bkz. [Koşullu Erişim: Uyumlu veya karma Azure AD'ye katılmış cihaz gerektirme](/azure/active-directory/conditional-access/howto-conditional-access-policy-compliant-device). |

## <a name="deployment-plans"></a>Dağıtım Planları

Her etkin kiracının, temel dağıtımdan gelen dağıtım adımlarını içeren bir Microsoft 365 Lighthouse vardır. Kiracının dağıtım planına erişmek için, Kiracılar sayfasındaki listeden etkin bir kiracı seçin ve  sonra da Dağıtım Planı **sekmesini** seçin.

:::image type="content" source="../media/m365-lighthouse-deploy-baselines/deployment-plan-tab.png" alt-text="Dağıtım Planı sekmesinin ekran görüntüsü.":::

Dağıtım Planı sekmesi aşağıdaki bilgileri içerir:


|Sütun  |Açıklama  |
|---------|---------|
|Dağıtım adımı     |  Dağıtım adımının açıklaması.       |
|Durum     |Dağıtım adımının durumu.         |
|Taban çizgisi     |Dağıtım adımının türetilen temeli.         |
|Kategori     | Dağıtım adımının Cihazlar, Kimlik veya Veri yönetimiyle ilişkili olup olmadığı.        |
|Son güncelleştirme    | Dağıtım adımının son güncelleştirme tarihi.        |


Dağıtım Planı sekmesi aşağıdaki seçenekleri de içerir:

- **Dışarı aktar:** Dağıtım adımı verilerini virgülle ayrılmış değerler (Excel) dosyasına dışarı .csv seçin.
- **Yenile:** En güncel dağıtım adımı verilerini almak için bunu seçin.
- **Arama:** Listede belirli bir dağıtım adımını hızla bulmak için anahtar sözcükleri girin.

## <a name="deployment-steps-and-processes"></a>Dağıtım adımları ve işlemleri

Her kiracının dağıtım planı, temel dağıtımdan Microsoft 365 Lighthouse içerir. Her dağıtım adımı, dağıtım adımının gereksinimlerini karşılamak için tamamlanması gereken bir veya daha fazla işlemden oluşur. Yeni bir kiracı etkin olduğunda, dağıtım adımları ve işlemleriyle ilişkilendirilmiş dağıtım etkinliklerini tamamlamanız gerekir.

Her dağıtım adımı için aşağıdaki eylemleri gerçekleştirebilirsiniz:

|Eylem  |Açıklama  |
|---------|---------|
| Paylaşma    |  Dağıtım Adımı'nın içeriğinin bir bağlantı veya e-postayla paylaşılıyor olması için olanak sağlar.    |
| Gözden geçirme ve dağıtma    |  Kullanıcının şunları şunları şunları sağlar: <ul><li>Desteklandığında, ayarları kiracıya dağıtmadan dağıtım adımını yapılandırma ayarlarıyla var olan ilkelerde yer alan ayarlarla karşılaştırın.<br>Aşağıdaki dağıtım adımları karşılaştırmayı destekler:</br><ul><li>Uyumluluk ve sonrası için cihaz Windows 10 ilkesi yapılandırma</li><li>Son kullanıcılar için MFA gerektirme</li><li>Yöneticiler için MFA gerektirme</li><li>Eski kimlik doğrulamayı engelle</li></ul></li> <li>Yapılandırma ayarlarını kiracıya dağıtın.</li></ul>**Not:** Ayarları kiracıya dağıtmadan karşılaştırma olanağını desteklemeen adımlar, yapılandırma ayarlarını gözden geçirmenizi ve bunları dağıtmanizi sağlar.|
| Eylem planı durumunu güncelleştirme    |  Kullanıcının, dağıtım adımı için eylem planının durumunu bildirmesini sağlar.      |

## <a name="related-content"></a>İlgili içerik

[Temel Microsoft 365 Lighthouse dağıtma](m365-lighthouse-deploy-baselines.md) (makale)\
[Ortak Koşullu Erişim ilkeleri](/azure/active-directory/conditional-access/concept-conditional-access-policy-common) (makale)\
[Microsoft 365 Lighthouse SSS](m365-lighthouse-faq.yml) (makale)
