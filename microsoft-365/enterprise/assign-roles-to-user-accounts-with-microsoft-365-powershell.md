---
title: PowerShell ile Microsoft 365 hesaplarına rol atama
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 09/23/2020
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
- PowerShell
- Ent_Office_Other
- seo-marvel-apr2020
ms.assetid: ede7598c-b5d5-4e3e-a488-195f02f26d93
description: Bu makalede, kullanıcı hesaplarına yönetici rolleri atamak üzere Microsoft 365 için PowerShell'in ne kadar hızlı ve kolay bir şekilde kullanıldığı hakkında bilgi edinebilirsiniz.
ms.openlocfilehash: 0b0fc0a5da1a6b84d4f13f95ace4846e367ae111
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62985057"
---
# <a name="assign-admin-roles-to-microsoft-365-user-accounts-with-powershell"></a>PowerShell ile Microsoft 365 hesaplarına yönetici rolleri atama

*Bu makale hem son hem de Microsoft 365 Kurumsal hem de Office 365 Kurumsal.*

Microsoft 365 için PowerShell kullanarak kullanıcı hesaplarına kolayca rol Microsoft 365.

>[!Note]
>Yeni yönetici [rolüyle kullanıcı](../admin/add-users/assign-admin-roles.md) hesaplarına yönetici rolleri Microsoft 365 yönetim merkezi.
>
>Ek kaynakların listesi için bkz. [Kullanıcıları ve grupları yönetme](/admin).
>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Graph modülü için Azure Active Directory PowerShell'i kullanma

İlk olarak, **kiracınıza bağlanmak için Azure AD DC** **yöneticisi**, Bulut Uygulaması  Yöneticisi veya [Genel yönetici Microsoft 365 kullanın](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
 
Daha fazla bilgi için bkz. [Yönetici rolleri hakkında](/microsoft-365/admin/add-users/about-admin-roles?).

Ardından, bir role eklemek istediğiniz kullanıcı hesabının oturum açma adını (örneğin: fredsm\@ contoso.com). Bu, kullanıcı asıl adı (UPN) olarak da bilinir.

Ardından, rolün adını belirlersiniz. Bkz [. Azure AD yerleşik rolleri](/azure/active-directory/roles/permissions-reference).

>[!Note]
>Bu makaledeki notlara dikkatin. Bazı rol adları Azure Active Directory (Azure AD) PowerShell'de farklıdır. Örneğin, Azure AD PowerShell *SharePoint* te Microsoft 365 yönetim merkezi Yönetici rolü *SharePoint* Yönetici rolüne sahip olur.
>

Ardından, oturum açma ve rol adlarını doldurun ve şu komutları çalıştırın:
  
```powershell
$userName="<sign-in name of the account>"
$roleName="<admin role name>"
$role = Get-AzureADDirectoryRole | Where {$_.displayName -eq $roleName}
if ($role -eq $null) {
$roleTemplate = Get-AzureADDirectoryRoleTemplate | Where {$_.displayName -eq $roleName}
Enable-AzureADDirectoryRole -RoleTemplateId $roleTemplate.ObjectId
$role = Get-AzureADDirectoryRole | Where {$_.displayName -eq $roleName}
}
Add-AzureADDirectoryRoleMember -ObjectId $role.ObjectId -RefObjectId (Get-AzureADUser | Where {$_.UserPrincipalName -eq $userName}).ObjectID
```

aşağıdaki örnekte, hizmet yöneticisi rolünü *belindan\@ SharePoint* hesabına ataan tamamlanmış contoso.com vardır:
  
```powershell
$userName="belindan@contoso.com"
$roleName="SharePoint Service Administrator"
$role = Get-AzureADDirectoryRole | Where {$_.displayName -eq $roleName}
if ($role -eq $null) {
$roleTemplate = Get-AzureADDirectoryRoleTemplate | Where {$_.displayName -eq $roleName}
Enable-AzureADDirectoryRole -RoleTemplateId $roleTemplate.ObjectId
$role = Get-AzureADDirectoryRole | Where {$_.displayName -eq $roleName}
}
Add-AzureADDirectoryRoleMember -ObjectId $role.ObjectId -RefObjectId (Get-AzureADUser | Where {$_.UserPrincipalName -eq $userName}).ObjectID
```

Belirli bir yönetici rolüne yönelik kullanıcı adlarının listesini görüntülemek için bu komutları kullanın.

```powershell
$roleName="<role name>"
Get-AzureADDirectoryRole | Where { $_.DisplayName -eq $roleName } | Get-AzureADDirectoryRoleMember | Ft DisplayName
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Kaynak için Microsoft Azure Active Directory Modülü'Windows PowerShell

İlk olarak, bir genel yönetici hesabı kullanarak [kiracınıza Microsoft 365 kullanın](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).
  
### <a name="for-a-single-role-change"></a>Tek bir rol değişikliği için

Kullanıcı hesabını belirtmenin en yaygın yolu, oturum açma adı veya kullanıcı asıl adı (UPN) olarak da bilinen görünen adını veya e-posta adını kullanmaktır.

#### <a name="display-names-of-user-accounts"></a>Kullanıcı hesaplarının görünen adları

Kullanıcı hesaplarının görünen adlarla çalışmaya alışdısanız, aşağıdaki bilgileri seçin:
  
- Yapılandırmak istediğiniz kullanıcı hesabı
    
    Kullanıcı hesabını belirtmek için, o hesabın Görünen Adını belirlemeniz gerekir. Hesapların tam listesini almak için şu komutu kullanın:
    
  ```powershell
  Get-MsolUser -All | Sort DisplayName | Select DisplayName | More
  ```

    Bu komutta, kullanıcı hesaplarınızı Görünen Ad'a göre sıralanmış, her bir ekrana göre sıralanmış Görünen Ad listele. Where cmdlet'ini kullanarak listeyi daha küçük bir **kümeye** filtreleyebilirsiniz. Aşağıdaki örnekle bakın.

   >[!Note]
   >PowerShell Core, adı *Msol* olan Microsoft Azure Active Directory Modülü Windows PowerShell cmdlet'leri desteklemez. Bu cmdlet'leri çalışma Windows PowerShell.
   >
    
  ```powershell
  Get-MsolUser -All | Where DisplayName -like "John*" | Sort DisplayName | Select DisplayName | More
  ```

    Bu komut yalnızca Görünen Ad'ın "Can" ile başladığı kullanıcı hesaplarını listeler.
    
- Atamak istediğiniz rol
    
    Kullanıcı hesaplarına atayabilirsiniz kullanılabilir yönetici rollerinin listesini görüntülemek için şu komutu kullanın:
    
  ```powershell
  Get-MsolRole | Sort Name | Select Name,Description
  ```

Hesabın Görünen Adı'nı ve rolün adını belirlerken, rolü hesaba atamak için şu komutları kullanın:
  
```powershell
$dispName="<The Display Name of the account>"
$roleName="<The admin role name you want to assign to the account>"
Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser -All | Where DisplayName -eq $dispName).UserPrincipalName -RoleName $roleName
```

Komutları diğer Not Defteri. Açıklama *$dispName* *değişkenlerini $roleName* , açıklama metnini kendi değerleriyle değiştirin. Karakterleri kaldırın \< and > ama tırnak işaretlerini kaldırın. Değiştirilen çizgileri, çalıştırmak Microsoft Azure Active Directory Için Windows PowerShell Modüle yapıştırın. Alternatif olarak, Windows PowerShell Betik Ortamı'nda (ISE) kullanabilirsiniz.
  
İşte tamamlanmış bir komut kümesi örneği:
  
```powershell
$dispName="Scott Wallace"
$roleName="SharePoint Service Administrator"
Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser -All | Where DisplayName -eq $dispName).UserPrincipalName -RoleName $roleName
```

#### <a name="sign-in-names-of-user-accounts"></a>Kullanıcı hesaplarının oturum açma adları

Kullanıcı hesaplarının oturum açma adlarında veya UPN'lerde çalışmaya alışdısanız, aşağıdaki bilgileri seçin:
  
- Kullanıcı hesabının UPN'si
    
    UPN'leri bilmiyorsanız, şu komutu kullanın:
    
  ```powershell
  Get-MsolUser -All | Sort UserPrincipalName | Select UserPrincipalName | More
  ```

    Bu komut, kullanıcı hesaplarınızı UPN'ye göre sıralanmış, her bir ekrandan tek bir ekranda listeler. Listeyi filtrelemek **için Where** cmdlet'ini kullanabilirsiniz. İşte bir örnek:
    
  ```powershell
  Get-MsolUser -All | Where DisplayName -like "John*" | Sort UserPrincipalName | Select UserPrincipalName | More
  ```

    Bu komut yalnızca Görünen Ad'ın "Can" ile başladığı kullanıcı hesaplarını listeler.
    
- Atamak istediğiniz rol
    
    Kullanıcı hesaplarına atayabilirsiniz kullanılabilir rollerin listesini görüntülemek için şu komutu kullanın:
    
  ```powershell
  Get-MsolRole | Sort Name | Select Name,Description
  ```

Hesabın UPN'niz ve rolün adı olduktan sonra, rolü hesaba atamak için şu komutları kullanın:
  
```powershell
$upnName="<The UPN of the account>"
$roleName="<The role name you want to assign to the account>"
Add-MsolRoleMember -RoleMemberEmailAddress $upnName -RoleName $roleName
```

Komutları kopyalayın ve başka bir Not Defteri. Değişken **ve $upnName** **$roleName** için. Açıklama metnini değerleriyle değiştirin. Karakterleri kaldırın \< and > ama tırnak işaretlerini kaldırın. Değiştirilen çizgileri, Microsoft Azure Active Directory için Modül Windows PowerShell bu pencereye yapıştırın. Alternatif olarak, ISE Windows PowerShell kullanabilirsiniz.
  
İşte tamamlanmış bir komut kümesi örneği:
  
```powershell
$upnName="scottw@contoso.com"
$roleName="SharePoint Service Administrator"
Add-MsolRoleMember -RoleMemberEmailAddress $upnName -RoleName $roleName
```

### <a name="multiple-role-changes"></a>Birden çok rol değişikliği

Birden çok rol değişikliği için aşağıdaki bilgileri belirler:
  
- Yapılandırmak istediğiniz kullanıcı hesapları. Önceki bölümde yer alan yöntemleri kullanarak görünen adlar veya UPN'ler kümelerini topabilirsiniz.
    
- Her kullanıcı hesabına atamak istediğiniz roller. Kullanıcı hesaplarına atayabilirsiniz kullanılabilir rollerin listesini görüntülemek için şu komutu kullanın:
    
  ```powershell
  Get-MsolRole | Sort Name | Select Name,Description
  ```

Ardından, görünen ad veya UPN ve rol adı alanlarının bulunduğu bir virgülle ayrılmış değer (CSV) metin dosyası oluşturun. Bunu kendi iş yerleri için Microsoft Excel.

Görünen adlar için bir örnek:
  
```powershell
DisplayName,RoleName
"Belinda Newman","Billing Administrator"
"Scott Wallace","SharePoint Service Administrator"
```

Ardından, CSV dosyasının konumunu doldurun ve PowerShell komut isteminde sonuç komutlarını çalıştırın.
  
```powershell
$fileName="<path and file name of the input CSV file that has the role changes, example: C:\admin\RoleUpdates.CSV>"
$roleChanges=Import-Csv $fileName | ForEach {Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser | Where DisplayName -eq $_.DisplayName).UserPrincipalName -RoleName $_.RoleName }

```

İşte UPN'ler için bir örnek:
  
```powershell
UserPrincipalName,RoleName
"belindan@contoso.com","Billing Administrator"
"scottw@contoso.com","SharePoint Service Administrator"
```

Ardından, CSV dosyasının konumunu doldurun ve PowerShell komut isteminde sonuç komutlarını çalıştırın.
  
```powershell
$fileName="<path and file name of the input CSV file that has the role changes, example: C:\admin\RoleUpdates.CSV>"
$roleChanges=Import-Csv $fileName | ForEach { Add-MsolRoleMember -RoleMemberEmailAddress $_.UserPrincipalName -RoleName $_.RoleName }

```

## <a name="see-also"></a>Ayrıca bkz.

- [PowerShell Microsoft 365 hesaplarını, lisanslarını ve gruplarını yönetme](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
- [PowerShell Microsoft 365'i yönetme](manage-microsoft-365-with-microsoft-365-powershell.md)
- [Microsoft 365 için PowerShell'i Microsoft 365](getting-started-with-microsoft-365-powershell.md)
