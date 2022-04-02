---
title: Microsoft Defender for Cloud Apps ile pilot Microsoft 365 Defender
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
ms.openlocfilehash: 9961caee57fade58581e8ddb8b9de7ea0d6aafd8
ms.sourcegitcommit: 3b8e009ea1ce928505b8fc3b8926021fb91155f3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/28/2022
ms.locfileid: "64498571"
---
# <a name="pilot-microsoft-defender-for-cloud-apps-with-microsoft-365-defender"></a>Microsoft Defender for Cloud Apps ile pilot Microsoft 365 Defender


**Aşağıdakiler için geçerlidir:**
- Microsoft 365 Defender

Bu makale, [değerlendirme ortamını ayarlama](eval-defender-mcas-overview.md) sürecindeki 3/ 3. Adımdır ve Microsoft Defender for Cloud Apps. Bu işlem hakkında daha fazla bilgi için genel bakış [makalesine bakın](eval-defender-mcas-overview.md).

Pilot uygulama ayarlarını yapmak ve yapılandırmak için aşağıdaki Microsoft Defender for Cloud Apps.


:::image type="content" source="../../media/defender/m365-defender-mcas-pilot-steps.png" alt-text="Pilot uygulama adımları Microsoft Defender for Cloud Apps" lightbox="../../media/defender/m365-defender-mcas-pilot-steps.png":::
- [1. Adım. Pilot grubu oluşturma—Pilot dağıtımınızı belirli kullanıcı gruplarıyla kapsam içinde oluşturma](#step-1-create-the-pilot-groupscope-your-pilot-deployment-to-certain-user-groups)
- [2. Adım. Korumayı yapılandırma— Koşullu Erişim Uygulama Denetimi](#step-2-configure-protectionconditional-access-app-control)
- [3. Adım. Özellikleri deneyin: Ortamınızı korumak için öğreticilere göz atabilirsiniz](#step-3-try-out-capabilitieswalk-through-tutorials-for-protecting-your-environment) 


## <a name="step-1-create-the-pilot-groupscope-your-pilot-deployment-to-certain-user-groups"></a>Adım 1. Pilot grubu oluşturma—Pilot dağıtımınızı belirli kullanıcı gruplarıyla kapsam içinde oluşturma

Microsoft Defender for Cloud Apps, dağıtımınız kapsamında size olanak sağlar. Kapsam, uygulamalar için izlenir veya izleme dışında tutulacak belirli kullanıcı gruplarını seçmenize olanak sağlar. Kullanıcı gruplarını dahil etmek veya dışarıda tutmak. Pilot dağıtımınızı kapsam içinde görmek için Bkz. [Kapsamı Olan Dağıtım](/cloud-app-security/scoped-deployment).


## <a name="step-2-configure-protectionconditional-access-app-control"></a>Adım 2. Korumayı yapılandırma— Koşullu Erişim Uygulama Denetimi

Yapılandırabilirsiniz en güçlü korumalardan biri Koşullu Erişim Uygulama Denetimi'dir. Bu koruma, E-Azure Active Directory (Azure AD) ile tümleştirme gerektirir. İlgili ilkeler (sağlıklı cihazlar gerektirme gibi) dahil olmak üzere koşullu Erişim ilkelerini, sizin kabul ettiysiniz bulut uygulamalarına uygulamanıza olanak tanır. 

SaaS uygulamalarını yönetmek için Microsoft Defender for Cloud Apps'i kullanmanın ilk adımı, bu uygulamaları keşfetmek ve ardından bunları Azure AD kiracınıza eklemektir. Keşifle ilgili yardıma ihtiyacınız varsa bkz [. Ağda SaaS uygulamalarını keşfetme ve yönetme](/cloud-app-security/tutorial-shadow-it). Uygulamaları bu keşfettikten sonra, [bu uygulamaları Azure AD kiracınıza ekleyin](/azure/active-directory/manage-apps/add-application-portal).

Aşağıdaki görevleri yürüterek bu uygulamaları yönetmeye başlayabilirsiniz:

- İlk olarak, Azure AD'de yeni bir koşullu erişim ilkesi oluşturun ve bunu "Koşullu Erişim Uygulama Denetimi Kullan" olarak yapılandırın. Bu yapılandırma, isteği uygulamalara yeniden yönlendirmeye Bulut için Defender yardımcı olur. Tek bir ilke oluşturabilir ve tüm SaaS uygulamalarını bu ilkeye  eklersiniz.
- Ardından, Bulut için Defender Uygulamaları'nın içinde oturum ilkeleri oluşturun. Uygulamak istediğiniz her denetim için bir ilke oluşturun.

Desteklenen uygulamalar ve istemciler gibi daha fazla bilgi için bkz[. Koşullu Erişim Uygulama Denetimi Microsoft Defender for Cloud Apps uygulamaları koruma](/cloud-app-security/proxy-intro-aad). 

Örneğin ilkeler için bkz[. SaaS Microsoft Defender for Cloud Apps önerilen İlkeler](../office-365-security/mcas-saas-access-policies.md). Bu ilkeler, tüm müşteriler [için başlangıç noktası](../office-365-security/microsoft-365-policies-configurations.md) olarak önerilen bir dizi ortak kimlik ve cihaz erişim ilkelerinin üzerine hazırlar. 

## <a name="step-3-try-out-capabilitieswalk-through-tutorials-for-protecting-your-environment"></a>Adım 3. Özellikleri deneyin: Ortamınızı korumak için öğreticilere göz atabilirsiniz 

Bu Microsoft Defender for Cloud Apps, risk keşfetmenize ve ortamınızı korumanıza yardımcı olacak bir dizi öğretici içerir. 

Uygulama öğreticilerini Bulut için Defender deneyin:

- [Şüpheli kullanıcı etkinliğini algılama](/cloud-app-security/tutorial-suspicious-activity)
- [Riskli kullanıcıları araştırma](/cloud-app-security/tutorial-ueba)
- [Riskli OAuth uygulamalarını araştırma](/cloud-app-security/investigate-risky-oauth)
- [Hassas bilgileri keşfetme ve koruma](/cloud-app-security/tutorial-dlp)
- [Organizasyonlar'daki herhangi bir uygulamayı gerçek zamanlı olarak koruma](/cloud-app-security/tutorial-proxy)
- [Hassas bilgilerin indirilmelerini engelle](/cloud-app-security/use-case-proxy-block-session-aad)
- [Dosyalarınızı yönetici karantinası ile koruma](/cloud-app-security/use-case-admin-quarantine)
- [Riskli bir işlemle ilgili olarak adım adım kimlik doğrulaması gerektirme](/cloud-app-security/tutorial-step-up-authentication)

Verileri görmek için gelişmiş Microsoft Defender for Cloud Apps için videoya [bakın](https://www.microsoft.com/en-us/videoplayer/embed/RWFISa).

## <a name="next-steps"></a>Sonraki adımlar

[Pilot ortamdaki bir Microsoft 365 Defender kullanarak inceleme ve yanıtlama](eval-defender-investigate-respond.md)

Değerlendirme görünümüne genel [bakış Microsoft Defender for Cloud Apps](eval-defender-mcas-overview.md)

Değerlendirme ve pilot uygulama için [genel bakış Microsoft 365 Defender](eval-overview.md)
