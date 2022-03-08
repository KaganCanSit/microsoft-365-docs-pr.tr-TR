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
ms.openlocfilehash: b542c1ee77c7b4ca7a6179bac5ce5eaa1090606a
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63330447"
---
# <a name="enabling-sharepoint-multi-geo-in-your-satellite-geo-location"></a>Uydu SharePoint Multi-Geo coğrafi konumdaki konumları etkinleştirme

Bu makale **, SharePoint Multi-Geo** 27 Mart 2019'da genel kullanıma hazır hale gelmeden ve uydu coğrafi konumlarında SharePoint Multi-Geo'i etkinleştirmemiş olan Genel ya da SharePoint Multi-Geo yöneticilerine yöneliktir. SharePoint 

>[!Note]
>**27 Mart 2019'dan** sonra yeni bir coğrafi konum eklediysanız, yeni coğrafi konumunuz coğrafi konum bilgi ve görev için zaten etkinleştirildiğinden bu yönergeleri OneDrive SharePoint Multi-Geo.

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


