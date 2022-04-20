---
title: Hassas bilgi türleri hakkında daha fazla bilgi edinme
f1.keywords:
- CSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: Admin
search.appverid: MET150
ms.topic: conceptual
f1_keywords:
- ms.o365.cc.UnifiedDLPRuleContainsSensitiveInformation
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
description: Bu makale hassas bilgi türlerine ve hassas öğeleri tanımlamak için sosyal güvenlik, kredi kartı veya banka hesabı numaraları gibi hassas bilgileri nasıl algıladıklarına genel bakış sağlar
ms.openlocfilehash: 0e154e0ee578b9a182cb7cd5b43cafba466f9bcd
ms.sourcegitcommit: 45bc65972d4007b2aa7760d4457a0d2699f81926
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/20/2022
ms.locfileid: "64971361"
---
# <a name="learn-about-sensitive-information-types"></a>Hassas bilgi türleri hakkında daha fazla bilgi edinme

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Kuruluşunuzun denetimi altındaki hassas öğeleri tanımlamak ve sınıflandırmak[, Information Protection uzmanlık alanında](./information-protection.md) ilk adımdır.  Microsoft Purview, sınıflandırılabilmeleri için öğeleri tanımlamanın üç yolunu sağlar:

- kullanıcılar tarafından el ile
- hassas bilgi türleri gibi otomatik desen tanıma
- [makine öğrenmesi](classifier-learn-about.md)

Hassas bilgi türleri (SIT), desen tabanlı sınıflandırıcılardır. Hassas öğeleri tanımlamak için sosyal güvenlik, kredi kartı veya banka hesabı numaraları gibi hassas bilgileri algılarlar. Tüm SID'lerin tam listesi için [bkz. Hassas bilgi türleri varlık tanımları](sensitive-information-type-entity-definitions.md) .

Microsoft çok sayıda önceden yapılandırılmış SID sağlar veya kendiniz oluşturabilirsiniz.

## <a name="sensitive-information-types-are-used-in"></a>Hassas bilgi türleri

- [Microsoft Purview Veri Kaybı Önleme ilkeleri](dlp-learn-about-dlp.md)
- [Duyarlılık etiketleri](sensitivity-labels.md)
- [Bekletme etiketleri](retention.md)
- [İçeriden risk yönetimi](insider-risk-management.md)
- [İletişim uyumluluğu](communication-compliance.md)
- [Otomatik etiketleme ilkeleri](apply-sensitivity-label-automatically.md#how-to-configure-auto-labeling-for-office-apps)
- [Microsoft Priva](/privacy/priva)

## <a name="categories-of-sensitive-information-types"></a>Hassas bilgi türleri kategorileri

### <a name="built-in-sensitive-information-types"></a>Yerleşik hassas bilgi türleri

Bu SID'ler Microsoft tarafından varsayılan olarak uyumluluk konsolunda gösterilir. Bu SID'ler düzenlenemez, ancak şablon olarak kullanılabilir ve özel hassas bilgi türleri oluşturmak için kopyalanabilir. Tüm SID'lerin tam listesi için [bkz. Hassas bilgi türü varlık tanımları](sensitive-information-type-entity-definitions.md) .

### <a name="named-entity-sensitive-information-types"></a>Adlandırılmış varlık duyarlı bilgi türleri

Adlandırılmış varlık SID'leri de varsayılan olarak uyumluluk konsolunda gösterilir. Kişi adlarını, fiziksel adresleri ve tıbbi hüküm ve koşulları algılar. Bunlar düzenlenemez veya kopyalanamaz. Daha fazla bilgi için bkz. [Adlandırılmış varlıklar hakkında bilgi edinin ](named-entities-learn.md#learn-about-named-entities) . Adlandırılmış varlık SID'leri iki türde gelir:

**paketlenmemiş**

Bu adlandırılmış varlık SID'leri, tek bir ülke veya tek bir terim sınıfı gibi daha dar bir odak noktası içerir. Daha dar bir algılama kapsamına sahip bir DLP ilkesine ihtiyacınız olduğunda bunları kullanın. Bkz. [Adlandırılmış varlık SID örnekleri](named-entities-learn.md#examples-of-named-entity-sits).

**Birlikte**

Paketlenmiş adlandırılmış varlık SID'leri, Tüm fiziksel adresler gibi bir sınıftaki tüm olası eşleşmeleri algılar. Bunları, hassas öğeleri algılamak için DLP ilkelerinizde geniş ölçütler olarak kullanın. Bkz. [Adlandırılmış varlık SID örnekleri](named-entities-learn.md#examples-of-named-entity-sits).

### <a name="custom-sensitive-information-types"></a>Özel hassas bilgi türleri

Önceden yapılandırılmış hassas bilgi türleri gereksinimlerinizi karşılamıyorsa, tamamen tanımladığınız kendi özel hassas bilgi türlerinizi oluşturabilir veya yerleşik bilgi türlerinden birini kopyalayıp değiştirebilirsiniz. Daha fazla bilgi için bkz. [Uyumluluk merkezinde özel hassas bilgi türü oluşturma](create-a-custom-sensitive-information-type.md) .

### <a name="exact-data-match-sensitive-information-types"></a>Hassas bilgi türleriyle tam olarak eşleşen veriler

Tüm EDM tabanlı SID'ler sıfırdan oluşturulur. Hassas bilgi veritabanında tanımladığınız tam değerlere sahip öğeleri algılamak için bunları kullanırsınız. Daha fazla bilgi için bkz. [Tam veri eşleşmesi tabanlı hassas bilgi türleri hakkında bilgi edinin](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types) .

## <a name="fundamental-parts-of-a-sensitive-information-type"></a>Hassas bilgi türünün temel bölümleri

Her hassas bilgi türü varlığı şu alanlar tarafından tanımlanır:

- name: Hassas bilgi türüne nasıl başvurulduğu
- description: Hassas bilgi türünün ne aradığını açıklar
- desen: Desen, hassas bir bilgi türünün algıladığı bilgileri tanımlar. Aşağıdaki bileşenlerden oluşur.
  - Birincil öğe – Hassas bilgi türünün aradığı ana öğe. Sağlama toplamı doğrulaması, **anahtar sözcük listesi, anahtar sözcük** **sözlüğü** veya **işlev** içeren veya olmayan **normal bir ifade** olabilir.
  - Destekleyici öğe – Eşleşmenin güvenilirliğini artırmaya yardımcı olan destekleyici kanıt görevi üstleyen öğeler. Örneğin, bir SSN numarasına yakın olan "SSN" anahtar sözcüğü. Sağlama toplamı doğrulaması, anahtar sözcük listesi, anahtar sözcük sözlüğü ile veya olmadan normal bir ifade olabilir.
  - Güvenilirlik Düzeyi - Güvenilirlik düzeyleri (yüksek, orta, düşük), birincil öğeyle birlikte ne kadar destekleyici kanıt algılandığını yansıtır. Bir öğe ne kadar destekleyici kanıt içeriyorsa, eşleşen bir öğenin aradığınız hassas bilgileri içerdiğine o kadar fazla güvenir.
  - Yakınlık – Birincil ve destekleyici öğe arasındaki karakter sayısı.

![Doğrulayıcı kanıt ve yakınlık penceresinin diyagramı.](../media/dc68e38e-dfa1-45b8-b204-89c8ba121f96.png)

Bu kısa videoda güvenilirlik düzeyleri hakkında daha fazla bilgi edinin.

 > [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4Hx60]

### <a name="example-sensitive-information-type"></a>Örnek hassas bilgi türü

#### <a name="argentina-national-identity-dni-number"></a>Arjantin ulusal kimlik (DNI) numarası

### <a name="format"></a>Biçim

Noktalarla ayrılmış sekiz basamak

### <a name="pattern"></a>Desen

Sekiz basamak:

- iki basamak
- dönem
- üç basamak
- dönem
- üç basamak

### <a name="checksum"></a>Sağlama toplamı

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karaktere yakın olduğunda bu tür hassas bilgiler algılandığının orta düzeyde güvenilirliğine sahiptir:

- Normal ifade Regex_argentina_national_id desenle eşleşen içeriği bulur.
- Keyword_argentina_national_id anahtar sözcüğü bulunur.

```xml
<!-- Argentina National Identity (DNI) Number -->
<Entity id="eefbb00e-8282-433c-8620-8f1da3bffdb2" recommendedConfidence="75" patternsProximity="300">
   <Pattern confidenceLevel="75">
      <IdMatch idRef="Regex_argentina_national_id"/>
      <Match idRef="Keyword_argentina_national_id"/>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>Anahtar kelime -ler

#### <a name="keyword_argentina_national_id"></a>Keyword_argentina_national_id

- Arjantin Ulusal Kimlik numarası
- Kimlik
- Kimlik Ulusal Kimlik Kartı
- DNI
- NIC Ulusal Kişi Kayıt Defteri
- Documento Nacional de Identidad
- Registro Nacional de las Personas
- Identidad
- Identificación

### <a name="more-on-confidence-levels"></a>Güvenilirlik düzeyleri hakkında daha fazla bilgi

Hassas bilgi türü varlık tanımında **güvenilirlik düzeyi** , birincil öğeye ek olarak ne kadar destekleyici kanıt algılandığından etkilenir. Bir öğe ne kadar destekleyici kanıt içeriyorsa, eşleşen bir öğenin aradığınız hassas bilgileri içerdiğine o kadar fazla güvenir. Örneğin, yüksek güvenilirlik düzeyine sahip eşleşmeler birincil öğeye yakın daha destekleyici kanıtlar içerirken, düşük güvenilirlik düzeyine sahip eşleşmeler çok az veya hiç destekleyici kanıt içermeyecektir.

Yüksek güvenilirlik düzeyi en az hatalı pozitif sonuç verir, ancak daha fazla hatalı negatife neden olabilir. Düşük veya orta güvenilirlik düzeyleri daha fazla hatalı pozitif sonuç verir, ancak az veya sıfır hatalı negatif döndürür.

- **düşük güvenilirlik**: Eşleşen öğeler en az hatalı negatif ancak en yanlış pozitifleri içerir. Düşük güvenilirlik, tüm düşük, orta ve yüksek güvenilirlik eşleşmelerini döndürür. Düşük güvenilirlik düzeyi 65 değerine sahiptir.
- **orta güvenilirlik**: Eşleşen öğeler ortalama miktarda hatalı pozitif ve hatalı negatifler içerir. Orta güvenilirlik, tüm orta ve yüksek güvenilirlik eşleşmelerini döndürür. Orta güvenilirlik düzeyi 75 değerine sahiptir.
- **yüksek güvenilirlik**: Eşleşen öğeler en az hatalı pozitif ancak en hatalı negatifleri içerir. Yüksek güvenilirlik yalnızca yüksek güvenilirlik eşleşmelerini döndürür ve 85 değerine sahiptir.

Düşük sayılarla yüksek güvenilirlik düzeyi desenleri, örneğin beş ile on arasında ve daha yüksek sayılarla (örneğin 20 veya daha fazla) düşük güvenilirlik desenleri kullanmalısınız.

> [!NOTE]
> Sayı tabanlı güvenilirlik düzeyleri (doğruluk olarak da bilinen) kullanılarak tanımlanmış mevcut ilkeleriniz veya özel hassas bilgi türleriniz (SCT'ler) varsa, bunlar otomatik olarak üç ayrı güvenilirlik düzeyiyle eşlenir; Güvenlik @ Uyumluluk Merkezi kullanıcı arabirimi genelinde düşük güvenilirlik, orta güvenilirlik ve yüksek güvenilirlik.
>
> - Minimum doğruluk düzeyine sahip tüm ilkeler veya 76 ile 100 arasında güvenilirlik düzeyine sahip özel SIT desenleri yüksek güvenilirlikle eşlenir.
> - Minimum doğruluk düzeyine veya 66 ile 75 arasında güvenilirlik düzeyine sahip özel SIT desenlerine sahip tüm ilkeler orta güven düzeyine eşlenir.
> - En düşük doğruluk düzeyine veya 65'e eşit güvenilirlik düzeyine sahip özel SIT desenlerine sahip tüm ilkeler düşük güvenilirlikle eşlenir.

## <a name="creating-custom-sensitive-information-types"></a>Özel hassas bilgi türleri oluşturma

Uyumluluk Merkezi'nde özel hassas bilgi türleri oluşturmak için çeşitli seçenekler arasından seçim yapabilirsiniz.

- **Kullanıcı arabirimini kullanma** - Uyumluluk Merkezi kullanıcı arabirimini kullanarak özel bir hassas bilgi türü ayarlayabilirsiniz. Bu yöntemle normal ifadeleri, anahtar sözcükleri ve anahtar sözcük sözlüklerini kullanabilirsiniz. Daha fazla bilgi için bkz. [Özel hassas bilgi türü oluşturma](create-a-custom-sensitive-information-type.md).

- **EDM kullanma** - Tam Veri Eşleştirme (EDM) tabanlı sınıflandırmayı kullanarak özel hassas bilgi türleri ayarlayabilirsiniz. Bu yöntem, düzenli aralıklarla yenileyebileceğiniz güvenli bir veritabanı kullanarak dinamik hassas bilgi türü oluşturmanıza olanak tanır. Bkz. [Tam veri eşleştirme tabanlı hassas bilgi türleri hakkında bilgi edinin](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types).

- **PowerShell kullanma - PowerShell** kullanarak özel hassas bilgi türleri ayarlayabilirsiniz. Bu yöntem kullanıcı arabirimini kullanmaktan daha karmaşık olsa da, daha fazla yapılandırma seçeneğiniz vardır. Bkz. [Güvenlik & Uyumluluk Merkezi PowerShell'de özel hassas bilgi türü oluşturma](create-a-custom-sensitive-information-type-in-scc-powershell.md).

> [!NOTE]
> Geliştirilmiş güvenilirlik düzeyleri Microsoft Purview veri kaybı önleme hizmetleri, bilgi koruma, İletişim Uyumluluğu, veri yaşam döngüsü yönetimi ve kayıt yönetimi içinde anında kullanılabilir.
> Information Protection artık aşağıdakiler için çift bayt karakter kümesi dillerini destekliyor:
> - Çince (basitleştirilmiş)
> - Çince (geleneksel)
> - Korean
> - Japanese
>
> Bu destek, hassas bilgi türleri için kullanılabilir. Daha fazla bilgi için bkz. [Çift bayt karakter kümeleri için bilgi koruma desteği sürüm notlarını ayarlar](mip-dbcs-relnotes.md) .

> [!TIP]
> Çince/Japonca karakterler ve tek bayt karakterler içeren desenleri algılamak veya Çince/Japonca ve İngilizce içeren desenleri algılamak için anahtar sözcüğün veya regex'in iki değişkenini tanımlayın.
>
> - Örneğin, "机密的document" gibi bir anahtar sözcüğü algılamak için anahtar sözcüğün iki değişkenini kullanın; Biri Japonca ve İngilizce metin arasında boşluk, diğeri ise Japonca ve İngilizce metin arasında boşluk olmadan. Bu nedenle, SIT'e eklenecek anahtar sözcükler "机密的 belgesi" ve "机密的document" olmalıdır. Benzer şekilde, "東京オリンピック2020" ifadesini algılamak için iki değişken kullanılmalıdır; "東京オリンピック 2020" ve "東京オリンピック2020".
>
> Çince/Japonca/çift bayt karakterlerle birlikte, anahtar sözcükler/tümcecikler listesinde Çince/Japonca olmayan sözcükler de varsa (yalnızca İngilizce gibi), iki sözlük/anahtar sözcük listesi oluşturmanız gerekir. Biri Çince/Japonca/çift bayt karakter içeren anahtar sözcükler için, diğeri ise yalnızca İngilizce için.
>
> - Örneğin, "Çok gizli", "機密性が高い" ve "机密的document" ifadelerini içeren bir anahtar sözcük sözlüğü/listesi oluşturmak istiyorsanız, iki anahtar sözcük listesi oluşturmanız gerekir.
>     1. Çok gizli
>     2. 機密性が高い, 机密的document ve 机密的 belgesi
>
> Çift bayt kısa çizgi veya çift bayt dönemi kullanarak bir regex oluştururken, bir kısa çizgi veya bir regex'teki nokta gibi karakterlerin her ikisine de kaçış yaptığınızdan emin olun. Başvuru için örnek bir regex aşağıda verilmiştir:
>
> `(?<!\d)([4][0-9]{3}[\-?\-\t]*[0-9]{4}`
>
> Anahtar sözcük listesinde sözcük eşleşmesi yerine dize eşleşmesi kullanmanızı öneririz.

## <a name="for-further-information"></a>Daha fazla bilgi için

- [Hassas bilgi türü varlık tanımları](sensitive-information-type-entity-definitions.md)
- [Özel hassas bilgi türü oluşturma](create-a-custom-sensitive-information-type.md)
- [PowerShell'de özel hassas bilgi türü oluşturma](create-a-custom-sensitive-information-type-in-scc-powershell.md)

Veri gizliliği düzenlemelerine uymak için hassas bilgi türlerini kullanmayı öğrenmek için bkz[. Microsoft 365 (aka.ms/m365dataprivacy) ile veri gizliliği düzenlemeleri için bilgi koruması dağıtma](../solutions/information-protection-deploy.md).

<!-- fwlink for this topic https://go.microsoft.com/fwlink/?linkid=2135644-->
