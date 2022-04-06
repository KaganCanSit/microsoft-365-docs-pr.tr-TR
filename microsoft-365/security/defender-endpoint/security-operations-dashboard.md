---
title: Microsoft Defender Güvenlik Merkezi İşlemler panosu
description: Risk altında cihazları tanımlamak, hizmetin durumunu izlemek ve cihazlar ve uyarılar hakkında istatistikleri ve bilgileri görmek için panoyu kullanın.
keywords: pano, uyarılar, yeni, devam eden, çözümlenen, risk, risk altında cihazlar, bulaşmalar, raporlama, istatistik, grafikler, grafikler, sağlık, etkin kötü amaçlı yazılım algılamaları, tehdit kategorisi, kategoriler, parola çalmak, fidye yazılımı, istismar, tehdit, düşük önem düzeyi, etkin kötü amaçlı yazılım
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: c08f592ac72be10bb4b967521e7e504a9ae70a86
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64472649"
---
# <a name="microsoft-defender-security-center-security-operations-dashboard"></a>Microsoft Defender Güvenlik Merkezi İşlemler panosu

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:**
- [Uç Nokta için Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)

> Bu deneyimi Uç Nokta için Microsoft Defender? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-secopsdashboard-abovefoldlink)

Güvenlik **işlemleri panosu**, en uç noktada algılama ve yanıtlama ortaya çıkar. Algılamaların nerede görüldükleri ve yanıt eylemlerinin gerekli olduğu vurgular hakkında üst düzey bir genel bakış sağlar.

Pano aşağıdakilerin anlık görüntüsünü görüntüler:

- Etkin uyarılar
- Risk altında cihazlar
- Algılayıcı sağlığı
- Hizmet durumu
- Günlük cihazlar raporlaması
- Etkin otomatik soruşturmalar
- Otomatik soruşturma istatistikleri
- Risk altında kullanıcılar
- Şüpheli etkinlikler

:::image type="content" source="images/atp-sec-ops-dashboard.png" alt-text="Güvenlik işlemleri panosu" lightbox="images/atp-sec-ops-dashboard.png":::

Ağ üzerinde şüpheli etkinliklerin gerçekleştir olup olmadığını, nerede ve ne zaman olduğunu hemen belirlemek için uyarıları ve cihazları inceler ve araştırabilirsiniz; bu etkinliklerin hangi bağlamda olduğunu anlamanıza yardımcı olur.

Güvenlik **işlemleri panosunda** , cihazda önemli etkinliklerin veya davranışların tanımlanmasını kolaylaştırmak için toplanan olayları görürsünüz. Ayrıca ayrıntılı olaylara ve düşük düzeyli göstergelere de detaya girsiniz.

Ayrıca, kurum genel durumuyla ilgili görsel ipuçları vermek için tıklanabilir kutucuklar da vardır. Her kutucuk ilgili genel görünümün ayrıntılı bir görünümünü açar.

## <a name="active-alerts"></a>Etkin uyarılar

Kutucukta, ağda son 30 gün içinde etkin uyarıların toplam sayısını görüntüebilirsiniz. Uyarılar Yeni ve Sürüyor **olarak** **gruplandı**.

:::image type="content" source="images/active-alerts-tile.png" alt-text="Etkin uyarılar sayfası" lightbox="images/active-alerts-tile.png":::

Her grup, ilgili uyarı önem düzeyine göre daha da alt kategorilere ayrılmıştır. Her uyarı halkası içindeki uyarı sayısını tıklatın ve o kategorinin kuyruğuna ait sıralanmış görünümü görüntüleyin (Yeni **veya** **Sürüyor**).

Daha fazla bilgi için [Uyarılar'a genel bakış bilgilerine bakın](alerts-queue.md).

Her satır bir uyarı önem düzeyi kategorisi ve uyarının kısa bir açıklamasını içerir. Ayrıntılı görünümünü görmek için uyarıya tıkabilirsiniz. Daha fazla bilgi için Bkz[. Uç Nokta için Microsoft Defender ve Uyarılar'a](investigate-alerts.md) [genel bakış](alerts-queue.md).

## <a name="devices-at-risk"></a>Risk altında cihazlar

Bu kutucuk size, en yüksek etkin uyarı sayısına sahip cihazların listesini gösterir. Her cihaz için toplam uyarı sayısı cihaz adının yanında bir daire içinde gösterilir ve kutucuğun en ucundaki önem düzeyine göre daha da kategorilere ayrılmıştır (etiketini görmek için her önem derecesi çubuğunun üzerine gelin).

:::image type="content" source="images/devices-at-risk-tile.png" alt-text="Risk altında Cihazlar sayfası" lightbox="images/devices-at-risk-tile.png":::

Bu cihazla ilgili ayrıntıları görmek için cihazın adına tıklayın. Daha fazla bilgi için Bkz[. Cihazlar listesinde Uç Nokta için Microsoft Defender araştırma](investigate-machines.md).

Etkin uyarı **sayısına göre** sıralanmış olarak doğrudan Cihazlar listesine gitmek **için** kutucuğun en üstünde Cihazlar listesine de tıkabilirsiniz. Daha fazla bilgi için Bkz[. Cihazlar listesinde Uç Nokta için Microsoft Defender araştırma](investigate-machines.md).

## <a name="devices-with-sensor-issues"></a>Algılayıcı sorunu olan cihazlar

Algılayıcı **sorunu olan cihazlar kutucuğu**, tek bir cihazın algılayıcı verilerini en iyi şekilde ve en iyi şekilde Uç Nokta için Microsoft Defender sağlar. Kaç cihaza dikkat gerek olduğunu rapor ediyor ve sorunlu cihazları tanımlamanıza yardımcı oluyor.

:::image type="content" source="images/atp-tile-sensor-health.png" alt-text="Algılayıcı sorunları olan cihazlar kutucuğu" lightbox="images/atp-tile-sensor-health.png":::

Hizmete düzgün bir şekilde rapor etmek için bildirilen cihazların sayısı hakkında bilgi sağlayan iki durum göstergesi vardır:

- **Yanlış Yapılandırılmış: Bu** cihazlar kısmen algılayıcı verilerini Uç Nokta için Microsoft Defender hizmetine bildiriyor olabilir ve düzeltilmesi gereken yapılandırma hataları olabilir.
- **Etkin değil**: Geçen ay içinde Uç Nokta için Microsoft Defender için raporlamayı durduran cihazlar.

Gruplardan herhangi birini tıklatmanız, tercihe bağlı olarak filtrelenmiş cihazlar listesine yönlendirildiniz. Daha fazla bilgi için bkz [. Algılayıcı durumunu denetleme](check-sensor-status.md) ve [Cihazları araştırma](investigate-machines.md).

## <a name="service-health"></a>Hizmet durumu

Bu **Hizmet durumu** kutucuğu, hizmetin etkin olup olduğunu veya sorun olup olduğunu size haber sağlar.

:::image type="content" source="images/status-tile.png" alt-text="Sayfa Hizmet durumu sayfası" lightbox="images/status-tile.png":::

Hizmet durumu hakkında daha fazla bilgi için bkz[. Hizmet Uç Nokta için Microsoft Defender denetleme](service-status.md).

## <a name="daily-devices-reporting"></a>Günlük cihazlar raporlaması

Günlük **cihazlar raporlama kutucuğu** , son 30 gün içinde günlük olarak rapor eden cihazların sayısını gösteren bir çubuk grafik gösterir. Her gün raporlama yapılan cihazların tam sayısını görmek için grafikte tek tek çubukların üzerine gelin.

:::image type="content" source="images/atp-daily-devices-reporting.png" alt-text="Günlük cihazlar raporlama kutucuğu" lightbox="images/atp-daily-devices-reporting.png":::

## <a name="active-automated-investigations"></a>Etkin otomatik soruşturmalar

Etkin otomatik soruşturmalar kutucuğunu kullanarak, ağınız için son 30 gün içinde yapılan otomatik **soruşturmaların toplam sayısını görüntüebilirsiniz** . Araştırma, Bekleyen eylem, **Cihaz bekleniyor** ve Çalışıyor **olarak** **gruplandı**.

:::image type="content" source="images/atp-active-investigations-tile.png" alt-text="Etkin otomatik soruşturmalar" lightbox="images/atp-active-investigations-tile.png":::

## <a name="automated-investigations-statistics"></a>Otomatik soruşturma istatistikleri

Bu kutucuk, son yedi gün içinde otomatik soruşturmalarla ilgili istatistikleri gösterir. Tamamlanan araştırma sayısını, başarılı bir şekilde düzeltilen soruşturmaların sayısını, bir soruşturmanın başlatılması için gereken ortalama bekleme süresi, bir uyarıyı düzeltmek için gereken ortalama süre, araştırılan uyarı sayısını ve genel bir elle incelemeden kaydedilen otomasyon saatlerini gösterir. 

:::image type="content" source="images/atp-automated-investigations-statistics.png" alt-text="Otomatik soruşturma istatistikleri" lightbox="images/atp-automated-investigations-statistics.png":::

Uygun kategoriye **göre filtrelenmiş** olarak Araştırma sayfasına gitmek için Otomatik  soruşturmalar **, Düzeltilen** soruşturmalar ve Araştırılan Uyarılar'a tıkleyebilirsiniz. Bu, bağlam içinde soruşturmaların ayrıntılı dökümünü görmenizi sağlar.

## <a name="users-at-risk"></a>Risk altında kullanıcılar

Kutucuk en etkin uyarılara ve yüksek, orta veya düşük uyarılarda görülen uyarı sayısına sahip kullanıcı hesaplarının listesini gösterir. 

:::image type="content" source="images/atp-users-at-risk.png" alt-text="Risk altında kullanıcılar sayfası" lightbox="images/atp-users-at-risk.png":::

Kullanıcı hesabıyla ilgili ayrıntıları görmek için kullanıcı hesabına tıklayın. Daha fazla bilgi için bkz [. Kullanıcı hesabını araştırma](investigate-user.md).

> Bu deneyimi Uç Nokta için Microsoft Defender? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-secopsdashboard-belowfoldlink)

## <a name="related-topics"></a>İlgili konular

- [Kullanıcı Uç Nokta için Microsoft Defender anlama](use.md)
- [Portala genel bakış](portal-overview.md)
- [Threat & Vulnerability Management panosunun görünümünü görüntüleme](tvm-dashboard-insights.md)
- [Threat Analytics panosuna göz atarak önerilen risk azaltma eylemleri gerçekleştirin](threat-analytics.md)
