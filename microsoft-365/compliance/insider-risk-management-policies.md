---
title: Insider risk yönetimi ilkeleri
description: Microsoft Purview'da insider risk yönetimi ilkeleri hakkında bilgi edinin
keywords: Microsoft 365, Microsoft Purview, insider riski, risk yönetimi, uyumluluk
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
ms.openlocfilehash: 22682a801123d4f8c24cbc11e2d0e35d42228bba
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66627293"
---
# <a name="insider-risk-management-policies"></a>Insider risk yönetimi ilkeleri

Insider risk yönetimi ilkeleri, hangi kullanıcıların kapsam içinde olduğunu ve uyarılar için hangi risk göstergesi türlerinin yapılandırıldığını belirler. Kuruluşunuzdaki tüm kullanıcılar için geçerli olan bir ilkeyi hızla oluşturabilir veya bir ilkede yönetim için tek tek kullanıcılar veya gruplar tanımlayabilirsiniz. İlkeler, ilke koşullarını birden çok veya belirli Microsoft Teams' e, SharePoint sitelerine, veri duyarlılığı türlerine ve veri etiketlerine odaklanmak için içerik önceliklerini destekler. Şablonları kullanarak belirli risk göstergelerini seçebilir ve ilke göstergeleri için olay eşiklerini özelleştirebilir, risk puanlarını ve uyarıların düzeyini ve sıklığını etkili bir şekilde özelleştirebilirsiniz. Buna ek olarak, risk puanı artırıcıları ve anomali algılamaları daha yüksek öneme sahip veya daha olağan dışı kullanıcı etkinliğini belirlemeye yardımcı olur. İlke pencereleri, ilkeyi uyarı etkinliklerine uygulamak için zaman dilimini tanımlamanızı sağlar ve etkinleştirildikten sonra ilkenin süresini belirlemek için kullanılır.

Yerleşik ilke şablonlarıyla oluşturulan ilkelerin olası riskler üzerinde hızlı bir şekilde işlem gerçekleştirmenize nasıl yardımcı olabileceğine ilişkin genel bir bakış için [Insider Risk Yönetimi İlkeleri Yapılandırması videosunu](https://www.youtube.com/watch?v=kudK5ajZTUo) inceleyin.

## <a name="policy-dashboard"></a>İlke panosu

**İlke panosu** kuruluşunuzdaki ilkeleri, ilkenin durumunu hızlı bir şekilde görmenizi, kullanıcıları ilkelere el ile eklemenizi ve her ilkeyle ilişkili uyarıların durumunu görüntülemenizi sağlar.

- **İlke adı**: İlke sihirbazında ilkeye atanan ad.
- **Durum**: Her ilkenin sistem durumu. İlke uyarılarının ve önerilerinin sayısını veya sorunsuz ilkeler için *Sağlıklı* durumunu görüntüler.  Uyarıların veya önerilerin sistem durumu ayrıntılarını görmek için ilkeyi seçebilirsiniz.
- **Etkin uyarılar**: Her ilke için etkin uyarı sayısı.
- **Onaylanan uyarılar**: son 365 gün içinde ilkeden gelen vakalarla sonuçlanan toplam uyarı sayısı.
- **Uyarılarda gerçekleştirilen eylemler**: Son 365 gün için onaylanan veya kapatılan uyarıların toplam sayısı.
- **İlke uyarı etkinliği**: Onaylanan toplam uyarı tarafından belirlenen yüzde, uyarılarda gerçekleştirilen toplam eyleme bölünür (son bir yıl içinde onaylanan veya kapatılan uyarıların toplamıdır).

![Insider risk yönetimi ilkesi panosu.](../media/insider-risk-policy-dashboard.png)

## <a name="policy-recommendations-from-analytics"></a>Analizden ilke önerileri

Insider risk analizi, herhangi bir iç risk ilkesi yapılandırmadan kuruluşunuzdaki olası insider risklerini değerlendirmenizi sağlar. Bu değerlendirme, kuruluşunuzun daha yüksek kullanıcı riski olan olası alanları belirlemesine yardımcı olabilir ve yapılandırmayı düşünebileceğiniz iç risk yönetimi ilkelerinin türünü ve kapsamını belirlemeye yardımcı olabilir.

Insider risk analizi ve ilke önerileri hakkında daha fazla bilgi edinmek için bkz. [Insider risk yönetimi ayarları: Analiz](insider-risk-management-settings.md#analytics).

## <a name="policy-templates"></a>İlke şablonları

Insider risk yönetimi şablonları, ilke tarafından kullanılan risk göstergesi türlerini ve risk puanlama modelini tanımlayan önceden tanımlanmış ilke koşullarıdır. İlke oluşturulmadan önce her ilkenin ilke oluşturma sihirbazında atanmış bir şablonu olmalıdır. Insider risk yönetimi her ilke şablonu için en fazla beş ilkeyi destekler. İlke sihirbazıyla yeni bir insider risk ilkesi oluşturduğunuzda, aşağıdaki ilke şablonlarından birini seçersiniz:

### <a name="data-theft-by-departing-users"></a>Ayrılan kullanıcılar tarafından veri hırsızlığı

Kullanıcılar kuruluşunuzdan ayrıldığında, genellikle ayrılan kullanıcıların veri hırsızlığıyla ilişkili belirli risk göstergeleri vardır. Bu ilke şablonu, risk puanlaması için sızdırma göstergelerini kullanır ve bu risk alanındaki algılama ve uyarılara odaklanır. Ayrılan kullanıcılar için veri hırsızlığı SharePoint Online'dan dosya indirmeyi, dosyaları yazdırmayı ve iş bırakma ve bitiş tarihlerine yakın kişisel bulut mesajlaşma ve depolama hizmetlerine veri kopyalamayı içerebilir. Microsoft 365 HR bağlayıcısını veya kuruluşunuz için Azure Active Directory'de kullanıcı hesabı silmeyi otomatik olarak algılama seçeneğini kullanarak, bu şablon bu etkinliklerle ve bunların kullanıcı çalışma durumuyla nasıl ilişkilendirildikleriyle ilgili risk göstergeleri için puanlama yapmaya başlar.

> [!IMPORTANT]
> Bu şablonu kullanırken, kuruluşunuzdaki kullanıcılar için istifa ve sonlandırma tarihi bilgilerini düzenli aralıklarla içeri aktarmak üzere bir Microsoft 365 İK bağlayıcısı yapılandırabilirsiniz. Kuruluşunuz için Microsoft 365 İK bağlayıcısını yapılandırmaya yönelik adım adım yönergeler için [İk bağlayıcısı ile verileri içeri aktarma](import-hr-data.md) makalesine bakın. İk bağlayıcısını kullanmamayı seçerseniz, ilke sihirbazında tetikleyici olaylarını yapılandırırken Azure AD kullanıcı hesabı silindi seçeneğini belirlemeniz gerekir.

### <a name="general-data-leaks"></a>Genel veri sızıntıları

Verilerin korunması ve veri sızıntılarının önlenmesi, özellikle kullanıcılar, cihazlar ve hizmetler tarafından oluşturulan yeni verilerin hızlı büyümesiyle çoğu kuruluş için sürekli bir zorluktur. Kullanıcılar, veri sızıntılarını yönetmeyi giderek daha karmaşık ve zor hale getiren hizmetler ve cihazlar arasında bilgi oluşturma, depolama ve paylaşma yetkisine sahiptir. Veri sızıntıları, bilgilerin yanlışlıkla kuruluşunuz dışında fazla paylaşımını veya kötü amaçlı olarak veri hırsızlığını içerebilir. Atanmış bir Microsoft Purview Veri Kaybı Önleme (DLP) ilkesi, yerleşik veya özelleştirilebilir tetikleyici olayları ile bu şablon şüpheli SharePoint Online veri indirmeleri, dosya ve klasör paylaşımı, dosyaları yazdırma ve verileri kişisel bulut mesajlaşma ve depolama hizmetlerine kopyalama gibi gerçek zamanlı algılamaları puanlama işlemine başlar.

*Veri sızıntıları* şablonu kullanırken, kuruluşunuzdaki yüksek önem dereceli uyarılar için iç risk ilkesindeki göstergeleri tetikleyen bir DLP ilkesi atayabilirsiniz. Office 365 denetim günlüğüne bir DLP ilke kuralı tarafından yüksek önem derecesi uyarısı oluşturulduğunda, bu şablonla oluşturulan iç risk ilkeleri otomatik olarak yüksek önem derecesi DLP uyarısını inceler. Uyarı, insider risk ilkesinde tanımlanan kapsam içi bir kullanıcı içeriyorsa, uyarı insider risk ilkesi tarafından yeni bir uyarı olarak işlenir ve bir iç risk önem derecesi ve risk puanı atanır. Ayrıca, seçili göstergeleri ilke için olayları tetikleme olarak atamayı da seçebilirsiniz. Bu esneklik ve özelleştirme, ilkenin kapsamını yalnızca göstergelerin kapsadığı etkinliklerle kapsamaya yardımcı olur. Bu ilke, bu uyarıyı olaya dahil edilen diğer etkinliklerle bağlamda değerlendirmenize olanak tanır.

#### <a name="data-leaks-policy-guidelines"></a>Veri sızıntıları ilkesi yönergeleri

İç risk yönetimi ilkeleriyle kullanmak üzere DLP ilkeleri oluştururken veya değiştirirken aşağıdaki yönergeleri göz önünde bulundurun:

- DLP ilkelerinizde kuralları yapılandırırken **Olay raporları** ayarlarını *Yüksek'e* atarken veri sızdırma olaylarının önceliğini belirleyin ve seçmeli olun. Örneğin, hassas belgeleri bilinen bir rakiple e-postayla göndermek *, Yüksek* uyarı düzeyi sızdırma olayı olmalıdır. Diğer DLP ilke kurallarında **Olay raporları** ayarlarında *Yüksek* düzeyin fazla atanarak şirket içi risk yönetimi uyarı iş akışındaki kirlilik artırılabilir ve veri araştırmacılarınızın ve analistlerinizin bu uyarıları düzgün bir şekilde değerlendirmesini zorlaştırabilirsiniz. Örneğin, DLP ilkelerindeki reddetme etkinliklerine erişmek için *Yüksek* uyarı düzeyleri atamak, gerçekten riskli kullanıcı davranışlarını ve etkinliklerini değerlendirmeyi daha zorlaştırır.
- Tetikleyici olay olarak bir DLP ilkesi kullanırken, hem DLP hem de şirket içi risk yönetimi ilkelerindeki kapsam içi kullanıcıları anladığınızdan ve doğru yapılandırdığınızdan emin olun. Yalnızca **Veri sızıntıları** şablonunu kullanan şirket içi risk yönetimi ilkeleri için kapsam içi olarak tanımlanan kullanıcıların yüksek önem derecesine sahip DLP ilkesi uyarıları işlenir. Ayrıca, yalnızca yüksek önem derecesi DLP uyarısı için bir kuralda kapsam içinde olarak tanımlanan kullanıcılar, göz önünde bulundurulacak iç risk yönetimi ilkesi tarafından incelenir. Kapsam içi kullanıcıları hem DLP hem de iç risk ilkelerinizde farkında olmadan çakışan bir şekilde yapılandırmamanız önemlidir.

     Örneğin, DLP ilke kurallarınızın kapsamı yalnızca Satış Ekibindeki kullanıcılara aitse ve **Veri sızıntıları** şablonundan oluşturulan iç risk ilkesi tüm kullanıcıları kapsam içi olarak tanımladıysa, iç risk ilkesi yalnızca Satış Ekibindeki kullanıcılar için yüksek önem dereceli DLP uyarılarını işler. Insider risk ilkesi, kullanıcıların bu örnekteki DLP kurallarında tanımlanmayan işlemleri için yüksek öncelikli DLP uyarısı almaz. Buna karşılık, **Veri sızıntıları** şablonlarından oluşturulan insider risk yönetimi ilkenizin kapsamı yalnızca Satış Ekibindeki kullanıcılara göre belirlenmişse ve atanan DLP ilkesinin kapsamı tüm kullanıcılar için belirlenmişse, iç risk ilkesi yalnızca Satış Ekibi üyeleri için yüksek önem derecesinde DLP uyarılarını işler. Insider risk yönetimi ilkesi, Satış Ekibi'ne dahil olmayan tüm kullanıcılar için yüksek önem dereceli DLP uyarılarını yoksayar.

- Bu iç risk yönetimi şablonu için kullanılan DLP ilkesindeki **Olay raporları** kuralı ayarının *Yüksek* önem düzeyi uyarıları için yapılandırıldığından emin olun. *Yüksek* önem düzeyi tetikleyici olaylardır ve **Olay raporları** alanı *Düşük* veya *Orta* olarak ayarlanmış DLP ilkelerindeki kurallardan iç risk yönetimi uyarıları oluşturulmaz.

    ![DLP ilkesi uyarı ayarı.](../media/insider-risk-DLP-policy-high-severity.png)

     > [!NOTE]
     > Yerleşik şablonları kullanarak yeni bir DLP ilkesi oluştururken, **Olay raporları** ayarını *Yüksek* önem düzeyi için yapılandırmak için **Gelişmiş DLP kuralları oluştur veya özelleştir** seçeneğini belirlemeniz gerekir.

**Veri sızıntıları** şablonundan oluşturulan her insider risk yönetimi ilkesi, bu tetikleyici olay seçeneği kullanılırken yalnızca bir DLP ilkesi atanabilir. Algılamak istediğiniz farklı etkinlikleri birleştiren ve **Veri sızıntıları** şablonunu kullanan insider risk ilkeleri için olayları tetikleyen bir eylemde bulunan ayrılmış bir DLP ilkesi oluşturmayı göz önünde bulundurun.

Kuruluşunuz için DLP ilkelerini yapılandırmaya yönelik adım adım yönergeler için [DLP ilkesi oluşturma, test etme ve ayarlama](create-test-tune-dlp-policy.md) makalesine bakın.

### <a name="data-leaks-by-priority-users-preview"></a>Öncelikli kullanıcılara göre veri sızıntıları (önizleme)

Kuruluşunuzdaki kullanıcıların verilerini korumak ve veri sızıntılarını önlemek konumlarına, hassas bilgilere erişim düzeylerine veya risk geçmişine bağlı olabilir. Veri sızıntıları, yüksek oranda hassas bilgilerin kuruluşunuz dışında yanlışlıkla fazla paylaşımını veya kötü amaçlı olarak veri hırsızlığını içerebilir. Tetikleme olayı seçeneği olarak atanmış bir veri kaybı önleme (DLP) ilkesiyle, bu şablon şüpheli etkinliğin gerçek zamanlı algılamalarını puanlamaya başlar ve daha yüksek önem derecelerine sahip iç risk uyarıları ve uyarıları olasılığının artmasına neden olur. Öncelikli kullanıcılar, insider risk yönetimi ayarları alanında yapılandırılmış [öncelikli kullanıcı gruplarında](insider-risk-management-settings.md#priority-user-groups-preview) tanımlanır.

**Genel veri sızıntıları şablonunda** olduğu gibi, kuruluşunuzdaki yüksek önem dereceli uyarılar için iç risk ilkesindeki göstergeleri tetikleyen bir DLP ilkesi seçebilirsiniz. Bu şablonu kullanırken DLP seçeneğiyle bir ilke oluştururken DLP ilkeleri için Veri sızıntıları ilkesi yönergelerini izleyin. Ayrıca, seçili göstergeleri ilke için olayları tetikleme olarak atamayı da seçebilirsiniz. Bu esneklik ve özelleştirme, ilkenin kapsamını yalnızca göstergelerin kapsadığı etkinliklerle kapsamaya yardımcı olur. Ayrıca, **Insider risk yönetimi** > **Ayarları** >  Öncelik kullanıcı grupları'nda oluşturulan öncelikli **kullanıcı gruplarını** ilkeye atamanız gerekir.

### <a name="data-leaks-by-disgruntled-users-preview"></a>Bozuk kullanıcılar tarafından veri sızıntıları (önizleme)

Kullanıcılar iş stresi yaşadığında, bu kişiler bozulabilir ve bu da içeriden risk etkinliği olasılığını artırabilir. Bu şablon, parçalanmayla ilişkili bir gösterge tanımlandığında kullanıcı etkinliğini puanlama işlemine başlar. Performans geliştirme bildirimleri, düşük performans gözden geçirmeleri veya iş düzeyi durumu değişiklikleri buna örnek olarak verilebilir. Dağıtılan kullanıcılar için veri sızıntıları, SharePoint Online'dan dosya indirmeyi ve çalışma stresi veya olaylarının yakınında kişisel bulut mesajlaşma ve depolama hizmetlerine veri kopyalamayı içerebilir.

Bu şablonu kullanırken, kuruluşunuzdaki kullanıcılar için performans geliştirme bildirimlerini, düşük performans gözden geçirme durumunu veya iş düzeyi değişiklik bilgilerini düzenli aralıklarla içeri aktarmak için bir Microsoft 365 İK bağlayıcısı da yapılandırmanız gerekir. Kuruluşunuz için Microsoft 365 İK bağlayıcısını yapılandırmaya yönelik adım adım yönergeler için [İk bağlayıcısı ile verileri içeri aktarma](import-hr-data.md) makalesine bakın.

### <a name="general-security-policy-violations-preview"></a>Genel güvenlik ilkesi ihlalleri (önizleme)

Birçok kuruluşta, kullanıcıların cihazlarına yazılım yükleme veya görevlerinde yardımcı olması için cihaz ayarlarını değiştirme izni vardır. Yanlışlıkla veya kötü amaçlı olarak, kullanıcılar kötü amaçlı yazılım yükleyebilir veya cihazlarında veya ağ kaynaklarınızdaki bilgilerin korunmasına yardımcı olan önemli güvenlik özelliklerini devre dışı bırakabilir. Bu ilke şablonu, Uç Nokta için Microsoft Defender güvenlik uyarılarını kullanarak bu etkinlikleri puanlamaya ve bu risk alanına odaklanma algılama ve uyarılar eklemeye başlar. Kullanıcıların şirket içi riskin göstergesi olabilecek bir güvenlik ilkesi ihlalleri geçmişine sahip olabileceği senaryolarda güvenlik ilkesi ihlallerine yönelik içgörüler sağlamak için bu şablonu kullanın.

Güvenlik ihlali uyarılarını içeri aktarmak için kuruluşunuzda Uç Nokta için Microsoft Defender yapılandırmanız ve Defender Güvenlik Merkezi'nde insider risk yönetimi tümleştirmesi için Uç Nokta için Defender'ı etkinleştirmeniz gerekir. Şirket içi risk yönetimi tümleştirmesi için Uç Nokta için Defender'ı yapılandırma hakkında daha fazla bilgi için bkz. [Uç Nokta için Defender'da gelişmiş özellikleri yapılandırma](/windows/security/threat-protection/microsoft-defender-atp/advanced-features#share-endpoint-alerts-with-microsoft-compliance-center).

### <a name="general-patient-data-misuse-preview"></a>Genel hasta verilerini kötüye kullanma (önizleme)

Sağlık kayıt verilerinin korunması ve hasta kişisel verilerinin kötüye kullanılmasının önlenmesi sağlık sektöründeki kuruluşlar için önemli bir endişe kaynağıdır. Bu kötüye kullanım, yetkisiz kişilere gizli veri sızıntıları, hasta kayıtlarının sahte olarak değiştirilmesi veya hasta sağlık kayıtlarının çalınması olabilir. Hasta verilerinin farkındalığı, ihmali veya kullanıcılar tarafından sahtekarlık olmaması nedeniyle kötüye kullanılmasını önlemek, Sağlık Sigortası Taşınabilirlik ve Sorumluluk Yasası (HIPAA) ve Ekonomik ve Klinik Sağlık için Sağlık Bilgi Teknolojisi (HITECH) Yasası'nın mevzuat gereksinimlerini karşılamada da önemli bir bileşendir. Bu eylemlerin her ikisi de hasta korumalı sağlık bilgilerini (PHI) korumaya yönelik gereksinimleri oluşturur.

Bu ilke şablonu, mevcut elektronik tıbbi kayıt (EMR) sistemlerinde barındırılan kayıtlarla ilişkili şüpheli etkinlikleri algılayan iç kullanıcılar için risk puanlaması sağlar. Algılama, hasta verilerini yetkisiz erişime, görüntülemeye, değiştirmeye ve dışarı aktarmaya odaklanır. EMR sisteminizdeki erişim, sızdırma veya engelleme etkinliklerinin algılanması için [bir bağlayıcıyı Microsoft Healthcare bağlayıcısı](import-healthcare-data.md) veya [Epic bağlayıcısı](import-epic-data.md) yapılandırmanız gerekir.

Bu şablonu kullanırken, kuruluşunuzdaki kullanıcılar için kuruluş profili verilerini düzenli aralıklarla içeri aktarmak için bir Microsoft 365 İK bağlayıcısı da yapılandırmanız gerekir. Kuruluşunuz için Microsoft 365 İK bağlayıcısını yapılandırmaya yönelik adım adım yönergeler için [İk verilerini içeri aktarmak için bağlayıcı ayarlama](/microsoft-365/compliance/import-hr-data) makalesine bakın.

### <a name="security-policy-violations-by-departing-users-preview"></a>Ayrılan kullanıcılar tarafından güvenlik ilkesi ihlalleri (önizleme)

Pozitif veya negatif koşullarda ayrılan kullanıcılar, güvenlik ilkesi ihlalleri açısından daha yüksek riskler olabilir. Bu ilke şablonu, ayrılan kullanıcıların yanlışlıkla veya kötü amaçlı güvenlik ihlallerine karşı korunmaya yardımcı olmak amacıyla güvenlikle ilgili etkinliklerle ilgili içgörüler sağlamak üzere Uç Nokta için Defender uyarılarını kullanır. Bu etkinlikler, kötü amaçlı yazılımları veya zararlı olabilecek diğer uygulamaları yükleyip cihazlarında güvenlik özelliklerini devre dışı bırakmayı içerir. [Microsoft 365 HR bağlayıcısını](import-hr-data.md) veya kuruluşunuz için Azure Active Directory'de kullanıcı hesabı silme işlemini otomatik olarak algılama seçeneğini kullanarak, bu şablon bu güvenlik etkinlikleriyle ve bunların kullanıcı çalışma durumuyla nasıl ilişkilendirildikleriyle ilgili risk göstergeleri için puanlama yapmaya başlar.

Güvenlik ihlali uyarılarını içeri aktarmak için kuruluşunuzda Uç Nokta için Microsoft Defender yapılandırmanız ve Defender Güvenlik Merkezi'nde insider risk yönetimi tümleştirmesi için Uç Nokta için Defender'ı etkinleştirmeniz gerekir. Şirket içi risk yönetimi tümleştirmesi için Uç Nokta için Defender'ı yapılandırma hakkında daha fazla bilgi için bkz. [Uç Nokta için Defender'da gelişmiş özellikleri yapılandırma](/windows/security/threat-protection/microsoft-defender-atp/advanced-features#share-endpoint-alerts-with-microsoft-compliance-center).

### <a name="security-policy-violations-by-priority-users-preview"></a>Öncelikli kullanıcılara göre güvenlik ilkesi ihlalleri (önizleme)

Kuruluşunuzdaki kullanıcıların güvenlik ihlallerine karşı koruma, konumlarına, hassas bilgilere erişim düzeylerine veya risk geçmişine bağlı olabilir. Öncelikli kullanıcıların güvenlik ihlalleri kuruluşunuzun kritik alanlarını önemli ölçüde etkileyebileceğinden, bu ilke şablonu bu göstergeler üzerinde puanlama yapmaya başlar ve bu kullanıcılar için güvenlikle ilgili etkinliklerle ilgili içgörüler sağlamak için Uç Nokta için Microsoft Defender uyarıları kullanır. Bu etkinlikler, kötü amaçlı yazılım veya zararlı olabilecek diğer uygulamaları yükleyen öncelikli kullanıcıları ve cihazlarında güvenlik özelliklerini devre dışı bırakmayı içerebilir. Öncelikli kullanıcılar, insider risk yönetimi ayarları alanında yapılandırılmış öncelikli kullanıcı gruplarında tanımlanır.

Güvenlik ihlali uyarılarını içeri aktarmak için kuruluşunuzda Uç Nokta için Microsoft Defender yapılandırmanız ve Defender Güvenlik Merkezi'nde insider risk yönetimi tümleştirmesi için Uç Nokta için Defender'ı etkinleştirmeniz gerekir. Şirket içi risk yönetimi tümleştirmesi için Uç Nokta için Defender'ı yapılandırma hakkında daha fazla bilgi için bkz. [Uç Nokta için Defender'da gelişmiş özellikleri yapılandırma](/windows/security/threat-protection/microsoft-defender-atp/advanced-features#share-endpoint-alerts-with-microsoft-compliance-center). Ayrıca, **Insider risk yönetimi** > **Ayarları** >  Öncelik kullanıcı grupları'nda oluşturulan öncelikli **kullanıcı gruplarını** ilkeye atamanız gerekir.

### <a name="security-policy-violations-by-disgruntled-users-preview"></a>Dağıtılmamış kullanıcıların güvenlik ilkesi ihlalleri (önizleme)

İş stresi olan kullanıcılar, yanlışlıkla veya kötü amaçlı güvenlik ilkesi ihlalleri için daha yüksek risk altında olabilir. Bu stresörler, kullanıcının bir performans geliştirme planına yerleştirilmesini, düşük performans gözden geçirme durumunu veya mevcut konumundan indirgenmeyi içerebilir. Bu ilke şablonu, bu kullanıcılar için bu olaylarla ilişkili bu göstergelere ve etkinliklere göre risk puanlaması başlatır.

Bu şablonu kullanırken, kuruluşunuzdaki kullanıcılar için performans geliştirme bildirimlerini, düşük performans gözden geçirme durumunu veya iş düzeyi değişiklik bilgilerini düzenli aralıklarla içeri aktarmak için bir Microsoft 365 İK bağlayıcısı da yapılandırmanız gerekir. Kuruluşunuz için Microsoft 365 İK bağlayıcısını yapılandırmaya yönelik adım adım yönergeler için [İk bağlayıcısı ile verileri içeri aktarma](import-hr-data.md) makalesine bakın.

Ayrıca kuruluşunuzda Uç Nokta için Microsoft Defender yapılandırmanız ve güvenlik ihlali uyarılarını içeri aktarmak için Defender Güvenlik Merkezi'nde insider risk yönetimi tümleştirmesi için Uç Nokta için Defender'ı etkinleştirmeniz gerekir. Şirket içi risk yönetimi tümleştirmesi için Uç Nokta için Defender'ı yapılandırma hakkında daha fazla bilgi için bkz. [Uç Nokta için Defender'da gelişmiş özellikleri yapılandırma](/windows/security/threat-protection/microsoft-defender-atp/advanced-features#share-endpoint-alerts-with-microsoft-compliance-center).

### <a name="policy-template-prerequisites-and-triggering-events"></a>İlke şablonu önkoşulları ve olayları tetikleme

Insider risk yönetimi ilkesi için seçtiğiniz şablona bağlı olarak, tetikleyen olaylar ve ilke önkoşulları farklılık gösterir. Olayların tetiklenmesi, bir kullanıcının bir iç risk yönetimi ilkesi için etkin olup olmadığını belirleyen önkoşullardır. Bir kullanıcı bir insider risk yönetimi ilkesine eklenirse ancak tetikleyici bir olayı yoksa, kullanıcı etkinliği Kullanıcılar panosuna el ile eklenmediği sürece ilke tarafından değerlendirilmez. İlke önkoşulları, ilkenin riski değerlendirmek için gerekli sinyalleri veya etkinlikleri alması için gerekli öğelerdir.

Aşağıdaki tabloda, her insider risk yönetimi ilkesi şablonundan oluşturulan ilkeler için tetikleyici olaylar ve önkoşullar listelenmektedir:

| **İlke şablonu** | **İlkeler için olayları tetikleme** | **Önkoşullar** |
| :------------------ | :--------------------------------- | :---------------- |
| **Ayrılan kullanıcılar tarafından veri hırsızlığı** | İk bağlayıcısından veya Azure Active Directory hesabı silme işleminden istifa veya sonlandırma tarihi göstergesi | (isteğe bağlı) Sonlandırma ve istifa tarihi göstergeleri için yapılandırılmış Microsoft 365 İk bağlayıcısı |
| **Genel veri sızıntıları** | *Yüksek önem derecesi* uyarısı veya yerleşik sızdırma olayı tetikleyicileri oluşturan veri sızıntısı ilkesi etkinliği | *Yüksek önem derecesi* uyarıları için yapılandırılmış DLP ilkesi <br><br> VEYA <br><br> Özelleştirilmiş tetikleyici göstergeleri |
| **Öncelikli kullanıcılara göre veri sızıntıları** | *Yüksek önem derecesi* uyarısı veya yerleşik sızdırma olayı tetikleyicileri oluşturan veri sızıntısı ilkesi etkinliği | *Yüksek önem derecesi* uyarıları için yapılandırılmış DLP ilkesi <br><br> VEYA <br><br> Özelleştirilmiş tetikleyici göstergeleri <br><br> Insider risk ayarlarında yapılandırılmış öncelikli kullanıcı grupları |
| **Bozuk kullanıcılar tarafından veri sızıntıları** | İk bağlayıcısından performans geliştirme, düşük performans veya iş düzeyi değişiklik göstergeleri | Microsoft 365 HR bağlayıcısı, dağıtım göstergeleri için yapılandırıldı |
| **Genel güvenlik ilkesi ihlalleri** | güvenlik denetimlerinin veya Uç Nokta için Microsoft Defender tarafından algılanan istenmeyen yazılımların savunulması | Etkin Uç Nokta için Microsoft Defender aboneliği <br><br> yapılandırılmış Microsoft Purview uyumluluk portalı ile Uç Nokta için Microsoft Defender tümleştirmesi |
| **Genel hasta verilerini kötüye kullanma** | EMR sistemlerinden güvenlik denetimlerinin savunulması <br><br> İk sistemlerinden kullanıcı ve hasta adresi eşleştirme göstergeleri | İlke veya şirket içi risk ayarlarında seçilen sağlık hizmeti erişim göstergeleri <br><br> Adres eşleştirme için yapılandırılmış Microsoft 365 İK bağlayıcısı <br><br> Microsoft Healthcare veya Epic bağlayıcısı yapılandırıldı |
| **Ayrılan kullanıcıların güvenlik ilkesi ihlalleri** | İk bağlayıcısından veya Azure Active Directory hesabı silme işleminden istifa veya sonlandırma tarihi göstergeleri | (isteğe bağlı) Sonlandırma ve istifa tarihi göstergeleri için yapılandırılmış Microsoft 365 İk bağlayıcısı <br><br> Etkin Uç Nokta için Microsoft Defender aboneliği <br><br> yapılandırılmış Microsoft Purview uyumluluk portalı ile Uç Nokta için Microsoft Defender tümleştirmesi |
| **Öncelikli kullanıcılara göre güvenlik ilkesi ihlalleri** | güvenlik denetimlerinin veya Uç Nokta için Microsoft Defender tarafından algılanan istenmeyen yazılımların savunulması | Etkin Uç Nokta için Microsoft Defender aboneliği <br><br> yapılandırılmış Microsoft Purview uyumluluk portalı ile Uç Nokta için Microsoft Defender tümleştirmesi <br><br> Insider risk ayarlarında yapılandırılmış öncelikli kullanıcı grupları |
| **Dağıtılan kullanıcının güvenlik ilkesi ihlalleri** | İk bağlayıcısından performans geliştirme, düşük performans veya iş düzeyi değişiklik göstergeleri | Microsoft 365 HR bağlayıcısı, dağıtım göstergeleri için yapılandırıldı <br><br> Etkin Uç Nokta için Microsoft Defender aboneliği <br><br> yapılandırılmış Microsoft Purview uyumluluk portalı ile Uç Nokta için Microsoft Defender tümleştirmesi |

## <a name="prioritize-content-in-policies"></a>İlkelerdeki içeriğin önceliğini belirleme

Insider risk yönetimi ilkeleri, nerede depolandığına, içerik türüne veya nasıl sınıflandırıldığına bağlı olarak içerik için daha yüksek bir öncelik belirtmeyi destekler. İçeriği öncelik olarak belirtmek, ilişkili etkinlikler için risk puanını artırır ve bu da yüksek önem derecesi uyarısı oluşturma olasılığını artırır. Ancak, ilgili içerik yerleşik veya özel hassas bilgi türleri içermediği veya ilkede öncelik olarak belirtilmediği sürece bazı etkinlikler uyarı oluşturmaz.

Örneğin, kuruluşunuzun son derece gizli bir proje için ayrılmış bir SharePoint sitesi vardır. Bu SharePoint sitesindeki bilgiler için veri sızıntıları projenin güvenliğini tehlikeye atabilir ve başarısını önemli ölçüde etkileyebilir. Veri sızıntıları ilkesinde bu SharePoint sitesine öncelik vererek, uygun etkinliklerin risk puanları otomatik olarak artırılır. Bu öncelik belirleme, bu etkinliklerin bir iç risk uyarısı oluşturma olasılığını artırır ve uyarı için önem derecesini yükseltir.

İlke sihirbazında bir insider risk yönetimi ilkesi oluşturduğunuzda, aşağıdaki önceliklerden birini seçebilirsiniz:

- **SharePoint siteleri**: Tanımlı SharePoint sitelerindeki tüm dosya türleriyle ilişkili tüm etkinliklere daha yüksek bir risk puanı atanır. İlkeyi yapılandıran ve öncelikli Share Point sitelerini seçen kullanıcılar, erişim iznine sahip oldukları SharePoint sitelerini seçebilir. SharePoint siteleri geçerli kullanıcı tarafından ilkede seçilemiyorsa, gerekli izinlere sahip başka bir kullanıcı ilkenin sitelerini daha sonra seçebilir veya geçerli kullanıcıya gerekli sitelere erişim verilmesi gerekir.
- **Hassas bilgi türleri**: [Hassas bilgi türleri](sensitive-information-type-entity-definitions.md) içeren içerikle ilişkili tüm etkinliklere daha yüksek bir risk puanı atanır.
- **Duyarlılık etiketleri**: Belirli [duyarlılık etiketleri](sensitivity-labels.md) uygulanmış içerikle ilişkili tüm etkinliklere daha yüksek bir risk puanı atanır.
- **Dosya uzantıları**: Belirli dosya uzantılarına sahip içerikle ilişkili tüm etkinlikler. İlke sihirbazında **öncelik belirlemek üzere Dosya uzantıları'nı** seçen bir veri hırsızlığı/sızıntı ilkesi yapılandıran kullanıcılar, ilkede öncelik belirlemek için en fazla 50 dosya uzantısı tanımlayabilir. Girilen uzantılar, önceliklendirilmiş uzantının ilk karakteri olarak bir '.' içerebilir veya atlayabilir.

## <a name="sequence-detection"></a>Sıra algılama

Riskli etkinlikler yalıtılmış olaylar olarak gerçekleşmeyebilir. Bu riskler genellikle daha büyük bir olay dizisinin parçasıdır. Sıra, art  iki veya daha fazla kullanıcı etkinliğinden oluşan ve yükseltilmiş risk önerebilecek bir grupdur. Bu ilgili etkinliklerin belirlenmesi, genel riski değerlendirmenin önemli bir parçasıdır. Veri hırsızlığı veya veri sızıntısı ilkeleri için sıra algılama etkinleştirildiğinde, sıra bilgisi etkinliklerinden elde edilen içgörüler, insider risk yönetimi olayı içindeki **Kullanıcı etkinliği** sekmesinde görüntülenir. Aşağıdaki ilke şablonları sıra algılamayı destekler:

- Ayrılan kullanıcılar tarafından veri hırsızlığı
- Genel veri sızıntıları
- Öncelikli kullanıcılara göre veri sızıntıları
- Bozuk kullanıcılar tarafından veri sızıntıları

Bu insider risk yönetimi ilkeleri belirli göstergeleri ve oluşan sırayı kullanarak risk dizisindeki her adımı algılayabilir. Bir dizide etkinlikleri eşlerken dosya adları kullanılır. Bu riskler dört ana etkinlik kategorisine ayrılır:

- **Koleksiyon**: Bu kategori sinyalleri kapsam içi ilke kullanıcıları tarafından yapılan indirme etkinliklerine odaklanır. Bu kategorideki bazı örnek etkinlikler, SharePoint sitelerinden dosya indirmek veya dosyaları sıkıştırılmış bir klasöre taşımak olabilir.
- **Sızdırma**: Bu kategori sinyalleri, kapsam içi ilke kullanıcıları tarafından iç ve dış kaynaklarda paylaşım veya ayıklama etkinliklerine odaklanır. Bu kategorideki örnek bir etkinlik, kuruluşunuzdan dış alıcılara ekleri olan e-postalar göndermek olabilir.
- **Karartma**: Bu kategori sinyalleri, kapsam içi ilke kullanıcıları tarafından riskli etkinliklerin maskelenmesine odaklanır. Bu kategorideki bazı örnek etkinlikler, bir cihazdaki dosyaları yeniden adlandırmak veya SharePoint dosyalarındaki duyarlılık etiketlerini kaldırmak veya düşürmek olabilir.
- **Temizleme**: Bu kategori sinyalleri kapsam içi ilke kullanıcılarına göre silme etkinliklerine odaklanır. Bu kategorideki örnek bir etkinlik, bir cihazdan dosya silmek olabilir.

> [!NOTE]
> Sıra algılama, iç risk yönetimi için genel ayarlarda etkinleştirilen göstergeleri ve ilkede seçilen göstergeleri kullanır. Uygun göstergeler seçilmezse, sıra algılama çalışmaz.

İlkede yapılandırıldığında her bir sıra algılama türü için tek tek eşik ayarlarını özelleştirebilirsiniz. Bu eşik ayarları, sırayla ilişkili dosyaların hacmine göre uyarıları ayarlar.

**Kullanıcı etkinliği** görünümünde sıra algılama yönetimi hakkında daha fazla bilgi edinmek için bkz. [Insider risk yönetimi durumları: Kullanıcı etkinliği](insider-risk-management-cases.md#user-activity).

## <a name="cumulative-exfiltration-detection-preview"></a>Kümülatif sızdırma algılama (önizleme)

Insider risk göstergeleri, şirket içi risk ilkeleri kapsamındaki kullanıcılar için günlük olarak değerlendirilen olağan dışı risk etkinlik düzeylerini belirlemeye yardımcı olur. Kümülatif sızdırma algılama, bir kullanıcının belirli bir süre boyunca gerçekleştirdiği sızdırma etkinliklerinin, kuruluşunuzdaki kullanıcılar tarafından son 30 gün içinde birden çok sızdırma etkinliği türünde gerçekleştirilen normal miktarı aştığını belirlemenize yardımcı olmak için makine öğrenmesi modellerini kullanır. Örneğin, bir kullanıcı son ay içinde kullanıcıların çoğundan daha fazla dosya paylaştıysa, bu etkinlik algılanabilir ve kümülatif sızdırma etkinliği olarak sınıflandırılır.

Insider risk yönetimi analistleri ve araştırmacıları, genellikle uyarı oluşturmayacak ancak kuruluşlarında tipik olanın üzerinde olan filtrasyon etkinliklerini tanımlamaya yardımcı olmak için kümülatif sızdırma algılama içgörüleri kullanabilir. Bazı örnekler, kullanıcıların verileri birkaç gün içinde yavaş bir şekilde dışarı aktarması veya kuruluşunuzda veri paylaşımı için kullanıcıların birden çok kanalda verileri her zamankinden daha fazla paylaşması olabilir.  SharePoint siteleri için toplu sızdırma etkinliklerine, hassas bilgi türlerine ve bir ilkede öncelik içeriği olarak yapılandırılmış [duyarlılık etiketlerine](/microsoft-365/compliance/sensitivity-labels#label-priority-order-matters) sahip içeriğe veya Microsoft Purview Bilgi Koruması yüksek öncelikli olarak yapılandırılmış etiketleri içeren etkinliklere daha yüksek risk puanları atanır.

Aşağıdaki ilke şablonları kullanılırken kümülatif sızdırma algılaması varsayılan olarak etkindir:

- Ayrılan kullanıcılar tarafından veri hırsızlığı
- Genel veri sızıntıları
- Öncelikli kullanıcılara göre veri sızıntıları
- Bozuk kullanıcılar tarafından veri sızıntıları

> [!NOTE]
> Kümülatif sızdırma algılama, ilkede seçilen insider risk yönetimi ve sızdırma göstergeleri için genel ayarlarda etkinleştirilen sızdırma göstergelerini kullanır. Bu nedenle kümülatif sızdırma algılaması yalnızca seçilen gerekli sızdırma göstergeleri için değerlendirilir. Öncelik içeriğinde yapılandırılan [duyarlılık etiketleri](sensitivity-labels.md) için kümülatif sızdırma etkinlikleri daha yüksek risk puanları oluşturur.

Veri hırsızlığı veya veri sızıntısı ilkeleri için kümülatif sızdırma algılama etkinleştirildiğinde, kümülatif sızdırma etkinliklerinden elde edilen içgörüler, bir iç risk yönetimi olayı içindeki **Kullanıcı etkinliği** sekmesinde görüntülenir.

Kullanıcı etkinliği yönetimi hakkında daha fazla bilgi edinmek için bkz. [Insider risk yönetimi örnekleri: Kullanıcı etkinlikleri](insider-risk-management-cases.md#user-activity).

## <a name="policy-health"></a>İlke durumu

İlke sistem durumu, insider risk yönetimi ilkelerinizle ilgili olası sorunlarla ilgili içgörüler sağlar. **İlkeler** sekmesindeki **Durum** sütunu, kullanıcı etkinliğinin bildirilmesini engelleyebilecek ilke sorunları veya etkinlik uyarılarının sayısının neden olağan dışı olduğu konusunda sizi uyarabilir. İlkenin sistem durumu, ilkenin iyi durumda olduğunu ve dikkate veya yapılandırma değişikliklerine gerek olmadığını da onaylayabilir.

İlkeyle ilgili sorunlar varsa, ilke sistem durumu, ilke sorunlarını çözmek için işlem yapmanıza yardımcı olacak bildirim uyarıları ve öneriler görüntüler. Bu bildirimler aşağıdaki sorunları çözmenize yardımcı olabilir:

- **Tamamlanmamış yapılandırmaya sahip ilkeler**. Bu sorunlar, ilkedeki eksik kullanıcıları veya grupları veya diğer tamamlanmamış ilke yapılandırma adımlarını içerebilir.
- **Gösterge yapılandırma sorunları olan ilkeler**. Göstergeler her ilkenin önemli bir parçasıdır. Göstergeler yapılandırılmamışsa veya çok az gösterge seçiliyse, ilke riskli etkinlikleri beklendiği gibi değerlendirmeyebilir.
- **İlke tetikleyicileri çalışmıyor veya ilke tetikleyici gereksinimleri düzgün yapılandırılmamış**. İlke işlevselliği, ilkedeki kullanıcılara risk puanı atamasını etkinleştirmek üzere tetikleyici olayları etkili bir şekilde algılamak için diğer hizmetlere veya yapılandırma gereksinimlerine bağlı olabilir. Bu bağımlılıklar bağlayıcı yapılandırması, Uç Nokta için Microsoft Defender uyarı paylaşımı veya veri kaybı önleme ilkesi yapılandırma ayarlarıyla ilgili sorunları içerebilir.
- **Birim sınırları sınırları yaklaşıyor veya aşıyor**. Insider risk yönetimi ilkeleri, risk etkinliği sinyallerini toplamak için çok sayıda Microsoft 365 hizmeti ve uç noktası kullanır. İlkelerinizdeki kullanıcı sayısına bağlı olarak, birim sınırları risk etkinliklerinin belirlenmesini ve raporlanmasında gecikmeye neden olabilir. Bu makalenin İlke şablonu sınırları bölümünde bu sınırlar hakkında daha fazla bilgi edinin.

İlkenin sistem durumunu hızla görüntülemek için **İlke** sekmesine ve **Durum** sütununa gidin. Burada her ilke için aşağıdaki ilke sistem durumu seçeneklerini göreceksiniz:

- *Sağlıklı*: İlkeyle ilgili hiçbir sorun belirlendi.
- *Öneriler*: İlkeyle ilgili, ilkenin beklendiği gibi çalıştırılmasını engelleyebilecek bazı sorunlar vardır.
- *Uyarılar*: İlkeyle ilgili, riskli etkinlikleri tanımlamasını engelleyecek sorunlar vardır.

Öneriler veya uyarılar hakkında daha fazla ayrıntı için **İlke** sekmesinde bir ilke seçerek ilke ayrıntıları kartını açın. Bu sorunların nasıl giderileceğine ilişkin yönergeler de dahil olmak üzere öneriler ve uyarılar hakkında daha fazla bilgi, ayrıntılar kartının **Bildirimler** bölümünde görüntülenir.

![Insider risk yönetimi ilkesi sistem durumu.](../media/insider-risk-policy-health.png)

### <a name="notification-messages"></a>Bildirim iletileri

Öneriler ve uyarı bildirimleri ve olası sorunları çözmek için yapılması gereken eylemler hakkında daha fazla bilgi edinmek için aşağıdaki tabloyu kullanın.

|Bildirim iletileri|İlke şablonları|Nedenler / Düzeltmek için bu eylemi deneyin|
|---|---|---|
|İlke, etkinliğe risk puanları atamıyor|Tüm ilke şablonları|İlkenin etkinliklere risk puanları atayabilmesi için ilke kapsamınızı gözden geçirmek ve olay yapılandırmasını tetiklemeniz gerekebilir <br><br> 1. İlke için seçilen kullanıcıları gözden geçirin. Seçili kullanıcı sayısı azsa, başka kullanıcılar da seçebilirsiniz. <br> 2. İk bağlayıcısı kullanıyorsanız İk bağlayıcınızın doğru verileri gönderdiğinden emin olun. <br> 3. Tetikleyici olayı olarak bir DLP ilkesi kullanıyorsanız, bu ilkede kullanılmak üzere yapılandırıldığından emin olmak için DLP ilke yapılandırmanızı denetleyin. <br> 4. Güvenlik ihlali ilkeleri için Insider risk ayarları > Akıllı algılamalar bölümünde seçilen Uç Nokta için Microsoft Defender uyarı önceliklendirme durumunu gözden geçirin. Uyarı filtresinin çok dar olmadığını onaylayın.|
|İlke hiçbir uyarı oluşturmadı|Tüm ilke şablonları|İlke yapılandırmanızı gözden geçirerek ilgilendiğiniz etkinliği puanlama işlemini analiz etmek isteyebilirsiniz. <br><br> 1. Puanlamak istediğiniz göstergeleri seçtiğinizi onaylayın. Ne kadar çok gösterge seçilirse, risk puanları o kadar fazla etkinlik atanır. <br> 2. İlke için eşik özelleştirmesini gözden geçirin. Seçilen eşikler kuruluşunuzun risk toleransıyla uyumlu değilse, uyarıların tercih ettiğiniz eşiklere göre oluşturulması için seçimleri ayarlayın. <br> 3. İlke için seçilen kullanıcıları ve grupları gözden geçirin. Tüm geçerli kullanıcıları ve grupları seçtiğinizi onaylayın. <br> 4. Güvenlik ihlali ilkeleri için, ayarlardaki Akıllı Algılamalar'da Uç Nokta için Microsoft Defender uyarıları için puanlamak istediğiniz uyarı önceliklendirme durumunu seçtiğinizi onaylayın.|
|Bu ilkeye hiçbir kullanıcı veya grup dahil değildir|Tüm ilke şablonları|Kullanıcılar veya gruplar ilkeye atanmadı. <br><br> İlkenizi düzenleyin ve ilke için kullanıcıları veya grupları seçin.|
|Bu ilke için hiçbir gösterge seçilmedi|Tüm ilke şablonları|İlke için göstergeler seçilmedi <br><br> İlkenizi düzenleyin ve ilke için uygun ilke göstergelerini seçin.|
|Bu ilkeye öncelikli kullanıcı grubu eklenmez|- Öncelikli kullanıcılara göre veri sızıntıları <br> - Öncelikli kullanıcılara göre güvenlik ilkesi ihlalleri|İlkeye öncelikli kullanıcı grupları atanmadı. <br><br> Insider risk yönetimi ayarlarında öncelikli kullanıcı gruplarını yapılandırın ve ilkeye öncelikli kullanıcı grupları atayın.|
|Bu ilke için tetikleyici olay seçilmedi|Tüm ilke şablonları|İlke için tetikleme olayı yapılandırılmadı <br><br> İlkeyi düzenleyip tetikleyici bir olay seçene kadar risk puanları kullanıcı etkinliklerine atanmayacak.|
|İk bağlayıcısı yapılandırılmadı veya beklendiği gibi çalışmıyor|- Ayrılan kullanıcı tarafından veri hırsızlığı <br> - Ayrılan kullanıcının güvenlik ilkesi ihlalleri <br> - Bozuk kullanıcılar tarafından veri sızıntıları <br> - Dağıtılmamış kullanıcıların güvenlik ilkesi ihlalleri|İk bağlayıcısıyla ilgili bir sorun var. <br><br> 1. İk bağlayıcısı kullanıyorsanız İk bağlayıcınızın doğru veri gönderip göndermediğini denetleyin <br><br> VEYA <br><br> 2. Silinen Azure AD hesap tetikleyici olayını seçin.|
|Hiçbir cihaz eklenmedi|- Ayrılan kullanıcılar tarafından veri hırsızlığı <br> - Genel veri sızıntıları <br> - Bozuk kullanıcılar tarafından veri sızıntıları <br> - Öncelikli kullanıcılara göre veri sızıntıları|Cihaz göstergeleri seçili ancak Microsoft 365'e eklenen cihaz yok <br><br> Cihazların eklenip eklenmediğini denetleyin ve gereksinimleri karşılayın.|
|İk bağlayıcısı son zamanlarda verileri karşıya yüklemedi|- Ayrılan kullanıcı tarafından veri hırsızlığı <br> - Ayrılan kullanıcının güvenlik ilkesi ihlalleri <br> - Bozuk kullanıcılar tarafından veri sızıntıları <br> - Dağıtılmamış kullanıcıların güvenlik ilkesi ihlalleri|İk bağlayıcısı 7 günden uzun süredir verileri içeri aktarmadı. <br><br> İk bağlayıcınızın doğru yapılandırılıp yapılandırılmadığını ve veri gönderilip gönderilmediğini denetleyin.|
|İk bağlayıcınızın durumunu şu anda kontrol edemiyoruz, lütfen daha sonra yeniden denetleyin|- Ayrılan kullanıcı tarafından veri hırsızlığı <br> - Ayrılan kullanıcının güvenlik ilkesi ihlalleri <br> - Bozuk kullanıcılar tarafından veri sızıntıları <br> - Dağıtılmamış kullanıcıların güvenlik ilkesi ihlalleri|Insider risk yönetimi çözümü İk bağlayıcınızın durumunu denetleyemiyor. <br><br> İk bağlayıcınızın doğru yapılandırılıp yapılandırılmadığını ve veri gönderilip gönderilmediğini denetleyin veya geri dönüp ilke durumunu denetleyin.|
|Tetikleme olayı olarak DLP ilkesi seçilmedi|- Genel Veri sızıntıları <br> - Öncelikli kullanıcılara göre veri sızıntıları|Bir DLP ilkesi tetikleyici olay olarak seçilmedi veya seçilen DLP ilkesi silindi. <br><br> İlkeyi düzenleyin ve etkin bir DLP ilkesi seçin veya ilke yapılandırmasında tetikleyici olay olarak 'Kullanıcı sızdırma etkinliği gerçekleştirir'.|
|Bu ilkede kullanılan DLP ilkesi kapalı|- Genel Veri sızıntıları <br> - Öncelikli kullanıcılara göre veri sızıntıları|Bu ilkede kullanılan DLP ilkesi kapalıdır. <br><br> 1. Bu ilkeye atanan DLP ilkesini açın. <br><br> VEYA <br><br> 2. Bu ilkeyi düzenleyin ve yeni bir DLP ilkesi seçin veya ilke yapılandırmasında tetikleyici olay olarak 'Kullanıcı bir sızdırma etkinliği gerçekleştirir'.|
|DLP ilkesi gereksinimleri karşılamıyor|- Genel Veri sızıntıları <br> - Öncelikli kullanıcılara göre veri sızıntıları|Olayları tetikleme olarak kullanılan DLP ilkeleri, yüksek önem derecesinde uyarılar oluşturacak şekilde yapılandırılmalıdır. <br><br>  1. Geçerli uyarıları *Yüksek önem derecesi* olarak atamak için DLP ilkenizi düzenleyin. <br><br> VEYA <br><br> 2. Bu ilkeyi düzenleyin ve *Tetikleme olayı olarak Kullanıcı bir sızdırma etkinliği gerçekleştirir'i* seçin.|
|Kuruluşunuzun Uç Nokta için Microsoft Defender aboneliği yok|- Genel güvenlik ilkesi ihlalleri <br> - Ayrılan kullanıcıların güvenlik ilkesi ihlalleri <br> - Dağıtılmamış kullanıcıların güvenlik ilkesi ihlalleri <br> - Öncelikli kullanıcılara göre güvenlik ilkesi ihlalleri|Kuruluşunuz için etkin bir Uç Nokta için Microsoft Defender aboneliği algılanmadı. <br><br> bir Uç Nokta için Microsoft Defender aboneliği eklenene kadar, bu ilkeler kullanıcı etkinliğine risk puanları atamaz.|
|Uç Nokta için Microsoft Defender uyarıları uyumluluk portalıyla paylaşılmıyor|- Genel güvenlik ilkesi ihlalleri <br> - Ayrılan kullanıcıların güvenlik ilkesi ihlalleri <br> - Dağıtılmamış kullanıcıların güvenlik ilkesi ihlalleri <br> - Öncelikli kullanıcılara göre güvenlik ilkesi ihlalleri|Uç Nokta için Microsoft Defender uyarılar uyumluluk portalıyla paylaşılmıyor. <br><br> Uç Nokta için Microsoft Defender uyarı paylaşımını yapılandırın.|
|Bu ilke şablonu için etkin olarak puanlanan maksimum kullanıcı sınırına yaklaşıyorsunuz.|Tüm ilke şablonları|Her ilke şablonunun kapsam içi kullanıcı sayısı üst sınırı vardır. Şablon sınırı bölüm ayrıntılarına bakın. <br><br> Kullanıcılar sekmesindeki kullanıcıları gözden geçirin ve artık puanlanması gerekmeyen kullanıcıları kaldırın.|
|Tetikleme olayı, bu ilkedeki kullanıcıların %15'inden fazlasında art arda gerçekleşir.|Tüm ilke şablonları|Kullanıcıların ilke kapsamına girme sıklıklarını azaltmaya yardımcı olmak için tetikleyici olayını ayarlayın.|

## <a name="policy-template-limits"></a>İlke şablonu sınırları

Insider risk yönetimi ilkesi şablonları kapsam içi kullanıcı riski etkinlikleri için işlem hacmini ve oranını ve bu işlemin Microsoft 365 hizmetlerini desteklemeyle nasıl tümleştirileceğini yönetmek için sınırları kullanır. Her ilke şablonu, risk etkinliklerini destekleyip etkili bir şekilde işleyip raporlayabildiği ilke için etkin olarak atanabilecek en fazla sayıda kullanıcıya sahiptir. Kapsam içi kullanıcılar, ilke için olayları tetikleyen kullanıcılardır.

Her ilkenin sınırı, ilke şablonu türü başına risk puanı alan toplam benzersiz kullanıcı sayısına göre hesaplanır. İlke şablonu türü için kullanıcı sayısı kullanıcı sınırına yakınsa veya sınırı aşarsa, ilke performansı düşer. İlkenin geçerli kullanıcı sayısını görüntülemek için İlke sekmesine ve Kapsam içindeki kullanıcılar sütununa gidin. Herhangi bir ilke şablonu için en fazla beş ilkeniz olabilir. Bu maksimum sınırlar, belirli bir ilke şablonunu kullanan tüm ilkeler genelinde kullanıcılar için geçerlidir.

Her ilke şablonu için desteklenen en fazla kapsam içi kullanıcı sayısını belirlemek için aşağıdaki tabloyu kullanın:

|İlke şablonu|Geçerli kapsam içi kullanıcı üst sınırı|
|---|---|
|Genel veri sızıntısı|15,000|
|Bozuk kullanıcılar tarafından veri sızıntısı|7,500|
|Öncelikli kullanıcılara göre veri sızıntısı|1,000|
|Ayrılan kullanıcılar tarafından veri hırsızlığı|20,000|
|Genel güvenlik ilkesi ihlalleri|1,000|
|Genel hasta verilerini kötüye kullanma|5,000|
|Öncelikli kullanıcılara göre güvenlik ilkesi ihlali|1,000|
|Ayrılan kullanıcıların güvenlik ilkesi ihlalleri|15,000|
|Dağıtılmamış kullanıcıların güvenlik ilkesi ihlalleri|7,500|

## <a name="create-a-new-policy"></a>Yeni ilke oluşturma

Yeni bir insider risk yönetimi ilkesi oluşturmak için, Microsoft Purview uyumluluk portalı **Insider risk yönetimi** çözümünde ilke sihirbazını kullanacaksınız.

Yeni ilke oluşturmak için aşağıdaki adımları tamamlayın:

1. [Microsoft Purview uyumluluk portalı](https://compliance.microsoft.com) **Insider risk yönetimi'ne** gidin ve **İlkeler** sekmesini seçin.
2. İlke sihirbazını açmak için İlke **oluştur'u** seçin.
3. **İlke şablonu** sayfasında bir ilke kategorisi seçin ve ardından yeni ilkenin şablonunu seçin. Bu şablonlar, algılamak ve araştırmak istediğiniz risk etkinliklerini tanımlayan koşullar ve göstergelerden oluşur. Bu ilke şablonunun gereksinimlerinize uygun olduğunu onaylamak için şablon önkoşullarını, tetikleyici olayları ve algılanan etkinlikleri gözden geçirin.

    > [!IMPORTANT]
    > Bazı ilke şablonlarının, ilgili uyarıları oluşturmak üzere ilke için yapılandırılması gereken önkoşulları vardır. Geçerli ilke önkoşullarını yapılandırmadıysanız yukarıdaki **4. adıma** bakın.

4. Devam etmek için **İleri'yi** seçin.
5. **Ad ve açıklama** sayfasında aşağıdaki alanları doldurun:
    - **Ad (gerekli):** İlke için kolay bir ad girin. İlke oluşturulduktan sonra bu ad değiştirilemez.
    - **Açıklama (isteğe bağlı)**: İlke için bir açıklama girin.

6. Devam etmek için **İleri'yi** seçin.
7. **Kullanıcılar ve gruplar** sayfasında, İlkeye hangi kullanıcıların veya grupların dahil olduğunu tanımlamak için **Tüm kullanıcıları ve grupları ekle'yi** veya **Belirli kullanıcıları ve grupları ekle'yi** seçin ya da öncelikli kullanıcılara dayalı bir şablon seçtiyseniz; **Öncelikli kullanıcı grupları ekle veya düzenle'yi** seçin. **Tüm kullanıcıları ve grupları dahil et'i** seçtiğinizde, ilke için risk puanları atamaya başlamak için kuruluşunuzdaki tüm kullanıcılar ve gruplar için tetikleme olayları aranacaktır. **Belirli kullanıcıları ve grupları dahil et'i** seçtiğinizde ilkeye atanacak kullanıcıları ve grupları tanımlayabilirsiniz. Konuk kullanıcı hesapları desteklenmez.
8. Devam etmek için **İleri'yi** seçin.
9. **Öncelik sırasına alınacak içerik** sayfasında, öncelik sırasına göre kaynakları atayabilir (gerekirse) bu kaynaklar için yüksek önem derecesi uyarısı oluşturma olasılığını artırabilirsiniz. Aşağıdaki seçeneklerden birini seçin:

    - **SharePoint sitelerini, duyarlılık etiketlerini ve/veya hassas bilgi türlerini öncelikli içerik olarak belirtmek istiyorum**. Bu seçeneğin seçilmesi, sihirbazdaki ayrıntılı sayfaların bu kanalları yapılandırmasına olanak tanır.
    - **Şu anda öncelik içeriğini belirtmek istemiyorum (ilke oluşturulduktan sonra bunu yapabilirsiniz)**. Bu seçeneğin seçilmesi, sihirbazdaki kanal ayrıntı sayfalarını atlar.

10. Devam etmek için **İleri'yi** seçin.

11. Önceki adımda **SharePoint sitelerini, duyarlılık etiketlerini, hassas bilgi türlerini ve/veya dosya uzantılarını öncelik içeriği olarak belirtmek istiyorum** seçeneğini belirlediyseniz, *SharePoint sitelerinin* ayrıntı sayfalarını, *hassas bilgi türlerini*, *duyarlılık etiketlerini* ve *dosya uzantılarını* görürsünüz. İlkeye öncelik vermek üzere SharePoint, hassas bilgi türleri ve duyarlılık etiketlerini tanımlamak için bu ayrıntı sayfalarını kullanın.

    - **SharePoint siteleri**: **SharePoint sitesi ekle'yi** seçin ve erişiminiz olan ve önceliklendirmek istediğiniz SharePoint sitelerini seçin. Örneğin, *"group1@contoso.sharepoint.com/sites/group1"*.
    - **Hassas bilgi türü**: **Hassas bilgi türü ekle'yi** seçin ve önceliklendirmek istediğiniz duyarlılık türlerini seçin. Örneğin, *"ABD Banka Hesap Numarası"* ve *"Kredi Kartı Numarası"*.
    - **Duyarlılık etiketleri**: **Duyarlılık etiketi ekle'yi** seçin ve önceliklendirmek istediğiniz etiketleri seçin. Örneğin, *"Gizli"* ve *"Gizli"*.
    - **Dosya uzantıları**: En fazla 50 dosya uzantısı ekleyin. '.' dosyasını dosya uzantısına ekleyebilir veya atlayabilirsiniz. Örneğin, *.py* veya *py* Python dosyalarının önceliklerini belirlemeye yöneliktir.

    >[!NOTE]
    >İlkeyi yapılandıran ve öncelikli Share Point sitelerini seçen kullanıcılar, erişim iznine sahip oldukları SharePoint sitelerini seçebilir. SharePoint siteleri geçerli kullanıcı tarafından ilkede seçilemiyorsa, gerekli izinlere sahip başka bir kullanıcı ilkenin sitelerini daha sonra seçebilir veya geçerli kullanıcıya gerekli sitelere erişim verilmesi gerekir.

12. Devam etmek için **İleri'yi** seçin.
13. *Öncelikli kullanıcılara göre* *Genel veri sızıntıları veya Veri sızıntıları* şablonlarını seçtiyseniz, özel tetikleyici olayları ve ilke göstergeleri için Bu ilkenin **tetikleyicileri** sayfasında seçenekleri görürsünüz. Etkinlik puanlaması için ilkeye atanan kullanıcıları kapsama alanlara getiren olayları tetikleme için bir DLP ilkesi veya gösterge seçme seçeneğiniz vardır. **Kullanıcı bir veri kaybı önleme (DLP) ilkesi tetikleme olayıyla eşleşir** seçeneğini belirlerseniz, bu iç risk yönetimi ilkesi için DLP İlkesi için tetikleyici göstergelerini etkinleştirmek üzere DLP ilkesi açılan listesinden bir DLP ilkesi seçmeniz gerekir. **Kullanıcı bir sızdırma etkinliği tetikleme olayı gerçekleştirir** seçeneğini belirlerseniz, ilke tetikleyici olayı için listelenen göstergelerden birini veya daha fazlasını seçmeniz gerekir.
    >[!IMPORTANT]
    >Listelenen bir göstergeyi seçemiyorsanız bunun nedeni, bunların kuruluşunuz için etkinleştirilmemiş olmasıdır. İlkeyi seçip atayabilmelerini sağlamak için **Insider risk yönetimi** > **Ayarları** > **İlke göstergelerinde göstergeleri** etkinleştirin.

    Diğer ilke şablonlarını seçtiyseniz özel tetikleyici olayları desteklenmez. Olayları tetikleyen yerleşik ilke uygulanır ve ilke öznitelikleri tanımlamadan 23. Adıma devam edersiniz.

14. Devam etmek için **İleri'yi** seçin.
15. Öncelikli kullanıcılara göre *Genel veri sızıntıları* veya *Veri sızıntıları şablonlarını* seçtiyseniz ve **Kullanıcı bir sızdırma etkinliği ve ilişkili göstergeler gerçekleştirir'i** seçtiyseniz, seçtiğiniz olayları tetikleyen gösterge için özel veya varsayılan eşikleri seçebilirsiniz. Tetikleyici olaylar için **Varsayılan eşikleri kullan (Önerilen)** veya **Özel eşikleri kullan'ı** seçin.
16. Devam etmek için **İleri'yi** seçin.
17. **Tetikleyici olaylar için özel eşikleri kullan'ı** seçtiyseniz, 13. Adımda seçtiğiniz her tetikleyici olay göstergesi için istenen etkinlik uyarısı düzeyini oluşturmak için uygun düzeyi seçin.
18. Devam etmek için **İleri'yi** seçin.
19. **İlke göstergeleri** sayfasında, **Insider risk ayarları** > **Göstergeleri** sayfasında kullanılabilir olarak tanımladığınız [göstergeleri](insider-risk-management-settings.md#indicators) görürsünüz. İlkeye uygulamak istediğiniz göstergeleri seçin.

    > [!IMPORTANT]
    > Bu sayfadaki göstergeler seçilemiyorsa, tüm ilkeler için etkinleştirmek istediğiniz göstergeleri seçmeniz gerekir. Sihirbazdaki **Göstergeleri aç** düğmesini kullanabilir veya **Insider risk yönetimi** > **Ayarlar** > **İlkesi göstergeleri** sayfasında göstergeleri seçebilirsiniz.

    En az bir *Office* veya *Cihaz* göstergesi seçtiyseniz **, Risk puanı güçlendiricilerini** uygun şekilde seçin. Risk puanı güçlendiricileri yalnızca seçili göstergeler için geçerlidir.
    *Veri hırsızlığı* veya *Veri sızıntıları* ilke şablonu seçtiyseniz, ilkeye uygulanacak bir veya daha fazla **Sıra algılama** yöntemi ve **bir Kümülatif sızdırma algılama** yöntemi seçin.

20. Devam etmek için **İleri'yi** seçin.
21. **Varsayılan veya özel gösterge eşiklerini kullanmaya karar ver** sayfasında, seçtiğiniz ilke göstergeleri için özel veya varsayılan eşikleri seçin. **Tüm göstergeler için varsayılan eşikleri kullan'ı** veya Seçili ilke göstergeleri için **özel eşikler belirtin'i** seçin. Özel eşikleri belirtin'i seçtiyseniz, her ilke göstergesi için istenen etkinlik uyarı düzeyini oluşturmak için uygun düzeyi seçin.
22. Devam etmek için **İleri'yi** seçin.
23. **Gözden Geçir** sayfasında, ilke için seçtiğiniz ayarları ve seçimleriniz için önerileri veya uyarıları gözden geçirin. İlke değerlerinden herhangi birini değiştirmek için **Düzenle'yi** veya ilkeyi oluşturup etkinleştirmek için **Gönder'i** seçin.

## <a name="update-a-policy"></a>İlkeyi güncelleştirme

Mevcut bir insider risk yönetimi ilkesini güncelleştirmek için, Microsoft Purview uyumluluk portalı **Insider risk yönetimi** çözümünde ilke sihirbazını kullanacaksınız.

Mevcut bir ilkeyi yönetmek için aşağıdaki adımları tamamlayın:

1. [Microsoft Purview uyumluluk portalı](https://compliance.microsoft.com) **Insider risk yönetimi'ne** gidin ve **İlkeler** sekmesini seçin.
2. İlke panosunda yönetmek istediğiniz ilkeyi seçin.
3. İlke ayrıntıları sayfasında **İlkeyi düzenle'yi** seçin
4. İlke sihirbazında aşağıdakileri düzenleyemezsiniz:
    - **İlke şablonu**: İlke tarafından izlenen risk göstergesi türlerini tanımlamak için kullanılan şablon.
    - **Ad**: İlkenin kolay adı
5. **Ad ve açıklama** sayfasında, **Açıklama** alanındaki ilkenin açıklamasını güncelleştirin.
6. Devam etmek için **İleri'yi** seçin.
7. **Kullanıcılar ve gruplar** sayfasında, İlkeye hangi kullanıcıların veya grupların dahil olduğunu tanımlamak için **Tüm kullanıcıları ve grupları ekle'yi** veya **Belirli kullanıcıları ve grupları ekle'yi** seçin ya da öncelikli kullanıcılara dayalı bir şablon seçtiyseniz; **Öncelikli kullanıcı grupları ekle veya düzenle'yi** seçin. **Tüm kullanıcıları ve grupları dahil et'i** seçtiğinizde, ilke için risk puanları atamaya başlamak için kuruluşunuzdaki tüm kullanıcılar ve gruplar için tetikleme olayları aranacaktır. **Belirli kullanıcıları ve grupları dahil et'i** seçtiğinizde ilkeye atanacak kullanıcıları ve grupları tanımlayabilirsiniz. Konuk kullanıcı hesapları desteklenmez.
8. Devam etmek için **İleri'yi** seçin.
9. **Öncelik sırasına alınacak içerik** sayfasında, öncelik sırasına göre kaynakları atayabilir (gerekirse) bu kaynaklar için yüksek önem derecesi uyarısı oluşturma olasılığını artırabilirsiniz. Aşağıdaki seçeneklerden birini seçin:

    - **SharePoint sitelerini, duyarlılık etiketlerini, hassas bilgi türlerini ve/veya dosya uzantılarını öncelikli içerik olarak belirtmek istiyorum**. Bu seçeneğin seçilmesi, sihirbazdaki ayrıntılı sayfaların bu kanalları yapılandırmasına olanak tanır.
    - **Şu anda öncelik içeriğini belirtmek istemiyorum (ilke oluşturulduktan sonra bunu yapabilirsiniz)**. Bu seçeneğin seçilmesi, sihirbazdaki kanal ayrıntı sayfalarını atlar.

10. Devam etmek için **İleri'yi** seçin.

11. Önceki adımda **SharePoint sitelerini, duyarlılık etiketlerini ve/veya hassas bilgi türlerini öncelik içeriği olarak belirtmek istiyorum** seçeneğini belirlediyseniz, *SharePoint sitelerinin* ayrıntı sayfalarını, *hassas bilgi türlerini* ve *duyarlılık etiketlerini* görürsünüz. İlkeye öncelik vermek üzere SharePoint, hassas bilgi türleri ve duyarlılık etiketlerini tanımlamak için bu ayrıntı sayfalarını kullanın.

    - **SharePoint siteleri**: **SharePoint sitesi ekle'yi** seçin ve erişiminiz olan ve önceliklendirmek istediğiniz SharePoint sitelerini seçin. Örneğin, *"group1@contoso.sharepoint.com/sites/group1"*.
    - **Hassas bilgi türü**: **Hassas bilgi türü ekle'yi** seçin ve önceliklendirmek istediğiniz duyarlılık türlerini seçin. Örneğin, *"ABD Banka Hesap Numarası"* ve *"Kredi Kartı Numarası"*.
    - **Duyarlılık etiketleri**: **Duyarlılık etiketi ekle'yi** seçin ve önceliklendirmek istediğiniz etiketleri seçin. Örneğin, *"Gizli"* ve *"Gizli"*.
    - **Dosya uzantıları**: En fazla 50 dosya uzantısı ekleyin. '.' dosyasını dosya uzantısına ekleyebilir veya atlayabilirsiniz. Örneğin, *.py* veya *py* Python dosyalarının önceliklerini belirlemeye yöneliktir.

    >[!NOTE]
    >İlkeyi yapılandıran ve öncelikli Share Point sitelerini seçen kullanıcılar, erişim iznine sahip oldukları SharePoint sitelerini seçebilir. SharePoint siteleri geçerli kullanıcı tarafından ilkede seçilemiyorsa, gerekli izinlere sahip başka bir kullanıcı ilkenin sitelerini daha sonra seçebilir veya geçerli kullanıcıya gerekli sitelere erişim verilmesi gerekir.

12. Devam etmek için **İleri'yi** seçin.
13. *Öncelikli kullanıcılara göre* *Genel veri sızıntıları veya Veri sızıntıları* şablonlarını seçtiyseniz, özel tetikleyici olayları ve ilke göstergeleri için Bu ilkenin **tetikleyicileri** sayfasında seçenekleri görürsünüz. Etkinlik puanlaması için ilkeye atanan kullanıcıları kapsama alanlara getiren olayları tetikleme için bir DLP ilkesi veya gösterge seçme seçeneğiniz vardır. **Kullanıcı bir veri kaybı önleme (DLP) ilkesi tetikleme olayıyla eşleşir** seçeneğini belirlerseniz, bu iç risk yönetimi ilkesi için DLP İlkesi için tetikleyici göstergelerini etkinleştirmek üzere DLP ilkesi açılan listesinden bir DLP ilkesi seçmeniz gerekir. **Kullanıcı bir sızdırma etkinliği tetikleme olayı gerçekleştirir** seçeneğini belirlerseniz, ilke tetikleyici olayı için listelenen göstergelerden birini veya daha fazlasını seçmeniz gerekir.
    >[!IMPORTANT]
    >Listelenen bir göstergeyi seçemiyorsanız bunun nedeni, bunların kuruluşunuz için etkinleştirilmemiş olmasıdır. İlkeyi seçip atayabilmelerini sağlamak için **Insider risk yönetimi** > **Ayarları** > **İlke göstergelerinde göstergeleri** etkinleştirin.

    Diğer ilke şablonlarını seçtiyseniz özel tetikleyici olayları desteklenmez. Olayları tetikleyen yerleşik ilke uygulanır ve ilke öznitelikleri tanımlamadan 23. Adıma devam edersiniz.

14. Devam etmek için **İleri'yi** seçin.
15. Öncelikli kullanıcılara göre *Genel veri sızıntıları* veya *Veri sızıntıları şablonlarını* seçtiyseniz ve **Kullanıcı bir sızdırma etkinliği ve ilişkili göstergeler gerçekleştirir'i** seçtiyseniz, seçtiğiniz olayları tetikleyen gösterge için özel veya varsayılan eşikleri seçebilirsiniz. Tetikleyici olaylar için **Varsayılan eşikleri kullan (Önerilen)** veya **Özel eşikleri kullan'ı** seçin.
16. Devam etmek için **İleri'yi** seçin.
17. **Tetikleyici olaylar için özel eşikleri kullan'ı** seçtiyseniz, 13. Adımda seçtiğiniz her tetikleyici olay göstergesi için istenen etkinlik uyarısı düzeyini oluşturmak için uygun düzeyi seçin.
18. Devam etmek için **İleri'yi** seçin.
19. **İlke göstergeleri** sayfasında, **Insider risk ayarları** > **Göstergeleri** sayfasında kullanılabilir olarak tanımladığınız [göstergeleri](insider-risk-management-settings.md#indicators) görürsünüz. İlkeye uygulamak istediğiniz göstergeleri seçin.

    > [!IMPORTANT]
    > Bu sayfadaki göstergeler seçilemiyorsa, tüm ilkeler için etkinleştirmek istediğiniz göstergeleri seçmeniz gerekir. Sihirbazdaki **Göstergeleri aç** düğmesini kullanabilir veya **Insider risk yönetimi** > **Ayarlar** > **İlkesi göstergeleri** sayfasında göstergeleri seçebilirsiniz.

    En az bir *Office* veya *Cihaz* göstergesi seçtiyseniz **, Risk puanı güçlendiricilerini** uygun şekilde seçin. Risk puanı güçlendiricileri yalnızca seçili göstergeler için geçerlidir.
    *Veri hırsızlığı* veya *Veri sızıntıları* ilke şablonu seçtiyseniz, ilkeye uygulanacak bir veya daha fazla **Sıra algılama** yöntemi ve **bir Kümülatif sızdırma algılama** yöntemi seçin.

20. Devam etmek için **İleri'yi** seçin.
21. **Varsayılan veya özel gösterge eşiklerini kullanmaya karar ver** sayfasında, seçtiğiniz ilke göstergeleri için özel veya varsayılan eşikleri seçin. **Tüm göstergeler için varsayılan eşikleri kullan'ı** veya Seçili ilke göstergeleri için **özel eşikler belirtin'i** seçin. Özel eşikleri belirtin'i seçtiyseniz, her ilke göstergesi için istenen etkinlik uyarı düzeyini oluşturmak için uygun düzeyi seçin.
22. Devam etmek için **İleri'yi** seçin.
23. **Gözden Geçir** sayfasında, ilke için seçtiğiniz ayarları ve seçimleriniz için önerileri veya uyarıları gözden geçirin. İlke değerlerinden herhangi birini değiştirmek için **Düzenle'yi** veya ilkeyi oluşturup etkinleştirmek için **Gönder'i** seçin.

## <a name="copy-a-policy"></a>İlkeyi kopyalama

Var olan bir ilkeye benzeyen ancak yalnızca birkaç yapılandırma değişikliği gerektiren yeni bir ilke oluşturmanız gerekebilir. Sıfırdan yeni ilke oluşturmak yerine, var olan bir ilkeyi kopyalayabilir ve ardından yeni ilkede güncelleştirililmesi gereken alanları değiştirebilirsiniz.

Mevcut bir ilkeyi kopyalamak için aşağıdaki adımları tamamlayın:

1. [Microsoft Purview uyumluluk portalı](https://compliance.microsoft.com) **Insider risk yönetimi'ne** gidin ve **İlkeler** sekmesini seçin.
2. İlke panosunda kopyalamak istediğiniz ilkeyi seçin.
3. İlke ayrıntıları sayfasında Kopyala'yı seçin.
4. İlke sihirbazında yeni ilkeyi adlandırın ve ilke yapılandırmasını gerektiği gibi güncelleştirin.

## <a name="immediately-start-scoring-user-activity"></a>Kullanıcı etkinliğini puanlamaya hemen başlayın

Insider risk yönetimi tetikleyici olay iş akışının dışında, içeriden risk ilkeleri olan kullanıcılara risk puanlarını hemen atamaya başlamanız gereken senaryolar olabilir. **İlkeler** **sekmesindeki kullanıcılar için Puanlama etkinliğini başlat'ı** kullanarak belirli bir süre boyunca bir veya daha fazla iç risk ilkesine el ile kullanıcı (veya kullanıcılar) ekleyin, etkinliklerine risk puanlarını hemen atamaya başlayın ve kullanıcının tetikleme göstergesine (DLP ilkesi eşleşmesi gibi) sahip olması gereksinimini atlayın. Kullanıcıyı ilkeye eklemek için bir neden de ekleyebilirsiniz. Bu neden kullanıcıların etkinlik zaman çizelgesinde görünür. İlkelere el ile eklenen kullanıcılar **Kullanıcılar** panosunda görüntülenir ve etkinlik ilke uyarı eşiklerini karşılıyorsa uyarılar oluşturulur.

Kullanıcı etkinliklerini hemen puanlamaya başlamak isteyebileceğiniz bazı senaryolar:

- Kullanıcılar risk endişeleriyle tanımlandığında ve bir veya daha fazla ilkeniz için etkinliklerine risk puanları atamaya hemen başlamak istediğinizde
- Bir veya daha fazla ilkeniz için ilgili kullanıcıların etkinliğine risk puanlarını hemen atamanızı gerektirebilecek bir olay olduğunda
- İk bağlayıcınızı henüz yapılandırmadıysanız ancak kullanıcılar için bir .csv dosyası yükleyerek İk olayları için kullanıcı etkinliklerine risk puanları atamaya başlamak istediğinizde

> [!NOTE]
> El ile eklenen yeni kullanıcıların **Kullanıcılar** panosunda görünmesi birkaç saat sürebilir. Bu kullanıcılar için önceki 90 güne ilişkin etkinliklerin görüntülenmesi 24 saat kadar sürebilir. El ile eklenen kullanıcıların etkinliklerini görüntülemek için **Kullanıcılar** sekmesine gidin, **Kullanıcılar** panosunda kullanıcıyı seçin ve ayrıntılar **bölmesindeki Kullanıcı etkinliği** sekmesini açın.

Bir veya daha fazla iç risk yönetimi ilkesindeki kullanıcılar için puanlama etkinliğini el ile başlatmak için aşağıdaki adımları tamamlayın:

1. [Microsoft Purview uyumluluk portalı](https://compliance.microsoft.com) **Insider risk yönetimi'ne** gidin ve **İlkeler** sekmesini seçin.
2. İlke panosunda, kullanıcıları eklemek istediğiniz ilkeyi veya ilkeleri seçin.
3. **Kullanıcılar için puanlama etkinliğini başlat'ı** seçin.
4. **Birden çok ilkeye kullanıcı ekle** bölmesindeki **Neden alanında**, kullanıcıları eklemek için bir neden ekleyin.
5. **Bu sürenin süresi (5 ile 30 gün arasında seçin)** alanında, kullanıcının eklendiği ilkenin etkinliğini puanlayacak gün sayısını tanımlayın
6. Active Directory'nizde kullanıcıları aramak için Kullanıcı ara alanını kullanarak **ilkelere ekleyin** . İlkelere eklemek istediğiniz kullanıcının adını yazın. İlkelere ek kullanıcılar atamak için kullanıcı adını seçin ve tekrarlayın. Seçtiğiniz kullanıcıların listesi, Birden çok ilkeye kullanıcı ekle bölmesinin kullanıcılar bölümünde görünür.
7. İlkelere eklenecek kullanıcıların listesini içeri aktarmak için **İçeri Aktar'ı** seçerek .csv (virgülle ayrılmış değerler) dosyasını içeri aktarın. Dosya aşağıdaki biçimde olmalı ve dosyadaki kullanıcı asıl adlarını listelemeniz gerekir:

    ```csv
    user principal name
    user1@domain.com
    user2@domain.com
    ```

8. Değişiklikleri kabul etmek ve ilkelere kullanıcı eklemek için İlkelere kullanıcı ekle'yi seçin veya değişiklikleri atmak ve iletişim kutusunu kapatmak için İptal'i seçin.

## <a name="stop-scoring-users-in-a-policy"></a>İlkedeki kullanıcıları puanlamayı durdurma

İlkedeki kullanıcıları puanlamayı durdurmak için [Insider risk yönetimi kullanıcıları: Kullanıcıları ilkelere kapsam içi atamadan kaldırma makalesine](insider-risk-management-users.md#remove-users-from-in-scope-assignment-to-policies) bakın.

## <a name="delete-a-policy"></a>İlke silme

> [!NOTE]
> İlke silindiğinde, ilkeden oluşturulan etkin veya arşivlenmiş uyarılar silinmez.

Mevcut bir insider risk yönetimi ilkesini silmek için aşağıdaki adımları tamamlayın:

1. [Microsoft Purview uyumluluk portalı](https://compliance.microsoft.com) **Insider risk yönetimi'ne** gidin ve **İlkeler** sekmesini seçin.
2. İlke panosunda silmek istediğiniz ilkeyi seçin.
3. Pano araç çubuğunda **Sil'i** seçin.
4. **Sil** iletişim kutusunda, ilkeyi silmek için **Evet'i** seçin veya iletişim kutusunu kapatmak için **İptal'i** seçin.
