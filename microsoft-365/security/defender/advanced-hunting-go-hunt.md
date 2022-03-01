---
title: Go Hunt ile bir varlık hakkında ilgili bilgi al
description: Gelişmiş av kullanarak bir varlık veya etkinlik hakkında ilgili bilgileri hızlıca sorgulamak için hareket arama aracını nasıl kullanabileceğiniz hakkında bilgi edinebilirsiniz.
keywords: gelişmiş av, olay, özet, varlık, avına git, ilgili etkinlikler, tehdit avı, siber tehdit araması, arama, sorgu, telemetri, Microsoft 365, Microsoft 365 Defender
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
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: e14f2d5e35585cf5b0edfe433084fa7c8a1d5280
ms.sourcegitcommit: 4af23696ff8b44872330202fe5dbfd2a69d9ddbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/30/2021
ms.locfileid: "62997079"
---
# <a name="quickly-hunt-for-entity-or-event-information-with-go-hunt"></a>Hareket avı ile varlık veya etkinlik bilgilerini hızla avına çıktılar

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:**
- Microsoft 365 Defender
- Uç Nokta için Microsoft Defender

Hızlı arama *eylemiyle* , güçlü sorgu tabanlı gelişmiş av özelliklerini kullanarak olayları ve çeşitli varlık [türlerini hızla](advanced-hunting-overview.md) araştırabilirsiniz. Bu eylem, seçili etkinlik veya varlıkla ilgili bilgileri bulmak için otomatik olarak gelişmiş bir arama sorgusu çalıştırır.

Etkinlik *veya varlık* ayrıntıları her görüntülendiğinde Bulut için Defender'ın go hunt eylemi çeşitli bölümlerinde kullanılabilir. Örneğin, aşağıdaki bölümlerden *go hunt'ı* kullanabilirsiniz:

- Olay [sayfasında kullanıcılar](investigate-incidents.md#summary), cihazlar ve bir olayla ilişkilendirilmiş diğer varlıklarla ilgili ayrıntıları gözden geçirebilirsiniz. Bir varlığı seçerek, ek bilgiler ve bu varlık üzerinde gerçekleştirebilirsiniz çeşitli işlemler elde edersiniz. Aşağıdaki örnekte, posta kutusuyla ilgili ayrıntıların yanı sıra posta kutusu hakkında daha fazla bilgi alma seçeneğini gösteren bir posta kutusu seçilmiştir.

    :::image type="content" source="../../media/go-hunt-1-incident.png" alt-text="Yeni portalda **Go hunt** seçeneğinin yer alan **Mailboxes** Microsoft 365 Defender sayfası" lightbox="../../media/go-hunt-1-incident.png":::

- Olay sayfasında, Kanıt sekmesinin altında varlıkların listesine de **erişebilirsiniz** . Bu varlıklardan birini seçmek, ilgili varlıkla ilgili bilgileri hızla arama seçeneği sağlar.

    :::image type="content" source="../../media/go-hunt-2-entity.png" alt-text="Portalda **Olay** sayfasındaki bir kanıt için Git Microsoft 365 Defender" lightbox="../../media/go-hunt-2-entity.png":::


- Bir cihaz için zaman çizelgesini görüntülerken, o etkinlikle ilgili ek bilgileri görüntülemek için zaman çizelgesinde bir olay seçin. Bir etkinlik seçildikten sonra, gelişmiş avda diğer ilgili etkinlikleri arama seçeneğiniz olur.

    :::image type="content" source="../../media/go-hunt-3-event.png" alt-text="Bir portalda **Zaman çizelgeleri** sekmesindeki bir etkinliğin sayfasındaki ilgili etkinlikler için çağrı yapın** Microsoft 365 Defender" lightbox="../../media/go-hunt-3-event.png":::

Go **hunt veya** **Hunt seçildiğinde** , bir varlık veya etkinlik seçtiğinize bağlı olarak ilgili etkinlikler için farklı sorgular geçer.

## <a name="query-for-entity-information"></a>Varlık bilgileri sorgusu
Kullanıcı, *cihaz veya* başka herhangi bir tür varlık hakkında bilgi almak için sorgu yapmak için go Hunt kullanılırken, sorgu ilgili tüm şema tablolarında söz konulan olayları denetler. Sonuçların yönetilebilir durumda olması için, sorgunun kapsamı, son 30 gün içinde var olan ve olayla ilişkilendirilmiş olan en erken etkinlikle aynı zaman süresi kapsamındadır.

Bir cihaz için go hunt sorgusu örneği:

```kusto
let selectedTimestamp = datetime(2020-06-02T02:06:47.1167157Z);
let deviceName = "fv-az770.example.com";
let deviceId = "device-guid";
search in (DeviceLogonEvents, DeviceProcessEvents, DeviceNetworkEvents, DeviceFileEvents, DeviceRegistryEvents, DeviceImageLoadEvents, DeviceEvents, DeviceImageLoadEvents, IdentityLogonEvents, IdentityQueryEvents)
Timestamp between ((selectedTimestamp - 1h) .. (selectedTimestamp + 1h))
and DeviceName == deviceName
// or RemoteDeviceName == deviceName
// or DeviceId == deviceId
| take 100
```
### <a name="supported-entity-types"></a>Desteklenen varlık türleri
Şu varlık *türlerinden herhangi birini* seçerek go hunt kullanabilirsiniz:

- Dosyalar
- E-postalar
- E-posta kümeleri
- Posta Kutuları
- Kullanıcılar
- Cihazlar
- IP adresleri
- URL'ler

## <a name="query-for-event-information"></a>Olay bilgileri sorgusu
Zaman çizelgesi *olayı hakkında* bilgi almak için gidip arama sırasında sorgulanan sorgu, tüm ilgili şema tablolarını seçili olayın olduğu zamanla ilgili diğer olayları denetler. Örneğin, aşağıdaki sorguda, aynı cihaz üzerinde aynı zaman dönemine kadar 44 saat içinde  meydana gelen çeşitli şema tablolarında yer alan olaylar listelemektedir:

```kusto
// List relevant events 30 minutes before and after selected LogonAttempted event
let selectedEventTimestamp = datetime(2020-06-04T01:29:09.2496688Z);
search in (DeviceFileEvents, DeviceProcessEvents, DeviceEvents, DeviceRegistryEvents, DeviceNetworkEvents, DeviceImageLoadEvents, DeviceLogonEvents)
    Timestamp between ((selectedEventTimestamp - 30m) .. (selectedEventTimestamp + 30m))
    and DeviceId == "079ecf9c5798d249128817619606c1c47369eb3e"
| sort by Timestamp desc
| extend Relevance = iff(Timestamp == selectedEventTimestamp, "Selected event", iff(Timestamp < selectedEventTimestamp, "Earlier event", "Later event"))
| project-reorder Relevance
```

## <a name="adjust-the-query"></a>Sorguyu ayarlama
Sorgu dilini biraz [bilgiyle](advanced-hunting-query-language.md), sorguyu tercihlerinize göre ayarlayabilirsiniz. Örneğin, zaman penceresinin boyutunu belirleyen bu satırı ayarlayabilirsiniz:

```kusto
Timestamp between ((selectedTimestamp - 1h) .. (selectedTimestamp + 1h))
```

Daha ilgili sonuçlar elde etmek için sorguyu değiştirmenin yanı sıra şunları da sebilirsiniz:
- [Sonuçları grafik olarak görüntüleme](advanced-hunting-query-results.md#view-query-results-as-a-table-or-chart)
- [Özel algılama kuralı oluşturma](custom-detection-rules.md)

>[!NOTE]
>Bu makaledeki bazı tablolar Uç Nokta için Microsoft Defender'da kullanılamıyor olabilir. [Daha fazla Microsoft 365 Defender](m365d-enable.md) kullanarak tehdit yakalamak için çok daha fazla kaynağı açabilirsiniz. Gelişmiş av iş akışlarınızı Uç Nokta için Microsoft Defender'dan Microsoft 365 Defender için [Microsoft Defender'dan gelişmiş arama sorgularını geçirme makalesinde](advanced-hunting-migrate-from-mde.md) yer alan adımları takip edebilirsiniz.

## <a name="related-topics"></a>İlgili konular
- [Gelişmiş ava genel bakış](advanced-hunting-overview.md)
- [Sorgu dilini öğrenme](advanced-hunting-query-language.md)
- [Sorgu sonuçlarıyla çalışma](advanced-hunting-query-results.md)
- [Özel algılama kuralları](custom-detection-rules.md)
