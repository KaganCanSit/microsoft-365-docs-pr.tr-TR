---
title: Microsoft 365 test ortamınız için kimlik ve cihaz erişimi
author: kelleyvice-msft
f1.keywords:
- NOCSH
ms.author: kvice
manager: scotv
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
ms.custom: ''
description: Kimlik ve cihaz erişimini test etmek için bir Microsoft 365 ortamı oluşturun.
ms.openlocfilehash: 09c7bf9ecb6aaadc89cedfd881e66a5fd19f28d7
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65091225"
---
# <a name="identity-and-device-access-for-your-microsoft-365-test-environment"></a>Microsoft 365 test ortamınız için kimlik ve cihaz erişimi

*Bu Test Laboratuvarı Kılavuzu yalnızca kurumsal test ortamları için Microsoft 365 için kullanılabilir.*

[Kimlik ve cihaz erişim yapılandırmaları](../security/office-365-security/microsoft-365-policies-configurations.md), Azure Active Directory (Azure AD) ile tümleştirilen tüm hizmetlere erişimi korumak için önerilen yapılandırmalar ve koşullu erişim ilkeleri kümesidir.

Ortak kimlik ve cihaz erişim yapılandırmalarının bulunduğu bir test ortamı oluşturmak için:

1. Seçtiğiniz kimlik modeline ve kimlik doğrulama yöntemine göre test ortamınızı önkoşul kimlik ve güvenlik özellikleriyle yapılandırın:

  - [Yalnızca bulut](cloud-only-prereqs-m365-test-environment.md)
  - [Parola karması eşitlemesi (PHS)](phs-prereqs-m365-test-environment.md)
  - [Doğrudan kimlik doğrulaması (PTA)](pta-prereqs-m365-test-environment.md)

2. Test ortamınız için yapılandırılmış önkoşulları temel alan ilkeleri yapılandırmak ve kimlikler ve cihazlar için korumayı keşfetmek ve doğrulamak için [Ortak kimlik ve cihaz erişim ilkelerini](../security/office-365-security/identity-access-policies.md) kullanın.

## <a name="see-also"></a>Ayrıca bkz.

[Ek kimlik Test Laboratuvarı Kılavuzları](m365-enterprise-test-lab-guides.md#identity)

[Kimliği dağıtma](deploy-identity-solution-overview.md)

[Kurumsal Test Laboratuvarı Kılavuzları için Microsoft 365](m365-enterprise-test-lab-guides.md)

[Microsoft 365 Kurumsal’a genel bakış](microsoft-365-overview.md)

[Kurumsal belgeler için Microsoft 365](/microsoft-365-enterprise/)
