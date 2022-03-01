---
title: Microsoft 365 Bağlantısı Konum Hizmetleri'ne Bağlan'a
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 12/06/2021
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: admindeeplinkMAC
description: Microsoft 365 Bağlantısı Konum Hizmetleri'ne Bağlan'a
ms.openlocfilehash: 6150102471b03fbc83be09b503a6969ca6615a87
ms.sourcegitcommit: 388279e10a160b85b345a8ad760f6816dda4e2ad
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2021
ms.locfileid: "62996619"
---
# <a name="microsoft-365-network-connectivity-location-services"></a>Microsoft 365 Bağlantısı Konum Hizmetleri'ne Bağlan'a

Bu <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 yönetim merkezi</a> şimdi Ağ **Analizler ve** kiracı kiracıdan toplanan canlı performans ölçümleri olan performans Microsoft 365 gösterir. Bu ölçümler yalnızca kiracınız içinde yer alan yönetim kullanıcıları tarafından sınanabilirsiniz. Kurumsal ağ bağlantısı, ofis konum başına İnternet'e bir ağ çıkış konumu aracılığıyla tasarlanmıştır. Microsoft 365 bağlantı bu yönlendirmeyi kullanır ve ardından İnternet üzerinden Microsoft hizmet ön kapı sunucularına bağlanır. Office konumlarının belirlenmesi, bu ağ içgörülerini göster able olmanın anahtarıdır.

## <a name="location-in-network-measurements"></a>Ağ ölçülerinde konum

Kuruluş yöneticisi, bu özellik tarafından kullanılan ağ ölçülerine konum katılmayı kabul ediyor olabilir. Bu, her ofisin bulunduğu şehrin otomatik olarak bulunmasına olanak sağlar. Konum bilgileri hassas değildir ve 300 m'ye kadar yok ve şehre göre kategorilere ayrılmıştır. Bir cihaz üzerinde konum Windows geçirilirken, cihaz araç tepsisinde **bir** Konum KullanımDa simgesi gösterir. Yöneticiler, kullanıcılara bu simgenin görünümünü bildirmek istiyor olabilir. Bu işlemeyle, konum bir kişi veya cihazın konumu olarak değil, kuruluş ofisi konumu olarak kabul edilir. Ağ içgörüleri, bulunan bu ofis konumu şehirlerinde gösterebilirsiniz. Önerilerde daha doğru bir doğruluk için belirli ofis konumu adreslerini girebilirsiniz. Bunun yerine ağ içgörüleri bu konumlara bir araya gelecektir. Office konumlar 300 metreden yakın bir şekilde top kullanılamaz.

## <a name="location-in-the-microsoft-365-admin-center"></a>Yer Merkezi'Microsoft 365 Yönetici konum

Gezinti <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 yönetim merkezi</a>, Bing ofis konumlarının yerini göstermek için harita denetimleri kullanılır. Denetimler ayrıca seçili bir ofis konumu için ağ çevre topolojisini de gösterir. Yönetici ofis konumları için belirli adres ayrıntıları ekley Bing Haritalar, veri girişini kolaylaştırmak için adres önermek için de kullanılabilir.

## <a name="terms-of-use"></a>Kullanım Koşulları

Coğrafi kodlar Bing Haritalar, kodlar aracılığıyla sağlanan tüm içerikler yalnızca içeriğin sağ bulunduğu ürün içinde kullanılabilir. Bing Haritalar tarafından desteklenen <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 yönetim merkezi</a> Konum Hizmetleri özelliğini kullanımı,  <https://go.microsoft.com/?linkid=9710837> Microsoft Gizlilik Bildirimi'nde Bing Haritalar End-User Kullanım Koşulları'nda ve geçerli olan [Microsoft'un Kullanım Koşulları'nda yönetilir](https://go.microsoft.com/fwlink/?LinkID=248686).

Bing Haritalar aracılığıyla sağlanan bu özellik **TomTom tarafından da de desteklenen bir özelliktir**. TomTom'in ürünleri ve hizmetleri hakkında daha fazla bilgiyi burada bulunabilir [https://www.tomtom.com/legal](https://www.tomtom.com/legal).

## <a name="related-topics"></a>İlgili konular

[Ağ Merkezi'nde Microsoft 365 Yönetici bağlantısı](office-365-network-mac-perf-overview.md)

[Microsoft 365 performansı içgörüleri hakkında bilgi edinin](office-365-network-mac-perf-insights.md)

[Microsoft 365 değerlendirmesini geri ayanız](office-365-network-mac-perf-score.md)

[Microsoft 365 bağlantı testi Microsoft 365 yönetim merkezi](office-365-network-mac-perf-onboarding-tool.md)
