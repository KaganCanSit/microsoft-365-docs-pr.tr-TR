---
title: Kullanıcı etkinlik raporlarını Microsoft 365 yönetim merkezi Teams
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
description: Microsoft Teams kullanıcı etkinliği raporunu almayı ve kuruluşunuzdaki Teams etkinliğiyle ilgili içgörüler elde etmeyi öğrenin.
ms.openlocfilehash: a2bfa434d5a564307498f621cb5105f411daff4d
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65087227"
---
# <a name="microsoft-365-reports-in-the-admin-center---microsoft-teams-user-activity"></a>Yönetim merkezinde raporları Microsoft 365 - Microsoft Teams kullanıcı etkinliği

Microsoft 365 Raporları panosu, kuruluşunuzdaki ürünler genelindeki etkinliğe genel bakışı gösterir. Bu pano sayesinde her bir üründeki etkinliklerle ilgili daha ayrıntılı bilgi edinmek için ürün düzeyinde raporları ayrıntılı olarak inceleyebilirsiniz. [Raporlara genel bakış konusunu](activity-reports.md) gözden geçirin. Microsoft Teams kullanıcı etkinliği raporunda, kuruluşunuzdaki Microsoft Teams etkinliğiyle ilgili öngörüler edinebilirsiniz.
 
## <a name="how-to-get-to-the-microsoft-teams-user-activity-report"></a>Microsoft Teams kullanıcı etkinliği raporuna ulaşma

1. Yönetim merkezinde, **Raporlar** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">Kullanımı</a> sayfasına gidin.

2. Pano giriş sayfasında, Microsoft Teams etkinlik kartındaki **Daha fazla görüntüle** düğmesine tıklayın.

## <a name="interpret-the-microsoft-teams-user-activity-report"></a>Microsoft Teams kullanıcı etkinliği raporunu yorumlama

Kullanıcı etkinliği sekmesini seçerek Teams raporundaki **kullanıcı etkinliğini** görüntüleyebilirsiniz. <br/>![Microsoft 365 raporları - kullanıcı etkinliğini Microsoft Teams.](../../media/user-activity-charts.png)

Rapora sütun eklemek veya rapordan sütun kaldırmak için Sütunları **seç'i** seçin.  <br/> ![Kullanıcı etkinliği raporunu Teams - sütunları seçin.](../../media/user-activity-columns.png)

Dışarı **Aktar bağlantısını** seçerek rapor verilerini bir Excel .csv dosyasına da aktarabilirsiniz. Bu işlem tüm kullanıcıların verilerini dışarı aktarır ve daha fazla çözümleme yapmak için basit sıralama ve filtreleme işlemlerini kullanmanıza olanak tanır. 2000'den az kullanıcınız varsa, raporun kendi içindeki tabloda sıralama ve filtreleme yapabilirsiniz. 2000'den çok kullanıcınız varsa, filtrelemek ve sıralamak için verileri dışarı aktarmanız gerekir. **Ses süresi**, **video süresi** ve **ekran paylaşım süresi** için dışarı aktarılan biçim ISO8601 süre biçimini izler.

**Microsoft Teams kullanıcı etkinliği** raporu son 7 gün, 30 gün, 90 gün veya 180 günlük eğilimler için görüntülenebilir. Ancak raporda belirli bir gün seçerseniz, tablo geçerli tarihten itibaren (raporun oluşturulduğu tarihten değil) 28 güne kadar olan verileri gösterir.

Veri kalitesini sağlamak için son üç güne ilişkin günlük veri doğrulama denetimleri gerçekleştiriyoruz ve algılanan boşlukları dolduracağız. İşlem sırasında geçmiş verilerde farklılıklar fark edebilirsiniz.

|Öğe|Açıklama|
|:-----|:-----|
|**Metrik**|**Tanım**|
|Kullanıcı adı  <br/> |Kullanıcının e-posta adresi. Asıl e-posta adresini görüntüleyebilir veya bu alanın anonim olmasını sağlayabilirsiniz.   <br/> |
|Kiracı adı  <br/> |Kullanıcının ait olduğu iç veya dış kiracının adı.   <br/> <br/> Bir kullanıcı dış kiracıya aitse, ilgili veri ölçümleri (örneğin, posta iletileri, yanıt iletileri vb.) yöneticinin kiracısının paylaşılan kanallarındaki etkileşimlerine göre hesaplanır. Kullanıcı tarafından kendi kiracısında (belirli bir kiracının paylaşılan kanalları dışında) yapılan etkileşimler, belirli bir kiracının yönetici kullanım raporu için dikkate alınmaz.  |
|Paylaşılan kanal kiracı adları   <br/> |Kullanıcının katıldığı paylaşılan kanalların iç veya dış kiracılarının adları.   <br/> |
|Kanal iletileri   <br/> |Kullanıcının belirtilen zaman aralığında bir ekip sohbetinde yayınladığı benzersiz iletilerin sayısı. Buna özgün gönderiler ve yanıtlar dahildir.   <br/> |
|Mesaj   <br/> |Belirtilen zaman aralığındaki tüm kanallardaki posta iletilerinin sayısı. Gönderi, teams sohbetindeki özgün iletidir.<br/> |
|Yanıt   <br/> |Belirtilen süre boyunca tüm kanallarda yanıtlanan ileti sayısı. <br/> |
|Acil iletiler    <br/> |Belirtilen zaman aralığındaki acil ileti sayısı. <br/> |
|Sohbet iletileri   <br/> |Kullanıcının belirtilen zaman aralığında özel bir sohbette yayınladığı benzersiz iletilerin sayısı.  <br/> |
|Toplam toplantı sayısı   <br/> |Kullanıcının belirtilen zaman aralığında katıldığı çevrimiçi toplantı sayısı.  <br/> |
|1:1 aramaları   <br/> | Kullanıcının belirtilen süre boyunca katıldığı 1:1 çağrısı sayısı.  <br/> |
|Son etkinlik tarihi (UTC)  <br/> |Kullanıcının bir Microsoft Teams etkinliğine katıldığı son tarih.<br/> |
|Geçici olarak katılmış toplantılar   <br/> | Bir kullanıcının belirtilen zaman aralığında katıldığı geçici toplantı sayısı.  <br/> |
|Düzenli toplantılar <br/> |Kullanıcının belirtilen süre boyunca düzenlediği geçici toplantı sayısı. <br/>|
|Toplam düzenli toplantı sayısı  <br/> |Kullanıcının belirtilen süre boyunca düzenlediği tek seferlik zamanlanmış, Yinelenen, geçici ve sınıflandırılmamış toplantıların toplamı.  <br/> |
|Toplam katılan toplantı sayısı  <br/> |Bir kullanıcının belirtilen süre boyunca katıldığı tek seferlik zamanlanmış, yinelenen, geçici ve sınıflandırılmamış toplantıların toplamı.  <br/> |
|Tek seferlik zamanlanmış olarak düzenlenmiş toplantılar  <br/> |Kullanıcının belirtilen zaman aralığında düzenlediği tek seferlik zamanlanmış toplantı sayısı.  <br/> |
|Toplantılar düzenlenmiş zamanlanmış yinelenen  <br/> |Kullanıcının belirtilen zaman aralığında düzenlediği yinelenen toplantı sayısı.  <br/> |
|Bir kerelik zamanlanmış zamanlanmış toplantılara katılma  <br/> |Bir kullanıcının belirtilen zaman aralığında katıldığı tek seferlik zamanlanmış toplantıların sayısı.  <br/> |
|Toplantılara katılan zamanlanmış yinelenen toplantılar  <br/> |Kullanıcının belirtilen zaman aralığında katıldığı yinelenen toplantıların sayısı.  <br/> |
|Lisanslıdır  <br/> |Kullanıcı Teams kullanma lisansına sahipse seçilir. <br/>|
|Diğer etkinlikler  <br/>|Kullanıcı etkindir ancak raporda sunulan eylem türlerinden (kanal iletilerini ve sohbet iletilerini gönderme veya yanıtlama, 1:1 aramaları ve toplantılarını zamanlama veya katılma) dışında başka etkinlikler gerçekleştirmiştir. Örnek eylemler, kullanıcı Teams durumunu veya Teams durum iletisini değiştirdiğinde veya kanal iletisi gönderisini açtığında ancak yanıt vermediğinde güncelleştirilir.  <br/>|


## <a name="make-the-user-specific-data-anonymous"></a>Kullanıcıya özgü verileri anonim hale getirme

Teams kullanıcı etkinlik raporundaki verileri anonim hale getirmek için genel yönetici olmanız gerekir. Bu, rapordaki görünen ad, e-posta ve Azure Active Directory Nesne Kimliği gibi tanımlanabilir bilgileri (MD5 karmalarını kullanarak) ve bunların dışarı aktarmasını gizler.

1. Microsoft 365 yönetim merkezi **Ayarlar** **Org Ayarlar** >  gidin ve **Hizmetler** sekmesinin altında **Raporlar'ı** seçin.

2. **Raporlar'ı** ve ardından **Anonim tanımlayıcıları görüntüle'yi** seçin. Bu ayar hem Microsoft 365 yönetim merkezi hem de Teams yönetim merkezindeki kullanım raporlarına uygulanır.

3. **Değişiklikleri kaydet'i** seçin.


## <a name="see-also"></a>Ayrıca bkz.
[cihaz kullanım raporunu Microsoft Teams](../activity-reports/microsoft-teams-device-usage-preview.md)

[kullanım etkinliği raporunu Microsoft Teams](../activity-reports/microsoft-teams-usage-activity.md) 
