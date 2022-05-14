---
title: Adım 5. Kurumsal kiracılar için Microsoft 365 cihaz ve uygulama yönetimi
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
- m365solution-tenantmanagement
- tenant-management
- m365solution-scenario
ms.custom:
- Ent_Solutions
description: Microsoft 365 kiracılarınız için cihaz ve uygulama yönetimi için doğru seçeneği dağıtın.
ms.openlocfilehash: 3999d30aaeee9ebfc2af90b0aeeeaea1b46986fb
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2022
ms.locfileid: "65419472"
---
# <a name="step-5-device-and-app-management-for-your-microsoft-365-for-enterprise-tenants"></a>Adım 5. Kurumsal kiracılar için Microsoft 365 cihaz ve uygulama yönetimi

kuruluş için Microsoft 365, mobil cihaz yönetimi (MDM) ve mobil uygulama yönetimi (MAM) ile cihazları yönetmeye ve kuruluşunuzdaki cihazlardaki uygulamaların kullanımına yardımcı olan özellikler içerir. Verileriniz dahil olmak üzere kuruluşunuzun kaynaklarına erişimi korumak için iOS, Android, macOS ve Windows cihazları yönetebilirsiniz. Örneğin, e-postaların kuruluşunuzun dışındaki kişilere gönderilmesini engelleyebilir veya çalışanınızın kişisel cihazlarında kuruluş verilerini kişisel verilerden yalıtabilirsiniz.

Aşağıda kullanıcıların, cihazlarının ve Microsoft Teams gibi yerel ve bulut üretkenlik uygulamalarının doğrulanması ve yönetilmesine ilişkin bir örnek verilmiştir.

![Kullanıcıların, cihazların ve uygulamaların doğrulanması ve yönetimi.](../media/tenant-management-overview/tenant-management-device-app-mgmt.png)

Kuruluşunuzun kaynaklarının güvenliğini sağlamanıza ve korumanıza yardımcı olmak için, Microsoft 365 kurumsal cihazlar ve uygulamalara erişimlerini yönetmeye yardımcı olacak özellikler içerir. Cihaz yönetimi için iki seçenek vardır:

- kuruluşlar için kapsamlı bir cihaz ve uygulama yönetimi çözümü olan Microsoft Intune.
- Kuruluşunuzdaki cihazları yönetmek için tüm Microsoft 365 ürünlerine dahil edilen Intune hizmetlerinin bir alt kümesi olan Temel Mobilite ve Güvenlik. Daha fazla bilgi için bkz. [Temel Mobilite ve Güvenlik Özellikleri](../admin/basic-mobility-security/capabilities.md).

Microsoft 365 E3 veya E5 kullanıyorsanız Intune kullanmalısınız.

## <a name="microsoft-intune"></a>Microsoft Intune

[MDM](/mem/intune/fundamentals/planning-guide) veya MAM kullanarak kuruluşunuza erişimi yönetmek için Microsoft Intune kullanırsınız. MDM, kullanıcıların cihazlarını Intune "kaydettiği" durumdur. Bir cihaz kaydedildikten sonra yönetilen bir cihazdır ve kuruluşunuzun ilkelerini, kurallarını ve ayarlarını alabilir. Örneğin, belirli uygulamaları yükleyebilir, parola ilkesi oluşturabilir, VPN bağlantısı yükleyebilir ve daha fazlasını yapabilirsiniz.

Kendi kişisel cihazları olan kullanıcılar cihazlarını kaydetmek istemeyebilir veya Intune ve kuruluşunuzun ilkeleri tarafından yönetilebilir. Ancak yine de kuruluşunuzun kaynaklarını ve verilerini korumanız gerekir. Bu senaryoda, MAM kullanarak uygulamalarınızı koruyabilirsiniz. Örneğin, cihazda SharePoint erişirken kullanıcının PIN girmesini gerektiren bir MAM ilkesi kullanabilirsiniz.

Ayrıca kişisel cihazları ve kuruluşa ait cihazları nasıl yöneteceğini de belirlersiniz. Cihazları kullanımlarına bağlı olarak farklı şekilde ele almak isteyebilirsiniz.

## <a name="identity-and-device-access-configurations"></a>Kimlik ve cihaz erişimi yapılandırmaları

Microsoft, güvenli ve üretken bir iş gücü sağlamak için [kimlik ve cihaz erişimi](../security/office-365-security/microsoft-365-policies-configurations.md) için bir dizi yapılandırma sağlar. Bu yapılandırmalar şunların kullanımını içerir:

- Koşullu Erişim ilkelerini Azure AD
- Cihaz uyumluluk ve uygulama koruma ilkelerini Microsoft Intune
- Kimlik Koruması kullanıcı risk ilkelerini Azure AD
- Bulut uygulamalarının ek ilkeleri

Aşağıda, kullanıcıları, cihazlarını ve Microsoft Teams gibi yerel ve bulut üretkenlik uygulamalarının kullanımını doğrulamak ve kısıtlamak için bu ayarların ve ilkelerin bir örneği verilmiştir.

![Kullanıcılar, cihazları ve uygulama kullanımıyla ilgili gereksinimler ve kısıtlamalar için kimlik ve cihaz erişim yapılandırmaları.](../media/tenant-management-overview/tenant-management-device-app-mgmt-golden-config.png)

Cihaz erişimi ve uygulama yönetimi için şu makalelerdeki yapılandırmaları kullanın:

- [Önkoşullar](../security/office-365-security/identity-access-prerequisites.md)
- [Genel kimlik ve cihaz erişim ilkeleri](../security/office-365-security/identity-access-policies.md)

## <a name="results-of-step-5"></a>5. Adımın Sonuçları

Microsoft 365 kiracınızın cihaz ve uygulama yönetimi için, kullanıcıları, cihazlarını ve yerel ve bulut üretkenlik uygulamalarının kullanımını doğrulamak ve kısıtlamak için Intune ayarlarını ve ilkelerini belirlediniz.

Aşağıda, yeni öğelerin vurgulandığı Intune cihaz ve uygulama yönetimine sahip bir kiracı örneği verilmiştir.

![Intune cihaz ve uygulama yönetimine sahip bir kiracı örneği.](../media/tenant-management-overview/tenant-management-tenant-build-step5.png)

Bu çizimde kiracının şunları vardır:

- Intune kayıtlı kuruluşa ait cihazlar.
- Kayıtlı ve kişisel cihazlar için cihaz ve uygulama ilkelerini Intune.

## <a name="ongoing-maintenance-for-device-and-app-management"></a>Cihaz ve uygulama yönetimi için sürekli bakım

Sürekli olarak şunları yapmanız gerekebilir: 

- Cihaz kaydını yönetme.
- Ek uygulamalar, cihazlar ve güvenlik gereksinimleri için ayarlarınızı ve ilkelerinizi düzeltin.
