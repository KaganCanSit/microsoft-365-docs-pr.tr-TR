---
title: Tehdit ve Güvenlik Açığı Yönetimi'da etkinlik Tehdit ve Güvenlik Açığı Yönetimi
description: Etkinlik zaman çizelgesi, kuruluşa riskin nasıl gir olduğunu ve bunu azaltmak için hangi risk azaltmalarının olduğunu yorumlamanıza yardımcı olan bir risk haber akışıdır.
keywords: olay zaman çizelgesi, Uç nokta olay zaman çizelgesi için Microsoft Defender, Uç nokta tvm etkinliği zaman çizelgesi için Microsoft Defender, Tehdit ve Güvenlik Açığı Yönetimi için Microsoft Defender
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: m365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 3fe3139f12b863b54d336e52939ffbb3057df6b4
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63316009"
---
# <a name="event-timeline---threat-and-vulnerability-management"></a>Etkinlik zaman çizelgesi - Tehdit ve Güvenlik Açığı Yönetimi

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Microsoft Defender'ı mı deneyimliysiniz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-portaloverview-abovefoldlink)

Etkinlik zaman çizelgesi, yeni güvenlik açıkları veya açıkları ya da açıkları aracılığıyla kuruluşa risklerin nasıl gir açıkları olduğunu yorumlamanıza yardımcı olan bir risk haber akışıdır. Kuruluş riskini etkileyilebilecek olayları görüntüabilirsiniz. Örneğin, ortaya eklenen yeni güvenlik açıklarını, sömürülebilir hale gelen güvenlik açıklarını, bir exploit kit'ine eklenen açıkları ve daha fazlasını bulabilirsiniz.

Etkinlik zaman çizelgesi, büyük değişikliklerin nedenini belirlemenize yardımcı [olmak](tvm-exposure-score.md) için pozlama puanınızı ve Cihazlar [için Microsoft Güvenli](tvm-microsoft-secure-score-devices.md) Puanı'nın öyküünü de anlatır. Etkinlikler cihazlarınızı veya cihaz puanınızı etkiler. Önceliklendirmeli güvenlik önerilerine dayalı olarak nelerin düzeltilleri gerektiğini ele alarak maruz kalma [süresini azaltabilirsiniz](tvm-security-recommendation.md).

> [!TIP]
> Yeni güvenlik açığı olayları hakkında e-postalar almak için bkz. Uç Nokta için [Microsoft Defender'da güvenlik açığı e-posta bildirimlerini yapılandırma](configure-vulnerability-email-notifications.md)

## <a name="navigate-to-the-event-timeline-page"></a>Olay zaman çizelgesi sayfasına gidin

Ayrıca, Giriş panosundan üç [Tehdit ve Güvenlik Açığı Yönetimi vardır](tvm-dashboard-insights.md):

- **Kuruluş pozlama puanı kartı**: "Zaman içinde pozlama puanı" grafiğinde etkinlik noktaları üzerine gelin ve "Bugünden tüm etkinlikleri gör" öğesini seçin. Olaylar yazılım güvenlik açıklarını temsil eder.
- **Cihazlar için Microsoft Güvenli** Puan: "Zaman içinde cihazlar için puanınız" grafiğinde etkinlik noktaları üzerine gelin ve "Bugünden itibaren tüm etkinlikleri gör" öğesini seçin. Olaylar yeni yapılandırma değerlendirmelerini temsil ediyor.
- **En önemli etkinlik** kartı: En önemli etkinlikler tablonun altındaki "Daha fazla göster"i seçin. Kart, son 7 gün içinde en çok etkileyen üç olayları görüntüler. Etkin etkinlikler, etkinliğin çok fazla sayıda cihazı etkilediği veya kritik bir güvenlik açığı olması durumunda dahil olabilir.

### <a name="exposure-score-and-microsoft-secure-score-for-devices-graphs"></a>Pozlama puanı ve Cihazlar için Microsoft Güvenli Puan grafikleri

Tehdit ve Güvenlik Açığı Yönetimi panosunda, cihazlarınızı etkileyen en önemli yazılım açığı olaylarını görüntülemek için etkilenme puanı grafiğinin üzerine gelin. Puanınızı etkileyen yeni güvenlik yapılandırması değerlendirmelerini görüntülemek için Cihazlar için Microsoft Güvenli Puanı grafiğinin üzerine gelin.

Cihazlarınızı veya cihazlarınız için puanınızı etkileyen bir etkinlik yoksa, hiçbiri gösterilmez.

![Pozlama puanı vurgulu.](images/tvm-event-timeline-exposure-score350.png) 
![ Cihazlar için Microsoft Güvenli Puan üzerine gelin.](images/tvm-event-timeline-device-hover360.png)

### <a name="drill-down-to-events-from-that-day"></a>O günün olaylarından ayrıntıya gitme

Bu günden **itibaren tüm etkinlikleri göster'i seçmek** , sizi o gün için özel bir tarih aralığı olan Etkinlik zaman çizelgesi sayfasına alır.

![Olay zaman çizelgesi özel tarih aralığını seçti.](images/tvm-event-timeline-drilldown.png)

Tarih **aralığını başka** bir özel aralıkla veya önceden ayarlanmış bir zaman aralığıyla değiştirmek için Özel aralık'ı seçin.

![Olay zaman çizelgesi tarih aralığı seçenekleri.](images/tvm-event-timeline-dates.png)

## <a name="event-timeline-overview"></a>Etkinlik zaman çizelgesine genel bakış

Olay zaman çizelgesi sayfasında, bir olayla ilgili tüm gerekli bilgileri görüntüleyebilirsiniz.

Özellikler:

- Sütunları özelleştirme
- Olay türüne veya etkilenmiş cihazların yüzdesini filtreleme
- Sayfa başına 30, 50 veya 100 öğe görüntüleme

Sayfanın en üstünde yer alan iki büyük sayı, yeni güvenlik açıklarının ve açıklarından yararlanılabilir güvenlik açıklarının sayısını gösterir; olaylar değil. Bazı olaylarda birden çok güvenlik açıkları ve bazı güvenlik açıkları da birden fazla olay olabilir.

![Olay zaman çizelgesi sayfası.](images/tvm-event-timeline-overview-mixed-type.png)

### <a name="columns"></a>Sütunlar

- **Tarih**: ay, gün, yıl
- **Olay**: Bileşen, tür ve etkiyisi olan cihazların sayısı da içinde olmak üzere etkili bir olay
- **İlgili bileşen**: yazılım
- **Başlangıçta etkileyen cihazlar**: bu etkinlikte etkilenen cihazların sayısı ve yüzde değeri. Ayrıca, toplam cihaz sayısının dışında, başlangıçtan etkilenmiş cihazların yüzdesini filtreleebilirsiniz.
- **Şu anda etki edilen** cihazlar: bu etkinliğin şu anda etkilemektedir olduğu cihazların geçerli numarası ve yüzde değeri. Bu alanı, Sütunları özelleştir'i **seçerek bulabilirsiniz**.
- **Türler**: puanı etkileyen zaman damgalı olayları yansıtın. Filtre ed olabilir.
  - Exploit bir exploit kit'e eklendi
  - Exploit doğrulandı
  - Yeni kamu açıklarından yararlanma
  - Yeni güvenlik açığı
  - Yeni yapılandırma değerlendirmesi
- **Puan eğilimi**: açık puan eğilimi

### <a name="icons"></a>Simgeler

Etkinliklerin yanında aşağıdaki simgeler gösterilir:

- ![hata simgesine dokunun.](images/tvm-black-bug-icon.png) Yeni kamu açıklarından yararlanma
- ![rapor uyarı simgesi.](images/report-warning-icon.png) Yeni güvenlik açığı yayımlandı
- ![exploit kit.](images/bug-lightning-icon2.png) Exploit kit'te bulunan exploit
- ![uyarı simgesiyle birlikte hata simgesi.](images/bug-caution-icon2.png) Exploit verified

### <a name="drill-down-to-a-specific-event"></a>Belirli bir olayın detaya gitme

Bir etkinlik seçin ve cihazlarınızı etkileyen geçerli CVE'leri listeli bir uç uçarak görünür. Daha fazla CVR gösterebilir veya ilgili öneriyi görüntüabilirsiniz.

"Puan eğilimi"nin altındaki ok, bu etkinliğin kurumsal açık kalma puanınızı yükseltip yükseltemeyebileceklerini belirlemenize yardımcı olur. Daha yüksek pozlama puanı, cihazların açıklarından yararlanmaya karşı daha korumasız olduğu anlamına gelir.

![Etkinlik zaman çizelgesi uçarak çıkış.](images/tvm-event-timeline-flyout500.png)

Buradan, güvenlik **önerileri sayfasında İlgili güvenlik** önerisine git'i seçerek yeni yazılım güvenlik [açığının giderin önerisine bakın](tvm-security-recommendation.md). Güvenlik önerisinde açıklamayı ve güvenlik açığı ayrıntılarını okuduktan sonra bir düzeltme isteği gönderebilir ve düzeltme sayfasında [isteği izleyebilirsiniz](tvm-remediation.md).

## <a name="view-event-timelines-in-software-pages"></a>Yazılım sayfalarında Etkinlik zaman çizelgelerini görüntüleme

Yazılım sayfasını açmak için, açılır > "İlgili bileşen" adlı bölümde köprüye bağlı yazılım adını (Visual Studio 2017 gibi) seçin. [Yazılım sayfaları hakkında daha fazla bilgi](tvm-software-inventory.md#software-pages)

Belirli bir yazılımın tüm ayrıntılarının yer olduğu tam bir sayfa görüntülenir. Belirli bir yazılımla ilgili olayların zaman çizelgesini görmek için fareyi grafiğin üzerinde tutun.

![Etkinlik zaman çizelgesi grafiğinin yer alan yazılım sayfası.](images/tvm-event-timeline-software2.png)

Bu yazılımla ilgili tüm olayları görüntülemek için olay zaman çizelgesi sekmesine gidin. Ayrıca güvenlik önerilerini, bulunan güvenlik açıklarını, yüklü cihazları ve sürüm dağıtımını da görüntüebilirsiniz.

![Etkinlik zaman çizelgesi sekmesinin yer alan Yazılım sayfası.](images/tvm-event-timeline-software-pages.png)

## <a name="related-topics"></a>İlgili konular

- [Tehdit ve güvenlik açığı yönetimi genel bakış](next-gen-threat-and-vuln-mgt.md)
- [Pano](tvm-dashboard-insights.md)
- [Pozlama puanı](tvm-exposure-score.md)
- [Güvenlik önerileri](tvm-security-recommendation.md)
- [Güvenlik açıklarını düzeltme](tvm-remediation.md)
- [Yazılım envanteri](tvm-software-inventory.md)
