---
title: PowerShell ile Microsoft 365 kullanıcı hesabı özelliklerini yapılandırma
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
- O365ITProTrain
- Ent_Office_Other
- PowerShell
- admindeeplinkMAC
ms.assetid: 30813f8d-b08d-444b-98c1-53df7c29b4d7
description: Microsoft 365 kiracınızdaki tek veya birden çok kullanıcı hesabının özelliklerini yapılandırmak için Microsoft 365 için PowerShell kullanın.
ms.openlocfilehash: 3a1aa77a6af3995d7cd4d072b6b6c6047bf89942
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65091357"
---
# <a name="configure-microsoft-365-user-account-properties-with-powershell"></a>PowerShell ile Microsoft 365 kullanıcı hesabı özelliklerini yapılandırma

*Bu makale hem Microsoft 365 Kurumsal hem de Office 365 Kurumsal için geçerlidir.*

<a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365</a> kiracınızın kullanıcı hesaplarının özelliklerini yapılandırmak için Microsoft 365 yönetim merkezi kullanabilirsiniz. PowerShell'de bunu ve yönetim merkezinde gerçekleştiremezseniz yapabileceğiniz diğer bazı şeyleri de yapabilirsiniz.
  
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Graph için Azure Active Directory PowerShell modülünü kullanma

Graph için Azure Active Directory PowerShell modülünde kullanıcı hesaplarının özelliklerini yapılandırmak için [**Set-AzureADUser**](/powershell/module/azuread/set-azureaduser) cmdlet'ini kullanın ve ayarlayıp değiştirecek özellikleri belirtin.

İlk olarak [Microsoft 365 kiracınıza bağlanın](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).

### <a name="change-properties-for-a-specific-user-account"></a>Belirli bir kullanıcı hesabının özelliklerini değiştirme

*Hesabı -ObjectID* parametresiyle tanımlar ve ek parametreler kullanarak belirli özellikleri ayarlar veya değiştirirsiniz. En yaygın parametrelerin listesi aşağıdadır:
  
- -Departman "\<department name>"

- -DisplayName "\<full user name>"

- -FacsimilieTelephoneNumber "\<fax number>"

- -GivenName "\<user first name>"

- -Soyadı "\<user last name>"

- -Mobil "\<mobile phone number>"

- -JobTitle "\<job title>"

- -PreferredLanguage "\<language>"

- -StreetAddress "\<street address>"

- -Şehir "\<city name>"

- -State "\<state name>"

- -PostalCode "\<postal code>"

- -Ülke "\<country name>"

- -TelephoneNumber "\<office phone number>"

- -UsageLocation "\<2-character country or region code>"

    Bu ISO 3166-1 alfa-2 (A2) iki harfli ülke veya bölge kodudur.

Ek parametreler için bkz. [Set-AzureADUser](/powershell/module/azuread/set-azureaduser).

> [!NOTE]
> Kullanıcı hesabına lisans atayabilmeniz için önce bir kullanım konumu atamanız gerekir.

Kullanıcı hesaplarınızın Kullanıcı Asıl Adını görüntülemek için aşağıdaki komutu çalıştırın.
  
```powershell
Get-AzureADUser | Sort UserPrincipalName | Select UserPrincipalName | More
```

Bu komut PowerShell'e şunları yönerge eder:
  
1. Kullanıcı hesaplarıyla ilgili tüm bilgileri (**Get-AzureADUser**) alın ve sonraki komuta (**|**) gönderin.

1. Kullanıcı Asıl Adları listesini alfabetik olarak sıralayın (**UserPrincipalName Sırala**) ve sonraki komuta (**|**) gönderin.

1. Her hesap için yalnızca Kullanıcı Asıl Adı özelliğini görüntüleyin (**UserPrincipalName'i seçin**).

1. Bunları bir kerede bir ekran görüntüleme (**Diğer**).

Bir hesabın görünen adına (ad ve soyadı) göre Kullanıcı Asıl Adı'nı görüntülemek için aşağıdaki komutları çalıştırın. *$userName* değişkenini doldurun ve karakterleri kaldırın\< and >:
  
```powershell
$userName="<Display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

Bu örnekte *, görünen adı Caleb Sills* olan kullanıcı hesabının Kullanıcı Asıl Adı görüntülenir.
  
```powershell
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

*$upn* değişkeni kullanarak, tek tek hesaplarda görünen adlarına göre değişiklik yapabilirsiniz. *Burada, Belinda Newman'ın* kullanım konumunu Fransa olarak ayarlayan bir örnek verilmiştir. Ancak Kullanıcı Asıl Adı yerine görünen adını belirtir:
  
```powershell
$userName="Belinda Newman"
$upn=(Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-AzureADUser -ObjectID $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a>Tüm kullanıcı hesaplarının özelliklerini değiştirme

Tüm kullanıcıların özelliklerini değiştirmek için **Get-AzureADUser** ve **Set-AzureADUser** cmdlet'lerinin bir bileşimini kullanabilirsiniz. Aşağıdaki örnek, tüm kullanıcıların kullanım konumunu *Fransa* olarak değiştirir:
  
```powershell
Get-AzureADUser | Set-AzureADUser -UsageLocation "FR"
```

Bu komut PowerShell'e şunları yönerge eder:
  
1. Kullanıcı hesaplarıyla ilgili tüm bilgileri alın (**Get-AzureADUser**) ve sonraki komuta (**|**) gönderin.

1. Kullanıcı konumunu Fransa olarak ayarlayın (**Set-AzureADUser -UsageLocation "FR"**).

### <a name="change-properties-for-a-specific-set-of-user-accounts"></a>Belirli bir kullanıcı hesabı kümesinin özelliklerini değiştirme

Belirli bir kullanıcı hesabı kümesinin özelliklerini değiştirmek için **Get-AzureADUser**, **Where** ve **Set-AzureADUser** cmdlet'lerinin bir bileşimini kullanabilirsiniz. Aşağıdaki örnek, Muhasebe departmanındaki tüm kullanıcıların kullanım konumunu *Fransa* olarak değiştirir:
  
```powershell
Get-AzureADUser | Where {$_.Department -eq "Accounting"} | Set-AzureADUser -UsageLocation "FR"
```

Bu komut PowerShell'e şunları yönerge eder:
  
1. Kullanıcı hesaplarıyla ilgili tüm bilgileri alın (**Get-AzureADUser**) ve sonraki komuta (**|** gönderin).

1.  *Department* özelliği "Accounting" (**Burada {$_) olarak ayarlanmış tüm kullanıcı hesaplarını bulun. Department -eq "Accounting"}**) ve elde edilen bilgileri bir sonraki komuta (**|**) gönderin.

1. Kullanıcı konumunu Fransa olarak ayarlayın (**Set-AzureADUser -UsageLocation "FR"**).

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Windows PowerShell için Microsoft Azure Active Directory Modülünü kullanma

Windows PowerShell için Microsoft Azure Active Directory Modülü ile kullanıcı hesaplarının özelliklerini yapılandırmak için **Set-MsolUser** cmdlet'ini kullanın ve ayarlayıp değiştirecek özellikleri belirtin.

İlk olarak [Microsoft 365 kiracınıza bağlanın](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).
  
> [!NOTE]
> PowerShell Core, Windows PowerShell modülü için Microsoft Azure Active Directory Modülünü ve adında *Msol* bulunan cmdlet'leri desteklemez. Bu cmdlet'leri Windows PowerShell çalıştırın.

### <a name="change-properties-for-a-specific-user-account"></a>Belirli bir kullanıcı hesabının özelliklerini değiştirme

Belirli bir kullanıcı hesabının özelliklerini yapılandırmak için [**Set-MsolUser**](/previous-versions/azure/dn194136(v=azure.100)) cmdlet'ini kullanın ve ayarlanacağı veya değiştirileceğini belirtin. 

*-UserPrincipalName* parametresiyle hesabı tanımlar ve ek parametreler kullanarak belirli özellikleri ayarlar veya değiştirirsiniz. En yaygın parametrelerin listesi aşağıdadır.
  
- -Şehir "\<city name>"

- -Ülke "\<country name>"

- -Departman "\<department name>"

- -DisplayName "\<full user name>"

- -Faks "\<fax number>"

- -FirstName "\<user first name>"

- -Soyadı "\<user last name>"

- -MobilePhone "\<mobile phone number>"

- -Office "\<office location>"

- -PhoneNumber "\<office phone number>"

- -PostalCode "\<postal code>"

- -PreferredLanguage "\<language>"

- -State "\<state name>"

- -StreetAddress "\<street address>"

- -Başlık "\<title name>"

- -UsageLocation "\<2-character country or region code>"

    Bu ISO 3166-1 alfa-2 (A2) iki harfli ülke veya bölge kodudur.

Ek parametreler için bkz. [Set-MsolUser](/previous-versions/azure/dn194136(v=azure.100)).

Tüm kullanıcılarınızın Kullanıcı Asıl Adlarını görmek için aşağıdaki komutu çalıştırın:
  
```powershell
Get-MSolUser | Sort UserPrincipalName | Select UserPrincipalName | More
```

Bu komut PowerShell'e şunları yönerge eder:
  
1. Kullanıcı hesaplarıyla ilgili tüm bilgileri alın (**Get-MsolUser**) ve sonraki komuta (**|**) gönderin.

1. Kullanıcı Asıl Adları listesini alfabetik olarak sıralayın (**UserPrincipalName Sırala**) ve sonraki komuta (**|**) gönderin.

1. Her hesap için yalnızca Kullanıcı Asıl Adı özelliğini görüntüleyin (**UserPrincipalName'i seçin**).

1. Bunları bir kerede bir ekran görüntüleme (**Diğer**).

Bir hesabın görünen adına (ad ve soyadı) göre Kullanıcı Asıl Adı'nı görüntülemek için aşağıdaki komutları çalıştırın. *$userName* değişkenini doldurun ve karakterleri kaldırın\< and >.
  
```powershell
$userName="<Display name>"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

Bu örnekte, Caleb Sills adlı kullanıcının Kullanıcı Asıl Adı görüntülenir:
  
```powershell
$userName="Caleb Sills"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

*$upn* değişkeni kullanarak, tek tek hesaplarda görünen adlarına göre değişiklik yapabilirsiniz. *Aşağıda, Belinda Newman'ın* kullanım konumunu *Fransa* olarak ayarlayan ancak Kullanıcı Asıl Adı yerine görünen adını belirten bir örnek verilmiştir:
  
```powershell
$userName="<display name>"
$upn=(Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-MsolUser -UserPrincipalName $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a>Tüm kullanıcı hesaplarının özelliklerini değiştirme

Tüm kullanıcıların özelliklerini değiştirmek için **Get-MsolUser** ve **Set-MsolUser** cmdlet'lerinin bir bileşimini kullanın. Aşağıdaki örnek, tüm kullanıcıların kullanım konumunu *Fransa* olarak değiştirir:
  
```powershell
Get-MsolUser | Set-MsolUser -UsageLocation "FR"
```

Bu komut PowerShell'e şunları yönerge eder:
  
1. Kullanıcı hesapları (**Get-MsolUser**) için tüm bilgileri alın ve sonraki komuta (**|**) gönderin.

1. Kullanıcı konumunu Fransa olarak ayarlayın (**Set-MsolUser -UsageLocation "FR"**).

### <a name="change-properties-for-a-specific-set-of-user-accounts"></a>Belirli bir kullanıcı hesabı kümesinin özelliklerini değiştirme

Belirli bir kullanıcı hesabı kümesinin özelliklerini değiştirmek için **Get-MsolUser**, **Where** ve **Set-MsolUser** cmdlet'lerinin bir bileşimini kullanabilirsiniz. Aşağıdaki örnek, Muhasebe departmanındaki tüm kullanıcıların kullanım konumunu *Fransa* olarak değiştirir:
  
```powershell
Get-MsolUser | Where {$_.Department -eq "Accounting"} | Set-MsolUser -UsageLocation "FR"
```

Bu komut PowerShell'e şunları yönerge eder:
  
1. Kullanıcı hesapları (**Get-MsolUser**) için tüm bilgileri alın ve sonraki komuta (**|**) gönderin.

1. *Department* özelliği "Accounting" (**Burada {$_) olarak ayarlanmış tüm kullanıcı hesaplarını bulun. Department -eq "Accounting"}**) ve elde edilen bilgileri sonraki komuta (**|**) gönderin.

1. Kullanıcı konumunu Fransa olarak ayarlayın (**Set-MsolUser -UsageLocation "FR"**).

## <a name="see-also"></a>Ayrıca bkz.

[PowerShell ile Microsoft 365 kullanıcı hesaplarını, lisanslarını ve gruplarını yönetme](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
  
[PowerShell ile Microsoft 365’i yönetme](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[Microsoft 365 için PowerShell ile Kullanmaya başlayın](getting-started-with-microsoft-365-powershell.md)
