---
title: PowerShell ile güvenlik gruplarını yönetme
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
description: Güvenlik gruplarını yönetmek için PowerShell kullanmayı öğrenin.
ms.openlocfilehash: d07296b88e626e854c57152a079cc96e1e23e8d3
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62988149"
---
# <a name="manage-security-groups-with-powershell"></a>PowerShell ile güvenlik gruplarını yönetme

*Bu makale hem son hem de Microsoft 365 Kurumsal hem de Office 365 Kurumsal.*

Güvenlik gruplarını yönetmek için Microsoft 365 alternatif olarak, Microsoft 365 yönetim merkezi PowerShell'i kullanabilirsiniz. 

Bu makalede, güvenlik gruplarını listeleme, oluşturma, ayarları değiştirme ve kaldırma açıklanmıştır. 

Bu makaledeki bir komut bloğu değişken değerleri belirtmenizi gerektiriyorsa, bu adımları kullanın.

1. Komut bloğuyu panoya kopyalayın ve Not Defteri PowerShell Tümleşik Betik Ortamına (ISE) yapıştırın.
2. Değişken değerlerini doldurun ve "özel" ve "<" > kaldırın.
3. PowerShell penceresinde veya PowerShell ISE'de komutları çalıştırın.

PowerShell [ile grup üyeliğini](maintain-group-membership-with-microsoft-365-powershell.md) yönetmek için bkz. Güvenlik grubu üyeliğini koruma.

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Graph modülü için Azure Active Directory PowerShell'i kullanma

İlk olarak[, kiracınıza bağlan Microsoft 365 bağlanin](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).

### <a name="list-your-groups"></a>Gruplarınızı listele

Tüm gruplarınızı listeley etmek için bu komutu kullanın.

```powershell
Get-AzureADGroup
```
Belirli bir grubun ayarlarını görünen adına göre görüntülemek için bu komutları kullanın.

```powershell
$groupName="<display name of the group>"
Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }
```

### <a name="create-a-new-group"></a>Yeni grup oluşturma

Yeni bir güvenlik grubu oluşturmak için bu komutu kullanın.

```powershell
New-AzureADGroup -Description "<group purpose>" -DisplayName "<name>" -MailEnabled $false -SecurityEnabled $true -MailNickName "<email name>"
```

### <a name="change-the-settings-on-a-group"></a>Gruptaki ayarları değiştirme

Bu komutlarla grubun ayarlarını görüntüleme.

```powershell
$groupName="<display name of the group>"
Get-AzureADGroup | Where { $_.DisplayName -eq $groupName } | Select *
```

Ardından, ayarın [nasıl değiştirile ilgili olduğunu belirlemek için Set-AzureADGroup](/powershell/module/azuread/set-azureadgroup) makalesini kullanın.

### <a name="remove-a-security-group"></a>Güvenlik grubunu kaldırma

Güvenlik grubunu kaldırmak için bu komutları kullanın.

```powershell
$groupName="<display name of the group>"
Remove-AzureADGroup -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectId
```

### <a name="manage-the-owners-of-a-security-group"></a>Güvenlik grubunun sahiplerini yönetme

Bir güvenlik grubunun geçerli sahiplerini görüntülemek için bu komutları kullanın.

```powershell
$groupName="<display name of the group>"
Get-AzureADGroupOwner -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectId
```
Bu komutları kullanarak bir güvenlik grubunun geçerli **sahiplerine kullanıcı asıl adı (UPN)** ile bir kullanıcı hesabı ekleyin.

```powershell
$userUPN="<UPN of the user account to add>"
$groupName="<display name of the group>"
Add-AzureADGroupOwner -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectId -RefObjectId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectId
```
Bir güvenlik grubunun geçerli sahiplerine görünen adıyla **kullanıcı** hesabı eklemek için bu komutları kullanın.

```powershell
$userName="<Display name of the user account to add>"
$groupName="<display name of the group>"
Add-AzureADGroupOwner -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectId -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $userName }).ObjectId
```
Kullanıcı hesabını **UPN'si** tarafından bir güvenlik grubunun geçerli sahiplerine kaldırmak için bu komutları kullanın.

```powershell
$userUPN="<UPN of the user account to remove>"
$groupName="<display name of the group>"
Remove-AzureADGroupOwner -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectId -OwnerId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectId
```

Bir güvenlik grubunun geçerli sahiplerine görünen adıyla **kullanıcı** hesabını kaldırmak için bu komutları kullanın.

```powershell
$userName="<Display name of the user account to remove>"
$groupName="<display name of the group>"
Remove-AzureADGroupOwner -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectId -OwnerId (Get-AzureADUser | Where { $_.DisplayName -eq $userName }).ObjectId
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Kaynak için Microsoft Azure Active Directory Modülü'Windows PowerShell

İlk olarak[, kiracınıza bağlan Microsoft 365 bağlanin](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

### <a name="list-your-groups"></a>Gruplarınızı listele

Tüm gruplarınızı listeley etmek için bu komutu kullanın.

```powershell
Get-MsolGroup
```
Belirli bir grubun ayarlarını görünen adına göre görüntülemek için bu komutları kullanın.

```powershell
$groupName="<display name of the group>"
Get-MsolGroup | Where { $_.DisplayName -eq $groupName }
```

### <a name="create-a-new-group"></a>Yeni grup oluşturma

Yeni bir güvenlik grubu oluşturmak için bu komutu kullanın.

```powershell
New-MsolGroup -Description "<group purpose>" -DisplayName "<name>"
```

### <a name="change-the-settings-on-a-group"></a>Gruptaki ayarları değiştirme

Bu komutlarla grubun ayarlarını görüntüleme.

```powershell
$groupName="<display name of the group>"
Get-MsolGroup | Where { $_.DisplayName -eq $groupName } | Select *
```

Daha sonra, [ayarın nasıl değiştirile ilgili olduğunu belirlemek için Set-MsolGroup](/powershell/module/msonline/set-msolgroup) makalesini kullanın.

### <a name="remove-a-security-group"></a>Güvenlik grubunu kaldırma

Güvenlik grubunu kaldırmak için bu komutları kullanın.

```powershell
$groupName="<display name of the group>"
Remove-MsolGroup -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectId
```

## <a name="see-also"></a>Ayrıca bkz.

[PowerShell Microsoft 365 hesaplarını, lisanslarını ve gruplarını yönetme](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
  
[PowerShell Microsoft 365'i yönetme](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[Microsoft 365 için PowerShell ile çalışmaya Microsoft 365](getting-started-with-microsoft-365-powershell.md)