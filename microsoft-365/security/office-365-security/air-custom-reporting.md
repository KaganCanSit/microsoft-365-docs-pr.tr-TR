---
title: Otomatik araştırma ve yanıt ile özel raporlama çözümleri
keywords: SIEM, API, AIR, autoIR, Uç Nokta için Microsoft Defender, otomatik araştırma, tümleştirme, özel rapor
f1.keywords:
- NOCSH
author: JoeDavies-MSFT
ms.author: josephd
manager: dansimp
audience: ITPro
ms.topic: article
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
description: Özel veya üçüncü taraf bir raporlama çözümüyle otomatik araştırmayı ve yanıtı nasıl tümleştirin öğrenin.
ms.date: 01/29/2021
ms.custom:
- air
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 7b1c0501bb044129c4fa626428dfc616ea8414e0
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62984680"
---
# <a name="custom-or-third-party-reporting-solutions-for-microsoft-defender-for-office-365"></a>Microsoft Defender for Office 365 için özel veya üçüncü taraf raporlama çözümleri

Microsoft [Defender For Office 365](defender-for-office-365.md) ile otomatik [soruşturmalar hakkında ayrıntılı bilgi edinebilirsiniz](air-view-investigation-results.md). Bununla birlikte, bazı kuruluşlar özel veya üçüncü taraf bir raporlama çözümü de kullanır. Organizasyonunız otomatik soruşturmalar hakkında bilgileri [böyle](office-365-air.md) bir çözümle tümleştirmek istiyorsa, Office 365 Api'sini kullanabilirsiniz.

**Geçerli olduğu yer:**
- [Office 365 için Microsoft Defender plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Microsoft [Defender For Office 365](defender-for-office-365.md) ile otomatik [soruşturmalar hakkında ayrıntılı bilgi edinebilirsiniz](air-view-investigation-results.md). Bununla birlikte, bazı kuruluşlar özel veya üçüncü taraf bir raporlama çözümü de kullanır. Organizasyonunız otomatik soruşturmalar hakkında bilgileri böyle bir çözümle tümleştirmek istiyorsa, Office 365 Api'sini kullanabilirsiniz.

|Kaynak|Açıklama|
|:---|:---|
|[Office 365 API'lere genel bakış](/office/office-365-management-api/office-365-management-apis-overview)|Yönetim Office 365 API'si, kullanıcı, yönetici, sistem ve etkinlik günlüklerine ilişkin çeşitli kullanıcı, yönetici, sistem ve ilke Microsoft 365 Azure Active Directory bilgi sağlar.|
|[Uygulama Yönetimi API'leriyle Office 365 başlama](/office/office-365-management-api/get-started-with-office-365-management-apis)|Yönetim Office 365 API'si, verilerinize erişmesi için uygulamanıza kimlik doğrulama hizmetleri sağlamak Microsoft 365 kullanır. Bunu ayarlamak için bu makaledeki adımları izleyin.|
|[Office 365 Yönetimi Etkinliği API başvurusu](/office/office-365-management-api/office-365-management-activity-api-reference)|Office 365 ve Azure AD etkinlik günlüklerinden kullanıcı, yönetici, sistem, ilke eylemleri ve Microsoft 365 olayları hakkında bilgi almak için Microsoft 365 Yönetim Etkinliği API'sini kullanabilirsiniz. Bunun nasıl çalıştığını öğrenmek için bu makaleyi okuyun.|
|[Office 365 Yönetimi Etkinlik API'si şeması](/office/office-365-management-api/office-365-management-activity-api-schema)|Office 365 Management Activity API aracılığıyla [](/office/office-365-management-api/office-365-management-activity-api-schema#common-schema) kullanılabilen belirli veri türleri hakkında bilgi edinmek için, Ortak şema ve [Office 365 için Defender](/office/office-365-management-api/office-365-management-activity-api-schema#office-365-advanced-threat-protection-and-threat-investigation-and-response-schema) ve tehdit soruşturması ve yanıt şeması hakkında genel bir bakış elde edin.|
|

## <a name="see-also"></a>Ayrıca bkz.

- [Office 365 için Microsoft Defender](defender-for-office-365.md)
- [Otomatik araştırma ve yanıt Microsoft 365 Defender](/microsoft-365/security/defender/m365d-autoir)
