---
title: Uç Nokta için Microsoft Defender Plan 1 ile Kullanmaya başlayın
description: Uç Nokta Için Defender Plan 1'i kullanarak Kullanmaya başlayın. Bulut için Defender kullanmayı, uyarıları ve cihazları yönetmeyi ve raporları görüntülemeyi öğrenin.
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: ITPro
ms.topic: overview
ms.date: 01/03/2022
ms.prod: m365-security
ms.technology: mdep1
ms.localizationpriority: medium
ms.reviewer: inbadian
f1.keywords: NOCSH
ms.collection:
- M365-security-compliance
- m365initiative-defender-endpoint
ms.custom: intro-get-started
ms.openlocfilehash: d332cbf32f5423fb16abb158f9a30a18c2391a22
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/19/2022
ms.locfileid: "64939355"
---
# <a name="get-started-with-microsoft-defender-for-endpoint-plan-1"></a>Uç Nokta için Microsoft Defender Plan 1 ile Kullanmaya başlayın

**Şunlar için geçerlidir:**
- [Uç Nokta için Microsoft Defender Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Microsoft 365 Defender portalı ([https://security.microsoft.com](https://security.microsoft.com)) algılanan tehditler hakkındaki bilgileri görüntülemenizi, uyarılarınızı ve olaylarınızı yönetmenizi, algılanan tehditler üzerinde gerekli eylemleri gerçekleştirmenizi ve cihazları yönetmenizi sağlar. Microsoft 365 Defender portalı, Uç Nokta için Defender Plan 1 ile elde ettiğiniz tehdit koruma özellikleriyle etkileşime geçebileceğiniz yerdir. Aşağıdaki bölümlerde nasıl kullanmaya başlandığı açıklanmaktadır:

- [Microsoft 365 Defender portalı](#the-microsoft-365-defender-portal)
- [Uyarıları & olayları görüntüleme ve yönetme](#view-and-manage-incidents--alerts)
- [Cihazları yönetme](#manage-devices)
- [Raporları görüntüleme](#view-reports)

## <a name="the-microsoft-365-defender-portal"></a>Microsoft 365 Defender portalı

Microsoft 365 Defender portalı ([https://security.microsoft.com](https://security.microsoft.com)), uyarıları görüntüleyebileceğiniz, cihazları yöneteceğiniz ve raporları görüntüleyebileceğiniz yerdir. Microsoft 365 Defender portalında oturum açtığınızda, aşağıdaki resimde gösterildiği gibi Giriş sayfasıyla başlarsınız:

:::image type="content" source="../../media/mde-p1/m365-defender-portal.png" alt-text="Microsoft 365 Defender portalı" lightbox="../../media/mde-p1/m365-defender-portal.png":::

Giriş sayfası güvenlik ekibinize uyarıların, cihaz durumunun ve algılanan tehditlerin anlık görüntü toplam görünümünü sağlar. Bulut için Defender, güvenlik operasyonları ekibinizin aradıkları bilgileri hızlı ve kolay bir şekilde bulabilmesi için ayarlanır.

> [!NOTE]
> Bu makalede gösterilen örneklerimiz, Microsoft 365 Defender portalınızda gördüklerinizden farklı olabilir. Portalınızda gördükleriniz lisanslarınıza ve izinlerinize bağlıdır. Ayrıca, güvenlik ekibiniz kartları ekleyerek, kaldırarak ve yeniden düzenleyerek kuruluşunuzun portalını özelleştirebilir.

### <a name="cards-highlight-key-information-and-include-recommendations"></a>Kartlar önemli bilgileri vurgular ve öneriler ekler

Giriş sayfasında, aşağıdaki görüntüde gösterilen Etkin olaylar kartı gibi kartlar bulunur:

:::image type="content" source="../../media/mde-p1/active-incidents-card.png" alt-text="Etkin olaylar kartı" lightbox="../../media/mde-p1/active-incidents-card.png":::

Kart, daha ayrıntılı bilgileri görüntülemek için seçebileceğiniz bir bağlantı veya düğmeyle birlikte size bir bakışta bilgi sağlar. Örnek Etkin olaylar kartımıza başvurarak **Tüm olayları görüntüle'yi** seçerek olay listemize gidebiliriz.

:::image type="content" source="../../media/mde-p1/incidents.png" alt-text="Olaylar listesi" lightbox="../../media/mde-p1/incidents.png":::

### <a name="navigation-bar-makes-it-easy-to-find-alerts-the-action-center-and-more"></a>Gezinti çubuğu uyarıları, İşlem merkezini ve daha fazlasını bulmayı kolaylaştırır

Ekranın sol tarafındaki gezinti çubuğu olaylar, uyarılar, İşlem merkezi, raporlar ve ayarlar arasında kolayca hareket etmenizi sağlar. Aşağıdaki tabloda gezinti çubuğu açıklanmaktadır.<br/><br/>

| Gezinti çubuğu öğesi | Açıklama |
|:---|:---|
| **Giriş** | [Microsoft 365 Defender portalın](../defender/microsoft-365-security-center-mde.md) Giriş sayfasına gider. |
| **Olaylar & uyarıları** | **Olayları** ve Uyarıları göstermek için **genişletir**. |
| **Olaylar & uyarıları** >  **Olay** | **Olaylar** listesine gider. Uyarılar tetiklendiğinde ve/veya tehditler algılandığında olaylar oluşturulur. Varsayılan olarak, **Olaylar** listesi son 30 güne ilişkin verileri görüntüler ve en son olay ilk sırada listelenir. <br/><br/> Daha fazla bilgi için bkz [. Olaylar](view-incidents-queue.md). |
| **Olaylar & uyarıları** >  **Uyarı** | **Uyarılar** listesine (**Uyarılar kuyruğu** olarak da adlandırılır) gider. Şüpheli veya kötü amaçlı bir dosya, işlem veya davranış algılandığında uyarılar tetiklenir. Varsayılan olarak, **Uyarılar** listesi son 30 güne ilişkin verileri görüntüler ve en son uyarı ilk sırada listelenir. <br/><br/> Daha fazla bilgi için bkz. [Uyarılar](alerts-queue.md). |
| **İşlem merkezi** | düzeltme ve el ile yanıt eylemlerini izleyen İşlem merkezine gider. İşlem merkezi aşağıdaki gibi etkinlikleri izler: <br/>- Microsoft Defender Virüsten Koruma kötü amaçlı bir dosyayla karşılaşır ve ardından bu dosyayı engeller/kaldırır. <br/>- Güvenlik ekibiniz bir cihazı yalıtıyor.<br/>- Uç Nokta için Defender bir dosyayı algılar ve karantinaya alır. <br/><br/> Daha fazla bilgi için bkz [. İşlem merkezi](auto-investigation-action-center.md). |
| **Güvenlik puanı** | İyileştirme eylemlerinin ve ölçümlerinin listesiyle birlikte kuruluşunuzun güvenlik duruşunun bir gösterimini görüntüler. <br/><br/> Daha fazla bilgi için bkz. [Microsoft Güvenli Puanı](../defender/microsoft-secure-score.md). |
| **Learning hub'ı** | Microsoft 365 güvenlik özellikleri hakkında daha fazla bilgi edinmek için erişebileceğiniz öğrenme yollarının listesine gider.  |
| **Bitiş noktası** >  **Arama** | Belirli cihazları cihaz adına göre arayabileceğiniz bir sayfaya gider. Sonuç listesinde, risk düzeyi ve sistem durumu gibi ayrıntıları bir bakışta görebilirsiniz. |
|  **Bitiş noktası** >  **Cihaz envanteri** | Uç Nokta için Defender'a eklenen cihazlar listenize gider. Cihazlar hakkında maruz kalma ve risk düzeyleri gibi bilgiler sağlar. <br/><br/> Daha fazla bilgi için bkz [. Cihaz envanteri](machines-view-overview.md). |
|  **Bitiş noktası** >  **Yapılandırma & temelleri** | **Güvenlik temellerini** ve **Yapılandırma yönetimini** gösterecek şekilde genişletir. |
|  **Bitiş noktası** >  **Yapılandırma & temelleri** >  **Güvenlik temelleri** | Güvenlik temelleri, önerilen güvenlik ayarlarını verimli ve etkili bir şekilde uygulamanıza yardımcı olabilecek önceden yapılandırılmış ilkeler ve ayar gruplarıdır. Temeller, endüstrinin en iyi yöntemlerini temel alan ayarları içerir. Varsayılan ayarları tutabilir veya temellerinizi kuruluşunuzun gereksinimlerine uyacak şekilde özelleştirebilirsiniz. <br/><br/> Daha fazla bilgi için bkz. [Intune'da Windows 10 cihazları yapılandırmak için güvenlik temellerini kullanma](/mem/intune/protect/security-baselines). |
|  **Bitiş noktası** >  **Yapılandırma & temelleri** >  **Yapılandırma yönetimi** | Eklenen cihazlar hakkındaki bilgileri görüntüleyebileceğiniz ve daha fazla cihaz ekleme adımlarını uygulayabileceğiniz **Cihaz yapılandırma yönetimi** sayfasına gider. |
| **Raporlar** | [Tehdit koruması raporunuz](threat-protection-reports.md), [Cihaz durumu ve uyumluluk raporunuz ve](machine-reports.md) [Web koruma raporunuz](web-protection-overview.md) gibi raporlarınıza gider. |
| **Hizmet Durumu** | **Hizmet durumu** ve **İleti merkezi** bağlantılarını içerir.  |
| **Sağlık** >  **Hizmet durumu** | Microsoft 365 yönetim merkezi Hizmet durumu sayfasına gider. Bu sayfa, kuruluşunuzun aboneliklerinde kullanılabilen tüm hizmetler genelinde sistem durumunu görüntülemenizi sağlar.   |
| **Sağlık** >  **İleti merkezi** | Microsoft 365 yönetim merkezi İleti merkezine gider. İleti merkezi planlı değişiklikler hakkında bilgi sağlar. Her ileti, gelenleri, kullanıcıları nasıl etkileyebileceğini ve değişikliklerin nasıl yönetileceğini açıklar. |  
| **İzinler & rolleri** | Microsoft 365 Defender portalını kullanmak için izinler vermenizi sağlar. İzinler Azure Active Directory 'deki (Azure AD) roller aracılığıyla verilir. Bir rol seçtiğinizde açılır pencere bölmesi görüntülenir. Açılır öğe, rol grubuna üye ekleyebileceğiniz veya kaldırabileceğiniz Bir Azure AD bağlantısı içerir. <br/><br/> Daha fazla bilgi edinmek için bkz. [Rol tabanlı erişim denetimini kullanarak portal erişimini yönetme](rbac.md).  |
| **Ayarlar** | Microsoft 365 Defender portalınız (**Güvenlik merkezi** olarak listelenir) ve Uç Nokta için Defender (Uç Nokta olarak listelenir) için genel **ayarlara** gider. <br/><br/> Daha fazla bilgi için bkz. [Ayarlar](../defender/microsoft-365-defender.md#the-microsoft-365-defender-portal). |
| **Diğer kaynaklar** | Azure Active Directory ve Microsoft Purview uyumluluk portalı gibi daha fazla portalın ve merkezin listesini görüntüler. <br/><br/> Daha fazla bilgi için bkz. [Microsoft güvenlik portalları ve yönetim merkezleri](../defender/portals.md). |

> [!TIP]
> Daha fazla bilgi edinmek için [bkz. Microsoft 365 Defender portalına genel bakış](../defender/microsoft-365-security-center-mde.md).

## <a name="view-and-manage-incidents--alerts"></a>Olayları & uyarıları görüntüleme ve yönetme

Microsoft 365 Defender portalında oturum açtığınızda olaylarınızı ve uyarılarınızı görüntüleyip yönettiğinizden emin olun. **Olaylar** listenizle başlayın. Aşağıdaki görüntüde, biri yüksek önem derecesine sahip, diğeri orta önem derecesine sahip olan bir olay listesi gösterilmektedir.

:::image type="content" source="../../media/mde-p1/incidents.png" alt-text="Olaylar listesi":::

Olayla ilgili ayrıntıları görüntülemek için bir olay seçin. Ayrıntılar hangi uyarıların tetiklendiğini, kaç cihaz ve kullanıcının etkilendiğini ve diğer ayrıntıları içerir. Aşağıdaki görüntüde olay ayrıntıları örneği gösterilmektedir.

:::image type="content" source="../../media/mde-p1/single-incident.png" alt-text="Bir olayın ayrıntıları" lightbox="../../media/mde-p1/single-incident.png":::

**Tetiklenen** uyarılar, etkilenen cihazlar ve etkilenen kullanıcı hesapları gibi daha fazla bilgi görüntülemek için Uyarılar, **Cihazlar** ve **Kullanıcılar** sekmelerini kullanın. Buradan, bir cihazı yalıtma, bir dosyayı durdurma ve quarantining gibi el ile yanıt eylemleri gerçekleştirebilirsiniz.

> [!TIP]
> Olay görünümünü kullanma hakkında daha fazla bilgi için bkz **. Olayları** [yönetme](manage-incidents.md).

## <a name="manage-devices"></a>Cihazları yönetme

Kuruluşunuzun cihazlarını görüntülemek ve yönetmek için gezinti çubuğundaki **Uç Noktalar'ın** altında **Cihaz envanteri'ni** seçin. Aşağıdaki görüntüde gösterildiği gibi cihazların listesini görürsünüz:

:::image type="content" source="../../media/mde-p1/device-inventory.png" alt-text="Cihaz envanteri" lightbox="../../media/mde-p1/device-inventory.png":::

Liste, uyarıların oluşturulduğu cihazları içerir. Varsayılan olarak, gösterilen veriler son 30 güne yöneliktir ve en son öğeler ilk sırada listelenir. Cihaz hakkında daha fazla bilgi görüntülemek için bir cihaz seçin. Aşağıdaki resimde gösterildiği gibi bir açılır pencere bölmesi açılır:

:::image type="content" source="../../media/mde-p1/device-inventory-selecteddevice.png" alt-text="Seçili cihaz ayrıntıları" lightbox="../../media/mde-p1/device-inventory-selecteddevice.png":::

Açılır bölme, cihaz için etkin uyarılar gibi ayrıntıları görüntüler ve cihaz yalıtma gibi eylem gerçekleştirme bağlantıları içerir.

Cihazda etkin uyarılar varsa bunları açılır pencere bölmesinde görüntüleyebilirsiniz. Hakkında daha fazla ayrıntı görüntülemek için tek bir uyarı seçin. Ya da cihazı daha fazla araştırırken diğer **cihazlara** bulaşma riskini en aza indirebilmeniz için Cihazı yalıt gibi bir işlem gerçekleştirebilirsiniz.

> [!TIP]
> Daha fazla bilgi edinmek [için Uç Nokta için Defender cihazları listesinde cihazları araştırma bölümüne bakın](investigate-machines.md).

## <a name="view-reports"></a>Raporları görüntüleme

Uç Nokta Için Defender Plan 1'de, Microsoft 365 Defender portalında çeşitli raporlar mevcuttur. Raporlarınıza erişmek için şu adımları izleyin:

1. Microsoft 365 Defender portalına ([https://security.microsoft.com](https://security.microsoft.com)) gidin ve oturum açın.

2. Gezinti çubuğunda **Raporlar'ı** seçin.

3. Listeden bir rapor seçin. Aşağıdaki üç raporu görürsünüz:

   - Tehdit koruma raporu
   - Cihaz durumu raporu
   - Web koruma raporu

> [!TIP]
> Daha fazla bilgi için bkz [. Tehdit koruma raporları](threat-protection-reports.md).

### <a name="threat-protection-report"></a>Tehdit koruma raporu

Tehdit koruması raporunuz için Microsoft 365 Defender portalında **Raporlar'ı** ve ardından **Tehdit koruması'nı** seçin. Tehdit Koruması raporu uyarı eğilimlerini, durumunu, kategorilerini ve daha fazlasını gösterir. Görünümler iki sütun halinde düzenlenmiştir: **Uyarı eğilimleri** ve **Uyarı durumu**, aşağıdaki görüntüde gösterildiği gibi:

:::image type="content" source="../../media/mde-p1/threat-protection-report.png" alt-text="Tehdit koruma raporu" lightbox="../../media/mde-p1/threat-protection-report.png":::

Her listedeki tüm görünümleri görmek için aşağı kaydırın.

- Varsayılan olarak, **Uyarı eğilimleri sütunundaki görünümler** son 30 güne ilişkin verileri görüntüler, ancak son üç ay, son altı ay veya özel bir zaman aralığına (180 güne kadar) ilişkin verileri görüntülemek için bir görünüm ayarlayabilirsiniz.
- **Uyarı durumu** sütunundaki görünümler, önceki iş gününün anlık görüntüsüdür.

> [!TIP]
> Daha fazla bilgi için bkz. [Uç Nokta için Defender'da tehdit koruma raporu](threat-protection-reports.md).

### <a name="device-health-report"></a>Cihaz durumu raporu

Cihaz durumu raporunuzla erişmek için Microsoft 365 Defender portalında **Raporlar'ı** ve ardından **Cihaz durumu'na** tıklayın. Cihaz durumu raporu, kuruluşunuzdaki cihazlarda sistem durumunu ve virüsten korumayı gösterir. [Tehdit koruması raporuna](#threat-protection-report) benzer şekilde görünümler de aşağıdaki görüntüde gösterildiği gibi iki sütun halinde düzenlenmiştir: **Cihaz eğilimleri** ve **Cihaz özeti**:

:::image type="content" source="../../media/mde-p1/device-health-report.png" alt-text="Cihaz durumu raporu" lightbox="../../media/mde-p1/device-health-report.png":::

Her listedeki tüm görünümleri görmek için aşağı kaydırın. Varsayılan olarak, **Cihaz eğilimleri sütunundaki görünümler** son 30 güne ilişkin verileri görüntüler, ancak görünümü son üç aya, son altı aya veya özel bir zaman aralığına (180 güne kadar) ilişkin verileri görüntüleyecek şekilde değiştirebilirsiniz. **Cihaz özet** görünümleri, önceki iş gününün anlık görüntüleridir.

> [!TIP]
> Daha fazla bilgi için bkz [. Cihaz durumu](machine-reports.md).

### <a name="web-protection-report"></a>Web koruma raporu

Cihaz durumu raporunuzla erişmek için Microsoft 365 Defender portalında **Raporlar'ı** ve ardından **Web koruması'nı** seçin. Web koruma raporu, aşağıdaki görüntüde gösterildiği gibi kötü amaçlı URL'ler ve engellenen URL'lere erişme girişimleri gibi zaman içindeki algılamaları gösterir:

:::image type="content" source="../../media/mde-p1/web-protection-report.png" alt-text="Web koruma raporu" lightbox="../../media/mde-p1/web-protection-report.png":::

Web koruması raporundaki tüm görünümleri görmek için ekranı aşağı kaydırın. Bazı görünümler daha fazla ayrıntı görüntülemenizi, tehdit koruma özelliklerinizi yapılandırmanızı ve hatta Uç Nokta için Defender'da özel durum olarak hizmet veren göstergeleri yönetmenizi sağlayan bağlantılar içerir.

> [!TIP]
> Daha fazla bilgi için bkz. [Web koruması](web-protection-overview.md).

## <a name="next-steps"></a>Sonraki adımlar

- [Uç Nokta için Microsoft Defender Plan 1'i yönetme](mde-p1-maintenance-operations.md)
- [Uç Nokta için Microsoft Defender](microsoft-defender-endpoint.md)
