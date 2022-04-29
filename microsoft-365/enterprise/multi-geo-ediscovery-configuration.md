---
title: Multi-Geo Microsoft 365 eKeşif'i yapılandırma
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
description: Microsoft 365 Multi-Geo'daki uydu konumlarında kullanılmak üzere eBulma'nın yapılandırılması için Region parametresini kullanmayı öğrenin.
ms.openlocfilehash: a220e68e6dbe010f2eab6876dc2813dcd84d5d6d
ms.sourcegitcommit: fdd0294e6cda916392ee66f5a1d2a235fb7272f8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/29/2022
ms.locfileid: "65130943"
---
# <a name="microsoft-365-multi-geo-ediscovery-configuration"></a>Multi-Geo eBulma yapılandırması Microsoft 365

[eBulma (Premium) özellikleri](../compliance/overview-ediscovery-20.md), çok coğrafi bölgeli bir eBulma yöneticisinin "Bölge" güvenlik filtresi kullanmak zorunda kalmadan tüm coğrafi bölgeleri aramasına olanak sağlar. Veriler, çok coğrafi kiracının merkezi konumunun Azure örneğine aktarılır.

eBulma (Premium) özellikleri olmadan, çok coğrafili bir kiracının eBulma yöneticisi veya yöneticisi eKeşif'i yalnızca bu kiracının merkezi konumunda gerçekleştirebilecektir. Uydu konumları için eBulma özelliğinin yürütülmesini desteklemek için PowerShell aracılığıyla "Region" adlı yeni bir uyumluluk güvenlik filtresi parametresi kullanılabilir. Bu parametre, merkezi konumu Kuzey Amerika, Avrupa veya Asya Pasifik'te olan kiracılar tarafından kullanılabilir. Merkezi konumu Kuzey Amerika, Avrupa veya Asya Pasifik'te olmayan ve uydu coğrafi konumlarında eBulma gerçekleştirmesi gereken kiracılar için eBulma (Premium) önerilir.

Microsoft 365 genel yöneticisinin, başkalarının eBulma gerçekleştirmesine izin vermek için eBulma Yöneticisi izinleri ataması ve eBulma işleminin uydu konumu olarak yürütüleceği bölgeyi belirtmek üzere ilgili Uyumluluk Güvenlik Filtrelerinde bir "Bölge" parametresi ataması gerekir; aksi takdirde, uydu konumu için eBulma gerçekleştirilmeyecektir. Kullanıcı başına yalnızca bir "Bölge" güvenlik filtresi desteklenir, bu nedenle tüm bölgelerin aynı güvenlik filtresi içinde olması gerekir.

eBulma Yöneticisi veya Yönetici rolü belirli bir uydu konumu için ayarlandığında, eBulma Yöneticisi veya Yönetici yalnızca o uydu konumunda bulunan SharePoint siteleri ve OneDrive sitelerinde eBulma arama eylemleri gerçekleştirebilir. Bir eBulma Yöneticisi veya Yönetici belirtilen uydu konumu dışındaki SharePoint veya OneDrive siteleri aramayı denerse hiçbir sonuç döndürülmeyecektir. Ayrıca, uydu konumunun eBulma Yöneticisi veya Yöneticisi dışarı aktarmayı tetiklediğinde veriler o bölgenin Azure örneğine aktarılır. Bu, içeriğin denetimli kenarlıklar arasında dışarı aktarılmasına izin vermeyerek kuruluşların uyumlu kalmasına yardımcı olur.

> [!NOTE]
> Bir eBulma Yöneticisinin birden çok SharePoint uydu konumu arasında arama gerçekleştirmesi gerekiyorsa, eBulma Yöneticisi için OneDrive veya SharePoint sitelerin bulunduğu alternatif uydu konumunu belirten başka bir kullanıcı hesabı oluşturulması gerekir.

[!INCLUDE [Microsoft 365 Multi-Geo locations](../includes/microsoft-365-multi-geo-locations.md)]

Bir Bölge için Uyumluluk Güvenlik Filtresi'ni ayarlamak için:

1. [Microsoft 365 Güvenlik & Uyumluluk Merkezi PowerShell'e Bağlan](/powershell/exchange/connect-to-scc-powershell)

2. Aşağıdaki sözdizimini kullanın:

   ```powershell
   New-ComplianceSecurityFilter -Action All -FilterName <TheNameYouWantToAssign> -Region <RegionValue> -Users <UserPrincipalName>
   ```

   Örneğin:

   ```powershell
   New-ComplianceSecurityFilter -Action All -FilterName "NAM eDiscovery Managers" -Region NAM -Users adwood@contoso.onmicrosoft.com
   ```

Ek parametreler ve söz dizimi için [New-ComplianceSecurityFilter](/powershell/module/exchange/new-compliancesecurityfilter) makalesine bakın.
