---
title: iOS'ta Uç Nokta için Microsoft Defender
ms.reviewer: ''
description: iOS'ta Uç Nokta için Microsoft Defender yükleme ve kullanma işlemleri açıklanır
keywords: microsoft, defender, Uç Nokta için Microsoft Defender, ios, genel bakış, yükleme, dağıtma, kaldırma, intune
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365-initiative-defender-endpoint
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: dcc67b2d2a9ad03dc1235eebd577e3525ab07a03
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2022
ms.locfileid: "64665942"
---
# <a name="microsoft-defender-for-endpoint-on-ios"></a>iOS'ta Uç Nokta için Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Şunlar için geçerlidir:**
- [Uç Nokta için Microsoft Defender Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Microsoft Defender mı yaşamak istiyorsunuz? [Ücretsiz deneme için kaydolun.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

**iOS'ta Uç Nokta için Microsoft Defender**, web sitelerinden, e-postalardan ve uygulamalardan gelen kimlik avına ve güvenli olmayan ağ bağlantılarına karşı koruma sağlar. Tüm uyarılar, Microsoft 365 Defender portalındaki tek bir cam bölmeden kullanılabilir. Portal, güvenlik ekiplerine diğer platformlarla birlikte iOS cihazlarında tehditlerin merkezi bir görünümünü sağlar.

> [!CAUTION]
> iOS'ta Uç Nokta için Defender'ın yanı sıra diğer üçüncü taraf uç nokta koruma ürünlerini çalıştırmak, performans sorunlarına ve öngörülemeyen sistem hatalarına neden olabilir.

## <a name="pre-requisites"></a>Önkoşullar

**Son Kullanıcılar için**

- Uygulamanın son kullanıcılarına atanmış Uç Nokta için Microsoft Defender lisans. Bkz. [lisanslama gereksinimleri Uç Nokta için Microsoft Defender](/microsoft-365/security/defender-endpoint/minimum-requirements#licensing-requirements).

- **Kayıtlı cihazlar için**:
    - Cihazlar, Intune cihaz uyumluluk ilkelerini zorunlu kılmak için Intune Şirket Portalı uygulaması aracılığıyla [kaydedilir](/mem/intune/user-help/enroll-your-device-in-intune-ios). Bunun için son kullanıcıya bir Microsoft Intune lisansı atanmalıdır.
    - Intune Şirket Portalı uygulaması [Apple App Store'dan](https://apps.apple.com/us/app/intune-company-portal/id719171358) indirilebilir.
    
    >[!NOTE]
    >Apple, kullanıcıların uygulama mağazasından diğer uygulamaları indirmesine izin vermez, bu nedenle bu adımın Uç Nokta için Microsoft Defender uygulamaya eklemeden önce kullanıcı tarafından yapılması gerekir.)
    
    - Cihazlar Azure Active Directory kaydedilir. Bunun için son kullanıcının [Microsoft Authenticator uygulama](https://apps.apple.com/app/microsoft-authenticator/id983156458) üzerinden oturum açması gerekir.

- **Kayıtlı olmayan cihazlar için**: Cihazlar Azure Active Directory kaydedilir. Bunun için son kullanıcının [Microsoft Authenticator uygulama](https://apps.apple.com/app/microsoft-authenticator/id983156458) üzerinden oturum açması gerekir.

- Lisans atama hakkında daha fazla bilgi için bkz. [Kullanıcılara lisans atama](/azure/active-directory/users-groups-roles/licensing-groups-assign).

**Yöneticiler için**

- Microsoft 365 Defender portalına erişim.

- [Microsoft Endpoint Manager yönetim merkezine](https://go.microsoft.com/fwlink/?linkid=2109431) erişim:
   - Uygulamayı kuruluşunuzdaki kayıtlı kullanıcı gruplarına dağıtın.
   - Uygulama koruma ilkesinde (MAM) Uç Nokta için Microsoft Defender risk sinyallerini yapılandırma


    > [!NOTE]
    > - Uç Nokta için Microsoft Defender artık mobil cihaz yönetimi (MDM) kullanmayan ancak mobil uygulamaları yönetmek için Intune kullananlar için yönetilen uygulama içindeki bir kuruluşun verilerine korumayı genişletiyor. Ayrıca bu destek, [mobil uygulama yönetimi (MAM)](/mem/intune/apps/mam-faq) için Intune kullanmaya devam ederken diğer kurumsal mobilite yönetimi çözümlerini kullanan müşterilere de genişletir.
    > - Ayrıca, Uç Nokta için Microsoft Defender zaten Intune mobil cihaz yönetimi (MDM) kullanılarak kaydedilen cihazları destekler.  

**Sistem Gereksinimleri**

- iOS 12.0 ve üzerini çalıştıran iOS cihazı. iPad'ler de desteklenir. *31-Mart 2022'den itibaren, Uç Nokta için Microsoft Defender tarafından desteklenen en düşük iOS sürümünün iOS 13.0 olacağını unutmayın.*

- Cihaz[, Intune Şirket Portalı uygulamasına](https://apps.apple.com/us/app/intune-company-portal/id719171358) kaydedilir veya aynı hesapla [Microsoft Authenticator aracılığıyla Azure Active Directory](https://apps.apple.com/app/microsoft-authenticator/id983156458) ile kaydedilir.

## <a name="installation-instructions"></a>Yükleme yönergeleri

iOS'ta Uç Nokta için Microsoft Defender dağıtımı Microsoft Endpoint Manager (MEM) aracılığıyla yapılabilir ve hem denetimli hem de denetimsiz cihazlar desteklenir. Son kullanıcılar uygulamayı [doğrudan Apple uygulama mağazasından](https://aka.ms/mdatpiosappstore) da yükleyebilir.

- Kayıtlı cihazlarda Microsoft Endpoint Manager veya Intune aracılığıyla dağıtma hakkında bilgi için bkz. [iOS'ta Uç Nokta için Microsoft Defender dağıtma](ios-install.md).
- Uygulama koruma ilkesinde (MAM) Uç Nokta için Defender'ı kullanma hakkında bilgi için bkz. [Uygulama koruma ilkesini Uç Nokta için Defender risk sinyallerini (MAM) içerecek şekilde yapılandırma](ios-install-unmanaged.md)

## <a name="resources"></a>Kaynaklar

- [iOS'ta Uç Nokta için Microsoft Defender'deki yenilikler](ios-whatsnew.md) sayfasını veya [blogumuzu](https://techcommunity.microsoft.com/t5/microsoft-defender-atp/bg-p/MicrosoftDefenderATPBlog/label-name/iOS) ziyaret ederek yaklaşan sürümler hakkında bilgi sahibi olun.

- Uygulama içi geri bildirim sistemi aracılığıyla veya [birleşik güvenlik konsolu](https://security.microsoft.com) aracılığıyla geri bildirim sağlayın

## <a name="next-steps"></a>Sonraki adımlar

- [Kayıtlı cihazlar için Intune aracılığıyla iOS'ta Uç Nokta için Microsoft Defender dağıtma](ios-install.md)
- [Uygulama koruma ilkesini Uç Nokta için Defender risk sinyallerini (MAM) içerecek şekilde yapılandırma](ios-install-unmanaged.md)
- [iOS özelliklerinde Uç Nokta için Microsoft Defender yapılandırma](ios-configure-features.md)
- [koşullu erişim ilkesini Uç Nokta için Microsoft Defender cihaz risk puanına göre yapılandırma](ios-configure-features.md#conditional-access-with-defender-for-endpoint-on-ios)
- [Mobil Uygulama Yönetimi (MAM) ile ilgili temel bilgiler](/mem/intune/apps/app-management#mobile-application-management-mam-basics)
