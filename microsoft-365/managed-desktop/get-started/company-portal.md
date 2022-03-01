---
title: Cihazlarına Intune Şirket Portalı yükleme
description: Microsoft Yönetilen Masaüstü cihazlarına şirket portalı uygulamasını yükleme hakkında bilgi
keywords: Microsoft Yönetilen Masaüstü, Microsoft 365, Şirket Portalı
ms.service: m365-md
author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.author: tiaraquan
manager: dougeby
ms.topic: article
ms.openlocfilehash: 48d9129689a820816dffe65355fa913fd0742864
ms.sourcegitcommit: 954c8af658adb270fe843991e048c6a30e86e77c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2022
ms.locfileid: "63016479"
---
# <a name="install-intune-company-portal-on-devices"></a>Cihazlarına Intune Şirket Portalı yükleme

Microsoft Yönetilen Masaüstü için, BILGISAYAR yöneticilerinin Microsoft Yönetilen Intune Şirket Portalı cihazlarına sahip kullanıcıları için yüklemesi gerekir. Organizasyon avantajları şunlardır:

- Kullanıcıların, kullanılabilir uygulamalara göz atarak yüklerini tek bir yere sahip olur.
- IT yöneticileri, uygulamaları kullanıcıları için kategorilere göre düzenleyebilir.  
- Bazı uygulamaların (Microsoft Project Microsoft Visio gibi) Microsoft Şirket Portalı Masaüstü ile dağıtım yapmak için bazı uygulamalara ihtiyaç vardır.
- IT yöneticileri, Şirket Portalı özelleştirilebilir. Özelleştirmeler marka görüntülemeyi, yerel destek kişilerine eklemeyi ve daha fazlasını içerir. Daha fazla bilgi için bkz[. Microsoft Intune Şirket Portalı yapılandırma](/intune/company-portal-app).

Bu makalede, Microsoft Yönetilen Masaüstü kullanıcılarınıza Intune Şirket Portalı işlemi belgelemektedir. Genel olarak süreç şöyle olur:

1. [E-Şirket Portalı satın İş İçin Microsoft Store ve Intune ile eşitle](#step-1-purchase-company-portal-from-microsoft-store-for-business-and-sync-with-intune).
2. [Kullanıcılarınıza Şirket Portalı e-posta atama](#step-2-assign-company-portal-to-your-users).
3. [Değişikliği kullanıcılarınıza iletir.](#step-3-communicate-change-to-your-users)

## <a name="step-1-purchase-company-portal-from-microsoft-store-for-business-and-sync-with-intune"></a>1. Adım: E-Şirket Portalı satın İş İçin Microsoft Store ve Intune ile eşitleme

Uygulamaları satın alma ve Intune ile eşitleme hakkında bilgi için bkz. Uygulamaları Microsoft Yönetilen Masaüstü [cihazlarına](deploy-apps.md#msfb-apps) dağıtma İş İçin Microsoft Store uygulamaları *kullanma*.

Bu makalede şunların nasıl olduğu hakkında bilgi sağlar:

- Satın Şirket Portalı satın İş İçin Microsoft Store.
- Intune ile OneDrive arasında İş İçin Microsoft Store.
- Intune ile OneDrive arasında etkin İş İçin Microsoft Store.

## <a name="step-2-assign-company-portal-to-your-users"></a>2. Adım: Kullanıcılarınıza Şirket Portalı posta atama

Microsoft Yönetilen Masaüstü'ne kayıt işleminizi takip etmek için, Şirket Portalı için otomatik olarak dağıtım gerçekleştirin ve uygulamayı kuruluşta Microsoft Yönetilen Masaüstü cihazlarına yükleyin.

## <a name="step-3-communicate-change-to-your-users"></a>3. Adım: Değişikliği kullanıcılarınıza iletir

Kuruluş için BIR YÖNETICI olarak, kullanıcılarınızı kuruluş içinde bu hizmet hizmetlerinden Şirket Portalı haber verebilirsiniz. Microsoft Yönetilen Masaüstü şunları önerer:

- Siteden uygulama yükleme adımları Şirket Portalı. Daha fazla bilgi için bkz [. Cihazınıza uygulama yükleme ve paylaşma](/intune-user-help/install-apps-cpapp-windows).
- Henüz kullanılabilir olmayan uygulamalar için IT yöneticilerine istek gönderme. Daha fazla bilgi için bkz [. İş veya okul için uygulama isteği](/intune-user-help/install-apps-cpapp-windows#request-an-app-for-work-or-school).  

## <a name="steps-to-get-started-with-microsoft-managed-desktop"></a>Microsoft Yönetilen Masaüstü ile çalışmaya başlama adımları

1. Access [yönetici portalı](access-admin-portal.md).
1. [Yönetici portalında yönetici kişilerini ekleyin ve doğrulayın](add-admin-contacts.md).
1. [Kayıt sonrasında ayarları ayarlayın](conditional-access.md).
1. Dağıtım ve atama Intune Şirket Portalı (bu makale).
1. [Lisans atama](assign-licenses.md).
1. [Uygulamaları dağıtın](deploy-apps.md).
1. [Cihazları ayarlama](set-up-devices.md)
1. [AutoPilot ve Kayıt Durumu Sayfası ile ilk çalıştırma deneyimini ayarlayın](esp-first-run.md).
1. [Kullanıcı desteği özelliklerini etkinleştirin](enable-support.md).
1. [Kullanıcılarınızı cihazları kullanmaya hazır hale hazırlayın](get-started-devices.md).
1. [Uygulama denetimi ile çalışmaya başlama](get-started-app-control.md).
