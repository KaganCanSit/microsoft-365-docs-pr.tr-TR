---
title: Gelişmiş avda hataları işleme Microsoft 365 Defender
description: Gelişmiş av kullanırken görüntülenen hataları anlama
keywords: gelişmiş av, tehdit avı, siber tehdit avı, Microsoft 365 Defender, Microsoft 365, m365, arama, sorgu, telemetri, şema, kusto, zaman aşımı, kaynaklar, hatalar, bilinmeyen hata, sınırlar, kota, parametre, ayırma
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
ms.openlocfilehash: 8bd7d4b5191ff88fe2bd958c87e930b91f64dd5e
ms.sourcegitcommit: bf3965b46487f6f8cf900dd9a3af8b213a405989
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2021
ms.locfileid: "62989993"
---
# <a name="handle-advanced-hunting-errors"></a>Gelişmiş av hatalarını işleme

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:**
- Microsoft 365 Defender
- Uç Nokta için Microsoft Defender


Gelişmiş av, söz dizimi hatalarını ve sorguların önceden tanımlanmış kotalara ve kullanım parametrelerine ne zaman isabet ede olduğunu [bildirmek için hataları görüntüler](advanced-hunting-limits.md). Hataları giderme veya önleme hakkında ipuçları için aşağıdaki tabloya bakın.

| Hata türü | Neden | Çözüm | Hata iletisi örnekleri |
|--|--|--|--|
| Söz dizimi hataları | Sorgu, olmayan işleçlere, sütunlara, işlevlere veya tablolara yapılan başvurular da içinde olmak üzere tanınmayan adlar içerir. | [Kusto işleçlerine ve işlevlerine yapılan başvuruların doğru olduğundan](/azure/data-explorer/kusto/query/) emin olun. [Şemada doğru](advanced-hunting-schema-tables.md) gelişmiş av sütunları, işlevleri ve tabloları olup olmadığını denetleyin. Değişken dizeleri tanınmak için tırnak içine alın. Sorgularınızı yazarken IntelliSense'in otomatik tamamlama önerilerini kullanın. | `A recognition error occurred.` |
| Semantik hatalar | Sorgu geçerli işleç, sütun, işlev veya tablo adları kullandığında, yapısında ve sonuç mantığında hatalar vardır. Bazı durumlarda, gelişmiş aramada hataya neden olan operatör tanımlar. | Sorgunun yapısında hataları denetleyin. Rehberlik için [Kusto belgelerine](/azure/data-explorer/kusto/query/) bakın. Sorgularınızı yazarken IntelliSense'in otomatik tamamlama önerilerini kullanın. |  `'project' operator: Failed to resolve scalar expression named 'x'`|
| Zaman Aşımı | Sorgu, zamanlamayı zamanlamadan önce [yalnızca sınırlı bir süre içinde çalışmasına neden olabilir](advanced-hunting-limits.md). Bu hata, karmaşık sorguları çalıştırma sırasında daha sık meydana geliyor. | [Sorguyu en iyi duruma getirme](advanced-hunting-best-practices.md) | `Query exceeded the timeout period.` |
| CPU azaltma | Aynı kiracıda yapılan sorgular kiracı [boyutuna](advanced-hunting-limits.md) göre ayrılmış CPU kaynaklarını aştı. | Hizmet, CPU kaynak kullanımını her 15 dakikada bir ve günde bir denetler ve kullanım ayrılan kotanın %10'larını aştıktan sonra uyarıları görüntüler. Kullanımın %100 oranına ulaşıyorsanız, hizmet sonraki günlük veya 15 dakikalık döngüye kadar sorguları engeller. [CPU kotalarına çarpmamak için sorgularınızı en iyi duruma getirme](advanced-hunting-best-practices.md) | - `This query used X% of your organization's allocated resources for the current 15 minutes.`<br>- `You have exceeded processing resources allocated to this tenant. You can run queries again in <duration>.` |
| Sonuç boyutu sınırı aşıldı  | Sorgu için sonuç kümesi toplam boyutu üst sınırı aştı. Sonuç kümesi 10.000 kayıt sınırının kırpılabilir boyuta ulaşacak kadar büyük olduğunda bu hata oluşabilir. Büyük/büyük olasılıkla bu hatadan etkilenebilir, birden çok sütunu olan sonuçlar. | [Sorguyu en iyi duruma getirme](advanced-hunting-best-practices.md) | `Result size limit exceeded. Use "summarize" to aggregate results, "project" to drop uninteresting columns, or "take" to truncate results.` |
| Aşırı kaynak tüketimi | Sorgu aşırı miktarda kaynak tüketti ve tamamlama işlemi durduruldu. Bazı durumlarda gelişmiş av, en iyi duruma getirilmiş belirli operatörü tanımlar. | [Sorguyu en iyi duruma getirme](advanced-hunting-best-practices.md) | -`Query stopped due to excessive resource consumption.`<br>-`Query stopped. Adjust use of the <operator name> operator to avoid excessive resource consumption.` |
| Bilinmeyen hatalar | Sorgu bilinmeyen bir nedenden dolayı başarısız oldu. | Sorguyu yeniden çalıştırmayı deneyin. Bilinmeyen hataların geri dönmesine devam ederse portal üzerinden Microsoft'a ulaşın. | `An unexpected error occurred during query execution. Please try again in a few minutes.`



## <a name="related-topics"></a>İlgili konular
- [Gelişmiş arama için en iyi yöntemler](advanced-hunting-best-practices.md)
- [Kotalar ve kullanım parametreleri](advanced-hunting-limits.md)
- [Şemayı anlama](advanced-hunting-schema-tables.md)
- [Kusto Query Language overview](/azure/data-explorer/kusto/query/)