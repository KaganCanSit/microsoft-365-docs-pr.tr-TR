---
title: PowerShell ile kullanıcı hesaplarına Microsoft 365 lisansları atama
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 09/23/2020
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- Ent_Office_Other
- LIL_Placement
- PowerShell
- O365ITProTrain
- seo-marvel-apr2020
ms.assetid: ba235f4f-e640-4360-81ea-04507a3a70be
search.appverid:
- MET150
description: Bu makalede, Lisanssız kullanıcılara Microsoft 365 lisansı atamak için PowerShell'i kullanmayı öğrenin.
ms.openlocfilehash: 3c92b3baaa0b8d67a5d5a626951b296be2516436
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/19/2022
ms.locfileid: "64941709"
---
# <a name="assign-microsoft-365-licenses-to-user-accounts-with-powershell"></a>PowerShell ile kullanıcı hesaplarına Microsoft 365 lisansları atama

*Bu makale hem Microsoft 365 Kurumsal hem de Office 365 Kurumsal için geçerlidir.*

Kullanıcılar, hesaplarına lisans planından lisans atanana kadar hiçbir Microsoft 365 hizmetini kullanamaz. Lisanssız hesaplara hızla lisans atamak için PowerShell'i kullanabilirsiniz. 

Kullanıcı hesaplarına önce bir konum atanmalıdır. Konum belirtmek, [Microsoft 365 yönetim merkezi](../admin/add-users/add-users.md) yeni bir kullanıcı hesabı oluşturmanın gerekli bir parçasıdır. 

şirket içi Active Directory Etki Alanı Hizmetlerinizden eşitlenen hesapların varsayılan olarak belirtilen bir konumu yoktur. Bu hesaplar için şu konumlardan birini yapılandırabilirsiniz:

- Microsoft 365 yönetim merkezi
- [PowerShell](configure-user-account-properties-with-microsoft-365-powershell.md)
- [Azure portal](/azure/active-directory/fundamentals/active-directory-users-profile-azure-portal) (**Active** **DirectoryKullanıçları** > , **ProfileContact** >  **infoCountry** >  veya bölge > kullanıcı hesabı >).

>[!Note]
>Microsoft 365 yönetim merkezi ile [kullanıcı hesaplarına lisans atamayı öğrenin](../admin/manage/assign-licenses-to-users.md). Ek kaynakların listesi için bkz. [Kullanıcıları ve grupları yönetme](/admin).
>

## <a name="use-the-microsoft-graph-powershell-sdk"></a>Microsoft Graph PowerShell SDK'sını kullanma

İlk olarak [Microsoft 365 kiracınıza bağlanın](/graph/powershell/get-started#authentication).

Bir kullanıcıya lisans atama ve kaldırma için User.ReadWrite.All izin kapsamı veya ['Lisans ata' Graph API başvuru sayfasında](/graph/api/user-assignlicense) listelenen diğer izinlerden biri gerekir.

Kiracıda bulunan lisansları okumak için Organization.Read.All izin kapsamı gereklidir.

```powershell
Connect-Graph -Scopes User.ReadWrite.All, Organization.Read.All
```

Kuruluşunuzdaki `Get-MgSubscribedSku` her bir plandaki kullanılabilir lisans planlarını ve kullanılabilir lisans sayısını görüntülemek için komutunu çalıştırın. Her plandaki kullanılabilir lisans sayısı **ActiveUnitsWarningUnitsConsumedUnits'tir** -  - . Lisans planları, lisanslar ve hizmetler hakkında daha fazla bilgi için bkz. [PowerShell ile lisansları ve hizmetleri görüntüleme](view-licenses-and-services-with-microsoft-365-powershell.md).

Kuruluşunuzdaki lisanssız hesapları bulmak için bu komutu çalıştırın.

```powershell
Get-MgUser -Filter 'assignedLicenses/$count eq 0' -ConsistencyLevel eventual -CountVariable unlicensedUserCount -All
```

Yalnızca **UsageLocation** özelliği geçerli bir ISO 3166-1 alfa-2 ülke koduna ayarlanmış kullanıcı hesaplarına lisans atayabilirsiniz. Örneğin, Birleşik Devletler için ABD ve Fransa için FR. Bazı Microsoft 365 hizmetleri belirli ülkelerde kullanılamaz. Daha fazla bilgi için bkz. [Lisans kısıtlamaları hakkında](https://go.microsoft.com/fwlink/p/?LinkId=691730).

**UsageLocation** değeri olmayan hesapları bulmak için bu komutu çalıştırın.

```powershell
Get-MgUser -Select Id,DisplayName,Mail,UserPrincipalName,UsageLocation,UserType | where { $_.UsageLocation -eq $null -and $_.UserType -eq 'Member' }
```

Bir hesapta **UsageLocation** değerini ayarlamak için bu komutu çalıştırın.

```powershell
$userUPN="<user sign-in name (UPN)>"
$userLoc="<ISO 3166-1 alpha-2 country code>"

Update-MgUser -UserId $userUPN -UsageLocation $userLoc
```

Örneğin:

```powershell
Update-MgUser -UserId "belindan@litwareinc.com" -UsageLocation US
```

**-All** parametresini kullanmadan **Get-MgUser** cmdlet'ini kullanırsanız, yalnızca ilk 100 hesap döndürülür.

### <a name="assigning-licenses-to-user-accounts"></a>Kullanıcı hesaplarına lisans atama

Kullanıcıya lisans atamak için PowerShell'de aşağıdaki komutu kullanın.
  
```powershell
Set-MgUserLicense -UserId $userUPN -AddLicenses @{SkuId = "<SkuId>"} -RemoveLicenses @()
```

Bu örnek **, lisanssız** kullanıcı **belindan'a\@** SPE_E5 (Microsoft 365 E5) lisans planından bir lisans atar litwareinc.com:
  
```powershell
$e5Sku = Get-MgSubscribedSku -All | Where SkuPartNumber -eq 'SPE_E5'
Set-MgUserLicense -UserId "belindan@litwareinc.com" -AddLicenses @{SkuId = $e5Sku.SkuId} -RemoveLicenses @()
```

Bu örnekte kullanıcı **belindansına\@** **SPE_E5** (Microsoft 365 E5) ve **EMSPREMIUM** (ENTERPRISE MOBILITY + SECURITY E5) atanır litwareinc.com:
  
```powershell
$e5Sku = Get-MgSubscribedSku -All | Where SkuPartNumber -eq 'SPE_E5'
$e5EmsSku = Get-MgSubscribedSku -All | Where SkuPartNumber -eq 'EMSPREMIUM'
$addLicenses = @(
    @{SkuId = $e5Sku.SkuId},
    @{SkuId = $e5EmsSku.SkuId}
)

Set-MgUserLicense -UserId "belinda@litwareinc.com" -AddLicenses $addLicenses -RemoveLicenses @()
```

Bu örnek **, MICROSOFTBOOKINGS** **(Microsoft Bookings**) ve LOCKBOX_ENTERPRISE (Müşteri Kasası) hizmetlerinin kapalı olduğu **SPE_E5 (Microsoft 365 E5**) atar:
  
```powershell
$e5Sku = Get-MgSubscribedSku -All | Where SkuPartNumber -eq 'SPE_E5'
$disabledPlans = $e5Sku.ServicePlans | `
    Where ServicePlanName -in ("LOCKBOX_ENTERPRISE", "MICROSOFTBOOKINGS") | `
    Select -ExpandProperty ServicePlanId

$addLicenses = @(
    @{
        SkuId = $e5Sku.SkuId
        DisabledPlans = $disabledPlans
    }
)

Set-MgUserLicense -UserId "belinda@litwareinc.com" -AddLicenses $addLicenses -RemoveLicenses @()
```

Bu örnek bir kullanıcıyı **SPE_E5** (Microsoft 365 E5) ile güncelleştirir ve kullanıcının mevcut devre dışı planlarını geçerli durumunda bırakırken Sway ve Forms hizmet planlarını kapatır:
  
```powershell
$userLicense = Get-MgUserLicenseDetail -UserId "belinda@fdoau.onmicrosoft.com"
$userDisabledPlans = $userLicense.ServicePlans | `
    Where ProvisioningStatus -eq "Disabled" | `
    Select -ExpandProperty ServicePlanId

$e5Sku = Get-MgSubscribedSku -All | Where SkuPartNumber -eq 'SPE_E5'
$newDisabledPlans = $e5Sku.ServicePlans | `
    Where ServicePlanName -in ("SWAY", "FORMS_PLAN_E5") | `
    Select -ExpandProperty ServicePlanId

$disabledPlans = ($userDisabledPlans + $newDisabledPlans) | Select -Unique

$addLicenses = @(
    @{
        SkuId = $e5Sku.SkuId
        DisabledPlans = $disabledPlans
    }
)

Set-MgUserLicense -UserId "belinda@litwareinc.onmicrosoft.com" -AddLicenses $addLicenses -RemoveLicenses @()
```

### <a name="assign-licenses-to-a-user-by-copying-the-license-assignment-from-another-user"></a>Lisans atamasını başka bir kullanıcıdan kopyalayarak kullanıcıya lisans atama

Bu örnekte **jamesp\@ litwareinc.com** **belindan'a\@** uygulanan lisanslama planıyla aynı şekilde atanır litwareinc.com:

```powershell
$mgUser = Get-MgUser -UserId "belindan@litwareinc.com"
Set-MgUserLicense -UserId "jamesp@litwareinc.com" -AddLicenses $mgUser.AssignedLicenses -RemoveLicenses @()
```

### <a name="move-a-user-to-a-different-subscription-license-plan"></a>Kullanıcıyı farklı bir aboneliğe taşıma (lisans planı)

Bu örnek, kullanıcıyı **SPE_E3 (Microsoft 365 E3**) lisans planından **SPE_E5 (Microsoft 365 E5**) lisans planına yükseltmektedir:

```powershell
$e3Sku = Get-MgSubscribedSku -All | Where SkuPartNumber -eq 'SPE_E3'
$e5Sku = Get-MgSubscribedSku -All | Where SkuPartNumber -eq 'SPE_E5'

# Unassign E3
Set-MgUserLicense -UserId "belindan@litwareinc.com" -AddLicenses @{} -RemoveLicenses @($e3Sku.SkuId)
# Assign E5
Set-MgUserLicense -UserId "belindan@litwareinc.com" -AddLicenses @{SkuId = $e5Sku.SkuId} -RemoveLicenses @()
```

Bu komutla kullanıcı hesabı için abonelikteki değişikliği doğrulayabilirsiniz.

```powershell
Get-MgUserLicenseDetail -UserId "belindan@litwareinc.com"
```

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Graph için Azure Active Directory PowerShell modülünü kullanma

>[!Note]
>Set-AzureADUserLicense cmdlet'i kullanımdan kaldırılacak şekilde zamanlanmıştır. Lütfen betiklerinizi yukarıda açıklandığı gibi Microsoft Graph SDK'sının Set-MgUserLicense cmdlet'ine geçirin. Daha fazla bilgi için bkz[. Microsoft Graph lisans yönetimi API'lerine erişmek için uygulamalarınızı geçirme](https://techcommunity.microsoft.com/t5/azure-active-directory-identity/migrate-your-apps-to-access-the-license-managements-apis-from/ba-p/2464366).
>

İlk olarak [Microsoft 365 kiracınıza bağlanın](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
  

Ardından, bu komutla kiracınızın lisans planlarını listeleyin.

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

Ardından, lisans eklemek istediğiniz hesabın oturum açma adını (kullanıcı asıl adı (UPN) olarak da bilinir) alın.

Ardından, kullanıcı hesabının atanmış bir kullanım konumu olduğundan emin olun.

```powershell
Get-AzureADUser -ObjectID <user sign-in name (UPN)> | Select DisplayName, UsageLocation
```

Atanmış bir kullanım konumu yoksa, şu komutlarla bir konum atayabilirsiniz:

```powershell
$userUPN="<user sign-in name (UPN)>"
$userLoc="<ISO 3166-1 alpha-2 country code>"
Set-AzureADUser -ObjectID $userUPN -UsageLocation $userLoc
```

Son olarak, kullanıcı oturum açma adını ve lisans planı adını belirtin ve bu komutları çalıştırın.

```powershell
$userUPN="<user sign-in name (UPN)>"
$planName="<license plan name from the list of license plans>"
$License = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$License.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $planName -EQ).SkuID
$LicensesToAssign = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$LicensesToAssign.AddLicenses = $License
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $LicensesToAssign
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Windows PowerShell için Microsoft Azure Active Directory Modülünü kullanma

>[!Note]
>Set-MsolUserLicense ve New-MsolUser (-LicenseAssignment) cmdlet'leri kullanımdan kaldırılacak şekilde zamanlanmıştır. Lütfen betiklerinizi yukarıda açıklandığı gibi Microsoft Graph SDK'sının Set-MgUserLicense cmdlet'ine geçirin. Daha fazla bilgi için bkz[. Microsoft Graph lisans yönetimi API'lerine erişmek için uygulamalarınızı geçirme](https://techcommunity.microsoft.com/t5/azure-active-directory-identity/migrate-your-apps-to-access-the-license-managements-apis-from/ba-p/2464366).
>

İlk olarak [Microsoft 365 kiracınıza bağlanın](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

Kuruluşunuzdaki `Get-MsolAccountSku` her bir plandaki kullanılabilir lisans planlarını ve kullanılabilir lisans sayısını görüntülemek için komutunu çalıştırın. Her plandaki kullanılabilir lisans sayısı **ActiveUnitsWarningUnitsConsumedUnits'tir** -  - . Lisans planları, lisanslar ve hizmetler hakkında daha fazla bilgi için bkz. [PowerShell ile lisansları ve hizmetleri görüntüleme](view-licenses-and-services-with-microsoft-365-powershell.md).

>[!Note]
>PowerShell Core, Windows PowerShell modülü için Microsoft Azure Active Directory Modülünü ve adında **Msol** bulunan cmdlet'leri desteklemez. Bu cmdlet'leri kullanmaya devam etmek için bunları Windows PowerShell çalıştırmanız gerekir.
>

Kuruluşunuzdaki lisanssız hesapları bulmak için bu komutu çalıştırın.

```powershell
Get-MsolUser -All -UnlicensedUsersOnly
```

Yalnızca **UsageLocation** özelliği geçerli bir ISO 3166-1 alfa-2 ülke koduna ayarlanmış kullanıcı hesaplarına lisans atayabilirsiniz. Örneğin, Birleşik Devletler için ABD ve Fransa için FR. Bazı Microsoft 365 hizmetleri belirli ülkelerde kullanılamaz. Daha fazla bilgi için bkz. [Lisans kısıtlamaları hakkında](https://go.microsoft.com/fwlink/p/?LinkId=691730).
    
**UsageLocation** değeri olmayan hesapları bulmak için bu komutu çalıştırın.

```powershell
Get-MsolUser -All | where {$_.UsageLocation -eq $null}
```

Bir hesapta **UsageLocation** değerini ayarlamak için bu komutu çalıştırın.

```powershell
Set-MsolUser -UserPrincipalName "<Account>" -UsageLocation <CountryCode>
```

Örneğin:

```powershell
Set-MsolUser -UserPrincipalName "belindan@litwareinc.com" -UsageLocation US
```
    
**-All** parametresini kullanmadan **Get-MsolUser** cmdlet'ini kullanırsanız, yalnızca ilk 500 hesap döndürülür.

### <a name="assigning-licenses-to-user-accounts"></a>Kullanıcı hesaplarına lisans atama
    
Kullanıcıya lisans atamak için PowerShell'de aşağıdaki komutu kullanın.
  
```powershell
Set-MsolUserLicense -UserPrincipalName "<Account>" -AddLicenses "<AccountSkuId>"
```

Bu örnek, lisanssız kullanıcı **belindan'a\@** **litwareinc:ENTERPRISEPACK** (Office 365 Kurumsal E3) lisans planından bir lisans atar litwareinc.com:
  
```powershell
Set-MsolUserLicense -UserPrincipalName "belindan@litwareinc.com" -AddLicenses "litwareinc:ENTERPRISEPACK"
```

Tüm lisanssız kullanıcılara lisans atamak için bu komutu çalıştırın.
  
```powershell
Get-MsolUser -All -UnlicensedUsersOnly [<FilterableAttributes>] | Set-MsolUserLicense -AddLicenses "<AccountSkuId>"
```
  
>[!Note]
>Bir kullanıcıya aynı lisans planından birden çok lisans atayamazsınız. Yeterli kullanılabilir lisansınız yoksa, kullanılabilir lisanslar tükenene kadar kullanıcılara **Get-MsolUser** cmdlet'i tarafından döndürülmeleri sırasına göre atanır.
>

Bu örnek, tüm lisanssız **kullanıcılara litwareinc:ENTERPRISEPACK** (Office 365 Kurumsal E3) lisans planından lisans atar:
  
```powershell
Get-MsolUser -All -UnlicensedUsersOnly | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```

Bu örnek, Birleşik Devletler Satış departmanındaki lisanssız kullanıcılara aynı lisansları atar:
  
```powershell
Get-MsolUser -All -Department "Sales" -UsageLocation "US" -UnlicensedUsersOnly | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```
  
## <a name="move-a-user-to-a-different-subscription-license-plan-with-the-azure-active-directory-powershell-for-graph-module"></a>Graph için PowerShell Azure Active Directory modülüyle kullanıcıyı farklı bir aboneliğe (lisans planı) taşıma

İlk olarak [Microsoft 365 kiracınıza bağlanın](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
  
Ardından, abonelikleri arasında geçiş yapmak istediğiniz kullanıcı hesabının oturum açma adını (kullanıcı asıl adı (UPN) olarak da bilinir) alın.

Ardından, bu komutla kiracınız için abonelikleri (lisans planları) listeleyin.

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

Ardından, kullanıcı hesabının şu anda sahip olduğu abonelikleri bu komutlarla listeleyin.

```powershell
$userUPN="<user account UPN>"
$licensePlanList = Get-AzureADSubscribedSku
$userList = Get-AzureADUser -ObjectID $userUPN | Select -ExpandProperty AssignedLicenses | Select SkuID 
$userList | ForEach { $sku=$_.SkuId ; $licensePlanList | ForEach { If ( $sku -eq $_.ObjectId.substring($_.ObjectId.length - 36, 36) ) { Write-Host $_.SkuPartNumber } } }
```

Kullanıcının şu anda sahip olduğu aboneliği (FROM aboneliği) ve kullanıcının taşıdığı aboneliği (TO aboneliği) belirleyin.

Son olarak, TO ve FROM abonelik adlarını (SKU parça numaraları) belirtin ve bu komutları çalıştırın.

```powershell
$subscriptionFrom="<SKU part number of the current subscription>"
$subscriptionTo="<SKU part number of the new subscription>"
# Unassign
$license = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$licenses = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$licenses.RemoveLicenses =  (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $subscriptionFrom -EQ).SkuID
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $licenses
# Assign
$license.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $subscriptionTo -EQ).SkuID
$licenses = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$licenses.AddLicenses = $License
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $licenses
```

Bu komutlarla kullanıcı hesabı için abonelikteki değişikliği doğrulayabilirsiniz.

```powershell
$licensePlanList = Get-AzureADSubscribedSku
$userList = Get-AzureADUser -ObjectID $userUPN | Select -ExpandProperty AssignedLicenses | Select SkuID 
$userList | ForEach { $sku=$_.SkuId ; $licensePlanList | ForEach { If ( $sku -eq $_.ObjectId.substring($_.ObjectId.length - 36, 36) ) { Write-Host $_.SkuPartNumber } } }
```

## <a name="see-also"></a>Ayrıca bkz.

[PowerShell ile kullanıcı hesaplarını, lisansları ve grupları yönetme](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
  
[PowerShell ile Microsoft 365’i yönetme](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[Microsoft 365 için PowerShell'i kullanmaya başlama](getting-started-with-microsoft-365-powershell.md)
