---
title: Temel Microsoft 365 Lighthouse dağıtma
f1.keywords: CSH
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
description: MICROSOFT 365 LIGHTHOUSE kullanarak Yönetilen Hizmet Sağlayıcıları (MSP)'ler için, temelleri Microsoft 365 Lighthouse öğrenin.
ms.openlocfilehash: c4cef0b966e1c35d5b8d4f282e5eeee4cb76a998
ms.sourcegitcommit: 6e43aeff217afe97876137b1ead8df26db6e9937
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/16/2022
ms.locfileid: "63015315"
---
# <a name="deploy-microsoft-365-lighthouse-baselines"></a>Temel Microsoft 365 Lighthouse dağıtma 

> [!NOTE]
> Bu makalede açıklanan özellikler Önizleme'dedir, değişebilir ve yalnızca gereksinimleri karşılayacak iş ortakları tarafından [kullanılabilir](m365-lighthouse-requirements.md). Henüz oturum açmadıysanız Microsoft 365 Lighthouse için [kaydolma'ya Microsoft 365 Lighthouse](m365-lighthouse-sign-up.md).

Microsoft 365 Lighthouse, kullanıcıların, cihazların ve verilerin müşteri kiracıları içinde güvenliğini sağlamak için standart yönetilen kiracı yapılandırmalarını dağıtmanıza izin verir. Deniz Feneri ile standart olarak gelen altı varsayılan taban çizgisi yapılandırma vardır:

- Yöneticiler için MFA gerektirme
- Son kullanıcılar için MFA gerektirme
- Eski Kimlik Doğrulamayı Engelle
- Cihaz Kaydı Ayarlama Microsoft Endpoint Manager – Azure AD Katılma
- Defender Virüsten Koruma ilkesi Windows yapılandırma
- Mobil cihazlar için Uyumluluk Windows yapılandırma

## <a name="before-you-begin"></a>Başlamadan önce

Sizin ve müşteri kiracıların, Kiracı gereksinimleri altında listelenen [gereksinimleri karşı Microsoft 365 Lighthouse](m365-lighthouse-requirements.md).

## <a name="learn-more-about-the-default-baseline"></a>Varsayılan taban çizgisi hakkında daha fazla bilgi

Taban **Çizgisi sayfasını** açmak için sol gezinti bölmesinde Taban Çizgisi'ni seçin. Varsayılan taban çizgisinin Önceden Varsayılan kiracı grubuna (tüm kiracılar) eklenmiştir. Varsayılan temel yapılandırmalarını görüntülemek için, **Temeli görüntüle'yi** seçerek Varsayılan temel sayfasını açın. Yapılandırmalar, dağıtım adımları olarak listelenmiştir. Dağıtım ayrıntılarını ve kullanıcı etkisini görüntülemek için herhangi bir dağıtım adımlarını seçin.

:::image type="content" source="../media/m365-lighthouse-deploy-baselines/default-baseline-page.png" alt-text="Varsayılan temel sayfası.temel sayfasının ekran >.":::

## <a name="deploy-a-baseline-configuration"></a>Temel yapılandırmayı dağıtma  

1. Deniz Feneri'nin sol gezinti bölmesinde **Kiracılar'ı** seçerek yerleşik kiracılarınızı görüntüleyin.

2. Temel yapılandırmayı dağıtmak istediğiniz kiracıyı seçin.

3. Kiracının **dağıtım** planına eklenen temelten tüm dağıtım adımlarını görmek için Dağıtım Planları sekmesini seçin.

4. Dağıtım adımı sayfasını açmak için bir dağıtım adımı seçin.

5. Seçili **dağıtım** adımını kiracıya uygulamak için Uygula'ya seçin. Dağıtım adımı "Bu eylem el ile bir adım gerektirir" ifadesini gösteriyorsa, dağıtım adımının doğru uygulanması için el ile adımı tamamlamalısınız.

## <a name="related-content"></a>İlgili içerik

[Standart kiracı yapılandırmalarını dağıtmak için taban çizgilerini kullanmaya genel bakış](m365-lighthouse-deploy-standard-tenant-configurations-overview.md) (makale)\
[Microsoft 365 Lighthouse SSS](m365-lighthouse-faq.yml) (makale)
