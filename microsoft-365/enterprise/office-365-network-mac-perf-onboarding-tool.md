---
title: Microsoft 365 ağ bağlantısı test aracı
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 1/18/2022
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
description: Microsoft 365 ağ bağlantısı test aracı
ms.openlocfilehash: 047a1ad10efa20f2c47491a20855a92bf141eb15
ms.sourcegitcommit: 5c9137f98e688ab23c144e75687399e390bb2601
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/07/2022
ms.locfileid: "64705591"
---
# <a name="microsoft-365-network-connectivity-test-tool"></a>Microsoft 365 ağ bağlantısı test aracı

Microsoft 365 ağ bağlantısı test aracı konumunda <https://connectivity.office.com>bulunur. Bu, Sistem Durumu | altındaki Microsoft 365 yönetim merkezi bulunan ağ değerlendirmesine ve ağ içgörülerine yönelik bir ek araçtır **Bağlantı** menüsü.

> [!IMPORTANT]
> Tüm test raporları yöneticinizle paylaşıldığından ve oturumunuz açıkken kiracıya yüklendiğinden, Microsoft 365 kiracınızda oturum açmanız önemlidir.

> [!div class="mx-imgBorder"]
> ![Bağlantı testi aracı.](../media/m365-mac-perf/m365-mac-perf-test-tool-page.png)

>[!NOTE]
>Ağ bağlantısı test aracı WW Ticari kiracılarını destekler ancak Orta, GCC Yüksek, DoD veya Çin GCC desteklemez.

Microsoft 365 Yönetici Merkezi'ndeki ağ içgörüleri, her gün toplanan Microsoft 365 kiracınız için düzenli ürün içi ölçümleri temel alır. Buna karşılık, Microsoft 365 ağ bağlantı testindeki ağ içgörüleri araçta yerel olarak çalıştırılır.

Ürün içi test sınırlıdır ve testlerin kullanıcıya yerel olarak çalıştırılması daha fazla veri toplar ve daha derin içgörüler elde edilir. Microsoft 365 Yönetici Merkezi'ndeki ağ içgörüleri, belirli bir ofis konumunda ağ sorunu olduğunu gösterir. Microsoft 365 bağlantı testi, bu sorunun kök nedenini belirlemeye ve hedeflenen bir performans geliştirme eylemi sağlamaya yardımcı olabilir.

Bu içgörülerin, ağ kalitesi durumunun Microsoft 365 Yönetici Merkezi'ndeki her ofis konumu için değerlendirilebildiği ve Microsoft 365 bağlantı testini temel alan test dağıtımından sonra daha fazla detayın bulunabileceği durumlarda birlikte kullanılmasını öneririz.

## <a name="what-happens-at-each-test-step"></a>Her test adımında ne olur?

### <a name="office-location-identification"></a>konum belirlemeyi Office

*Testi çalıştır* düğmesine tıkladığınızda, çalışan test sayfasını gösterir ve ofis konumunu belirleriz. Konumunuzu şehre, eyalete ve ülkeye göre yazabilir veya sizin için algılanan bir konum seçebilirsiniz. Ofis konumunu algılarsanız, araç web tarayıcısından enlem ve boylamı talep eder ve kullanımdan önce doğruluğu 300 metre ile 300 metre ile sınırlar. Ağ performansını ölçmek için konumu binadan daha doğru bir şekilde tanımlamak gerekmez.

### <a name="javascript-tests"></a>JavaScript testleri

Office konum belirlemesinden sonra JavaScript'te bir TCP gecikme süresi testi çalıştırıyoruz ve hizmetten kullanımda olan ve önerilen Microsoft 365 hizmet ön kapı sunucuları hakkında veri istiyoruz. Bu testler tamamlandığında, bunları haritada ve bir sonraki adımdan önce görüntülenebileceği ayrıntılar sekmesinde gösteririz.

### <a name="download-the-advanced-tests-client-application"></a>Gelişmiş testler istemci uygulamasını indirme

Ardından, gelişmiş testler istemci uygulamasını indirmeye başlayacağız. İstemci uygulamasını başlatmak için kullanıcıya güveniriz ve .NET 6.0 Çalışma Zamanı da yüklü olmalıdır.

Microsoft 365 ağ bağlantı testinin iki bölümü vardır: web sitesi <https://connectivity.office.com> ve gelişmiş ağ bağlantı testleri çalıştıran indirilebilir bir Windows istemci uygulaması. Testlerin çoğu uygulamanın çalıştırılmasını gerektirir. Sonuçlar çalıştırılırken web sayfasına geri doldurulur.

Web tarayıcısı testleri tamamlandıktan sonra gelişmiş istemci testi uygulamasını web sitesinden indirmeniz istenir. İstendiğinde dosyayı açın ve çalıştırın.

> [!div class="mx-imgBorder"]
> ![Gelişmiş testler istemci uygulaması.](../media/m365-mac-perf/m365-mac-perf-open-run-file.png)

### <a name="start-the-advanced-tests-client-application"></a>Gelişmiş testler istemci uygulamasını başlatma

İstemci uygulaması başlatıldıktan sonra web sayfası bu sonucu gösterecek şekilde güncelleştirilir. Test verileri web sayfasına alınmaya başlar. Yeni veriler her alındığında sayfa güncelleştirilir ve verileri geldikçe gözden geçirebilirsiniz.

### <a name="advanced-tests-completed-and-test-report-upload"></a>Gelişmiş testler tamamlandı ve test raporu karşıya yükleme

Testler tamamlandığında, web sayfası ve gelişmiş testler istemcisi bunu gösterir. Kullanıcı oturum açtıysa, test raporu müşterinin kiracısına yüklenir.

## <a name="sharing-your-test-report"></a>Test raporunuzu paylaşma

Test raporu, Microsoft 365 hesabınızda kimlik doğrulaması gerektirir. Yöneticiniz test raporunuzu nasıl paylaşabileceğinizi seçer. Varsayılan ayarlar, raporlarınızın kuruluşunuzdaki diğer kullanıcılarla paylaşılması için izin verir ve ReportID bağlantısı kullanılamaz. Raporların süresi varsayılan olarak 90 gün sonra dolacaktır.

### <a name="sharing-your-report-with-your-administrator"></a>Raporunuzu yöneticinizle paylaşma

Bir test raporu gerçekleştiğinde oturum açtıysanız rapor yöneticinizle paylaşılır.

### <a name="sharing-with-your-microsoft-account-team-support-or-other-personnel"></a>Microsoft hesabı ekibiniz, desteğiniz veya diğer personelinizle paylaşma

Test raporları (herhangi bir kişisel kimlik hariç) Microsoft çalışanlarıyla paylaşılır. Bu paylaşım varsayılan olarak etkindir ve Sistem Durumu | yöneticiniz tarafından devre dışı bırakılabilir **** Microsoft 365 Yönetici Merkezi'ndeki Ağ Bağlantısı sayfası.

### <a name="sharing-with-other-users-who-sign-in-to-the-same-microsoft-365-tenant"></a>Aynı Microsoft 365 kiracıda oturum açan diğer kullanıcılarla paylaşma

Raporunuzu paylaşmak için kullanıcıları seçebilirsiniz. Seçebilmek varsayılan olarak etkindir, ancak yöneticiniz tarafından devre dışı bırakılabilir.

> [!div class="mx-imgBorder"]
> ![Test sonuçlarınızın bağlantısını bir kullanıcıyla paylaşma.](../media/m365-mac-perf/m365-mac-perf-share-to-user.png)

### <a name="sharing-with-anyone-using-a-reportid-link"></a>ReportID bağlantısı kullanan herkesle paylaşma

Bir ReportID bağlantısına erişim sağlayarak test raporunuzu herkesle paylaşabilirsiniz. Bu bağlantı, oturum açmadan test raporunu ortaya çıkarabilmesi için birine gönderebileceğiniz bir URL oluşturur. Bu paylaşım varsayılan olarak devre dışıdır ve yöneticiniz tarafından etkinleştirilmesi gerekir.

> [!div class="mx-imgBorder"]
> ![Test sonuçlarınızın bağlantısını paylaşma.](../media/m365-mac-perf/m365-mac-perf-share-link.png)

## <a name="network-connectivity-test-results"></a>Ağ Bağlantısı Test Sonuçları

Sonuçlar **Özet** ve **Ayrıntılar** sekmelerinde gösterilir. Özet sekmesinde algılanan ağ çevresinin haritası ve ağ değerlendirmesinin yakındaki diğer Microsoft 365 müşterilerle karşılaştırması gösterilir. Ayrıca test raporunun paylaşılmasına da olanak tanır. Özet sonuçları görünümü şöyle görünür:

> [!div class="mx-imgBorder"]
> ![Ağ bağlantısı test aracı özet sonuçları.](../media/m365-mac-perf/m365-mac-perf-summary-page.png)

Ayrıntılar sekmesi çıkışının bir örneği aşağıda verilmiştir. Ayrıntılar sekmesinde, sonucun olumlu bir şekilde karşılaştırılması durumunda yeşil daire onay işareti gösterilir. Sonucun ağ içgörülerini belirten bir eşiği aşması durumunda kırmızı üçgen ünlem işareti gösteririz. Aşağıdaki bölümlerde ayrıntılar sekmesi sonuç satırlarının her biri ve ağ içgörüleri için kullanılan eşikler açıklanmaktadır.

> [!div class="mx-imgBorder"]
> ![Ağ bağlantısı test aracı örnek test sonuçları.](../media/m365-mac-perf/m365-mac-perf-all-details.png)

### <a name="your-location-information"></a>Konum bilgileriniz

Bu bölümde konumunuzla ilgili test sonuçları gösterilir.

#### <a name="your-location"></a>Konumunuz

Kullanıcı konumu, kullanıcılar web tarayıcısından algılanır. Kullanıcının tercihi ile de yazılabilir. Kurumsal ağ çevresinin belirli bölümlerine ağ uzaklıklarını tanımlamak için kullanılır. Rapora yalnızca bu konum algılamadan şehir ve diğer ağ noktalarına olan uzaklık kaydedilir.

Kullanıcı ofisi konumu harita görünümünde gösterilir.

#### <a name="network-egress-location-the-location-where-your-network-connects-to-your-isp"></a>Ağ çıkış konumu (ağınızın ISS'nize bağlandığı konum)

Sunucu tarafında ağ çıkış IP adresini tanımlarız. Konum veritabanları, ağ çıkışının yaklaşık konumunu aramak için kullanılır. Bu veritabanları genellikle IP adreslerinin yaklaşık %90'ının doğruluğuna sahiptir. Ağ çıkış IP adresinden aranan konum doğru değilse, bu yanlış bir sonuce yol açar. Bu hatanın belirli bir IP adresi için oluşup oluşmadiğini doğrulamak için, gerçek konumunuzla karşılaştırmak için genel olarak erişilebilen ağ IP adresi konumu web sitelerini kullanabilirsiniz.

#### <a name="your-distance-from-the-network-egress-location"></a>Ağ çıkış konumundan uzaklığınız

Bu konumdan ofis konumuna olan uzaklığı belirleriz. Bu, TCP gecikme süresini 25 ms'den fazla artırabileceği ve kullanıcı deneyimini etkileyebileceği için uzaklık **500 milden** (800 kilometre) büyükse ağ içgörüsü olarak gösterilir.

Harita, kuruluş WAN'ının içindeki ağ geri durumunu gösteren kullanıcı ofisi konumuyla ilişkili olarak ağ çıkış konumunu gösterir.

En iyi Microsoft 365 ağ bağlantısı için kullanıcı ofisi konumlarından İnternet'e yerel ve doğrudan ağ çıkışı uygulayın. Bu ağ içgörülerini ele almak için en iyi yol yerel ve doğrudan çıkış geliştirmeleridir.

#### <a name="proxy-server-information"></a>Ara sunucu bilgileri

Ara sunucuların yerel makinede **İyileştir** kategorisindeki Microsoft 365 ağ trafiğini geçirmek üzere yapılandırılıp yapılandırılmadığını belirleriz. Kullanıcı ofisi konumundan ara sunuculara olan uzaklığı belirleriz.

Mesafe ilk olarak ICMP ping ile test edilir. Bu başarısız olursa, TCP ping ile test ederiz ve son olarak bir IP adresi konumu veritabanında ara sunucu IP adresini ararız. Ara sunucu, kullanıcı ofisi konumundan **500 milden** (800 kilometre) daha uzaktaysa bir ağ içgörüsü gösteririz.

#### <a name="virtual-private-network-vpn-you-use-to-connect-to-your-organization"></a>Kuruluşunuza bağlanmak için kullandığınız sanal özel ağ (VPN)

Bu test, Microsoft 365 bağlanmak için VPN kullanıp kullanmadığınızı algılar. Vpn'iniz yoksa veya Microsoft 365 için önerilen bölünmüş tünel yapılandırmasına sahip bir VPN'niz varsa bir geçiş sonucu gösterilir.

#### <a name="vpn-split-tunnel"></a>VPN Split Tunnel

Exchange Online, SharePoint Online ve Microsoft Teams için her **İyileştir** kategori yolu, VPN'de tünellenip tünellenmediğini görmek için test edilir. Ayrılmış bir iş yükü VPN'i tamamen önler. VPN üzerinden tünellenmiş bir iş yükü gönderilir. Seçmeli tünelli bir iş yükünde VPN üzerinden gönderilen bazı yollar ve bazıları ayrılmıştır. Bir geçiş sonucu, tüm iş yüklerinin bölünmüş veya seçmeli tünelli olup olmadığını gösterir.

#### <a name="customers-in-your-metropolitan-area-with-better-performance"></a>Metropol bölgenizdeki müşteriler daha iyi performansla

Kullanıcı ofisi konumu ile Exchange Online hizmeti arasındaki ağ gecikme süresi, aynı metro alanındaki diğer Microsoft 365 müşterilerle karşılaştırılır. Aynı metro alanındaki müşterilerin %10'unun veya daha fazlasının daha iyi performansa sahip olması durumunda ağ içgörüleri gösterilir. Bu, kullanıcılarının Microsoft 365 kullanıcı arabiriminde daha iyi performansa sahip olacağı anlamına gelir.

Bu ağ içgörüleri, bir şehirdeki tüm kullanıcıların aynı telekomünikasyon altyapısına ve İnternet bağlantı hatlarına ve Microsoft ağına aynı yakınlığı temel alarak oluşturulur.

#### <a name="time-to-make-a-dns-request-on-your-network"></a>Ağınızda DNS isteğinde bulunma zamanı

Bu, testleri çalıştıran istemci makinede yapılandırılmış DNS sunucusunu gösterir. Bu bir DNS Özyinelemeli Çözümleyici sunucusu olabilir, ancak bu sık karşılaşılan bir durumdur. Dns sonuçlarını önbelleğe alan ve herhangi bir eklenmemiş DNS isteğini başka bir DNS sunucusuna ileten bir DNS ileticisi sunucusu olma olasılığı daha yüksektir.

Bu yalnızca bilgi için sağlanır ve herhangi bir ağ içgörüsüsüne katkıda bulunmaz.

#### <a name="your-distance-from-andor-time-to-connect-to-a-dns-recursive-resolver"></a>DNS özyinelemeli çözümleyiciye bağlanmak için ve/veya zamandan uzaklığınız

Kullanımda olan DNS Özyinelemeli Çözümleyicisi, belirli bir DNS isteği oluşturup dns ad sunucusundan aynı isteği aldığı IP Adresini isteyerek tanımlanır. Bu IP Adresi, DNS Özyinelemeli Çözümleyici'dir ve konumu bulmak için IP Adresi konum veritabanlarında aranacaktır. Ardından kullanıcı ofisi konumundan DNS Özyinelemeli Çözümleyici sunucu konumuna olan uzaklık hesaplanır. Bu, mesafe **500 milden (800** kilometre) büyükse bir ağ içgörüsü olarak gösterilir.

Ağ çıkış IP Adresinden aranan konum doğru olmayabilir ve bu, bu testten yanlış bir sonuç elde edilmesine neden olabilir. Bu hatanın belirli bir IP Adresi için oluşup oluşmadiğini doğrulamak için genel olarak erişilebilen ağ IP Adresi konumu web sitelerini kullanabilirsiniz.

Bu ağ içgörüleri özellikle Exchange Online hizmeti ön kapı seçimini etkiler. Bu içgörü yerel ve doğrudan ağ çıkışını ele almak için bir ön koşul olmalı ve ardından DNS Özyinelemeli Çözümleyici bu ağ çıkışına yakın bir yerde bulunmalıdır.

### <a name="exchange-online"></a>Exchange Online

Bu bölümde Exchange Online ile ilgili test sonuçları gösterilir.

#### <a name="exchange-service-front-door-location"></a>Exchange servis ön kapı konumu

Kullanımda olan Exchange hizmeti front door, Outlook bunu yaptığı şekilde tanımlanır ve kullanıcı konumundan bu hizmete ağ TCP gecikmesini ölçeriz. TCP gecikme süresi gösterilir ve kullanımdaki Exchange hizmet ön kapısı, geçerli konum için en iyi hizmet ön kapıları listesiyle karşılaştırılır. En iyi Exchange hizmet ön kapılarından biri kullanımda değilse, bu bir ağ içgörüsü olarak gösterilir.

En iyi Exchange hizmet ön kapılarından birinin kullanılmaması, şirket ağ çıkışından önce ağ geri sıkışması olabilir. Bu durumda yerel ve doğrudan ağ çıkışı öneririz. Bunun nedeni, uzak DNS özyinelemeli çözümleyici sunucusunun kullanılması olabilir. Bu durumda, DNS özyinelemeli çözümleyici sunucusunu ağ çıkışıyla hizalamanızı öneririz.

Exchange hizmeti ön kapısında TCP gecikme süresinde (ms) olası bir iyileştirmeyi hesaplıyoruz. Bu işlem, test edilen kullanıcı ofisi konumu ağ gecikme süresine bakarak ve ağ gecikmesini geçerli konumdan hizmet ön kapısı Exchange dolaplara çıkararak yapılır. Fark, geliştirme için olası fırsatı temsil eder.

#### <a name="best-exchange-service-front-doors-for-your-location"></a>Konumunuz için en iyi Exchange hizmeti ön kapı

Bu, konumunuz için şehre göre en iyi Exchange hizmet ön kapı konumlarını listeler.

#### <a name="service-front-door-recorded-in-the-client-dns"></a>İstemci DNS'sine kaydedilen hizmet ön kapısı

Bu, yönlendirildiğiniz Exchange hizmeti ön kapı sunucusunun DNS adını ve IP Adresini gösterir. Yalnızca bilgi için sağlanır ve ilişkili ağ içgörüleri yoktur.

### <a name="sharepoint-online"></a>SharePoint Online

Bu bölümde SharePoint Online ve OneDrive ile ilgili test sonuçları gösterilir.

#### <a name="the-service-front-door-location"></a>Hizmet ön kapı konumu

Kullanımda olan SharePoint hizmeti ön kapısı, OneDrive istemcisiyle aynı şekilde tanımlanır ve kullanıcı ofisi konumundan ona kadar ağ TCP gecikmesini ölçeriz.

#### <a name="download-speed"></a>İndirme hızı

SharePoint hizmeti ön kapısından 15 Mb'lık bir dosyanın indirme hızını ölçüyoruz. Sonuç, megabayt cinsinden hangi boyut dosyasının SharePoint veya OneDrive **bir saniyede** indirilebileceğini göstermek için saniyede megabayt cinsinden gösterilir. Sayı, saniyedeki megabit cinsinden minimum devre bant genişliğinin onda birine benzer olmalıdır. Örneğin 100 mb/sn İnternet bağlantınız varsa saniyede 10 megabayt (10 MB/sn) bekleyebilirsiniz.

#### <a name="buffer-bloat"></a>Arabellek şişkinliği

15 Mb indirme sırasında SharePoint hizmeti ön kapısına TCP gecikmesini ölçeriz. Bu, yük altındaki gecikme süresidir ve yük altında değilken gecikme süresiyle karşılaştırılır. Yük altındayken gecikme süresindeki artış genellikle yüklenen (veya şişirilmiş) tüketici ağ cihazı arabelleklerine atf edilir. 1.000 veya daha fazla herhangi bir blob için bir ağ içgörüsü gösterilir.

#### <a name="service-front-door-recorded-in-the-client-dns"></a>İstemci DNS'sine kaydedilen hizmet ön kapısı

Bu, yönlendirildiğiniz SharePoint hizmeti ön kapı sunucusunun DNS adını ve IP Adresini gösterir. Yalnızca bilgi için sağlanır ve ilişkili ağ içgörüleri yoktur.

### <a name="microsoft-teams"></a>Microsoft Teams

Bu bölümde Microsoft Teams ile ilgili test sonuçları gösterilir.

#### <a name="media-connectivity-audio-video-and-application-sharing"></a>Medya bağlantısı (ses, video ve uygulama paylaşımı)

Bu, Microsoft Teams hizmeti ön kapısına UDP bağlantısını sınar. Bu engellenirse, Microsoft Teams TCP kullanarak çalışmaya devam edebilir, ancak ses ve görüntü engellenir. Skype Kurumsal [Online'da Medya Kalitesi ve Ağ Bağlantısı Performansı'ndaki Microsoft Teams](/skypeforbusiness/optimizing-your-network/media-quality-and-network-connectivity-performance) için de geçerli olan bu UDP ağ ölçümleri hakkında daha fazla bilgi edinin.

#### <a name="packet-loss"></a>Paket kaybı

İstemciden Microsoft Teams hizmeti ön kapısına yapılan 10 saniyelik test sesli çağrısında ölçülen UDP paket kaybını gösterir. Bu, geçiş için **%1,00'den** düşük olmalıdır.

#### <a name="latency"></a>Gecikme

**100ms'den** daha düşük olması gereken ölçülen UDP gecikme süresini gösterir.

#### <a name="jitter"></a>Değişimi

**30ms'den** daha düşük olması gereken ölçülen UDP değişimini gösterir.

#### <a name="connectivity"></a>Bağlantı

Kullanıcı ofisi konumundan tüm gerekli Microsoft 365 ağ uç noktalarına HTTP bağlantısını test ediyoruz. Bunlar adresinde [https://aka.ms/o365ip](./urls-and-ip-address-ranges.md)yayımlanır. Bağlanılamayan gerekli ağ uç noktaları için bir ağ içgörüsü gösterilir.

Bağlantı, kurumsal ağ çevresi üzerindeki bir ara sunucu, güvenlik duvarı veya başka bir ağ güvenlik cihazı tarafından engellenebilir. TCP bağlantı noktası 80'e bağlantı bir HTTP isteğiyle test edilir ve 443 numaralı TCP bağlantı noktasına bağlantı bir HTTPS isteğiyle test edilir. Yanıt yoksa FQDN hata olarak işaretlenir. HTTP yanıt kodu 407 varsa FQDN hata olarak işaretlenir. Bir HTTP yanıt kodu 403 varsa yanıtın Sunucu özniteliğini denetleriz ve bir ara sunucu gibi görünüyorsa bunu hata olarak işaretleriz. Windows komut satırı aracı curl.exe gerçekleştirdiğimiz testlerin benzetimini yapabilirsiniz.

SSL sertifikasını, '[https://aka.ms/o365ip](./urls-and-ip-address-ranges.md)de tanımlandığı şekilde iyileştirme veya izin verme kategorisindeki her gerekli Microsoft 365 ağ uç noktasında test ediyoruz. Herhangi bir test bir Microsoft SSL sertifikası bulamazsa, bağlanan şifrelenmiş ağın aracı bir ağ cihazı tarafından kesilmiş olması gerekir. Kesilen şifrelenmiş ağ uç noktaları üzerinde ağ içgörüleri gösterilir.

Microsoft tarafından sağlanmayan bir SSL sertifikası bulunduğunda, test için FQDN'yi ve kullanımdaki SSL sertifika sahibini gösteririz. Bu SSL sertifika sahibi bir ara sunucu satıcısı veya kurumsal otomatik olarak imzalanan bir sertifika olabilir.

#### <a name="network-path"></a>Ağ yolu

Bu bölümde, Exchange Online hizmeti ön kapısına, SharePoint Online hizmet ön kapısına ve Microsoft Teams hizmeti ön kapısına ICMP izleme yönlendirmesinin sonuçları gösterilir. Yalnızca bilgi için sağlanır ve ilişkili ağ içgörüleri yoktur. Sağlanan üç izleme yolu vardır. _outlook.office365.com_ bir izleme yolu, ön ucu SharePoint müşterilere veya sağlanmadıysa _microsoft.sharepoint.com_ bir izleme yolu ve _world.tr.teams.microsoft.com_ bir izleme yolu.

## <a name="connectivity-reports"></a>Bağlantı raporları

Oturum açtığınızda, çalıştırdığınız önceki raporları gözden geçirebilirsiniz. Ayrıca bunları paylaşabilir veya listeden silebilirsiniz.

> [!div class="mx-imgBorder"]
> ![Rapor.](../media/m365-mac-perf/m365-mac-perf-reports-list.png)

## <a name="network-health-status"></a>Ağ sistem durumu

Bu, Microsoft'un küresel ağında Microsoft 365 müşterileri etkileyebilecek önemli sistem durumu sorunlarını gösterir.

> [!div class="mx-imgBorder"]
> ![Ağ sistem durumu.](../media/m365-mac-perf/m365-mac-perf-status-page.png)

## <a name="testing-from-the-command-line"></a>Komut Satırından Test Etme

Uzaktan dağıtım ve yürütme araçlarınız tarafından kullanılabilecek bir komut satırı yürütülebilir dosyası sağlıyoruz ve Microsoft 365 ağ bağlantısı test aracı web sitesinde bulunan testlerin aynısını çalıştırıyoruz.

Komut satırı test aracı buradan indirilebilir: [Komut Satırı Aracı](https://connectivity.office.com/api/AnonymousConnectivityTest/DownloadStandAloneRichClient)

Windows Dosya Gezgini'da yürütülebilir dosyaya çift tıklayarak çalıştırabilir veya komut isteminden başlatabilir veya görev zamanlayıcı ile zamanlayabilirsiniz.

Yürütülebilir dosyayı ilk kez başlattığınızda, test yapılmadan önce son kullanıcı lisans sözleşmesini (EULA) kabul etmek isteyip istemediğiniz sorulur. EULA'yı zaten okuduysanız ve kabul ettiyseniz yürütülebilir işlem başlatıldığında geçerli çalışma dizininde Microsoft-365-Network-Connectivity-Test-EULA-accepted.txt adlı boş bir dosya oluşturabilirsiniz. EULA'yı kabul etmek için 'y' yazabilir ve istendiğinde komut satırı penceresinde Enter tuşuna basabilirsiniz.

Yürütülebilir dosya, bu yardım belgelerinin bağlantısını göstermek için /h komut satırı parametresini kabul eder.

### <a name="results"></a>Sonuç -ları
Sonuçların çıktısı, henüz mevcut olmadığı sürece işlemin geçerli çalışma dizininde oluşturulan TestResults adlı klasördeki bir JSON dosyasına yazılır. Çıktının dosya adı biçimi connectivity_test_result_YYYY-MM-DD-HH-MM-SS.json şeklindedir. Sonuçlar, Microsoft 365 ağ bağlantısı test aracı web sitesinin web sayfasında gösterilen çıktıyla eşleşen JSON düğümlerinde bulunur. Her çalıştırdığınızda yeni bir sonuç dosyası oluşturulur ve tek başına yürütülebilir dosya, Sonuçları Yönetim Merkezi Ağ Bağlantısı sayfalarında görüntülemek üzere Microsoft kiracınıza yüklemez.

### <a name="launching-from-windows-file-explorer"></a>Windows Dosya Gezgini'den başlatma
Testi başlatmak için yürütülebilir dosyaya çift tıklayabilirsiniz ve bir komut istemi penceresi görüntülenir.

### <a name="launching-from-the-command-prompt"></a>Komut İsteminden Başlatma
CMD.EXE komut istemi penceresinde çalıştırılacak yürütülebilir dosyanın yolunu ve adını yazabilirsiniz. Dosya adı Microsoft.Connectivity.Test.exe

### <a name="launching-from-windows-task-scheduler"></a>Windows Görev Zamanlayıcı'dan başlatma
Windows Görev Zamanlayıcı'da, tek başına test yürütülebilir dosyasını başlatmak için bir görev ekleyebilirsiniz. Yürütülebilir dosya EULA kabul edilene kadar engel olacağından, eula kabul edilen dosyayı oluşturduğunuz görevin geçerli çalışma dizinini belirtmeniz gerekir. İşlem konsolu olmadan arka planda başlatılırsa EULA'yı etkileşimli olarak kabul edemezsiniz.

### <a name="more-details-on-the-standalone-executable"></a>Tek başına yürütülebilir dosya hakkında daha fazla ayrıntı
Komut satırı aracı, bazı uzaklıkları belirlemek için kullanıcıların City State Country bilgilerini bulmak için Windows Konum Hizmetleri'ni kullanır. Windows Konum Hizmetleri denetim masasında devre dışı bırakılırsa, kullanıcı konumu tabanlı değerlendirmeler boş olur. Windows Ayarlar "Konum hizmetleri" açık olmalı ve "Masaüstü uygulamalarının konumunuza erişmesine izin ver" de açık olmalıdır.

Komut satırı aracı, henüz yüklü değilse .NET Framework yüklemeyi dener. Ayrıca Microsoft 365 ağ bağlantısı test aracından ana test yürütülebilir dosyasını indirir ve bunu başlatır.

## <a name="faq"></a>SSS

Burada sık sorulan sorularımızdan bazılarının yanıtları yer alır.

### <a name="what-is-required-to-run-the-advanced-test-client"></a>Gelişmiş test istemcisini çalıştırmak için ne gereklidir?

Gelişmiş test istemcisi .NET 6.0 Çalışma Zamanı gerektirir. Gelişmiş test istemcisini bu yükleme olmadan çalıştırırsanız [.NET 6.0 yükleyici sayfasına](https://dotnet.microsoft.com/en-us/download/dotnet/6.0/runtime?utm_source=getdotnetcore) yönlendirilirsiniz. Windows için Masaüstü uygulamalarını çalıştır sütunundan yüklemeyi unutmayın. .NET 6.0 Runtime'ı yüklemek için makinedeki yönetici izinleri gereklidir.

Gelişmiş test istemcisi, web sayfasıyla iletişim kurmak için SignalR kullanır. Bunun için **connectivity.service.signalr.net** tcp bağlantı noktası 443 bağlantısının açık olduğundan emin olmanız gerekir. Microsoft 365 istemci uygulaması kullanıcısı için bağlantı gerekli olmadığından bu URL'de <https://aka.ms/o365ip> yayımlanmaz.

### <a name="what-is-microsoft-365-service-front-door"></a>Microsoft 365 hizmeti ön kapı nedir?

Microsoft 365 hizmeti ön kapısı, Microsoft'un genel ağında Office istemci ve hizmetlerin ağ bağlantılarını sonlandırdığı bir giriş noktasıdır. Microsoft 365 en uygun ağ bağlantısı için, ağ bağlantınızın şehrinizdeki veya metronuzdaki en yakın Microsoft 365 ön kapıya sonlandırılması önerilir.

> [!NOTE]
> Microsoft 365 hizmeti front door' un Azure Market'te bulunan **Azure Front Door Service** ürünüyle doğrudan bir ilişkisi yoktur.

### <a name="what-is-the-best-microsoft-365-service-front-door"></a>En iyi Microsoft 365 hizmeti ön kapı hangisidir?

En iyi Microsoft 365 hizmet ön kapı (eski adıyla en uygun hizmet ön kapı), genellikle şehir veya metro bölgenizde, ağ çıkışınıza en yakın olan kapıdır. Kullanımdaki Microsoft 365 hizmet ön kapınızın konumunu ve en iyi servis ön kapılarınızı belirlemek için Microsoft 365 ağ performans aracını kullanın. Araç, kullanımdaki ön kapınızın en iyilerinden biri olduğunu belirlerse, Microsoft'un küresel ağına harika bir bağlantı bekleyebilirsiniz.

### <a name="what-is-an-internet-egress-location"></a>İnternet çıkış konumu nedir?

İnternet çıkış Konumu, ağ trafiğinizin kurumsal ağınızdan çıktığı ve İnternet'e bağlandığı konumdur. Bu, ağ adresi çevirisi (NAT) cihazınız olduğu ve genellikle İnternet Servis Sağlayıcısı (ISS) ile bağlandığınız konum olarak da tanımlanır. Konumunuz ile İnternet çıkış konumunuz arasında uzun bir mesafe görürseniz, bu önemli bir WAN geri dönüş değerini tanımlayabilir.

## <a name="related-topics"></a>İlgili konular

[Microsoft 365 Yönetici Merkezi'nde ağ bağlantısı](office-365-network-mac-perf-overview.md)

[ağ performansı içgörülerini Microsoft 365](office-365-network-mac-perf-insights.md)

[ağ değerlendirmesi Microsoft 365](office-365-network-mac-perf-score.md)

[ağ bağlantısı konum hizmetlerini Microsoft 365](office-365-network-mac-location-services.md)
