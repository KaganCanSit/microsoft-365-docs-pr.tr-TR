---
title: Cihaz uyumluluk ilkesi ayarlarını karşılaştırma
f1.keywords: NOCSH
ms.author: sharik
author: SKjerland
manager: scotv
audience: Admin
ms.topic: article
ms.prod: microsoft-365-lighthouse
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolio
- M365-Lighthouse
search.appverid: MET150
description: Yönetilen Servis Sağlayıcıları (MSP) Microsoft 365 Lighthouse, cihaz uyumluluk ilkesi ayarlarını karşılaştırmayı öğrenin.
ms.openlocfilehash: 5e4fc396e2ea1e1cce576f6064f4239179db33cc
ms.sourcegitcommit: 6e43aeff217afe97876137b1ead8df26db6e9937
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/16/2022
ms.locfileid: "63015313"
---
# <a name="compare-device-compliance-policy-settings"></a>Cihaz uyumluluk ilkesi ayarlarını karşılaştırma

> [!NOTE]
> Bu makalede açıklanan özellikler Önizleme'dedir, değişebilir ve yalnızca gereksinimleri karşılayacak iş ortakları tarafından [kullanılabilir](m365-lighthouse-requirements.md). Henüz oturum açmadıysanız Microsoft 365 Lighthouse için [kaydolma'ya Microsoft 365 Lighthouse](m365-lighthouse-sign-up.md).

Microsoft 365 Lighthouse, kiracılar genelinde uyumluluk ilkelerini tek bir görünümde görüntülemenize olanak sağlar. İlkeleri karşılaştırarak kiracılar arasında güvenliği ve standardlaştırmayı sabilirsiniz. Yapılandırılmış ayarları (yapılandırılmamış olan ayarlarla), yapılandırmalarında farklı olan ayarları veya eşleşmelerini görmek için görünümlere filtre  edebilirsiniz. Ayrıca, ilkeler arasında nasıl karşılaştır olduklarını görmek için belirli ayarları da arayabilirsiniz.

## <a name="before-you-begin"></a>Başlamadan önce

Cihazların Microsoft Intune lisansına sahip olduğundan ve ODT (MEM) Microsoft Endpoint Manager emin olun.

## <a name="compare-policy-settings"></a>İlke ayarlarını karşılaştırma

1. Deniz Feneri'nin sol gezinti bölmesinde Cihazlar'ı **seçin**.

2. **İlkeler sekmesini** seçin.

3. Filtreler **açılan** listesinden bir işletim sistemi veya platform seçin.

   > [!NOTE]
   > İlkeleri yalnızca aynı işletim sistemi veya platformla karşılaştırabilirsiniz.

4. Filtrelenmiş listeden karşılaştırmak istediğiniz en çok üç ilke seçin.

5. **Karşılaştır'ı seçin**.

Farklı, aynı ayarları veya **Ayarlar ayarları görmek** **Ayarlar sonuçları** **filtre edebilirsiniz**.

## <a name="configure-a-policy-setting"></a>İlke ayarını yapılandırma

1. Deniz Feneri'nin sol gezinti bölmesinde Cihazlar'ı **seçin**.

2. **İlkeler sekmesini** seçin.

3. Listeden bir ilke adı seçin.

4. İlke ayrıntıları bölmesinde Bu ilkeyi **şu şekilde görüntüle: seçeneğini Microsoft Endpoint Manager**.

5. MEM'de, ilke ayarlarını gereken şekilde düzenleyin.

## <a name="next-steps"></a>Sonraki adımlar

İlke ayarlamaları yapınken, değişikliklerinizi geçerli taban çizgisi ayarlarınıza göre değerlendirin. Daha fazla bilgi için bkz [. Standart kiracı yapılandırmalarını dağıtmak için taban çizgilerini kullanmaya genel bakış](m365-lighthouse-deploy-standard-tenant-configurations-overview.md).

## <a name="related-content"></a>İlgili içerik

[Intune'da cihaz kaydı nedir?](/mem/intune/enrollment/device-enrollment) (makale)  
[Intune ile yönettikleri cihazlar için kurallar ayarlamak için uyumluluk ilkelerini kullanma](/mem/intune/protect/device-compliance-get-started) (makale)  
[Standart kiracı yapılandırmalarını dağıtmak için taban çizgilerini kullanmaya genel bakış](m365-lighthouse-deploy-standard-tenant-configurations-overview.md) (makale)
