---
title: Multi-Geo Microsoft 365 Bulma'yi yapılandırma
ms.reviewer: adwood
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
f1.keywords:
- NOCSH
ms.custom: seo-marvel-apr2020
ms.localizationpriority: medium
ms.collection: Strat_SP_gtc
description: eKover'ı Multi-Geo'da uydu konumlarında kullanmak üzere yapılandırmak için Region Microsoft 365 kullanmayı öğrenin.
ms.openlocfilehash: 1bdf03a7c639e659d1b4ec12c691c65863318ad7
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62984468"
---
# <a name="microsoft-365-multi-geo-ediscovery-configuration"></a>Microsoft 365 Multi-Geo eK bulma yapılandırması

[Advanced eDiscovery özellikleri](../compliance/overview-ediscovery-20.md), çok coğrafi eBulma yöneticisinin "Bölge" güvenlik filtresi kullanmak zorunda kalmadan tüm coğrafi verileri aramasına olanak sağlar. Veriler, çok coğrafi kiracının merkezi konumunun Azure örneğine dışarı aktarıldı. 

Gelişmiş eBulma özellikleri olmadan, eBulma yöneticisi veya çok coğrafi bir kiracı yöneticisi eKbulma'ı yalnızca o kiracının merkezi konumda yürütebilirsiniz. Uydu konumları için eKbulma'nın yönetilebilme olanağını desteklemek için PowerShell üzerinden "Bölge" adlı yeni bir uyumluluk güvenlik filtresi parametresi kullanılabilir. Bu parametre, merkezi konumu Kuzey Amerika, Avrupa veya Asya Pasifik'te olan kiracılar tarafından kullanılabilir. Advanced eDiscovery konumu Kuzey Amerika, Avrupa veya Asya Pasifik'te olmayan ve uydu coğrafi konumlarında eK bağlantısı gerçekleştirmesi gereken kiracılar için önerilen bir öneridir. 

Microsoft 365 genel yöneticisinin, diğer kullanıcıların eBulma gerçekleştirmesine izin vermek ve eBulma'nın uydu konumu olarak gerçekleştirecek bölgeyi belirtmek üzere geçerli Uyumluluk Güvenlik Filtrelerinde bir "Bölge" parametresi ataması gerekir, aksi takdirde uydu konumu için eKbulma yapılmaz.

eBulma Yöneticisi veya Yönetici rolü belirli bir uydu konumu için ayarlanmışsa, eBulma Yöneticisi veya Yönetici, bu uydu konumu içinde bulunan SharePoint siteleri ve OneDrive sitelerinde yalnızca eBulma arama eylemleri gerçekleştirebilirsiniz. eBulma Yöneticisi veya Yönetici belirtilen uydu konumu SharePoint ya da OneDrive herhangi bir konumda arama yapmak isterse, hiçbir sonuç döndürülilmez. Ayrıca, uydu konumu için eBulma Yöneticisi veya Yöneticisi bir dışarı aktarmayı tetiklese, veriler o bölgenin Azure örneğine dışarı aktarıldı. Bu, kuruluşların denetimli kenarlıklar arasında içerik dışarı aktarılamalarına izin vermelerine yardımcı olur.

> [!NOTE]
> eBulma Yöneticisi'nin birden çok SharePoint uydu konumda araması gerekiyorsa, OneDrive veya SharePoint uydularının bulunduğu alternatif uydu konumunu belirten eBulma Yöneticisi için başka bir kullanıcı hesabı oluşturulyacaktır.

[!INCLUDE [Microsoft 365 Multi-Geo locations](../includes/microsoft-365-multi-geo-locations.md)]

Bir Bölgenin Uyumluluk Güvenlik Filtresini ayarlamak için:

1. [Bağlan ve Uyumluluk Microsoft 365 PowerShell& i ziyaret edin](/powershell/exchange/connect-to-scc-powershell)

2. Aşağıdaki sözdizimini kullanın:

   ```powershell
   New-ComplianceSecurityFilter -Action All -FilterName <TheNameYouWantToAssign> -Region <RegionValue> -Users <UserPrincipalName>
   ```

   Örneğin:

   ```powershell
   New-ComplianceSecurityFilter -Action All -FilterName "NAM eDiscovery Managers" -Region NAM -Users adwood@contoso.onmicrosoft.com
   ```

Ek parametreler [ve söz dizimi için New-ComplianceSecurityFilter](/powershell/module/exchange/new-compliancesecurityfilter) makalesine bakın.