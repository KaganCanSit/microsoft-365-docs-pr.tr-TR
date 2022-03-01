---
title: Insider risk yönetimi hakkında bilgi
description: Kuruluş içinde Insider risk yönetimiyle, organizasyonda riski en aza indirmeye nasıl yardımcı Microsoft 365.
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
ms.collection:
- m365-security-compliance
- m365solution-insiderrisk
- m365initiative-compliance
ms.openlocfilehash: f1911dcfa697d620e8d5d2109cc0d21e9638e5b5
ms.sourcegitcommit: 39838c1a77d4e23df56af74059fb95970223f718
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2022
ms.locfileid: "63010765"
---
# <a name="learn-about-insider-risk-management-in-microsoft-365"></a>Microsoft 365'da Insider risk yönetimi hakkında bilgi Microsoft 365

Insider risk yönetimi, Microsoft 365'de bulunan ve organizasyonda kötü amaçlı ve yanlışlıkla yapılan etkinlikleri algılamanıza, araştırmanıza ve bu etkinliklere yönelik eylemlerinizi gerçekleştirerek dahili riskleri en aza indirmenize yardımcı olan bir uyumluluk çözümüdür. Insider risk ilkeleri, davalar üzerinde hareket etmek ve gerekirse davaları Microsoft'a geri yükseltme dahil olmak üzere, tanımlamak Advanced eDiscovery riskleri tanımlamanıza olanak sağlar. Organizasyonu kullanan risk analistleri, kullanıcıların kuruluş uyumluluk standartlarına uygun olduğundan emin olmak için uygun eylemleri hızla gerçekleştirebilirsiniz.

Insider risk yönetiminin, kuruluş değerlerinizi, kültürlerinizi ve kullanıcı deneyiminizi öncelik sırasıyla belirlemenin, riskleri algılamanıza ve engellemenize nasıl yardımcı olduğunu öğrenmek için aşağıdaki videoları izleyin:
<br>
<br>

**Geliştirme için Insider risk & çözümü**:
>[!VIDEO https://www.microsoft.com/videoplayer/embed/RE4j9CN]
<br>

**Insider risk yönetimi iş akışı**:
>[!VIDEO https://www.microsoft.com/videoplayer/embed/RE4OUXB]

> [!IMPORTANT]
> Insider risk yönetimi, şu anda Azure hizmet bağımlılıkları tarafından desteklenen coğrafi bölgelerde ve ülkelerde barındırılan kiracılarda kullanılabilir. Insider risk yönetiminin organizasyonunız için destek olduğunu doğrulamak için bkz. [Ülkeye/bölgeye göre Azure bağımlılığı kullanılabilirliği](/troubleshoot/azure/general/dependency-availability-by-country).

## <a name="modern-risk-pain-points"></a>Modern risk noktaları

Organizasyonda riski yönetme ve en aza indirme, modern çalışma yerinde bulunan risk türlerini anlamayla başlar. Bazı riskler dış olaylar ve doğrudan denetimin dışında olan etmenler tarafından yönlendiriliyor. Diğer riskler, simge durumuna küçültilebilecek ve kaçınilebilecek iç olaylar ve kullanıcı etkinlikleri tarafından yönlendirildi. Bazı örnekler, kuruluşta yer alan kullanıcılar tarafından yasa dışı, uygun olmayan, yetkisiz veya etik olmayan davranışlardan ve eylemlerden risklerdir. Bu davranışlar, kullanıcılardan gelen çok çeşitli iç riskleri içerir:

- Hassas verilerin ve veri taşmalarının sızıntıları
- Gizlilik ihlalleri
- Fikri mülkiyet (IP) hırsızlığı
- Dolandırıcılık
- Insider alım satım
- Mevzuat uyumluluğu ihlalleri

Modern çalışma alanı içinde yer alan kullanıcıların çeşitli platformlar ve hizmetler genelinde veri oluşturma, yönetme ve paylaşma erişimi vardır. Çoğu durumda, kuruluşlar kuruluş genelindeki riskleri belirlemeye ve azaltmak için, ayrıca kullanıcı gizlilik standartlarına uygun kaynaklara ve araçlara sahiptir.

Insider risk yönetimi, risk etkinliğini hızla tanımlamanıza, öncelik belirlemeye ve değerlendirmeye yardımcı olmak için eksiksiz hizmet ve üçüncü taraf göstergeleri kullanır. Insider risk yönetimi Microsoft 365 Microsoft Graph günlükleri kullanarak, risk göstergelerini tanımlamak için belirli ilkeler tanımlamanıza olanak sağlar. Bu ilkeler, riskli etkinlikleri tanımlamanıza ve bu riskleri azaltmak için eylemde bulundurmanıza olanak sağlar.

Insider risk yönetimi aşağıdaki ilkeler çerçevesinde ortalandı:

- **Saydamlık**: Tasarıma göre gizlilik mimarisiyle kullanıcı gizliliğini ve kuruluş riskini dengeler.
- **Yapılandırılabilir**: Sektöre, coğrafi gruplara ve iş gruplarına dayalı olarak yapılandırılabilir ilkeler.
- **Tümleşik**: Uyumluluk çözümleri genelinde tümleşik Microsoft 365 iş akışı.
- **İşlem Edilebilir**: Gözden geçiren bildirimleri, veri soruşturmalarını ve kullanıcı soruşturmalarını etkinleştirmek için içgörüler sağlar.

## <a name="identifying-potential-risks-with-analytics"></a>Analizle olası riskleri belirleme

Insider risk analizi, insider risk ilkelerini yapılandırmadan, organizasyonumda olası insider risklerini değerlendirmenizi sağlar. Bu değerlendirme, kuruluşa daha yüksek kullanıcı riski olan olası alanları belirlemede yardımcı olabilir ve yapılandırmayı göz önünde bulundurarak göz önünde bulundurarak, insider risk yönetimi ilkelerinin türünü ve kapsamını belirlemeye yardımcı olabilir. Bu değerlendirme, ek lisanslama veya mevcut Insider risk ilkelerinin gelecekteki iyileştirmesi  ihtiyaçlarını belirlemenize de yardımcı olabilir.

Insider risk analizi hakkında daha fazla bilgi edinmek için [bkz. Insider risk yönetimi ayarları: Analiz](insider-risk-management-settings.md#analytics).

## <a name="get-started-with-recommended-actions-preview"></a>Önerilen eylemleri (önizleme) başlama

İster ilk kez Insider risk yönetimini ayarlarken ister yeni ilkeler oluşturmaya başlarken, önerilen eylemler deneyimi Insider risk yönetimi [](insider-risk-management-configure.md#recommended-actions-preview) yetenekleriden en iyi şekilde çıkmanıza yardımcı olabilir. Önerilen eylemler arasında izinleri ayarlama, ilke göstergeleri seçme, ilke oluşturma ve daha fazlası yer almaktadır.

## <a name="workflow"></a>İş Akışı

Insider risk yönetimi iş akışı, kuruluş içindeki iç riskleri tanımlamanıza, araştırmanıza ve bu risklere karşı harekete çalışmanıza yardımcı olur. Odaklanmış ilke şablonları, Microsoft 365 hizmeti genelinde kapsamlı etkinlik sinyali ve uyarı ve olay yönetim araçlarıyla, riskli davranışı hızla tanımlamak ve buna göre hareket etmek için işlemde değiştirilebilir öngörüler kullanabilirsiniz.

Şirket içi risk etkinliklerini tanımlama ve çözme ve Insider risk yönetimiyle ilgili uyumluluk Microsoft 365 iş akışı kullanılır:

![Insider risk yönetimi iş akışı.](../media/insider-risk-workflow.png)

### <a name="policies"></a>İlkeler

[Insider risk yönetimi](insider-risk-management-policies.md) ilkeleri, olayları ve risk göstergelerini tetikleyen olayları ve risk göstergelerini tanımlayan önceden tanımlanmış şablonlar ve ilke koşulları kullanılarak oluşturulur. Bu koşullar, uyarılarda risk göstergelerinin nasıl kullanılmalarını, ilkeye hangi kullanıcıların dahil olduğunu, hangi hizmetlerin önceliklerinin olduğunu ve izleme süresi hakkında bilgi içerir.

Insider risk yönetimini hızla kullanmak için aşağıdaki ilke şablonlarından birini seçin:

- [Ayrılan kullanıcılarla veri hırsızlığı](insider-risk-management-policies.md#data-theft-by-departing-users)
- [Genel veri sızıntıları](insider-risk-management-policies.md#general-data-leaks)
- [Öncelik kullanıcıların veri sızıntıları (önizleme)](insider-risk-management-policies.md#data-leaks-by-priority-users-preview)
- [Göz korkutucu kullanıcıların veri sızıntıları (önizleme)](insider-risk-management-policies.md#data-leaks-by-disgruntled-users-preview)
- [Genel güvenlik ilkesi ihlalleri (önizleme)](insider-risk-management-policies.md#general-security-policy-violations-preview)
- [Genel hasta verileri yanlış kullanımı (önizleme)](insider-risk-management-policies.md#general-patient-data-misuse-preview)
- [Ayrılan kullanıcılarla güvenlik ilkesi ihlalleri (önizleme)](insider-risk-management-policies.md#security-policy-violations-by-departing-users-preview)
- [Öncelik kullanıcıların güvenlik ilkesi ihlalleri (önizleme)](insider-risk-management-policies.md#security-policy-violations-by-priority-users-preview)
- [Korkutucu kullanıcıların güvenlik ilkesi ihlalleri (önizleme)](insider-risk-management-policies.md#security-policy-violations-by-disgruntled-users-preview)

![Insider risk yönetimi ilkesi panosu.](../media/insider-risk-policy-dashboard.png)

### <a name="alerts"></a>Uyarılar

Uyarılar, ilke koşullarına uygun risk göstergeleri tarafından otomatik olarak oluşturulur ve [Uyarılar panosunda görüntülenir](insider-risk-management-activities.md#alert-dashboard). Bu pano, gözden geçirmesi gereken tüm uyarıların, zaman içinde açık uyarıların ve kurum için uyarı istatistiklerinin hızlı bir görünümüne olanak sağlar. Var olan uyarıların ve eylem gereken yeni uyarıların durumunu hızla tanımlamanıza yardımcı olmak için, tüm ilke uyarıları aşağıdaki bilgilerle görüntülenir:

- Durum
- Önem Derecesi
- Algılanan saat
- Büyük//harf
- Vaka durumu

![Insider risk yönetimi uyarı panosu.](../media/insider-risk-alerts-dashboard.png)

### <a name="triage"></a>Triyale

Araştırma yapılması gereken yeni kullanıcı etkinlikleri, Ihtiyaçları gözden geçirme durumuna atanan uyarıları otomatik *olarak* üretir. Gözden geçirenler bu uyarıları hızla tanımlayabilir, gözden geçirip değerlendirip, önceliklerini belirlemeye ve değerlendirmeye yardımcı olabilir.

Uyarılar, yeni bir vaka açarak, uyarıyı var olan bir vakaya ataarak veya uyarıyı reddederek çözülür. Uyarı filtrelerini kullanarak, uyarıları durum, önem derecesi veya algılanan saatlere göre hızla tanımlamak kolaydır. Değerlendirme işlemi kapsamında, gözden geçirenler ilke tarafından tanımlanan etkinliklere ilişkin uyarı ayrıntılarını  görebilir, ilke eşleşmesi ile ilişkili kullanıcı etkinliğini  görebilir, uyarının önem derecesini görebilir ve kullanıcı profili bilgilerini gözden geçirebilirsiniz.

![Insider risk yönetimi önceliği.](../media/insider-risk-triage.png)

### <a name="investigate"></a>Araştır

Kullanıcı etkinliği raporları (önizleme) ile seçili kullanıcının tüm [etkinliklerini hızla araştırabilirsiniz](insider-risk-management-activities.md#user-activity-reports-preview). Bu raporlar, kuruluşlarda bir kullanıcıya geçici veya açık olarak bir insider risk yönetimi ilkesi atamak zorunda kalmadan, tanımlı bir süre boyunca belirli kullanıcıların etkinliklerini incelemelerine olanak sağlar. Bir kullanıcının etkinliklerini inceledikten sonra, güvenlik açıkları tek tek etkinlikleri kapatarak sömey etkinlikleri yok sayma, rapora bağlantı paylaşma veya diğer parolalarla e-postayla gönderme ya da kullanıcıları geçici veya açık olarak insider risk yönetimi ilkesine atamayı seçme.

[Olaylar](insider-risk-management-cases.md) , ilke eşleşmesi ile ilgili etkinlik ayrıntılarının ve durumlarının daha ayrıntılı incelemesini ve incesini gerektiren uyarılar için oluşturulur. Vaka **panosu tüm** etkin vakaların, zaman içinde açık vakaların ve kurum için vaka istatistiklerinin hepsi hazır görünümünü sağlar. Gözden geçirenler vakaları durum, vakanın açılamadısı tarih ve son güncelleştirme tarihine göre hızla filtreleyebilir.

Olay panosunda bir vaka seçerek inceleme ve inceleme için vakayı açabilirsiniz. Bu adım, insider risk yönetimi iş akışının kalbidir. Bu alanda risk etkinlikleri, ilke koşulları, uyarı ayrıntıları ve kullanıcı ayrıntıları gözden geçirenler için tümleşik bir görünümde birleştirilmiş olarak birleştirilmiştir. Bu  kapsamındaki birincil araştırma araçları:

- **Kullanıcı etkinliği**: Kullanıcı etkinliği, zaman içinde etkinlikleri çizen ve mevcut veya geçmiş risk etkinlikleri için risk düzeyine göre etkileşimli bir grafikte otomatik olarak görüntülenir. Gözden geçirenler, kullanıcının tüm risk geçmişini hızla filtreleyen ve süzer ve daha ayrıntılı bilgi için belirli etkinliklerde detaya inerler.
- **İçerik gezgini**: Uyarı etkinlikleriyle ilişkili tüm veri dosyaları ve e-posta iletileri otomatik olarak yakalanır ve İçerik gezgininde görüntülenir. Gözden geçirenler, dosyaları ve iletileri veri kaynağına, dosya türüne, etiketlere, konuşmaya ve daha birçok özelliğe göre filtre uygulama ve görüntüleme.
- **Olay notları**: Gözden geçirenler, Vaka Notları bölümünde davayla ilgili notlar sağlar. Bu liste merkezi bir görünümde tüm notları birleştirerek gözden geçiren ve gönderilen tarihi içerir.

![Insider risk yönetimi soruşturması.](../media/insider-risk-investigate.png)

Buna ek olarak, [yeni Denetim günlüğü (önizleme),](insider-risk-management-audit-log.md) Insider risk yönetimi özelliklerinde yapılan işlemler hakkında bilgi sahibi kalmanız için olanak sağlar. Bu kaynak, bir veya birden çok insider risk yönetimi rol gruplarına atanan kullanıcıların  gerçekleştirdığı eylemlerin bağımsız bir şekilde gözden geçir 100 kez gözden geçir 10.

### <a name="action"></a>Eylem

Vakalar araştırıldıktan sonra, gözden geçirenler vakayı çözmek veya organizasyonunuzu diğer risk katılımcılarıyla işbirliği yapmak için hızlı bir şekilde harekete geçecektir. Kullanıcılar yanlışlıkla veya yanlışlıkla ilke koşullarını ihlal ediyorsa, kullanıcıya, sizin için özelleştirebileceğiniz bildirim şablonlarından basit bir anımsatıcı bildirimi gönderebilirsiniz. Bu bildirimler basit anımsatıcılar olarak veya gelecekte riskli davranışı önlemeye yardımcı olmak için kullanıcıyı yenileme eğitimine veya rehberlike yönlendirecektir. Daha fazla bilgi için [bkz. Insider risk yönetimi bildirim şablonları](insider-risk-management-notices.md).

Daha ciddi durumlarda, insider risk yönetimi durumu bilgilerini kuruluş içindeki diğer gözden geçirenlerle veya hizmetlerle paylaşmanız gerekir. Insider risk yönetimi,  uç uç risk Microsoft 365 yardımcı olmak için diğer uyumluluk çözümleriyle sıkı bir şekilde tümleştirilmiştir.

- **Advanced eDiscovery**: Vakayı soruşturma için yükseltme, verilerin ve yönetiminin aynı zamanda başka bir Advanced eDiscovery'a Microsoft 365. Advanced eDiscovery, kurum içi ve dış araştırmalarında yanıt veren içerikleri korumak, toplamak, gözden geçirmek, çözümlemek ve dışarı aktarmak için  uç uç iş akışı sağlar. Yasal ekiplere yasal tutma bildirimi iş akışının tamamını yönetmesini sağlar. Bu tür durumlar hakkında daha Advanced eDiscovery fazla bilgi edinmek için bu konuda [daha fazla bilgi Advanced eDiscovery' Microsoft 365](overview-ediscovery-20.md).
- **Office 365 Yönetimi API'leri tümleştirmesi (önizleme)**: Insider risk yönetimi, uyarı bilgilerini Güvenlik Yönetimi API'leri aracılığıyla güvenlik bilgileri ve olay yönetimi (SIEM) hizmetleri Office 365 destekler. Platformda uyarı bilgilerine erişimin, kuruluşun risk süreçlerine en uygun şekilde erişmeniz, risk etkinlikleri üzerinde işlem konusunda size daha fazla esneklik sağlar. Uyarı bilgilerini yönetim API'leriyle birlikte dışarı aktarma Office 365 için Bkz. [Uyarıları dışarı aktarma](insider-risk-management-settings.md#export-alerts).

> [!NOTE]
> ServiceNow bağlayıcısı önizlemesi sırasında geri bildiriminiz ve desteğiniz için teşekkür ederiz. 30 Kasım 2020 tarihinde ServiceNow bağlayıcı önizlemesini sona erdir karar verdik ve Insider risk yönetiminde desteği sona erdirelim. Müşterilere ServiceNow tümleştirmesi sağlamak için alternatif yöntemleri etkin bir şekilde değerlendiririz Insider risk yönetimiyle tümleştirme.

## <a name="scenarios"></a>Senaryolar

Insider risk yönetimi, çeşitli yaygın senaryolarda, kuruluş içindeki riskleri algılamanıza, araştırmanıza ve bu riskleri azaltmak için işlemnize yardımcı olabilir:

### <a name="data-theft-by-departing-users"></a>Ayrılan kullanıcılarla veri hırsızlığı

Kullanıcılar kuruluşlardan isteğe bağlı olarak veya fesih sonucu olarak ayrılsa da, çoğunlukla şirket, müşteri ve kullanıcı verileri risk altında olduğu konusunda yasal kaygılar ortaya çıkar. Kullanıcılar aslında proje verilerin mülkiyeti kapsamında olmadığını varsaysa da, şirket verilerini kişisel kazanç için ve şirket ilke ve yasal standartlarını ihlal etmek için almak cazip olabilir. Ayrılan kullanıcılar ilke şablonuyla Veri hırsızlığı kullanan [](insider-risk-management-policies.md#policy-templates) Insider risk yönetimi ilkeleri normalde bu tür bir hırsızlıkla ilişkilendirilmiş etkinlikleri otomatik olarak algılar. Bu ilkeyle, kullanıcıları ayrılan ve veri hırsızlığıyla ilişkilendirilmiş şüpheli etkinliklere yönelik otomatik olarak uyarılar alırsınız, böylece uygun yatırım önlemlerini gerçekleştirebilirsiniz. Bu ilke şablonu [Microsoft 365 İk bağlayıcısı](import-hr-data.md) için bir İk bağlayıcısı yapılandırmak gerekir.

### <a name="intentional-or-unintentional-leak-of-sensitive-or-confidential-information"></a>Hassas veya gizli bilgilerin bilerek veya kasıtsız olarak sızdırılmış olması

Çoğu durumda, kullanıcılar hassas veya gizli bilgileri düzgün bir şekilde işlemek için en iyi şekilde deneyebilirler. Ancak bazen kullanıcılar hata yapabilir ve bilgiler yanlışlıkla kuruluş dışında paylaşılır veya bilgi koruma ilkeleriniz ihlal edildi. Diğer durumlarda, kullanıcılar hassas ve gizli bilgileri kötü amaçlı amaçlarla veya olası kişisel kazançlar için bilerek sızdırmış veya paylaşabilir. Aşağıdaki Veri sızıntıları ilke şablonları kullanılarak oluşturulan Insider risk yönetimi ilkeleri, normalde hassas veya gizli bilgileri paylaşmayla ilişkilendirilmiş etkinlikleri otomatik olarak algılar:

- [Genel veri sızıntıları](insider-risk-management-policies.md#general-data-leaks)
- [Öncelik kullanıcıların veri sızıntıları (önizleme)](insider-risk-management-policies.md#data-leaks-by-priority-users-preview)
- [Göz korkutucu kullanıcıların veri sızıntıları (önizleme)](insider-risk-management-policies.md#data-leaks-by-disgruntled-users-preview)

## <a name="intentional-or-unintentional-security-policy-violations-preview"></a>Bilerek veya kasıtsız güvenlik ilkesi ihlalleri (önizleme)

Kullanıcıların modern çalışma alanında cihazlarını yönetmeleri normalde büyük ölçüde denetime sahip olur. Bu denetim, görevlerin performansında gereken uygulamaları yükleme veya kaldırma izinlerini veya cihaz güvenlik özelliklerini geçici olarak devre dışı bırakma yeteneğini içerebilir. Bu etkinlik yanlışlıkla, yanlışlıkla veya kötü amaçlı olsa da, bu davranış organizasyon açısından riskler oluştursa da, bunu tanımlamanız ve simge durumuna küçültmek için eylemde yer almak önemlidir. Bu riskli güvenlik etkinliklerinin kimliğini doğrulamaya yardımcı olmak için, aşağıdaki Insider risk yönetimi güvenlik ilkesi ihlal şablonları güvenlik riski göstergelerini puanlar ve güvenlikle ilgili etkinliklere yönelik öngörüler sağlamak için Uç Nokta için Microsoft Defender uyarılarını kullanır:

- [Genel güvenlik ilkesi ihlalleri (önizleme)](insider-risk-management-policies.md#general-security-policy-violations-preview)
- [Ayrılan kullanıcılarla güvenlik ilkesi ihlalleri (önizleme)](insider-risk-management-policies.md#security-policy-violations-by-departing-users-preview)
- [Öncelik kullanıcıların güvenlik ilkesi ihlalleri (önizleme)](insider-risk-management-policies.md#security-policy-violations-by-priority-users-preview)
- [Korkutucu kullanıcıların güvenlik ilkesi ihlalleri (önizleme)](insider-risk-management-policies.md#security-policy-violations-by-disgruntled-users-preview)

## <a name="policies-for-users-based-on-position-access-level-or-risk-history-preview"></a>Konum, erişim düzeyi veya risk geçmişine (önizleme) dayalı kullanıcılar için ilkeler

Kuruluşta yer alan kullanıcıların konumlarına, hassas bilgilere erişim düzeylerine veya risk geçmişine bağlı olarak farklı risk düzeyleri olabilir. Bu yapıda, kuruluş yönetim liderlik ekibinin üyeleri, kapsamlı veriler ve ağ erişimi ayrıcalıklarına sahip IT yöneticileri veya geçmişteki riskli etkinlikler geçmişine sahip kullanıcılar yer almaktadır. Bu koşullarda, daha yakın inceleme ve daha saldırgan risk puanlama, soruşturma ve hızlı işlem için yüzey uyarıları konusunda yardımcı olmak açısından önemlidir. Bu tür kullanıcılar için riskli etkinliklerin belirlenmesine yardımcı olmak için, öncelik kullanıcı grupları oluşturabilir ve aşağıdaki ilke şablonlarından ilkeler oluşturabilirsiniz:

- [Öncelik kullanıcıların güvenlik ilkesi ihlalleri (önizleme)](insider-risk-management-policies.md#security-policy-violations-by-priority-users-preview)
- [Öncelik kullanıcıların veri sızıntıları (önizleme)](insider-risk-management-policies.md#data-leaks-by-priority-users-preview)

## <a name="healthcare-preview"></a>Sağlık (önizleme)

Sağlık sektöründeki kuruluşlar için yapılan son çalışmalar, insider ile ilgili çok yüksek oranda veri ihlalleri olduğunu tespit etti. Hasta verileriyle sağlık kaydı bilgisinin yanlış kullanımını algılamak, hasta gizliliğini korumanın ve Sağlık Sigortası Taşınabilirlik ve Sorumluluk Yasası (HIPAA) ve Ekonomik ve Klinik Sağlık (HITECH) Yasası için Sağlık Bilgileri Teknolojisi gibi uyumluluk düzenlemelerine uymanın kritik bir bileşenidir. Hasta veri yanlışı, ayrıcalıklı hasta kayıtlarına erişmekten kötü amaçlı hasta kayıtlarına erişmeye kadar değişiklik gösterir. Bu tür riskli etkinliklerin kimliklerini doğrulamaya yardımcı olmak için, aşağıdaki insider risk yönetimi ilkesi şablonları Microsoft 365 HR bağlayıcısını ve sağlıkla ilgili veri bağlayıcısını kullanarak, elektronik ısı kaydı (EHR) sistemleriniz içinde meydana gelebilir davranışlarla ilgili puanlama riski göstergelerini başlatmaya başlar:

- [Genel hasta verileri yanlış kullanımı (önizleme)](insider-risk-management-policies.md#general-patient-data-misuse-preview)

## <a name="actions-and-behaviors-by-disgruntled-users-preview"></a>Göz korkutucu kullanıcıların eylemleri ve davranışları (önizleme)

Çalışma, olayların, insider riskleri ile ilgili çeşitli şekillerdeki kullanıcı davranışını etkiley riski olduğunu vurgular. Bu strese sahip kullanıcılar düşük bir performans incelemesi, konum indirgeme veya performans değerlendirme planına yer alan kullanıcı olabilir. Çoğu kullanıcı bu olaylara kötü niyetli bir şekilde yanıt vermese de, bu eylemlerin stresi bazı kullanıcıların normalde göz önünde bulundurmayacakları eylemlere neden olabilir. Bu tür riskli etkinliklerin kimliğine yardımcı olmak için, aşağıdaki insider risk yönetimi ilkesi şablonları Microsoft 365 HR bağlayıcısını kullanır ve işe giriş stresi etkinliklerinin yanında meydana gelebilir davranışlarla ilgili risk göstergelerini puanlamaya başlar:

- [Göz korkutucu kullanıcıların veri sızıntıları (önizleme)](insider-risk-management-policies.md#data-leaks-by-disgruntled-users-preview)
- [Korkutucu kullanıcıların güvenlik ilkesi ihlalleri (önizleme)](insider-risk-management-policies.md#security-policy-violations-by-disgruntled-users-preview)

## <a name="ready-to-get-started"></a>Başlamaya hazır mısınız?

- Bkz [. Kurumda insider risk yönetimi](insider-risk-management-plan.md) ilkelerini etkinleştirmeye hazırlanmak için Insider risk yönetimini planlama.
- [Insider risk ilkeleriyle ilgili genel ayarları yapılandırmak için bkz. Insider risk](insider-risk-management-settings.md) yönetimi ayarlarıyla çalışmaya başlama.
- [Önkoşulları yapılandırmak, ilke oluşturmak](insider-risk-management-configure.md) ve uyarı almaya başlamak için bkz. Insider risk yönetimiyle çalışmaya başlama.
