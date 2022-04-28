---
title: PowerShell ile güvenlik grubu üyeliğini koruma
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
ms.assetid: 6770c5fa-b886-4512-8c67-ffd53226589e
description: Microsoft 365 gruplarında üyeliği korumak için PowerShell'i kullanmayı öğrenin.
ms.openlocfilehash: 48720d5f3922598feec5a64eaa2c2532e17248ad
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65095696"
---
# <a name="maintain-security-group-membership-with-powershell"></a>PowerShell ile güvenlik grubu üyeliğini koruma

*Bu makale hem Microsoft 365 Kurumsal hem de Office 365 Kurumsal için geçerlidir.*

Microsoft 365'da güvenlik grubu üyeliğini korumak için Microsoft 365 yönetim merkezi alternatif olarak Microsoft 365 için PowerShell'i kullanabilirsiniz. 

>[!Note]
>[Microsoft 365 yönetim merkezi ile Microsoft 365 grup üyeliğini korumayı öğrenin](../admin/create-groups/add-or-remove-members-from-groups.md). Ek kaynakların listesi için bkz. [Kullanıcıları ve grupları yönetme](/admin).
>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Graph için Azure Active Directory PowerShell modülünü kullanma
İlk olarak [Microsoft 365 kiracınıza bağlanın](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).

### <a name="add-or-remove-user-accounts-as-members-of-a-group"></a>Kullanıcı hesaplarını grubun üyesi olarak ekleme veya kaldırma

**UpN'sine göre kullanıcı hesabı eklemek için** kullanıcı hesabı Kullanıcı Asıl Adı (UPN) (örnek: belindan@contoso.com) ve güvenlik grubu görünen adını doldurun, "<" ve ">" karakterlerini kaldırıp bu komutları PowerShell penceresinde veya PowerShell Tümleşik Betik Ortamı'nda (ISE) çalıştırın.

```powershell
$userUPN="<UPN of the user account to add>"
$groupName="<display name of the group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

**Kullanıcı hesabını görünen adına göre eklemek için kullanıcı hesabının** görünen adını (örneğin: Belinda Newman) ve grup görünen adını doldurun ve bu komutları PowerShell penceresinde veya PowerShell ISE'de çalıştırın.

```powershell
$userName="<display name of the user account to add>"
$groupName="<display name of the group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $userName }).ObjectID -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

**Bir kullanıcı hesabını UPN'siyle kaldırmak için**, kullanıcı hesabı UPN'sini (örnek: belindan@contoso.com) ve grubun görünen adını doldurun ve bu komutları PowerShell penceresinde veya PowerShell ISE'de çalıştırın.

```powershell
$userUPN="<UPN of the user account to remove>"
$groupName="<display name of the group>"
Remove-AzureADGroupMember -MemberId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

**Bir kullanıcı hesabını görünen adına göre kaldırmak için**, kullanıcı hesabının görünen adını (örneğin: Belinda Newman) ve grup görünen adını doldurun ve bu komutları PowerShell penceresinde veya PowerShell ISE'de çalıştırın.

```powershell
$userName="<display name of the user account to remove>"
$groupName="<display name of the group>"
Remove-AzureADGroupMember -MemberId (Get-AzureADUser | Where { $_.DisplayName -eq $userName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

### <a name="add-or-remove-groups-as-members-of-a-group"></a>Grupları grubun üyesi olarak ekleme veya kaldırma

Güvenlik grupları, üye olarak diğer grupları içerebilir. Ancak Microsoft 365 gruplar bunu yapamaz. Bu bölüm, yalnızca bir güvenlik grubu için grup eklemek veya kaldırmak için PowerShell komutlarını içerir.

**Bir grubu görünen adına göre eklemek için**, ekleyeceğiniz grubun görünen adını ve üye grubu içerecek grubun görünen adını doldurun ve bu komutları PowerShell penceresinde veya PowerShell ISE'de çalıştırın.

```powershell
$groupMemberName="<display name of the group to add>"
$groupName="<display name of the group that will contain the member group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

**Bir grubu görünen adına göre kaldırmak için**, kaldıracağınız grubun görünen adını ve üye grubu içerecek grubun görünen adını doldurun ve bu komutları PowerShell penceresinde veya PowerShell ISE'de çalıştırın.

```powershell
$groupMemberName="<display name of the group to add>"
$groupName="<display name of the group that will contain the member group>"
Remove-AzureADGroupMember -MemberId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Windows PowerShell için Microsoft Azure Active Directory Modülünü kullanma

İlk olarak [Microsoft 365 kiracınıza bağlanın](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).


### <a name="add-or-remove-user-accounts-as-members-of-a-group"></a>Kullanıcı hesaplarını grubun üyesi olarak ekleme veya kaldırma

**UPN'sine göre kullanıcı hesabı eklemek için** kullanıcı hesabı Kullanıcı Asıl Adı (UPN) (örnek: belindan@contoso.com) ve grup görünen adını doldurun, "<" ve ">" karakterlerini kaldırıp bu komutları PowerShell penceresinde veya PowerShell ISE'de çalıştırın.

```powershell
$userUPN="<UPN of the user account to add>"
$groupName="<display name of the group>"
Add-MsolGroupMember -GroupMemberObjectId (Get-MsolUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

**Kullanıcı hesabını görünen adına göre eklemek için kullanıcı hesabının** görünen adını (örneğin: Belinda Newman) ve grup görünen adını doldurun ve bu komutları PowerShell penceresinde veya PowerShell ISE'de çalıştırın.

```powershell
$userName="<display name of the user account to add>"
$groupName="<display name of the group>"
Add-MsolGroupMember -GroupMemberObjectId (Get-MsolUser | Where { $_.DisplayName -eq $userName }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

**Bir kullanıcı hesabını UPN'siyle kaldırmak için**, kullanıcı hesabı UPN'sini (örnek: belindan@contoso.com) ve grubun görünen adını doldurun ve bu komutları PowerShell penceresinde veya PowerShell ISE'de çalıştırın.

```powershell
$userUPN="<UPN of the user account to remove>"
$groupName="<display name of the group>"
Remove-MsolGroupMember -GroupMemberObjectId (Get-MsolUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

**Bir kullanıcı hesabını görünen adına göre kaldırmak için**, kullanıcı hesabının görünen adını (örneğin: Belinda Newman) ve grup görünen adını doldurun ve bu komutları PowerShell penceresinde veya PowerShell ISE'de çalıştırın.

```powershell
$userName="<display name of the user account to remove>"
$groupName="<display name of the group>"
Remove-MsolGroupMember -GroupMemberObjectId (Get-MsolUser | Where { $_.DisplayName -eq $userName }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

### <a name="add-or-remove-groups-as-members-of-a-group"></a>Grupları grubun üyesi olarak ekleme veya kaldırma

Güvenlik grupları, üye olarak diğer grupları içerebilir. Ancak Microsoft 365 gruplar bunu yapamaz. Bu bölüm, yalnızca bir güvenlik grubu için grup eklemek veya kaldırmak için PowerShell komutlarını içerir.

**Bir grubu görünen adına göre eklemek için**, ekleyeceğiniz grubun görünen adını ve üye grubu içerecek grubun görünen adını doldurun ve bu komutları PowerShell penceresinde veya PowerShell ISE'de çalıştırın.

```powershell
$groupMemberName="<display name of the group to add>"
$groupName="<display name of the group that will contain the member group>"
Add-MsolGroupMember -GroupMemberObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID -GroupMemberType Group
```

**Bir grubu görünen adına göre kaldırmak için**, kaldıracağınız grubun görünen adını ve üye grubu içerecek grubun görünen adını doldurun ve bu komutları PowerShell penceresinde veya PowerShell ISE'de çalıştırın.

```powershell
$groupMemberName="<display name of the group to add>"
$groupName="<display name of the group contains the member group>"
Remove-MsolGroupMember -GroupMemberObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID -GroupMemberType Group
```

## <a name="see-also"></a>Ayrıca bkz.

[PowerShell ile Microsoft 365 kullanıcı hesaplarını, lisanslarını ve gruplarını yönetme](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
  
[PowerShell ile Microsoft 365’i yönetme](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[Microsoft 365 için PowerShell'i kullanmaya başlama](getting-started-with-microsoft-365-powershell.md)