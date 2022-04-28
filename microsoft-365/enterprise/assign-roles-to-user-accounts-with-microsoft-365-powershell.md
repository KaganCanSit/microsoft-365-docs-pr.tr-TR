---
title: PowerShell ile Microsoft 365 kullanıcı hesaplarına rol atama
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: Bu makalede, kullanıcı hesaplarına yönetici rolleri atamak üzere Microsoft 365 için PowerShell'i ne kadar hızlı ve kolay bir şekilde kullanabileceğinizi öğrenin.
ms.openlocfilehash: 8ac98920dd3d2d0487905b001434d73274463f9a
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65097458"
---
# <a name="assign-admin-roles-to-microsoft-365-user-accounts-with-powershell"></a>PowerShell ile Microsoft 365 kullanıcı hesaplarına yönetici rolleri atama

*Bu makale hem Microsoft 365 Kurumsal hem de Office 365 Kurumsal için geçerlidir.*

Microsoft 365 için PowerShell'i kullanarak kullanıcı hesaplarına kolayca rol atayabilirsiniz.

>[!Note]
>Microsoft 365 yönetim merkezi ile kullanıcı hesaplarına [yönetici rolleri atamayı](../admin/add-users/assign-admin-roles.md) öğrenin.
>
>Ek kaynakların listesi için bkz. [Kullanıcıları ve grupları yönetme](/admin).
>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Graph için Azure Active Directory PowerShell modülünü kullanma

İlk olarak, [Microsoft 365 kiracınıza bağlanmak](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module) için **bir Azure AD DC yöneticisi**, **Bulut Uygulaması Yöneticisi** veya **Genel yönetici** hesabı kullanın.
 
Daha fazla bilgi için bkz. [Yönetici rolleri hakkında](/microsoft-365/admin/add-users/about-admin-roles?).

Ardından, bir role eklemek istediğiniz kullanıcı hesabının oturum açma adını tanımlayın (örnek: fredsm\@ contoso.com). Bu, kullanıcı asıl adı (UPN) olarak da bilinir.

Ardından rolün adını belirleyin. Bkz. [Azure AD yerleşik rolleri](/azure/active-directory/roles/permissions-reference).

>[!Note]
>Bu makaledeki notlara dikkat edin. Bazı rol adları Azure Active Directory (Azure AD) PowerShell için farklıdır. Örneğin, *Microsoft 365 yönetim merkezi SharePoint Yöneticisi* rolü Azure AD PowerShell'de *SharePoint Hizmet Yöneticisi'dir*.
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

Aşağıda, SharePoint Hizmet Yöneticisi rolünü *belindan\@ contoso.com* hesabına atayan tamamlanmış bir komut kümesi örneği verilmiştir:
  
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

Belirli bir yönetici rolünün kullanıcı adlarının listesini görüntülemek için bu komutları kullanın.

```powershell
$roleName="<role name>"
Get-AzureADDirectoryRole | Where { $_.DisplayName -eq $roleName } | Get-AzureADDirectoryRoleMember | Ft DisplayName
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Windows PowerShell için Microsoft Azure Active Directory Modülünü kullanma

İlk olarak, [Microsoft 365 kiracınıza bağlanmak için](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell) bir genel yönetici hesabı kullanın.
  
### <a name="for-a-single-role-change"></a>Tek bir rol değişikliği için

Kullanıcı hesabını belirtmenin en yaygın yolları, oturum açma adı veya kullanıcı asıl adı (UPN) olarak da bilinen görünen adını veya e-posta adını kullanmaktır.

#### <a name="display-names-of-user-accounts"></a>Kullanıcı hesaplarının adlarını görüntüleme

Kullanıcı hesaplarının görünen adlarıyla çalışmaya alışkınsanız aşağıdaki bilgileri belirleyin:
  
- Yapılandırmak istediğiniz kullanıcı hesabı
    
    Kullanıcı hesabını belirtmek için Görünen Adını belirlemeniz gerekir. Hesapların tam listesini almak için şu komutu kullanın:
    
  ```powershell
  Get-MsolUser -All | Sort DisplayName | Select DisplayName | More
  ```

    Bu komut, kullanıcı hesaplarınızın Görünen Adı'nı, Görünen Ad'a göre sıralanmış olarak listeler. **Where** cmdlet'ini kullanarak listeyi daha küçük bir kümeye filtreleyebilirsiniz. Aşağıdaki örne bakın.

   >[!Note]
   >PowerShell Core, Windows PowerShell modülü için Microsoft Azure Active Directory Modülünü ve adında *Msol* bulunan cmdlet'leri desteklemez. Bu cmdlet'leri Windows PowerShell çalıştırın.
   >
    
  ```powershell
  Get-MsolUser -All | Where DisplayName -like "John*" | Sort DisplayName | Select DisplayName | More
  ```

    Bu komut yalnızca Görünen Ad'ın "John" ile başladığı kullanıcı hesaplarını listeler.
    
- Atamak istediğiniz rol
    
    Kullanıcı hesaplarına atayabileceğiniz kullanılabilir yönetici rollerinin listesini görüntülemek için şu komutu kullanın:
    
  ```powershell
  Get-MsolRole | Sort Name | Select Name,Description
  ```

Hesabın Görünen Adını ve rolün adını belirledikten sonra, rolü hesaba atamak için şu komutları kullanın:
  
```powershell
$dispName="<The Display Name of the account>"
$roleName="<The admin role name you want to assign to the account>"
Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser -All | Where DisplayName -eq $dispName).UserPrincipalName -RoleName $roleName
```

Komutları Not Defteri yapıştırın. *$dispName* ve *$roleName* değişkenleri için açıklama metnini değerleriyle değiştirin. \< and > Karakterleri kaldırın ancak tırnak işaretlerini koruyun. Değiştirilen satırları çalıştırmak üzere Windows PowerShell için Microsoft Azure Active Directory Modülüne yapıştırın. Alternatif olarak, Windows PowerShell Tümleşik Betik Ortamı'nı (ISE) kullanabilirsiniz.
  
Aşağıda tamamlanmış bir komut kümesi örneği verilmişti:
  
```powershell
$dispName="Scott Wallace"
$roleName="SharePoint Service Administrator"
Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser -All | Where DisplayName -eq $dispName).UserPrincipalName -RoleName $roleName
```

#### <a name="sign-in-names-of-user-accounts"></a>Kullanıcı hesaplarının oturum açma adları

Kullanıcı hesaplarının oturum açma adlarıyla veya UPN'leriyle çalışmaya alışkınsanız aşağıdaki bilgileri belirleyin:
  
- Kullanıcı hesabının UPN'sini
    
    UPN'yi bilmiyorsanız şu komutu kullanın:
    
  ```powershell
  Get-MsolUser -All | Sort UserPrincipalName | Select UserPrincipalName | More
  ```

    Bu komut, kullanıcı hesaplarınızın UPN'sini UPN'ye göre sıralanmış ve her seferinde bir ekran olarak listeler. Listeyi filtrelemek için **Where** cmdlet'ini kullanabilirsiniz. İşte bir örnek:
    
  ```powershell
  Get-MsolUser -All | Where DisplayName -like "John*" | Sort UserPrincipalName | Select UserPrincipalName | More
  ```

    Bu komut yalnızca Görünen Ad'ın "John" ile başladığı kullanıcı hesaplarını listeler.
    
- Atamak istediğiniz rol
    
    Kullanıcı hesaplarına atayabileceğiniz kullanılabilir rollerin listesini görüntülemek için şu komutu kullanın:
    
  ```powershell
  Get-MsolRole | Sort Name | Select Name,Description
  ```

Hesabın UPN'sine ve rolün adına sahip olduktan sonra, rolü hesaba atamak için şu komutları kullanın:
  
```powershell
$upnName="<The UPN of the account>"
$roleName="<The role name you want to assign to the account>"
Add-MsolRoleMember -RoleMemberEmailAddress $upnName -RoleName $roleName
```

Komutları kopyalayın ve Not Defteri yapıştırın. **$upnName** ve **$roleName** değişkenleri için. Açıklama metnini değerleriyle değiştirin. \< and > Karakterleri kaldırın ancak tırnak işaretlerini koruyun. Değiştirilen satırları çalıştırmak üzere Windows PowerShell penceresi için Microsoft Azure Active Directory Modülüne yapıştırın. Alternatif olarak, WINDOWS POWERSHELL ISE'yi kullanabilirsiniz.
  
Aşağıda tamamlanmış bir komut kümesi örneği verilmişti:
  
```powershell
$upnName="scottw@contoso.com"
$roleName="SharePoint Service Administrator"
Add-MsolRoleMember -RoleMemberEmailAddress $upnName -RoleName $roleName
```

### <a name="multiple-role-changes"></a>Birden çok rol değişikliği

Birden çok rol değişikliği için aşağıdaki bilgileri belirleyin:
  
- Yapılandırmak istediğiniz kullanıcı hesapları. Görüntü adları veya UPN'ler kümesini toplamak için önceki bölümdeki yöntemleri kullanabilirsiniz.
    
- Her kullanıcı hesabına atamak istediğiniz roller. Kullanıcı hesaplarına atayabileceğiniz kullanılabilir rollerin listesini görüntülemek için şu komutu kullanın:
    
  ```powershell
  Get-MsolRole | Sort Name | Select Name,Description
  ```

Ardından görünen ad veya UPN ve rol adı alanlarını içeren bir virgülle ayrılmış değer (CSV) metin dosyası oluşturun. Bunu Microsoft Excel kolayca yapabilirsiniz.

Görünen adlar için bir örnek aşağıda verilmişti:
  
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

UPN'ler için bir örnek aşağıda verilmiştir:
  
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

- [PowerShell ile Microsoft 365 kullanıcı hesaplarını, lisanslarını ve gruplarını yönetme](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
- [PowerShell ile Microsoft 365’i yönetme](manage-microsoft-365-with-microsoft-365-powershell.md)
- [Microsoft 365 için PowerShell ile Kullanmaya başlayın](getting-started-with-microsoft-365-powershell.md)
