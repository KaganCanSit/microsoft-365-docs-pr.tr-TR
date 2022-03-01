---
title: Yazılım yöntemleri ve özellikleri
description: En son uyarıları alınır.
keywords: api'ler, grafik api'leri, desteklenen api'ler, get, alerts, recent
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dolmont
author: DulceMontemayor
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
MS.technology: mde
ms.custom: api
ms.openlocfilehash: 6b08b7c4ebb0a818dec5bdf799c3114d91764259
ms.sourcegitcommit: 348f3998a029a876a9dcc031f808e9e350804f22
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2021
ms.locfileid: "62996554"
---
# <a name="software-resource-type"></a>Yazılım kaynak türü

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

<br>

****

|Yöntem|İade Türü|Açıklama|
|---|---|---|
|[Liste yazılımı](get-software.md)|Yazılım koleksiyonu|Kuruluş yazılım envanterini listele|
|[Yazılımı kimlikle al](get-software-by-id.md)|Yazılım|Belirli bir yazılımı yazılım kimliğiyle elde|
|[Liste yazılım sürümü dağıtımı](get-software-ver-distribution.md)|Dağıtım koleksiyonu|Yazılım kimliğine göre liste yazılım sürümü dağıtımı|
|[Yazılıma göre liste makineleri](get-machines-by-software.md)|MachineRef koleksiyonu|Yazılım kimliğiyle ilişkilendirilmiş cihazların listesini alma|
|[Yazılıma göre açıkları listele](get-vuln-by-software.md)|[Güvenlik Açığı](vulnerability.md) koleksiyonu|Yazılım kimliğiyle ilişkilendirilmiş güvenlik açıklarının listesini alma|
|[Eksik KB'leri al](get-missing-kbs-software.md)|KB koleksiyonu|Yazılım kimliğiyle ilişkilendirilmiş eksik KB'lerin listesini al|
|

## <a name="properties"></a>Özellikler

<br>

****

|Özellik|Tür|Açıklama|
|---|---|---|
|id|Dize|Yazılım Kimliği|
|Name|Dize|Yazılım adı|
|Satıcı|Dize|Yazılım yayıncısı adı|
|Zayıflar|Long|Bulunan güvenlik açıklarının sayısı|
|publicExploit|Boole|Açıklardan bazıları için genel açıklardan yararlanma|
|activeAlert|Boole|Etkin uyarı bu yazılımla ilişkilendirildi|
|exposedMaamaes|Long|Maruz kalan cihaz sayısı|
|impactScore|Double|Bu yazılımın etkilenme puanı|
|
