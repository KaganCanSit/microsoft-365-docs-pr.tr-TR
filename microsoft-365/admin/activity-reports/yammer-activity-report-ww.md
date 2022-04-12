---
title: etkinlik raporlarını Microsoft 365 yönetim merkezi Yammer
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
search.appverid:
- BCS160
- MST160
- MET150
- MOE150
description: Yammer Etkinliği raporunu alın ve ileti göndermek, beğenmek veya okumak için Yammer kullanan kullanıcı sayısı hakkında daha fazla bilgi edinin.
ms.openlocfilehash: 3ab1f13ec9b7b86bb1a7d858b849f22e687ae8aa
ms.sourcegitcommit: ac0ae5c2888e2b323e36bad041a4abef196c9c96
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/12/2022
ms.locfileid: "64781303"
---
# <a name="microsoft-365-reports-in-the-admin-center---yammer-activity-report"></a>Yönetim merkezinde raporları Microsoft 365 - Yammer etkinlik raporu

Microsoft 365 yöneticisi olarak Raporlar panosu, kuruluşunuzdaki ürünlerin kullanımıyla ilgili verileri gösterir. [Yönetim merkezinde etkinlik raporlarına](activity-reports.md) göz atın. **Yammer Etkinlik raporuyla**, ileti göndermek, beğenmek veya okumak için Yammer kullanan benzersiz kullanıcıların sayısına ve kuruluş genelinde gerçekleştirilen etkinlik miktarına bakarak, kuruluşunuzun Yammer'ı kullanma düzeyini anlayabilirsiniz. 
 
## <a name="how-do-i-get-to-the-yammer-activity-report"></a>Yammer etkinlik raporuna Nasıl yaparım? ulaşabilirsiniz?

1. Yönetim merkezinde, **Raporlar** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">Kullanımı</a> sayfasına gidin. 
2. Pano giriş sayfasında, Yammer kartındaki **Daha fazla görüntüle** düğmesine tıklayın.

  
## <a name="interpret-the-yammer-activity-report"></a>Yammer etkinlik raporunu yorumlama

**Etkinlik** sekmesini seçerek Yammer raporundaki etkinlikleri görüntüleyebilirsiniz.<br/>![Microsoft 365 raporları - Microsoft Yammer etkinlik raporu.](../../media/9b251183-c2b3-430c-ab2d-58bf11e7e3ae.png)

Rapora sütun eklemek veya rapordan sütun kaldırmak için Sütunları **seç'i** seçin.  <br/> ![etkinlik raporunu Yammer - sütunları seçin.](../../media/7ef6351d-f7e9-4504-913d-2c2df9062bf6.png)

Dışarı **Aktar bağlantısını** seçerek rapor verilerini bir Excel .csv dosyasına da aktarabilirsiniz. Bu işlem tüm kullanıcıların verilerini dışarı aktarır ve daha fazla çözümleme yapmak için basit sıralama ve filtreleme işlemlerini kullanmanıza olanak tanır. 2000'den az kullanıcınız varsa, raporun kendi içindeki tabloda sıralama ve filtreleme yapabilirsiniz. 2000'den çok kullanıcınız varsa, filtrelemek ve sıralamak için verileri dışarı aktarmanız gerekir. 

**Yammer etkinlik** raporu son 7 gün, 30 gün, 90 gün veya 180 günlük eğilimler için görüntülenebilir. Ancak raporda belirli bir gün seçerseniz, tablo geçerli tarihten itibaren (raporun oluşturulduğu tarihten değil) 28 güne kadar olan verileri gösterir.
  
|Öğe|Açıklama|
|:-----|:-----|
|**Metrik**|**Tanım**|
|Kullanıcı Adı  <br/> |Kullanıcının e-posta adresi. Asıl e-posta adresini görüntüleyebilir veya bu alanın anonim olmasını sağlayabilirsiniz. Bu kılavuzda, Microsoft 365 hesabını kullanarak Yammer oturum açan veya çoklu oturum açma kullanarak ağda oturum açan kullanıcılar gösterilir. <br/> |
|Görünen ad  <br/> |Kullanıcının tam adı. Asıl e-posta adresini görüntüleyebilir veya bu alanın anonim olmasını sağlayabilirsiniz.  <br/> |
|Kullanıcı durumu  <br/> |Üç değerden biri: Etkinleştirildi, Silindi veya Askıya Alındı. Bu raporlarda etkin, askıya alınan ve silinen kullanıcıların verileri gösterilir. Bunlar bekleyen kullanıcıları yansıtmaz, çünkü bekleyen kullanıcılar iletileri gönderemez, okuyamaz veya beğenemez.  <br/> |
|Durum değiştirme tarihi (UTC)  <br/> |kullanıcının durumunun Yammer değiştirildiği tarih.  <br/> |
|Son etkinlik tarihi (UTC)  <br/> | Kullanıcının bir iletiyi yayınladığı, okuduğu veya beğendiği son tarih.  <br/> |
|Yayınlanan  <br/> |Kullanıcının belirttiğiniz zaman aralığında yayımlamış olduğu ileti sayısı. <br/>|
|Okuma  <br/> |Kullanıcının belirttiğiniz zaman aralığında okuduğu konuşma sayısı.  <br/> |
|Sevdim  <br/> |Belirttiğiniz zaman aralığında kullanıcının beğendiği ileti sayısı.  <br/>|
|Ürün atandı  <br/> |Bu kullanıcıya atanan ürünler.|
|||