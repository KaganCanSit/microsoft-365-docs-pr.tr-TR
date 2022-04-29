---
title: Gelişmiş tehdit avcılığı şemasındaki UrlClickEvents tablosu
description: Gelişmiş tehdit avcılığı şemasındaki UrlClickEvents tablosunu kullanarak kimlik avı kampanyalarını ve şüpheli tıklamaları nasıl avlayacağınızı öğrenin.
keywords: gelişmiş tehdit avcılığı, tehdit avcılığı, siber tehdit avcılığı, Microsoft 365 Defender, microsoft 365, m365, arama, sorgu, telemetri, şema başvurusu, kusto, tablo, sütun, veri türü, açıklama, UrlClickEvents, SafeLinks, kimlik avı, kötü amaçlı yazılım, kötü amaçlı tıklamalar, Outlook, ekipler, e-posta, Office365
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: maccruz
author: schmurky
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: m365-security-compliance
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: bb7ee0397c79cc64c6f7396b6c3ca9450c8306f2
ms.sourcegitcommit: fdd0294e6cda916392ee66f5a1d2a235fb7272f8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/29/2022
ms.locfileid: "65130292"
---
# <a name="urlclickevents"></a>UrlClickEvents

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Şunlar için geçerlidir:**
- Microsoft 365 Defender
- Office 365 için Microsoft Defender


`UrlClickEvents` Gelişmiş tehdit avcılığı şemasındaki tablo, desteklenen masaüstü, mobil ve web uygulamalarında e-posta iletileri, Microsoft Teams ve Office 365 uygulamalarından Kasa [Bağlantıları](../office-365-security/safe-links.md) tıklamaları hakkında bilgi içerir. 

> [!IMPORTANT]
> Bazı bilgiler, ticari olarak piyasaya sürülmeden önce önemli ölçüde değiştirilebilen önceden yayımlanmış ürünle ilgilidir. Microsoft, burada sağlanan bilgilerle ilgili olarak açık veya zımni hiçbir garanti vermez.

Gelişmiş tehdit avcılığı şemasındaki diğer tablolar hakkında bilgi için gelişmiş [avcılık başvurusuna](advanced-hunting-schema-tables.md) bakın.

| Sütun adı | Veri türü | Açıklama |
|-------------|-----------|-------------|
| `Timestamp` | `datetime` | Kullanıcının bağlantıya tıkladığında tarih ve saat |
| `Url` | `string` | Kullanıcı tarafından tıklanan tam URL |
| `ActionType` | `string` | Tıklamaya izin verilip verilmeyeceğini veya Kasa Bağlantıları tarafından engellenip engellenmediğini veya bir kiracı ilkesi nedeniyle engellenip engellenmediğini gösterir; örneğin, Kiracı İzin Verme Bloğu listesinden|
| `AccountUpn` | `string` | Bağlantıya tıklanan hesabın Kullanıcı Asıl Adı|
| `Workload` | `string` | Kullanıcının bağlantıya tıkladığı uygulama ve değerler E-posta, Office ve Teams|
| `NetworkMessageId` | `string` | Microsoft 365 tarafından oluşturulan tıklanan bağlantıyı içeren e-postanın benzersiz tanımlayıcısı|
| `IPAddress` | `string` | Kullanıcının bağlantıya tıkladığı cihazın genel IP adresi|
| `ThreatTypes` | `string` | Url'nin kötü amaçlı yazılıma mı, kimlik avına mı yoksa diğer tehditlere mi yol açtığını belirten tıklama sırasında karar verme|
| `DetectionMethods` | `string` | Tıklama sırasında tehdidi tanımlamak için kullanılan algılama teknolojisi|
| `IsClickedThrough` | `bool` | Kullanıcının özgün URL'ye tıklayıp tıklayamadığını veya buna izin verilmediğini gösterir|
| `UrlChain` | `string` | Yeniden yönlendirme içeren senaryolar için, yeniden yönlendirme zincirinde bulunan URL'leri içerir|
| `ReportId` | `string` | Bu, tıklama olayının benzersiz tanımlayıcısıdır. Tıklama senaryoları için rapor kimliğinin aynı değere sahip olacağını ve bu nedenle bir tıklama olayını ilişkilendirmek için kullanılması gerektiğini unutmayın.|

Kullanıcının devam etmesine izin verilen bağlantıların `UrlClickEvents` listesini döndürmek için tabloyu kullanan bu örnek sorguyu deneyebilirsiniz: 

```kusto
// Search for malicious links where user was allowed to proceed through
UrlClickEvents
| where ActionType == "ClickAllowed" or IsClickedThrough !="0"
| where ThreatTypes has "Phish"
| summarize by ReportId, IsClickedThrough, AccountUpn, NetworkMessageId, ThreatTypes, Timestamp
```

## <a name="related-topics"></a>İlgili konular

- [Tehditleri proaktif olarak avlama](advanced-hunting-overview.md)
- [Office 365 için Microsoft Defender'da bağlantıları Kasa](../office-365-security/safe-links.md)
- [Gelişmiş tehdit avcılığı sorgu sonuçları üzerinde eylem gerçekleştirme](advanced-hunting-take-action.md)