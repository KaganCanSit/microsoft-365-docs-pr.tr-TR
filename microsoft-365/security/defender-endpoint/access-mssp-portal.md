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
ms.openlocfilehash: b1c133048e6600d553f0530e135ebfc2c441dd84
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63323675"
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

Varsayılan olarak, MSSP müşterileri aşağıdaki URL Microsoft 365 Defender kiracılarına erişim sağlar: `https://security.microsoft.com/`.

Ancak MSSP'lerin kiracıya özgü URL'leri aşağıdaki biçimde kullanmaları gerekir:  `https://security.microsoft.com?tid=customer_tenant_id` MSSP müşteri portalına erişmek için.

Genel olarak, MSSP'ler yönetmeyi amaçlasa da, MSSP müşterilerinin Azure AD'sinde yer alan her bir kullanıcıya eklenmiştir.

MSSP müşteri kiracı kimliğini almak için aşağıdaki adımları izleyin ve sonra da kimliği kullanarak kiracıya özgü URL'ye erişin:

1. MSSP olarak, kimlik bilgilerinizle Azure AD'de oturum açma.

2. Dizinden MSSP müşterisi kiracısına geçiş.

3. **Özellikler'Azure Active Directory > seçin**. Kiracı kimliğini Dizin Kimliği alanında bulabilirsiniz.

4. MSSP müşteri portalına, değeri aşağıdaki `customer_tenant_id` URL'de değiştirerek erişin: `https://security.microsoft.com/?tid=customer_tenant_id`.

## <a name="related-topics"></a>İlgili konular

- [Portala MSSP erişimi ver](grant-mssp-access.md)
- [Uyarı bildirimlerini yapılandırma](configure-mssp-notifications.md)
- [Müşteri kiracısı uyarılarını getirme](fetch-alerts-mssp.md)
