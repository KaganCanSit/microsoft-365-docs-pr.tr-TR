---
title: Microsoft 365 için Temel Hareketlilik ve Güvenlik'e genel bakış
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
description: Temel Hareketlilik ve Güvenlik’i ayarlayıp kullanarak Microsoft 365 kuruluşunuza bağlı mobil cihazları yönetin ve güvenliklerini sağlayın.
ms.openlocfilehash: 9a9b3d433408d4ce5225f1a74351d01150744132
ms.sourcegitcommit: 1fa0b15f86470c49dddf0d6de59d553a38ae259b
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/03/2022
ms.locfileid: "65863216"
---
# <a name="overview-of-basic-mobility-and-security-for-microsoft-365"></a>Microsoft 365 için Temel Hareketlilik ve Güvenlik'e genel bakış

Temel Hareketlilik ve Güvenlik’i kullanarak, Microsoft 365 kuruluşunuza bağlı olduklarında mobil cihazları yönetebilir ve güvenliğini sağlayabilirsiniz. İş e-posta adresine, takvime, kişilere ve belgelere erişmek için kullanılan akıllı telefonlar ve tabletler gibi mobil cihazlar, çalışanların işlerini her zaman, her yerden yapmalarını sağlamada önemli rol oynar. Bu nedenle, insanlar cihazları kullandığında kuruluşunuzun bilgilerini korumaya yardımcı olmanız çok önemlidir. Cihaz güvenlik ilkelerini ve erişim kurallarını belirlemek ve kaybolmaları veya çalınmaları durumunda mobil cihazları silmek için Temel Hareketlilik ve Güvenlik'i kullanabilirsiniz.

:::image type="content" source="../../media/basic-mobility-security/bms-3-setup.png" alt-text="Temel Hareketlilik ve Güvenlik Kurulumu.":::

## <a name="what-types-of-devices-can-you-manage"></a>Hangi cihaz türlerini yönetebilirsiniz?

Temel Hareketlilik ve Güvenlik'i kullanarak Windows Phone, Android, iPhone ve iPad gibi birçok mobil cihaz türlerini yönetebilirsiniz. Kuruluşunuzdaki kişiler tarafından kullanılan mobil cihazları yönetmek için her kişinin geçerli bir Microsoft 365 lisansına sahip olması ve cihazlarının Temel Hareketlilik ve Güvenlik'e kayıtlı olması gerekir.

Temel Hareketlilik ve Güvenlik’in her bir cihaz türü için neleri desteklediğini görmek için, bkz. [Temel Hareketlilik ve Güvenlik Özellikleri](capabilities.md).

## <a name="setup-steps-for-basic-mobility-and-security"></a>Temel Hareketlilik ve Güvenlik için kurulum adımları

Bir Microsoft 365 genel yöneticisinin Temel Hareketlilik ve Güvenlik’i etkinleştirmek ve ayarlamak için aşağıdaki adımları tamamlaması gerekir. Ayrıntılı adımlar için [Temel Hareketlilik ve Güvenlik’i Ayarlama](set-up.md)’daki kılavuzu izleyin. 

Adımların özeti şöyledir:

**1. Adım:** [Temel Hareketlilik ve Güvenlik’i Ayarlama](set-up.md)’daki adımları izleyerek Temel Hareketlilik ve Güvenlik’i etkinleştirin.

**2. Adım:** Örneğin, iOS cihazlarını yönetmek için bir APNs sertifikası oluşturarak ve etki alanınız için Windows telefonlarını desteklemek üzere bir Etki Alanı Adı Sistemi (DNS) kaydı ekleyerek Temel Hareketlilik ve Güvenlik’i ayarlayın.

**3. Adım:** Cihaz ilkeleri oluşturun ve bunları kullanıcı gruplarına uygulayın. Bunu yaptığınızda, kullanıcılarınız cihazlarına kayıt iletisi alır ve kayıtlarını tamamladıklarında cihazları, onlar için ayarladığınız ilkeler tarafından kısıtlanır. Daha fazla bilgi için bkz. [Mobil cihazınızı Temel Hareketlilik ve Güvenlik kullanarak kaydettirin](enroll-your-mobile-device.md). 

:::image type="content" source="../../media/basic-mobility-security/basic-mobility-microsoft-purview.png" alt-text="Temel Güvenlik ve Hareketlilik ilkesi ayarları.":::

## <a name="device-management-tasks"></a>Cihaz yönetimi görevleri

Temel Hareketlilik ve Güvenlik ayarını yaptıktan ve kullanıcılarınız cihazlarını kaydettirdikten sonra, gerekirse cihazları yönetebilir, erişimi engelleyebilir veya bir cihazı silebilirsiniz. Görevlerin nerede tamamlanacağı da dahil olmak üzere bazı yaygın cihaz yönetimi görevleri hakkında daha fazla bilgi edinmek için bkz. [Microsoft 365 için Mobil Cihaz Yönetimi'ne kaydedilen cihazları yönetme](manage-enrolled-devices.md).

## <a name="other-ways-to-manage-devices-and-apps"></a>Cihazları ve uygulamaları yönetmenin diğer yolları

Yalnızca kendi cihazlarında iş projelerini güncelleştiren kişiler için mobil uygulama yönetimine (MAM) ihtiyacınız varsa, Intune cihazları kaydetmenin ve yönetmenin yanı sıra başka bir seçenek sunar. Intune aboneliği, kullanıcıların cihazları Intune'a kayıtlı olmasa bile Azure portalını kullanarak MAM ilkeleri ayarlamanıza olanak sağlar. Daha fazla bilgi için bkz.[Uygulama koruması ilkelerine genel bakış](/mem/intune/apps/app-protection-policy).

## <a name="related-content"></a>İlgili içerik

[Temel Hareketlilik ve Güvenlik Ayarlama](set-up.md) (makale)\
[Mobil cihazınızı Temel Hareketlilik ve Güvenlik kullanarak kaydetme](enroll-your-mobile-device.md) (makale)\
[Microsoft 365 için Mobil Cihaz Yönetimi'ne kayıtlı cihazları yönetme](manage-enrolled-devices.md) (makale)\
[Temel Hareketlilik ve Güvenlik tarafından yönetilen cihazlarla ilgili ayrıntıları öğrenme](get-details-about-managed-devices.md) (makale)