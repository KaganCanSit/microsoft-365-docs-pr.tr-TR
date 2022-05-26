---
title: Microsoft Purview Uyumluluk Yöneticisi'ndeki yenilikler
f1.keywords:
- NOCSH
ms.author: chvukosw
author: chvukosw
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- m365solution-compliancemanager
- m365initiative-compliance
search.appverid:
- MOE150
- MET150
description: Uyumluluk Yöneticisi'ndeki yeniliklere ve gelecek yeniliklere ulaşın. Güncelleştirilmiş değerlendirmeler, yeni değerlendirme şablonları, yeni eylemler ve daha fazlası hakkında bilgi edinin.
ms.openlocfilehash: cf817b28c6d375e92e7aabdb1f57ea632c6f1a28
ms.sourcegitcommit: 852075d8d8a4ca052f69e854396d1565ef713500
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/26/2022
ms.locfileid: "65692749"
---
# <a name="whats-new-in-microsoft-purview-compliance-manager"></a>Microsoft Purview Uyumluluk Yöneticisi'ndeki yenilikler

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

**Bu makalede:** Uyumluluk Yöneticisi'ndeki son güncelleştirmeler hakkında bilgi edinin.

## <a name="may-2022"></a>Mayıs 2022

Uyumluluk Yöneticisi aşağıdaki yeni değerlendirme şablonlarını yayımladı:

Avrupa, Orta Doğu ve Afrika (EMEA)
- Katar Ulusal Bilgi Güvencesi (NIA)
- BAE Veri Gizliliği Yasası

ABD Kamu Community (GCC) Orta, GCC Yüksek ve Savunma Bakanlığı (DoD) müşterileri bu şablonları önümüzdeki birkaç hafta içinde kullanıma sunmalıdır.

[Değerlendirme şablonlarının tam listesini](compliance-manager-templates-list.md) görüntüleyin.

## <a name="march-2022"></a>Mart 2022

### <a name="new-templates-available"></a>Yeni şablonlar kullanılabilir

Uyumluluk Yöneticisi aşağıdaki yeni değerlendirme şablonlarını yayımladı:

**Genel**
- ISO 37301
- NIST 800-207 - Sıfır Güven Mimarisi
- SIG 2022

**ABD Hükümeti**
- CMMC v2 Düzey 1
- CMMC v2 Düzey 2

**Kuzey Amerika**
- Bilgi Güvenliği Yönetim Yasası - Britanya Kolumbiyası Eyaleti, CA

[Değerlendirme şablonlarının tam listesini](compliance-manager-templates-list.md) görüntüleyin.

### <a name="continuous-compliance-assessment-of-improvement-actions"></a>İyileştirme eylemlerinin sürekli uyumluluk değerlendirmesi

Uyumluluk Yöneticisi'nde daha önce Güvenli Puan kapsamında olmayan 35'in üzerinde geliştirme eylemi için otomatik test ve kanıt oluşturma işlemi ekliyoruz. Sürekli uyumluluk değerlendirmesiyle, uyumluluk değerlendirmelerinizle ilgiliyse ve ilgili çözümlere erişme lisansınız varsa bu iyileştirme eylemlerinden hangilerini tamamladığınızla ilgili güncelleştirmeler alabilirsiniz. Sürekli uyumluluk değerlendirmesi ayrıca kullanıcılara iyileştirme eylemlerinizin puanlama mantığı hakkında görünürlük sağlar ve neden belirli bir puan aldığınıza ilişkin içgörü ve kanıt sağlar. Bu özellik, Microsoft 365 Güvenli Puan ile mevcut tümleştirmelerle birlikte çalışır ve daha önce yapılandırdığınız tüm otomatik eylemler olduğu gibi çalışmaya devam eder. [Otomatik test ayarları](compliance-manager-setup.md#set-up-automated-testing) hakkında daha fazla bilgi edinin.

## <a name="february-2022"></a>Şubat 2022

### <a name="alerts-and-alert-policies"></a>Uyarılar ve uyarı ilkeleri

Kullanıcılar artık Uyumluluk Yöneticisi'nde bir kuruluşun izlemek istediği değişiklikler için uyarılar ayarlayabilir. Kolay kurulum sihirbazını kullanarak, aşağıdaki olay türleri gerçekleştiğinde bildirim oluşturmak için uyarı ilkeleri oluşturabilirsiniz: geliştirme eylem puanı değişikliği, iyileştirme eylemi atama değişikliği, geliştirme eyleminde test veya uygulama durumu değişikliği ve bir iyileştirme eyleminin Belgeler sekmesinde dosya yükleme veya silme. [Uyumluluk Yöneticisi uyarıları ve uyarı ilkeleri](compliance-manager-alert-policies.md) sayfasını ziyaret ederek daha fazla bilgi edinin.

### <a name="try-recommended-assessment-templates-for-your-organization"></a>Kuruluşunuz için önerilen değerlendirme şablonlarını deneyin

Kuruluşunuz artık, çalışmaya başlamak için hızlı bir kurulum işlemiyle hangi değerlendirmelerin sizin için en uygun olabileceği konusunda Uyumluluk Yöneticisi'nden öneriler alabilir. Öneriler ve lisans satın almadan önce premium değerlendirme şablonlarını deneme hakkında daha fazla bilgi edinmek için bkz. [Premium değerlendirme denemesi başlatma](compliance-manager-setup.md#start-a-premium-assessments-trial).

## <a name="november-2021"></a>Kasım 2021

### <a name="zero-trust-integration-for-the-data-protection-baseline-template"></a>Veri Koruma Temeli şablonu için Sıfır Güven tümleştirmesi

Sıfır Güven, her işlemi açıkça ve sürekli olarak doğrulayan, en az ayrıcalığı onaylayan ve tehditlere karşı akıllı, gelişmiş algılama ve gerçek zamanlı yanıta dayalı, dijital varlığın tüm katmanları arasında güvenlik için proaktif, tümleşik bir yaklaşımdır. Tüm kullanıcılara dahil edilen Uyumluluk Yöneticisi'nin Veri Koruma Temeli şablonu, artık aşağıdaki denetim aileleri arasında uyumlu Sıfır Güven için 57 yeni denetimi ve 36 yeni eylemi tümleştirir:

- Sıfır Güven Uygulaması
- Sıfır Güven Uygulama geliştirme kılavuzu
- Sıfır Güven Uç Noktası
- verileri Sıfır Güven
- Sıfır Güven Kimliği
- Sıfır Güven Altyapısı
- ağ Sıfır Güven
- Sıfır Güven Görünürlük, otomasyon ve düzenleme

### <a name="new-preview-templates"></a>Yeni önizleme şablonları

Aşağıdaki değerlendirme şablonları önizleme aşamasında kullanıma sunulmuştur:

- Azure için ISO 27001:2013 (Önizleme)
- Dynamics 365 için ISO 27001:2013 (Önizleme)
- Dynamics 365 için FedRAMP Moderate (Önizleme)
- Azure için FedRAMP Moderate (Önizleme)
- Azure için FedRAMP High (Önizleme)
- Dynamics 365 için FedRAMP High (Önizleme)
- Azure için SOC 2 (Önizleme)
- Dynamics 365 için SOC 2 (Önizleme)
- Azure için ISO 27018:2019 (Önizleme)
- Dynamics 365 için ISO 27018:2019 (Önizleme)

## <a name="october-2021"></a>Ekim 2021

### <a name="new-assessment-templates"></a>Yeni değerlendirme şablonları

Aşağıdakileri içeren yeni değerlendirme şablonları yayımladık:

- Colorado Gizlilik Yasası (CPA)
- Virginia Tüketici Verileri Gizlilik Yasası (CDPA)
- Mısır - Veri Koruma Yasası
- Avustralya - ASD Temel 8 Olgunluk Düzeyi 1
- Avustralya - ASD Essential 8 Olgunluk Düzeyi 2
- Avustralya - ASD Essential 8 Olgunluk Düzeyi 3

### <a name="integration-with-microsoft-priva"></a>Microsoft Priva ile tümleştirme

Uyumluluk Yöneticisi artık kuruluşunuzun Microsoft 365 depoladığınız kişisel verileri korumanıza yardımcı olabilecek bir çözüm olan Microsoft Priva ile birlikte çalışabilir. Priva verilerinizi görselleştirmenize ve anlamanıza, önemli risk senaryolarını yönetmeye ve konu hakları isteklerini işlemeye yönelik ilkeler uygulamanıza yardımcı olacak araçlar sunar. Depoladığınız kişisel verileri korumak için Priva adımlarını uyguladığınızda bu, Uyumluluk Yöneticisi'ndeki gizlilik değerlendirmelerinize katkıda bulunabilir ve uyumluluk puanınızı geliştirmenize yardımcı olabilir. Priva ve diğer çözümlerin puanınıza nasıl katkıda bulunduğuna bakmak ve daha fazla geliştirme için olası fırsatlar hakkında bilgi edinmek için Uyumluluk Yöneticisi'ndeki **Çözümler** sekmesine bakın. Priva hakkında daha fazla ayrıntıyı [Microsoft Priva hakkında bilgi edinin](/privacy/priva) makalesinde de bulabilirsiniz.

## <a name="july-2021"></a>Temmuz 2021

Şablonlarımızın yeni evrensel sürümlerini temel alarak Microsoft 365 dışındaki ürünler için değerlendirmeler oluşturma özelliğini ekledik. Daha fazla bilgi edinmek için [Değerlendirme şablonlarıyla çalışma ile](compliance-manager-templates.md) başlayın.

## <a name="may-2021"></a>Mayıs 2021

### <a name="new-assessment-templates"></a>Yeni değerlendirme şablonları

Şu 75 yeni değerlendirme şablonu yayımladık:
- Avustralya Gizlilik Yasası
- CIS Microsoft 365 Temel Düzeyleri 1 ve 2
- Almanya - Finansal Kurumlarda BT için Denetim Gereksinimleri (BAIT)
- Sarbanes-Oxley Yasası
- Güney Afrika - Bilgiye Erişimin Teşviki Yasası

[Değerlendirme şablonlarının](compliance-manager-templates-list.md) tam listesine göz atın.

## <a name="april-2021"></a>Nisan 2021

### <a name="support-for-us-government-dod-customers"></a>US Government DoD müşterileri için destek

Uyumluluk Yöneticisi artık US Government DoD müşterilerinin yanı sıra US Government Community (GCC) Moderate ve GCC High müşterileri tarafından da kullanılabilir.

## <a name="march-2021"></a>Mart 2021

### <a name="active-and-inactive-templates"></a>Etkin ve etkin olmayan şablonlar

Her değerlendirme sayfası ve değerlendirme şablonu sayfasında etkinleştirilmiş şablonlar sayacı vardır. Bu sayaç, lisans sözleşmenize göre kaç uygun şablon kullandığınızı gösterir. Daha fazla bilgi edinmek için [Şablon kullanılabilirliğini ve lisanslamasını](compliance-manager-templates.md#template-availability-and-licensing) görüntüleyin.
