---
title: iOS'ta Uç Nokta için Microsoft Defender
ms.reviewer: ''
description: iOS'ta Uç Nokta için Microsoft Defender'ı yükleme ve kullanma açıkları
keywords: microsoft, defender, Endpoint için Microsoft Defender, ios, genel bakış, yükleme, dağıtma, kaldırma, intune
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
ms.openlocfilehash: c144eb3cd0cec2d96f20294475618e7e9c49c816
ms.sourcegitcommit: 007822d16e332522546e948f5c216327254a4d49
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/17/2022
ms.locfileid: "63015329"
---
# <a name="microsoft-defender-for-endpoint-on-ios"></a>iOS'ta Uç Nokta için Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Microsoft Defender'ı mı deneyimliysiniz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

**iOS'ta Uç Nokta için Microsoft Defender, web** siteleri, e-postalar ve uygulamalardan kimlik avına ve güvenli olmayan ağ bağlantılarına karşı koruma sağlar. Tüm uyarılar portalda tek bir cam bölmesi Microsoft 365 Defender. Portal, güvenlik ekiplerine diğer platformlarla birlikte iOS cihazlarına yönelik tehditlerin merkezi bir görünümünü sağlar.

> [!CAUTION]
> Diğer üçüncü taraf uç nokta koruma ürünlerini iOS üzerinde Uç Nokta için Defender ile birlikte çalıştırmanın performans sorunlarına ve öngörülemeyen sistem hatalarına neden olması olasıdır.

## <a name="pre-requisites"></a>Önkoşullar

**Son Kullanıcılar için**

- Uygulamanın son kullanıcılara atanan Uç Nokta lisansı için Microsoft Defender. Uç [nokta lisans gereksinimleri için Microsoft Defender'a bakın](/microsoft-365/security/defender-endpoint/minimum-requirements#licensing-requirements).

- **Kayıtlı cihazlar için**:
    - Cihaz/[cihazları,](/mem/intune/user-help/enroll-your-device-in-intune-ios) Intune cihaz Intune Şirket Portalı ilkelerini zorunlu Intune Şirket Portalı mobil cihaz uygulaması aracılığıyla kayıtlıdır. Bu işlem için son kullanıcıya son kullanıcıya Microsoft Intune gerekir.
    - Intune Şirket Portalı uygulaması [Apple App Store'dan indirilebilir](https://apps.apple.com/us/app/intune-company-portal/id719171358).
    
    >[!NOTE]
    >Apple, yeniden yönlendirme kullanıcılarının uygulama mağazasından başka uygulamalar indirmesine izin vermez, bu nedenle bu adımın Uç Nokta uygulaması için Microsoft Defender'a eklemeden önce kullanıcı tarafından yapılması gerekir.)
    
    - Cihaz(lar) başka bir Azure Active Directory. Bunun için son kullanıcının Microsoft Authenticator [gerekir](https://apps.apple.com/app/microsoft-authenticator/id983156458).

- **Kaydı olmayan cihazlar için**: Cihazlar kayıtta kayıtlı Azure Active Directory. Bunun için son kullanıcının Microsoft Authenticator [gerekir](https://apps.apple.com/app/microsoft-authenticator/id983156458).

- Lisans atama hakkında daha fazla bilgi için bkz. [Kullanıcılara lisans atama](/azure/active-directory/users-groups-roles/licensing-groups-assign).

**Yöneticiler için**

- Portala Microsoft 365 Defender.

- Yönetim [Microsoft Endpoint Manager erişim,](https://go.microsoft.com/fwlink/?linkid=2109431) şunları yapmak için:
   - Uygulamayı, kurumda kayıtlı kullanıcı gruplarına dağıtın.
   - Uygulama koruma ilkesinde (MAM) Uç nokta risk işaretleri için Microsoft Defender'ı yapılandırma


    > [!NOTE]
    > - Artık Uç Nokta için Microsoft Defender, mobil cihaz yönetimini (MDM) kullanmayan ancak mobil uygulamaları yönetmek için Intune kullananlar için, yönetilen bir uygulama içindeki verilerine korumayı genişletmektedir. Ayrıca bu desteği, mobil uygulama yönetimi (MAM) için Intune kullanmaya devam ederken diğer kurumsal hareket yönetimi çözümlerini [kullanan müşterilere de genişletmektedir](/mem/intune/apps/mam-faq).
    > - Buna ek olarak, Uç Nokta için Microsoft Defender zaten Intune mobil cihaz yönetimi (MDM) kullanılarak kaydolan cihazları destekler.  

**Sistem Gereksinimleri**

- iOS 12.0 ve üzerini çalıştıran iOS cihazı. iPad'ler de de destek almaktadır. *31-Mart-2022'den itibaren, Uç Nokta için Microsoft Defender tarafından desteklenen en düşük iOS sürümünün iOS 13.0 olacağını unutmayın.*

- Cihaz, Intune Şirket Portalı uygulamasına [kaydedilir veya aynı](https://apps.apple.com/us/app/intune-company-portal/id719171358) hesabı kullanarak Azure Active Directory [Microsoft Authenticator](https://apps.apple.com/app/microsoft-authenticator/id983156458) ile kaydedilir.

## <a name="installation-instructions"></a>Yükleme yönergeleri

iOS'ta Uç Nokta için Microsoft Defender'ın dağıtımı Microsoft Endpoint Manager (MEM) üzerinden yapılabilir ve denetlenen ve denetlenemeyen cihazlar da de destekler. Son kullanıcılar uygulamayı Apple uygulama mağazasından da doğrudan [yükleyebilir](https://aka.ms/mdatpiosappstore).

- Microsoft Endpoint Manager veya Intune aracılığıyla kayıtlı cihazlara dağıtım hakkında bilgi için bkz. [iOS'ta Uç Nokta için Microsoft Defender'ı Dağıtma](ios-install.md).
- Uygulama koruma ilkesinde (MAM) Uç Nokta için Defender'ı kullanma hakkında bilgi için bkz. Uç nokta [risk işaretleri için Defender'ı (MAM) içerecek şekilde uygulama koruma ilkesi yapılandırma](ios-install-unmanaged.md)

## <a name="resources"></a>Kaynaklar

- iOS'ta uç nokta için [Microsoft Defender'daki tüm yenilikler'i](ios-whatsnew.md) veya blog'u ziyaret ederek yaklaşan sürümler hakkında bilgi [sahibi olun](https://techcommunity.microsoft.com/t5/microsoft-defender-atp/bg-p/MicrosoftDefenderATPBlog/label-name/iOS).

- Uygulama içinde geri bildirim sistemi aracılığıyla veya birleşik güvenlik konsolu aracılığıyla [geri bildirim sağlama](https://security.microsoft.com)

## <a name="next-steps"></a>Sonraki adımlar

- [Kayıtlı cihazlar için Intune aracılığıyla iOS'ta Uç Nokta için Microsoft Defender'ı dağıtma](ios-install.md)
- [Uç nokta risk işaretleri (MAM) için Defender'ı içerecek şekilde uygulama koruma ilkesi yapılandırma](ios-install-unmanaged.md)
- [iOS'ta Uç Nokta için Microsoft Defender'ı yapılandırma](ios-configure-features.md)
- [Uç Nokta için Microsoft Defender'ın cihaz risk puanına dayalı olarak Koşullu Erişim ilkesi yapılandırma](ios-configure-features.md#conditional-access-with-defender-for-endpoint-on-ios)
- [Mobil Uygulama Yönetimi (MAM) ile ilgili temel bilgiler](/mem/intune/apps/app-management#mobile-application-management-mam-basics)
