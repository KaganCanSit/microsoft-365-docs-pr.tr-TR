---
title: Microsoft 365 Defender ile araştırma ve yanıtlama
description: olayları Microsoft 365 Defender özellikleriyle araştırın ve yanıt verin.
keywords: olaylar, uyarılar, araştırma, analiz etme, yanıt, bağıntı, saldırı, makineler, cihazlar, kullanıcılar, kimlikler, kimlik, posta kutusu, e-posta, 365, Microsoft, m365, olay yanıtı, siber saldırı
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
- m365solution-incidentresponse
- m365solution-scenario
- m365solution-overview
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.openlocfilehash: a4edb82291ff01a4876ad93d688dbbbf19416c05
ms.sourcegitcommit: 9255a7e8b398f92d8dae09886ae95dc8577bf29a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2022
ms.locfileid: "65435379"
---
# <a name="investigate-and-respond-with-microsoft-365-defender"></a>Microsoft 365 Defender ile araştırma ve yanıtlama

Microsoft 365 Defender için birincil araştırma ve yanıtlama görevleri şunlardır:

- [Olaylara karşı yanıt verin](#incident-response)
- [Otomatik düzeltme eylemlerini gözden geçirme ve onaylama](#automated-investigation-and-remediation)
- [Verilerinizde bilinen tehditleri arama](#proactive-search-for-threats-with-advanced-hunting)
- [En son siber saldırıları anlama](#get-ahead-of-emerging-threats-with-threat-analytics)
- [Yardım alın](#collaborate-with-microsoft-experts)

## <a name="incident-response"></a>Olay yanıtı

Microsoft 365 hizmetler ve uygulamalar, şüpheli veya kötü amaçlı bir olay veya etkinlik algıladığında uyarılar oluşturur. Tek tek uyarılar, tamamlanmış veya devam eden bir saldırı hakkında değerli ipuçları sağlar. Ancak saldırılar genellikle cihazlar, kullanıcılar ve posta kutuları gibi farklı varlık türlerine karşı çeşitli teknikler uygular. Sonuç, kiracınızdaki birden çok varlık için birden çok uyarıdır. Bir saldırı hakkında içgörü elde etmek için tek tek uyarıların birlikte pastalanması zor ve zaman alıcı olabileceğinden, Microsoft 365 Defender uyarıları ve ilişkili bilgilerini bir olayda otomatik olarak toplar.

Sürekli olarak, olay kuyruğundaki analiz ve çözüm için en yüksek öncelikli olayları tanımlamanız ve yanıt için hazırlamanız gerekir. Bu, aşağıdakilerin bir bileşimidir:

- [Olay](incident-queue.md) kuyruğunun filtrelenmesi ve sıralanması yoluyla en yüksek öncelikli olayları belirlemeye öncelik verme. Bu, önceliklendirme olarak da bilinir.
- Olay başlıklarını değiştirerek, bunları bir analiste atayarak, etiketler ve açıklamalar ekleyerek ve çözümlendiğinde bunları sınıflandırarak [olayları yönetme](manage-incidents.md).

Her olay için olay yanıt iş akışınızı kullanarak olayı ve saldırıyı içeren uyarıları ve verileri analiz edin, tehdidi silin, saldırıdan kurtarın ve ondan bilgi edinin. Microsoft 365 Defender için [bu örne](incidents-overview.md#example-incident-response-workflow-for-microsoft-365-defender) bakın.

## <a name="automated-investigation-and-remediation"></a>Otomatik araştırma ve düzeltme

Kuruluşunuz Microsoft 365 Defender kullanıyorsa, kötü amaçlı veya şüpheli bir etkinlik veya yapıt algılandığında güvenlik operasyonları ekibiniz Microsoft 365 Defender portalında bir uyarı alır. Gelen tehditlerin hiç bitmeyen akışı göz önünde bulundurulduğunda, güvenlik ekipleri genellikle yüksek hacimli uyarıları ele alma zorluğuyla karşı karşıya kalır. Neyse ki Microsoft 365 Defender, güvenlik operasyonları ekibinizin tehditleri daha verimli ve etkili bir şekilde ele almasına yardımcı olabilecek otomatik araştırma ve yanıt (AIR) özelliklerini içerir.

Otomatik bir araştırma tamamlandığında, bir olayın her kanıtı için bir karara ulaşılır. Karara bağlı olarak düzeltme eylemleri tanımlanır. Bazı durumlarda düzeltme eylemleri otomatik olarak gerçekleştirilen; diğer durumlarda, düzeltme eylemleri Microsoft 365 Defender İşlem merkezi aracılığıyla onay bekler. 

Daha fazla bilgi için bkz. [Microsoft 365 Defender'de otomatik araştırma ve yanıt](m365d-autoir.md).

## <a name="proactive-search-for-threats-with-advanced-hunting"></a>Gelişmiş avcılık ile tehditler için proaktif arama

Saldırılara meydana gelen saldırılara yanıt vermek yeterli değildir. Fidye yazılımı gibi uzun ve çok aşamalı saldırılar için, devam eden bir saldırının kanıtını proaktif olarak aramanız ve tamamlanmadan önce durdurmak için harekete geçmeniz gerekir.

Gelişmiş avcılık, Microsoft 365 Defender 30 güne kadar ham verileri keşfetmenizi sağlayan sorgu tabanlı bir tehdit avcılığı aracıdır. Tehdit göstergelerini ve varlıkları bulmak için ağınızdaki olayları proaktif olarak inceleyebilirsiniz. Microsoft 365 Defender verilerine yönelik bu esnek erişim, hem bilinen hem de olası tehditler için kısıtlanmamış avcılık sağlar.

Özel algılama kuralları oluşturmak için aynı tehdit avcılığı sorgularını kullanabilirsiniz. Bu kurallar, şüpheli ihlal etkinliğini, yanlış yapılandırılmış makineleri ve diğer bulguları denetlemek ve yanıtlamak için otomatik olarak çalıştırılır.

Daha fazla bilgi için bkz. [Microsoft 365 Defender gelişmiş avcılık ile tehditleri proaktif olarak avlama](advanced-hunting-overview.md).

## <a name="get-ahead-of-emerging-threats-with-threat-analytics"></a>Tehdit analizi ile yeni tehditlerin önüne geçin

Tehdit analizi, Microsoft 365 Defender'de güvenlik ekibinizin ortaya çıkan tehditlerle karşı karşıyayken mümkün olduğunca verimli olmasına yardımcı olmak için tasarlanmış bir tehdit zekası özelliğidir. Aşağıdakiler hakkında ayrıntılı analiz ve bilgi içerir:

- Etkin tehdit aktörleri ve kampanyaları
- Popüler ve yeni saldırı teknikleri
- Kritik güvenlik açıkları
- Yaygın saldırı yüzeyleri
- Yaygın kötü amaçlı yazılım

Tehdit analizi, tanımlanan her tehdit için Microsoft 365 kiracınızdaki ilgili olaylar ve etkilenen varlıklar hakkında da bilgi içerir.

Tanımlanan her tehdit, siber güvenlik algılama ve analizinin ön saflarında yer alan Microsoft güvenlik araştırmacıları tarafından yazılan tehdidin kapsamlı bir analizi olan bir analist raporu içerir. Bu raporlar, saldırıların Microsoft 365 Defender nasıl göründüğü hakkında da bilgi sağlayabilir.

Daha fazla bilgi için bkz[. Microsoft 365 Defender'de tehdit analizi](threat-analytics.md).

## <a name="collaborate-with-microsoft-experts"></a>Microsoft uzmanlarıyla işbirliği yapma

Microsoft Tehdit Uzmanları - Hedefli Saldırı Bildirimleri yönetilen bir tehdit avcılığı hizmetidir. Başvurduktan ve kabul edildikten sonra, Microsoft tehdit uzmanlarından hedefli saldırı bildirimleri alırsınız, böylece ortamınıza yönelik kritik tehditleri kaçırmazsınız. Bu bildirimler kuruluşunuzun uç noktalarını, e-postalarını ve kimliklerini korumanıza yardımcı olur. Microsoft Tehdit Uzmanları – İsteğe Bağlı Uzmanlar, kuruluşunuzun karşılaştığı tehditler hakkında uzman tavsiyeleri almanızı sağlar ve kuruluşunuzun karşılaştığı tehditlerle ilgili yardım almak için size ulaşabilirsiniz. Ek abonelik hizmeti olarak kullanılabilir.

Daha fazla bilgi için bkz. [Microsoft 365 genel bakış bölümünde Microsoft Tehdit Uzmanları](/microsoft-365/security/defender/microsoft-threat-experts).
