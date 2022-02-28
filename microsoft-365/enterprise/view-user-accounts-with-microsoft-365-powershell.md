---
title: PowerShell Microsoft 365 hesaplarını görüntüleme
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: PowerShell ile kullanıcı hesaplarınızı farklı şekillerde görüntülemeyi, Microsoft 365 ve görüntülemeyi öğrenin.
ms.openlocfilehash: 5c434825da95fd7d90594b2424cab287305f7d26
ms.sourcegitcommit: bf3965b46487f6f8cf900dd9a3af8b213a405989
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/02/2021
ms.locfileid: "62989972"
---
# <a name="view-microsoft-365-user-accounts-with-powershell"></a>PowerShell Microsoft 365 hesaplarını görüntüleme

*Bu makale hem son hem de Microsoft 365 Kurumsal hem de Office 365 Kurumsal.*

Microsoft 365 yönetim merkezi'i kullanarak kiracınız için hesapları Microsoft 365 kullanabilirsiniz. Microsoft 365 için PowerShell bunu sağlar, ancak ek işlevler de sağlar.
  
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Graph modülü için Azure Active Directory PowerShell'i kullanma

İlk olarak[, kiracınıza bağlan Microsoft 365 bağlanin](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
  
### <a name="view-all-accounts"></a>Tüm hesapları görüntüleme

Kullanıcı hesaplarının tam listesini görüntülemek için şu komutu çalıştırın:
  
```powershell
Get-AzureADUser
```

Aşağıdakine benzer bilgiler alalısiniz:
  
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

Belirli bir kullanıcı hesabını görüntülemek için aşağıdaki komutu çalıştırın. Kullanıcı hesabının, kullanıcı asıl adı (UPN) olarak da bilinen oturum açma hesabı adını doldurun. "<" ve ">" karakterlerini kaldırın.
  
```powershell
Get-AzureADUser -ObjectID <sign-in name of the user account>
```

İşte bir örnek:
  
```powershell
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com
```

### <a name="view-additional-property-values-for-a-specific-account"></a>Belirli bir hesabın ek özellik değerlerini görüntüleme

Varsayılan olarak, **Get-AzureADUser** cmdlet'i hesapların *yalnızca ObjectID*, *DisplayName* *ve UserPrincipalName* özelliklerini görüntüler.

Görüntülenmek üzere özellikler konusunda daha seçici olmak için **, Get-AzureADUser cmdlet'iyle birlikte Select** cmdlet'ini kullanın. İki cmdlet'i birleştirmek için, Graph için PowerShell'Azure Active Directory bir komutun sonuçlarını alıp bir sonraki komuta göndermenizi söyleyen "pipe" karakterini ("|") kullanın. Her kullanıcı hesabı için *DisplayName*, *Department* ve *UsageLocation* komutlarını görüntüleyen örnek bir komut şöyledir:
  
```powershell
Get-AzureADUser | Select DisplayName,Department,UsageLocation
```

Bu komut PowerShell'e şunları sağlar:
  
1. Kullanıcı hesaplarından (**Get-AzureADUser**) tüm bilgileri edinin ve sonraki komuta () gönderin **|**.
    
1.  Yalnızca kullanıcı hesabı adını, departmanı ve kullanım konumunu görüntüler (**DisplayName, Department, UsageLocation öğesini seçin**).
  
Belirli bir kullanıcı hesabının tüm özelliklerini görmek için, **Seç cmdlet'ini** ve joker karakteri (*) kullanın. İşte bir örnek:
  
```powershell
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com | Select *
```

Başka bir örnek olarak, belirli bir kullanıcı hesabının etkin durumunu kontrol etmek için aşağıdaki komutu çalıştırın:
  
```powershell
Get-AzureADUser -ObjectID <sign-in name of the user account> | Select DisplayName,UserPrincipalName,AccountEnabled
```

### <a name="view-account-synchronization-status"></a>Hesap eşitleme durumunu görüntüleme

Kullanıcı hesaplarının iki kaynağı vardır: 

- Windows Server Active Directory (AD), şirket içi AD'den buluta eşitlenen hesaplardır.

- Azure Active Directory bulutta oluşturulan kullanıcı hesapları (Azure AD) hesaplarıdır.

Şirket içi AD'den eşitleyen hesapları bulmak için aşağıdaki **komutu kullanabilirsiniz** . Bu özellik, PowerShell'e *DirSyncEnabled özniteliğine* sahip olan tüm kullanıcıları True olarak ayarlamalarını *sağlar*. 

```powershell
Get-AzureADUser | Where {$_.DirSyncEnabled -eq $true}
```

Aşağıdaki komutu yalnızca bulut hesaplarını **bulmak için kullanabilirsiniz** . PowerShell'e *, DirSyncEnabled* özniteliği false olarak ayarlanmış veya ayarlenmemiş (Null) olan  tüm kullanıcıları ayarlaması *için bilgi verir*.
Şirket içi AD'den hiç eşitlenmemiş bir hesapta *DirSyncEnabled Null* olarak *ayarlanmıştır*. Başlangıçta şirket içi AD'den eşitlenen ancak artık eşitlenmemiş olan bir *hesapta DirSyncEnabled* *False olarak ayarlanmıştır*. 

```powershell
Get-AzureADUser | Where {$_.DirSyncEnabled -ne $true}
```

### <a name="view-accounts-based-on-a-common-property"></a>Hesapları ortak bir özele dayalı olarak görüntüleme

Görünen hesap listesi konusunda daha seçici olmak için **Where** cmdlet'ini **Get-AzureADUser cmdlet'iyle birlikte** kullanabilirsiniz. İki cmdlet'i birleştirmek için, Graph için PowerShell'Azure Active Directory bir komutun sonuçlarını alıp bir sonraki komuta göndermenizi söyleyen "pipe" karakterini ("|") kullanın. İşte, yalnızca belirtilmemiş bir kullanım konumu olan kullanıcı hesaplarını görüntüleyen örnek bir komut:
  
```powershell
Get-AzureADUser | Where {$_.UsageLocation -eq $Null}
```

Bu komut, Azure Active Directory PowerShell'e şunları Graph:
  
1. Kullanıcı hesaplarından (**Get-AzureADUser**) tüm bilgileri edinin ve sonraki komuta () gönderin **|**.
    
1. Belirtilmemiş kullanım konumu olan tüm kullanıcı hesaplarını bulun (**Burada {$\_. UsageLocation -eq $Null}**). Küme ayraçlarının içindeki komut, PowerShell'e yalnızca UsageLocation kullanıcı hesabı özelliğinin () kullanıldığı hesap kümelerini bulmalarını sağlar **$\_. UsageLocation**) belirtilmemiş (**-eq $Null**).
    
**UsageLocation** özelliği, kullanıcı hesabıyla ilişkilendirilmiş birçok özelliktir. Belirli bir kullanıcı hesabının tüm özelliklerini görüntülemek için, **Seç cmdlet'ini** ve joker karakteri (*) kullanın. İşte bir örnek:
  
```powershell
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com | Select *
```

Örneğin, **Şehir** , kullanıcı hesabı özelliğinin adıdır. Londra'da yaşayan kullanıcıların tüm hesaplarını listeleyen aşağıdaki komutu kullanabilirsiniz:
  
```powershell
Get-AzureADUser | Where {$_.City -eq "London"}
```

> [!TIP]
> Bu örneklerde **Where** cmdlet'inin söz dizimi **Where {$\_.** [kullanıcı hesabı özellik adı] [karşılaştırma işleci] [değer] **}**.> [karşılaştırma işleci] eşittir **için -eq** , eşittir için **-ne** , **küçükten küçük için -lt** , **büyüktür için -gt** ve diğerleri.  [değer], genellikle bir dizedir (harf, sayı dizisi ve diğer karakterlerden oluşur), sayısal değerdir **$Null** belirtilmemiş bir dizedir. Daha fazla bilgi için bkz. [Where](/powershell/module/microsoft.powershell.core/where-object).

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Kaynak için Microsoft Azure Active Directory Modülü'Windows PowerShell

İlk olarak[, kiracınıza bağlan Microsoft 365 bağlanin](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

### <a name="view-all-accounts"></a>Tüm hesapları görüntüleme

Kullanıcı hesaplarının tam listesini görüntülemek için şu komutu çalıştırın:
  
```powershell
Get-MsolUser
```

>[!Note]
>PowerShell Core, adı *Msol* olan Microsoft Azure Active Directory Modülü Windows PowerShell cmdlet'leri desteklemez. Bu cmdlet'leri çalışma Windows PowerShell.
>

Aşağıdakine benzer bilgiler alalısiniz:
  
```powershell
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BonnieK@litwareinc.onmicrosoft.com    Bonnie Kearney        True
FabriceC@litwareinc.onmicrosoft.com   Fabrice Canel         True
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False 
AnneWlitwareinc.onmicrosoft.com       Anne Wallace          True
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False
```

**Get-MsolUser** cmdlet'in, görüntülenen kullanıcı hesapları kümesine filtre uygulama için bir parametre kümesi de vardır. Örneğin, lisanssız kullanıcıların listesi için (Microsoft 365'e eklenmiş olan ancak hizmetlerden herhangi birini kullanmak üzere henüz lisanslanmamış kullanıcılar) şu komutu çalıştırın:
  
```powershell
Get-MsolUser -UnlicensedUsersOnly
```

Aşağıdakine benzer bilgiler alalısiniz:
  
```powershell
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False
```

Görüntülenen kullanıcı hesapları kümesine filtre uygulamanın ek parametreleri hakkında bilgi için bkz. [Get-MsolUser](/previous-versions/azure/dn194133(v=azure.100)).
  
### <a name="view-a-specific-account"></a>Belirli bir hesabı görüntüleme

Belirli bir kullanıcı hesabını görüntülemek için aşağıdaki komutu çalıştırın. Kullanıcı hesabının, kullanıcı asıl adı (UPN) olarak da bilinen oturum açma adını doldurun. "<" ve ">" karakterlerini kaldırın.
  
```powershell
Get-MsolUser -UserPrincipalName <sign-in name of the user account>
```

### <a name="view-accounts-based-on-a-common-property"></a>Hesapları ortak bir özele dayalı olarak görüntüleme

Görünen hesap listesi konusunda daha seçici olmak için **, Get-MsolUser** cmdlet'iyle birlikte **Where** cmdlet'ini kullanabilirsiniz. İki cmdlet'i birleştirmek için, PowerShell'e bir komutun sonuçlarını almalarını ve bir sonraki komuta göndermelerini söyleyen "pipe" karakterini ("|") kullanın. Burada, yalnızca belirtilmemiş bir kullanım konumu olan kullanıcı hesaplarını gösteren bir örnek ve almaktadırsınız:
  
```powershell
Get-MsolUser | Where {$_.UsageLocation -eq $Null}
```

Bu komut PowerShell'e şunları sağlar:
  
1. Kullanıcı hesaplarından (**Get-MsolUser) tüm bilgileri alır** ve bir sonraki komuta () gönderir **|**.
    
1. Belirtilmemiş kullanım konumu olan tüm kullanıcı hesaplarını bulun (**Burada {$\_. UsageLocation -eq $Null}**). Küme ayraçlarının içindeki komut, PowerShell'e yalnızca UsageLocation kullanıcı hesabı özelliğinin () kullanıldığı hesap kümelerini bulmalarını sağlar **$\_. UsageLocation**) belirtilmemiş (**-eq $Null**).
    
Aşağıdakine benzer bilgiler alalısiniz:
  
```powershell
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False 
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False

```

*UsageLocation* özelliği, kullanıcı hesabıyla ilişkilendirilmiş birçok özelliktir. Kullanıcı hesaplarının tüm özelliklerini görmek için, **Select** cmdlet'ini ve joker karakteri (*) kullanarak belirli bir kullanıcı hesabının tüm özelliklerini görüntüye açın. İşte bir örnek:
  
```powershell
Get-MsolUser -UserPrincipalName BelindaN@litwareinc.onmicosoft.com | Select *
```

Örneğin, *Şehir* , kullanıcı hesabı özelliğinin adıdır. Londra'da yaşayan kullanıcıların tüm kullanıcı hesaplarını listeleyen aşağıdaki komutu kullanabilirsiniz:
  
```powershell
Get-MsolUser | Where {$_.City -eq "London"}
```

> [!TIP]
> Bu örneklerde **Where** cmdlet'inin söz dizimi **Where {$\_.** [kullanıcı hesabı özellik adı] [karşılaştırma işleci] [değer] **}**.  [karşılaştırma işleci] eşittir **için -eq** , eşittir için **-ne** , **küçük için -lt** , **büyüktür için -gt** ve diğerleri.  [değer], genellikle bir dizedir (harf, sayı dizisi ve diğer karakterlerden oluşur), sayısal değerdir **$Null** belirtilmemiş bir dizedir. Daha fazla bilgi için bkz. [Where](/powershell/module/microsoft.powershell.core/where-object).
  
Kullanıcı hesabının engellenmiş durumunu kontrol etmek için aşağıdaki komutu kullanın:
  
```powershell
Get-MsolUser -UserPrincipalName <UPN of user account> | Select DisplayName,BlockCredential
```

### <a name="view-additional-property-values-for-accounts"></a>Hesapların ek özellik değerlerini görüntüleme

Varsayılan olarak, **Get-MsolUser** cmdlet'i kullanıcı hesaplarının şu üç özelliklerini görüntüler:
  
- UserPrincipalName

- DisplayName

- isLicensed

Kullanıcının çalışma bölümü ve Microsoft 365 hizmetlerini kullanan ülke/bölge gibi ek özelliklere ihtiyacınız varsa, kullanıcı hesabı özelliklerinin listesini belirtmek için **Get-MsolUser'ı** **Select** cmdlet'iyle birlikte çalıştırabilirsiniz. İşte bir örnek:
  
```powershell
Get-MsolUser | Select DisplayName, Department, UsageLocation
```

Bu komut PowerShell'e şunları sağlar:
  
1. Kullanıcı hesapları (**Get-MsolUser) hakkında tüm bilgileri alır** ve bir sonraki komuta () gönderir **|**.
    
1. Yalnızca kullanıcı hesabı adını, departmanı ve kullanım konumunu görüntüler (**DisplayName, Department, UsageLocation öğesini seçin**).
    
Aşağıdakine benzer bilgiler alalısiniz:
  
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

**Seç** cmdlet'i, hangi özelliklerin görüntüleniyor olduğunu seçmenize olanak sağlar. Belirli bir kullanıcı hesabının tüm özelliklerini görüntülemek için, joker karakteri (*) kullanın. İşte bir örnek:
  
```powershell
Get-MsolUser -UserPrincipalName BelindaN@litwareinc.onmicosoft.com | Select *
```

Görünen hesap listesi konusunda daha seçici olmak için Where **cmdlet'ini de** kullanabilirsiniz. İşte, yalnızca belirtilmemiş bir kullanım konumu olan kullanıcı hesaplarını görüntüleyen örnek bir komut:
  
```powershell
Get-MsolUser | Where {$_.UsageLocation -eq $Null} | Select DisplayName, Department, UsageLocation
```

Bu komut PowerShell'e şunları sağlar:
  
1. Kullanıcı hesapları (**Get-MsolUser) hakkında tüm bilgileri alır** ve bir sonraki komuta () gönderir **|**.
    
1. Belirtilmemiş kullanım konumu olan tüm kullanıcı hesaplarını bulun (**Burada {$\_. UsageLocation -eq $Null}**) ve sonuç bilgilerini sonraki komuta () gönderin **|**. Küme ayraçlarının içindeki komut, PowerShell'e yalnızca UsageLocation kullanıcı hesabı özelliğinin () kullanıldığı hesap kümelerini bulmalarını sağlar **$\_. UsageLocation**) belirtilmemiş (**-eq $Null**).
    
1. Yalnızca kullanıcı hesabı adını, departmanı ve kullanım konumunu görüntüler (**DisplayName, Department, UsageLocation öğesini seçin**).
    
Aşağıdakine benzer bilgiler alalısiniz:
  
```powershell
DisplayName              Department                      UsageLocation
-----------              ----------                      -------------
Brian Johnson 
Scott Wallace            Operations
```

Kullanıcılarınızı oluşturmak ve yönetmek için dizin eşitlemesi kullanıyorsanız, Microsoft 365 kullanıcılarının projesinin Microsoft 365 yerel hesabı görüntüebilirsiniz. Aşağıdaki örnekte, aşağıdakilerin olduğu varsay varsay almaktadır:

- Azure AD Bağlan, ObjectGUID'nin varsayılan kaynak bağlantısı kullanmak üzere yapılandırılır. (Kaynak bağlantısı yapılandırma hakkında daha fazla bilgi için bkz. [Azure AD Bağlan: Tasarım kavramları](/azure/active-directory/hybrid/plan-connect-design-concepts)).
- PowerShell için Active Directory Etki Alanı Hizmetleri modülü yüklenmiştir ( [bkz. RSAT araçları](https://www.microsoft.com/en-gb/download/details.aspx?id=45520)).

```powershell
Get-ADUser ([guid][System.Convert]::FromBase64String((Get-MsolUser -UserPrincipalName <UPN of user account>).ImmutableID)).guid
```

## <a name="see-also"></a>Ayrıca bkz.

[PowerShell Microsoft 365 hesaplarını, lisanslarını ve gruplarını yönetme](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
  
[PowerShell Microsoft 365'i yönetme](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[Microsoft 365 için PowerShell'i Microsoft 365](getting-started-with-microsoft-365-powershell.md)
