---
title: Grup Microsoft 365 yönetme
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
description: Grup gruplarınızı yönetmeyi Microsoft 365 öğrenin.
ms.openlocfilehash: 28d8bae8aaed6d02fe082824c07afe03bdc0ce5a
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62977673"
---
# <a name="manage-microsoft-365-groups"></a>Grup Microsoft 365 yönetme

*Bu makale hem son hem de Microsoft 365 Kurumsal hem de Office 365 Kurumsal.*

Her Microsoft 365, yapılandırmanıza bağlı olarak farklı şekillerde yönetebilirsiniz. Kullanıcı hesaplarını [Microsoft 365 yönetim merkezi,](/admin) PowerShell, Active Directory Etki Alanı Hizmetleri'nde (AD DS[) veya Azure Active Directory (Azure AD) yönetim merkezinde yönetebilirsiniz](/azure/active-directory/fundamentals/active-directory-groups-create-azure-portal). 

## <a name="plan-for-where-and-how-you-will-manage-your-groups"></a>Gruplarınızı nasıl ve nerede yöneteceklerinizi planlama

Kullanıcı hesaplarınızı nasıl ve nerede yönetebilirsiniz, kullanıcı hesaplarınız için kullanmak istediğiniz kimlik modeline Microsoft 365. Genel olarak iki model yalnızca bulut ve karmadır.
  
### <a name="cloud-only"></a>Yalnızca bulut

Grupları şu şekilde oluşturabilir ve yönetsiniz:

- [Microsoft 365 yönetim merkezi](/admin)
- [PowerShell](maintain-group-membership-with-microsoft-365-powershell.md)
- [Azure AD yönetim merkezi](/azure/active-directory/fundamentals/active-directory-groups-create-azure-portal)
    
### <a name="hybrid"></a>Karma

AD DS grupları AD DS Microsoft 365 gelen adlarla eşitlenir, dolayısıyla bu grupları yönetmek için şirket içi AD DS araçlarını kullan gerekir.

Ayrıca, AD DS gruplarından ayrı olan, ancak AD DS'den kullanıcılar ve gruplar içeren Azure AD gruplarını oluşturabilir ve yönetebilirsiniz. Bu durumda şunları kullanabilirsiniz:

- [Microsoft 365 yönetim merkezi](/admin)
- [PowerShell](maintain-group-membership-with-microsoft-365-powershell.md)
- [Azure AD yönetim merkezi](/azure/active-directory/fundamentals/active-directory-groups-create-azure-portal)

## <a name="allow-users-to-create-and-manage-their-own-groups"></a>Kullanıcıların kendi gruplarını oluşturmasına ve yönetmesine izin verme

Azure AD, grupların, IT yöneticileri yerine grup sahipleri tarafından yönetillere izin verir. Self servis *grup yönetimi olarak bilinen* bu özellik, yönetim rolü atanmamış grup sahiplerinin güvenlik gruplarını oluşturmalarına ve yönetmelerine olanak sağlar. 

Kullanıcılar bir güvenlik grubunda üyelik isteğinde  olabilir ve bu istek, bir IT yöneticisi yerine grup sahibine gider. Bu, grup üyeliğinin günlük denetimlerini, grubun ticari kullanımını an eden ve üyeliklerini yöneten ekip, proje veya iş sahiplerine temsilci olarak verir.

>[!Note]
>Self servis grup yönetimi yalnızca Azure AD güvenliği ve gruplarında Microsoft 365 kullanılabilir. Posta özellikli gruplarda, dağıtım listelerinde veya AD DS'den eşitlenmiş herhangi bir grupta kullanılamaz.
>

Daha fazla bilgi için, [self servis yönetim için Azure AD grubunu yapılandırma yönergelerine bakın](/azure/active-directory/active-directory-accessmanagement-self-service-group-management).

## <a name="set-up-dynamic-group-membership"></a>Dinamik grup üyeliğini ayarlama

Azure AD, kullanıcı hesaplarını bir Azure AD grubunun üyeleri olarak otomatik olarak ekleyip kaldıran bir dizi kural yapılandırmayı destekler. Bu, dinamik grup *üyeliği olarak bilinir*. Kurallar, Departman veya Ülke gibi kullanıcı hesabı özniteliklerine dayalıdır.

Kurallar şöyle uygulanır:

- Yeni bir kullanıcı hesabı grubun tüm kurallarıyla eşleşirse, üye olur.
- Kullanıcı hesabı grubun üyesi değilse, ancak öznitelikleri grubun tüm kurallarıyla eşleşir şekilde değişirse, o grubun üyesi olur.
- Bir kullanıcı hesabı grubun tüm kurallarına uymazsa, gruba eklenmez.
- Kullanıcı hesabı grubun bir üyesi ise, ancak öznitelikleri değişse de, artık grubun tüm kurallarıyla eşleşmesi için öznitelikler değişir, grup üyesi olarak kaldırılır.

Dinamik üyeliği kullanmak için, önce ortak bir kullanıcı hesabı öznitelikleri kümesine sahip grup kümelerini belirlemeniz gerekir. Örneğin, Satış departmanının tüm üyeleri, Department tarafından "Satışlar" olarak ayarlanmış kullanıcı hesabı özniteliğine bağlı olarak Satış Azure AD grubunda yer a olmalı.

Dinamik [Azure AD grubu için kuralları oluşturma ve yapılandırma yönergelerine bakın](/azure/active-directory/active-directory-groups-dynamic-membership-azure-portal).

## <a name="set-up-automatic-licensing"></a>Otomatik lisans ayarlama

Azure AD'de güvenlik gruplarını, bir abonelik kümesinden tüm grup üyelerine otomatik olarak lisans atamak üzere yapılandırabilirsiniz. Bu, grup *tabanlı lisanslama olarak bilinir*. Gruba bir kullanıcı hesabı eklenir veya gruptan kaldırılırsa, grubun aboneliklerine yönelik lisanslar kullanıcı hesabından otomatik olarak atanır veya atanmamış olur.

Daha Microsoft 365 Kurumsal için, Azure AD güvenlik gruplarını uygun lisans atamasını Microsoft 365 Kurumsal gerekir.

Tüm grup üyeleri için yeterli lisansa sahip olduğundan emin olun. Lisans yoksa, yeni kullanıcılara lisanslar kullanılabilir olana kadar lisans atanmaz.

>[!Note]
>Azure İş (B2B) hesaplarını içeren gruplar için grup tabanlı lisanslama yapılandırmanız gerekir.
>

Daha fazla bilgi için bkz [. Azure AD'de grup tabanlı lisanslama temel bilgileri](/azure/active-directory/active-directory-licensing-whatis-azure-portal).

Azure [güvenlik grubu için grup tabanlı lisansları yapılandırma yönergelerine bakın](/azure/active-directory/active-directory-licensing-group-assignment-azure-portal).