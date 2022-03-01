---
title: Microsoft 365 bağlantısı ilkeleri
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: Bu makale, ağ bağlantısını güvenli bir şekilde en iyi duruma Microsoft 365 en güncel kılavuzu sağlar.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 1cea07745295f945f472dfeaa7042d3b027eea85
ms.sourcegitcommit: 1ef176c79a0e6dbb51834fe30807409d4e94847c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/19/2021
ms.locfileid: "63006763"
---
# <a name="microsoft-365-network-connectivity-principles"></a>Microsoft 365 bağlantısı ilkeleri

*Bu makale hem son hem de Microsoft 365 Kurumsal hem de Office 365 Kurumsal.*

Ağ bağlantınızı ağ bağlantısını Microsoft 365 başlamadan önce, trafiği güvenli bir şekilde yönetmeye ve mümkün olan en iyi performansı elde Microsoft 365 bağlantı ilkelerini anlamak önemlidir. Bu makale, ağ bağlantısını güvenli bir şekilde en iyi duruma getirme konusunda Microsoft 365 yardımcı olacaktır.
  
Geleneksel kurumsal ağlar öncelikle kullanıcıların güçlü çevre güvenliğine sahip, şirket tarafından işletilen veri merkezlerinde barındırılan uygulamalara ve verilere erişmesini sağlamak için tasarlanmıştır. Geleneksel model, kullanıcıların şirket ağ çevresi içinde, şubelerden WAN bağlantıları üzerinden veya VPN bağlantıları üzerinden uzaktan uygulamalara ve verilere erişeceklerini varsayıyor.
  
SaaS uygulamalarının benimsenmesi, Microsoft 365 ve veri bileşimlerini ağ çevrenin dışına taşır. İyileştirme olmadan, kullanıcılar ve SaaS uygulamaları arasındaki trafik paket incelemeleri, ağ A uç noktaları, coğrafi olarak uzak uç noktalara ve diğer etmenlere yanlışlıkla bağlantılar tarafından ortaya konu alan gecikmeye neden olur. Önemli iyileştirme yönergelerini an Microsoft 365 ve uygulayarak en iyi performansı ve güvenilirliği sabilirsiniz.
  
Bu makalede şunları öğrenirsiniz:
  
- [Microsoft 365 bulut](microsoft-365-network-connectivity-principles.md#BKMK_Architecture) bağlantısı için geçerli olan mimariyi benimser
- Ağ [Microsoft 365 ve](microsoft-365-network-connectivity-principles.md#BKMK_Principles) son kullanıcı deneyimini en iyi duruma getirmeyle ilgili güncelleştirilmiş bağlantı ilkeleri ve stratejileri
- Ağ [yöneticilerinin Office 365 iyileştirmede](microsoft-365-network-connectivity-principles.md#BKMK_WebSvc) kullanmak üzere yapılandırılmış uç nokta listesini kullanmalarını sağlayan Kullanıcı Uç Noktaları web hizmetidir
- [Yeni Office 365 uç noktası kategorilerini ve](microsoft-365-network-connectivity-principles.md#BKMK_Categories) iyileştirme kılavuzu
- [Ağ çevre güvenliği ile uç nokta güvenliği karşılaştırması](microsoft-365-network-connectivity-principles.md#BKMK_SecurityComparison)
- [Trafiğin artımlı](microsoft-365-network-connectivity-principles.md#BKMK_IncOpt) iyileştirme Microsoft 365 seçenekleri
- The [Microsoft 365 connectivity test the new](https://aka.ms/netonboard) tool for testing basic connectivity to Microsoft 365

## <a name="microsoft-365-architecture"></a>Microsoft 365 mimarisi
<a name="BKMK_Architecture"> </a>

Microsoft 365, Exchange Online, SharePoint Online ve Skype Kurumsal Online gibi farklı mikro hizmetler ve uygulamalar kümesi aracılığıyla üretkenlik ve işbirliği senaryoları sağlayan, dağıtılmış bir Hizmet Olarak Yazılım (SaaS) bulutudur. Microsoft Teams tarayıcıda Exchange Online Protection, Office ve daha birçok şey olabilir. Belirli Microsoft 365 uygulamalarının, müşteri ağı ve bulut bağlantısı için geçerli olduğu benzersiz özellikleri olabilir, ancak bunların hepsi bazı önemli ana bilgileri, hedefleri ve mimari desenlerini paylaşır. Bu ilkeler ve bağlantı mimarisi desenleri, diğer birçok SaaS bulutu için tipikdir ve aynı zamanda Microsoft Azure gibi Platform-as-a-Service ve Infrastructure-as-a-Service bulutlarının tipik dağıtım modellerinden farklıdır.
  
Microsoft 365'in en önemli mimari özelliklerinden biri (çoğunlukla ağ mimarları tarafından kaçırıldığında veya yanlış kullanılan) bu hizmetin, kullanıcıların buna bağlanma bağlamında gerçekten küresel dağıtılmış bir hizmet olmasıdır. Hedef Microsoft 365 kiracının konumu, müşteri verilerinizin bulutta depolandığı konumu anlamak açısından önemlidir, ancak Microsoft 365 ile kullanıcı deneyimi verileri içeren disklere doğrudan bağlanmayla ilgili değildir. Performans özellikleriyle (Microsoft 365, güvenilirlik ve diğer önemli kalite özellikleri dahil) kullanıcı deneyimi, dünya çapında yüzlerce Microsoft konumunun ölçeğini artıran yüksek dağıtılmış hizmet ön kapıları üzerinden bağlantı içerir. Çoğu durumda, en iyi kullanıcı deneyimi elde etmek için müşteri ağının kullanıcı isteklerini merkezi bir konumda veya bölgede bir çıkış noktasından Microsoft 365'e bağlamak yerine en yakın Microsoft 365 Microsoft 365 hizmet giriş noktasına yönlendirmesi sağlanır.
  
Çoğu müşteri için Microsoft 365 çok sayıda konuma dağıtılmıştır. En iyi sonuçları elde etmek için, bu belgede ana hatları verilen ilkelere genel bakış açısından ölçek ölçeği (ölçeği yukarı değil) noktasından temel almak gerekir, bu ilkeler Microsoft 365 kiracının coğrafi konumuyla değil Microsoft Global Ağı'nda iletişim durumu en yakın noktasına olan bağlantıları en iyi duruma getirmeye odaklanmalıdır. Öz olarak bu, Microsoft 365 kiracı verileri belirli bir coğrafi konumda depolanıyor olsa bile, o kiracının Microsoft 365 deneyimi dağıtılmış olarak kalır ve kiracının sahip olduğu son kullanıcı konumlarına çok yakın bir konumda (ağ) yakınlığı içinde yer almaktadır.
  
## <a name="microsoft-365-connectivity-principles"></a>Microsoft 365 ilkeleri
<a name="BKMK_Principles"> </a>

Microsoft, en iyi bağlantı ve performansı elde etmek için Microsoft 365 ilkeler önermektedir. Trafiğinizi yönetmek Microsoft 365 bağlantıda en iyi performansı elde etmek için bu Microsoft 365.
  
Ağ tasarımında temel amaç, ağınız arasındaki gidiş dönüş süresini (RTT) Microsoft Genel Ağı'na azaltarak ve Microsoft'un tüm veri merkezleriyle düşük gecikme süresi ve dünyanın her yerine bulut uygulaması giriş noktaları arasında bağlantı oluşturan genel ağ omurgasını azaltarak gecikmeyi en aza indirmek olmalıdır. Microsoft'un hızlı ve güvenilir global ağı oluşturması [bağlantısında Microsoft Genel Ağ hakkında daha fazla bilgi öğrenebilirsiniz](https://azure.microsoft.com/blog/how-microsoft-builds-its-fast-and-reliable-global-network/).
  
<a name="BKMK_P1"> </a>
### <a name="identify-and-differentiate-microsoft-365-traffic"></a>Trafiği tanımlama ve Microsoft 365 ayırma

![Trafik Microsoft 365 belirleme.](../media/621aaec9-971d-4f19-907a-1ae2ef6d72fc.png)
  
Ağ Microsoft 365 belirlemek, trafiğin genel İnternet'e bağlı ağ trafiğinden ayırt  olmanın ilk adımıdır. Microsoft 365 bağlantı, ağ yönlendirmesi iyileştirme, güvenlik duvarı kuralları, tarayıcı ara sunucu ayarları ve bazı uç noktalar için ağ denetleme cihazlarını atlama gibi bir yaklaşım birleşimi uygulanarak en iyi duruma edilebilir.
  
Daha Microsoft 365 iyileştirme kılavuzu, uç Microsoft 365 Gerekli ve İsteğe Bağlı olarak **iki kategoriye** **ayrılmıştır**. Yeni Microsoft 365 hizmetleri ve özelliklerini desteklemek için uç noktalar eklendik ve Microsoft 365 üç kategori olarak yeniden düzenledik **: En** İyi Duruma **Getirme, İzin** Ver ve **Varsayılan**. Her kategoriye yönelik yönergeler, kategorideki tüm uç noktalar için geçerlidir, bu da iyileştirmelerin daha kolay anlaşılır ve uygulandığını sağlar.
  
Uç nokta kategorilerini ve iyileştirme Microsoft 365 hakkında daha fazla bilgi için Yeni uç nokta [Office 365 bölümüne](microsoft-365-network-connectivity-principles.md#BKMK_Categories) bakın.
  
Microsoft artık tüm Microsoft 365 uç noktalarını bir web hizmeti olarak yayımlar ve bu verilerin en iyi kullanımı konusunda yol göstermeyi sağlar. Bu uç noktaları getirme ve bu uç noktalarla Microsoft 365 hakkında daha fazla bilgi için [URL'Office 365 IP adresi aralıklarını görme makalesine bakın](https://support.office.com/article/office-365-urls-and-ip-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2?ui=en-US&amp;rs=en-US&amp;ad=US).
  
<a name="BKMK_P2"> </a>
### <a name="egress-network-connections-locally"></a>Egress bağlantılarını yerel olarak yapılandırma

![Egress ağ bağlantılarını yerel olarak tıklatın.](../media/b42a45be-1ab4-4073-a7dc-fbdfb4aedd24.png)
  
Yerel DNS ve İnternet çıkış, bağlantı gecikmesini azaltmaya ve kullanıcı bağlantılarının hizmetlere en yakın giriş noktasına gidilemesini sağlama açısından Microsoft 365 önem taşır. Karmaşık bir ağ topolojisinde, hem yerel DNS hem de yerel İnternet çıkışlarını birlikte uygulamak önemlidir. Bu makalede, istemci bağlantılarını Microsoft 365 girdinin en yakın noktasına nasıl yönlendir olduğu hakkında daha fazla bilgi için, İstemci Bağlantısı [makalesine bakın](https://support.office.com/article/client-connectivity-4232abcf-4ae5-43aa-bfa1-9a078a99c78b).
  
Ağ mimarisinde tasarım faktörü olarak son Microsoft 365 İnternet bağlantısı, önceden oldukça basitti. İnternet hizmetleri ve web siteleri dünyanın her yerine dağıtıldığında, şirket çıkış noktalarıyla verilen hedef uç nokta arasındaki gecikme süresi büyük ölçüde coğrafi mesafeye sahip bir işlevdir.
  
Geleneksel ağ mimarisinde, tüm giden İnternet bağlantıları şirket ağına çapraz geçiş ve merkezi bir konumdan çıkış sağlar. Microsoft'un bulut teklifleri olgunlaştıkça, İnternet'e yönelik dağıtılmış bir ağ mimarisi gecikmeye duyarlı bulut hizmetlerini desteklemek için kritik hale geldi. Microsoft Global Network, gelen bulut hizmeti bağlantılarını en yakın giriş noktasına yönlendiren global giriş noktalarına sahip dinamik bir doku olan Dağıtılmış Hizmet Ön Kapı altyapısıyla gecikme gereksinimlerini karşılayacak şekilde tasarlanmıştır. Bu, Microsoft bulut müşterileri için müşteriyle bulut arasındaki yolu etkili bir şekilde kısaltarak "son kilometre" uzunluğunu azaltmayı amaçlıyor.
  
Enterprise WAN'ler, çoğunlukla bir veya birden çok ara sunucu üzerinden İnternet'e çıkış öncesinde ağ trafiğini merkezi bir şirket genel dairesine inceleme yapmak üzere tasarlanmıştır. Aşağıdaki diyagramda bu tür bir ağ topolojisi gösterilmiştir.
  
![Geleneksel kurumsal ağ modeli.](../media/fc87b8fd-a191-47a7-9704-1e445599813a.png)
  
Microsoft Microsoft 365 tüm dünyada ön uç sunucularını da içeren Microsoft Global Network'de çalışır, bu nedenle genellikle kullanıcının bulunduğu konuma yakın bir ön uç sunucusu olur. Yerel İnternet çıkış sağlamanın yanı sıra iç DNS sunucularını Microsoft 365 uç noktaları için yerel ad çözümlemesi sağlayacak şekilde yapılandırarak, Microsoft 365'i amaçlanan ağ trafiği kullanıcıya mümkün olduğunca yakın bir şekilde Microsoft 365 ön uç sunucularına bağlanabilirsiniz. Aşağıdaki diyagramda, kullanıcıların ana ofis, şube ve uzak konumlardan en kısa yolu takip etmek için en yakın ofis veya giriş noktasına bağlanmalarına olanak sağlayan bir Microsoft 365 örneği gösterilir.
  
![Bölgesel çıkış noktalarına sahip WAN ağ modeli.](../media/4d4c07cc-a928-42b8-9a54-6c3741380a33.png)
  
Bu şekilde Microsoft 365 girdi noktalarının ağ yolunun kısaltılması, Microsoft 365'te bağlantı performansını ve son kullanıcı deneyimini geliştirebilir ve ağ mimarisinde gelecekteki değişikliklerin Microsoft 365 performansı ve güvenilirliği üzerindeki etkisini azaltmaya yardımcı olabilir.
  
Ayrıca, yanıt veren DNS sunucusu uzak veya meşgulse DNS istekleri gecikmeye neden olabilir. Dal konumlarında yerel DNS sunucularını sağ kullanarak ve DNS kayıtlarını doğru önbelleğe aecek şekilde yapılandırıldıklarına emin olarak ad çözümleme gecikmesini en aza indirebilirsiniz.
  
Bölgesel çıkış Microsoft 365'da iyi sonuç sağlaysa da, en uygun bağlantı modeli bunun şirket ağın içinde mi yoksa ev, oteller, kafe ve havalimanları gibi uzak konumlarda mı bulunduğuna bakılmaksızın her zaman kullanıcının bulunduğu konumda ağ çıkış sağlamak olabilir. Bu yerel doğrudan çıkış modeli aşağıdaki diyagramda gösterilmiştir.
  
![Yerel çıkış ağı mimarisi.](../media/6bc636b0-1234-4ceb-a45a-aadd1044b39c.png)
  
Microsoft 365 benimseyen kuruluşlar, kullanıcı bağlantılarının mümkün olan en kısa yolu en yakın Microsoft Genel Ağ giriş noktasına almalarını sağlayarak Microsoft Global Network Microsoft 365'un Dağıtılmış Hizmet Ön Kapı mimarisinin avantajını kullanabilir. Yerel çıkış ağ mimarisi bunu, kullanıcı Microsoft 365 bakılmaksızın trafiğin en yakın çıkış üzerinden yönlendirilemelerine izin vererek bunu yapar.
  
Yerel çıkış mimarisi geleneksel model üzerinde aşağıdaki avantajlara sahiptir:
  
- Yönlendirme uzunluğunu Microsoft 365 iyi bir performans sağlar. Son kullanıcı bağlantıları Dağıtılmış Hizmet Ön Microsoft 365 tarafından en yakın kapı giriş noktasına dinamik olarak yönlendirildi.
- Yerel çıkışa izin vererek şirket ağ altyapısının yükünü azaltır.
- İstemci uç noktası güvenliği ve bulut güvenliği özelliklerinden yararlanarak her iki uç üzerindeki bağlantıların güvenliğini sağlar.

<a name="BKMK_P3"> </a>
### <a name="avoid-network-hairpins"></a>Ağ Apin'lerden kaçının

![Apinlerden kaçının.](../media/ee53e8af-f57b-4292-a256-4f36733b263a.png)
  
Genel bir başparmak kuralı olarak, kullanıcıyla en yakın uç nokta arasındaki en kısa, Microsoft 365 yönlendirme en iyi performansı sunar. Belirli bir hedefle ilişkili WAN veya VPN trafiği önce başka bir ara konuma (güvenlik yığını, bulut erişimi aracısı veya bulut tabanlı web ağ geçidi gibi) yönlendirilmesi, gecikme süresinin ve coğrafi olarak uzak bir uç noktanın olası yeniden yönlendirmesine neden olmasıyla gerçekleşir. Ağ kökleri yönlendirme/eşleme tutarsızlıklarından veya alt (uzak) DNS aramalarından da kaynaklandırabilirsiniz.
  
Microsoft 365 bağlantısının yerel çıkış durumunda bile ağ U-fi'lerine tabi olmadığını sağlamak için, kullanıcı konumu için İnternet çıkış sağlamak için kullanılan ISS'nin Microsoft Genel Ağ ile bu konuma yakın bir doğrudan eşleme ilişkisi olup olmadığını denetleyin. Ayrıca İnternet'e bağlı trafiğinizi işlemeye yönelik üçüncü taraf bulut veya bulut tabanlı bir ağ güvenlik satıcısına ara sunucu ve trafiğin bu şekilde geçişini yapmak yerine, güvenilir Microsoft 365 trafiğini doğrudan göndermek için çıkış yönlendirmesi yapılandırabilirsiniz. Kullanıcı bağlantılarında kullanılan Microsoft 365 DNS ad çözümlemesi, doğrudan yönlendirmeye ek olarak, kullanıcı bağlantılarında Microsoft 365 en yakın girdi noktalarının da kullanılmaktadır.
  
Microsoft 365 trafiğiniz için bulut tabanlı ağ veya güvenlik hizmetleri kullanıyorsanız, Apin'in sonucun değerlendirili olduğundan ve bu ağın performans üzerindeki Microsoft 365 anlaşıla olduğundan emin olun. Bu, hizmet sağlayıcısı konumlarının sayısı ve konumları ince kullanarak trafiğin şube say geçen ofis sayısıyla ve Microsoft Genel Ağ eşliği noktalarıyla, hizmet sağlayıcısının ISS ve Microsoft ile ağ eşliği ilişkisi kalitesiyle ve hizmet sağlayıcısı altyapısında geri yönlendirmenin performans üzerindeki etkisi ince yoluyla yapılabilir.
  
Microsoft 365 giriş noktaları bulunan çok fazla sayıda dağıtılmış konum ve bunların son kullanıcılara yakınlığı nedeniyle, Microsoft 365 trafiğini üçüncü taraf ağlara veya güvenlik sağlayıcılarına yönlendirme, sağlayıcı ağı en iyi performans için yapılandırılmamışsa Microsoft 365 bağlantılarında olumsuz Microsoft 365 eşliği.
  
<a name="BKMK_P4"> </a>
### <a name="assess-bypassing-proxies-traffic-inspection-devices-and-duplicate-security-technologies"></a>Atlayan aracıları, trafik denetleme cihazlarını ve yinelenen güvenlik teknolojilerini değerlendirme

![Geçişleri, trafik denetleme cihazlarını ve yinelenen güvenlik teknolojilerini atlar.](../media/0131930d-c6cb-4ae1-bbff-fe4cf6939a23.png)
  
Enterprise müşterilerin özellikle Microsoft 365'a bağlı trafik için ağ güvenliği ve risk azaltma yöntemlerini gözden geçirmesi ve Microsoft 365 ağ trafiği için izinsiz Microsoft 365, performansı etkileyen ve pahalı ağ güvenlik teknolojilerine bağlı Microsoft 365 özelliklerini kullanmaları gerekir.
  
Kurumsal ağların çoğu, aracılar, SSL incelemesi, paket incelemesi ve veri kaybı önleme sistemleri gibi teknolojileri kullanarak İnternet trafiği için ağ güvenliğini zorunludur. Bu teknolojiler genel İnternet istekleri için önemli risk azaltmaları sağlar, ancak Microsoft 365 uç noktalarına uygulandığında performansı, ölçeklenebilirliği ve son kullanıcı deneyiminin kalitesini önemli ölçüde azaltır.
  
<a name="BKMK_WebSvc"> </a>
#### <a name="office-365-endpoints-web-service"></a>Office 365 Uç Noktaları web hizmeti

Microsoft 365 yöneticileri betik veya REST çağrısı kullanarak Office 365 Uç Noktaları web hizmetinin yapılandırılmış uç noktalarının listesini kullanabilir ve çevre güvenlik duvarları ile diğer ağ cihazlarının yapılandırmalarını güncelleştirebilirsiniz. Bu, genel ve çoğunlukla bilinmeyen İnternet web siteleri için Microsoft 365 olan ağ trafiğinden farklı tanım, işlem yapılması ve yönetilmelerini sağlar. Office 365 Endpoints web hizmetinin kullanımı hakkında daha fazla bilgi için URL'ler [Office 365 IP adresi aralıkları makalesine bakın](https://support.office.com/article/office-365-urls-and-ip-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2?ui=en-US&amp;rs=en-US&amp;ad=US).
  
#### <a name="pac-proxy-automatic-configuration-scripts"></a>PAC (Proxy Otomatik Yapılandırma) betikleri
<a name="BKMK_WebSvc"> </a>

Microsoft 365 yöneticiler, WPAD veya GPO aracılığıyla kullanıcı bilgisayarlarına teslim edilen PAC (Proxy Otomatik Yapılandırması) betikleri oluşturabilir. PAC betikleri, WAN veya VPN kullanıcılarından gelen Microsoft 365 sunucularını atlamak için kullanılabilir ve Microsoft 365 trafiğinin şirket ağına çapraz geçiş yerine doğrudan İnternet bağlantılarını kullanmasına olanak verir.
  
#### <a name="microsoft-365-security-features"></a>Microsoft 365 özelliklerini ve
<a name="BKMK_WebSvc"> </a>

Microsoft, veri merkezi güvenliği, işlem güvenliği ve temsil edilen Microsoft 365 uç noktaları çevresinde risk azaltma konusunda saydamdır. Microsoft 365 Kaybı Önleme, Virüsten Koruma, Multi-Factor Authentication, Müşteri Kilidi Kutusu, Office 365 için Defender, Microsoft 365 Tehdit İstihbaratı, Güvenlik Puanı gibi ağ güvenliği riskini azaltmak için Office 365 yerleşik güvenlik Microsoft 365 kullanılabilir. Exchange Online Protection ve Ağ DDOS Güvenliği'ne bağlanın.
  
Microsoft veri merkezi ve Genel Ağ güvenliği hakkında daha fazla bilgi için bkz. [Microsoft Güven Merkezi](https://www.microsoft.com/trustcenter/security).
  
## <a name="new-office-365-endpoint-categories"></a>Yeni Office 365 uç noktası kategorileri
<a name="BKMK_Categories"> </a>

Office 365 uç noktaları, değişken bir ağ adresi ve alt ağ kümesi temsil ediyor. Uç noktalar URL'ler, IP adresleri veya IP aralıkları olabilir ve bazı uç noktalar belirli TCP/UDP bağlantı noktalarıyla listelenmiştir. URL'ler, account.office.net gibi bir FQDN *\*veya .office365.com*.
  
> [!NOTE]
> Ağ içindeki Office 365 konumları, kiracı verilerini alan veya kiracının Microsoft 365 ilgili değildir. Bu nedenle, müşteriler Microsoft 365 ve genel hizmet olarak değerlendirmeli ve coğrafi ölçütlere dayalı olarak Office 365 uç noktalarına ağ bağlantılarını engellemeye çalışmamalı.
  
Daha önce yol gösterici trafiğin yönetimiyle ilgili Microsoft 365, uç noktalar Gerekli ve İsteğe Bağlı olarak iki **kategori olarak** **düzenlenmiştir**. Her kategorideki uç noktalar, hizmetin kritik durumuna bağlı olarak farklı iyileştirmeler gerektirir ve birçok müşteri aynı ağ iyileştirmelerinin uygulamayı Office 365 URL'leri ve IP adreslerinin tam listesine ikiser olarak yaslamada zorlukla karşılaşmaktadır.
  
Yeni modelde uç noktalar En İyi Duruma Getir, İzin Ver ve Varsayılan olarak üç kategoride ayrılır ve en iyi performans iyileştirmelerini gerçekleştirmek ve yatırıma dönmek için ağ iyileştirme çabalarına odaklanan, öncelik tabanlı bir özet sunar.  Uç noktalar yukarıdaki kategorilerde, etkin kullanıcı deneyiminin senaryolar için ağ kalitesi, hacim ve performans zarfının duyarlılığına ve uygulama kolaylığına bağlı olarak birleştirilmiştir. Önerilen iyileştirmeler, verilen kategorideki tüm uç noktalara aynı şekilde uygulanabilir.
  
- **En** iyi duruma getirme uç noktaları, her Office 365 hizmetine bağlantı için gereklidir ve Office 365, bağlantı Office 365 ve veri hacminin %75'ini temsil eder. Bu uç noktalar Office 365 performansı, gecikme süresi ve kullanılabilirliği konusunda en hassas senaryoları temsil ediyor. Tüm uç noktalar Microsoft veri merkezlerinde barındırıldı. Bu kategorideki uç noktalara yönelik değişiklik oranının, diğer iki kategorideki uç noktalardan çok daha düşük olması bekmektedir. Bu kategori küçük (~10) anahtar URL'leri kümesi ve Exchange Online, SharePoint Online, Skype Kurumsal Online ve Microsoft Teams gibi temel Office 365 iş yüklerini ayrılmış ip alt ağlarının küçük bir (~10) kümesine dahildir.

    İyi tanımlanmış kritik uç noktaların kismli bir listesi, bu hedefler için yüksek değerli ağ iyileştirmelerini daha hızlı ve daha kolay planlamanıza ve uygulamanıza yardımcı olur.

    En iyi  *duruma*  getirme uç noktalarına *https://outlook.office365.com* örnek olarak *, https://\<tenant\>.sharepoint.com* ve *https://\<tenant\>-my.sharepoint.com*.

    İyileştirme yöntemleri şunlardır:

  - *Trafiğin kesişme* noktası, SSL şifre çözme, derin paket incelemesi ve içerik filtrelemesi yapan ağ cihazlarında ve hizmetlerde en iyi duruma getirme uç noktalarını atla.
  - Genel İnternet'e gözatma için yaygın olarak kullanılan şirket içi ara sunucu cihazlarını ve bulut tabanlı ara sunucu hizmetlerini atla.
  - Bu uç noktaların ağ altyapınız ve çevre sistemleriniz tarafından tümüyle güvenilir olacak şekilde değerlendirilmesine öncelik verir.
  - WAN geri kullanımında azaltma veya eleme önceliklerini belirleme ve bu uç noktalar için kullanıcılara/dal konumlarına mümkün olduğunca yakın, doğrudan dağıtılmış İnternet tabanlı çıkışını kolaylaştırın.
  - Bölünmüş bölmeler gerçekleştirerek VPN kullanıcıları için bu bulut uç noktalarına doğrudan bağlantıları kolaylaştırın.
  - DNS ad çözümlemesi tarafından döndürülen IP adreslerinin bu uç noktaların yönlendirme çıkış yoluyla eş olduğundan emin olun.
  - Microsoft genel ağının en yakın İnternet eşleme noktasına doğrudan, en düşük gecikme süresi yönlendirmesi için SD-WAN tümleştirmesi için bu uç noktaların önceliklerini belirleme.

- **Belirli** Office 365 hizmetleri ve özellikleriyle bağlantı için uç noktalara izin ver gerekir, ancak En İyi Duruma Getirme kategorisindekilerle aynı ağ performansına ve gecikme süresine *duyarlı* değildir. Bant genişliği ve bağlantı sayısı açısından bu uç noktaların ağ kap kaplanı da daha küçüktür. Bu uç noktalar özel Office 365 ve Microsoft veri merkezlerinde barındırıldı. Bunlar çok çeşitli Office 365 mikro hizmetler ve bağımlılıklarını (~100 URL'ler sırasıyla) temsil ediyor ve En İyi Duruma Getirme kategorisindekilerden daha yüksek bir oranda değişmeleri *bek* gerekmektedir. Bu kategorideki uç noktaların hepsi, tanımlanmış ayrılmış IP alt ağlarıyla ilişkilendirilz.

    Uç noktalara *izin ver* için ağ iyileştirmeleri kullanıcı deneyimini Office 365, ancak bazı müşteriler ağ üzerindeki değişiklikleri en aza indirmek için bu iyileştirmelerin kapsamını daha dar olarak artırmayı seçebilir.

    uç *noktalara izin* ver örnekleri *https://\*.protection.outlook.com* ve .*https://accounts.accesscontrol.windows.net*

    İyileştirme yöntemleri şunlardır:

  - *Atla Trafik* kesişme, SSL şifre çözme, derin paket incelemesi ve içerik filtrelemesi yapan ağ cihazlarında ve hizmetlerde uç noktalara izin ver'i atla.
  - Bu uç noktaların ağ altyapınız ve çevre sistemleriniz tarafından tümüyle güvenilir olacak şekilde değerlendirilmesine öncelik verir.
  - WAN geri kullanımında azaltma veya eleme önceliklerini belirleme ve bu uç noktalar için kullanıcılara/dal konumlarına mümkün olduğunca yakın, doğrudan dağıtılmış İnternet tabanlı çıkışını kolaylaştırın.
  - DNS ad çözümlemesi tarafından döndürülen IP adreslerinin bu uç noktaların yönlendirme çıkış yoluyla eş olduğundan emin olun.
  - Microsoft genel ağının en yakın İnternet eşleme noktasına doğrudan, en düşük gecikme süresi yönlendirmesi için SD-WAN tümleştirmesi için bu uç noktaların önceliklerini belirleme.

- **Varsayılan** uç noktalar Office 365 iyileştirme gerektirmeyen etki alanı hizmetlerini ve bağımlılıkları temsil etmekte ve müşteri ağları tarafından İnternet'e bağlı trafik olarak kabul edilebilir. Bu kategorideki bazı uç noktalar Microsoft veri merkezlerinde barındırlanmıyor olabilir. Örnek olarak ve *https://odc.officeapps.live.com* .*https://appexsin.stb.s-msn.com*

Ağ iyileştirme tekniklerini Office 365 daha fazla bilgi için Office 365 [makalesine bakın](managing-office-365-endpoints.md).
  
## <a name="comparing-network-perimeter-security-with-endpoint-security"></a>Ağ çevre güvenliği ile uç nokta güvenliği karşılaştırması
<a name="BKMK_SecurityComparison"> </a>

Geleneksel ağ güvenliğinin amacı izinsiz giriş ve kötü amaçlı istismarlara karşı şirket ağ çevresini güvenliğini hedeflemektir. Kuruluşlar genel Microsoft 365 olarak, bazı ağ hizmetleri ve veriler kısmen veya tamamen buluta geçirilir. Ağ mimarisinde herhangi bir temel değişiklik yapmak için, bu süreç yeni ortaya çıkan faktörleri hesaba alan ağ güvenliğinin yeniden de değerlendirilmesini gerektirir:
  
- Bulut hizmetleri benimsendi olarak, ağ hizmetleri ve veriler şirket içi veri merkezleriyle bulut arasında dağıtılır ve çevre güvenliği artık kendi başına yeterli olmaz.
- Uzak kullanıcılar hem şirket içi veri merkezlerinden hem de bulutta ev, oteller ve kafe gibi kontrol edilemeyen konumlardan şirket kaynaklarına bağlanıyor.
- Amaca yönelik güvenlik özellikleri giderek bulut hizmetlerde yerleşik olarak gelir ve var olan güvenlik sistemlerini tamamlar veya değiştirebilir.

Microsoft, çeşitli güvenlik özellikleri Microsoft 365 sağlar ve güvenlik özellikleri için veri ve ağ güvenliğini sağlamaya yardımcı olacak en iyi güvenlik uygulamalarının kullanımına yönelik, gerekli Microsoft 365. Önerilen en iyi yöntemler şunlardır:
  
- **Çok faktörlü kimlik doğrulamasını (MFA) kullanma** MFA, kullanıcıların parolalarını doğru girdikten sonra akıllı telefonlarında bir telefon aramasını, kısa mesajı veya uygulama bildirimini kabul aramasını, kısa mesajı veya uygulama bildirimini kabul aramasını gerekli bulundurarak, güçlü bir parola stratejisine ek bir koruma katmanı ekler.

- **Bulut Uygulamaları için Microsoft Defender'ı kullanma** İlkeleri anormal etkinlikleri izlemek ve buna göre hareket etmek için yapılandırma. Yöneticilerin büyük miktarda veri indirme, birden çok başarısız oturum açma denemesi veya bilinmeyen veya tehlikeli IP adreslerinden gelen bağlantılar gibi olağan dışı veya riskli kullanıcı etkinliklerini gözden geçiremelerini için Bulut Uygulamaları için Microsoft Defender ile uyarılar ayarlayın.

- **Veri Kaybı Önleme (DLP) Yapılandırma** DLP, hassas verileri tanımlamanıza ve kullanıcılarınızı yanlışlıkla veya bilerek paylaşmasını önlemeye yardımcı olacak ilkeler oluşturmanıza olanak sağlar. DLP, Microsoft 365, Exchange Online SharePoint Online ve OneDrive de dahil olmak üzere tüm iş akışlarında çalışır ve kullanıcılarınızı iş akışlarını kesintiye uğratmadan uyumlu kalabilirsiniz.

- **Müşteri Kilidi'ne kullan** Bir Microsoft 365 yöneticisi olarak, müşteri kilidi'ni kullanarak bir Microsoft destek mühendisinin yardım oturumu sırasında verilerinize nasıl erişirlerini kontrol edebilirsiniz. Mühendisin bir sorunu gidermek ve düzeltmek için verilerinize erişmesi gereken durumlarda, Müşteri Kilit Kutusu erişim isteğini onaylamanıza veya reddetmenize izin verir.

- **Güvenli Office 365 Puanı'nı kullanın** Riski daha fazla azaltmak için neler neler yapnizi öneren bir güvenlik analizi aracı. Güvenli Puan, Microsoft 365 ayarlarınıza ve etkinliklerinize bakarak Microsoft'un kurduğu bir taban çizgisiyle karşılaştırıldığında. En iyi güvenlik uygulamaları ile ne hizalı olduğunu temel alarak bir puan elde edin.

Gelişmiş güvenlik için holist bir yaklaşım, aşağıdakileri dikkate almalıdır:
  
- Bulut tabanlı uygulama ve istemci güvenlik özelliklerini kullanarak çevre güvenliğinden uç nokta güvenliği Office vurgulu olun.
  - Veri merkezi için güvenlik çevresini küçültme
  - Ofis içindeki veya uzak konumlar içindeki kullanıcı cihazları için eşdeğer güveni etkinleştirme
  - Veri konumunun ve kullanıcının konumunun güvenliğini sağlamaya odaklanma
  - Yönetilen kullanıcı makinelerini uç nokta güvenliğine yüksek güven vardır
- Yalnızca çevreye odaklanmak yerine tüm bilgi güvenliğini holistik olarak yönetme
  - Güvenilir trafiğin güvenlik cihazlarını atlayarak ve unmanaged cihazları konuk ağlarına ayırmasına izin vererek WAN'ı yeniden tanımlayarak ve çevre Wi-Fi oluşturun
  - Kurumsal WAN kenarının ağ güvenlik gereksinimlerini azaltma
  - Güvenlik duvarları gibi bazı ağ çevre güvenlik cihazlarının hala gerekli olması gerekir, ancak yük azaltıldı
  - Yerel trafiğin yerel Microsoft 365 sağlar
- Artımlı iyileştirme bölümünde açıklandığı gibi artımlı olarak [iyileştirmeler ele alınabilirsiniz](microsoft-365-network-connectivity-principles.md#BKMK_IncOpt) . Bazı iyileştirme teknikleri ağ mimarinize bağlı olarak daha iyi maliyet/avantaj oranları sunabiliyor ve organizasyonunız için en anlamlı iyileştirmeleri seçiyorsanız.

Güvenlik ve uyumluluğu Microsoft 365 daha fazla bilgi için güvenlik [ve uyumluluk Microsoft 365 makalelerine](../security/index.yml) [Microsoft 365 bakın](../compliance/index.yml).
  
## <a name="incremental-optimization"></a>Artımlı iyileştirme
<a name="BKMK_IncOpt"> </a>

Bu makalenin önceki sayfalarında SaaS için ideal ağ bağlantı modelini temsil ettiyiz, ancak geçmiş karmaşık ağ mimarileri olan birçok büyük kuruluşta, bu değişikliklerin hepsini doğrudan yapmak pratik olmaz. Bu bölümde, performans ve güvenilirliği artırmaya yardımcı olacak bir dizi artımlı Microsoft 365 tartışacağız.
  
Veri trafiğini iyileştirmek için Microsoft 365 yöntemler, ağ topolojinize ve uygulaymış olduğunuz ağ cihazlarına bağlı olarak değişir. Birçok konumu olan ve karmaşık ağ güvenlik uygulamaları olan büyük kuruluşların, [Microsoft 365](microsoft-365-network-connectivity-principles.md#BKMK_Principles) bağlantı ilkeleri bölümünde listelenen ilkelerin çoğunu veya hepsini içeren bir strateji geliştirmeleri gerekirken, küçük kuruluşların da yalnızca bir veya ikiyi dikkate a saymaları gerekir.
  
İyileştirmeyi artımlı bir işlem olarak yaklaşımarak, her yöntemi artarak uygulayarak anabilirsiniz. Aşağıdaki tabloda, en çok sayıda kullanıcının gecikme süresi ve güvenilirliği üzerindeki etkisine göre önemli iyileştirme yöntemleri listelemektedir.
  
|**İyileştirme yöntemi**|**Açıklama**|**Etki**|
|:-----|:-----|:-----|
|Yerel DNS çözümleme ve İnternet çıkış  <br/> |Her konumda yerel DNS sunucularını sağlama ve Microsoft 365 konumuyla mümkün olan en yakın İnternet bağlantılarına erişim sağlama.  <br/> | Gecikme süresini en aza indirme  <br/>  En yakın girdi noktasına güvenilir Microsoft 365 geliştirin  <br/> |
|Bölgesel çıkış noktaları ekleme  <br/> |Kurumsal ağda birden çok konum ama tek bir çıkış noktası varsa, kullanıcıların en yakın konum veya giriş noktasına bağlanmalarını sağlamak için bölgesel Microsoft 365 ekleyin.  <br/> | Gecikme süresini en aza indirme  <br/>  En yakın girdi noktasına güvenilir Microsoft 365 geliştirin  <br/> |
|Aracıları ve denetleme cihazlarını atlama  <br/> |Doğrudan çıkış noktalarına kullanıcı isteği Microsoft 365 PAC dosyalarıyla tarayıcıları yapılandırabilirsiniz.  <br/> Uç yönlendiricileri ve güvenlik duvarlarını yapılandırarak trafiğin Microsoft 365 izin ver.  <br/> | Gecikme süresini en aza indirme  <br/>  Ağ cihazları üzerindeki yükü azaltma  <br/> |
|VPN kullanıcıları için doğrudan bağlantıyı etkinleştirme  <br/> |VPN kullanıcıları için, Microsoft 365 bölme uygulayarak VPN yolu üzerinden değil doğrudan kullanıcının ağına bağlanmak için bu bağlantı bağlantılarını etkinleştirin.  <br/> | Gecikme süresini en aza indirme  <br/>  En yakın girdi noktasına güvenilir Microsoft 365 geliştirin  <br/> |
|Geleneksel WAN'dan SD-WAN'a geçiş  <br/> |SD-WANs (Yazılım Tanımlı Geniş Alan Ağları), sanal makineler (VM) kullanan bilişim kaynaklarının sanallaştırma gibi geleneksel WAN yönlendiricilerini sanal cihazlarla değiştirerek WAN yönetimini basitleştirir ve performansı artırır.  <br/> | WAN trafiğinin performansını ve yönetilebilirliğini geliştirme  <br/>  Ağ cihazları üzerindeki yükü azaltma  <br/> |

## <a name="related-topics"></a>İlgili konular

[Microsoft 365 Bağlantısına Genel Bakış](microsoft-365-networking-overview.md)

[Kullanıcı Office 365 yönetme](managing-office-365-endpoints.md)

[Office 365 URL'leri ve IP adresi aralıkları](urls-and-ip-address-ranges.md)

[Office 365 IP Adresi ve URL Web hizmeti](microsoft-365-ip-web-service.md)

[Ağ Microsoft 365 değerlendirme](assessing-network-connectivity.md)

[Ağ planlaması ve performans ayarı Microsoft 365](network-planning-and-performance.md)

[Office 365 ve performans geçmişini kullanarak performans ayarlamayı ayarlama](performance-tuning-using-baselines-and-history.md)

[Destek için performans sorunlarını giderme Office 365](performance-troubleshooting-plan.md)

[İçerik Teslim Ağları](content-delivery-networks.md)

[Microsoft 365 bağlantı testi](https://aka.ms/netonboard)

[Microsoft hızlı ve güvenilir küresel ağına nasıl sahip olur?](https://azure.microsoft.com/blog/how-microsoft-builds-its-fast-and-reliable-global-network/)

[Office 365 Ağı blogu](https://techcommunity.microsoft.com/t5/Office-365-Networking/bd-p/Office365Networking)
