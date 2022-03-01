---
title: Uygulamalı Bulut Uygulamaları için Microsoft Defender'ı Microsoft 365 Defender
description: Cihazları, Microsoft 365 Defender, verileri ve uygulamaları korumak üzere tasarlanmış güvenlik çözümünü test etmek ve deneyim yaşamak için test etmek üzere laboratuvar veya pilot ortamınızı ayarlayın.
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: bcarter
author: brendacarter
ms.date: 07/09/2021
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-scenario
- m365solution-evalutatemtp
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: 484924d936f348fb29421b6bcc1789df4a44dc90
ms.sourcegitcommit: 6f3bc00a5cf25c48c61eb3835ac069e9f41dc4db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2022
ms.locfileid: "63010751"
---
# <a name="pilot-microsoft-defender-for-cloud-apps-with-microsoft-365-defender"></a>Uygulamalı Bulut Uygulamaları için Microsoft Defender'ı Microsoft 365 Defender


**Aşağıdakiler için geçerlidir:**
- Microsoft 365 Defender

Bu makale, [Bulut Uygulamaları için](eval-defender-mcas-overview.md) Microsoft Defender değerlendirme ortamını ayarlama işleminin 3. adımıdır. Bu işlem hakkında daha fazla bilgi için genel bakış [makalesine bakın](eval-defender-mcas-overview.md).

Bulut Uygulamaları için Microsoft Defender pilotlarını ayarlamak ve yapılandırmak için aşağıdaki adımları kullanın.


![Bulut Uygulamaları için Microsoft Defender'ı pilotlara uygulama adımları.](../../media/defender/m365-defender-mcas-pilot-steps.png)

- Adım 1. [Pilot grup oluşturma — Pilot dağıtımınızı belirli kullanıcı gruplarıyla planlama](#step-1-create-the-pilot-group--scope-your-pilot-deployment-to-certain-user-groups)
- [2. Adım. Korumayı yapılandırma — Koşullu Erişim Uygulama Denetimi](#step-2-configure-protection--conditional-access-app-control)
- [3. Adım. Özellikleri deneyin: Ortamınızı korumak için öğreticilere göz atabilirsiniz](#step-3-try-out-capabilities--walk-through-tutorials-for-protecting-your-environment) 


## <a name="step-1-create-the-pilot-group--scope-your-pilot-deployment-to-certain-user-groups"></a>Adım 1. Pilot grup oluşturma — Pilot dağıtımınızı belirli kullanıcı gruplarıyla planlama

Bulut Uygulamaları için Microsoft Defender, dağıtımınız kapsamında size olanak sağlar. Kapsam, uygulamalar için izlenir veya izleme dışında tutulacak belirli kullanıcı gruplarını seçmenize olanak sağlar. Kullanıcı gruplarını dahil etmek veya dışarıda tutmak. Pilot dağıtımınızı kapsam içinde görmek için Bkz. [Kapsamı Olan Dağıtım](/cloud-app-security/scoped-deployment).


## <a name="step-2-configure-protection--conditional-access-app-control"></a>Adım 2. Korumayı yapılandırma — Koşullu Erişim Uygulama Denetimi

Yapılandırabilirsiniz en güçlü korumalardan biri Koşullu Erişim Uygulama Denetimi'dir. Bunun için E-Azure Active Directory (Azure AD) ile tümleştirme gerekir. İlgili ilkeler (sağlıklı cihazlar gerektirme gibi) dahil olmak üzere koşullu Erişim ilkelerini, sizin kabul ettiysiniz bulut uygulamalarına uygulamanıza olanak tanır. 

SaaS uygulamalarını yönetmek için Bulut Uygulamaları için Microsoft Defender'ı kullanmanın ilk adımı, bunları keşfetmek ve ardından bunları Azure AD kiracınıza eklemektir. Keşifle ilgili yardıma ihtiyacınız varsa bkz [. Ağda SaaS uygulamalarını keşfetme ve yönetme](/cloud-app-security/tutorial-shadow-it). Uygulamaları budikten sonra, [bunları Azure AD kiracınıza ekleyin](/azure/active-directory/manage-apps/add-application-portal).

Aşağıdakini yaparak bunları yönetmeye başlayabilirsiniz:

- İlk olarak, Azure AD'de yeni bir koşullu erişim ilkesi oluşturun ve bunu "Koşullu Erişim Uygulama Denetimi Kullan" olarak yapılandırın. Bu işlem, isteği Bulut Uygulamaları için Defender'a yeniden yönlendirer. Tek bir ilke oluşturabilir ve tüm SaaS uygulamalarını bu ilkeye  eklersiniz.
- Ardından Bulut Uygulamaları için Defender'da oturum ilkeleri oluşturun. Uygulamak istediğiniz her denetim için bir ilke oluşturun.

Desteklenen uygulamalar ve istemciler gibi daha fazla bilgi için bkz. Bulut Uygulamaları için [Microsoft Defender ile Uygulamaları Koruma Koşullu Erişim Uygulama Denetimi](/cloud-app-security/proxy-intro-aad). 

Örneğin ilkeler için bkz [. SaaS uygulamaları için Bulut Uygulamaları için önerilen Microsoft Defender ilkeleri](../office-365-security/mcas-saas-access-policies.md). Bu ilkeler, tüm müşteriler [için başlangıç noktası](../office-365-security/microsoft-365-policies-configurations.md) olarak önerilen bir dizi ortak kimlik ve cihaz erişim ilkelerinin üzerine hazırlar. 

## <a name="step-3-try-out-capabilities--walk-through-tutorials-for-protecting-your-environment"></a>Adım 3. Özellikleri deneyin: Ortamınızı korumak için öğreticilere göz atabilirsiniz 

Bulut Uygulamaları için Microsoft Defender belgeleri, risk keşfetmenize ve ortamınızı korumanıza yardımcı olacak bir dizi öğretici içerir. 

Bulut Uygulamaları için Defender öğreticilerini deneyin:

- [Şüpheli kullanıcı etkinliğini algılama](/cloud-app-security/tutorial-suspicious-activity)
- [Riskli kullanıcıları araştırma](/cloud-app-security/tutorial-ueba)
- [Riskli OAuth uygulamalarını araştırma](/cloud-app-security/investigate-risky-oauth)
- [Hassas bilgileri keşfetme ve koruma](/cloud-app-security/tutorial-dlp)
- [Organizasyonlar'daki herhangi bir uygulamayı gerçek zamanlı olarak koruma](/cloud-app-security/tutorial-proxy)
- [Hassas bilgilerin indirilmelerini engelle](/cloud-app-security/use-case-proxy-block-session-aad)
- [Dosyalarınızı yönetici karantinası ile koruma](/cloud-app-security/use-case-admin-quarantine)
- [Riskli bir işlemle ilgili olarak adım adım kimlik doğrulaması gerektirme](/cloud-app-security/tutorial-step-up-authentication)

Bulut Uygulamaları için Microsoft Defender'da gelişmiş av verileriyle ilgili daha fazla bilgi için [videoya bakın](https://www.microsoft.com/en-us/videoplayer/embed/RWFISa).

## <a name="next-steps"></a>Sonraki adımlar

[Pilot ortamdaki bir Microsoft 365 Defender kullanarak inceleme ve yanıtlama](eval-defender-investigate-respond.md)

Bulut Uygulamaları için [Microsoft Defender'ı Değerlendirme'ye genel bakış](eval-defender-mcas-overview.md)

Değerlendirme ve pilot uygulama için [genel bakış Microsoft 365 Defender](eval-overview.md)
