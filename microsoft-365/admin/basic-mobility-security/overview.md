---
title: Mobil için Temel Hareketlilik ve Güvenlik'e Microsoft 365
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
- AdminTemplateSet
search.appverid:
- MET150
description: Cihaz güvenliği ilkelerini ve erişim kurallarını ayarlamak için Temel Mobil Kullanım ve Güvenlik'i kullanın.
ms.openlocfilehash: 4fb1b8ca467d86259f2608af5140510a2a88b23a
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62983996"
---
# <a name="overview-of-basic-mobility-and-security-for-microsoft-365"></a>Mobil için Temel Hareketlilik ve Güvenlik'e Microsoft 365

Temel Mobil Kullanım ve Güvenlik'i kullanarak, mobil cihazları Microsoft 365 bağlandıktan sonra yönetebilirsiniz. İş e-postalarına, takvime, kişilere ve belgelere erişmek için kullanılan akıllı telefonlar ve tabletler gibi mobil cihazlar, çalışanların çalışmalarını her zaman, her yerden yapmalarını büyük bir rol oynar. Bu nedenle, kişiler cihazları kullanıyorken kuruluş bilgilerini korumaya yardımcı olmak çok önemlidir. Cihaz güvenliği ilkelerini ve erişim kurallarını ayarlamak, kaybolan veya çalınan mobil cihazları temizlemek için Temel Mobil Kullanım ve Güvenlik'i kullanabilirsiniz.

:::image type="content" source="../../media/basic-mobility-security/bms-3-setup.png" alt-text="Temel Mobil Kullanım ve Güvenlik Kurulumu.":::

## <a name="what-types-of-devices-can-you-manage"></a>Hangi tür cihazları yönetebilirsiniz?

Temel Mobil Kullanım ve Güvenlik'i kullanarak Windows Phone, Android, IPhone ve iPad. Kurumda kişilerin kullandığı mobil cihazları yönetmek için her kişinin geçerli bir mobil cihaz lisansına Microsoft 365 cihazı Temel Mobil Kullanım ve Güvenlik'e kaydolması gerekir.

Temel Mobil Kullanım ve Güvenlik'in her cihaz türü için neleri desteklediğini görmek için bkz.  [Temel Mobil kullanım ve güvenlik güvenlik bilgileri](capabilities.md).

## <a name="setup-steps-for-basic-mobility-and-security"></a>Temel Hareketlilik ve Güvenlik için kurulum adımları

Genel Microsoft 365 yöneticisinin Temel Hareketlilik ve Güvenlik'i etkinleştirmek ve ayarlamak için aşağıdaki adımları tamamlaması gerekir. Ayrıntılı adımlar için Temel Mobil kullanım ve [güvenlik ayarlama ile ilgili yönergeleri izleyin](set-up.md). 

Adımların özeti şöyledir:

**1. Adım:** Temel Mobil Kullanım ve Güvenlik'isettir adımlarını takip  [edin ve Temel Mobil Kullanım ve Güvenlik'i etkinleştirin](set-up.md).

**2. Adım:** Örneğin, iOS cihazlarını yönetmek için APNs sertifikası oluşturma ve telefonlarınızı desteklemek için etki alanınıza bir Etki Alanı Adı Sistemi (DNS) kaydı ekleme gibi temel Mobil Windows ayarlayın.

**3. Adım:** Cihaz ilkeleri oluşturun ve bunları kullanıcı gruplarına uygulayabilirsiniz. Bunu yapmak için kullanıcılarınız cihazlarına bir kayıt iletisi alırlar ve kayıt işlemini tamamladıklarında, cihazları sizin onlar için ayarlamış olduğunuz ilkeler tarafından kısıtlanır. Daha fazla bilgi için bkz [. Temel Mobil Kullanım ve Güvenlik kullanarak mobil cihazınızı kaydetme](enroll-your-mobile-device.md). 

:::image type="content" source="../../media/basic-mobility-security/bms-4-policy.png" alt-text="Temel Güvenlik ve Mobil Kullanım ilkesi ayarları.":::

## <a name="device-management-tasks"></a>Cihaz yönetimi görevleri

Temel Mobil Kullanım ve Güvenlik'i ayarladıktan ve kullanıcılarınız cihazlarını kaydettikten sonra, gerektiğinde cihazları yönetebilir, erişimi engelleyebilir veya cihazı temizebilirsiniz. Görevlerin nereye tamamlanacakları da dahil olmak üzere sık kullanılan bazı cihaz yönetim görevleri hakkında daha fazla bilgi edinmek için bkz. Görevler için Mobil Cihaz [Yönetimi'ne Microsoft 365](manage-enrolled-devices.md).

## <a name="other-ways-to-manage-devices-and-apps"></a>Cihazları ve uygulamaları yönetmenin diğer yolları

Yalnızca mobil uygulama yönetimine (MAM) ihtiyacınız varsa, belki kendi cihazlarında iş projelerini güncelleştiren kişiler için Intune cihazları kaydetme ve yönetme dışında bir seçenek daha sağlar. Intune aboneliği, kişilerin cihazları Intune'a kaydolmamış olsa bile Azure portalını kullanarak MAM ilkeleri ayarlamaya olanak tanır. Daha fazla bilgi için bkz [. Koruma ilkelerine genel bakış](/mem/intune/apps/app-protection-policy).

## <a name="related-content"></a>İlgili içerik

[Temel Mobil Kullanım ve Güvenlik'i ayarlama](set-up.md) (makale)\
[Temel Mobil Kullanım ve Güvenlik'i kullanarak mobil cihazınızı kaydetme](enroll-your-mobile-device.md) (makale)\
[Cihazlar için Mobil Cihaz Yönetimi'ne kayıtlı cihazları Microsoft 365](manage-enrolled-devices.md) (makale)\
[Temel Hareketlilik ve Güvenlik tarafından yönetilen cihazlar hakkında ayrıntılı bilgi edinebilirsiniz](get-details-about-managed-devices.md) (makale)