---
title: Adım 2. Kurumsal kiracılar için Microsoft 365 ağınız için en iyi ağ
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
- m365solution-tenantmanagement
- tenant-management
- m365solution-scenario
ms.custom:
- Ent_Solutions
description: Kiracınıza ağ erişimini en Microsoft 365.
ms.openlocfilehash: 2ee0f5cd784112909cbba465b94031ac2429963f
ms.sourcegitcommit: 22cae7ec541268d519d45518c32f22bf5811aec1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/10/2022
ms.locfileid: "63011787"
---
# <a name="step-2-optimal-networking-for-your-microsoft-365-for-enterprise-tenants"></a>Adım 2. Kurumsal kiracılar için Microsoft 365 ağınız için en iyi ağ

Microsoft 365 uygulamaları, Teams ve Exchange Online gibi bulut üretkenlik uygulamalarının yanı sıra birçok Microsoft Intune kimlik ve güvenlik hizmetlerini de Microsoft Azure. Bu bulut tabanlı hizmetlerin hepsi, şirket içi ağ veya İnternet'in herhangi bir yerindeki istemci cihazlarından gelen bağlantıların güvenliğine, performansına ve güvenilirliğine güvenir. 

Kiracınız için ağ erişimini en iyi duruma getirmek için şunları gerekir:

- Şirket içi kullanıcılarınız ve Microsoft Genel Ağı'nın en yakın konumu arasındaki yolu en iyi duruma getirme.
- Uzaktan erişim VPN çözümü kullanan uzak kullanıcılarınız için Microsoft Genel Ağa erişimi en iyi duruma getirme.
- Ofis Analizler ağ çevresini tasarlamak için Ağ Ağı iletişimini kullanın.
- Sitelerde barındırılan belirli varlıklara erişimi SharePoint en iyi duruma Office 365 CDN.
- Proxy ve ağ uç cihazları, uç Microsoft 365 listesiyle güvenli trafiğin işleniyorlarını atlayan ve değişiklikler yapılırken listenin güncelleştiril sürecini otomatik hale edecek şekilde yapılandırın.

## <a name="enterprise-on-premises-workers"></a>Enterprise çalışanları

Kurumsal ağlarda, istemciler ve en yakın ağ uç noktaları arasında en yüksek performans gösteren ağ erişimini etkinleştirerek son kullanıcı Microsoft 365 en iyi duruma getirmelisiniz. Son kullanıcı deneyiminin kalitesi, doğrudan kullanıcının kullanmakta olduğu uygulamanın performansı ve yanıt süresiyle ilgilidir. Örneğin, Microsoft Teams görüşmeleri, konferansları ve paylaşılan ekran işbirliğinin hatasız olması için düşük gecikme süresine dayandırılır.

Ağ tasarımında temel amaç, istemci cihazlarından Microsoft Global Network'e gidiş dönüş süresini (RTT) azaltarak gecikmeyi en aza indirmek ve Microsoft'un tüm veri merkezleriyle düşük gecikme süresi, ön kapı olarak bilinen yüksek kullanılabilir bulut uygulaması giriş noktalarıyla bağlantılı olan genel ağ omurgasını dünyanın her yerine yaslamalı olmalıdır.

Geleneksel kurumsal ağın bir örneği şu şekildedir.

![İnternet'e merkezi erişime sahip geleneksel bir kurumsal ağ.](../media/tenant-management-overview/tenant-management-networking-traditional.png)

Bu çizimde, şubeler geniş alan ağı (WAN) cihazları ve WAN omurgasını kullanarak merkezi bir ofislere bağlanmektedir. İnternet erişimi, merkezi ofisin ağ kenarında bulunan bir güvenlik veya ara sunucu cihazı ve İnternet servis sağlayıcısı (ISS) üzerindendir. İnternet üzerinden, Microsoft Global Network'te dünyanın her bölgesinde bir dizi ön kapı vardır. Kuruluşlar ara konumları, ek paket işleme ve trafik güvenliği için de kullanabilir. Bir kuruluşun kiracısı Microsoft 365 Microsoft Genel Ağı'nın içinde yer alıyor.

Bulut hizmetleri için bu yapılandırmada Microsoft 365 sorunlar:

- Şubelerde bulunan kullanıcılar için trafik, yerel olmayan ön kapılara gönderilir ve bu da gecikme süresini artırıyor.
- Trafiğin ara konumlara gönderilmesi, güvenilir trafikte yinelenen paket işlemesi gerçekleştirerek gecikmeyi artıran ağ A-T'leri oluşturabilir.
- Ağ uç cihazları güvenilen trafikte gerekli olmayan ve yinelenen paket işlemesi gerçekleştirerek gecikmeyi artırıyor.

Ağ Microsoft 365 iyileştirmenin karmaşık olması gerek değildir. Birkaç temel ilkeyi kullanarak mümkün olan en iyi performansı elde etmek için:

- Microsoft Microsoft 365 hizmetlerini hedef alan güvenilen ağ trafiğini tanımlama.
- Kullanıcıların ağ trafiğinin, kullanıcıların Microsoft 365 her konumdan İnternet'e yerel dalı çıkışlarına izin Microsoft 365.
- Ağ Ağın Ası'larından kaçının.
- Geçiş Microsoft 365, aracıları ve paket denetleme cihazlarını atlar.

Bu ilkeleri uygulamaya devam ediyorsanız, iş ağınız için iyileştirilmiş bir Microsoft 365.

![İşletmeler için iyileştirilmiş kurumsal Microsoft 365.](../media/tenant-management-overview/tenant-management-networking-optimized.png)

Bu çizimde, şubelerin yazılım tanımlı bir WAN cihazı (SDWAN) cihazı üzerinden kendi İnternet bağlantıları vardır ve bu ofisler güvenilen iş Microsoft 365 yakın ön kapıya güvenilir bir trafik gönderir. Merkezi ofiste, güvenilen Microsoft 365 güvenlik veya ara cihaz ve ara cihazlar artık kullanılmamaktadır.

En iyi duruma getirilmiş yapılandırma, geleneksel bir kurumsal ağın gecikme sorunlarını şöyle çözer:

- Güvenilen Microsoft 365 WAN omurgasını atlar ve gecikme süresini azaltarak tüm ofislerin yerel ön kapılarına gönderilir.
- Yinelenen paket işlemesi gerçekleştirmekte olan ağ geri yüklemeleri güvenilen Microsoft 365 için atlanır ve gecikme süresi kısalır.
- Gerekli olmayan ve yinelenen paket işlemesi gerçekleştiren ağ uç cihazları güvenilen trafikte Microsoft 365 azaltarak atlanır.

Daha fazla bilgi için bkz. [Microsoft 365 bağlantısına genel bakış](../enterprise/microsoft-365-networking-overview.md).

## <a name="remote-workers"></a>Uzaktan çalışanlar

Uzaktan çalışanlarınız kuruluş ağınıza uzaktan erişim elde etmek için geleneksel bir VPN istemcisi kullanıyorsa VPN istemcisinin bölünmüş şifreleme desteğine sahip olduğunu doğrulayın. Bölünmüş bölme olmadan, uzaktan iş trafiğinizin hepsi VPN bağlantısı üzerinden gönderilir, bu trafik kuruluşun uç cihazlarına ilet olmalı, işlenmeli ve İnternet'e gönderilir. İşte bir örnek.

![VPN istemcilerinden gelen ağ trafiğine hiçbir şey olunmaz.](../media/empower-people-to-work-remotely-remote-access/empower-people-to-work-remotely-remote-access-before-tunneling.png)

Bu çizimde Microsoft 365 trafiğin, VPN istemcisinin fiziksel konumunun çok dışında bir Microsoft Global Network ön kapıya yönlendirilen dolaylı bir yol olması gerekir. Bu dolaylı yol ağ trafiğine gecikme ekler ve genel performansı düşürer. 

Bölünmüş bölmeyle, VPN istemcinizi kuruluş ağına VPN bağlantısı üzerinden gönderilen trafiğin belirli türlerini dışarıda bırakacak şekilde yapılandırabilirsiniz.

Bulut kaynaklarına erişimi Microsoft 365 için bölünmüş VPN istemcilerinizi yapılandırarak trafiği VPN bağlantısı üzerinden en iyi duruma Microsoft 365 uç noktalarını iyileştirmek için  kullanın. Daha fazla bilgi için bkz[. Office 365 uç noktası](../enterprise/microsoft-365-network-connectivity-principles.md#new-office-365-endpoint-categories) kategorilerini [yapılandırma ve](../enterprise/microsoft-365-vpn-implement-split-tunnel.md#implement-vpn-split-tunneling) Bölünmüş geçiş için kategori uç noktalarını en iyi duruma getirme listeleri.

Bölünmüş olay için sonuçta ortaya çıkan trafik akışı yer alsa da bulut uygulamalarının trafiğin büyük bir Microsoft 365 VPN bağlantısını atlar.

![VPN istemcilerinden gelen ağ trafiği ve tarak.](../media/empower-people-to-work-remotely-remote-access/empower-people-to-work-remotely-remote-access-after-tunneling.png)

Bu çizimde, VPN istemcisi doğrudan İnternet üzerinden Microsoft 365 Microsoft Genel Ağı'nın en yakın ön kapısını gönderir ve önemli bir bulut hizmeti trafiği alır.

Daha fazla bilgi ve rehberlik için bkz. [VPN bölünmüş Office 365 kullanan uzak kullanıcılar için en iyi duruma getirme](../enterprise/microsoft-365-vpn-split-tunnel.md).

## <a name="using-network-insights-preview"></a>Ağ bağlantı Analizler (önizleme) kullanma

Ağ içgörüleri, ofis konumlarınızı Microsoft 365 ağ çevrelerini tasarlamanıza yardımcı olacak şekilde kiracınız tarafından toplanan performans ölçümleridir. Her içgörü, şirket içi kullanıcıların kiracınıza eriştiği her coğrafi konum için belirli bir soruna ilişkin performans özellikleri hakkında canlı ayrıntılar sağlar.

Kiracı için iki kiracı düzeyinde ağ içgörüleri gösterebilirsiniz:

- [Exchange sorundan etkilenen örnek bağlantılar](../enterprise/office-365-network-mac-perf-insights.md#exchange-sampled-connections-affected-by-connectivity-issues)
- [SharePoint sorundan etkilenen örnek bağlantıların sayısı](../enterprise/office-365-network-mac-perf-insights.md#sharepoint-sampled-connections-affected-by-connectivity-issues)

Her ofis konumu için belirli ağ içgörüleri bunlardır:

- [Geri dönülen ağ çıkış](../enterprise/office-365-network-mac-perf-insights.md#backhauled-network-egress)
- [Yakın gelecekte bulunan müşteriler için daha iyi performans algılandı](../enterprise/office-365-network-mac-perf-insights.md#better-performance-detected-for-customers-near-you)
- [En iyi olmayan ön Exchange Online kapı kullanımı](../enterprise/office-365-network-mac-perf-insights.md#use-of-a-non-optimal-exchange-online-service-front-door)
- [En iyi olmayan çevrimiçi hizmet SharePoint ön kapı kullanımı](../enterprise/office-365-network-mac-perf-insights.md#use-of-a-non-optimal-sharepoint-online-service-front-door)
- [Ön kapılardan düşük SharePoint indirme hızı](../enterprise/office-365-network-mac-perf-insights.md#low-download-speed-from-sharepoint-front-door)
- [Çin kullanıcısı en iyi ağ çıkış](../enterprise/office-365-network-mac-perf-insights.md#china-user-optimal-network-egress)

> [!IMPORTANT]
> Ağ içgörüleri, performans önerileri ve değerlendirmeleri Microsoft 365 Yönetici şu anda önizleme durumundadır. Yalnızca özellik Microsoft 365 programda kayıtlı olan tüm kiracılar tarafından kullanılabilir.

Daha fazla bilgi için bkz. [Microsoft 365 Ağ Analizler](../enterprise/office-365-network-mac-perf-insights.md).

## <a name="sharepoint-performance-with-the-office-365-cdn"></a>SharePoint performansı Office 365 CDN

Bulut tabanlı bir Content Delivery Network (CDN) yükleme sürelerini azaltmaya, bant genişliğini kaydetmeye ve hızlı yanıt hızına olanak sağlar. Bir CDN, onlardan talep eden tarayıcılara daha yakın olan grafik veya video dosyaları gibi statik varlıkları önbelleğe alma işleminin performansını artırır ve bu da indirmeleri hızlandırmak ve gecikmeyi azaltmaya yardımcı olur. Microsoft 365 E3 ve E5'te SharePoint'e dahil olan yerleşik Office 365 Content Delivery Network (CDN) varlıklarını kullanarak, statik varlıkları ana bilgisayar sayfalarınıza daha iyi bir performans SharePoint sabilirsiniz.

Kaynak Office 365 CDN birden çok konumda veya kaynakta statik varlıkları barındırmana ve bunları genel yüksek hızlı ağlardan hizmet vermesine olanak sağlayan birden çok CDN'den oluşur. Kaynak 2013'te barındırmak istediğiniz içeriğin türüne bağlı olarak, Office 365 CDN veya **her ikisini birden** ebilirsiniz.

İnternet'Office 365 CDN ve özel kaynaklarda yer alan varlıklar, dağıtıldığında ve yapılandırıldığında karşıya yükler ve İnternet'Office 365 CDN kullanıcılara hızlı erişim için kullanılabilir.

![Office 365 CDN dağıtılan uygulama.](../media/O365-CDN/o365-cdn-flow-transparent.svg "Office 365 CDN için dağıtılan uygulama")

Daha fazla bilgi için bkz[. Office 365 CDN Online ile SharePoint kullanma](../enterprise/use-microsoft-365-cdn-with-spo.md).

## <a name="automated-endpoint-listing"></a>Otomatik uç nokta listesi

Şirket içi istemcilerinizi, uç cihazlarınızı ve bulut tabanlı paket çözümleme hizmetlerinizin güvenilen Microsoft 365 trafiğini işlemeyi atlasını sağlamak için, bunları Microsoft 365 hizmetlerinize karşılık gelen uç noktalar kümesiyle (IP adresi aralıkları ve DNS adları) yapılandırmanız gerekir. Bu uç noktalar güvenlik duvarlarında ve diğer uç güvenlik cihazlarında el ile yaslanır, istemci bilgisayarların istemci bilgisayarlarına yönelik PAC dosyaları ya da şubelerde yer alan SD-WAN cihazları atlanır. Bununla birlikte, uç noktalar zaman içinde değişir ve bu konumlarda uç nokta listelerinin sürekli el ile bakımını gerektirir.

İstemci PAC dosyalarınız ve ağ cihazlarınız Microsoft 365 uç noktalarında liste işlemini otomatikleştirmek ve değişiklik yönetimini otomatikleştirmek için, Office 365 IP Adresi ve [URL REST tabanlı web hizmetini kullanın](../enterprise/microsoft-365-ip-web-service.md). Bu hizmet ağ trafiğini daha iyi tanımlamanıza Microsoft 365 ayırmanıza yardımcı olur ve en son değişiklikleri değerlendirmeniz, yapılandırmanız ve güncel kalmanızı kolaylaştırır.

Zaman içinde uç noktalara yapılan değişiklikleri belirlemek ve PAC dosyalarınızı ve kenar ağ cihazlarınızı yapılandırmak için PowerShell, Python veya diğer dilleri kullanabilirsiniz.

Temel süreç şöyledir:

1. PAC Office 365 ağ cihazlarınızı geçerli MICROSOFT 365 uç noktaları kümesiyle yapılandırmak için tercihinizin yapılandırma ip adresi ve URL web hizmetini ve yapılandırma Microsoft 365 kullanın.
2. Uç noktaların değişikliklerini kontrol etmek veya bildirim yöntemini kullanmak için günlük yinelenen bir çalışma yapın.
3. Değişiklikler algılandığında, istemci bilgisayarlar için PAC dosyasını yeniden oluşturma ve yeniden dağıtarak ağ cihazlarınıza değişiklikleri yapın.

Daha fazla bilgi için BKZ[. IP Office 365 URL web hizmetini yapılandırma](../enterprise/microsoft-365-ip-web-service.md).

## <a name="results-of-step-2"></a>Adım 2'nin sonuçları

En Microsoft 365 ağı olan kiracınız için, şunları belirlediniz:

- Tüm şubelere İnternet bağlantıları ekleyerek ve ağ A-A'larını ortadan kaldırarak şirket içi kullanıcıların ağ performansını iyileştirme.
- İstemci tabanlı PAC dosyalarınız, ağ cihazlarınız ve hizmetleriniz için, devam eden güncelleştirmeler de dahil olmak üzere (en uygun kurumsal ağlar için) otomatik güvenilen uç nokta listesini nasıl uygulayabilirsiniz?
- Uzak çalışanların şirket içi kaynaklara erişimini destekleme.
- Ağ Bağlantıları nasıl Analizler
- Dağıtımın nasıl Office 365 CDN.

Burada, en iyi ağ iletişimi olan bir kurumsal kuruluş ve onun kiracısı örneği ve ve bir örneği yer alan.

![En uygun ağ için bir kiracı örneği.](../media/tenant-management-overview/tenant-management-tenant-build-step2.png)

[Bu resmin daha büyük bir sürümüne bakın](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/media/tenant-management-overview/tenant-management-tenant-build-step2.png)

Bu çizimde, bu kurumsal kuruluşun kiracısına aşağıdakiler gösterilmiştir:

- Güvenilir postane trafiğini yerel bir ön kapıya ileten SDWAN Microsoft 365 her şube için yerel İnternet erişimi.
- Ağ Apin'i yok.
- Güvendiği trafiği yerel bir ön Microsoft 365 ileten merkezi ofis güvenliği ve ara sunucu uç cihazları.

## <a name="ongoing-maintenance-for-optimal-networking"></a>En iyi ağ için sürekli bakım

Sürekli olarak şunları yapmak zorundayabilirsiniz:

- Uç noktalarda değişiklikler için uç cihazlarınızı güncelleştirin ve PAC dosyalarını dağıtın veya otomatik işleminizin düzgün çalıştığını doğrulayın.
- Varlıklarınızı diğer Office 365 CDN.
- Uç noktalarda yapılan değişiklikler için VPN istemcilerinizin bölünmüş bölme yapılandırmasını güncelleştirin.

## <a name="next-step"></a>Sonraki adım

[![3. Adım. Kimliklerinizi eşitler ve güvenli oturum açmaları zorlar.](../media/tenant-management-overview/tenant-management-step-grid-identity.png)](tenant-management-identity.md)

Şirket içi [hesaplarınızı](tenant-management-identity.md) ve gruplarınızı eşitlemek ve güvenli kullanıcı oturum açmalarını zorlamak için kimlikle devam.
