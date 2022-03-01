---
title: Tek bir kullanıcının parolasını süresi hiç dolmayacak şekilde ayarlama
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
- AdminTemplateSet
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: f493e3af-e1d8-4668-9211-230c245a0466
description: Bazı bireysel kullanıcı parolalarını Microsoft 365 parolalarını kişisel parola kullanarak süresi hiç dolmak üzere ayarlamak için Windows PowerShell.
ms.openlocfilehash: f0eff70b2b95c7e318f8a7e52777d4b684dbd8bf
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2022
ms.locfileid: "63021679"
---
# <a name="set-an-individual-users-password-to-never-expire"></a>Tek bir kullanıcının parolasını süresi hiç dolmayacak şekilde ayarlama

Bu makalede, tek bir kullanıcının süresi dolmak üzere parola ayarlaması açıklanmıştır. Bu adımları PowerShell kullanarak tamamlamanız gerekir.

## <a name="before-you-begin"></a>Başlamadan önce

Bu makale, bir işletme, okul veya kar amacı gütmeyen kuruluş için parola süre sonu ilkesi belirleyen kişilere yöneliktir. Bu adımları tamamlamak için yönetici hesabınızla oturum Microsoft 365 gerekir. Bkz[. İlkelere genel Microsoft 365 yönetim merkezi](/microsoft-365/admin/admin-overview/admin-center-overview?view=o365-worldwide).

Bu adımları gerçekleştirmek [için genel yönetici veya parola](about-admin-roles.md) yöneticisi olun.

Microsoft bulut hizmetinin genel yöneticisi, belirli kullanıcıların parolalarını [Azure Active Directory için Graph PowerShell'i](/powershell/azure/active-directory/install-adv2) kullanabilir. Ayrıca, [azureAD](/powershell/module/Azuread) cmdlet'lerini kullanarak süresi hiç dolmaan yapılandırmasını kaldırabilir veya hangi kullanıcı parolalarını süresi hiç dolmay olarak ayarlan hazır olduğunu da kullanabilirsiniz.

Bu kılavuz, kimlik ve dizin hizmetleri için Azure AD'den de Microsoft 365 Intune ve Microsoft 365 gibi diğer sağlayıcılar için geçerlidir. Parola süre sonu, ilkenin değiştir değiştir yarıda bir bölümü olur.


## <a name="how-to-check-the-expiration-policy-for-a-password"></a>Parolanın süre sonu ilkesi nasıl kontrol olur?

AzureAD modülünde Get-AzureADUser hakkında daha fazla bilgi için [Get-AzureADUser başvuru makalesine bakın](/powershell/module/Azuread/Get-AzureADUser).

Aşağıdaki komutlardan birini çalıştırın:

- Tek bir kullanıcının parolasının süresinin hiç dolmayacak şekilde ayar olup olmadıklarına bakın, UPN'leri (örneğin, *user@contoso.onmicrosoft.com*) veya kontrol etmek istediğiniz kullanıcının kullanıcı kimliğini kullanarak aşağıdaki cmdlet'i çalıştırın:

    ```powershell
    Get-AzureADUser -ObjectId <user id or UPN> | Select-Object UserprincipalName,@{
        N="PasswordNeverExpires";E={$_.PasswordPolicies -contains "DisablePasswordExpiration"}
    }
    ```

    Örneğin:

    ```powershell
    Get-AzureADUser -ObjectId userUPN@contoso.com | Select-Object UserprincipalName,@{
        N="PasswordNeverExpires";E={$_.PasswordPolicies -contains "DisablePasswordExpiration"}
    }
    ```

- Tüm kullanıcılar için **Parolanın süresi hiçbir zaman** dolmaz ayarını görmek için aşağıdaki cmdlet'i çalıştırın:

    ```powershell
    Get-AzureADUser -All $true | Select-Object UserprincipalName,@{
        N="PasswordNeverExpires";E={$_.PasswordPolicies -contains "DisablePasswordExpiration"}
     }
    ```

- PasswordNeverExpires ile geçerli kullanıcının masaüstünde PasswordNeverExpires adı ve parolası olan tüm kullanıcıların raporunu  **ReportPasswordNeverExpires.html**

    ```powershell
    Get-AzureADUser -All $true | Select-Object UserprincipalName,@{
        N="PasswordNeverExpires";E={$_.PasswordPolicies -contains "DisablePasswordExpiration"}
    } | ConvertTo-Html | Out-File $env:userprofile\Desktop\ReportPasswordNeverExpires.html
    ```

- PasswordNeverExpires'i olan tüm kullanıcıların raporunu almak için, kullanıcının masaüstünde CSV'ye adı ve **adıReportPasswordNeverExpires.csv**

    ```powershell
    Get-AzureADUser -All $true | Select-Object UserprincipalName,@{
        N="PasswordNeverExpires";E={$_.PasswordPolicies -contains "DisablePasswordExpiration"}
    } | ConvertTo-Csv -NoTypeInformation | Out-File $env:userprofile\Desktop\ReportPasswordNeverExpires.csv

## Set a password to never expire

Run one of the following commands:

- To set the password of one user to never expire, run the following cmdlet by using the UPN or the user ID of the user:

    ```powershell
    Set-AzureADUser -ObjectId <user ID> -PasswordPolicies DisablePasswordExpiration
    ```

- Kuruluşta kullanıcıların parolalarını süresi hiç dolmayacak şekilde ayarlamak için aşağıdaki cmdlet'i çalıştırın:

    ```powershell
    Get-AzureADUser -All $true | Set-AzureADUser -PasswordPolicies DisablePasswordExpiration
    ```

> [!WARNING]
> Özniteliği temel alarak yine yaş parametresiyle `-PasswordPolicies DisablePasswordExpiration` yapılandırılmış kullanıcı `pwdLastSet` hesapları. Özniteliği temel `pwdLastSet` alarak, `-PasswordPolicies None`sona erme tarihini ' olarak değiştirirseniz, pwdLastSet 90'dan eski olan tüm parolalar, kullanıcının bir sonraki oturum açmalarında onu değiştirmesini gerektirir. Bu değişiklik çok fazla sayıda kullanıcıyı etkileyebilir.

### <a name="set-a-password-to-expire"></a>Parolayı süresi dolmak üzere ayarlama

Aşağıdaki komutlardan birini çalıştırın:

- Parolanın süresinin dolması için bir kullanıcının parolasını ayarlamak için, UPN'yi veya kullanıcının kullanıcı kimliğini kullanarak aşağıdaki cmdlet'i çalıştırın:

    ```powershell
    Set-AzureADUser -ObjectId <user ID> -PasswordPolicies None
    ```

- Kuruluşta tüm kullanıcıların parolalarını süresi dol olacak şekilde ayarlamak için, aşağıdaki cmdlet'i kullanın:

    ```powershell
    Get-AzureADUser -All $true | Set-AzureADUser -PasswordPolicies None
    ```

## <a name="related-content"></a>İlgili içerik

[Kullanıcıların kendi parolalarını sıfırlamasına izin verme](../add-users/let-users-reset-passwords.md) (makale)\
[Parolaları sıfırlama](../add-users/reset-passwords.md) (makale)\
[Kurum için parola süre sonu ilkesi ayarlama](../manage/set-password-expiration-policy.md) (makale)
