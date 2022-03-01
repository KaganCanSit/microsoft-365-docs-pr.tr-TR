---
title: MSSP'lere gönderilen uyarı bildirimlerini yapılandırma
description: MSSP'lere gönderilen uyarı bildirimlerini yapılandırma
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
ms.openlocfilehash: 0cead78048fcf8ef25637e969aae816b7a8d8e76
ms.sourcegitcommit: dfa9f28a5a5055a9530ec82c7f594808bf28d0dc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/29/2021
ms.locfileid: "62997030"
---
# <a name="configure-alert-notifications-that-are-sent-to-mssps"></a>MSSP'lere gönderilen uyarı bildirimlerini yapılandırma

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Defender'ı deneyimli yapmak mı istiyor musunuz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-mssp-support-abovefoldlink)

> [!NOTE]
> Bu adım, MSSP müşterisi veya MSSP tarafından yapılabilir. MSSP müşterisi adına BUNU yapılandırmak için MSSP'lere uygun izinlerin verilmesi gerekir.

Portala erişim verildikten sonra, kiracıyla ilişkili uyarılar oluşturulduğunda ve koşulların karşılandıktan sonra E-postaların MSSP'lere gönderilmesi için uyarı bildirimi kuralları oluşturulabilir.

Daha fazla bilgi için bkz [. Uyarı bildirimleri için kural oluşturma](configure-email-notifications.md#create-rules-for-alert-notifications).

Bu onay kutuları denetlenir:

- **Kuruluş adını ekle** - Müşteri adı e-posta bildirimlerine eklenecek
- **Kiracıya özgü portal bağlantısını dahil** etme - Uyarı bağlantısı URL'sinin, hedef kiracı portalına doğrudan erişimi sağlayan kiracıya özgü bir parametresi (tid=target_tenant_id) olur

## <a name="related-topics"></a>İlgili konular

- [Portala MSSP erişimi ver](grant-mssp-access.md)
- [MSSP müşteri portalına erişme](access-mssp-portal.md)
- [Müşteri kiracısı uyarılarını getirme](fetch-alerts-mssp.md)
