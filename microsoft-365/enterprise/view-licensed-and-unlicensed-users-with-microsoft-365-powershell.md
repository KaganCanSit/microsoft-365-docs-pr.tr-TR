---
title: PowerShell ile lisanslı ve lisanssız Microsoft 365 kullanıcılarını görüntüleme
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
description: Bu makalede, lisanslı ve lisanssız Microsoft 365 kullanıcı hesaplarını görüntülemek için PowerShell'in nasıl kullanılacağı açıklanmaktadır.
ms.openlocfilehash: 1be54b20d3b50985fea8eb665a1b6098a26aa703
ms.sourcegitcommit: 195e4734d9a6e8e72bd355ee9f8bca1f18577615
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/13/2022
ms.locfileid: "64823641"
---
# <a name="view-licensed-and-unlicensed-microsoft-365-users-with-powershell"></a>PowerShell ile lisanslı ve lisanssız Microsoft 365 kullanıcılarını görüntüleme

*Bu makale hem Microsoft 365 Kurumsal hem de Office 365 Kurumsal için geçerlidir.*

Microsoft 365 kuruluşunuzdaki kullanıcı hesaplarının, kuruluşunuzda bulunan lisans planlarından kendilerine atanmış olan lisansların bir kısmı, tümü veya hiçbiri olabilir. Kuruluşunuzdaki lisanslı ve lisanssız kullanıcıları hızla bulmak için Microsoft 365 için PowerShell'i kullanabilirsiniz.

## <a name="use-the-microsoft-graph-powershell-sdk"></a>Microsoft Graph PowerShell SDK'sını kullanma

İlk olarak [Microsoft 365 kiracınıza bağlanın](/graph/powershell/get-started#authentication).

Lisans ayrıntıları dahil olmak üzere kullanıcı özelliklerinin okunması için User.Read.All izin kapsamı veya ['Kullanıcı edinin' Graph API başvuru sayfasında](/graph/api/user-get) listelenen diğer izinlerden biri gerekir.

Kiracıda bulunan lisansları okumak için Organization.Read.All izin kapsamı gereklidir.

```powershell
Connect-Graph -Scopes User.Read.All, Organization.Read.All
```

Belirli bir kullanıcı hesabının lisans ayrıntılarını görüntülemek için aşağıdaki komutu çalıştırın:
  
```powershell
Get-MgUserLicenseDetail -UserId "<user sign-in name (UPN)>"
```

Örneğin:

```powershell
Get-MgUserLicenseDetail -UserId "belindan@litwareinc.com"
```

Kuruluşunuzda lisans planlarınızdan herhangi birine (lisanssız kullanıcılar) atanmamış tüm kullanıcı hesaplarının listesini görüntülemek için aşağıdaki komutu çalıştırın:
  
```powershell
Get-MgUser -Filter 'assignedLicenses/$count eq 0' -ConsistencyLevel eventual -CountVariable unlicensedUserCount -All

Write-Host "Found $unlicensedUserCount unlicensed users."
```

Kuruluşunuzda lisans planlarınızdan herhangi birine (lisanssız kullanıcılar) atanmamış tüm üye kullanıcı hesaplarının (konuklar hariç) listesini görüntülemek için aşağıdaki komutu çalıştırın:
  
```powershell
Get-MgUser -Filter "assignedLicenses/`$count eq 0 and userType eq 'Member'" -ConsistencyLevel eventual -CountVariable unlicensedUserCount -All

Write-Host "Found $unlicensedUserCount unlicensed users (excluding guests)."
```

Kuruluşunuzda lisans planlarınızdan herhangi birine (lisanslı kullanıcılar) atanmış tüm kullanıcı hesaplarının listesini görüntülemek için aşağıdaki komutu çalıştırın:
  
```powershell
Get-MgUser -Filter 'assignedLicenses/$count ne 0' -ConsistencyLevel eventual -CountVariable licensedUserCount -All -Select UserPrincipalName,DisplayName,AssignedLicenses | Format-Table -Property UserPrincipalName,DisplayName,AssignedLicenses

Write-Host "Found $licensedUserCount licensed users."
```

Kuruluşunuzda E5 lisansı atanmış olan tüm kullanıcı hesaplarının listesini görüntülemek için aşağıdaki komutu çalıştırın:

```powershell
$e5Sku = Get-MgSubscribedSku -All | Where SkuPartNumber -eq 'SPE_E5'

Get-MgUser -Filter "assignedLicenses/any(x:x/skuId eq $($e5sku.SkuId) )" -ConsistencyLevel eventual -CountVariable e5licensedUserCount -All

Write-Host "Found $e5licensedUserCount E5 licensed users."
```

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Graph için Azure Active Directory PowerShell modülünü kullanma

İlk olarak [Microsoft 365 kiracınıza bağlanın](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
 
Kuruluşunuzda lisans planlarınızdan herhangi birine (lisanssız kullanıcılar) atanmamış tüm kullanıcı hesaplarının listesini görüntülemek için aşağıdaki komutu çalıştırın:
  
```powershell
Get-AzureAdUser | ForEach{ $licensed=$False ; For ($i=0; $i -le ($_.AssignedLicenses | Measure).Count ; $i++) { If( [string]::IsNullOrEmpty(  $_.AssignedLicenses[$i].SkuId ) -ne $True) { $licensed=$true } } ; If( $licensed -eq $false) { Write-Host $_.UserPrincipalName} }
```

Kuruluşunuzda lisans planlarınızdan herhangi birine (lisanslı kullanıcılar) atanmış tüm kullanıcı hesaplarının listesini görüntülemek için aşağıdaki komutu çalıştırın:
  
```powershell
Get-AzureAdUser | ForEach { $licensed=$False ; For ($i=0; $i -le ($_.AssignedLicenses | Measure).Count ; $i++) { If( [string]::IsNullOrEmpty(  $_.AssignedLicenses[$i].SkuId ) -ne $True) { $licensed=$true } } ; If( $licensed -eq $true) { Write-Host $_.UserPrincipalName} }
```

>[!Note]
>Aboneliğinizdeki tüm kullanıcıları listelemek için komutunu kullanın `Get-AzureAdUser -All $true` .
>

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Windows PowerShell için Microsoft Azure Active Directory Modülünü kullanma

İlk olarak [Microsoft 365 kiracınıza bağlanın](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

Kuruluşunuzdaki tüm kullanıcı hesaplarının ve lisans durumlarının listesini görüntülemek için PowerShell'de aşağıdaki komutu çalıştırın:
  
```powershell
Get-MsolUser -All
```

>[!Note]
>PowerShell Core, Windows PowerShell modülü için Microsoft Azure Active Directory Modülünü ve adında **Msol** bulunan cmdlet'leri desteklemez. Bu cmdlet'leri kullanmaya devam etmek için bunları Windows PowerShell çalıştırmanız gerekir.
>

Kuruluşunuzdaki tüm lisanssız kullanıcı hesaplarının listesini görüntülemek için aşağıdaki komutu çalıştırın:
  
```powershell
Get-MsolUser -All -UnlicensedUsersOnly
```

Kuruluşunuzdaki tüm lisanslı kullanıcı hesaplarının listesini görüntülemek için aşağıdaki komutu çalıştırın:
  
```powershell
Get-MsolUser -All | where {$_.isLicensed -eq $true}
```

## <a name="see-also"></a>Ayrıca bkz.

[PowerShell ile Microsoft 365 kullanıcı hesaplarını, lisanslarını ve gruplarını yönetme](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
  
[PowerShell ile Microsoft 365’i yönetme](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[Microsoft 365 için PowerShell'i kullanmaya başlama](getting-started-with-microsoft-365-powershell.md)
