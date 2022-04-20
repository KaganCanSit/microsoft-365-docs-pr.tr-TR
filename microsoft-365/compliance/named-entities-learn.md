---
title: Adlandırılmış varlıklar hakkında bilgi edinin
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
description: Adlandırılmış varlıkların, veri kaybı önleme ilkeleri aracılığıyla kişi adlarını, fiziksel adresleri ve tıbbi terimleri içeren hassas öğeleri algılamanıza nasıl yardımcı olduğunu öğrenin
ms.openlocfilehash: 6c20932216953d64abe4515b529bba66b2561647
ms.sourcegitcommit: 45bc65972d4007b2aa7760d4457a0d2699f81926
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/20/2022
ms.locfileid: "64973211"
---
# <a name="learn-about-named-entities"></a>Adlandırılmış varlıklar hakkında bilgi edinin

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

*Adlandırılmış varlıklar* [hassas bilgi türleridir](sensitive-information-type-learn-about.md) (SIT). Bunlar kişi adlarını, fiziksel adresleri ve tıbbi hüküm ve koşulları algılamak için kullanabileceğiniz karmaşık sözlük ve desen tabanlı sınıflandırıcılardır. Bunları **Microsoft Purview uyumluluk portalında > Veri sınıflandırma > Hassas bilgi türlerinde** görebilirsiniz. BURADA, SID'leri kullanabileceğiniz kısmi bir liste yer alıyor:


- [Microsoft Purview Veri Kaybı Önleme ilkeleri (DLP)](dlp-learn-about-dlp.md) 
- [Duyarlılık etiketleri](sensitivity-labels.md)
- [İçeriden risk yönetimi](insider-risk-management-solution-overview.md)
- [Bulut Uygulamaları için Microsoft Defender](/cloud-app-security/what-is-cloud-app-security)
- [Microsoft Purview Information Protection](apply-sensitivity-label-automatically.md)
- [Veri Yaşam Döngüsü Yönetimi](information-governance.md)
- [Kayıt yönetimi](records-management.md)
- [Microsoft Purview eKeşif](ediscovery.md)
- [Microsoft Priva](/privacy/priva/priva-overview.md)
- [Hassas bilgi türleriyle tam olarak eşleşen veriler](sit-learn-about-exact-data-match-based-sits.md)

DLP, kuruluşunuzun ihtiyaçlarına göre özelleştirebileceğiniz önceden yapılandırılmış DLP ilkeleri olan *gelişmiş ilke şablonlarında* adlandırılmış varlıkları özel olarak kullanır. Ayrıca [boş bir şablondan](create-a-dlp-policy-from-a-template.md) [kendi DLP ilkelerinizi oluşturabilir](create-test-tune-dlp-policy.md) ve koşul olarak adlandırılmış bir varlık SIT kullanabilirsiniz.

<!-- There are many other SITs that detect strings like social security, credit card, or bank account numbers to identify sensitive items. For more information, see [Sensitive information types entity definitions](sensitive-information-type-entity-definitions.md).-->



## <a name="examples-of-named-entity-sits"></a>Adlandırılmış varlık SID örnekleri

Adlandırılmış varlık SID'leri *paketlenmiş* ve *sarmalanmamış* iki farklı türde gelir

Paketlenmiş adlandırılmış varlık SID'leri tüm olası eşleşmeleri algılar. Bunları, hassas öğeleri algılamak için DLP ilkelerinizde geniş ölçütler olarak kullanın.

Unbundled adlandırılmış varlık SID'leri, tek bir ülke gibi daha dar bir odak noktası içerir. Daha dar bir algılama kapsamına sahip bir DLP ilkesine ihtiyacınız olduğunda bunları kullanın.
 
Burada adlandırılmış varlık SID'lerine bazı örnekler verilmiştir. Bunların tümünü [Hassas bilgi türü varlık tanımlarında](sensitive-information-type-entity-definitions.md) bulabilirsiniz.

|Adlandırılmış Varlık |Açıklama  |Paketlenmiş/Sarmalanmamış  |
|---------|---------|---------|
|Tüm tam adlar    |tam adların tüm olası eşleşmelerini algılar         |   Birlikte      |
|Tüm fiziksel adresler    |fiziksel adreslerin tüm olası eşleşmelerini algılar     | Birlikte |
|Tüm tıbbi hüküm ve koşullar    |tıbbi hüküm ve koşulların tüm olası eşleşmelerini algılar |Birlikte |
|Avustralya Fiziksel Adresleri |  Avustralya'dan gelen fiziksel adreslerle ilgili desenleri algılar. Tüm fiziksel adresler SIT'e dahildir. |unbundled |
|Kan Testi Koşulları     |'hCG' gibi kan testleriyle ilgili terimleri algılar. Yalnızca İngilizce terimler. Tüm tıbbi hüküm ve koşullara dahil sit      |unbundled |
|Marka İlaç Adları     |'Tylenol' gibi marka ilacı adlarını algılar. Yalnızca İngilizce terimler. Tüm tıbbi hüküm ve koşullara dahil edilmiştir.         |unbundled |

## <a name="examples-of-enhanced-dlp-policies"></a>Gelişmiş DLP ilkeleri örnekleri

Burada adlandırılmış varlık SID'lerini kullanan gelişmiş DLP ilkelerine bazı örnekler verilmiştir. Bunların 10'unu **Microsoft Purview uyumluluk portalında > Veri kaybını önleme > İlke oluştur'da** bulabilirsiniz. Gelişmiş şablonlar DLP ve otomatik etiketlemede kullanılabilir.

|İlke kategorisi  |Şablon  |Açıklama  |
|---------|---------|---------|
|Finansal|U.S. Gramm-Leach-Bliley Act (GLBA) Enhanced         |Sosyal güvenlik numaraları veya kredi kartı numaraları gibi bilgiler de dahil olmak üzere Gramm-Leach-Bliley Yasası'na (GLBA) tabi bilgilerin varlığını algılamaya yardımcı olur. Bu gelişmiş şablon, kişilerin tam adlarını (ABD/Birleşik Krallık) algılayarak özgün şablonu genişletir. pasaport numarası, ABD ehliyet numarası ve ABD fiziksel adresleri.         |
| Tıbbi ve sağlık   |Avustralya Sağlık Kayıtları Yasası (HRIP Yasası) Geliştirildi         |Avustralya'da sağlık hesabı numarası ve vergi dosya numarası gibi Sağlık Kayıtları ve Bilgi Gizliliği (HRIP) eylemine tabi olarak kabul edilen bilgilerin varlığını algılamaya yardımcı olur. Bu gelişmiş şablon, kişilerin tam adlarını, tıbbi hüküm ve koşullarını ve Avustralya fiziksel adreslerini de algılayarak orijinali genişletir.         |
|Gizlilik   |Genel Veri Koruma Yönetmeliği (GDPR) Geliştirildi         | GDPR gizlilik yükümlülüklerini karşılamaya yardımcı olmak için Avrupa Birliği (AB) içindeki bireyler için kişisel bilgilerin varlığını algılamaya yardımcı olur. Bu gelişmiş şablon, AB'deki ülkeler için kişilerin tam adlarını ve fiziksel adreslerini algılar.        |


## <a name="next-steps"></a>Sonraki adımlar

- [Veri kaybı önleme ilkelerinizde adlandırılmış varlıkları kullanma](named-entities-use.md)


## <a name="for-further-information"></a>Daha fazla bilgi için

- [Hassas bilgi türü varlık tanımları](sensitive-information-type-entity-definitions.md)
- [Hassas bilgi türleri hakkında bilgi edinin](sensitive-information-type-learn-about.md)
- [Özel hassas bilgi türü oluşturma](create-a-custom-sensitive-information-type.md)
- [PowerShell'de özel hassas bilgi türü oluşturma](create-a-custom-sensitive-information-type-in-scc-powershell.md)
- [Veri kaybı önleme ilkeleri (DLP)](data-loss-prevention-policies.md) 
- [Duyarlılık etiketleri](sensitivity-labels.md)
- [Bekletme etiketleri](retention.md)
- [İletişim uyumluluğu](communication-compliance.md)
- [Otomatik etiketleme ilkeleri](apply-sensitivity-label-automatically.md#how-to-configure-auto-labeling-for-office-apps)
- [Bir DLP ilkesi oluşturma, test etme ve ayarlama](create-test-tune-dlp-policy.md)
- [Bir şablondan DLP ilkesi oluşturma](create-a-dlp-policy-from-a-template.md) 
