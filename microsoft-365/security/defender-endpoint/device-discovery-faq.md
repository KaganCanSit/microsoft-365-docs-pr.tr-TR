---
title: Cihaz bulma ile ilgili sık sorulan sorular
description: Cihaz bulma hakkında sık sorulan soruların (SSS) yanıtlarını bulma
keywords: cihaz bulma, keşif, pasif, proaktif, ağ, görünürlük, sunucu, iş istasyonu, ekleme, yönetimi olmayan cihazlar
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: m365-security-compliance
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: 530846d4a7c18900f0697806bb656aa653b71947
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63326181"
---
# <a name="device-discovery-frequently-asked-questions"></a>Cihaz bulma ile ilgili sık sorulan sorular

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- - [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

[!include[Prerelease information](../../includes/prerelease.md)]

Cihaz bulma hakkında sık sorulan soruların (SSS) yanıtlarını bulun.

## <a name="what-is-basic-discovery-mode"></a>Temel bulma modu nedir?

Bu mod, uç nokta için her Microsoft Defender ekli cihazın ağ verilerini toplamasını ve komşu cihazları keşfetmesini sağlar. Yerleşik uç noktalar pasif olarak ağ üzerindeki olayları toplar ve onlardan cihaz bilgilerini ayıklar. Hiçbir ağ trafiği başlatılacaktır. Onboarded endpoints will simply extract data from every network traffic that is seen by an onboarded device. Bu veriler, ağ bağlantısı olmayan cihazları listelerken kullanılır.

## <a name="can-i-disable-basic-discovery"></a>Temel bulma'ya devre dışı musunuz?

Gelişmiş özellikler sayfası aracılığıyla cihaz bulma'ya kapatma [seçeneğiniz](advanced-features.md) vardır. Bununla birlikte, ağ bağlantınız altında olmayan cihazlarda görünürlüğü kaybedeceksiniz. Keşif SenseNDR.exe bakılmaksızın, yerleşik cihazlarda her bağlantının hala çalışıyor olacağını unutmayın. 

## <a name="what-is-standard-discovery-mode"></a>Standart bulma modu nedir?

Uç nokta için Microsoft Defender'a alınan bu modda uç noktalar, toplanan verileri zenginleştirmek için (uygun olmayan ağ trafiği miktarıyla) ağda gözlemlenen cihazları etkin bir şekilde gözlemlenebilir. Yalnızca temel bulma modu tarafından gözlemlenen cihazlar standart modda etkin bir şekilde gözlenir. Bu mod, güvenilir ve tutarlı bir cihaz stoku için kesinlikle önerilir. Bu modu devre dışı bırakmayı ve Temel bulma modunu seçerseniz, büyük olasılıkla yalnızca ağ bağlantınız içinde, bağlantıların sınırlı görünürlüğünü kazanırsınız.

 Standart mod aynı zamanda pasif yöntemi kullanılarak gözlemlenenlere ek olarak daha fazla cihaz bulmak için ağda sorgular kullanan yaygın bulma protokolleri kullanır.

## <a name="can-i-control-which-devices-perform-standard-discovery"></a>Hangi cihazların Standart keşif gerçekleştireceklerini kontrol  olabilir miyim?

Standart keşif gerçekleştirmek için kullanılan cihazların listesini özelleştirebilirsiniz. Bu özelliği de destekleyen tüm yerleşik cihazlarda (şu anda Windows 10 veya daha sonraki bir sürümü ve yalnızca Windows Server 2019 veya daha sonraki cihazlar) Standart bulma özelliğini etkinleştirebilirsiniz veya cihaz etiketlerini belirterek cihazlarınızı bir alt küme veya alt küme olarak belirleyebilirsiniz. Bu durumda, diğer tüm cihazlar yalnızca Temel keşif'i çalıştıracak şekilde yapılandırılır. Yapılandırma, cihaz bulma ayarları sayfasında kullanılabilir.

## <a name="can-i-exclude-unmanaged-devices-from-the-device-inventory-list"></a>Yönetimi olmayan cihazları cihaz stok listesinden çıkarabilirsiniz mi?

Evet, yönetimi olmayan cihazları cihaz stok listesinden dışarıda tutmak için filtreler uygulayabilirsiniz. Ayrıca, yönetimi olmayan cihazları filtrelemek için API sorgularında ekleme durumu sütununu da kullanabilirsiniz.

## <a name="which-onboarded-devices-can-perform-discovery"></a>Hangi yerleşik cihazlar keşif gerçekleştirebilirsiniz?

Windows 10 sürüm 1809 veya sonraki sürümler, Windows 11, Windows Server 2019 veya Windows Server 2022 bulunan yerleşik cihazlar keşif gerçekleştirebilirsiniz.

## <a name="what-happens-if-my-onboarded-devices-is-connected-to-my-home-network-or-to-public-access-point"></a>Cihazlarım ev ağıma veya genel erişim noktasına bağlı olursa ne olur?

Keşif altyapısı, şirket ağına alınan ağ olaylarını şirket ağının dışından ayırt edicidir. Ağ tanımlayıcılarını tüm kiracının istemcileri arasında birbiriyle ilişkili olarak, olaylar özel ağlardan ve şirket ağlarından alınanlar arasında ayırt edilir. Örneğin, kuruluşta cihazların çoğunluğu aynı ağ adına, aynı varsayılan ağ geçidi ve ZAMAN sunucusu adresine bağlı olduğunu bildirse, bu ağın büyük olasılıkla bir şirket ağı olduğu varsayılır. Özel ağ cihazları stokta listelenmiyor ve etkin bir şekilde ağulanmayacak.

## <a name="what-protocols-are-you-capturing-and-analyzing"></a>Hangi protokolleri yakalama ve çözümlemektesiniz?

Varsayılan olarak, sürüm 1809 veya Windows 10 çalıştıran tüm yerleşik cihazlar, Windows 11, Windows Server 2019 veya Windows Server 2022 aşağıdaki protokolleri yakalayarak analiz ediyor: ARP, CDP, UDP, DHCPv6, IP (üst bilgiler), LLDP, LLMNR, mDNS, MNDP, NBNS, SSDP, TCP (SYN üst bilgileri), UDP (üst bilgiler), WSD

## <a name="which-protocols-do-you-use-for-active-probing-in-standard-discovery"></a>Standart bulma'da etkin olasılıklar için hangi protokolleri kullanasınız?
Bir cihaz Standart bulma'yi çalıştıracak şekilde yapılandırıldığında, aşağıdaki protokoller kullanılarak ortaya çıkar: ARP, FTP, HTTP, HTTPS, ICMP, LLMNR, NBNS, RDP, SIP, SMTP, SNMP, SSH, Telnet, UPNP, WSD, SMB, NBSS, IPP, PJL, RPC, mDNS, LDAP, AFP, CrestonCIP, IphoneSync, WinRM, VNC, SLP, LDAP


## <a name="how-can-i-exclude-targets-from-being-probed-with-standard-discovery"></a>Hedefleri Standart keşif kapsamından nasıl çıkartırm?

Ağ üzerinde etkin bir şekilde sahip olunmaması gereken cihazlar varsa, bu cihazların taranmalarını önlemek için bir dışlama listesi de tanımlayabilirsiniz. Yapılandırma, cihaz bulma ayarları sayfasında kullanılabilir.

> [!NOTE]
> Cihazlar yine de ağda çok büyük keşif girişimlerine yanıt verir. Bu cihazlar keşfedilen ancak etkin bir şekilde sahip olunmayacak. 

## <a name="can-i-exclude-devices-from-being-discovered"></a>Cihazları bulunanların dışında tutabilirsiniz mi?

Cihaz bulma, ağ üzerindeki cihazları bulmak için pasif yöntemleri kullandığı için, şirket ağınıza ekli cihazlarınız ile iletişimde bulunan her cihaz stokta yer alan ve listelenmiş olabilir. Cihazları yalnızca etkin olasılıklar dışında tutabilirsiniz.

## <a name="how-frequent-is-the-active-probing"></a>Etkin olasılıklar ne sıklıkta?

Mevcut bilgilerin güncel olduğundan emin olmak için cihaz özelliklerinde yapılan değişiklikler gözlenirse (normalde, üç haftalık bir dönemde en fazla bir kez cihaz cihaza sahip değildir)

## <a name="my-security-tool-raised-alert-on-unicastscannerps1--psscript_guidps1-or-port-scanning-activity-initiated-by-it-what-should-i-do"></a>Güvenlik aracım tarafından başlatılan UnicastScanner.ps1 / PSScript_{GUID}.ps1 veya bağlantı noktası tarama etkinliği hakkında uyarı aldı, ne yapabilirim?

Etkin olasılık betikleri Microsoft tarafından imzalanmıştır ve güvenlidir. Dışlama listeniz için aşağıdaki yolu ekleyebilirsiniz: `C:\ProgramData\Microsoft\Windows Defender Advanced Threat Protection\Downloads\*.ps1`

## <a name="what-is-the-amount-of-traffic-being-generated-by-the-standard-discovery-active-probe"></a>Standart keşif etkin araştırma tarafından oluşturulan trafik miktarı nedir?

Etkin olasılık, her olasılık denemesi olan ve yerleşik cihazla cihaz arasında en fazla 50 Kb trafik üretebilirsiniz

## <a name="why-is-there-a-discrepancy-between-can-be-onboarded-devices-in-the-device-inventory-and-the-number-of-devices-to-onboard-in-the-dashboard-tile"></a>Neden cihaz envanteri içinde "kullanılabilir" cihazlar arasında bir uyuşmazlık ve pano kutucuğunun içinde "ekleme için" yapılan cihazların sayısı arasında bir uyuşmazlık var?

Listelenen cihazların sayısı ile cihaz envanteri içinde "eklensin" ifadesinin altında, "Uç nokta için Microsoft Defender'a ekle" güvenlik önerisi ve "ekleme için cihazlar" pano widget'ı arasında farklar olduğunu görebilirsiniz.

 Güvenlik önerisi ve pano widget'ı ağ üzerinde kararlı cihazlara göredir; ephemeral cihazlar, konuk cihazlar ve diğer cihazlar hariç. Amaç, kalıcı cihazlara, ayrıca kuruluşun genel güvenlik puanlarını da ima eden kalıcı cihazlar önermektedir.

## <a name="can-i-onboard-unmanaged-devices-that-were-found"></a>Bulunan, unmanaged cihazları eklemem gerekir mi?

Evet. Unmanaged cihazları el ile ekleyebilirsiniz. Ağ bağlantınız için yönelik olmayan uç noktalar, ağ bağlantınız için güvenlik açıklarına ve risklere neden olur. Bunları hizmete ekleme, güvenlik görünürlüğünü artırabilir.

## <a name="ive-noticed-that-unmanaged-device-health-state-is-always-active-why-is-that"></a>Cihazın durumu, neden her zaman "Etkin" olduğunu fark ettim.

Cihaz durumu ne olursa olsun, geçici olarak, cihaz envanteri standart bekletme süresi boyunca "Etkin" durumda olur.

## <a name="does-standard-discovery-look-like-malicious-network-activity"></a>Standart keşif kötü amaçlı ağ etkinliklerine mi benziyor?

Standart keşifleri göz önünde bulundurarak, olasılıkların etkilerini ve özel olarak güvenlik araçlarının bu tür etkinliklerden kötü amaçlı olarak şüpheleniyor olup olmadığını merak ediyor olabilir. Aşağıdaki alt bölüm, kuruluşların neredeyse tüm durumlarda Standart keşifleri etkinleştirme konusunda kaygıları olması gerektiğini açıklar.  

### <a name="probing-is-distributed-across-all-windows-devices-on-the-network"></a>Olasılık, ağ Windows tüm cihazlarda dağıtılıyor

Normalde güvenliği tehlikeye atılmış az sayıda cihazdan ağın tamamını tarayacak olan kötü amaçlı etkinliklere karşı olarak, Uç Nokta'nın Standart keşif olasılıkları için Microsoft Defender, etkinliği her zaman anormal ve anormal olmayan hale gelen tüm yerleşik Windows cihazlarından başlatılır. Olasılık, ağ üzerindeki desteklenen tüm yerleşik cihazlar arasındaki olasılık denemesini dengelemek için buluttan merkezi olarak yönetilir.  

### <a name="active-probing-generates-negligible-amount-of-extra-traffic"></a>Etkin olasılık, uygun olmayan trafik miktarına neden olur

Unmanaged devices would normalde get no more than once in a three-week period and generate less 50KB of traffic. Kötü amaçlı etkinlikler çoğunlukla yüksek tekrarlı olasılık girişimlerini ve bazı durumlarda da ağ izleme araçlarıyla anormal olarak tanım edilemeyen önemli miktarda ağ trafiğine neden olan veri sızıntısını içerir.

### <a name="your-windows-device-already-runs-active-discovery"></a>Windows cihazınız zaten etkin keşifleri çalıştırır

Ağın uç noktaları arasında daha kolay "tak ve oynat" deneyimleri ve dosya paylaşımını kolaylaştırmak için etkin bulma özellikleri Windows işletim sistemine eklenmişti. Benzer işlevler mobil cihazlarda, ağ ekipmanında ve stok uygulamalarında yalnızca birkaçıdır.  

Standart bulma, cihazları tanımlamak ve aynı bulma yöntemlerini kullanarak, aynı bulma yöntemlerini kullanarak, aynı mobil cihaz Envanteri'nin altında ağ'daki tüm cihazlar için birleşik Microsoft 365 Defender olur. Örneğin – Standart bulma, ağ'daki yakındaki uç noktaları aynı ağ Windows yazıcıları listeleyeni gibi tanımlar. 

Ağ güvenliği ve izleme araçları, ağ üzerinde cihazlar tarafından gerçekleştirilen bu tür etkinliklere kayıtsızdır. 

### <a name="only-unmanaged-devices-are-being-probed"></a>Yalnızca unmanaged devices are being esnad

Cihaz bulma özellikleri, yalnızca ağ üzerinde yönetimi olmayan cihazları keşfetmek ve tanımlamak için yerleşik olarak bulundu. Bu, daha önce Uç Nokta için Microsoft Defender ile birlikte edinilen cihazların satın alıma açık olduğu anlamına gelir.

### <a name="you-can-exclude-network-lures-from-active-probing"></a>Ağ nedenlerini etkin olasılıktan çıkarabilirsiniz

Standart keşif, etkin olasılıklardan cihazların veya aralıkların (alt ağların) hariç tutulmasını destekler. Dağıtılan ağ hedefleriniz varsa, IP adreslerine veya alt ağlara (IP adresleri aralığı) dayalı dışlamaları tanımlamak için Cihaz Bulma ayarlarını kullanabilirsiniz. Bu dışlamaların tanımlanması, bu cihazların etkin şekilde uyarılmalarını ve uyarılmalarını sağlar. Bu cihazlar yalnızca pasif yöntemleri kullanılarak keşfeder (Temel bulma moduna benzer).
