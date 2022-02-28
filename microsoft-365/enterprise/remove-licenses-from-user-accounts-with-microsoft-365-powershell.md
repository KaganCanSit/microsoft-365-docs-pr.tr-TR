---
title: PowerShell Microsoft 365 hesaplarından kullanıcı lisanslarını kaldırma
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
- LIL_Placement
- O365ITProTrain
ms.assetid: e7e4dc5e-e299-482c-9414-c265e145134f
description: PowerShell kullanarak daha önce kullanıcılara Microsoft 365 lisansları kaldırmayı açıklar.
ms.openlocfilehash: 4aa40b4405dda07eea34151bd2fddcde0030e8b8
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62988784"
---
# <a name="remove-microsoft-365-licenses-from-user-accounts-with-powershell"></a>PowerShell Microsoft 365 hesaplarından kullanıcı lisanslarını kaldırma

*Bu makale hem son hem de Microsoft 365 Kurumsal hem de Office 365 Kurumsal.*

>[!Note]
>[Kullanıcı hesaplarından lisansları kaldırmayı öğrenmek için](../admin/manage/remove-licenses-from-users.md) Microsoft 365 yönetim merkezi. Ek kaynakların listesi için bkz. [Kullanıcıları ve grupları yönetme](/admin).
>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Graph modülü için Azure Active Directory PowerShell'i kullanma

İlk olarak[, kiracınıza bağlan Microsoft 365 bağlanin](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).

Ardından, bu komutla kiracınıza uygun lisans planlarını listelenin.

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

Ardından, kullanıcı asıl adı (UPN) olarak da bilinen lisansı kaldırmak istediğiniz hesabın oturum açma adını alın.

Son olarak, kullanıcı oturum açma ve lisans planı adlarını belirtin, "<" ve ">" karakterlerini kaldırın ve bu komutları çalıştırın.

```powershell
$userUPN="<user sign-in name (UPN)>"
$planName="<license plan name from the list of license plans>"
$license = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$License.RemoveLicenses = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $planName -EQ).SkuID
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
            $Licenses.RemoveLicenses +=  (Get-AzureADSubscribedSku | Where-Object -Property SkuID -Value $Skus[$i].SkuId -EQ).SkuID   
        }
        Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $licenses
    } else {
        $licenses = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
        $Licenses.RemoveLicenses =  (Get-AzureADSubscribedSku | Where-Object -Property SkuID -Value $Skus.SkuId -EQ).SkuID
        Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $licenses
    }
}
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Kaynak için Microsoft Azure Active Directory Modülü'Windows PowerShell

İlk olarak[, kiracınıza bağlan Microsoft 365 bağlanin](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).
   
Kuruluş lisans planı (**AccountSkuID**) bilgilerini görüntülemek için aşağıdaki konulara bakın:
    
  - [PowerShell ile lisansları ve hizmetleri görüntüleme](view-licenses-and-services-with-microsoft-365-powershell.md)
    
  - [PowerShell ile hesap lisansını ve hizmet ayrıntılarını görüntüleme](view-account-license-and-service-details-with-microsoft-365-powershell.md)
    
**Get-MsolUser** cmdlet'ini _-All_ parametresini kullanmadan kullanırsanız, yalnızca ilk 500 hesap döndürülür.
    
### <a name="removing-licenses-from-user-accounts"></a>Kullanıcı hesaplarından lisansları kaldırma

Var olan kullanıcı hesabından lisansları kaldırmak için aşağıdaki söz dizimi kullanın:
  
```powershell
Set-MsolUserLicense -UserPrincipalName <Account> -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...
```

>[!Note]
>PowerShell Core, **Msol'Microsoft Azure Active Directory Msol** Windows PowerShell cmdlet'leri için Modül Adını Desteklemez. Bu cmdlet'leri kullanmaya devam etmek için, tüm cmdlet'leri Windows PowerShell.
>

Bu örnekte, kullanıcı hesabı **lisansından litwareinc:ENTERPRISEPACK** (Office 365 Kurumsal E3) lisansı BelindaN@litwareinc.com.
  
```powershell
Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -RemoveLicenses "litwareinc:ENTERPRISEPACK"
```

>[!Note]
>Cmdlet'i `Set-MsolUserLicense` kullanarak iptal edilen lisansların kullanıcı *atamasını açamazsiniz* . Bunu aşağıdaki hesapta yer alan her kullanıcı hesabı için ayrı Microsoft 365 yönetim merkezi.
>

Var olan lisanslı kullanıcılar grubundan tüm lisansları kaldırmak için, aşağıdaki yöntemlerden birini kullanın:
  
- **Hesapları mevcut bir hesap özniteliğine göre filtreleme** Bunu yapmak için aşağıdaki söz dizimlerini kullanın:
    
```powershell
$userArray = Get-MsolUser -All <FilterableAttributes> | where {$_.isLicensed -eq $true}
for ($i=0; $i -lt $userArray.Count; $i++)
{
Set-MsolUserLicense -UserPrincipalName $userArray[$i].UserPrincipalName -RemoveLicenses $userArray[$i].licenses.accountskuid
}
```

Bu örnek, ABD'de Satış departmanında yer alan tüm kullanıcı hesaplarından tüm lisansları kaldırır.
    
```powershell
$userArray = Get-MsolUser -All -Department "Sales" -UsageLocation "US" | where {$_.isLicensed -eq $true}
for ($i=0; $i -lt $userArray.Count; $i++)
{
Set-MsolUserLicense -UserPrincipalName $userArray[$i].UserPrincipalName -RemoveLicenses $userArray[$i].licenses.accountskuid
}
```

- **Belirli bir lisans için belirli hesapların listesini kullanma** Bunu yapmak için aşağıdaki adımları izleyin:
    
1. Her satırda bir hesap içeren bir metin dosyası oluşturun ve kaydedin:
    
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
Bu örnekte, C:\My Documents\Accounts.txt metin dosyasında tanımlanan kullanıcı hesaplarından **litwareinc:ENTERPRISEPACK** (Office 365 Kurumsal E3) lisansı kaldırılmış Documents\Accounts.txt.
    
  ```powershell
  $x=Get-Content "C:\My Documents\Accounts.txt"
  for ($i=0; $i -lt $x.Count; $i++)
  {
  Set-MsolUserLicense -UserPrincipalName $x[$i] -RemoveLicenses "litwareinc:ENTERPRISEPACK"
  }
  ```

Var olan tüm kullanıcı hesaplarından tüm lisansları kaldırmak için aşağıdaki söz dizimi kullanın:
  
```powershell
$userArray = Get-MsolUser -All | where {$_.isLicensed -eq $true}
for ($i=0; $i -lt $userArray.Count; $i++)
{
Set-MsolUserLicense -UserPrincipalName $userArray[$i].UserPrincipalName -RemoveLicenses $userArray[$i].licenses.accountskuid
}
```

Lisansı serbest uygulamanın bir diğer yolu da kullanıcı hesabını silmektir. Daha fazla bilgi için bkz [. PowerShell'de kullanıcı hesaplarını silme ve geri yükleme](delete-and-restore-user-accounts-with-microsoft-365-powershell.md).
  
## <a name="see-also"></a>Ayrıca bkz.

[PowerShell Microsoft 365 hesaplarını, lisanslarını ve gruplarını yönetme](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
  
[PowerShell Microsoft 365'i yönetme](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[Microsoft 365 için PowerShell ile çalışmaya Microsoft 365](getting-started-with-microsoft-365-powershell.md)