---
title: Belirli bir Microsoft 365 veri konumuyla Veri Grubu oluşturma
ms.reviewer: adwood
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
f1.keywords:
- NOCSH
ms.collection: Strat_SP_gtc
ms.localizationpriority: medium
description: Çok coğrafi bir ortamda Microsoft 365 tercih edilen veri konumuyla kaynak grubu oluşturma hakkında bilgi öğrenin.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 6ce4ed337b07206e6508a5955edc2c264586df4b
ms.sourcegitcommit: 0ee2dabe402d44fecb6856af98a2ef7720d25189
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/09/2021
ms.locfileid: "62996130"
---
# <a name="create-a-microsoft-365-group-with-a-specific-preferred-data-location"></a>Belirli bir Microsoft 365 veri konumuyla Veri Grubu oluşturma

Çok coğrafi bir ortamdaki kullanıcılar Microsoft 365 Grubu oluşturduklarında, grup tercih edilen veri konumu (PDL) otomatik olarak kullanıcınınkiyle ayarlanır. Genel, SharePoint grupları Exchange Yöneticiler kendi oluşturdukları herhangi bir bölgede grup oluşturabilir. 

Belirli bir PDL'ye sahip bir grup oluşturmanız gerekirse, bunu SharePoint yönetim merkezinden veya Microsoft PowerShell cmdlet'i aracılığıyla Exchange Online New-UnifiedGroup aracılığıyla da yapabiliriz. Bunu yapmak için, hem grup posta kutusu SharePoint grupla ilişkilendirilmiş olan posta kutusu, belirtilen PDL içinde sağlandı.

Belirttiğiniz PDL Microsoft 365 BIR Grup Oluşturmak için, grup sitesini oluşturmak istediğiniz coğrafi konumda SharePoint yönetim merkezine gidin.

Örneğin:

Avustralya konumunuz içinde bir grup sitesi oluşturmak için https://ContosoAUS-admin.sharepoint.com/_layouts/15/online/AdminHome.aspx#/siteManagement

1. **+ Oluştur'a seçin**.
2. Grup sitesi oluşturmak için işlemi izleyin.

Grup siteniz, site oluşturma isteğini başlattığınız SharePoint ilgili yönetim merkezine karşılık gelen coğrafi konumda sağlanarak. 

Exchange PowerShell'i kullanma 

Bağlan PowerShell Exchange Online e tıklayın ve coğrafi konum koduyla *-MailBoxRegion* parametresini geçecek şekilde seçin.

Örneğin: 

```PowerShell
New-UnifiedGroup -DisplayName MultiGeoEUR -Alias "MultiGeoEUR" -AccessType Public -MailboxRegion EUR 
```

![Söz dizimi New-UnifiedGroup PowerShell cmdlet'inin ekran görüntüsü.](../media/multi-geo-new-group-with-pdl-powershell.png)

Grup SharePoint sağlamanın isteğe bağlı olduğunu unutmayın. Site, ilk kez bir grup sahibi veya üye bu siteye erişmeye ilk kez girişimde bulunacaktır.

## <a name="geo-location-codes"></a>Coğrafi konum kodları

[!INCLUDE [Microsoft 365 Multi-Geo locations](../includes/microsoft-365-multi-geo-locations.md)]

## <a name="related-topics"></a>İlgili konular

[Bağlan'Exchange Online PowerShell'e](/powershell/exchange/connect-to-exchange-online-powershell)

[GRAPH API'sini kullanarak belirli bir tercih edilen veri Graph oluşturma](/graph/api/group-post-groups)
