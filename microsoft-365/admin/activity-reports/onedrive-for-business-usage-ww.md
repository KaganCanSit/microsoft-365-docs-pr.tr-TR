---
title: Microsoft 365 OneDrive İş raporları
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
description: "Kuruluş genelinde OneDrive İş ve depolama alanı sayısı hakkında bilgi almak için En Fazla Kullanım Raporu'OneDrive İş kullanın. "
ms.openlocfilehash: d3b884f374cf3dde572bd67ad905fc308a1701d1
ms.sourcegitcommit: cdb90f28e59f36966f8751fa8ba352d233317fc1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2022
ms.locfileid: "63400789"
---
# <a name="microsoft-365-reports-in-the-admin-center---onedrive-for-business-usage"></a>Microsoft 365 Merkezinde Rapor Raporları - OneDrive İş kullanımı

Rapor Microsoft 365 panosu, kurum kurum genelindeki ürünlerde etkinliğin genel görünümünü gösterir. Bu pano sayesinde her bir üründeki etkinliklerle ilgili daha ayrıntılı bilgi edinmek için ürün düzeyinde raporları ayrıntılı olarak inceleyebilirsiniz. [Raporlara genel bakış konusuna](activity-reports.md) göz atın.
  
Örneğin panodaki OneDrivekartı, kuruluşunuzdaki tüm hesapları genelinde kullanılan toplam dosya sayısı ve depolama olarak OneDrive İş'dan aldığınız değerin üst düzey görünümünü sağlar. Ardından, etkin OneDrivehesaplarının eğilimlerini anlamak, kullanıcıların kaç dosyayla etkileşimli çalıştığını ve ne kadar depolama kullanıldığı görmek için detaya gidebilirsiniz. Ayrıca, tek tek OneDrive hesaplarının ayrıntıları da verilir.

## <a name="how-do-i-get-to-the-onedrive-usage-report"></a>Kaynak kullanım raporunu OneDrive edinebilirsiniz?

1. Yönetim merkezinde, **Raporlar** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">Kullanımı</a> sayfasına gidin. 
2. Pano giriş sayfasında, pano kartında **Daha fazla** görüntüle OneDrive tıklayın.
  
## <a name="interpret-the-onedrive-usage-report"></a>OneDrive raporunu yorumlama

Kullanım sekmesini seçerek OneDrive raporuna **bakabilirsiniz**.<br/>![Microsoft 365 - Microsoft OneDrive raporu.](../../media/3cdaf2fb-1817-479b-a0e1-2afa228690cf.png)

Raporda **sütun eklemek** veya kaldırmak için Sütunları seç'i seçin.  <br/> ![OneDrive raporu - Sütunları seçin.](../../media/9ee80f25-cfe3-411d-8e31-08f1507d18c1.png)

Ayrıca, Dışarı Aktar bağlantısını seçerek Excel .csv verilerini bir Excel .csv dosyasına **aktarabilirsiniz**. Bu işlem tüm kullanıcıların verilerini dışarı aktarır ve daha fazla çözümleme yapmak için basit sıralama ve filtreleme işlemlerini kullanmanıza olanak tanır. 2000'den az kullanıcınız varsa, raporun kendi içindeki tabloda sıralama ve filtreleme yapabilirsiniz. 2000'den çok kullanıcınız varsa, filtrelemek ve sıralamak için verileri dışarı aktarmanız gerekir. 

En **OneDrive İş raporu**, son 7 gün, 30 gün, 90 gün veya 180 günlük eğilimler için 2013'te 2013'ü 2013'e kadar yıllar olarak 2013'e kadar görüntüleyebilirsiniz. Ancak rapordaki belirli bir günü seçersiniz, tablo geçerli tarihten (raporun oluşturulma tarihine değil) itibaren 28 güne kadar olan verileri gösterir.
  
|Öğe|Açıklama|
|:-----|:-----|
|**Metrik**|**Tanım**|
|URL  <br/> |Kullanıcının posta adresinin web OneDrive. <br/> |
|Silindi  <br/> |TSK'nin silme OneDrive. Hesapların silinmiş olarak işaretlenmesi en az 7 gün sürer.  <br/> |
|Sahip  <br/> |Etki alanı yöneticisinin birincil yöneticisinin kullanıcı OneDrive.   <br/> |
|Sahip asıl adı  <br/> |E-posta adresi, e-posta OneDrive. <br/> |
|Son etkinlik tarihi (UTC)  <br/> | Dosya etkinlik gerçekleştirilen son tarih OneDrive. OneDrive değerinde hiç dosya etkinliği yoksa değer boş olur.  <br/> |
|Dosyalar  <br/> |Dosya sayısı OneDrive. <br/>|
|Etkin dosyalar  <br/> | Dönem içindeki etkin dosyaların sayısı.<br/> NOT: Rapor için belirtilen dönem içinde dosya kaldırıldısa, raporda gösterilen etkin dosyaların sayısı dosya sayısı, rapor'daki dosyaların mevcut sayısından OneDrive. >  Silinmiş kullanıcılar 180 gün süreyle raporlarda gösterilmeye devam eder.  <br/> |
|Depolama kullanılan alan (MB)  <br/> |MB olarak kullanan OneDrive depolama miktarı. |
|||
   
> [!NOTE]
> Rapor yalnızca geçerli bir lisansa sahip OneDrive İş içerir.
