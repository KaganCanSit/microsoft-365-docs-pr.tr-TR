---
title: Web tehditlerine Uç Nokta için Microsoft Defender
description: Kötü amaçlı ve istenmeyen web sitelerle ilgili uyarılara yanıt verin. Web tehdit korumasının son kullanıcıları web tarayıcıları ve bildirimlerini kullanarak nasıl Windows anlama
keywords: web koruması, web tehdit koruması, web'e gözatma, uyarılar, yanıt, güvenlik, kimlik avı, kötü amaçlı yazılım, exploit, web siteleri, ağ koruması, Edge, Internet Explorer, Chrome, Firefox, web tarayıcısı, bildirimler, son kullanıcılar, Windows bildirimleri, engelleme sayfası,
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 3a7202c6e522441ecbbfd738d3533a242c966f8c
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64467543"
---
# <a name="respond-to-web-threats"></a>Web tehditlerine yanıt verme

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta için Microsoft Defender Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta için Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Bu deneyimi Uç Nokta için Microsoft Defender? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-main-abovefoldlink&rtc=1)

Web koruma Uç Nokta için Microsoft Defender, özel gösterge listeniz içinde kötü amaçlı web siteleri ve web siteleri ile ilgili uyarıları etkili bir şekilde araştırmanıza ve yanıtlamanıza olanak sağlar.

## <a name="view-web-threat-alerts"></a>Web tehdit uyarılarını görüntüleme

Uç Nokta için Microsoft Defender kötü amaçlı veya [şüpheli web etkinlikleri](manage-alerts.md) için aşağıdaki uyarıları üretir:

- **Ağ koruması tarafından engellenen** şüpheli bağlantı: Bu uyarı, özel gösterge listesinde kötü amaçlı bir web sitesine veya web sitesine erişme girişimi engelleme modunda ağ koruması tarafından *durdurulursa* oluşturulur 
- **Ağ koruması tarafından algılanan** şüpheli bağlantı: Bu uyarı, özel gösterge listenizin kötü amaçlı bir web sitesine veya web sitesine erişme girişimi yalnızca denetim modunda ağ koruması tarafından *algılandığında* oluşturulur

Her uyarı aşağıdaki bilgileri sağlar:

- Engellenen web sitesine erişmeye çalışan cihaz
- Web isteğini göndermek için kullanılan uygulama veya program
- Özel gösterge listesinde kötü amaçlı URL veya URL
- Yanıtlayanlar için önerilen eylemler

:::image type="content" source="images/wtp-alert.png" alt-text="Web tehdit korumasıyla ilgili uyarı" lightbox="images/wtp-alert.png":::

> [!NOTE]
> Uyarıların ses düzeyini azaltmak için, Uç Nokta için Microsoft Defender her gün aynı cihaz üzerinde aynı etki alanı için web tehdit algılamalarını tek bir uyarıda birleştirilmiştir. Yalnızca bir uyarı oluşturulur ve [web koruma raporuna sayılır](web-protection-monitoring.md).

## <a name="inspect-website-details"></a>Web sitesi ayrıntılarını denetleme

Uyarıda web sitesinin URL'sini veya etki alanını seçerek daha derine inebilirsiniz. Bu işlem, söz konusu URL veya etki alanı hakkında aşağıdaki çeşitli bilgilerin bulunduğu bir sayfa açar:

- Web sitesine erişmeye çalışan cihazlar
- Web sitesiyle ilgili olaylar ve uyarılar
- Web sitesinin, kurumuz daki olaylarda ne sıklıkta görüldü?

  :::image type="content" source="images/wtp-website-details.png" alt-text="Etki alanı veya URL varlık ayrıntıları sayfası" lightbox="images/wtp-website-details.png":::

[URL veya etki alanı varlık sayfaları hakkında daha fazla bilgi](investigate-domain.md)

## <a name="inspect-the-device"></a>Cihazı denetleme

Ayrıca, engellenen bir URL'ye erişmeye çalışan cihazı da kontrol edebilirsiniz. Uyarı sayfasında cihazın adını seçmek, cihazla ilgili kapsamlı bilgilerin yer olduğu bir sayfa açar.

[Cihaz varlık sayfaları hakkında daha fazla bilgi](investigate-machines.md)

## <a name="web-browser-and-windows-notifications-for-end-users"></a>Web tarayıcısı Windows son kullanıcılar için bildirim uygulama

Uç Nokta için Microsoft Defender'de web korumasıyla, son kullanıcılarınızı diğer tarayıcılarda veya diğer tarayıcılarda kullanarak kötü amaçlı veya istenmeyen web sitelerini Microsoft Edge engellenebilir. Engelleme ağ koruması tarafından [gerçekleştirili](network-protection.md) olduğundan, web tarayıcısında genel bir hata alırlar. Ayrıca diğer ilgili posta bildirimleri de Windows.

:::image type="content" source="images/wtp-browser-blocking-page.png" alt-text="Bu Microsoft Edge 403 hatasını ve hata Windows gösterir" lightbox="images/wtp-browser-blocking-page.png":::

*Web tehditi iş yer Microsoft Edge*

:::image type="content" source="images/wtp-chrome-browser-blocking-page.png" alt-text="Güvenli bağlantı uyarısı ve bildirim Windows Chrome web tarayıcısı" lightbox="images/wtp-chrome-browser-blocking-page.png":::
*Chrome'da web tehditi engellendi*

## <a name="related-topics"></a>İlgili konular

- [Web korumasına genel bakış](web-protection-overview.md)
- [Web içeriği filtreleme](web-content-filtering.md)
- [Web tehdit koruması](web-threat-protection.md)
- [Web güvenliğini izleme](web-protection-monitoring.md)
