---
title: Puan yöntemleri ve özellikleri
description: Cihaz grubuna göre kuruluşlarının pozlama puanını, cihazın güvenli puanını ve pozlama puanını verir
keywords: api'ler, grafik api'leri, desteklenen api'ler, puan, pozlama puanı, cihazın güvenli puanı, cihaz grubuna göre pozlama puanı
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
MS.technology: mde
ms.custom: api
ms.openlocfilehash: fe69b42c2d8bf80089b749cd41e59664cc2921e3
ms.sourcegitcommit: 348f3998a029a876a9dcc031f808e9e350804f22
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2021
ms.locfileid: "62996518"
---
# <a name="score-resource-type"></a>Puan kaynak türü

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Microsoft Defender'ı mı deneyimliysiniz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

[!include[Prerelease information](../../includes/prerelease.md)]

## <a name="methods"></a>Yöntemler

Yöntem|İade Türü|Açıklama
:---|:---|:---
[Pozlama puanı elde](get-exposure-score.md)|[Puan](score.md)|Kurumsal pozlama puanına sahip olur.
[Cihazın güvenli puanını al](get-device-secure-score.md)|[Puan](score.md)|Kurumsal cihaz güvenliğinin puanına sahip olun.
[Cihaz grubuna göre açık kalma puanı listesi](get-machine-group-exposure-score.md)|[Puan](score.md)|Cihaz grubuna göre puanları listele.

## <a name="properties"></a>Özellikler

Özellik|Tür|Açıklama
:---|:---|:---
Puan|Double|Geçerli puandır.
Saat|DateTime|Bu API için çağrının hangi tarih ve saatte yapılmış olduğu.
RbacGroupName|Dize|Cihaz grubu adı.
RbacGroupId|Dize|Cihaz grup kimliği.
