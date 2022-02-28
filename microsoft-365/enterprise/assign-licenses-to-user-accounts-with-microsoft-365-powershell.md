---
title: PowerShell Microsoft 365 hesaplarına kullanıcı lisansları atama
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
description: Bu makalede, PowerShell kullanarak lisanssız kullanıcılara Microsoft 365 lisans atamayı öğrenin.
ms.openlocfilehash: b9f076e4856820d9f10e4cf92718dd6ddd3971c5
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62985356"
---
# <a name="assign-microsoft-365-licenses-to-user-accounts-with-powershell"></a>PowerShell Microsoft 365 hesaplarına kullanıcı lisansları atama

*Bu makale hem son hem de Microsoft 365 Kurumsal hem de Office 365 Kurumsal.*

Kullanıcılar, hesaplarına lisans Microsoft 365 lisansı atanana kadar bu hizmetlerde hiçbir hizmeti kullanamaz. Lisanssız hesaplara hızla lisans atamak için PowerShell kullanabilirsiniz. 

Kullanıcı hesaplarına önce bir konum atanıyor olması gerekir. Konum belirtmek, kullanıcı hesabında yeni kullanıcı hesabı oluşturmanın gerekli [bir Microsoft 365 yönetim merkezi.](../admin/add-users/add-users.md) 

Şirket içi Active Directory Etki Alanı Hizmetleri'niz tarafından eşitlenen hesapların varsayılan olarak belirtilmiş bir konumu olmaz. Şu konumdan bu hesaplar için konum yapılandırabilirsiniz:

- Microsoft 365 yönetim merkezi
 - [PowerShell](configure-user-account-properties-with-microsoft-365-powershell.md)
 - [Azure portalı](/azure/active-directory/fundamentals/active-directory-users-profile-azure-portal) (**Active** **DirectoryUsers** >  > hesabı > **ProfileContact** >  **infoCountry** >  **or region**).

>[!Note]
>[Kullanıcı hesaplarına lisans atamayı öğrenmek için](../admin/manage/assign-licenses-to-users.md) Microsoft 365 yönetim merkezi. Ek kaynakların listesi için bkz. [Kullanıcıları ve grupları yönetme](/admin).
>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Graph modülü için Azure Active Directory PowerShell'i kullanma

İlk olarak[, kiracınıza bağlan Microsoft 365 bağlanin](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
  

Ardından, bu komutla kiracınıza uygun lisans planlarını listelenin.

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

Ardından, lisans eklemek istediğiniz hesabın kullanıcı asıl adı (UPN) olarak da bilinen oturum açma adını alın.

Ardından, kullanıcı hesabına atanmış bir kullanım konumu olduğundan emin olun.

```powershell
Get-AzureADUser -ObjectID <user sign-in name (UPN)> | Select DisplayName, UsageLocation
```

Kullanım konumu atanmamışsa şu komutları kullanarak bir konum atabilirsiniz:

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

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Kaynak için Microsoft Azure Active Directory Modülü'Windows PowerShell

Bu modülün işlevselliği daha yeni olan [Azure Active Directory Azure Active Directory PowerShell](/powershell/azuread/v2/azureactivedirectory) modülünde kullanılabilir olduğunda bu modülün kullanımdan Graph unutmayın. Yeni PowerShell betikleri oluşturan müşterilerin bu modül yerine daha yeni modülü kullanmalarını tavsiye ediyoruz.

İlk olarak[, kiracınıza bağlan Microsoft 365 bağlanin](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

Komutu çalıştırarak `Get-MsolAccountSku` , kullanılabilir lisans planlarını ve organizasyonlar'daki her bir plan için kullanılabilir lisans sayısını görüntüye alın. Her plan için kullanılabilir lisans sayısı ActiveUnitsWarningUnitsConsumedUnits'tır -  - . Lisans planları, lisanslar ve hizmetler hakkında daha fazla bilgi için bkz [. PowerShell ile lisansları ve hizmetleri görüntüleme](view-licenses-and-services-with-microsoft-365-powershell.md).

>[!Note]
>PowerShell Core, **Msol'Microsoft Azure Active Directory Msol** Windows PowerShell cmdlet'leri için Modül Adını Desteklemez. Bu cmdlet'leri kullanmaya devam etmek için, tüm cmdlet'leri Windows PowerShell.
>

Organizasyon'daki lisanssız hesapları bulmak için bu komutu çalıştırın.

```powershell
Get-MsolUser -All -UnlicensedUsersOnly
```

Yalnızca **UsageLocation** özelliği geçerli bir ISO 3166-1 alfa-2 ülke koduna ayarlanmış kullanıcı hesaplarına lisans atayın. Örneğin, ABD için US ve Fransa için FR. Bazı Microsoft 365 hizmetleri belirli ülkelerde kullanılamaz. Daha fazla bilgi için bkz [. Lisans kısıtlamaları hakkında](https://go.microsoft.com/fwlink/p/?LinkId=691730).
    
**UsageLocation** değerine sahip hesaplar bulmak için bu komutu çalıştırın.

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
    
**Get-MsolUser** cmdlet'ini **-All** parametresini kullanmadan kullanırsanız, yalnızca ilk 500 hesap döndürülür.

### <a name="assigning-licenses-to-user-accounts"></a>Kullanıcı hesaplarına lisans atama
    
Kullanıcıya lisans atamak için PowerShell'de aşağıdaki komutu kullanın.
  
```powershell
Set-MsolUserLicense -UserPrincipalName "<Account>" -AddLicenses "<AccountSkuId>"
```

Bu örnekte **, litwareinc:ENTERPRISEPACK** (Office 365 Kurumsal E3) lisans planından lisanssız kullanıcı **belindan'a\@ bir lisans atar litwareinc.com**:
  
```powershell
Set-MsolUserLicense -UserPrincipalName "belindan@litwareinc.com" -AddLicenses "litwareinc:ENTERPRISEPACK"
```

Tüm lisanssız kullanıcılara lisans atamak için bu komutu çalıştırın.
  
```powershell
Get-MsolUser -All -UnlicensedUsersOnly [<FilterableAttributes>] | Set-MsolUserLicense -AddLicenses "<AccountSkuId>"
```
  
>[!Note]
>Aynı lisans planından bir kullanıcıya birden çok lisans atayayız. Yeterli kullanılabilir lisansınız yoksa, lisanslar kullanıcılara **Get-MsolUser** cmdlet'i tarafından döndürülme sırasına göre atanır ve kullanılabilir lisanslar çalışmadığı zaman da verilir.
>

Bu örnekte, **litwareinc:ENTERPRISEPACK** (Office 365 Kurumsal E3) lisans planından lisansları tüm lisanssız kullanıcılara atar:
  
```powershell
Get-MsolUser -All -UnlicensedUsersOnly | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```

Bu örnekte, bu lisanslar ABD'de Satış departmanında yer alan lisanssız kullanıcılara atanıyor:
  
```powershell
Get-MsolUser -All -Department "Sales" -UsageLocation "US" -UnlicensedUsersOnly | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```
  
## <a name="move-a-user-to-a-different-subscription-license-plan-with-the-azure-active-directory-powershell-for-graph-module"></a>Kullanıcı, Graph için PowerShell modülü Azure Active Directory yle farklı bir aboneliğe (lisans planı) taşıma

İlk olarak[, kiracınıza bağlan Microsoft 365 bağlanin](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
  
Ardından, aboneliklerini değiştirmek istediğiniz kullanıcı hesabının oturum açma adını (kullanıcı asıl adı (UPN) olarak da bilinir) edinin.

Ardından, bu komutla kiracınıza abonelikleri (lisans planları) listelenin.

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

Ardından, kullanıcı hesabının şu anda sahip olduğu abonelikleri bu komutlarla listelenin.

```powershell
$userUPN="<user account UPN>"
$licensePlanList = Get-AzureADSubscribedSku
$userList = Get-AzureADUser -ObjectID $userUPN | Select -ExpandProperty AssignedLicenses | Select SkuID 
$userList | ForEach { $sku=$_.SkuId ; $licensePlanList | ForEach { If ( $sku -eq $_.ObjectId.substring($_.ObjectId.length - 36, 36) ) { Write-Host $_.SkuPartNumber } } }
```

Kullanıcının şu anda sahip olduğu aboneliği (FROM aboneliği) ve kullanıcının hareket ettir olduğu aboneliği (TO aboneliği) belirleme.

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

Bu komutlarla, kullanıcı hesabının aboneliğinde yapılan değişikliği doğru edebilirsiniz.

```powershell
$licensePlanList = Get-AzureADSubscribedSku
$userList = Get-AzureADUser -ObjectID $userUPN | Select -ExpandProperty AssignedLicenses | Select SkuID 
$userList | ForEach { $sku=$_.SkuId ; $licensePlanList | ForEach { If ( $sku -eq $_.ObjectId.substring($_.ObjectId.length - 36, 36) ) { Write-Host $_.SkuPartNumber } } }
```

## <a name="see-also"></a>Ayrıca bkz.

[PowerShell ile kullanıcı hesaplarını, lisansları ve grupları yönetme](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
  
[PowerShell Microsoft 365'i yönetme](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[Microsoft 365 için PowerShell ile çalışmaya Microsoft 365](getting-started-with-microsoft-365-powershell.md)
