---
title: EOP ve Office 365 için Defender güvenlik ayarları için Microsoft önerileri
keywords: Office 365 güvenlik önerileri, Gönderen İlkesi Çerçevesi, Etki Alanı Tabanlı İleti Raporlama ve Uyumluluk, DomainKeys Tanımlı Posta, adımlar, nasıl çalıştığı, güvenlik temelleri, EOP temelleri, Office 365 için Defender için temeller, Office 365 için Defender ayarlama, EOP'yi ayarlama, yapılandırma Office 365 için Defender, EOP'yi yapılandırma, güvenlik yapılandırması
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
ms.date: ''
manager: dansimp
audience: ITPro
ms.topic: conceptual
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: 6f64f2de-d626-48ed-8084-03cc72301aa4
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
description: Exchange Online Protection (EOP) ve Office 365 için Defender güvenlik ayarları için en iyi yöntemler nelerdir? Standart koruma için geçerli öneriler neleri içerir? Daha katı olmak istiyorsanız ne kullanılmalıdır? Ayrıca Office 365 için Defender kullanıyorsanız ne kadar ekstra alırsınız?
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 96eb39bf6cdf0ba110c7474e86a16b2e3a7e72fe
ms.sourcegitcommit: 1c8f54f9e7a7665bc10b5ef4a3d8c36e3e48f44c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/14/2022
ms.locfileid: "66078864"
---
# <a name="recommended-settings-for-eop-and-microsoft-defender-for-office-365-security"></a>EOP ve Office 365 için Microsoft Defender güvenliği için önerilen ayarlar

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Uygulandığı öğe**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Office 365 için Microsoft Defender plan 1 ve plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

**Exchange Online Protection (EOP),** Microsoft 365 abonelikler için güvenliğin temelidir ve kötü amaçlı e-postaların çalışanınızın gelen kutularına ulaşmasını engeller. Ancak her gün ortaya çıkan yeni ve daha gelişmiş saldırılarla, genellikle iyileştirilmiş korumalar gerekir. **Office 365 için Microsoft Defender** Plan 1 veya Plan 2, yöneticilere daha fazla güvenlik, denetim ve araştırma katmanı sağlayan ek özellikler içerir.

Güvenlik yöneticilerine güvenlik ayarlarını özelleştirme yetkisi verilmektedir ancak EOP ve Office 365 için Microsoft Defender iki güvenlik düzeyi vardır: **Standart** ve **Katı**. Müşteri ortamları ve ihtiyaçları farklı olsa da, bu filtreleme düzeyleri çoğu durumda istenmeyen postaların çalışanlarınızın Gelen Kutusuna ulaşmasını önlemeye yardımcı olur.

Standart veya Katı ayarları kullanıcılara otomatik olarak uygulamak için bkz. [EOP'de önceden ayarlanmış güvenlik ilkeleri ve Office 365 için Microsoft Defender](preset-security-policies.md).

Bu makalede varsayılan ayarlar ve kullanıcılarınızın korunmasına yardımcı olmak için önerilen Standart ve Katı ayarlar açıklanmaktadır. Tablolar, Microsoft 365 Defender portalındaki ve PowerShell'deki ayarları içerir (Exchange Online posta kutusu olmayan kuruluşlar için PowerShell veya tek başına Exchange Online Protection PowerShell Exchange Online).

> [!NOTE]
> PowerShell için Office 365 Gelişmiş Tehdit Koruması Önerilen Yapılandırma Çözümleyicisi (ORCA) modülü, (yöneticiler) bu ayarların geçerli değerlerini bulmanıza yardımcı olabilir. Özellikle **, Get-ORCAReport** cmdlet'i istenmeyen posta önleme, kimlik avı önleme ve diğer ileti hijyen ayarlarının bir değerlendirmesini oluşturur. ORCA modülünü adresinden <https://www.powershellgallery.com/packages/ORCA/>indirebilirsiniz.
>
> Microsoft 365 kuruluşlarda Gereksiz E-posta Filtresi'ni EOP'den gelen istenmeyen posta filtreleme kararlarıyla gereksiz çakışmaları (hem pozitif hem de negatif) önlemek için otomatik **filtreleme yok** olarak Outlook olarak bırakmanızı öneririz. Daha fazla bilgi için aşağıdaki makalelere bakın:
>
> - [Exchange Online posta kutularında gereksiz e-posta ayarlarını yapılandırma](configure-junk-email-settings-on-exo-mailboxes.md)
> - [Outlook'deki gereksiz e-posta ayarları hakkında](configure-junk-email-settings-on-exo-mailboxes.md#about-junk-email-settings-in-outlook)
> - [Gereksiz E-posta Filtresi'nde koruma düzeyini değiştirme](https://support.microsoft.com/en-us/office/e89c12d8-9d61-4320-8c57-d982c8d52f6b)
> - [EOP'de güvenilir gönderen listeleri oluşturma](create-safe-sender-lists-in-office-365.md)
> - [EOP'de engellenen gönderen listeleri oluşturma](create-block-sender-lists-in-office-365.md)

## <a name="anti-spam-anti-malware-and-anti-phishing-protection-in-eop"></a>EOP'de istenmeyen posta önleme, kötü amaçlı yazılımdan koruma ve kimlik avı koruması

İstenmeyen posta, kötü amaçlı yazılımdan koruma ve kimlik avı önleme, yöneticiler tarafından yapılandırılabilir EOP özellikleridir. Aşağıdaki Standart veya Katı yapılandırmaları öneririz.

### <a name="eop-anti-spam-policy-settings"></a>EOP istenmeyen posta önleme ilkesi ayarları

İstenmeyen posta önleme ilkeleri oluşturmak ve yapılandırmak için bkz. [EOP'de istenmeyen posta önleme ilkelerini yapılandırma](configure-your-spam-filter-policies.md).

|Güvenlik özelliği adı|Varsayılan|Standard|Sıkı|Açıklama ekleme|
|---|:---:|:---:|:---:|---|
|**İstenmeyen posta özellikleri & toplu e-posta eşiği**|||||
|**Toplu e-posta eşiği** <p> _BulkThreshold_|7|6|4|Ayrıntılar için bkz. [EOP'de toplu şikayet düzeyi (BCL).](bulk-complaint-level-values.md)|
|_MarkAsSpamBulkMail_|`On`|`On`|`On`|Bu ayar yalnızca PowerShell'de kullanılabilir.|
|**İstenmeyen posta puanı ayarlarını artırma**|Kapalı|Kapalı|Kapalı|Bu ayarların tümü Gelişmiş İstenmeyen Posta Filtresi'nin (ASF) bir parçasıdır. Daha fazla bilgi için bu makalenin [istenmeyen posta önleme ilkelerindeki ASF ayarları](#asf-settings-in-anti-spam-policies) bölümüne bakın.|
|**İstenmeyen posta ayarları olarak işaretle**|Kapalı|Kapalı|Kapalı|Bu ayarların çoğu ASF'nin bir parçasıdır. Daha fazla bilgi için bu makalenin [istenmeyen posta önleme ilkelerindeki ASF ayarları](#asf-settings-in-anti-spam-policies) bölümüne bakın.|
|**Belirli dilleri içerir** <p> _EnableLanguageBlockList_ <p> _LanguageBlockList_|**Kapalı** <p> `$false` <p> Boş|**Kapalı** <p> `$false` <p> Boş|**Kapalı** <p> `$false` <p> Boş|Bu ayar için belirli bir önerimiz yok. İş gereksinimlerinize göre belirli dillerde iletileri engelleyebilirsiniz.|
|**Bu ülkelerden** <p> _EnableRegionBlockList_ <p> _RegionBlockList_|**Kapalı** <p> `$false` <p> Boş|**Kapalı** <p> `$false` <p> Boş|**Kapalı** <p> `$false` <p> Boş|Bu ayar için belirli bir önerimiz yok. İş gereksinimlerinize göre belirli ülkelerden gelen iletileri engelleyebilirsiniz.|
|**Test modu** (_TestModeAction_)|**Hiçbiri**|**Hiçbiri**|**Hiçbiri**|Bu ayar ASF'nin bir parçasıdır. Daha fazla bilgi için bu makalenin [istenmeyen posta önleme ilkelerindeki ASF ayarları](#asf-settings-in-anti-spam-policies) bölümüne bakın.|
|**Eylem**||||**Karantina iletisini** seçtiğiniz her yerde **Karantina ilkesi** seçin kutusu kullanılabilir. Karantina ilkeleri, kullanıcıların karantinaya alınan iletilere ne yapmalarına izin verılacağını tanımlar. <p> Standart ve Katı önceden ayarlanmış güvenlik ilkeleri [, buradaki](quarantine-policies.md#step-2-assign-a-quarantine-policy-to-supported-features) tabloda açıklandığı gibi varsayılan karantina ilkelerini (AdminOnlyAccessPolicy veya DefaultFullAccessPolicy karantina bildirimleri olmadan) kullanır. <p> Yeni bir istenmeyen posta önleme ilkesi oluşturduğunuzda, boş bir değer varsayılan karantina ilkesinin söz konusu karar tarafından karantinaya alınan iletilerin geçmiş özelliklerini tanımlamak için kullanıldığı anlamına gelir ( **Yüksek güvenilirlikli kimlik avı** için karantina bildirimleri olmadan AdminOnlyAccessPolicy; Diğer her şey için karantina bildirimi olmayan DefaultFullAccessPolicy). <p> Yöneticiler, varsayılan veya özel istenmeyen posta önleme ilkelerinde kullanıcılar için daha kısıtlayıcı veya daha az kısıtlayıcı özellikler tanımlayan özel karantina ilkeleri oluşturabilir ve seçebilir. Daha fazla bilgi için bkz [. Karantina ilkeleri](quarantine-policies.md).|
|**İstenmeyen posta** algılama eylemi <p> _İstenmeyen Posta_|**İletiyi Gereksiz E-posta klasörüne taşıma** <p> `MoveToJmf`|**İletiyi Gereksiz E-posta klasörüne taşıma** <p> `MoveToJmf`|**Karantina iletisi** <p> `Quarantine`||
|**Yüksek güvenilirlikli istenmeyen posta** algılama eylemi <p> _HighConfidenceSpamAction_|**İletiyi Gereksiz E-posta klasörüne taşıma** <p> `MoveToJmf`|**Karantina iletisi** <p> `Quarantine`|**Karantina iletisi** <p> `Quarantine`||
|**Kimlik avı** algılama eylemi <p> _PhishSpamAction_|**İletiyi Gereksiz E-posta klasörüne taşıma**<sup>\*</sup> <p> `MoveToJmf`|**Karantina iletisi** <p> `Quarantine`|**Karantina iletisi** <p> `Quarantine`|<sup>\*</sup> Varsayılan değer, Varsayılan istenmeyen posta önleme ilkesinde ve PowerShell'de oluşturduğunuz yeni istenmeyen posta önleme ilkelerinde **iletiyi Gereksiz E-posta klasörüne taşı'dır** . Varsayılan değer, Microsoft 365 Defender portalında oluşturduğunuz yeni istenmeyen posta önleme ilkelerinde **karantina iletisidir**.|
|**Yüksek güvenilirlikli kimlik avı** algılama eylemi <p> _HighConfidencePhishAction_|**Karantina iletisi** <p> `Quarantine`|**Karantina iletisi** <p> `Quarantine`|**Karantina iletisi** <p> `Quarantine`||
|**Toplu** algılama eylemi <p> _BulkSpamAction_|**İletiyi Gereksiz E-posta klasörüne taşıma** <p> `MoveToJmf`|**İletiyi Gereksiz E-posta klasörüne taşıma** <p> `MoveToJmf`|**Karantina iletisi** <p> `Quarantine`||
|**İstenmeyen postaları bu kadar gün boyunca karantinada tutma** <p> _QuarantineRetentionPeriod_|15 gün<sup>\*</sup>|30 gün|30 gün|<sup>\*</sup> Varsayılan değer, varsayılan istenmeyen posta önleme ilkesinde ve PowerShell'de oluşturduğunuz yeni istenmeyen posta önleme ilkelerinde 15 gündür. varsayılan değer, Microsoft 365 Defender portalında oluşturduğunuz yeni istenmeyen posta önleme ilkelerinde 30 gündür. <p> Bu değer, kimlik avı önleme ilkeleri tarafından karantinaya alınan iletileri de etkiler. Daha fazla bilgi için bkz. [EOP'de karantinaya alınan e-posta iletileri](quarantine-email-messages.md).|
|**İstenmeyen posta güvenliği ipuçlarını etkinleştirme** <p> _InlineSafetyTipsEnabled_|Seçili <p> `$true`|Seçili <p> `$true`|Seçili <p> `$true`||
|Kimlik avı iletileri için sıfır saatlik otomatik temizlemeyi (ZAP) etkinleştirme <p> _PhishZapEnabled_|Seçili <p> `$true`|Seçili <p> `$true`|Seçili <p> `$true`||
|İstenmeyen posta iletileri için ZAP'i etkinleştirme <p> _SpamZapEnabled_|Seçili <p> `$true`|Seçili <p> `$true`|Seçili <p> `$true`||
|**& engelleme listesine izin ver**|||||
|İzin verilen gönderenler <p> _AllowedSenders_|Yok|Yok|Yok||
|İzin verilen gönderen etki alanları <p> _AllowedSenderDomains_|Yok|Yok|Yok|İzin verilen gönderenler listesine etki alanları eklemek çok kötü bir fikirdir. Saldırganlar, aksi takdirde filtrelenecek e-postaları size gönderebilir. <p> Kuruluşunuzun e-posta etki alanlarında gönderen e-posta adreslerini sahtekarlık yapan veya dış etki alanlarında gönderen e-posta adreslerini sahtekarlık yapan tüm gönderenleri gözden geçirmek için kimlik sahtekarlığına ilişkin bilgi sahtekarlık [içgörülerini](learn-about-spoof-intelligence.md) ve [Kiracı İzin Ver/Engelle Listesi'ni](tenant-allow-block-list.md) kullanın.|
|Engellenen gönderenler <p> _BlockedSenders_|Yok|Yok|Yok||
|Engellenen gönderen etki alanları <p> _BlockedSenderDomains_|Yok|Yok|Yok||

#### <a name="asf-settings-in-anti-spam-policies"></a>İstenmeyen posta önleme ilkelerinde ASF ayarları

Bu bölümdeki tabloda, istenmeyen posta önleme ilkelerinde kullanılabilen Gelişmiş İstenmeyen Posta Filtresi (ASF) ayarları açıklanmaktadır. Bu ayarların tümü hem **Standart** hem de **Katı** düzeyler için **Kapalıdır**. ASF ayarları hakkında daha fazla bilgi için bkz. [EOP'de Gelişmiş İstenmeyen Posta Filtresi (ASF) ayarları](advanced-spam-filtering-asf-options.md).

|Güvenlik özelliği adı|Açıklama ekleme|
|---|---|
|**Uzak sitelere resim bağlantıları** (_IncreaseScoreWithImageLinks_)||
|**URL'deki sayısal IP adresi** (_IncreaseScoreWithNumericIps_)||
|**URL'yi başka bir bağlantı noktasına yönlendirme** (_IncreaseScoreWithRedirectToOtherPort_)||
|**.biz veya .info web sitelerine bağlantılar** (_IncreaseScoreWithBizOrInfoUrls_)||
|**Boş iletiler** (_MarkAsSpamEmptyMessages_)||
|**HTML'ye etiket ekleme** (_MarkAsSpamEmbedTagsInHtml_)||
|**HTML'de JavaScript veya VBScript** (_MarkAsSpamJavaScriptInHtml_)||
|**HTML'de form etiketleri** (_MarkAsSpamFormTagsInHtml_)||
|**HTML'de çerçeve veya iframe etiketleri** (_MarkAsSpamFramesInHtml_)||
|**HTML'deki web hataları** (_MarkAsSpamWebBugsInHtml_)||
|**HTML'deki nesne etiketleri** (_MarkAsSpamObjectTagsInHtml_)||
|**Hassas sözcükler** (_MarkAsSpamSensitiveWordList_)||
|**SPF kaydı: sabit başarısız (**_MarkAsSpamSpfRecordHardFail_)||
|**Gönderen Kimliği filtreleme sabit başarısız (**_MarkAsSpamFromAddressAuthFail_)||
|**Backscatter** (_MarkAsSpamNdrBackscatter_)||
|**Test modu** (_TestModeAction_)|Eylem olarak **Test'i** destekleyen ASF ayarları için, test modu eylemini **Yok**, **Varsayılan X Üst Bilgisi metni ekle** veya **Gizli İleti Gönder** (`None`, `AddXHeader`veya `BccMessage`) olarak yapılandırabilirsiniz. Daha fazla bilgi için bkz [. ASF ayarlarını etkinleştirme, devre dışı bırakma veya test edin](advanced-spam-filtering-asf-options.md#enable-disable-or-test-asf-settings).|

#### <a name="eop-outbound-spam-policy-settings"></a>EOP giden istenmeyen posta ilkesi ayarları

Giden istenmeyen posta ilkeleri oluşturmak ve yapılandırmak için bkz. [EOP'de giden istenmeyen posta filtrelemesini yapılandırma](configure-the-outbound-spam-policy.md).

Hizmetteki varsayılan gönderme sınırları hakkında daha fazla bilgi için bkz [. Gönderme sınırları](/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits#sending-limits-1).

> [!NOTE]
> Giden istenmeyen posta ilkeleri Standart veya Katı önceden ayarlanmış güvenlik ilkelerinin bir parçası değildir. **Standart** ve **Katı** değerleri, oluşturduğunuz varsayılan giden istenmeyen posta ilkesinde veya özel giden istenmeyen posta ilkelerinde **önerilen** değerlerimizi gösterir.

|Güvenlik özelliği adı|Varsayılan|Önerilen<br/>Standard|Önerilen<br/>Sıkı|Açıklama ekleme|
|---|:---:|:---:|:---:|---|
|**Dış ileti sınırı ayarlama** <p> _RecipientLimitExternalPerHour_|0|500|400|Varsayılan değer 0, hizmet varsayılanlarını kullanma anlamına gelir.|
|**İç ileti sınırı ayarlama** <p> _RecipientLimitInternalPerHour_|0|1000|800|Varsayılan değer 0, hizmet varsayılanlarını kullanma anlamına gelir.|
|**Günlük ileti sınırı ayarlama** <p> _RecipientLimitPerDay_|0|1000|800|Varsayılan değer 0, hizmet varsayılanlarını kullanma anlamına gelir.|
|**İleti sınırına ulaşan kullanıcılara getirilen kısıtlama** <p> _ActionWhenThresholdReached_|**Kullanıcının posta göndermesini bir sonraki güne kadar kısıtlayın** <p> `BlockUserForToday`|**Kullanıcının posta göndermesini kısıtlama** <p> `BlockUser`|**Kullanıcının posta göndermesini kısıtlama** <p> `BlockUser`||
|**Otomatik iletme kuralları** <p> _AutoForwardingMode_|**Otomatik - Sistem kontrollü** <p> `Automatic`|**Otomatik - Sistem kontrollü** <p> `Automatic`|**Otomatik - Sistem kontrollü** <p> `Automatic`|
|**Bu sınırları aşan giden iletilerin bir kopyasını bu kullanıcılara ve gruplara gönder** <p> _BccSuspiciousOutboundMail_ <p> _BccSuspiciousOutboundAdditionalRecipients_|Seçili değil <p> `$false` <p> Boş|Seçili değil <p> `$false` <p> Boş|Seçili değil <p> `$false` <p> Boş|Bu ayar için belirli bir önerimiz yok. <p> Bu ayar yalnızca varsayılan giden istenmeyen posta ilkesinde çalışır. Oluşturduğunuz özel giden istenmeyen posta ilkelerinde çalışmaz.|
|**Bir gönderen giden istenmeyen posta gönderdiği için engellendiyse bu kullanıcıları ve grupları bilgilendirin** <p> _NotifyOutboundSpam_ <p> _NotifyOutboundSpamRecipients_|Seçili değil <p> `$false` <p> Boş|Seçili değil <p> `$false` <p> Boş|Seçili değil <p> `$false` <p> Boş|**Kullanıcı'nın e-posta göndermesi kısıtlandı** adlı varsayılan [uyarı ilkesi](../../compliance/alert-policies.md), ilkedeki sınırları aştığı için kullanıcılar engellendiğinde **TenantAdmins** (**Genel yöneticiler**) grubunun üyelerine zaten e-posta bildirimleri gönderir. **Yöneticileri ve diğer kullanıcıları bilgilendirmek için giden istenmeyen posta ilkesinde bu ayar yerine uyarı ilkesini kullanmanızı kesinlikle öneririz**. Yönergeler için bkz [. Kısıtlı kullanıcılar için uyarı ayarlarını doğrulama](removing-user-from-restricted-users-portal-after-spam.md#verify-the-alert-settings-for-restricted-users).|

### <a name="eop-anti-malware-policy-settings"></a>EOP kötü amaçlı yazılımdan koruma ilkesi ayarları

Kötü amaçlı yazılımdan koruma ilkeleri oluşturmak ve yapılandırmak için bkz. [EOP'de kötü amaçlı yazılımdan koruma ilkelerini yapılandırma](configure-anti-malware-policies.md).

|Güvenlik özelliği adı|Varsayılan|Standard|Sıkı|Açıklama ekleme|
|---|:---:|:---:|:---:|---|
|**Koruma ayarları**|||||
|**Ortak ekler filtresini etkinleştirme** <p> _EnableFileFilter_|Seçili değil <p> `$false`|Seçili <p> `$true`|Seçili <p> `$true`|Bu ayar, dosya türüne bağlı olarak, ek içeriğine bakılmaksızın yürütülebilir ekler içeren iletileri karantinaya alır.|
|**Kötü amaçlı yazılım için sıfır saatlik otomatik temizlemeyi etkinleştirme** <p> _ZapEnabled_|Seçili <p> `$true`|Seçili <p> `$true`|Seçili <p> `$true`||
|**Karantina ilkesi**|AdminOnlyAccessPolicy|AdminOnlyAccessPolicy|AdminOnlyAccessPolicy|Yeni bir kötü amaçlı yazılımdan koruma ilkesi oluşturduğunuzda boş bir değer, kötü amaçlı yazılım olarak karantinaya alınan iletilerin geçmiş özelliklerini tanımlamak için varsayılan karantina ilkesinin kullanıldığı anlamına gelir (Karantina bildirimleri olmadan AdminOnlyAccessPolicy). <p> Standart ve Katı önceden ayarlanmış güvenlik ilkeleri [, buradaki](quarantine-policies.md#step-2-assign-a-quarantine-policy-to-supported-features) tabloda açıklandığı gibi varsayılan karantina ilkesini (Karantina bildirimleri olmadan AdminOnlyAccessPolicy) kullanır. <p> Yöneticiler, varsayılan veya özel kötü amaçlı yazılımdan koruma ilkelerinde kullanıcılar için daha fazla özellik tanımlayan özel karantina ilkeleri oluşturabilir ve seçebilir. Daha fazla bilgi için bkz [. Karantina ilkeleri](quarantine-policies.md).|
|**Alıcı bildirimleri**|||||
|**İletiler kötü amaçlı yazılım olarak karantinaya alındığında alıcılara bildirme** <p> _Eylem_|Seçili değil <p> _DeleteMessage_|Seçili değil <p> _DeleteMessage_|Seçili değil <p> _DeleteMessage_|E-posta ekinde kötü amaçlı yazılım algılanırsa, ileti karantinaya alınır ve yalnızca bir yönetici tarafından yayımlanabilir.|
|**Gönderen bildirimleri**|||||
|**İletiler kötü amaçlı yazılım olarak karantinaya alındığında iç gönderenlere bildirme** <p> _EnableInternalSenderNotifications_|Seçili değil <p> `$false`|Seçili değil <p> `$false`|Seçili değil <p> `$false`||
|**İletiler kötü amaçlı yazılım olarak karantinaya alındığında dış gönderenlere bildirme** <p> _EnableExternalSenderNotifications_|Seçili değil <p> `$false`|Seçili değil <p> `$false`|Seçili değil <p> `$false`||
|**Yönetici bildirimleri**|||||
|**İç gönderenlerden gelen teslim edilmemiş iletiler hakkında yöneticiyi bilgilendirme** <p> _EnableInternalSenderAdminNotifications_ <p> _InternalSenderAdminAddress_|Seçili değil <p> `$false`|Seçili değil <p> `$false`|Seçili değil <p> `$false`|Bu ayar için belirli bir önerimiz yok.|
|**Dış gönderenlerden gelen teslim edilmemiş iletiler hakkında yöneticiye bildirme** <p> _EnableExternalSenderAdminNotifications_ <p> _ExternalSenderAdminAddress_|Seçili değil <p> `$false`|Seçili değil <p> `$false`|Seçili değil <p> `$false`|Bu ayar için belirli bir önerimiz yok.|
|**Bildirimleri özelleştirme**||||Bu ayarlar için belirli bir önerimiz yok.|
|**Özelleştirilmiş bildirim metnini kullanma** <p> _CustomNotifications_|Seçili değil <p> `$false`|Seçili değil <p> `$false`|Seçili değil <p> `$false`||
|**Kimden adı** <p> _CustomFromName_|Boş <p> `$null`|Boş <p> `$null`|Boş <p> `$null`||
|**Kimden adresi** <p> _CustomFromAddress_|Boş <p> `$null`|Boş <p> `$null`|Boş <p> `$null`||
|**İç gönderenlerden gelen iletiler için bildirimleri özelleştirme**||||Bu ayarlar yalnızca **, iletiler kötü amaçlı yazılım olarak karantinaya alındığında iç gönderenleri bilgilendir** veya **İç gönderenlerden teslim edilmemiş iletileri yöneticiye bildir** seçiliyse kullanılır.|
|**Konu** <p> _CustomInternalSubject_|Boş <p> `$null`|Boş <p> `$null`|Boş <p> `$null`||
|**İleti** <p> _CustomInternalBody_|Boş <p> `$null`|Boş <p> `$null`|Boş <p> `$null`||
|**Dış gönderenlerden gelen iletiler için bildirimleri özelleştirme**||||Bu ayarlar yalnızca **, iletiler kötü amaçlı yazılım olarak karantinaya alındığında dış gönderenlere bildir** veya **Dış gönderenlerden gelen teslim edilmemiş iletiler hakkında yöneticiye bildir** seçildiğinde kullanılır.|
|**Konu** <p> _CustomExternalSubject_|Boş <p> `$null`|Boş <p> `$null`|Boş <p> `$null`||
|**İleti** <p> _CustomExternalBody_|Boş <p> `$null`|Boş <p> `$null`|Boş <p> `$null`||

### <a name="eop-anti-phishing-policy-settings"></a>EOP kimlik avı önleme ilkesi ayarları

Bu ayarlar hakkında daha fazla bilgi için bkz. [Kimlik sahtekarlık ayarları](set-up-anti-phishing-policies.md#spoof-settings). Bu ayarları yapılandırmak için bkz. [EOP'de kimlik avı önleme ilkelerini yapılandırma](configure-anti-phishing-policies-eop.md).

Kimlik sahtekarlığı ayarları birbiriyle ilişkilidir, ancak **İlk kişiyi göster güvenlik ipucu** ayarının kimlik sahtekarlığı ayarlarına bağımlılığı yoktur.

|Güvenlik özelliği adı|Varsayılan|Standard|Sıkı|Açıklama ekleme|
|---|:---:|:---:|:---:|---|
|**Kimlik avı eşiği & koruma**|||||
|**Kimlik sahtekarı zekasını etkinleştirme** <p> _EnableSpoofIntelligence_|Seçili <p> `$true`|Seçili <p> `$true`|Seçili <p> `$true`||
|**Eylem**|||||
|**İletinin yanıltma olarak algılanırsa** <p> _AuthenticationFailAction_|**İletiyi alıcıların Gereksiz E-posta klasörlerine taşıma** <p> `MoveToJmf`|**İletiyi alıcıların Gereksiz E-posta klasörlerine taşıma** <p> `MoveToJmf`|**İletiyi karantinaya al** <p> `Quarantine`|Bu ayar, kimlik sahtekarlığı [bilgileri içgörülerinde](learn-about-spoof-intelligence.md) gösterildiği gibi otomatik olarak engellenen veya [Kiracı İzin Ver/Engelle Listesi'nde](tenant-allow-block-list.md) el ile engellenen sahte gönderenler için geçerlidir. <p> **İletiyi karantinaya al'ı** seçerseniz, kullanıcıların kimlik sahtekarlığına karşı **karantinaya** alınan iletilere ne yapmalarına izin verildiğini tanımlayan karantina ilkesini seçmek için bir Karantina ilkesi uygula kutusu kullanılabilir. Yeni bir kimlik avı önleme ilkesi oluşturduğunuzda boş bir değer, kimlik sahtekarlığı olarak karantinaya alınan iletilerin geçmiş özelliklerini tanımlamak için varsayılan karantina ilkesinin kullanıldığı anlamına gelir (Karantina bildirimleri olmadan DefaultFullAccessPolicy). <p> Standart ve Katı önceden ayarlanmış güvenlik ilkeleri [, buradaki](quarantine-policies.md#step-2-assign-a-quarantine-policy-to-supported-features) tabloda açıklandığı gibi varsayılan karantina ilkesini (Karantina bildirimleri olmadan DefaultFullAccessPolicy) kullanır. <p> Yöneticiler, varsayılan veya özel kimlik avı önleme ilkelerinde kullanıcılar için daha kısıtlayıcı veya daha az kısıtlayıcı özellikler tanımlayan özel karantina ilkeleri oluşturabilir ve seçebilir. Daha fazla bilgi için bkz [. Karantina ilkeleri](quarantine-policies.md).|
|**İlk kişi güvenlik ipucu göster** <p> _EnableFirstContactSafetyTips_|Seçili değil <p> `$false`|Seçili değil <p> `$false`|Seçili değil <p> `$false`|Daha fazla bilgi için bkz. [İlk kişi güvenlik ipucu](set-up-anti-phishing-policies.md#first-contact-safety-tip).|
|**Kimlik sahtekarlığına yönelik kimliği doğrulanmamış gönderenler için göster (?)** <p> _EnableUnauthenticatedSender_|Seçili <p> `$true`|Seçili <p> `$true`|Seçili <p> `$true`|Kimliği belirsiz gönderenler için Outlook'da gönderenin fotoğrafına soru işareti (?) ekler. Daha fazla bilgi için bkz. [Kimliği doğrulanmamış gönderen göstergeleri](set-up-anti-phishing-policies.md#unauthenticated-sender-indicators).|
|**"via" etiketini göster** <p> _EnableViaTag_|Seçili <p> `$true`|Seçili <p> `$true`|Seçili <p> `$true`|DKIM imzasında etki alanından veya **MAIL FROM** adresinden farklıysa Kimden adresine bir via etiketi (fabrikam.com aracılığıyla chris@contoso.com) ekler. <p> Daha fazla bilgi için bkz. [Kimliği doğrulanmamış gönderen göstergeleri](set-up-anti-phishing-policies.md#unauthenticated-sender-indicators).|

## <a name="microsoft-defender-for-office-365-security"></a>güvenlik Office 365 için Microsoft Defender

Ek güvenlik avantajları, Office 365 için Microsoft Defender bir abonelikle birlikte gelir. En son haberler ve bilgiler için [Office 365 için Defender'deki yenilikler'i](whats-new-in-defender-for-office-365.md) görebilirsiniz.

> [!IMPORTANT]
>
> - Office 365 için Microsoft Defender'daki varsayılan kimlik avı önleme ilkesi, tüm alıcılar için [kimlik sahtekarlığı koruması](set-up-anti-phishing-policies.md#spoof-settings) ve posta kutusu zekası sağlar. Ancak, diğer kullanılabilir [kimliğe bürünme koruması](#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365) özellikleri ve [gelişmiş ayarlar](#advanced-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365) varsayılan ilkede yapılandırılmaz veya etkinleştirilmez. Tüm koruma özelliklerini etkinleştirmek için varsayılan kimlik avı önleme ilkesini değiştirin veya ek kimlik avı önleme ilkeleri oluşturun.
>
> - Varsayılan Kasa Ekler ilkesi veya Kasa Bağlantıları ilkesi olmasa **da, Yerleşik koruma** önceden ayarlanmış güvenlik ilkesi, özel Kasa Ekler ilkelerine veya Kasa Bağlantıları ilkelerine henüz dahil olmayan alıcılara Kasa Ekler koruması ve Kasa Bağlantılar koruması sağlar. Daha fazla bilgi için bkz. [EOP'de önceden ayarlanmış güvenlik ilkeleri ve Office 365 için Microsoft Defender](preset-security-policies.md).
>
> - [Kasa SharePoint, OneDrive, Microsoft Teams](mdo-for-spo-odb-and-teams.md) koruması ve [Kasa Belgeler koruması için eklerin](safe-docs.md) Kasa Bağlantıları ilkelerine bağımlılığı yoktur.

Aboneliğinizde Office 365 için Microsoft Defender varsa veya Office 365 için Defender eklenti olarak satın aldıysanız aşağıdaki Standart veya Katı yapılandırmaları ayarlayın.

### <a name="anti-phishing-policy-settings-in-microsoft-defender-for-office-365"></a>Office 365 için Microsoft Defender kimlik avı önleme ilkesi ayarları

EOP müşterileri daha önce açıklandığı gibi temel kimlik avı önleme özelliğine sahiptir, ancak Office 365 için Defender saldırıları önlemeye, algılamaya ve bunlara karşı düzeltmeye yardımcı olmak için daha fazla özellik ve denetim içerir. Bu ilkeleri oluşturmak ve yapılandırmak için bkz. [Office 365 için Defender'de kimlik avı önleme ilkelerini yapılandırma](configure-mdo-anti-phishing-policies.md).

#### <a name="advanced-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365"></a>Office 365 için Microsoft Defender'de kimlik avı önleme ilkelerindeki gelişmiş ayarlar

Bu ayar hakkında daha fazla bilgi için bkz. [Office 365 için Microsoft Defender'de kimlik avı önleme ilkelerinde gelişmiş kimlik avı eşikleri](set-up-anti-phishing-policies.md#advanced-phishing-thresholds-in-anti-phishing-policies-in-microsoft-defender-for-office-365). Bu ayarı yapılandırmak için bkz. [Office 365 için Defender'de kimlik avı önleme ilkelerini yapılandırma](configure-mdo-anti-phishing-policies.md).

|Güvenlik özelliği adı|Varsayılan|Standard|Sıkı|Açıklama ekleme|
|---|:---:|:---:|:---:|---|
|**Kimlik avı e-posta eşiği** <p> _PhishThresholdLevel_|**1 - Standart** <p> `1`|**2 - Agresif** <p> `2`|**3 - Daha agresif** <p> `3`||

#### <a name="impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365"></a>Office 365 için Microsoft Defender kimlik avı önleme ilkelerindeki kimliğe bürünme ayarları

Bu ayarlar hakkında daha fazla bilgi için bkz[. Office 365 için Microsoft Defender kimlik avı önleme ilkelerindeki kimliğe bürünme ayarları](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365). Bu ayarları yapılandırmak için bkz. [Office 365 için Defender'de kimlik avı önleme ilkelerini yapılandırma](configure-mdo-anti-phishing-policies.md).

|Güvenlik özelliği adı|Varsayılan|Standard|Sıkı|Açıklama ekleme|
|---|:---:|:---:|:---:|---|
|**Kimlik avı eşiği & koruma**|||||
|**Kullanıcıların korumasını sağlama** (kimliğine bürünülen kullanıcı koruması) <p> _EnableTargetedUserProtection_ <p> _TargetedUsersToProtect_|Seçili değil <p> `$false` <p> yok|Seçili <p> `$true` <p> \<list of users\>|Seçili <p> `$true` <p> \<list of users\>|Önemli rollere kullanıcı (ileti gönderenler) eklemenizi öneririz. Dahili olarak, korunan gönderenler CEO'nuz, CFO'nuz ve diğer üst düzey liderler olabilir. Dışarıdan, korunan gönderenler konsey üyelerini veya yönetim kurulunuzu içerebilir.|
|**Etki alanlarının korunmasını etkinleştirme** (kimliğine bürünülen etki alanı koruması)|Seçili değil|Seçili|Seçili||
|**Sahip olduğum etki alanlarını dahil et** <p> _EnableOrganizationDomainsProtection_|Kapalı <p> `$false`|Seçili <p> `$true`|Seçili <p> `$true`||
|**Özel etki alanları ekleme** <p> _EnableTargetedDomainsProtection_ <p> _TargetedDomainsToProtect_|Kapalı <p> `$false` <p> yok|Seçili <p> `$true` <p> \<list of domains\>|Seçili <p> `$true` <p> \<list of domains\>|Sahip olmadığınız ancak sık sık etkileşimde olduğunuz etki alanlarını (gönderen etki alanları) eklemenizi öneririz.|
|**Güvenilir gönderenler ve etki alanları ekleme** <p> _ExcludedSenders_ <p> _ExcludedDomains_|Yok|Yok|Yok|Kuruluşunuza bağlı olarak, kimliğine bürünme girişimleri olarak yanlış tanımlanan gönderenler veya etki alanları eklemenizi öneririz.|
|**Posta kutusu zekasını etkinleştirme** <p> _EnableMailboxIntelligence_|Seçili <p> `$true`|Seçili <p> `$true`|Seçili <p> `$true`||
|**Kimliğe bürünme koruması için zekayı etkinleştirme** <p> _EnableMailboxIntelligenceProtection_|Kapalı <p> `$false`|Seçili <p> `$true`|Seçili <p> `$true`|Bu ayar, posta kutusu zekası tarafından kimliğe bürünme algılamaları için belirtilen eyleme izin verir.|
|**Eylem**||||**İletiyi karantinaya al'ı** seçtiğinizde **, Karantina ilkesi** seçin kutusu kullanılabilir. Karantina ilkeleri, kullanıcıların karantinaya alınan iletilere ne yapmalarına izin verılacağını tanımlar. <p> Standart ve Katı önceden ayarlanmış güvenlik ilkeleri [, buradaki](quarantine-policies.md#step-2-assign-a-quarantine-policy-to-supported-features) tabloda açıklandığı gibi varsayılan karantina ilkesini (Karantina bildirimleri olmadan DefaultFullAccessPolicy) kullanır. <p> Yeni bir kimlik avı önleme ilkesi oluşturduğunuzda, boş bir değer varsayılan karantina ilkesinin bu karar tarafından karantinaya alınan iletilerin geçmiş özelliklerini tanımlamak için kullanıldığı anlamına gelir (tüm kimliğe bürünme algılama türleri için DefaultFullAccessPolicy). <p> Yöneticiler, varsayılan veya özel kimlik avı önleme ilkelerindeki kullanıcılar için daha az kısıtlayıcı veya daha kısıtlayıcı özellikler tanımlayan özel karantina ilkeleri oluşturabilir ve seçebilir. Daha fazla bilgi için bkz [. Karantina ilkeleri](quarantine-policies.md).|
|**İleti kimliğine bürünülen bir kullanıcı olarak algılanırsa** <p> _TargetedUserProtectionAction_|**Hiçbir eylem uygulama** <p> `NoAction`|**İletiyi karantinaya al** <p> `Quarantine`|**İletiyi karantinaya al** <p> `Quarantine`||
|**İleti kimliğine bürünülen bir etki alanı olarak algılanırsa** <p> _TargetedDomainProtectionAction_|**Hiçbir eylem uygulama** <p> `NoAction`|**İletiyi karantinaya al** <p> `Quarantine`|**İletiyi karantinaya al** <p> `Quarantine`||
|**Posta kutusu zekası algılarsa ve kimliğine bürünülen kullanıcı** <p> _MailboxIntelligenceProtectionAction_|**Hiçbir eylem uygulama** <p> `NoAction`|**İletiyi alıcıların Gereksiz E-posta klasörlerine taşıma** <p> `MoveToJmf`|**İletiyi karantinaya al** <p> `Quarantine`||
|**Kullanıcı kimliğe bürünme güvenlik ipucu göster** <p> _EnableSimilarUsersSafetyTips_|Kapalı <p> `$false`|Seçili <p> `$true`|Seçili <p> `$true`||
|**Etki alanı kimliğe bürünme güvenlik ipucu göster** <p> _EnableSimilarDomainsSafetyTips_|Kapalı <p> `$false`|Seçili <p> `$true`|Seçili <p> `$true`||
|**Kullanıcı kimliğine bürünme olağan dışı karakterleri güvenlik ipucu gösterme** <p> _EnableUnusualCharactersSafetyTips_|Kapalı <p> `$false`|Seçili <p> `$true`|Seçili <p> `$true`||

#### <a name="eop-anti-phishing-policy-settings-in-microsoft-defender-for-office-365"></a>Office 365 için Microsoft Defender'da EOP kimlik avı önleme ilkesi ayarları

Bunlar [, EOP'deki istenmeyen posta önleme ilkesi ayarlarında kullanılabilen ayarlarla](#eop-anti-spam-policy-settings) aynıdır.

### <a name="safe-attachments-settings"></a>ek ayarlarını Kasa

Office 365 için Microsoft Defender Kasa Ekleri, Kasa Ekler ilkeleriyle ilişkisi olmayan genel ayarları ve her Kasa Bağlantıları ilkesine özgü ayarları içerir. Daha fazla bilgi için bkz. [Office 365 için Defender ekleri Kasa](safe-attachments.md).

Varsayılan Kasa Ekler ilkesi olmasa **da Yerleşik koruma** önceden ayarlanmış güvenlik ilkesi, özel Kasa Ekler ilkelerine henüz dahil olmayan tüm alıcılara Kasa Ekler koruması sağlar. Daha fazla bilgi için bkz. [EOP'de önceden ayarlanmış güvenlik ilkeleri ve Office 365 için Microsoft Defender](preset-security-policies.md).

#### <a name="global-settings-for-safe-attachments"></a>Kasa Ekleri için genel ayarlar

> [!NOTE]
> Kasa Ekleri için genel ayarlar **Yerleşik koruma** önceden ayarlanmış güvenlik ilkesi tarafından ayarlanır, ancak **Standart** veya **Katı** önceden belirlenmiş güvenlik ilkeleri tarafından ayarlanmaz. Her iki durumda da yöneticiler bu genel Kasa Ek ayarlarını istedikleri zaman değiştirebilir.
>
> **Varsayılan** sütun **, Yerleşik koruma** önceden ayarlanmış güvenlik ilkesinin varlığından önceki değerleri gösterir. **Yerleşik koruma** sütunu, yerleşik **koruma** önceden ayarlanmış güvenlik ilkesi tarafından ayarlanan değerleri gösterir ve bunlar da önerilen değerlerimizdir.

Bu ayarları yapılandırmak için bkz. [SharePoint, OneDrive ve Microsoft Teams için Kasa Eklerini açma ve](turn-on-mdo-for-spo-odb-and-teams.md) [Microsoft 365 E5'da Belgeleri Kasa](safe-docs.md).

PowerShell'de, bu ayarlar için [Set-AtpPolicyForO365](/powershell/module/exchange/set-atppolicyforo365) cmdlet'ini kullanırsınız.

|Güvenlik özelliği adı|Varsayılan|Yerleşik koruma|Açıklama ekleme|
|---|:---:|:---:|---|
|**SharePoint, OneDrive ve Microsoft Teams için Office 365 için Defender açma** <p> _EnableATPForSPOTeamsODB_|Kapalı <p> `$false`|-Inı <p> `$true`|Kullanıcıların kötü amaçlı dosyaları indirmesini önlemek için bkz. [Kullanıcıların kötü amaçlı dosyaları indirmesini önlemek için çevrimiçi SharePoint PowerShell kullanma](turn-on-mdo-for-spo-odb-and-teams.md#step-2-recommended-use-sharepoint-online-powershell-to-prevent-users-from-downloading-malicious-files).|
|**Office istemcileri için Kasa Belgeleri açma** <p> _EnableSafeDocs_|Kapalı <p> `$false`|-Inı <p> `$true`|Bu özellik yalnızca Office 365 için Defender (örneğin, Microsoft 365 E5 veya Microsoft 365 E5 Güvenlik) dahil olmayan lisanslarla kullanılabilir ve anlamlıdır. Daha fazla bilgi için bkz. [Microsoft 365 E5 belgeleri Kasa](safe-docs.md).|
|**Kasa Belgeler dosyayı kötü amaçlı olarak tanımlasa bile kişilerin Korumalı Görünüm'e tıklamasına izin ver** <p> _AllowSafeDocsOpen_|Kapalı <p> `$false`|Kapalı <p> `$false`|Bu ayar Kasa Belgeleri ile ilgilidir.|

#### <a name="safe-attachments-policy-settings"></a>Kasa Ekler ilke ayarları

Bu ayarları yapılandırmak için bkz. [Office 365 için Defender Kasa Ekler ilkelerini ayarlama](set-up-safe-attachments-policies.md).

PowerShell'de, bu ayarlar için [New-SafeAttachmentPolicy](/powershell/module/exchange/new-safeattachmentpolicy) ve [Set-SafeAttachmentPolicy](/powershell/module/exchange/set-safelinkspolicy) cmdlet'lerini kullanırsınız.

> [!NOTE]
> Daha önce açıklandığı gibi, Ekleri Kasa varsayılan ilkesi yoktur, ancak Kasa Ekler koruması [**yerleşik koruma** önceden ayarlanmış güvenlik ilkesi](preset-security-policies.md) tarafından tüm alıcılara atanır.
>
> **Özel sütunda Varsayılan**, oluşturduğunuz yeni Kasa Ekler ilkelerindeki varsayılan değerlere başvurur. Kalan sütunlar, karşılık gelen önceden belirlenmiş güvenlik ilkelerinde yapılandırılan değerleri belirtir (aksi belirtilmedikçe).

|Güvenlik özelliği adı|Özelde varsayılan|Yerleşik koruma|Standard|Sıkı|Açıklama ekleme|
|---|:---:|:---:|:---:|:---:|---|
|**Kasa Ekler bilinmeyen kötü amaçlı yazılım yanıtı** <p> _Etkinleştir_ ve _Eylem_|**Kapalı** <p> `-Enable $false` Ve `-Action Block`|**Engelle** <p> `-Enable $true` Ve `-Action Block`|**Engelle** <p> `-Enable $true` Ve `-Action Block`|**Engelle** <p> `-Enable $true` Ve `-Action Block`|_Enable_ parametresi $false olduğunda _, Action_ parametresinin değeri önemli değildir.|
|**Karantina ilkesi** (_QuarantineTag_)|AdminOnlyAccessPolicy|AdminOnlyAccessPolicy|AdminOnlyAccessPolicy|AdminOnlyAccessPolicy| <p> Standart ve Katı önceden ayarlanmış güvenlik ilkeleri [, buradaki](quarantine-policies.md#step-2-assign-a-quarantine-policy-to-supported-features) tabloda açıklandığı gibi varsayılan karantina ilkesini (Karantina bildirimleri olmadan AdminOnlyAccessPolicy) kullanır. <p> Yeni bir Kasa Ekler ilkesi oluşturduğunuzda, boş bir değer varsayılan karantina ilkesinin Kasa Ekleri tarafından karantinaya alınan iletilerin geçmiş özelliklerini tanımlamak için kullanıldığı anlamına gelir (Karantina bildirimleri olmadan AdminOnlyAccessPolicy). <p> Yöneticiler, kullanıcılar için daha fazla özellik tanımlayan özel karantina ilkeleri oluşturabilir ve seçebilir. Daha fazla bilgi için bkz [. Karantina ilkeleri](quarantine-policies.md).|
|**Algılanan eklerle eki yeniden yönlendirme** : **Yeniden yönlendirmeyi etkinleştirme** <p> _Yönlendirme_ <p> _RedirectAddress_|Seçili değil ve e-posta adresi belirtilmedi. <p> `-Redirect $false` <p> _RedirectAddress_ boş (`$null`)|Seçili değil ve e-posta adresi belirtilmedi. <p> `-Redirect $false` <p> _RedirectAddress_ boş (`$null`)|Seçili ve bir e-posta adresi belirtin. <p> `$true` <p> e-posta adresi|Seçili ve bir e-posta adresi belirtin. <p> `$true` <p> e-posta adresi|İletileri gözden geçirilmek üzere bir güvenlik yöneticisine yeniden yönlendirin. <p> **Not**: Bu ayar **Standart**, **Katı** veya Yerleşik koruma önceden ayarlanmış güvenlik **ilkelerinde** yapılandırılmaz. **Standart** ve **Katı** değerleri, oluşturduğunuz yeni Kasa Ekler ilkelerinde **önerilen** değerlerimizi gösterir.|
|**Tarama tamamlanamadıysa Kasa Ekler algılama yanıtını uygulama (zaman aşımı veya hatalar)** <p> _ActionOnError_|Seçili <p> `$true`|Seçili <p> `$true`|Seçili <p> `$true`|Seçili <p> `$true`||

### <a name="safe-links-settings"></a>Kasa Bağlantıları ayarları

Office 365 için Defender Kasa Bağlantıları, etkin Kasa Bağlantıları ilkelerine dahil olan tüm kullanıcılar için geçerli olan genel ayarları ve her Kasa Bağlantılar ilkesine özgü ayarları içerir. Daha fazla bilgi için bkz. [Office 365 için Defender Kasa Bağlantıları](safe-links.md).

Varsayılan Kasa Bağlantıları ilkesi olmasa **da, yerleşik koruma** önceden ayarlanmış güvenlik ilkesi tüm alıcılara Kasa Bağlantılar koruması sağlar (özel Kasa Bağlantıları ilkelerinde tanımlanmayan kullanıcılar). Daha fazla bilgi için bkz. [EOP'de önceden ayarlanmış güvenlik ilkeleri ve Office 365 için Microsoft Defender](preset-security-policies.md).

#### <a name="global-settings-for-safe-links"></a>Kasa Bağlantıları için genel ayarlar

> [!NOTE]
> Kasa Bağlantıları için genel ayarlar **Yerleşik koruma** önceden ayarlanmış güvenlik ilkesi tarafından ayarlanır, ancak **Standart** veya **Katı** önceden belirlenmiş güvenlik ilkeleri tarafından ayarlanmaz. Her iki durumda da yöneticiler bu genel Kasa Bağlantıları ayarlarını istedikleri zaman değiştirebilir.
>
> **Varsayılan** sütun **, Yerleşik koruma** önceden ayarlanmış güvenlik ilkesinin varlığından önceki değerleri gösterir. **Yerleşik koruma** sütunu, yerleşik **koruma** önceden ayarlanmış güvenlik ilkesi tarafından ayarlanan değerleri gösterir ve bunlar da önerilen değerlerimizdir.

Bu ayarları yapılandırmak için bkz[. Office 365 için Defender'da Kasa Bağlantıları için genel ayarları yapılandırma](configure-global-settings-for-safe-links.md).

PowerShell'de, bu ayarlar için [Set-AtpPolicyForO365](/powershell/module/exchange/set-atppolicyforo365) cmdlet'ini kullanırsınız.

|Güvenlik özelliği adı|Varsayılan|Yerleşik koruma|Açıklama ekleme|
|---|:---:|:---:|---|
|**Aşağıdaki URL'leri engelleyin** <p> _ExcludedUrls_|Boş <p> `$null`|Boş <p> `$null`|Bu ayar için belirli bir önerimiz yok. <p> Daha fazla bilgi için Kasa [Bağlantıları için "Aşağıdaki URL'leri engelle" listesine bakın](safe-links.md#block-the-following-urls-list-for-safe-links).
|**Office 365 uygulamalarında Kasa Bağlantılarını kullanma** <p> _EnableSafeLinksForO365Clients_|-Inı <p> `$true`|-Inı <p> `$true`|Desteklenen Office 365 masaüstü ve mobil (iOS ve Android) uygulamalarında Kasa Bağlantılarını kullanın. Daha fazla bilgi için bkz. [Office 365 uygulamalar için bağlantılar ayarları Kasa](safe-links.md#safe-links-settings-for-office-365-apps).|
|**Kullanıcıların Office 365 uygulamalarda korumalı bağlantılara ne zaman tıkladığını izlemeyin** <p> _TrackClicks_|-Inı <p> `$false`|Kapalı <p> `$true`|Bu ayarı kapatmak (_TrackClicks_ ayarı`$true`) desteklenen Office 365 uygulamalarında kullanıcı tıklamalarını izler.|
|**Kullanıcıların Office 365 uygulamalarında özgün URL'ye tıklamasına izin verme** <p> _AllowClickThrough_|-Inı <p> `$false`|-Inı <p> `$false`|Bu ayarın (_AllowClickThrough_ `$false`olarak ayarlı) etkinleştirilmesi, desteklenen Office 365 uygulamalarında özgün URL'ye tıklamayı engeller.|

#### <a name="safe-links-policy-settings"></a>Kasa Bağlantılar ilke ayarları

Bu ayarları yapılandırmak için bkz. [Office 365 için Microsoft Defender Kasa Bağlantıları ilkelerini ayarlama](set-up-safe-links-policies.md).

PowerShell'de, bu ayarlar için [New-SafeLinksPolicy](/powershell/module/exchange/new-safelinkspolicy) ve [Set-SafeLinksPolicy](/powershell/module/exchange/set-safelinkspolicy) cmdlet'lerini kullanırsınız.

> [!NOTE]
> Daha önce açıklandığı gibi, varsayılan Kasa Bağlantıları ilkesi yoktur, ancak Kasa Bağlantılar koruması [**yerleşik koruma** önceden ayarlanmış güvenlik ilkesi](preset-security-policies.md) tarafından tüm alıcılara atanır.
>
> **Özel sütunda Varsayılan**, oluşturduğunuz yeni Kasa Bağlantıları ilkelerindeki varsayılan değerlere başvurur. Kalan sütunlar, karşılık gelen önceden belirlenmiş güvenlik ilkelerinde yapılandırılan değerleri belirtir (aksi belirtilmedikçe).

|Güvenlik özelliği adı|Özelde varsayılan|Yerleşik koruma|Standard|Sıkı|Açıklama ekleme|
|---|:---:|:---:|:---:|:---:|---|
|**URL & koruma ayarlarına tıklayın**||||||
|**E-postalar içindeki kötü amaçlı olabilecek URL'ler üzerinde eylem**||||||
|**Açık: Kasa Bağlantılar, kullanıcılar e-postadaki bağlantılara tıkladığında bilinen, kötü amaçlı bağlantıların listesini denetler** <p> _EnableSafeLinksForEmail_|Seçili değil <p> `$false`|Seçili <p> `$true`|Seçili <p> `$true`|Seçili <p> `$true`||
|**Kuruluş içinde gönderilen e-posta iletilerine Kasa Bağlantıları uygulama** <p> _EnableForInternalSenders_|Seçili değil <p> `$false`|Seçili <p> `$true`|Seçili <p> `$true`|Seçili <p> `$true`||
|**Şüpheli bağlantılar ve dosyalara işaret eden bağlantılar için gerçek zamanlı URL taraması uygulama** <p> _ScanUrls_|Seçili değil <p> `$false`|Seçili <p> `$true`|Seçili <p> `$true`|Seçili <p> `$true`||
|**İletiyi teslim etmeden önce URL taramasının tamamlanmasını bekleyin** <p> _DeliverMessageAfterScan_|Seçili değil <p> `$false`|Seçili <p> `$true`|Seçili <p> `$true`|Seçili <p> `$true`||
|**URL'leri yeniden yazmayın, denetimleri yalnızca Kasa Bağlantılar API'si aracılığıyla yapın** <p> _DisableURLRewrite_|Seçili değil <p> `$false`|Seçili <p> `$true`|Seçili değil <p> `$false`|Seçili değil <p> `$false`||
|**E-postada aşağıdaki URL'leri yeniden yazmayın** <p> _DoNotRewriteUrls_|Seçili değil <p> Boş|Seçili değil <p> Boş|Seçili değil <p> Boş|Seçili değil <p> Boş|Bu ayar için belirli bir önerimiz yok. Daha fazla bilgi için Kasa [Bağlantıları ilkelerindeki "Aşağıdaki URL'leri yeniden yazmayın" listelerine](safe-links.md#do-not-rewrite-the-following-urls-lists-in-safe-links-policies) bakın.|
|**Microsoft Teams'de kötü amaçlı olabilecek URL'ler için eylem**||||||
|**Açık: Kasa Bağlantılar, kullanıcılar Microsoft Teams'deki bağlantılara tıkladığında bilinen, kötü amaçlı bağlantıların listesini denetler** <p> _EnableSafeLinksForTeams_|Seçili değil <p> `$false`|Seçili <p> `$true`|Seçili <p> `$true`|Seçili <p> `$true`||
|**Koruma ayarları'nı tıklatın**||||||
|**Kullanıcı tıklamalarını izleme** <p> _TrackUserClicks_|Seçili <p> `$true`|Seçili <p> `$true`|Seçili <p> `$true`|Seçili <p> `$true`||
|**Kullanıcıların özgün URL'ye tıklamasına izin ver** <p> _AllowClickThrough_|Seçili <p> `$true`|Seçili <p> `$true`|Seçili değil <p> `$false`|Seçili değil <p> `$false`|Bu ayarı kapatmak ( _AllowClickThrough_ `$false`ayarı) özgün URL'ye tıklamayı engeller.|
|**Bildirim ve uyarı sayfalarında kuruluş markasını görüntüleme** <p> _EnableOrganizationBranding_|Seçili değil <p> `$false`|Seçili değil <p> `$false`|Seçili değil <p> `$false`|Seçili değil <p> `$false`|Bu ayar için belirli bir önerimiz yok. <p> Bu ayarı açmadan önce, kuruluşunuzun şirket logonuzu karşıya yüklemek [için Microsoft 365 temasını özelleştirme başlığı altında yer alan](../../admin/setup/customize-your-organization-theme.md) yönergeleri izlemeniz gerekir.|
|**Bildirim**||||||
|**Kullanıcılarınıza nasıl bildirimde bulunacaksınız?**|**Varsayılan bildirim metnini kullanma**|**Varsayılan bildirim metnini kullanma**|**Varsayılan bildirim metnini kullanma**|**Varsayılan bildirim metnini kullanma**|Bu ayar için belirli bir önerimiz yok. <p> **Kullanılacak özelleştirilmiş bildirim metnini girmek için Özel bildirim metnini kullan** (_CustomNotificationText_) seçeneğini belirleyebilirsiniz. Özel bildirim metnini kullanıcının diline çevirmek **için Otomatik yerelleştirme için Microsoft Çeviri kullan** (_UseTranslatedNotificationText_) seçeneğini de belirleyebilirsiniz.

## <a name="related-articles"></a>İlgili makaleler

- **posta akışı kuralları (taşıma kuralları olarak da bilinir) Exchange** için en iyi yöntemleri mi arıyorsunuz? Bkz. [Exchange Online'da posta akışı kurallarını yapılandırmak için en iyi yöntemler](/exchange/security-and-compliance/mail-flow-rules/configuration-best-practices).

- Yöneticiler ve kullanıcılar yanlış pozitifler (kötü olarak işaretlenmiş iyi e-postalar) ve hatalı negatifler (hatalı e-postaya izin verilir) analiz için Microsoft'a gönderebilir. Daha fazla bilgi için bkz. [İletileri ve dosyaları Microsoft'a bildirme](report-junk-email-messages-to-microsoft.md).

- [EOP hizmetinizi](/exchange/standalone-eop/set-up-your-eop-service) **ayarlama** ve [Office 365 için Microsoft Defender](defender-for-office-365.md) **yapılandırma** hakkında bilgi için bu bağlantıları kullanın. 'Office 365 [Tehditlere Karşı Koruma](protect-against-threats.md)' bölümünde yer alan yararlı yönergeleri unutmayın.

- **Windows güvenlik temelleri** burada bulunabilir: GPO/şirket içi seçenekleri için [güvenlik temellerini nereden alabilirim?](/windows/security/threat-protection/windows-security-baselines#where-can-i-get-the-security-baselines) ve Intune tabanlı güvenlik için [Intune Windows cihazları yapılandırmak için güvenlik temellerini kullanma](/intune/protect/security-baselines). Son olarak, Uç Nokta için Microsoft Defender ile Microsoft Intune güvenlik temelleri arasındaki karşılaştırma[, Uç Nokta için Microsoft Defender ve Windows Intune güvenliğini karşılaştırma bölümünde sağlanır temellerini seçin](/windows/security/threat-protection/microsoft-defender-atp/configure-machines-security-baseline#compare-the-microsoft-defender-atp-and-the-windows-intune-security-baselines).
