---
title: Cihaz bulma hakkında sık sorulan sorular
description: Cihaz bulma hakkında sık sorulan soruların (SSS) yanıtlarını bulma
keywords: cihaz bulma, bulma, pasif, proaktif, ağ, görünürlük, sunucu, iş istasyonu, ekleme, yönetilmeyen cihazlar
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
ms.openlocfilehash: 54a1b816f3d1322cab5558e5bd09d5d9b4285ae8
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2022
ms.locfileid: "64665018"
---
# <a name="device-discovery-frequently-asked-questions"></a>Cihaz bulma hakkında sık sorulan sorular

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Şunlar için geçerlidir:**
- - [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

[!include[Prerelease information](../../includes/prerelease.md)]

Cihaz bulma hakkında sık sorulan soruların (SSS) yanıtlarını bulun.

## <a name="what-is-basic-discovery-mode"></a>Temel bulma modu nedir?

Bu mod, eklenen her Uç Nokta için Microsoft Defender cihazın ağ verilerini toplamasına ve komşu cihazları bulmasına olanak tanır. Eklenen uç noktalar, ağdaki olayları pasif olarak toplar ve onlardan cihaz bilgilerini ayıklar. Ağ trafiği başlatılmaz. Eklenen uç noktalar, eklenen bir cihaz tarafından görülen her ağ trafiğinden verileri ayıklar. Ağınızdaki yönetilmeyen cihazları listelemek için kullanılan bu veriler.

## <a name="can-i-disable-basic-discovery"></a>Temel bulma özelliğini devre dışı bırakabilir miyim?

[Gelişmiş özellikler](advanced-features.md) sayfasından cihaz bulmayı kapatma seçeneğiniz vardır. Ancak ağınızdaki yönetilmeyen cihazlarda görünürlüğü kaybedersiniz. Bulma özelliği kapatılsa da eklenen cihazlarda SenseNDR.exe çalışmaya devam edeceğine dikkat edin. 

## <a name="what-is-standard-discovery-mode"></a>Standart bulma modu nedir?

bu modda Uç Nokta için Microsoft Defender eklenen uç noktalar, toplanan verileri zenginleştirmek için ağdaki gözlemlenen cihazları etkin bir şekilde yoklayabilir (göz ardı edilebilir miktarda ağ trafiğiyle). Yalnızca temel bulma modu tarafından gözlemlenen cihazlar standart modda etkin bir şekilde yoklanır. Bu mod, güvenilir ve tutarlı bir cihaz envanteri oluşturmak için kesinlikle önerilir. Bu modu devre dışı bırakmayı ve Temel bulma modunu seçerseniz, büyük olasılıkla ağınızdaki yönetilmeyen uç noktaların yalnızca sınırlı görünürlüğünü elde edebilirsiniz.

 Standart mod, pasif yöntem kullanılarak gözlemlenenlere ek olarak daha fazla cihaz bulmak için ağda çok noktaya yayın sorguları kullanan yaygın bulma protokollerinden de yararlanıyor.

## <a name="can-i-control-which-devices-perform-standard-discovery"></a>Hangi cihazların Standart bulma gerçekleştirebileceğini denetleyebilirim?

Standart bulma gerçekleştirmek için kullanılan cihazların listesini özelleştirebilirsiniz. Bu özelliği de destekleyen tüm eklenen cihazlarda Standart bulma özelliğini etkinleştirebilir (şu anda yalnızca Windows 10 veya üzeri ve Windows Server 2019 veya üzeri cihazlar) ya da cihaz etiketlerini belirterek cihazlarınızın alt kümesini veya alt kümelerini seçebilirsiniz. Bu durumda, diğer tüm cihazlar yalnızca Temel bulma'yı çalıştıracak şekilde yapılandırılır. Yapılandırma, cihaz bulma ayarları sayfasında sağlanır.

## <a name="can-i-exclude-unmanaged-devices-from-the-device-inventory-list"></a>Yönetilmeyen cihazları cihaz envanter listesinden dışlayabilir miyim?

Evet, yönetilmeyen cihazları cihaz envanter listesinden dışlamak için filtreler uygulayabilirsiniz. Yönetilmeyen cihazları filtrelemek için API sorgularında ekleme durumu sütununu da kullanabilirsiniz.

## <a name="which-onboarded-devices-can-perform-discovery"></a>Hangi eklenen cihazlar bulma gerçekleştirebilir?

Windows 10 sürüm 1809 veya üzeri, Windows 11, Windows Server 2019 veya Windows Server 2022 üzerinde çalışan eklenen cihazlar bulma gerçekleştirebilir.

## <a name="what-happens-if-my-onboarded-devices-is-connected-to-my-home-network-or-to-public-access-point"></a>Eklenen cihazlarım ev ağıma veya genel erişim noktasına bağlıysa ne olur?

Bulma altyapısı, şirket ağında alınan ağ olaylarını kurumsal ağın dışından ayırt eder. Ağ tanımlayıcıları tüm kiracının istemcileri arasında ilişkilendirilerek olaylar, özel ağlardan ve şirket ağlarından alınanlar arasında ayırt edilir. Örneğin, kuruluştaki cihazların büyük bölümü aynı ağ adına, aynı varsayılan ağ geçidine ve DHCP sunucu adresine bağlı olduklarını bildirirse, bu ağın büyük olasılıkla bir şirket ağı olduğu varsayılabilir. Özel ağ cihazları envanterde listelenmez ve etkin bir şekilde yoklanmaz.

## <a name="what-protocols-are-you-capturing-and-analyzing"></a>Hangi protokolleri yakalayıp analiz ediyorsunuz?

Varsayılan olarak, Windows 10 sürüm 1809 veya sonraki sürümlerde çalışan tüm eklenen cihazlar, Windows 11, Windows Server 2019 veya Windows Server 2022 şu protokolleri yakalayıp analiz ediyor: ARP, CDP, DHCP, DHCPv6, IP (üst bilgiler), LLDP, LLMNR, mDNS, MNDP, NBNS, SSDP, TCP (SYN üst bilgileri), UDP (üst bilgiler), WSD

## <a name="which-protocols-do-you-use-for-active-probing-in-standard-discovery"></a>Standart bulmada etkin yoklama için hangi protokolleri kullanırsınız?
Bir cihaz Standart bulma çalıştıracak şekilde yapılandırıldığında, Kullanıma sunulan hizmetler şu protokoller kullanılarak araştırılıyor: ARP, FTP, HTTP, HTTPS, ICMP, LLMNR, NBNS, RDP, SIP, SMTP, SNMP, SSH, Telnet, UPNP, WSD, SMB, NBSS, IPP, PJL, RPC, mDNS, DHCP, AFP, CrestonCIP, IphoneSync, WinRM, VNC, SLP, LDAP


## <a name="how-can-i-exclude-targets-from-being-probed-with-standard-discovery"></a>Standart bulma ile hedeflerin yoklanmasını nasıl dışlayabilirim?

Ağınızda etkin olarak araştırılmaması gereken cihazlar varsa, taranmalarını önlemek için bir dışlama listesi de tanımlayabilirsiniz. Yapılandırma, cihaz bulma ayarları sayfasında sağlanır.

> [!NOTE]
> Cihazlar yine de ağdaki çok noktaya yayın bulma girişimlerini yanıtlayabilir. Bu cihazlar bulunur ancak etkin bir şekilde yoklamaz. 

## <a name="can-i-exclude-devices-from-being-discovered"></a>Cihazların bulunmasını dışlayabilir miyim?

Cihaz bulma, ağdaki cihazları bulmak için pasif yöntemler kullandığından, şirket ağındaki eklenen cihazlarınızla iletişim kuran tüm cihazlar bulunabilir ve envanterde listelenebilir. Cihazları yalnızca etkin yoklamanın dışında tutabilirsiniz.

## <a name="how-frequent-is-the-active-probing"></a>Etkin yoklama ne sıklıktadır?

Mevcut bilgilerin güncel olduğundan emin olmak için cihaz özelliklerindeki değişiklikler gözlemlendiğinde cihazlar etkin bir şekilde yoklanır (genellikle, cihazlar üç haftalık bir süre içinde en fazla bir kez yoklanır)

## <a name="my-security-tool-raised-alert-on-unicastscannerps1--psscript_guidps1-or-port-scanning-activity-initiated-by-it-what-should-i-do"></a>Güvenlik aracım tarafından başlatılan UnicastScanner.ps1 /PSScript_{GUID}.ps1 veya bağlantı noktası tarama etkinliğinde uyarı tetikledi, ne yapmalıyım?

Etkin yoklama betikleri Microsoft tarafından imzalandığından güvenlidir. Dışlama listenize aşağıdaki yolu ekleyebilirsiniz: `C:\ProgramData\Microsoft\Windows Defender Advanced Threat Protection\Downloads\*.ps1`

## <a name="what-is-the-amount-of-traffic-being-generated-by-the-standard-discovery-active-probe"></a>Standart bulma etkin yoklaması tarafından oluşturulan trafik miktarı nedir?

Etkin yoklama, eklenen cihaz ve yoklama cihazı arasında her yoklama girişiminde 50 KB'a kadar trafik oluşturabilir

## <a name="why-is-there-a-discrepancy-between-can-be-onboarded-devices-in-the-device-inventory-and-the-number-of-devices-to-onboard-in-the-dashboard-tile"></a>Cihaz envanterindeki "eklenebilir" cihazlar ile pano kutucuğundaki "eklenecek cihazlar" arasında neden bir tutarsızlık var?

Cihaz envanterinde "eklenebilir" altında listelenen cihazların sayısı, "Uç Nokta için Microsoft Defender'a ekleme" güvenlik önerisi ve "eklenecek cihazlar" pano pencere öğesi arasında farklar görebilirsiniz.

 Güvenlik önerisi ve pano pencere öğesi ağdaki kararlı cihazlara yöneliktir; kısa ömürlü cihazlar, konuk cihazlar ve diğerleri hariç. Fikir, kuruluşun genel güvenlik puanına da işaret eden kalıcı cihazlarda önermektir.

## <a name="can-i-onboard-unmanaged-devices-that-were-found"></a>Bulunan yönetilmeyen cihazları ekleyebilir miyim?

Evet. Yönetilmeyen cihazları el ile ekleyebilirsiniz. Ağınızdaki yönetilmeyen uç noktalar ağınıza güvenlik açıkları ve riskler getirir. Bunları hizmete eklemek, bu hizmetlerde güvenlik görünürlüğünü artırabilir.

## <a name="ive-noticed-that-unmanaged-device-health-state-is-always-active-why-is-that"></a>Yönetilmeyen cihaz sistem durumunun her zaman "Etkin" olduğunu fark ettim, neden bu?

Gerçek durumları ne olursa olsun, cihaz envanterinin standart saklama süresi boyunca geçici olarak yönetilmeyen cihaz sistem durumu "Etkin" olur.

## <a name="does-standard-discovery-look-like-malicious-network-activity"></a>Standart bulma kötü amaçlı ağ etkinliği gibi görünüyor mu?

Standart bulmayı değerlendirirken, yoklamanın etkilerini ve özellikle güvenlik araçlarının kötü amaçlı etkinlik gibi etkinliklerden şüphelenip şüphelenmeyeceğini merak ediyor olabilirsiniz. Aşağıdaki alt bölüm, neredeyse tüm durumlarda kuruluşların Standart bulmayı etkinleştirme konusunda neden endişeleri olmaması gerektiğini açıklar.  

### <a name="probing-is-distributed-across-all-windows-devices-on-the-network"></a>Yoklama, ağdaki tüm Windows cihazlara dağıtılır

Genellikle az sayıda güvenliği aşılmış cihazdan ağın tamamını tarayan kötü amaçlı etkinliklerin aksine, Uç Nokta için Microsoft Defender Standart bulma yoklama işlemi, etkinliği zararsız ve anormal olmayan hale getiren tüm eklenen Windows cihazlardan başlatılır. Yoklama, ağdaki desteklenen tüm eklenen cihazlar arasında yoklama girişimini dengelemek için buluttan merkezi olarak yönetilir.  

### <a name="active-probing-generates-negligible-amount-of-extra-traffic"></a>Etkin yoklama göz ardı edilebilir miktarda ek trafik oluşturur

Yönetilmeyen cihazlar genellikle üç haftalık bir süre içinde en fazla bir kez yoklanır ve 50 KB'tan az trafik oluşturur. Kötü amaçlı etkinlikler genellikle yüksek yinelenen yoklama girişimlerini ve bazı durumlarda ağ izleme araçları tarafından anomali olarak tanımlanabilen önemli miktarda ağ trafiği oluşturan veri sızdırmayı içerir.

### <a name="your-windows-device-already-runs-active-discovery"></a>Windows cihazınız zaten etkin bulma çalıştırıyor

Etkin bulma özellikleri, ağdaki uç noktalar arasında daha kolay "tak çalıştır" deneyimleri ve dosya paylaşımı için yakındaki cihazları, uç noktaları ve yazıcıları bulmak için her zaman Windows işletim sistemine eklenmiştir. Benzer işlevler mobil cihazlarda, ağ ekipmanında ve envanter uygulamalarında yalnızca birkaç adla uygulanır.  

Standart bulma, cihazları tanımlamak ve Microsoft 365 Defender Cihaz Envanteri'nde ağınızdaki tüm cihazlar için birleşik görünürlüğe sahip olmak için aynı bulma yöntemlerini kullanır. Örneğin– Standart bulma, ağdaki yakın uç noktaları ağdaki kullanılabilir yazıcıları Windows şekilde tanımlar. 

Ağ güvenliği ve izleme araçları, ağdaki cihazlar tarafından gerçekleştirilen bu tür etkinliklere kayıtsızdır. 

### <a name="only-unmanaged-devices-are-being-probed"></a>Yalnızca yönetilmeyen cihazlar yoklanıyor

Cihaz bulma özellikleri yalnızca ağınızdaki yönetilmeyen cihazları bulmak ve tanımlamak için oluşturulmuş. Bu, önceden bulunan ve önceden Uç Nokta için Microsoft Defender eklenen cihazların yoklanmayacağı anlamına gelir.

### <a name="you-can-exclude-network-lures-from-active-probing"></a>Ağ yemlerini etkin yoklamanın dışında tutabilirsiniz

Standart bulma, cihazların veya aralıkların (alt ağlar) etkin yoklamadan dışlanmasını destekler. Dağıtılan ağ yemleriniz varsa, IP adreslerine veya alt ağlara (bir dizi IP adresi) dayalı dışlamaları tanımlamak için Cihaz Bulma ayarlarını kullanabilirsiniz. Bu dışlamaları tanımlamak, bu cihazların etkin bir şekilde yoklanmamasını ve uyarı almamasını sağlar. Bu cihazlar yalnızca pasif yöntemler kullanılarak bulunur (Temel bulma moduna benzer).
