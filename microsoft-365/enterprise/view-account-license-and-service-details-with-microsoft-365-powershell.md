---
title: PowerShell Microsoft 365 lisansı ve hizmet ayrıntılarını görüntüleme
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
description: Kullanıcılara atanmış olan her hizmet için Microsoft 365 PowerShell'in nasıl kullanıldığı açıklarıdır.
ms.openlocfilehash: c02d3ffe2fff330f46adfc6b6dd49e553f69ad86
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62988725"
---
# <a name="view-microsoft-365-account-license-and-service-details-with-powershell"></a>PowerShell Microsoft 365 lisansı ve hizmet ayrıntılarını görüntüleme

*Bu makale hem son hem de Microsoft 365 Kurumsal hem de Office 365 Kurumsal.*

Lisans Microsoft 365 lisans planlarının lisansları (SKU'lar veya Microsoft 365 planları olarak da adlandırılan), kullanıcılara bu planlar için tanımlanmış Microsoft 365 hizmetleri için erişim sağlar. Bununla birlikte, kullanıcı o anda ona atanmış olan lisansta bulunan tüm hizmetlere erişim sahibi olamabilir. Kullanıcı hesaplarından hizmetlerin durumunu Microsoft 365 için PowerShell for Microsoft 365'i kullanabilirsiniz. 

Lisans planları, lisanslar ve hizmetler hakkında daha fazla bilgi için bkz [. PowerShell ile lisansları ve hizmetleri görüntüleme](view-licenses-and-services-with-microsoft-365-powershell.md).

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Graph modülü için Azure Active Directory PowerShell'i kullanma

İlk olarak[, kiracınıza bağlan Microsoft 365 bağlanin](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
  
Ardından, bu komutla kiracınıza uygun lisans planlarını listelenin.

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

Her lisans planında bulunan hizmetleri liste için bu komutları kullanın.

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

Kullanıcı hesabına atanan lisansları liste için bu komutları kullanın.

```powershell
$userUPN="<user account UPN, such as belindan@contoso.com>"
$licensePlanList = Get-AzureADSubscribedSku
$userList = Get-AzureADUser -ObjectID $userUPN | Select -ExpandProperty AssignedLicenses | Select SkuID 
$userList | ForEach { $sku=$_.SkuId ; $licensePlanList | ForEach { If ( $sku -eq $_.ObjectId.substring($_.ObjectId.length - 36, 36) ) { Write-Host $_.SkuPartNumber } } }
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Kaynak için Microsoft Azure Active Directory Modülü'Windows PowerShell

İlk olarak[, kiracınıza bağlan Microsoft 365 bağlanin](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

Ardından, bu komutu çalıştırarak, kurumda kullanılabilen lisans planlarını listelenin. 

```powershell
Get-MsolAccountSku
```
>[!Note]
>PowerShell Core, **Msol'Microsoft Azure Active Directory Msol** Windows PowerShell cmdlet'leri için Modül Adını Desteklemez. Bu cmdlet'leri kullanmaya devam etmek için, tüm cmdlet'leri Windows PowerShell.
>

Ardından, bu komutu çalıştırarak her lisans planında bulunan hizmetleri ve bunların liste sırası (dizin numarası) listelenin.

```powershell
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "<AccountSkuId>"}).ServiceStatus
```
  
Bir kullanıcıya atanan lisansları ve bunların liste sırası (dizin numarası) için bu komutu kullanın.

```powershell
Get-MsolUser -UserPrincipalName <user account UPN> | Format-List DisplayName,Licenses
```

### <a name="to-view-services-for-a-user-account"></a>Kullanıcı hesabının hizmetlerini görüntülemek için

Kullanıcının erişimi olan Microsoft 365 tüm hizmetlerde görüntülemek için, aşağıdaki söz dizimi kullanın:
  
```powershell
(Get-MsolUser -UserPrincipalName <user account UPN>).Licenses[<LicenseIndexNumber>].ServiceStatus
```

Bu örnekte, kullanıcının hangi hizmetlere BelindaN@litwareinc.com olduğu gösterir. Bu, hesabına atanan tüm lisanslarla ilişkilendirilmiş hizmetleri gösterir.
  
```powershell
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses.ServiceStatus
```

Bu örnekte, kullanıcıya BelindaN@litwareinc.com hesabına atanan ilk lisanstan erişim izni olan hizmetler (dizin numarası 0'dır) gösterir.
  
```powershell
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses[0].ServiceStatus
```

Birden çok lisans atanmış bir kullanıcının tüm hizmetlerini görüntülemek *için aşağıdaki söz* dizimi kullanın:

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

[PowerShell Microsoft 365 hesaplarını, lisanslarını ve gruplarını yönetme](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
  
[PowerShell Microsoft 365'i yönetme](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[Microsoft 365 için PowerShell ile çalışmaya Microsoft 365](getting-started-with-microsoft-365-powershell.md)
