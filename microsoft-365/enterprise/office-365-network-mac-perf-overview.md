---
title: Ağ Merkezi'nde Microsoft 365 Yönetici bağlantısı
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 12/06/2021
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- m365initiative-coredeploy
description: Microsoft 365 Yönetici Merkezi'nde ağ bağlantısına genel bakış
ms.openlocfilehash: ce0878037a3741ad440d0bddeefcca86b7b62f74
ms.sourcegitcommit: 39838c1a77d4e23df56af74059fb95970223f718
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2022
ms.locfileid: "63010776"
---
# <a name="network-connectivity-in-the-microsoft-365-admin-center"></a>Ağ Merkezi'nde Microsoft 365 Yönetici bağlantısı

Yönetim Microsoft 365 Yönetici şimdi kiracınız tarafından toplanan toplanan ağ bağlantısı ölçümlerini Microsoft 365 ve kiracınız içinde yalnızca yönetim kullanıcıları tarafından  görüntülemeye hazır.

> [!div class="mx-imgBorder"]
> ![Ağ bağlantısı test aracı.](../media/m365-mac-perf/m365-mac-perf-admin-center.png)

**Ağ değerlendirmeleri ve** **ağ içgörüleri**, Durum Bilgileri Microsoft 365 Yönetici **Merkezi'nde | Ağ bağlantısı**.

> [!div class="mx-imgBorder"]
> ![Ağ performansı sayfası.](../media/m365-mac-perf/m365-mac-perf-page-nav.png)

>[!NOTE]
>Yönetim Merkezi'nde ağ bağlantısı WW Ticari ve Almanya'daki kiracıları destekler ancak Orta, GCC Yüksek, DoD GCC Çin'de bulunan kiracıları desteklemez.

Ağ performansı sayfasına ilk kez göz atsanız, genel ağ performansının haritasını, tüm kiracıyı kapsamış olan ağ değerlendirmesini, kullanıcılarının yüzdesini yerinde uzaktan çalışan kullanıcılarının yüzdesini ve daha fazla araştırma yapmak üzere geçerli sorunların listesini görmek için konumlarınızı yapılandırmanız gerekir. Genel bakış bölmesinde, belirli ağ performansı ölçümlerini ve sorunları konuma göre görmek için detaya inebilirsiniz. Daha fazla bilgi için Bkz[. Merkezi'nde ağ Microsoft 365 Yönetici genel bakış](#network-connectivity-overview-in-the-microsoft-365-admin-center).

Bu özellik için, kuruluş adına genel önizlemeye katılmanız istenebilirsiniz. Kabul genellikle hemen gerçekleşir ve bundan sonra ağ bağlantısı sayfasını görebilirsiniz.

Ağ bağlantısı sayfasına erişmek için, ağ bağlantısının içinde kuruluşun yöneticisi Microsoft 365. Rapor Okuyucusu yönetim rolü, bu bilgilere okuma erişimine sahip olacak. Konumları ve ağ bağlantısının diğer öğelerini yapılandırmak için, yöneticinin Hizmet Desteği Yöneticisi rolüne sahip olması gerekir.

## <a name="pre-requisites-for-network-connectivity-assessments-to-appear"></a>Ağ bağlantısı değerlendirmeleri için önkkullar

Kullanmaya başlarken, Windows Konum Hizmetleri kullanan cihazlardan otomatik olarak veri toplamak için konum kabul ayarınızı seçin, konum verilerini eklemek veya karşıya yüklemek için Konumlar listeniz'e gidin veya ofis konumlarından Microsoft 365 ağ bağlantısı testini çalıştırın. Kuruluş genelinde ağ bağlantısı değerlendirilirken belirli ofis konumlarında ağ tasarım iyileştirmeleri yapılması gerekir. Her ofis konumu için ağ bağlantısı bilgileri, bu konumlar belirlenene kadar sağlanır. Ofis konumlardan ağ değerlendirmeleri almak için üç seçenek vardır:

### <a name="1-enable-windows-location-services"></a>1. Konum Windows'i etkinleştirme

Bu seçenek için, önkulları destekleyen her ofis konumda en az iki bilgisayar çalıştırabilirsiniz. OneDrive sürümün Windows her bilgisayara güncel ve yüklü olması gerekir. Yeni sürümler hakkında OneDrive için bkz. [OneDrive bakın](https://support.office.com/article/onedrive-release-notes-845dcf18-f921-435e-bf28-4e24b95e5fc0). Ağ ölçülerin yakın gelecekte diğer istemci Office 365 eklenebilir.

Windows Makinelerde Konum Hizmeti'nin izinli olması gerekir. Bunu test etmek için **Haritalar çalıştırabilirsiniz**. Özelliği olan tek bir makinede **etkinleştirilebilir Ayarlar | Gizlilik | Uygulamaların** konumunuza _erişmesine izin ver ayarının etkinleştirildikten_ sonra konumu. Windows Konum Hizmetleri onayı, _LetAppsAccessLocation_ ayarıyla MDM veya Grup İlkesi kullanılarak bilgisayarlara dağıtılabilir.

Yönetim Merkezi'nde konum eklemenize gerek yok, çünkü bunlar şehir çözünürlüğünde otomatik olarak tanımlandıklarından, bu yöntemle konum eklemenize gerek olmaz. Aynı şehir içinde birden çok ofis konumu Konum Hizmetleri'nin kullanımı Windows gösterilmez. Konum bilgileri en yakın 300 metreye 300 metre yuvarlanarak daha hassas konum bilgilerine erişilemez.

Makinelerde ethernet Wi-Fi yerine ağ bağlantısı olması gerekir. Ethernet kablosu olan makinelerde doğru konum bilgileri olmayabilir.

Bu önkullar karşı ondan 24 saat sonra ölçü örnekleri ve ofis konumları görünmeye başlayacaktır.

### <a name="2-add-locations-and-provide-lan-subnet-information"></a>2. Konum ekleme ve LAN alt ağı bilgilerini sağlama

Bu seçenek için konum Windows ya da hizmet Wi-Fi gerekli değildir. OneDrive sürümünüz Windows güncel olmalı ve bu konumda en az bir bilgisayara yüklü olmalıdır.

Konumlar sayfasına konumlar da eklemek veya bu **konumları bir** CSV dosyasından içeri aktarın. Eklenen konumlar office LAN alt ağ bilginizi de içermeli. Konum ekleme veya düzenleme iletişim kutusunda bir dizi LAN alt ağı ve bir dizi genel çıkış IP alt ağı belirtebilirsiniz. LAN alt ağları gereklidir ve sonuçların göster olması için, bunlardan biri alınan bir ağ değerlendirmesinde LAN alt ağ özniteliğiyle eşleşmesi gerekir. Süper ağlar destek desteklemez, bu nedenle LAN alt ağın tam olarak eşleşmesi gerekir.

LAN alt ağlarının çoğunlukla RFC1918'da tanımlandığı gibi özel IP adresi aralıkları olduğunu, örneğin genel IP adreslerinin LAN alt ağları olarak kullanımının yanlış olma olasılığı olduğunu unutmayın. İletişim kutusunda, seçimnizi yapacak son ağ değerlendirme testlerinde görülen LAN alt ağlarının önerileri görüntülenir.

Genel çıkış IP adresleri eklersiniz, bunlar ikincil farklıtıcı olarak kullanılır ve aynı LAN alt ağı IP adresi aralıklarını kullanan birden çok site varsa bunların amacıdır. Test sonuçlarınızı göstermek için, genel çıkış IP adresi aralıklarını boş bırakarak başlamanız gerekir. Bir test sonucu dahil edilirse, hem LAN alt ağı IP adresi aralıklarından hem de genel çıkış IP adresi aralıklarından birini eşleşmesi gerekir.

Bu seçenek, bir şehir içinde tanımlanmış birden fazla ofislere sahip olmak için size olanak sağlar.

İstemci makinelerinden gelen tüm test ölçüleri, girdiğiniz ofis konumu ayrıntılarıyla ilişkili LAN alt ağı bilgilerini içerir. Bu önkullar karşı ondan 24 saat sonra ölçü örnekleri ve ofis konumları görünmeye başlayacaktır.

### <a name="3-manually-gather-test-reports-with-the-microsoft-365-network-connectivity-test-tool"></a>3. Test raporlarını el ile Microsoft 365 bağlantı test aracıyla toplama

Bu seçenek için her konumdan bir kişiyi tanımlamamız gerekir. Yöneticiden, yönetim [Microsoft 365 olan](https://connectivity.office.com) bir Windows makinede ağ bağlantısı testini görüntülemelerini iste. Web sitesinde, sonuçları görmek istediğiniz kuruluşa Office 365 hesabıyla oturum açmaları gerekir. Ardından Test **çalıştır'a tıklamaları gerekir**. Test sırasında indirilen bir Bağlantı testi EXE'si vardır. Bunu açmaları ve yürütmeleri gerekir. Testler tamamlandıktan sonra, test sonucu Yönetim Merkezi'ne yükler.

Test raporları, LAN alt ağı bilgileriyle eklenmişse bir konuma bağlıdır, aksi takdirde yalnızca şehir konumda gösterilir.

Ölçü örnekleri ve ofis konumları, test raporu tamamlandıktan 2-3 dakika sonra görünmeye başlayacaktır. Daha fazla bilgi için bkz[. Microsoft 365 bağlantı testi.](office-365-network-mac-perf-onboarding-tool.md)

> [!NOTE]
> Şu anda, wKimlik ağ Microsoft 365 office konumlarınızı eklerken, LAN alt Microsoft 365 yönetim merkezi yalnızca IPv4 adreslerini sebilirsiniz. Egress IP adreslerinin IPv4'ü kullanması gerekir.

## <a name="how-do-i-use-this-information"></a>Bu bilgileri nasıl kullanabilirim?

**Ağ içgörüleri**, bunların ilgili performans önerileri ve ağ değerlendirmeleri ofis konumlarında ağ çevrelerini tasarlamaya yardımcı olmak için tasarlanmıştır. Her içgörü, kullanıcıların kiracınıza eriştiği her coğrafi konumda belirli bir genel ağ sorununa yönelik performans özellikleri hakkında ayrıntılar sağlar. **Her ağ içgörüsi** için performans önerileri, ağ bağlantısını geliştirmek ve ağ bağlantısıyla ilgili kullanıcı deneyimini geliştirmek için Microsoft 365 değişiklikler sunar. Ağ değerlendirmesi, ağ bağlantısının kullanıcı deneyimini nasıl etkile olduğunu gösterir ve bu da farklı kullanıcı konumu ağ bağlantılarının karşılaştırılmasına olanak sağlar.

**Ağ değerlendirmeleri** , birçok ağ performansı ölçümünü toplamını, 0 - 100 arasında bir nokta değeriyle temsil edilen kurumsal ağ sistem durumunun anlık görüntüsüne tasarlanmıştır. Ağ değerlendirmeleri hem kiracının tamamını hem de kullanıcıların kiracınıza bağladığı her coğrafi konumun kapsamına girmektedir ve Microsoft 365 yöneticilerine, kuruluş ağ durumunu anında anlamanın ve herhangi bir genel ofis konumuyla ilgili ayrıntılı rapora hızla gitmeleri için kolay bir yol sağlar.

Birden çok ofis konumu ve trivi olmayan ağ çevre mimarisine sahip karmaşık kuruluşlar, Microsoft 365'a ilk ekleme sırasında veya kullanım büyümesiyle bulunan ağ performansı sorunlarını düzeltmek için bu bilgiden yararlanabilir. Bu genellikle E-posta hizmeti kullanan küçük işletmeler Microsoft 365 zaten basit ve doğrudan ağ bağlantısı olan kuruluşlar için gerekli değildir. 500'den fazla kullanıcısı ve birden çok ofis konumu olan kuruluşların en çok yararlanması bek gerekmektedir.

>[!IMPORTANT]
>Microsoft 365 Yönetici Merkezi'nde ağ içgörüleri, performans önerileri ve değerlendirmeleri şu anda önizleme durumundadır ve yalnızca özellik önizleme programına Microsoft 365 kiracılar tarafından kullanılabilir.

## <a name="enterprise-network-connectivity-challenges"></a>Enterprise bağlantısının zorluklarını aşabilirsiniz

> [!div class="mx-imgBorder"]
> ![Müşteri ağına buluta.](../media/m365-mac-perf/m365-mac-perf-first-last-mile.png)

Birçok kuruluşta zamanla büyüme olan ve öncelikli olarak çoğu web sitesi önceden bilinemeyen ve güvenilmeyen çalışan İnternet web sitesi erişimini barındıracak şekilde tasarlanmış ağ çevre yapılandırmaları vardır. Burada en gerekli ve gerekli odak, bu bilinmeyen web sitelerinden kötü amaçlı yazılım ve kimlik avı saldırılarından kaçınmaktır. Bu ağ yapılandırma stratejisi, güvenlik amacıyla yardımcı olmakla birlikte, kullanıcı performansının Microsoft 365 deneyiminde performans düşüşüne yol açabilir.

## <a name="how-we-can-solve-these-challenges"></a>Bu güçlükleri nasıl çözebiliriz?

Kuruluşlar, temel bağlantı ilkelerine uygun olarak ve Merkezi Merkezi [ağ Office 365](./microsoft-365-network-connectivity-principles.md) kullanarak genel kullanıcı deneyimini Microsoft 365 Yönetici ortamını güvenlik altına atayabilir. Çoğu durumda, bu genel ilkelere uygun olarak son kullanıcı gecikme süresi, hizmet güvenilirliği ve genel performans üzerinde önemli olumlu bir Microsoft 365.

Microsoft'un bazen büyük kurumsal müşteriler için Microsoft 365 performans sorunlarını araştırması istenebilir ve bu sorunların sık sık müşterinin ağ çevre altyapısıyla ilgili kök bir nedeni vardır. Bir müşteri ağı çevre sorununa ilişkin yaygın bir kök neden bulunduğu zaman bunu tanımlayan basit test ölçülerini tanımlamak için aramamız gerekir. Belirli bir sorunu tanımlayan ölçü eşiğine sahip bir test değerlidir, çünkü herhangi bir konumda aynı ölçümü sınayıp bu kök nedenin orada olup olmadığını an ederiz ve bunu yöneticiyle bir ağ içgörü olarak paylaşabiliriz.

Bazı ağ içgörüleri yalnızca daha fazla araştırma yapılması gereken bir soruna işaret ediyor. Kök nedenini düzeltmek için belirli bir düzeltme eylemi göstermek için yeterli testlerin bulunduğu ağ içgörüleri, önerilen bir **eylem olarak listelenir**. Bu öneriler, önceden belirlenen bir eşiğin dışında olan değerleri ortaya koyan canlı ölçümlere dayalı olarak, ortamınıza özgü olması nedeniyle genel en iyi uygulama önerilerden çok daha değerlidir ve önerilen değişiklikler yapıldıktan sonra gerçek iyileştirmeyi gösterir.

## <a name="network-connectivity-overview-in-the-microsoft-365-admin-center"></a>Ağ Bağlantısı Merkezi'nde ağ Microsoft 365 Yönetici görünümü

Microsoft'un, çeşitli masaüstü Office web istemcilerinden gelen ağ ölçüleri vardır ve bu ölçümler microsoft tarafından Microsoft 365. Bu ölçümler şimdi, Genel Merkezi'nin Ağ bağlantısı sayfasında gösterilen ağ mimarisi tasarım içgörüleri ve ağ  değerlendirmesi sağlamak Microsoft 365 Yönetici kullanılır.

Varsayılan olarak, ağ ölçüleriyle ilişkili yaklaşık konum bilgileri istemci cihazlarının bulunduğu şehri ayarlar. Her konumdaki ağ değerlendirmesi renkle gösterilir ve her konumdaki göreli kullanıcı sayısı dairenin boyutuyla gösterilir.

> [!div class="mx-imgBorder"]
> ![Ağ içgörüleri genel bakış haritası.](../media/m365-mac-perf/m365-mac-perf-overview-map.png)

Genel bakış sayfası, tüm ofis konumlarına müşteri için ağ değerlendirmesini de ağırlıklı ortalama olarak gösterir.

> [!div class="mx-imgBorder"]
> ![Ağ değerlendirmesi.](../media/m365-mac-perf/m365-mac-perf-overview-score.png)

Konumlar sekmesinde filtrelenemez, sıralanın ve düzenlenemez konumların tablo **görünümünü görüntüleyebilirsiniz** . Belirli önerilere sahip konumlar tahmini bir gecikme süresini de içerebilir. Bu, aynı şehirde bulunan tüm kuruluşlarda kuruluş kullanıcılarının orta gecikme süresini alarak ve orta gecikme süresini çıkararak hesaplanır.

> [!div class="mx-imgBorder"]
> ![Ağ içgörüleri konumları.](../media/m365-mac-perf/m365-mac-perf-locations.png)

## <a name="remote-worker-assessment-and-user-connection-metrics"></a>Uzaktan çalışan değerlendirme ve kullanıcı bağlantısı ölçümleri

Ağ trafiği günlüklerini uzak veya site içi kullanıcılar olarak sınıflandırıyor ve genel bakış bölmesinin kullanıcı bağlantısı ölçümleri bölümünde yüzdelerini gösteriyoruz. Uzak kullanıcılarınız olduğu şehirler için, o konumun sayfasını asanız konuma özgü uzak ağ değerlendirme puanı bulursanız. Konum listesi hem ofis konumlarını hem de uzak çalışan şehirlerini içerir; bu şehir filtre ve sıralanmış olabilir. Uzaktan çalışan değerlendirme puanı sağlar ve bu puanın, çalışma puanı, Exchange ve SharePoint değerlendirme Teams.

Ev kullanıcısı ağı içgörüleri şehir düzeyinde bir araya toplanır ve raporlandığı gibi, en az 5 uzak çalışana sahip şehirlerle sınırlıdır. Evden çalışan çalışanları tanımlamaz.

Öte yandan, konumlar otomatik olarak site içinde veya uzak olarak sınıflandırılır; bununla birlikte, tüm site içi çıkış IP adreslerinizi el ile girerek %100 sınıflandırmayı silebilirsiniz. Bu yönlendirmeye gitmek için karar verirsiniz, Tüm çıkış IP adreslerinizi  ekledikten sonra Konumlar ve veri dışarı Ayarlar yerinde çıkış IP adreslerini el ile gir onay kutusunu denetlemeniz gerekir. Bu olduğunda, çıkış IP adreslerinden çıkış IP adreslerinden gelen tüm ağ trafiği günlükleri her zaman ofis olarak sınıflandırılır ve diğer tüm çıkış IP adresleri uzak olarak sınıflandırılır.

## <a name="specific-office-location-network-performance-summary-and-insights"></a>Belirli ofis konumu ağ performansı özeti ve öngörüleri

Ofis konumu seçerek, ofis konumunun ölçümlerinden belirlenen ağ çıkışlarının ayrıntılarını gösteren konuma özgü bir özet sayfası açılır.

> [!div class="mx-imgBorder"]
> ![Konuma göre ağ içgörüleri ayrıntıları.](../media/m365-mac-perf/m365-mac-perf-locations-plan-overview.png)

Konumda yer alan kuruluş kullanıcıları için çevre ağının haritası, şu öğelerin birkaçı veya hepsiyle birlikte gösterilir:

- **Office** konumu - Baktayır sayfa için ofis konumu
- **Ağ çevresi** - Ofis bulunduğu konumdan bağlantıların kaynak IP Adresi konumu. Bu, coğrafi IP konum veritabanlarının doğruluğuna bağlıdır
- **Exchange en iyi hizmet ön kapı** - Bu ofisteki Exchange kullanıcıların bağlanması gereken önerilen ön kapılardan biri
- **Exchange en iyi ön kapı** - kullanıcıların Exchange bağlı olduğu, ancak önerilmez bir hizmet ön kapı
- **SharePoint en iyi hizmet ön kapı** - Bu ofisteki SharePoint kullanıcıların bağlanması gereken önerilen ön kapılardan biri
- **SharePoint en iyi hizmet ön** SharePoint - Kullanıcıların bağlı olduğu, ancak önerilen bir SharePoint hizmet ön kapı
- **DNS tekrarlayıcı çözümleyici sunucusu** - Algılayan DNS yeniden doğrulayıcı çözümleyicinin coğrafi IP veritabanından gelen konum Exchange Online (varsa)
- **Ara sunucunuz** - Algılanan proxy sunucusunun coğrafi IP veritabanındaki konum (varsa)

Ofis konumu özet sayfası ayrıca, konumun ağ değerlendirmesini, ağ değerlendirme geçmişini, bu konumun değerlendirmesini aynı şehirde diğer müşterilere karşılaştırmayı ve ağ performansını ve güvenilirliğini geliştirmek için taahhütlerde bulunabilirsiniz belirli içgörülerin ve önerilerin listesini gösterir.

Aynı şehrin müşterileri arasındaki karşılaştırmalar, tüm müşterilerin ağ hizmet sağlayıcılarına, telekomünikasyon altyapısına ve yakındaki Microsoft ağ iletişim durumu noktalarına eşit erişime sahip olması beklentilerine dayalıdır.

Konum adları, yeni konum eklerken veya konum çıktısı içinde var olan bir konumu düzenlerken özelleştirilebilir. Bu size istediğiniz zaman konum adlarınızı özelleştirme esnekliği sağlar. Ayrıca, doğrudan konum açılır listesine LAN alt ağlarını eklerken, seçim oynanabilir, yumuşak eşleşmeli LAN alt ağlarının bir açılan listesini gösteririz. Belirli office çıkış IP adresleri için devre adları da eklenebilir ve düzenlenebilir.

Ofis konumu sayfasındaki ayrıntılar sekmesi herhangi bir içgörü, öneri ve ağ değerlendirmesiyle ortaya çıktık belirli ölçü sonuçlarını gösterir. Ağ mühendislerinin kendi ortamındaki herhangi bir kısıtlama veya özel durumdaki önerileri ve faktörü doğrulaymalarını sağlar. Ayrıca bu ofis konumlarında toplanan örnekler için tahmin edilen kullanıcı sayısını, aynı zamanda bu şehrin uzak çalışanlarını da bulabilirsiniz.

> [!div class="mx-imgBorder"]
> ![Konuma özgü ayrıntılar.](../media/m365-mac-perf/m365-mac-perf-locations-plan-details-all.png)

## <a name="sharing-network-assessment-data-with-microsoft"></a>Ağ değerlendirme verilerini Microsoft ile paylaşma

Varsayılan olarak, kurum için ağ değerlendirmeleri ve ağ içgörüleri Microsoft çalışanları ile paylaşılır. Bu, personelinizin kişisel verilerini değil, yalnızca ofis konumlarına ilişkin yönetim merkezinde gösterilen belirli ağ değerlendirme ölçümlerini ve ağ içgörülerini içerir. Ayrıca ofis konum adları veya sokak adresleri de dahil değildir, dolayısıyla onlara tartışmak istediğiniz ofisin şehrini ve destek kimliğini söylemeniz gerekir. Bu kapalı olursa, ağ bağlantınızı tartışırken microsoft mühendisleri bu bilgilerin hiçbirini görüntüleyemz. Bu ayarın etkinleştirilmesi, yalnızca gelecekte etkinleştirdikten sonra başlayacak olan verileri paylar.

## <a name="csv-import-for-lan-subnet-office-locations"></a>LAN alt ağ ofis konumları için CSV İçeri Aktarma

LAN alt ağı office kimliği için, her konumu önceden eklemeniz gerekir. Konumlar sekmesine ofis konumlarını tek tek **eklemek** yerine, bunları bir CSV dosyasından içeri aktarabilirsiniz. Arama Kalitesi Panosu veya Active Directory Siteleri ve Hizmetleri gibi, bu verileri depolanmış olan diğer yerlerden elde edebilirsiniz

CSV dosyasında, bulunan bir şehir konumu kullanıcıda görünüyorSatır sütunu boş olarak girildi ve elle eklenmiş bir ofis konumu da 1 olarak görünüyor.

1. Ana _Konumlar ve Microsoft 365_ penceresinde **Konumlar sekmesine** tıklayın.

1. Konum **listesinin** hemen üstündeki İçeri Aktar düğmesine tıklayın. Office **konumlarını içeri aktar** flyout görüntülenir.

   > [!div class="mx-imgBorder"]
   > ![CSV içeri aktarma iletisi.](../media/m365-mac-perf/m365-mac-perf-import.png)

1. Geçerli **konumlar listesini** CSV dosyasına dışarı aktar .csv için Geçerli ofis konumlarını indir (.csv) bağlantısına tıklayın ve bunu yerel sabit diske kaydedin. Bu size, konum ekyebilirsiniz sütun başlıklarıyla doğru biçimlendirilmiş bir CSV sağlar. Var olan dışarı aktarma konumlarını olduğu gibi  bırakın; güncelleştirilmiş CSV'leri içeri aktarsanız da bu yinelemeler yinelenmez. Var olan bir konumun adresini değiştirmek isterseniz, CSV'i içeri aktararak bu adres güncelleştirilir. Bulunan bir şehrin adresini değiştiremezsiniz.

1. EKLEMEK istediğiniz her konum için yeni bir satıra aşağıdaki alanları doldurarak CSV'yi açın ve konumlarınızı ekleyin. Diğer tüm alanları boş bırakın; diğer alanlara değerler yoksayılır.

   1. **userEntered** (gerekli): Eklenen yeni bir LAN Alt Ağ ofis konumu için 1 olmalı
   1. **Ad** (gerekli): Ofis konumunun adı
   1. **Adres** (gerekli): Ofisin fiziksel adresi
   1. **Enlem** (isteğe bağlı): Bing, boşsa adresin haritalar araması ile doldurulur
   1. **Boylam** (isteğe bağlı): Bing, boşsa adresin arama yapılan eşlemeleri ile doldurulur
   1. **Egress IP Adresi aralıkları 1-5** (isteğe bağlı): Her aralık için devre adını girin ve ardından geçerli IPv4 CIDR adreslerinin yer alan boşlukla ayrılmış listesini girin. Bu değerler, aynı LAN alt ağı IP Adreslerinin bulunduğu birden çok ofis konumunu ayırt etmek için kullanılır. Egress IP Adresi aralıkların hepsi /24 ağ boyutu olmalıdır ve /24 girişe dahil değildir.
   1. **LanIps** (gerekli): Bu ofis konumda, kullanımda olan LAN alt ağı aralıklarını listele. LAN alt ağ kimlikleri, ağ boyutunun /8 ile /29 arasında olduğu bir CIDR ağ boyutunun dahil olması gerekir. Birden çok LAN alt ağ aralığı virgül veya noktalı virgülle ayrılabilir.

1. Ofis konumlarınızı ekp dosyayı kaydettiyken, tamamlanan alanı silmek **için** Upload  Gözat düğmesini tıklatın ve kaydedilmiş CSV dosyasını seçin.

1. Dosya otomatik olarak doğrulanır. Doğrulama hataları varsa, şu hata iletisini görüntülersiniz: _İçeri aktarma dosyasında bazı hatalar var. Hataları gözden geçirin, içeri aktarma dosyasını düzeltin ve yeniden deneyin._ Belirli alan doğrulama **hatalarını içeren bir liste** için Hata ayrıntılarını aç bağlantısına tıklayın.

   > [!div class="mx-imgBorder"]
   > ![CSV içeri aktarma hata iletisi.](../media/m365-mac-perf/m365-mac-perf-import-error.png)

1. Dosyada hata yoksa, şu iletiyi görüntülersiniz: _Rapor hazır. Ekli x konumlar ve güncelleştirilen x konumlar bulundu._ **CSV'yi karşıya** yüklemek için İçeri Aktar düğmesine tıklayın.

   > [!div class="mx-imgBorder"]
   > ![CSV içeri aktarma hazır iletisi.](../media/m365-mac-perf/m365-mac-perf-import-ready.png)

## <a name="faq"></a>SSS

### <a name="what-is-a-microsoft-365-service-front-door"></a>Hizmet Microsoft 365 nedir?

Müşteri Microsoft 365 ön kapı, Microsoft'un genel ağın, istemci ve hizmetlerin ağ Office sonlandırılan bir giriş noktasıdır. E-Microsoft 365 en iyi ağ bağlantısı için, ağ bağlantının ön kapının en yakın Microsoft 365 kullanılması önerilir.

>[!NOTE]
>Microsoft 365 ön kapı, Azure marketi'nden edinilen Azure Front Door Service ürünüyle doğrudan ilişkisi yoktur.

### <a name="what-is-an-optimal-microsoft-365-service-front-door"></a>En iyi hizmet Microsoft 365 kapı nedir?

En iyi Microsoft 365 hizmet ön kapı, genel olarak şehir veya metro bölgenize ağ çıkışa en yakın olan kapıdır. Hizmet [Microsoft 365 ön kapınız ve](office-365-network-mac-perf-onboarding-tool.md) en iyi hizmet ön Microsoft 365 konumunu belirlemek için Microsoft 365 bağlantı test aracını (önizleme) kullanın. Araç, kullanım için ön kapının en uygun olduğunu belirlerse Microsoft'un genel ağına en uygun şekilde bağlanırsanız.

### <a name="what-is-an-internet-egress-location"></a>İnternet çıkış konumu nedir?

İnternet çıkış konumu, ağ trafiğinizin kurumsal ağdan çıkış bulunduğu ve İnternet'e bağlandığı konumtur. Bu ayrıca, Ağ Adresi Çevirisi (NAT) cihazınızın bulunduğu ve genellikle bir İnternet Servis Sağlayıcısına (ISS) bağlandıysanız konum olarak da tanımlanır. Konumunuzla İnternet çıkış konumunuz arasında uzun bir mesafe görüyorsanız, bu önemli bir WAN gerilemesi gösteriyor olabilir.

### <a name="what-license-is-needed-for-this-capability"></a>Bu özellik için hangi lisans gereklidir?

Lisansa erişim sağlayan bir lisans Microsoft 365 yönetim merkezi.

## <a name="related-topics"></a>İlgili konular

[Microsoft 365 içgörüleri](office-365-network-mac-perf-insights.md)

[Microsoft 365 değerlendirmesini geri ayanız](office-365-network-mac-perf-score.md)

[Microsoft 365 bağlantı test aracı](office-365-network-mac-perf-onboarding-tool.md)

[Microsoft 365 Bağlantısı Konum Hizmetleri'ne Bağlan'a](office-365-network-mac-location-services.md)
