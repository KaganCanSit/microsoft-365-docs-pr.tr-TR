---
title: Mac'te Uç Nokta için Microsoft Defender lisans sorunlarını giderme
description: Mac'te Uç Nokta için Microsoft Defender'daki lisans sorunlarını giderin.
keywords: microsoft, defender, Uç Nokta için Microsoft Defender, mac, performans
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
ms.openlocfilehash: b0a328ffeee6ee5796cb92f00b8491b257e88a65
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/12/2022
ms.locfileid: "63011853"
---
# <a name="troubleshoot-license-issues-for-microsoft-defender-for-endpoint-on-macos"></a>macOS'ta Uç Nokta için Microsoft Defender lisans sorunlarını giderme

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:**

- [macOS'ta](microsoft-defender-endpoint-mac.md)
 Uç Nokta için Microsoft Defender [Uç Nokta Planı 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
 için Microsoft Defender [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Microsoft Defender'ı mı deneyimliysiniz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[macOS'ta Uç Nokta için Microsoft Defender](microsoft-defender-endpoint-mac.md) ve El ile dağıtım [](mac-install-manually.md) testi veya Kavram Kanıtı (PoC) üzerinden ilerlerken aşağıdaki hatayı alabilirsiniz:

![Lisans hatası görüntüsü.](images/no-license-found.png)

**İleti:** 

Lisans bulunamadı

Görünüşe göre, kuruma bu abonelik için Microsoft 365 Kurumsal yok.

Yardım için yöneticinize başvurun.

**Neden:** 

MacOS paketinde ("Yükleme paketini indir") Uç Nokta için Microsoft Defender'ı dağıttınız ve/veya yüklemişsiniz, ancak yapılandırma betiğini çalıştırmamış ("Ekleme paketini indir") veya kullanıcıya lisans atamamışsınız olabilir.

MacOS aracısı için Microsoft Defender Uç Nokta güncel değilse de bu hatayla karşılaşebilirsiniz. 


**Çözüm:**

Burada MicrosoftDefenderATPOnboardingMacOs.py yönergeleri izleyin: [İstemci yapılandırması](mac-install-manually.md#client-configuration)

macOS üzerinde Uç Nokta için Microsoft Defender'ın güncel olmadığınız senaryolarda aracıyı güncelleştirmeniz gerekir. 
