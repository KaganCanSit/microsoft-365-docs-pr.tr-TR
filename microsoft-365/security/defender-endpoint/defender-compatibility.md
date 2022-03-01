---
title: Virüsten koruma çözümü ile Uç Nokta için Defender uyumluluğu
description: Uç nokta için Microsoft Defender Windows Defender nasıl çalıştığını öğrenin. Ayrıca, üçüncü taraf kötü amaçlı yazılımdan koruma istemcisi kullanılırken Uç Nokta için Defender'ın nasıl çalıştığını da öğrenin.
keywords: windows Defender uyumluluğu, Defender, Uç Nokta için Microsoft Defender, uç nokta için Defender, virüsten koruma, mde
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
ms.date: 05/06/2021
ms.technology: mde
ms.openlocfilehash: a8384ed28e8c65871f61241dc522461390106be0
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2021
ms.locfileid: "62998072"
---
# <a name="antivirus-solution-compatibility-with-microsoft-defender-for-endpoint"></a>Uç nokta için Microsoft Defender ile virüsten koruma çözümü uyumluluğu

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Defender'ı deneyimli yapmak mı istiyor musunuz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-defendercompat-abovefoldlink)

Uç nokta aracısı için Microsoft Defender Microsoft Defender Virüsten Koruma tarama gibi bazı özelliklere bağlı olarak değişir.

> [!IMPORTANT]
> Uç Nokta için Defender Microsoft Defender Virüsten Koruma Dışlamalar ayarlarına uymaz.

Etkin kötü amaçlı yazılımdan koruma olsa da, Uç nokta cihazları için Defender Microsoft Defender Virüsten Koruma Güvenlik zekası güncelleştirmelerini yapılandırmanız gerekir. Daha fazla bilgi için bkz[. Güncelleştirmeleri Microsoft Defender Virüsten Koruma ve taban çizgilerini uygulama](manage-updates-baselines-microsoft-defender-antivirus.md).

Yerleşik bir cihaz üçüncü taraf kötü amaçlı yazılımdan koruma istemcisi tarafından korunuyorsa, Microsoft Defender Virüsten Koruma böyle bir uç noktada pasif moduna girer.

Microsoft Defender Virüsten Koruma almaya devam edecektir ve *mspeng.exe* işlemi çalışan bir hizmet olarak listelenir. Ancak, taramalar gerçekleştirmez ve çalışan üçüncü taraf kötü amaçlı yazılımdan koruma istemcisini değiştirmez.

Microsoft Defender Virüsten Koruma arabirimi devre dışı bırakılır. Cihaza bağlı kullanıcılar isteğe bağlı taramalar Microsoft Defender Virüsten Koruma veya seçeneklerin çoğunu yapılandırmak için e-posta oturumlarını kullanamazsanız.

Daha fazla bilgi için uç [nokta uyumluluğu Microsoft Defender Virüsten Koruma Defender'ın nasıl sıralanmıştır? başlığına bakın](microsoft-defender-antivirus-compatibility.md).
