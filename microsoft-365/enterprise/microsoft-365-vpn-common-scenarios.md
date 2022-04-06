---
title: Kullanıcılar için yaygın VPN bölme bölme Microsoft 365
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
f1.keywords:
- NOCSH
description: Kullanıcılar için yaygın VPN bölme bölme Microsoft 365
ms.openlocfilehash: 26f4cf10de3282c5257592a26ea61d073a0d3cd4
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63705182"
---
# <a name="common-vpn-split-tunneling-scenarios-for-microsoft-365"></a>Kullanıcılar için yaygın VPN bölme bölme Microsoft 365

>[!NOTE]
>Bu makale, uzak kullanıcılar için iyileştirmeyi Microsoft 365 makale kümelerinin bir bölümüdir.

>- Uzak kullanıcılar için Microsoft 365 bağlantısını en iyi duruma getirmek için VPN bölünmüş şifreleme kullanma hakkında genel bir bakış için bkz[.](microsoft-365-vpn-split-tunnel.md) Genel Bakış: Vpn bölünmüş Microsoft 365.
>- VPN bölünmüş bölmeyi uygulama hakkında ayrıntılı kılavuz için bkz. [VPN bölünmüş bölmeyi uygulama Microsoft 365](microsoft-365-vpn-implement-split-tunnel.md).
>- VPN bölünmüş trafiğinde Teams trafiğinin güvenliğini sağlama kılavuzu için bkz. VPN bölünmüş trafiği için Teams trafiğinin güvenliğini [sağlama](microsoft-365-vpn-securing-teams.md).
>- VPN ortamlarında Stream ve canlı etkinlikleri yapılandırma hakkında bilgi için bkz. VPN ortamlarında akış ve canlı etkinlikler [için dikkat edilmesi gereken noktalar](microsoft-365-vpn-stream-and-live-events.md).
>- Çin'deki kullanıcılar için Microsoft 365 kiracı performansını iyileştirme hakkında bilgi için bkz. [Microsoft 365 için performans iyileştirme.](microsoft-365-networking-china.md)

Aşağıdaki listede, kurumsal ortamlarda görülen en yaygın VPN senaryolarını görebilirsiniz. Çoğu müşteri geleneksel olarak model 1'i (VPN Zorlamalı Vpn Tunnel). Bu bölüm, görece az çabayla elde edilebilir olan ve ağ performansıyla kullanıcı deneyiminin inanılmaz avantajları olan **Model 2'ye** hızlı ve güvenli bir şekilde geçiş içinde size yardımcı olur.

| Model | Açıklama |
| --- | --- |
| [1. VPN Zorunlu Tunnel](#1-vpn-forced-tunnel) | Trafiğin %100'ü şirket içi, İnternet ve tüm O365/M365 gibi VPN trafiğine gidiyor |
| [2. VPN Zorlanan Tunnel birkaç özel durumla](#2-vpn-forced-tunnel-with-a-small-number-of-trusted-exceptions) | VPN hattı varsayılan olarak kullanılır (varsayılan rota noktaları VPN'ye), ve doğrudan gitme izni verilen birkaç önemli muaf senaryo |
| [3. VPN Zorunlu Tunnel özel durumlar dışında](#3-vpn-forced-tunnel-with-broad-exceptions) | VPN hattı varsayılan olarak kullanılır (varsayılan rota noktaları VPN'ye), doğrudan yönlendiri izin verilen çok özel durumlar (tüm Microsoft 365, Tüm Salesforce, Tüm Yakınlaştırma) |
| [4. VPN Seçmeli Tunnel](#4-vpn-selective-tunnel) | VPN yolu yalnızca Corpnet tabanlı hizmetler için kullanılır. Varsayılan rota (İnternet ve tüm İnternet tabanlı hizmetler) doğrudan gider. |
| [5. VPN yok](#5-no-vpn) | #2'nin çeşitlemesi. Eski VPN yerine tüm corpnet hizmetleri modern güvenlik yaklaşımları (Zscaler ZPA, Azure Active Directory (Azure AD) Proxy/MCAS gibi) aracılığıyla yayımlanır. |

## <a name="1-vpn-forced-tunnel"></a>1. VPN Zorunlu Tunnel

Kurumsal müşterilerin çoğu için en yaygın başlangıç senaryosu. Zorlamalı bir VPN kullanılır, bu da uç nokta şirket ağı içinde olsun ya da yer alınsın trafiğin %100'musunuz şirket ağına yönlendirildi anlamına gelir. İnternet'e Microsoft 365 veya İnternet'e gözatma gibi dış (İnternet) bağlı tüm trafik, sonrasında şirket içi güvenlik donanımının (örneğin, şirket içi güvenlik donanımı) geri sabitlenmiş olmasıdır. Geçerli karnede uzaktan çalışan kullanıcıların neredeyse %100'olduğu bu model dolayısıyla VPN altyapısına yüksek yük koyar ve büyük olasılıkla tüm şirket trafiğinin performansını önemli ölçüde azaltır ve dolayısıyla kuruluş kriz durumlarında etkili bir şekilde çalışmaya devam etmektedir.

![VPN Zorunlu Tunnel model 1.](../media/vpn-split-tunneling/vpn-model-1.png)

## <a name="2-vpn-forced-tunnel-with-a-small-number-of-trusted-exceptions"></a>2. VPN Tunnel çok az sayıda güvenilen özel durum ile zorunlu vpn

Bir işletmenin şu kuruluş kapsamında çalışması çok daha verimlidir. Bu model, yüksek yüke ve gecikme süresine duyarlı az sayıda denetimli ve tanımlanmış uç noktaların VPN taraklarını atlayarak doğrudan Microsoft 365 sağlar. Bu, yüklenen hizmetlerin performansını önemli ölçüde artırır ve VPN altyapısının yükünü de azaltır; böylelikle, kaynaklar için daha düşük içerikle çalışması için yine de gereken öğelerin çalışmasına olanak sağlar. Bu makalenin çok sayıda pozitif sonuçla hızlı bir şekilde basit ve tanımlı eylemlere izin verirken geçişte yardımcı olmaya odaklanan bu modeldir.

![Bölünmüş Tunnel VPN modeli 2.](../media/vpn-split-tunneling/vpn-model-2.png)

## <a name="3-vpn-forced-tunnel-with-broad-exceptions"></a>3. VPN Zorunlu Tunnel özel durumlar dışında

Model 2'nin kapsamını genişleten. Yalnızca küçük bir tanımlı uç nokta grubunu doğrudan göndermek yerine, bunun yerine tüm trafiği doğrudan Microsoft 365 SalesForce gibi güvenilir hizmetlere gönderir. Bu da şirket VPN altyapısının yükünü daha da azaltır ve tanımlanan hizmetlerin performansını iyiler. Bu modelin uygulanabililiğini değerlendirmek ve uygulamak için daha fazla zaman gerektir, bu büyük olasılıkla iki model başarılı bir şekilde tamam olduktan sonra ileri bir tarihte tekrarlayan bir adımdır.

![Bölünmüş Tunnel VPN modeli 3.](../media/vpn-split-tunneling/vpn-model-3.png)

## <a name="4-vpn-selective-tunnel"></a>4. VPN seçmeli Tunnel

Üçüncü modeli tersine çevirerek yalnızca şirket IP adresi olması olarak tanımlanan trafiğin VPN trafiğine iner ve İnternet yolu diğer her şey için varsayılan yol olur. Bu model, bu modeli güvenli bir şekilde uygulayabilecek [Sıfır](https://www.microsoft.com/security/zero-trust?rtc=1) Güven yolunda kuruluşun iyi bir şekilde yola sahip olması gerekir. Bu modelin veya böyle bir çeşitlemenin, zaman içinde daha fazla hizmet şirket ağına ve buluta taşınacak şekilde gerekli varsayılan ayar olacağını dikkate alın.

Microsoft bu modeli dahili olarak kullanır. Microsoft'un VPN bölünmüş bölme uygulaması hakkında daha fazla bilgiyi VPN'de çalıştırma: Microsoft uzaktan iş gücü bağlantısını [nasıl bağlı tutarak devam ediyor makalesinde bulabilirsiniz](https://www.microsoft.com/itshowcase/blog/running-on-vpn-how-microsoft-is-keeping-its-remote-workforce-connected/?elevate-lv).

![Bölünmüş Tunnel VPN modeli 4.](../media/vpn-split-tunneling/vpn-model-4.png)

## <a name="5-no-vpn"></a>5. VPN yok

Model numarası 2'nin daha gelişmiş bir sürümü; böylece tüm iç hizmetler, Azure AD Proxy, Bulut Uygulamaları için Defender, Zscaler ZPA, vb. modern bir güvenlik yaklaşımı veya SDWAN çözümü aracılığıyla yayımlanır.

![Bölünmüş Tunnel VPN modeli 5.](../media/vpn-split-tunneling/vpn-model-5.png)

## <a name="related-articles"></a>İlgili makaleler

[Genel bakış: VPN bölme bölme Microsoft 365](microsoft-365-vpn-split-tunnel.md)

[VPN bölmeli bölme Microsoft 365](microsoft-365-vpn-implement-split-tunnel.md)

[VPN bölünmüş tüneli için Teams medya trafiğinin güvenliğini sağlama](microsoft-365-vpn-securing-teams.md)

[VPN ortamlarında Stream ve canlı etkinlikler için dikkat edilmesi gereken noktalar](microsoft-365-vpn-stream-and-live-events.md)

[Microsoft 365 kullanıcıları için performans iyileştirmeyi iyileştirme](microsoft-365-networking-china.md)

[Microsoft 365 Ağ Bağlantısı İlkeleri](microsoft-365-network-connectivity-principles.md)

[Microsoft 365 ağ bağlantısını değerlendirme](assessing-network-connectivity.md)

[Microsoft 365 ve performans ayarını yapılandırma](network-planning-and-performance.md)

[Günümüzün benzersiz uzaktan çalışma senaryolarında güvenlik uzmanlarının ve BT'nin modern güvenlik denetimlerini elde etmenin alternatif yolları (Microsoft Güvenlik Ekibi blogu)](https://www.microsoft.com/security/blog/2020/03/26/alternative-security-professionals-it-achieve-modern-security-controls-todays-unique-remote-work-scenarios/)

[Microsoft'ta VPN performansını geliştirme: otomatik Windows 10 izin vermek için VPN profillerini kullanma](https://www.microsoft.com/itshowcase/enhancing-remote-access-in-windows-10-with-an-automatic-vpn-profile)

[VPN ile çalışma: Microsoft uzaktan iş gücüne nasıl bağlı tutarak](https://www.microsoft.com/itshowcase/blog/running-on-vpn-how-microsoft-is-keeping-its-remote-workforce-connected/?elevate-lv)

[Microsoft genel ağı](/azure/networking/microsoft-global-network)
