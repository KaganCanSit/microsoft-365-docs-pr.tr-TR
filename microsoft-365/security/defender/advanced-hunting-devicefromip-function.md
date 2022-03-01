---
title: Microsoft 365 Defender için gelişmiş avda DeviceFromIP() işlevi
description: Belirli bir IP adresi atanmış cihazları almak için DeviceFromIP() işlevini kullanmayı öğrenin
keywords: gelişmiş av, tehdit avı, siber tehdit avı, Microsoft 365 Defender, Microsoft 365, m365, arama, sorgu, telemetri, şema başvurusu, kusto, cihaz, devicefromIP, işlev, zenginleştirme
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
ms.openlocfilehash: 4a1f1198c247aefbcbb093d1a5f5105704255692
ms.sourcegitcommit: 6dcc3b039e0f0b9bae17c386f14ed2b577b453a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/15/2021
ms.locfileid: "63019034"
---
# <a name="devicefromip"></a>DeviceFromIP()

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:**
- Microsoft 365 Defender


[!INCLUDE [Prerelease information](../includes/prerelease.md)]


Belirli bir `DeviceFromIP()` noktada [belirli bir](advanced-hunting-overview.md) IP adresine atanmış cihazların listesini hızla elde etmek için gelişmiş arama sorgularında işlevi kullanın. 

Bu işlev, aşağıdaki sütunları içeren bir tablo döndürür:

| Sütun | Veri türü | Açıklama |
|------------|-------------|-------------|
| `IP` | `string` | IP adresi  |
| `DeviceId` | `string` | Hizmette cihaz için benzersiz tanımlayıcı |


## <a name="syntax"></a>Söz dizimi

```kusto
invoke DeviceFromIP()
```

## <a name="arguments"></a>Bağımsız değişkenler

Bu işlev sorgunun bir parçası olarak çağırıldı.

- **x**—İlk parametre normalde sorguda zaten bir sütundur. Bu durumda, ip adresi olarak `IP`adlandırılmış olan ve ona atanmış cihazların listesini görmek istediğiniz IP adresidir. Yerel bir IP adresi olmalı. Dış IP adresleri desteklenmiyor.
- **y**—İkinci isteğe bağlı `Timestamp`parametre, işleve belirli bir zaman içinde en son atanan cihazları almalarını haber verir. Belirtilmezse, işlev kullanılabilen en son kayıtları döndürür.

## <a name="example"></a>Örnek


### <a name="get-the-latest-devices-that-have-been-assigned-specific-ip-addresses"></a>Belirli IP adresleri atanmış en son cihazları al

```kusto
DeviceNetworkEvents 
| limit 100 
| project IP = LocalIP 
| invoke DeviceFromIP()
```

## <a name="related-topics"></a>İlgili konular
- [Gelişmiş ava genel bakış](advanced-hunting-overview.md)
- [Sorgu dilini öğrenme](advanced-hunting-query-language.md)
- [Şemayı anlama](advanced-hunting-schema-tables.md)
