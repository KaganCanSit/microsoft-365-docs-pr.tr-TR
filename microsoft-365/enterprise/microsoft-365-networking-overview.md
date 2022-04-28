---
title: Microsoft 365 Ağ Bağlantısına Genel Bakış
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 08/27/2021
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- m365initiative-coredeploy
f1.keywords:
- NOCSH
description: SaaS hizmetleri için ağ iyileştirmenin neden önemli olduğunu, Microsoft 365 ağ oluşturma hedefini ve SaaS'ın diğer iş yüklerinden farklı ağ gerektirmesini açıklar.
ms.openlocfilehash: 64af558653ff57e91068d2e028235b73c165376b
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65096776"
---
# <a name="microsoft-365-network-connectivity-overview"></a>ağ bağlantısına genel bakış Microsoft 365

*Bu makale hem Microsoft 365 Kurumsal hem de Office 365 Kurumsal için geçerlidir.*

Microsoft 365, çeşitli mikro hizmetler ve uygulamalar aracılığıyla üretkenlik ve işbirliği senaryoları sağlayan dağıtılmış bir Hizmet Olarak Yazılım (SaaS) bulutudur. Outlook, Word ve PowerPoint gibi Microsoft 365 istemci bileşenleri kullanıcı bilgisayarlarda çalışır ve Microsoft veri merkezlerinde çalışan diğer Microsoft 365 bileşenlerine bağlanır. Microsoft 365 son kullanıcı deneyiminin kalitesini belirleyen en önemli faktör, Microsoft 365 istemcileri ile Microsoft 365 hizmet ön kapıları arasındaki ağ güvenilirliği ve düşük gecikme süresidir.

Bu makalede, Microsoft 365 ağın hedefleri ve Microsoft 365 ağın neden genel İnternet trafiğinden farklı bir iyileştirme yaklaşımı gerektirdiği hakkında bilgi edineceksiniz.

## <a name="microsoft-365-networking-goals"></a>ağ hedeflerini Microsoft 365

Microsoft 365 ağın nihai hedefi, istemciler ve en yakın Microsoft 365 uç noktaları arasında en az kısıtlayıcı erişimi etkinleştirerek son kullanıcı deneyimini iyileştirmektir. Son kullanıcı deneyiminin kalitesi, kullanıcının kullandığı uygulamanın performansı ve yanıt hızıyla doğrudan ilgilidir. Örneğin Microsoft Teams, kullanıcı telefon aramalarının, konferansların ve paylaşılan ekran işbirliklerinin sorunsuz olması ve Outlook sunucu tarafı dizin oluşturma ve yapay zeka özellikleri uygulayan anlık arama özellikleri için harika ağ bağlantısına bağlı olması için düşük gecikme süresine dayanır.

Ağ tasarımındaki birincil hedef, istemci makinelerden Microsoft'un tüm veri merkezlerine düşük gecikme süresi ve yüksek kullanılabilirlik içeren bulut uygulaması giriş noktaları arasında bağlantı sağlayan microsoft genel ağ omurgası olan Microsoft Global Network'e gidiş dönüş süresini (RTT) azaltarak gecikme süresini en aza indirmek olmalıdır. Microsoft Global Network hakkında daha fazla bilgi edinmek için [Microsoft'un hızlı ve güvenilir küresel ağını oluşturmasını](https://azure.microsoft.com/blog/how-microsoft-builds-its-fast-and-reliable-global-network/) sağlayabilirsiniz.

Microsoft 365 ağ performansını iyileştirmenin karmaşık olması gerekmez. Birkaç temel ilkeyi izleyerek mümkün olan en iyi performansı elde edebilirsiniz:

- Microsoft 365 ağ trafiğini tanımlama
- Kullanıcıların Microsoft 365 bağlandığı her konumdan İnternet'e Microsoft 365 ağ trafiğinin yerel dal çıkışına izin ver
- Microsoft 365 trafiğinin proxy'leri ve paket denetleme cihazlarını atlamasına izin ver

Microsoft 365 ağ bağlantı ilkeleri hakkında daha fazla bilgi için bkz. [Ağ Bağlantı İlkeleri'Microsoft 365](microsoft-365-network-connectivity-principles.md).

## <a name="traditional-network-architectures-and-saas"></a>Geleneksel ağ mimarileri ve SaaS

İstemci/sunucu iş yükleri için geleneksel ağ mimarisi ilkeleri, istemciler ve uç noktalar arasındaki trafiğin kurumsal ağ çevresi dışında genişletilmediği varsayımı doğrultusunda tasarlanmıştır. Ayrıca, birçok kurumsal ağda, tüm giden İnternet bağlantıları şirket ağından ve merkezi bir konumdan çıkar.

Geleneksel ağ mimarilerinde, genel İnternet trafiği için daha yüksek gecikme süresi, ağ çevre güvenliğini korumak için gerekli bir dengedir ve İnternet trafiği için performans iyileştirmesi genellikle ağ çıkış noktalarında ekipmanı yükseltmeyi veya ölçeği genişletmeyi içerir. Ancak bu yaklaşım, Microsoft 365 gibi SaaS hizmetlerinin en iyi ağ performansı gereksinimlerini karşılamaz.

## <a name="identifying-microsoft-365-network-traffic"></a>Microsoft 365 ağ trafiğini tanımlama

Ağ trafiğinin Microsoft 365 tanımlanmasını kolaylaştırıyoruz ve ağ tanımlamasını yönetmeyi kolaylaştırıyoruz.

- Son derece kritik ağ trafiğini İnternet gecikmelerinden etkilenmeyen ağ trafiğinden ayırt etmek için yeni ağ uç noktaları kategorileri. En kritik "İyileştir" kategorisinde yalnızca birkaç URL ve destekleyici IP Adresi vardır.
- Betik kullanımı veya doğrudan cihaz yapılandırması ve Microsoft 365 ağ tanımlamasının değişiklik yönetimi için web hizmetleri. Değişiklikler web hizmetinden veya RSS biçiminde ya da Microsoft Flow şablonu kullanılarak e-postada kullanılabilir.
- Microsoft 365 ağ bağlantısı ilkelerine uygun ve basit yapılandırmaya sahip cihazlar veya hizmetler sağlayan Microsoft iş ortaklarıyla Office 365 Ağ [iş ortağı programı](./microsoft-365-networking-partner-program.md).

## <a name="securing-microsoft-365-connections"></a>Microsoft 365 bağlantılarının güvenliğini sağlama

Geleneksel ağ güvenliğinin amacı, şirket ağ çevresini yetkisiz erişime ve kötü amaçlı açıklara karşı sağlamlaştırmaktır. Çoğu kurumsal ağ, proxy sunucuları, güvenlik duvarları, SSL kesme ve inceleme, derin paket incelemesi ve veri kaybı önleme sistemleri gibi teknolojileri kullanarak İnternet trafiği için ağ güvenliğini zorunlu kılır. Bu teknolojiler, genel İnternet istekleri için önemli risk azaltma sağlar ancak Microsoft 365 uç noktalarına uygulandığında performansı, ölçeklenebilirliği ve son kullanıcı deneyiminin kalitesini önemli ölçüde azaltabilir.

Microsoft 365, özel olarak Microsoft 365 özellikleri ve iş yükleri için tasarlanmış yerleşik güvenlik ve idare özellikleriyle kuruluşunuzun içerik güvenliği ve veri kullanımı uyumluluğu gereksinimlerini karşılamaya yardımcı olur. Microsoft 365 güvenlik ve uyumluluk hakkında daha fazla bilgi için [Office 365 güvenlik yol haritasına](/office365/securitycompliance/security-roadmap) bakın. Microsoft'un Microsoft 365 trafiğinde gelişmiş düzey işleme gerçekleştiren gelişmiş ağ çözümleriyle ilgili önerileri ve destek konumu hakkında daha fazla bilgi için bkz. [Office 365 trafiğinde üçüncü taraf ağ cihazlarını veya çözümlerini kullanma](https://support.microsoft.com/help/2690045).

## <a name="why-is-microsoft-365-networking-different"></a>Microsoft 365 ağı neden farklı?

Microsoft 365 uç nokta güvenliği ve şifrelenmiş ağ bağlantıları kullanılarak en iyi performans için tasarlanmıştır ve çevre güvenliği uygulama gereksinimini azaltır. Microsoft 365 veri merkezleri dünyanın farklı yerlerinde bulunur ve hizmet, istemcileri en iyi kullanılabilir hizmet uç noktalarına bağlamak için çeşitli yöntemler kullanmak üzere tasarlanmıştır. Kullanıcı verileri ve işleme birçok Microsoft veri merkezi arasında dağıtıldığından, istemci makinelerin bağlanabileceği tek bir ağ uç noktası yoktur. Aslında, Microsoft 365 kiracınızdaki veriler ve hizmetler, son kullanıcılar tarafından erişildiği coğrafi konumlara uyum sağlamak için Microsoft Global Network tarafından dinamik olarak iyileştirilmiştir.

Microsoft 365 trafiği paket incelemesine ve merkezi çıkışa tabi olduğunda bazı yaygın performans sorunları oluşturulur:

- Yüksek gecikme süresi, video ve ses akışlarının düşük performansına ve veri alma, aramalar, gerçek zamanlı işbirliği, takvim serbest/meşgul bilgileri, ürün içi içerik ve diğer hizmetlerin yavaş yanıtlamasına neden olabilir
- Merkezi bir konumdan çıkış bağlantıları, Microsoft 365 genel ağının dinamik yönlendirme özelliklerini bozarak gecikme süresi ve gidiş dönüş süresi ekler
- SSL güvenli Microsoft 365 ağ trafiğinin şifresini çözmek ve yeniden şifrelemek protokol hatalarıyla neden olabilir ve güvenlik riski vardır

İstemci trafiğinin coğrafi konumlarına mümkün olduğunca yakın şekilde çıkış yapmalarına izin vererek ağ yolunu Microsoft 365 giriş noktalarına kısaltmak, Microsoft 365 bağlantı performansını ve son kullanıcı deneyimini iyileştirebilir. Ayrıca, gelecekte ağ mimarisinde yapılan değişikliklerin Microsoft 365 performans ve güvenilirlik üzerindeki etkisini azaltmaya da yardımcı olabilir. En uygun bağlantı modeli, bunun şirket ağında veya ev, otel, kafe ve havaalanları gibi uzak konumlarda olmasına bakılmaksızın her zaman kullanıcının konumunda ağ çıkışı sağlamaktır. Genel İnternet trafiği ve WAN tabanlı kurumsal ağ trafiği ayrı olarak yönlendirilebilir ve yerel doğrudan çıkış modelini kullanmaz. Bu yerel doğrudan çıkış modeli aşağıdaki diyagramda gösterilmiştir.

![Yerel çıkış ağ mimarisi.](../media/6bc636b0-1234-4ceb-a45a-aadd1044b39c.png)

Yerel çıkış mimarisi, geleneksel model üzerinden Microsoft 365 ağ trafiği için aşağıdaki avantajlara sahiptir:
  
- Yol uzunluğunu iyileştirerek en iyi Microsoft 365 performansı sağlar. Son kullanıcı bağlantıları, Microsoft Global _Network'ün Dağıtılmış Hizmet Front Door_ altyapısı tarafından dinamik olarak en yakın Microsoft 365 giriş noktasına yönlendirilir ve trafik daha sonra Microsoft'un ultra düşük gecikme süreli yüksek kullanılabilirlik fiberi üzerinden veri ve hizmet uç noktalarına dahili olarak yönlendirilir.
- Proxy'leri ve trafik denetleme cihazlarını atlayarak Microsoft 365 trafik için yerel çıkışa izin vererek kurumsal ağ altyapısındaki yükü azaltır.
- İstemci uç noktası güvenliği ve bulut güvenliği özellikleri uygulayarak, yedekli ağ güvenlik teknolojilerinin uygulanmasını önleyerek her iki uçta da bağlantıların güvenliğini sağlar.

> [!NOTE]
> _Dağıtılmış Hizmet Front Door_ altyapısı, Microsoft Global Network'ün coğrafi olarak dağıtılmış konumlara sahip yüksek oranda kullanılabilir ve ölçeklenebilir ağ kenarıdır. Son kullanıcı bağlantılarını sonlandırır ve bunları Microsoft Global Network içinde verimli bir şekilde yönlendirir. Microsoft Global Network hakkında daha fazla bilgi edinmek için [Microsoft'un hızlı ve güvenilir küresel ağını oluşturmasını](https://azure.microsoft.com/blog/how-microsoft-builds-its-fast-and-reliable-global-network/) sağlayabilirsiniz.

Microsoft 365 ağ bağlantısı ilkelerini anlama ve uygulama hakkında daha fazla bilgi için bkz. [Ağ Bağlantısı İlkeleri Microsoft 365](microsoft-365-network-connectivity-principles.md).

## <a name="conclusion"></a>Sonuç

Microsoft 365 ağ performansını iyileştirmek, gereksiz engelleri ortadan kaldırmaya neden olur. Microsoft 365 bağlantıları güvenilir trafik olarak değerlendirerek, paket denetimi ve ara sunucu bant genişliği rekabeti ile gecikme süresinin ortaya çıkmasını önleyebilirsiniz. İstemci makineleriyle Office 365 uç noktaları arasında yerel bağlantılara izin vermek, trafiğin Microsoft Genel Ağ üzerinden dinamik olarak yönlendirilmesine olanak tanır.

## <a name="related-topics"></a>İlgili Konular

[ağ bağlantısı ilkelerini Microsoft 365](microsoft-365-network-connectivity-principles.md)

[Office 365 uç noktalarını yönetme](managing-office-365-endpoints.md)

[Office 365 URL'leri ve IP adresi aralıkları](urls-and-ip-address-ranges.md)

[Office 365 IP Adresi ve URL Web hizmeti](microsoft-365-ip-web-service.md)

[Microsoft 365 ağ bağlantısını değerlendirme](assessing-network-connectivity.md)

[Microsoft 365 için ağ planlama ve performans ayarlama](network-planning-and-performance.md)

[Temelleri ve performans geçmişini kullanarak performans ayarlamayı Office 365](performance-tuning-using-baselines-and-history.md)

[Office 365 için performans sorunlarını giderme planı](performance-troubleshooting-plan.md)

[İçerik Teslim Ağları](content-delivery-networks.md)

[Microsoft 365 bağlantı testi](https://aka.ms/netonboard)

[Microsoft hızlı ve güvenilir küresel ağını nasıl oluşturur?](https://azure.microsoft.com/blog/how-microsoft-builds-its-fast-and-reliable-global-network/)

[Office 365 Ağ blogu](https://techcommunity.microsoft.com/t5/Office-365-Networking/bd-p/Office365Networking)
