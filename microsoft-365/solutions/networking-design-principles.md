---
title: Ağ oluşturma (buluta) — One Architect'in görünüm noktası
description: En yaygın hatalardan kaçınarak ağın bulut bağlantısı için nasıl en iyi duruma getirmek olduğunu öğrenin.
ms.author: bcarter
author: brendacarter
manager: bcarter
ms.audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: medium
ms.collection:
- M365-identity-device-management
- M365-security-compliance
ms.custom: ''
f1.keywords: NOCSH
ms.openlocfilehash: 519f3035040f563a6f3663198be3952830cb21cb
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62983614"
---
# <a name="networking-up-to-the-cloudone-architects-viewpoint"></a>Ağ oluşturma (buluta) — One Architect'in görünüm noktası

Bu makalede, Microsoft'ta Güvenlik & Uyumluluk Mimarı [Ed Fisher](https://www.linkedin.com/in/edfisher/), en yaygın hatalardan kaçınarak bulut bağlantısı için ağın nasıl en iyi duruma getirmekte olduğunu açıklar. 

## <a name="about-the-author"></a>Yazar hakkında

![Ed Fisher fotoğrafı.](../media/solutions-architecture-center/ed-fisher-networking.jpg) 

Şu anda Perakende ve Tüketici Ürünleri ekibimizde Güvenlik ve Uyumluluk üzerine odaklanan Ana Teknik & sahibiyim. Son on yıldır Office 365 müşterilerle çalıştım. Dünyanın her yanında dağıtılmış milyonlarca kullanıcılı kamu kuruluşları ve kuruluşlar için birkaç konumun ve arasında, çoğunluğu on binlerce kullanıcıya, dünyanın çeşitli yerlerinde birden fazla konuma sahip olan, çok sayıda başka müşteriyle, yüksek derecede güvenlik gereksinimlerine ve çok sayıda uyumluluk gereksinimlerine ihtiyacı olan küçük mağazalarla çalıştım. Yüzlerce kuruluşa ve milyonlarca kullanıcıya güvenli bir şekilde buluta taşımaya yardımcı oldum.

Son 25 yılı güvenlik, altyapı ve ağ mühendisliğini içeren bir arka planla ve Microsoft'a katılmadan önce önceki iki işverenimi Office 365'e taşıdım, ben bu tabloda pek çok kez sizin yanındayım ve bunun nasıl bir şey olduğunu hatırlamıyorum. İki müşteri her zaman aynı olmazken, çoğu müşteri benzer ihtiyaçlara sahip olur ve herhangi bir SaaS veya PaaS platformu gibi standartlaştırılmış bir hizmeti tüketirken en iyi yaklaşımlar aynı olur.

## <a name="its-not-the-network--its-how-youre-misusing-it"></a>Ağ değil, nasıl (yanlış) kullanıyorsanız o şekildedir!

Ne kadar çok olursa olsun, hiçbir zaman yaratıcı güvenlik ekiplerinin ve ağ ekiplerinin  Microsoft bulut hizmetleriyle nasıl bağlantı kuracaklarını düşünmelerine ne kadar yardımcı olamayan bir durumla karşıma çıkamaz. Her zaman, ne yapmaya çalıştığı veya neleri daha iyi, daha kolay, daha düşük maliyetli ve daha iyi performansa sahip yolların sözlerine yer vermek zorunda kalmadan kullanmaya karar vermek için bir  güvenlik ilkesi, uyumluluk standardı veya daha iyi bir yol vardır. 

Bu tür bir şey bana artmış durumdayken, genellikle bu zor işi almaya ve nasıl ve nedenlerin üzerinden geçerek onları olması gereken yere götürmeye hazır olurum. Ancak, tamamen Frank olursam, bazen onların yapacaklarını yapmalarına izin vermenizi istiyorum ve sonunda bunu kabul etmelerine izin verdim demek istiyorum. Bazen bunu yapmak istediğimde, bunu *yapmak istemiyorum*. Bu gönderiye eklayacağım her şeyi açıklamaya çalışmam. Rolünüz ne olursa olsun, organizasyonunız Microsoft bulut hizmetlerini kullanmak istiyorsa, muhtemelen aşağıdaki durumlarda size yardımcı olacak bazı güzel şeyler vardır.

## <a name="guiding-principles"></a>Yol gösteren ilkeler

Burada ne yapıyoruz? ile ilgili bazı temel kurallarla başlayalım. Gerçek güvenliği koruyarak en düşük karmaşıklığı ve en yüksek performansı sağlamak için bulut hizmetleriyle güvenli bir şekilde nasıl bağlantı kur üzerinden tartışırken, bu konu hakkında konuşuyoruz. Aşağıdakilerin hiçbiri, siz veya müşteriniz her şey için favori proxy sunucularınızı kullanamasanız bile bunların hiçbirinin tersini yapmaktır.

- **Bunun nedeni, bunu** yapmak anlamına da gelen bir şey değil: Ya da Ahuassic Park filmi'den Dr. Ian Zaman'ı yardım etmek için "... Evet, evet, ama güvenlik ekibinin içinde o kadar çok sorun oldu ki, öyle olup olmadığını düşünmekten vazgeçerler."
- **Güvenlik karmaşıklık anlamına değildir**: Yalnızca daha fazla para harcadığınız, daha fazla cihaza yönlendirerek veya daha fazla düğmeyi tıklatmanız nedeniyle daha güvenli olmaznız.
- **Office 365 İnternet üzerinden erişilir**: Ancak bu İnternet'i Office 365 olanla aynı şey değildir. Bu, Microsoft tarafından yönetilen ve sizin yönetiminizi yapan bir SaaS hizmetidir. İnternet'te ziyaret ettiğiniz web sitelerinden farklı olarak, aslında perdenin arkasına göz atabilirsiniz ve amaçlarınıza ulaşabilirsiniz ve amaçlarınıza uygun olduğunu anlıyoruz ki, ilkelerinize ve uyumluluk standartlarına uymanız için gereken denetimleri uygulayabilirsiniz.
- **Hızlı** erişim kötü, yerelleştirilmiş ara erişimler iyidir: Herkes her zaman tüm İnternet trafiklerini merkezi bir noktaya geri almak ister; bu nedenle genellikle ilkeyi izleyebilir ve zorunlu hale gelirler, ancak çoğu durumda tüm konumlarında İnternet erişimi sağlamadan daha düşük olabilir veya böyle yapmaları gerekir. Ancak bu tiryaklar tam olarak böyledir... trafik yoğunluğu olan noktalar. Kullanıcılarınızı Gözatma veya kedi videoları akışına engel olan hiçbir sorun yoktur, ancak iş açısından kritik iş uygulaması trafiğinizi aynı şekilde kabul etmeyin.
- **DNS mutlu değilse,** hiçbir şey mutlu olmaz: En iyi tasarlanmış ağ kötü DNS tarafından (dünyanın diğer alanlarındaki sunuculara yönelik istekler ister ISS'nizin DNS sunucularını veya DNS çözümleme bilgilerini önbelleğe alan diğer genel DNS sunucularını kullanarak) daha küçük bir DNS tarafından iş için kullanılabilir.
- **Bunu önceden yaptığınız** için, şu anda bunu böyle yapmak demek değildir: Teknoloji sürekli değişir ve Office 365 bir istisna değildir. Şirket içi hizmetler için geliştirilen ve dağıtılan güvenlik önlemleri uygulamak veya web'de gezinmeyi kontrol etmek aynı güvenlik güvencesi düzeyini sağlamaz ve performansı önemli ölçüde olumsuz etkileyebilir.
- **Office 365 İnternet üzerinden erişilacak şekilde inşa** edilmiş olması: Bir kısaca bu kadar. Kullanıcılarınız ile kenarınız arasında ne yapmak istediğinize bakmadan, trafik ağınıza ve ağımıza başlamadan önce İnternet üzerinden yine gider. Ağ gecikmeye duyarlı bazı trafiği doğrudan kendi ağımıza yönlendiren Azure ExpressRoute kullansanız bile, İnternet bağlantısı kesinlikle gereklidir. Kabul et. Fazla gözden geçirmeyin.

## <a name="where-bad-choices-are-often-made"></a>Kötü seçimlerin sık yapılan yeri

Güvenlik adı altında hatalı kararlar alınan birçok yer varken, müşterilerle en sık karşılaştığım yer bunlardır. Birçok müşteri görüşmesi, bunların hepsini bir kerede içerir.

### <a name="insufficient-resources-at-the-edge"></a>Edge'de yetersiz kaynaklar

Çok az müşteri yeşil alan ortamlarının dağıtımında yer aldı ve kullanıcılarının çalışma ve İnternet çıkışlarının nasıl olduğuyla ilgili yıl deneyimine sahiptir. Müşterilerin ara sunucularının olması veya doğrudan erişime izin vermeleri ve yalnızca NAT giden trafiğine izin vermeleri gibi, bunu yıllar boyunca yapıyor ve geleneksel iç uygulamaları buluta taşıarak kenarlarına ne kadar daha bağlanacaklarını düşünmezler.

Bant genişliği her zaman önemli bir konudur, ancak NAT cihazlarının artan yükü işlemek için yeterli beygir gücüne sahip olamayabilirsiniz ve kaynakları serbest etmek için bağlantıları hemen kapatmaya başlayabilirler. Office 365'a bağlanan istemci yazılımlarının çoğu kalıcı bağlantılar olmasını ve tam olarak kullanan kullanıcıların Office 365 32 veya daha fazla eş zamanlı bağlantı olmasını bekler. NAT cihazı onları bir şekilde bırakıyorsa, artık orada olmayan bağlantıları kullanmaya çalışılan uygulamalar yanıt vermemeye devam ediyor olabilir. Bu yeni bağlantıdan vazgeçer ve yeni bağlantılar kurmayı deneseler, ağ dişlinize daha da fazla yük sağlarlar.

### <a name="localized-breakout"></a>Yerelleştirilmiş kesme

Bu listede yer alan diğer her şey tek bir yere, yani ağdan ve mümkün olduğunca hızlı bir şekilde ağımıza geliyor. Kullanıcı trafiğinizi merkezi bir çıkış noktasına geri alma, özellikle de bu çıkış noktası kullanıcılarınızı kullananlardan başka bir bölgede olduğunda gereksiz gecikmeye neden olur ve hem istemci deneyimini hem de indirme hızlarını etkiler. Microsoft, her büyük ISS'ye göre her temel ISS'yi temel alan tüm hizmetlerimiz ve eşliğimiz için ön uçlarla dünyanın her yerinde iletişim durumu noktalarını bulundurarak, kullanıcılarının trafiğini yerel olarak dışarı yönlendirmenin minimum gecikme süresiyle ağımıza hızlı bir şekilde girilesini sağlar.

### <a name="dns-resolution-traffic-should-follow-the-internet-egress-path"></a>DNS çözümleme trafiği İnternet çıkış yolunu izlemeli

Elbette bir istemcinin uç noktaları bulması için DNS'yi kullanması gerekir. Microsoft'un DNS sunucuları, isteğin kaynağına en yakın İnternet terimleriyle yanıtın geri dönmesi için DNS isteklerinin kaynağını değerlendirir. Ad çözümleme isteklerinin kullanıcı trafiğiyle aynı yola gitmeleri için DNS'inizin yapılandırıldığından emin olun; çünkü bu istekleri onlara yerel çıkış ancak başka bir bölgedeki uç nokta üzerinden vermenizi sağlar. Bu, yerel DNS sunucularının uzak veri merkezlerindeki DNS sunucularına iletilme yerine "köke gitmesine" izin verdiğiniz anlamına gelir. Ayrıca, dünyanın bir kısmından sonuçları önbelleğe alan ve dünyanın diğer kısımlarından gelen isteklere hizmet eden genel ve özel DNS hizmetlerini de izleyebilirsiniz.

### <a name="to-proxy-or-not-to-proxy-that-is-the-question"></a>Proxy'ye gerek yok veya proxy'ye gerek yok, bu soru

Dikkate alınmanız gereken ilk şeylerden biri, ara sunucu kullanıcılarının ara sunucu bağlantılarının Office 365. Bunu kolayca, proxy yok. Office 365 İnternet üzerinden erişilir, ancak İnternet değildir. Bu, temel hizmetlerinizin bir uzantısıdır ve bu şekilde işlem edilmelidir. DLP veya kötü amaçlı yazılımlardan koruma veya içerik incelemesi gibi bir proxy'nin yapmak istemeniz gereken her şey, hizmette zaten kullanılabilir ve ÖLÇEK'te kullanılabilir ve TLS şifreli bağlantıları kırmak zorunda kalmadan kullanılabilir. Ancak, başka türlü denetlemeyilen bir ara sunucu trafiğine gerçekten sahip olmak istemiyorsanız, [https://aka.ms/pnc](../enterprise/microsoft-365-network-connectivity-principles.md) 'da ve 'da yer alan trafik kategorileri üzerinden kılavuzlarımıza dikkat etmek gerekir [https://aka.ms/ipaddrs](../enterprise/urls-and-ip-address-ranges.md). Üç kategori trafiğimiz var ve Office 365. İyileştir ve İzin Ver gerçekten doğrudan gidip proxy'nizi atlalı. Varsayılan, proxied olabilir. Ayrıntılar bu belgelerde... okuyabilirsiniz.

Proxy kullanmaya sahip olan çoğu müşteri, aslında ne yaptığına bakarken, istemci ara sunucuya HTTP CONNECT isteğinde geldiğinde, proxy'nin artık fazladan pahalı bir yönlendirici olduğunu fark eder. MAPI ve RTC gibi kullanım protokolleri, webx'leri anlıyoruz protokoller değildir, dolayısıyla TLS ile kırılasa bile fazladan güvenlik elde olmazsınız. Fazladan *gecikme* süresiyle karşılanıyoruz. Daha [https://aka.ms/pnc](../enterprise/microsoft-365-network-connectivity-principles.md) fazla bilgi için bkz. Trafiğin en iyi duruma getirme, İzin Ver ve Varsayılan Microsoft 365.

Son olarak, proxy'ye ve ona karşılık gelen yanıt üzerinde bu etkiyi bir bütün olarak düşünün. Ara sunucu aracılığıyla daha fazla bağlantı yapılırken, TCP Ölçek Faktörü'dür ve böylece çok fazla trafiği arabelleğe almaları gerekmeyen şekilde azaltabilirsiniz. Prox'larının Ölçek Faktörü 0'ı kullanmaları nedeniyle fazla yüklerinin olduğu müşterileri gördüm. Ölçek Faktörü üstel bir değer olduğu için 8 kullanmakla birlikte, Ölçek Faktörü değerinin azaltılması işlem hacmine büyük olumsuz etkiyi verir.

TLS İncelemesi, GÜVENLİ! Aslında değil! Ara araca sahip birçok müşteri tüm trafiği incelemek için bunları kullanmak istiyor; bu da TLS "kesme ve denetleme" anlamına geliyor. BUNU HTTPS üzerinden erişilen bir web sitesi için yapmaya devam edersiniz (gizlilik kaygıları dikkate alınmadan) proxy'nizin bunu birkaç yüz milisaniye için 10, hatta 20 eş zamanlı akış için yapmak zorunda olabilir. Büyük bir indirme veya belki de ilgili bir video söz konusu olursa, söz konusu bağlantıların bir veya birden çoğu çok daha uzun sürebilir, ancak bir bütün olarak, söz konusu bağlantıların çoğu çok hızlı bir şekilde bağlantı kuramaz, aktaramaz ve kapatır. Ara sunucu çift çalışmak ve incelemek, proxy'nin iki kez çalışması gerektiğini anlamına gelir. İstemciden proxy'ye her bağlantı için, proxy'nin uç noktayla ayrı bir bağlantı olması gerekir. Dolayısıyla, 1 olur 2 olur, 2 olur 4 olur, 32 olur 64 olur...nereye gidiyorum? Büyük olasılıkla proxy çözümünüz normal web gezinmesi için uygun boyutlandırdınız ama Office 365'a istemci bağlantıları için de aynı şeyi yapmaya çalışıyorken, eş zamanlı, uzun yaşanan bağlantı sayısı boyutuna göre büyük boyutlu olan siparişler olabilir.

### <a name="streaming-isnt-important-except-that-it-is"></a>Akış, akışla ilgili önemli bir şey *değil*;

UDP kullanan tek Office 365 UDP kullanan hizmetler Skype (yakında kullanımdan kaldıracak) ve Microsoft Teams. Teams, ses, video ve sunu paylaşımı gibi akış trafiği için UDP kullanır. Ses, görüntü ve sunum desteleri ile çevrimiçi bir toplantı gerçekleştirerek veya tanıtım yaparken olduğu gibi trafiğin akışı canlıdır. Bunlar UDP kullanır çünkü paketler bırakılır veya sipariş dışında bırakılırsa, bu durum kullanıcı tarafından kolay bir şekilde ortaya çıkar ve akış devam edeebilir.

İstemcilerden hizmete giden UDP trafiğine izin vermezsiniz, TCP kullanmaya geri dönebilir. Ancak bir TCP paketi bırakılırsa *, Yeniden* Iletim Zaman Aşımı (RTO) süresi dolana ve eksik paket yeniden aktarılabilir. Bir paket sipariş dışında gelirse, diğer paketler gelene ve sırayla yeniden birleşinceye kadar her şey durur. Her ikisi de ses (Max Headroom?) ve video (bir şeye tıkladı mı... İşte bu kadar) ve kötü performansa ve kötü bir kullanıcı deneyimine yol açıyor. Yukarıda,x'ler hakkında neleri hatırlatır musunuz? Bir ara sunucu Teams ara sunucu kullanmaya zorlarken, TCP kullanmaya zorlarlar. Dolayısıyla, şimdi iki kez performans üzerindeki olumsuz etkilere neden oluyoruz.

### <a name="split-tunneling-may-seem-scary"></a>Bölünmüş bölme ürkütücü olabilir

Ancak değil. Veri bağlantılarının Office 365 TLS üzerindendir. Uzun zamandır TLS 1.2'yi teklif ediyor ve eski istemciler bunları kullanmaya devam ederken bu risk nedeniyle yakında eski sürümleri devre dışı bırakacağız.

TLS bağlantısına veya 32'nize VPN üzerinden gitmek için bu bağlantıdan daha sonra hizmete gitmek zorunda olmak güvenlik eklemez. Bu işlem gecikme süresi ekler ve genel performansı azaltır. Bazı VPN çözümlerinde UDP'yi TCP üzerinden iş açmaya bile zorlar ve bu da akış trafiği üzerinde çok olumsuz bir etki sağlar. TLS incelemesi yapmıyorsanız terslik yok. İş gücü çalışanlarının büyük bir oranı uzak olduğu için müşteriler arasında çok yaygın bir tema, en iyi duruma getirme kategorisine ve uç noktalarına erişim için bölünmüş şifreleme yapılandırmak yerine tüm kullanıcılarının [Office 365](../enterprise/microsoft-365-network-connectivity-principles.md#new-office-365-endpoint-categories) VPN kullanarak bağlanmalarını sağlamaktan önemli bant genişliği ve performans etkisi görüyorlar.

Bu, bölünmüş bölme yapmak için kolay bir düzeltmedir ve bunu da sizin düzeltmelidir. Daha fazla bilgi için VPN bölünmüş [bölmeyi kullanan uzak Office 365 için en iyi duruma getirme bağlantısını gözden geçirmeyi denetleyin](../enterprise/microsoft-365-vpn-split-tunnel.md).

## <a name="the-sins-of-the-past"></a>Geçmiştekilerden olan bir o kadar da önemli değil

Çoğu zaman, kötü seçimlerin nedeni (1) hizmetin nasıl çalıştığını bilmeme, (2) bulutu benimsemeden önce yazılmış şirket ilkelerine uymaya çalışma ve (3) hedeflerini gerçekleştirmenin birden fazla yolu olduğunu kolayca kabul  etmeyen güvenlik ekiplerinden (3) gelir. Umarız yukarıdakiler ve aşağıdaki bağlantılar ilk bağlantıda yardımcı olur. İkinciyi geride geride etmek için yönetime destek gerekebilir. Güvenlik ilkelerinin hedeflerine, yöntemleri yerine 3. ilkeye yönelik hedefler, üçüncüye yardımcı olur. Koşullu erişimden içerik denetimine, DLP'den bilgi korumasına, uç nokta doğrulamasından sıfır günlük tehditlere kadar her uç amaç, makul bir güvenlik ilkesi Office 365'te bulunanlarla gerçek edilebilir ve şirket içi ağ dişlilerine, zorlamalı VPN geçişlerine ve TLS'ye bağımlı kalmadan gerçek edilebilir ve inceler.

Diğer zamanlarda, kuruluşun buluta taşınmaya başlamadan önce boyutlandıran ve satın alınan donanımlar, yeni trafik düzenlerini ve yüklerini işlemek için ölçeklendirimeden önce ölçek olamaz. Tüm trafiği tek bir çıkış noktası ve/veya ara sunucu üzerinden gerçekten yönlendirmeniz gerekirse, ağ donanımı ve bant genişliğini buna uygun olarak yükseltmeye hazır olun. Her ikisinde de kullanımını dikkatle izleyin, çünkü deneyim daha fazla kullanıcı kullansınca yavaş yavaş azalttı. Her şey yolundadır; o zaman herkes seğirecek.

## <a name="exceptions-to-the-rules"></a>Kurallar için özel durumlar

Organizasyonunız kiracı [kısıtlamaları](/azure/active-directory/manage-apps/tenant-restrictions) gerektiriyorsa TLS molası olan bir ara sunucu kullanın ve ara sunucu üzerinden bazı trafiği zorlamak için incelemeniz gerekir, ancak tüm trafiği bu ara sunucu üzerinden zorlamanız gerekli değildir.  Bu, her şeyi açık bir şekilde ifade etmek değildir; bu nedenle proxy tarafından nelerin değiştirilmesi gerekenlere dikkat etmek gerekir.

Bölünmüş trafiğin izin veremeyecek, aynı zamanda genel web trafiği için ara sunucu kullanmaya devam ediyorsanız, PAC dosyanız hem doğrudan hem de VPN yolundan geçen trafik için ilginç trafik tanımlamanız gerekenleri tanımladığından emin olun. Bu noktada, bunu yönetmenizi kolaylaştıracak [https://aka.ms/ipaddrs](../enterprise/urls-and-ip-address-ranges.md) örnek PAC dosyaları sunuyoruz.

## <a name="conclusion"></a>Sonuç

Fortune 500'in neredeyse hepsi de dahil olmak üzere on binlerce kuruluş, iş açısından kritik Office 365 işlevler için her gün yeni bir gün kullanır. Bunu İnternet üzerinden güvenli bir şekilde yapar.

Hangi güvenlik hedeflerini kullanıyor olursanız olun, kullanıcılarınızı ağdan ve mümkün olan en kısa sürede almak için VPN bağlantıları, ara sunucular, TLS sonu ve incelemesi veya merkezi İnternet çıkışını gerektirmeyen, bu hedefleri gerçekleştirmenin yolları vardır. Bu da ağınız şirketin genel merkezi olsa da en iyi performansı sağlar  uzak bir ofis veya evde çalışan bir kullanıcı. Bizim kılavuzumuz, kullanıcı hizmetlerinin Office 365 ve güvenli ve iyi performansta bir kullanıcı deneyimi sağlamaya dayalıdır.

## <a name="further-reading"></a>Daha fazla okuma

[Office 365 Ağ Bağlantısı İlkeleri](../enterprise/microsoft-365-network-connectivity-principles.md)

[Office 365 URL'leri ve IP adresi aralıkları](../enterprise/urls-and-ip-address-ranges.md)

[Kullanıcı Office 365 yönetme](../enterprise/managing-office-365-endpoints.md)

[Office 365 IP Adresi ve URL Web hizmeti](../enterprise/microsoft-365-ip-web-service.md)

[Ağ Office 365 değerlendirme](../enterprise/assessing-network-connectivity.md)

[Office 365 ve performans ayarını yapılandırma](../enterprise/network-planning-and-performance.md)

[Ağ Office 365 değerlendirme](../enterprise/assessing-network-connectivity.md)

[Office 365 ve performans geçmişini kullanarak performans ayarlamayı ayarlama](../enterprise/performance-tuning-using-baselines-and-history.md)

[Destek için performans sorunlarını giderme Office 365](../enterprise/performance-troubleshooting-plan.md)

[İçerik Teslim Ağları](../enterprise/content-delivery-networks.md)

[Microsoft 365 bağlantı testi](https://connectivity.office.com/)

[Microsoft hızlı ve güvenilir küresel ağına nasıl sahip olur?](https://azure.microsoft.com/blog/how-microsoft-builds-its-fast-and-reliable-global-network/)

[Office 365 Ağı blogu](https://techcommunity.microsoft.com/t5/office-365-networking/bd-p/Office365Networking)

[Office 365 VPN bölünmüş şifreleme kullanarak uzak kullanıcılar için hızlı bağlantı](../enterprise/microsoft-365-vpn-split-tunnel.md)
