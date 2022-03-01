---
title: Portalda verilerin Microsoft 365 Defender erişimi Microsoft 365 Defender yönetme
description: E-postada veri izinlerini yönetmeyi Microsoft 365 Defender
keywords: erişim, izinler, Microsoft 365 Defender, M365, güvenlik, MCAS, Bulut Uygulamaları Güvenliği, Uç Nokta için Microsoft Defender, kapsam, kapsam, RBAC
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
ms.collection: M365-security-compliance
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.openlocfilehash: 8e9cacf3fb7d74acc210ac0b77ed5e68c7a93961
ms.sourcegitcommit: 2c3b737e71038f843ef9e9ff4d5b99d6110b8ec5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2022
ms.locfileid: "63010031"
---
# <a name="manage-access-to-microsoft-365-defender-with-azure-active-directory-global-roles"></a>Genel rollerle Microsoft 365 Defender erişimi Azure Active Directory yönetme

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:**
- Microsoft 365 Defender

E-postanıza erişimi yönetmenin iki Microsoft 365 Defender:
- **Genel Azure Active Directory (AD) rolleri**
- **Özel rol erişimi**

Aşağıdaki Genel Kullanıcı Görevleri **(AD) Azure Active Directory atanan** hesaplar, genel Microsoft 365 Defender verilere erişim sağlar:
- Genel yönetici
- Güvenlik yöneticisi
- Güvenlik İşleci
- Genel Okuyucu
- Güvenlik Okuyucu

Bu rollere sahip hesapları gözden geçirmek için [Portalda yer alan Microsoft 365 Defender görünümüne tıklayın](https://security.microsoft.com/permissions).

**Özel rol** erişimi, yeni bir Microsoft 365 Defender özelliktir ve proje içinde belirli verilere, görevlere ve özelliklere erişimi yönetmenize Microsoft 365 Defender. Özel roller, genel Azure AD rollerine göre daha fazla denetim sağlayarak, kullanıcılara yalnızca gereken en az izinli rollerle erişim sağlar.  Genel Azure AD rollerinin yanı sıra özel roller de oluşturulabilir. [Özel roller hakkında daha fazla bilgi edinmek için](custom-roles.md):

> [!NOTE]
> Bu makale yalnızca genel kullanıcı rollerinin yönetimi Azure Active Directory geçerlidir. Özel rol tabanlı erişim denetimi kullanma hakkında daha fazla bilgi için bkz. [Rol tabanlı erişim denetimi için özel roller](custom-roles.md)

## <a name="access-to-functionality"></a>İşlevlere erişim
Belirli işlevlere erişim, [Azure AD rolünüz tarafından belirlenir](/azure/active-directory/roles/permissions-reference). Sizin veya kullanıcı grubunuzla yeni bir rol atamanızı gerektiren belirli işlevlere erişmeniz gerekirse, genel yöneticiye başvurun.

### <a name="approve-pending-automated-tasks"></a>Bekleyen otomatik görevleri onaylama
[Otomatik araştırma ve düzeltme,](m365d-autoir-actions.md) e-postalar, iletme kuralları, dosyalar, kalıcılık mekanizmaları ve araştırma sırasında bulunan diğer yapılar üzerinde eylemde bulunabilir. Açık onay gerektiren bekleyen eylemleri onaylamak veya reddetmek için, belirli rollere Belirli roller Microsoft 365. Daha fazla bilgi edinmek için bkz [. İşlem merkezi izinleri](m365d-action-center.md#required-permissions-for-action-center-tasks).

## <a name="access-to-data"></a>Verilere erişim
Kullanıcı gruplarına Microsoft 365 Defender, Uç nokta rol tabanlı erişim denetimi (RBAC) için Microsoft Defender'da kullanıcı gruplarına atanan kapsam kullanılarak denetlenabilir. Erişiminizin kapsamı Uç Nokta için Defender'daki belirli bir cihaz kümesinde yoksa, tüm cihazlardaki verilere tam Microsoft 365 Defender. Bununla birlikte, hesabınız kapsamındaki verileri yalnızca kapsam kapsamındaki cihazlarla ilgili olarak görüntülersiniz.

Örneğin, Microsoft Defender for Endpoint rolüne sahip tek bir kullanıcı grubunda yer aldıysanız ve bu kullanıcı grubuna yalnızca satış cihazlarına erişim verildiyse, Microsoft 365 Defender'de yalnızca satış cihazlarıyla ilgili verileri Microsoft 365 Defender. [Uç Nokta için Microsoft Defender'daki RBAC ayarları hakkında daha fazla bilgi](/windows/security/threat-protection/microsoft-defender-atp/rbac)

### <a name="microsoft-defender-for-cloud-apps-access-controls"></a>Bulut Uygulamaları için Microsoft Defender erişim denetimleri
Önizleme sırasında, Microsoft 365 Defender Uygulamaları için Defender ayarlarına göre erişim denetimlerini zorunlu tutulmayacaktır. Veri Microsoft 365 Defender bu ayarlardan etkilenmez.

## <a name="related-topics"></a>İlgili konular
- [Görevler için rol tabanlı erişim denetiminde özel Microsoft 365 Defender](custom-roles.md)
- [Azure AD yerleşik rolleri](/azure/active-directory/roles/permissions-reference)
- [Endpoint RBAC için Microsoft Defender](/windows/security/threat-protection/microsoft-defender-atp/rbac)
- [Bulut Uygulamaları rolleri için Defender](/cloud-app-security/manage-admins)
