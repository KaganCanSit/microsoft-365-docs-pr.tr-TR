---
title: Güvenlik ayarlarını değiştirmek için EOP ve Defender Office 365 Microsoft önerileri
keywords: Office 365 güvenlik önerileri, Sender Policy Framework, Etki Alanı Tabanlı İleti Raporlama ve Uyumluluk, DomainKeys Tanımlanan Posta, adımlar, nasıl çalışır, güvenlik taban çizgisi, EOP için taban çizgisi, Office 365 için Defender taban çizgisi, Office 365 için Defender'ı ayarlama, EOP'yi ayarlama, Office 365 için Defender'ı yapılandırma , EOP'yi, güvenlik yapılandırmasını yapılandırma
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
description: Güvenlik ayarları için EOP (EOP) Exchange Online Protection Defender ile ilgili en Office 365 yöntemlerdir? Standart koruma için geçerli öneriler neler? Daha katı olmak için ne kullanılmaları gerekir? Ayrıca Defender'ı bu iş için kullanıyorsanız hangi ek Office 365?
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 66d221b422236c6818ebb146babc0cc90eab1206
ms.sourcegitcommit: f563b4229760fa099703296d1ad2c1f0264f1647
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/14/2022
ms.locfileid: "63016267"
---
# <a name="recommended-settings-for-eop-and-microsoft-defender-for-office-365-security"></a>EOP ve Microsoft Defender için önerilen güvenlik Office 365 ayarları

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Geçerli olduğu yer:**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [1. plan Office 365 plan 2 için Microsoft Defender](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

**Exchange Online Protection (EOP),** Microsoft 365 abonelikleri için güvenliğin temel güvenliğidir ve kötü amaçlı e-postaların çalışanın gelen kutularına ulaşmasını korumanıza yardımcı olur. Ancak her gün ortaya çıkan yeni ve daha gelişmiş saldırılarla, çoğunlukla gelişmiş korumalar gereklidir. Uygulama **için Microsoft Defender Office 365** Plan 1 veya Plan 2, yöneticilere daha fazla güvenlik, denetim ve soruşturma katmanıen ek özellikler içerir.

Güvenlik yöneticilerine güvenlik ayarlarını özelleştirme konusunda güç sağlar olsak da, önerebileceğiniz iki güvenlik düzeyi EOP ve Office 365 Microsoft Defender vardır: **Standart** ve **Katı**. Müşteri ortamları ve ihtiyaçları farklı olsa da, bu filtreleme düzeyleri çoğu durumda istenmeyen postaların çalışanlarının Gelen Kutusu'na ulaşmasını önlemeye yardımcı olur.

Kullanıcılara otomatik olarak Standart veya Katı ayarları uygulamak için bkz. [EOP'de](preset-security-policies.md) önceden belirlenmiş güvenlik ilkeleri ve Office 365.

Bu makalede, varsayılan ayarların yanı sıra kullanıcılarınızı korumaya yardımcı olmak için önerilen Standart ve Katı ayarlar da açıklanmıştır. Tablolar, Microsoft 365 Defender posta kutuları olmayan kuruluşlar için Microsoft 365 Defender PowerShell (Exchange Online PowerShell veya tek başına Exchange Online Protection PowerShell Exchange Online içerir.

> [!TIP]
> Önerilen Standart ve Katı ayarlarını portalda değiştiremezsiniz Microsoft 365 Defender. Kullanıcıların korumayı etkinleştirmesi gibi **önerilen değerleri değiştirmek** için, [PowerShell'de Exchange Online gerekir](/powershell/exchange/connect-to-exchange-online-powershell).
>
> PowerShell Office 365 Gelişmiş Tehdit Koruması Önerilen Yapılandırma Çözümleyicisi (ORCA) modülü, (yöneticiler) bu ayarların geçerli değerlerini bu konuda size yardımcı olabilir. Özel olarak, **Get-ORCAReport** cmdlet'i istenmeyen posta önleme, kimlik avı önleme ve diğer ileti ayarlarıyla ilgili bir değerlendirme oluştur. ORCA modülünü şu bağlantıdan indirebilirsiniz <https://www.powershellgallery.com/packages/ORCA/>: .

## <a name="anti-spam-anti-malware-and-anti-phishing-protection-in-eop"></a>EOP'de istenmeyen posta önleme, kötü amaçlı yazılımdan koruma ve kimlik avı koruması

İstenmeyen postadan koruma, kötü amaçlı yazılımdan koruma ve kimlik avı önleme, yöneticiler tarafından yapılandırılan EOP özellikleridir. Aşağıdaki Standart veya Katı yapılandırmalarını öneririz.

### <a name="eop-anti-spam-policy-settings"></a>EOP istenmeyen posta önleme ilkesi ayarları

İstenmeyen posta önleme ilkeleri oluşturmak ve yapılandırmak için bkz. [EOP'de istenmeyen posta önleme ilkelerini yapılandırma](configure-your-spam-filter-policies.md).

<br>

****

|Güvenlik özelliği adı|Default|Standard|Katı|Açıklama ekleme|
|---|:---:|:---:|:---:|---|
|**İstenmeyen posta & toplu e-posta eşiği**|||||
|**Toplu e-posta eşiği** <p> _BulkThreshold_|7|6|4|Ayrıntılar için bkz. [EOP'de toplu şikayet düzeyi (BCL](bulk-complaint-level-values.md)).|
|_MarkAsSpamBulkMail_|`On`|`On`|`On`|Bu ayar yalnızca PowerShell'de kullanılabilir.|
|**İstenmeyen posta puanı ayarlarını** artırma|Kapalı|Kapalı|Kapalı|Bu ayarların hepsi Gelişmiş İstenmeyen Posta Filtresi'nin (ASF) bir parçası. Daha fazla bilgi için, bu [makalenin İstenmeyen posta önleme ilkeleri'nin ASF](#asf-settings-in-anti-spam-policies) ayarları bölümüne bakın.|
|**İstenmeyen posta ayarları olarak** işaretleme|Kapalı|Kapalı|Kapalı|Bu ayarların çoğu ASF'nin bir bölümüdir. Daha fazla bilgi için, bu [makalenin İstenmeyen posta önleme ilkeleri'nin ASF](#asf-settings-in-anti-spam-policies) ayarları bölümüne bakın.|
|**Belirli diller içerir** <p> _EnableLanguageBlockList_ <p> _LanguageBlockList_|**Kapalı** <p> `$false` <p> Boş|**Kapalı** <p> `$false` <p> Boş|**Kapalı** <p> `$false` <p> Boş|Bu ayar için özel bir önerimiz yok. İş ihtiyaçlarına bağlı olarak belirli dillerdeki iletileri engelleyebilirsiniz.|
|**Bu ülkelerden** <p> _EnableRegionBlockList_ <p> _RegionBlockList_|**Kapalı** <p> `$false` <p> Boş|**Kapalı** <p> `$false` <p> Boş|**Kapalı** <p> `$false` <p> Boş|Bu ayar için özel bir önerimiz yok. İş ihtiyaçlarına göre belirli ülkelerden gelen iletileri engelleyebilirsiniz.|
|**Test modu** (_TestModeAction_)|**Yok**|**Yok**|**Yok**|Bu ayar ASF'nin bir kısmıdır. Daha fazla bilgi için, bu [makalenin İstenmeyen posta önleme ilkeleri'nin ASF](#asf-settings-in-anti-spam-policies) ayarları bölümüne bakın.|
|**Eylemler**||||İletiyi **karantinaya gönder'i** her **seçseniz, Karantina ilkesi** seç kutusu da kullanılabilir. Karantina ilkeleri, kullanıcıların karantinaya alınmış iletilerde neler yapmalarına izin verilmiyor? <p> Yeni bir istenmeyen posta önleme ilkesi musunuz? Boş değer, belirli bir kararla karantinaya alınan iletiler için geçmiş özelliklerini tanımlamak üzere varsayılan karantina ilkesi anlamına gelir (Yüksek güven kimlik avı için AdminOnlyAccessPolicy **;** Diğer her şey için DefaultFullAccessPolicy). <p> Yöneticiler, kullanıcılar için daha kısıtlayıcı veya daha az kısıtlayıcı özellikler tanımlayan özel karantina ilkeleri oluşturabilir ve bu ilkeleri kullanabilir. Daha fazla bilgi için bkz. [Karantina ilkeleri](quarantine-policies.md).|
|**İstenmeyen** posta algılama eylemi <p> _SpamAction_|**İletiyi Gereksiz E-posta klasörüne taşıma** <p> `MoveToJmf`|**İletiyi Gereksiz E-posta klasörüne taşıma** <p> `MoveToJmf`|**İletiyi karantinaya alın** <p> `Quarantine`||
|**Yüksek güven istenmeyen posta** algılama eylemi <p> _HighConfidenceSpamAction_|**İletiyi karantinaya alın** <p> `MoveToJmf`|**İletiyi karantinaya alın** <p> `Quarantine`|**İletiyi karantinaya alın** <p> `Quarantine`||
|**Kimlik avı algılama** eylemi <p> _PhishSpamAction_|**İletiyi karantinaya alın** <p> `MoveToJmf`|**İletiyi karantinaya alın** <p> `Quarantine`|**İletiyi karantinaya alın** <p> `Quarantine`||
|**Yüksek güven kimlik avı algılama** eylemi <p> _HighConfidencePhishAction_|**İletiyi karantinaya alın** <p> `Quarantine`|**İletiyi karantinaya alın** <p> `Quarantine`|**İletiyi karantinaya alın** <p> `Quarantine`||
|**Toplu** algılama eylemi <p> _BulkSpamAction_|**İletiyi Gereksiz E-posta klasörüne taşıma** <p> `MoveToJmf`|**İletiyi Gereksiz E-posta klasörüne taşıma** <p> `MoveToJmf`|**İletiyi karantinaya alın** <p> `Quarantine`||
|**İstenmeyen postayı şu kadar gün karantinada tutma** <p> _KarantinaRetentionPeriod_|15 gün<sup>\*</sup>|30 gün|30 gün|<sup>\*</sup> Varsayılan değer, varsayılan istenmeyen posta önleme ilkesinde ve PowerShell'de oluştur ilkelerin yeni istenmeyen posta önleme ilkelerde 15 gündür. Varsayılan değer, yeni istenmeyen posta önleme ilkelerde varsayılan değer olarak 30 gündür ve Microsoft 365 Defender vardır. <p> Bu değer, kimlik avı önleme ilkeleri tarafından karantinaya alınan iletileri de etkiler. Daha fazla bilgi için bkz. [EOP'de e-posta iletileri karantinaya alınmış](quarantine-email-messages.md).|
|**İstenmeyen posta güvenliği ipuçlarını etkinleştirme** <p> _InlineSafetyTipsEnabled_|Seçildi <p> `$true`|Seçildi <p> `$true`|Seçildi <p> `$true`||
|Kimlik avı iletileri için sıfır saatlik otomatik temizlemeyi (ZAP) etkinleştirme <p> _PhishZapEnabled_|Seçildi <p> `$true`|Seçildi <p> `$true`|Seçildi <p> `$true`||
|İstenmeyen posta iletileri için ZAP'yi etkinleştirme <p> _SpamZapEnabled_|Seçildi <p> `$true`|Seçildi <p> `$true`|Seçildi <p> `$true`||
|**Engellenenler & izin ver**|||||
|İzin verilen gönderenler <p> _AllowedSenders_|Yok|Yok|Yok||
|İzin verilen gönderen etki alanları <p> _AllowedSenderDomains_|Yok|Yok|Yok|İzin verilen gönderenler listesine etki alanları eklemek çok iyi bir fikir değildir. Saldırganlar size aksi halde filtrelenmiş e-posta gönderebilirler. <p> Kuruluş [e-posta](learn-about-spoof-intelligence.md) etki alanlarındaki gönderen e-posta adreslerini kullanarak ya da dış etki alanlarındaki gönderen e-posta adreslerini kullanarak gönderenin e-posta adreslerini kullanarak e-posta gönderenin e-postalarını kullanarak e-posta gönderenin e-postalarını e-posta olarak gönderenlerin e-postalarını e-posta ile birlikte kullanarak e-postaların e-postalarını kullanarak ya da e-postaların e-postalarını kullanarak ya da e-posta e-postalarını kullanarak ya da e-posta e-postalarını kullanarak bilgi e-postalarını kullanarak ya da e-posta e-postalarını kullanarak ya da e-posta e-postalarını kullanarak e-posta gönderene ya da e-posta [](tenant-allow-block-list.md)|
|Engellenen gönderenler <p> _BlockedSenders_|Yok|Yok|Yok||
|Engellenen gönderen etki alanları <p> _BlockedSenderDomains_|Yok|Yok|Yok||
|

#### <a name="asf-settings-in-anti-spam-policies"></a>İstenmeyen posta önleme ilkelerde ASF ayarları

Bu bölümdeki tabloda, istenmeyen posta önleme ilkelerde kullanılabilen Gelişmiş İstenmeyen Posta Filtresi (ASF) ayarları açık bulunmaktadır. Hem Standart hem de Katı **düzeyler** için **bu ayarların** **hepsi Kapalıdır** . ASF ayarları hakkında daha fazla bilgi için bkz. [EOP'de Gelişmiş İstenmeyen Posta Filtresi (ASF) ayarları](advanced-spam-filtering-asf-options.md).

<br>

****

|Güvenlik özelliği adı|Açıklama ekleme|
|---|---|
|**Uzak sitelere resim bağlantıları** (_IncreaseScoreWithImageLinks_)||
|**URL'de Sayısal IP** adresi (_IncreaseScoreWithNumericIps_)||
|**URL diğer bağlantı noktasına yönlendirme** (_IncreaseScoreWithRedirectToOtherPort_)||
|**.biz veya .info web sitelerinin** bağlantıları (_IncreaseScoreWithBizOrInfoUrls_)||
|**Boş iletiler** (_MarkAsSpamEmptyMessages_)||
|**HTML'ye etiket ekleme** (_MarkAsSpamEmbedTagsInHtml_)||
|**HTML'de JavaScript veya VBScript** (_MarkAsSpamJavaScriptInHtml_)||
|**HTML'de form** _etiketleri (MarkAsSpamFormTagsInHtml_)||
|**HTML'de çerçeve veya iframe** etiketleri (_MarkAsSpamFramesInHtml_)||
|**HTML'de web hataları** (_MarkAsSpamWebBugsInHtml_)||
|**HTML'de nesne etiketleri** (_MarkAsSpamObjectTagsInHtml_)||
|**Hassas sözcükler** (_MarkAsSpamSensitiveWordList_)||
|**SPF kaydı: sabit başarısız** (_MarkAsSpamSpfRecordFail_)||
|**Gönderen Kimliği filtrelemesi zor başarısız oldu** (_MarkAsSpamFromAddressAuthFail_)||
|**Geri Çıktı** (_MarkAsSpamNdrBackscatter_)||
|**Test modu** (_TestModeAction_)|Test eylemini destekleyen ASF  ayarları için, sınama modu eylemini Yok olarak yapılandırabilirsiniz **, varsayılan** **X Üstbilgi** metni ekleyebilir veya Gizli **iletisi (**`None`, `AddXHeader``BccMessage`veya ) gönderebilirsiniz. Daha fazla bilgi için bkz. [ASF ayarlarını etkinleştirme, devre dışı bırakma veya test edin](advanced-spam-filtering-asf-options.md#enable-disable-or-test-asf-settings).|
|

#### <a name="eop-outbound-spam-policy-settings"></a>EOP giden istenmeyen posta ilkesi ayarları

Giden istenmeyen posta ilkeleri oluşturmak ve yapılandırmak için bkz. [EOP'de giden istenmeyen posta filtrelemeyi yapılandırma](configure-the-outbound-spam-policy.md).

Hizmette varsayılan gönderme sınırları hakkında daha fazla bilgi için bkz. [Gönderme sınırları](/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits#sending-limits-1).

> [!NOTE]
> Giden istenmeyen posta ilkeleri Standart veya Katı önceden tanımlı güvenlik ilkelerinin bir parçası değildir. **Standart ve** **Katı değerleri**, varsayılan **giden istenmeyen** posta ilkesinde veya sizin oluşturmanız için özel ilkelerde önerilen değerlerimizi gösterir.

<br>

****

|Güvenlik özelliği adı|Default|Standard|Katı|Açıklama ekleme|
|---|:---:|:---:|:---:|---|
|**Dış ileti sınırı ayarlama** <p> _RecipientLimitExternalPerHour_|0|500|400|Varsayılan değer 0, hizmet varsayılanlarını kullanmak anlamına gelir.|
|**İç ileti sınırı ayarlama** <p> _RecipientLimitInternalPerHour_|0|1000|800|Varsayılan değer 0, hizmet varsayılanlarını kullanmak anlamına gelir.|
|**Günlük ileti sınırı ayarlama** <p> _RecipientLimitPerDay_|0|1000|800|Varsayılan değer 0, hizmet varsayılanlarını kullanmak anlamına gelir.|
|**İleti sınırına ulaşan kullanıcılara kısıtlama** <p> _ActionWhenThresholdReached_|**Kullanıcının posta göndermesi için sonraki güne kadar kısıtlama** <p> `BlockUserForToday`|**Kullanıcının posta göndermesi kısıtlama** <p> `BlockUser`|**Kullanıcının posta göndermesi kısıtlama** <p> `BlockUser`||
|**Otomatik iletme kuralları** <p> _AutoForwardingMode_|**Otomatik - Sistem denetimli** <p> `Automatic`|**Otomatik - Sistem denetimli** <p> `Automatic`|**Otomatik - Sistem denetimli** <p> `Automatic`|
|**Bu sınırları aşan giden iletilerin bir kopyasını bu kullanıcılara ve gruplara gönderin** <p> _BccSuspiciousOutboundMail_ <p> _BccSuspiciousOutboundAdditionalRecipients_|Seçili değil <p> `$false` <p> Boş|Seçili değil <p> `$false` <p> Boş|Seçili değil <p> `$false` <p> Boş|Bu ayar için özel bir önerimiz yok. <p> Bu ayar yalnızca varsayılan giden istenmeyen posta ilkesinde çalışır. Sizin oluşturan özel giden istenmeyen posta ilkelerde işe yaramadı.|
|**Gönderenin giden istenmeyen posta göndermesi nedeniyle engellenmişse, bu kullanıcıları ve grupları bilgilendirin** <p> _NotifyOutboundSpam_ <p> _NotifyOutboundSpamRecipients_|Seçili değil <p> `$false` <p> Boş|Seçili değil <p> `$false` <p> Boş|Seçili değil <p> `$false` <p> Boş|Kullanıcı e-posta göndermeyle kısıtlandı adlı varsayılan uyarı ilkesi, ilke sınırları aşılmış olması nedeniyle kullanıcılar engellenmiş durumdayken **TenantAdmins** (**Genel** yöneticiler) grubunun üyelerine zaten e-posta bildirimleri gönderir.[](../../compliance/alert-policies.md)  **Yöneticileri ve diğer kullanıcıları bilgilendirmek için giden** istenmeyen posta ilkesinde bu ayar yerine uyarı ilkesi kullanmalarını kesinlikle öneririz. Yönergeler için bkz [. Kısıtlanmış kullanıcılar için uyarı ayarlarını doğrulama](removing-user-from-restricted-users-portal-after-spam.md#verify-the-alert-settings-for-restricted-users).|
|

### <a name="eop-anti-malware-policy-settings"></a>EOP kötü amaçlı yazılımdan koruma ilkesi ayarları

Kötü amaçlı yazılımdan koruma ilkeleri oluşturmak ve yapılandırmak için bkz. [EOP'de kötü amaçlı yazılımdan koruma ilkelerini yapılandırma](configure-anti-malware-policies.md).

<br>

****

|Güvenlik özelliği adı|Default|Standard|Katı|Açıklama ekleme|
|---|:---:|:---:|:---:|---|
|**Koruma ayarları**|||||
|**Yaygın ekler filtresini etkinleştirme** <p> _EnableFileFilter_|Seçili değil <p> `$false`|Seçildi <p> `$true`|Seçildi <p> `$true`|Bu ayar, yürütülebilir ek içeren iletileri ek içeriği ne olursa olsun, dosya türüne göre karantinaya ayarlar.|
|**Kötü amaçlı yazılım için sıfır saatlik otomatik temizlemeyi etkinleştirme** <p> _ZapEnabled_|Seçildi <p> `$true`|Seçildi <p> `$true`|Seçildi <p> `$true`||
|**Karantina ilkesi**|AdminOnlyAccessPolicy|AdminOnlyAccessPolicy|AdminOnlyAccessPolicy|Yeni bir kötü amaçlı yazılımdan koruma ilkesi  oluşturursanız, boş bir değer, kötü amaçlı yazılım olarak karantinaya alınmış iletiler için geçmiş özelliklerini tanımlamak için varsayılan karantina ilkesi kullanılır (AdminOnlyAccessPolicy). <p> Yöneticiler kullanıcılar için daha fazla özellik tanımlayan özel karantina ilkeleri oluşturabilir ve bu ilkeleri kullanabilir. Daha fazla bilgi için bkz. [Karantina ilkeleri](quarantine-policies.md).|
|**Alıcı bildirimleri**|||||
|**İletiler kötü amaçlı yazılım olarak karantinaya alınırken alıcıları bilgilendirme** <p> _Eylem_|Seçili değil <p> _DeleteMessage_|Seçili değil <p> _DeleteMessage_|Seçili değil <p> _DeleteMessage_|Bir e-posta eksinde kötü amaçlı yazılım algılanırsa, ileti karantinaya alınır ve yalnızca yönetici tarafından yayımlanır.|
|**Gönderen bildirimleri**|||||
|**İletiler kötü amaçlı yazılım olarak karantinaya alınırken iç gönderenlere bildirim gönderme** <p> _EnableInternalSenderNotifications_|Seçili değil <p> `$false`|Seçili değil <p> `$false`|Seçili değil <p> `$false`||
|**İletiler kötü amaçlı yazılım olarak karantinaya alınırken dış gönderenlere bildirim gönderme** <p> _EnableExternalSenderNotifications_|Seçili değil <p> `$false`|Seçili değil <p> `$false`|Seçili değil <p> `$false`||
|**Yönetici bildirimleri**|||||
|**Yöneticiye, iç gönderenlerden gelen teslim edilmeyen iletileri bildirme** <p> _EnableInternalSenderAdminNotifications_ <p> _InternalSenderAdminAddress_|Seçili değil <p> `$false`|Seçili değil <p> `$false`|Seçili değil <p> `$false`|Bu ayar için özel bir önerimiz yok.|
|**Yöneticiye dış gönderenlerden gelen teslim edilmeyen iletileri bildirme** <p> _EnableExternalSenderAdminNotifications_ <p> _ExternalSenderAdminAddress_|Seçili değil <p> `$false`|Seçili değil <p> `$false`|Seçili değil <p> `$false`|Bu ayar için özel bir önerimiz yok.|
|**Bildirimleri özelleştirme**||||Bu ayarlar için özel önerilerimiz yok.|
|**Özelleştirilmiş bildirim metnini kullanma** <p> _CustomNotifications_|Seçili değil <p> `$false`|Seçili değil <p> `$false`|Seçili değil <p> `$false`||
|**From name** <p> _CustomFromName_|Boş <p> `$null`|Boş <p> `$null`|Boş <p> `$null`||
|**Adresten** <p> _CustomFromAddress_|Boş <p> `$null`|Boş <p> `$null`|Boş <p> `$null`||
|**İç gönderenlerden gelen iletiler için bildirimleri özelleştirme**||||Bu ayarlar yalnızca, **İletiler kötü** amaçlı yazılım olarak karantinaya alınırken iç gönderenlere bildir veya Yöneticiye iç gönderenlerden teslim edilmeyen iletileri bildir **seçili olduğunda kullanılır** .|
|**Konu** <p> _CustomInternalSubject_|Boş <p> `$null`|Boş <p> `$null`|Boş <p> `$null`||
|**İleti** <p> _CustomInternal YerKarakdi_|Boş <p> `$null`|Boş <p> `$null`|Boş <p> `$null`||
|**Dış gönderenlerden gelen iletiler için bildirimleri özelleştirme**||||Bu ayarlar yalnızca, **İletiler kötü** amaçlı yazılım olarak karantinaya alınırken dış gönderenlere bildir veya Yöneticiye dış gönderenlerden teslim edilmeyen iletileri bildir **seçili olduğunda kullanılır** .|
|**Konu** <p> _CustomExternalSubject_|Boş <p> `$null`|Boş <p> `$null`|Boş <p> `$null`||
|**İleti** <p> _CustomExternal YerKarakdi_|Boş <p> `$null`|Boş <p> `$null`|Boş <p> `$null`||
|

### <a name="eop-anti-phishing-policy-settings"></a>EOP kimlik avı önleme ilkesi ayarları

Bu ayarlar hakkında daha fazla bilgi için bkz [. Spoof ayarları](set-up-anti-phishing-policies.md#spoof-settings). Bu ayarları yapılandırmak için bkz. [EOP'de kimlik avı koruma ilkelerini yapılandırma](configure-anti-phishing-policies-eop.md).

<br>

****

|Güvenlik özelliği adı|Default|Standard|Katı|Açıklama ekleme|
|---|:---:|:---:|:---:|---|
|**Kimlik avı eşiği & koruması**|||||
|**Akıllı ifadeyi etkinleştirme** <p> _EnableSpoofIntelligence_|Seçildi <p> `$true`|Seçildi <p> `$true`|Seçildi <p> `$true`||
|**Eylemler**|||||
|**İleti, bir ifadeyle algılanırsa** <p> _AuthenticationFailAction_|**İletiyi alıcıların Gereksiz E-posta klasörlerine taşıma** <p> `MoveToJmf`|**İletiyi alıcıların Gereksiz E-posta klasörlerine taşıma** <p> `MoveToJmf`|**İletiyi karantinaya alın** <p> `Quarantine`|Bu ayar, bilgi e-posta bilgisinde gösterildiği gibi otomatik olarak engellenen veya Kiracı İzin Ver/[](learn-about-spoof-intelligence.md)Engelleme Listesi'ne el ile engellenen kimliği doğrulandı [gönderenler için geçerlidir](tenant-allow-block-list.md). <p> İletiyi **karantinaya alın'ı** seçerseniz, kullanıcıların oturum açma olarak karantinaya alınmış iletilerde ne yapmalarına izin verilmiyor öğesini tanımlayan karantina ilkesi kutusunu seçmek için bir Karantina ilkesi uygula kutusu kullanılabilir. Yeni kimlik avı önleme ilkesi musunuz? Boş değer, kimlik avı dolandırıcılığı olarak karantinaya alınmış iletiler için geçmiş özelliklerini tanımlamak için varsayılan karantina ilkesi anlamına gelir (DefaultFullAccessPolicy). <p> Yöneticiler, kullanıcılar için daha kısıtlayıcı veya daha az kısıtlayıcı özellikler tanımlayan özel karantina ilkeleri oluşturabilir ve bu ilkeleri kullanabilir. Daha fazla bilgi için bkz. [Karantina ilkeleri](quarantine-policies.md).|
|**İlk kişi bilgilerini güvenlik ipucu** <p> _EnableFirstContactSafetyTips_|Seçili değil <p> `$false`|Seçili değil <p> `$false`|Seçili değil <p> `$false`|Daha fazla bilgi için bkz[. İlk kişi güvenlik ipucu](set-up-anti-phishing-policies.md#first-contact-safety-tip).|
|**Kimlik doğrulaması için kimliği doğrulanmamış gönderenler için göster (?)** <p> _EnableUnauthenticatedSender_|Seçildi <p> `$true`|Seçildi <p> `$true`|Seçildi <p> `$true`|Tanımlanamayan kimliksiz gönderenler için Outlook'da gönderenin fotoğrafına bir soru işareti (?) ekler. Daha fazla bilgi için bkz [. Kimliği doğrulanmamış gönderen](set-up-anti-phishing-policies.md#unauthenticated-sender).|
|**"Aracılığıyla" etiketini göster** <p> _EnableViaTag_|Seçildi <p> `$true`|Seçildi <p> `$true`|Seçildi <p> `$true`|DKIM imzası veya MAIL **FROM** chris@contoso.com farklı ise, Gönderen adresine aracılığıyla etiketi (chris@contoso.com fabrikam.com aracılığıyla gönder) ekler. <p> Daha fazla bilgi için bkz [. Kimliği doğrulanmamış gönderen](set-up-anti-phishing-policies.md#unauthenticated-sender).|
|

## <a name="microsoft-defender-for-office-365-security"></a>Office 365 güvenliği için Microsoft Defender

Çevrimiçi abonelik için Microsoft Defender ile birlikte ek Office 365 gelir. En son haberler ve bilgiler için bkz. Yeni sürümler için [Defender'daki Office 365](whats-new-in-defender-for-office-365.md).

> [!IMPORTANT]
>
> - Office 365 için Microsoft Defender'daki varsayılan kimlik avı koruma ilkesi, tüm alıcılar için kimlik [](set-up-anti-phishing-policies.md#spoof-settings) avı koruması ve posta kutusu zekası sağlar. Bununla birlikte, diğer kullanılabilir [kimliğe bürünme](#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365) koruma [özellikleri ve gelişmiş](#advanced-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365) ayarlar varsayılan ilkede yapılandırılmaz veya etkinleştirilmez. Tüm koruma özelliklerini etkinleştirmek için, varsayılan kimlik avı önleme ilkesine değişiklik veya ek kimlik avı koruma ilkeleri oluşturun.
>
> - Varsayılan Kasa Ekler ilkesi veya Kasa Bağlantılar ilkesi her ne kadar da olsa, yerleşik koruma önceden ayarlanmış güvenlik ilkesi Kasa Ekler  koruması ve tüm alıcılara Kasa Bağlantıları koruması sağlar (özel Kasa Ek ilkeleri veya Kasa Bağlantıları ilkeleri içinde tanımlanmamış kullanıcılar). Daha fazla bilgi için bkz[. İlke için EOP'de ve Microsoft Defender'da önceden Office 365](preset-security-policies.md).
>
> - [Kasa Bağlantı ilkelerine SharePoint, OneDrive ve Microsoft Teams](mdo-for-spo-odb-and-teams.md) koruması [Kasa](safe-docs.md) için eklerin Kasa yoktur.

Aboneliğiniz Office 365 için Microsoft Defender'ı dahil ediyorsa veya Office 365 için Defender'ı eklenti olarak satın verdiysanız, aşağıdaki Standart veya Katı yapılandırmalarını ayarlayın.

### <a name="anti-phishing-policy-settings-in-microsoft-defender-for-office-365"></a>Kimlik avı için Microsoft Defender'da kimlik avıyla mücadele ilkesi Office 365

EOP müşterileri daha önce açıklandığı gibi temel kimlik avı önleme özelliklerine sahip olur ancak Office 365 Defender saldırılara karşı önlemeye, algılamaya ve düzeltmeye yardımcı olmak için daha fazla özellik ve denetim içerir. Bu ilkeleri oluşturmak ve yapılandırmak için bkz. Kimlik avı için [Defender'da kimlik avı ilkelerini Office 365](configure-mdo-anti-phishing-policies.md).

#### <a name="advanced-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365"></a>Kimlik avıyla mücadele ilkeleri için Microsoft Defender'daki gelişmiş Office 365

Bu ayar hakkında daha fazla bilgi için bkz. Gelişmiş kimlik avı ilkeleri için [Microsoft Defender'da kimlik avıyla mücadele Office 365](set-up-anti-phishing-policies.md#advanced-phishing-thresholds-in-anti-phishing-policies-in-microsoft-defender-for-office-365). Bu ayarı yapılandırmak için bkz. Kimlik avı için [Defender'da kimlik avı ilkelerini Office 365](configure-mdo-anti-phishing-policies.md).

<br>

****

|Güvenlik özelliği adı|Default|Standard|Katı|Açıklama ekleme|
|---|:---:|:---:|:---:|---|
|**Kimlik avı e-posta eşiği** <p> _PhishThresholdLevel_|**1 - Standart** <p> `1`|**2 - Saldırgan** <p> `2`|**3 - Daha agresif** <p> `3`||
|

#### <a name="impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365"></a>Office 365 için Microsoft Defender'da kimlik avı önleme ilkelerinde kimliğe bürünme Office 365

Bu ayarlar hakkında daha fazla bilgi için bkz. Kimlik avı önleme ilkeleri için [Microsoft Defender'da Kimliğe Bürünme Office 365](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365). Bu ayarları yapılandırmak için bkz. [Kimlik avı için Defender'da kimlik avı ilkelerini Office 365](configure-mdo-anti-phishing-policies.md).

<br>

****

|Güvenlik özelliği adı|Default|Standard|Katı|Açıklama ekleme|
|---|:---:|:---:|:---:|---|
|**Kimlik avı eşiği & koruması**|||||
|**Kullanıcıların korumasını etkinleştirme** (kimliğine bürünülen kullanıcı koruması) <p> _EnableTargetedUserProtection_ <p> _TargetedUsersToProtect_|Seçili değil <p> `$false` <p> yok|Seçildi <p> `$true` <p> \<list of users\>|Seçildi <p> `$true` <p> \<list of users\>|Önemli rollere kullanıcı (ileti gönderenleri) eklemenizi öneririz. Şirket içinde koruma altında olan gönderenler CEO'nız, CFO'nız ve diğer üst düzey liderlerden olabilir. Dışarıdan korumalı gönderenler, üyeleri veya yönetim kurulu üyelerini içerebilir. <p> Önceden ayarlanmış güvenlik ilkelerde, korumak istediğiniz kullanıcıları belirtebilirsiniz. Önerilen önemli rollere kullanıcı eklemek için önceden ayarlanmış güvenlik ilkelerini devre dışı bırakmanız ve özel kimlik avı koruma ilkelerini kullanmalıdır.|
|**Korumak için etki alanlarını etkinleştirme** (kimliğine bürünülen etki alanı koruması)|Seçili değil|Seçildi|Seçildi||
|**Sahibim olan etki alanlarını dahil** <p> _EnableOrganizationDomainsProtection_|Kapalı <p> `$false`|Seçildi <p> `$true`|Seçildi <p> `$true`||
|**Özel etki alanlarını dahil eder** <p> _EnableTargetedDomainsProtection_ <p> _TargetedDomainsToProtect_|Kapalı <p> `$false` <p> yok|Seçildi <p> `$true` <p> \<list of domains\>|Seçildi <p> `$true` <p> \<list of domains\>|Sahip olmadığınız, ancak sık sık etkileşim kurduğunız etki alanlarını (gönderen etki alanları) eklemenizi öneririz. <p> Önceden belirlenmiş güvenlik ilkelerde, korumak için özel etki alanlarını belirtebilirsiniz. Önerilen şekilde korumak üzere özel etki alanları eklemek için önceden ayarlanmış güvenlik ilkelerini devre dışı bırakmanız ve özel kimlik avı koruma ilkelerini kullanmalıdır.|
|**Güvenilen gönderenleri ve etki alanlarını ekleme** <p> _ExcludedSenders_ <p> _ExcludedDomains_|Yok|Yok|Yok|Organizasyona bağlı olarak, yanlış şekilde kimliğe bürünme girişimleri olarak tanımlanan gönderenleri veya etki alanlarını eklemenizi öneririz.|
|**Posta kutusu zekası etkinleştirme** <p> _EnableMailboxIntelligence_|Seçildi <p> `$true`|Seçildi <p> `$true`|Seçildi <p> `$true`||
|**Kimliğe bürünme koruması için zekayı etkinleştirme** <p> _EnableMailboxIntelligenceProtection_|Kapalı <p> `$false`|Seçildi <p> `$true`|Seçildi <p> `$true`|Bu ayar, belirtilen eylemin posta kutusu zekası tarafından kimliğe bürünme algılamaları için izin verir.|
|**Eylemler**||||İletiyi **karantinaya alın'ı her** **seçseniz, Karantina ilkesi seç** kutusu da kullanılabilir. Karantina ilkeleri, kullanıcıların karantinaya alınmış iletilerde neler yapmalarına izin verilmiyor? <p> Yeni bir kimlik avı önleme ilkesi musunuz? Boş bir değer, bu kararla karantinaya alınan iletiler için geçmiş özelliklerini tanımlamak üzere varsayılan karantina ilkesi anlamına gelir (tüm kimliğe bürünme algılama türleri için DefaultFullAccessPolicy). <p> Yöneticiler, kullanıcılar için daha az kısıtlayıcı veya daha kısıtlayıcı özellikler tanımlayan özel karantina ilkeleri oluşturabilir ve bu ilkeleri kullanabilir. Daha fazla bilgi için bkz. [Karantina ilkeleri](quarantine-policies.md).|
|**İleti kimliğine bürünülen bir kullanıcı olarak algılanırsa** <p> _TargetedUserProtectionAction_|**Hiçbir eylem uygulama** <p> `NoAction`|**İletiyi karantinaya alın** <p> `Quarantine`|**İletiyi karantinaya alın** <p> `Quarantine`|Önceden ayarlanmış güvenlik ilkelerinin, korumak istediğiniz kullanıcıları belirtmenize izin olmadığını unutmayın; dolayısıyla bu ayar önceden ayarlanmış güvenlik ilkelerde hiçbir şeyi etkili bir şekilde yapar.|
|**İleti kimliğine bürünülen bir etki alanı olarak algılanırsa** <p> _TargetedDomainProtectionAction_|**Hiçbir eylem uygulama** <p> `NoAction`|**İletiyi karantinaya alın** <p> `Quarantine`|**İletiyi karantinaya alın** <p> `Quarantine`|Önceden ayarlanmış güvenlik ilkelerinin korunmak üzere özel etki alanlarını belirtmenize izin vermeyeceğini unutmayın; bu nedenle bu ayar özel etki alanlarını değil, yalnızca sahibi olduğunuz etki alanlarını etkiler.|
|**Posta kutusu zekası kimliğine bürünülen kullanıcı algılarsa** <p> _MailboxIntelligenceProtectionAction_|**Hiçbir eylem uygulama** <p> `NoAction`|**İletiyi alıcıların Gereksiz E-posta klasörlerine taşıma** <p> `MoveToJmf`|**İletiyi karantinaya alın** <p> `Quarantine`||
|**Kullanıcı kimliğe bürünme kullanıcı kimliğini güvenlik ipucu** <p> _EnableSimilarUsersSafetyTips_|Kapalı <p> `$false`|Seçildi <p> `$true`|Seçildi <p> `$true`||
|**Etki alanı kimliğe bürünme kullanıcılarını güvenlik ipucu** <p> _EnableSimilarDomainsSafetyTips_|Kapalı <p> `$false`|Seçildi <p> `$true`|Seçildi <p> `$true`||
|**Kullanıcı kimliğe bürünme alışılmadık karakterleri güvenlik ipucu** <p> _EnableUnusualCharactersSafetyTips_|Kapalı <p> `$false`|Seçildi <p> `$true`|Seçildi <p> `$true`||
|

#### <a name="eop-anti-phishing-policy-settings-in-microsoft-defender-for-office-365"></a>Kimlik avı için Microsoft Defender'da EOP kimlik avına karşı koruma Office 365

Bunlar, [EOP'de istenmeyen posta önleme ilkesi ayarlarında kullanılabilen ayarlarla aynıdır](#eop-anti-spam-policy-settings).

Poof ayarları birbirine göre bağlantılıdır, ancak İlk kişi güvenlik ipucu  ayarının gizlilik ayarına bağımlılığı yoktur.

<br>

****

|Güvenlik özelliği adı|Default|Standard|Katı|Açıklama ekleme|
|---|:---:|:---:|:---:|---|
|**Kimlik avı eşiği & koruması**|||||
|**Akıllı ifadeyi etkinleştirme** <p> _EnableSpoofIntelligence_|Seçildi <p> `$true`|Seçildi <p> `$true`|Seçildi <p> `$true`||
|**Eylemler**|||||
|**İleti, bir ifadeyle algılanırsa** <p> _AuthenticationFailAction_|**İletiyi alıcıların Gereksiz E-posta klasörlerine taşıma** <p> `MoveToJmf`|**İletiyi alıcıların Gereksiz E-posta klasörlerine taşıma** <p> `MoveToJmf`|**İletiyi karantinaya alın** <p> `Quarantine`|Bu ayar, bilgi e-posta bilgisinde gösterildiği gibi otomatik olarak engellenen veya Kiracı İzin Ver/[](learn-about-spoof-intelligence.md)Engelleme Listesi'ne el ile engellenen kimliği doğrulandı [gönderenler için geçerlidir](tenant-allow-block-list.md). <p> İletiyi **karantinaya alın'ı** seçerseniz, kullanıcıların karantinaya alınmış iletilerde neler yapmalarına izin verilmiyor öğesini tanımlayan karantina ilkesi kutusunu seçmek için bir Karantina ilkesi uygula kutusu kullanılabilir. Yeni kimlik avı önleme ilkesi musunuz? Boş değer, kimlik karantinası iletileri (DefaultFullAccessPolicy) için geçmiş özellikleri tanımlamak üzere varsayılan karantina ilkesi anlamına gelir. <p> Yöneticiler, alıcıların karantinada bu iletilerde yapmalarına izin verilenleri tanımlayan bir özel karantina ilkesi oluşturabilir ve bu ilkeyi kullanabilir. Daha fazla bilgi için bkz. [Karantina ilkeleri](quarantine-policies.md).|
|**İlk kişi bilgilerini güvenlik ipucu** <p> _EnableFirstContactSafetyTips_|Seçili değil <p> `$false`|Seçildi <p> `$true`|Seçildi <p> `$true`|Daha fazla bilgi için bkz[. İlk kişi güvenlik ipucu](set-up-anti-phishing-policies.md#first-contact-safety-tip).|
|**Kimlik doğrulaması için kimliği doğrulanmamış gönderenler için göster (?)** <p> _EnableUnauthenticatedSender_|Seçildi <p> `$true`|Seçildi <p> `$true`|Seçildi <p> `$true`|Tanımlanamayan kimliksiz gönderenler için Outlook'da gönderenin fotoğrafına bir soru işareti (?) ekler. Daha fazla bilgi için bkz [. Kimliği doğrulanmamış gönderen](set-up-anti-phishing-policies.md#unauthenticated-sender).|
|**"Aracılığıyla" etiketini göster** <p> _EnableViaTag_|Seçildi <p> `$true`|Seçildi <p> `$true`|Seçildi <p> `$true`|DKIM imzası veya MAIL **FROM** chris@contoso.com farklı ise, Gönderen adresine aracılığıyla etiketi (chris@contoso.com fabrikam.com aracılığıyla gönder) ekler. <p> Daha fazla bilgi için bkz [. Kimliği doğrulanmamış gönderen](set-up-anti-phishing-policies.md#unauthenticated-sender).|
|

### <a name="safe-attachments-settings"></a>Kasa Ek ayarlarını değiştirme

Kasa için Microsoft Defender'daki Office 365 Ekleri, Kasa Ekleri ilkeleriyle ilişkisiz genel ayarları ve her bir Kasa içerir. Daha fazla bilgi için bkz[. Kasa için Defender'daki Ekler'Office 365](safe-attachments.md).

Varsayılan Kasa Ekler ilkesi her ne kadar da olsa, yerleşik koruma önceden ayarlanmış güvenlik  ilkesi tüm alıcılara Kasa Ekler koruması sağlar (özel Kasa Ek ilkeleri içinde tanımlanmamış kullanıcılar). Daha fazla bilgi için bkz[. İlke için EOP'de ve Microsoft Defender'da önceden Office 365](preset-security-policies.md).

#### <a name="global-settings-for-safe-attachments"></a>E-posta Ekleri Kasa genel ayarları

> [!NOTE]
> Ekler için genel Kasa yerleşik koruma önceden ayarlanmış güvenlik ilkesiyle ayarlanır, ancak  **Standart** veya Katı önceden tanımlı güvenlik ilkeleri **tarafından** ayarlanmaz. Her iki durumda da, yöneticiler bu genel Kasa Ek ayarları üzerinde istediğiniz zaman değişiklik yapabilirsiniz.
>
> Varsayılan **sütunda** , yerleşik koruma önceden ayarlanmış güvenlik ilkesi **varlığından önce değerler** görüntülenir. Yerleşik **koruma sütunu,** yerleşik koruma önceden ayarlanmış güvenlik ilkesi tarafından ayarlanan değerleri gösterir  ve bu da bizim önerilen değerlerimizdir.

Bu ayarları yapılandırmak için bkz. SharePoint, [OneDrive](turn-on-mdo-for-spo-odb-and-teams.md), Microsoft Teams ve Kasa Belgeleri için Kasa [Ekleri Microsoft 365 E5](safe-docs.md).

PowerShell'de, bu ayarlar için [Set-AtpPolicyForO365](/powershell/module/exchange/set-atppolicyforo365) cmdlet'ini kullanırsiniz.

<br>

****

|Güvenlik özelliği adı|Default|Yerleşik koruma|Açıklama ekleme|
|---|:---:|:---:|---|
|**SharePoint, OneDrive ve Office 365 için Defender'ı Microsoft Teams** <p> _EnableATPForSPOTeamsODB_|Kapalı <p> `$false`|On <p> `$true`|Kullanıcıların kötü amaçlı dosyaları indirmesini engellemek için bkz[. SharePoint Online PowerShell kullanarak kullanıcıların kötü amaçlı dosyaları indirmesini engelleme](turn-on-mdo-for-spo-odb-and-teams.md#step-2-recommended-use-sharepoint-online-powershell-to-prevent-users-from-downloading-malicious-files).|
|**Office istemcileri için Belgeleri Kasa açma** <p> _EnableSafeDocs_|Kapalı <p> `$false`|On <p> `$true`|Bu özellik yalnızca Office 365 için Defender'a dahil edilen lisanslarla (örneğin, Microsoft 365 E5 veya başka bir Microsoft 365 E5 Güvenlik). Daha fazla bilgi için bkz[. Kasa Belge Belgeleri'Microsoft 365 E5](safe-docs.md).|
|**Belgelerin dosyayı kötü amaçlı olarak tanımlasa bile Kasa Korumalı Görünüm'e tıklamasına izin ver** <p> _AllowSafeDocsOpen_|Kapalı <p> `$false`|Kapalı <p> `$false`|Bu ayar, Belgeler'Kasa ilgilidir.|
|

#### <a name="safe-attachments-policy-settings"></a>Kasa ler ilke ayarlarını değiştirme

Bu ayarları yapılandırmak için bkz. [Kasa Office 365 için Defender'da Ek İlkeleri Office 365](set-up-safe-attachments-policies.md).

PowerShell'de, bu ayarlar için [New-SafeAttachmentPolicy](/powershell/module/exchange/new-safeattachmentpolicy) ve [Set-SafeAttachmentPolicy](/powershell/module/exchange/set-safelinkspolicy) cmdlet'lerini kullanırsiniz.

> [!NOTE]
> Daha önce açıklandığı gibi, Kasa için varsayılan bir ek ilkesi yoktur ancak Kasa Ekleri koruması yerleşik koruma önceden ayarlanmış güvenlik ilkesi tarafından tüm [ alıcılara atanır](preset-security-policies.md).
>
> Özel **sütundaki Varsayılan**, yeni sütunda varsayılan değerlere başvurur Kasa Ekler ilkelerine başvurur. Kalan sütunlar, karşılık gelen önceden ayarlanmış güvenlik ilkelerde yapılandırılan değerleri gösterir (aksi belirtilmedikçe).

<br>

****

|Güvenlik özelliği adı|Özelde varsayılan|Yerleşik koruma|Standard|Katı|Açıklama ekleme|
|---|:---:|:---:|:---:|:---:|---|
|**Kasa bilinmeyen kötü amaçlı yazılım yanıtı** <p> _Etkinleştirme_ ve _Eylem_|**Kapalı** <p> `-Enable $false` ve `-Action Block`|**Engelle** <p> `-Enable $true` ve `-Action Block`|**Engelle** <p> `-Enable $true` ve `-Action Block`|**Engelle** <p> `-Enable $true` ve `-Action Block`|Enable _parametresi_ etkinleştir $false, _Action parametresinin değeri_ önemli değildir.|
|**Karantina ilkesi** (_Karantina Etiketi_)|AdminOnlyAccessPolicy|AdminOnlyAccessPolicy|AdminOnlyAccessPolicy|AdminOnlyAccessPolicy|Ekler ilkesi oluşturmak Kasa, boş bir değer, Kasa Attachments (AdminOnlyAccessPolicy) tarafından karantinaya alınmış iletiler için geçmiş özelliklerini tanımlamak için varsayılan karantina ilkesi anlamına gelir. <p> Yöneticiler kullanıcılar için daha fazla özellik tanımlayan özel karantina ilkeleri oluşturabilir ve bu ilkeleri kullanabilir. Daha fazla bilgi için bkz. [Karantina ilkeleri](quarantine-policies.md).|
|**Algılanan eklerle eki yeniden yönlendirme** : **Yeniden yönlendirmeyi etkinleştir** <p> _Yeniden yönlendirme_ <p> _RedirectAddress_|Seçilmedi ve e-posta adresi belirtilmemiş. <p> `-Redirect $false` <p> _RedirectAddress_ boş (`$null`)|Seçilmedi ve e-posta adresi belirtilmemiş. <p> `-Redirect $false` <p> _RedirectAddress_ boş (`$null`)|Bir e-posta adresi seçin ve belirtin. <p> `$true` <p> e-posta adresi|Bir e-posta adresi seçin ve belirtin. <p> `$true` <p> e-posta adresi|İletileri gözden geçirmesi için bir güvenlik yöneticisine yönlendirin. <p> **Not**: Bu ayar **Standart, Katı** veya **Yerleşik koruma önceden** ayarlanmış **güvenlik ilkelarında** yapılandırılmaz. Standart **ve** **Katı değerleri**, yeni **veya sizin** Kasa Ek ilkeleri içinde önerilen değerlerimizi gösterir.|
|**Tarama Kasa tamamlanmadı ise Ekler algılama yanıtı uygulama (zaman aşımı veya hatalar)** <p> _ActionOnError_|Seçildi <p> `$true`|Seçildi <p> `$true`|Seçildi <p> `$true`|Seçildi <p> `$true`||
|

### <a name="safe-links-settings"></a>Kasa Bağlantıları ayarları

Kasa için Defender'daki bağlantılar Office 365 etkin Kasa Bağlantıları ilkelerine dahil olan tüm kullanıcılar için geçerli olan genel ayarları ve her bir Grup Kasa içerir. Daha fazla bilgi için bkz. [Kasa için Defender'daki Bağlantılar'Office 365](safe-links.md).

Varsayılan Bağlantı ilkesi Kasa, yerleşik koruma önceden ayarlanmış güvenlik ilkesi tüm alıcılara  Kasa Bağlantıları koruması sağlar (özel Bağlantılar ilkeleri içinde tanımlanmamış kullanıcılar Kasa). Daha fazla bilgi için bkz[. İlke için EOP'de ve Microsoft Defender'da önceden Office 365](preset-security-policies.md).

#### <a name="global-settings-for-safe-links"></a>Yeni Bağlantılar için Kasa ayarları

> [!NOTE]
> Dış Bağlantılar Kasa genel ayarları Yerleşik koruma önceden ayarlanmış güvenlik ilkesiyle ayarlanır, ancak **Standart** veya Katı önceden tanımlı güvenlik ilkeleri **tarafından** ayarlanmaz. Her iki durumda da, yöneticiler bu genel bağlantı Kasa zaman değiştirebilir.
>
> Varsayılan **sütunda** , yerleşik koruma önceden ayarlanmış güvenlik ilkesi **varlığından önce değerler** görüntülenir. Yerleşik **koruma sütunu,** yerleşik koruma önceden ayarlanmış güvenlik ilkesi tarafından ayarlanan değerleri gösterir  ve bu da bizim önerilen değerlerimizdir.

Bu ayarları yapılandırmak için bkz. [Windows için Defender'Kasa Bağlantılar için genel Office 365](configure-global-settings-for-safe-links.md).

PowerShell'de, bu ayarlar için [Set-AtpPolicyForO365](/powershell/module/exchange/set-atppolicyforo365) cmdlet'ini kullanırsiniz.

<br>

****

|Güvenlik özelliği adı|Default|Yerleşik koruma|Açıklama ekleme|
|---|:---:|:---:|---|
|**Aşağıdaki URL'leri engelleme** <p> _ExcludedUrls_|Boş <p> `$null`|Boş <p> `$null`|Bu ayar için özel bir önerimiz yok. <p> Daha fazla bilgi için, [Bu Bağlantılar için "Aşağıdaki URL'leri engelleme" Kasa bakın](safe-links.md#block-the-following-urls-list-for-safe-links).
|**Office 365 Kasa Bağlantılarını kullanma** <p> _EnableSafeLinksForO365Clients_|On <p> `$true`|On <p> `$true`|Desteklenen Kasa ve mobil (iOS Office 365 Android) uygulamalarda Bağlantılar'a tıklayın. Daha fazla bilgi için bkz[. Kasa uygulamaları için bağlantılar Office 365 bakın](safe-links.md#safe-links-settings-for-office-365-apps).|
|**Kullanıcılar Office 365 uygulamaları korumalı bağlantılara tıklay Office 365 izleme** <p> _TrackClicks_|On <p> `$false`|Kapalı <p> `$true`|Bu ayarı kapatarak (_Tıklatmaları İzle ayarı_`$true`), desteklenen uygulamalarda kullanıcı tıklamalarını Office 365 izler.|
|**Kullanıcıların uygulamalarda özgün URL'ye tıklamalarına izin Office 365 verme** <p> _AllowClickThrough_|On <p> `$false`|On <p> `$false`|Bu ayarın açması (_AllowClickThrough_ `$false`ayarı), desteklenen diğer uygulamalarda özgün URL'ye Office 365 sağlar.|
|

#### <a name="safe-links-policy-settings"></a>Kasa Bağlantıları ilke ayarları

Bu ayarları yapılandırmak için bkz. [Aşağıdakiler için Microsoft Defender Kasa Bağlantı ilkelerini Office 365](set-up-safe-links-policies.md).

PowerShell'de, bu ayarlar için [New-SafeLinksPolicy](/powershell/module/exchange/new-safelinkspolicy) ve [Set-SafeLinksPolicy](/powershell/module/exchange/set-safelinkspolicy) cmdlet'lerini kullanırsiniz.

> [!NOTE]
> Daha önce açıklandığı gibi, varsayılan Kasa yoktur, ancak Kasa önceden ayarlanmış güvenlik ilkesiyle Tüm alıcılara Bağlantı koruması [ atanır](preset-security-policies.md).
>
> Özel **sütundaki Varsayılan**, yeni sütunda varsayılan değerlere başvurur Kasa Bağlantılar ilkelerine başvurur. Kalan sütunlar, karşılık gelen önceden ayarlanmış güvenlik ilkelerde yapılandırılan değerleri gösterir (aksi belirtilmedikçe).

<br>

****

|Güvenlik özelliği adı|Özelde varsayılan|Yerleşik koruma|Standard|Katı|Açıklama ekleme|
|---|:---:|:---:|:---:|:---:|---|
|**Koruma ayarları**||||||
|**İletilerde kötü amaçlı olabilecek bilinmeyen URL'lerin eylemlerini seçme** <p> _IsEnabled_|**Kapalı** <p> `$false`|**On** <p> `$true`|**On** <p> `$true`|**On** <p> `$true`||
|**Dosya içindeki bilinmeyen veya kötü amaçlı olabilecek URL'lere yönelik eylemi Microsoft Teams** <p> _EnableSafeLinksForTeams_|**Kapalı** <p> `$false`|**On** <p> `$true`|**On** <p> `$true`|**On** <p> `$true`||
|**Dosyaları işaret alan şüpheli bağlantılar ve bağlantılar için gerçek zamanlı URL tarama uygulama** <p> _ScanUrls_|Seçili değil <p> `$false`|Seçildi <p> `$true`|Seçildi <p> `$true`|Seçildi <p> `$true`||
|**İletiyi teslim etmek için URL tarama işleminin tamamlanacak şekilde bekleme** <p> _DeliverMessageAfterScan_|Seçili değil <p> `$false`|Seçildi <p> `$true`|Seçildi <p> `$true`|Seçildi <p> `$true`||
|**Kuruluş Kasa e-posta iletilerine özel bağlantılar uygulama** <p> _EnableForInternalSenders_|Seçili değil <p> `$false`|Seçildi <p> `$true`|Seçildi <p> `$true`|Seçildi <p> `$true`||
|**Kullanıcı tıklamalarını izleme** <p> _DoNotTrackUserClicks_|Seçili değil <p> `$false`|Seçili değil <p> `$false`|Seçili değil <p> `$false`|Seçili değil <p> `$false`|Bu ayarın kapatılmamıştır ( _DoNotTrackUserClicks_ ayarı), kullanıcılara `$false`yapılan tıklamaları izler.|
|**Kullanıcıların özgün URL'ye tıklamalarına izin verme** <p> _DoNotAllowClickThrough_|Seçili değil <p> `$false`|Seçili değil <p> `$false`|Seçildi <p> `$true`|Seçildi <p> `$true`|Bu ayarın açması ( _DoNotAllowClickThrough_ ayarı `$true`), özgün URL'ye tıklamayı engeller.|
|**Bildirim ve uyarı sayfalarında kuruluşun markasını görüntüleme** <p> _EnableOrganizationBranding_|Seçili değil <p> `$false`|Seçili değil <p> `$false`|Seçili değil <p> `$false`|Seçili değil <p> `$false`|Bu ayar için özel bir önerimiz yok. <p> Bu ayarı açmadan önce, Şirket logonuzu yüklemek için [Microsoft 365'daki](../../admin/setup/customize-your-organization-theme.md) Yönergeleri izledikten sonra, Microsoft 365 temasını özelleştirme.|
|**URL'leri yeniden yazmama, yalnızca Bağlantı API'si Kasa yoluyla kontrol edin** <p> _DisableURLRewrite_|Seçili değil <p> `$false`|Seçildi <p> `$true`|Seçili değil <p> `$false`|Seçili değil <p> `$false`||
|**Aşağıdaki URL'leri yeniden yazma** <p> _DoNotRewriteUrls_|Seçili değil <p> boş|Seçili değil <p> boş|Seçili değil <p> boş|Seçili değil <p> boş|Bu ayar için özel bir önerimiz yok. Daha fazla bilgi için, [Bağlantılar ilkeleri altında "Aşağıdaki URL'leri yeniden yazma" Kasa bakın](safe-links.md#do-not-rewrite-the-following-urls-lists-in-safe-links-policies).|
|**Bildirim**||||||
|**Kullanıcılarınıza nasıl bildirim yapmak gerekir?**|**Varsayılan bildirim metnini kullanma**|**Varsayılan bildirim metnini kullanma**|**Varsayılan bildirim metnini kullanma**|**Varsayılan bildirim metnini kullanma**|Bu ayar için özel bir önerimiz yok. <p> Kullanmak üzere özelleştirilmiş **bildirim metni girmek için Özel** bildirim metni kullan'ı (_CustomNotificationText_) seçin. Ayrıca, özel bildirim **metnini Microsoft Çeviri diline** çevirmek için Otomatik olarak yerelleştirme için Metin Kullan'ı (_UseTranslatedNotificationText_) de kullanabilirsiniz.
|

## <a name="related-articles"></a>İlgili makaleler

- Posta akış kurallarını (aktarım kuralları **olarak Exchange) hakkında en iyi uygulamaları mı arıyorsunuz**? Bkz[. Aynı adreste posta akış kurallarını yapılandırmak için en Exchange Online](/exchange/security-and-compliance/mail-flow-rules/configuration-best-practices).

- Yöneticiler ve kullanıcılar çözümleme için hatalı pozitif sonuçları (iyi e-posta kötü olarak işaretlenmiş) ve hatalı negatifleri (izin verilen hatalı e-posta) Microsoft'a gönderebilirsiniz. Daha fazla bilgi için bkz [. İletileri ve dosyaları Microsoft'a bildirme](report-junk-email-messages-to-microsoft.md).

- [EOP](/exchange/standalone-eop/set-up-your-eop-service) hizmetinizi ayarlama ve Windows için Microsoft **Defender'ı** yapılandırma hakkında **bilgi için** [bu Office 365](defender-for-office-365.md). 'Aynı adreste Tehditlere Karşı Koruma' içinde [yararlı Office 365](protect-against-threats.md) unutmayın.

- **Windows** için güvenlik taban çizgilerini burada bulunabilir: GPO/şirket içi seçenekler için güvenlik taban çizgilerini nereden edinebilirsiniz [?](/windows/security/threat-protection/windows-security-baselines#where-can-i-get-the-security-baselines) ve [Intune tabanlı güvenlik için Intune'da](/intune/protect/security-baselines) Windows cihazlarını yapılandırmak için güvenlik taban çizgilerini kullanın. Son olarak, Uç Nokta için Microsoft Defender ile Microsoft Intune güvenlik taban çizgilerini karşılaştırma, Uç Nokta için [Microsoft Defender ile Intune güvenlik taban çizgilerini karşılaştırma makalesinde Windows da kullanılabilir](/windows/security/threat-protection/microsoft-defender-atp/configure-machines-security-baseline#compare-the-microsoft-defender-atp-and-the-windows-intune-security-baselines).
