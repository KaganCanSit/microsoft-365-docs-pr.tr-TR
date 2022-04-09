---
title: Microsoft 365 Defender'de otomatik araştırma ve yanıt
description: Microsoft 365 Defender'da otomatik araştırma ve yanıt özelliklerine genel bakış (kendi kendini iyileştirme olarak da adlandırılır) edinin
keywords: otomatik, araştırma, uyarı, tetikleyici, eylem, düzeltme, kendi kendini düzeltme
search.appverid: met150
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
ms.topic: conceptual
ms.custom: autoir
ms.reviewer: evaldm, isco
ms.technology: m365d
ms.openlocfilehash: 332802150235ec6f47c4bdea34b34edb94ea1b90
ms.sourcegitcommit: dd7e5b67ff4ae4e7f74490e437c1795933c74cc7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2022
ms.locfileid: "64731339"
---
# <a name="automated-investigation-and-response-in-microsoft-365-defender"></a>Microsoft 365 Defender'de otomatik araştırma ve yanıt

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Şunlar için geçerlidir:**
- Microsoft 365 Defender

Kuruluşunuz [Microsoft 365 Defender](microsoft-365-defender.md) kullanıyorsa, kötü amaçlı veya şüpheli bir etkinlik veya yapıt algılandığında güvenlik operasyonları ekibiniz Microsoft 365 Defender portalında bir uyarı alır. Gelen tehditlerin hiç bitmeyen akışı göz önünde bulundurulduğunda, güvenlik ekipleri genellikle yüksek hacimli uyarıları ele alma zorluğuyla karşı karşıya kalır. Neyse ki Microsoft 365 Defender, güvenlik operasyonları ekibinizin tehditleri daha verimli ve etkili bir şekilde ele almasına yardımcı olabilecek otomatik araştırma ve yanıt (AIR) özelliklerini içerir.

Bu makale AIR'e genel bir bakış sağlar ve sonraki adımlara ve ek kaynaklara bağlantılar içerir.

## <a name="how-automated-investigation-and-self-healing-works"></a>Otomatik araştırma ve kendi kendini iyileştirme nasıl çalışır?

Güvenlik uyarıları tetiklendiğinde, bu uyarıları incelemek ve kuruluşunuzu korumak için adımlar atmak güvenlik operasyonları ekibinize bağlı olur. Uyarıların önceliklerini belirlemek ve araştırmak, özellikle de bir araştırma devam ederken yeni uyarılar gelmeye devam ettiğinde çok zaman alabilir. Güvenlik operasyonları ekipleri izlemeleri ve korumaları gereken büyük tehdit hacminden bunalmış hissedebilir. otomatik araştırma ve yanıt özellikleri, kendi kendini iyileştirme ile, Microsoft 365 Defender yardımcı olabilir.

Kendi kendini iyileştirmenin nasıl çalıştığını görmek için aşağıdaki videoyu izleyin: <p>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4BzwB]

Microsoft 365 Defender otomatik araştırma ve kendi kendini iyileştirme özelliklerine sahip yanıt, cihazlarınız, e-posta & içeriği ve kimliklerinizde çalışır.
 
> [!TIP]
> Bu makalede otomatik araştırma ve yanıtın nasıl çalıştığı açıklanmaktadır. Bu özellikleri yapılandırmak için bkz[. Microsoft 365 Defender'de otomatik araştırma ve yanıt özelliklerini yapılandırma](m365d-configure-auto-investigation-response.md).

## <a name="your-own-virtual-analyst"></a>Kendi sanal analistiniz

Katman 1 veya Katman 2 güvenlik operasyonları ekibinizde sanal analiste sahip Imagine. Sanal analist, güvenlik işlemlerinin tehditleri araştırmak ve düzeltmek için atacağı ideal adımları taklit eder. Sanal analist, sınırsız kapasiteyle 7/24 çalışabilir ve önemli bir araştırma ve tehdit düzeltme yükü üstlenebilir. Böyle bir sanal analist, yanıt verme süresini önemli ölçüde azaltarak güvenlik operasyonları ekibinizin diğer önemli tehditlere veya stratejik projelere serbest olmasını sağlayabilir. Bu senaryo bilim kurgu gibi görünüyorsa, değil! Böyle bir sanal analist, Microsoft 365 Defender paketinizin bir parçasıdır ve adı *otomatik araştırma ve yanıttır*.

Otomatik araştırma ve yanıt özellikleri, güvenlik operasyonları ekibinizin kuruluşunuzun güvenlik uyarılarıyla ve olaylarıyla başa çıkma kapasitesini önemli ölçüde artırmasına olanak tanır. Otomatik araştırma ve yanıt ile araştırma ve yanıt etkinlikleriyle ilgilenme maliyetini azaltabilir ve tehdit koruması paketinizden en iyi şekilde yararlanın. Otomatik araştırma ve yanıt özellikleri güvenlik operasyonları ekibinize şu şekilde yardımcı olur:

1. Bir tehdidin eylem gerekip gerekmediğini belirleme.
2. Gerekli düzeltme eylemlerini gerçekleştirme (veya önerme).
3. Diğer araştırmaların yapılıp yapılmayacağını ve ne olması gerektiğini belirleme.
4. Diğer uyarılar için gerekli olan işlemi tekrarlama.

## <a name="the-automated-investigation-process"></a>Otomatik araştırma işlemi

Uyarı, otomatik araştırma başlatabilen bir olay oluşturur. Otomatik araştırma, her kanıt parçası için bir karara neden olur. Hükümler:
- *Kötü amaçlı*
- *Şüpheli* 
- *Tehdit bulunamadı* 

Kötü amaçlı veya şüpheli varlıklar için düzeltme eylemleri tanımlanır. Düzeltme eylemlerine örnek olarak şunlar verilebilir:

- Karantinaya dosya gönderme
- İşlemi durdurma
- Cihazı yalıtma
- URL'yi engelleme 
- Diğer eylemler

Daha fazla bilgi için bkz. [Microsoft 365 Defender düzeltme eylemleri](m365d-remediation-actions.md).

Kuruluşunuz için [otomatik araştırma ve yanıt özelliklerinin nasıl yapılandırıldığına](m365d-configure-auto-investigation-response.md) bağlı olarak, düzeltme eylemleri otomatik olarak veya yalnızca güvenlik operasyonları ekibinizin onayıyla gerçekleştirilen işlemlerdir. Bekleyen veya tamamlanan tüm eylemler [İşlem merkezinde](m365d-action-center.md) listelenir.

Bir araştırma çalışırken, ortaya çıkan diğer ilgili uyarılar tamamlanana kadar araştırmaya eklenir. Etkilenen bir varlık başka bir yerde görülürse, otomatik araştırma kapsamını bu varlığı içerecek şekilde genişletir ve araştırma işlemi yinelenir. 

Microsoft 365 Defender her otomatik araştırma sinyalleri Kimlik için Microsoft Defender, Uç Nokta için Microsoft Defender ve aşağıdaki tabloda özetlenen Office 365 için Microsoft Defender: 

|Varlık |Tehdit koruma hizmetleri  |
|:---------|:---------|
|Cihazlar (uç nokta veya makine olarak da adlandırılır) |[Uç Nokta için Defender](../defender-endpoint/automated-investigations.md) |      
|Şirket içi Active Directory kullanıcıları, varlık davranışı ve etkinlikleri     |[Kimlik için Microsoft Defender](/azure-advanced-threat-protection/what-is-atp) |      
|E-posta içeriği (dosya ve URL içerebilen e-posta iletileri)     |[Office 365 için Defender](../office-365-security/defender-for-office-365.md) |

> [!NOTE]
> Her uyarı otomatik bir araştırma tetiklemez ve her araştırma otomatik düzeltme eylemleriyle sonuçlanmaz. Bu, kuruluşunuz için otomatik araştırma ve yanıtın nasıl yapılandırıldığına bağlıdır. Bkz [. Otomatik araştırma ve yanıt özelliklerini yapılandırma](m365d-configure-auto-investigation-response.md).

## <a name="viewing-a-list-of-investigations"></a>Araştırma listesini görüntüleme

Araştırmaları görüntülemek için **Olaylar** sayfasına gidin. Bir olay seçin ve ardından **Araştırmalar** sekmesini seçin. Daha fazla bilgi için bkz. [Otomatik araştırmanın ayrıntıları ve sonuçları](m365d-autoir-results.md).

## <a name="training-for-security-analysts"></a>Güvenlik analistleri için eğitim

Microsoft 365 Defender olay araştırması ve yanıtı için otomatik kendi kendini düzeltmeyi nasıl kullandığını anlamak için Microsoft Learn'den bu öğrenme modülünü kullanın.

|Eğitim:|Microsoft 365 Defender ile kendi kendini iyileştirmeyi otomatikleştirme|
|---|---|
|![Microsoft 365 Defender eğitim simgesiyle kendi kendini düzeltmeyi otomatikleştirin.](../../media/m365d-autoir/m365-defender-auto-self-healing.svg)| Microsoft 365 Defender, güvenlik operasyonları ekibinizin tehditleri daha verimli ve etkili bir şekilde ele alınmasına yardımcı olarak olayların düzeltilmesine yardımcı olmak için yapay zekayı kullanır. <p> 11 dk - 5 Birim |

> [!div class="nextstepaction"]
> [Başlangıç >](/learn/modules/defender-self-healing/)

## <a name="next-steps"></a>Sonraki adımlar

- [Otomatik araştırma ve yanıt önkoşullarına bakın](m365d-configure-auto-investigation-response.md#prerequisites-for-automated-investigation-and-response-in-microsoft-365-defender)
- [Kuruluşunuz için otomatik araştırma ve yanıt yapılandırma](m365d-configure-auto-investigation-response.md)
- [İşlem merkezi hakkında daha fazla bilgi edinin](m365d-action-center.md)
