---
title: Microsoft 365 Merkezinde Raporlar - E-posta uygulamaları kullanımı
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
description: E-posta uygulamaları kullanım raporunu, kullanıcıların Exchange Online ve Outlook e-posta uygulamaları hakkında bilgi edinmek için nasıl edinebilirsiniz.
ms.openlocfilehash: 601258d721f817438f0bd6a08d98d73aa22b7afb
ms.sourcegitcommit: bf3965b46487f6f8cf900dd9a3af8b213a405989
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/02/2021
ms.locfileid: "62989913"
---
# <a name="microsoft-365-reports-in-the-admin-center---email-apps-usage"></a>Microsoft 365 Merkezinde Raporlar - E-posta uygulamaları kullanımı

Rapor Microsoft 365 panosu, kurum kurum genelindeki ürünlerde etkinliğin genel görünümünü gösterir. Bu pano sayesinde her bir üründeki etkinliklerle ilgili daha ayrıntılı bilgi edinmek için ürün düzeyinde raporları ayrıntılı olarak inceleyebilirsiniz. [Raporlara genel bakış konusuna](activity-reports.md) göz atın. E-posta uygulamaları kullanım raporunda, bir e-posta uygulamasına kaç e-posta uygulaması Exchange Online. Ayrıca, kullanıcıların Outlook uygulamalarının desteklenen sürümlerini yüklemek için desteklenmeyen sürümleri kullananlarla izlemesine olanak sağlayan sürüm bilgilerini de Outlook.
  
## <a name="how-to-get-to-the-email-apps-report"></a>E-posta uygulamaları raporuna nasıl gönderilir?

1. Yönetim merkezinde, **Raporlar** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">Kullanımı</a> sayfasına gidin.
2. **E-posta etkinliği'nin altında** Daha **Fazlasını Görüntüle'yi seçin**. 
3. **E-posta etkinliği açılan** listesinde, E-posta uygulamaları **Exchange'ı** \> seçin.
  
## <a name="interpret-the-email-apps-report"></a>E-posta uygulamaları raporunu yorumlama

Kullanıcılar ve İstemciler grafiklerine bakarak e-posta uygulamaları **etkinliğinin bir görünümünü** elde edin. 
  
![Kullanılan e-posta istemcileri.](../../media/d78af7db-2b41-4d37-8b6e-bc7e47edd1dd.png)
  
|Öğe|Açıklama|
|:-----|:-----|
|1.  <br/> |**E-posta** uygulamaları kullanım raporu, son 7 gün, 30 gün, 90 gün veya 180 günlük eğilimler için görüntülenebilirsiniz. Ancak rapordaki belirli bir günü seçersiniz, tablo geçerli tarihten (raporun oluşturulma tarihine değil) itibaren 28 güne kadar olan verileri gösterir.  <br/> |
|2.  <br/> |Her raporda yer alan veriler genellikle son 24 - 48 saati kapsar.  <br/> |
|3.  <br/> |**Kullanıcılar** görünümü, herhangi bir e-posta uygulamasını kullanarak Exchange Online'a bağlanan benzersiz kullanıcıların sayısını gösterir.  <br/> |
|4.  <br/> |**Uygulamalar** görünümü, seçilen süre içinde uygulamaya göre benzersiz kullanıcı sayısını gösterir.  <br/> |
|5.  <br/> |**Sürümler** görünümü, 2013'te her sürüm için Outlook kullanıcı Windows.  <br/> |
|6.  <br/> | **Kullanıcılar** grafiğinde Y ekseni, rapor dönemindeki herhangi bir günde bir uygulamaya bağlanan benzersiz kullanıcıların toplam sayısını gösterir.  <br/>  **Kullanıcılar** grafiğinde X ekseni, seçili rapor döneminde uygulamayı kullanan benzersiz kullanıcıların sayısını gösterir.  <br/>  **Uygulamalar** grafiğinde Y ekseni, rapor dönemi içerisinde belirli bir uygulamayı kullanan benzersiz kullanıcıların toplam sayısını gösterir.  <br/>  **Uygulamalar** grafiğinde X ekseni, kuruluşunuzdaki uygulamaların listesini gösterir.  <br/>  **Sürümler** grafiğinde Y ekseni, Outlook masaüstünün belirli bir sürümünü kullanan benzersiz kullanıcıların toplam sayısını gösterir. Rapor, yeni raporun sürüm numarasını çözümleye Outlook, bu değer Belirsiz **olarak gösterir**.  <br/>  **Sürümler** grafiğinde X ekseni, kuruluşunuzdaki uygulamaların listesini gösterir.  <br/> |
|7.  <br/> |Göstergede bir öğe seçerek grafikte gördüğünüz seriyi filtrenin ekleyebilirsiniz.  <br/> |
|8.  <br/> | Tüm öğeleri ekleyene kadar aşağıdaki listenin sütunlarında bu öğeleri göremeyebilirsiniz.<br/> **Kullanıcı** adı, e-posta uygulamasının sahibinin adıdır.  <br/> **Son etkinlik tarihi,** kullanıcının en son e-posta iletisi okuması veya göndermesi tarihidir.  <br/> **Mac Mail**, **Mac Outlook** ve **Outlook**, **Outlook Mobile** ve **Web üzerinde Outlook**, kuruluşunuzda olabilecek e-posta uygulamalarından bazılarıdır.  <br/>  Kuruluşunuzun ilkeleri nedeniyle kişisel kullanıcı bilgilerinin bulunduğu raporları görüntüleyemiyorsanız bu raporların gizlilik ayarını değiştirebilirsiniz. Aşağıdaki çalışma **sayfalarındaki Etkinlik Raporları'nın** kullanıcı düzeyi ayrıntılarını [nasıl gizleyim? Microsoft 365 yönetim merkezi](activity-reports.md).  <br/> |
|9.  <br/> |Raporda **sütun eklemek** veya kaldırmak için Sütunları seç'i seçin.  <br/> ![E-posta uygulamaları kullanım raporu - Sütunları seçin.](../../media/041bd6ff-27e8-409d-9608-282edcfa2316.png)|
|10.  <br/> |Ayrıca, Dışarı Aktar bağlantısını seçerek rapor Excel .csv bir çalışma dosyasına da **aktarabilirsiniz**. Bu işlem tüm kullanıcıların verilerini dışarı aktarır ve daha fazla çözümleme yapmak için basit sıralama ve filtreleme işlemlerini kullanmanıza olanak tanır. 2000'den az kullanıcınız varsa, raporun kendi içindeki tabloda sıralama ve filtreleme yapabilirsiniz. 2000'den çok kullanıcınız varsa, filtrelemek ve sıralamak için verileri dışarı aktarmanız gerekir.  <br/> |
|||
   
