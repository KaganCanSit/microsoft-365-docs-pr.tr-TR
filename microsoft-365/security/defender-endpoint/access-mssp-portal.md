---
title: MSSP Microsoft 365 Defender portalına erişme
description: MSSP Microsoft 365 Defender portalına erişme
keywords: yönetilen güvenlik hizmeti sağlayıcısı, mssp, yapılandırma, tümleştirme
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 5a359938dbee85ea64b5f46804761410cae1f48e
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2021
ms.locfileid: "62973866"
---
# <a name="access-the-microsoft-365-defender-mssp-customer-portal"></a>MSSP Microsoft 365 Defender portalına erişme

**Aşağıdakiler için geçerlidir:**
- [ Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [ Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


> Uç Nokta için Microsoft Defender'ı mı deneyimliysiniz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-mssp-support-abovefoldlink)

> [!NOTE]
> Bu adım kümesi MSSP'ye yöneliktir.

Varsayılan olarak, MSSP müşterileri Microsoft 365 Defender URL aracılığıyla kiracılarına erişim sağlar: `https://securitycenter.windows.com/`.

Ancak MSSP'lerin kiracıya özgü URL'leri aşağıdaki biçimde kullanmaları gerekir:  `https://securitycenter.windows.com?tid=customer_tenant_id` MSSP müşteri portalına erişmek için.

Genel olarak, MSSP'ler yönetmeyi amaçlasa da, MSSP müşterilerinin Azure AD'sinde yer alan her bir kullanıcıya eklenmiştir.

MSSP müşteri kiracı kimliğini almak için aşağıdaki adımları izleyin ve sonra da kimliği kullanarak kiracıya özgü URL'ye erişin:

1. MSSP olarak, kimlik bilgilerinizle Azure AD'de oturum açma.

2. Dizinden MSSP müşterisi kiracısına geçiş.

3. **Özellikler'Azure Active Directory > seçin**. Kiracı kimliğini Dizin Kimliği alanında bulabilirsiniz.

4. MSSP müşteri portalına, değeri aşağıdaki `customer_tenant_id` URL'de değiştirerek erişin: `https://securitycenter.windows.com/?tid=customer_tenant_id`.

## <a name="related-topics"></a>İlgili konular

- [Portala MSSP erişimi ver](grant-mssp-access.md)
- [Uyarı bildirimlerini yapılandırma](configure-mssp-notifications.md)
- [Müşteri kiracısı uyarılarını getirme](fetch-alerts-mssp.md)
