---
title: E-posta etkinlik raporlarını Microsoft 365 yönetim merkezi
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
- MET150
- MOE150
- GEA150
ms.assetid: 1cbe2c00-ca65-4fb9-9663-1bbfa58ebe44
description: Microsoft 365 yönetim merkezi Microsoft 365 Raporlar panosunu kullanarak e-posta etkinlik raporu almayı ve kullanıcı e-posta eğilimlerini anlama hakkında bilgi edinin.
ms.openlocfilehash: b84d8c3e6e85ab64b1ec70379e7c016374f28e78
ms.sourcegitcommit: da6b3cb3b2ccfcdcd5091efce8290b6c486547db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/18/2022
ms.locfileid: "65467690"
---
# <a name="microsoft-365-reports-in-the-admin-center---email-activity"></a>Yönetim merkezinde raporları Microsoft 365 - E-posta etkinliği

Microsoft 365 Raporları panosu, kuruluşunuzdaki ürünler genelindeki etkinliğe genel bakışı gösterir. Bu pano sayesinde her bir üründeki etkinliklerle ilgili daha ayrıntılı bilgi edinmek için ürün düzeyinde raporları ayrıntılı olarak inceleyebilirsiniz. [Raporlara genel bakış konusuna](activity-reports.md) göz atın.
  
Örneğin, Raporlar sayfasında kuruluşunuzun içindeki e-posta trafiğinin üst düzey bir görünümünü elde edebilir ve ardından, kuruluşunuzdaki e-posta etkinliğinin eğilimlerini ve tek tek kullanıcılar düzeyindeki ayrıntılarını anlamak için E-posta etkinliği widget'inde detaya gidebilirsiniz.

## <a name="how-to-get-to-the-email-activity-report"></a>E-posta etkinlik raporuna ulaşma

1. Yönetim merkezinde, **Raporlar** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">Kullanımı</a> sayfasına gidin.
2. **E-posta etkinliği** altında **Daha Fazla Görüntüle'yi** seçin. 
3. **E-posta etkinliği** açılan listesinde **e-posta etkinliğini** **Exchange** \> seçin.
  
## <a name="interpret-the-email-activity-report"></a>E-posta etkinlik raporunu yorumlama

Kullanıcınızın e-posta etkinliğini görmek için, **Etkinlik** ve **Kullanıcılar** grafiklerine bakabilirsiniz. 
  
![E-posta etkinlik raporu.](../../media/5eb1d9e9-8106-4843-acb7-c0238c0da816.png)
  
|Öğe|Açıklama|
|:-----|:-----|
|1.  <br/> |**E-posta etkinlik** raporu son 7 gün, 30 gün, 90 gün veya 180 günlük eğilimler için görüntülenebilir. Ancak raporda belirli bir gün seçerseniz, tablo geçerli tarihten itibaren (raporun oluşturulduğu tarihten değil) 28 güne kadar olan verileri gösterir.  <br/> |
|2.  <br/> |Her rapordaki veriler genellikle son 24-48 saati kapsar.  <br/> |
|3.  <br/> |**Etkinlik** grafiği, kuruluşunuzda devam eden e-posta etkinliğinin miktarına ilişkin eğilimi anlamasına olanak tanır. E-posta gönderme, e-posta okuma, alınan e-posta, toplantı oluşturma veya toplantı etkileşim etkinliklerinin bölünmesini anlayabilirsiniz.  <br/> |
|4.  <br/> |**Kullanıcı** grafiği, e-posta etkinliklerini gerçekleştiren benzersiz kullanıcı sayısına ilişkin eğilimi anlamanıza olanak tanır. E-posta gönderme, e-posta okuma, e-posta alma, toplantı oluşturma veya toplantı etkileşim etkinlikleri gerçekleştiren kullanıcıların eğilimine bakabilirsiniz.  <br/> |
|5.  <br/> | **Etkinlik** grafiğinde, Y ekseni gönderilen, alınan e-posta, okunan e-posta, oluşturulan toplantı ve etkileşimde bulunan toplantı türündeki etkinlik sayısıdır.  <br/>  **Kullanıcılar** etkinlik grafiğinde, Y ekseni, kullanıcının gönderilen, alınan e-posta, e-posta okuma, toplantı oluşturma veya etkileşimde bulunan toplantı türündeki etkinliğidir.  <br/>  Her iki grafikte bulunan X ekseni, söz konusu rapora ait seçilen tarih aralığıdır.  <br/> |
|6.  <br/> |Göstergede bir öğe seçerek grafikte gördüğünüz seriyi filtreleyebilirsiniz.  <br/> |
|7.  <br/> | Tabloda, kullanıcı düzeyine göre e-posta etkinliklerinin dökümü gösterilir. Bu, kendisine Exchange ürünü atanmış olan kullanıcıları ve onların e-posta etkinliklerini gösterir. <br/> <br/> **Kullanıcı adı**, kullanıcının e-posta adresidir.  <br/> **Görünen ad** , kullanıcıysa tam addır.  <br/> **Silinmiş**, geçerli durumu silinmiş olan ancak raporun raporlama döneminin bir bölümünde etkin olan kullanıcıya karşılık gelir.  <br/> **Silinme tarihi**, kullanıcının silindiği tarihtir.  <br/> **Son etkinlik tarihi**, kullanıcının e-posta okuma veya gönderme etkinliği gerçekleştirdiği en son tarihe karşılık gelir.  <br/> **Gönderme eylemi**, kullanıcı için kaydedilen e-posta gönderme eyleminin sayısını gösterir.  <br/> **Alma eylemi**, kullanıcı için kaydedilen e-posta alma eyleminin sayısını gösterir.  <br/> **Okuma eylemi**, kullanıcı için kaydedilen e-posta okuma eyleminin sayısını gösterir.  <br/> **Toplantı tarafından oluşturulan eylemler** , kullanıcı için toplantı isteği gönderme eyleminin kaç kez kaydedildiğini gösterir.  <br/> **Toplantıyla etkileşimli eylemler** , bir toplantı isteğinin kullanıcı için kabul etme, belirsiz, reddetme veya iptal eyleminin kaç kez kaydedildiğini gösterir.  <br/> **Atanan ürün** , bu kullanıcıya atanan ürünlerdir.  <br/>  Kuruluşunuzun ilkeleri nedeniyle kişisel kullanıcı bilgilerinin bulunduğu raporları görüntüleyemiyorsanız bu raporların gizlilik ayarını değiştirebilirsiniz. Microsoft 365 yönetim merkezi Etkinlik Raporları'nın **kullanıcı düzeyi ayrıntılarını Nasıl yaparım?** [gizlensin mi](activity-reports.md)? bölümüne göz atın.  <br/> |
|8.  <br/> |Rapora sütun eklemek veya rapordan sütun kaldırmak için Sütunları **seç'i** seçin.  <br/> ![E-posta etkinliği raporu - sütunları seçin.](../../media/80ffa0ad-61c5-4a6f-8a1d-5f6730ff7da9.png)|
|9.  <br/> |Dışarı **Aktar bağlantısını** seçerek rapor verilerini bir Excel .csv dosyasına da aktarabilirsiniz. Bu işlem tüm kullanıcıların verilerini dışarı aktarır ve daha fazla çözümleme yapmak için basit sıralama ve filtreleme işlemlerini kullanmanıza olanak tanır. 2000'den az kullanıcınız varsa, raporun kendi içindeki tabloda sıralama ve filtreleme yapabilirsiniz. 2000'den çok kullanıcınız varsa, filtrelemek ve sıralamak için verileri dışarı aktarmanız gerekir.  <br/> |
|||
   
> [!NOTE]
> E-posta etkinlik raporu yalnızca lisansları olan kullanıcılarla ilişkilendirilmiş posta kutuları için kullanılabilir.
