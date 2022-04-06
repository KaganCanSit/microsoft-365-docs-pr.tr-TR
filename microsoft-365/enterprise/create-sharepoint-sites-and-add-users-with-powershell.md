---
title: PowerShell SharePoint ve kullanıcı ekleme
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: 'Özet: Yeni SharePoint Online siteleri oluşturmak ve ardından bu sitelere kullanıcı ve grup eklemek için PowerShell kullanın.'
ms.openlocfilehash: 95bd3fb5647a5c6680fd9a07ebdf45e106acb095
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2022
ms.locfileid: "63681380"
---
# <a name="create-sharepoint-online-sites-and-add-users-with-powershell"></a>PowerShell SharePoint ve kullanıcı ekleme

*Bu makale hem son hem de Microsoft 365 Kurumsal hem de Office 365 Kurumsal.*

Microsoft 365 için PowerShell'i kullanarak SharePoint Online siteleri oluşturabilir ve kullanıcı eklerken Microsoft 365 yönetim merkezi, görevleri hızla ve tekrar tekrar gerçekleştirebilirsiniz. Ayrıca, çalışma sayfalarında gerçekleştirilemayacak görevleri Microsoft 365 yönetim merkezi.

## <a name="connect-to-sharepoint-online"></a>Bağlan Online'SharePoint'a

Bu konudaki yordamlar için SharePoint Online'a bağlanmanız gerekir. Yönergeler için bkz. [Bağlan Online PowerShell SharePoint e yükleme](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online)

## <a name="step-1-create-new-site-collections-using-powershell"></a>1. Adım: PowerShell kullanarak yeni site koleksiyonları oluşturma

PowerShell ve sağlanan örnek kodu kullanarak .csv bir .csv dosyası kullanarak birden çok site Not Defteri. Bu yordam için, köşeli ayraç içinde gösterilen yer tutucu bilgilerini kendi sitenize ve kiracıya özgü bilgilerle değiştirirsiniz. Bu işlem, tek bir dosya oluşturmanıza ve bu dosyayı kullanan tek bir PowerShell komutunu çalıştırmanızı sağlar. Bu, eylemlerin hem yinelenebilir hem de taşınabilir olmasına neden olur ve çok sayıda (yoksa) hataların, SharePoint Online Management Shell'a yazarak gelebilirsiniz. Bu yordamın iki işlemi vardır. İlk olarak bir .csv dosyası oluşturacağız ve ardından .csv oluşturmak için içeriğini kullanan PowerShell'i kullanarak bu dosyaya başvuracağız.

PowerShell cmdlet'i .csv dosyayı içeri aktarır ve dosyayı sütun başlıkları olarak ilk satırı okunan kıvrımlı köşeli ayraçlar içinde bir döngüye alır. Ardından PowerShell cmdlet'i kalan kayıtlarda yineler, her kayıt için yeni bir site koleksiyonu oluşturur ve site koleksiyonunun özelliklerini sütun başlıklarına göre atar.

### <a name="create-a-csv-file"></a>.csv oluşturma

> [!NOTE]
> Kaynak kotası parametresi yalnızca klasik sitelerde çalışır. Modern bir sitede bu parametreyi kullanırsanız, kullanımdan kullanımdan kullanım dışı olduğunu haber alan bir uyarı iletisi alabilirsiniz.

1. Metin Not Defteri açın ve aşağıdaki metin bloğuna yapıştırın:

   ```powershell
   Owner,StorageQuota,Url,ResourceQuota,Template,TimeZoneID,Name
   owner@tenant.onmicrosoft.com,100,https://tenant.sharepoint.com/sites/TeamSite01,25,EHS#1,10,Contoso Team Site
   owner@tenant.onmicrosoft.com,100,https://tenant.sharepoint.com/sites/Blog01,25,BLOG#0,10,Contoso Blog
   owner@tenant.onmicrosoft.com,150,https://tenant.sharepoint.com/sites/Project01,25,PROJECTSITE#0,10,Project Alpha
   owner@tenant.onmicrosoft.com,150,https://tenant.sharepoint.com/sites/Community01,25,COMMUNITY#0,10,Community Site
   ```

   Burada *kiracı*, kiracının adı ve sahibi de kiracınız üzerinde birincil site koleksiyonu yöneticisi rolünü vermek istediğiniz kullanıcının kullanıcı adıdır.

   (Toplu olarak daha hızlı değiştirmek için Not Defteri Ctrl+H tuşlarına basabilirsiniz.)

2. Dosyayı masaüstünüze **farklı birSiteCollections.csv**.

> [!TIP]
> Bu veya başka herhangi bir .csv Windows PowerShell betik dosyası kullanamadan önce, fazladan veya yazdırılmayan karakter kullanmamanız iyi bir yöntemdir. Dosyayı Word'de açın ve şeritte paragraf simgesine tıklarsanız yazdırıl olmayan karakterler gösterilir. Fazladan yazdırılmamalıdır. Örneğin, dosyanın sonunda son paragrafın ötesinde bir paragraf işareti olmayacaktır.

### <a name="run-the-windows-powershell-command"></a>Windows PowerShell komutunu çalıştırma

1. Komut Windows PowerShell, aşağıdaki komutu yazın veya kopyalayıp yapıştırın ve Enter tuşuna basın:

   ```powershell
   Import-Csv C:\users\MyAlias\desktop\SiteCollections.csv | ForEach-Object {New-SPOSite -Owner $_.Owner -StorageQuota $_.StorageQuota -Url $_.Url -NoWait -ResourceQuota $_.ResourceQuota -Template $_.Template -TimeZoneID $_.TimeZoneID -Title $_.Name}
   ```

   Burada *MyAlias* kullanıcı diğer adınıza eşittir.

2. Yeniden Windows PowerShell istemini bekleyin. Bu birkaç dakika kadar zaman alır.

3. Komut Windows PowerShell, aşağıdaki cmdlet'i yazın veya kopyalayıp yapıştırın ve Enter tuşuna basın:

   ```powershell
   Get-SPOSite -Detailed | Format-Table -AutoSize
   ```

4. Listede yeni site koleksiyonlarını not edin. Örnek CSV dosyamızı kullanarak aşağıdaki site koleksiyonlarını görüyorsunuz: **TeamSite01**, **Blog01**, **Project01** ve **Community01**

Hepsi bu kadar. Oluşturduğunuz dosya ve tek bir site .csv kullanarak birden çok site koleksiyonu Windows PowerShell. Artık bu sitelerde kullanıcı oluşturmak ve atamak için hazır mısınız?

## <a name="step-2-add-users-and-groups"></a>2. Adım: Kullanıcıları ve grupları ekleme

Şimdi kullanıcıları oluşturacak ve bir site koleksiyonu grubuna eklirsiniz. Daha sonra yeni grupları ve .csv toplu olarak karşıya yüklemek için bir dosya kullanırsanız.

Aşağıdaki yordamlar Ekip Sitesi01, Blog01, Project01 ve Topluluk01 örnek sitelerini kullanmaya devam eder.

### <a name="create-csv-and-ps1-files"></a>Dosyaları .csv ve .ps1 oluşturma

1. Metin Not Defteri açın ve aşağıdaki metin bloğuna yapıştırın:

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

   Burada *kiracı,* kiracı adınıza eşittir.

2. Dosyayı masaüstünüze farklı bir dosya **GroupsAndPermissions.csv**.

3. Yeni bir metin örneği Not Defteri ve aşağıdaki metin bloğuni bu metin bloğuna yapıştırın:

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

   Burada *kiracı* kiracı adınıza, kullanıcı *adı* ise mevcut bir kullanıcının kullanıcı adına eşittir.

4. Dosyayı masaüstünüze farklı bir dosya **Users.csv**.

5. Yeni bir metin örneği Not Defteri ve aşağıdaki metin bloğuni bu metin bloğuna yapıştırın:

   ```powershell
   Import-Csv C:\users\MyAlias\desktop\GroupsAndPermissions.csv | ForEach-Object {New-SPOSiteGroup -Group $_.Group -PermissionLevels $_.PermissionLevels -Site $_.Site}
   Import-Csv C:\users\MyAlias\desktop\Users.csv | where {Add-SPOUser -Group $_.Group –LoginName $_.LoginName -Site $_.Site}
   ```

   Burada MyAlias, o anda oturum açmış olan kullanıcının kullanıcı adına eşittir.

6. Dosyayı masaüstünüze farklı bir dosya **UsersAndGroups.ps1**. Bu basit bir Windows PowerShell betiğidir.

Artık, birçok site koleksiyonuna kullanıcı UsersAndGroup.ps1 için bu komut dosyasını çalıştırmaya hazır mısınız?

### <a name="run-usersandgroupsps1-script"></a>Komut UsersAndGroups.ps1 çalıştırma

1. Yeni Çevrimiçi Yönetim SharePoint dönme.

2. Komut Windows PowerShell, aşağıdaki satırı yazın veya kopyalayıp yapıştırın ve Enter tuşuna basın:

   ```powershell
   Set-ExecutionPolicy Bypass
   ```

3. Onay isteminde Y tuşuna **basın**.

4. Komut Windows PowerShell, şunları yazın veya kopyalayıp yapıştırın ve Enter tuşuna basın:

   ```powershell
   c:\users\MyAlias\desktop\UsersAndGroups.ps1
   ```

   Burada *MyAlias* kullanıcı adınıza eşittir.

5. Devam edene kadar istemnin geri dönmesini bekleyin. Gruplar oluşturulduklarında ilk olarak görünürler. Ardından, kullanıcılar eklendiklerine göre grup listesinin yinelenir.

## <a name="see-also"></a>Ayrıca bkz.

[Bağlan Online PowerShell SharePoint e geri ödeme](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online)

[PowerShell SharePoint Online site gruplarını yönetme](manage-sharepoint-site-groups-with-powershell.md)

[PowerShell Microsoft 365'i yönetme](manage-microsoft-365-with-microsoft-365-powershell.md)

[Microsoft 365 için PowerShell ile çalışmaya Microsoft 365](getting-started-with-microsoft-365-powershell.md)
