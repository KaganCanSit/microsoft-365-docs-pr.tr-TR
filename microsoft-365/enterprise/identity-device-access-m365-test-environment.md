---
title: Test ortamınız için kimlik Microsoft 365 cihaz erişimi
author: kelleyvice-msft
f1.keywords:
- NOCSH
ms.author: kvice
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
ms.custom: ''
description: Kimliği ve Microsoft 365 erişimini test etmek için bir kullanıcı ortamı oluşturun.
ms.openlocfilehash: 488bd22b555ab30a27e0d9c8ef662af1b6945da9
ms.sourcegitcommit: 6c57f1e90339d5a95c9e7875599dac9d3e032c3a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/04/2022
ms.locfileid: "63016466"
---
# <a name="identity-and-device-access-for-your-microsoft-365-test-environment"></a>Test ortamınız için kimlik Microsoft 365 cihaz erişimi

*Bu Test Laboratuvarı Kılavuzu yalnızca kurumsal test Microsoft 365 test ortamları için kullanılabilir.*

[Kimlik ve cihaz erişimi yapılandırmaları](../security/office-365-security/microsoft-365-policies-configurations.md), Azure Active Directory (Azure AD) ile tümleştirilmiş tüm hizmetlere erişimi korumak için önerilen yapılandırmalar ve koşullu erişim ilkeleridir.

Ortak kimlik ve cihaz erişim yapılandırmalarının olduğu bir test ortamı oluşturmak için:

1. Kimlik modeli ve kimlik doğrulama yöntemi seçiminizi temel alarak, test ortamınızı önkoşul kimlik ve güvenlik özellikleriyle yapılandırma:

  - [Yalnızca bulut](cloud-only-prereqs-m365-test-environment.md)
  - [Parola karması eşitlemesi (PHS)](phs-prereqs-m365-test-environment.md)
  - [Geçişli kimlik doğrulaması (PTA)](pta-prereqs-m365-test-environment.md)

2. Test [ortamınız için yapılandırılmış](../security/office-365-security/identity-access-policies.md) önkoşulları temel alan ilkeleri yapılandırmak ve kimlikler ile cihazlar için korumayı araştırmak ve doğrulamak için Ortak kimlik ve cihaz erişim ilkelerini kullanın.

## <a name="see-also"></a>Ayrıca bkz.

[Ek kimlik Test Laboratuvarı Kılavuzları](m365-enterprise-test-lab-guides.md#identity)

[Kimliği dağıtma](deploy-identity-solution-overview.md)

[Microsoft 365 Test Laboratuvarı Kılavuzları için kılavuzlar](m365-enterprise-test-lab-guides.md)

[Microsoft 365 genel bakış için genel bakış](microsoft-365-overview.md)

[Microsoft 365 belgeleri için belgeler](/microsoft-365-enterprise/)
