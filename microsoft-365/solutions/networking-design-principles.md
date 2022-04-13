---
title: Ağ oluşturma (buluta)—Bir mimarın bakış açısı
description: En yaygın tuzaklardan kaçınarak ağınızı bulut bağlantısı için iyileştirmeyi öğrenin.
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
ms.openlocfilehash: 5f90e4616edd3534baefd64bba5a2eec640f6366
ms.sourcegitcommit: 195e4734d9a6e8e72bd355ee9f8bca1f18577615
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/13/2022
ms.locfileid: "64823948"
---
# <a name="networking-up-to-the-cloudone-architects-viewpoint"></a>Ağ oluşturma (buluta)—Bir mimarın bakış açısı

Bu makalede, Microsoft'ta Güvenlik & Uyumluluk Mimarı [Ed Fisher](https://www.linkedin.com/in/edfisher/), en yaygın tuzaklardan kaçınarak ağınızı bulut bağlantısı için iyileştirmeyi açıklar.

## <a name="about-the-author"></a>Yazar hakkında

![Ed Fisher'ın fotoğrafı.](../media/solutions-architecture-center/ed-fisher-networking.jpg)

Şu anda Perakende ve Tüketici Ürünleri ekibimizde Güvenlik & Uyumluluğuna odaklanan Baş Teknik Uzmanıyım. Son on yıldır Office 365 taşınan müşterilerle çalıştım. Dünyanın dört bir yanında milyonlarca kullanıcı dağıtılan devlet kurumları ve kuruluşlara birkaç farklı konumdan oluşan küçük mağazalarla ve aralarında birçok başka müşteriyle çalıştım, çoğunluğu on binlerce kullanıcıya, dünyanın çeşitli yerlerinde birden çok konuma, daha yüksek güvenlik düzeyine ve çok sayıda uyumluluk gereksinimine ihtiyaç duyuyordu. Yüzlerce kuruluşun ve milyonlarca kullanıcının güvenli ve güvenli bir şekilde buluta taşınmasına yardımcı oldu.

Son 25 yılda güvenlik, altyapı ve ağ mühendisliğini içeren bir geçmişe sahip olan ve Microsoft'a katılmadan önce önceki iki işverenimi Office 365 taşıyarak, birçok kez masanın sizin tarafınızda bulundum ve bunun nasıl bir şey olduğunu hatırlıyorum. Hiçbir iki müşteri aynı olmasa da, çoğu benzer gereksinimlere sahiptir ve herhangi bir SaaS veya PaaS platformu gibi standartlaştırılmış bir hizmeti kullanırken en iyi yaklaşımlar aynı olma eğilimindedir.

## <a name="its-not-the-network--its-how-youre-misusing-it"></a>Ağ değil, bu şekilde kullanıyorsunuz!

Kaç kez olursa olsun, *yaratıcı* güvenlik ekiplerinin ve ağ ekiplerinin Microsoft bulut hizmetlerine bağlanmaları gerektiğini düşündükleri şekilde çalışmaya nasıl çalıştıkları beni hiçbir zaman şaşırtamıyor. Neyi gerçekleştirmeye çalıştıkları veya bunu yapmanın *daha* iyi, daha kolay, daha uygun maliyetli ve daha yüksek performanslı yolları hakkında bir konuşmaya katılmak istemeden her zaman bazı güvenlik ilkeleri, uyumluluk standardı veya kullanma konusunda ısrar ettikleri daha iyi bir yol vardır.

Bu tür şeyler bana yükseltildiğinde, genellikle meydan okumayı kabul ederim ve onlara nasıl ve nedenler konusunda yol gösteririm ve onları olmaları gereken yere götürürüm. Ama tamamen açık sözlü olursam, bazen ne yapacaklarını yapmalarına izin vermek istediğimi ve sonunda işe yaramadığını söylediklerinde sana söylediğimi söylemek istediğimi paylaşmalıyım. Bazen bunu yapmak isteyebilirim ama *istemiyorum*. Yaptığım şey, bu gönderiye neleri dahil edeceğimi açıklamaya çalışmak. Rolünüz ne olursa olsun, kuruluşunuz Microsoft bulut hizmetlerini kullanmak istiyorsa, size yardımcı olabilecek bazı bilgeliklerden yararlanabilirsiniz.

## <a name="guiding-principles"></a>Yol gösteren ilkeler

Burada yaptığımız işlerle ilgili bazı temel kurallarla başlayalım. Gerçek güvenliği korurken en düşük karmaşıklığı ve maksimum performansı sağlamak için bulut hizmetlerine nasıl güvenli bir şekilde bağlanabileceğinizi ele alıyoruz. Siz veya müşteriniz her şey için en sevdiğiniz proxy sunucusunu kullanamayacak olsanız bile, aşağıdakilerden hiçbiri bunların hiçbirine karşı değildir.

- **Sadece bunu yapasın diye, şu anlama gelmez**: Ya da Jurassic Park filminden Dr. Ian Malcolm'un "... Evet, evet, ama güvenlik ekibiniz o kadar meşgul ki.
- **Güvenlik karmaşıklık anlamına gelmez**: Daha fazla para harcadığınız, daha fazla cihazdan yönlendirdiğiniz veya daha fazla düğmeye tıkladığınız için daha güvenli olmazsınız.
- **Office 365 İnternet üzerinden erişilir**: Ancak bu, Office 365 İnternet ile aynı şey değildir. Microsoft tarafından yönetilen ve sizin tarafınızdan yönetilen bir SaaS hizmetidir. İnternet'te ziyaret ettiğiniz web sitelerinden farklı olarak, perdenin arkasına göz atabilir ve ilkelerinizi ve uyumluluk standartlarınızı karşılamak için ihtiyacınız olan denetimleri uygulayabilirsiniz, ancak hedeflerinize ulaşabildiğiniz sürece, bunları farklı bir şekilde yapmanız gerekebilir.
- **Boğma noktaları kötü, yerelleştirilmiş tartışmalar iyidir**: Herkes her zaman tüm kullanıcıları için İnternet trafiğini merkezi bir noktaya geri almak ister, bu sayede genellikle bunu izleyebilir ve ilke uygulayabilirler, ancak genellikle tüm konumlarında İnternet erişimi sağlamaktan daha ucuz olduğu için ya da sadece bunu nasıl yaptıklarıdır. Ama bu boğulma noktaları tam olarak... trafiğin boğulduğu yere işaret eder. Kullanıcılarınızın Instagram'a veya akış kedi videolarına göz atmasını engellemenin yanlış bir tarafı yoktur, ancak görev açısından kritik iş uygulaması trafiğinize aynı şekilde davranmayın.
- **DNS mutlu değilse, hiçbir şey mutlu değil**: En iyi tasarlanmış ağ, dünyanın diğer bölgelerindeki sunuculara istekleri yinelemek veya ISS'nizin DNS sunucularını veya DNS çözümleme bilgilerini önbelleğe alan diğer genel DNS sunucularını kullanarak kötü DNS tarafından silinebilir.
- Eskiden böyle **yapıyor olmanız, şu anda bunu yapmanız gerektiği anlamına gelmez**: Teknoloji sürekli değişir ve Office 365 bir istisna değildir. Şirket içi hizmetler için geliştirilen ve dağıtılan güvenlik önlemlerinin uygulanması veya web'de gezinmeyi denetlemek aynı güvenlik güvencesi düzeyini sağlamaz ve performansı önemli ölçüde olumsuz etkileyebilir.
- **Office 365 İnternet üzerinden erişilecek şekilde oluşturulmuştu**: Özetle bu kadar. Kullanıcılarınız ve uçlarınız arasında ne yapmak isterseniz yapın, trafiğin ağınızdan çıkıp bizim ağımıza girmeden önce İnternet üzerinden geçmesine neden olur. Ağınızdan gelen gecikmeye duyarlı trafiği doğrudan bizimkine yönlendirmek için Azure ExpressRoute kullanıyor olsanız bile İnternet bağlantısı kesinlikle gereklidir. Kabul edin. Fazla düşünme.

## <a name="where-bad-choices-are-often-made"></a>Kötü seçimlerin sıklıkla yapıldığı yerler

Güvenlik adına kötü kararların alındığı birçok yer olsa da, müşterilerle en sık karşılaştığım yerler bunlardır. Birçok müşteri konuşması aynı anda bunların tümünü içerir.

### <a name="insufficient-resources-at-the-edge"></a>Uçta yetersiz kaynak

Çok az müşteri yeşil alan ortamları dağıtıyor ve kullanıcılarının nasıl çalıştığı ve İnternet çıkışlarının nasıl olduğu konusunda yılların deneyimine sahip. Müşterilerin proxy sunucuları olsun veya doğrudan erişime izin versin ve yalnızca NAT giden trafiği olsun, bunu yıllardır yapıyorlar ve geleneksel olarak iç uygulamaları buluta taşırken uçlarından ne kadar daha fazla pompalamaya başlayacaklarını düşünmediler.

Bant genişliği her zaman sorun oluşturur, ancak NAT cihazları artan yükü işlemek için yeterli beygir gücüne sahip olmayabilir ve kaynakları boşaltmak için bağlantıları erken kapatmaya başlayabilir. Office 365 bağlanan istemci yazılımlarının çoğu kalıcı bağlantılar bekler ve Office 365 kullanan bir kullanıcının 32 veya daha fazla eşzamanlı bağlantısı olabilir. NAT cihazı bunları erken bırakıyorsa, artık orada olmayan bağlantıları kullanmaya çalıştıkları için bu uygulamalar yanıt vermemeye başlayabilir. Pes edip yeni bağlantılar kurmaya çalıştıklarında, ağ dişlinize daha da fazla yük bindiriyorlar.

### <a name="localized-breakout"></a>Yerelleştirilmiş tartışma

Bu listedeki diğer her şey, ağınızdan ve bizim ağınızdan mümkün olan en kısa sürede çıkmak gibi tek bir şeye iner. Özellikle bu çıkış noktası kullanıcılarınızdan başka bir bölgedeyse, kullanıcılarınızın trafiğini merkezi bir çıkış noktasına geri döndürmek gereksiz gecikme süresine neden olur ve hem istemci deneyimini hem de indirme hızlarını etkiler. Microsoft, tüm hizmetlerimiz ve neredeyse tüm büyük ISS'lerle kurulan eşleme için ön uçları olan tüm iletişim noktalarına sahiptir, bu nedenle kullanıcılarınızın trafiğini *yerel olarak* dışarı yönlendirmek, ağımıza minimum gecikme süresiyle hızlı bir şekilde girilmesini sağlar.

### <a name="dns-resolution-traffic-should-follow-the-internet-egress-path"></a>DNS çözümleme trafiği İnternet çıkış yolunu izlemelidir

Tabii ki, bir istemcinin herhangi bir uç noktayı bulması için DNS kullanması gerekir. Microsoft'un DNS sunucuları, isteğin kaynağına en yakın olan yanıtı İnternet terimleriyle döndürmek için DNS isteklerinin kaynağını değerlendirir. DNS'nizin, ad çözümleme isteklerinin kullanıcılarınızın trafiğiyle aynı yoldan gitmesi için yapılandırıldığından emin olun; bu sayede onlara yerel çıkış verirsiniz ancak başka bir bölgedeki bir uç noktaya gidersiniz. Bu, uzak veri merkezlerindeki DNS sunucularına iletmek yerine yerel DNS sunucularının "köke gitmesine" izin vermek anlamına gelir. Ayrıca, dünyanın bir yerinden gelen sonuçları önbelleğe alabilen ve bunları dünyanın diğer bölgelerinden gelen isteklere sunabilen genel ve özel DNS hizmetlerine dikkat edin.

### <a name="to-proxy-or-not-to-proxy-that-is-the-question"></a>Ara sunucuya veya ara sunucuya değil, asıl soru bu

Dikkate alınması gereken ilk şeylerden biri, kullanıcıların Office 365 bağlantılarını ara sunucuya alıp almamaktır. Bu çok kolay; ara sunucu kullanmayın. Office 365 İnternet üzerinden erişilir, ancak İnternet değildir. Bu, temel hizmetlerinizin bir uzantısıdır ve bu şekilde ele alınmalıdır. DLP, kötü amaçlı yazılımdan koruma veya içerik denetimi gibi bir proxy'nin yapmak isteyebileceğiniz her şey hizmette zaten kullanılabilir ve büyük ölçekte ve TLS ile şifrelenmiş bağlantıların kırılmasına gerek kalmadan kullanılabilir. Ancak, başka türlü denetleyemeyeceğiniz trafiği gerçekten ara sunucu olarak kullanmak istiyorsanız, konumundaki kılavuzumuza [https://aka.ms/pnc](../enterprise/microsoft-365-network-connectivity-principles.md) ve konumundaki [https://aka.ms/ipaddrs](../enterprise/urls-and-ip-address-ranges.md)trafik kategorilerine dikkat edin. Office 365 için üç trafik kategorimiz var. İyileştir ve İzin Ver gerçekten doğrudan gitmeli ve proxy'nizi atlamalıdır. Varsayılan değer proksid edilebilir. Ayrıntılar bu belgelerde... bunları okuyun.

Ara sunucu kullanmakta ısrar eden müşterilerin çoğu, gerçekte ne yaptıklarına baktıklarında, istemci ara sunucuya HTTP CONNECT isteği yaptığında, proxy'nin artık yalnızca pahalı bir ek yönlendirici olduğunu fark eder. MAPI ve RTC gibi kullanımdaki protokoller, web proxy'lerinin anladığı protokoller bile değildir, bu nedenle TLS'yi kırsa bile fazladan güvenlik elde edemeyebilirsiniz. *Ek gecikme* süresi alıyorsunuz. Microsoft 365 trafiği için İyileştir, İzin Ver ve Varsayılan kategorileri de dahil olmak üzere bu konuda daha fazla bilgi için bkz[https://aka.ms/pnc](../enterprise/microsoft-365-network-connectivity-principles.md).

Son olarak, bu etkiyle başa çıkmak için ara sunucu üzerindeki genel etkiyi ve buna karşılık gelen yanıtı göz önünde bulundurun. Ara sunucu üzerinden giderek daha fazla bağlantı yapıldığından, tcp ölçek faktörünü azaltabilir, böylece çok fazla trafiği arabelleğe almak zorunda kalmayabilir. Proxy'lerinin aşırı yüklendiği ve 0'lık bir Ölçek Faktörü kullandıkları müşterileri gördüm. Ölçek Faktörü üstel bir değer olduğundan ve 8'i kullanmayı tercih ettiğimizden, Ölçek Faktörü değerindeki her azalma aktarım hızı üzerinde büyük bir olumsuz etki oluşturur.

TLS İnceleme, GÜVENLİk anlamına gelir! Ama gerçekten değil! Proxy'leri olan birçok müşteri tüm trafiği incelemek için bunları kullanmak ister ve bu da TLS'nin "kesme ve inceleme" anlamına gelir. HTTPS üzerinden erişilen bir web sitesi için bunu yaptığınızda (gizlilikle ilgili endişeler olmasa da) proxy'nizin bunu birkaç yüz milisaniye boyunca 10 veya hatta 20 eşzamanlı akış için yapması gerekebilir. Büyük bir indirme veya belki de bir video söz konusuysa, bu bağlantılardan biri veya daha fazlası çok daha uzun sürebilir, ancak tüm bu bağlantıların çoğu çok hızlı bir şekilde kurulur, aktarılır ve kapatılabilir. Kesme ve inceleme yapmak, proxy'nin işi iki katına alması gerektiği anlamına gelir. İstemciden ara sunucuya yapılan her bağlantı için, ara sunucu da uç noktaya ayrı bir bağlantı yapmalıdır. Yani, 1 2 olur, 2 4 olur, 32 64 olur... Nereye gittiğimi görüyor musunuz? Proxy çözümünüzü büyük olasılıkla normal web'de gezinmek için uygun boyutlandırmış olabilirsiniz, ancak Office 365 istemci bağlantıları için de aynı şeyi yapmaya çalıştığınızda eşzamanlı, uzun süreli bağlantı sayısı, boyutlandırdığınız boyuttan daha büyük bir sipariş olabilir.

### <a name="streaming-isnt-important-except-that-it-is"></a>Akış önemli değildir, ancak *önemli değildir*

Office 365'da UDP kullanan tek hizmetler Skype (yakında kullanımdan kaldırılacak) ve Microsoft Teams. Teams ses, video ve sunu paylaşımı gibi akış trafiği için UDP kullanır. Akış trafiği, örneğin ses, video ve sunum desteleriyle çevrimiçi toplantı yaparken veya tanıtımlar yaparken canlı olarak gerçekleştirilir. Paketler bırakıldığında veya sıra dışı geldiğinde kullanıcı tarafından neredeyse fark edilemediğinden ve akış devam ettiğinden, bunlar UDP kullanır.

İstemcilerden hizmete giden UDP trafiğine izin vermediğinizde tcp kullanmaya geri dönebilirler. Ancak bir TCP paketi bırakılırsa, Yeniden İletim Zaman Aşımı (RTO) süresi dolana ve eksik paket yeniden aktarılana kadar *her şey durur* . Bir paket sırayla ulaşırsa, diğer paketler gelene kadar her şey durur ve sırayla yeniden birleştirilebilir. Her ikisi de ses (Max Headroom'u hatırlıyor musunuz?) ve videoda algılanabilir hatalara yol açar (bir şeye tıkladığınızda... oh, işte orada) ve düşük performansa ve kötü bir kullanıcı deneyimine yol açar. Ve proxy'ler hakkında yukarıda ne koyduğumu hatırlıyor musun? bir Teams istemcisini ara sunucu kullanmaya zorladığınızda, tcp kullanmaya zorlarsınız. Şimdi iki kez olumsuz performans etkisine neden oluyorsunuz.

### <a name="split-tunneling-may-seem-scary"></a>Bölünmüş tünel korkutucu görünebilir

Ama değil. Office 365 tüm bağlantılar TLS üzerinden yapılır. Uzun süredir TLS 1.2'yi sunuyoruz ve eski istemciler bunları kullanmaya devam ettiğinden eski sürümleri yakında devre dışı bırakacağız ve bu bir risktir.

BIR TLS bağlantısını veya 32'sini hizmete gitmeden önce VPN üzerinden geçmek için zorlamak güvenlik eklemez. Gecikme süresi ekler ve genel aktarım hızını azaltır. Bazı VPN çözümlerinde, UDP'yi TCP üzerinden tünel yapmaya zorlar ve bu da akış trafiğini çok olumsuz etkiler. AYRıCA, TLS denetimi yapmıyorsanız, bunun bir ters tarafı yoktur. İş gücünün çoğu uzak olduğu için müşteriler arasında çok yaygın bir tema, [optimize kategorisi Office 365 uç noktalarına](../enterprise/microsoft-365-network-connectivity-principles.md#new-office-365-endpoint-categories) erişim için bölünmüş tünel yapılandırmak yerine tüm kullanıcılarının VPN kullanarak bağlanmasını sağlamaktan önemli bant genişliği ve performans etkileri görüyor olmalarıdır.

Bu, bölünmüş tünel oluşturmanın kolay bir düzeltmesi ve bunu yapmanız gerekir. Daha fazla bilgi [için VPN bölünmüş tünel kullanarak uzak kullanıcılar için Office 365 bağlantısını iyileştirme'yi](../enterprise/microsoft-365-vpn-split-tunnel.md) gözden geçirin.

## <a name="the-sins-of-the-past"></a>Geçmişin günahları

Çoğu zaman, kötü seçimlerin olmasının nedeni (1) hizmetin nasıl çalıştığını bilmemenin, (2) bulutu benimsemeden önce yazılmış şirket ilkelerine uymaya çalışmanın ve (3) hedeflerini gerçekleştirmenin birden fazla yolu olduğuna kolayca ikna edilemeyen güvenlik ekiplerinin birleşiminden kaynaklanmaktadır. Umarım yukarıdakiler ve aşağıdaki bağlantılar ilkinde yardımcı olur. İkinci aşamayı geçmek için yönetici sponsorluğu gerekebilir. Güvenlik ilkelerinin yöntemlerini değil hedeflerini ele almak, üçüncü ilkeye yardımcı olur. Koşullu erişimden içerik denetimine, DLP'den bilgi korumasına, uç nokta doğrulamadan sıfır günlük tehditlere kadar makul bir güvenlik ilkesi, Office 365'da sağlananlarla ve şirket içi ağ dişlisine, zorlamalı VPN tünellerine ve TLS kesme ve incelemeye bağımlı olmadan gerçekleştirilebilir.

Diğer zamanlarda, kuruluş buluta taşınmaya başlamadan önce boyutlandırılan ve satın alınan donanımlar, yeni trafik düzenlerini ve yüklerini işleyecek şekilde ölçeklendirilemez. Tüm trafiği tek bir çıkış noktası üzerinden yönlendirmeniz ve/veya ara sunucu kullanmanız gerekiyorsa, ağ ekipmanını ve bant genişliğini uygun şekilde yükseltmeye hazır olun. Her ikisinde de kullanımı dikkatle izleyin çünkü deneyim daha fazla kullanıcı eklendiği kadar yavaş azalmaz. Devrilme noktasına ulaşılana kadar her şey iyi olacak, o zaman herkes acı çeker.

## <a name="exceptions-to-the-rules"></a>Kurallar için özel durumlar

Kuruluşunuz [kiracı kısıtlamaları](/azure/active-directory/manage-apps/tenant-restrictions) gerektiriyorsa, ara sunucu üzerinden bazı trafiği zorlamak için TLS kesmesi olan bir ara sunucu kullanmanız ve denetlemeniz gerekir, ancak tüm trafiği zorlamanız gerekmez.  Bu bir ya hep ya hiç teklifi değildir, bu nedenle proxy tarafından değiştirilmesi gerekenlere dikkat edin.

Bölünmüş tünele izin verecek ancak genel web trafiği için bir ara sunucu da kullanacaksanız, PAC dosyanızın neyin doğrudan gitmesi gerektiğini tanımladığından ve VPN tünelinden geçenler için ilginç trafiği nasıl tanımladığınızdan emin olun. Bunu yönetmeyi kolaylaştıracak örnek PAC dosyaları [https://aka.ms/ipaddrs](../enterprise/urls-and-ip-address-ranges.md) sunuyoruz.

## <a name="conclusion"></a>Sonuç

Neredeyse tüm Fortune 500 dahil olmak üzere on binlerce kuruluş, görev açısından kritik işlevleri için her gün Office 365 kullanıyor. Bunu güvenli bir şekilde ve İnternet üzerinden yapıyorlar.

Hangi güvenlik hedeflerine sahip olursanız olun, vpn bağlantıları, ara sunucu, TLS kesme ve inceleme ya da kullanıcılarınızın trafiğini ağınızdan ve bizim ağınızdan olabildiğince hızlı bir şekilde çıkarmak için merkezi İnternet çıkışı gerektirmeyen ve ağınız şirket genel merkezi olsun en iyi performansı sağlayan yöntemler vardır.  bir uzak ofis veya evde çalışan kullanıcı. Kılavuzumuz, Office 365 hizmetlerinin nasıl oluşturulduğuna ve güvenli ve performanslı bir kullanıcı deneyimi sağlamaya dayalıdır.

## <a name="further-reading"></a>Daha fazla okuma

[Office 365 Ağ Bağlantı İlkeleri](../enterprise/microsoft-365-network-connectivity-principles.md)

[Office 365 URL'leri ve IP adresi aralıkları](../enterprise/urls-and-ip-address-ranges.md)

[Office 365 uç noktalarını yönetme](../enterprise/managing-office-365-endpoints.md)

[Office 365 IP Adresi ve URL Web hizmeti](../enterprise/microsoft-365-ip-web-service.md)

[Office 365 ağ bağlantısını değerlendirme](../enterprise/assessing-network-connectivity.md)

[ağ ve performans ayarlamayı Office 365](../enterprise/network-planning-and-performance.md)

[Office 365 ağ bağlantısını değerlendirme](../enterprise/assessing-network-connectivity.md)

[Temelleri ve performans geçmişini kullanarak performans ayarlamayı Office 365](../enterprise/performance-tuning-using-baselines-and-history.md)

[Office 365 için performans sorunlarını giderme planı](../enterprise/performance-troubleshooting-plan.md)

[İçerik Teslim Ağları](../enterprise/content-delivery-networks.md)

[Microsoft 365 bağlantı testi](https://connectivity.office.com/)

[Microsoft hızlı ve güvenilir küresel ağını nasıl oluşturur?](https://azure.microsoft.com/blog/how-microsoft-builds-its-fast-and-reliable-global-network/)

[Office 365 Ağ blogu](https://techcommunity.microsoft.com/t5/office-365-networking/bd-p/Office365Networking)

[VPN bölünmüş tünel kullanarak uzak kullanıcılar için Office 365 bağlantısı](../enterprise/microsoft-365-vpn-split-tunnel.md)
