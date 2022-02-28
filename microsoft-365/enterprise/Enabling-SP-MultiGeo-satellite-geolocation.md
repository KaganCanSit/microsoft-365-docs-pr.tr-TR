---
title: Uydu SharePoint Multi-Geo coğrafi konumdaki konumları etkinleştirme
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
description: Bu makalede, Genel veya SharePoint uydu coğrafi konumlarında SharePoint Multi-Geo hakkında bilgi sağlar.
ms.openlocfilehash: e48e6feedfab47f6faa17cadcff1d858bced4379
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62985557"
---
# <a name="enabling-sharepoint-multi-geo-in-your-satellite-geo-location"></a>Uydu SharePoint Multi-Geo coğrafi konumdaki konumları etkinleştirme

Bu makale **, SharePoint Multi-Geo** 27 Mart 2019'da genel kullanıma hazır hale gelmeden ve uydu coğrafi konumlarında SharePoint Multi-Geo'i etkinleştirmemiş olan Genel ya da SharePoint Multi-Geo yöneticilerine yöneliktir. SharePoint 

>[!Note]
>**27** Mart'tan sonra yeni bir coğrafi konum eklediysanız, bu yönergeleri gerçekleştirmeniz gerekli değildir çünkü yeni coğrafi konumunuz coğrafi konum bilgi işlemlerinde OneDrive SharePoint Multi-Geo.

Bu yönergeler, çok coğrafi SharePoint uydu kullanıcılarının O365'te hem uydu hem de OneDrive SharePoint Multi-Geo olanaklarını kullanmalarını sağlayacaktır. 

>[!IMPORTANT]
>Bu özelliğin tek bir yolu olduğunu lütfen unutmayın. SPO modunu ayarlamanın ardından, desteği olan bir yükseltme olmadan OneDrive Multi-Geo modunu geri döndürmeniz mümkün olmayacaktır. 

## <a name="to-set-a-geo-location-into-spo-mode"></a>SPO Moduna coğrafi bir konum ayarlamak için

SPO moduna coğrafi bir konum ayarlamak için, SPO Modunda ayarlamak istediğiniz coğrafi konuma bağlanin:

1.    SharePoint Online Yönetim Kabuğu'nu açma 
2.    Connect-SPOService -URL "https://$tenantGeo-admin.sharepoint.com" -Credential $credential
3.    Set-SPOMultiGeoExperience</br></br>
![Set-SPOMultiGeoExperience.](../media/Set-SPO-MultiGeo.jpg)
4.    Bu işlem genellikle, hizmette çeşitli yayımlama işlemleri yaparken ve kiracınızı yeniden damgalarken yaklaşık bir saat sürer. En az 1 saat sonra lütfen Get-SPOMultiGeoExperience işlemi gerçekleştirin.  Bu size, bu coğrafi konumun SPO modunda olup olmadığını gösterir.</br></br>
![Set-SPOMultiGeoExperience.](../media/Get-SPO-MultiGeo.jpg)

 
 
 
>[!Note]
>Hizmette bazı önbellekler 24 saatte bir güncelleştirilmektedir, bu nedenle 24 saate kadar bir süre boyunca uydu coğrafi olarak ODB modundaymış gibi aralıklı olarak davranabilirsiniz. Bu, herhangi bir teknik soruna neden olmaz. 
 
E-SharePoint Multi-Geo daha fazla bilgi için lütfen şu konuya [aka.ms/sharepointmultigeo](multi-geo-capabilities-in-onedrive-and-sharepoint-online-in-microsoft-365.md)


