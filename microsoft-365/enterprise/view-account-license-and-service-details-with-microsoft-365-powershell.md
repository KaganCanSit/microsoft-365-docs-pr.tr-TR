---
title: PowerShell ile Microsoft 365 hesabı lisansı ve hizmet ayrıntılarını görüntüleme
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 07/17/2020
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
- LIL_Placement
ms.assetid: ace07d8a-15ca-4b89-87f0-abbce809b519
description: Kullanıcılara atanmış Microsoft 365 hizmetlerini belirlemek için PowerShell'in nasıl kullanılacağını açıklar.
ms.openlocfilehash: 2789026e2e22bbae3e84e91ada7ad21af2252f03
ms.sourcegitcommit: 195e4734d9a6e8e72bd355ee9f8bca1f18577615
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/13/2022
ms.locfileid: "64823970"
---
# <a name="view-microsoft-365-account-license-and-service-details-with-powershell"></a>PowerShell ile Microsoft 365 hesabı lisansı ve hizmet ayrıntılarını görüntüleme

*Bu makale hem Microsoft 365 Kurumsal hem de Office 365 Kurumsal için geçerlidir.*

Microsoft 365'de lisans planlarından (SKU'lar veya Microsoft 365 planları olarak da adlandırılır) lisanslar, kullanıcılara bu planlar için tanımlanan Microsoft 365 hizmetlerine erişim sağlar. Ancak, bir kullanıcının şu anda kendisine atanmış bir lisansta bulunan tüm hizmetlere erişimi olmayabilir. Kullanıcı hesaplarında hizmetlerin durumunu görüntülemek için Microsoft 365 için PowerShell'i kullanabilirsiniz.

Lisans planları, lisans ve hizmetler hakkında daha fazla bilgi için bkz. [PowerShell ile lisansları ve hizmetleri görüntüleme](view-licenses-and-services-with-microsoft-365-powershell.md).

## <a name="use-the-microsoft-graph-powershell-sdk"></a>Microsoft Graph PowerShell SDK'sını kullanma

İlk olarak [Microsoft 365 kiracınıza bağlanın](/graph/powershell/get-started#authentication).

Lisans ayrıntıları dahil olmak üzere kullanıcı özelliklerinin okunması için User.Read.All izin kapsamı veya ['Kullanıcı edinin' Graph API başvuru sayfasında](/graph/api/user-get) listelenen diğer izinlerden biri gerekir.

```powershell
Connect-Graph -Scopes User.Read.All
```

Ardından, bu komutla kiracınızın lisans planlarını listeleyin.

```powershell
Get-MgSubscribedSku
```

Her lisans planında kullanılabilen hizmetleri listelemek için bu komutları kullanın.

```powershell

$allSKUs = Get-MgSubscribedSku -Property SkuPartNumber, ServicePlans 
$allSKUs | ForEach-Object {
    Write-Host "Service Plan:" $_.SkuPartNumber
    $_.ServicePlans | ForEach-Object {$_}
}

```

Bir kullanıcı hesabına atanan lisansları listelemek için bu komutları kullanın.

```powershell
Get-MgUserLicenseDetail -UserId "<user sign-in name (UPN)>"
```

Örneğin:

```powershell
Get-MgUserLicenseDetail -UserId "belindan@litwareinc.com"
```

### <a name="to-view-services-for-a-user-account"></a>Kullanıcı hesabının hizmetlerini görüntülemek için

Kullanıcının erişimi olan tüm Microsoft 365 hizmetlerini görüntülemek için aşağıdaki söz dizimini kullanın:
  
```powershell
(Get-MgUserLicenseDetail -UserId <user account UPN> -Property ServicePlans)[<LicenseIndexNumber>].ServicePlans
```

Bu örnekte, kullanıcının BelindaN@litwareinc.com erişime sahip olduğu hizmetler gösterilir. Bu, hesabına atanan tüm lisanslarla ilişkili hizmetleri gösterir.
  
```powershell
(Get-MgUserLicenseDetail -UserId belindan@litwareinc.com -Property ServicePlans).ServicePlans
```

Bu örnekte, kullanıcının BelindaN@litwareinc.com hesabına atanan ilk lisanstan erişim sahibi olduğu hizmetler gösterilir (dizin numarası 0'dır).
  
```powershell
(Get-MgUserLicenseDetail -UserId belindan@litwareinc.com -Property ServicePlans)[0].ServicePlans
```

*Birden çok lisans* atanmış bir kullanıcının tüm hizmetlerini görüntülemek için aşağıdaki söz dizimini kullanın:

```powershell
$userUPN="<user account UPN>"
$allLicenses = Get-MgUserLicenseDetail -UserId $userUPN -Property SkuPartNumber, ServicePlans
$allLicenses | ForEach-Object {
    Write-Host "License:" $_.SkuPartNumber
    $_.ServicePlans | ForEach-Object {$_}
}

```

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Graph için Azure Active Directory PowerShell modülünü kullanma

İlk olarak [Microsoft 365 kiracınıza bağlanın](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
  
Ardından, bu komutla kiracınızın lisans planlarını listeleyin.

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

Her lisans planında kullanılabilen hizmetleri listelemek için bu komutları kullanın.

```powershell
$allSKUs=Get-AzureADSubscribedSku
$licArray = @()
for($i = 0; $i -lt $allSKUs.Count; $i++)
{
$licArray += "Service Plan: " + $allSKUs[$i].SkuPartNumber
$licArray +=  Get-AzureADSubscribedSku -ObjectID $allSKUs[$i].ObjectID | Select -ExpandProperty ServicePlans
$licArray +=  ""
}
$licArray
```

Bir kullanıcı hesabına atanan lisansları listelemek için bu komutları kullanın.

```powershell
$userUPN="<user account UPN, such as belindan@contoso.com>"
$licensePlanList = Get-AzureADSubscribedSku
$userList = Get-AzureADUser -ObjectID $userUPN | Select -ExpandProperty AssignedLicenses | Select SkuID 
$userList | ForEach { $sku=$_.SkuId ; $licensePlanList | ForEach { If ( $sku -eq $_.ObjectId.substring($_.ObjectId.length - 36, 36) ) { Write-Host $_.SkuPartNumber } } }
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Windows PowerShell için Microsoft Azure Active Directory Modülünü kullanma

İlk olarak [Microsoft 365 kiracınıza bağlanın](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

Ardından, kuruluşunuzda kullanılabilen lisans planlarını listelemek için bu komutu çalıştırın. 

```powershell
Get-MsolAccountSku
```
>[!Note]
>PowerShell Core, Windows PowerShell modülü için Microsoft Azure Active Directory Modülünü ve adında **Msol** bulunan cmdlet'leri desteklemez. Bu cmdlet'leri kullanmaya devam etmek için bunları Windows PowerShell çalıştırmanız gerekir.
>

Ardından, her lisans planında kullanılabilen hizmetleri ve bunların listelenme sırasını (dizin numarası) listelemek için bu komutu çalıştırın.

```powershell
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "<AccountSkuId>"}).ServiceStatus
```
  
Kullanıcıya atanan lisansları ve bunların listelenme sırasını (dizin numarası) listelemek için bu komutu kullanın.

```powershell
Get-MsolUser -UserPrincipalName <user account UPN> | Format-List DisplayName,Licenses
```

### <a name="to-view-services-for-a-user-account"></a>Kullanıcı hesabının hizmetlerini görüntülemek için

Kullanıcının erişimi olan tüm Microsoft 365 hizmetlerini görüntülemek için aşağıdaki söz dizimini kullanın:
  
```powershell
(Get-MsolUser -UserPrincipalName <user account UPN>).Licenses[<LicenseIndexNumber>].ServiceStatus
```

Bu örnekte, kullanıcının BelindaN@litwareinc.com erişime sahip olduğu hizmetler gösterilir. Bu, hesabına atanan tüm lisanslarla ilişkili hizmetleri gösterir.
  
```powershell
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses.ServiceStatus
```

Bu örnekte, kullanıcının BelindaN@litwareinc.com hesabına atanan ilk lisanstan erişim sahibi olduğu hizmetler gösterilir (dizin numarası 0'dır).
  
```powershell
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses[0].ServiceStatus
```

*Birden çok lisans* atanmış bir kullanıcının tüm hizmetlerini görüntülemek için aşağıdaki söz dizimini kullanın:

```powershell
$userUPN="<user account UPN>"
$AllLicenses=(Get-MsolUser -UserPrincipalName $userUPN).Licenses
$licArray = @()
for($i = 0; $i -lt $AllLicenses.Count; $i++)
{
$licArray += "License: " + $AllLicenses[$i].AccountSkuId
$licArray +=  $AllLicenses[$i].ServiceStatus
$licArray +=  ""
}
$licArray
```

## <a name="see-also"></a>Ayrıca bkz.

[PowerShell ile Microsoft 365 kullanıcı hesaplarını, lisanslarını ve gruplarını yönetme](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
  
[PowerShell ile Microsoft 365’i yönetme](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[Microsoft 365 için PowerShell'i kullanmaya başlama](getting-started-with-microsoft-365-powershell.md)
