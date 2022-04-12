---
title: Uygulama kullanım raporlarını Microsoft 365 yönetim merkezi Teams
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_NonTOC
ms.custom: AdminSurgePortfolio
ROBOTS: NOINDEX, NOFOLLOW
search.appverid:
- BCS160
- MST160
- MET150
- MOE150
description: Microsoft 365 Raporlarından Microsoft Teams uygulama kullanım raporunu alarak kuruluşunuzda kullanılan Microsoft Teams uygulamaları hakkında içgörüler elde edin.
ms.openlocfilehash: de12133d16cd2b53140ccf2fafafc76abc064776
ms.sourcegitcommit: ac0ae5c2888e2b323e36bad041a4abef196c9c96
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/12/2022
ms.locfileid: "64781785"
---
# <a name="microsoft-365-reports-in-the-admin-center---microsoft-teams-device-usage"></a>Yönetim merkezinde raporları Microsoft 365 - cihaz kullanımını Microsoft Teams

Microsoft 365 Raporları panosu, kuruluşunuzdaki ürünler genelindeki etkinliğe genel bakışı gösterir. Bu pano sayesinde her bir üründeki etkinliklerle ilgili daha ayrıntılı bilgi edinmek için ürün düzeyinde raporları ayrıntılı olarak inceleyebilirsiniz. [Raporlara genel bakış konusunu](activity-reports.md) gözden geçirin. Microsoft Teams uygulama kullanımı raporunda, kuruluşunuzda kullanılan Microsoft Teams uygulamalarıyla ilgili öngörüler edinebilirsiniz.
  
## <a name="how-to-get-to-the-microsoft-teams-app-usage-report"></a>Microsoft Teams uygulama kullanımı raporuna ulaşma

1. Yönetim merkezinde, **Raporlar** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">Kullanımı</a> sayfasına gidin. 
2. Pano giriş sayfasında, Microsoft Teams etkinlik kartındaki **Daha fazla görüntüle** düğmesine tıklayın.
  
## <a name="interpret-the-microsoft-teams-app-usage-report"></a>Microsoft Teams uygulama kullanımı raporunu yorumlama

Cihaz **kullanımı** sekmesini seçerek cihaz kullanımını Teams raporunda görüntüleyebilirsiniz.<br/>![Microsoft 365 raporları - cihaz kullanımını Microsoft Teams.](../../media/e46c7f7c-8371-4a20-ae82-b20df64b0205.png)

Rapora sütun eklemek veya rapordan sütun kaldırmak için Sütunları **seç'i** seçin.  <br/> ![Kullanıcı cihazı raporunu Teams - sütunları seçin.](../../media/3358d5d9-931b-4d30-931f-450b2f5717da.png)

Dışarı **Aktar bağlantısını** seçerek rapor verilerini bir Excel .csv dosyasına da aktarabilirsiniz. Bu işlem tüm kullanıcıların verilerini dışarı aktarır ve daha fazla çözümleme yapmak için basit sıralama ve filtreleme işlemlerini kullanmanıza olanak tanır. 2000'den az kullanıcınız varsa, raporun kendi içindeki tabloda sıralama ve filtreleme yapabilirsiniz. 2000'den çok kullanıcınız varsa, filtrelemek ve sıralamak için verileri dışarı aktarmanız gerekir. 

**Microsoft Teams cihaz kullanımı** raporu, son 7 gün, 30 gün, 90 gün veya 180 günlük eğilimler için görüntülenebilir. Ancak raporda belirli bir gün seçerseniz, tablo geçerli tarihten itibaren (raporun oluşturulduğu tarihten değil) 28 güne kadar olan verileri gösterir.
  
|Öğe|Açıklama|
|:-----|:-----|
|**Metrik**|**Tanım**|
|Kullanıcı adı  <br/> |Kullanıcının görünen adı.  <br/> |
|Windows  <br/> |Kullanıcı Windows tabanlı bir bilgisayarda Teams masaüstü istemcisinde etkinse seçilir.  <br/> |
|Mac  <br/> |Kullanıcı macOS bilgisayardaki Teams masaüstü istemcisinde etkinse seçilir.  <br/> |
|iOS  <br/> |Kullanıcı iOS için Teams mobil istemcisinde etkinse seçilir.  <br/> |
|Android telefon  <br/> | Kullanıcı Android için Teams mobil istemcisinde etkinse seçilir.  <br/> |
|Chrome OS  <br/> |Kullanıcının ChromeOS bilgisayardaki Teams masaüstü istemcisinde etkin olup olmadığını seçin.|
|Linux  <br/> | Kullanıcı bir Linux bilgisayardaki Teams masaüstü istemcisinde etkinse seçilir.  <br/> |
|Web  <br/> |Kullanıcı cihazlardaki Teams web istemcisinde etkinse seçilir.|
|Son etkinlik tarihi (UTC)  <br/> |Kullanıcının bir Teams etkinliğine katıldığı son tarih (UTC).  <br/> |
|Lisanslıdır|Kullanıcı Teams kullanma lisansına sahipse seçilir.|

## <a name="see-also"></a>Ayrıca bkz.
[kullanıcı etkinlik raporunu Microsoft Teams](../activity-reports/microsoft-teams-user-activity-preview.md) 

[kullanım etkinliği raporunu Microsoft Teams](../activity-reports/microsoft-teams-usage-activity.md) 
