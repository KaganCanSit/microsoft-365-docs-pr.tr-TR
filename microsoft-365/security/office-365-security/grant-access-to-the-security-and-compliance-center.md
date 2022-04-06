---
title: Kullanıcılara Güvenlik ve Uyumluluk Merkezi'& verme
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: Admin
ms.topic: how-to
f1_keywords:
- ms.o365.cc.PermissionsHelp
ms.collection: M365-security-compliance
ms.localizationpriority: medium
search.appverid:
- MOE150
- MET150
ms.assetid: 2cfce2c8-20c5-47f9-afc4-24b059c1bd76
description: Kullanıcıların güvenlik ve uyumluluk özelliklerinden herhangi birini yönete Microsoft 365 için önce & Güvenlik ve Uyumluluk Merkezi'nde izinlerin atanları gerekir.
ms.custom: seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 5af3d045b174c4405dc2060fea1db22b3b4066ac
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2022
ms.locfileid: "63680697"
---
# <a name="give-users-access-to-the-security--compliance-center"></a>Kullanıcılara Güvenlik ve Uyumluluk Merkezi'& verme

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Geçerli olduğu yer:**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [1. plan Office 365 plan 2 için Microsoft Defender](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Kullanıcıların güvenlik ve uyumluluk özelliklerinden herhangi birini yönetemeden & için Güvenlik ve Uyumluluk Merkezi'nde izinlerin atanları gerekir. Güvenlik ve Uyumluluk Merkezi'nde OrganizationManagement rol grubunun genel yöneticisi veya & olarak, kullanıcılara bu izinleri veebilirsiniz. Kullanıcılar yalnızca onlara erişim izni vermekte olduğunuz güvenlik ve uyumluluk özelliklerini yönetebilir.

Güvenlik ve Uyumluluk Merkezi'nde kullanıcılara verebilirsiniz farklı izinler hakkında daha fazla & için Güvenlik ve Uyumluluk Merkezi'nde [& bakın](permissions-in-the-security-and-compliance-center.md).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Başlamadan önce bilmeniz gerekenler

- Bu makaledeki adımları tamamlamak için Güvenlik ve Uyumluluk Merkezi'nde OrganizationManagement rol grubunun bir üyesi veya genel yönetici & gerekir.

- Güvenlik Ve Uyumluluk & rol grupları, Uyumluluk Merkezi'nde yer alan rol gruplarına benzer adlara Exchange Online, ancak aynı değildir.

- Rol grubu üyelikleri Güvenlik ve Uyumluluk Merkezi Exchange Online arasında & paylaşılmaz.

- Temsilcili Erişim İzni (DAP) Adına Yönetme (AOBO) izinleriyle birlikte iş ortakları Güvenlik ve Uyumluluk Merkezi'& erişamaz.

## <a name="use-the-security--compliance-center-to-give-another-user-access-to-the-security--compliance-center"></a>Başka bir kullanıcıya & Güvenlik ve Uyumluluk Merkezi'ne erişim vermek için Güvenlik ve Uyumluluk & kullanma

1. Güvenlik ve Uyumluluk &'ne gidin <https://protection.office.com> ve ardından İzinler'e **gidin**. Doğrudan İzinler **sekmesine gitmek** için, 'i açın <https://protection.office.com/permissions>.

2. Rol grupları listesinden rol grubunu seçin ve düzenle **simgesine** ![tıklayın](../../media/O365-MDM-CreatePolicy-EditIcon.gif).

3. Rol grubunun özellikler sayfasında, Üyeler'in **altında** Ekle **Simgesi'ne**![ tıklayın.](../../media/ITPro-EAC-AddIcon.gif) ve eklemek istediğiniz kullanıcının (veya kullanıcıların) adını seçin.

4. Rol grubuna eklemek istediğiniz tüm kullanıcıları seçtikten sonra Ekle'ye ve **sonra Tamam'a\>** **tıklayın**.

5. Bitirdiğinizde, **Kaydet**'i tıklatın.

## <a name="use-security--compliance-center-powershell-to-give-another-user-access-to-the-security--compliance-center"></a>Başka bir & Güvenlik ve Uyumluluk Merkezi'ne erişmesi için PowerShell'i Güvenlik & kullanma

1. [Bağlan ve Uyumluluk & PowerShell'e.](/powershell/exchange/connect-to-scc-powershell)

2. Aşağıdaki sözdizimini kullanın:

   ```powershell
   Add-RoleGroupMember -Identity <RoleGroup> -Member <UserIdentity>

   - _Identity_ is the role group.
   - _Member_ is the user or universal security group (USG). You can specify only one member at a time.

   This example adds MatildaS to the Organization Management role group.

   ```PowerShell
   Add-RoleGroupMember -Identity "Organization Management" -Member MatildaS
   ```

Ayrıntılı söz dizimi ve parametre sorunları için [bkz. Add-RoleGroupMember](/powershell/module/exchange/add-rolegroupmember)

### <a name="how-do-you-know-this-worked"></a>Bunun çalıştığını nasıl anlarsınız?

Güvenlik ve Uyumluluk Merkezi'ne başarıyla erişim & doğrulamak için, aşağıdaki adımlardan birini uygulayın:

- Güvenlik ve Uyumluluk &'nde **İzinler'e gidin** ve rol grubunu seçin. Açılan ayrıntılar açılır grubunda, rol grubunun üyelerini doğrulayın.

- Güvenlik ve & Merkezi PowerShell'de \<RoleGroupName\> rol grubunun adını değiştirin ve aşağıdaki komutu çalıştırın:

  ```powershell
  Get-RoleGroupMember -Identity "<RoleGroupName>"
  ```

  Ayrıntılı söz dizimi ve parametre bilgileri için bkz [. Get-RoleGroupMember](/powershell/module/exchange/Get-RoleGroupMember).