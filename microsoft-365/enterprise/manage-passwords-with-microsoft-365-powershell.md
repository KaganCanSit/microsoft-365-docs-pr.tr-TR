---
title: PowerShell ile parolaları yönetme
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
- PowerShell
- Ent_Office_Other
- O365ITProTrain
description: Parolaları yönetmek için PowerShell kullanmayı öğrenin.
ms.openlocfilehash: 64c46f774db2ae2153ea336b8afb1f1aa7536d94
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62959931"
---
# <a name="manage-passwords-with-powershell"></a>PowerShell ile parolaları yönetme

*Bu makale hem diğer Microsoft 365 Kurumsal hem de Office 365 Kurumsal.*

E-postada parolaları yönetmek Microsoft 365 alternatifi olarak Microsoft 365 yönetim merkezi için PowerShell'i Microsoft 365. 

Bu makaledeki bir komut bloğu değişken değerleri belirtmenizi gerektiriyorsa, bu adımları kullanın.

1. Komut bloğuyu panoya kopyalayın ve Not Defteri veya PowerShell Tümleşik Betik Ortamına (ISE) yapıştırın.
2. Değişken değerlerini doldurun ve "özel" ve "<" > kaldırın.
3. PowerShell penceresinde veya PowerShell ISE'de komutları çalıştırın.

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Azure Active Directory için PowerShell modülünü Graph kullanma

İlk olarak[, kiracınıza bağlan Microsoft 365 bağlanin](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).

### <a name="set-a-password"></a>Parola ayarlama

Kullanıcı hesabına parola belirtmek için bu komutları kullanın.

```powershell
$userUPN="<user account sign in name, such as belindan@contoso.com>"
$newPassword="<new password>"
$secPassword = ConvertTo-SecureString $newPassword -AsPlainText -Force
Set-AzureADUserPassword -ObjectId  $userUPN -Password $secPassword
```
### <a name="force-a-user-to-change-their-password"></a>Bir kullanıcıya parolasını değiştirmesini zorla

Parola ayarlamak ve bir kullanıcıya yeni parolasını değiştirmeye zorlamak için bu komutları kullanın.

```powershell
$userUPN="<user account sign in name, such as belindan@contoso.com>"
$newPassword="<new password>"
$secPassword = ConvertTo-SecureString $newPassword -AsPlainText -Force
Set-AzureADUserPassword -ObjectId  $userUPN -Password $secPassword -EnforceChangePasswordPolicy $true
```

Bu komutları kullanarak bir parola ayarlayın ve bir sonraki oturum açmaları için bir kullanıcı yeni parolasını değiştirmeye zorlar.

```powershell
$userUPN="<user account sign in name, such as belindan@contoso.com>"
$newPassword="<new password>"
$secPassword = ConvertTo-SecureString $newPassword -AsPlainText -Force
Set-AzureADUserPassword -ObjectId  $userUPN -Password $secPassword -ForceChangePasswordNextLogin $true
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Kaynak için Microsoft Azure Active Directory Modülü'Windows PowerShell

İlk olarak[, kiracınıza bağlan Microsoft 365 bağlanin](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

### <a name="set-a-password"></a>Parola ayarlama

Kullanıcı hesabına parola belirtmek için bu komutları kullanın.

```powershell
$userUPN="<user account sign in name>"
$newPassword="<new password>"
Set-MsolUserPassword -UserPrincipalName $userUPN -NewPassword $newPassword
```

### <a name="force-a-user-to-change-their-password"></a>Bir kullanıcıya parolasını değiştirmesini zorla

Bir kullanıcıya parolasını değiştirmeye zorlamak için bu komutları kullanın.

```powershell
$userUPN="<user account sign in name>"
Set-MsolUserPassword -UserPrincipalName $userUPN -ForceChangePassword $true
```

## <a name="see-also"></a>Ayrıca bkz.

[PowerShell Microsoft 365 hesaplarını, lisanslarını ve gruplarını yönetme](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
  
[PowerShell Microsoft 365 yönetme](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[Microsoft 365 için PowerShell ile çalışmaya Microsoft 365](getting-started-with-microsoft-365-powershell.md)

