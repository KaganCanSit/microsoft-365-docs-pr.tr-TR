---
title: Veri gizliliği düzenlemesine tabi olan bilgileri idare etme
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
description: Microsoft 365 ortamınızdaki kişisel verileri yönetmek için Microsoft 365 bekletme etiketlerini ve ilkelerini kullanın.
ms.openlocfilehash: 05aad5b26f65dc66543afb29834e7cc4514e3366
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/19/2022
ms.locfileid: "64947395"
---
# <a name="govern-information-subject-to-data-privacy-regulation"></a>Veri gizliliği düzenlemesine tabi olan bilgileri idare etme

Genel Veri Koruma Yönetmeliği (GDPR), HIPAA-HITECH (Birleşik Devletler sağlık hizmetleri gizlilik yasası), California Tüketici Koruma Yasası (CCPA) ve Brezilya Veri Koruma Yasası (LGPD) gibi veri gizliliği uyumluluk gereksinimlerini karşılamaya yardımcı olmak için ortamınızda bilgi idare denetimleri kullanılabilir. 

Bu denetimler öncelikli olarak aşağıdaki çözüm alanlarına girer:

- Bekletme ilkeleri
- Bekletme etiketleri
- Kayıt yönetimi

## <a name="data-privacy-regulations-impacting-information-governance-controls"></a>Bilgi idare denetimlerini etkileyen veri gizliliği düzenlemeleri

Bilgi idaresi denetimleriyle ilgili olabilecek veri gizliliği düzenlemelerinin örnek bir listesi aşağıda verilmiştir:

- GDPR Makalesi (13)(2)(a)
- GDPR Makalesi (5)(1)(f)
- HIPAA-HITECH (45 CFR 164.312(c)(2))
- HIPAA-HITECH (45 CFR 164.316(b)(1)(i))
- HIPAA-HITECH (45 CFR 164.316(b)(1)(ii))
- LGPD Makale 46

Bu düzenlemeler hakkında daha fazla bilgi için [veri gizliliği risklerini değerlendirme ve hassas bilgileri tanımlama makalesine bakın](information-protection-deploy-assess.md).

Bilgi idaresi için veri gizliliği düzenlemeleri genellikle aşağıdakileri çağırır:

- Microsoft 365'de depolanan kişisel veriler için saklama ve silme için teknik bir şema kullanmanız gerekir.
- Kişisel verileri depolayacaksanız, ön uç web sistemlerinde standart bir uygulama olan verilerin ne kadar süreyle depolanacağı konusunda konuyu bilgilendirin.
- Kişisel veriler doğrulanabilir yöntemler kullanılarak yanlışlıkla işlemeye, kaybolmaya veya değiştirilmeye karşı korunmalıdır.
- Kişisel verilere karşı yürütülen tüm eylemler belgelenmeli ve bu belgeler belirli bir süre boyunca saklanmalıdır.

Veri saklama ve silme söz konusu olduğunda veri gizliliği düzenlemeleri çok özel olmadığından, Microsoft 365 aboneliğinizde depolanan kişisel bilgiler için bilgi idaresi yönergelerini dikte eden diğer faktörlerin dikkate alınması gerekir. Aşağıda birkaç örnek verilmiştir:

- 5 yıllık işlem yapılmadıktan sonra tüketici hesaplarının eskimesi ve bu noktadan sonra hesap verilerinin silinmesini veya anonimleştirilmesini gerektirir, bu nedenle verileri depolayan sistem ile bildirimler ve diğer otomasyonla ilgili iş akışları arasında düzenleme yapılmasını gerektirir.
- GDPR ile ilgili ilkelerin ve yordamların yerini aldıktan yaklaşık üç yıl sonra tutulmasına yönelik kurallar yapılandırılır ve bu da kuruluşun ilkeler ve yordamlar için bekletme zamanlaması ile uyumludur.
- Destek kuruluşu aracılığıyla tüketicilerle iletişim kurmak için ayrı bir abonelik tutma. Sistemdeki gizlilik borcu birikmesini azaltmak için tüm e-posta iletişimleri iki hafta sonra tutuldu ve silindi.

Yanıtlaması gereken önemli bir soru: 

- "Sonsuza kadar saklama" uygulamalarından kaçınmak için kişisel verileri içeren bilgilerin geçerli iş nedenleriyle ne kadar süreyle saklanması gerekiyor? Bu, iş sürekliliği için bekletme gereksinimleriyle dengelenmelidir.

Microsoft, kişisel bilgileri saklamanın veya silmenin yasal nedenlerinden ve iş nedenlerinden bağımsız olarak, Microsoft 365'da veri idare şemanızı uygulamaya yönelik bir dizi özellik sağlar.

## <a name="managing-information-governance-in-microsoft-365"></a>Microsoft 365'de bilgi idaresini yönetme

Başlamak için bkz[. Microsoft 365'de Verilerinizi Microsoft Purview](../compliance/manage-data-governance.md) ve [Veri Saklama, Silme ve Yok Etme](/office365/Enterprise/office-365-data-retention-deletion-and-destruction-overview) ile yönetme.

### <a name="develop-data-retention-schedules-for-containers-email-and-content"></a>Kapsayıcılar, e-posta ve içerik için veri saklama zamanlamaları geliştirme

Aşağıdakileri unutmayın:

- Tanımlı bilgi türleri için bir veri saklama zamanlaması oluşturmak, bekletme veya silme düzenini uygulamak için önkoşul olarak kabul edilmelidir.

- Çoğu kuruluşun önemli kabul ettiğiniz bilgi türü sayısı ve bunlara karşılık gelen büyük kayıt saklama zamanlamaları dikkate alındığında, bir veri saklama ve kayıt yönetimi stratejisinin uygulanması planlama gerektirir. 

- Bu tür etkili bir veri idare stratejisi oluşturmanın anahtarı, daha resmi yönetim gerektiren en yüksek öncelikli iş işlevlerine ve bilgi türlerine odaklanmaktır. Yasal sözleşmeler, finansal tablolar ve mevzuat uyumluluğu belgeleri buna örnek olarak verilebilir. Her bir bilgi türü için ayrı bir bekletme zamanlaması olmasını önlemeye çalışın. Genel kategorileri mümkün olduğunca kullanmayı deneyin, örneğin, genel iş içeriği için 7 yıllık bekletme zamanlamaları.

- Ortamınızdaki kişisel bilgi türleri daha iyi biliniyorsa, bu tür içerikler için saklama ve silme zamanlamaları oluşturun ve bu tür bilgilerin idaresini kolaylaştırmak için bilgi mimarinizi ayarlayın. Örneğin, kişisel bilgileri ayrı sitelerde, kitaplıklarda veya klasörlerde denetimli erişimle yalıtabilirsiniz.

### <a name="retention-policies-and-retention-labels"></a>Bekletme ilkeleri ve bekletme etiketleri

Kişisel verileri içeren veya içermesi beklenen içeriği Microsoft 365 tutmak veya silmek için [bekletme ilkelerini ve bekletme etiketlerini](../compliance/retention.md) kullanın.

### <a name="records-management"></a>Kayıt yönetimi

Microsoft 365'deki veriler için kayıt [yönetimi çözümü](../compliance/records-management.md) uygulamak üzere içeriği kayıt olarak bildiren bekletme etiketlerini kullanın.

Veri gizliliği için, hukuk departmanı tarafından alınan veri sahibi istekleri (DSR) kayıt olarak bildirilir ve mevzuat etkinliği saklama belirtimlerine uymak için süresiz olarak depolanabilir veya kanıt ile atılabilir.