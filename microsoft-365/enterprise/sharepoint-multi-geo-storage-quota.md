---
title: SharePoint coğrafi ortamlarda depolama kotalarını atama
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
ms.collection:
- Strat_SP_gtc
- SPO_Content
ms.localizationpriority: medium
description: Çok SharePoint ortamlarda depolama kotalarını nasıl etkileyebilirsiniz ve kotaların SharePoint Online yöneticisi tarafından nasıl yönetilebilirsiniz.
ms.openlocfilehash: d1e47c206f1353093ba8bebf9db03ab7142d6da9
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62984487"
---
# <a name="sharepoint-storage-quotas-in-multi-geo-environments"></a>SharePoint coğrafi ortamlarda depolama kotalarını atama

Varsayılan olarak, çok coğrafi ortamın tüm coğrafi konumları kullanılabilir kiracı depolama kotasını paylaşır.

Coğrafi SharePoint kotası ayarlamayla, her coğrafi konumun depolama kotasını yönetebilirsiniz. Coğrafi konum için depolama kotası tahsis etmek, bu coğrafi konum için kullanılabilen en yüksek depolama miktarı olur ve kullanılabilir kiracı depolama kotalarından düşüler. Kullanılabilir kalan kiracı depolama kotası daha sonra belirli bir depolama kotasının tahsis edilmiş olduğu yapılandırılmış coğrafi konumlarda paylaşılır.

Coğrafi SharePoint depolama alanı kotası, merkezi konuma bağlanarak SharePoint Online yöneticisi tarafından tahsis edilir. Uydu konumları için coğrafi yöneticiler depolama kotasını sınar ancak ayıramaz.

## <a name="configure-a-storage-quota-for-a-geo-location"></a>Coğrafi konum için depolama kotasını yapılandırma

Depolama Microsoft Office SharePoint Online [kullanın](https://www.microsoft.com/download/details.aspx?id=35588) ve coğrafi konum için depolama kotasını tahsis etmek üzere merkezi konuma bağlanin.

Bir konuma Depolama Kotası tahsis etmek için cmdlet'i çalıştırın:

```powershell
Set-SPOGeoStorageQuota -GeoLocation <geolocationcode> -StorageQuotaMB <value>
```

Geçerli Depolama Konum Kotası'nın görünümünü görüntülemek için, şu çalıştırın:

```powershell
Get-SPOGeoStorageQuota
```

![PowerShell penceresinin cmdlet'i Get-SPOGeoStorageQuota ekran görüntüsü.](../media/multi-geo-storage-quota.png)

Tüm coğrafi Depolama Kotasını görüntülemek için, şu çalıştırın:

```powershell
Get-SPOGeoStorageQuota -AllLocations
```

Coğrafi konuma ayrılan depolama kotasını kaldırmak için şunları ayarlayın `StorageQuota value = 0`:

```powershell
Set-SPOGeoStorageQuota -GeoLocation <geolocationcode> -StorageQuotaMB 0
```
