---
title: Yönetilen güvenlik hizmeti sağlayıcısı desteğini yapılandırma
description: Uç Nokta için Microsoft Defender ile MSSP tümleştirmesini yapılandırmak için gerekli adımları izleyin
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
ms.openlocfilehash: 1a9a7e24bc08338549a78fcf9e9b2756701cd83f
ms.sourcegitcommit: dd6514ae173f1c821d4ec25298145df6cb232e2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2022
ms.locfileid: "63014051"
---
# <a name="configure-managed-security-service-provider-integration"></a>Yönetilen güvenlik hizmeti sağlayıcısı tümleştirmesi yapılandırma

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Defender'ı deneyimli yapmak mı istiyor musunuz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-mssp-support-abovefoldlink)

[!include[Prerelease information](../../includes/prerelease.md)]

Yönetilen güvenlik hizmeti sağlayıcısı (MSSP) tümleştirmeyi etkinleştirmek için aşağıdaki yapılandırma adımlarını atabilirsiniz.

> [!NOTE]
> Bu makalede, hizmet sağlayıcıyla hizmet tüketicisi arasında ayrım yapmak için aşağıdaki terimler kullanılır:
>
> - MSSP'ler: Bir kuruluş için güvenlik cihazlarını izleme ve yönetme teklif sunan güvenlik kuruluşları.
> - MSSP müşterileri: MSSP'ler hizmetleriyle etkileşime girmeleri için kuruluşlar.

Tümleştirme, MSSP'lere aşağıdaki eylemleri gerçekleştirecek:

- MSSP müşterisi posta portalına Microsoft 365 Defender alma
- E-posta bildirimlerini alın ve
- Güvenlik bilgileri ve olay yönetimi (SIEM) araçlarıyla uyarıları getirme

MSSP'ler bu eylemleri gerçekleştiremeden önce, MSSP müşterisi portala erişmek için kendi Uç Nokta kiracısı için Defender'a erişim izni ver yapmalıdır.

MSSP müşterileri normalde, MSSP'lere Güvenlik Merkezi kiracılarına erişim vermek için Windows Defender adımlarını alır. Erişim verildikten sonra, diğer yapılandırma adımları MSSP müşterisi veya MSSP tarafından yapılabilir.

Genelde aşağıdaki yapılandırma adımlarının benim alınması gerekir:

- **E-postanıza MSSP Microsoft 365 Defender**

  Bu eylemin MSSP müşterisi tarafından yapılması gerekir. MSSP'ye, Uç nokta kiracısı için MSSP müşterisi Defender'a erişim izni sağlar.

- **MSSP'lere gönderilen uyarı bildirimlerini yapılandırma**

  Bu eylem, MSSP müşterisi veya MSSP tarafından  alınır. Böylece MSSP'ler, MSSP müşterisi için hangi uyarılara ihtiyaçları olduğunu biliyor olur.

- **MSSP müşterisini kiracıdan SIEM sistemine uyarıları getirme**

  Bu eylem MSSP tarafından  alınır. MSSP'lerin SIEM araçlarında uyarı getirmesini sağlar.

- **API'leri kullanarak MSSP müşteri kiracısına uyarılar getirme**

  Bu eylem MSSP tarafından  alınır. MSSP'lerin API'leri kullanarak uyarı getirmesini sağlar.

## <a name="multi-tenant-access-for-mssps"></a>MSSP'ler için çok kiracılı erişim

Çok kiracılı temsilcili erişim uygulama hakkında bilgi için bkz. Yönetilen Güvenlik Hizmeti Sağlayıcıları [için Çok Kiracılı Erişim](https://techcommunity.microsoft.com/t5/microsoft-defender-atp/multi-tenant-access-for-managed-security-service-providers/ba-p/1533440).

## <a name="related-topics"></a>İlgili konular

- [Portala MSSP erişimi ver](grant-mssp-access.md)
- [MSSP müşteri portalına erişme](access-mssp-portal.md)
- [Uyarı bildirimlerini yapılandırma](configure-mssp-notifications.md)
- [Müşteri kiracısı uyarılarını getirme](fetch-alerts-mssp.md)
