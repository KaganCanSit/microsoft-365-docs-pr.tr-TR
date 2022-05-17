---
title: Microsoft Purview denetim çözümleri
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
- m365-security-compliance
- m365solution-audit
- m365initiative-compliance
- m365solution-overview
search.appverid:
- MOE150
- MET150
description: Microsoft 365 kuruluşunuzdaki kullanıcıların ve yöneticilerin etkinliklerini denetlemeyi öğrenin.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: d7c6ba3e63e50370579f6db89a919ec8a2dafd8f
ms.sourcegitcommit: f645e0e9db74b25663cd9ddec7e3824d6ffc57f7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2022
ms.locfileid: "65444255"
---
# <a name="auditing-solutions-in-microsoft-purview"></a>Microsoft Purview'de çözümleri denetleme

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Microsoft Purview denetim çözümleri, kuruluşların güvenlik olaylarına, adli araştırmalara, iç araştırmalara ve uyumluluk yükümlülüklerine etkili bir şekilde yanıt vermelerine yardımcı olmak için tümleşik bir çözüm sağlar. Onlarca Microsoft 365 hizmeti ve çözümünde gerçekleştirilen binlerce kullanıcı ve yönetici işlemi, kuruluşunuzun birleşik denetim günlüğünde yakalanır, kaydedilir ve saklanır. Bu olaylar için denetim kayıtları güvenlik işlemleri, BT yöneticileri, insider risk ekipleri ve kuruluşunuzdaki uyumluluk ve hukuk araştırmacıları tarafından aranabilir. Bu özellik, Microsoft 365 kuruluşunuz genelinde gerçekleştirilen etkinliklere görünürlük sağlar.

## <a name="microsoft-purview-auditing-solutions"></a>Microsoft Purview denetim çözümleri

Microsoft Purview iki denetim çözümü sağlar: Denetim (Standart) ve Denetim (Premium).

![Denetim (Standart) ve Denetim (Premium) özelliklerinin temel özellikleri.](..\media\AuditingSolutionsComparison.png)

### <a name="audit-standard"></a>Denetim (Standart)

Microsoft Purview Denetimi (Standart), denetimli etkinlikleri günlüğe kaydetme ve arama olanağı sağlar ve adli, BT, uyumluluk ve yasal araştırmalarınızı güçlendirir.

- **Varsayılan olarak etkindir**. Uygun aboneliğe sahip tüm kuruluşlar için denetim (Standart) varsayılan olarak açıktır. Bu, denetlenen etkinliklerin kayıtlarının yakalanacağı ve aranabilir olacağı anlamına gelir. Gereken tek kurulum, denetim günlüğü arama aracına (ve ilgili cmdlet'e) erişmek için gerekli izinleri atamak ve kullanıcıya Microsoft Purview Denetim (Premium) özellikleri için doğru lisans atandığından emin olmaktır.
- **Binlerce aranabilir denetim olayı**. Kuruluşunuzdaki Microsoft 365 hizmetlerinin çoğu gerçekleşen çok çeşitli denetimli etkinlikleri arayabilirsiniz. Arayabileceğiniz etkinliklerin kısmi listesi için bkz [. Denetlenen etkinlikler](search-the-audit-log-in-security-and-compliance.md#audited-activities). Denetlenen etkinlikleri destekleyen hizmetlerin ve özelliklerin listesi için bkz. [Denetim günlüğü kayıt türü](/office/office-365-management-api/office-365-management-activity-api-schema#auditlogrecordtype).
- **Microsoft Purview uyumluluk portalı denetim arama aracı**. Denetim kayıtlarını aramak için uyumluluk portalındaki Denetim günlüğü arama aracını kullanın. Belirli kullanıcılar tarafından gerçekleştirilen etkinlikler ve tarih aralığıyla gerçekleşen etkinlikler için belirli etkinlikleri arayabilirsiniz. Uyumluluk merkezindeki Denetim arama aracının ekran görüntüsü aşağıdadır.

   ![Uyumluluk portalında denetim günlüğü arama aracı.](../media/AuditLogSearchToolMCC.png)

- **Search-UnifiedAuditLog cmdlet'i**. Denetim olaylarını aramak veya bir betikte kullanmak için Exchange Online PowerShell'de (arama aracının temel cmdlet'i) **Search-UnifiedAuditLog** cmdlet'ini de kullanabilirsiniz. Daha fazla bilgi için bkz.:

  - [Search-UnifiedAuditLog cmdlet başvurusu](/powershell/module/exchange/search-unifiedauditlog)
  - [Denetim günlüğünü aramak için PowerShell betiği kullanma](audit-log-search-script.md)

- **Denetim kayıtlarını CSV dosyasına** aktarın. Uyumluluk portalında Denetim günlüğü arama aracını çalıştırdıktan sonra, arama tarafından döndürülen denetim kayıtlarını csv dosyasına aktarabilirsiniz. Bu, farklı denetim kaydı özelliklerinde sıralama ve filtreleme Microsoft Excel kullanmanıza olanak tanır. AuditData JSON nesnesindeki her özelliği kendi sütununa bölmek için Excel Power Query dönüştürme işlevini de kullanabilirsiniz. Bu, farklı olaylar için benzer verileri etkili bir şekilde görüntülemenizi ve karşılaştırmanızı sağlar. Daha fazla bilgi için bkz. [Denetim günlüğü kayıtlarını dışarı aktarma, yapılandırma ve görüntüleme](export-view-audit-log-records.md).

- **Office 365 Yönetim Etkinliği API'sini kullanarak denetim günlüklerine erişim**. Denetim kayıtlarına erişmek ve bunları almak için üçüncü bir yöntem Office 365 Yönetim Etkinliği API'sini kullanmaktır. Bu, kuruluşların denetim verilerini varsayılan 90 günden daha uzun süre saklamalarına ve denetim verilerini bir SIEM çözümüne aktarmalarına olanak tanır. Daha fazla bilgi için bkz. [Office 365 Yönetim Etkinliği API başvurusu](/office/office-365-management-api/office-365-management-activity-api-reference).

- **90 günlük denetim günlüğü saklama**. Bir kullanıcı veya yönetici tarafından denetlenen bir etkinlik gerçekleştirildiğinde, bir denetim kaydı oluşturulur ve kuruluşunuz için denetim günlüğünde depolanır. Denetim 'de (Standart), kayıtlar 90 gün boyunca tutulur, bu da son üç ay içinde gerçekleşen etkinlikleri arayabileceğiniz anlamına gelir.

### <a name="audit-premium"></a>Denetim (Premium)

Denetim (Premium), denetim günlüğü saklama ilkeleri, denetim kayıtlarının daha uzun süre saklanması, yüksek değerli kritik olaylar ve Office 365 Yönetim Etkinliği API'sine daha yüksek bant genişliği erişimi sağlayarak Denetim (Standart) özelliklerini temel alır.

- **Denetim günlüğü saklama ilkeleri**. Denetim kayıtlarını bir yıla kadar (ve gerekli eklenti lisansına sahip kullanıcılar için 10 yıla kadar) daha uzun süreler boyunca tutmak için özelleştirilmiş denetim günlüğü saklama ilkeleri oluşturabilirsiniz. Denetim etkinliklerinin gerçekleştiği hizmeti, belirli denetlenen etkinlikleri veya denetimli etkinliği gerçekleştiren kullanıcıyı temel alarak denetim kayıtlarını tutmak için bir ilke oluşturabilirsiniz.

- **Denetim kayıtlarının daha uzun süre saklanması**. Exchange, SharePoint ve Azure Active Directory denetim kayıtları varsayılan olarak bir yıl boyunca saklanır. Diğer tüm etkinliklerin denetim kayıtları varsayılan olarak 90 gün boyunca tutulur veya daha uzun saklama dönemlerini yapılandırmak için denetim günlüğü saklama ilkelerini kullanabilirsiniz.

- **Yüksek değerli, önemli Denetim (Premium) olayları**. Kritik olaylar için denetim kayıtları, posta öğelerine ne zaman erişildiği, posta öğelerinin ne zaman yanıtlandığı ve iletildiği ya da kullanıcının Exchange Online ve SharePoint Online'da ne zaman ve ne zaman arama yaptığı gibi olaylara görünürlük sağlayarak kuruluşunuzun adli ve uyumluluk araştırmaları gerçekleştirmesine yardımcı olabilir. Bu önemli olaylar olası ihlalleri araştırmanıza ve güvenliğin kapsamını belirlemenize yardımcı olabilir.

- **Office 365 Yönetim Etkinliği API'sine daha yüksek bant genişliği**. Denetim (Premium), kuruluşlara Office 365 Yönetim Etkinliği API'sini kullanarak denetim günlüklerine erişmek için daha fazla bant genişliği sağlar. Denetim (Standart) veya Denetim (Premium) olan tüm kuruluşlara başlangıçta dakikada 2.000 istek temeli ayrılmış olsa da, bu sınır kuruluşun koltuk sayısına ve lisanslama aboneliklerine bağlı olarak dinamik olarak artar. Bu, Denetim (Premium) olan kuruluşların, Denetim (Standart) olan kuruluşlara göre bant genişliğinin yaklaşık iki katını almasına neden olur.

Denetim (Premium) özellikleri hakkında daha ayrıntılı bilgi için bkz. [Microsoft 365'de Denetim (Premium).](advanced-audit.md)

## <a name="comparison-of-key-capabilities"></a>Önemli özelliklerin karşılaştırması

Aşağıdaki tabloda, Denetim (Standart) ve Denetim (Premium) içindeki temel özellikler karşılaştırılıyor. Tüm Denetim (Standart) işlevleri Denetim 'e (Premium) dahil edilir.

|Yeteneği|Denetim (Standart)|Denetim (Premium)|
|:------|:-------------|:-------------|
|Varsayılan olarak etkin|![Desteklenir.](../media/check-mark.png)|![Desteklenir.](../media/check-mark.png)|
|Binlerce aranabilir denetim olayı|![Desteklenir.](../media/check-mark.png)|![Desteklenir.](../media/check-mark.png)|
|Uyumluluk portalında arama aracını denetleme|![Desteklenir.](../media/check-mark.png)|![Desteklenir.](../media/check-mark.png)|
|Search-UnifiedAuditLog cmdlet|![Desteklenir.](../media/check-mark.png)|![Desteklenir.](../media/check-mark.png)|
|Denetim kayıtlarını CSV dosyasına aktarma|![Desteklenir.](../media/check-mark.png)|![Desteklenir.](../media/check-mark.png)|
|Office 365 Yönetim Etkinliği <sup>API'si 1</sup> aracılığıyla denetim günlüklerine erişim|![Desteklenir.](../media/check-mark.png)|![Desteklenir.](../media/check-mark.png)</sup>|
|90 günlük denetim günlüğü saklama|![Desteklenir.](../media/check-mark.png)|![Desteklenir.](../media/check-mark.png)|
|1 yıllık denetim günlüğü saklama||![Desteklenir.](../media/check-mark.png)|
|10 yıllık denetim günlüğü saklama <sup>2</sup>||![Destekleniyor](../media/check-mark.png)|
|Denetim günlüğü saklama ilkeleri||![Destekleniyor](../media/check-mark.png)|
|Yüksek değerli, kritik olaylar||![Destekleniyor](../media/check-mark.png)|

> [!NOTE]
> <sup>1</sup> Denetim (Premium), denetim verilerine daha hızlı erişim sağlayan Office 365 Yönetim Etkinliği API'sine daha yüksek bant genişliği erişimi içerir.<br/><sup>2</sup> Denetim için gerekli lisanslamaya ek olarak (Premium) (sonraki bölümde açıklanmıştır), kullanıcıya denetim kayıtlarını 10 yıl boyunca saklamak için 10 Yıllık Denetim Günlüğü Saklama lisansı atanmış olmalıdır.

## <a name="licensing-requirements"></a>Lisans gereksinimleri

Aşağıdaki bölümlerde Denetim (Standart) ve Denetim (Premium) için lisanslama gereksinimleri belirlenir. Denetim (Standart) işlevi Denetim (Premium) ile birlikte sağlanır.

### <a name="audit-standard"></a>Denetim (Standart)

- Microsoft Purview Business Basic aboneliği
- İş için Uygulamalar aboneliğini Microsoft Purview
- E3 aboneliğini Microsoft Purview Enterprise
- Microsoft Purview İş Premium
- Microsoft Purview Education A3 aboneliği
- Microsoft Purview Kamu G3 aboneliği
- Microsoft Purview Government G1 aboneliği
- Ön Hat F1 veya F3 aboneliğini veya F5 Güvenlik eklentisini Microsoft Purview
- E3 aboneliğini Office 365 Kurumsal
- E1 aboneliğini Office 365 Kurumsal
- A1 aboneliğini Office 365 Eğitim
- A3 aboneliğini Office 365 Eğitim

### <a name="audit-premium"></a>Denetim (Premium)

- E5 aboneliğini Microsoft 365 Kurumsal
- Microsoft 365 Kurumsal E3 aboneliği + Microsoft 365 E5 Uyumluluk eklentisi
- Microsoft 365 Kurumsal E3 aboneliği + Microsoft 365 E5 eBulma ve Denetim eklentisi
- A5 aboneliğini Microsoft 365 Eğitim
- A3 aboneliğini + Microsoft 365 A5 Uyumluluğu eklentisini Microsoft 365 Eğitim
- Microsoft 365 Eğitim A3 aboneliği + Microsoft 365 A5 eKeşif ve Denetim eklentisi
- kamu G5 aboneliğini Microsoft 365
- Microsoft 365 Kamu G3 aboneliği + Microsoft 365 G5 Uyumluluğu eklentisi
- Microsoft 365 Government G3 aboneliği + Microsoft 365 G5 eKeşif ve Denetim eklentisi
- Ön Hat F5 Uyumluluğunu veya F5 Güvenlik & Uyumluluğu eklentisini Microsoft 365
- E5 aboneliğini Office 365 Kurumsal
- A5 aboneliğini Office 365 Eğitim

## <a name="set-up-microsoft-purview-auditing-solutions"></a>Microsoft Purview denetim çözümlerini ayarlama

Microsoft Purview'da denetim çözümlerini kullanmaya başlamak için aşağıdaki kurulum kılavuzuna bakın.

### <a name="set-up-audit-standard"></a>Denetimi (Standart) Ayarlama

İlk adım, Denetim (Standart) ayarlayıp denetim günlüğü aramalarını çalıştırmaya başlamaktır.

![Denetimi ayarlamak için iş akışı (Standart).](../media/BasicAuditingWorkflow.png)

1. Kuruluşunuzun Denetimi (Standart) destekleyen bir aboneliği ve varsa Denetim (Premium) destekleyen bir aboneliği olduğunu doğrulayın.

2. Kuruluşunuzdaki uyumluluk portalında denetim günlüğü arama aracını veya **Search-UnifiedAuditLog** cmdlet'ini kullanacak kişilere Exchange Online izinleri atayın. Özellikle, kullanıcılara Exchange Online View-Only Denetim Günlükleri veya Denetim Günlükleri rolü atanmalıdır.

3. Denetim günlüğünde arama yapın. 1. ve 2. adımı tamamladıktan sonra, kuruluşunuzdaki kullanıcılar denetim günlüğü arama aracını (veya ilgili cmdlet'i) kullanarak denetlenen etkinlikleri arayabilir.

Daha ayrıntılı yönergeler için bkz. [Denetimi Ayarlama (Standart)](set-up-basic-audit.md).

### <a name="set-up-audit-premium"></a>Denetimi (Premium) Ayarlama

Kuruluşunuzun Denetimi (Premium) destekleyen bir aboneliği varsa, Denetim (Premium) bölümündeki ek özellikleri ayarlamak ve kullanmak için aşağıdaki adımları gerçekleştirin.

![Denetimi ayarlamak için iş akışı (Premium).](../media/AdvancedAuditWorkflow.png)

1. Kullanıcılar için Denetimi (Premium) ayarlayın. Bu adım aşağıdaki görevlerden oluşur:

   - Kullanıcılara Denetim (Premium) için uygun lisans veya eklenti lisansı atandığını doğrulama.
  
   - Denetim (Premium) uygulama/hizmet planının bu kullanıcılar için etkinleştirilmesi gerekir.
  
   - Kritik olayların denetimini etkinleştirme ve ardından söz konusu kullanıcılar için Denetim (Premium)uygulama/hizmet planını açma.

2. Kullanıcılar Exchange Online ve SharePoint Online'da arama yaparken Denetim (Premium) olaylarının günlüğe kaydedilmesini etkinleştirin.

3. Denetim günlüğü saklama ilkelerini ayarlayın. Bir yıl boyunca Exchange, SharePoint ve Azure AD denetim kayıtlarını saklayan varsayılan ilkeye ek olarak, kuruluşunuzun güvenlik operasyonları, BT ve uyumluluk ekiplerinin gereksinimlerini karşılamak için ek denetim günlüğü saklama ilkeleri oluşturabilirsiniz.

4. Adli araştırma yaparken kritik Denetim (Premium) olayları ve diğer etkinlikleri arayın. 1. ve 2. adımı tamamladıktan sonra, güvenliği aşılmış hesapların ve diğer güvenlik veya uyumluluk araştırmalarının adli araştırmaları sırasında denetim günlüğünde Denetim (Premium) olayları ve diğer etkinlikler için arama yapabilirsiniz.

Daha ayrıntılı yönergeler için bkz. [Denetimi Ayarlama (Premium)](set-up-advanced-audit.md).

<!--
## Encrypt audit records using Customer Key

You can enable Customer Key encryption for audit records. Auditing builds on the [Service encryption with Customer Key](customer-key-overview.md) to encrypt sensitive information in your organization's auditing data. Implementing Customer Key provides extra protection by preventing unauthorized systems or Microsoft data center personnel from viewing your auditing data in the auditing pipeline and at rest. Using Customer Key to encrypt your auditing data also helps you meet regulatory or compliance obligations because your organization provides and controls the encryption keys.

To implement Customer Key for auditing, you have to create a multi-workload Data Encryption Policy (DEP), which defines the encryption hierarchy. For detailed step-by-step instructions, see [Set up Customer Key](customer-key-set-up.md).

> [!NOTE]
> Not all audit records in your organization are encrypted. The Microsoft Purview service that generates specific audit records for activity in that service defines whether the audit record is encrypted or not.
-->

## <a name="training"></a>Eğitim

Güvenlik operasyonları ekibinize, BT yöneticilerine ve uyumluluk araştırmacıları ekibinize Denetim (Standart) ve Denetim (Premium) ile ilgili temel bilgiler konusunda eğitim vermek, kuruluşunuzun araştırmalarınıza yardımcı olmak için denetimi daha hızlı kullanmaya başlamasına yardımcı olabilir. Microsoft Purview, kuruluşunuzdaki bu kullanıcıların denetime başlamalarına yardımcı olmak için aşağıdaki kaynağı sağlar: [Microsoft Purview eBulma ve denetim özelliklerini açıklama](/learn/modules/describe-ediscovery-capabilities-of-microsoft-365).
