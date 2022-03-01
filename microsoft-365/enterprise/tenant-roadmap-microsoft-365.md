---
title: Kiracı yol haritası Microsoft 365
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- m365initiative-coredeploy
ms.custom: it-pro
description: Kiracılarınızı daha iyi ayarlamak için yol Microsoft 365.
ms.openlocfilehash: 180f7f998819986d05febe6ae19877da290d20a5
ms.sourcegitcommit: 6c57f1e90339d5a95c9e7875599dac9d3e032c3a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/04/2022
ms.locfileid: "63016457"
---
# <a name="tenant-roadmap-for-microsoft-365"></a>Kiracı yol haritası Microsoft 365

Kiracı Microsoft 365 kiracınız, organizasyona atanan hizmet kümesidir. Normalde, bu kiracı genel DNS etki alanı adlardan bir veya birkaçla ilişkilendirilır ve farklı abonelikler ve kullanıcı hesaplarına atadığınız farklı abonelikler ve içindeki lisanslar için merkezi ve yalıtılmış bir kapsayıcı olarak davranır. Daha fazla bilgi için bkz [. Microsoft'un bulut teklifleri için abonelikler, lisanslar, hesaplar ve kiracılar](subscriptions-licenses-accounts-and-tenants-for-microsoft-cloud-offerings.md).

Yeni bir kiracı Microsoft 365, bunu belirli bir coğrafi konuma atar. Ayrıca, birden çok coğrafi konumu olan bir kiracınız olabilir ve kiracınızı bir konumdan diğerine de taşıabilirsiniz.

Kiracınızı kullanıcı, gruplar, lisanslar ve bulut uygulamalarına hazır hale almak için, kiracı yapılandırmanızı dikkatle planlamak ve yürütmek çok önemlidir.

## <a name="set-up-your-microsoft-365-tenant"></a>Kiracınızı Microsoft 365 ayarlama

Ağ bağlantılarının hem şirket içi hem de uzak çalışanlar için Microsoft 365 erişimi için en iyi duruma getirilmiş olduğundan emin olduktan sonra, bir sonraki büyük görevleriniz DNS etki alanı adları, ortak hizmetler ve güvenli kullanıcı oturum açma desteği olan bu kimlik altyapısı için Microsoft 365 kiracınızı planlamak ve yapılandırmaktır.

### <a name="plan"></a>Plan

Kiracı uygulamanızı planlamak için:

- [Abonelikleri, lisansları ve Azure Active Directory (Azure AD) kiracılarını anlama](subscriptions-licenses-accounts-and-tenants-for-microsoft-cloud-offerings.md)
- [Üçüncü taraf SSL sertifikalarını kullanmayı anlama](plan-for-third-party-ssl-certificates.md)
- [Bir kiracının Azure AD Microsoft 365 ile tümleşik olan yollarını anlama](integrated-apps-and-azure-ads.md)
- [İstemci uygulaması desteğini planlama](microsoft-365-client-support-certificate-based-authentication.md)
- [Karma modern kimlik doğrulamanın nasıl kullanıla birlikte kullanılasını belirleme](hybrid-modern-auth-overview.md)
- [2007 Office 2010 yükseltmelerini Office planlama](plan-upgrade-previous-versions-office.md)
- [Kiracı yalıtımı anlama](/compliance/assurance/microsoft-365-isolation-controls)

### <a name="deploy"></a>Dağıtma

Kiracınızı dağıtmak için: 

- Dns etki [alanlarını organizasyonunız](../admin/setup/add-domain.md) için ekleyin.
- Aşağıdaki [kılavuzlarda yer alan kurulum Microsoft 365 yönetim merkezi](setup-guides-for-microsoft-365.md).
- Kimlik [altyapınızı oluşturma](deploy-identity-solution-overview.md).

### <a name="move-a-tenants-geographic-locations"></a>Kiracının coğrafi konumlarını taşıma

Microsoft, coğrafi hizmetler için yeni veri merkezi coğrafi konumlarını (geos) açmaya Microsoft 365 devam eder. Bu yeni veri merkezi, müşteri talebi ve kullanım artışlarını desteklemek için kapasite ve bilgi işlem kaynakları ekler. Buna ek olarak, yeni veri merkezi coğrafi konum, çekirdek müşteri verileri için coğrafi olarak yer sağlar.

Daha fazla bilgi için bkz[. Temel verileri yeni veri Microsoft 365 coğrafilere taşıma](moving-data-to-new-datacenter-geos.md).


## <a name="deploy-microsoft-365-multi-geo"></a>Multi-Geo Microsoft 365'i dağıtma

Birden Microsoft 365 Multi-Geo'ya sahip olan organizasyonu, Microsoft 365 kiracı içinde birden çok coğrafi bölgeye ve/veya ülkeye genişletip kullanılabilir.

Daha fazla bilgi için bkz[. Microsoft 365 Multi-Geo](microsoft-365-multi-geo.md).

## <a name="manage-multiple-microsoft-365-tenants"></a>Birden çok Microsoft 365 kiracıyı yönetme 

Kiracınız için tek bir kiracı olması ideal bir neden olsa da, birden çok kiracısı olan birçok kuruluştan biri olabilirsiniz. Şirket birleşmeleri ve alımları, yönetimsel yalıtım isteme veya kurumsal bir IT'ye sahip olmak gibi nedenleri olabilir.

Birden çok kiracınız Microsoft 365 daha fazla bilgi için şu makalelere bakın:

- [Kiracılar arası işbirliği](microsoft-365-inter-tenant-collaboration.md)
- [Kiracılar arası posta kutusu geçişi](cross-tenant-mailbox-migration.md)
- [Kiracıdan kiracıya geçişler](microsoft-365-tenant-to-tenant-migrations.md)

## <a name="next-step"></a>Sonraki adım

Abonelikler, [lisanslar, hesaplar ve kiracılar ile kiracı planlamanızı başlatabilirsiniz](subscriptions-licenses-accounts-and-tenants-for-microsoft-cloud-offerings.md).