---
title: Adlandırılmış varlıklar (önizleme) hakkında bilgi
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
localization_priority: Normal
ms.collection:
- M365-security-compliance
description: Adlandırılmış varlıkların, veri kaybı önleme ilkeleri aracılığıyla kişi adları, fiziksel adresler ve tıbbi terimler içeren hassas öğeleri algılamanıza nasıl yardımcı olduğunu öğrenin
ms.openlocfilehash: 002905264d789e7ebe0b163a80fe033c028a6b4b
ms.sourcegitcommit: 1ef176c79a0e6dbb51834fe30807409d4e94847c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/19/2021
ms.locfileid: "63006318"
---
# <a name="learn-about-named-entities-preview"></a>Adlandırılmış varlıklar (önizleme) hakkında bilgi

> [!IMPORTANT]
> Adlandırılmış varlıklar özelliği sunulmaktadır ve sizin için kullanılabilir olduğunda kiracıda görünür. İçerik gezgininde ve veri kaybı önleme (DLP) ilkesi yazma akışında bunları kontrol edin. 

*Adlandırılmış varlıklar hassas* [bilgi türleridir](sensitive-information-type-learn-about.md) (SIT). Bunlar, kişi adlarını, fiziksel adresleri, tıbbi hüküm ve koşulları algılamak için kullanabileceğiniz karmaşık sözlük ve desen tabanlı sınıflayıcılardır. Bunları Uyumluluk Merkezi'nde veya **Veri sınıflandırması > Hassas > türlerinde görebilirler**. SiTS'leri kullanabileceğiniz yerlerin kısmi bir listesi:

- [Veri kaybı önleme ilkeleri (DLP)](dlp-learn-about-dlp.md) 
- [Duyarlılık etiketleri](sensitivity-labels.md)
- [Insider risk yönetimi](insider-risk-management-solution-overview.md)
- [Bulut Uygulamaları için Microsoft Defender](/cloud-app-security/what-is-cloud-app-security)

DLP, yapılandırılmış ve kuruluşlarınız için özelleştirebileceğiniz önceden yapılandırılmış DLP ilkeleri olan gelişmiş ilke şablonlarında adlandırılmış varlıkları özel olarak kullanır. Ayrıca, boş [bir şablondan kendi DLP](create-test-tune-dlp-policy.md) ilkelerinizi [oluşturabilir ve](create-a-dlp-policy-from-a-template.md) koşul olarak adlandırılmış bir varlık SIT kullanabilirsiniz.

<!-- There are many other SITs that detect strings like social security, credit card, or bank account numbers to identify sensitive items. For more information, see [Sensitive information types entity definitions](sensitive-information-type-entity-definitions.md).-->



## <a name="examples-of-named-entity-sits"></a>Adlandırılmış varlık SI'leri örnekleri

Adlandırılmış varlık SITS'leri iki çeşittir; *paketli* *ve şaşırtıcı değil*

Paketli adlandırılmış varlık SIT'leri tüm olası eşleşmeleri algılar. Hassas öğeleri algılamak için DLP ilkeleriniz içinde bunları geniş ölçüt olarak kullanın.

Tek bir ülke gibi, şaşırtıcı olmayan adlandırılmış varlık SITS'leri daha dar bir odak noktası sağlar. Daha dar algılama kapsamına sahip bir DLP ilkesine ihtiyacınız olduğunda bunları kullanın.
 
Adlandırılmış varlık SIT'lerinden bazı örnekler aşağıda verilmiştir. Bunların 52'lerinin hepsini Uyumluluk Merkezi'nde bulabilirsiniz **> Sınıflandırması > bilgi türleri olabilir**.

|Adlandırılmış Varlık |Açıklama  |Paketli/İşsiz  |
|---------|---------|---------|
|Tüm tam adlar    |tam adların tüm olası eşleşmelerini algılar         |   paketli      |
|Tüm fiziksel adresler    |fiziksel adreslerin tüm olası eşleşmelerini algılar     | paketli |
|Tüm tıbbi hüküm ve koşullar    |sağlık hüküm ve koşullarının tüm olası eşleşmelerini algıla |paketli |
|Avustralya Fiziksel Adresleri |  Avustralya'dan gelen fiziksel adreslerle ilgili desenleri algılar. |undled |
|Kan Testi Koşulları     |Kan testleri ile ilgili 'hCG' gibi terimleri algılar. Yalnızca İngilizce terimler.      |undled |
|Marka ilaç adları     |Ilaç markalarının adlarını algılar, örneğin 'Tylenol'. Yalnızca İngilizce terimler.         |undled |

## <a name="examples-of-enhanced-dlp-policies"></a>Gelişmiş DLP ilkeleri örnekleri

Burada, adlandırılmış varlık SITS'leri kullanan gelişmiş DLP ilkelerine bazı örnekler verilmiştir. Bunların 10'larını Uyumluluk Merkezi'nde bulabilir, **> engellemeyi veya İlke > edinebilirsiniz**. Geliştirilmiş şablonlar DLP'de ve otomatik etiketlemede kullanılabilir.

|İlke kategorisi  |Şablon  |Açıklama  |
|---------|---------|---------|
|Finansal|U.S. Gramm-Leach-Bliley Act (GLBA) Enhanced         |Sosyal güvenlik numaraları veya kredi kartı numaraları gibi bilgiler de dahil olmak üzere Gramm-Leach-Bliley Yasası'nın (GLBA) tabi olduğu bilgilerin varlığını algılamaya yardımcı olur. Bu iyileştirilmiş şablon, abd/birleşik posta gibi tüm adları algılayan özgün şablonu genişlettir. Pasaport numarası, ABD ehliyeti ve ABD fiziksel adresleri.         |
| Sağlık ve sağlık   |Avustralya Sağlık Kayıtları Yasası (HRIP Yasası) Geliştirilmiş         |Yaygın olarak Sağlık Kayıtları ve Bilgi Gizliliği (HRIP) tarafından Avustralya'da tıbbi hesap numarası ve vergi dosyası numarası gibi işlemlere tabi kabul edilen bilgilerin varlığını algılamaya yardımcı olur. Bu iyileştirilmiş şablon, aynı zamanda kişilerin tam adlarını, tıbbi hüküm ve koşullarını ve Avustralya fiziksel adreslerini algılayan özgün şablonu genişlettir.         |
|Gizlilik   |Gelişmiş Genel Veri Koruma Yönetmeliği (GDPR)         | GDPR gizlilik yükümlülüklerini karşılamaya yardımcı olmak için Avrupa Birliği (AB) içindeki kişilerin kişisel bilgilerin varlığını algılamaya yardımcı olur. Gelişmiş bu şablon, AB'nin ülkelerdeki kişilerin tam adlarını ve fiziksel adreslerini algılar.        |


## <a name="next-steps"></a>Sonraki adımlar

- [Veri kaybı önleme ilkelerinize adlandırılmış varlıkları kullanma (önizleme)](named-entities-use.md)


## <a name="for-further-information"></a>Daha fazla bilgi için
<!--- [Sensitive information type entity definitions](sensitive-information-type-entity-definitions.md)-->
- [Hassas bilgi türleri hakkında bilgi](sensitive-information-type-learn-about.md)
- [Özel hassas bilgi türü oluşturma](create-a-custom-sensitive-information-type.md)
- [PowerShell'de özel duyarlı bilgi türü oluşturma](create-a-custom-sensitive-information-type-in-scc-powershell.md)
- [Veri kaybı önleme ilkeleri (DLP)](data-loss-prevention-policies.md) 
- [Duyarlılık etiketleri](sensitivity-labels.md)
- [Bekletme etiketleri](retention.md)
- [İletişim uyumluluğu](communication-compliance.md)
- [Otomatik etiket ilkeleri](apply-sensitivity-label-automatically.md#how-to-configure-auto-labeling-for-office-apps)
- [DLP ilkesi oluşturma, sınama ve ayarlama](create-test-tune-dlp-policy.md)
- [Şablondan DLP ilkesi oluşturma](create-a-dlp-policy-from-a-template.md) 
