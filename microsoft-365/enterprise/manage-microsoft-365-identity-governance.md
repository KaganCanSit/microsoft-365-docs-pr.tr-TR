---
title: Microsoft 365 kimlik idaresi yönetme
ms.author: kvice
author: kelleyvice-msft
manager: scotv
audience: Admin
ms.topic: overview
ms.prod: office-online-server
ms.localizationpriority: medium
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-mar2020
ms.collection:
- Ent_O365
- M365-subscription-management
search.appverid:
- MET150
- MOE150
- MED150
- BCS160
ms.assetid: 98ca5b3f-f720-4d8e-91be-fe656548a25a
description: Microsoft 365 kimlik idaresi özelliklerini kullanma hakkında bilgi edinin.
ms.openlocfilehash: f4fcfed9fcb978e40c3bf7c0e7a35eb717fee343
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65091181"
---
# <a name="manage-microsoft-365-identity-governance"></a>Microsoft 365 kimlik idaresi yönetme

Kimlik idaresi, çalışanların üretkenliğini sağlarken kritik varlıklara erişimi korumak, izlemek ve denetlemekle alakalıdır. Örneğin, kimlik idaresi ile doğru kullanıcıların doğru kaynaklara doğru erişime sahip olduğundan emin olabilir ve bu erişimin zaman içinde değişip değişmediğini belirleyebilirsiniz.

Daha fazla bilgi için bkz. [Azure Active Directory (Azure AD) için kimlik idaresine genel bakış](/azure/active-directory/governance/identity-governance-overview).

## <a name="set-up-azure-ad-access-reviews"></a>Azure AD erişim gözden geçirmelerini ayarlama

Azure AD erişim gözden geçirmeleri, yalnızca doğru kişilerin erişimine devam ettiğinden emin olmak için kullanıcının erişimini gözden geçirmenize olanak tanır. Örneğin:

- Kuruluşunuza yeni bir çalışan katıldığında, üretken olmak için doğru erişime sahip olduklarından emin olmanız gerekir.
- Bu çalışan diğer ekiplere, konumlara veya departmanlara taşınırken, önceki ekiplere, konumlara veya departmanlara erişiminin gerektiğinde kaldırıldığından emin olmanız gerekir.
- Bu çalışan veya konuk kuruluşunuzdan ayrıldığında, erişiminin kaldırıldığından emin olmanız gerekir.

Bu özellikle, kuruluşunuzun kullanıcı hesaplarının çok fazla erişime sahip olup olmadığını belirlemek için güvenlik denetimlerine tabi olması durumunda önemlidir ve bu da sektör veya bölgesel düzenlemelerin ihlali durumunda para cezasına neden olabilir.

Daha fazla bilgi için [erişim gözden geçirmelerine genel bakış bölümüne](/azure/active-directory/governance/access-reviews-overview) bakın.

Farklı erişim gözden geçirme türlerini yapılandırmak için şu makalelere bakın:

- [Gruplar ve uygulamalar](/azure/active-directory/governance/create-access-review)
- [Azure AD rolleri](/azure/active-directory/privileged-identity-management/pim-how-to-start-security-review?toc=%2fazure%2factive-directory%2fgovernance%2ftoc.json)
- [Azure kaynak rolleri](/azure/active-directory/privileged-identity-management/pim-resource-roles-start-access-review?toc=%2fazure%2factive-directory%2fgovernance%2ftoc.json)

## <a name="set-up-azure-ad-entitlement-management"></a>Azure AD yetkilendirme yönetimini ayarlama

Wiht Azure AD yetkilendirme yönetimi; erişim isteği iş akışlarını, erişim atamalarını, incelemeleri ve süre sonunu otomatikleştirerek kimliği ve erişim yaşam döngüsünü uygun ölçekte yönetebilirsiniz.

Çalışanlarınızın işlerini gerçekleştirmek için çeşitli gruplara, uygulamalara ve sitelere erişmesi gerekir. Gereksinimler değiştiği, yeni uygulamalar eklendiği veya kullanıcıların ek erişim haklarına ihtiyacı olduğu için bu erişimi yönetmek zor olabilir. Diğer kuruluşlarla işbirliği yaptığınızda, diğer kuruluşta kimlerin kuruluşunuzun kaynaklarına erişmesi gerektiğini bilmiyor olabilirsiniz ve dış kullanıcılar kuruluşunuzun hangi uygulamaları, grupları veya siteleri kullandığını bilmeyecektir.

Azure AD yetkilendirme yönetimi, iç ve dış kullanıcılar için gruplara, uygulamalara ve SharePoint sitelerine erişimi daha verimli bir şekilde yönetmenize yardımcı olabilir.
 
Daha fazla bilgi için bkz. [Azure AD yetkilendirme yönetimine genel bakış](/azure/active-directory/governance/entitlement-management-overview).