---
title: Microsoft 365 kullanıcıları için genel kiracı performansını iyileştirme
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 3/3/2022
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- remotework
search.appverid: MET150
f1.keywords:
- NOCSH
description: Bu makalede, çin'deki genel kullanıcı ve kiracılar için ağ performansını iyileştirmeye Microsoft 365 kılavuzlar yer almaktadır.
ms.openlocfilehash: 6c99245d523048d30124fc8f8b0c01d7c2004327
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63326937"
---
# <a name="microsoft-365-global-tenant-performance-optimization-for-china-users"></a>Microsoft 365 kullanıcıları için genel kiracı performansını iyileştirme

> [!IMPORTANT]
> Bu kılavuz, Çin'de bulunan kurumsal **Microsoft 365** kullanıcıların genel bir kiracıya bağlı olduğu **kullanım Microsoft 365 yöneliktir**. Bu **kılavuz,** 21Vianet tarafından Office 365 kiracılar için geçerli değildir.

>[!NOTE]
>Bu makale, uzak kullanıcılar için iyileştirmeyi Microsoft 365 makale kümelerinin bir bölümüdir.

>- Uzak kullanıcılar için Microsoft 365 bağlantısını en iyi duruma getirmek için VPN bölünmüş şifreleme kullanma hakkında genel bir bakış için bkz[.](microsoft-365-vpn-split-tunnel.md) Genel Bakış: Vpn bölünmüş Microsoft 365.
>- VPN bölünmüş bölmeyi uygulama hakkında ayrıntılı kılavuz için bkz. [VPN bölünmüş bölmeyi uygulama Microsoft 365](microsoft-365-vpn-implement-split-tunnel.md).
>- VPN bölünmüş bölme senaryolarının ayrıntılı listesi için bkz. Daha fazla bilgi için bkz. Genel [VPN bölünmüş Microsoft 365](microsoft-365-vpn-common-scenarios.md).
>- VPN bölünmüş trafiğinde Teams trafiğinin güvenliğini sağlama kılavuzu için bkz. VPN bölünmüş trafiği için Teams trafiğinin güvenliğini [sağlama](microsoft-365-vpn-securing-teams.md).
>- VPN ortamlarında Stream ve canlı etkinlikleri yapılandırma hakkında bilgi için bkz. VPN ortamlarında akış ve canlı etkinlikler [için dikkat edilmesi gereken noktalar](microsoft-365-vpn-stream-and-live-events.md).

Global kurumsal kiracıları olan Microsoft 365 Çin'de kurumsal varlığı olan kuruluşlar için, Microsoft 365 tabanlı kullanıcılar için istemci performansı, Çin Telco'nun İnternet mimarisine özgü faktörler tarafından karmaşık olabilir.

Çin ISS'ler, yüksek sınır ötesi ağ tıkanıklığı düzeyine açık çevre cihazlardan geçen genel genel İnternet bağlantılarını düzenlemeye sahiptir. Bu tıkanıklık, Çin'e giden ve dışarı giden tüm İnternet trafiği için paket kaybı ve gecikme süresi oluşturur.

![Microsoft 365 - göz korkutucu değil.](../media/O365-networking/China-O365-unoptimized.png)

Paket kaybı ve gecikme süresi, ağ hizmetlerinin performansına, özellikle de büyük veri değişimleri gerektiren (büyük dosya aktarımları gibi) veya yakın gerçek zamanlı performans (ses ve video uygulamaları) gerektiren hizmetlere zararlıdır.

Bu konunun amacı, Çin'de çapraz sınır ağ tıkanıklığı üzerindeki etkiyi azaltmaya yönelik en iyi Microsoft 365 sağlamaktır. Bu konu, Çin taşıyıcıları içindeki karmaşık yönlendirme nedeniyle yüksek paket gecikme süresi sorunları gibi sık karşılaşılan son mesafe performans sorunlarına çözüm aramaz.

## <a name="corporate-network-best-practices"></a>Kurumsal ağ için en iyi yöntemler

Çin'de küresel Microsoft 365 kiracıları ve kullanıcıları olan birçok kuruluş, Çin'deki ofis konumları ile dünyanın her yanında yer alan okul konumları arasında şirket ağı trafiği taşıyan özel ağlar uygulamaya başladı. Bu kuruluşlar, çapraz ağ tıkanıklıklarından kaçınmak ve Çin'deki ağ hizmet Microsoft 365 en iyi duruma getirmek için bu ağ altyapısından faydalanebilir.

> [!IMPORTANT]
> Tüm özel WAN uygulamaları gibi, ağ yapılandırmanın uyumlu olduğundan emin olmak için ülkeniz ve/veya bölgeniz için her zaman mevzuat gereksinimlerine bakabilirsiniz.

İlk adım olarak, karşılaştırma ağı kılavuzumızı takip etmek, karşılaştırma ağı için ağ planlaması [ve](./network-planning-and-performance.md) performans ayarı konusunda yol gösterici Microsoft 365. Birinci hedef, mümkünse Çin'de İnternet'Microsoft 365 gelen genel posta hizmetlerine erişimi önlemektir.

- Çin ofis ağları ve çin dışındaki genel İnternet Microsoft 365 ağ trafiğini taşımak için mevcut özel ağdan faydalanabilirsiniz. Çin'in dışındaki neredeyse tüm konumlar net bir avantaj sağlayacaktır. Ağ yöneticileri, Microsoft genel ağıyla düşük gecikme süresi bağlantılı olan alanlarda çıkışarak daha [da iyi hale gelir](/azure/networking/microsoft-global-network). Hong Kong, Singapur, Japonya ve Güney Kore örnek olarak verilmiştir.
- Kullanıcıların şirket ağına VPN bağlantısı üzerinden erişmek üzere kullanıcı cihazlarını yapılandırarak, Microsoft 365 ağın özel bağlantısının aktar olmasına izin verir. VPN istemcilerinin bölünmüş bölmeyi kullanmak üzere yapılandırılmamış olduğundan veya kullanıcı cihazlarının bölünmüş trafiğin bölünmüş olaylarını yok saymak üzere yapılandırıldığından Microsoft 365 olun. GERÇEK ZAMANLı medya trafiği için VPN bağlantısını Teams hakkında ek bilgi için bu [bölüme bakın](#optimizing-microsoft-teams-meetings-network-performance-for-users-in-china).
- Tüm trafiği özel Microsoft 365 bağlantınıza yönlendiracak şekilde anızı yapılandırabilirsiniz. Özel bağlantınız üzerindeki trafik hacmini en aza indirmeniz gerekirse, uç noktaları yalnızca En İyi Duruma Getirme kategorisinde yönlendirmeyi ve isteklerin İnternet'i aktarmasına  İzin Ver  ve Varsayılan uç noktalarına izin vermeyi seçebilirsiniz. Bu, iyileştirilmiş trafiği yüksek gecikme süresi ve paket kaybına karşı en duyarlı kritik hizmetlerle sınırlandırarak performansı iyiler ve bant genişliği tüketimini en aza indirecektir.
- Mümkünse, canlı medya akışı trafiği için TCP yerine UDP kullanın; örneğin, Teams. UDP, TCP'ye göre daha iyi canlı medya akışı performansı sunar.

Trafiği seçmeli olarak yönlendirme hakkında bilgi Microsoft 365 için bkz[. Office 365 yönetme](managing-office-365-endpoints.md). Tüm dünya çapında 2013 URL'leri Office 365 IP adreslerinin listesi için bkz. Office 365 [VE IP adresi aralıkları](urls-and-ip-address-ranges.md).

![Microsoft 365 - iyileştirilmiş.](../media/O365-networking/China-O365-optimized.png)

## <a name="user-best-practices"></a>Kullanıcı için en iyi yöntemler

Çin'de ev, kafe mağazaları, oteller ve ofisler gibi uzak konumlardan küresel Microsoft 365 kiracılarına bağlanan ve kurumsal ağlara bağlantısı olmayan kullanıcılar, cihazları ve Microsoft 365 arasındaki trafiğin Çin'in tıkanık çapraz ağ bağlantı hatlarını aktarması nedeniyle düşük ağ performansıyla yaşanıyor.

Şirket ağına sınır ötesi özel ağlar ve/veya VPN erişimi bir seçenek yoksa, Çin tabanlı kullanıcılarınızı bu en iyi yöntemleri izlemeleri için eğitimle kullanıcı başına performans sorunlarının azaltılmasına devam eder.

- Önbelleğe almayı Office zengin veri istemcilerini kullanın (örneğin, Outlook, Teams, OneDrive, vb.) ve web tabanlı istemcilerden kaçının. Office önbelleğe alma ve çevrimdışı erişim özellikleri ağ tıkanıklığı ve gecikme süresinin etkisini önemli ölçüde azaltır.
- Kullanıcı Microsoft 365 Sesli Konferans özelliğiyle yapılandırılmışsa, Teams kullanıcılar ortak anahtarlı telefon ağı (PSTN) üzerinden toplantılara katılabilir. Daha fazla bilgi için bkz. [Office 365](/microsoftteams/audio-conferencing-in-office-365).
- Kullanıcılar ağ performansı sorunlarıyla yaşanıyorsa, sorun giderme için KENDI IT departmanlarına bildirmeleri ve Microsoft 365 hizmetleriyle ilgili sorun olması Microsoft 365 Microsoft desteğine yükseltmeleri gerekir. Tüm sorunlar kenarlıklar arası ağ performansından kaynaklanmaz.

## <a name="optimizing-microsoft-teams-meetings-network-performance-for-users-in-china"></a>Çin'Microsoft Teams kullanıcılar için toplantı ağ performansını iyileştirme

Genel posta kiracıları olan Microsoft 365 Çin'de iletişim durumu olan kuruluşlar için, Microsoft 365 tabanlı kullanıcılar için istemci performansının karmaşık olması, Çin İnternet mimarisine özgü faktörler tarafından karmaşık olabilir. Birçok şirket ve okul bu kılavuza uygun sonuçlar bildirdi. Ancak bu kapsam, VPN bağlantısı olan ofis konumları veya ev/mobil uç noktaları gibi, IT ağı kurulumunun denetimi altındaki kullanıcı ağı konumlarıyla sınırlıdır. Microsoft Teams aramalar ve toplantılar genellikle ev ofisleri, mobil konumlar, yolda ve kafe gibi dış konumlardan kullanılır. Aramalar ve toplantılar gerçek zamanlı medya trafiğine dayanması nedeniyle, bu Teams deneyimleri özellikle ağ tıkanıklığı konusunda hassastır.

Sonuç olarak, Microsoft Çin'deki yerel ve genel İnternet bağlantıları ile Microsoft 365 küresel bulut üzerinde yer alan Teams ve Skype hizmetleri arasında daha kaliteli, tercihen bir ağ yolu kullanarak Teams ve Skype Kurumsal Online gerçek zamanlı medya trafiği taşımak için telekomünikasyon sağlayıcılarıyla ortak çalışmalar yürütmektedir. Bu özellik, paket kaybına ve kullanıcı deneyimini etkileyen diğer önemli ölçümlere göre on kattan fazla geliştirme elde etti.

>[!IMPORTANT]
>Şu anda bu iyileştirmeler büyük yayın veya "kasaba salonu" stili toplantılar gibi Microsoft Live Events toplantılarına katılmayı ele Teams ya da Microsoft Stream'i kullanmaz. Canlı Etkinlikler toplantısını görüntülemek için Çin'deki kullanıcıların özel bir ağ veya SDWAN/VPN çözümü kullanmaları gerekir. Bununla birlikte, ağ geliştirmeleri Canlı Etkinlik toplantılarını yapan veya üreten kullanıcılara fayda sağlar, çünkü bu deneyim yapımcı veya sunucu için normal bir Teams toplantısı gibi davranır.

### <a name="organization-network-best-practices-for-teams-meetings"></a>Toplantılara yönelik kuruluş ağı Teams yöntemleri

Önceki kılavuzda, sınır ötesi ağ tıkanıklığından kaçınmak için özel bir ağ uzantısını göz önünde bulundurursa, bu ağ geliştirmelerini nasıl kullanılay? göz önünde bulundurabilirsiniz. Kuruluş office ağları için iki genel seçenek vardır:

1. Yeni bir şey yapma. Kenarlıklar arası tıkanıklığı önlemek için, özel ağ atlama çevresinde önceki yönergeleri takip etmeye devam edin. Teams gerçek zamanlı medya trafiği, daha önce olduğu gibi bu kurulumdan yararlanacak.
2. Bölünmüş/karma desen uygulama.
   - Toplantılar ve gerçek zamanlı medya trafiğini arama dışında, iyileştirme Teams tüm trafik için önceki kılavuzu kullanın.
   - Toplantı Teams ve gerçek zamanlı medya trafiğini ortak İnternet üzerinden yönlendirin. Gerçek zamanlı medya ağ trafiğini belirlemeyle ilgili bilgiler için aşağıdaki bilgilere bakın.

Yüksek Teams kullanan genel İnternet üzerinden gerçek zamanlı medya ses ve görüntü trafiği göndermek, önemli ölçüde maliyet tasarrufu sağlar çünkü bu trafik özel bir ağ üzerinden ücret ödeme yerine ücretsizdir. Kullanıcılar SDWAN veya VPN istemcileri de kullanıyorsa, benzer ek avantajlar olabilir. Bazı kuruluşlar, genel uygulama olarak daha fazla veri çapraz İnternet bağlantısına sahip olmayı da tercih ediyor olabilir.

Aynı seçenekler SDWAN veya VPN yapılandırmaları için de uygulanabilir. Örneğin, bir kullanıcı şirket ağına giden trafiği Microsoft 365 için SDWAN veya VPN kullanıyor ve sonra da sınır ötesi tıkanıklığı önlemek için bu ağın özel uzantısından yararlanarak kullanıyor. Kullanıcının SDWAN veya VPN'i artık VPN yönlendirmesi dışında Teams gerçek zamanlı trafik çağrılarını dışarıda bırakacak şekilde yalıtabilirsiniz. Bu VPN yapılandırması bölünmüş kazıma olarak adlandırılır. Daha [fazla bilgi için bkz. Office 365](/microsoft-365/enterprise/microsoft-365-vpn-implement-split-tunnel) VPN bölünmüş bölme.

Ayrıca, gerçek zamanlı trafik de dahil olmak üzere tüm dünya trafiği Microsoft 365 SDWAN veya VPN Microsoft Teams kullanabilirsiniz. Microsoft'un SDWAN veya VPN çözümlerinin kullanımıyla ilgili hiçbir önerisi yoktur.

### <a name="home-mobile-and-user-network-best-practices-for-teams-meetings"></a>Toplantılarınız için ev, mobil ve kullanıcı ağı için Teams yöntemleri

Çin'deki kullanıcılar, Çin'deki genel İnternet hizmetine sabit hat veya mobil bağlantı üzerinden bağlanarak bu geliştirmelerden faydalanabilirsiniz. Teams gerçek zamanlı medya ses ve video trafiğinin genel İnternet'te gerçek zamanlı olarak

Bununla birlikte, diğer Microsoft 365 hizmetlerinden ve Teams veya dosyalar gibi diğer trafiğin verileri bu geliştirmelerden doğrudan yararlanamaz. Kuruluş ağının dışındaki kullanıcılar da bu trafikte ağ performansı düşük olabilir. Bu makalede de ele alınarak, VPN veya SDWAN kullanarak bu etkiyi azaltmak için kullanabilirsiniz. Ayrıca, kullanıcılarının ağ sorunlarını azaltmak için uygulama içinde önbelleğe almayı destekleyen web istemcileri üzerinden zengin masaüstü istemcileri kullanmalarını da sebilirsiniz.

### <a name="identifying-teams-real-time-media-network-traffic"></a>Gerçek Teams medya ağ trafiğini tanımlama

Ağ cihazı veya VPN/SDWAN kurulumu yapılandırmak için yalnızca gerçek zamanlı medya Teams video trafiğini hariç tutabilirsiniz. Trafik ayrıntıları, kimlik 11 için URL'ler ve [IP adresi Office 365 resmi listesinde bulunabilir](urls-and-ip-address-ranges.md#skype-for-business-online-and-microsoft-teams). Diğer tüm ağ yapılandırmaları olduğu gibi kal olmalıdır.

Microsoft mümkün olan en geniş ağ mimarisi Microsoft 365 özellikleri genelinde kullanıcı deneyimini ve istemcilerin performansını geliştirmek için sürekli olarak çalışıyor. Konuşma başlatmak [Office 365 katılmak, Community kaynak bulmak Office 365](https://techcommunity.microsoft.com/t5/office-365-networking/bd-p/Office365Networking) özellik istekleri ve öneriler göndermek için Ağ Ağı Teknik Ekibi iletişim sitesini ziyaret edin

## <a name="related-articles"></a>İlgili makaleler

[Genel bakış: VPN bölme bölme Microsoft 365](microsoft-365-vpn-split-tunnel.md)

[VPN bölmeli bölme Microsoft 365](microsoft-365-vpn-implement-split-tunnel.md)

[Kullanıcılar için yaygın VPN bölme bölme Microsoft 365](microsoft-365-vpn-common-scenarios.md)

[VPN bölünmüş Teams için medya trafiğinin güvenliğini sağlama](microsoft-365-vpn-securing-teams.md)

[VPN ortamlarında Stream ve canlı etkinlikler için dikkat edilmesi gereken noktalar](microsoft-365-vpn-stream-and-live-events.md)

[Microsoft 365 Ağ Bağlantısı İlkeleri](microsoft-365-network-connectivity-principles.md)

[Ağ Microsoft 365 değerlendirme](assessing-network-connectivity.md)

[Microsoft 365 ve performans ayarını yapılandırma](network-planning-and-performance.md)

[Günümüzün benzersiz uzaktan çalışma senaryolarında güvenlik uzmanlarının ve BT'nin modern güvenlik denetimlerini elde etmenin alternatif yolları (Microsoft Güvenlik Ekibi blogu)](https://www.microsoft.com/security/blog/2020/03/26/alternative-security-professionals-it-achieve-modern-security-controls-todays-unique-remote-work-scenarios/)

[Microsoft'ta VPN performansını geliştirme: otomatik Windows 10 izin vermek için VPN profillerini kullanma](https://www.microsoft.com/itshowcase/enhancing-remote-access-in-windows-10-with-an-automatic-vpn-profile)

[VPN ile çalışma: Microsoft uzaktan iş gücüne nasıl bağlı tutarak](https://www.microsoft.com/itshowcase/blog/running-on-vpn-how-microsoft-is-keeping-its-remote-workforce-connected/?elevate-lv)

[Microsoft genel ağı](/azure/networking/microsoft-global-network)
