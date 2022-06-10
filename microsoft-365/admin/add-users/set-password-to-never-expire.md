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
description: Azure AD PowerShell kullanarak bazı bireysel kullanıcı parolalarının süresinin hiç dolmamasına ayarlamak için Microsoft 365 yönetici hesabınızda oturum açın.
ms.openlocfilehash: a8357e3c72ea4bcd30234492b30e75eff8cb123a
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/10/2022
ms.locfileid: "66010200"
---
# <a name="set-an-individual-users-password-to-never-expire"></a>Tek bir kullanıcının parolasını süresi hiç dolmayacak şekilde ayarlama

Bu makalede, tek bir kullanıcının süresinin dolmaması için parolanın nasıl ayarlanacağı açıklanmaktadır. PowerShell kullanarak bu adımları tamamlamanız gerekir.

## <a name="before-you-begin"></a>Başlamadan önce

Bu makale, bir işletme, okul veya kar amacı gütmeyen kuruluş için parola süre sonu ilkesi belirleyen kişilere yöneliktir. Bu adımları tamamlamak için Microsoft 365 yönetici hesabınızla oturum açmanız gerekir. Bkz. [Microsoft 365 yönetim merkezi genel bakış](/microsoft-365/admin/admin-overview/admin-center-overview).

Bu adımları gerçekleştirmek için [genel yönetici veya parola yöneticisi](about-admin-roles.md) olmanız gerekir.

Microsoft bulut hizmeti genel yöneticisi, parolaların belirli kullanıcılar için süresinin dolmaması [için Graph için Azure Active Directory PowerShell](/powershell/azure/active-directory/install-adv2) kullanabilir. [AzureAD](/powershell/module/Azuread) cmdlet'lerini, süresi hiç dolmayan yapılandırmayı kaldırmak veya hangi kullanıcı parolalarının hiçbir zaman sona ermeyecek şekilde ayarlandığını görmek için de kullanabilirsiniz.

Bu kılavuz, kimlik ve dizin hizmetleri için de Azure AD kullanan Intune ve Microsoft 365 gibi diğer sağlayıcılar için geçerlidir. Parola süre sonu, ilkenin değiştirilebilen tek bölümüdür.

## <a name="how-to-check-the-expiration-policy-for-a-password"></a>Parola için süre sonu ilkesini denetleme

AzureAD modülündeki Get-AzureADUser komutu hakkında daha fazla bilgi için [Get-AzureADUser](/powershell/module/Azuread/Get-AzureADUser) başvuru makalesine bakın.

Aşağıdaki komutlardan birini çalıştırın:

- Tek bir kullanıcının parolasının süresi hiç dolmak üzere ayarlı olup olmadığını görmek için, UPN'yi (örneğin, *user@contoso.onmicrosoft.com*) veya denetlemek istediğiniz kullanıcının kullanıcı kimliğini kullanarak aşağıdaki cmdlet'i çalıştırın:

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

- Tüm kullanıcılar için **Parolanın süresi hiç dolmaz** ayarını görmek için aşağıdaki cmdlet'i çalıştırın:

    ```powershell
    Get-AzureADUser -All $true | Select-Object UserprincipalName,@{
        N="PasswordNeverExpires";E={$_.PasswordPolicies -contains "DisablePasswordExpiration"}
     }
    ```

- Geçerli kullanıcının masaüstünde Html'de PasswordNeverExpires bulunan tüm kullanıcıların raporunu  **ReportPasswordNeverExpires.html**

    ```powershell
    Get-AzureADUser -All $true | Select-Object UserprincipalName,@{
        N="PasswordNeverExpires";E={$_.PasswordPolicies -contains "DisablePasswordExpiration"}
    } | ConvertTo-Html | Out-File $env:userprofile\Desktop\ReportPasswordNeverExpires.html
    ```

- Geçerli kullanıcının masaüstünde CSV'de PasswordNeverExpires bulunan tüm kullanıcıların raporunu **ReportPasswordNeverExpires.csv**

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

- Bir kuruluştaki tüm kullanıcıların parolalarını hiçbir zaman sona ermeyecek şekilde ayarlamak için aşağıdaki cmdlet'i çalıştırın:

    ```powershell
    Get-AzureADUser -All $true | Set-AzureADUser -PasswordPolicies DisablePasswordExpiration
    ```

> [!WARNING]
> özniteliğine `-PasswordPolicies DisablePasswordExpiration` göre `pwdLastSet` hala yaş parametresiyle yapılandırılmış kullanıcı hesapları. özniteliğine `pwdLastSet` bağlı olarak, süre sonunu `-PasswordPolicies None`olarak değiştirirseniz, 90 günden eski bir pwdLastSet'e sahip tüm parolalar, kullanıcının bir sonraki oturum açışında bunları değiştirmesini gerektirir. Bu değişiklik çok sayıda kullanıcıyı etkileyebilir.

### <a name="set-a-password-to-expire"></a>Parolayı süresi dolacak şekilde ayarlama

Aşağıdaki komutlardan birini çalıştırın:

- Parolanın süresinin dolması için bir kullanıcının parolasını ayarlamak için UPN'yi veya kullanıcının kullanıcı kimliğini kullanarak aşağıdaki cmdlet'i çalıştırın:

    ```powershell
    Set-AzureADUser -ObjectId <user ID> -PasswordPolicies None
    ```

- Kuruluştaki tüm kullanıcıların parolalarını süresi dolacak şekilde ayarlamak için aşağıdaki cmdlet'i kullanın:

    ```powershell
    Get-AzureADUser -All $true | Set-AzureADUser -PasswordPolicies None
    ```

## <a name="related-content"></a>İlgili içerik

[Kullanıcıların kendi parolalarını sıfırlamasına izin ver](../add-users/let-users-reset-passwords.md) (makale)\
[Parolaları sıfırlama](../add-users/reset-passwords.md) (makale)\
[Kuruluşunuz için parola süre sonu ilkesini ayarlama](../manage/set-password-expiration-policy.md) (makale)
