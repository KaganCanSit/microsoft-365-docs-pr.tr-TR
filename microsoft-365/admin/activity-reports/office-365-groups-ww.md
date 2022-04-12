---
title: Microsoft 365 yönetim merkezi grupları raporları
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
- MET150
- MOE150
- GEA150
ms.assetid: a27f1a99-3557-4f85-9560-a28e3d822a40
description: Gruplar ve etkinlikleri hakkında bilgi edinmek için bir Microsoft 365 grupları raporu alın.
ms.openlocfilehash: d4130d577341bbc8c4516234964ea9e805be81ee
ms.sourcegitcommit: ac0ae5c2888e2b323e36bad041a4abef196c9c96
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/12/2022
ms.locfileid: "64781687"
---
# <a name="microsoft-365-reports-in-the-admin-center---microsoft-365-groups"></a>Yönetim merkezinde raporları Microsoft 365 - Microsoft 365 grupları

Microsoft 365 Raporları panosu, kuruluşunuzdaki ürünler genelindeki etkinliğe genel bakışı gösterir. Bu pano sayesinde her bir üründeki etkinliklerle ilgili daha ayrıntılı bilgi edinmek için ürün düzeyinde raporları ayrıntılı olarak inceleyebilirsiniz. [Raporlara genel bakış konusuna](activity-reports.md) göz atın. Microsoft 365 grupları raporunda, kuruluşunuzdaki grupların etkinliği hakkında içgörüler elde edebilir ve kaç grubun oluşturulup kullanıldığını görebilirsiniz.
  
## <a name="how-to-get-to-the-groups-report"></a>Gruplar raporuna erişme

1. Yönetim merkezinde, **Raporlar** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">Kullanımı</a> sayfasına gidin.

2. Pano giriş sayfasında, Office 365 rapor sayfasına ulaşmak için Etkin kullanıcılar - Microsoft 365 应用版 veya Etkin kullanıcılar - Microsoft 365 Hizmetleri kartındaki Daha **fazla** görüntüle düğmesine tıklayın.
  
## <a name="interpret-the-groups-report"></a>Gruplar raporunu yorumlama

**Gruplar etkinlik** sekmesini seçerek etkinleştirmeleri Office 365 raporunda görüntüleyebilirsiniz.

:::image type="content" alt-text="raporları Microsoft 365 - Microsoft Office 365 grupları etkinliği." source="../../media/ab90e30b-8938-4110-ab3d-ee472a4cfe21.png" lightbox="../../media/ab90e30b-8938-4110-ab3d-ee472a4cfe21.png":::

Rapora sütun eklemek veya rapordan sütun kaldırmak için Sütunları **seç'i** seçin.

:::image type="content" alt-text="Office 365 grupları etkinlik raporu - sütunları seçin." source="../../media/1600556a-f5f1-47d9-b325-cd77c78f4004.png":::

Dışarı **Aktar bağlantısını** seçerek rapor verilerini bir Excel .csv dosyasına da aktarabilirsiniz. Bu işlem tüm kullanıcıların verilerini dışarı aktarır ve daha fazla çözümleme yapmak için basit sıralama ve filtreleme işlemlerini kullanmanıza olanak tanır. 2000'den az kullanıcınız varsa, raporun kendi içindeki tabloda sıralama ve filtreleme yapabilirsiniz. 2000'den çok kullanıcınız varsa, filtrelemek ve sıralamak için verileri dışarı aktarmanız gerekir. 

**Gruplar** raporu son 7 gün, 30 gün, 90 gün veya 180 günlük eğilimler için görüntülenebilir. Ancak raporda belirli bir gün seçerseniz, tablo geçerli tarihten itibaren (raporun oluşturulduğu tarihten değil) 28 güne kadar olan verileri gösterir.

|Metrik|Tanım|
|:-----|:-----|
|Grup adı |Grubun adı. |
|Silindi |Silinen grupların sayısı. Bu bayrak doğru olarak ayarlanırsa, raporlama dönemi içinde etkinlik gerçekleştirmiş gruplar daha sonra silinmiş olsa bile kılavuzda gösterilir. |
|Grup sahibi |Grup sahibinin adı. |
|Son etkinlik tarihi (UTC) |Grup tarafından iletinin alındığı en son tarih. Bu tarih, bir e-posta konuşmasında, Yammer'da veya sitede etkinliğin olduğu en son tarihtir. |
|Tür |Grubun türü. Bu, özel veya ortak grup olabilir. |
|Exchange alınan e-postalar |Grup tarafından alınan ileti sayısı.|
|Exchange e-postalar (toplam) |Grubun posta kutusunda yer alan toplam öğe sayısı. |
|Exchange için kullanılan posta kutusu depolama alanı (MB) |Grubun posta kutusu tarafından kullanılan depolama alanı. |
|SharePoint dosyaları (toplam) |SharePoint grup sitelerinde depolanan dosyaların sayısı. |
|SharePoint dosyaları (etkin) |raporlama döneminde SharePoint grup sitesinde işlem yapılan (görüntülenen veya değiştirilen, eşitlenen, şirket içinde veya dışında paylaşılan) dosya sayısı. |
|SharePoint için kullanılan toplam site depolama alanı (MB) |Raporlama döneminde kullanılan MB cinsinden depolama miktarı. |
|Yammer'deki iletiler (gönderilen) |Raporlama döneminde Yammer grubuna gönderilen ileti sayısı. |
|Yammer iletileri (okuma) |Raporlama döneminde Yammer grubunda okunan konuşma sayısı. |
|Yammer'deki iletiler (beğenildi) |Raporlama döneminde Yammer grubunda beğenilen iletilerin sayısı. |
|Üyeler |Gruptaki üye sayısı. |
|Dış üyeler |Gruptaki dış kullanıcıların sayısı.|


## <a name="related-content"></a>İlgili içerik

[yönetim merkezinde Microsoft 365 Raporları](activity-reports.md) (makale)\
[Güvenlik & Uyumluluk Merkezi'ndeki akıllı raporlar ve içgörüler](/microsoft-365/security/office-365-security/reports-and-insights-in-security-and-compliance) (makale)\
[Yönetim merkezinde Microsoft 365 Raporları - Etkin Kullanıcılar](../../admin/activity-reports/active-users-ww.md) (makale)

