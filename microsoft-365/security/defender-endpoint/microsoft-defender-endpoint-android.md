---
title: Android'de Uç Nokta için Microsoft Defender
ms.reviewer: ''
description: Android'de Uç Nokta için Microsoft Defender'ı yükleme ve kullanma açıkları
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
ms.openlocfilehash: 7d4e553e89f83f9b641367bb4037b4eb7da21f8b
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/12/2022
ms.locfileid: "63011995"
---
# <a name="microsoft-defender-for-endpoint-on-android"></a>Android'de Uç Nokta için Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Microsoft Defender'ı mı deneyimliysiniz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Bu konu başlığında, Android'de Uç Nokta için Defender'ı yükleme, yapılandırma, güncelleştirme ve kullanma açıklanmıştır.

> [!CAUTION]
> Diğer üçüncü taraf uç nokta koruma ürünlerini, Android'de Uç Nokta için Defender'ın yanı sıra çalıştırmanın performans sorunlarına ve öngörülemeyen sistem hatalarına neden olması olasıdır.

## <a name="how-to-install-microsoft-defender-for-endpoint-on-android"></a>Android'de Uç Nokta için Microsoft Defender'ı yükleme

### <a name="prerequisites"></a>Önkoşullar

- **Son kullanıcılar için**:
  - Uygulamanın son kullanıcılara atanan Uç Nokta lisansı için Microsoft Defender. Uç [nokta lisans gereksinimleri için Microsoft Defender'a bakın](/microsoft-365/security/defender-endpoint/minimum-requirements#licensing-requirements)
  - Intune Şirket Portalı Google [Play'den](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal) indirilebilir ve Android cihazında kullanılabilir.
  - Bunlara ek olarak, Intune cihaz [uyumluluk](/mem/intune/user-help/enroll-device-android-company-portal) ilkelerini zorunlu Intune Şirket Portalı cihaz(lar) uygulaması yoluyla da kaydolabilirsiniz. Bu işlem için son kullanıcıya son kullanıcıya Microsoft Intune gerekir.
  - Lisans atama hakkında daha fazla bilgi için bkz. [Kullanıcılara lisans atama](/azure/active-directory/users-groups-roles/licensing-groups-assign).

- **Yöneticiler için**
   - Portala Microsoft 365 Defender.
   - Yönetim [Microsoft Endpoint Manager Access](https://go.microsoft.com/fwlink/?linkid=2109431)
       - Uygulamayı, kurumda kayıtlı kullanıcı gruplarına dağıtın.
       - Uygulama koruma ilkesinde Uç nokta risk işaretleri için Microsoft Defender'ı yapılandırın.
  
    > [!NOTE]
    > - Uç Nokta için Microsoft Defender artık, mobil cihaz yönetimi (MDM) kullanılarak kaydolmamış olan ancak mobil uygulamaları yönetmek için Intune kullanan cihazlar için, yönetilen bir uygulama (MAM) içinde kuruluşun verilerini genişletmektedir. Ayrıca bu desteği, mobil uygulama yönetimi (MAM) için Intune kullanmaya devam ederken diğer kurumsal hareket yönetimi çözümlerini [kullanan müşterilere de genişletmektedir](/mem/intune/apps/mam-faq).
    > - Buna ek olarak, Uç Nokta için Microsoft Defender zaten Intune mobil cihaz yönetimi (MDM) kullanılarak kaydolan cihazları destekler.


### <a name="network-requirements"></a>Ağ Gereksinimleri

- Android'de Uç Nokta için Microsoft Defender'ın bir ağa bağlıyken çalışması için güvenlik duvarının/ara sunucunun Uç Nokta hizmeti URL'leri için Microsoft Defender'a erişimi etkinleştirecek şekilde [yapılandırılması gerekir](configure-proxy-internet.md#enable-access-to-microsoft-defender-for-endpoint-service-urls-in-the-proxy-server).

### <a name="system-requirements"></a>Sistem Gereksinimleri

- Android 6.0 ve üzerini çalıştıran cep telefonları. **Android go, tabletler ve Android çalıştıran diğer mobil cihazları çalıştıran cep telefonları şu anda desteklemektedir.**
- Intune Şirket Portalı uygulaması [Google Play'den indirilir](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal) ve yüklenir. Intune cihaz uyumluluk ilkelerinin zorunlu tutul olması için cihaz kaydı gereklidir.

### <a name="installation-instructions"></a>Yükleme yönergeleri

Android'de Uç Nokta için Microsoft Defender, kayıtlı cihazların her iki moduyla (eski Cihaz Yöneticisi ve Android cihaz modu) Enterprise destekler. **Şu anda, İş profiline sahip ve Kurumsal'a ait tam kullanıcı cihaz kayıtlarına sahip olan, kişisel olarak sahip olunan cihazlar Android Enterprise. Hazır olduğunda diğer Android Enterprise modları desteği duyuruldu.**

- Android'de Uç Nokta için Microsoft Defender'ın dağıtımı Microsoft Intune (MDM) üzerindendir. Daha fazla bilgi için bkz. [Android'de Uç Nokta için Microsoft Defender'ı Farklı Microsoft Intune](android-intune.md).
- Intune mobil cihaz yönetimi (MDM) kullanılarak kaydolmamış cihazlara Uç Nokta için Microsoft Defender yüklemesi, bkz. Uygulama koruma ilkesinde [(MAM) Uç nokta risk işaretleri için Microsoft Defender'ı yapılandırma](android-configure-mam.md).

> [!NOTE]
> **Android'de Uç Nokta için Microsoft Defender artık [Google Play'de](https://play.google.com/store/apps/details?id=com.microsoft.scmx) kullanılabilir.**
>
> Intune'dan Google Play'e bağlanarak Cihaz Yöneticisi ve Android için Uç Nokta uygulaması için Microsoft Defender'ı ve kayıt Enterprise dağıtabilirsiniz.

## <a name="how-to-configure-microsoft-defender-for-endpoint-on-android"></a>Android'de Uç Nokta için Microsoft Defender'ı Yapılandırma

Android üzerinde Uç Nokta için Microsoft Defender'ı yapılandırma kılavuzuna Android üzerinde [Uç Nokta için Microsoft Defender özelliklerini yapılandırma makalesinden de sunabilirsiniz](android-configure.md).

## <a name="related-topics"></a>İlgili konular

- [Android'de Uç Nokta için Microsoft Defender'ı Microsoft Intune](android-intune.md)
- [Android'de Uç Nokta için Microsoft Defender özelliklerini yapılandırma](android-configure.md)
- [Mobil Uygulama Yönetimi (MAM) ile ilgili temel bilgiler](/mem/intune/apps/app-management#mobile-application-management-mam-basics)
