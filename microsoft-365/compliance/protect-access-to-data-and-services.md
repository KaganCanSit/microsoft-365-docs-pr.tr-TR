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
description: Verileri ve hizmetleri korumak ve veri kaybına karşı korumak Microsoft 365 ve cihaz erişimini korumayı öğrenin.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 48f483422fda158c02429aec642f60e05b8c933a
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2022
ms.locfileid: "63679598"
---
# <a name="protect-user-and-device-access"></a>Kullanıcı ve cihaz erişimini koruma

Yeni verilerinizin ve hizmetlerinizin Microsoft 365 siber saldırılara karşı savunma ve veri kaybına karşı koruma açısından çok önemlidir. Aynı korumalar ortamınız içinde diğer SaaS uygulamalarına, hatta Azure Active Directory Uygulama Ara Sunucusu ile yayımlanan şirket içi uygulamalara da uygulanabilir.
  
## <a name="step-1-review-recommendations"></a>1. Adım: Önerileri gözden geçirme

Azure AD Uygulama Ara Sunucusu ile yayımlanan Office 365, diğer SaaS hizmetleri ve şirket içi uygulamalara erişen kimlikleri ve cihazları korumak için önerilen özellikler.
  
[PDF](https://go.microsoft.com/fwlink/p/?linkid=841656) |  [](https://go.microsoft.com/fwlink/p/?linkid=841657) |  Visio [More languages](https://www.microsoft.com/download/details.aspx?id=55032)
  
## <a name="step-2-protect-administrator-accounts-and-access"></a>2. Adım: Yönetici hesaplarını ve erişimini koruma
Ortamınızı yönetmek için kullanabileceğiniz yönetim hesapları Microsoft 365 yükseltilmiş ayrıcalıklar içerir. Bunlar korsanlar ve siber saldırıların değerli hedefleridir. 

Başlangıç olarak, yönetici hesaplarını yalnızca yönetim için kullansın. Yöneticilerin normal, yönetim dışı kullanım için ayrı bir kullanıcı hesabına sahip olması ve yalnızca görevleriyle ilişkilendirilmiş bir görevi tamamlamak için gerektiğinde yönetim hesaplarını kullanmaları gerekir.

Çok faktörlü kimlik doğrulaması ve koşullu erişimle yönetici hesaplarınızı koruyun. Daha fazla bilgi için bkz [. Yönetici hesaplarını koruma](../security/office-365-security/identity-access-prerequisites.md#protecting-administrator-accounts). 

Ardından, aynı konumda ayrıcalıklı erişim yönetimini Office 365. Ayrıcalıklı erişim yönetimi, aynı konumdaki ayrıcalıklı yönetici görevleri üzerinde ayrıntılı erişim Office 365. Bu, hassas verilere ayakta erişim veya kritik yapılandırma ayarlarına erişimle, var olan ayrıcalıklı yönetici hesaplarının kullanılamalarına neden olan ihlallere karşı kuruluşu korumaya yardımcı olabilir.

- [Ayrıcalıklı erişim yönetimine genel bakış](privileged-access-management-overview.md)
- [Ayrıcalıklı erişim yönetimini yapılandırma](privileged-access-management-configuration.md)

Bir diğer önemli öneri de, özellikle yönetim işi için yapılandırılmış iş istasyonları kullanmaktır. Bunlar, yalnızca yönetim görevleri için kullanılan ayrılmış cihazlardır. Bkz [. Ayrıcalıklı erişimin güvenliğini sağlama](/windows-server/identity/securing-privileged-access/securing-privileged-access).

Son olarak, kiracıda iki veya daha fazla acil durum erişim hesabı oluşturarak, yönetim erişiminin istemeden ortaya olmaması etkisini azaltmak için bir yol vardır. Bkz [. Azure AD'de acil durum erişim hesaplarını yönetme](/azure/active-directory/users-groups-roles/directory-emergency-access). 

## <a name="step-3-configure-recommended-identity-and-device-access-policies"></a>3. Adım: Önerilen kimlik ve cihaz erişimi ilkelerini yapılandırma
Çok faktörlü kimlik doğrulaması (MFA) ve koşullu erişim ilkeleri güvenliği ihlal edilmiş hesaplara ve yetkisiz erişime karşı risk azaltmaya yönelik güçlü araçlardır. Birlikte test edilmiş bir dizi ilkeyi uygulamanizi öneririz. Dağıtım adımları da dahil olmak üzere daha fazla bilgi için bkz. [Kimlik ve cihaz erişimi yapılandırmaları](../security/office-365-security/microsoft-365-policies-configurations.md).

 Bu ilkeler aşağıdaki özellikleri benimser:
- Çok faktörlü kimlik doğrulaması
- Koşullu erişim
- Intune uygulama koruması (cihazlar için uygulama ve veri koruması)
- Intune cihaz uyumluluğu
- Azure AD Identity Protection

Intune cihaz uyumluluğunu uygulamak için cihaz kaydı gerekir. Cihazları yönetme, ortamınız içinde yer alan kaynaklara erişmelerine izin vermeden önce sağlıklı ve uyumlu olduğundan emin olamanıza olanak tanır. Bkz [. Intune'da yönetim için cihazları kaydetme](/mem/intune/user-help/enroll-windows-10-device)

## <a name="step-4-configure-sharepoint-device-access-policies"></a>4. Adım: Cihaz SharePoint ilkelerini yapılandırma

Microsoft, cihaz erişim denetimleriyle hassas SharePoint düzenlemeye tabi içeriği olan tüm sitelerde yer alan içeriği korumanıza izin verir. Daha fazla bilgi için bkz[. Site ve dosyaların güvenliğini SharePoint ilke önerileri](../security/office-365-security/sharepoint-file-access-policies.md).



