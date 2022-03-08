---
title: Hassas bilgi türleri hakkında bilgi
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
description: Bu makale, hassas bilgi türlerine ve hassas öğeleri tanımlamak için sosyal güvenlik, kredi kartı veya banka hesabı numarası gibi hassas bilgileri nasıl algılalarına genel bir bakış sağlar
ms.openlocfilehash: fbe23bbb6c639857367cc0b8467f6084e9116af1
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63318851"
---
# <a name="learn-about-sensitive-information-types"></a>Hassas bilgi türleri hakkında bilgi

Kuruluş denetimi altındaki hassas öğeleri tanımlama ve sınıflendirme, Bilgi Koruma disiplini için ilk [adımdır](./information-protection.md).  Microsoft 365, sınıflandırılmalarını belirlemek için üç yol sağlar:

- kullanıcılar tarafından el ile
- hassas bilgi türleri gibi otomatik desen tanıma
- [makine öğrenimi](classifier-learn-about.md)

Hassas bilgi türleri (SIT) desen tabanlı sınıflayıcılardır. Hassas öğeleri tanımlamak için sosyal güvenlik, kredi kartı veya banka hesabı numaraları gibi hassas bilgileri algılarlar, tüm SIT'lerin tam listesi için Hassas bilgi türleri varlık tanımları'ne bakın.[](sensitive-information-type-entity-definitions.md)

Microsoft çok sayıda önceden yapılandırılmış SIT sağlar veya kendi nızı oluşturabilirsiniz.

## <a name="sensitive-information-types-are-used-in"></a>Hassas bilgi türleri

- [Veri kaybı önleme ilkeleri](dlp-learn-about-dlp.md)
- [Duyarlılık etiketleri](sensitivity-labels.md)
- [Bekletme etiketleri](retention.md)
- [Insider risk yönetimi](insider-risk-management.md)
- [İletişim uyumluluğu](communication-compliance.md)
- [Otomatik etiketleme ilkeleri](apply-sensitivity-label-automatically.md#how-to-configure-auto-labeling-for-office-apps)
- [Microsoft Priva](/privacy/priva)

## <a name="categories-of-sensitive-information-types"></a>Hassas bilgi türleri kategorileri

### <a name="built-in-sensitive-information-types"></a>Yerleşik hassas bilgi türleri

Bu SIT'ler Microsoft tarafından varsayılan olarak uyumluluk konsolunda oluşturulur. Bu SIT'ler düzenlenemez, ancak şablon olarak kullanılabilir ve özel hassas bilgi türleri oluşturmak için kopyalanır. Tüm [SI'ların tam listesi için](sensitive-information-type-entity-definitions.md) Bkz. Hassas bilgi türü varlık tanımları.

### <a name="named-entity-sensitive-information-types"></a>Adlandırılmış varlık duyarlı bilgi türleri

Adlandırılmış varlık SIT'leri de varsayılan olarak uyumluluk konsolunda görüntülenir. Kişi adlarını, fiziksel adresleri, tıbbi hüküm ve koşulları algılar. Düzenlenemez veya kopyalanamaz. Daha fazla [bilgi için Bkz. Adlandırılmış varlıklar (önizleme)](named-entities-learn.md#learn-about-named-entities-preview) hakkında bilgi. Adlandırılmış varlık SIT'leri iki tür gelir:

**paketsiz**

Bu adlandırılmış varlık SITS'leri, tek bir ülke veya tek bir terim sınıfı gibi daha dar bir odaktadır. Daha dar algılama kapsamına sahip bir DLP ilkesine ihtiyacınız olduğunda bunları kullanın. Bkz [. Adlandırılmış varlık SI'lerinin örnekleri](named-entities-learn.md#examples-of-named-entity-sits).

**paketli**

Paketli adlandırılmış varlık SIT'leri, Sınıftaki Tüm fiziksel adresler gibi olası tüm eşleşmeleri algılar. Hassas öğeleri algılamak için DLP ilkeleriniz içinde bunları geniş ölçüt olarak kullanın. Bkz [. Adlandırılmış varlık SI'lerinin örnekleri](named-entities-learn.md#examples-of-named-entity-sits).

### <a name="custom-sensitive-information-types"></a>Özel hassas bilgi türleri

Önceden yapılandırılmış hassas bilgi türleri sizin ihtiyaçlarını karşılamazsanız, tamamen tanımladığınız kendi özel hassas bilgi türlerinizi oluşturabilir veya yerleşik bilgilerden birini kopyalayıp değiştirebilirsiniz. Daha fazla [bilgi için Uyumluluk Merkezi'nde özel hassas bilgi türü](create-a-custom-sensitive-information-type.md) oluşturma' konularına bakın.

### <a name="exact-data-match-sensitive-information-types"></a>Hassas bilgi türleriyle tam eşleşmesi

Tüm EDM tabanlı SITS'ler sıfırdan oluşturulur. Hassas bilgiler veritabanında tanımladığınız tam değerlere sahip öğeleri algılamak için bunları kullanırsınız. Daha fazla [bilgi için Bkz. Temel alınan hassas bilgi türleriyle tam eşleşme hakkında](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types) bilgi.

## <a name="fundamental-parts-of-a-sensitive-information-type"></a>Hassas bir bilgi türünün temel parçaları

Her hassas bilgi türü varlığa şu alanlar tanımlanır:

- ad: Hassas bilgi türü nasıl adlandırılır?
- açıklama: Hassas bilgi türünün ne arıyor olduğunu açıklar
- desen: Desen, hassas bir bilgi türünün algıladığı şeyi tanımlar. Aşağıdaki bileşenlerden oluşur.
    - Birincil öğe – Hassas bilgi türünün arıyor olduğu ana öğe. Denetim doğrulama, **anahtar sözcük listesi**, anahtar sözcük sözlüğü veya işlev içeren veya olmayan normal bir ifade **olabilir**.
    - Destekleyen öğe – Eşleşmenin güvenlerini artırmaya yardımcı olacak kanıt olarak destekleyen öğeler. Örneğin, bir SSN sayısına yakınlık içinde "SSN" anahtar sözcüğünü kullanın. Denetimler, anahtar sözcük listesi ve anahtar sözcük sözlüğü içeren veya olmayan normal bir ifade olabilir.
    - Güven Düzeyi - Güven düzeyleri (yüksek, orta, düşük), birincil öğeyle birlikte ne kadar destekleyen kanıtın algılandığından anlar. Bir öğenin içerdiği kanıt ne kadar fazla olursa, eşanlı öğenin sizin istediğiniz hassas bilgileri içerdiği güven o kadar yüksektir.
    - Yakınlık – Birincil ve desteklenen öğe arasındaki karakter sayısı.

![Kanıt ve yakınlık penceresi diyagramı.](../media/dc68e38e-dfa1-45b8-b204-89c8ba121f96.png)

Güven düzeyleri hakkında daha fazla bilgi edinmek için bu kısa videoyu izleyin.


 > [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4Hx60]  



### <a name="example-sensitive-information-type"></a>Örnek duyarlı bilgi türü


#### <a name="argentina-national-identity-dni-number"></a>Arjantin ulusal kimliği (DNI) numarası

### <a name="format"></a>Biçim

Noktayla ayrılmış sekiz basamak

### <a name="pattern"></a>Desen

Sekiz basamak:
- İki basamak
- dönem
- üç basamak
- dönem
- üç basamak

### <a name="checksum"></a>Checksum

Hayır

### <a name="definition"></a>Tanım

DLP ilkesi, 300 karakter yakınlık içinde olursa, bu tür hassas bilgilerin algılandığından orta düzeyde güven sağlar:
- Normal ifade Regex_argentina_national_id desene eşleşen içeriği bulur.
- Anahtar sözcük Keyword_argentina_national_id bulunur.

```xml
<!-- Argentina National Identity (DNI) Number -->
<Entity id="eefbb00e-8282-433c-8620-8f1da3bffdb2" recommendedConfidence="75" patternsProximity="300">
   <Pattern confidenceLevel="75">
      <IdMatch idRef="Regex_argentina_national_id"/>
      <Match idRef="Keyword_argentina_national_id"/>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>Anahtar Sözcükler

#### <a name="keyword_argentina_national_id"></a>Keyword_argentina_national_id

- Arjantin Ulusal Kimliği numarası 
- Kimlik 
- Kimlik Ulusal Kimlik Kartı 
- DNI 
- NIC National Registry of Persons 
- Documento Nacional de Identidad 
- Registro Nacional de las Personas 
- Identidad 
- Identificación 

### <a name="more-on-confidence-levels"></a>Güven düzeyleri hakkında daha fazla bilgi

Hassas bir bilgi türü varlık tanımında **, güven** düzeyi birincil öğeye ek olarak ne kadar destekleyen kanıtın algılandığından fazlasını yansıtır. Bir öğenin içerdiği kanıt ne kadar fazla olursa, eşanlı öğenin sizin istediğiniz hassas bilgileri içerdiği güven o kadar yüksektir. Örneğin, yüksek güven düzeyindeki eşleşmeler birincil öğeye yakın bir şekilde daha fazla destekleyen kanıt içerirken, düşük güven düzeyine sahip eşleşmeler yakınlık içinde çok az destek kanıtı içerebilir. 

Yüksek güven düzeyi en düşük hatalı pozitif sonuçları verir, ancak daha çok yanlış negatif sonuçlar verir. Düşük veya orta düzeydeki güven düzeyleri daha çok hatalı pozitif, ancak sıfırdan sıfıra sıfırdan küçük negatifler döndürür.

- **düşük güven**: Eşleşmeli öğeler, en düşük yanlış negatifleri, ancak en yanlış pozitifleri içerir. Düşük güven, düşük, orta ve yüksek güven eşleşmelerini döndürür. Düşük güven düzeyi 65 değerindedir.
- **orta düzeyde** güven: Eşleşmeli öğeler, ortalama bir miktarda yanlış pozitif ve yanlış negatif sonuçlar içerir. Orta güven, tüm orta ve yüksek güven eşleşmelerini döndürür. Orta güven düzeyi 75 değerindedir.
- **yüksek güven**: Eşleşmeli öğeler, en düşük yanlış pozitif, ancak en yanlış negatifleri içerir. Yüksek güven yalnızca yüksek güven eşleşmelerini döndürür ve değeri 85'tir.  

Düşük sayımlarla, beş ile on arasında ve daha yüksek sayımlarla, diyelim ki 20 veya daha çok güven düzeyi düzenleriyle yüksek güven düzeyi düzenleri kullan gerekir.

> [!NOTE]
> Sayı tabanlı güven düzeyleri (doğruluğu da denir) kullanılarak tanımlanmış ilkeleriniz veya özel hassas bilgi türleriniz (SITS) varsa, bunlar otomatik olarak üç ayrık güven düzeyine eşlenir; güvenlik @ Uyumluluk Merkezi kullanıcı arabirimi genelinde düşük güven, orta güven ve yüksek güven oranı.
> - 76 ile 100 arasında güven düzeyine sahip en düşük doğruluk veya özel SIT düzenine sahip tüm ilkeler, yüksek güven düzeyine eşlenmiş olur. 
> - 66 ile 75 arasında güven düzeyine sahip en düşük doğruluk veya özel SIT düzenleri olan tüm ilkeler, orta düzeyde güven düzeyine eşlenmiş olur.
> - Güven düzeyleri 65'e eşit veya daha düşük olan en düşük doğruluk veya özel SIT düzenleri olan tüm ilkeler, düşük güven düzeyine eşlenmiş olur. 

## <a name="creating-custom-sensitive-information-types"></a>Özel hassas bilgi türleri oluşturma

Uyumluluk Merkezi'nde özel hassas bilgi türleri oluşturmak için çeşitli seçenekler seçebilirsiniz.

- **Kullanıcı arabirimini** kullanma - Uyumluluk Merkezi kullanıcı arabirimini kullanarak özel bir hassas bilgi türü oluşturabilirsiniz. Bu yöntemle, normal ifadeleri, anahtar sözcükleri ve anahtar sözcük sözlüklerini kullanabilirsiniz. Daha fazla bilgi edinmek için bkz [. Özel duyarlı bilgi türü oluşturma](create-a-custom-sensitive-information-type.md).

- **EDM kullan** - Tam Veri Eşleşmesi (EDM) tabanlı sınıflandırmayı kullanarak özel hassas bilgi türleri oluşturabilirsiniz. Bu yöntem, düzenli aralıklarla yeniley güvenli bir veritabanı kullanarak dinamik ve hassas bir bilgi türü oluşturmanıza olanak sağlar. Bkz[. Temel alınan hassas bilgi türleriyle tam veri eşleşmesi hakkında bilgi.](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types)

- **PowerShell kullanma** - PowerShell kullanarak özel hassas bilgi türlerini kurabilirsiniz. Bu yöntem, kullanıcı arabirimi kullanımından daha karmaşık olsa da, daha fazla yapılandırma seçeneği vardır. Güvenlik [ve Uyumluluk Merkezi PowerShell'de özel & bilgi türü oluşturma.](create-a-custom-sensitive-information-type-in-scc-powershell.md)

> [!NOTE]
> Gelişmiş güven düzeyleri; Veri Kaybı Önleme'nin içinde Microsoft 365 hizmetleri, Microsoft Bilgi Koruması hizmetleri, Microsoft 365 Uyumluluğu, Bilgi Yönetimi ve Kayıt Yönetimi için anında kullanılabilir.
> Microsoft 365 Koruması artık çift byte karakter kümesi dillerini şu dillerde destekler:
> - Çince (basitleştirilmiş)
> - Çince (geleneksel)
> - Korean
> - Japanese
> 
> Bu destek, hassas bilgi türlerinde kullanılabilir. Daha fazla [bilgi için çift byte karakter kümesi sürüm notları için Bilgi koruma](mip-dbcs-relnotes.md) desteği'ne bakın.

> [!TIP]
> Çince/Japonca karakterler ve tek bir byte karakteri içeren desenleri algılamak veya Çince/Japonca ve İngilizce dillerini içeren desenleri algılamak için anahtar sözcüğün veya regex'in iki çeşitleni tanımlayın.
> - Örneğin, "机密的document" gibi bir anahtar sözcüğü algılamak için, anahtar sözcüğün iki çeşitleni kullanın; Japonca ve İngilizce metin arasında boşluk olmayan ve Japonca ve İngilizce metinler arasında boşluk olmayan bir metin. Dolayısıyla SIT'e eklenecek anahtar sözcükler "机密的 belgesi" ve "机密的document" olabilir. Benzer şekilde, "東京オリンピック2020" tümceciği algılamak için iki değişken kullanılmalıdır: "東京オリンピック 2020" ve "東京オリンピック2020".
> 
> Anahtar sözcükler/tümcecikler listesi Çince/Japonca sözcükler de (yalnızca İngilizce gibi) içeriyorsa, Çince/Japonca/çift byte karakterleriyle birlikte, iki sözlük/anahtar sözcük listesi oluşturmanız gerekir. Çince/Japonca/çift byte karakter içeren anahtar sözcükler için bir tane ve yalnızca İngilizce için bir tane daha. 
> - Örneğin, "Çok gizli", "機密性が高い" ve "机密的document" ifadelerini içeren bir anahtar sözcük sözlüğü/listesi oluşturmak için iki anahtar sözcük listesi oluşturmanız gerekir. 
>     1. Çok gizli
>     2. 機密性が高い, 机密的document ve 机密的 belgesi
> 
> Çift bayt kısa çizgi veya çift byte dönemi kullanarak bir kayıtex oluşturulurken, bir kayıtex içinde bir kısa çizgi veya nokta gibi iki karakterin de kaçışta olduğundan emin olun. Başvuru için örnek bir kayıtex:
>    - (?<!\d) ([4][0-9]{3} [\-?\-\t]*[0-9]{4}
>
> Anahtar sözcük listesinde sözcük eşleşmesi yerine dize eşleşmesi kullanılması önerilir.

## <a name="for-further-information"></a>Daha fazla bilgi için
- [Hassas bilgi türü varlık tanımları](sensitive-information-type-entity-definitions.md)
- [Özel hassas bilgi türü oluşturma](create-a-custom-sensitive-information-type.md)
- [PowerShell'de özel duyarlı bilgi türü oluşturma](create-a-custom-sensitive-information-type-in-scc-powershell.md)

Hassas bilgi türlerinin veri gizliliği düzenlemelerine uygun şekilde nasıl kullanıla ilgili olduğunu öğrenmek için bkz. Gizlilikle ilgili veri gizliliği düzenlemelerine [Microsoft 365 (aka.ms/m365dataprivacy](../solutions/information-protection-deploy.md)).

<!-- fwlink for this topic https://go.microsoft.com/fwlink/?linkid=2135644-->
