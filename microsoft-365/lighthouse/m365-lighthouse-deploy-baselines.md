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
ms.openlocfilehash: fa443fa025f0a1ffba6a230427797755611328a3
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63324638"
---
# <a name="deploy-microsoft-365-lighthouse-baselines"></a>Temel Microsoft 365 Lighthouse dağıtma 

Microsoft 365 Lighthouse, kullanıcıların, cihazların ve verilerin müşteri kiracıları içinde güvenliğini sağlamak için standart yönetilen kiracı yapılandırmalarını dağıtmanıza izin verir. Deniz Feneri ile standart olarak gelen yedi varsayılan taban çizgisi yapılandırmaları vardır:

- Yöneticiler için MFA gerektirme
- Son kullanıcılar için MFA gerektirme
- Eski Kimlik Doğrulamayı Engelle
- Cihaz Kaydı Ayarlama Microsoft Endpoint Manager – Azure AD Katılma
- Windows için Defender Virüsten Koruma Windows 10 ve sonrası için yapılandırma
- Güvenlik Duvarı'nı güvenlik Windows 10 yapılandırma
- Uyumluluk İlkesini Uyumluluk Windows 10 ve sonrası için yapılandırma

## <a name="before-you-begin"></a>Başlamadan önce

Sizin ve müşteri kiracıların, Kiracı gereksinimleri altında listelenen [gereksinimleri karşı Microsoft 365 Lighthouse](m365-lighthouse-requirements.md).

## <a name="learn-more-about-the-default-baseline"></a>Varsayılan taban çizgisi hakkında daha fazla bilgi

Deniz **Feneri'nde** sol gezinti bölmesinde Taban Çizgisi'ni seçerek Taban Çizgisi sayfasını açın. Varsayılan taban çizgisinin Önceden Varsayılan kiracı grubuna (tüm kiracılar) eklenmiştir. Varsayılan temel yapılandırmalarını görüntülemek için, **Temeli görüntüle'yi** seçerek Varsayılan temel sayfasını açın. Yapılandırmalar, dağıtım adımları olarak listelenmiştir. Dağıtım ayrıntılarını ve kullanıcı etkisini görüntülemek için herhangi bir dağıtım adımlarını seçin.

:::image type="content" source="../media/m365-lighthouse-deploy-baselines/default-baseline-page.png" alt-text="Varsayılan taban çizgisi sayfasının ekran görüntüsü.":::

## <a name="deploy-a-baseline-configuration"></a>Temel yapılandırmayı dağıtma  

1. Deniz Feneri'nin sol gezinti bölmesinde **Kiracılar'ı** seçerek yerleşik kiracılarınızı görüntüleyin.

2. Temel yapılandırmayı dağıtmak istediğiniz kiracıyı seçin.

3. Kiracının **dağıtım** planına eklenen temelten tüm dağıtım adımlarını görmek için Dağıtım Planları sekmesini seçin.

4. Dağıtım adımı sayfasını açmak için bir dağıtım adımı seçin.

5. Seçilen **dağıtım adımını kiracıya** uygulamak için Gözden Geçir ve Uygula'ya seçin. Dağıtım adımı "Bu eylem el ile bir adım gerektirir" ifadesini gösteriyorsa, dağıtım adımının doğru uygulanması için el ile adımı tamamlamalısınız.

## <a name="related-content"></a>İlgili içerik

[Standart kiracı yapılandırmalarını dağıtmak için taban çizgilerini kullanmaya genel bakış](m365-lighthouse-deploy-standard-tenant-configurations-overview.md) (makale)\
[Microsoft 365 Kiracılar sayfasına genel bakış](m365-lighthouse-tenants-page-overview.md) (makale)\
[Microsoft 365 Lighthouse SSS](m365-lighthouse-faq.yml) (makale)\
[Portal Microsoft 365 Lighthouse yapılandırma](m365-lighthouse-configure-portal-security.md) (makale) 