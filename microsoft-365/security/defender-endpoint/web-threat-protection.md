---
title: Organizasyonlarınızı web tehditlerine karşı koruma
description: Uç Nokta için Microsoft Defender'da web korumasını ve organizasyonlarınızı nasıl koruy koruyacı olduğunu öğrenin.
keywords: web koruması, web tehdit koruması, web'e gözatma, güvenlik, kimlik avı, kötü amaçlı yazılım, açıkları kullanma, web siteleri, ağ koruması, Edge, Internet Explorer, Chrome, Firefox, web tarayıcısı
search.appverid: met150
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
ms.openlocfilehash: 398fdb8bbfb5bba59fce83e24e7d6cdd496e90bd
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2021
ms.locfileid: "62997554"
---
# <a name="protect-your-organization-against-web-threats"></a>Organizasyonlarınızı web tehditlerine karşı koruma

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Microsoft Defender'ı mı deneyimliysiniz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-main-abovefoldlink&rtc=1)

Web tehdit koruması, Uç nokta için [Defender'daki Web](web-protection-overview.md) korumasının bir bölümüdur. Cihazlarınızı [web tehditlerine](network-protection.md) karşı korumak için ağ koruması kullanır. Microsoft Edge Chrome ve Firefox gibi popüler üçüncü taraf tarayıcılarla tümleştirerek, web tehdit koruması web ara sunucusu olmadan web tehditlerini durdurur ve cihazları uzakta ya da şirket içindeyken koruyabilir. Web tehdit koruması kimlik avı sitelerine, kötü amaçlı yazılım vektörlerine, açıklarından yararlanan sitelere, güvenilmeyen veya düşük itibarlı sitelere ve özel gösterge listesinde engellemiş olduğunuz sitelere erişimi [durdurur](manage-indicators.md).

> [!NOTE]
> Cihazların yeni özel göstergeler edinsi bir saat kadar zaman alabiliyor.

## <a name="prerequisites"></a>Önkoşullar

Web koruması, web tarayıcıları ve üçüncü taraf web tarayıcılarda web Microsoft Edge göz atma güvenliği sağlamak için ağ koruması kullanır.

Cihazlarınız üzerinde ağ korumasını açmak için:

- Ağ korumasını dağıtmadan veya yeniden dağıtmadan **önce etkinleştirmek için, Web &** Ağ Koruması altında Uç nokta güvenlik temeli için Defender'ı düzenleyin. [Uç nokta güvenlik temeli için Defender'ı gözden geçirme ve atama hakkında bilgi](configure-machines-security-baseline.md#review-and-assign-the-microsoft-defender-for-endpoint-security-baseline)
- Intune cihaz yapılandırmasını, SCCM'i, Grup İlkesi'i veya MDM çözümlerinizi kullanarak ağ korumasını açın. [Ağ korumasını etkinleştirme hakkında daha fazla bilgi](enable-network-protection.md)

> [!NOTE]
> Ağ korumasını Yalnızca denetim olarak **ayarsanız** engelleme kullanılamaz. Ayrıca, yalnızca web sitelerinden kötü amaçlı ve istenmeyen web sitelerine erişim denemelerini algılanabilir Microsoft Edge.

## <a name="configure-web-threat-protection"></a>Web tehdit korumasını yapılandırma

Aşağıdaki yordamda, bu yönetim merkezinde web tehdit korumasının nasıl yapılandır Microsoft Endpoint Manager açık almaktadır.

1. Yönetim merkezine Microsoft Endpoint Manager ()[https://endpoint.microsoft.com](https://endpoint.microsoft.com) ve oturum açma.
 
2. Uç **nokta güvenliği Saldırı** \> **yüzeyini azaltma'ya ve** ardından + İlke **oluştur'a seçin**.

3. Web koruma profili ve daha **Windows 10 bir** platform seçin, **ardından** Oluştur'a **tıklayın**. 

4. Temel **Bilgiler sekmesinde** bir ad ve açıklama belirtin ve ardından Sonraki'yi **seçin**.

5. Yapılandırma ayarları **sekmesinde Web** **Koruması'nın kapsamını genişletin**, ayarlarınızı belirtin ve ardından Sonraki'yi **seçin**.

   - Web **korumasının açık olduğu** **Ağ korumasını** etkinleştir ayarını Etkin olarak ayarlayın. Alternatif olarak, ortamınıza nasıl **çalışacaklarını görmek için** ağ korumasını Denetim moduna da kurabilirsiniz. Denetim modunda ağ koruması kullanıcıların siteleri veya etki alanlarını ziyaretsini engellemez, ancak algılamaları olay olarak izlemez. 
   - Kullanıcıları olası kimlik avı dolandırıcılığı ve kötü amaçlı yazılımlardan korumak için, Kimlik avı **dolandırıcılığı için SmartScreen Microsoft Edge'in eski sürümü'i Evet'e** **döndürebilirsiniz**.
   - Kullanıcıların kötü amaçlı olabilecek siteler hakkında uyarıları atlamalarını önlemek için Kötü amaçlı **site erişimini engelle'ye Evet** **ayarlayın**.
   - Kullanıcıların uyarıları atlayarak ve doğrulanmamış dosyaları indirmesini önlemek için Doğrulanmamış dosya indirmesini engelle **tl Evet'i** **ayarlayın**. 

6. Kapsam etiketleri **sekmesinde,** organizasyonunız kapsam etiketleri kullanıyorsa, **+ Kapsam etiketlerini seç'i ve sonra** da Sonraki'yi **seçin**. (Kapsam etiketlerini kullan değilken Sonraki'yi **seçin**.) Kapsam etiketleri hakkında daha fazla bilgi edinmek için bkz. Dağıtılmış IT için rol tabanlı erişim [denetimi (RBAC) ve kapsam etiketlerini kullanma](/mem/intune/fundamentals/scope-tags).

7. Ödevler **sekmesinde** , web koruma ilkesi alacak kullanıcıları ve cihazları belirtin ve ardından Sonraki'yi **seçin**.

8. Gözden Geçir **+ oluştur sekmesinde** , ilke ayarlarınızı gözden geçirin ve sonra Oluştur'a **tıklayın**.

## <a name="related-topics"></a>İlgili konular

- [Web korumasına genel bakış](web-protection-overview.md)
- [Web tehdit koruması](web-threat-protection.md)
- [Web güvenliğini izleme](web-protection-monitoring.md)
- [Web tehditlerine yanıt verme](web-protection-response.md)
- [Ağ koruması](network-protection.md)
