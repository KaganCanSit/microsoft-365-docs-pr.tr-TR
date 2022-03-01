---
title: Veri gizliliği risklerini değerlendirin ve hassas öğeleri doğru Microsoft 365
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
description: Veri gizliliği düzenlemelerini, ilgili senaryoları, hazırlıklarınızı ve çalışma ortamınıza ilişkin hassas bilgi türlerini Microsoft 365.
ms.openlocfilehash: 5f8b5844ad3db4152a6144f9506a0267fa3af8f2
ms.sourcegitcommit: bae72428d229827cba4c807d9cd362417afbcccb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/02/2022
ms.locfileid: "63010153"
---
# <a name="assess-data-privacy-risks-and-identify-sensitive-items-with-microsoft-365"></a>Veri gizliliği risklerini değerlendirin ve hassas öğeleri doğru Microsoft 365

Verilerinizin tabi olduğu veri gizliliği düzenlemelerini ve risklerini değerlendirmek, proje özellikleri ve hizmetleriyle ilgili gerçekleştirilebilir eylemler de dahil olmak üzere ilgili iyileştirme eylemlerini hayata Microsoft 365 bir adımdır.

## <a name="potentially-applicable-data-privacy-regulations"></a>Geçerli olabilecek veri gizliliği düzenlemeleri

Veri gizliliği düzenlemelerine ilişkin daha geniş bir yasal düzenleme çerçevesi hakkında iyi bir referans için [, Microsoft Hizmetleri](https://servicetrust.microsoft.com/) Güven Portalı'na ve Genel Veri Koruma Yönetmeliği [(GDPR) yönetmeliğiyle ilgili makalelere bakın](/compliance/regulatory/gdpr). Ayrıca, endüstriniz veya bölgeniz için tabi olacağınız düzenlemelere ilişkin malzemeleri de gözden geçirin.

### <a name="gdpr"></a>GDPR

GDPR, veri gizliliği yasal düzenlemelerinin en iyi bilinen ve adı olandır. Avrupa Birliği'nde (AB) ikamet eden, tanımlanabilen veya tanımlanabilen bir doğal kişiyle ilgili tüm kişisel verilerin toplanması, depolanması, işlanması ve paylaşımına düzenlemeye devam ediyor.

GDPR Makalesine göre 4:

- 'kişisel veriler', tanımlanabilen veya tanımlanabilen bir doğal kişiyle ('veri konusu' ilgili tüm bilgiler) anlamına gelir; Tanımlanabilen doğal kişi, özellikle ad, tanımlama numarası, konum verileri, çevrimiçi tanımlayıcı veya bu doğal kişinin fiziksel, genetik, zihinsel, ekonomik, kültürel veya sosyal kimliğine özgü bir veya birden çok faktöre başvuru olarak tanımlanabilen, doğrudan veya dolaylı olarak tanımlanabilen kişidir.

### <a name="iso-27001"></a>ISO 27001

ISO 27001 gibi diğer standartlara bağlı kalma ayrıca, çeşitli Avrupa denetim yetkilileri tarafından kişiler, süreçler ve teknoloji yelpazesinde geçerli bir amacın proxy'si olarak tanındı. ÖRTÜşme ve ISO-27001 odaklı koruma mekanizmalarına bağlı olacağını belirten standartlar, bazı durumlarda bazı gizlilik yükümlülüklerini yerine getiren bir proxy olarak kabul edilir.

### <a name="other-data-privacy-regulations"></a>Diğer veri gizliliği düzenlemeleri

Diğer dikkat çeken veri gizliliği düzenlemeleri de kişisel verilerin işlenmesiyle ilgili gereksinimleri belirtir.

Amerika Birleşik Devletleri'nde, bunlar California Tüketici Koruma Yasası ([CCPA](/compliance/regulatory/ccpa-faq)), HIPAA-HITECH (AMERIKA Birleşik Devletleri sağlık bakımı gizlilik yasası) ve Graham Leach Bliley Yasası'dır (GLBA). Devlete özgü diğer düzenlemeler de yerindedir veya geliştirme aşamasındadır.

Dünya geneline, Almanya'nın Ulusal GDPR Uygulama Yasası (BDSG), Brezilya Veri Koruma Yasası (LGPD) ve daha birçok örnek daha vardır.

## <a name="regulation-mapping-to-microsoft-365-technical-control-categories"></a>Teknik denetim kategorilerinin Microsoft 365 eşlemesi

Veri gizliliğiyle ilgili düzenlemelerin birçoğu gereksinimleri çakışıyor, dolayısıyla herhangi bir teknik denetim düzenini geliştirmeden önce hangi yasal düzenlemelere tabi olduklarını anlamanız gerekir.

Bu genel çözümün makalelerine daha sonra başvuru için, bu tabloda veri gizliliğiyle ilgili düzenlemelere ilişkin alıntılar ve alıntılar bulunmaktadır.

|Düzenleme|Makale/bölüm|Alıntı|Geçerli teknik denetim kategorileri|
|---|---|---|---|
|GDPR|Makale 5(1)(f)|Kişisel veriler, yetkisiz veya yasa dışı işlemeye karşı koruma ve yanlışlıkla kayıp, zarar görme veya zarara karşı uygun teknik veya kurumsal ölçüler ('bütünlük ve gizlilik') kullanılarak kişisel verilerin uygun güvenliğini sağlayan bir şekilde işlenir.|(All) <br> Kimlik <br> Cihaz <br> Tehdit Koruması <br> Bilgileri koruma <br> Geçerli bilgiler <br> Keşfetme ve yanıtlama|
||Makale (32)(1)(a)|Doğal kişilerin hakları ve serbestlik hakları ve önem düzeyine yönelik farklı olasılık ve önem riski ile birlikte, sanat eserinin durumunu, uygulama maliyetlerini ve doğasını, kapsamını, bağlamını ve amaçlarını, ayrıca doğal kişilerin haklarını ve önem derecesini hesaba bağlı olarak dikkate alarak, denetleyici ve işlemci risk için uygun teknik ve kurumsal önlemleri uygulayacak,  uygun olduğu şekilde interlia da dahil: (a) takma ad ve kişisel verilerin şifreleştirilmesi.|Bilgileri koruma|
||Makale (13)(2)(a)|"... denetleyici, kişisel verilerin alınca adil ve saydam işlem sağlamak için gerekli olan diğer bilgileri veri konusuyla birlikte sağlar: (a) kişisel verilerin depolandığı dönem veya bu mümkün değilse, bu dönemi belirlemek için kullanılan ölçütler.|Geçerli bilgiler|
||Makale (15)(1)(e)|Veri konusu, ilgili kişisel verilerin işleniyor olup olmadığı ve bu durumda kişisel verilere ve şu bilgilere erişim ile ilgili olarak denetleyici onay kutusundan alma hakkı elde eder: (e) denetleyiciden kişisel verileri düzeltme veya silme hakkının varlığı ya da veri konusuyla ilgili kişisel verilerin işlenmesi ya da bu tür bir nesneye nesne ekleme hakkının var olması işleme|Keşfetme ve yanıtlama|
|LGPD|Makale 46|İşleme aracıları, kişisel verileri yetkisiz erişimlere, yanlışlıkla veya yasa dışı durumlara karşı yasal olmayan, kayıp, değiştirme, iletişim ya da uygunsuz veya yasa dışı herhangi bir tür işlemeye karşı koruyabilecek güvenlik, teknik ve yönetim önlemleri benimsemektedir.|Bilgileri koruma <br> Geçerli bilgiler <br> Keşfetme ve yanıtlama|
||Makale 48|Denetleyici, ulusal yetkiliye ve veri konularına risk veya ilgili zararlar oluşturabilecek bir güvenlik olayı oluşması durumuyla ilgili olarak veri konusuyla ilgili iletişim kurmalı.|Keşfetme ve yanıtlama|
|HIPPA-HITECH|45 CFR 164.312(e)(1)|Bir elektronik iletişim ağı üzerinden iletilen elektronik korumalı sağlık bilgilerine yetkisiz erişimi engellemek için teknik güvenlik önlemleri alın.|Bilgileri koruma|
||45 C.F.R. 164.312(e)(2)(ii)|Elektronik korumalı sağlık bilgilerini uygun görüldüğü her an şifrelemek için bir mekanizma uygulama.|Bilgileri koruma|
||45 CFR 164.312(c)(2)|Elektronik korumalı sağlık bilgisinin yetkisiz biçimde değiştirilmedi veya yok edilmeyen durum bilgilerini parolayla değiştirmek için elektronik mekanizmalar uygulama.|Geçerli bilgiler|
||45 CFR 164.316(b)(1)(i)|Bu alt bölüm için bir eylemin, etkinliğin veya değerlendirmenin belgeye uygun olması gerekirse, eylemin, etkinliğin veya değerlendirmenin yazılı (elektronik olabilir) kaydının korunmasını sağlar|Geçerli bilgiler|
||45 CFR 164.316(b)(1)(ii)|Bu bölümün paragraf (b)(1) tarafından oluşturulmasından sonraki 6 yıl veya en son yürürlüğe girecek tarih (hangisi daha sonra olursa) için gerekli belgeleri tutma.|Geçerli bilgiler|
||45 C.F.R. 164.308(a)(1)(ii)(D)|Denetim günlükleri, erişim raporları ve güvenlik olayı izleme raporları gibi bilgi sistemi etkinliğinin kayıtlarını düzenli olarak gözden geçirmek için yordamlar uygulama|Keşfetme ve yanıtlama|
||45 C.F.R. 164.308(a)(6)(ii)|Şüpheli veya bilinen güvenlik olaylarını tanımlama ve yanıtlama; kapsanacak varlık veya iş ortaklarının bilinen güvenlik olaylarının izin verdiği ölçüde zararlı etkiyi azaltmak; ve belge güvenlik olayları ve bunların sonuçları.|Keşfetme ve yanıtlama|
||45 C.F.R. 164.312(b)|Elektronik koruma durumu bilgileri içeren veya kullanan bilgi sistemlerindeki etkinliği kaydeden ve inceleyen donanım, yazılım ve yordam mekanizmaları kullanın.|Keşfetme ve yanıtlama|
|CCPA|1798.105(c)|Bu bölümün alt bölümü (a) uyarınca tüketicinin kişisel bilgilerini silmek için tüketiciden doğrulanabilir bir istek alan bir işletme, tüketicinin kişisel bilgilerini kayıtlarından silebilir ve tüm hizmet sağlayıcılarını, tüketicinin kişisel bilgilerini kayıtlarından silebilir|Keşfetme ve yanıtlama|
||1798.105(d)|(1798.105(c) <br> İşletmenin veya hizmet sağlayıcının, ticari veya hizmet sağlayıcının kişisel bilgilerini şu şekilde bulundurdu: (ek bilgiler için geçerli düzenlemeye bakın) gerekirse, tüketicinin kişisel bilgilerini silme talebine uyması gerekmez.|Keşfetme ve yanıtlama|
|||||

> [!IMPORTANT]
> Bunun çok kapsamlı bir liste olması hedefle değildir. Listelenen [teknik denetim](../compliance/compliance-manager.md) kategorilerine başvurulan bölümlerin uygulanabilirliği hakkında daha fazla bilgi için Uyumluluk Yöneticisi'ne veya yasal ya da uyumluluk danışmanınıza bakın.

## <a name="knowing-your-data"></a>Verilerinizi bilme

Tabi olduğunuz düzenlemelere bakılmaksızın, kuruluş içinde ve dışında farklı kullanıcı veri türlerinin sistemleriniz ile etkileşim kurduğu tüm önemli faktörler, genel kişisel veri koruma stratejinizi etkileyabilecek önemli faktörlerdir; bu faktörler, organizasyonunıza uygun endüstri ve kamu düzenlemelere tabidir. Kişisel verilerin nerede depolandığı, ne tür olduğu, ne kadar kişisel veri bulunduğu ve hangi koşullarda toplandığı bu tür bilgileri kapsar.

![Verilerinizi bilme: Ne tür olduğu, ne kadarı olduğu ve hangi koşullarda toplanmış olduğu.](../media/information-protection-deploy-assess/information-protection-deploy-assess-knowing-data.png)

### <a name="data-portability"></a>Veri taşınabilirliği

Veriler işlendiğinde, zariflendiklerinden ve diğer sürümlerden türetildiklerinden zaman içinde hareket eder. İlk anlık görüntü hiçbir zaman yeterli değildir. Verilerinizi bilmek için devam eden bir işlem yapılması gerekir. Bu, önemli hacimli kişisel verileri işlemekte olan büyük kuruluşların en büyük zorluklarından birini temsil eder. "Verilerinizi biliyor" sorununa çözüm bulmayan kuruluşlar, büyük olasılıkla çok yüksek risklere ve yasal düzenlemelere karşı olası ince bilgilerle sonuçlanabilecektir.

![Veri yaşam döngüsü.](../media/information-protection-deploy-assess/information-protection-deploy-assess-data-lifecycle.png)

### <a name="where-the-personal-data-is"></a>Kişisel verilerin nerede olduğu

Veri gizliliği düzenlemelerine yönelik olarak, kişisel verilerin şu anda veya gelecekte var olabileceğini düşünmeniz gereken genel notlara güvenebilirsiniz. Veri gizliliği düzenlemeleri, kuruluşların kişisel verilerin nerede olduğunu sürekli olarak biliyor olduklarını kanıtlamalarını gerektirir. Bu, Microsoft 365 ortamınız da dahil olmak üzere kişisel bilgilerin olası depolanması için tüm veri kaynaklarınızı içeren ilk anlık görüntüyü almanızı ve sürekli izleme ve algılama için mekanizmalar oluşturmanızı önemli yapar.

Veri gizliliği düzenlemeleriyle ilişkili genel hazırlık ve risklerinizi henüz değerlendirmedıysanız, kullanmaya başlamanız için aşağıdaki 3 adımlık çerçeveyi kullanın.

![Veri gizliliği düzenlemeleriyle ilişkili genel hazırlık ve risklerinizi değerlendirme adımları.](../media/information-protection-deploy-assess/information-protection-deploy-assess-grid.png)

> [!NOTE]
> Bu makalenin ve içeriğinin yasal danışmanlık hizmetlerini yerine götürmesi gerekli değildir. Yalnızca değerlendirmenizin ilk aşamalarında yardımcı olacak bazı temel rehberlik ve araçlara bağlantılar sağlar.

## <a name="step-1-develop-a-foundational-understanding-of-your-organizations-personal-data-scenarios"></a>1. Adım: Kuruluş kişisel veri senaryolarını temelden anlama

Şu anda yönetmekte olduğu kişisel verilerin türüne, nerede depolandığına, hangi koruyucu denetimlerin yerleştiril aralığına, yaşam döngüsünün nasıl yönetillandığına ve bu verilere kimlerin erişimi olduğuna bağlı olarak, veri gizliliği riskine maruz kalmaktan korunmayı ölçmeniz gerekir.

Başlangıç noktası olarak, bu ortamda kişisel verilerin türlerinde bulunan kişisel verilerin envanterini Microsoft 365 önemlidir. Şu kategorileri kullanın:

- Günlük iş işlevlerini yerine taşımak için gereken çalışan verileri
- Kuruluşun, işletmelere ilişkin (B2B) senaryolarında iş müşterileri, iş ortakları ve diğer ilişkileriyle ilgili verileri var
- Kuruluşun, kurumsal müşteri (B2C) senaryosunda yöneten çevrimiçi hizmetlere bilgi sağlayan tüketicilerle ilgili verileri

Burada, bir kuruluşun tipik departmanları için farklı veri türleri örneği ve almaktadır.

![Kişisel veri türleri.](../media/information-protection-deploy-assess/information-protection-deploy-assess-data-types.png)

Veri gizlilik düzenlemeye tabi olan kişisel verilerin büyük bir çoğu normalde verilerin dışında toplanır ve Microsoft 365. Tüketiciye yönelik web veya mobil uygulamalardan gelen tüm kişisel verilerin, kişisel verilerin Microsoft 365 gizlilik incelemesine tabi olması için söz konusu uygulamalardan Microsoft 365.

Bu çözümün karşı kullanma Microsoft 365, web uygulamalarınıza ve CRM sistemlerinize göre daha sınırlı olabilir.

Risk profilinizi değerlendirirken aşağıdaki yaygın veri gizliliği uyumluluğu güçlüklerini düşünmek de önemlidir:

- **Kişisel veri dağıtımı.** Dağılımlı bir konu hakkında ne kadar bilgi var? Mevzuat gövdelerini düzgün denetimlerin yerine konul olduğuna ikna etmek için iyi bilinen bir bilgi mi var? Gerekirse araştırma ve düzeltme olabilir mi?
- **Sızıntıya karşı koruma.** Verili bir türün veya kaynağın kişisel verilerini güvenliği ihlallerden nasıl korursunuz ve varsa nasıl yanıt verirsiniz?
- **Koruma ve risk.** Hangi bilgi koruma mekanizmaları risklere göre uygun olup, iş sürekliliğini ve üretkenliğini nasıl sürdürecek ve son kullanıcı müdahalesi gerekli olduğunda son kullanıcı etkisini en aza indirecektir? Örneğin elle sınıflandırma veya şifreleme kullanılmalı mı?
- **Kişisel veri bekletme.** Kişisel verileri içeren bilgilerin geçerli iş nedenleriyle ne kadar süreyle korunması ve geçmiş kalıcı saklama uygulamalarından nasıl kaçınılması gerekir ve iş sürekliliği için bekletme ihtiyaçlarıyla dengelemek gerekir?
- **Veri konusu isteklerini işleme.** Veri konusu isteklerini (DSR) ve anonimleştirme, yeniden işleme ve silme gibi düzeltme işlemlerini işlemek için hangi mekanizmalara ihtiyaç duyulacak?
- **Sürekli izleme ve raporlama.** Farklı veri türleri ve kaynakları için hangi tür günlük izleme, yatırım teknikleri ve raporlama teknikleri vardır?
- **Veri işlemeyle ilgili sınırlamalar.** Kuruluşun gizlilik denetimlerine yansıtması gereken bu yöntemler aracılığıyla toplanan veya depolanan bilgiler için veri kullanımında sınırlamalar var mı? Örneğin, kişisel verilerin satış personeli tarafından kullanılamayacak taahhütleri, satış kuruluşuyla ilişkili sistemlerde söz konusu bilgilerin aktarımını veya depolanmasını önleyen mekanizmalar koymasını gerekli bulundurabilirsiniz.

### <a name="employee-data-required-to-carry-out-day-to-day-business-functions"></a>Günlük iş işlevlerini yerine taşımak için gereken çalışan verileri

Doğaya göre kuruluşların, çalışan sözleşmelerinde kabul edildiklerine bağlı olarak elektronik kimlik ve İk amaçlarına uygun olarak çalışanlar üzerinde veri toplaması gerekir. Bir şirket için çalışan kişiler olduğu sürece, bu normalde bir sorun değildir. Kuruluş, çalışan kişisel verilerine sızıntı veya sızdırma amaçlı kötü amaçlı etkiyi önleyen mekanizmalar koymak istiyor olabilir.

Bir kişi şirketten ayrılırsa, kuruluşların normalde kullanıcı hesaplarını kaldırma, posta kutularını ve kişisel sürücüleri kaldırma ve insan kaynakları sistemleri gibi sistemlerde çalışan durumunu değiştirmeyle ilgili süreçler, yordamlar, bekletme ve silme zamanlamaları olur. Davanın söz konusu olduğu durumlarda, bir çalışan veya başka bir taraf yasal soruşturma için geçerli nedenler kuruluşun sistemlerinde depolanan kişisel veriler hakkında bilgi almak için geçerli nedenlere sahip olabilir. Bazı durumlarda, taraf bu tür verilerin kaldırılmasını veya anonim hale getirildirildiğini talep ediyor olabilir.

Bu tür ihtiyaçları karşılamak için kuruluşların, bu tür istekleri kolaylaştıracak önlem ve yordamlara sahip olması gerekir. Bir çalışanla ilgili bazı bilgilerin makul bir şekilde iş sürekliliği açısından kritik öneme sahip olduğunu göz önüne alınmalıdır. Örneğin, bir kişinin bir dosya yazması veya bir işlev gerçekleştirilen bilgiler.

> [!NOTE]
> Bu makaledeki kişisel verilere yatırım ve düzeltme teknikleri Microsoft 365, makaleyi izleme [ve yanıtlama makalesine bakın](information-protection-deploy-monitor-respond.md). Ayrıca, kişisel verilerin kuruluş içindeyken denetlenmakta olduğundan emin olmak ve kötü niyetli kuruluşlarda kuruluştan ayrılarak bu verilerin denetim altında olduğundan emin olmak için otomatik sınıflandırma ve koruma düzenlerini de kullanırabilirsiniz. Daha fazla [bilgi için koruma bilgileri](information-protection-deploy-protect-information.md) makalesine bakın.

### <a name="data-the-organization-has-about-its-business-customers-in-the-b2b-scenario"></a>B2B senaryosunda kuruluşun iş müşterileri hakkında sahip olduğu veriler

B2B bilgilerini toplama da çok zor olabilir, çünkü kuruluş müşteri adlarının ve işlemlerin kayıtlarını iş sürekliliği amacıyla çeşitli sistemlerde tutması, ancak bu bilgilerin yanlışlıkla veya kötü amaçlı sızıntılara karşı korunmasına ihtiyaç olabilir. Kuruluşların, çalışan verileri gibi, bu tür verileri korumak için ilkeleri, yordamları ve teknik denetimleri olması ve bu verileri tanımlı bekletme ve silme zamanlamaları göre yaşlarını ayamaları gerekir.

Normalde, dış müşteriler, ortaklar ve kuruluşun iş yaptığı diğer varlıklarla sözleşmeler, kuruluşun kuruluşla bir ilişkisi olduğu zaman ve sonrasında koruma, bekletme ve silme de dahil olmak üzere bu verilerin işlenmesine çözüm olarak dil bilgilerine sahip olur.

### <a name="data-the-organization-has-about-consumers-who-provide-information-to-online-services-that-the-organization-manages-in-the-b2c-scenario"></a>Kuruluşun B2C senaryosunda yöneten çevrimiçi hizmetlere bilgi sağlayan tüketiciler hakkında sahip olduğu veriler

Bu kategori, birçok genel müşteri veri sızıntıları nedeniyle veri gizliliği hakkında en çok insanların düşünmesi gereken kategoridir. Bu, sağlayıcıya yapılan bir sözleşmenin üçüncü taraf olması veya kötü niyetli bir ifadeyle ortaya alınması gibi bilerek yapılan bir durum olabilir. Tüketici verileri koruması, AB ve diğerlerinde bu düzenlemelerin başlıca nedenlerinden biridir. GDPR ve CCPA gibi veri gizliliğiyle ilgili düzenlemeler için planlama yapmayı gerektirir:

- [Eylem planları](/compliance/regulatory/gdpr-action-plan) [ve sorumluluk hazırlığı denetim listeleri](/compliance/regulatory/gdpr-arc-Office365)
- [Veri Koruması Değerlendirmeleri Etkiliyor](/compliance/regulatory/gdpr-data-protection-impact-assessments)
- [İhlal bildirimleri](/compliance/regulatory/gdpr-breach-Office365)
- [Veri konusu istekleri](/compliance/regulatory/gdpr-dsr-Office365)

If your organization does do çok fazla doğrudan-from-consumer data collection, this category may be less of an issue. Bununla birlikte, uyumluluğu elde etmek için yine de bu makalelerde ana hatları verilen işlemlerin üzerinden geçerek devam edin.

### <a name="step-1-summary"></a>Adım 1 özeti

Riske maruz kalmanızı ve veri gizlilik düzenlemelerini anlamanız, kurum verilerinizle ilgili senaryoları temelden anlamak temel öneme sahip bir adımdır.

Microsoft 365 ortamınıza tüketicilerden gelen kişisel verileriniz yoksa veya bu veriler ortamın belirli bölümleriyle sınırlı kalacaksa ve teknik denetime gerek kalmaları, tüketici türünde verilerin maruz kalma olarak maruz kalmalarına neden oluyorsa, bu teknik denetimin her yerde değil, yalnızca ortamın yüksek riskli bölümlerine yer olması gerekir.

Microsoft 365'ta Uyumluluk Yöneticisi'nin önerisini gibi bir dış kuruluş veya standart denetim kümesi önerisi denetim stratejinizi bilgilendirmeye yardımcı olabilir, ancak gerçek riskin ne kadar açık olacağını ölçmek için uygulama seçiminiz veri stoku farkındalığıyla yönlendirildi.

Çoğu kuruluş, yukarıdaki senaryolardan birinin maruz kalmak zorunda kalma süresine sahip olur. Değerlendirmeye holist bir yaklaşım benimser almak önemlidir.

## <a name="step-2-assess-your-readiness-for-complying-with-data-privacy-regulations"></a>2. Adım: Veri gizliliği düzenlemelerine uyumlu olmak için hazırlığınızı değerlendirin

GDPR'ye özgü olsa da, ücretsiz [Microsoft GDPR](https://clouddamcdnprodep.azureedge.net/gdc/1863571/original) değerlendirme aracında yer alan sorular, genel veri gizliliği hazırlığınızı anlama yolunda iyi bir başlangıç sağlar.

Kuruluşlar, ABD'deki CCPA veya Brazil's LGPD gibi diğer veri gizlilik düzenlemelerine tabidirler, GDPR ile birlikte, bu aracın hazırlık nedeniyle örtüşen hazırlık hükümlerinin envanteri de yararlanabilir.

GDPR değerlendirmesi şu bölümlerden oluşur:

|Bölüm|Açıklama|
|:-------|:-----|
|İdare|<ol><li>Gizlilik ilkeniz hangi veri bilgisinin işleniyor olduğunu açıkça belirtir mi? </li><li>Gizlilik Üzerinde Etki Değerlendirmelerini (PIA) düzenli olarak mı çalıştırıyorsunuz? </li><li> Kişisel bilgileri (Pİ) yönetmek için araç kullanıyor musunuz? </li><li> Herhangi bir bir kişide Pİ verilerini kullanarak iş yapmaya yasal yetkiniz var mı? Veriler için onayı izley var mı? </li><li> Denetim denetimlerini izleme, uygulama ve yönetme Veri sızıntılarını mı izleylisiniz? </li></ol>|
|Silme ve bildirim|<ol><li>Kullanıcıların verilerine nasıl erişilebilir olduğuyla ilgili açık yönergeler mi sunuyorsunuz? </li><li> Geri almayı iptal iznini işlemeye devam etmek için belgelenmiş işlemleriniz var mı? </li><li> Veriler için otomatik silme işleminiz mi var? </li><li> Bir müşteriyle cazip hale getirirken kimliği doğrulama işleminiz mi var? </li></ol>|
|Risk azaltma ve bilgi güvenliği|<ol><li>Yapılandırılmamış verileri taramak için araçlar kullanıyor musunuz? </li><li>Tüm sunucular güncel mi ve bunları korumak için güvenlik duvarı kullanıyor musunuz? </li><li>Sunucularınızı düzenli aralıklarla mı çalıştırıyorsunuz? </li><li>Veri sızıntılarını etkin olarak mı izleylisiniz? </li><li>İletim devam ettir yerinde ve iletimde verilerinizi şifreler misiniz? </li></ol>|
|İlke yönetimi|<ol><li>Bağlayıcı Şirket Kurallarınızı (BCR) nasıl yönetirsiniz? </li><li>Veriler için onayı izley var mı? </li><li> 1 ile 5 arasında bir ölçekte, 5'in tamamen kapsaması konusunda sözleşmeniz veri sınıflandırmalarını ve gereksinimlerini karşılar mı? </li><li>Bir olay yanıt planınız var ve düzenli olarak test ediyor musunuz? </li><li>Erişimi yönetmek için hangi ilkeyi kullanırsınız? </li></ol>|
|||

## <a name="step-3-identify-sensitive-information-types-that-occur-in-your-microsoft-365-environment"></a>3. Adım: Çalışma ortamınıza gelen hassas bilgi Microsoft 365 belirleme

Bu adım, belirli mevzuat denetimlerine tabi olan belirli hassas bilgi türlerinin tanımlanması ve bu tür bilgilerin ortamınıza Microsoft 365 içerir.

Kişisel içerik içeren ortamınıza içerik bulmak, önceden Uyumluluk Araması, eKbulma, Advanced eDiscovery, DLP ve denetim gibi içeriklerin bir bileşimini içeren formlara uygun bir görev olabilir.

Microsoft Uyumluluk yönetim  merkezinde yer alan yeni Veri Sınıflandırma çözümüyle, kişisel verilerle ilgili olanlar da dahil olmak [](../compliance/data-classification-content-explorer.md) üzere yerleşik veya özel hassas bilgi türleriyle çalışan İçerik Gezgini özelliği sayesinde bu özellik çok daha kolay hale geldi.

### <a name="sensitive-information-types"></a>Hassas bilgi türleri

Microsoft Uyumluluk yönetim merkezi, büyük bir çoğu kişisel verileri tanımlama ve bulma ile ilgili olarak 100'den fazla hassas bilgi türü önceden yüklenmiş olarak gelir. Bu yerleşik hassas bilgi türleri, normal ifade (regex) veya işlev tarafından tanımlanan desenlere bağlı olarak kredi kartı numaralarını, banka hesap numaralarını, pasaport numaralarını ve daha fazlasını tanımlamanıza ve korumanıza yardımcı olabilir. Daha fazla bilgi edinmek için [bkz. Hassas bilgi türleri nasıl görünüyor](../compliance/sensitive-information-type-entity-definitions.md)?

Çalışan kimlikleri için özel biçim veya yerleşik hassas bilgi türünde ele henüz kapsamış olmayan diğer kişisel bilgiler gibi, kuruluşa özgü veya bölgesel bir hassas öğe türünü tanımlamanız ve korumanız gerekirse, şu yöntemlerle özel bir hassas bilgi türü oluşturabilirsiniz:

- PowerShell
- Tam veri eşleşmesi olan özel kurallar (EDM)
- Uyumluluk Puanı ve Uyumluluk Yöneticisi'ni Kullanma makalesinde vurgulanan [Uyumluluk Merkezi yönetici arabirimi aracılığıyla](information-protection-deploy-compliance.md)

Ayrıca, var olan ve yerleşik hassas bilgi türünü özelleştirebilirsiniz.

Daha fazla bilgi için şu makalelere bakın:

- [Yerleşik hassas bilgi türünü özelleştirme](../compliance/customize-a-built-in-sensitive-information-type.md)
- [Hassas bilgi türleri hakkında bilgi](../compliance/sensitive-information-type-learn-about.md)
- [Güvenlik ve Uyumluluk Merkezi'nde özel ve hassas & oluşturma](../compliance/create-a-custom-sensitive-information-type.md)
- [Güvenlik ve Uyumluluk Merkezi PowerShell'de özel & bilgi türü oluşturma](../compliance/create-a-custom-sensitive-information-type-in-scc-powershell.md)
- [Tam Veri Eşleşmesi tabanlı sınıflandırmayla özel hassas bilgi türleri oluşturma](../compliance/create-custom-sensitive-information-types-with-exact-data-match-based-classification.md)

### <a name="content-explorer"></a>İçerik Gezgini

Ortamınıza hassas öğelerin tekrarını belirlemeye yardımcı olan önemli bir araç, Uyumluluk Yönetim Merkezi'nde bulunan yeni Microsoft 365 aracıdır.[](../compliance/data-classification-content-explorer.md) Bu, hassas bilgi türlerinin ortaya çıkmasını ve sonuçların  görüntülenmesini Microsoft 365 ve tüm Microsoft 365 tarama için otomatik bir araçtır.

Yeni İçerik Gezgini aracı, yerleşik hassas bilgi türlerini veya özel bilgileri kullanarak ortamınıza hassas öğelerin konumlarını hızla tanımlamanıza olanak sağlar. Bu, hassas öğelerin iletişim durumu ve konumunu düzenli olarak araştırmak üzere bir işlem ve sorumluluk atamayı içerir.

Bu makalede vurgulanan diğer adımların yanı sıra, bu genel risk maruz kalmak, hazırlık ve planlanan güvenlik yapılandırması ve izlemesi aracılığıyla hassas öğelerin konumunu belirlemek için bir Microsoft 365 sağlar.

### <a name="other-methods-to-identify-personal-data-in-your-environment"></a>Ortamınıza kişisel verileri tanımlamak için diğer yöntemler

Kuruluşlar, İçerik Gezgini'ne ek olarak, İçerik Arama özelliğine de sahiptir ve gelişmiş arama ölçütleri ve özel filtreler kullanarak kendi ortamında kişisel verileri bulmak için özel aramalar oluşturabilir.

Kişisel verileri bulmak için İçerik Arama'nın kullanımı hakkında ayrıntılı kılavuz bu makalede [sağlanmaktadır](/compliance/regulatory/gdpr). [GDPR ve CCPA için DSR'lerde İçerik Arama ve diğer keşif tekniklerini de incelemektedir](/compliance/regulatory/gdpr-dsr-Office365#introduction-to-dsrs).

Kişisel veriler için Microsoft 365 ve düzeltme teknikleri hakkında ek içgörüler izleme [ve yanıt makalesinde sağlanır](information-protection-deploy-monitor-respond.md).

> [!NOTE]
> Şirket içinde depolanan dosyalarda hangi hassas bilgileri bulmak için, lütfen [Azure Information Protection'a bakın](/azure/information-protection/quickstart-findsensitiveinfo).
