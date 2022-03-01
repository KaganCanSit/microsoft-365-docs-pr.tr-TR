---
title: Microsoft 365 çözümleri deneme sürümü oynatma kitabı
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
audience: Admin
ms.topic: hub-page
ms.service: O365-seccomp
ms.collection: m365-security-compliance
ms.localizationpriority: high
ROBOTS: NOINDEX, NOFOLLOW
search.appverid:
- MOE150
- MET150
description: Microsoft 365 çözümleri deneme sürümü oynatma kitabınız.
ms.openlocfilehash: fc04e5d745997e31799511d4a9edb7e7207f4088
ms.sourcegitcommit: 954c8af658adb270fe843991e048c6a30e86e77c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2022
ms.locfileid: "63016477"
---
# <a name="trial-playbook-microsoft-365-compliance-solutions"></a>Deneme oynatma kitabı: Microsoft 365 Uyumluluk çözümleri

Uyumluluk çözümleri deneme Microsoft 365 defterine hoş geldiniz. Bu çalışma kitabı, uyumluluk ve güvenlik ürünlerinin güçlü ve kapsamlı özelliklerini keşfetmenize yardımcı olarak 90 günlük ücretsiz denemenizi en Microsoft 365 yardımcı olur.

Her çözümün  çalışıyor olması, kuruluşun uyumluluk  gereklerini karşılamak için bilinçli kararlar ademeye yardımcı olur.

Özellikler:

- [Gelişmiş Denetim](#advanced-audit)
- [İletişim Uyumluluğu](#communication-compliance)
- [Uyumluluk Yöneticisi](#compliance-manager)
- [Veri Kaybını Önleme](#data-loss-prevention)
- [eKbulma](#ediscovery)
- [Bilgi Koruması](#information-protection)
- [Insider Risk Yönetimi](#insider-risk-management)
- [Kayıt Yönetimi](#records-management)

İsteğe bağlı eklentiler:

- [Uyumluluk Yöneticisi premium değerlendirmeleri](#compliance-manager-premium-assessments)
- [Microsoft Priva Gizlilik Risk Yönetimi ve Microsoft Priva Konu Hakları İstekleri](#microsoft-priva-privacy-risk-management-and-microsoft-priva-subject-rights-requests)

## <a name="compliance-actions-with-microsoft-365"></a>Uyumluluk eylemleri ve Microsoft 365

Microsoft'un uyumluluk çözümlerini, kuruluşun meta verilerini değiştirmeden kolayca ve hızla deneyin. Önceliklerinize bağlı olarak, hemen değeri görmek için bu çözüm alanlarından herhangi biri ile başlayabilirsiniz. Aşağıda, müşterilerimiz tarafından iletilecek kurumsal kaygılar ve başlangıç olarak önerilen beş çözüm verilmiştir.

:::image type="content" source="../media/compliance-trial/workflow.png" alt-text="Uyumluluk eylemleri ve Microsoft 365":::

## <a name="advanced-audit"></a>Gelişmiş Denetim

**Soruşturma yürütme**

Gelişmiş Denetim, araştırma yapmak için gereken denetim günlüğü bekletmesini artırarak, güvenlik ve uyumluluk kapsamını belirlemeye yardımcı olan önemli olaylara erişim sağlayarak ve güvenlik güvenliğinin kapsamını daha hızlı belirleyerek denetim günlüğü bekletmesini artırarak kuruluşların denetim ve uyumluluk Office 365 yardımcı olur.

### <a name="step-1-apply-the-e5-license-to-each-user-for-which-youd-like-to-generate-e5-events"></a>1 [. Adım: E5 olaylarını oluşturmak için her kullanıcıya E5 lisansını uygulama](set-up-advanced-audit.md#step-1-set-up-advanced-audit-for-users)

> [!TIP]
> Deneme için en iyi yöntem: 1. Gün

MailItemsAccessed ve Send gibi önemli olayları günlüğe yazma yeteneği gibi gelişmiş Denetim özellikleri, kullanıcılara uygun bir E5 lisansı atamayı gerektirir. Buna ek olarak, bu kullanıcılar için Gelişmiş Denetim uygulaması/hizmet planı da etkinleştirilmelidir.

Kullanıcılar için Gelişmiş Denetim'i ayarlama - Kullanıcılara Gelişmiş Denetim uygulamasının atandığı doğrulamak için, her kullanıcı [için aşağıdaki adımları gerçekleştirin](set-up-advanced-audit.md#step-1-set-up-advanced-audit-for-users).

1. Gelişmiş Denetim olaylarını etkinleştirme - Exchange Online [PowerShell'de](/powershell/exchange/connect-to-exchange-online-powershell) her kullanıcı için [SearchQueryInitiatedExchange ve SearchQueryInitiatedSharePoint'i](set-up-advanced-audit.md#step-2-enable-advanced-audit-events) etkinleştirin.
1. Denetim bekletme ilkelerini ayarlama - [kuruluş güvenlik işlemlerinin](set-up-advanced-audit.md#step-3-set-up-audit-retention-policies) , IT'lerinin ve uyumluluk ekiplerinin gereksinimlerini karşılamak için ek denetim günlüğü bekletme ilkeleri oluşturun.
1. Gelişmiş Denetim olaylarını arama - [Araştırma araştırmalarını yürüten çok önemli](set-up-advanced-audit.md#step-4-search-for-advanced-audit-events) Gelişmiş Denetim olaylarını ve diğer etkinlikleri arama.

### <a name="step-2-create-new-audit-log-policies-to-specify-how-long-to-retain-audit-logs-in-your-org-for-activities-performed-by-users-and-define-priority-levels-for-your-policies"></a>2. Adım: Kullanıcılar tarafından gerçekleştirilen etkinlikler için kuruluşta denetim günlüklerinin ne kadar süreyle tutularak gerçekleştirileceklerini belirtmek ve ilkeleriniz için öncelik düzeyleri tanımlamak üzere yeni [Denetim Günlüğü ilkeleri oluşturun](audit-log-retention-policies.md#before-you-create-an-audit-log-retention-policy)

> [!TIP]
> Deneme için en iyi yöntem: İlk 30 gün içinde oluşturun

Denetim günlüğü bekletme ilkeleri, denetim ilkesi yönetimi kapsamındaki yeni Gelişmiş Denetim Microsoft 365. Denetim günlüğü bekletme ilkesi, denetim günlüklerinin kurumda ne kadar süreyle tutula tutula tutula açık olduğunu belirtmenize olanak sağlar.

1. Denetim günlüğü bekletme ilkesi oluşturmadan önce, [ilkenizi oluşturmadan önce bunu](audit-log-retention-policies.md#before-you-create-an-audit-log-retention-policy) bilmek gereken önemli şeyler vardır.
1. [Denetim günlüğü bekletme ilkesi oluşturma](audit-log-retention-policies.md#create-an-audit-log-retention-policy)
1. [Denetim günlüğü bekletme ilkelerini yönetme Microsoft 365 uyumluluk merkezi](audit-log-retention-policies.md#manage-audit-log-retention-policies-in-the-microsoft-365-compliance-center) - Denetim günlüğü bekletme ilkeleri, Denetim bekletme ilkeleri sekmesinde (pano olarak da denir) listelenir. Denetim bekletme ilkelerini görüntülemek, düzenlemek ve silmek için panoyu kullanabilirsiniz.
1. PowerShell'de denetim günlüğü bekletme ilkelerini oluşturma ve yönetme - Denetim günlüğü bekletme ilkelerini oluşturmak ve yönetmek için Güvenlik & Uyumluluk Merkezi [PowerShell'i de kullanabilirsiniz](audit-log-retention-policies.md#create-and-manage-audit-log-retention-policies-in-powershell). PowerShell'i kullanmanın bir nedeni, kullanıcı arabiriminde olmayan bir kayıt türü veya etkinliği için ilke oluşturmaktır.

## <a name="communication-compliance"></a>İletişim Uyumluluğu

**Yürütme ilkesi ihlallerini tanımlama ve bu ihlallere karşı harekete geç**

İletişim uyumluluğu, uygun olmayan iletileri algılamanıza, olası ilke ihlallerini araştırmanıza ve düzeltmek için adımlar atarak uyumlu ve sağlıklı bir çalışma ortamını desteklemeye yardımcı olmak için iletişim ihlallerini akıllı bir şekilde tanımlamanıza yardımcı olur.

### <a name="step-1-enable-permissions-for-communication-compliance"></a>1. Adım: [İletişim uyumluluğu için izinleri etkinleştirme](communication-compliance-configure.md#step-1-required-enable-permissions-for-communication-compliance)

> [!TIP]
> Deneme için en iyi yöntem: 1. Gün

[Tüm uyumluluk kullanıcılarını İletişim Uyumluluğu rol grubuna attayabilirsiniz](communication-compliance-configure.md#step-1-required-enable-permissions-for-communication-compliance).
### <a name="step-2-enable-the-audit-log"></a>2. Adım: [Denetim günlüğünü etkinleştirme](communication-compliance-configure.md#step-2-required-enable-the-audit-log)

> [!TIP]
> Deneme için en iyi uygulama: İlk 30 gün içinde kurulum

Bu özelliği kullanmak için, denetimi açarak kuruluşta kullanıcı ve yönetici etkinliğini kaydetmeye başlaysını seçin. Bunu açabilirsiniz, etkinlik denetim günlüğüne kaydedilir ve raporda ilebilir. Daha fazla bilgi edinmek için [bkz. Denetim günlüğü aramalarını açma veya kapatma](turn-audit-log-search-on-or-off.md).

### <a name="step-3-create-a-communication-compliance-policy"></a>3. Adım [: İletişim uyumluluk ilkesi oluşturma](communication-compliance-policies.md)

[Mevcut şablonları kullanarak iletişim uyumluluk ilkesi oluşturma](communication-compliance-policies.md): 1- Uygunsuz içerik; 2- Hassas bilgiler; 3- Yasal düzenlemelere uyum; 4- Faiz çakışması.

### <a name="step-4-investigate-and-remediate-alerts"></a>4. Adım: [Uyarıları araştırma ve düzeltme](communication-compliance-investigate-remediate.md)

[İletişim uyumluluk uyarılarını araştırarak](communication-compliance-investigate-remediate.md) düzeltmek.

## <a name="compliance-manager"></a>Uyumluluk Yöneticisi

**Kuruluş uyumluluğunızı kolayca yönetin**

Uyumluluk Yöneticisi, veri koruma risklerinizi envanterini almaktan denetimleri uygulamanın karmaşıklıklarını yönetmeye, yasal düzenlemeler ve sertifikalarla güncel kalmanıza ve denetçilere bildirmeye kadar uyumluluk yolculuğunuz boyunca size yardımcı olabilir.

### <a name="step-1-get-to-know-compliance-manager"></a>1. Adım: [Uyumluluk Yöneticisi'ni hakkında bilgi](compliance-manager-quickstart.md#first-visit-get-to-know-compliance-manager)

> [!TIP]
> Deneme için en iyi yöntem: 1. Gün

Uyumluluk Yöneticisi genel bakış sayfamız, Uyumluluk Yöneticisi'nin ne olduğunu ve nasıl çalıştığını kapsamlı bir şekilde gözden geçirmek için ilk durakdır. Aşağıdaki bağlantıları kullanarak belgelerimizin önemli bölümlerine de geçebilirsiniz:

- [Uyumluluk puanınızı anlama](compliance-manager.md#understanding-your-compliance-score)
- [Önemli öğelere genel bakış: denetimler, değerlendirmeler, şablonlar ve geliştirme eylemleri](compliance-manager.md#key-elements-controls-assessments-templates-improvement-actions)
- [Uyumluluk Yöneticisi panosunun ne olduğunu anlama](compliance-manager-setup.md#understand-the-compliance-manager-dashboard)
- [Pano görünüme filtre uygulama](compliance-manager-setup.md#filtering-your-dashboard-view)
- [Geliştirme eylemleri hakkında bilgi](compliance-manager-setup.md#improvement-actions-page)
- [Değerlendirmeleri anlama](compliance-manager.md#assessments)
- [Microsoft Uyumluluk Yapılandırma Yöneticisi'ni kullanarak ortamınızı hızlı bir şekilde tarama](compliance-manager-mcca.md)

![Uyumluluk Yöneticisi - pano.](../media/compliance-manager-dashboard.png "Uyumluluk Yöneticisi panosu")

### <a name="step-2-configure-compliance-manager-to-manage-your-compliance-activities"></a>2. Adım: [Uyumluluk etkinliklerinizi yönetmek için Uyumluluk Yöneticisi'ni yapılandırma](compliance-manager-assessments.md)

> [!TIP]
> Deneme için en iyi uygulama: İlk 30 gün içinde denetleme

Değerlendirmelerle çalışmaya ve denetimleri uygulamaya ve uyumluluk puanınızı iyileştirmeye ilişkin iyileştirme eylemleri yapmaya başlayabilirsiniz.

1. [İlk değerlendirmenizi oluşturmak ve yönetmek için önceden yerleşik bir şablon seçin](compliance-manager-assessments.md).
1. [Değerlendirme oluşturmak için şablonların nasıl kullanıla olduğunu anlıyoruz](compliance-manager-templates.md).
1. [Değerlendirmelerizdeki denetimleri tamamlamak için geliştirme eylemleri üzerinde uygulama ve test çalışmaları gerçekleştirin](compliance-manager-improvement-actions.md).
1. [Farklı eylemlerin uyumluluk puanınızı nasıl etkileyeni daha iyi anlıyoruz](compliance-score-calculation.md).

> [!NOTE]
> Microsoft 365 veya Office 365 E1 E3 aboneliği Microsoft Veri Koruma Temel şablonu içerir. Microsoft 365 veya Office 365 E5, E5 Uyumluluğu aşağıdakiler için şablonlar içerir:
>
> - Microsoft Veri Koruma Temeli
> - Avrupa Birliği GDPR  
> - ISO/IEC 27001,
> - NIST 800-53
>
> Uyumluluk Yöneticisi, eklenti olarak satın alınan 300'den fazla mevzuat veya premium şablon içerir. Listeye buradan bakın. Herhangi bir premium şablonla (aboneliğinize dahil olan veya eklenti olarak satın alınan şablonlar) bu şablonların evrensel sürümünü alırsınız ve bu da herhangi bir ürün veya hizmetle uyumluluğunu yönetmenize olanak sağlar

### <a name="step-3-scaling-up-use-advanced-functionality-to-meet-your-custom-needs"></a>3. Adım: [Ölçeklendirme: Özel ihtiyaçları karşılamak için gelişmiş işlevselliği kullanma](compliance-manager-templates-create.md)

Özel değerlendirmeler şunların için yararlıdır:

- Üçüncü taraf uygulamaları ve Microsoft 365, şirket içi uygulamalar ve diğer varlıklar gibi üçüncü taraf ürünleri için uyumluluğu yönetme
- Kendi özel veya işletmeye özgü uyumluluk denetimlerinizi yönetme

1. [Kendi denetimlerinizi ve geliştirme eylemlerinizi ekleyerek Uyumluluk Yöneticisi şablonunu genişletme](compliance-manager-templates-extend.md)
1. [Kendi özel şablonlarınızı oluşturma](compliance-manager-templates-create.md)
1. [Denetimleri ve eylemleri eklemek veya kaldırmak için var olan şablonu değiştirme](compliance-manager-templates-modify.md)
1. [Geliştirme eylemlerinin otomatik testlerini ayarlama](compliance-manager-setup.md#set-up-automated-testing)
1. [Geliştirme eylemlerini başka bir kullanıcıya yeniden atama](compliance-manager-setup.md#reassign-improvement-actions-to-another-user)

## <a name="data-loss-prevention"></a>Veri Kaybını Önleme

**Hassas verileri koruma**

İş standartları ve endüstri yönetmeliklerine uygun olması için, kuruluşların yanlışlıkla açıklanmasını önlemek için hassas bilgileri korumaları gerekir. Tüm iş yer genelinde hassas bilgileri tanımlamak, izlemek ve otomatik olarak korumak için veri kaybı önleme Microsoft 365.

### <a name="step-1-protect-data-loss-on-teams-locations"></a>1. Adım: [Konumlarda veri Teams koruma](dlp-microsoft-teams.md#dlp-licensing-for-microsoft-teams)

> [!TIP]
> Deneme için en iyi yöntem: 1. Gün

Kuruluşta veri kaybı önleme (DLP) varsa, bir kanalda veya sohbet oturumunda kişilerin hassas bilgileri paylaşmasını Microsoft Teams ilkeler tanımlayabilirsiniz.

1. DLP [Lisanslama Lisansları hakkında Microsoft Teams ve DLP koruma kapsamı hakkında bilgi](dlp-microsoft-teams.md#dlp-licensing-for-microsoft-teams)
1. [Varolan Microsoft Teams DLP ilkelerine konum olarak ekleme](dlp-microsoft-teams.md#add-microsoft-teams-as-a-location-to-existing-dlp-policies)
1. [Varsayılan DLP ilkemizi daha iyi Teams](mip-easy-trials.md) [DLP ilkesi tanımlama veya DLP için yeni bir DLP Microsoft Teams](dlp-microsoft-teams.md#define-a-new-dlp-policy-for-microsoft-teams)

### <a name="step-2-protect-data-loss-on-device-locations"></a>2. Adım: [Cihaz konumlarda veri kaybını koruma](endpoint-dlp-getting-started.md)

> [!TIP]
> Deneme için en iyi uygulama: İlk 30 gün içinde kurulum

Microsoft Endpoint DLP, en son cihazları Windows 10 hassas öğelerin ne zaman kullanılmış ve paylaşılıyor olduğunu algılamaya olanak tanır.

1. Uç noktalarınızı hazırlama - Bu gereksinimleri karşılamak Windows 10 Uç Nokta DLP'yi dağıtmayı planlayınız Windows 10 macOS cihazlarının [](endpoint-dlp-getting-started.md)
1. [Cihazları cihaz yönetimine ekleme](endpoint-dlp-getting-started.md)  - Bir cihazdaki hassas öğeleri izlemek ve korumak için önce cihaz izlemeyi etkinleştirmeniz ve uç noktaları eklemeniz gerekir. Bu eylemlerin ikisi de Uyumluluk Portalı'Microsoft 365 yapılır.
   - Senaryo 1 – [Henüz](endpoint-dlp-getting-started.md) eklememiş olan ekleme cihazları.
   - Senaryo 2 - [Uç Nokta için Microsoft Defender zaten dağıtılır ve raporlama uç noktaları vardır](endpoint-dlp-getting-started.md). Tüm bu uç noktalar yönetilen cihazlar listesinde görünür.
1. [Cihazlar için varsayılan DLP ilkemizi yapılandırma veya](mip-easy-trials.md#dlp-for-devices) [Cihazlar için yeni DLP ilkesi tanımlama](endpoint-dlp-learn-about.md).
1. [DLP Uyarıları Yönetimi panosunda](dlp-configure-view-alerts-policies.md) Uç Nokta DLP uyarılarını görüntüleme.
1. [Etkinlik gezgininde Uç Nokta DLP](data-classification-activity-explorer.md) verilerini görüntüleme.

### <a name="step-3-expand-policies-in-scope-or-protection"></a>3. Adım: [Kapsam veya korumada ilkeleri genişletme](dlp-learn-about-dlp.md#dlp-policy-configuration-overview)

DLP ilkelerinizi yapılandırma esnekliğiniz vardır. Daha fazla konumu, hassas bilgi türlerini veya etiketleri korumak Teams için varsayılan DLP ilkemizi kullanarak başlayabilir ve bu ilkeleri genişletebilirsiniz. Ayrıca, ilke eylemlerine göre genişletebilirsiniz ve uyarıyı özelleştirebilirsiniz.

1. Konum ekleme
1. Korumak için hassas bilgi türleri veya etiketleri ekleme
1. Eylem ekleme
   - Teams:
      - [Hassas belgelere dış erişimi engelleme](dlp-microsoft-teams.md#prevent-external-access-to-sensitive-documents)
      - [Kullanıcıları eğitip ilke ipuçlarını özelleştirme yönergelerini almaya yardımcı olacak ilke ipuçları al](dlp-microsoft-teams.md#policy-tips-help-educate-users)
   - Cihazlar: yalnızca denetimden engellemeye geçiş
1. [Veri kaybı önleme ilkeleri için uyarıları yapılandırma ve görüntüleme - Uyumluluk Microsoft 365'| Microsoft Docs](dlp-configure-view-alerts-policies.md)

## <a name="ediscovery"></a>eKbulma

**Uçtan  uç iş akışıyla daha fazlasını keşfetme**

Kuruluşun iç ve dış soruşturmalarına yanıt veren içerikleri korumak, toplamak, çözümlemek ve dışarı aktarmak için  uç iş akışılardan faydalanın. Yasal ekipler, bir olaya dahil olan koruyucularla iletişim kurarak yasal tutma bildirimi işleminin tamamını yönetebilir.

### <a name="step-1-required-permissions"></a>1. Adım (gerekli): [İzinler](https://aka.ms/ediscoveryninja)

> [!TIP]
> Deneme için en iyi yöntem: 1. Gün

Kullanıcıya Advanced eDiscovery veya bir davanın üyesi olarak Advanced eDiscovery için, kullanıcıya uygun izinler atanabilir.

1. [EBulma Advanced eDiscovery ayarlama – eBulma izinleri atama](get-started-with-advanced-ediscovery.md#step-2-assign-ediscovery-permissions)
1. [Vakaya üye ekleme veya vakadan üye kaldırma](add-or-remove-members-from-a-case-in-advanced-ediscovery.md)

### <a name="step-2-required-create-a-case"></a>2. Adım (gerekli): Olay oluşturma

> [!TIP]
> Deneme için en iyi yöntem: İlk 30 gün içinde oluşturun

Diğer kuruluşlar kritik eK Advanced eDiscovery için Microsoft 365 çözümlerini bu çözümde kullanır. Bu düzenlemelere ilişkin taleplere, soruşturmalara ve mahkemelere yanıt vermeyi kapsar.

1. Posta Advanced eDiscovery Yönetme – Güvenlik Advanced eDiscovery Uyumluluk Merkezi'& kullanarak vakaları [yapılandırmayı, Advanced eDiscovery'te](/learn/modules/manage-advanced-ediscovery) iş akışını yönetmeyi ve arama sonuçlarını çözümlemeyi Advanced eDiscovery öğrenin.
1. [eBulma'nın yeni vaka biçimini ilerlet'i kullanarak eBulma vakası oluşturma](advanced-ediscovery-new-case-format.md)
1. [Vakayı kapatma veya silme](close-or-delete-case.md) - Dava veya soruşturma tamamlandığında, vakayı veya soruşturmayı kapatarak veya silebilirsiniz. Ayrıca, kapalı bir vakayı yeniden açılmıştır.

### <a name="step-3-optional-settings"></a>3. Adım (isteğe bağlı): Ayarlar

Kuruluşların kişilerin vakaları oluşturmasına ve kullanmaya başlamasına izin vermek için, kuruluşun tüm örnekleri için geçerli olan genel ayarları yapılandırmanız gerekir. Şu anda tek genel ayar avukat-istemci ayrıcalık algılaması **özelliğidir** (gelecekte daha fazla genel ayar kullanılabilir).

1. [Genel Advanced eDiscovery'i Ayarlar](get-started-with-advanced-ediscovery.md#step-3-configure-global-settings-for-advanced-ediscovery)
1. [Arama ve çözümleme ayarlarını yapılandırma](configure-search-and-analytics-settings-in-advanced-ediscovery.md)
1. [İş yerlerinde işleri Advanced eDiscovery](managing-jobs-ediscovery20.md)

### <a name="step-4-optional-compliance-boundaries"></a>4. Adım (isteğe bağlı): [Uyumluluk Sınırları](set-up-compliance-boundaries.md)

Uyumluluk sınırları, eBulma yöneticilerinin aray kontrolü yaptığı kullanıcı içerik konumlarını (posta kutuları, OneDrive hesapları ve SharePoint siteleri gibi) kontrol altına alan bir kuruluş içinde mantıksal sınırlar oluşturabilir. Ayrıca, kuruluş içinde yasal, insan kaynakları veya diğer soruşturmaları yönetmek için kullanılan eBulma olaylarına kimlerin eriş erişeni de kontrol etmek için kullanılırlar.

![Uyumluluk sınırları, eBulma durumlarına erişimi denetim altına alan kuruluşlara ve yönetici rolü gruplarına erişimi denetim altına alan arama izinleri filtrelerinden oluşur.](../media/M365_ComplianceBoundary_OrgChart_v2.png)

eBulma soruşturmaları için uyumluluk sınırlarını ayarlayın:

1. [Kuruluşları tanımlamak için bir kullanıcı özniteliği belirleme](set-up-compliance-boundaries.md#step-1-identify-a-user-attribute-to-define-your-agencies)
1. [Her acente için bir rol grubu oluşturma](set-up-compliance-boundaries.md#step-2-create-a-role-group-for-each-agency)
1. [Uyumluluk sınırını zorunlu aramak için arama izinleri filtresi oluşturma](set-up-compliance-boundaries.md#step-3-create-a-search-permissions-filter-to-enforce-the-compliance-boundary)
1. [Bir şirket içi soruşturmalar için eBulma vakası oluşturma](set-up-compliance-boundaries.md#step-4-create-an-ediscovery-case-for-intra-agency-investigations)

### <a name="step-5-optional-learn-about-content-search-tool"></a>5. Adım (isteğe bağlı): [İçerik arama aracı hakkında bilgi](search-for-content.md)

Microsoft 365 uyumluluk merkezi posta kutularında, SharePoint sitelerinde ve Exchange OneDrive konumlarında e-postayı, Skype Kurumsal'te anlık ileti konuşmalarını hızlı bir şekilde bulmak için Skype Kurumsal. İçerik arama aracını kullanarak, Grup Sohbetleri ve Grupları Birleştirme gibi işbirliği araçlarında e-postaları, belgeleri ve anlık Microsoft Teams Microsoft 365 kullanabilirsiniz.

- [Arama hakkında daha Advanced eDiscovery bilgi](search-for-content.md#search-for-content)

## <a name="information-protection"></a>Bilgi Koruması

**Hassas bilgileri keşfetme, sınıflandırma ve koruma**

Hassas Microsoft Bilgi Koruması içinde yer alan veya seyahat her yerde bu içeriği bu şekilde sınıflandırmanıza ve korumanıza yardımcı olmak için, daha fazla etiket ve duyarlılık etiketi kullanın.

### <a name="step-1-start-your-information-protection-trial"></a>1. Adım: [Bilgi koruma denemenizi başlatma](mip-easy-trials.md)

> [!TIP]
> Deneme için en iyi yöntem: 1. Gün

Uygun müşteriler, iş için varsayılan etiketleri ve Microsoft Bilgi Koruması. Denemede varsayılan yapılandırmayı etkinleştirirken, kiracınız için tüm ilkelerin yapılandırılması yaklaşık 2 dakika sürer ve bu varsayılan ilkelerin sonuçlarını görmek 24 saate kadar sürer.

Varsayılan yapılandırmayı seçin ve tek tıklamayla aşağıdakiler otomatik olarak yapılandırılır:

- Duyarlılık etiketleri ve duyarlılık etiketi ilkesi
- İstemci tarafı otomatik etiketleme
- Hizmet tarafı otomatik etiketleme
- Verileri ve cihazlarınız için veri kaybı önleme (DLP) Teams ilkeleri

[Varsayılan etiketleri ve ilkeleri etkinleştirme](mip-easy-trials.md#activate-the-default-labels-and-policies). Gerekirse, yapılandırma tamamlandıktan sonra el ile düzenleyebilirsiniz.

### <a name="step-2-automatically-apply-sensitivity-labels-to-documents"></a>2. Adım: [Belgelere duyarlılık etiketlerini otomatik olarak uygulama](apply-sensitivity-label-automatically.md)

> [!TIP]
> Deneme için en iyi uygulama: İlk 30 gün içinde kurulum

Duyarlılık etiketi  oluşturduktan sonra, belirttiğiniz koşullarla eşleşen dosyalara ve e-postalara otomatik olarak bu etiketi atabilirsiniz.

1. [Duyarlılık etiketlerini oluşturma ve yapılandırma](create-sensitivity-labels.md#create-and-configure-sensitivity-labels)
1. [Tüm kullanıcılara duyarlılık etiketi ilkesi yayımlama](create-sensitivity-labels.md#publish-sensitivity-labels-by-creating-a-label-policy)
1. [Otomatik etiketleme ilkesi oluşturma](create-sensitivity-labels.md#publish-sensitivity-labels-by-creating-a-label-policy)
   - Etiketin uygulanmalarını istediğiniz bilgileri seçin
   - Etiket uygulanacak konumları tanımlama
   - Uygulanacak etiketi seçin
   - [Benzetim modunda çalıştırma ilkesi](create-sensitivity-labels.md#publish-sensitivity-labels-by-creating-a-label-policy)

![Otomatik etiketleme için yeni ilke yapılandırması.](../media/auto-labeling-wizard.png)

### <a name="step-3-review-and-turn-on-auto-labeling-policy"></a>3. Adım: [Otomatik etiketleme İlkesini gözden geçirme ve açma](apply-sensitivity-label-automatically.md#how-to-configure-auto-labeling-policies-for-sharepoint-onedrive-and-exchange)

Information **protectionAuto-labeling**  >  sayfasında, otomatik etiketleme ilkenizi Benzetim **bölümünde görebilirsiniz**.

Yapılandırma ve durum ayrıntılarını görmek için ilkenizi seçin. Benzetim tamamlandığında, hangi e-posta veya belgelerin belirtilen kurallarla eş olduğunu görmek için Gözden geçirlanacak öğeler sekmesini seçin.

Benzetim olmadan ilkeyi çalıştırmaya hazırsanız, **İlkeyi aç seçeneğini** belirleyin.

## <a name="insider-risk-management"></a>Insider Risk Yönetimi

**Insider risklerini algılama ve düzeltme**

şirket içi riskleri hızlı bir şekilde tanımlamanıza, dengelemeye ve düzeltmeye yardımcı olacak yapay zekadan faydalanabilirsiniz. Microsoft 365 Azure hizmetlerinden günlükleri kullanarak, insider risk sinyallerini izleten ilkeler tanımlayabilir ve sonra kullanıcı eğitiminin tanıtımını alma veya bir araştırmanın başlatıldığı gibi düzeltme eylemleri gerçekleştirebilirsiniz.

### <a name="step-1-required-enable-permissions-for-insider-risk-management"></a>1. Adım (gerekli): [Insider risk yönetimi için izinleri etkinleştirme](insider-risk-management-configure.md#step-1-required-enable-permissions-for-insider-risk-management)

> [!TIP]
> Deneme için en iyi yöntem: 1. Gün

Insider risk yönetimi özelliklerini yönetmek için izinleri yapılandırmak için kullanılan dört rol grubu vardır.

[Kullanıcıları bir Insider risk yönetimi rol grubuna ekleyin.](insider-risk-management-configure.md#add-users-to-an-insider-risk-management-role-group)

İzinleri görmüyorsanız doğru rolleri atamak için lütfen kiracı yöneticinizle iletişime gidin.

### <a name="step-2-start-with-user-quick-start-guide"></a>2. Adım: [Kullanıcı hızlı başlangıç kılavuzu ile başlama](insider-risk-management-configure.md#recommended-actions-preview)

Hızlı bir şekilde işe başlandı ve önerilen eylemlerle Insider risk yönetimi yeteneklerine en iyi şekilde sahip olun. Genel Bakış sayfasında yer alan önerilen eylemler, ilkeleri yapılandırma ve dağıtma ve ilke eşleşmelerinden uyarı oluşturan kullanıcı eylemleri için soruşturma eylemlerine yönelik işlemlerde size yol bu konuda yol yardımcı olur.

[Insider risk yönetimini yapılandırmaya](insider-risk-management-configure.md#recommended-actions-preview) başlamaya başlama için listeden bir öneri seçin.

![Insider risk yönetimi önerilen eylemler.](../media/insider-risk-recommended-actions.png)

Önerilen her eylem, gereksinimleri, neler beklemeniz gerekenler ve özelliğin kuruluş içinde yapılandırılma etkisini de içinde olmak üzere, öneriye yönelik gerekli etkinliklerde size yol sunar.

### <a name="step-3-required-enable-the-microsoft-365-audit-log"></a>3. Adım (gerekli): [Denetim Microsoft 365 etkinleştirme](insider-risk-management-configure.md#step-2-required-enable-the-microsoft-365-audit-log)

Bu kuruluşlarda denetim Microsoft 365 varsayılan olarak etkinleştirilir. Bazı kuruluşlar belirli nedenlerle denetimi devre dışı bırakmıştır. If auditing is disabled for your organization, it might be because another administrator has turned it. Bu adımı tamamlarken denetimi yeniden açmanın bir sorun olduğunu doğrulamanızı öneririz.

Denetimi açma adım adım yönergeler için bkz. [Denetim günlüğü aramalarını açma veya kapatma](turn-audit-log-search-on-or-off.md). Denetimi açmak için denetim günlüğünün hazır olduğunu ve birkaç saat içinde hazırlık tamamlandıktan sonra arama çalıştırabilirsiniz iletisi görüntülenir. Bu eylemi yalnızca bir kez yapmak gerekir. Denetim günlüğünü kullanma hakkında daha fazla Microsoft 365 için bkz. [Denetim günlüğünde arama.](search-the-audit-log-in-security-and-compliance.md)

### <a name="step-4-required-enable-and-view-insider-risk-analytics-insights"></a>4. Adım (gerekli): [Insider risk analizi içgörülerini etkinleştirme ve görüntüleme](insider-risk-management-configure.md#step-3-optional-enable-and-view-insider-risk-analytics-insights)

Insider risk yönetimi analizi, insider risk ilkelerini yapılandırmadan, organizasyonda olası insider risklerini değerlendirmenizi sağlar. İncelemelerin rapor olarak gözden geçirilmeden önce analiz tarama sonuçları 48 saat kadar sürebilir. Analiz içgörüleri hakkında daha fazla bilgi edinmek için [Insider risk yönetimi ayarları: Analiz (önizleme)](insider-risk-management-settings.md) ve [Insider Risk Management Analytics videosunu inceleyin. Insider risk](https://www.youtube.com/watch?v=5c0P5MCXNXk) durumlarınızı anlamanıza yardımcı olur ve riskli kullanıcıları tanımlamak için uygun ilkeleri ayarerek önlem ayasınız.

Insider risk Analytics'i etkinleştirmek için Insider Risk Yönetimi veya Insider Risk Yönetimi Yöneticisi'ne üye olmak gerekir. Insider risk analizini etkinleştirmek için [bu adımları tamamlayın](insider-risk-management-configure.md).

## <a name="records-management"></a>Kayıt Yönetimi

**İş açısından kritik kayıtlar için bekletme zamanlamayı otomatikleştirme**

Kurumsal düzenlemeler, yasal ve iş açısından kritik kayıtlar için bekletme zamanlamayı otomatikleştirmek üzere tümleşik Kayıt Yönetimi özelliklerini kullanın. Oluşturmadan işbirliğine, kayıt bildiriminden bekletmeye ve yok durumuna kadar tüm içerik yaşam döngüsü desteği elde edin.

### <a name="step-1-dynamically-target-retention-policies-with-adaptive-policy-scopes"></a>1. Adım: Uyarlanabilir İlke Kapsamları olan dinamik olarak hedef bekletme ilkeleri

> [!TIP]
> Deneme için en iyi yöntem: 1. Gün

Uyarlanabilir ilke kapsamları, belirli kullanıcılara, gruplara veya sitelere AD özniteliklerine göre dinamik olarak bir ilke hedeflemeniz için olanak sağlar.

Kapsamlar için öznitelikler listeden seçilebilir veya gelişmiş sorgu oluşturucusu kullanılarak özelleştirilebilir.

Uyarlamalı ilke kapsamlarını kullanan ilkeler, kuruluş, katılan veya katılan yeni çalışanlarla değiştikleriyle güncel kalır. Buna ek olarak, ilkeye dahil edilen 100/1000 konum önceki sınırlara tabi değildir.

- Uyarlanabilir [İlke Kapsamı](retention.md#adaptive-or-static-policy-scopes-for-retention) oluşturma ve bu kapsamı bekletme ilkesiyle kullanma

### <a name="step-2-automate-labeling-of-sensitive-information-with-the-ability-to-review-before-disposal"></a>2. Adım: Hassas bilgilerin etiketlerini, dağıtımdan önce gözden geçirme özelliğiyle otomatikleştirme

> [!TIP]
> Deneme için en iyi uygulama: İlk 30 gün içinde kurulum

Bekletme etiketleri, kredi kartı numarası gibi hassas bilgiler algılayan içeriğe otomatik olarak uygulanacak şekilde ayarlanmış olabilir. Böylece, kullanıcıların etiket etkinliğini el ile gerçekleştirmesi gerekmez.

Bekletme döneminin sonunda, belirttiğiniz kullanıcılara ("gözden geçirenler") içeriği gözden geçirmeleri ve kalıcı olarak kaldırma eylemlerini onaylamaları için bir bilgi verilir. Bu şekilde, bir şeyin daha uzun süre tutul olması gerekirse, böyle olabilir.

Etiket uygulaması etkinliği ve disposition gözden geçirme etkinliğinin her ikisi de Kayıt Yönetimine Genel Bakış ekranından ılamaz.

1. [Hassas bilgiler içeren içeriğe bekletme etiketlerini otomatik olarak uygulama](retention.md#retention-labels)
1. Bekletme döneminin sonunda konumlandırma [incelemesiyle bir](disposition.md#disposition-reviews) bekletme etiketi oluşturma ve uygulama

### <a name="step-3-label-content-as-records-automatically-using-trainable-classifiers"></a>3. Adım: Eğitilebilir sınıflayıcıları kullanarak içeriği otomatik olarak kayıt olarak etiketleme

İçerik kayıt olarak bildirildikten sonra, öğeye izin verilen veya engellenen eylemler, öğelerle ilgili ek etkinlikler günlüğe kaydedilir ve bekletme döneminin sonunda öğeler silinirse silinme kanıtınız olur.

Eğitilebilir sınıflayıcılar, verilen örneklere göre çeşitli içerik türlerini tanıyan araçlardır. Çeşitli yerleşik seçeneklerden birini seçin veya özel ihtiyaçlarınızı karşılamak için özel bir sınıflandırıcı ayarlayın.

1. İçeriği kayıt veya [mevzuat kaydı olarak bildiren bir bekletme etiketi oluşturma](records-management.md#records)
1. [Eğitilebilir sınıflayıcıları kullanarak bekletme etiketlerini otomatik olarak içeriğe uygulama](apply-retention-labels-automatically.md#auto-apply-labels-to-content-by-using-trainable-classifiers)

### <a name="more-information-auto-apply-retention-labels--disposition-review"></a>Daha fazla bilgi: Bekletme etiketlerini otomatik olarak uygulama + yok geçirme

**Gerekenleri korumak için etiketleri otomatik olarak uygula...**
Bekletme etiketleri aşağıdaki içeriği içerdiğinde otomatik olarak içeriğe uygulanabilir:

- [Belirli türlerde hassas bilgi](apply-retention-labels-automatically.md#auto-apply-labels-to-content-with-specific-types-of-sensitive-information)
- [Bir sorguyla eşan belirli anahtar sözcükler veya aranabilir özellikler](apply-retention-labels-automatically.md#auto-apply-labels-to-content-with-keywords-or-searchable-properties)
- [Eğitilebilir sınıflayıcılar için bir eşleşme](apply-retention-labels-automatically.md#auto-apply-labels-to-content-by-using-trainable-classifiers)

**... ardından da sonunda güvenle atabilirsiniz.**

Bekletme döneminin sonunda bir disposition gözden geçirmesi tetiklendiğinde, seçtiğiniz gözden geçirenler gözden geçirilmesi gereken içerikleri olduğunu haber içeren bir e-posta bildirimi alırlar.

Disposition gözden geçirmesini bekleyen içerik, ancak yorum son aşamasında gözden geçiren kişi içeriği kalıcı olarak silmeyi seçtikten sonra kalıcı olarak silinir.

## <a name="additional-trials-and-add-ons"></a>Ek denemeler ve eklentiler

### <a name="compliance-manager-premium-assessments"></a>Uyumluluk Yöneticisi premium değerlendirmeleri

**Riskleri değerlendirin ve etkili bir şekilde yanıt verin**

Verilerinizin toplanması ve kullanımını yöneten uluslara, bölgeye ve sektör gereksinimlerine karşı, organizasyonların riskleri değerlendirmesine ve etkin biçimde yanıt vermelerine yardımcı olun.

[Uyumluluk Yöneticisi premium değerlendirme denemesi hakkında daha fazla bilgi](compliance-easy-trials-compliance-manager-assessments.md).

[Deneme çalışma kitabı: Microsoft Uyumluluk Yöneticisi premium değerlendirmeleri](compliance-easy-trials-compliance-manager-assessment-playbook.md)

### <a name="microsoft-priva-privacy-risk-management-and-microsoft-priva-subject-rights-requests"></a>Microsoft Priva Gizlilik Risk Yönetimi ve Microsoft Priva Konu Hakları İstekleri

**Gizlilik & önlemeyi belirleme**

Veri toplama, veri aktarımları ve verilerin fazla şekillendirimini gibi gizlilik risklerini önceden belirleyerek ve bu risklere karşı korunmaya yardımcı olarak, organizasyon ölçeğinde konu isteklerini otomatikleştirmeye ve yönetmeye yardımcı olun.

[Microsoft Priva hakkında daha fazla bilgi edinmek için](/privacy/solutions/privacymanagement/privacy-management):

[Deneme çalışma kitabı: Microsoft Priva](/privacy/solutions/privacymanagement/privacy-management-trial-playbook)

## <a name="additional-resources"></a>Ek kaynaklar

**Neler dahildir: Ürün** katmanına göre listelenen uyumluluk Microsoft 365 özelliklerinin tam listesi için Özellik Matrisi'ne [bakın](https://go.microsoft.com/fwlink/?linkid=2139145).

**Microsoft Güvenlik Teknik İçerik Kitaplığı**: İhtiyaçlarınızı karşılamak için etkileşimli kılavuzları ve diğer öğrenme içeriğini bulmak için bu kitaplığı keşfedin. [Kitaplık'ı ziyaret edin](/security/content-library).

**Microsoft Güvenlik Kaynakları**: Kötü amaçlı yazılımdan Sıfır Güven'e kadar, kuruma uygun tüm kaynakları ve güvenlik ihtiyaçlarını karşılar. [Kaynaklar'ı ziyaret edin](/security/business/resources).
