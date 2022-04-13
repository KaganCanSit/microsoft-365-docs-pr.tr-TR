---
title: Microsoft 365 Defender gelişmiş avcılık API'si
description: Microsoft 365 Defender gelişmiş tehdit avcılığı API'sini kullanarak gelişmiş avcılık sorguları çalıştırmayı öğrenin
keywords: Gelişmiş Avcılık, API'ler, api, M365 Defender, Microsoft 365 Defender
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.custom: api
ms.openlocfilehash: d01cdacc40b58eb940b2773606221b4fdbe18728
ms.sourcegitcommit: 195e4734d9a6e8e72bd355ee9f8bca1f18577615
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/13/2022
ms.locfileid: "64823200"
---
# <a name="microsoft-365-defender-advanced-hunting-api"></a>Microsoft 365 Defender Gelişmiş avcılık API'si

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Şunlar için geçerlidir:**

- Microsoft 365 Defender

> [!IMPORTANT]
> Bazı bilgiler, ticari olarak piyasaya sürülmeden önce önemli ölçüde değiştirilebilen önceden yayımlanmış ürünle ilgilidir. Microsoft, burada sağlanan bilgilerle ilgili olarak açık veya zımni hiçbir garanti vermez.

[Gelişmiş avcılık](advanced-hunting-overview.md), Microsoft 365 Defender'da son 30 günlük olay verilerini incelemek için [özel olarak oluşturulan sorguları](advanced-hunting-query-language.md) kullanan bir tehdit avcılığı aracıdır. Olağan dışı etkinlikleri incelemek, olası tehditleri algılamak ve hatta saldırılara yanıt vermek için gelişmiş tehdit avcılığı sorgularını kullanabilirsiniz. Gelişmiş tehdit avcılığı API'si, olay verilerini programlı olarak sorgulamanıza olanak tanır.

## <a name="quotas-and-resource-allocation"></a>Kotalar ve kaynak ayırma

Aşağıdaki koşullar tüm sorgular ile ilgilidir.

1. Sorgular son 30 güne ait verileri inceler ve döndürür.
2. Sonuçlar en fazla 100.000 satır döndürebilir.
3. Kiracı başına dakikada en fazla 45 çağrı yapabilirsiniz.
4. Kiracı sonraki 15 dakikalık döngüden sonra %100'e ulaşmışsa sorgular engellenir.
5. Tek bir istek 10 dakikadan uzun süre çalıştırılırsa zaman aşımına uğradıktan sonra bir hata döndürür.
6. `429` HTTP yanıt kodu, gönderilen istek sayısına veya ayrılan çalışma süresine göre bir kotaya ulaştığınızı gösterir. Ulaştığınız sınırı anlamak için yanıt gövdesini okuyun. 

> [!NOTE]
> Yukarıda listelenen tüm kotalar (örneğin, dakika başına 15 çağrı) kiracı boyutuna göredir. Bu kotalar minimum değerdir.

## <a name="permissions"></a>İzinler

Gelişmiş tehdit avcılığı API'sini çağırmak için aşağıdaki izinlerden biri gereklidir. İzinlerin nasıl seçileceği de dahil olmak üzere daha fazla bilgi edinmek için bkz. [Microsoft 365 Defender Koruması API'lerine erişme](api-access.md)

İzin türü | Izni | İzin görünen adı
-|-|-
Uygulama | AdvancedHunting.Read.All| Gelişmiş sorgular çalıştırma
Temsilci (iş veya okul hesabı) | AdvancedHunting.Read | Gelişmiş sorgular çalıştırma

>[!Note]
> Kullanıcı kimlik bilgilerini kullanarak belirteç alırken:
>
>- Kullanıcının 'Verileri Görüntüle' AD rolüne sahip olması gerekir
>- Kullanıcının cihaz grubu ayarlarına göre cihaza erişimi olmalıdır.

## <a name="http-request"></a>HTTP isteği

```HTTP
POST https://api.security.microsoft.com/api/advancedhunting/run
```

## <a name="request-headers"></a>İstek üst bilgileri

Üstbilgi | Değer
-|-
Yetkilendirme | Taşıyıcı {token} **Not: gerekli**
İçerik Türü | application/json

## <a name="request-body"></a>İstek gövdesi

İstek gövdesinde aşağıdaki parametreleri içeren bir JSON nesnesi sağlayın:

Parametre | Tür | Açıklama
-|-|-
Sorgu | Metin | Çalıştırılacak sorgu. **Not: gerekli**

## <a name="response"></a>Yanıt

Başarılı olursa, bu yöntem yanıt gövdesinde ve _bir QueryResponse_ nesnesi döndürür`200 OK`.

Yanıt nesnesi üç üst düzey özellik içerir:

1. İstatistikler - Sorgu performansı istatistikleri sözlüğü.
2. Schema - Yanıtın şeması, her sütun için Name-Type çiftlerinin listesi.
3. Sonuçlar - Gelişmiş tehdit avcılığı olaylarının listesi.

## <a name="example"></a>Örnek

Aşağıdaki örnekte, kullanıcı aşağıdaki sorguyu gönderir ve , `Schema`ve `Results`içeren `Stats`bir API yanıt nesnesi alır.

### <a name="query"></a>Sorgu

```json
{
    "Query":"DeviceProcessEvents | where InitiatingProcessFileName =~ \"powershell.exe\" | project Timestamp, FileName, InitiatingProcessFileName | order by Timestamp desc | limit 2"
}

```

### <a name="response-object"></a>Yanıt nesnesi

```json
{
    "Stats": {
        "ExecutionTime": 4.621215,
        "resource_usage": {
            "cache": {
                "memory": {
                    "hits": 773461,
                    "misses": 4481,
                    "total": 777942
                },
                "disk": {
                    "hits": 994,
                    "misses": 197,
                    "total": 1191
                }
            },
            "cpu": {
                "user": "00:00:19.0468750",
                "kernel": "00:00:00.0156250",
                "total cpu": "00:00:19.0625000"
            },
            "memory": {
                "peak_per_node": 236822432
            }
        },
        "dataset_statistics": [
            {
                "table_row_count": 2,
                "table_size": 102
            }
        ]
    },
    "Schema": [
        {
            "Name": "Timestamp",
            "Type": "DateTime"
        },
        {
            "Name": "FileName",
            "Type": "String"
        },
        {
            "Name": "InitiatingProcessFileName",
            "Type": "String"
        }
    ],
    "Results": [
        {
            "Timestamp": "2020-08-30T06:38:35.7664356Z",
            "FileName": "conhost.exe",
            "InitiatingProcessFileName": "powershell.exe"
        },
        {
            "Timestamp": "2020-08-30T06:38:30.5163363Z",
            "FileName": "conhost.exe",
            "InitiatingProcessFileName": "powershell.exe"
        }
    ]
}
```

## <a name="related-articles"></a>İlgili makaleler

- [Microsoft 365 Defender API'lerine erişme](api-access.md)
- [API sınırları ve lisanslama hakkında bilgi edinin](api-terms.md)
- [Hata kodlarını anlama](api-error-codes.md)
- [Gelişmiş avcılığa genel bakış](advanced-hunting-overview.md)
