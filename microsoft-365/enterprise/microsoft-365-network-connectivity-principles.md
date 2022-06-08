---
title: Microsoft 365 ağ bağlantısı ilkeleri
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 6/23/2020
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: high
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
search.appverid: MET150
ms.assetid: 76e7f232-917a-4b13-8fe2-4f8dbccfe041
f1.keywords:
- NOCSH
description: Bu makalede, Microsoft 365 ağ bağlantısını güvenli bir şekilde iyileştirmeye yönelik en son yönergeler sağlanmaktadır.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 76bbad1b392966f9140db36cf4adbbfff7b62b2b
ms.sourcegitcommit: 61bdfa84f2d6ce0b61ba5df39dcde58df6b3b59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2022
ms.locfileid: "65940964"
---
# <a name="microsoft-365-network-connectivity-principles"></a>Microsoft 365 ağ bağlantısı ilkeleri

*Bu makale hem Microsoft 365 Kurumsal hem de Office 365 Kurumsal için geçerlidir.*

Ağınızı Microsoft 365 ağ bağlantısı için planlamaya başlamadan önce, Microsoft 365 trafiğini güvenli bir şekilde yönetmek ve mümkün olan en iyi performansı elde etmek için bağlantı ilkelerini anlamanız önemlidir. Bu makale, Microsoft 365 ağ bağlantısını güvenli bir şekilde iyileştirmeye yönelik en son yönergeleri anlamanıza yardımcı olur.
  
Geleneksel kurumsal ağlar öncelikli olarak kullanıcıların güçlü çevre güvenliğine sahip şirket tarafından çalıştırılan veri merkezlerinde barındırılan uygulamalara ve verilere erişmesini sağlamak için tasarlanmıştır. Geleneksel model, kullanıcıların kurumsal ağ çevresinin içinden, şube ofislerinden WAN bağlantıları üzerinden veya VPN bağlantıları üzerinden uzaktan uygulamalara ve verilere erişeceğini varsayar.
  
Microsoft 365 gibi SaaS uygulamalarının benimsenmesi, bazı hizmet ve veri birleşimlerini ağ çevresi dışına taşır. İyileştirme olmadan, kullanıcılar ve SaaS uygulamaları arasındaki trafik paket denetimi, ağ saç tokaları, coğrafi olarak uzak uç noktalara yanlışlıkla yapılan bağlantılar ve diğer faktörler tarafından ortaya çıkan gecikme süresine tabidir. Temel iyileştirme yönergelerini anlayıp uygulayarak en iyi Microsoft 365 performansını ve güvenilirliğini sağlayabilirsiniz.
  
Bu makalede şunları öğreneceksiniz:
  
- Buluta müşteri bağlantısı için geçerli olan [Microsoft 365 mimarisi](microsoft-365-network-connectivity-principles.md#BKMK_Architecture)
- Ağ trafiğini ve son kullanıcı deneyimini iyileştirmeye yönelik [Microsoft 365 bağlantı ilkeleri](microsoft-365-network-connectivity-principles.md#BKMK_Principles) ve stratejileri güncelleştirildi
- Ağ yöneticilerinin ağ iyileştirmesinde kullanmak üzere yapılandırılmış uç noktaların listesini kullanmasına olanak tanıyan [Office 365 Uç Noktaları web hizmeti](microsoft-365-network-connectivity-principles.md#BKMK_WebSvc)
- [Yeni Office 365 uç nokta kategorileri](microsoft-365-network-connectivity-principles.md#BKMK_Categories) ve iyileştirme kılavuzu
- [Ağ çevre güvenliğini uç nokta güvenliğiyle karşılaştırma](microsoft-365-network-connectivity-principles.md#BKMK_SecurityComparison)
- Microsoft 365 trafiği için [artımlı iyileştirme](microsoft-365-network-connectivity-principles.md#BKMK_IncOpt) seçenekleri
- [Microsoft 365'e temel bağlantıyı](https://aka.ms/netonboard) test etmek için yeni bir araç olan Microsoft 365 bağlantı testi

## <a name="microsoft-365-architecture"></a>Microsoft 365 mimarisi
<a name="BKMK_Architecture"> </a>

Microsoft 365; Exchange Online, SharePoint Online, Skype Kurumsal Çevrimiçi Sürüm, Microsoft Teams, Exchange Online Koruması, Tarayıcıda Office gibi çeşitli mikro hizmetler ve uygulamalar aracılığıyla üretkenlik ve işbirliği senaryoları sağlayan dağıtılmış bir Hizmet Olarak Yazılım (SaaS) bulutudur. Belirli Microsoft 365 uygulamalarının benzersiz özellikleri müşteri ağı ve bulut bağlantısı için geçerli olsa da, hepsi bazı temel sorumluları, hedefleri ve mimari desenlerini paylaşır. Bu bağlantı ilkeleri ve mimari desenleri, diğer birçok SaaS bulutu için tipiktir ve aynı zamanda Microsoft Azure gibi Hizmet Olarak Platform ve Hizmet Olarak Altyapı bulutlarının tipik dağıtım modellerinden farklıdır.
  
Microsoft 365'in (genellikle ağ mimarları tarafından kaçırılan veya yanlış yorumlanan) en önemli mimari özelliklerinden biri, kullanıcıların ona nasıl bağlandığı bağlamında gerçekten genel bir dağıtılmış hizmet olmasıdır. Hedef Microsoft 365 kiracısının konumu, müşteri verilerinin bulutta depolandığı konumu anlamak için önemlidir, ancak Microsoft 365 ile kullanıcı deneyimi, verileri içeren disklere doğrudan bağlanmayı içermez. Microsoft 365 ile kullanıcı deneyimi (performans, güvenilirlik ve diğer önemli kalite özellikleri dahil) dünya çapında yüzlerce Microsoft konumunda ölçeği genişletilen yüksek oranda dağıtılmış hizmet ön kapılarından bağlantıyı içerir. Çoğu durumda en iyi kullanıcı deneyimi, müşteri ağının kullanıcı isteklerini merkezi bir konum veya bölgedeki bir çıkış noktası üzerinden Microsoft 365'e bağlanmak yerine en yakın Microsoft 365 hizmet giriş noktasına yönlendirmesine izin vererek elde edilir.
  
Çoğu müşteri için Microsoft 365 kullanıcıları birçok konuma dağıtılır. En iyi sonuçları elde etmek için, bu belgede özetlenen ilkelere ölçeği genişletme (ölçeği artırma değil) açısından, Microsoft 365 kiracısının coğrafi konumuyla değil, Microsoft Global Network'teki en yakın iletişim noktasıyla bağlantıyı iyileştirmeye odaklanarak bakılmalıdır. Temelde bu, Microsoft 365 kiracı verilerinin belirli bir coğrafi konumda depolanabilmesine rağmen, söz konusu kiracı için Microsoft 365 deneyiminin dağıtılmış kaldığı ve kiracının sahip olduğu her son kullanıcı konumuna çok yakın bir konumda (ağ) bulunabileceği anlamına gelir.
  
## <a name="microsoft-365-connectivity-principles"></a>Microsoft 365 bağlantı ilkeleri
<a name="BKMK_Principles"> </a>

Microsoft, en iyi Microsoft 365 bağlantısını ve performansını elde etmek için aşağıdaki ilkeleri önerir. Trafiğinizi yönetmek ve Microsoft 365'e bağlanırken en iyi performansı elde etmek için bu Microsoft 365 bağlantı ilkelerini kullanın.
  
Ağ tasarımındaki birincil hedef, ağınızdan Microsoft'un düşük gecikme süresi ve bulut uygulaması giriş noktalarıyla tüm Microsoft veri merkezlerini birbirine bağlayan microsoft genel ağ omurgası olan Microsoft Global Network'e gidiş dönüş süresini (RTT) azaltarak gecikme süresini en aza indirmek olmalıdır. Microsoft Global Network hakkında daha fazla bilgi edinmek için [Microsoft'un hızlı ve güvenilir küresel ağını oluşturmasını](https://azure.microsoft.com/blog/how-microsoft-builds-its-fast-and-reliable-global-network/) sağlayabilirsiniz.
  
<a name="BKMK_P1"> </a>
### <a name="identify-and-differentiate-microsoft-365-traffic"></a>Microsoft 365 trafiğini belirleme ve ayırt edin

![Microsoft 365 trafiğini tanımlama.](../media/621aaec9-971d-4f19-907a-1ae2ef6d72fc.png)
  
Microsoft 365 ağ trafiğini tanımlamak, trafiği genel İnternet'e bağlı ağ trafiğinden ayırt edebilmenin ilk adımıdır. Microsoft 365 bağlantısı, ağ yolu iyileştirmesi, güvenlik duvarı kuralları, tarayıcı proxy ayarları ve belirli uç noktalar için ağ denetleme cihazlarının atlanması gibi yaklaşımların bir bileşimi uygulanarak iyileştirilebilir.
  
Önceki Microsoft 365 iyileştirme kılavuzu, Microsoft 365 uç noktalarını **Gerekli** ve **İsteğe Bağlı** olmak üzere iki kategoriye böldü. Yeni Microsoft 365 hizmetlerini ve özelliklerini desteklemek üzere uç noktalar eklendiğinden, Microsoft 365 uç noktalarını üç kategoride yeniden düzenledik: **İyileştir**, **İzin Ver** ve **Varsayılan**. Her kategoriye yönelik yönergeler, kategorideki tüm uç noktalar için geçerlidir ve iyileştirmelerin anlaşılmasını ve uygulanmasını kolaylaştırır.
  
Microsoft 365 uç nokta kategorileri ve iyileştirme yöntemleri hakkında daha fazla bilgi için [Yeni Office 365 uç nokta kategorileri](microsoft-365-network-connectivity-principles.md#BKMK_Categories) bölümüne bakın.
  
Microsoft artık tüm Microsoft 365 uç noktalarını bir web hizmeti olarak yayımlar ve bu verileri en iyi şekilde kullanma konusunda rehberlik sağlar. Microsoft 365 uç noktalarını getirme ve bunlarla çalışma hakkında daha fazla bilgi için [Office 365 URL'leri ve IP adresi aralıkları](https://support.office.com/article/office-365-urls-and-ip-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2?ui=en-US&amp;rs=en-US&amp;ad=US) makalesine bakın.
  
<a name="BKMK_P2"> </a>
### <a name="egress-network-connections-locally"></a>Yerel olarak çıkış ağ bağlantıları

![Yerel olarak çıkış ağ bağlantıları.](../media/b42a45be-1ab4-4073-a7dc-fbdfb4aedd24.png)
  
Yerel DNS ve İnternet çıkışı, bağlantı gecikme süresini azaltmak ve kullanıcı bağlantılarının Microsoft 365 hizmetlerine en yakın giriş noktasına yapılmasını sağlamak için kritik öneme sahiptir. Karmaşık bir ağ topolojisinde hem yerel DNS hem de yerel İnternet çıkışını birlikte uygulamak önemlidir. Microsoft 365'in istemci bağlantılarını en yakın giriş noktasına nasıl yönlendirdiğini öğrenmek için [İstemci Bağlantısı](https://support.office.com/article/client-connectivity-4232abcf-4ae5-43aa-bfa1-9a078a99c78b) makalesine bakın.
  
Microsoft 365 gibi bulut hizmetlerinin ortaya çıkmasından önce, ağ mimarisinde tasarım faktörü olarak son kullanıcı İnternet bağlantısı nispeten basitti. İnternet hizmetleri ve web siteleri dünya çapında dağıtıldığında, kurumsal çıkış noktaları ile belirli bir hedef uç nokta arasındaki gecikme süresi büyük ölçüde coğrafi uzaklık işlevidir.
  
Geleneksel bir ağ mimarisinde, tüm giden İnternet bağlantıları şirket ağından ve merkezi bir konumdan çıkar. Microsoft'un bulut teklifleri olgunlaştıkça, İnternet'e yönelik dağıtılmış bir ağ mimarisi gecikmeye duyarlı bulut hizmetlerini desteklemek için kritik hale gelmiştir. Microsoft Global Network, gelen bulut hizmeti bağlantılarını en yakın giriş noktasına yönlendiren küresel giriş noktalarının dinamik bir dokusu olan Dağıtılmış Hizmet Front Door altyapısıyla gecikme gereksinimlerini karşılamak üzere tasarlanmıştır. Bu, müşteri ile bulut arasındaki rotayı etkili bir şekilde kısaltarak Microsoft bulut müşterileri için "son kilometre" uzunluğunu azaltmaya yöneliktir.
  
Kurumsal WAN'ler genellikle İnternet'e çıkıştan önce, genellikle bir veya daha fazla ara sunucu aracılığıyla denetim için merkezi bir şirket yönetim merkezine ağ trafiğini geri almak üzere tasarlanmıştır. Aşağıdaki diyagramda bu tür bir ağ topolojisi gösterilmektedir.
  
![Geleneksel kurumsal ağ modeli.](../media/fc87b8fd-a191-47a7-9704-1e445599813a.png)
  
Microsoft 365, dünyanın dört bir yanındaki ön uç sunucularını içeren Microsoft Global Network'te çalıştığından, genellikle kullanıcının konumuna yakın bir ön uç sunucusu olacaktır. Yerel İnternet çıkışı sağlayarak ve Iç DNS sunucularını Microsoft 365 uç noktaları için yerel ad çözümlemesi sağlayacak şekilde yapılandırarak, Microsoft 365'i hedefleyen ağ trafiği Kullanıcıya mümkün olduğunca yakın microsoft 365 ön uç sunucularına bağlanabilir. Aşağıdaki diyagramda, ana ofis, şube ve uzak konumlardan bağlanan kullanıcıların en yakın Microsoft 365 giriş noktasına giden en kısa yolu izlemesine olanak tanıyan bir ağ topolojisi örneği gösterilmektedir.
  
![Bölgesel çıkış noktalarına sahip WAN ağ modeli.](../media/4d4c07cc-a928-42b8-9a54-6c3741380a33.png)
  
Ağ yolunun Microsoft 365 giriş noktalarına bu şekilde kısaltılması, Microsoft 365'te bağlantı performansını ve son kullanıcı deneyimini geliştirebilir ve ayrıca ağ mimarisinde gelecekte yapılan değişikliklerin Microsoft 365 performansı ve güvenilirliği üzerindeki etkisini azaltmaya yardımcı olabilir.
  
Ayrıca, yanıtlayan DNS sunucusu uzak veya meşgulse DNS istekleri gecikmeye neden olabilir. Dal konumlarında yerel DNS sunucuları sağlayarak ve DNS kayıtlarını uygun şekilde önbelleğe almak için yapılandırıldığından emin olarak ad çözümleme gecikme süresini en aza indirebilirsiniz.
  
Bölgesel çıkış Microsoft 365 için uygun olsa da, bunun şirket ağında veya ev, otel, kafe ve havalimanları gibi uzak konumlarda olmasına bakılmaksızın, en uygun bağlantı modeli her zaman kullanıcının konumunda ağ çıkışı sağlamaktır. Bu yerel doğrudan çıkış modeli aşağıdaki diyagramda gösterilmiştir.
  
![Yerel çıkış ağ mimarisi.](../media/6bc636b0-1234-4ceb-a45a-aadd1044b39c.png)
  
Microsoft 365'i benimseyen kuruluşlar, Microsoft 365'e yönelik kullanıcı bağlantılarının en yakın Microsoft Global Network giriş noktasına giden mümkün olan en kısa yolu izlemesini sağlayarak Microsoft Global Network'ün Dağıtılmış Hizmet Front Door mimarisinden yararlanabilir. Yerel çıkış ağ mimarisi bunu Microsoft 365 trafiğinin kullanıcı konumundan bağımsız olarak en yakın çıkış üzerinden yönlendirilmesine izin vererek yapar.
  
Yerel çıkış mimarisi, geleneksel modele göre aşağıdaki avantajlara sahiptir:
  
- Yol uzunluğunu iyileştirerek en iyi Microsoft 365 performansını sağlar. son kullanıcı bağlantıları, Dağıtılmış Hizmet Front Door altyapısı tarafından dinamik olarak en yakın Microsoft 365 giriş noktasına yönlendirilir.
- Yerel çıkışa izin vererek kurumsal ağ altyapısı üzerindeki yükü azaltır.
- İstemci uç noktası güvenliği ve bulut güvenliği özelliklerinden yararlanarak her iki uçta bağlantıların güvenliğini sağlar.

<a name="BKMK_P3"> </a>
### <a name="avoid-network-hairpins"></a>Ağ saç tokalarından kaçının

![Saç tokalarından kaçının.](../media/ee53e8af-f57b-4292-a256-4f36733b263a.png)
  
Genel bir kural olarak, kullanıcı ile en yakın Microsoft 365 uç noktası arasındaki en kısa, en doğrudan yol en iyi performansı sunar. Ağ saç tokası, belirli bir hedefe bağlı WAN veya VPN trafiği ilk olarak başka bir ara konuma (güvenlik yığını, bulut erişim aracısı veya bulut tabanlı web ağ geçidi gibi) yönlendirildiğinde ortaya çıkar ve coğrafi olarak uzak bir uç noktaya gecikme ve olası yeniden yönlendirme sağlar. Ağ saç tokaları, yönlendirme/eşleme yetersizliklerinden veya yetersiz (uzak) DNS aramalarından da kaynaklanabilir.
  
Microsoft 365 bağlantısının yerel çıkış durumunda bile ağ saç tokalarına tabi olmadığından emin olmak için, kullanıcı konumu için İnternet çıkışı sağlamak için kullanılan ISS'nin Microsoft Global Network ile bu konuma yakın bir doğrudan eşleme ilişkisine sahip olup olmadığını denetleyin. Çıkış yönlendirmesini, İnternet'e bağlı trafiğinizi işleyen üçüncü taraf bir bulut veya bulut tabanlı ağ güvenlik satıcısı üzerinden ara sunucu oluşturma veya tünel oluşturma yerine doğrudan güvenilir Microsoft 365 trafiği gönderecek şekilde yapılandırmak da isteyebilirsiniz. Microsoft 365 uç noktalarının yerel DNS ad çözümlemesi, doğrudan yönlendirmeye ek olarak, kullanıcı bağlantıları için en yakın Microsoft 365 giriş noktalarının kullanılmasını sağlamaya yardımcı olur.
  
Microsoft 365 trafiğiniz için bulut tabanlı ağ veya güvenlik hizmetleri kullanıyorsanız saç tokasının sonucunun değerlendirildiğinden ve Microsoft 365 performansı üzerindeki etkisinin anlaşılmış olduğundan emin olun. Bu işlem, şube ofislerinizin sayısı ve Microsoft Küresel Ağ eşleme noktalarıyla ilişkili olarak trafiğin iletildiği hizmet sağlayıcısı konumlarının sayısı ve konumları, hizmet sağlayıcısının ISS'niz ve Microsoft ile ağ eşleme ilişkisinin kalitesi ve hizmet sağlayıcısı altyapısındaki geri akışın performans etkisi incelenerek yapılabilir.
  
Microsoft 365 giriş noktalarına sahip çok sayıda dağıtılmış konum ve bunların son kullanıcılara yakınlığı nedeniyle, sağlayıcı ağı en iyi Microsoft 365 eşlemesi için yapılandırılmamışsa Microsoft 365 trafiğini herhangi bir üçüncü taraf ağ veya güvenlik sağlayıcısına yönlendirmek Microsoft 365 bağlantılarını olumsuz etkileyebilir.
  
<a name="BKMK_P4"> </a>
### <a name="assess-bypassing-proxies-traffic-inspection-devices-and-duplicate-security-technologies"></a>Proxy'leri atlama, trafik denetleme cihazları ve yinelenen güvenlik teknolojilerini değerlendirme

![Proxy'leri, trafik denetleme cihazlarını ve yinelenen güvenlik teknolojilerini atla.](../media/0131930d-c6cb-4ae1-bbff-fe4cf6939a23.png)
  
Kurumsal müşteriler, özellikle Microsoft 365'e bağlı trafik için ağ güvenliği ve risk azaltma yöntemlerini gözden geçirmeli ve Microsoft 365 ağ trafiği için müdahaleci, performans etkileyen ve pahalı ağ güvenliği teknolojilerine olan güvenlerini azaltmak için Microsoft 365 güvenlik özelliklerini kullanmalıdır.
  
Çoğu kurumsal ağ, proxy'ler, SSL denetimi, paket denetimi ve veri kaybı önleme sistemleri gibi teknolojileri kullanarak İnternet trafiği için ağ güvenliğini zorunlu kmaktadır. Bu teknolojiler, genel İnternet istekleri için önemli risk azaltma sağlar, ancak Microsoft 365 uç noktalarına uygulandığında performansı, ölçeklenebilirliği ve son kullanıcı deneyiminin kalitesini önemli ölçüde azaltabilir.
  
<a name="BKMK_WebSvc"> </a>
#### <a name="office-365-endpoints-web-service"></a>Office 365 Uç Noktaları web hizmeti

Microsoft 365 yöneticileri, Office 365 Uç Noktaları web hizmetinden yapılandırılmış uç noktaların listesini kullanmak ve çevre güvenlik duvarlarının ve diğer ağ cihazlarının yapılandırmalarını güncelleştirmek için bir betik veya REST çağrısı kullanabilir. Bu, Microsoft 365'e yönelik trafiğin tanımlanmasını, uygun şekilde işlenmesini ve genel ve genellikle bilinmeyen İnternet web siteleri için ağ trafiğinden farklı yönetilmesini sağlar. Office 365 Uç Noktaları web hizmetini kullanma hakkında daha fazla bilgi için [Office 365 URL'leri ve IP adresi aralıkları](https://support.office.com/article/office-365-urls-and-ip-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2?ui=en-US&amp;rs=en-US&amp;ad=US) makalesine bakın.
  
#### <a name="pac-proxy-automatic-configuration-scripts"></a>PAC (Ara Sunucu Otomatik Yapılandırma) betikleri
<a name="BKMK_WebSvc"> </a>

Microsoft 365 yöneticileri, WPAD veya GPO aracılığıyla kullanıcı bilgisayarlarına teslim edilebilen PAC (Proxy Otomatik Yapılandırma) betikleri oluşturabilir. PAC betikleri, WAN veya VPN kullanıcılarından gelen Microsoft 365 isteklerine yönelik proxy'leri atlamak için kullanılabilir ve Microsoft 365 trafiğinin şirket ağından geçmek yerine doğrudan İnternet bağlantılarını kullanmasına olanak tanır.
  
#### <a name="microsoft-365-security-features"></a>Microsoft 365 güvenlik özellikleri
<a name="BKMK_WebSvc"> </a>

Microsoft, Microsoft 365 sunucuları ve temsil ettikleri ağ uç noktaları çevresinde veri merkezi güvenliği, operasyonel güvenlik ve risk azaltma konusunda şeffaftır. Microsoft Purview Veri Kaybı Önleme, Virüsten Koruma, Multi-Factor Authentication, Müşteri Kilit Kutusu, Office 365 için Defender, Microsoft 365 Tehdit Bilgileri, Microsoft 365 Güvenli Puanı, Exchange Online Protection ve Ağ DDOS Güvenliği gibi ağ güvenlik riskini azaltmak için Microsoft 365 yerleşik güvenlik özellikleri kullanılabilir.
  
Microsoft veri merkezi ve Genel Ağ güvenliği hakkında daha fazla bilgi için bkz. [Microsoft Güven Merkezi](https://www.microsoft.com/trustcenter/security).
  
## <a name="new-office-365-endpoint-categories"></a>Yeni Office 365 uç nokta kategorileri
<a name="BKMK_Categories"> </a>

Office 365 uç noktaları çeşitli ağ adresleri ve alt ağlar kümesini temsil eder. Uç noktalar URL'ler, IP adresleri veya IP aralıkları olabilir ve bazı uç noktalar belirli TCP/UDP bağlantı noktalarıyla listelenir. URL'ler *account.office.net* gibi bir FQDN veya *.office365.com gibi\** bir joker karakter URL'si olabilir.
  
> [!NOTE]
> Office 365 uç noktalarının ağ içindeki konumları, Microsoft 365 kiracı verilerinin konumuyla doğrudan ilişkili değildir. Bu nedenle müşteriler Microsoft 365'e dağıtılmış ve genel bir hizmet olarak bakmalı ve coğrafi ölçütlere göre Office 365 uç noktalarına ağ bağlantılarını engellemeye çalışmamalıdır.
  
Microsoft 365 trafiğini yönetmeye yönelik önceki kılavuzumuzda uç noktalar **Gerekli** ve **İsteğe Bağlı** olarak iki kategoride düzenlenmişti. Her kategorideki uç noktalar, hizmetin kritikliğine bağlı olarak farklı iyileştirmeler gerektiriyor ve birçok müşteri aynı ağ iyileştirmelerinin uygulanmasını Office 365 URL'lerinin ve IP adreslerinin tam listesine gerekçelendirme konusunda zorluklarla karşılaştı.
  
Yeni modelde uç noktalar **İyileştir**, **İzin Ver** ve **Varsayılan** olmak üzere üç kategoriye ayrılmıştır ve en iyi performans iyileştirmelerini gerçekleştirmek ve yatırım getirisi elde etmek için ağ iyileştirme çalışmalarına odaklanmak için öncelik tabanlı bir özet sağlar. Uç noktalar, etkili kullanıcı deneyiminin senaryoların ağ kalitesine, hacmine ve performans zarfı ile uygulama kolaylığına duyarlılığına bağlı olarak yukarıdaki kategorilerde birleştirilir. Önerilen iyileştirmeler, belirli bir kategorideki tüm uç noktalara aynı şekilde uygulanabilir.
  
- **İyileştirme** uç noktaları her Office 365 hizmetine bağlantı için gereklidir ve Office 365 bant genişliğinin, bağlantılarının ve veri hacminin %75'inden fazlasını temsil eder. Bu uç noktalar ağ performansı, gecikme süresi ve kullanılabilirlik açısından en hassas olan Office 365 senaryolarını temsil eder. Tüm uç noktalar Microsoft veri merkezlerinde barındırılır. Bu kategorideki uç noktalarda değişiklik oranının diğer iki kategorideki uç noktalardan çok daha düşük olması beklenir. Bu kategoride küçük bir anahtar URL kümesi (~10 sırasıyla) ve Exchange Online, SharePoint Online, Skype Kurumsal Çevrimiçi Sürüm ve Microsoft Teams gibi temel Office 365 iş yüklerine ayrılmış tanımlı bir IP alt ağları kümesi bulunur.

    İyi tanımlanmış kritik uç noktaların yoğun bir listesi, bu hedefler için yüksek değerli ağ iyileştirmelerini daha hızlı ve daha kolay planlamanıza ve uygulamanıza yardımcı olmalıdır.

    *İyileştirme* uç noktalarına örnek olarak *https://outlook.office365.com*, *https://\<tenant\>.sharepoint.com* ve *https://\<tenant\>-my.sharepoint.com* verilebilir.

    İyileştirme yöntemleri şunlardır:

  - Ağ cihazlarında ve hizmetlerde trafik kesme, SSL şifre çözme, derin paket incelemesi ve içerik filtreleme gerçekleştiren uç noktaları  *iyileştirmeyi*  atla.
  - Genel İnternet'e gözatma için yaygın olarak kullanılan şirket içi proxy cihazlarını ve bulut tabanlı proxy hizmetlerini atla.
  - Ağ altyapınız ve çevre sistemleriniz tarafından tam olarak güvenilir olarak bu uç noktaların değerlendirilmesine öncelik belirleyin.
  - WAN backhauling'in azaltılmasını veya ortadan kaldırılmasını öncelik sırasına alın ve bu uç noktalar için kullanıcılara/dal konumlarına mümkün olduğunca yakın olan doğrudan dağıtılmış İnternet tabanlı çıkışı kolaylaştırın.
  - Bölünmüş tünel uygulayarak VPN kullanıcıları için bu bulut uç noktalarına doğrudan bağlantıyı kolaylaştırma.
  - DNS ad çözümlemesi tarafından döndürülen IP adreslerinin bu uç noktaların yönlendirme çıkış yoluyla eşleştiğinden emin olun.
  - Microsoft genel ağının en yakın İnternet eşleme noktasına doğrudan ve en düşük gecikme süresi yönlendirmesi için SD-WAN tümleştirmesi için bu uç noktaların önceliklerini belirleyin.

- Belirli Office 365 hizmetleri ve özelliklerine bağlantı için **izin ver** uç noktaları gereklidir, ancak *en iyi duruma getirme* kategorisindekiler kadar ağ performansına ve gecikme süresine duyarlı değildir. Bant genişliği ve bağlantı sayısı açısından bu uç noktaların genel ağ ayak izi de daha küçüktür. Bu uç noktalar Office 365'e ayrılmıştır ve Microsoft veri merkezlerinde barındırılır. Geniş bir Office 365 mikro hizmetlerini ve bağımlılıklarını (yaklaşık 100 URL sırasına göre) temsil eder ve İyileştir kategorisindekilerden daha yüksek bir oranda değişmesi  *beklenir*  . Bu kategorideki tüm uç noktalar tanımlı ayrılmış IP alt ağlarıyla ilişkilendirilmemiştir.

    *İzin ver* uç noktaları için ağ iyileştirmeleri Office 365 kullanıcı deneyimini geliştirebilir, ancak bazı müşteriler ağlarındaki değişiklikleri en aza indirmek için bu iyileştirmelerin kapsamını daha daraltmayı tercih edebilir.

    *İzin Ver* uç noktalarına örnek olarak *https://\*.protection.outlook.com* ve *https://accounts.accesscontrol.windows.net* verilebilir.

    İyileştirme yöntemleri şunlardır:

  - Ağ cihazlarında ve hizmetlerde trafik kesme, SSL şifre çözme, derin paket incelemesi ve içerik filtreleme gerçekleştiren uç noktalara *izin ver'i*  atla.
  - Ağ altyapınız ve çevre sistemleriniz tarafından tam olarak güvenilir olarak bu uç noktaların değerlendirilmesine öncelik belirleyin.
  - WAN backhauling'in azaltılmasını veya ortadan kaldırılmasını öncelik sırasına alın ve bu uç noktalar için kullanıcılara/dal konumlarına mümkün olduğunca yakın olan doğrudan dağıtılmış İnternet tabanlı çıkışı kolaylaştırın.
  - DNS ad çözümlemesi tarafından döndürülen IP adreslerinin bu uç noktaların yönlendirme çıkış yoluyla eşleştiğinden emin olun.
  - Microsoft genel ağının en yakın İnternet eşleme noktasına doğrudan ve en düşük gecikme süresi yönlendirmesi için SD-WAN tümleştirmesi için bu uç noktaların önceliklerini belirleyin.

- **Varsayılan** uç noktalar, herhangi bir iyileştirme gerektirmeyen ve müşteri ağları tarafından normal İnternet'e bağlı trafik olarak ele alınabilen Office 365 hizmetlerini ve bağımlılıklarını temsil eder. Bu kategorideki bazı uç noktalar Microsoft veri merkezlerinde barındırılamayabilir. Örnek olarak ve *`https://appexsin.stb.s-msn.com`* verilebilir *https://odc.officeapps.live.com*.

Office 365 ağ iyileştirme teknikleri hakkında daha fazla bilgi için [Office 365 uç noktalarını yönetme](managing-office-365-endpoints.md) makalesine bakın.
  
## <a name="comparing-network-perimeter-security-with-endpoint-security"></a>Ağ çevre güvenliğini uç nokta güvenliğiyle karşılaştırma
<a name="BKMK_SecurityComparison"> </a>

Geleneksel ağ güvenliğinin amacı, şirket ağ çevresini yetkisiz erişime ve kötü amaçlı açıklara karşı sağlamlaştırmaktır. Kuruluşlar Microsoft 365'i benimsedikçe, bazı ağ hizmetleri ve veriler kısmen veya tamamen buluta geçirilir. Ağ mimarisinde yapılan temel değişikliklere gelince, bu işlem yeni faktörleri dikkate alan ağ güvenliğinin yeniden değerlendirilmesini gerektirir:
  
- Bulut hizmetleri benimsendikçe, ağ hizmetleri ve veriler şirket içi veri merkezleriyle bulut arasında dağıtılır ve çevre güvenliği artık tek başına yeterli değildir.
- Uzak kullanıcılar hem şirket içi veri merkezlerindeki hem de buluttaki şirket kaynaklarına ev, otel ve kafe gibi kontrolsüz konumlardan bağlanır.
- Amaca yönelik güvenlik özellikleri bulut hizmetlerinde giderek daha fazla yerleşik hale getiriliyor ve mevcut güvenlik sistemlerini destekleyebilir veya değiştirebilir.

Microsoft, çok çeşitli Microsoft 365 güvenlik özellikleri sunar ve Microsoft 365 için veri ve ağ güvenliğini sağlamanıza yardımcı olabilecek en iyi güvenlik uygulamalarını kullanmaya yönelik açıklayıcı yönergeler sağlar. Önerilen en iyi yöntemler şunlardır:
  
- **Çok faktörlü kimlik doğrulamasını (MFA) kullanma** MFA, kullanıcıların parolalarını doğru girdikten sonra akıllı telefonlarında telefon aramasını, kısa mesajı veya uygulama bildirimini kabul etmelerini gerektirerek güçlü bir parola stratejisine ek bir koruma katmanı ekler.

- **Cloud Apps için Microsoft Defender'u kullanma** Anormal etkinlikleri izlemek ve üzerinde işlem yapmak için ilkeleri yapılandırın. Yöneticilerin büyük miktarda veri indirme, birden fazla başarısız oturum açma girişimi veya bilinmeyen veya tehlikeli bir IP adreslerinden bağlantılar gibi olağan dışı veya riskli kullanıcı etkinliklerini gözden geçirebilmesi için Cloud Apps için Microsoft Defender ile uyarılar ayarlayın.

- **Veri Kaybı Önlemeyi Yapılandırma (DLP)** DLP, hassas verileri belirlemenize ve kullanıcılarınızın verileri yanlışlıkla veya kasıtlı olarak paylaşmasını önlemeye yardımcı olan ilkeler oluşturmanıza olanak tanır. DLP, kullanıcılarınızın iş akışlarını kesintiye uğratmadan uyumlu kalabilmeleri için Exchange Online, SharePoint Online ve OneDrive dahil olmak üzere Microsoft 365 genelinde çalışır.

- **Müşteri Kasası kullanma** Microsoft 365 yöneticisi olarak, bir Microsoft destek mühendisinin yardım oturumu sırasında verilerinize nasıl erişebileceğini denetlemek için Müşteri Kasası'nu kullanabilirsiniz. Mühendisin bir sorunu gidermek ve düzeltmek için verilerinize erişmesi gereken durumlarda, Müşteri Kasası erişim isteğini onaylamanıza veya reddetmenize olanak tanır.

- **Office 365 Güvenli Puanını kullanma** Riski daha da azaltmak için neler yapabileceğinizi öneren bir güvenlik analizi aracı. Güvenli Puan, Microsoft 365 ayarlarınıza ve etkinliklerinize bakar ve bunları Microsoft tarafından oluşturulan bir temelle karşılaştırır. En iyi güvenlik uygulamalarıyla ne kadar uyumlu olduğunuzu temel alan bir puan alırsınız.

Gelişmiş güvenlik için bütünsel bir yaklaşım aşağıdakileri dikkate almalıdır:
  
- Bulut tabanlı ve Office istemci güvenlik özelliklerini uygulayarak çevre güvenliğinden uç nokta güvenliğine doğru geçiş vurgusu.
  - Güvenlik çevresini veri merkezine küçültme
  - Ofis içindeki veya uzak konumlardaki kullanıcı cihazları için eşdeğer güveni etkinleştirme
  - Veri konumunun ve kullanıcı konumunun güvenliğini sağlamaya odaklanma
  - Yönetilen kullanıcı makineleri uç nokta güvenliği konusunda daha yüksek güvene sahiptir
- Tüm bilgi güvenliğini bütünsel olarak yönetin, yalnızca çevresine odaklanmayı değil
  - Güvenilen trafiğin güvenlik cihazlarını atlamasına izin vererek ve yönetilmeyen cihazları konuk Wi-Fi ağlarına ayırarak WAN'ı yeniden tanımlama ve çevre ağı güvenliğini oluşturma
  - Kurumsal WAN kenarının ağ güvenlik gereksinimlerini azaltma
  - Güvenlik duvarları gibi bazı ağ çevre güvenlik cihazları hala gereklidir, ancak yük azaltılır
  - Microsoft 365 trafiği için yerel çıkış sağlar
- İyileştirmeler [Artımlı iyileştirme bölümünde açıklandığı gibi artımlı](microsoft-365-network-connectivity-principles.md#BKMK_IncOpt) olarak ele alınabilir. Bazı iyileştirme teknikleri, ağ mimarinize bağlı olarak daha iyi maliyet/avantaj oranları sunabilir ve kuruluşunuz için en anlamlı iyileştirmeleri seçmeniz gerekir.

Microsoft 365 güvenliği ve uyumluluğu hakkında daha fazla bilgi için [Microsoft 365 güvenliği](../security/index.yml) ve [Microsoft Purview](../compliance/index.yml) makalelerine bakın.
  
## <a name="incremental-optimization"></a>Artımlı iyileştirme
<a name="BKMK_IncOpt"> </a>

Bu makalenin başlarında SaaS için ideal ağ bağlantı modelini temsil ettik, ancak geçmişe dönük olarak karmaşık ağ mimarileri olan birçok büyük kuruluş için bu değişikliklerin tümünü doğrudan yapmak pratik olmayacaktır. Bu bölümde, Microsoft 365 performansını ve güvenilirliğini geliştirmeye yardımcı olabilecek bir dizi artımlı değişiklik ele alınacağız.
  
Microsoft 365 trafiğini iyileştirmek için kullanacağınız yöntemler, ağ topolojinize ve uyguladığınız ağ cihazlarına bağlı olarak değişir. Birçok konumu ve karmaşık ağ güvenlik uygulamaları olan büyük kuruluşların [Microsoft 365 bağlantı ilkeleri](microsoft-365-network-connectivity-principles.md#BKMK_Principles) bölümünde listelenen ilkelerin çoğunu veya tümünü içeren bir strateji geliştirmesi gerekirken, küçük kuruluşların yalnızca bir veya iki ilkeyi dikkate almaları gerekebilir.
  
İyileştirmeye artımlı bir işlem olarak yaklaşabilir ve her yöntemi art arda uygulayabilirsiniz. Aşağıdaki tabloda, en fazla kullanıcı için gecikme süresi ve güvenilirlik üzerindeki etkileri için anahtar iyileştirme yöntemleri listelenmektedir.
  
|**İyileştirme yöntemi**|**Açıklama**|**Etki**|
|:-----|:-----|:-----|
|Yerel DNS çözümlemesi ve İnternet çıkışı  <br/> |Her konumda yerel DNS sunucuları sağlayın ve Microsoft 365 bağlantılarının kullanıcının konumuna mümkün olduğunca yakın İnternet'e çıkışını sağlayın.  <br/> | Gecikme süresini en aza indirme  <br/>  En yakın Microsoft 365 giriş noktasına güvenilir bağlantıyı geliştirme  <br/> |
|Bölgesel çıkış noktaları ekleme  <br/> |Şirket ağınızda birden çok konum varsa ancak yalnızca bir çıkış noktası varsa, kullanıcıların en yakın Microsoft 365 giriş noktasına bağlanmasını sağlamak için bölgesel çıkış noktaları ekleyin.  <br/> | Gecikme süresini en aza indirme  <br/>  En yakın Microsoft 365 giriş noktasına güvenilir bağlantıyı geliştirme  <br/> |
|Proxy'leri ve denetleme cihazlarını atlama  <br/> |Microsoft 365 isteklerini doğrudan çıkış noktalarına gönderen PAC dosyalarıyla tarayıcıları yapılandırın.  <br/> Microsoft 365 trafiğine denetim olmadan izin vermek için kenar yönlendiricilerini ve güvenlik duvarlarını yapılandırın.  <br/> | Gecikme süresini en aza indirme  <br/>  Ağ cihazlarında yükü azaltma  <br/> |
|VPN kullanıcıları için doğrudan bağlantıyı etkinleştirme  <br/> |VPN kullanıcıları için, bölünmüş tünel uygulayarak Microsoft 365 bağlantılarının VPN tüneli üzerinden değil doğrudan kullanıcının ağından bağlanmasına olanak tanıyın.  <br/> | Gecikme süresini en aza indirme  <br/>  En yakın Microsoft 365 giriş noktasına güvenilir bağlantıyı geliştirme  <br/> |
|Geleneksel WAN'dan SD-WAN'a geçiş  <br/> |SD-WANs (Yazılım Tanımlı Geniş Alan Ağları), sanal makineleri (VM) kullanarak işlem kaynaklarını sanallaştırmaya benzer şekilde geleneksel WAN yönlendiricilerini sanal gereçlerle değiştirerek WAN yönetimini basitleştirir ve performansı geliştirir.  <br/> | WAN trafiğinin performansını ve yönetilebilirliğini geliştirme  <br/>  Ağ cihazlarında yükü azaltma  <br/> |

## <a name="related-topics"></a>İlgili konular

[Microsoft 365 Ağ Bağlantısına Genel Bakış](microsoft-365-networking-overview.md)

[Office 365 uç noktalarını yönetme](managing-office-365-endpoints.md)

[Office 365 URL'leri ve IP adresi aralıkları](urls-and-ip-address-ranges.md)

[Office 365 IP Adresi ve URL Web hizmeti](microsoft-365-ip-web-service.md)

[Microsoft 365 ağ bağlantısını değerlendirme](assessing-network-connectivity.md)

[Microsoft 365 için ağ planlama ve performans ayarlama](network-planning-and-performance.md)

[Temelleri ve performans geçmişini kullanarak Office 365 performans ayarlama](performance-tuning-using-baselines-and-history.md)

[Office 365 için performans sorunlarını giderme planı](performance-troubleshooting-plan.md)

[İçerik Teslim Ağları](content-delivery-networks.md)

[Microsoft 365 bağlantı testi](https://aka.ms/netonboard)

[Microsoft hızlı ve güvenilir küresel ağını nasıl oluşturur?](https://azure.microsoft.com/blog/how-microsoft-builds-its-fast-and-reliable-global-network/)

[Office 365 Ağ blogu](https://techcommunity.microsoft.com/t5/Office-365-Networking/bd-p/Office365Networking)
