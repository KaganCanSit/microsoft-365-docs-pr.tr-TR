---
title: Microsoft 365 Bağlantısına Genel Bakış
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: SaaS hizmetleri için ağ iyileştirmenin neden önemli olduğu, ağ Microsoft 365 ve SaaS'ın diğer iş yüklerinden farklı ağ ağlarını nasıl gerektirdiği hakkında tartışıldı.
ms.openlocfilehash: e5dcbae5a1fbac3b0b4fd4472fdcac2380b84382
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62988732"
---
# <a name="microsoft-365-network-connectivity-overview"></a>Microsoft 365 bağlantısına genel bakış

*Bu makale hem son hem de Microsoft 365 Kurumsal hem de Office 365 Kurumsal.*

Microsoft 365, farklı bir mikro hizmetler ve uygulamalar kümesi aracılığıyla üretkenlik ve işbirliği senaryoları sağlayan, dağıtılmış bir Hizmet Olarak Yazılım (SaaS) bulutudur. Microsoft 365, Word Outlook gibi istemci bileşenleri PowerPoint kullanıcı bilgisayarlarında çalışır ve Microsoft veri Microsoft 365'de çalıştıran diğer bileşenlerine bağlanabilirsiniz. Microsoft 365 son kullanıcı deneyiminin kalitesini belirleyen en önemli faktör, Microsoft 365 istemcileri ile Microsoft 365 ön kapıları arasındaki ağ güvenilirliği ve düşük gecikme süresidir.

Bu makalede, ağ oluşturmanın hedefleri ve Microsoft 365 ağlarının iyileştirme için genel İnternet Microsoft 365 göre neden farklı bir yaklaşım gerektirdiğini öğrenirsiniz.

## <a name="microsoft-365-networking-goals"></a>Microsoft 365 ağ hedeflerini oluşturma

Ağ oluşturmanın en Microsoft 365 hedefi, istemciler ve en yakın istemci uç noktaları arasında en az kısıtlayıcı erişimi etkinleştirerek son kullanıcı Microsoft 365 iyileştirmektir. Son kullanıcı deneyiminin kalitesi, doğrudan kullanıcının kullanmakta olduğu uygulamanın performansı ve yanıt süresiyle ilgilidir. Örneğin, Microsoft Teams kullanıcı telefon görüşmeleri, konferanslar ve paylaşılan ekran işbirliğinin hatasız olması için düşük gecikme süresine dayandırılır ve Outlook sunucu tarafı dizin oluşturma ve AI özelliklerini uygulayan hızlı arama özellikleri için mükemmel ağ bağlantısına dayandırılır.

Ağ tasarımında temel amaç, istemci makinelerinden Microsoft Global Network'e gidiş dönüş süresini (RTT) azaltarak gecikmeyi en aza indirmek ve Microsoft'un tüm veri merkezleriyle düşük gecikmeli, yüksek kullanılabilir bulut uygulaması giriş noktaları arasında bağlantı oluşturan genel ağ omurgasını tüm dünyaya yaymaktır. Microsoft'un hızlı ve güvenilir global ağı oluşturması [bağlantısında Microsoft Genel Ağ hakkında daha fazla bilgi öğrenebilirsiniz](https://azure.microsoft.com/blog/how-microsoft-builds-its-fast-and-reliable-global-network/).

Ağ Microsoft 365 iyileştirmenin karmaşık olması gerek değildir. Birkaç temel ilkeyi kullanarak mümkün olan en iyi performansı elde etmek için:

- Ağ Microsoft 365 tanımlama
- Kullanıcıların ağ trafiğine bağlanıyor Microsoft 365 konumdan İnternet'e gelen yerel ağ trafiğine izin Microsoft 365
- Geçiş Microsoft 365 aracıları ve paket denetleme cihazlarını atlamasına izin ver

Ağ bağlantısı ilkeleri hakkında daha Microsoft 365 için bkz. Ağ [Microsoft 365 İlkeleri](microsoft-365-network-connectivity-principles.md).

## <a name="traditional-network-architectures-and-saas"></a>Geleneksel ağ mimarileri ve SaaS

İstemci/sunucu iş yükleri için geleneksel ağ mimarisi ilkeleri, istemciler ve uç noktalar arasındaki trafiğin şirket ağ çevresini dışına çıkarama varsayımı ile tasarlanmıştır. Ayrıca, birçok kurumsal ağda, tüm giden İnternet bağlantıları şirket ağına çapraz geçiş ve merkezi bir konumdan çıkış sağlar.

Geleneksel ağ mimarilerde, genel İnternet trafiğinde daha yüksek gecikme süresi, ağ çevre güvenliğini korumak için gereken bir işlemdir ve İnternet trafiği için performans iyileştirme, genellikle ağ çıkış noktalarında donanımın yükseltilmesi veya ölçeklendirilmesi içerir. Ancak bu yaklaşım, saas gibi SaaS hizmetlerinin en uygun ağ performansı gereksinimlerini Microsoft 365.

## <a name="identifying-microsoft-365-network-traffic"></a>Ağ Microsoft 365 tanımlama

Ağ trafiğini tanımlamayı ve ağ Microsoft 365 yönetmeyi kolaylaştırıyoruz.

- Üst düzeyde kritik ağ trafiğini İnternet gecikmelerinden etkilenmez ağ trafiğinden ayırt etmek için ağ uç noktaları yeni kategorileri. En kritik "En İyi Duruma Getirme" kategorisinde yalnızca birkaç URL ve DESTEKLENEN IP Adresi var.
- Komut dosyası kullanımına veya doğrudan cihaz yapılandırmasına ve kullanıcı ağı kimliğinin Microsoft 365 web hizmetleri. Değişiklikler web hizmeti veya RSS biçiminde ya da bir şablon kullanarak e-postada Microsoft Flow kullanılabilir.
- [Office 365 bağlantı ilkelerine uygun ve](./microsoft-365-networking-partner-program.md) basit yapılandırmaya sahip cihazlar veya hizmetler sağlayan Microsoft Microsoft 365 iş ortağı programıdır.

## <a name="securing-microsoft-365-connections"></a>Microsoft 365 bağlantılarının güvenliğini sağlama

Geleneksel ağ güvenliğinin amacı izinsiz giriş ve kötü amaçlı istismarlara karşı şirket ağ çevresini güvenliğini hedeflemektir. Kurumsal ağların çoğu, ara sunucu, güvenlik duvarı, SSL sonu ve incele, derin paket incelemesi ve veri kaybı önleme sistemleri gibi teknolojileri kullanarak İnternet trafiğinde ağ güvenliğini zorunlu oluşturur. Bu teknolojiler genel İnternet istekleri için önemli risk azaltmaları sağlar, ancak Microsoft 365 uç noktalarına uygulandığında performansı, ölçeklenebilirliği ve son kullanıcı deneyiminin kalitesini önemli ölçüde azaltır.

Microsoft 365, özel olarak güvenlik özellikleri ve iş yükleri için tasarlanmış yerleşik güvenlik ve yönetim özellikleriyle, kuruluş içerik güvenliği ve veri kullanımı uyumluluğuyla ilgili ihtiyaçlarını karşılamaya Microsoft 365 yardımcı olur. Güvenlik ve uyumluluğu Microsoft 365 daha fazla bilgi için güvenlik [Office 365 bakın](/office365/securitycompliance/security-roadmap). Microsoft'un Microsoft 365 trafiği üzerinde gelişmiş düzeyde işlem gerçekleştiren gelişmiş ağ çözümlerine ilişkin önerileri ve destek konumu hakkında daha fazla bilgi için bkz. Üçüncü taraf ağ cihazlarını veya çözümlerini Office 365 [kullanma](https://support.microsoft.com/help/2690045).

## <a name="why-is-microsoft-365-networking-different"></a>Ağ Microsoft 365 farklı?

Microsoft 365 noktası güvenliği ve şifrelenmiş ağ bağlantıları kullanılarak en iyi performans için tasarlanmıştır ve çevre güvenliği zorlama ihtiyacı azaltıldı. Microsoft 365 olan veri merkezleri dünya genelinde bulunur ve hizmet, istemcileri en iyi kullanılabilir hizmet uç noktalarına bağlamak için çeşitli yöntemler kullanmak üzere tasarlanmıştır. Kullanıcı verileri ve işleme birçok Microsoft veri merkezi arasında dağıtıldığından, istemci makinelerinin bağlan bağlana bile olduğu tek bir ağ uç noktası yoktur. Aslında, kiracınız olan Microsoft 365 ve hizmetler Microsoft Global Network tarafından son kullanıcılar tarafından erişilemedikleri coğrafi konumlara göre dinamik olarak en iyi duruma getirilmiş olur.

Trafiğin paket incelemesine ve merkezi Microsoft 365 çıkışa tabi olduğunda bazı genel performans sorunları oluşturulur:

- Yüksek gecikme süresi video ve ses akışlarının düşük performansına, veri alma, aramalar, gerçek zamanlı işbirliği, takvim serbest/meşgul bilgisi, ürün içeriği ve diğer hizmetlerin yavaş yanıtlarına neden olabilir
- Merkezi bir konumdan çıkış bağlantıları, genel ağın dinamik yönlendirme özelliklerini Microsoft 365, buna gecikme ve gidiş dönüş süresi ekler
- Güvenli SSL güvenlik Microsoft 365 çözme ve bu trafiği yeniden şifreleme, protokol hatalarına neden olabilir ve güvenlik riski vardır

İstemci trafiğinin coğrafi Microsoft 365 konumlarına mümkün olduğunca yakın çıkışa izin vererek bu ağ yolu girdi noktalarının kısaltılması, bağlantı performansını ve son kullanıcı deneyimini Microsoft 365. Ayrıca, ağ mimarisinde gelecek değişikliklerin performans ve güvenilirlik üzerindeki etkisini azaltmaya Microsoft 365 yardımcı olabilir. En uygun bağlantı modeli, ister şirket ağına ister ev, oteller, kafe mağazaları ve havalimanları gibi uzak konumlara olsun, kullanıcının bulunduğu konumda ağ çıkışlarını sağlamaktır. Genel İnternet trafiği ve WAN tabanlı şirket ağ trafiği ayrı ayrı yönlendirilebilir ve yerel doğrudan çıkış modeli kullanılabilir. Bu yerel doğrudan çıkış modeli aşağıdaki diyagramda gösterilmiştir.

![Yerel çıkış ağı mimarisi.](../media/6bc636b0-1234-4ceb-a45a-aadd1044b39c.png)

Yerel çıkış mimarisi, ağ trafiğini geleneksel model üzerinden Microsoft 365 için aşağıdaki avantajlara sahiptir:
  
- Yönlendirme uzunluğunu Microsoft 365 iyi bir performans sağlar. Son kullanıcı bağlantıları Microsoft Global Network'in Dağıtılmış Hizmet _Ön_ Kapı altyapısı tarafından en yakın Microsoft 365 giriş noktasına dinamik olarak yönlendirilen ve trafik de Microsoft'un ultra düşük gecikme süresi fiber kaynağı üzerinden dahili olarak verilere ve hizmet uç noktalarına yönlendir edilir.
- Aracıları ve trafik denetleme cihazlarını atlayarak, şirket Microsoft 365 çıkışa izin vererek şirket ağ altyapısının yükünü azaltır.
- İstemci uç noktası güvenliği ve bulut güvenlik özellikleri uygulayarak, yedekli ağ güvenlik teknolojileri uygulamasından kaçınarak her iki uçta bağlantıların güvenliğini sağlar.

> [!NOTE]
> Dağıtılmış _Hizmet Ön Kapı altyapısı_ , coğrafi olarak dağıtılmış konumlara sahip Microsoft Global Network'un yüksek düzeyde kullanılabilir ve ölçeklendirilebilir ağ kenarıdır. Son kullanıcı bağlantılarını sonlandırılır ve bunları Microsoft Genel Ağı içinde etkili bir şekilde yönlendirer. Microsoft'un hızlı ve güvenilir global ağı oluşturması [bağlantısında Microsoft Genel Ağ hakkında daha fazla bilgi öğrenebilirsiniz](https://azure.microsoft.com/blog/how-microsoft-builds-its-fast-and-reliable-global-network/).

Ağ bağlantısı ilkeleri hakkında daha fazla bilgi Microsoft 365 hakkında daha fazla bilgi için ağ Bağlantısı [Microsoft 365 ilkeler'e bakın](microsoft-365-network-connectivity-principles.md).

## <a name="conclusion"></a>Sonuç

Ağ Microsoft 365 iyileştirme, gereksiz gereksiz gerekliliklerin ortadan kaldırılmasına gerçekten neden olur. Tek tek Microsoft 365 güvenli trafik olarak ele alınarak, paket incelemesi ve proxy bant genişliği için rekabet nedeniyle gecikme süresinin önüne geçebileceksiniz. İstemci makineleriyle uç noktalar arasında yerel Office 365 izin verme, trafiğin Microsoft Global Network üzerinden dinamik olarak yönlendirilene kadar devamsını sağlar.

## <a name="related-topics"></a>İlgili Konular

[Microsoft 365 Ağ Bağlantısı İlkeleri](microsoft-365-network-connectivity-principles.md)

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
