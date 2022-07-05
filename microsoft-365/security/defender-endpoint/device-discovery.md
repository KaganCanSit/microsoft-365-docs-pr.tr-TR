---
title: Cihaz keşfine genel bakış
description: Ağınızdaki yönetilmeyen cihazları bulmak için Microsoft 365 Defender uç nokta bulmadan nasıl yararlanacağınızı öğrenin
keywords: cihaz bulma, bulma, pasif, proaktif, ağ, görünürlük, sunucu, iş istasyonu, ekleme, yönetilmeyen cihazlar
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
ms.openlocfilehash: 2e4939eb21a62c99ecf6572060213c87c2c01176
ms.sourcegitcommit: 44ece87e3e0c0c851dfc1e77211ac3e5e4a5b973
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/05/2022
ms.locfileid: "66617314"
---
# <a name="device-discovery-overview"></a>Cihaz keşfine genel bakış

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Şunlar için geçerlidir:**

- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

Ortamınızı korumak için ağınızdaki cihazların envanterinin alınması gerekir. Ancak, bir ağdaki cihazları eşlemek genellikle pahalı, zorlayıcı ve zaman alıcı olabilir.

Uç Nokta için Microsoft Defender, şirket ağınıza bağlı yönetilmeyen cihazları ek gereçlere veya hantal işlem değişikliklerine gerek kalmadan bulmanıza yardımcı olan bir cihaz bulma özelliği sağlar. Cihaz bulma, ağınızdaki yerleşik uç noktaları kullanarak yönetilmeyen cihazları bulmak için ağınızda toplar, yoklar veya tarar. Cihaz bulma özelliği şunları keşfetmenize olanak tanır:

- Henüz Uç Nokta için Microsoft Defender eklenmemiş kurumsal uç noktalar (iş istasyonları, sunucular ve mobil cihazlar)
- Yönlendiriciler ve anahtarlar gibi ağ cihazları
- Yazıcılar ve kameralar gibi IoT cihazları

Bilinmeyen ve yönetilmeyen cihazlar ağınıza önemli riskler getirir. Bu, eşleşmeyen bir yazıcı, zayıf güvenlik yapılandırmalarına sahip ağ cihazları veya güvenlik denetimleri olmayan bir sunucu olabilir. Cihazlar bulunduktan sonra şunları yapabilirsiniz:

- Yönetilmeyen uç noktaları hizmete ekleyip bu uç noktaların güvenlik görünürlüğünü artırır.
- Güvenlik açıklarını tanımlayıp değerlendirerek ve yapılandırma boşluklarını algılayarak saldırı yüzeyini azaltın.

Keşfedilen Uç Nokta için Microsoft Defender yönetilmeyen cihazları değerlendirmeye ve eklemeye hızlı bir genel bakış için bu videoyu izleyin.
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4RwQz]

Bu özellik ile birlikte, mevcut Tehdit ve Güvenlik Açığı Yönetimi deneyiminin bir parçası olarak cihazları Uç Nokta için Microsoft Defender eklemeye yönelik bir güvenlik önerisi sağlanır.

## <a name="discovery-methods"></a>Bulma yöntemleri

Eklenen cihazlarınız tarafından kullanılacak bulma modunu seçebilirsiniz. Mod, şirket ağınızdaki yönetilmeyen cihazlar için alabileceğiniz görünürlük düzeyini denetler.

Kullanılabilir iki bulma modu vardır:

- **Temel bulma**: Bu modda uç noktalar ağınızdaki olayları pasif olarak toplar ve onlardan cihaz bilgilerini ayıklar. Temel bulma, pasif ağ veri toplama için SenseNDR.exe ikili dosyasını kullanır ve hiçbir ağ trafiği başlatılmaz. Uç noktalar, eklenen bir cihaz tarafından görülen her ağ trafiğinden verileri ayıklar. Temel bulma ile ağınızdaki yönetilmeyen uç noktaların yalnızca sınırlı görünürlüğünü elde edersiniz.

- **Standart bulma** (önerilen): Bu mod, uç noktaların toplanan verileri zenginleştirmek ve daha fazla cihaz bulmak için ağınızdaki cihazları etkin bir şekilde bulmasına olanak tanır ve güvenilir ve tutarlı bir cihaz envanteri oluşturmanıza yardımcı olur. Standart mod, pasif yöntem kullanılarak gözlemlenen cihazlara ek olarak, daha da fazla cihaz bulmak için ağdaki çok noktaya yayın sorgularını kullanan yaygın bulma protokollerinden de yararlanıyor. Standart mod, mevcut cihaz bilgilerini zenginleştirmek için gözlemlenen cihazlar hakkında ek bilgileri keşfetmek için akıllı ve etkin yoklama kullanır. Standart mod etkinleştirildiğinde, kuruluşunuzdaki ağ izleme araçları tarafından bulma algılayıcısı tarafından oluşturulan en düşük ve ihmal edilebilir ağ etkinliği gözlemlenebilir.

Bulma ayarlarınızı değiştirebilir ve özelleştirebilirsiniz. Daha fazla bilgi için bkz. [Cihaz bulmayı yapılandırma](configure-device-discovery.md).

> [!IMPORTANT]
> Standart bulma, 19 Temmuz 2021'den itibaren tüm müşteriler için varsayılan moddur. Ayarlar sayfasından bu yapılandırmayı temel olarak değiştirmeyi seçebilirsiniz. Temel modu seçerseniz ağınızdaki yönetilmeyen uç noktaların yalnızca sınırlı görünürlüğünü elde edersiniz.

> [!NOTE]
> Bulma altyapısı, şirket ağında alınan ağ olaylarını kurumsal ağın dışından ayırt eder. Şirket ağlarına bağlı olmayan cihazlar bulunmayacak veya cihaz envanterinde listelenmeyecektir.

## <a name="device-inventory"></a>Cihaz envanteri

Bulunan ancak henüz Uç Nokta için Microsoft Defender tarafından eklenen ve güvenliği sağlanmamış cihazlar, Bilgisayarlar ve Mobil sekmesindeki cihaz envanterinde listelenir.

Bu cihazları değerlendirmek için cihaz envanter listesinde Ekleme durumu adlı bir filtre kullanabilirsiniz ve bu filtre aşağıdaki değerlerden herhangi birine sahip olabilir:

- Eklenen: Uç nokta Uç Nokta için Microsoft Defender eklenir.
- Eklenebilir: Uç nokta ağda bulundu ve İşletim Sistemi, Uç Nokta için Microsoft Defender tarafından desteklenen bir uç nokta olarak tanımlandı, ancak şu anda eklenmedi. Bu cihazları eklemenizi kesinlikle öneririz.
- Desteklenmeyen: Uç nokta ağda bulundu ancak Uç Nokta için Microsoft Defender tarafından desteklenmiyor.
- Yetersiz bilgi: Sistem cihazın desteklenebilirliğini belirleyemedi. Ağdaki daha fazla cihazda standart bulmayı etkinleştirmek bulunan öznitelikleri zenginleştirebilir.

:::image type="content" source="images/2b62255cd3a9dd42f3219e437b956fb9.png" alt-text="Cihaz envanteri panosu" lightbox="images/2b62255cd3a9dd42f3219e437b956fb9.png":::

> [!TIP]
> Yönetilmeyen cihazları cihaz envanter listesinden dışlamak için istediğiniz zaman filtre uygulayabilirsiniz. Yönetilmeyen cihazları filtrelemek için API sorgularında ekleme durumu sütununu da kullanabilirsiniz.

Daha fazla bilgi için bkz [. Cihaz envanteri](machines-view-overview.md).

## <a name="network-device-discovery"></a>Ağ cihazı bulma

Bir kuruluşa dağıtılan çok sayıda yönetilmeyen ağ cihazı, büyük bir yüzey saldırı alanı oluşturur ve kuruluşun tamamı için önemli bir riski temsil eder. Uç Nokta için Microsoft Defender ağ bulma özellikleri, ağ cihazlarının bulunmasını, doğru sınıflandırılmasını ve varlık envanterine eklenmesini sağlamanıza yardımcı olur.

Uç Nokta için Defender'ın ağ cihazlarında yerleşik bir algılayıcısı olmadığından, ağ cihazları standart uç nokta olarak yönetilmez. Bu tür cihazlar, uzaktan taramanın cihazlardan gerekli bilgileri edineceği aracısız bir yaklaşım gerektirir. Bunu yapmak için, önceden yapılandırılmış ağ cihazlarında düzenli aralıklarla kimliği doğrulanmış taramalar gerçekleştirmek için her ağ kesiminde belirlenmiş bir Uç Nokta için Microsoft Defender cihazı kullanılır. Uç Nokta için Defender'ın Tehdit ve Güvenlik Açığı Yönetimi özellikleri, bulunan anahtarları, yönlendiricileri, WLAN denetleyicilerini, güvenlik duvarlarını ve VPN ağ geçitlerini güvenli hale getirmek için tümleşik iş akışları sağlar.

Daha fazla bilgi için bkz [. Ağ cihazları](network-devices.md).

## <a name="device-discovery-integrations"></a>Cihaz bulma Tümleştirmeleri

Ot/IOT varlık envanterinizi bulmak, tanımlamak ve güvenliğini sağlamak için yeterli görünürlük elde etme zorluğuna çözüm bulmak için Uç Nokta için Microsoft Defender şimdi aşağıdaki tümleştirmeleri destekler:

- **Corelight**: Microsoft, Corelight ağ gereçlerinden veri almak için Corelight ile iş ortaklığı yaptı. Bu, diğer yönetilmeyen cihazlar veya dış ağlarla iletişim de dahil olmak üzere yönetilmeyen cihazların ağ etkinliklerine daha fazla görünürlük sağlayan Microsoft 365 Defender sağlar. Daha fazla bilgi için bkz [. Corelight veri tümleştirmesini etkinleştirme](corelight-integration.md).

- **IoT için Microsoft Defender**: Bu tümleştirme, Uç Nokta için Microsoft Defender cihaz bulma özelliklerini IoT için Microsoft Defender'ın aracısız izleme özellikleriyle bir araya getirerek bir BT ağına bağlı kurumsal IoT cihazlarının (örneğin, İnternet Üzerinden Ses Protokolü (VoIP), yazıcıların ve akıllı TV'lerin güvenliğini sağlar. Daha fazla bilgi için bkz. [IoT için Microsoft Defender tümleştirmesini etkinleştirme](enable-microsoft-defender-for-iot-integration.md).

## <a name="vulnerability-assessment-on-discovered-devices"></a>Bulunan cihazlarda güvenlik açığı değerlendirmesi

Cihazlarınızdaki güvenlik açıkları ve riskler ve ağda bulunan diğer yönetilmeyen cihazlar, "Güvenlik Önerileri" altındaki geçerli TVM akışlarının bir parçasıdır ve portaldaki varlık sayfalarında gösterilir.
Yönetilmeyen ve yönetilen cihazlarla ilgili SSH güvenlik açıklarını bulmak için "SSH" ile ilgili güvenlik önerilerini arayın.

:::image type="content" source="images/1156c82ffadd356ce329d1cf551e806c.png" alt-text="Güvenlik önerileri panosu" lightbox="images/1156c82ffadd356ce329d1cf551e806c.png":::

## <a name="use-advanced-hunting-on-discovered-devices"></a>Bulunan cihazlarda gelişmiş avcılık kullanma

Bulunan cihazlarda görünürlük elde etmek için gelişmiş tehdit avcılığı sorgularını kullanabilirsiniz. Bulunan cihazlar hakkındaki ayrıntıları DeviceNetworkInfo tablosundaki DeviceInfo tablosunda veya bu cihazlarla ilgili ağ ile ilgili bilgileri bulabilirsiniz.

:::image type="content" source="images/f48ba1779eddee9872f167453c24e5c9.png" alt-text="Sorguların kullanılabilmesi için Gelişmiş tehdit avcılığı sayfası" lightbox="images/f48ba1779eddee9872f167453c24e5c9.png":::

### <a name="query-discovered-devices-details"></a>Bulunan cihazların ayrıntılarını sorgulama

Bulunan tüm cihazları ve her cihaz için en güncel ayrıntıları döndürmek için bu sorguyu DeviceInfo tablosunda çalıştırın:

```query
DeviceInfo
| summarize arg_max(Timestamp, *) by DeviceId  // Get latest known good per device Id
| where isempty(MergedToDeviceId) // Remove invalidated/merged devices
| where OnboardingStatus != "Onboarded"
```

**SeenBy** işlevini çağırarak, gelişmiş tehdit avcılığı sorgunuzda bulunan bir cihazın hangi yerleşik cihazın görüldüğünü ayrıntılı olarak öğrenebilirsiniz. Bu bilgiler, bulunan her cihazın ağ konumunu belirlemeye yardımcı olabilir ve daha sonra bu cihazın ağda tanımlanmasına yardımcı olabilir.

```query
DeviceInfo
| where OnboardingStatus != "Onboarded"
| summarize arg_max(Timestamp, *) by DeviceId 
| where isempty(MergedToDeviceId) 
| limit 100
| invoke SeenBy()
| project DeviceId, DeviceName, DeviceType, SeenBy
```

Daha fazla bilgi için [bkz. SeenBy()](/microsoft-365/security/defender/advanced-hunting-seenby-function) işlevi.

### <a name="query-network-related-information"></a>Ağla ilgili bilgileri sorgulama

Cihaz bulma, eklenen Uç Nokta için Microsoft Defender cihazları, eklememiş cihazlara etkinlikleri öznitelik etmek için ağ veri kaynağı olarak kullanır. Eklenen Uç Nokta için Microsoft Defender cihazdaki ağ algılayıcısı iki yeni bağlantı türü tanımlar:

- ConnectionAttempt - TCP bağlantısı kurma girişimi (syn)
- ConnectionAcknowledged - TCP bağlantısının kabul edildiğine ilişkin bir bildirim (syn\ack)

Başka bir deyişle, eklenmemiş bir cihaz eklenen Uç Nokta için Microsoft Defender cihazıyla iletişim kurmaya çalıştığında, girişim bir DeviceNetworkEvent oluşturur ve eklenen cihaz zaman çizelgesinde ve Gelişmiş avcılık DeviceNetworkEvents tablosu aracılığıyla eklenmeyen cihaz etkinlikleri görülebilir.

Bu örnek sorguyu deneyebilirsiniz:

```text
DeviceNetworkEvents
| where ActionType == "ConnectionAcknowledged" or ActionType == "ConnectionAttempt"
| take 10
```

## <a name="next-steps"></a>Sonraki adımlar

- [Cihaz keşif ayarlarını yapılandırın](configure-device-discovery.md)
- [Cihaz bulma hakkında SSS](device-discovery-faq.md)
