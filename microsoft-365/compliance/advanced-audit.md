---
title: Gelişmiş Denetim Microsoft 365
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
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
description: Gelişmiş Denetim Microsoft 365 araştırmalarda araştırma ve uyumluluk ile ilgili olarak organizasyona yardımcı olmak için yeni denetim özellikleri sağlar.
ms.openlocfilehash: 4a378071a59d2462cff1af5b87f9ab99d1e1337f
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2022
ms.locfileid: "63032491"
---
# <a name="advanced-audit-in-microsoft-365"></a>Gelişmiş Denetim Microsoft 365

Denetim [işlevselliği,](search-the-audit-log-in-security-and-compliance.md) Microsoft 365 birçok farklı hizmet genelinde, birçok farklı hizmette denetlenen birçok etkinlik türüyle ilgili görünürlük Microsoft 365. Gelişmiş Denetim, araştırma yapmak için gereken denetim günlüğü bekletmesini artırarak, önemli olaylara erişim sağlayarak (Microsoft 365 uyumluluk merkezi ve Office 365 Yönetim Etkinliği API'sinde Denetim günlüğü araması kullanarak) güvenliğin kapsamını belirlemeye ve güvenlik kapsamını belirlemeye yardımcı olarak Office 365 Yönetimi Etkinliği API'si.

> [!NOTE]
> Gelişmiş Denetim, Office 365 E5/A5/G5 veya Microsoft 365 Kurumsal E5/A5/G5 aboneliği olan kuruluşlarda kullanılabilir. Bir Microsoft 365 E5/A5/G5 Uyumluluğu veya E5/A5/G5 eBulma ve Denetim eklenti lisansı, uzun vadeli denetim günlükleri tutma ve soruşturmalar için Gelişmiş Denetim olaylarının yeniden üretimi gibi Gelişmiş Denetim özellikleri için kullanıcılara atanabilir. Lisanslama hakkında daha fazla bilgi için bkz:<br/>- [Gelişmiş Denetim lisans gereksinimleri](auditing-solutions-overview.md#licensing-requirements)<br/>- [Microsoft 365 uyumluluğu için lisans & kılavuzu.](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#advanced-audit)

Bu makalede, Gelişmiş Denetim özelliklerine genel bir bakış ve Gelişmiş Denetim için kullanıcıların nasıl ayarlanmıştır.

## <a name="long-term-retention-of-audit-logs"></a>Denetim günlüklerinin uzun süreli tutma

Gelişmiş Denetim, tüm Exchange, SharePoint ve Azure Active Directory yıllık denetim kayıtlarını korur. Bu, bir yıl süreyle **workload** özelliği için **Exchange**, **SharePoint** veya **AzureActiveDirectory** değerini içeren tüm denetim kaydını tutan bir varsayılan denetim günlüğü bekletme ilkesiyle işler. Denetim kayıtlarının daha uzun süre tutularak devam edecek yasal incelemeler veya uyumluluk soruşturmaları için yardımcı olabilir. Daha fazla bilgi için Denetim günlüğü bekletme ilkelerini yönetme bölümündeki "Varsayılan denetim günlüğü bekletme [ilkesi" bölümüne bakın](audit-log-retention-policies.md#default-audit-log-retention-policy).

Gelişmiş Denetim'in bir yıllık bekletme özelliklerine ek olarak, denetim günlüklerini 10 yıl süreyle tutma özelliğini de yayınladık. Denetim günlüklerinin 10 yıllık tutulması, uzun süre devam eden soruşturmaları desteklemeye ve mevzuat, yasal ve iç yükümlülüklere yanıt vermeye yardımcı olur.

> [!NOTE]
> 10 yıllık denetim günlüklerinin tutulması için kullanıcı başına ek eklenti lisansı gerekir. Bu lisans bir kullanıcıya atandıktan ve kullanıcı için uygun 10 yıllık denetim günlüğü bekletme ilkesi ayarlandıktan sonra, bu ilkenin kapsadığı denetim günlükleri 10 yıllık süre boyunca korunur. Bu ilke geriye dönük değildir ve 10 yıllık denetim günlüğü bekletme ilkesi oluşturulmadan önce oluşturulan denetim günlüklerini koruyamıyor. Daha fazla bilgi için, bu [makaledeki Gelişmiş Denetim ile ilgili SSS](#faqs-for-advanced-audit) bölümüne bakın.

### <a name="audit-log-retention-policies"></a>Denetim günlüğü bekletme ilkeleri

Varsayılan denetim günlüğü bekletme ilkesi kapsamında olmayan diğer hizmetlerde oluşturulan tüm denetim kayıtları (önceki bölümde açıklanmıştır) 90 gün boyunca korunur. Ancak, diğer denetim kayıtlarını 10 yıl süreyle daha uzun süre tutmak için, özelleştirilmiş denetim günlüğü bekletme ilkeleri oluşturabilirsiniz. Aşağıdaki ölçütlerden birini veya birden fazlasını temel alarak denetim kayıtlarını tutmak için bir ilke oluşturabilirsiniz:

- Denetlenen Microsoft 365 gerçekleştiren en iyi hizmet.

- Denetlenen belirli etkinlikler.

- Denetlenen bir etkinlik gerçekleştiren kullanıcı.

Ayrıca, belirli ilkelerin diğer ilkelere göre öncelik alacak şekilde, ilkeyle ve öncelik düzeyiyle eşleşmesi için denetim kayıtlarının ne kadar süreyle korunacaklarını da belirtmelisiniz. Ayrıca, özel denetim günlüğü bekletme ilkesi, varsayılan denetim bekletme ilkesinden önceliğe sahip olacaktır. Bu durumda, kuruluş birçok kullanıcının veya tüm kullanıcıların Exchange, SharePoint veya Azure Active Directory denetim kayıtlarını bir dakikadan daha kısa bir süreyle (veya 10 yıl boyunca) tutmanız gerekir. Daha fazla bilgi için bkz [. Denetim günlüğü bekletme ilkelerini yönetme](audit-log-retention-policies.md).

## <a name="advanced-audit-events"></a>Gelişmiş Denetim olayları

Gelişmiş Denetim, posta öğelerine erişilme, posta öğelerine ne zaman yanıt ve iletil olduğu, Exchange Online ve SharePoint Exchange Online Online'da kullanıcının ne zaman ve ne zaman arandığı gibi önemli olaylara erişim sağlayarak kuruluşların denetim ve uyumluluk soruşturmaları yürütmesine yardımcı olur. Bu olaylar olası ihlalleri araştırmanıza ve güvenlik ihlallerinin kapsamını belirlemenize yardımcı olabilir. Exchange ve SharePoint'te bu olaylara ek olarak, önemli olaylar kabul edilen ve kullanıcılara uygun Gelişmiş Denetim lisansının atanmalarını gerektiren başka Microsoft 365 hizmetlerinden [de olay vardır](auditing-solutions-overview.md#licensing-requirements). Kullanıcılar bu olayları gerçekleştirecekken denetim günlükleri oluşturulacak şekilde kullanıcılara Bir Gelişmiş Denetim lisansı atanabilir.

Gelişmiş Denetim aşağıdaki olayları sağlar:

- [MailItemsAccessed](#mailitemsaccessed)

- [Gönderin](#send)

- [SearchQueryInitiatedExchange](#searchqueryinitiatedexchange)

- [SearchQueryInitiatedSharePoint](#searchqueryinitiatedsharepoint)

- [Microsoft 365'daki diğer Gelişmiş Denetim Microsoft 365](#other-advanced-audit-events-in-microsoft-365)

### <a name="mailitemsaccessed"></a>MailItemsAccessed

MailItemsAccessed olayı, posta kutusu denetim eylemidir ve posta verilerine posta protokolleri ve posta istemcilerinin eriştiğinde tetiklenir. Bu olay, kullanıcıya veri ihlallerini belirleme ve ihlal edilmiş olan iletilerin kapsamını belirlemede yardımcı olabilir. Bir saldırgan e-posta iletilerine erişim kazandı ise, iletilerin aslında okundu olarak açıkça sinyal hiç okunmasa bile MailItemsAccessed eylemi tetiklenir (başka bir deyişle, bağlama veya eşitleme gibi erişim türü denetim kaydına kaydedilir).

MailItemsAccessed olayı, Exchange Online'te posta kutusu denetim günlüğünde MessageBind'in yerini alır ve şu iyileştirmeleri sağlar:

- MessageBind yalnızca AuditAdmin kullanıcı oturum açma türü için yapılandırılabilirdi; temsilci veya sahip eylemleri için geçerli değildir. MailItemsAccessed tüm oturum açma türleri için geçerlidir.

- MessageBind yalnızca bir posta istemcisi tarafından ele ele alır. Eşitleme etkinlikleri için geçerli değildi. MailItemsAccessed olayları hem bağlama hem de eşitleme erişim türleri tarafından tetiklenir.

- MessageBind eylemleri, aynı e-posta iletisine erişilirken birden çok denetim kaydı oluşturulmasını tetikler ve bunun sonucunda "gürültü" denetlenebilir. Buna karşılık, MailItemsAccessed olayları daha az denetim kaydında bir araya toplanır.

MailItemsAccessed etkinliklerinin denetim kayıtları hakkında bilgi için bkz. Güvenliği ihlal edilmiş hesapları araştırmak [için Gelişmiş Denetimi kullanma](mailitemsaccessed-forensics-investigations.md).

MailItemsAccessed denetim kayıtlarını aramak için, denetim günlüğü arama aracında yer  alan **Exchange** posta kutusu etkinlikleri açılan listesinde Erişilen posta kutusu öğeleri etkinliği için Microsoft 365 uyumluluk merkezi.[](search-the-audit-log-in-security-and-compliance.md)

![Denetim günlüğü arama aracında MailItemsAccessed eylemleri arama.](../media/AdvAudit_MailItemsAccessed.png)

Ayrıca, Exchange Online PowerShell'de [Search-UnifiedAuditLog -Operations MailItemsAccessed](/powershell/module/exchange/search-unifiedauditlog) veya [Search-MailboxAuditLog -Operations MailItemsAccessed](/powershell/module/exchange/search-mailboxauditlog) komutlarını da çalıştırabilirsiniz.

### <a name="send"></a>Gönderin

Send olayı aynı zamanda posta kutusu denetim eylemidir ve kullanıcı aşağıdaki eylemlerden birini gerçekleştir olduğunda tetiklenir:

- E-posta iletisi gönderir

- E-posta iletisi yanıtlar

- E-posta iletisi iletir

İlkeler güvenliği ihlal edilmiş bir hesaptan gönderilen e-postaları tanımlamak için Gönderme etkinliği kullanabilir. Gönder olayı denetim kaydı, ileti hakkında, örneğin iletinin gönderildiği zaman, InternetMessage Kimliği, konu satırı ve iletinin ekleri olup içermesi gibi bilgileri içerir. Bu denetim bilgileri, güvenliği tehlikeye atılmış bir hesaptan gönderilen veya bir saldırgan tarafından gönderilen e-posta iletileriyle ilgili bilgileri belirlemeye yardımcı olabilir. Buna ek olarak, güvenlik nedenleri Microsoft 365 iletinin gönderildiği alıcıları ve gönderilen iletinin gerçek içeriğini tanımlamak üzere iletiyi aramak için (konu satırı veya ileti kimliği kullanarak) bir Microsoft 365 eBulma aracı kullanabilir.

Denetim kayıtlarını gönder için, denetim günlüğü arama aracında yer alan  **Exchange** posta kutusu etkinlikleri açılan listesinde Gönderilmiş ileti etkinliği için arama Microsoft 365 uyumluluk merkezi.[](search-the-audit-log-in-security-and-compliance.md)

![Denetim günlüğü arama aracında Gönderilen ileti eylemlerini arama.](../media/AdvAudit_SentMessage.png)

Ayrıca, Exchange Online PowerShell'de [Search-UnifiedAuditLog -Operations Send](/powershell/module/exchange/search-unifiedauditlog) veya [Search-MailboxAuditLog -Operations Send](/powershell/module/exchange/search-mailboxauditlog) komutlarını çalıştırabilirsiniz.

### <a name="searchqueryinitiatedexchange"></a>SearchQueryInitiatedExchange

Bir kişi posta kutusunda öğe aramak için Outlook kullandığında SearchQueryInitiatedExchange olayı tetiklenir. Aşağıdaki ortamlarda aramalar gerçekleştirilen olaylar Outlook tetiklenir:

- Outlook (masaüstü istemcisi)

- Web üzerinde Outlook (OWA)

- iOS Outlook için yeni bir ifade

- Android için Outlook'i

- Posta uygulaması Windows 10

Esnaflar, bir hesabı tehlikeye atmış olan ya da posta kutusunda hassas bilgilere erişmeye çalışan bir saldırgan olup olmadığını belirlemek için SearchQueryInitiatedExchange olayini kullanabilir. SearchQueryInitiatedExchange olayı denetim kaydı, arama sorgusunun gerçek metni gibi bilgileri içerir. Denetim kaydı, aramanın Outlook ortamını da gösterir. Bir saldırgan tarafından gerçekleştirilen arama sorgularına bakarak, bir saldırgan, aranan e-posta verilerinin amacını daha iyi anlayacaktır.

SearchQueryInitiatedExchange denetim kayıtlarını aramak için, uyumluluk merkezinde denetim günlüğü arama aracında Arama etkinlikleri açılan listesinde gerçekleştirilen  e-posta arama etkinliği için arama yapılabilir.[](search-the-audit-log-in-security-and-compliance.md) 

![Denetim günlüğü arama aracında Gerçekleştirilen e-posta arama eylemleri aranma.](../media/AdvAudit_SearchExchange.png)

PowerShell'de [Search-UnifiedAuditLog -Operations SearchQueryInitiatedExchange](/powershell/module/exchange/search-unifiedauditlog) Exchange Online çalıştırabilirsiniz.

> [!NOTE]
> Denetim günlüğünde bu olayı aray için SearchQueryInitiatedExchange'in günlüğe kaydedileceğini etkinleştirmeniz gerekir. Yönergeler için bkz. [Gelişmiş Denetimi Ayarlama](set-up-advanced-audit.md#step-2-enable-advanced-audit-events).

### <a name="searchqueryinitiatedsharepoint"></a>SearchQueryInitiatedSharePoint

Posta kutusu öğelerini aramaya benzer şekilde, bir kişi posta kutusunda öğeleri ararken de SearchQueryInitiatedSharePoint SharePoint. Aşağıdaki site türlerinin kök veya varsayılan sayfasında arama yapılırken olaylar SharePoint:

- Giriş siteleri

- İletişim siteleri

- Merkez siteleri

- Sitelerle ilişkili Microsoft Teams

İlkeler, bir saldırganın bu dosyada hassas bilgileri bulmaya (ve muhtemelen erişilebiliyor) hassas bilgileri bulmaya çalışsın (ve erişilsin mi) olduğunu belirlemek için SearchQueryInitiatedSharePoint SharePoint. SearchQueryInitiatedSharePoint olay denetim kaydı da arama sorgusunun asıl metnini içerir. Denetim kaydı, arama yapılan SharePoint sitenin türünü de gösterir. Bir saldırgan tarafından gerçekleştirilen arama sorgularına bakarak, bir saldırgan aramanın amacını ve kapsamını daha iyi anlayacaktır.

SearchQueryInitiatedSharePoint denetim kayıtlarını aramak için, uyumluluk merkezinde denetim günlüğü arama aracında Arama etkinlikleri açılan listesinde **SharePoint** Arama etkinlikleri için  yapılan arama etkinliğini arayabilirsiniz.[](search-the-audit-log-in-security-and-compliance.md)

![Denetim günlüğü arama SharePoint arama eylemlerini kullanarak Gerçekleştirilen araması.](../media/AdvAudit_SearchSharePoint.png)

[Search-UnifiedAuditLog -Operations SearchQueryInitiatedSharePoint'i](/powershell/module/exchange/search-unifiedauditlog) Exchange Online PowerShell'de çalıştırabilirsiniz.

> [!NOTE]
> Denetim günlüğünde bu olayı aray için SearchQueryInitiatedSharePoint'in günlüğe kaydedileceğini etkinleştirmeniz gerekir. Yönergeler için bkz. [Gelişmiş Denetimi Ayarlama](set-up-advanced-audit.md#step-2-enable-advanced-audit-events).

### <a name="other-advanced-audit-events-in-microsoft-365"></a>Microsoft 365'daki diğer Gelişmiş Denetim Microsoft 365

Exchange Online ve SharePoint Online'daki olaylara ek olarak, diğer Microsoft 365 hizmetlerde kullanıcılara uygun Gelişmiş Denetim lisansı atandığı zaman günlüğe kaydedilen olaylar da vardır. Aşağıdaki tablo Microsoft 365 Denetim olayları sağlar. Bu olayları tanımlayan ve açıklayan makaleye gitmek için ilgili bağlantıyı seçin.

- [Microsoft Forms](search-the-audit-log-in-security-and-compliance.md#microsoft-forms-activities)

- [Microsoft Stream](/stream/audit-logs#actions-logged-in-stream)

- [Microsoft Teams](/microsoftteams/audit-log-events#teams-activities)

- [Yammer](search-the-audit-log-in-security-and-compliance.md#yammer-activities)

## <a name="high-bandwidth-access-to-the-office-365-management-activity-api"></a>Office 365 Yönetim Etkinliği API'sinde yüksek bant genişliği erişimi

Denetim günlüklerine Office 365 Yönetim Etkinliği API'si aracılığıyla erişen kuruluşlar, yayıncı düzeyinde azaltma sınırlarıyla sınırlandırılmıştır. Bu, yayıncının birden çok müşteri adına veri çekmesi için bu sınırın tüm müşteriler tarafından paylaşılması anlamına gelir.

Gelişmiş Denetim'in yayımladığı sürümle, yayıncı düzeyindeki bir sınırdan kiracı düzeyi sınırına taşıyoruz. Sonuç olarak, her kuruluş denetim verilerine erişmek için kendi tam ayrılmış bant genişliği kotasını elde edecek. Bant genişliği statik, önceden tanımlı bir sınır değildir, ancak kuruluşta yer alan kullanıcı sayısı gibi etmenlerin bir birleşimiyle modele alındı ve E5/A5/G5 kuruluşları, E5/A5/G5 olmayan kuruluşlardan daha fazla bant genişliğine sahip olacak.

Başlangıçta tüm kuruluşlara dakikada 2.000 istek taban çizgisi ayrılır. Bu sınır, kuruluşun lisans sayısına ve lisans aboneliklerine bağlı olarak dinamik olarak artar. E5/A5/G5 kuruluşları, E5/A5/G5 kuruluşu olmayan kuruluşlara yaklaşık iki kat daha fazla bant genişliği sağlar. Ayrıca, hizmetin durumunu korumak için üst bant genişliği üst sınırı da olur.

Daha fazla bilgi için Yönetim Etkinliği API başvurusu'nın "API azaltma" [Office 365 bölümüne bakın](/office/office-365-management-api/office-365-management-activity-api-reference#api-throttling).

## <a name="faqs-for-advanced-audit"></a>Gelişmiş Denetim ile ilgili SSS

**Gelişmiş Denetimden yararlanmak için her kullanıcının bir E5/A5/G5 lisansına ihtiyacı var mı?**

Kullanıcı düzeyi Gelişmiş Denetim özelliklerinden yararlanabilmek için, bir kullanıcıya E5/A5/G5 lisansı atanabilir. Özelliğin kullanıcıya açık olması için uygun lisansı denetlemeye yardımcı olacak bazı özellikler vardır. Örneğin, uygun lisansa 90 gündür atanmamış bir kullanıcının denetim kayıtlarını korumaya çalışıyorsanız, sistem bir hata iletisi döndürür.

**Kuruluşumda E5/A5/G5 aboneliği var, Gelişmiş Denetim olaylarının denetim kayıtlarına erişmek için herhangi bir şey ihtiyacım var mı?**

Uygun müşterilere ve uygun E5/A5/G5 lisansı atanan kullanıcılar için, SearchQueryInitiatedExchange ve SearchQueryInitiatedSharePoint olaylarını etkinleştirme dışında (daha önce bu makalede açıklandığı gibi) Gelişmiş Denetim olaylarına erişmek için herhangi bir işlem gerekmez. Gelişmiş Denetim olayları, yalnızca E5/A5/G5 lisansı olan kullanıcılar için bu lisanslar atandıktan sonra oluşturulur.

**Gelişmiş Denetim'de yer alan yeni etkinlikler, Office 365 Api'sinde kullanılabilir mi?**

Evet. Uygun lisansa sahip kullanıcılar için denetim kayıtları oluşturulan sürece, bu kayıtlara Proje Yönetimi Etkinlik API'si Office 365 erişebilirsiniz.

**Özellik genel kullanılabilirlik için serbest bırakılana kadar ama gerekli eklenti lisansı kullanılabilir olmadan önce bir 10 yıllık denetim günlüğü bekletme ilkesi oluşturabilirim, kuruluşum denetim günlüğü verilerine ne olur?**

Özelliğin son 2020'de genel kullanılabilirlik durumuna çıkarktan sonra oluşturduğunuz 10 yıllık denetim günlüğü bekletme ilkesi kapsamındaki tüm denetim günlüğü verileri 10 yıl boyunca korunur. Bu, gerekli eklenti lisansının Mart 2021'de satışa çıkarılamadan önce oluşturulmuş 10 yıllık denetim günlüğü bekletme ilkelerini içerir. Bununla birlikte, 10 Yıllık Denetim Günlüğü Bekletme Eklenti Lisansı artık kullanılabilir olduğundan, denetim verileri 10 yıllık denetim bekletme ilkesi kapsamında olan tüm kullanıcılar için bu eklenti lisanslarını satın almalı ve ata atalınız.
