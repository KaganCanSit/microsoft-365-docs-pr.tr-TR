---
title: Microsoft 365 bulut kimliği
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
description: Yeni aboneliğiniz yalnızca bulut kimliğini kullanırken Microsoft 365 ve grup oluşturma hakkında bilgi sağlar.
ms.openlocfilehash: 81c13a6b7e32883d4cb846ef5956102f08fecd6e
ms.sourcegitcommit: 6c57f1e90339d5a95c9e7875599dac9d3e032c3a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/04/2022
ms.locfileid: "63016443"
---
# <a name="microsoft-365-cloud-only-identity"></a>Microsoft 365 bulut kimliği

*Bu makale hem son hem de Microsoft 365 Kurumsal hem de Office 365 Kurumsal.*

Yalnızca bulut kimlik modelini seçtiysanız, kullanıcılarınızı, gruplarınızı ve kişilerinizi Azure Active Directory depolamak için Microsoft 365 aboneliğiniz için zaten bir Azure Active Directory (Azure AD) kiracınız vardır. [2](protect-your-global-administrator-accounts.md). Adımda yönetici hesapları için korumayı ve bu çözümün [3](microsoft-365-secure-sign-in.md). Adım'daki kullanıcı hesaplarını ayardikten sonra, artık kuruma gereken yeni hesapları ve grupları oluşturmaya başlamaya hazırsınız.

Burada, yalnızca bulut kimliğinin temel bileşenleri ve bilgileri ve bilgileri ve hizmetleri ve diğer bileşenleri ve daha sonralarını açıklarız.
 
![Yalnızca bulut kimliğinin temel bileşenleri.](../media/about-microsoft-365-identity/cloud-only-identity.png)

Kuruluşlarda kullanıcılar ve onların kullanıcı hesapları çeşitli yollarla kategorilere ayırabilirsiniz. Örneğin, bazıları çalışandır ve kalıcı bir durumundadır. Bazı satıcılar, yükleniciler veya geçici durumu olan iş ortaklarıdır. Bazılarına kullanıcı hesabı yoktur, ancak etkileşim ve işbirliğini desteklemek için yine de belirli hizmetlere ve kaynaklara erişim verilmesi gerekir. Örneğin:

- Kiracı hesapları, kuruluş içinde yer alan ve bulut hizmetleri için lisans lisansla

- İşletmeler Için (B2B) hesapları, iş birliğine katılmaya davet etmek için davet edilen kuruluş dışındaki kullanıcıları temsil ediyor

Kurumda kullanıcı türlerinin hisse senedini alın. Gruplamalar nedir? Örneğin, kullanıcıları üst düzey bir işleve veya amacına göre kuruluşa göre grupabilirsiniz.

Buna ek olarak, bazı bulut hizmetleri herhangi bir kullanıcı hesabı olmadan kuruluş dışındaki kullanıcılarla paylaşılır. Bu kullanıcı gruplarını da tanımlamanız gerekir.

Azure AD'de grupları, bulut ortamınızı yönetimini basitleştirmek için çeşitli amaçlarla kullanabilirsiniz. Örneğin, Azure AD gruplarında şunları kullanabilirsiniz:

- Grup tabanlı lisansları, üye olarak Microsoft 365 hesaplarınıza otomatik olarak lisans atamak için kullanın.
- Kullanıcı hesaplarını, bölüm adı gibi kullanıcı hesabı özniteliklerine göre dinamik olarak belirli gruplara ekleyin.
- Hizmet Olarak Yazılım (SaaS) uygulamaları için kullanıcıları otomatik olarak sağlama ve çok faktörlü kimlik doğrulaması (MFA) ve diğer Koşullu Erişim ilkeleriyle bu uygulamalara erişimi korumak için.
- Ekipler ve çevrimiçi ekip siteleri için izinler SharePoint erişim düzeyleri.

## <a name="next-steps-for-cloud-only-identity"></a>Yalnızca bulut kimliği için sonraki adımlar

- [Kullanıcı hesaplarını yönetme](manage-microsoft-365-accounts.md)
- [Kullanıcı hesaplarına lisans atama](assign-licenses-to-user-accounts.md)
- [Grupları ve grup üyeliğini yönetme](manage-microsoft-365-groups.md)
- [Kullanıcı hesabı parolalarını yönetme](manage-microsoft-365-passwords.md)
