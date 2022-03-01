---
title: Uç nokta için Microsoft Defender'da olayları araştırma
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
ms.openlocfilehash: 2a297813fbde94499f2d239627be6c33c153e8b0
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/12/2022
ms.locfileid: "63011792"
---
# <a name="investigate-incidents-in-microsoft-defender-for-endpoint"></a>Uç nokta için Microsoft Defender'da olayları araştırma

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


Anızı etkileyen olayları araştıryın, bunların ne anlama gelen olduğunu an olun ve bunları çözmek için kanıtları harmanlar.

Bir olayı incelerken şunları görüyorsunuz:

- Olay ayrıntıları
- Olay yorumları ve eylemleri
- Sekmeler (uyarılar, cihazlar, soruşturmalar, kanıt, grafik)

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4qLUV]

## <a name="analyze-incident-details"></a>Olay ayrıntılarını çözümleme

Olay bölmesini görmek için bir **olayı tıklatın**. Olay **ayrıntılarını ve ilgili bilgileri** (uyarılar, cihazlar, soruşturmalar, kanıt, grafik) görmek için Olay sayfasını aç'ı seçin.

![Olay ayrıntılarının resmi1.](images/atp-incident-details.png)

### <a name="alerts"></a>Uyarılar

Uyarıları inceler ve bir olayda nasıl bağlantılı olduklarını öğrensiniz. Uyarılar, aşağıdaki nedenlere göre olaylarda gruptur:

- Otomatik araştırma - Otomatik araştırma, özgün uyarıyı araştırırken bağlantılı uyarıyı tetikler
- Dosya özellikleri - Uyarıyla ilişkilendirilmiş dosyaların benzer özellikleri vardır
- El ile ilişkilendirme - Bir kullanıcı uyarıları el ile birbirine bağlı
- Proximate time - Uyarılar belirli bir zaman çerçevesi içinde aynı cihazda tetikldi
- Aynı dosya - Uyarıyla ilişkilendirilmiş dosyalar tamamen aynıdır
- Aynı URL - Uyarıyı tetikleyen URL tamamen aynıdır

![Uyarıların o olayda neden birbirine bağlı olduğunu gösteren olay ayrıntıları sayfasının görüntüsü.](images/atp-incidents-alerts-reason.png)

Ayrıca, uyarıyı yönetebilir ve diğer bilgilerle birlikte uyarı meta verilerini de görebilirsiniz. Daha fazla bilgi için bkz [. Uyarıları araştırma](investigate-alerts.md).

### <a name="devices"></a>Cihazlar

Ayrıca, ilgili veya bir olayın parçası olan cihazları da araştırabilirsiniz. Daha fazla bilgi için bkz. [Cihazları araştırma](investigate-machines.md).

![Olay ayrıntıları sayfasında cihazlar sekmesinin resmi.](images/atp-incident-device-tab.png)

### <a name="investigations"></a>İncelemeler

Sistem **tarafından başlatılan** tüm otomatik soruşturmaları olay uyarılarına yanıt olarak görmek için Araştırmalar'ı seçin.

![Olay ayrıntıları sayfasındaki soruşturmalar sekmesinin resmi.](images/atp-incident-investigations-tab.png)

## <a name="going-through-the-evidence"></a>Kanıtın üzerinden geçerek

Uç Nokta için Microsoft Defender, uyarılarda olayların desteklenen tüm olaylarını ve şüpheli varlıklarını otomatik olarak inceler ve önemli dosyalar, işlemler, hizmetler ve daha fazlası hakkında otomatik yanıt ve bilgi sağlar.

Çözümlenen varlıkların her biri virüs bulaştırıldı, düzeltildi veya şüpheli olarak işaretlenir.

![Olay ayrıntıları sayfasındaki kanıt sekmesinin görüntüsü.](images/atp-incident-evidence-tab.png)

## <a name="visualizing-associated-cybersecurity-threats"></a>İlişkili siber güvenlik tehditlerini görselleştirme

Uç Nokta için Microsoft Defender tehdit bilgilerini bir olayla bir araya toplar, böylece çeşitli veri noktalarından gelen desenleri ve korelasyonları görmek için kullanılır. Bu tür bağıntıyı olay grafiği aracılığıyla görüntüabilirsiniz.

### <a name="incident-graph"></a>Olay grafiği

Güvenlik **Graph** siber güvenlik saldırılarının anlat olduğu bir anlatıdır. Örneğin, hangi giriş noktası olduğunu, hangi cihazda güvenliğin veya etkinliğin gözlenen bir göstergesini gösterir. vb.

![Olay grafiğinin resmi.](images/atp-incident-graph-tab.png)

Olay grafiğinde çemberlere tıklayarak kötü amaçlı dosyaların ayrıntılarını, ilişkili dosya algılamalarını, dünya çapında kaç örnek olduğunu, kaç örnek olduğunu, bu durumda kaç örnek olduğunu, kuruluş içinde gözlemlenmiş olup olmadığını görebilirsiniz.

![Olay ayrıntılarının resmi.](images/atp-incident-graph-details.png)

## <a name="related-topics"></a>İlgili konular

- [Olay sırası](/microsoft-365/security/defender-endpoint/view-incidents-queue)
- [Uç nokta için Microsoft Defender'da olayları araştırma](/microsoft-365/security/defender-endpoint/investigate-incidents)
- [Uç nokta olayları için Microsoft Defender'ı yönetme](/microsoft-365/security/defender-endpoint/manage-incidents)
