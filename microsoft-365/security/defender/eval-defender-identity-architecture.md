---
title: Kimlik için Microsoft Defender'ın mimari gereksinimlerini ve teknik çerçeveyi gözden geçirme
description: Microsoft 365 Defender'daki Identity için Microsoft Defender'a yönelik teknik diyagram, deneme laboratuvarınızı veya pilot ortamınızı oluşturmadan önce Microsoft 365'de kimliğinizi anlamanıza yardımcı olur.
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: josephd
author: JoeDavies-MSFT
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
ms.openlocfilehash: 2569349bd5255f47ebca710263dfd7510aee817b
ms.sourcegitcommit: 6f3bc00a5cf25c48c61eb3835ac069e9f41dc4db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2022
ms.locfileid: "63014153"
---
# <a name="review-architecture-requirements-and-key-concepts-for-microsoft-defender-for-identity"></a>Kimlik için Microsoft Defender'da mimari gereksinimlerini ve temel kavramları gözden geçirin


**Aşağıdakiler için geçerlidir:**
- Microsoft 365 Defender

Bu makale [, Kimlik için](eval-defender-identity-overview.md) Microsoft Defender değerlendirme ortamını ayarlama işleminin 1/ 3. adımıdır. Bu işlem hakkında daha fazla bilgi için genel bakış [makalesine bakın](eval-defender-identity-overview.md).

Kimlik için Microsoft Defender'ı etkinleştirmeden önce mimariyi anlıyoruz ve gereksinimleri karşılaya hazır olduğundan emin olun.

Identity için Microsoft Defender, bulut kimlikleriyle ilişkili kullanıcı oturum açma risklerini algılama ve önceden engellemenin yanı sıra şirket içi ağınız genelindeki saldırıları belirlemek için makine öğrenme ve davranış çözümlemelerini kullanır. Daha fazla bilgi için bkz [. Kimlik için Microsoft Defender nedir?](/defender-for-identity/what-is)

Identity için Defender, şirket içi Active Directory kullanıcılarınızı ve/veya kullanıcılarınızı etki alanınıza (Azure AD) Azure Active Directory korur. Yalnızca Azure AD kullanıcılarının neden olduğu bir ortamı korumak için bkz. [Azure AD Kimlik Koruması](/azure/active-directory/identity-protection/overview-identity-protection).

## <a name="understand-the-architecture"></a>Mimariyi anlama

Aşağıdaki diyagramda, Kimlik için Defender'ın temel mimarisini gösterir. 

![Kimlik için Microsoft Defender Mimarisi.](../../media/defender/m365-defender-identity-architecture.png)

Bu şekilde:
- AD etki alanı denetleyicilerinde yüklü algılayıcılar günlükleri ve ağ trafiğini ayrıştırarak analiz ve raporlama için Identity için Microsoft Defender'a gönderir.
-  Azure AD, federasyon kimlik doğrulaması kullanmak üzere yapılandırıldığında (çizimde noktalı çizgi) algılayıcılar da Active Directory Federasyon Hizmetleri'nin (AD FS) ayrıştırmasını sağlar. 
- Kimlik için Microsoft Defender, genişletilmiş algılama ve Microsoft 365 Defender (XDR) için sinyaller gönderir.


Identity algılayıcıları için Defender doğrudan aşağıdaki sunuculara yükleyebilir:

- Etki alanı denetleyicileri: Algılayıcı doğrudan etki alanı denetleyicisi trafiğini, özel bir sunucuya veya bağlantı noktası yansıtma yapılandırmasına gerek kalmadan izler.
- AD FS: Algılayıcı doğrudan ağ trafiğini ve kimlik doğrulama olaylarını izler.

Bulut Uygulamaları için Defender ile tümleştirme de dahil olmak üzere Identity için Defender'ın mimarisine daha derinlemesine bakmak için bkz. Kimlik mimarisi için [Microsoft Defender](/defender-for-identity/architecture).


## <a name="understand-key-concepts"></a>Önemli kavramları anlama

Aşağıdaki tabloda, Identity için Microsoft Defender'ı değerlendirirken, yapılandırarak ve dağıtırken anlamanın önemli olduğu önemli kavramlar tanımlandı.


|Kavram  |Açıklama |Daha fazla bilgi  |
|---------|---------|---------|
| Izlenen etkinlikler | Kimlik için Defender, şüpheli veya kötü amaçlı etkinlikleri saptamak için kuruluş içinde oluşturulan sinyalleri izler ve her olası tehdidin geçerliliğini belirlemenize yardımcı olarak, etkili bir belirleme belirleme ve yanıt vermenizi sağlar.  |  [Kimlik tarafından izlenen etkinlikler için Microsoft Defender](/defender-for-identity/monitored-activities)       |
| Güvenlik uyarıları    | Kimlik güvenlik uyarıları için Defender, ağınızdaki algılayıcılar tarafından algılanan şüpheli etkinliklerin yanı sıra her tehditte yer alan istemci ve bilgisayarlara da açıklama sağlar.   | [Kimlik Güvenliği Uyarıları için Microsoft Defender](/defender-for-identity/suspicious-activity-guide?tabs=external)    |
| Varlık profilleri    | Varlık profilleri, erişim geçmişiyle birlikte kullanıcılar, bilgisayarlar, cihazlar ve kaynaklar hakkında kapsamlı bir inceleme sağlar.   | [Varlık profillerini anlama](/defender-for-identity/entity-profiles)  |
| Lateral movement paths    | MDI güvenlik içgörülerinin önemli bir bileşeni, bir saldırganın ağ genelinde hassas hesaplara veya makinelere erişmek için hassas olmayan hesapları kullandığı ikigen hareket yollarını belirlemektir.  | [Kimlik  Önemli Hareket Yolları (LMP) için Microsoft Defender](/defender-for-identity/use-case-lateral-movement-path)  |
| Ağ Adı Çözümlemesi    |  Ağ Adı Çözümlemesi (NNR), MDI işlevselliğinin ağ trafiği, Windows etkinlikleri, ETW vb. temel alınan etkinliklerini yakalayan ve bu ham verileri her etkinlikte yer alan ilgili bilgisayarlarla ilişkili olarak bir bütün olarak ifade eden bir bileşenidir.       | [Ağ Adı Çözümlemesi nedir?](/defender-for-identity/nnr-policy)      |
| Raporlar    | Kimlik raporları için Defender, sistem ve varlık durumu bilgilerini sağlayan raporları zamanlamanız veya hemen indirmeniz için olanak sağlar.  Ortamınıza algılanan sistem durumu, güvenlik uyarıları ve olası lateral movement paths hakkında raporlar oluşturabilirsiniz.   | [Kimlik Raporları için Microsoft Defender ](/defender-for-identity/reports)       |
| Rol grupları    | Kimlik için Defender, yöneticiler, Kullanıcılar ve Görüntüleyiciler'i de içeren, kuruluşa özgü güvenlik ve uyumluluk ihtiyaçlarına göre verileri korumak için rol tabanlı gruplar ve temsilci erişimi sağlar.        |  [Kimlik rol grupları için Microsoft Defender](/defender-for-identity/role-groups)       |
| Yönetim portalı    |  Güvenlik portalına Microsoft 365 Defender, şüpheli etkinlikleri izlemek ve yanıtlamak için Identity portal cab için Defender kullanılır.      | [Kimlik için Microsoft Defender portalıyla çalışma](/defender-for-identity/workspace-portal)        |
| Bulut Uygulamaları tümleştirmesi için Microsoft Defender   | Bulut Uygulamaları için Microsoft Defender, kullanıcı varlık davranış analizini (UEBA) karma bir ortamda (hem bulut uygulaması hem de şirket içi) sağlamak için Identity için Microsoft Defender ile tümleştirilmiştir   | Identity tümleştirmesi için Microsoft Defender  |
| | | |


## <a name="review-prerequisites"></a>Önkoşulları gözden geçirme

Şirket içi kimlik ve ağ bileşenlerinizin en düşük gereksinimleri karşılaması için Kimlik için Defender'ın bazı önkoşullar çalışması gerekir. Ortamının hazır olduğundan emin olmak için denetim listesi olarak bu makaleyi kullanın: [Kimlik için Microsoft Defender önkoşulları](/defender-for-identity/prerequisites).


## <a name="next-steps"></a>Sonraki adımlar

Adım 2 / 3: [Kimlik için değerlendirme ortamı Defender'ı etkinleştirme](eval-defender-identity-enable-eval.md)

Kimlik için [Microsoft Defender'ı Değerlendirme'ye genel bakış](eval-defender-identity-overview.md)

Değerlendirme ve pilot uygulama için [genel bakış Microsoft 365 Defender](eval-overview.md) 
