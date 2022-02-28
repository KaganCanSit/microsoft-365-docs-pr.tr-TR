---
title: PowerShell ile Microsoft 365 erişimini devre dışı bırakma
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: Bu makalede, kullanıcıların powershell ve hizmetlere erişimini devre dışı bırakmak için Microsoft 365 öğrenin.
ms.openlocfilehash: bce02c40bf6ca99d74b8747fb0c5eb5c0b485888
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62985583"
---
# <a name="disable-access-to-microsoft-365-services-with-powershell"></a>PowerShell ile Microsoft 365 erişimini devre dışı bırakma

*Bu makale hem son hem de Microsoft 365 Kurumsal hem de Office 365 Kurumsal.*

Lisans Microsoft 365 lisansı atandığı zaman, Microsoft 365 lisansından kullanıcıya bu hizmetler kullanılabilir. Bununla birlikte, kullanıcının Microsoft 365 eriş erişen diğer hizmetleri de denetim altına aabilirsiniz. Örneğin, lisans SharePoint Online hizmetine erişim izni olsa bile, buna erişimi devre dışı abilirsiniz. Aşağıdakiler için belirli bir lisans planında herhangi bir sayıda hizmete erişimi devre dışı bırakmak üzere PowerShell'i kullanabilirsiniz:

- Tek bir hesap.
- Bir grup hesap.
- Organizasyon'daki tüm hesaplar.

>[!Note]
>Diğer Microsoft 365 bağlı olduğunda, belirli bir hizmeti devre dışı bırakmanıza engel olacak başka hizmet bağımlılıkları vardır.
>

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Kaynak için Microsoft Azure Active Directory Modülü'Windows PowerShell

İlk olarak[, kiracınıza bağlan Microsoft 365 bağlanin](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

Ardından, accountSkuIds olarak da bilinen kullanılabilir lisans planlarınızı görüntülemek için bu komutu kullanın:

```powershell
Get-MsolAccountSku | Select AccountSkuId | Sort AccountSkuId
```

>[!Note]
>PowerShell Core, **Msol'Microsoft Azure Active Directory Msol** Windows PowerShell cmdlet'leri için Modül Adını Desteklemez. Bu cmdlet'leri kullanmaya devam etmek için, tüm cmdlet'leri Windows PowerShell.
>

Daha fazla bilgi için bkz [. PowerShell ile lisansları ve hizmetleri görüntüleme](view-licenses-and-services-with-microsoft-365-powershell.md).
    
Bu konudaki yordamların önceki ve sonra sonuçlarını görmek için bkz. [PowerShell ile hesap lisansını ve hizmet ayrıntılarını görüntüleme](view-account-license-and-service-details-with-microsoft-365-powershell.md).
    
Bu konuda açıklanan yordamları otomatik haleleştiren bir PowerShell betiği kullanılabilir. Özel olarak betik, Sway dahil olmak üzere Microsoft 365 hizmetleri görüntülemenize ve devre dışı bırakmanıza olanak sağlar. Daha fazla bilgi için bkz. [PowerShell ile Sway'e erişimi devre dışı bırakma](disable-access-to-sway-with-microsoft-365-powershell.md).
    
    
### <a name="disable-specific-microsoft-365-services-for-specific-users-for-a-specific-licensing-plan"></a>Belirli bir Microsoft 365 planı için belirli kullanıcı hizmetleri devre dışı bırakma
  
Belirli bir lisans planına yönelik Microsoft 365 hizmet kümelerini devre dışı bırakmak için aşağıdaki adımları izleyin:
  
#### <a name="step-1-identify-the-undesired-services-in-the-licensing-plan-by-using-the-following-syntax"></a>1. Adım: Lisans planında, aşağıdaki söz dizimlerini kullanarak, masasız hizmetleri tanımlama:
    
```powershell
$LO = New-MsolLicenseOptions -AccountSkuId <AccountSkuId> -DisabledPlans "<UndesiredService1>", "<UndesiredService2>"...
```

Aşağıdaki örnek, lisans planında (Office 365 Kurumsal E3) Office ve SharePoint Online `litwareinc:ENTERPRISEPACK` hizmetlerini devre dışı bırakan **bir LicenseOptions** nesnesi oluşturur.
    
```powershell
$LO = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
```

#### <a name="step-2-use-the-licenseoptions-object-from-step-1-on-one-or-more-users"></a>2. Adım: Bir **veya birden çok kullanıcıda** 1. Adım'da yer alan LicenseOptions nesnesini kullanın.
    
Hizmetlerin devre dışı olduğu yeni bir hesap oluşturmak için aşağıdaki söz dizimlerini kullanın:
    
```powershell
New-MsolUser -UserPrincipalName <Account> -DisplayName <DisplayName> -FirstName <FirstName> -LastName <LastName> -LicenseAssignment <AccountSkuId> -LicenseOptions $LO -UsageLocation <CountryCode>
```

Aşağıdaki örnek, Allie Bellew için lisansı ataan ve 1. Adımda açıklanan hizmetleri devre dışı bırakmak için yeni bir hesap oluşturur.
    
```powershell
New-MsolUser -UserPrincipalName allieb@litwareinc.com -DisplayName "Allie Bellew" -FirstName Allie -LastName Bellew -LicenseAssignment litwareinc:ENTERPRISEPACK -LicenseOptions $LO -UsageLocation US
```

Microsoft 365 için PowerShell'de kullanıcı hesapları oluşturma hakkında daha fazla bilgi için bkz[. PowerShell ile kullanıcı hesapları oluşturma](create-user-accounts-with-microsoft-365-powershell.md).
    
Mevcut lisanslı kullanıcının hizmetlerini devre dışı bırakmak için aşağıdaki söz dizimi kullanın:
    
```powershell
Set-MsolUserLicense -UserPrincipalName <Account> -LicenseOptions $LO
```

Bu örnekte, kullanıcının oturum ayaları devre dışı BelindaN@litwareinc.com.
    
```powershell
Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -LicenseOptions $LO
```

1. Adımda açıklanan hizmetleri devre dışı bırakmak için, **Get-MsolAccountSku** cmdlet'ini (**litwareinc:ENTERPRISEPACK** gibi) görüntüden Microsoft 365 planınızı belirtin ve sonra aşağıdaki komutları çalıştırın:
    
```powershell
$acctSKU="<AccountSkuId>"
$AllLicensed = Get-MsolUser -All | Where {$_.isLicensed -eq $true -and $_.licenses.AccountSku.SkuPartNumber -contains ($acctSKU).Substring($acctSKU.IndexOf(":")+1, $acctSKU.Length-$acctSKU.IndexOf(":")-1)}
$AllLicensed | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
```

 **Get-MsolUser** cmdlet'ini _All_ parametresini kullanmadan kullanırsanız, yalnızca ilk 500 kullanıcı hesabı döndürülür.

Var olan bir grup kullanıcının hizmetlerini devre dışı bırakmak için, kullanıcıları tanımlamak için aşağıdaki yöntemlerden birini kullanın:
    
**Yöntem 1. Hesapları mevcut bir hesap özniteliğine göre filtreleme** 

Bunu yapmak için aşağıdaki söz dizimlerini kullanın:
    
```powershell
$x = Get-MsolUser -All <FilterableAttributes>
$x | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
```

Aşağıdaki örnekte, ABD'de Satış departmanında yer alan kullanıcılar için hizmetler devre dışıdır.
    
```powershell
$USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US"
$USSales | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
```

**Yöntem 2: Belirli hesapların listesini kullanma** 

Bunu yapmak için aşağıdaki adımları izleyin:
    
1. Her satırda bir hesap içeren bir metin dosyası şu şekilde oluşturun:
    
   ```powershell
   akol@contoso.com
   tjohnston@contoso.com
   kakers@contoso.com
   ```

   Bu örnekte metin dosyası şu şekildedir: C:\\BelgelerimAccounts.txt\\ .
    
2. Aşağıdaki komutu çalıştırın:
    
   ```powershell
   Get-Content "C:\My Documents\Accounts.txt" | foreach {Set-MsolUserLicense -UserPrincipalName $_ -LicenseOptions $LO}
   ```

Birden çok lisans planında hizmetlere erişimi devre dışı bırakmak için yukarıdaki yönergeleri her lisans planı için tekrarlayın; şu yönergeler sağlanabilir:

- Kullanıcı hesaplarına lisans planı atandı.
- Devre dışı bırakılama hizmetleri lisans planında kullanılabilir.

Lisans planına Microsoft 365 hizmetleri devre dışı bırakmak için bkz. Kullanıcı lisansları atarken hizmetlere erişimi [devre dışı bırakma](disable-access-to-services-while-assigning-user-licenses.md).

### <a name="assign-all-services-in-a-licensing-plan-to-a-user-account"></a>Lisans planında yer alan tüm hizmetleri kullanıcı hesabına atama

Hizmetleri devre dışı bırakılmış olan kullanıcı hesapları için, şu komutlarla belirli bir lisans planı için tüm hizmetleri etkinleştirebilirsiniz:

```powershell
$userUPN="<user account UPN>"
$acctSKU="<AccountSkuId>"
$LO = New-MsolLicenseOptions -AccountSkuId $acctSKU
Set-MsolUserLicense -UserPrincipalName $userUPN -LicenseOptions $LO
```

## <a name="related-topic"></a>İlgili konu

[PowerShell Microsoft 365 hesaplarını, lisanslarını ve gruplarını yönetme](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
  
[PowerShell Microsoft 365'i yönetme](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[Microsoft 365 için PowerShell ile çalışmaya Microsoft 365](getting-started-with-microsoft-365-powershell.md)
