---
title: Uç nokta için Microsoft Defender'da web tehditlerine yanıt verme
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
ms.openlocfilehash: cefeb36b43b0c59663935b0dd3a0155e80e44f33
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2021
ms.locfileid: "62997609"
---
# <a name="respond-to-web-threats"></a>Web tehditlerine yanıt verme

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Microsoft Defender'ı mı deneyimliysiniz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-main-abovefoldlink&rtc=1)

Uç Nokta için Microsoft Defender'daki Web Koruması, özel gösterge listeniz içinde kötü amaçlı web siteleri ve web siteleri ile ilgili uyarıları etkili bir şekilde incelemenize ve yanıtlamanıza olanak sağlar.

## <a name="view-web-threat-alerts"></a>Web tehdit uyarılarını görüntüleme

Uç Nokta için Microsoft Defender kötü amaçlı [veya şüpheli](manage-alerts.md) web etkinlikleri için aşağıdaki uyarıları üretir:

- **Ağ koruması tarafından engellenen** şüpheli bağlantı: Bu uyarı, özel gösterge listesinde kötü amaçlı bir web sitesine veya web sitesine erişme girişimi engelleme modunda ağ koruması tarafından *durdurulursa* oluşturulur 
- **Ağ koruması tarafından algılanan** şüpheli bağlantı: Bu uyarı, özel gösterge listenizin kötü amaçlı bir web sitesine veya web sitesine erişme girişimi yalnızca denetim modunda ağ koruması tarafından *algılandığında* oluşturulur

Her uyarı aşağıdaki bilgileri sağlar:

- Engellenen web sitesine erişmeye çalışan cihaz
- Web isteğini göndermek için kullanılan uygulama veya program
- Özel gösterge listesinde kötü amaçlı URL veya URL
- Yanıtlayanlar için önerilen eylemler

![Web tehdit korumasıyla ilgili uyarının resmi.](images/wtp-alert.png)

> [!NOTE]
> Uyarıların ses düzeyini azaltmak için, Uç Nokta için Microsoft Defender her gün aynı cihaz üzerinde aynı etki alanı için web tehdit algılamalarını tek bir uyarıda bir araya gösterir. Yalnızca bir uyarı oluşturulur ve [web koruma raporuna sayılır](web-protection-monitoring.md).

## <a name="inspect-website-details"></a>Web sitesi ayrıntılarını denetleme

Uyarıda web sitesinin URL'sini veya etki alanını seçerek daha derine inebilirsiniz. Bu işlem, söz konusu URL veya etki alanı hakkında aşağıdaki çeşitli bilgilerin bulunduğu bir sayfa açar:

- Web sitesine erişmeye çalışan cihazlar
- Web sitesiyle ilgili olaylar ve uyarılar
- Web sitesinin, kurumuz daki olaylarda ne sıklıkta görüldü?

    ![Etki alanı veya URL varlık ayrıntıları sayfasının görüntüsü.](images/wtp-website-details.png)

[URL veya etki alanı varlık sayfaları hakkında daha fazla bilgi](investigate-domain.md)

## <a name="inspect-the-device"></a>Cihazı denetleme

Ayrıca, engellenen bir URL'ye erişmeye çalışan cihazı da kontrol edebilirsiniz. Uyarı sayfasında cihazın adını seçmek, cihazla ilgili kapsamlı bilgilerin yer olduğu bir sayfa açar.

[Cihaz varlık sayfaları hakkında daha fazla bilgi](investigate-machines.md)

## <a name="web-browser-and-windows-notifications-for-end-users"></a>Web tarayıcısı Windows son kullanıcılar için bildirim uygulama

Uç nokta için Microsoft Defender'da web korumasıyla, son kullanıcılarınızı diğer tarayıcılarda veya diğer tarayıcılarda kullanarak kötü amaçlı veya istenmeyen web sitelerini Microsoft Edge engellenebilir. Engelleme ağ koruması tarafından [gerçekleştirili](network-protection.md) olduğundan, web tarayıcısında genel bir hata alırlar. Ayrıca diğer ilgili posta bildirimleri de Windows.

![403 Microsoft Edge hatasını ve hata bildirimini gösteren Windows görüntüsü.](images/wtp-browser-blocking-page.png)
 *Web tehditi iş yer Microsoft Edge*

![Güvenli bir bağlantı uyarısı ve bildirimle ilgili bildirim gösteren Chrome web Windows görüntüsü.](images/wtp-chrome-browser-blocking-page.png)
 *Chrome'da web tehditi engellendi*

## <a name="related-topics"></a>İlgili konular

- [Web korumasına genel bakış](web-protection-overview.md)
- [Web içeriği filtreleme](web-content-filtering.md)
- [Web tehdit koruması](web-threat-protection.md)
- [Web güvenliğini izleme](web-protection-monitoring.md)
