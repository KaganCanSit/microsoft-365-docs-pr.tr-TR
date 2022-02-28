---
title: Microsoft 365 Merkezi'nde Raporlar - Dynamics 365 Müşteri Sesi etkinliği
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
description: Microsoft Dynamics 365 Müşteri Sesi etkinlik raporunu, rapor üzerinde Microsoft 365 Raporlar panosu kullanarak nasıl Microsoft 365 yönetim merkezi.
ms.openlocfilehash: d143728f8170ae9c12a6d007e9e256a23f7ff74d
ms.sourcegitcommit: bf3965b46487f6f8cf900dd9a3af8b213a405989
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/02/2021
ms.locfileid: "62989911"
---
# <a name="microsoft-365-reports-in-the-admin-center---dynamics-365-customer-voice-activity"></a>Microsoft 365 Merkezi'nde Raporlar - Dynamics 365 Müşteri Sesi etkinliği

Rapor Microsoft 365 panosu, kurum kurum genelindeki ürünlerde etkinliğin genel görünümünü gösterir. Bu pano sayesinde ürünlerin her birindeki etkinliklerle ilgili daha ayrıntılı bilgi edinmek için ürün düzeyinde raporları ayrıntılı olarak inceleyebilirsiniz. [Raporlara genel bakış konusuna](activity-reports.md) göz atın.
  
Örneğin, Microsoft Dynamics 365 Customer Voice kullanma lisansı olan her kullanıcının etkinliğini anlamak için Dynamics 365 Customer Voice ile etkileşimlerine bakebilirsiniz. Ayrıca, oluşturulan Pro Anketlerin sayısına bakarak işbirliği düzeyini anlamanıza ve kullanıcıların yanıt Pro Anketler oluşturmanıza da yardımcı olur. 
  
## <a name="how-to-get-to-the-dynamics-365-customer-voice-activity-report"></a>Dynamics 365 Müşteri Sesi etkinlik raporuna nasıl elde olur?

1. Yönetim merkezinde, **Raporlar** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">Kullanımı</a> sayfasına gidin. 
2. Pano giriş sayfasında, Dynamics 365  Müşteri Sesi kartında Daha fazla görüntüle düğmesine tıklayın.
  
## <a name="interpret-the-dynamics-365-customer-voice-activity-report"></a>Dynamics 365 Müşteri Sesi etkinlik raporunu yorumlama

Dynamics 365 Customer Voice raporunda Etkinlik sekmesini seçerek etkinlikleri **görüntüleyebilirsiniz** .<br/>![Microsoft 365- Microsoft Dynamics 365 Müşteri Sesi etkinliği raporu.](../../media/a7e57d18-1ac8-4d4b-bd70-83361505dc3e.png)

Raporda **sütun eklemek** veya kaldırmak için Sütunları seç'i seçin.  <br/> ![Dynamics 365 Müşteri Sesi etkinlik raporu - Sütunları seçin.](../../media/5ab66f4b-32eb-4c9b-9683-1157ae9e2c0a.png)

Ayrıca, Dışarı Aktar bağlantısını seçerek Excel .csv verilerini bir Excel .csv dosyasına **aktarabilirsiniz**. Bu işlem tüm kullanıcıların verilerini dışarı aktarır ve daha fazla çözümleme yapmak için basit sıralama ve filtreleme işlemlerini kullanmanıza olanak tanır. 2000'den az kullanıcınız varsa, raporun kendi içindeki tabloda sıralama ve filtreleme yapabilirsiniz. 2000'den çok kullanıcınız varsa, filtrelemek ve sıralamak için verileri dışarı aktarmanız gerekir. 

**Dynamics 365 Müşteri** Sesi etkinlik raporu, son 7 gün, 30 gün, 90 gün veya 180 günlük eğilimler için görüntülenebilirsiniz. Ancak rapordaki belirli bir günü seçersiniz, tablo geçerli tarihten (raporun oluşturulma tarihine değil) itibaren 28 güne kadar olan verileri gösterir.
  
|Öğe|Açıklama|
|:-----|:-----|
|**Metrik**|**Tanım**|
|Kullanıcı Adı  <br/> |Etkinliği Microsoft Forms üzerinde gerçekleştiren kullanıcının e-posta adresi.  <br/> |
|Son etkinlik tarihi (UTC)  <br/> |Seçilen tarih aralığı için kullanıcı tarafından form etkinliğinin gerçekleştirmiş olduğu en son tarih. Belirli bir tarihte gerçekleştirilen etkinliği görmek için, grafikte doğrudan tarihi seçin.<br/>Bu, yalnızca o gün etkinlik gerçekleştirilen kullanıcılar için dosya etkinliği verilerini görüntülemek için tabloya filtre uygulamaz.  <br/> |
|Oluşturulan anket sayısı  <br/> |Kullanıcının oluşturduğu anketlerin sayısı.   <br/> |
|Anket yanıtı sayısı  <br/> |Anketi dağıtan yanıtlayanlardan gelen yanıt sayısı.|
|||