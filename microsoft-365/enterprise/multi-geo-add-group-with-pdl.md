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
ms.custom:
- seo-marvel-apr2020
- admindeeplinkSPO
ms.openlocfilehash: 7de00ad0d94cda0a47f4981d78ebc07cedab6ada
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63318809"
---
# <a name="create-a-microsoft-365-group-with-a-specific-preferred-data-location"></a>Belirli bir Microsoft 365 veri konumuyla Veri Grubu oluşturma

Çok coğrafi bir ortamdaki kullanıcılar Microsoft 365 Grubu oluşturduklarında, grup tercih edilen veri konumu (PDL) otomatik olarak kullanıcınınkiyle ayarlanır. Genel, SharePoint grupları Exchange Yöneticiler kendi oluşturdukları herhangi bir bölgede grup oluşturabilir. 

Belirli bir PDL'ye sahip bir grup oluşturmanız gerekirse, bunu <a href="https://go.microsoft.com/fwlink/?linkid=2185219" target="_blank">yapmak için SharePoint</a> yönetim merkezinden veya Microsoft PowerShell cmdlet'inden Exchange Online New-UnifiedGroup kullanabilirsiniz. Bunu yapmak için, hem grup posta kutusu SharePoint grupla ilişkilendirilmiş olan posta kutusu, belirtilen PDL içinde sağlandı.

Belirttiğiniz PDL Microsoft 365 BIR Grup Oluşturmak için, <a href="https://go.microsoft.com/fwlink/?linkid=2185219" target="_blank">grup sitesini oluşturmak istediğiniz coğrafi konumda SharePoint</a> yönetim merkezine gidin.

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
