---
title: PowerShell ile Microsoft 365 kullanıcı hesapları oluşturma
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
- O365ITProTrain
- seo-marvel-apr2020
ms.assetid: 6770c5fa-b886-4512-8c67-ffd53226589e
description: PowerShell'i kullanarak bireysel veya birden çok Microsoft 365 kullanıcı hesabı oluşturma.
ms.openlocfilehash: 9f96c5a96e014055622deb34c37cb8523f0041f8
ms.sourcegitcommit: a5e75d7f7651313818bd2de292d5c38b290d8975
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/07/2022
ms.locfileid: "65930251"
---
# <a name="create-microsoft-365-user-accounts-with-powershell"></a>PowerShell ile Microsoft 365 kullanıcı hesapları oluşturma

*Bu makale hem Microsoft 365 Kurumsal hem de Office 365 Kurumsal için geçerlidir.*

Birden çok hesap dahil olmak üzere kullanıcı hesaplarını verimli bir şekilde oluşturmak için Microsoft 365 için PowerShell'i kullanabilirsiniz.

PowerShell'de kullanıcı hesapları oluşturduğunuzda, belirli hesap özellikleri her zaman gereklidir. Diğer özellikler gerekli değildir ancak önemlidir. Aşağıdaki tabloya bakın.
  
|**Özellik adı**|**Gerekli mi?**|**Açıklama**|
|:-----|:-----|:-----|
|**Displayname** <br/> |Evet  <br/> |Bu, Microsoft 365 hizmetlerinde kullanılan görünen addır. Örneğin, *Caleb Sills*. <br/> |
|**Userprincipalname** <br/> |Evet  <br/> |Bu, Microsoft 365 hizmetlerinde oturum açmak için kullanılan hesap adıdır. Örneğin *, CalebS\@contoso.onmicrosoft.com*.  <br/> |
|**Ad** <br/> |Hayır  <br/> ||
|**Soyadı** <br/> |Hayır  <br/> ||
|**LicenseAssignment** <br/> |Hayır  <br/> |Bu, kullanıcı hesabına kullanılabilir bir lisansın atandığı lisans [planıdır (lisans planı veya SKU](/azure/active-directory/enterprise-users/licensing-service-plan-reference) olarak da bilinir). Lisans, hesaba sağlanan Microsoft 365 hizmetlerini tanımlar. Hesabı oluştururken kullanıcıya lisans atamanız gerekmez, ancak hesabın Microsoft 365 hizmetlerine erişmek için bir lisansı olmalıdır. Kullanıcı hesabını oluşturduktan sonra lisans vermek için 30 gününüz vardır. |
|**Password** <br/> |Hayır  <br/> | Parola belirtmezseniz kullanıcı hesabına rastgele bir parola atanır ve parola komutun sonuçlarında görünür. Parola belirtirseniz, şu türlerde 8 ile 16 ASCII metin karakteri olmalıdır: küçük harfler, büyük harfler, sayılar ve simgeler.<br/> |
|**UsageLocation** <br/> |Hayır  <br/> |Bu geçerli bir ISO 3166-1 alfa-2 ülke kodudur. Örneğin, *ABD için ABD* ve Fransa için *FR* . Bazı Microsoft 365 hizmetleri belirli ülkelerde kullanılamadığından bu değeri sağlamak önemlidir. Hesapta bu değer yapılandırılmadığı sürece kullanıcı hesabına lisans atayamazsınız. Daha fazla bilgi için bkz. [Lisans kısıtlamaları hakkında](https://go.microsoft.com/fwlink/p/?LinkId=691730).<br/> |

>[!Note]
>Microsoft 365 yönetim [merkezini kullanarak kullanıcı hesapları oluşturmayı öğrenin](../admin/add-users/add-users.md).
> 
> Ek kaynakların listesi için bkz. [Kullanıcıları ve grupları yönetme](/admin).
>   

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Graph için Azure Active Directory PowerShell modülünü kullanma

İlk olarak [Microsoft 365 kiracınıza bağlanın](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).

Bağlandıktan sonra, tek bir hesap oluşturmak için aşağıdaki söz dizimini kullanın:
  
```powershell
$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password="<user account password>"
New-AzureADUser -DisplayName "<display name>" -GivenName "<first name>" -SurName "<last name>" -UserPrincipalName <sign-in name> -UsageLocation <ISO 3166-1 alpha-2 country code> -MailNickName <mailbox name> -PasswordProfile $PasswordProfile -AccountEnabled $true
```

Bu örnek, ABD'de *Caleb Sills* kullanıcısı için bir hesap oluşturur:
  
```powershell
$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password="3Rv0y1q39/chsy"
New-AzureADUser -DisplayName "Caleb Sills" -GivenName "Caleb" -SurName "Sills" -UserPrincipalName calebs@contoso.onmicrosoft.com -UsageLocation US -MailNickName calebs -PasswordProfile $PasswordProfile -AccountEnabled $true
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Windows PowerShell için Microsoft Azure Active Directory Modülünü kullanma

İlk olarak [Microsoft 365 kiracınıza bağlanın](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

### <a name="create-an-individual-user-account"></a>Tek bir kullanıcı hesabı oluşturma

Tek bir hesap oluşturmak için aşağıdaki söz dizimini kullanın:
  
```powershell
New-MsolUser -DisplayName <display name> -FirstName <first name> -LastName <last name> -UserPrincipalName <sign-in name> -UsageLocation <ISO 3166-1 alpha-2 country code> -LicenseAssignment <licensing plan name> [-Password <Password>]
```

>[!Note]
>PowerShell Core, Windows PowerShell modülü ve adında *Msol* bulunan cmdlet'ler için Microsoft Azure Active Directory Modülünü desteklemez. Bu cmdlet'leri Windows PowerShell'den çalıştırın.
>

Kullanılabilir [lisans planı adlarını](/azure/active-directory/enterprise-users/licensing-service-plan-reference) listelemek için şu komutu kullanın:

````powershell
Get-MsolAccountSku
````

Bu örnek, ABD kullanıcısı *Caleb Sills* için bir hesap oluşturur ve (Office 365 Kurumsal E3) lisans planından `contoso:ENTERPRISEPACK` bir lisans atar.
  
```powershell
New-MsolUser -DisplayName "Caleb Sills" -FirstName Caleb -LastName Sills -UserPrincipalName calebs@contoso.onmicrosoft.com -UsageLocation US -LicenseAssignment contoso:ENTERPRISEPACK
```

### <a name="create-multiple-user-accounts"></a>Birden çok kullanıcı hesabı oluşturma

1. Gerekli kullanıcı hesabı bilgilerini içeren bir virgülle ayrılmış değer (CSV) dosyası oluşturun. Örneğin:

     ```powershell
     UserPrincipalName,FirstName,LastName,DisplayName,UsageLocation,AccountSkuId
     ClaudeL@contoso.onmicrosoft.com,Claude,Loiselle,Claude Loiselle,US,contoso:ENTERPRISEPACK
     LynneB@contoso.onmicrosoft.com,Lynne,Baxter,Lynne Baxter,US,contoso:ENTERPRISEPACK
     ShawnM@contoso.onmicrosoft.com,Shawn,Melendez,Shawn Melendez,US,contoso:ENTERPRISEPACK
     ```

   >[!NOTE]
   >CSV dosyasının ilk satırındaki sütun adları ve sıraları rastgeledir. Ancak, dosyanın geri kalanındaki verilerin sırasının sütun adlarının sırasıyla eşleştiğinden emin olun. Ayrıca Microsoft 365 için PowerShell komutundaki parametre değerlerinin sütun adlarını kullanın.
    
2. Aşağıdaki sözdizimini kullanın:
    
    ```powershell
     Import-Csv -Path <Input CSV File Path and Name> | foreach {New-MsolUser -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -UserPrincipalName $_.UserPrincipalName -UsageLocation $_.UsageLocation -LicenseAssignment $_.AccountSkuId [-Password $_.Password]} | Export-Csv -Path <Output CSV File Path and Name>
    ```

   Bu örnek *, C:\My Documents\NewAccounts.csv* dosyasından kullanıcı hesapları oluşturur ve sonuçları *C:\My Documents\NewAccountResults.csv* adlı bir dosyada günlüğe kaydeder.
    
    ```powershell
    Import-Csv -Path "C:\My Documents\NewAccounts.csv" | foreach {New-MsolUser -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -UserPrincipalName $_.UserPrincipalName -UsageLocation $_.UsageLocation -LicenseAssignment $_.AccountSkuId} | Export-Csv -Path "C:\My Documents\NewAccountResults.csv"
    ```

3. Sonuçları görmek için çıkış dosyasını gözden geçirin. Parola belirtmediğimiz için Microsoft 365'in oluşturduğu rastgele parolalar çıkış dosyasında görünür.
    
## <a name="see-also"></a>Ayrıca bkz.

[PowerShell ile Microsoft 365 kullanıcı hesaplarını, lisanslarını ve gruplarını yönetme](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
  
[PowerShell ile Microsoft 365’i yönetme](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[Microsoft 365 için PowerShell'i kullanmaya başlama](getting-started-with-microsoft-365-powershell.md)
