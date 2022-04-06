---
title: VPN bölünmüş tüneli için Teams medya trafiğinin güvenliğini sağlama
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
description: VPN bölünmüş tüneli için Teams medya trafiğinin güvenliğini sağlama
ms.openlocfilehash: 0f16ed8f7f9721a79375f05f7b889bc8aab2d824
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63704942"
---
# <a name="securing-teams-media-traffic-for-vpn-split-tunneling"></a>VPN bölünmüş tüneli için Teams medya trafiğinin güvenliğini sağlama

>[!NOTE]
>Bu makale, uzak kullanıcılar için iyileştirmeyi Microsoft 365 makale kümelerinin bir bölümüdir.

>- Uzak kullanıcılar için Microsoft 365 bağlantısını en iyi duruma getirmek için VPN bölünmüş şifreleme kullanma hakkında genel bir bakış için bkz[.](microsoft-365-vpn-split-tunnel.md) Genel Bakış: Vpn bölünmüş Microsoft 365.
>- VPN bölünmüş bölmeyi uygulama hakkında ayrıntılı kılavuz için bkz. [VPN bölünmüş bölmeyi uygulama Microsoft 365](microsoft-365-vpn-implement-split-tunnel.md).
>- VPN bölünmüş bölme senaryolarının ayrıntılı listesi için bkz. Daha fazla bilgi için bkz. Genel [VPN bölünmüş Microsoft 365](microsoft-365-vpn-common-scenarios.md).
>- VPN ortamlarında Stream ve canlı etkinlikleri yapılandırma hakkında bilgi için bkz. VPN ortamlarında akış ve canlı etkinlikler [için dikkat edilmesi gereken noktalar](microsoft-365-vpn-stream-and-live-events.md).
>- Çin'deki kullanıcılar için Microsoft 365 kiracı performansını iyileştirme hakkında bilgi için bkz. [Microsoft 365 için performans iyileştirme.](microsoft-365-networking-china.md)

Bazı Microsoft Teams yöneticileri, bölünmüş bir geçiş modelini kullanan Teams akışların Teams bağlantı güvenliği nasıl sağlandı hakkında ayrıntılı bilgi gerektirir.

## <a name="configuration"></a>Yapılandırma

Hem çağrılar hem de toplantılar için, Teams medyası için gerekli IP alt ağlarını yol tablosunda doğru olarak iyi duruma getirmekse, Teams hangi yerel arabirimin belirli bir hedef için kullanması gereken yönlendirmeye karşılık geldiğinde[,](/windows/win32/api/iphlpapi/nf-iphlpapi-getbestroute) yukarıda listelenen Microsoft IP bloklarında Microsoft hedefleri için yerel arabirim döndürülür.

Bazı VPN istemci yazılımları URL'ye göre yönlendirme işlemeye izin verir. Bununla birlikte Teams medya trafiğinin URL'si yoktur, bu nedenle bu trafik için yönlendirmenin denetimi IP alt ağları kullanılarak yapılması gerekir.

Bazı senaryolarda, genellikle istemci Teams ilgili olmayan medya trafiği yerine doğru yönlendirmeler olsa bile VPN trafiğine çapraz geçişlere neden olur. Bu senaryoyla karşılaşırsanız, IP alt ağlarının veya VPN'nin Teams bağlantı noktalarını engellemek için güvenlik duvarı kuralı kullanmak yeterlidir.

>[!IMPORTANT]
>Medya trafiğinin Teams VPN senaryolarında istenen yöntem ile yönlendirilebilir olduğundan emin olmak için, lütfen kullanıcıların Microsoft Teams **1.3.00.13565** veya daha yeni bir sürüm çalıştır çalıştırya olduğundan emin olun. Bu sürüm, istemcinin kullanılabilir ağ yollarını algılaması ile ilgili geliştirmeler içerir.

Trafiğin sinyali HTTPS üzerinden yapılır, medya trafiği kadar gecikmeye duyarlı değildir ve URL/IP verisinde İzin Ver olarak  işaretlenir ve böylece istenirse VPN istemcisi üzerinden güvenli bir şekilde yönlendirilebilir.

>[!NOTE]
>Microsoft Edge **96 ve üzeri**, eşler arası trafik için VPN bölünmüş şifrelemeyi de destekler. Bu da, örneğin müşterilerin Edge'de web istemcilerinde VPN bölünmüş Teams avantajından yararlanabilecekleri anlamına gelir. Edge'de çalışan web siteleri için ayarlamak isteyen müşteriler, Edge [WebRtcRespectOsRoutingTableEnabled](/deployedge/microsoft-edge-policies#webrtcrespectosroutingtableenabled) İlkesini etkinleştirmenin ek adımlarını atarak bunu elde edebilirsiniz.

### <a name="security"></a>Güvenlik

Bölünmüş bölmelerden kaçınmak için yaygın bir bağımsız değişken, örneğin böyle yapmak için daha az güvenlidir VPN hattından geç yapmayan trafikler VPN şemalarına uygulanan şifreleme düzeninden yararlanmayacaktır ve bu nedenle daha az güvenli olur.

Bunun ana bağımsız değişkeni, medya trafiğinin RTP trafiğine gizlilik, kimlik doğrulama ve saldırı koruması sağlayan bir Real-Time Aktarım Protokolü (RTP) profili olan Güvenli Real-Time Aktarım Protokolü _(SRTP_) aracılığıyla zaten şifrelenmiş durumdadır. SRTP'nin kendisi, TLS güvenli sinyal kanalı üzerinden yapılan rastgele oluşturulmuş bir oturum anahtarına dayandır. Bu, bu güvenlik kılavuzunda çok [ayrıntılı olarak ele almaktadır](/skypeforbusiness/optimizing-your-network/security-guide-for-skype-for-business-online), ancak ilgili birincil bölüm medya şifrelemedir.

Medya trafiği, güvenli bir rastgele sayı oluşturucu tarafından oluşturulan ve sinyal TLS kanalı kullanılarak değişten bir oturum anahtarı kullanan SRTP kullanılarak şifrelenir. Buna ek olarak, Ara Sunucu ile bir sonraki iç atlama arasında her iki yönde de akan medya da SRTP kullanılarak şifrelenir.

Skype Kurumsal Online, NAT (TURN) çevresinde Geçişleri Kullanarak Çapraz Geçiş üzerinden medya geçişlerine güvenli erişim için kullanıcı adı/_parolalar üretir_. Medya geçişleri, kullanıcı adını/parolayı TLS güvenliği olan bir SIP kanalı üzerinden değiştirmektedir. İstemciyi şirket ağına bağlamak için VPN yolu kullansanız bile trafiğin hizmete ulaşmak için şirket ağına ulaşacak şekilde SRTP biçimine akmaya devam ediyor olması gerekir.

Teams _NAT (STUN)_ amplification saldırılarının ses veya Oturum Çapraz Yardımcı Programları gibi yaygın güvenlik endişelerini nasıl azaltmakta olduğuyla ilgili bilgiler [, Uygulamacılar için 5.1](/openspecs/office_protocols/ms-ice2/69525351-8c68-4864-b8a6-04bfbc87785c) GüvenlikLe ilgili Dikkate Alınacak Noktalar'da bulunabilir.

Ayrıca, uzak çalışma senaryolarında modern güvenlik denetimleri hakkında bilgi edinebilirsiniz. Bunun için, güvenlik uzmanları ve BT'nin günümüzün benzersiz uzaktan çalışma senaryolarında modern güvenlik denetimlerine ulaşmanın alternatif yolları [(Microsoft Güvenlik Ekibi blogu)](https://www.microsoft.com/security/blog/2020/03/26/alternative-security-professionals-it-achieve-modern-security-controls-todays-unique-remote-work-scenarios/)'nda da okuyabilirsiniz.

### <a name="testing"></a>Test

İlke tamam olduktan sonra, İlke'nin beklendiği gibi çalıştığını onaylamanız gerekir. Yolu yerel İnternet bağlantısını kullanmak için doğru olarak ayarlanmış olan birden çok test yolu vardır:

- Yukarıda [Microsoft 365 izleme yollarını](https://aka.ms/netonboard) da dahil olmak üzere sizin için bağlantı testleri çalıştıracak olan hızlı bağlantı testini çalıştırın. Ayrıca bu araçta, ek içgörüler de sağlayacak ŞEKILDE VPN testleri ekliyoruz.

- Bölünmüş yolun **kapsamı** içindeki bir uç noktasına giden basit bir izleme yolu, alınan yolu gösterse, örneğin:

  ```powershell
  tracert worldaz.tr.teams.microsoft.com
  ```

  Ardından, yerel ISS üzerinden bu uç noktaya giden ve bölünmüş bölme için yapılandırmış Teams aralıklarında bir IP'ye çözümlemesi gereken bir yol görüyorsanız.

- Wireshark gibi bir aracı kullanarak ağ yakalaması alma. Arama sırasında UDP'ye göre filtre uygulama ve En İyi Duruma Getirme aralığında **IP'ye** Teams gerekir. Bu trafik için VPN trafiği kullanılıyorsa, medya trafiği izlemede görünmez.

## <a name="additional-support-logs"></a>Ek destek günlükleri

Sorun gidermek için daha fazla veriye ihtiyacınız varsa veya Microsoft desteğinden yardım bekliyorsanız, aşağıdaki bilgileri almak çözüm bulma işleminizi hızlandırabilirsiniz. Microsoft desteğinin **TSS Windows CMD tabanlı evrensel** Sorun Betik araçları, ilgili günlükleri basit bir şekilde toplamanıza yardımcı olabilir. Araç ve kullanım yönergelerini burada bulunabilir <https://aka.ms/TssTools>.

## <a name="related-articles"></a>İlgili makaleler

[Genel bakış: VPN bölme bölme Microsoft 365](microsoft-365-vpn-split-tunnel.md)

[VPN bölmeli bölme Microsoft 365](microsoft-365-vpn-implement-split-tunnel.md)

[Kullanıcılar için yaygın VPN bölme bölme Microsoft 365](microsoft-365-vpn-common-scenarios.md)

[VPN ortamlarında Stream ve canlı etkinlikler için dikkat edilmesi gereken noktalar](microsoft-365-vpn-stream-and-live-events.md)

[Microsoft 365 kullanıcıları için performans iyileştirmeyi iyileştirme](microsoft-365-networking-china.md)

[Microsoft 365 Ağ Bağlantısı İlkeleri](microsoft-365-network-connectivity-principles.md)

[Microsoft 365 ağ bağlantısını değerlendirme](assessing-network-connectivity.md)

[Microsoft 365 ve performans ayarını yapılandırma](network-planning-and-performance.md)

[Günümüzün benzersiz uzaktan çalışma senaryolarında güvenlik uzmanlarının ve BT'nin modern güvenlik denetimlerini elde etmenin alternatif yolları (Microsoft Güvenlik Ekibi blogu)](https://www.microsoft.com/security/blog/2020/03/26/alternative-security-professionals-it-achieve-modern-security-controls-todays-unique-remote-work-scenarios/)

[Microsoft'ta VPN performansını geliştirme: otomatik Windows 10 izin vermek için VPN profillerini kullanma](https://www.microsoft.com/itshowcase/enhancing-remote-access-in-windows-10-with-an-automatic-vpn-profile)

[VPN ile çalışma: Microsoft uzaktan iş gücüne nasıl bağlı tutarak](https://www.microsoft.com/itshowcase/blog/running-on-vpn-how-microsoft-is-keeping-its-remote-workforce-connected/?elevate-lv)

[Microsoft genel ağı](/azure/networking/microsoft-global-network)
