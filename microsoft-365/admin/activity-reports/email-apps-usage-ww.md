---
title: E-posta uygulamaları kullanım raporlarını Microsoft 365 yönetim merkezi
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
ms.assetid: c2ce12a2-934f-4dd4-ba65-49b02be4703d
description: Exchange Online bağlanan e-posta uygulamalarının sayısını ve Outlook kullanıcılarının hangi sürümünü kullandığını öğrenmek için e-posta uygulamaları kullanım raporunu nasıl alacağınızı öğrenin.
ms.openlocfilehash: 8a9a416e533bd1e8b30f385ec8b15db182e593c6
ms.sourcegitcommit: da6b3cb3b2ccfcdcd5091efce8290b6c486547db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/18/2022
ms.locfileid: "65467700"
---
# <a name="microsoft-365-reports-in-the-admin-center---email-apps-usage"></a>Yönetim merkezinde Microsoft 365 Raporları - E-posta uygulamaları kullanımı

Microsoft 365 Raporları panosu, kuruluşunuzdaki ürünler genelindeki etkinliğe genel bakışı gösterir. Bu pano sayesinde her bir üründeki etkinliklerle ilgili daha ayrıntılı bilgi edinmek için ürün düzeyinde raporları ayrıntılı olarak inceleyebilirsiniz. [Raporlara genel bakış konusuna](activity-reports.md) göz atın. E-posta uygulamaları kullanım raporunda, Exchange Online bağlanan e-posta uygulamalarının sayısını görebilirsiniz. Ayrıca kullanıcıların kullandığı Outlook uygulamaların sürüm bilgilerini de görebilirsiniz. Bu bilgiler, desteklenmeyen sürümleri kullananları izleyerek desteklenen Outlook sürümlerini yüklemenizi sağlar.
  
## <a name="how-to-get-to-the-email-apps-report"></a>E-posta uygulamaları raporuna erişme

1. Yönetim merkezinde, **Raporlar** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">Kullanımı</a> sayfasına gidin.
2. **E-posta etkinliği** altında **Daha Fazla Görüntüle'yi** seçin. 
3. **E-posta etkinliği** açılan listesinde **e-posta uygulamaları kullanımı** **Exchange** \> seçin.
  
## <a name="interpret-the-email-apps-report"></a>E-posta uygulamaları raporunu yorumlama

**Kullanıcılar** ve **İstemciler** grafiklerine bakarak e-posta uygulamaları etkinliğine ilişkin bir görünüm elde edebilirsiniz. 
  
![Kullanılan e-posta istemcileri.](../../media/d78af7db-2b41-4d37-8b6e-bc7e47edd1dd.png)
  
|Öğe|Açıklama|
|:-----|:-----|
|1.  <br/> |**E-posta uygulamaları kullanım** raporu son 7 gün, 30 gün, 90 gün veya 180 günlük eğilimler için görüntülenebilir. Ancak raporda belirli bir gün seçerseniz, tablo geçerli tarihten itibaren (raporun oluşturulduğu tarihten değil) 28 güne kadar olan verileri gösterir.  <br/> |
|2.  <br/> |Her rapordaki veriler genellikle son 24-48 saati kapsar.  <br/> |
|3.  <br/> |**Kullanıcılar** görünümü, herhangi bir e-posta uygulamasını kullanarak Exchange Online'a bağlanan benzersiz kullanıcıların sayısını gösterir.  <br/> |
|4.  <br/> |**Uygulamalar** görünümü, seçilen süre içinde uygulamaya göre benzersiz kullanıcı sayısını gösterir.  <br/> |
|5.  <br/> |**Sürümler** görünümü, Windows'daki her Outlook sürümü için benzersiz kullanıcı sayısını gösterir.  <br/> |
|6.  <br/> | **Kullanıcılar** grafiğinde Y ekseni, rapor dönemindeki herhangi bir günde bir uygulamaya bağlanan benzersiz kullanıcıların toplam sayısını gösterir.  <br/>  **Kullanıcılar** grafiğinde X ekseni, seçili rapor döneminde uygulamayı kullanan benzersiz kullanıcıların sayısını gösterir.  <br/>  **Uygulamalar** grafiğinde Y ekseni, rapor dönemi içerisinde belirli bir uygulamayı kullanan benzersiz kullanıcıların toplam sayısını gösterir.  <br/>  **Uygulamalar** grafiğinde X ekseni, kuruluşunuzdaki uygulamaların listesini gösterir.  <br/>  **Sürümler** grafiğinde Y ekseni, Outlook masaüstünün belirli bir sürümünü kullanan benzersiz kullanıcıların toplam sayısını gösterir. Rapor Outlook sürüm numarasını çözümleyemiyorsa miktar **Belirsiz** olarak gösterilir.  <br/>  **Sürümler** grafiğinde X ekseni, kuruluşunuzdaki uygulamaların listesini gösterir.  <br/> |
|7.  <br/> |Göstergede bir öğe seçerek grafikte gördüğünüz seriyi filtreleyebilirsiniz.  <br/> |
|8.  <br/> | Tüm öğeleri ekleyene kadar aşağıdaki listenin sütunlarında bu öğeleri göremeyebilirsiniz.<br/> **Kullanıcı adı** , e-posta uygulamasının sahibinin adıdır.  <br/> **Son etkinlik tarihi** , kullanıcının e-posta iletisini okuduğu veya gönderdiği en son tarihtir.  <br/> **Mac Mail**, **Mac Outlook** ve **Outlook**, **Outlook Mobile** ve **Web üzerinde Outlook**, kuruluşunuzda olabilecek e-posta uygulamalarından bazılarıdır.  <br/>  Kuruluşunuzun ilkeleri nedeniyle kişisel kullanıcı bilgilerinin bulunduğu raporları görüntüleyemiyorsanız bu raporların gizlilik ayarını değiştirebilirsiniz. Microsoft 365 yönetim merkezi Etkinlik Raporları'nın **kullanıcı düzeyi ayrıntılarını Nasıl yaparım?** [gizlensin mi](activity-reports.md)? bölümüne göz atın.  <br/> |
|9.  <br/> |Rapora sütun eklemek veya rapordan sütun kaldırmak için Sütunları **seç'i** seçin.  <br/> ![E-posta uygulamaları kullanım raporu - sütunları seçin.](../../media/041bd6ff-27e8-409d-9608-282edcfa2316.png)|
|10.  <br/> |Dışarı **Aktar bağlantısını** seçerek rapor verilerini bir Excel .csv dosyasına da aktarabilirsiniz. Bu işlem tüm kullanıcıların verilerini dışarı aktarır ve daha fazla çözümleme yapmak için basit sıralama ve filtreleme işlemlerini kullanmanıza olanak tanır. 2000'den az kullanıcınız varsa, raporun kendi içindeki tabloda sıralama ve filtreleme yapabilirsiniz. 2000'den çok kullanıcınız varsa, filtrelemek ve sıralamak için verileri dışarı aktarmanız gerekir.  <br/> |
|||
   
