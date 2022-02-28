---
title: Kimlik Microsoft 365 yönetme
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: Kimlik yönetimi özelliklerini nasıl Microsoft 365 hakkında bilgi öğrenin.
ms.openlocfilehash: 35b2092412ddbeacd5d6962e110de1931b2d0f4b
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62977672"
---
# <a name="manage-microsoft-365-identity-governance"></a>Kimlik Microsoft 365 yönetme

Kimlik yönetimi, kritik varlıklara erişimi koruma, izleme ve denetlemeyle, ayrıca çalışanların üretkenliğini sağlamayla da önemlidir. Örneğin, kimlik yönetimiyle, doğru kullanıcıların doğru kaynaklara doğru erişimi olduğundan emin olabilir ve bu erişimin zaman içinde değişirse bunu belirlersiniz.

Daha fazla bilgi için bu Kimlik [Yönetimi (Azure AD) Azure Active Directory genel bakış bilgilerine bakın](/azure/active-directory/governance/identity-governance-overview).

## <a name="set-up-azure-ad-access-reviews"></a>Azure AD erişim incelemelerini ayarlama

Azure AD erişim incelemeleri, yalnızca doğru kişilerin erişmeye devam olduğundan emin olmak için kullanıcının erişimini gözden geçirmenıza olanak sağlar. Örneğin:

- Organizasyona yeni bir çalışan kat kat katıldı olarak, üretken olmak için doğru erişime sahip olduğundan emin olun.
- Bu çalışan başka ekiplere, konumlara veya departmanlara taşınırken, önceki ekiplere, konumlara veya departmanlara erişiminin gerektiğinde kaldırıldıklarından emin olmak gerekir.
- Bu çalışan veya bir konuk kuruluştan ayrıldığında, erişiminin kaldırıldıklarından emin olun.

Bu özellikle, kuruluş kullanıcı hesaplarına çok fazla erişim olup olmadığını belirlemek için güvenlik denetimlerine tabi olması açısından önemlidir; bu durum sektör veya bölgesel düzenlemelerin ihlalinde ince neden olabilir.

Daha fazla bilgi için erişim [incelemelerine genel bakış bilgilerine bakın](/azure/active-directory/governance/access-reviews-overview).

Farklı erişim incelemeleri türlerini yapılandırmak için şu makalelere bakın:

- [Gruplar ve uygulamalar](/azure/active-directory/governance/create-access-review)
- [Azure AD rolleri](/azure/active-directory/privileged-identity-management/pim-how-to-start-security-review?toc=%2fazure%2factive-directory%2fgovernance%2ftoc.json)
- [Azure kaynak rolleri](/azure/active-directory/privileged-identity-management/pim-resource-roles-start-access-review?toc=%2fazure%2factive-directory%2fgovernance%2ftoc.json)

## <a name="set-up-azure-ad-entitlement-management"></a>Azure AD yetkilendirme yönetimini ayarlama

Azure AD yetkilendirme yönetimi ile erişim isteği iş akışlarını otomatik başlatarak, atamalara, incelemelere ve süre sonuyla kimlik ve erişim yaşam döngüsünü ölçekte yönetebilirsiniz.

Çalışanlarınızı, yaptıkları işi gerçekleştirmek için çeşitli gruplara, uygulamalara ve sitelere erişmeleri gerekir. Gereksinimler değişmesi, yeni uygulamalar ekli olması veya kullanıcıların ek erişim haklarına ihtiyacı olduğundan, bu erişimi yönetmek zor olabilir. Başka kuruluşlarla işbirliği yapıyorsanız, diğer kuruluşta kimlerin kuruluş kaynaklarına erişmesi gerektiğini bilmiyorsanız ve dış kullanıcılar da kurum hangi uygulamaları, grupları veya siteleri kullanmakta olduğunu bilmiyor olabilir.

Azure AD yetkilendirme yönetimi, iç ve dış kullanıcılar için gruplara, uygulamalara ve sitelere SharePoint şekilde yönetmenize yardımcı olabilir.
 
Daha fazla bilgi için bkz [. Azure AD yetkilendirme yönetimine genel bakış](/azure/active-directory/governance/entitlement-management-overview).