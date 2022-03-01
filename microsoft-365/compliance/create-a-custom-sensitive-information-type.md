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
description: Uyumluluk Merkezi'nde özel hassas bilgi türlerini oluşturma, değiştirme, kaldırma ve test etmeyi öğrenin.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 2526ab9fdde4e5cedbbf3e831e6ec8ac9a6a5747
ms.sourcegitcommit: bb493f12701f6d6ee7d5e64b541adb87470bc7bc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/18/2022
ms.locfileid: "63015485"
---
# <a name="create-custom-sensitive-information-types-in-the-compliance-center"></a>Uyumluluk merkezinde özel hassas bilgi türleri oluşturma

Önceden yapılandırılmış hassas bilgi türleri sizin ihtiyaçlarını karşılamazsa, tamamen tanımladığınız kendi özel hassas bilgi türlerinizi oluşturabilir veya önceden yapılandırılmış bilgilerden birini kopyalayıp değiştirebilirsiniz.

Bu yöntemi kullanarak oluştursanız da özel hassas bilgi türleri, adlı kural paketine eklenir `Microsoft.SCCManaged.CustomRulePack`.

Yeni hassas bilgi türü oluşturmanın iki yolu vardır:

- [tüm öğeleri tümüyle tanımladığınız sıfırdan](#create-a-custom-sensitive-information-type)
- [Var olan hassas bilgi türünü kopyalama ve değiştirme](#copy-and-modify-a-sensitive-information-type)


## <a name="before-you-begin"></a>Başlamadan önce

- Hassas bilgi türlerini ve bunların ne tür içeriklerini biliyor olması gerekir. Hassas bilgi [türleri hakkında bilgi edinmek için bkz](sensitive-information-type-learn-about.md). Aşağıdakilerin rollerini anlamak çok önemlidir:
    - [normal ifadeler](https://www.boost.org/doc/libs/1_68_0/libs/regex/doc/html/) - Microsoft 365 bilgi türleri için Boost.RegEx 5.1.3 altyapısını kullanır
    - anahtar sözcük listeleri - Hassas bilgi türlerinizi tanımlarken veya var olan anahtar sözcük listelerinden birini seçenken kendi listenizi oluşturabilirsiniz
    - [anahtar sözcük sözlüğü](create-a-keyword-dictionary.md)
    - [Hassas bilgi türü işlevleri](sit-functions.md)
    - [güven düzeyleri](sensitive-information-type-learn-about.md#more-on-confidence-levels)
 
- Kullanıcı arabirimi aracılığıyla özel hassas bilgi türünü oluşturmak, test etmek ve dağıtmak için Genel yönetici veya Uyumluluk yöneticisi izinlerine sahip olmak gerekir. Bkz[. Office 365'da](/office365/admin/add-users/about-admin-roles) yönetici rolleri hakkında.

- Kuruluş, Veri Kaybı Önleme (DLP) dahil Office 365 Kurumsal, örneğin bir aboneliğe sahip olması gerekir. Bkz [. İleti İlkesi ve Uyumluluk HizmetiAzınlama](/office365/servicedescriptions/exchange-online-protection-service-description/messaging-policy-and-compliance-servicedesc). 


> [!IMPORTANT]
> Microsoft Müşteri & Desteği, özel sınıflandırmalar veya normal ifade düzenleri oluşturmaya yardımcı olabilir. Destek mühendisleri, özellik için test amacıyla örnek normal ifade modelleri sağlama veya beklendiği gibi tetik getirmeyen mevcut normal ifade düzeninde sorun gidermeye yardımcı olmak gibi, ancak özel içerik eşleştirme geliştirmeleri için gereksinimlerinizi veya yükümlülüklerinizi karşılayacak güvenceler sağlanmaz.

## <a name="create-a-custom-sensitive-information-type"></a>Özel hassas bilgi türü oluşturma

Tümüyle tanımladığınız yeni bir hassas bilgi türü oluşturmak için bu yordamı kullanın. 

1. Uyumluluk Merkezi'nde Veri sınıflandırması Hassas **bilgi türleri'ne** \> **gidin ve Hassas** bilgi **türü oluştur'a tıklayın**.

2. Ad ve Açıklama değerlerini **doldurun** **ve Sonraki'yi** **seçin**.

3. Desen **oluştur'a seçin**. Yeni hassas bilgi türlerinizi tanımladığınız gibi, her biri farklı öğelere ve güven düzeylerine sahip birden çok düzen oluşturabilirsiniz.

4. Desen için varsayılan güven düzeyini seçin. Değerler **Düşük güven,** Orta güven **ve** Yüksek **güven değerleridir**.

5. Birincil öğeyi seçin **ve tanımlayın**. Birincil öğe, isteğe bağlı  olarak doğrulayıcı, Anahtar sözcük listesi, Anahtar sözcük sözlüğü veya önceden yapılandırılmış işlevlerden birini içeren bir Normal ifade **olabilir**. DLP işlevleri hakkında daha fazla bilgi için bkz. [Hassas bilgi türü işlevleri](sit-functions.md). Tarih ve denetimli aralık geçerliliği hakkında daha fazla bilgi için bkz. Hassas Bilgi [Türü normal ifade doğrulayıcıları](sit-regex-validators-additional-checks.md#sensitive-information-type-regular-expression-validators).

6. Karakter yakınlığı için bir **değer doldurun**.

7. (İsteğe bağlı) Varsa, destekleyen öğeler ekleyin. Destek öğeleri, isteğe bağlı olarak doğrulayıcı, anahtar sözcük listesi, anahtar sözcük sözlüğü veya önceden tanımlanmış işlevlerden birini içeren normal bir ifade olabilir. Destekleyen öğelerin kendi Karakter yakınlığı **yapılandırması** olabilir. 

8. (İsteğe bağlı) Kullanılabilir [**denetimler listesinden**](sit-regex-validators-additional-checks.md#sensitive-information-type-additional-checks) daha fazla denetim ekleyin.

9. **Oluştur**'u seçin.

10. **İleri**'yi seçin.

11. Bu hassas **bilgi türü için önerilen** güven düzeyini seçin.

12. Ayarınızı kontrol edin ve Gönder'i **seçin**.

    > [!IMPORTANT]
    > Microsoft 365, SharePoint Online ve OneDrive İş sitelerine ilişkin hassas bilgileri tanımlamak ve sınıflandırmak için arama OneDrive İş kullanır. Var olan içerikte yeni özel hassas bilgi türlerinizi tanımlamak için, içerikte yeniden gezinilenler gerekir. İçerikte zamanlamaya göre gezinilir, ancak site koleksiyonu, liste veya kitaplığın içeriği üzerinde el ile yeniden gezinebilirsiniz. Daha fazla bilgi için bkz. Site, kitaplık veya liste için gezinme ve yeniden dizin [oluşturma el ile isteğinde bulundurabilirsiniz](/sharepoint/crawl-site-content).

13. Veri **sınıflandırma sayfasında** tüm hassas bilgi türlerinin listelenmiş olduğunu görebilirsiniz. **Yenile'yi** seçin ve oluşturduğunuz hassas bilgi türünü bulmak için arama aracına göz atabilir veya aracı kullanabilirsiniz.

### <a name="copy-and-modify-a-sensitive-information-type"></a>Hassas bilgi türünü kopyalama ve değiştirme

Var olan hassas bilgi türünü temel alan yeni bir hassas bilgi türü oluşturmak için bu yordamı kullanın. 

> [!NOTE]
> Şu SIT'ler kopyalanamaz:
> - Kanada sürücüsünün lisans numarası
> - AB sürücü lisans numarası
> - AB ulusal kimlik numarası
> - AB pasaport numarası
> - AB sosyal güvenlik numarası veya eşdeğer tanımlama
> - AB vergi tanımlama numarası
> - Ulusal hukuk sınıflandırması (ICD-10-CM)
> - Uluslararası hastalık sınıflandırması (ICD-9-CM)
> - ABD sürücüsünün lisans numarası

Ayrıca, PowerShell ve Tam Veri Eşleşmesi özelliklerini kullanarak özel hassas bilgi türleri de oluşturabilirsiniz. Bu yöntemler hakkında daha fazla bilgi edinmek için bkz:
- [Güvenlik ve Uyumluluk Merkezi PowerShell'de özel & bilgi türü oluşturma](create-a-custom-sensitive-information-type-in-scc-powershell.md)
- [Hassas bilgi türlerine dayalı tam veri eşleşmesi hakkında bilgi](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types)

1. Uyumluluk Merkezi'nde Veri **sınıflandırması Hassas** \> **bilgi türleri'ne** gidin ve kopyalamak istediğiniz hassas bilgi türünü seçin.

2. Uçarak çıkışta Kopyala'ya **seçin**.

3. Hassas **bilgi** türleri listesinde Yenile'yi seçin ve az önce hazır olduğunuz kopyaya göz atabilir veya bu kopyayı arayabilirsiniz. Kısmi parçalı aramalar çalışır, böylece `copy` yalnızca aramayla tüm hassas bilgi türlerini arayabilir ve adını bu sözcükle `copy` birlikte arayabilirsiniz. 

4. Ad ve Açıklama değerlerini **doldurun** **ve Sonraki'yi** **seçin**.

5. Hassas bilgi türlerinizi kopyalayıp Düzenle'yi **seçin**. 

6. Yeni hassas bilgilerinize yeni bir Ad ve **Açıklama** **yazın**.

7. Var olan desenleri düzenlemeyi veya kaldırmayı ve yenilerini  eklemeyi seçebilirsiniz. Yeni model için varsayılan güven düzeyini seçin. Değerler **Düşük güven,** Orta güven **ve** Yüksek **güven değerleridir**.

8. Birincil öğeyi seçin **ve tanımlayın**. Birincil öğe bir Normal ifade, **Anahtar** **sözcük listesi**, Anahtar sözcük **sözlüğü veya** önceden yapılandırılmış işlevlerden biri **olabilir**. Bkz. [Hassas bilgi türü işlevleri](sit-functions.md).

9. Karakter yakınlığı için bir **değer doldurun**.

10. (İsteğe bağlı) Destekleyen öğeler **veya ek denetimler** [**varsa, bunları**](sit-regex-validators-additional-checks.md#sensitive-information-type-additional-checks) ekleyin. Gerekirse, Destekleyen **öğelerinizi gruplamanız da gerekir**.

11. **Oluştur**'u seçin.

12. **İleri**'yi seçin.

13. Bu hassas **bilgi türü için önerilen** güven düzeyini seçin.

14. Ayarınızı kontrol edin ve Gönder'i **seçin**.

## <a name="test-a-sensitive-information-type"></a>Hassas bir bilgi türünü test edin

Listede herhangi bir hassas bilgi türünü test edin. İlkede kullanmadan önce, oluştursanız bile her hassas bilgi türünü sınamanızı öneririz.

1. Word belgesi gibi iki dosya hazırlayın. Hassas bilgi türünüzde belirttiğiniz öğelerle eşleşen ve eşleşmeen içerikli bir içerik.

2. Uyumluluk Merkezi'nde Veri sınıflandırması  \> Hassas bilgi **türleri'ne** gidin, ayrıntılar bölmesini açmak için listeden hassas bilgi türünü seçin ve sonra da Sına'ya **tıklayın**.

3. Upload ve Sına'ya **seçin**.

4. Eşleşme **sonuçları sayfasında sonuçları gözden** geçirip Son'a **tıklayın**.

## <a name="custom-sensitive-information-types-limits"></a>Özel hassas bilgi türleri sınırları

Yüksek performans ve düşük gecikme süresi sağlamak için, özel SITS yapılandırmalarında sınırlamalar vardır.

|Sınır|Değer|
|--------|--------|
|Uyumluluk Merkezi aracılığıyla oluşturulan özel SIT sayısı üst sayısı| 500 |
|normal ifade en fazla uzunluğu| 1024 karakter|
|anahtar sözcük listesinde verilen bir terim için maksimum uzunluk| 50 karakter|
|anahtar sözcük listesinde en fazla terim sayısı| 2048|
|hassas bilgi türü başına en fazla farklı kayıt değeri sayısı| 20|
|anahtar sözcük sözlüğünün en büyük boyutu (sıkıştırma sonrası)| 1 MB (~1.000.000 karakter)|
|kiracıda HT'leri temel alan anahtar sözcük sözlüğü sayısı üst sayısı|50 |

> [!NOTE] 
> İşletmeniz için 500'den fazla özel SIT oluşturmanız gerekirse lütfen destek bileti yükseltin.

### <a name="instance-count-supported-values-for-sit"></a>SIT için örnek sayısı desteklenen değerler

ŞU çözümlerde SITS'ler kullanılırken SIT örneği sayısı sınırı geçerlidir:

- DLP ilkeleri
- Bilgi Koruması
- Bilgi Yönetimi
- İletişim Uyumluluğu
- Kayıt Yönetimi
- Bulut Uygulamaları için Microsoft Defender
- Microsoft Priva

Kural ölçütlerini karşılayan taranan bir öğe için, tek bir öğede SIT'in benzersiz örneklerinin sayısı en küçük ve en yüksek değer arasında olmalıdır. Buna Örnek sayısı **denir**.

- **Min** alanı: Eşleşmeyi tetiklemek için bir öğede bulunan benzersiz SIT örneklerinin alt sınırı (en küçük sayı). En küçük alan şunların değerlerini destekler:
    - 1-500 arasında
- **En** Büyük alan: Bir öğede bulunan ve yine de eşleşmeyi tetikleyen sit'in benzersiz örneklerinin sayısında üst sınır. En büyük alan şunların değerlerini destekler:
    - 1 - 500 arasında - Bir öğede SIT'in tekrar sayısına göre 500 veya daha az belirli bir üst sınır ayarlamak için bunu kullanın.
    - Herhangi - `Any` Sit'in tanımlanmamış sayıda benzersiz örneği taranmış bir öğede bulunursa ve bu sayıda benzersiz örnek, en az sayıda benzersiz örnek değerine uyan veya bunu aştıdığında benzersiz örnek sayısı ölçütlerinin karşılandırılacağı durumlarda kullanın. Başka bir deyişle, en küçük değer karşılandı sürece benzersiz örnek sayısı ölçütleri karşılandı.

Örneğin, tek bir öğede SIT'in en az 500 benzersiz örneği bulunurken kuralın bir eşleşmeyi tetiklemesine izin vermek için,  `500` en küçük değeri ve en büyük değeri olarak ayarlayın. `Any`

> [!NOTE]
> Microsoft 365 Koruması aşağıdakiler için çift byte karakter kümesi dillerini destekler:
> - Çince (basitleştirilmiş)
> - Çince (geleneksel)
> - Korean
> - Japanese
>
>Bu destek, hassas bilgi türlerinde kullanılabilir. Daha fazla [bilgi için çift byte karakter kümesi sürüm notları (önizleme) için Bilgi koruma](mip-dbcs-relnotes.md) desteği'ne bakın.

> [!TIP]
> Çince/Japonca karakterler ve tek bir byte karakteri içeren desenleri algılamak veya Çince/Japonca ve İngilizce dillerini içeren desenleri algılamak için anahtar sözcüğün veya regex'in iki çeşitleni tanımlayın. 
> - Örneğin, "机密的document" gibi bir anahtar sözcüğü algılamak için, anahtar sözcüğün iki çeşitleni kullanın; Japonca ve İngilizce metin arasında boşluk olmayan ve Japonca ve İngilizce metinler arasında boşluk olmayan bir metin. Dolayısıyla SIT'e eklenecek anahtar sözcükler "机密的 belgesi" ve "机密的document" olabilir. Benzer şekilde, "東京オリンピック2020" tümceciği algılamak için iki değişken kullanılmalıdır: "東京オリンピック 2020" ve "東京オリンピック2020".
>
> Anahtar sözcükler/tümcecikler listesi Çince/Japonca sözcükler de (yalnızca İngilizce gibi) içeriyorsa, Çince/Japonca/çift byte karakterleriyle birlikte, iki sözlük/anahtar sözcük listesi oluşturmanız önerilir. Çince/Japonca/çift byte karakter içeren anahtar sözcükler için bir tane ve yalnızca İngilizce için bir tane daha. 
> - Örneğin, "Çok gizli", "機密性が高い" ve "机密的document" ifadelerini içeren bir anahtar sözcük sözlüğü/listesi oluşturmak için iki anahtar sözcük listesi oluşturmanız gerekir. 
>     1. Çok gizli
>     2. 機密性が高い, 机密的document ve 机密的 belgesi
>
> Çift bayt kısa çizgi veya çift byte dönemi kullanarak bir kayıtex oluşturulurken, bir kayıtex içinde bir kısa çizgi veya nokta gibi iki karakterin de kaçışta olduğundan emin olun. Başvuru için örnek bir kayıtex:
>    - (?<!\d) ([4][0-9]{3} [\-?\-\t]*[0-9]{4})
>
> Anahtar sözcük listesinde sözcük eşleşmesi yerine dize eşleşmesi kullanılması önerilir.
