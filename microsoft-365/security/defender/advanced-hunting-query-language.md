---
title: Microsoft 365 Defender'te gelişmiş arama sorgusu dilini Microsoft 365 Defender
description: İlk tehdit arama sorgunuz oluşturun ve yaygın kullanılan işleçler ve gelişmiş arama sorgusu dilinin diğer yönleri hakkında bilgi öğrenin
keywords: gelişmiş av, tehdit avı, siber tehdit avı, Microsoft 365 Defender, Microsoft 365, m365, arama, sorgu, dil, öğrenme, ilk sorgu, telemetri, olaylar, telemetri, özel algılamalar, şema, kusto, işleçler, veri türleri, powershell indirme, sorgu örneği
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
ms.openlocfilehash: 7092b4ed30400fb559751d4d939801c1982407f8
ms.sourcegitcommit: 400ef9ac34247978e3de7ecc0b376c4abb6c99d8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/27/2022
ms.locfileid: "63010885"
---
# <a name="learn-the-advanced-hunting-query-language"></a>Gelişmiş arama sorgusu dilini öğrenin

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:**
- Microsoft 365 Defender
- Uç Nokta için Microsoft Defender

Gelişmiş av, [Kusto sorgu diline dayalıdır](/azure/kusto/query/). Özel bir şemada bilgi bulunan sorguları oluşturmak için Kusto işleçlerini ve deyimlerini [kullanabilirsiniz](advanced-hunting-schema-tables.md). 

Bu kısa videoyu izleyin ve kullanışlı Bire bir sorgu diliyle ilgili temel bilgileri öğrenin.

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWRwfJ]
 
Bu kavramları daha iyi anlamak için ilk sorguyu çalıştırın.

## <a name="try-your-first-query"></a>İlk sorguyu deneme

Microsoft 365 Defender sorguyu çalıştırmak için **Atla'ya** gidin. Aşağıdaki örneği kullanın: 

```kusto
// Finds PowerShell execution events that could involve a download
union DeviceProcessEvents, DeviceNetworkEvents
| where Timestamp > ago(7d)
// Pivoting on PowerShell processes
| where FileName in~ ("powershell.exe", "powershell_ise.exe")
// Suspicious commands
| where ProcessCommandLine has_any("WebClient",
 "DownloadFile",
 "DownloadData",
 "DownloadString",
"WebRequest",
"Shellcode",
"http",
"https")
| project Timestamp, DeviceName, InitiatingProcessFileName, InitiatingProcessCommandLine, 
FileName, ProcessCommandLine, RemoteIP, RemoteUrl, RemotePort, RemoteIPType
| top 100 by Timestamp
```

**[Gelişmiş avda bu sorguyu çalıştır](https://security.microsoft.com/hunting?query=H4sIAAAAAAAEAI2TW0sCURSF93PQfxh8Moisp956yYIgQtLoMaYczJpbzkkTpN_et_dcdPQkcpjbmrXXWftyetKTQG5lKqmMpeB9IJksJJKZDOWdZ8wKeP5wvcm3OLgZbMXmXCmIxjnYIfcAVgYvRi8w3TnfsXEDGAG47pCCZXyP5ViO4KeNbt-Up-hEuJmB6lvButnY8XSL-cDl0M2I-GwxVX8Fe2H5zMzHiKjEVB0eEsnBrszfBIWuXOLrxCJ7VqEBfM3DWUYTkNKrv1p5y3X0jwetemzOQ_NSVuuXZ1c6aNTKRaN8VvWhY9n7OS-o6J5r7mYeQypdEKc1m1qfiqpjCSuspsDntt2J61bEvTlXls5AgQfFl5bHM_gr_BhO2RF1rztoBv2tWahrso_TtzkL93KGMGZVr2pe7eWR-xeZl91f_113UOsx3nDR4Y9j5R6kaCq8ajr_YWfFeedsd27L7it-Z6dAZyxsJq1d9-2ZOSzK3y2NVd8-zUPjtZaJnYsIH4Md7AmdeAcd2Cl1XoURc5PzXlfU8U9P54WcswL6t_TW9Q__qX-xygQAAA&runQuery=true&timeRangeId=week)**

### <a name="describe-the-query-and-specify-the-tables-to-search"></a>Sorguyu açıklar ve aranan tabloları belirtir
Ne için olduğunu açıklamak için sorgunun başına kısa bir açıklama eklenmiştir. Bu açıklama, daha sonra sorguyu kaydedecek ve sorguyu organizasyonunu diğerleriyle paylaşacağız. 

```kusto
// Finds PowerShell execution events that could involve a download
```

Sorgunun kendisi normalde bir tablo adı ile başlar ve bunu bir boru () ile başlatan birkaç öğe devam eder`|`. Bu örnekte, iki tabloyu bir bütün olarak oluşturarak  `DeviceProcessEvents` `DeviceNetworkEvents`ve ve gerektiğinde boruları ekerek başlayacağız.

```kusto
union DeviceProcessEvents, DeviceNetworkEvents
```
### <a name="set-the-time-range"></a>Zaman aralığını ayarlama
İlk borusu yapılan öğe, önceki yedi gün kapsamındaki bir zaman filtresidir. Zaman aralığını sınırlamak, sorguların iyi performans gösterip yönetilebilir sonuçlar elde  etmelerine ve zaman çıkmamalarına yardımcı olur.

```kusto
| where Timestamp > ago(7d)
```

### <a name="check-specific-processes"></a>Belirli işlemleri denetleme
Zaman aralığı hemen arkasından PowerShell uygulamasını temsil eden işlem dosyası adlarını arayabilir.

```kusto
// Pivoting on PowerShell processes
| where FileName in~ ("powershell.exe", "powershell_ise.exe")
```

### <a name="search-for-specific-command-strings"></a>Belirli komut dizelerini arama
Daha sonra sorgu, normalde PowerShell kullanılarak dosya indirmek için kullanılan komut satırlarında dizeler için arama yapmaktır.

```kusto
// Suspicious commands
| where ProcessCommandLine has_any("WebClient",
    "DownloadFile",
    "DownloadData",
    "DownloadString",
    "WebRequest",
    "Shellcode",
    "http",
    "https")
```

### <a name="customize-result-columns-and-length"></a>Sonuç sütunlarını ve uzunluğunu özelleştirme 
Artık sorgunuz bulmak istediğiniz verileri net bir şekilde tanımladığınıza göre, sonuçların nasıl bir görünümde olduğunu tanımlayabilirsiniz. `project` belirli sütunları döndürür ve `top` sonuç sayısını sınırlar. Bu işleçler, sonuçların iyi biçimlendirilmiş ve makul ölçüde büyük ve işlemesi kolay olmasını sağlamaya yardımcı olur.

```kusto
| project Timestamp, DeviceName, InitiatingProcessFileName, InitiatingProcessCommandLine, 
FileName, ProcessCommandLine, RemoteIP, RemoteUrl, RemotePort, RemoteIPType
| top 100 by Timestamp
```

Sonuçları **görmek için Sorguyu** çalıştır'ı seçin.

>[!TIP]
>Sorgu sonuçlarını grafik olarak ekleyebilirsiniz ve filtreleri hızla ayarlayabilirsiniz. Kılavuz için, [sorgu sonuçlarıyla çalışma hakkında bilgi](advanced-hunting-query-results.md)

## <a name="learn-common-query-operators"></a>Sık kullanılan sorgu işleçlerini öğrenme

İlk sorguyu çalıştırdınız ve bileşenleri hakkında genel bir fikirniz var. Biraz geri dönmenin ve bazı temel bilgileri öğrenmenin zamanı geldi. Gelişmiş atlar tarafından kullanılan Kusto sorgu dili, yaygın kullanılanlar da dahil olmak üzere bir dizi operatöre destek sağlar.

| İşleç | Açıklama ve kullanım |
|--|--|
| `where` | Tabloyu, bir ölçüte karşılayan satırların alt kümesine filtre uygulama. |
| `summarize` | Giriş tablonun içeriğini topan bir tablo üretin. |
| `join` | Her tabloda belirtilen sütun veya sütunların değerlerini eşleştirerek yeni bir tablo oluşturmak için iki tablonun satırlarını birleştirin. |
| `count` | Giriş kaydı kümesinde kayıtların sayısını iade eder. |
| `top` | Belirtilen sütunlara göre sıralanmış ilk N kaydı geri dönme. |
| `limit` | Belirtilen sayıda satıra kadar dönme. |
| `project` | Dahil etmek, yeniden adlandırmak veya bırakmak ve yeni hesaplanan sütunlar eklemek için sütunları seçin. |
| `extend` | Hesaplanan sütunlar oluşturun ve bunları sonuç kümesine ekler. |
| `makeset` |  Expr'in gruba kattır olduğu farklı değerler kümesi dinamik (JSON) dizisini döndürür. |
| `find` | Bir tablo kümesi genelindeki bir yüklem ile eşan satırları bulun. |

Bu işleçlerin canlı bir örneğini görmek için bunları gelişmiş **avına başlama** bölümünden çalıştırın.

## <a name="understand-data-types"></a>Veri türlerini anlama

Gelişmiş av, şu yaygın türler de dahil olmak üzere Kuşto veri türlerini destekler:

| Veri türü | Açıklama ve sorgu sonuçlarının sonuçları |
|--|--|
| `datetime` | Normalde olay zaman damgasını temsil eden veri ve saat bilgisi. [Desteklenen tarih saat biçimlerine bakın](/azure/data-explorer/kusto/query/scalar-data-types/datetime) |
| `string` | Tek tırnak () veya çift tırnak ( ) içine alınmış UTF-8`'` karakter dizesi`"`. [Dizeler hakkında daha fazla makale okuyun](/azure/data-explorer/kusto/query/scalar-data-types/string) |
| `bool` | Bu veri türü, durumları `true` destekler veya `false` durumlarını destekler. [Desteklenen değişmez metinlere ve işleçlere bakın](/azure/data-explorer/kusto/query/scalar-data-types/bool) |
| `int` | 32 bit tamsayı  |
| `long` | 64 bit tamsayı |

Bu veri türleri hakkında daha fazla bilgi edinmek için [, Kusto skaler veri türleri hakkında bilgi okuyun](/azure/data-explorer/kusto/query/scalar-data-types/).

## <a name="get-help-as-you-write-queries"></a>Sorgular yazarken yardım al
Sorguları daha hızlı yazmak için aşağıdaki işlevlerden faydalanabilirsiniz:
- **Sorgu yazmaya devam ettirdiğiniz** gibi, gelişmiş arama özelliği IntelliSense'in önerilerini sağlar. 
- **Şema ağacı**: Tablo listesini ve sütunlarını içeren bir şema gösterimi, çalışma alanınız yanında sağlanır. Daha fazla bilgi için bir öğenin üzerine gelin. Sorgu düzenleyicisine eklemek istediğiniz öğeye çift tıklayın.
- **[Şema başvurusu](advanced-hunting-schema-tables.md#get-schema-information-in-the-security-center)**— tablo ve sütun açıklamalarının yanı sıra desteklenen olay türleri (`ActionType` değerler) ve örnek sorgularla portal içinde başvuru

## <a name="work-with-multiple-queries-in-the-editor"></a>Düzenleyicide birden çok sorguyla çalışma
Birden çok sorguyla denemeler yapmak için sorgu düzenleyicisini kullanabilirsiniz. Birden çok sorgu kullanmak için:

- Her sorguyu boş bir çizgiyle birbirinden ayırabilirsiniz.
- çalıştırmadan önce imleci sorgunun herhangi bir yerine yerleştirerek o sorguyu seçin. Bu yalnızca seçili sorguyu çalıştıracak. Başka bir sorgu çalıştırmak için, imleci uygun şekilde hareket ettirin ve Sorguyu **çalıştır'ı seçin**.

:::image type="content" source="../../media/learn-work-with-multiple.png" alt-text="Portalda **New query** sayfasında birden çok sorgu yürütme Microsoft 365 Defender" lightbox="../../media/learn-work-with-multiple.png":::

## <a name="use-sample-queries"></a>Örnek sorguları kullanma

Kullanmaya **başlama bölümünde** , sık kullanılan işleçleri kullanan birkaç basit sorgu vardır. Bu sorguları çalıştırmayı ve bunlarda küçük değişiklikler yapmaya deneyin.

:::image type="content" source="../../media/get-started-section.png" alt-text="Yeni portalda **Gelişmiş av** sayfasındaki **Başlarken** Microsoft 365 Defender" lightbox="../../media/get-started-section.png":::

>[!NOTE]
>Temel sorgu örnekleri dışında, belirli tehdit avı senaryoları [için](advanced-hunting-shared-queries.md) paylaşılan sorgulara da erişebilirsiniz. Sayfanın veya ana veri havuzun sol tarafındaki [paylaşılan GitHub keşfedin](https://aka.ms/hunting-queries).

## <a name="access-query-language-documentation"></a>Access sorgu dili belgeleri

Kusto sorgu dili ve desteklenen işleçler hakkında daha fazla bilgi için [, Kusto sorgu dili belgelerine bakın](/azure/kusto/query/).

>[!NOTE]
>Bu makaledeki bazı tablolar Uç Nokta için Microsoft Defender'da kullanılamıyor olabilir. [Daha fazla Microsoft 365 Defender](m365d-enable.md) kullanarak tehdit yakalamak için çok daha fazla kaynağı açabilirsiniz. Gelişmiş av iş akışlarınızı Uç Nokta için Microsoft Defender'dan Microsoft 365 Defender için [Microsoft Defender'dan gelişmiş arama sorgularını geçirme makalesinde](advanced-hunting-migrate-from-mde.md) yer alan adımları takip edebilirsiniz.

## <a name="related-topics"></a>İlgili konular
- [Gelişmiş ava genel bakış](advanced-hunting-overview.md)
- [Sorgu sonuçlarıyla çalışma](advanced-hunting-query-results.md)
- [Paylaşılan sorguları kullanma](advanced-hunting-shared-queries.md)
- [Cihazlar, e-postalar, uygulamalar ve kimlikler arasında iş avı](advanced-hunting-query-emails-devices.md)
- [Şemayı anlama](advanced-hunting-schema-tables.md)
- [Sorguyla ilgili en iyi yöntemleri uygulama](advanced-hunting-best-practices.md)