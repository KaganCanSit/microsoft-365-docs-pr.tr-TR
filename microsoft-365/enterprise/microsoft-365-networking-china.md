---
title: Microsoft 365 kullanıcıları için genel kiracı performansını iyileştirme
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 11/17/2020
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
description: Bu makale, çin'deki genel kullanıcı ve kiracıları kullanan Çin kullanıcılarının ağ Microsoft 365 için kılavuz sağlar.
ms.openlocfilehash: 65f80137786ea708e2ee0200e63600906fd18d24
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62973725"
---
# <a name="microsoft-365-global-tenant-performance-optimization-for-china-users"></a>Microsoft 365 kullanıcıları için genel kiracı performansını iyileştirme

> [!IMPORTANT]
> Bu kılavuz, Çin'de bulunan kurumsal **Microsoft 365** kullanıcıların genel bir kiracıya bağlı olduğu kullanım **Microsoft 365 yöneliktir**. Bu **kılavuz,** 21Vianet tarafından Office 365 kiracılar için geçerli değildir.

Global kurumsal kiracıları olan Microsoft 365 Çin'de kurumsal varlığı olan kuruluşlar için, Microsoft 365 tabanlı kullanıcılar için müşteri performansının karmaşık olması, Çin Telco'nun İnternet mimarisine özgü faktörler tarafından karmaşık olabilir.

Çin ISS'ler, yüksek sınır ötesi ağ tıkanıklığı düzeyine açık çevre cihazlardan geçen genel genel İnternet bağlantılarını düzenlemeye sahiptir. Bu tıkanıklık, Çin'e giden ve dışarı giden tüm İnternet trafiği için paket kaybı ve gecikme süresi oluşturur.

![Microsoft 365 - göz korkutucu değil.](../media/O365-networking/China-O365-unoptimized.png)

Paket kaybı ve gecikme süresi, ağ hizmetlerinin performansına, özellikle de büyük veri değişimleri gerektiren (büyük dosya aktarımları gibi) veya yakın gerçek zamanlı performans (ses ve video uygulamaları) gerektiren hizmetlere zararlıdır.

Bu konunun amacı, Çin'de çapraz sınır ağ tıkanıklığı üzerindeki etkiyi azaltmaya yönelik en iyi Microsoft 365 sağlamaktır. Bu konu, Çin taşıyıcıları içindeki karmaşık yönlendirme nedeniyle yüksek paket gecikme süresi sorunları gibi sık karşılaşılan son mesafe performans sorunlarına çözüm aramaz.

## <a name="corporate-network-best-practices"></a>Kurumsal ağ için en iyi yöntemler

Çin'de küresel Microsoft 365 kiracılarına ve kullanıcılarına sahip olan birçok kuruluş, Çin'deki ofis konumları ile dünyanın her yanında yer alan konumlar arasında şirket ağı trafiği taşıyan özel ağlar uygulamaya başladı. Bu kuruluşlar, çapraz ağ tıkanıklıklarından kaçınmak ve Çin'deki en iyi hizmet Microsoft 365 için bu ağ altyapısından faydalanebilir.

> [!IMPORTANT]
> Tüm özel WAN uygulamaları gibi, ağ yapılandırmanın uyumlu olduğundan emin olmak için ülkeniz ve/veya bölgeniz için her zaman mevzuat gereksinimlerine bakabilirsiniz.

İlk adım olarak, karşılaştırma ağı kılavuzumızı Takip etmek için ağ planlaması ve performans ayarı konusunda kılavuza [uymanız çok Microsoft 365](./network-planning-and-performance.md). Birinci hedef, mümkünse Çin'de İnternet'Microsoft 365 gelen genel hizmetlere erişimi engellemektir.

- Çin ofis ağları ve çin dışındaki genel İnternet Microsoft 365 konumlar arasındaki ağ trafiğini taşımak için mevcut özel ağdan faydalanabilirsiniz. Çin'in dışındaki neredeyse tüm konumlar net bir avantaj sağlayacaktır. Ağ yöneticileri, Microsoft genel ağıyla düşük gecikme süresi bağlantılı olan alanlarda çıkışarak daha [da iyi hale gelir](/azure/networking/microsoft-global-network). Hong Kong, Singapur, Japonya ve Güney Kore örnek olarak verilmiştir.
- Kullanıcıların şirket ağına VPN bağlantısı üzerinden erişmek üzere kullanıcı cihazlarını yapılandırarak, Microsoft 365 ağın özel bağlantısının geçişe izin verir. VPN istemcilerinin bölünmüş bölmeyi kullanmak üzere yapılandırılmamış olduğundan veya kullanıcı cihazlarının bölünmüş trafiği bölmeyi yok saymak üzere yapılandırıldığından Microsoft 365 olun. GERÇEK ZAMANLı medya trafiği için VPN bağlantısını Teams hakkında ek bilgi için bu [bölüme bakın](#optimizing-microsoft-teams-meetings-network-performance-for-users-in-china).
- Tüm trafiği özel Microsoft 365 bağlantınıza yönlendiracak şekilde anızı yapılandırabilirsiniz. Özel bağlantınız üzerindeki trafik hacmini en aza indirmeniz gerekirse, uç noktaları yalnızca En İyi Duruma Getirme kategorisinde yönlendirmeyi ve isteklerin İnternet'i aktarmasına  İzin Ver  ve Varsayılan uç noktalarına izin vermeyi seçebilirsiniz. Bu, iyileştirilmiş trafiği yüksek gecikme süresi ve paket kaybına karşı en duyarlı kritik hizmetlerle sınırlandırarak performansı iyiler ve bant genişliği tüketimini en aza indirecektir.
- Mümkünse, canlı medya akışı trafiği için TCP yerine UDP kullanın; örneğin, Teams. UDP, TCP'ye göre daha iyi canlı medya akışı performansı sunar.

Trafiği seçmeli olarak yönlendirme hakkında bilgi Microsoft 365 için bkz[. Office 365 yönetme](managing-office-365-endpoints.md). Tüm dünya çapında her türlü URL'Office 365 IP adreslerinin listesi için bkz. OFFICE 365 [ve IP adresi aralıkları](urls-and-ip-address-ranges.md).

![Microsoft 365 - iyileştirilmiş.](../media/O365-networking/China-O365-optimized.png)

## <a name="user-best-practices"></a>Kullanıcı için en iyi yöntemler

Çin'de ev, kafe mağazaları, oteller ve ofisler gibi uzak konumlardan küresel Microsoft 365 kiracılarına bağlanan ve kurumsal ağlara bağlantısı olmayan kullanıcılar, cihazlarıyla Microsoft 365 arasındaki trafiğin Çin'in tıkanık çapraz ağ devrelerini aktarması nedeniyle düşük ağ performansıyla yaşanıyor.

Şirket ağına sınır ötesi özel ağlar ve/veya VPN erişimi bir seçenek yoksa, Çin tabanlı kullanıcılarınızı bu en iyi yöntemleri izlemeleri için eğitimle kullanıcı başına performans sorunlarının azaltılmasına devam eder.

- Önbelleği destekleyen zengin Office istemcileri kullanın (örneğin, Outlook, Teams, OneDrive, vb.) ve web tabanlı istemcilerden kaçının. Office önbelleğe alma ve çevrimdışı erişim özellikleri ağ tıkanıklığı ve gecikme süresinin etkisini önemli ölçüde azaltır.
- Kullanıcı Microsoft 365 Sesli Konferans özelliğiyle yapılandırılmışsa, Teams kullanıcılar ortak anahtarlı telefon ağı (PSTN) üzerinden toplantılara katılabilir. Daha fazla bilgi için bkz. [Office 365](/microsoftteams/audio-conferencing-in-office-365).
- Kullanıcılar ağ performansı sorunlarıyla yaşanıyorsa, sorun giderme için KENDI IT departmanlarına bildirmeleri ve güvenlik hizmetleriyle ilgili sorun olması Microsoft 365 Microsoft desteğine yükseltmeleri gerekir. Tüm sorunlar kenarlıklar arası ağ performansından kaynaklanmaz.

## <a name="optimizing-microsoft-teams-meetings-network-performance-for-users-in-china"></a>Çin'Microsoft Teams kullanıcılar için toplantı ağ performansını iyileştirme

Genel posta kiracıları olan Microsoft 365 Çin'de iletişim durumu olan kuruluşlarda, Microsoft 365 tabanlı kullanıcılar için istemci performansı, Çin İnternet mimarisine özgü faktörler tarafından karmaşık olabilir. Birçok şirket ve okul bu kılavuza uygun sonuçlar bildirdi. Ancak bu kapsam, VPN bağlantısı olan ofis konumları veya ev/mobil uç noktaları gibi, IT ağı kurulumunun denetimi altındaki kullanıcı ağı konumlarıyla sınırlıdır. Microsoft Teams aramalar ve toplantılar genellikle ev ofisleri, mobil konumlar, yolda ve kafe gibi dış konumlardan kullanılır. Aramalar ve toplantılar gerçek zamanlı medya trafiğine dayanmalarından dolayı, Teams bu deneyimler ağ tıkanıklığı konusunda özellikle duyarlıdır.

Sonuç olarak, Microsoft Çin'deki yerel ve genel İnternet bağlantıları ile Teams ve Skype hizmetleri arasındaki daha kaliteli ve tercih edilen bir ağ yolu kullanarak Teams ve Skype Kurumsal Online gerçek zamanlı medya trafiğini taşımak için telekomünikasyon sağlayıcılarıyla ortak çalışmalar yürütmektedir Microsoft 365. Bu özellik, paket kaybına ve kullanıcı deneyimini etkileyen diğer önemli ölçümlere göre on kattan fazla geliştirme elde etti.

>[!IMPORTANT]
>Şu anda bu iyileştirmeler, büyük yayın veya Microsoft Stream kullanarak yapılan büyük toplantı veya "kasaba salonu" stili toplantılar gibi Microsoft Live Events Teams ilgili değildir. Canlı Etkinlikler toplantısını görüntülemek için Çin'deki kullanıcıların özel bir ağ veya SDWAN/VPN çözümü kullanmaları gerekir. Bununla birlikte, ağ geliştirmeleri Canlı Etkinlik toplantılarını yapan veya üreten kullanıcılara fayda sağlar, çünkü bu deneyim yapımcı veya sunucu için normal Teams toplantısı gibi davranır.

### <a name="organization-network-best-practices-for-teams-meetings"></a>Toplantılara yönelik kuruluş ağı Teams yöntemleri

Önceki kılavuzda, sınır ötesi ağ tıkanıklığından kaçınmak için özel bir ağ uzantısını göz önünde bulundurursa, bu ağ geliştirmelerini nasıl kullanılay? göz önünde bulundurabilirsiniz. Kuruluş office ağları için iki genel seçenek vardır:

1. Yeni bir şey yapma. Kenarlıklar arası tıkanıklığı önlemek için, özel ağ atlama çevresinde önceki yönergeleri takip etmeye devam edin. Teams gerçek zamanlı medya trafiği, daha önce olduğu gibi bu kurulumdan yararlanacak.
2. Bölünmüş/karma desen uygulama.
   - Toplantılar ve gerçek zamanlı medya trafiğini arama dışında, iyileştirme Teams tüm trafik için önceki kılavuzu kullanın.
   - Toplantı Teams ve gerçek zamanlı medya trafiğini ortak İnternet üzerinden yönlendirin. Gerçek zamanlı medya ağ trafiğini belirlemeyle ilgili bilgiler için aşağıdaki bilgilere bakın.

Yüksek Teams kullanan genel İnternet üzerinden gerçek zamanlı medya ses ve görüntü trafiği göndermek, önemli ölçüde maliyet tasarrufu sağlar çünkü bu trafik özel bir ağ üzerinden ücret ödeme yerine ücretsizdir. Kullanıcılar SDWAN veya VPN istemcileri de kullanıyorsa, benzer ek avantajlar olabilir. Bazı kuruluşlar, genel uygulama olarak daha fazla veri çapraz İnternet bağlantısına sahip olmayı da tercih ediyor olabilir.

Aynı seçenekler SDWAN veya VPN yapılandırmaları için de uygulanabilir. Örneğin, bir kullanıcı şirket ağına giden trafiği Microsoft 365 için SDWAN veya VPN kullanıyor ve ardından çapraz tıkanıklığı önlemek için bu ağın özel uzantısından yararlanarak kullanıyor. Kullanıcının SDWAN veya VPN'i artık VPN yönlendirmesinde toplantı Teams gerçek zamanlı trafiği aramak dışında tutulacak şekilde yaslanabilirsiniz. Bu VPN yapılandırması bölünmüş kazıma olarak adlandırılır. Daha [fazla bilgi için bkz. Office 365](/microsoft-365/enterprise/microsoft-365-vpn-implement-split-tunnel) VPN bölünmüş bölme.

Ayrıca, gerçek zamanlı trafik de dahil olmak üzere tüm dünya trafiği Microsoft 365 SDWAN veya VPN Microsoft Teams kullanmaya devam edersiniz. Microsoft'un SDWAN veya VPN çözümlerinin kullanımıyla ilgili hiçbir önerisi yoktur.

### <a name="home-mobile-and-user-network-best-practices-for-teams-meetings"></a>Toplantılarınız için ev, mobil ve kullanıcı ağı için Teams yöntemleri

Çin'deki kullanıcılar, Çin'deki genel İnternet hizmetine sabit hat veya mobil bağlantı üzerinden bağlanarak bu geliştirmelerden faydalanabilirsiniz. Teams gerçek zamanlı medya ses ve video trafiğinin genel İnternet'te gerçek zamanlı olarak

Bununla birlikte, sohbet Microsoft 365 dosyalar gibi diğer Teams hizmetlerinden ve diğer trafiğin verileri bu geliştirmelerden doğrudan yararlanamaz. Kuruluş ağının dışındaki kullanıcılar da bu trafikte ağ performansı düşük olabilir. Bu makalede de ele alınarak, VPN veya SDWAN kullanarak bu etkiyi azaltmak için kullanabilirsiniz. Ayrıca, kullanıcılarının ağ sorunlarını azaltmak için uygulama içinde önbelleğe almayı destekleyen web istemcileri üzerinden zengin masaüstü istemcileri kullanmalarını da sebilirsiniz.

### <a name="identifying-teams-real-time-media-network-traffic"></a>Gerçek Teams medya ağ trafiğini tanımlama

Ağ cihazı veya VPN/SDWAN kurulumu yapılandırmak için yalnızca gerçek zamanlı medya Teams video trafiğini hariç tutabilirsiniz. Trafik ayrıntıları, kimlik 11 için URL'ler ve [IP adresi Office 365 resmi listesinde bulunabilir](urls-and-ip-address-ranges.md#skype-for-business-online-and-microsoft-teams). Diğer tüm ağ yapılandırmaları olduğu gibi kal olmalıdır.

Microsoft mümkün olan en geniş ağ Microsoft 365 özellikleri genelinde kullanıcı deneyimini ve istemcilerin performansını geliştirmek için sürekli olarak çalışıyor. Konuşma başlatmak [Office 365 katılmak](https://techcommunity.microsoft.com/t5/office-365-networking/bd-p/Office365Networking) Community kaynak bulmak, özellik istekleri ve öneriler göndermek için Ağ Ağı Teknik Ekibi iletişim sitesini ziyaret edin

## <a name="related-topics"></a>İlgili konular

[Ağ planlaması ve performans ayarı Microsoft 365](./network-planning-and-performance.md)

[Microsoft 365 bağlantısı ilkeleri](microsoft-365-network-connectivity-principles.md)

[Kullanıcı Office 365 yönetme](managing-office-365-endpoints.md)

[Office 365 URL'leri ve IP adresi aralıkları](urls-and-ip-address-ranges.md)

[Microsoft genel ağı](/azure/networking/microsoft-global-network)
