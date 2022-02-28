---
title: Microsoft 365 Merkezinde Rapor Raporları - SharePoint etkinlikleri
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
description: Her SharePoint etkinliği, paylaşılan dosya sayısı ve depolama kullanımı hakkında bilgi SharePoint bir etkinlik kullanım raporuna sahip olur.
ms.openlocfilehash: b130ad1cca6e25a939b942ed98910ba10150ab40
ms.sourcegitcommit: bf3965b46487f6f8cf900dd9a3af8b213a405989
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/02/2021
ms.locfileid: "62989897"
---
# <a name="microsoft-365-reports-in-the-admin-center---sharepoint-activity"></a>Microsoft 365 Merkezinde Rapor Raporları - SharePoint etkinlikleri

Bir Microsoft 365 yöneticisi olarak, Raporlar panosu, kurum çeşitli ürünlerin etkinliğine bir genel bakış gösterir. Bu pano size, her ürüne özgü etkinlikler hakkında daha ayrıntılı bilgi edinmek için detaya gitme olanağı tanır. Etkinlik raporlarını [çalışma sayfalarında Microsoft 365 yönetim merkezi](activity-reports.md).
  
Örneğin, SharePoint kullanma lisansı olan her kullanıcının etkinliğini anlamak için dosyalarla etkileşimlerine bakabilirsiniz. Ayrıca, paylaşılan dosya sayısına bakarak işbirliği düzeyini anlamanıza da yardımcı olabilir.
  
## <a name="how-do-i-get-to-the-to-the-sharepoint-activity-report"></a>SharePoint etkinlik raporuna nereden ulaşabilirim?

1. Yönetim merkezinde, **Raporlar** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">Kullanımı</a> sayfasına gidin. 
2. Pano giriş sayfasında, pano kartında **Daha fazla** görüntüle SharePoint tıklayın.
  
## <a name="interpret-the-sharepoint-activity-report"></a>Etkinlik SharePoint yorumlama

Etkinlik sekmesini seçerek çalışma SharePoint etkinlikleri **görüntüleyebilirsiniz**.<br/>![Microsoft 365- Microsoft SharePoint raporu.](../../media/5a0a96f-0e4f-4fb9-8baa-3262275b3d1f.png)

Raporda **sütun eklemek** veya kaldırmak için Sütunları seç'i seçin.  <br/> ![SharePoint raporu - Sütunlar'ı seçin.](../../media/3c396cd1-9701-4712-8eaa-eb7bba702aa8.png)

Ayrıca, Dışarı Aktar bağlantısını seçerek Excel .csv verilerini bir Excel .csv dosyasına **aktarabilirsiniz**. Bu işlem tüm kullanıcıların verilerini dışarı aktarır ve daha fazla çözümleme yapmak için basit sıralama ve filtreleme işlemlerini kullanmanıza olanak tanır. 2000'den az kullanıcınız varsa, raporun kendi içindeki tabloda sıralama ve filtreleme yapabilirsiniz. 2000'den çok kullanıcınız varsa, filtrelemek ve sıralamak için verileri dışarı aktarmanız gerekir. 

Yeni **SharePoint raporu**, son 7 gün, 30 gün, 90 gün veya 180 günlük eğilimler için 2013'te 2013'te 2013'ü 2013'e kadar 2013'e kadar olan eğilimler için 2013'te 2013'ü 2013'e kadar görüntüleyebilirsiniz. Ancak rapordaki belirli bir günü seçersiniz, tablo geçerli tarihten (raporun oluşturulma tarihine değil) itibaren 28 güne kadar olan verileri gösterir.
  
|Öğe|Açıklama|
|:-----|:-----|
|**Metrik**|**Tanım**|
|Kullanıcı Adı  <br/> |Etkinlik 2013 Sitesinde etkinliği gerçekleştiren kullanıcının e-SharePoint.  <br/> |
|Son etkinlik tarihi (UTC)  <br/> |Seçilen tarih aralığı için dosya etkinliğinin gerçekleştir başlangıç tarihi veya bir sayfanın ziyaret edildi olduğu tarih. Belirli bir tarihte gerçekleştirilen etkinliği görmek için, grafikte doğrudan tarihi seçin.  <br/> |
|Görüntülenen veya düzenlenen dosyalar  <br/> |Kullanıcının karşıya yükleytiği, indirdiğiniz, değiştirdiğiniz veya görüntülediğiniz dosya sayısı.   <br/> |
|Eşitlenen dosyalar  <br/> |Kullanıcının yerel cihazından site siteyle eşitlenen dosyaların SharePoint. <br/> |
|Şirket içinde paylaşılan dosyalar  <br/> | Kuruluş içindeki kullanıcılarla veya gruplarda bulunan kullanıcılarla (dış kullanıcılar da dahil) paylaşılan dosyaların sayısı.  <br/> |
|Dışarıdan paylaşılan dosyalar  <br/> |Kuruluşun dışındaki kullanıcılarla paylaşılan dosya sayısı. <br/>|
|Ziyaret edilen sayfalar  <br/> |Kullanıcı tarafından benzersiz sayfalara yapılan ziyaretler. <br/>|
|Silindi  <br/> | Bu, kullanıcının lisansının kaldırıldığına işarettir.  <br/>  **NOT:** Seçilen dönem içinde bir süre lisanslı olduğu sürece, silinen kullanıcının etkinliği raporda görüntülenir. Silindi sütunu, kullanıcının artık etkin olamayacağını ama rapordaki verilere katkıda bulunduğunu belirlemenize yardımcı olur.  <br/> |
|Silinme tarihi  <br/> |Kullanıcının lisansının kaldırıldığı tarih. <br/>|
|Ürün atandı  <br/> |Kullanıcıya Microsoft 365 lisansları olan ürünler.|
|||