---
title: Özel hassas bilgi türü filtreleri referansı
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
audience: Admin
ms.topic: reference
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Bu makalede, özel hassas bilgi türlerine kodlanabilen filtrelerin listesi gösterilir.
ms.openlocfilehash: 79e4a2520ab922248f65adf1b0506219987fe832
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66631969"
---
# <a name="custom-sensitive-information-type-filters-reference"></a>Özel hassas bilgi türü filtreleri referansı

Microsoft'ta, özel hassas bilgi türleri (SIT) oluştururken filtreler veya başka denetimler tanımlayabilirsiniz.

## <a name="list-of-supported-filters-and-use-cases"></a>Desteklenen filtrelerin ve kullanım örneklerinin listesi

### <a name="alldigitssame-exclude"></a>AllDigitsSame Exclude

Açıklama: 111111111 veya 111-111-111 gibi tüm basamakları yinelenen basamak olarak içeren eşleşmeleri hariç tutmanıza olanak tanır

Filtreleri tanımlama
```xml
<Filters id="ssn_filters">
    <Filter type="AllDigitsSameFilter"></Filter>
</Filters>
```

Varlık düzeyinde kural paketinde kullanma
```xml
<Entity id="50842eb7-edc8-4019-85dd-5a5c1f2bb085" patternsProximity="300" recommendedConfidence="85"  filters="ssn_filters">
      <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_ssn" />
      </Pattern>
</Entity>
```

Kural paketinde desen düzeyinde kullanma
```xml
<Entity id="50842eb7-edc8-4019-85dd-5a5c1f2bb085" patternsProximity="300" recommendedConfidence="85">
      <Pattern confidenceLevel="85"  filters="ssn_filters">
        <IdMatch idRef="Func_ssn" />
      </Pattern>
</Entity>
```

### <a name="textmatchfilter-startswith"></a>TextMatchFilter StartsWith 

Açıklama: Varlığın başlangıç karakterlerini tanımlamanızı sağlar. dahil edip hariç tutmak üzere iki çeşidi vardır.

Örneğin, aşağıdaki gibi bir listede 0500, 91, 091, 010 ile başlayan sayıları dışlamak için:

- 0500-4500-027
- 91564721450
- 91-8523697410
- 700-8956-7844
- 1000-3265-9874
- 0100-7892-3012

Aşağıdaki xml dosyasını kullanabilirsiniz

```xml
<Filters id="phone_number_filters_exc">
    <Filter type="TextMatchFilter" direction="StartsWith" logic="Exclude" textProcessorId="Keyword_false_positives_sw">
</Filter>
</Filters>

  <Keyword id="Keyword_false_positives_sw">
    <Group matchStyle="string">
      <Term>0500</Term>
      <Term>91</Term>
      <Term>091</Term>
      <Term>0100</Term>
    </Group>
  </Keyword>
```
Örneğin, 0500, 91, 091, 0100 ile başlayan sayıları aşağıdaki gibi bir listeye eklemek için: 

- 0500-4500-027
- 91564721450
- 91-8523697410
- 700-8956-7844
- 1000-3265-9874
- 0100-7892-3012

Aşağıdaki xml dosyasını kullanabilirsiniz

```xml
<Filters id="phone_filters_inc">
    <Filter type="TextMatchFilter" direction="StartsWith" logic="Include" textProcessorId="Keyword_false_positives_sw">
</Filter>
```

### <a name="textmatchfilter-endswith"></a>TextMatchFilter EndsWith 

Açıklama: Varlığın bitiş karakterlerini tanımlamanızı sağlar. 

Örneğin, aşağıdaki gibi bir listede 0500.91.091, 0100 ile biten sayıları dışlamak için:

- 1234567891
- 1234-5678-0091
- 1234.4567.7091
- 1234-8091-4564

Aşağıdaki xml dosyasını kullanabilirsiniz

```xml
<Filters id="phone_number_filters_exc">
    <Filter type="TextMatchFilter" direction="EndsWith" logic="Exclude" textProcessorId="Keyword_false_positives_sw">
</Filter>

  <Keyword id="Keyword_false_positives_sw">
    <Group matchStyle="string">
      <Term>0500</Term>
      <Term>91</Term>
      <Term>091</Term>
      <Term>0100</Term>
    </Group>
  </Keyword>
```

Örneğin, 0500, 91, 091, 0100 ile biten sayıları aşağıdaki gibi bir listeye eklemek için:

- 1234567891
- 1234-5678-0091
- 1234.4567.7091
- 1234-8091-4564

Aşağıdaki xml dosyasını kullanabilirsiniz

```xml
<Filters id="phone_filters_inc">
    <Filter type="TextMatchFilter" direction=" EndsWith" logic="Include" textProcessorId="Keyword_false_positives_sw">
</Filter>
```

### <a name="textmatchfilter-full"></a>TextMatchFilter Full

Açıklama: Kuralı tetiklemelerini önlemek için belirli eşleşmeleri yasaklamanıza izin verir. Örneğin, 4111111111111111 geçerli kredi kartı eşleşmeleri listesinden hariç tutun.

Örneğin, 4111111111111111 ve 3241891031113111 gibi kredi kartı numaralarını aşağıdaki gibi bir listede hariç tutmak için:

- 4485 3647 3952 7352
- 4111111111111111
- 3241891031113111

Aşağıdaki xml dosyasını kullanabilirsiniz

```xml
<Filters id="cc_number_filters_exc">
    <Filter type="TextMatchFilter" direction="Full" logic="Exclude" textProcessorId="Keyword_false_positives_full">
</Filter>

  <Keyword id="Keyword_false_positives_full">
    <Group matchStyle="string">
      <Term>4111111111111111</Term>
      <Term>3241891031113111</Term>
    </Group>
  </Keyword>
```

Örneğin, 4111111111111111 ve 3241891031113111 gibi kredi kartı numaralarını aşağıdaki gibi bir listeye eklemek için:

- 4485 3647 3952 7352
- 4111111111111111
- 3241891031113111

Aşağıdaki xml dosyasını kullanabilirsiniz

```xml
<Filters id="cc_filters_inc">
    <Filter type="TextMatchFilter" direction="Full" logic="Include" textProcessorId="Keyword_false_positives_full">
</Filter>
```

### <a name="textmatchfilter-prefix"></a>TextMatchFilter Ön Eki

Açıklama: Her zaman dahil edilmesi veya dışlanması gereken önceki karakterleri tanımlamanıza olanak tanır. Örneğin, Kredi kartı numarasından önce 'Sipariş Kimliği:' varsa, eşleşmeyi geçerli eşleşmelerden kaldırın.

Örneğin, Telefon numarası olan telefon numaralarının oluşumlarını dışlamak ve telefon **numarasından** önceki dizelerde **beni şu** şekilde bir listede aramak için:

- Telefon numarası 091-8974-653278
- Telefon 45-124576532-123
- 45-124576532-123

Aşağıdaki xml dosyasını kullanabilirsiniz

```xml
<Filters id="cc_number_filters_exc">
    <Filter type="TextMatchFilter" direction="Prefix" logic="Exclude" textProcessorId="Keyword_false_positives_prefix">
</Filter>
  <Keyword id="Keyword_false_positives_prefix">
    <Group matchStyle="string">
      <Term>phone number</Term>
      <Term>call me at</Term>
    </Group>
  </Keyword>
```

Örneğin, kredi kartı numarasından önce **kredi kartı** ve **kart #** dizeleri olan oluşumları aşağıdaki gibi bir listeye eklemek için:

- Kredi kartı 45-124576532-123 
- 45-124576532-123 (telefon numarası olabilir)

Aşağıdaki xml dosyasını kullanabilirsiniz

```xml
<Filters id="cc_filters_inc">
    <Filter type="TextMatchFilter" direction="Full" logic="Include" textProcessorId="Keyword_true_positives_prefix">
</Filter>

  <Keyword id="Keyword_true_positives_prefix">
    <Group matchStyle="string">
      <Term>credit card</Term>
      <Term>card #</Term>
    </Group>
  </Keyword
```

### <a name="textmatchfilter-suffix"></a>TextMatchFilter Soneki

Açıklama: Her zaman dahil edilmesi veya dışlanması gereken aşağıdaki karakterleri tanımlamanıza olanak tanır. Örneğin, Kredi kartı numarasının ardından '/xuid' geliyorsa, eşleşmeyi geçerli eşleşmelerden kaldırın.

Örneğin, aşağıdaki gibi bir listede sonek olarak dört basamak içeren beş örnek daha varsa, en üst dışlama oluşumları:

- 1234-5678-9321 4500 9870 6321 48925566
- 1234-5678-9321

Aşağıdaki xml dosyasını kullanabilirsiniz

```xml
<Filters id="cc_number_filters_exc">
    <Filter type="TextMatchFilter" direction="Prefix" logic="Exclude" textProcessorId="Regex_false_positives_suffix">
</Filter>

  <Regexid="Regex_false_positives_suffix">(\d{4}){5,}</Regex>
```
Örneğin, / **xuidsuffix** tarafından takip edilen oluşumları dışlamak için, örneğin bu listedekilerden biri:

- 1234-5678-9321 /xuid
- 1234-5678-9321

Bu xml dosyasını kullanabilirsiniz

```xml
<Filters id="cc_number_filters_exc">
    <Filter type="TextMatchFilter" direction="Prefix" logic="Exclude" textProcessorId="Keyword_false_positives_suffix">
</Filter>

  <Keyword id="Keyword_false_positives_suffix">
    <Group matchStyle="string">
      <Term>/xuid</Term>
    </Group>
  </Keyword>
```

Örneğin, bir oluşumu yalnızca **cvv** tarafından takip edilirse veya **süresi dolarsa** (bu listedeki iki örnek gibi) dahil etmek için:

- 45-124576532-123 
- 45-124576532-123 cvv 966
- 45-124576532-123'un süresi 03/23 doluyor

Bu xml dosyasını kullanabilirsiniz

```xml
<Filters id="cc_filters_inc">
    <Filter type="TextMatchFilter" direction="Full" logic="Include" textProcessorId="Keyword_true_positives_suffix">
</Filter>

  <Keyword id="Keyword_true_positives_suffix">
    <Group matchStyle="string">
      <Term>cvv</Term>
      <Term>expires</Term>
    </Group>
  </Keyword>
```

## <a name="using-filters-in-rule-packages"></a>Kural paketlerinde filtre kullanma

Filtreler tüm SIT üzerinde veya bir desen üzerinde tanımlanabilir. Burada bazı kod parçacıkları örnekleri verilmiştir. 

### <a name="at-sensitive-information-type-level"></a>Hassas bilgi türü düzeyinde

Varlık filtreleri - tüm alt desenleri kapsar

Filtreler, bu varlıktaki /hassas türdeki desenlerden herhangi biri tarafından sınıflandırılan **tüm** örneklere uygulanır

```xml
<Entity id="6443b88f-2808-482a-8e1a-3ae5026645e1" patternsProximity="300" recommendedConfidence="85" filters="CompositeFiltersAtEntityLevel">
      <Pattern confidenceLevel="85">
        <IdMatch idRef="Regex_denmark_id" />
      </Pattern>
</Entity>
```

### <a name="at-the-individual-pattern-of-the-sensitive-information-type-level"></a>Hassas bilgi türü düzeyinin bireysel deseninde

Yalnızca desen düzeyinde filtreler.

Filtre, desenle eşleşen örneklere uygulanır.

```xml
<Entity id="50842eb7-edc8-4019-85dd-5a5c1f2bb085" patternsProximity="300" recommendedConfidence="85">
      <Pattern confidenceLevel="85"  filters="CompositeFiltersAtPattern">
        <IdMatch idRef="Keyword_cc_verification" />
      </Pattern>
</Entity>
```


### <a name="at-sensitive-information-type-level-and-an-additional-filter-on-some-of-the-patterns-of-that-entity"></a>Hassas bilgi türü düzeyinde ve bu varlığın bazı desenleri üzerinde ek bir filtre

Varlık + desendeki filtreler

Filtreler, bu varlık/hassas türdeki desenlerden herhangi biri tarafından sınıflandırılan **tüm** örneklere uygulanır. Desen düzeyi filtresi, bu desenle eşleşen örnekleri filtreler.

```xml
<Entity id="6443b88f-2808-482a-8e1a-3ae5026645e1" patternsProximity="300" recommendedConfidence="85" filters="CompositeFiltersAtEntityLevel">
      <Pattern confidenceLevel="85" filters="CompositeFiltersAtPattern">
        <IdMatch idRef="Regex_denmark_id" />
      </Pattern>
</Entity>
``` 

 

## <a name="more-information"></a>Daha fazla bilgi

- [Microsoft Purview Veri Kaybı Önleme hakkında bilgi edinin](dlp-learn-about-dlp.md)

- [Hassas bilgi türü varlık tanımları](sensitive-information-type-entity-definitions.md)

- [Hassas bilgi türü işlevleri](sit-functions.md)
