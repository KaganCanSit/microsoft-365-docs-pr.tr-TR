---
title: Veri kaybını önlemeyi planlama
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: conceptual
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
search.appverid:
- MET150
description: Veri kaybını önleme planlama sürecine genel bakış
ms.openlocfilehash: c695a6a2a4bd21a147e5e81bc73fb65ab1378960
ms.sourcegitcommit: 1ef176c79a0e6dbb51834fe30807409d4e94847c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/19/2021
ms.locfileid: "63005462"
---
# <a name="plan-for-data-loss-prevention-dlp"></a>Veri kaybı önleme (DLP) planı

Her kuruluşun iş ihtiyaçları, hedefleri, kaynakları ve durumu benzersiz olduğundan her kuruluş veri kaybı önleme (DLP) önlemeyi (DLP) farklı şekilde planlar ve uygulayamaz. Bununla birlikte, tüm başarılı DLP uygulamaları için ortak olan öğeler vardır. Bu makalede, kuruluşların DLP planlamalarında kullandığı en iyi yöntemler yer almaktadır.

## <a name="multiple-starting-points"></a>Birden çok başlangıç noktası

Birçok kuruluş, çeşitli devlet veya endüstri düzenlemelerine uyumlu olmak için DLP'yi uygulamaya karar verdi. Örneğin, Avrupa Birliği Genel Veri Koruma Yönetmeliği (GDPR) veya Sağlık Sigortası Taşınabilirlik ve Sorumluluk Yasası (HIPAA) veya California Tüketici Gizliliği Yasası (CCPA). Ayrıca, fikri mülkiyetlerini korumak için veri kaybını önlemeyi de hayata geçirmektedirler. Ama DLP yolculuğunun başlangıç noktası ve üst düzey hedefi farklılık gösterir. 

Kuruluşlar DLP yolculuğuna başlayabilir:

- gibi platform odaklarından, Sohbet ve Kanal iletileri Teams cihazlarda bilgileri korumak Windows 10.
- korumayı önceliklendirmek istediğiniz hassas bilgileri (sağlık hizmetleri kayıtları gibi) bilmek ve doğrudan koruma için ilkeler tanımlamaya gitmek
- hassas bilgilerini bilmeden ne olduğunu, nerede olduğunu ve kimlerle birlikte ne yaptığını bilmeden keşif ve kategoriyle çalışmaya başlar ve daha yöntemleri bir yaklaşım benimserler
- hassas bilgilerini ne olduğunu, nerede olduğunu veya bu bilgilerle ne yaptığını bilmeden, doğrudan ilkeler tanımlamaya ve bu sonuçları başlangıç noktası olarak kullanmaya ve sonra buradan ilkelerini geliştirmeye doğru hareket eder
- Bilgi Koruma yığınının tamamını uygulamaları Microsoft 365 ve bu nedenle daha uzun vadeli, yöntemsel bir yaklaşım benimserler

Bunlar, müşterilerin DLP'ye nasıl yaklaştığına ve nereden başlayacağının önemi yoktur; Microsoft 365 DLP, baştan tamamıyla gerçekleştirilen veri kaybı önleme stratejisinde çeşitli bilgi koruma seyahatlerine uyum sağlayacak kadar esnektir. 

## <a name="overview-of-planning-process"></a>Planlama sürecine genel bakış

Veri [kaybı önleme hakkında bilgi edinmek](dlp-learn-about-dlp.md#learn-about-data-loss-prevention) , [DLP planlama sürecinin üç farklı yönüne ortaya konur](dlp-learn-about-dlp.md#plan-for-dlp). Burada, tüm DLP planlarında ortak olan öğeler hakkında daha fazla ayrıntıya giracağız.

### <a name="identify-stakeholders"></a>Paydaşları tanımlama

Uygulama uygulandığında DLP ilkeleri, kuruluşun büyük bölümlerine uygulanabilir. IT, negatif sonuçlar olmadan kendi başına geniş bir plan geliştirebilir. Şunları kimlerin etkiley proje katılımcılarını tanımlamalı:

- düzenlemelerini, yasaları ve endüstri standartlarıyla ilgili olarak
- korunacak hassas öğe kategorileri
- kullanılan iş süreçleri
- sınırlı olması gereken riskli davranış
- öncelikle hangi verilerin korunması gerektiğini, ilgili öğelerin duyarlılığına ve risklere göre önceliklerini belirleme
- DLP ilkesi, olay inceleme ve düzeltme işlemiyle eşleşme ana hatlarıyla açık 
 
Genelde bu ihtiyaçların %85'i mevzuat ve uyumluluk koruması, %15'i fikri mülkiyet koruması olmaktır. planlama sürecinize dahil olacak roller hakkında bazı öneriler şunlardır:

- Mevzuat ve uyumluluk yetkililerini
- Baş risk görevlisi
- Hukuk görevlileri
- Güvenlik ve uyumluluk görevlileri
- Veri öğelerinin işletme sahipleri
- Kurumsal kullanıcılar
- IT

### <a name="describe-the-categories-of-sensitive-information-to-protect"></a>Korunması için hassas bilgi kategorilerini açıkla

Bundan sonra paydaşlar, korunması gereken hassas bilgi kategorilerini ve bunların kullanılmaları gereken iş sürecini açıklar. Örneğin, Microsoft 365 DLP şu kategorileri tanımlar:

- Finansal 
- Sağlık ve sağlık bilgileri
- Gizlilik
- Özel

Paydaşlar hassas bilgileri "Bir veri işlemcisiyiz, bu nedenle veri konusu bilgilerine ve finansal bilgilere gizlilik korumaları uygulamamız gerekir" olarak tanımlayabilir.

 
  <!-- The business process is important as it informs the ‘data at rest’, ‘data in transit’, ‘data in use’ aspect of DLP planning and who should be sharing the items and who should not.-->

### <a name="set-goals-and-strategy"></a>Hedef ve strateji ayarlama

Paydaşlarınızı belirlediktan ve hangi hassas bilgilerin korunması gerektiğini ve bunun nerede kullan gerektiğini biliyorken, paydaşlar koruma hedeflerini belirlediklerinden ve bir uygulama planı geliştirebilirler. 


 <!--
### Discovery
 for the locations (DLP workloads) of these types of items.  (mapping DLP locations and data at rest, data in transit, data in use)

### IT can start coding test policies
start small and always in test mode. Note that DLP policies can feed into insider risk.

### Business process owners help with tuning
 false positive/false negative results and fitting DLP into their business processes.

-->

### <a name="set-implementation-plan"></a>Uygulama planını ayarlama

Uygulama planınız şunları içerebilir:

- Başlangıç durumunuzla istenen bitiş durumunu eşleme ve birden diğerini eşleştirme
- hassas öğeleri bulma konusunda nasıl adrese sahip olayabilirsiniz
- ilke planlama ve uygulanacakları düzen
- önkoşulları nasıl karşılayabilirsiniz?
- zorlamaya başlamadan önce ilkelerin nasıl test edileceklerini planlama
- son kullanıcılarınızı nasıl eğiteceksiniz
- ilkelerinizi nasıl test edin ve ayar edin
- düzenleme, yasal, endüstri standardı veya fikri mülkiyet koruma ve iş ihtiyaçlarına dayalı olarak veri kaybı önleme stratejinizi nasıl gözden geçirer ve güncelleştirebilirsiniz

#### <a name="map-out-path-from-start-to-desired-end-state"></a>Baştan istenen bitiş durumuna eşleme yolu

Katılımcılarla iletişim kurmak ve proje kapsamının ayarını yapmak için, kuruluşlarının başlangıç durumunun istenen son durumuna nasıl ulaşacaklarını belgeleyebilirsiniz. DLP'nin dağıtımında yaygın olarak kullanılan adımlardan bir dizisini burada veserlerde edinebilirsiniz. Daha fazla ayrıntıya sahip olmak istiyor, ancak bunu kullanarak DLP benimseme yollarınızı çerçevelendirebilirsiniz.

![DLP'nin dağıtımında yaygın sırayı gösteren grafik.](../media/dlp-deployment-planning.png)

#### <a name="sensitive-item-discovery"></a>Hassas öğe bulma

Tek tek hassas öğelerin ne olduğunu ve nerede olduklarını bulmanın çeşitli yolları vardır. Daha önce duyarlılık etiketleri dağıtmış veya yalnızca öğeleri bulan ve denetleen tüm konumlara geniş bir DLP ilkesi dağıtmaya karar vermiş olabilirsiniz. Daha fazla bilgi edinmek için bkz [. Verilerinizi bilebilirsiniz](information-protection.md#know-your-data).

#### <a name="policy-planning"></a>İlke planlama

DLP benimsemeye başlayana kadar, bu soruları kullanarak ilke tasarımınıza ve uygulama çabalarınıza odaklanın.

##### <a name="what-laws-regulations-and-industry-standards-must-your-organization-comply-with"></a>Düzenlemenizin hangi yasalara, düzenlemelere ve endüstri standartlarıyla uyumlu olması gerekir?

Birçok kuruluş yasal düzenlemelere uyum amacı ile DLP'ye geldi olduğundan, bu soruyu yanıtlamaK DLP uygulamanızı planlamak için doğal bir başlangıç noktasıdır. Ancak, IT uygulaması olarak büyük olasılıkla yanıt verecek konumda olmazsiniz. Bunu hukuk ekibinin ve işletme yöneticilerinin yanıtlaması gerekir. 
 
**Örnek** Organizasyonunız İngiltere'ye tabidir. yasal düzenlemelere tabidir.


##### <a name="what-sensitive-items-does-your-organization-have-that-must-be-protected-from-leakage"></a>Bu kuruluşta, sızıntıya karşı korunması gereken hangi hassas öğeler var?

Düzenleme uyumluluğu ihtiyaçları açısından kurum bu öğenin nereyi ifade ediyor olduğunu bir kez bilir, hangi hassas öğelerin sızıntıya karşı korunması gerektiğini ve bunları korumak için ilke uygulamanın önceliklerini nasıl belirlemek istediğiniz konusunda bir fikir edinebilirsiniz. Bu, en uygun DLP ilkesi şablonlarını seçmenize yardımcı olur. Microsoft 365, Finansal, Tıbbi ve sağlık, Gizlilik için önceden yapılandırılmış DLP şablonlarıyla birlikte gelir ve Özel şablonunu kullanarak kendi şablonlarınızı oluşturabilirsiniz. Gerçek DLP ilkelerinizi tasarlar ve oluşturdukken, bu sorunun yanıtlarını bilmek doğru hassas bilgi türünü seçmenize de [yardımcı olur](sensitive-information-type-learn-about.md#learn-about-sensitive-information-types).

**Örnek** Hızlı bir şekilde çalışmaya başlamak için`U.K. Financial Data`, ' ve hassas bilgi türlerini içeren `Credit Card Number``EU Debit Card Number`ilke şablonunu `SWIFT Code` seçersiniz. 

##### <a name="where-are-the-sensitive-items-and-what-business-processes-are-they-involved-in"></a>Hassas öğeler nerede ve hangi iş süreçlerine dahil?

Kuruluş hassas bilgileri içeren öğeler, iş yapma kursunda her gün kullanılır. Bu hassas bilgi örneklerinin nerede ortaya çıkar olduğunu ve bunların hangi iş süreçleri için kullanıla olduğunu bilmek gerekir. Bu, DLP ilkelerinizi uygulamak için doğru konumları seçmenize yardımcı olur. Microsoft 365 DLP ilkeleri konumlara uygulanır:

- Exchange-posta gönderme
- SharePoint siteleri
- OneDrive hesapları
- Teams ve kanal iletilerini gönderme
- Windows 10 Cihazları
- Bulut Uygulamaları için Microsoft Defender
- Şirket içi depolar

**Örnek** Kuruluş iç denetçileri bir dizi kredi kartı numarası izliyor. Bu sitenin güvenli bir çalışma SharePoint tutmaları gerekir. Çalışanlardan birkaçı kopya kopyalar ve bunları kendi OneDrive İş kendi cihazlarında eşitlenen iş Windows 10 kaydedin. Bunlardan biri, 14'ü listenin bir listesini e-postaya yapıştırarak gözden geçirme için dış denetçilere göndermeye çalışır. İlkeyi güvenli SharePoint sitesine, tüm iç denetçiler OneDrive İş hesaplarına, Windows 10 cihazlarına ve Exchange uygulamak Exchange gerekir.

##### <a name="what-is-your-organizations-tolerance-for-leakage"></a>Kuruluşlarınız sızıntının dayanıklılığı nedir?

Nelerin kabul edilebilir bir hassas ürün sızıntı düzeyi olduğu ve nelerin olmadığının farklı görünümleri kuruluşta farklı gruplarda olabilir. İşletmenin sıfır sızıntısını önlemek çok yüksek bir maliyetle ortaya gelebilir.

**Örnek** Hem kuruluş kuruluşlarının güvenlik grubu hem de hukuk ekibi, kredi kartı numaralarının kuruluş dışındaki herkesle paylaşılamamalıdır ve sıfır sağıyla birlikte bulunabilir. Ancak, kredi kartı numarası etkinliğinin normal gözden geçirmesi kapsamında, iç denetçilerin bazı kredi kartı numaralarını üçüncü taraf denetçilerle paylaşması gerekir. DLP ilkeniz kuruluş dışında kredi kartı numaralarının tüm paylaşımını yasaklasa, iç denetçilerin izlemesini tamamlamasına yardımcı olacak kesintileri azaltmak için önemli bir iş sürecinde kesintiler yaşanacak ve ek maliyet eklenecektir. Bu ek maliyet, yönetim liderleri açısından kabul edilemez. Bu sorunu çözmek için, kabul edilebilir bir sızıntı düzeyine karar vermek için dahili bir görüşme yapılması gerekir. Bu karar verildiklerinde, ilke belirli kişilerin bilgileri paylaşması için özel durumlar sağlar veya yalnızca denetim modunda uygulanabilir.

#### <a name="planning-for-prerequisites"></a>Önkoşulları planlama

Bazı DLP konumlarını izlemeden önce karşı izlenmesi gereken önkoşullar vardır. Şu **bölümlerin Başlamadan önce bölümlerine** bakın:

- [Şirket içi tarayıcıda (önizleme) veri kaybı önleme özelliğiyle çalışmaya başlama](dlp-on-premises-scanner-get-started.md#before-you-begin)
- [Uç nokta veri kaybını önlemeye başlama](endpoint-dlp-getting-started.md#before-you-begin)
- [Microsoft uyumluluk uzantısıyla (önizleme) çalışmaya başlama](dlp-chrome-get-started.md#before-you-begin)
- [Microsoft dışı bulut uygulamaları için veri kaybı önleme ilkelerini kullanma (önizleme)](dlp-use-policies-non-microsoft-cloud-apps.md#before-you-begin)

#### <a name="policy-deployment"></a>İlke dağıtımı

DLP ilkelerinizi  oluşturmadan önce, bunların etkisini değerlendirmek ve bunların etkisini test etmek için bunları aşamalı olarak kademeli olarak değerlendirmeniz gerekir. Örneğin, binlerce belgeye erişimi istemeden engellemek veya mevcut bir iş sürecini bozmak için yeni bir DLP ilkesi istemiyorsunuz.
  
Olası etkisi büyük olan DLP ilkeleri oluşturuyorsanız, bu diziyi takip öneririz:
  
1. **İlke Raporu olmadan test İpuçları** ve ardından etkisini değerlendirmek için DLP raporlarını ve herhangi bir olay raporlarını kullanın. DLP raporlarını kullanarak ilke eşleşmelerinin sayısını, konumunu, türünü ve önem derecesine bakabilirsiniz. Sonuçlara bağlı olarak, ilkelerin ince ayarını yapmak için gereken ayarlamaları da yapmak gerekir. Test modunda DLP ilkeleri, kuruluşta çalışan kişilerin üretkenliğini etkilemez. Ayrıca, bu aşamayı, DLP olay incelemesi ve sorun düzeltmesi için iş akışınızı test etmek için kullanın.
    
2. **Kullanıcılara uyumluluk ilkelerinizi** öğretecek ve uygulanacak ilkeler için hazırlayacak şekilde İpuçları ilkeler ve bildirimler ve İlkeler ile Test moduna geçersiniz. İlke ipucunda ilke hakkında daha fazla ayrıntı sağlayan bir kuruluş ilkesi sayfasının bağlantısına sahip olmak yararlı olur. Bu aşamada, ilkeleri daha da geliştirmek için kullanıcılardan hatalı pozitif sonuçları bildirmelerini de sorabilirsiniz. İlke uygulamasının sonuçlarının, proje katılımcılarının sahip olduğu sonuçlarla eşekli olduğunu doğru bir kez daha ifade ederseniz bu aşamaya geçebilirsiniz. 
    
3. **Kurallarda eylemlerin uygulanması** ve içeriğin korunması için ilkeler üzerinde tam zorlamaya başlayabilirsiniz. Sonuçların sizin için uygun olduğundan emin olmak için DLP raporlarını ve tüm olay raporlarını veya bildirimlerini izlemeye devam edin. 

    ![Test modunu kullanma ve ilkeyi açma seçenekleri.](../media/49fafaac-c6cb-41de-99c4-c43c3e380c3a.png)

    DLP ilkesini, herhangi bir zamanda kapatabilirsiniz ve bu da ilkenin tüm kurallarını etkiler. Bununla birlikte, kural düzenleyicisinde durumunu kapatarak her kural tek tek de kapatabilirsiniz.

    ![bir ilkede kuralı kapatma seçenekleri.](../media/f7b258ff-1b8b-4127-b580-83c6492f2bef.png)

    Ayrıca, bir ilkede birden çok kuralın önceliğini de değiştirebilirsiniz. Bunu yapmak için, düzenleme için bir ilke açın. Kuralın bir satırda üç noktayı (**...**) seçin ve sonra aşağı taşı veya En son **getir gibi** **bir seçenek belirtin**.

    ![Kural önceliğini ayarlama.](../media/dlp-set-rule-priority.png)

#### <a name="end-user-training"></a>Son kullanıcı eğitimi

DLP ilkesi tetiklendiğinde, ilkelerinizi E-posta bildirimleri gönderecek ve [DLP](use-notifications-and-policy-tips.md#send-email-notifications-and-show-policy-tips-for-dlp-policies) ilkeleriyle ilgili ilke ipuçlarını yöneticilere ve son kullanıcılara gösterecek şekilde yapılandırabilirsiniz. İlkeleriniz test modundayken ve engelleme eylemini uygulamaya uygulanmadan önce, ilke ipuçları hassas öğeler üzerinde riskli davranışlar farkındalığını artırmak ve kullanıcıları gelecekte bu davranışlardan kaçınmak için eğitmek için yararlı yollardır.  

#### <a name="review-dlp-requirements-and-update-strategy"></a>DLP gereksinimlerini ve güncelleştirme stratejisini gözden geçirme

Kuruluşta tabi olan düzenlemeler, yasalar ve endüstri standartları zaman içinde değişir ve DLP'ye ilişkin iş hedefleriniz de değişir. Tüm bu alanlar için düzenli olarak incelemeler bulundurarak, kuruluşta uyumluluğun devam ettiği ve DLP uygulamanın iş ihtiyaçlarınızı karşılamaya devam ettiğine emin olun.

## <a name="approaches-to-deployment"></a>Dağıtıma yaklaşımlar

|Müşteri iş ihtiyaçları açıklaması  | yaklaşım  |
|---------|---------|
|**Contoso Bank** , son derece düzenlemeye tabi bir sektöre sahiptir ve birçok farklı konumda birçok farklı türde hassas öğeye sahiptir. </br> - hangi hassas bilgi türlerinin en yüksek öncelik olduğunu bilir. </br> - ilkeler geldiklerinde iş aksaklıklarını en aza indirmesi gerekir. </br> - IT kaynakları vardır ve planlamaya, tasarım dağıtımına yardımcı olmak için uzman kiralayabilirsiniz </br> - Microsoft ile bir premier destek sözleşmesi var| - Hangi düzenlemelere uymaları gerektiğini ve nasıl uyumlu olacaklarını anlamak için zaman zaman kabul edin. </br> -Bilgi Koruma yığınının birlikte daha iyi değerini anlamak Microsoft 365 zaman al </br> - Öncelikleri olan öğeler için duyarlılık etiketleme düzeni geliştirin ve </br> - İş süreci sahiplerini içerir </br>- Tasarım/kod ilkeleri, test modunda dağıtım, kullanıcıları eğitin </br>- yinele|
|**TailSpin Toys** ne olduğunu veya nerede olduğunu bilmiyor ve kaynak derinliği çok az. Bunlar yoğun Teams, OneDrive İş ve Exchange şekilde kullanır.     |- Önceliklerli konumlarda basit ilkelerle çalışmaya başlama. </br>- Nelerin tanım yaptığını izleme </br>- Duyarlılık etiketlerini buna uygun olarak uygulama </br>- İlkeleri geliştirme, kullanıcıları eğitma       |
|**Fabrikam** küçük bir başlangıçtır ve fikri mülkiyetini korumak istiyor ve hızla hareket gerekiyor. Bazı kaynakları ayırmaya hazırlar, ancak dışarıdan uzmanları işe alamazlar. </br>- Hassas öğelerin hepsi aynı Microsoft 365 OneDrive İş/SharePoint </br>- Kullanıcıların ve kullanıcıların OneDrive İş yavaş SharePoint, çalışanlar/gölgeLI IT, öğeleri paylaşmak/depolamak için DropBox ve Google sürücüsü kullanır </br>- Veri koruma disiplini üzerinden çalışanların çalışma değeri hızı </br>- 18 çalışanın hepsini yeni bir cihazla çarpıp Windows 10 satın aldı     |- E-postada varsayılan DLP ilkesi Teams </br>- Bu ürünler için varsayılan olarak kısıtlanmış SharePoint kullanın </br>- Dış paylaşımı engelleyen ilkeleri dağıtma </br>- Önceliklendirmek istediğiniz konumlara ilkeleri dağıtın </br>- İlkeleri Windows 10 dağıtma </br>- Bulut depolama alanı olmayan OneDrive İş engelleme      |

<!--

## Planning for workloads

### Exchange

### SharePoint

### OneDrive for Business

### Teams

### Windows 10 Devices

### Microsoft Cloud App Security (MCAS)

### On-premises Scanner
-->

## <a name="see-also"></a>Ayrıca bkz.
- [Veri kaybını önleme hakkında bilgi](dlp-learn-about-dlp.md#learn-about-data-loss-prevention)
