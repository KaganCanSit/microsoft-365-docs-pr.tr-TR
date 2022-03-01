---
title: Insider risk yönetimi etkinliklerini araştırma
description: Ekip ekiplerde Insider risk yönetimi etkinliklerini inceleme Microsoft 365
keywords: Microsoft 365, insider riski, risk yönetimi, uyumluluk
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
ms.openlocfilehash: a34e876e1ea6f9be9004609daf8afeec97cc4fbb
ms.sourcegitcommit: 7fd1bcbd8246501029837e3ea92adea64c3406e1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/01/2022
ms.locfileid: "63010118"
---
# <a name="investigate-insider-risk-management-activities"></a>Insider risk yönetimi etkinliklerini araştırma

Riskli kullanıcı etkinliklerinin araştırilmesi, organizasyonunız için insider risklerini en aza indirmenin önemli bir ilk adımıdır. Bu riskler, Insider risk yönetimi ilkelerinden uyarı oluşturan etkinlikler veya ilkeler tarafından algılanan ancak kullanıcılar için hemen bir insider risk yönetimi uyarısı oluşturmamış etkinlikler olabilir. Kullanıcı etkinliği raporlarını (önizleme) kullanarak veya Uyarı **panosuyla bu tür etkinlikleri** **araştırabilirsiniz**.

## <a name="user-activity-reports-preview"></a>Kullanıcı etkinliği raporları (önizleme)

Kullanıcı etkinliği raporları, tanımlı bir süre boyunca belirli kullanıcıların etkinliklerini, insider risk yönetimi ilkesine geçici veya açık olarak atamak zorunda kalmadan incelemeniz için olanak sağlar. Insider risk yönetimi senaryolarının çoğunda, kullanıcılar ilkelerde açık olarak tanımlanırlar ve ilke uyarıları (olayları tetiklemeye bağlı olarak) ve etkinliklerle ilişkili risk puanları olabilir. Ancak bazı senaryolarda, bir ilkede açıkça tanımlanmamış kullanıcıların etkinliklerini incelemek iyi olabilir. Bu etkinlikler, kullanıcı ve olası riskli etkinlikler hakkında ipucu almış olduğunuz kullanıcılar veya normalde insider risk yönetimi ilkesine atanmamış kullanıcılar için olabilir.

Insider risk yönetimi sayfasında göstergeleri **yapılandırdıktan Ayarlar**, seçili göstergelerle ilişkilendirilmiş riskli etkinlikler için kullanıcı etkinliği algılanır. Kuruluş kapsamındaki kullanıcılar tarafından riskli etkinlikleri saptamak ve rapor etmek üzere kullanıcı etkinliği raporları için bir ilke yapılandırmanız gerekmektedir. Kullanıcı etkinliği raporlarına dahil edilen etkinlikler için etkinliklerin tetikleniyor olması gerekli değildir. Bu yapılandırma, kullanıcı için algılanan tüm etkinliğin, tetikleyen bir olayı olup olup bakılmaksızın veya bir uyarı oluşturduğuna bakılmaksızın gözden geçirilemez anlamına gelir. Raporlar, kullanıcı başına temelinde oluşturulur ve özel 90 günlük bir süre için tüm etkinlikleri içerebilir. Aynı kullanıcı için birden çok rapor desteklenmiyor.

Bir kullanıcının etkinliklerini inceledikten sonra, güvenlik açıkları tek tek etkinlikleri kapatarak sömey etkinlikleri yok sayma, rapora bağlantı paylaşma veya diğer parolalarla e-postayla gönderme ya da kullanıcıları geçici veya açık olarak insider risk yönetimi ilkesine atamayı seçme. Kullanıcı etkinliği raporları sayfasını görüntülemek için kullanıcıların *Insider Risk YönetimiNesnedenler* **rol grubuna atanmaları** gerekir.  

![Insider risk yönetimi kullanıcı etkinliği raporuna genel bakış.](../media/insider-risk-user-activity-report-overview.png)

Insider risk yönetimine genel **bakış** sayfasındaki **Kullanıcı etkinliğini** araştırma bölümünde Raporları yönet'i seçerek işe **başlatabilirsiniz** . Kullanıcının etkinliklerini görüntülemek için önce **Kullanıcı etkinliği raporu** oluştur'a tıklayın ve Yeni kullanıcı etkinliği **raporu bölmesinde aşağıdaki alanları** doldurun:

- **Kullanıcı**: Bir kullanıcıya ad veya e-posta adresine göre arama
- **Başlangıç tarihi**: Kullanıcı etkinliklerinin başlangıç tarihini seçmek için takvim denetimi kullanın.
- **Bitiş tarihi**: Kullanıcı etkinliklerinin bitiş tarihini seçmek için takvim denetimi kullanın. Seçilen bitiş tarihi, seçilen başlangıç tarihten sonra iki gün daha uzun olmalı ve seçilen başlangıç tarihinden itibaren 90 gün içinde olmalıdır.
Yeni raporların gözden geçirimaya hazır hale gelmeden önce normal olarak 10 saat içinde hazır hale bunlar olur. Rapor hazır olduğunda, Kullanıcı *etkinliği raporu sayfasının* **Durum sütununda** Rapor hazır'a bakın. Ayrıntılı raporu görüntülemek için bir kullanıcı seçin:

![Insider risk yönetimi kullanıcı etkinliği raporu.](../media/insider-risk-user-activity-report.png)

Seçili **kullanıcının Kullanıcı etkinliği** raporu, Kullanıcı etkinliği **ve Etkinlik gezgini** **sekmelerini** içerir:

- **Kullanıcı etkinliği**: Etkinlikleri araştırmak ve sıralı olarak oluşan olası etkinlikleri görüntülemek için bu grafik görünümünü kullanın. Bu sekme, tüm etkinliklerin geçmiş zaman çizelgesi, etkinlik ayrıntıları, kullanıcının olayda geçerli risk puanı, risk olaylarının dizisi ve yatırım çabalarına yardımcı olacak filtreleme denetimleri de içinde olmak üzere vakanın hızlı gözden geçir sekmesini etkinleştirmek üzere yapılandırılmıştır.
- **Etkinlik gezgini**: **Etkinlik gezgini sekmesi** , etkinlikler hakkında ayrıntılı bilgi sağlayan kapsamlı bir analitik araçla risk risklerini sağlar. Etkinlik gezginiyle, gözden geçirenler algılanan riskli etkinliğin zaman çizelgesini hızla gözden geçirebilirsiniz ve uyarılarla ilişkilendirilmiş tüm risk etkinliklerini tanımlayabilir ve filtreleyebilirsiniz. Etkinlik gezginini kullanma hakkında daha fazla bilgi edinmek için, bu *makalenin* devam bölümündeki Etkinlik gezgini bölümüne bakın.

## <a name="alert-dashboard"></a>Uyarı panosu

Insider risk yönetimi uyarıları, Insider risk yönetimi ilkelerde tanımlanan risk göstergeleri tarafından otomatik olarak oluşturulur. Bu uyarılar, uyumluluk analistlerine ve tahminlere geçerli risk durumunun tam olarak göz atlarını sağlar ve kuruluşlarının, bulunan riskler için değerlendirme ve işlemler gerçekleştirlerine olanak sağlar. Varsayılan olarak, ilkeler belirli miktarda düşük, orta ve yüksek önem düzeyi uyarıları üretir, ancak uyarı ses düzeyini kendi ihtiyaçlarına göre artırabilir veya azaltebilirsiniz.[](insider-risk-management-settings.md#alert-volume) Buna ek olarak, ilke [oluşturma aracıyla yeni bir](insider-risk-management-settings.md#indicator-level-settings-preview) ilke oluştururken ilke göstergeleri için uyarı eşiğini yapılandırabilirsiniz.

Uyarıların riskli etkinliklere yönelik ayrıntıları, bağlamı ve ilgili içeriği nasıl sağ çıkartır ve araştırma sürecinizi daha etkili hale nasıl getirebilirsiniz hakkında genel bir bakış için [Insider Risk](https://www.youtube.com/watch?v=KgmpxBLJLPI) Yönetimi Uyarıları Önceliği Deneyimi videosuna göz atabilirsiniz.

Insider riski **Uyarı panosu,** insider risk ilkeleri tarafından oluşturulan uyarıları görüntülemeye ve bu uyarılara karşı harekete geçebilirsiniz. Her rapor pencere öğesi, son 30 günlük bilgileri görüntüler.

- **Gözden geçirmesi gereken toplam** uyarılar: Uyarı önem derecesine göre çözümleme de içinde olmak üzere, gözden geçirmesi gereken uyarıların toplam sayısı ve önem düzeyi listelenir.
- **Son 30** gün içinde uyarıları açma: İlke tarafından oluşturulan toplam uyarı sayısı yüksek, orta ve düşük uyarı önem düzeyine göre sıralanmış, son 30 gün içinde eştir.
- **Uyarıları çözümlemek için ortalama süre**: Yararlı uyarı istatistiklerinin özeti:
  - Saat, gün veya ay olarak listelenen yüksek önem derecesi uyarılarını çözümlemek için ortalama süre.
  - Saat, gün veya ay olarak listelenen orta önem derecesi uyarılarını çözümlemek için ortalama süre.
  - Saat, gün veya ay olarak listelenen düşük önem düzeyi uyarılarını çözümlemek için ortalama süre.

![Insider risk yönetimi uyarı panosu.](../media/insider-risk-alerts-dashboard.png)

> [!NOTE]
> Insider risk yönetimi, risk araştırmanızı korumaya ve iyileştirmeye ve deneyimi gözden geçirmeye yardımcı olmak için yerleşik uyarı azaltmayı kullanır. Bu azaltma, hatalı yapılandırılmış veri bağlayıcıları veya DLP ilkeleri gibi ilke uyarılarının aşırı yüklenmesine neden olan sorunlar için karşıtlık sağlar. Sonuç olarak, kullanıcı için yeni uyarıların görüntülenmesinde gecikme olabilir.

## <a name="alert-status-and-severity"></a>Uyarı durumu ve önem düzeyi

Uyarıları aşağıdaki durumlardan biri için öncelik durumuna göre düzeltin:

- **Onaylandı**: Yeni veya mevcut bir vakaya onaylandı ve atanmış bir uyarı.
- **Reddedildi**: Triyaklık sürecinde bir uyarı " olarak yok sayıldı.
- **Gözden geçirmesi** gerekiyor: Değerlendirme eylemlerinin henüz gerçekleştirilememiş olduğu yeni bir uyarı.
- **Çözümlendi**: Kapalı ve çözülen bir davanın parçası olan uyarı.

Uyarı risk puanları çeşitli risk etkinliği göstergelerinden otomatik olarak hesaplanır. Bu göstergeler, risk etkinliğinin türünü, etkinlik tekrar sayısının ve sıklığını, kullanıcı risk etkinliğinin geçmişini ve etkinlik etkinliğinin ciddiliğini artırabilecek etkinlik risklerinin de eksini içerir. Uyarı risk puanı, her uyarı için bir risk önem düzeyine göre programlı bir atamaya devam ediyor ve özelleştirilene değil. Uyarılar artmış olarak kalır ve risk etkinlikleri uyarıya tahakkukya devam ederse, risk önem düzeyi artabilir. Risk analistleri ve tahminler, uyarı risk önem derecesine uygun olarak uyarıların önceliğinin kuruma aittir ve standartlara uygun olarak kullanabilir.

Uyarı risk önem düzeyi şu şekildedir:

- **Yüksek önem derecesi**: Uyarı için etkinlikler ve göstergeler önemli riskler ortaya ediyor. İlişkili risk etkinlikleri ciddi, yinelenen ve çekirdek öneme sahip diğer önemli risk etmenleridir.
- **Orta önem derecesi**: Uyarı için etkinlikler ve göstergeler orta derecede risk sağlar. İlişkili risk etkinlikleri ortalama, sık olur ve diğer risk etmenleri ile bir düzeyde bağıntıya sahip olur.
- **Düşük önem düzeyi**: Uyarının etkinlikleri ve göstergeleri küçük bir risk oluşturduğuna dikkat ediyor. İlişkili risk etkinlikleri küçük, seyrektir ve diğer önemli risk etmenlerini temel almak zorunda da değil.

## <a name="filter-alerts-on-the-alert-dashboard"></a>Uyarı panosunda uyarıları filtreleme

Kuruluşta etkin Insider risk yönetimi ilkelerinin sayısına ve türüne bağlı olarak, büyük bir uyarı kuyruğu gözden geçirmek zor olabilir. Uyarı filtrelerinin kullanımı, analistlerin ve tahminlerin çeşitli özniteliklere göre uyarıları sıralamanıza yardımcı olabilir. Uyarılar panosunda uyarıları **filtrelemek için** Filtre **denetimi'ne** seçin. Uyarıları bir veya birden çok öznitelike göre filtreleysiniz:

- **Durum**: Uyarı listesini filtrelemek için bir veya birden çok durum değeri seçin. Seçenekler Onaylandı, *Reddedildi*, *Gözden geçirilsin* *mi ve* *Çözümlendi seçenekleridir*.
- **Önem derecesi**: Uyarı listesini filtrelemek için bir veya daha fazla uyarı riski önem düzeyi seçin. Seçenekler *Yüksek, Orta* *ve* *Düşük'tür*.
- **Algılanan saat**: Uyarının ne zaman oluşturulduğunda başlangıç ve bitiş tarihlerini seçin. Bu filtre, başlangıç tarihinde SAAT 00:00 ile bitiş tarihinde UTC 00:00 arasındaki uyarıları arar. Belirli bir günün uyarılarını filtrelemek için, Başlangıç tarihi alanına günün tarihini ve Bitiş tarihi  alanına da sonraki **günün tarihini** girin.
- **İlke**: Seçili ilkeler tarafından oluşturulan uyarıları filtrelemek için bir veya birden çok ilke seçin.

## <a name="search-alerts-on-the-alert-dashboard"></a>Uyarı panosunda arama uyarıları

Belirli bir sözcüğün uyarı adını aramak için Arama **denetimi'ne** seçin ve aramak istediğiniz sözcüğü yazın. Arama sonuçları, aramada tanımlanan sözcüğü içeren tüm ilke uyarılarını görüntüler.

## <a name="dismiss-multiple-alerts-preview"></a>Birden çok uyarıyı (önizleme) yok sayma

Bu, analistlerin ve tahminlerin aynı anda birden çok uyarıyı hemen yok saymalarını sağlar. Uyarıları **yokla** komut çubuğu seçeneği panoda İncelemeniz gerekiyor durumu ile bir veya daha fazla uyarı  seçmenizi ve bu uyarıları değerlendirme işleminize uygun şekilde hemen yok saymanızı sağlar. Bir defada yok sayacak en çok 400 uyarı seçin.

Insider risk uyarısını yok say etmek için aşağıdaki adımları tamamlayın:

1. Daha [Microsoft 365 uyumluluk merkezi](https://compliance.microsoft.com) **Insider risk yönetimi'ne gidin** ve Uyarılar **sekmesini** seçin.
2. Uyarılar **panosunda**, yok etmek istediğiniz Gözden geçirme durumu bilgisinde *olan uyarıyı* (veya uyarıları) seçin.
3. Uyarılar komut çubuğunda Uyarıları yok **say'ı seçin**.
4. Uyarıları **gizle ayrıntı bölmesinde** , seçili uyarılarla ilişkilendirilmiş olan kullanıcı ve ilke ayrıntılarını gözden geçirebilirsiniz.
5. Uyarıları **açık olarak çözümlemek** için Uyarıları kapat'ı veya uyarıları kapatmadan ayrıntılar bölmesini kapatmak için İptal'i seçin.

## <a name="triage-alerts"></a>Triyaneleme uyarıları

Insider risk uyarılarını öncelik durumuna almak için aşağıdaki adımları tamamlayın:

1. Daha [Microsoft 365 uyumluluk merkezi](https://compliance.microsoft.com) **Insider risk yönetimi'ne gidin** ve Uyarılar **sekmesini** seçin.
2. Uyarılar **panosunda**, önceliklerini almak istediğiniz uyarıyı seçin.
3. Uyarı **ayrıntıları sayfasında** , uyarıyla ilgili bilgileri gözden geçirebilirsiniz; ayrıca uyarıyı onaylayabilir ve yeni bir vaka oluşturabilir, uyarıyı onaylayabilir ve mevcut bir vakaya ekleyebilir ya da uyarıyı yok sayabilirsiniz. Bu sayfa ayrıca, Yüksek, Orta veya Düşük olarak listelenmiş, uyarının geçerli durumunu ve uyarı önem düzeyi düzeyini de içerir. Uyarının önem düzeyi, önemli değilse zamanla artabilir veya azalacaktır.

    Uyarı ayrıntıları **sayfasındaki sekmeler** uyarı için daha fazla bilgi sağlar:
    - **Özet**: Bu sekme, uyarıyla ilgili genel bilgiler içerir.
        - **Tetikleyen olay nedir?**: İlkeden kullanıcının etkinliğine risk puanları atamayı başlatmayı istemiyle en son tetikleyen olayı görüntüler.
        - **Bu uyarıyı oluşturan etkinlik**: Uyarının oluşturulmaya neden olduğu etkinlik değerlendirme süresinde en üst risk etkinliğini ve ilke eşleşmesini görüntüler.
        - **Bu uyarıda etkinlikle ilgili risk** öngörüleri: Uyarıyla ilgili risk öngörülerinin sayısını görüntüler. Bazı örnekler, uyarının sıralı etkinlikler, kümülatif sızıntı etkinlik riski, izin verilmeyen etki alanlarına sahip etkinlikleri içeren etkinlikler, öncelik içeriği bulunan etkinlikleri veya kullanıcının sıra dışı etkinliklerini içerdiği durumlarla ilgili örneklerdir.
        - **Kullanıcı ayrıntıları**: Uyarıya atanan kullanıcı hakkında genel bilgileri görüntüler. Anonimleştirme etkinleştirildiyse, kullanıcı adı, e-posta adresi, diğer ad ve kuruluş alanları anonimleştirilmiştir.
        - **Uyarı ayrıntıları**: Uyarının oluşturulma süresini, uyarıyı oluşturan ilkeler listelenir ve uyarıdan oluşturulan durum listelenir. Yeni uyarılar için Olay **alanında Yok** görüntülenir.
        - **Algılanan içerik**: Uyarı için risk etkinlikleriyle ilişkili içeriği içerir ve önemli alanlara göre etkinlik olaylarını özetler. Etkinlik bağlantısı seçerek Etkinlik gezgini açılır ve etkinlikle ilgili daha fazla ayrıntı görüntülenir.
    - **Etkinlik gezgini**: Bu sekme Etkinlik **gezginini açar**. Daha fazla bilgi için, bu makalenin sonraki bölümüne bakın.

## <a name="retention-and-item-limits"></a>Bekletme ve öğe sınırları

Insider risk yönetimi uyarılarının yaşı, riskli etkinliği en aza indirmeye değer olarak çoğu kuruluşta azalarak devam ediyor. Buna karşılık, etkin durumlar ve ilişkili yapılar (uyarılar, içgörüler, etkinlikler) kuruluşlar için her zaman değerlidir ve otomatik bir son kullanma tarihi olmaması gerekir. Bu, etkin bir vakayla ilişkilendirilmiş herhangi bir kullanıcı için etkin durumdaki gelecekteki tüm uyarıları ve yapıları içerir.

Sınırlı geçerli değer sağlayan eski öğelerin sayısını en aza indirmeye yardımcı olmak için aşağıdaki bekletme ve sınırlar insider risk yönetimi uyarıları, vakaları ve kullanıcı etkinliği raporları için geçerlidir:

|**Öğe**|**Bekletme/Sınır**|
|:-------|:------------------|
| İhtiyaçlar gözden geçirme durumu ile uyarılar | Uyarı oluşturmadan 120 gün sonra otomatik olarak silindi |
| Etkin durumlar (ve ilişkili yapılar) | Belirsiz bekletme, asla süresi dolmaz |
| Çözülen vakalar (ve ilişkili yapıtlar) | Olay çözümünden 120 gün sonra otomatik olarak silinir |
| En fazla etkin vaka sayısı | 100 |
| Kullanıcı etkinlikleri raporları | Etkinlik algılamadan 120 gün sonra otomatik olarak silindi |

## <a name="activity-explorer"></a>Etkinlik gezgini

> [!NOTE]
> Bu özellik kurumda kullanılabilir olduktan sonra, olayları tetikleyen kullanıcılar için uyarı yönetim alanında etkinlik gezgini kullanılabilir.

Etkinlik gezgini, uyarılarla ilgili ayrıntılı bilgi sağlayan kapsamlı bir analitik araçla risk tahminlerini ve analistlerini sağlar. Etkinlik gezginiyle, gözden geçirenler algılanan riskli etkinliğin zaman çizelgesini hızla gözden geçirebilirsiniz ve uyarılarla ilişkilendirilmiş tüm risk etkinliklerini tanımlayabilir ve filtreleyebilirsiniz. 

Etkinlik gezgininde sütun bilgilerine ilişkin uyarıları filtrelemek için Filtre denetimi'ni seçin. Uyarıları, uyarının ayrıntılar bölmesinde listelenen bir veya birden çok öznitelike göre filtreleyebilirsiniz. Etkinlik gezgini, uzman ve analistlerin panoyu onlar için en önemli bilgilere odaklanmalarına yardımcı olmak için özelleştirilebilir sütunları da destekler.

Etkinlik kapsamını ve Risk içgörü filtrelerini kullanarak aşağıdaki alanlara yönelik etkinlikleri ve içgörüleri görüntüleyen ve sıralayın.

- **Etkinlik kapsamı filtreleri**: Kullanıcı için tüm puanlı etkinlikleri filtreler.
    - Bu kullanıcı için tüm puanlı etkinlikler
    - Bu uyarıda yalnızca puanlı etkinlik

- **Risk içgörü** filtreleri: Risk puanları atanan tüm ilkeler için geçerli etkinlik filtreleri.
    - Kümülatif filtreleme etkinlikleri
    - Öncelik içeriği olan olayı içerir
    - Izin verilmeyen etki alanına sahip olayı içerir
    - Sıralı etkinlikler
    - Alışılmış dışı etkinlik

![Insider risk yönetimi etkinlik gezginine genel bakış.](../media/insider-risk-activity-explorer.png)

Etkinlik **gezginini kullanmak için** aşağıdaki adımları tamamlayın:

1. Daha [Microsoft 365 uyumluluk merkezi](https://compliance.microsoft.com) **Insider risk yönetimi'ne gidin** ve Uyarılar **sekmesini** seçin.
2. Uyarılar **panosunda**, önceliklerini almak istediğiniz uyarıyı seçin.
3. Uyarılar ayrıntı **bölmesinde Genişletilmiş görünümü** **aç'ı seçin**.
4. Seçili uyarının sayfasında Etkinlik gezgini **sekmesini** seçin.

Etkinlik gezgininde etkinlikleri gözden geçirerek, tahminler ve analistler belirli bir etkinliği seçerek etkinlik ayrıntıları bölmesini açabilir. Bölmede, uyarı üç aydan fazla süre önce uyarılarını ve analistlerin kullanabileceği etkinlik hakkında ayrıntılı bilgiler görüntülenir. Ayrıntılı bilgiler uyarı için bağlam sağlar ve uyarıyı tetikleyen risk etkinliğinin tam kapsamını belirlemeye yardımcı olabilir.

Etkinlik zaman çizelgesinden bir etkinliğin olaylarını seçenlerken, gezginde görüntülenen etkinliklerin sayısı zaman çizelgesinde listelenen etkinlik etkinliklerinin sayısıyla eşleşmez. Bu farkın neden ortaya çıkabilir örnekleri:

- **Kümülatif filtreleme algılaması**: Kümülatif sızıntı algılaması olay günlüklerini analiz eder, ancak kümülatif kesinti riskini hesaplamak için benzer etkinliklerin de-yinelemesi içeren bir model uygular. Buna ek olarak, mevcut ilke veya ayarlarınız üzerinde değişiklik yaptınız, Etkinlik gezgininde görüntülenen etkinlik sayısında da fark olabilir. Örneğin, bir ilke oluşturulduktan ve etkinlik eşleşmeleri gerçekleştikten sonra izin verilen/izin verilmeyen etki alanlarında değişiklik yaptıktan sonra yeni dosya türü dışlamaları eklerseniz, kümülatif sızıntı algılama etkinlikleri ilke veya ayarlarda değişiklikten önceki sonuçlardan farklıdır. Kümülatif sızıntı algılama etkinlik toplamları, işlem yaptığınız sırada ilke ve ayarlar yapılandırmasına dayalıdır, ilke ve ayarlar değişikliklerinden önceki etkinlikleri dahil etmez
- **Dış alıcılara gönderilen e-postalar**: Dış alıcılara gönderilen e-postalarda etkinlik, gönderilen e-posta sayısına bağlı olarak bir risk puanı atanır ve bu da etkinlik olay günlükleri ile eşleşmez.

![Insider risk yönetimi etkinlik gezgini ayrıntıları.](../media/insider-risk-activity-explorer-details.png)

## <a name="create-a-case-for-an-alert"></a>Uyarı için vaka oluşturma

Uyarı gözden geçirildik ve triya göre sıralandı olarak, risk etkinliğini daha fazla araştırmak üzere yeni bir vaka oluşturabilirsiniz. Uyarı için olay oluşturmak için şu adımları izleyin:

1. Daha [Microsoft 365 uyumluluk merkezi](https://compliance.microsoft.com) **Insider risk yönetimi'ne gidin** ve Uyarılar **sekmesini** seçin.
2. Uyarılar **panosunda**, onaylamak istediğiniz uyarıyı seçin ve için yeni bir vaka oluşturun.
3. Uyarılar **ayrıntıları bölmesinde, Olay** oluşturmak için **EylemlerFirm** >  **uyarıları'& seçin**.
4. Uyarıyı **onayla ve Insider risk** durumu oluştur iletişim kutusunda, vaka için bir ad girin, katılımcı olarak eklemek istediğiniz kullanıcıları seçin ve uygun olduğunda açıklamalar ekleyin. Açıklamalar, büyük/küçük harfe not olarak otomatik olarak eklenir.
5. Yeni **bir vaka oluşturmak** için Büyük/küçük harf oluştur'a veya büyük **/** küçük harf oluşturmadan iletişim kutusunu kapatmak için İptal'e seçin.

Olay oluşturulduktan sonra, tahminler ve analistler vakayı yönetebilir ve buna göre eylemde  davranır. Daha fazla bilgi için [Insider risk yönetimi durum makalesine](insider-risk-management-cases.md) bakın.

## <a name="get-help-managing-your-insider-risk-alert-queue"></a>Insider risk uyarı kuyruğunızı yönetme ile ilgili yardım al

Insider risk uyarılarının gözden geçirilmesi, araştırilmesi ve bu uyarılara karşı harekete geçen etkili bir rol, organizasyonumda insider risklerini en aza indirmenin önemli parçalarıdır. Bu riskleri en aza indirmek için hızlıca işlem yapmak zamandan, paradan ve mevzuatlardan veya yasal düzenlemelerden tasarruf sağlar. Bu düzeltme sürecinde, uyarıları gözden geçirmenin ilk adımı birçok analist ve tahminci için en zor görev gibi görünebilir. Sizin koşullarınıza bağlı olarak, insider risk uyarılarını aşarak küçük engellerle karşı karşıyaymanıza neden olabilir. Aşağıdaki önerileri gözden geçirme ve uyarı gözden geçirme işlemini nasıl en iyi duruma getirme hakkında bilgi öğrenin.

### <a name="too-many-alerts-to-review"></a>Gözden geçirilene kadar çok uyarı var

Insider risk yönetimi ilkelerinizin neden olduğu uyarı sayısına boğ olmak can sıkıcı olabilir. Alınan uyarı ses düzeyi türüne bağlı olarak, basit adımlarla uyarı sayısına hızla değinebilirsiniz. Çok fazla geçerli uyarı alıyor veya çok fazla eski düşük riskli uyarınız olabilir. Aşağıdaki eylemleri gerçekleştirin:

- **Insider risk ilkelerinizi** ayarlama: Doğru insider risk ilkesi seçme ve yapılandırma, uyarıların türü ve hacmiyle ilgili en temel yöntemdir. Uygun ilke [şablonuyla başlayarak](insider-risk-management-policies.md#policy-templates) , göreceğiniz risk etkinlikleri ve uyarı türlerine odaklanmanıza yardımcı olur. Uyarı ses düzeyini etki başka faktörler, kapsam içinde yer alan kullanıcı ve grupların boyutu ile öncelikleri olan [içerikle kanalların boyutudur](insider-risk-management-policies.md#prioritize-content-in-policies). Bu alanları, organizasyonunız için en önemli olan alanlara geliştirmek için ilkeler ayarlamayı düşünmelisiniz.
- **Insider risk ayarlarınızı değiştirin**: Insider risk ayarları, alırsınız uyarı hacmini ve türlerini etki etki riski olan çok çeşitli yapılandırma seçenekleri içerir. Bunlar ilke göstergeleri [, gösterge eşikleri](insider-risk-management-settings.md#indicators) [ve ilke](insider-risk-management-settings.md#indicator-level-settings-preview) zaman [çerçeveleri ile ilgili ayarları içerir](insider-risk-management-settings.md#policy-timeframes). Belirli dosya türlerini [hariç](insider-risk-management-settings.md#intelligent-detections) tutmak için akıllı algılama seçeneklerini yapılandırmayı, etkinlik uyarıları ilkeleriniz tarafından bildirmeden önce minimum eşikleri tanımlamayı ve uyarı sesi yapılandırmasını daha düşük bir ayara değiştirmeyi göz önünde bulundurabilirsiniz.
- **Uyarıların uygun olduğunda toplu** olarak silinmesi: Analistlerin ve tahminlerin aynı anda birden çok uyarıyı hemen yok saymalarına yardımcı [](insider-risk-management-activities.md#dismiss-multiple-alerts-preview) olabilir. Bir defada yok sayacak en çok 400 uyarı seçin.

### <a name="not-familiar-with-the-alert-triage-process"></a>Uyarı üç aydan fazla bilgi sahibi değil

Insider risk yönetiminde uyarıları araştırma ve bu uyarılara karşı dikkatli olmak kolaydır:

1. **Uyarılar için [Gözden geçirmesi](insider-risk-management-activities.md#alert-dashboard) gerekiyor durumunun olduğu Uyarı panosunda gözden geçirme**. [Bu](insider-risk-management-activities.md#filter-alerts-on-the-alert-dashboard) uyarı türlerini *bulmak* için gerekirse uyarıya göre filtre uygulama Durumu.
2. **En yüksek öneme sahip uyarılarla başlama**. [Bu](insider-risk-management-activities.md#filter-alerts-on-the-alert-dashboard) uyarı türlerini *bulmak için* gerekirse Uyarı Önem Düzeyine göre filtrele.
3. **Daha fazla bilgi keşfetmek ve uyarı ayrıntılarını gözden geçirmek için bir uyarı seçin**. Gerekirse, Etkinlik [Gezgini'ni kullanarak ilişkili](insider-risk-management-activities.md#activity-explorer) riskli davranışın zaman çizelgesini gözden geçirmek ve uyarının tüm risk etkinliklerini tanımlamak için kullanın.
4. **Uyarıya göre hareket etmek**. Uyarıyı onaylayabilir [ve bu durumla ilgili bir](insider-risk-management-activities.md#create-a-case-for-an-alert) olay oluşturabilir ya da uyarıyı reddeder ve gidersiniz.

### <a name="resource-constraints-in-my-organization"></a>Kuruluşumda kaynak kısıtlamaları

Modern çalışma alanı kullanıcılarının çoğunlukla zamanıyla ilgili çok çeşitli sorumluluklara ve taleplere sahip olur. Kaynak kısıtlamalarına yardımcı olmak için gerçekleştirebilirsiniz:

- **Önce en yüksek risk uyarılarına odaklanın ve çabalarını takipin**. İlkelerinize bağlı olarak, risk azaltma çabalarınız üzerinde değişiklik dereceleri olan etkinlikleri yakalayarak uyarılar oluşturabiliyor ve bunu gerçekleştiriyor da olabilirsiniz. [Uyarıları önem derecesine](insider-risk-management-activities.md#filter-alerts-on-the-alert-dashboard) göre filtrele ve Yüksek önem *derecesi uyarılarını önceliklendirme* .
- **Kullanıcıları analist ve tahmin olarak attayabilirsiniz**. Insider risklerini gözden geçirme işleminin önemli bir parçası olarak doğru kullanıcıya doğru roller atanabilir. Uygun kullanıcıları *Insider Risk* Yönetimi Analistleri'ne ve *Insider Risk* Yönetimi Tahminleri rol gruplarına atayın.  
- **En yüksek risk etkinliklerini keşfetmenize yardımcı olması için otomatik Insider risk özelliklerini kullanın**. Insider risk yönetimi [dizi algılama ve](insider-risk-management-policies.md#sequence-detection-preview) [kümülatif sızıntı](insider-risk-management-policies.md#cumulative-exfiltration-detection-preview) algılama özellikleri, organizasyonum riskler için riskleri hızla bulamanıza yardımcı olabilir. İlkeleriniz için [risk puanınızı](insider-risk-management-settings.md#indicators), dosya [türü dışlamalarını](insider-risk-management-settings.md#file-type-exclusions)[, etki](insider-risk-management-settings.md#domains) alanlarını ve en düşük [gösterge eşiği ayarlarını](insider-risk-management-settings.md#indicator-level-settings-preview) ayarlamayı göz önünde bulundurabilirsiniz.
