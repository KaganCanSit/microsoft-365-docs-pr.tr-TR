---
title: Gelişmiş avda AssignedIPAddresses() işlevi Microsoft 365 Defender
description: Bir cihaza atanan en son IP adreslerini almak için AssignedIPAddresses() işlevini kullanmayı öğrenin
keywords: gelişmiş av, tehdit avı, siber tehdit avı, Microsoft 365 Defender, Microsoft 365, m365, arama, sorgu, telemetri, şema başvurusu, kusto, FileProfile, dosya profili, işlev, zenginleştirme
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
ms.openlocfilehash: b82a079a476ee6ed3d5465b52bca381cd49746b5
ms.sourcegitcommit: 6dcc3b039e0f0b9bae17c386f14ed2b577b453a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/15/2021
ms.locfileid: "63018996"
---
# <a name="assignedipaddresses"></a>AssignedIPAddresses()

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:**
- Microsoft 365 Defender

Bir cihaza `AssignedIPAddresses()` atanmış [en son](advanced-hunting-overview.md) IP adreslerini hızla elde etmek için gelişmiş arama sorgularında işlevi kullanın. Zaman damgası bağımsız değişkeni belirtirsiniz, bu işlev belirtilen zamanda en yeni IP adreslerini elde edilir. 

Bu işlev, aşağıdaki sütunları içeren bir tablo döndürür:

| Sütun | Veri türü | Açıklama |
|------------|-------------|-------------|
| `Timestamp` | `datetime` | Cihaz IP adresi kullanılarak gözlemlenen en son saat |
| `IPAddress` | `string` | Cihaz tarafından kullanılan IP adresi |
| `IPType` | `string` | IP adresinin genel veya özel bir adres olup olmadığını gösterir |
| `NetworkAdapterType` | `int` | IP adresi atanmış olan cihaz tarafından kullanılan ağ bağdaştırıcısı türü. Olası değerler için bu [numaralamaya bakın](/dotnet/api/system.net.networkinformation.networkinterfacetype) |
| `ConnectedNetworks` | `int` | Atanmış IP adresine sahip bağdaştırıcının bağlı olduğu ağlar. Her JSON dizisi ağ adını, kategoriyi (genel, özel veya etki alanı), bir açıklamayı ve İnternet'e genel olarak bağlı olup olmadığını gösteren bir bayrak içerir |

## <a name="syntax"></a>Söz dizimi

```kusto
AssignedIPAddresses(x, y)
```

## <a name="arguments"></a>Bağımsız değişkenler

- **x**—`DeviceId` veya `DeviceName` cihazı tanımlayan değer
- **y**—`Timestamp` (datetime) değeri, işleve belirli bir tarihten en son atanan IP adreslerini almalarını sağlar. Belirtilmezse, işlev en son IP adreslerini döndürür.

## <a name="examples"></a>Örnekler

### <a name="get-the-list-of-ip-addresses-used-by-a-device-24-hours-ago"></a>Bir cihaz tarafından kullanılan IP adreslerinin listesini 24 saat önce al

```kusto
AssignedIPAddresses('example-device-name', ago(1d))
```

### <a name="get-ip-addresses-used-by-a-device-and-find-devices-communicating-with-it"></a>Bir cihaz tarafından kullanılan IP adreslerini al ve cihazla iletişim kurma cihazlarını bul
Bu sorgu, cihazın `AssignedIPAddresses()` () belirli bir tarihte () veya daha önce atanmış`example-device-name` IP adreslerini almak için işlevi kullanır`example-date`. Ardından IP adreslerini kullanarak, diğer cihazlar tarafından başlatılan cihaza bağlantıları bulur. 

```kusto
let Date = datetime(example-date);
let DeviceName = "example-device-name";
// List IP addresses used on or before the specified date
AssignedIPAddresses(DeviceName, Date)
| project DeviceName, IPAddress, AssignedTime = Timestamp 
// Get all network events on devices with the assigned IP addresses as the destination addresses
| join kind=inner DeviceNetworkEvents on $left.IPAddress == $right.RemoteIP
// Get only network events around the time the IP address was assigned
| where Timestamp between ((AssignedTime - 1h) .. (AssignedTime + 1h))
```

## <a name="related-topics"></a>İlgili konular
- [Gelişmiş ava genel bakış](advanced-hunting-overview.md)
- [Sorgu dilini öğrenme](advanced-hunting-query-language.md)
- [Şemayı anlama](advanced-hunting-schema-tables.md)