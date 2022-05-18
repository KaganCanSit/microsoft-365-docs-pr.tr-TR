---
title: etkinlik raporlarını Microsoft 365 OneDrive İş
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
description: Kuruluşunuz için OneDrive kullanım raporunu alın ve her OneDrive kullanıcının etkinliğini, paylaşılan dosya sayısını ve depolama kullanımını öğrenin.
ms.openlocfilehash: 65046154e17cdb79ee671ec14aa45d089730ca97
ms.sourcegitcommit: da6b3cb3b2ccfcdcd5091efce8290b6c486547db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/18/2022
ms.locfileid: "65467262"
---
# <a name="microsoft-365-reports-in-the-admin-center---onedrive-for-business-activity"></a>Yönetim merkezinde raporları Microsoft 365 - OneDrive İş etkinliği

Microsoft 365 Raporları panosu, kuruluşunuzdaki ürünler genelindeki etkinliğe genel bakışı gösterir. Bu pano sayesinde ürünlerin her birindeki etkinliklerle ilgili daha ayrıntılı bilgi edinmek için ürün düzeyinde raporları ayrıntılı olarak inceleyebilirsiniz. [Raporlara genel bakış konusuna](activity-reports.md) göz atın.
  
Örneğin, OneDrive kullanma lisansı olan her kullanıcının etkinliğini anlamak için OneDrive'da dosyalarla etkileşimlerine bakabilirsiniz. Ayrıca, paylaşılan dosya sayısına bakarak işbirliği düzeyini anlamanıza da yardımcı olabilir.

## <a name="how-do-i-get-to-the-onedrive-activity-report"></a>OneDrive Etkinlik raporuna nasıl ulaşabilirim?

1. Yönetim merkezinde, **Raporlar** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">Kullanımı</a> sayfasına gidin. 
2. Pano giriş sayfasında, OneDrive kartındaki **Daha fazla görüntüle** düğmesine tıklayın.
  
## <a name="interpret-the-onedrive-for-business-activity-report"></a>OneDrive İş etkinlik raporunu yorumlama

**Etkinlik** sekmesini seçerek OneDrive raporundaki etkinlikleri görüntüleyebilirsiniz.<br/>![Microsoft 365 raporları - etkinlik raporu Microsoft OneDrive.](../../media/c89df0b0-2611-4acf-9ef7-17cedf7977be.png)

Rapora sütun eklemek veya rapordan sütun kaldırmak için Sütunları **seç'i** seçin.  <br/> ![etkinlik raporunu OneDrive - sütunları seçin.](../../media/252f311f-ffde-4e5a-9158-2b822bf86964.png)

Dışarı **Aktar bağlantısını** seçerek rapor verilerini bir Excel .csv dosyasına da aktarabilirsiniz. Bu işlem tüm kullanıcıların verilerini dışarı aktarır ve daha fazla çözümleme yapmak için basit sıralama ve filtreleme işlemlerini kullanmanıza olanak tanır. 2000'den az kullanıcınız varsa, raporun kendi içindeki tabloda sıralama ve filtreleme yapabilirsiniz. 2000'den çok kullanıcınız varsa, filtrelemek ve sıralamak için verileri dışarı aktarmanız gerekir.

**OneDrive İş aktivite** raporu, son 7 gün, 30 gün, 90 gün veya 180 günlük eğilimler için görüntülenebilir. Ancak raporda belirli bir gün seçerseniz, tablo geçerli tarihten itibaren (raporun oluşturulduğu tarihten değil) 28 güne kadar olan verileri gösterir.
  
|Öğe|Açıklama|
|:-----|:-----|
|**Metrik**|**Tanım**|
|Kullanıcı Adı  <br/> |OneDrive hesabının sahibinin kullanıcı adı.  <br/> |
|Son etkinlik tarihi (UTC)  <br/> |Seçilen tarih aralığı için OneDrive hesabında bir dosya etkinliğinin gerçekleştirildiği en son tarih. . Belirli bir tarihte gerçekleştirilen etkinliği görmek için, grafikte doğrudan tarihi seçin.  <br/> |
|Görüntülenen veya düzenlenen dosyalar  <br/> |Kullanıcının karşıya yüklediği, indirdiği, değiştirdiği veya görüntülendiği dosya sayısı.   <br/> |
|Eşitlenen dosyalar  <br/> |Kullanıcının yerel cihazından OneDrive hesabına eşitlenen dosyaların sayısı. <br/> |
|Dahili olarak paylaşılan dosyalar  <br/> | Kuruluştaki kullanıcılarla veya gruplar içindeki kullanıcılarla (dış kullanıcıları içerebilecek) paylaşılan dosyaların sayısı.  <br/> |
|Harici olarak paylaşılan dosyalar  <br/> |Kuruluş dışındaki kullanıcılarla paylaşılan dosyaların sayısı. <br/>|
|Silindi  <br/> | Bu, kullanıcının lisansının kaldırıldığını gösterir.  <br/> NOT: Silinen bir kullanıcının etkinliği, seçilen zaman aralığında bir süre lisanslandığı sürece raporda görüntülenmeye devam eder. **Silindi** sütunu, kullanıcının artık etkin olamayacağını ama rapordaki verilere katkıda bulunduğunu belirlemenize yardımcı olur.  <br/> |
|Silinme tarihi  <br/> |Kullanıcının lisansının kaldırıldığı tarih. <br/>|
|Ürün atandı  <br/> |Kullanıcıya lisans verilen Microsoft 365 ürünleri.|
|||