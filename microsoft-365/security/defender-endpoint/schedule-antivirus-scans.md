---
title: Microsoft Defender Virüsten Koruma ile düzenli hızlı ve tam taramalar zamanlama
description: Ne zaman çalıştırılmaları gerektiği ve tam veya hızlı tarama olarak çalıştırılıp çalıştırılmadıkları da dahil olmak üzere yinelenen (zamanlanmış) taramalar ayarlama
keywords: hızlı tarama, tam tarama, hızlı ve tam, tarama zamanlama, günlük, haftalık, zaman, zamanlanmış, yinelenen, düzenli
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 02/22/2022
ms.reviewer: pauhijbr, ksarens, mkaminska
manager: dansimp
ms.technology: mde
ms.topic: how-to
ms.collection: M365-security-compliance
ms.openlocfilehash: c0dac136b740ba9ff1ddccb5b121a2e2abb2334b
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2022
ms.locfileid: "65419626"
---
# <a name="configure-scheduled-quick-or-full-microsoft-defender-antivirus-scans"></a>Zamanlanmış hızlı veya tam Microsoft Defender Virüsten Koruma taramalarını yapılandırma

**Şunlar için geçerlidir:**
- [Uç Nokta için Microsoft Defender Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- Microsoft Defender Virüsten Koruma

**Platform**
- Windows

Her zaman açık, gerçek zamanlı koruma ve [isteğe bağlı virüsten koruma](run-scan-microsoft-defender-antivirus.md) taramalarına ek olarak, düzenli, zamanlanmış virüsten koruma taramaları da ayarlayabilirsiniz. Taramanın türünü, taramanın ne zaman gerçekleşebileceğini ve taramanın [bir koruma güncelleştirmesinin](manage-protection-updates-microsoft-defender-antivirus.md) ardından mı yoksa uç nokta kullanılmadığında mı gerçekleşip gerçekleşmeyeceğini yapılandırabilirsiniz. Gerekirse düzeltme eylemlerini tamamlamak için özel taramalar da ayarlayabilirsiniz.

## <a name="what-do-you-want-to-do"></a>Ne yapmak istiyorsunuz?

- [Hızlı taramalar, tam taramalar ve özel taramalar hakkında bilgi edinin](#quick-scan-full-scan-and-custom-scan)
- [Virüsten koruma taramaları zamanlamak için grup ilkesi kullanma](schedule-antivirus-scans-group-policy.md)
- [Virüsten koruma taramaları zamanlamak için Windows PowerShell kullanma](schedule-antivirus-scans-powershell.md)
- [Virüsten koruma taramaları zamanlamak için Windows Yönetim Araçları'nı kullanma](schedule-antivirus-scans-wmi.md)

## <a name="keep-the-following-points-in-mind"></a>Aşağıdaki noktaları göz önünde bulundurun

- Varsayılan olarak, Microsoft Defender Virüsten Koruma zamanlanmış taramaların zamanından 15 dakika önce bir güncelleştirme olup olmadığını denetler. [Bu varsayılanı geçersiz kılmak için koruma güncelleştirmelerinin ne zaman indirileceği ve uygulanacağı zaman çizelgesini yönetebilirsiniz](manage-protection-update-schedule-microsoft-defender-antivirus.md).

- Bir cihazın fişi takılı değilse ve zamanlanmış bir tam tarama sırasında pille çalışıyorsa, zamanlanan tarama 1002 olayıyla durdurulur ve tarama tamamlanmadan önce durdurulur. Microsoft Defender Virüsten Koruma, bir sonraki zamanlanan saatte tam tarama çalıştırır.

## <a name="quick-scan-full-scan-and-custom-scan"></a>Hızlı tarama, tam tarama ve özel tarama

Zamanlanmış taramaları ayarlarken, taramanın tam tarama mı yoksa hızlı tarama mı olacağını belirtebilirsiniz. Çoğu durumda hızlı tarama önerilir.

<br/><br/>

|Hızlı tarama|Tam tarama|Özel tarama|
|---|---|---|
|(Önerilen) Hızlı tarama, kayıt defteri anahtarları ve bilinen Windows başlangıç klasörleri gibi sistemle başlamak için kötü amaçlı yazılımların kaydedilebileceği tüm konumları gözden geçirin. <br/><br/>Her zaman açık, gerçek zamanlı koruma ile birlikte, dosyalar açıldığında ve kapatıldığında incelenir ve bir kullanıcı bir klasöre her gittiği zaman hızlı tarama, sistem ve çekirdek düzeyinde kötü amaçlı yazılımlarla başlayan kötü amaçlı yazılımlara karşı güçlü koruma sağlamaya yardımcı olur.<br/><br/>Çoğu durumda hızlı tarama yeterlidir ve zamanlanmış taramalar için önerilen seçenektir.|Tam tarama, hızlı bir tarama çalıştırarak başlar ve ardından tüm bağlı sabit disklerin ve çıkarılabilir/ağ sürücülerinin sıralı dosya taramasıyla devam eder (tam tarama bunu yapacak şekilde yapılandırılmışsa).<br/><br/>Taranması gereken verilerin miktarına ve türüne bağlı olarak tam taramanın tamamlanması birkaç saat veya gün sürebilir.<br/><br/>Tam tarama tamamlandığında, yeni güvenlik bilgileri kullanılabilir ve yeni güvenlik bilgileriyle başka bir tehdit algılandığından emin olmak için yeni bir tarama gerekir.<br/><br/>Tam taramada yer alan zaman ve kaynaklar nedeniyle, Genel olarak Microsoft tam taramaların zamanlamasını önermez.|Özel tarama, belirttiğiniz dosya ve klasörlerde çalışır. Örneğin, bir USB sürücüsünü veya cihazınızın yerel sürücüsündeki belirli bir klasörü taramayı seçebilirsiniz.|

> [!NOTE]
> Varsayılan olarak, hızlı taramalar USB sürücüleri gibi takılı çıkarılabilir cihazlarda çalışır.

## <a name="how-do-i-know-which-scan-type-to-choose"></a>Hangi tarama türünü seçeceğinizi Nasıl yaparım? biliyor musunuz?

Bir tarama türü seçmek için aşağıdaki tabloyu kullanın.
<br/><br/>

|Senaryo|Önerilen tarama türü|
|---|---|
|Düzenli, zamanlanmış taramalar ayarlamak istiyorsunuz|Hızlı tarama <p> Hızlı tarama işlemi, belleği, profilleri ve cihazdaki belirli konumları denetler. [Her zaman açık gerçek zamanlı koruma](configure-real-time-protection-microsoft-defender-antivirus.md) ile birlikte, hızlı tarama hem sistemle başlayan kötü amaçlı yazılımlarda hem de çekirdek düzeyinde kötü amaçlı yazılımlarda güçlü bir kapsama sağlamaya yardımcı olur. Gerçek zamanlı koruma, dosyalar açıldığında ve kapatıldığında ve bir kullanıcı bir klasöre gittiği zaman dosyaları inceler.|
|Kötü amaçlı yazılım gibi tehditler tek bir cihazda algılanıyor|Hızlı tarama <p> Çoğu durumda, hızlı tarama algılanan kötü amaçlı yazılımları yakalar ve temizler.|
|[İsteğe bağlı tarama](run-scan-microsoft-defender-antivirus.md) çalıştırmak istiyorsunuz|Hızlı tarama|
|USB sürücüsü gibi taşınabilir bir cihazın kötü amaçlı yazılım içermediğinden emin olmak istiyorsunuz|Özel tarama <p> Özel tarama, belirli konumları, klasörleri veya dosyaları seçmenizi ve hızlı bir tarama çalıştırmanızı sağlar.|

## <a name="what-else-do-i-need-to-know-about-quick-and-full-scans"></a>Hızlı ve tam taramalar hakkında başka ne bilmem gerekiyor?

- Kötü amaçlı dosyalar, hızlı taramaya dahil olmayan konumlarda depolanabilir. Ancak, her zaman açık gerçek zamanlı koruma, açılan ve kapatılan tüm dosyaları ve bir kullanıcı tarafından erişilen klasörlerdeki tüm dosyaları gözden geçirin. Gerçek zamanlı koruma ve hızlı taramanın birleşimi, kötü amaçlı yazılımlara karşı güçlü koruma sağlamaya yardımcı olur.

- [Bulut tabanlı koruma](cloud-protection-microsoft-defender-antivirus.md) ile erişim üzerinde koruma, sistemde erişilen tüm dosyaların en son güvenlik bilgileri ve bulut makine öğrenmesi modelleriyle taranmasını sağlamaya yardımcı olur.

- Gerçek zamanlı koruma kötü amaçlı yazılım algıladığında ve etkilenen dosyaların kapsamı başlangıçta belirlenmediğinde, Microsoft Defender Virüsten Koruma düzeltme işleminin bir parçası olarak tam tarama başlatır.

- Tam tarama, hızlı tarama gibi diğer taramalar tarafından algılanmayan kötü amaçlı dosyaları algılayabilir. Ancak, tam tarama biraz zaman alabilir ve tamamlamak için değerli sistem kaynaklarını kullanabilir.

- Bir cihaz uzun süre çevrimdışı kalırsa, tam taramanın tamamlanması daha uzun sürebilir.

> [!TIP]
> Diğer platformlar için Virüsten Koruma ile ilgili bilgileri arıyorsanız bkz:
> - [MacOS'ta Uç Nokta için Microsoft Defender tercihlerini ayarlayın](mac-preferences.md)
> - [Mac'te Uç Nokta için Microsoft Defender](microsoft-defender-endpoint-mac.md)
> - [Intune için Microsoft Defender için macOS Virüsten Koruma ilke ayarları](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Linux'ta Uç Nokta için Microsoft Defender tercihlerini ayarlayın](linux-preferences.md)
> - [Linux'ta Uç Nokta için Microsoft Defender](microsoft-defender-endpoint-linux.md)
> - [Android özelliklerinde Uç Nokta için Defender’ı yapılandırın](android-configure.md)
> - [iOS özelliklerinde Uç Nokta için Microsoft Defender’ı yapılandırın](ios-configure-features.md)