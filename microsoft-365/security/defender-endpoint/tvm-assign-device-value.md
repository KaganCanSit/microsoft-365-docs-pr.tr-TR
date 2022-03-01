---
title: Cihaz değeri atama - Tehdit ve Güvenlik Açığı Yönetimi
description: Varlık öncelikleri arasında ayrımnıza yardımcı olması için bir cihaza düşük, normal veya yüksek değer atamayı öğrenin.
keywords: Uç nokta cihaz değeri, cihaz Tehdit ve Güvenlik Açığı Yönetimi, yüksek değerli cihazlar, cihaz değeri pozlama puanı için Microsoft Defender
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
- m365initiative-defender-endpoint
ms.topic: article
ms.technology: mde
ms.openlocfilehash: cb8c0bd0870ea240e64c33dfac2fd6c00156def8
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2021
ms.locfileid: "62998250"
---
# <a name="assign-device-value---threat-and-vulnerability-management"></a>Cihaz değeri atama - Tehdit ve Güvenlik Açığı Yönetimi

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Tehdit ve güvenlik açığı yönetimi](next-gen-threat-and-vuln-mgt.md)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Microsoft Defender'ı mı deneyimliysiniz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-portaloverview-abovefoldlink)

[!include[Prerelease information](../../includes/prerelease.md)]

Bir cihazın değerini tanımlamak, varlık öncelikleri arasında ayrımnıza yardımcı olur. Cihaz değeri, bireysel bir varlığın risk yorumlarını maruz kalma puanı hesaplamasına Tehdit ve Güvenlik Açığı Yönetimi kullanılır. "Yüksek değer" olarak atanan cihazlar daha fazla ağırlık alır.

Cihaz değeri [API'sini ayarlamayı da kullanabilirsiniz](set-device-value.md).

Cihaz değeri seçenekleri:

- Düşük
- Normal (Varsayılan)
- Yüksek

Yüksek değer atanacak cihazlara örnekler:

- Etki alanı denetleyicileri, Active Directory
- İnternet'e yönelik cihazlar
- VIP cihazlar
- İç/dış üretim hizmetlerini barındıran cihazlar

## <a name="choose-device-value"></a>Cihaz değerini seçin

1. Herhangi bir cihaz sayfasına gidin, en kolay yer cihaz envanteridir.

2. Sayfanın **en** üstünde, eylemler çubuğunun yanındaki üç noktanın yanındaki Cihaz değeri'ne tıklayın.

    ![Cihaz değeri açılan liste örneği.](images/tvm-device-value-dropdown.png)

3. Geçerli cihaz değeri ve anlamıyla birlikte bir çıkış görünür. Cihazın değerini gözden geçirin ve cihazınıza en uygun olanı seçin.
![Cihaz değeri uçarak çıkış örneği.](images/tvm-device-value-flyout.png)

## <a name="how-device-value-impacts-your-exposure-score"></a>Cihaz değeri etkilenme puanınızı nasıl etkiler?

Pozlama puanı tüm cihazlarda ağırlıklı ortalamadır. Cihaz gruplarınız varsa, puanı cihaz grubuna göre de filtre edebilirsiniz.

- Normal cihazların ağırlıkları 1'tir
- Düşük değerli cihazların ağırlıkları 0,75'tir
- Yüksek değerli cihazların ağırlıkları NumberOfAssets / 10'dur.
    - 100 cihazınız varsa, her yüksek değerli cihazın ağırlık 10 (100/10) olur

## <a name="related-topics"></a>İlgili konular

- [Tehdit ve güvenlik açığı yönetimi genel bakış](next-gen-threat-and-vuln-mgt.md)
- [Pozlama Puanı](tvm-exposure-score.md)
- [API'ler](next-gen-threat-and-vuln-mgt.md#apis)