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
ms.openlocfilehash: 23ebc0d0562cf06bd92456e18c0833a61c564673
ms.sourcegitcommit: bae72428d229827cba4c807d9cd362417afbcccb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/02/2022
ms.locfileid: "63014268"
---
# <a name="overview-of-using-baselines-to-deploy-standard-tenant-configurations"></a>Standart kiracı yapılandırmalarını dağıtmak için taban çizgilerini kullanmaya genel bakış 

> [!NOTE]
> Bu makalede açıklanan özellikler Önizleme'dedir, değişebilir ve yalnızca gereksinimleri karşılayacak iş ortakları tarafından [kullanılabilir](m365-lighthouse-requirements.md). Henüz oturum açmadıysanız Microsoft 365 Lighthouse için [kaydolma'ya Microsoft 365 Lighthouse](m365-lighthouse-sign-up.md).

Microsoft 365 Lighthouse taban çizgisi, birden çok müşteri kiracısı genelinde güvenlik ayarlarını değerlendirmeniz ve yönetmeniz için Microsoft 365 ölçeklendirilebilir bir yol sağlar. Taban çizgisi ayrıca, kullanıcıların, cihazların ve verilerin güvenliğini sağlayın yapılandırmalarında temel güvenlik ilkelerini ve kiracı uyumluluk standartlarını izlemeye yardımcı olur.

İş ortaklarının güvenliği kendi hızıyla benimsemelerine yardımcı olmak için tasarlanan Deniz Feneri, standart bir taban çizgisi parametreleri kümesi ve hizmetlerin önceden tanımlanmış Microsoft 365 sunar. Bu güvenlik yapılandırmaları kiracıların güvenlik ve uyumluluk Microsoft 365 ölçülebilir.

Deniz Feneri'nin içinde varsayılan taban çizgisini ve bu temelin dağıtım adımlarını görüntüebilirsiniz. Kiracıya taban çizgilerini uygulamak için, sol gezinti **bölmesinde Kiracılar'ı** seçin ve sonra da bir kiracı seçin. Ardından, Dağıtım planları **sekmesine gidin** ve istediğiniz temeli gerçekleştirin.

## <a name="standard-baseline-security-templates"></a>Standart taban çizgisi güvenlik şablonları

Deniz feneri standart temel yapılandırmaları, güvenlik iş yükleri için tüm yönetilen kiracıların kabul edilebilir bir güvenlik kapsamı ve uyumluluğu durumuna ulaşmalarına yardımcı olmak üzere tasarlanmıştır.

Aşağıdaki tabloda yer alan taban çizgisi yapılandırmaları, Deniz Feneri varsayılan temeli ile standarttır.<br><br>

| Temel yapılandırma | Açıklama |
|--|--|
| Yöneticiler için MFA gerektirme | Yöneticiler için çok faktörlü kimlik doğrulaması gerektiren bir Koşullu Erişim ilkesi. Tüm bulut uygulamaları için gereklidir. |
| Son kullanıcılar için MFA gerektirme | Kullanıcılar için çok faktörlü kimlik doğrulaması gerektiren bir Koşullu Erişim ilkesi. Tüm bulut uygulamaları için gereklidir. |
| Eski kimlik doğrulamayı engelle | Eski istemci kimlik doğrulamasını engellemek için koşullu Erişim ilkesi. |
| Cihaz kaydı ayarlama | Kiracı cihazlarınızı postanıza kaydolmasına izin vermek için cihaz Microsoft Endpoint Manager. Bu, Azure Active Directory ile Microsoft Endpoint Manager arasında Otomatik Kayıt Azure Active Directory. |
| Microsoft Defender Virüsten Koruma ve sonraki Windows 10 yapılandırma | Önceden yapılandırılmış sistem ayarlarına Windows cihazlar için Cihaz Yapılandırması Microsoft Defender Virüsten Koruma. |
| Uyumluluk ve sonrası için cihaz Windows 10 ilkesi yapılandırma | Temel Windows gereksinimlerini karşılamak için önceden yapılandırılmış ayarları olan en iyi cihaz ilkesi. |

## <a name="related-content"></a>İlgili içerik

[Temel Microsoft 365 Lighthouse dağıtma](m365-lighthouse-deploy-baselines.md) (makale)\
[Microsoft 365 Lighthouse SSS](m365-lighthouse-faq.yml) (makale)
