---
title: kullanım raporlarını Microsoft 365 OneDrive Entreprise
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
ms.custom:
- AdminSurgePortfolio
- AdminTemplateSet
search.appverid:
- BCS160
- MST160
- MET150
- MOE150
description: "Kuruluşunuzda kullanılan toplam dosya ve depolama alanı sayısı hakkında bilgi edinmek için OneDrive Entreprise Kullanım Raporu'na ulaşın. "
ms.openlocfilehash: f212a29a5fb41aae9ecb0daeae0638d7af1e5dd1
ms.sourcegitcommit: ac0ae5c2888e2b323e36bad041a4abef196c9c96
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/12/2022
ms.locfileid: "64781593"
---
# <a name="microsoft-365-reports-in-the-admin-center---onedrive-for-business-usage"></a>Yönetim merkezinde raporları Microsoft 365 - kullanımı OneDrive Entreprise

Microsoft 365 Raporları panosu, kuruluşunuzdaki ürünler genelindeki etkinliğe genel bakışı gösterir. Bu pano sayesinde her bir üründeki etkinliklerle ilgili daha ayrıntılı bilgi edinmek için ürün düzeyinde raporları ayrıntılı olarak inceleyebilirsiniz. [Raporlara genel bakış konusuna](activity-reports.md) göz atın.
  
Örneğin panodaki OneDrivekartı, kuruluşunuzdaki tüm hesapları genelinde kullanılan toplam dosya sayısı ve depolama olarak OneDrive İş'dan aldığınız değerin üst düzey görünümünü sağlar. Ardından, etkin OneDrivehesaplarının eğilimlerini anlamak, kullanıcıların kaç dosyayla etkileşimli çalıştığını ve ne kadar depolama kullanıldığı görmek için detaya gidebilirsiniz. Ayrıca, tek tek OneDrive hesaplarının ayrıntıları da verilir.

## <a name="how-do-i-get-to-the-onedrive-usage-report"></a>OneDrive kullanım raporuna Nasıl yaparım? ulaşabilirsiniz?

1. Yönetim merkezinde, **Raporlar** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">Kullanımı</a> sayfasına gidin. 
2. Pano giriş sayfasında, OneDrive kartındaki **Daha fazla görüntüle** düğmesine tıklayın.
  
## <a name="interpret-the-onedrive-usage-report"></a>OneDrive raporunu yorumlama

Kullanım sekmesini seçerek OneDrive raporundaki **kullanımı** görüntüleyebilirsiniz.<br/>![Microsoft 365 raporları - kullanım raporu Microsoft OneDrive.](../../media/3cdaf2fb-1817-479b-a0e1-2afa228690cf.png)

Rapora sütun eklemek veya rapordan sütun kaldırmak için Sütunları **seç'i** seçin.  <br/> ![kullanım raporunu OneDrive - sütunları seçin.](../../media/9ee80f25-cfe3-411d-8e31-08f1507d18c1.png)

Dışarı **Aktar bağlantısını** seçerek rapor verilerini bir Excel .csv dosyasına da aktarabilirsiniz. Bu işlem tüm kullanıcıların verilerini dışarı aktarır ve daha fazla çözümleme yapmak için basit sıralama ve filtreleme işlemlerini kullanmanıza olanak tanır. 2000'den az kullanıcınız varsa, raporun kendi içindeki tabloda sıralama ve filtreleme yapabilirsiniz. 2000'den çok kullanıcınız varsa, filtrelemek ve sıralamak için verileri dışarı aktarmanız gerekir. 

**OneDrive Entreprise kullanım** raporu son 7 gün, 30 gün, 90 gün veya 180 günlük eğilimler için görüntülenebilir. Ancak raporda belirli bir gün seçerseniz, tablo geçerli tarihten itibaren (raporun oluşturulduğu tarihten değil) 28 güne kadar olan verileri gösterir.
  
|Öğe|Açıklama|
|:-----|:-----|
|**Metrik**|**Tanım**|
|URL  <br/> |Kullanıcının OneDrive web adresi. <br/> |
|Silindi  <br/> |OneDrive silme durumu. Hesapların silinmiş olarak işaretlenmesi en az 7 gün sürer.  <br/> |
|Sahibi  <br/> |OneDrive birincil yöneticisinin kullanıcı adı.   <br/> |
|Sahip asıl adı  <br/> |OneDrive sahibinin e-posta adresi. <br/> |
|Son etkinlik tarihi (UTC)  <br/> | OneDrive bir dosya etkinliğinin en son gerçekleştirildiği tarih. OneDrive değerinde hiç dosya etkinliği yoksa değer boş olur.  <br/> |
|Dosyaları  <br/> |OneDrive dosya sayısı. <br/>|
|Etkin dosyalar  <br/> | Zaman aralığındaki etkin dosyaların sayısı.<br/> NOT: Rapor için belirtilen süre boyunca dosyalar kaldırıldıysa, raporda gösterilen etkin dosyaların sayısı OneDrive geçerli dosya sayısından daha fazla olabilir. >  Silinmiş kullanıcılar 180 gün süreyle raporlarda gösterilmeye devam eder.  <br/> |
|kullanılan Depolama (MB)  <br/> |OneDrive MB cinsinden kullandığı depolama alanı miktarı. |
|||
   
> [!NOTE]
> Rapor yalnızca geçerli bir OneDrive Entreprise lisansına sahip kullanıcıları içerir.
