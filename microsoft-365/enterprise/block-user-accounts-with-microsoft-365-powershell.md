---
title: PowerShell Microsoft 365 hesaplarını engelleme
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 07/16/2020
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- Ent_Office_Other
- PowerShell
- seo-marvel-apr2020
ms.assetid: 04e58c2a-400b-496a-acd4-8ec5d37236dc
description: Hesaplara erişimi engellemek ve hesapların engellemesini kaldırmak için PowerShell Microsoft 365 kullanın.
ms.openlocfilehash: 0ecfdfb8f99175ce5312769593c7637a7d1ae25b
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62985151"
---
# <a name="block-microsoft-365-user-accounts-with-powershell"></a>PowerShell Microsoft 365 hesaplarını engelleme

*Bu makale hem son hem de Microsoft 365 Kurumsal hem de Office 365 Kurumsal.*

Microsoft 365 hesabına erişimi engelle işaretleyen, herkesin bu hesabı kullanarak oturum açmasını ve Microsoft 365 engellemeniz gerekir. Tek tek veya birden çok kullanıcı hesabına erişimi engellemek için PowerShell kullanabilirsiniz.

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Graph modülü için Azure Active Directory PowerShell'i kullanma

İlk olarak[, kiracınıza bağlan Microsoft 365 bağlanin](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).

### <a name="block-access-to-individual-user-accounts"></a>Tek tek kullanıcı hesaplarına erişimi engelleme

Tek bir kullanıcı hesabını engellemek için aşağıdaki söz dizimi kullanın:

```powershell
Set-AzureADUser -ObjectID <sign-in name of the user account> -AccountEnabled $false
```

> [!NOTE]
> **Set-AzureAD** cmdlet'inin *-ObjectID* parametresi, Kullanıcı Asıl Adı olarak da bilinen hesap oturum açma adını veya hesabın nesne kimliğini kabul eder.

Bu örnekte, kullanıcı hesabına veya posta hesabına *fabricec@litwareinc.com*.

```powershell
Set-AzureADUser -ObjectID fabricec@litwareinc.com -AccountEnabled $false
```

Bu kullanıcı hesabının engellemesini kaldırmak için aşağıdaki komutu çalıştırın:

```powershell
Set-AzureADUser -ObjectID fabricec@litwareinc.com -AccountEnabled $true
```

Kullanıcının görünen adına bağlı olarak kullanıcı hesabı UPN'lerini görüntülemek için aşağıdaki komutları kullanın:

```powershell
$userName="<display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName

```

Bu örnekte, kullanıcı Veya Sills kullanıcı için kullanıcı hesabı  *UPN'si görüntülenir*.

```powershell
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

Kullanıcının görünen adına göre hesabı engellemek için aşağıdaki komutları kullanın:

```powershell
$userName="<display name>"
Set-AzureADUser -ObjectID (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName -AccountEnabled $false

```

Kullanıcı hesabının engellenmiş durumunu kontrol etmek için aşağıdaki komutu kullanın:

```powershell
Get-AzureADUser  -ObjectID <UPN of user account> | Select DisplayName,AccountEnabled
```

### <a name="block-multiple-user-accounts"></a>Birden çok kullanıcı hesabını engelleme

Birden çok kullanıcı hesabına erişimi engellemek için, her satırda bir hesap oturum açma adı içeren bir metin dosyası oluşturun:

  ```powershell
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

Aşağıdaki komutlarda, örnek metin dosyası *şu şekildedir: C:\Documents\Accounts.txt*. Bu dosya adını metin dosyanın yolu ve dosya adıyla değiştirin.

Metin dosyasında listelenen hesaplara erişimi engellemek için aşağıdaki komutu çalıştırın:

```powershell
Get-Content "C:\My Documents\Accounts.txt" | ForEach {Set-AzureADUser -ObjectID $_ -AccountEnabled $false}
```

Metin dosyasında listelenen hesapların engellemesini kaldırmak için aşağıdaki komutu çalıştırın:

```powershell
Get-Content "C:\My Documents\Accounts.txt" | ForEach {Set-AzureADUser -ObjectID $_ -AccountEnabled $true}
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Kaynak için Microsoft Azure Active Directory Modülü'Windows PowerShell

İlk olarak[, kiracınıza bağlan Microsoft 365 bağlanin](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

### <a name="block-individual-user-accounts"></a>Tek tek kullanıcı hesaplarını engelleme

Tek bir kullanıcı hesabına erişimi engellemek için aşağıdaki söz dizimi kullanın:

```powershell
Set-MsolUser -UserPrincipalName <sign-in name of user account>  -BlockCredential $true
```

>[!Note]
>PowerShell Core, *Msol'Microsoft Azure Active Directory Msol* Windows PowerShell cmdlet'ler için Modülünü desteklemez. Bu cmdlet'leri kendi Windows PowerShell.

Bu örnekte, *Fabricec kullanıcı hesabı fabricec litwareinc.com\@*.

```powershell
Set-MsolUser -UserPrincipalName fabricec@litwareinc.com -BlockCredential $true
```

Kullanıcı hesabının engellemesini kaldırmak için aşağıdaki komutu çalıştırın:

```powershell
Set-MsolUser -UserPrincipalName <sign-in name of user account>  -BlockCredential $false
```

Kullanıcı hesabının engellenmiş durumunu kontrol etmek için aşağıdaki komutu çalıştırın:

```powershell
Get-MsolUser -UserPrincipalName <sign-in name of user account> | Select DisplayName,BlockCredential
```

### <a name="block-access-for-multiple-user-accounts"></a>Birden çok kullanıcı hesabı için erişimi engelleme

İlk olarak, her satırda bir hesap içeren bir metin dosyası oluşturun:

```powershell
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
```

Aşağıdaki komutlarda, örnek metin dosyası *şu şekildedir: C:\Documents\Accounts.txt*. Bu dosya adını metin dosyanın yolu ve dosya adıyla değiştirin.

Metin dosyasında listelenen hesaplara erişimi engellemek için aşağıdaki komutu çalıştırın:

  ```powershell
  Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-MsolUser -UserPrincipalName $_ -BlockCredential $true }
  ```
Metin dosyasında listelenen hesapların engellemesini kaldırmak için aşağıdaki komutu çalıştırın:

  ```powershell
  Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-MsolUser -UserPrincipalName $_ -BlockCredential $false }
  ```

## <a name="see-also"></a>Ayrıca bkz.

[PowerShell Microsoft 365 hesaplarını, lisanslarını ve gruplarını yönetme](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)

[PowerShell Microsoft 365'i yönetme](manage-microsoft-365-with-microsoft-365-powershell.md)

[Microsoft 365 için PowerShell'i Microsoft 365](getting-started-with-microsoft-365-powershell.md)
