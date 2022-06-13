---
title: PowerShell kullanarak özel hassas bilgi türü oluşturma
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Uyumluluk merkezinde ilkeler için özel bir hassas bilgi türü oluşturmayı ve içeri aktarmayı öğrenin.
ms.openlocfilehash: 8678b7c218844d9963bd610b66e8b6c2c2647dea
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/10/2022
ms.locfileid: "66014530"
---
# <a name="create-a-custom-sensitive-information-type-using-powershell"></a>PowerShell kullanarak özel hassas bilgi türü oluşturma

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Bu makalede, özel [hassas bilgi türlerini](sensitive-information-type-entity-definitions.md) tanımlayan bir XML *kural paketi* dosyasının nasıl oluşturulacağı gösterilmektedir. Bu makalede, çalışan kimliğini tanımlayan özel bir hassas bilgi türü açıklanmaktadır. Bu makaledeki örnek XML'yi kendi XML dosyanız için başlangıç noktası olarak kullanabilirsiniz.

Hassas bilgi türleri hakkında daha fazla bilgi için bkz. [Hassas bilgi türleri hakkında bilgi edinin](sensitive-information-type-learn-about.md).

İyi biçimlendirilmiş bir XML dosyası oluşturduktan sonra PowerShell kullanarak dosyayı Microsoft 365 yükleyebilirsiniz. Ardından, ilkelerde özel hassas bilgi türünüzü kullanmaya hazır olursunuz. Hassas bilgileri istediğiniz gibi algılamadaki etkinliğini test edebilirsiniz.

> [!NOTE]
> PowerShell'in sağladığı ayrıntılı denetime ihtiyacınız yoksa, Microsoft Purview uyumluluk portalında özel hassas bilgi türleri oluşturabilirsiniz. Daha fazla bilgi için bkz. [Özel hassas bilgi türü oluşturma](create-a-custom-sensitive-information-type.md).

## <a name="important-disclaimer"></a>Önemli sorumluluk reddi

Microsoft Desteği içerik eşleştirme tanımları oluşturmanıza yardımcı olamaz.

Özel içerik eşleştirme geliştirme, test etme ve hata ayıklama için kendi iç BT kaynaklarınızı kullanmanız veya Microsoft Danışmanlık Hizmetleri (MCS) gibi danışmanlık hizmetlerini kullanmanız gerekir. Microsoft Desteği mühendisleri bu özellik için sınırlı destek sağlayabilir, ancak özel içerik eşleştirme önerilerinin ihtiyaçlarınızı tam olarak karşılayacağını garanti etmez.

MCS, test amacıyla normal ifadeler sağlayabilir. Ayrıca, tek bir belirli içerik örneğinde beklendiği gibi çalışmayan mevcut bir RegEx deseninde sorun giderme konusunda da yardım sağlayabilirler.

Bu makalede [dikkat edilmesi gereken olası doğrulama sorunları](#potential-validation-issues-to-be-aware-of) konusuna bakın.

Metni işlemek için kullanılan Boost.RegEx (eski adıyla RegEx++) altyapısı hakkında daha fazla bilgi için bkz [. Boost.Regex 5.1.3](https://www.boost.org/doc/libs/1_68_0/libs/regex/doc/html/).

> [!NOTE]
> Özel hassas bilgi türünüzde bir anahtar sözcüğün parçası olarak ve karakteri (&) kullanıyorsanız, karakterin çevresinde boşluklar olan bir terim daha eklemeniz gerekir. Örneğin, _değil_ `L&P`kullanın`L & P`.

## <a name="sample-xml-of-a-rule-package"></a>Kural paketinin örnek XML'i

Bu makalede oluşturacağımız kural paketinin örnek XML'i aşağıda verilmiştır. Öğeler ve öznitelikler aşağıdaki bölümlerde açıklanmıştır.

```xml
<?xml version="1.0" encoding="UTF-16"?>
<RulePackage xmlns="http://schemas.microsoft.com/office/2011/mce">
<RulePack id="DAD86A92-AB18-43BB-AB35-96F7C594ADAA">
  <Version build="0" major="1" minor="0" revision="0"/>
  <Publisher id="619DD8C3-7B80-4998-A312-4DF0402BAC04"/>
  <Details defaultLangCode="en-us">
    <LocalizedDetails langcode="en-us">
      <PublisherName>Contoso</PublisherName>
      <Name>Employee ID Custom Rule Pack</Name>
      <Description>
      This rule package contains the custom Employee ID entity.
      </Description>
    </LocalizedDetails>
  </Details>
</RulePack>
<Rules>
<!-- Employee ID -->
  <Entity id="E1CC861E-3FE9-4A58-82DF-4BD259EAB378" patternsProximity="300" recommendedConfidence="75">
    <Pattern confidenceLevel="65">
      <IdMatch idRef="Regex_employee_id"/>
    </Pattern>
    <Pattern confidenceLevel="75">
      <IdMatch idRef="Regex_employee_id"/>
      <Match idRef="Func_us_date"/>
    </Pattern>
    <Pattern confidenceLevel="85">
      <IdMatch idRef="Regex_employee_id"/>
      <Match idRef="Func_us_date"/>
      <Any minMatches="1">
        <Match idRef="Keyword_badge" minCount="2"/>
        <Match idRef="Keyword_employee"/>
      </Any>
      <Any minMatches="0" maxMatches="0">
        <Match idRef="Keyword_false_positives_local"/>
        <Match idRef="Keyword_false_positives_intl"/>
      </Any>
    </Pattern>
  </Entity>
  <Regex id="Regex_employee_id">(\s)(\d{9})(\s)</Regex>
  <Keyword id="Keyword_employee">
    <Group matchStyle="word">
      <Term>Identification</Term>
      <Term>Contoso Employee</Term>
    </Group>
  </Keyword>
  <Keyword id="Keyword_badge">
    <Group matchStyle="string">
      <Term>card</Term>
      <Term>badge</Term>
      <Term caseSensitive="true">ID</Term>
    </Group>
  </Keyword>
  <Keyword id="Keyword_false_positives_local">
    <Group matchStyle="word">
      <Term>credit card</Term>
      <Term>national ID</Term>
    </Group>
  </Keyword>
  <Keyword id="Keyword_false_positives_intl">
    <Group matchStyle="word">
      <Term>identity card</Term>
      <Term>national ID</Term>
      <Term>EU debit card</Term>
    </Group>
  </Keyword>
  <LocalizedStrings>
    <Resource idRef="E1CC861E-3FE9-4A58-82DF-4BD259EAB378">
      <Name default="true" langcode="en-us">Employee ID</Name>
      <Description default="true" langcode="en-us">
      A custom classification for detecting Employee IDs.
      </Description>
      <Description default="false" langcode="de-de">
      Description for German locale.
      </Description>
    </Resource>
  </LocalizedStrings>
</Rules>
</RulePackage>
```

## <a name="what-are-your-key-requirements-rule-entity-pattern-elements"></a>Temel gereksinimleriniz nelerdir? [Kural, Varlık, Desen öğeleri]

Bir kural için XML şemasının temel yapısını anlamanız önemlidir. Yapıyı anlamanız, özel hassas bilgi türünüzün doğru içeriği tanımlamasına yardımcı olur.

Kural bir veya daha fazla varlığı tanımlar (hassas bilgi türleri olarak da bilinir). Her varlık bir veya daha fazla desen tanımlar. Desen, bir ilke içeriği değerlendirirken (örneğin, e-posta ve belgeler) arar.

XML işaretlemesinde "kurallar", hassas bilgi türünü tanımlayan desenler anlamına gelir. Bu makaledeki kurallarla ilgili başvuruları, diğer Microsoft özelliklerinde yaygın olarak kullanılan "koşullar" veya "eylemler" ile ilişkilendirmayın.

### <a name="simplest-scenario-entity-with-one-pattern"></a>En basit senaryo: Tek desenli varlık

İşte basit bir senaryo: İlkenizin kuruluşunuzda kullanılan dokuz basamaklı çalışan kimliklerini içeren içeriği tanımlamasını istiyorsunuz. Desen, kuraldaki dokuz basamaklı sayıları tanımlayan normal ifadeye başvurur. Dokuz basamaklı bir sayı içeren tüm içerikler deseni karşılar.

![Tek desenli varlığın diyagramı.](../media/4cc82dcf-068f-43ff-99b2-bac3892e9819.png)

Ancak bu düzen, daha uzun sayılar veya çalışan kimlikleri olmayan diğer dokuz basamaklı sayı türleri de dahil olmak üzere dokuz basamaklı **sayıları tanımlayabilir.** Bu tür istenmeyen *eşleşmeler hatalı pozitif* olarak bilinir.

### <a name="more-common-scenario-entity-with-multiple-patterns"></a>Daha yaygın senaryo: birden çok desene sahip varlık

Hatalı pozitifler olasılığı nedeniyle, genellikle bir varlığı tanımlamak için birden fazla desen kullanırsınız. Birden çok desen, hedef varlık için destekleyici kanıt sağlar. Örneğin, ek anahtar sözcükler, tarihler veya diğer metinler özgün varlığı (örneğin dokuz basamaklı çalışan numarası) tanımlamaya yardımcı olabilir.

Örneğin, çalışan kimliği içeren içeriği tanımlama olasılığını artırmak için, aranacak diğer desenleri tanımlayabilirsiniz:

- İşe alma tarihini tanımlayan desen.
- Hem işe alma tarihini hem de "çalışan kimliği" anahtar sözcüğünü tanımlayan desen.

![Birden çok desene sahip varlığın diyagramı.](../media/c8dc2c9d-00c6-4ebc-889a-53b41a90024a.png)

Birden çok desen eşleşmesi için dikkate alınması gereken önemli noktalar vardır:

- Daha fazla kanıt gerektiren desenler daha yüksek güvenilirlik düzeyine sahiptir. Güvenilirlik düzeyine bağlı olarak aşağıdaki eylemleri gerçekleştirebilirsiniz:
  - Daha yüksek güvenilirlik eşleşmeleriyle daha kısıtlayıcı eylemler (örneğin, içeriği engelle) kullanın.
  - Daha düşük güvenilirlik eşleşmeleriyle daha az kısıtlayıcı eylemler (bildirim gönderme gibi) kullanın.

- Destekleyici `IdMatch` ve `Match` öğeler, öğesinin değil, öğesinin alt öğeleri `Rule` olan RegExes ve anahtar sözcüklere başvurur `Pattern`. Bu destekleyici öğelere `Pattern`tarafından başvurulur, ancak öğesine `Rule`dahil edilir. Bu davranış, normal ifade veya anahtar sözcük listesi gibi bir destekleyici öğenin tek bir tanımına birden çok varlık ve desen tarafından başvurulabileceği anlamına gelir.

## <a name="what-entity-do-you-need-to-identify-entity-element-id-attribute"></a>Hangi varlığı tanımlamanız gerekiyor? [Entity öğesi, ID özniteliği]

Varlık, iyi tanımlanmış bir desene sahip olan kredi kartı numarası gibi hassas bir bilgi türüdür. Her varlığın kimliği benzersiz bir GUID'si vardır.

### <a name="name-the-entity-and-generate-its-guid"></a>Varlığı adlandırın ve GUID'sini oluşturun

1. seçtiğiniz XML düzenleyicisinde ve `Entity` öğelerini ekleyin`Rules`.
2. Çalışan Kimliği gibi özel varlığınızın adını içeren bir açıklama ekleyin. Daha sonra, varlık adını yerelleştirilmiş dizeler bölümüne ekleyeceksiniz ve ilke oluşturduğunuzda bu ad yönetim merkezinde görünür.
3. Varlığınız için benzersiz bir GUID oluşturun. Örneğin, Windows PowerShell içinde komutunu `[guid]::NewGuid()`çalıştırabilirsiniz. Daha sonra, GUID'yi varlığın yerelleştirilmiş dizeler bölümüne de ekleyeceksiniz.

![Kuralları ve Varlık öğelerini gösteren XML işaretlemesi.](../media/c46c0209-0947-44e0-ac3a-8fd5209a81aa.png)

## <a name="what-pattern-do-you-want-to-match-pattern-element-idmatch-element-regex-element"></a>Hangi deseni eşleştirmek istiyorsunuz? [Pattern öğesi, IdMatch öğesi, Regex öğesi]

Desen, hassas bilgi türünün aradığı şeyin listesini içerir. Desen RegExes, anahtar sözcükler ve yerleşik işlevleri içerebilir. İşlevler tarihleri veya adresleri bulmak için RegExes çalıştırma gibi bir görev yapar. Hassas bilgi türlerinin benzersiz güvenleri olan birden çok deseni olabilir.

Aşağıdaki diyagramda, tüm desenler aynı normal ifadeye başvurur. Bu RegEx, boşlukla `(\s) ... (\s)`çevrili dokuz basamaklı bir sayı `(\d{9})` arar. Bu normal ifadeye öğesi tarafından `IdMatch` başvurulur ve Çalışan Kimliği varlığının arandığı tüm desenler için ortak gereksinimdir. `IdMatch` , desenin eşleşmeye çalıştığı tanımlayıcıdır. Bir `Pattern` öğenin tam olarak bir `IdMatch` öğesi olmalıdır.

![Tek Regex öğesine başvuran birden çok Pattern öğesini gösteren XML işaretlemesi.](../media/8f3f497b-3b8b-4bad-9c6a-d9abf0520854.png)

Memnun desen eşleşmesi, ilkenizdeki koşullarda kullanabileceğiniz bir sayı ve güvenilirlik düzeyi döndürür. bir ilkeye hassas bilgi türünü algılamak için bir koşul eklediğinizde, aşağıdaki diyagramda gösterildiği gibi sayı ve güvenilirlik düzeyini düzenleyebilirsiniz. Güvenilirlik düzeyi (eşleşme doğruluğu olarak da adlandırılır) bu makalenin ilerleyen bölümlerinde açıklanmıştır.

![Örnek sayısı ve eşleşme doğruluğu seçenekleri.](../media/sit-confidence-level.png)

Normal ifadeler güçlü olduğundan bilmeniz gereken sorunlar vardır. Örneğin, çok fazla içerik tanımlayan bir RegEx performansı etkileyebilir. Bu sorunlar hakkında daha fazla bilgi edinmek için bu makalenin devamında [dikkat edilmesi gereken olası doğrulama sorunları](#potential-validation-issues-to-be-aware-of) bölümüne bakın.

## <a name="do-you-want-to-require-additional-evidence-match-element-mincount-attribute"></a>Ek kanıta mı ihtiyacınız var? [Match öğesi, minCount özniteliği]

düzenine ek olarak `IdMatch`öğesini kullanarak `Match` anahtar sözcük, RegEx, tarih veya adres gibi ek destekleyici kanıtlar gerektirebilir.

Bir `Pattern` , birden çok `Match` öğe içerebilir:

- Doğrudan öğesinde `Pattern` .
- öğesi kullanılarak birleştirilir `Any` .

`Match` öğeleri örtük bir AND işleciyle birleştirilir. Başka bir deyişle, desenin eşleşmesi için tüm `Match` öğelerin karşılanması gerekir.

VE veya OR işleçlerini tanıtmak için öğesini kullanabilirsiniz `Any` . `Any` öğesi bu makalenin ilerleyen bölümlerinde açıklanmıştır.

Her `Match` öğe için kaç eşleşme örneğinin bulunması gerektiğini belirtmek için isteğe bağlı `minCount` özniteliğini kullanabilirsiniz. Örneğin, bir desenin yalnızca bir anahtar sözcük listesinden en az iki anahtar sözcük bulunduğunda karşılandığını belirtebilirsiniz.

![MinOccurs özniteliğine sahip Match öğesini gösteren XML işaretlemesi.](../media/607f6b5e-2c7d-43a5-a131-a649f122e15a.png)

### <a name="keywords-keyword-group-and-term-elements-matchstyle-and-casesensitive-attributes"></a>Anahtar Sözcükler [Anahtar Sözcük, Grup ve Terim öğeleri, matchStyle ve caseSensitive öznitelikleri]

Daha önce açıklandığı gibi, hassas bilgilerin tanımlanması için genellikle destekleyici kanıt olarak ek anahtar sözcükler gerekir. Örneğin, dokuz basamaklı bir sayıyı eşleştirmenin yanı sıra Anahtar Sözcük öğesini kullanarak "kart", "rozet" veya "kimlik" gibi sözcükleri de arayabilirsiniz. öğesi, `Keyword` birden çok desen veya varlıktaki birden çok `Match` öğe tarafından başvurulabilen bir `ID` özniteliğe sahiptir.

Anahtar sözcükler bir öğedeki `Group` öğelerin listesi `Term` olarak eklenir. öğesinin `Group` iki olası değeri olan bir `matchStyle` özniteliği vardır:

- **matchStyle="word"**: Sözcük eşleşmesi, boşluk veya diğer sınırlayıcılarla çevrili tüm sözcükleri tanımlar. Asya dillerindeki **sözcüklerin** veya sözcüklerin parçalarını eşleştirmeniz gerekmediği sürece her zaman sözcük kullanmalısınız.

- **matchStyle="string"**: Dize eşleşmesi, etrafı ne olursa olsun dizeleri tanımlar. Örneğin, "Kimlik" "teklif" ve "fikir" ile eşleşir. Yalnızca Asya sözcüklerini eşleştirmeniz gerektiğinde veya anahtar sözcüğünüz diğer dizelere dahil edilebilirse kullanın `string` .

Son olarak, içeriğin küçük harf ve büyük harf de dahil olmak üzere anahtar sözcükle tam olarak eşleşmesi gerektiğini belirtmek için öğesinin özniteliğini `Term` kullanabilirsiniz`caseSensitive`.

![Anahtar sözcüklere başvuran Öğeleri eşleştir seçeneğini gösteren XML işaretlemesi.](../media/e729ba27-dec6-46f4-9242-584c6c12fd85.png)

### <a name="regular-expressions-regex-element"></a>Normal ifadeler [Regex öğesi]

Bu örnekte, çalışan `ID` varlığı desen için normal ifadeye başvurmak için öğesini zaten kullanır `IdMatch` : boşlukla çevrili dokuz basamaklı bir sayı. Buna ek olarak, bir desen, abd posta kodu biçiminde beş basamaklı veya dokuz basamaklı bir sayı gibi doğrulayıcı kanıtı tanımlamak için ek `Regex` bir öğeye başvurmak için bir öğe kullanabilir`Match`.

### <a name="additional-patterns-such-as-dates-or-addresses-built-in-functions"></a>Tarihler veya adresler gibi ek desenler [yerleşik işlevler]

Hassas bilgi türleri, doğrulama kanıtlarını tanımlamak için yerleşik işlevleri de kullanabilir. Örneğin, ABD tarihi, AB tarihi, son kullanma tarihi veya ABD adresi. Microsoft 365 kendi özel işlevlerinizi karşıya yüklemeyi desteklemez. Ancak özel bir hassas bilgi türü oluşturduğunuzda varlığınız yerleşik işlevlere başvurabilir.

Örneğin, bir çalışan kimliği rozetinin işe alma tarihi vardır, bu nedenle bu özel varlık, ABD'de `Func_us_date` yaygın olarak kullanılan biçimdeki bir tarihi tanımlamak için yerleşik işlevi kullanabilir.

Daha fazla bilgi için bkz [. Hassas bilgi türü işlevleri](sit-functions.md).

![Yerleşik işleve başvuran Match öğesini gösteren XML işaretlemesi.](../media/dac6eae3-9c52-4537-b984-f9f127cc9c33.png)

## <a name="different-combinations-of-evidence-any-element-minmatches-and-maxmatches-attributes"></a>Farklı kanıt bileşimleri [Herhangi bir öğe, minMatches ve maxMatches öznitelikleri]

Bir `Pattern` öğede, tüm `IdMatch` ve `Match` öğeleri örtük bir AND işleciyle birleştirilir. Başka bir deyişle, desenin karşılanabilmesi için önce tüm eşleşmelerin karşılanması gerekir.

Öğeleri gruplandırmak `Match` için öğesini kullanarak `Any` daha esnek eşleştirme mantığı oluşturabilirsiniz. Örneğin, öğesini tüm, hiçbiri veya alt `Match` öğelerinin tam alt kümesiyle eşleştirmek için kullanabilirsiniz`Any`.

`Any` öğesi, desen eşleşmeden önce kaç alt `Match` öğenin karşılanması gerektiğini tanımlamak için kullanabileceğiniz isteğe bağlı `minMatches` ve `maxMatches` özniteliklere sahiptir. Bu öznitelikler, eşleşmeler için bulunan kanıt örneklerinin sayısını değil, öğe sayısını tanımlar. `Match` Listeden iki anahtar sözcük gibi belirli bir eşleşme için en az sayıda örnek tanımlamak için `Match` bir öğenin özniteliğini `minCount` kullanın (yukarıya bakın).

### <a name="match-at-least-one-child-match-element"></a>En az bir alt eşleşme öğesi eşleştir

Yalnızca en az sayıda öğe gerektirmek `Match` için özniteliğini `minMatches` kullanabilirsiniz. Aslında, bu `Match` öğeler örtük bir OR işleci tarafından birleştirilir. BU `Any` öğe, ABD biçimli bir tarih veya iki listeden bir anahtar sözcük bulunursa memnun olur.

```xml
<Any minMatches="1" >
     <Match idRef="Func_us_date" />
     <Match idRef="Keyword_employee" />
     <Match idRef="Keyword_badge" />
</Any>
```

### <a name="match-an-exact-subset-of-any-children-match-elements"></a>Alt öğelerin tam alt kümesini eşleştir Öğeleri eşleştir

Tam sayıda `Match` öğe gerektirmek için ve `maxMatches` değerlerini aynı değere ayarlayın`minMatches`. Bu `Any` öğe yalnızca tam olarak bir tarih veya anahtar sözcük bulunduğunda karşılanır. Başka eşleşmeler varsa, desen eşleşmez.

```xml
<Any minMatches="1" maxMatches="1" >
     <Match idRef="Func_us_date" />
     <Match idRef="Keyword_employee" />
     <Match idRef="Keyword_badge" />
</Any>
```

### <a name="match-none-of-children-match-elements"></a>Alt öğelerin hiçbirini eşleştirme Öğeleri eşleştir

Bir desenin karşılanması için belirli bir kanıtın olmamasını istiyorsanız, hem minMatches hem de maxMatches değerini 0 olarak ayarlayabilirsiniz. Bu, bir anahtar sözcük listeniz veya hatalı pozitiflik gösterme olasılığı olan başka bir kanıtınız varsa yararlı olabilir.

Örneğin, çalışan kimliği varlığı bir "kimlik kartına" başvurabileceğinden "kart" anahtar sözcüğünü arar. Ancak, kart yalnızca "kredi kartı" ifadesinde görünüyorsa, bu içerikteki "kart" ifadesi "kimlik kartı" anlamına gelmez. Bu nedenle, deseni karşılamaktan dışlamak istediğiniz terimler listesine anahtar sözcük olarak "kredi kartı" ekleyebilirsiniz.

```xml
<Any minMatches="0" maxMatches="0" >
    <Match idRef="Keyword_false_positives_local" />
    <Match idRef="Keyword_false_positives_intl" />
</Any>
```

### <a name="match-a-number-of-unique-terms"></a>Bir dizi benzersiz terimle eşleşme

Bir dizi benzersiz terimle eşleştirmek istiyorsanız, aşağıdaki örnekte gösterildiği gibi *true* olarak ayarlanmış *uniqueResults* parametresini kullanın:

```xml
<Pattern confidenceLevel="75">
    <IdMatch idRef="Salary_Revision_terms" />
    <Match idRef=" Salary_Revision_ID " minCount="3" uniqueResults="true" />
</Pattern>
```

Bu örnekte, en az üç benzersiz eşleşme kullanılarak maaş düzeltmesi için bir desen tanımlanmıştır.

## <a name="how-close-to-the-entity-must-the-other-evidence-be-patternsproximity-attribute"></a>Diğer kanıtın varlığa ne kadar yakın olması gerekir? [patternsProximity özniteliği]

Hassas bilgi türünüz bir çalışan kimliğini temsil eden bir desen arıyor ve bu düzenin bir parçası olarak da "ID" gibi bir anahtar sözcük gibi doğrulayıcı kanıtlar arıyor. Bu kanıt ne kadar yakın olursa, desenin gerçek bir çalışan kimliği olma olasılığının da o kadar yüksek olması mantıklıdır. Entity öğesinin gerekli patternsProximity özniteliğini kullanarak desendeki diğer kanıtların varlığa ne kadar yakın olması gerektiğini belirleyebilirsiniz.

![patternsProximity özniteliğini gösteren XML işaretlemesi.](../media/e97eb7dc-b897-4e11-9325-91c742d9839b.png)

Varlıktaki her desen için patternsProximity öznitelik değeri, bu Desen için belirtilen diğer tüm Eşleşmeler için IdMatch konumundan uzaklığı (Unicode karakterlerinde) tanımlar. Yakınlık penceresi IdMatch konumuna sabitlenmiştir ve pencere IdMatch'in soluna ve sağına uzanır.

![Yakınlık penceresinin diyagramı.](../media/b593dfd1-5eef-4d79-8726-a28923f7c31e.png)

Aşağıdaki örnekte, yakınlık penceresinin, çalışan kimliği özel varlığı için IdMatch öğesinin anahtar sözcük veya tarihin en az bir eşleştirilmesini gerektirdiği desen eşleştirmesini nasıl etkilediği gösterilmektedir. Kimlik2 ve ID3 için yakınlık penceresinde yalnızca kısmi doğrulama kanıtı bulunduğundan yalnızca ID1 eşleşir.

![Doğrulayıcı kanıt ve yakınlık penceresinin diyagramı.](../media/dc68e38e-dfa1-45b8-b204-89c8ba121f96.png)

E-posta için ileti gövdesinin ve her ekin ayrı öğeler olarak ele alındığını unutmayın. Bu, yakınlık penceresinin bu öğelerin her birinin sonunun ötesine geçmediği anlamına gelir. Her öğe (ek veya gövde) için hem idMatch hem de corroborative kanıtının bu öğede bulunması gerekir.

## <a name="what-are-the-right-confidence-levels-for-different-patterns-confidencelevel-attribute-recommendedconfidence-attribute"></a>Farklı desenler için doğru güvenilirlik düzeyleri nelerdir? [confidenceLevel özniteliği, recommendedConfidence özniteliği]

Bir desenin gerektirdiği kanıt ne kadar fazlaysa, desen eşleştiğinde gerçek bir varlığın (çalışan kimliği gibi) belirlendiğinden o kadar emin olursunuz. Örneğin, dokuz basamaklı kimlik numarası, işe alma tarihi ve anahtar sözcük gerektiren bir desene, yalnızca dokuz basamaklı kimlik numarası gerektiren bir düzende olduğundan daha fazla güvenirsiniz.

Pattern öğesinin gerekli bir confidenceLevel özniteliği vardır. ConfidenceLevel değerini (1 ile 100 arasında bir tamsayı) bir varlıktaki her desen için benzersiz bir kimlik olarak düşünebilirsiniz; bir varlıktaki desenlerin atadığınız farklı güvenilirlik düzeylerine sahip olması gerekir. Tamsayının tam değeri önemli değildir; uyumluluk ekibiniz için anlamlı sayılar seçmeniz yeterlidir. Özel hassas bilgi türünüzü karşıya yükleyip bir ilke oluşturduktan sonra, oluşturduğunuz kuralların koşullarında bu güvenilirlik düzeylerine başvurabilirsiniz.

![confidenceLevel özniteliği için farklı değerlere sahip Desen öğelerini gösteren XML işaretlemesi.](../media/sit-xml-markedup-2.png)

Her Pattern için confidenceLevel'e ek olarak, Varlığın önerilen birConfidence özniteliği vardır. Önerilen güvenilirlik özniteliği, kural için varsayılan güvenilirlik düzeyi olarak düşünülebilir. İlkede kural oluşturduğunuzda, kuralın kullanması için bir güvenilirlik düzeyi belirtmezseniz, bu kural varlık için önerilen güvenilirlik düzeyine göre eşleşecektir. Kural Paketindeki her Varlık Kimliği için önerilenConfidence özniteliğinin zorunlu olduğunu, eksikse Hassas Bilgi Türünü kullanan ilkeleri kaydedemeyeceğinizi lütfen unutmayın.

## <a name="do-you-want-to-support-other-languages-in-the-ui-of-the-compliance-center-localizedstrings-element"></a>Uyumluluk merkezinin kullanıcı arabiriminde diğer dilleri desteklemek istiyor musunuz? [LocalizedStrings öğesi]

Uyumluluk ekibiniz farklı yerel ayarlarda ve farklı dillerde ilke oluşturmak için Microsoft Purview uyumluluk portalını kullanıyorsa, özel hassas bilgi türünüzün adının ve açıklamasının yerelleştirilmiş sürümlerini sağlayabilirsiniz. Uyumluluk ekibiniz desteklediğiniz bir dilde Microsoft 365 kullandığında kullanıcı arabiriminde yerelleştirilmiş adı görür.

![Örnek sayısı ve eşleşme doğruluğu yapılandırması.](../media/11d0b51e-7c3f-4cc6-96d8-b29bcdae1aeb.png)

Rules öğesi, özel varlığınızın GUID'sine başvuran bir Resource öğesini içeren bir LocalizedStrings öğesi içermelidir. Buna karşılık, her Resource öğesi belirli bir dil için yerelleştirilmiş bir dize sağlamak üzere langcode özniteliğini kullanan bir veya daha fazla Ad ve Açıklama öğesi içerir.

![LocalizedStrings öğesinin içeriğini gösteren XML işaretlemesi.](../media/a96fc34a-b93d-498f-8b92-285b16a7bbe6.png)

Yerelleştirilmiş dizeleri yalnızca özel hassas bilgi türünüzün Uyumluluk merkezi kullanıcı arabiriminde nasıl göründüğü için kullandığınızı unutmayın. Bir anahtar sözcük listesinin veya normal ifadenin farklı yerelleştirilmiş sürümlerini sağlamak için yerelleştirilmiş dizeleri kullanamazsınız.

## <a name="other-rule-package-markup-rulepack-guid"></a>Diğer kural paketi işaretlemesi [RulePack GUID]

Son olarak, her RulePackage'ın başlangıcı, doldurmanız gereken bazı genel bilgileri içerir. Aşağıdaki işaretlemeyi şablon olarak kullanabilir ve ". . ." yer tutucularını kendi bilgilerinizle birlikte kullanın.

En önemlisi, RulePack için bir GUID oluşturmanız gerekir. Yukarıda, varlık için bir GUID oluşturacaksınız; Bu, RulePack için ikinci bir GUID'dir. GUID oluşturmanın çeşitli yolları vardır, ancak bunu PowerShell'de [guid]::NewGuid() yazarak kolayca yapabilirsiniz.

Version öğesi de önemlidir. Kural paketinizi ilk kez karşıya yüklediğinizde Microsoft 365 sürüm numarasını not edin. Daha sonra kural paketini güncelleştirir ve yeni bir sürüm yüklerseniz sürüm numarasını güncelleştirdiğinizden emin olun; Microsoft 365 kural paketini dağıtmaz.

```xml
<?xml version="1.0" encoding="utf-16"?>
<RulePackage xmlns="http://schemas.microsoft.com/office/2011/mce">
  <RulePack id=". . .">
    <Version major="1" minor="0" build="0" revision="0" />
    <Publisher id=". . ." />
    <Details defaultLangCode=". . .">
      <LocalizedDetails langcode=" . . . ">
         <PublisherName>. . .</PublisherName>
         <Name>. . .</Name>
         <Description>. . .</Description>
      </LocalizedDetails>
    </Details>
  </RulePack>

 <Rules>
  . . .
 </Rules>
</RulePackage>
```

Tamamlandığında RulePack öğeniz şöyle görünmelidir.

![RulePack öğesini gösteren XML işaretlemesi.](../media/fd0f31a7-c3ee-43cd-a71b-6a3813b21155.png)

## <a name="validators"></a>Doğrulayıcıları

Microsoft 365, yaygın olarak kullanılan SID'ler için işlev işlemcilerini doğrulayıcı olarak kullanıma sunar. İşte bunların listesi.

### <a name="list-of-currently-available-validators"></a>Şu anda kullanılabilir doğrulayıcıların listesi

- `Func_credit_card`
- `Func_ssn`
- `Func_unformatted_ssn`
- `Func_randomized_formatted_ssn`
- `Func_randomized_unformatted_ssn`
- `Func_aba_routing`
- `Func_south_africa_identification_number`
- `Func_brazil_cpf`
- `Func_iban`
- `Func_brazil_cnpj`
- `Func_swedish_national_identifier`
- `Func_india_aadhaar`
- `Func_uk_nhs_number`
- `Func_Turkish_National_Id`
- `Func_australian_tax_file_number`
- `Func_usa_uk_passport`
- `Func_canadian_sin`
- `Func_formatted_itin`
- `Func_unformatted_itin`
- `Func_dea_number_v2`
- `Func_dea_number`
- `Func_japanese_my_number_personal`
- `Func_japanese_my_number_corporate`

Bu sayede kendi RegEx'inizi tanımlayabilir ve bunları doğrulayabilirsiniz. Doğrulayıcıları kullanmak için kendi RegEx'inizi tanımlayın ve özelliğini kullanarak `Validator` istediğiniz işlev işlemcisini ekleyin. Tanımlandıktan sonra, bu RegEx'i bir SIT'te kullanabilirsiniz.

Aşağıdaki örnekte, Kredi kartı için normal bir ifade - Regex_credit_card_AdditionalDelimiters tanımlanmıştır ve daha sonra Func_credit_card doğrulayıcı olarak kullanılarak kredi kartı için sağlama toplamı işlevi kullanılarak doğrulanır.

```xml
<Regex id="Regex_credit_card_AdditionalDelimiters" validators="Func_credit_card"> (?:^|[\s,;\:\(\)\[\]"'])([0-9]{4}[ -_][0-9]{4}[ -_][0-9]{4}[ -_][0-9]{4})(?:$|[\s,;\:\(\)\[\]"'])</Regex>
<Entity id="675634eb7-edc8-4019-85dd-5a5c1f2bb085" patternsProximity="300" recommendedConfidence="85">
<Pattern confidenceLevel="85">
<IdMatch idRef="Regex_credit_card_AdditionalDelimiters" />
<Any minMatches="1">
<Match idRef="Keyword_cc_verification" />
<Match idRef="Keyword_cc_name" />
<Match idRef="Func_expiration_date" />
</Any>
</Pattern>
</Entity>
```

Microsoft 365 iki genel doğrulayıcı sağlar

### <a name="checksum-validator"></a>Sağlama toplamı doğrulayıcısı

Bu örnekte, Çalışan Kimliği için RegEx'i doğrulamak için çalışan kimliği için sağlama toplamı doğrulayıcısı tanımlanmıştır.

```xml
<Validators id="EmployeeIDChecksumValidator">
<Validator type="Checksum">
<Param name="Weights">2, 2, 2, 2, 2, 1</Param>
<Param name="Mod">28</Param>
<Param name="CheckDigit">2</Param> <!-- Check 2nd digit -->
<Param name="AllowAlphabets">1</Param> <!— 0 if no Alphabets -->
</Validator>
</Validators>
<Regex id="Regex_EmployeeID" validators="ChecksumValidator">(\d{5}[A-Z])</Regex>
<Entity id="675634eb7-edc8-4019-85dd-5a5c1f2bb085" patternsProximity="300" recommendedConfidence="85">
<Pattern confidenceLevel="85">
<IdMatch idRef="Regex_EmployeeID"/>
</Pattern>
</Entity>
```

### <a name="date-validator"></a>Tarih Doğrulayıcı

Bu örnekte, bir RegEx bölümü için tarih doğrulayıcı tanımlanmıştır.

```xml
<Validators id="date_validator_1"> <Validator type="DateSimple"> <Param name="Pattern">DDMMYYYY</Param> <!—supported patterns DDMMYYYY, MMDDYYYY, YYYYDDMM, YYYYMMDD, DDMMYYYY, DDMMYY, MMDDYY, YYDDMM, YYMMDD --> </Validator> </Validators>
<Regex id="date_regex_1" validators="date_validator_1">\d{8}</Regex>
```

## <a name="changes-for-exchange-online"></a>Exchange Online değişiklikleri

Daha önce, DLP için özel hassas bilgi türlerinizi içeri aktarmak için PowerShell Exchange Online kullanmış olabilirsiniz. Artık özel hassas bilgi türleriniz hem <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange yönetim merkezinde</a> hem de Uyumluluk merkezinde kullanılabilir. Bu geliştirmenin bir parçası olarak, özel hassas bilgi türlerinizi içeri aktarmak için Güvenlik & Uyumluluğu PowerShell'i kullanmalısınız; bunları artık Exchange Online PowerShell'den içeri aktaramazsınız. Özel hassas bilgi türleriniz daha önce olduğu gibi çalışmaya devam eder; ancak Uyumluluk merkezindeki özel hassas bilgi türlerinde yapılan değişikliklerin Exchange yönetim merkezinde görünmesi bir saat kadar sürebilir.

Uyumluluk merkezinde, bir kural paketini karşıya yüklemek için **[New-DlpSensitiveInformationTypeRulePackage](/powershell/module/exchange/new-dlpsensitiveinformationtyperulepackage)** cmdlet'ini kullandığınızı unutmayın. (Daha önce Exchange yönetim merkezinde **ClassificationRuleCollection** cmdlet'ini kullandınız.)

## <a name="upload-your-rule-package"></a>Kural paketinizi Upload

Kural paketinizi karşıya yüklemek için aşağıdaki adımları uygulayın:

1. Unicode kodlamalı .xml dosyası olarak kaydedin.

2. [Güvenlik & Uyumluluğu PowerShell'e Bağlan](/powershell/exchange/exchange-online-powershell)

3. Aşağıdaki sözdizimini kullanın:

   ```powershell
   New-DlpSensitiveInformationTypeRulePackage -FileData ([System.IO.File]::ReadAllBytes('PathToUnicodeXMLFile'))
   ```

   Bu örnek, C:\Belgelerim konumundan MyNewRulePack.xml adlı Unicode XML dosyasını karşıya yükler.

   ```powershell
   New-DlpSensitiveInformationTypeRulePackage -FileData ([System.IO.File]::ReadAllBytes('C:\My Documents\MyNewRulePack.xml'))
   ```

   Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [New-DlpSensitiveInformationTypeRulePackage](/powershell/module/exchange/new-dlpsensitiveinformationtyperulepackage).

   > [!NOTE]
   > Desteklenen en fazla kural paketi sayısı 10'dur, ancak her paket birden çok hassas bilgi türünün tanımını içerebilir.

4. Yeni bir hassas bilgi türünü başarıyla oluşturduğunuzu doğrulamak için aşağıdaki adımlardan herhangi birini yapın:

   - Yeni kural paketinin listelendiğini doğrulamak için [Get-DlpSensitiveInformationTypeRulePackage](/powershell/module/exchange/get-dlpsensitiveinformationtyperulepackage) cmdlet'ini çalıştırın:

     ```powershell
     Get-DlpSensitiveInformationTypeRulePackage
     ```

   - Hassas bilgi türünün listelendiğini doğrulamak için [Get-DlpSensitiveInformationType](/powershell/module/exchange/get-dlpsensitiveinformationtype) cmdlet'ini çalıştırın:

     ```powershell
     Get-DlpSensitiveInformationType
     ```

     Özel hassas bilgi türleri için Publisher özellik değeri Microsoft Corporation dışında bir değer olacaktır.

   - değerini \<Name\> hassas bilgi türünün Ad değeriyle değiştirin (örnek: Çalışan Kimliği) ve [Get-DlpSensitiveInformationType](/powershell/module/exchange/get-dlpsensitiveinformationtype) cmdlet'ini çalıştırın:

     ```powershell
     Get-DlpSensitiveInformationType -Identity "<Name>"
     ```

## <a name="potential-validation-issues-to-be-aware-of"></a>Dikkat edilmesi gereken olası doğrulama sorunları

Kural paketi XML dosyanızı karşıya yüklediğinizde sistem XML'yi doğrular ve bilinen hatalı desenleri ve belirgin performans sorunlarını denetler. Doğrulamanın denetlediği bilinen bazı sorunlar şunlardır: normal ifade:

- Normal ifadedeki lookbehind onayları yalnızca sabit uzunlukta olmalıdır. Değişken uzunluğu onaylamaları hatalara neden olur.

  Örneğin, `"(?<=^|\s|_)"` doğrulamayı geçmeyecek. İlk desen (`^`) sıfır uzunluktayken, sonraki iki desen (`\s` ve `_`) bir uzunluğa sahiptir. Bu normal ifadeyi yazmanın alternatif bir yoludur `"(?:^|(?<=\s|_))"`.

- Boş eşleşme olarak kabul edildiğinden her şeyle eşleşen alternatör `|`ile başlayamaz veya bitemez.

  Örneğin, `|a` veya `b|` doğrulamayı geçmeyecek.

- İşlevsel amacı olmayan ve yalnızca performansı bozan bir `.{0,m}` desenle başlayamaz veya sonlandırılamaz.

  Örneğin, `.{0,50}ASDF` veya `ASDF.{0,50}` doğrulamayı geçmeyecek.

- Gruplara veya `.{1,m}` gruplara sahip `.{0,m}` `.\*` olamaz ve gruplarda veya `.+` olamaz.

  Örneğin, `(.{0,50000})` doğrulamayı geçmeyecek.

- Gruplarda veya `{1,m}` yineleyicilerle `{0,m}` karakter olamaz.

  Örneğin, `(a\*)` doğrulamayı geçmeyecek.

- ile başlayamaz veya bitemez `.{1,m}`; bunun yerine kullanın `.`.

  Örneğin, `.{1,m}asdf` doğrulamayı geçmeyecek. Bunun yerine kullanın `.asdf`.

- Bir grupta ilişkisiz bir yineleyici (veya `+`gibi`*`) olamaz.

  Örneğin ve `(xx)\*` `(xx)+` doğrulamayı geçmeyecek.

- Anahtar sözcüklerin Uzunluğu en fazla 50 karakterdir.  Bir Grup içinde bunu aşan bir anahtar kelimeniz varsa, önerilen çözüm Terim Grubunu [Anahtar Sözcük Sözlüğü](./create-a-keyword-dictionary.md) olarak oluşturmak ve dosyadaki Eşleşme veya idMatch Için Varlık'ın bir parçası olarak XML yapısı içinde Anahtar Sözcük Sözlüğü GUID'sine başvurmaktır.

- Her Özel Hassas Bilgi Türü toplamda en fazla 2048 anahtar sözcük içerebilir.

- Tek bir kiracıdaki Anahtar Sözcük Sözlüklerinin boyutu üst sınırı, AD Şema sınırlarına uymak için 480 KB sıkıştırılmıştır. Özel hassas bilgi türleri oluştururken gerektiği kadar aynı sözlüğe başvurun. Hassas bilgi türünde özel anahtar sözcük listeleri oluşturmaya başlayın ve anahtar sözcük listesinde 2048'den fazla anahtar sözcük varsa veya anahtar sözcüğün uzunluğu 50 karakterden büyükse anahtar sözcük sözlüklerini kullanın.

- Kiracıda en fazla 50 anahtar sözcük sözlüğü tabanlı hassas bilgi türüne izin verilir.

- Her Entity öğesinin önerilen birConfidence özniteliği içerdiğini doğrulayın.

- PowerShell Cmdlet'ini kullanırken, Seri Durumdan Çıkarılmış Verilerin maksimum dönüş boyutu yaklaşık 1 megabayttır.   Bu, kural paketi XML dosyanızın boyutunu etkiler. İşlem sırasında hata olmadan tutarlı sonuçlar elde etmek için önerilen sınır olarak karşıya yüklenen dosyayı 770 kilobayt üst sınırla sınırlı tutun.

- XML yapısı boşluk, sekme veya satır başı/satır besleme girdileri gibi biçimlendirme karakterleri gerektirmez.  Karşıya yüklemelerde yer için iyileştirme yaparken bunu not edin. Microsoft Visual Code gibi araçlar, XML dosyasını sıkıştırmak için birleştirme satırı özellikleri sağlar.

Özel bir hassas bilgi türü performansı etkileyebilecek bir sorun içeriyorsa, karşıya yüklenmez ve şu hata iletilerinden birini görebilirsiniz:

- `Generic quantifiers which match more content than expected (e.g., '+', '*')`

- `Lookaround assertions`

- `Complex grouping in conjunction with general quantifiers`

## <a name="recrawl-your-content-to-identify-the-sensitive-information"></a>Hassas bilgileri tanımlamak için içeriğinizi yeniden gezinin

Microsoft 365, site içeriğindeki hassas bilgileri tanımlamak ve sınıflandırmak için arama gezginini kullanır. SharePoint Online ve OneDrive İş sitelerindeki içerik her güncelleştirildiğinde otomatik olarak yeniden gezilir. Ancak tüm mevcut içerikteki yeni özel hassas bilgi türünüzü tanımlamak için bu içeriğin yeniden bulunması gerekir.

Microsoft 365'da, bir kuruluşun tamamını el ile yeniden tarama isteğinde bulunamazsınız, ancak site koleksiyonu, listesi veya kitaplığı için el ile yeniden gezinme isteğinde bulunabilirsiniz. Daha fazla bilgi için bkz. [Sitenin, kitaplığın veya listenin el ile gezinmesini ve yeniden dizine alınmasını isteme](/sharepoint/crawl-site-content).

## <a name="reference-rule-package-xml-schema-definition"></a>Başvuru: Kural paketi XML şema tanımı

Bu işaretlemeyi kopyalayabilir, XSD dosyası olarak kaydedebilir ve kural paketi XML dosyanızı doğrulamak için kullanabilirsiniz.

```xml
<?xml version="1.0" encoding="utf-8"?>
<xs:schema xmlns:mce="http://schemas.microsoft.com/office/2011/mce"
           targetNamespace="http://schemas.microsoft.com/office/2011/mce"
           xmlns:xs="https://www.w3.org/2001/XMLSchema"
           elementFormDefault="qualified"
           attributeFormDefault="unqualified"
           id="RulePackageSchema">
  <!-- Use include if this schema has the same target namespace as the schema being referenced, otherwise use import -->
  <xs:element name="RulePackage" type="mce:RulePackageType"/>
  <xs:simpleType name="LangType">
    <xs:union memberTypes="xs:language">
      <xs:simpleType>
        <xs:restriction base="xs:string">
          <xs:enumeration value=""/>
        </xs:restriction>
      </xs:simpleType>
    </xs:union>
  </xs:simpleType>
  <xs:simpleType name="GuidType" final="#all">
    <xs:restriction base="xs:token">
      <xs:pattern value="[0-9a-fA-F]{8}\-([0-9a-fA-F]{4}\-){3}[0-9a-fA-F]{12}"/>
    </xs:restriction>
  </xs:simpleType>
  <xs:complexType name="RulePackageType">
    <xs:sequence>
      <xs:element name="RulePack" type="mce:RulePackType"/>
      <xs:element name="Rules" type="mce:RulesType">
        <xs:key name="UniqueRuleId">
          <xs:selector xpath="mce:Entity|mce:Affinity|mce:Version/mce:Entity|mce:Version/mce:Affinity"/>
          <xs:field xpath="@id"/>
        </xs:key>
        <xs:key name="UniqueProcessorId">
          <xs:selector xpath="mce:Regex|mce:Keyword|mce:Fingerprint"></xs:selector>
          <xs:field xpath="@id"/>
        </xs:key>
        <xs:key name="UniqueResourceIdRef">
          <xs:selector xpath="mce:LocalizedStrings/mce:Resource"/>
          <xs:field xpath="@idRef"/>
        </xs:key>
        <xs:keyref name="ReferencedRuleMustExist" refer="mce:UniqueRuleId">
          <xs:selector xpath="mce:LocalizedStrings/mce:Resource"/>
          <xs:field xpath="@idRef"/>
        </xs:keyref>
        <xs:keyref name="RuleMustHaveResource" refer="mce:UniqueResourceIdRef">
          <xs:selector xpath="mce:Entity|mce:Affinity|mce:Version/mce:Entity|mce:Version/mce:Affinity"/>
          <xs:field xpath="@id"/>
        </xs:keyref>
      </xs:element>
    </xs:sequence>
  </xs:complexType>
  <xs:complexType name="RulePackType">
    <xs:sequence>
      <xs:element name="Version" type="mce:VersionType"/>
      <xs:element name="Publisher" type="mce:PublisherType"/>
      <xs:element name="Details" type="mce:DetailsType">
        <xs:key name="UniqueLangCodeInLocalizedDetails">
          <xs:selector xpath="mce:LocalizedDetails"/>
          <xs:field xpath="@langcode"/>
        </xs:key>
        <xs:keyref name="DefaultLangCodeMustExist" refer="mce:UniqueLangCodeInLocalizedDetails">
          <xs:selector xpath="."/>
          <xs:field xpath="@defaultLangCode"/>
        </xs:keyref>
      </xs:element>
      <xs:element name="Encryption" type="mce:EncryptionType" minOccurs="0" maxOccurs="1"/>
    </xs:sequence>
    <xs:attribute name="id" type="mce:GuidType" use="required"/>
  </xs:complexType>
  <xs:complexType name="VersionType">
    <xs:attribute name="major" type="xs:unsignedShort" use="required"/>
    <xs:attribute name="minor" type="xs:unsignedShort" use="required"/>
    <xs:attribute name="build" type="xs:unsignedShort" use="required"/>
    <xs:attribute name="revision" type="xs:unsignedShort" use="required"/>
  </xs:complexType>
  <xs:complexType name="PublisherType">
    <xs:attribute name="id" type="mce:GuidType" use="required"/>
  </xs:complexType>
  <xs:complexType name="LocalizedDetailsType">
    <xs:sequence>
      <xs:element name="PublisherName" type="mce:NameType"/>
      <xs:element name="Name" type="mce:RulePackNameType"/>
      <xs:element name="Description" type="mce:OptionalNameType"/>
    </xs:sequence>
    <xs:attribute name="langcode" type="mce:LangType" use="required"/>
  </xs:complexType>
  <xs:complexType name="DetailsType">
    <xs:sequence>
      <xs:element name="LocalizedDetails" type="mce:LocalizedDetailsType" maxOccurs="unbounded"/>
    </xs:sequence>
    <xs:attribute name="defaultLangCode" type="mce:LangType" use="required"/>
  </xs:complexType>
  <xs:complexType name="EncryptionType">
    <xs:sequence>
      <xs:element name="Key" type="xs:normalizedString"/>
      <xs:element name="IV" type="xs:normalizedString"/>
    </xs:sequence>
  </xs:complexType>
  <xs:simpleType name="RulePackNameType">
    <xs:restriction base="xs:token">
      <xs:minLength value="1"/>
      <xs:maxLength value="64"/>
    </xs:restriction>
  </xs:simpleType>
  <xs:simpleType name="NameType">
    <xs:restriction base="xs:normalizedString">
      <xs:minLength value="1"/>
      <xs:maxLength value="256"/>
    </xs:restriction>
  </xs:simpleType>
  <xs:simpleType name="OptionalNameType">
    <xs:restriction base="xs:normalizedString">
      <xs:minLength value="0"/>
      <xs:maxLength value="256"/>
    </xs:restriction>
  </xs:simpleType>
  <xs:simpleType name="RestrictedTermType">
    <xs:restriction base="xs:string">
      <xs:minLength value="1"/>
      <xs:maxLength value="100"/>
    </xs:restriction>
  </xs:simpleType>
  <xs:complexType name="RulesType">
    <xs:sequence>
      <xs:choice maxOccurs="unbounded">
        <xs:element name="Entity" type="mce:EntityType"/>
        <xs:element name="Affinity" type="mce:AffinityType"/>
        <xs:element name="Version" type="mce:VersionedRuleType"/>
      </xs:choice>
      <xs:choice minOccurs="0" maxOccurs="unbounded">
        <xs:element name="Regex" type="mce:RegexType"/>
        <xs:element name="Keyword" type="mce:KeywordType"/>
        <xs:element name="Fingerprint" type="mce:FingerprintType"/>
        <xs:element name="ExtendedKeyword" type="mce:ExtendedKeywordType"/>
      </xs:choice>
      <xs:element name="LocalizedStrings" type="mce:LocalizedStringsType"/>
    </xs:sequence>
  </xs:complexType>
  <xs:complexType name="EntityType">
    <xs:sequence>
      <xs:element name="Pattern" type="mce:PatternType" maxOccurs="unbounded"/>
      <xs:element name="Version" type="mce:VersionedPatternType" minOccurs="0" maxOccurs="unbounded" />
    </xs:sequence>
    <xs:attribute name="id" type="mce:GuidType" use="required"/>
    <xs:attribute name="patternsProximity" type="mce:ProximityType" use="required"/>
    <xs:attribute name="recommendedConfidence" type="mce:ProbabilityType"/>
    <xs:attribute name="workload" type="mce:WorkloadType"/>
  </xs:complexType>
  <xs:complexType name="PatternType">
    <xs:sequence>
      <xs:element name="IdMatch" type="mce:IdMatchType"/>
      <xs:choice minOccurs="0" maxOccurs="unbounded">
        <xs:element name="Match" type="mce:MatchType"/>
        <xs:element name="Any" type="mce:AnyType"/>
      </xs:choice>
    </xs:sequence>
    <xs:attribute name="confidenceLevel" type="mce:ProbabilityType" use="required"/>
  </xs:complexType>
  <xs:complexType name="AffinityType">
    <xs:sequence>
      <xs:element name="Evidence" type="mce:EvidenceType" maxOccurs="unbounded"/>
      <xs:element name="Version" type="mce:VersionedEvidenceType" minOccurs="0" maxOccurs="unbounded" />
    </xs:sequence>
    <xs:attribute name="id" type="mce:GuidType" use="required"/>
    <xs:attribute name="evidencesProximity" type="mce:ProximityType" use="required"/>
    <xs:attribute name="thresholdConfidenceLevel" type="mce:ProbabilityType" use="required"/>
    <xs:attribute name="workload" type="mce:WorkloadType"/>
  </xs:complexType>
  <xs:complexType name="EvidenceType">
    <xs:sequence>
      <xs:choice maxOccurs="unbounded">
        <xs:element name="Match" type="mce:MatchType"/>
        <xs:element name="Any" type="mce:AnyType"/>
      </xs:choice>
    </xs:sequence>
    <xs:attribute name="confidenceLevel" type="mce:ProbabilityType" use="required"/>
  </xs:complexType>
  <xs:complexType name="IdMatchType">
    <xs:attribute name="idRef" type="xs:string" use="required"/>
  </xs:complexType>
  <xs:complexType name="MatchType">
    <xs:attribute name="idRef" type="xs:string" use="required"/>
    <xs:attribute name="minCount" type="xs:positiveInteger" use="optional"/>
    <xs:attribute name="uniqueResults" type="xs:boolean" use="optional"/>
  </xs:complexType>
  <xs:complexType name="AnyType">
    <xs:sequence>
      <xs:choice maxOccurs="unbounded">
        <xs:element name="Match" type="mce:MatchType"/>
        <xs:element name="Any" type="mce:AnyType"/>
      </xs:choice>
    </xs:sequence>
    <xs:attribute name="minMatches" type="xs:nonNegativeInteger" default="1"/>
    <xs:attribute name="maxMatches" type="xs:nonNegativeInteger" use="optional"/>
  </xs:complexType>
  <xs:simpleType name="ProximityType">
    <xs:union>
      <xs:simpleType>
        <xs:restriction base='xs:string'>
          <xs:enumeration value="unlimited"/>
        </xs:restriction>
      </xs:simpleType>
      <xs:simpleType>
        <xs:restriction base="xs:positiveInteger">
          <xs:minInclusive value="1"/>
        </xs:restriction>
      </xs:simpleType>
    </xs:union>
  </xs:simpleType>
  <xs:simpleType name="ProbabilityType">
    <xs:restriction base="xs:integer">
      <xs:minInclusive value="1"/>
      <xs:maxInclusive value="100"/>
    </xs:restriction>
  </xs:simpleType>
  <xs:simpleType name="WorkloadType">
    <xs:restriction base="xs:string">
      <xs:enumeration value="Exchange"/>
      <xs:enumeration value="Outlook"/>
    </xs:restriction>
  </xs:simpleType>
  <xs:simpleType name="EngineVersionType">
    <xs:restriction base="xs:token">
      <xs:pattern value="^\d{2}\.01?\.\d{3,4}\.\d{1,3}$"/>
    </xs:restriction>
  </xs:simpleType>
  <xs:complexType name="VersionedRuleType">
    <xs:choice maxOccurs="unbounded">
      <xs:element name="Entity" type="mce:EntityType"/>
      <xs:element name="Affinity" type="mce:AffinityType"/>
    </xs:choice>
    <xs:attribute name="minEngineVersion" type="mce:EngineVersionType" use="required" />
  </xs:complexType>
  <xs:complexType name="VersionedPatternType">
    <xs:sequence>
      <xs:element name="Pattern" type="mce:PatternType" maxOccurs="unbounded"/>
    </xs:sequence>
    <xs:attribute name="minEngineVersion" type="mce:EngineVersionType" use="required" />
  </xs:complexType>
  <xs:complexType name="VersionedEvidenceType">
    <xs:sequence>
      <xs:element name="Evidence" type="mce:EvidenceType" maxOccurs="unbounded"/>
    </xs:sequence>
    <xs:attribute name="minEngineVersion" type="mce:EngineVersionType" use="required" />
  </xs:complexType>
  <xs:simpleType name="FingerprintValueType">
    <xs:restriction base="xs:string">
      <xs:minLength value="2732"/>
      <xs:maxLength value="2732"/>
    </xs:restriction>
  </xs:simpleType>
  <xs:complexType name="FingerprintType">
    <xs:simpleContent>
      <xs:extension base="mce:FingerprintValueType">
        <xs:attribute name="id" type="xs:token" use="required"/>
        <xs:attribute name="threshold" type="mce:ProbabilityType" use="required"/>
        <xs:attribute name="shingleCount" type="xs:positiveInteger" use="required"/>
        <xs:attribute name="description" type="xs:string" use="optional"/>
      </xs:extension>
    </xs:simpleContent>
  </xs:complexType>
  <xs:complexType name="RegexType">
    <xs:simpleContent>
      <xs:extension base="xs:string">
        <xs:attribute name="id" type="xs:token" use="required"/>
      </xs:extension>
    </xs:simpleContent>
  </xs:complexType>
  <xs:complexType name="KeywordType">
    <xs:sequence>
      <xs:element name="Group" type="mce:GroupType" maxOccurs="unbounded"/>
    </xs:sequence>
    <xs:attribute name="id" type="xs:token" use="required"/>
  </xs:complexType>
  <xs:complexType name="GroupType">
    <xs:sequence>
      <xs:choice>
        <xs:element name="Term" type="mce:TermType" maxOccurs="unbounded"/>
      </xs:choice>
    </xs:sequence>
    <xs:attribute name="matchStyle" default="word">
      <xs:simpleType>
        <xs:restriction base="xs:NMTOKEN">
          <xs:enumeration value="word"/>
          <xs:enumeration value="string"/>
        </xs:restriction>
      </xs:simpleType>
    </xs:attribute>
  </xs:complexType>
  <xs:complexType name="TermType">
    <xs:simpleContent>
      <xs:extension base="mce:RestrictedTermType">
        <xs:attribute name="caseSensitive" type="xs:boolean" default="false"/>
      </xs:extension>
    </xs:simpleContent>
  </xs:complexType>
  <xs:complexType name="ExtendedKeywordType">
    <xs:simpleContent>
      <xs:extension base="xs:string">
        <xs:attribute name="id" type="xs:token" use="required"/>
      </xs:extension>
    </xs:simpleContent>
  </xs:complexType>
  <xs:complexType name="LocalizedStringsType">
    <xs:sequence>
      <xs:element name="Resource" type="mce:ResourceType" maxOccurs="unbounded">
      <xs:key name="UniqueLangCodeUsedInNamePerResource">
        <xs:selector xpath="mce:Name"/>
        <xs:field xpath="@langcode"/>
      </xs:key>
      <xs:key name="UniqueLangCodeUsedInDescriptionPerResource">
        <xs:selector xpath="mce:Description"/>
        <xs:field xpath="@langcode"/>
      </xs:key>
    </xs:element>
    </xs:sequence>
  </xs:complexType>
  <xs:complexType name="ResourceType">
    <xs:sequence>
      <xs:element name="Name" type="mce:ResourceNameType" maxOccurs="unbounded"/>
      <xs:element name="Description" type="mce:DescriptionType" minOccurs="0" maxOccurs="unbounded"/>
    </xs:sequence>
    <xs:attribute name="idRef" type="mce:GuidType" use="required"/>
  </xs:complexType>
  <xs:complexType name="ResourceNameType">
    <xs:simpleContent>
      <xs:extension base="xs:string">
        <xs:attribute name="default" type="xs:boolean" default="false"/>
        <xs:attribute name="langcode" type="mce:LangType" use="required"/>
      </xs:extension>
    </xs:simpleContent>
  </xs:complexType>
  <xs:complexType name="DescriptionType">
    <xs:simpleContent>
      <xs:extension base="xs:string">
        <xs:attribute name="default" type="xs:boolean" default="false"/>
        <xs:attribute name="langcode" type="mce:LangType" use="required"/>
      </xs:extension>
    </xs:simpleContent>
  </xs:complexType>
</xs:schema>
```

## <a name="more-information"></a>Daha fazla bilgi

- [Microsoft Purview Veri Kaybı Önleme hakkında bilgi edinin](dlp-learn-about-dlp.md)
- [Hassas bilgi türü varlık tanımları](sensitive-information-type-entity-definitions.md)
- [Hassas bilgi türü işlevleri](sit-functions.md)
