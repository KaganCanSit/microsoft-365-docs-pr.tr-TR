---
title: Site SharePoint coğrafi konumla kısıtlama
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
ms.collection: Strat_SP_gtc
ms.localizationpriority: medium
description: Bu makalede, sitelerin çok SharePoint bir ortamda belirli bir coğrafi konumla nasıl kısıtla ilgili olduğunu öğrenin.
ms.openlocfilehash: 06401658afe9f6a26b1280f5931ba6b3ba761742
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62983368"
---
# <a name="restrict-sharepoint-site-content-to-a-geo-location"></a>Site SharePoint coğrafi konumla kısıtlama

Bazı durumlarda, sitenin ve dosya içeriğinin, sitenin taşınmasını engelerek veya sitenin dosya içeriğinin başka bir coğrafi konumda önbelleğe alınmasını engelerek, sitenin oluşturulmuş olduğu coğrafi konumda kalmasını zorunlu  edebilirsiniz.

Bunu yapmak için [Set-SPOSite](/powershell/module/sharepoint-online/set-sposite) cmdlet'ini **RestrictedToGeo parametresiyle birlikte kullanın** . Bu parametrenin varsayılan bir NULL değeri vardır, ancak bunu aşağıdaki değerlerden biri ile değiştirebilirsiniz:

|Kısıtlama|Açıklama|
|:----------|:----------|
|NoRestriction|Site başka bir coğrafi konuma taşınabilirsiniz.|
|BlockMoveOnly|Site başka bir coğrafi konuma taşınamaz, ancak site içeriği başka coğrafi konumlarda önbelleğe alınamaz.|
|BlockFull|Site başka bir coğrafi konuma taşınamaz ve diğer coğrafi konumlarda tam dosya içeriği önbelleğe alınmaz. Dosyaların başlığı (içerikten toplanarak), dosya adı ve diğer özellikler yine de başka coğrafi konumlarda önbelleğe alınıyor.<br>BlockFull olarak yapılandırılmadan önce sitede depolanan içerik, diğer coğrafi konumlarda önbelleğe alınmaya devam edebilirsiniz.|

Aşağıdaki sözdizimini kullanın:

`Set-SPOSite -Identity <siteURL> -RestrictedToGeo <restriction>`

Örneğin:

`Set-SPOSite -Identity https://contoso.sharepoint.com/sites/RegionRestrictedTeamSite -RestrictedToGeo BlockFull`