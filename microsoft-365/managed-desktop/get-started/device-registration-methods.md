---
title: Microsoft Yönetilen Masaüstü'nden cihaz kayıt yöntemleri
description: Microsoft Yönetilen Masaüstü'nden cihaz kayıt yöntemleriyle ilgili bilgiler
keywords: Microsoft Yönetilen Masaüstü, Microsoft 365, hizmet, belgeler
ms.service: m365-md
author: tiaraquan
ms.author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
manager: dougeby
ms.topic: article
audience: Admin
ms.openlocfilehash: 7d0cabc0a9d11d337e5adabde568bd2a56ceca86
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63704672"
---
# <a name="device-registration-methods"></a>Cihaz kayıt yöntemleri

Microsoft'un cihazlarınızı Microsoft Yönetilen Masaüstü'nden yönetemeden önce, hizmete kayıtlı cihazlarınız olması gerekir.

## <a name="registration-process"></a>Kayıt işlemi

Microsoft Yönetilen Masaüstü, cihaz kayıt iş Windows AutoPilot hizmeti tarafından yönetilir. Başarılı cihaz kaydı için iki adımlık bir işlem gerekir:

1. Cihazın donanım karması olarak bilinen benzersiz donanım kimliği AutoPilot hizmetine yakalanır ve karşıya yükler.
1. Cihaz, bir kullanıcı Azure Active Directory ilişkilendirildi.

İdeal olarak, her iki adım da cihazların satın alın bulunduğu OEM, satıcı veya dağıtımcı tarafından gerçekleştirilir. Bir OEM veya başka bir cihaz sağlayıcısı, sizin adına cihaz kaydı gerçekleştirmek için kayıt yetkilendirme işlemini kullanır.

## <a name="registration-methods"></a>Kayıt yöntemleri

Kayıt işlemi, yeni veya mevcut cihazlardan donanım kimliğini toplayarak ve el ile karşıya yükerek de kuruluş içinde gerçekilebilir. Microsoft Yönetilen Masaüstü'nin desteklediği cihaz kayıt yöntemleri aşağıda verilmiştir:

- OEM kaydı
    - [İş Ortağı portalını kullanma](partner-registration.md#register-devices-using-the-partner-center)
    - [OEM API'lerini kullanma](partner-registration.md#register-devices-by-using-the-oem-api)
- [El ile kayıt](manual-registration.md)
- [Mevcut cihazlar için el ile kayıt](manual-registration-existing-devices.md)

## <a name="recommended-resources"></a>Önerilen kaynaklar

- [AutoPilot'a Windows genel bakış](/mem/autopilot/windows-autopilot)
- [Windows AutoPilot kaydına genel bakış](/mem/autopilot/registration-overview)

## <a name="steps-to-get-started-with-microsoft-managed-desktop"></a>Microsoft Yönetilen Masaüstü ile çalışmaya başlama adımları

1. Access [yönetici portalı](access-admin-portal.md).
1. [Yönetici portalında yönetici kişilerini ekleyin ve doğrulayın](add-admin-contacts.md).
1. [Kayıt sonrasında ayarları ayarlayın](conditional-access.md).
1. Dağıtım ve [Intune Şirket Portalı](company-portal.md).
1. [Lisans atama](assign-licenses.md).
1. [Uygulamaları dağıtın](deploy-apps.md).
1. [Cihazları hazırlayın](prepare-devices.md).
1. [AutoPilot ve Kayıt Durumu Sayfası ile ilk çalıştırma deneyimini ayarlayın](esp-first-run.md).
1. [Kullanıcı desteği özelliklerini etkinleştirin](enable-support.md).
1. [Kullanıcılarınızı cihazları kullanmaya hazır hale hazırlayın](get-started-devices.md).
1. [Uygulama denetimi ile çalışmaya başlama](get-started-app-control.md).
