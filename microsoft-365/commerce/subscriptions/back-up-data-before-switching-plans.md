---
title: Planları değiştirmeden önce verileri koruma
f1.keywords:
- NOCSH
author: cmcatee-MSFT
ms.author: cmcatee
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
- commerce_subscriptions
- AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
- BEA160
description: Microsoft 365 planlarını değiştirmeden önce Outlook, OneDrive, Yammer ve SharePoint içeriğini yedekler.
ms.date: 03/17/2021
ms.openlocfilehash: 57f897b353cfe61d5c9cae56c1d367d5e57a29ca
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63317941"
---
# <a name="back-up-data-before-switching-microsoft-365-for-business-plans"></a>Microsoft 365 İş planlarını değiştirmeden önce verileri koruma

Kullanıcı daha az veriyle ilgili hizmeti olan başka bir aboneliğe geçilecekse veya bir kullanıcı kuruluşten ayrılırsa, bu kullanıcının Microsoft 365'te depolanan verilerin bir kopyası yeni aboneliğe geçilmadan önce indirilebilir.

Bir kullanıcıyı aynı veya daha fazla hizmeti olan bir aboneliğe taşınıyorsanız, kullanıcı verilerini korumanız gerek değildir. Bkz [. Kullanıcıları farklı bir aboneliğe taşıma](./move-users-different-subscription.md).
  
## <a name="save-a-copy-of-outlook-information"></a>Outlook bilgilerini bir kopyasını kaydetme

Kullanıcıların Outlook'u varsa, planları değiştir gelmeden önce e-postaları, kişileri ve takvimi [bir Outlook .pst](https://support.microsoft.com/office/14252b52-3075-4e9b-be4e-ff9ef1068f91) dosyasına aktararak veya yedekler.
  
Yeni plana geçiş tamamlandığında, kullanıcılar e-postaları, kişileri ve takvimi [bir Outlook .pst dosyasından içeri aktarabilirsiniz](https://support.microsoft.com/office/431a8e9a-f99f-4d5f-ae48-ded54b3440ac).
  
## <a name="save-files-stored-in-onedrive-for-business"></a>OneDrive İş'te depolanan dosyaları kaydetme

Kullanıcılar, farklı bir aboneliğe geçiş öncesinde [OneDrive veya SharePoint'te](https://support.microsoft.com/office/5c7397b7-19c7-4893-84fe-d02e8fa5df05) bilgisayarlarının sabit sürücüsüne sahip bir klasör veya kuruluşun ağı üzerinde dosya paylaşımı gibi farklı bir konuma dosya ve klasör indirebilir.
  
## <a name="save-yammer-information"></a>Yammer bilgilerini kaydetme

Yöneticiler tüm iletileri, notları, dosyaları, konuları, kullanıcıları ve grupları bir .zip aktarabilirsiniz. Daha fazla bilgi için bkz [. Yammer Kurumsal'dan verileri dışarı aktarma](/yammer/manage-security-and-compliance/export-yammer-enterprise-data). Geliştiriciler yammer [API'sini](https://go.microsoft.com/fwlink/p/?linkid=842495) de bunu yapmak için kullanabilir.
  
## <a name="how-to-save-sharepoint-information"></a>SharePoint bilgilerini kaydetme

Kullanıcı, SharePoint Online'a sahip olmayan bir abonelikten geçiş yaptı ise, **SharePoint** kutucuğu artık Microsoft 365 menüsünde görünmez.
  
Bununla birlikte, yeni abonelik geçiş yapılan abonelikle aynı kuruluş içinde olduğu sürece, kullanıcılar SharePoint ekip sitesine erişmeye devam edebilirsiniz. Ekip sitesinin doğrudan URL'sini kullanarak not defterlerini, belgeleri, görevleri ve takvimleri güncelleştirmeyi güncelleştirmeyi sağlarlar.
  
> [!TIP]
> Kullanıcıların abonelikleri değiştirilmezken önce ekip sitesine gitmelerini ve tarayıcılarında URL'yi sık kullanılan veya yer işareti olarak kaydetmelerini öneririz.
  
Varsayılan olarak, ekip web sitesinin URL'si şu formdadır:
  
```html
https://<orgDomain>/_layouts/15/start.aspx#/SitePages/Home.aspx
```

burada  _\<orgDomain\>_ , kuruluşun URL'si yer alan bir URL'ye tıklayın.
  
Örneğin, kuruluşun etki alanı contoso.onmicrosoft.com, ekip sitesinin doğrudan URL'si olabilir `https://contoso.onmicrosoft.com/_layouts/15/start.aspx#/SitePages/Home.aspx`.
  
Doğal olarak, kullanıcılar SharePoint ekip sitesinden SharePoint Online belgelerini kendi yerel bilgisayarlarına veya başka bir konuma istediğiniz zaman indirebilirler.
