---
title: Eklentileri yönetmek için Merkezi Dağıtım PowerShell cmdlet'lerini kullanma
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 1/24/2020
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- BCS160
f1.keywords:
- NOCSH
ms.assetid: 94f4e86d-b8e5-42dd-b558-e6092f830ec9
ms.custom:
- seo-marvel-apr2020
description: Merkezi Dağıtım PowerShell cmdlet'lerini kullanarak, bu Office eklentilerin dağıtımını ve yönetimine yardımcı Microsoft 365 kullanın.
ms.openlocfilehash: acdda1c30dbd0a19762040140b1bb3bf1a7715d4
ms.sourcegitcommit: 0ee2dabe402d44fecb6856af98a2ef7720d25189
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/09/2021
ms.locfileid: "62996162"
---
# <a name="use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins"></a>Eklentileri yönetmek için Merkezi Dağıtım PowerShell cmdlet'lerini kullanma

Genel Microsoft 365 yöneticisi olarak, Office eklentileri Merkezi Dağıtım özelliği aracılığıyla dağıtabilirsiniz (bkz. [Yönetim merkezinde Office Eklentileri Dağıtma](../admin/manage/manage-deployment-of-add-ins.md). Microsoft PowerShell Office eklentilerinin dağıtım Microsoft 365 yönetim merkezi, ayrıca Microsoft PowerShell'i de kullanabilirsiniz. [O365 Merkezi Dağıtım Modülü'Add-In Merkezi Dağıtım Modülü'Windows PowerShell](https://www.powershellgallery.com/packages/O365CentralizedAddInDeployment). 

Modülü indirdikten sonra, normal bir Windows PowerShell penceresi açın ve aşağıdaki cmdlet'i çalıştırın:

```powershell
 Import-Module -Name O365CentralizedAddInDeployment
```
    
## <a name="connect-using-your-admin-credentials"></a>Bağlan kimlik bilgilerinizi kullanarak oturum açma

Merkezi Dağıtım cmdlet'lerini kullanamadan önce oturum açmanız gerekir.
  
1. PowerShell'i başlatma.
    
2. Bağlan yönetici kimlik bilgilerini kullanarak PowerShell'e erişin. Aşağıdaki cmdlet'i çalıştırın.
    
  ```powershell
  Connect-OrganizationAddInService
  ```

3. Kimlik Bilgilerini **Girin sayfasında**, Kullanıcı Yöneticisi Microsoft 365 **Genel** yönetici **kimlik bilgilerinizi** girin. Alternatif olarak, kimlik bilgilerinizi doğrudan cmdlet'e girebilirsiniz. 
    
    Şirket yöneticisi kimlik bilgilerinizi PSCredential nesnesi olarak belirten aşağıdaki cmdlet'i çalıştırın.
    
  ```powershell
  $secpasswd = ConvertTo-SecureString "MyPassword" -AsPlainText -Force
  $mycredentials = New-Object System.Management.Automation.PSCredential ("serviceaccount@contoso.com", $secpasswd)
  Connect-OrganizationAddInService -Credential $mycredentials
  ```

> [!NOTE]
> PowerShell'i kullanma hakkında daha fazla bilgi için bkz[. Bağlan Microsoft 365 PowerShell'i kullanma.](./connect-to-microsoft-365-powershell.md) 
  
## <a name="upload-an-add-in-manifest"></a>Upload bildirimini ekleme

Bir dosya konumu veya URL yolundan karşıya eklenti bildirimi yüklemek için **New-OrganizationAdd-In** cmdlet'ini çalıştırın. Aşağıdaki örnekte, ManifestPath parametresi değeri için bir  _dosya konumu_ gösterir. 
  
```powershell
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

Ayrıca, aşağıdaki örnekte gösterildiği gibi, bir eklentiyi _Members_ parametresini kullanarak karşıya yüklemek ve doğrudan kullanıcılara veya gruplara atamak için **New-OrganizationAdd-In** cmdlet'ini de çalıştırabilirsiniz. Üyelerin e-posta adreslerini virgülle birbirinden ayırabilirsiniz. 
  
```powershell
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US' -Members  'KathyBonner@contoso.com', 'MaxHargrave@contoso.com'
```

## <a name="upload-an-add-in-from-the-office-store"></a>Upload Mağazası'dan bir Office ekleme

Office Store'dan karşıya bildirim yüklemek için **New-OrganizationAddIn** cmdlet'ini çalıştırın.
  
Aşağıdaki örnekte **New-OrganizationAddIn** cmdlet'i, Amerika Birleşik Devletleri konumu ve içerik pazarı için bir eklentinin AssetId'nizi belirtir.
  
```powershell
New-OrganizationAddIn -AssetId 'WA104099688' -Locale 'en-US' -ContentMarket 'en-US'
```

_AssetId parametresinin değerini belirlemek_ için, eklentiye uygun Office Mağazası web sayfasının URL'sinde bunu kopya edebilirsiniz. AssetId'ler her zaman "WA" ile ve ardından bir numarayla başlar. Örneğin, önceki örnekte WA104099688 AssetId değerinin kaynağı, eklentinin Office Mağazası web sayfası URL'sinin kaynağıdır: [https://store.office.com/en-001/app.aspx?assetid=WA104099688](https://store.office.com/en-001/app.aspx?assetid=WA104099688).
  
_Locale_ ve _ContentMarket_ parametresinin değerleri aynıdır ve eklentiyi yüklemek istediğiniz ülkeyi/bölgeyi gösterir. Bu en-US, fr-FR biçimindedir. vb. 
  
> [!NOTE]
> Office Mağazası'dan yüklenen eklentiler, Office Mağazası'da bulunan en son güncelleştirmeden sonra birkaç gün içinde otomatik Office güncelleştirmesi yapılır. 
  
## <a name="get-details-of-an-add-in"></a>Eklenti ayrıntılarını al

Kiracıya yüklenen tüm eklentilerin ürün kimliği dahil olmak için aşağıda gösterildiği gibi **Get-OrganizationAddIn** cmdlet'ini çalıştırın.
  
```powershell
Get-OrganizationAddIn
```

Ayrıntıları **almak istediğiniz eklentiyi belirtmek için, Get-OrganizationAddIn** cmdlet'ini  _ProductId_ parametresi değeriyle çalıştırın. 
  
```powershell
Get-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122
```

Tüm eklentilerin tüm ayrıntılarının yanı sıra atanan kullanıcı ve grupları da almak için, **Get-OrganizationAddIn** cmdlet'inin çıktısını Format-List örnekte gösterildiği gibi Format-List cmdlet'ine dışarıyın.
  
```powershell
foreach($G in (Get-organizationAddIn)){Get-OrganizationAddIn -ProductId $G.ProductId | Format-List}
```

## <a name="turn-on-or-turn-off-an-add-in"></a>Eklentiyi açma veya kapatma

Eklentiyi kapatarak buna atanan kullanıcıların ve grupların erişimlerini yitirecek şekilde kapatmak için, aşağıdaki örnekte gösterildiği gibi **Set-OrganizationAddIn** cmdlet'ini  _ProductId_ parametresi ve  _Enabled_  `$false`parametresi olarak ayarlanmış ile çalıştırın.
  
```powershell
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $false
```

Bir eklentiyi yeniden açmak için, aynı cmdlet'i  _Enabled parametresi olarak ayarlanmış_ olarak çalıştırın  `$true`.
  
```powershell
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $true
```

## <a name="add-or-remove-users-from-an-add-in"></a>Eklentiye kullanıcı ekleme veya eklentiden kullanıcı kaldırma

Belirli bir eklentiye kullanıcı ve grup eklemek için **, Set-OrganizationAddInAssignments** cmdlet'ini  _ProductId_,  _Add_ ve  _Members parametreleriyle_ çalıştırın. Üyelerin e-posta adreslerini virgülle birbirinden ayırabilirsiniz. 
  
```powershell
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Add -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

Kullanıcıları ve grupları kaldırmak için, aynı cmdlet'i  _Remove parametresini kullanarak_ çalıştırın. 
  
```powershell
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Remove -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

Bir eklentiyi kiracının tüm kullanıcılarına atamak için,  _assignToEveryone_ parametresinde değeri 'a ayarlanmış olan aynı cmdlet'i çalıştırın  `$true`.
  
```powershell
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $true
```

Bir eklentiyi herkese atamama ve önceden atanmış kullanıcı ve gruplara geri dönme işlemi yapmak için,  _assignToEveryone_ parametresinin değerini ' ayarerek aynı cmdlet'i çalıştırabilir ve kapatabilirsiniz  `$false`.
  
```powershell
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $false
```

## <a name="update-an-add-in"></a>Eklentiyi güncelleştirme

Bir eklentiyi bildirimden güncelleştirmek için, **Set-OrganizationAddIn** cmdlet'ini  _ProductId_,  _ManifestPath_ ve  _Locale_ parametreleriyle aşağıdaki örnekte gösterildiği gibi çalıştırın. 
  
```powershell
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

> [!NOTE]
> Office Mağazası'dan yüklenen eklentiler, Office Mağazası'da bulunan en son güncelleştirmeden sonra birkaç gün içinde otomatik Office güncelleştirmesi yapılır. 
  
## <a name="delete-an-add-in"></a>Eklentiyi silme

Bir eklentiyi silmek için, **aşağıdaki örnekte gösterildiği gibi, Remove-OrganizationAddIn** cmdlet'ini  _ProductId_ parametresiyle çalıştırın. 
  
```powershell
Remove-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122
```

<!--
## Customize Microsoft Store add-ins for your organization

You must customize the add-in before you deploy it to your organization. Add-ins older than version 1.1 are not supported by this feature. 

We recommend that you deploy a customized add-in  to yourself first to make sure it works as expected before you deploy it to your entire organization.

Note also the following restrictions:
- All URLs must be absolute (include http or https) and valid.
- *DisplayName* must not exceed 125 characters 
- *DisplayName*, *Resources* and *AppDomains* must not include the following characters: 
 
    - \<
    -  \>
    -  ;
    -  =   

If you want to customize an add-in that has been deployed, you have to uninstall it in the admin center, and see [remove an add-in from local cache](#remove-an-add-in-from-local-cache) for steps to remove it from each computer it has been deployed to.

To customize an add-in, run the **Set –OrganizationAddInOverrides** cmdlet with the *ProductId* as a parameter, followed by the tag you want to overwrite and the new value. To find out how to get the *ProductId* see [get details of an add-in](#get-details-of-an-add-in) in this article. For example:

```powershell
 Set-OrganizationAddInOverrides -ProductId 5b31b349-2c41-4f94-b720-6ee40349d391 -IconUrl "https://site.com/img.jpg" 
```
To customize multiple tags for an add-in, add those tags to the commandline:

```powershell
Set-OrganizationAddInOverrides -ProductId 5b31b349-2c41-4f94-b720-6ee40349d391 -Hosts h1, 2 -DisplayName "New DocuSign W" -IconUrl "https://site.com/img.jpg" 
```

> [!IMPORTANT]
> You must apply multiple customized tags to one add-in as one command. If you customize tags one by one, only the last customization will be applied. Additionally, if you customize a tag by mistake, you must remove all customizations and start over.

### Tags you can customize

| Tag                  | Description          |
| :------------------- | :------------------- |
| \<IconURL>   </br>| The URL of the image used as the add-in’s icon (in admin center). </br> |
| \<DisplayName>| The title of the add-in  (in admin center).|
| \<Hosts>| List of apps that will support the add-in.|
| \<SourceLocation> | The source URL that the add-in will connect to.| 
| \<AppDomains> | A list of domains that the add-in can connect with. | 
| \<SupportURL>| The URL users can use to access help and support. | 
| \<Resources>  | This tag contains a number of elements including titles, tooltips, and icons of different sizes.| 
|
### Customize Resources tag

Any element in the <Resources> tag of the manifest can be customized dynamically. You first need to check the manifest to find the element id to which you want to assign a new value. The <Resources> tag looks like this:

```
<Resources>  
    <bt:Images> 
          <bt:Image id=”img16icon” DefaultValue=”https://site.com/img.jpg” 
    </bt:Images> 
</Resources> 
``` 
In this case, the element id for the image is “img16icon” and the value associated with it is “http:<i></i>//site.<i></i>com/img.jpg.”

Once you have identified the elements you want to customize, use the following command in Powershell to assign new values to the elements:

```powershell
Set-OrganizationAddInOverrides -Resources @{“ElementID” = “New Value”; “NextElementID” = “Next New Value”} 
```

You can customize as many elements with the command as you need to.

### Remove customization from an add-in

The only option currently available for deleting customizations is to delete all of them at once:

```powershell
Remove-OrganizationAddInOverrides -ProductId 5b31b349-2c41-4f94-b720-6ee40349d391 
```

### View add-in customizations

To view a list of applied customizations, run the **Get-OrganizationAddInOverrides** cmdlet. If **Get-OrganizationAddInOverrides** is run without a *ProductId* then a list of all add-ins with applied overrides are returned.  

```powershell
Get-OrganizationAddInOverrides 
```
If ProductId is specified, then a list of overrides applied to that add-in is returned. 

```powershell
Get-OrganizationAddInOverrides -ProductId 5b31b349-2c41-4f94-b720-6ee40349d391 
```

### Remove an add-in from local cache

If an add-in has been deployed, it has to be removed from the cache in each computer before it can be customized. To remive an add-in from cache:

1. Navigate to the “Users” folder in C:\ 
1. Go to your user folder
1. Navigate to AppData\Local\Microsoft\Office and select the folder associated with your version of Office
1. In the *Wef* folder delete the *Manifests* folder.

-->

## <a name="get-detailed-help-for-each-cmdlet"></a>Tüm cmdlet'ler için ayrıntılı yardım

Get-help cmdlet'ini kullanarak tüm cmdlet'ler hakkında ayrıntılı yardım almak için bu cmdlet'i ziyaret edin. Örneğin, aşağıdaki cmdlet, cmdlet'ini Remove-OrganizationAddIn bilgi sağlar.
  
```powershell
Get-help Remove-OrganizationAddIn -Full
```
