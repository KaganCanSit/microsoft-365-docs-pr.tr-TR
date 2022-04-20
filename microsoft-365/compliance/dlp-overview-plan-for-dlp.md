---
title: Veri kaybı önleme planı
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
description: Veri kaybı önlemeye yönelik planlama sürecine genel bakış
ms.openlocfilehash: 68e2b3145521433dd8e0f602b8edb571c45ed9df
ms.sourcegitcommit: e911dd506ea066795e418daf7b84c1e11381a21c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/19/2022
ms.locfileid: "64953459"
---
# <a name="plan-for-data-loss-prevention-dlp"></a>Veri kaybı önlemeyi planlama (DLP)

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Her kuruluşun iş gereksinimleri, hedefleri, kaynakları ve durumu kendilerine özel olduğundan, her kuruluş veri kaybı önlemeyi (DLP) farklı şekilde planlar ve uygular. Ancak, tüm başarılı DLP uygulamaları için ortak olan öğeler vardır. Bu makalede, kuruluşların DLP planlamalarında kullandığı en iyi yöntemler yer alır.

## <a name="multiple-starting-points"></a>Birden çok başlangıç noktası

Birçok kuruluş, çeşitli kamu veya sektör düzenlemelerine uymak için DLP uygulamayı tercih eder. Örneğin, Avrupa Birliği Genel Veri Koruma Yönetmeliği (GDPR) veya Sağlık Sigortası Taşınabilirlik ve Sorumluluk Yasası (HIPAA) veya California Tüketici Gizliliği Yasası (CCPA). Ayrıca fikri mülkiyetlerini korumak için veri kaybı önleme uygular. Ancak DLP yolculuğunda başlangıç yeri ve nihai hedef farklılık gösterir. 

Kuruluşlar DLP yolculuğuna başlayabilir:

- Teams Sohbet ve Kanal iletilerindeki veya Windows 10 cihazlardaki bilgileri korumak isteme gibi bir platform odağından
- sağlık kayıtları gibi korumaya öncelik vermek istedikleri hassas bilgileri bilme ve doğrudan korumak için ilke tanımlamaya gitme
- hassas bilgilerinin ne olduğunu, nerede olduğunu ve kimlerin ne yaptığını bilmeden keşif ve kategorilere ayırma ile başlayıp daha yöntemli bir yaklaşım benimsediler
- hassas bilgilerinin ne olduğunu, nerede olduğunu ya da kimlerin ne yaptığını bilmeden, ancak doğrudan ilkeleri tanımlamaya ve bu sonuçları başlangıç noktası olarak kullanmaya ve ardından ilkelerini oradan iyileştirmeye devam ederler
- Tam Microsoft Purview Information Protection yığınını uygulamaları gerektiğini bilerek ve bu nedenle daha uzun vadeli, yöntemsel bir yaklaşım benimsemeyi amaçladılar

Bunlar, müşterilerin DLP'ye nasıl yaklaşabileceğine dair bazı örneklerdir ve nereden başladığınız önemli değildir, DLP başlangıçtan tam olarak gerçekleştirilen veri kaybı önleme stratejisine kadar çeşitli bilgi koruma yolculuklarını barındıracak kadar esnektir. 

## <a name="overview-of-planning-process"></a>Planlama sürecine genel bakış

[Microsoft Purview Veri Kaybı Önleme hakkında bilgi edinin](dlp-learn-about-dlp.md#learn-about-data-loss-prevention) bölümünde [DLP planlama sürecinin](dlp-learn-about-dlp.md#plan-for-dlp) üç farklı yönü tanıtılır. Burada tüm DLP planlarında ortak olan öğeler hakkında daha ayrıntılı bilgi vereceğiz.

### <a name="identify-stakeholders"></a>Paydaşları belirleme

DLP ilkeleri uygulandığında kuruluşunuzun büyük bölümlerine uygulanabilir. BT, olumsuz sonuçlar olmadan kendi başına geniş kapsamlı bir plan geliştiremez. Aşağıdakileri yapabilecek paydaşları tanımlamanız gerekir:

- kuruluşunuzun tabi olduğu düzenlemeleri, yasaları ve endüstri standartlarını açıklama
- korunacak hassas öğe kategorileri
- kullanıldıkları iş süreçleri
- sınırlı olması gereken riskli davranış
- söz konusu öğelerin ve riskin duyarlılığına bağlı olarak öncelikle hangi verilerin korunması gerektiğini önceliklendirme
- DLP ilkesi eşleştirme olay incelemesi ve düzeltme işleminin ana hattı 
 
Genel olarak bu ihtiyaçlar %85 mevzuat ve uyumluluk koruması ve %15 fikri mülkiyet koruması olma eğilimindedir. Planlama sürecinize dahil etmek için rollerle ilgili bazı öneriler şunlardır:

- Mevzuat ve uyumluluk görevlileri
- Risk sorumlusu
- Hukuk görevlileri
- Güvenlik ve uyumluluk görevlileri
- Veri öğeleri için işletme sahipleri
- İş kullanıcıları
- IT

### <a name="describe-the-categories-of-sensitive-information-to-protect"></a>Korunacak hassas bilgi kategorilerini açıklama

Paydaşlar daha sonra korunacak hassas bilgi kategorilerini ve kullanıldıkları iş sürecini açıklar. Örneğin, DLP şu kategorileri tanımlar:

- Finansal 
- Tıbbi bilgiler ve sağlık bilgileri
- Gizlilik
- Özel

Paydaşlar hassas bilgileri "Veri işleyicisiyiz, bu nedenle veri sahibi bilgileri ve finansal bilgiler üzerinde gizlilik korumaları uygulamamız gerekiyor" olarak tanımlayabilir.

 
  <!-- The business process is important as it informs the ‘data at rest’, ‘data in transit’, ‘data in use’ aspect of DLP planning and who should be sharing the items and who should not.-->

### <a name="set-goals-and-strategy"></a>Hedefleri ve stratejiyi belirleme

Paydaşlarınızı tanımladıktan ve hangi hassas bilgilerin korunması gerektiğini ve nerede kullanıldığını bildiğinizde, paydaşlar koruma hedeflerini belirleyebilir ve BT bir uygulama planı geliştirebilir. 


 <!--
### Discovery
 for the locations (DLP workloads) of these types of items.  (mapping DLP locations and data at rest, data in transit, data in use)

### IT can start coding test policies
start small and always in test mode. Note that DLP policies can feed into insider risk.

### Business process owners help with tuning
 false positive/false negative results and fitting DLP into their business processes.

-->

### <a name="set-implementation-plan"></a>Uygulama planını ayarlama

Uygulama planınız şunları içermelidir:

- Başlangıç durumunuzu ve istediğiniz bitiş durumunu ve birinden diğerine alma adımlarını eşleme
- hassas öğelerin bulunmasıyla nasıl ilgileneceksiniz?
- ilke planlaması ve bunların uygulanacağı sıra
- önkoşulları nasıl ele alasınız?
- zorlamaya geçmeden önce ilkelerin ilk olarak nasıl test edileceğini planlama
- son kullanıcılarınızı nasıl eğiteceğiniz
- ilkelerinizi nasıl test edeceğinizi ve ayarlayabileceğinizi
- değişen mevzuat, yasal, endüstri standardı veya fikri mülkiyet koruması ve iş gereksinimlerine göre veri kaybı önleme stratejinizi nasıl gözden geçireceğiniz ve güncelleştirdiğiniz

#### <a name="map-out-path-from-start-to-desired-end-state"></a>Başlangıçtan istenen bitiş durumuna giden yolu eşleme

Kuruluşunuzun başlangıç durumundan istenen bitiş durumuna nasıl geçeceğini belgeleme, proje katılımcılarınızla iletişim kurmak ve proje kapsamını ayarlamak için gereklidir. DLP'yi dağıtmak için yaygın olarak kullanılan bir dizi adım aşağıdadır. Bundan daha fazla ayrıntı isteyeceksiniz, ancak bunu kullanarak DLP benimseme yolunuzu çerçeveleyebilirsiniz.

![DLP dağıtımı için ortak sırayı gösteren grafik.](../media/dlp-deployment-planning.png)

#### <a name="sensitive-item-discovery"></a>Hassas öğe bulma

Tek tek hassas öğelerin ne olduğunu ve nerede bulunduklarını keşfetmenin birden çok yolu vardır. Duyarlılık etiketleriniz zaten dağıtılmış olabilir veya yalnızca öğeleri bulup denetleyebilen tüm konumlara geniş bir DLP ilkesi dağıtmaya karar vermiş olabilirsiniz. Daha fazla bilgi edinmek için bkz. [Verilerinizi öğrenme](information-protection.md#know-your-data).

#### <a name="policy-planning"></a>İlke planlaması

DLP benimsemenize başlarken, ilke tasarımınıza ve uygulama çalışmalarınıza odaklanmak için bu soruları kullanabilirsiniz.

##### <a name="what-laws-regulations-and-industry-standards-must-your-organization-comply-with"></a>Kuruluşunuzun hangi yasalara, düzenlemelere ve endüstri standartlarına uyması gerekir?

Birçok kuruluş mevzuat uyumluluğu hedefiyle DLP'ye geldiğinden, bu soruyu yanıtlamak DLP uygulamanızı planlamak için doğal bir başlangıç noktasıdır. Ancak BT uygulayıcısı olarak büyük olasılıkla yanıt verecek konumda değilsinizdir. Yasal ekibiniz ve iş yöneticileriniz tarafından yanıtlanması gerekir. 
 
**Örnek** Kuruluşunuz birleşik krallık'a tabidir. finansal düzenlemeler.


##### <a name="what-sensitive-items-does-your-organization-have-that-must-be-protected-from-leakage"></a>Kuruluşunuzda sızıntıya karşı korunması gereken hangi hassas öğeler var?

Kuruluşunuz mevzuat uyumluluğu gereksinimleri açısından nerede durduğunu öğrendikten sonra, hangi hassas öğelerin sızıntıya karşı korunması gerektiği ve bunları korumak için ilke uygulamasının önceliğini nasıl ayarlamak istediğiniz konusunda fikir sahibi olursunuz. Bu, en uygun DLP ilkesi şablonlarını seçmenize yardımcı olur. Microsoft Purview Finansal, Tıbbi ve sağlık, Gizlilik için önceden yapılandırılmış DLP şablonlarıyla birlikte gelir ve Özel şablonunu kullanarak kendi DLP şablonlarınızı oluşturabilirsiniz. Gerçek DLP ilkelerinizi tasarlayıp oluştururken, bu sorunun yanıtını bilmek doğru [hassas bilgi türünü](sensitive-information-type-learn-about.md#learn-about-sensitive-information-types) seçmenize de yardımcı olur.

**Örnek** Hızlı bir şekilde başlamak için, , `EU Debit Card Number`ve `SWIFT Code` hassas bilgi türlerini içeren `Credit Card Number`ilke şablonunu seçersiniz`U.K. Financial Data`. 

##### <a name="where-are-the-sensitive-items-and-what-business-processes-are-they-involved-in"></a>Hassas öğeler nerede ve hangi iş süreçlerine dahil oluyor?

Kuruluşunuzun hassas bilgilerini içeren öğeler, iş yaparken her gün kullanılır. Bu hassas bilgilerin örneklerinin nerede gerçekleşebileceğini ve hangi iş süreçlerinde kullanıldıklarını bilmeniz gerekir. Bu, DLP ilkelerinizin uygulanacağı doğru konumları seçmenize yardımcı olur. DLP ilkeleri konumlara uygulanır:

- e-postayı Exchange
- siteleri SharePoint
- hesapları OneDrive
- Sohbet ve kanal iletilerini Teams
- cihazları Windows 10
- Bulut Uygulamaları için Microsoft Defender
- Şirket içi depolar

**Örnek** Kuruluşunuzun iç denetçileri bir dizi kredi kartı numarasını izliyor. Elektronik tablolarını güvenli bir SharePoint sitesinde tutarlar. Çalışanlardan bazıları kopyaları alır ve Windows 10 cihazlarıyla eşitlenen iş OneDrive İş sitesine kaydeder. Bunlardan biri, 14 tanesinin listesini bir e-postaya yapıştırır ve gözden geçirilmesi için dış denetçilere göndermeye çalışır. İlkeyi güvenli SharePoint sitesine, tüm iç denetçilerin hesaplarına, Windows 10 cihazlarına ve Exchange e-postasına OneDrive İş istiyorsunuz.

##### <a name="what-is-your-organizations-tolerance-for-leakage"></a>Kuruluşların sızıntıya karşı dayanıklılığı nedir?

Kuruluşunuzdaki farklı grupların, kabul edilebilir düzeyde hassas öğe sızıntısı olup nelerin olmadığı konusunda farklı görünümleri olabilir. Sıfır sızıntı mükemmellik elde etmek, işletme için çok yüksek bir maliyete neden olabilir.

**Örnek** Kuruluşunuzun güvenlik grubu, hukuk ekibiyle birlikte hem kredi kartı numaralarının kuruluş dışındaki kişilerle paylaşılmaması gerektiğini düşünüyor hem de sıfır sızıntı konusunda ısrar ediyor. Ancak, kredi kartı numarası etkinliğinin düzenli olarak gözden geçirilmesi kapsamında, iç denetçilerin bazı kredi kartı numaralarını üçüncü taraf denetçilerle paylaşması gerekir. DLP ilkeniz kredi kartı numaralarının kuruluş dışında tüm paylaşımını yasaklarsa, iç denetçilerin izlemelerini tamamlaması için önemli bir iş süreci kesintisi ve kesintiyi azaltmak için maliyet eklenir. Bu ek maliyet, yönetici liderliği için kabul edilemez. Bu sorunu çözmek için, kabul edilebilir bir sızıntı düzeyine karar vermek için bir iç konuşma olması gerekir. Bu karar verildikten sonra, ilke belirli kişilerin bilgileri paylaşması için özel durumlar sağlayabilir veya yalnızca denetim modunda uygulanabilir.

#### <a name="planning-for-prerequisites"></a>Önkoşulları planlama

Bazı DLP konumlarını izleyebilebilmeniz için karşılanması gereken önkoşullar vardır. Başlamadan **önce** bölümlerine bakın:

- [Şirket içi tarayıcı (önizleme) veri kaybı önleme ile Kullanmaya başlayın](dlp-on-premises-scanner-get-started.md#before-you-begin)
- [Uç noktada veri kaybı önlemeyi kullanmaya başlama](endpoint-dlp-getting-started.md#before-you-begin)
- [Microsoft uyumluluk uzantısıyla Kullanmaya başlayın](dlp-chrome-get-started.md#before-you-begin)
- [Microsoft dışı bulut uygulamaları için veri kaybı önleme ilkelerini kullanma (önizleme)](dlp-use-policies-non-microsoft-cloud-apps.md#before-you-begin)

#### <a name="policy-deployment"></a>İlke dağıtımı

DLP ilkelerinizi oluştururken, etkilerini değerlendirmek ve tam olarak zorlamadan önce etkinliklerini test etmek için bunları aşamalı olarak kullanıma almayı düşünmelisiniz. Örneğin, yeni bir DLP ilkesinin binlerce belgeye erişimi istemeden engellemesini veya mevcut bir iş sürecini bozmasını istemezsiniz.
  
Büyük bir olası etkiyle DLP ilkeleri oluşturuyorsanız şu diziyi takip kullanmanızı öneririz:
  
1. **İlke İpuçları olmadan test modunda başlayın** ve ardından etkiyi değerlendirmek için DLP raporlarını ve olay raporlarını kullanın. İlke eşleşmelerinin sayısını, konumunu, türünü ve önem derecesini görüntülemek için DLP raporlarını kullanabilirsiniz. Sonuçlara bağlı olarak, ilkeleri gerektiği gibi ayarlayabilirsiniz. Test modunda DLP ilkeleri, kuruluşunuzda çalışan kişilerin üretkenliğini etkilemez. Ayrıca, DLP olay incelemesi ve sorun düzeltmesi için iş akışınızı test etmek için bu aşamayı kullanın.
    
2. Kullanıcılara uyumluluk ilkelerinizi **öğretmeye ve uygulanacak ilkelere hazırlamaya başlamak için bildirimler ve İlke İpuçları ile Test moduna geçin**. İlke ipucunda ilke hakkında daha fazla ayrıntı sağlayan bir kuruluş ilkesi sayfasının bağlantısının olması yararlı olur. Bu aşamada, ilkeleri daha da geliştirebilmek için kullanıcılardan hatalı pozitif sonuçları bildirmelerini de isteyebilirsiniz. İlke uygulamasının sonuçlarının proje katılımcılarının aklındakiyle eşleştiğinden emin olduktan sonra bu aşamaya geçin. 
    
3. Kurallardaki eylemlerin uygulanması ve içeriğin korunması için **ilkeler üzerinde tam zorlama başlatın**. Sonuçların amacınız olduğundan emin olmak için DLP raporlarını ve olay raporlarını veya bildirimlerini izlemeye devam edin. 

    ![Test modunu kullanma ve ilkeyi açma seçenekleri.](../media/49fafaac-c6cb-41de-99c4-c43c3e380c3a.png)

    bir DLP ilkesini istediğiniz zaman kapatabilirsiniz ve bu ilkedeki tüm kuralları etkiler. Ancak, her kural, durumunu kural düzenleyicisinde değiştirerek tek tek kapatılabilir.

    ![İlkedeki bir kuralı kapatma seçenekleri.](../media/f7b258ff-1b8b-4127-b580-83c6492f2bef.png)

    İlkedeki birden çok kuralın önceliğini de değiştirebilirsiniz. Bunu yapmak için düzenlemek üzere bir ilke açın. Bir kuralın satırında üç noktayı (**...**) ve ardından **Aşağı taşı** veya **En sona getir** gibi bir seçenek belirleyin.

    ![Kural önceliğini ayarlayın.](../media/dlp-set-rule-priority.png)

#### <a name="end-user-training"></a>Son kullanıcı eğitimi

Bir DLP ilkesi tetiklendiğinde, ilkelerinizi [E-posta bildirimleri gönderecek ve DLP ilkeleri için ilke ipuçlarını](use-notifications-and-policy-tips.md#send-email-notifications-and-show-policy-tips-for-dlp-policies) yöneticilere ve son kullanıcılara gösterecek şekilde yapılandırabilirsiniz. İlkeleriniz hala test modundayken ve engelleyici bir eylemi zorunlu kılmaya ayarlanmadan önce ilke ipuçları, hassas öğelerdeki riskli davranışların farkındalığını artırmanın ve kullanıcıları gelecekte bu davranışlardan kaçınmaları için eğitmenin yararlı yollarıdır.  

#### <a name="review-dlp-requirements-and-update-strategy"></a>DLP gereksinimlerini ve güncelleştirme stratejisini gözden geçirin

Kuruluşunuzun tabi olduğu düzenlemeler, yasalar ve endüstri standartları zaman içinde değişir ve DLP için iş hedefleriniz de değişir. Kuruluşunuzun uyumlu kalması ve DLP uygulamanızın iş gereksinimlerinizi karşılamaya devam etmesi için tüm bu alanların düzenli incelemelerini eklediğinizden emin olun.

## <a name="approaches-to-deployment"></a>Dağıtım yaklaşımları

|Müşteri iş gereksinimleri açıklaması  | Yaklaşım  |
|---------|---------|
|**Contoso Bank** yüksek düzeyde düzenlenmiş bir sektördedir ve birçok farklı konumda birçok farklı hassas öğe türüne sahiptir. </br> - Hangi hassas bilgi türlerinin en öncelikli olduğunu bilir. </br> - ilkeler dağıtılırken iş kesintilerini en aza indirmelidir. </br> - BT kaynaklarına sahiptir ve planlamaya, tasarım dağıtımına yardımcı olması için uzmanları işe alabilir </br> - Microsoft ile premier bir destek sözleşmesi var| - Hangi düzenlemelere uymaları gerektiğini ve nasıl uyum sağlayacaklarını anlamak için zaman ayırın. </br> -Microsoft Purview Information Protection yığınının birlikte daha iyi değerini anlamak için zaman ayırın </br> - Önceliklendirilmiş öğeler için duyarlılık etiketleme şeması geliştirin ve uygulayın </br> - İş süreci sahiplerini dahil edin </br>- Tasarım/kod ilkeleri, test modunda dağıtma, kullanıcıları eğitma </br>- tekrarla|
|**TailSpin Toys** neleri olduğunu veya nerede olduğunu bilmez ve çok az kaynak derinliğine sahiptir. Teams, OneDrive İş ve Exchange kapsamlı olarak kullanırlar.     |- Öncelikli konumlarda basit ilkelerle başlayın. </br>- Tanımlananları izleme </br>- Duyarlılık etiketlerini uygun şekilde uygulama </br>- İlkeleri iyileştirme, kullanıcıları eğitma       |
|**Fabrikam** küçük bir startup ve fikri mülkiyetini korumak istiyor ve hızla hareket etmelidir. Bazı kaynakları ayırmaya istekliler, ancak dışarıdan uzmanlar kiralamayı göze alamıyorlar. </br>- Hassas öğelerin tümü Microsoft 365 OneDrive İş/SharePoint </br>- OneDrive İş ve SharePoint benimsenmesi yavaştır, çalışanlar/gölge BT öğeleri paylaşmak/depolamak için DropBox ve Google sürücüsü kullanır </br>- Çalışanlar veri koruma uzmanlık alanına göre iş hızına değer verir </br>- Müşteri 18 çalışanın tümünü yeni Windows 10 cihazları birleştirip satın aldı     |- Teams'da varsayılan DLP ilkesinden yararlanın </br>- SharePoint öğeleri için varsayılan olarak kısıtlanmış ayarını kullanın </br>- Dış paylaşımı engelleyen ilkeler dağıtma </br>- İlkeleri öncelikli konumlara dağıtma </br>- Windows 10 cihazlara ilke dağıtma </br>- OneDrive İş olmayan bulut depolama alanına yüklemeleri engelleme      |

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
- [Veri kaybı önleme hakkında daha fazla bilgi edinme](dlp-learn-about-dlp.md#learn-about-data-loss-prevention)
