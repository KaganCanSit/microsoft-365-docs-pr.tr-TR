---
title: Microsoft 365 yönetim merkezi-posta etkinliği raporlarını gönderme
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
description: Bir e-posta etkinlik raporunu, rapor Microsoft 365 Raporlar panosu kullanarak nasıl Microsoft 365 yönetim merkezi.
ms.openlocfilehash: e7441bc24661f279a43a655d17ef23047ed48a43
ms.sourcegitcommit: cdb90f28e59f36966f8751fa8ba352d233317fc1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2022
ms.locfileid: "63400958"
---
# <a name="microsoft-365-reports-in-the-admin-center---email-activity"></a>Microsoft 365 Merkezinde Raporlar - E-posta etkinliği

Rapor Microsoft 365 panosu, kurum kurum genelindeki ürünlerde etkinliğin genel görünümünü gösterir. Bu pano sayesinde her bir üründeki etkinliklerle ilgili daha ayrıntılı bilgi edinmek için ürün düzeyinde raporları ayrıntılı olarak inceleyebilirsiniz. [Raporlara genel bakış konusuna](activity-reports.md) göz atın.
  
Örneğin, Raporlar sayfasında kuruluşunuzun içindeki e-posta trafiğinin üst düzey bir görünümünü elde edebilir ve ardından, kuruluşunuzdaki e-posta etkinliğinin eğilimlerini ve tek tek kullanıcılar düzeyindeki ayrıntılarını anlamak için E-posta etkinliği widget'inde detaya gidebilirsiniz.

## <a name="how-to-get-to-the-email-activity-report"></a>E-posta etkinlik raporuna ulaşma

1. Yönetim merkezinde, **Raporlar** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">Kullanımı</a> sayfasına gidin.
2. **E-posta etkinliği'nin altında** Daha **Fazlasını Görüntüle'yi seçin**. 
3. **E-posta etkinliği açılan** listesinde E-posta etkinliğini **Exchange** \> **seçin**.
  
## <a name="interpret-the-email-activity-report"></a>E-posta etkinlik raporunu yorumlama

Kullanıcınızın e-posta etkinliğini görmek için, **Etkinlik** ve **Kullanıcılar** grafiklerine bakabilirsiniz. 
  
![E-posta etkinliği raporu.](../../media/5eb1d9e9-8106-4843-acb7-c0238c0da816.png)
  
|Öğe|Açıklama|
|:-----|:-----|
|1.  <br/> |**E-posta etkinlik** raporu son 7 gün, 30 gün, 90 gün veya 180 günlük eğilimler için görüntülenebilir. Ancak rapordaki belirli bir günü seçersiniz, tablo geçerli tarihten (raporun oluşturulma tarihine değil) itibaren 28 güne kadar olan verileri gösterir.  <br/> |
|2.  <br/> |Her raporda yer alan veriler genellikle son 24 - 48 saati kapsar.  <br/> |
|3.  <br/> |**Etkinlik** grafiği, kuruluşunuzda devam eden e-posta etkinliğinin miktarına ilişkin eğilimi anlamasına olanak tanır. E-posta gönderme, e-posta okuma, alınan e-posta, toplantı oluşturma veya toplantı etkileşimleri gibi etkinliklerin bölüşüştüşterlerini anlıyoruz.  <br/> |
|4.  <br/> |**Kullanıcı** grafiği, e-posta etkinliklerini gerçekleştiren benzersiz kullanıcı sayısına ilişkin eğilimi anlamanıza olanak tanır. E-posta gönderme, e-posta okuma, e-posta alma, toplantı oluşturma veya toplantı etkileşimleri gerçekleştirme eğilimine bakabilirsiniz.  <br/> |
|5.  <br/> | Etkinlik **grafiğinde** , Y ekseni gönderilen e-posta türü, alınan e-posta, okunan e-posta, toplantı oluşturma ve etkileşim toplantıyı içeren etkinliğin sayısıdır.  <br/>  Kullanıcılar etkinlik **grafiğinde** , Y ekseni gönderilen e-posta, alınan e-posta, alınan e-posta, okunan e-posta, toplantı oluşturma veya etkileşim toplantıyı içeren etkinlik gerçekleştiren kullanıcı sayısıdır.  <br/>  Her iki grafikte bulunan X ekseni, söz konusu rapora ait seçilen tarih aralığıdır.  <br/> |
|6.  <br/> |Göstergede bir öğe seçerek grafikte gördüğünüz seriyi filtrenin ekleyebilirsiniz.  <br/> |
|7.  <br/> | Tabloda, kullanıcı düzeyine göre e-posta etkinliklerinin dökümü gösterilir. Bu, kendisine Exchange ürünü atanmış olan kullanıcıları ve onların e-posta etkinliklerini gösterir. <br/> <br/> **Kullanıcı adı**, kullanıcının e-posta adresidir.  <br/> **Görünen ad** , kullanıcıya tam addır.  <br/> **Silinmiş**, geçerli durumu silinmiş olan ancak raporun raporlama döneminin bir bölümünde etkin olan kullanıcıya karşılık gelir.  <br/> **Silinme tarihi**, kullanıcının silindiği tarihtir.  <br/> **Son etkinlik tarihi**, kullanıcının e-posta okuma veya gönderme etkinliği gerçekleştirdiği en son tarihe karşılık gelir.  <br/> **Gönderme eylemi**, kullanıcı için kaydedilen e-posta gönderme eyleminin sayısını gösterir.  <br/> **Alma eylemi**, kullanıcı için kaydedilen e-posta alma eyleminin sayısını gösterir.  <br/> **Okuma eylemi**, kullanıcı için kaydedilen e-posta okuma eyleminin sayısını gösterir.  <br/> **Toplantı oluşturma eylemleri** , kullanıcı için kaydedilen toplantı isteği gönderme eyleminin sayısıdır.  <br/> **Toplantı etkileşim eylemleri,** kullanıcı için kaydedilen toplantı isteğinin kabul etme, belirsiz, reddetme veya iptal eyleminin sayısını ifade eder.  <br/> **Atanan ürün** , bu kullanıcıya atanan ürünlerdir.  <br/>  Kuruluşunuzun ilkeleri nedeniyle kişisel kullanıcı bilgilerinin bulunduğu raporları görüntüleyemiyorsanız bu raporların gizlilik ayarını değiştirebilirsiniz. Aşağıdaki çalışma **sayfalarındaki Etkinlik Raporları'nın** kullanıcı düzeyi ayrıntılarını [nasıl gizleyim? Microsoft 365 yönetim merkezi](activity-reports.md).  <br/> |
|8.  <br/> |Raporda **sütun eklemek** veya kaldırmak için Sütunları seç'i seçin.  <br/> ![E-posta etkinliği raporu - Sütunları seçin.](../../media/80ffa0ad-61c5-4a6f-8a1d-5f6730ff7da9.png)|
|9.  <br/> |Ayrıca, Dışarı Aktar bağlantısını seçerek rapor Excel .csv bir çalışma dosyasına da **aktarabilirsiniz**. Bu işlem tüm kullanıcıların verilerini dışarı aktarır ve daha fazla çözümleme yapmak için basit sıralama ve filtreleme işlemlerini kullanmanıza olanak tanır. 2000'den az kullanıcınız varsa, raporun kendi içindeki tabloda sıralama ve filtreleme yapabilirsiniz. 2000'den çok kullanıcınız varsa, filtrelemek ve sıralamak için verileri dışarı aktarmanız gerekir.  <br/> |
|||
   
> [!NOTE]
> E-posta etkinliği raporu yalnızca lisansı olan kullanıcılarla ilişkilendirilmiş posta kutuları için kullanılabilir.
