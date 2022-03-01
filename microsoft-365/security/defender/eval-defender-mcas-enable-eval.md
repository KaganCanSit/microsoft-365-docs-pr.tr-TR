---
title: Bulut Uygulamaları için Microsoft Defender değerlendirme ortamını etkinleştirme
description: Daha fazla bilgi edinmek ve satın alan ürünler arasındaki etkileşimleri anlamak Office 365 için Microsoft Defender'da Bulut Uygulamaları için Defender Microsoft 365 Defender öğrenin.
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: bcarter
author: brendacarter
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-scenario
- m365solution-evalutatemtp
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: 4c8f0ff2ca13d7f1c0e8adfcf4e0bdf09aa1c2ac
ms.sourcegitcommit: 6f3bc00a5cf25c48c61eb3835ac069e9f41dc4db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2022
ms.locfileid: "63014191"
---
# <a name="enable-the-evaluation-environment-for-microsoft-defender-for-cloud-apps"></a>Bulut Uygulamaları için Microsoft Defender değerlendirme ortamını etkinleştirme

**Aşağıdakiler için geçerlidir:**

- Microsoft 365 Defender

Bu makale, [Bulut Uygulamaları için](eval-defender-mcas-overview.md) Microsoft Defender değerlendirme ortamını ayarlama işleminin 2. adımıdır. Bu işlem hakkında daha fazla bilgi için genel bakış [makalesine bakın](eval-defender-mcas-overview.md).

Bu makale, Bulut Uygulamaları için Defender portalına erişme ve bulut uygulaması trafik verilerini toplamak için gerekli tümleştirmeyi yapılandırma sürecinde size yol sunar.

Ortamınıza kullanılan bulut uygulamalarını keşfetmek için, aşağıdakilerin birini veya her ikisini de yapabilirsiniz:

- Uç Nokta için Microsoft Defender ile tümleştirerek Bulut Bulma ile hızla hareket edin. Bu yerel tümleştirme, ağ üzerinde ve 11 cihaz genelinde bulut trafiği Windows 10 Windows veri toplamaya başlamanıza olanak tanır.
- Ağınıza bağlı tüm cihazlardan erişilen tüm bulut uygulamalarını bulmak için güvenlik duvarlarınız ve diğer yardımcı sunucularda Bulut Uygulamaları için Defender günlük toplayıcısı dağıtın. Bu işlem uç noktalarından verileri toplar ve çözümleme için Bulut Uygulamaları için Defender'a gönderir. Bulut Uygulamaları için Defender, daha fazla özellik için bazı üçüncü taraf taraflarla yerel olarak tümleştirilmiştir.

Bu makalede her iki yönteme de yönelik kılavuz bilgiler yer almaktadır.

Bulut Uygulamaları için Microsoft Defender'ı ayarlamak için aşağıdaki adımları kullanın.

![Microsoft Defender değerlendirme ortamında Bulut Uygulamaları için Microsoft Defender'ı etkinleştirme adımları.](../../media/defender/m365-defender-mcas-eval-enable-steps.png)

- [1. Adım. Bağlan için Defender portalına giriş](#step-1)
- [2. Adım. Uç Nokta için Microsoft Defender ile Tümleştir](#step-2)
- [3. Adım. Güvenlik duvarlarınız ve diğer yardımcı sunucularda Bulut Uygulamaları için Defender günlük toplayıcıyı dağıtma](#step-3)
- [Adım 4. Bulutta hangi uygulamaların kullanılıyor olduğunu görmek için Bulut Keşif panosuna bakın](#step-4)

<a name="step-1"></a>

## <a name="step-1-connect-to-the-defender-for-cloud-apps-portal"></a>Adım 1. Bağlan için Defender portalına giriş

Lisansı doğrulamak ve Bulut Uygulamaları için Defender portalına bağlanmak için bkz. [Hızlı Başlangıç: Bulut Uygulamaları için Microsoft Defender'ı kullanma](/cloud-app-security/getting-started-with-cloud-app-security).

Portala hemen bağlanamıyorsanız IP adresini güvenlik duvarının izin listesine eklemeniz gerekebilir. Bkz [. Bulut Uygulamaları için Defender'ın temel kurulumu](/cloud-app-security/general-setup).

Hala sorun yaşıyorsanız Ağ gereksinimlerini [gözden geçirin](/cloud-app-security/network-requirements).

<a name="step-2"></a>

## <a name="step-2-integrate-with-microsoft-defender-for-endpoint"></a>Adım 2. Uç Nokta için Microsoft Defender ile Tümleştir

Bulut Uygulamaları için Microsoft Defender yerel olarak Uç Nokta için Microsoft Defender ile tümleştirilmiştir. Tümleştirme, Bulut Keşif'in daha kolay kullanılabilir olması için, Bulut Keşif özelliklerini şirket ağınız dışında da genişletiyor ve cihaz tabanlı soruşturmaya olanakıyor. Bu tümleştirme, bulut uygulamalarına ve hizmetlere IT tarafından yönetilen Windows 10 11 Windows erişilebilenleri ortaya çıkar.

Uç Nokta için Microsoft Defender'ı daha önce kurdıysanız, Bulut Uygulamaları için Defender ile tümleştirmeyi yapılandırma, gelişmiş Microsoft 365 Defender. Tümleştirme açıkken, Bulut Uygulamaları için Defender portalına geri dönebilirsiniz ve zengin verileri Bulut Bulma Panosu'nda görüntüleyebilirsiniz.

Bu görevleri gerçekleştirmek için bkz. [Bulut Uygulamaları için Microsoft Defender ile Uç Nokta Tümleştirmesi için Microsoft Defender](/cloud-app-security/mde-integration).

<a name="step-3"></a>

## <a name="step-3-deploy-the-defender-for-cloud-apps-log-collector-on-your-firewalls-and-other-proxies"></a>Adım 3. Güvenlik duvarlarınız ve diğer yardımcı sunucularda Bulut Uygulamaları için Defender günlük toplayıcıyı dağıtma

Ağınıza bağlı tüm cihazlarda kapsam için, güvenlik duvarlarınız ve diğer aracılarda Bulut Uygulamaları için Defender günlük toplayıcısı'nı dağıtarak uç noktalardan veri toplayın ve analiz için Bulut Uygulamaları için Defender'a gönderin.

Aşağıdaki Güvenli Web Ağ Geçidi'ni (SWG) kullanıyorsanız Bulut Uygulamaları için Defender sorunsuz dağıtım ve tümleştirme sağlar:

- Zscaler
- iboss
- Corrata
- Menlo Security

Bu ağ cihazlarıyla tümleştirme hakkında daha fazla bilgi için bkz. [Bulut Keşif'i ayarlama](/cloud-app-security/set-up-cloud-discovery).

<a name="step-4"></a>

## <a name="step-4-view-the-cloud-discovery-dashboard-to-see-what-apps-are-being-used-in-your-organization"></a>Adım 4. Bulutta hangi uygulamaların kullanılıyor olduğunu görmek için Bulut Keşif panosuna bakın

Bulut Keşif panosu, bulut uygulamalarının organizasyonda nasıl kullanıldıklarına dair daha fazla fikir vermek üzere tasarlanmıştır. Bu uygulama türleri için kullanılan uygulamalar, açık uyarılarınız ve kuruluşta uygulamaların risk düzeylerine bir bakışta göz atmanızı sağlar.

Bulut Keşif panosuyu kullanmaya başlamak için bkz. [Bulunan uygulamalarla çalışma](/cloud-app-security/discovered-apps).

## <a name="next-steps"></a>Sonraki adımlar

Adım 3 / 3: [Bulut Uygulamaları için Pilot Microsoft Defender](eval-defender-mcas-pilot.md)

Bulut Uygulamaları için [Microsoft Defender'ı Değerlendirme'ye genel bakış](eval-defender-mcas-overview.md)

Değerlendirme ve pilot uygulama için [genel bakış Microsoft 365 Defender](eval-overview.md)
