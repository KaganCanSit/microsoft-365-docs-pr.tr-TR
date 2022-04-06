---
title: Mac'te Uç Nokta için Microsoft Defender lisans sorunlarını giderme
description: Mac'te Uç Nokta için Microsoft Defender sorunlarını giderin.
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
ms.openlocfilehash: 35b77183ee9ceb00569c956d30debb0dd61e63f7
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64471747"
---
# <a name="troubleshoot-license-issues-for-microsoft-defender-for-endpoint-on-macos"></a>macOS'ta Uç Nokta için Microsoft Defender sorunları giderme

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:**

- [Uç Nokta için Microsoft Defender os'ta Uç Nokta için Microsoft Defender](microsoft-defender-endpoint-mac.md)
 [Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
 [Uç Nokta için Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Bu deneyimi Uç Nokta için Microsoft Defender? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[macOS ve El ile Uç Nokta için Microsoft Defender testi veya](microsoft-defender-endpoint-mac.md) Kavram Kanıtı (PoC[](mac-install-manually.md)) üzerinden çalışırken aşağıdaki hatayı alabilirsiniz:

:::image type="content" source="images/no-license-found.png" alt-text="Lisans hatası" lightbox="images/no-license-found.png":::

**İleti:** 

Lisans bulunamadı

Görünüşe göre, kuruma bu abonelik için Microsoft 365 Kurumsal yok.

Yardım için yöneticinize başvurun.

**Neden:** 

Uç Nokta için Microsoft Defender'i macOS paketine ("Yükleme paketini indir") dağıttınız ve/veya yüklemişsinizdir, ancak yapılandırma betiğini çalıştırmamış ("Ekleme paketini indir") veya kullanıcıya lisans atamamış olabilirsiniz.

MacOS aracısı üzerinde Uç Nokta için Microsoft Defender güncel değilse bu hatayla da karşılaşebilirsiniz. 


**Çözüm:**

Burada MicrosoftDefenderATPOnboardingMacOs.py yönergeleri izleyin: [İstemci yapılandırması](mac-install-manually.md#client-configuration)

macOS'Uç Nokta için Microsoft Defender güncel olmayan senaryolarda aracıyı güncelleştirmeniz gerekir. 
