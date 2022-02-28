---
title: İçerik teslim ağları
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 07/15/2020
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Ent_O365
- SPO_Content
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 0140f704-6614-49bb-aa6c-89b75dcd7f1f
description: Bu bilgileri, performansı geliştirmek için Office 365 Ağlarını (CDN) nasıl kullandığı hakkında bilgi edinmek için kullanın.
ms.openlocfilehash: 1aecd8b23502ed8626979d258f7d26a90b4d3d51
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62985355"
---
# <a name="content-delivery-networks-cdns"></a>İçerik Teslim Ağları (CDN)

*Bu makale hem son hem de Microsoft 365 Kurumsal hem de Office 365 Kurumsal.*

CDNs, son kullanıcılar Office 365 ve güvenilir bir şekilde çalışmanıza yardımcı olur. Office 365 bulut hizmetleri, indirmeleri hızlandırmak ve son kullanıcı gecikmesini algılanmalarını azaltmak için daha yakın olan tarayıcıların statik varlıklarını önbelleğe alan CDN'leri kullanır. Bu konu başlığı altında yer alan bilgiler İçerik Teslim Ağları (CDN) ve dağıtım ağları tarafından nasıl kullanıldıları hakkında bilgi Office 365.

## <a name="what-exactly-is-a-cdn"></a>Bu tam olarak CDN?

Hızlı CDN, yüksek hızlı omurga ağları ile bağlanan veri merkezlerinde ara sunuculardan ve dosya sunucularından oluşan, coğrafi olarak dağıtılmış bir ağdır. CDNs, bir web sitesi veya hizmette belirtilen dosya ve nesneler kümesinde gecikmeyi ve yükleme sürelerini azaltmak için kullanılır. Bir CDN herhangi bir konumdan gelen istekleri en iyi şekilde sağlamak için binlerce uç noktası olabilir.

CDNs, yaygın olarak Javascript dosyaları, simgeler ve resimler gibi bir web sitesi veya hizmeti için genel içeriğin daha hızlı indirilmelerini sağlamak için kullanılır ve ayrıca SharePoint Online belge kitaplıklarında dosyalar, medya dosyası akışı ve özel kod gibi kullanıcı içeriğine özel erişim sağlar.

CDNs, kurumsal bulut hizmetlerinin çoğu tarafından kullanılır. Office 365 bulut hizmetlerinin, tescilli içerikle (e-postalar gibi) genel içeriği (simgeler gibi) aynı anda karma olarak indiren milyonlarca müşterisi vardır. Simgeler gibi herkesin kullandığı resimleri kullanıcının bilgisayarına mümkün olduğunca yakın bir yere koymak daha verimli olur. Her bulut hizmeti, bu genel içeriği tüm metropolitan CDN, hatta dünyanın her büyük İnternet hub'sinde depolar ve bu nedenle bu CDNs'lerden bir bazıları paylaşılır.

## <a name="how-do-cdns-make-services-work-faster"></a>CDNs, hizmetlerin daha hızlı çalışmasına nasıl neden olur?

Site resimleri ve simgeler gibi yaygın nesneleri tekrar tekrar indirmek, e-posta veya belgeler gibi önemli kişisel içeriği indirmek için daha iyi  kullanılay ağ bant genişliğini yer alabiliyor. Varsayılan Office 365 CDN'ler içeren bir mimari kullandığından, simgeler, betikler ve diğer genel içerik istemci bilgisayarlara daha yakın olan sunuculardan indirilebilir ve böylece indirmeler daha hızlı olur. Bu, veri merkezleri içinde güvenli bir şekilde depolanan kişisel içeriğinize daha Office 365 anlamına gelir.

CDNs çeşitli yollarla bulut hizmeti performansını iyileştirmeye yardımcı olur:

- CDN'ler ağın bir bölümünü ve dosya indirme yükünü bulut hizmetinin dışında bırakarak, statik varlıklara yönelik isteklere hizmet etme ihtiyacını azaltarak kullanıcı içeriğine ve diğer hizmetlere hizmet etmek için bulut hizmeti kaynaklarını serbest bırakarak.
- CDNs, yüksek performanslı ağları ve dosya sunucularını uygulayarak ve üst düzeyde verimli sıkıştırmayla [HTTP/2](https://en.wikipedia.org/wiki/HTTP/2) gibi güncelleştirilmiş ağ protokollerinden yararlanarak ve çoklu sıkıştırma isteğinde bulunarak düşük gecikme süresi dosya erişimi sağlamak için tasarlanmıştır.
- CDN ağlarda, içeriğin kullanıcılara mümkün olduğunca yakın bir şekilde kullanılabilir olması için genel olarak dağıtılmış birçok uç nokta kullanılır.

## <a name="the-office-365-cdn"></a>Office 365 CDN

Yerleşik Office 365 Content Delivery Network (CDN), Office 365 yöneticilerinin statik varlıkları istekte bulunan tarayıcılara daha yakın bir zamanda önbelleğe alınarak kuruluşlarının SharePoint Online sayfaları için daha iyi performans sağlamalarına olanak sağlar ve bu da indirmeleri hızlandırmak ve gecikmeyi azaltmaya yardımcı olur. Gelişmiş Office 365 CDN ve [indirme hızları için HTTP/2](https://en.wikipedia.org/wiki/HTTP/2) protokolünü kullanır.

> [!NOTE]
> Ürün Office 365 CDN yalnızca Üretim (dünya çapında) **bulutunda** bulunan kiracılar tarafından kullanılabilir. ABD Kamu, Çin ve Almanya bulutlarında yer alan kiracılar şu anda bu Office 365 CDN.

Kaynak Office 365 CDN birden çok konumda veya kaynakta statik varlıkları barındırmana ve bunları genel yüksek hızlı ağlardan hizmet vermesine olanak sağlayan birden çok CDN'den oluşur. Kaynak 2013'te barındırmak istediğiniz içeriğin türüne Office 365 CDN, özel kökenleri veya **her ikisini birden** ebilirsiniz.

![Office 365 CDN diyagramı oluşturma.](../media/O365-CDN/o365-cdn-flow-transparent.svg "Office 365 CDN kavramsal diyagramı")

Kaynakta **yer** alan genel Office 365 CDN anonim olarak erişilebilir ve barındırılan varlıklara sahip URL'leri olan herkes bu içeriğe erişilebilir. Genel kaynaklarda içeriğe erişim anonim olduğundan, bunları yalnızca Javascript dosyaları, betikler, simgeler ve resimler gibi hassas olmayan genel içeriği önbelleğe alırsiniz. Varsayılan Office 365 CDN, genel kaynak varlıklarını bir genel kaynağa Office 365 kaynak varlıklarını indirmek için kullanılır.

**Site** içindeki özel Office 365 CDN, SharePoint Online belge kitaplıkları, siteler ve özel resimler gibi kullanıcı içeriğine özel erişim sağlar. Özel kaynaklarda içeriğe erişim dinamik olarak oluşturulan belirteçlerle güvence altına alınır, dolayısıyla bu içeriğe yalnızca özgün belge kitaplığı veya depolama konumu izinleri olan kullanıcılar tarafından erişilebilir. Kaynak veri kaynağı Office 365 CDN yalnızca SharePoint Online içeriği için kullanılabilir ve SharePoint Online kiracınızı yeniden yönlendirme yoluyla varlıklara erişebilirsiniz.

Office 365 CDN Hizmeti, SharePoint Online aboneliğinizin bir parçası olarak dahil edilir.

E-posta teslim ağın nasıl Office 365 CDN daha fazla bilgi için bkz[. Office 365 Online'la SharePoint.](use-microsoft-365-cdn-with-spo.md)

Videoların kullanımı hakkında kavramsal ve HOWTO bilgileri sağlayan bir kısa video serisini Office 365 CDN Geliştirici SharePoint [Yöntemleri YouTube kanalını ziyaret edin](https://aka.ms/sppnp-videos).

## <a name="other-microsoft-cdns"></a>Diğer Microsoft CDN'leri

Office 365 CDN'ın bir parçası değil de, bu CDNs'leri Office 365 kiracınız içinde SharePoint geliştirme kitaplıklarına, özel kodlara ve kitaplığın kapsamı dışında olan diğer amaçlara erişmek için Office 365 CDN.

### <a name="azure-cdn"></a>Azure CDN

>[!NOTE]
>SharePoint Online, 3 2020'den itibaren gelişmiş video kayıttan Azure CDN güvenilirliğini desteklemek üzere videoların önbelleğe alınmasını başlayacaktır. Popüler videolar, kullanıcıya en CDN uç nokta üzerinden akışla gönderilir. Bu veriler, uyumluluk Microsoft 365 kalır. Bu, tüm kiracılar için ücretsiz bir hizmettir ve herhangi bir müşteri eyleminin yapılandırılması gerektirmez.

**Azure CDN'i** kullanarak özel web bölümlerini, kitaplıkları ve diğer kaynak varlıklarını barındırmak üzere kendi CDN örneğinizi dağıtarak, CDN depolama alanınıza erişim tuşları uygulamanızı ve CDN yapılandırmanız üzerinde daha fazla denetim uygulamanıza olanak verir. Aboneliğin kullanımı Azure CDN ücretsiz değildir ve Azure aboneliği gerektirir.

Bir örneği yapılandırma hakkında daha fazla bilgi Azure CDN için bkz. Hızlı Başlangıç: Azure depolama hesabını depolama [alanıyla Azure CDN](/azure/cdn/cdn-create-a-storage-account-with-cdn).

Bu web bölümlerini barındırmak Azure CDN örneğin, SharePoint için SharePoint istemci tarafı web bölümünü dağıtma [Azure CDN](/sharepoint/dev/spfx/web-parts/get-started/deploy-web-part-to-cdn).

Yeni PowerShell modülü Azure CDN için bkz. [PowerShell'Azure CDN yönetme](/azure/cdn/cdn-manage-powershell).

### <a name="microsoft-ajax-cdn"></a>Microsoft Ajax CDN

Microsoft'un **Ajax CDN** CDN jQuery (ve diğer tüm kitaplıkları), ASP.NET Ajax, Bootstrap, Knockout.js gibi birçok popüler geliştirme kitaplığını sunan salt okunur bir Knockout.js.
  
Bu betikleri projenize eklemek için, bu genel kullanıma açık kitaplıklara yapılan başvuruları projenizin kendisine eklemek yerine CDN adresine yapılan başvurularla değiştirmeniz gerekir. Örneğin, jQuery'ye bağlantı vermek için aşağıdaki kodu kullanın:

``` html
<script src=https://ajax.aspnetcdn.com/ajax/jquery-2.1.1.js> </script>
```

Microsoft Ajax ajax sürümü kullanma hakkında daha fazla bilgi CDN bkz. [Microsoft Ajax CDN](/aspnet/ajax/cdn/overview).

## <a name="how-does-office-365-use-content-from-a-cdn"></a>Bir Office 365 içeriği nasıl CDN?

Kiracınız için CDN neleri yapılandırmış olur Office 365, temel veri alma işlemi aynıdır.

1. İstemciniz (tarayıcı veya Office istemci uygulaması) siteden Office 365.

2. Office 365 verileri doğrudan istemcinize döndürür veya veriler müşteriniz tarafından barındırılan bir içerik kümesi kapsamında yer CDN, istemcinizi ana bilgisayar URL'nize CDN.

    a. Veriler genel kaynak olarak önbelleğe alınmışsa,  istemciniz verileri doğrudan en yakın kaynak konumdan CDN istemcinize indirir.

    b. Veriler özel bir kaynakta zaten önbelleğe alınmışsa, CDN hizmeti kaynak Office 365 izinlerini denetler. İzinleriniz varsa, SharePoint Online varlık yolundan oluşan özel bir URL'yi dinamik olarak CDN iki erişim belirteci oluşturur ve istemcinize özel URL'yi döndürür. Ardından istemciniz, özel URL'yi kullanarak verileri CDN yakın adres konumdan istemcinize indirir.

3. Veriler CDN'de önbelleğe alınmazsa, CDN düğümü Office 365'den verileri seçer ve ardından istemciniz verileri indirdikten sonra bir süre için verileri önbelleğe verir.

Kullanıcı CDN tarayıcısına en yakın veri merkezi ortaya çıkar ve yeniden yönlendirmeyi kullanarak istenen verileri buradan indirir. CDN yönlendirmesi hızlıdır ve kullanıcılara çok fazla indirme süresi tasarrufu sağlar.

## <a name="how-should-i-set-up-my-network-so-that-cdns-work-best-with-office-365"></a>CDN'lerin en iyi şekilde çalışması için ağımı nasıl Office 365?

En iyi performansın sağlanması için ağ istemcilerle CDN uç noktaları arasındaki gecikme süresini en aza indirmek en önemli noktadır. Ağ yapılandırmanız, istemci tarayıcılarının gereksiz gecikmelere neden olmasını önlemek için[, Office 365](managing-office-365-endpoints.md) uç noktalarını yönetme konusunda belirtilen en iyi yöntemleri kullanarak, istemci tarayıcılarının CDN trafiğini merkezixler üzerinden yönlendirme yerine doğrudan CDN erişimine izin verir.

Ayrıca, ağ Office 365 [iyileştirmenin ardındaki](./microsoft-365-network-connectivity-principles.md) kavramları anlamak için Ağ Bağlantısı Office 365 okuyabilirsiniz.

## <a name="is-there-a-list-of-all-the-cdns-that-office-365-uses"></a>Bunu kullanan tüm CDN'lerin listesi Office 365 var mı?

OFFICE 365 tarafından kullanımda olan CDN'ler her zaman değişebilir ve birçok durumda, kullanılamayan durumda CDN iş ortağı yapılandırılmış birden çok iş ortağı vardır. Aşağıdakiler tarafından kullanılan birincil CDN'Office 365:

|CDN  |Şirket  |Kullanım  |Bağlantı  |
|---------|---------|---------|---------|
|Office 365 CDN     |Microsoft Azure         |Genel kaynaklarda genel varlıklar, SharePoint kaynaklarda yer alan kullanıcı içeriklerini         |[Microsoft Azure CDN](https://azure.microsoft.com/documentation/services/cdn/)         |
|Azure CDN     |Microsoft         |Özel kod ve SharePoint Framework çözümleri         |[Microsoft Azure CDN](https://azure.microsoft.com/documentation/services/cdn/)         |
|Microsoft Ajax CDN (salt okunur)     |Microsoft         |Ajax, jQuery, ASP.NET, Bootstrap, Knockout.js gibi ortak kitaplıklar.         |[Microsoft Ajax CDN](/aspnet/ajax/cdn/overview)         |

## <a name="what-performance-gains-does-a-cdn-provide"></a>Bir CDN ne CDN sağlar?

Doğrudan Office 365'tan indirilen veriler ile kiracınıza ve en yakın CDN uç noktasına göre belirli bir CDN'tan indirilen veriler, CDN tarafından kullanılan bir sayfada yer alan varlık sayısı ve ağ gecikme süresi ve bant genişliğinde geçici değişiklikler gibi performans farklılıklarını ölçmeye katılan birçok faktör vardır. Bununla birlikte, basit bir A/B testi belirli bir dosya için indirme süresi farkı göstermeye yardımcı olabilir.

Aşağıdaki ekran görüntülerinde, Office 365'te yerel dosya konumuyla Microsoft Ajax dosyasında barındırılan dosya arasındaki indirme [hızı Content Delivery Network](/aspnet/ajax/cdn/overview). Bu ekran görüntüleri Internet Explorer 11 geliştirici araçlarının Ağ sekmesinden alınarak görüntülenir. Bu ekran görüntüleri, popüler jQuery kitaplığında gecikmeyi gösterir. Bu ekranı yukarı getirmek için, Internet Explorer'da **F12'ye** basın ve  sekme simgesiyle simgesiyle birlikte Wi-Fi seçin.
  
![F12 Ağ'ın ekran görüntüsü.](../media/930541fd-af9b-434a-ae18-7bda867be128.png)
  
Bu ekran görüntüsü, çevrimiçi sitenin kendisinde ana sayfa galerisine SharePoint kitaplığı gösterir. Kitaplığı karşıya yükleme süresi 1,51 saniyedir.
  
![1.51s yükleme süresi ekran görüntüsü.](../media/64225c79-fa53-480f-81cd-0d351674320e.png)
  
İkinci ekran görüntüsünde, aynı dosyanın Microsoft tarafından teslim CDN. Bu kez gecikme süresi 496 milisaniye civarındadır. Bu büyük bir gelişmedir ve nesneyi indirmek için gereken toplam sürenin tam bir saniye süre içinde olduğunu gösterir.
  
![469 ms'de yükleme zamanlarının ekran görüntüsü.](../media/6a553cc3-25a0-42c1-aae7-4aebbc2eb4c3.png)

## <a name="is-my-data-safe"></a>Verilerim güvenli mi?

İşlerinizi halleden verilerin korunması için büyük bir özenle karşılarız. Veri kaynağında depolanan Office 365 CDN hem iletilip hem de saklanan olarak şifrelenir ve Office 365 SharePoint CDN'deki verilere erişim, kullanıcı Office 365 ve belirteç yetkilendirmesi ile güvence altına alınır. Veri kaynağında veri Office 365 SharePoint CDN istekleri, Office 365 kiracınıza yönlendirilmesi (yeniden yönlendirilmesi) gerekir veya bir yetkilendirme belirteci oluşturulmaz.

Verilerinizin güvenli kalmasını sağlamak için, kullanıcı içeriğini veya diğer hassas verileri hiçbir zaman genel sitelerde depolamamanızı CDN. Genel posta dosyasındaki verilere CDN anonim olduğundan, genel CDN'ler yalnızca web betiği dosyaları, simgeler, resimler ve hassas olmayan diğer varlıklar gibi genel içerikleri barındırmak için kullanılmalıdır.

> [!NOTE]
> Üçüncü taraf CDN sağlayıcılar, Güvenlik Merkezi tarafından belirtilen taahhütlerden farklı gizlilik ve uyumluluk Office 365 olabilir. CDN hizmeti tarafından önbelleğe alınan veriler Microsoft Veri İşleme Koşullarına (DPT) uygun değildir ve Office 365 Merkezi uyumluluk sınırları dışında olabilir.

Sağlayıcıların gizlilik ve veri koruması hakkında ayrıntılı bilgi Office 365 CDN, şu ziyaretleri ziyaret edin:  

- Microsoft Güven Merkezi Office 365 altında gizlilik ve veri koruması hakkında [daha fazla bilgi edinebilirsiniz](https://www.microsoft.com/trustcenter)
- Akamai Gizlilik Güven Merkezi'nde Akamai'nin gizlilik ve [veri koruması hakkında daha fazla bilgi edinebilirsiniz](https://www.akamai.com/us/en/about/compliance/data-protection-at-akamai.jsp)
- Azure Güven Merkezi'nde Azure gizliliği ve veri koruması hakkında daha [fazla bilgi edinin](https://azure.microsoft.com/overview/trusted-cloud/)

## <a name="how-can-i-secure-my-network-with-all-these-3rd-party-services"></a>Tüm bu üçüncü taraf hizmetleriyle ağın güvenliğini nasıl sağlarum?

Geniş bir iş ortağı hizmetleri kümesiden yararlanarak Office 365 ölçeklendireme ve kullanılabilirlik gereksinimlerini karşılamanın yanı sıra iş ortağı hizmetleri kullanırken kullanıcı deneyimini Office 365. Yararlanan üçüncü taraf Office 365 hizmetler, crl.microsoft.com veya sa.symcb.com gibi sertifika iptal listelerini ve CDN'leri içerir (örneğin, r3.res.outlook.com. Her CDN FQDN, Office 365 için özel bir FQDN'Office 365. Bir FQDN'ye sizin isteğiniz üzerine gönderilirse Office 365 FQDN'yi ve o konumdaki temel içeriği CDN sağlayıcısının denetim altında bulunduğundan emin olabilirsiniz.
  
Microsoft veya Office 365 veri merkezi olan istekleri üçüncü tarafları yöneten isteklerden azaltmak isteyen müşteriler için, Uç noktaları yönetme konusunda yol [Office 365 yazdık](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a).

## <a name="is-there-a-list-of-all-the-fqdns-that-leverage-cdns"></a>CDN'lerden yararlanan tüm FQDN'lerin listesi var mı?

FQDN'ler listesi ve bunların CDN'lerden nasıl yararlanıldıları zaman içinde değişir. CDNs'Office 365 en son FQDN'leri hakkında güncel bilgi almak için yayımlanmış URL'ler ve [IP](./urls-and-ip-address-ranges.md) adresi aralıkları sayfamıza bakın.

CSV veya JSON Office 365 biçimlendirilmiş geçerli URL'ler ve IP adresi aralıklarını talep etmek için Office 365 IP Adresi ve [URL Web](microsoft-365-ip-web-service.md) hizmetini de kullanabilirsiniz.

## <a name="can-i-use-my-own-cdn-and-cache-content-on-my-local-network"></a>Yerel ağımda kendi içerik CDN içeriğimi kullanabilir miyim?

Müşterilerimizin ihtiyaçlarını desteklemek için sürekli yeni yollar arıyoruz ve şu anda ara sunucu çözümlerini ve diğer şirket içi ürün çözümlerini önbelleğe alma kullanımını CDN çalışıyoruz.

Office 365 CDN'ın bir parçası değildir, ancak CDN depolama alanınıza erişim tuşları uygulamanıza ve **CDN** yapılandırmanız üzerinde daha fazla denetim uygulamanıza olanak sağlayan, özel web bölümlerini, kitaplıkları ve diğer kaynak varlıklarını barındırmak için de Azure CDN'i kullanabilirsiniz. Aboneliğin kullanımı Azure CDN ücretsiz değildir ve Azure aboneliği gerektirir. Bir örneği yapılandırma hakkında daha fazla bilgi Azure CDN için bkz. Hızlı Başlangıç: Azure depolama hesabını depolama [alanıyla Azure CDN](/azure/cdn/cdn-create-a-storage-account-with-cdn).

## <a name="im-using-azure-expressroute-for-office-365-does-that-change-things"></a>Diğer iş için Azure ExpressRoute'u Office 365, bu işleri değiştirir mi?

[İnternet için Azure ExpressRoute Office 365](azure-expressroute.md) genel İnternet'Office 365 ayrılmış bir altyapıya özel bir bağlantı sağlar. Bu, istemcilerin ExpressRoute tarafından desteklenen hizmetler listesine açıkça eksiz olan CDN'lere ve diğer Microsoft altyapısına bağlanmak için yine de ExpressRoute dışı bağlantılar üzerinden bağlanması gerek duyduğu anlamına gelir. Belirli bir trafiğin, örneğin CDN'leri hedef alan isteklerin nasıl yönlendir yönetimiyle ilgili daha fazla bilgi için, Office 365 [yönetimine bakın](routing-with-expressroute.md).

## <a name="can-i-use-cdns-with-sharepoint-server-on-premises"></a>CDNs'leri SharePoint Server şirket içi ile kullanabilir miyim?

CDNs kullanmak yalnızca SharePoint Online bağlamında anlamlıdır ve SharePoint Server ile engelılmalıdır. Çünkü coğrafi konumun çevresindeki tüm avantajlar, sunucu şirket içinde veya coğrafi olarak yakın herhangi bir yerde yer alıyorsa, bu avantajların hepsi doğru olmaz. Buna ek olarak, barındır bulunduğu sunucuların ağ bağlantısı varsa, site İnternet bağlantısı olmadan da kullanılabilir ve dolayısıyla bu CDN alınamaz. Bunun dışında, siteniz için CDN kitaplık ve dosyalar için kullanılabilir ve kararlı bir dosya varsa, bir kitaplık kullan gerekir.
  
İşte geri dönmek için kullanabileceğiniz kısa bir bağlantı: [https://aka.ms/o365cdns]()
  
## <a name="see-also"></a>Ayrıca bkz.

[Office 365 Bağlantısı İlkeleri](./microsoft-365-network-connectivity-principles.md)

[Ağ Office 365 değerlendirme](assessing-network-connectivity.md)

[Kullanıcı Office 365 yönetme](managing-office-365-endpoints.md)

[Office 365 URL'leri ve IP adresi aralıkları](./urls-and-ip-address-ranges.md)

[Office 365 Online ile SharePoint içerik teslim SharePoint kullanma](use-microsoft-365-cdn-with-spo.md)

[Microsoft Güven Merkezi](https://www.microsoft.com/trustcenter)

[Performans Office 365 ayarlama](tune-microsoft-365-performance.md)
