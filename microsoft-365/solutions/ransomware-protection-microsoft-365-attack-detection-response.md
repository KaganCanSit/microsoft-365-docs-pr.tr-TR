---
title: Adım 2. Saldırı algılamayı ve yanıtı dağıtın
author: JoeDavies-MSFT
f1.keywords:
- NOCSH
ms.author: josephd
manager: dansimp
audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- Strat_O365_Enterprise
- ransomware
- m365solution-ransomware
ms.custom: seo-marvel-jun2020
keywords: fidye yazılımı, insan tarafından işletilen fidye yazılımı, insan tarafından işletilen fidye yazılımı, HumOR, extortion saldırısı, fidye yazılımı saldırı, şifreleme, cryptovirology, sıfır güven
description: Microsoft 365 Defender kaynaklarınızı fidye yazılımlarına karşı korumak için Microsoft 365 ve güvenlik sinyali kaynaklarını kullanın.
ms.openlocfilehash: 8459d9ce8a22192d362fd8b3bf95e34c7015f08f
ms.sourcegitcommit: 23a90ed17cddf3b0db8d4084c8424f0fabd7b1de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/17/2022
ms.locfileid: "63015346"
---
# <a name="step-2-deploy-attack-detection-and-response"></a>Adım 2. Saldırı algılamayı ve yanıtı dağıtın

Fidye yazılımı saldırı algılaması ve Microsoft 365 kiracınıza yanıt olarak, fidye yazılımı saldırı algılama ve yanıt için önerilen bir başlangıç adımı [olarak, yazılım](/microsoft-365/security/defender/eval-overview) yazılımlarının özelliklerini ve özelliklerini değerlendirmek için bir deneme Microsoft 365 Defender.

Daha fazla bilgi için bu kaynaklara bakın.

| Özellik | Açıklama | Nereden başlayacak? | Algılama ve yanıt için nasıl kullanılır? |
|:-------|:-----|:-------|:-------|
| [Microsoft 365 Defender](/microsoft-365/security/defender) | Sinyal ve ek özellikler özelliklerini tek bir çözümde birleştirir. <br><br> Güvenlik uzmanlarının tehdit sinyallerini bir araya getirdir ve bir tehdidin tam kapsamını ve etkisini belirler. <br><br> Saldırıyı ve etkilenen kendi kendine etkilenen posta kutularını, uç noktaları ve kullanıcı kimliklerini önlemeye veya durdurmaya yönelik eylemleri otomatikleştirir. | [Başlarken](/microsoft-365/security/defender/get-started) | [Olay yanıtı](/microsoft-365/security/defender/incidents-overview) |
| [Kimlik için Microsoft Defender](/defender-for-identity/what-is) |  Bulut tabanlı bir güvenlik arabirimi aracılığıyla, şirket içi Active Directory Etki Alanı Hizmetleri (AD DS) sinyallerini kullanarak, gelişmiş tehditleri, güvenliği tehlikeye kimlikleri ve kötü amaçlı insider eylemlerini tanımlar, algılar ve araştırın. | [Genel bakış](/defender-for-identity/what-is) | [Kimlik için Microsoft Defender portalıyla çalışma](/defender-for-identity/workspace-portal) |
| [Office 365 için Microsoft Defender](/microsoft-365/security/office-365-security) | E-posta iletileri, bağlantılar (URL'ler) ve işbirliği araçları tarafından tehditlere karşı organizasyonlarınızı korur. <br><br> Kötü amaçlı yazılımlara, kimlik avına, kimlik sahtelerine ve diğer saldırı türlerine karşı koruma sağlar. | [Genel bakış](/microsoft-365/security/office-365-security/overview) | [Tehdit avı](/microsoft-365/security/office-365-security/threat-hunting-in-threat-explorer) |
| [Uç Nokta için Microsoft Defender](/microsoft-365/security/defender-endpoint) | Uç noktalar (cihazlar) genelinde gelişmiş tehditleri algılamayı ve buna yanıt verir. | [Genel bakış](/microsoft-365/security/defender-endpoint/microsoft-defender-endpoint)  | [Uç nokta algılama ve yanıt](/microsoft-365/security/defender-endpoint/overview-endpoint-detection-response) |
| [Azure Active Directory (Azure AD) Kimlik Koruması](/azure/active-directory/identity-protection/) | Kimlik tabanlı riskleri algılamayı ve düzeltmeyi, bu riskleri incelemeyi otomatik haleler. | [Genel bakış](/azure/active-directory/identity-protection/overview-identity-protection) | [Riski araştırma](/azure/active-directory/identity-protection/howto-identity-protection-investigate-risk) |
| [Bulut Uygulamaları için Microsoft Defender](/cloud-app-security) | Tüm Microsoft ve üçüncü taraf bulut hizmetleriniz genelinde keşif, araştırma ve yönetim için bulut erişimi güvenlik aracısı. | [Genel bakış](/cloud-app-security/what-is-cloud-app-security) | [Araştır](/cloud-app-security/investigate) |

>[!Note]
>Bu hizmetlerin hepsi, Microsoft 365 E5 eklentiyle Microsoft 365 E3 veya Microsoft 365 E5 Güvenlik gerektirir.
>

Fidye yazılımı yazılımı yazılımına yönelik aşağıdaki yaygın tehditleri tespit etmek ve bunlara yanıt vermek için bu hizmetleri kullanın:

- Kimlik bilgileri hırsızlığı

   - Azure AD Identity Protection
   - Kimlik için Defender
   - Office 365 için Defender

- Cihaz güvenliği

   - Uç Nokta için Defender
   - Office 365 için Defender

- Ayrıcalık yükseltme

   - Azure AD Identity Protection
   - Bulut Uygulamaları için Defender

- Kötü amaçlı uygulama davranışı

   - Bulut Uygulamaları için Defender

- Veri sızıntısı, silinmesi veya karşıya yükleme

   - Office 365 için Defender
   - Anormal algılama ilkeleriyle [Bulut Uygulamaları için](/cloud-app-security/anomaly-detection-policy#ransomware-activity) Defender

Aşağıdaki hizmetler, Microsoft 365 Defender portalı (https://security.microsoft.com)yaygın bir tehdit toplama ve çözümleme noktası olarak) kullanır:

- Kimlik için Defender
- Office 365 için Defender
- Uç Nokta için Defender
- Bulut Uygulamaları için Defender

Microsoft 365 Defender, güvenlik analistlerinin fidye yazılımı saldırılarının aşamalarını daha hızlı algılaylarını, inceleylerini ve düzeltmek için tehdit sinyallerini uyarılarda ve bağlantılı uyarılarda bir olayda birleştirir.

## <a name="resulting-configuration"></a>Sonuçta elde edilen yapılandırma

İşte, 1. ve 2. adımlar için kiracınız için fidye yazılımı koruması.

![2. Adım'dan Microsoft 365 kiracınız için fidye yazılımı koruması](../media/ransomware-protection-microsoft-365/ransomware-protection-microsoft-365-architecture-step2.png)

## <a name="next-step"></a>Sonraki adım

[![Yazılımla fidye yazılımına karşı 3. Microsoft 365](../media/ransomware-protection-microsoft-365/ransomware-protection-microsoft-365-step3.png)](ransomware-protection-microsoft-365-identities.md)

Kiracınıza [kimlikleri korumak için 3](ransomware-protection-microsoft-365-identities.md). Adıma Microsoft 365 geçin.
