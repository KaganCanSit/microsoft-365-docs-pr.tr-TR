---
title: Kullanıcı ve cihaz erişimini koruma
f1.keywords:
- NOCSH
ms.author: bcarter
author: brendacarter
manager: laurawi
ms.date: 4/17/2018
audience: Admin
ms.topic: landing-page
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MOE150
- MET150
ms.assetid: a6ef28a4-2447-4b43-aae2-f5af6d53c68e
description: Microsoft 365 veri ve hizmetlerine kullanıcı ve cihaz erişimini korumayı ve veri kaybına karşı korumayı öğrenin.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: f8b6b266d037e8bbc185643e530bf7a2f6919038
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66623726"
---
# <a name="protect-user-and-device-access"></a>Kullanıcı ve cihaz erişimini koruma

Microsoft 365 verilerinize ve hizmetlerinize erişimi korumak, siber saldırılara karşı savunmak ve veri kaybına karşı korunmak için çok önemlidir. Aynı korumalar ortamınızdaki diğer SaaS uygulamalarına ve hatta Azure Active Directory Uygulama Ara Sunucusu ile yayımlanan şirket içi uygulamalara da uygulanabilir.
  
## <a name="step-1-review-recommendations"></a>1. Adım: Önerileri gözden geçirme

Azure AD Uygulama Ara Sunucusu ile yayımlanan Office 365, diğer SaaS hizmetlerine ve şirket içi uygulamalara erişen kimlikleri ve cihazları korumaya yönelik önerilen özellikler.
  
[PDF](https://go.microsoft.com/fwlink/p/?linkid=841656) |  [Visio](https://go.microsoft.com/fwlink/p/?linkid=841657) |  [Diğer diller](https://www.microsoft.com/download/details.aspx?id=55032)
  
## <a name="step-2-protect-administrator-accounts-and-access"></a>2. Adım: Yönetici hesaplarını ve erişimi koruma

Microsoft 365 ortamınızı yönetmek için kullandığınız yönetim hesapları yükseltilmiş ayrıcalıklar içerir. Bunlar bilgisayar korsanları ve siber saldırganlar için değerli hedeflerdir.

Yalnızca yönetim için yönetici hesaplarını kullanarak başlayın. Yöneticilerin düzenli ve yönetici olmayan kullanım için ayrı bir kullanıcı hesabı olmalıdır ve yalnızca iş işleviyle ilişkili bir görevi tamamlamak için gerektiğinde yönetim hesaplarını kullanmalıdır.

Çok faktörlü kimlik doğrulaması ve koşullu erişim ile yönetici hesaplarınızı koruyun. Daha fazla bilgi için bkz. [Yönetici hesaplarını koruma](../security/office-365-security/identity-access-prerequisites.md#protecting-administrator-accounts). 

Ardından Microsoft Purview Privileged Access Management'ı yapılandırın. Ayrıcalıklı erişim yönetimi, Office 365'daki ayrıcalıklı yönetici görevleri üzerinde ayrıntılı erişim denetimine olanak tanır. Kuruluşunuzun hassas verilere veya kritik yapılandırma ayarlarına erişimi olan mevcut ayrıcalıklı yönetici hesaplarını kullanabilecek ihlallere karşı korunmasına yardımcı olabilir.

- [Ayrıcalıklı erişim yönetimine genel bakış](privileged-access-management.md)
- [Ayrıcalıklı erişim yönetimini yapılandırma](privileged-access-management-configuration.md)

Bir diğer önemli öneri de, özellikle yönetim çalışmaları için yapılandırılmış iş istasyonlarını kullanmaktır. Bunlar yalnızca yönetim görevleri için kullanılan ayrılmış cihazlardır. Bkz [. Ayrıcalıklı erişimin güvenliğini sağlama](/windows-server/identity/securing-privileged-access/securing-privileged-access).

Son olarak, kiracınızda iki veya daha fazla acil durum erişim hesabı oluşturarak yanlışlıkla yönetim erişimi eksikliğinin etkisini azaltabilirsiniz. Bkz. [Azure AD'de acil durum erişim hesaplarını yönetme](/azure/active-directory/users-groups-roles/directory-emergency-access). 

## <a name="step-3-configure-recommended-identity-and-device-access-policies"></a>3. Adım: Önerilen kimlik ve cihaz erişim ilkelerini yapılandırma

Çok faktörlü kimlik doğrulaması (MFA) ve koşullu erişim ilkeleri, güvenliği aşılmış hesaplara ve yetkisiz erişime karşı azaltmaya yönelik güçlü araçlardır. Birlikte test edilmiş bir dizi ilkenin uygulanmasını öneririz. Dağıtım adımları da dahil olmak üzere daha fazla bilgi için bkz. [Kimlik ve cihaz erişim yapılandırmaları](../security/office-365-security/microsoft-365-policies-configurations.md).

 Bu ilkeler aşağıdaki özellikleri uygular:

- Çok faktörlü kimlik doğrulaması
- Koşullu erişim
- Intune uygulama koruması (cihazlar için uygulama ve veri koruması)
- cihaz uyumluluğunu Intune
- Azure AD Kimlik Koruması

Intune cihaz uyumluluğu uygulamak için cihaz kaydı gerekir. Cihazları yönetmek, ortamınızdaki kaynaklara erişmelerine izin vermeden önce iyi ve uyumlu olduklarından emin olmanıza olanak tanır. Bkz[. Intune'de yönetim için cihazları kaydetme](/mem/intune/user-help/enroll-windows-10-device)

## <a name="step-4-configure-sharepoint-device-access-policies"></a>4. Adım: SharePoint cihaz erişim ilkelerini yapılandırma

Microsoft, SharePoint sitelerindeki içeriği hassas ve yüksek oranda düzenlenmiş içerikle cihaz erişim denetimleriyle korumanızı önerir. Daha fazla bilgi için bkz. [SharePoint sitelerinin ve dosyalarının güvenliğini sağlamaya yönelik ilke önerileri](../security/office-365-security/sharepoint-file-access-policies.md).
