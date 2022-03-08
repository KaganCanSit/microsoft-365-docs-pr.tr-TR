---
title: Uygulama denetimi ile çalışmaya başlama
description: Bu makalede uygulama denetimi nasıl etkinleştirilen açıklanmıştır
keywords: Microsoft Yönetilen Masaüstü, Microsoft 365, hizmet, belgeler
ms.service: m365-md
author: tiaraquan
ms.author: tiaraquan
manager: dougeby
audience: ITpro
ms.topic: article
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.openlocfilehash: a671bf36e957ffc416f51ec531aaeed6ddfa41b3
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63315407"
---
# <a name="get-started-with-app-control"></a>Uygulama denetimi ile çalışmaya başlama

Ortamınıza uygulama denetimi etkinleştirmeden önce, [Microsoft](../service-description/app-control.md) Yönetilen Masaüstü'nin bunu nasıl uygulaydığını ve rollerinizi ve sorumluluklarınızı gözden geçirmeyi ve anlamaya emin olun.

Microsoft Yönetilen Masaüstü, güvenli temel ilke almada daha zor olan yönleri dikkate alarak uygulama yönetimini basitleştirmektedir.

IT Yöneticilerinizin uygulamalarınızı Test halkası içinde test edin ve uyarı ya da hata varsa günlüklerini gözden geçirmesi gerekir. Bir uygulamanın muaf olması gerekirse, önce kimlerin bunu algılayana bağlı olarak bir istek dosyası açabilirsiniz veya Microsoft Yönetilen Masaüstü İşlemleri olabilir.

## <a name="initial-deployment-of-apps"></a>Uygulamaların ilk dağıtımı

Uygulamaları ilk dağıtsanız da, Microsoft Yönetilen Masaüstü'nin geçerli davranışlarını değerlendirmesi gerekir. Uygulama denetimi etkinleştirmenin tam adımları, cihazları ortamınıza zaten dağıtıp dağıtıp dağıtmamanıza bağlıdır.

### <a name="devices-not-yet-in-use"></a>Henüz kullanmayan cihazlar

Kullanımda henüz hiç cihaz yoksa, uygulama denetimi açmak için Microsoft Yönetilen Masaüstü İşlemleri'nin olduğu bir destek bileti açın. İşlemler, ilkeleri bu zamanlamayı takip eden dağıtım gruplarına aşamalı olarak dağıtır:

| Dağıtım grubu | İlke türü | Zamanlama |
| ------ | ------ | ------ |
| Test |  Denetim |  0. Gün |
| Birinci | Zorunlu | 1. Gün |
| Hızlı | Zorunlu |  2. Gün |
| Geniş | Zorunlu |  3. Gün |

Dağıtım sırasında istediğiniz zaman bu dağıtımın bir bölümünü duraklatmak veya geri almak için başka bir destek isteği açabilirsiniz.

### <a name="devices-already-in-use"></a>Zaten kullanımda olan cihazlar

Kullanımda zaten en az bir Microsoft Yönetilen Masaüstü cihazı varsa şu adımları izleyin:

1. Microsoft Yönetilen Masaüstü İşlemleri'nin uygulama denetimi açmamız için istekte bulundurarak bir hizmet bileti açın. İşlemler, tüm [cihazlara Denetim](../service-description/app-control.md#audit-policy) ilkesi dağıtır.
2. [Engel olup olacağını](../working-with-managed-desktop/work-with-app-control.md#add-a-new-app) görmek için uygulamalarınızı test edin. Uygulama engellenmişse, imzacı [isteği açın](../working-with-managed-desktop/work-with-app-control.md#add-or-remove-a-trusted-signer).
3. Testlerinizi tamamlandıktan (sonuçlar ne olursa olsun) sonra İşlemler'e bekleyen imzalayanların isteklerini not olarak bildirin. İşlemler, ilkeleri bu zamanlamayı takip eden dağıtım gruplarına aşamalı olarak dağıtır:

| Dağıtım grubu | İlke türü | Zamanlama |
| ------ | ------ | ------ |
| Test     | Denetim |  0. Gün |
| Birinci     | Zorunlu | 1. Gün |
| Hızlı     | Zorunlu |  Duraklatıldı, isteğin üzerine yuvarlandı |
| Geniş     | Zorunlu |  Duraklatıldı, isteğin üzerine yuvarlandı |

Dağıtım sırasında istediğiniz zaman bu dağıtımın bir bölümünü duraklatmak veya geri almak için başka bir destek isteği açabilirsiniz.

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
1. Uygulama denetimiyle çalışmaya başlama (bu makale).
