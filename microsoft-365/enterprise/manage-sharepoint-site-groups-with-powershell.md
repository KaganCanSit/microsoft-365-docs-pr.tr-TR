---
title: PowerShell SharePoint Online site gruplarını yönetme
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/17/2019
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
description: Bu makalede, Microsoft 365 Online site gruplarını yönetmek SharePoint PowerShell kullanımı yordamlarını bulabilirsiniz.
ms.openlocfilehash: 393771fec5346b10d76bbe5af471ca3dd42ebf80
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2022
ms.locfileid: "63681226"
---
# <a name="manage-sharepoint-online-site-groups-with-powershell"></a>PowerShell SharePoint Online site gruplarını yönetme

*Bu makale hem son hem de Microsoft 365 Kurumsal hem de Office 365 Kurumsal.*

Microsoft 365 yönetim merkezi Online site gruplarınızı yönetmek için Microsoft 365 için PowerShell SharePoint de kullanabilirsiniz.

## <a name="before-you-begin"></a>Başlamadan önce

Bu makaledeki yordamlar için SharePoint Online'a bağlanmanız gerekir. Yönergeler için bkz. [Bağlan Online PowerShell SharePoint e yükleme](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online).

## <a name="view-sharepoint-online-with-powershell-for-microsoft-365"></a>Microsoft 365 için PowerShell ile SharePoint Online'Microsoft 365

Web SharePoint Yönetim Merkezi'nde site gruplarını yönetmek için kullanımı kolay bazı yöntemler vardır. Örneğin, site için gruplara ve grup üyelerine bakmak istediğiniz varsayalım `https://litwareinc.sharepoint.com/sites/finance` . İşte yapmak için şunları yapacaksınız:

1. Genel SharePoint merkezinde Etkin <a href="https://go.microsoft.com/fwlink/?linkid=2185220" target="_blank">**siteler'i seçin**</a> ve sonra da sitenin URL'sini seçin.
2. Site sayfasında, Seçenekler <a href="https://go.microsoft.com/fwlink/?linkid=2185072" target="_blank">**Ayarlar**</a> (sayfanın sağ üst köşesinde bulunur) öğesini ve sonra da **Site izinleri'ne tıklayın**.

Ardından, bakmak istediğiniz bir sonraki site için işlemi tekrarlayın.

Microsoft 365 için PowerShell ile grupların listesini Microsoft 365 aşağıdaki komutları kullanabilirsiniz:

```powershell
$siteURL = "https://litwareinc.sharepoint.com/sites/finance"
$x = Get-SPOSiteGroup -Site $siteURL
foreach ($y in $x)
    {
        Write-Host $y.Title -ForegroundColor "Yellow"
        Get-SPOSiteGroup -Site $siteURL -Group $y.Title | Select-Object -ExpandProperty Users
        Write-Host
    }
```

SharePoint Online Yönetim Kabuğu komut isteminde bu komut SharePoint çalıştırabilirsiniz:

- Komutları Not Defteri (veya başka bir metin düzenleyicisine) kopyalayın, **$siteURL** değişkeninin değerini değiştirebilir, komutları seçin ve sonra da SharePoint Çevrimiçi Yönetim Kabuğu komut istemine yapıştırın. Bunu yapmak için, PowerShell komut isteminde durur **>>** . Komutu yürütmek için Enter tuşuna `foreach` basın.<br/>
- Komutları Not Defteri (veya başka bir metin düzenleyicisine) kopyalayın, **$siteURL** değişkeninin değerini değiştirebilir ve sonra bu metin dosyasını bir adla ve .ps1 uzantısıyla uygun bir klasöre kaydedin. Ardından, betiği, yolunu SharePoint dosya adını belirterek Çevrimiçi Yönetim Kabuğu komut isteminden çalıştırın. İşte örnek bir komut:

```powershell
C:\Scripts\SiteGroupsAndUsers.ps1
```

Her iki durumda da, aşağıdakine benzer bir şey görüyor gerekir:

![SharePoint Online site grupları.](../media/SPO-site-groups.png)

Bunlar, site için oluşturulmuş tüm gruplar ve `https://litwareinc.sharepoint.com/sites/finance`bu gruplara atanan tüm kullanıcılardır. Grup adlarını üyelerinden ayırmanıza yardımcı olmak için grup adları sarıdır.

Başka bir örnek olarak, bu komut kümesi tüm gruplarınızı ve tüm Grup üyeliklerini listelemektedir SharePoint Online siteleriniz için.

```powershell
$x = Get-SPOSite
foreach ($y in $x)
    {
        Write-Host $y.Url -ForegroundColor "Yellow"
        $z = Get-SPOSiteGroup -Site $y.Url
        foreach ($a in $z)
            {
                 $b = Get-SPOSiteGroup -Site $y.Url -Group $a.Title
                 Write-Host $b.Title -ForegroundColor "Cyan"
                 $b | Select-Object -ExpandProperty Users
                 Write-Host
            }
    }
```

## <a name="see-also"></a>Ayrıca bkz.

[Bağlan Online PowerShell SharePoint e geri ödeme](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online)

[PowerShell SharePoint ve kullanıcı ekleme](create-sharepoint-sites-and-add-users-with-powershell.md)

[PowerShell SharePoint Online kullanıcılarını ve gruplarını yönetme](manage-sharepoint-users-and-groups-with-powershell.md)

[PowerShell Microsoft 365'i yönetme](manage-microsoft-365-with-microsoft-365-powershell.md)

[Microsoft 365 için PowerShell ile çalışmaya Microsoft 365](getting-started-with-microsoft-365-powershell.md)
