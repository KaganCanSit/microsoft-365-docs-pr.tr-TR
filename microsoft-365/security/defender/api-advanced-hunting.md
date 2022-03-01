---
title: Microsoft 365 Defender av API'sini edinin
description: Gelişmiş av API'sini kullanarak gelişmiş Microsoft 365 Defender sorgularını çalıştırmayı öğrenin
keywords: Gelişmiş Av, API'ler, api, M365 Defender, Microsoft 365 Defender
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
ms.openlocfilehash: 94ce63f30b0016a920fdca60dd10b486922ffa32
ms.sourcegitcommit: 6f3bc00a5cf25c48c61eb3835ac069e9f41dc4db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2022
ms.locfileid: "63010734"
---
# <a name="microsoft-365-defender-advanced-hunting-api"></a>Microsoft 365 Defender av API'si

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**

- Microsoft 365 Defender

> [!IMPORTANT]
> Bazı bilgiler, ticari olarak piyasaya sürmeden önce önemli ölçüde değiştirilmiş olabilir, önceden satın alınan ürünle ilgilidir. Microsoft, burada sağlanan bilgilerle ilgili olarak açık veya zımni hiçbir garanti vermez.

[Gelişmiş av](advanced-hunting-overview.md), özel olarak oluşturulmuş sorguları kullanarak son 30 günlük etkinlik verilerini aynı yılda incelemek için kullanan bir tehdit Microsoft 365 Defender.[](advanced-hunting-query-language.md) Olağandışı etkinlikleri incelemek, olası tehditleri tespit etmek ve hatta saldırılara yanıt vermek için gelişmiş arama sorgularını kullanabilirsiniz. Gelişmiş av API'si, etkinlik verilerini programlı olarak sorgulamanız için olanak sağlar.

## <a name="quotas-and-resource-allocation"></a>Kotalar ve kaynak ayırma

Aşağıdaki koşullar tüm sorgulara göredir.

1. Sorgular son 30 gün içinde verileri inceler ve geri sağlar.
2. Sonuçlar en çok 100.000 satır geri dönecektir.
3. Kiracı başına dakikada 45'e kadar arama yapma.
4. Kiracı sonraki 15 dakikalık döngüye kadar %100 oranına ulaştı ise, sorgular engellenir.
5. Tek bir istek 10 dakikadan uzun bir süreyle çalışırsa, zaman out ve hata döndürür.
6. HTTP `429` yanıt kodu, gönderilen istek sayısıyla veya en çok çalışan süreyle bir kotaya ulaştığını gösterir. Ulaştığımız sınırı anlamak için yanıt gövdesini okuyun. 

> [!NOTE]
> Yukarıda listelenen tüm kotalar (örneğin, dakika başına 15 çağrı) kiracı başına boyuta göredir. Bu kotalar en düşük değerdir.

## <a name="permissions"></a>İzinler

Gelişmiş av API'sini aramak için aşağıdaki izinlerden biri gereklidir. İzinleri seçme de dahil olmak üzere daha fazla bilgi edinmek için bkz. Microsoft 365 Defender [API'lerine erişme](api-access.md)

İzin türü | İzin | İzin görünen adı
-|-|-
Uygulama | AdvancedAyıldız.Read.All | Gelişmiş sorguları çalıştırma
Temsilcili (iş veya okul hesabı) | Advanced Olarak Arama.Okuma | Gelişmiş sorguları çalıştırma

>[!Note]
> Kullanıcı kimlik bilgilerini kullanarak belirteç elde edilirken:
>
>- Kullanıcının 'Verileri Görüntüle' AD rolüne sahip olması gerekir
>- Kullanıcının, cihaz grubu ayarlarına göre cihaza erişimi olması gerekir.

## <a name="http-request"></a>HTTP isteği

```HTTP
POST https://api.security.microsoft.com/api/advancedhunting/run
```

## <a name="request-headers"></a>Üstbilgi isteği

Üst bilgi | Değer
-|-
Yetkilendirme | Taşıyıcı {token} **Notu: gerekli**
İçerik Türü | application/json

## <a name="request-body"></a>İstek gövdesi

İstek gövdesinde, aşağıdaki parametreleri olan bir JSON nesnesi girin:

Parametre | Tür | Açıklama
-|-|-
Sorgu | Metin | Çalıştıracak sorgu. **Not: gerekli**

## <a name="response"></a>Yanıt

Başarılı olursa, bu yöntem yanıt `200 OK`gövdesine _ve bir QueryResponse_ nesnesi dönecektir.

Yanıt nesnesi üç üst düzey özellik içerir:

1. İstatistik - Sorgu performans istatistiklerinin bir sözlüğü.
2. Şema - Yanıtın şeması, her sütun için Name-Type çiftleridir.
3. Sonuçlar - Gelişmiş av etkinliklerinin listesi.

## <a name="example"></a>Örnek

Aşağıdaki örnekte, kullanıcı sorguyu aşağıdaki sorguyu gönderir ve içinde , ve bulunan bir API yanıt `Stats`nesnesi `Schema`alır `Results`.

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

- [Api'lere Microsoft 365 Defender erişme](api-access.md)
- [API sınırları ve lisanslama hakkında bilgi edinin](api-terms.md)
- [Hata kodlarını anlama](api-error-codes.md)
- [Gelişmiş ava genel bakış](advanced-hunting-overview.md)
