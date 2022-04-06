---
title: Jamf'te cihaz gruplarını Pro
description: macOS'ta Jamf'te Pro grupları Uç Nokta için Microsoft Defender ayarlay öğrenin
keywords: device, group, microsoft, defender, Uç Nokta için Microsoft Defender, mac, yükleme, dağıtma, kaldırma, intune, jamfpro, macos, catalina, mojave, high sierra
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
ms.openlocfilehash: c22a1a68af2722e6b17d155a37632c1f6417b605
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64471769"
---
# <a name="set-up-microsoft-defender-for-endpoint-on-macos-device-groups-in-jamf-pro"></a>Jamf Uç Nokta için Microsoft Defender macOS cihaz gruplarında kullanıcı Pro

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta için Microsoft Defender Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta için Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Defender'ı deneyimli yapmak mı istiyor musunuz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)

Cihaz gruplarını Grup ilkesi kuruluş birimi (OU'lar), Microsoft Endpoint Configuration Manager'ın cihaz koleksiyonu ve Intune gruplarına benzer şekilde ayarlayın.

1. Statik Bilgisayar **Grupları'ne gidin**.

2. **Yeni**'yi seçin. 

   :::image type="content" source="images/jamf-pro-static-group.png" alt-text="Jamf Pro1 sayfası" lightbox="images/jamf-pro-static-group.png":::

3. Bir görünen ad girin ve Kaydet'i **seçin**.

   :::image type="content" source="images/jamfpro-machine-group.png" alt-text="Jamf Pro2 sayfası" lightbox="images/jamfpro-machine-group.png":::

4. Şimdi, Statik Bilgisayar Grupları **altında Contoso'nun** Makine **Grubu'nun olduğunu görüyorsunuz**.

   :::image type="content" source="images/contoso-machine-group.png" alt-text="Jamf Pro3 sayfası" lightbox="images/contoso-machine-group.png":::

## <a name="next-step"></a>Sonraki adım
- [Jamf Uç Nokta için Microsoft Defender'da macOS ilkeleri hakkında bilgi Pro](mac-jamfpro-policies.md)
