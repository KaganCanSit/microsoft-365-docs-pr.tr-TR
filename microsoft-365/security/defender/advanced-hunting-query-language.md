---
title: Microsoft 365 Defender'de gelişmiş tehdit avcılığı sorgu dilini öğrenin
description: İlk tehdit avcılığı sorgunuzu oluşturun ve yaygın işleçler ve gelişmiş tehdit avcılığı sorgu dilinin diğer yönleri hakkında bilgi edinin
keywords: gelişmiş tehdit avcılığı, tehdit avcılığı, siber tehdit avcılığı, Microsoft 365 Defender, microsoft 365, m365, arama, sorgu, dil, learn, ilk sorgu, telemetri, olaylar, telemetri, özel algılamalar, şema, kusto, operatörler, veri türleri, powershell indirme, sorgu örneği
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
ms.openlocfilehash: b9bca10cf946a7e812064f07cc3be6fa658edf39
ms.sourcegitcommit: b3f5fe84a319741583954ef8ff2ec9ec6da69bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/05/2022
ms.locfileid: "65217408"
---
# <a name="learn-the-advanced-hunting-query-language"></a>Gelişmiş tehdit avcılığı sorgu dilini öğrenme

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Şunlar için geçerlidir:**
- Microsoft 365 Defender
- Uç Nokta için Microsoft Defender

Gelişmiş avcılık[, Kusto sorgu dilini](/azure/kusto/query/) temel alır. Kusto işleçlerini ve deyimlerini kullanarak özel bir [şemadaki](advanced-hunting-schema-tables.md) bilgileri bu alan sorgular oluşturabilirsiniz. 

Kullanışlı Kusto sorgu dili temel bilgilerini öğrenmek için bu kısa videoyu izleyin.

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWRwfJ]
 
Bu kavramları daha iyi anlamak için ilk sorgunuzu çalıştırın.

## <a name="try-your-first-query"></a>İlk sorgunuzu deneyin

Microsoft 365 Defender portalında, ilk sorgunuzu çalıştırmak için **Avcılık'a** gidin. Aşağıdaki örneği kullanın: 

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

**[Bu sorguyu gelişmiş avcılıkta çalıştırın](https://security.microsoft.com/hunting?query=H4sIAAAAAAAEAI2TW0sCURSF93PQfxh8Moisp956yYIgQtLoMaYczJpbzkkTpN_et_dcdPQkcpjbmrXXWftyetKTQG5lKqmMpeB9IJksJJKZDOWdZ8wKeP5wvcm3OLgZbMXmXCmIxjnYIfcAVgYvRi8w3TnfsXEDGAG47pCCZXyP5ViO4KeNbt-Up-hEuJmB6lvButnY8XSL-cDl0M2I-GwxVX8Fe2H5zMzHiKjEVB0eEsnBrszfBIWuXOLrxCJ7VqEBfM3DWUYTkNKrv1p5y3X0jwetemzOQ_NSVuuXZ1c6aNTKRaN8VvWhY9n7OS-o6J5r7mYeQypdEKc1m1qfiqpjCSuspsDntt2J61bEvTlXls5AgQfFl5bHM_gr_BhO2RF1rztoBv2tWahrso_TtzkL93KGMGZVr2pe7eWR-xeZl91f_113UOsx3nDR4Y9j5R6kaCq8ajr_YWfFeedsd27L7it-Z6dAZyxsJq1d9-2ZOSzK3y2NVd8-zUPjtZaJnYsIH4Md7AmdeAcd2Cl1XoURc5PzXlfU8U9P54WcswL6t_TW9Q__qX-xygQAAA&runQuery=true&timeRangeId=week)**

### <a name="describe-the-query-and-specify-the-tables-to-search"></a>Sorguyu açıklama ve aranacak tabloları belirtme
Sorgunun ne için olduğunu açıklamak için sorgunun başına kısa bir açıklama eklenmiştir. Bu açıklama, daha sonra sorguyu kaydetmeye ve kuruluşunuzdaki diğer kişilerle paylaşmaya karar vermenize yardımcı olur. 

```kusto
// Finds PowerShell execution events that could involve a download
```

Sorgunun kendisi genellikle bir tablo adıyla başlar ve ardından bir kanalla (`|` ile başlayan birkaç öğe gösterilir). Bu örnekte, iki tablo  `DeviceProcessEvents` ve öğesinin birleşimini oluşturarak başlayacağız ve `DeviceNetworkEvents`gerektiğinde kanallı öğeler ekleyeceğiz.

```kusto
union DeviceProcessEvents, DeviceNetworkEvents
```
### <a name="set-the-time-range"></a>Zaman aralığını ayarlama
İlk kanallı öğe, kapsamı önceki yedi güne göre belirlenmiş bir zaman filtresidir. Zaman aralığını sınırlamak sorguların iyi performans göstermesini, yönetilebilir sonuçlar döndürmesini ve zaman aşımına neden olmamasını sağlamaya yardımcı olur.

```kusto
| where Timestamp > ago(7d)
```

### <a name="check-specific-processes"></a>Belirli işlemleri denetleme
Zaman aralığı hemen ardından PowerShell uygulamasını temsil eden işlem dosyası adları araması yapılır.

```kusto
// Pivoting on PowerShell processes
| where FileName in~ ("powershell.exe", "powershell_ise.exe")
```

### <a name="search-for-specific-command-strings"></a>Belirli komut dizelerini arama
Daha sonra sorgu, genellikle PowerShell kullanarak dosyaları indirmek için kullanılan komut satırlarındaki dizeleri arar.

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
Artık sorgunuz bulmak istediğiniz verileri net bir şekilde tanımladığınıza göre sonuçların nasıl görüneceğini tanımlayabilirsiniz. `project` belirli sütunları döndürür ve `top` sonuç sayısını sınırlar. Bu işleçler, sonuçların iyi biçimlendirildiğinden, makul ölçüde büyük ve işlenmesi kolay olduğundan emin olunmasını sağlar.

```kusto
| project Timestamp, DeviceName, InitiatingProcessFileName, InitiatingProcessCommandLine, 
FileName, ProcessCommandLine, RemoteIP, RemoteUrl, RemotePort, RemoteIPType
| top 100 by Timestamp
```

Sonuçları görmek için **Sorguyu çalıştır'ı** seçin.

>[!TIP]
>Sorgu sonuçlarını grafik olarak görüntüleyebilir ve filtreleri hızla ayarlayabilirsiniz. Yönergeler için [sorgu sonuçlarıyla çalışma hakkında bilgi edinin](advanced-hunting-query-results.md)

## <a name="learn-common-query-operators"></a>Yaygın sorgu işleçlerini öğrenme

İlk sorgunuzu çalıştırdıktan sonra bileşenleri hakkında genel bir fikir edindiniz. Biraz geri dönüp bazı temel bilgileri öğrenmenin zamanı geldi. Gelişmiş avcılık tarafından kullanılan Kusto sorgu dili, aşağıdaki yaygın olanlar da dahil olmak üzere çeşitli işleçleri destekler.

| Işleç | Açıklama ve kullanım |
|--|--|
| `where` | Bir tabloyu koşula uyan satırların alt kümesine göre filtreleyin. |
| `summarize` | Giriş tablosunun içeriğini toplayan bir tablo oluşturma. |
| `join` | Her tablodan belirtilen sütunların değerlerini eşleştirerek yeni bir tablo oluşturmak için iki tablonun satırlarını birleştirin. |
| `count` | Giriş kaydı kümesindeki kayıt sayısını döndürür. |
| `top` | Belirtilen sütunlara göre sıralanmış ilk N kayıtlarını döndürür. |
| `limit` | Belirtilen satır sayısına kadar geri dönün. |
| `project` | Eklenecek sütunları seçin, yeniden adlandırın veya bırakın ve yeni hesaplanan sütunlar ekleyin. |
| `extend` | Hesaplanmış sütunlar oluşturun ve bunları sonuç kümesine ekler. |
| `makeset` |  İfade'nin grupta aldığı ayrı değerler kümesinin dinamik (JSON) dizisini döndürür. |
| `find` | Bir tablo kümesinde koşulla eşleşen satırları bulun. |

Bu işleçlerin canlı bir örneğini görmek için bunları gelişmiş avcılık **bölümündeki Kullanmaya başlayın** bölümünden çalıştırın.

## <a name="understand-data-types"></a>Veri türlerini anlama

Gelişmiş avcılık, aşağıdaki yaygın türler de dahil olmak üzere Kusto veri türlerini destekler:

| Veri türü | Açıklama ve sorgu etkileri |
|--|--|
| `datetime` | Veri ve zaman bilgileri genellikle olay zaman damgalarını temsil eder. [Desteklenen tarih saat biçimlerine bakın](/azure/data-explorer/kusto/query/scalar-data-types/datetime) |
| `string` | UTF-8'de tek tırnak () veya çift tırnak (`'``"`) içine alınmış karakter dizesi. [Dizeler hakkında daha fazla bilgi edinin](/azure/data-explorer/kusto/query/scalar-data-types/string) |
| `bool` | Bu veri türü veya `false` durumlarını destekler`true`. [Desteklenen değişmez değerlere ve işleçlere bakın](/azure/data-explorer/kusto/query/scalar-data-types/bool) |
| `int` | 32 bit tamsayı  |
| `long` | 64 bit tamsayı |

Bu veri türleri hakkında daha fazla bilgi edinmek için [Kusto skaler veri türleri hakkında bilgi edinin](/azure/data-explorer/kusto/query/scalar-data-types/).

## <a name="get-help-as-you-write-queries"></a>Sorgu yazarken yardım alma
Sorguları daha hızlı yazmak için aşağıdaki işlevlerden yararlanın:
- **Otomatik öneri**: Sorgu yazarken gelişmiş avcılık, IntelliSense'ten öneriler sağlar. 
- **Şema ağacı**; çalışma alanınızın yanında tabloların ve sütunlarının listesini içeren bir şema gösterimidir. Daha fazla bilgi için bir öğenin üzerine gelin. Bir öğeyi sorgu düzenleyicisine eklemek için çift tıklayın.
- **[Şema başvurusu](advanced-hunting-schema-tables.md#get-schema-information-in-the-security-center)**— tablo ve sütun açıklamalarının yanı sıra desteklenen olay türleri (`ActionType` değerler) ve örnek sorgularla portal içi başvuru

## <a name="work-with-multiple-queries-in-the-editor"></a>Düzenleyicide birden çok sorguyla çalışma
Birden çok sorguyla deneme yapmak için sorgu düzenleyicisini kullanabilirsiniz. Birden çok sorgu kullanmak için:

- Her sorguyu boş bir satırla ayırın.
- Çalıştırmadan önce sorguyu seçmek için imleci sorgunun herhangi bir bölümüne getirin. Bu işlem yalnızca seçili sorguyu çalıştırır. Başka bir sorgu çalıştırmak için imleci uygun şekilde hareket ettirin ve **Sorguyu çalıştır'ı** seçin.

:::image type="content" source="../../media/multiple-queries.png" alt-text="Microsoft 365 Defender portalındaki **Yeni sorgu** sayfasında birden çok sorgu yürütme örneği" lightbox="../../media/multiple-queries.png":::

Daha verimli bir çalışma alanı için aynı avlanma sayfasında birden çok sekme de kullanabilirsiniz. **Yeni sorgunuz** için bir sekme açmak için Yeni sorgu'yu seçin.

:::image type="content" source="../../media/multitab.png" alt-text="Microsoft 365 Defender portalında Gelişmiş avcılıkta yeni oluştur'u seçerek yeni bir sekme açma" lightbox="../../media/multitab.png":::

Daha sonra yeni bir tarayıcı sekmesi açmadan farklı sorgular çalıştırabilirsiniz. 

:::image type="content" source="../../media/multitab-examples.png" alt-text="Microsoft 365 Defender portalındaki gelişmiş tehdit avcılığı sayfasından çıkmadan farklı sorgular çalıştırma" lightbox="../../media/multitab-examples.png":::

>[!NOTE] 
> Gelişmiş avcılık ile birden çok tarayıcı sekmesi kullanmak kaydedilmemiş sorgularınızı kaybetmenize neden olabilir. Bunun olmasını önlemek için, ayrı tarayıcı sekmeleri yerine gelişmiş avcılık içindeki sekme özelliğini kullanın.

## <a name="use-sample-queries"></a>Örnek sorguları kullanma

**Kullanmaya başlayın** bölümü, yaygın olarak kullanılan işleçleri kullanan birkaç basit sorgu sağlar. Bu sorguları çalıştırmayı ve küçük değişiklikler yapmayı deneyin.

:::image type="content" source="../../media/get-started-section.png" alt-text="Microsoft 365 Defender portalındaki **Gelişmiş avcılık** sayfasındaki **Başlarken** bölümü" lightbox="../../media/get-started-section.png":::

>[!NOTE]
>Temel sorgu örneklerinin dışında, belirli tehdit avcılığı senaryoları için [paylaşılan sorgulara](advanced-hunting-shared-queries.md) da erişebilirsiniz. Sayfanın sol tarafındaki paylaşılan sorguları veya [GitHub sorgu deposunu](https://aka.ms/hunting-queries) keşfedin.

## <a name="access-query-language-documentation"></a>Sorgu dili belgelerine erişme

Kusto sorgu dili ve desteklenen işleçler hakkında daha fazla bilgi için [Kusto sorgu dili belgelerine bakın](/azure/kusto/query/).

>[!NOTE]
>Bu makaledeki bazı tablolar Uç Nokta için Microsoft Defender'de kullanılamayabilir. Daha fazla veri kaynağı kullanarak tehditleri avlamak için [Microsoft 365 Defender açın](m365d-enable.md). Gelişmiş avcılık sorgularını Uç Nokta için Microsoft Defender'den geçirme bölümünde yer alan adımları izleyerek [gelişmiş avcılık iş akışlarınızı Uç Nokta için Microsoft Defender'den Microsoft 365 Defender](advanced-hunting-migrate-from-mde.md) taşıyabilirsiniz.

## <a name="related-topics"></a>İlgili konular
- [Gelişmiş avcılığa genel bakış](advanced-hunting-overview.md)
- [Sorgu sonuçlarıyla çalışın](advanced-hunting-query-results.md)
- [Paylaşılan sorguları kullanın](advanced-hunting-shared-queries.md)
- [Cihazlar, e-postalar, uygulamalar ve kimlikler arasında avlayın](advanced-hunting-query-emails-devices.md)
- [Şemayı anlayın](advanced-hunting-schema-tables.md)
- [Sorgu en iyi yöntemlerini uygulayın](advanced-hunting-best-practices.md)