---
title: PowerShell SharePoint Online kullanıcılarını ve gruplarını yönetme
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 07/17/2020
audience: Admin
ms.topic: hub-page
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
- SPO_Content
- seo-marvel-apr2020
ms.assetid: d0d3877a-831f-4744-96b0-d8167f06cca2
description: Bu makalede, Microsoft 365 Online kullanıcılarını, gruplarını ve sitelerini yönetmek için SharePoint Için PowerShell'in nasıl kullanıldığı hakkında bilgi edinebilirsiniz.
ms.openlocfilehash: 10991c2ac065331ab8eff3e782cecbdbcc5d034b
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62985579"
---
# <a name="manage-sharepoint-online-users-and-groups-with-powershell"></a>PowerShell SharePoint Online kullanıcılarını ve gruplarını yönetme

*Bu makale hem son hem de Microsoft 365 Kurumsal hem de Office 365 Kurumsal.*

Çok sayıda kullanıcı hesabı SharePoint gruplarla çalışan ve bunları yönetmek için daha kolay bir yol isteyen bir SharePoint Online yöneticisiyseniz, bu hesapları yönetmek için PowerShell'i Microsoft 365.

Başlamadan önce, bu konudaki yordamlar için SharePoint Online'a bağlanmanız gerekir. Yönergeler için bkz. [Bağlan Online PowerShell SharePoint e yükleme](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online)

## <a name="get-a-list-of-sites-groups-and-users"></a>Sitelerin, grupların ve kullanıcıların listesini al

Kullanıcıları ve grupları yönetmeye başlamadan önce, sitelerinizi, gruplarınızı ve kullanıcılarınızı listelersiniz. Daha sonra bu makaledeki örnekte yer alan bu bilgilerle çalışabilirsiniz.

Bu komutla kiracınıza sitelerin listesini almak için:

```powershell
Get-SPOSite
```

Bu komutu kullanarak kiracınıza grup listesini almak için:

```powershell
Get-SPOSite | ForEach {Get-SPOSiteGroup -Site $_.Url} | Format-Table
```

Bu komutu kullanarak kiracınıza kullanıcıların listesini ekleyin:

```powershell
Get-SPOSite | ForEach {Get-SPOUser -Site $_.Url}
```

## <a name="add-a-user-to-the-site-collection-administrators-group"></a>Site Koleksiyonu Yöneticileri grubuna kullanıcı ekleme

`Set-SPOUser` Cmdlet'i kullanarak site koleksiyonunda Site Koleksiyonu Yöneticileri listesine kullanıcı ekleyebilirsiniz.

```powershell
$tenant = "<tenant name, such as litwareinc for litwareinc.com>"
$site = "<site name>"
$user = "<user account name, such as opalc>"
Set-SPOUser -Site https://$tenant.sharepoint.com/sites/$site -LoginName $user@$tenant.com -IsSiteCollectionAdmin $true
 ```

Bu komutları kullanmak için, tırnak içindeki her şeyi, tırnak içindeki < > adlarla değiştirin.

Örneğin, bu komut kümesi Opal Cast her ikisinde de (kullanıcı adı opalc) ContosoTest site koleksiyonunda Site Koleksiyonu Yöneticileri listesine eklenir:

```powershell
$tenant = "contoso"
$site = "contosotest"
$user = "opalc"
Set-SPOUser -Site https://$tenant.sharepoint.com/sites/$site -LoginName $user@$tenant.com -IsSiteCollectionAdmin $true
```

Bu komutları kopyalayıp Not Defteri'a yapıştırabilirsiniz, $tenant, $site ve $user için değişken değerlerini ortamından gerçek değerlerle değiştirebilir ve sonra da bu komutları çalıştırmak için SharePoint Çevrimiçi Yönetim Kabuğu pencerenize yapıştırabilirsiniz.

## <a name="add-a-user-to-other-site-collection-groups"></a>Başka site koleksiyonu gruplarına kullanıcı ekleme

Bu görevde, cmdlet'i `Add-SPOUser` kullanarak site koleksiyonunda yer alan SharePoint bir kullanıcı ekley ekle olamız.

```powershell
$tenant = "<tenant name, such as litwareinc for litwareinc.com>"
$site = "<site name>"
$user = "<user account name, such as opalc>"
$group = "<group name name, such as Auditors>"
Add-SPOUser -Group $group -LoginName $user@$tenant.com -Site https://$tenant.sharepoint.com/sites/$site

```

Örneğin, glen Rife'yi (kullanıcı adı glenr) ContosoTest site koleksiyonunda, contoso kiraya bağlı Denetçiler grubuna ekalım:

```powershell
$tenant = "contoso"
$site = "contosotest"
$user = "glenr"
$group = "Auditors"
Add-SPOUser -Group $group -LoginName $user@$tenant.com -Site https://$tenant.sharepoint.com/sites/$site
```

## <a name="create-a-site-collection-group"></a>Site koleksiyonu grubu oluşturma

`New-SPOSiteGroup` Cmdlet'i kullanarak yeni bir grup SharePoint ve site koleksiyonuna eklersiniz.

```powershell
$tenant = "<tenant name, such as litwareinc for litwareinc.com>"
$site = "<site name>"
$group = "<group name name, such as Auditors>"
$level = "<permission level, such as View Only>"
New-SPOSiteGroup -Group $group -PermissionLevels $level -Site https://$tenant.sharepoint.com/sites/$site
```

İzin düzeyleri gibi grup özellikleri daha sonra cmdlet kullanılarak `Set-SPOSiteGroup` güncelleştirilebilir.

Örneğin, contoso kiraya alınan contosotest site koleksiyonuna Yalnızca Görüntüleme izinleri olan Denetçiler grubunu ekalım:

```powershell
$tenant = "contoso"
$site = "contosotest"
$group = "Auditors"
$level = "View Only"
New-SPOSiteGroup -Group $group -PermissionLevels $level -Site https://$tenant.sharepoint.com/sites/$site
```

## <a name="remove-users-from-a-group"></a>Gruptan kullanıcı kaldırma

Bazen bir siteden, hatta tüm sitelerden kullanıcı kaldırmanız gerekir. Çalışan belki bir bölümden diğerine taşınır veya şirketten ayrılır. Bunu kullanıcı arabiriminde bir çalışan için kolayca yapabilirsiniz, ancak bir siteden diğerine tam bir bölme taşımak zorundayken bu kolay değildir.

Bununla birlikte, SharePoint Online Yönetim Kabuğu ve CSV dosyalarıyla, bu hızlı ve kolaydır. Bu görev içinde, site koleksiyonu Windows PowerShell grubundan bir kullanıcı kaldırmak için Kullanıcı Grubu Yöneticisi'ne kullanıyabilirsiniz. Ardından bir CSV dosyası kullanır ve farklı sitelerden çok sayıda kullanıcı kaldırırsiniz.

Komut söz dizimi'ne bakılamız için, yalnızca site koleksiyonu grubundan tek bir kullanıcı Microsoft 365'ı kaldırmak için 'Remove-SPOUser' cmdlet'ini kullanıyoruz. Söz dizimi şöyle olur:

```powershell
$tenant = "<tenant name, such as litwareinc for litwareinc.com>"
$site = "<site name>"
$user = "<user account name, such as opalc>"
$group = "<group name name, such as Auditors>"
Remove-SPOUser -LoginName $user@$tenant.com -Site https://$tenant.sharepoint.com/sites/$site -Group $group
```

Örneğin, ahmet Ahmet'i contoso kiralığında bulunan contosotest site koleksiyonunda bulunan site koleksiyonu Denetçiler grubundan kaldıralım:

```powershell
$tenant = "contoso"
$site = "contosotest"
$user = "bobbyo"
$group = "Auditors"
Remove-SPOUser -LoginName $user@$tenant.com -Site https://$tenant.sharepoint.com/sites/$site -Group $group
```

Ahmet'i o anda içinde olduğu tüm gruplardan çıkarmak istediğimi varsayalım. Bunu şu şekilde yapabiliriz:

```powershell
$tenant = "contoso"
$user = "bobbyo"
Get-SPOSite | ForEach {Get-SPOSiteGroup –Site $_.Url} | ForEach {Remove-SPOUser -LoginName $user@$tenant.com -Site &_.Url}
```

> [!WARNING]
> Bu yalnızca bir örnektir. Örneğin kullanıcı şirketten ayrıldığında gibi, her gruptan bir kullanıcı gerçekten kaldırmak zorunda olmadığınız sürece bu komutu çalıştırmanız gerekir.

## <a name="automate-management-of-large-lists-of-users-and-groups"></a>Büyük kullanıcı ve grup listelerinin yönetimini otomatikleştirme

SharePoint sitelerine çok sayıda hesap eklemek ve onlara izin vermek için Microsoft 365 yönetim merkezi, tek tek PowerShell komutlarını veya PowerShell'i bir CSV dosyası kullanabilirsiniz. Bu seçimler arasında, bu görevi otomatikleştirmenin en hızlı yolu CSV dosyasıdır.

Temel işlem, betiğin gerektiği parametrelere karşılık gelen üstbilgiler (sütunlar) içeren bir CSV Windows PowerShell oluşturmaktır. Bu tür bir listeyi Excel csv dosyası olarak dışarı aktarabilirsiniz. Ardından, CSV dosyasındaki Windows PowerShell (satırlar) üzerinden kullanıcıları gruplara ve grupları sitelere eklemek için bir e-posta betiği kullanırsanız.

Örneğin, bir grup site koleksiyonu, grup ve izin tanımlamak için bir CSV dosyası oluşturabilirsiniz. Ardından, grupları kullanıcılarla doldurmak için bir CSV dosyası oluştur aynı şekilde oluruz. Son olarak, grupları oluşturan ve doldurmak için Windows PowerShell bir komut dosyası oluşturur ve bu betiği çalıştırın.

İlk CSV dosyası, bir veya birden çok site koleksiyonuna bir veya daha fazla grup ekler ve şu yapıya sahip olur:

Üst bilgi:

```powershell
Site,Group,PermissionLevels
```

Öğe:

```powershell
https://tenant.sharepoint.com/sites/site,group,level
```

İşte örnek bir dosya:

```powershell
Site,Group,PermissionLevels
https://contoso.sharepoint.com/sites/contosotest,Contoso Project Leads,Full Control
https://contoso.sharepoint.com/sites/contosotest,Contoso Auditors,View Only
https://contoso.sharepoint.com/sites/contosotest,Contoso Designers,Design
https://contoso.sharepoint.com/sites/TeamSite01,XT1000 Team Leads,Full Control
https://contoso.sharepoint.com/sites/TeamSite01,XT1000 Advisors,Edit
https://contoso.sharepoint.com/sites/Blog01,Contoso Blog Designers,Design
https://contoso.sharepoint.com/sites/Blog01,Contoso Blog Editors,Edit
https://contoso.sharepoint.com/sites/Project01,Project Alpha Approvers,Full Control
```

İkinci CSV dosyası bir veya birden çok gruba bir veya daha fazla kullanıcı ekler ve şu yapıya sahip olur:

Üst bilgi:

```powershell
Group,LoginName,Site
```

Öğe:

```powershell
group,login,https://tenant.sharepoint.com/sites/site
```

İşte örnek bir dosya:

```powershell
Group,LoginName,Site
Contoso Project Leads,bobbyo@contoso.com,https://contoso.sharepoint.com/sites/contosotest
Contoso Auditors,allieb@contoso.com,https://contoso.sharepoint.com/sites/contosotest
Contoso Designers,bonniek@contoso.com,https://contoso.sharepoint.com/sites/contosotest
XT1000 Team Leads,dorenap@contoso.com,https://contoso.sharepoint.com/sites/TeamSite01
XT1000 Advisors,garthf@contoso.com,https://contoso.sharepoint.com/sites/TeamSite01
Contoso Blog Designers,janets@contoso.com,https://contoso.sharepoint.com/sites/Blog01
Contoso Blog Editors,opalc@contoso.com,https://contoso.sharepoint.com/sites/Blog01
Project Alpha Approvers,robinc@contoso.com,https://contoso.sharepoint.com/sites/Project01
```

Sonraki adım için, iki CSV dosyasının sürücünize kaydedilmiş olması gerekir. Hem CSV dosyalarını hem de izinleri ve grup üyeliğini kullanan örnek komutlar şöyledir:

```powershell
Import-Csv C:\O365Admin\GroupsAndPermissions.csv | ForEach {New-SPOSiteGroup -Group $_.Group -PermissionLevels $_.PermissionLevels -Site $_.Site}
Import-Csv C:\O365Admin\Users.csv | ForEach {Add-SPOUser -Group $_.Group –LoginName $_.LoginName -Site $_.Site}
```

Betik, CSV dosya içeriğini içeri aktarır ve **New-SPOSiteGroup** ve **Add-SPOUser** komutlarının parametrelerini doldurmak için sütunlarda yer alan değerleri kullanır. Örneğimizde, bunu C sürücüsünde yer alanO365Admin klasörüne kaydedtik, ancak istediğiniz yere kaydedebilirsiniz.

Şimdi de aynı CSV dosyasını kullanarak farklı sitelerde yer alan birkaç grup için bir grup kişiyi kaldırabilirsiniz. İşte örnek bir komut:

```powershell
Import-Csv C:\O365Admin\Users.csv | ForEach {Remove-SPOUser -LoginName $_.LoginName -Site $_.Site -Group $_.Group}
```

## <a name="generate-user-reports"></a>Kullanıcı raporları oluşturma

Birkaç site için basit bir rapor almak ve bu sitelerin kullanıcılarını, onların izin düzeyini ve diğer özelliklerini görüntülemek istiyor olabilir. Söz dizimi şöyledir:

```powershell
$tenant = "<tenant name, such as litwareinc for litwareinc.com>"
$site = "<site name>"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site | select * | Format-table -Wrap -AutoSize | Out-File c\UsersReport.txt -Force -Width 360 -Append
```

Bu, bu üç sitenin verilerini alıp yerel sürücünizden bir metin dosyasına yazar. –Ekle parametresi, var olan dosyaya yeni içerik ekleyecek.

Örneğin, Contoso1 kiracısı için ContosoTest, Ekip Sitesi01 ve Project01 sitelerinde bir rapor çalıştıralım:

```powershell
$tenant = "contoso"
$site = "contosotest"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site | Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
$site = "TeamSite01"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site |Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
$site = "Project01"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site | Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
```

Yalnızca veri değişkenlerini değiştirmemiz **$site** unutmayın. En **$tenant** değişkeni, komutun üç çalıştırması boyunca değerini tutar.

Öte yandan, bunu her site için yapmak istediniz ne olacak? Bu komutu kullanarak tüm web sitelerini yazmadan bunu kullanabilirsiniz:

```powershell
Get-SPOSite | ForEach {Get-SPOUser –Site $_.Url} | Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
```

Bu rapor oldukça basittir ve daha ayrıntılı bilgiler içeren daha özel raporlar veya raporlar oluşturmak için daha fazla kod  eklersiniz. Ancak bu size, çevrimiçi ortamda kullanıcıları yönetmek için SharePoint Çevrimiçi Yönetim Kabuğu'SharePoint vermalıdır.

## <a name="see-also"></a>Ayrıca bkz.

[Bağlan Online PowerShell SharePoint e geri ödeme](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online)

[PowerShell SharePoint Online'da yönetme](create-sharepoint-sites-and-add-users-with-powershell.md)

[PowerShell Microsoft 365'i yönetme](manage-microsoft-365-with-microsoft-365-powershell.md)

[Microsoft 365 için PowerShell ile çalışmaya Microsoft 365](getting-started-with-microsoft-365-powershell.md)
