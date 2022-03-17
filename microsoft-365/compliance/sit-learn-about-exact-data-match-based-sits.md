---
title: Hassas bilgi türlerine dayalı tam veri eşleşmesi hakkında bilgi
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
description: Hassas bilgi türlerine dayalı tam veri eşleşmesi hakkında bilgi edinebilirsiniz.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 21e6f3c12d7c401562a1ee1915e1e1c266724b1b
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/17/2022
ms.locfileid: "63526928"
---
# <a name="learn-about-exact-data-match-based-sensitive-information-types"></a>Hassas bilgi türlerine dayalı tam veri eşleşmesi hakkında bilgi

[Hassas](sensitive-information-type-learn-about.md) bilgi türleri hassas öğeleri tanımlamanıza yardımcı olmak için kullanılır; böylelikle yanlışlıkla veya uygunsuz şekilde paylaşılmalarını önlenebilir, eBulma'da ilgili verileri bulmak ve belirli bilgi türlerine yönetim eylemleri uygulamak için kullanılır. Özel bir hassas bilgi türü (SIT) tanımlamanız için şunları temel alarak:

- desenler
- çalışan, sosyal *güvenlik numarası* *veya kimlik gibi anahtar* sözcük *kanıtı*
- belirli bir kalıpta kanıta karakter yakınlığı
- güven düzeyleri

Peki genel desenlere göre eşleşmelerden birini değil, tam veya neredeyse tam olarak kullanan özel bir hassas bilgi türü (SIT) kullanmak ister misiniz? Tam Veri Eşleşmesi (EDM) tabanlı sınıflandırmayla, şunları yapmak için tasarlanmış özel bir hassas bilgi türü oluşturabilirsiniz:

- dinamik ve kolayca yenilenir
- daha ölçeklenebilir
- sonucu daha az yanlış pozitif sonuç verir
- yapılandırılmış hassas verilerle çalışma
- hassas bilgileri Microsoft dahil hiç kimseyle paylaşmadan daha güvenli bir şekilde işleme
- birkaç Microsoft bulut hizmetiyle kullanılabilir

![EDM tabanlı sınıflandırma.](../media/EDMClassification.png)

EDM tabanlı sınıflandırma, hassas bilgiler veritabanındaki tam değerlere başvuran özel hassas bilgi türleri oluşturmanıza olanak sağlar. Veritabanı günlük olarak yenilenir ve en çok 100 milyon veri satırı içerir. Böylece çalışanlar, hastalar veya müşteriler gelip gider ve kayıtlar değiştiklerinde özel hassas bilgi türleriniz güncel ve geçerli kalır. Ayrıca, veri kaybı önleme ilkeleri veya dosya ilkeleri gibi ilkelerle EDM tabanlı [Microsoft Cloud App Security kullanabilirsiniz](/cloud-app-security/data-protection-policies).[](dlp-learn-about-dlp.md)

> [!NOTE]
> Microsoft 365 Koruması aşağıdakiler için çift byte karakter kümesi dillerini destekler:
>
> - Çince (basitleştirilmiş)
> - Çince (geleneksel)
> - Korean
> - Japanese
>
> Bu destek, hassas bilgi türlerinde kullanılabilir. Daha fazla [bilgi için çift byte karakter kümesi sürüm notları (önizleme) için Bilgi koruma](mip-dbcs-relnotes.md) desteği'ne bakın.

## <a name="whats-different-in-an-edm-sit"></a>EDM SIT'daki farklar

EDM SITS ile çalışıyorken, benzersiz olan birkaç kavramı anlamak yararlı olur.  

### <a name="schema"></a>Şema

Şema, şunları tanımlayan bir XML dosyasıdır:

- Şemanın daha sonra Veri Deposu olarak adlandırılan *adı*. 
- Hassas bilgi kaynağı tablonuzda yer alan alan adları. Şema alanı adının hassas bilgi kaynağı tablo sütun adına 1:1 eşlemesi vardır.
- Hangi alanlarda arama değiştirilebilir?
- Aranan değerlerde sınırlayıcıları ve *büyük/harfe* yoksayma gibi yapılandırılabilir eşleşme olarak adlandırılan herhangi bir arama değiştirme parametresi.

### <a name="sensitive-information-source-table"></a>Hassas bilgi kaynağı tablosu

Hassas kaynak tablo, EDM SIT'in bakacağız hassas bilgi değerlerini içerir. Sütunlar ve satırlardan yapılır. Sütun başlıkları alan adlarıdır, satırlar bir veri örneğidir ve her hücrede bu alanın değerleri yer alır.

Burada, hassas bir bilgi kaynağı tablosuna basit bir örnek ve ve bir ve sonra da ve bir örnek ve bir başka ifade ve daha sonra açık ve açık bir şekilde ve şekilde açık ve açık bir şekilde açık ve

|Ad  |Soyadı  |Doğum tarihi  |
|---------|---------|---------|
|Isaiah   |Langer  | 05-05-1960 |
|Ana   |Bowman         |11-24-1971 |
|Nite   |Burya         |02-12-1998 |


### <a name="rule-package"></a>Kural paketi

Her SIT'in bir kural paketi vardır. Kural paketini bir EDM SIT'te kullanarak şunları tanımlar:

- Tam aramada kullanılacak birincil öğe olacak alanı belirten eşleşmeler. Denetim doğrulama, anahtar sözcük listesi, anahtar sözcük sözlüğü veya işlev içeren veya olmayan normal bir ifade olabilir.
- Sınıflandırma, EDM aramalarını tetikleyen hassas tür eşleşmesi belirtir.
- Destek öğesi, bulunduklarında eşleşmenin güvenlerini artırmaya yardımcı olacak destekleyen kanıt sağlayan öğelerdir. Örneğin, bir SSN sayısının yakınlığında "SSN" anahtar sözcüğünü kullanın. Denetimler, anahtar sözcük listesi ve anahtar sözcük sözlüğü içeren veya olmayan normal bir ifade olabilir.
- Güven düzeyleri (yüksek, orta, düşük), birincil öğeyle birlikte ne kadar destekleyen kanıtın algıladığnı yansıtır. Bir öğenin içerdiği kanıt ne kadar fazla olursa, eşanlı öğenin sizin istediğiniz hassas bilgileri içerdiği güven o kadar yüksektir. Güven düzeyleri [hakkında daha fazla bilgi için bkz.](sensitive-information-type-learn-about.md#fundamental-parts-of-a-sensitive-information-type) Hassas bir bilgi türünün temel parçaları.
Yakınlık – Birincil ve desteklenen öğe arasındaki karakter sayısı

### <a name="you-supply-your-own-schema-and-data"></a>Kendi şemanızı ve verilerinizi siz sağlarsınız

Microsoft 365 tanımlı şemalar, regex desenleri, anahtar sözcükler ve güven düzeyleri ile [birlikte 200'den fazla SITS](sensitive-information-type-entity-definitions.md) ile birlikte gelir. EDM SITS'lerle, hassas öğeleri tanımlayan hem şemayı hem de birincil ve ikincil alanları tanımlamak sizin sorumluluğundadır. Şema ve birincil ve ikincil veri değerleri çok hassas olduğundan, bunları rastgele veya kendi kendine sağlanan bir salt değeri içeren bir [](/dotnet/standard/security/ensuring-data-integrity-with-hash-codes) karma işleviyle [şifrelersiniz](https://en.wikipedia.org/wiki/Salt_(cryptography)#:~:text=The%20salt%20value%20is%20generated%20at%20random%20and,the%20salt%20value%20and%20hashed%20value%20are%20stored.). Bundan sonra söz konusu karma değerler hizmete yüklenmez ve böylece hassas verileriniz hiçbir zaman açık değildir.

### <a name="primary-and-secondary-support-elements"></a>Birincil ve ikincil destek öğeleri

EDM SIT oluşturmada, kural *paketinde* bir birincil öğe alanı tanımlarsanız. Birincil alanlar, tüm içeriğinizi araytıracak ve tanımlanacak tanımlı bir düzeni izlemesi gereken öğelerdir. Birincil öğe taranmış öğelerin içinde bulunurken, EDM bir desene uyması gerek etmeyen ikincil veya destekleyen öğeleri ve birincil öğeye yakınlıklarını aratır. EDM, birincil öğenin önce var olan bir SIT aracılığıyla keşfedilebilir olması gerekir. Kullanılabilir [SITS'lerin tam listesi](sensitive-information-type-entity-definitions.md) için Bkz. Hassas bilgi türü varlık tanımları. EDM SIT'inizin algılaması istediğiniz sınıfı algılayanlardan birini bulmanız gerekir. Örneğin, EDM SIT şemanız birincil öğe olarak ABD sosyal güvenlik numarasına sahipse, EDM şemanızı oluştursanız bunu ABD sosyal güvenlik numarası [(SSN)](sensitive-information-type-entity-definitions.md#us-social-security-number-ssn) SIT ile ilişkilendirilmiş olursanız.


## <a name="how-matching-works"></a>Eşleştirme nasıl çalışır?

EDM, bulduğu içeriği sizin tanımladığınız hassas veri tablosuyla karşılaştırarak eşleşmeleri bulur. Eşleşme testi, eşleşme verilerin bulmak ve korumak istediğiniz gerçek bir veri örneği olduğundan emin olmak için geleneksel kurallar ve düzenlerin bir birleşimi kullanılarak yapılır. EDM, temel işlevi, tek yol şifreleme karmaları karşılaştırarak içeriğinizin değerlerinin tabloda bulun bulup bulmasını sağlamak için, bu verileri sağlayan hassas veri tablosunda yer alan değerlerle belgeleriniz ve e-postalardaki dizeleri karşılaştırarak çalışır.

> [!TIP]
> Yaygın bir uygulama, EDM Duyarlı bilgi türlerinin ve DLP kurallarına dayalı normal hassas bilgi türlerinin kullanımını farklı eşiklerle birleştirmektir. Örneğin, bir veya birden çok eşleşmenin DLP uyarısına neden olduğu yerde düşük olan ve sıkı gereksinimleri olan ve düşük olan, sosyal güvenlik numaralarını ve diğer verileri araması için EDM'ye duyarlı bir bilgi türü kullanabilir ve daha yüksek sayımlar için yerleşik olarak yer alan ABD Sosyal Güvenlik Numarası gibi normal hassas bilgi türünü kullanabilirsiniz.  

## <a name="see-also"></a>Ayrıca bkz.

- [Hassas bilgi türlerine dayalı tam veri eşleşmesi ile çalışmaya başlama](sit-get-started-exact-data-match-based-sits-overview.md#get-started-with-exact-data-match-based-sensitive-information-types)
   
