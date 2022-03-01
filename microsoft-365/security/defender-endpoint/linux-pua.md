---
title: Linux'ta Uç Nokta için Microsoft Defender ile istenmeyen olabilecek uygulamaları algılama ve engelleme
description: Linux'ta Uç Nokta için Microsoft Defender'ı kullanarak olası İstenmeyen Uygulamaları (PUA) algıla ve engelle.
keywords: microsoft, defender, Endpoint için Microsoft Defender, linux, pua, pus
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 03c6f64e7272706262ef622a173e58260468e01b
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2021
ms.locfileid: "62997529"
---
# <a name="detect-and-block-potentially-unwanted-applications-with-microsoft-defender-for-endpoint-on-linux"></a>Linux'ta Uç Nokta için Microsoft Defender ile istenmeyen olabilecek uygulamaları algılama ve engelleme

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Defender'ı deneyimli yapmak mı istiyor musunuz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)

Linux'ta Uç Nokta için Defender'daki istenmeyen uygulama (PUA) koruma özelliği ağ bağlantı noktalarında PUA dosyalarını algılanabilir ve engelleyebilir.

Bu uygulamalar virüs, kötü amaçlı yazılım veya diğer tehdit türleri olarak kabul alınmaz, ancak performanslarını veya kullanımını olumsuz etkileyen uç noktalar üzerinde eylemler gerçekleştirebilir. PUA, kötü bir üne sahip olduğu kabul edilen uygulamalara da başvurur.

Bu uygulamalar, ağlarının kötü amaçlı yazılımdan bulaşma riskini artırabilir, kötü amaçlı yazılım bulaşmalarının belirlenmesini daha zorlaştırabilir ve uygulamaları temizlerken IT kaynaklarını israf edebilir.

## <a name="how-it-works"></a>Nasıl çalışır?

Linux'ta Uç Nokta için Defender PUA dosyalarını algılanabilir ve bildirebilirsiniz. Engelleme modunda yapılandırıldığında, PUA dosyaları karantinaya taşınır.

Bir uç noktada PUA algılandığında Linux'ta Uç Nokta için Defender tehdit geçmişinde bulaşmanın kaydını tutar. Geçmiş, portalda Microsoft 365 Defender komut satırı aracı aracılığıyla `mdatp` görselleştirilmiş olabilir. Tehdit adı "Uygulama" sözcüğü içerir.

## <a name="configure-pua-protection"></a>PUA korumasını yapılandırma

Linux'ta Uç Nokta için Defender'daki PUA koruması aşağıdaki yöntemlerden birini yapılandırabilirsiniz:

- **Kapalı**: PUA koruması devre dışı bırakılır.
- **Denetim**: PUA dosyaları ürün günlüklerine bildiriliyor, ancak Microsoft 365 Defender. Bulaşma kaydı tehdit geçmişinde depolandığı gibi ürünle ilgili hiçbir işlem de alınmaz.
- **Engelle**: PUA dosyaları ürün günlüklerine ve dosya dosyaları Microsoft 365 Defender. Bulaşma kaydı tehdit geçmişinde depolanır ve ürün tarafından işlem alınır.

> [!WARNING]
> Varsayılan olarak, PUA koruması **Denetim modunda yapılandırılır** .

PUA dosyalarının komut satırı veya yönetim konsolundan nasıl işleniyor olduğunu yapılandırabilirsiniz.

### <a name="use-the-command-line-tool-to-configure-pua-protection"></a>PUA korumasını yapılandırmak için komut satırı aracını kullanın:

Terminal'de PUA korumasını yapılandırmak için aşağıdaki komutu yürütün:

```bash
mdatp threat policy set --type potentially_unwanted_application --action [off|audit|block]
```

### <a name="use-the-management-console-to-configure-pua-protection"></a>PUA korumasını yapılandırmak için yönetim konsolunu kullanın:

Kurumunuzun içinde, diğer ürün ayarlarının yapılandırılma örneğine benzer şekilde, Şirket konsolundan PUA korumasını Yapılandırabilirsiniz . Daha fazla bilgi için [Linux'ta Uç nokta için](linux-preferences.md#threat-type-settings) Defender tercihlerini ayarlama makalesinde Tehdit [türü ayarları bölümüne](linux-preferences.md) bakın.

## <a name="related-articles"></a>İlgili makaleler

- [Linux'ta Uç Nokta için Defender tercihlerini ayarlama](linux-preferences.md)
