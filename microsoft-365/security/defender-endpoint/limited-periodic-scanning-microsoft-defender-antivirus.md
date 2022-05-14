---
title: Sınırlı düzenli Microsoft Defender Virüsten Koruma tarama özelliğini etkinleştirme
description: Sınırlı düzenli tarama, diğer yüklü AV sağlayıcılarınıza ek olarak Microsoft Defender Virüsten Koruma kullanmanızı sağlar
keywords: lps, sınırlı, periyodik, tarama, tarama, uyumluluk, 3. taraf, diğer av, devre dışı
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
ms.topic: article
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 10/18/2018
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.collection: m365-security-compliance
ms.openlocfilehash: 2b9320c5d7086d41be363fd01b786c98ffbc52d5
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2022
ms.locfileid: "65417918"
---
# <a name="use-limited-periodic-scanning-in-microsoft-defender-antivirus"></a>Microsoft Defender Virüsten Koruma’da sınırlı düzenli taramayı kullanın 

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Şunlar için geçerlidir:**

- [Uç Nokta için Microsoft Defender Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Microsoft Defender Virüsten Koruma

**Platform**
- Windows

Sınırlı düzenli tarama, bir Windows 10 veya Windows 11 cihaza başka bir virüsten koruma ürünü yüklediğinizde etkinleştirilebilen özel bir tehdit algılama ve düzeltme türüdür.

Yalnızca belirli durumlarda etkinleştirilebilir. Sınırlı düzenli tarama ve Microsoft Defender Virüsten Koruma diğer virüsten koruma ürünleriyle nasıl çalıştığı hakkında daha fazla bilgi için bkz. [uyumluluk Microsoft Defender Virüsten Koruma](microsoft-defender-antivirus-compatibility.md).

**Microsoft bu özelliğin kurumsal ortamlarda kullanılmasını önermez. Bu, öncelikli olarak tüketicilere yönelik bir özelliktir.** Bu özellik, kötü amaçlı yazılımları algılamak için yalnızca Microsoft Defender Virüsten Koruma özelliklerinin sınırlı bir alt kümesini kullanır ve çoğu kötü amaçlı yazılımı ve istenmeyebilecek yazılımları algılayamaz. Ayrıca, yönetim ve raporlama özellikleri sınırlı olacaktır. Microsoft, kuruluşların birincil virüsten koruma çözümünü seçmelerini ve özel olarak kullanmasını önerir.

## <a name="how-to-enable-limited-periodic-scanning"></a>Sınırlı düzenli taramayı etkinleştirme

Varsayılan olarak, başka bir virüsten koruma ürünü yüklü değilse veya diğer ürün güncel değilse, süresi dolmuşsa veya düzgün çalışmıyorsa Microsoft Defender Virüsten Koruma bir Windows 10 veya Windows 11 cihazında kendisini etkinleştirir.

Microsoft Defender Virüsten Koruma etkinleştirilirse, söz konusu cihazda yapılandırmak için her zamanki seçenekler görünür:

:::image type="content" source="images/vtp-wdav.png" alt-text="Tarama seçenekleri, ayarlar ve güncelleştirme seçenekleri de dahil olmak üzere Microsoft Defender AV seçeneklerini gösteren Windows Güvenliği uygulaması" lightbox="images/vtp-wdav.png":::

Başka bir virüsten koruma ürünü yüklüyse ve düzgün çalışıyorsa, Microsoft Defender Virüsten Koruma kendisini devre dışı bırakır. Windows Güvenliği uygulaması **Virüs & tehdit koruması** bölümünü AV ürünüyle ilgili durumu gösterecek şekilde değiştirecek ve ürünün yapılandırma seçeneklerine bir bağlantı sağlayacaktır.

Herhangi bir üçüncü taraf AV ürününün altında **, Microsoft Defender Virüsten Koruma seçenekleri** olarak yeni bir bağlantı görünür. Bu bağlantıya tıklanması, sınırlı düzenli taramayı etkinleştiren iki durumlu düğmeyi göstermek için genişler. Sınırlı düzenli seçeneğin düzenli taramayı etkinleştirmek veya devre dışı bırakmak için kullanabileceğiniz bir geçiş noktası olduğunu unutmayın. 

Anahtarı **Açık** olarak kaydırarak üçüncü taraf AV ürününün altında standart Microsoft Defender AV seçenekleri gösterilir. Sınırlı düzenli tarama seçeneği sayfanın en altında görünür.

## <a name="related-articles"></a>İlgili makaleler

- [Davranışsal, buluşsal ve gerçek zamanlı korumayı yapılandırın](configure-protection-features-microsoft-defender-antivirus.md)
- [Windows 10'da Microsoft Defender Virüsten Koruma](microsoft-defender-antivirus-in-windows-10.md)

> [!TIP]
> Diğer platformlar için Virüsten Koruma ile ilgili bilgileri arıyorsanız bkz:
> - [MacOS'ta Uç Nokta için Microsoft Defender tercihlerini ayarlayın](mac-preferences.md)
> - [Mac'te Uç Nokta için Microsoft Defender](microsoft-defender-endpoint-mac.md)
> - [Intune için Microsoft Defender için macOS Virüsten Koruma ilke ayarları](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Linux'ta Uç Nokta için Microsoft Defender tercihlerini ayarlayın](linux-preferences.md)
> - [Linux'ta Uç Nokta için Microsoft Defender](microsoft-defender-endpoint-linux.md)
> - [Android özelliklerinde Uç Nokta için Defender’ı yapılandırın](android-configure.md)
> - [iOS özelliklerinde Uç Nokta için Microsoft Defender’ı yapılandırın](ios-configure-features.md)