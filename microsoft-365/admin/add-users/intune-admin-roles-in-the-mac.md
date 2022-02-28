---
title: Intune yönetici rolleri Microsoft 365 yönetim merkezi
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
ms.openlocfilehash: 650a46c20acaf207f757ebbbe8f8b7179c29158f
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62983733"
---
# <a name="intune-admin-roles-in-the-microsoft-365-admin-center"></a>Intune yönetici rolleri Microsoft 365 yönetim merkezi

Microsoft 365 veya Office 365 aboneliğiniz, Microsoft 365 yönetim merkezi kullanarak kuruluşta kullanıcılara atayabilirsiniz bir dizi <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">yönetici rolüyle Microsoft 365 yönetim merkezi</a>. Her bir yönetici rolü, işletme ile ilgili genel işlevlere yöneliktir ve kuruluşunuzdaki kişilere, yönetim merkezlerinde belirli görevler yapma izni verir.

Bu Microsoft 365 yönetim merkezi, bazı önemli rolleri yönetmenize Microsoft Intune sağlar. Bununla birlikte, bu roller Intune yönetim merkezinde kullanılabilen rollerin bir alt kümesidir. Bu program için ayrıntılı rol açıklamalarını Microsoft Intune? Daha fazla [bilgi için rol tabanlı erişim denetimi (RBAC) Microsoft Intune](/mem/intune/fundamentals/role-based-access-control).

Kaynakta rol atama hakkında daha fazla bilgi <a href="https://go.microsoft.com/fwlink/p/?linkid=2097861" target="_blank">Microsoft 365 yönetim merkezi</a> bkz. [Yönetici rolleri atama](assign-admin-roles.md).

Ayrıntılar Microsoft 365 yönetim merkezi Roller'e **gidip** herhangi bir rolü seçerek ayrıntı bölmesini açabilirsiniz. Bu **rolü ataan** yöneticilerin yapma iznine sahip olduğu yöneticilerin ayrıntılı listesini görüntülemek için İzinler sekmesini seçin. Atanan **veya Atanan** yöneticiler **sekmesini seçerek** kullanıcıları rollere ekleyin.

## <a name="microsoft-intune-roles-available-in-the-microsoft-365-admin-center"></a>Microsoft Intune Microsoft 365 yönetim merkezi

|Yönetici rolü     |Bu role kim atanmalıdır?  |
|---------|---------|
|Uygulama yöneticisi     |   Mobil uygulamalar için uygulama yaşam döngüsünü kullanan kullanıcılara Uygulama yöneticisi rolü ata, ilke tarafından yönetilen uygulamaları yapılandırarak cihaz bilgilerini ve yapılandırma profillerini görüntüler.  |
|Yardım masası işleci     |   Kullanıcılara ve cihazlara uygulama ve ilke ataan kullanıcılara yardım masası operatörü rolü attayabilirsiniz. |
|Intune rol yöneticisi    |   Intune rol yöneticisini, Intune izinlerini diğer yöneticilere atayacak ve özel ve yerleşik Intune rollerini yönetecek kullanıcılara attayabilirsiniz.   |
|İlke ve profil yöneticisi     |   Kullanıcılara uyumluluk ilkesi, yapılandırma profilleri ve Apple kaydı yönetimi için ilke ve profil yöneticisi rolü attayabilirsiniz.   |
|Salt okunur işleci     |   Kullanıcıları, cihazları, kayıt ayrıntılarını ve yapılandırmaları yalnızca görüntüley kullanıcılara salt okunur işleç rolü attayabilirsiniz.   |
|Okul yöneticisi     |   Eğitim için Intune'da okul yöneticisi rolünü Windows 10 iOS cihazlarını, uygulamalarını ve yapılandırmalarını yönetmek için kullanıcılara tam erişim verin.   |

## <a name="delegated-administration-for-microsoft-partners"></a>Microsoft İş ortakları için temsilci yönetim

Bir Microsoft iş ortağıyla çalışıyorsanız, iş ortağınız için yönetici rolleri atayabilirsiniz. İş ortağınız da sizin şirketinizdeki ya da kendi şirketindeki kullanıcılara yönetici rolleri atayabilir. Örneğin bunu, sizin için çevrimiçi kuruluşunuzu oluşturup yönetecekse iş ortağınıza yönetici rolü atamak isteyebilirsiniz.
  
Bir iş ortağı şu rolleri atayabilir: 
  
- Genel yöneticiye eşdeğer ayrıcalıklara sahip olan ve Iş Ortağı Merkezi aracılığıyla Çok Faktörlü Kimlik Doğrulama'yı yönetme dışında tam yönetim.

- Yardım masası yöneticisiyle eşdeğer ayrıcalıklara sahip sınırlı yönetim.

İş ortağı bu rolleri kullanıcılara atamadan önce, iş ortağını hesabınıza temsili yönetici olarak eklemeniz gerekir. Bu işlem, yetkili bir iş ortağı tarafından başlatılır. İş ortağı size bir e-posta göndererek size yönetici temsilcisi olarak görev yapma izni vermek isteyip istemediğinizi sorar. Yönergeler için, bkz. [İş ortağı ilişkilerini yetkilendirme veya kaldırma](../misc/add-partner.md).
  
## <a name="related-content"></a>İlgili içerik

[Yönetici Microsoft 365 hakkında](about-admin-roles.md) (makale)\
[Yönetici rollerini atama](assign-admin-roles.md) (makale)\
[Çalışma Microsoft 365 yönetim merkezi](../activity-reports/activity-reports.md) raporları (makale)