---
title: OneDrive SharePoint Online'daki Multi-Geo Özellikleri
ms.reviewer: adwood
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
f1.keywords:
- NOCSH
ms.custom: admindeeplinkSPO
ms.collection:
- Strat_SP_gtc
- SPO_Content
- m365solution-scenario
- m365solution-spintranet
ms.localizationpriority: medium
ms.assetid: 094e86f2-9ff0-40ac-af31-28fcaba00c1d
description: OneDrive Online Microsoft 365 da birden çok coğrafi özelliği olan birden çok coğrafi bölgeye genişletebilirsiniz.
ms.openlocfilehash: 778efca6035dad05ec9bc77298b888e50f381ca1
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63330041"
---
# <a name="multi-geo-capabilities-in-onedrive-and-sharepoint-online"></a>OneDrive ve SharePoint Online’da Multi-Geo Özellikleri

OneDrive ve SharePoint Online'daki Multi-Geo özellikleri, ekip siteleri ve SharePoint konumlarında saklanan Microsoft 365 Grup posta kutuları gibi paylaşılan kaynakların denetimine olanak sağlar.

Her kullanıcı, Grup posta kutusu SharePoint sitenin, ilgili verilerin depolandığı coğrafi konumun notlandığı Tercih Edilen Veri Konumu'nda (PDL) yer almaktadır. Kullanıcıların kişisel verileri (Exchange posta kutusu ve OneDrive) ile birlikte, Microsoft 365 Grupları veya SharePoint siteleri de veri yerleşim gereksinimlerini karşılamak için belirtilen coğrafi konumda depolanıyor olabilir. Her coğrafi [konum için farklı yöneticiler belirtebilirsiniz](add-a-sharepoint-geo-admin.md).

Kullanıcılar, uygulama, uygulama ve Microsoft 365 Arama dahil Office hizmet OneDrive sorunsuz bir deneyim elde ediyor. Ayrıntılar [için bkz. Çok coğrafi ortamda kullanıcı](multi-geo-user-experience.md) deneyimi.

## <a name="onedrive"></a>OneDrive

Her kullanıcının OneDrive PDL'sine uygun olarak bir uydu konuma bir yönetici [](move-onedrive-between-geo-locations.md) tarafından sağ olabilir veya bu konuma taşınabilirsiniz. Kişisel dosyalar daha sonra bu coğrafi konumda tutulur, ancak bunlar başka coğrafi konumlarda yer alan kullanıcılarla paylaşılır.

## <a name="sharepoint-sites-and-groups"></a>SharePoint Siteleri ve Grupları

Multi-Geo özelliğinin yönetimi yönetim <a href="https://go.microsoft.com/fwlink/?linkid=2185219" target="_blank">merkezinden SharePoint kullanılabilir</a>. Ayrıntılı bilgileri ilgili blog [gönderisinde bulabilirsiniz](https://techcommunity.microsoft.com/t5/Office-365-Blog/Now-available-Multi-Geo-in-SharePoint-and-Office-365-Groups/ba-p/263302).

Kullanıcı çok coğrafi SharePoint grup bağlantılı bir site oluşturduğunda, PDL'leri sitenin ve ilişkili Grup posta kutusunun oluşturularak coğrafi konumu belirlemek için kullanılır. (Kullanıcının PDL değeri ayarilmamışsa veya uydu konumu olarak yapılandırılmamış coğrafi konum olarak ayarlanmışsa, site ve posta kutusu merkezi konumda oluşturulur.)

Microsoft 365, Exchange, OneDrive, SharePoint Teams dışında hiçbir hizmet Multi-Geo değildir. Ancak Microsoft 365 tarafından oluşturulan Gruplarda, oluşturanın PDL'si ve bunların Exchange Grubu posta kutusu ile yalıtılan SharePoint ilgili coğrafi grupta sağlandı. 

## <a name="managing-the-multi-geo-environment"></a>Çok coğrafi ortamı yönetme

Çok coğrafi ortamınızı ayarlama ve yönetme, yönetim merkezinden <a href="https://go.microsoft.com/fwlink/?linkid=2185219" target="_blank">SharePoint yapılır</a>. 

![Yönetim merkezinde coğrafi konumlar sayfasının SharePoint görüntüsü.](../media/sharepoint-multi-geo-admin-center.png)

(Site taşıma ya da SharePoint sitesi gibi bazı OneDrive, Microsoft PowerShell gerektirir.)

## <a name="see-also"></a>Ayrıca bkz.

[Multi-Geo in SharePoint and Microsoft 365 Groups](https://techcommunity.microsoft.com/t5/Office-365-Blog/Now-available-Multi-Geo-in-SharePoint-and-Office-365-Groups/ba-p/263302)

[Çok coğrafi ortamı yönetme](administering-a-multi-geo-environment.md)

[SharePoint coğrafi ortamlarda depolama kotalarını atama](sharepoint-multi-geo-storage-quota.md)

[Çok Exchange Online ortamda posta kutularını yönetme](administering-exchange-online-multi-geo.md)
