---
title: DLP ilkesi oluşturma, sınama ve ayarlama
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
audience: Admin
ms.topic: article
f1_keywords:
- ms.o365.cc.NewPolicyFromTemplate
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
search.appverid:
- MET150
ms.custom:
- seo-marvel-mar2020
ms.assetid: 59414438-99f5-488b-975c-5023f2254369
description: Bu makalede, bir DLP ilkesi oluşturma, test etmeyi ve kuruluş ihtiyaçlarına göre ayarlamayı öğrenirsiniz.
ms.openlocfilehash: cc31d067eaf2684c17a09d7b2731a5cc3500af76
ms.sourcegitcommit: 99067d5eb1fa7b094e7cdb1f7be65acaaa235a54
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2022
ms.locfileid: "63010056"
---
# <a name="create-test-and-tune-a-dlp-policy"></a>DLP ilkesi oluşturma, sınama ve ayarlama

Veri kaybını önleme (DLP), hassas bilgilerin yanlışlıkla veya yanlışlıkla paylaşımını önlemeye yardımcı olur.

DLP, kredi kartı numarası gibi hassas bilgiler için e-posta iletilerini ve dosyaları inceler. DLP kullanarak hassas bilgileri algılanabilir ve şu tür bir işlemden geçebilirsiniz:

- Denetimin amacına yönelik olarak olayı günlüğe günlüğe kayıtlama
- E-postayı gönderen veya dosyayı paylaşan son kullanıcıya uyarı görüntüleme
- E-posta veya dosya paylaşımının yer almalarını etkin bir şekilde engelleme

## <a name="permissions"></a>İzinler

DLP ilkeleri oluşturacak uyumluluk ekibimizin üyelerinin Uyumluluk Merkezi için izinleri olmalıdır. Varsayılan olarak, kiracı yöneticiniz uyumluluk görevlilerine ve diğer kullanıcılara erişim izni vetir. Şu adımları izleyin:
  
1. Grup içinde bir Microsoft 365 oluşturun ve uyumluluk yetkililerini ekleyin.
    
2. Güvenlik Uyumluluk Merkezi'nin **İzinler** sayfasında bir rol &amp; grubu oluşturun. 

3. Rol grubunu oluştururken, rol grubuna **aşağıdaki rolü eklemek** için Rolleri Seçin bölümünü kullanın: **DLP Uyumluluk Yönetimi**.
    
4. Daha önce **oluşturduğunuz** üye grubunu rol Microsoft 365 için Üye Seç bölümünü kullanın.

DLP **ilkelerinin ve DLP** raporlarının yalnızca görüntüleme ayrıcalıklarına sahip rol grubu oluşturmak için Yalnızca Görüntüleme DLP Uyumluluk Yönetimi rolünü kullanın.

Daha fazla bilgi için bkz[. Kullanıcılara Uyumluluk Merkezi'Office 365 erişme izni verme](../security/office-365-security/grant-access-to-the-security-and-compliance-center.md).
  
İlkeleri uygulamak için değil de DLP ilkesi oluşturmak ve uygulamak için bu izinler gereklidir.

### <a name="roles-and-role-groups-in-preview"></a>Önizlemede Roller ve Rol Grupları

Önizlemede, erişim denetimlerinize ince ayar yapmak için test etmek için deney erişiminiz olan roller ve rol grupları vardır.

İşte önizlemede olan Microsoft Bilgi Koruması (MIP) rollerinin listesi. Bu roller hakkında daha fazla bilgi edinmek [için Güvenlik ve Uyumluluk Merkezi'& bakın](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center)

- Bilgi Koruması Yöneticisi
- Bilgi Koruma Analisti
- Bilgi Koruma Koruma Koruma Koruması
- Bilgi Koruma Okuyucusu

Önizlemede olan MIP rol gruplarının listesi burada ve ve şekildedir. Daha fazla bilgi edinmek için [Güvenlik ve Uyumluluk Merkezi'nde rol & bakın](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#role-groups-in-the-security--compliance-center).

- Bilgi Koruması
- Bilgi Koruması Yöneticileri
- Bilgi Koruma Analistleri
- Bilgi Koruma Koruma KorumaLarı
- Bilgi Koruma Okuyucuları

## <a name="how-sensitive-information-is-detected-by-dlp"></a>DLP tarafından hassas bilgiler nasıl algılanır?

DLP, belirli anahtar sözcüklerin eşleşen desenlere yakınlığı gibi diğer göstergelerle birlikte, normal ifade (RegEx) desen eşleştirmesine göre hassas bilgileri bulur. Örneğin, VISA kredi kartı numarası 16 basamak içerir. Ancak, bu basamaklar 1111-1111-1111-1111, 1111 1111 1111 1111 veya daha fazla 1111111111111111.

Herhangi bir 16 basamaklı dizenin kredi kartı numarası olması gerekmez, yardım masası sisteminden bir bilet numarası veya bir donanım parçasının seri numarası olabilir. Bir kredi kartı numarasıyla zararsız 16 basamaklı dize arasındaki farkı anlatmak için, numaraların çeşitli kredi kartı markalarından bilinen bir desene eş olduğunu onaylamak üzere bir hesaplama (denetimli toplam) gerçekleştirilir.

DLP, kredi kartının son kullanma tarihi olabileceği yakın tarih değerleri olan "VISA" veya "AMEX" gibi anahtar sözcükler bulursa, DLP bu verileri dizenin bir kredi kartı numarası olup olmadığını karar vermek için de kullanır.

Başka bir deyişle, DLP bir e-postada şu iki metin dizeleri arasındaki farkı tanıyacak kadar akıllıdır:

- "Bana yeni bir dizüstü bilgisayar sipariş ettiysiniz. VISA numaramı 1111-1111-1111-1111, son kullanma tarihi 22/11/22 olarak kullanın ve tahmini teslim tarihini sahip oldu mu gönderin."
- "Dizüstü bilgisayar seri numaram 2222-2222-2222-2222 ve 11/2010 tarihinde satın alındı. Bu arada, seyahat nedenim yeni için onaylandı?"

Her [bilgi türünün nasıl algılandığından](sensitive-information-type-entity-definitions.md) bunu açıklayan Hassas bilgi türü varlık tanımları'ne bakın.

## <a name="where-to-start-with-data-loss-prevention"></a>Veri kaybını önleme ile başlama

Veri sızıntılarının riskleri tamamen belirgin olmadığı durumda, DLP'i uygulamaya başlarken tam olarak nerede başlamamız gerektiğini bulmak zordur. Neyse ki DLP ilkeleri "test modunda" çalıştırarak, bunları açmadan önce bunların etkisini ve doğruluğunu ölçebilirsiniz.

E-posta Exchange Online DLP ilkeleri Exchange yönetim merkezinden yönetilebilir. Ancak, Güvenlik ve Uyumluluk Merkezi aracılığıyla tüm iş yükleri & için DLP ilkelerini yapılandırabilirsiniz, dolayısıyla bu makaledeki gösterimlerde bunu kullanabilirsiniz. Güvenlik ve Uyumluluk &'nde, DLP ilkelerini Veri kaybı **önlemePolicy altında** >  **bulabilirsiniz**. başlamak **için İlke oluştur'a** seçin.

Microsoft 365, ilkeleri oluşturmak [için kullanabileceğiniz bir dizi DLP](what-the-dlp-policy-templates-include.md) ilkesi şablonu sağlar. Diyelim ki, Avustralyalı bir işletmesiniz. Avustralya'daki şablonları filtre seçebilir ve Finansal, Tıbbi ve Sağlık ve Gizlilik'i seçebilirsiniz.

![Ülke veya bölge seçme seçeneği.](../media/DLP-create-test-tune-choose-country.png)

Bu gösterim için, Avustralya Vergi Dosyası Numarası (TFN) ve Sürücü Lisans Numarası bilgi türlerini içeren Avustralyalı Kişisel Bilgileri (PII) Verileri'yi seçeceğim.

![İlke şablonu seçme seçeneği.](../media/DLP-create-test-tune-choose-policy-template.png)

Yeni DLP ilkenize bir ad verme. Varsayılan ad DLP ilkesi şablonuyla eş değere sahip olur, ancak aynı şablondan birden çok ilke oluşturula bile, size ait daha açıklayıcı bir ad seçmelisiniz.

![İlkenizi isim seçeneği.](../media/DLP-create-test-tune-name-policy.png)

İlkenin uygulanacak konumlarını seçin. DLP ilkeleri Exchange Online, SharePoint Online ve OneDrive İş. Bu ilkeyi tüm konumlara uygulanacak şekilde yapılandırılmış bırakılacak.

![Tüm konumları seçme seçeneği.](../media/DLP-create-test-tune-choose-locations.png)

İlk İlke **Ayarlar** şimdilik varsayılanları kabul edin. DLP ilkelerini özelleştirebilirsiniz, ancak varsayılanlar iyi bir başlangıçtır.

![Korunması gereken içerik türünü özelleştirme seçenekleri.](../media/DLP-create-test-tune-default-customization-settings.png)

Sonraki'ye tık olduktan sonra** size daha fazla **özelleştirme seçeneği Ayarlar** ilke sayfası görüntülenir. Yalnızca test etmekte olduğunuz bir ilke için, burada bazı ayarlamalar yapmaya başlayabilirsiniz.

- Şimdilik ilke ipuçlarını devre dışıdim, bu, yalnızca test ediyor ve kullanıcılara henüz hiçbir şey göstermek istemiyorsanız atacak makul bir adımdır. İlke ipuçları, kullanıcılara DLP politikasını ihlal etmek hakkında uyarılar görüntüler. Örneğin, Outlook bir kullanıcı ekli olduğu dosyanın kredi kartı numaraları içerdiğine ve e-postanın reddedilmesine neden olacağını içeren bir uyarı alır. İlke ipuçlarının amacı, uyumlu olmayan davranışı olmadan önce durdurmaktır.
- Ayrıca, örnek sayısını da 10'dan 1'e azalttırarak, bu ilkenin verilerin yalnızca toplu paylaşımını değil Avustralya PII verilerinden herhangi bir paylaşımını algılaytır.
- Ayrıca olay raporu e-postasına başka bir alıcı ekledim.

![Ek ilke ayarları.](../media/DLP-create-test-tune-more-policy-settings.png)

Son olarak, bu ilkeyi başlangıçta test modunda çalıştıracak şekilde yapılandırdım. Test modundayken ilke ipuçlarını devre dışı bırakma seçeneği de vardır. Bu size, ilke ipuçlarının ilkede etkinleştirilmesi için esneklik sağlar, ancak sonra testniz sırasında ipuçlarının göster mi, yoksa gizleme mi olduğuna karar verir.

![İlkeyi test etmek için seçenek.](../media/DLP-create-test-tune-test-mode.png)

İlkeyi oluşturmayı bitirmek için son gözden **geçirme ekranında** Oluştur'a tıklayın.

## <a name="test-a-dlp-policy"></a>DLP ilkesi sınama

Normal kullanıcı etkinliği tarafından ilkenin tetiklenirken beklemeniz veya ilkeyi kendi tetiklersiniz. Daha önce size DLP [eşleşmelerini tetikleme](sensitive-information-type-entity-definitions.md) hakkında bilgi sağlayan Hassas bilgi türü varlık tanımlarına bağlanmıştım.

Örnek olarak, bu makale için oluşturduğum DLP ilkesi Avustralya vergi dosyası numaralarını (TFN) algılar. Belgeye göre, eşleşmede aşağıdaki ölçütler temel alınlanmıştır.

![Avustralya Vergi Dosyası Numarası Belgeleri.](../media/DLP-create-test-tune-Australia-Tax-File-Number-doc.png)
 
TFN algılamayı tercihen bir şekilde göstermek için, "Vergi dosyası numarası" sözcüklerinin yer aldığı bir e-posta ve yakın yakınlıkta dokuz basamaklı bir dize hiçbir sorun olmadan tekneyle binecek. DLP ilkesine tetik uygulamanın nedeni, dokuz basamaklı dizenin, yalnızca zararsız bir sayı dizesi değil, geçerli bir TFN olduğunu belirten denetimler numarasını geçmesidir.

![Denetim toplamlarını geçemediklerinden Avustralya vergi dosyası numarası.](../media/DLP-create-test-tune-email-test1.png)

Buna göre, "Vergi dosyası numarası" sözcüklerini içeren bir e-posta ve denetim toplamtan geçen geçerli bir TFN ilkeyi tetikler. Buradaki kayıt için, kullanmakta olduğumun TFN'si geçerli ama orijinal olmayan bir TFN'ler üreten bir web sitesinden alındı. Bir DLP ilkesi test etme sırasında en yaygın hatalardan biri geçersiz sahte bir numara kullanmak ve denetim toplamlarını geçememek olduğundan (dolayısıyla ilkeyi tetiklemeyeceği için) bu tür siteler yararlı olur.

![Denetim toplamlarını geçen Avustralya vergi dosyası numarası.](../media/DLP-create-test-tune-email-test2.png)

Olay raporu e-postası, algılanan hassas bilgilerin türünü, kaç örneğin algılandığından ve algılamanın güven düzeyini içerir.

![Algılanan vergi dosyası numarasını gösteren olay raporu.](../media/DLP-create-test-tune-email-incident-report.png)

DLP ilkenizi test modunda bırakır ve olay raporu e-postalarını analiz ederseniz, DLP politikasının doğruluğu ve zorunlu tutularak ne kadar etkili olacağını almaya başlayabilirsiniz. Olay raporlarına ek olarak, kiracınız genelinde ilke eşleşmelerinin toplanmış bir görünümünü görmek için [DLP](view-the-dlp-reports.md) raporlarını da kullanabilirsiniz.

## <a name="tune-a-dlp-policy"></a>DLP ilkesi ayarlama

İlke isabetlerini çözümlerken, ilkelerin nasıl davranacağını görmek için bazı ayarlamalar yapmak iyi olabilir. Basit bir örnek olarak, e-postada bir TFN'nin sorun olmadığını düşünebilirsiniz (yine de olduğunu düşünüyoruz ama bunu gösterim amaçlı olarak düşünebilirsiniz), ancak iki veya daha fazla örnek sorun olabilir. Birden çok örnek, İk veritabanından bir dış taraflara (örneğin, dış muhasebe hizmeti) CSV dışarı aktarma e-postası gönderen bir çalışan gibi riskli bir senaryo olabilir. Kesinlikle algılamayı ve engellemeyi tercih edersiniz.

Uyumluluk Merkezi'nde davranışı düzenlemek için var olan bir ilkeyi düzenleyebilirsiniz.

![İlkeyi düzenleme seçeneği.](../media/DLP-create-test-tune-edit-policy.png)
 
Konum ayarlarını, ilkenin yalnızca belirli iş yüklerine ya da belirli sitelere ve hesaplara uygulanması için ayarlayabilirsiniz.

![Belirli konumları seçme seçenekleri.](../media/DLP-create-test-tune-edit-locations.png)

Ayrıca, ilke ayarlarını değiştirebilir ve kuralları ihtiyaçlarınıza daha uygun olacak şekilde düzenleyebilirsiniz.

![Kuralı düzenleme seçeneği.](../media/DLP-create-test-tune-edit-rule.png)

DLP ilkesi içinde bir kuralı düzenlerken şunları değiştirebilirsiniz:

- Kuralı tetikleyen hassas verilerin türü ve örnekleri de dahil olmak üzere koşullar.
- İçeriğin erişimini kısıtlama gibi 2007'ye kadar olan eylemler.
- Kullanıcıya e-posta istemcisinde veya web tarayıcısında görüntülenen ilke ipuçları olan kullanıcı bildirimleri.
- Kullanıcı geçersiz kılmalar, kullanıcıların yine de e-postalarıyla veya dosya paylaşımıyla devam edip e-postayla devam edip e-posta
- Yöneticilere bildirmek için olay raporları.

![Kuralın bölümlerini düzenleme seçenekleri.](../media/DLP-create-test-tune-editing-options.png)

Bu gösterim için, ilkeye kullanıcı bildirimleri ekledim (yeterli kullanıcı farkındalığı eğitimi olmadan bunu yaparken dikkatli olun) ve kullanıcıların ilkeyi işletme gerekçelendirmesi ile veya yanlış pozitif olarak ekleriyle geçersiz kilmesine izin verdim. Ayrıca, e-posta ve ilke ipucu metnini özelleştirebileceğiniz gibi, kurum ilkeleri hakkında ek bilgiler eklemek veya kullanıcılardan sorularınız varsa de destekle iletişim kurmalarını istenebilirsiniz.

![Kullanıcı bildirimleri ve geçersiz kılma seçenekleri.](../media/DLP-create-test-tune-user-notifications.png)

İlke, yüksek ve düşük hacimleri işlemeye için iki kural içerir, bu nedenle her ikisini de istediğiniz eylemlerle düzenlemeye emin olun. Bu, davaları özelliklerine bağlı olarak farklı bir şekilde değerlendiren bir fırsattır. Örneğin, düşük hacim ihlalleri için geçersiz kılmalara izin verse de yüksek hacim ihlalleri için geçersiz kılmalara izin vermezsiniz.

![Yüksek hacim için bir kural ve düşük hacim için bir kural.](../media/DLP-create-test-tune-two-rules.png)

Ayrıca, aslında ilke ihlali olan içeriği engellemek veya kısıtlamak için kural üzerinde bir eylem yapılandırmak da gerekir.

![içeriğe erişimi kısıtlama seçeneği.](../media/DLP-create-test-tune-restrict-access-action.png)

Bu değişiklikleri ilke ayarlarına kaydeddikten sonra, aynı zamanda ilkenin ana ayarlar sayfasına dönüp ilke test modundayken kullanıcılara ilke ipuçlarını gösterme seçeneğini etkinleştirmem gerekir. Bu, DLP ilkelerini son kullanıcılarınıza tanıtmanın ve verimliliklerini etkileyen hatalı pozitif sonuçlardan çok fazla risk almadan kullanıcı farkındalığı eğitimi yapmanın etkili bir yoludur.

![Test modunda ilke ipuçlarını gösterme seçeneği.](../media/DLP-create-test-tune-show-policy-tips.png)

Sunucu tarafında (veya tercih ederseniz bulut tarafında), çeşitli işlem aralıkları nedeniyle bu değişiklik hemen etkili olamayabilirsiniz. Bir kullanıcıya yeni ilke ipuçları görüntüecek bir DLP ilkesi değişikliği yapıyorsanız, kullanıcı değişiklikleri hemen Outlook istemcisinde görebilir ve bu değişiklik 24 saatte bir ilke değişikliklerini denetler. Işleri test etmek üzere hızlandırmak için, bu kayıt defteri düzeltmesini kullanarak PolicyNudges anahtarından son indirme zaman [damgasını temiz devre dışı indirebilirsiniz](https://support.microsoft.com/en-au/help/2823261/changes-to-a-data-loss-prevention-policy-don-t-take-effect-in-outlook?__hstc=18650278.46377037dc0a82baa8a30f0ef07a7b2f.1538687978676.1538693509953.1540315763430.3&__hssc=18650278.1.1540315763430&__hsfp=3446956451). Outlook sonra yeniden başlatacak ve e-posta iletisi oluşturmaya başlanacak en son ilke bilgilerini indirir.

İlke ipuçlarını etkinleştirdiysek, kullanıcı ipuçlarında bu ipuçlarını Outlook ve oluştuğunda hatalı pozitif sonuçlar bildirebilirsiniz.

![Hatalı pozitif sonuç bildirme seçeneğinin yer olduğu ilke ipucu.](../media/DLP-create-test-tune-policy-tip-in-outlook.png)

## <a name="investigate-false-positives"></a>Hatalı pozitif pozitifleri araştırma

DLP ilkesi şablonları hemen her durumda mükemmel değildir. Ortamınıza hatalı pozitif sonuçlar geliyor olabilir. İşte bu nedenle, DLP dağıtımına kolay bir şekilde gidip, yeterli test yapmak ve ilkelerinizi ayarlamak zaman almak çok önemlidir.

Burada, hatalı pozitif sonuç örneği ve bir örneği ve bir örnek veser. Bu e-posta zararsızdır. Kullanıcı, birine cep telefonu numarasını ve e-posta imzasını da sağlıyor.

![Hatalı pozitif bilgilerin gösteren e-posta.](../media/DLP-create-test-tune-false-positive-email.png)
 
Ancak kullanıcı, e-postada özellikle Avustralyalı sürücünün lisans numarası olmak üzere hassas bilgiler olduğu konusunda bir ilke ipucu görür.

![İlke ipucunda hatalı pozitifi bildirme seçeneği.](../media/DLP-create-test-tune-policy-tip-closeup.png)

Kullanıcı hatalı pozitif pozitifi bildirebilirsiniz ve yönetici bunun neden ortaya çıktıine bakarak bakabilirsiniz. Olay raporu e-postası içinde, e-posta hatalı pozitif olarak işaretlenir.

![Hatalı pozitif sonuç gösteren olay raporu.](../media/DLP-create-test-tune-false-positive-incident-report.png)

Bu sürücünün lisans durumu, incelemeniz için iyi bir örnektir. Bu hatalı pozitif değerin ortaya çıkma nedeni, "Avustralya Sürücü Lisansı" türünün 300 karakterlik "Sydney nsw" anahtar sözcüklerine yakınlığı içinde 9 basamaklı herhangi bir dize (10 basamaklı bir dizenin parçası olan bir dize bile) tarafından tetiklenir (büyük/küçük harfe duyarlı değildir). Bu durum, kullanıcının Sidney'de olması nedeniyle telefon numarası ve e-posta imzası tarafından tetiklenir.


Seçeneklerden biri, Avustralyalı sürücünün lisans bilgi türünü ilkeden kaldırmaktır. DLP ilke şablonunun bir parçası olduğu için buradadır, ancak bu şablonu kullanmak zorunda değilim. Yalnızca Vergi Dosyası Numaraları ile ilgileniyorsanız ve sürücü lisansları ilginizi çekmiyorsa, bunu kaldırabilirsiniz. Örneğin, ilkede bunu düşük hacimli kuraldan kaldırabilir, ancak bunu yüksek hacimli kuralda bırakarak birden çok sürücü lisansının listelerinin yine algılandığından emin olabilir.
 
Bir diğer seçenek de örnek sayısını artırmak, böylelikle yalnızca birden çok örnek olduğunda düşük sürücü lisansları algılanır.

![Örnek sayısını düzenleme seçeneği.](../media/DLP-create-test-tune-edit-instance-count.png)

Örnek sayısını değiştirmenin yanı sıra, eşleşmenin doğruluğunu (veya güven düzeyini) de ayarlayabilirsiniz. Hassas bilgi türünüz birden çok desene sahipse, kuralınız yalnızca belirli desenlere uygun olacak şekilde, kuralda eşleşmenin doğruluğunu ayarlayabilirsiniz. Örneğin, hatalı pozitif sonuçları azaltmaya yardımcı olması için kuralınıza, yalnızca en yüksek güven düzeyine sahip desenle eşleşmesi için, kurala uygun olan eşleşme doğruluğunu ayarlayın. Güven düzeyleri hakkında daha fazla bilgi için bkz [. Kurallarınızı ayarlamak için güven düzeyini kullanma](data-loss-prevention-policies.md#match-accuracy).

Son olarak, biraz daha ileri düzeye gitmek için hassas bilgi türlerinden herhangi birini özelleştirebilirsiniz. Örneğin, yukarıda tetiklenen hatalı pozitif sonuç ortadan kaldırmak için Avustralya sürücüsünün lisans numarasına ilişkin anahtar sözcükler [](sensitive-information-type-entity-definitions.md#australia-drivers-license-number)listesinden "Sydney NSW"yi kaldırabilirsiniz. XML ve PowerShell kullanarak bunu yapmayı öğrenmek için bkz. [Yerleşik duyarlı bilgi türünü özelleştirme](customize-a-built-in-sensitive-information-type.md).

## <a name="turn-on-a-dlp-policy"></a>DLP ilkesi açma

DLP ilkenizin hassas bilgi türlerini doğru ve etkili bir şekilde algılasın ve son kullanıcılarının geçerli olan ilkelerle başa çıkmaya hazır olmasını sağlamaktan memnun olursanız, ilkeyi etkinleştirebilirsiniz.

![İlkeyi açma seçeneği.](../media/DLP-create-test-tune-turn-on-policy.png)
 
İlkenin ne zaman yürürlüğe gireceklerini bekliyorsanız, Güvenlik Bağlan Uyumluluk Merkezi [PowerShell'e &](/powershell/exchange/connect-to-scc-powershell) DistributionStatus'u görmek için [Get-DlpCompliancePolicy cmdlet'ini](/powershell/module/exchange/get-dlpcompliancepolicy) çalıştırın.

 ```powershell
 Get-DlpCompliancePolicy "Testing -Australia PII" -DistributionDetail | Select distributionstatus
 ```
DLP ilkesine başladıktan sonra, beklenen ilke eylemlerinin gerçekleştir olduğundan emin olmak için kendi bazı son testlerinizi çalıştırabilirsiniz. Kredi kartı verileri gibi şeyleri test etmeye çalışıyorsanız, çevrimiçi olarak örnek kredi kartı veya diğer kişisel bilgilerin nasıl oluşturuleceği ve kimlik denetimlerini geçecek ve ilkelerinizi tetikleyecek bilgilerle birlikte web siteleri vardır.

Kullanıcı geçersiz kılmalarına izin verecek ilkeler, bu seçeneği ilke ipucu kapsamında kullanıcıya sunacak.

![Kullanıcının geçersiz kılmaya izin veren ilke ipucu.](../media/DLP-create-test-tune-override-option.png)

İçeriği kısıtlayan ilkeler, uyarıyı ilke ipucu kapsamında kullanıcıya sunacak ve kullanıcının e-posta göndermesini önler.

![İçeriğin kısıtlanmış olduğu ilke ipucu.](../media/DLP-create-test-tune-restrict-warning.png)

## <a name="summary"></a>Özet

Veri kaybı önleme ilkeleri, tüm türlerde olan kuruluşlar için kullanışlıdır. İlke ipuçları, son kullanıcı geçersiz kılmalar ve olay raporları gibi üzerinde denetimiz olması nedeniyle, bazı DLP ilkelerini test etmek düşük riskli bir uygulamadır. Bazı DLP ilkelerini, zaten kuruluşta ne tür ihlaller olduğunu görmek için sessiz bir şekilde sınayabilirsiniz ve ardından düşük pozitif oranların olduğu ilkeler hazırlar, kullanıcılarınızı izin verilenler ve izin verilmiyor konusunda eğitin ve sonra DLP ilkelerinizi kuruluşa yazın.
