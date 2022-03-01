---
title: Mac'te Uç Nokta için Microsoft Defender ile istenmeyen olabilecek uygulamaları algılama ve engelleme
description: macOS'ta Uç Nokta için Microsoft Defender'ı kullanarak olası İstenmeyen Uygulamaları (PUA) algıla ve engelle.
keywords: microsoft, defender, Endpoint için Microsoft Defender, mac, pua, pus
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
ms.openlocfilehash: a0fb8e19dd573da67936892c81cd515b463a7cba
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/12/2022
ms.locfileid: "63011855"
---
# <a name="detect-and-block-potentially-unwanted-applications-with-microsoft-defender-for-endpoint-on-macos"></a>macOS'ta Uç Nokta için Microsoft Defender ile istenmeyen olabilecek uygulamaları algılama ve engelleme

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Microsoft Defender'ı mı deneyimliysiniz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

macOS üzerinde Uç Nokta için Microsoft Defender'daki istenmeyen uygulama (PUA) koruma özelliği ağ bağlantı noktalarında PUA dosyalarını algılanabilir ve engelleyebilir.

Bu uygulamalar virüs, kötü amaçlı yazılım veya diğer tehdit türleri olarak kabul alınmaz, ancak performanslarını veya kullanımını olumsuz etkileyen uç noktalar üzerinde eylemler gerçekleştirebilir. PUA, kötü bir üne sahip olduğu kabul edilen uygulamalara da başvurur.

Bu uygulamalar, ağlarının kötü amaçlı yazılımdan bulaşma riskini artırabilir, kötü amaçlı yazılım bulaşmalarının belirlenmesini daha zorlaştırabilir ve uygulamaları temizlerken IT kaynaklarını israf edebilir.

## <a name="how-it-works"></a>Nasıl çalışır?

macOS'ta Uç Nokta için Microsoft Defender PUA dosyalarını algılanabilir ve bildirebilirsiniz. Engelleme modunda yapılandırıldığında, PUA dosyaları karantinaya taşınır.

Bir uç noktada PUA algılandığında, bildirimlerin devre dışı bırakılamadıkça macOS'ta Uç Nokta için Microsoft Defender kullanıcıya bir bildirim sunar. Tehdit adı "Uygulama" sözcüğü içerir.

## <a name="configure-pua-protection"></a>PUA korumasını yapılandırma

macOS üzerinde Uç Nokta için Microsoft Defender'da PUA koruması aşağıdaki yöntemlerden biri ile yalnabilirsiniz:

- **Kapalı**: PUA koruması devre dışı bırakılır.
- **Denetim**: PUA dosyaları ürün günlüklerine bildiriliyor ancak portalda Microsoft 365 Defender değil. Kullanıcıya herhangi bir bildirim olmaz ve ürün hiçbir işlemde yoktur.
- **Engelle**: PUA dosyaları ürün günlüklerine ve portala Microsoft 365 Defender. Kullanıcıya bir bildirim ve ürün tarafından işlem yapıldı bildirimini alır.

> [!WARNING]
> Varsayılan olarak, PUA koruması **Denetim modunda yapılandırılır** .

PUA dosyalarının komut satırı veya yönetim konsolundan nasıl işleniyor olduğunu yapılandırabilirsiniz.

### <a name="use-the-command-line-tool-to-configure-pua-protection"></a>PUA korumasını yapılandırmak için komut satırı aracını kullanın:

Terminal'de PUA korumasını yapılandırmak için aşağıdaki komutu yürütün:

```bash
mdatp threat policy set --type potentially_unwanted_application --action [off|audit|block]
```

### <a name="use-the-management-console-to-configure-pua-protection"></a>PUA korumasını yapılandırmak için yönetim konsolunu kullanın:

Kurumunuzun içinde, aynı diğer ürün ayarlarının yapılandırılma örneğine benzer şekilde, JAMF veya Intune gibi bir yönetim konsolundan PUA korumasını yapılandırabilirsiniz. Daha fazla bilgi için macOS [üzerinde Uç nokta](mac-preferences.md#threat-type-settings) için Microsoft Defender tercihlerini ayarlama konusunun [Tehdit türü ayarları bölümüne](mac-preferences.md) bakın.

## <a name="related-topics"></a>İlgili konular

- [macOS'ta Uç Nokta için Microsoft Defender tercihlerini ayarlama](mac-preferences.md)
