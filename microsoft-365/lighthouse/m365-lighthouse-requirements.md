---
title: Sistem gereksinimleri Microsoft 365 Lighthouse
f1.keywords: CSH
ms.author: sharik
author: SKjerland
manager: scotv
audience: Admin
ms.topic: article
ms.prod: microsoft-365-lighthouse
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolio
- M365-Lighthouse
search.appverid: MET150
description: Yönetilen Hizmet Sağlayıcıları (MSP)'ler için, Hizmet Sağlayıcılarını (MSP) kullanmak Microsoft 365 Lighthouse.
ms.openlocfilehash: 8a502e056d570ef81e1bdb02321f0492c2b50395
ms.sourcegitcommit: 0ee2dabe402d44fecb6856af98a2ef7720d25189
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/09/2021
ms.locfileid: "62998888"
---
# <a name="requirements-for-microsoft-365-lighthouse"></a>Sistem gereksinimleri Microsoft 365 Lighthouse

> [!NOTE]
> Bu makalede açıklanan özellikler Önizleme'dedir, değişebilir ve yalnızca bu makalede listelenen gereksinimleri karşılayacak iş ortakları tarafından kullanılabilir. Henüz oturum açmadıysanız Microsoft 365 Lighthouse için [kaydolma'ya Microsoft 365 Lighthouse](m365-lighthouse-sign-up.md).

Microsoft 365 Lighthouse Küçük ve orta ölçekli işletme (SMB) müşterileri için, Yönetilen Hizmet Sağlayıcılarının (MSP) cihazları, verileri ve kullanıcıları güvenli ve yönetmeye yardımcı olan bir yönetici portalıdır.  

MSP'ler, Deniz Bulut Çözümü Sağlayıcısı'ı kullanmak için Bulut Çözümü Sağlayıcısı (CSP) programına Dolaylı Bayi veya Doğrudan Fatura iş ortağı olarak kaydolmaları gerekir.  

Buna ek olarak, her MSP müşteri kiracısı aşağıdaki gereksinimleri karşıerek Deniz Feneri'ne hak kazanmakla hak kazanmakla da gerekir: 
 
- MSP için Temsili Yönetici Ayrıcalıkları (DAP) 
- En az bir Microsoft 365 İş Ekstra veya Microsoft 365 E3 lisansı 
- 500'den az lisanslı kullanıcı  

## <a name="requirements-for-enablingdevice-management"></a>Cihaz yönetimini etkinleştirme gereksinimleri   

Cihaz yönetimi sayfalarında müşteri kiracı cihazlarını görüntülemek için MSP'nin aşağıdakiler gerekir:    

- Tüm müşteri cihazlarını Microsoft Endpoint Manager (MEM) olarak kaydettir.Daha fazla bilgi için bkz[. Cihazları Microsoft Intune](/mem/intune/enrollment/).
- Tüm müşteri cihazlarına uyumluluk ilkeleri attayabilirsiniz.Daha fazla bilgi için bkz[. 2013'te uyumluluk Microsoft Intune](/mem/intune/protect/create-compliance-policy). 

## <a name="requirements-for-enabling-usermanagement"></a>Kullanıcı yönetimini etkinleştirme gereksinimleri 

Müşteri verilerini, Risky kullanıcıları, Çok Faktörlü kimlik doğrulaması ve Parola sıfırlama gibi kullanıcı yönetimi sayfalarında gösteriymleri için, müşteri kiracılarının Azure Active Directory Premium P1 veya sonrası için lisansları olmalıdır. Azure AD Premium P1, e-Microsoft 365 İş Ekstra ve Microsoft 365 E3.   

## <a name="requirements-for-enablingthreat-management"></a>Tehdit yönetimini etkinleştirme gereksinimleri 

Müşteri kiracı cihazlarını ve tehdit sayfalarını görüntülemek için, tüm müşteri kiracı cihazlarını Microsoft Endpoint Manager'a (MEM) kaydetmeniz ve diğer cihazlara çalıştırarak onları korumanız Microsoft Defender Virüsten Koruma.  

Daha fazla bilgi için bkz[. Cihazları Microsoft Intune](/mem/intune/enrollment/).  

Microsoft Defender Virüsten Koruma, Windows sisteminin bir parçasıdır ve işletim sistemini çalıştıran cihazlarda varsayılan olarak Windows 10.  

> [!NOTE] 
> Microsoft dışı bir virüsten koruma çözümü kullanıyor ve herhangi bir çözüm Microsoft Defender Virüsten Koruma, Microsoft Defender Virüsten Koruma devre dışı bırakılır. Microsoft olmayan virüsten koruma çözümünü kaldırdığınız zaman, Microsoft Defender Virüsten Koruma cihazlarınızı tehditlere karşı korumak için Windows etkinleştirilir.    

## <a name="related-content"></a>İlgili içerik   

[Portal Microsoft 365 Lighthouse yapılandırma](m365-lighthouse-configure-portal-security.md) (makale)\
[Microsoft 365 Lighthouse Uyumluluk sayfasına genel bakış](m365-lighthouse-device-compliance-page-overview.md) (makale)\
[Microsoft 365 Lighthouse sayfasına genel bakış](m365-lighthouse-users-page-overview.md) (makale)\
[Microsoft 365 Lighthouse yönetimi sayfasına genel bakış](m365-lighthouse-threat-management-page-overview.md) (makale)\
[Microsoft 365 Lighthouse SSS](m365-lighthouse-faq.yml) (makale)

