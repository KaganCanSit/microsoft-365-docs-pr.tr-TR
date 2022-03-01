---
title: PowerShell kullanarak özel duyarlı bilgi türü oluşturma
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
description: Uyumluluk Merkezi'nde ilkeler için özel hassas bilgi türünün nasıl oluşturul ve içeri aktarıla öğrenin.
ms.openlocfilehash: 89c215ca52b255a6e3aed72ff032cdd2475c0d87
ms.sourcegitcommit: bb493f12701f6d6ee7d5e64b541adb87470bc7bc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/18/2022
ms.locfileid: "63015523"
---
# <a name="create-a-custom-sensitive-information-type-using-powershell"></a>PowerShell kullanarak özel duyarlı bilgi türü oluşturma

Bu makalede, özel hassas bilgi türlerini tanımlayan bir XML *kural* paketi dosyasının nasıl [oluşturulacakları açıklanmıştır](sensitive-information-type-entity-definitions.md). Bu makalede, çalışan kimliğini tanımlayan özel ve hassas bir bilgi türü açıklanmıştır. Bu makaledeki örnek XML'yi kendi XML dosyanız için başlangıç noktası olarak kullanabilirsiniz.

Hassas bilgi türleri hakkında daha fazla bilgi için bkz. [Hassas bilgi türleri hakkında bilgi.](sensitive-information-type-learn-about.md)

İyi oluşturulduğunda bir XML dosyası oluşturduktan sonra, bu dosyayı PowerShell Microsoft 365 bilgisayarınıza yükleyebilirsiniz. Ardından, ilkelerde özel hassas bilgi türlerinizi kullanmaya hazır olursanız. Hassas bilgilerin hedeflenen şekilde algıla etkisini test edin.

> [!NOTE]
> PowerShell'in sağladığı ince  taneli denetime ihtiyacınız yoksa, Çalışma Alanı'nın içinde özel hassas bilgi türleri Microsoft 365 uyumluluk merkezi. Daha fazla bilgi için bkz [. Özel duyarlı bilgi türü oluşturma](create-a-custom-sensitive-information-type.md).

## <a name="important-disclaimer"></a>Önemli uyarı

Microsoft Desteği, içerikle eşleşen tanımlar oluşturmanıza yardımcı olmaz.

İçerikle eşleşen özel geliştirme, sınama ve hata ayıklama için kendi iç IT kaynaklarınızı veya Microsoft Consulting Services (MCS) gibi danışmanlık hizmetlerini kullanasınız. Microsoft Destek mühendisleri bu özellik için sınırlı destek sağsa da, bunlar özel içerik eşleştirme önerilerinin tamamen sizin ihtiyaçlarını karşılayacaklarını garanti etmezler.

MCS, test amacıyla normal ifadeler sağlar. Ayrıca, tek bir belirli içerik örneğinde olması beklendiği gibi çalışmayan mevcut RegEx düzeninde sorun giderme konusunda da yardımcı olabilir.

Bu [makalede dikkat dikkat etmek gereken olası doğrulama](#potential-validation-issues-to-be-aware-of) sorunları makalesine bakın.

Metni işlemede kullanılan Boost.RegEx (eski adıyla RegEx++) altyapısı hakkında daha fazla bilgi için bkz. [Boost.Regex 5.1.3](https://www.boost.org/doc/libs/1_68_0/libs/regex/doc/html/).

> [!NOTE]
> Özel hassas bilgi türdeki bir anahtar sözcüğün parçası olarak ve karakter (&) kullanıyorsanız, karakterin etrafında boşluklar olan ek bir terim eklemeniz gerekir. Örneğin, not `L & P` _kullanın_`L&P`.

## <a name="sample-xml-of-a-rule-package"></a>Kural paketinin örnek XML'si

İşte bu makalede oluştur işte size kural paketinin örnek XML'si. Öğeler ve öznitelikler aşağıdaki bölümlerde açıklanmaktadır.

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

Bir kural için XML şemasının temel yapısını anlamanız önemlidir. Yapıyı anlamanız, özel hassas bilgi türlerinizi doğru içeriği tanımlamanıza yardımcı olur.

Kural bir veya birden çok varlığı (hassas bilgi türleri olarak da bilinir) tanımlar. Her varlık bir veya daha fazla düzen tanımlar. Bir ilke içeriği değerlendirirken (örneğin, e-posta ve belgeler) bir düzenin bakarak bakııdır.

XML işaretlemesinde "kurallar", hassas bilgi türünü tanımlayan desenleri ifade ediyor. Bu makaledeki kurallara yapılan başvuruları, diğer Microsoft özelliklerinde yaygın olan "koşullar" veya "eylemler" ile ilişkilendirmeyin.

### <a name="simplest-scenario-entity-with-one-pattern"></a>En basit senaryo: Tek bir düzeni olan varlık

İşte basit bir senaryo: İlkenizin, kurumda kullanılan dokuz basamaklı çalışan kimliklerini içeren içeriği tanımlamalarını istiyorsunuz. Desen, kuralda dokuz basamaklı sayıları tanımlayan normal ifadeye başvurur. Dokuz basamaklı bir sayı içeren tüm içerik bu düzeni sağlar.

![Tek bir desenli varlık diyagramı.](../media/4cc82dcf-068f-43ff-99b2-bac3892e9819.png)

Ancak bu model **, daha uzun** sayılar veya çalışan kimlikleri olmayan dokuz basamaklı sayı türleri de dahil olmak üzere dokuz basamaklı bir sayı tanımlayabilir. Bu tür istenmeyen eşleşme, hatalı pozitif *sonuç olarak bilinir*.

### <a name="more-common-scenario-entity-with-multiple-patterns"></a>Daha yaygın senaryo: birden çok düzeni olan varlık

Yanlış pozitif sonuçlar için olası olduğundan, normalde bir varlık tanımlamak için birden fazla model kullanırsınız. Birden çok düzen hedef varlık için destek kanıtı sağlar. Örneğin, ek anahtar sözcükler, tarihler veya diğer metinler özgün varlığı tanımlamanıza yardımcı olabilir (örneğin, dokuz basamaklı çalışan numarası).

Örneğin, çalışan kimliği içeren içeriği tanımlama olasılığını artırmak için, arayacak başka desenler tanımlayabilirsiniz:

- İşe alma tarihini tanımlayan model.
- Hem işe alma tarihini hem de "çalışan kimliğini" anahtar sözcüğünü tanımlayan model.

![Birden çok desenli varlık diyagramı.](../media/c8dc2c9d-00c6-4ebc-889a-53b41a90024a.png)

Birden çok desen eşleşmesi için dikkate almak gereken önemli noktalar vardır:

- Daha fazla kanıt gerektiren desenlerin güven düzeyi daha yüksektir. Güven düzeyine bağlı olarak, aşağıdaki eylemleri gerçekleştirabilirsiniz:
  - Daha yüksek güvene sahip eşleşmelerde daha kısıtlayıcı eylemler (örneğin, içeriği engelle) kullanın.
  - Daha düşük güveni olan eşleşmelerde daha az kısıtlayıcı eylemler (bildirim gönderme gibi) kullanın.

- Destekleyen ve öğeler `IdMatch` `Match` için RegExes ve anahtar sözcükler başvurur; `Rule` bu öğenin değil, aslında öğenin çocuklarıdır `Pattern`. Bu destekleyen öğelere , tarafından başvurulsa `Pattern`da, 'ya dahildir `Rule`. Bu davranış, normal ifade veya anahtar sözcük listesi gibi destekleyen bir öğenin tek tanımına birden çok varlık ve desen tarafından başvurul olabilir anlamına gelir.

## <a name="what-entity-do-you-need-to-identify-entity-element-id-attribute"></a>Hangi varlığı tanımlamamız gerekiyor? [Varlık öğesi, Kimlik özniteliği]

Bir varlık, iyi tanımlanmış bir düzeni olan, kredi kartı numarası gibi hassas bir bilgi t türündedir. Her varlığın kimliği olarak benzersiz bir GUID'si vardır.

### <a name="name-the-entity-and-generate-its-guid"></a>Varlığa ad ve GUID'sini oluşturma

1. Xml düzenleyiciniz tarafından istediğiniz öğe ve `Rules` öğeleri `Entity` ekleyin.
2. Çalışan Kimliği gibi özel varlık adı içeren bir açıklama ekleyin. Daha sonra, yerelleştirilmiş dizeler bölümüne varlık adını eklersiniz ve bir ilke seniz bu ad yönetim merkezinde görünür.
3. Varlığınız için benzersiz bir GUID oluşturma. Örneğin, Windows PowerShell'de komutu çalıştırabilirsiniz`[guid]::NewGuid()`. Daha sonra, GUID'yi var olan yerelleştirilmiş dizeler bölümüne de eklersiniz.

![Kurallar ve Varlık öğelerini gösteren XML işaretlemesi.](../media/c46c0209-0947-44e0-ac3a-8fd5209a81aa.png)

## <a name="what-pattern-do-you-want-to-match-pattern-element-idmatch-element-regex-element"></a>Hangi düzenle eşleşmek istiyoruz? [Desen öğesi, IdMatch öğesi, Regex öğesi]

Bu düzen, hassas bilgi türünün ne istediğinin listesini içerir. Bu desen RegExes, anahtar sözcükler ve yerleşik işlevleri içerebilir. İşlevler, tarihleri veya adresleri bulmak için RegExes çalıştırmayı görevi yapar. Hassas bilgi türlerinin, benzersiz güven içeren birden çok düzeni olabilir.

Aşağıdaki diyagramda, tüm desenler aynı normal ifadeye başvurur. Bu RegEx, boşlukla çevrili dokuz `(\d{9})` basamaklı bir sayı aratır `(\s) ... (\s)`. Bu normal ifade öğeye başvurur `IdMatch` ve Çalışan Kimliği varlığa göz atan tüm desenler için yaygın gereksinimdir. `IdMatch` desenin eşleşmeye çalıştığı tanımlayıcıdır. Bir `Pattern` öğenin tam olarak bir öğesi `IdMatch` olması gerekir.

![Tek Regex öğesine başvuran birden çok Desen öğesini gösteren XML işaretlemesi.](../media/8f3f497b-3b8b-4bad-9c6a-d9abf0520854.png)

Memnun bir desen eşleşmesi, ilkenizin koşullarında kullanabileceğiniz bir sayım ve güven düzeyi döndürür. bir ilkeye hassas bilgi türünü algılamak için bir koşul eklerken, say ve güven düzeyini aşağıdaki diyagramda gösterildiği gibi düzenleyebilirsiniz. Güven düzeyi (eşleşme doğruluğu olarak da adlandırılan), bu makalenin devamsında açıklanmıştır.

![Örnek sayısı ve eşleşme doğruluğu seçenekleri.](../media/sit-confidence-level.png)

Normal ifadeler güçlü olduğu için hakkında bilginiz olması gereken sorunlar vardır. Örneğin, çok fazla içerik tanımlayan bir RegEx performansı etkileyebilir. Bu sorunlar hakkında daha fazla bilgi edinmek için, bu makalenin devam bölümündeki Dikkat olması [gereken](#potential-validation-issues-to-be-aware-of) doğrulama sorunları bölümüne bakın.

## <a name="do-you-want-to-require-additional-evidence-match-element-mincount-attribute"></a>Ek kanıta gerek mi var? [Öğeyle eşle, minCount özniteliği]

Buna ek olarak `IdMatch`, bir desen `Match` öğeyi anahtar sözcük, RegEx, tarih veya adres gibi ek destek kanıtı gerektirecek şekilde kullanabilir.

A `Pattern` birden çok öğe `Match` içerebilir:

- Doğrudan öğenin `Pattern` içinde.
- Öğe kullanılarak birleştirilmiş `Any` .

`Match` öğeler, bir örtülü AND işleciyle bir araya geldi. Başka bir deyişle, `Match` desenin eş eşleşmesi için tüm öğelerden memnun olması gerekir.

VE veya OR işleçlerini `Any` tanıtmak için bu öğeyi kullanabilirsiniz. Bu `Any` makalenin devamsında bu öğe açıklanmıştır.

İsteğe bağlı özniteliği `minCount` kullanarak her öğe için kaç eşleşme örneğinin bulun birden çok kez bulun olacağını belirtsiniz `Match` . Örneğin, bir düzenin yalnızca bir anahtar sözcük listesinden en az iki anahtar sözcük bulunduğu zaman memnun olduğunu belirtebilirsiniz.

![Öğeyi minOccurs özniteliğiyle eşle'yi gösteren XML işaretlemesi.](../media/607f6b5e-2c7d-43a5-a131-a649f122e15a.png)

### <a name="keywords-keyword-group-and-term-elements-matchstyle-and-casesensitive-attributes"></a>Anahtar Sözcükler [Anahtar Sözcük, Grup ve Terim öğeleri,Style ve büyük/harfe duyarlı öznitelikler]

Daha önce de açıklandığı gibi, hassas bilgilerin belirlenmesi çoğunlukla ek anahtar sözcüklerin kanıt olarak doğru olmasını gerektirir. Örneğin, dokuz basamaklı bir sayıyla eşleştirmeye ek olarak, Keyword öğesini kullanarak "kart", "rozet" veya "Kimlik" gibi sözcükler de arayabilirsiniz. Öğenin `Keyword` , birden `ID` çok kalıp veya varlıkta birden çok öğe `Match` tarafından başvurul kurumalan bir özniteliği vardır.

Anahtar sözcükler bir öğenin öğeleri listesi `Term` olarak dahil `Group` edilir. Öğenin `Group` , iki olası `matchStyle` değere sahip bir özniteliği vardır:

- **matchStyle="word"**: Sözcük eşleşmesi, boşluk veya diğer sınırlayıcılar içinde tam sözcükleri tanımlar. Asya dillerinde **sözcüklerin** veya sözcüklerin bir kısımlarını eşleşmeniz gerektir olmadıkça her zaman sözcük kullansanız iyi olur.

- **matchStyle="string"**: Dize eşleşmesi, hangi dizenin etrafını sarmış olursa olsun dizeleri tanımlar. Örneğin, "Kimlik" "teklif" ve "fikir" ile eşler. Yalnızca `string` Asya sözcüklerini eşleşmeniz veya anahtar sözcüğün diğer dizelere dahil olması gerekirken kullanın.

Son olarak, öğenin `caseSensitive` özniteliğini kullanarak içeriğin `Term` anahtar sözcükle tam olarak eşleşmesi gerektiğini (küçük harf ve büyük harfler de içinde olmak üzere) belirtebilirsiniz.

![Anahtar sözcüklere başvuran öğeleri eşle'yi gösteren XML işaretlemesi.](../media/e729ba27-dec6-46f4-9242-584c6c12fd85.png)

### <a name="regular-expressions-regex-element"></a>Normal ifadeler [Regex öğesi]

Bu örnekte, çalışan `ID` var olan varlık `IdMatch` zaten bu öğeyi kullanarak desene normal bir ifadeye başvurur: boşlukla çevrili dokuz basamaklı bir sayı. Buna ek olarak, `Match` `Regex` bir desen, US posta kodu biçiminde beş basamaklı veya dokuz basamaklı bir sayı gibi, üç basamaklı bir kanıt tanımlamak üzere ek bir öğeye başvuru yapmak için de bir öğe kullanabilir.

### <a name="additional-patterns-such-as-dates-or-addresses-built-in-functions"></a>Tarih veya adresler gibi ek desenler [yerleşik işlevler]

Hassas bilgi türleri, yanınıza alınan kanıtı tanımlamak için yerleşik işlevleri de kullanabilir. Örneğin, ABD tarihi, AB tarihi, son kullanma tarihi veya ABD adresi. Microsoft 365 işlevlerinizin karşıya yüklenmeyi desteklemez. Ancak, özel bir hassas bilgi türü  oluşturmak, varlık yerleşik işlevlere başvurabilirsiniz.

Örneğin, çalışan kimlik kartında bir işe giriş tarihi vardır, `Func_us_date` dolayısıyla bu özel varlık ABD'de yaygın olarak kullanılan biçimdeki bir tarihi tanımlamak için yerleşik işlevi kullanabilir.

Daha fazla bilgi için bkz [. Hassas bilgi türü işlevleri](sit-functions.md).

![Öğe başvurularını yerleşik işleve göre eşlemeyi gösteren XML işaretlemesi.](../media/dac6eae3-9c52-4537-b984-f9f127cc9c33.png)

## <a name="different-combinations-of-evidence-any-element-minmatches-and-maxmatches-attributes"></a>Farklı kanıt bileşimleri [Herhangi bir öğe, minMatches ve maxMatches öznitelikleri]

Bir öğede `Pattern` , tüm `IdMatch` öğeler `Match` ve öğeler örtülü AND işleciyle bir araya kullanılır. Başka bir deyişle, tüm eşleşmelerin desene memnun kalıptan memnun olması gerekir.

Öğeyi öğeleri grupla kullanarak daha esnek bir eşleştirme `Any` mantığı oluşturabilirsiniz `Match` . Örneğin, öğeyi alt öğelerinin tamamını `Any` , hiçbirini veya tam alt kümesini eşleşmek için kullanabilirsiniz `Match` .

Öğenin `Any` , desen `minMatches` eşleşmeden `maxMatches` önce `Match` kaç alt öğeden memnun olması gerektiğini tanımlamak için kullanabileceğiniz isteğe bağlı ve öznitelikleri vardır. Bu öznitelikler *, eşleşmeler* `Match` için bulunan kanıt örneklerinin sayısını değil, öğe sayısını tanımlar. Belirli bir eşleşme için, örneğin bir listeden iki anahtar sözcük için en az sayıda örnek tanımlamak için, `minCount` `Match` öğenin özniteliğini kullanın (yukarı bakın).

### <a name="match-at-least-one-child-match-element"></a>En az bir alt öğeyle eşle Ögeyi eşle

Yalnızca en az sayıda öğe `Match` gerektirmek için özniteliği kullanabilirsiniz `minMatches` . Aslında, bu öğeler `Match` örtülü OR işleciyle bir araya kullanılır. ABD `Any` biçimlendirilmiş bir tarih veya iki listeden bir anahtar sözcük bulunursa, bu öğeden memnun olur.

```xml
<Any minMatches="1" >
     <Match idRef="Func_us_date" />
     <Match idRef="Keyword_employee" />
     <Match idRef="Keyword_badge" />
</Any>
```

### <a name="match-an-exact-subset-of-any-children-match-elements"></a>Tüm çocukların tam alt kümesini eşleşme Ögeleri eşle

Tam sayıda öğe gerektirmek `Match` için, aynı `minMatches` değeri `maxMatches` ayarlayın ve ayarlayın. Bu `Any` öğe yalnızca tam olarak bir tarih veya anahtar sözcük bulunursa memnun olur. Başka eşleşme varsa, desen eşleşmez.

```xml
<Any minMatches="1" maxMatches="1" >
     <Match idRef="Func_us_date" />
     <Match idRef="Keyword_employee" />
     <Match idRef="Keyword_badge" />
</Any>
```

### <a name="match-none-of-children-match-elements"></a>Çocukların hiçbirini eşleşmez Öğelerle eşleşme

Bir düzenin karşılanacak olması için belirli kanıt olmamasını gerekli görmek için, hem minMatches hem de maxMatches'i 0 olarak ayarlayın. Bu, bir anahtar sözcük listeniz veya yanlış pozitif bir kanıtınız olması muhtemel başka bir kanıtınız varsa yararlı olabilir.

Örneğin çalışan kimliği var olan kişi, "kimlik kartı" anahtar sözcüğünü "kimlik kartı" olarak bakarak bakabilirsiniz. Ancak, bu içerikte yalnızca "kredi kartı" tümceciğiyle birlikte "kart" ifadesi görünüyorsa bu büyük bir ifadeyle "kimlik kartı" anlamına gelmmektedir. Dolayısıyla, bu düzeni karşılamanın dışında tutmak istediğiniz terimlerin listesine bir anahtar sözcük olarak "kredi kartı" ekleyebilirsiniz.

```xml
<Any minMatches="0" maxMatches="0" >
    <Match idRef="Keyword_false_positives_local" />
    <Match idRef="Keyword_false_positives_intl" />
</Any>
```

### <a name="match-a-number-of-unique-terms"></a>Bir dizi benzersiz terimle eşleşme

Bir dizi benzersiz terimle eşleşmek için, aşağıdaki örnekte gösterildiği gibi *uniqueResults* parametresini *true* olarak ayarlayın:

```xml
<Pattern confidenceLevel="75">
    <IdMatch idRef="Salary_Revision_terms" />
    <Match idRef=" Salary_Revision_ID " minCount="3" uniqueResults="true" />
</Pattern>
```

Bu örnekte, en az üç benzersiz eşleşme kullanılarak maaş düzeltmeleri için bir desen tanımlanmıştır.

## <a name="how-close-to-the-entity-must-the-other-evidence-be-patternsproximity-attribute"></a>Varlığa ne kadar yakın başka kanıt gerekir? [patternsProximity özniteliği]

Hassas bilgi türünüz çalışan kimliğini temsil eden bir model arıyor ve bu desenin bir parçası olarak aynı zamanda "Kimlik" gibi bir anahtar sözcük gibi geçerli kanıt arıyor. Bu kanıtın ne kadar yakın olduğuna göre, desenin gerçek bir çalışan kimliği olma olasılığı o kadar yüksek olur. Entity öğesinin gerekli desenleriniProximity özniteliğini kullanarak, desendeki diğer kanıtın varlığa ne kadar yakın olması gerektiğini belirlenebilirsiniz.

![DesenlerProximity özniteliğini gösteren XML işaretlemesi.](../media/e97eb7dc-b897-4e11-9325-91c742d9839b.png)

Varlıkta yer alan her desen için patternsProximity öznitelik değeri, idMatch konumuyla ilgili Desen için belirtilen diğer tüm Eşleşmeler için uzaklığı (Unicode karakter olarak) tanımlar. Yakınlık penceresi IdMatch konumu tarafından tutturucu olarak gösterilir ve pencere IdMatch'in sol ve sağına doğru genişler.

![Yakınlık penceresi diyagramı.](../media/b593dfd1-5eef-4d79-8726-a28923f7c31e.png)

Aşağıdaki örnekte, yakınlık penceresinin, çalışan kimliği özel varlığı için IdMatch öğesinin anahtar sözcük veya tarihle en az bir uyum eşleşmesi gerektirdiği desen eşleştirmesini nasıl etkileyeceğini gösterir. Yalnızca KIMLIK1 eşleşmesi, ID2 ve ID3 için yakınlık penceresinin içinde hiçbir kanıt veya yalnızca kısmi ya daroborlu kanıt bulunamay (eşleşmez).

![Kanıt ve yakınlık penceresi diyagramı.](../media/dc68e38e-dfa1-45b8-b204-89c8ba121f96.png)

E-posta için ileti gövdesinin ve her ekin ayrı öğeler olarak işlem gören bir ileti olduğunu unutmayın. Bu, yakınlık penceresinin bu öğelerin her biri sonundan daha öteye geç anlamına gelir. Her öğe (ek veya gövde) için, bu öğede hem idMatch hem de corroborative kanıt gerekir.

## <a name="what-are-the-right-confidence-levels-for-different-patterns-confidencelevel-attribute-recommendedconfidence-attribute"></a>Farklı desenler için doğru güven düzeyleri nedir? [confidenceLevel özniteliği, önerilenConfidence özniteliği]

Bir düzenin gerektirdiği kanıt ne kadar fazla kanıtsa, model eş olduğunda gerçek bir varlığa (örneğin çalışan kimliği) o kadar güvenebilirsiniz. Örneğin, yakın bir şekilde dokuz basamaklı kimlik numarası, işe giriş tarihi ve anahtar sözcük gerektiren bir düzende, yalnızca dokuz basamaklı kimlik numarası gerektiren bir düzende daha fazla güvene sahipsiniz.

Pattern öğesinin gerekli bir confidenceLevel özniteliği vardır. Güven düzeyi değerinin (1 ile 100 arasında bir tamsayı) var olan her model için benzersiz bir kimlik olarak düşünebilirsiniz; var olan düzenlerin, atadığınız farklı güven düzeylerine sahip olması gerekir. Tamsayının tam değeri önemli değildir; yalnızca uyumluluk takımınız için anlamlı olan sayıları seçin. Özel hassas bilgi türlerinizi karşıya yükledikten ve sonra bir ilke oluşturduklardan sonra, bu güven düzeylerine, kendi oluşturt istediğiniz kuralların koşullarında başvurebilirsiniz.

![confidenceLevel özniteliği için farklı değerlere sahip Desen öğelerini gösteren XML işaretlemesi.](../media/sit-xml-markedup-2.png)

Her Desen için confidenceLevel'e ek olarak, Varlık için önerilen birConfidence özniteliği vardır. Önerilen güven özniteliği, kuralın varsayılan güven düzeyi olarak kabul edilir. Bir ilkede kural 7 seniz, kuralın kullanıla bir güven düzeyi belirtmezseniz, bu kural varlığa önerilen güven düzeyine göre eş olur. Kural Paketi'deki her Varlık Kimliği için önerilenConfidence özniteliğinin zorunlu olduğunu unutmayın; eksikse, Hassas Bilgi Türü kullanan ilkeleri kaydedesiniz.

## <a name="do-you-want-to-support-other-languages-in-the-ui-of-the-compliance-center-localizedstrings-element"></a>Uyumluluk Merkezi'nin kullanıcı arabiriminde diğer dilleri desteklemek istiyor musunuz? [LocalizedStrings öğesi]

Uyumluluk ekipleriniz farklı yerel Microsoft 365 farklı dillerde ilkeler oluşturmak için Uyumluluk Merkezi'nde kullanıyorsa, özel hassas bilgi türle ilgili adın ve açıklamanın yerelleştirilmiş sürümlerini sebilirsiniz. Uyumluluk ekibinin destek Microsoft 365 bir dilde kullanıcı arabiriminde kullanıcı arabiriminde yerelleştirilmiş adı görebilir.

![Örnek sayısı ve doğruluk yapılandırmasını eşleşme.](../media/11d0b51e-7c3f-4cc6-96d8-b29bcdae1aeb.png)

Rules öğesi, özel varlık guid'nize başvuran bir Resource öğesi içeren bir LocalizedStrings öğesi içermeli. Böylece, her Kaynak öğesi, belirli bir dile yerelleştirilmiş dize sağlamak için her biri langcode özniteliğini kullanan bir veya birden çok Ad ve Açıklama öğesi içerir.

![LocalizedStrings öğesinin içeriğini gösteren XML işaretlemesi.](../media/a96fc34a-b93d-498f-8b92-285b16a7bbe6.png)

Yalnızca özel hassas bilgi türlerinizi Uyumluluk merkezi kullanıcı arabiriminde nasıl görüntülendiğinde yerelleştirilmiş dizeler kullanabileceğinizi unutmayın. Bir anahtar sözcük listesinin veya normal ifadenin farklı yerelleştirilmiş sürümlerini sağlamak için yerelleştirilmiş dizeler kullana zaman yoktur.

## <a name="other-rule-package-markup-rulepack-guid"></a>Diğer kural paketi işaretlemesi [RulePack GUID]

Son olarak, her RulePackage başlangıcı, doldurmanız gereken bazı genel bilgiler içerir. Aşağıdaki işaretlemeyi şablon olarak kullanabilir ve " ifadesini değiştirebilirsiniz. . ." yer tutucularını kullanabilirsiniz.

En önemlisi de, RulePack için bir GUID oluşturmanız gerekir. Üst yukarıda, varlık için bir GUID oluşturduz; bu, RulePack için ikinci bir GUID'dir. GUID oluşturmanın çeşitli yolları vardır, ancak [guid]::NewGuid( yazarak PowerShell'de bunu kolayca yapabilirsiniz.

Sürüm öğesi de önemlidir. Kural paketinizi ilk kez karşıya yüklerken, Microsoft 365 numarasını not alın. Daha sonra kural paketini güncelleştirdikten sonra yeni bir sürüm karşıya yüklersanız, sürüm numarasını güncelleştirin veya Microsoft 365 paketi dağıtmaz.

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

Tamamlandığında, RulePack öğeniz aşağıdakine benzer bir görünümde olur.

![RulePack öğesini gösteren XML işaretlemesi.](../media/fd0f31a7-c3ee-43cd-a71b-6a3813b21155.png)

## <a name="validators"></a>Doğrulayıcılar

Microsoft 365 kullanılan SITS'leri geçerlik olarak işlev işlemcileri olarak gösterir. İşte bu ifadelerin listesi.

### <a name="list-of-currently-available-validators"></a>Şu anda kullanılabilir olan geçerlilerin listesi

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

Bu size kendi RegEx'inizi tanımlama ve doğrulama olanağı verir. Doğrulayıcıları kullanmak için, kendi RegEx değerinizi `Validator` tanımlayın ve istediğiniz işlev işlemcisini eklemek için özelliği kullanın. Tanımlananda, bu RegEx'i sit'te kullanabilirsiniz.

Aşağıdaki örnekte, kredi kartı için normal bir ifade - Regex_credit_card_AdditionalDelimiters tanımlanır ve kredi kartı için checksum işlevi kullanılarak doğrulanır ve bu ifade geçerli Func_credit_card olarak doğrulanır.

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

Microsoft 365 iki genel doğrulama sağlar

### <a name="checksum-validator"></a>Checksum geçerlileyicisi

Bu örnekte, ÇalışanKimliği için RegEx'i doğrulamak için çalışan kimliği için bir denetim numarası doğrulayıcı tanımlanır.

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

Bu örnekte, bir kısmı tarih olan RegEx bölümü için tarih doğrulayıcı tanımlanmıştır.

```xml
<Validators id="date_validator_1"> <Validator type="DateSimple"> <Param name="Pattern">DDMMYYYY</Param> <!—supported patterns DDMMYYYY, MMDDYYYY, YYYYDDMM, YYYYMMDD, DDMMYYYY, DDMMYY, MMDDYY, YYDDMM, YYMMDD --> </Validator> </Validators>
<Regex id="date_regex_1" validators="date_validator_1">\d{8}</Regex>
```

## <a name="changes-for-exchange-online"></a>Daha fazla Exchange Online

Daha önce, DLP için özel Exchange Online bilgi türlerinizi içeri aktarmada PowerShell'i kullandınız. Artık özel hassas bilgi türleriniz yönetim merkezinde ve <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Uyumluluk Exchange kullanılabilir</a>. Bu geliştirmenin bir parçası olarak, Uyumluluk Merkezi PowerShell'i kullanarak özel hassas bilgi türlerinizi içeri aktarmanız gerekir; artık bunları PowerShell'in Exchange içeri aktaramazsınız. Özel hassas bilgi türleriniz daha önce olduğu gibi çalışmaya devam edecektir; Bununla birlikte, Uyumluluk Merkezi'nde özel hassas bilgi türlerinde yapılan değişikliklerin Yönetim Merkezi'nde Exchange zaman alabiliyor.

Uyumluluk merkezinde, kural paketini karşıya yüklemek için **[New-DlpSensitiveInformationTypeRulePackage](/powershell/module/exchange/new-dlpsensitiveinformationtyperulepackage)** cmdlet'ini kullanabileceğinizi unutmayın. (Daha önce, Exchange yönetim merkezinde **ClassificationRuleCollection'ın** cmdlet'ini kullanıiyn.

## <a name="upload-your-rule-package"></a>Upload paketinizi seçin

Kural paketinizi karşıya yüklemek için aşağıdaki adımları izleyin:

1. Unicode kodlamayla .xml bir dosya olarak kaydedin.

2. [Bağlan merkezi PowerShell'e](/powershell/exchange/exchange-online-powershell)

3. Aşağıdaki sözdizimini kullanın:

   ```powershell
   New-DlpSensitiveInformationTypeRulePackage -FileData ([System.IO.File]::ReadAllBytes('PathToUnicodeXMLFile'))
   ```

   Bu örnekte, C:\Belgelerim klasöründen MyNewRulePack.xml Unicode XML dosyası karşıya yükler.

   ```powershell
   New-DlpSensitiveInformationTypeRulePackage -FileData ([System.IO.File]::ReadAllBytes('C:\My Documents\MyNewRulePack.xml'))
   ```

   Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [New-DlpSensitiveInformationTypeRulePackage](/powershell/module/exchange/new-dlpsensitiveinformationtyperulepackage).

   > [!NOTE]
   > Desteklenen kural paketi sayısı üst sayısı 10'dır, ancak her paket birden çok hassas bilgi türü tanım içerebilir.

4. Yeni hassas bir bilgi türünü başarıyla oluşturduğunuzdan emin olmak için, aşağıdaki adımlardan herhangi birini yapın:

   - Yeni kural [paketinin listelediğini doğrulamak için Get-DlpSensitiveInformationTypeRulePackage](/powershell/module/exchange/get-dlpsensitiveinformationtyperulepackage) cmdlet'ini çalıştırın:

     ```powershell
     Get-DlpSensitiveInformationTypeRulePackage
     ```

   - Hassas bilgi [türünün listelenmiş olduğunu doğrulamak için Get-DlpSensitiveInformationType](/powershell/module/exchange/get-dlpsensitiveinformationtype) cmdlet'ini çalıştırın:

     ```powershell
     Get-DlpSensitiveInformationType
     ```

     Özel hassas bilgi türlerinde, Publisher değeri Microsoft Corporation'dan farklı bir değer olur.

   - Hassas \<Name\> bilgi türünün Ad değeriyle değiştirin (örneğin: Çalışan Kimliği) ve [Get-DlpSensitiveInformationType](/powershell/module/exchange/get-dlpsensitiveinformationtype) cmdlet'ini çalıştırın:

     ```powershell
     Get-DlpSensitiveInformationType -Identity "<Name>"
     ```

## <a name="potential-validation-issues-to-be-aware-of"></a>Dikkatlanması gereken olası doğrulama sorunları

Kural paketi XML dosyanızı karşıya yüklerken, sistem XML'yi doğrular ve bilinen kötü desenleri ve belirgin performans sorunlarını denetler. Doğrulamanın normal bir ifade olarak denetler olduğu bilinen bazı sorunlar:

- Normal ifadede yapılan bakıla onaylamalar yalnızca sabit uzunlukta olmalıdır. Değişken uzunluğu onaylamaları hatalara neden olur.

  Örneğin, `"(?<=^|\s|_)"` doğrulamayı geçmez. İlk desen (`^`) sıfır uzunlukken, sonraki iki desen (`\s` `_`ve ) biri uzunluğuna sahip olur. Bu normal ifadeyi yazmanın alternatif bir yolu da şu şekildedir `"(?:^|(?<=\s|_))"`: .

- Her şey boş bir eşleşme olarak değerlendiril olduğundan `|`her şey ile eşleşen alternator ile başamaz veya bitebilir.

  Örneğin, doğrulamayı `|a` `b|` geçecek şekilde değil.

- İşlevsel amacı olmayan ve yalnızca `.{0,m}` performansı bozan bir desenle başlayamaz veya bitebilir.

  Örneğin, doğrulamayı `.{0,50}ASDF` `ASDF.{0,50}` geçecek şekilde değil.

- Grupların `.{0,m}` içinde `.{1,m}` veya gruplarında bulunamaz ve grupların `.\*` içinde veya gruplarında `.+` bulunamaz.

  Örneğin, `(.{0,50000})` doğrulamayı geçmez.

- Gruplarda herhangi bir karakter `{0,m}` veya `{1,m}` tekrarlayıcı olamaz.

  Örneğin, `(a\*)` doğrulamayı geçmez.

- Bunun yerine ile başlayamaz veya `.{1,m}`bitamaz; bunun yerine , kullanın `.`.

  Örneğin, `.{1,m}asdf` doğrulamayı geçmez. Bunun yerine, kullanın `.asdf`.

- Grupta bağlı olmayan bir tekrarlayıcı (veya gibi `*` `+`) olamaz.

  Örneğin, doğrulama `(xx)\*` `(xx)+` başarılı olmaz.

- Anahtar sözcüklerin Uzunluk değeri en fazla 50 karakter olabilir.  Bir Grup içinde bunu aşan bir anahtar sözcüğüniz varsa, önerilen bir çözüm, Anahtar Sözcük Sözlüğü olarak bir Terim Grubu oluşturmak ve [](./create-a-keyword-dictionary.md) dosyada Eşleşme veya idMatch için Varlık'ın bir parçası olarak XML yapısında Anahtar Sözcük Sözlüğü'ne GUID başvurusu yapmaktır.

- Her Özel Duyarlı Bilgi Türü'ne en çok 2048 anahtar sözcük ekleyebilirsiniz.

- AD Şeması sınırlarına uymak için sıkıştırılmış tek bir kiracıda Anahtar Sözcük Sözlükleri boyutu üst sınırı 480 KB'dir. Özel hassas bilgi türleri oluştururken, aynı sözlüğe gereken sayıda başvuru. Hassas bilgi türünde özel anahtar sözcük listeleri oluşturarak çalışmaya devam edin ve bir anahtar sözcük listesinde 2048'den fazla anahtar sözcük varsa veya anahtar sözcük uzunluğu 50 karakteri aşıyorsa anahtar sözcük sözlüklerini kullanın.

- Bir kiracıda en fazla 50 anahtar sözcük sözlüğüne temel alınan hassas bilgi türlerine izin verilir.

- Her Entity elementin recommendedConfidence özniteliği içerdiğiden emin olmak.

- PowerShell Cmdlet'i kullanılırken, Deserialized Data 'ın yaklaşık 1 megabayttan büyük bir dönüş boyutu vardır.   Bu, kural paketi XML dosyanızı boyutunu etkiler. Karşıya yüklenen dosyanın, işlem sırasında hatasız tutarlı sonuçlar için önerilen bir sınır olarak 770 kilobayt üst sınırıyla sınırlı tutma.

- XML yapısı boşluk, sekme veya satır başı/satır besleme girdileri gibi biçimlendirme karakterleri gerektirmez.  Karşıya yüklemelerde alan iyileştirmeleri için bunu unutmayın. Microsoft Visual Code gibi araçlar XML dosyasını sıkıştırmak için birleşim çizgisi özellikleri sağlar.

Özel duyarlı bilgi türü performansı etkileyebilecek bir sorun içeriyorsa, yük yüklenmez ve şu hata iletilerinden birini alabilirsiniz:

- `Generic quantifiers which match more content than expected (e.g., '+', '*')`

- `Lookaround assertions`

- `Complex grouping in conjunction with general quantifiers`

## <a name="recrawl-your-content-to-identify-the-sensitive-information"></a>Hassas bilgileri tanımlamak için içeriğinizi yeniden çalışma

Microsoft 365, site içeriğinde hassas bilgileri tanımlamak ve sınıflandırmak için arama gezginini kullanır. SharePoint Online'daki OneDrive İş güncelleştirildiğinde siteler otomatik olarak yeniden aratılır. Ancak, var olan tüm içerikte yeni özel tür hassas bilginizi tanımlamak için, bu içerikte recrawled olması gerekir.

Microsoft 365'de, tüm bir kuruluşun el ile yeniden tedransını talep edebilirsiniz, ancak el ile site koleksiyonu, liste veya kitaplık için yeniden tedin isteğinde bulundurabilirsiniz. Daha fazla bilgi için bkz. Site, kitaplık veya liste için gezinme ve yeniden [ininde el ile istekte bulundurabilirsiniz](/sharepoint/crawl-site-content).

## <a name="reference-rule-package-xml-schema-definition"></a>Başvuru: Kural paketi XML şema tanımı

Bu işaretlemeyi kopyalayıp XSD dosyası olarak kaydedebilir ve kural paketi XML dosyanızı doğrulamak için kullanabilirsiniz.

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

- [Veri kaybını önleme hakkında bilgi](dlp-learn-about-dlp.md)
- [Hassas bilgi türü varlık tanımları](sensitive-information-type-entity-definitions.md)
- [Hassas bilgi türü işlevleri](sit-functions.md)
