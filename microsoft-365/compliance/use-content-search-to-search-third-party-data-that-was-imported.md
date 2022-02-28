---
title: Üçüncü taraf içe aktarılan veride arama yapmak için İçerik Arama'ya
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
description: İçerik Arama eBulma aracını kullanarak sorgular oluşturarak bir üçüncü taraf veri kaynağından Microsoft 365 posta kutularına aktarılan öğeleri arayabilirsiniz.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 068a6e3164154129ba9148b41138d50c518042ed
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62988158"
---
# <a name="use-content-search-to-search-third-party-data-imported-by-a-custom-partner-connector"></a>Özel bir iş ortağı bağlayıcısı tarafından alınan üçüncü taraf verileri aramak için İçerik Arama'ya kullanma

bir üçüncü taraf veri [kaynağından](content-search.md) Microsoft 365 uyumluluk merkezi posta kutularına aktarılan öğeleri aramak için, Microsoft 365 arama eBulma aracını kullanabilirsiniz. İçe aktarılan tüm üçüncü taraf veri öğeleri arasında arama yapmak için sorgu oluşturabilir veya belirli üçüncü taraf veri öğeleri içinde arama yapmak için sorgu oluşturabilirsiniz. Ayrıca, üçüncü taraf verilerini korumak için sorgu tabanlı bir bekletme ilkesi veya sorgu tabanlı eBulma saklaması da oluşturabilirsiniz.
  
Üçüncü taraf verilerini içeri aktaran bir iş ortağıyla çalışma ve Microsoft 365'a aktarabilirsiniz üçüncü taraf veri türlerinin listesi hakkında daha fazla bilgi için bkz. Office 365'te üçüncü taraf verilerini arşivlemek için iş [ortağıyla çalışma](work-with-partner-to-archive-third-party-data.md).

> [!IMPORTANT]
> Bu makaledeki kılavuz, yalnızca özel bir iş ortağı bağlayıcısı tarafından aktarılan üçüncü taraf verileri için geçerlidir. Bu makale, Microsoft uyumluluk merkezinde üçüncü taraf veri bağlayıcıları kullanılarak [aktarılan üçüncü](archiving-third-party-data.md#third-party-data-connectors) taraf verileri için geçerli değildir.
  
## <a name="creating-a-query-to-search-all-third-party-data"></a>Tüm üçüncü taraf verilerini aramak için sorgu oluşturma

Office 365'e aktarılmış herhangi bir üçüncü taraf veri türünü aramak (veya yerinde tutmak) için, `kind:externaldata` İçerik Arama için anahtar sözcük kutusunda veya sorgu tabanlı bir yerinde tutma oluştururken ileti özellik değeri çiftini kullanabilirsiniz. Örneğin, herhangi bir üçüncü taraf veri kaynağından alınan ve alınan öğenin Konu özelliğinde "contoso" sözcüğü geçen öğeleri aramak için aşağıdaki sorguyu kullanabilirsiniz: 
  
```powershell
kind:externaldata AND subject:contoso
```

Önceki anahtar sözcük sorgusu örneği konu özelliğini içerir. Bir anahtar sözcük sorgusuna dahil olan üçüncü taraf veri öğelerinin diğer özelliklerinin listesi için, İş ortağıyla birlikte üçüncü taraf verilerini bir anahtar sözcükte arşivlemek için çalışma bölümündeki "Daha fazla [bilgi" Office 365](work-with-partner-to-archive-third-party-data.md#more-information).
  
Üçüncü taraf verilerde arama yapmak ve tutmak için sorgu oluştururken, arama sonuçlarını daraltmak için koşullar da kullanabilirsiniz. İçerik Arama sorguları oluşturma hakkında daha fazla bilgi için bkz. [Anahtar sözcük sorguları ve İçerik Arama için arama koşulları](keyword-queries-and-search-conditions.md).
  
## <a name="creating-a-query-to-search-specific-types-of-third-party-data"></a>Belirli türlerde üçüncü taraf verilerinde arama yapmak için sorgu oluşturma

Tüm üçüncü taraf veri türlerini aramak yerine, yalnızca şu ileti özelliğini kullanarak belirli bir üçüncü taraf veri türünü belirten sorgular oluşturabilirsiniz *:* İçerik Arama için anahtar sözcük kutusunda değer çifti:
  
```powershell
itemclass:ipm.externaldata.<third-party data type>* 
```

Örneğin, Konu özelliğinde "contoso" sözcüğü geçen Facebook verisinde arama yapmak için aşağıdaki sorguyu kullanabilirsiniz:
  
```powershell
itemclass:ipm.externaldata.Facebook* AND subject:contoso
```

Aşağıdaki tabloda, arayabilirsiniz  `itemclass:` üçüncü taraf veri türleri ve özel olarak bu tür üçüncü taraf verileri için arama yapmak üzere ileti özelliği için kullanmak üzere değer listelemektedir. Sorgu söz dizimi büyük/harfe duyarlı değildir. 
  
|**Üçüncü taraf veri türü**|**`itemclass:` Özellik değeri**|
|:-----|:-----|
|AIM  <br/> | `ipm.externaldata.AIM*` <br/> |
|Amerikan Burdan  <br/> | `ipm.externaldata.AmericanIdol*` <br/> |
|Pivot Client ile AOL  <br/> | `ipm.externaldata.Pivot.IM` <br/> |
|Elma Suyu  <br/> | `ipm.externaldata.AppleJuice*` <br/> |
|Ares  <br/> | `ipm.externaldata.Ares*` <br/> |
|Axs Encrypted  <br/> | `ipm.externaldata.AxsEncrypted*` <br/> |
|Axs Exchange  <br/> | `ipm.externaldata.AxsExchange*` <br/> |
|Axs Local Archive  <br/> | `ipm.externaldata.AxsLocalArchive*` <br/> |
|Axs Yer Tutucusu  <br/> | `ipm.externaldata.AxsPlaceHolder*` <br/> |
|Axs İmzalı  <br/> | `ipm.externaldata.AxsSigned*` <br/> |
|Esnaf  <br/> | `ipm.externaldata.Bazaarvoice*` <br/> |
|Bearshare  <br/> | `ipm.externaldata.Bearshare*` <br/> |
|Bit YerDiya  <br/> | `ipm.externaldata.BitTorrent*` <br/> |
|Blackberry  <br/> | `ipm.externaldata.Blackberry*` <br/> |
|BlackBerry Arama Günlükleri  <br/> | `ipm.externaldata.BlackBerryCall*` <br/> |
|BlackBerry Messenger  <br/> | `ipm.externaldata.BlackBerryMessenger*` <br/> |
|BlackBerry PIN'i  <br/> | `ipm.externaldata.BlackBerryPIN*` <br/> |
|BlackBerry SMS  <br/> | `ipm.externaldata.BlackBerrySMS*` <br/> |
|Bloomberg  <br/> | `ipm.externaldata.Bloomberg*` <br/> |
|Bloomberg Message  <br/> | `ipm.externaldata.conversation.Bloomberg Message*` <br/> |
|Bloomberg Messaging  <br/> | `ipm.externaldata.BloombergMessaging*` <br/> |
|Box  <br/> | `ipm.externaldata.Box*` <br/> |
|Cisco IM &amp; Presence Server  <br/> | `ipm.externaldata.Jabber.IM` <br/> |
|Cisco Cisco Ciscober  <br/> | `ipm.externaldata.Jabber*` <br/> |
|Salesforce Sohbetter için CipherCloud  <br/> | `ipm.externaldata.Chatter.Post` <br/>  `ipm.externaldata.Chatter.Comment` <br/> |
|Doğrudan Bağlan  <br/> | `ipm.externaldata.DirectConnect*` <br/> |
|Facebook  <br/> | `ipm.externaldata.Facebook*` <br/> |
|FastTrack  <br/> | `ipm.externaldata.FastTrack*` <br/> |
|FXConnect  <br/> | `ipm.externaldata.FXConnect.chat` <br/> |
|Flickr  <br/> | `ipm.externaldata.Flickr*` <br/> |
|Ltella  <br/> | `ipm.externaldata.Gnutella*` <br/> |
|Google+  <br/> | `ipm.externaldata.GooglePlus*` <br/> |
|Google Talk  <br/> | `ipm.externaldata.GoogleTalk*` <br/> |
|GoToMyPC  <br/> | `ipm.externaldata.GoToMyPC*` <br/> |
|HipChat  <br/> | `ipm.externaldata.HipChat*` <br/> |
|Hopster  <br/> | `ipm.externaldata.Hopster*` <br/> |
|HubConnex  <br/> | `ipm.externaldata.HubConnex*` <br/> |
|IBM Connections  <br/> | `ipm.externaldata.Connections*` <br/> |
|IBM SameTime  <br/> | `ipm.externaldata.Sametime*` <br/> |
|ICE Sohbeti  <br/> | `ipm.externaldata.conversation.Ice Chat*` <br/> |
|Indii Messenger  <br/> | `ipm.externaldata.Indii*` <br/> |
|Bur kadar, Türkiye  <br/> | `ipm.externaldata.Instagram*` <br/> |
|Instant Bloomberg  <br/> | `ipm.externaldata.InstantBloomberg*` <br/> |
|InvestEdge  <br/> | `ipm.externaldata.InvestEdge*` <br/> |
|IRC  <br/> | `ipm.externaldata.IRC*` <br/> |
|Jive  <br/> | `ipm.externaldata.Jive*` <br/> |
|JiveApiRetention  <br/> | `ipm.externaldata.JiveApiRetention*` <br/> |
|JXTA  <br/> | `ipm.externaldata.JXTA*` <br/> |
|LinkedIn  <br/> | `ipm.externaldata.LinkedIn*` <br/> |
|MFTP  <br/> | `ipm.externaldata.MFTP*` <br/> |
|Microsoft UC  <br/> | `ipm.externaldata.MicrosoftUC*` <br/> |
|Fikir Hizala  <br/> | `ipm.externaldata.MindAlign*` <br/> |
|Mobile Guard  <br/> | `ipm.externaldata.MobileGuard*` <br/> |
|MSN  <br/> | `ipm.externaldata.MSN*` <br/> |
|MySpace  <br/> | `ipm.externaldata.MySpace*` <br/> |
|NEONetwork  <br/> | `ipm.externaldata.NEONetwork*` <br/> |
|OpenNap  <br/> | `ipm.externaldata.OpenNap*` <br/> |
|Pinterest  <br/> | `ipm.externaldata.Pinterest*` <br/> |
|Özet  <br/> | `ipm.externaldata.Pivot*` <br/> |
|QQ  <br/> | `ipm.externaldata.QQ*` <br/> |
|Microsoft SharePoint  <br/> | `ipm.externaldata.SharePoint*` <br/> |
|Salesforce SohbetTeri  <br/> | `ipm.externaldata.Chatter*` <br/> |
|Skype Kurumsal  <br/> | `ipm.externaldata.Skype*` <br/> |
|Slack Enterprise Kılavuzu  <br/> | `ipm.externaldata.Slack.IM` <br/> |
|SoftEther  <br/> | `ipm.externaldata.SoftEther*` <br/> |
|Squawker  <br/> | `ipm.externaldata.Squawker*` <br/> |
|Burya  <br/> | `ipm.externaldata.Symphony*` <br/> |
|Thomson Reuters  <br/> | `ipm.externaldata.Reuters*` <br/> |
| Thomson Reuters E ilgili Messenger  <br/> | `ipm.externaldata.ReutersEikon*` <br/> |
|Tor  <br/> | `ipm.externaldata.Tor*` <br/> |
|TTT  <br/> | `ipm.externaldata.TTT*` <br/> |
|Twitter  <br/> | `ipm.externaldata.Twitter*` <br/> |
|UBS Sohbeti  <br/> | `ipm.externaldata.UBS*` <br/> |
|Vimeo  <br/> | `ipm.externaldata.Vimeo*` <br/> |
|WinMX  <br/> | `ipm.externaldata.WinMX*` <br/> |
|Winie  <br/> | `ipm.externaldata.Winny*` <br/> |
|Yahoo!  <br/> | `ipm.externaldata.Yahoo!*` <br/> |
|Yammer  <br/> | `ipm.externaldata.Yammer*` <br/> |
|YellowEt  <br/> | `ipm.externaldata.YellowJacket*` <br/> |
|YouTube  <br/> | `ipm.externaldata.YouTube*` <br/> |
