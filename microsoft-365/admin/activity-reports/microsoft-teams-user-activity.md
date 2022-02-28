---
title: Microsoft 365 yönetim merkezi raporları - Microsoft Teams etkinliğini gösterir
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
ms.assetid: 07f67fc4-c0a4-4d3f-ad20-f40c7f6db524
description: Kullanıcı etkinliği raporunu nasıl Microsoft Teams hakkında bilgi edinin ve Teams öngörüler elde edin.
ms.openlocfilehash: ec5e6d2aa17fb3e58136a61336f06f6d41f3162f
ms.sourcegitcommit: bf3965b46487f6f8cf900dd9a3af8b213a405989
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/02/2021
ms.locfileid: "62989899"
---
# <a name="microsoft-365-admin-center-reports---microsoft-teams-user-activity"></a>Microsoft 365 yönetim merkezi raporları - Microsoft Teams etkinliğini gösterir

Rapor Microsoft 365 panosu, kurum kurum genelindeki ürünlerde etkinliğin genel görünümünü gösterir. Bu pano sayesinde her bir üründeki etkinliklerle ilgili daha ayrıntılı bilgi edinmek için ürün düzeyinde raporları ayrıntılı olarak inceleyebilirsiniz. [Raporlara genel bakış konusunu](activity-reports.md) gözden geçirin. Microsoft Teams kullanıcı etkinliği raporunda, kuruluşunuzdaki Microsoft Teams etkinliğiyle ilgili öngörüler edinebilirsiniz.
 
## <a name="how-to-get-to-the-microsoft-teams-user-activity-report"></a>Microsoft Teams kullanıcı etkinliği raporuna ulaşma

1. Yönetim merkezinde, **Raporlar** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">Kullanımı</a> sayfasına gidin.

    
2. Rapor **seçin açılan listesinde** Kullanıcı etkinliğini Microsoft Teams  \> **seçin**.
  
## <a name="interpret-the-microsoft-teams-user-activity-report"></a>Microsoft Teams kullanıcı etkinliği raporunu yorumlama

Microsoft Teams kullanıcı etkinliğini görmek için, **Etkinlik** ve **Kullanıcılar** grafiklerine bakabilirsiniz.<br/>![Microsoft 365 sağlar - Microsoft Teams etkinliğini gösterir.](../../media/40359f81-25f7-416d-bb1e-37289133ef6b.png)
  
|Öğe|Açıklama|
|:-----|:-----|
|1.  <br/> |Yeni **Microsoft Teams aktivite** raporu, son 7 gün, 30 gün, 90 gün veya 180 günlük eğilimler için 2013'te 2013'te 2013'ü 2013'e kadar olan eğilimler için 2013'te 2013'ü gösterir. Ancak rapordaki belirli bir günü seçersiniz, tablo geçerli tarihten (raporun oluşturulma tarihine değil) itibaren 28 güne kadar olan verileri gösterir.  <br/> |
|2.  <br/> |Her raporda yer alan veriler genellikle son 24 - 48 saati kapsar.  <br/> |
|3.  <br/> |Veri kalitesini sağlamak için son beş gün içinde günlük veri doğrulama denetimleri gerçekleştirluyoruz ve tespit edilen boşlukları dolduruyoruz. İşlem sırasında geçmiş verilerde farklar olduğunu farkebilirsiniz.  <br/> |
|4.  <br/> |**Etkinlik** görünümü, etkinlik türüne göre Microsoft Teams etkinliklerinin sayısını görüntüler. Etkinlik türleri, ekip sohbeti iletilerinin, özel sohbet iletilerinin, aramaların veya toplantıların sayısıdır.  <br/> |
|5.  <br/> |**Kullanıcılar** görünümü etkinlik türüne göre kullanıcıların sayısını gösterir. Etkinlik türleri, ekip sohbeti iletilerinin, özel sohbet iletilerinin, aramaların veya toplantıların sayısıdır.  <br/> |
|6.  <br/> | Etkinlik **grafiğinde** Y ekseni, belirtilen etkinliğin sayısıdır.  <br/>  Dosyalar **grafiğinde** Y ekseni, ekip sohbetlarına, özel sohbetlere, aramalara veya toplantılara katılan kullanıcıların sayısıdır.  <br/>  Grafiklerde X ekseni, belirli bir rapor için seçilen tarih aralığıdır.  <br/> |
|7.  <br/> |Göstergede bir öğe seçerek grafikte gördüğünüz seriyi filtrenin ekleyebilirsiniz. Örneğin Etkinlik grafiğinde **Kanal** iletileri, Sohbet **iletileri****, Aramalar** veya Toplantılar'ı seçerek yalnızca  bunlardan biri ile ilgili bilgileri görebilirler. Bu seçim değiştirildiğinde kılavuz tablosundaki bilgiler değişmez.  <br/> ![Filtre Microsoft Teams grafiklerini filtreleme.](../../media/c819c4ea-6e9a-4411-a0dd-9f800d64ce38.png)|
|8.  <br/> | Görüntülenen grupların listesi, en geniş raporlama zaman aralığında (180 gün) var olan (silinmemiş) tüm grupların kümesine göre belirlenir. Etkinlik sayısı, tarih seçimine göre değişir.  <br/> NOT: Aşağıdaki listede yer alan tüm öğeleri, siz ekleyene kadar sütunlarda görmeyebilirsiniz.<br/>**Kullanıcı adı**, kullanıcının e-posta adresidir. Asıl e-posta adresini görüntüleyebilir veya bu alanın anonim olmasını sağlayabilirsiniz.  <br/> **Son Etkinlik Tarihi (UTC)**, kullanıcının bir Microsoft Teams etkinliğine katıldığı son tarihi gösterir.  <br/> **Kanal iletileri**, kullanıcının belirtilen süre boyunca ekip sohbetine gönderdiği benzersiz iletilerin sayısıdır.  <br/> **Sohbet iletileri**, kullanıcının belirtilen süre boyunca özel bir sohbete gönderdiği benzersiz iletilerin sayısıdır.  <br/> **Aramalar**, kullanıcının belirtilen süre boyunca katıldığı aramaların sayısıdır.  <br/> **Toplantılar**, kullanıcının belirtilen süre boyunca katıldığı çevrimiçi toplantıların sayısıdır.  <br/> **Diğer etkinlikler**, kullanıcının diğer ekip etkinliklerinin sayısıdır.  <br/> **Silinmiş**, silinen ekip sayısını gösterir. Ekip silinmişse ancak raporlama dönemi içinde etkinliği varsa, kılavuzda silinmiş ayarı doğru değeriyle gösterilir.  <br/> **Silinme tarihi**, ekibin silindiği tarihtir.  <br/> **Atanan ürün**, kullanıcıya atanan ürünlerin listesidir.  <br/>  Kuruluş ilkeleri, kişisel kullanıcı bilgileri içeren raporları görüntülemenizi engel alıyorsa bu raporların gizlilik ayarını değiştirebilirsiniz. Aşağıdaki çalışma **sayfalarındaki Etkinlik Raporları'nın** kullanıcı düzeyi ayrıntılarını [nasıl gizleyim? Microsoft 365 yönetim merkezi](activity-reports.md).  <br/> |
|9.  <br/> |Raporda **sütun** eklemek veya kaldırmak için Sütunlar'ı seçin.  <br/> ![Teams etkinlik raporunu değiştirme - Sütunları seçin.](../../media/eb5fbcee-e371-4d36-a0c6-fa54732311ec.png)|
|10.  <br/> |Ayrıca, Dışarı Aktar bağlantısını seçerek Excel .csv verilerini bir Excel .csv dosyasına **aktarabilirsiniz**. Bu işlem tüm kullanıcıların verilerini dışarı aktarır ve daha fazla çözümleme yapmak için basit sıralama ve filtreleme işlemlerini kullanmanıza olanak tanır. 2000'den az kullanıcınız varsa, raporun kendi içindeki tabloda sıralama ve filtreleme yapabilirsiniz. 2000'den çok kullanıcınız varsa, filtrelemek ve sıralamak için verileri dışarı aktarmanız gerekir.  <br/> |
|||
   

