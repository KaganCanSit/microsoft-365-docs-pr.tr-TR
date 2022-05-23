---
title: Microsoft Dynamics 365 müşteri ses etkinliği raporları
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
description: Raporlar panosunu kullanarak Microsoft Dynamics 365 Customer Voice etkinlik raporu almayı öğrenin ve lisanslı kullanıcıların nasıl işbirliğine sahip olduğunu öğrenin.
ms.openlocfilehash: 8f936f2b3232d8086928751c9846a8d762ff8219
ms.sourcegitcommit: db1e48af88995193f15bbd5962f5101a6088074b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/23/2022
ms.locfileid: "65636580"
---
# <a name="microsoft-365-reports-in-the-admin-center---dynamics-365-customer-voice-activity"></a>Yönetim merkezinde raporları Microsoft 365 - Dynamics 365 Customer Voice etkinliği

Microsoft 365 Raporları panosu, kuruluşunuzdaki ürünler genelindeki etkinliğe genel bakışı gösterir. Bu pano sayesinde ürünlerin her birindeki etkinliklerle ilgili daha ayrıntılı bilgi edinmek için ürün düzeyinde raporları ayrıntılı olarak inceleyebilirsiniz. [Raporlara genel bakış konusuna](activity-reports.md) göz atın.
  
Örneğin, Dynamics 365 Customer Voice ile etkileşimlerine bakarak Microsoft Dynamics 365 Customer Voice kullanma lisansına sahip her kullanıcının etkinliğini anlayabilirsiniz. Ayrıca, oluşturulan Pro Anketlerinin sayısına bakarak ve kullanıcıların yanıt verdiği Anketleri Pro işbirliği düzeyini anlamanıza yardımcı olur. 
  
## <a name="how-to-get-to-the-dynamics-365-customer-voice-activity-report"></a>Dynamics 365 Customer Voice etkinlik raporuna erişme

1. Yönetim merkezinde, **Raporlar** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">Kullanımı</a> sayfasına gidin. 
2. Pano giriş sayfasında Dynamics 365 Müşteri Sesi kartındaki **Daha fazla görüntüle** düğmesine tıklayın.
  
## <a name="interpret-the-dynamics-365-customer-voice-activity-report"></a>Dynamics 365 Customer Voice etkinlik raporunu yorumlama

**Etkinlik** sekmesini seçerek Dynamics 365 Customer Voice raporunda etkinlikleri görüntüleyebilirsiniz.<br/>![Microsoft 365 raporları - Microsoft Dynamics 365 Customer Voice etkinlik raporu.](../../media/a7e57d18-1ac8-4d4b-bd70-83361505dc3e.png)

Rapora sütun eklemek veya rapordan sütun kaldırmak için Sütunları **seç'i** seçin.  <br/> ![Dynamics 365 Customer Voice etkinlik raporu - sütunları seçin.](../../media/5ab66f4b-32eb-4c9b-9683-1157ae9e2c0a.png)

Dışarı **Aktar bağlantısını** seçerek rapor verilerini bir Excel .csv dosyasına da aktarabilirsiniz. Bu işlem tüm kullanıcıların verilerini dışarı aktarır ve daha fazla çözümleme yapmak için basit sıralama ve filtreleme işlemlerini kullanmanıza olanak tanır. 2000'den az kullanıcınız varsa, raporun kendi içindeki tabloda sıralama ve filtreleme yapabilirsiniz. 2000'den fazla kullanıcınız varsa, filtrelemek ve sıralamak için verileri dışarı aktarmanız gerekir. 

**Dynamics 365 Customer Voice etkinlik** raporu son 7 gün, 30 gün, 90 gün veya 180 günlük eğilimler için görüntülenebilir. Ancak raporda belirli bir gün seçerseniz, tablo geçerli tarihten itibaren (raporun oluşturulduğu tarihten değil) 28 güne kadar olan verileri gösterir.
  
|Öğe|Açıklama|
|:-----|:-----|
|**Metrik**|**Tanım**|
|Kullanıcı Adı  <br/> |Microsoft Forms etkinliği gerçekleştiren kullanıcının e-posta adresi.  <br/> |
|Son etkinlik tarihi (UTC)  <br/> |Bir form etkinliğinin seçilen tarih aralığı için kullanıcı tarafından gerçekleştirildiği en son tarih. Belirli bir tarihte gerçekleştirilen etkinliği görmek için, grafikte doğrudan tarihi seçin.<br/>Bu, tabloyu yalnızca belirli bir günde etkinliği gerçekleştiren kullanıcılar için dosya etkinliği verilerini görüntüleyecek şekilde filtreler.  <br/> |
|Oluşturulan anket sayısı  <br/> |Kullanıcının oluşturduğu anket sayısı.   <br/> |
|Anket yanıtlarının sayısı  <br/> |Anketin dağıtıldığı yanıtlayıcıların yanıtlarının sayısı.|
|||