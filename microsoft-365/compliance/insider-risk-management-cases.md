---
title: Insider risk yönetimi vakaları
description: Risk yönetimiyle ilgili Insider risk Microsoft 365
keywords: Microsoft 365, insider risk yönetimi, risk yönetimi, uyumluluk
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
ms.openlocfilehash: d37a47a3cb46214d098623edbf5f0b9bea4b242a
ms.sourcegitcommit: efb333ce0772265da91632110acba39acfbe0bde
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/01/2021
ms.locfileid: "62997102"
---
# <a name="insider-risk-management-cases"></a>Insider risk yönetimi vakaları

Durumlar, insider risk yönetiminin merkezindedir ve ilkeleriniz içinde tanımlanmış risk göstergeleri tarafından oluşturulan sorunları derinden incelemenize ve üzerinde çalışmanıza olanak sağlar. Olaylar, kullanıcının uyumlulukla ilgili bir sorunu gidermek için başka bir işlem gerektirebilecek durumlarda uyarılardan el ile oluşturulur. Her olay tek bir kullanıcıya yöneliktir ve kullanıcı için mevcut bir vakaya veya yeni bir vakaya birden çok uyarı eklenebilir.

Olayın ayrıntılarını araştırdikten sonra, aşağıdakiler ile eyleme geçebilirsiniz:

- kullanıcıya bildirim gönderme
- durum olarak çözümleme
- ServiceNow örneğiniz veya bir e-posta alıcısı ile vakayı paylaşma
- davanın bir iş araştırmasından Advanced eDiscovery yükseltme

[Insider risk yönetimiyle ilgili davaların nasıl](https://www.youtube.com/watch?v=UONUSmkRC8s) araştırıldığına ve yönetilişine genel bir bakış için Insider Risk Yönetimi soruşturması ve yükseltme videosunu gözdenın.

## <a name="cases-dashboard"></a>Vakalar panosu

Insider risk yönetimi **Vakalar panosu** , vakaları görüntüleme ve bu vakalara göre işlem görüntülemeye olanak sağlar. Panoda yer alan her rapor pencere öğesi, son 30 günle ilgili bilgileri görüntüler.

- **Etkin durumlar**: soruşturma kapsamındaki etkin vakaların toplam sayısıdır.
- **Son 30 gün içinde vakalar**: Etkin ve Kapalı durumuna göre sıralanmış, oluşturulan *toplam* *vaka* sayısı.
- **İstatistikler**: Saat, gün veya ay olarak listelenen etkin vakaların ortalama süresi.

Servis durumu sırası, aşağıdaki olay özniteliklerinin geçerli durumuna ek olarak, tüm etkin ve kapalı durumdaki kuruluş durumlarını da listeler:

- **Vaka adı**: Bir uyarının onaylandığı ve oluşturulduğunda tanımlanan vakanın adı.  
- **Durum**: Etkin veya *Kapalı durumdadır**.*
- **Kullanıcı**: Olay için kullanıcı. Kullanıcı adları için anonimleştirme etkinleştirilirse, anonimleştirilmiş bilgiler görüntülenir.
- **Büyük/küçük** harf açma zamanı: Vakanın açılmasından bu yana geçen zaman.
- **Toplam ilke uyarıları**: İlkenin olayla eşleşme sayısı. Bu sayı, vakaya yeni uyarılar eklenirse artabilir.
- **Büyük/küçük** harf son güncelleştirme: Olay durumunda bir büyük/küçük harf notu veya değişiklik oldu, bu yana geçen zaman.
- **Son güncelleştirme**: Insider risk yönetimi analisti veya bu vakayı son güncelleştirmede tercihen tercihlerinin adı.

![Insider risk yönetimi Vakalar panosu.](../media/insider-risk-cases-dashboard.png)

Belirli bir **metinde** büyük/harf adlarını aramak için Ara denetimlerini kullanın ve vakaları aşağıdaki özniteliklere göre sıralamak için büyük/harf filtresini kullanın:

- Durum
- Açılmış saat durumu, başlangıç tarihi ve bitiş tarihi
- Son güncelleştirme, başlangıç tarihi ve bitiş tarihi

## <a name="filter-cases"></a>Vakaları filtreleme

Kuruluşta etkin Insider risk yönetimi ilkelerinin sayısına ve türüne bağlı olarak, büyük bir dava sırasına gözden geçirmek zor olabilir. Vaka filtrelerinin kullanımı, analistlerin ve tahminlerin vakaları çeşitli özniteliklere göre sıralamanıza yardımcı olabilir. Vakalar panosunda uyarıları **filtrelemek için** Filtre **denetimi'ne** seçin. Vakaları bir veya birden çok öznitelike göre filtreleysiniz:

- **Durum**: Vaka listesini filtrelemek için bir veya birden çok durum değeri seçin. Seçenekler Etkin ve  *Kapalı'dır*.
- **Açılmış saat durumu**: Vakanın açl olduğu tarihin başlangıç ve bitiş tarihlerini seçin.
- **Son güncelleştirme**: Vakanın güncelleştirilmiş olduğu tarihin başlangıç ve bitiş tarihlerini seçin.

## <a name="investigate-a-case"></a>Vakayı araştırma

Insider risk yönetimi uyarıları hakkında daha derin araştırma yapmak, doğru düzeltme eylemleri yapmak için çok önemlidir. Insider risk yönetimi örnekleri, kullanıcı risk etkinliği geçmişini, uyarı ayrıntılarını, risk olaylarının sırasını incelemenin, risklere açık olan içeriği ve iletileri incelemenin merkezi yönetim aracıdır. Risk analistleri ve tahminler, geri bildirimleri ve notları merkezi bir şekilde gözden geçirmek ve dava çözümlerini süreç etmek için vakaları da kullanır.

Vakayı seçmek, olay yönetim araçlarını açar ve analistlerin ve tahminlere vakaların ayrıntılarını ayrıntılarıyla açmalarını sağlar.

### <a name="case-overview"></a>Büyük/harfe genel bakış

Vaka **genel bakış sekmesi** , risk analistleri ve tahminlere ilişkin olay ayrıntılarını özetler. Bu vaka hakkında alanında **aşağıdaki bilgileri içerir**

- **Durum**: Etkin veya Kapalı durumda olan vakanın geçerli durumu.
- **Vaka oluşturma tarihi**: Vakanın oluşturulma tarihi ve saati.
- **Kullanıcının risk puanı**: Olay için kullanıcının geçerli hesaplanan risk düzeyidir. Bu puan her 24 saatte bir hesaplanır ve kullanıcıyla ilişkili tüm etkin uyarılardan uyarı riski puanlarını kullanır.
- **E-posta**: Olay için kullanıcının e-posta diğer adı.
- **Kuruluş veya** bölüm: Kullanıcının atandığı kuruluş veya bölüm.
- **Yönetici adı**: Kullanıcının yöneticisinin adı.
- **Yönetici e-postası**: Kullanıcının yöneticisinin e-posta diğer adı.

![Insider risk yönetimi olay ayrıntıları.](../media/insider-risk-case-details.png)

**Vakaya genel** bakış sekmesi ayrıca **, olayla** ilişkili ilke eşleşme uyarıları hakkında aşağıdaki bilgileri içeren Uyarılar bölümünü de içerir:

- **İlke eşleşmeleri**: Kullanıcı etkinliğine yönelik eşleşme uyarıları ile ilişkilendirilmiş insider risk yönetimi ilkesi adı.
- **Durum**: Uyarının durumu.
- **Önem Derecesi**: Uyarının önem derecesi.
- **Algılanan saat**: Uyarının oluşturulmadan bu yana geçen zaman.

### <a name="alerts"></a>Uyarılar

Uyarılar **sekmesi** olayla birlikte gelen geçerli uyarıları özetler. Mevcut bir vakaya yeni uyarılar eklenebilir ve bunlar atandığı sırada Uyarı kuyruğuna eklenir. Aşağıdaki uyarı öznitelikleri sıraya göre listelenir:

- Durum
- Önem Derecesi
- Algılanan saat

Uyarı ayrıntı sayfasını görüntülemek için kuyruktan bir **uyarı** seçin.

Belirli metinlerin uyarı adlarında arama yapmak için arama denetimi kullanın ve aşağıdaki özniteliklere göre vakaları sıralamak için uyarı filtresini kullanın:

- Durum
- Önem Derecesi
- Algılanan saat, başlangıç tarihi ve bitiş tarihi

Uyarıları aşağıdakiler gibi çeşitli özniteliklere göre filtrelemek için filtre denetimi kullanın:

- **Durum**: Uyarı listesini filtrelemek için bir veya birden çok durum değeri seçin. Seçenekler Onaylandı, *Reddedildi*, *Gözden geçirilsin* *mi ve* *Çözümlendi seçenekleridir*.
- **Önem derecesi**: Uyarı listesini filtrelemek için bir veya daha fazla uyarı riski önem düzeyi seçin. Seçenekler *Yüksek, Orta* *ve* *Düşük'tür*.
- **Algılanan saat**: Uyarının ne zaman oluşturulduğunda başlangıç ve bitiş tarihlerini seçin.
- **İlke**: Seçili ilkeler tarafından oluşturulan uyarıları filtrelemek için bir veya birden çok ilke seçin.

### <a name="user-activity"></a>Kullanıcı etkinliği

Kullanıcı **etkinliği sekmesi** , insider risk yönetimi çözümünde şirket içi risk çözümlemesi ve soruşturma için en güçlü araçlardan biridir. Bu sekme, tüm uyarıların geçmiş zaman çizelgesi, uyarı ayrıntıları, kullanıcının olayda geçerli risk puanı, risk olaylarının dizisi ve durumdaki riskleri etkili bir şekilde içeren denetimler de içinde olmak üzere olaylarda hızlı gözden geçirmeyi sağlayacak şekilde yapılandırılmıştır.

![Insider risk yönetimi kullanıcı etkinliği.](../media/insider-risk-user-activities.png)

1. **Saat filtreleri**: Varsayılan olarak, olayda onaylanmış son altı uyarı, Kullanıcı etkinliği grafiğinde görüntülenir. Kabarcık grafiğinde *6* Ay, *3* Ay veya *1 Ay sekmelerini* seçerek grafik görünümünü kolayca filtrelayabilirsiniz.
2. **Risk uyarısı etkinliği ve ayrıntıları**: Risk etkinlikleri, Kullanıcı etkinliği grafiğinde görsel olarak renkli kabarcıklar olarak görüntülenir. Kabarcıklar farklı risk kategorileri için oluşturulur ve kabarcık boyutu kategori için risk etkinliklerinin sayısına orantılıdır. Her risk etkinliğinin ayrıntılarını görüntülemek için bir kabarcık seçin. Ayrıntılar şunlardır:
    - **Risk** etkinliğinin tarihi.
    - **Risk etkinliği kategorisi**. Örneğin, *kuruluşun dışından gönderilen ekleri içeren e-posta* veya *SharePoint Online'dan indirilen e-SharePoint.*
    - **Uyarının** risk puanı. Bu puan, uyarı riski önem düzeyine göre sayısal puandır.
    - Uyarıyla ilişkili olayların sayısı. Risk etkinliğiyle ilişkili her dosya veya e-postanın bağlantıları da kullanılabilir.
3. **Risk sırası (önizleme)**: Riskli etkinliklerin kronolojik sırası, risk araştırmanın ve bu ilişkili etkinliklerin belirlenmesi, kurum açısından bir bütün olarak riski değerlendirmenin önemli bir kısmıdır. İlgili uyarı etkinlikleri, bu etkinliklerin daha büyük bir risk alanıyla ilişkilendiril vurgulu olduğu bağlantı çizgileri ile görüntülenir. Etkinliklerin bu görünümü, yalıtılmış veya tek başına etkinlikler olarak görüntülenilebilecek risk etkinlikleri için kelime anlamıyla "noktaları birbirine bağlama" yardımcı olabilir. İlişkili tüm risk etkinliklerinin ayrıntılarını görüntülemek için sırayla herhangi bir kabarcık seçin. Ayrıntılar şunlardır:

    - **Sıranın** adı.
    - **Sıranın** **tarih veya** tarih aralığı.
    - **Dizi için** risk puanı. Bu puan, dizide ilgili her etkinlik için birleştirilmiş uyarı risk önem düzeyi düzeylerinin sırasının sayısal puanıdır.
    - **Dizide yer alan her uyarıyla ilişkilendirilmiş olay sayısı**. Risk etkinliklerinin her biri ile ilişkilendirilmiş her dosya veya e-postanın bağlantıları da mevcuttur.
    - **Etkinlikleri sırayla gösterme**. Sırayı kabarcık grafiğinde vurgu çizgisi olarak görüntüler ve ilgili tüm uyarıları sırayla görüntülemek için uyarı ayrıntılarını genişleter.

4. **Risk etkinliği gösterge**: Kullanıcı etkinliği grafiğinin alt kısmında, renk kodlu bir gösterge her uyarı için risk kategorisini hızla belirlemenize yardımcı olur.
5. **Risk etkinliği kronolojisi**: Vakayla ilişkilendirilmiş tüm risk uyarılarının tam kronolojik listesi, buna karşılık gelen uyarı balonunda bulunan tüm ayrıntılar da dahil olmak üzere listelenir.
6. **Olay eylemleri**: Vakayı çözmeye yönelik seçenekler, olay eylemi araç çubuğundadır. Bir durumu çözebilir, kullanıcıya e-posta bildirimi gönderebilir veya veri veya kullanıcı soruşturması için durumu en iyi şekilde ifade edin.

### <a name="activity-explorer-preview"></a>Etkinlik gezgini (önizleme)

> [!IMPORTANT]
> Etkinlik gezgini sekmesi, bu özellik kurumda kullanılabilir olduktan sonra olayları tetikleyen kullanıcılar için olay yönetimi alanında yer almaktadır.

Etkinlik **gezgini sekmesi,** risk analistlerine ve tahminlere, risk uyarıları ile ilişkili etkinlik ayrıntılarını gözden geçirmelerine olanak sağlar. Örneğin, olay yönetimi eylemlerinin bir parçası olarak, analistlerin ve analistlerin daha ayrıntılı bilgi için olayla ilişkili tüm risk etkinliklerini gözden geçirmeleri gerekir. Etkinlik **gezginiyle**, gözden geçirenler algılanan riskli etkinliğin zaman çizelgesini hızla gözden geçirebilirsiniz ve uyarılarla ilişkilendirilmiş tüm risk etkinliklerini tanımlayabilir ve filtreleyebilirsiniz.

Etkinlik gezgini hakkında daha fazla bilgi için [Insider risk yönetimi uyarıları makalesine](insider-risk-management-activities.md#activity-explorer) bakın.

### <a name="content-explorer"></a>İçerik gezgini

İçerik **gezgini sekmesi** , risk uyarıları ile ilişkilendirilmiş tüm tek tek dosyaların ve e-posta iletilerinin kopyalarını gözden geçirme riski sağlar. Örneğin, bir kullanıcı SharePoint Online'dan yüzlerce dosya indirirken uyarı oluşturulursa ve etkinlik bir ilke uyarısı tetiklerse, uyarıyla ilgili olarak indirilen tüm dosyalar özgün depolama kaynaklarından insider risk yönetimi durumuna yakalanır ve kopyalanır.

İçerik gezgini, temel ve gelişmiş arama ve filtreleme özelliklerine sahip güçlü bir araçtır. İçerik gezginini kullanma hakkında daha fazla bilgi edinmek için bkz. [Insider risk yönetimi İçerik gezgini](insider-risk-management-content-explorer.md).

![Insider risk yönetimi durumu İçerik gezgini.](../media/insider-risk-content-explorer.png)

### <a name="case-notes"></a>Olay notları

**Olayda Örnek Olay** notları sekmesi, risk analistleri ve tahminlerinin olayla ilgili görüşlerini, geri bildirimleri ve içgörüleri paylaştığı durumtur. Notlar, bir vakaya kalıcı eklemedir ve not kaydedildikten sonra düzenlenemez veya silinemez. Uyarıdan olay oluşturulduğunda, Uyarıyı onayla ve **Insider risk** durumu oluştur iletişim kutusuna girilen açıklamalar, otomatik olarak olay notu olarak eklenir.

Büyük/küçük harf notları panosu, notu oluşturan kullanıcının notları ve not kaydedildiktan sonra geçen zamanı görüntüler. Büyük/küçük harf notu metin alanında belirli bir anahtar sözcüğü aramak için,  büyük/küçük harf panosunda Ara düğmesini kullanın ve belirli bir anahtar sözcüğü girin.

Vakaya not eklemek için:

1. Giriş [Microsoft 365 uyumluluk merkezi](https://compliance.microsoft.com) **Insider risk yönetimi'ne gidin ve** Vakalar **sekmesini** seçin.
2. Bir vaka seçin ve ardından Büyük/küçük **harf notları sekmesini** seçin.
3. Büyük/ **harf notu ekle'yi seçin**.
4. Büyük **/harf notu ekle** iletişim kutusunda, vakayla ilgili notunu yazın. Notu **vakaya** eklemek için Kaydet'i seçin veya **notu büyük/** harfe kaydetmeden kapat'ı seçin.

### <a name="contributors"></a>Katkıda Bulunanlar

**Olayda Katkıda** Bulunanlar sekmesi, risk analistleri ve güvenlikçilerin vakaya başka gözden geçirenler ekleyt olduğu durumtur. Varsayılan olarak, **Insider Risk Yönetimi** Analistleri'ne atanan tüm kullanıcılar ve **Insider Risk** Yönetimi Tahminleri rolleri her etkin ve kapalı vaka için katkıda bulunanlar olarak listelenir. Yalnızca **Insider Risk Yönetimi Güvenlik rolüne** atanan kullanıcıların İçerik gezgininde dosyaları ve iletileri görüntüleme izni vardır.

Bir kullanıcı katkıda bulunan olarak ek tarafından vakaya geçici erişim ve verilmek. Katkıda bulunanların, aşağıdakiler dışında belirli bir vaka üzerinde tüm olay yönetimi denetimi vardır:

- Uyarıları onaylama veya yok sayma izni
- Vakalara katkıda bulunanları düzenleme izni
- İçerik Gezgini'nde dosya ve iletileri görüntüleme izni

Vakaya katkıda bulunan eklemek için:

1. Giriş [Microsoft 365 uyumluluk merkezi](https://compliance.microsoft.com) **Insider risk yönetimi'ne gidin ve** Vakalar **sekmesini** seçin.
2. Bir vaka seçin ve ardından Katkıda **Bulunanlar sekmesini** seçin.
3. Katılımcı **ekle'yi seçin**.
4. Katılımcı **ekle iletişim** kutusunda, eklemek istediğiniz kullanıcının adını yazmaya başlayın ve ardından önerilen kullanıcı listesinden bir kullanıcı seçin. Bu liste, kiracı Azure Active Directory en son oluşturulan listedir.
5. Katılımcı **olarak** kullanıcı eklemek için Ekle'yi seçin veya katılımcı **olarak** kullanıcı eklemeden iletişim kutusunu kapat'ı seçin.

## <a name="case-actions"></a>Büyük/harf eylemleri

Risk risklerini almak için, durumun önem düzeyine, kullanıcının riski geçmişine ve kuruluş risk yönergelerine bağlı olarak çeşitli yöntemlerden birini kullanarak bir dava üzerinde işlem risklerini kabul edersiniz. Bazı durumlarda, kuruluşun diğer alanlarıyla işbirliği yapmak ve risk etkinliklerini daha derine indirmak için bir durumu kullanıcıya veya veri araştırmaya yükseltmeniz gerekiyor olabilir. Insider risk yönetimi,  end-end çözüm Microsoft 365 uyumluluk çözümleriyle sıkı bir şekilde tümleştirilmiştir.

### <a name="send-email-notice"></a>E-posta bildirimi gönderme

Çoğu durumda, insider risk uyarıları oluşturan kullanıcı eylemleri yanlışlıkla veya yanlışlıkla olur. Kullanıcıya e-postayla anımsatıcı bildirimi göndermek, büyük/küçük harf incelemesini ve eylemlerini belgelemenin etkili bir yöntemidir ve kurumsal ilkeleri kullanıcılara anımsatma veya onları yenileme eğitimine işaret eden bir yöntemdir. Bildirimler, insider risk [yönetim altyapınız için sizin oluştur](insider-risk-management-notices.md) oluşturursanız, bildirim şablonlarından oluşturulur.

Bir kullanıcıya ***** e-posta bildirimi göndermenin, sorunu çözemezse' hatanın kabul _Closed*. Bazı durumlarda, kullanıcıya yeni vakayı açmaya gerek kalmadan daha fazla risk etkinliklerine bakmak için bildirim gönderdikten sonra dosyayı açık bırakmak iyi olabilir. Bir bildirim gönderdikten sonra bir vakayı çözmek için, bildirimi verdikten sonra devam  eden bir adım olarak Vakayı çöz seçeneğini seçmeniz gerekir.

Vakaya atanan kullanıcıya bildirim göndermek için:

1. Giriş [Microsoft 365 uyumluluk merkezi](https://compliance.microsoft.com) **Insider risk yönetimi'ne gidin ve** Vakalar **sekmesini** seçin.
2. Bir vaka seçin ve ardından vaka eylem **araç çubuğundaki** E-posta bildirimini gönder düğmesini seçin.
3. **E-posta bildirimi gönder iletişim kutusunda**, Bildirimin bildirim **şablonunu seçmek** için Bildirim şablonu seç açılan kutusunu seçin. Bu seçim, bildirimle ilgili diğer alanları önceden doldurur.
4. Bildirim alanlarını gözden geçirebilirsiniz ve uygun şekilde güncelleştirebilirsiniz. Buraya girilen değerler, şablonda yer alan değerleri geçersiz kılar.
5. Bildirimi **kullanıcıya** göndermek için Gönder'i seçin veya bildirimi  kullanıcıya göndermeden İptal'i seçerek iletişim kutusunu kapatın. Tüm gönderilmiş bildirimler, Büyük/harf notları panosunda vaka notları **kuyruğuna** eklenir.

### <a name="escalate-for-investigation"></a>soruşturma için yükseltme

Kullanıcının risk etkinliği için ek yasal inceleme gerektirebilecek durumlarda, kullanıcı soruşturması için durumu en iyi duruma getirin. Bu yükseltme, Advanced eDiscovery başka bir Microsoft 365 açar. Advanced eDiscovery, kurum içi ve dış yasal soruşturmalarına yanıt veren içerikleri korumak, toplamak, gözden geçirmek, çözümlemek ve dışarı aktarmak için  uç uç iş akışı sağlar. Ayrıca, hukuk ekibimizin bir olaya dahil olan koruyucularla iletişim kurması için yasal tutma bildirimi iş akışının tamamını yönetmesini sağlar. Insider risk yönetimi durumundan oluşturulan bir Advanced eDiscovery durumunda bir gözden geçirene koruyucu olarak atamak, yasal ekibimizin uygun önlemleri almalarını ve içeriğin korunmasını yönetmelerini sağlar. Bu tür durumlar hakkında daha Advanced eDiscovery fazla bilgi edinmek için bu konuda [daha fazla bilgi Advanced eDiscovery' Microsoft 365](overview-ediscovery-20.md).

Vakayı kullanıcı araştırmaya yükseltme:

1. Giriş [Microsoft 365 uyumluluk merkezi](https://compliance.microsoft.com) **Insider risk yönetimi'ne gidin ve** Vakalar **sekmesini** seçin.
2. Bir vaka seçin ve ardından olay eylem **araç çubuğundaki** Araştırma için yükseltme düğmesini seçin.
3. Araştırma için **yükseltme iletişim kutusunda** , yeni kullanıcı soruşturması için bir ad girin. Gerekirse olayla ilgili notları girin ve İlerle'yi **seçin**.
4. Bildirim alanlarını gözden geçirebilirsiniz ve uygun şekilde güncelleştirebilirsiniz. Buraya girilen değerler, şablonda yer alan değerleri geçersiz kılar.
5. Kullanıcı **araştırma vakası** oluşturmak için Onayla'ya veya yeni **bir** kullanıcı soruşturması durumu oluşturmadan iletişim kutusunu kapatmak için İptal'e seçin.

Insider risk yönetimi durumu yeni bir kullanıcı soruşturması durumuna getirildikten sonra, ilk incelemede eKbulmaAdvanced  >  alanında yeni vakayı Microsoft 365 uyumluluk merkezi.

### <a name="run-automated-tasks-with-power-automate-flows-for-the-case"></a>Olayla ilgili otomatik Power Automate akışlarını kullanarak otomatik görevleri çalıştırma

Önerilen güvenlik Power Automate kullanarak risk tahminleri ve analistleri şunları yapmak için hızlı bir şekilde işlem tamamlar:

- İk veya işletmeden insider risk durumundaki bir kullanıcı hakkında bilgi talep edin
- Kullanıcının insider risk uyarısı olduğunda yöneticiye bildirme
- ServiceNow'da insider risk yönetimi durumu için kayıt oluşturma
- Insider risk ilkesine eklenen kullanıcıları bilgilendirme

Insider risk yönetimi durumuna yönelik Power Automate akışlarını çalıştırmak, yönetmek veya oluşturmak için:

1. Olay **eylemi araç** çubuğunda Otomatikleştir'i seçin. 
2. Çalıştıracak Power Automate seçin ve ardından Akışı **çalıştır'ı seçin**. 
3. Akış tamamlandıktan sonra Bitti'yi **seçin**.

Insider risk yönetimine Power Automate hakkında daha fazla bilgi edinmek için bkz[. Insider risk yönetimi ayarlarıyla çalışmaya başlama](insider-risk-management-settings.md#power-automate-flows-preview).

### <a name="view-or-create-a-microsoft-teams-team-for-the-case"></a>Olay için Microsoft Teams ekibi görüntüleme veya oluşturma

Ayarlar Microsoft Teams Insider risk yönetimiyle ilgili tümleştirme etkinleştirildiğinde, her uyarı onaylandıktan ve bir olay oluşturulduğunda Microsoft Teams bir ekip otomatik olarak oluşturulur. Risk risklerine sahipler ve analistler, Microsoft Teams araç çubuğundaki Ekip görüntüle'yi seçerek Microsoft Teams ekipte hemen açabilir ve  dava için doğrudan ekipte gezinebilirsiniz.

Microsoft Team tümleştirmesini etkinleştirmeden önce açılan vakalar için, risk tahminleri ve analistleri dava eylem araç çubuğunda Microsoft Teams bir ekip oluştur'u seçerek yeni bir **Microsoft Teams** ekibi oluşturabilir.

Bir olay çözülürse, ilişkili Microsoft Team otomatik olarak arşivlenir (gizli ve salt okunur olarak açılır).

Insider risk yönetimine Microsoft Teams fazla bilgi edinmek için bkz[. Insider risk yönetimi ayarlarıyla çalışmaya başlama](insider-risk-management-settings.md#microsoft-teams-preview).

### <a name="resolve-the-case"></a>Vakayı çözme

Risk analistleri ve güvenlik analistleri incelemelerini ve incelemelerini tamamlandıktan sonra, bir dava o anda davaya dahil olan tüm uyarılar üzerinde hareket etmek üzere çözümlenebilir. Bir vakayı çözümlemek bir çözüm sınıflandırması ekler, servis durumunu Kapalı olarak değiştirir ve çözüm eylemi nedenleri, Büyük/küçük harf notları panosunda servis sorunu notları kuyruğuna otomatik **olarak** eklenir. Vakalar şu şekilde çözülür:

- **İşte**: İlke eşleşme uyarılarının düşük risk, ciddi olmayan veya hatalı pozitif olarak değerlendirilen durumlar için sınıflandırma.
- **Onaylandı ilke** ihlali: İlke eşleşme uyarılarının riskli, önemli veya kötü niyetli amacın sonucu olarak değerlendirilen durumlar için sınıflandırma.

Bir sorunu çözmek için:

1. Giriş [Microsoft 365 uyumluluk merkezi](https://compliance.microsoft.com) **Insider risk yönetimi'ne gidin ve** Vakalar **sekmesini** seçin.
2. Bir vaka seçin ve ardından büyük **/küçük harf eylemi** araç çubuğundaki Büyük/küçük harfe çöz düğmesini seçin.
3. Vakayı **çöz iletişim** kutusunda, **vakanın çözüm sınıflandırması** seçmek için Farklı çöz açılan kutusunu seçin. Seçenekler, **Onaylandı veya** **Onaylandı ilke ihlalleridir**.
4. Büyük/ **düşük harfe** çöz iletişim kutusunda, Alınan eylem metin alanına çözüm **sınıflandırması nedenlerini** girin.
5. **Vakayı kapatmak** için Çöz'e veya sorunu **çözmeden** İletişim kutusunu kapatmayı iptal et'i seçin.
