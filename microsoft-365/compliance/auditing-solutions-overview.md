---
title: Microsoft 365 çözümlerini denetleme
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
- m365-security-compliance
- m365solution-audit
- m365initiative-compliance
- m365solution-overview
search.appverid:
- MOE150
- MET150
description: İlk kuruluş kapsamındaki kullanıcılar ve yöneticilerin etkinliklerini denetlemeyi Microsoft 365 öğrenin.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 92fb008e7fe03b4871b8838d78965c1508a20fdc
ms.sourcegitcommit: 584b4757f715a3eedf748858461c568f45137438
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2022
ms.locfileid: "63494534"
---
# <a name="auditing-solutions-in-microsoft-365"></a>Denetim çözümleri Microsoft 365

Microsoft 365 çözümlerini kontrol etmek, kuruluşların güvenlik olaylarına, araştırmalara, iç soruşturmalara ve uyumluluk yükümlülüklerine etkili bir şekilde yanıt vermelerine yardımcı olmak için tümleşik bir çözüm sağlar. Onlarca farklı hizmet ve Microsoft 365 gerçekleştirilen binlerce kullanıcı ve yönetici işlemi, kuruluşun birleşik denetim günlüğünde yakalanır, kaydedilir ve korunur. Bu olayların denetim kayıtlarında, güvenlik görevlileri, IT yöneticileri, insider risk ekipleri ve organizasyon organizasyonlarında uyumluluk ve yasal güvenlik nedeniyle arama edilebilir. Bu özellik, ülkeniz genelinde gerçekleştirilen etkinliklerin görünürlüğünü Microsoft 365 sağlar.

## <a name="microsoft-365-auditing-solutions"></a>Microsoft 365 çözümlerini denetleme

Microsoft 365 çözüm sağlar: Temel Denetim ve Gelişmiş Denetim.

![Temel Denetim ve Gelişmiş Denetim'in temel özellikleri.](..\media\AuditingSolutionsComparison.png)

### <a name="basic-audit"></a>Temel Denetim

Temel Denetim, denetlenen etkinlikleri günlüğe kaydedebilme ve arama yapma olanağı sağlar ve araştırma, IT, uyumluluk ve yasal soruşturmalarınızı güç sağlar.

- **Varsayılan olarak etkindir**. Temel Denetim, uygun aboneliğe sahip tüm kuruluşlarda varsayılan olarak açıktır. Bu, denetlenen etkinliklerin kayıtlarının yakalanır ve aranabilir olduğu anlamına gelir. Gereken tek kurulum denetim günlüğü arama aracına (ve ilgili cmdlet'e) erişmek için gerekli izinleri atamak ve kullanıcıya Gelişmiş Denetim özellikleri için doğru lisans atan olduğundan emin olmaktır.
- **Binlerce aranabilir denetim olayları**. Denetlenen etkinliklerin büyük bir çoğunun denetlenen birçok etkinlik için arama Microsoft 365 bir hizmettir. Arayabilirsiniz etkinliklerin kısmi bir listesi için bkz. [Denetlenen etkinlikler](search-the-audit-log-in-security-and-compliance.md#audited-activities). Denetlenen etkinlikleri destekleyen hizmetlerin ve özelliklerin listesi için bkz. [Denetim günlüğü kayıt türü](/office/office-365-management-api/office-365-management-activity-api-schema#auditlogrecordtype).
- **Denetim arama aracı Microsoft 365 uyumluluk merkezi**. Denetim kayıtlarını aramak için denetim günlüğü Microsoft 365 uyumluluk merkezi denetim günlüğü arama aracını kullanın. Belirli etkinlikleri, belirli kullanıcılar tarafından gerçekleştirilen etkinlikleri ve tarih aralığıyla gerçekleştirilen etkinlikleri arayabilirsiniz. Uyumluluk merkezi'nde Denetim arama aracının ekran görüntüsü.

   ![Denetim günlüğü arama aracı Microsoft 365 uyumluluk merkezi.](../media/AuditLogSearchToolMCC.png)

- **Search-UnifiedAuditLog cmdlet**. Denetim olaylarını aramak veya bir betikte kullanmak için Exchange Online PowerShell'de (arama aracının temel cmdlet'i) **Search-UnifiedAuditLog** cmdlet'ini de kullanabilirsiniz. Daha fazla bilgi için bkz.:

  - [Search-UnifiedAuditLog cmdlet başvurusu](/powershell/module/exchange/search-unifiedauditlog)
  - [Denetim günlüğünde arama yapmak için PowerShell betiği kullanma](audit-log-search-script.md)

- **Denetim kayıtlarını CSV dosyasına aktarın**. Uyumluluk merkezinde Denetim günlüğü arama aracını çalıştırdikten sonra, arama tarafından döndürülen denetim kayıtlarını CSV dosyasına aktarabilirsiniz. Bu, farklı denetim kaydı Microsoft Excel sıralamak ve filtrelemek için veri sıralama ve filtreleme özelliklerini kullanmanizi sağlar. Denetim Verileri JSON Excel tek tek her özelliği kendi sütununa bölmek için Power Query dönüştürme işlevini de kullanabilirsiniz. Bu, farklı olaylar için benzer verileri etkili bir şekilde görüntülemenizi ve karşılaştırmayı sağlar. Daha fazla bilgi için bkz [. Denetim günlüğü kayıtlarını dışarı aktarma, yapılandırma ve görüntüleme](export-view-audit-log-records.md).

- **Yönetim Etkinliği API'si aracılığıyla Office 365 erişimi.** Denetim kayıtlarına erişmek ve kayıt almak için üçüncü bir yöntem de denetim Office 365 API'sini kullanmaktır. Bu, kuruluşların denetim verilerini varsayılan 90 günlük süreden daha uzun süre tutmalarını ve denetim verilerini SIEM çözümüne aktarmalarını sağlar. Daha fazla bilgi için bkz[. Office 365 API başvurusu.](/office/office-365-management-api/office-365-management-activity-api-reference)

- **90 günlük denetim günlüğü tutma**. Kullanıcı veya yönetici tarafından denetlenen bir etkinlik gerçekleştirilen, bir denetim kaydı oluşturulur ve kuruluşun denetim günlüğünde depolanır. Temel Denetim'de kayıtlar 90 gün süreyle korunur; bu da, son üç ay içinde 4 etkinlik için arama esasını atayabilirsiniz.

### <a name="advanced-audit"></a>Gelişmiş Denetim

Denetim günlüğü bekletme ilkeleri, denetim kayıtlarının daha uzun süre saklama, yüksek değerli önemli olaylar ve genel Yönetim Etkinliği API'sinde daha yüksek bant genişliği erişimi sağlayarak Temel Denetim özelliklerini temel Office 365 oluşturur.

- **Denetim günlüğü bekletme ilkeleri**. Bir yıla kadar (ve gerekli eklenti lisansına sahip kullanıcılar için en fazla 10 yıl) denetim kayıtlarını daha uzun süre tutmak için, özelleştirilmiş denetim günlüğü bekletme ilkeleri oluşturabilirsiniz. Denetlenen etkinliklerin oluştuğu hizmet, denetlenen belirli etkinlikler veya denetlenen etkinlik gerçekleştiren kullanıcıya bağlı olarak denetim kayıtlarını tutmak için bir ilke oluşturabilirsiniz.

- **Denetim kayıtlarının daha uzun süre tutulması**. Exchange, SharePoint ve Azure Active Directory kayıtları varsayılan olarak bir yıl boyunca korunur. Diğer tüm etkinliklerin denetim kayıtları varsayılan olarak 90 gün süreyle korunur veya daha uzun bekletme sürelerini yapılandırmak için denetim günlüğü bekletme ilkelerini kullanabilirsiniz.

- **Yüksek değerli, çok önemli Gelişmiş Denetim olayları**. Önemli olayların denetim kayıtları, posta öğelerine ne zaman erişıldığı, posta öğelerine ne zaman yanıt ve iletil olduğu, Exchange Online ve SharePoint Online'da kullanıcının ne zaman ve ne zaman arandığı gibi olaylar için görünürlük sağlayarak, kuruluşa araştırma ve uyumluluk soruşturmaları yürütmesine yardımcı olabilir. Bu önemli olaylar olası ihlalleri araştırmanıza ve güvenlik ihlallerinin kapsamını belirlemenize yardımcı olabilir.

- **Office 365 Yönetim Etkinliği API'si için daha yüksek bant genişliği**. Gelişmiş Denetim, kuruluşlara Yönetim Etkinliği API'si aracılığıyla denetim günlüklerine erişmek için Office 365 sağlar. Temel Denetim veya Gelişmiş Denetime sahip tüm kuruluşlara başlangıçta dakikada 2.000 istek temel ayrılmış olsa da, kuruluşun lisans sayısına ve lisans aboneliklerine bağlı olarak bu sınır dinamik olarak artar. Bu da, Gelişmiş Denetim'e sahip kuruluşların Temel Denetim'i olan kuruluşlar olarak bant genişliğinin yaklaşık iki katını almalarını sağlar.

Gelişmiş Denetim özellikleri hakkında daha ayrıntılı bilgi için bkz. Gelişmiş [Denetim Microsoft 365](advanced-audit.md).

## <a name="comparison-of-key-capabilities"></a>Önemli becerilerin karşılaştırılması

Aşağıdaki tabloda, Temel Denetim ve Gelişmiş Denetim'de bulunan temel özellikler karşılaştırıldı. Tüm Temel Denetim işlevleri Gelişmiş Denetim'e dahil edilir.

|Özellik|Temel Denetim|Gelişmiş Denetim|
|:------|:-------------|:-------------|
|Varsayılan olarak etkin|![Desteklenir.](../media/check-mark.png)|![Desteklenir.](../media/check-mark.png)|
|Aranabilir binlerce denetim olayları|![Desteklenir.](../media/check-mark.png)|![Desteklenir.](../media/check-mark.png)|
|Denetim arama aracı Microsoft 365 uyumluluk merkezi|![Desteklenir.](../media/check-mark.png)|![Desteklenir.](../media/check-mark.png)|
|Search-UnifiedAuditLog cmdlet'i|![Desteklenir.](../media/check-mark.png)|![Desteklenir.](../media/check-mark.png)|
|Denetim kayıtlarını CSV dosyasına aktarma|![Desteklenir.](../media/check-mark.png)|![Desteklenir.](../media/check-mark.png)|
|Office 365 Yönetim Etkinliği API'si 1 üzerinden denetim <sup>günlüklerine erişim</sup>|![Desteklenir.](../media/check-mark.png)|![Desteklenir.](../media/check-mark.png)</sup>|
|90 günlük denetim günlüğü bekletme|![Desteklenir.](../media/check-mark.png)|![Desteklenir.](../media/check-mark.png)|
|1 yıllık denetim günlüğü tutma||![Desteklenir.](../media/check-mark.png)|
|10 yıllık denetim günlüğü bekletme <sup>2</sup>||![Destekleniyor](../media/check-mark.png)|
|Denetim günlüğü bekletme ilkeleri||![Destekleniyor](../media/check-mark.png)|
|Yüksek değerli, çok önemli olaylar||![Destekleniyor](../media/check-mark.png)|
||||
> [!NOTE]
> <sup>1</sup> Gelişmiş Denetim, denetim verilerine daha hızlı erişim Office 365 Yönetim Etkinliği API'sinde daha yüksek bant genişliği erişimi içerir.<br/><sup>2</sup> Gelişmiş Denetim için gereken lisanslara ek olarak (sonraki bölümde açıklanmıştır), bir kullanıcıya 10 yıl boyunca denetim kayıtlarını korumak için 10 Yıllık Denetim Günlüğü Bekletme ekleme lisansı atanabilir.

## <a name="licensing-requirements"></a>Lisans gereksinimleri

Aşağıdaki bölümlerde Temel Denetim ve Gelişmiş Denetim için lisans gereksinimleri tanımlanmaktadır. Temel Denetim işlevselliği Gelişmiş Denetim'e dahil edilir.

### <a name="basic-audit"></a>Temel Denetim

- Microsoft 365 İş Temel aboneliği
- Microsoft 365 Uygulamaları kurumsal aboneliği
- Microsoft 365 Kurumsal E3 aboneliği
- Microsoft 365 Business Premium
- Microsoft 365 Eğitim A3 aboneliği
- Microsoft 365 Government G3 aboneliği
- Microsoft 365 Government G1 aboneliği
- Microsoft 365 F1 veya F3 aboneliği ya da F5 Güvenlik eklentiniz var
- Office 365 Kurumsal E3 aboneliği
- Office 365 Kurumsal E1 aboneliği
- Office 365 Eğitim A1 aboneliği
- Office 365 Eğitim A3 aboneliği

### <a name="advanced-audit"></a>Gelişmiş Denetim

- Microsoft 365 Kurumsal E5 aboneliği
- Microsoft 365 Kurumsal E3 aboneliği + Microsoft 365 E5 Uyumluluk eklenti
- Microsoft 365 Kurumsal E3 aboneliği + Microsoft 365 E5 eBulma ve Denetim eklentiniz
- Microsoft 365 Eğitim A5 aboneliği
- Microsoft 365 Eğitim A3 aboneliği + Microsoft 365 A5 Uyumluluk eklentisi
- Microsoft 365 Eğitim A3 aboneliği + Microsoft 365 A5 eBulma ve Denetim eklentileri
- Microsoft 365 Government G5 aboneliği
- Microsoft 365 G3 aboneliği + Microsoft 365 G5 Uyumluluk eklentiniz
- Microsoft 365 G3 aboneliği + Microsoft 365 G5 eKbulma ve Denetim eklentileri
- Microsoft 365 F5 Uyumluluğu veya F5 Güvenlik & Uyumluluk eklentisi
- Office 365 Kurumsal E5 aboneliği
- Office 365 Eğitim A5 aboneliği

## <a name="set-up-microsoft-365-auditing-solutions"></a>Denetim Microsoft 365 ayarlama

Aşağıdaki kurulum kılavuzunda denetim çözümlerini kullanmaya Microsoft 365 için aşağıdaki kurulum kılavuzuna bakın.

### <a name="set-up-basic-audit"></a>Temel Denetimi Ayarlama

İlk adım, Temel Denetim'i ayarlamak ve ardından denetim günlüğü aramalarını çalıştırmaya başlamaktır.

![Temel Denetimi ayarlamak için iş akışı.](../media/BasicAuditingWorkflow.png)

1. Kuruluşta Temel Denetimi destekleyen bir abonelik ve varsa Gelişmiş Denetimi destekleyen bir abonelik olduğunu doğrulayın.

2. Exchange Online'da denetim günlüğü arama aracını kullanacak veya **Search-UnifiedAuditLog** cmdlet'ini Microsoft 365 uyumluluk merkezi izinler atabilirsiniz. Özel olarak, kayıtta kullanıcılara View-Only Günlükleri veya Denetim Günlükleri rolü Exchange Online.

3. Denetim günlüğünde arama yapın. 1. adımı ve 2. adımı tamamladıktan sonra, kurumundaki kullanıcılar denetim günlüğü arama aracını (veya ilgili cmdlet) kullanarak denetlenen etkinlikleri arayabilir.

Daha ayrıntılı yönergeler için bkz. [Temel Denetimi Ayarlama](set-up-basic-audit.md).

### <a name="set-up-advanced-audit"></a>Gelişmiş Denetimi Ayarlama

Kuruluşta Gelişmiş Denetimi destekleyen bir abonelik varsa, Gelişmiş Denetim'de ek özellikleri ayarlamak ve kullanmak için aşağıdaki adımları uygulayın.

![Gelişmiş Denetimi ayarlamak için iş akışı.](../media/AdvancedAuditWorkflow.png)

1. Kullanıcılar için Gelişmiş Denetim'i ayarlayın. Bu adım aşağıdaki görevlerden oluşur:

   - Kullanıcılara Gelişmiş Denetim için uygun lisans veya eklenti lisansı atan olduğunu doğrulama.
  
   - Bu kullanıcılar için Gelişmiş Denetim uygulaması/hizmet planının açış olması gerekir.
  
   - Önemli olayların denetimini etkinleştirme ve sonra bu kullanıcılar için Gelişmiş Denetim uygulaması/hizmet planını etkinleştirme.

2. Kullanıcılar Exchange Online SharePoint Online'da arama gerçekleştirebilirken Gelişmiş Denetim olaylarının günlüğe SharePoint.

3. Denetim günlüğü bekletme ilkelerini ayarlama. Exchange, SharePoint ve Azure AD denetim kayıtlarını bir yıl süreyle alıkoyan varsayılan ilkeye ek olarak, kuruluşun güvenlik işlemleri, IT ve uyumluluk ekiplerinin gereksinimlerini karşılamak için ek denetim günlüğü bekletme ilkeleri oluşturabilirsiniz.

4. Araştırma yürüten çok önemli Gelişmiş Denetim etkinliklerini ve diğer etkinlikleri arayabilirsiniz. 1. ve 2. adımı tamamladıktan sonra, güvenliği tehlikeye atılmış hesaplarda ve diğer türlerde güvenlik ve uyumluluk soruşturmaları ile ilgili araştırmalarda Gelişmiş Denetim olayları ve diğer etkinlikler için denetim günlüğünde arama gerçekleştirebilirsiniz.

Daha ayrıntılı yönergeler için bkz. [Gelişmiş Denetimi Ayarlama](set-up-advanced-audit.md).

## <a name="training"></a>Eğitim

Temel Denetim ve Gelişmiş Denetim temellerine yönelik temel bilgilerle güvenlik işlemleri ekibinizi, IT yöneticilerini ve uyumluluk ekibini eğitime almak, incelemelerinize yardımcı olmak için denetimi daha hızlı kullanmaya başlamanıza yardımcı olabilir. Microsoft 365, bu kullanıcıların denetime başlamalarına yardımcı olmak için aşağıdaki kaynağı sağlar: Kullanıcıların eBulma ve denetim [özelliklerini Microsoft 365](/learn/modules/describe-ediscovery-capabilities-of-microsoft-365).
