---
title: Özel hassas bilgi türleri oluşturma
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
description: Uyumluluk Merkezi'nde özel hassas bilgi türlerini oluşturmayı, değiştirmeyi, kaldırmayı ve test etmeyi öğrenin.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 0d93259cfe76419e253c450c4cd5ed7f03f3b85c
ms.sourcegitcommit: 6a981ca15bac84adbbed67341c89235029aad476
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2022
ms.locfileid: "65753528"
---
# <a name="create-custom-sensitive-information-types-in-the-compliance-center"></a>Uyumluluk merkezinde özel hassas bilgi türleri oluşturma

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Önceden yapılandırılmış hassas bilgi türleri gereksinimlerinizi karşılamıyorsa, tamamen tanımladığınız kendi özel hassas bilgi türlerinizi oluşturabilir veya önceden yapılandırılmış bilgi türlerinden birini kopyalayıp değiştirebilirsiniz.

Bu yöntemi kullanarak oluşturduğunuz özel hassas bilgi türleri adlı `Microsoft.SCCManaged.CustomRulePack`kural paketine eklenir.

Yeni bir hassas bilgi türü oluşturmanın iki yolu vardır:

- [tüm öğeleri tam olarak tanımladığınız sıfırdan](#create-a-custom-sensitive-information-type)
- [var olan hassas bilgi türünü kopyalama ve değiştirme](#copy-and-modify-a-sensitive-information-type)


## <a name="before-you-begin"></a>Başlamadan önce

- Hassas bilgi türleri ve bunların nelerden oluştuğu hakkında bilgi sahibi olmanız gerekir. Bkz. [Hassas bilgi türleri hakkında bilgi edinin](sensitive-information-type-learn-about.md). Aşağıdakilerin rollerini anlamak kritik önem taşır:
  - [normal ifadeler](https://www.boost.org/doc/libs/1_68_0/libs/regex/doc/html/) - Microsoft 365 hassas bilgi türleri Boost.RegEx 5.1.3 altyapısını kullanır
  - anahtar sözcük listeleri - Hassas bilgi türünüzü tanımlarken kendi anahtar sözcüğünüzü oluşturabilir veya mevcut anahtar sözcük listelerinden seçim yapabilirsiniz
  - [anahtar sözcük sözlüğü](create-a-keyword-dictionary.md)
  - [Hassas bilgi türü işlevleri](sit-functions.md)
  - [güvenilirlik düzeyleri](sensitive-information-type-learn-about.md#more-on-confidence-levels)

- Kuruluşunuzun Microsoft Purview Veri Kaybı Önleme (DLP) içeren Office 365 Kurumsal gibi bir aboneliği olmalıdır. bkz[. Microsoft Mesajlaşma İlke ve Uyumluluk HizmetiDescription](/office365/servicedescriptions/exchange-online-protection-service-description/messaging-policy-and-compliance-servicedesc). 

- Kuruluşunuzun veri kaybı önleme (DLP) içeren Office 365 Kurumsal gibi bir aboneliği olmalıdır. bkz[. Microsoft Mesajlaşma İlke ve Uyumluluk HizmetiDescription](/office365/servicedescriptions/exchange-online-protection-service-description/messaging-policy-and-compliance-servicedesc).

> [!IMPORTANT]
> Microsoft Müşteri Hizmetleri & Desteği, özel sınıflandırmalar veya normal ifade desenleri oluşturmaya yardımcı olamaz. Destek mühendisleri, test amacıyla örnek normal ifade desenleri sağlama veya beklendiği gibi tetiklenmeyen mevcut normal ifade deseninde sorun gidermeye yardımcı olma gibi özellikler için sınırlı destek sağlayabilir, ancak herhangi bir özel içerik eşleştirme geliştirmesinin gereksinimlerinizi veya yükümlülüklerinizi yerine getireceği konusunda güvence sağlayamaz.

## <a name="create-a-custom-sensitive-information-type"></a>Özel hassas bilgi türü oluşturma

Tam olarak tanımladığınız yeni bir hassas bilgi türü oluşturmak için bu yordamı kullanın.

1. Uyumluluk Merkezi'nde **Veri sınıflandırması** \> **Hassas bilgi türleri'ne** gidin ve **Hassas bilgi türü oluştur'u** seçin.

2. **Ad** ve **Açıklama** değerlerini doldurun ve **İleri'yi** seçin.

3. **Desen oluştur'u** seçin. Yeni hassas bilgi türünüzü tanımlarken her biri farklı öğelere ve güvenilirlik düzeylerine sahip birden çok desen oluşturabilirsiniz.

4. Desen için varsayılan güvenilirlik düzeyini seçin. Değerler **Düşük güvenilirlik**, **Orta güvenilirlik** ve **Yüksek güvenilirliktir**.

5. **Birincil öğeyi** seçin ve tanımlayın. Birincil öğe isteğe bağlı doğrulayıcı, **Anahtar Sözcük listesi, Anahtar Sözcük** **sözlüğü** veya önceden yapılandırılmış **İşlevlerden** birine sahip bir **Normal ifade** olabilir. DLP işlevleri hakkında daha fazla bilgi için bkz [. Hassas bilgi türü işlevleri](sit-functions.md). Tarih ve sağlama toplamı doğrulayıcıları hakkında daha fazla bilgi için bkz [. Hassas Bilgi Türü normal ifade doğrulayıcıları](sit-regex-validators-additional-checks.md#sensitive-information-type-regular-expression-validators).

6. **Karakter yakınlığı** için bir değer girin.

7. (İsteğe bağlı) Varsa destekleyici öğeler ekleyin. Destekleyici öğeler isteğe bağlı bir doğrulayıcı, anahtar sözcük listesi, anahtar sözcük sözlüğü veya önceden tanımlanmış işlevlerden birine sahip normal bir ifade olabilir. Destekleyici öğelerin kendi **Karakter yakınlık** yapılandırması olabilir.

8. (İsteğe bağlı) Kullanılabilir [**denetimler**](sit-regex-validators-additional-checks.md#sensitive-information-type-additional-checks) listesinden ek denetimler ekleyin.

9. **Oluştur**'u seçin.

10. **İleri**'yi seçin.

11. Bu hassas bilgi türü için **önerilen güvenilirlik düzeyini** seçin.

12. Ayarınızı denetleyin ve **Gönder'i** seçin.

    > [!IMPORTANT]
    > Microsoft 365, SharePoint Online ve OneDrive İş sitelerindeki hassas bilgileri tanımlamak ve sınıflandırmak için arama gezginini kullanır. Mevcut içerikteki yeni özel hassas bilgi türünüzü tanımlamak için içerikte yeniden gezinilmesi gerekir. İçerik bir zamanlamaya göre gezinilir, ancak site koleksiyonu, listesi veya kitaplığı için içeriği el ile yeniden gezinebilirsiniz. Daha fazla bilgi için bkz. [Site, kitaplık veya liste için el ile gezinme ve yeniden dizin oluşturma isteği](/sharepoint/crawl-site-content).

13. **Veri sınıflandırma** sayfasında, listelenen tüm hassas bilgi türlerini görürsünüz. **Yenile'yi** seçin ve oluşturduğunuz hassas bilgi türünü bulmak için arama aracına göz atın veya kullanın.

### <a name="copy-and-modify-a-sensitive-information-type"></a>Hassas bir bilgi türünü kopyalama ve değiştirme

Var olan bir hassas bilgi türünü temel alan yeni bir hassas bilgi türü oluşturmak için bu yordamı kullanın.

> [!NOTE]
> Bu SID'ler kopyalanamaz:
>
> - Kanada ehliyet numarası
> - AB ehliyet numarası
> - AB ulusal kimlik numarası
> - AB pasaport numarası
> - AB sosyal güvenlik numarası veya eşdeğer kimlik
> - AB vergi kimlik numarası
> - Uluslararası hastalık sınıflandırması (ICD-10-CM)
> - Uluslararası hastalık sınıflandırması (ICD-9-CM)
> - ABD ehliyet numarası

Ayrıca PowerShell ve Tam Veri Eşleştirme özelliklerini kullanarak özel hassas bilgi türleri de oluşturabilirsiniz. Bu yöntemler hakkında daha fazla bilgi edinmek için bkz:

- [Microsoft Purview PowerShell'de özel hassas bilgi türü oluşturma](create-a-custom-sensitive-information-type-in-scc-powershell.md)
- [Tam veri eşleşmesine dayalı hassas bilgi türleri hakkında daha fazla bilgi edinme](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types)

1. Uyumluluk Merkezi'nde **Veri sınıflandırması** \> **Hassas bilgi türleri'ne** gidin ve kopyalamak istediğiniz hassas bilgi türünü seçin.

2. Açılır öğede **Kopyala'yı** seçin.

3. Hassas bilgi türleri listesinde **Yenile'yi** seçin ve yeni oluşturduğunuz kopyaya göz atın veya bu kopyayı arayın. Kısmi sting aramaları işe yaradığından, yalnızca arama `copy` yapabilir ve arama, adında sözcük `copy` bulunan tüm hassas bilgi türlerini döndürür.

4. **Ad** ve **Açıklama** değerlerini doldurun ve **İleri'yi** seçin.

5. Hassas bilgi türünüzün kopyasını seçin ve **Düzenle'yi** seçin.

6. Yeni hassas bilgilerinize yeni bir **Ad** ve **Açıklama** yazın.

7. Mevcut desenleri düzenlemeyi veya kaldırmayı ve yeni desenler eklemeyi seçebilirsiniz. Yeni desen için varsayılan güvenilirlik düzeyini seçin. Değerler **Düşük güvenilirlik**, **Orta güvenilirlik** ve **Yüksek güvenilirliktir**.

8. **Birincil öğeyi** seçin ve tanımlayın. Birincil öğe **bir Normal ifade**, **Anahtar Sözcük listesi**, **Anahtar Sözcük sözlüğü** veya önceden yapılandırılmış **İşlevlerden** biri olabilir. Bkz. [Hassas bilgi türü işlevleri](sit-functions.md).

9. **Karakter yakınlığı** için bir değer girin.

10. (İsteğe bağlı) **Destekleyici öğeleriniz** veya [**ek denetimleriniz**](sit-regex-validators-additional-checks.md#sensitive-information-type-additional-checks) varsa bunları ekleyin. Gerekirse **Destekleyici öğelerinizi** gruplandırabilirsiniz.

11. **Oluştur**'u seçin.

12. **İleri**'yi seçin.

13. Bu hassas bilgi türü için **önerilen güvenilirlik düzeyini** seçin.

14. Ayarınızı denetleyin ve **Gönder'i** seçin.

## <a name="test-a-sensitive-information-type"></a>Hassas bilgi türünü test edin

Listedeki herhangi bir hassas bilgi türünü test edebilirsiniz. Bir ilkede kullanmadan önce oluşturduğunuz tüm hassas bilgi türlerini test etmenizi öneririz.

1. Word belgesi gibi iki dosya hazırlayın. Hassas bilgi türünüzde belirttiğiniz öğelerle eşleşen içeriğe ve eşleşmeyen içeriğe sahip bir tane.

2. Uyumluluk Merkezi'nde **Veri sınıflandırması** \> **Hassas bilgi türleri'ne** gidin ve listeden hassas bilgi türünü seçerek ayrıntılar bölmesini açın ve **Test'i** seçin.

3. Bir dosya Upload ve **Test'i** seçin.

4. **Sonuçlarla eşleşir** sayfasında sonuçları gözden geçirin ve **Son'u** seçin.

## <a name="custom-sensitive-information-types-limits"></a>Özel hassas bilgi türleri sınırları

Yüksek performans ve daha düşük gecikme süresi sağlamak için özel SID yapılandırmalarında sınırlamalar vardır.

|Sınırı|Değer|
|---|---|
|Uyumluluk merkezi aracılığıyla oluşturulan en fazla özel SID sayısı| 500 |
|normal ifadenin maksimum uzunluğu| 1024 karakter|
|anahtar sözcük listesindeki belirli bir terim için maksimum uzunluk| 50 karakter|
|anahtar sözcük listesindeki en fazla terim sayısı| 2048|
|hassas bilgi türü başına en fazla benzersiz kayıt defteri sayısı| 20|
|anahtar sözcük sözlüğünün en büyük boyutu (sıkıştırma sonrası)| 1 MB (~1.000.000 karakter)|
|kiracıdaki anahtar sözcük sözlüğü tabanlı SID sayısı üst sınırı|50 |

> [!NOTE]
> İşletmenin 500'den fazla özel SID oluşturması gerekiyorsa lütfen bir destek bileti oluşturun.

### <a name="instance-count-supported-values-for-sit"></a>SIT için örnek sayısı desteklenen değerler

SIT örneği sayısı sınırı, şu çözümlerde SID'ler kullanıldığında geçerlidir:

- DLP ilkeleri
- Information Protection
- Veri Yaşam Döngüsü Yönetimi
- İletişim Uyumluluğu
- Kayıt Yönetimi
- Bulut Uygulamaları için Microsoft Defender
- Microsoft Priva

Taranan bir öğenin kural ölçütlerini karşılaması için, tek bir öğedeki bir SIT'in benzersiz örneklerinin sayısı min ve max değerleri arasında olmalıdır. Buna **Örnek sayısı** adı verilir.

- **En küçük** alan: Eşleşmeyi tetikleyebilmek için bir öğede bulunması gereken bir SIT'in benzersiz örneklerinin alt sınırı (minimum sayı). Min alanı şu değerleri destekler:
  - 1 - 500
- **Maksimum** alan: Bir öğede bulunabilen ve yine de eşleşme tetikleyen benzersiz sit örneği sayısı üst sınırı. Max alanı şu değerleri destekler:
  - 1 ile 500 arası - Bir öğedeki SIT örneğinin sayısı için 500 veya daha az olan belirli bir üst sınır ayarlamak istediğinizde bunu kullanın.
  - Herhangi Biri - Taranan bir öğede bir SIT'in tanımlanmamış sayıda benzersiz örneği bulunduğunda ve benzersiz örnek sayısı minimum benzersiz örnek değerini karşıladığında veya aştığında benzersiz örnek sayısı ölçütlerinin karşılanmasını istediğinizde kullanın `Any` . Başka bir deyişle, min değeri karşılandığı sürece benzersiz örnek sayısı ölçütleri karşılanır.

Örneğin, bir SIT'in en az 500 benzersiz örneği tek bir öğede bulunduğunda kuralın eşleşme tetiklemesini istiyorsanız **, en küçük** değeri olarak `500` , **maksimum** değeri `Any`olarak ayarlayın.

> [!NOTE]
> Microsoft 365 Information Protection için çift bayt karakter kümesi dillerini destekler:
>
> - Çince (basitleştirilmiş)
> - Çince (geleneksel)
> - Korean
> - Japanese
>
> Bu destek, hassas bilgi türleri için kullanılabilir. Daha fazla bilgi için bkz. [Çift bayt karakter kümeleri için bilgi koruma desteği sürüm notları (önizleme).](mip-dbcs-relnotes.md)

> [!TIP]
> Çince/Japonca karakterler ve tek bayt karakterler içeren desenleri algılamak veya Çince/Japonca ve İngilizce içeren desenleri algılamak için anahtar sözcüğün veya regex'in iki değişkenini tanımlayın.
>
> - Örneğin, "机密的document" gibi bir anahtar sözcüğü algılamak için anahtar sözcüğün iki değişkenini kullanın; Biri Japonca ve İngilizce metin arasında boşluk, diğeri ise Japonca ve İngilizce metin arasında boşluk olmadan. Bu nedenle, SIT'e eklenecek anahtar sözcükler "机密的 belgesi" ve "机密的document" olmalıdır. Benzer şekilde, "東京オリンピック2020" ifadesini algılamak için iki değişken kullanılmalıdır; "東京オリンピック 2020" ve "東京オリンピック2020".
>
> Çince/Japonca/çift bayt karakterlerle birlikte, anahtar sözcükler/tümcecikler listesinde Çince/Japonca olmayan sözcükler de varsa (yalnızca İngilizce gibi), iki sözlük/anahtar sözcük listesi oluşturmanız önerilir. Biri Çince/Japonca/çift bayt karakter içeren anahtar sözcükler için, diğeri ise yalnızca İngilizce için.
>
> - Örneğin, "Çok gizli", "機密性が高い" ve "机密的document" ifadelerini içeren bir anahtar sözcük sözlüğü/listesi oluşturmak istiyorsanız, iki anahtar sözcük listesi oluşturmanız gerekir.
>   1. Çok gizli
>   2. 機密性が高い, 机密的document ve 机密的 belgesi
>
> Çift bayt kısa çizgi veya çift bayt dönemi kullanarak bir regex oluştururken, bir kısa çizgi veya bir regex'teki nokta gibi karakterlerin her ikisine de kaçış yaptığınızdan emin olun. Başvuru için örnek bir regex aşağıda verilmiştir:
>
> `(?<!\d)([4][0-9]{3}[\-?\-\t]*[0-9]{4})`
>
> Anahtar sözcükte çift baytlık özel karakterler kullanılmamalıdır.
>
> Anahtar sözcük listesinde sözcük eşleşmesi yerine dize eşleşmesi kullanmanızı öneririz.
