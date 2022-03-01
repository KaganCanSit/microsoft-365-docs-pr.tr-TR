---
title: Adım 5. Kurumsal kiracılar için mobil Microsoft 365 ve uygulama yönetimi
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
description: Cihaz ve uygulama yönetimi için doğru seçeneği kiracılarınızı Microsoft 365 dağıtın.
ms.openlocfilehash: 09fd96977fbde0f546049d24b1705d27b4c92080
ms.sourcegitcommit: 22cae7ec541268d519d45518c32f22bf5811aec1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/10/2022
ms.locfileid: "63027605"
---
# <a name="step-5-device-and-app-management-for-your-microsoft-365-for-enterprise-tenants"></a>Adım 5. Kurumsal kiracılar için mobil Microsoft 365 ve uygulama yönetimi

Microsoft 365 kurumsal destek, mobil cihaz yönetimi (MDM) ve mobil uygulama yönetimi (MAM) ile cihazları ve bu cihazlarda uygulamaların kullanımını yönetmeye yardımcı olan özellikler içerir. Verileriniz dahil olmak üzere kuruluş kaynaklarınıza erişimi korumak Windows iOS, Android, macOS ve Windows cihazlarını yönetebilirsiniz. Örneğin, e-postaların kuruluş dışındakilere gönderilmesini önlenebilir veya kuruluş verilerini çalışanın kişisel cihazlarında kişisel verilerden ayırabilirsiniz.

Burada, kullanıcıların, cihazlarının doğrulanması ve yönetiminin, mobil cihazlar gibi yerel ve bulut üretkenlik uygulamalarını kullanmalarının bir Microsoft Teams.

![Kullanıcıların, cihazların ve uygulamaların doğrulanması ve yönetimi.](../media/tenant-management-overview/tenant-management-device-app-mgmt.png)

Kuruluş kaynaklarının güvenliğini sağlamanıza ve korumanıza yardımcı olmak için Microsoft 365, cihazları yönetmeye ve uygulamalara erişimlerini korumaya yardımcı olacak özellikler içerir. Cihaz yönetimi için iki seçenek vardır:

- Microsoft Intune kapsamlı bir cihaz ve uygulama yönetim çözümü olan Genel Web Uygulaması.
- Temel Mobil kullanım ve Güvenlik, tüm Kuruluş ürünleriyle birlikte kullanılan Intune hizmetlerinin bir alt kümesidir Microsoft 365 cihazları yönetmek için kullanılır. Daha fazla bilgi için bkz [. Temel Mobil Kullanım ve Güvenlik Özellikleri](../admin/basic-mobility-security/capabilities.md).

E5 veya Microsoft 365 E3 varsa Intune kullansanız gerekir.

## <a name="microsoft-intune"></a>Microsoft Intune

MDM [Microsoft Intune](/mem/intune/fundamentals/planning-guide) MAM kullanarak kuruluş erişimini yönetmek için E-Posta Yönetim'i kullanırsanız. MDM, kullanıcıların cihazlarını Intune'a "kaydettir" olduğu zamandır. Cihaz kaydettikten sonra yönetilen bir cihazdır ve kuruma yönelik ilkeleri, kuralları ve ayarları alır. Örneğin, belirli uygulamaları yükleyebilir, parola ilkesi oluşturabilir, VPN bağlantısı yükleyebilir ve daha fazlasını kullanabilirsiniz.

Kendi kişisel cihazları olan kullanıcılar cihazlarını kaydetmek istemeyebilirsiniz veya Intune ve organizasyon ilkeleri tarafından yönetilebilirsiniz. Ancak yine de kurum kaynak ve verilerini korumanız gerekir. Bu senaryoda, uygulamalarınızı MAM kullanarak koruyabilirsiniz. Örneğin, kullanıcının cihaza erişirken PIN girmesini gerektiren bir MAM SharePoint kullanabilirsiniz.

Kişisel cihazları ve kuruluşa ait cihazları nasıl yöneteceklerini de siz belirlersiniz. Cihazlara, kullanımlarına bağlı olarak farklı şekilde davranabilirsiniz.

## <a name="identity-and-device-access-configurations"></a>Kimlik ve cihaz erişimi yapılandırmaları

Microsoft, güvenli ve üretken bir iş [gücü sağlamak için kimlik ve](../security/office-365-security/microsoft-365-policies-configurations.md) cihaz erişimi için bir dizi yapılandırma sunar. Bu yapılandırmalar şunların kullanımını içerir:

- Azure AD Koşullu Erişim ilkeleri
- Microsoft Intune uyumluluk ve uygulama koruma ilkelerini koruma
- Azure AD Kimlik Koruması kullanıcı riski ilkeleri
- Bulut uygulamalarının ek ilkeleri

Kullanıcıları, cihazlarını ve masaüstü gibi yerel ve bulut üretkenlik uygulamalarını kullanmaya yönelik doğrulama ve kısıtlamaya yönelik bu ayarlar ve ilkelere örnek olarak Microsoft Teams.

![Kullanıcıların, cihazlarının ve uygulamalarının kullanımlarıyla ilgili gereksinimler ve kısıtlamalar için kimlik ve cihaz erişimi yapılandırmaları.](../media/tenant-management-overview/tenant-management-device-app-mgmt-golden-config.png)

Cihaz erişimi ve uygulama yönetimi için şu makalelerde yer alan yapılandırmaları kullanın:

- [Önkoşullar](../security/office-365-security/identity-access-prerequisites.md)
- [Ortak kimlik ve cihaz erişimi ilkeleri](../security/office-365-security/identity-access-policies.md)

## <a name="results-of-step-5"></a>Adım 5'in sonuçları

Microsoft 365 kiracınız için cihaz ve uygulama yönetimi için, kullanıcıları, cihazlarını ve yerel ve bulut üretkenlik uygulamalarının kullanımını doğrulayan ve kısıtlayan Intune ayarları ve ilkelerini belirlediniz.

Burada, Intune cihazı ve uygulama yönetiminin vurgulanmış olduğu bir kiracı örneği ve bu örnekte yer alan bir kiracı vardır.

![Intune cihazı ve uygulama yönetimine sahip bir kiracı örneği.](../media/tenant-management-overview/tenant-management-tenant-build-step5.png)

Bu çizimde, kiracının sahip olduğu:

- Intune'a kaydolan kuruluşa ait cihazlar.
- Kayıtlı ve kişisel cihazlar için Intune cihaz ve uygulama ilkeleri.

## <a name="ongoing-maintenance-for-device-and-app-management"></a>Cihaz ve uygulama yönetimi için sürekli bakım

Sürekli olarak şunları yapmak zorundayabilirsiniz: 

- Cihaz kaydı yönet'i seçin.
- Ek uygulamalar, cihazlar ve güvenlik gereksinimleri için ayarlarınızı ve ilkelerinizi düzeltin.