---
title: Kullanıcı hesaplarına Microsoft 365 lisansları atama
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: Kullanıcı hesaplarına tek tek veya grup üyeliğine dayalı olarak Microsoft 365 lisansların nasıl atandığı açıklanır.
ms.openlocfilehash: ab9769aa4dee6a9f7982f72f377b0c7e0d3f444e
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65091423"
---
# <a name="assign-microsoft-365-licenses-to-user-accounts"></a>Kullanıcı hesaplarına Microsoft 365 lisansları atama

*Bu makale hem Microsoft 365 Kurumsal hem de Office 365 Kurumsal için geçerlidir.*

Yalnızca bulut kimlik modeli için, Microsoft 365 lisansları nasıl oluşturduğunuza bağlı olarak kullanıcı hesaplarına oluşturuldukları şekilde atayabilirsiniz.

Karma kimlik modeli için, Active Directory Domain Services (AD DS) kullanıcı hesapları ilk kez eşitlendiğinde, bunlara otomatik olarak bir konum veya Microsoft 365 lisansı atanamaz. **Lisans atamadan önce veya atamadan önce her kullanıcı hesabını bir kullanıcı konumuyla yapılandırmanız gerekir.**

Her iki durumda da, kullanıcılarınızın e-posta ve Microsoft Teams gibi Microsoft 365 hizmetlerine erişebilmesi için kullanıcı hesaplarına bir lisans atamanız gerekir.

Kullanıcı hesaplarına lisansları tek tek veya grup üyeliği aracılığıyla otomatik olarak atayabilirsiniz.

Tek tek kullanıcı hesaplarına Microsoft 365 lisansları atamak için şunları kullanabilirsiniz:

- [Microsoft 365 yönetim merkezi](../admin/manage/assign-licenses-to-users.md)
- [PowerShell](assign-licenses-to-user-accounts-with-microsoft-365-powershell.md)
- Azure AD yönetim merkezi

## <a name="group-based-licensing"></a>Grup tabanlı lisanslama

Azure AD'de güvenlik gruplarını, bir abonelik kümesindeki lisansları grubun tüm üyelerine otomatik olarak atayacak şekilde yapılandırabilirsiniz. Bu, *grup tabanlı lisanslama* olarak bilinir. Gruba bir kullanıcı hesabı eklenirse veya gruptan kaldırılırsa, grup abonelikleri için lisanslar otomatik olarak atanır veya kullanıcı hesabından atanmamış olur.

Tüm grup üyeleri için yeterli lisansa sahip olduğunuzdan emin olun. Lisanslar tükenirse, lisanslar kullanılabilir duruma gelene kadar yeni kullanıcılara lisans atanamaz.

>[!Note]
>Azure işletmeden işletmeye (B2B) hesapları içeren gruplar için grup tabanlı lisanslama yapılandırmamalısınız.
>

Daha fazla bilgi için bkz. [Azure AD'de grup tabanlı lisanslama](/azure/active-directory/fundamentals/active-directory-licensing-whatis-azure-portal).

## <a name="next-steps"></a>Sonraki adımlar

Lisans atanmış uygun kullanıcı hesapları kümesiyle artık şunları yapmaya hazırsınız:

- [Güvenlik uygulama](../security/office-365-security/security-roadmap.md)
- [Microsoft 365 Uygulamaları gibi istemci yazılımlarını dağıtma](/DeployOffice/deployment-guide-microsoft-365-apps)
- [Cihaz yönetimini ayarlama](device-management-roadmap-microsoft-365.md)
- [Hizmetleri ve uygulamaları yapılandırma](configure-services-and-applications.md)