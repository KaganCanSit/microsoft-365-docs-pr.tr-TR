---
title: E-posta uygulaması erişimini Microsoft 365 yönetim merkezi
f1.keywords:
- CSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Adm_O365
- Adm_NonTOC
ms.custom:
- AdminSurgePortfolio
- admindeeplinkEXCHANGE
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
ms.assetid: d00b6b83-1f14-4e9c-a2c5-dbd9a92816f4
ROBOTS: NOINDEX, NOFOLLOW
description: Kişilerin e-postaya, takvime ve kişilere erişmek için hangi mobil uygulamaları kullanabileceğini seçmeyi öğrenin.
ms.openlocfilehash: e3a7999900e85bde1bee7bf220b46a74a1151f57
ms.sourcegitcommit: b1066b2a798568afdea9c09401d52fa38fe93546
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/13/2021
ms.locfileid: "63018775"
---
# <a name="manage-email-app-access-in-the-microsoft-365-admin-center"></a>E-posta uygulaması erişimini mobil Microsoft 365 yönetim merkezi

E-postaya, takvime ve kişilere erişmek üzere kuruluşta çalışan kişilerin iş veya okul hesaplarına erişmek için hangi mobil uygulamaları kullanabileceğini seçmek için mobil e-posta erişimi ayarlarını kullanın.
  
> [!IMPORTANT]
> Microsoft Intune kullanıyorsanız veya yönetim merkezinde mobil cihaz yönetimi ayarlarını yapılandırmadınız sürece, kuruluş bu <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange erişebilirsiniz</a>. 
  
## <a name="manage-email-app-options"></a>E-posta uygulaması seçeneklerini yönetme

> [!IMPORTANT]
>  Bu özelliği kullansanız bile, kullanıcı deneyiminde hiçbir değişiklik olmaz. E-posta, takvim ve kişiler için iş veya okul hesaplarına mobil cihazlarından erişmek üzere herhangi bir mobil e-posta uygulamasını kullanabilirler. 
    
1. Yönetim merkezinde, **Ayarlar** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2053743" target="_blank">Hizmetler &amp; eklentiler</a> sayfasına gidin. 

2. Mobil **e-posta erişim seçenekleri** sayfasında, onay kutusunu seçin ve sonra da organizasyon cihazlarınız üzerinden kullanıcıların e-posta uygulamalarını nasıl kullanabileceğini seçin:
  
Organizasyonlu kullanıcıların mobil cihazlarından iş veya okul hesaplarına nasıl erişeceklerini ayarlama seçeneğini belirleyin
  
- **Outlook-** Android için Outlook veya iOS için Outlook uygulamasını mobil cihazlarında kullanmaları gerekir. 
    
- **Herhangi bir e-posta** uygulaması- tüm kullanıcılardan E-posta Outlook, ancak herhangi bir e-posta uygulamasını kullanmayı seçebilirler. 
    
- **Herhangi bir e-posta** uygulaması - yeni kullanıcılardan veya kuruluşlardan bir kez Outlook, ancak herhangi bir e-posta uygulamasını kullanmayı seçebilirler. 
    
Daha fazla ayrıntı için Mobil aygıtınızdan [e-postaya erişim seçenekleri'ne göz atabilirsiniz](access-email-from-a-mobile-device.md).
  
## <a name="new-user-or-device-is-activated-in-your-organization"></a>Yeni kullanıcı veya cihaz, kurum içinde etkinleştirildi

Bir kullanıcı, iş veya okul e-postalarını üçüncü taraf bir e-posta uygulamasına veya yeni bir cihaza ekler ekleyene kadar, Microsoft'tan sizin cihazınız adına bir **e-posta alır**. Bu e-posta, mobil Outlook kullanmanın avantajlarını onlara haber sağlar ve indirme konumu için bir bağlantı sağlar. Bundan sonra kullanıcılarınız üçüncü taraf uygulamasını kullanmaya devam edip edeceğini veya üçüncü taraf uygulamasını Outlook seçebilirler. Kullanıcı bu e-postayı ilk kez aldığından 24 saat boyunca cihazı karantinaya alınır ve e-posta, takvim ve kişi verileri güncelleştirilmez. Bu kullanıcı mobil uygulamayı Outlook, üçüncü taraf uygulama karantinada kalır ve veriler yalnızca Outlook eşitler. Üçüncü taraf uygulamasını kullanmaya devam olduğuna karar verirse, veriler hemen eşit kullanmaya başlar. İlk 24 saat içinde hiçbir işlem yapılırsa, e-posta onların gelen kutusundan kaldırılır ve veriler sunucudan otomatik olarak eşitlenir.
  
## <a name="previously-configured-users-in-your-organization"></a>Organizasyonda daha önceden yapılandırılmış kullanıcılar

Yukarıda yeni kullanıcılar için açıklanan deneyime ek olarak Outlook'i kuruluş içindeki herkese öneririz. Daha önce iş veya okul e-posta hesaplarını bir üçüncü taraf uygulamasına bağladılar, bu ayar etkinleştirildikten sonra 48 saat içinde **kuruluş adına Microsoft'tan** bir e-posta alırlar. Bu e-posta, mobil Outlook kullanmanın avantajlarını onlara haber sağlar ve indirme konumu için bir bağlantı sağlar. Bundan sonra kullanıcılarınız üçüncü taraf uygulamasını kullanmaya devam edip edeceğini veya üçüncü taraf uygulamasını Outlook seçebilirler. Kullanıcı bu e-postayı ilk kez aldığından 24 saat boyunca cihazı karantinaya alınır ve e-posta, takvim ve kişi verileri güncelleştirilmez. Bu kullanıcı mobil uygulamayı Outlook, üçüncü taraf uygulama karantinada kalır ve veriler yalnızca Outlook eşitler. Üçüncü taraf uygulamasını kullanmaya devam olduğuna karar verirse, veriler hemen eşit kullanmaya başlar. İlk 24 saat içinde hiçbir işlem yapılırsa, e-posta onların gelen kutusundan kaldırılır ve veriler sunucudan otomatik olarak eşitlenir. 
  

