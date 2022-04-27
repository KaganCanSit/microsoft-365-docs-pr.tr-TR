---
title: Grup Microsoft 365 yönetme
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
description: Microsoft 365 gruplarını yönetme hakkında bilgi edinin.
ms.openlocfilehash: 0e7cef7d1b55f695af9a33f22393172f6eee6485
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65100511"
---
# <a name="manage-microsoft-365-groups"></a>Grup Microsoft 365 yönetme

*Bu makale hem Microsoft 365 Kurumsal hem de Office 365 Kurumsal için geçerlidir.*

yapılandırmanıza bağlı olarak Microsoft 365 gruplarını çeşitli yollarla yönetebilirsiniz. Microsoft 365 yönetim merkezi, PowerShell, [Active Directory Domain Services](/admin) (AD DS) veya [Azure Active Directory (Azure AD) yönetim merkezinde](/azure/active-directory/fundamentals/active-directory-groups-create-azure-portal) kullanıcı hesaplarını yönetebilirsiniz. 

## <a name="plan-for-where-and-how-you-will-manage-your-groups"></a>Gruplarınızı nerede ve nasıl yönetebileceğinizi planlama

Kullanıcı hesaplarınızı nerede ve nasıl yönetebileceğiniz, Microsoft 365 için kullanmak istediğiniz kimlik modeline bağlıdır. İki genel model yalnızca bulut ve hibrit modeldir.
  
### <a name="cloud-only"></a>Yalnızca bulut

Grupları oluşturmak ve yönetmek için:

- [Microsoft 365 yönetim merkezi](/admin)
- [PowerShell](maintain-group-membership-with-microsoft-365-powershell.md)
- [Azure AD yönetim merkezi](/azure/active-directory/fundamentals/active-directory-groups-create-azure-portal)
    
### <a name="hybrid"></a>Karma

AD DS grupları AD DS'den Microsoft 365 ile eşitlenir, bu nedenle bu grupları yönetmek için şirket içi AD DS araçlarını kullanmanız gerekir.

Ayrıca, AD DS gruplarından ayrı olan ancak AD DS'den kullanıcılar ve gruplar içerebilen Azure AD grupları oluşturabilir ve yönetebilirsiniz. Bu durumda şunları kullanabilirsiniz:

- [Microsoft 365 yönetim merkezi](/admin)
- [PowerShell](maintain-group-membership-with-microsoft-365-powershell.md)
- [Azure AD yönetim merkezi](/azure/active-directory/fundamentals/active-directory-groups-create-azure-portal)

## <a name="allow-users-to-create-and-manage-their-own-groups"></a>Kullanıcıların kendi gruplarını oluşturmasına ve yönetmesine izin ver

Azure AD, BT yöneticileri yerine grup sahipleri tarafından yönetilebilen gruplara izin verir. *Self servis grup yönetimi* olarak bilinen bu özellik, yönetici rolü atanmayan grup sahiplerinin güvenlik grupları oluşturmasına ve yönetmesine olanak tanır. 

Kullanıcılar bir güvenlik grubunda üyelik isteyebilir ve bu istek BT yöneticisi yerine grup sahibine gider. Bu, grup üyeliğinin günlük denetiminin, grubun iş kullanımını anlayan ve üyeliğini yönetebilen ekip, proje veya işletme sahiplerine temsilci olarak atanmasını sağlar.

>[!Note]
>Self servis grup yönetimi yalnızca Azure AD güvenliği ve Microsoft 365 grupları için kullanılabilir. Posta etkin gruplar, dağıtım listeleri veya AD DS'den eşitlenmiş herhangi bir grup için kullanılamaz.
>

Daha fazla bilgi [için self servis yönetimi için Azure AD grubu yapılandırma yönergelerine](/azure/active-directory/active-directory-accessmanagement-self-service-group-management) bakın.

## <a name="set-up-dynamic-group-membership"></a>Dinamik grup üyeliğini ayarlama

Azure AD, bir Azure AD grubunun üyesi olarak kullanıcı hesaplarını otomatik olarak ekleyen veya kaldıran bir dizi kuralın yapılandırılmasını destekler. Bu, *dinamik grup üyeliği* olarak bilinir. Kurallar, Departman veya Ülke gibi kullanıcı hesabı özniteliklerini temel alır.

Kurallar şu şekilde uygulanır:

- Yeni bir kullanıcı hesabı grubun tüm kurallarıyla eşleşirse üye olur.
- Bir kullanıcı hesabı grubun üyesi değilse, ancak öznitelikleri grubun tüm kurallarıyla eşleşeceği şekilde değişirse, o grubun üyesi olur.
- Bir kullanıcı hesabı grubun tüm kurallarıyla eşleşmiyorsa gruba eklenmez.
- Bir kullanıcı hesabı grubun üyesiyse ancak öznitelikleri artık grubun tüm kurallarıyla eşleşmemesi için değişirse, grubun üyesi olarak kaldırılır.

Dinamik üyeliği kullanmak için öncelikle ortak kullanıcı hesabı öznitelikleri kümesine sahip grup kümelerini belirlemeniz gerekir. Örneğin, Satış departmanının tüm üyeleri, Departman kullanıcı hesabı özniteliğinin "Satış" olarak ayarlanmasına bağlı olarak Sales Azure AD grubunda olmalıdır.

[Dinamik bir Azure AD grubu için kurallar oluşturma ve yapılandırma yönergelerine](/azure/active-directory/active-directory-groups-dynamic-membership-azure-portal) bakın.

## <a name="set-up-automatic-licensing"></a>Otomatik lisanslama ayarlama

Azure AD'de güvenlik gruplarını, bir abonelik kümesindeki lisansları grubun tüm üyelerine otomatik olarak atayacak şekilde yapılandırabilirsiniz. Bu, *grup tabanlı lisanslama* olarak bilinir. Gruba bir kullanıcı hesabı eklenirse veya gruptan kaldırılırsa, grup abonelikleri için lisanslar otomatik olarak atanır veya kullanıcı hesabından atanmamış olur.

Microsoft 365 Kurumsal için Azure AD güvenlik gruplarını uygun Microsoft 365 Kurumsal lisansını atayacak şekilde yapılandıracaksınız.

Tüm grup üyeleri için yeterli lisansa sahip olduğunuzdan emin olun. Lisanslar tükenirse, lisanslar kullanılabilir duruma gelene kadar yeni kullanıcılara lisans atanamaz.

>[!Note]
>Azure işletmeden işletmeye (B2B) hesapları içeren gruplar için grup tabanlı lisanslama yapılandırmamalısınız.
>

Daha fazla bilgi için bkz. [Azure AD'de grup tabanlı lisanslama temelleri](/azure/active-directory/active-directory-licensing-whatis-azure-portal).

[Azure güvenlik grubu için grup tabanlı lisanslama yapılandırma yönergelerine](/azure/active-directory/active-directory-licensing-group-assignment-azure-portal) bakın.