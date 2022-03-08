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
ms.openlocfilehash: f59ca686892e0b20ce5e9ffb6d62859ce8079896
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63323157"
---
# <a name="overview-of-using-baselines-to-deploy-standard-tenant-configurations"></a>Standart kiracı yapılandırmalarını dağıtmak için taban çizgilerini kullanmaya genel bakış 

Microsoft 365 Lighthouse temel, birden çok müşteri kiracısı genelinde güvenlik ayarlarını yönetebilirsiniz Microsoft 365 ve ölçeklendirilebilir bir yol sağlar. Taban çizgisi ayrıca, kullanıcıların, cihazların ve verilerin güvenliğini sağlayın yapılandırmalarında temel güvenlik ilkelerini ve kiracı uyumluluk standartlarını izlemeye yardımcı olur.

Yönetilen Hizmet Sağlayıcılarının (MSP) güvenliğin müşteri tarafından benimsenmesine yardımcı olmak için tasarlanan Deniz Feneri, standart bir taban çizgisi parametreleri kümesi ve hizmetlerin önceden tanımlanmış Microsoft 365 sunar. Bu güvenlik yapılandırmaları kiracıların güvenlik ve uyumluluk Microsoft 365 ölçülebilir.

Deniz Feneri'nin içinde varsayılan taban çizgisini ve bu temelin dağıtım adımlarını görüntüebilirsiniz. Bir kiracıya taban çizgisi uygulamak için, sol gezinti **bölmesinde Kiracılar'ı** seçin ve sonra da bir kiracı seçin. Ardından, Dağıtım planları **sekmesine gidin** ve taban çizgisini gerçekleştirin.

## <a name="default-baseline-security-templates"></a>Varsayılan temel güvenlik şablonları

Deniz feneri varsayılan güvenlik taban çizgisi yapılandırmaları, yönetilen tüm kiracıların güvenli ve uyumlu olduğundan emin olmak için tasarlanmıştır.

Aşağıdaki tabloda yer alan taban çizgisi yapılandırmaları, Deniz Feneri varsayılan temeli ile standarttır.<br><br>

| Temel yapılandırma | Açıklama |
|--|--|
| Yöneticiler için MFA gerektirme | Tüm yöneticiler için çok faktörlü kimlik doğrulaması gerektiren bir Koşullu Erişim ilkesi. Tüm bulut uygulamaları için gereklidir. Bu taban çizgisi hakkında daha fazla bilgi için bkz. [Koşullu Erişim: Tüm yöneticiler için MFA gerektirme](/azure/active-directory/conditional-access/howto-conditional-access-policy-admin-mfa).|
| Son kullanıcılar için MFA gerektirme | Tüm kullanıcılar için çok faktörlü kimlik doğrulaması gerektiren bir Koşullu Erişim ilkesi.  Tüm bulut uygulamaları için gereklidir. Bu taban çizgisi hakkında daha fazla bilgi için bkz. [Koşullu Erişim: Tüm kullanıcılar için MFA gerektirme](/azure/active-directory/conditional-access/howto-conditional-access-policy-all-users-mfa). |
| Eski kimlik doğrulamayı engelle | Eski istemci kimlik doğrulamasını engellemek için koşullu Erişim ilkesi. Bu taban çizgisi hakkında daha fazla bilgi için bkz. Koşullu [Erişimle Azure AD'nin eski kimlik doğrulamasını engelleme](/azure/active-directory/conditional-access/block-legacy-authentication).|
| Cihaz kaydı ayarlama | Kiracı cihazlarınızı postanıza kaydolmasına izin vermek için cihaz Microsoft Endpoint Manager. Bu, Azure Active Directory ile Microsoft Endpoint Manager arasında Otomatik Kayıt Azure Active Directory. Bu taban çizgisi hakkında daha fazla bilgi için bkz[. Birden fazla Windows ayarlama](/mem/intune/enrollment/windows-enroll). |
| Microsoft Defender Virüsten Koruma ve sonraki Windows 10 yapılandırma | Önceden yapılandırılmış sistem ayarlarına Windows cihazlar için cihaz yapılandırma Microsoft Defender Virüsten Koruma. Bu taban çizgisi hakkında daha fazla bilgi için bkz. [Intune'da Uç Nokta için Microsoft Defender'ı yapılandırma](/mem/intune/protect/advanced-threat-protection-configure).|
| Güvenlik Duvarı'nı güvenlik Windows 10 yapılandırma | İstenmeyen ve yetkisiz ağ trafiğini engelleyen cihazların güvenliğini sağlamak için güvenlik duvarı ilkesi. Bu taban çizgisi hakkında daha fazla bilgi için bkz[. Güvenlik Duvarı'nı yapılandırmaya Windows Defender yöntemleri](/windows/security/threat-protection/windows-firewall/best-practices-configuring).  |
| Uyumluluk ve sonrası için cihaz Windows 10 ilkesi yapılandırma | Temel Windows gereksinimlerini karşılamak için önceden yapılandırılmış ayarları olan en iyi cihaz ilkesi. Bu taban çizgisi hakkında daha fazla bilgi için bkz. [Koşullu Erişim: Uyumlu veya karma Azure AD'ye katılmış cihaz gerektirme](/azure/active-directory/conditional-access/howto-conditional-access-policy-compliant-device). |


## <a name="related-content"></a>İlgili içerik

[Temel Microsoft 365 Lighthouse dağıtma](m365-lighthouse-deploy-baselines.md) (makale)\
[Ortak Koşullu Erişim ilkeleri](/azure/active-directory/conditional-access/concept-conditional-access-policy-common) (makale)\
[Microsoft 365 Lighthouse SSS](m365-lighthouse-faq.yml) (makale)
