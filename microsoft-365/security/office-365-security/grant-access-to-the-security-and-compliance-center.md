---
title: Kullanıcılara Güvenlik ve Uyumluluk Merkezi'ne erişim izni verme
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
description: Kullanıcılara güvenlik veya uyumluluk özelliklerinden herhangi birini yönetebilmeleri için önce Microsoft 365 Güvenlik & Uyumluluk Merkezi'nde izinlerin atanması gerekir.
ms.custom: seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 4e0ca3874f03d9f0c386a84c9e8b56ea58bbfe72
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/10/2022
ms.locfileid: "66018018"
---
# <a name="give-users-access-to-the-security--compliance-center"></a>Kullanıcılara Güvenlik ve Uyumluluk Merkezi'ne erişim izni verme

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Uygulandığı öğe**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Office 365 için Microsoft Defender plan 1 ve plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Kullanıcılara güvenlik veya uyumluluk özelliklerinden herhangi birini yönetebilmeleri için önce Güvenlik & Uyumluluk Merkezi'nde izinlerin atanması gerekir. Güvenlik & Uyumluluk Merkezi'ndeki OrganizationManagement rol grubunun genel yöneticisi veya üyesi olarak bu izinleri kullanıcılara verebilirsiniz. Kullanıcılar yalnızca erişim verdiğiniz güvenlik veya uyumluluk özelliklerini yönetebilir.

Güvenlik & Uyumluluk Merkezi'nde kullanıcılara verebileceğiniz farklı izinler hakkında daha fazla bilgi için [Güvenlik & Uyumluluk Merkezi'nde İzinler'e](permissions-in-the-security-and-compliance-center.md) göz atın.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Başlamadan önce bilmeniz gerekenler

- Bu makaledeki adımları tamamlamak için genel yönetici veya Güvenlik & Uyumluluk Merkezi'nde OrganizationManagement rol grubunun üyesi olmanız gerekir.

- Güvenlik & Uyumluluk Merkezi rol gruplarının adları Exchange Online rol gruplarıyla benzer olabilir, ancak aynı değildir.

- Rol grubu üyelikleri Exchange Online ile Güvenlik & Uyumluluk Merkezi arasında paylaşılamaz.

- Adına Yönetme (AOBO) izinlerine sahip Temsilci Erişim İzni (DAP) iş ortakları Güvenlik & Uyumluluk Merkezi'ne erişemez.

## <a name="use-the-security--compliance-center-to-give-another-user-access-to-the-security--compliance-center"></a>Başka bir kullanıcıya Güvenlik & Uyumluluk Merkezi'ne erişim vermek için Güvenlik & Uyumluluk Merkezi'ni kullanın

1. Adresinde Güvenlik & Uyumluluk Merkezi'ni <https://protection.office.com> açın ve **İzinler'e** gidin. Doğrudan **İzinler** sekmesine gitmek için dosyasını açın <https://protection.office.com/permissions>.

2. Rol grupları listesinden rol grubunu seçin ve **Düzenle simgesine** tıklayın ![.](../../media/O365-MDM-CreatePolicy-EditIcon.gif).

3. Rol grubunun özellikler sayfasında **Üyeler'in** altında Ekle **Simgesi'ne**![tıklayın.](../../media/ITPro-EAC-AddIcon.gif) ve eklemek istediğiniz kullanıcının (veya kullanıcıların) adını seçin.

4. Rol grubuna eklemek istediğiniz tüm kullanıcıları seçtiğinizde **ekle'ye\>** ve ardından **Tamam'a** tıklayın.

5. Bitirdiğinizde, **Kaydet**'i tıklatın.

## <a name="use-security--compliance-powershell-to-give-another-user-access-to-the-security--compliance-center"></a>Güvenlik & Uyumluluk Merkezi'ne başka bir kullanıcıya erişim vermek için Güvenlik & Uyumluluğu PowerShell'i kullanın

1. [Güvenlik & Uyumluluğu PowerShell'e Bağlan](/powershell/exchange/connect-to-scc-powershell).

2. Aşağıdaki sözdizimini kullanın:

   ```powershell
   Add-RoleGroupMember -Identity <RoleGroup> -Member <UserIdentity>

   - _Identity_ is the role group.
   - _Member_ is the user or universal security group (USG). You can specify only one member at a time.

   This example adds MatildaS to the Organization Management role group.

   ```PowerShell
   Add-RoleGroupMember -Identity "Organization Management" -Member MatildaS
   ```

Ayrıntılı söz dizimi ve parametre sorunları için bkz. [Add-RoleGroupMember](/powershell/module/exchange/add-rolegroupmember)

### <a name="how-do-you-know-this-worked"></a>Bunun çalıştığını nasıl anlarsınız?

Güvenlik & Uyumluluk Merkezi'ne başarıyla erişim izni verdiğini doğrulamak için aşağıdaki adımlardan birini yapın:

- Güvenlik & Uyumluluk Merkezi'nde **İzinler'e** gidin ve rol grubunu seçin. Açılan ayrıntılar açılır penceresinde rol grubunun üyelerini doğrulayın.

- Güvenlik & Uyumluluk PowerShell'inde öğesini rol grubunun adıyla değiştirin \<RoleGroupName\> ve aşağıdaki komutu çalıştırın:

  ```powershell
  Get-RoleGroupMember -Identity "<RoleGroupName>"
  ```

  Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [Get-RoleGroupMember](/powershell/module/exchange/Get-RoleGroupMember).
