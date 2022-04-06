---
title: Microsoft 365 Defender'de gelişmiş tehdit avcılığı sorgu sonuçlarıyla çalışma
description: Microsoft 365 Defender'de gelişmiş avcılık tarafından döndürülen sorgu sonuçlarından en iyi şekilde emin olun
keywords: gelişmiş tehdit avcılığı, tehdit avcılığı, siber tehdit avcılığı, Microsoft 365 Defender, microsoft 365, m365, arama, sorgu, telemetri, özel algılamalar, şema, kusto, görselleştirme, grafik, filtreler, detaya gitme
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
ms.openlocfilehash: 0bfec0b56a67b1242d8dfd76b845aa273a76d27e
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2022
ms.locfileid: "64667262"
---
# <a name="work-with-advanced-hunting-query-results"></a>Gelişmiş tehdit avcılığı sorgu sonuçlarıyla çalışma

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Şunlar için geçerlidir:**
- Microsoft 365 Defender
- Uç Nokta için Microsoft Defender

[!INCLUDE [Prerelease information](../includes/prerelease.md)]

Hassas bilgiler döndürmek için [gelişmiş tehdit avcılığı](advanced-hunting-overview.md) sorgularınızı oluşturabilirsiniz ancak daha fazla içgörü elde etmek ve belirli etkinlikleri ve göstergeleri araştırmak için sorgu sonuçlarıyla da çalışabilirsiniz. Sorgu sonuçlarınızda aşağıdaki eylemleri gerçekleştirebilirsiniz:

- Sonuçları tablo veya grafik olarak görüntüleme
- Tabloları ve grafikleri dışarı aktarma
- Ayrıntılı varlık bilgilerini detaya gitme
- Sorgularınızı doğrudan sonuçlardan ayarlama veya filtre uygulama

## <a name="view-query-results-as-a-table-or-chart"></a>Sorgu sonuçlarını tablo veya grafik olarak görüntüleme

Varsayılan olarak, gelişmiş avcılık sorgu sonuçlarını tablosal veriler olarak görüntüler. Grafikle aynı verileri de görüntüleyebilirsiniz. Gelişmiş avcılık aşağıdaki görünümleri destekler:

| Görünüm türü | Açıklama |
|--|--|
| **Tablo** | Sorgu sonuçlarını tablo biçiminde görüntüler |
| **Sütun grafik** | X ekseninde bir dizi benzersiz öğeyi, yükseklikleri başka bir alandaki sayısal değerleri temsil eden dikey çubuklar olarak işler |
| **Yığılmış sütun grafik** | X ekseninde bir dizi benzersiz öğeyi, yükseklikleri bir veya daha fazla alandan sayısal değerleri temsil eden yığılmış dikey çubuklar olarak işler |
| **Pasta grafik** | Benzersiz öğeleri temsil eden bölüm pastalarını işler. Her pastanın boyutu başka bir alandaki sayısal değerleri temsil eder. |
| **Halka grafik** | Benzersiz öğeleri temsil eden bölümsel yayları işler. Her yay uzunluğu başka bir alandan sayısal değerleri temsil eder. |
| **Çizgi grafik** | Bir dizi benzersiz öğe için sayısal değerleri çizer ve çizilen değerleri bağlar |
| **Dağılım grafiği** | Bir dizi benzersiz öğe için sayısal değerler çizer |
| **Alan grafiği** | Bir dizi benzersiz öğe için sayısal değerler çizer ve çizilen değerlerin altındaki bölümleri doldurur |

### <a name="construct-queries-for-effective-charts"></a>Etkin grafikler için sorgu oluşturma

Grafikleri işlerken, gelişmiş avcılık ilgi çekici sütunları ve toplanmış sayısal değerleri otomatik olarak tanımlar. Anlamlı grafikler elde etmek için, sorgularınızı görselleştirilmiş olarak görmek istediğiniz belirli değerleri döndürecek şekilde ayarlayın. Bazı örnek sorgular ve sonuçta elde edilen grafikler aşağıda verilmiştir.

#### <a name="alerts-by-severity"></a>Önem derecesine göre uyarılar

Grafiğini `summarize` oluşturmak istediğiniz değerlerin sayısal sayısını elde etmek için işlecini kullanın. Aşağıdaki sorgu, önem derecesine göre uyarı sayısını almak için işlecini kullanır `summarize` .

```kusto
AlertInfo
| summarize Total = count() by Severity
```

Sonuçlar işlenirken, bir sütun grafiği her önem derecesini ayrı bir sütun olarak görüntüler:

:::image type="content" source="../../media/advanced-hunting-column-chart-new.png" alt-text="Microsoft 365 Defender portalında gelişmiş avcılık sonuçlarını görüntüleyen bir grafik örneği" lightbox="../../media/advanced-hunting-column-chart-new.png":::
*Uyarıların önem derecesine göre sorgu sonuçları sütun grafiği olarak görüntülenir*

#### <a name="phishing-emails-across-top-ten-sender-domains"></a>İlk on gönderen etki alanında kimlik avı e-postaları

Sınırlı olmayan değerlerin listesiyle ilgileniyorsanız işlecini `Top` kullanarak yalnızca en çok örneğe sahip değerlerin grafiğini oluşturabilirsiniz. Örneğin, en çok kimlik avı e-postasına sahip ilk 10 gönderen etki alanını almak için aşağıdaki sorguyu kullanın:

```kusto
EmailEvents
| where ThreatTypes has "Phish"
| summarize Count = count() by SenderFromDomain
| top 10 by Count
```

En üst etki alanları arasında dağıtımı etkili bir şekilde göstermek için pasta grafik görünümünü kullanın:

:::image type="content" source="../../media/advanced-hunting-pie-chart-new.png" alt-text="Microsoft 365 Defender portalında gelişmiş avcılık sonuçlarını görüntüleyen pasta grafik" lightbox="../../media/advanced-hunting-pie-chart-new.png":::
*En çok gönderen etki alanları arasında kimlik avı e-postalarının dağıtımını gösteren pasta grafik*

#### <a name="file-activities-over-time"></a>Zaman içindeki dosya etkinlikleri
`summarize` işlecini `bin()` işleviyle birlikte kullanarak belirli bir göstergeyi içeren olayları zaman içinde de kontrol edebilirsiniz. Aşağıdaki sorgu, dosyayla ilgili etkinlikteki ani artışları göstermek için dosyayla `invoice.doc` ilgili olayları 30 dakikalık aralıklarla sayar:

```kusto
CloudAppEvents
| union DeviceFileEvents
| where FileName == "invoice.doc"
| summarize FileCount = count() by bin(Timestamp, 30m)
```

Aşağıdaki çizgi grafik, içeren daha fazla etkinlik içeren zaman aralıklarını net bir şekilde vurgular `invoice.doc`:

:::image type="content" source="../../media/line-chart-a.png" alt-text="Microsoft 365 Defender portalında gelişmiş avcılık sonuçlarını görüntüleyen çizgi grafik" lightbox="../../media/line-chart-a.png":::
*Bir dosyanın zaman içindeki olay sayısını gösteren çizgi grafik*

## <a name="export-tables-and-charts"></a>Tabloları ve grafikleri dışarı aktarma

Sorguyu çalıştırdıktan sonra dışarı **aktar'ı** seçerek sonuçları yerel dosyaya kaydedin. Seçtiğiniz görünüm sonuçların nasıl dışarı aktarileceğini belirler:

- **Tablo görünümü**—Sorgu sonuçları tablo biçiminde Microsoft Excel çalışma kitabı olarak dışarı aktarılır
- **Herhangi bir grafik**—Sorgu sonuçları, işlenen grafiğin JPEG görüntüsü olarak dışarı aktarılır

## <a name="drill-down-from-query-results"></a>Sorgu sonuçlarından detaya gitme

Sorgu sonuçlarınızdaki bir kaydı hızla incelemek için ilgili satırı seçerek **Kaydı incele** panelini açın. Panel, seçili kayda göre aşağıdaki bilgileri sağlar:

- **Varlıklar**—Kayıtta bulunan ana varlıkların (posta kutuları, cihazlar ve kullanıcılar) özetlenmiş görünümü, risk ve maruz kalma düzeyleri gibi kullanılabilir bilgilerle zenginleştirilmiştir
- **Tüm ayrıntılar**—Kayıttaki sütunlardan gelen tüm değerler

:::image type="content" source="../../media/results-inspect-record.png" alt-text="Microsoft 365 Defender portalında kaydı incelemek için panel içeren seçili kayıt" lightbox="../../media/results-inspect-record.png":::

Sorgu sonuçlarınızda makine, dosya, kullanıcı, IP adresi veya URL gibi belirli bir varlık hakkında daha fazla bilgi görüntülemek için varlık tanımlayıcısını seçerek bu varlık için ayrıntılı bir profil sayfası açın.

## <a name="tweak-your-queries-from-the-results"></a>Sorgularınızı sonuçlardan ayarlama

**Kaydı incele** panelinde herhangi bir sütunun sağındaki üç noktayı seçin. Aşağıdakileri yapmak için seçenekleri kullanabilirsiniz:

- Seçili değeri`==` () açıkça arayın
- Seçili değeri sorgunun dışında tutma (`!=`)
- Sorgunuza değer eklemek için , `starts with`ve gibi `contains`daha gelişmiş işleçler edinin`ends with`

:::image type="content" source="../../media/work-with-query-tweak-query.png" alt-text="Microsoft 365 Defender portalındaki Kaydı incele sayfasındaki Eylem Türü bölmesi" lightbox="../../media/work-with-query-tweak-query.png":::

> [!NOTE]
> Bu makaledeki bazı tablolar Uç Nokta için Microsoft Defender'da kullanılamayabilir. Daha fazla veri kaynağı kullanarak tehditleri avlamak için [Microsoft 365 Defender açın](m365d-enable.md). Gelişmiş avcılık sorgularını Uç Nokta için Microsoft Defender'den geçirme bölümünde yer alan adımları izleyerek [gelişmiş avcılık iş akışlarınızı Uç Nokta için Microsoft Defender'den Microsoft 365 Defender](advanced-hunting-migrate-from-mde.md) taşıyabilirsiniz.

## <a name="related-topics"></a>İlgili konular

- [Gelişmiş avcılığa genel bakış](advanced-hunting-overview.md)
- [Sorgu dilini öğrenin](advanced-hunting-query-language.md)
- [Paylaşılan sorguları kullanın](advanced-hunting-shared-queries.md)
- [Cihazlar, e-postalar, uygulamalar ve kimlikler arasında avlayın](advanced-hunting-query-emails-devices.md)
- [Şemayı anlayın](advanced-hunting-schema-tables.md)
- [Sorgu en iyi yöntemlerini uygulayın](advanced-hunting-best-practices.md)
- [Özel algılamalara genel bakış](custom-detections-overview.md)
