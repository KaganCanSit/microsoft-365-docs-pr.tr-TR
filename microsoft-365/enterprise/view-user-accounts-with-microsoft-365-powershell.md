---
title: PowerShell ile Microsoft 365 kullanıcı hesaplarını görüntüleme
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 07/17/2020
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
- LIL_Placement
- PowerShell
- Ent_Office_Other
- seo-marvel-apr2020
ms.assetid: bb12f49d-a85d-4f3b-ada2-5c4e33977b10
description: PowerShell ile Microsoft 365 kullanıcı hesaplarınızı farklı şekillerde görüntülemeyi, listelemeyi veya görüntülemeyi öğrenin.
ms.openlocfilehash: cbbb188c50e4d163d5ef4226a83968c64e8a260c
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65090739"
---
# <a name="view-microsoft-365-user-accounts-with-powershell"></a>PowerShell ile Microsoft 365 kullanıcı hesaplarını görüntüleme

*Bu makale hem Microsoft 365 Kurumsal hem de Office 365 Kurumsal için geçerlidir.*

Microsoft 365 kiracınızın hesaplarını görüntülemek için Microsoft 365 yönetim merkezi kullanabilirsiniz. Microsoft 365 için PowerShell bunu etkinleştirir ancak ek işlevler de sağlar.
  
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Graph için Azure Active Directory PowerShell modülünü kullanma

İlk olarak [Microsoft 365 kiracınıza bağlanın](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
  
### <a name="view-all-accounts"></a>Tüm hesapları görüntüleme

Kullanıcı hesaplarının tam listesini görüntülemek için şu komutu çalıştırın:
  
```powershell
Get-AzureADUser
```

Şuna benzer bilgiler almalısınız:
  
```powershell
ObjectId                             DisplayName                                           UserPrincipalName
--------                             -----------                                           -----------------
032fc1fc-b5a2-46f1-8635-3d7dcb52c48d Adele Vance                                           AdeleV@litwareinc.OnMicr...
bd1e6af1-41e7-4f77-a2ac-5b209950135c Global Administrator                                  admin@litwareinc.onmicro...
ec37a4d6-232e-4eb7-82a5-1613490642a5 Alex Wilber                                           AlexW@litwareinc.OnMicro...
be4bdddd-c790-424c-9f96-a0cf609b7815 Allan Deyoung                                         AllanD@litwareinc.OnMicr...
598ab87b-76f0-4bf9-9538-bd46b10f4438 Christie Cline                                        ChristieC@litwareinc.OnM...
40722671-e520-4a5f-97d4-0bc9e9b2dc0f Debra Berger                                          DebraB@litwareinc.OnMicr...
```

### <a name="view-a-specific-account"></a>Belirli bir hesabı görüntüleme

Belirli bir kullanıcı hesabını görüntülemek için aşağıdaki komutu çalıştırın. Kullanıcı hesabının oturum açma hesabı adını (kullanıcı asıl adı (UPN) olarak da bilinir) doldurun. "<" ve ">" karakterlerini kaldırın.
  
```powershell
Get-AzureADUser -ObjectID <sign-in name of the user account>
```

İşte bir örnek:
  
```powershell
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com
```

### <a name="view-additional-property-values-for-a-specific-account"></a>Belirli bir hesap için ek özellik değerlerini görüntüleme

Varsayılan olarak, **Get-AzureADUser** cmdlet'i hesapların yalnızca *ObjectID*, *DisplayName* ve *UserPrincipalName* özelliklerini görüntüler.

Görüntülenecek özellikler hakkında daha seçici olmak için Select cmdlet'ini **Get-AzureADUser** cmdlet'iyle birlikte kullanın. İki cmdlet'i birleştirmek için, Azure Active Directory PowerShell'e Graph için bir komutun sonuçlarını alıp sonraki komuta göndermesini bildiren "kanal" karakterini ("|") kullanın. Her kullanıcı hesabı için *DisplayName*, *Department* ve *UsageLocation* değerlerini görüntüleyen örnek bir komut aşağıda verilmiştir:
  
```powershell
Get-AzureADUser | Select DisplayName,Department,UsageLocation
```

Bu komut PowerShell'e şunları yönerge eder:
  
1. Kullanıcı hesaplarıyla ilgili tüm bilgileri (**Get-AzureADUser**) alın ve sonraki komuta (**|**) gönderin.
    
1.  Yalnızca kullanıcı hesabı adını, departmanı ve kullanım konumunu görüntüleyin (**DisplayName, Department, UsageLocation'ı seçin**).
  
Belirli bir kullanıcı hesabının tüm özelliklerini görmek için **Select** cmdlet'ini ve joker karakterini (*) kullanın. İşte bir örnek:
  
```powershell
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com | Select *
```

Başka bir örnek olarak, belirli bir kullanıcı hesabının etkin durumunu denetlemek için aşağıdaki komutu çalıştırın:
  
```powershell
Get-AzureADUser -ObjectID <sign-in name of the user account> | Select DisplayName,UserPrincipalName,AccountEnabled
```

### <a name="view-account-synchronization-status"></a>Hesap eşitleme durumunu görüntüleme

Kullanıcı hesaplarının iki kaynağı vardır: 

- şirket içi AD'den buluta eşitlenen hesaplar olan Windows Server Active Directory (AD).

- doğrudan bulutta oluşturulan Azure Active Directory (Azure AD) hesapları.

**Şirket içi** AD'den eşitlenen hesapları bulmak için aşağıdaki komutu kullanabilirsiniz. PowerShell'e *DirSyncEnabled* özniteliği *True* olarak ayarlanmış olan tüm kullanıcıları alma talimatını sağlar. 

```powershell
Get-AzureADUser | Where {$_.DirSyncEnabled -eq $true}
```

**Yalnızca bulut** hesaplarını bulmak için aşağıdaki komutu kullanabilirsiniz. PowerShell'e *DirSyncEnabled* özniteliği *False* olarak ayarlanmış veya ayarlanmamış (*Null*) tüm kullanıcıları alma talimatını vemektedir.
Şirket içi AD'den hiçbir zaman eşitlenmemiş bir hesabın *DirSyncEnabled* değeri *Null* olarak ayarlanmıştır. Başlangıçta şirket içi AD'den eşitlenen ancak artık eşitlenemeyen bir hesabın *DirSyncEnabled* değeri *False* olarak ayarlanmıştır. 

```powershell
Get-AzureADUser | Where {$_.DirSyncEnabled -ne $true}
```

### <a name="view-accounts-based-on-a-common-property"></a>Ortak bir özelliğe göre hesapları görüntüleme

Görüntülenecek hesap listesi hakkında daha seçici olmak için **Get-AzureADUser** cmdlet'iyle birlikte **Where** cmdlet'ini kullanabilirsiniz. İki cmdlet'i birleştirmek için, Azure Active Directory PowerShell'e Graph için bir komutun sonuçlarını alıp sonraki komuta göndermesini bildiren "kanal" karakterini ("|") kullanın. Aşağıda, yalnızca belirtilmemiş kullanım konumuna sahip olan kullanıcı hesaplarını görüntüleyen örnek bir komut verilmiştir:
  
```powershell
Get-AzureADUser | Where {$_.UsageLocation -eq $Null}
```

Bu komut, Graph için Azure Active Directory PowerShell'e şu yönergeleri sağlar:
  
1. Kullanıcı hesaplarıyla ilgili tüm bilgileri (**Get-AzureADUser**) alın ve sonraki komuta (**|**) gönderin.
    
1. Belirtilmemiş kullanım konumu olan tüm kullanıcı hesaplarını bulun (**Burada {$\_. UsageLocation -eq $Null}**). Küme ayraçlarının içinde, komut PowerShell'e yalnızca UsageLocation kullanıcı hesabı özelliğinin (**$\_) bulunduğu hesap kümesini bulmasını ister. UsageLocation**) belirtilmemiş (**-eq $Null**).
    
**UsageLocation** özelliği, bir kullanıcı hesabıyla ilişkili birçok özelliknden yalnızca biridir. Belirli bir kullanıcı hesabının tüm özelliklerini görüntülemek için **Select** cmdlet'ini ve joker karakterini (*) kullanın. İşte bir örnek:
  
```powershell
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com | Select *
```

Örneğin, **City** bir kullanıcı hesabı özelliğinin adıdır. Londra'da yaşayan kullanıcıların tüm hesaplarını listelemek için aşağıdaki komutu kullanabilirsiniz:
  
```powershell
Get-AzureADUser | Where {$_.City -eq "London"}
```

> [!TIP]
> Bu örneklerde **Where** cmdlet'inin söz dizimi **Where {$\_** şeklindedir. [kullanıcı hesabı özellik adı] [karşılaştırma işleci] [değer] **}**.> [karşılaştırma işleci] eşittir için **-eq** , eşit değil için **-ne** , küçüktür için **-lt** , büyüktür ve diğerleri için **-gt** şeklindedir.  [value] genellikle bir dizedir (harf, sayı ve diğer karakter dizisi), sayısal bir değer veya belirtilmemiş için **$Null** . Daha fazla bilgi için bkz [. Where](/powershell/module/microsoft.powershell.core/where-object).

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Windows PowerShell için Microsoft Azure Active Directory Modülünü kullanma

İlk olarak [Microsoft 365 kiracınıza bağlanın](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

### <a name="view-all-accounts"></a>Tüm hesapları görüntüleme

Kullanıcı hesaplarının tam listesini görüntülemek için şu komutu çalıştırın:
  
```powershell
Get-MsolUser
```

>[!Note]
>PowerShell Core, Windows PowerShell modülü için Microsoft Azure Active Directory Modülünü ve adında *Msol* bulunan cmdlet'leri desteklemez. Bu cmdlet'leri Windows PowerShell çalıştırın.
>

Şuna benzer bilgiler almalısınız:
  
```powershell
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BonnieK@litwareinc.onmicrosoft.com    Bonnie Kearney        True
FabriceC@litwareinc.onmicrosoft.com   Fabrice Canel         True
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False 
AnneWlitwareinc.onmicrosoft.com       Anne Wallace          True
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False
```

**Get-MsolUser** cmdlet'i, görüntülenen kullanıcı hesapları kümesini filtrelemek için bir dizi parametreye de sahiptir. Örneğin, lisanssız kullanıcıların listesi için (Microsoft 365 eklenmiş ancak henüz hizmetlerden herhangi birini kullanma lisansına sahip olmayan kullanıcılar) şu komutu çalıştırın:
  
```powershell
Get-MsolUser -UnlicensedUsersOnly
```

Şuna benzer bilgiler almalısınız:
  
```powershell
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False
```

Görüntülenen kullanıcı hesapları kümesini filtrelemeye yönelik ek parametreler hakkında bilgi için bkz. [Get-MsolUser](/previous-versions/azure/dn194133(v=azure.100)).
  
### <a name="view-a-specific-account"></a>Belirli bir hesabı görüntüleme

Belirli bir kullanıcı hesabını görüntülemek için aşağıdaki komutu çalıştırın. Kullanıcı hesabının oturum açma adını (kullanıcı asıl adı (UPN) olarak da bilinir) doldurun. "<" ve ">" karakterlerini kaldırın.
  
```powershell
Get-MsolUser -UserPrincipalName <sign-in name of the user account>
```

### <a name="view-accounts-based-on-a-common-property"></a>Ortak bir özelliğe göre hesapları görüntüleme

Görüntülenecek hesap listesi hakkında daha seçici olmak için **Where** cmdlet'ini **Get-MsolUser** cmdlet'iyle birlikte kullanabilirsiniz. İki cmdlet'i birleştirmek için PowerShell'e bir komutun sonuçlarını alıp sonraki komuta göndermesini söyleyen "kanal" karakterini ("|") kullanın. Aşağıda, yalnızca belirtilmemiş kullanım konumuna sahip olan kullanıcı hesaplarını gösteren bir örnek verilmiştir:
  
```powershell
Get-MsolUser | Where {$_.UsageLocation -eq $Null}
```

Bu komut PowerShell'e şunları yönerge eder:
  
1. Kullanıcı hesaplarındaki (**Get-MsolUser**) tüm bilgileri alın ve sonraki komuta (**|**) gönderin.
    
1. Belirtilmemiş kullanım konumuna sahip tüm kullanıcı hesaplarını bulun (**Burada {$\_. UsageLocation -eq $Null}**). Küme ayraçlarının içinde, komut PowerShell'e yalnızca UsageLocation kullanıcı hesabı özelliğinin (**$\_) bulunduğu hesap kümesini bulmasını ister. UsageLocation**) belirtilmemiş (**-eq $Null**).
    
Şuna benzer bilgiler almalısınız:
  
```powershell
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False 
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False

```

*UsageLocation* özelliği, bir kullanıcı hesabıyla ilişkili birçok özelliknden yalnızca biridir. Kullanıcı hesaplarının tüm özelliklerini görmek için **Select** cmdlet'ini ve joker karakterini (*) kullanarak belirli bir kullanıcı hesabının tümünü görüntüleyin. İşte bir örnek:
  
```powershell
Get-MsolUser -UserPrincipalName BelindaN@litwareinc.onmicosoft.com | Select *
```

Örneğin, *City* bir kullanıcı hesabı özelliğinin adıdır. Londra'da yaşayan kullanıcıların tüm kullanıcı hesaplarını listelemek için aşağıdaki komutu kullanabilirsiniz:
  
```powershell
Get-MsolUser | Where {$_.City -eq "London"}
```

> [!TIP]
> Bu örneklerde **Where** cmdlet'inin söz dizimi **Where {$\_** şeklindedir. [kullanıcı hesabı özellik adı] [karşılaştırma işleci] [değer] **}**.  [comparison operator] eşittir için **-eq** , eşit değil için **-ne** , küçüktür için **-lt** , büyüktür ve diğerleri için **-gt** şeklindedir.  [value] genellikle bir dizedir (harf, sayı ve diğer karakter dizisi), sayısal bir değer veya belirtilmemiş için **$Null** . Daha fazla bilgi için bkz [. Where](/powershell/module/microsoft.powershell.core/where-object).
  
Kullanıcı hesabının engellenen durumunu denetlemek için aşağıdaki komutu kullanın:
  
```powershell
Get-MsolUser -UserPrincipalName <UPN of user account> | Select DisplayName,BlockCredential
```

### <a name="view-additional-property-values-for-accounts"></a>Hesaplar için ek özellik değerlerini görüntüleme

Varsayılan olarak **, Get-MsolUser** cmdlet'i kullanıcı hesaplarının şu üç özelliğini görüntüler:
  
- Userprincipalname

- Displayname

- isLicensed

Kullanıcının çalıştığı departman ve Microsoft 365 hizmetlerini kullandığı ülke/bölge gibi ek özelliklere ihtiyacınız varsa, kullanıcı hesabı özelliklerinin listesini belirtmek için **Get-MsolUser'ı** **Seç** cmdlet'iyle birlikte çalıştırabilirsiniz. İşte bir örnek:
  
```powershell
Get-MsolUser | Select DisplayName, Department, UsageLocation
```

Bu komut PowerShell'e şunları yönerge eder:
  
1. Kullanıcı hesapları (**Get-MsolUser**) hakkındaki tüm bilgileri alın ve sonraki komuta (**|**) gönderin.
    
1. Yalnızca kullanıcı hesabı adını, departmanı ve kullanım konumunu görüntüleyin (**DisplayName, Department, UsageLocation'ı seçin**).
    
Şuna benzer bilgiler almalısınız:
  
```powershell
DisplayName             Department                       UsageLocation
-----------             ----------                       -------------
Bonnie Kearney          Sales & Marketing                    US
Fabrice Canel           Legal                                US
Brian Johnson
Anne Wallace            Executive Management                 US
Alex Darrow             Sales & Marketing                    US
Scott Wallace           Operations
```

**Seç** cmdlet'i hangi özelliklerin görüntüleneceğini seçmenize olanak tanır. Belirli bir kullanıcı hesabının tüm özelliklerini görüntülemek için (*) joker karakterini kullanın. İşte bir örnek:
  
```powershell
Get-MsolUser -UserPrincipalName BelindaN@litwareinc.onmicosoft.com | Select *
```

Görüntülenecek hesap listesi hakkında daha seçici olmak için **Where** cmdlet'ini de kullanabilirsiniz. Aşağıda, yalnızca belirtilmemiş kullanım konumuna sahip olan kullanıcı hesaplarını görüntüleyen örnek bir komut verilmiştir:
  
```powershell
Get-MsolUser | Where {$_.UsageLocation -eq $Null} | Select DisplayName, Department, UsageLocation
```

Bu komut PowerShell'e şunları yönerge eder:
  
1. Kullanıcı hesapları (**Get-MsolUser**) hakkındaki tüm bilgileri alın ve sonraki komuta (**|**) gönderin.
    
1. Belirtilmemiş kullanım konumuna sahip tüm kullanıcı hesaplarını bulun (**Burada {$\_. UsageLocation -eq $Null}**) ve elde edilen bilgileri sonraki komuta (**|**) gönderin. Küme ayraçlarının içinde, komut PowerShell'e yalnızca UsageLocation kullanıcı hesabı özelliğinin (**$\_) bulunduğu hesap kümesini bulmasını ister. UsageLocation**) belirtilmemiş (**-eq $Null**).
    
1. Yalnızca kullanıcı hesabı adını, departmanı ve kullanım konumunu görüntüleyin (**DisplayName, Department, UsageLocation'ı seçin**).
    
Şuna benzer bilgiler almalısınız:
  
```powershell
DisplayName              Department                      UsageLocation
-----------              ----------                      -------------
Brian Johnson 
Scott Wallace            Operations
```

Microsoft 365 kullanıcılarınızı oluşturmak ve yönetmek için dizin eşitlemesi kullanıyorsanız, Microsoft 365 kullanıcının yansıtıldığı yerel hesabı görüntüleyebilirsiniz. Aşağıdaki örnekte şu varsayımlar yer alır:

- Azure AD Bağlan, ObjectGUID'nin varsayılan kaynak bağlantı noktasını kullanacak şekilde yapılandırılmıştır. (Kaynak tutturucu yapılandırma hakkında daha fazla bilgi için bkz. [Azure AD Bağlan: Tasarım kavramları](/azure/active-directory/hybrid/plan-connect-design-concepts)).
- PowerShell için Active Directory Domain Services modülü yüklendi (bkz[. RSAT araçları](https://www.microsoft.com/en-gb/download/details.aspx?id=45520)).

```powershell
Get-ADUser ([guid][System.Convert]::FromBase64String((Get-MsolUser -UserPrincipalName <UPN of user account>).ImmutableID)).guid
```

## <a name="see-also"></a>Ayrıca bkz.

[PowerShell ile Microsoft 365 kullanıcı hesaplarını, lisanslarını ve gruplarını yönetme](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
  
[PowerShell ile Microsoft 365’i yönetme](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[Microsoft 365 için PowerShell ile Kullanmaya başlayın](getting-started-with-microsoft-365-powershell.md)
