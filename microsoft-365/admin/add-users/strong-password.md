---
title: Kullanıcılar için güçlü parola gereksinimlerini kapatma
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
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
- MSStore_Link
- AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
description: bir işletme, okul veya kar amacı gütmeyen kuruluş için parola ilkesini yöneten bir yöneticiyseniz, PowerShell'Azure AD kullanarak güçlü parola gereksinimleri ayarlayabilirsiniz.
ms.openlocfilehash: e98c9a3f7b31cbb53d4c853487f4908a6dec72d5
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/10/2022
ms.locfileid: "66010266"
---
# <a name="turn-off-strong-password-requirements-for-users"></a>Kullanıcılar için güçlü parola gereksinimlerini kapatma

Bu makalede, kullanıcılarınız için güçlü parola gereksinimlerini nasıl kapattığınız açıklanmaktadır. İş için Microsoft 365 kuruluşunuzda güçlü parola gereksinimleri varsayılan olarak açıktır. Kuruluşunuzun güçlü parolaları devre dışı bırakma gereksinimleri olabilir. Güçlü parola gereksinimlerini kapatmak için aşağıdaki adımları izleyin. PowerShell kullanarak bu adımları tamamlamanız gerekir.

## <a name="before-you-begin"></a>Başlamadan önce

Bu makale, bir işletme, okul veya kar amacı gütmeyen kuruluş için parola ilkesini yöneten kişilere yöneliktir. Bu adımları tamamlamak için Microsoft 365 yönetici hesabınızla oturum açmanız gerekir. [Yönetici hesabı nedir?] (Microsoft 365 yönetim merkezi Genel Bakış](.. /admin-overview/admin-center-overview.md) Bu adımları gerçekleştirmek için [genel yönetici veya parola yöneticisi](about-admin-roles.md) olmanız gerekir.

Ayrıca PowerShell ile Microsoft 365 bağlanmalısınız.

## <a name="set-strong-passwords"></a>Güçlü parolalar ayarlama

1. [PowerShell ile Microsoft 365 Bağlan](/office365/enterprise/powershell/connect-to-office-365-powershell#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

2. PowerShell'i kullanarak, aşağıdaki komutu kullanarak tüm kullanıcılar için güçlü parola gereksinimlerini kapatabilirsiniz:

    ```powershell
    Get-MsolUser | Set-MsolUser -StrongPasswordRequired $false

3. You can turn **OFF** strong password requirements for specific users with this command:

    ```powershell
    Set-MsolUser –UserPrincipalName –StrongPasswordRequired  $false
    ```

> [!NOTE]
> userPrincipalName, kullanıcı adının ardından at işareti (@) ve bir etki alanı adının geldiği İnternet stilinde oturum açma biçiminde olmalıdır. Örneğin: user@contoso.com.

## <a name="related-content"></a>İlgili içerik

[PowerShell ile Microsoft 365 bağlanma](/office365/enterprise/powershell/connect-to-office-365-powershell#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)

[PowerShell MsolUser komutları hakkında daha fazla bilgi](/powershell/azure/active-directory/install-adv2)

[Parola ilkesi hakkında daha fazla bilgi](/azure/active-directory/authentication/concept-sspr-policy#password-policies-that-only-apply-to-cloud-user-accounts)
