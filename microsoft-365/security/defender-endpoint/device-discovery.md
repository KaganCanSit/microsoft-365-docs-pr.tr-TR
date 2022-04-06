---
title: Cihaz keşfine genel bakış
description: Ağ 365'te, Microsoft 365 Defender olmayan cihazları bulmak için uç nokta bulmada nasıl yararlan yararlanıy öğrenin
keywords: cihaz bulma, keşif, pasif, proaktif, ağ, görünürlük, sunucu, iş istasyonu, ekleme, yönetimi olmayan cihazlar
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: siosulli
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
- m365-initiative-defender-endpoint
ms.custom: admindeeplinkDEFENDER
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: 926d23cb4e9abcecd9d34e976dee60851471613b
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64472935"
---
# <a name="device-discovery-overview"></a>Cihaz keşfine genel bakış

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta için Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

Ortamınızı korumak, ağda yer alan cihazların envanterini almak gerektirir. Bununla birlikte, bir ağ üzerinden eşleme cihazları genellikle pahalı, zorlu ve zaman alıcı olabilir.

Uç Nokta için Microsoft Defender, ek aletler veya zahmetli süreç değişikliklerine gerek kalmadan şirket ağınıza bağlı, yönetimi olmayan cihazları bulamıyorum bir cihaz bulma özelliği sağlar. Cihaz bulma, ağın içinde bulunan yerleşik uç noktaları, ağını toplamak, taramak veya taramak için, unmanaged cihazları bulmak için kullanır. Cihaz bulma özelliği şunları keşfetme olanağı sağlar:

- Enterprise henüz iş istasyonuna dahil edilemeyen uç noktaları (iş istasyonları, sunucular ve mobil cihazlar) Uç Nokta için Microsoft Defender
- Yönlendiriciler ve anahtarlar gibi ağ cihazları
- Yazıcılar ve kameralar gibi IoT cihazları

Eşleşmeyen bir yazıcı, zayıf güvenlik yapılandırmalarına sahip ağ cihazları veya güvenlik denetimleri olmayan bir sunucu gibi bilinmeyen ve belirlenemeyen cihazlar ağınıza önemli riskler gönderir. Cihazlar bulunduktan sonra şunlarıabilirsiniz:

- Hizmet için unmanaged endpoints onboard, bu uç noktalar üzerindeki güvenlik görünürlüğünü artırıyor.
- Güvenlik açıklarını tanımip değerlendirerek ve yapılandırma boşluklarını algıarak saldırı yüzeyini azaltın.

Cihaz bulmayla ilgili hızlı bir genel bakış için bu videoyu izleyin:

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWORdQ]

Bu özellikle birlikte, mevcut cihaz deneyiminin bir parçası olarak Uç Nokta için Microsoft Defender cihazları eklemeye yardımcı olacak bir Tehdit ve Güvenlik Açığı Yönetimi önerisi vardır.

## <a name="discovery-methods"></a>Bulma yöntemleri

Yerleşik cihazlarınız tarafından kullanılacak bulma modunu seçebilirsiniz. Mod, şirket ağınız içinde yönetimi olmayan cihazlar için edinebilirsiniz görünürlük düzeyini kontrol eder.

Kullanılabilir iki keşif modu vardır:

- **Temel bulma**: Bu modda, uç noktalar ağnizdeki olayları pasif olarak toplar ve onlardan cihaz bilgilerini ayıklar. Temel bulma, pasif SenseNDR.exe veri toplama için ikili olarak kullanılır ve ağ trafiği başlat olmaz. Uç noktalar yalnızca, bir cihaz tarafından görülen her ağ trafiğinden veri ayıklar. Temel bulma sayesinde, yalnızca ağ bağlantınız için unmanaged uç noktalarında sınırlı görünürlük elde olursiniz.

- **Standart bulma** (önerilen): Bu mod, uç noktaların toplanan verileri zenginleştirmek ve daha fazla cihaz keşfetmek için ağ'daki cihazları etkin bir şekilde bulmalarına olanak tanır ve güvenilir ve tutarlı bir cihaz envanteri oluşturmanıza yardımcı olur. Pasif yöntemi kullanılarak gözlemlenen cihazlara ek olarak, standart mod daha fazla cihaz bulmak için ağda sorgular kullanan yaygın bulma protokollerini de kullanır. Standart mod, gözlemlenen cihazlar hakkında mevcut cihaz bilgilerini zenginleştirmek için ek bilgiler bulmak için akıllı ve etkin olasılıklar kullanır. Standart modu etkinleştirildiğinde, keşif algılayıcısı tarafından oluşturulan çok az ve uygun olmayan ağ etkinlikleri, kurum içinde ağ izleme araçları tarafından gözlemlenebilir.

Bulma ayarlarınızı değiştirebilir ve özelleştirebilirsiniz. Daha fazla bilgi için bkz. Cihaz [bulma'yi yapılandırma](configure-device-discovery.md).

> [!IMPORTANT]
> 19 Temmuz 2021'den itibaren tüm müşteriler için standart keşif varsayılan moddur. Ayarlar sayfasından, bu yapılandırmayı temel yapılandırma olarak değiştirebilirsiniz. Temel modu seçerseniz, yalnızca ağ bağlantınız için unmanaged uç noktalarında sınırlı görünürlük kazanırsınız.

> [!NOTE]
> Keşif altyapısı, şirket ağına alınan ağ olaylarını şirket ağının dışından ayırt edicidir. Şirket ağlarına bağlı değil cihazlar, cihaz envanteri içinde keşfed olmaz veya listelenmiyor.

## <a name="device-inventory"></a>Cihaz envanteri

Bilgisayar tarafından henüz ekli veya güvenlik altına alınmış olan cihazlar Uç Nokta için Microsoft Defender ve Mobil cihazlar sekmesindeki cihaz envanteri içinde listelenir.

Bu cihazları değerlendirmek için, cihaz stoku listesinde Aşağıdaki değerlerden herhangi birini bulunduran Ekleme durumu adlı bir filtre kullanabilirsiniz:

- Eklemeli: Uç nokta, başka bir Uç Nokta için Microsoft Defender.
- Kullanılabilir: Uç nokta ağda keşfedildi ve İşletim Sistemi Uç Nokta için Microsoft Defender tarafından desteklenen bir uç nokta olarak tanımlanır, ancak şu anda eklemede değildir. Bu cihazları işe eklemenizi kesinlikle öneririz.
- Desteklenmiyor: Uç nokta ağda bulundu ancak diğer kullanıcılar tarafından Uç Nokta için Microsoft Defender.
- Yetersiz bilgi: Sistem, cihazın desteklanabilirliğini belirleyemedi. Ağ'daki diğer cihazlarda standart bulmanın etkinleştirilmesi, bulunan öznitelikleri zenginleştirebilirsiniz.

:::image type="content" source="images/2b62255cd3a9dd42f3219e437b956fb9.png" alt-text="Cihaz stoku panosu" lightbox="images/2b62255cd3a9dd42f3219e437b956fb9.png":::

> [!TIP]
> Yönetimi olmayan cihazları cihaz stok listesinden dışarıda tutmak için her zaman filtre uygulayabilirsiniz. Ayrıca, yönetimi olmayan cihazları filtrelemek için API sorgularında ekleme durumu sütununu da kullanabilirsiniz.

Daha fazla bilgi için bkz. [Cihaz envanteri](machines-view-overview.md).

## <a name="network-device-discovery"></a>Ağ cihazı bulma

Kuruluşta dağıtılan, fazla sayıdaki yönetimi olmayan ağ cihazları büyük bir saldırı alanı oluşturur ve tüm kuruluş için önemli bir riski temsil eder. Uç Nokta için Microsoft Defender bulma özellikleri, ağ cihazlarının varlık stoku içinde bulunmasına, doğru şekilde sınıflandırılması ve eklenmelerine yardımcı olur.

Ağ cihazları standart uç nokta olarak yönetilmiyor, çünkü Uç Nokta için Defender'ın kendi ağ cihazlarına yerleşik bir algılayıcısı olmaz. Bu tür cihazlar, uzaktan taramanın cihazlardan gerekli bilgileri edineni aracısız bir yaklaşım gerektirir. Bunu yapmak için, her Uç Nokta için Microsoft Defender kesimde önceden yapılandırılmış ağ cihazlarının düzenli olarak kimlik doğrulanmış taramalarını gerçekleştirmek için belirlenen bir kimlik doğrulama cihazı kullanılır. Bulunduktan sonra, Uç Nokta İçin Defender güvenlik Tehdit ve Güvenlik Açığı Yönetimi bulunan anahtarlar, yönlendiriciler, WLAN denetleyicileri, güvenlik duvarları ve VPN ağ geçitleri için tümleşik iş akışları sağlar.

Daha fazla bilgi için bkz. [Ağ cihazları](network-devices.md).

## <a name="device-discovery-integrations"></a>Cihaz Bulma Tümleştirmeleri

Eksiksiz OT/IOT varlık envanterini bulmak, belirlemek ve güvenliğini sağlamak üzere yeterli görünürlük elde etmek için Uç Nokta için Microsoft Defender şimdi aşağıdaki tümleştirmeleri destekler:

- **Corelight**: Microsoft, Corelight ağ cihazlarından veri almak için Corelight ile ortak çalışma kaydetti. Bu, Microsoft 365 Defender da içinde olmak üzere, diğer unmanaged cihazlar veya dış ağlarla iletişim gibi, unmand cihazların ağ etkinliklerine karşı daha fazla görünürlük sağlar. Daha fazla bilgi için bkz [. Corelight veri tümleştirmesini etkinleştirme](corelight-integration.md).

- **IoT için Microsoft Defender**: Bu tümleştirme, bir IT ağına bağlı kurumsal IoT cihazlarının (örneğin, İnternet Protokolü (VoIP), yazıcılar ve akıllı TV'ler gibi kurumsal IoT cihazlarının güvenliğini sağlamak için Uç Nokta için Microsoft Defender'ın cihaz bulma özellikleriyle IoT için Microsoft Defender'ın aracısız izleme özelliklerini birleştirir. Daha fazla bilgi için bkz [. IoT tümleştirmesi için Microsoft Defender'ı etkinleştirme](enable-microsoft-defender-for-iot-integration.md).

## <a name="vulnerability-assessment-on-discovered-devices"></a>Bulunan cihazlarda güvenlik açığı değerlendirmesi

Cihazlarınız ve ağ üzerinde bulunan diğer güvenlik açıkları ve riskler, ağda bulunan ve "Güvenlik Öneriler" kapsamındaki mevcut TVM akışlarının bir parçası ve portalda var olan varlık sayfalarında temsil edilenler.
Yönetilemeyen ve yönetilen cihazlarla ilgili SSH güvenlik açıklarını bulmak için "SSH" ile ilgili güvenlik önerilerini arama.

:::image type="content" source="images/1156c82ffadd356ce329d1cf551e806c.png" alt-text="Güvenlik önerileri panosu" lightbox="images/1156c82ffadd356ce329d1cf551e806c.png":::


## <a name="use-advanced-hunting-on-discovered-devices"></a>Bulunan cihazlarda Gelişmiş Av kullanma

Bulunan cihazlarda görünürlük kazanmak için Gelişmiş Av sorgularını kullanabilirsiniz.
CihazBilgileri tablosunda bulunan Uç Noktalar hakkında ayrıntıları veya DeviceNetworkInfo tablosunda bu cihazlar hakkında ağla ilgili bilgileri bulabilirsiniz.

:::image type="content" source="images/f48ba1779eddee9872f167453c24e5c9.png" alt-text="Sorguların kullanl olduğu Gelişmiş av sayfası" lightbox="images/f48ba1779eddee9872f167453c24e5c9.png":::

Cihaz bulma, Uç Nokta için Microsoft Defender olmayan cihazlara öznitelik etkinlikleri için ağ veri kaynağı olarak yerleşik cihazları kullanıyor ve bu cihazlardan yararlanıyor. Başka bir ifadeyle Uç Nokta için Microsoft Defender bir cihaz, yerleşik olmayan bir cihazla iletişim kurarsa, eklemeyen cihazdaki etkinliklerin zaman çizelgesinde ve Gelişmiş av deviceNetworkEvents tablosu üzerinden görülebiz.

Yeni etkinlikler, İletim Denetimi Protokolü (TCP) bağlantı tabanlıdır ve geçerli DeviceNetworkEvents düzenine uyar. ETKIN olmayan bir Uç Nokta için Microsoft Defender ETKIN olan cihaza TCP Uç Nokta için Microsoft Defender.

Aşağıdaki eylem türleri de eklendi:

- ConnectionAttempt - TCP bağlantısı (syn) kurma girişimi
- ConnectionAcknowledged - TCP bağlantısının kabul edilen bir bildirim (syn\ack)

Şu örnek sorguyu  deneyebilirsiniz:

```text
DeviceNetworkEvents
| where ActionType == "ConnectionAcknowledged" or ActionType == "ConnectionAttempt"
| take 10
```

## <a name="next-steps"></a>Sonraki adımlar

- [Cihaz bulma'yi yapılandırma](configure-device-discovery.md)
- [Cihaz bulma SSS](device-discovery-faq.md)
