---
title: üçüncü taraf içeri aktarılan verileri aramak için İçerik Arama'yı kullanma
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
ms.collection: M365-security-compliance
ms.localizationpriority: medium
search.appverid:
- MOE150
- MET150
ms.assetid: ec2677ff-c4d7-4363-a9e7-22c80e015688
description: Sorgular oluşturarak üçüncü taraf veri kaynağından Microsoft 365 posta kutularına aktarılan öğeleri aramak için İçerik Arama eBulma aracını kullanın.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 29c033f7d31aca14b527aa6b7fd83d533a5875e7
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/19/2022
ms.locfileid: "64939465"
---
# <a name="use-content-search-to-search-third-party-data-imported-by-a-custom-partner-connector"></a>Özel bir iş ortağı bağlayıcısı tarafından içeri aktarılan üçüncü taraf verilerde arama yapmak için İçerik Arama'yı kullanma

Üçüncü taraf veri kaynağından Microsoft 365 posta kutularına aktarılan öğeleri aramak için Microsoft Purview uyumluluk portalındaki [İçerik arama eBulma aracını](content-search.md) kullanabilirsiniz. İçeri aktarılan tüm üçüncü taraf veri öğelerini aramak için bir sorgu oluşturabilir veya belirli üçüncü taraf veri öğelerini aramak için bir sorgu oluşturabilirsiniz. Ayrıca, üçüncü taraf verileri korumak için sorgu tabanlı saklama ilkesi veya sorgu tabanlı eBulma ayrı tutma da oluşturabilirsiniz.
  
Üçüncü taraf verileri içeri aktarmak için bir iş ortağıyla çalışma hakkında daha fazla bilgi ve Microsoft 365 aktarabileceğiniz üçüncü taraf veri türlerinin listesi için bkz. [Office 365'da üçüncü taraf verileri arşivlemek için iş ortağıyla çalışma](work-with-partner-to-archive-third-party-data.md).

> [!IMPORTANT]
> Bu makaledeki yönergeler yalnızca özel bir iş ortağı bağlayıcısı tarafından içeri aktarılan üçüncü taraf veriler için geçerlidir. Bu makale, Microsoft uyumluluk merkezindeki üçüncü taraf [veri bağlayıcıları kullanılarak içeri aktarılan üçüncü taraf veriler](archiving-third-party-data.md#third-party-data-connectors) için geçerli değildir.
  
## <a name="creating-a-query-to-search-all-third-party-data"></a>Tüm üçüncü taraf verilerde arama yapmak için sorgu oluşturma

Office 365 aktardığınız herhangi bir üçüncü taraf veri türünü aramak (veya ayrı tutmak) için, İçerik Araması için anahtar sözcük kutusundaki ileti özellik-değer çiftini veya sorgu tabanlı ayrı tutma oluştururken kullanabilirsiniz`kind:externaldata`. Örneğin, herhangi bir üçüncü taraf veri kaynağından içeri aktarılan ve içeri aktarılan öğenin Subject özelliğinde "contoso" sözcüğünü içeren öğeleri aramak için aşağıdaki sorguyu kullanabilirsiniz: 
  
```powershell
kind:externaldata AND subject:contoso
```

Önceki anahtar sözcük sorgu örneği, konu özelliğini içerir. Anahtar sözcük sorgusuna eklenebilen üçüncü taraf veri öğelerinin diğer özelliklerinin listesi için, üçüncü taraf [verilerini Office 365 arşivlemek için iş ortağıyla çalışma](work-with-partner-to-archive-third-party-data.md#more-information) bölümündeki "Daha fazla bilgi" bölümüne bakın.
  
Üçüncü taraf verileri aramak ve tutmak için sorgular oluştururken, arama sonuçlarını daraltmak için koşulları da kullanabilirsiniz. İçerik Arama sorguları oluşturma hakkında daha fazla bilgi için bkz [. İçerik Arama için anahtar sözcük sorguları ve arama koşulları](keyword-queries-and-search-conditions.md).
  
## <a name="creating-a-query-to-search-specific-types-of-third-party-data"></a>Belirli üçüncü taraf veri türlerini aramak için sorgu oluşturma

Tüm üçüncü taraf veri türlerini aramak yerine, aşağıdaki ileti özelliğini kullanarak yalnızca üçüncü taraf veri türünü belirten sorgular oluşturabilirsiniz: İçerik Araması için anahtar sözcük kutusunda *değer* çifti:
  
```powershell
itemclass:ipm.externaldata.<third-party data type>* 
```

Örneğin, Subject özelliğinde "contoso" sözcüğünü içeren Facebook verilerinde arama yapmak için aşağıdaki sorguyu kullanırsınız:
  
```powershell
itemclass:ipm.externaldata.Facebook* AND subject:contoso
```

Aşağıdaki tabloda, arayabileceğiniz üçüncü taraf veri türleri ve ileti özelliği için  `itemclass:` kullanılacak değer, bu tür üçüncü taraf verileri için özel olarak arama yapmak üzere listelenmiştir. Sorgu söz dizimi büyük/küçük harfe duyarlı değildir. 
  
|**Üçüncü taraf veri türü**|**Özelliğin  `itemclass:` değeri**|
|:-----|:-----|
|AMACI  <br/> | `ipm.externaldata.AIM*` <br/> |
|Amerikan Idol  <br/> | `ipm.externaldata.AmericanIdol*` <br/> |
|Pivot Client ile AOL  <br/> | `ipm.externaldata.Pivot.IM` <br/> |
|Elma Suyu  <br/> | `ipm.externaldata.AppleJuice*` <br/> |
|Ares  <br/> | `ipm.externaldata.Ares*` <br/> |
|Axs Encrypted  <br/> | `ipm.externaldata.AxsEncrypted*` <br/> |
|Axs Exchange  <br/> | `ipm.externaldata.AxsExchange*` <br/> |
|Axs Yerel Arşivi  <br/> | `ipm.externaldata.AxsLocalArchive*` <br/> |
|Axs Yer Tutucusu  <br/> | `ipm.externaldata.AxsPlaceHolder*` <br/> |
|Axs İmzalı  <br/> | `ipm.externaldata.AxsSigned*` <br/> |
|Bazaarvoice  <br/> | `ipm.externaldata.Bazaarvoice*` <br/> |
|Bearshare  <br/> | `ipm.externaldata.Bearshare*` <br/> |
|Bittorrent  <br/> | `ipm.externaldata.BitTorrent*` <br/> |
|Blackberry  <br/> | `ipm.externaldata.Blackberry*` <br/> |
|BlackBerry Arama Günlükleri  <br/> | `ipm.externaldata.BlackBerryCall*` <br/> |
|BlackBerry Messenger  <br/> | `ipm.externaldata.BlackBerryMessenger*` <br/> |
|BlackBerry PIN'i  <br/> | `ipm.externaldata.BlackBerryPIN*` <br/> |
|BlackBerry SMS  <br/> | `ipm.externaldata.BlackBerrySMS*` <br/> |
|Bloomberg  <br/> | `ipm.externaldata.Bloomberg*` <br/> |
|Bloomberg Message  <br/> | `ipm.externaldata.conversation.Bloomberg Message*` <br/> |
|Bloomberg Mesajlaşma  <br/> | `ipm.externaldata.BloombergMessaging*` <br/> |
|Kutusu  <br/> | `ipm.externaldata.Box*` <br/> |
|Cisco Anlık İleti &amp; İletişim Durumu Sunucusu  <br/> | `ipm.externaldata.Jabber.IM` <br/> |
|Cisco Jabber  <br/> | `ipm.externaldata.Jabber*` <br/> |
|Salesforce Chatter için CipherCloud  <br/> | `ipm.externaldata.Chatter.Post` <br/>  `ipm.externaldata.Chatter.Comment` <br/> |
|Doğrudan Bağlan  <br/> | `ipm.externaldata.DirectConnect*` <br/> |
|Facebook  <br/> | `ipm.externaldata.Facebook*` <br/> |
|FastTrack  <br/> | `ipm.externaldata.FastTrack*` <br/> |
|FXConnect  <br/> | `ipm.externaldata.FXConnect.chat` <br/> |
|Flickr  <br/> | `ipm.externaldata.Flickr*` <br/> |
|Gnutella  <br/> | `ipm.externaldata.Gnutella*` <br/> |
|Google+  <br/> | `ipm.externaldata.GooglePlus*` <br/> |
|Google Talk  <br/> | `ipm.externaldata.GoogleTalk*` <br/> |
|GoToMyPC  <br/> | `ipm.externaldata.GoToMyPC*` <br/> |
|HipChat  <br/> | `ipm.externaldata.HipChat*` <br/> |
|Hopster  <br/> | `ipm.externaldata.Hopster*` <br/> |
|HubConnex  <br/> | `ipm.externaldata.HubConnex*` <br/> |
|IBM Connections  <br/> | `ipm.externaldata.Connections*` <br/> |
|IBM SameTime  <br/> | `ipm.externaldata.Sametime*` <br/> |
|ICE Chat  <br/> | `ipm.externaldata.conversation.Ice Chat*` <br/> |
|Indii Messenger  <br/> | `ipm.externaldata.Indii*` <br/> |
|Instagram  <br/> | `ipm.externaldata.Instagram*` <br/> |
|Instant Bloomberg  <br/> | `ipm.externaldata.InstantBloomberg*` <br/> |
|InvestEdge  <br/> | `ipm.externaldata.InvestEdge*` <br/> |
|IRC  <br/> | `ipm.externaldata.IRC*` <br/> |
|Jive  <br/> | `ipm.externaldata.Jive*` <br/> |
|JiveApiRetention  <br/> | `ipm.externaldata.JiveApiRetention*` <br/> |
|JXTA  <br/> | `ipm.externaldata.JXTA*` <br/> |
|LinkedIn  <br/> | `ipm.externaldata.LinkedIn*` <br/> |
|MFTP  <br/> | `ipm.externaldata.MFTP*` <br/> |
|Microsoft UC  <br/> | `ipm.externaldata.MicrosoftUC*` <br/> |
|Zihin Hizalama  <br/> | `ipm.externaldata.MindAlign*` <br/> |
|Mobile Guard  <br/> | `ipm.externaldata.MobileGuard*` <br/> |
|MSN  <br/> | `ipm.externaldata.MSN*` <br/> |
|Myspace  <br/> | `ipm.externaldata.MySpace*` <br/> |
|NEONetwork  <br/> | `ipm.externaldata.NEONetwork*` <br/> |
|OpenNap  <br/> | `ipm.externaldata.OpenNap*` <br/> |
|Pinterest  <br/> | `ipm.externaldata.Pinterest*` <br/> |
|Pivot  <br/> | `ipm.externaldata.Pivot*` <br/> |
|QQ  <br/> | `ipm.externaldata.QQ*` <br/> |
|Microsoft SharePoint  <br/> | `ipm.externaldata.SharePoint*` <br/> |
|Salesforce Chatter  <br/> | `ipm.externaldata.Chatter*` <br/> |
|Skype Kurumsal  <br/> | `ipm.externaldata.Skype*` <br/> |
|Slack Enterprise Kılavuzu  <br/> | `ipm.externaldata.Slack.IM` <br/> |
|SoftEther  <br/> | `ipm.externaldata.SoftEther*` <br/> |
|Squawker  <br/> | `ipm.externaldata.Squawker*` <br/> |
|Symphony  <br/> | `ipm.externaldata.Symphony*` <br/> |
|Thomson Reuters  <br/> | `ipm.externaldata.Reuters*` <br/> |
| Thomson Reuters Eikon Messenger  <br/> | `ipm.externaldata.ReutersEikon*` <br/> |
|Tor  <br/> | `ipm.externaldata.Tor*` <br/> |
|TTT  <br/> | `ipm.externaldata.TTT*` <br/> |
|Twitter  <br/> | `ipm.externaldata.Twitter*` <br/> |
|UBS Sohbeti  <br/> | `ipm.externaldata.UBS*` <br/> |
|Vimeo  <br/> | `ipm.externaldata.Vimeo*` <br/> |
|Winmx  <br/> | `ipm.externaldata.WinMX*` <br/> |
|Winny  <br/> | `ipm.externaldata.Winny*` <br/> |
|Yahoo!  <br/> | `ipm.externaldata.Yahoo!*` <br/> |
|Yammer  <br/> | `ipm.externaldata.Yammer*` <br/> |
|YellowJacket  <br/> | `ipm.externaldata.YellowJacket*` <br/> |
|YouTube  <br/> | `ipm.externaldata.YouTube*` <br/> |
