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
ms.custom: AdminSurgePortfolio
search.appverid:
- BCS160
- MST160
- MET150
- MOE150
description: Organizasyonun OneDrive bir kullanım raporuna sahip olur ve her kullanıcının OneDrive, paylaşılan dosya sayısını ve depolama kullanımını bilirsiniz.
ms.openlocfilehash: 52e925774ba2315f582f1b5ba50a4a75fe221c10
ms.sourcegitcommit: cdb90f28e59f36966f8751fa8ba352d233317fc1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2022
ms.locfileid: "63400803"
---
# <a name="microsoft-365-reports-in-the-admin-center---onedrive-for-business-activity"></a>Microsoft 365 Merkezinde Rapor Raporları - OneDrive İş raporları

Rapor Microsoft 365 panosu, kurum kurum genelindeki ürünlerde etkinliğin genel görünümünü gösterir. Bu pano sayesinde ürünlerin her birindeki etkinliklerle ilgili daha ayrıntılı bilgi edinmek için ürün düzeyinde raporları ayrıntılı olarak inceleyebilirsiniz. [Raporlara genel bakış konusuna](activity-reports.md) göz atın.
  
Örneğin, OneDrive kullanma lisansı olan her kullanıcının etkinliğini anlamak için OneDrive'da dosyalarla etkileşimlerine bakabilirsiniz. Ayrıca, paylaşılan dosya sayısına bakarak işbirliği düzeyini anlamanıza da yardımcı olabilir.

## <a name="how-do-i-get-to-the-onedrive-activity-report"></a>OneDrive Etkinlik raporuna nasıl ulaşabilirim?

1. Yönetim merkezinde, **Raporlar** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">Kullanımı</a> sayfasına gidin. 
2. Pano giriş sayfasında, pano kartında **Daha fazla** görüntüle OneDrive tıklayın.
  
## <a name="interpret-the-onedrive-for-business-activity-report"></a>OneDrive İş etkinlik raporunu yorumlama

Etkinlik sekmesini seçerek çalışma OneDrive etkinlikleri **görüntüleyebilirsiniz**.<br/>![Microsoft 365- Microsoft OneDrive raporu.](../../media/c89df0b0-2611-4acf-9ef7-17cedf7977be.png)

Raporda **sütun eklemek** veya kaldırmak için Sütunları seç'i seçin.  <br/> ![OneDrive - Sütunlar'ı seçin.](../../media/252f311f-ffde-4e5a-9158-2b822bf86964.png)

Ayrıca, Dışarı Aktar bağlantısını seçerek Excel .csv verilerini bir Excel .csv dosyasına **aktarabilirsiniz**. Bu işlem tüm kullanıcıların verilerini dışarı aktarır ve daha fazla çözümleme yapmak için basit sıralama ve filtreleme işlemlerini kullanmanıza olanak tanır. 2000'den az kullanıcınız varsa, raporun kendi içindeki tabloda sıralama ve filtreleme yapabilirsiniz. 2000'den çok kullanıcınız varsa, filtrelemek ve sıralamak için verileri dışarı aktarmanız gerekir.

**OneDrive İş aktivite** raporu, son 7 gün, 30 gün, 90 gün veya 180 günlük eğilimler için görüntülenebilir. Ancak rapordaki belirli bir günü seçersiniz, tablo geçerli tarihten (raporun oluşturulma tarihine değil) itibaren 28 güne kadar olan verileri gösterir.
  
|Öğe|Açıklama|
|:-----|:-----|
|**Metrik**|**Tanım**|
|Kullanıcı Adı  <br/> |Hesap sahibi olan kullanıcının OneDrive.  <br/> |
|Son etkinlik tarihi (UTC)  <br/> |Seçilen tarih aralığı için Dosya hesabında OneDrive etkinlik gerçekleştirilen son tarih. . Belirli bir tarihte gerçekleştirilen etkinliği görmek için, grafikte doğrudan tarihi seçin.  <br/> |
|Görüntülenen veya düzenlenen dosyalar  <br/> |Kullanıcının karşıya yükleytiği, indirdiğiniz, değiştirdiğiniz veya görüntülediğiniz dosya sayısı.   <br/> |
|Eşitlenen dosyalar  <br/> |Kullanıcının yerel cihazından hesap hesabıyla eşitlenen dosya OneDrive. <br/> |
|Şirket içinde paylaşılan dosyalar  <br/> | Kuruluş içindeki kullanıcılarla veya gruplarda bulunan kullanıcılarla (dış kullanıcılar da dahil) paylaşılan dosya sayısı.  <br/> |
|Dışarıdan paylaşılan dosyalar  <br/> |Kuruluşun dışındaki kullanıcılarla paylaşılan dosya sayısı. <br/>|
|Silindi  <br/> | Bu, kullanıcının lisansının kaldırıldığına işarettir.  <br/> NOT: Seçilen dönem içinde bir süre lisanslı olduğu sürece, silinen kullanıcının etkinliği raporda görüntülenir. **Silindi** sütunu, kullanıcının artık etkin olamayacağını ama rapordaki verilere katkıda bulunduğunu belirlemenize yardımcı olur.  <br/> |
|Silinme tarihi  <br/> |Kullanıcının lisansının kaldırıldığı tarih. <br/>|
|Ürün atandı  <br/> |Kullanıcıya Microsoft 365 lisansları olan ürünler.|
|||