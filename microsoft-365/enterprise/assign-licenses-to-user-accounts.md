---
title: Kullanıcı Microsoft 365 hesaplarına kullanıcı lisansı atama
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 09/30/2020
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- O365p_AddUsersWithDirSync
- O365M_AddUsersWithDirSync
- O365E_HRCSetupAADConnectAboutLM617031
- O365E_AddUsersWithDirSync
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOP150
- MOE150
- MBS150
ms.assetid: 01920974-9e6f-4331-a370-13aea4e82b3e
description: Kullanıcı hesaplarına tek Microsoft 365 veya grup üyeliğine dayalı olarak lisans atamayı açıklar.
ms.openlocfilehash: dd941be0d257aa356cf6e69bfdd59a8d1743ed93
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62983618"
---
# <a name="assign-microsoft-365-licenses-to-user-accounts"></a>Kullanıcı Microsoft 365 hesaplarına kullanıcı lisansı atama

*Bu makale hem son hem de Microsoft 365 Kurumsal hem de Office 365 Kurumsal.*

Yalnızca bulut kimlik modeli için, Microsoft 365 oluşturduğunuza bağlı olarak kullanıcı hesaplarına kullanıcı hesaplarına kimlik lisansı atabilirsiniz.

Karma kimlik modeli için, Active Directory Etki Alanı Hizmetleri (AD DS) kullanıcı hesapları ilk kez eşitlenirken, onlara otomatik olarak bir konum veya kullanıcı Microsoft 365 atanmamış olur. **Lisans atamadan önce veya atamadan önce kullanıcı konumuyla birlikte her kullanıcı hesabını yapılandırmanız gerekir.**

Her iki durumda da, kullanıcılarınızı e-posta ve posta gibi Microsoft 365 hizmetlere erişim için kullanıcı hesaplarına lisans Microsoft Teams.

Kullanıcı hesaplarına tek tek veya grup üyeliği aracılığıyla otomatik olarak lisans atabilirsiniz.

Bireysel Microsoft 365 hesaplarına kullanıcı lisansı atamak için şunları kullanabilirsiniz:

- [Microsoft 365 yönetim merkezi](../admin/manage/assign-licenses-to-users.md)
- [PowerShell](assign-licenses-to-user-accounts-with-microsoft-365-powershell.md)
- Azure AD yönetim merkezi

## <a name="group-based-licensing"></a>Grup tabanlı lisanslama

Azure AD'de güvenlik gruplarını, bir abonelik kümesinden tüm grup üyelerine otomatik olarak lisans atamak üzere yapılandırabilirsiniz. Bu, grup *tabanlı lisanslama olarak bilinir*. Gruba bir kullanıcı hesabı eklenir veya gruptan kaldırılırsa, grubun aboneliklerine yönelik lisanslar kullanıcı hesabından otomatik olarak atanır veya atanmamış olur.

Tüm grup üyeleri için yeterli lisansa sahip olduğundan emin olun. Lisans yoksa, yeni kullanıcılara lisanslar kullanılabilir olana kadar lisans atanmaz.

>[!Note]
>Azure İş (B2B) hesaplarını içeren gruplar için grup tabanlı lisanslama yapılandırmanız gerekir.
>

Daha fazla bilgi için bkz. [Azure AD'de grup tabanlı lisanslama](/azure/active-directory/fundamentals/active-directory-licensing-whatis-azure-portal).

## <a name="next-steps"></a>Sonraki adımlar

Lisans atanmış uygun kullanıcı hesapları kümesiyle artık şunları yapmaya hazırsınız:

- [Güvenlik uygulama](../security/office-365-security/security-roadmap.md)
- [Dağıtım ayarları gibi istemci yazılımlarını Microsoft 365 Uygulamaları](/DeployOffice/deployment-guide-microsoft-365-apps)
- [Cihaz yönetimini ayarlama](device-management-roadmap-microsoft-365.md)
- [Hizmetleri ve uygulamaları yapılandırma](configure-services-and-applications.md)