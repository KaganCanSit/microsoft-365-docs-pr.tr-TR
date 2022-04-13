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
description: Microsoft 365 kuruluşunuz için Office eklentileri dağıtmanıza ve yönetmenize yardımcı olması için Merkezi Dağıtım PowerShell cmdlet'lerini kullanın.
ms.openlocfilehash: 9f9a3e36c6e1c76d99d8abb7dc47f97a04541322
ms.sourcegitcommit: 195e4734d9a6e8e72bd355ee9f8bca1f18577615
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/13/2022
ms.locfileid: "64824750"
---
# <a name="use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins"></a>Eklentileri yönetmek için Merkezi Dağıtım PowerShell cmdlet'lerini kullanma

Microsoft 365 genel yöneticisi olarak, Merkezi Dağıtım özelliği aracılığıyla kullanıcılara Office eklentileri dağıtabilirsiniz (bkz. [Yönetim merkezinde Office Eklentileri dağıtma](../admin/manage/manage-deployment-of-add-ins.md). Microsoft 365 yönetim merkezi aracılığıyla Office eklentileri dağıtmanın yanı sıra Microsoft PowerShell'i de kullanabilirsiniz. [Windows PowerShell için O365 Merkezi Add-In Dağıtım Modülünü](https://www.powershellgallery.com/packages/O365CentralizedAddInDeployment) yükleyin.

Modülü indirdikten sonra normal bir Windows PowerShell penceresi açın ve aşağıdaki cmdlet'i çalıştırın:

```powershell
 Import-Module -Name O365CentralizedAddInDeployment
```

## <a name="connect-using-your-admin-credentials"></a>Yönetici kimlik bilgilerinizi kullanarak Bağlan

Merkezi Dağıtım cmdlet'lerini kullanabilmeniz için önce oturum açmanız gerekir.

1. PowerShell'i başlatın.

2. Şirket yöneticisi kimlik bilgilerinizi kullanarak PowerShell'e Bağlan. Aşağıdaki cmdlet'i çalıştırın.

  ```powershell
  Connect-OrganizationAddInService
  ```

3. **Kimlik Bilgilerini Girin** sayfasında, Microsoft 365 **Kullanıcı Yöneticisi** veya **Genel yönetici** kimlik bilgilerinizi girin. Alternatif olarak, kimlik bilgilerinizi doğrudan cmdlet'ine girebilirsiniz.

    Şirket yöneticisi kimlik bilgilerinizi PSCredential nesnesi olarak belirterek aşağıdaki cmdlet'i çalıştırın.

  ```powershell
  $secpasswd = ConvertTo-SecureString "MyPassword" -AsPlainText -Force
  $mycredentials = New-Object System.Management.Automation.PSCredential ("serviceaccount@contoso.com", $secpasswd)
  Connect-OrganizationAddInService -Credential $mycredentials
  ```

> [!NOTE]
> PowerShell kullanma hakkında daha fazla bilgi için bkz. [PowerShell ile Microsoft 365 için Bağlan](./connect-to-microsoft-365-powershell.md).

## <a name="upload-an-add-in-manifest"></a>Eklenti bildirimi Upload

Dosya konumu veya URL olabilecek bir yoldan eklenti bildirimini karşıya yüklemek için **New-OrganizationAdd-In cmdlet'ini** çalıştırın. Aşağıdaki örnekte  _, ManifestPath_ parametresinin değeri için bir dosya konumu gösterilmektedir.

```powershell
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

Aşağıdaki örnekte gösterildiği gibi, bir eklentiyi karşıya yüklemek ve _üyeler parametresini_ kullanarak doğrudan kullanıcılara veya gruplara atamak için **New-OrganizationAdd-In** cmdlet'ini de çalıştırabilirsiniz. Üyelerin e-posta adreslerini virgülle ayırın.

```powershell
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US' -Members  'KathyBonner@contoso.com', 'MaxHargrave@contoso.com'
```

## <a name="upload-an-add-in-from-the-office-store"></a>Office Store'dan bir eklenti Upload

Office Store'dan bir bildirim yüklemek için **New-OrganizationAddIn** cmdlet'ini çalıştırın.

Aşağıdaki örnekte **, New-OrganizationAddIn** cmdlet'i bir Birleşik Devletler konumu ve içerik pazarı için eklentinin AssetId değerini belirtir.

```powershell
New-OrganizationAddIn -AssetId 'WA104099688' -Locale 'en-US' -ContentMarket 'en-US'
```

_AssetId_ parametresinin değerini belirlemek için, eklentinin Office Store web sayfasının URL'sinden kopyalayabilirsiniz. AssetId'ler her zaman "WA" ile başlar ve ardından bir sayı gelir. Örneğin, önceki örnekte WA104099688 AssetId değerinin kaynağı eklentinin Office Store web sayfası URL'sidir: [https://store.office.com/en-001/app.aspx?assetid=WA104099688](https://store.office.com/en-001/app.aspx?assetid=WA104099688).

_Locale_ parametresi ve _ContentMarket_ parametresinin değerleri aynıdır ve eklentiyi yüklemeye çalıştığınız ülkeyi/bölgeyi gösterir. Biçim en-US, fr-FR şeklindedir. ve benzeri.

> [!NOTE]
> Office Store'dan yüklenen eklentiler, Office Store'da kullanıma sunulan en son güncelleştirmeden sonra birkaç gün içinde otomatik olarak güncelleştirilir.

## <a name="get-details-of-an-add-in"></a>Eklentinin ayrıntılarını alma

Aşağıda gösterildiği gibi **Get-OrganizationAddIn** cmdlet'ini çalıştırarak bir eklentinin ürün kimliğini içeren kiracıya yüklenen tüm eklentilerin ayrıntılarını alın.

```powershell
Get-OrganizationAddIn
```

Ayrıntıları almak istediğiniz eklentiyi belirtmek için **Get-OrganizationAddIn** cmdlet'ini  _ProductId_ parametresi için bir değerle çalıştırın.

```powershell
Get-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122
```

Tüm eklentilerin ve atanan kullanıcı ve grupların tüm ayrıntılarını almak için, aşağıdaki örnekte gösterildiği gibi **Get-OrganizationAddIn** cmdlet'inin çıktısını Format-List cmdlet'ine yöneltin.

```powershell
foreach($G in (Get-organizationAddIn)){Get-OrganizationAddIn -ProductId $G.ProductId | Format-List}
```

## <a name="turn-on-or-turn-off-an-add-in"></a>Eklentiyi açma veya kapatma

Eklentiyi, kendisine atanan kullanıcıların ve grupların artık erişimi kalmaması için kapatmak için **Set-OrganizationAddIn** cmdlet'ini  _ProductId_ parametresiyle ve  _Enabled_ parametresi aşağıdaki örnekte gösterildiği gibi olarak ayarlayın  `$false`.

```powershell
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $false
```

Eklentiyi yeniden açmak için  _Enabled_ parametresi olarak ayarlanmış  `$true`aynı cmdlet'i çalıştırın.

```powershell
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $true
```

## <a name="add-or-remove-users-from-an-add-in"></a>Eklentiye kullanıcı ekleme veya eklentiden kullanıcı kaldırma

Belirli bir eklentiye kullanıcı ve grup eklemek için **Set-OrganizationAddInAssignments** cmdlet'ini  _ProductId_,  _Add_ ve  _Members_ parametreleriyle çalıştırın. Üyelerin e-posta adreslerini virgülle ayırın.

```powershell
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Add -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

Kullanıcıları ve grupları kaldırmak için  _Remove_ parametresini kullanarak aynı cmdlet'i çalıştırın.

```powershell
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Remove -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

Kiracıdaki tüm kullanıcılara bir eklenti atamak için, değeri olarak ayarlanmış  _AssignToEveryone_ parametresini kullanarak aynı cmdlet'i  `$true`çalıştırın.

```powershell
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $true
```

Bir eklentiyi herkese atamamak ve önceden atanan kullanıcılara ve gruplara geri dönmek için, aynı cmdlet'i çalıştırabilir ve değerini `$false`olarak ayarlayarak _AssignToEveryone_ parametresini kapatabilirsiniz.

```powershell
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $false
```

## <a name="update-an-add-in"></a>Eklentiyi güncelleştirme

Bildirimden bir eklentiyi güncelleştirmek için, aşağıdaki örnekte gösterildiği gibi **Set-OrganizationAddIn** cmdlet'ini  _ProductId_,  _ManifestPath_ ve  _Locale_ parametreleriyle çalıştırın.

```powershell
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

> [!NOTE]
> Office Store'dan yüklenen eklentiler, Office Store'da kullanıma sunulan en son güncelleştirmeden sonra birkaç gün içinde otomatik olarak güncelleştirilir.

## <a name="delete-an-add-in"></a>Eklentiyi silme

Bir eklentiyi silmek için aşağıdaki örnekte gösterildiği gibi **Remove-OrganizationAddIn** cmdlet'ini  _ProductId_ parametresiyle çalıştırın.

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

To customize an add-in, run the **Set -OrganizationAddInOverrides** cmdlet with the *ProductId* as a parameter, followed by the tag you want to overwrite and the new value. To find out how to get the *ProductId* see [get details of an add-in](#get-details-of-an-add-in) in this article. For example:

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
| \<IconURL>   </br>| The URL of the image used as the add-in's icon (in admin center). |
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
          <bt:Image id="img16icon" DefaultValue="https://site.com/img.jpg"
    </bt:Images>
</Resources>
```
In this case, the element id for the image is "img16icon" and the value associated with it is "http:<i></i>//site.<i></i>com/img.jpg."

Once you have identified the elements you want to customize, use the following command in Powershell to assign new values to the elements:

```powershell
Set-OrganizationAddInOverrides -Resources @{"ElementID" = "New Value"; "NextElementID" = "Next New Value"}
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

If an add-in has been deployed, it has to be removed from the cache in each computer before it can be customized. To remove an add-in from cache:

1. Navigate to the "Users" folder in C:\
1. Go to your user folder
1. Navigate to AppData\Local\Microsoft\Office and select the folder associated with your version of Office
1. In the *Wef* folder delete the *Manifests* folder.

-->

## <a name="get-detailed-help-for-each-cmdlet"></a>Her cmdlet için ayrıntılı yardım alın

Get-help cmdlet'ini kullanarak her cmdlet için ayrıntılı yardıma bakabilirsiniz. Örneğin, aşağıdaki cmdlet Remove-OrganizationAddIn cmdlet'i hakkında ayrıntılı bilgi sağlar.

```powershell
Get-help Remove-OrganizationAddIn -Full
```
