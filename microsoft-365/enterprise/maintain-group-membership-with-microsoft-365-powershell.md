---
title: PowerShell ile güvenlik grubu üyeliğini koruma
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
ms.assetid: 6770c5fa-b886-4512-8c67-ffd53226589e
description: Yeni gruplarda üyeliği korumak için PowerShell Microsoft 365 öğrenin.
ms.openlocfilehash: 3637fb7d2e68091c43e624e9b6780d032c1930bc
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62988717"
---
# <a name="maintain-security-group-membership-with-powershell"></a>PowerShell ile güvenlik grubu üyeliğini koruma

*Bu makale hem son hem de Microsoft 365 Kurumsal hem de Office 365 Kurumsal.*

Microsoft 365'te güvenlik Microsoft 365 grubu üyeliğini korumak için Microsoft 365 yönetim merkezi alternatif olarak, Microsoft 365. 

>[!Note]
>[Grup üyeliğinizi nasıl Microsoft 365 bu grup üyeliğiyle](../admin/create-groups/add-or-remove-members-from-groups.md) nasıl Microsoft 365 yönetim merkezi. Ek kaynakların listesi için bkz. [Kullanıcıları ve grupları yönetme](/admin).
>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Graph modülü için Azure Active Directory PowerShell'i kullanma
İlk olarak[, kiracınıza bağlan Microsoft 365 bağlanin](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).

### <a name="add-or-remove-user-accounts-as-members-of-a-group"></a>Kullanıcı hesaplarını grubun üyeleri olarak ekleme veya kaldırma

**UPN'sini** kullanarak bir kullanıcı hesabı eklemek için, kullanıcı hesabını Kullanıcı Asıl Adı (UPN) (örnek: belindan@contoso.com) ve güvenlik grubu görünen adını doldurun, "<" ve ">" karakterlerini kaldırarak PowerShell penceresinde veya PowerShell Tümleşik Betik Ortamı'nda (ISE) bu komutları çalıştırın.

```powershell
$userUPN="<UPN of the user account to add>"
$groupName="<display name of the group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

**Kullanıcı hesabını görünen adına göre** eklemek için, kullanıcı hesabı görünen adını (örneğin: Belina Newman) ve grup görünen adını doldurun ve Bu komutları PowerShell penceresinde veya PowerShell ISE'de çalıştırın.

```powershell
$userName="<display name of the user account to add>"
$groupName="<display name of the group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $userName }).ObjectID -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

**Kullanıcı hesabını UPN'sini** kullanarak kaldırmak için, kullanıcı hesabı UPN'sini (örneğin: belindan@contoso.com) ve grup görünen adını doldurun ve bu komutları PowerShell penceresinde veya PowerShell ISE'de çalıştırın.

```powershell
$userUPN="<UPN of the user account to remove>"
$groupName="<display name of the group>"
Remove-AzureADGroupMember -MemberId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

**Kullanıcı hesabını görünen** adıyla kaldırmak için, kullanıcı hesabı görünen adını (örneğin: Belina Newman) ve grup görünen adını doldurun ve bu komutları PowerShell penceresinde veya PowerShell ISE'de çalıştırın.

```powershell
$userName="<display name of the user account to remove>"
$groupName="<display name of the group>"
Remove-AzureADGroupMember -MemberId (Get-AzureADUser | Where { $_.DisplayName -eq $userName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

### <a name="add-or-remove-groups-as-members-of-a-group"></a>Grupları grubun üyesi olarak ekleme veya kaldırma

Güvenlik grupları, üye olarak başka gruplar içerebilir. Microsoft 365, ancak gruplarda hayır. Bu bölüm, yalnızca güvenlik grubu için grup ekleme veya kaldırma PowerShell komutlarını içerir.

Grubu **görünen adına göre** eklemek için, ekleyeceksiniz grubun görünen adını ve üye grubu içeren grubun görünen adını doldurun ve bu komutları PowerShell penceresinde veya PowerShell ISE'de çalıştırın.

```powershell
$groupMemberName="<display name of the group to add>"
$groupName="<display name of the group that will contain the member group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

Grubu **görünen adına** göre kaldırmak için, kaldıracağız grubun görünen adını ve üye grubu içeren grubun görünen adını doldurun ve bu komutları PowerShell penceresinde veya PowerShell ISE'de çalıştırın.

```powershell
$groupMemberName="<display name of the group to add>"
$groupName="<display name of the group that will contain the member group>"
Remove-AzureADGroupMember -MemberId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Kaynak için Microsoft Azure Active Directory Modülü'Windows PowerShell

İlk olarak[, kiracınıza bağlan Microsoft 365 bağlanin](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).


### <a name="add-or-remove-user-accounts-as-members-of-a-group"></a>Kullanıcı hesaplarını grubun üyeleri olarak ekleme veya kaldırma

**UPN'sini** kullanarak bir kullanıcı hesabı eklemek için, kullanıcı hesabını Kullanıcı Asıl Adı (UPN) (örnek: belindan@contoso.com) ve grup görünen adını doldurun, "<" ve ">" karakterlerini kaldırarak PowerShell penceresinde veya PowerShell ISE'de bu komutları çalıştırın.

```powershell
$userUPN="<UPN of the user account to add>"
$groupName="<display name of the group>"
Add-MsolGroupMember -GroupMemberObjectId (Get-MsolUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

**Kullanıcı hesabını görünen adına göre** eklemek için, kullanıcı hesabı görünen adını (örneğin: Belina Newman) ve grup görünen adını doldurun ve Bu komutları PowerShell penceresinde veya PowerShell ISE'de çalıştırın.

```powershell
$userName="<display name of the user account to add>"
$groupName="<display name of the group>"
Add-MsolGroupMember -GroupMemberObjectId (Get-MsolUser | Where { $_.DisplayName -eq $userName }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

**Kullanıcı hesabını UPN'sini** kullanarak kaldırmak için, kullanıcı hesabı UPN'sini (örneğin: belindan@contoso.com) ve grup görünen adını doldurun ve bu komutları PowerShell penceresinde veya PowerShell ISE'de çalıştırın.

```powershell
$userUPN="<UPN of the user account to remove>"
$groupName="<display name of the group>"
Remove-MsolGroupMember -GroupMemberObjectId (Get-MsolUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

**Kullanıcı hesabını görünen** adıyla kaldırmak için, kullanıcı hesabı görünen adını (örneğin: Belina Newman) ve grup görünen adını doldurun ve bu komutları PowerShell penceresinde veya PowerShell ISE'de çalıştırın.

```powershell
$userName="<display name of the user account to remove>"
$groupName="<display name of the group>"
Remove-MsolGroupMember -GroupMemberObjectId (Get-MsolUser | Where { $_.DisplayName -eq $userName }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

### <a name="add-or-remove-groups-as-members-of-a-group"></a>Grupları grubun üyesi olarak ekleme veya kaldırma

Güvenlik grupları, üye olarak başka gruplar içerebilir. Microsoft 365, ancak gruplarda hayır. Bu bölüm, yalnızca güvenlik grubu için grup ekleme veya kaldırma PowerShell komutlarını içerir.

Grubu **görünen adına göre** eklemek için, ekleyeceksiniz grubun görünen adını ve üye grubu içeren grubun görünen adını doldurun ve bu komutları PowerShell penceresinde veya PowerShell ISE'de çalıştırın.

```powershell
$groupMemberName="<display name of the group to add>"
$groupName="<display name of the group that will contain the member group>"
Add-MsolGroupMember -GroupMemberObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID -GroupMemberType Group
```

Grubu **görünen adına** göre kaldırmak için, kaldıracağız grubun görünen adını ve üye grubu içeren grubun görünen adını doldurun ve bu komutları PowerShell penceresinde veya PowerShell ISE'de çalıştırın.

```powershell
$groupMemberName="<display name of the group to add>"
$groupName="<display name of the group contains the member group>"
Remove-MsolGroupMember -GroupMemberObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID -GroupMemberType Group
```

## <a name="see-also"></a>Ayrıca bkz.

[PowerShell Microsoft 365 hesaplarını, lisanslarını ve gruplarını yönetme](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
  
[PowerShell Microsoft 365'i yönetme](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[Microsoft 365 için PowerShell ile çalışmaya Microsoft 365](getting-started-with-microsoft-365-powershell.md)