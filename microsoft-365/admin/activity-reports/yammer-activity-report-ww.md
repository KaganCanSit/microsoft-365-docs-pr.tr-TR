---
title: Microsoft 365 yönetim merkezi Yammer raporları
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
description: Etkinlik Yammer raporunu alarak ileti gönderebilirsiniz, iletiyi Yammer veya okuyabilirsiniz.
ms.openlocfilehash: e5e865266d09d839777ed00feddf3682a24b6e7e
ms.sourcegitcommit: cdb90f28e59f36966f8751fa8ba352d233317fc1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2022
ms.locfileid: "63400441"
---
# <a name="microsoft-365-reports-in-the-admin-center---yammer-activity-report"></a>Microsoft 365 Merkezinde Rapor Raporları - Yammer raporu

Bir Microsoft 365 yöneticisi olarak, Raporlar panosu size kuruluş içindeki ürünlerin kullanımıyla ilgili veriler gösterir. Yönetim merkezinde [etkinlik raporlarına göz at.](activity-reports.md) **Yammer Etkinlik raporuyla**, ileti göndermek, beğenmek veya okumak için Yammer kullanan benzersiz kullanıcıların sayısına ve kuruluş genelinde gerçekleştirilen etkinlik miktarına bakarak, kuruluşunuzun Yammer'ı kullanma düzeyini anlayabilirsiniz. 
 
## <a name="how-do-i-get-to-the-yammer-activity-report"></a>Etkinlik raporunu nasıl Yammer?

1. Yönetim merkezinde, **Raporlar** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">Kullanımı</a> sayfasına gidin. 
2. Pano giriş sayfasında, pano kartında **Daha fazla** görüntüle Yammer tıklayın.

  
## <a name="interpret-the-yammer-activity-report"></a>Yammer etkinlik raporunu yorumlama

Etkinlik sekmesini seçerek çalışma Yammer etkinlikleri **görüntüleyebilirsiniz**.<br/>![Microsoft 365- Microsoft Yammer raporu.](../../media/9b251183-c2b3-430c-ab2d-58bf11e7e3ae.png)

Raporda **sütun eklemek** veya kaldırmak için Sütunları seç'i seçin.  <br/> ![Yammer raporu - Sütunlar'ı seçin.](../../media/7ef6351d-f7e9-4504-913d-2c2df9062bf6.png)

Ayrıca, Dışarı Aktar bağlantısını seçerek Excel .csv verilerini bir Excel .csv dosyasına **aktarabilirsiniz**. Bu işlem tüm kullanıcıların verilerini dışarı aktarır ve daha fazla çözümleme yapmak için basit sıralama ve filtreleme işlemlerini kullanmanıza olanak tanır. 2000'den az kullanıcınız varsa, raporun kendi içindeki tabloda sıralama ve filtreleme yapabilirsiniz. 2000'den çok kullanıcınız varsa, filtrelemek ve sıralamak için verileri dışarı aktarmanız gerekir. 

Yammer **aktivite** raporu, son 7 gün, 30 gün, 90 gün veya 180 günlük eğilimler için görüntülenebilirsiniz. Ancak rapordaki belirli bir günü seçersiniz, tablo geçerli tarihten (raporun oluşturulma tarihine değil) itibaren 28 güne kadar olan verileri gösterir.
  
|Öğe|Açıklama|
|:-----|:-----|
|**Metrik**|**Tanım**|
|Kullanıcı Adı  <br/> |Kullanıcının e-posta adresi. Asıl e-posta adresini görüntüleyebilir veya bu alanın anonim olmasını sağlayabilirsiniz. Bu kılavuzda, hesap hesabını kullanarak Yammer veya çoklu oturum açma Microsoft 365 kullanarak ağa oturum açan kullanıcılar görüntülenir. <br/> |
|Görünen ad  <br/> |Kullanıcının tam adı. Asıl e-posta adresini görüntüleyebilir veya bu alanın anonim olmasını sağlayabilirsiniz.  <br/> |
|Kullanıcı durumu  <br/> |Üç değerden biri: Etkinleştirildi, Silindi veya Askıya Alındı. Bu raporlarda etkin, askıya alınan ve silinen kullanıcıların verileri gösterilir. Bunlar bekleyen kullanıcıları yansıtmaz, çünkü bekleyen kullanıcılar iletileri gönderemez, okuyamaz veya beğenemez.  <br/> |
|Durum değişiklik tarihi (UTC)  <br/> |Bu tarihte kullanıcının durumunun hangi tarihte değiştir Yammer.  <br/> |
|Son etkinlik tarihi (UTC)  <br/> | Kullanıcının bir iletiyi göndermesi, okuması veya beğen olduğu son tarih.  <br/> |
|Gönderilen  <br/> |Belirttiğiniz süre boyunca kullanıcının göndermesi gönderilen ileti sayısı. <br/>|
|Oku  <br/> |Belirttiğiniz süre boyunca kullanıcının okuduğu konuşma sayısı.  <br/> |
|Beğenildi  <br/> |Belirttiğiniz süre boyunca kullanıcının beğendiğini iletilerin sayısı.  <br/>|
|Ürün atandı  <br/> |Bu kullanıcıya atanan ürünler.|
|||