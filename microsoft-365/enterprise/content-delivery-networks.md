---
title: İçerik teslim ağları
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: Office 365 performansı geliştirmek için Content Delivery Networks'i (CDN) nasıl kullandığı hakkında bilgi edinmek için bu bilgileri kullanın.
ms.openlocfilehash: b2809a524088b3cb53e415d3d83d1f8a02b27dc1
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65092745"
---
# <a name="content-delivery-networks-cdns"></a>İçerik Teslim Ağları (CDN'ler)

*Bu makale hem Microsoft 365 Kurumsal hem de Office 365 Kurumsal için geçerlidir.*

CDN'ler son kullanıcılar için Office 365 hızlı ve güvenilir tutmaya yardımcı olur. Office 365 gibi bulut hizmetleri, indirmeleri hızlandırmak ve algılanan son kullanıcı gecikme süresini azaltmak için statik varlıkları tarayıcılara daha yakın bir şekilde önbelleğe almak için CDN'leri kullanır. Bu konudaki bilgiler Content Delivery Networks (CDN) ve bunların Office 365 tarafından nasıl kullanıldığı hakkında bilgi edinmenize yardımcı olacaktır.

## <a name="what-exactly-is-a-cdn"></a>CDN tam olarak nedir?

CDN, yüksek hızlı omurga ağları tarafından bağlanan veri merkezlerindeki proxy ve dosya sunucularından oluşan coğrafi olarak dağıtılmış bir ağdır. CDN'ler, bir web sitesindeki veya hizmetteki belirli bir dosya ve nesne kümesinin gecikme süresini ve yükleme sürelerini azaltmak için kullanılır. Bir CDN, herhangi bir konumdan gelen isteklerin en iyi şekilde bakımı için binlerce uç noktaya sahip olabilir.

CDN'ler yaygın olarak Javascript dosyaları, simgeler ve resimler gibi bir web sitesi veya hizmet için genel içeriğin daha hızlı indirilmesi için kullanılır ve ayrıca SharePoint Çevrimiçi belge kitaplıklarındaki dosyalar, akış medya dosyaları ve özel kod gibi kullanıcı içeriğine özel erişim sağlayabilir.

CDN'ler çoğu kurumsal bulut hizmeti tarafından kullanılır. Office 365 gibi bulut hizmetleri, bir kerede özel içerik (e-postalar gibi) ve genel içerik (simgeler gibi) karışımını indiren milyonlarca müşteriye sahiptir. Simgeleri gibi herkesin kullandığı görüntüleri kullanıcının bilgisayarına mümkün olduğunca yaklaştırmak daha verimlidir. Her bulut hizmetinin bu genel içeriği her metropol bölgesinde, hatta dünyanın her yanındaki tüm büyük İnternet merkezlerinde depolayan CDN veri merkezleri oluşturması pratik değildir, bu nedenle bu CDN'lerin bazıları paylaşılır.

## <a name="how-do-cdns-make-services-work-faster"></a>CDN'ler hizmetlerin daha hızlı çalışmasını nasıl sağlar?

Site görüntüleri ve simgeler gibi yaygın nesneleri tekrar tekrar indirmek, e-posta veya belgeler gibi önemli kişisel içerikleri indirmek için daha iyi kullanılabilecek ağ bant genişliğini alabilir. Office 365 CDN'leri içeren bir mimari kullandığından, istemci bilgisayarlara daha yakın sunuculardan simgeler, betikler ve diğer genel içerik indirilebilir ve böylece indirmeler daha hızlı hale getirilebilir. Bu, Office 365 veri merkezlerinde güvenli bir şekilde depolanan kişisel içeriğinize daha hızlı erişim anlamına gelir.

CDN'ler bulut hizmeti performansını çeşitli yollarla iyileştirmeye yardımcı olur:

- CDN'ler ağın ve dosya indirme yükünün bir kısmını bulut hizmetinden uzaklaştırarak, statik varlıklara yönelik istekleri sunma gereksinimini azaltarak kullanıcı içeriği ve diğer hizmetleri sunmak için bulut hizmeti kaynaklarını serbest bırakabilirsiniz.
- CDN'ler, yüksek performanslı ağlar ve dosya sunucuları uygulayarak ve [HTTP/2](https://en.wikipedia.org/wiki/HTTP/2) gibi güncelleştirilmiş ağ protokollerinden son derece verimli sıkıştırma ve istek çoğullama ile yararlanarak düşük gecikme süreli dosya erişimi sağlamak için oluşturulmuş bir amaçtır.
- CDN ağlar, içeriği kullanıcılara mümkün olduğunca yakın bir şekilde kullanılabilir hale getirmek için genel olarak dağıtılmış birçok uç nokta kullanır.

## <a name="the-office-365-cdn"></a>Office 365 CDN

Yerleşik Office 365 Content Delivery Network (CDN), Office 365 yöneticilerin statik varlıkları isteyen tarayıcılara daha yakın önbelleğe alarak kuruluşlarının SharePoint Çevrimiçi sayfaları için daha iyi performans sağlamasına olanak tanır ve bu da indirme işlemlerini hızlandırmaya ve gecikme süresini azaltmaya yardımcı olur. Office 365 CDN, gelişmiş sıkıştırma ve indirme hızları için [HTTP/2 protokollerini](https://en.wikipedia.org/wiki/HTTP/2) kullanır.

> [!NOTE]
> Office 365 CDN yalnızca **Üretim** (dünya çapında) buluttaki kiracılar tarafından kullanılabilir. ABD Hükümeti, Çin ve Almanya bulutlarındaki kiracılar şu anda Office 365 CDN desteklememektedir.

Office 365 CDN, statik varlıkları birden çok konumda veya _kaynakta_ barındırmanıza ve bunları genel yüksek hızlı ağlardan sunmanıza olanak sağlayan birden çok CDN'den oluşur. Office 365 CDN barındırmak istediğiniz içerik türüne bağlı olarak **genel kaynaklar,** **özel** kaynaklar veya her ikisini birden ekleyebilirsiniz.

![kavramsal diyagramı Office 365 CDN.](../media/O365-CDN/o365-cdn-flow-transparent.svg "kavramsal diyagramı Office 365 CDN")

Office 365 CDN içindeki **genel** kaynaklardan gelen içeriğe anonim olarak erişilebilir ve barındırılan varlıklara URL'leri olan herkes tarafından erişilebilir. Genel kaynaklardaki içeriğe erişim anonim olduğundan, bunları yalnızca Javascript dosyaları, betikler, simgeler ve görüntüler gibi hassas olmayan genel içerikleri önbelleğe almak için kullanmanız gerekir. Office 365 CDN, Office 365 istemci uygulamaları gibi genel kaynak varlıklarını genel bir kaynaktan indirmek için varsayılan olarak kullanılır.

Office 365 CDN içindeki **özel** kaynaklar, SharePoint Çevrimiçi belge kitaplıkları, siteler ve özel görüntüler gibi kullanıcı içeriğine özel erişim sağlar. Özel kaynaklardaki içeriğe erişim, dinamik olarak oluşturulan belirteçlerle güvenli hale getirildiğinden, içeriğe yalnızca özgün belge kitaplığı veya depolama konumu izinleri olan kullanıcılar tarafından erişilebilir. Office 365 CDN özel kaynaklar yalnızca çevrimiçi SharePoint içerik için kullanılabilir ve varlıklara yalnızca SharePoint Online kiracınızdan yeniden yönlendirme yoluyla erişebilirsiniz.

Office 365 CDN hizmeti, SharePoint Online aboneliğinizin bir parçası olarak dahil edilir.

Office 365 CDN kullanma hakkında daha fazla bilgi için bkz. [SharePoint Online ile Office 365 içerik teslim ağını kullanma](use-microsoft-365-cdn-with-spo.md).

Office 365 CDN kullanımı hakkında kavramsal ve HOWTO bilgileri sağlayan bir dizi kısa video izlemek için [geliştirici desenleri ve uygulamaları SharePoint YouTube kanalını](https://aka.ms/sppnp-videos) ziyaret edin.

## <a name="other-microsoft-cdns"></a>Diğer Microsoft CDN'leri

Office 365 CDN bir parçası olmasa da, Office 365 kiracınızda bu CDN'leri SharePoint geliştirme kitaplıklarına, özel koda ve Office 365 CDN kapsamı dışında kalan diğer amaçlara erişim için kullanabilirsiniz.

### <a name="azure-cdn"></a>Azure CDN

>[!NOTE]
>3.03.2020'de SharePoint Online, geliştirilmiş video kayıttan yürütmeyi ve güvenilirliği desteklemek için videoları Azure CDN önbelleğe almaya başlayacaktır. Popüler videolar kullanıcıya en yakın CDN uç noktasından akışla aktarılacaktır. Bu veriler Microsoft Purview sınırı içinde kalır. Bu, tüm kiracılar için ücretsiz bir hizmettir ve yapılandırmak için herhangi bir müşteri eylemi gerektirmez.

**özel** web bölümlerini, kitaplıkları ve diğer kaynak varlıklarını barındırmak üzere kendi CDN örneğinizi dağıtmak için Azure CDN kullanabilirsiniz. Bu sayede CDN depolama alanınıza erişim anahtarları uygulayabilir ve CDN yapılandırmanız üzerinde daha fazla denetim sağlayabilirsiniz. Azure CDN kullanımı ücretsiz değildir ve Bir Azure aboneliği gerektirir.

Azure CDN örneği yapılandırma hakkında daha fazla bilgi için bkz[. Hızlı Başlangıç: Azure depolama hesabını Azure CDN ile tümleştirme](/azure/cdn/cdn-create-a-storage-account-with-cdn).

Azure CDN SharePoint web bölümlerini barındırmak için nasıl kullanılabileceğini gösteren bir örnek için bkz. [SharePoint istemci tarafı web bölümünüzü Azure CDN dağıtma](/sharepoint/dev/spfx/web-parts/get-started/deploy-web-part-to-cdn).

Azure CDN PowerShell modülü hakkında bilgi için bkz. [PowerShell ile Azure CDN yönetme](/azure/cdn/cdn-manage-powershell).

### <a name="microsoft-ajax-cdn"></a>Microsoft Ajax CDN

**Microsoft'un Ajax CDN**, jQuery (ve diğer tüm kitaplıkları), ASP.NET Ajax, Bootstrap, Knockout.js ve diğerleri gibi birçok popüler geliştirme kitaplığı sunan salt okunur bir CDN.
  
Bu betikleri projenize eklemek için, bu genel kullanıma açık kitaplıklara yapılan başvuruları projenize eklemek yerine CDN adresine yapılan başvurularla değiştirmeniz yeterlidir. Örneğin, jQuery'ye bağlanmak için aşağıdaki kodu kullanın:

``` html
<script src=https://ajax.aspnetcdn.com/ajax/jquery-2.1.1.js> </script>
```

Microsoft Ajax CDN kullanma hakkında daha fazla bilgi için bkz. [Microsoft Ajax CDN](/aspnet/ajax/cdn/overview).

## <a name="how-does-office-365-use-content-from-a-cdn"></a>Office 365 bir CDN içeriğini nasıl kullanır?

Office 365 kiracınız için hangi CDN yapılandırdığınızdan bağımsız olarak, temel veri alma işlemi aynıdır.

1. İstemciniz (tarayıcı veya Office istemci uygulaması) Office 365'dan veri ister.

2. Office 365 verileri doğrudan istemcinize döndürür veya veriler CDN tarafından barındırılan bir içerik kümesinin parçasıysa, istemcinizi CDN URL'sine yönlendirir.

    a. Veriler zaten _genel_ bir kaynakta önbelleğe alınmışsa, istemciniz verileri doğrudan en yakın CDN konumdan istemcinize indirir.

    b. Veriler zaten _özel_ bir kaynakta önbelleğe alınmışsa, CDN hizmeti Office 365 kullanıcı hesabınızın kaynak üzerindeki izinlerini denetler. İzinleriniz varsa, SharePoint Online dinamik olarak CDN ve iki erişim belirtecindeki varlığın yolundan oluşan özel bir URL oluşturur ve istemcinize özel URL'yi döndürür. Ardından istemciniz, özel URL'yi kullanarak verileri doğrudan en yakın CDN konumdan istemcinize indirir.

3. Veriler CDN önbelleğe alınmazsa, CDN düğümü verileri Office 365'dan talep eder ve istemciniz verileri indirdikten sonra belirli bir süre boyunca verileri önbelleğe alır.

CDN, kullanıcının tarayıcısına en yakın veri merkezini görür ve yeniden yönlendirmeyi kullanarak istenen verileri oradan indirir. CDN yeniden yönlendirme hızlıdır ve kullanıcılara çok fazla indirme süresi kazandırabilir.

## <a name="how-should-i-set-up-my-network-so-that-cdns-work-best-with-office-365"></a>CDN'lerin Office 365 ile en iyi şekilde çalışması için ağımı nasıl ayarlamam gerekir?

Ağınızdaki istemcilerle CDN uç noktaları arasındaki gecikme süresini en aza indirmek, en iyi performansı sağlamak için dikkat edilmesi gereken önemli noktadır. Ağ yapılandırmanızın gereksiz gecikmeyi önlemek için merkezi proxy'ler üzerinden CDN trafiği yönlendirmek yerine istemci tarayıcılarının CDN doğrudan erişmesine izin vermesini sağlamak için Office 365 [uç noktalarını yönetme](managing-office-365-endpoints.md) bölümünde açıklanan en iyi yöntemleri kullanabilirsiniz.

Office 365 ağ performansını iyileştirmenin ardındaki kavramları anlamak için Office 365 [Ağ Bağlantısı İlkeleri'ni](./microsoft-365-network-connectivity-principles.md) de okuyabilirsiniz.

## <a name="is-there-a-list-of-all-the-cdns-that-office-365-uses"></a>Office 365 tarafından kullanılan tüm CDN'lerin listesi var mı?

Office 365 tarafından kullanılan CDN'ler her zaman değiştirilebilir ve çoğu durumda bir iş ortağının kullanılamadığı durumlarda yapılandırılmış birden çok CDN iş ortağı vardır. Office 365 tarafından kullanılan birincil CDN'ler şunlardır:

|CDN  |Şirket  |Kullanım  |Bağlantı  |
|---------|---------|---------|---------|
|Office 365 CDN     |Microsoft Azure         |Genel kaynaklarda genel varlıklar, özel kaynaklarda kullanıcı içeriği SharePoint         |[Microsoft Azure CDN](https://azure.microsoft.com/documentation/services/cdn/)         |
|Azure CDN     |Microsoft         |Özel kod, SharePoint Framework çözümleri         |[Microsoft Azure CDN](https://azure.microsoft.com/documentation/services/cdn/)         |
|Microsoft Ajax CDN (salt okunur)     |Microsoft         |Ajax, jQuery, ASP.NET, Bootstrap, Knockout.js vb. için ortak kitaplıklar.         |[Microsoft Ajax CDN](/aspnet/ajax/cdn/overview)         |

## <a name="what-performance-gains-does-a-cdn-provide"></a>bir CDN hangi performans kazançlarını sağlar?

Doğrudan Office 365 indirilen veriler ile belirli bir CDN indirilen veriler arasındaki performans farklarının ölçülmesiyle ilgili birçok faktör vardır. Örneğin, kiracınıza ve en yakın CDN uç noktasına göre konumunuz, CDN tarafından sunulan sayfadaki varlık sayısı ve ağ gecikme süresi ile bant genişliğindeki geçici değişiklikler. Ancak basit bir A/B testi, belirli bir dosya için indirme süresi farkını göstermeye yardımcı olabilir.

Aşağıdaki ekran görüntüleri, Office 365'daki yerel dosya konumu ile [Microsoft Ajax](/aspnet/ajax/cdn/overview) Content Delivery Network'nde barındırılan dosya arasındaki indirme hızı farkını gösterir. Bu ekran görüntüleri Internet Explorer 11 geliştirici araçlarının **Ağ** sekmesinden alınmaktadır. Bu ekran görüntüleri popüler jQuery kitaplığındaki gecikme süresini gösterir. Bu ekranı açmak için Internet Explorer'da **F12** tuşuna basın ve Wi-Fi simgesiyle simgelenmiş **Ağ** sekmesini seçin.
  
![F12 Ağı'nın ekran görüntüsü.](../media/930541fd-af9b-434a-ae18-7bda867be128.png)
  
Bu ekran görüntüsü, SharePoint Online sitesinin kendisinde ana sayfa galerisine yüklenen kitaplığı gösterir. Kitaplığı karşıya yüklemek için geçen süre 1,51 saniyedir.
  
![Yükleme süresi 1,51'lerin ekran görüntüsü.](../media/64225c79-fa53-480f-81cd-0d351674320e.png)
  
İkinci ekran görüntüsü, Microsoft'un CDN tarafından sunulan dosyanın aynısını gösterir. Bu kez gecikme süresi yaklaşık 496 milisaniyedir. Bu büyük bir geliştirmedir ve nesneyi indirmek için toplam süre boyunca bir saniyenin tıraşlandığını gösterir.
  
![469 ms içindeki yükleme sürelerinin ekran görüntüsü.](../media/6a553cc3-25a0-42c1-aae7-4aebbc2eb4c3.png)

## <a name="is-my-data-safe"></a>Verilerim güvenli mi?

İşinizi yürüten verileri korumak için büyük özen gösteririz. Office 365 CDN depolanan veriler hem aktarımda hem de bekleme durumunda şifrelenir ve Office 365 SharePoint CDN veri erişimi Office 365 kullanıcı izinleri ve belirteç yetkilendirmesi ile güvenli hale getirilir. Office 365 SharePoint CDN veri isteklerinin Office 365 kiracınızdan yönlendirilmesi (yeniden yönlendirilmesi) gerekir, aksi takdirde yetkilendirme belirteci oluşturulmaz.

Verilerinizin güvenli kalmasını sağlamak için, kullanıcı içeriğini veya diğer hassas verileri hiçbir zaman genel CDN depolamamanızı öneririz. Genel CDN verilere erişim anonim olduğundan, genel CDN'ler yalnızca web betik dosyaları, simgeler, resimler ve diğer hassas olmayan varlıklar gibi genel içeriği barındırmak için kullanılmalıdır.

> [!NOTE]
> Üçüncü taraf CDN sağlayıcıları, Office 365 Güven Merkezi tarafından belirtilen taahhütlerden farklı gizlilik ve uyumluluk standartlarına sahip olabilir. CDN hizmeti aracılığıyla önbelleğe alınan veriler Microsoft Veri İşleme Koşulları'na (DPT) uymayabilir ve Office 365 Güven Merkezi uyumluluk sınırlarının dışında olabilir.

Office 365 CDN sağlayıcılarının gizlilik ve veri koruması hakkında ayrıntılı bilgi için aşağıdakileri ziyaret edin:  

- [Microsoft Güven Merkezi'nde](https://www.microsoft.com/trustcenter) gizlilik ve veri koruması Office 365 hakkında daha fazla bilgi edinin
- Akamai [Gizlilik Güven Merkezi'nde Akamai'nin](https://www.akamai.com/us/en/about/compliance/data-protection-at-akamai.jsp) gizliliği ve veri koruması hakkında daha fazla bilgi edinin
- Azure [Güven Merkezi'nde](https://azure.microsoft.com/overview/trusted-cloud/) Azure gizliliği ve veri koruması hakkında daha fazla bilgi edinin

## <a name="how-can-i-secure-my-network-with-all-these-3rd-party-services"></a>Tüm bu üçüncü taraf hizmetleriyle ağımın güvenliğini nasıl sağlayabilirim?

Kapsamlı bir iş ortağı hizmetleri kümesinden yararlanarak Office 365 kullanılabilirlik gereksinimlerini ölçeklendirebilir ve karşılayabilir ve Office 365 kullanırken kullanıcı deneyimini geliştirebilir. Office 365 3. taraf hizmetleri, crl.microsoft.com veya sa.symcb.com gibi sertifika iptal listelerini ve r3.res.outlook.com gibi CDN'leri içerir. Office 365 tarafından oluşturulan her CDN FQDN, Office 365 için özel bir FQDN'dir. Office 365 isteği üzerine bir FQDN'ye gönderilirseniz, CDN sağlayıcısının FQDN'yi ve bu konumdaki temel içeriği denetleyeceğinden emin olabilirsiniz.
  
Bir Microsoft veya Office 365 veri merkezini hedefleyen istekleri üçüncü tarafa yönelik isteklerden ayırmak isteyen müşteriler için [Office 365 uç noktalarını yönetme](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a) yönergelerini yazdık.

## <a name="is-there-a-list-of-all-the-fqdns-that-leverage-cdns"></a>CDN'lerden yararlanan tüm FQDN'lerin listesi var mı?

FQDN'lerin listesi ve CDN'lerden nasıl yararlandıkları zaman içinde değişir. CDN'lerden yararlanan en son FQDN'lerden haberdar olmak için yayımlanan [Office 365 URL'leri ve IP adresi aralıkları](./urls-and-ip-address-ranges.md) sayfamıza bakın.

Csv veya JSON olarak biçimlendirilmiş geçerli Office 365 URL'lerini ve IP adresi aralıklarını istemek için Office 365 IP [Adresi ve URL Web hizmetini](microsoft-365-ip-web-service.md) de kullanabilirsiniz.

## <a name="can-i-use-my-own-cdn-and-cache-content-on-my-local-network"></a>Kendi CDN kullanabilir ve yerel ağımda içeriği önbelleğe alabilir miyim?

Müşterilerimizin ihtiyaçlarını desteklemek için sürekli yeni yollar arıyoruz ve şu anda önbelleğe alma proxy çözümlerinin ve diğer şirket içi CDN çözümlerinin kullanımını araştırıyoruz.

Office 365 CDN bir parçası olmasa da, CDN depolama alanınıza erişim anahtarları uygulamanıza ve **CDN** yapılandırmanız üzerinde daha fazla denetime sahip olmanıza olanak tanıyan özel web bölümlerini, kitaplıkları ve diğer kaynak varlıklarını barındırmak için de Azure CDN kullanabilirsiniz. Azure CDN kullanımı ücretsiz değildir ve Bir Azure aboneliği gerektirir. Azure CDN örneği yapılandırma hakkında daha fazla bilgi için bkz[. Hızlı Başlangıç: Azure depolama hesabını Azure CDN ile tümleştirme](/azure/cdn/cdn-create-a-storage-account-with-cdn).

## <a name="im-using-azure-expressroute-for-office-365-does-that-change-things"></a>Office 365 için Azure ExpressRoute kullanıyorum, bu bir şeyleri değiştiriyor mu?

[Office 365 için Azure ExpressRoute](azure-expressroute.md), genel İnternet'ten ayrılmış Office 365 altyapısına ayrılmış bir bağlantı sağlar. Bu, istemcilerin ExpressRoute tarafından desteklenen hizmetler listesine açıkça dahil edilmeyen CDN'lere ve diğer Microsoft altyapısına bağlanmak için ExpressRoute olmayan bağlantılar üzerinden bağlanmaları gerekeceği anlamına gelir. CDN'leri hedefleyen istekler gibi belirli trafiği yönlendirme hakkında daha fazla bilgi için [ağ trafiği yönetimini Office 365](routing-with-expressroute.md) konusuna bakın.

## <a name="can-i-use-cdns-with-sharepoint-server-on-premises"></a>CDN'leri şirket içi SharePoint Sunucusu ile kullanabilir miyim?

CDN'lerin kullanılması yalnızca SharePoint Çevrimiçi bağlamında anlamlıdır ve SharePoint Server ile bundan kaçınılmalıdır. Bunun nedeni, sunucunun şirket içinde veya coğrafi olarak yakın olması durumunda coğrafi konumla ilgili tüm avantajların geçerli olmamasıdır. Ayrıca, barındırıldığı sunuculara bir ağ bağlantısı varsa, site İnternet bağlantısı olmadan kullanılabilir ve bu nedenle CDN dosyalarını alamaz. Aksi takdirde, siteniz için ihtiyacınız olan kitaplık ve dosyalar için kullanılabilir ve kararlı bir CDN kullanmanız gerekir.
  
İşte geri dönmek için kullanabileceğiniz kısa bir bağlantı: [https://aka.ms/o365cdns]()
  
## <a name="see-also"></a>Ayrıca bkz.

[Office 365 Ağ Bağlantı İlkeleri](./microsoft-365-network-connectivity-principles.md)

[Office 365 ağ bağlantısını değerlendirme](assessing-network-connectivity.md)

[Office 365 uç noktalarını yönetme](managing-office-365-endpoints.md)

[Office 365 URL'leri ve IP adresi aralıkları](./urls-and-ip-address-ranges.md)

[SharePoint Online ile Office 365 içerik teslim ağını kullanma](use-microsoft-365-cdn-with-spo.md)

[Microsoft Güven Merkezi](https://www.microsoft.com/trustcenter)

[Office 365 performansını ayarlama](tune-microsoft-365-performance.md)
