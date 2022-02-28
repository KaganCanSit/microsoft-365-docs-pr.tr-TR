---
title: PowerShell Microsoft 365 hesaplarını silme
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 09/23/2020
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
- seo-marvel-apr2020
ms.assetid: 209c9868-448c-49bc-baae-11e28b923a39
description: Kullanıcı hesaplarını silmek için PowerShell'de farklı Microsoft 365 kullanmayı öğrenin.
ms.openlocfilehash: dc1e5c53f2d356f0585da5a0a5285b9af28dc8f0
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62985553"
---
# <a name="delete-microsoft-365-user-accounts-with-powershell"></a>PowerShell Microsoft 365 hesaplarını silme

Kullanıcı hesaplarını silmek ve geri yüklemek Microsoft 365 için PowerShell'i kullanabilirsiniz.

>[!Note]
>Kullanıcı hesabını [geri yüklemek için aşağıdaki bilgileri](../admin/add-users/restore-user.md) Microsoft 365 yönetim merkezi.
>
>Ek kaynakların listesi için bkz. [Kullanıcıları ve grupları yönetme](/admin).
>   
   
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Graph modülü için Azure Active Directory PowerShell'i kullanma

İlk olarak[, kiracınıza bağlan Microsoft 365 bağlanin](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).

Bağlandikten sonra, tek bir kullanıcı hesabını kaldırmak için aşağıdaki söz dizimlerini kullanın:
  
```powershell
Remove-AzureADUser -ObjectID <sign-in name>
```

Bu örnekte, *fabricec kullanıcı hesabı fabricec\@ litwareinc.com*.
  
```powershell
Remove-AzureADUser -ObjectID fabricec@litwareinc.com
```

> [!NOTE]
> **Remove-AzureADUser** cmdlet'inde *-ObjectID* parametresi, kullanıcının Kullanıcı Asıl Adı olarak da bilinen oturum açma adını veya hesabın nesne kimliğini kabul eder.
  
Kullanıcının adına göre hesap adını görüntülemek için aşağıdaki komutları kullanın:
  
```powershell
$userName="<User name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

Bu örnekte, kullanıcının *Sills kullanıcı hesabı adı görüntülenir*.
  
```powershell
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

Kullanıcının görünen adına bağlı olarak hesabı kaldırmak için aşağıdaki komutları kullanın:
  
```powershell
$userName="<display name>"
Remove-AzureADUser -ObjectID (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Kaynak için Microsoft Azure Active Directory Modülü'Windows PowerShell

Kullanıcı hesabını Iş için Microsoft Azure Active Directory Modülü Windows PowerShell aracılığıyla sildikten sonra, hesap kalıcı olarak silinmez. Silinen kullanıcı hesabını 30 gün içinde geri yükleyebilirsiniz.

İlk olarak[, kiracınıza bağlan Microsoft 365 bağlanin](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

Kullanıcı hesabını silmek için aşağıdaki söz dizimlerini kullanın:
  
```powershell
Remove-MsolUser -UserPrincipalName <sign-in name>
```

>[!Note]
>PowerShell Core, adı *Msol* olan Microsoft Azure Active Directory Modülü Windows PowerShell cmdlet'leri desteklemez. Bu cmdlet'leri çalışma Windows PowerShell.
>

Bu örnekte, kullanıcı *hesabı hesabı BelindaN@litwareinc.com*.
  
```powershell
Remove-MsolUser -UserPrincipalName belindan@litwareinc.com
```

Silinen kullanıcı hesabını 30 günlük yetkisiz kullanım süresi içinde geri yüklemek için aşağıdaki söz dizimini kullanın:
  
```powershell
Restore-MsolUser -UserPrincipalName <sign-in name>
```

Bu örnek, silinmiş hesabı Zeynep *Yılik litwareinc.com\@*.
  
```powershell
Restore-MsolUser -UserPrincipalName BelindaN@litwareinc.com
```

>[!Note]
> Geri yüklenecek silinmiş kullanıcıların listesini görmek için aşağıdaki komutu çalıştırın:
>    
> ```powershell
> Get-MsolUser -All -ReturnDeletedUsers
> ```
>
> Kullanıcı hesabının özgün kullanıcı asıl adı başka bir hesap tarafından kullanılıyorsa, kullanıcı hesabını geri yüklemek için _UserPrincipalName yerine NewUserPrincipalName_ parametresini kullanın.


## <a name="see-also"></a>Ayrıca bkz.

[PowerShell Microsoft 365 hesaplarını, lisanslarını ve gruplarını yönetme](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
  
[PowerShell Microsoft 365'i yönetme](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[Microsoft 365 için PowerShell'i Microsoft 365](getting-started-with-microsoft-365-powershell.md)