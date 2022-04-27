---
title: PowerShell ile güvenlik gruplarını yönetme
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: Güvenlik gruplarını yönetmek için PowerShell'i kullanmayı öğrenin.
ms.openlocfilehash: c1ae74e60eb00e74efe5ad881e9ce3c0ebb3cf12
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65099421"
---
# <a name="manage-security-groups-with-powershell"></a>PowerShell ile güvenlik gruplarını yönetme

*Bu makale hem Microsoft 365 Kurumsal hem de Office 365 Kurumsal için geçerlidir.*

Güvenlik gruplarını yönetmek için Microsoft 365 yönetim merkezi alternatif olarak Microsoft 365 için PowerShell'i kullanabilirsiniz. 

Bu makalede, ayarları listeleme, oluşturma, değiştirme ve güvenlik gruplarını kaldırma işlemleri açıklanmaktadır. 

Bu makaledeki bir komut bloğu değişken değerleri belirtmenizi gerektirdiğinde bu adımları kullanın.

1. Komut bloğunu panoya kopyalayın ve Not Defteri veya PowerShell Tümleşik Betik Ortamı'na (ISE) yapıştırın.
2. Değişken değerlerini doldurun ve "<" ve ">" karakterlerini kaldırın.
3. Komutları PowerShell penceresinde veya PowerShell ISE'de çalıştırın.

PowerShell ile [grup üyeliğini](maintain-group-membership-with-microsoft-365-powershell.md) yönetmek için bkz. Güvenlik grubu üyeliğini koruma.

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Graph için Azure Active Directory PowerShell modülünü kullanma

İlk olarak [Microsoft 365 kiracınıza bağlanın](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).

### <a name="list-your-groups"></a>Gruplarınızı listeleme

Tüm gruplarınızı listelemek için bu komutu kullanın.

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

Bu komutlarla grubun ayarlarını görüntüleyin.

```powershell
$groupName="<display name of the group>"
Get-AzureADGroup | Where { $_.DisplayName -eq $groupName } | Select *
```

Ardından, bir ayarın nasıl değiştirileceğini belirlemek için [Set-AzureADGroup](/powershell/module/azuread/set-azureadgroup) makalesini kullanın.

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
Bir güvenlik grubunun geçerli sahiplerine **kullanıcı asıl adına (UPN)** göre bir kullanıcı hesabı eklemek için bu komutları kullanın.

```powershell
$userUPN="<UPN of the user account to add>"
$groupName="<display name of the group>"
Add-AzureADGroupOwner -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectId -RefObjectId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectId
```
Bir güvenlik grubunun geçerli sahiplerine **görünen adına** göre bir kullanıcı hesabı eklemek için bu komutları kullanın.

```powershell
$userName="<Display name of the user account to add>"
$groupName="<display name of the group>"
Add-AzureADGroupOwner -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectId -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $userName }).ObjectId
```
Bir güvenlik grubunun geçerli sahiplerine **UPN'siyle** kullanıcı hesabını kaldırmak için bu komutları kullanın.

```powershell
$userUPN="<UPN of the user account to remove>"
$groupName="<display name of the group>"
Remove-AzureADGroupOwner -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectId -OwnerId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectId
```

Bir güvenlik grubunun geçerli sahiplerine görünen **adıyla** kullanıcı hesabını kaldırmak için bu komutları kullanın.

```powershell
$userName="<Display name of the user account to remove>"
$groupName="<display name of the group>"
Remove-AzureADGroupOwner -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectId -OwnerId (Get-AzureADUser | Where { $_.DisplayName -eq $userName }).ObjectId
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Windows PowerShell için Microsoft Azure Active Directory Modülünü kullanma

İlk olarak [Microsoft 365 kiracınıza bağlanın](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

### <a name="list-your-groups"></a>Gruplarınızı listeleme

Tüm gruplarınızı listelemek için bu komutu kullanın.

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

Bu komutlarla grubun ayarlarını görüntüleyin.

```powershell
$groupName="<display name of the group>"
Get-MsolGroup | Where { $_.DisplayName -eq $groupName } | Select *
```

Ardından, bir ayarın nasıl değiştirileceğini belirlemek için [Set-MsolGroup](/powershell/module/msonline/set-msolgroup) makalesini kullanın.

### <a name="remove-a-security-group"></a>Güvenlik grubunu kaldırma

Güvenlik grubunu kaldırmak için bu komutları kullanın.

```powershell
$groupName="<display name of the group>"
Remove-MsolGroup -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectId
```

## <a name="see-also"></a>Ayrıca bkz.

[PowerShell ile Microsoft 365 kullanıcı hesaplarını, lisanslarını ve gruplarını yönetme](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
  
[PowerShell ile Microsoft 365’i yönetme](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[Microsoft 365 için PowerShell'i kullanmaya başlama](getting-started-with-microsoft-365-powershell.md)