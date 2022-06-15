---
title: Planları değiştirmeden önce verileri yedekleme
f1.keywords:
- NOCSH
author: cmcatee-MSFT
ms.author: cmcatee
manager: scotv
ms.reviewer: mijeffer, jmueller
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- commerce_subscriptions
- AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
- BEA160
description: Microsoft 365 planlarını değiştirmeden önce içeriği yedekleme Outlook, OneDrive, Yammer ve SharePoint.
ms.date: 03/17/2021
ms.openlocfilehash: fd5239deb88fbf9b87df7e62d85a3d2cc18e1df7
ms.sourcegitcommit: 3b194dd6f9ce531ae1b33d617ab45990d48bd3d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/15/2022
ms.locfileid: "66102514"
---
# <a name="back-up-data-before-switching-microsoft-365-for-business-plans"></a>İş planları için Microsoft 365 değiştirmeden önce verileri yedekleme

Bir kullanıcı veriyle ilgili daha az hizmet içeren başka bir aboneliğe geçirilirse veya bir kullanıcı kuruluşta ayrılırsa, yeni aboneliğe geçmeden önce Microsoft 365 depolanan verilerinin bir kopyası indirilebilir.

Kullanıcıyı aynı veya daha fazla hizmete sahip bir aboneliğe taşıyorsanız, kullanıcı verilerini yedeklemeniz gerekmez. Bkz. [Kullanıcıları farklı bir aboneliğe taşıma](./move-users-different-subscription.md).
  
## <a name="save-a-copy-of-outlook-information"></a>Outlook bilgilerinin kopyasını kaydetme

Kullanıcıların Outlook varsa, planları değiştirilmeden önce [e-postayı, kişileri ve takvimi bir Outlook .pst dosyasına aktarabilir veya yedekleyebilirler](https://support.microsoft.com/office/14252b52-3075-4e9b-be4e-ff9ef1068f91).
  
Yeni plana geçiş tamamlandıktan sonra, kullanıcılar [bir Outlook .pst dosyasından e-postayı, kişileri ve takvimi içeri aktarabilir](https://support.microsoft.com/office/431a8e9a-f99f-4d5f-ae48-ded54b3440ac).
  
## <a name="save-files-stored-in-onedrive-for-business"></a>OneDrive İş'de depolanan dosyaları kaydetme

Kullanıcılar, farklı bir aboneliğe geçmeden önce [dosyaları ve klasörleri OneDrive veya SharePoint](https://support.microsoft.com/office/5c7397b7-19c7-4893-84fe-d02e8fa5df05) bilgisayarlarının sabit sürücüsündeki bir klasör veya kuruluşun ağındaki dosya paylaşımı gibi farklı bir konuma indirebilir.
  
## <a name="save-yammer-information"></a>Yammer bilgilerini kaydetme

Yöneticiler tüm iletileri, notları, dosyaları, konuları, kullanıcıları ve grupları bir .zip dosyasına aktarabilir. Daha fazla bilgi için bkz. [verileri Yammer Enterprise dışarı aktarma](/yammer/manage-security-and-compliance/export-yammer-enterprise-data). Geliştiriciler bunu yapmak için [Yammer API'sini](https://go.microsoft.com/fwlink/p/?linkid=842495) de kullanabilir.
  
## <a name="how-to-save-sharepoint-information"></a>SharePoint bilgileri kaydetme

Bir kullanıcı SharePoint Online'a sahip olmayan bir aboneliğe geçirilirse **, SharePoint** kutucuğu artık Microsoft 365 menüsünde görünmez.
  
Ancak, yeni abonelik geçiş yaptıkları kuruluşla aynı kuruluş içinde olduğu sürece, kullanıcılar SharePoint ekip sitesine erişmeye devam edebilir. Ekip sitesinin doğrudan URL'sini kullanarak not defterlerini, belgeleri, görevleri ve takvimleri görüntüleyebilir ve güncelleştirebilirler.
  
> [!TIP]
> Kullanıcıların abonelikleri değiştirilmeden önce ekip sitesine gitmelerini ve URL'yi tarayıcılarında sık kullanılan veya yer işareti olarak kaydetmelerini öneririz.
  
Varsayılan olarak, ekip web sitesinin URL'si şu biçimdedir:
  
```html
https://<orgDomain>/_layouts/15/start.aspx#/SitePages/Home.aspx
```

burada  _\<orgDomain\>_ kuruluşun URL'sidir.
  
Örneğin, kuruluşun etki alanı contoso.onmicrosoft.com ise, ekip sitesinin doğrudan URL'si olur `https://contoso.onmicrosoft.com/_layouts/15/start.aspx#/SitePages/Home.aspx`.
  
Elbette, kullanıcılar SharePoint Çevrimiçi belgelerini SharePoint ekip sitesinden yerel bilgisayarlarına veya istedikleri zaman başka bir konuma da indirebilirler.
