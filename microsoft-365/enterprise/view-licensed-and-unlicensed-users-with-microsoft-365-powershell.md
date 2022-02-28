---
title: PowerShell'i olan Microsoft 365 ve lisanssız kullanıcılarını görüntüleme
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 07/21/2020
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
- O365ITProTrain
- Ent_Office_Other
- PowerShell
- seo-marvel-apr2020
ms.assetid: e4ee53ed-ed36-4993-89f4-5bec11031435
description: Bu makalede, kullanıcı hesaplarının lisanslı ve lisanssız kullanıcı hesaplarını görüntülemek Microsoft 365 açıklanmıştır.
ms.openlocfilehash: 015cb63fd692131d77799fe30fc94c6214bb01d3
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62988623"
---
# <a name="view-licensed-and-unlicensed-microsoft-365-users-with-powershell"></a>PowerShell'i olan Microsoft 365 ve lisanssız kullanıcılarını görüntüleme

*Bu makale hem son hem de Microsoft 365 Kurumsal hem de Office 365 Kurumsal.*

Microsoft 365 Microsoft 365 kullanıcı hesaplarında, kurumda kullanılabilen lisans planlarından bu hesaplara atanmış lisansların bir bazıları, hepsi veya hiçbiri bulunuyor olabilir. Microsoft 365 için PowerShell'i kullanarak, kurumdaki lisanslı ve lisanssız kullanıcıları hızla bulabilirsiniz.

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Graph modülü için Azure Active Directory PowerShell'i kullanma

İlk olarak[, kiracınıza bağlan Microsoft 365 bağlanin](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
 
Lisans planlardan herhangi biri (lisanssız kullanıcılar) atanmamış, kuruluşta yer alan tüm kullanıcı hesaplarının listesini görüntülemek için aşağıdaki komutu çalıştırın:
  
```powershell
Get-AzureAdUser | ForEach{ $licensed=$False ; For ($i=0; $i -le ($_.AssignedLicenses | Measure).Count ; $i++) { If( [string]::IsNullOrEmpty(  $_.AssignedLicenses[$i].SkuId ) -ne $True) { $licensed=$true } } ; If( $licensed -eq $false) { Write-Host $_.UserPrincipalName} }
```

Lisans planlardan herhangi biri (lisanslı kullanıcılar) atanmış olan kuruluşta tüm kullanıcı hesaplarının listesini görüntülemek için, aşağıdaki komutu çalıştırın:
  
```powershell
Get-AzureAdUser | ForEach { $licensed=$False ; For ($i=0; $i -le ($_.AssignedLicenses | Measure).Count ; $i++) { If( [string]::IsNullOrEmpty(  $_.AssignedLicenses[$i].SkuId ) -ne $True) { $licensed=$true } } ; If( $licensed -eq $true) { Write-Host $_.UserPrincipalName} }
```

>[!Note]
>Aboneliğinize dahil olan tüm kullanıcıların listesini yapmak için komutu `Get-AzureAdUser -All $true` kullanın.
>

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Kaynak için Microsoft Azure Active Directory Modülü'Windows PowerShell

İlk olarak[, kiracınıza bağlan Microsoft 365 bağlanin](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

Kurumdaki tüm kullanıcı hesaplarının listesini ve lisans durumlarını görüntülemek için PowerShell'de aşağıdaki komutu çalıştırın:
  
```powershell
Get-MsolUser -All
```

>[!Note]
>PowerShell Core, **Msol'Microsoft Azure Active Directory Msol** Windows PowerShell cmdlet'leri için Modül Adını Desteklemez. Bu cmdlet'leri kullanmaya devam etmek için, tüm cmdlet'leri Windows PowerShell.
>

Organizasyon'daki tüm lisanssız kullanıcı hesaplarının listesini görüntülemek için aşağıdaki komutu çalıştırın:
  
```powershell
Get-MsolUser -All -UnlicensedUsersOnly
```

Kuruluşta tüm lisanslı kullanıcı hesaplarının listesini görüntülemek için aşağıdaki komutu çalıştırın:
  
```powershell
Get-MsolUser -All | where {$_.isLicensed -eq $true}
```

## <a name="see-also"></a>Ayrıca bkz.

[PowerShell Microsoft 365 hesaplarını, lisanslarını ve gruplarını yönetme](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
  
[PowerShell Microsoft 365'i yönetme](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[Microsoft 365 için PowerShell ile çalışmaya Microsoft 365](getting-started-with-microsoft-365-powershell.md)
