---
title: Microsoft Purview çözümleri deneme playbook'u
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
audience: Admin
ms.topic: landing-page
ms.service: O365-seccomp
ms.collection: m365-security-compliance
ms.localizationpriority: high
ROBOTS: NOINDEX, NOFOLLOW
search.appverid:
- MOE150
- MET150
description: Microsoft Purview çözümleri deneme playbook'u.
ms.openlocfilehash: 3ff103a2e6ebc260f5f00964ae09c6b6bbc1fd69
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65098900"
---
# <a name="trial-playbook-microsoft-purview-solutions"></a>Deneme playbook'u: Microsoft Purview çözümleri

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Microsoft Purview çözümleri deneme playbook'una hoş geldiniz. Bu playbook, Microsoft Purview ve güvenlik ürünlerinin güçlü ve kapsamlı özelliklerini keşfetmenize yardımcı olarak 90 günlük ücretsiz denemenizden en iyi şekilde yararlanabilirsiniz.

Her çözümü denemek, kuruluşunuzun uyumluluk gereksinimlerini karşılamak için bilinçli kararlar oluşturmanıza yardımcı olur.

Özellikler:

- [Denetim (Premium)](#audit-premium)
- [İletişim Uyumluluğu](#communication-compliance)
- [Uyumluluk Yöneticisi](#compliance-manager)
- [Veri Yaşam Döngüsü Yönetimi](#data-lifecycle-management)
- [Microsoft Purview Veri Kaybı Önleme](#data-loss-prevention)
- [Ediscovery](#ediscovery)
- [Information Protection](#information-protection)
- [Insider Risk Management](#insider-risk-management)
- [Kayıt Yönetimi](#records-management)

İsteğe bağlı eklentiler:

- [Uyumluluk Yöneticisi premium değerlendirmeleri](#compliance-manager-premium-assessments)
- [Microsoft Priva Gizlilik Risk Yönetimi ve Microsoft Priva Konu Hakları İstekleri](#microsoft-priva-privacy-risk-management-and-microsoft-priva-subject-rights-requests)

## <a name="compliance-actions-with-microsoft-purview"></a>Microsoft Purview ile Uyumluluk Eylemleri

Kuruluşunuzun meta verilerini değiştirmeden Microsoft'un uyumluluk çözümlerini kolayca ve hızlı bir şekilde denemeye başlayın. Önceliklerinize bağlı olarak, hemen değeri görmek için bu çözüm alanlarından herhangi biriyle başlayabilirsiniz. Aşağıda müşterilerimizin iletmiş olduğu en önemli kuruluş endişeleri ve başlangıç olarak önerilen çözümler yer almaktadır.

:::image type="content" source="../media/compliance-trial/workflow.png" alt-text="Microsoft 365 ile uyumluluk eylemleri":::

## <a name="audit-premium"></a>Denetim (Premium)

**Araştırma yapma**

Microsoft Purview Audit (Premium), kuruluşların bir araştırma yürütmek için gereken denetim günlüğü saklama süresini artırarak, risk kapsamını belirlemeye yardımcı olan önemli olaylara erişim sağlayarak ve Office 365 Yönetim Etkinliği API'sine daha hızlı erişim sağlayarak, kuruluşların adli ve uyumluluk araştırmaları gerçekleştirmesine yardımcı olur.

### <a name="step-1-apply-the-e5-license-to-each-user-for-which-youd-like-to-generate-e5-events"></a>1. Adım: [E5 olaylarını oluşturmak istediğiniz her kullanıcıya E5 lisansını uygulama](set-up-advanced-audit.md#step-1-set-up-audit-premium-for-users)

> [!TIP]
> Deneme için en iyi uygulama: 1. Gün

MailItemsAccessed ve Send gibi önemli olayları günlüğe kaydetme özelliği gibi denetim (Premium) özellikleri için kullanıcılara uygun bir E5 lisansı atanması gerekir. Ayrıca, bu kullanıcılar için Gelişmiş Denetim uygulaması/hizmet planı etkinleştirilmelidir.

Kullanıcılar için Denetim 'i (Premium) ayarlayın- Gelişmiş Denetim uygulamasının kullanıcılara atandığını doğrulamak [için, her kullanıcı için aşağıdaki adımları uygulayın](set-up-advanced-audit.md#step-1-set-up-audit-premium-for-users).

1. Denetim (Premium) olaylarını [etkinleştir - SearchQueryInitiatedExchange ve SearchQueryInitiatedSharePoint'i](set-up-advanced-audit.md#step-2-enable-audit-premium-events) [Exchange Online PowerShell'deki](/powershell/exchange/connect-to-exchange-online-powershell) her kullanıcı için denetlenecek şekilde etkinleştirin.
1. Denetim saklama ilkelerini ayarlama - Kuruluşunuzun güvenlik işlemlerinin, BT'nin ve uyumluluk ekiplerinin gereksinimlerini karşılamak için [ek denetim günlüğü saklama ilkeleri oluşturun](set-up-advanced-audit.md#step-3-set-up-audit-retention-policies) .
1. Denetim (Premium) olaylarını arayın- Adli araştırma yaparken [kritik Denetim (Premium) olayları](set-up-advanced-audit.md#step-4-search-for-audit-premium-events) ve diğer etkinlikleri arayın.

### <a name="step-2-create-new-audit-log-policies-to-specify-how-long-to-retain-audit-logs-in-your-org-for-activities-performed-by-users-and-define-priority-levels-for-your-policies"></a>2. Adım: [Kullanıcılar tarafından gerçekleştirilen etkinlikler için kuruluşunuzda denetim günlüklerinin ne kadar süre tutulacağını belirtmek ve ilkeleriniz için öncelik düzeylerini tanımlamak için yeni Denetim Günlüğü ilkeleri oluşturun](audit-log-retention-policies.md#before-you-create-an-audit-log-retention-policy)

> [!TIP]
> Deneme için en iyi uygulama: İlk 30 gün içinde oluşturma

Denetim günlüğü saklama ilkeleri, Microsoft 365'deki yeni Denetim (Premium) özelliklerinin bir parçasıdır. Denetim günlüğü saklama ilkesi, kuruluşunuzda denetim günlüklerinin ne kadar süre tutulacağını belirtmenize olanak tanır.

1. Bir denetim günlüğü saklama ilkesi oluşturmadan önce, ilkenizi oluşturmadan önce [bilmeniz gereken önemli şeyler](audit-log-retention-policies.md#before-you-create-an-audit-log-retention-policy) .
1. [Denetim günlüğü saklama ilkesi oluşturma](audit-log-retention-policies.md#create-an-audit-log-retention-policy)
1. [Microsoft Purview uyumluluk portalında denetim günlüğü saklama ilkelerini yönetme](audit-log-retention-policies.md#manage-audit-log-retention-policies-in-the-compliance-portal) - Denetim günlüğü saklama ilkeleri, Denetim bekletme ilkeleri sekmesinde (pano olarak da adlandırılır) listelenir. Denetim bekletme ilkelerini görüntülemek, düzenlemek ve silmek için panoyu kullanabilirsiniz.
1. PowerShell'de denetim günlüğü saklama ilkeleri oluşturma ve yönetme - Güvenlik & Uyumluluk Merkezi PowerShell'i kullanarak [denetim günlüğü saklama ilkeleri oluşturabilir ve yönetebilirsiniz](audit-log-retention-policies.md#create-and-manage-audit-log-retention-policies-in-powershell). PowerShell'i kullanmanın bir nedeni, kullanıcı arabiriminde bulunmayan bir kayıt türü veya etkinliği için ilke oluşturmaktır.

## <a name="communication-compliance"></a>İletişim Uyumluluğu

**Davranış kuralları ilke ihlallerini belirleme ve buna göre işlem yapma**

Microsoft Purview İletişim Uyumluluğu, uygunsuz iletileri algılamanıza, olası ilke ihlallerini araştırmanıza ve düzeltmeye yönelik adımlar atmanıza yardımcı olarak uyumlu ve sağlıklı bir çalışma ortamını desteklemek için iletişim ihlallerini akıllı bir şekilde belirlemenize yardımcı olur.

### <a name="step-1-enable-permissions-for-communication-compliance"></a>1. Adım: [İletişim uyumluluğu için izinleri etkinleştirme](communication-compliance-configure.md#step-1-required-enable-permissions-for-communication-compliance)

> [!TIP]
> Deneme için en iyi uygulama: 1. Gün

[Tüm uyumluluk kullanıcılarını İletişim Uyumluluğu rol grubuna atayın](communication-compliance-configure.md#step-1-required-enable-permissions-for-communication-compliance).

### <a name="step-2-enable-the-audit-log"></a>2. Adım: [Denetim günlüğünü etkinleştirme](communication-compliance-configure.md#step-2-required-enable-the-audit-log)

> [!TIP]
> Deneme için en iyi uygulama: İlk 30 gün içinde kurulum

Bu özelliği kullanmak için, kuruluşunuzun kuruluşunuzda kullanıcı ve yönetici etkinliğini kaydetmeye başlayabilmesi için denetimi açın. Bunu açtığınızda, etkinlik denetim günlüğüne kaydedilir ve raporda görüntülenebilir. Daha fazla bilgi için bkz [. Denetim günlüğü aramasını açma veya kapatma](turn-audit-log-search-on-or-off.md).

### <a name="step-3-create-a-communication-compliance-policy"></a>3. Adım: [İletişim uyumluluk ilkesi oluşturma](communication-compliance-policies.md)

[Mevcut şablonları kullanarak iletişim uyumluluk ilkesi oluşturma](communication-compliance-policies.md): 1- Uygunsuz içerik; 2- Hassas bilgiler; 3- Mevzuat uyumluluğu; 4- Çıkar çatışması.

### <a name="step-4-investigate-and-remediate-alerts"></a>4. Adım: [Uyarıları araştırma ve düzeltme](communication-compliance-investigate-remediate.md)

İletişim uyumluluk uyarılarını [araştırın ve düzeltin](communication-compliance-investigate-remediate.md).

## <a name="compliance-manager"></a>Uyumluluk Yöneticisi

**Kuruluş uyumluluğunuzu kolayca yönetin**

Microsoft Purview Uyumluluk Yöneticisi, veri koruma risklerinizin envanterini almaktan denetimleri uygulama, düzenlemeler ve sertifikalarla güncel kalma ve denetçilere raporlama gibi karmaşıklıkları yönetmeye kadar uyumluluk yolculuğunuz boyunca size yardımcı olabilir.

### <a name="step-1-get-to-know-compliance-manager"></a>1. Adım: [Uyumluluk Yöneticisi'ne alışma](compliance-manager-quickstart.md#first-visit-get-to-know-compliance-manager)

> [!TIP]
> Deneme için en iyi uygulama: 1. Gün

Uyumluluk Yöneticisi'ne genel bakış sayfamız, Uyumluluk Yöneticisi'nin ne olduğu ve nasıl çalıştığına ilişkin kapsamlı bir inceleme için en iyi ilk duraktır. Aşağıdaki bağlantıları kullanarak belgelerimizin önemli bölümlerine doğrudan geçmek de isteyebilirsiniz:

- [Uyumluluk puanınızı anlama](compliance-manager.md#understanding-your-compliance-score)
- [Önemli öğelere genel bakış: denetimler, değerlendirmeler, şablonlar ve iyileştirme eylemleri](compliance-manager.md#key-elements-controls-assessments-templates-improvement-actions)
- [Uyumluluk Yöneticisi panosunu anlama](compliance-manager-setup.md#understand-the-compliance-manager-dashboard)
- [Pano görünümünüzü filtreleme](compliance-manager-setup.md#filtering-your-dashboard-view)
- [İyileştirme eylemleri hakkında bilgi edinin](compliance-manager-setup.md#improvement-actions-page)
- [Değerlendirmeleri anlama](compliance-manager.md#assessments)
- [Microsoft Uyumluluk Configuration Manager kullanarak ortamınızda hızlı bir tarama yapın](compliance-manager-mcca.md)

![Uyumluluk Yöneticisi - pano.](../media/compliance-manager-dashboard.png "Uyumluluk Yöneticisi panosu")

### <a name="step-2-configure-compliance-manager-to-manage-your-compliance-activities"></a>2. Adım: [Uyumluluk Yöneticisini uyumluluk etkinliklerinizi yönetecek şekilde yapılandırma](compliance-manager-assessments.md)

> [!TIP]
> Deneme için en iyi uygulama: İlk 30 gün içinde inceleme

Değerlendirmelerle çalışmaya başlayın ve denetimleri uygulamak ve uyumluluk puanınızı geliştirmek için iyileştirme eylemleri gerçekleştirin.

1. [İlk değerlendirmenizi oluşturmak ve yönetmek için önceden oluşturulmuş bir şablon seçin](compliance-manager-assessments.md).
1. [Değerlendirme oluşturmak için şablonların nasıl kullanılacağını anlama](compliance-manager-templates.md).
1. [Değerlendirmelerinizdeki denetimleri tamamlamak için iyileştirme eylemleri üzerinde uygulama ve test çalışmaları gerçekleştirin](compliance-manager-improvement-actions.md).
1. [Farklı eylemlerin uyumluluk puanınızı nasıl etkilediğini daha iyi anlayın](compliance-score-calculation.md).

> [!NOTE]
> Microsoft 365 veya Office 365 E1/E3 aboneliği Microsoft Veri Koruma Temeli şablonunu içerir. E5 Uyumluluğu, Microsoft 365 veya Office 365 E5 için şablonlar içerir:
>
> - Microsoft Veri Koruma Temeli
> - Avrupa Birliği GDPR  
> - ISO/IEC 27001,
> - NIST 800-53
>
> Uyumluluk Yöneticisi, eklenti olarak satın alınabilecek 300'in üzerinde mevzuat veya premium şablon içerir. Listeye buradan bakın. Tüm premium şablonlarla (aboneliğinize dahil edilir veya eklenti olarak satın alınır) bu şablonların evrensel sürümünü alırsınız ve herhangi bir ürün veya hizmetle uyumluluğunuzu yönetmenizi sağlar

### <a name="step-3-scaling-up-use-advanced-functionality-to-meet-your-custom-needs"></a>3. Adım: [Ölçeği artırma: Özel gereksinimlerinizi karşılamak için gelişmiş işlevleri kullanın](compliance-manager-templates-create.md)

Özel değerlendirmeler şunlar için yararlıdır:

- Üçüncü taraf uygulamalar ve hizmetler, şirket içi uygulamalar ve diğer varlıklar gibi Microsoft 365 olmayan ürünler için uyumluluğu yönetme
- Kendi özel veya işletmeye özgü uyumluluk denetimlerinizi yönetme

1. [Kendi denetimlerinizi ve iyileştirme eylemlerinizi ekleyerek Uyumluluk Yöneticisi şablonunu genişletme](compliance-manager-templates-extend.md)
1. [Kendi özel şablonunuzu oluşturma](compliance-manager-templates-create.md)
1. [Denetimleri ve eylemleri eklemek veya kaldırmak için mevcut şablonu değiştirme](compliance-manager-templates-modify.md)
1. [İyileştirme eylemlerinin otomatik testini ayarlama](compliance-manager-setup.md#set-up-automated-testing)
1. [Geliştirme eylemlerini başka bir kullanıcıya yeniden atama](compliance-manager-setup.md#reassign-improvement-actions-to-another-user)

## <a name="data-lifecycle-management"></a>Veri Yaşam Döngüsü Yönetimi

**Otomasyon ile büyük ölçekte idare**

Otomatik olarak güncelleştirilen ilke kapsamları ile kuruluşunuzdaki değişikliklere uyum sağlama becerinizi geliştirin. El ile yapılan çabaları azaltmak ve uyumluluk duruşunu geliştirmek için içeriğin etiketlenmesinde otomatikleştirme.

### <a name="step-1-dynamically-target-retention-policies-with-adaptive-policy-scopes"></a>1. Adım: Uyarlamalı İlke Kapsamları ile bekletme ilkelerini dinamik olarak hedefleme
> [!TIP]
> Deneme için en iyi uygulama: 1. Gün

Uyarlamalı ilke kapsamları, bir ilkeyi AD özniteliklerine göre belirli kullanıcılara, gruplara veya sitelere dinamik olarak hedeflemenizi sağlar.  Kapsamların öznitelikleri listeden seçilebilir veya gelişmiş sorgu oluşturucu kullanılarak özelleştirilebilir.

Uyarlamalı ilke kapsamlarını kullanan ilkeler, yeni çalışanların katılması veya ayrılmasıyla kuruluş değiştikçe güncel kalır. Ayrıca, ilkeye dahil edilen 100/1.000 konumun önceki sınırlarına tabi değildir.

- Uyarlamalı İlke Kapsamı oluşturma ve bunu bekletme ilkesiyle kullanma

### <a name="step-2-automate-labeling-to-apply-a-label-to-all-items-by-default"></a>2. Adım: Varsayılan olarak tüm öğelere etiket uygulamak için etiketlemeyi otomatikleştirme

> [!TIP]
> Deneme için en iyi uygulama: İlk 30 gün içinde kurulum

Varsayılan etiketler, SharePoint'da belirtilen kitaplık, klasör veya belge kümesi içindeki tüm öğelere otomatik olarak bekletme etiketi uygulamanıza olanak sağlar.

- Etiketi yayımlama ve SharePoint'de varsayılan olarak uygulama

## <a name="data-loss-prevention"></a>Veri Kaybı Önleme

**Hassas verileri koruma**

kuruluşların iş standartlarına ve sektör düzenlemelerine uyum sağlamak için hassas bilgileri yanlışlıkla açığa çıkmasını önlemek için koruması gerekir. Microsoft 365 genelinde hassas bilgileri tanımlamak, izlemek ve otomatik olarak korumak için Microsoft Purview Veri Kaybı Önleme ilkelerini ayarlayın.

### <a name="step-1-protect-data-loss-on-teams-locations"></a>1. Adım: [Teams konumlarda veri kaybını koruma](dlp-microsoft-teams.md#dlp-licensing-for-microsoft-teams)

> [!TIP]
> Deneme için en iyi uygulama: 1. Gün

Kuruluşunuzda veri kaybı önleme (DLP) varsa, kişilerin bir Microsoft Teams kanalında veya sohbet oturumunda hassas bilgileri paylaşmasını engelleyen ilkeler tanımlayabilirsiniz.

1. [Microsoft Teams için DLP Lisansı ve DLP korumasının kapsamı](dlp-microsoft-teams.md#dlp-licensing-for-microsoft-teams) hakkında bilgi edinin
1. [Mevcut DLP ilkelerine konum olarak Microsoft Teams ekleme](dlp-microsoft-teams.md#add-microsoft-teams-as-a-location-to-existing-dlp-policies)
1. [Teams için varsayılan DLP ilkemizi yapılandırın](mip-easy-trials.md) veya [Microsoft Teams için yeni bir DLP ilkesi tanımlayın](dlp-microsoft-teams.md#define-a-new-dlp-policy-for-microsoft-teams)

### <a name="step-2-protect-data-loss-on-device-locations"></a>2. Adım: [Cihaz konumlarında veri kaybını koruma](endpoint-dlp-getting-started.md)

> [!TIP]
> Deneme için en iyi uygulama: İlk 30 gün içinde kurulum

Microsoft Endpoint DLP, Windows 10 cihazları izlemenize ve hassas öğelerin ne zaman kullanıldığını ve paylaşılmasını algılamanıza olanak tanır.

1. Uç noktalarınızı hazırlama - [Bu gereksinimleri karşılamak](endpoint-dlp-getting-started.md) için Uç Nokta DLP'sini dağıtmayı planladığınız Windows 10 ve macOS cihazlarının
1. [Cihazları cihaz yönetimine ekleme](endpoint-dlp-getting-started.md)  - Cihazdaki hassas öğeleri izleyip koruyabilmeniz için önce cihaz izlemeyi etkinleştirmeniz ve uç noktalarınızı eklemeniz gerekir. Bu eylemlerin her ikisi de Microsoft Purview uyumluluk portalında gerçekleştirilir.
   - Senaryo 1 – [Henüz eklenmemiş cihazları](endpoint-dlp-getting-started.md) ekleme.
   - Senaryo 2 - [Uç Nokta için Microsoft Defender zaten dağıtıldı ve içinde raporlama yapılan uç noktalar var](endpoint-dlp-getting-started.md). Tüm bu uç noktalar yönetilen cihazlar listesinde görünür.
1. [Cihazlar için varsayılan DLP ilkemizi yapılandırın veya Cihazlar için](mip-easy-trials.md#dlp-for-devices) [yeni bir DLP ilkesi tanımlayın](endpoint-dlp-learn-about.md).
1. DLP Uyarıları Yönetimi panosunda [Uç Nokta DLP uyarılarını görüntüleyin](dlp-configure-view-alerts-policies.md).
1. Etkinlik gezgininde [Uç Nokta DLP verilerini görüntüleyin](data-classification-activity-explorer.md).

### <a name="step-3-expand-policies-in-scope-or-protection"></a>3. Adım: [Kapsam veya korumadaki ilkeleri genişletme](dlp-learn-about-dlp.md#dlp-policy-configuration-overview)

DLP ilkelerinizi yapılandırma konusunda esnekliğe sahipsiniz. Teams ve cihazlar için varsayılan DLP ilkemizle başlayabilir ve ek konumları, hassas bilgi türlerini veya etiketleri korumak için bu ilkeleri genişletebilirsiniz. Ayrıca, ilke eylemlerini genişletebilir ve uyarıları özelleştirebilirsiniz.

1. Konum ekleme
1. Korumak için hassas bilgi türleri veya etiketler ekleme
1. Eylem ekleme
   - Teams:
      - [Hassas belgelere dış erişimi engelleme](dlp-microsoft-teams.md#prevent-external-access-to-sensitive-documents)
      - [Kullanıcıları eğitmeye yardımcı olacak ilke ipuçları ve ilke ipuçlarını özelleştirme yönergeleri alma](dlp-microsoft-teams.md#policy-tips-help-educate-users)
   - Cihazlar: Yalnızca denetimden engellemeye geçme
1. [Veri kaybı önleme ilkeleri için uyarıları yapılandırma ve görüntüleme - Microsoft Purview | Microsoft Docs](dlp-configure-view-alerts-policies.md)

## <a name="ediscovery"></a>Ediscovery

**Uçtan uca iş akışıyla daha fazlasını keşfedin**

Kuruluşunuzun iç ve dış araştırmalarına yanıt veren içeriği korumak, toplamak, analiz etmek ve dışarı aktarmak için uçtan uca iş akışından yararlanın. Yasal ekipler, bir davaya dahil olan koruyucularla iletişim kurarak yasal tutma bildirim sürecinin tamamını da yönetebilir.

### <a name="step-1-required-permissions"></a>1. Adım (gerekli): [İzinler](https://aka.ms/ediscoveryninja)

> [!TIP]
> Deneme için en iyi uygulama: 1. Gün

eBulma 'ya (Premium) erişmek veya bir eBulma (Premium) olayının üyesi olarak eklemek için, kullanıcıya uygun izinlerin atanması gerekir.

1. [eBulma ayarlama (Premium) – eBulma izinlerini atama](get-started-with-advanced-ediscovery.md#step-2-assign-ediscovery-permissions)
1. [Bir vakaya üye ekleme veya kaldırma](add-or-remove-members-from-a-case-in-advanced-ediscovery.md)

### <a name="step-2-required-create-a-case"></a>2. Adım (gerekli): Servis Talebi Oluşturma

> [!TIP]
> Deneme için en iyi uygulama: İlk 30 gün içinde oluşturma

Daha fazla kuruluş eBulma (Premium) çözümünü kritik eBulma işlemleri için Microsoft 365 kullanır. Bu, mevzuat isteklerine, araştırmalara ve davalara yanıt vermeyi içerir.

1. eBulmayı Yönetme (Premium) – [eBulma (Premium) yapılandırmayı, Güvenlik & Uyumluluk Merkezi'ni kullanarak servis taleplerini yönetmeyi, eBulma'da (Premium) bir iş akışını yönetmeyi ve eBulma (Premium) arama sonuçlarını analiz etmeyi öğrenin](/learn/modules/manage-advanced-ediscovery).
1. [Advance eDiscovery'nin yeni servis talebi biçimini kullanarak eBulma olayı oluşturma](advanced-ediscovery-new-case-format.md)
1. [Bir olayı kapatma veya silme](close-or-delete-case.md) - Yasal dava veya araştırma tamamlandığında, kapatabilir veya silebilirsiniz. Kapatılan bir olayı da yeniden açabilirsiniz.

### <a name="step-3-optional-settings"></a>3. Adım (isteğe bağlı): Ayarlar

Kuruluşunuzdaki kişilerin örnek oluşturmaya ve kullanmaya başlamasına izin vermek için, kuruluşunuzdaki tüm durumlar için geçerli olan genel ayarları yapılandırmanız gerekir. Şu anda tek genel ayar **avukat-istemci ayrıcalık algılamadır** (gelecekte daha fazla genel ayar sağlanacaktır).

1. [eBulma ayarlama (Premium) – Genel Ayarlar](get-started-with-advanced-ediscovery.md#step-3-configure-global-settings-for-ediscovery-premium)
1. [Arama ve analiz ayarlarını yapılandırma](configure-search-and-analytics-settings-in-advanced-ediscovery.md)
1. [eBulma'da işleri yönetme (Premium)](managing-jobs-ediscovery20.md)

### <a name="step-4-optional-compliance-boundaries"></a>4. Adım (isteğe bağlı): [Uyumluluk Sınırları](set-up-compliance-boundaries.md)

Uyumluluk sınırları, eBulma yöneticilerinin arayabileceği kullanıcı içerik konumlarını (posta kutuları, OneDrive hesapları ve SharePoint siteleri gibi) denetleen bir kuruluş içinde mantıksal sınırlar oluşturur. Ayrıca kuruluşunuzdaki yasal, insan kaynaklarını veya diğer soruşturmaları yönetmek için kullanılan eBulma olaylarına kimlerin erişebileceğini de denetler.

![Uyumluluk sınırları, eBulma olaylarına erişimi denetleen ajanslara ve yönetici rol gruplarına erişimi denetleen arama izinleri filtrelerinden oluşur.](../media/M365_ComplianceBoundary_OrgChart_v2.png)

eBulma araştırmaları için uyumluluk sınırlarını ayarlayın:

1. [Ajanslarınızı tanımlamak için bir kullanıcı özniteliği tanımlama](set-up-compliance-boundaries.md#step-1-identify-a-user-attribute-to-define-your-agencies)
1. [Her ajans için bir rol grubu oluşturma](set-up-compliance-boundaries.md#step-2-create-a-role-group-for-each-agency)
1. [Uyumluluk sınırını zorlamak için arama izinleri filtresi oluşturma](set-up-compliance-boundaries.md#step-3-create-a-search-permissions-filter-to-enforce-the-compliance-boundary)
1. [Kurum içi araştırmalarda eBulma olayı oluşturma](set-up-compliance-boundaries.md#step-4-create-an-ediscovery-case-for-intra-agency-investigations)

### <a name="step-5-optional-learn-about-content-search-tool"></a>5. Adım (isteğe bağlı): [İçerik arama aracı hakkında bilgi edinin](search-for-content.md)

Exchange posta kutularında e-postayı, SharePoint sitelerdeki ve OneDrive konumlardaki belgeleri ve Skype Kurumsal anlık ileti konuşmalarını hızla bulmak için Microsoft Purview uyumluluk portalındaki İçerik arama aracını kullanın. Microsoft Teams ve Microsoft 365 Grupları gibi işbirliği araçlarında e-posta, belge ve anlık ileti konuşmalarını aramak için içerik arama aracını kullanabilirsiniz.

- [eBulma (Premium) araması hakkında daha fazla bilgi edinin](search-for-content.md#search-for-content)

## <a name="information-protection"></a>Information Protection

**Hassas bilgilerinizi keşfetme, sınıflandırma ve koruma**

Hassas içeriğinizi yaşadığınız veya seyahat ettiğiniz her yerde keşfetmenize, sınıflandırmanıza ve korumanıza yardımcı olmak için Microsoft Purview Information Protection ve duyarlılık etiketlerini uygulayın.

### <a name="step-1-start-your-information-protection-trial"></a>1. Adım: [Bilgi koruma denemenizi başlatma](mip-easy-trials.md)

> [!TIP]
> Deneme için en iyi uygulama: 1. Gün

Uygun müşteriler, Microsoft Purview Information Protection için varsayılan etiketleri ve ilkeleri etkinleştirebilir. Deneme sürümünde varsayılan yapılandırmayı etkinleştirdiğinizde, kiracınız için tüm ilkelerin yapılandırılması yaklaşık 2 dakika ve bu varsayılan ilkelerin sonuçlarını görmek 24 saate kadar sürer.

Varsayılan yapılandırmayı seçerek, 1 tıklamayla aşağıdakiler otomatik olarak yapılandırılır:

- Duyarlılık etiketleri ve duyarlılık etiketi ilkesi
- İstemci tarafı otomatik etiketleme
- Hizmet tarafı otomatik etiketleme
- Teams ve cihazlar için veri kaybı önleme (DLP) ilkeleri

[Varsayılan etiketleri ve ilkeleri etkinleştirin](mip-easy-trials.md#activate-the-default-labels-and-policies). Gerekirse, yapılandırma tamamlandıktan sonra el ile düzenleyebilirsiniz.

### <a name="step-2-automatically-apply-sensitivity-labels-to-documents"></a>2. Adım: [Belgelere duyarlılık etiketlerini otomatik olarak uygulama](apply-sensitivity-label-automatically.md)

> [!TIP]
> Deneme için en iyi uygulama: İlk 30 gün içinde kurulum

Duyarlılık etiketi oluşturduğunuzda, belirttiğiniz koşullarla eşleştiğinde bu etiketi dosyalara ve e-postalara otomatik olarak atayabilirsiniz.

1. [Duyarlılık etiketleri oluşturma ve yapılandırma](create-sensitivity-labels.md#create-and-configure-sensitivity-labels)
1. [Duyarlılık etiketi ilkesini tüm kullanıcılara yayımlama](create-sensitivity-labels.md#publish-sensitivity-labels-by-creating-a-label-policy)
1. [Otomatik etiketleme ilkesi oluşturma](create-sensitivity-labels.md#publish-sensitivity-labels-by-creating-a-label-policy)
   - Etiketin uygulanmasını istediğiniz bilgileri seçin
   - Etiket uygulanacak konumları tanımlama
   - Uygulanacak etiketi seçin
   - [İlkeyi simülasyon modunda çalıştırma](create-sensitivity-labels.md#publish-sensitivity-labels-by-creating-a-label-policy)

![Otomatik etiketleme için yeni ilke yapılandırması.](../media/auto-labeling-wizard.png)

### <a name="step-3-review-and-turn-on-auto-labeling-policy"></a>3. Adım: [Otomatik etiketleme ilkesini gözden geçirme ve açma](apply-sensitivity-label-automatically.md#how-to-configure-auto-labeling-policies-for-sharepoint-onedrive-and-exchange)

**Şimdi Information protectionAuto** >  **etiketleme** sayfasında **Simülasyon** bölümünde otomatik etiketleme ilkenizi görürsünüz.

Yapılandırmanın ve durumun ayrıntılarını görmek için ilkenizi seçin. Simülasyon tamamlandığında, hangi e-postaların veya belgelerin belirtilen kurallarla eşleştiğine bakmak için Gözden geçirilir öğeler sekmesini seçin.

İlkeyi simülasyon olmadan çalıştırmaya hazır olduğunuzda İlkeyi **aç** seçeneğini belirleyin.

## <a name="insider-risk-management"></a>Insider Risk Management

**Insider risklerini algılama ve düzeltme**

İç riskleri hızla belirlemenize, önceliklendirmenize ve düzeltmenize yardımcı olmak için yapay zekadan yararlanın. Microsoft 365 ve Azure hizmetlerindeki günlükleri kullanarak, içeriden risk sinyallerini izleyen ilkeler tanımlayabilir, ardından kullanıcı eğitimini yükseltme veya araştırma başlatma gibi düzeltme eylemleri gerçekleştirebilirsiniz.

### <a name="step-1-required-enable-permissions-for-insider-risk-management"></a>1. Adım (gerekli): [Insider risk yönetimi için izinleri etkinleştirme](insider-risk-management-configure.md#step-1-required-enable-permissions-for-insider-risk-management)

> [!TIP]
> Deneme için en iyi uygulama: 1. Gün

Insider risk yönetimi özelliklerini yönetmek için izinleri yapılandırmak için kullanılan dört rol grubu vardır.

[Kullanıcıları bir insider risk yönetimi rol grubuna ekleyin.](insider-risk-management-configure.md#add-users-to-an-insider-risk-management-role-group)

İzinleri göremiyorsanız, doğru rolleri atamak için lütfen kiracı yöneticinizle görüşün.

### <a name="step-2-start-with-user-quick-start-guide"></a>2. Adım: [Kullanıcı hızlı başlangıç kılavuzuyla başlama](insider-risk-management-configure.md#recommended-actions-preview)

Önerilen eylemlerle hızlıca başlayın ve içeriden risk yönetimi özelliklerinden en iyi şekilde yararlanın. Genel Bakış sayfasına eklenen önerilen eylemler, ilkeleri yapılandırma ve dağıtma ve ilke eşleşmelerinden uyarı oluşturan kullanıcı eylemleri için araştırma eylemleri gerçekleştirme adımlarında size yol gösterir.

Insider risk yönetimini yapılandırmaya başlamak için [listeden bir öneri seçin](insider-risk-management-configure.md#recommended-actions-preview).

![Insider risk yönetimi önerilen eylemler.](../media/insider-risk-recommended-actions.png)

Önerilen her eylem, gereksinimler, beklenecekler ve özelliğin kuruluşunuzdaki yapılandırmasının etkisi de dahil olmak üzere öneri için gerekli etkinliklerde size yol gösterir.

### <a name="step-3-required-enable-the-microsoft-365-audit-log"></a>3. Adım (gerekli): [Microsoft 365 denetim günlüğünü etkinleştirme](insider-risk-management-configure.md#step-2-required-enable-the-microsoft-365-audit-log)

Denetim, Microsoft 365 kuruluşlar için varsayılan olarak etkindir. Bazı kuruluşlar belirli nedenlerle denetimi devre dışı bırakmış olabilir. Kuruluşunuzda denetim devre dışı bırakıldıysa, bunun nedeni başka bir yöneticinin kapatması olabilir. Bu adımı tamamlarken denetimi yeniden açmanın uygun olduğunu onaylamanızı öneririz.

Denetimi açmak için adım adım yönergeler için bkz. [Denetim günlüğü aramasını açma veya kapatma](turn-audit-log-search-on-or-off.md). Denetimi açtıktan sonra, denetim günlüğünün hazırlandığını ve hazırlık tamamlandıktan birkaç saat sonra bir arama çalıştırabileceğinizi belirten bir ileti görüntülenir. Bu eylemi yalnızca bir kez yapmanız gerekir. Microsoft 365 denetim günlüğünü kullanma hakkında daha fazla bilgi için bkz[. Denetim günlüğünde arama](search-the-audit-log-in-security-and-compliance.md) yapma.

### <a name="step-4-required-enable-and-view-insider-risk-analytics-insights"></a>4. Adım (gerekli): [Insider risk analizi içgörülerini etkinleştirme ve görüntüleme](insider-risk-management-configure.md#step-3-optional-enable-and-view-insider-risk-analytics-insights)

Insider risk yönetimi analizi, herhangi bir insider risk ilkesi yapılandırmadan kuruluşunuzdaki olası insider risklerini değerlendirmenizi sağlar. Analiz tarama sonuçlarının, içgörülerin gözden geçirilebilir raporlar olarak kullanılabilir hale gelmesi 48 saat kadar sürebilir. Analiz içgörüleri hakkında daha fazla bilgi edinmek için [Insider risk yönetimi ayarları: Analiz (önizleme)](insider-risk-management-settings.md) bölümüne bakın ve insider risk duruşunuzu anlamanıza yardımcı olmak ve riskli kullanıcıları tanımlamak için uygun ilkeleri ayarlayarak eyleme geçmenize yardımcı olmak için [Insider Risk Management Analytics videosunu](https://www.youtube.com/watch?v=5c0P5MCXNXk) gözden geçirin.

Insider risk Analizi'ni etkinleştirmek için Insider Risk Management veya Insider Risk Management Yöneticisi üyesi olmanız gerekir. [Insider risk analizini etkinleştirmek için bu adımları tamamlayın](insider-risk-management-configure.md).

## <a name="records-management"></a>Kayıt Yönetimi

**İş, yasal veya mevzuat kaydı tutma gereksinimleri için yüksek değerli öğeleri yönetme**

Kuruluş düzenleme, yasal ve iş açısından kritik kayıtların bekletme zamanlamasını otomatikleştirmek için Microsoft Purview Kayıt Yönetimi özelliklerini kullanın. Kayıtları bildirmek, içeriği saklamak ve bunları en sonda atmak için işbirliği aracılığıyla oluşturmadan otomasyon özelliklerinden yararlanın.

### <a name="step-1-mark-contents-as-records"></a>1. Adım: İçeriği kayıt olarak işaretleme  

> [!TIP]
> Deneme için en iyi uygulama: 1. Gün

İçerik kayıt olarak bildirildiğinde, öğeye izin verilen veya engellenen eylemlere göre kısıtlamalar uygulanır, öğelerle ilgili ek etkinlikler günlüğe kaydedilir ve öğelerin saklama süresinin sonunda silinmesi durumunda değerlendirme kanıtınız olur.

- İçerikleri kayıt veya mevzuat kaydı olarak bildiren bir bekletme etiketi oluşturma

### <a name="step-2-review-content-to-approve-before-its-permanently-deleted"></a>2. Adım: Kalıcı olarak silinmeden önce onaylayacak içeriği gözden geçirme

> [!TIP]
> Deneme için en iyi uygulama: 1. Gün

Saklama süresinin sonunda, belirttiğiniz kullanıcılara ("gözden geçirenler") içeriği gözden geçirmeleri ve kalıcı elden çıkarma eylemini onaylamaları bildirilebilir. Bu, silme işleminden farklı bir eylemin içeriğe farklı bir saklama süresi atama veya bir denetim için silme işlemini askıya alma gibi daha uygun olup olmadığını destekler.

- Değerlendirme gözden geçirmesini kullanan bir bekletme etiketi oluşturma

### <a name="step-3-apply-labels-automatically-to-content-that-matches-specific-conditions"></a>3. Adım: Etiketleri belirli koşullarla eşleşen içeriğe otomatik olarak uygulama

> [!TIP]
> Deneme için en iyi uygulama: İlk 30 gün içinde kurulum

Etiketlerin otomatik uygulanması, kullanıcıların etiketleme etkinliklerini el ile gerçekleştirme gereksinimini ortadan kaldırır. Bu içerikte henüz bir bekletme etiketi uygulanmamışsa ve hassas bilgiler, anahtar sözcükler veya aranabilir özellikler ya da eğitilebilir sınıflandırıcılar için eşleşme içerdiğinde içeriğe otomatik olarak bekletme etiketleri uygulayabilirsiniz.

- Belirli türde hassas bilgilere sahip içeriğe bekletme etiketlerini otomatik uygulama
- Eğitilebilir sınıflandırıcıları kullanarak içeriğe bekletme etiketlerini otomatik uygulama
- Anahtar sözcükler veya aranabilir özelliklerle bekletme etiketlerini otomatik uygulama

## <a name="additional-trials-and-add-ons"></a>Ek denemeler ve eklentiler

### <a name="compliance-manager-premium-assessments"></a>Uyumluluk Yöneticisi premium değerlendirmeleri

**Riskleri değerlendirme ve verimli yanıt verme**

Kuruluşunuzun riskleri değerlendirmesine ve verilerin toplanması ve kullanımını yöneten ülkelere, bölgesel ve sektör gereksinimlerine verimli bir şekilde yanıt vermesine yardımcı olun.

[Uyumluluk Yöneticisi premium değerlendirme deneme sürümü hakkında daha fazla bilgi](compliance-easy-trials-compliance-manager-assessments.md).

[Deneme playbook'u: Microsoft Purview Compliance Manager premium değerlendirmeleri](compliance-easy-trials-compliance-manager-assessment-playbook.md)

### <a name="microsoft-priva-privacy-risk-management-and-microsoft-priva-subject-rights-requests"></a>Microsoft Priva Gizlilik Risk Yönetimi ve Microsoft Priva Konu Hakları İstekleri

**Gizlilik risklerini & önlemeyi belirleme**

Veri depolama, veri aktarımları ve fazla paylaşım gibi gizlilik risklerini proaktif olarak belirleyin ve koruyun ve kuruluşunuzun büyük ölçekte konu isteklerini otomatikleştirmeye ve yönetmeye yardımcı olun.

[Microsoft Priva hakkında daha fazla bilgi edinin](/privacy/solutions/privacymanagement/privacy-management).

[Deneme playbook'u: Microsoft Priva](/privacy/solutions/privacymanagement/privacy-management-trial-playbook)

## <a name="additional-resources"></a>Ek kaynaklar

**Dahil olanlar**: Ürün katmanı tarafından listelenen Microsoft Purview çözümlerinin ve özelliklerinin tam listesi için [Özellik Matrisi'ni](https://go.microsoft.com/fwlink/?linkid=2139145) görüntüleyin.

**Microsoft Güvenlik Teknik İçerik Kitaplığı**: Etkileşimli kılavuzları ve gereksinimlerinizle ilgili diğer öğrenme içeriğini bulmak için bu kitaplığı keşfedin. [Kitaplığı ziyaret edin](/security).

**Microsoft Güvenlik Kaynakları**: Kötü amaçlı yazılımdan korumadan Sıfır Güven kuruluşunuzun güvenlik gereksinimlerine uygun tüm kaynakları alın. [Kaynaklar'a bakın](/security/business/resources).
