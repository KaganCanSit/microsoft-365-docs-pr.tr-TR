---
title: Uç Nokta Planı 1 için Microsoft Defender ile çalışmaya başlama
description: Uç Nokta Plan 1 için Defender'ı kullanmaya başlama. Bulut için Defender'ı kullanmayı, uyarıları ve cihazları yönetmeyi ve raporları görüntülemeyi öğrenin.
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
ms.openlocfilehash: d4e585a7714bddc8c89de75ae49464da7bfe0305
ms.sourcegitcommit: aac7e002ec6e10a41baa2d0bd38614b0ed471a70
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/27/2022
ms.locfileid: "63010020"
---
# <a name="get-started-with-microsoft-defender-for-endpoint-plan-1"></a>Uç Nokta Planı 1 için Microsoft Defender ile çalışmaya başlama

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Bu Microsoft 365 Defender portalı ([https://security.microsoft.com](https://security.microsoft.com)), algılanan tehditlerle ilgili bilgileri görüntülemenize, uyarılarınızı ve olaylarınızı yönetmenize, algılanan tehditlere karşı gerekli eylemi uygulamanıza ve cihazları yönetmenize olanak tanır. En Microsoft 365 Defender portalı, Uç Nokta Planı 1 için Defender ile edinen tehdit koruması özellikleriyle etkileşime nereden başlayabileceksiniz? Aşağıdaki bölümlerde nasıl baş çık çık başlandı? açıklanmaktadır:

- [Microsoft 365 Defender portalı](#the-microsoft-365-defender-portal)
- [Uyarılarda olayları görüntüleme & yönetme](#view-and-manage-incidents--alerts)
- [Cihazları yönetme](#manage-devices)
- [Raporları görüntüleme](#view-reports)

## <a name="the-microsoft-365-defender-portal"></a>Microsoft 365 Defender portalı

En Microsoft 365 Defender portalı ([https://security.microsoft.com](https://security.microsoft.com)), uyarıları görüntüley İhlalleri görüntüleytnizi, cihazları yönettnizi ve raporları görüntüley yeridir. Oturum açma portalında Microsoft 365 Defender, aşağıdaki resimde gösterildiği gibi Giriş sayfasıyla başlarsınız:

:::image type="content" source="../../media/mde-p1/m365-defender-portal.png" alt-text="Microsoft 365 Defender portalı":::

Giriş sayfası, güvenlik ekibinize uyarıların, cihazın durumunun ve algılanan tehditlerin anlık görüntü toplu görünümünü sağlar. Bulut için Defender, güvenlik işlemleri ekibinin aray çalışmaları için hızlı ve kolay bir şekilde bilgi edineceği şekilde ayarlanır.

> [!NOTE]
> Bu makalede gösterilen örneklerimiz, kullanıcı portalında gördüğünüzden Microsoft 365 Defender olabilir. Portalda ne göreceğiniz, lisanslara ve izinlere bağlıdır. Buna ek olarak, güvenlik takımınız kartları ekleyerek, kaldırarak ve yeniden düzenleyerek organizasyon portalınızı özelleştirilebilir.

### <a name="cards-highlight-key-information-and-include-recommendations"></a>Kartlar önemli bilgileri vurgular ve öneriler içerir

Giriş sayfası, aşağıdaki resimde gösterilen Etkin olayları kartı gibi kartları içerir:

:::image type="content" source="../../media/mde-p1/active-incidents-card.png" alt-text="Etkin olay kartı":::

Kart size bir bakışta bilgi sağlar ve daha ayrıntılı bilgileri görüntülemek için seçerek ek bir bağlantı veya düğme sağlar. Örnek Etkin olaylar kartımıza başvurup Tüm olayları görüntüle'yi **seçerek** olay listemize bakabilirsiniz.

:::image type="content" source="../../media/mde-p1/incidents.png" alt-text="Olaylar listesi":::

### <a name="navigation-bar-makes-it-easy-to-find-alerts-the-action-center-and-more"></a>Gezinti çubuğu uyarıları, İşlem merkezini ve daha fazlasını bulmayı kolaylaştırır

Ekranın sol tarafındaki gezinti çubuğu olaylar, uyarılar, İşlem merkezi, raporlar ve ayarlar arasında kolayca hareket etmenizi sağlar. Aşağıdaki tabloda gezinti çubuğu açık almaktadır.<br/><br/>

| Gezinti çubuğu öğesi | Açıklama |
|:---|:---|
| **Giriş** | Kullanıcı portalının Giriş sayfasına [Microsoft 365 Defender.](../defender/microsoft-365-security-center-mde.md) |
| **Olaylar & uyarıları** | Olayları ve Uyarıları **gösterecek şekilde** **genişletildi**. |
| **Olaylar & uyarıları** >  **Olaylar** | Olaylar **listesine** gidin. Uyarılar tetiklendiğinde ve/veya tehdit algılandığında olaylar oluşturulur. Varsayılan olarak, **Olaylar listesi** son 30 günlük verileri görüntüler ve en son olay en başta listelenir. <br/><br/> Daha fazla bilgi edinmek için bkz. [Olaylar](view-incidents-queue.md). |
| **Olaylar & uyarıları** >  **Uyarılar** | Uyarılar listesine **(Uyarılar** sırası olarak da adlandırılır **) gidin**. Şüpheli veya kötü amaçlı bir dosya, işlem veya davranış algılandığında uyarılar tetiklenir. Varsayılan olarak, **Uyarılar listesi** son 30 günlük verileri görüntüler ve en son uyarı en başta listelenir. <br/><br/> Daha fazla bilgi edinmek için bkz [. Uyarılar](alerts-queue.md). |
| **İşlem merkezi** | Düzeltme ve el ile yanıt eylemlerini takip etmek için İşlem merkezine gidin. İşlem merkezi aşağıdaki gibi etkinlikleri izler: <br/>- Microsoft Defender Virüsten Koruma bir dosyayla karşılaşır ve o dosyayı engeller/kaldırır. <br/>- Güvenlik ekipleriniz bir cihazı yalıtır.<br/>- Uç Nokta için Defender dosyayı algılar ve karantinaya eder. <br/><br/> Daha fazla bilgi edinmek için bkz. [İşlem merkezi](auto-investigation-action-center.md). |
| **Skoru güvenli hale** | Geliştirme eylemleri ve ölçümlerin listesiyle birlikte, organizasyon organizasyon güvenlik mezra nın bir gösterimini görüntüler. <br/><br/> Daha fazla bilgi edinmek için [bkz. Microsoft Güvenli Puanı](../defender/microsoft-secure-score.md). |
| **Learning hub** | Güvenlik özellikleri hakkında daha fazla bilgi edinmek için erişebilirsiniz eğitim yollarının Microsoft 365 gidin.  |
| **Uç noktalar** >  **Arama** | Cihaz adına göre belirli cihazları arayabilirsiniz. Sonuç listesinde, risk düzeyi ve sağlık durumu gibi ayrıntıları bir bakışta görebilirsiniz. |
|  **Uç noktalar** >  **Cihaz envanteri** | Uç nokta için Defender'a eklen cihazlar listenize gidin. Cihazlar hakkında, pozlama ve risk düzeyleri gibi bilgiler sağlar. <br/><br/> Daha fazla bilgi edinmek için bkz [. Cihaz envanteri](machines-view-overview.md). |
|  **Uç noktalar** >  **Yapılandırma & taban çizgilerini yapılandırma** | Güvenlik taban çizgilerini **ve Yapılandırma yönetimini gösterecek** **şekilde genişletildiğinde**. |
|  **Uç noktalar** >  **Yapılandırma & taban çizgilerini yapılandırma** >  **Güvenlik taban çizgilerini** | Güvenlik taban çizgisi, önerilen güvenlik ayarlarını verimli ve etkili bir şekilde uygulamanıza yardımcı olacak, önceden yapılandırılmış ilkeler ve ayar gruplarıdır. Taban çizgisi, sektöre yönelik en iyi uygulamaları temel alan ayarları içerir. Varsayılan ayarları saklayabilirsiniz veya taban çizgilerinizi, kurum gereksinimlerine uygun olarak özelleştirebilirsiniz. <br/><br/> Daha fazla bilgi edinmek için bkz[. Intune'da güvenlik Windows 10 için güvenlik taban çizgilerini kullanma](/mem/intune/protect/security-baselines). |
|  **Uç noktalar** >  **Yapılandırma & taban çizgilerini yapılandırma** >  **Yapılandırma yönetimi** | Cihaz yapılandırma yönetimi **sayfasına gidin. Burada** , yerleşik cihazlarla ilgili bilgileri görüntüleyebilirsiniz ve daha fazla cihaz ekleme adımlarını izleyin. |
| **Raporlar** | Tehdit koruması raporunuz, Cihaz sistem durumu ve uyumluluk [raporunuz](threat-protection-reports.md) ve Web koruma [raporunuz](machine-reports.md) gibi [raporlarınıza gidin](web-protection-overview.md). |
| **Hizmet Durumu** | Hizmet durumu ve **İleti merkezi** **bağlantılarını içerir**.  |
| **Durum** >  **Hizmet durumu** | Durum sayfasında Hizmet durumu sayfasına Microsoft 365 yönetim merkezi. Bu sayfa, kurum abonelikleriyle birlikte kullanılabilen tüm hizmetler genelinde sistem durumunu görüntülemenizi sağlar.   |
| **Durum** >  **İleti merkezi** | İleti merkezinde İleti merkezine Microsoft 365 yönetim merkezi. İleti merkezi planlanan değişiklikler hakkında bilgi sağlar. Her iletide, neler olduğu, bunun kullanıcıları nasıl etkileyebilecek olduğu ve değişikliklerin nasıl yönet kullanıcılar tarafından yönet olabileceği açık vardır. |  
| **İzinler & rolleri** | Kullanıcı portalının kullanımına izin Microsoft 365 Defender olanak sağlar. Azure Active Directory (Azure AD) Azure Active Directory üzerinden izinler verebilirsiniz. Bir rol seçin; bir açılır pencere görüntülenir. Uçarak çıkış, bir rol grubuna üye eklerini veya kaldırabilirsiniz, Azure AD'nin bağlantısını içerir. <br/><br/> Daha fazla bilgi edinmek için [bkz. Rol tabanlı erişim denetimi kullanarak portal erişimini yönetme](rbac.md).  |
| **Ayarlar** | Güvenlik portalınız (Güvenlik merkezi olarak **Microsoft 365 Defender) ve** Uç Nokta için Defender (Uç Nokta olarak listelenmiş) genel **ayarlara gidin**. <br/><br/> Daha fazla bilgi edinmek için bkz. [Ayarlar](../defender/microsoft-365-defender.md#the-microsoft-365-defender-portal). |
| **Diğer kaynaklar** | E-Azure Active Directory gibi daha fazla portal ve Microsoft 365 uyumluluk merkezi. <br/><br/> Daha fazla bilgi edinmek için [bkz. Microsoft güvenlik portalları ve yönetim merkezleri](../defender/portals.md). |

> [!TIP]
> Daha fazla bilgi edinmek için [portala Microsoft 365 Defender bakın](../defender/microsoft-365-security-center-mde.md).

## <a name="view-and-manage-incidents--alerts"></a>Uyarılarda olayları & yönetme

Güvenlik portalında oturum Microsoft 365 Defender, olaylarınızı ve uyarılarınızı görüntüden ve yönet'den emin olun. Olaylar **listenizi başlatabilirsiniz** . Aşağıdaki resimde, yüksek önem düzeyi yüksek olan bir olay ve orta önem düzeyi yüksek olan bir diğer olay listesi görüntülenir.

:::image type="content" source="../../media/mde-p1/incidents.png" alt-text="Olaylar listesi":::

Olayla ilgili ayrıntıları görüntülemek için bir olay seçin. Hangi uyarıların tetiklendiği, kaç cihaz ve kullanıcının etkilendiği ve diğer ayrıntıları içerir. Aşağıdaki resimde olay ayrıntılarının bir örneği yer aldı.

:::image type="content" source="../../media/mde-p1/single-incident.png" alt-text="Olay ayrıntıları":::

Tetiklenen **uyarılar**, **etkilenen** cihazlar ve etkilenen  kullanıcı hesapları gibi daha fazla bilgiyi görüntülemek için Uyarılar, Cihazlar ve Kullanıcılar sekmelerini kullanın. Buradan, cihazı yalıtma, bir dosyayı durdurma ve başka bir dosyaya yer alma gibi elle yanıt eylemleri gerçekleştirebilirsiniz.

> [!TIP]
> Olay görünümünü kullanma hakkında daha fazla **bilgi edinmek** için bkz. [Olayları yönetme](manage-incidents.md).

## <a name="manage-devices"></a>Cihazları yönet

Kuruluş cihazlarınızı görüntülemek ve yönetmek için gezinti çubuğundaki Uç noktalar'ın altında **Cihaz** envanteri'ni **seçin**. Aşağıdaki resimde gösterildiği gibi cihazların listesini görüntülenir:

:::image type="content" source="../../media/mde-p1/device-inventory.png" alt-text="Cihaz envanteri":::

Bu liste, uyarıların oluşturulmuş olduğu cihazları içerir. Varsayılan olarak, gösterilen veriler son 30 gündür ve en son öğeler önce listelenir. Bir cihaz hakkında daha fazla bilgi görüntülemek için o cihazı seçin. Aşağıdaki resimde gösterildiği gibi bir açılır pencere bölmesi açılır:

:::image type="content" source="../../media/mde-p1/device-inventory-selecteddevice.png" alt-text="Seçilen cihaz ayrıntıları":::

Uçarak çıkış bölmesi, cihaz için etkin uyarılar gibi ayrıntıları görüntüler ve bir cihazı yalıtma gibi işlem yapmak için gereken bağlantıları içerir.

Cihazda etkin uyarılar varsa, bunları çıkış bölmesinde görüntüleyebilirsiniz. Hakkında daha fazla ayrıntı görüntülemek için tek bir uyarı seçin. Ya da Cihazı Yalıt gibi bir işlemle cihazı daha fazla araştırıp diğer cihazlara bulaşma riskini en aza indirebilirsiniz.

> [!TIP]
> Daha fazla bilgi için bkz [. Uç nokta cihazları için Defender listesinde cihazları araştırma](investigate-machines.md).

## <a name="view-reports"></a>Raporları görüntüleme

Uç Nokta Planı 1 için Defender'da, uygulama portalında Microsoft 365 Defender vardır. Raporlarınıza erişmek için şu adımları izleyin:

1. Erişim portalına Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com) ) ve oturum açın.

2. Gezinti çubuğunda Raporlar'ı **seçin**.

3. Listeden bir rapor seçin. Aşağıdaki üç raporu görüyorsunuz:

   - Tehdit koruması raporu
   - Cihaz durumu raporu
   - Web koruma raporu

> [!TIP]
> Daha fazla bilgi için bkz [. Tehdit koruması raporları](threat-protection-reports.md).

### <a name="threat-protection-report"></a>Tehdit koruması raporu

Tehdit koruması raporunuza erişmek için, Microsoft 365 Defender raporlar'ı **ve ardından Tehdit** **koruması'ı seçin**. Tehdit Koruması raporu uyarı eğilimlerini, durumu, kategorileri ve daha fazlasını gösterir. Görünümler iki sütunda düzenlenmiştir: **Aşağıdaki** resimde **gösterildiği gibi**, Uyarı eğilimleri ve Uyarı durumu:

:::image type="content" source="../../media/mde-p1/threat-protection-report.png" alt-text="Tehdit koruması raporu":::

Her bir listede tüm görünümleri görmek için aşağı kaydırın.

- Varsayılan olarak, Uyarı eğilimleri sütunundaki  görünümler son 30 günlük verileri görüntüler, ancak son üç aya, son altı aya veya özel bir zaman aralığına (180 gün kadar) yönelik verileri görüntülemek üzere bir görünüm oluşturabilirsiniz.
- Uyarı durumu **sütunundaki görünümler** , önceki iş günü için bir anlık görüntüdir.

> [!TIP]
> Daha fazla bilgi edinmek için bkz [. Uç Nokta için Defender'da tehdit koruması raporu](threat-protection-reports.md).

### <a name="device-health-report"></a>Cihaz durumu raporu

Cihaz durumu raporunuza erişmek için, Rapor Microsoft 365 Defender ve **ardından** Cihaz **durumu'Microsoft 365 Defender'ı seçin**. Cihaz durumu raporu, kurum genelindeki cihazlar arasında durum durumunu ve virüsten koruma yazılımını gösterir. Tehdit koruması [raporuna benzer](#threat-protection-report) şekilde görünümler iki sütunda düzenlenmiştir: **Cihaz** eğilimleri ve Cihaz **özeti, aşağıdaki** resimde gösterildiği gibi:

:::image type="content" source="../../media/mde-p1/device-health-report.png" alt-text="Cihaz durumu raporu":::

Her bir listede tüm görünümleri görmek için aşağı kaydırın. Varsayılan olarak, Cihaz eğilimleri sütunundaki  görünümler son 30 günlük verileri görüntüler, ancak görünümü son üç aya, son altı aya veya özel bir zaman aralığına (180 gün kadar) yönelik verileri görüntüecek şekilde değiştirebilirsiniz. Cihaz **özeti görünümleri** , önceki iş günü anlık görüntüleridir.

> [!TIP]
> Daha fazla bilgi edinmek için bkz. [Cihaz durumu](machine-reports.md).

### <a name="web-protection-report"></a>Web koruma raporu

Cihaz durumu raporunuza erişmek için, Mobil Microsoft 365 Defender **Raporlar'ı ve** ardından **Web koruması'ı seçin**. Web koruma raporu, aşağıdaki resimde gösterildiği gibi kötü amaçlı URL'ler ve engellenen URL'lere erişme girişimleri gibi zamanla algılamaları gösterir:

:::image type="content" source="../../media/mde-p1/web-protection-report.png" alt-text="Web koruma raporu":::

Web koruma raporu'daki tüm görünümleri görmek için sayfayı aşağı kaydırın. Bazı görünümler daha fazla ayrıntı görüntülemenize, tehdit koruması özelliklerinizi yapılandırmanıza ve hatta Uç Nokta için Defender'da özel durumlara hizmet eden göstergeleri yönetmenizi sağlayan bağlantılar içerir.

> [!TIP]
> Daha fazla bilgi edinmek için bkz. [Web koruması](web-protection-overview.md).

## <a name="next-steps"></a>Sonraki adımlar

- [Uç Nokta Planı 1 için Microsoft Defender'ı yönetme](mde-p1-maintenance-operations.md)
- [Uç Nokta için Microsoft Defender](microsoft-defender-endpoint.md)
