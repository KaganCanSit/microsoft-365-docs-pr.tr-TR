---
title: 'Genel bakış: VPN bölme bölme Office 365'
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 9/22/2020
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
description: Uzak kullanıcılar için ağ bağlantısını iyileştirmek Office 365 VPN bölünmüş Office 365 kılavuzu.
ms.openlocfilehash: 09900e1650ee1221d9b9877903a08e18af7154b3
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62986528"
---
# <a name="optimize-office-365-connectivity-for-remote-users-using-vpn-split-tunneling"></a>VPN bölünmüş Office 365 kullanarak uzak kullanıcılar için ayrım bağlantısını en iyi duruma getirme
<!---
>[!NOTE]
>This topic is part of a set of topics that address Office 365 optimization for remote users.
>- For VPN split tunnel implementation guidance, see [Implementing VPN split tunneling for Office 365](microsoft-365-vpn-implement-split-tunnel.md).
>- For information about optimizing Office 365 worldwide tenant performance for users in China, see [Office 365 performance optimization for China users](microsoft-365-networking-china.md).
-->

Uzaktan çalışan cihazlarını VPN üzerinden şirket ağına veya bulut altyapısına bağlamak isteyen müşteriler için Microsoft, önemli **Office 365 senaryoları Microsoft Teams**, **SharePoint Online** ve **Exchange Online'in** _VPN_ bölünmüş yapılandırma üzerinden yönlendirilmez. COVID-19 kriz gibi evden gelen büyük ölçekli etkinlikler sırasında çalışan üretkenliğinin devamını kolaylaştıran ilk satır stratejisi olarak bu durum özellikle önemli hale gelir.

![VPN Tunnel bölün.](../media/vpn-split-tunneling/vpn-model-2.png)

_Şekil 1: Doğrudan hizmete gönderilen tanımlı veya özel Office 365 VPN bölünmüş olay çözümü. Diğer tüm trafik hedeften bağımsız olarak VPN trafiği üzerinden çapraz geçiş yaptı._

Bu yaklaşımın özünü, kuruluşlara VPN altyapısının doygunluğu riskini azaltmak ve mümkün olan en kısa zaman diliminde Office 365 performansını önemli ölçüde artırmak için basit bir yöntem sağlamaktır. VPN istemcilerini VPN hedeflerini atlayarak en kritik ve Office 365 hacmini sağlayan bir trafiğin yapılandırılması, aşağıdaki avantajların elde  olmasına olanak sağlar:

- Kurumsal VPN mimarisinde müşteri tarafından bildirilen performans ve ağ kapasitesi sorunlarının büyük bir çoğunluğunun, kullanıcı deneyimini etkileyen Office 365 etkisini anında azaltmak
  
  Önerilen çözüm özellikle URL'ler Office 365 IP adresi aralıkları için konu başlığında En İyi Duruma  Office 365 [hizmet uç noktalarının hedeflemektedir](./urls-and-ip-address-ranges.md). Bu uç noktalara gelen trafik gecikme süresi ve bant genişliği azaltmaya son derece duyarlıdır ve VPN trafiğini atlayarak son kullanıcı deneyimini önemli ölçüde geliştirebilecektir ve şirket ağ yükünü düşürebilirsiniz. Office 365 genişliğinin veya kullanıcı deneyiminin kap kaplanı çoğunluğunu oluşturmaz bağlantılar, İnternet'e bağlı trafiğin geri kalanıyla birlikte VPN trafiği yoluyla yönlendirilene kadar devam eder. Daha fazla bilgi için bkz[. VPN bölünmüş strateji.](#the-vpn-split-tunnel-strategy)

- Müşteriler tarafından hızlı bir şekilde yafta edilebilir, test edilebilir ve hızlı bir şekilde uygulansa da ek altyapı veya uygulama gereksinimleri yoktur.

  VPN platformuna ve ağ mimarisine bağlı olarak, uygulama birkaç saat kadar sürebilir. Daha fazla bilgi için bkz [. VPN bölünmüş tarak uygulama](microsoft-365-vpn-implement-split-tunnel.md#implement-vpn-split-tunneling).

- İnternet trafiği dahil olmak üzere diğer bağlantıların nasıl yönlendirildiklerini değiştirmeerek müşteri VPN uygulamalarının güvenlik nedenlerini korur

  Önerilen yapılandırma, VPN trafiği özel  durumları için en az ayrıcalık ilkesine sahiptir ve müşterilerin bölünmüş vpn VPN'lerini, kullanıcıları veya altyapıyı ek güvenlik risklerine açık yapmadan uygulamalarına olanak sağlar. Doğrudan Office 365 uç noktalarına yönlendirilen ağ trafiği şifrelenir, Office istemci uygulaması yığınları tarafından bütünlük için doğrulanır ve hem uygulama hem de ağ düzeyinde ayrılmış Office 365 hizmetleri için ayrılmış IP adresleri kapsamındadır. Daha fazla bilgi için, günümüzün benzersiz uzaktan çalışma senaryolarında modern güvenlik denetimlerine ulaşmak için güvenlik uzmanları ve [BT'nin alternatif yolları (Microsoft Güvenlik Ekibi blogu) makalelerine bakın](https://www.microsoft.com/security/blog/2020/03/26/alternative-security-professionals-it-achieve-modern-security-controls-todays-unique-remote-work-scenarios/).

- Kurumsal VPN platformlarının çoğu yerel olarak destekler

  Microsoft, iş ortaklarının yukarıdaki önerilere uygun olarak çözümleri için hedefli kılavuz ve yapılandırma şablonları geliştirmelerine yardımcı olmak için ticari VPN çözümleri üreten sektör ortaklarıyla işbirliğine devam etmektedir. Daha fazla bilgi için bkz. [Yaygın VPN platformları için HOWTO kılavuzları](microsoft-365-vpn-implement-split-tunnel.md#howto-guides-for-common-vpn-platforms).

>[!TIP]
>Microsoft, bu hizmetlerde ayrık VPN yapılandırmasının belgelenmiş ayrılmış IP aralıkları üzerine odaklan Office 365 önermektedir. FQDN veya AppID tabanlı bölünmüş yapılandırmalar varken bazı VPN istemci platformlarında mümkün olduğunca anahtar ve Office 365 senaryolarını tam olarak kapatmayabiliyor ve IP tabanlı VPN yönlendirme kurallarıyla çakışabiliyor. Bu nedenle, Microsoft bölünmüş vpn'leri yapılandırmak Office 365 FQDN'ler kullanılması önerilmez. FQDN yapılandırmasının kullanımı, .pac dosyası özelleştirmeleri veya proxy atlamaları uygulama gibi diğer ilgili senaryolarda yararlı olabilir.

Tam uygulama kılavuzu için bkz[. OFFICE 365 için VPN bölünmüş Office 365](microsoft-365-vpn-implement-split-tunnel.md).

Uzak çalışanların e-postalarını yapılandırmaya Microsoft 365 adım adım işlem için bkz[. Uzak çalışma için altyapınızı ayarlama](..\solutions\empower-people-to-work-remotely.md)

## <a name="the-vpn-split-tunnel-strategy"></a>VPN bölünmüş strateji

Geleneksel şirket ağları çoğunlukla, kullanıcıların çoğunluğunda olduğu gibi en önemli verilerin, hizmetlerin, uygulamaların şirket içinde barındır yer alan ve doğrudan şirket içi ağa bağlı olduğu bulut öncesi bir dünyada güvenli bir şekilde çalışacak şekilde tasarlanmıştır. Dolayısıyla bu şubelerde bu öğelerin çevresinde ağ altyapısı yerleşik olarak kullanılır ve ofislerin genel ofisleri _Multiprotocol Label Switching (MPLS)_ ağları üzerinden bağlanır ve uzak kullanıcıların hem şirket içi uç noktalara hem de İnternet'e erişmek için şirket ağına VPN üzerinden bağlanması gerekir. Bu modelde, uzak kullanıcılardan gelen tüm trafik şirket ağına çapraz geçiş yaptı ve ortak bir çıkış noktasından bulut hizmetine yönlendirildi.

![Zorunlu VPN yapılandırması.](../media/vpn-split-tunneling/vpn-model-1.png)

_Şekil 2: Hedeften bağımsız olarak tüm trafiğin şirket ağına geri dönüş yapmak zorunda olduğu uzak kullanıcılar için ortak bir VPN çözümü_

Kuruluşlar verileri ve uygulamaları buluta taşıydıklarında, bu model hızlı şekilde zahmetli, pahalı ve sıralanmamış hale geldi ve kullanıcıların ağ performansını ve verimliliğini önemli ölçüde etkilemektedir ve kuruluşun değişen ihtiyaçlara uyum sağlama becerisini kısıtlamaktadır. Çok sayıda Microsoft müşterisi, birkaç yıl önce ağ trafiğinin %80'inin iç hedefe bağlandı, ancak 2020'de %80 artı trafik, bulut tabanlı bir dış kaynağa bağlandı.

COVID-19 krizi, kuruluşların büyük çoğunluğu için acil çözümler gerektirmesi bu sorunu aştı. Birçok müşteri zorlanan VPN modelinin, bu kriz gibi %100 uzaktan çalışma senaryolarına yetecek kadar ölçeklendirilebilir veya performanslı olmadığını buldu. Bu kuruluşların verimli bir şekilde çalışmaya devam etmek için hızlı çözümler gereklidir.

Office 365 hizmeti için, Microsoft hizmet için bağlantı gereksinimlerini bu sorunu kare kare olarak tasarlamaktadır; burada odaklanmış, sıkı bir şekilde denetlenen ve görece statik bir hizmet uç noktaları kümesi çok basit ve hızlı bir şekilde en iyi duruma gelebilir; böylelikle hizmete erişen kullanıcılar için yüksek performans sunmak ve VPN altyapısı üzerindeki yükü azaltarak hala onu gerektiren trafik tarafından kullanılabilir.

Office 365 için gerekli uç noktaları üç kategoriye **Office 365: En** İyi Duruma Getirme, **İzin Ver** **ve Varsayılan**. **En** iyi duruma getirme uç noktaları buradadır ve aşağıdaki özelliklere sahiptir:

- Microsoft'un sahip olduğu ve yönetilen uç noktaları Microsoft altyapısında barındırılan mı
- Exchange Online, SharePoint Online, Skype Kurumsal Online ve Microsoft Teams gibi temel Office 365 iş yüklerini Microsoft Teams
- IP'ler sağlanıyor mu?
- Düşük değişiklik oranına sahip olması ve sayı olarak az kalması beklenir (şu anda 20 IP alt ağı)
- Yüksek hacim ve/veya gecikmeye duyarlıdır
- Ağ üzerinde satır içi yerine hizmette gerekli güvenlik öğelerini sağlanıyor olabilir
- Kullanıcı hizmetine gelen trafik hacminin yaklaşık %70-80'Office 365 hesaba Office 365

Bu sıkı kapsamı olan bu uç nokta kümesi zorlanan VPN hedeflerine ayrılarak, kullanıcının yerel arabirimi üzerinden güvenli bir şekilde Office 365 hizmetine gönderebilirsiniz. Bu, bölünmüş **kazıma olarak bilinir**.

DLP, AV koruması, kimlik doğrulama ve erişim denetimi gibi güvenlik öğelerinin hepsi hizmet içindeki farklı katmanlarda bu uç noktalara karşı çok daha verimli bir şekilde teslim edilir. Ayrıca trafik hacmini VPN çözümünden yönlendiren bir sistem olduğu için VPN kapasitesine hala bağlı olan iş açısından kritik trafik için VPN kapasitesi serbesttir. Ayrıca, bu yeni işletim sistemiyle başa çıkılacak şekilde uzun ve maliyetli bir yükseltme programından geçerek, birçok durumda ihtiyacı kaldırması gerekir.

![Bölünmüş Tunnel VPN yapılandırma ayrıntıları.](../media/vpn-split-tunneling/vpn-split-tunnel-example.png)

_Şekil 3: Doğrudan hizmete gönderilen tanımlı özel Office 365 VPN bölünmüş olay çözümü. Diğer tüm trafik hedeflere bakılmaksızın şirket ağına geri zorunludur._

Güvenlik açısından bakıldığında, Microsoft'un bir dizi güvenlik özelliği vardır ve bu özellikler şirket içi güvenlik yığınları tarafından satır içi denetimle yapılan denetimlere göre benzer, hatta gelişmiş güvenlik sağlamak için kullanılabilir. Microsoft Güvenlik ekibinin blog gönderisi Günümüzün benzersiz uzaktan çalışma senaryolarında modern güvenlik denetimlerine ulaşmak için güvenlik uzmanları ve [BT'nin](https://www.microsoft.com/security/blog/2020/03/26/alternative-security-professionals-it-achieve-modern-security-controls-todays-unique-remote-work-scenarios/) alternatif yolları, kullanılabilen özelliklerin net bir özetini içerir ve bu makalede daha ayrıntılı kılavuzu bulabilirsiniz. Ayrıca, Microsoft'un VPN üzerinde çalışma: Microsoft uzaktan iş gücü bağlantısını nasıl bağlı tutmuştur makalesinde VPN bölünmüş izleme uygulaması [hakkında da bilgi okuyabilirsiniz](https://www.microsoft.com/itshowcase/blog/running-on-vpn-how-microsoft-is-keeping-its-remote-workforce-connected/?elevate-lv).

Birçok durumda, bu uygulama birkaç saat içinde sağlanıyor olabilir ve kuruluşların karşılaştığı en önemli sorunlardan biri olan hızlı çözüme olanak sağlamak için hızlı bir şekilde hızlı bir şekilde, hızlı bir şekilde uzak ölçekte çalışmaya geçiş yapmaktır. VPN bölünmüş şifreleme uygulama kılavuzu için bkz[. Daha fazla bilgi için VPN bölünmüş Office 365](microsoft-365-vpn-implement-split-tunnel.md).

## <a name="related-topics"></a>İlgili konular

[VPN bölmeli bölme Office 365](microsoft-365-vpn-implement-split-tunnel.md)

[Office 365 kullanıcılar için performans iyileştirmeyi iyileştirme](microsoft-365-networking-china.md)

[Günümüzün benzersiz uzaktan çalışma senaryolarında güvenlik uzmanlarının ve BT'nin modern güvenlik denetimlerini elde etmenin alternatif yolları (Microsoft Güvenlik Ekibi blogu)](https://www.microsoft.com/security/blog/2020/03/26/alternative-security-professionals-it-achieve-modern-security-controls-todays-unique-remote-work-scenarios/)

[Microsoft'ta VPN performansını geliştirme: otomatik Windows 10 izin vermek için VPN profillerini kullanma](https://www.microsoft.com/itshowcase/enhancing-remote-access-in-windows-10-with-an-automatic-vpn-profile)

[VPN ile çalışma: Microsoft uzaktan iş gücüne nasıl bağlı tutarak](https://www.microsoft.com/itshowcase/blog/running-on-vpn-how-microsoft-is-keeping-its-remote-workforce-connected/?elevate-lv)

[Office 365 Bağlantısı İlkeleri](microsoft-365-network-connectivity-principles.md)

[Ağ Office 365 değerlendirme](assessing-network-connectivity.md)

[Microsoft 365 bağlantı testi](https://aka.ms/netonboard)