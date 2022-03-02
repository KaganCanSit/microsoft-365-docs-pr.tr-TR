---
title: Uç Nokta için Microsoft Defender'da web'e gözatma güvenliğini izleme
description: Web'de gözatma güvenliğini izlemek üzere Uç Nokta için Microsoft Defender'da web korumasını kullanma
keywords: web koruması, web tehdit koruması, web'e gözatma, izleme, raporlar, kartlar, etki alanı listesi, güvenlik, kimlik avı, kötü amaçlı yazılım, exploit, web siteleri, ağ koruması, Edge, Internet Explorer, Chrome, Firefox, web tarayıcısı
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 6d10354f68dd5ba26db7f4260425559167c8888c
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2021
ms.locfileid: "63008090"
---
# <a name="monitor-web-browsing-security"></a>Web'e gözatma güvenliğini izleme

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Microsoft Defender'ı mı deneyimliysiniz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-main-abovefoldlink&rtc=1)

Web koruması, portalda Web koruması için raporlar ve Web > altında yer alan raporlar **aracılığıyla** Microsoft 365 Defender sağlar. Raporda, web tehdit algılama istatistiklerini sağlayan kartlar yer almaktadır.

- **Web tehdit** koruması zamanla algılamaları - Bu popüler kart, seçilen dönem boyunca tür tarafından algılanan web tehditlerinin sayısını görüntüler (Son 30 gün, Son 3 ay, Son 6 ay)

  :::image type="content" alt-text="Zaman içinde web tehdit koruma algılamalarını gösteren kartın resmi." source="images/wtp-blocks-over-time.png" lightbox="images/wtp-blocks-over-time.png":::

- **Web tehdit koruması özeti** - Bu kart son 30 gün içinde toplam web tehdit algılamalarını görüntüler ve farklı türlerde web tehditlerinin dağılımını gösterir. Dilim seçerek, kötü amaçlı veya istenmeyen web siteleriyle bulunan etki alanlarının listesi açılır.

  :::image type="content" alt-text="Web tehdit koruması özetini gösteren kartın resmi." source="images/wtp-summary.png" lightbox="images/wtp-summary.png":::

> [!NOTE]
> Engelin kartlara veya etki alanı listesine yansıtılamadan önce 12 saat kadar sürebilir.

## <a name="types-of-web-threats"></a>Web tehdit türleri

Web koruması kötü amaçlı ve istenmeyen web sitelerini aşağıdaki gibi kategorilere ayırabilir:

- **Kimlik avı** - kullanıcıları kimlik bilgilerini ve diğer hassas bilgileri bölmeleri için kandırmak üzere tasarlanmış sahte web formları ve diğer kimlik avı mekanizmaları içeren web siteleri
- **Kötü amaçlı** - kötü amaçlı yazılım ve açıklardan yararlanma kodu barındırılan web siteleri
- **Özel gösterge** - URL'leri veya etki alanlarını engellemeye yönelik özel gösterge [listeniz'e ekleyttikleri web](manage-indicators.md) siteleri

## <a name="view-the-domain-list"></a>Etki alanı listesini görüntüleme

Etki Alanları sayfasını açmak için Web tehdit koruması **özet kartında belirli bir** web tehdit **kategorisi** seçin. Bu sayfada, bu tehdit kategorisi altındaki etki alanlarının listesi görüntülenir. Sayfa, her etki alanı için aşağıdaki bilgileri sağlar:

- **Erişim sayısı** - etki alanındaki URL'ler için istek sayısı
- **Bloklar** - isteklerin kaç kez engellenmiş olduğu
- **Erişim eğilimi** - erişim deneme sayısının değişmesi
- **Tehdit kategorisi** - web tehdit türü
- **Cihazlar** - erişim denemeleri olan cihaz sayısı

Bir etki alanındaki URL'lere erişmeye çalışan cihazların listesini ve URL'lerin listesini görüntülemek için bir etki alanı seçin.

## <a name="related-topics"></a>İlgili konular

- [Web korumasına genel bakış](web-protection-overview.md)
- [Web içeriği filtreleme](web-content-filtering.md)
- [Web tehdit koruması](web-threat-protection.md)
- [Web tehditlerine yanıt verme](web-protection-response.md)