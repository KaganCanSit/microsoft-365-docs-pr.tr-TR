---
title: Microsoft 365 Merkezinde Raporlar - Microsoft tarayıcı kullanımı
ms.author: waxiaoyu
author: sarahwxy
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
description: Microsoft tarayıcı kullanım raporunu, çalışma sayfalarındaki raporlar Microsoft 365 kullanarak nasıl ala bir Microsoft 365 yönetim merkezi.
ms.openlocfilehash: d653bf1132f461b14644b1ddc04bab2fdceee358
ms.sourcegitcommit: 542e6b5d12a8d400c3b9be44d849676845609c5f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/15/2021
ms.locfileid: "62999588"
---
# <a name="microsoft-365-reports-in-the-admin-center---microsoft-browser-usage"></a>Microsoft 365 Merkezinde Raporlar - Microsoft tarayıcı kullanımı

Rapor Microsoft 365 panosu, size kurum genelindeki ürünlerde etkinliğin bir genel görünümünü gösterir. Bu, her bir ürün içindeki etkinliklerle ilgili daha ayrıntılı bilgi vermek için ürün düzeyinde raporları ayrıntılı olarak incelemeye olanak sağlar. [Raporlara genel bakış konusuna](activity-reports.md) göz atın. Microsoft tarayıcı kullanımı raporunda Internet Explorer, uygulama kullanımı ve kullanım Microsoft Edge'in eski sürümü öngörüler Microsoft Edge edinebilirsiniz. Kullanım raporlama, Microsoft Microsoft 365 kullanarak erişilen çevrimiçi hizmetlere dayalıdır.

## <a name="how-to-get-to-the-microsoft-browser-usage-report"></a>Microsoft tarayıcı kullanım raporuna nasıl gönderilir?

1. Yönetim merkezinde Rapor Kullanımı **sayfasına** \> <b><a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">gidin.</a></b>

2. Pano giriş sayfasında, Microsoft tarayıcı kullanım **kartında** Daha fazla görüntüle düğmesine tıklayın.

## <a name="how-to-notify-users-to-upgrade-their-browser"></a>Kullanıcıları tarayıcılarını yükseltmeleri için bildirme

:::image type="content" alt-text="Microsoft tarayıcı kullanımı raporu eylem akışı." source="../../media/1ef4eb08-18b8-4dda-aa15-1aad013ecd70.png" lightbox="../../media/1ef4eb08-18b8-4dda-aa15-1aad013ecd70.png":::

Genel yöneticiler, Internet Explorer'dan Microsoft 365 hizmetlerine erişen kullanıcılara ileti göndermeyi kabul etmek için (anımsatıcı olarak, Internet Explorer masaüstü uygulaması 15 Haziran 2022'de devre dışı olacak). Bu hedefli ileti, bu tarayıcıları destekleyen kullanıcılara çok yakında bir destek makalesi göndereceklerini ve tarayıcılar arasında geçiş yapmak için Microsoft Edge adımlarını içeren bir destek makalesi bağlantıları gönderir. 

Bu özelliği, kurumda raporda gösterilen Internet Explorer kullanımı varsa (genel yönetici izinleri gereklidir) Microsoft tarayıcı kullanımı raporu sayfasında bulabilirsiniz. İleti oluşturulduktan sonra, kullanıcılar 15 Haziran 2022'ye kadar belirtilen sıklıkta bilgi alırlar. Bu özelliği her zaman açabilirsiniz veya kapatabilirsiniz.

Bu, şu anda yalnızca ABD'de genel yöneticiler tarafından kullanılabilen ve çevrimiçi durumda kullanıcı bildirimlerine izin veren, sınırlı Excel özelliktir.

## <a name="interpret-the-microsoft-browser-usage-report"></a>Microsoft tarayıcı kullanım raporunu yorumlama

:::image type="content" alt-text="Microsoft tarayıcı kullanımı raporu." source="../../media/95557c88-24ee-417d-a828-96ba00b17aaf.png" lightbox="../../media/95557c88-24ee-417d-a828-96ba00b17aaf.png":::

|Öğe|Açıklama|
|:-----|:-----|
|1. |**Microsoft tarayıcı kullanımı** raporu, son 7 gün, 30 gün, 90 gün veya 180 günlük eğilimler için görüntülenebilirsiniz. |
|2. |Her rapora gelen veriler genellikle son yedi günü kapsar. |
|3. |Günlük **etkin kullanıcılar grafiği**, belirli hizmetlere Microsoft Edge, Microsoft Edge'in eski sürümü ve Internet Explorer için günlük kullanıcı Microsoft 365 gösterir. |
|4. |Etkin **Kullanıcılar grafiği**, seçilen dönem içinde Microsoft Edge, Microsoft Edge'in eski sürümü ve Internet Explorer kullanan Microsoft 365 kullanıcı sayısını gösterir. |
|5. |Tablo, kullanıcı başına verilerin dökümünü gösterir. Tablodaki sütunları ekleyebilir veya kaldırabilirsiniz.  <br/><br/>**Kullanıcı** adı, Microsoft tarayıcılarını kullanarak Microsoft 365 hizmetleriyle bağlantı yapan kullanıcının e-posta adresidir.<br><br/>**Kullanılan Microsoft Edge**, kullanıcı Microsoft Edge hizmetlerini bağlamak için Microsoft Edge için onay Microsoft 365 gösterir.<br/><br/>**Kullanılan Microsoft Edge'in eski sürümü**, kullanıcı Microsoft Edge'in eski sürümü hizmetlerini bağlamak için Microsoft Edge'in eski sürümü için onay Microsoft 365 gösterir.<br/><br/>**Kullanılan Internet Explorer**, kullanıcı internet hizmetine bağlanmak için Internet Explorer'ı kullandı ise bir onay Microsoft 365 gösterir. |
|6. |Raporda **sütun eklemek veya** kaldırmak için Sütunları seç simgesini seçin.|
|7. |Ayrıca, Dışarı Aktar bağlantısını seçerek Excel .csv verilerini bir Excel .csv dosyasına **aktarabilirsiniz**. Bu işlem tüm kullanıcıların verilerini dışarı aktarır ve daha fazla çözümleme yapmak için basit toplama, sıralama ve filtreleme gibi işlemlerde size olanak sağlar. 100'den az kullanıcınız varsa, raporun kendi içindeki tabloda sıralama ve filtre uygulama. 100'den fazla kullanıcınız varsa, filtrelemek ve sıralamak için verileri dışarı aktarmanız gerekir.|
