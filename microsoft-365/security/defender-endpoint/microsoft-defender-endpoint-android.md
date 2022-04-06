---
title: Android'de Uç Nokta için Microsoft Defender
ms.reviewer: ''
description: Android'de Uç Nokta için Microsoft Defender yükleme ve kullanma işlemleri açıklanır
keywords: microsoft, defender, Uç Nokta için Microsoft Defender, android, yükleme, dağıtma, kaldırma, intune
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365-initiative-defender-endpoint
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: ea1c551c216dffe8d9ac4e0cedd5679146483e5e
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2022
ms.locfileid: "64666250"
---
# <a name="microsoft-defender-for-endpoint-on-android"></a>Android'de Uç Nokta için Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Şunlar için geçerlidir:**
- [Uç Nokta için Microsoft Defender Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Microsoft Defender mı yaşamak istiyorsunuz? [Ücretsiz deneme için kaydolun.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Bu konuda, Android'de Uç Nokta için Defender'ın nasıl yükleneceği, yapılandırıldığı, güncelleştirildiği ve kullanılacağı açıklanmaktadır.

> [!CAUTION]
> Android'de Uç Nokta için Defender ile birlikte diğer üçüncü taraf uç nokta koruma ürünlerini çalıştırmak, performans sorunlarına ve öngörülemeyen sistem hatalarına neden olabilir.

## <a name="how-to-install-microsoft-defender-for-endpoint-on-android"></a>Android'de Uç Nokta için Microsoft Defender yükleme

### <a name="prerequisites"></a>Önkoşullar

- **Son kullanıcılar için**:
  - Uygulamanın son kullanıcılarına atanmış Uç Nokta için Microsoft Defender lisans. [Lisanslama gereksinimleri Uç Nokta için Microsoft Defender](/microsoft-365/security/defender-endpoint/minimum-requirements#licensing-requirements) bakın
  - Intune Şirket Portalı uygulama [Google Play'den](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal) indirilebilir ve Android cihazda kullanılabilir.
  - Ayrıca cihazlar, Intune cihaz uyumluluk ilkelerini zorunlu kılmak için Intune Şirket Portalı uygulaması aracılığıyla [kaydedilebilir](/mem/intune/user-help/enroll-device-android-company-portal). Bunun için son kullanıcıya bir Microsoft Intune lisansı atanmalıdır.
  - Lisans atama hakkında daha fazla bilgi için bkz. [Kullanıcılara lisans atama](/azure/active-directory/users-groups-roles/licensing-groups-assign).

- **Yöneticiler için**
   - Microsoft 365 Defender portalına erişim.
   - [Microsoft Endpoint Manager yönetim merkezine](https://go.microsoft.com/fwlink/?linkid=2109431)
       - Uygulamayı kuruluşunuzdaki kayıtlı kullanıcı gruplarına dağıtın.
       - Uygulama koruma ilkesinde Uç Nokta için Microsoft Defender risk sinyallerini yapılandırın.
  
    > [!NOTE]
    > - Uç Nokta için Microsoft Defender artık mobil cihaz yönetimi (MDM) kullanılarak kaydedilmemiş ancak mobil uygulamaları yönetmek için Intune kullanan cihazlar için yönetilen uygulama (MAM) içindeki bir kuruluşun verilerine korumayı genişletiyor. Ayrıca bu destek, [mobil uygulama yönetimi (MAM)](/mem/intune/apps/mam-faq) için Intune kullanmaya devam ederken diğer kurumsal mobilite yönetimi çözümlerini kullanan müşterilere de genişletir.
    > - Ayrıca, Uç Nokta için Microsoft Defender zaten Intune mobil cihaz yönetimi (MDM) kullanılarak kaydedilen cihazları destekler.


### <a name="network-requirements"></a>Ağ Gereksinimleri

- Android'de Uç Nokta için Microsoft Defender bir ağa bağlıyken çalışması için güvenlik duvarının/proxy'nin [Uç Nokta için Microsoft Defender hizmet URL'lerine erişimi etkinleştirecek şekilde yapılandırılması](configure-proxy-internet.md#enable-access-to-microsoft-defender-for-endpoint-service-urls-in-the-proxy-server) gerekir.

### <a name="system-requirements"></a>Sistem Gereksinimleri

- Android 6.0 ve üzerini çalıştıran cep telefonları. **Android go çalıştıran cep telefonları, tabletler ve Android çalıştıran diğer mobil cihazlar şu anda desteklenmemektedir.**
- Intune Şirket Portalı uygulaması [Google Play'den](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal) indirilir ve yüklenir. Intune cihaz uyumluluk ilkelerinin uygulanması için cihaz kaydı gereklidir.

### <a name="installation-instructions"></a>Yükleme yönergeleri

Android'de Uç Nokta için Microsoft Defender, kayıtlı cihazların her iki moduna da (eski Cihaz Yöneticisi ve Android Enterprise modları) yüklemeyi destekler. **Şu anda, android Enterprise iş profiline ve Şirkete ait tam olarak yönetilen kullanıcı cihaz kayıtlarına sahip kişisel cihazlar desteklenmektedir. Diğer Android Enterprise modları için destek hazır olduğunda duyurulacaktır.**

- Android'de Uç Nokta için Microsoft Defender dağıtımı Microsoft Intune (MDM) üzerinden yapılır. Daha fazla bilgi için bkz[. Microsoft Intune ile Android'de Uç Nokta için Microsoft Defender dağıtma](android-intune.md).
- Intune mobil cihaz yönetimi (MDM) kullanılarak kaydedilmemiş cihazlara Uç Nokta için Microsoft Defender yüklemesi için bkz. [Uygulama koruma ilkesinde (MAM) Uç Nokta için Microsoft Defender risk sinyallerini yapılandırma](android-configure-mam.md).

> [!NOTE]
> **Android'de Uç Nokta için Microsoft Defender artık [Google Play'de](https://play.google.com/store/apps/details?id=com.microsoft.scmx) kullanılabilir.**
>
> Uç Nokta için Microsoft Defender uygulamasını Cihaz Yöneticisi ve Android Enterprise kayıt modları arasında dağıtmak için Intune'den Google Play'e bağlanabilirsiniz.

## <a name="how-to-configure-microsoft-defender-for-endpoint-on-android"></a>Android'de Uç Nokta için Microsoft Defender Yapılandırma

Android özelliklerinde Uç Nokta için Microsoft Defender yapılandırma yönergelerine Android özelliklerinde [Uç Nokta için Microsoft Defender yapılandırma](android-configure.md) bölümünden ulaşabilirsiniz.

## <a name="related-topics"></a>İlgili konular

- [Android’de Uç Nokta için Defender’ı Microsoft Intune ile dağıtın](android-intune.md)
- [Android’de Uç Nokta için Microsoft Defender’ı yapılandırın](android-configure.md)
- [Mobil Uygulama Yönetimi (MAM) ile ilgili temel bilgiler](/mem/intune/apps/app-management#mobile-application-management-mam-basics)
