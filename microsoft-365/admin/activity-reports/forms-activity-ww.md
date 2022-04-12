---
title: form etkinlik raporlarını Microsoft 365 yönetim merkezi
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
description: Microsoft 365 yönetim merkezi Microsoft 365 Raporları panosunu kullanarak Microsoft Forms etkinlik raporu almayı öğrenin.
ms.openlocfilehash: c00c9e91d4b8e37021a30798088f46b786b3b4fc
ms.sourcegitcommit: ac0ae5c2888e2b323e36bad041a4abef196c9c96
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/12/2022
ms.locfileid: "64781939"
---
# <a name="microsoft-365-reports-in-the-admin-center---forms-activity"></a>Yönetim merkezinde raporları Microsoft 365 - Formlar etkinliği

Microsoft 365 Raporları panosu, kuruluşunuzdaki ürünler genelindeki etkinliğe genel bakışı gösterir. Bu pano sayesinde ürünlerin her birindeki etkinliklerle ilgili daha ayrıntılı bilgi edinmek için ürün düzeyinde raporları ayrıntılı olarak inceleyebilirsiniz. [Raporlara genel bakış konusuna](activity-reports.md) göz atın.
  
Örneğin, formlarla etkileşimlerine bakarak Microsoft Forms kullanma lisansına sahip her kullanıcının etkinliğini anlayabilirsiniz. Ayrıca, kullanıcının yanıt verdiği form ve form sayısına bakarak devam eden işbirliği düzeyini anlamanıza da yardımcı olur.
  
## <a name="how-to-get-to-the-forms-activity-report"></a>Forms etkinlik raporuna erişme

1. Yönetim merkezinde, **Raporlar** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">Kullanımı</a> sayfasına gidin. 
2. Pano giriş sayfasında, Formlar kartındaki **Daha fazla görüntüle** düğmesine tıklayın.
  
## <a name="interpret-the-forms-activity-report"></a>Forms etkinlik raporunu yorumlama

**Etkinlik** sekmesini seçerek Etkinlikleri Formlar raporunda görüntüleyebilirsiniz.<br/>![Microsoft 365 raporları - etkinlik raporu Microsoft Forms.](../../media/275fb0a1-b9d9-4233-8aaf-e7df73cc705f.png)

Rapora sütun eklemek veya rapordan sütun kaldırmak için Sütunları **seç'i** seçin.  <br/> ![Formlar etkinlik raporu - sütunları seçin.](../../media/0c9b0b69-5dc7-43ea-8e2c-54407b6ce2ab.png)

Dışarı **Aktar bağlantısını** seçerek rapor verilerini bir Excel .csv dosyasına da aktarabilirsiniz. Bu işlem tüm kullanıcıların verilerini dışarı aktarır ve daha fazla çözümleme yapmak için basit sıralama ve filtreleme işlemlerini kullanmanıza olanak tanır. 2000'den az kullanıcınız varsa, raporun kendi içindeki tabloda sıralama ve filtreleme yapabilirsiniz. 2000'den çok kullanıcınız varsa, filtrelemek ve sıralamak için verileri dışarı aktarmanız gerekir. 

**Formlar etkinlik** raporu son 7 gün, 30 gün, 90 gün veya 180 günlük eğilimler için görüntülenebilir. Ancak raporda belirli bir gün seçerseniz, tablo geçerli tarihten itibaren (raporun oluşturulduğu tarihten değil) 28 güne kadar olan verileri gösterir.
  
|Öğe|Açıklama|
|:-----|:-----|
|**Metrik**|**Tanım**|
|Kullanıcı Adı  <br/> |Microsoft Forms etkinliği gerçekleştiren kullanıcının e-posta adresi.  <br/> |
|Son etkinlik tarihi (UTC)  <br/> |Bir form etkinliğinin seçilen tarih aralığı için kullanıcı tarafından gerçekleştirildiği en son tarih. Belirli bir tarihte gerçekleştirilen etkinliği görmek için, grafikte doğrudan tarihi seçin.<br/><br/>Bu, tabloyu yalnızca belirli bir günde etkinliği gerçekleştiren kullanıcılar için dosya etkinliği verilerini görüntüleyecek şekilde filtreler.  <br/> |
|Oluşturulan form sayısı  <br/> |Kullanıcının oluşturduğu form sayısı.   <br/> |
|Yanıtlanan form sayısı  <br/> |Kullanıcının yanıt gönderdiği form sayısı.|
|||
