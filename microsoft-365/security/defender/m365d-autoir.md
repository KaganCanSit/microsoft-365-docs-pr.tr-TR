---
title: Otomatik araştırma ve yanıt Microsoft 365 Defender
description: Yeni bir ekipte, otomatik araştırma ve yanıt özelliklerine genel bir bakış Microsoft 365 Defender
keywords: otomatik, araştırma, uyarı, tetikleyici, eylem, düzeltme, kendi kendine sorun
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
ms.openlocfilehash: 180599007a47fe9cfa9ae68d6647f7494dd2f410
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63314273"
---
# <a name="automated-investigation-and-response-in-microsoft-365-defender"></a>Otomatik araştırma ve yanıt Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- Microsoft 365 Defender

Bu uygulama[, Microsoft 365 Defender veya](microsoft-365-defender.md) şüpheli bir etkinlik algılandığında güvenlik işlemleri Microsoft 365 Defender portalında bir uyarı alır. Karşı karşıya gelebilir gibi görünen ve hiç bitmeyen tehdit akışına bağlı olarak, güvenlik ekipleri çoğu zaman yüksek hacimli uyarıların zorlukla karşı karşıya olduğunu kabul ediyor. Neyse ki Microsoft 365 Defender güvenlik işlemlerinin tehditlere daha etkili ve etkili bir biçimde müdahale edebilirim.

Bu makalede AIR'ye genel bir bakış ve sonraki adımlarla ek kaynakların bağlantıları yer sağlar.

> [!TIP]
> Bu deneyimi Microsoft 365 Defender? Bunu bir [laboratuvar ortamında değerlendirin veya](m365d-evaluation.md?ocid=cx-docs-MTPtriallab) [üretimde pilot projenizi çalıştırın](m365d-pilot.md?ocid=cx-evalpilot).

## <a name="how-automated-investigation-and-self-healing-works"></a>Otomatik araştırma ve kendi kendine yapılan çalışmalar nasıl çalışır?

Güvenlik uyarıları tetiklendiğinden, güvenlik işlemleri ekibinin bu uyarılara göz atarak kurumlarınızı korumak için gerekli adımları atmış olur. Özellikle araştırma devam ederken yeni uyarılar gelmeye devam ederken uyarıların önceliklerini belirlemek ve araştır çok zaman alabilir. Güvenlik işlemleri ekipleri izlemesi ve korunması gereken çok büyük tehditlere karşı boğmuş gibi hissetmelerini sağlar. Yeni bir ekipte otomatik araştırma ve yanıt özellikleri, Microsoft 365 Defender yardımcı olabilir.

Kendi kendine çalışan çalışmaları görmek için aşağıdaki videoyu izleyin: <p>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4BzwB]

Daha Microsoft 365 Defender, kendine özgü özelliklere sahip otomatik araştırma ve yanıt, cihazlarınız arasında çalışır, e-& içeriği ve kimlikleri sunar.
 
> [!TIP]
> Bu makalede, otomatik araştırma ve yanıtın nasıl çalışır olduğu açıklanmıştır. Bu özellikleri yapılandırmak için bkz. Yeni bir ekipte otomatik [soruşturma ve Microsoft 365 Defender](m365d-configure-auto-investigation-response.md).

## <a name="your-own-virtual-analyst"></a>Kendi sanal analistiniz

Imagine 1 veya Katman 2 güvenlik işlemleri ekibinde sanal bir analiste sahip olabilir. Sanal analist, güvenlik işlemlerinin tehditleri araştırması ve düzeltmesi için atılacak ideal adımları taklit ediyor. Sanal analist sınırsız kapasiteyle 7/24 çalışarak önemli bir inceleme ve tehdit düzeltmesi yükü elde ediyor olabilir. Böyle bir sanal analist yanıt verme süresini önemli ölçüde azaltır ve güvenlik işlemleri ekibinizi diğer önemli tehditlere veya stratejik projelere karşı serbest bırakabilir. Bu senaryo size bilim kurgu gibi geliyorsa, bu bir şey değildir! Böyle bir sanal analist, Microsoft 365 Defender paketinizin bir parçası olur ve adı otomatik *araştırma ve yanıt olur*.

Otomatik soruşturma ve yanıt özellikleri, güvenlik işlemleri ekibinin güvenlik uyarıları ve olaylarla başa çalışma kapasitesini önemli ölçüde artırmasını sağlar. Otomatik soruşturma ve yanıtla, soruşturma ve yanıt etkinlikleriyle ilgilenme maliyetini düşürer ve tehdit koruma paketinizden en iyi şekilde çıkarabilirsiniz. Otomatik soruşturma ve yanıt özellikleri, güvenlik işlemleri ekibinize şu işlemler için yardımcı olur:

1. Bir tehdit eylem gerekip gerektir olmadığını belirleme.
2. Gerekli düzeltme eylemlerini gerçekleştirin (veya önerin).
3. Diğer incelemelerin olup olmadığını ve neleri incelemeleri gerektiğini belirleme.
4. Diğer uyarılar için gerekli olan işlemi yineleme.

## <a name="the-automated-investigation-process"></a>Otomatik soruşturma işlemi

Uyarı, otomatik bir araştırma başlatan bir olay oluşturur. Otomatik araştırma, her kanıt parçası için karar verir. Kararların karşılanması şunları sağlar:
- *Kötü Amaçlı*
- *Şüpheli* 
- *Tehdit bulunamadı* 

Kötü amaçlı veya şüpheli varlıklara yönelik düzeltme eylemleri tanımlanır. Düzeltme eylemlerine örnek olarak şunlar yer içerir:

- Dosyayı karantinaya gönderme
- bir işlemi durdurma
- Bir cihazı yalıtma
- URL engelleme 
- Diğer eylemler

Daha fazla bilgi için bkz. [Diğer Microsoft 365 Defender](m365d-remediation-actions.md).

Otomatik araştırma [ve yanıt yeteneklerinizin](m365d-configure-auto-investigation-response.md) , sizin için nasıl yapılandırıldığına bağlı olarak, düzeltme eylemleri otomatik olarak veya yalnızca güvenlik işlemleri ekibinin onayı üzerine alınır. Beklemede veya tamamlandıktan sonra tüm eylemler İşlem merkezinde [listelenir](m365d-action-center.md).

Bir araştırma sürerken, ortaya çıkan ilgili diğer tüm uyarılar inceleme tamamlayana kadar araştırmaya eklenir. Etkilenen bir varlık başka bir yerde görülürse, otomatik araştırma kapsamı bu varlığı içerecek şekilde genişleter ve araştırma süreci yineler. 

Microsoft Microsoft 365 Defender Office 365'de, her otomatik soruşturma aşağıdaki tabloda özetlenmiştir: 

|Varlıklar |Tehdit koruması hizmetleri  |
|:---------|:---------|
|Cihazlar (uç noktalar veya makineler olarak da adlandırılır) |[Uç Nokta için Defender](../defender-endpoint/automated-investigations.md) |      
|Şirket içi Active Directory kullanıcıları, varlık davranışı ve etkinlikleri     |[Kimlik için Defender](/azure-advanced-threat-protection/what-is-atp) |      
|E-posta içeriği (dosya ve URL içer dayandıran e-posta iletileri)     |[Office 365 için Defender](../office-365-security/defender-for-office-365.md) |

> [!NOTE]
> Her uyarı otomatik bir araştırmayı tetiklemez ve her soruşturma otomatik düzeltme eylemleriyle sonuçlanmaz. Bu, kurum için otomatik araştırmanın ve yanıtın nasıl yapılandırıldığına bağlıdır. Bkz [. Otomatik araştırma ve yanıt özelliklerini yapılandırma](m365d-configure-auto-investigation-response.md).

## <a name="viewing-a-list-of-investigations"></a>Soruşturma listesini görüntüleme

Soruşturmaları görüntülemek için Olaylar **sayfasına** gidin. Bir olay seçin ve ardından **Araştırmalar sekmesini** seçin. Daha fazla bilgi edinmek için [bkz. Otomatik bir soruşturmanın ayrıntıları ve sonuçları](m365d-autoir-results.md).

## <a name="training-for-security-analysts"></a>Güvenlik analistleri için eğitim

Microsoft Learn'un bu öğrenme modülünü kullanarak, Microsoft 365 Defender araştırma ve yanıt için otomatik öz güveni nasıl kullandığını öğrenin.

|Eğitim:|Yeni ve öz özgü Microsoft 365 Defender|
|---|---|
|![Yeni eğitim simgesiyle öz Microsoft 365 Defender otomatikleştirin.](../../media/m365d-autoir/m365-defender-auto-self-healing.svg)| Microsoft 365 Defender, AI'yi kullanarak olayları düzeltmeye yardımcı olarak güvenlik işlemlerinin ekiplerinin tehditlere daha verimli ve etkili bir şekilde müdahale etmelerine yardımcı olur. <p> 11 dak. - 5 Birim |

> [!div class="nextstepaction"]
> [Başlangıç >](/learn/modules/defender-self-healing/)

## <a name="next-steps"></a>Sonraki adımlar

- [Otomatik araştırma ve yanıt için önkoşullara bakın](m365d-configure-auto-investigation-response.md#prerequisites-for-automated-investigation-and-response-in-microsoft-365-defender)
- [Otomatik araştırmayı ve kurum için yanıtı yapılandırma](m365d-configure-auto-investigation-response.md)
- [İşlem merkezi hakkında daha fazla bilgi](m365d-action-center.md)
