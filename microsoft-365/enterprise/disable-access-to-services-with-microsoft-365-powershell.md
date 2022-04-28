---
title: PowerShell ile Microsoft 365 hizmetlerine erişimi devre dışı bırakma
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 07/27/2020
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
- Ent_Office_Other
- PowerShell
- LIL_Placement
- seo-marvel-apr2020
ms.assetid: 264f4f0d-e2cd-44da-a9d9-23bef250a720
description: Bu makalede, kullanıcılar için Microsoft 365 hizmetlerine erişimi devre dışı bırakmak için PowerShell'i kullanmayı öğrenin.
ms.openlocfilehash: 0acd174fce25e0332aa8f927595657e4d0a464b9
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65097722"
---
# <a name="disable-access-to-microsoft-365-services-with-powershell"></a>PowerShell ile Microsoft 365 hizmetlerine erişimi devre dışı bırakma

*Bu makale hem Microsoft 365 Kurumsal hem de Office 365 Kurumsal için geçerlidir.*

Bir lisans planından bir Microsoft 365 hesabına lisans atandığında, Microsoft 365 hizmetler söz konusu lisanstan kullanıcının kullanımına sunulur. Ancak, kullanıcının erişebileceği Microsoft 365 hizmetlerini denetleyebilirsiniz. Örneğin, lisans SharePoint Online hizmetine erişime izin verse de, bu hizmete erişimi devre dışı bırakabilirsiniz. PowerShell'i kullanarak belirli bir lisans planı için herhangi bir sayıda hizmete erişimi devre dışı bırakabilirsiniz:

- Tek bir hesap.
- Bir hesap grubu.
- Kuruluşunuzdaki tüm hesaplar.

>[!Note]
>Diğer hizmetler buna bağımlı olduğunda belirli bir hizmeti devre dışı bırakmanızı engelleyebilecek Microsoft 365 hizmet bağımlılıkları vardır.
>

## <a name="use-the-microsoft-graph-powershell-sdk"></a>Microsoft Graph PowerShell SDK'sını kullanma

İlk olarak [Microsoft 365 kiracınıza bağlanın](/graph/powershell/get-started#authentication).

Bir kullanıcıya lisans atama ve kaldırma için User.ReadWrite.All izin kapsamı veya ['Lisans ata' Graph API başvuru sayfasında](/graph/api/user-assignlicense) listelenen diğer izinlerden biri gerekir.

Kiracıda bulunan lisansları okumak için Organization.Read.All izin kapsamı gereklidir.

```powershell
Connect-Graph -Scopes User.ReadWrite.All, Organization.Read.All
```

Ardından, SkuPartNumber olarak da bilinen kullanılabilir lisans planlarınızı görüntülemek için bu komutu kullanın:

```powershell
Get-MgSubscribedSku | Select SkuId, SkuPartNumber, ServicePlans | Sort SkuPartNumber
```

Daha fazla bilgi için bkz. [PowerShell ile lisansları ve hizmetleri görüntüleme](view-licenses-and-services-with-microsoft-365-powershell.md).

Bu konudaki yordamların önce ve sonra sonuçlarını görmek için bkz. [PowerShell ile hesap lisansı ve hizmet ayrıntılarını görüntüleme](view-account-license-and-service-details-with-microsoft-365-powershell.md).

### <a name="disable-specific-microsoft-365-services-for-specific-users-for-a-specific-licensing-plan"></a>Belirli bir lisans planı için belirli kullanıcılar için belirli Microsoft 365 hizmetlerini devre dışı bırakma
  
Belirli bir lisans planı için kullanıcılara yönelik belirli bir Microsoft 365 hizmetini devre dışı bırakmak için aşağıdaki adımları uygulayın:
  
#### <a name="step-1-identify-the-undesired-services-in-the-licensing-plan-by-using-the-following-syntax"></a>1. Adım: Aşağıdaki söz dizimini kullanarak lisans planındaki istenmeyen hizmetleri belirleyin:

Önce aşağıdaki komutu kullanarak kiracınızda kullanılabilen lisans planlarını listeleyin.

```powershell
Get-MgSubscribedSku | Select SkuPartNumber

SkuPartNumber
-------------
EMSPREMIUM
SPE_E5
RIGHTSMANAGEMENT_ADHOC

```

Ardından, yukarıdaki komuttan SkuPartNumber'ı kullanın, belirli bir lisans planı (Sku) için kullanılabilir hizmet planlarını listeleyin.

Aşağıdaki örnek, **SPE_E5 (Microsoft 365 E5**) için kullanılabilen tüm hizmet planlarını listeler.

```powershell
Get-MgSubscribedSku -All | Where SkuPartNumber -eq 'SPE_E5' |  select -ExpandProperty ServicePlans
```

```text
AppliesTo ProvisioningStatus ServicePlanId                        ServicePlanName
--------- ------------------ -------------                        ---------------
User      Success            b21a6b06-1988-436e-a07b-51ec6d9f52ad PROJECT_O365_P3
User      Success            64bfac92-2b17-4482-b5e5-a0304429de3e MICROSOFTENDPOINTDLP
User      Success            199a5c09-e0ca-4e37-8f7c-b05d533e1ea2 MICROSOFTBOOKINGS
User      Success            6db1f1db-2b46-403f-be40-e39395f08dbb CUSTOMER_KEY
User      Success            4a51bca5-1eff-43f5-878c-177680f191af WHITEBOARD_PLAN3
User      Success            07699545-9485-468e-95b6-2fca3738be01 FLOW_O365_P3
User      Success            9c0dab89-a30c-4117-86e7-97bda240acd2 POWERAPPS_O365_P3
User      Success            e212cbc7-0961-4c40-9825-01117710dcb1 FORMS_PLAN_E5
User      Success            57ff2da0-773e-42df-b2af-ffb7a2317929 TEAMS1
User      Success            21b439ba-a0ca-424f-a6cc-52f954a5b111 WIN10_PRO_ENT_SUB
User      Success            eec0eb4f-6444-4f95-aba0-50c24d67f998 AAD_PREMIUM_P2
User      Success            c1ec4a95-1f05-45b3-a911-aa3fa01094f5 INTUNE_A
User      Success            7547a3fe-08ee-4ccb-b430-5077c5041653 YAMMER_ENTERPRISE
User      Success            a23b959c-7ce8-4e57-9140-b90eb88a9e97 SWAY
User      Success            e95bec33-7c88-4a70-8e19-b10bd9d0c014 SHAREPOINTWAC
User      Success            5dbe027f-2339-4123-9542-606e4d348a72 SHAREPOINTENTERPRISE
User      Success            b737dad2-2f6c-4c65-90e3-ca563267e8b9 PROJECTWORKMANAGEMENT
User      Success            43de0ff5-c92c-492b-9116-175376d08c38 OFFICESUBSCRIPTION
User      Success            0feaeb32-d00e-4d66-bd5a-43b5b83db82c MCOSTANDARD
User      Success            9f431833-0334-42de-a7dc-70aa40db46db LOCKBOX_ENTERPRISE
User      Success            efb87545-963c-4e0d-99df-69c6916d9eb0 EXCHANGE_S_ENTERPRISE
```

Lisans planlarının tam listesi (ürün adları olarak da bilinir), bunların dahil edilen hizmet planları ve bunlara karşılık gelen kolay adları için bkz. [Lisanslama için ürün adları ve hizmet planı tanımlayıcıları](/azure/active-directory/users-groups-roles/licensing-service-plan-reference). (Hizmet planının ilgili kolay adını aramak için ServicePlanId'yi kullanarak arama.

Aşağıdaki örnek **, MICROSOFTBOOKINGS** **(Microsoft Bookings**) ve LOCKBOX_ENTERPRISE (Müşteri Kasası) hizmetlerinin kapalı olduğu **SPE_E5 (Microsoft 365 E5**) atar:
  
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

Set-MgUserLicense içindeki AddLicenses parametresinin DisabledPlans özelliği, kullanıcının mevcut DisabledPlans değerinin üzerine yazar. Mevcut hizmet planlarının durumunu korumak için, kullanıcının geçerli hizmet planlarının durumu devre dışı bırakılacak yeni planlarla birleştirilmelidir.

Mevcut DisabledPlans'ın eklenememesi, kullanıcının daha önce devre dışı bırakılmış planının etkinleştirilmesine neden olur.

Aşağıdaki örnek bir kullanıcıyı **SPE_E5** (Microsoft 365 E5) ile güncelleştirir ve kullanıcının mevcut devre dışı planlarını geçerli durumunda bırakırken Sway ve Forms hizmet planlarını kapatır:
  
```powershell
## Get the services that have already been disabled for the user.
$userLicense = Get-MgUserLicenseDetail -UserId "belinda@fdoau.onmicrosoft.com"
$userDisabledPlans = $userLicense.ServicePlans | `
    Where ProvisioningStatus -eq "Disabled" | `
    Select -ExpandProperty ServicePlanId

## Get the new service plans that are going to be disabled
$e5Sku = Get-MgSubscribedSku -All | Where SkuPartNumber -eq 'SPE_E5'
$newDisabledPlans = $e5Sku.ServicePlans | `
    Where ServicePlanName -in ("SWAY", "FORMS_PLAN_E5") | `
    Select -ExpandProperty ServicePlanId

## Merge the new plans that are to be disabled with the user's current state of disabled plans
$disabledPlans = ($userDisabledPlans + $newDisabledPlans) | Select -Unique

$addLicenses = @(
    @{
        SkuId = $e5Sku.SkuId
        DisabledPlans = $disabledPlans
    }
)
## Update user's license
Set-MgUserLicense -UserId "belinda@litwareinc.onmicrosoft.com" -AddLicenses $addLicenses -RemoveLicenses @()
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Windows PowerShell için Microsoft Azure Active Directory Modülünü kullanma

İlk olarak [Microsoft 365 kiracınıza bağlanın](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

Ardından, AccountSkuIds olarak da bilinen kullanılabilir lisans planlarınızı görüntülemek için bu komutu kullanın:

```powershell
Get-MsolAccountSku | Select AccountSkuId | Sort AccountSkuId
```

>[!Note]
>PowerShell Core, Windows PowerShell modülü için Microsoft Azure Active Directory Modülünü ve adında **Msol** bulunan cmdlet'leri desteklemez. Bu cmdlet'leri kullanmaya devam etmek için bunları Windows PowerShell çalıştırmanız gerekir.
>

Daha fazla bilgi için bkz. [PowerShell ile lisansları ve hizmetleri görüntüleme](view-licenses-and-services-with-microsoft-365-powershell.md).
    
Bu konudaki yordamların önce ve sonra sonuçlarını görmek için bkz. [PowerShell ile hesap lisansı ve hizmet ayrıntılarını görüntüleme](view-account-license-and-service-details-with-microsoft-365-powershell.md).
    
Bu konuda açıklanan yordamları otomatik hale getiren bir PowerShell betiği mevcuttur. Özellikle betik, Sway dahil olmak üzere Microsoft 365 kuruluşunuzdaki hizmetleri görüntülemenize ve devre dışı bırakmanıza olanak tanır. Daha fazla bilgi için bkz. [PowerShell ile Sway erişimini devre dışı bırakma](disable-access-to-sway-with-microsoft-365-powershell.md).
    
    
### <a name="disable-specific-microsoft-365-services-for-specific-users-for-a-specific-licensing-plan"></a>Belirli bir lisans planı için belirli kullanıcılar için belirli Microsoft 365 hizmetlerini devre dışı bırakma
  
Belirli bir lisans planı için kullanıcılara yönelik belirli bir Microsoft 365 hizmetini devre dışı bırakmak için aşağıdaki adımları uygulayın:
  
#### <a name="step-1-identify-the-undesired-services-in-the-licensing-plan-by-using-the-following-syntax"></a>1. Adım: Aşağıdaki söz dizimini kullanarak lisans planındaki istenmeyen hizmetleri belirleyin:
    
```powershell
$LO = New-MsolLicenseOptions -AccountSkuId <AccountSkuId> -DisabledPlans "<UndesiredService1>", "<UndesiredService2>"...
```

Aşağıdaki örnek, (Office 365 Kurumsal E3) adlı `litwareinc:ENTERPRISEPACK` lisans planında Office ve SharePoint Online hizmetlerini devre dışı bırakmaya yönelik bir **LicenseOptions** nesnesi oluşturur.
    
```powershell
$LO = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
```

#### <a name="step-2-use-the-licenseoptions-object-from-step-1-on-one-or-more-users"></a>2. Adım: Bir veya daha fazla kullanıcıda 1. Adımdaki **LicenseOptions** nesnesini kullanın.
    
Hizmetleri devre dışı bırakmış yeni bir hesap oluşturmak için aşağıdaki söz dizimini kullanın:
    
```powershell
New-MsolUser -UserPrincipalName <Account> -DisplayName <DisplayName> -FirstName <FirstName> -LastName <LastName> -LicenseAssignment <AccountSkuId> -LicenseOptions $LO -UsageLocation <CountryCode>
```

Aşağıdaki örnek, Allie Bellew için lisansı atayan ve 1. Adımda açıklanan hizmetleri devre dışı bırakmaya yönelik yeni bir hesap oluşturur.
    
```powershell
New-MsolUser -UserPrincipalName allieb@litwareinc.com -DisplayName "Allie Bellew" -FirstName Allie -LastName Bellew -LicenseAssignment litwareinc:ENTERPRISEPACK -LicenseOptions $LO -UsageLocation US
```

Microsoft 365 için PowerShell'de kullanıcı hesapları oluşturma hakkında daha fazla bilgi için bkz. [PowerShell ile kullanıcı hesapları oluşturma](create-user-accounts-with-microsoft-365-powershell.md).
    
Mevcut lisanslı bir kullanıcının hizmetlerini devre dışı bırakmak için aşağıdaki söz dizimini kullanın:
    
```powershell
Set-MsolUserLicense -UserPrincipalName <Account> -LicenseOptions $LO
```

Bu örnek, kullanıcı BelindaN@litwareinc.com için hizmetleri devre dışı bırakır.
    
```powershell
Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -LicenseOptions $LO
```

1. Adım'da açıklanan hizmetleri tüm mevcut lisanslı kullanıcılar için devre dışı bırakmak için **Get-MsolAccountSku** cmdlet'inin (**litwareinc:ENTERPRISEPACK** gibi) görüntüsünden Microsoft 365 planınızın adını belirtin ve ardından aşağıdaki komutları çalıştırın:
    
```powershell
$acctSKU="<AccountSkuId>"
$AllLicensed = Get-MsolUser -All | Where {$_.isLicensed -eq $true -and $_.licenses.AccountSku.SkuPartNumber -contains ($acctSKU).Substring($acctSKU.IndexOf(":")+1, $acctSKU.Length-$acctSKU.IndexOf(":")-1)}
$AllLicensed | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
```

 **Get-MsolUser** cmdlet'ini _All_ parametresini kullanmadan kullanırsanız, yalnızca ilk 500 kullanıcı hesabı döndürülür.

Mevcut bir kullanıcı grubunun hizmetlerini devre dışı bırakmak için, kullanıcıları tanımlamak için aşağıdaki yöntemlerden birini kullanın:
    
**Yöntem 1. Hesapları mevcut bir hesap özniteliğine göre filtreleme** 

Bunu yapmak için aşağıdaki söz dizimini kullanın:
    
```powershell
$x = Get-MsolUser -All <FilterableAttributes>
$x | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
```

Aşağıdaki örnek, Birleşik Devletler Satış departmanındaki kullanıcılar için hizmetleri devre dışı bırakır.
    
```powershell
$USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US"
$USSales | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
```

**Yöntem 2: Belirli hesapların listesini kullanma** 

Bunu yapmak için aşağıdaki adımları uygulayın:
    
1. Her satırda aşağıdaki gibi bir hesap içeren bir metin dosyası oluşturun:
    
   ```powershell
   akol@contoso.com
   tjohnston@contoso.com
   kakers@contoso.com
   ```

   Bu örnekte, metin dosyası C:\\Belgelerim\\Accounts.txt şeklindedir.
    
2. Aşağıdaki komutu çalıştırın:
    
   ```powershell
   Get-Content "C:\My Documents\Accounts.txt" | foreach {Set-MsolUserLicense -UserPrincipalName $_ -LicenseOptions $LO}
   ```

Birden çok lisans planı için hizmetlere erişimi devre dışı bırakmak istiyorsanız, aşağıdakilerden emin olmak için yukarıdaki yönergeleri her lisans planı için tekrarlayın:

- Kullanıcı hesaplarına lisans planı atanmıştır.
- Devre dışı bırakacak hizmetler lisans planında kullanılabilir.

Kullanıcılara lisans planı atarken Microsoft 365 hizmetlerini devre dışı bırakmak için bkz. [Kullanıcı lisansları atarken hizmetlere erişimi devre dışı bırakma](disable-access-to-services-while-assigning-user-licenses.md).

### <a name="assign-all-services-in-a-licensing-plan-to-a-user-account"></a>Lisans planındaki tüm hizmetleri kullanıcı hesabına atama

Hizmetleri devre dışı bırakılmış kullanıcı hesapları için, aşağıdaki komutlarla belirli bir lisans planı için tüm hizmetleri etkinleştirebilirsiniz:

```powershell
$userUPN="<user account UPN>"
$acctSKU="<AccountSkuId>"
$LO = New-MsolLicenseOptions -AccountSkuId $acctSKU
Set-MsolUserLicense -UserPrincipalName $userUPN -LicenseOptions $LO
```

## <a name="related-topic"></a>İlgili konu

[PowerShell ile Microsoft 365 kullanıcı hesaplarını, lisanslarını ve gruplarını yönetme](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
  
[PowerShell ile Microsoft 365’i yönetme](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[Microsoft 365 için PowerShell'i kullanmaya başlama](getting-started-with-microsoft-365-powershell.md)
