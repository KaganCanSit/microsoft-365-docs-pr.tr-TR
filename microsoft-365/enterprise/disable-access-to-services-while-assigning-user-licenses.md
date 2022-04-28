---
title: Kullanıcı lisansları atarken Microsoft 365 hizmetlerine erişimi devre dışı bırakma
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 04/24/2020
audience: Admin
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-administration
ms.localizationpriority: medium
search.appverid:
- MET150
f1.keywords:
- CSH
ms.custom:
- PowerShell
- Ent_Office_Other
ms.assetid: bb003bdb-3c22-4141-ae3b-f0656fc23b9c
description: Microsoft 365 için PowerShell kullanarak kullanıcı hesaplarına lisans atamayı ve belirli hizmet planlarını aynı anda devre dışı bırakmayı öğrenin.
ms.openlocfilehash: 6c0c3a3860da8a1935152fcaefb29f2f355cfa49
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65095740"
---
# <a name="disable-access-to-microsoft-365-services-while-assigning-user-licenses"></a>Kullanıcı lisansları atarken Microsoft 365 hizmetlerine erişimi devre dışı bırakma

*Bu makale hem Microsoft 365 Kurumsal hem de Office 365 Kurumsal için geçerlidir.*

Microsoft 365 abonelikler tek tek hizmetler için hizmet planları ile birlikte gelir. Microsoft 365 yöneticilerin genellikle kullanıcılara lisans atarken belirli planları devre dışı bırakması gerekir. Bu makaledeki yönergelerle, tek bir kullanıcı hesabı veya birden çok kullanıcı hesabı için PowerShell kullanarak belirli hizmet planlarını devre dışı bırakırken bir Microsoft 365 lisansı atayabilirsiniz.

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Graph için Azure Active Directory PowerShell modülünü kullanma

İlk olarak [Microsoft 365 kiracınıza bağlanın](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).


Ardından, bu komutla kiracınızın lisans planlarını listeleyin.

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

Ardından, lisans eklemek istediğiniz hesabın oturum açma adını (kullanıcı asıl adı (UPN) olarak da bilinir) alın.

Ardından, etkinleştirecek hizmetlerin listesini derleyin. Lisans planlarının tam listesi (ürün adları olarak da bilinir), bunların dahil edilen hizmet planları ve bunlara karşılık gelen kolay adları için bkz. [Lisanslama için ürün adları ve hizmet planı tanımlayıcıları](/azure/active-directory/users-groups-roles/licensing-service-plan-reference).

Aşağıdaki komut bloğu için, açıklayıcı metni ve karakterleri etkinleştirmek ve kaldırmak için kullanıcı hesabının kullanıcı asıl adını, SKU parça numarasını ve \< and > hizmet planlarının listesini doldurun. Ardından, PowerShell komut isteminde sonuç komutlarını çalıştırın.

```powershell
$userUPN="<user account UPN>"
$skuPart="<SKU part number>"
$serviceList=<double-quoted enclosed, comma-separated list of enabled services>
$user = Get-AzureADUser -ObjectID $userUPN
$skuID= (Get-AzureADSubscribedSku  | Where {$_.SkuPartNumber -eq $skuPart}).SkuID
$SkuFeaturesToEnable = @($serviceList)
$StandardLicense = Get-AzureADSubscribedSku | Where {$_.SkuId -eq $skuID}
$SkuFeaturesToDisable = $StandardLicense.ServicePlans | ForEach-Object { $_ | Where {$_.ServicePlanName -notin $SkuFeaturesToEnable }}
$License = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$License.SkuId = $StandardLicense.SkuId
$License.DisabledPlans = $SkuFeaturesToDisable.ServicePlanId
$LicensesToAssign = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$LicensesToAssign.AddLicenses = $License
Set-AzureADUserLicense -ObjectId $user.ObjectId -AssignedLicenses $LicensesToAssign
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Windows PowerShell için Microsoft Azure Active Directory Modülünü kullanma

İlk olarak [Microsoft 365 kiracınıza bağlanın](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

Ardından, geçerli aboneliklerinizi görmek için şu komutu çalıştırın:

```powershell
Get-MsolAccountSku
```

>[!Note]
>PowerShell Core, Windows PowerShell modülü için Microsoft Azure Active Directory Modülünü ve adında **Msol** bulunan cmdlet'leri desteklemez. Bu cmdlet'leri kullanmaya devam etmek için bunları Windows PowerShell çalıştırmanız gerekir.
>

Komutun görüntüsünde  `Get-MsolAccountSku` :

- **AccountSkuId**, kuruluşunuz için biçimindeki \<OrganizationName>\<Subscription> bir aboneliktir. \<OrganizationName>, Microsoft 365 kaydolduğunuz sırada sağladığınız değerdir ve kuruluşunuz için benzersizdir. \<Subscription> Değer belirli bir aboneliğe yöneliktir. Örneğin, litwareinc:ENTERPRISEPACK için kuruluş adı litwareinc, abonelik adı ise ENTERPRISEPACK (Office 365 Kurumsal E3) şeklindedir.

- **ActiveUnits** , abonelik için satın aldığınız lisans sayısıdır.

- **WarningUnits** , abonelikte yenilemediğiniz lisansların sayısıdır ve bu lisans 30 günlük yetkisiz kullanım süresinden sonra sona erer.

- **ConsumedUnits** , abonelik için kullanıcılara atadığınız lisans sayısıdır.

Lisanslamak istediğiniz kullanıcıları içeren Microsoft 365 aboneliğinizin AccountSkuId değerini not edin. Ayrıca, atanacak yeterli lisans olduğundan emin olun (**ConsumedUnits'i ActiveUnits'ten** çıkarın).

Ardından, tüm aboneliklerinizde kullanılabilen Microsoft 365 hizmet planları hakkındaki ayrıntıları görmek için şu komutu çalıştırın:

```powershell
Get-MsolAccountSku | Select -ExpandProperty ServiceStatus
```

Bu komutun görüntüsünden, kullanıcılara lisans atarken hangi hizmet planlarını devre dışı bırakmak istediğinizi belirleyin.

Hizmet planlarının ve ilgili Microsoft 365 hizmetlerinin kısmi listesi aşağıdadır.

Aşağıdaki tabloda Microsoft 365 hizmet planları ve bunların en yaygın hizmetler için kolay adları gösterilmektedir. Hizmet planlarınızın listesi farklı olabilir.

|**Hizmet planı**|**Açıklama**|
|:-----|:-----|
| `SWAY` <br/> |Sway  <br/> |
| `TEAMS1` <br/> |Microsoft Teams  <br/> |
| `YAMMER_ENTERPRISE` <br/> |Yammer  <br/> |
| `RMS_S_ENTERPRISE` <br/> |Azure Rights Management (RMS)  <br/> |
| `OFFICESUBSCRIPTION` <br/> |Kurumlar için Microsoft 365 Uygulamaları *(eski adıyla Office 365 ProPlus)*  <br/> |
| `MCOSTANDARD` <br/> |Skype Kurumsal Çevrimiçi  <br/> |
| `SHAREPOINTWAC` <br/> |Office   <br/> |
| `SHAREPOINTENTERPRISE` <br/> |SharePoint Online  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |Exchange Online Plan 2  <br/> |

Lisans planlarının tam listesi (ürün adları olarak da bilinir), bunların dahil edilen hizmet planları ve bunlara karşılık gelen kolay adları için bkz. [Lisanslama için ürün adları ve hizmet planı tanımlayıcıları](/azure/active-directory/users-groups-roles/licensing-service-plan-reference).

Artık AccountSkuId'niz ve devre dışı bırakabileceğiniz hizmet planlarınız olduğuna göre, tek bir kullanıcı veya birden çok kullanıcı için lisans atayabilirsiniz.

### <a name="for-a-single-user"></a>Tek bir kullanıcı için

Tek bir kullanıcı için, açıklayıcı metni ve karakterleri devre dışı bırakmak ve kaldırmak için kullanıcı hesabının kullanıcı asıl adını, AccountSkuId değerini ve \< and > hizmet planlarının listesini doldurun. Ardından, PowerShell komut isteminde sonuç komutlarını çalıştırın.

```powershell
$userUPN="<the user's account name in email format>"
$accountSkuId="<the AccountSkuId from the Get-MsolAccountSku command>"
$planList=@( <comma-separated, double-quote enclosed list of the service plans to disable> )
$licenseOptions=New-MsolLicenseOptions -AccountSkuId $accountSkuId -DisabledPlans $planList
Set-MsolUserLicense -UserPrincipalName $userUpn -AddLicenses $accountSkuId -ErrorAction SilentlyContinue
Sleep -Seconds 5
Set-MsolUserLicense -UserPrincipalName $userUpn -LicenseOptions $licenseOptions -ErrorAction SilentlyContinue
```

contoso:ENTERPRISEPACK lisansı için belindan@contoso.com adlı hesap için örnek bir komut bloğu ve devre dışı bırakılma planları RMS_S_ENTERPRISE, SWAY, INTUNE_O365 ve YAMMER_ENTERPRISE:

```powershell
$userUPN="belindan@contoso.com"
$accountSkuId="contoso:ENTERPRISEPACK"
$planList=@( "RMS_S_ENTERPRISE","SWAY","INTUNE_O365","YAMMER_ENTERPRISE" )
$licenseOptions=New-MsolLicenseOptions -AccountSkuId $accountSkuId -DisabledPlans $planList
Set-MsolUserLicense -UserPrincipalName $userUpn -AddLicenses $accountSkuId -ErrorAction SilentlyContinue
Sleep -Seconds 5
Set-MsolUserLicense -UserPrincipalName $userUpn -LicenseOptions $licenseOptions -ErrorAction SilentlyContinue
```

### <a name="for-multiple-users"></a>Birden çok kullanıcı için

Bu yönetim görevini birden çok kullanıcı için gerçekleştirmek için UserPrincipalName ve UsageLocation alanlarını içeren bir virgülle ayrılmış değer (CSV) metin dosyası oluşturun. Aşağıda bir örnek verilmiştir:

```powershell
UserPrincipalName,UsageLocation
ClaudeL@contoso.onmicrosoft.com,FR
LynneB@contoso.onmicrosoft.com,US
ShawnM@contoso.onmicrosoft.com,US
```

Ardından, giriş ve çıkış CSV dosyalarının konumunu, hesap SKU kimliğini ve devre dışı bırakılacak hizmet planlarının listesini doldurun ve ardından PowerShell komut isteminde sonuç komutlarını çalıştırın.

```powershell
$inFileName="<path and file name of the input CSV file that contains the users, example: C:\admin\Users2License.CSV>"
$outFileName="<path and file name of the output CSV file that records the results, example: C:\admin\Users2License-Done.CSV>"
$accountSkuId="<the AccountSkuId from the Get-MsolAccountSku command>"
$planList=@( <comma-separated, double-quote enclosed list of the plans to disable> )
$users=Import-Csv $inFileName
$licenseOptions=New-MsolLicenseOptions -AccountSkuId $accountSkuId -DisabledPlans $planList
ForEach ($user in $users)
{
$user.Userprincipalname
$upn=$user.UserPrincipalName
Set-MsolUserLicense -UserPrincipalName $upn -AddLicenses $accountSkuId -ErrorAction SilentlyContinue
sleep -Seconds 5
Set-MsolUserLicense -UserPrincipalName $upn -LicenseOptions $licenseOptions -ErrorAction SilentlyContinue
$users | Get-MsolUser | Select UserPrincipalName, Islicensed,Usagelocation | Export-Csv $outFileName
}
```

Bu PowerShell komut bloğu:

- Her kullanıcının kullanıcı asıl adını görüntüler.

- Her kullanıcıya özelleştirilmiş lisanslar atar.

- İşlenen tüm kullanıcılarla birlikte bir CSV dosyası oluşturur ve lisans durumlarını gösterir.

## <a name="see-also"></a>Ayrıca bkz.

[PowerShell ile Microsoft 365 hizmetlerine erişimi devre dışı bırakma](disable-access-to-services-with-microsoft-365-powershell.md)

[PowerShell ile Sway erişimini devre dışı bırakma](disable-access-to-sway-with-microsoft-365-powershell.md)

[PowerShell ile Microsoft 365 kullanıcı hesaplarını, lisanslarını ve gruplarını yönetme](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)

[PowerShell ile Microsoft 365’i yönetme](manage-microsoft-365-with-microsoft-365-powershell.md)