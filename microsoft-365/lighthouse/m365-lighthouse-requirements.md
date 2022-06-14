---
title: Microsoft 365 Lighthouse için gereksinimler
f1.keywords: CSH
ms.author: sharik
author: SKjerland
manager: scotv
ms-reviewer: crimora
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
description: Yönetilen Hizmet Sağlayıcıları (MSP' ler) için Microsoft 365 Lighthouse kullanmak için gereksinimlerin listesini alın.
ms.openlocfilehash: 27d5440b70916ebdb3b761ac4308d3b97ccb27da
ms.sourcegitcommit: f181e110cdb983788a86f30d5bb018e53c83e64d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/13/2022
ms.locfileid: "66057784"
---
# <a name="requirements-for-microsoft-365-lighthouse"></a>Microsoft 365 Lighthouse için gereksinimler

Microsoft 365 Lighthouse, Yönetilen Hizmet Sağlayıcılarının (MSP' ler) küçük ve orta ölçekli işletme (SMB) müşterileri için cihazları, verileri ve kullanıcıları uygun ölçekte güvenli hale gelip yönetmelerine yardımcı olan bir yönetici portalıdır.

MSP'lerin Lighthouse kullanmak için Bulut Çözümü Sağlayıcısı (CSP) programına Dolaylı Bayi veya Doğrudan Fatura iş ortağı olarak kaydedilmesi gerekir.

Ayrıca, her MSP müşteri kiracısının aşağıdaki gereksinimleri karşılayarak Lighthouse'a uygun olması gerekir:

- Müşteri kiracısını yönetebilmek için Yönetilen Hizmet Sağlayıcısı (MSP) için temsilci erişimi ayarlanmış olmalıdır*
- En az bir Microsoft 365 İş Ekstra, Microsoft 365 E3, Microsoft 365 E5, Windows 365 Business veya İş için Microsoft Defender lisansı olmalıdır
- En fazla 2500 lisanslı kullanıcı olmalıdır

Müşterileri Lighthouse'a eklemek için Ayrıntılı Yönetici Ayrıcalıkları (GDAP) ve dolaylı bayi ilişkisi ya da Temsilci Yönetici Ayrıcalıkları (DAP) ilişkisi gerekir. MÜŞTERI kiracısında DAP ve GDAP birlikte varsa, GDAP özellikli güvenlik gruplarındaki MSP teknisyenleri için GDAP izinleri önceliklidir. Yakında yalnızca GDAP ilişkilerine (dolaylı kurumsal bayi ilişkileri olmadan) sahip müşteriler Lighthouse'a eklenecek.

## <a name="requirements-for-enabling-device-management"></a>Cihaz yönetimini etkinleştirme gereksinimleri

Cihaz yönetimi sayfalarında müşteri kiracı cihazlarını görüntülemek için bir MSP şunları yapmalıdır:

- Tüm müşteri cihazlarını Microsoft Endpoint Manager'a (MEM) kaydedin. Daha fazla bilgi için bkz[. Cihazları Microsoft Intune kaydetme](/mem/intune/enrollment/).
- Tüm müşteri cihazlarına uyumluluk ilkeleri atayın. Daha fazla bilgi için bkz. [Microsoft Intune'da uyumluluk ilkesi oluşturma](/mem/intune/protect/create-compliance-policy).

## <a name="requirements-for-enabling-user-management"></a>Kullanıcı yönetimini etkinleştirme gereksinimleri

Müşteri verilerinin Riskli kullanıcılar, Çok Faktörlü kimlik doğrulaması ve Parola sıfırlama dahil olmak üzere kullanıcı yönetimi sayfalarındaki raporlarda gösterilmesi için, müşteri kiracılarının Azure Active Directory Premium P1 veya üzeri için lisansları olmalıdır. Azure AD Premium P1 Microsoft 365 İş Ekstra ve Microsoft 365 E3 dahildir. Azure AD Premium P2 Microsoft 365 E5 dahildir.

## <a name="requirements-for-enabling-threat-management"></a>Tehdit yönetimini etkinleştirme gereksinimleri

Müşteri kiracı cihazlarını ve tehditlerini tehdit yönetimi sayfalarında görüntülemek için tüm müşteri kiracı cihazlarını Microsoft Endpoint Manager'a (MEM) kaydetmeniz ve Microsoft Defender Virüsten Koruma çalıştırarak korumanız gerekir.

Daha fazla bilgi için bkz[. Cihazları Microsoft Intune kaydetme](/mem/intune/enrollment/).

Microsoft Defender Virüsten Koruma Windows işletim sisteminin bir parçasıdır ve Windows 10 çalıştıran cihazlarda varsayılan olarak etkinleştirilir.

> [!NOTE]
> Microsoft dışı bir virüsten koruma çözümü kullanıyorsanız ve Microsoft Defender Virüsten Koruma kullanmıyorsanız, Microsoft Defender Virüsten Koruma otomatik olarak devre dışı bırakılır. Microsoft dışı virüsten koruma çözümünü kaldırdığınızda, Windows cihazlarınızı tehditlere karşı korumak için Microsoft Defender Virüsten Koruma otomatik olarak etkinleştirilir.

## <a name="related-content"></a>İlgili içerik

[Microsoft 365 Lighthouse portal güvenliğini yapılandırma](m365-lighthouse-configure-portal-security.md) (makale)\
[Microsoft 365 Lighthouse'de Cihaz uyumluluğu sayfasına genel bakış](m365-lighthouse-device-compliance-page-overview.md) (makale)\
[Microsoft 365 Lighthouse'deki Kullanıcılar sayfasına genel bakış](m365-lighthouse-users-page-overview.md) (makale)\
[Microsoft 365 Lighthouse'daki Tehdit yönetimi sayfasına genel bakış](m365-lighthouse-threat-management-page-overview.md) (makale)\
[Microsoft 365 Lighthouse SSS](m365-lighthouse-faq.yml) (makale)
