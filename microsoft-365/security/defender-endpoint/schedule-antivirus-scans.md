---
title: Diğer programlarla düzenli hızlı ve tam tarama Microsoft Defender Virüsten Koruma
description: Ne zaman çalıştıracakları ve tam veya hızlı tarama olarak çalıştırıp çalışmamaları da dahil olmak üzere yinelenen (zamanlanmış) taramalar ayarlayın
keywords: hızlı tarama, tam tarama, hızlı vs tam, zamanlama taraması, günlük, haftalık, zaman, zamanlanmış, yinelenen, düzenli
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
ms.openlocfilehash: 96827430b8d2fe1b45b9839ffe87eb5aa5571b93
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63326601"
---
# <a name="configure-scheduled-quick-or-full-microsoft-defender-antivirus-scans"></a>Zamanlanmış hızlı veya tam ekran taramalarını Microsoft Defender Virüsten Koruma yapılandırma

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)

Her zaman açık, gerçek zamanlı koruma ve isteğe bağlı virüsten koruma taramalarına ek olarak, düzenli, zamanlanmış virüsten koruma taramaları da kurabilirsiniz.[](run-scan-microsoft-defender-antivirus.md) Tarama türünü, taramanın ne zaman gerçekleşmesi gerektiğini ve taramanın bir koruma güncelleştirmesi sonrasında mı yoksa uç nokta kullanılmadan [](manage-protection-updates-microsoft-defender-antivirus.md) mı gerçekleşmesi gerektiğini yapılandırabilirsiniz. Ayrıca, gerekirse düzeltme eylemlerini tamamlamak için özel taramalar da kurabilirsiniz.

## <a name="what-do-you-want-to-do"></a>Ne yapmak istiyorsunuz?

- [Hızlı taramalar, tam taramalar ve özel taramalar hakkında bilgi](#quick-scan-full-scan-and-custom-scan)
- [Virüsten koruma taramalarını zaman etmek için Grup İlkesi kullanma](schedule-antivirus-scans-group-policy.md)
- [Virüsten Windows PowerShell taramalarını zamanlamayı kullanmak için virüsten koruma yazılımını kullanma](schedule-antivirus-scans-powershell.md)
- [Virüsten Windows taramalarını zaman etmek için Yönetim Aracı Kullanma](schedule-antivirus-scans-wmi.md)

## <a name="keep-the-following-points-in-mind"></a>Aşağıdaki noktaları unutmayın

- Varsayılan olarak, Microsoft Defender Virüsten Koruma herhangi bir zamanlanmış taramadan 15 dakika önce güncelleştirmeleri denetler. Koruma [güncelleştirmelerinin ne zaman indirilecek ve bu varsayılanı geçersiz kılmak için ne zaman uygulanmalıdır](manage-protection-update-schedule-microsoft-defender-antivirus.md) ? zamanlamayı yönetabilirsiniz.

- Zamanlanmış bir tam tarama sırasında bir cihaz bağlı değil ve pille çalışıyorsa, zamanlanan tarama etkinlik 1002'de durur ve bu da taramanın tamamlanmadan önce durdurulmuş olduğunu haber verir. Microsoft Defender Virüsten Koruma zamanlanmış bir sonraki zaman tam taramayı çalıştıracak.

## <a name="quick-scan-full-scan-and-custom-scan"></a>Hızlı tarama, tam tarama ve özel tarama

Zamanlanmış taramaları ayar hazırlarken, taramanın tam tarama mı yoksa hızlı tarama mı olacağını belirtsiniz. Çoğu durumda, hızlı tarama önerilir.

<br/><br/>

|Hızlı tarama|Tam tarama|Özel tarama|
|---|---|---|
|(Önerilen) Hızlı tarama, kayıt defteri anahtarları ve bilinen başlangıç klasörleri gibi sistemle başlamak üzere kötü amaçlı yazılım kaydedilmiş Windows tüm konumlara göz atıyor. <br/><br/>Her zaman açık, gerçek zamanlı korumayla birlikte, açıldığında ve kapatılan dosyaları gözden birleştiren ve kullanıcı bir klasöre her defa geldiğinde hızlı tarama, sistemle ve çekirdek düzeyinde kötü amaçlı yazılımla başlayan kötü amaçlı yazılımlara karşı güçlü koruma sağlar.<br/><br/>Çoğu durumda, hızlı tarama yeterli olur ve zamanlanmış taramalar için önerilen seçenektir.|Tam tarama, hızlı bir tarama çalıştırarak başlar ve ardından takılan tüm sabit disklerin ve çıkarılabilir/ağ sürücülerinin sıralı dosya tarama işlemiyle devam eder (tam tarama bunu yapacak şekilde yapılandırılmışsa).<br/><br/>Tam taramanın tamamlanması, taranacak verilerin miktarına ve türüne bağlı olarak birkaç saat veya gün sürebilir.<br/><br/>Tam tarama tamamlandığında, yeni güvenlik zekası kullanılabilir ve yeni güvenlik zekası ile başka hiçbir tehdit algılanmaz olduğundan emin olmak için yeni bir tarama gereklidir.<br/><br/>Tam taramaya katılan zaman ve kaynaklar nedeniyle, Microsoft genel olarak tam taramalar zamanlamayı önerilmez.|Özel tarama, belirttiğiniz dosya ve klasörlerde çalışır. Örneğin, bir USB sürücüsüne veya cihazınızın yerel sürücüsüne belirli bir klasörü taramayı seçebilirsiniz.|

> [!NOTE]
> Varsayılan olarak, hızlı taramalar USB sürücüler gibi çıkarılabilir cihazlarda çalışır.

## <a name="how-do-i-know-which-scan-type-to-choose"></a>Hangi tarama türünü seç olduğumu nasıl bilim?

Tarama türünü seçmek için aşağıdaki tabloyu kullanın.
<br/><br/>

|Senaryo|Önerilen tarama türü|
|---|---|
|Düzenli, zamanlanmış taramalar ayarlamak istiyor|Hızlı tarama <p> Hızlı tarama işlemi, cihazla ilgili süreçleri, belleği, profilleri ve belirli konumları denetler. Hızlı tarama, [her zaman gerçek zamanlı](configure-real-time-protection-microsoft-defender-antivirus.md) korumayla birlikte hem sistemle başlayan kötü amaçlı yazılım hem de çekirdek düzeyinde kötü amaçlı yazılım için güçlü kapsam sağlar. Gerçek zamanlı koruma, açıldığında ve kapatılan dosyaları ve kullanıcı klasöre her geldiğinde gözden kullanır.|
|Kötü amaçlı yazılım gibi tehditler tek bir cihazda algılanır|Hızlı tarama <p> Çoğu durumda, hızlı taramalar algılanan kötü amaçlı yazılımları yakalar ve temizler.|
|Bir isteğe bağlı [tarama çalıştırmak istiyor](run-scan-microsoft-defender-antivirus.md)|Hızlı tarama|
|USB sürücüsü gibi taşınabilir bir cihazın kötü amaçlı yazılım içermeyer|Özel tarama <p> Özel tarama belirli konumları, klasörleri veya dosyaları seçmenize olanak sağlar ve hızlı bir tarama çalıştırır.|

## <a name="what-else-do-i-need-to-know-about-quick-and-full-scans"></a>Hızlı ve tam taramalar hakkında başka neleri bileceğim?

- Kötü amaçlı dosyalar hızlı taramaya dahil edilen konumlarda depolanıyor olabilir. Bununla birlikte, her zaman açık olan gerçek zamanlı koruma, açılan ve kapatılan tüm dosyaları ve kullanıcı tarafından erişilen klasörlerde yer alan tüm dosyaları gözden kullanır. Gerçek zamanlı koruma ve hızlı tarama birlikte kötü amaçlı yazılıma karşı güçlü koruma sağlar.

- Buluta teslim [edilen korumayla](cloud-protection-microsoft-defender-antivirus.md) erişime koruma, sistemde erişilen tüm dosyaların en son güvenlik zekası ve bulut makinesi öğrenme modelleriyle taranmakta olduğundan emin olmaya yardımcı olur.

- Gerçek zamanlı koruma kötü amaçlı yazılım algılasa ve etkilenen dosyaların kapsamı başlangıçta belirlenene kadar, Microsoft Defender Virüsten Koruma düzeltme işleminin bir parçası olarak tam tarama başlatılır.

- Tam tarama, diğer taramalar tarafından algılanmadı olarak algılanan hızlı tarama gibi kötü amaçlı dosyaları algılanabilir. Ancak, tam tarama biraz zaman alıp tamamlanacak değerli sistem kaynaklarını kullanabilir.

- Bir cihaz uzun süre çevrimdışı durumdaysa, tam taramanın tamamlanması daha uzun sürebilir.
