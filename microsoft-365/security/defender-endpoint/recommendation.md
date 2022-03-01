---
title: Öneri yöntemleri ve özellikleri
description: En son uyarıları almaya devam ediyor.
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
ms.openlocfilehash: f6e8295d83d5ab6fb86726903800d2779f394836
ms.sourcegitcommit: 348f3998a029a876a9dcc031f808e9e350804f22
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2021
ms.locfileid: "62996537"
---
# <a name="recommendation-resource-type"></a>Öneri kaynak türü

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Uç Nokta için Defender'ı deneyimli yapmak mı istiyor musunuz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

[!include[Prerelease information](../../includes/prerelease.md)]

## <a name="methods"></a>Yöntemler

<br>

****

|Yöntem|İade Türü|Açıklama|
|---|---|---|
|[Tüm önerileri listele](get-all-recommendations.md)|Öneri koleksiyonu|Kuruluşu etkileyen tüm güvenlik önerilerinin listesini alma|
|[Kimlikle öneriyi al](get-recommendation-by-id.md)|Öneri|Kimliğiyle bir güvenlik önerisi sağlar|
|[Öneri yazılımı al](list-recommendation-software.md)|[Yazılım](software.md)|Belirli bir yazılımla ilgili bir güvenlik önerisi sağlar|
|[Öneri cihazları al](get-recommendation-machines.md)|MachineRef koleksiyonu|Güvenlik önerisiyle ilişkilendirilmiş cihazların listesini verir|
|[Öneri güvenlik açıklarını al](get-recommendation-vulnerabilities.md)|[Güvenlik Açığı](vulnerability.md) koleksiyonu|Güvenlik önerisiyle ilişkilendirilmiş güvenlik açıklarının listesini alma|
|

## <a name="properties"></a>Özellikler

<br>

****

|Özellik|Tür|Açıklama|
|---|---|---|
|id|Dize|Öneri Kimliği|
|ürünAdı|Dize|İlgili yazılım adı|
|recommendationName|Dize|Öneri adı|
|Zayıflar|Long|Bulunan güvenlik açıklarının sayısı|
|Satıcı|Dize|İlgili satıcı adı|
|recommendedVersion|Dize|Önerilen sürüm|
|recommendedProgram|Dize|Önerilen program|
|önerilenVendor|Dize|Önerilen satıcı|
|recommendationCategory|Dize|Öneri kategorisi. Olası değerler şöyledir: "Hesaplar", "Uygulama", "Ağ", "işletim sistemi", "SecurityControls"|
|altKategori|Dize|Öneri alt kategorisi|
|önem derecesiScore|Double|Yapılandırmanın, kuruluşun Cihazlar için Microsoft Güvenli Puanı'nın olası etkileri (1-10)|
|publicExploit|Boole|Kamu açıkları kullanılabilir|
|activeAlert|Boole|Etkin uyarı bu öneriyle ilişkilendirildi|
|associatedThreats|Dize koleksiyonu|Tehdit analizi raporu bu öneriyle ilişkilendirilmiştir|
|remediationType|Dize|Düzeltme türü. Olası değerler: "ConfigurationChange","Güncelleştir","Yükselt","Kaldır"|
|Durum|Enum|Öneri özel durumu. Olası değerler şöyledir: "Etkin" ve "Özel Durum"|
|configScoreImpact|Double|Cihazlar üzerindeki etki için Microsoft Güvenli Puan|
|exposureImpact|Double|Etkilenme puanının etkisi|
|totalMachineCount|Long|Yüklü cihaz sayısı|
|exposedMacount|Long|Güvenlik açıklarına açık olan yüklü cihaz sayısı|
|nonProductivityImpactedAssets|Long|Etkilenmez cihaz sayısı|
|relatedComponent|Dize|İlgili yazılım bileşeni|
|
