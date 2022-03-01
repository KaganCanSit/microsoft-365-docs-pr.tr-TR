---
title: Özel Hassas Bilgi Türü Filtreleri Başvurusu
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
description: Bu makalede, özel hassas bilgi türlerine kodlanmış filtrelerin listesi görüntülenir.
ms.openlocfilehash: bcecc13776b20f8b4c61eaf499a99397931fe498
ms.sourcegitcommit: bb493f12701f6d6ee7d5e64b541adb87470bc7bc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/18/2022
ms.locfileid: "63015516"
---
# <a name="custom-sensitive-information-type-filters-reference"></a>Özel hassas bilgi türü filtreleri başvurusu

Microsoft'ta, özel hassas bilgi türleri (SIT) oluştururken filtreler veya diğer denetimleri tanımlayabilirsiniz.

## <a name="list-of-supported-filters-and-use-cases"></a>Desteklenen filtrelerin ve kullanım durumlarının listesi

### <a name="alldigitssame-exclude"></a>AllDigitsSame Exclude

Açıklama: 111-111-111 gibi, tüm basamakları yinelenen basamaklar olarak 111111111 eşleşmeleri dışlamana olanak sağlar

Filtreleri tanımlama
```xml
<Filters id="ssn_filters">
    <Filter type="AllDigitsSameFilter"></Filter>
</Filters>
```

Bunu varlık düzeyindeki kural paketinde kullanma
```xml
<Entity id="50842eb7-edc8-4019-85dd-5a5c1f2bb085" patternsProximity="300" recommendedConfidence="85"  filters="ssn_filters">
      <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_ssn" />
      </Pattern>
</Entity>
```

Bunu desen düzeyindeki kural paketinde kullanma
```xml
<Entity id="50842eb7-edc8-4019-85dd-5a5c1f2bb085" patternsProximity="300" recommendedConfidence="85">
      <Pattern confidenceLevel="85"  filters="ssn_filters">
        <IdMatch idRef="Func_ssn" />
      </Pattern>
</Entity>
```

### <a name="textmatchfilter-startswith"></a>TextMatchFilter StartsWith 

Açıklama: Varlık için başlangıç karakterlerini tanımlamaya olanak sağlar. bu modelin, dahil etmek ve hariç tutmak için iki çeşitlemesi vardır.

Örneğin, aşağıdaki gibi bir listede 0500, 91, 091, 010 ile başlayan sayıları dışarıda tutmak için:

- 0500-4500-027
- 91564721450
- 91-8523697410
- 700-8956-7844
- 1000-3265-9874
- 0100-7892-3012

Aşağıdaki xml'yi kullanabilirsiniz

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

Aşağıdaki xml'yi kullanabilirsiniz

```xml
<Filters id="phone_filters_inc">
    <Filter type="TextMatchFilter" direction="StartsWith" logic="Include" textProcessorId="Keyword_false_positives_sw">
</Filter>
```

### <a name="textmatchfilter-endswith"></a>TextMatchFilter EndsWith 

Açıklama: Varlığa ilişkin bitiş karakterlerini tanımlamaya olanak sağlar. 

Örneğin, aşağıdaki gibi bir listede 0500.91.091, 0100 ile biten sayıları dışarıda tutmak için:

- 1234567891
- 1234-5678-0091
- 1234.4567.7091
- 1234-8091-4564

Aşağıdaki xml'yi kullanabilirsiniz

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

Aşağıdaki xml'yi kullanabilirsiniz

```xml
<Filters id="phone_filters_inc">
    <Filter type="TextMatchFilter" direction=" EndsWith" logic="Include" textProcessorId="Keyword_false_positives_sw">
</Filter>
```

### <a name="textmatchfilter-full"></a>TextMatchFilter Full

Açıklama: Bazı eşleşmeleri engelleyerek kuralı tetiklemesini engellemeye olanak sağlar. Örneğin, geçerli 4111111111111111 kartı eşleşmeleri listesinden bu listede yer alan geçerli kredi kartlarını dışlayın.

Örneğin, aşağıdaki gibi bir listede yer alan 4111111111111111 3241891031113111 kredi kartı numaralarını hariç tutmak için:

- 4485 3647 3952 7352
- 4111111111111111
- 3241891031113111

Aşağıdaki xml'yi kullanabilirsiniz

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

Örneğin, aşağıdaki gibi bir listeye 4111111111111111 3241891031113111 kredi kartı numaraları eklemek için:

- 4485 3647 3952 7352
- 4111111111111111
- 3241891031113111

Aşağıdaki xml'yi kullanabilirsiniz

```xml
<Filters id="cc_filters_inc">
    <Filter type="TextMatchFilter" direction="Full" logic="Include" textProcessorId="Keyword_false_positives_full">
</Filter>
```

### <a name="textmatchfilter-prefix"></a>TextMatchFilter Prefix

Açıklama: Her zaman dahil edilecek veya hariç tutulacak önceki karakterleri tanımlamaya olanak sağlar. Örneğin, Kredi kartı numarasının önünde 'Sipariş Kimliği:' varsa geçerli eşleşmelerden eşleşmeyi kaldırın.

Örneğin, numara içeren telefon numaraları Telefon **ve** beni telefon numarasıdan önce dizelerle aramak için,  aşağıdaki gibi bir listede:

- Telefon 091-8974-653278
- Telefon 45-124576532-123
- 45-124576532-123

Aşağıdaki xml'yi kullanabilirsiniz

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

Örneğin, kredi kartı numarasından önce kredi **kartı** ve **kart #** dizeleri içeren tekrarları şu şekilde listeye eklemek için:

- Kredi kartı 45-124576532-123 
- 45-124576532-123 (telefon numarası olabilir)

Aşağıdaki xml'yi kullanabilirsiniz

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

Açıklama: Her zaman dahil edilecek veya hariç tutulacak aşağıdaki karakterleri tanımlamaya olanak sağlar. Örneğin, Kredi kartı numarasından sonra '/xuid' varsa, geçerli eşleşmelerden eşleşmeyi kaldırın.

Örneğin, bir listede sonek olarak dört basamaktan beş basamak daha varsa, en çok yineler şunların gibi olur:

- 1234-5678-9321 4500 9870 6321 48925566
- 1234-5678-9321

Aşağıdaki xml'yi kullanabilirsiniz

```xml
<Filters id="cc_number_filters_exc">
    <Filter type="TextMatchFilter" direction="Prefix" logic="Exclude" textProcessorId="Regex_false_positives_suffix">
</Filter>

  <Regexid="Regex_false_positives_suffix">(\d{4}){5,}</Regex>
```
Örneğin, bu listede olduğu gibi, / **xuidsuffix tarafından takip** edilen oluşumları hariç tutmak için:

- 1234-5678-9321 /xuid
- 1234-5678-9321

Bu xml'yi kullanabilirsiniz

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

Örneğin, bir oluşumun bu listede ikisi gibi süresi **cvv** veya süresi dolsa içermesi gerekir:

- 45-124576532-123 
- 45-124576532-123 cvv 966
- 45-124576532-123 son kullanma tarihi 23/03

Bu xml'yi kullanabilirsiniz

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

Filtreler BÜTÜN SIT'ta veya belirli bir düzende tanımlanabilir. Aşağıda bazı kod parçacıkları örnekleri verilmiştir. 

### <a name="at-sensitive-information-type-level"></a>Hassas bilgi türü düzeyinde

Varlık- Filtreler tüm alt düzenleri kapsıyor

Filtreler, o **varlıkta yer alan** herhangi bir desene / hassas türe göre sınıflandırılan tüm örneklere uygulanır

```xml
<Entity id="6443b88f-2808-482a-8e1a-3ae5026645e1" patternsProximity="300" recommendedConfidence="85" filters="CompositeFiltersAtEntityLevel">
      <Pattern confidenceLevel="85">
        <IdMatch idRef="Regex_denmark_id" />
      </Pattern>
</Entity>
```

### <a name="at-the-individual-pattern-of-the-sensitive-information-type-level"></a>Hassas bilgi türü düzeyinin tek tek deseninde

Yalnızca desen düzeyinde filtreler.

Filtre, desene göre örneklerde uygulanır.

```xml
<Entity id="50842eb7-edc8-4019-85dd-5a5c1f2bb085" patternsProximity="300" recommendedConfidence="85">
      <Pattern confidenceLevel="85"  filters="CompositeFiltersAtPattern">
        <IdMatch idRef="Keyword_cc_verification" />
      </Pattern>
</Entity>
```


### <a name="at-sensitive-information-type-level-and-an-additional-filter-on-some-of-the-patterns-of-that-entity"></a>Hassas bilgi türü düzeyinde ve o varlığın bazı desenleri üzerinde ek bir filtre

Varlık + desenli Filtreler

Filtreler, o varlık **/hassas** tür içinde yer alan düzenlerden herhangi biri tarafından sınıflandırılan tüm örneklere uygulanır. Desen düzeyi filtresi, bu modelle eşlenmiş olan örnekleri filtrelemektedir.

```xml
<Entity id="6443b88f-2808-482a-8e1a-3ae5026645e1" patternsProximity="300" recommendedConfidence="85" filters="CompositeFiltersAtEntityLevel">
      <Pattern confidenceLevel="85" filters="CompositeFiltersAtPattern">
        <IdMatch idRef="Regex_denmark_id" />
      </Pattern>
</Entity>
``` 

 

## <a name="more-information"></a>Daha fazla bilgi

- [Veri kaybını önleme hakkında bilgi](dlp-learn-about-dlp.md)

- [Hassas bilgi türü varlık tanımları](sensitive-information-type-entity-definitions.md)

- [Hassas bilgi türü işlevleri](sit-functions.md)
