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
description: Kuruluşunuzdaki grupların etkinliği hakkında içgörüler elde etmek ve kaç grubun oluşturulup kullanıldığını görmek için bir Microsoft 365 Grupları raporu alın.
ms.openlocfilehash: dc3d05fdad68f18b24dae06021b0cb15306b4338
ms.sourcegitcommit: e6443eb3a4c826792806873428c0c17b59f4fde5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2022
ms.locfileid: "65889246"
---
# <a name="microsoft-365-reports-in-the-admin-center---microsoft-365-groups"></a>Yönetim merkezinde Microsoft 365 Raporları - Microsoft 365 grupları

Microsoft 365 Raporları panosu, kuruluşunuzdaki ürünler genelindeki etkinliğe genel bakışı gösterir. Bu pano sayesinde her bir üründeki etkinliklerle ilgili daha ayrıntılı bilgi edinmek için ürün düzeyinde raporları ayrıntılı olarak inceleyebilirsiniz. [Raporlara genel bakış konusuna](activity-reports.md) göz atın. Microsoft 365 grupları raporunda, kuruluşunuzdaki grupların etkinliği hakkında içgörüler elde edebilir, kaç grubun oluşturulup kullanıldığını görebilirsiniz.
  
## <a name="how-to-get-to-the-groups-report"></a>Gruplar raporuna erişme

1. Yönetim merkezinde, **Raporlar** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">Kullanımı</a> sayfasına gidin.

2. Pano giriş sayfasında, Office 365 rapor sayfasına ulaşmak için Etkin kullanıcılar - Microsoft 365 Uygulamaları veya Etkin kullanıcılar - Microsoft 365 Hizmetleri kartındaki **Daha fazlasını görüntüle** düğmesine tıklayın.
  
## <a name="interpret-the-groups-report"></a>Gruplar raporunu yorumlama

Etkinleştirmeleri Office 365 raporunda **Gruplar etkinlik** sekmesini seçerek görüntüleyebilirsiniz.

:::image type="content" alt-text="Microsoft 365 raporları - Microsoft Office 365 grupları etkinliği." source="../../media/ab90e30b-8938-4110-ab3d-ee472a4cfe21.png" lightbox="../../media/ab90e30b-8938-4110-ab3d-ee472a4cfe21.png":::

Rapora sütun eklemek veya rapordan sütun kaldırmak için Sütunları **seç'i** seçin.

:::image type="content" alt-text="Office 365 grupları etkinlik raporu - sütunları seçin." source="../../media/1600556a-f5f1-47d9-b325-cd77c78f4004.png":::

Dışarı **Aktar** bağlantısını seçerek rapor verilerini bir Excel .csv dosyasına da aktarabilirsiniz. Bu işlem tüm kullanıcıların verilerini dışarı aktarır ve daha fazla çözümleme yapmak için basit sıralama ve filtreleme işlemlerini kullanmanıza olanak tanır. 2000'den az kullanıcınız varsa, raporun kendi içindeki tabloda sıralama ve filtreleme yapabilirsiniz. 2000'den fazla kullanıcınız varsa, filtrelemek ve sıralamak için verileri dışarı aktarmanız gerekir. 

**Gruplar** raporu son 7 gün, 30 gün, 90 gün veya 180 günlük eğilimler için görüntülenebilir. Ancak raporda belirli bir gün seçerseniz, tablo geçerli tarihten itibaren (raporun oluşturulduğu tarihten değil) 28 güne kadar olan verileri gösterir.

|Metrik|Tanım|
|:-----|:-----|
|Grup adı |Grubun adı. |
|Silindi |Silinen grupların sayısı. Bu bayrak doğru olarak ayarlanırsa, raporlama dönemi içinde etkinlik gerçekleştirmiş gruplar daha sonra silinmiş olsa bile kılavuzda gösterilir. |
|Grup sahibi |Grup sahibinin adı. |
|Son etkinlik tarihi (UTC) |Grup tarafından iletinin alındığı en son tarih. Bu tarih, bir e-posta konuşmasında, Yammer'da veya sitede etkinliğin olduğu en son tarihtir. |
|Tür |Grubun türü. Bu, özel veya ortak grup olabilir. |
|Exchange'de alınan e-postalar |Grup tarafından alınan ileti sayısı.|
|Exchange'de e-postalar (toplam) |Grubun posta kutusunda yer alan toplam öğe sayısı. |
|Exchange için kullanılan posta kutusu depolama alanı (MB) |Grubun posta kutusu tarafından kullanılan depolama alanı. |
|SharePoint dosyaları (toplam) |SharePoint grup sitelerinde depolanan dosyaların sayısı. |
|SharePoint dosyaları (etkin) |SharePoint grup sitesindeki raporlama döneminde üzerinde işlem yapılan (görüntülenen veya değiştirilen, eşitlenen, şirket içinde veya dışında paylaşılan) dosya sayısı. |
|SharePoint için kullanılan toplam site depolama alanı (MB) |Raporlama döneminde kullanılan MB cinsinden depolama miktarı. |
|Yammer'daki iletiler (gönderilen) |Raporlama döneminde Yammer grubunda gönderilen ileti sayısı. |
|Yammer'da iletiler (okuma) |Yammer grubunda raporlama döneminde okunan konuşma sayısı. |
|Yammer'daki iletiler (beğenildi) |Raporlama döneminde Yammer grubunda beğenilen iletilerin sayısı. |
|Üyeler |Gruptaki üye sayısı. |
|Dış üyeler |Gruptaki dış kullanıcıların sayısı.|
|Toplam düzenli toplantı sayısı  |Kullanıcının belirtilen zaman aralığında düzenlediği tek seferlik zamanlanmış ve yinelenen toplantıların toplamı.|
|Kanal iletileri  |Kullanıcının belirtilen zaman aralığında ekip sohbetinde yayınladığı benzersiz iletilerin sayısı. Buna özgün gönderiler ve yanıtlar dahildir. |


## <a name="related-content"></a>İlgili içerik

[Yönetim merkezinde Microsoft 365 Raporları](activity-reports.md) (makale)\
[Güvenlik & Uyumluluk Merkezi'ndeki akıllı raporlar ve içgörüler](/microsoft-365/security/office-365-security/reports-and-insights-in-security-and-compliance) (makale)\
[Yönetim merkezinde Microsoft 365 Raporları - Etkin Kullanıcılar](../../admin/activity-reports/active-users-ww.md) (makale)

