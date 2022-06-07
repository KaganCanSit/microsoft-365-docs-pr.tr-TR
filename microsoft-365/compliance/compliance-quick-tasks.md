---
title: Microsoft Purview'da uyumlulukla çalışmaya başlamaya yönelik hızlı görevler
description: Microsoft Purview'da uyumluluğu hızla kullanmaya başlamanıza yardımcı olacak görevler hakkında bilgi edinin.
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
f1.keywords:
- NOCSH
ms.collection:
- m365-security-compliance
- m365initiative-compliance
ms.custom:
- admindeeplinkDEFENDER
- intro-get-started
ms.localizationpriority: medium
ms.openlocfilehash: cb8471ffea418ac47921777a0ee9594fa73fe4ac
ms.sourcegitcommit: a5e75d7f7651313818bd2de292d5c38b290d8975
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/07/2022
ms.locfileid: "65930229"
---
# <a name="quick-tasks-for-getting-started-with-compliance-in-microsoft-purview"></a>Microsoft Purview'da uyumlulukla çalışmaya başlamaya yönelik hızlı görevler

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Microsoft Purview'u kullanmaya yeni başladıysanız ve nereden başlayacağınızı merak ediyorsanız, bu makale temel bilgiler hakkında rehberlik sağlar ve önemli uyumluluk görevlerinin önceliklerini verir. Bu makale verilerinizi yönetmeye ve izlemeye, bilgileri korumaya ve iç riskleri en aza indirmeye hızlı bir şekilde başlamanıza yardımcı olur.

Riskleri en iyi şekilde yönetmeyi, verilerinizi korumayı ve yeni uzak bir iş gücüyle düzenlemelere ve standartlara uymayı düşünüyorsanız bu makale de yararlıdır. Çalışanlar artık yeni yollarla işbirliği yapıp birbirleriyle bağlantı kuruyor ve bu değişiklik, mevcut uyumluluk süreçlerinizin ve denetimlerinizin uyum sağlaması gerekebileceği anlamına geliyor. Kuruluşunuzda bu yeni uyumluluk risklerini belirlemek ve yönetmek, verilerinizi korumak ve tehditleri ve riskleri en aza indirmek için kritik öneme sahiptir.

Bu temel uyumluluk görevlerini tamamladıktan sonra, ek Microsoft Purview çözümleri uygulayarak kuruluşunuzda uyumluluk kapsamını genişletmeyi göz önünde bulundurun.

## <a name="task-1-configure-compliance-permissions"></a>Görev 1: Uyumluluk izinlerini yapılandırma

İçeriği görüntülemek ve yönetim görevlerini gerçekleştirmek için kuruluşunuzda kimlerin Microsoft Purview uyumluluk portalına erişimi olduğunu yönetmek önemlidir. Microsoft 365, uyumluluk ve Microsoft Purview uyumluluk portalında bulunan araçları kullanmaya özgü yönetim rolleri sağlar.

Kuruluşunuzdaki kişilere bu görevleri gerçekleştirebilmeleri ve yetkisiz kişilerin sorumlulukları dışındaki alanlara erişmesini önlemek için uyumluluk izinleri atayarak başlayın. Microsoft 365'e dahil edilen uyumluluk çözümlerini yapılandırmaya ve uygulamaya başlamadan önce uygun kişileri **Uyumluluk veri yöneticisine** ve **Uyumluluk yöneticisi** yönetici rollerine atadığınızdan emin olmak istersiniz. Ayrıca, Uyumluluk Yöneticisi'nde verileri görüntülemek için kullanıcıları Azure Active Directory genel okuyucu rolüne atamanız gerekir.

İzinleri yapılandırmaya ve kişileri yönetici rollerine atamaya yönelik adım adım yönergeler için bkz [. Güvenlik & Uyumluluk Merkezi'ndeki İzinler](/microsoft-365/security/office-365-security/permissions-in-the-security-and-compliance-center).

## <a name="task-2-know-your-state-of-compliance"></a>Görev 2: Uyumluluk durumunuzu bilin

Nerede olduğunu bilmiyorsan nereye gideceğini bilmek zordur. Uyumluluk gereksinimlerinizi karşılamak, mevcut risk düzeyinizi ve sürekli değişen bu zamanlarda hangi güncelleştirmelerin gerekebileceğini anlamanızı içerir. Kuruluşunuzun uyumluluk gereksinimleri konusunda yeni olması veya sektörünüzü yöneten standartlar ve düzenlemeler konusunda derin deneyime sahip olması fark etmese de uyumluluğu geliştirmek için yapabileceğiniz en iyi şey kuruluşunuzun yerini anlamaktır.

[Microsoft Purview Uyumluluk Yöneticisi](/microsoft-365/compliance/compliance-manager) , kuruluşunuzun uyumluluk duruşlarını anlamanıza ve iyileştirme gerekebilecek alanları vurgulamanıza yardımcı olabilir. Uyumluluk Yöneticisi, risk tabanlı puanı hesaplamak için merkezi bir pano kullanır ve veri koruma ve mevzuat standartlarıyla ilgili riskleri azaltmaya yardımcı olan eylemleri tamamlamadaki ilerlemenizi ölçer. Ayrıca, tüm risk değerlendirmelerinizi izlemek için Bir araç olarak Uyumluluk Yöneticisi'ni de kullanabilirsiniz. Ortak bir araç aracılığıyla risk değerlendirmelerinizi verimli bir şekilde tamamlamanıza yardımcı olacak iş akışı özellikleri sağlar.

Uyumluluk Yöneticisi'ne başlamaya yönelik adım adım yönergeler için bkz. [Uyumluluk Yöneticisi'ne başlama](/microsoft-365/compliance/compliance-manager-setup).

> [!IMPORTANT]
> Güvenlik ve uyumluluk çoğu kuruluş için sıkı bir şekilde tümleşiktir. Kuruluşunuzun hem güvenlik hem de uyumluluk açısından derinlemesine bir savunma yaklaşımı sağlamaya yardımcı olmak için temel güvenlik, tehdit koruması ve kimlik ve erişim yönetimi alanlarını ele almaları önemlidir.
>
> [Microsoft 365](/microsoft-365/security/defender/microsoft-secure-score) <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Defender portalında Microsoft 365</a> Güvenli Puanınızı denetleyin ve aşağıdaki makalelerde açıklanan görevleri tamamlayın:
>
> - [Güvenlik yol haritası - İlk 30 gün, 90 gün ve sonrası için en önemli öncelikler](/microsoft-365/security/office-365-security/security-roadmap)
> - [Güvenlik ekiplerinin evden çalışmayı desteklemesi için en önemli 12 görev](/microsoft-365/security/top-security-tasks-for-remote-work)

## <a name="task-3-enable-auditing-for-your-organization"></a>3. Görev: Kuruluşunuz için denetimi etkinleştirme

Kuruluşunuzun geçerli durumunu ve uyumluluk işlevlerini kimlerin yönetebileceğini belirlediğinize göre, bir sonraki adım uyumluluk araştırmalarını yürütmek ve kuruluşunuzdaki ağ ve kullanıcı etkinlikleri için raporlar oluşturmak üzere verilere sahip olduğunuzdan emin olmaktır. Denetimi etkinleştirmek, bu makalenin ilerleyen bölümlerinde ele alınan uyumluluk çözümleri için de önemli bir önkoşuldur.

Denetim günlüğü tarafından sağlanan içgörüler, uyumluluk gereksinimlerinizi iyileştirme gerektiren uyumluluk alanlarını yönetmenize ve izlemenize yardımcı olabilecek çözümlerle eşleştirmenize yardımcı olan değerli bir araçtır. Etkinlikler kaydedilmeden önce ve denetim günlüğünde arama yapmadan önce denetim günlüğü etkinleştirilmelidir. Etkinleştirildiğinde, kuruluşunuzdaki kullanıcı ve yönetici etkinliği denetim günlüğüne kaydedilir ve kullanıcılara atanan lisansa bağlı olarak 90 gün boyunca ve bir yıla kadar saklanır.

Denetimi açmak için adım adım yönergeler için bkz. [Denetim günlüğü aramasını açma veya kapatma](/microsoft-365/compliance/turn-audit-log-search-on-or-off).

## <a name="task-4-create-policies-to-alert-you-about-potential-compliance-issues"></a>Görev 4: Olası uyumluluk sorunları hakkında sizi uyarmak için ilkeler oluşturma

Microsoft, yönetici izinlerinin kötüye kullanımı, kötü amaçlı yazılım etkinliği, olası dış ve iç tehditler ve veri yaşam döngüsü yönetimi risklerinin belirlenmesine yardımcı olan çeşitli yerleşik uyarı ilkeleri sağlar. Bu ilkeler varsayılan olarak açıktır, ancak kuruluşunuza özgü uyumluluk gereksinimlerini yönetmeye yardımcı olmak için özel uyarılar yapılandırmanız gerekebilir.

Özel uyarı ilkeleri oluşturmak ve kullanıcılar ilke koşullarıyla eşleşen etkinlikler gerçekleştirdiğinde oluşturulan uyarıları görüntülemek için uyarı ilkesi ve uyarı panosu araçlarını kullanın. Bazı örnekler, kuruluşunuzdaki uyumluluk gereksinimlerini, izinlerini ve veri kaybı olaylarını etkileyen kullanıcı ve yönetici etkinliklerini izlemek için uyarı ilkelerini kullanmak olabilir.

Özel uyarı ilkeleri oluşturmaya yönelik adım adım yönergeler için bkz. [Güvenlik ve uyumluluk merkezinde uyarı ilkeleri](/microsoft-365/compliance/alert-policies).

## <a name="task-5-classify-and-protect-sensitive-data"></a>5. Görev: Hassas verileri sınıflandırma ve koruma

Kuruluşunuzdaki kişiler işlerini yapmak için hem kuruluş içindeki hem de dışındaki kişilerle işbirliği yapabilir. Bu, içeriğin artık bir güvenlik duvarının arkasında kalmayabileceği anlamına gelir; cihazlar, uygulamalar ve hizmetler arasında her yerde gezinebilir. Dolaşımdayken, bunu kuruluşunuzun iş ve uyumluluk ilkelerine uygun güvenli ve korumalı bir şekilde gerçekleştirmesini istersiniz.

[Duyarlılık etiketleri](/microsoft-365/compliance/sensitivity-labels) , kuruluşunuzun verilerini sınıflandırmanıza ve korumanıza olanak tanırken, kullanıcı üretkenliğinin ve işbirliği yapma yeteneğinin engellenmediğinden emin olmanıza olanak tanır. Şifreleme ve kullanım kısıtlamalarını zorunlu kılmak için duyarlılık etiketlerini kullanın, görsel işaretler uygulayın ve bilgileri platformlar ve cihazlar arasında, şirket içinde ve bulutta koruyun.

Duyarlılık etiketlerini yapılandırma ve kullanma konusunda adım adım yönergeler için bkz. [Duyarlılık etiketlerini kullanmaya başlama](/microsoft-365/compliance/get-started-with-sensitivity-labels).

## <a name="task-6-configure-retention-policies"></a>Görev 6: Bekletme ilkelerini yapılandırma

[Bekletme ilkesi](/microsoft-365/compliance/retention), içeriği saklamaya, içeriği silmeye veya her ikisine de proaktif olarak karar vermenize olanak tanır; belirtilen saklama süresinin sonunda içeriği saklayıp silmeniz gerekir. Bu eylemler, endüstri düzenlemelerine ve iç politikalara uymak ve dava veya güvenlik ihlali durumunda riskinizi azaltmak için gerekli olabilir.

İçerik bir bekletme ilkesine tabi olduğunda, kişiler içeriği düzenlemeye ve hiçbir şey değişmemiş gibi çalışmaya devam edebilir. İçerik, özgün konumunda yerinde tutulur. Ancak birisi bekletme ilkesine tabi içeriği düzenler veya silerse, özgün içeriğin bir kopyası, söz konusu içeriğin bekletme ilkesi etkinken korunduğu güvenli bir konuma kaydedilir.

Microsoft 365 ortamınızda Teams ve Yammer iletileri, Exchange postası, SharePoint siteleri ve OneDrive hesaplarını içeren birden çok hizmet için bekletme ilkelerini hızla uygulamaya koyabilirsiniz. Bir bekletme ilkesinin otomatik olarak içerebileceği kullanıcı, posta kutusu veya site sayısıyla ilgili bir sınır yoktur. Ancak daha seçici olmanız gerekiyorsa, belirli örnekleri dinamik olarak hedeflemek için sorgu tabanlı uyarlamalı bir kapsam veya her zaman dahil etmek veya her zaman dışlamak için belirli örnekleri belirten statik bir kapsam yapılandırarak bunu yapabilirsiniz.

Bekletme ilkelerini yapılandırmaya yönelik adım adım yönergeler için bkz. [Bekletme ilkeleri oluşturma ve yapılandırma](/microsoft-365/compliance/create-retention-policies). Bekletme ilkeleri Microsoft 365 uygulamaları ve hizmetleri için veri yaşam döngüsü yönetim stratejisinin temel taşını oluşturduğundan bkz. [Veri yaşam döngüsü yönetimini kullanmaya başlama](/microsoft-365/compliance/get-started-with-data-lifecycle-management).

## <a name="task-7-configure-sensitive-information-and-inappropriate-language-policies"></a>7. Görev: Hassas bilgileri ve uygunsuz dil ilkelerini yapılandırma

Hassas bilgilerin korunması, iş yerinde taciz olaylarının algılanması ve bu olaylarda eylemde bulunılması, iç politikalar ve standartlara uyumun önemli bir parçasıdır. Microsoft Purview'da [iletişim uyumluluğu](/microsoft-365/compliance/communication-compliance), e-posta ve Microsoft Teams iletişimleri için hızlı bir şekilde algılamanıza, yakalamanıza ve düzeltme eylemleri gerçekleştirmenize yardımcı olarak bu riskleri en aza indirmeye yardımcı olur. Bunlar küfür, tehdit ve taciz içeren uygunsuz iletişimler ile kuruluşunuzun içinde ve dışında hassas bilgileri paylaşan iletişimleri içerir.

Önceden tanımlanmış *Uygun olmayan metin ilkesi algıla* şablonu, belirlenen gözden geçirenler tarafından incelenebilmeleri için ilke eşleşmeleri için iç ve dış iletişimleri taramanıza olanak tanır. Gözden geçirenler kuruluşunuzdaki taranmış e-postaları, Microsoft Teams'i, Yammer'ı veya üçüncü taraf iletişimlerini araştırabilir ve kuruluşunuzun standartlarıyla uyumlu olduklarından emin olmak için uygun düzeltme eylemlerini gerçekleştirebilir.

Önceden tanımlanmış *Hassas bilgileri algıla* ilke şablonu, önemli verilerin erişimi olmaması gereken kişilerle paylaşılmadığından emin olmak için e-postayı ve tanımlı hassas bilgi türlerini veya anahtar sözcükleri içeren Microsoft Teams iletişimlerini taramak için hızla bir ilke oluşturmanıza yardımcı olur. Bu etkinlikler arasında gizli projeler hakkında yetkisiz iletişim veya şirket içi ticaret veya diğer harmanlama etkinlikleriyle ilgili sektöre özgü kurallar yer alabilir.

İletişim uyumluluğunu planlama ve yapılandırmaya yönelik adım adım yönergeler için bkz. [İletişim uyumluluğunu planlama](/microsoft-365/compliance/communication-compliance-plan) ve [İletişim uyumluluğunu kullanmaya başlama](/microsoft-365/compliance/communication-compliance-configure). İletişim uyumluluğu lisanslama bilgileri için bkz. [Güvenlik & uyumluluğu için Microsoft 365 lisanslama kılavuzu](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#communication-compliance).

## <a name="task-8-see-whats-happening-with-your-sensitive-items"></a>8. Görev: Hassas öğelerinizde neler olduğunu görün

Duyarlılık etiketleri, hassas bilgi türleri, bekletme etiketleri ve ilkeleri ile eğitilebilir sınıflandırıcılar, önceki görevlerde gördüğünüz gibi Exchange, SharePoint ve OneDrive genelinde hassas öğeleri sınıflandırmak ve etiketlemek için kullanılabilir. Hızlı görev yolculuğunuzun son adımı, hangi öğelerin etiketlendiğini ve kullanıcılarınızın bu hassas öğeler üzerinde hangi eylemleri gerçekleştirdiğini görmektir. [içerik gezgini](/microsoft-365/compliance/data-classification-content-explorer) ve [etkinlik gezgini](/microsoft-365/compliance/data-classification-activity-explorer) bu görünürlüğü sağlar.

### <a name="content-explorer"></a>İçerik gezgini

İçerik gezgini, hassas bilgi türü olarak sınıflandırılmış veya eğitilebilir bir sınıflandırıcı tarafından belirli bir sınıflandırmaya ait olan tüm öğeleri ve duyarlılık veya bekletme etiketi uygulanmış tüm öğeleri yerel biçimlerinde görüntülemenizi sağlar.

İçerik gezginini kullanma hakkında adım adım yönergeler için bkz. [Verilerinizi tanıma - veri sınıflandırmasına genel bakış](/microsoft-365/compliance/data-classification-overview) ve [İçerik gezginini kullanmaya başlama](/microsoft-365/compliance/data-classification-content-explorer).

### <a name="activity-explorer"></a>Etkinlik gezgini

Etkinlik gezgini, sınıflandırılmış ve etiketlenmiş hassas öğelerinizle yapılanları izlemenize yardımcı olur:

- SharePoint
- Exchange
- OneDrive

30'un üzerinde farklı filtre kullanılabilir, bazıları şunlardır:

- tarih aralığı
- etkinlik türü
- Konum
- Kullanıcı
- duyarlılık etiketi
- bekletme etiketi
- dosya yolu
- DLP ilkesi

Etkinlik gezginini kullanmaya yönelik adım adım yönergeler için bkz. [Etkinlik gezginini kullanmaya başlama](/microsoft-365/compliance/data-classification-activity-explorer).

## <a name="next-steps"></a>Sonraki adımlar

Kuruluşunuz için uyumluluk yönetimiyle ilgili temel bilgileri yapılandırdığınıza göre, hassas bilgileri korumanıza ve ek insider risklerini algılamanıza ve üzerinde işlem yapmaya yardımcı olmak için Microsoft Purview'da aşağıdaki uyumluluk çözümlerini göz önünde bulundurun.

### <a name="configure-retention-labels"></a>Bekletme etiketlerini yapılandırma

Bekletme ilkeleri kapsayıcı düzeyindeki tüm öğelere (SharePoint siteleri, kullanıcı posta kutuları vb.) otomatik olarak uygulanırken, [bekletme etiketleri](/microsoft-365/compliance/retention#retention-labels) SharePoint belgesi veya e-posta iletisi gibi tek tek öğelere uygulanır. Bu etiketleri el ile veya otomatik olarak uygulayabilirsiniz.

Bekletme etiketleri, ihtiyacınız olanı korumak ve olmayanları silmek için veri idaresi stratejinizin bir parçası olarak kullanılabilir. Belirli belgeler veya e-postalar farklı bekletme veya silme ayarlarına ihtiyaç duyduğunda bekletme ilkelerinizde özel durumlara ihtiyacınız olduğunda bu etiketleri kullanın. Örneğin, SharePoint ilkeniz tüm belgeleri üç yıl boyunca korur, ancak belirli iş belgelerinin beş yıl boyunca saklanması gerekir. Daha fazla bilgi için bkz [. Bekletme ilkelerinizin özel durumları için bekletme etiketleri oluşturma](/microsoft-365/compliance/create-retention-labels-data-lifecycle-management).

Ancak, [kayıt yönetimiyle](/microsoft-365/compliance/records-management) birlikte kullanıldığında bekletme etiketleri, belge ve e-postaları öğe düzeyinde desteklemek için çok daha fazla yönetim seçeneği sağlar. Bu veri yönetimi düzeyi, iş, yasal veya mevzuat kaydı tutma gereksinimleri için yüksek değerli öğeler için çok uygundur. Daha fazla bilgi için bkz. [Kayıt yönetimini kullanmaya başlama](/microsoft-365/compliance/get-started-with-records-management).

### <a name="identify-and-define-sensitive-information-types"></a>Hassas bilgi türlerini tanımlama ve tanımlama

Kuruluşunuzun verilerinde yer alan bilgilere göre hassas bilgi türlerini tanımlayın. Kredi kartı numaralarını, banka hesap numaralarını, pasaport numaralarını ve daha fazlasını tanımlamaya ve korumaya yardımcı olan [yerleşik hassas bilgi türlerini](./sensitive-information-type-entity-definitions.md) kullanın. Veya kuruluşunuza özgü kendi [özel duyarlılık bilgileri türlerinizi](/microsoft-365/compliance/create-a-custom-sensitive-information-type) oluşturabilirsiniz.

Özel hassas bilgi türlerini tanımlamaya yönelik adım adım yönergeler için bkz [. Güvenlik & Uyumluluk Merkezi'nde özel hassas bilgi türü oluşturma](./create-a-custom-sensitive-information-type.md).

### <a name="prevent-data-loss"></a>Veri kaybını önleme

[Microsoft Purview Veri Kaybı Önleme (DLP) ilkeleri](/microsoft-365/compliance/dlp-learn-about-dlp) , Microsoft 365 kuruluşunuz genelinde hassas bilgileri tanımlamanıza, izlemenize ve otomatik olarak korumanıza olanak sağlar. Microsoft hizmetlerindeki hassas öğeleri tanımlamak, hassas öğelerin yanlışlıkla paylaşılmasını önlemek ve kullanıcıların iş akışlarını kesintiye uğratmadan uyumlu kalmayı öğrenmelerine yardımcı olmak için DLP ilkelerini kullanın.

DLP ilkelerini yapılandırmaya yönelik adım adım yönergeler için [DLP ilkesi oluşturma, test etme ve ayarlama](/microsoft-365/compliance/create-test-tune-dlp-policy). Veri kaybı yönetimi lisans bilgileri için bkz. [Güvenlik & uyumluluğu için Microsoft 365 lisanslama kılavuzu](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#office-365-data-loss-prevention-for-exchange-online-sharepoint-online-and-onedrive-for-business).

### <a name="detect-and-act-on-insider-risks"></a>Insider risklerini algılama ve üzerinde işlem yapma

Çalışanlar, çok çeşitli platformlar ve hizmetler genelinde veri oluşturma, yönetme ve paylaşmaya giderek daha fazla erişim elde ediyor. Çoğu durumda kuruluşlar, uyumluluk gereksinimlerini ve çalışan gizlilik standartlarını karşılarken kuruluş genelindeki riskleri belirlemek ve azaltmak için sınırlı kaynaklara ve araçlara sahiptir. Bu riskler, çalışanları terk ederek veri hırsızlığını ve yanlışlıkla fazla paylaşım veya kötü amaçlı olarak kuruluşunuzun dışındaki bilgilerin veri sızıntılarını içerebilir.

[Insider risk yönetimi](/microsoft-365/compliance/insider-risk-management-policies) , riskli kullanıcı etkinliklerini hızla tanımlamanıza, önceliklendirmenize ve harekete geçirmenize yardımcı olmak için hizmetin ve üçüncü taraf göstergelerin tamamını kullanır. Insider risk yönetimi, Microsoft 365 ve Microsoft Graph günlüklerini kullanarak risk göstergelerini tanımlamak ve bu riskleri azaltmak için eyleme geçmek için belirli ilkeler tanımlamanızı sağlar.

Insider risk yönetimi ilkelerini planlama ve yapılandırmaya yönelik adım adım yönergeler için bkz. [Insider risk yönetimini planlama ve Insider risk yönetimini](/microsoft-365/compliance/insider-risk-management-plan) [kullanmaya başlama](/microsoft-365/compliance/insider-risk-management-configure). Insider risk yönetimi lisanslama bilgileri için bkz. [Güvenlik & uyumluluğu için Microsoft 365 lisanslama kılavuzu](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#insider-risk-management).
