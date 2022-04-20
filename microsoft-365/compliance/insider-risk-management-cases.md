---
title: Insider risk yönetimi durumları
description: Microsoft Purview'da insider risk yönetimi durumları hakkında bilgi edinin
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
ms.openlocfilehash: 687eb92693d3343fb0ef5b2392d4622d9af4bb9d
ms.sourcegitcommit: 45bc65972d4007b2aa7760d4457a0d2699f81926
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/20/2022
ms.locfileid: "64971957"
---
# <a name="insider-risk-management-cases"></a>Insider risk yönetimi durumları

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Vakalar, içeriden risk yönetiminin merkezidir ve ilkelerinizde tanımlanan risk göstergeleri tarafından oluşturulan sorunları derinlemesine araştırmanıza ve üzerinde işlem yapmanızı sağlar. Servis talepleri, kullanıcının uyumlulukla ilgili bir sorunu gidermek için başka bir eyleme ihtiyaç duyulduğu durumlarda uyarılardan el ile oluşturulur. Her servis talebinin kapsamı tek bir kullanıcı olarak belirlenmiştir ve mevcut bir servis talebine veya yeni bir servis talebine kullanıcı için birden çok uyarı eklenebilir.

Bir olayın ayrıntılarını araştırdıktan sonra şunları yaparak işlem yapabilirsiniz:

- kullanıcıya bildirim gönderme
- olayı iyi huylu olarak çözümleme
- servis talebini ServiceNow örneğinle veya bir e-posta alıcısıyla paylaşma
- eBulma (Premium) araştırması için olayı yükseltme

Insider risk yönetiminde vakaların nasıl araştırıldığını ve yönetildiğini gösteren bir genel bakış için [Insider Risk Yönetimi Araştırması ve Yükseltme videosunu](https://www.youtube.com/watch?v=UONUSmkRC8s) gözden geçirin.

## <a name="cases-dashboard"></a>Servis Talepleri panosu

Insider risk yönetimi **Servis Talepleri panosu** , servis taleplerini görüntülemenize ve üzerinde işlem yapmanızı sağlar. Panodaki her rapor pencere öğesi son 30 güne ilişkin bilgileri görüntüler.

- **Etkin vakalar**: Araştırma kapsamındaki etkin vakaların toplam sayısı.
- **Son 30 gün içindeki servis talepleri**: Oluşturulan toplam servis talebi sayısı, *Etkin* ve *Kapalı* durumuna göre sıralanır.
- **İstatistikler**: Etkin servis taleplerinin saat, gün veya ay olarak listelenen ortalama süresi.

Servis talebi kuyruğu, aşağıdaki servis talebi özniteliklerinin geçerli durumuna ek olarak kuruluşunuz için tüm etkin ve kapalı servis taleplerini listeler:

- **Servis talebi adı**: Bir uyarı onaylandığında ve servis talebi oluşturulduğunda tanımlanan servis talebi adı.  
- **Durum**: Servis talebinin durumu( *Etkin* veya *Kapalı*).
- **Kullanıcı**: Servis talebi için kullanıcı. Kullanıcı adları için anonimleştirme etkinleştirilirse anonimleştirilmiş bilgiler görüntülenir.
- **Büyük/küçük harf açma zamanı**: Servis talebi açıldığından bu yana geçen süre.
- **Toplam ilke uyarısı**: Servis talebine dahil edilen ilke eşleşmelerinin sayısı. Servis talebine yeni uyarılar eklenirse bu sayı artabilir.
- **Servis talebi son güncelleştirildi**: Servis talebi durumunda bir büyük/küçük harf notu veya değişiklik eklendikten sonra geçen süre.
- **Son güncelleştirme:** Olayı en son güncelleştiren insider risk yönetimi analistinin veya araştırmacının adı.

![Insider risk yönetimi Servis Talepleri panosu.](../media/insider-risk-cases-dashboard.png)

Arama **denetimini kullanarak** belirli bir metin için büyük/küçük harf adlarını arayın ve servis talebi filtresini kullanarak servis taleplerini aşağıdaki özniteliklere göre sıralayın:

- Durum
- Servis talebinin açıldığı saat, başlangıç tarihi ve bitiş tarihi
- Son güncelleştirme, başlangıç tarihi ve bitiş tarihi

## <a name="filter-cases"></a>Durumlara filtre uygulama

Kuruluşunuzdaki etkin insider risk yönetimi ilkelerinin sayısına ve türüne bağlı olarak, büyük bir servis talebi kuyruğunun gözden geçirilmesi zor olabilir. Olay filtrelerini kullanmak analistlerin ve araştırmacıların servis taleplerini çeşitli özniteliklere göre sıralamalarına yardımcı olabilir. **Servis Talepleri panosundaki** uyarıları filtrelemek için **Filtre** denetimini seçin. Servis taleplerini bir veya daha fazla özniteliğe göre filtreleyebilirsiniz:

- **Durum**: Servis talebi listesini filtrelemek için bir veya daha fazla durum değeri seçin. Seçenekler *Etkin* ve *Kapalı'dır*.
- **Servis talebinin açıldığı zaman: Servis talebinin** ne zaman açıldığına ilişkin başlangıç ve bitiş tarihlerini seçin.
- **Son güncelleştirme**: Servis talebinin ne zaman güncelleştirildiğinin başlangıç ve bitiş tarihlerini seçin.

## <a name="investigate-a-case"></a>Bir olayı araştırma

Insider risk yönetimi uyarılarına yönelik daha ayrıntılı araştırma, doğru düzeltici eylemler gerçekleştirme açısından kritik öneme sahiptir. Insider risk yönetimi örnekleri, kullanıcı riski etkinlik geçmişini, uyarı ayrıntılarını, risk olaylarının sırasını daha ayrıntılı incelemeye ve risklere maruz kalan içeriği ve iletileri keşfetmeye yönelik merkezi yönetim aracıdır. Risk analistleri ve araştırmacıları ayrıca gözden geçirme geri bildirimlerini ve notlarını merkezileştirmek ve olay çözümünü işlemek için örnekleri kullanır.

Bir servis talebi seçildiğinde olay yönetimi araçları açılır ve analistlerin ve araştırmacıların vakaların ayrıntılarını incelemesine olanak tanır.

### <a name="case-overview"></a>Servis talebine genel bakış

**Olaya genel bakış** sekmesi, risk analistleri ve araştırmacıları için servis talebi ayrıntılarını özetler. **Bu durum hakkında** alanında aşağıdaki bilgileri içerir

- **Durum**: Etkin veya Kapalı durumdaki servis talebinin geçerli durumu.
- **Olay oluşturma tarihi**: Servis talebinin oluşturulduğu tarih ve saat.
- **Kullanıcının risk puanı**: Kullanıcının servis talebi için geçerli hesaplanan risk düzeyi. Bu puan 24 saatte bir hesaplanır ve kullanıcıyla ilişkili tüm etkin uyarılardan alınan uyarı riski puanlarını kullanır.
- **E-posta**: Kullanıcının servis talebi için e-posta diğer adı.
- **Kuruluş veya departman**: Kullanıcının atandığı kuruluş veya departman.
- **Yönetici adı**: Kullanıcının yöneticisinin adı.
- **Yönetici e-postası**: Kullanıcının yöneticisinin e-posta diğer adı.

![Insider risk yönetimi servis talebi ayrıntıları.](../media/insider-risk-case-details.png)

**Olaya genel bakış** sekmesi, servis talebiyle ilişkili ilke eşleştirme uyarıları hakkında aşağıdaki bilgileri içeren bir **Uyarılar** bölümü de içerir:

- **İlke eşleşmeleri**: Kullanıcı etkinliği için eşleştirme uyarılarıyla ilişkili insider risk yönetimi ilkesinin adı.
- **Durum**: Uyarının durumu.
- **Önem Derecesi**: Uyarının önem derecesi.
- **Algılanan zaman**: Uyarının oluşturulmasından bu yana geçen süre.

### <a name="alerts"></a>Uyarılar

**Uyarılar** sekmesi, servis talebine dahil edilen geçerli uyarıları özetler. Mevcut bir servis talebine yeni uyarılar eklenebilir ve atandıkları sırada **Uyarı** kuyruğuna eklenirler. Aşağıdaki uyarı öznitelikleri kuyrukta listelenir:

- Durum
- Önem
- Algılanan süre

**Uyarı ayrıntı** sayfasını görüntülemek için kuyruktan bir uyarı seçin.

Belirli bir metin için uyarı adlarını aramak için arama denetimini kullanın ve servis taleplerini aşağıdaki özniteliklere göre sıralamak için uyarı filtresini kullanın:

- Durum
- Önem
- Algılanan saat, başlangıç tarihi ve bitiş tarihi

Uyarıları aşağıdakiler gibi çeşitli özniteliklere göre filtrelemek için filtre denetimini kullanın:

- **Durum**: Uyarı listesini filtrelemek için bir veya daha fazla durum değeri seçin. Seçenekler *Onaylandı*, *Kapatıldı*, *Gözden geçirilmesi gerekiyor* ve *Çözümlendi şeklindedir*.
- **Önem derecesi**: Uyarı listesini filtrelemek için bir veya daha fazla uyarı riski önem düzeyi seçin. Seçenekler *Yüksek*, *Orta* ve *Düşük'tir*.
- **Algılanan zaman**: Uyarının oluşturulduğu zaman için başlangıç ve bitiş tarihlerini seçin.
- **İlke**: Seçili ilkeler tarafından oluşturulan uyarıları filtrelemek için bir veya daha fazla ilke seçin.

### <a name="user-activity"></a>Kullanıcı etkinliği

**Kullanıcı etkinliği** sekmesi, risk analistlerinin ve araştırmacıların etkinlik ayrıntılarını gözden geçirmesine ve risk uyarıları ve vakalarıyla ilişkili tüm etkinliklerin görsel bir gösterimini kullanmasına olanak tanır. Örneğin, uyarı önceliklendirme sürecinin bir parçası olarak analistlerin daha fazla ayrıntı için servis talebiyle ilişkili tüm risk etkinliklerini gözden geçirmeleri gerekebilir. Böyle durumlarda risk araştırmacıları, olayla ilişkili etkinliklerin genel kapsamını anlamanıza yardımcı olmak için kullanıcı etkinliği ayrıntılarını ve kabarcık grafiğini gözden geçirebilir. Kullanıcı etkinlik grafiği hakkında daha fazla bilgi için [Insider risk yönetimi etkinlikleri](insider-risk-management-activities.md#user-activity) makalesine bakın.

### <a name="activity-explorer-preview"></a>Etkinlik gezgini (önizleme)

**Etkinlik gezgini** sekmesi, risk analistlerinin ve araştırmacıların risk uyarılarıyla ilişkili etkinlik ayrıntılarını gözden geçirmesine olanak tanır. Örneğin, olay yönetimi eylemleri kapsamında araştırmacıların ve analistlerin daha fazla ayrıntı için olayla ilişkili tüm risk etkinliklerini gözden geçirmeleri gerekebilir. **Etkinlik gezgini** ile gözden geçirenler algılanan riskli etkinliğin zaman çizelgesini hızla gözden geçirebilir ve uyarılarla ilişkili tüm risk etkinliklerini tanımlayıp filtreleyebilir.

Etkinlik gezgini hakkında daha fazla bilgi için [Insider risk yönetimi etkinlikleri](insider-risk-management-activities.md#activity-explorer) makalesine bakın.

### <a name="content-explorer"></a>İçerik gezgini

**İçerik gezgini** sekmesi, risk araştırmacılarının risk uyarılarıyla ilişkili tüm dosyaların ve e-posta iletilerinin kopyalarını gözden geçirmesine olanak tanır. Örneğin, bir kullanıcı SharePoint Online'dan yüzlerce dosya indirdiğinde ve etkinlik bir ilke uyarısı tetiklediğinde bir uyarı oluşturulursa, uyarı için indirilen tüm dosyalar yakalanır ve özgün depolama kaynaklarından insider risk yönetimi olayına kopyalanır.

İçerik gezgini, temel ve gelişmiş arama ve filtreleme özelliklerine sahip güçlü bir araçtır. İçerik gezginini kullanma hakkında daha fazla bilgi edinmek için bkz [. Insider risk yönetimi İçerik gezgini](insider-risk-management-content-explorer.md).

![Insider risk yönetimi olayı İçerik gezgini.](../media/insider-risk-content-explorer.png)

### <a name="case-notes"></a>Olay notları

**Olay notları** sekmesi, risk analistlerinin ve araştırmacıların olayla ilgili çalışmaları hakkında yorum, geri bildirim ve içgörü paylaştığı yerdir. Notlar bir servis talebine kalıcı eklemelerdir ve not kaydedildikten sonra düzenlenemez veya silinemez. Uyarıdan bir servis talebi oluşturulduğunda Uyarıyı **onayla ve iç risk olayı oluştur** iletişim kutusuna girilen açıklamalar otomatik olarak servis talebi notu olarak eklenir.

Servis talebi notları panosu, notu oluşturan kullanıcının notlarını ve not kaydedildikten sonra geçen süreyi görüntüler. Servis talebi notu metin alanında belirli bir anahtar sözcüğü aramak için servis talebi panosundaki **Ara** düğmesini kullanın ve belirli bir anahtar sözcük girin.

Bir servis talebine not eklemek için:

1. [Microsoft Purview uyumluluk portalında](https://compliance.microsoft.com) **Insider risk yönetimi'ne** gidin ve **Servis Talepleri** sekmesini seçin.
2. Bir servis talebi seçin ve ardından **Servis Talebi notları** sekmesini seçin.
3. **Büyük/küçük harf notu ekle'yi** seçin.
4. **Servis talebi notu ekle** iletişim kutusunda, servis talebi için notunuzu yazın. Notu servis talebine eklemek için **Kaydet'i** veya notu servis talebine kaydetmeden Kapatmayı **iptal et'i** seçin.

### <a name="contributors"></a>Katkıda bulunan

Olaydaki **Katkıda Bulunanlar** sekmesi, risk analistlerinin ve araştırmacıların olaya başka gözden geçirenler ekleyebileceği yerdir. Varsayılan olarak, **Insider Risk Management Analysts** ve **Insider Risk Management Investigators rollerini** atamış olan tüm kullanıcılar, etkin ve kapalı her olay için katkıda bulunanlar olarak listelenir. Yalnızca **Insider Risk Yönetimi Araştırmacıları** rolüne atanan kullanıcıların İçerik gezginindeki dosyaları ve iletileri görüntüleme izni vardır.

Bir kullanıcıyı katkıda bulunan olarak ekleyerek bir servis talebine geçici erişim verilebilir. Katkıda bulunanlar, aşağıdakiler dışında belirli bir servis talebi üzerinde tüm servis talebi yönetimi denetimine sahiptir:

- Uyarıları onaylama veya kapatma izni
- Vakalar için katkıda bulunanları düzenleme izni
- İçerik gezgininde dosya ve iletileri görüntüleme izni

Bir servis talebine katkıda bulunan eklemek için:

1. [Microsoft Purview uyumluluk portalında](https://compliance.microsoft.com) **Insider risk yönetimi'ne** gidin ve **Servis Talepleri** sekmesini seçin.
2. Bir servis talebi seçin ve katkıda **bulunanlar** sekmesini seçin.
3. **Katkıda bulunan ekle'yi** seçin.
4. **Katkıda bulunan ekle** iletişim kutusunda, eklemek istediğiniz kullanıcının adını yazmaya başlayın ve ardından önerilen kullanıcı listesinden kullanıcıyı seçin. Bu liste, kiracı aboneliğinizin Azure Active Directory oluşturulur.
5. Kullanıcıyı katkıda bulunan olarak eklemek için **Ekle'yi** seçin veya **İptal'i** seçerek kullanıcıyı katkıda bulunan olarak eklemeden iletişim kutusunu kapatın.

## <a name="case-actions"></a>Servis talebi eylemleri

Risk araştırmacıları olayın önem derecesine, kullanıcının risk geçmişine ve kuruluşunuzun risk yönergelerine bağlı olarak birkaç yöntemden birinde bir olay üzerinde işlem yapabilir. Bazı durumlarda, kuruluşunuzun diğer alanlarıyla işbirliği yapmak ve risk etkinliklerini daha ayrıntılı incelemek için bir olayı bir kullanıcıya veya veri araştırmasına aktarmanız gerekebilir. Insider risk yönetimi, uçtan uca çözüm yönetimi konusunda size yardımcı olmak için diğer Microsoft Purview çözümleriyle sıkı bir şekilde tümleşiktir.

### <a name="send-email-notice"></a>E-posta bildirimi gönderme

Çoğu durumda, iç risk uyarıları oluşturan kullanıcı eylemleri yanlışlıkla veya yanlışlıkla olur. Kullanıcıya e-posta yoluyla anımsatıcı bildirimi göndermek, olay incelemesini ve eylemi belgelemenin etkili bir yöntemidir ve kullanıcılara şirket ilkelerini anımsatmak veya onları daha yenileyici eğitime yöneltmek için bir yöntemdir. Bildirimler, insider risk yönetimi [altyapınız için oluşturduğunuz bildirim şablonlarından](insider-risk-management-notices.md) oluşturulur.

Bir kullanıcıya e-posta bildirimi göndermenin * sorunu _Closed* olarak **çözmediğini** unutmayın. Bazı durumlarda, kullanıcıya yeni bir servis talebi açmadan daha fazla risk etkinliği araması için bildirim gönderdikten sonra servis talebini açık bırakmak isteyebilirsiniz. Bildirim gönderdikten sonra bir olayı çözmek istiyorsanız, bildirim gönderdikten sonra servis **talebi çözümle** adımını izleme adımı olarak seçmeniz gerekir.

Servis talebine atanan kullanıcıya bildirim göndermek için:

1. [Microsoft Purview uyumluluk portalında](https://compliance.microsoft.com) **Insider risk yönetimi'ne** gidin ve **Servis Talepleri** sekmesini seçin.
2. Bir servis talebi seçin ve servis talebi eylem araç çubuğunda **e-posta bildirimi gönder** düğmesini seçin.
3. **E-posta bildirimi gönder** iletişim kutusunda Bildirim **şablonu seçin** açılan denetimini seçerek bildirimin bildirim şablonunu seçin. Bu seçim, bildirimdeki diğer alanları önceden doldurur.
4. Bildirim alanlarını gözden geçirin ve uygun şekilde güncelleştirin. Buraya girilen değerler şablondaki değerleri geçersiz kılar.
5. Bildirimi kullanıcıya göndermek için **Gönder'i** veya **İptal'i** seçerek bildirimi kullanıcıya göndermeden iletişim kutusunu kapatın. Gönderilen tüm bildirimler Servis Talebi notları panosundaki servis **talebi notları** kuyruğuna eklenir.

### <a name="escalate-for-investigation"></a>Araştırma için yükseltme

Kullanıcının risk etkinliği için ek yasal inceleme gerektiren durumlarda kullanıcı araştırması için olayı yükseltin. Bu yükseltme, Microsoft 365 kuruluşunuzda yeni bir Microsoft Purview eKeşif (Premium) olayı açar. eBulma (Premium), kuruluşunuzun iç ve dış yasal araştırmalarına yanıt veren içeriği korumak, toplamak, gözden geçirmek, analiz etmek ve dışarı aktarmak için uçtan uca bir iş akışı sağlar. Ayrıca, yasal ekibinizin bir olaya dahil olan koruyucularla iletişim kurmak için yasal tutma bildirimi iş akışının tamamını yönetmesine olanak tanır. Bir iç risk yönetimi olayından oluşturulan bir eBulma (Premium) olayında bir gözden geçireni koruyucu olarak atamak, hukuk ekibinizin uygun eylemi gerçekleştirmesine ve içerik korumayı yönetmesine yardımcı olur. eBulma (Premium) durumları hakkında daha fazla bilgi edinmek için bkz. [Microsoft Purview eKeşif'e Genel Bakış (Premium)](overview-ediscovery-20.md).

Bir olayı kullanıcı araştırmasına ilerletmek için:

1. [Microsoft Purview uyumluluk portalında](https://compliance.microsoft.com) **Insider risk yönetimi'ne** gidin ve **Servis Talepleri** sekmesini seçin.
2. Bir servis talebi seçin ve ardından servis talebi eylem araç çubuğunda **araştırma için yükselt** düğmesini seçin.
3. **Araştırma için yükselt** iletişim kutusunda, yeni kullanıcı araştırması için bir ad girin. Gerekirse servis talebiyle ilgili notlar girin ve **Yükselt'i** seçin.
4. Bildirim alanlarını gözden geçirin ve uygun şekilde güncelleştirin. Buraya girilen değerler şablondaki değerleri geçersiz kılar.
5. Kullanıcı araştırma olayı oluşturmak için **Onayla'yı** seçin veya yeni bir kullanıcı araştırma olayı oluşturmadan iletişim kutusunu kapatmak için **İptal'i** seçin.

Insider risk yönetimi olayı yeni bir kullanıcı araştırma olayına yükseltildikten sonra, yeni olayı Microsoft Purview uyumluluk portalındaki **eKeşifGelişmiş** >  alanında gözden geçirebilirsiniz.

### <a name="run-automated-tasks-with-power-automate-flows-for-the-case"></a>Servis talebi için Power Automate akışlarıyla otomatik görevleri çalıştırma

Önerilen Power Automate akışlarını kullanarak risk araştırmacıları ve analistler aşağıdaki işlemleri hızla gerçekleştirebilir:

- şirket içi risk durumundaki bir kullanıcı hakkında İk'dan veya işletmeden bilgi isteme
- Kullanıcının içeriden risk uyarısı olduğunda yöneticiye bildirme
- ServiceNow'da insider risk yönetimi olayı için kayıt oluşturma
- Insider risk ilkesine eklendiklerinde kullanıcılara bildirme

Insider risk yönetimi olayı için Power Automate akışları çalıştırmak, yönetmek veya oluşturmak için:

1. Servis talebi eylem araç çubuğunda **Otomatikleştir'i** seçin. 
2. Çalıştırılacak Power Automate akışını seçin ve ardından **Akışı çalıştır'ı** seçin. 
3. Akış tamamlandıktan sonra **Bitti'yi** seçin.

Insider risk yönetimine yönelik Power Automate akışları hakkında daha fazla bilgi edinmek için bkz. [Insider risk yönetimi ayarlarını kullanmaya başlama](insider-risk-management-settings.md#power-automate-flows-preview).

### <a name="view-or-create-a-microsoft-teams-team-for-the-case"></a>Servis talebi için bir Microsoft Teams ekibi görüntüleme veya oluşturma

Ayarlarda insider risk yönetimi için Microsoft Teams tümleştirme etkinleştirildiğinde, bir uyarı onaylandığında ve servis talebi oluşturulduğunda otomatik olarak bir Microsoft Teams ekibi oluşturulur. Risk araştırmacıları ve analistleri Microsoft Teams hızla açabilir ve servis talebi eylem araç çubuğundan Ekibi görüntüle Microsoft Teams seçerek servis talebi için doğrudan **takıma** gidebilir.

Microsoft Team tümleştirmesini etkinleştirmeden önce açılan servis talepleri için risk araştırmacıları ve analistler, servis talebi eylem araç çubuğunda Microsoft Teams **ekip oluştur'u** seçerek bir servis talebi için yeni bir Microsoft Teams ekibi oluşturabilir.

Bir servis talebi çözümlendiğinde, ilişkili Microsoft Ekibi otomatik olarak arşivlenir (gizlenir ve salt okunur duruma gelir).

Insider risk yönetimi Microsoft Teams hakkında daha fazla bilgi edinmek için bkz. [Insider risk yönetimi ayarlarını kullanmaya başlama](insider-risk-management-settings.md#microsoft-teams-preview).

### <a name="resolve-the-case"></a>Servis talebini çözme

Risk analistleri ve araştırmacılar incelemelerini ve araştırmalarını tamamladıktan sonra, şu anda olaya dahil olan tüm uyarılar üzerinde işlem yapmak için bir dava çözümlenebilir. Bir servis talebini çözümlemek bir çözüm sınıflandırması ekler, servis talebi durumunu *Kapalı* olarak değiştirir ve çözüm eylemi nedenleri **servis talebi notları** panosundaki servis talebi notları kuyruğuna otomatik olarak eklenir. Servis talepleri şunlardan biri olarak çözümlenir:

- **Zararsız**: İlke eşleştirme uyarılarının düşük riskli, ciddi olmayan veya hatalı pozitif olarak değerlendirildiği durumlar için sınıflandırma.
- **Onaylanan ilke ihlali: İlke** eşleştirme uyarılarının riskli, ciddi veya kötü amaçlı bir amaç sonucu olarak değerlendirildiği durumlar için sınıflandırma.

Bir sorunu çözmek için:

1. [Microsoft Purview uyumluluk portalında](https://compliance.microsoft.com) **Insider risk yönetimi'ne** gidin ve **Servis Talepleri** sekmesini seçin.
2. Bir servis talebi seçin, ardından servis talebi eylem araç çubuğunda servis **talebini çöz** düğmesini seçin.
3. **Servis talebini çözümle** iletişim kutusunda, servis talebi için çözüm sınıflandırmasını seçmek üzere **Farklı çözümle** açılan denetimini seçin. Seçenekler **Zararsız** veya **Onaylanan ilke ihlalidir**.
4. **Servis talebini çöz** iletişim kutusunda, **Eylem gerçekleştirilen** metin alanına çözüm sınıflandırmasının nedenlerini girin.
5. Olayı kapatmak için **Çözümle'yi** seçin veya **İptal'i** seçerek servis talebini çözmeden iletişim kutusunu kapatın.
