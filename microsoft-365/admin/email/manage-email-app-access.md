---
title: Microsoft 365 yönetim merkezi'de e-posta uygulaması erişimini yönetme
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
ms.openlocfilehash: 5f5a96a0ac44757cfe168db87deb494019759c36
ms.sourcegitcommit: ac0ae5c2888e2b323e36bad041a4abef196c9c96
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/12/2022
ms.locfileid: "64780247"
---
# <a name="manage-email-app-access-in-the-microsoft-365-admin-center"></a>Microsoft 365 yönetim merkezi e-posta uygulaması erişimini yönetme

Kuruluşunuzdaki kişilerin e-posta, takvim ve kişilere erişmek için iş veya okul hesaplarına erişmek için hangi mobil uygulamaları kullanabileceğini seçmek için mobil e-posta erişim ayarlarını kullanın.
  
> [!IMPORTANT]
> Microsoft Intune kullanmıyorsanız veya Exchange <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">yönetim merkezinde</a> mobil cihaz yönetimi ayarlarını yapılandırmadıysanız kuruluşunuz bu ayara erişebilir.
  
## <a name="manage-email-app-options"></a>E-posta uygulaması seçeneklerini yönetme

> [!IMPORTANT]
> Bu özelliği kullanmazsanız, kullanıcılarınızın deneyiminde hiçbir değişiklik olmaz. Mobil cihazlarından e-posta, takvim ve kişiler için iş veya okul hesaplarına erişmek için herhangi bir mobil e-posta uygulamasını kullanabilirler.

1. Yönetim merkezinde, **Ayarlar** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2053743" target="_blank">Hizmetler &amp; eklentiler</a> sayfasına gidin.

2. **Mobil e-posta erişim seçenekleri** sayfasında onay kutusunu seçin ve ardından kuruluşunuzdaki kullanıcıların cihazlarında e-posta uygulamalarını nasıl kullandığını seçin:
  
Kuruluşunuzdaki kullanıcıların iş veya okul hesaplarına mobil cihazlarından nasıl erişeceğini ayarlama seçeneğini belirleyin
  
- **Yalnızca Outlook** - Kuruluşunuzdaki kullanıcıların mobil cihazlarında Android için Outlook veya iOS uygulaması için Outlook kullanmaları gerekir.

- **Herhangi bir e-posta uygulaması**- Kuruluşunuzdaki tüm kullanıcılardan Outlook kullanmaları istenir, ancak herhangi bir e-posta uygulamasını kullanmayı seçebilirler.

- **Herhangi bir e-posta uygulaması** - Kuruluşunuzdaki yeni kullanıcılardan veya cihazlardan bir kez Outlook kullanmaları istenir, ancak herhangi bir e-posta uygulamasını kullanmayı seçebilirler.

Daha fazla ayrıntı [için mobil cihazınızdan e-postaya erişme seçenekleri'ne](access-email-from-a-mobile-device.md) göz atın.
  
## <a name="new-user-or-device-is-activated-in-your-organization"></a>Kuruluşunuzda yeni kullanıcı veya cihaz etkinleştirildi

Kuruluşunuzdaki bir kullanıcı iş veya okul e-postasını üçüncü taraf e-posta uygulamasına veya yeni bir cihaza ekler eklemez, **kuruluşunuz adına Microsoft'tan** bir e-posta alır. E-posta, Outlook mobil uygulamasını kullanmanın avantajları hakkında bilgi verir ve indirme konumunun bağlantısını sağlar. Kullanıcılarınız daha sonra üçüncü taraf uygulamasını kullanmaya devam etmeyi veya Outlook mobil uygulamasını kullanmayı seçebilir. Kullanıcı bu e-postayı ilk aldıktan sonraki 24 saat boyunca cihazı karantinaya alınır ve e-posta, takvim ve kişi verileri güncelleştirilmez. Outlook mobil uygulamasını kullanmayı seçerlerse üçüncü taraf uygulama karantinada kalır ve veriler yalnızca Outlook mobil uygulamasıyla eşitlenir. Üçüncü taraf uygulamasını kullanmaya devam etmeye karar verirse veriler anında eşitlenmeye başlar. İlk 24 saat içinde hiçbir işlem yapılmazsa, e-posta gelen kutusundan kaldırılır ve veriler sunucudan otomatik olarak eşitlenmeye başlar.
  
## <a name="previously-configured-users-in-your-organization"></a>Kuruluşunuzda önceden yapılandırılmış kullanıcılar

Kuruluşunuzdaki herkese Outlook önermeye karar verirseniz, yeni kullanıcılar için yukarıda açıklanan deneyime ek olarak, daha önce iş veya okul e-posta hesabını üçüncü taraf bir uygulamaya bağlamış olan kullanıcılar, bu ayarın etkinleştirilmesinden sonraki 48 saat içinde **kuruluşunuz adına Microsoft'tan** bir e-posta alır. E-posta, Outlook mobil uygulamasını kullanmanın avantajları hakkında bilgi verir ve indirme konumunun bağlantısını sağlar. Kullanıcılarınız daha sonra üçüncü taraf uygulamasını kullanmaya devam etmeyi veya Outlook mobil uygulamasını kullanmayı seçebilir. Kullanıcı bu e-postayı ilk aldıktan sonraki 24 saat boyunca cihazı karantinaya alınır ve e-posta, takvim ve kişi verileri güncelleştirilmez. Outlook mobil uygulamasını kullanmayı seçerlerse üçüncü taraf uygulama karantinada kalır ve veriler yalnızca Outlook mobil uygulamasıyla eşitlenir. Üçüncü taraf uygulamasını kullanmaya devam etmeye karar verirse veriler anında eşitlenmeye başlar. İlk 24 saat içinde hiçbir işlem yapılmazsa, e-posta gelen kutusundan kaldırılır ve veriler sunucudan otomatik olarak eşitlenmeye başlar.
