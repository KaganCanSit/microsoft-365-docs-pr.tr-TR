---
title: Microsoft 365 yönetim merkezi grupları raporlarını
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
description: Gruplar Microsoft 365 etkinlikleri hakkında bilgi almak için gruplarla ilgili bir rapor rapora sahip oluruz.
ms.openlocfilehash: ff3a5fa428bb993dac9a518229744754d106e589
ms.sourcegitcommit: cdb90f28e59f36966f8751fa8ba352d233317fc1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2022
ms.locfileid: "63400817"
---
# <a name="microsoft-365-reports-in-the-admin-center---microsoft-365-groups"></a>Microsoft 365 Merkezi'nde Raporlar - Microsoft 365 grupları

Rapor Microsoft 365 panosu, kurum kurum genelindeki ürünlerde etkinliğin genel görünümünü gösterir. Bu pano sayesinde her bir üründeki etkinliklerle ilgili daha ayrıntılı bilgi edinmek için ürün düzeyinde raporları ayrıntılı olarak inceleyebilirsiniz. [Raporlara genel bakış konusuna](activity-reports.md) göz atın. En Microsoft 365 raporuna bakarak, organizasyon kazandırılan grupların etkinliğiyle ilgili öngörüler edinebilirsiniz ve kaç grubun oluşturularak kullanılmaya neden olduğunu görebilirsiniz.
  
## <a name="how-to-get-to-the-groups-report"></a>Gruplar raporuna nasıl inersiniz?

1. Yönetim merkezinde, **Raporlar** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">Kullanımı</a> sayfasına gidin.

2. Pano giriş sayfasında, Microsoft 365 Uygulamaları rapor sayfasına almak  için Etkin kullanıcılar - Microsoft 365 Uygulamaları veya Etkin kullanıcılar - Microsoft 365 Hizmetleri kartında Daha fazla görüntüle Office 365 tıklayın.
  
## <a name="interpret-the-groups-report"></a>Gruplar raporunu yorumlama

Grup etkinliği sekmesini seçerek Office 365 rapora **bakabilirsiniz**.

:::image type="content" alt-text="Microsoft 365- grup Microsoft Office 365 etkinliklerini gösterir." source="../../media/ab90e30b-8938-4110-ab3d-ee472a4cfe21.png" lightbox="../../media/ab90e30b-8938-4110-ab3d-ee472a4cfe21.png":::

Raporda **sütun eklemek** veya kaldırmak için Sütunları seç'i seçin.

:::image type="content" alt-text="Office 365 grupları etkinlik raporunu değiştirme - Sütunları seçin." source="../../media/1600556a-f5f1-47d9-b325-cd77c78f4004.png":::

Ayrıca, Dışarı Aktar bağlantısını seçerek Excel .csv verilerini bir Excel .csv dosyasına **aktarabilirsiniz**. Bu işlem tüm kullanıcıların verilerini dışarı aktarır ve daha fazla çözümleme yapmak için basit sıralama ve filtreleme işlemlerini kullanmanıza olanak tanır. 2000'den az kullanıcınız varsa, raporun kendi içindeki tabloda sıralama ve filtreleme yapabilirsiniz. 2000'den çok kullanıcınız varsa, filtrelemek ve sıralamak için verileri dışarı aktarmanız gerekir. 

Gruplar **raporu** , son 7 gün, 30 gün, 90 gün veya 180 günlük eğilimler için görüntülenebilirsiniz. Ancak rapordaki belirli bir günü seçersiniz, tablo geçerli tarihten (raporun oluşturulma tarihine değil) itibaren 28 güne kadar olan verileri gösterir.

|Metrik|Tanım|
|:-----|:-----|
|Grup adı |Grubun adı. |
|Silindi |Silinen grupların sayısı. Bu bayrak doğru olarak ayarlanırsa, raporlama dönemi içinde etkinlik gerçekleştirmiş gruplar daha sonra silinmiş olsa bile kılavuzda gösterilir. |
|Grup sahibi |Grup sahibinin adı. |
|Son etkinlik tarihi (UTC) |Grubun en son ileti aldığı tarih. Bu tarih, bir e-posta konuşmasında, Yammer'da veya sitede etkinliğin olduğu en son tarihtir. |
|Tür |Grubun türü. Bu, özel veya ortak grup olabilir. |
|E-postalar Exchange |Grup tarafından alınan iletilerin sayısı.|
|E-Exchange (toplam) |Grubun posta kutusunda yer alan öğelerin toplam sayısı. |
|Posta kutusu depolama alanı Exchange (MB) |Grubun posta kutusu tarafından kullanılan depolama alanı. |
|SharePoint (toplam) |Grup sitelerinden bir SharePoint sayısı. |
|SharePoint (etkin) |Raporlama döneminde üzerinde SharePoint üzerinde eylem ed (görüntülenen veya değiştirilen, eşitlenen, şirket içinde veya dışında paylaşılan) dosyaların sayısı. |
|Site depolama alanı olarak kullanılan SharePoint depolama alanı (MB) |Raporlama döneminde kullanılan MB depolama miktarı. |
|İletiler Yammer (gönderilen) |Raporlama dönemi süresi boyunca Yammer ileti sayısı. |
|İletiler Yammer (okuma) |Rapor dönemindeki grup içinde Yammer konuşma sayısı. |
|E-posta Yammer (beğenildi) |Raporlama dönemi süresi boyunca grup Yammer ileti sayısı. |
|Üyeler |Gruptaki üye sayısıdır. |
|Dış üyeler |Gruptaki dış kullanıcıların sayısı.|


## <a name="related-content"></a>İlgili içerik

[Microsoft 365 Merkezinde Raporları (makale](activity-reports.md))\
[Güvenlik Ve Uyumluluk Merkezi'nde akıllı & öngörüler](/microsoft-365/security/office-365-security/reports-and-insights-in-security-and-compliance) (makale)\
[Microsoft 365 Merkezinde Rapor Raporları - Etkin Kullanıcılar](../../admin/activity-reports/active-users-ww.md) (makale)

