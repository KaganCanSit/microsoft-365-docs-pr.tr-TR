---
title: Insider risk yönetimini planlama
description: Kuruluşta Insider risk yönetimi ilkelerini kullanmayı planlamayı öğrenin.
keywords: Microsoft 365, insider riski, risk yönetimi, uyumluluk
ms.localizationpriority: medium
ms.service: O365-seccomp
ms.topic: article
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: itpro
ms.collection: m365-security-compliance
ms.custom: admindeeplinkCOMPLIANCE
ms.openlocfilehash: 3a1a2fcebdc097b1402d866a2af59d3caac633d3
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63315603"
---
# <a name="plan-for-insider-risk-management"></a>Insider risk yönetimini planlama

Kurumda [Insider risk yönetimiyle](insider-risk-management.md) çalışmaya başlamadan önce, bilgi teknolojisi ve uyumluluk yönetim ekipleri tarafından gözden geçir edilmesi gereken önemli planlama etkinlikleri ve dikkate alınacak noktalar vardır. Aşağıdaki alanlarda dağıtımın kapsamlı bir şekilde anlaşılması ve planlanması, insider risk yönetimi özelliklerinin uygulama ve kullanımınızı sorunsuz bir şekilde gerçekleştirecek ve çözüme yönelik en iyi yöntemlerle uyumlu hale gelecek şekilde hazır hale getirecektir.

Insider risk yönetimi iş akışının, kuruluş değerlerinizi, kültürlerinizi ve kullanıcı deneyiminizi öncelik sırasına eklerken, riskleri engellemenize, algılamanıza ve içermenize nasıl yardımcı olduğunu öğrenmek için aşağıdaki videoyu izleyin:
<br>
<br>

>[!VIDEO https://www.microsoft.com/videoplayer/embed/RE4OUXB]

## <a name="work-with-stakeholders-in-your-organization"></a>Kuruluşta proje katılımcıları ile çalışma

Insider risk yönetimi uyarıları ve durumlarıyla ilgili eylemler için iş birliği yapmak için, organizasyonda uygun paydaşları tanımlayabilirsiniz. İlk planlamada dikkate almak üzere önerilen bazı paydaşlar ve uç-uç [insider risk yönetimi](insider-risk-management.md#workflow) iş akışı, kuruluşun aşağıdaki alanlarından kişilerdir:

- Bilgi teknolojisi
- Uyumluluk
- Gizlilik
- Güvenlik
- İnsan kaynakları
- Yasal

## <a name="determine-any-regional-compliance-requirements"></a>Bölgesel uyumluluk gereksinimlerini belirleme

Farklı coğrafi ve kuruluş alanlarının uyumluluk ve gizlilik gereksinimleri, kuruluşun diğer alanlarından farklı olabilir. Insider risk yönetiminde yer alan uyumluluk ve gizlilik denetimlerini ve bunların kuruluşun farklı alanlarında nasıl kullanılmaları gerektiğini anlamalarını sağlamak için bu alanlarda paydaşlarla birlikte çalışabilirsiniz. Bazı senaryolarda, uyumluluk ve gizlilik gereksinimleri, bazı paydaşları ilgili alana ilişkin bir kullanıcı veya mevzuat ya da ilke gereksinimlerine dayalı olarak soruşturmalar ve davalar için kısıtlayan ilkeler gerekli olabilir.

Belirli bölgeleri, rolleri veya bölmeleri içeren olay incelemelerine katılan belirli proje katılımcıları için gereksinimleriniz varsa, farklı bölgeleri ve popülasyonları hedef alan ayrı (aynı) [insider risk](insider-risk-management-policies.md) yönetimi ilkeleri uygulamak istiyor olabilir. Bu yapılandırma, doğru proje katılımcılarının rolleriyle ve bölgeleriyle ilgili vakaları öncelesini ve yönetmesini kolaylaştırır. Buna ek olarak, insider risk yönetimi uyarıları ve davaları için yükseltme sürecini kolaylaştırmaya yardımcı olmak için, kullanıcılarının ve gözden geçirenlerin aynı dili konuştuğu bölgeler için süreçler ve ilkeler oluşturmayı düşünebilirsiniz.

## <a name="plan-for-the-review-and-investigation-workflow"></a>gözden geçirme ve soruşturma iş akışını planlama

Insider risk yönetimi ilkelerini ve uyarılarını nasıl yönetmek istediğinize bağlı olarak, farklı Insider risk yönetimi özellikleri kümelerini yönetmek için kullanıcıları belirli rol gruplarına atamanız gerekir. Insider risk yönetimi özelliklerinin farklı alanlarını yönetmek için, belirli rol gruplarına farklı uyumluluk sorumluluklarına sahip kullanıcılar atama seçeneğiniz vardır. Ya da belirlenen yöneticiler, analistler, tahminler ve görüntüleyiciler için tüm kullanıcı hesaplarını Insider Risk Management rol grubuna atamaya karar veabilirsiniz. Uyumluluk yönetimi gereksinimlerinize en uygun şekilde tek bir rol grubu veya birden çok rol grubu kullanın.

Insider risk yönetimiyle çalışırken, bu rol grubu seçenekleri ve çözüm eylemleri arasında seçim yapabilirsiniz:

|**Eylemler**|**Insider Risk Yönetimi**|**Insider Risk Yönetimi Yöneticisi**|**İçeriden Risk Yönetimi Analistleri**|**İçeriden Risk Yönetimi Araştırmacıları**|**Insider Risk Yönetimi Denetçileri**|
|:----------|:--------------------------|:--------------------------------|:-----------------------------------|:----------------------------------------|:-----------------------------------|
| İlkeleri ve ayarları yapılandırma | Evet | Evet | Hayır | Hayır | Hayır |
| Access analiz içgörüleri | Evet | Evet | Evet | Hayır | Hayır |
| Access & araştırma uyarıları | Evet | Hayır | Evet | Evet | Hayır |
| Vakaları & Access araştıracak | Evet | Hayır | Evet | Evet | Hayır |
| Access & Gezgini'ni görüntüde görüntüleme | Evet | Hayır | Hayır | Evet | Hayır |
| Bildirim şablonlarını yapılandırma | Evet | Hayır | Evet | Evet | Hayır |
| Denetim & görüntüleme | Evet | Hayır | Hayır | Hayır | Evet |

>[!IMPORTANT]
>*Insider Risk Yönetimi veya Insider Risk Yönetimi* Yöneticisi rol gruplarında (seçtiğiniz seçen bağlı olarak) her zaman en az bir kullanıcınız olduğundan emin olun; böylelikle, insider risk yönetimi yapılandırmanız belirli kullanıcılar kuruluş içinden ayrılırsa "sıfır yönetici" senaryosuna girilamaz.

Aşağıdaki rollerin üyeleri kullanıcıları Insider risk yönetimi rol gruplarına ata atayar ve *Insider Risk Management Admin* rol grubuna dahil edilenlerle aynı çözüm izinlerine sahip olabilir:

- Azure Active Directory *Yönetici*
- Azure Active Directory *Uyumluluk Yöneticisi*
- Microsoft 365 uyumluluk merkezi *Yönetimi*
- Microsoft 365 uyumluluk merkezi *Uyumluluk Yöneticisi*

## <a name="understand-requirements-and-dependencies"></a>Gereksinimleri ve bağımlılıkları anlama

Insider risk yönetimi ilkelerini nasıl uygulamayı planla planınıza bağlı olarak, lisans aboneliklerini doğru lisanslama Microsoft 365 bazı çözüm önkoşullarını anlamanız ve planlamanız gerekir.

**Lisanslama:** Insider risk yönetimi, lisans abonelikleri ile ilgili geniş bir Microsoft 365 kapsamında yer sağlar. Ayrıntılı bilgi için [Insider risk yönetimiyle çalışmaya başlama makalesine](insider-risk-management-configure.md#subscriptions-and-licensing) bakın.

> [!IMPORTANT]
> Insider risk yönetimi, şu anda Azure hizmet bağımlılıkları tarafından desteklenen coğrafi bölgelerde ve ülkelerde barındırılan kiracılarda kullanılabilir. Insider risk yönetiminin organizasyonunız için destek olduğunu doğrulamak için bkz. [Ülkeye/bölgeye göre Azure bağımlılığı kullanılabilirliği](/troubleshoot/azure/general/dependency-availability-by-country).

Mevcut bir Microsoft 365 Kurumsal E5 planınız yoksa ve insider risk yönetimini denemek için mevcut aboneliğinize [Microsoft 365](/office365/admin/try-or-buy-microsoft-365) ekleyebilir veya Microsoft 365 Kurumsal E5 deneme sürümüne kaydolabilirsiniz.[](https://www.microsoft.com/microsoft-365/enterprise)

**İlke şablonu gereksinimleri:** Seçtiğiniz ilke şablonuna bağlı olarak, kurumda insider risk yönetimini yapılandırmadan önce anlamanız ve planlamanız gereken gereksinimler vardır:

- Ayrılan kullanıcı **şablonuyla** Veri hırsızlığı şablonunu kullanırken, Microsoft 365 kullanıcılar için düzenli aralıklarla sözleşmeli ve fesih tarihi bilgilerini içeri aktaracak bir Microsoft 365 hr bağlayıcısı yapılandırmanız gerekir. Microsoft 365 İk bağlayıcısını [kurum için](import-hr-data.md) yapılandırmaya yönelik adım adım kılavuz bilgiler için İk bağlayıcısı makalesine bakarak verileri içeri aktarın.
- Veri **sızıntıları** şablonlarını kullanırken, en az bir Veri Kaybı Önleme (DLP) ilkesi yapılandırarak, kuruluşta hassas bilgiler tanımlamanız ve Yüksek Önem Düzeyi DLP ilkesi uyarıları için insider risk uyarıları alamanız gerekir. DLP [ilkelerini yapılandırmayla ilgili adım](create-test-tune-dlp-policy.md) adım kılavuz için DLP ilkesi oluşturma, test ve ayarlama makalesine bakın.
- Güvenlik ilkesi **ihlali şablonlarını** kullanırken, güvenlik ihlal uyarılarını içeri aktaracak Defender Güvenlik Merkezi'nde Insider risk yönetimi tümleştirmesi için Uç Nokta için Microsoft Defender'ı etkinleştirmeniz gerekir. Insider risk yönetimiyle Uç Nokta tümleştirmesi için Defender'ı etkinleştirmeye yönelik adım adım kılavuz için bkz. Uç Nokta için [Microsoft Defender'da gelişmiş özellikleri yapılandırma](/windows/security/threat-protection/microsoft-defender-atp/advanced-features).
- Korkutucu kullanıcı **şablonlarını kullanırken**, Microsoft 365 İk bağlayıcısını, organizasyonu kullanan kullanıcılar için performansı veya etkiyi düşürme durum bilgilerini düzenli aralıklarla içeri aktarabilecek şekilde yapılandırmanız gerekir. Microsoft 365 İk bağlayıcısını [kurum için](import-hr-data.md) yapılandırmaya yönelik adım adım kılavuz bilgiler için İk bağlayıcısı makalesine bakarak verileri içeri aktarın.

## <a name="test-with-a-small-group-of-users-in-a-production-environment"></a>Üretim ortamında küçük bir kullanıcı grubuyla test

Çözümü üretim ortamınıza geniş bir şekilde etkinleştirmeden önce, kuruluş içinde gerekli uyumluluk, gizlilik ve yasal incelemeler için düzenleme yaparken küçük bir dizi üretim kullanıcısı ile ilkeleri test etmek göz önünde bulundurabilirsiniz. Test ortamında insider risk yönetimini değerlendirmek, triyak ve işleme durumlarında uyarılar oluşturmak için sanal kullanıcı eylemleri ve diğer sinyaller oluşturmanızı gerektirir. Bu yaklaşım çoğu kuruluş için pratik değildir, bu nedenle üretim ortamında küçük bir kullanıcı grubuyla insider risk yönetimini test etmek tercih edilir.

Araç içinde gizliliği korumak için bu test sırasında kullanıcı görünen adlarını Insider risk yönetim konsolunda anonimleştirmek için ilke ayarlarında anonimleştirme özelliğini etkin durumda tutabilirsiniz. Bu ayar, ilke eşleşmesi olan kullanıcıların gizliliğini korumaya yardımcı olur ve insider risk uyarıları için veri araştırmasında ve çözümleme incelemesinde nesnenin daha fazla yer korunmasına yardımcı olabilir.

Insider risk yönetimi ilkesi yapılandır hemen sonra herhangi bir uyarı görmüyorsanız, bu durum minimum risk eşiğinin henüz karşı bkz. İlkenin tetiklendiğinden ve beklendiği gibi çalışarak çalışarak, kullanıcının Kullanıcılar sayfasındaki ilkenin kapsamı içinde olup olduğunu denetlemenin iyi **bir yolu** .

## <a name="resources-for-stakeholders"></a>Paydaşlara kaynaklar

Insider risk yönetimi belgelerini, yönetiminize ve düzeltme iş akışınıza dahil olan kuruluşta yer alan paydaşlarla paylaşın:

- [Insider risk ilkelerini oluşturma ve yönetme](insider-risk-management-policies.md)
- [Insider risk etkinliklerini araştırma](insider-risk-management-activities.md)
- [Insider risk durumlarında eyleme geç](insider-risk-management-cases.md)
- [Insider riski olan İçerik gezgini ile vaka verilerini gözden geçirme](insider-risk-management-content-explorer.md)
- [Insider risk bildirimi şablonları oluşturma](insider-risk-management-notices.md)

## <a name="ready-to-get-started"></a>Başlamaya hazır mısınız?

Organizasyonunız için Insider risk yönetimini yapılandırmaya hazır mısınız? Aşağıdaki makaleleri gözden geçirin:

- [Genel ilke ayarlarını yapılandırmak için Insider risk](insider-risk-management-settings.md) yönetimi ayarlarıyla çalışmaya başlama.
- [Önkoşulları yapılandırmak, ilkeler](insider-risk-management-configure.md) oluşturmak ve uyarı almaya başlamak için Insider risk yönetimiyle çalışmaya başlama.
