---
title: PowerShell ile SharePoint Çevrimiçi site gruplarını yönetme
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: Bu makalede, SharePoint Çevrimiçi site gruplarını yönetmek üzere Microsoft 365 için PowerShell kullanma yordamlarını bulabilirsiniz.
ms.openlocfilehash: 411ab477668b7956a63843d0b58b8d6d9bfc9059
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65096446"
---
# <a name="manage-sharepoint-online-site-groups-with-powershell"></a>PowerShell ile SharePoint Çevrimiçi site gruplarını yönetme

*Bu makale hem Microsoft 365 Kurumsal hem de Office 365 Kurumsal için geçerlidir.*

Microsoft 365 yönetim merkezi kullanabilmenize rağmen, SharePoint Çevrimiçi site gruplarınızı yönetmek için Microsoft 365 için PowerShell'i de kullanabilirsiniz.

## <a name="before-you-begin"></a>Başlamadan önce

Bu makaledeki yordamlar, SharePoint Online'a bağlanmanızı gerektirir. Yönergeler için bkz. [Çevrimiçi PowerShell'i SharePoint için Bağlan](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online).

## <a name="view-sharepoint-online-with-powershell-for-microsoft-365"></a>Microsoft 365 için PowerShell ile SharePoint Online'i görüntüleme

SharePoint Online yönetim merkezinde site gruplarını yönetmek için bazı kolay kullanım yöntemleri vardır. Örneğin, sitenin gruplarına ve grup üyelerine `https://litwareinc.sharepoint.com/sites/finance` bakmak istediğinizi varsayalım. Yapmanız gerekenler şunlardır:

1. SharePoint yönetim merkezinde <a href="https://go.microsoft.com/fwlink/?linkid=2185220" target="_blank">**Etkin siteler'i**</a> ve ardından sitenin URL'sini seçin.
2. Site sayfasında <a href="https://go.microsoft.com/fwlink/?linkid=2185072" target="_blank">**Ayarlar**</a> seçin (sayfanın sağ üst köşesinde bulunur) ve ardından **Site izinleri'ni** seçin.

Ardından, bakmak istediğiniz sonraki site için işlemi yineleyin.

Microsoft 365 için PowerShell ile grupların listesini almak için aşağıdaki komutları kullanabilirsiniz:

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

SharePoint Online Management Shell komut isteminde bu komut kümesini çalıştırmanın iki yolu vardır:

- Komutları Not Defteri (veya başka bir metin düzenleyicisine) kopyalayın, **$siteURL** değişkeninin değerini değiştirin, komutları seçin ve SharePoint Çevrimiçi Yönetim Kabuğu komut istemine yapıştırın. Bunu yaptığınızda, PowerShell bir **>>** istemde durur. Komutu yürütmek için Enter tuşuna `foreach` basın.<br/>
- Komutları Not Defteri (veya başka bir metin düzenleyicisine) kopyalayın, **$siteURL** değişkeninin değerini değiştirin ve ardından bu metin dosyasını bir adla ve .ps1 uzantısıyla uygun bir klasöre kaydedin. Ardından, yolunu ve dosya adını belirterek SharePoint Çevrimiçi Yönetim Kabuğu komut isteminden betiği çalıştırın. Aşağıda örnek bir komut verilmiştir:

```powershell
C:\Scripts\SiteGroupsAndUsers.ps1
```

Her iki durumda da şuna benzer bir şey görmeniz gerekir:

![çevrimiçi site gruplarını SharePoint.](../media/SPO-site-groups.png)

Bunlar, sitesi `https://litwareinc.sharepoint.com/sites/finance`için oluşturulan tüm gruplar ve bu gruplara atanan tüm kullanıcılardır. Grup adlarını üyelerinden ayırmanıza yardımcı olması için grup adları sarı renktedir.

Başka bir örnek olarak, SharePoint Online sitelerinizin tümü için grupları ve tüm grup üyeliklerini listeleyen bir komut kümesi aşağıda verilmiştir.

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

[Çevrimiçi PowerShell'i SharePoint için Bağlan](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online)

[PowerShell ile SharePoint Online siteleri oluşturma ve kullanıcı ekleme](create-sharepoint-sites-and-add-users-with-powershell.md)

[PowerShell ile SharePoint Çevrimiçi kullanıcıları ve grupları yönetme](manage-sharepoint-users-and-groups-with-powershell.md)

[PowerShell ile Microsoft 365’i yönetme](manage-microsoft-365-with-microsoft-365-powershell.md)

[Microsoft 365 için PowerShell'i kullanmaya başlama](getting-started-with-microsoft-365-powershell.md)
