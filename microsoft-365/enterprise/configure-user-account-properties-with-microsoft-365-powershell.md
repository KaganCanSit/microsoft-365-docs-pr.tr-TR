---
title: PowerShell Microsoft 365 hesabı özelliklerini yapılandırma
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
- O365ITProTrain
- Ent_Office_Other
- PowerShell
- admindeeplinkMAC
ms.assetid: 30813f8d-b08d-444b-98c1-53df7c29b4d7
description: Microsoft 365 kiracınıza tek tek veya birden çok kullanıcı hesabının özelliklerini yapılandırmak için Microsoft 365 kullanın.
ms.openlocfilehash: 01b17837e4babc31d385be66f9387129baf87da1
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62984494"
---
# <a name="configure-microsoft-365-user-account-properties-with-powershell"></a>PowerShell Microsoft 365 hesabı özelliklerini yapılandırma

*Bu makale hem son hem de Microsoft 365 Kurumsal hem de Office 365 Kurumsal.*

<a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 yönetim merkezi</a> kiracınıza kullanıcı hesaplarının özelliklerini yapılandırmak için Microsoft 365 kullanabilirsiniz. PowerShell'de bunu ve ayrıca yönetim merkezinde bazı diğer şeyleri de yapmaya devam edin.
  
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Graph modülü için Azure Active Directory PowerShell'i kullanma

Azure Active Directory Graph için PowerShell modülünde kullanıcı hesaplarının özelliklerini yapılandırmak için [**, Set-AzureADUser**](/powershell/module/azuread/set-azureaduser) cmdlet'ini kullanın ve ayar ya da değişiklik özelliklerini belirtin.

İlk olarak[, kiracınıza bağlan Microsoft 365 bağlanin](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).

### <a name="change-properties-for-a-specific-user-account"></a>Belirli bir kullanıcı hesabının özelliklerini değiştirme

Hesabı -ObjectID parametresiyle *tanımlayabilir ve ek* parametreler kullanarak belirli özellikleri değiştirebilir veya değiştirebilirsiniz. En yaygın parametrelerin listesi:
  
- -Department "\<department name>"

- -DisplayName "\<full user name>"

- -FacsimilieTelephoneNumber "\<fax number>"

- -GivenName "\<user first name>"

- -Surname "\<user last name>"

- -Mobile "\<mobile phone number>"

- -JobTitle "\<job title>"

- -PreferredLanguage "\<language>"

- -StreetAddress "\<street address>"

- -Şehir "\<city name>"

- -State "\<state name>"

- -PostalCode "\<postal code>"

- -Country "\<country name>"

- -TelephoneNumber "\<office phone number>"

- -UsageLocation "\<2-character country or region code>"

    Bu, ISO 3166-1 alfa-2 (A2) iki harfli ülke veya bölge kodudur.

Ek parametreler için bkz. [Set-AzureADUser](/powershell/module/azuread/set-azureaduser).

> [!NOTE]
> Kullanıcı hesabına lisans atamadan önce bir kullanım konumu atamanız gerekir.

Kullanıcı hesaplarınızı kullanıcı asıl adını görüntülemek için aşağıdaki komutu çalıştırın.
  
```powershell
Get-AzureADUser | Sort UserPrincipalName | Select UserPrincipalName | More
```

Bu komut PowerShell'e şunları sağlar:
  
1. Kullanıcı hesaplarından (**Get-AzureADUser**) tüm bilgileri edinin ve sonraki komuta () gönderin **|**.

1. Kullanıcı Asıl Adları listesini alfabetik olarak (**UserPrincipalName Sıralama) sırala** ve sonraki komuta () gönderin **|**.

1. Her hesap için yalnızca Kullanıcı Asıl Adı özelliğini görüntüleme (**UserPrincipalName öğesini seçin**).

1. Bunları bir defada bir ekran olarak görüntüleme (**Diğer).**

Bir hesabın görünen adına (ad ve soyadı) dayalı olarak Kullanıcı Asıl Adını görüntülemek için aşağıdaki komutları çalıştırın. Metin *$userName doldurun* ve karakterleri \< and > kaldırın:
  
```powershell
$userName="<Display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

Bu örnekte, Görüntü adı Sills olan kullanıcı hesabının Kullanıcı Asıl *Adı görüntülenir*.
  
```powershell
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

Hesap değişkeni *$upn* , tek tek hesaplarda görünen adlarına göre değişiklik yapabilirsiniz. Bu örnekte, *Beliya Newman'ın kullanım* konumu Fransa olarak ayarlandı. Ancak, kullanıcı Asıl Adı yerine görünen adını belirtir:
  
```powershell
$userName="Belinda Newman"
$upn=(Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-AzureADUser -ObjectID $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a>Tüm kullanıcı hesaplarının özelliklerini değiştirme

Tüm kullanıcıların özelliklerini değiştirmek için, **Get-AzureADUser** ve **Set-AzureADUser cmdlet'lerinin bir** bileşimini kullanabilirsiniz. Aşağıdaki örnekte, tüm kullanıcıların kullanım konumu Fransa olarak *değişir*:
  
```powershell
Get-AzureADUser | Set-AzureADUser -UsageLocation "FR"
```

Bu komut PowerShell'e şunları sağlar:
  
1. Kullanıcı hesaplarından (**Get-AzureADUser**) tüm bilgileri edinin ve sonraki komuta () gönderin **|**.

1. Kullanıcı konumunu Fransa olarak ayarlayın (**Set-AzureADUser -UsageLocation "FR"**).

### <a name="change-properties-for-a-specific-set-of-user-accounts"></a>Belirli bir kullanıcı hesabı kümesi için özellikleri değiştirme

Belirli bir kullanıcı hesabı kümesi özelliklerini değiştirmek için **, Get-AzureADUser, Where ve Set-AzureADUser** cmdlet'lerinin bir  bileşimini kullanabilirsiniz.  Aşağıdaki örnekte, Muhasebe departmanında yer alan tüm kullanıcıların kullanım konumu Fransa olarak *değişir*:
  
```powershell
Get-AzureADUser | Where {$_.Department -eq "Accounting"} | Set-AzureADUser -UsageLocation "FR"
```

Bu komut PowerShell'e şunları sağlar:
  
1. Kullanıcı hesaplarından (**Get-AzureADUser) tüm bilgileri edinin** ve sonraki komuta () gönderin **|**.

1.  Department özelliği "Accounting" olarak ayarlanmış olan tüm  kullanıcı hesaplarını bulun (**Where {$_. Department -eq "Accounting"}**) ve sonuçta elde edilen bilgileri sonraki komuta () gönderin **|**.

1. Kullanıcı konumunu Fransa olarak ayarlayın (**Set-AzureADUser -UsageLocation "FR"**).

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Kaynak için Microsoft Azure Active Directory Modülü'Windows PowerShell

Windows PowerShell için Microsoft Azure Active Directory Modülü ile kullanıcı hesaplarının özelliklerini yapılandırmak için **, Set-MsolUser** cmdlet'ini kullanın ve ayarlamak veya değiştirmek için özellikleri belirtin.

İlk olarak[, kiracınıza bağlan Microsoft 365 bağlanin](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).
  
> [!NOTE]
> PowerShell Core, adı *Msol* olan Microsoft Azure Active Directory Modülü Windows PowerShell cmdlet'leri desteklemez. Bu cmdlet'leri çalışma Windows PowerShell.

### <a name="change-properties-for-a-specific-user-account"></a>Belirli bir kullanıcı hesabının özelliklerini değiştirme

Belirli bir kullanıcı hesabının özelliklerini yapılandırmak için [**, Set-MsolUser**](/previous-versions/azure/dn194136(v=azure.100)) cmdlet'ini kullanın ve ayar değişecek özellikleri belirtin. 

Hesabı - *UserPrincipalName parametresiyle* tanımlayabilir ve ek parametreler kullanarak belirli özellikleri değiştirebilirsiniz. En yaygın parametrelerin listesi:
  
- -Şehir "\<city name>"

- -Country "\<country name>"

- -Department "\<department name>"

- -DisplayName "\<full user name>"

- -Faks "\<fax number>"

- -Ad "\<user first name>"

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

    Bu, ISO 3166-1 alfa-2 (A2) iki harfli ülke veya bölge kodudur.

Ek parametreler için bkz. [Set-MsolUser](/previous-versions/azure/dn194136(v=azure.100)).

Tüm kullanıcılarının Kullanıcı Asıl Adlarını görmek için aşağıdaki komutu çalıştırın:
  
```powershell
Get-MSolUser | Sort UserPrincipalName | Select UserPrincipalName | More
```

Bu komut PowerShell'e şunları sağlar:
  
1. Kullanıcı hesaplarıyla (**Get-MsolUser) ilgili tüm bilgileri alır** ve bir sonraki komuta () gönderir **|**.

1. Kullanıcı Asıl Adları listesini alfabetik olarak (**UserPrincipalName Sıralama) sırala** ve sonraki komuta () gönderin **|**.

1. Her hesap için yalnızca Kullanıcı Asıl Adı özelliğini görüntüleme (**UserPrincipalName öğesini seçin**).

1. Bunları bir defada bir ekran olarak görüntüleme (**Diğer).**

Bir hesabın görünen adına (ad ve soyadı) dayalı olarak Kullanıcı Asıl Adını görüntülemek için aşağıdaki komutları çalıştırın. Metin *$userName doldurun* ve karakterleri \< and > kaldırın.
  
```powershell
$userName="<Display name>"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

Bu örnekte, Sills adlı kullanıcının Kullanıcı Asıl Adı görüntülenir:
  
```powershell
$userName="Caleb Sills"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

Hesap değişkeni *$upn* , tek tek hesaplarda görünen adlarına göre değişiklik yapabilirsiniz. Bu örnekte, *Beliya Newman'ın* kullanım konumu Fransa olarak ayarlandı *ancak Kullanıcı* Asıl Adı yerine görünen adı gösterilir:
  
```powershell
$userName="<display name>"
$upn=(Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-MsolUser -UserPrincipalName $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a>Tüm kullanıcı hesaplarının özelliklerini değiştirme

Tüm kullanıcıların özelliklerini değiştirmek için, **Get-MsolUser ve Set-MsolUser** **cmdlet'lerinin** bir bileşimini kullanın. Aşağıdaki örnekte, tüm kullanıcıların kullanım konumu Fransa olarak *değişir*:
  
```powershell
Get-MsolUser | Set-MsolUser -UsageLocation "FR"
```

Bu komut PowerShell'e şunları sağlar:
  
1. Kullanıcı hesaplarının (**Get-MsolUser) tüm bilgilerini alır** ve bir sonraki komuta () gönderir **|**.

1. Kullanıcı konumunu Fransa olarak ayarlayın (**Set-MsolUser -UsageLocation "FR"**).

### <a name="change-properties-for-a-specific-set-of-user-accounts"></a>Belirli bir kullanıcı hesabı kümesi için özellikleri değiştirme

Belirli bir kullanıcı hesabı kümesiyle ilgili özellikleri değiştirmek için **, Get-MsolUser**, **Where** ve **Set-MsolUser** cmdlet'lerinin bir bileşimini kullanabilirsiniz. Aşağıdaki örnekte, Muhasebe departmanında yer alan tüm kullanıcıların kullanım konumu Fransa olarak *değişir*:
  
```powershell
Get-MsolUser | Where {$_.Department -eq "Accounting"} | Set-MsolUser -UsageLocation "FR"
```

Bu komut PowerShell'e şunları sağlar:
  
1. Kullanıcı hesaplarının (**Get-MsolUser) tüm bilgilerini alır** ve bir sonraki komuta () gönderir **|**.

1. Department özelliği "Accounting" olarak *ayarlanmış olan tüm* kullanıcı hesaplarını bulun (**Where {$_. Department -eq "Accounting"}**) ve sonuç bilgilerini sonraki komuta () gönderin **|**.

1. Kullanıcı konumunu Fransa olarak ayarlayın (**Set-MsolUser -UsageLocation "FR"**).

## <a name="see-also"></a>Ayrıca bkz.

[PowerShell Microsoft 365 hesaplarını, lisanslarını ve gruplarını yönetme](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
  
[PowerShell Microsoft 365'i yönetme](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[Microsoft 365 için PowerShell'i Microsoft 365](getting-started-with-microsoft-365-powershell.md)
