---
title: Kullanıcı lisansları atarken Microsoft 365'e erişimi devre dışı bırakma
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: Microsoft 365 için PowerShell kullanarak kullanıcı hesaplarına lisans atamayı ve belirli hizmet planlarını devre dışı bırakmayı Microsoft 365.
ms.openlocfilehash: 5b7130930097970f5cfabc9a7599c211393b7c7a
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62985149"
---
# <a name="disable-access-to-microsoft-365-services-while-assigning-user-licenses"></a>Kullanıcı lisansları atarken Microsoft 365'e erişimi devre dışı bırakma

*Bu makale hem son hem de Microsoft 365 Kurumsal hem de Office 365 Kurumsal.*

Microsoft 365 abonelikler, tek tek hizmetler için hizmet planları içerir. Microsoft 365 kullanıcılarına lisans atarken genellikle bazı planları devre dışı bırakması gerekir. Bu makaledeki yönergelerle, tek bir kullanıcı hesabı veya birden çok kullanıcı hesabı için PowerShell kullanarak belirli hizmet planlarını devre dışı bırakarak Microsoft 365 lisansı atabilirsiniz.

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Graph modülü için Azure Active Directory PowerShell'i kullanma

İlk olarak[, kiracınıza bağlan Microsoft 365 bağlanin](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).


Ardından, bu komutla kiracınıza uygun lisans planlarını listelenin.

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

Ardından, lisans eklemek istediğiniz hesabın kullanıcı asıl adı (UPN) olarak da bilinen oturum açma adını alın.

Ardından, etkinleştirmek için hizmetlerin listesini derlenin. Lisans planlarının (ürün adları olarak da bilinir), dahil edilen hizmet planlarının ve bunların uygun adlarının tam listesi için bkz. Lisans için ürün adları ve [hizmet planı tanımlayıcıları](/azure/active-directory/users-groups-roles/licensing-service-plan-reference).

Aşağıdaki komut bloğunda, açıklayıcı metni ve karakterleri etkinleştirmek ve kaldırmak için kullanıcı hesabının kullanıcı asıl adını, SKU parça numarasını ve hizmet planlarının listesini \< and > doldurun. Ardından, PowerShell komut isteminde sonuç komutlarını çalıştırın.

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

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Kaynak için Microsoft Azure Active Directory Modülü'Windows PowerShell

İlk olarak[, kiracınıza bağlan Microsoft 365 bağlanin](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

Ardından, geçerli aboneliklerinizi görmek için bu komutu çalıştırın:

```powershell
Get-MsolAccountSku
```

>[!Note]
>PowerShell Core, **Msol'Microsoft Azure Active Directory Msol** Windows PowerShell cmdlet'leri için Modül Adını Desteklemez. Bu cmdlet'leri kullanmaya devam etmek için, tüm cmdlet'leri Windows PowerShell.
>

Komutun görüntüsünde  `Get-MsolAccountSku` :

- **AccountSkuId** , organizasyon için : biçimindeki bir \<OrganizationName>aboneliktir\<Subscription> . Bu\<OrganizationName>, e-okul hizmetine kaydolarak Microsoft 365 ve benzersiz olan değerdir. Değer \<Subscription> belirli bir abonelik içindir. Örneğin, litwareinc:ENTERPRISEPACK için, kuruluşun adı litwareinc ve abonelik adı da ENTERPRISEPACK (Office 365 Kurumsal E3) olur.

- **ActiveUnits** , abonelik için satın aldığınız lisansların sayısıdır.

- **UyarıUnits** , yenilememiş bir abonelikte yer alan ve 30 günlük yetkisiz kullanım süresinin ardından sona erecek olan lisansların sayısıdır.

- **ConsumedUnits** , aboneliğe atadınız lisansların sayısıdır.

Lisans almak istediğiniz kullanıcıları içeren Microsoft 365 AccountSkuId hesabına dikkat edin. Ayrıca, atamak için yeterli lisans olduğundan emin olun (**ActiveUnits'den ConsumedUnits'i çıkarma**).

Ardından, tüm aboneliklerinize uygun olan Microsoft 365 planlarına ilişkin ayrıntıları görmek için bu komutu çalıştırın:

```powershell
Get-MsolAccountSku | Select -ExpandProperty ServiceStatus
```

Bu komutun görüntüsünden, kullanıcılara lisans atarken devre dışı bırakmak istediğiniz hizmet planlarını seçin.

Burada, hizmet planlarının ve ilgili hizmet planlarının kısmi bir listesi Microsoft 365 ve sonra Microsoft 365 ve ve devammektedir.

Aşağıdaki tabloda, en yaygın Microsoft 365 planları ve kolay adları yer alır. Hizmet planları listeniz farklı olabilir.

|**Hizmet planı**|**Açıklama**|
|:-----|:-----|
| `SWAY` <br/> |Sway  <br/> |
| `TEAMS1` <br/> |Microsoft Teams  <br/> |
| `YAMMER_ENTERPRISE` <br/> |Yammer  <br/> |
| `RMS_S_ENTERPRISE` <br/> |Azure Hak Yönetimi (RMS)  <br/> |
| `OFFICESUBSCRIPTION` <br/> |Kurumlar için Microsoft 365 Uygulamaları *(daha önce adlandırılmış Office 365 ProPlus)*  <br/> |
| `MCOSTANDARD` <br/> |Skype Kurumsal Çevrimiçi  <br/> |
| `SHAREPOINTWAC` <br/> |Office   <br/> |
| `SHAREPOINTENTERPRISE` <br/> |SharePoint Online  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |Exchange Online Plan 2  <br/> |

Lisans planlarının (ürün adları olarak da bilinir), dahil edilen hizmet planlarının ve bunların uygun adlarının tam listesi için bkz. Lisans için ürün adları ve [hizmet planı tanımlayıcıları](/azure/active-directory/users-groups-roles/licensing-service-plan-reference).

Artık AccountSkuId'niz ve devre dışı bırakmak istediğiniz hizmet planlarına sahip olduğunuz için, tek bir kullanıcıya veya birden çok kullanıcıya lisans atabilirsiniz.

### <a name="for-a-single-user"></a>Tek bir kullanıcı için

Tek bir kullanıcı için, açıklayıcı metni ve karakterleri devre dışı bırakmak ve kaldırmak için kullanıcı hesabının kullanıcı asıl adını, AccountSkuId'yi ve hizmet planlarının listesini \< and > doldurun. Ardından, PowerShell komut isteminde sonuç komutlarını çalıştırın.

```powershell
$userUPN="<the user's account name in email format>"
$accountSkuId="<the AccountSkuId from the Get-MsolAccountSku command>"
$planList=@( <comma-separated, double-quote enclosed list of the service plans to disable> )
$licenseOptions=New-MsolLicenseOptions -AccountSkuId $accountSkuId -DisabledPlans $planList
Set-MsolUserLicense -UserPrincipalName $userUpn -AddLicenses $accountSkuId -ErrorAction SilentlyContinue
Sleep -Seconds 5
Set-MsolUserLicense -UserPrincipalName $userUpn -LicenseOptions $licenseOptions -ErrorAction SilentlyContinue
```

contoso:ENTERPRISEPACK lisansı için belindan@contoso.com adlı hesabın örnek bir komut bloğu ve devre dışı bırakılma planları RMS_S_ENTERPRISE, SWAY, INTUNE_O365 ve YAMMER_ENTERPRISE:

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

Bu yönetim görevini birden çok kullanıcı için gerçekleştirmek için, UserPrincipalName ve UsageLocation alanlarını içeren bir virgülle ayrılmış değer (CSV) metin dosyası oluşturun. İşte bir örnek:

```powershell
UserPrincipalName,UsageLocation
ClaudeL@contoso.onmicrosoft.com,FR
LynneB@contoso.onmicrosoft.com,US
ShawnM@contoso.onmicrosoft.com,US
```

Ardından, CSV dosyaları için giriş ve çıkış konumlarını, hesap SKU Kimliği'ni ve devre dışı bırakacak hizmet planlarının listesini doldurun, ardından PowerShell komut isteminde sonuç komutlarını çalıştırın.

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

- İşlenen tüm kullanıcılarla bir CSV dosyası oluşturur ve bu kullanıcıların lisans durumlarını gösterir.

## <a name="see-also"></a>Ayrıca bkz.

[PowerShell ile Microsoft 365 erişimini devre dışı bırakma](disable-access-to-services-with-microsoft-365-powershell.md)

[PowerShell ile Sway erişimini devre dışı bırakma](disable-access-to-sway-with-microsoft-365-powershell.md)

[PowerShell Microsoft 365 hesaplarını, lisanslarını ve gruplarını yönetme](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)

[PowerShell Microsoft 365'i yönetme](manage-microsoft-365-with-microsoft-365-powershell.md)