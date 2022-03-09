---
title: Microsoft 365 yönetim merkezi Teams etkinlik raporlarını raporlar
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ROBOTS: NOINDEX, NOFOLLOW
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
description: Kullanıcı etkinliği raporunu nasıl Microsoft Teams hakkında bilgi edinin ve Teams öngörüler elde edin.
ms.openlocfilehash: cfb503c09577d4538371ad6a5b35520d8da24bdb
ms.sourcegitcommit: cdb90f28e59f36966f8751fa8ba352d233317fc1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2022
ms.locfileid: "63400846"
---
# <a name="microsoft-365-reports-in-the-admin-center---microsoft-teams-user-activity"></a>Microsoft 365 Merkezinde Rapor Raporları - Microsoft Teams etkinliğini gösterir

Rapor Microsoft 365 panosu, kurum kurum genelindeki ürünlerde etkinliğin genel görünümünü gösterir. Bu pano sayesinde her bir üründeki etkinliklerle ilgili daha ayrıntılı bilgi edinmek için ürün düzeyinde raporları ayrıntılı olarak inceleyebilirsiniz. [Raporlara genel bakış konusunu](activity-reports.md) gözden geçirin. Microsoft Teams kullanıcı etkinliği raporunda, kuruluşunuzdaki Microsoft Teams etkinliğiyle ilgili öngörüler edinebilirsiniz.
 
## <a name="how-to-get-to-the-microsoft-teams-user-activity-report"></a>Microsoft Teams kullanıcı etkinliği raporuna ulaşma

1. Yönetim merkezinde, **Raporlar** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">Kullanımı</a> sayfasına gidin.
2. Pano giriş sayfasında, etkinlik kartında **Daha fazla** görüntüle Microsoft Teams tıklayın.

## <a name="interpret-the-microsoft-teams-user-activity-report"></a>Microsoft Teams kullanıcı etkinliği raporunu yorumlama

Kullanıcı etkinliği sekmesini seçerek Teams raporunda **görüntüleyebilirsiniz**. <br/>![Microsoft 365 sağlar - Microsoft Teams etkinliğini gösterir.](../../media/1011877f-3cf0-4417-9447-91d0b2312aab.png)

Raporda **sütun eklemek** veya kaldırmak için Sütunları seç'i seçin.  <br/> ![Teams etkinlik raporunu değiştirme - Sütunları seçin.](../../media/6d3c013e-2c5e-4d66-bb41-998aa4bd1c20.png)

Ayrıca, Dışarı Aktar bağlantısını seçerek Excel .csv verilerini bir Excel .csv dosyasına **aktarabilirsiniz**. Bu işlem tüm kullanıcıların verilerini dışarı aktarır ve daha fazla çözümleme yapmak için basit sıralama ve filtreleme işlemlerini kullanmanıza olanak tanır. 2000'den az kullanıcınız varsa, raporun kendi içindeki tabloda sıralama ve filtreleme yapabilirsiniz. 2000'den çok kullanıcınız varsa, filtrelemek ve sıralamak için verileri dışarı aktarmanız gerekir. Ses zamanı, video **zamanı ve** **ekran** paylaşım süresi için dışarı **aktarıldı biçimi** ISO8601 süre biçimini izler.

Yeni **Microsoft Teams aktivite** raporu, son 7 gün, 30 gün, 90 gün veya 180 günlük eğilimler için 2013'te 2013'te 2013'ü 2013'e kadar olan eğilimler için 2013'te 2013'ü gösterir. Ancak rapordaki belirli bir günü seçersiniz, tablo geçerli tarihten (raporun oluşturulma tarihine değil) itibaren 28 güne kadar olan verileri gösterir.

Veri kalitesini sağlamak için, son üç gün içinde günlük veri doğrulama denetimleri gerçekleştirluyoruz ve tespit edilen boşlukları dolduruyoruz. İşlem sırasında geçmiş verilerde farklar olduğunu farkebilirsiniz.

|Öğe|Açıklama|
|:-----|:-----|
|**Metrik**|**Tanım**|
|Kullanıcı adı  <br/> |Kullanıcının e-posta adresi. Asıl e-posta adresini görüntüleyebilir veya bu alanın anonim olmasını sağlayabilirsiniz.   <br/> |
|Kanal iletileri   <br/> |Kullanıcının belirtilen süre boyunca bir ekip sohbeti'ne posta gönderen benzersiz iletilerin sayısı.  <br/> |
|Sohbet iletileri   <br/> |Kullanıcının belirtilen süre boyunca özel bir sohbete göndermesi için gönderilen benzersiz iletilerin sayısı.  <br/> |
|Toplam toplantı sayısı   <br/> |Kullanıcının belirtilen süre boyunca katıldığı çevrimiçi toplantıların sayısı.  <br/> |
|Bire bir aramalar   <br/> | Kullanıcının belirtilen süre boyunca katıldığı 1:1 arama sayısı.  <br/> |
|Son etkinlik tarihi (UTC)  <br/> |Kullanıcının bir etkinlik etkinliğine katıldığı son Microsoft Teams.<br/> |
|Geçici olarak katılan toplantılar   <br/> | Kullanıcının belirtilen süre boyunca katıldığı geçici toplantı sayısı.  <br/> |
|Geçici olarak düzenlenen toplantılar <br/> |Kullanıcının belirtilen süre boyunca düzenlediği geçici toplantı sayısı. <br/>|
|Düzenlenen toplam toplantılar  <br/> |Kullanıcının belirtilen süre boyunca düzenlediği bir defalık zamanlanmış, Yinelenen, özel ve sınıflandırılmamış toplantıların toplamı.  <br/> |
|Toplam katılımlı toplantılar  <br/> |Kullanıcının belirtilen süre boyunca katıldığı bir defalık zamanlanmış, yinelenen, özel ve sınıflandırılmamış toplantıların toplamı.  <br/> |
|Tek sefer olarak zamanlanmış toplantılar  <br/> |Kullanıcının belirtilen süre boyunca düzenlediği, bir defalık zamanlanmış toplantıların sayısı.  <br/> |
|Zamanlanmış yinelenen toplantılar düzenlenmiş  <br/> |Kullanıcının belirtilen süre boyunca düzenlediği yinelenen toplantıların sayısı.  <br/> |
|Tek sefer olarak zamanlanan toplantılar  <br/> |Kullanıcının belirtilen süre boyunca katıldığı bir defalık zamanlanmış toplantıların sayısı.  <br/> |
|Zamanlanan yinelenen toplantıya katılan toplantılar  <br/> |Kullanıcının belirtilen süre boyunca katıldığı yinelenen toplantıların sayısı.  <br/> |
|Lisansı var  <br/> |Kullanıcının e-posta hesabı kullanma lisansı varsa Teams. <br/>|
|Diğer etkinlikler  <br/>|Kullanıcı etkindir, ancak raporda sunulan eylem türlerinden farklı etkinlikler gerçekleştirmiştir (kanal iletilerini ve sohbet iletilerini gönderme veya yanıtlama, bire bir arama ve toplantı zamanlama veya buna katılma). Örnek eylemler, kullanıcı e-posta Teams durumunu veya son durum Teams değiştirir ya da Kanal Mesajı gönderisi açtığında yanıtlanmaz.  <br/>|
|Sınıflandırılmamış toplantılar <br/>|Zamanlama, yinelenen veya geçici olarak sınıflandırılamaz. Bunlar sayı olarak kısadır ve çoğunlukla oynanmış telemetri bilgileri nedeniyle belirlenemeyen bir bilgidir. |
|||
