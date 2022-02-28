---
title: Veri gizliliği düzenlemeye tabi olan bilgileri yönetme
ms.author: bcarter
author: brendacarter
f1.keywords:
- NOCSH
manager: laurawi
ms.date: 06/09/2020
audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- Strat_O365_Enterprise
- m365solution-infoprotection
- m365solution-scenario
ms.custom: ''
description: Kendi Microsoft 365 kişisel verileri yönetmek için bekletme etiketlerini ve Microsoft 365 kullanın.
ms.openlocfilehash: b131c90e83a2ce211d51af444dd570f71f3b8263
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62984430"
---
# <a name="govern-information-subject-to-data-privacy-regulation"></a>Veri gizliliği düzenlemeye tabi olan bilgileri yönetme

Bilgi yönetimi denetimleri ortamınıza, Genel Veri Koruma Yönetmeliği (GDPR), HIPAA-HITECH (ABD sağlık bakımı gizlilik yasası), California Tüketici Koruma Yasası (CCPA) ve Brezilya Veri Koruma Yasası (LGPD) gibi özel bir sayıyla birlikte, veri gizliliği uyumluluk 2013'e yardımcı olmak üzere yer değiştirebilir. 

Bu denetimler öncelikle aşağıdaki çözüm alanlarına girmektedir:

- Bekletme ilkeleri
- Bekletme etiketleri
- Kayıt yönetimi

## <a name="data-privacy-regulations-impacting-information-governance-controls"></a>Bilgi yönetimi denetimlerini etkileyen veri gizliliği düzenlemeleri

Aşağıda, bilgi idaresi denetimleriyle ilgili olacak veri gizliliği düzenlemelerinin örnek bir listesi ve ve vemektedir:

- GDPR Makalesi (13)(2)(a)
- GDPR Makalesi (5)(1)(f)
- HIPAA-HITECH (45 CFR 164.312(c)(2))
- HIPAA-HITECH (45 CFR 164.316(b)(1)(i))
- HIPAA-HITECH (45 CFR 164.316(b)(1)(ii))
- LGPD Makale 46

Bu düzenlemeler hakkında daha fazla bilgi için veri gizlilik [risklerini değerlendirme ve hassas bilgileri belirleme makalesine bakın](information-protection-deploy-assess.md).

Bilgi idaresi için veri gizlilik düzenlemeleri genellikle şunları arar:

- Farklı bir düzende depolanan kişisel verilerin elde tutulması ve silinmesi için teknik bir düzen Microsoft 365.
- Kişisel verileri depoacaksanız verilerin ne kadar süreyle depolandığı konusunda bilgi edinebilirsiniz. Bu, şimdi ön uç web sistemlerinde standart bir uygulamadır.
- Kişisel veriler, doğrulanabilir yöntemler kullanılarak yanlışlıkla işleme, kayıp veya değişiklik durumlarına karşı korumalıdır.
- Kişisel veriler üzerinde  yürütülen her türlü eylemin belgelenmiş olması ve belgelerin belirtilen süre boyunca muhafaza edilmiş olması gerekir.

Veri gizliliği düzenlemeleri veri bekletme ve silme gibi konulara çok açık olduğundan, Microsoft 365 aboneliğinde depolanan kişisel bilgiler için bilgi yönetimi yönergelerini dikte ediyor olması gereken başka etmenler de dikkate alınmalıdır. İşte birkaç örnek:

- 5 yıllık işlem dışı kalmanın ardından tüketici hesaplarının eskitilmesi ve bu noktadan sonra hesap verilerinin silinmesi veya anonimleştirilmesi gerekir; bu da sistemin bildirimler ve diğer otomasyonlarla ilgili verileri ve iş akışlarını depolaması arasında ayrım yapmak gerektirir.
- GDPR ile ilgili ilkeleri ve yordamları üç yıl boyunca tutmak için kuralların yapılandırılması, bunların yerine konduktan sonra, ilkeleri ve yordamları kuruluşun bekletme zamanlamasıyla uyumlu olur.
- Destek kuruluşu aracılığıyla tüketicilerle iletişim kurmak için ayrı bir aboneliği koruma. Sistemle ilgili gizlilik kalıcı derlemelerini azaltmak için, tüm e-posta iletişimi iki hafta sonra korunur ve silinir.

Yanıt verecek önemli bir soru: 

- Kişisel verileri içeren bilgilerin "sonsuza kadar tutma" uygulamalarından kaçınmak için, geçerli iş nedenleriyle ne kadar süreyle tutulması gerekir? Bu, iş sürekliliği için bekletme ihtiyaçlarıyla dengelenmeli.

Kişisel bilgilerinizi korumanın veya silmenin yasal ve ticari nedenlerinden bağımsız olarak, Microsoft kurumsal yönetim düzeninizi başka kullanıcılarla birlikte uygulamak için Microsoft 365.

## <a name="managing-information-governance-in-microsoft-365"></a>E-Microsoft 365'de bilgi idaresi Microsoft 365

Başlamak için bkz. [Yeni Yönetimde bilgi idaresi](../compliance/manage-information-governance.md) [ve Veri Bekletme, Silme ve Microsoft 365](/office365/Enterprise/office-365-data-retention-deletion-and-destruction-overview).

### <a name="develop-data-retention-schedules-for-containers-email-and-content"></a>Kapsayıcılar, e-posta ve içerik için veri bekletme zamanlamaları geliştirme

Şunları unutmayın:

- Tanımlanmış bilgi türleri için veri bekletme zamanlaması oluşturma, herhangi bir bekletme veya silme düzenini uygulamanın önkoşulları olarak kabul edilir.

- Çoğu kuruluşun önemli dikkate alan bilgi türleri ve buna karşılık gelen büyük kayıt bekletme zamanlamalarının sayısı göz önünde tutularak, veri bekletme ve kayıt yönetim stratejisini uygulamak planlamayı gerektirir. 

- Bu tür için etkili bir veri yönetim stratejisi kurmanın en önemli noktası, daha resmi bir yönetim gerektiren en yüksek öncelikli iş işlevlerine ve bilgi türlerine odaklanmaktır. Örnek olarak yasal sözleşmeler, mali açıklamalar ve mevzuat uyumluluğu belgeleri örnek olarak verilmiştir. Her tek bilgi türü için ayrı bir bekletme zamanlaması elde etmek zorunda kalmamaya çalış. Genel iş içeriği için 7 yıllık bekletme zamanlamaları gibi, mümkün olduğunca genel kategorileri deneyin.

- Ortamınıza kişisel bilgi türleri daha iyi tanındıktan sonra, bu tür içerik için bekletme ve silme zamanlamaları ayarlayın ve bu tür bilgilerin daha kolay idaresi için bilgi mimarinizi ayarlayın. Örneğin, kişisel bilgileri denetimli erişimle ayrı sitelerde, kitaplıklarda veya klasörlerde yalıtabilirsiniz.

### <a name="retention-policies-and-retention-labels"></a>Bekletme ilkeleri ve bekletme etiketleri

Kişisel [veri içeren veya içermesi](../compliance/retention.md) beklenen bir çalışma Microsoft 365 içeriği tutmak veya silmek için bekletme ilkelerini ve bekletme etiketlerini kullanın.

### <a name="records-management"></a>Kayıt yönetimi

Kayıt yönetiminde veriler için kayıt yönetimi çözümü uygulamak üzere [kayıt bildiren](../compliance/records-management.md) bekletme Microsoft 365.

Veri gizliliği için, hukuk departmanı tarafından alınan veri konusu istekleri (DSR) kayıt olarak beyan edilebilir ve yasal düzenleme etkinliği saklama belirtimlerine uyması için süresiz olarak depo edilebilir veya kanıt ile at edilebilir.