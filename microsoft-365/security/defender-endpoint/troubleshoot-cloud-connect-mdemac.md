---
title: macOS'ta Uç Nokta için Microsoft Defender'da bulut bağlantı sorunlarını giderme
description: Bu konu başlığında, macOS üzerinde Uç Nokta için Microsoft Defender'da bulut bağlantısı sorunlarının nasıl giderilir
keywords: microsoft, defender, Endpoint için Microsoft Defender, mac, yükleme, dağıtma, kaldırma, intune, jamf, macos, catalina, mojave, high sierra
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: lovina-saldanha
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: m365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 677737f530e35ed52a2a1f3fe7a8d6f18c26e7b6
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63326576"
---
# <a name="troubleshoot-cloud-connectivity-issues-for-microsoft-defender-for-endpoint-on-macos"></a>macOS'ta Uç Nokta için Microsoft Defender'da bulut bağlantı sorunlarını giderme

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

**Platform** macOS

Bu konu başlığında, macOS üzerinde Uç Nokta için Microsoft Defender'da bulut bağlantısı sorunlarını giderme başlığı açıklanmıştır.

## <a name="run-the-connectivity-test"></a>Bağlantı testini çalıştırma
Mac'te Uç Nokta için Defender'ın geçerli ağ ayarlarıyla buluta iletişim kurap kura geçeylene kadar test etmek için, komut satırdan bir bağlantı testi çalıştırın:

```Bash
mdatp connectivity test
```

beklenen çıkış:
```Bash
Testing connection with https://cdn.x.cp.wd.microsoft.com/ping ... [OK]
Testing connection with https://eu-cdn.x.cp.wd.microsoft.com/ping ... [OK]
Testing connection with https://wu-cdn.x.cp.wd.microsoft.com/ping ... [OK]
Testing connection with https://x.cp.wd.microsoft.com/api/report ... [OK]
Testing connection with https://winatp-gw-cus.microsoft.com/test ... [OK]
Testing connection with https://winatp-gw-eus.microsoft.com/test ... [OK]
Testing connection with https://winatp-gw-weu.microsoft.com/test ... [OK]
Testing connection with https://winatp-gw-neu.microsoft.com/test ... [OK]
Testing connection with https://winatp-gw-ukw.microsoft.com/test ... [OK]
Testing connection with https://winatp-gw-uks.microsoft.com/test ... [OK]
Testing connection with https://eu-v20.events.data.microsoft.com/ping ... [OK]
Testing connection with https://us-v20.events.data.microsoft.com/ping ... [OK]
Testing connection with https://uk-v20.events.data.microsoft.com/ping ... [OK]
Testing connection with https://v20.events.data.microsoft.com/ping ... [OK]
```

Bağlantı testi başarısız olursa, cihazın İnternet erişimi olup denetleyin ve ürün için gereken uç [](microsoft-defender-endpoint-mac.md#network-connections) noktalardan herhangi biri bir ara sunucu veya güvenlik duvarı tarafından engellenmişse.

35 veya 60 hatasını hataları sertifika sabitleme reddetmesi gösterir ve bu da SSL veya HTTPS incelemesinde olası bir sorunu gösterir. SSL denetleme yapılandırmasıyla ilgili aşağıdaki yönergelere bakın.

## <a name="troubleshooting-steps-for-environments-without-proxy-or-with-proxy-autoconfig-pac-or-with-web-proxy-autodiscovery-protocol-wpad"></a>Ara sunucu olmayan veya Proxy otomatik yapılandırması (PAC) veya Web Proxy Otomatik Bulma Protokolü (WPAD) ile ortamlar için sorun giderme adımları
Proxy olmayan veya Proxy otomatik yapılandırması (PAC) veya Web Proxy Otomatik Bulma Protokolü (WPAD) ile bir ortamda bağlantının engel olmadığını test etmek için aşağıdaki yordamı kullanın.

Bir ara sunucu veya güvenlik duvarı anonim trafiği engelliyorsa, anonim trafiğin daha önce listelenen URL'lerde izin verildiğindan emin olun.

> [!WARNING]
> Kimliği doğrulanmışxler desteklanmaz. Yalnızca PAC, WPAD veya statik ara sunucu kullanılırken emin olma. SSL incelemesi ve kesişme prox'leri güvenlik nedenleriyle de desteklanmaz. macOS'ta Uç Nokta için Microsoft Defender'dan kesme noktası olmadan ilgili URL'lere doğrudan geçmek üzere SSL incelemesi ve proxy sunucunuz için bir özel durum yapılandırın. Kesme noktası sertifikanızı genel mağazaya eklemek kesme noktası engellemesine izin vermez.
Bağlantının engel olmadığını test etmek için: Mac veya Safari https://x.cp.wd.microsoft.com/api/report https://cdn.x.cp.wd.microsoft.com/pingiçin Microsoft Edge ve .

İsteğe bağlı olarak, Terminal'de aşağıdaki komutu çalıştırın:

```Bash
curl -w ' %{url_effective}\n' 'https://x.cp.wd.microsoft.com/api/report' 'https://cdn.x.cp.wd.microsoft.com/ping' 
```

Bu komutun çıkışı aşağıdakine benzer olmalı:
```bash
OK https://x.cp.wd.microsoft.com/api/report
OK https://cdn.x.cp.wd.microsoft.com/ping
```
