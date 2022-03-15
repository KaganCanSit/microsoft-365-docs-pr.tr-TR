---
title: Microsoft 365 bağlantı test aracı
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
description: Microsoft 365 bağlantı test aracı
ms.openlocfilehash: e464b4e651276f8b36f54e91ea0bfc7b7b52d69b
ms.sourcegitcommit: 8423f47fce3905a48db9daefe69c21c841da43a0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2022
ms.locfileid: "63504556"
---
# <a name="microsoft-365-network-connectivity-test-tool"></a>Microsoft 365 bağlantı test aracı

En Microsoft 365 bağlantı test aracı , üzerindedir<https://connectivity.office.com>. Bu, Ağ değerlendirmesi ve ağ içgörüleri için, Genel Durum iletişim Microsoft 365 yönetim merkezi altında bulunan ağ **değerlendirmesine yönelik bir | Bağlantı** menüsü.

> [!IMPORTANT]
> Tüm test raporları yöneticinizle paylaşılır ve oturum Microsoft 365 kiracınıza yüklenmek için kiracınıza giriş yapmak önemlidir.

> [!div class="mx-imgBorder"]
> ![Bağlantı test aracı.](../media/m365-mac-perf/m365-mac-perf-test-tool-page.png)

>[!NOTE]
>Ağ bağlantısı test aracı WW Ticari amaçlı kiracıları destekler, ancak Orta, GCC Yüksek, DoD GCC Çin'de kiracıları desteklemez.

Genel Merkezi'Microsoft 365 Yönetici ağ içgörüleri, her gün toplanan bir kiracınız Microsoft 365 ürün için düzenli olarak yapılan ölçümlere dayalıdır. Buna karşılık, ağ bağlantı Microsoft 365 ile ilgili ağ içgörüleri araçta yerel olarak sınanr.

Ürün içinde sınama sınırlıdır ve yerel olarak kullanıcının çalıştır çalıştırarak daha fazla veri toplayan bu durum daha derin içgörüler sağlar. Web Merkezi'Microsoft 365 Yönetici yönelik ağ içgörüleri, belirli bir ofis konumuyla ilgili bir ağ sorunu olduğunu gösterir. Microsoft 365 bağlantı testi, bu sorunun temel nedenini belirlemeye ve hedefli bir performans geliştirme eylemi sağlamaya yardımcı olabilir.

Bu içgörülerin birlikte kullanılması önerilir; burada Microsoft 365 Yönetici Merkezi'nde her ofis konumu için ağ kalitesi durumu değerlendirilir ve Microsoft 365 bağlantı testini temel alan teste dayalı testlerden sonra daha fazla bilgi bulunabilir.

## <a name="what-happens-at-each-test-step"></a>Her test adıminde neler olur?

### <a name="office-location-identification"></a>Office kimliği

Sınamayı çalıştır *düğmesine tıklaytığınızda* , çalışan test sayfasını gösterir ve ofis konumunu gösteririz. Konumunuz için şehre, bölgeye ve ülkeye göre yazarak veya sizin için algılandığından emin olmak için bunu seçebilirsiniz. Ofis konumunu algılarsanız, araç web tarayıcısında enlem ve boylam bilgisini talep eder ve kullanımdan önce doğruluğu 300 metre ile 300 metreyle sınırlar. Konumu, ağ performansını ölçmek için yapıdan daha doğru bir şekilde tanımlamak gerekmez.

### <a name="javascript-tests"></a>JavaScript testleri

Ofis konumu tanımlayıcısından sonra JavaScript'te bir TCP gecikme süresi testi çalıştıracağız ve hizmetten kullanım hakkında veri talep ederiz ve bu verileri Microsoft 365 ön kapı sunucularına öneririz. Bu sınamalar tamamlandığında, bunları bir sonraki adımdan önce harita üzerinde ve ayrıntılar sekmesinde gösterebilirsiniz.

### <a name="download-the-advanced-tests-client-application"></a>Gelişmiş test istemci uygulamasını indirme

Ardından, gelişmiş test istemci uygulamasının indir indirebilirsiniz. kullanıcıya, istemci uygulamasını başlatması için güvenmekte ve .NET 6.0 Runtime'ın da yüklü olması gerekir.

Ağ bağlantı testinin iki Microsoft 365 vardır: web <https://connectivity.office.com> sitesi ve gelişmiş ağ bağlantısı testleri Windows indirilebilir bir istemci uygulaması. Testleri çoğu için uygulamanın çalışması gerekir. Çalıştırılamaz ve sonuçlar web sayfasına geri döner.

Web tarayıcısı testleri tamamlandıktan sonra gelişmiş istemci test uygulamasını web sitesinden indirmeniz istenir. İstendiğinde dosyayı açın ve çalıştırın.

> [!div class="mx-imgBorder"]
> ![Gelişmiş test istemci uygulaması.](../media/m365-mac-perf/m365-mac-perf-open-run-file.png)

### <a name="start-the-advanced-tests-client-application"></a>Gelişmiş test istemci uygulamasını başlatma

İstemci uygulaması başladıktan sonra, web sayfası bu sonucu gösterecek şekilde güncelleştirmesi olur. Test verileri web sayfasına alınarak alınyacaktır. Her yeni veri geldiğinde sayfa ler ve siz de verileri geldiken gözden geçirebilirsiniz.

### <a name="advanced-tests-completed-and-test-report-upload"></a>Gelişmiş testler tamamlandı ve rapor yüklemesi test edildi

Testler tamamlandığında, web sayfası ve gelişmiş test istemcisinin her ikisi de bunu gösterir. Kullanıcı oturum a ayında ise, test raporu müşterinin kiracısına karşıya yükler.

## <a name="sharing-your-test-report"></a>Test raporlarınızı paylaşma

Test raporu, hesap hesabınız için kimlik Microsoft 365 gerektirir. Yöneticiniz, test raporlarınızı nasıl paylaşabilirsiniz? öğesini seçer.

### <a name="sharing-your-report-with-your-administrator"></a>Raporlarınızı yöneticinizle paylaşma

Bir test raporu oluştuğunda oturum açın, rapor yöneticinizle paylaşılır.

### <a name="sharing-with-your-microsoft-account-team-support-or-other-personnel"></a>Microsoft hesabı ekibiniz, destek veya diğer personelle paylaşma

Test raporları (herhangi bir kişisel kimlik hariç) Microsoft çalışanları ile paylaşılır. Bu paylaşım varsayılan olarak etkinleştirilir ve Sistem Durumu hizmet durumu bilgisinde yöneticiniz tarafından **devre | Veri Merkezi'nde** Ağ Microsoft 365 Yönetici sayfası.

### <a name="sharing-with-other-users-who-sign-in-to-the-same-microsoft-365-tenant"></a>Aynı kiracıda oturum alan diğer kullanıcılarla Microsoft 365 paylaşma

Raporlarınızı paylaşmak istediğiniz kullanıcıları seçebilirsiniz. Seçil özelliği varsayılan olarak etkindir, ancak yöneticiniz tarafından devre dışı bırakılabilir.

> [!div class="mx-imgBorder"]
> ![Test sonuçlarınıza bir bağlantı paylaşma.](../media/m365-mac-perf/m365-mac-perf-share-to-user.png)

### <a name="sharing-with-anyone-using-a-reportid-link"></a>RaporKimlik bağlantısını kullanan herkesle paylaşma

RaporKimlik bağlantısına erişim sağlayarak test raporlarınızı herkesle paylaşabilirsiniz. Bu bağlantı, birine gönderebilirsiniz ve böylelikle oturum açmadan test raporunu getirebilir. Bu paylaşım varsayılan olarak devre dışıdır ve yöneticiniz tarafından etkinleştirilmesi gerekir.

> [!div class="mx-imgBorder"]
> ![Test sonuçlarınıza bağlantı paylaşma.](../media/m365-mac-perf/m365-mac-perf-share-link.png)

## <a name="network-connectivity-test-results"></a>Ağ Bağlantısı Testi Sonuçları

Sonuçlar, Özet ve **Ayrıntılar sekmelerinde** **gösterilir.** Özet sekmesi algılanan ağ çevresini gösteren bir harita ve yakındaki diğer müşterilerle ağ değerlendirmesini Microsoft 365 gösterir. Ayrıca test raporunun paylaşımına olanak sağlar. Özet sonuçları görünümü şöyle olur:

> [!div class="mx-imgBorder"]
> ![Ağ bağlantısı test aracı özet sonuçları.](../media/m365-mac-perf/m365-mac-perf-summary-page.png)

Burada, ayrıntılar sekmesi çıkışını görebilirsiniz. Ayrıntılar sekmesinde, sonuç olumlu olarak karşılaştırıldığında yeşil daire onay işareti gösteririz. Sonuç, ağ içgörü gösteren bir eşiği aşarsa kırmızı üçgen ünlem işareti gösteririz. Aşağıdaki bölümlerde ayrıntılar sekmesi sonuçları satırlarının her biri açıklanmaktadır ve ağ içgörüleri için kullanılan eşikler açıklanmaktadır.

> [!div class="mx-imgBorder"]
> ![Ağ bağlantısı test aracı örnek test sonuçları.](../media/m365-mac-perf/m365-mac-perf-all-details.png)

### <a name="your-location-information"></a>Konum bilginiz

Bu bölümde konumunuzla ilgili test sonuçları yer almaktadır.

#### <a name="your-location"></a>Konumunuz

Kullanıcı konumu, kullanıcıların web tarayıcısında algılanır. Kullanıcının tercihi ile de yaz yazın. Kurumsal ağ çevrenin belirli bölümlerine yönelik ağ mesafelerini tanımlamak için kullanılır. Yalnızca bu konum algılamadan şehir ve diğer ağ noktalarına olan uzaklık rapora kaydedilir.

Kullanıcı ofisi konumu harita görünümünde gösterilir.

#### <a name="network-egress-location-the-location-where-your-network-connects-to-your-isp"></a>Ağ çıkış konumu (ağ ın ISS'nize bağlandığı konum)

Sunucu tarafında ağ çıkış IP adresini tanımlayız. Konum veritabanları, ağ çıkışlarının yaklaşık konumunu bakmak için kullanılır. Bu veritabanları genellikle IP adreslerinin yaklaşık %90'lık bir doğruluk oranına sahiptir. Konum, ağ çıkış IP adresi doğru değilse yanlış bir sonuç verir. Belirli bir IP adresi için bu hatanın oluştuğunu doğrulamak üzere, genel olarak erişilebilir bir ağ IP adresi konumu web sitelerini kullanarak gerçek konumunuzla karşılaştırabilirsiniz.

#### <a name="your-distance-from-the-network-egress-location"></a>Ağ çıkış konumuyla olan uzaklığınız

Bu konumdan ofis konumuyla olan uzaklığı belirleriz. Tcp gecikme süresini 25 ms'den fazla artıracak olması ve kullanıcı deneyimini etkileme olasılığı nedeniyle mesafe **500** km'den (800 kilometre) uzunsa, bu bir ağ içgörü olarak gösterilir.

Harita, kurumsal WAN'ın içindeki ağın geri kullanılabilir olduğunu belirten kullanıcı ofisi konumuyla ilişkili olarak ağ çıkış konumunu gösterir.

Ağ bağlantısını en iyi şekilde sağlamak için kullanıcı ofisi konumlarından İnternet'e yerel ve doğrudan Microsoft 365 kullanın. Yerel ve doğrudan çıkışta yapılan iyileştirmeler, bu ağ içgörülerine yönelik en iyi yollardır.

#### <a name="proxy-server-information"></a>Proxy sunucu bilgileri

Ara sunucuların yerel makinede En İyi Duruma Getirme kategorisindeki ağ Microsoft 365 geçecek şekilde **yapılandırıldığından eminiz**. Kullanıcı ofisi konumuyla proxy sunucularına olan uzaklığı tanımlayanık.

Mesafe önce ICMP ping ile test edilir. Bu başarısız olursa, TCP ping ile test eder ve son olarak da IP adresi konumu veritabanında ara sunucu IP adresini ara sunucu IP adresini aratıriz. Ara sunucu kullanıcı ofisinin bulunduğu konumdan **500** km'den (800 kilometre) uzakta ise, ağ içgörü gösteriyoruz.

#### <a name="virtual-private-network-vpn-you-use-to-connect-to-your-organization"></a>Sanal özel ağ (VPN), organizasyonunıza bağlanmak için kullanın

Bu test, bilgisayarınıza bağlanmak için VPN mi Microsoft 365. Geçen sonuç, VPN'nizin olup olmadığını veya bir VPN'nizin önerilen bölünmüş yapılandırmaya sahip bir VPN'nız olup olmadığını Microsoft 365.

#### <a name="vpn-split-tunnel"></a>VPN Bölme Tunnel

**Exchange Online,** SharePoint Online ve Microsoft Teams için kategori yönlendirmelerini en iyi duruma getirmek için, VPN'de Microsoft Teams'in test edilmiş olup değildir. Bölünmüş iş yükü VPN'den tamamen kaçındır. VPN üzerinden bir iş yükü iş yüküne şey gönderilir. Seçmeli nitelikli iş yükünün VPN üzerinden gönderilen bazı yönlendirmeleri vardır ve bazıları bölünmüş olur. Geçen sonuç, tüm iş yüklerinin bölünmüş olup olduğunu veya seçmeli olarak bölünüyorsa gösterir.

#### <a name="customers-in-your-metropolitan-area-with-better-performance"></a>Metropolitan bölgenize gelen ve daha iyi performansa sahip müşteriler

Kullanıcı ofisi konumuyla hizmet arasındaki ağ gecikme süresi Exchange Online aynı metro Microsoft 365 ilgili diğer müşterilerle karşılaştırıldığında. Aynı metro alanında, %10 veya daha fazla müşteri daha iyi performansa sahipse bir ağ içgörü gösterilir. Bu, kullanıcılarının aynı kullanıcı arabiriminde daha iyi Microsoft 365 anlamına gelir.

Bu ağ içgörüsi, bir şehirli tüm kullanıcıların aynı telekomünikasyon altyapısına, aynı İnternet devrelerine ve Microsoft ağına aynı yakınlığı elde etmelerine temel olarak oluşturulur.

#### <a name="time-to-make-a-dns-request-on-your-network"></a>Ağ üzerinde BIR DNS isteği yapma zamanı

Bu, testlerin yapılandırılan istemci makinede yapılandırılmış olan DNS sunucusunu gösterir. Bu, DNS Yineleyici Çözümleyici sunucusu olabilir, ancak bu seyrek görülen bir durumdur. DNS sonuçlarını önbelleğe alan ve istenmemiş DNS isteklerini başka bir DNS sunucusuna ileten bir DNS iletici sunucusu olması daha olasıdır.

Bu yalnızca bilgiler için sağlanmıştır ve ağ içgörüsine katkıda bulunmak değildir.

#### <a name="your-distance-from-andor-time-to-connect-to-a-dns-recursive-resolver"></a>DNS tekrarlayan çözümleyiciye bağlanmak için gereken mesafe ve/veya süre

Kullanım dışı DNS Yineleyici Çözümleyicisi, belirli bir DNS isteği göndererek ve ardından DNS Ad Sunucusu'dan aynı isteği aldığı IP Adresini sorarak tanımlanır. Bu IP Adresi DNS Tekrarlayıcı Çözümleyici'dir ve konumu bulmak için IP Adresi konum veritabanlarında bilgi bulunacaktır. Kullanıcı ofisi konumuyla DNS Yineleyici Çözümleyici sunucu konumu arasındaki mesafe hesaplanır. Mesafe **500 kilometreden (800** kilometre) uzunsa, bu ağ içgörü olarak gösterilir.

Ağ çıkış IP Adresi'den bakilen konum doğru olmayabilir ve bu da bu sınamadan yanlış bir sonuç atıi olur. Belirli bir IP Adresi için bu hatanın oluştuğunu doğrulamak için, genel olarak erişilebilir ağ IP Adresi konumu web sitelerini kullanabilirsiniz.

Bu ağ içgörüleri, özellikle Exchange Online ön kapı seçimini etkiler. Bu içgörü yerel ve doğrudan ağ çıkış çözümleyicisi için önkul olmalıdır ve ardından DNS Tekrarlayan Çözümleyici bu ağ çıkışa yakın bir konumda olmalıdır.

### <a name="exchange-online"></a>Exchange Online

Bu bölümde, çalışma sayfalarla ilgili test Exchange Online.

#### <a name="exchange-service-front-door-location"></a>Exchange ön kapı konumu

Kullanım için Exchange ön kapı, aynı Outlook ile aynı şekilde tanımlanır ve kullanıcı konumdan buraya ağ TCP gecikme süresini ölçeriz. TCP gecikme süresi gösterilir ve hizmet ön Exchange kullanılan kapı, geçerli konumdaki en iyi hizmet ön kapıları listesiyle karşılaştır gösterilir. En iyi hizmet ön kapılarından biri Exchange ise, bu ağ içgörü olarak gösterilir.

En iyi Exchange ön kapılarından birinin kullanılması şirket ağı çıkışlarından önce ağ geri dönmelerinden kaynaklandırulmalarına neden olabilir; bu durumda yerel ve doğrudan ağ çıkışlarını öneririz. Ayrıca, uzak DNS yineleyici çözümleyici sunucusunun kullanılması da bu durumda DNS yineleyici çözümleyici sunucusunu ağ çıkışla hizalamayı öneririz.

Bir hizmet ön Exchange TCP gecikme süresinde (ms) olası bir iyileştirme hesaplarız. Bu işlem, test edilmiş kullanıcı konumu ağ gecikme süresine bakarak ve ağ gecikme süresinin geçerli konumdan hizmet ön Exchange çıkararak yapılır. Bu fark, potansiyel geliştirme fırsatlarını temsil eder.

#### <a name="best-exchange-service-front-doors-for-your-location"></a>Konumunuz Exchange en iyi hizmet ön kapıları

Bu, konumunuz Exchange hizmet ön kapı konumlarını en iyi şekilde listeler.

#### <a name="service-front-door-recorded-in-the-client-dns"></a>İstemci DNS'sinde kayıtlı hizmet ön kapı

Bu, yönlendirilen Exchange hizmet ön kapı sunucusunun DNS adını ve IP Adresi'ni gösterir. Yalnızca bilgi için sağlanmıştır ve ilgili ağ içgörüleri yoktur.

### <a name="sharepoint-online"></a>SharePoint Online

Bu bölümde, SharePoint Online ve OneDrive ile ilgili test OneDrive.

#### <a name="the-service-front-door-location"></a>Hizmet ön kapı konumu

Kullanım için SharePoint ön kapı, OneDrive istemcisinin tanımları ile aynı şekilde tanımlanır ve kullanıcı ofisi konumdan buraya ağ TCP gecikme süresini ölçeriz.

#### <a name="download-speed"></a>İndirme hızı

15 MB'lık bir dosyanın indirme hızını, servis SharePoint kapıdan ölçüruz. Sonuçta, megabayt cinsinden dosyanın bir saniye içinde megabayttan veya dosyadan SharePoint OneDrive **göstermek için saniye başına megabayt cinsinden gösterilir**. Bu sayı, megabit/saniye başına en düşük devre bant genişliğinin onda biri kadar olması gerekir. Örneğin, 100 MB/sn İnternet bağlantınız varsa, saniye başına 10 megabayt (10 MBps) olabilir.

#### <a name="buffer-bloat"></a>Tampon lekesi

15 Mb indirme sırasında, hizmet ön SharePoint TCP gecikmesini ölçeriz. Bu, yükün altındaki gecikme süresidir ve yük altında değilkenki gecikme süresiyle karşılaştırıldığında. Yük altında olduğunda gecikme süresindeki artış, genellikle yükleniyor olan tüketici ağı cihaz tamponları için attributable (veya doldurulur). Her türlü 1.000 veya daha fazla bilgi için bir ağ içgörü gösteriliyor.

#### <a name="service-front-door-recorded-in-the-client-dns"></a>İstemci DNS'sinde kayıtlı hizmet ön kapı

Bu, yönlendirilen SharePoint hizmet ön kapı sunucusunun DNS adını ve IP Adresi'ni gösterir. Yalnızca bilgi için sağlanmıştır ve ilgili ağ içgörüleri yoktur.

### <a name="microsoft-teams"></a>Microsoft Teams

Bu bölümde, çalışma sayfalarla ilgili test Microsoft Teams.

#### <a name="media-connectivity-audio-video-and-application-sharing"></a>Medya bağlantısı (ses, video ve uygulama paylaşımı)

Bu, hizmet ön Microsoft Teams UDP bağlantısı için test etmektir. Bu engellenmişse, Microsoft Teams TCP kullanılarak çalışmaya devam olabilir, ancak ses ve görüntü engellidir. Skype Kurumsal Online'da Medya Kalitesi ve Ağ Bağlantısı Performansı makalesinde de Microsoft Teams için geçerli olan bu UDP [ağ ölçüleri hakkında daha fazla Skype Kurumsal okuyun](/skypeforbusiness/optimizing-your-network/media-quality-and-network-connectivity-performance).

#### <a name="packet-loss"></a>Paket kaybı

İstemciden gelen ve hizmet ön Microsoft Teams olan 10 saniyelik bir test sesli aramada alınan UDP paket kaybını gösterir. Bu, geçiş için % **1,00'den** daha düşük olmalı.

#### <a name="latency"></a>Gecikme süresi

100 m'den düşük olması gereken, ölçülen UDP **gecikme süresini gösterir**.

#### <a name="jitter"></a>Değişimi

30m'den düşük olması gereken, ölçülen UDP **değişimini gösterir**.

#### <a name="connectivity"></a>Bağlantı

Kullanıcı ofisi konumuyla gerekli tüm ağ uç noktalarına kadar HTTP Microsoft 365 test etmek için. Bunlar 'da yayımlanır [https://aka.ms/o365ip](./urls-and-ip-address-ranges.md). Gerekli ağ uç noktaları için bağlanılamayacak bir ağ içgörü gösterilir.

Bağlantı, bir ara sunucu, güvenlik duvarı veya kurumsal ağ çevresi üzerinde başka bir ağ güvenlik cihazı tarafından engellenmiş olabilir. TCP bağlantı noktası 80 bağlantısı bir HTTP isteğiyle test edilir ve TCP bağlantı noktası 443 bağlantısı bir HTTPS isteğiyle test edilir. Yanıt yoksa, FQDN hata olarak işaretlenir. Bir HTTP yanıt kodu 407 varsa, FQDN hata olarak işaretlenir. HTTP yanıt kodu 403 varsa yanıtın Server özniteliğini kontrol etmek ve proxy sunucusu gibi görünüyorsa bunu hata olarak işaretlliz. Komut satırı araç Windows gerçekleştirmız testleri benzetim curl.exe.

SSL sertifikasını, en iyi duruma Microsoft 365 veya izin ver kategorisindeki en iyi duruma getirmek için gereken her ağ uç noktasına yönelik olarak test etmek için:[https://aka.ms/o365ip](./urls-and-ip-address-ranges.md) Herhangi bir test Microsoft SSL sertifikası bulamazsa, bağlantılı şifrelenmiş ağın bir aracı ağ cihazı tarafından kesişmiş olması gerekir. Kesişen herhangi bir şifreli ağ uç noktasına ağ içgörü gösterilir.

Microsoft tarafından sağ kullanmayan bir SSL sertifikasının bulunduğu yerde, test için FQDN'yi ve kullanım için SSL sertifikasının sahibini gösteririz. Bu SSL sertifikasının sahibi bir proxy sunucu satıcısı veya kurumsal otomatik olarak imzalanan bir sertifika olabilir.

#### <a name="network-path"></a>Ağ yolu

Bu bölümde, Exchange Online hizmet ön SharePoint ve Microsoft Teams hizmet ön kapıya giden ICMP izleme hizmetinin sonuçları yer almaktadır. Yalnızca bilgi için sağlanmıştır ve ilgili ağ içgörüleri yoktur. Üç izleme yönlendirmesi sağlanır. Bir izleme _outlook.office365.com,_ müşterilere bir izleme SharePoint uç veya bir microsoft.sharepoint.com sağlanmazsa microsoft.sharepoint.com izleme yönlendirme ve _world.tr.teams.microsoft.com._

## <a name="connectivity-reports"></a>Bağlantı raporları

Oturum aken, daha önce çalıştırmış olduğunuz raporları gözden geçirsiniz. Ayrıca bunları paylaşabilir veya listeden silebilirsiniz.

> [!div class="mx-imgBorder"]
> ![Raporlar.](../media/m365-mac-perf/m365-mac-perf-reports-list.png)

## <a name="network-health-status"></a>Ağ durumu

Bu, Microsoft'un genel ağına ilişkin, müşterilerin etkilenmesi gibi önemli Microsoft 365 gösterir.

> [!div class="mx-imgBorder"]
> ![Ağ durumu.](../media/m365-mac-perf/m365-mac-perf-status-page.png)

## <a name="testing-from-the-command-line"></a>Komut Satırı'dan sınama

Uzaktan dağıtım ve yürütme araçlarınız tarafından kullanılabilen bir komut satırı yürütülebilir dosyası sağlar ve Microsoft 365 ağ bağlantı test aracı web sitesinde bulunanla aynı testleri çalıştırın.

Komut satırı test aracı buradan indirilebilir: [Komut Satırı Aracı](https://connectivity.office.com/api/AnonymousConnectivityTest/DownloadStandAloneRichClient)

Dosya Gezgini'nde yürütülebilir dosyaya çift tıklayarak Windows çalıştırabilirsiniz veya bunu bir komut isteminden başlatabilirsiniz veya görev zamanlayıcıyla zamanabilirsiniz.

Yürütülebilir dosyayı ilk kez başlatacakken, test gerçekleştirilmeden önce son kullanıcı lisans sözleşmesi (EULA) kabul etmek istenir. EULA'yı zaten okumuş ve kabul ettiysanız, yürütülebilir dosya işlemi için Microsoft-365-Network-Connectivity-Test-EULA-accepted.txt dizinde yürütülebilir dosya olarak adlandırılan boş bir dosya oluşturabilirsiniz. EULA'yı kabul etmek için, istendiğinde komut satırı penceresine 'y' yazarak Enter tuşuna basabilirsiniz.

Yürütülebilir dosya, bu yardım belgelerinin bağlantısını göstermek için /h dosyasının bir komut satırı parametresini kabul eder.

### <a name="results"></a>Sonuçlar
Sonuçların çıkışı, testResults adlı bir klasörde bulunan ve daha önce var olmadığı sürece sürecin geçerli çalışma dizininde oluşturulmuş bir JSON dosyasına yazılır. Çıktının dosya adı biçimi connectivity_test_result_YYYY-MM-DD-HH-MM-SS.json'dir. Sonuçlar, bir ağ bağlantısı test aracı web sitesi için web sayfasında gösterilen çıkışla Microsoft 365 JSON düğümlerdedir. Her çalıştırılan yeni sonuç dosyası oluşturulur ve tek başına yürütülebilir dosya, Yönetim Merkezi Ağ Bağlantısı sayfalarını görüntülemek üzere Microsoft kiracınıza sonuçları yüklemez.

### <a name="launching-from-windows-file-explorer"></a>Dosya Gezgini'Windows başlatma
Sınamayı başlatmak için yürütülebilir dosyayı çift tıklarsınız ve bir komut istemi penceresi görüntülenir.

### <a name="launching-from-the-command-prompt"></a>Komut İstemi'den başlatma
Bir CMD.EXE istemi penceresinde yürütülebilir dosyanın yolunu ve adını yazarak çalıştırabilirsiniz. Dosya adı Microsoft.Connectivity.Test.exe

### <a name="launching-from-windows-task-scheduler"></a>Görev Zamanlayıcı'dan Windows başlatıyor
Görev Windows Zamanlayıcı'da, tek başına test yürütülebilir dosyasını başlatmak için bir görev  eklersiniz. YÜRÜTÜlebilir dosya EULA kabul edilene kadar engelleninceye kadar, görevin geçerli çalışma dizinini EULA'yı kabul etmiş olduğunuz yerde belirtebilirsiniz. süreç arka planda başladı ancak konsolları yoksa, EULA'yı etkileşimli olarak kabul etmezsiniz.

### <a name="more-details-on-the-standalone-executable"></a>Tek başına yürütülebilir dosyayla ilgili daha fazla ayrıntı
Komut satırı aracı, Windows olan Şehir Şehri Ülke bilgilerini bulmak için Konum Hizmetleri'nde yer almaktadır. Denetim Windows Konum Hizmetleri devre dışı bırakılırsa, kullanıcı konumu tabanlı değerlendirmeler boş olur. Başka Windows Ayarlar "Konum hizmetleri" açık olmalı ve "Masaüstü uygulamalarının konumunuza erişmesine izin ver" açık da olmalı.

Komut satırı aracı, yüklü .NET Framework yüklememişse, yükleme yapmaya çalıştır. Ayrıca, yürütülebilir ana test dosyasını Microsoft 365 bağlantı test aracından indirir ve yürütülebilir bir araçtır.

## <a name="faq"></a>SSS

Burada, sık sorulan sorulardan bazılarının yanıtları ve ardından bir sorunuz vardır.

### <a name="what-is-required-to-run-the-advanced-test-client"></a>Gelişmiş test istemcisini çalıştırmak için neler gereklidir?

Gelişmiş test istemcisi için .NET 6.0 Çalışma Zamanı gerekir. Gelişmiş test istemcisini yüklemeden çalıştırsanız, [.NET 6.0 yükleyici sayfasına yönlendirilene kadar devam edebilirsiniz](https://dotnet.microsoft.com/en-us/download/dotnet/6.0/runtime?utm_source=getdotnetcore). Daha fazla bilgi için Masaüstü uygulamalarını çalıştır sütunundan yükleme Windows. Makinede yönetici izinleri .NET 6.0 Çalışma Zamanı'nın yüklemek için gereklidir.

Gelişmiş test istemcisi web sayfasına iletişim kurmak için SignalR kullanır. Bunun için, bağlantı noktası 443 bağlantı noktasının açık **connectivity.service.signalr.net** gerekir. Bu URL, bir kullanıcı istemci uygulaması <https://aka.ms/o365ip> kullanıcısı için bağlantı Microsoft 365 yayımlanamaz.

### <a name="what-is-microsoft-365-service-front-door"></a>Hizmet Microsoft 365 nedir?

Müşteri Microsoft 365 ön kapı, Microsoft'un genel ağın, istemci ve hizmetlerin ağ Office sonlandırılan bir giriş noktasıdır. İnternet'e Microsoft 365 en uygun ağ bağlantısı için, ağ bağlantının şehir veya metro'da en yakın Microsoft 365 kapınıza sonlandırılır.

> [!NOTE]
> Microsoft 365 ön kapı, Azure marketi'nden **edinilen Azure Front Door Service** ürünüyle doğrudan ilişkisi yoktur.

### <a name="what-is-the-best-microsoft-365-service-front-door"></a>Hizmet ön Microsoft 365 en iyi ne olabilir?

En iyi Microsoft 365 hizmet ön kapı (eski adıyla en iyi hizmet ön kapı), genel olarak şehir veya metro bölgenize ağ çıkışa en yakın olan kapıdır. Hizmet Microsoft 365 ve en iyi hizmet ön Microsoft 365 da kullanım için performans aracını kullanın. Araç, en iyi ön kapının kullanım için ön kapınız olduğunu belirlerse, Microsoft'un genel ağına mükemmel bir bağlantı beklemeniz gerekir.

### <a name="what-is-an-internet-egress-location"></a>İnternet çıkış konumu nedir?

İnternet çıkış Konumu, ağ trafiğinizin kurumsal ağdan çıkış bulunduğu ve İnternet'e bağlandığı konumtur. Bu ayrıca, Ağ Adresi Çevirisi (NAT) cihazınızın bulunduğu ve genellikle bir İnternet Servis Sağlayıcısına (ISS) bağlandıysanız konum olarak da tanımlanır. Konumunuzla İnternet çıkış konumunuz arasında uzun bir mesafe görüyorsanız, bu önemli bir WAN gerihali tanımlayabilir.

## <a name="related-topics"></a>İlgili konular

[Ağ Merkezi'nde Microsoft 365 Yönetici bağlantısı](office-365-network-mac-perf-overview.md)

[Microsoft 365 performansı içgörüleri hakkında bilgi edinin](office-365-network-mac-perf-insights.md)

[Microsoft 365 değerlendirmesini geri ayanız](office-365-network-mac-perf-score.md)

[Microsoft 365 Bağlantısı Konum Hizmetleri'ne Bağlan'a](office-365-network-mac-location-services.md)
