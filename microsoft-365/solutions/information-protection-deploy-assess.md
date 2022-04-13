---
title: veri gizliliği risklerini değerlendirme ve Microsoft 365 ile hassas öğeleri tanımlama
ms.author: bcarter
author: brendacarter
f1.keywords:
- NOCSH
manager: laurawi
ms.date: 07/13/2020
audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- Strat_O365_Enterprise
- m365solution-infoprotection
- m365solution-scenario
ms.custom: ''
description: Veri gizliliği düzenlemelerini, ilgili senaryoları, hazır olma durumunuzu ve Microsoft 365 ortamınızdaki hassas bilgi türlerini belirleyin.
ms.openlocfilehash: ea151577f31ad8ea9454addf171c1079f334d377
ms.sourcegitcommit: 195e4734d9a6e8e72bd355ee9f8bca1f18577615
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/13/2022
ms.locfileid: "64822704"
---
# <a name="assess-data-privacy-risks-and-identify-sensitive-items-with-microsoft-365"></a>veri gizliliği risklerini değerlendirme ve Microsoft 365 ile hassas öğeleri tanımlama

Kuruluşunuzun tabi olduğu veri gizliliği düzenlemelerini ve risklerini değerlendirmek, Microsoft 365 özellikleri ve hizmetleriyle ulaşılabilir eylemler de dahil olmak üzere ilgili iyileştirme eylemlerini uygulamadan önce ilk adımdır.

## <a name="potentially-applicable-data-privacy-regulations"></a>Olası geçerli veri gizliliği düzenlemeleri

Veri gizliliği düzenlemeleri için daha geniş bir mevzuat çerçevesi hakkında iyi bir başvuru için [Microsoft Hizmetleri Güven Portalı'na](https://servicetrust.microsoft.com/) ve [Genel Veri Koruma Yönetmeliği (GDPR) yönetmeliğine ilişkin makale serisine](/compliance/regulatory/gdpr) bakın. Ayrıca, sektörünüzde veya bölgenizde tabi olabileceğiniz düzenlemelere ilişkin malzemeleri gözden geçirin.

### <a name="gdpr"></a>GDPR

GDPR, veri gizliliği düzenlemelerinin en iyi bilinen ve alıntısı olandır. Avrupa Birliği'nin (AB) ikamet eden kimliği belirlenmiş veya tanımlanabilir bir gerçek kişiyle ilgili tüm kişisel verilerin toplanmasını, depolanmasını, işlenmesini ve paylaşıldığını düzenler.

GDPR Madde 4'e göre:

- 'kişisel veriler', tanımlanan veya tanımlanabilir bir gerçek kişiyle ('veri sahibi') ilgili herhangi bir bilgi anlamına gelir; tanımlanabilir bir gerçek kişi, özellikle ad, kimlik numarası, konum verileri, çevrimiçi tanımlayıcı gibi bir tanımlayıcıya veya o gerçek kişinin fiziksel, fizyolojik, genetik, zihinsel, ekonomik, kültürel veya sosyal kimliğine özgü bir veya daha fazla faktöre başvurularak, doğrudan veya dolaylı olarak tanımlanabilen kişidir.

### <a name="iso-27001"></a>ISO 27001

ISO 27001 gibi diğer standartlara uygunluk, çeşitli Avrupa denetim otoriteleri tarafından insanlar, süreç ve teknoloji spektrumu genelinde geçerli bir amaç proxy'si olarak kabul edilmiştir. ISO-27001 temelli koruma mekanizmalarına çakışma ve uymayı belirttiği standartlar, belirli durumlarda bazı gizlilik yükümlülüklerini yerine getiren bir proxy olarak kabul edilebilir.

### <a name="other-data-privacy-regulations"></a>Diğer veri gizliliği düzenlemeleri

Diğer önemli veri gizliliği düzenlemeleri de kişisel verilerin işlenmesine yönelik gereksinimleri belirtir.

Birleşik Devletler bunlar California Tüketici Koruma Yasası ([CCPA](/compliance/regulatory/ccpa-faq)), HIPAA-HITECH (Birleşik Devletler sağlık hizmetleri gizlilik yasası) ve Graham Leach Bliley Yasası (GLBA) içerir. Devlete özgü ek düzenlemeler de yerinde veya geliştirme aşamasındadır.

Diğer örnekler arasında Almanya'nın Ulusal GDPR Uygulama Yasası (BDSG), Brezilya Veri Koruma Yasası (LGPD) ve diğerleri sayılabilir.

## <a name="regulation-mapping-to-microsoft-365-technical-control-categories"></a>Microsoft 365 teknik denetim kategorilerine düzenleme eşlemesi

Veri gizliliğiyle ilgili düzenlemelerin çoğu çakışan gereksinimlere sahiptir, bu nedenle herhangi bir teknik denetim şeması geliştirmeden önce hangi düzenlemelere tabi olduklarını anlamalısınız.

Bu genel çözümün makalelerinde daha sonra başvurmak için, bu tabloda veri gizliliği düzenlemelerinin örneklemesinden alıntılar sağlanır.

|Düzenleme|Makale/bölüm|Alıntı|Geçerli teknik denetim kategorileri|
|---|---|---|---|
|GDPR|Madde 5(1)(f)|Kişisel veriler, yetkisiz veya yasa dışı işlemeye karşı koruma ve uygun teknik veya kurumsal önlemler ('bütünlük ve gizlilik' kullanılarak yanlışlıkla kaybedilme, imha veya hasara karşı koruma dahil olmak üzere kişisel verilerin uygun güvenliğini sağlayacak şekilde işlenecektir.|(Tümü) <br> Kimlik <br> Cihaz <br> Tehdit Koruması <br> Bilgileri koruma <br> İdare bilgileri <br> Keşfetme ve yanıtlama|
||Makale (32)(1)(a)|Sanat durumunu, uygulama maliyetlerini ve doğasını, kapsamını, bağlamını ve işleme amaçlarını ve gerçek kişilerin hak ve özgürlükleri için değişken olasılık ve önem derecesini göz önünde bulundurarak, denetleyici ve işlemci riske uygun bir güvenlik düzeyi sağlamak için uygun teknik ve kurumsal önlemler uygulayacaktır,  uygun şekilde inter alia dahil: (a) kişisel verilerin takma adlandırılması ve şifrelenmesi.|Bilgileri koruma|
||Makale (13)(2)(a)|"... denetleyici, kişisel veriler elde edildiğinde, veri sahibine adil ve şeffaf bir şekilde işlenmesini sağlamak için gereken aşağıdaki ek bilgileri sağlayacaktır: (a) kişisel verilerin depolanacağı süre veya mümkün değilse, bu süreyi belirlemek için kullanılan ölçütler.|İdare bilgileri|
||Makale (15)(1)(e)|Veri sahibi, kendisiyle ilgili kişisel verilerin işlenip işlenmediği ve bu durumda kişisel verilere erişim ve aşağıdaki bilgilerle ilgili olarak denetleyici onayı alma hakkına sahip olacaktır: (e) denetleyiciden kişisel verilerin düzeltilmesini veya silinmesini isteme hakkının varlığı ya da kişisel verilerin ilgili verilerle ilgili işlenmesinin kısıtlanması ya da buna itiraz etme hakkı Işleme|Keşfetme ve yanıtlama|
|LGPD|Madde 46|İşleme aracıları, kişisel verileri yetkisiz erişimlerden ve yanlışlıkla veya yasa dışı imha, kayıp, değiştirme, iletişim ya da herhangi bir uygunsuz veya yasa dışı işleme türünden koruyabilen güvenlik, teknik ve idari önlemleri benimseyecektir.|Bilgileri koruma <br> İdare bilgileri <br> Keşfetme ve yanıtlama|
||Makale 48|Denetleyicinin ulusal yetkiliye ve veri sahibine, veri öznelerinde risk veya ilgili hasar oluşturabilecek bir güvenlik olayının meydana geldiğini bildirmesi gerekir.|Keşfetme ve yanıtlama|
|HIPPA-HITECH|45 CFR 164.312(e)(1)|Elektronik iletişim ağı üzerinden iletilen elektronik korumalı sistem durumu bilgilerine yetkisiz erişime karşı korunmak için teknik güvenlik önlemleri uygulayın.|Bilgileri koruma|
||45 C.F.R. 164.312(e)(2)(ii)|Uygun görüldüğünde elektronik korumalı sistem durumu bilgilerini şifrelemek için bir mekanizma uygulayın.|Bilgileri koruma|
||45 CFR 164.312(c)(2)|Elektronik korumalı sistem durumu bilgilerinin yetkisiz bir şekilde değiştirilmediğini veya yok edilmediğini doğrulayan elektronik mekanizmalar uygulayın.|İdare bilgileri|
||45 CFR 164.316(b)(1)(i)|Bu alt bölümün belgelenmiş olması için bir eylem, etkinlik veya değerlendirme gerekiyorsa, eylemin, etkinliğin veya değerlendirmenin yazılı (elektronik olabilir) kaydını koruyun|İdare bilgileri|
||45 CFR 164.316(b)(1)(ii)|Bu bölümün paragrafı (b)(1) için gereken belgeleri, oluşturulduğu tarihten veya en son yürürlüğe giren tarihten (hangisi daha sonraysa) itibaren 6 yıl boyunca saklayın.|İdare bilgileri|
||45 C.F.R. 164.308(a)(1)(ii)(D)|Denetim günlükleri, erişim raporları ve güvenlik olayı izleme raporları gibi bilgi sistemi etkinliğinin kayıtlarını düzenli olarak gözden geçirmek için yordamlar uygulayın|Keşfetme ve yanıtlama|
||45 C.F.R. 164.308(a)(6)(ii)|Şüpheli veya bilinen güvenlik olaylarını belirleme ve yanıtlama; kapsamına alınan varlık veya iş ortağı tarafından bilinen güvenlik olaylarının uygulanabilir, zararlı etkilerini azaltmak; ve güvenlik olaylarını ve bunların sonuçlarını belgelemektedir.|Keşfetme ve yanıtlama|
||45 C.F.R. 164.312(b)|Elektronik korumalı sistem durumu bilgilerini içeren veya kullanan bilgi sistemlerinde etkinliği kaydeden ve inceleyen donanım, yazılım ve yordam mekanizmaları uygulayın.|Keşfetme ve yanıtlama|
|CCPA|1798.105(c)|Bir tüketiciden, bu bölümün (a) bölümü uyarınca tüketicinin kişisel bilgilerini silmek için doğrulanabilir bir istek alan bir işletme, tüketicinin kişisel bilgilerini kayıtlarından silecek ve tüm hizmet sağlayıcılarını tüketicinin kişisel bilgilerini kayıtlarından silmeye yönlendirecektir|Keşfetme ve yanıtlama|
||1798.105(d)|(1798.105(c) özel durumları <br> bir işletmenin veya hizmet sağlayıcısının, tüketicinin kişisel bilgilerini şu şekilde tutması gerekiyorsa, bir işletmenin veya hizmet sağlayıcısının tüketicinin kişisel bilgilerini silme isteğine uyması gerekmeyecektir: (ek bilgi için geçerli yönetmeliğe bakın).|Keşfetme ve yanıtlama|
|||||

> [!IMPORTANT]
> Bu, kapsamlı bir liste olarak tasarlanmamıştır. Belirtilen bölümlerin listelenen teknik denetim kategorilerine uygulanabilirliği hakkında daha fazla bilgi için [Uyumluluk Yöneticisi'ne](../compliance/compliance-manager.md) veya yasal veya uyumluluk danışmanınıza başvurun.

## <a name="knowing-your-data"></a>Verilerinizi öğrenme

Tabi olduğunuz düzenlemelere bakılmaksızın, kuruluşunuzun içindeki ve dışındaki farklı kullanıcı veri türlerinin sistemlerinizle etkileşime geçtiği durumlarda, kuruluşunuz için geçerli olan sektör ve kamu düzenlemelerine tabi olarak, genel kişisel veri koruma stratejinizi etkileyebilecek tüm önemli faktörlerdir. Bu, kişisel verilerin nerede depolandığını, ne tür olduğunu, ne kadarının bulunduğunu ve hangi koşullarda toplandığını içerir.

![Verilerinizi öğrenme: Ne tür olduğunu, ne kadarının bulunduğunu ve hangi koşullar altında toplandığını öğrenin.](../media/information-protection-deploy-assess/information-protection-deploy-assess-knowing-data.png)

### <a name="data-portability"></a>Veri taşınabilirliği

Veriler ayrıca işlendikçe, iyileştirilirken ve diğer sürümler ondan türetildikçe zaman içinde hareket eder. İlk anlık görüntü hiçbir zaman yeterli olmaz. Verilerinizi bilmek için devam eden bir süreç olmalıdır. Bu, önemli hacimlerde kişisel verileri işleyen büyük kuruluşlar için en büyük zorluklardan birini temsil eder. "Verilerinizi bilin" sorununu gidermeyen kuruluşlar büyük olasılıkla çok yüksek risklere ve düzenleyici kurumlardan olası para cezalarına neden olabilir.

![Veri yaşam döngüsü.](../media/information-protection-deploy-assess/information-protection-deploy-assess-data-lifecycle.png)

### <a name="where-the-personal-data-is"></a>Kişisel verilerin bulunduğu yer

Veri gizliliği düzenlemelerini ele almak için, kişisel verilerin şu anda veya gelecekte nerede mevcut olabileceğini düşündüğünüze ilişkin genel düşüncelere güvenemezsiniz. Veri gizliliği düzenlemeleri, kuruluşların kişisel verilerin nerede olduğunu sürekli olarak bildiklerini kanıtlamalarını gerektirir. Bu, Microsoft 365 ortamınız da dahil olmak üzere olası kişisel bilgilerin depolanması için tüm veri kaynaklarınızın ilk anlık görüntüsünü almayı ve sürekli izleme ve algılama mekanizmaları oluşturmanızı önemli kılar.

Veri gizliliği düzenlemeleriyle ilişkili genel hazırlığınızı ve riskinizi henüz değerlendirmediyseniz, başlamak için aşağıdaki 3 adımlı çerçeveyi kullanın.

![Veri gizliliği düzenlemeleriyle ilişkili genel hazırlığınızı ve riskinizi değerlendirme adımları.](../media/information-protection-deploy-assess/information-protection-deploy-assess-grid.png)

> [!NOTE]
> Bu makalenin ve içeriğinin yasal danışmanlık hizmetlerinin yerini alması amaçlanmamaktadır. Yalnızca değerlendirmenizin ilk aşamalarında yardımcı olabilecek bazı temel yönergeler ve araçlara bağlantılar sağlar.

## <a name="step-1-develop-a-foundational-understanding-of-your-organizations-personal-data-scenarios"></a>1. Adım: Kuruluşunuzun kişisel veri senaryoları hakkında temel bir anlayış geliştirme

Şu anda yönettiği kişisel verilerin türüne, nerede depolandığına, hangi koruyucu denetimlerin yerleştirildiğine, yaşam döngüsünün nasıl yönetildiğine ve kimlerin eriştiğine bağlı olarak veri gizliliği riskine maruz kalma riskini ölçmeniz gerekir.

Başlangıç noktası olarak, Microsoft 365 ortamınızda ne tür kişisel verilerin mevcut olduğunu envantere kaydetmek önemlidir. Şu kategorileri kullanın:

- Günlük iş işlevlerini gerçekleştirmek için gereken çalışan verileri
- Kuruluşun işletmeden işletmeye (B2B) senaryosundaki iş müşterileri, iş ortakları ve diğer ilişkileri hakkında sahip olduğu veriler
- Kuruluşun işletmeden müşteriye (B2C) senaryosunda yönettiği çevrimiçi hizmetler bilgi sağlayan tüketiciler hakkında sahip olduğu veriler

Burada, bir kuruluşun tipik bölümleri için farklı veri türlerinin bir örneği verilmiştir.

![Kişisel veri türleri.](../media/information-protection-deploy-assess/information-protection-deploy-assess-data-types.png)

Veri gizliliği düzenlemesine tabi olan kişisel verilerin çoğu genellikle Microsoft 365 dışında toplanır ve depolanır. Tüketiciye yönelik web veya mobil uygulamalardan gelen tüm kişisel verilerin Microsoft 365 içinde veri gizliliği incelemesine tabi olması için bu tür uygulamalardan Microsoft 365'a aktarılmış olması gerekir.

Microsoft 365'de verilerinizin gizliliğine maruz kalmanız web uygulamalarınıza ve CRM sistemlerinize göre daha sınırlı olabilir ve bu çözüm bu çözümle ilgili değildir.

Risk profilinizi değerlendirirken aşağıdaki yaygın veri gizliliği uyumluluk güçlükleri hakkında düşünmek de önemlidir:

- **Kişisel veri dağıtımı.** Belirli bir konu hakkındaki bilgiler ne kadar dağınıktır? Yasal kuruluşları uygun denetimlerin gerçekleştiğine ikna edecek kadar iyi biliniyor mu? Gerekirse araştırılabilir ve düzeltilebilir mi?
- **Sızdırmaya karşı koruma.** Belirli bir tür veya kaynağın kişisel verilerini tehlikeye atılmaktan nasıl korursunuz ve varsa nasıl yanıt verirsiniz?
- **Koruma ve risk karşılaştırması.** Riskle ilgili olarak hangi bilgi koruma mekanizmaları uygundur ve son kullanıcı müdahalesi gerekiyorsa iş sürekliliğini ve üretkenliği nasıl sürdürür ve son kullanıcı etkisini en aza indirir? Örneğin, el ile sınıflandırma veya şifreleme kullanılmalı mı?
- **Kişisel veri saklama.** Geçerli iş nedenleriyle kişisel verileri içeren bilgilerin ne kadar süreyle saklanması gerekiyor ve iş sürekliliği için saklama gereksinimleriyle dengelenmiş, geçmişteki sonsuza kadar saklama uygulamalarından nasıl kaçınılır?
- **Veri sahibi isteklerini işleme.** Veri sahibi isteklerini (DSR) ve anonimleştirme, yeniden düzenleme ve silme gibi herhangi bir düzeltme eylemini işlemek için hangi mekanizmalar gerekir?
- **Sürekli izleme ve raporlama.** Farklı veri türleri ve kaynakları için günlük izleme, araştırma ve raporlama teknikleri ne tür kullanılabilir?
- **Veri işlemeyle ilgili sınırlamalar.** Kuruluşun gizlilik denetimlerinde yansıtması gereken bu yöntemler aracılığıyla toplanan veya depolanan bilgiler için veri kullanımıyla ilgili sınırlamalar var mı? Örneğin, satış personeli tarafından kişisel verilerin kullanılmayacağı taahhütleri, kuruluşunuzun bu bilgilerin satış kuruluşuyla ilişkili sistemlerde aktarılmasını veya depolanmasını önlemek için mekanizmalar koymasını gerektirebilir.

### <a name="employee-data-required-to-carry-out-day-to-day-business-functions"></a>Günlük iş işlevlerini gerçekleştirmek için gereken çalışan verileri

Doğası gereği kuruluşların, çalışan sözleşmelerinde kabul ettiklerine bağlı olarak elektronik kimlik ve İk amaçları için çalışanlar hakkında veri toplaması gerekir. Bir kişi bir şirkette çalıştığı sürece, bu genellikle bir sorun değildir. Kuruluş, kötü amaçlı aktörlerin çalışan kişisel verilerini sızdırmasını veya sızdırmasını önlemek için mekanizmalar koymak isteyebilir.

Bir kişi şirketten ayrılırsa kuruluşların genellikle kullanıcı hesaplarını kaldırma, posta kutularının ve kişisel sürücülerin yetkisini alma ve insan kaynakları sistemleri gibi durumlarda çalışan durumunu değiştirme işlemleri, yordamları ve saklama ve silme zamanlamaları vardır. Davanın söz konusu olduğu durumlarda, bir çalışanın veya yasal soruşturmanın başka bir tarafı, kuruluşun sistemlerinde depolanan kişisel veriler hakkında bilgi almak için geçerli nedenlere sahip olabilir. Bazı durumlarda, söz konusu taraf bu tür verilerin kaldırılmasını veya anonim olmasını isteyebilir.

Kuruluşların bu tür ihtiyaçları karşılamak için, bu tür istekleri kolaylaştırmaya yönelik önleyici, dedektif ve düzeltici ihtiyaçları ele alan süreçler ve yordamlar olması gerekir ve bir çalışan hakkındaki bazı bilgilerin iş sürekliliği açısından makul bir şekilde önemli olarak değerlendirilebileceğini unutmayın. Örneğin, bir kişinin bir dosya yazdığını veya bir işlev gerçekleştirdiğini gösteren bilgiler.

> [!NOTE]
> Microsoft 365'daki kişisel verilere yönelik araştırma ve düzeltme teknikleri için [izleme ve yanıtlama makalesine](information-protection-deploy-monitor-respond.md) bakın. Ayrıca, kişisel verilerin kuruluş içindeyken denetlendiğinden emin olmak ve kötü amaçlı aktör durumlarında kuruluştan ayrılmasını önlemek için otomatik sınıflandırma ve koruma şemaları kullanmak isteyebilirsiniz. Daha fazla [bilgi için bilgileri koruma makalesine](information-protection-deploy-protect-information.md) bakın.

### <a name="data-the-organization-has-about-its-business-customers-in-the-b2b-scenario"></a>B2B senaryosunda kuruluşun işletme müşterileri hakkında sahip olduğu veriler

B2B bilgilerinin toplanması da zor bir durumdur çünkü kuruluşunuzun iş sürekliliği amacıyla çeşitli sistemlerinde müşteri adlarının ve işlemlerinin kayıtlarını tutması gerekebilir ancak bu bilgiler yanlışlıkla veya kötü amaçlı sızdırmaya karşı korunur. Çalışanların verileri gibi kuruluşların da bu tür verileri korumak için ilkeleri, yordamları ve teknik denetimleri olması ve tanımlanan saklama ve silme zamanlamalarına göre eskimesi gerekir.

Genellikle dış müşteriler, iş ortakları ve kuruluşun iş yaptığı diğer varlıklarla yapılan sözleşmelerde koruma, saklama ve silme dahil olmak üzere kuruluşun kuruluşla ilişkisi olduğu sırada ve sonrasında bu verilerin işlenmesini ele alan bir dil bulunur.

### <a name="data-the-organization-has-about-consumers-who-provide-information-to-online-services-that-the-organization-manages-in-the-b2c-scenario"></a>Kuruluşun B2C senaryosunda yönettiği çevrimiçi hizmetler bilgi sağlayan tüketiciler hakkında sahip olduğu veriler

Bu kategori, birçok genel müşteri veri sızıntısı örneği nedeniyle çoğu kişinin veri gizliliği için düşündüğü kategoridir. Bu, sağlayıcıyla sözleşme kapsamındaki üçüncü bir taraf gibi kasıtlı veya kötü amaçlı bir aktör tarafından sızma gibi kasıtsız olabilir. Tüketici verilerinin korunması, AB ve diğerlerinin bu düzenlemeleri düzenlemesinin başlıca nedenlerinden biridir. GDPR ve CCPA gibi veri gizliliği düzenlemeleri için planlama yapmanız gerekir:

- [Eylem planları](/compliance/regulatory/gdpr-action-plan) ve [sorumluluk hazırlığı denetim listeleri](/compliance/regulatory/gdpr-arc-Office365)
- [Veri Koruma Etki Değerlendirmeleri](/compliance/regulatory/gdpr-data-protection-impact-assessments)
- [İhlal bildirimleri](/compliance/regulatory/gdpr-breach-Office365)
- [Veri sahibi istekleri](/compliance/regulatory/gdpr-dsr-Office365)

Kuruluşunuz çok fazla doğrudan tüketiciden veri toplama işlemi gerçekleştirmiyorsa, bu kategori daha az sorun olabilir. Ancak, uyumluluk elde etmek için bu makalelerde özetlenen işlemleri yine de yapmanız gerekebilir.

### <a name="step-1-summary"></a>1. Adım özeti

Risk ve veri gizliliği düzenlemelerine maruz kalma durumunuzu anlamak, kuruluşunuzun kişisel veri senaryolarını temel alan önemli bir ilk adımdır.

Microsoft 365 ortamınızda tüketicilerden gelen kişisel verileriniz yoksa veya ortamın belirli bölümleriyle sınırlıysa ve teknik denetim gereksinimi, tüketici türündeki verilerin açığa çıkarıldığına göre önceden belirtiliyorsa, bu teknik denetimin her yerde değil, yalnızca ortamın yüksek riskli bölümlerinde çalıştırılması gerekebilir.

Microsoft 365'daki Uyumluluk Yöneticisi gibi bir dış kuruluş veya standart denetim kümesi önerisi denetim stratejinizi bilgilendirmeye yardımcı olabilir ancak gerçek risk kapsamınızı belirlemek için uygulama seçiminiz veri envanteri farkındalığı tarafından yönlendirilmelidir.

Çoğu kuruluş, yukarıdaki senaryolardan birine maruz kalacaktır. Değerlendirmeye bütüncül bir yaklaşım benimsemek önemlidir.

## <a name="step-2-assess-your-readiness-for-complying-with-data-privacy-regulations"></a>2. Adım: Veri gizliliği düzenlemelerine uymaya hazır olma durumunuzu değerlendirme

GDPR'ye özgü olsa da, ücretsiz [Microsoft GDPR değerlendirme aracında](https://clouddamcdnprodep.azureedge.net/gdc/1863571/original) sunulan sorular, genel veri gizliliği hazırlığınızı anlamak için iyi bir başlangıç sağlar.

Birleşik Devletler CCPA veya Brezilya'nın LGPD'si gibi diğer veri gizliliği düzenlemelerine tabi olan kuruluşlar, bu aracın GDPR ile çakışan hükümlerden dolayı hazır olma envanterinden de yararlanabilir.

GDPR değerlendirmesi şu bölümlerden oluşur:

|Bölüm|Açıklama|
|:-------|:-----|
|İdare|<ol><li>Gizlilik ilkeniz hangi veri bilgilerinin işlendiğini açıkça belirtir mi? </li><li>Gizlilik Etkisi Değerlendirmelerini (PIA) düzenli olarak çalıştırıyor musunuz? </li><li> Kişisel bilgileri (PI) yönetmek için bir araç kullanıyor musunuz? </li><li> Belirli bir kişi üzerinde PI verilerini kullanarak iş yapma konusunda yasal yetkiniz var mı? Veriler için onayı izliyor musunuz? </li><li> Denetim denetimlerini izliyor, uyguluyor ve yönetiyor musunuz? Veri sızıntılarını izliyor musunuz? </li></ol>|
|Silme ve bildirim|<ol><li>Kullanıcıların verilerine nasıl erişilebileceği hakkında açık yönergeler veriyor musunuz? </li><li> Onay almayı geri çevirme işlemini işlemek için belgelenmiş süreçleriniz var mı? </li><li> Veriler için Otomatik Silme işleminiz var mı? </li><li> Müşteriyle etkileşime geçtiğinde kimliği doğrulama işleminiz var mı? </li></ol>|
|Risk azaltma ve bilgi güvenliği|<ol><li>Yapılandırılmamış verileri taramak için araçlar kullanıyor musunuz? </li><li>Tüm sunucular güncel mi ve bunları korumak için güvenlik duvarlarından yararlanıyor musunuz? </li><li>Sunucularınızın düzenli yedeklemelerini çalıştırıyor musunuz? </li><li>Veri sızıntılarını etkin bir şekilde izliyor musunuz? </li><li>Bekleyen ve iletimdeki verilerinizi şifreler misiniz? </li></ol>|
|İlke yönetimi|<ol><li>Bağlama Şirket Kurallarınızı (BCR) nasıl yönetirsiniz? </li><li>Veriler için onayı izliyor musunuz? </li><li> Tamamen kapsanan 1 ile 5 arasında bir ölçekte sözleşmeleriniz veri sınıflandırmalarını ve işleme gereksinimlerini kapsıyor mu? </li><li>Bir olay yanıt planınız var mı ve düzenli olarak test mi edindiniz? </li><li>Erişimi yönetmek için hangi ilkeyi kullanırsınız? </li></ol>|
|||

## <a name="step-3-identify-sensitive-information-types-that-occur-in-your-microsoft-365-environment"></a>3. Adım: Microsoft 365 ortamınızda gerçekleşen hassas bilgi türlerini belirleme

Bu adım, belirli yasal denetimlere tabi olan belirli hassas bilgi türlerinin tanımlanmasını ve bunların Microsoft 365 ortamınızda oluşumunu içerir.

Ortamınızda kişisel içerik içeren içerik bulmak, daha önce Uyumluluk Arama, eBulma, Advanced eDiscovery, DLP ve denetimin bir birleşimini içeren, zor bir görev olabilir.

Microsoft Uyumluluk yönetim merkezindeki yeni **Veri Sınıflandırma** çözümü ile bu, kişisel verilerle ilgili olanlar da dahil olmak üzere yerleşik veya özel hassas bilgi türleriyle çalışan [İçerik Gezgini](../compliance/data-classification-content-explorer.md) özelliğiyle çok daha kolay hale gelmiştir.

### <a name="sensitive-information-types"></a>Hassas bilgi türleri

Microsoft Uyumluluk yönetim merkezi, çoğu kişisel verileri tanımlama ve bulma ile ilgili 100'den fazla hassas bilgi türüyle önceden yüklenmiş olarak gelir. Bu yerleşik hassas bilgi türleri, normal ifade (regex) veya işlev tarafından tanımlanan desenlere göre kredi kartı numaralarını, banka hesap numaralarını, pasaport numaralarını ve daha fazlasını tanımlamaya ve korumaya yardımcı olabilir. Daha fazla bilgi edinmek için bkz [. Hassas bilgi türleri ne arar](../compliance/sensitive-information-type-entity-definitions.md)?

Çalışan kimlikleri için özel biçim veya yerleşik hassas bilgi türü kapsamında olmayan diğer kişisel bilgiler gibi kuruluşa özgü veya bölgesel türde hassas öğeleri tanımlamanız ve korumanız gerekiyorsa, şu yöntemlerle özel bir hassas bilgi türü oluşturabilirsiniz:

- PowerShell
- Tam veri eşleşmesi (EDM) ile özel kurallar
- [Uyumluluk Puanı ve Uyumluluk Yöneticisi'ni Kullanma makalesinde](information-protection-deploy-compliance.md) vurgulandığı gibi Uyumluluk Merkezi yönetici kullanıcı arabirimi aracılığıyla

Ayrıca mevcut, yerleşik hassas bilgi türünü özelleştirebilirsiniz.

Daha fazla bilgi için şu makalelere bakın:

- [Yerleşik hassas bilgi türünü özelleştirme](../compliance/customize-a-built-in-sensitive-information-type.md)
- [Hassas bilgi türleri hakkında daha fazla bilgi edinme](../compliance/sensitive-information-type-learn-about.md)
- [Güvenlik & Uyumluluk Merkezi'nde özel hassas bilgi türü oluşturma](../compliance/create-a-custom-sensitive-information-type.md)
- [Güvenlik & Uyumluluk Merkezi PowerShell'de özel hassas bilgi türü oluşturma](../compliance/create-a-custom-sensitive-information-type-in-scc-powershell.md)
- [Tam Veri Eşleşmesi tabanlı sınıflandırma ile özel hassas bilgi türleri oluşturma](../compliance/create-custom-sensitive-information-types-with-exact-data-match-based-classification.md)

### <a name="content-explorer"></a>İçerik Gezgini

Ortamınızda hassas öğelerin oluşumunu belirlemek için Microsoft 365 Uyumluluk yönetim merkezindeki yeni [İçerik Gezgini'nin](../compliance/data-classification-content-explorer.md) önemli bir aracıdır. Hassas bilgi türlerinin ortaya çıkması ve sonuçların görüntülenmesi için Microsoft 365 aboneliğinizin tamamının ilk ve devam eden taraması için otomatikleştirilmiş bir araçtır.

Yeni İçerik Gezgini aracı, yerleşik hassas bilgi türlerini veya özel bilgileri kullanarak ortamınızdaki hassas öğelerin konumlarını hızla tanımlamanızı sağlar. Bu, hassas öğelerin varlığını ve konumunu düzenli olarak araştırmak için bir süreç oluşturmayı ve sorumluluk atamayı içerebilir.

Bu makalede vurgulanan diğer adımlarla birlikte, planlı Microsoft 365 yapılandırması ve izlemesi aracılığıyla korunacak hassas öğelerin genel risklere maruz kalma, hazır olma durumu ve konumunu belirlemeye yönelik bir başlangıç noktası sağlar.

### <a name="other-methods-to-identify-personal-data-in-your-environment"></a>Ortamınızdaki kişisel verileri tanımlamak için diğer yöntemler

kuruluşlar İçerik Gezgini'ne ek olarak, ortamlarında gelişmiş arama ölçütleri ve özel filtreler kullanarak kişisel verileri bulmak için özel aramalar oluşturmak için İçerik Arama özelliğine erişebilir.

Bu [makalede](/compliance/regulatory/gdpr) kişisel verileri bulmak için İçerik Arama'nın kullanımıyla ilgili ayrıntılı yönergeler sağlanmıştır. İçerik Arama ve diğer bulma teknikleri de [GDPR ve CCPA için DSR'lerde](/compliance/regulatory/gdpr-dsr-Office365#introduction-to-dsrs) incelenir.

Microsoft 365'daki kişisel veriler için araştırma ve düzeltme teknikleri hakkında ek içgörüler [izleyici ve yanıt makalesinde](information-protection-deploy-monitor-respond.md) sağlanır.

> [!NOTE]
> Şirket içinde depolanan dosyalarda hangi hassas bilgilere sahip olduğunuzu bulmak için bkz. [Azure Information Protection](/azure/information-protection/quickstart-findsensitiveinfo).
