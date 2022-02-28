---
title: Planları değiştirmeden önce verileri koruma
f1.keywords:
- NOCSH
ms.author: cmcatee
author: cmcatee-MSFT
manager: scotv
ms.reviewer: jkinma, jmueller
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolio
- commerce_subscriptions
search.appverid:
- BCS160
- MET150
- MOE150
- BEA160
description: Plan Outlook değiştirmeden OneDrive, Yammer SharePoint, yedekleme, yedekleme Microsoft 365.
ms.date: 03/17/2021
ms.openlocfilehash: c65c0ce533739f5d39314dc575d407d8d1af9ca8
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62985712"
---
# <a name="back-up-data-before-switching-microsoft-365-for-business-plans"></a>İşletmeler için plan değiştirmeden Microsoft 365 verileri koruma

Kullanıcı verilerle ilgili daha az hizmeti olan başka bir aboneliğe geçilecekse veya bir kullanıcı kuruluşten ayrılırsa, kullanıcı yeni aboneliğe Microsoft 365'de depolanan verilerin bir kopyası indirilebilir.

Bir kullanıcıyı aynı veya daha fazla hizmeti olan bir aboneliğe taşınıyorsanız, kullanıcı verilerini korumanız gerek değildir. Bkz [. Kullanıcıları farklı bir aboneliğe taşıma](./move-users-different-subscription.md).
  
## <a name="save-a-copy-of-outlook-information"></a>Çalışma bilgileri kopyasını Outlook kaydetme

Kullanıcıların e-Outlook varsa, planları değiştir gelmeden önce e-postaları, kişileri ve [takvimi Outlook .pst](https://support.microsoft.com/office/14252b52-3075-4e9b-be4e-ff9ef1068f91) dosyasına aktararak veya yedekler.
  
Yeni plana geçiş tamamlandığında, kullanıcılar E-postaları, kişileri ve takvimi [bir .pst dosyasından Outlook aktarabilirsiniz](https://support.microsoft.com/office/431a8e9a-f99f-4d5f-ae48-ded54b3440ac).
  
## <a name="save-files-stored-in-onedrive-for-business"></a>Farklı bir dosyada depolanan OneDrive İş

Kullanıcılar, farklı bir aboneliğe geçiş öncesinde dosya ve klasörleri [OneDrive veya SharePoint'tan](https://support.microsoft.com/office/5c7397b7-19c7-4893-84fe-d02e8fa5df05) bilgisayarlarının sabit sürücüsüne bir klasör veya kuruluşun ağına dosya paylaşımı gibi farklı bir konuma indirebilir.
  
## <a name="save-yammer-information"></a>Tüm Yammer kaydetme

Yöneticiler tüm iletileri, notları, dosyaları, konuları, kullanıcıları ve grupları bir .zip aktarabilirsiniz. Daha fazla bilgi için bkz[. Veri kaynağından Yammer Enterprise](/yammer/manage-security-and-compliance/export-yammer-enterprise-data). Geliştiriciler bu [Yammer API'sini](https://go.microsoft.com/fwlink/p/?linkid=842495) de kullanabilir.
  
## <a name="how-to-save-sharepoint-information"></a>Daha fazla bilgi SharePoint kaydetme

Kullanıcı SharePoint Online'a sahip olmayan bir aboneliğe geçse, **SharePoint** kutucuğu artık Microsoft 365 görünmez.
  
Bununla birlikte, yeni abonelik geçiş yapılan abonelikle aynı kuruluş içinde olduğu sürece, kullanıcılar ekip sitesine SharePoint sahip olabilir. Ekip sitesinin doğrudan URL'sini kullanarak not defterlerini, belgeleri, görevleri ve takvimleri güncelleştirmeyi güncelleştirmeyi sağlarlar.
  
> [!TIP]
> Kullanıcıların abonelikleri değiştirilmezken önce ekip sitesine gitmelerini ve tarayıcılarında URL'yi sık kullanılan veya yer işareti olarak kaydetmelerini öneririz.
  
Varsayılan olarak, ekip web sitesinin URL'si şu formdadır:
  
```html
https://<orgDomain>/_layouts/15/start.aspx#/SitePages/Home.aspx
```

burada  _\<orgDomain\>_ , kuruluşun URL'si yer alan bir URL'ye tıklayın.
  
Örneğin, kuruluşun etki alanı contoso.onmicrosoft.com, ekip sitesinin doğrudan URL'si olabilir `https://contoso.onmicrosoft.com/_layouts/15/start.aspx#/SitePages/Home.aspx`.
  
Doğal olarak, kullanıcılar SharePoint Online belgelerini ekip sitesinden kendi SharePoint bilgisayarlarına veya başka bir konuma istediğiniz zaman indirebilirler.
