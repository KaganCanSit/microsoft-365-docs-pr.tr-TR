---
title: Microsoft Purview Denetimi (Premium)
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- SPO_Content
- m365solution-audit
- m365initiative-compliance
search.appverid:
- MOE150
- MET150
description: Microsoft Purview Audit (Premium), kuruluşunuzun adli ve uyumluluk araştırmalarına yardımcı olmak için yeni denetim özellikleri sağlar.
ms.openlocfilehash: 07a441557cacdbb92e9442370210b88d898ccd3b
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65099004"
---
# <a name="microsoft-purview-audit-premium"></a>Microsoft Purview Denetimi (Premium)

> [!TIP]
> *Dokuz Microsoft Purview çözümlerinin tamamının premium sürümlerini ücretsiz olarak deneyebileceğinizi biliyor muydunuz?* Sağlam Purview özelliklerinin kuruluşunuzun uyumluluk gereksinimlerini karşılamasına nasıl yardımcı olabileceğini keşfetmek için 90 günlük Purview çözümleri deneme sürümünü kullanın. Microsoft 365 E3 ve Office 365 E3 müşterileri artık [Microsoft Purview uyumluluk portalı deneme hub'ında](https://compliance.microsoft.com/trialHorizontalHub?sku=ComplianceE5&ref=DocsRef) başlayabilir. [Kaydolabilecek kişiler ve deneme koşulları](compliance-easy-trials.md) hakkında ayrıntılı bilgi edinin.

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Microsoft Purview'daki [Denetim işlevi](search-the-audit-log-in-security-and-compliance.md), kuruluşlara Microsoft 365'deki birçok farklı hizmette birçok denetim etkinliği türüne görünürlük sağlar. Microsoft Purview Denetimi (Premium), kuruluşların bir araştırma yürütmek için gereken denetim günlüğü saklama süresini artırarak, önemli olaylara erişim sağlayarak (Microsoft Purview uyumluluk portalında ve Office 365 Yönetim Etkinliği API'sinde Denetim günlüğü aramasını kullanarak) güvenlik ihlallerinin kapsamını belirlemeye ve daha hızlı erişim sağlayarak, kuruluşların adli ve uyumluluk araştırmaları gerçekleştirmesine yardımcı olur Office 365 Yönetim Etkinliği API'si.

> [!NOTE]
> Denetim (Premium), Office 365 E5/A5/G5 veya Microsoft 365 Kurumsal E5/A5/G5 aboneliği olan kuruluşlar için kullanılabilir. Microsoft 365 E5/A5/G5 Uyumluluğu veya E5/A5/G5 eBulma ve Denetim eklentisi lisansı, denetim günlüklerinin uzun süreli saklaması ve araştırma için Denetim (Premium) olaylarının oluşturulması gibi Denetim (Premium) özellikleri için kullanıcılara atanmalıdır. Lisanslama hakkında daha fazla bilgi için bkz:<br/>- [Denetim (Premium) lisans gereksinimleri](auditing-solutions-overview.md#licensing-requirements)<br/>- [Güvenlik & uyumluluğu için lisanslama yönergelerini Microsoft 365](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#advanced-audit).

Bu makalede Denetim (Premium) özelliklerine genel bir bakış sağlanır ve kullanıcıların Denetim (Premium) için nasıl ayarlanacağı gösterilir.

## <a name="long-term-retention-of-audit-logs"></a>Denetim günlüklerinin uzun süreli saklaması

Denetim (Premium), tüm Exchange, SharePoint ve Azure Active Directory denetim kayıtlarını bir yıl boyunca saklar. Bu, **workload** özelliği (etkinliğin gerçekleştiği hizmeti gösterir) için **Exchange**, **SharePoint** veya **AzureActiveDirectory** değerini içeren tüm denetim kayıtlarını bir yıl boyunca tutan varsayılan denetim günlüğü saklama ilkesi tarafından gerçekleştirilir. Denetim kayıtlarının daha uzun süre saklanması, devam eden adli veya uyumluluk araştırmalarına yardımcı olabilir. Daha fazla bilgi için Denetim [günlüğü saklama ilkelerini yönetme bölümündeki "Varsayılan denetim günlüğü saklama ilkesi](audit-log-retention-policies.md#default-audit-log-retention-policy)" bölümüne bakın.

Denetim 'in (Premium) bir yıllık saklama özelliklerine ek olarak, denetim günlüklerini 10 yıl boyunca saklama özelliğini de yayımladık. Denetim günlüklerinin 10 yıllık saklama süresi, uzun süre devam eden araştırmaları desteklemeye ve mevzuat, yasal ve iç yükümlülüklere yanıt vermeye yardımcı olur.

> [!NOTE]
> Denetim günlüklerinin 10 yıl boyunca korunması için kullanıcı başına ek bir eklenti lisansı gerekir. Bu lisans bir kullanıcıya atandıktan ve bu kullanıcı için uygun bir 10 yıllık denetim günlüğü saklama ilkesi ayarlandıktan sonra, bu ilkenin kapsadığı denetim günlükleri 10 yıllık süre boyunca korunmaya başlar. Bu ilke geriye dönük değildir ve 10 yıllık denetim günlüğü saklama ilkesi oluşturulmadan önce oluşturulan denetim günlüklerini tutamaz. Daha fazla bilgi için bu makaledeki [Denetim (Premium) hakkında SSS](#faqs-for-audit-premium) bölümüne bakın.

### <a name="audit-log-retention-policies"></a>Denetim günlüğü saklama ilkeleri

Diğer hizmetlerde oluşturulan ve varsayılan denetim günlüğü saklama ilkesi kapsamında olmayan tüm denetim kayıtları (önceki bölümde açıklanmıştır) 90 gün boyunca saklanır. Ancak, diğer denetim kayıtlarını 10 yıla kadar daha uzun süreler boyunca tutmak için özelleştirilmiş denetim günlüğü saklama ilkeleri oluşturabilirsiniz. Denetim kayıtlarını aşağıdaki ölçütlerden birine veya daha fazlasına göre tutmak için bir ilke oluşturabilirsiniz:

- Denetlenen etkinliklerin gerçekleştiği Microsoft 365 hizmeti.

- Belirli denetlenen etkinlikler.

- Denetlenen bir etkinlik gerçekleştiren kullanıcı.

Ayrıca, belirli ilkelerin diğer ilkelere göre öncelik alması için ilkeyle ve öncelik düzeyiyle eşleşen denetim kayıtlarının ne kadar süre tutulacağını da belirtebilirsiniz. Ayrıca, kuruluşunuzdaki kullanıcıların bir kısmı veya tamamı için Exchange denetim kayıtlarını bir yıldan (Azure Active Directory veya 10 yıldan) kısa süre boyunca saklamanız gerektiğinde SharePoint, özel denetim günlüğü saklama ilkelerinin varsayılan denetim saklama ilkesinden öncelikli olduğunu da unutmayın. Daha fazla bilgi için bkz. [Denetim günlüğü saklama ilkelerini yönetme](audit-log-retention-policies.md).

## <a name="audit-premium-events"></a>Denetim (Premium) olayları

Denetim (Premium), kuruluşların posta öğelerine ne zaman erişildiği, posta öğelerine ne zaman yanıtlandığı ve iletildiği ve kullanıcının Exchange Online ve SharePoint Online'da ne zaman ve ne zaman arama yaptığı gibi önemli olaylara erişim sağlayarak adli ve uyumluluk araştırmaları gerçekleştirmesine yardımcı olur. Bu olaylar olası ihlalleri araştırmanıza ve güvenliğin kapsamını belirlemenize yardımcı olabilir. Exchange ve SharePoint bu olaylara ek olarak, diğer Microsoft 365 hizmetlerinde önemli olaylar olarak kabul edilen ve kullanıcılara [uygun Denetim (Premium) lisansının](auditing-solutions-overview.md#licensing-requirements) atanmalarını gerektiren olaylar vardır. Kullanıcılar bu olayları gerçekleştirdiğinde denetim günlüklerinin oluşturulabilmesi için kullanıcılara bir Denetim (Premium) lisansı atanmalıdır.

Denetim (Premium) aşağıdaki olayları sağlar:

- [MailItemsAccessed](#mailitemsaccessed)

- [Gönderin](#send)

- [SearchQueryInitiatedExchange](#searchqueryinitiatedexchange)

- [SearchQueryInitiatedSharePoint](#searchqueryinitiatedsharepoint)

- [Microsoft 365'deki diğer Denetim (Premium) olayları](#other-audit-premium-events-in-microsoft-365)

### <a name="mailitemsaccessed"></a>MailItemsAccessed

MailItemsAccessed olayı bir posta kutusu denetim eylemidir ve posta verilerine posta protokolleri ve posta istemcileri tarafından erişildiğinde tetikler. Bu olay, araştırmacıların veri ihlallerini tanımlamalarına ve tehlikeye girmiş olabilecek iletilerin kapsamını belirlemelerine yardımcı olabilir. Bir saldırgan e-posta iletilerine erişim kazandıysa, iletilerin gerçekten okunduğunu belirten açık bir sinyal olmasa bile MailItemsAccessed eylemi tetiklenir (başka bir deyişle, bağlama veya eşitleme gibi erişim türü denetim kaydına kaydedilir).

MailItemsAccessed olayı, Exchange Online posta kutusu denetim günlüğündeki MessageBind'in yerini alır ve şu iyileştirmeleri sağlar:

- MessageBind yalnızca AuditAdmin kullanıcı oturum açma türü için yapılandırılabilirdi; temsilci veya sahip eylemleri için geçerli değildir. MailItemsAccessed tüm oturum açma türleri için geçerlidir.

- MessageBind yalnızca posta istemcisi tarafından kapsanan erişim. Eşitleme etkinlikleri için geçerli değildi. MailItemsAccessed olayları hem bağlama hem de eşitleme erişim türleri tarafından tetiklenir.

- MessageBind eylemleri, aynı e-posta iletisine erişildiğinde birden çok denetim kaydının oluşturulmasını tetikler ve bu da "kirlilik" denetiminin yapılmasına neden olur. Buna karşılık, MailItemsAccessed olayları daha az denetim kaydı halinde toplanır.

MailItemsAccessed etkinliklerinin denetim kayıtları hakkında bilgi için bkz. [Güvenliği aşılmış hesapları araştırmak için Denetimi (Premium) kullanma](mailitemsaccessed-forensics-investigations.md).

MailItemsAccessed denetim kayıtlarını aramak için, uyumluluk portalındaki [denetim günlüğü arama aracındaki](search-the-audit-log-in-security-and-compliance.md) **Exchange posta kutusu etkinlikleri** açılan listesinde **Erişilen** posta kutusu öğeleri etkinliğini arayabilirsiniz.

![Denetim günlüğü arama aracında MailItemsAccessed eylemlerini arama.](../media/AdvAudit_MailItemsAccessed.png)

Exchange Online PowerShell'de [Search-UnifiedAuditLog -Operations MailItemsAccessed](/powershell/module/exchange/search-unifiedauditlog) veya [Search-MailboxAuditLog -Operations MailItemsAccessed komutlarını](/powershell/module/exchange/search-mailboxauditlog) da çalıştırabilirsiniz.

### <a name="send"></a>Gönderin

Gönder olayı aynı zamanda bir posta kutusu denetim eylemidir ve kullanıcı aşağıdaki eylemlerden birini gerçekleştirdiğinde tetiklanır:

- E-posta iletisi gönderir

- E-posta iletisine yanıtlar

- E-posta iletisini iletir

Araştırmacılar, güvenliği aşılmış bir hesaptan gönderilen e-postaları tanımlamak için Gönder olayını kullanabilir. Gönderme olayının denetim kaydı, iletinin ne zaman gönderildiği, InternetMessage Kimliği, konu satırı ve iletinin ekler içerip içermediği gibi ileti hakkında bilgi içerir. Bu denetim bilgileri, araştırmacıların güvenliği aşılmış bir hesaptan gönderilen veya saldırgan tarafından gönderilen e-posta iletileri hakkındaki bilgileri tanımlamalarına yardımcı olabilir. Ayrıca araştırmacılar, iletinin gönderildiği alıcıları ve gönderilen iletinin gerçek içeriğini belirlemek üzere iletiyi aramak için (konu satırını veya ileti kimliğini kullanarak) Microsoft 365 eBulma aracını kullanabilir.

Denetim kayıtlarını gönder'i aramak için, uyumluluk portalındaki [denetim günlüğü arama aracındaki](search-the-audit-log-in-security-and-compliance.md) **Exchange posta kutusu etkinlikleri** açılan listesinde **Gönderilmiş ileti** etkinliğini arayabilirsiniz.

![Denetim günlüğü arama aracında Gönderilmiş ileti eylemleri aranıyor.](../media/AdvAudit_SentMessage.png)

PowerShell'de [Search-UnifiedAuditLog -Operations Send](/powershell/module/exchange/search-unifiedauditlog) veya [Search-MailboxAuditLog -Operations Send](/powershell/module/exchange/search-mailboxauditlog) komutlarını da Exchange Online çalıştırabilirsiniz.

### <a name="searchqueryinitiatedexchange"></a>SearchQueryInitiatedExchange

SearchQueryInitiatedExchange olayı, bir kişi posta kutusunda öğeleri aramak için Outlook kullandığında tetikleniyor. Aşağıdaki Outlook ortamlarında arama yapıldığında olaylar tetiklenir:

- Outlook (masaüstü istemcisi)

- Web üzerinde Outlook (OWA)

- iOS için Outlook

- Android için Outlook

- Windows 10 için posta uygulaması

Araştırmacılar SearchQueryInitiatedExchange olayını kullanarak bir hesabı ele geçiren bir saldırganın posta kutusunda hassas bilgileri arayıp aramadığını veya erişmeye çalışıp çalışmadığını belirleyebilir. SearchQueryInitiatedExchange olayının denetim kaydı, arama sorgusunun gerçek metni gibi bilgileri içerir. Denetim kaydı, aramanın gerçekleştirildiği Outlook ortamını da gösterir. Bir araştırmacı, saldırganın gerçekleştirdiği arama sorgularını inceleyerek, aranan e-posta verilerinin amacını daha iyi anlayabilir.

SearchQueryInitiatedExchange denetim kayıtlarını aramak için, uyumluluk merkezindeki [denetim günlüğü arama aracındaki](search-the-audit-log-in-security-and-compliance.md) **Arama etkinlikleri** açılan listesinde **Gerçekleştirilen e-posta** arama etkinliğini arayabilirsiniz.

![Denetim günlüğü arama aracında gerçekleştirilen e-posta arama eylemleri aranıyor.](../media/AdvAudit_SearchExchange.png)

Exchange Online PowerShell'de [Search-UnifiedAuditLog -Operations SearchQueryInitiatedExchange'i](/powershell/module/exchange/search-unifiedauditlog) de çalıştırabilirsiniz.

> [!NOTE]
> Bu olayı denetim günlüğünde arayabilmeniz için SearchQueryInitiatedExchange'in günlüğe kaydedilmesini etkinleştirmeniz gerekir. Yönergeler için bkz. [Denetimi Ayarlama (Premium)](set-up-advanced-audit.md#step-2-enable-audit-premium-events).

### <a name="searchqueryinitiatedsharepoint"></a>SearchQueryInitiatedSharePoint

Posta kutusu öğelerini aramaya benzer şekilde, bir kişi SharePoint öğeleri ararken SearchQueryInitiatedSharePoint olayı tetiklenir. Aşağıdaki SharePoint site türlerinin kök veya varsayılan sayfasında aramalar yapıldığında olaylar tetiklenir:

- Giriş siteleri

- İletişim siteleri

- Merkez siteleri

- Microsoft Teams ile ilişkilendirilmiş siteler

Araştırmacılar SearchQueryInitiatedSharePoint olayını kullanarak bir saldırganın SharePoint hassas bilgileri bulmaya çalışıp çalışmadığını (ve büyük olasılıkla erişip erişmediğini) belirleyebilir. SearchQueryInitiatedSharePoint olayının denetim kaydı, arama sorgusunun gerçek metnini de içerir. Denetim kaydı, arama yapılan SharePoint sitenin türünü de gösterir. Bir araştırmacı, saldırganın gerçekleştirmiş olabileceği arama sorgularını inceleyerek, aranmakta olan dosya verilerinin amacını ve kapsamını daha iyi anlayabilir.

SearchQueryInitiatedSharePoint denetim kayıtlarını aramak için, uyumluluk merkezindeki [denetim günlüğü arama aracındaki](search-the-audit-log-in-security-and-compliance.md) **Arama etkinlikleri** açılan listesinde **Gerçekleştirilen SharePoint** arama etkinliğini arayabilirsiniz.

![Denetim günlüğü arama aracında Gerçekleştirilen SharePoint arama eylemlerini arama.](../media/AdvAudit_SearchSharePoint.png)

Exchange Online PowerShell'de [Search-UnifiedAuditLog -Operations SearchQueryInitiatedSharePoint'i](/powershell/module/exchange/search-unifiedauditlog) de çalıştırabilirsiniz.

> [!NOTE]
> Bu olayı denetim günlüğünde arayabilmeniz için SearchQueryInitiatedSharePoint'in günlüğe kaydedilmesini etkinleştirmeniz gerekir. Yönergeler için bkz. [Denetimi Ayarlama (Premium)](set-up-advanced-audit.md#step-2-enable-audit-premium-events).

### <a name="other-audit-premium-events-in-microsoft-365"></a>Microsoft 365'deki diğer Denetim (Premium) olayları

Exchange Online ve SharePoint Online'daki olaylara ek olarak, diğer Microsoft 365 hizmetlerinde kullanıcılara uygun Denetim (Premium) lisansı atandığında günlüğe kaydedilen olaylar vardır. Aşağıdaki Microsoft 365 hizmetleri Denetim (Premium) olayları sağlar. Bu olayları tanımlayan ve açıklayan bir makaleye gitmek için ilgili bağlantıyı seçin.

- [Microsoft Forms](search-the-audit-log-in-security-and-compliance.md#microsoft-forms-activities)

- [Microsoft Stream](/stream/audit-logs#actions-logged-in-stream)

- [Microsoft Teams](/microsoftteams/audit-log-events#teams-activities)

- [Yammer](search-the-audit-log-in-security-and-compliance.md#yammer-activities)

## <a name="high-bandwidth-access-to-the-office-365-management-activity-api"></a>Office 365 Yönetim Etkinliği API'sine yüksek bant genişliği erişimi

Office 365 Yönetim Etkinliği API'si aracılığıyla denetim günlüklerine erişen kuruluşlar, yayımcı düzeyinde azaltma sınırlarıyla kısıtlandı. Bu, birden çok müşteri adına veri çeken bir yayımcı için sınırın tüm müşteriler tarafından paylaşıldığı anlamına gelir.

Denetim (Premium) sürümüyle, yayımcı düzeyi sınırından kiracı düzeyi sınırına geçiyoruz. Sonuç olarak her kuruluş, denetim verilerine erişmek için kendi tam olarak ayrılmış bant genişliği kotasına sahip olur. Bant genişliği statik, önceden tanımlanmış bir sınır değildir, ancak kuruluştaki koltuk sayısı ve E5/A5/G5 kuruluşlarının E5/A5/G5 olmayan kuruluşlara göre daha fazla bant genişliği elde edeceği gibi faktörlerin bir bileşimine göre modellenir.

Başlangıçta tüm kuruluşlara dakikada 2.000 istek temeli ayrılır. Bu sınır, kuruluşun koltuk sayısı ve lisanslama aboneliğine bağlı olarak dinamik olarak artar. E5/A5/G5 kuruluşları, E5/A5/G5 olmayan kuruluşların yaklaşık iki katı bant genişliğine sahip olur. Hizmetin durumunu korumak için maksimum bant genişliği sınırı da olacaktır.

Daha fazla bilgi için Office 365 [Yönetim Etkinliği API başvurusunun "API](/office/office-365-management-api/office-365-management-activity-api-reference#api-throttling) azaltma" bölümüne bakın.

## <a name="faqs-for-audit-premium"></a>Denetim hakkında SSS (Premium)

**Denetim (Premium) özelliğinden yararlanmak için her kullanıcının E5/A5/G5 lisansına ihtiyacı var mı?**

Kullanıcı düzeyinde Denetim (Premium) özelliklerinden yararlanmak için kullanıcıya E5/A5/G5 lisansı atanması gerekir. Özelliği kullanıcıya göstermek için uygun lisansı denetleyecek bazı özellikler vardır. Örneğin, uygun lisansa 90 günden uzun süre atanmamış bir kullanıcının denetim kayıtlarını korumaya çalışıyorsanız sistem bir hata iletisi döndürür.

**Kuruluşumun E5/A5/G5 aboneliği var, Denetim (Premium) olaylarının denetim kayıtlarına erişmek için herhangi bir şey yapmam gerekiyor mu?**

Uygun E5/A5/G5 lisansını atamış uygun müşteriler ve kullanıcılar için, SearchQueryInitiatedExchange ve SearchQueryInitiatedSharePoint olaylarını (bu makalede daha önce açıklandığı gibi) etkinleştirme dışında Denetim (Premium) olaylarına erişmek için herhangi bir eylem gerekmez. Denetim (Premium) olayları E5/A5/G5 lisansına sahip kullanıcılar için yalnızca bu lisanslar atandıktan sonra oluşturulur.

**Denetim (Premium) içindeki yeni olaylar Office 365 Yönetim Etkinliği API'sinde kullanılabilir mi?**

Evet. Uygun lisansa sahip kullanıcılar için denetim kayıtları oluşturulduğu sürece, bu kayıtlara Office 365 Yönetim Etkinliği API'sini kullanarak erişebilirsiniz.

**Özellik genel kullanıma sunulduğunda ancak gerekli eklenti lisansı kullanıma sunulmadan önce 10 yıllık bir denetim günlüğü saklama ilkesi oluşturursam kuruluşumun denetim günlüğü verilerine ne olur?**

Özellik 2020'nin son çeyreğinde genel kullanıma sunulduktan sonra oluşturduğunuz 10 yıllık denetim günlüğü saklama ilkesi kapsamındaki tüm denetim günlüğü verileri 10 yıl boyunca saklanır. Buna, mart 2021'de satın almak üzere gerekli eklenti lisansı yayınlanmadan önce oluşturulmuş 10 yıllık denetim günlüğü saklama ilkeleri dahildir. Ancak, 10 Yıllık Denetim Günlüğü Saklama Ekleme lisansı artık kullanılabilir olduğundan, denetim verileri 10 yıllık denetim saklama ilkesi kapsamında olan tüm kullanıcılar için bu eklenti lisanslarını satın almanız ve atamanız gerekir.
