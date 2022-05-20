---
title: İçeriden risk yönetimi hakkında daha fazla bilgi edinme
description: Microsoft Purview'de insider risk yönetimiyle kuruluşunuzda riski en aza indirmeye nasıl yardımcı olunacağınızı öğrenin.
keywords: Microsoft 365, Microsoft Purview, iç risk, risk yönetimi, uyumluluk
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
ms.openlocfilehash: 86a56ec16f81eaa6b61a452829e65251b673cb78
ms.sourcegitcommit: b5529afa84f7dde0a89b1e08aeaf6a3a15cd7679
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/20/2022
ms.locfileid: "65599265"
---
# <a name="learn-about-insider-risk-management"></a>İçeriden risk yönetimi hakkında daha fazla bilgi edinme

> [!TIP]
> *Dokuz Microsoft Purview çözümün de premium sürümlerini ücretsiz olarak deneyebileceğinizi biliyor muydunuz?* Sağlam Purview özelliklerinin kuruluşunuzun uyumluluk gereksinimlerini karşılamasına nasıl yardımcı olabileceğini keşfetmek için 90 günlük Purview çözümleri deneme sürümünü kullanın. Microsoft 365 E3 ve Office 365 E3 müşterileri şimdi [Microsoft Purview uyumluluk portalı deneme hub'ında](https://compliance.microsoft.com/trialHorizontalHub?sku=ComplianceE5&ref=DocsRef) başlayabilir. [Kaydolabilecek kişiler ve deneme koşulları](compliance-easy-trials.md) hakkında ayrıntılı bilgi edinin.

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Microsoft Purview İçeriden Risk Yönetimi, kuruluşunuzdaki kötü amaçlı ve yanlışlıkla etkinlikleri algılamanıza, araştırmanıza ve eyleme geçirmenize olanak tanıyarak iç riskleri en aza indirmenize yardımcı olan bir uyumluluk çözümüdür. Insider risk ilkeleri, kuruluşunuzda tanımlanması ve algılanması gereken risk türlerini tanımlamanıza olanak sağlar; örneğin, servis talepleri üzerinde işlem yapmak ve gerekirse servis taleplerini Microsoft eBulma'ya (Premium) iletmenizi sağlar. Kuruluşunuzdaki risk analistleri, kullanıcıların kuruluşunuzun uyumluluk standartlarıyla uyumlu olduğundan emin olmak için hızlı bir şekilde uygun eylemler gerçekleştirebilir.

Daha fazla bilgi edinmek ve kuruluşunuzdaki riskli etkinlikleri ele almak için planlama sürecine genel bakış için bkz. [Insider risk yönetimi programı başlatma](https://download.microsoft.com/download/b/2/0/b208282a-2482-4986-ba07-15a9b9286df0/pwc-starting-an-insider-risk-management-program-with-pwc-and-microsoft.pdf).

Insider risk yönetiminin kuruluşunuzun kuruluşunuzun değerlerini, kültürünü ve kullanıcı deneyimini öncelik sırasına getirirken riskleri engellemesine, algılamasına ve içermesine nasıl yardımcı olabileceğini öğrenmek için aşağıdaki videoları izleyin:
<br>
<br>

**Insider risk yönetimi çözümü geliştirme &**:
>[!VIDEO https://www.microsoft.com/videoplayer/embed/RE4j9CN]
<br>

**Insider risk yönetimi iş akışı**:
>[!VIDEO https://www.microsoft.com/videoplayer/embed/RE4OUXB]

> [!IMPORTANT]
> Insider risk yönetimi şu anda coğrafi bölgelerde barındırılan kiracılarda ve Azure hizmet bağımlılıkları tarafından desteklenen ülkelerde kullanılabilir. Kuruluşunuzda insider risk yönetiminin desteklendiğini doğrulamak için bkz. [Ülkeye/bölgeye göre Azure bağımlılığı kullanılabilirliği](/troubleshoot/azure/general/dependency-availability-by-country).

## <a name="modern-risk-pain-points"></a>Modern risk ağrı noktaları

Kuruluşunuzda riski yönetmek ve en aza indirmek, modern çalışma alanında bulunan risk türlerini anlamakla başlar. Bazı riskler, doğrudan denetimin dışında kalan dış olaylar ve faktörler tarafından yönlendirilir. Diğer riskler, en aza indirilebilen ve önlenebilen iç olaylara ve kullanıcı etkinliklerine bağlıdır. Bazı örnekler, kuruluşunuzdaki kullanıcıların yasa dışı, uygunsuz, yetkisiz veya etik olmayan davranışlarından ve eylemlerinden kaynaklanan risklerdir. Bu davranışlar, kullanıcıların çok çeşitli iç risklerini içerir:

- Hassas veri sızıntıları ve veri taşması
- Gizlilik ihlalleri
- Fikri mülkiyet (IP) hırsızlığı
- Dolandırıcı -lık
- Insider ticareti
- Mevzuat uyumluluğu ihlalleri

Modern çalışma alanında bulunan kullanıcılar, geniş bir platform ve hizmet yelpazesinde veri oluşturma, yönetme ve paylaşma erişimine sahiptir. Çoğu durumda kuruluşlar, kullanıcı gizlilik standartlarını karşılarken kuruluş genelindeki riskleri belirlemek ve azaltmak için sınırlı kaynaklara ve araçlara sahiptir.

Insider risk yönetimi, risk etkinliğini hızla tanımlamanıza, önceliklendirmenize ve harekete geçirmenize yardımcı olmak için hizmetin ve üçüncü taraf göstergelerin tamamını kullanır. insider risk yönetimi, Microsoft 365 ve Microsoft Graph günlüklerini kullanarak risk göstergelerini tanımlamak için belirli ilkeler tanımlamanızı sağlar. Bu ilkeler riskli etkinlikleri belirlemenize ve bu riskleri azaltmak için harekete geçirmenize olanak sağlar.

Insider risk yönetimi aşağıdaki ilkeler etrafında ortalanır:

- **Saydamlık**: Tasarıma göre gizlilik mimarisiyle kullanıcı gizliliği ile kuruluş risklerini dengeleyin.
- **Yapılandırılabilir**: Sektör, coğrafi ve iş gruplarını temel alan yapılandırılabilir ilkeler.
- **Tümleşik**: Microsoft Purview çözümleri arasında tümleşik iş akışı.
- **Eyleme dönüştürülebilir**: Gözden geçiren bildirimlerini, veri araştırmalarını ve kullanıcı araştırmalarını etkinleştirmek için içgörüler sağlar.

## <a name="identifying-potential-risks-with-analytics"></a>Analizle olası riskleri belirleme

Insider risk analizi, herhangi bir iç risk ilkesi yapılandırmadan kuruluşunuzdaki olası insider risklerini değerlendirmenizi sağlar. Bu değerlendirme, kuruluşunuzun daha yüksek kullanıcı riski olan olası alanları belirlemesine yardımcı olabilir ve yapılandırmayı düşünebileceğiniz iç risk yönetimi ilkelerinin türünü ve kapsamını belirlemeye yardımcı olabilir. Bu değerlendirme, mevcut insider risk ilkelerinin ek lisanslama veya gelecekteki iyileştirme gereksinimlerini belirlemenize de yardımcı olabilir.

Insider risk analizi hakkında daha fazla bilgi edinmek için bkz. [Insider risk yönetimi ayarları: Analiz](insider-risk-management-settings.md#analytics).

## <a name="get-started-with-recommended-actions-preview"></a>Önerilen eylemlerle Kullanmaya başlayın (önizleme)

İster içeriden risk yönetimini ilk kez ayarlarken ister yeni ilkeler oluşturmaya başlarken [, yeni önerilen eylemler](insider-risk-management-configure.md#recommended-actions-preview) deneyimi, iç risk yönetimi özelliklerinden en iyi şekilde yararlanmak için size yardımcı olabilir. Önerilen eylemler arasında izinleri ayarlama, ilke göstergelerini seçme, ilke oluşturma ve daha fazlası yer alır.

## <a name="workflow"></a>Iş akışı

Insider risk yönetimi iş akışı, kuruluşunuzdaki iç riskleri tanımlamanıza, araştırmanıza ve harekete geçmenize yardımcı olur. Odaklanmış ilke şablonları, Microsoft 365 hizmeti genelinde kapsamlı etkinlik sinyalleri ve uyarı ve olay yönetimi araçlarıyla, riskli davranışları hızla tanımlamak ve üzerinde işlem yapmak için eyleme dönüştürülebilir içgörüleri kullanabilirsiniz.

İç risk etkinliklerini ve iç risk yönetimiyle ilgili uyumluluk sorunlarını tanımlamak ve çözmek için aşağıdaki iş akışı kullanılır:

![Insider risk yönetimi iş akışı.](../media/insider-risk-workflow.png)

### <a name="policies"></a>İlkeler

[Insider risk yönetimi ilkeleri](insider-risk-management-policies.md) , kuruluşunuzda hangi tetikleyici olayların ve risk göstergelerinin incelendiğini tanımlayan önceden tanımlanmış şablonlar ve ilke koşulları kullanılarak oluşturulur. Bu koşullar uyarılarda risk göstergelerinin nasıl kullanıldığını, ilkeye hangi kullanıcıların dahil olduğunu, hangi hizmetlerin önceliklendirildiği ve izleme süresini içerir.

Insider risk yönetimine hızlı bir şekilde başlamak için aşağıdaki ilke şablonlarından seçim yapabilirsiniz:

- [Ayrılan kullanıcılar tarafından veri hırsızlığı](insider-risk-management-policies.md#data-theft-by-departing-users)
- [Genel veri sızıntıları](insider-risk-management-policies.md#general-data-leaks)
- [Öncelikli kullanıcılara göre veri sızıntıları (önizleme)](insider-risk-management-policies.md#data-leaks-by-priority-users-preview)
- [Bozuk kullanıcılar tarafından veri sızıntıları (önizleme)](insider-risk-management-policies.md#data-leaks-by-disgruntled-users-preview)
- [Genel güvenlik ilkesi ihlalleri (önizleme)](insider-risk-management-policies.md#general-security-policy-violations-preview)
- [Genel hasta verilerini kötüye kullanma (önizleme)](insider-risk-management-policies.md#general-patient-data-misuse-preview)
- [Ayrılan kullanıcılar tarafından güvenlik ilkesi ihlalleri (önizleme)](insider-risk-management-policies.md#security-policy-violations-by-departing-users-preview)
- [Öncelikli kullanıcılara göre güvenlik ilkesi ihlalleri (önizleme)](insider-risk-management-policies.md#security-policy-violations-by-priority-users-preview)
- [Dağıtılmamış kullanıcıların güvenlik ilkesi ihlalleri (önizleme)](insider-risk-management-policies.md#security-policy-violations-by-disgruntled-users-preview)

![Insider risk yönetimi ilkesi panosu.](../media/insider-risk-policy-dashboard.png)

### <a name="alerts"></a>Uyarılar

Uyarılar, ilke koşullarıyla eşleşen risk göstergeleri tarafından otomatik olarak oluşturulur ve [Uyarılar panosunda](insider-risk-management-activities.md#alert-dashboard) görüntülenir. Bu pano, gözden geçirmesi, zaman içinde uyarıları açması ve kuruluşunuz için uyarı istatistiklerine ihtiyaç duyan tüm uyarıların hızlı bir görünümünü sağlar. Tüm ilke uyarıları, mevcut uyarıların ve eylem gerektiren yeni uyarıların durumunu hızla belirlemenize yardımcı olmak için aşağıdaki bilgilerle birlikte görüntülenir:

- Durum
- Önem
- Algılanan süre
- Durumda
- Servis talebi durumu

![Insider risk yönetimi uyarı panosu.](../media/insider-risk-alerts-dashboard.png)

### <a name="triage"></a>Önceliklendirme

Araştırma gerektiren yeni kullanıcı etkinlikleri, gözden *geçirme durumu gerekiyor* olarak atanmış uyarıları otomatik olarak oluşturur. Gözden geçirenler bu uyarıları hızlı bir şekilde belirleyebilir, gözden geçirebilir, değerlendirebilir ve önceliklendirebilir.

Uyarılar, yeni bir servis talebi açılarak, uyarı mevcut bir servis talebine atanarak veya uyarı kapatılarak çözülür. Uyarı filtrelerini kullanarak uyarıları durum, önem derecesi veya algılanan zamana göre hızla tanımlamak kolaydır. Gözden geçirenler önceliklendirme işleminin bir parçası olarak, ilke tarafından tanımlanan etkinlikler için uyarı ayrıntılarını görüntüleyebilir, ilke eşleşmesiyle ilişkili kullanıcı etkinliğini görüntüleyebilir, uyarının önem derecesini görebilir ve kullanıcı profili bilgilerini gözden geçirebilir.

![Insider risk yönetimi önceliklendirmesi.](../media/insider-risk-triage.png)

### <a name="investigate"></a>Araştır

[Kullanıcı etkinlik raporları (önizleme)](insider-risk-management-activities.md#user-activity-reports-preview) ile seçili bir kullanıcının tüm etkinliklerini hızla araştırın. Bu raporlar, kuruluşunuzdaki araştırmacıların belirli bir süre boyunca belirli kullanıcılara yönelik etkinlikleri geçici veya açık bir şekilde şirket içi risk yönetimi ilkesine atamak zorunda kalmadan incelemelerine olanak sağlar. Bir kullanıcının etkinliklerini inceledikten sonra araştırmacılar zararsız olarak tek tek etkinlikleri kapatabilir, raporun bağlantısını diğer araştırmacılarla paylaşabilir veya e-postayla gönderebilir ya da kullanıcıyı geçici veya açık olarak bir iç risk yönetimi ilkesine atamayı seçebilir.

[Olaylar](insider-risk-management-cases.md) , ilke eşleşmesi ile ilgili etkinlik ayrıntılarının ve koşullarının daha ayrıntılı bir şekilde incelenmesini ve incelenmesini gerektiren uyarılar için oluşturulur. **Servis Talebi panosu** tüm etkin servis taleplerinin, zaman içindeki açık servis taleplerinin ve kuruluşunuzun servis talebi istatistiklerinin tümünün görünümünü sağlar. Gözden geçirenler servis taleplerini duruma, servis talebinin açıldığı tarihe ve servis talebinin son güncelleştirildiği tarihe göre hızla filtreleyebilir.

Servis talebi panosunda bir servis talebi seçildiğinde araştırma ve inceleme için servis talebi açılır. Bu adım, insider risk yönetimi iş akışının kalbidir. Bu alan, risk etkinliklerinin, ilke koşullarının, uyarı ayrıntılarının ve kullanıcı ayrıntılarının gözden geçirenler için tümleşik bir görünümde sentezlendiği yerdir. Bu alandaki birincil araştırma araçları şunlardır:

- **Kullanıcı etkinliği**: Kullanıcı etkinliği, zaman içinde ve geçerli veya geçmiş risk etkinlikleri için risk düzeyine göre etkinlikleri çizen etkileşimli bir grafikte otomatik olarak görüntülenir. Gözden geçirenler, kullanıcı için risk geçmişinin tamamını hızla filtreleyebilir ve görüntüleyebilir ve daha fazla ayrıntı için belirli etkinliklerin detayına gidebilir.
- **İçerik gezgini**: Uyarı etkinlikleriyle ilişkili tüm veri dosyaları ve e-posta iletileri otomatik olarak yakalanır ve İçerik gezgininde görüntülenir. Gözden geçirenler dosyaları ve iletileri veri kaynağına, dosya türüne, etiketlere, konuşmaya ve daha birçok özniteliğe göre filtreleyebilir ve görüntüleyebilir.
- **Servis talebi notları**: Gözden geçirenler Servis Talebi Notları bölümünde bir servis talebi için notlar sağlayabilir. Bu liste, tüm notları merkezi bir görünümde birleştirir ve gözden geçiren ve gönderilen tarih bilgilerini içerir.

![Insider risk yönetimi araştırması.](../media/insider-risk-investigate.png)

Ayrıca, yeni [Denetim günlüğü (önizleme),](insider-risk-management-audit-log.md) iç risk yönetimi özelliklerinde gerçekleştirilen eylemler hakkında bilgi sahibi olmanıza olanak tanır. Bu kaynak, bir veya daha fazla iç risk yönetimi rol grubuna atanan kullanıcılar tarafından gerçekleştirilen eylemlerin bağımsız olarak gözden geçirilmesini sağlar.

### <a name="action"></a>Eylem

Olaylar araştırıldıktan sonra, gözden geçirenler olayı çözmek için hızlı bir şekilde harekete geçebilir veya kuruluşunuzdaki diğer risk paydaşlarıyla işbirliği yapabilir. Kullanıcılar yanlışlıkla veya yanlışlıkla ilke koşullarını ihlal ederse, kuruluşunuz için özelleştirebileceğiniz bildirim şablonlarından kullanıcıya basit bir anımsatıcı bildirimi gönderilebilir. Bu bildirimler basit anımsatıcılar olarak görev yapabilir veya kullanıcıyı gelecekteki riskli davranışları önlemeye yardımcı olmak için daha yenileyici eğitime veya rehberliğe yönlendirebilir. Daha fazla bilgi için bkz [. Insider risk yönetimi bildirim şablonları](insider-risk-management-notices.md).

Daha ciddi durumlarda, insider risk yönetimi olay bilgilerini kuruluşunuzdaki diğer gözden geçirenler veya hizmetlerle paylaşmanız gerekebilir. Insider risk yönetimi, uçtan uca risk çözümünde size yardımcı olmak için diğer Microsoft Purview çözümleriyle sıkı bir şekilde tümleşiktir.

- **eBulma (Premium)**: Araştırma için bir olayı yükseltme, eBulma(Premium) Microsoft Purview servis talebi verilerini ve yönetimini aktarmanıza olanak tanır. eBulma (Premium), kuruluşunuzun iç ve dış araştırmalarına yanıt veren içeriği korumak, toplamak, gözden geçirmek, analiz etmek ve dışarı aktarmak için uçtan uca bir iş akışı sağlar. Yasal ekiplerin yasal tutma bildirimi iş akışının tamamını yönetmesine olanak tanır. eBulma (Premium) durumları hakkında daha fazla bilgi edinmek için bkz. [Microsoft Purview eKeşif'e (Premium) genel bakış](overview-ediscovery-20.md).
- **Office 365 Yönetimi API'leri tümleştirmesi (önizleme)**: Insider risk yönetimi, uyarı bilgilerinin Office 365 Yönetimi API'leri aracılığıyla güvenlik bilgilerine ve olay yönetimi (SIEM) hizmetlerine dışarı aktarmayı destekler. Platformdaki uyarı bilgilerine en uygun erişime sahip olmak, kuruluşunuzun risk süreçlerine en uygun olanı size risk etkinlikleri üzerinde işlem yapma konusunda daha fazla esneklik sağlar. Office 365 Yönetim API'leriyle uyarı bilgilerini dışarı aktarma hakkında daha fazla bilgi edinmek için bkz. [Uyarıları dışarı aktarma](insider-risk-management-settings.md#export-alerts).

> [!NOTE]
> ServiceNow bağlayıcısının önizlemesi sırasında geri bildiriminiz ve desteğiniz için teşekkür ederiz. ServiceNow bağlayıcısının önizlemesini sonlandırmaya ve 30 Kasım 2020'de insider risk yönetimi desteğini sona erdirmeye karar verdik. Müşterilere insider risk yönetiminde ServiceNow tümleştirmesi sağlamak için alternatif yöntemleri etkin bir şekilde değerlendiriyoruz.

## <a name="scenarios"></a>Senaryo

Insider risk yönetimi, çeşitli yaygın senaryolarda kuruluşunuzdaki iç riskleri algılamanıza, araştırmanıza ve önlem almanıza yardımcı olabilir:

### <a name="data-theft-by-departing-users"></a>Ayrılan kullanıcılar tarafından veri hırsızlığı

Kullanıcılar bir kuruluşta kendi istekleriyle veya sonlandırma sonucunda ayrıldığında genellikle şirket, müşteri ve kullanıcı verilerinin risk altında olduğu konusunda meşru endişeler vardır. Kullanıcılar, proje verilerinin mülkiyete ait olmadığını kabul edebilir veya kişisel kazanç sağlamak ve şirket ilkesi ile yasal standartları ihlal etmek amacıyla şirket verilerini almak isteyebilirler. [Kullanıcılar ilke şablonundan ayrılarak Veri hırsızlığını](insider-risk-management-policies.md#policy-templates) kullanan Insider risk yönetimi ilkeleri, genellikle bu tür bir hırsızlıkla ilişkili etkinlikleri otomatik olarak algılar. Bu ilkeyle, uygun araştırma eylemlerini gerçekleştirebilmeniz için kullanıcılardan ayrılarak veri hırsızlığıyla ilişkili şüpheli etkinlikler için otomatik olarak uyarılar alırsınız. Bu ilke şablonu için kuruluşunuz için [bir Microsoft 365 İk bağlayıcısı](import-hr-data.md) yapılandırmanız gerekir.

### <a name="intentional-or-unintentional-leak-of-sensitive-or-confidential-information"></a>Hassas veya gizli bilgilerin kasıtlı veya kasıtsız olarak sızması

Çoğu durumda, kullanıcılar hassas veya gizli bilgileri düzgün bir şekilde işlemek için ellerinden gelenin en iyisini yapmaya çalışır. Ancak bazen kullanıcılar hatalar yapabilir ve bilgiler yanlışlıkla kuruluşunuzun dışında veya bilgi koruma ilkelerinizi ihlal ederek paylaşılır. Diğer durumlarda, kullanıcılar hassas ve gizli bilgileri kasıtlı olarak kötü amaçlı ve potansiyel kişisel kazanç amacıyla sızdırabilir veya paylaşabilir. Aşağıdaki Veri sızıntıları ilke şablonları kullanılarak oluşturulan Insider risk yönetimi ilkeleri, genellikle hassas veya gizli bilgilerin paylaşılmasıyla ilişkili etkinlikleri otomatik olarak algılar:

- [Genel veri sızıntıları](insider-risk-management-policies.md#general-data-leaks)
- [Öncelikli kullanıcılara göre veri sızıntıları (önizleme)](insider-risk-management-policies.md#data-leaks-by-priority-users-preview)
- [Bozuk kullanıcılar tarafından veri sızıntıları (önizleme)](insider-risk-management-policies.md#data-leaks-by-disgruntled-users-preview)

## <a name="intentional-or-unintentional-security-policy-violations-preview"></a>Kasıtlı veya kasıtsız güvenlik ilkesi ihlalleri (önizleme)

Kullanıcılar genellikle cihazlarını modern çalışma alanında yönetirken büyük ölçüde denetime sahiptir. Bu denetim, görevlerinin performansında gereken uygulamaları yükleme veya kaldırma izinlerini veya cihaz güvenlik özelliklerini geçici olarak devre dışı bırakma özelliğini içerebilir. Bu etkinliğin yanlışlıkla, yanlışlıkla veya kötü amaçlı olması fark etmeksizin, bu davranış kuruluşunuz için risk oluşturabilir ve en aza indirmek için tanımlamak ve harekete geçmek önemlidir. Aşağıdaki insider risk management güvenlik ilkesi ihlal şablonları, bu riskli güvenlik etkinliklerini tanımlamaya yardımcı olmak için güvenlik riski göstergelerini puanlar ve güvenlikle ilgili etkinliklere yönelik içgörüler sağlamak için Uç Nokta için Microsoft Defender uyarılarını kullanır:

- [Genel güvenlik ilkesi ihlalleri (önizleme)](insider-risk-management-policies.md#general-security-policy-violations-preview)
- [Ayrılan kullanıcılar tarafından güvenlik ilkesi ihlalleri (önizleme)](insider-risk-management-policies.md#security-policy-violations-by-departing-users-preview)
- [Öncelikli kullanıcılara göre güvenlik ilkesi ihlalleri (önizleme)](insider-risk-management-policies.md#security-policy-violations-by-priority-users-preview)
- [Dağıtılmamış kullanıcıların güvenlik ilkesi ihlalleri (önizleme)](insider-risk-management-policies.md#security-policy-violations-by-disgruntled-users-preview)

## <a name="policies-for-users-based-on-position-access-level-or-risk-history-preview"></a>Kullanıcılar için konum, erişim düzeyi veya risk geçmişine dayalı ilkeler (önizleme)

Kuruluşunuzdaki kullanıcılar konumlarına, hassas bilgilere erişim düzeylerine veya risk geçmişine bağlı olarak farklı risk düzeylerine sahip olabilir. Bu yapı, kuruluşunuzun yönetici liderlik ekibinin üyelerini, kapsamlı veri ve ağ erişim ayrıcalıklarına sahip BT yöneticilerini veya geçmişte riskli etkinlikler geçmişi olan kullanıcıları içerebilir. Bu durumlarda daha yakın inceleme ve daha agresif risk puanlaması, araştırma ve hızlı işlem için uyarıların ortaya konulmalarına yardımcı olmak için önemlidir. Bu tür kullanıcılar için riskli etkinlikleri tanımlamaya yardımcı olmak için, aşağıdaki ilke şablonlarından öncelikli kullanıcı grupları oluşturabilir ve ilkeler oluşturabilirsiniz:

- [Öncelikli kullanıcılara göre güvenlik ilkesi ihlalleri (önizleme)](insider-risk-management-policies.md#security-policy-violations-by-priority-users-preview)
- [Öncelikli kullanıcılara göre veri sızıntıları (önizleme)](insider-risk-management-policies.md#data-leaks-by-priority-users-preview)

## <a name="healthcare-preview"></a>Healthcare (önizleme)

Sağlık sektöründeki kuruluşlar için yapılan son çalışmalar, insider ile ilgili veri ihlallerinin çok yüksek oranda olduğunu tespit etti. Hasta verilerinin ve sağlık kaydı bilgilerinin kötüye kullanımını algılamak, hasta gizliliğini korumanın ve Sağlık Sigortası Taşınabilirlik ve Sorumluluk Yasası (HIPAA) ve Ekonomik ve Klinik Sağlık için Sağlık Bilgi Teknolojisi (HITECH) Yasası gibi uyumluluk düzenlemelerine uymanın kritik bir bileşenidir. Hasta verilerinin kötüye kullanılması, ayrıcalıklı hasta kayıtlarına erişmekten kötü amaçlı olarak aile veya komşulardan gelen hastaların kayıtlarına erişmeye kadar değişebilir. Aşağıdaki insider risk yönetimi ilkesi şablonları, bu tür riskli etkinliklerin kimliğini belirlemeye yardımcı olmak için Microsoft 365 İk bağlayıcısını ve sağlık hizmetlerine özgü bir veri bağlayıcısını kullanarak elektronik ısı kaydı (EHR) sistemlerinizde oluşabilecek davranışlarla ilgili risk göstergelerini puanlamaya başlar:

- [Genel hasta verilerini kötüye kullanma (önizleme)](insider-risk-management-policies.md#general-patient-data-misuse-preview)

## <a name="actions-and-behaviors-by-disgruntled-users-preview"></a>Dağıtılmamış kullanıcıların eylemleri ve davranışları (önizleme)

Çalışma stresi olayları, kullanıcı davranışını insider riskleriyle ilgili çeşitli şekillerde etkileyebilir. Bu stresörler kötü bir performans incelemesi, konum indirgeme veya performans gözden geçirme planına yerleştirilen kullanıcı olabilir. Kullanıcıların çoğu bu olaylara kötü amaçlı olarak yanıt vermese de, bu eylemlerin stresi bazı kullanıcıların normal koşullarda normalde dikkate almayabilecekleri eylemler gerçekleştirmesine neden olabilir. Aşağıdaki insider risk yönetimi ilkesi şablonları, bu tür riskli etkinliklerin kimliğini belirlemeye yardımcı olmak için Microsoft 365 İk bağlayıcısını kullanır ve istihdam stresi olayları yakınında oluşabilecek davranışlarla ilgili risk göstergelerini puanlama işlemine başlar:

- [Bozuk kullanıcılar tarafından veri sızıntıları (önizleme)](insider-risk-management-policies.md#data-leaks-by-disgruntled-users-preview)
- [Dağıtılmamış kullanıcıların güvenlik ilkesi ihlalleri (önizleme)](insider-risk-management-policies.md#security-policy-violations-by-disgruntled-users-preview)

## <a name="ready-to-get-started"></a>Başlamaya hazır mısınız?

- [Kuruluşunuzda insider risk yönetimi](insider-risk-management-plan.md) ilkelerini etkinleştirmeye hazırlanmak için bkz. Insider risk yönetimi planlama.
- Insider risk ilkeleri için genel ayarları yapılandırmak için bkz. [insider risk yönetimi ayarlarıyla Kullanmaya başlayın](insider-risk-management-settings.md).
- Önkoşulları yapılandırmak, ilke oluşturmak ve uyarıları almaya başlamak için [bkz. insider risk yönetimiyle Kullanmaya başlayın](insider-risk-management-configure.md).
