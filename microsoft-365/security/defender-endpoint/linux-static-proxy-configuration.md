---
title: Linux statik ara sunucu bulma üzerinde Uç Nokta için Microsoft Defender
ms.reviewer: ''
description: Statik proxy bulma için Linux'ta Uç Nokta için Microsoft Defender'ın nasıl yapılandırıldığından emin olun.
keywords: microsoft, defender, Uç Nokta için Microsoft Defender, linux, yükleme, proxy
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
ms.openlocfilehash: 3b5061f0230a9704cb0fb9b80752c4d38954ad12
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2021
ms.locfileid: "62997575"
---
# <a name="configure-microsoft-defender-for-endpoint-on-linux-for-static-proxy-discovery"></a>Statik proxy bulma için Linux'ta Uç Nokta için Microsoft Defender'ı yapılandırma

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Defender'ı deneyimli yapmak mı istiyor musunuz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)

Uç Nokta için Microsoft Defender ortam değişkensini kullanarak bir ara sunucu `HTTPS_PROXY` bu olabilir. Bu ayar **hem yükleme sırasında** hem de ürün yüklendikten sonra yapılandırıldı.

## <a name="installation-time-configuration"></a>Yükleme süresi yapılandırması

Yükleme sırasında, ortam `HTTPS_PROXY` değişkeninin paket yöneticisine geçir olması gerekir. Paket yöneticisi bu değişkeni aşağıdaki yöntemlerden herhangi birini okuyabilir:

- Değişken `HTTPS_PROXY` aşağıdaki satırla `/etc/environment` tanımlanır:

  ```bash
  HTTPS_PROXY="http://proxy.server:port/"
  ```

- Değişken `HTTPS_PROXY` paket yöneticisi genel yapılandırmasında tanımlanır. Örneğin, Ubuntu 18.04'te aşağıdaki satırı şu satıra eklersiniz `/etc/apt/apt.conf.d/proxy.conf`:

  ```bash
  Acquire::https::Proxy "http://proxy.server:port/";
  ```

  > [!CAUTION]
  > Yukarıdaki iki yöntemin, sisteminiz üzerindeki diğer uygulamalar için kullanabileceğiniz proxy'nin tanımlanana kadar açık olduğunu unutmayın. Bu yöntemi dikkatli kullanın veya bunun genel bir genel yapılandırma olması için uygun olması gerekir.

- Değişken `HTTPS_PROXY` , yükleme veya kaldırma komutlarının hazırlayın. Örneğin, APT paket yöneticisiyle, Uç Nokta için Microsoft Defender'ı yüklerken değişkeni aşağıdaki gibi hazırlayın:

  ```bash
  HTTPS_PROXY="http://proxy.server:port/" apt install mdatp
  ```

  > [!NOTE]
  > Ortam değişken tanımı ile apt arasına sudo ekleme, aksi takdirde değişken yayılmaz.

Kaldırma `HTTPS_PROXY` sırasında ortam değişkeni de benzer şekilde tanımlanabilir.

Proxy gerekli ancak yapılandırılmazsa, yükleme ve kaldırma işleminin başarısız olamayacaklarını unutmayın. Öte yandan, telemetri gönderilmez ve ağ zaman aşımı nedeniyle işlem çok daha uzun sürebilir.

## <a name="post-installation-configuration"></a>Yükleme sonrası yapılandırması

Yüklemeden sonra `HTTPS_PROXY` , ortam değişkeni Uç nokta için Defender hizmet dosyasında tanımlanmalıdır. Bunu yapmak için , çalıştırın `sudo systemctl edit --full mdatp.service`.
Ardından, değişkeni hizmete iki şekilde yayabilirsiniz:

- Satırın sıkıştırın ve `#Environment="HTTPS_PROXY=http://address:port"` statik proxy adresinizi belirtin.

- Satır ekleyin `EnvironmentFile=/path/to/env/file`. Bu yol, aşağıdaki `/etc/environment` satırı eklemeniz gereken özel bir dosyayı işaret ediyor olabilir:

  ```bash
  HTTPS_PROXY="http://proxy.server:port/"
  ```

Değiştirdikten sonra `mdatp.service`, dosyayı kaydedin ve değişikliklerin aşağıdaki komutlar kullanılarak uygulananı için hizmeti yeniden başlatın:

```bash
sudo systemctl daemon-reload; sudo systemctl restart mdatp
```
