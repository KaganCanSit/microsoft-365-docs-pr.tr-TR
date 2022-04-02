---
title: Değerlendirme ortamını belirli bir Microsoft Defender for Cloud Apps
description: Farklı bir uygulamanın içindeki Bulut için Defender mimarisini Office 365 için Microsoft Defender ve bu ürünler arasındaki Microsoft 365 Defender öğrenin.
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
ms.openlocfilehash: a66a3563d01e8e4239a0f4815fec9234fd46e1fc
ms.sourcegitcommit: 3b8e009ea1ce928505b8fc3b8926021fb91155f3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/28/2022
ms.locfileid: "64498989"
---
# <a name="enable-the-evaluation-environment-for-microsoft-defender-for-cloud-apps"></a>Değerlendirme ortamını belirli bir Microsoft Defender for Cloud Apps

**Aşağıdakiler için geçerlidir:**

- Microsoft 365 Defender

Bu makale, [değerlendirme ortamını ayarlama sürecindeki Adım 2/ 2'ye](eval-defender-mcas-overview.md), Microsoft Defender for Cloud Apps. Bu işlem hakkında daha fazla bilgi için genel bakış [makalesine bakın](eval-defender-mcas-overview.md).

Bu makale, Bulut için Defender Uygulamaları portalına erişme ve bulut uygulaması trafik verilerini toplamak için gerekli tümleştirmeyi yapılandırma sürecinde size yol sunar.

Ortamınıza kullanılan bulut uygulamalarını keşfetmek için, aşağıdaki yöntemlerden birini veya her ikisini de uygulayabilirsiniz:

- Bulut Bulma ile tümleştirerek Bulut Bulma ile hızlı bir şekilde Uç Nokta için Microsoft Defender. Bu yerel tümleştirme sayesinde hem cihazlarınız hem de cihazlarınız arasında bulut trafiği Windows 10 ağ üzerinde veya Windows 11 veri toplamaya başlayabilirsiniz.
- Ağınıza bağlı tüm cihazlardan erişilen tüm bulut uygulamalarını keşfetmek için güvenlik duvarlarınız ve diğer Bulut için Defender uygulama günlüğü toplayıcısı dağıtın. Bu dağıtım uç noktalarından veri toplamanıza yardımcı olur ve bunları çözümleme için Bulut için Defender Uygulamalar'a gönderir. Bulut için Defender Uygulamalar, daha fazla özellik için bazı üçüncü taraf taraflarla yerel olarak tümleştirilmiştir.

Bu makalede her iki yönteme de yönelik kılavuz bilgiler yer almaktadır.

Bu sorunu ayarlamak için aşağıdaki Microsoft Defender for Cloud Apps.

:::image type="content" source="../../media/defender/m365-defender-mcas-eval-enable-steps.png" alt-text="Microsoft Defender değerlendirme Microsoft Defender for Cloud Apps Microsoft güvenlik yazılımlarını etkinleştirme adımları" lightbox="../../media/defender/m365-defender-mcas-eval-enable-steps.png":::

- [1. Adım. Bağlan uygulamaları Bulut için Defender portalına](#step-1)
- [2. Adım. E-Uç Nokta için Microsoft Defender](#step-2)
- [3. Adım. Güvenlik Bulut için Defender ve diğer artımlarda Uygulama Günlüğü toplayıcıyı dağıtma](#step-3)
- [Adım 4. Bulutta hangi uygulamaların kullanılıyor olduğunu görmek için Bulut Keşif panosuna bakın](#step-4)

<a name="step-1"></a>

## <a name="step-1-connect-to-the-defender-for-cloud-apps-portal"></a>Adım 1. Bağlan uygulamaları Bulut için Defender portalına

Lisansı doğrulamak ve Bulut için Defender Uygulamaları portalına bağlanmak için bkz. [Hızlı Başlangıç: Kullanmaya başlayın'i Microsoft Defender for Cloud Apps](/cloud-app-security/getting-started-with-cloud-app-security).

Portala hemen bağlanamıyorsanız IP adresini güvenlik duvarının izin listesine eklemeniz gerekebilir. Bkz[. Bulut için Defender için temel kurulum](/cloud-app-security/general-setup).

Hala sorun yaşıyorsanız Ağ gereksinimlerini [gözden geçirin](/cloud-app-security/network-requirements).

<a name="step-2"></a>

## <a name="step-2-integrate-with-microsoft-defender-for-endpoint"></a>Adım 2. E-Uç Nokta için Microsoft Defender

Microsoft Defender for Cloud Apps, verilerle Uç Nokta için Microsoft Defender olarak tümleştirilmiştir. Tümleştirme, Bulut Keşif'in daha kolay kullanılabilir olması için, Bulut Keşif özelliklerini şirket ağınız dışında da genişletiyor ve cihaz tabanlı soruşturmaya olanakıyor. Bu tümleştirme, bulut uygulamalarına ve hizmetlere IT tarafından yönetilen Windows 10 cihazlardan Windows 11 ortaya çıkar.

Mobil cihaz ayarlarını zaten Uç Nokta için Microsoft Defender, Bulut için Defender uygulamalarıyla tümleştirmeyi yapılandırma, Microsoft 365 Defender. Tümleştirme açık olduktan sonra, Bulut için Defender Uygulamaları portalına geri dönebilirsiniz ve zengin verileri Bulut Bulma Panosu'nda görüntüleyebilirsiniz.

Bu görevleri gerçekleştirmek için bkz. [Uç Nokta için Microsoft Defender tümleştirmeyi Microsoft Defender for Cloud Apps](/cloud-app-security/mde-integration).

<a name="step-3"></a>

## <a name="step-3-deploy-the-defender-for-cloud-apps-log-collector-on-your-firewalls-and-other-proxies"></a>Adım 3. Güvenlik Bulut için Defender ve diğer artımlarda Uygulama Günlüğü toplayıcıyı dağıtma

Ağınıza bağlı tüm cihazlarda kapsam için, güvenlik duvarlarınız ve diğer aracılarda Bulut için Defender Uygulamaları günlük toplayıcıyı dağıtarak uç noktalardan veri toplayın ve çözümleme için Bulut için Defender Uygulamalarına gönderin.

Aşağıdaki Güvenli Web Ağ Geçidi'ni (SWG) kullanıyorsanız, Bulut için Defender Uygulamaları sorunsuz dağıtım ve tümleştirme sağlar:

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

Adım 3 / 3: [Pilot Microsoft Defender for Cloud Apps](eval-defender-mcas-pilot.md)

Değerlendirme görünümüne genel [bakış Microsoft Defender for Cloud Apps](eval-defender-mcas-overview.md)

Değerlendirme ve pilot uygulama için [genel bakış Microsoft 365 Defender](eval-overview.md)
