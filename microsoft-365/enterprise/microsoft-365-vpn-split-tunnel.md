---
title: 'Genel bakış: VPN bölme bölme Microsoft 365'
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 3/3/2022
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- remotework
- m365initiative-coredeploy
f1.keywords:
- NOCSH
description: Uzak kullanıcılar için bağlantıları en iyi duruma getirmek Microsoft 365 ile VPN bölünmüş bölmelerine genel bakış.
ms.openlocfilehash: 67ce8a38b536dab12af679ba860aac6d974db60e
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63329079"
---
# <a name="overview-vpn-split-tunneling-for-microsoft-365"></a>Genel bakış: VPN bölme bölme Microsoft 365

>[!NOTE]
>Bu makale, uzak kullanıcılar için iyileştirmeyi Microsoft 365 makale kümelerinin bir bölümüdir.

>- VPN bölünmüş bölmeyi uygulama hakkında ayrıntılı kılavuz için bkz. [VPN bölünmüş bölmeyi uygulama Microsoft 365](microsoft-365-vpn-implement-split-tunnel.md).
>- VPN bölünmüş bölme senaryolarının ayrıntılı listesi için bkz. Daha fazla bilgi için bkz. Genel [VPN bölünmüş Microsoft 365](microsoft-365-vpn-common-scenarios.md).
>- VPN bölünmüş trafiğinde Teams trafiğinin güvenliğini sağlama kılavuzu için bkz. VPN bölünmüş trafiği için Teams trafiğinin güvenliğini [sağlama](microsoft-365-vpn-securing-teams.md).
>- VPN ortamlarında Stream ve canlı etkinlikleri yapılandırma hakkında bilgi için bkz. VPN ortamlarında akış ve canlı etkinlikler [için dikkat edilmesi gereken noktalar](microsoft-365-vpn-stream-and-live-events.md).
>- Çin'deki kullanıcılar için Microsoft 365 kiracı performansını iyileştirme hakkında bilgi için bkz. [Microsoft 365 için performans iyileştirme.](microsoft-365-networking-china.md)

Kuruluşlar, geleneksel olarak kullanıcıları için güvenli uzak deneyimleri desteklemek üzere VPN'ler kullanmaktadır. Temel iş yükleri şirket içinde kalırken, uzak kullanıcıların şirket kaynaklarına erişmesi için birincil yöntem, şirket ağının veri merkezi aracılığıyla yönlendirilen uzak istemciden VPN'tir. Kuruluşlar bu bağlantıları korumak için VPN yolları boyunca ağ güvenlik çözümlerinin katmanlarını oluşturmaz. Bu güvenlik, iç altyapıyı korumak ve trafiği VPN'ye yeniden yönlendirerek ve sonra da şirket içi İnternet çevresi üzerinden dışarı doğru yönlendirerek dış web sitelerini mobil taramayı korumak için yerleşik olarak kullanılır. VPN'ler, ağ çevreleri ve ilişkili güvenlik altyapısı genellikle amaca yönelik olarak yerleşik ve tanımlı bir trafik hacmi için ölçeklendirildi; bunlar genellikle çoğu bağlantı şirket ağının içinde ve büyük bir çoğu da iç ağ sınırları içinde kalıyor.

Bir süredir, uzak kullanıcı cihazından gelen tüm bağlantıların şirket içi ağa geri yönlendirdiği VPN modelleri (zorlamalı kaza olarak _bilinir), uzak_ kullanıcıların eş zamanlı ölçeği normal olduğu ve VPN'den çapraz geçen trafik hacminin düşük olduğu sürece büyük ölçüde sürdürülebilirdi.  Bazı müşteriler, uygulamaları şirket çevresi içinden genel SaaS bulutlarına taşındıktan sonra bile VPN zorlamasını status quo olarak kullanmaya devam etti.

Dağıtılmış ve performansa duyarlı bulut uygulamalarına bağlanmak için zorlamalı VPN'lerin kullanımı alt bir uygulamadır, ancak güvenlik durumu güvenliğinin korunması için bazı kuruluşlar bunu kabul eder. Bu senaryoya örnek bir diyagram aşağıdan görülebilir:

![VPN Tunnel zorunlu.](../media/vpn-split-tunneling/enterprise-network-traditional.png)

_Şekil 1: Geleneksel Zorunlu vpn Tunnel çözümü._

Birçok müşteri ağ trafiği desenlerinin önemli bir değişimini raporlamaktadır ve bu sorun yıllar boyunca büyüyen bir sorundur. Şirket içinde kalmak için kullanılan trafik artık dış bulut uç noktalarına bağlanır. Birçok Microsoft müşterisi, daha önce ağ trafiğinin yaklaşık %80'inin bir iç kaynakta (yukarıdaki diyagramda noktalı çizgiyle gösterildiği) olduğunu bildirmiştir. 2020'de bu sayı, büyük iş yüklerini buluta kaydırarak yaklaşık %20 veya daha düşük bir sayıya düşürdü. Bu eğilimler diğer kuruluşlarda az görülen bir eğilim değildir. Bulut yolculuğu ilerledikçe yukarıdaki model giderek zahmetli ve zahmetsiz hale gelir ve kuruluşun ilk bulut dünyasında çevik olması önlenebilir hale gelir.

Dünya çapında COVID-19 krizi bu sorunu acil düzeltme gerektirecek şekilde İlerledi. Kurumsal IT üzerinde, ev dışından üretkenliği muazzam bir ölçekte desteklemek için çalışan güvenliğinin sağlanmasıyla ilgili talepler üretmektedir. Microsoft 365 müşterilerin bu talebi karşılamalarına yardımcı olmak için iyi bir konumdadır, ancak evden çalışan kullanıcıların yüksek eşzamanlılığı nedeniyle zorunlu VPN ve şirket içi ağ çevrelerine yönlendirilen çok büyük miktarda Microsoft 365 trafiği, doygunluğa neden olur ve VPN altyapısını kapasitenin dışında çalıştırır. Bu yeni gerçeklikte, Microsoft 365'e erişmek için VPN kullanmak artık yalnızca bir performans taadı değildir; yalnızca Microsoft 365'ı değil, aynı zamanda vpn'in çalışması için güvenmek zorunda olduğu kritik iş işlemlerini de etkileyen sıkı bir duvardır.

Microsoft, kendi hizmetlerimizden bu sorunlara etkili ve modern çözümler sunmak ve endüstrinin en iyi uygulamasıyla uyumlu olmak için müşterilerle ve daha geniş bir endüstriyle birlikte çalışıyor. [Yeni Hizmet Hizmeti'Microsoft 365](./microsoft-365-network-connectivity-principles.md) bağlantı ilkeleri, kuruluşun bağlantı üzerinde güvenlik ve denetime sahip çalışmasına olanak sağlarken, uzak kullanıcılar için etkili bir şekilde çalışacak şekilde tasarlanmıştır. Bu çözümler sınırlı çalışmayla da hızlı bir şekilde uygulanarak, yine de yukarıda belirtilen sorunlar üzerinde önemli olumlu bir etki elde edildi.

Uzaktan çalışan cihazlarını VPN üzerinden şirket ağına veya bulut altyapısına bağlamak isteyen müşteriler için Microsoft, Microsoft 365, **Microsoft Teams SharePoint** **Online** ve **Exchange Online** gibi önemli Microsoft 365 senaryolarının _VPN_ bölünmüş yapılandırmaları üzerinden yönlendirilmez. COVID-19 kriz gibi evden gelen büyük ölçekli etkinlikler sırasında çalışan üretkenliğinin devamını kolaylaştıran ilk satır stratejisi olarak bu durum özellikle önemli hale gelir.

![VPN Tunnel bölün.](../media/vpn-split-tunneling/vpn-model-2.png)

_Şekil 2: Doğrudan hizmete gönderilen tanımlı veya özel Microsoft 365 VPN bölünmüş olay çözümü. Diğer tüm trafik hedeften bağımsız olarak VPN trafiği üzerinden çapraz geçiş yaptı._

Bu yaklaşımın özünü, kuruluşlara VPN altyapısının doygunluğu riskini azaltmak ve mümkün olan en kısa zaman diliminde Microsoft 365 performansı önemli ölçüde artırmak için basit bir yöntem sağlamaktır. VPN istemcilerini VPN hedeflerini atlayarak en kritik, Microsoft 365 hacmini ve trafiğin aşağıdaki avantajları elde edene izin verecek şekilde yapılandırılması:

- Kurumsal VPN mimarisinde müşteri tarafından bildirilen performans ve ağ kapasitesi sorunlarının büyük bir çoğunluğunun kullanıcı deneyimini etkileyen temel Microsoft 365 etkisini anında azaltmak
  
  Önerilen çözüm özellikle URL'ler Microsoft 365 IP adresi aralıkları için konu başlığında En Microsoft 365  olarak [kategorilere ayrılmış hizmet uç noktalarını hedefler](./urls-and-ip-address-ranges.md). Bu uç noktalara gelen trafik gecikme süresi ve bant genişliği azaltmaya son derece duyarlıdır ve VPN trafiğini atlayarak son kullanıcı deneyimini önemli ölçüde geliştirebilecektir ve şirket ağ yükünü düşürebilirsiniz. Microsoft 365 genişliğinin veya kullanıcı deneyiminin kap kaplanı çoğunluğunu oluşturmaz bağlantılar, İnternet'e bağlı trafiğin geri kalanıyla birlikte VPN trafiği yoluyla yönlendirilene kadar devam eder. Daha fazla bilgi için bkz[. VPN bölünmüş strateji.](#the-vpn-split-tunnel-strategy)

- Müşteriler tarafından hızlı bir şekilde yafta edilebilir, test edilebilir ve hızlı bir şekilde uygulansa da ek altyapı veya uygulama gereksinimleri yoktur.

  VPN platformuna ve ağ mimarisine bağlı olarak, uygulama birkaç saat kadar sürebilir. Daha fazla bilgi için bkz [. VPN bölünmüş tarak uygulama](microsoft-365-vpn-implement-split-tunnel.md#implement-vpn-split-tunneling).

- İnternet trafiği dahil olmak üzere diğer bağlantıların nasıl yönlendirildiklerini değiştirmeerek müşteri VPN uygulamalarının güvenlik nedenlerini korur

  Önerilen yapılandırma, VPN trafiği özel  durumları için en az ayrıcalık ilkesine sahiptir ve müşterilerin bölünmüş vpn VPN'lerini, kullanıcıları veya altyapıyı ek güvenlik risklerine açık yapmadan uygulamalarına olanak sağlar. Doğrudan Microsoft 365 uç noktalarına yönlendirilen ağ trafiği şifrelenir, Office istemci uygulaması yığınları tarafından bütünlük için doğrulanır ve hem uygulama hem de ağ düzeyinde ayrılmış Microsoft 365 hizmetleri için ayrılmış IP adresleri kapsamındadır. Daha fazla bilgi için, günümüzün benzersiz uzaktan çalışma senaryolarında modern güvenlik denetimlerine ulaşmak için güvenlik uzmanları ve [BT'nin alternatif yolları (Microsoft Güvenlik Ekibi blogu) makalelerine bakın](https://www.microsoft.com/security/blog/2020/03/26/alternative-security-professionals-it-achieve-modern-security-controls-todays-unique-remote-work-scenarios/).

- Kurumsal VPN platformlarının çoğu yerel olarak destekler

  Microsoft, iş ortaklarının yukarıdaki önerilere uygun olarak çözümleri için hedefli kılavuz ve yapılandırma şablonları geliştirmelerine yardımcı olmak için ticari VPN çözümleri üreten sektör ortaklarıyla işbirliğine devam etmektedir. Daha fazla bilgi için bkz. [Yaygın VPN platformları için HOWTO kılavuzları](microsoft-365-vpn-implement-split-tunnel.md#howto-guides-for-common-vpn-platforms).

>[!TIP]
>Microsoft, ayrık hizmetler için ayrılmış ayrılmış IP aralıklarına bölünmüş VPN yapılandırmasının Microsoft 365 önermektedir. FQDN veya AppID tabanlı bölünmüş yapılandırmalar varken, bazı VPN istemci platformlarında mümkün olduğunca anahtar Microsoft 365 senaryolarını tam olarak kapatmayabiliyor ve IP tabanlı VPN yönlendirme kurallarıyla çakışabiliyor. Bu nedenle, Microsoft bölünmüş vpn'leri yapılandırmak Microsoft 365 FQDN'ler kullanılması önerilmez. FQDN yapılandırmasının kullanımı, .pac dosyası özelleştirmeleri veya proxy atlamaları uygulama gibi diğer ilgili senaryolarda yararlı olabilir.

Tam uygulama kılavuzu için bkz[. MICROSOFT 365 için VPN bölünmüş Microsoft 365](microsoft-365-vpn-implement-split-tunnel.md).

Uzak çalışanların e-postalarını yapılandırmaya Microsoft 365 adım adım işlem için bkz[. Uzak çalışma için altyapınızı ayarlama](..\solutions\empower-people-to-work-remotely.md)

## <a name="the-vpn-split-tunnel-strategy"></a>VPN bölünmüş strateji

Geleneksel şirket ağları çoğunlukla, kullanıcıların çoğunluğunda olduğu gibi en önemli verilerin, hizmetlerin, uygulamaların şirket içinde barındır yer alan ve doğrudan şirket içi ağa bağlı olduğu bulut öncesi bir dünyada güvenli bir şekilde çalışacak şekilde tasarlanmıştır. Dolayısıyla bu şubelerde bu öğelerin çevresinde ağ altyapısı yerleşik olarak kullanılır ve ofislerin genel ofisleri _Multiprotocol Label Switching (MPLS)_ ağları üzerinden bağlanır ve uzak kullanıcıların hem şirket içi uç noktalara hem de İnternet'e erişmek için şirket ağına VPN üzerinden bağlanması gerekir. Bu modelde, uzak kullanıcılardan gelen tüm trafik şirket ağına çapraz geçiş yaptı ve ortak bir çıkış noktasından bulut hizmetine yönlendirildi.

![Zorunlu VPN yapılandırması.](../media/vpn-split-tunneling/vpn-model-1.png)

_Şekil 2: Hedeften bağımsız olarak tüm trafiğin şirket ağına geri dönüş yapmak zorunda olduğu uzak kullanıcılar için ortak bir VPN çözümü_

Kuruluşlar verileri ve uygulamaları buluta taşıydıklarında, bu model hızlı şekilde zahmetli, pahalı ve sıralanmamış hale geldi ve kullanıcıların ağ performansını ve verimliliğini önemli ölçüde etkilemektedir ve kuruluşun değişen ihtiyaçlara uyum sağlama becerisini kısıtlamaktadır. Çok sayıda Microsoft müşterisi, birkaç yıl önce ağ trafiğinin %80'inin iç hedefe bağlandı, ancak 2020'de %80 artı trafik, bulut tabanlı bir dış kaynağa bağlandı.

COVID-19 krizi, kuruluşların büyük çoğunluğu için acil çözümler gerektirmesi bu sorunu aştı. Birçok müşteri zorlanan VPN modelinin, bu kriz gibi %100 uzaktan çalışma senaryolarına yetecek kadar ölçeklendirilebilir veya performanslı olmadığını buldu. Bu kuruluşların verimli bir şekilde çalışmaya devam etmek için hızlı çözümler gereklidir.

Microsoft 365 hizmeti için, Microsoft hizmet için bağlantı gereksinimlerini bu sorunu kare kare olarak tasarlar; burada odaklanmış, sıkı denetimli ve görece statik bir hizmet uç noktaları kümesi çok basit ve hızlı bir şekilde en iyi duruma gelebilir; böylelikle hizmete erişen kullanıcılar için yüksek performans sunmak ve vpn altyapısı üzerindeki yükü azaltarak hala onu gerektiren trafik tarafından kullanılabilir.

Microsoft 365 için gerekli uç noktaları üç kategoriye **Microsoft 365 kategorilere** ayrılır: En İyi Duruma Getirme, **İzin Ver** **ve Varsayılan**. **En** iyi duruma getirme uç noktaları buradadır ve aşağıdaki özelliklere sahiptir:

- Microsoft'un sahip olduğu ve yönetilen uç noktaları Microsoft altyapısında barındırılan mı
- Exchange Online, SharePoint Online, Skype Kurumsal Online ve Microsoft Teams gibi temel Microsoft 365 iş yüklerini Microsoft Teams
- IP'ler sağlanıyor mu?
- Düşük değişiklik oranına sahip olması ve sayı olarak az kalması beklenir (şu anda 20 IP alt ağı)
- Yüksek hacim ve/veya gecikmeye duyarlıdır
- Ağ üzerinde satır içi yerine hizmette gerekli güvenlik öğelerini sağlanıyor olabilir
- Hizmet hizmetine gelen trafik hacminin yaklaşık %70-80'i Microsoft 365 hesaba Microsoft 365

Bu sıkı kapsamı olan bu uç nokta kümesi zorlanan VPN hedeflerine ayrılarak, kullanıcının yerel arabirimi üzerinden güvenli bir şekilde ve doğrudan Microsoft 365 hizmetine gönderebilirsiniz. Bu, bölünmüş **kazıma olarak bilinir**.

DLP, AV koruması, kimlik doğrulama ve erişim denetimi gibi güvenlik öğelerinin hepsi hizmet içindeki farklı katmanlarda bu uç noktalara karşı çok daha verimli bir şekilde teslim edilir. Ayrıca trafik hacmini VPN çözümünden yönlendiren bir sistem olduğu için VPN kapasitesine hala bağlı olan iş açısından kritik trafik için VPN kapasitesi serbesttir. Ayrıca, bu yeni işletim sistemiyle başa çıkılacak şekilde uzun ve maliyetli bir yükseltme programından geçerek, birçok durumda ihtiyacı kaldırması gerekir.

![Bölünmüş Tunnel VPN yapılandırma ayrıntıları.](../media/vpn-split-tunneling/vpn-split-tunnel-example.png)

_Şekil 3: Doğrudan hizmete gönderilen tanımlı özel Microsoft 365 VPN bölünmüş olay çözümü. Diğer tüm trafik hedeflere bakılmaksızın şirket ağına geri zorunludur._

Güvenlik açısından bakıldığında, Microsoft'un bir dizi güvenlik özelliği vardır ve bu özellikler şirket içi güvenlik yığınları tarafından satır içi denetimle yapılan denetimlere göre benzer, hatta gelişmiş güvenlik sağlamak için kullanılabilir. Microsoft Güvenlik ekibinin blog gönderisi Günümüzün benzersiz uzaktan çalışma senaryolarında modern güvenlik denetimlerine ulaşmak için güvenlik uzmanları ve [BT'nin](https://www.microsoft.com/security/blog/2020/03/26/alternative-security-professionals-it-achieve-modern-security-controls-todays-unique-remote-work-scenarios/) alternatif yolları, kullanılabilen özelliklerin net bir özetini içerir ve bu makalede daha ayrıntılı kılavuzu bulabilirsiniz. Ayrıca, Microsoft'un VPN üzerinde çalışma: Microsoft uzaktan iş gücü bağlantısını nasıl bağlı tutmuştur makalesinde VPN bölünmüş izleme uygulaması [hakkında da bilgi okuyabilirsiniz](https://www.microsoft.com/itshowcase/blog/running-on-vpn-how-microsoft-is-keeping-its-remote-workforce-connected/?elevate-lv).

Birçok durumda, bu uygulama birkaç saat içinde sağlanıyor olabilir ve kuruluşların karşılaştığı en önemli sorunlardan biri olan hızlı çözüme olanak sağlamak için hızlı bir şekilde hızlı bir şekilde, hızlı bir şekilde uzak ölçekte çalışmaya geçiş yapmaktır. VPN bölünmüş şifreleme uygulama kılavuzu için bkz[. Daha fazla bilgi için VPN bölünmüş Microsoft 365](microsoft-365-vpn-implement-split-tunnel.md).

## <a name="faq"></a>SSS

Microsoft Güvenlik Ekibi, günümüzün benzersiz uzaktan çalışma senaryolarında modern güvenlik denetimleri elde etmek için güvenlik uzmanları ve BT'nin modern güvenlik denetimlerine ulaşmak için alternatif yollar yayımladığı blog gönderisinde, güvenlik uzmanlarının ve [BT'nin](https://www.microsoft.com/security/blog/2020/03/26/alternative-security-professionals-it-achieve-modern-security-controls-todays-unique-remote-work-scenarios/) günümüzün benzersiz uzaktan çalışma senaryolarında modern güvenlik denetimlerini elde etmenin önemli yollarını özetler. Buna ek olarak, bu konuda sık sorulan müşteri sorularının ve yanıtlarının bazıları aşağıda verilmiştir.

### <a name="how-do-i-stop-users-accessing-other-tenants-i-do-not-trust-where-they-could-exfiltrate-data"></a>Kullanıcıların diğer kiracılara erişimini nasıl durdurabilirim? Güvenim yok, ama verileri bu kullanıcılardan kesebilirler?

Yanıtı kiracı kısıtlamaları [adı verilen bir özelliktir](/azure/active-directory/manage-apps/tenant-restrictions). Kimlik doğrulama trafiği yüksek hacimde değildir ve özellikle gecikmeye duyarlı değildir, bu nedenle özelliğin uygulandığı şirket içi ara sunucuya VPN çözümü aracılığıyla gönderebilirsiniz. Burada, güvenilir kiracıların izin verme listesi korunur ve istemci güvenilir olmayan bir kiracıya belirteç almak için çalışırsa, ara sunucu yalnızca isteği reddettir. Kiracı güvenilirse, kullanıcının doğru kimlik bilgilerine ve haklara sahip olduğu bir belirteçe erişilebilir.

Dolayısıyla kullanıcı söz konusu kiracıya erişmek için geçerli bir belirteç olmadan yukarıdaki İşaretli uç noktaları en iyi duruma getirme bağlantısına TCP/UDP bağlantısı alsa da, oturum açamaz ve hiçbir veriye erişamaz/verileri taşıyamaz.

### <a name="does-this-model-allow-access-to-consumer-services-such-as-personal-onedrive-accounts"></a>Bu model kişisel kişisel hesap hesapları gibi tüketici hizmetlerine OneDrive olanak sağlar mı?

Hayır, değil, Microsoft 365 uç noktaları tüketici hizmetleriyle (örnek olarak Onedrive.live.com) aynı değildir, dolayısıyla bölünmüş bölme kullanıcının doğrudan tüketici hizmetlerine erişmesine izin vermez. Tüketici uç noktalarına yönelik trafik VPN trafiğini kullanmaya devam edecektir ve var olan ilkeler de uygulanır.

### <a name="how-do-i-apply-dlp-and-protect-my-sensitive-data-when-the-traffic-no-longer-flows-through-my-on-premises-solution"></a>Trafik artık şirket içi çözümümde akmasa da DLP'i nasıl uygulayabilirim ve hassas verilerimi nasıl koruyabilirim?

Hassas bilgilerin yanlışlıkla açıklanmasına yardımcı olmak için Microsoft 365 çok zengin bir [araç kümesi vardır](../compliance/information-protection.md). Uygunsuz şekilde depolanan veya paylaşılan hassas [bilgileri algılamak](../compliance/dlp-learn-about-dlp.md) için Teams ve SharePoint DLP özelliklerini kullanabilirsiniz. Uzaktan çalışma stratejinizin bir parçası kendi cihazınızı getirme (BYOD) ilkesi içeriyorsa, hassas verilerin kullanıcıların kişisel cihazlarına indirilsini önlemek için uygulama tabanlı Koşullu Erişim'i kullanabilirsiniz [](/azure/active-directory/conditional-access/app-based-conditional-access)

### <a name="how-do-i-evaluate-and-maintain-control-of-the-users-authentication-when-they-are-connecting-directly"></a>Doğrudan bağlanıyorken kullanıcının kimlik doğrulamasını nasıl değerlendirir ve denetimlerini sürdürürim?

Q1'de belirtilen kiracı kısıtlamaları özelliğine ek [olarak, kimlik](/azure/active-directory/conditional-access/overview) doğrulama isteğinin riskini dinamik olarak değerlendirmek ve uygun şekilde ifade etmek için koşullu erişim ilkeleri de uygulanabilir. Microsoft zaman içinde [Sıfır Güven modelinin](https://www.microsoft.com/security/zero-trust?rtc=1) uygulanmasını önermektedir ve mobil ve ilk bulutta denetimi korumak için Azure AD koşullu erişim ilkelerini kullanabiliriz. Koşullu erişim ilkeleri, kimlik doğrulama isteğinin başarılı olup olmadığı konusunda gerçek zamanlı olarak karar vermede kullanılabilir. Örneğin:

- Cihaz, bilinen/güvenilen/Etki Alanı katılmış cihaz mı?
- IP – Kimlik doğrulama isteği bilinen bir şirket IP adresinden mi geliyor? Yoksa güven güvenmemiz gereken bir ülkede mi?
- Uygulama – Kullanıcı bu uygulamayı kullanma yetkisine sahip mi?

Bundan sonra onaylama, MFA'ya yönelik kimlik doğrulamayı tetikleme veya bu ilkelere dayalı kimlik doğrulamayı engelleme gibi ilkeler tetikl olabilir.

### <a name="how-do-i-protect-against-viruses-and-malware"></a>Virüslere ve kötü amaçlı yazılımlara nasıl koruma yapabilirim?

Ayrıca, Microsoft 365 bu belgede ana hatlarıyla açıklanan, hizmetin kendi içinde yer alan çeşitli katmanlarda en iyi duruma getirme uç noktaları için [de koruma sağlar](/office365/Enterprise/office-365-malware-and-ransomware-protection). Burada da olduğu gibi, bu güvenlik öğelerini, protokolleri/trafiği tam olarak anlamayan cihazlarla uyumlu olarak yerine hizmette sağlamak çok daha verimlidir. Varsayılan olarak, SharePoint Online [bilinen kötü amaçlı yazılım için dosya karşıya yüklemelerini](../security/office-365-security/virus-detection-in-spo.md) otomatik olarak tarar

Yukarıda listelenen Exchange uç noktaları için, [Exchange Online Protection](/office365/servicedescriptions/exchange-online-protection-service-description/exchange-online-protection-service-description) ve [Microsoft 365 için Microsoft Defender](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description) hizmette trafiğin güvenliğini sağlama konusunda mükemmel bir iş yapar.

### <a name="can-i-send-more-than-just-the-optimize-traffic-direct"></a>Trafiği doğrudan en iyi duruma getirme hakkında daha fazla şey gönderebilir miyim?

En iyi duruma getirmek **için en iyi** duruma getirme uç noktalarına öncelik ver verilmesi gerekir, bu da düşük bir çalışma düzeyi için en yüksek avantaj sağlar. Öte yandan isterseniz, hizmetin çalışması için İşaretli uç noktalara izin ver gerekir ve gerekirse  kullanılan uç noktalar için IP adresleri sağlanır.

Ayrıca, genel web'e gözatma için merkezi güvenlik, denetim ve şirket ilkesi uygulaması sağlayan güvenli _web_ ağ geçitleri olarak adlandırılan bulut tabanlı ara sunucu/güvenlik çözümleri sunan çeşitli satıcılar da vardır. Bu çözümler yüksek düzeyde kullanılabilir, performansı yüksekse ve kullanıcıya yakın bulut tabanlı bir konumdan güvenli İnternet erişimi sağlayarak kullanıcılarınıza yakın bir konumda sağlandısa, bu çözümler ilk bulutta işe kullanılabilir. Bu işlem, genel göz atma trafiği için VPN/şirket ağına göz atma ihtiyacını ortadan kaldırır ve yine de merkezi güvenlik denetimine izin verir.

Ancak bu çözümler yerine hiç gönderilmese bile Microsoft, Trafiğin Microsoft 365 olarak en iyi duruma getirmenin doğrudan hizmete gönderilmelerini kesinlikle önermektedir.

Azure Sanal Ağına doğrudan erişim izni vermeyle ilgili kılavuz için bkz. [Azure VPN Ağ Geçidi Noktadan siteye kullanılarak uzaktan çalışma](/azure/vpn-gateway/work-remotely-support).

### <a name="why-is-port-80-required-is-traffic-sent-in-the-clear"></a>Bağlantı noktası 80 neden gereklidir? Trafik temiz olarak gönderilir mi?

Bağlantı noktası 80 yalnızca bağlantı noktası 443 oturumuna yeniden yönlendirme gibi şeyler için kullanılır, müşteri verileri gönderilmez veya bağlantı noktası 80 üzerinden erişilebilir olmaz. [Şifreleme](../compliance/encryption.md), toplu taşımadaki ve kalan verilerin ana hatlarını Microsoft 365 türleri ve medya trafiğini korumak için [](/microsoftteams/microsoft-teams-online-call-flows#types-of-traffic) SRTP'yi nasıl Teams ana hatlarıyla gösterir.

### <a name="does-this-advice-apply-to-users-in-china-using-a-worldwide-instance-of-microsoft-365"></a>Bu öneri dünya çapında bir örnek kullanan Çin'deki kullanıcılar için geçerli Microsoft 365?

**Hayır**, yok. Yukarıdaki tavsiyeye bir uyarı, Dünya çapında bir örnekle bağlantılı olan ÇÇY'de yer alan kullanıcılardır ve bu Microsoft 365. Bölgede çapraz ağ tıkanıklığı sık ortaya çıkma nedeniyle, doğrudan İnternet çıkış performansı değişken olabilir. Bölgedeki çoğu müşteri, trafiği şirket ağına getirmek için VPN kullanarak çalışır ve en iyi duruma getirilmiş bir yol üzerinden ülke dışına çıkışa benzer şekilde yetkili MPLS devrelerini kullanır. Bu durum, Çin kullanıcılarına performans iyileştirme [Microsoft 365 ilgili makalede daha ayrıntılı olarak açıklanmıştır](microsoft-365-networking-china.md).

### <a name="does-split-tunnel-configuration-work-for-teams-running-in-a-browser"></a>Bölünmüş yapılandırma yapılandırması bir tarayıcıda Teams için çalışıyor mu?

Evet, uyarılarla birlikte. en Teams işlevleri, Şu tarayıcılar için istemci [al'da listelenen tarayıcılarda Microsoft Teams](/microsoftteams/get-clients#web-client).

Buna ek Microsoft Edge **96** ve üzeri, Edge [WebRtcRespectOsRoutingTableEnabled](/deployedge/microsoft-edge-policies#webrtcrespectosroutingtableenabled) ilkesi etkinleştirerek eşler arası trafik için VPN bölünmüş trafiği destekler. Şu anda, diğer tarayıcılar eşler arası trafik için VPN bölünmüş eşlemeyi desteklemeyebilirsiniz.

## <a name="related-articles"></a>İlgili makaleler

[VPN bölmeli bölme Microsoft 365](microsoft-365-vpn-implement-split-tunnel.md)

[Kullanıcılar için yaygın VPN bölme bölme Microsoft 365](microsoft-365-vpn-common-scenarios.md)

[VPN bölünmüş Teams için medya trafiğinin güvenliğini sağlama](microsoft-365-vpn-securing-teams.md)

[VPN ortamlarında Stream ve canlı etkinlikler için dikkat edilmesi gereken noktalar](microsoft-365-vpn-stream-and-live-events.md)

[Microsoft 365 kullanıcıları için performans iyileştirmeyi iyileştirme](microsoft-365-networking-china.md)

[Microsoft 365 Ağ Bağlantısı İlkeleri](microsoft-365-network-connectivity-principles.md)

[Ağ Microsoft 365 değerlendirme](assessing-network-connectivity.md)

[Microsoft 365 ve performans ayarını yapılandırma](network-planning-and-performance.md)

[Günümüzün benzersiz uzaktan çalışma senaryolarında güvenlik uzmanlarının ve BT'nin modern güvenlik denetimlerini elde etmenin alternatif yolları (Microsoft Güvenlik Ekibi blogu)](https://www.microsoft.com/security/blog/2020/03/26/alternative-security-professionals-it-achieve-modern-security-controls-todays-unique-remote-work-scenarios/)

[Microsoft'ta VPN performansını geliştirme: otomatik Windows 10 izin vermek için VPN profillerini kullanma](https://www.microsoft.com/itshowcase/enhancing-remote-access-in-windows-10-with-an-automatic-vpn-profile)

[VPN ile çalışma: Microsoft uzaktan iş gücüne nasıl bağlı tutarak](https://www.microsoft.com/itshowcase/blog/running-on-vpn-how-microsoft-is-keeping-its-remote-workforce-connected/?elevate-lv)

[Microsoft genel ağı](/azure/networking/microsoft-global-network)
