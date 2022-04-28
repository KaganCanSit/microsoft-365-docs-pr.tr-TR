---
title: Yalnızca bulut kimliğini Microsoft 365
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
description: Microsoft 365 aboneliğiniz yalnızca bulut kimliği kullanırken kullanıcı ve grup oluşturmayı açıklar.
ms.openlocfilehash: 7b2ad2cee32f075302ea591806214b697fa9b206
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65091379"
---
# <a name="microsoft-365-cloud-only-identity"></a>Yalnızca bulut kimliğini Microsoft 365

*Bu makale hem Microsoft 365 Kurumsal hem de Office 365 Kurumsal için geçerlidir.*

Yalnızca bulut kimlik modelini seçtiyseniz, tüm kullanıcılarınızı, gruplarınızı ve kişilerinizi depolamak için Microsoft 365 aboneliğiniz için zaten bir Azure Active Directory (Azure AD) kiracınız vardır. [Adım 2'de](protect-your-global-administrator-accounts.md) yönetici hesapları ve bu çözümün [3. Adımındaki](microsoft-365-secure-sign-in.md) kullanıcı hesapları için korumayı ayarladıktan sonra, artık kuruluşunuzun ihtiyaç duyduğu yeni hesapları ve grupları oluşturmaya başlayabilirsiniz.

Burada yalnızca bulut kimliğinin temel bileşenleri yer alır.
 
![Yalnızca bulut kimliğinin temel bileşenleri.](../media/about-microsoft-365-identity/cloud-only-identity.png)

Kuruluşlardaki kullanıcılar ve kullanıcı hesapları çeşitli yollarla kategorilere ayırılabilir. Örneğin, bazıları çalışanlardır ve kalıcı bir duruma sahiptir. Bazıları geçici durumu olan satıcılar, yükleniciler veya iş ortaklarıdır. Bazıları kullanıcı hesabı olmayan ancak etkileşim ve işbirliğini desteklemek için belirli hizmetlere ve kaynaklara erişim izni verilmesi gereken dış kullanıcılardır. Örneğin:

- Kiracı hesapları, kuruluşunuzda bulut hizmetleri için lisansladığınız kullanıcıları temsil eden

- İşletmeler arası (B2B) hesapları, işbirliğine katılmaya davet ettiğiniz kuruluşunuzun dışındaki kullanıcıları temsil eder

Kuruluşunuzdaki kullanıcı türlerinin stokunu alın. Gruplandırmalar nelerdir? Örneğin, kullanıcıları kuruluşunuz için üst düzey işleve veya amaca göre gruplandırabilirsiniz.

Ayrıca, bazı bulut hizmetleri herhangi bir kullanıcı hesabı olmadan kuruluşunuzun dışındaki kullanıcılarla paylaşılabilir. Bu kullanıcı gruplarını da tanımlamanız gerekir.

Bulut ortamınızın yönetimini basitleştiren çeşitli amaçlar için Azure AD'deki grupları kullanabilirsiniz. Örneğin, Azure AD gruplarıyla şunları yapabilirsiniz:

- Microsoft 365 lisanslarını üye olarak eklendikleri anda otomatik olarak kullanıcı hesaplarınıza atamak için grup tabanlı lisanslama kullanın.
- Bölüm adı gibi kullanıcı hesabı özniteliklerine göre belirli gruplara kullanıcı hesaplarını dinamik olarak ekleyin.
- Hizmet Olarak Yazılım (SaaS) uygulamaları için kullanıcıları otomatik olarak sağlayın ve bu uygulamalara erişimi çok faktörlü kimlik doğrulaması (MFA) ve diğer Koşullu Erişim ilkeleriyle koruyun.
- Ekipler ve SharePoint Çevrimiçi ekip siteleri için izinler ve erişim düzeyleri sağlayın.

## <a name="next-steps-for-cloud-only-identity"></a>Yalnızca bulut kimliği için sonraki adımlar

- [Kullanıcı hesaplarını yönetme](manage-microsoft-365-accounts.md)
- [Kullanıcı hesaplarına lisans atama](assign-licenses-to-user-accounts.md)
- [Grupları ve grup üyeliğini yönetme](manage-microsoft-365-groups.md)
- [Kullanıcı hesabı parolalarını yönetme](manage-microsoft-365-passwords.md)
