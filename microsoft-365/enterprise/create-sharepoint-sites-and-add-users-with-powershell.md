---
title: PowerShell ile SharePoint Online siteleri oluşturma ve kullanıcı ekleme
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: 'Özet: PowerShell kullanarak yeni SharePoint Çevrimiçi siteler oluşturun ve ardından bu sitelere kullanıcı ve grup ekleyin.'
ms.openlocfilehash: 9d99f98825d88e2d2e63f106a7b5704c773c8be1
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65101347"
---
# <a name="create-sharepoint-online-sites-and-add-users-with-powershell"></a>PowerShell ile SharePoint Online siteleri oluşturma ve kullanıcı ekleme

*Bu makale hem Microsoft 365 Kurumsal hem de Office 365 Kurumsal için geçerlidir.*

SharePoint Online siteleri oluşturmak ve kullanıcı eklemek için Microsoft 365 için PowerShell kullandığınızda, görevleri Microsoft 365 yönetim merkezi çok daha hızlı ve tekrar tekrar gerçekleştirebilirsiniz. ayrıca Microsoft 365 yönetim merkezi gerçekleştirilemez görevleri de gerçekleştirebilirsiniz.

## <a name="connect-to-sharepoint-online"></a>SharePoint Online'a Bağlan

Bu konudaki yordamlar, SharePoint Online'a bağlanmanızı gerektirir. Yönergeler için bkz. [çevrimiçi PowerShell SharePoint Bağlan](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online)

## <a name="step-1-create-new-site-collections-using-powershell"></a>1. Adım: PowerShell kullanarak yeni site koleksiyonları oluşturma

PowerShell kullanarak birden çok site ve sağlanan örnek kodu kullanarak oluşturduğunuz bir .csv dosyası oluşturun ve Not Defteri. Bu yordam için köşeli ayraç içinde gösterilen yer tutucu bilgilerini kendi sitenize ve kiracıya özgü bilgilerle değiştireceksiniz. Bu işlem, tek bir dosya oluşturmanıza ve bu dosyayı kullanan tek bir PowerShell komutu çalıştırmanıza olanak tanır. Bu, gerçekleştirilen eylemlerin hem yinelenebilir hem de taşınabilir olmasını sağlar ve SharePoint Çevrimiçi Yönetim Kabuğu'na uzun komutlar yazmanın neden olabileceği birçok hatayı (hepsi olmasa da) ortadan kaldırır. Bu yordamın iki bölümü vardır. İlk olarak bir .csv dosyası oluşturacak ve ardından PowerShell kullanarak bu .csv dosyasına başvuracaksınız. Bu dosya, siteleri oluşturmak için içeriğini kullanır.

PowerShell cmdlet'i .csv dosyasını içeri aktarır ve dosyanın ilk satırını sütun üst bilgileri olarak okuyan küme ayraçlarının içinde bir döngüye aktarır. PowerShell cmdlet'i daha sonra kalan kayıtlarda yinelenir, her kayıt için yeni bir site koleksiyonu oluşturur ve site koleksiyonunun özelliklerini sütun üst bilgilerine göre atar.

### <a name="create-a-csv-file"></a>.csv dosyası oluşturma

> [!NOTE]
> Kaynak kotası parametresi yalnızca klasik sitelerde çalışır. Bu parametreyi modern bir sitede kullanırsanız, kullanım dışı bırakıldığını belirten bir uyarı iletisi alabilirsiniz.

1. Not Defteri açın ve içine aşağıdaki metin bloğunu yapıştırın:

   ```powershell
   Owner,StorageQuota,Url,ResourceQuota,Template,TimeZoneID,Name
   owner@tenant.onmicrosoft.com,100,https://tenant.sharepoint.com/sites/TeamSite01,25,EHS#1,10,Contoso Team Site
   owner@tenant.onmicrosoft.com,100,https://tenant.sharepoint.com/sites/Blog01,25,BLOG#0,10,Contoso Blog
   owner@tenant.onmicrosoft.com,150,https://tenant.sharepoint.com/sites/Project01,25,PROJECTSITE#0,10,Project Alpha
   owner@tenant.onmicrosoft.com,150,https://tenant.sharepoint.com/sites/Community01,25,COMMUNITY#0,10,Community Site
   ```

   Burada *kiracı* , kiracınızın adıdır ve *sahip* , birincil site koleksiyonu yöneticisi rolünü vermek istediğiniz kiracınızdaki kullanıcının kullanıcı adıdır.

   (Toplu değiştirme işlemlerini daha hızlı yapmak için Not Defteri kullandığınızda Ctrl+H tuşlarına basabilirsiniz.)

2. Dosyayı masaüstünüzde **SiteCollections.csv** olarak kaydedin.

> [!TIP]
> Bu veya başka bir .csv veya Windows PowerShell betik dosyası kullanmadan önce, fazladan veya yazdırılmayan karakter olmadığından emin olmak iyi bir uygulamadır. Dosyayı Word'de açın ve şeritte paragraf simgesine tıklayarak yazdırılmayan karakterleri görüntüleyin. Yazdırılmayan fazladan karakter olmamalıdır. Örneğin, dosyanın sonundaki son paragraf işaretinin ötesinde paragraf işareti olmamalıdır.

### <a name="run-the-windows-powershell-command"></a>Windows PowerShell komutunu çalıştırma

1. Windows PowerShell isteminde aşağıdaki komutu yazın veya kopyalayıp yapıştırın ve Enter tuşuna basın:

   ```powershell
   Import-Csv C:\users\MyAlias\desktop\SiteCollections.csv | ForEach-Object {New-SPOSite -Owner $_.Owner -StorageQuota $_.StorageQuota -Url $_.Url -NoWait -ResourceQuota $_.ResourceQuota -Template $_.Template -TimeZoneID $_.TimeZoneID -Title $_.Name}
   ```

   *MyAlias'ın* kullanıcı diğer adınıza eşit olduğu yer.

2. Windows PowerShell isteminin yeniden belirmesini bekleyin. Bir veya iki dakika sürebilir.

3. Windows PowerShell isteminde aşağıdaki cmdlet'i yazın veya kopyalayıp yapıştırın ve Enter tuşuna basın:

   ```powershell
   Get-SPOSite -Detailed | Format-Table -AutoSize
   ```

4. Listedeki yeni site koleksiyonlarını not edin. Örnek CSV dosyamızı kullanarak şu site koleksiyonlarını görürsünüz: **TeamSite01**, **Blog01**, **Project01** ve **Community01**

Hepsi bu kadar. Oluşturduğunuz .csv dosyasını ve tek bir Windows PowerShell komutunu kullanarak birden çok site koleksiyonu oluşturdunuz. Artık kullanıcıları oluşturmaya ve bu sitelere atamaya hazırsınız.

## <a name="step-2-add-users-and-groups"></a>2. Adım: Kullanıcı ve grup ekleme

Şimdi kullanıcıları oluşturacak ve bir site koleksiyonu grubuna ekleyeceksiniz. Ardından yeni grupları ve kullanıcıları toplu olarak karşıya yüklemek için bir .csv dosyası kullanacaksınız.

Aşağıdaki yordamlar TeamSite01, Blog01, Project01 ve Community01 örnek sitelerini kullanmaya devam eder.

### <a name="create-csv-and-ps1-files"></a>.csv ve .ps1 dosyaları oluşturma

1. Not Defteri açın ve içine aşağıdaki metin bloğunu yapıştırın:

   ```powershell
   Site,Group,PermissionLevels
   https://tenant.sharepoint.com/sites/Community01,Contoso Project Leads,Full Control
   https://tenant.sharepoint.com/sites/Community01,Contoso Auditors,View Only
   https://tenant.sharepoint.com/sites/Community01,Contoso Designers,Design
   https://tenant.sharepoint.com/sites/TeamSite01,XT1000 Team Leads,Full Control
   https://tenant.sharepoint.com/sites/TeamSite01,XT1000 Advisors,Edit
   https://tenant.sharepoint.com/sites/Blog01,Contoso Blog Designers,Design
   https://tenant.sharepoint.com/sites/Blog01,Contoso Blog Editors,Edit
   https://tenant.sharepoint.com/sites/Project01,Project Alpha Approvers,Full Control
   ```

   Burada *kiracı, kiracı* adınıza eşittir.

2. Dosyayı **masaüstünüzdeGroupsAndPermissions.csv** olarak kaydedin.

3. Yeni bir Not Defteri örneği açın ve içine aşağıdaki metin bloğunu yapıştırın:

   ```powershell
   Group,LoginName,Site
   Contoso Project Leads,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/Community01
   Contoso Auditors,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/Community01
   Contoso Designers,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/Community01
   XT1000 Team Leads,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/TeamSite01
   XT1000 Advisors,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/TeamSite01
   Contoso Blog Designers,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/Blog01
   Contoso Blog Editors,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/Blog01
   Project Alpha Approvers,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/Project01
   ```

   Burada *kiracı* kiracı adınız ile *kullanıcı adı* , mevcut bir kullanıcının kullanıcı adına eşittir.

4. Dosyayı **masaüstünüzdeUsers.csv** olarak kaydedin.

5. Yeni bir Not Defteri örneği açın ve içine aşağıdaki metin bloğunu yapıştırın:

   ```powershell
   Import-Csv C:\users\MyAlias\desktop\GroupsAndPermissions.csv | ForEach-Object {New-SPOSiteGroup -Group $_.Group -PermissionLevels $_.PermissionLevels -Site $_.Site}
   Import-Csv C:\users\MyAlias\desktop\Users.csv | where {Add-SPOUser -Group $_.Group –LoginName $_.LoginName -Site $_.Site}
   ```

   Burada MyAlias, şu anda oturum açmış olan kullanıcının kullanıcı adına eşittir.

6. Dosyayı **masaüstünüzdeUsersAndGroups.ps1** olarak kaydedin. Bu basit bir Windows PowerShell betiğidir.

Artık birden çok site koleksiyonuna kullanıcı ve grup eklemek için UsersAndGroup.ps1 betiğini çalıştırmaya hazırsınız.

### <a name="run-usersandgroupsps1-script"></a>UsersAndGroups.ps1 betiğini çalıştırma

1. SharePoint Çevrimiçi Yönetim Kabuğu'na dönün.

2. Windows PowerShell isteminde aşağıdaki satırı yazın veya kopyalayıp yapıştırın ve Enter tuşuna basın:

   ```powershell
   Set-ExecutionPolicy Bypass
   ```

3. Onay isteminde **Y tuşuna** basın.

4. Windows PowerShell isteminde aşağıdakileri yazın veya kopyalayıp yapıştırın ve Enter tuşuna basın:

   ```powershell
   c:\users\MyAlias\desktop\UsersAndGroups.ps1
   ```

   *MyAlias* kullanıcı adınıza eşit olduğunda.

5. Devam etmeden önce istemin döndürülmesini bekleyin. Önce grupların oluşturuldukları sırada göründüğünü görürsünüz. Ardından, kullanıcılar eklendikçe grup listesinin yinelendiğini görürsünüz.

## <a name="see-also"></a>Ayrıca bkz.

[Çevrimiçi PowerShell'i SharePoint için Bağlan](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online)

[PowerShell ile SharePoint Çevrimiçi site gruplarını yönetme](manage-sharepoint-site-groups-with-powershell.md)

[PowerShell ile Microsoft 365’i yönetme](manage-microsoft-365-with-microsoft-365-powershell.md)

[Microsoft 365 için PowerShell'i kullanmaya başlama](getting-started-with-microsoft-365-powershell.md)
