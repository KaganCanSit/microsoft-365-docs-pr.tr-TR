---
title: Linux'ta Uç Nokta için Microsoft Defender'da bulut bağlantı sorunlarını giderme
ms.reviewer: ''
description: Linux'ta Uç Nokta için Microsoft Defender'da bulut bağlantı sorunlarını gidermeyi öğrenin
keywords: microsoft, defender, Uç Nokta için Microsoft Defender, linux, bulut, bağlantı, iletişim
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
ms.openlocfilehash: a4c279dff6fa5a5c85a2f65144a301dde75a1615
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2021
ms.locfileid: "62997452"
---
# <a name="troubleshoot-cloud-connectivity-issues-for-microsoft-defender-for-endpoint-on-linux"></a>Linux'ta Uç Nokta için Microsoft Defender'da bulut bağlantı sorunlarını giderme

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Defender'ı deneyimli yapmak mı istiyor musunuz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)

## <a name="run-the-connectivity-test"></a>Bağlantı testini çalıştırma

Linux'ta Uç Nokta için Defender'ın geçerli ağ ayarlarıyla buluta iletişim kurap kuraya geçene kadar test etmek için, komut satırdan bir bağlantı testi çalıştırın:

```bash
mdatp connectivity test
```

beklenen çıkış:

```output
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

Bağlantı testi başarısız olursa, cihazın İnternet erişimi olup denetleyin ve ürün için gereken uç [](microsoft-defender-endpoint-linux.md#network-connections) noktalardan herhangi biri bir ara sunucu veya güvenlik duvarı tarafından engellenmişse.

35 veya 60 kıvrıklık hataları sertifika sabitleme reddetmesi gösterir. Lütfen bağlantının SSL veya HTTPS denetimi altında olup olduğunu kontrol edin. Varsa, izin listesine Uç Nokta için Microsoft Defender ekleyin.

## <a name="troubleshooting-steps-for-environments-without-proxy-or-with-transparent-proxy"></a>Proxy olmayan veya saydam ara sunucu olan ortamlar için sorun giderme adımları

Proxy veya saydam proxy olmayan bir ortamda bağlantının engel olmadığını test etmek için terminalde aşağıdaki komutu çalıştırın:

```bash
curl -w ' %{url_effective}\n' 'https://x.cp.wd.microsoft.com/api/report' 'https://cdn.x.cp.wd.microsoft.com/ping'
```

Bu komutun çıkışı aşağıdakine benzer olmalı:

```Output
OK https://x.cp.wd.microsoft.com/api/report
OK https://cdn.x.cp.wd.microsoft.com/ping
```

## <a name="troubleshooting-steps-for-environments-with-static-proxy"></a>Statik proxy ile ortamlar için sorun giderme adımları

> [!WARNING]
> PAC, WPAD ve kimliği doğrulanmışxler desteklanmaz. Yalnızca statik ara sunucu veya saydam proxy'nin kullanılıyor olduğundan emin olun.
>
> SSL incelemesi ve kesişme prox'leri güvenlik nedenleriyle de desteklanmaz. Linux'ta Uç Nokta için Defender'dan kesme noktası olmadan ilgili URL'lere doğrudan veri geçecek SSL incelemesi ve ara sunucu için bir özel durum yapılandırın. Kesme noktası sertifikanızı genel mağazaya eklemek kesme noktası engellemesine izin vermez.

Statik bir ara sunucu gerekli ise yukarıdaki komuta bir proxy parametresi ekleyin (burada proxy `proxy_address:port` adresine ve bağlantı noktasına karşılık gelen parametre):

```bash
curl -x http://proxy_address:port -w ' %{url_effective}\n' 'https://x.cp.wd.microsoft.com/api/report' 'https://cdn.x.cp.wd.microsoft.com/ping'
```

Dosyada yapılandırılan proxy adresini ve bağlantı noktasını kullanmaya emin `/lib/system/system/mdatp.service` olun. Yukarıdaki komutlarda hata varsa proxy yapılandırmanızı denetleyin.

mdatp proxy'sini ayarlamak için aşağıdaki komutu kullanın:

```bash
mdatp config proxy set --value http://address:port 
```


Başarılı oldu sonra, komut satırına gelen başka bir bağlantı sınaması sınayın:

```bash
mdatp connectivity test
```

Sorun devam ederse müşteri desteğine başvurun.

## <a name="resources"></a>Kaynaklar

- Ürünü statik proxy'yi kullanmak üzere yapılandırma hakkında daha fazla bilgi için bkz. Statik proxy bulma için Uç Nokta için [Microsoft Defender'ı yapılandırma](linux-static-proxy-configuration.md).
