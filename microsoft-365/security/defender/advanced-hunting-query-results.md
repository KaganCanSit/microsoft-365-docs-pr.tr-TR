---
title: E-Microsoft 365 Defender'de gelişmiş arama sorgusu sonuçlarıyla Microsoft 365 Defender
description: 2013'te gelişmiş avla döndürülen sorgu sonuçlarından en Microsoft 365 Defender
keywords: gelişmiş av, tehdit avı, siber tehdit avı, Microsoft 365 Defender, Microsoft 365, m365, arama, sorgu, telemetri, özel algılamalar, şema, kusto, görselleştirme, grafik, filtreler, detaya gitme
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
ms.openlocfilehash: 41427760a0a02f0dafbb9685da457a473698207c
ms.sourcegitcommit: d32654bdfaf08de45715dd362a7d42199bdc1ee7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/23/2022
ms.locfileid: "63754991"
---
# <a name="work-with-advanced-hunting-query-results"></a>Gelişmiş arama sorgusu sonuçlarıyla çalışma

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:**
- Microsoft 365 Defender
- Uç Nokta için Microsoft Defender

[!INCLUDE [Prerelease information](../includes/prerelease.md)]

Hassas bilgiler elde etmek [için gelişmiş](advanced-hunting-overview.md) arama sorgularınızı oluşturabilirsiniz, ancak daha fazla bilgi almak, belirli etkinlikleri ve göstergeleri araştırmak için sorgu sonuçlarıyla çalışabilirsiniz. Sorgu sonuçlarınız üzerinde aşağıdaki eylemleri gerçekleştirebilirsiniz:

- Sonuçları tablo veya grafik olarak görüntüleme
- Tabloları ve grafikleri dışarı aktarma
- Ayrıntılı varlık bilgilerine gitme
- Sorgularınızı sonuçlardan doğrudan ayarlama veya filtre uygulama

## <a name="view-query-results-as-a-table-or-chart"></a>Sorgu sonuçlarını tablo veya grafik olarak görüntüleme
Varsayılan olarak, gelişmiş arama sorgu sonuçlarını tablo verileri olarak görüntüler. Grafikle aynı verileri de görüntüebilirsiniz. Gelişmiş av aşağıdaki görünümleri destekler:

| Görünüm türü | Açıklama |
|--|--|
| **Tablo** | Sorgu sonuçlarını tablo biçiminde görüntüler |
| **Sütun grafik** | X ekseni üzerinde, yükseklikleri başka bir  alanından sayısal değerleri temsil eden dikey çubuklar olarak bir dizi benzersiz öğe işler |
| **Yığılmış sütun grafik** | X ekseni üzerinde, yükseklikleri bir veya daha fazla  alanlardaki sayısal değerleri temsil eden yığılmış dikey çubuklar olarak bir dizi benzersiz öğe işler |
| **Pasta grafik** | Benzersiz öğeleri temsil eden bölüm pastaları işler. Her pastanın boyutu başka bir  alanından gelen sayısal değerleri temsil eder. |
| **Pasta grafik** | Benzersiz öğeleri temsil eden bölüm yayları işler. Her yay uzunluğu başka bir  alanından gelen sayısal değerleri temsil eder. |
| **Çizgi grafik** | Bir dizi benzersiz öğe için sayısal değerler çizer ve çizilen değerleri bağlar |
| **Dağılım grafiği** | Bir dizi benzersiz öğe için sayısal değerler verir |
| **Alan grafiği** | Bir dizi benzersiz öğe için sayısal değerler çizer ve çizilen değerlerin altındaki bölümleri doldurur |

### <a name="construct-queries-for-effective-charts"></a>Etkili grafikler için sorguları oluşturma
Grafikleri işlenirken gelişmiş av, ilgi alanlarının sütunlarını ve toplanmış sayısal değerleri otomatik olarak tanımlar. Anlamlı grafikler elde etmek için, görselleştirilmiş olarak görmek istediğiniz belirli değerleri elde etmek için sorgularınızı oluşturun. Burada bazı örnek sorgular ve sonuçta elde edilen grafikler ve yer almaktadır.

#### <a name="alerts-by-severity"></a>Önem derecesine göre uyarılar
Grafiğini `summarize` oluşturmak istediğiniz değerlerin sayısal sayısını elde etmek için işleci kullanın. Aşağıdaki sorgu, önem derecesine `summarize` göre uyarıların sayısını almak için işleci kullanır.

```kusto
AlertInfo
| summarize Total = count() by Severity
```
Sonuçları işlerken, sütun grafik her önem derecesi değerini ayrı bir sütun olarak görüntüler:

:::image type="content" source="../../media/advanced-hunting-column-chart-new.png" alt-text="Portalda gelişmiş av sonuçlarını gösteren bir Microsoft 365 Defender" lightbox="../../media/advanced-hunting-column-chart-new.png":::
*Sütun grafik olarak görüntülenen önem derecesine göre uyarılar için sorgu sonuçları*


#### <a name="phishing-emails-across-top-ten-sender-domains"></a>İlk on gönderen etki alanı arasında kimlik avı e-postaları
Sonlu olmayan bir değer listesiyle uğraşıyorsanız, `Top` yalnızca en çok örneği olan değerlerin grafiğini oluşturmak için işleci kullanabilirsiniz. Örneğin, kimlik avı e-postası en çok olan ilk 10 gönderen etki alanına sahip olmak için aşağıdaki sorguyu kullanın:

```kusto
EmailEvents
| where ThreatTypes has "Phish" 
| summarize Count = count() by SenderFromDomain 
| top 10 by Count
```
Üst etki alanları arasında dağıtımı etkili bir şekilde göstermek için pasta grafik görünümünü kullanın:

:::image type="content" source="../../media/advanced-hunting-pie-chart-new.png" alt-text="Portalda gelişmiş arama sonuçlarını görüntüleyen Microsoft 365 Defender grafiği" lightbox="../../media/advanced-hunting-pie-chart-new.png":::
*Kimlik avı e-postalarının üst gönderen etki alanları arasında dağıtımını gösteren pasta grafik*

#### <a name="file-activities-over-time"></a>Zaman içinde dosya etkinlikleri
İşleci `summarize` işlevle `bin()` birlikte kullanarak, belirli bir göstergenin zaman içinde yer aldığı olayları denetlemeye devam edebilirsiniz. Aşağıdaki sorgu, dosyayla ilgili etkinlikteki `invoice.doc` depoları göstermek için, dosyayı 30 dakikalık aralıklarla içeren olayları sayar:

```kusto
CloudAppEvents
| union DeviceFileEvents
| where FileName == "invoice.doc"
| summarize FileCount = count() by bin(Timestamp, 30m)
```
Aşağıdaki çizgi grafik, şunları içeren daha fazla etkinlikle zaman dönemlerini açıkça vurgular `invoice.doc`: 

:::image type="content" source="../../media/line-chart-a.png" alt-text="Portalda gelişmiş arama sonuçlarını görüntüleyen çizgi Microsoft 365 Defender." lightbox="../../media/line-chart-a.png":::
*Zaman içinde dosyayı içeren etkinliklerin sayısını gösteren çizgi grafik*


## <a name="export-tables-and-charts"></a>Tabloları ve grafikleri dışarı aktarma
Sorguyu çalıştırdikten sonra, sonuçları **yerel dosyaya** kaydetmek için Dışarı Aktar'ı seçin. Sonuçların nasıl dışarı aktarıldıklarını seçtiğiniz görünüm belirler:

- **Tablo görünümü**— Sorgu sonuçları tablo şeklinde, çalışma kitabı olarak Microsoft Excel dışarı aktarıldı
- **Herhangi bir** grafik— Sorgu sonuçları, işlenen grafiğin JPEG görüntüsü olarak dışarı aktarıldı

## <a name="drill-down-from-query-results"></a>Sorgu sonuçlarından detaya gitme
Sorgu sonuçlarındaki bir kaydı hızla incelemek için, ilgili satırı seçerek Kayıt inceleme **panelini** açın. Panelde, seçili kayda dayalı olarak aşağıdaki bilgiler bulunur:

- **Varlıklar**—Kayıtta bulunan ana varlıkların (posta kutuları, cihazlar ve kullanıcılar) özetlenmiş görünümü, risk ve pozlama düzeyleri gibi kullanılabilir bilgilerle zenginleştirilmiştir
- **Tüm ayrıntılar**—Kayıtta sütunlardan gelen tüm değerler  

:::image type="content" source="../../media/results-inspect-record.png" alt-text="Portalda kaydı denetleme paneli olan Microsoft 365 Defender" lightbox="../../media/results-inspect-record.png":::

Sorgu sonuçlarınız içinde makine, dosya, kullanıcı, IP adresi veya URL gibi belirli bir varlık hakkında daha fazla bilgi görüntülemek için, varlık tanımlayıcısını seçerek söz konusu varlık için ayrıntılı bir profil sayfası açın.

## <a name="tweak-your-queries-from-the-results"></a>Sonuçlardan sorgularınızı ayarlama
Kayıt panelini incele'de herhangi bir sütunun sağ üç **noktayı** seçin. Bu seçenekleri kullanarak şunları yapabilirsiniz:

- Seçili değeri açıkça (`==`)
- Seçili değeri sorgunun dışında tut (`!=`)
- Sorgunuza değer eklemek için , gibi daha gelişmiş işleçler `contains`elde etmek için , ve `starts with``ends with` 

:::image type="content" source="../../media/work-with-query-tweak-query.png" alt-text="Microsoft 365 Defender portalında Kaydı incele sayfasındaki Eylem Microsoft 365 Defender bölmesi" lightbox="../../media/work-with-query-tweak-query.png":::



>[!NOTE]
>Bu makaledeki bazı tablolar, Uç Nokta için Microsoft Defender'da kullanılamıyor olabilir. [Daha fazla Microsoft 365 Defender](m365d-enable.md) kullanarak tehdit yakalamak için çok daha fazla kaynağı açabilirsiniz. Gelişmiş av iş akışlarınızı Uç Nokta için Microsoft Defender'dan Microsoft 365 Defender için [Microsoft Defender'dan gelişmiş arama sorgularını geçirme makalesinde](advanced-hunting-migrate-from-mde.md) yer alan adımları takip edebilirsiniz.

## <a name="related-topics"></a>İlgili konular
- [Gelişmiş ava genel bakış](advanced-hunting-overview.md)
- [Sorgu dilini öğrenin](advanced-hunting-query-language.md)
- [Paylaşılan sorguları kullanın](advanced-hunting-shared-queries.md)
- [Cihazlar, e-postalar, uygulamalar ve kimlikler arasında avlayın](advanced-hunting-query-emails-devices.md)
- [Şemayı anlayın](advanced-hunting-schema-tables.md)
- [Sorgu en iyi yöntemlerini uygulayın](advanced-hunting-best-practices.md)
- [Özel algılamalara genel bakış](custom-detections-overview.md)
