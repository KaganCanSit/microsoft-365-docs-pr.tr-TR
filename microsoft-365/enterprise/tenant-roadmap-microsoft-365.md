---
title: Microsoft 365 için kiracı yol haritası
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: scotv
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- m365initiative-coredeploy
ms.custom: it-pro
description: Microsoft 365 için kiracılarınızı ayarlamaya yönelik yol haritası.
ms.openlocfilehash: 85695c38f724f215192d7659963c35f25b006dc5
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65092061"
---
# <a name="tenant-roadmap-for-microsoft-365"></a>Microsoft 365 için kiracı yol haritası

Microsoft 365 kiracınız, kuruluşunuza atanan hizmet kümesidir. Genellikle, bu kiracı bir veya daha fazla genel DNS etki alanı adınızla ilişkilendirilir ve farklı abonelikler ve kullanıcı hesaplarına atadığınız lisanslar için merkezi ve yalıtılmış bir kapsayıcı görevi görür. Daha fazla bilgi için bkz. [Microsoft'un bulut teklifleri için abonelikler, lisanslar, hesaplar ve kiracılar](subscriptions-licenses-accounts-and-tenants-for-microsoft-cloud-offerings.md).

Microsoft 365 kiracı oluşturduğunuzda, kiracıyı belirli bir coğrafi konuma atarsınız. Ayrıca birden çok coğrafi konuma sahip bir kiracınız olabilir ve kiracınızı bir konumdan diğerine taşıyabilirsiniz.

Kiracınızı kullanıcı, gruplar, lisanslar ve bulut uygulamalarına hazırlamak için kiracı yapılandırmanızı dikkatle planlamak ve yürütmek kritik önem taşır.

## <a name="set-up-your-microsoft-365-tenant"></a>Microsoft 365 kiracınızı ayarlama

Ağınızın hem şirket içi hem de uzak çalışanlar için Microsoft 365 erişim için iyileştirildiğinden emin olduktan sonra, sonraki büyük görevleriniz Microsoft 365 kiracınızı DNS etki alanı adları, ortak hizmetler ve güvenli kullanıcı oturum açmasını destekleyen kimlik altyapısı için planlayıp yapılandırıyor.

### <a name="plan"></a>Plan

Kiracı uygulamanızı planlamak için:

- [Abonelikleri, lisansları ve Azure Active Directory (Azure AD) kiracılarını anlama](subscriptions-licenses-accounts-and-tenants-for-microsoft-cloud-offerings.md)
- [Üçüncü taraf SSL sertifikalarının nasıl kullanılacağını anlama](plan-for-third-party-ssl-certificates.md)
- [Microsoft 365 kiracısının Azure AD hizmetleriyle tümleştirme yöntemlerini anlama](integrated-apps-and-azure-ads.md)
- [İstemci uygulaması desteğini planlama](microsoft-365-client-support-certificate-based-authentication.md)
- [Karma modern kimlik doğrulamasının nasıl kullanılacağını belirleme](hybrid-modern-auth-overview.md)
- [Office 2007 ve Office 2010 yükseltmelerini planlama](plan-upgrade-previous-versions-office.md)
- [Kiracı yalıtımını anlama](/compliance/assurance/microsoft-365-isolation-controls)

### <a name="deploy"></a>Dağıtım

Kiracınızı dağıtmak için: 

- Kuruluşunuz için [DNS etki alanlarını](../admin/setup/add-domain.md) ekleyin.
- [Microsoft 365 yönetim merkezi kurulum kılavuzlarını](setup-guides-for-microsoft-365.md) kullanın.
- [Kimlik altyapınızı](deploy-identity-solution-overview.md) oluşturun.

### <a name="move-a-tenants-geographic-locations"></a>Kiracının coğrafi konumlarını taşıma

Microsoft, Microsoft 365 hizmetleri için yeni veri merkezi coğrafi konumları (coğrafi konumlar) açmaya devam ediyor. Bu yeni veri merkezi coğrafi alanları, müşteri talebini ve kullanım artışlarını desteklemek için kapasite ve işlem kaynakları ekler. Ayrıca yeni veri merkezi coğrafi bölgeleri, temel müşteri verileri için coğrafi veri yerleşimi sunar.

Daha fazla bilgi için bkz[. Çekirdek verileri yeni Microsoft 365 veri merkezi coğrafi bölgelerine taşıma](moving-data-to-new-datacenter-geos.md).


## <a name="deploy-microsoft-365-multi-geo"></a>Multi-Geo Microsoft 365 dağıtma

Microsoft 365 Multi-Geo ile kuruluşunuz, Microsoft 365 varlığını mevcut kiracınızdaki birden çok coğrafi bölgeye ve/veya ülkeye genişletebilir.

Daha fazla bilgi için bkz[. Multi-Geo Microsoft 365](microsoft-365-multi-geo.md).

## <a name="manage-multiple-microsoft-365-tenants"></a>Birden çok Microsoft 365 kiracıyı yönetme 

Oganizasyonunuz için tek bir kiracınız olması ideal olsa da, birden çok kiracısı olan birçok kuruluş arasında yer alabilirsiniz. Nedenler arasında birleşmeler ve devralmalar olabilir, yönetim yalıtımı isteyebilirsiniz veya merkezi olmayan bir BT'niz olabilir.

Birden çok Microsoft 365 kiracınız varsa, aşağıdakiler hakkında daha fazla bilgi için şu makalelere bakın:

- [Kiracılar arası işbirliği](microsoft-365-inter-tenant-collaboration.md)
- [Kiracılar arası posta kutusu geçişi](cross-tenant-mailbox-migration.md)
- [Kiracıdan kiracıya geçişler](microsoft-365-tenant-to-tenant-migrations.md)

## <a name="next-step"></a>Sonraki adım

[Abonelikler, lisanslar, hesaplar ve kiracılar ile kiracı](subscriptions-licenses-accounts-and-tenants-for-microsoft-cloud-offerings.md) planlamanızı başlatın.