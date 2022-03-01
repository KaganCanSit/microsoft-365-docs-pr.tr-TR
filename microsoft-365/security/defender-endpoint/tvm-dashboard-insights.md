---
title: Pano içgörüleri - Tehdit ve Güvenlik Açığı Yönetimi
description: Güvenlik Tehdit ve Güvenlik Açığı Yönetimi, SecOps ve güvenlik yöneticilerine siber güvenlik tehditlerine karşı yardımcı olabilir ve kuruluşlarının güvenlik kullanılabilirliklerini oluşturabilir.
keywords: Endpoint-tvm için Microsoft Defender, Endpoint-tvm panosu için Microsoft Defender, tehdit & güvenlik açığı yönetimi, Tehdit ve Güvenlik Açığı Yönetimi, risk tabanlı tehdit & güvenlik açığı yönetimi, güvenlik yapılandırması, Cihazlar için Microsoft Güvenli Puanı , pozlama puanı
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365initiative-defender-endpoint
ms.custom: admindeeplinkDEFENDER
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: fb93b179b9d342a4a0d098ddb889a94371fbabc4
ms.sourcegitcommit: 4c207a9bdbb6c8ba372ae37907ccefca031a49f8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/09/2022
ms.locfileid: "63016698"
---
# <a name="dashboard-insights---threat-and-vulnerability-management"></a>Pano içgörüleri - Tehdit ve Güvenlik Açığı Yönetimi

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**

- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Tehdit ve güvenlik açığı yönetimi](next-gen-threat-and-vuln-mgt.md)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Defender'ı deneyimli yapmak mı istiyor musunuz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-portaloverview-abovefoldlink)

Threat ve güvenlik açığı yönetimi, Uç Nokta için Defender'ın bir bileşenidir ve hem güvenlik yöneticileri hem de güvenlik işlemleri ekiplerine benzersiz değer verir:

- Uç nokta güvenlik uç noktada algılama ve yanıtlama ilişkili EDR öngörüler (EDR) öngörüleri
- Olay soruşturmaları sırasında paha biçilemez cihaz güvenlik açığı bağlamı
- Düzeltme ve düzeltme işlemleri aracılığıyla Microsoft Intune Microsoft Endpoint Configuration Manager

Aşağıdakiler için Tehdit ve Güvenlik Açığı Yönetimi portalında Microsoft 365 Defender <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">kullanabilirsiniz</a>:

- En çok güvenlik önerileri, yazılım açığı, düzeltme etkinlikleri ve açık cihazlarla birlikte etkilenme puanınızı ve Cihazlar için Microsoft Güvenli Puanı'nızı görüntüleme
- Uç nokta EDR açıkları ile bilgileri birbiriyle bağlantılı bir şekilde işleme ve işleme
- Düzeltme görevlerinin öncelleme ve izlemesi için düzeltme seçeneklerini belirleyin
- Özel durum seçeneklerini belirleyin ve etkin özel durumları izleme

> [!NOTE]
> Son 30 gün içinde etkin olunan cihazlar, kurum una maruz kalma puanınızı ve Cihazlar için Microsoft Güvenli Puanı'Tehdit ve Güvenlik Açığı Yönetimi verilere faktör değildir.

Tehdit ve Güvenlik Açığı Yönetimi panosunda neler olduğu hakkında hızlı bir genel bakış için bu Tehdit ve Güvenlik Açığı Yönetimi izleyin.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4r1nv]

## <a name="threat-and-vulnerability-management-dashboard"></a>Tehdit ve güvenlik açığı yönetimi panosu

:::image type="content" source="../../media/tvmdashboard.png" lightbox="../../media/tvmdashboard.png" alt-text="Cihazlar için Tehdit ve Güvenlik Açığı Yönetimi panosu.":::

<br>

****

|Alan|Açıklama|
|---|---|
|**Seçili cihaz grupları (#/#)**|Panoda Tehdit ve Güvenlik Açığı Yönetimi cihaz gruplarına göre istediğiniz her veriye filtre ekleyin. Filtrede seçiminiz tüm sayfalara Tehdit ve Güvenlik Açığı Yönetimi.|
|[**Pozlama puanı**](tvm-exposure-score.md)|Kuruluş cihazınızın tehditlere ve güvenlik açıklarına açık durumunu nasıl göreceğinizi görmek. Organizasyon un maruz kalma puanını etkileyen çeşitli faktörler vardır: cihazlarınız içinde bulunan riskler, cihazlarınızı ihlal olasılığı, kuruluş için cihazların değeri ve cihazlarınız ile bulunan ilgili uyarılar. Amaç, daha güvenli olması için organizasyon sürenizin daha düşük olmasıdır. Puanı azaltmak için, güvenlik önerilerinde listelenen ilgili güvenlik yapılandırması sorunlarını düzeltmeniz gerekir.|
|[**Cihazlar için Microsoft Güvenli Puan**](tvm-microsoft-secure-score-devices.md)|Kuruluş işletim sisteminin, uygulamaların, ağın, hesapların ve güvenlik denetimlerinin güvenlik nedenlerine bakın. Amaç, ilgili güvenlik yapılandırması sorunlarını düzeltmek ve cihazlarınız için puanınızı artırmaktır. Çubukları seçmek sizi Güvenlik önerisi **sayfasına** götürebilirsiniz.|
|**Cihaz pozlama dağılımı**|Pozlama düzeyine göre kaç cihaz maruz kaldığına bakın. Halka grafikte bir bölüm seçerek Cihazlar listesi sayfasına gidin  ve etkilenen cihaz adlarını, etkilenme düzeyini, risk düzeyini ve etki alanı, işletim sistemi platformu, sistem durumu, en son ne zaman görüldü ve etiketleri gibi diğer ayrıntıları görüntüleyebilirsiniz.|
|**En iyi güvenlik önerileri**|Kuruluş riskine maruz kalma riski ve bu acil durum nedeniyle sıralanmış ve öncelikleri belirli olan harmanlanmış güvenlik önerilerine bakın. Listede **güvenlik önerilerinin** kalan kalanını görmek için Daha fazla göster'i seçin. Özel **durumu olan öneriler** listesi için Özel durumları göster'i seçin.|
|**En korumasız yazılım**|Ağ cihazlarınıza yüklenmiş zayıf yazılımlardan ve bunların kurumsal etkilenme puanınızı nasıl etkileyeni ifade ederken, yığılmış dereceli bir yazılım listesiyle, kuruluş yazılım envanteri üzerinde gerçek zamanlı görünürlük elde edin. Ayrıntılar için bir öğe seçin veya **Yazılım envanteri** sayfasındaki zayıf yazılım listesinin geri kalanını görmek için **Daha fazla göster'i** seçin.|
|**En iyi düzeltme etkinlikleri**|Güvenlik önerilerinden oluşturulan düzeltme etkinliklerini izleme. Düzeltme sayfasında ayrıntıları görmek için listeden her öğeyi seçebilirsiniz veya düzeltme etkinliklerinin ve  etkin özel durumların geri kalanını  görüntülemek için Daha fazla göster'i seçin.|
|**En yüksek düzeye sahip cihazlar**|Açığa çıkarıla cihaz adlarını ve bunların açığa çıkacak düzeylerini görüntüleme. Uyarılarını, riskleri, olayları, güvenlik önerilerini, yüklü yazılımları ve ortaya çıkacak cihazlarla ilişkili güvenlik açıklarını görüntüleyebilirsiniz. Maruz **kalan cihazlar listesini** görmek için Daha fazla göster'i seçin. Cihazlar listesinden etiketleri yönetebilir, otomatik soruşturmalar başlatabilirsiniz, canlı yanıt oturumu başlatabilirsiniz, bir araştırma paketi toplayabilirsiniz, virüsten koruma taraması çalıştırabilirsiniz, uygulama yürütmeyi kısıtlayabilirsiniz ve cihazı yalıtabilirsiniz.|
|

Portal genelinde kullanılan simgeler hakkında daha fazla bilgi için bkz. Uç nokta simgeleri [için Microsoft Defender](portal-overview.md#microsoft-defender-for-endpoint-icons).

## <a name="related-topics"></a>İlgili konular

- [Tehdit ve güvenlik açığı yönetimi genel bakış](next-gen-threat-and-vuln-mgt.md)
- [Pozlama puanı](tvm-exposure-score.md)
- [Cihazlar için Microsoft Güvenli Puan](tvm-microsoft-secure-score-devices.md)
- [Güvenlik önerileri](tvm-security-recommendation.md)
- [Yazılım envanteri](tvm-software-inventory.md)
- [Etkinlik zaman çizelgesi](threat-and-vuln-mgt-event-timeline.md)
