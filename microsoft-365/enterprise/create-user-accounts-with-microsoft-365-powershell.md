---
title: PowerShell Microsoft 365 hesapları oluşturma
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: PowerShell kullanarak tek tek veya birden çok Microsoft 365 hesapları oluşturma.
ms.openlocfilehash: 7396e98e597491910b639e5a0d0c57b8f685bc02
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62985554"
---
# <a name="create-microsoft-365-user-accounts-with-powershell"></a>PowerShell Microsoft 365 hesapları oluşturma

*Bu makale hem son hem de Microsoft 365 Kurumsal hem de Office 365 Kurumsal.*

Birden çok hesap gibi kullanıcı hesaplarını Microsoft 365 için PowerShell for Microsoft 365'i kullanabilirsiniz.

PowerShell'de kullanıcı hesapları sanız, bazı hesap özellikleri her zaman gereklidir. Diğer özellikler gerekli değildir, ancak önemlidir. Aşağıdaki tabloya bakın.
  
|**Özellik adı**|**Gerekli mi?**|**Açıklama**|
|:-----|:-----|:-----|
|**DisplayName** <br/> |Evet  <br/> |Bu, diğer hizmetlerde kullanılan görünen Microsoft 365. Örneğin, *Sil silleri*. <br/> |
|**UserPrincipalName** <br/> |Evet  <br/> |Bu, hizmetlerde oturum a açmada kullanılan hesap Microsoft 365 adıdır. Örneğin, *Çok contoso.onmicrosoft.com\@*.  <br/> |
|**Ad** <br/> |Hayır  <br/> ||
|**Soyadı** <br/> |Hayır  <br/> ||
|**LicenseAssignment** <br/> |Hayır  <br/> |Bu, kullanıcı hesabına kullanılabilir bir lisansın atandığı lisans planıdır (lisans planı veya SKU olarak da bilinir). Lisans, Microsoft 365 kullanılabilen kullanıcı hizmetlerini tanımlar. Hesabı yken kullanıcıya lisans atamanız gerekmektedir, ancak bu hesabın kullanıcı hizmetleri için erişim lisansı olması Microsoft 365 gerekir. Oluşturduk sonra kullanıcı hesabına lisans oluşturmak için 30 gün süreniz vardır. |
|**Password** <br/> |Hayır  <br/> | Bir parola belirtmezseniz, kullanıcı hesabına rastgele bir parola atanır ve komutun sonuçlarında parola görünür. Parola belirtirseniz, aşağıdaki türlerde 8 - 16 ASCII metin karakteri olması gerekir: küçük harfler, büyük harfler, sayılar ve simgeler.<br/> |
|**UsageLocation** <br/> |Hayır  <br/> |Bu geçerli bir ISO 3166-1 alfa-2 ülke kodudur. Örneğin, *ABD* için US ve *Fransa için FR* . Bu değeri sağlamak önemlidir, çünkü bazı Microsoft 365 hizmetleri bazı ülkelerde sağlanıyor değildir. Hesap bu değeri yapılandırmadığınız sürece kullanıcı hesabına lisans atayabilirsiniz. Daha fazla bilgi için bkz [. Lisans kısıtlamaları hakkında](https://go.microsoft.com/fwlink/p/?LinkId=691730).<br/> |

>[!Note]
>[Kullanıcı hesaplarını oluşturmak için aşağıdaki bilgileri](../admin/add-users/add-users.md) Microsoft 365 yönetim merkezi.
> 
> Ek kaynakların listesi için bkz. [Kullanıcıları ve grupları yönetme](/admin).
>   

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Graph modülü için Azure Active Directory PowerShell'i kullanma

İlk olarak[, kiracınıza bağlan Microsoft 365 bağlanin](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).

Bağlandikten sonra, tek bir hesap oluşturmak için aşağıdaki söz dizimi kullanın:
  
```powershell
$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password="<user account password>"
New-AzureADUser -DisplayName "<display name>" -GivenName "<first name>" -SurName "<last name>" -UserPrincipalName <sign-in name> -UsageLocation <ISO 3166-1 alpha-2 country code> -MailNickName <mailbox name> -PasswordProfile $PasswordProfile -AccountEnabled $true
```

Bu örnek, ABD kullanıcısı *Olan Sills için bir hesap oluşturur*:
  
```powershell
$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password="3Rv0y1q39/chsy"
New-AzureADUser -DisplayName "Caleb Sills" -GivenName "Caleb" -SurName "Sills" -UserPrincipalName calebs@contoso.onmicrosoft.com -UsageLocation US -MailNickName calebs -PasswordProfile $PasswordProfile -AccountEnabled $true
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Kaynak için Microsoft Azure Active Directory Modülü'Windows PowerShell

İlk olarak[, kiracınıza bağlan Microsoft 365 bağlanin](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

### <a name="create-an-individual-user-account"></a>Tek bir kullanıcı hesabı oluşturma

Tek bir hesap oluşturmak için aşağıdaki söz dizimlerini kullanın:
  
```powershell
New-MsolUser -DisplayName <display name> -FirstName <first name> -LastName <last name> -UserPrincipalName <sign-in name> -UsageLocation <ISO 3166-1 alpha-2 country code> -LicenseAssignment <licensing plan name> [-Password <Password>]
```

>[!Note]
>PowerShell Core, *Msol'Microsoft Azure Active Directory Msol* Windows PowerShell cmdlet'ler için Modülünü desteklemez. Bu cmdlet'leri çalışma Windows PowerShell.
>

Kullanılabilir lisans planı adlarını listeleyebilirsiniz, şu komutu kullanın:

````powershell
Get-MsolAccountSku
````

Bu örnek, ABD kullanıcısı *Olan Sills*`contoso:ENTERPRISEPACK` için bir hesap oluşturur ve (Office 365 Kurumsal E3) lisans planından bir lisans atar.
  
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
   >CSV dosyasının ilk sütunundaki sütun adları ve bunların sırası rastgeledir. Ancak, dosyanın geri kalanındaki verilerin sıralarının sütun adlarının sırasıyla eş olduğundan emin olun. Ve bu parametre için PowerShell komutunda parametre değerleri için sütun Microsoft 365 kullanın.
    
2. Aşağıdaki sözdizimini kullanın:
    
    ```powershell
     Import-Csv -Path <Input CSV File Path and Name> | foreach {New-MsolUser -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -UserPrincipalName $_.UserPrincipalName -UsageLocation $_.UsageLocation -LicenseAssignment $_.AccountSkuId [-Password $_.Password]} | Export-Csv -Path <Output CSV File Path and Name>
    ```

   Bu örnek, *C:\* Documents\NewAccounts.csvdosyasından kullanıcı hesapları oluşturur ve *C:\My Documents\NewAccountResults.csvadlı bir dosyada sonuçları günlüğe Documents\NewAccountResults.csv*.
    
    ```powershell
    Import-Csv -Path "C:\My Documents\NewAccounts.csv" | foreach {New-MsolUser -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -UserPrincipalName $_.UserPrincipalName -UsageLocation $_.UsageLocation -LicenseAssignment $_.AccountSkuId} | Export-Csv -Path "C:\My Documents\NewAccountResults.csv"
    ```

3. Sonuçları görmek için çıkış dosyasını gözden geçirebilirsiniz. Parolaları belirtmedik, dolayısıyla oluşturulan Microsoft 365 rastgele parolalar çıkış dosyasında görünür durumda olur.
    
## <a name="see-also"></a>Ayrıca bkz.

[PowerShell Microsoft 365 hesaplarını, lisanslarını ve gruplarını yönetme](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
  
[PowerShell Microsoft 365'i yönetme](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[Microsoft 365 için PowerShell ile çalışmaya Microsoft 365](getting-started-with-microsoft-365-powershell.md)