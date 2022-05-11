---
title: Farklı cihaz ve uygulama veri koruma yöntemlerini karşılaştırma
f1.keywords:
- NOCSH
ms.author: sharik
author: skjerland
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
search.appverid:
- MET150
description: Farklı MDM ve MAM yöntemleri arasında seçim yapın.
ms.openlocfilehash: 49c8fe8e61026e56b1698d7da2fdbac07896c858
ms.sourcegitcommit: 7dc7e9fd76adf848f941919f86ca25eecc704015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/11/2022
ms.locfileid: "65317504"
---
# <a name="options-for-protecting-your-devices-and-app-data"></a>Cihazlarınızı ve uygulama verilerinizi korumaya yönelik seçenekler

İşletmeler ve kuruluşlar için Microsoft 365 ile kuruluşunuzun cihaz ve verilerinin güvenliğini sağlamanın çeşitli yolları vardır. Aşağıdaki tek başına planları kullanabilirsiniz:

- Intune (Microsoft Endpoint Management'ın bir parçası)
- planları Azure Active Directory Premium.
- Temel Mobilite ve Güvenlik (iş ve kurumsal planlar için çoğu Microsoft 365 dahildir) Veya önceki tek başına planların bazılarını veya tümünü içeren abonelikleri kullanın.
- İş için Microsoft Defender (Microsoft 365 İş Ekstra dahil; tek başına plan olarak da kullanılabilir)
- 300 kullanıcıdan küçük işletmeler için güvenlik ve tehdit koruması içeren bir Microsoft 365 İş Ekstra aboneliği.
- Gelişmiş güvenlik ve tehdit koruması içeren planları Microsoft 365 Kurumsal.

## <a name="device-management-options"></a>Cihaz yönetimi seçenekleri

- **Temel Mobilite ve Güvenlik** çoğu Microsoft 365 planıyla sunulur ve Microsoft 365 İş Standart ve Microsoft 365 İş Temel için sunulan tek yerleşik seçenektir. Daha fazla bilgi için bkz. [Basic Mobility ve Security'nin kullanılabilirliği](../basic-mobility-security/choose-between-basic-mobility-and-security-and-intune.md#availability-of-basic-mobility-and-security-and-intune). 

    Microsoft 365 İş Temel veya Microsoft 365 İş Standart varsa, kuruluşunuzun daha karmaşık güvenlik gereksinimleri varsa Intune de satın alabilirsiniz.
 
- **Microsoft Intune**, iş veya kurumsal planlara yönelik bazı Microsoft 365 de dahil olan tek başına bir plandır. Tek başına veya aboneliğinizin bir parçası olarak Intune sahipseniz, cihazınıza ve uygulama veri yönetimine ince ayar yapabilmenizi sağlar. Microsoft 365 kullanılabilirliği hakkında daha fazla bilgi için bkz. [Intune kullanılabilirliği](../basic-mobility-security/choose-between-basic-mobility-and-security-and-intune.md#availability-of-basic-mobility-and-security-and-intune).

    Microsoft Intune, mobil cihaz yönetimine (MDM) ve mobil uygulama yönetimine (MAM) odaklanan bulut tabanlı bir hizmettir. Cep telefonları, tabletler ve dizüstü bilgisayarlar dahil olmak üzere kuruluşunuzun cihazlarının nasıl kullanıldığını siz denetlersiniz. Uygulamaları denetlemek için belirli ilkeleri de yapılandırabilirsiniz. Daha fazla bilgi [için Microsoft Intune belgelerine bakın](/mem/intune/).

- **Azure Active Directory (AD) Premium** planları, iş ve kurumsal planlar için Microsoft 365 bazılarıyla birlikte gelen tek başına planlardır. Daha fazla bilgi için bkz. [fiyatlandırma Azure AD](https://azure.microsoft.com/pricing/details/active-directory/).

     Azure AD Premium P1 ve Azure AD Premium P2 koşullu erişim özellikleri, self servis parola sıfırlama vb. ayarlamanızı sağlar. Premium planlarının özellikleri hakkında daha fazla bilgi için Azure AD [fiyatlandırma](https://azure.microsoft.com/pricing/details/active-directory/) sayfasına bakın.

- **Microsoft 365 İş Ekstra** Intune ve Azure Active Directory Premium P1, Office 365 için Microsoft Defender Plan 1 ve İş için Microsoft Defender. 
 
    Microsoft 365 İş Ekstra, cihazlarınızın ve uygulama verilerinizin güvenliğini sağlamak için bir dizi ilke şablonu sunar. 300'ün altındaki çoğu işletme için iyi bir güvenlik ve tehdit koruması sunar. Daha fazla bilgi için bkz. [Microsoft 365 İş Ekstra Genel Bakış](../../business-premium/index.md) ve [İş için Microsoft Defender Genel Bakış](../../security/defender-business/mdb-overview.md).

- Kurumsal abonelikler **için Microsoft 365** Microsoft Intune ve E5 de Azure AD premium plan 1 ve 2'yi içerir.

    Microsoft 365 E5, tüm Microsoft 365 abonelikleri için en yüksek güvenlik ve tehdit koruması düzeyini sunar. Daha fazla bilgi için bkz. [kuruluşa genel bakış için Microsoft 365](../../enterprise/microsoft-365-overview.md).

## <a name="see-also"></a>Ayrıca bkz.

[İş planları için Microsoft 365 güvenliğini sağlamaya yönelik en iyi yöntemler](../security-and-compliance/secure-your-business-data.md)