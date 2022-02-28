---
title: Taksonomi için SKOS SharePoint başvurusu
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: admin
ms.topic: article
ms.prod: microsoft-365-enterprise
search.appverid: ''
ms.collection: enabler-strategic
ms.localizationpriority: high
description: Taksonomi için SKOS SharePoint başvurusu
ms.openlocfilehash: 95183b64d76a70f69d08cd5a3c9dcf76f4e83bce
ms.sourcegitcommit: dc26169e485c3a31e1af9a5f495be9db75c49760
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/04/2021
ms.locfileid: "62990009"
---
# <a name="skos-format-reference-for-sharepoint-taxonomy"></a>Taksonomi için SKOS SharePoint başvurusu

Bu makale, bir taksonomiyi temsil [etmek SharePoint](/dotnet/api/microsoft.sharepoint.taxonomy) kullanılan ve [SKOS'u](https://www.w3.org/TR/skos-primer/) temel alan RDF sözcük dağarcığı içerir. Bu RDF söz dizimlerinin seri hale getirmesi için RDF [TURTLE kullanın](https://www.w3.org/TR/turtle/).

Aşağıdaki tabloda, bu taksonomi sözcük dağarcığına SharePoint [SKOS](https://www.w3.org/TR/skos-primer/) [eşdeğerleri](/dotnet/api/microsoft.sharepoint.taxonomy) yer almaktadır. SharePoint, [taksonomi eşdeğeri olan SKOS](https://www.w3.org/TR/skos-primer/) SharePoint desteklemez.

|SharePoint taksonomiyi|SKOS eşdeğeri|
|:-----------------|:--------------|
|sharepoint-taksonomi:Terim|skos:Kavram|
|sharepoint-taksonomi:TermSet|skos:ConceptScheme|
|sharepoint-taksonomi:inTermSet|skos:inScheme|
|sharepoint-taksonomi:hasTopLevelTerm|skos:hasTopConcept|
|sharepoint-taksonomi:topLevelTermOf|skos:topConceptOf|
|sharepoint-taksonomi:defaultLabel|skos:prefLabel|
|sharepoint-taksonomi:termSetName|skos:prefLabel|
|sharepoint-taksonomi:propertyName|skos:prefLabel|
|sharepoint-taksonomi:otherLabel|skos:altLabel|
|sharepoint-taksonomi:açıklama|skos:definition|
|sharepoint-taksonomi:parent|skos:broader|
|sharepoint-taksonomi:çocuk|skos:narrower|

Aşağıdaki tablo OWL'den türetilen SharePoint sözcük dağarcığının [varlıklarını görüntüler](https://www.w3.org/TR/owl2-primer/).

|SharePoint terim dağarcığı|OWL'dan türetilen|
|:-----------------------------|:----------------------|
|sharepoint-taksonomi:isAvailableForTagging|owl:datatypeproperty|
|sharepoint-taksonomi:SharedCustomPropertyForTerm|owl:ObjectProperty|
|sharepoint-taksonomi:LocalCustomPropertyForTerm|owl:ObjectProperty|
|sharepoint-taksonomi:CustomPropertyForTermSet|owl:ObjectProperty|

## <a name="sharepoint-taxonomy-vocabulary"></a>SharePoint terim dağarcığı

Taksonomi resmi bir sınıflandırma sistemidir. Taksonomi, bir şeyi açıklayan sözcükleri, etiketleri ve terimleri gruplar ve sonra da grupları bir hiyerarşi halinde düzenlenmiştir.

**sharepoint-taksonomi:Terim**

Yönetilen bir meta veri hiyerarşisinde bir Terimi veya Anahtar Sözcüğü temsil eder.

Terim[,](/dotnet/api/microsoft.sharepoint.taxonomy.term) [TermStore'nın](/dotnet/api/microsoft.sharepoint.taxonomy.termstore) bölünmez SharePoint birimidir. Her [Terim](/dotnet/api/microsoft.sharepoint.taxonomy.term) bir [TermGroup'a ait](/dotnet/api/microsoft.sharepoint.taxonomy.termset) olan bir [Terim Kümesine aittir](/dotnet/api/microsoft.sharepoint.taxonomy.group).

Terim tanımlama söz [dizimi aşağıdaki](/dotnet/api/microsoft.sharepoint.taxonomy.term) gibidir:

```SKOS
ex:TermA    a    sharepoint-taxonomy:Term;
    sharepoint-taxonomy:inTermSet    ex:TermSetA;
    sharepoint-taxonomy:topLevelTermOf    ex:TermSetA;
    sharepoint-taxonomy:child    ex:TermA1;
    sharepoint-taxonomy:isAvailableForTagging    “true”^^xsd:Boolean;
    sharePoint-taxonomy:defaultLabel    “Term A”@en-us.
```

Bir [Terim](/dotnet/api/microsoft.sharepoint.taxonomy.term) Kümesi içinde her zaman yeni [bir Terim vardır](/dotnet/api/microsoft.sharepoint.taxonomy.termset). DefaultLabel, görsel [temsilde göründüğü](/dotnet/api/microsoft.sharepoint.taxonomy.term) şekilde Terimin adıdır. Terim tanımlamak için gerekli [alanlar şunlardır](/dotnet/api/microsoft.sharepoint.taxonomy.term) :

- sharepoint-taksonomi:defaultLabel
- sharepoint-taksonomi:inTermSet

Bir [Terim şunları](/dotnet/api/microsoft.sharepoint.taxonomy.term) olabilir:

- Hem Koşulların aynı Terim Kümesine [ait](/dotnet/api/microsoft.sharepoint.taxonomy.term) olması hem de başka bir [Terimle](/dotnet/api/microsoft.sharepoint.taxonomy.term) hiyerarşik [olarak ilişkili olması.](/dotnet/api/microsoft.sharepoint.taxonomy.termset)
- Birden çok alt Hüküm [var](/dotnet/api/microsoft.sharepoint.taxonomy.term), ancak tek bir üst [Terim var](/dotnet/api/microsoft.sharepoint.taxonomy.term).
- Bir Terim Kümesi [için](/dotnet/api/microsoft.sharepoint.taxonomy.term) topLevelTermOf ise, tanımlanmış üst Terim [yok.](/dotnet/api/microsoft.sharepoint.taxonomy.termset)
- TerimStore çalışma dili başına tek [bir defaultLabel](/dotnet/api/microsoft.sharepoint.taxonomy.termstore) sahibi olur.
- Üst Terim veya Terim [Kümesi için üst](/dotnet/api/microsoft.sharepoint.taxonomy.term) DüzeyTerm [yoksa, yoktur](/dotnet/api/microsoft.sharepoint.taxonomy.termset).
- Yalnızca aynı hiyerarşik düzeyde benzersiz bir defaultLabel var.

**sharepoint-taksonomi:TermSet**

"Terim Kümesi" olarak bilinen hiyerarşik veya düz bir Terim nesneleri kümesi temsil eder.

Adı da anlaşılacağı gibi, Terim Kümesi bir dizi [Terimdir](/dotnet/api/microsoft.sharepoint.taxonomy.term). Terim [Deposu'daki](/dotnet/api/microsoft.sharepoint.taxonomy.term) [bir Terim](/dotnet/api/microsoft.sharepoint.taxonomy.termstore) , bir Terim [Kümesine ait olması gerekir](/dotnet/api/microsoft.sharepoint.taxonomy.termset). Hiçbir [Terim](/dotnet/api/microsoft.sharepoint.taxonomy.term) bağımsız olarak var olamaz.

Terim Kümesi tanımlama söz [dizimi aşağıdaki](/dotnet/api/microsoft.sharepoint.taxonomy.termset) gibidir:

```SKOS
ex:TermSetA    a    sharepoint-taxonomy:TermSet;
    sharepoint-taxonomy:termSetName    “TermSet A";
    sharepoint-taxonomy:isAvailableForTagging    “true”^^xsd:Boolean;
    sharepoint-taxonomy:hasTopLevelTerm    Ex:Term A.
```

[Terim Kümeleri](/dotnet/api/microsoft.sharepoint.taxonomy.termset) , TermGroups içinde mantıksal olarak [birlikte gruplandırılmaktadır](/dotnet/api/microsoft.sharepoint.taxonomy.group). Terim Kümesi tanımlamak için gereken [alan](/dotnet/api/microsoft.sharepoint.taxonomy.termset) :

- sharepoint-taksonomi:termSetName

SağlananSetName [terimiNin TermGroup](/dotnet/api/microsoft.sharepoint.taxonomy.group) içinde benzersiz olması durumunda, SharePoint setName/s terimlerini benzersizliğini korumak için adın sonuna bir sayı ekler.

**sharepoint-taksonomi:hasTopLevelTerm**

SharePoint bu özelliği, [Terim](/dotnet/api/microsoft.sharepoint.taxonomy.termset) Kümesi'nin en üst terimlerini [](/dotnet/api/microsoft.sharepoint.taxonomy.term) eşlemek için kullanır. Bu, Terim Kümesi'nin Terim hiyerarşisinin giriş [](/dotnet/api/microsoft.sharepoint.taxonomy.term) [noktasıdır](/dotnet/api/microsoft.sharepoint.taxonomy.termset). Bu, sharepoint-taksonomi:topLevelTermOf ile ters bir ilişkidir.

Bunu tanımlayan söz dizimi:

```SKOS
ex:TermSetA    sharepoint-taxonomy:hasTopLevelTerm    ex:TermA.
```

> [!NOTE]
> Bir üst Terimin en [üst düzey Terimini](/dotnet/api/microsoft.sharepoint.taxonomy.term) [tanımamazsiniz](/dotnet/api/microsoft.sharepoint.taxonomy.term).

**sharepoint-taksonomi:topLevelTermOf**

Sharepoint-taksonomi:topLevelTermOf, sharepoint-taksonominin tersidir:hasTopLevelTerm

Bunu tanımlayan söz dizimi:

```SKOS
ex:TermA    sharepoint-taxonomy:topLevelTermOf    ex:TermSetA.
```

**sharepoint-taksonomi:inTermSet**

Bir Terimi Terim Kümesine [eşlemek](/dotnet/api/microsoft.sharepoint.taxonomy.term) için [bunu kullanın](/dotnet/api/microsoft.sharepoint.taxonomy.termset). Bir [Terim](/dotnet/api/microsoft.sharepoint.taxonomy.term) yalnızca tek bir Terim [Kümesinde yer alan bir terim olabilir](/dotnet/api/microsoft.sharepoint.taxonomy.termset). SharePoint bir terim tanımlarken bu [özelliğin gerekli olduğunu unutmayın](https://github.com/MicrosoftDocs/microsoft-365-docs-pr/blob/3a3cd54dd076b18bdff1d43b3e342897f8704c23/microsoft-365/contentunderstanding/skos-format-reference.md#term).

## <a name="required-labels"></a>Gerekli etiketler

Yönetilen meta verileri kullanmaya başlamadan önce, kuruluş dikkatli bir planlama yapmak istiyor olabilir. Planlamanız gereken planlama miktarı taksonominizin ne kadar resmi olduğunu bağlıdır. Ayrıca, meta verilere ne kadar denetim dayatma istediğinize de bağlıdır. Hiyerarşinin her düzeyinde, Terim veya Terim Kümesi için gerekli etiketleri yapılandırmaniz gerekir.

Bir Terim, varsayılan dilde bir veya daha fazla etikete ve varsayılan olmayan dilde sıfır veya daha fazla etikete sahip olabilir. Terimin bir dilde etiketleri varsa, etiketlerden biri varsayılan etiket olmalı.

**sharepoint-taksonomi:defaultLabel**

Bir Terim için gerekli parametre olan [bir Terim için](/dotnet/api/microsoft.sharepoint.taxonomy.term) bu varsayılan sözcük etiketini [kullanın](/dotnet/api/microsoft.sharepoint.taxonomy.term). Terimi görsel olarak temsil etmek için [kullanın](/dotnet/api/microsoft.sharepoint.taxonomy.term).

DefaultLabel tanımlamak için kullanılan söz dizimi:

```SKOS
ex:TermA    sharepoint-taxonomy:defaultLabel    “Term A”@en-us.
```

defaultLabel iki parça içerir: dize ve dil etiketi. Dil, Terim Deposu çalışma [dillerinden](/dotnet/api/microsoft.sharepoint.taxonomy.termstore) biri olmalı. defaultLabel, aynı Terim [Kümesi'nde](/dotnet/api/microsoft.sharepoint.taxonomy.term) yer [alan tüm](/dotnet/api/microsoft.sharepoint.taxonomy.termset) Terimler için aynı hiyerarşik düzeyde benzersiz olmalıdır.

**sharepoint-taksonomi:termSetName**

Geçerli Terim Kümesi nesnesinin adını alır ve ayarlar.

Terim Deposu çalışma dilindeki Bu, [Terim](/dotnet/api/microsoft.sharepoint.taxonomy.termset) Deposu'un [lexical](/dotnet/api/microsoft.sharepoint.taxonomy.termstore) etiketi. Bu, bir TermSet için gerekli [bir parametredir](/dotnet/api/microsoft.sharepoint.taxonomy.termset). Terim Kümesi'nde görsel olarak [temsil etmek için kullanın](/dotnet/api/microsoft.sharepoint.taxonomy.termset).

SetName terimini tanımlamak için kullanılan söz dizimi:

```SKOS
ex:TermA    sharepoint-taxonomy:TermSetName    “Term Set A”@en-us.
```

**sharepoint-taksonomi:propertyName**

Geçerli Terim Kümesi nesnesinin özellik adını alır ve ayarlar.

Bu, sharepoint-taksonominin lexical etiketidir:SharedCustomPropertyForTerm, sharepoint-taksonomi:LocalCustomPropertyForTerm ve sharepoint-taksonomi:CustomPropertyForTermSet in a [TermStore](/dotnet/api/microsoft.sharepoint.taxonomy.termstore) çalışma dilinde.

Sharepoint-taksonomi:özellikAdı, CustomProperty'nin anahtarı olarak kabul edilir.

ÖzellikAdı tanımlama söz dizimi aşağıdaki gibidir:

```SKOS
ex:SharedCustomProperty1    sharepoint-taxonomy:propertyName    “Shared Custom Property Key 1”@en-us.
```

## <a name="optional-labels"></a>İsteğe bağlı etiketler

Taksonominize isteğe bağlı etiketler de abilirsiniz.

**sharepoint-taksonomi:otherLabel**

Bu, Terim'in alternatif lexical [etiketidir](/dotnet/api/microsoft.sharepoint.taxonomy.term).

Diğer Etiket tanımlama söz dizimi aşağıdaki gibidir:

```SKOS
ex:TermA    sharepoint-taxonomy:otherLabel    “Term A”@en-us.
```

## <a name="semantic-relationships"></a>Semantik ilişkiler

Taksonomilerin hiyerarşik ve bazen de basit bir "ilgili terim" ilişkisi vardır, ancak bazılarının "semantik ilişkileri" veya özel olarak oluşturulmuş ilişkileri vardır.

**sharepoint-taksonomi:parent**

Bu hiyerarşik olarak Bir Terim başka [Bir Terimle](/dotnet/api/microsoft.sharepoint.taxonomy.term) [ilgilidir](/dotnet/api/microsoft.sharepoint.taxonomy.term). Bir [Terim](/dotnet/api/microsoft.sharepoint.taxonomy.term) , bir Terim [Kümesi'nin](/dotnet/api/microsoft.sharepoint.taxonomy.term) [en üst düzey](/dotnet/api/microsoft.sharepoint.taxonomy.termset) Süresi olabilir, ancak böyle bir durumda üst Bir Terime sahip olması [gerekir](/dotnet/api/microsoft.sharepoint.taxonomy.term).

Üst öğe tanımlamak için kullanılan söz dizimi:

```SKOS
ex:TermA1    sharepoint-taxonomy:parent    ex:TermA.
```

Bu, TerimA'nın üst ve TermA'nın ise çocuk olduğu anlamına gelir.

**sharepoint-taksonomi:çocuk**

Nesne bir veya birden çok alt Terim Kümesi örneği içerir ve bunlara TermSets özelliğiyle erişilebilir. Bu sınıf yeni alt Terim Kümesi nesneleri oluşturma yöntemleri de sağlar. Alt Terim ve Terim Kümesi örneklerini düzenleme izinleri grupta belirtilir.

Bu hiyerarşik olarak Bir Terim başka [Bir Terimle](/dotnet/api/microsoft.sharepoint.taxonomy.term) [ilgilidir](/dotnet/api/microsoft.sharepoint.taxonomy.term).

Çocuk tanımlamak için kullanılan söz dizimi:

```SKOS
ex:TermA    sharepoint-taxonomy:child    ex:TermA1.
```

Bu, TerimA'nın üst ve TermA'nın ise çocuk olduğu anlamına gelir.

## <a name="documentation-notes"></a>Belge notları

Bu bölümde, Microsoft'ta ayrıntılı olarak ayrıntılı olarak yer alan taksonomi ele almaktadır. SharePoint. Taksonomi Ad Alanı.

**sharepoint-taksonomi:açıklama**

Bu, herhangi bir taksonomi [sözcük dağarcığı SharePoint ayrıntılı](/dotnet/api/microsoft.sharepoint.taxonomy) bir açıklamasıdır.

Açıklama ekleme söz dizimi:

```SKOS
ex:TermA    sharepoint-taxonomy:description    “Term A is the top level term of TermSetA”@en-us.
```

## <a name="custom-properties"></a>Özel özellikler

Salt okunur sözlükten geçerli Terim nesnesi için özel özellik nesneleri koleksiyonunu alır.

Özel Özellikler, Terim veya Terim Kümesi için tanımlanan anahtar değer [](/dotnet/api/microsoft.sharepoint.taxonomy.term) [](/dotnet/api/microsoft.sharepoint.taxonomy.term) [çiftleridir](/dotnet/api/microsoft.sharepoint.taxonomy.termset).[](/dotnet/api/microsoft.sharepoint.taxonomy.termset) SharePoint ÖzellikAdı yardımı ile özel özelliğin anahtarını belirtir.

**sharepoint-taksonomi:CustomPropertyForTermSet**

Bunu tanımlayan söz dizimi:

```SKOS
ex:CustomProp1    rdf:type    sharepoint-taxonomy:CustomPropertyForTermSet;
    sharepoint-taxonomy:propertyName “Colour”.

ex:TermSetA    ex:CustomProp1    “Red”@en-us.
```

**sharepoint-taksonomi:SharedCustomPropertyForTerm**

Bir Terim için özel [özelliğin Terim](/dotnet/api/microsoft.sharepoint.taxonomy.term) ile birlikte gerçekleştirilen olması [gerekirse, Terimi](/dotnet/api/microsoft.sharepoint.taxonomy.term) başka bir yerde yeniden kullanmanız gerekirse[](/dotnet/api/microsoft.sharepoint.taxonomy.term), onu SharedCustomPropertyForTerm altında tanımlamanız gerekir.

Bunu tanımlayan söz dizimi:

```SKOS
ex:CustomProp2    rdf:type sharepoint-taxonomy:SharedCustomPropertyForTerm;
    sharepoint-taxonomy:propertyName “Length”.

ex:TermA    ex:CustomProp2    “5 cm”@en-us.
```
**sharepoint-taksonomi:LocalCustomPropertyForTerm**

Bir Terim için özel özelliğin [](/dotnet/api/microsoft.sharepoint.taxonomy.term) Terim ile birlikte gerçekleştirilen bir özellik olması gerek [yoksa, Terimi](/dotnet/api/microsoft.sharepoint.taxonomy.term) başka bir yerde yeniden kullanmanız [](/dotnet/api/microsoft.sharepoint.taxonomy.term) gerekir ve bu özelliği LocalCustomPropertyForTerm altında tanımlamanız gerekir.

Bunu tanımlayan söz dizimi:

```SKOS
ex:CustomProp3    rdf:type sharepoint-taxonomy:LocalCustomPropertyForTerm;
    sharepoint-taxonomy:propertyName “width”.

ex:TermA    ex:CustomProp3    “5 cm”@en-us.
```

## <a name="data-properties"></a>Veri özellikleri

Hiyerarşinin her düzeyinde, Terim veya Terim Kümesi için belirli veri özelliklerini yapılandırabilirsiniz.

**sharepoint-taksonomi:isAvailableForTagging**

Listelerde ve Kitaplıklarda [Bir Terim](/dotnet/api/microsoft.sharepoint.taxonomy.term) veya [Terim Kümesi'nin](/dotnet/api/microsoft.sharepoint.taxonomy.termset) kullanılabilir SharePoint için kullanın.

Bunun söz dizimi:

```SKOS
ex:TermA    sharepoint-taxonomy:isAvailableForTagging     "true"^^xsd:Boolean;
```

## <a name="domain-and-range"></a>Etki alanı ve aralık

Aşağıdaki tabloda, taksonomi sözcük dağarcığının etki SharePoint aralığı açıklanmıştır.

|Yüklemler/fiil|Anlamı|Etki alanı|Aralık|
|:--------------|:------|:-----|:----|
inTermSet|Terim kümesinde|Dönem|Terim Kümesi|
inTermGroup|Terim grubunda|Terim Kümesi|TermGroup|
topLevelTermOf|en üst düzey terimdir|Dönem|Terim Kümesi|
hasTopLevelTerm|Üst düzey terimi var|Terim Kümesi|Dönem|
terimSetName|Terim kümesi Ad'a sahip|Dönem|Düz metin|
defaultLabel|Terim varsayılan etiketine sahip|Dönem|Düz metin|
otherLabel|Terimin başka bir etiketi var|Dönem|Düz metin|
özellikAdı|Özellik Etiketi Var|SharedCustomPropertyForTerm, LocalCustomPropertyForTerm, CustomPropertyForTermSet |Boole, Dize, Tamsayı, Ondalık, Çift|
|açıklama|Açıklama var|Tümü|Düz metin|
|üst|Üst öğesi var|Dönem|Dönem|
|çocuk|Çocuğun Var|Dönem|Dönem|
|isAvailableForTagging|Etiketleme için kullanılabilir|Terim, Terim Kümesi|Boole|
|SharedCustomPropertyForTerm|Paylaşılan özel özellik var|Dönem|Boole, dize, Tamsayı, Ondalık, Çift|
|LocalCustomPropertyForTerm|Yerel özel özelliği var|Dönem|Boole, Dize, Tamsayı, Ondalık, Çift|
|CustomPropertyForTermSet|Özel Özelliği Var|Terim Kümesi|Boole, Dize, Tamsayı, Ondalık, Çift|

[Taksonomiye izin SharePoint SKOS](https://www.w3.org/TR/skos-primer/) [geçerli](/dotnet/api/microsoft.sharepoint.taxonomy) senaryoları:

- Hiyerarşik yedekli çalışma - [SKOS](https://www.w3.org/TR/skos-primer/) kavramı birçok daha geniş kavrama aynı anda ek kullanılabilir, ancak sharepoint-taksonomisi:Terim tek bir sharepoint-taksonomisine sahip olabilir: parent, bu nedenle döngüsel bağımlılık, Terimler için de izin verilmez.
- Sahipsiz terimlere taksonomide SharePoint verilmez. Her sharepoint-taksonomisi:Terim için bir sharepoint-taksonomisi:parent veya sharepoint-taxonomy:topLevelTermOf a TermSet olması gerekir.
- SharePoint taksonomi ilişkisel ilişkileri desteklemez.
- SharePoint taksonomi yalnızca 2 tür Hiyerarşik ilişki türüne izin verir: sharepoint-taksonomi:parent ve sharepoint-Taxonomy:child.
- [SKOS'dan](https://www.w3.org/TR/skos-primer/) farklı olarak, SharePoint terim dağarcığı içindeki hiyerarşik ilişki, yalnızca aynı Terim Kümesi içindeki Terimler ile kurular.

## <a name="see-also"></a>Ayrıca bkz.

[SKOS tabanlı bir biçim kullanarak terim kümesi içeri aktarma](import-term-set-skos.md)