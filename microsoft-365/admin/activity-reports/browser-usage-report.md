---
title: tarayıcı kullanım raporlarını Microsoft 365 yönetim merkezi
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
description: Microsoft 365 yönetim merkezi Microsoft 365 Raporları panosunu kullanarak Microsoft tarayıcı kullanım raporu almayı öğrenin.
ms.openlocfilehash: 5515c00b5c7fc64a6f0295bdce724e5b798fb018
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65078323"
---
# <a name="microsoft-365-reports-in-the-admin-center---microsoft-browser-usage"></a>Yönetim merkezinde Microsoft 365 Raporları - Microsoft tarayıcı kullanımı

Microsoft 365 Raporları panosu, kuruluşunuzdaki ürünler genelinde bir etkinliğe genel bakış gösterir. Her bir üründeki etkinlikler hakkında daha ayrıntılı içgörüler elde etmek için tek tek ürün düzeyi raporlarında detaya gitmenizi sağlar. [Raporlara genel bakış konusuna](activity-reports.md) göz atın. Microsoft tarayıcı kullanım raporunda Internet Explorer, Microsoft Edge'in eski sürümü ve yeni Microsoft Edge kullanımı hakkında içgörüler elde edebilirsiniz. Kullanım raporlaması, Microsoft 365 hesabı kullanan herhangi bir cihazda Microsoft tarayıcısı kullanılarak erişilen Microsoft 365 çevrimiçi hizmetler temel alır.

## <a name="how-to-get-to-the-microsoft-browser-usage-report"></a>Microsoft tarayıcı kullanım raporuna erişme

1. Yönetim merkezinde **Rapor** \> <b><a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">Kullanımı</a></b> sayfasına gidin.

2. Pano giriş sayfasında, Microsoft tarayıcı kullanım kartındaki **Daha fazla görüntüle** düğmesine tıklayın.

## <a name="how-to-notify-users-to-upgrade-their-browser"></a>Kullanıcılara tarayıcılarını yükseltmeleri için bildirim gönderme

:::image type="content" alt-text="Microsoft tarayıcı kullanım raporu eylem akışı." source="../../media/1ef4eb08-18b8-4dda-aa15-1aad013ecd70.png" lightbox="../../media/1ef4eb08-18b8-4dda-aa15-1aad013ecd70.png":::

Genel yöneticiler, Internet Explorer'dan Microsoft 365 hizmetlerine erişen kullanıcılara ileti göndermeyi tercih edebilir (anımsatıcı olarak, Internet Explorer masaüstü uygulaması 15 Haziran 2022'de kullanımdan kaldırılacaktır). Bu hedeflenen ileti, kullanıcılara bu tarayıcıları destekleyenlerin yakında sona ereceğini bildirir ve Microsoft Edge ve tarayıcılar arasında geçiş yapmak için izlenecek basit adımları içeren bir destek makalesine bağlanır. 

Kuruluşunuzda raporda Internet Explorer kullanımı gösteriliyorsa (genel yönetici izinleri gerekiyor) bu özelliği Microsoft tarayıcı kullanım raporu sayfasında bulabilirsiniz. İleti oluşturulduktan sonra kullanıcılara 15 Haziran 2022'ye kadar belirtilen sıklıkta bildirim gönderilir. Bu özelliği istediğiniz zaman açıp kapatabilirsiniz.

Bu, şu anda yalnızca ABD'deki genel yöneticiler için kullanılabilen ve çevrimiçi Excel kullanıcı bildirimlerine izin veren sınırlı bir özelliktir.

## <a name="interpret-the-microsoft-browser-usage-report"></a>Microsoft tarayıcı kullanım raporunu yorumlama

:::image type="content" alt-text="Microsoft tarayıcı kullanım raporu." source="../../media/95557c88-24ee-417d-a828-96ba00b17aaf.png" lightbox="../../media/95557c88-24ee-417d-a828-96ba00b17aaf.png":::

|Öğe|Açıklama|
|:-----|:-----|
|1. |**Microsoft tarayıcı kullanım** raporu son 7 gün, 30 gün, 90 gün veya 180 günlük eğilimler için görüntülenebilir. |
|2. |Her rapordaki veriler genellikle son yedi güne kadar kapsar. |
|3. |**Günlük etkin kullanıcılar** grafiği, Microsoft 365 hizmetlerine erişmek için kullanılan Microsoft Edge, Microsoft Edge'in eski sürümü ve Internet Explorer için günlük kullanıcı sayısını gösterir. |
|4. |**Etkin Kullanıcılar** grafiği, seçilen zaman aralığında Microsoft 365 hizmetlerine erişmek için kullanıldığında Microsoft Edge, Microsoft Edge'in eski sürümü ve Internet Explorer kullanan toplam kullanıcı sayısını gösterir. |
|5. |Tablo, kullanıcı başına verilerin dökümünü gösterir. Tablodaki sütunları ekleyebilir veya kaldırabilirsiniz.  <br/><br/>**Kullanıcı adı**, Microsoft tarayıcılarını kullanarak Microsoft 365 hizmetlerine bağlanan kullanıcının e-posta adresidir.<br><br/>**Kullanılan Microsoft Edge**, kullanıcının Microsoft 365 hizmetlerine bağlanmak için Microsoft Edge kullandığında bir onay işareti gösterir.<br/><br/>**Kullanılan Microsoft Edge'in eski sürümü**, kullanıcının Microsoft 365 hizmetlerine bağlanmak için Microsoft Edge'in eski sürümü kullandığında bir onay işareti gösterir.<br/><br/>**Kullanılan Internet Explorer**, kullanıcı internet explorer kullanarak Microsoft 365 hizmetlerine bağlandıysa bir onay işareti gösterir. |
|6. |**Rapora sütun** eklemek veya rapordan sütun kaldırmak için Sütunları seç simgesini seçin.|
|7. |Dışarı **Aktar bağlantısını** seçerek rapor verilerini bir Excel .csv dosyasına da aktarabilirsiniz. Bu, tüm kullanıcılar için verileri dışarı aktarır ve daha fazla analiz için basit toplama, sıralama ve filtreleme gerçekleştirmenize olanak tanır. 100'den az kullanıcınız varsa, raporun içindeki tablonun içinde sıralama ve filtreleme yapabilirsiniz. 100'den fazla kullanıcınız varsa, filtrelemek ve sıralamak için verileri dışarı aktarmanız gerekir.|
