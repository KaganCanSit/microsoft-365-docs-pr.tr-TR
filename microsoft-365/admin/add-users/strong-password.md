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
description: Parolayı kullanarak kullanıcılarınız için güçlü parola gereksinimleri ayarlamayı Windows PowerShell.
ms.openlocfilehash: 5932f01c2f17a72f4f6a20a6457d263bed7dd85e
ms.sourcegitcommit: 6dcc3b039e0f0b9bae17c386f14ed2b577b453a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/15/2021
ms.locfileid: "63018885"
---
# <a name="turn-off-strong-password-requirements-for-users"></a>Kullanıcılar için güçlü parola gereksinimlerini kapatma

Bu makalede, kullanıcılarınız için güçlü parola gereksinimlerini nasıl kapatabilirsiniz? Kurumsal kuruluş e-posta ağ ağ gereksinimleriniz Microsoft 365 açıktır. Kuruluşta güçlü parolaları devre dışı bırakma gereksinimleri olabilir. Güçlü parola gereksinimlerini kapatmak için aşağıdaki adımları izleyin. Bu adımları PowerShell kullanarak tamamlamanız gerekir.

## <a name="before-you-begin"></a>Başlamadan önce

Bu makale bir işletme, okul veya kar amacı gütmeyen kuruluş için parola ilkesi yöneten kişiler için hazırlanmıştır. Bu adımları tamamlamak için yönetici hesabınızla oturum Microsoft 365 gerekir. [Yönetici hesabı nedir?] (genel bakış Microsoft 365 yönetim merkezi](.. /admin-overview/admin-center-overview.md) Bu adımları gerçekleştirmek için genel yönetici veya [parola](about-admin-roles.md) yöneticisi olun.

Microsoft 365'a PowerShell'Microsoft 365 bağlanmanız gerekir.

## <a name="set-strong-passwords"></a>Güçlü parolalar ayarlama

1. [Bağlan PowerShell Microsoft 365'e çok zaman var](/office365/enterprise/powershell/connect-to-office-365-powershell#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

2. PowerShell kullanarak, şu komutu kullanarak tüm kullanıcılar için güçlü parola gereksinimlerini kapatabilirsiniz:

    ```powershell
    Get-MsolUser | Set-MsolUser -StrongPasswordRequired $false

3. You can turn **OFF** strong password requirements for specific users with this command:

    ```powershell
    Set-MsolUser –UserPrincipalName –StrongPasswordRequired  $false
    ```

> [!NOTE]
> userPrincipalName, kullanıcı adının ardından @ işareti ve etki alanı adının bulunduğu İnternet stili oturum açma biçiminde olmalıdır. Örneğin: user@contoso.com.

## <a name="related-content"></a>İlgili içerik

[Microsoft 365'a PowerShell ile bağlanma](/office365/enterprise/powershell/connect-to-office-365-powershell#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)

[PowerShell MsolUser komutları hakkında daha fazla bilgi](/powershell/azure/active-directory/install-adv2)

[Parola ilkesi hakkında daha fazla bilgi](/azure/active-directory/authentication/concept-sspr-policy#password-policies-that-only-apply-to-cloud-user-accounts)
