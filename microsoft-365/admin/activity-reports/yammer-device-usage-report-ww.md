---
title: Microsoft 365 Merkezinde Raporları - Cihaz Yammer raporuna bakın
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
description: Kullanıcı Yammer hangi cihazları Yammer bilgi almak için cihaz kullanım Yammer edin.
ms.openlocfilehash: 25dbf966d0756cf90e39dcbe69d587434d3de3ae
ms.sourcegitcommit: bf3965b46487f6f8cf900dd9a3af8b213a405989
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/02/2021
ms.locfileid: "62989882"
---
# <a name="microsoft-365-reports-in-the-admin-center---yammer-device-usage-report"></a>Microsoft 365 Merkezinde Raporları - Cihaz Yammer raporuna bakın

Rapor Microsoft 365 panosu, kurum kurum genelindeki ürünlerde etkinliğin genel görünümünü gösterir. Bu pano sayesinde her bir üründeki etkinliklerle ilgili daha ayrıntılı bilgi edinmek için ürün düzeyinde raporları ayrıntılı olarak inceleyebilirsiniz. [Raporlara genel bakış konusuna](activity-reports.md) göz atın.
  
Yammer cihaz kullanım raporları kullanıcılarınızın Yammer'ı hangi cihazlar üzerinde kullandığı hakkında bilgi verir. Cihaz türüne göre günlük kullanıcı sayısını ve cihaz türüne göre kullanıcı sayısını görüntüleyebilirsiniz. Bu bilgilerin ikisi de seçili bir zaman aralığında görüntülenebilir. Dilerseniz, kullanıcı başına ayrıntıları da görüntüleyebilirsiniz.
 
## <a name="how-do-i-get-to-the-yammer-device-usage-report"></a>Yammer cihaz kullanım raporuna nasıl ulaşabilirim?

1. Yönetim merkezinde, **Raporlar** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">Kullanımı</a> sayfasına gidin. 
2. Pano giriş sayfasında, pano kartında **Daha fazla** görüntüle Yammer tıklayın.
  
## <a name="interpret-the-yammer-device-usage-report"></a>Cihaz Yammer raporunu yorumlama

Cihaz kullanımı sekmesini seçerek OneDrive raporuna **bakabilirsiniz**.<br/>![Microsoft 365 sağlar - Microsoft Yammer kullanım raporu.](../../media/e21af4c0-0ad2-4485-8ab1-2f82d7dfa90e.png)

Raporda **sütun eklemek** veya kaldırmak için Sütunları seç'i seçin.  <br/> ![Yammer kullanım raporunu değiştirme - Sütunlar'ı seçin.](../../media/fc1fc8db-e197-4878-85c7-7ba0d67b9379.png)

Ayrıca, Dışarı Aktar bağlantısını seçerek Excel .csv verilerini bir Excel .csv dosyasına **aktarabilirsiniz**. Bu işlem tüm kullanıcıların verilerini dışarı aktarır ve daha fazla çözümleme yapmak için basit sıralama ve filtreleme işlemlerini kullanmanıza olanak tanır. 2000'den az kullanıcınız varsa, raporun kendi içindeki tabloda sıralama ve filtreleme yapabilirsiniz. 2000'den çok kullanıcınız varsa, filtrelemek ve sıralamak için verileri dışarı aktarmanız gerekir. 

En **Yammer kullanım** raporu, son 7 gün, 30 gün, 90 gün veya 180 günlük eğilimler için görüntülenebilirsiniz. Ancak rapordaki belirli bir günü seçersiniz, tablo geçerli tarihten (raporun oluşturulma tarihine değil) itibaren 28 güne kadar olan verileri gösterir.
  
|Öğe|Açıklama|
|:-----|:-----|
|**Metrik**|**Tanım**|
|Kullanıcı Adı  <br/> |Kullanıcının e-posta adresi. Asıl e-posta adresini görüntüleyebilir veya bu alanın anonim olmasını sağlayabilirsiniz. Bu kılavuzda, hesap hesabını kullanarak Yammer veya çoklu oturum açma Microsoft 365 kullanarak ağa oturum açan kullanıcılar görüntülenir. <br/> |
|Görünen ad  <br/> |Kullanıcının tam adı. Asıl e-posta adresini görüntüleyebilir veya bu alanın anonim olmasını sağlayabilirsiniz.  <br/> |
|Kullanıcı durumu  <br/> |Üç değerden biri: Etkin, Silindi veya Askıya Alındı. Bu raporlarda etkin, askıya alınan ve silinen kullanıcıların verileri gösterilir. Bunlar bekleyen kullanıcıları yansıtmaz, çünkü bekleyen kullanıcılar iletileri gönderemez, okuyamaz veya beğenemez.   <br/> |
|Durum değişiklik tarihi (UTC)  <br/> |Bu tarihte kullanıcının durumunun hangi tarihte değiştir Yammer.  <br/> |
|Son etkinlik tarihi (UTC)  <br/> |Kullanıcının bir etkinlikte katıldığı son tarih (UTC Yammer.  <br/> |
|Web  <br/> |Kullanıcının web üzerinde e-posta Yammer olduğunu gösterir.  <br/> |
|Windows telefonu  <br/> | Kullanıcının başka bir telefonda telefon Yammer olduğunu Windows gösterir.  <br/> |
|Android telefon  <br/> |Kullanıcının bir Android telefonda Yammer kullanıcı adını kullandırdı olduğunu gösterir. <br/>|
|iphone <br/> | Kullanıcının bir dosyada kimlik Yammer olduğunu iPhone.  <br/> |
|ipad  <br/> |Kullanıcının bir dosyada kimlik Yammer olduğunu iPad. <br/>|
|diğer  <br/> |Kullanıcının daha önce listelenmiyorsa Yammer kullanıcı adını başka bir cihazda kullandı olup olmadığını gösterir. <br/>|
|||