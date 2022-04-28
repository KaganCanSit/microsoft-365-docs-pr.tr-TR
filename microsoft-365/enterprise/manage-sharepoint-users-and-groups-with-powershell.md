---
title: PowerShell ile SharePoint Çevrimiçi kullanıcıları ve grupları yönetme
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 07/17/2020
audience: Admin
ms.topic: landing-page
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
description: Bu makalede, SharePoint Çevrimiçi kullanıcıları, grupları ve siteleri yönetmek üzere Microsoft 365 için PowerShell'i kullanmayı öğrenin.
ms.openlocfilehash: 78c829e476c63e435d9543b3a4175cdbbccb76e8
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65100687"
---
# <a name="manage-sharepoint-online-users-and-groups-with-powershell"></a>PowerShell ile SharePoint Çevrimiçi kullanıcıları ve grupları yönetme

*Bu makale hem Microsoft 365 Kurumsal hem de Office 365 Kurumsal için geçerlidir.*

Büyük kullanıcı hesapları veya grupları listeleriyle çalışan ve bunları yönetmek için daha kolay bir yol isteyen SharePoint Online yöneticisiyseniz, Microsoft 365 için PowerShell'i kullanabilirsiniz.

Başlamadan önce, bu makaledeki yordamlar SharePoint Online'a bağlanmanızı gerektirir. Yönergeler için bkz. [çevrimiçi PowerShell SharePoint Bağlan](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online)

## <a name="get-a-list-of-sites-groups-and-users"></a>Sitelerin, grupların ve kullanıcıların listesini alma

Kullanıcıları ve grupları yönetmeye başlamadan önce sitelerinizin, gruplarınızın ve kullanıcılarınızın listelerini almanız gerekir. Daha sonra, bu makaledeki örnekle çalışmak için bu bilgileri kullanabilirsiniz.

Şu komutla kiracınızdaki sitelerin listesini alın:

```powershell
Get-SPOSite
```

Şu komutla kiracınızdaki grupların listesini alın:

```powershell
Get-SPOSite | ForEach {Get-SPOSiteGroup -Site $_.Url} | Format-Table
```

Şu komutla kiracınızdaki kullanıcıların listesini alın:

```powershell
Get-SPOSite | ForEach {Get-SPOUser -Site $_.Url}
```

## <a name="add-a-user-to-the-site-collection-administrators-group"></a>Site Koleksiyonu Yöneticileri grubuna kullanıcı ekleme

Bir site koleksiyonundaki `Set-SPOUser` Site Koleksiyonu Yöneticileri listesine bir kullanıcı eklemek için cmdlet'ini kullanırsınız.

```powershell
$tenant = "<tenant name, such as litwareinc for litwareinc.com>"
$site = "<site name>"
$user = "<user account name, such as opalc>"
Set-SPOUser -Site https://$tenant.sharepoint.com/sites/$site -LoginName $user@$tenant.com -IsSiteCollectionAdmin $true
 ```

Bu komutları kullanmak için tırnak içindeki < ve > karakterleri dahil olmak üzere her şeyi doğru adlarla değiştirin.

Örneğin, bu komut kümesi Contoso kiracısında ContosoTest site koleksiyonundaki Site Koleksiyonu Yöneticileri listesine Opal Castillo'yu (kullanıcı adı opalc) ekler:

```powershell
$tenant = "contoso"
$site = "contosotest"
$user = "opalc"
Set-SPOUser -Site https://$tenant.sharepoint.com/sites/$site -LoginName $user@$tenant.com -IsSiteCollectionAdmin $true
```

Bu komutları kopyalayıp Not Defteri yapıştırabilir, $tenant, $site ve $user değişken değerlerini ortamınızdaki gerçek değerlerle değiştirebilir ve ardından bunları çalıştırmak için SharePoint Çevrimiçi Yönetim Kabuğu pencerenize yapıştırabilirsiniz.

## <a name="add-a-user-to-other-site-collection-groups"></a>Diğer site koleksiyonu gruplarına kullanıcı ekleme

Bu görevde, bir site koleksiyonundaki `Add-SPOUser` SharePoint grubuna kullanıcı eklemek için cmdlet'ini kullanacağız.

```powershell
$tenant = "<tenant name, such as litwareinc for litwareinc.com>"
$site = "<site name>"
$user = "<user account name, such as opalc>"
$group = "<group name name, such as Auditors>"
Add-SPOUser -Group $group -LoginName $user@$tenant.com -Site https://$tenant.sharepoint.com/sites/$site

```

Örneğin, contoso kiracısında ContosoTest site koleksiyonundaki Denetçiler grubuna Glen Rife (kullanıcı adı glenr) ekleyelim:

```powershell
$tenant = "contoso"
$site = "contosotest"
$user = "glenr"
$group = "Auditors"
Add-SPOUser -Group $group -LoginName $user@$tenant.com -Site https://$tenant.sharepoint.com/sites/$site
```

## <a name="create-a-site-collection-group"></a>Site koleksiyonu grubu oluşturma

Cmdlet'ini `New-SPOSiteGroup` kullanarak yeni bir SharePoint grubu oluşturur ve bunu bir site koleksiyonuna eklersiniz.

```powershell
$tenant = "<tenant name, such as litwareinc for litwareinc.com>"
$site = "<site name>"
$group = "<group name name, such as Auditors>"
$level = "<permission level, such as View Only>"
New-SPOSiteGroup -Group $group -PermissionLevels $level -Site https://$tenant.sharepoint.com/sites/$site
```

İzin düzeyleri gibi grup özellikleri daha sonra cmdlet'i kullanılarak `Set-SPOSiteGroup` güncelleştirilebilir.

Örneğin, contoso kiracısında contosotest site koleksiyonuna Yalnızca Görüntüleme izinlerine sahip Denetçiler grubunu ekleyelim:

```powershell
$tenant = "contoso"
$site = "contosotest"
$group = "Auditors"
$level = "View Only"
New-SPOSiteGroup -Group $group -PermissionLevels $level -Site https://$tenant.sharepoint.com/sites/$site
```

## <a name="remove-users-from-a-group"></a>Gruptan kullanıcı kaldırma

Bazen bir kullanıcıyı bir siteden, hatta tüm sitelerden kaldırmanız gerekir. Belki de çalışan bir bölümden diğerine geçer veya şirketten ayrılır. Bunu kullanıcı arabiriminde bir çalışan için kolayca yapabilirsiniz, ancak tam bir bölümü bir siteden diğerine taşımanız gerektiğinde bu işlem kolayca yapılamaz.

Ancak, SharePoint Çevrimiçi Yönetim Kabuğu ve CSV dosyalarını kullanarak bu hızlı ve kolaydır. Bu görevde, bir kullanıcıyı site koleksiyonu güvenlik grubundan kaldırmak için Windows PowerShell kullanacaksınız. Ardından bir CSV dosyası kullanacak ve farklı sitelerden çok sayıda kullanıcıyı kaldıracaksınız.

Komut söz dizimini görebilmek için site koleksiyonu grubundan tek bir Microsoft 365 kullanıcıyı kaldırmak için 'Remove-SPOUser' cmdlet'ini kullanacağız. Söz dizimi şöyle görünür:

```powershell
$tenant = "<tenant name, such as litwareinc for litwareinc.com>"
$site = "<site name>"
$user = "<user account name, such as opalc>"
$group = "<group name name, such as Auditors>"
Remove-SPOUser -LoginName $user@$tenant.com -Site https://$tenant.sharepoint.com/sites/$site -Group $group
```

Örneğin, Ahmet Overby'yi contoso kiracısında contosotest site koleksiyonundaki site koleksiyonu Denetçileri grubundan kaldıralım:

```powershell
$tenant = "contoso"
$site = "contosotest"
$user = "bobbyo"
$group = "Auditors"
Remove-SPOUser -LoginName $user@$tenant.com -Site https://$tenant.sharepoint.com/sites/$site -Group $group
```

Bobby'yi şu anda içinde olduğu tüm gruplardan kaldırmak istediğimizi varsayalım. Bunu şu şekilde yaparız:

```powershell
$tenant = "contoso"
$user = "bobbyo"
Get-SPOSite | ForEach {Get-SPOSiteGroup –Site $_.Url} | ForEach {Remove-SPOUser -LoginName $user@$tenant.com -Site &_.Url}
```

> [!WARNING]
> Bu sadece bir örnektir. Her gruptan bir kullanıcıyı kaldırmanız gerekmediği sürece (örneğin, kullanıcı şirketten ayrıldığında) bu komutu çalıştırmamalısınız.

## <a name="automate-management-of-large-lists-of-users-and-groups"></a>Büyük kullanıcı ve grup listelerinin yönetimini otomatikleştirme

SharePoint sitelerine çok sayıda hesap eklemek ve bunlara izin vermek için Microsoft 365 yönetim merkezi, tek tek PowerShell komutlarını veya PowerShell'i ve csv dosyasını kullanabilirsiniz. Bu seçenekler arasında CSV dosyası, bu görevi otomatikleştirmenin en hızlı yoludur.

Temel işlem, Windows PowerShell betiğin ihtiyaç duyduğu parametrelere karşılık gelen üst bilgileri (sütunları) içeren bir CSV dosyası oluşturmaktır. Excel'da bu tür bir listeyi kolayca oluşturabilir ve csv dosyası olarak dışarı aktarabilirsiniz. Ardından, CSV dosyasındaki kayıtlar (satırlar) arasında yineleme yapmak ve kullanıcıları gruplara ve grupları sitelere eklemek için bir Windows PowerShell betiği kullanırsınız.

Örneğin, bir grup site koleksiyonu, grup ve izin tanımlamak için bir CSV dosyası oluşturalım. Ardından, grupları kullanıcılarla doldurmak için bir CSV dosyası oluşturacağız. Son olarak grupları oluşturan ve dolduran bir Windows PowerShell betiği oluşturup çalıştıracağız.

İlk CSV dosyası bir veya daha fazla site koleksiyonuna bir veya daha fazla grup ekler ve şu yapıya sahip olur:

Üstbilgi:

```powershell
Site,Group,PermissionLevels
```

Öğe:

```powershell
https://tenant.sharepoint.com/sites/site,group,level
```

Örnek bir dosya aşağıda verilmişti:

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

İkinci CSV dosyası bir veya daha fazla gruba bir veya daha fazla kullanıcı ekler ve şu yapıya sahip olur:

Üstbilgi:

```powershell
Group,LoginName,Site
```

Öğe:

```powershell
group,login,https://tenant.sharepoint.com/sites/site
```

Örnek bir dosya aşağıda verilmişti:

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

Sonraki adım için, sürücünüze kaydedilmiş iki CSV dosyasının olması gerekir. Burada hem CSV dosyalarını kullanan hem de izin ve grup üyeliği ekleyen örnek komutlar verilmiştir:

```powershell
Import-Csv C:\O365Admin\GroupsAndPermissions.csv | ForEach {New-SPOSiteGroup -Group $_.Group -PermissionLevels $_.PermissionLevels -Site $_.Site}
Import-Csv C:\O365Admin\Users.csv | ForEach {Add-SPOUser -Group $_.Group –LoginName $_.LoginName -Site $_.Site}
```

Betik, CSV dosya içeriğini içeri aktarır ve **New-SPOSiteGroup** ve **Add-SPOUser** komutlarının parametrelerini doldurmak için sütunlardaki değerleri kullanır. Örneğimizde, bu dosyayı C sürücüsündeki O365Admin klasörüne kaydediyoruz, ancak istediğiniz yere kaydedebilirsiniz.

Şimdi aynı CSV dosyasını kullanarak farklı sitelerdeki birkaç grup için bir grup kişiyi kaldıralım. Aşağıda örnek bir komut verilmişti:

```powershell
Import-Csv C:\O365Admin\Users.csv | ForEach {Remove-SPOUser -LoginName $_.LoginName -Site $_.Site -Group $_.Group}
```

## <a name="generate-user-reports"></a>Kullanıcı raporları oluşturma

Birkaç site için bir rapor almak ve bu sitelerin kullanıcılarını, izin düzeylerini ve diğer özellikleri görüntülemek isteyebilirsiniz. Söz dizimi şöyle görünür:

```powershell
$tenant = "<tenant name, such as litwareinc for litwareinc.com>"
$site = "<site name>"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site | select * | Format-table -Wrap -AutoSize | Out-File c\UsersReport.txt -Force -Width 360 -Append
```

Bu, bu üç sitenin verilerini alır ve yerel sürücünüzdeki bir metin dosyasına yazar. –Append parametresi var olan bir dosyaya yeni içerik ekler.

Örneğin, Contoso1 kiracısı için ContosoTest, TeamSite01 ve Project01 sitelerinde bir rapor çalıştıralım:

```powershell
$tenant = "contoso"
$site = "contosotest"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site | Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
$site = "TeamSite01"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site |Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
$site = "Project01"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site | Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
```

Yalnızca **$site** değişkenini değiştirmek zorunda kaldık. **$tenant** değişkeni, değerini komutun üç çalıştırmasına kadar korur.

Ancak, bunu her site için yapmak isterseniz ne olur? Bu komutu kullanarak tüm bu web sitelerini yazmak zorunda kalmadan bunu yapabilirsiniz:

```powershell
Get-SPOSite | ForEach {Get-SPOUser –Site $_.Url} | Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
```

Bu rapor oldukça basittir ve daha ayrıntılı bilgiler içeren daha belirli raporlar veya raporlar oluşturmak için daha fazla kod ekleyebilirsiniz. Ancak bu, SharePoint Online ortamındaki kullanıcıları yönetmek için SharePoint Çevrimiçi Yönetim Kabuğu'nun nasıl kullanılacağı hakkında size bir fikir vermelidir.

## <a name="see-also"></a>Ayrıca bkz.

[Çevrimiçi PowerShell'i SharePoint için Bağlan](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online)

[PowerShell ile SharePoint Online'i yönetme](create-sharepoint-sites-and-add-users-with-powershell.md)

[PowerShell ile Microsoft 365’i yönetme](manage-microsoft-365-with-microsoft-365-powershell.md)

[Microsoft 365 için PowerShell'i kullanmaya başlama](getting-started-with-microsoft-365-powershell.md)
