---
title: Microsoft 365 Defender tarafından desteklenen hizmetleri dağıtma
description: Microsoft 365 Defender tarafından tümleştirilebilen Microsoft güvenlik hizmetleri, lisans gereksinimleri ve dağıtım yordamları hakkında bilgi edinin
keywords: dağıtma, lisanslar, desteklenen hizmetler, sağlama, yapılandırma Microsoft 365 Defender, M365, lisans uygunluğu, Uç Nokta için Microsoft Defender, Office 365 için Microsoft Defender, Kimlik için Microsoft Defender, Microsoft Cloud App Security, MCAS, E5, A5, EMS
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.openlocfilehash: 4ac6186f3ec8ca7d4888a995b2352ec50529e4f1
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2022
ms.locfileid: "64664908"
---
# <a name="deploy-supported-services"></a>Desteklenen hizmetleri dağıtın

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Şunlar için geçerlidir:**
- Microsoft 365 Defender

[!INCLUDE [Prerelease information](../includes/prerelease.md)]

[Microsoft 365 Defender](microsoft-365-defender.md), gelişmiş saldırılara karşı merkezi algılama, önleme ve araştırma özellikleri sağlamak için çeşitli Microsoft güvenlik hizmetlerini tümleştirir. Bu makalede desteklenen hizmetler, lisans gereksinimleri, bir veya daha fazla hizmet dağıtımıyla ilgili avantajlar ve sınırlamalar ve bunları tek tek nasıl tam olarak dağıtabileceğinize ilişkin bağlantılar açıklanmaktadır.

## <a name="supported-services"></a>Desteklenen hizmetler

Microsoft 365 E5, E5 Güvenlik, A5 veya A5 Güvenlik lisansı ya da geçerli bir lisans birleşimi, aşağıdaki desteklenen hizmetlere erişim sağlar ve Microsoft 365 Defender kullanmanızı sağlar. [Bkz. lisans gereksinimleri](prerequisites.md#licensing-requirements)

| Desteklenen hizmet | Açıklama |
| ------ | ------ |
| Uç Nokta için Microsoft Defender | Güçlü davranış algılayıcıları, bulut analizi ve tehdit zekası ile oluşturulmuş uç nokta koruma paketi |
|Office 365 için Microsoft Defender | E-posta ve diğer işbirliği araçları dahil olmak üzere Office 365 uygulamalarınız ve verileriniz için gelişmiş koruma |
| Kimlik için Microsoft Defender | İlişkili Active Directory sinyallerini kullanarak gelişmiş tehditlere, güvenliği aşılmış kimliklere ve kötü amaçlı insider'lara karşı savunma |
| Bulut Uygulamaları için Microsoft Defender | Microsoft ve üçüncü taraf bulut hizmetlerinizde siber tehditleri belirleme ve mücadele |

## <a name="deployed-services-and-functionality"></a>Dağıtılan hizmetler ve işlevler

Microsoft 365 Defender daha fazla desteklenen hizmet dağıttıkça daha iyi görünürlük, bağıntı ve düzeltme sağlar.

### <a name="benefits-of-full-deployment"></a>Tam dağıtımın avantajları

Microsoft 365 Defender tüm avantajlarından yararlanmak için desteklenen tüm hizmetleri dağıtmanızı öneririz. Tam dağıtımın temel avantajlarından bazıları şunlardır:

- Olaylar, mevcut tüm algılayıcılardan ve hizmete özgü analiz özelliklerinden gelen uyarılara ve olay sinyallerine göre belirlenir ve ilişkilendirilir
- Otomatik araştırma ve düzeltme (AIR) playbook'ları cihazlar, posta kutuları ve kullanıcı hesapları gibi çeşitli varlık türlerine uygulanır
- Cihazlardan, posta kutularından ve diğer varlıklardan gelen olay ve varlık verileri için daha kapsamlı bir gelişmiş tehdit avcılığı şeması sorgulanabilir

### <a name="limited-deployment-scenarios"></a>Sınırlı dağıtım senaryoları

Dağıttığınız her desteklenen hizmet, son derece zengin bir dizi ham sinyal ve bağıntılı bilgi sağlar. Sınırlı dağıtım, Microsoft 365 Defender işlevselliğin kapanmasına neden olmasa da uç noktalarınız, uygulamalarınız, verileriniz ve kimlikleriniz arasında kapsamlı görünürlük sağlayabilmesi bundan etkilenir. Aynı zamanda, tüm düzeltme özellikleri yalnızca dağıttığınız hizmetler tarafından yönetilebilen varlıklar için geçerlidir.

Aşağıdaki tabloda desteklenen her hizmetin ek verileri nasıl sağladığı, verilerle bağıntı sağlayarak ek içgörü elde etme fırsatları ve daha iyi düzeltme ve yanıt özellikleri listelenmektedir.

| Hizmet | Veriler (ilişkili bilgiler & sinyaller) | Düzeltme & yanıt kapsamı |
| ------ | ------ | ------ |
| Uç Nokta için Microsoft Defender |<ul><li>Uç nokta durumları ve ham olaylar</li><li>Virüsten koruma, EDR, saldırı yüzeyini azaltma dahil olmak üzere uç nokta algılamaları ve uyarıları</li><li>Uç noktalarda gözlemlenen dosyalar ve diğer varlıklar hakkında bilgi</li></ul> |  Uç Noktaları |
|Office 365 için Microsoft Defender |<ul><li>Posta ve posta kutusu durumları ve ham olaylar</li><li>E-posta, ek ve bağlantı algılamaları</li></ul> | <ul><li>Posta kutu -ları</li><li>hesapları Microsoft 365</li></ul> |
| Kimlik için Microsoft Defender |<ul><li>Kimlik doğrulama olayları da dahil olmak üzere Active Directory sinyalleri</li><li>Kimlikle ilgili davranış algılamaları</li></ul> | Kimlik |
| Bulut Uygulamaları için Microsoft Defender |<ul><li>Tasdik edilmemiş bulut uygulamalarının ve hizmetlerinin (gölge BT) algılanması</li><li>Verilerin bulut uygulamalarına açık olması</li><li>Bulut uygulamalarıyla ilişkili tehdit etkinliği</li></ul> | Bulut uygulamaları |

## <a name="deploy-the-services"></a>Hizmetleri dağıtma

Her hizmetin dağıtılması için genellikle kiracınıza sağlama ve bazı ilk yapılandırmalar gerekir. Bu hizmetlerin her birinin nasıl dağıtıldığından anlamak için aşağıdaki tabloya bakın.

| Hizmet | Sağlama yönergeleri | İlk yapılandırma |
| ------ | ------ | ------ |
| Uç Nokta için Microsoft Defender | [Uç Nokta için Microsoft Defender dağıtım kılavuzu](../defender-endpoint/deployment-phases.md) | *Bkz. sağlama yönergeleri* |
|Office 365 için Microsoft Defender | *Yok, Office 365 ile sağlandı* | [Office 365 için Microsoft Defender ilkelerini yapılandırma](/microsoft-365/security/office-365-security/defender-for-office-365#configure-atp-policies) |
| Kimlik için Microsoft Defender | [Hızlı Başlangıç: Kimlik için Microsoft Defender örneğinizi oluşturma](/azure-advanced-threat-protection/install-atp-step1) | *Bkz. sağlama yönergeleri* |
| Bulut Uygulamaları için Microsoft Defender | *Yok* | [Hızlı Başlangıç: Microsoft Defender for Cloud Apps ile Kullanmaya başlayın](/cloud-app-security/getting-started-with-cloud-app-security) |

Desteklenen hizmetleri dağıttıktan sonra [Microsoft 365 Defender açın](m365d-enable.md).

## <a name="related-topics"></a>İlgili konular

- [Microsoft 365 Defender genel bakış](microsoft-365-defender.md)
- [Microsoft 365 Defender’ı açın](m365d-enable.md)
- [Uç Nokta için Microsoft Defender genel bakış](../defender-endpoint/microsoft-defender-endpoint.md)
- [Office 365 için Microsoft Defender genel bakış](../office-365-security/defender-for-office-365.md)
- [Microsoft Defender for Cloud Apps genel bakış](/cloud-app-security/what-is-cloud-app-security)
- [Kimlik için Microsoft Defender genel bakış](/azure-advanced-threat-protection/what-is-atp)
