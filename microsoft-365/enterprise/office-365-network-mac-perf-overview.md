---
title: Microsoft 365 Yönetici Merkezi'nde ağ bağlantısı
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 06/15/2022
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.reviewer: pandrew1
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- m365initiative-coredeploy
description: Microsoft 365 Yönetici Merkezi'nde ağ bağlantısına genel bakış
ms.openlocfilehash: 5c360820c39be6ec1c42ecdfa0a045a51716e408
ms.sourcegitcommit: 18bc521a88b7b521bccb0e69d02deac764218087
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/16/2022
ms.locfileid: "66115661"
---
# <a name="network-connectivity-in-the-microsoft-365-admin-center"></a>Microsoft 365 Yönetici Merkezi'nde ağ bağlantısı

Microsoft 365 Yönetici Merkezi artık Microsoft 365 kiracınızdan toplanan toplu ağ bağlantısı ölçümlerini içerir ve yalnızca kiracınızdaki yönetici kullanıcılar tarafından görüntülenebilir.

> [!div class="mx-imgBorder"]
> ![Ağ bağlantısı test aracı.](../media/m365-mac-perf/m365-mac-perf-admin-center.png)

**Ağ değerlendirmeleri** ve **ağ içgörüleri** sistem **durumu | altındaki Microsoft 365 Yönetici Merkezi'nde görüntülenir Ağ bağlantısı**.

> [!div class="mx-imgBorder"]
> ![Ağ performansı sayfası.](../media/m365-mac-perf/m365-mac-perf-page-nav.png)

> [!NOTE]
> Yönetici Merkezi'ndeki ağ bağlantısı WW Ticari ve Almanya'daki kiracıları destekler ancak Orta, GCC Yüksek, DoD veya Çin GCC desteklemez.

Ağ performansı sayfasına ilk gittiğinizde, genel ağ performansı haritasını, kiracının tamamının kapsamına alınmış bir ağ değerlendirmesinin, uzaktan çalışan kullanıcılarınızın yüzdesini ve daha fazla araştırma yapmak ve/veya araştırmak için geçerli sorunların listesini görmek için konumlarınızı yapılandırmanız gerekir. Genel bakış bölmesinden, konuma göre belirli ağ performansı ölçümlerini ve sorunlarını görüntülemek için detaya gidebilirsiniz. Daha fazla bilgi için [Microsoft 365 Yönetici Merkezi'nde ağ performansına genel bakış](#network-connectivity-overview-in-the-microsoft-365-admin-center) bölümüne bakın.

Ağ bağlantısı sayfasına erişmek için Microsoft 365 içindeki kuruluşun yöneticisi olmanız gerekir. Rapor Okuyucusu yönetim rolü bu bilgilere okuma erişimine sahip olacaktır. Ağ bağlantısının konumlarını ve diğer öğelerini yapılandırmak için bir yöneticinin Hizmet Desteği Yöneticisi rolüne sahip olması gerekir.

## <a name="pre-requisites-for-network-connectivity-assessments-to-appear"></a>Ağ bağlantısı değerlendirmelerinin görünmesi için önkoşullar

Başlamak için Konum Servisleri'ni Windows kullanarak cihazlardan otomatik olarak veri toplamak için konum kabul etme ayarınızı açın, konum verilerini eklemek veya karşıya yüklemek için Konumlar listenize gidin veya ofis konumlarınızdan Microsoft 365 ağ bağlantısı testini çalıştırın. Office konum bilgileri için bu üç seçenek aşağıda ayrıntılı olarak yer almaktadır. Ağ bağlantısı kuruluş genelinde değerlendirilebilir ancak belirli ofis konumları için ağ tasarımı geliştirmeleri yapılması gerekir. Bu konumlar belirlendikten sonra her ofis konumu için ağ bağlantısı bilgileri sağlanır. Ofis konumlarınızdan ağ değerlendirmeleri almak için üç seçenek vardır:

### <a name="1-enable-windows-location-services"></a>1. Windows Konum Hizmetlerini etkinleştirme

Bu seçenek için, ön koşulları destekleyen her ofis konumunda çalışan en az iki bilgisayar olmalıdır. Windows sürüm için OneDrive güncel olmalı ve her bilgisayara yüklenmelidir. Ağ testleri günde rastgele bir zamanda en fazla bir kez çalıştırılır. Ağ ölçümlerinin yakında diğer Office 365 istemci uygulamalarına eklenmesi planlanıyor.

Windows Konum Hizmeti makinelerde onaylanmalıdır. **Haritalar** uygulamasını çalıştırıp kendinizi bularak bunu test edebilirsiniz. Ayarlar | ile tek bir makinede etkinleştirilebilir **Gizlilik |** _Uygulamaların konumunuza erişmesine izin ver_ ayarının etkinleştirildiği konum. Windows Konum Hizmetleri onayı, MDM kullanılarak bilgisayarlara dağıtılabilir veya _LetAppsAccessLocation_ ayarıyla grup ilkesi.

Bu yöntemle Yönetici Merkezi'ne konum eklemeniz gerekmez çünkü şehir çözünürlüğünde otomatik olarak tanımlanırlar. Windows Konum Hizmetleri kullanılırken aynı şehir içindeki birden çok ofis konumu gösterilmez. Konum bilgileri, daha hassas konum bilgilerine erişilemeyecek şekilde en yakın 300 metreye 300 metre yuvarlanmış olur. Windows Konum Hizmetleri'nin ağ ölçümleri için kullanılması müşteriler için varsayılan olarak kapalıdır. Ağ Bağlantısı Ayarlar Konumu açılır öğesinde etkinleştirmeniz gerekir.

   > [!div class="mx-imgBorder"]
   > ![Konumu etkinleştir](../media/m365-mac-perf/m365-mac-perf-location-enable.png)

Makinelerin ethernet kablosu yerine Wi-Fi ağı olmalıdır. Ethernet kablosu olan makinelerin konum bilgileri doğru değildir.

Ölçüm örnekleri ve ofis konumları, bu önkoşullar karşılandıktan 24 saat sonra görünmeye başlamalıdır. Windows Konum Hizmetleri'nden bulunan Office konumlar Şehir başına toplanır ve örnekler artık alınmadıktan sonra 90 gün boyunca görünümünüzde tutulur. YÖNETICI tarafından LAN alt ağ bilgileriyle eklenen ofis konumlarına geçmeyi seçerseniz Konum Hizmetleri Windows'ni devre dışı bırakabilir ve bulunan tüm konumları gizleyebilirsiniz. Bunlar 90 günlük süreden sonra kaldırılacaktır.

### <a name="2-add-locations-and-provide-lan-subnet-information"></a>2. Konum ekleme ve LAN alt ağı bilgilerini sağlama

Bu seçenek için konum hizmetlerini Windows veya Wi-Fi gerekli değildir. Windows sürümü için OneDrive güncel olmalı ve konumdaki en az bir bilgisayara yüklenmiş olmalıdır ve her ofis için LAN alt ağ bilgilerinizi bilmeniz gerekir. Bu seçenek, şehir başına birden çok ofis konumuna izin verir ve ofis konumlarınızı adlandırabilirsiniz. Bunları diğer kaynaklardan da karşıya yükleyebilirsiniz.

**Ayrıca konumlar sayfasına** konum eklediğinizden veya bunları csv dosyasından içeri aktardığınızdan emin olun. Eklenen konumlar office LAN alt ağ bilgilerinizi içermelidir. Konum ekleme veya düzenleme iletişim kutusunda, bir dizi LAN alt ağı ve bir dizi genel çıkış IP alt ağı belirtebilirsiniz. LAN alt ağları gereklidir ve sonuçların gösterilmesi için bunlardan birinin alınan ağ değerlendirmesinde LAN alt ağı özniteliğiyle eşleşmesi gerekir. Süper ağlar desteklenmez, bu nedenle LAN alt ağı tam olarak eşleşmelidir.

LAN alt ağları genellikle RFC1918'de tanımlandığı gibi, LAN alt ağları olarak genel IP adreslerinin kullanımının yanlış olması gibi özel IP adresi aralıklarıdır. İletişim kutusunda, seçebilmeniz için kuruluşunuz için son ağ değerlendirme testlerinde görülen LAN alt ağlarına ilişkin öneriler gösterilir.

Genel çıkış IP adresleri eklerseniz, bunlar ikincil bir ayırıcı olarak kullanılır ve aynı LAN alt ağı IP adresi aralıklarını kullanan birden çok siteniz olduğunda için tasarlanmıştır. Test sonuçlarınızın göründüğünden emin olmak için genel çıkış IP adresi aralıklarını boş bırakarak işe başlamanız gerekir. Bunlar dahil edilirse, test sonucunun hem LAN alt ağı IP adresi aralıklarından hem de genel çıkış IP adresi aralıklarından biriyle eşleşmesi gerekir.

Bu seçenek, bir şehirde birden çok ofis tanımlamanızı sağlar.

İstemci makinelerinden alınan tüm test ölçümleri, girdiğiniz ofis konumu ayrıntılarıyla ilişkili LAN alt ağ bilgilerini içerir. Ölçüm örnekleri ve ofis konumları, bu önkoşullar karşılandıktan 24 saat sonra görünmeye başlamalıdır.

### <a name="3-manually-gather-test-reports-with-the-microsoft-365-network-connectivity-test-tool"></a>3. Microsoft 365 ağ bağlantısı test aracıyla test raporlarını el ile toplayın

Bu seçenek için her konumda bir kişiyi tanımlamanız gerekir. Yönetici izinlerine sahip oldukları bir Windows makinesinde Microsoft 365 [ağ bağlantısı testine](https://connectivity.office.com) göz atmalarını isteyin. Web sitesinde, sonuçları görmek istediğiniz kuruluş için Office 365 hesaplarında oturum açmaları gerekir. Ardından **Testi çalıştır'a** tıklamaları gerekir. Test sırasında indirilmiş bir Bağlantı testi EXE'sı vardır. Bunu açıp yürütmeleri gerekir. Testler tamamlandıktan sonra test sonucu Yönetici Merkezi'ne yüklenir.

Test raporları LAN alt ağ bilgileriyle eklenmişse bir konuma bağlanır, aksi takdirde bunlar yalnızca bulunan Şehir konumunda gösterilir.

Ölçüm örnekleri ve ofis konumları, test raporu tamamlandıktan 2-3 dakika sonra görünmeye başlamalıdır. Daha fazla bilgi için bkz. [ağ bağlantısı test Microsoft 365](office-365-network-mac-perf-onboarding-tool.md).

> [!NOTE]
> Şu anda, ofis konumlarınızı Microsoft 365 yönetim merkezi Microsoft 365 ağ bağlantısına eklerken, LAN alt ağlarınız için yalnızca IPv4 adresleri sağlayabilirsiniz. Egress IP adresleri IPv4 kullanmalıdır.

## <a name="how-do-i-use-this-information"></a>Bu bilgileri Nasıl yaparım? kullanıyorsunuz?

**Ağ içgörüleri**, ilgili performans önerileri ve ağ değerlendirmeleri, ofis konumlarınız için ağ çevreleri tasarlamaya yardımcı olmak için tasarlanmıştır. Her içgörü, kullanıcıların kiracınıza eriştiği her coğrafi konum için belirli bir ortak ağ sorununun performans özellikleri hakkında ayrıntılar sağlar. Her ağ içgörüsü için **performans önerileri**, Microsoft 365 ağ bağlantısıyla ilgili kullanıcı deneyimini geliştirmek için yapabileceğiniz belirli ağ mimarisi tasarım değişiklikleri sunar. Ağ değerlendirmesi, farklı kullanıcı konumu ağ bağlantılarının karşılaştırılması için ağ bağlantısının kullanıcı deneyimini nasıl etkilediğini gösterir.

**Ağ değerlendirmeleri** , birçok ağ performansı ölçümünün toplamını kurumsal ağ durumunuzun anlık görüntüsüne dönüştürür ve 0 ile 100 arasında bir puan değeriyle gösterilir. Ağ değerlendirmelerinin kapsamı hem kiracının tamamına hem de kullanıcıların kiracınıza bağlandığı her coğrafi konum için belirlenir ve Microsoft 365 yöneticilerine kuruluşun ağ durumunu anında kavramanın ve herhangi bir genel ofis konumu için ayrıntılı bir raporun detayına gitmenin kolay bir yolunu sunar.

Birden çok ofis konumuna ve önemsiz olmayan ağ çevre mimarilerine sahip karmaşık kuruluşlar, Microsoft 365 ilk katılımları sırasında veya kullanım büyümesiyle birlikte bulunan ağ performansı sorunlarını gidermek için bu bilgilerden yararlanabilir. Bu genellikle Microsoft 365 kullanan küçük işletmeler veya zaten basit ve doğrudan ağ bağlantısı olan kuruluşlar için gerekli değildir. 500'den fazla kullanıcısı ve birden çok ofis konumu olan kuruluşların en çok avantajlı olması beklenmektedir.

## <a name="enterprise-network-connectivity-challenges"></a>ağ bağlantısı sorunlarını Enterprise

> [!div class="mx-imgBorder"]
> ![Müşteri ağından buluta.](../media/m365-mac-perf/m365-mac-perf-first-last-mile.png)

Birçok kuruluşun ağ çevre yapılandırmaları vardır. Bu yapılandırmalar zamanla büyümüştür ve öncelikli olarak çoğu web sitesinin önceden bilinmediği ve güvenilmeyen çalışan İnternet web sitesi erişimini barındıracak şekilde tasarlanmıştır. Geçerli ve gerekli odak, bu bilinmeyen web sitelerinden gelen kötü amaçlı yazılım ve kimlik avı saldırılarından kaçınmaktır. Bu ağ yapılandırma stratejisi, güvenlik amacıyla yararlı olsa da Microsoft 365 kullanıcı performansının ve kullanıcı deneyiminin bozulmasına neden olabilir.

## <a name="how-we-can-solve-these-challenges"></a>Bu zorlukları nasıl çözebiliriz?

Kuruluşlar, [Office 365 bağlantı ilkelerini](./microsoft-365-network-connectivity-principles.md) izleyerek ve Microsoft 365 Yönetici Merkezi ağ bağlantısı özelliğini kullanarak genel kullanıcı deneyimini geliştirebilir ve ortamlarının güvenliğini sağlayabilir. Çoğu durumda, bu genel ilkelerin izlenerek son kullanıcı gecikme süresi, hizmet güvenilirliği ve Microsoft 365 genel performansı üzerinde önemli bir olumlu etkisi olacaktır.

Microsoft'un bazen büyük kurumsal müşteriler için Microsoft 365 ile ilgili ağ performansı sorunlarını araştırması istenir ve bunların genellikle müşterinin ağ çevre altyapısıyla ilgili temel bir nedeni vardır. Müşteri ağ çevre sorununun yaygın bir kök nedeni bulunduğunda, basit test ölçümlerini belirlemeye çalışırız. Belirli bir sorunu tanımlayan bir ölçüm eşiğine sahip test değerlidir çünkü aynı ölçümü herhangi bir konumda test edebilir, bu kök nedenin orada bulunup bulunmadığını söyleyebilir ve bunu yöneticiyle ağ içgörüsü olarak paylaşabiliriz.

Bazı ağ içgörüleri yalnızca daha fazla araştırma gerektiren bir sorunu gösterir. Kök nedeni düzeltmek için belirli bir düzeltme eylemini göstermek için yeterli teste sahip olduğumuz bir ağ içgörüsü **önerilen eylem** olarak listelenir. Önceden belirlenmiş eşiğin dışında kalan değerleri ortaya koyan canlı ölçümlere dayalı bu öneriler, ortamınıza özgü olduklarından genel en iyi deneyim önerilerinden çok daha değerlidir ve önerilen değişiklikler yapıldıktan sonra gerçek iyileştirmeyi gösterir.

## <a name="network-connectivity-overview-in-the-microsoft-365-admin-center"></a>Microsoft 365 Yönetici Merkezi'nde ağ bağlantısına genel bakış

Microsoft, Microsoft 365 çalışmasını destekleyen çeşitli Office masaüstü ve web istemcilerinden gelen mevcut ağ ölçümlerine sahiptir. Bu ölçümler artık ağ mimarisi tasarım içgörüleri ve Microsoft 365 Yönetici Merkezi'ndeki **Ağ bağlantısı** sayfasında gösterilen bir ağ değerlendirmesi sağlamak için kullanılıyor.

Varsayılan olarak, ağ ölçümleriyle ilişkili yaklaşık konum bilgileri istemci cihazlarının bulunduğu şehri tanımlar. Her konumdaki ağ değerlendirmesi renkle gösterilir ve her konumdaki göreli kullanıcı sayısı dairenin boyutuyla temsil edilir.

> [!div class="mx-imgBorder"]
> ![Ağ içgörülerine genel bakış haritası.](../media/m365-mac-perf/m365-mac-perf-overview-map.png)

Genel bakış sayfasında ayrıca müşteri için ağ değerlendirmesi tüm ofis konumlarında ağırlıklı ortalama olarak gösterilir.

> [!div class="mx-imgBorder"]
> ![Ağ değerlendirmesi.](../media/m365-mac-perf/m365-mac-perf-overview-score.png)

**Konumlar** sekmesinde filtrelenebilen, sıralanıp düzenlenebilen konumların tablo görünümünü görüntüleyebilirsiniz. Belirli önerilere sahip konumlar tahmini gecikme süresi iyileştirmesi de içerebilir. Bu, kuruluş kullanıcılarınızın konumundaki ortanca gecikme süresi alınarak ve aynı şehirdeki tüm kuruluşlar için ortanca gecikme süresi çıkarılarak hesaplanır.

> [!div class="mx-imgBorder"]
> ![Ağ içgörüleri konumları.](../media/m365-mac-perf/m365-mac-perf-locations.png)

## <a name="remote-worker-assessment-and-user-connection-metrics"></a>Uzaktan çalışan değerlendirmesi ve kullanıcı bağlantısı ölçümleri

Ağ trafiği günlüklerini uzak veya yerinde kullanıcılar olarak sınıflandırır ve yüzdelerini genel bakış bölmesinin kullanıcı bağlantısı ölçümleri bölümünde gösteririz. Uzak kullanıcılarınız olan şehirler için, bu konumun sayfasını açtığınızda konuma özgü uzak ağ değerlendirme puanını bulursunuz. Konumlar listesinde hem ofis konumları hem de uzak çalışan şehirleri bulunur ve bunlar filtrelenebilir ve sıralanabilir. Exchange, SharePoint ve Teams puan dökümüyle uzaktan çalışan değerlendirme puanını sağlarız.

Ev kullanıcısı ağ içgörüleri, şehir düzeyinde toplanır ve raporlanır ve en az 5 uzak çalışanı olan şehirlerle sınırlıdır. Evden çalışan bireysel çalışanları tanımlıyoruz.

Konumlar otomatik olarak yerinde veya uzak olarak sınıflandırılır, ancak %100 sınıflandırma sağlamak için tüm yerinde çıkış IP adreslerinizi el ile girme seçeneğiniz vardır. Bu yola gitmeye karar verirseniz, tüm çıkış IP adreslerinizi ekledikten sonra Konumlar Ayarlar açılır öğesinde **Tüm yerinde çıkış IP adreslerini el ile girin** onay kutusunu işaretlemeniz gerekir. Bu işlem tamamlandığında, yerinde olarak işaretlediğiniz çıkış IP adreslerinden gelen tüm ağ trafiği günlükleri her zaman ofis olarak sınıflandırılır ve diğer tüm çıkış IP adresleri uzak olarak sınıflandırılır.

## <a name="specific-office-location-network-performance-summary-and-insights"></a>Belirli ofis konumu ağ performansı özeti ve içgörüleri

Bir ofis konumu seçildiğinde, o ofis konumuna ilişkin ölçümlerden tanımlanan ağ çıkışının ayrıntılarını gösteren konuma özgü bir özet sayfası açılır.

> [!div class="mx-imgBorder"]
> ![Konuma göre ağ içgörüleri ayrıntıları.](../media/m365-mac-perf/m365-mac-perf-locations-plan-overview.png)

Konumdaki kuruluş kullanıcılarınız için çevre ağının haritası şu öğelerin bir kısmı veya tamamıyla gösterilir:

- **Office konumu** - Baktığınız sayfanın ofis konumu
- **Ağ çevresi** - Ofis konumundan bağlantıların kaynak IP Adresinin konumu. Bu, coğrafi IP konum veritabanlarının doğruluğuna bağlıdır
- **en uygun hizmet ön kapısı Exchange** - Bu ofis konumundaki kullanıcıların bağlanması gereken önerilen Exchange hizmet ön kapılarından biri
- **Exchange en uygun ön kapı** - Kullanıcıların bağlı olduğu ancak önerilmez Exchange hizmet ön kapısı
- **en uygun hizmet ön kapısı SharePoint** - Bu ofis konumundaki kullanıcıların bağlanması gereken önerilen SharePoint hizmet ön kapılarından biri
- **SharePoint alt en uygun hizmet ön kapısı** - Kullanıcıların bağlı olduğu ancak önerilmez SharePoint hizmet ön kapısı
- **DNS özyinelemeli çözümleyici sunucusu** - Exchange Online için kullanılan algılanan DNS özyinelemeli çözümleyicisinin coğrafi IP veritabanından konum (varsa)
- Proxy sunucunuz - Algılanan **ara sunucunun** coğrafi IP veritabanından konum (varsa)

Ofis konumu özet sayfası ayrıca konumun ağ değerlendirmesini, ağ değerlendirme geçmişini, bu konumun değerlendirmesini aynı şehirdeki diğer müşterilerle karşılaştırmayı ve ağ performansını ve güvenilirliğini artırmak için üstleyebileceğiniz belirli içgörülerin ve önerilerin listesini gösterir.

Aynı şehirdeki müşteriler arasındaki karşılaştırmalar, tüm müşterilerin ağ hizmeti sağlayıcılarına, telekomünikasyon altyapısına ve yakındaki Microsoft ağ iletişim noktalarına eşit erişime sahip olması beklentisine bağlıdır.

Konum adları, yeni bir konum eklenirken veya konum açılır öğesinde mevcut bir konum düzenlenirken özelleştirilebilir. Bu, konum adlarınızı istediğiniz zaman özelleştirme esnekliği sağlar. Ayrıca, LAN alt ağlarını doğrudan konum açılır listesine eklerken, arasından seçim yapabileceğiniz, yazılımla eşleşen LAN alt ağlarının açılan listesini gösteririz. Belirli ofis çıkış IP adresleri için bağlantı hattı adları da eklenebilir ve düzenlenebilir.

Ofis konumu sayfasındaki ayrıntılar sekmesinde içgörüler, öneriler ve ağ değerlendirmesi için kullanılan belirli ölçüm sonuçları gösterilir. Bu, ağ mühendislerinin önerileri doğrulayıp ortamlarındaki kısıtlamaları veya özellikleri dikkate almalarını sağlayan bir özelliktir. Ayrıca bu ofis konumlarında toplanan örnekler için tahmini kullanıcı sayısını ve bu şehirdeki uzak çalışanları da bulabilirsiniz.

> [!div class="mx-imgBorder"]
> ![Konuma özgü ayrıntılar.](../media/m365-mac-perf/m365-mac-perf-locations-plan-details-all.png)

## <a name="sharing-network-assessment-data-with-microsoft"></a>Ağ değerlendirme verilerini Microsoft ile paylaşma

Varsayılan olarak, kuruluşunuz ve ağ içgörüleri için ağ değerlendirmeleri Microsoft çalışanlarıyla paylaşılır. Bu, personelinizin kişisel verilerini içermez, yalnızca ofis konumlarınız için yönetim merkezinde gösterilen belirli ağ değerlendirme ölçümlerini ve ağ içgörülerini içerir. Ayrıca, ofis konum adlarınızı veya sokak adreslerinizi içermez, bu nedenle onlara tartışmak istediğiniz ofisin şehrini ve destek kimliğini söylemeniz gerekir. Bu kapatılırsa, ağ bağlantınızı tartıştığınız Microsoft mühendisleri bu bilgilerin hiçbirini görüntüleyemez. Bu ayarın etkinleştirilmesi yalnızca etkinleştirildikten sonraki günden itibaren gelecekteki verileri paylaşır.

## <a name="csv-import-for-lan-subnet-office-locations"></a>LAN alt ağı ofis konumları için CSV İçeri Aktarma

LAN alt ağ ofisi tanımlaması için her konumu önceden eklemeniz gerekir. **Konumlar** sekmesine tek tek ofis konumları eklemek yerine bunları csv dosyasından içeri aktarabilirsiniz. Bu verileri, Arama Kalitesi Panosu veya Active Directory Siteleri ve Hizmetleri gibi depoladığınız diğer yerlerden alabilirsiniz

CSV dosyasında bulunan bir şehir konumu userEntered sütununda boş, el ile eklenen bir ofis konumu ise 1 olarak gösterilir.

1. _Microsoft 365 ana Bağlantısı_ penceresinde **Konumlar** sekmesine tıklayın.

1. Konumlar listesinin hemen üstündeki **İçeri Aktar** düğmesine tıklayın. **Ofis konumlarını içeri aktar** açılır öğesi görüntülenir.

   > [!div class="mx-imgBorder"]
   > ![CSV içeri aktarma iletisi.](../media/m365-mac-perf/m365-mac-perf-import.png)

1. Geçerli konumlar listesini csv dosyasına aktarmak ve yerel sabit diskinize kaydetmek için Geçerli **ofis konumlarını indir (.csv)** bağlantısına tıklayın. Bu size konum ekleyebileceğiniz sütun başlıklarıyla doğru biçimlendirilmiş bir CSV sağlar. Mevcut dışarı aktarılan konumları olduğu gibi bırakabilirsiniz; güncelleştirilmiş CSV'yi içeri aktardığınızda bunlar yinelenmez. Mevcut bir konumun adresini değiştirmek isterseniz, CSV'yi içeri aktardığınızda bu konum güncelleştirilir. Bulunan bir şehrin adresini değiştiremezsiniz.

1. CSV'yi açın ve eklemek istediğiniz her konum için yeni bir satırda aşağıdaki alanları doldurarak konumlarınızı ekleyin. Diğer tüm alanları boş bırakın; diğer alanlara girdiğiniz değerler yoksayılır.

   1. **userEntered** (gerekli): Yeni bir LAN Alt Ağı ofis konumunun eklenmesi için 1 olmalıdır
   1. **Ad** (gerekli): Ofis konumunun adı
   1. **Adres** (gerekli): Ofisin fiziksel adresi
   1. **Enlem** (isteğe bağlı): Bing eşler boşsa adres aramasından doldurulur
   1. **Boylam** (isteğe bağlı): Bing eşler tarafından adres aramasından (boşsa) doldurulur
   1. **Egress IP Adresi aralığı 1-5** (isteğe bağlı): Her aralık için bağlantı hattı adını ve ardından geçerli IPv4 CIDR adreslerinin boşlukla ayrılmış listesini girin. Bu değerler, aynı LAN alt ağı IP Adreslerini kullandığınız birden çok ofis konumunu ayırt etmek için kullanılır. Egress IP Adresi aralıklarının tümü /24 ağ boyutu olmalıdır ve /24 girişe dahil değildir.
   1. **LanIps** (gerekli): Bu ofis konumunda kullanılan LAN alt ağ aralıklarını listeleyin. LAN alt ağ kimliklerinin ağ boyutunun /8 ile /29 arasında olabileceği bir CIDR ağ boyutuna sahip olması gerekir. Birden çok LAN alt ağ aralığı virgül veya noktalı virgülle ayrılabilir.

1. Office konumlarınızı ekleyip dosyayı kaydettiğinizde, **tamamlanmış alanın Upload** yanındaki **Gözat** düğmesine tıklayın ve kaydedilen CSV dosyasını seçin.

1. Dosya otomatik olarak doğrulanır. Doğrulama hataları varsa şu hata iletisini görürsünüz: _İçeri aktarma dosyasında bazı hatalar var. Hataları gözden geçirin, içeri aktarma dosyasını düzeltin ve yeniden deneyin._ Belirli alan doğrulama **hatalarının listesi için Hata ayrıntılarını aç** bağlantısına tıklayın.

   > [!div class="mx-imgBorder"]
   > ![CSV içeri aktarma hata iletisi.](../media/m365-mac-perf/m365-mac-perf-import-error.png)

1. Dosyada hata yoksa şu iletiyi görürsünüz: _Rapor hazır. Eklenecek x konum ve güncelleştirilecek x konum bulundu._ CSV'yi karşıya yüklemek için **İçeri Aktar** düğmesine tıklayın.

   > [!div class="mx-imgBorder"]
   > ![CSV içeri aktarmaya hazır ileti.](../media/m365-mac-perf/m365-mac-perf-import-ready.png)

## <a name="cqd-tsv-import-for-lan-subnet-office-locations"></a>LAN alt ağı ofis konumları için CQD TSV İçeri Aktarma

Derleme verilerini Çağrı Kalitesi Panonuza yüklediyseniz, ağ bağlantılarını değerlendirmeye başlamak için bu konumları buraya ekleyebilirsiniz. Bu, mevcut konumlarınızı etkilemez.

Çağrı Kalitesi Panosu'nda [Kiracı Verileri Upload'ne gidin](https://cqd.teams.microsoft.com/spd/#/TenantDataUpload). Derleme verilerinizi karşıya yüklediyseniz bir .tsv dosyasına indirme seçeneği görürsünüz. Arama Kalitesi Panosu'ndan .tsv dosyasını indirin, ardından aşağıdaki adımları izleyerek CQD açılır öğesinde karşıya yükleyin. .tsv dosyasını el ile oluşturmak istiyorsanız, şemayı veri dosyası oluşturma Upload bununla hizalayın veya bunun yerine LAN alt ağı ofis konumları için CSV İçeri Aktarma'yı deneyin.

1. Microsoft 365 ana Bağlantısı penceresinde **Konumlar** sekmesine tıklayın.

2. Konum listesinin hemen üstündeki **Birden çok konumu yönet** düğmesine tıklayın.

   > [!div class="mx-imgBorder"]
   > ![Birden çok konumu yönet menüsü.](../media/m365-mac-perf/m365-mac-perf-import-cqd-manage-multiple.png)

3. **Arama Kalitesi Panosu'ndan Konum ekle'ye** tıklayın; **Arama Kalitesi Panosu'ndan konum ekle** açılır öğesi görüntülenir.

   > [!div class="mx-imgBorder"]
   > ![Arama Kalitesi Panosu açılır öğesinden konumlar ekleyin.](../media/m365-mac-perf/m365-mac-perf-import-cqd-add-locations.png)

4. **Karşıya yüklenecek bir .tsv dosyası seçin** alanının yanındaki **Gözat** düğmesine tıklayın ve kaydedilen TSV dosyasını seçin. Lütfen dosyadaki değerin sekmeyle ayrıldığından emin olun.

5. Dosya otomatik olarak doğrulanır ve office konumları listesine ayrıştırılır. Doğrulama hataları varsa, hataları listelemek için **Dosyanızı karşıya yükleyemedik** açılır öğesi görüntülenir.

   > [!div class="mx-imgBorder"]
   > ![Dosya açılır öğenizi karşıya yükleyemedik.](../media/m365-mac-perf/m365-mac-perf-import-cqd-couldnt-upload.png)

6. Dosyada hata yoksa şu iletiyi görürsünüz: _test.tsv dosyanız karşıya yüklendi ve hazır. Bilgilerinizi karşıya yüklemek için İçeri Aktar'ı seçin._

   > [!div class="mx-imgBorder"]
   > ![Karşıya yüklenecek .tsc dosyasını seçin.](../media/m365-mac-perf/m365-mac-perf-import-cqd-select-tsv.png)

7. Ofis konumlarını karşıya yüklemek için panelin alt kısmındaki **Upload** düğmesine tıklayın.

## <a name="faq"></a>SSS

### <a name="what-is-a-microsoft-365-service-front-door"></a>Microsoft 365 hizmeti ön kapı nedir?

Microsoft 365 hizmeti ön kapısı, Microsoft'un genel ağında Office istemci ve hizmetlerin ağ bağlantılarını sonlandırdığı bir giriş noktasıdır. Microsoft 365 en uygun ağ bağlantısı için ağ bağlantınızın en yakın Microsoft 365 ön kapıya sonlandırılması önerilir.

> [!NOTE]
> Microsoft 365 hizmeti front door' un Azure Market'te bulunan Azure Front Door Service ürünüyle doğrudan bir ilişkisi yoktur.

### <a name="what-is-an-optimal-microsoft-365-service-front-door"></a>En uygun Microsoft 365 hizmeti ön kapı nedir?

En uygun Microsoft 365 hizmet ön kapısı, genellikle şehir veya metro bölgenizde ağ çıkışınıza en yakın kapıdır. Microsoft 365 [bağlantı test aracını](office-365-network-mac-perf-onboarding-tool.md) kullanarak kullanımdaki Microsoft 365 servis ön kapınızın konumunu ve en uygun hizmet ön kapısını belirleyin. Araç, kullanımdaki ön kapınızın en uygun olduğunu belirlerse, Microsoft'un küresel ağına en uygun şekilde bağlanırsınız.

### <a name="what-is-an-internet-egress-location"></a>İnternet çıkış konumu nedir?

İnternet çıkış konumu, ağ trafiğinizin kurumsal ağınızdan çıktığı ve İnternet'e bağlandığı konumdur. Bu, ağ adresi çevirisi (NAT) cihazınız olduğu ve genellikle İnternet Servis Sağlayıcısı (ISS) ile bağlandığınız konum olarak da tanımlanır. Konumunuz ile İnternet çıkış konumunuz arasında uzun bir mesafe görürseniz, bu önemli bir WAN geri talihini gösterebilir.

### <a name="what-license-is-needed-for-this-capability"></a>Bu özellik için hangi lisans gereklidir?

Microsoft 365 yönetim merkezi erişim sağlayan bir lisansa ihtiyacınız vardır.

## <a name="related-topics"></a>İlgili konular

[Ağ içgörülerini Microsoft 365](office-365-network-mac-perf-insights.md)

[ağ değerlendirmesi Microsoft 365](office-365-network-mac-perf-score.md)

[Microsoft 365 bağlantı testi aracı](office-365-network-mac-perf-onboarding-tool.md)

[ağ bağlantısı konum hizmetlerini Microsoft 365](office-365-network-mac-location-services.md)
