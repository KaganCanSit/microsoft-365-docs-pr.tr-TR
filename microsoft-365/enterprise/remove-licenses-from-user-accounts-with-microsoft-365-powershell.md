---
title: PowerShell ile kullanıcı hesaplarından Microsoft 365 lisanslarını kaldırma
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
- LIL_Placement
- O365ITProTrain
ms.assetid: e7e4dc5e-e299-482c-9414-c265e145134f
description: Daha önce kullanıcılara atanmış Microsoft 365 lisansları kaldırmak için PowerShell'in nasıl kullanılacağını açıklar.
ms.openlocfilehash: b036f58686ac179fc93c1a0605ed2b585ea89c30
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65096336"
---
# <a name="remove-microsoft-365-licenses-from-user-accounts-with-powershell"></a>PowerShell ile kullanıcı hesaplarından Microsoft 365 lisanslarını kaldırma

*Bu makale hem Microsoft 365 Kurumsal hem de Office 365 Kurumsal için geçerlidir.*

>[!Note]
>Microsoft 365 yönetim merkezi ile [kullanıcı hesaplarından lisansları kaldırmayı öğrenin](../admin/manage/remove-licenses-from-users.md). Ek kaynakların listesi için bkz. [Kullanıcıları ve grupları yönetme](/admin).
>

## <a name="use-the-microsoft-graph-powershell-sdk"></a>Microsoft Graph PowerShell SDK'sını kullanma

İlk olarak [Microsoft 365 kiracınıza bağlanın](/graph/powershell/get-started#authentication).

Bir kullanıcıya lisans atama ve kaldırma için User.ReadWrite.All izin kapsamı veya ['Lisans ata' Graph API başvuru sayfasında](/graph/api/user-assignlicense) listelenen diğer izinlerden biri gerekir.

Kiracıda bulunan lisansları okumak için Organization.Read.All izin kapsamı gereklidir.

```powershell
Connect-Graph -Scopes User.ReadWrite.All, Organization.Read.All
```

Kuruluşunuzdaki lisans planı bilgilerini görüntülemek için aşağıdaki konulara bakın:

- [PowerShell ile lisansları ve hizmetleri görüntüleme](view-licenses-and-services-with-microsoft-365-powershell.md)

- [PowerShell ile hesap lisansı ve hizmet ayrıntılarını görüntüleme](view-account-license-and-service-details-with-microsoft-365-powershell.md)

### <a name="removing-licenses-from-user-accounts"></a>Kullanıcı hesaplarından lisansları kaldırma

Mevcut bir kullanıcı hesabından lisansları kaldırmak için aşağıdaki söz dizimini kullanın:
  
```powershell
Set-MgUserLicense -UserId "<Account>" -RemoveLicenses @("<AccountSkuId1>") -AddLicenses @{}
```

Bu **örnek,** **kullanıcı BelindaN@litwareinc.com SPE_E5** (Microsoft 365 E5) lisans planını kaldırır:

```powershell
$e5Sku = Get-MgSubscribedSku -All | Where SkuPartNumber -eq 'SPE_E5'
Set-MgUserLicense -UserId "belindan@litwareinc.com" -RemoveLicenses @($e5Sku.SkuId) -AddLicenses @{}
```

Mevcut lisanslı kullanıcılar grubundan tüm lisansları kaldırmak için aşağıdaki söz dizimini kullanın:

```powershell
$licensedUsers = Get-MgUser -Filter 'assignedLicenses/$count ne 0' `
    -ConsistencyLevel eventual -CountVariable licensedUserCount -All `
    -Select UserPrincipalName,DisplayName,AssignedLicenses

foreach($user in $licensedUsers)
{
    $licencesToRemove = $user.AssignedLicenses | Select -ExpandProperty SkuId
    $user = Set-MgUserLicense -UserId $user.UserPrincipalName -RemoveLicenses $licencesToRemove -AddLicenses @{} 
}
```

Lisans boşaltmanın bir diğer yolu da kullanıcı hesabını silmektir. Daha fazla bilgi için bkz. [PowerShell ile kullanıcı hesaplarını silme ve geri yükleme](delete-and-restore-user-accounts-with-microsoft-365-powershell.md).

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Graph için Azure Active Directory PowerShell modülünü kullanma

>Set-AzureADUserLicense cmdlet'i kullanımdan kaldırılacak şekilde zamanlanmıştır. Lütfen betiklerinizi yukarıda açıklandığı gibi Microsoft Graph SDK'sının Set-MgUserLicense cmdlet'ine geçirin. Daha fazla bilgi için bkz[. Microsoft Graph lisans yönetimi API'lerine erişmek için uygulamalarınızı geçirme](https://techcommunity.microsoft.com/t5/azure-active-directory-identity/migrate-your-apps-to-access-the-license-managements-apis-from/ba-p/2464366).
>

İlk olarak [Microsoft 365 kiracınıza bağlanın](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).

Ardından, bu komutla kiracınızın lisans planlarını listeleyin.

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

Ardından, lisansını kaldırmak istediğiniz hesabın oturum açma adını (kullanıcı asıl adı (UPN) olarak da bilinir) alın.

Son olarak, kullanıcı oturum açma ve lisans planı adlarını belirtin, "<" ve ">" karakterlerini kaldırın ve bu komutları çalıştırın.

```powershell
$userUPN="<user sign-in name (UPN)>"
$planName="<license plan name from the list of license plans>"
$license = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$license.RemoveLicenses = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $planName -EQ).SkuID
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $license
```

Belirli bir kullanıcı hesabının tüm lisanslarını kaldırmak için, kullanıcı oturum açma adını belirtin, "<" ve ">" karakterlerini kaldırın ve bu komutları çalıştırın.

```powershell
$userUPN="<user sign-in name (UPN)>"
$userList = Get-AzureADUser -ObjectID $userUPN
$Skus = $userList | Select -ExpandProperty AssignedLicenses | Select SkuID
if($userList.Count -ne 0) {
    if($Skus -is [array])
    {
        $licenses = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
        for ($i=0; $i -lt $Skus.Count; $i++) {
            $licenses.RemoveLicenses +=  (Get-AzureADSubscribedSku | Where-Object -Property SkuID -Value $Skus[$i].SkuId -EQ).SkuID   
        }
        Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $licenses
    } else {
        $licenses = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
        $licenses.RemoveLicenses =  (Get-AzureADSubscribedSku | Where-Object -Property SkuID -Value $Skus.SkuId -EQ).SkuID
        Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $licenses
    }
}
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Windows PowerShell için Microsoft Azure Active Directory Modülünü kullanma

>[!Note]
>Set-MsolUserLicense ve New-MsolUser (-LicenseAssignment) cmdlet'leri kullanımdan kaldırılacak şekilde zamanlanmıştır. Lütfen betiklerinizi yukarıda açıklandığı gibi Microsoft Graph SDK'sının Set-MgUserLicense cmdlet'ine geçirin. Daha fazla bilgi için bkz[. Microsoft Graph lisans yönetimi API'lerine erişmek için uygulamalarınızı geçirme](https://techcommunity.microsoft.com/t5/azure-active-directory-identity/migrate-your-apps-to-access-the-license-managements-apis-from/ba-p/2464366).
>

İlk olarak [Microsoft 365 kiracınıza bağlanın](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).
   
Kuruluşunuzdaki lisans planı (**AccountSkuID**) bilgilerini görüntülemek için aşağıdaki konulara bakın:
    
  - [PowerShell ile lisansları ve hizmetleri görüntüleme](view-licenses-and-services-with-microsoft-365-powershell.md)
    
  - [PowerShell ile hesap lisansı ve hizmet ayrıntılarını görüntüleme](view-account-license-and-service-details-with-microsoft-365-powershell.md)
    
_-All_ parametresini kullanmadan **Get-MsolUser** cmdlet'ini kullanırsanız, yalnızca ilk 500 hesap döndürülür.
    
### <a name="removing-licenses-from-user-accounts"></a>Kullanıcı hesaplarından lisansları kaldırma

Mevcut bir kullanıcı hesabından lisansları kaldırmak için aşağıdaki söz dizimini kullanın:
  
```powershell
Set-MsolUserLicense -UserPrincipalName <Account> -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...
```

>[!Note]
>PowerShell Core, Windows PowerShell modülü için Microsoft Azure Active Directory Modülünü ve adında **Msol** bulunan cmdlet'leri desteklemez. Bu cmdlet'leri kullanmaya devam etmek için bunları Windows PowerShell çalıştırmanız gerekir.
>

Bu örnek, kullanıcı hesabı BelindaN@litwareinc.com **litwareinc:ENTERPRISEPACK** (Office 365 Kurumsal E3) lisansını kaldırır.
  
```powershell
Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -RemoveLicenses "litwareinc:ENTERPRISEPACK"
```

>[!Note]
>Kullanıcıların *iptal edilmiş* lisans atamalarını kaldırmak için cmdlet'ini kullanamazsınız`Set-MsolUserLicense`. Bunu Microsoft 365 yönetim merkezi her kullanıcı hesabı için ayrı ayrı yapmanız gerekir.
>

Mevcut lisanslı kullanıcılar grubundan tüm lisansları kaldırmak için aşağıdaki yöntemlerden birini kullanın:
  
- **Hesapları mevcut bir hesap özniteliğine göre filtreleme** Bunu yapmak için aşağıdaki söz dizimini kullanın:
    
```powershell
$userArray = Get-MsolUser -All <FilterableAttributes> | where {$_.isLicensed -eq $true}
for ($i=0; $i -lt $userArray.Count; $i++)
{
Set-MsolUserLicense -UserPrincipalName $userArray[$i].UserPrincipalName -RemoveLicenses $userArray[$i].licenses.accountskuid
}
```

Bu örnek, Birleşik Devletler Satış departmanındaki tüm kullanıcı hesaplarından tüm lisansları kaldırır.
    
```powershell
$userArray = Get-MsolUser -All -Department "Sales" -UsageLocation "US" | where {$_.isLicensed -eq $true}
for ($i=0; $i -lt $userArray.Count; $i++)
{
Set-MsolUserLicense -UserPrincipalName $userArray[$i].UserPrincipalName -RemoveLicenses $userArray[$i].licenses.accountskuid
}
```

- **Belirli bir lisans için belirli hesapların listesini kullanma** Bunu yapmak için aşağıdaki adımları uygulayın:
    
1. Her satırda aşağıdaki gibi bir hesap içeren bir metin dosyası oluşturun ve kaydedin:
    
  ```powershell
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

2. Aşağıdaki sözdizimini kullanın:
    
  ```powershell
  $x=Get-Content "<FileNameAndPath>"
  for ($i=0; $i -lt $x.Count; $i++)
  {
  Set-MsolUserLicense -UserPrincipalName $x[$i] -RemoveLicenses "<AccountSkuId1>","<AccountSkuId2>"...
  }
  ```
Bu örnek, C:\My Documents\Accounts.txt metin dosyasında tanımlanan kullanıcı hesaplarından **litwareinc:ENTERPRISEPACK** (Office 365 Kurumsal E3) lisansını kaldırır.
    
  ```powershell
  $x=Get-Content "C:\My Documents\Accounts.txt"
  for ($i=0; $i -lt $x.Count; $i++)
  {
  Set-MsolUserLicense -UserPrincipalName $x[$i] -RemoveLicenses "litwareinc:ENTERPRISEPACK"
  }
  ```

Tüm mevcut kullanıcı hesaplarından tüm lisansları kaldırmak için aşağıdaki söz dizimini kullanın:
  
```powershell
$userArray = Get-MsolUser -All | where {$_.isLicensed -eq $true}
for ($i=0; $i -lt $userArray.Count; $i++)
{
Set-MsolUserLicense -UserPrincipalName $userArray[$i].UserPrincipalName -RemoveLicenses $userArray[$i].licenses.accountskuid
}
```

Lisans boşaltmanın bir diğer yolu da kullanıcı hesabını silmektir. Daha fazla bilgi için bkz. [PowerShell ile kullanıcı hesaplarını silme ve geri yükleme](delete-and-restore-user-accounts-with-microsoft-365-powershell.md).
  
## <a name="see-also"></a>Ayrıca bkz.

[PowerShell ile Microsoft 365 kullanıcı hesaplarını, lisanslarını ve gruplarını yönetme](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
  
[PowerShell ile Microsoft 365’i yönetme](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[Microsoft 365 için PowerShell'i kullanmaya başlama](getting-started-with-microsoft-365-powershell.md)
