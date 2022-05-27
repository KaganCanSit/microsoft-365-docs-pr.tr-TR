---
title: Gelişmiş tehdit avcılığı ile cihazlar, e-postalar, uygulamalar ve kimlikler arasında tehditleri avlama
description: Cihazlar, e-postalar, uygulamalar ve kimlikleri kapsayan yaygın tehdit avcılığı senaryolarını ve örnek sorguları inceleyin.
keywords: gelişmiş tehdit avcılığı, Office365 verileri, Windows cihazlar, Office365 e-postaları normalleştirme, e-postalar, uygulamalar, kimlikler, tehdit avcılığı, siber tehdit avcılığı, arama, sorgulama, telemetri, Microsoft 365, Microsoft 365 Defender
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: maccruz
author: schmurky
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: 0ca9a951ffd561113a806341d25bc1f0661732cc
ms.sourcegitcommit: a8fbaf4b441b5325004f7a2dacd9429ec9d80534
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/26/2022
ms.locfileid: "65739959"
---
# <a name="hunt-for-threats-across-devices-emails-apps-and-identities"></a>Cihazlar, e-postalar, uygulamalar ve kimlikler arasında tehditleri avlama

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Şunlar için geçerlidir:**
- Microsoft 365 Defender

Microsoft 365 Defender'da [gelişmiş avcılık](advanced-hunting-overview.md), aşağıdakiler arasında tehditleri proaktif olarak avlamanıza olanak tanır:
- Uç Nokta için Microsoft Defender tarafından yönetilen cihazlar
- Microsoft 365 tarafından işlenen e-postalar
- Microsoft Defender for Cloud Apps ve Kimlik için Microsoft Defender tarafından izlenen bulut uygulaması etkinlikleri, kimlik doğrulama olayları ve etki alanı denetleyicisi etkinlikleri

Bu görünürlük düzeyiyle, e-postaya veya web'e ulaşan karmaşık yetkisiz erişimler, yerel ayrıcalıkları yükseltme, ayrıcalıklı etki alanı kimlik bilgilerini alma ve cihazlarınız arasında yanlamasına geçiş yapma dahil olmak üzere ağınızın bölümlerinden geçen tehditleri hızla avlayabilirsiniz. 

Burada, bu tür gelişmiş tehditleri avlarken nasıl sorgular oluşturabilirsiniz keşfetmenize yardımcı olabilecek çeşitli tehdit avcılığı senaryolarına dayalı genel teknikler ve örnek sorgular verilmiştir.

## <a name="get-entity-info"></a>Varlık bilgilerini alma
Kullanıcı hesapları, cihazlar ve dosyalar hakkında nasıl hızlı bilgi alabileceğinizi öğrenmek için bu sorguları kullanın. 

### <a name="obtain-user-accounts-from-email-addresses"></a>E-posta adreslerinden kullanıcı hesaplarını alma
[Cihazlar ve e-postaları kapsayan tablolar](advanced-hunting-schema-tables.md) arasında sorgu oluştururken, büyük olasılıkla gönderen veya alıcı e-posta adreslerinden kullanıcı hesabı adları almanız gerekir. Bunu genellikle *e-posta adresinden yerel ana bilgisayarı* kullanarak alıcı veya gönderen adresi için yapabilirsiniz.

Aşağıdaki kod parçacığında [tostring()](/azure/data-explorer/kusto/query/tostringfunction) Kusto işlevini kullanarak yerel konağı sütunundaki `@` `RecipientEmailAddress`alıcı e-posta adreslerinden hemen önce ayıklarız.

```kusto
//Query snippet showing how to extract the account name from an email address
AccountName = tostring(split(RecipientEmailAddress, "@")[0])
```
Aşağıdaki sorguda bu kod parçacığının nasıl kullanılabileceğini gösterilmektedir:

```kusto
EmailEvents
| where Timestamp > ago(7d)
| project RecipientEmailAddress, AccountName = tostring(split(RecipientEmailAddress, "@")[0]);
```

### <a name="merge-the-identityinfo-table"></a>IdentityInfo tablosunu birleştirme

[IdentityInfo tablosunu](advanced-hunting-identityinfo-table.md) birleştirerek veya birleştirerek hesap adlarını ve diğer hesap bilgilerini alabilirsiniz. Aşağıdaki sorgu [EmailEvents tablosundan](advanced-hunting-emailevents-table.md) kimlik avı ve kötü amaçlı yazılım algılamalarının listesini alır ve her alıcı hakkında ayrıntılı bilgi almak için bu bilgileri tabloyla `IdentityInfo` birleştirir. 

```kusto
EmailEvents
| where Timestamp > ago(7d)
//Get email processing events where the messages were identified as either phishing or malware
| where ThreatTypes has "Malware" or ThreatTypes has "Phish"
//Merge email events with identity info to get recipient details
| join (IdentityInfo | distinct AccountUpn, AccountDisplayName, JobTitle, 
Department, City, Country) on $left.RecipientEmailAddress == $right.AccountUpn 
//Show important message and recipient details
| project Timestamp, NetworkMessageId, Subject, ThreatTypes, 
SenderFromAddress, RecipientEmailAddress, AccountDisplayName, JobTitle, 
Department, City, Country
```

Tabloları birleştirmek için Kusto Sorgu Dili nasıl kullanabileceğinizi öğrenmek için bu [kısa videoyu](https://www.youtube.com/watch?v=8qZx7Pp5XgM) izleyin.  

### <a name="get-device-information"></a>Cihaz bilgilerini alma

[Gelişmiş tehdit avcılığı şeması](advanced-hunting-schema-tables.md), çeşitli tablolarda kapsamlı cihaz bilgileri sağlar. Örneğin [, DeviceInfo tablosu](advanced-hunting-deviceinfo-table.md) düzenli olarak toplanan olay verilerini temel alan kapsamlı cihaz bilgileri sağlar. Bu sorgu, `DeviceInfo` güvenliği aşılmış olabilecek bir kullanıcının (`<account-name>`) herhangi bir cihazda oturum açıp açmadığını denetlemek için tabloyu kullanır ve ardından bu cihazlarda tetiklenen uyarıları listeler.

>[!Tip]
> Bu sorgu, için sol taraftaki değerlerin yinelenenleri kaldırmasını önleyen bir [iç birleşim](/azure/data-explorer/kusto/query/joinoperator?pivots=azuredataexplorer#inner-join-flavor) belirtmek için `DeviceId`kullanır`kind=inner`.

```kusto
DeviceInfo
//Query for devices that the potentially compromised account has logged onto
| where LoggedOnUsers contains '<account-name>'
| distinct DeviceId
//Crosscheck devices against alert records in AlertEvidence and AlertInfo tables
| join kind=inner AlertEvidence on DeviceId
| project AlertId
//List all alerts on devices that user has logged on to
| join AlertInfo on AlertId
| project AlertId, Timestamp, Title, Severity, Category 
```


### <a name="get-file-event-information"></a>Dosya olay bilgilerini alma

Dosyayla ilgili olaylar hakkında bilgi almak için aşağıdaki sorguyu kullanın. 

```kusto
DeviceInfo
| where Timestamp > ago(1d)
| where ClientVersion startswith "20.1"
| summarize by DeviceId
| join kind=inner (
    DeviceFileEvents 
    | where Timestamp > ago(1d)
) on DeviceId
| take 10
```


### <a name="get-network-event-information"></a>Ağ olayı bilgilerini alma

Ağ ile ilgili olaylar hakkında bilgi almak için aşağıdaki sorguyu kullanın.

```kusto
DeviceInfo
| where Timestamp > ago(1d)
| where ClientVersion startswith "20.1"
| summarize by DeviceId
| join kind=inner (
    DeviceNetworkEvents 
    | where Timestamp > ago(1d)
) on DeviceId
| take 10
```

### <a name="get-device-agent-version-information"></a>Cihaz aracısı sürüm bilgilerini alma

Bir cihazda çalışan aracının sürümünü almak için aşağıdaki sorguyu kullanın.

```kusto
DeviceInfo
| where Timestamp > ago(1d)
| where ClientVersion startswith "20.1"
| summarize by DeviceId
| join kind=inner (
    DeviceNetworkEvents 
    | where Timestamp > ago(1d)
) on DeviceId
| take 10
```


### <a name="example-query-for-macos-devices"></a>macOS cihazlar için örnek sorgu

Catalina'dan eski bir sürüme sahip macOS çalıştıran tüm cihazları görmek için aşağıdaki örnek sorguyu kullanın.

```kusto
DeviceInfo
| where Timestamp > ago(1d)
| where OSPlatform == "macOS" and  OSVersion !contains "10.15" and OSVersion !contains "11."
| summarize by DeviceId
| join kind=inner (
    DeviceInfo
    | where Timestamp > ago(1d)
) on DeviceId
| take 10
```

### <a name="get-device-status-info"></a>Cihaz durumu bilgilerini alma

Bir cihazın durumunu almak için aşağıdaki sorguyu kullanın. Aşağıdaki örnekte, sorgu cihazın eklenip eklenmediğini denetler.

```kusto
DeviceInfo
| where Timestamp > ago(1d)
| where OnboardingStatus != "Onboarded"
| summarize by DeviceId
| join kind=inner (
    DeviceInfo
    | where Timestamp > ago(1d)
) on DeviceId
| take 10
```


## <a name="hunting-scenarios"></a>Tehdit avcılığı senaryoları

### <a name="list-logon-activities-of-users-that-received-emails-that-were-not-zapped-successfully"></a>Başarıyla eşlenmemiş e-postalar alan kullanıcıların oturum açma etkinliklerini listeleme

[Sıfır saatlik otomatik temizleme (ZAP),](../office-365-security/zero-hour-auto-purge.md) alındıktan sonra kötü amaçlı e-postaları giderir. ZAP başarısız olursa, kötü amaçlı kod sonunda cihazda çalışabilir ve hesapları tehlikeye atabilir. Bu sorgu, ZAP tarafından başarıyla ele alınmayan e-postaların alıcıları tarafından yapılan oturum açma etkinliğini denetler.

```kusto
EmailPostDeliveryEvents 
| where Timestamp > ago(7d)
//List malicious emails that were not zapped successfully
| where ActionType has "ZAP" and ActionResult == "Error"
| project ZapTime = Timestamp, ActionType, NetworkMessageId , RecipientEmailAddress 
//Get logon activity of recipients using RecipientEmailAddress and AccountUpn
| join kind=inner IdentityLogonEvents on $left.RecipientEmailAddress == $right.AccountUpn
| where Timestamp between ((ZapTime-24h) .. (ZapTime+24h))
//Show only pertinent info, such as account name, the app or service, protocol, the target device, and type of logon
| project ZapTime, ActionType, NetworkMessageId , RecipientEmailAddress, AccountUpn, 
LogonTime = Timestamp, AccountDisplayName, Application, Protocol, DeviceName, LogonType
```

### <a name="get-logon-attempts-by-domain-accounts-targeted-by-credential-theft"></a>Kimlik bilgisi hırsızlığı tarafından hedeflenen etki alanı hesapları tarafından oturum açma girişimlerini alma

Bu sorgu önce tablodaki `AlertInfo` tüm kimlik bilgileri erişim uyarılarını tanımlar. Ardından tabloyu birleştirir veya birleştirir `AlertEvidence` ; bu tablo hedeflenen hesapların adları için ayrıştırılır ve yalnızca etki alanına katılmış hesaplar için filtreler. Son olarak, etki alanına katılmış hedeflenen hesaplar tarafından tüm oturum açma etkinliklerini almak için tabloyu denetler `IdentityLogonEvents` .

```kusto
AlertInfo
| where Timestamp > ago(30d)
//Get all credential access alerts
| where Category == "CredentialAccess"
//Get more info from AlertEvidence table to get the SID of the target accounts
| join AlertEvidence on AlertId
| extend IsJoined=(parse_json(AdditionalFields).Account.IsDomainJoined)
| extend TargetAccountSid=tostring(parse_json(AdditionalFields).Account.Sid)
//Filter for domain-joined accounts only
| where IsJoined has "true"
//Merge with IdentityLogonEvents to get all logon attempts by the potentially compromised target accounts
| join kind=inner IdentityLogonEvents on $left.TargetAccountSid == $right.AccountSid
//Show only pertinent info, such as account name, the app or service, protocol, the accessed device, and type of logon
| project AccountDisplayName, TargetAccountSid, Application, Protocol, DeviceName, LogonType
```

### <a name="check-if-files-from-a-known-malicious-sender-are-on-your-devices"></a>Bilinen bir kötü amaçlı gönderenden gelen dosyaların cihazlarınızda olup olmadığını denetleyin

Kötü amaçlı dosyalar`MaliciousSender@example.com` gönderen bir e-posta adresi ( ) bildiğinizi varsayarsak, bu gönderenden gelen dosyaların cihazlarınızda mevcut olup olmadığını belirlemek için bu sorguyu çalıştırabilirsiniz. Örneğin, bir kötü amaçlı yazılım dağıtım kampanyasından etkilenen cihazları tanımlamak için bu sorguyu kullanabilirsiniz.

```kusto
EmailAttachmentInfo
| where SenderFromAddress =~ "MaliciousSender@example.com"
//Get emails with attachments identified by a SHA-256
| where isnotempty(SHA256)
| join (
//Check devices for any activity involving the attachments
DeviceFileEvents
| project FileName, SHA256, DeviceName, DeviceId
) on SHA256
| project Timestamp, FileName , SHA256, DeviceName, DeviceId,  NetworkMessageId, SenderFromAddress, RecipientEmailAddress
```

### <a name="review-logon-attempts-after-receipt-of-malicious-emails"></a>Kötü amaçlı e-posta alındıktan sonra oturum açma girişimlerini gözden geçirme

Bu sorgu, bilinen kötü amaçlı e-postaları aldıktan sonra 30 dakika içinde e-posta alıcıları tarafından gerçekleştirilen en son 10 oturum açmayı bulur. E-posta alıcılarının hesaplarının gizliliğinin ihlal edilip edilmediğini denetlemek için bu sorguyu kullanabilirsiniz.

```kusto
//Define new table for malicious emails
let MaliciousEmails=EmailEvents
//List emails detected as malware, getting only pertinent columns
| where ThreatTypes has "Malware" 
| project TimeEmail = Timestamp, Subject, SenderFromAddress, AccountName = tostring(split(RecipientEmailAddress, "@")[0]);
MaliciousEmails
| join (
//Merge malicious emails with logon events to find logons by recipients
IdentityLogonEvents
| project LogonTime = Timestamp, AccountName, DeviceName
) on AccountName 
//Check only logons within 30 minutes of receipt of an email
| where (LogonTime - TimeEmail) between (0min.. 30min)
| take 10
```

### <a name="review-powershell-activities-after-receipt-of-emails-from-known-malicious-sender"></a>Bilinen kötü amaçlı gönderenden gelen e-postalar alındıktan sonra PowerShell etkinliklerini gözden geçirin

Kötü amaçlı e-postalar genellikle ek yükleri teslim etmek için PowerShell komutlarını çalıştıran belgeler ve diğer özel hazırlanmış ekleri içerir. Bilinen bir kötü amaçlı gönderenden (`MaliciousSender@example.com` ) gelen e-postaları biliyorsanız, gönderenden bir e-posta alındıktan sonra 30 dakika içinde gerçekleşen PowerShell etkinliklerini listelemek ve gözden geçirmek için bu sorguyu kullanabilirsiniz.  

```kusto
//Define new table for emails from specific sender
let EmailsFromBadSender=EmailEvents
| where SenderFromAddress =~ "MaliciousSender@example.com"
| project TimeEmail = Timestamp, Subject, SenderFromAddress, AccountName = tostring(split(RecipientEmailAddress, "@")[0]);
//Merge emails from sender with process-related events on devices
EmailsFromBadSender
| join (
DeviceProcessEvents
//Look for PowerShell activity
| where FileName =~ "powershell.exe"
//Add line below to check only events initiated by Outlook
//| where InitiatingProcessParentFileName =~ "outlook.exe"
| project TimeProc = Timestamp, AccountName, DeviceName, InitiatingProcessParentFileName, InitiatingProcessFileName, FileName, ProcessCommandLine
) on AccountName 
//Check only PowerShell activities within 30 minutes of receipt of an email
| where (TimeProc - TimeEmail) between (0min.. 30min)
```

## <a name="related-topics"></a>İlgili konular

- [Gelişmiş avcılığa genel bakış](advanced-hunting-overview.md)
- [Sorgu dilini öğrenin](advanced-hunting-query-language.md)
- [Sorgu sonuçlarıyla çalışın](advanced-hunting-query-results.md)
- [Paylaşılan sorguları kullanın](advanced-hunting-shared-queries.md)
- [Şemayı anlayın](advanced-hunting-schema-tables.md)
- [Sorgu en iyi yöntemlerini uygulayın](advanced-hunting-best-practices.md)
