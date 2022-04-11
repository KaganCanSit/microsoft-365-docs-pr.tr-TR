---
title: Tam veri eşleşmesine dayalı hassas bilgi türleri hakkında daha fazla bilgi edinme
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.date: ''
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Tam veri eşleşmesi tabanlı hassas bilgi türleri hakkında bilgi edinin.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 7f883d2509961ee07045949530f8fbb50629212f
ms.sourcegitcommit: 9ba00298cfa9ae293e4a57650965fdb3e8ffe07b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/11/2022
ms.locfileid: "64759777"
---
# <a name="learn-about-exact-data-match-based-sensitive-information-types"></a>Tam veri eşleşmesine dayalı hassas bilgi türleri hakkında daha fazla bilgi edinme

[Hassas bilgi türleri](sensitive-information-type-learn-about.md) , hassas öğelerin yanlışlıkla veya uygunsuz bir şekilde paylaşılmasını önlemek, eBulma'da ilgili verilerin bulunmasına yardımcı olmak ve belirli bilgi türlerine idare eylemleri uygulamak için kullanılır. Aşağıdakilere göre özel bir hassas bilgi türü (SIT) tanımlarsınız:

- Desen
- *çalışan*, *sosyal güvenlik numarası* veya *kimlik* gibi anahtar sözcük kanıtı
- belirli bir desendeki kanıta karakter yakınlığı
- güvenilirlik düzeyleri

Peki ya genel desenleri temel alan eşleşmeler bulmak yerine tam veya neredeyse tam veri değerlerini kullanan özel bir hassas bilgi türü (SIT) istiyorsanız? Tam Veri Eşleşmesi (EDM) tabanlı sınıflandırma ile, aşağıdakileri yapmak için tasarlanmış özel bir hassas bilgi türü oluşturabilirsiniz:

- dinamik olmak ve kolayca yenilenmek
- daha ölçeklenebilir olmak
- daha az hatalı pozitif sonuç
- yapılandırılmış hassas verilerle çalışma
- Hassas bilgileri daha güvenli bir şekilde işleme, Microsoft dahil olmak üzere kimseyle paylaşmama
- çeşitli Microsoft bulut hizmetleriyle kullanılmak

![EDM tabanlı sınıflandırma.](../media/EDMClassification.png)

EDM tabanlı sınıflandırma, hassas bilgi veritabanındaki tam değerlere başvuran özel hassas bilgi türleri oluşturmanıza olanak tanır. Veritabanı günlük olarak yenilenebilir ve 100 milyon satıra kadar veri içerebilir. Çalışanlar, hastalar veya müşteriler gelip gittikçe ve kayıtlar değiştikçe, özel hassas bilgi türleriniz güncel ve geçerli kalır. Ayrıca, [veri kaybı önleme](dlp-learn-about-dlp.md) ilkeleri veya [Microsoft Cloud App Security dosya](/cloud-app-security/data-protection-policies) ilkeleri gibi ilkelerle EDM tabanlı sınıflandırmayı kullanabilirsiniz.

> [!NOTE]
> Microsoft 365 Information Protection için çift bayt karakter kümesi dillerini destekler:
>
> - Çince (basitleştirilmiş)
> - Çince (geleneksel)
> - Korean
> - Japanese
>
> Bu destek, hassas bilgi türleri için kullanılabilir. Daha fazla bilgi için bkz. [Çift bayt karakter kümeleri için bilgi koruma desteği sürüm notları (önizleme).](mip-dbcs-relnotes.md)

## <a name="whats-different-in-an-edm-sit"></a>EDM SIT'teki farklar

EDM SID'leri ile çalışırken, kendilerine özgü birkaç kavramı anlamanız yararlı olur.  

### <a name="schema"></a>Şema

Şema, aşağıdakileri tanımlayan bir xml dosyasıdır:

- Daha sonra *DataStore* olarak adlandırılan şemanın adı. 
- Hassas bilgi kaynağı tablonuzun içerdiği alan adları. Şema alanı adının hassas bilgi kaynağı tablo sütun adıyla 1:1 eşlemesi vardır.
- Hangi alanlar aranabilir.
- Sınırlayıcıları ve aranan değerlerdeki büyük/küçük harflerini yoksayma gibi *yapılandırılabilir eşleşme* olarak adlandırılan parametreleri değiştiren tüm aramalar.

### <a name="sensitive-information-source-table"></a>Hassas bilgi kaynağı tablosu

Hassas kaynak tablo, EDM SIT'in arayacağı hassas bilgi değerlerini içerir. Sütunlardan ve satırlardan oluşur. Sütun başlıkları alan adlarıdır, satırlar bir veri örneğidir ve her hücre o alanın o örneğine ait değerleri içerir.

Hassas bilgi kaynağı tablosunun basit bir örneği aşağıda verilmiştır.

|Ad|Soyadı|Doğum tarihi|
|---|---|---|
|Yeşaya|Langer| 05-05-1960|
|Ana|Bowman|11-24-1971|
|Oscar|Ward|02-12-1998|

### <a name="rule-package"></a>Kural paketi

Her SIT'in bir kural paketi vardır. Kural paketini bir EDM SIT'te kullanarak aşağıdakileri tanımlarsınız:

- Eşleşmeler, tam aramada kullanılacak birincil öğe olacak alanı belirtir. Sağlama toplamı doğrulaması, anahtar sözcük listesi, anahtar sözcük sözlüğü veya işlev içeren veya olmayan normal bir ifade olabilir.
- EDM aramasını tetikleyen hassas tür eşleşmesini belirten sınıflandırma.
- Bulunduğunda eşleşmenin güvenilirliğini artırmaya yardımcı olacak destekleyici kanıt sağlayan öğeler olan destekleyici öğe. Örneğin, bir SSN numarasının yakınında "SSN" anahtar sözcüğü. Sağlama toplamı doğrulaması, anahtar sözcük listesi, anahtar sözcük sözlüğü ile veya olmadan normal bir ifade olabilir.
- Güvenilirlik düzeyleri (yüksek, orta, düşük), birincil öğeyle birlikte ne kadar destekleyici kanıt algılandığını yansıtır. Bir öğe ne kadar destekleyici kanıt içeriyorsa, eşleşen bir öğenin aradığınız hassas bilgileri içerdiğine o kadar fazla güvenir. Güvenilirlik düzeyleri hakkında daha fazla [bilgi için bkz. Hassas bilgi türünün temel bölümleri](sensitive-information-type-learn-about.md#fundamental-parts-of-a-sensitive-information-type) .
Yakınlık - Birincil ve destekleyici öğe arasındaki karakter sayısı

### <a name="you-supply-your-own-schema-and-data"></a>Kendi şemanızı ve verilerinizi sağlayın

Microsoft 365 önceden tanımlanmış şemalar, regex desenleri, anahtar sözcükler ve güvenilirlik düzeyleri ile [200'den fazla SITS ile birlikte gelir](sensitive-information-type-entity-definitions.md). EDM SID'leri ile, şemanın yanı sıra hassas öğeleri tanımlayan birincil ve ikincil alanları tanımlamak sizin sorumluluğundadır. Şema ve birincil ve ikincil veri değerleri son derece hassas olduğundan, bunları rastgele oluşturulan veya kendi kendine sağlanan [bir tuz](https://en.wikipedia.org/wiki/Salt_(cryptography)#:~:text=The%20salt%20value%20is%20generated%20at%20random%20and,the%20salt%20value%20and%20hashed%20value%20are%20stored.) değeri içeren bir [karma](/dotnet/standard/security/ensuring-data-integrity-with-hash-codes) işlevi aracılığıyla şifrelersiniz. Bu karma değerler daha sonra hizmete yüklenir, dolayısıyla hassas verileriniz hiçbir zaman açık olmaz.

### <a name="primary-and-secondary-support-elements"></a>Birincil ve ikincil destek öğeleri

EDM SIT oluşturduğunuzda, kural paketinde *bir birincil öğe* alanı tanımlarsınız. Birincil alanlar, tüm içeriğinizin aranacağı ve tanımlanabilmesi için tanımlı bir deseni izlemesi gereken öğelerdir. Taranan öğelerde birincil öğe bulunduğunda, EDM bir deseni izlemesi gerekmeyen *ikincil* veya destekleyici öğeleri ve bunların birincil öğeye yakınlıklarını arar. EDM, birincil öğenin önce var olan bir SIT aracılığıyla bulunabilir olmasını gerektirir. Kullanılabilir SID'lerin tam listesi için [bkz. Hassas bilgi türü varlık tanımları](sensitive-information-type-entity-definitions.md) . EDM SIT'inizin algılamasını istediğiniz sınıfı algılayanlardan birini bulmanız gerekir. Örneğin, EDM SIT şemanızda birincil öğe olarak ABD sosyal güvenlik numarası varsa, EDM şemanızı oluşturduğunuzda, bunu [ABD sosyal güvenlik numarası (SSN)](sensitive-information-type-entity-definitions.md#us-social-security-number-ssn) SIT ile ilişkilendirmiş olursunuz.


## <a name="how-matching-works"></a>Eşleştirme nasıl çalışır?

EDM, bulduğu içeriği sizin tanımladığınız hassas veri tablosuyla karşılaştırarak eşleşmeleri bulur. Eşleştirme testi, eşleştirilen verilerin bulmak ve korumak istediğiniz verilerin gerçek bir örneği olduğundan emin olmak için geleneksel kurallar ve desenlerin bir bileşimi kullanılarak gerçekleştirilir. EDM, tek yönlü şifreleme karmalarını karşılaştırarak içeriğinizdeki değerlerin tabloda mevcut olup olmadığını öğrenmek için belgelerinizdeki dizeleri ve e-postaları sağladığınız hassas veri tablosundaki değerlerle karşılaştırarak çalışır.

> [!TIP]
> Yaygın bir uygulama, EDM Hassas bilgi türlerinin ve DLP kurallarında temel aldıkları normal hassas bilgi türlerinin kullanımını farklı eşiklerle birleştirmektir. Örneğin, bir veya daha fazla eşleşmenin DLP uyarısına neden olacağı katı gereksinimler ve düşük tolerans ile sosyal güvenlik numaralarını ve diğer verileri arayabilen bir EDM hassas bilgi türü kullanabilir ve daha yüksek sayımlar için ABD Sosyal Güvenlik Numarası yerleşik konumu gibi normal hassas bilgi türünü kullanabilirsiniz.  

## <a name="see-also"></a>Ayrıca bkz.

- [Tam veri eşleşmesine dayalı hassas bilgi türlerini kullanmaya başlama](sit-get-started-exact-data-match-based-sits-overview.md#get-started-with-exact-data-match-based-sensitive-information-types)
   
