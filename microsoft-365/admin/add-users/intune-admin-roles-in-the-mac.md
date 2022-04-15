---
title: Microsoft 365 yönetim merkezi Intune yönetici rolleri hakkında
f1.keywords:
- CSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: overview
ms.service: o365-administration
ms.localizationpriority: high
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolio
- AdminTemplateSet
- admindeeplinkMAC
description: Yönetici rolleri, işletme işlevlerine eşlenir ve Yönetim merkezinde belirli görevleri yerine getirmek için izinler verir. Örneğin, Hizmet yöneticisi Microsoft’a destek bileti açar.
ms.openlocfilehash: 6ee5c8410b64bffe66ee69e5c4468a9eda601cd8
ms.sourcegitcommit: 23e186b46b27a6a4863f507a52a11105afae9726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/15/2022
ms.locfileid: "64882208"
---
# <a name="intune-admin-roles-in-the-microsoft-365-admin-center"></a>Microsoft 365 yönetim merkezi yönetici rollerini Intune

Microsoft 365 veya Office 365 aboneliğiniz, <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 yönetim merkezi</a> kullanarak kuruluşunuzdaki kullanıcılara atayabileceğiniz bir dizi yönetici rolüyle birlikte gelir. Her bir yönetici rolü, işletme ile ilgili genel işlevlere yöneliktir ve kuruluşunuzdaki kişilere, yönetim merkezlerinde belirli görevler yapma izni verir.

Microsoft 365 yönetim merkezi bazı Microsoft Intune rolleri yönetmenize olanak tanır. Ancak bu roller, Intune yönetim merkezinde bulunan rollerin bir alt kümesidir. Microsoft Intune için ayrıntılı rol açıklamalarını mı arıyorsunuz? [Microsoft Intune ile Rol tabanlı erişim denetimine (RBAC)](/mem/intune/fundamentals/role-based-access-control) göz atın.

<a href="https://go.microsoft.com/fwlink/p/?linkid=2097861" target="_blank">Microsoft 365 yönetim merkezinde</a> rol atama hakkında daha fazla bilgi için bkz. [Yönetici rolleri atama](assign-admin-roles.md).

Microsoft 365 yönetim merkezi **Roller'e** gidip herhangi bir rolü seçerek ayrıntı bölmesini açabilirsiniz. Bu role atanan yöneticilerin neler yapmaya izninin olduğu ayrıntılı listeyi görüntülemek için **İzinler** sekmesini seçin. **Atanan** veya **Atanan yöneticiler** sekmesini seçerek kullanıcıları rollere ekleyin.

## <a name="microsoft-intune-roles-available-in-the-microsoft-365-admin-center"></a>Microsoft Intune Rolleri Microsoft 365 yönetim merkezi

|Yönetici rolü     |Bu role kim atanmalıdır?  |
|---------|---------|
|Uygulama yöneticisi     |   Uygulama yöneticisi rolünü mobil uygulamalar için uygulama yaşam döngüsünü yöneten, ilkeyle yönetilen uygulamaları yapılandıran ve cihaz bilgilerini ve yapılandırma profillerini görüntüleyen kullanıcılara atayın.  |
|Yardım masası operatörü     |   Kullanıcılara ve cihazlara uygulama ve ilke atayan kullanıcılara yardım masası operatörü rolünü atayın. |
|Intune rol yöneticisi    |   Intune rol yöneticisini, diğer yöneticilere Intune izinleri atayabilen ve özel ve yerleşik Intune rollerini yönetebilen kullanıcılara atayın.   |
|İlke ve profil yöneticisi     |   Uyumluluk ilkesini, yapılandırma profillerini ve Apple kaydını yöneten kullanıcılara ilke ve profil yöneticisi rolünü atayın.   |
|Salt okunur işleç     |   Salt okunur işleç rolünü yalnızca kullanıcıları, cihazları, kayıt ayrıntılarını ve yapılandırmaları görüntüleyebilen kullanıcılara atayın.   |
|Okul yöneticisi     |   Eğitim için Intune'da Windows 10 ve iOS cihazlarını, uygulamalarını ve yapılandırmalarını yönetmek için kullanıcılara tam erişim için okul yöneticisi rolünü atayın.   |

## <a name="delegated-administration-for-microsoft-partners"></a>Microsoft İş ortakları için temsilci yönetim

Bir Microsoft iş ortağıyla çalışıyorsanız, iş ortağınız için yönetici rolleri atayabilirsiniz. İş ortağınız da sizin şirketinizdeki ya da kendi şirketindeki kullanıcılara yönetici rolleri atayabilir. Örneğin bunu, sizin için çevrimiçi kuruluşunuzu oluşturup yönetecekse iş ortağınıza yönetici rolü atamak isteyebilirsiniz.
  
Bir iş ortağı şu rolleri atayabilir: 
  
- Genel yöneticiye eşdeğer ayrıcalıklara sahip olan ve Iş Ortağı Merkezi aracılığıyla Çok Faktörlü Kimlik Doğrulama'yı yönetme dışında tam yönetim.

- Yardım masası yöneticisiyle eşdeğer ayrıcalıklara sahip sınırlı yönetim.

İş ortağı bu rolleri kullanıcılara atamadan önce, iş ortağını hesabınıza temsili yönetici olarak eklemeniz gerekir. Bu işlem, yetkili bir iş ortağı tarafından başlatılır. İş ortağı size bir e-posta göndererek size yönetici temsilcisi olarak görev yapma izni vermek isteyip istemediğinizi sorar. Yönergeler için, bkz. [İş ortağı ilişkilerini yetkilendirme veya kaldırma](../misc/add-partner.md).
  
## <a name="related-content"></a>İlgili içerik

[Microsoft 365 yönetici rolleri hakkında](about-admin-roles.md) (makale)\
[Yönetici rollerini atama](assign-admin-roles.md) (makale)\
[Microsoft 365 yönetim merkezi etkinlik raporları](../activity-reports/activity-reports.md) (makale)
