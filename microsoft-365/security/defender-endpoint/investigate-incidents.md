---
title: E-Uç Nokta için Microsoft Defender'daki olayları araştır
description: İlişkili uyarıları görüntüleme, olayı yönetme ve bir olayı araştırmanıza yardımcı olacak uyarı meta verilerini görüntüleme
keywords: araştırma, olay, uyarılar, meta veriler, risk, algılama kaynağı, etkilenen cihazlar, desenler, korelasyon
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365-initiative-defender-endpoint
ms.topic: article
ms.technology: mde
ms.openlocfilehash: d66dde2c3f346449c7ecd03a7ef577e39cf98991
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64468809"
---
# <a name="investigate-incidents-in-microsoft-defender-for-endpoint"></a>E-Uç Nokta için Microsoft Defender'daki olayları araştır

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta için Microsoft Defender Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta için Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


Anızı etkileyen olayları araştıryın, bunların ne anlama gelen olduğunu an olun ve bunları çözmek için kanıtları harmanlar.

Bir olayı incelerken şunları görüyorsunuz:

- Olay ayrıntıları
- Olay yorumları ve eylemleri
- Sekmeler (uyarılar, cihazlar, soruşturmalar, kanıt, grafik)

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4qLUV]

## <a name="analyze-incident-details"></a>Olay ayrıntılarını çözümleme

Olay bölmesini görmek için bir **olayı tıklatın**. Olay **ayrıntılarını ve ilgili bilgileri** (uyarılar, cihazlar, soruşturmalar, kanıt, grafik) görmek için Olay sayfasını aç'ı seçin.

:::image type="content" source="images/atp-incident-details.png" alt-text="Olayın ayrıntıları" lightbox="images/atp-incident-details.png":::

### <a name="alerts"></a>Uyarılar

Uyarıları inceler ve bir olayda nasıl bağlantılı olduklarını öğrensiniz. Uyarılar, aşağıdaki nedenlere göre olaylarda gruptur:

- Otomatik araştırma - Otomatik araştırma, özgün uyarıyı araştırırken bağlantılı uyarıyı tetikler
- Dosya özellikleri - Uyarıyla ilişkilendirilmiş dosyaların benzer özellikleri vardır
- El ile ilişkilendirme - Bir kullanıcı uyarıları el ile birbirine bağlı
- Proximate time - Uyarılar belirli bir zaman çerçevesi içinde aynı cihazda tetikldi
- Aynı dosya - Uyarıyla ilişkilendirilmiş dosyalar tamamen aynıdır
- Aynı URL - Uyarıyı tetikleyen URL tamamen aynıdır

:::image type="content" source="images/atp-incidents-alerts-reason.png" alt-text="Uyarıların o olayda neden birbirine bağlı olduğunu gösteren olay ayrıntıları sayfasının olduğu Uyarılar sekmesi" lightbox="images/atp-incidents-alerts-reason.png":::

Ayrıca, uyarıyı yönetebilir ve diğer bilgilerle birlikte uyarı meta verilerini de görebilirsiniz. Daha fazla bilgi için bkz [. Uyarıları araştırma](investigate-alerts.md).

### <a name="devices"></a>Cihazlar

Ayrıca, ilgili veya bir olayın parçası olan cihazları da araştırabilirsiniz. Daha fazla bilgi için bkz. [Cihazları araştırma](investigate-machines.md).

:::image type="content" source="images/atp-incident-device-tab.png" alt-text="Olay ayrıntıları sayfasında Cihazlar sekmesi" lightbox="images/atp-incident-device-tab.png":::

### <a name="investigations"></a>İncelemeler

Sistem **tarafından başlatılan** tüm otomatik soruşturmaları olay uyarılarına yanıt olarak görmek için Araştırmalar'ı seçin.

:::image type="content" source="images/atp-incident-investigations-tab.png" alt-text="Olay ayrıntıları sayfasındaki soruşturmalar sekmesi" lightbox="images/atp-incident-investigations-tab.png":::

## <a name="going-through-the-evidence"></a>Kanıtın üzerinden geçerek

Uç Nokta için Microsoft Defender, uyarılarda olayların tüm desteklenen olaylarını ve şüpheli varlıklarını otomatik olarak inceler ve önemli dosyalar, işlemler, hizmetler ve daha fazlası hakkında otomatik yanıt ve bilgi sağlar.

Çözümlenen varlıkların her biri virüs bulaştırıldı, düzeltildi veya şüpheli olarak işaretlenir.

:::image type="content" source="images/atp-incident-evidence-tab.png" alt-text="Olay ayrıntıları sayfasındaki Kanıt sekmesi" lightbox="images/atp-incident-evidence-tab.png":::

## <a name="visualizing-associated-cybersecurity-threats"></a>İlişkili siber güvenlik tehditlerini görselleştirme

Uç Nokta için Microsoft Defender tehdit bilgilerini bir olayda bir araya toplar ve böylece çeşitli veri noktalarından gelen desenleri ve korelasyonları görmek için kullanılır. Bu tür bağıntıyı olay grafiği aracılığıyla görüntüabilirsiniz.

### <a name="incident-graph"></a>Olay grafiği

Güvenlik **Graph** siber güvenlik saldırılarının anlat olduğu bir anlatıdır. Örneğin, hangi giriş noktası olduğunu, hangi cihazda güvenliğin veya etkinliğin gözlenen bir göstergesini gösterir. vb.

:::image type="content" source="images/atp-incident-graph-tab.png" alt-text="Olay grafiği" lightbox="images/atp-incident-graph-tab.png":::

Olay grafiğinde çemberlere tıklayarak kötü amaçlı dosyaların ayrıntılarını, ilişkili dosya algılamalarını, dünya çapında kaç örnek olduğunu, kaç örnek olduğunu, bu durumda kaç örnek olduğunu, kuruluş içinde gözlemlenmiş olup olmadığını görebilirsiniz.

:::image type="content" source="images/atp-incident-graph-details.png" alt-text="Olay ayrıntıları sayfası" lightbox="images/atp-incident-graph-details.png":::

## <a name="related-topics"></a>İlgili konular

- [Olay sırası](/microsoft-365/security/defender-endpoint/view-incidents-queue)
- [E-Uç Nokta için Microsoft Defender'daki olayları araştır](/microsoft-365/security/defender-endpoint/investigate-incidents)
- [Olay Uç Nokta için Microsoft Defender yönetme](/microsoft-365/security/defender-endpoint/manage-incidents)
