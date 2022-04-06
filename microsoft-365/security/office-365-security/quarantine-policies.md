---
title: Karantina ilkeleri
ms.author: chrisda
author: chrisda
manager: dansimp
ms.reviewer: ''
ms.date: ''
audience: ITPro
ms.topic: how-to
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: ''
ms.collection:
- M365-security-compliance
ms.custom: ''
description: Yöneticiler, kullanıcıların karantinaya alınmış iletilerde neler yapasını denetlemek için karantina ilkelerini kullanmayı öğrenebilir.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 0e5f1ea75a24d84f0b6d6b9e003a0123928ac49a
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2022
ms.locfileid: "63682845"
---
# <a name="quarantine-policies"></a>Karantina ilkeleri

Exchange Online Protection (EOP _) ve_ Office 365 için Microsoft Defender'daki karantina ilkeleri (daha önce karantina etiketleri olarak bilinirdi) yöneticilerin, iletinin neden karantinaya alındığına bağlı olarak kullanıcıların karantinaya alınmış iletilerde neler yapacılarını denetlemesine olanak sağlar.

Geleneksel olarak, ileti neden karantinaya alındığına bağlı olarak kullanıcılara karantina iletileri için etkileşim düzeylerine izin verilmiş veya reddedilmiştir. Örneğin, kullanıcılar istenmeyen posta önleme filtresiyle istenmeyen posta veya toplu olarak karantinaya alınmış iletileri  görüntüp serbest bıraksa da, yüksek güveni olan kimlik avı veya kötü amaçlı yazılım olarak karantinaya alınmış iletileri görüntüden veya serbest bırakarak görüntüde bırak yayımlanan iletiler görüntüde değildir.

Desteklenen [koruma özellikleri için](#step-2-assign-a-quarantine-policy-to-supported-features) karantina ilkeleri, kullanıcıların karantinada ve karantina bildirimleri içinde kendi iletileri (alıcıları olan iletiler) için neler yapmalarına izin verilmiyor _?_ [Karantina bildirimleri,](use-spam-notifications-to-release-and-report-quarantined-messages.md) son kullanıcı istenmeyen posta bildirimlerinin yerine gelen bildirimdir. Bu bildirimler artık karantina ilkeleriyle denetlenmektedir ve tüm desteklenen koruma özellikleri için karantinaya alınmış iletiler hakkında bilgi içerir (yalnızca istenmeyen posta önleme ilkesi ve kimlik avı koruma ilkesi kararları değil).

Geçmiş kullanıcı özelliklerini zorunlu alan varsayılan karantina ilkeleri, iletileri karantinaya alan desteklenen koruma özelliklerinde eylemlere otomatik olarak atanır. Öte ya da, özel karantina ilkeleri oluşturabilir ve bunları desteklenen koruma özelliklerine atayarak kullanıcıların bu tür karantinaya alınmış ileti türlerinde belirli eylemler gerçekleştirmesine izin ve ardından bunları atabilirsiniz.

Tek tek karantina ilkesi izinleri, aşağıdaki önceden ayarlanmış izin gruplarında bir araya alınır:

- Erişim yok
- Sınırlı erişim
- Tam erişim

Önceden ayarlanmış izin gruplarında bulunan tek tek karantina ilkesi izinleri aşağıdaki tabloda açıklanmıştır:

|İzin|Erişim yok|Sınırlı erişim|Tam erişim|
|---|:---:|:---:|:---:|
|**Göndereni engelleme** (_PermissionToBlockSender_)||![Onay işareti.](../../media/checkmark.png)|![Onay işareti.](../../media/checkmark.png)|
|**Delete** (_PermissionToDelete_)||![Onay işareti.](../../media/checkmark.png)|![Onay işareti.](../../media/checkmark.png)|
|**Önizleme** (_PermissionToPreview_)||![Onay işareti.](../../media/checkmark.png)|![Onay işareti.](../../media/checkmark.png)|
|**Alıcıların iletiyi karantinadan bırakmasına izin verme** (_PermissionToRelease_)|||![Onay işareti.](../../media/checkmark.png)|
|**Alıcıların bir iletinin karantinadan çıkarılmaz** için istekte olmasına izin verme (_PermissionToRequestRelease_)||![Onay işareti](../../media/checkmark.png)||

Varsayılan karantina ilkeleri, ilişkili izin grupları ve karantina bildirimlerinin etkin olup olmadığı aşağıdaki tabloda açıklanmıştır:

|Varsayılan karantina ilkesi|İzin grubu kullanıldı|Karantina bildirimleri etkinleştirilsin mi?|
|---|---|---|
|AdminOnlyAccessPolicy|Erişim yok|Hayır|
|DefaultFullAccessPolicy|Tam erişim|Hayır|
|NotificationEnabledPolicy<sup>\*</sup>|Tam erişim|Evet|

Önceden ayarlanmış izin gruplarında varsayılan izinleri istemiyorsanız veya karantina bildirimlerini etkinleştirmek için özel karantina ilkeleri oluşturun ve kullanın. Her iznin ne yaptığı hakkında daha fazla bilgi için, bu [makalenin devam](#quarantine-policy-permission-details) bölümündeki Karantina ilkesi izin ayrıntıları bölümüne bakın.

Microsoft 365 Defender portalında veya PowerShell'de (Exchange Online posta kutuları olan Microsoft 365 PowerShell için Exchange Online, EOP kuruluşlarında tek başına EOP PowerShell oluşturma ve atama Exchange Online kutularını da) kullanın.

> [!NOTE]
> İletilerin kullanım süresi ne kadar süre dolsa da, istenmeyen posta önleme ilkelerde İstenmeyen postayı bu kadar süre karantinada **tutma (**_KarantinaRetentionPeriod_) tarafından denetlenmeden önce karantinada tutulacak. Daha fazla bilgi için bkz. [EOP'de istenmeyen posta önleme ilkelerini yapılandırma](configure-your-spam-filter-policies.md).
>
> Desteklenen bir koruma özelliğine atanmış karantina ilkesi değiştirdikten sonra bu değişiklik, değişikliği yapıldıktan sonra karantinaya alınan iletileri etkiler. Daha önce bu koruma özelliği tarafından karantinaya alınmış olan iletiler yeni karantina ilkesi ataması ayarlarından etkilenmez.

## <a name="full-access-permissions-and-quarantine-notifications"></a>Tam erişim izinleri ve karantina bildirimleri

<sup>\*</sup> NotificationEnabledPolicy adlı karantina ilkesi her ortamda yok. Organizasyonunız aşağıdaki gereksinimlerin ikisini de karşılamıyorsa NotificationEnabledPolicy karantina ilkesine sahip olursunuz:

- Karantina ilkesi özelliği önceden (Temmuz sonunda/Ağustos 2021'in başlarında) açıktı.
- Son kullanıcı istenmeyen posta bildirimlerini etkinleştir ayarının açık olduğu bir veya birden çok istenmeyen posta önleme ilkesi (varsayılan istenmeyen posta önleme ilkesi  veya özel istenmeyen posta önleme ilkeleri) vardı.[](configure-your-spam-filter-policies.md)

Daha önce açıklandığı gibi, istenmeyen posta önleme ilkelerini açmak veya kapatmak için kullanılan son kullanıcı istenmeyen posta bildirimlerini karantina ilkeleri içinde karantinaya alın. DefaultFullAccessPolicy adlı yerleşik karantina ilkesi, karantinaya alınmış iletiler için geçmiş  izinlerini yineler, ancak karantina  ilkesinde karantina bildirimleri açık değildir. Yerleşik ilkede değişiklik de yapılaamayacağınız için, DefaultFullAccessPolicy'de karantina bildirimlerini açasınız.

DefaultFullAccessPolicy izinlerini sağlamak, ancak karantina bildirimleri açık durumda olmak için, buna ihtiyacı olan kuruluşlarda (son kullanıcı istenmeyen posta bildirimlerinin açık olduğu kuruluşlar) DefaultFullAccessPolicy yerine Kullanmak üzere NotificationEnabledPolicy adlı ilkeyi oluşturduk.

İstenmeyen posta önleme ilkelerde son kullanıcı istenmeyen posta bildirimlerinin hiç etkinleştirilmemiş olduğu yeni kuruluşlarda veya daha eski kuruluşlarda, NotificationEnabledPolicy adlı karantina ilkesi olmayacaktır. Karantina bildirimlerini açmanın yolu, karantina bildirimlerinin açık olduğu özel karantina ilkeleri oluşturmak ve kullanmaktır.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Başlamadan önce bilmeniz gerekenler

- Microsoft 365 Defender portalını açın<https://security.microsoft.com>. Doğrudan Karantina ilkeleri **sayfasına gitmek için** , kullanın <https://security.microsoft.com/quarantinePolicies>.

- Exchange Online PowerShell'e bağlanmak [için bkz. Bağlan PowerShell Exchange Online e bağlama](/powershell/exchange/connect-to-exchange-online-powershell). Tek başına EOP PowerShell'e bağlanmak [için bkz. Bağlan PowerShell Exchange Online Protection e bağlama](/powershell/exchange/connect-to-exchange-online-protection-powershell).

- Karantina ilkelerini görüntülemek, oluşturmak, değiştirmek veya kaldırmak için, Microsoft 365 Defender portalında Kuruluş **Yönetimi, Güvenlik** Yöneticisi veya Karantina Yöneticisi rollerinin üyesi Microsoft 365 Defender gerekir.  Daha fazla bilgi için bkz[. Microsoft 365 Defender portalına.](permissions-microsoft-365-security-center.md)

## <a name="step-1-create-quarantine-policies-in-the-microsoft-365-defender-portal"></a>1. Adım: İlke portalında karantina Microsoft 365 Defender oluşturma

1. Microsoft 365 Defender [portalında, Kurallar](https://security.microsoft.com) bölümündeki **&-posta** \> ve işbirliği **& Kuralları** \> **Tehdit** \> ilkeleri **Karantina** **ilkeleri'ne** gidin.

2. Karantina ilkesi **sayfasında Özel** ilke ekle simgesine ![tıklayın.](../../media/m365-cc-sc-create-icon.png) **Özel ilke ekleyin**.

3. Yeni **ilke sihirbazı** açılır. İlke **adı sayfasında** , İlke adı kutusuna kısa ama benzersiz **bir ad** girin. Önümüzdeki adımlarda, karantina ilkesi tanımlamanız ve adla seçmeniz gerekir. Bitirdikten sonra, Sonraki'ne **tıklayın**.

4. Alıcı **iletisi erişimi sayfasında** , aşağıdaki değerlerden birini seçin:
   - **Sınırlı erişim**: Bu izin grubuna tek tek izinler bu makalenin önceki sayfalarında açıklanmıştır.
   - **Özel erişim ayarlama (Gelişmiş)**: Özel izinler belirtmek için bu değeri kullanın. Aşağıdaki ayarları yapılandırarak görünür:
     - **Sürüm eylemi tercihini** seçin: Aşağıdaki değerlerden birini seçin:
       - Boş: Bu, varsayılan değerdir.
       - **Alıcıların iletiyi karantinadan bırakmasına izin ver**
       - **Alıcıların bir iletinin karantinadan çıkarılım için istekte olmasına izin ver**
     - **Alıcıların karantinaya alınmış iletilere ek eylemleri seçme**: Aşağıdaki değerlerden birini, hiçbirini veya hiçbirini seçme:
       - **Silme**
       - **Önizleme**
       - **Göndereni engelle**

   Bu izinler ve karantinaya alınmış iletiler üzerindeki etkisi ve karantina bildirimlerinin içinde, bu makalenin sonraki [kısımlarında Karantina ilkesi](#quarantine-policy-permission-details) izin ayrıntıları bölümünde açıklanmıştır.

   Bitirdikten sonra, Sonraki'ne **tıklayın**.

5. Son kullanıcı **istenmeyen posta bildirimi sayfasında**, karantina bildirimlerini  (eski adı son kullanıcı istenmeyen posta bildirimleri) etkinleştirmek için Etkinleştir'i seçin. Bitirdikten sonra, Sonraki'ne **tıklayın**.

   > [!NOTE]
   > Daha önce de belirtildiği gibi, yerleşik ilkeler (AdminOnlyAccessPolicy veya DefaultFullAccessPolicy) karantinaya alınmış bildirimler açık değildir ve ilkeleri değiştiremezsiniz.

6. **İlkeyi gözden geçir** sayfasında ayarlarınızı gözden geçirebilirsiniz. Bölümün içindeki **ayarları değiştirmek** için her bölümde Düzenle'yi seçebilirsiniz. Geri'ye **tıklar** veya sihirbazda belirli bir sayfayı seçersiniz.

   Bitirdikten sonra Gönder'e **tıklayın**.

7. Görüntülenen onay sayfasında Bitti'ye **tıklayın**.

Artık, Adım 2 bölümünde açıklandığı gibi karantina ilkesine karantina özelliği [atamaya hazırsınız](#step-2-assign-a-quarantine-policy-to-supported-features) .

### <a name="create-quarantine-policies-in-powershell"></a>PowerShell'de karantina ilkeleri oluşturma

Karantina ilkeleri oluşturmak için PowerShell kullanmayı tercih ediyorsanız, PowerShell'Exchange Online veya PowerShell Exchange Online Protection e bağlanın ve **New-QuarantinePolicy** cmdlet'ini kullanın.

> [!NOTE]
> _ESNEnabled_ parametresini ve değerini kullansanız bile`$true`, karantina bildirimleri kapalıdır.

#### <a name="use-the-enduserquarantinepermissionsvalue-parameter"></a>EndUserQuarantinePermissionsValue parametresini kullanma

_EndUserQuarantinePermissionsValue parametresini_ kullanarak bir karantina ilkesi oluşturmak için, aşağıdaki söz dizimi kullanın:

```powershell
New-QuarantinePolicy -Name "<UniqueName>" -EndUserQuarantinePermissionsValue <0 to 236> [-EsnEnabled $true]
```

_EndUserQuarantinePermissionsValue_ parametresi, ikili değerden dönüştürülen bir ondalık değer kullanır. İkili değer, kullanılabilir son kullanıcı karantina izinlerine belirli bir sırada karşılık gelen değerdir. Her izin için 1 değeri Doğru'ya ve 0 değeri de Yanlış'a eşittir.

Tek tek her izin için gereken sıra ve değerler aşağıdaki tabloda açıklanmıştır:

|İzin|Ondalık değer|İkili değer|
|---|:---:|:---:|
|PermissionToViewHeader<sup>\*</sup>|128|10000000|
|PermissionToDownload<sup>\*\*</sup>|64|01000000|
|PermissionToAllowSender<sup>\*\*</sup>|32|00100000|
|PermissionToBlocksender|16|00010000|
|PermissionToRequestRelease<sup>\*\*\*</sup>|8|00001000|
|PermissionToRelease<sup>\*\*\*</sup>|4|00000100|
|PermissionToPreview|2|00000010|
|PermissionToDelete|1|00000001|

<sup>\*</sup>0 değeri, karantinaya alınmış iletinin ayrıntılarında İleti üstbilgilerini görüntüle düğmesini gizlemez (düğme her zaman kullanılabilir).

<sup>\*\*</sup> Bu ayar kullanılmaz (0 veya 1 değeri hiçbir şey yapar).

<sup>\*\*\*</sup> Bu değerlerin ikisini de 1 olarak ayarlayın. Birini 1,0 olarak ayarlayın veya her ikisini de 0 olarak ayarlayın.

Sınırlı erişim izinleri için gerekli değerler:

|İzin|Sınırlı erişim|
|---|:--:|
|PermissionToViewHeader|0|
|PermissionToDownload|0|
|PermissionToAllowSender|0|
|PermissionToBlocksender|1|
|PermissionToRequestRelease|1|
|PermissionToRelease|0|
|PermissionToPreview|1|
|PermissionToDelete|1|
|İkili değer|00011011|
|Ondalık değer|27|

Bu örnek, önceki tabloda açıklandığı gibi Sınırlı erişim izinlerini ataan karantina bildirimleri açık olarak Sınırlı Erişim adlı yeni bir karantina ilkesi oluşturur.

```powershell
New-QuarantinePolicy -Name LimitedAccess -EndUserQuarantinePermissionsValue 27 -EsnEnabled $true
```

Özel izinler için, istediğiniz izinlere karşılık gelen ikili değeri almak için önceki tabloyu kullanın. İkili değeri ondalık değere dönüştürin ve _EndUserQuarantinePermissionsValue parametresi için ondalık değeri_ kullanın. Parametre değeri için ikili değeri kullanmayın.

Ayrıntılı söz dizimi ve parametre bilgileri için bkz [. New-QuarantinePolicy](/powershell/module/exchange/new-quarantinepolicy).

## <a name="step-2-assign-a-quarantine-policy-to-supported-features"></a>2. Adım: Desteklenen özelliklere karantina ilkesi atama

_E-posta iletilerini_ karantinaya alan desteklenen koruma özelliklerinde, kullanılabilir karantina eylemlerine karantina ilkesi atabilirsiniz. İletileri karantinaya alan özellikler ve karantina ilkelerinin kullanılabilirliği aşağıdaki tabloda açıklanmıştır:

|Özellik|Karantina ilkeleri destekli mi?|Kullanılan varsayılan karantina ilkeleri|
|---|:---:|---|
|[İstenmeyen posta önleme ilkeleri](configure-your-spam-filter-policies.md): <ul><li>**İstenmeyen** Posta (_spamAction_)</li><li>**Yüksek güven istenmeyen** posta (_HighConfidenceSpamAction_)</li><li>**Kimlik Avı** (_PhishSpamAction_)</li><li>**Yüksek güven kimlik avı** (_HighConfidencePhishAction_)</li><li>**Toplu** (_BulkSpamAction_)</li></ul>|Evet|<ul><li>DefaultFullAccessPolicy<sup>\*</sup> (Tam erişim)</li><li>DefaultFullAccessPolicy<sup>\*</sup> (Tam erişim)</li><li>DefaultFullAccessPolicy<sup>\*</sup> (Tam erişim)</li><li>AdminOnlyAccessPolicy (erişim yok)</li><li>DefaultFullAccessPolicy<sup>\*</sup> (Tam erişim)</li></ul>|
|Kimlik avı önleme ilkeleri: <ul><li>[Kimliksiz zeka koruması](set-up-anti-phishing-policies.md#spoof-settings) (_AuthenticationFailAction_)</li><li>[Office 365 için Defender'da kimliğe bürünme koruması](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365):<ul><li>**İleti kimliğine bürünülen bir kullanıcı olarak algılanırsa** (_TargetedUserProtectionAction_)</li><li>**İleti kimliğine bürünülen bir etki alanı** olarak algılanırsa (_TargetedDomainProtectionAction_)</li><li>**Posta kutusu zekası kimliğine bürünülen kullanıcı algılarsa** (_MailboxIntelligenceProtectionAction_)</li></ul></li></ul>|Evet|<ul><li>DefaultFullAccessPolicy<sup>\*</sup> (Tam erişim)</li><li>Kimliğe bürünme koruması:<ul><li>DefaultFullAccessPolicy<sup>\*</sup> (Tam erişim)</li><li>DefaultFullAccessPolicy<sup>\*</sup> (Tam erişim)</li><li>DefaultFullAccessPolicy<sup>\*</sup> (Tam erişim)</li></ul></li></ul>|
|[Kötü amaçlı yazılımdan koruma](configure-anti-malware-policies.md) ilkeleri: Tüm algılanan iletiler her zaman karantinaya alınır.|Evet|AdminOnlyAccessPolicy (erişim yok)|
|[Kasa Korumasını Koruma](safe-attachments.md): <ul><li>Ekleri olan ve Ek ilkeleri (Etkinleştir ve Eylem) tarafından kötü amaçlı yazılım Kasa _e-posta_ _iletileri_</li><li>E-posta, OneDrive ve [Kasa Ekleri SharePoint tarafından kötü amaçlı yazılım olarak karantinaya Microsoft Teams](mdo-for-spo-odb-and-teams.md)</li></ul>|<ul><li>Evet</li><li>Hayır</li></ul>|<ul><li>AdminOnlyAccessPolicy (erişim yok)</li><li>yok</li></ul>|
|[Eylemle birlikte](/exchange/security-and-compliance/mail-flow-rules/mail-flow-rules) posta akışı kuralları (aktarım kuralları olarak da bilinir): **İletiyi** barındırılan karantinaya (Karantina) _teslim._|Hayır|yok|

<sup>\*</sup> Bu [makalede daha önce açıklandığı gibi](#full-access-permissions-and-quarantine-notifications), kuruluşta DefaultFullAccessPolicy yerine NotificationEnabledPolicy kullanılabilir. Bu iki karantina ilkeleri arasındaki tek fark, NotificationEnabledPolicy'de karantina bildirimlerinin açılabilir ve DefaultFullAccessPolicy'de kapatılabilir.

Varsayılan karantina ilkeleri, önceden ayarlanmış izin grupları ve izinler bu makalenin başında ve sonraki [makalesinde açıklanmıştır](#preset-permissions-groups).[](#quarantine-policies)

> [!NOTE]
> Varsayılan karantina ilkeleri tarafından sağlanan (veya sağlanmaz) varsayılan son kullanıcı izinlerini ve karantina bildirimlerini memnunsanız, bir şey yapmaya gerek yok. Kullanıcı karantinaya alınmış iletiler için son kullanıcı özellikleri (kullanılabilir düğmeler) eklemek veya kaldırmak ya da karantina bildirimlerini etkinleştirmek ve karantina bildirimlerine aynı özellikleri eklemek veya kaldırmak için, karantina eylemine farklı bir karantina ilkesi atabilirsiniz.

## <a name="assign-quarantine-policies-in-supported-policies-in-the-microsoft-365-defender-portal"></a>Microsoft 365 Defender portalında desteklenen ilkelerde karantina ilkeleri atama

### <a name="anti-spam-policies"></a>İstenmeyen posta önleme ilkeleri

1. Microsoft 365 Defender [portalında](https://security.microsoft.com), İlkeler **bölümünde** \> E-& işbirliği **& kuralları** \> \> Tehdit ilkeleri **İstenmeyen** postayla mücadele **bölümüne** gidin.

   Veya doğrudan **ant-spam ilkeleri sayfasına gitmek için** , kullanın <https://security.microsoft.com/antispam>.

2. **İstenmeyen posta önleme ilkeleri** sayfasında, aşağıdaki adımlardan birini uygulayın:
   - Var olan bir istenmeyen posta **önleme ilkesi bulun** ve seçin.
   - Yeni bir istenmeyen **posta önleme** ilkesi oluşturun.

3. Aşağıdaki adımlardan birini yapın:
   - **Var olanı** düzenle: İlkenin adına tıklayarak ilkeyi seçin. İlke ayrıntıları uç bilgisinde Eylemler bölümüne **gidin ve Eylemleri** **düzenle'ye tıklayın**.
   - **Yeni oluştur**: Yeni ilke sihirbazında Eylemler **sayfasına** gidin.

4. Eylemler **sayfasında**, Karantina ileti eylemine sahip olan her  kararda, ilgili karantina ilkesi seçmeniz  için Karantinayı seç ilke kutusu da olur.

   **Not**: Yeni bir ilke seniz, boş bir Karantina ilkesi  seçin değeri, bu karar için varsayılan karantina ilkesi olduğunu gösterir. İlkeyi daha sonra düzenleyseniz, boş değerlerin yerini önceki tabloda açıklandığı gibi asıl varsayılan karantina ilkesi adları alır.

   ![İstenmeyen posta önleme ilkesinde ilke seçimlerini karantinaya alın.](../../media/quarantine-tags-in-anti-spam-policies.png)

İstenmeyen posta önleme ilkelerini oluşturma ve değiştirme yönergelerinin tam yönergeleri [EOP'de istenmeyen posta önleme ilkelerini yapılandırma konusunda açıklanmıştır](configure-your-spam-filter-policies.md).

#### <a name="anti-spam-policies-in-powershell"></a>PowerShell'de istenmeyen posta önleme ilkeleri

İstenmeyen posta önleme ilkelerde karantina ilkeleri atamak için PowerShell kullanmayı tercih ediyorsanız, Exchange Online PowerShell'e veya PowerShell'Exchange Online Protection aşağıdaki söz dizimlerini kullanın:

```powershell
<New-HostedContentFilterPolicy -Name "<Unique name>" | Set-HostedContentFilterPolicy -Identity "<Policy name>"> [-SpamAction Quarantine] [-SpamQuarantineTag <QuarantineTagName>] [-HighConfidenceSpamAction Quarantine] [-HighConfidenceSpamQuarantineTag <QuarantineTagName>] [-PhishSpamAction Quarantine] [-PhishQuarantineTag <QuarantineTagName>] [-HighConfidencePhishQuarantineTag <QuarantineTagName>] [-BulkSpamAction Quarantine] [-BulkQuarantineTag <QuarantineTagName>] ...
```

**Notlar**:

- _PhishSpamAction_ ve _HighConfidencePhishAction_ parametrelerinin varsayılan değeri Karantina'dır, dolayısıyla PowerShell'de yeni istenmeyen posta filtresi ilkeleri irken bu parametreleri kullanmak zorunda değildir. Yeni veya var olan istenmeyen posta önleme ilkeleri içinde _SpamAction_, _HighConfidenceSpamAction_ ve _BulkSpamAction_ parametrelerinde, karantina ilkesi ancak değer Karantina ise geçerli olur.

  Var olan istenmeyen posta önleme ilkelerde önemli parametre değerlerini görmek için, aşağıdaki komutu çalıştırın:

  ```powershell
  Get-HostedContentFilterPolicy | Format-List Name,*SpamAction,HighConfidencePhishAction,*QuarantineTag
  ```

  Varsayılan eylem değerleri ve Standart ve Katı için önerilen eylem değerleri hakkında bilgi için bkz. [EOP istenmeyen posta önleme ilkesi ayarları](recommended-settings-for-eop-and-office365.md#eop-anti-spam-policy-settings).

- Yeni istenmeyen posta önleme ilkeleri musunuz? İstenmeyen posta filtreleme kararını ilgili karantina ilkesi parametresi olmadan almak, bu karar [](#step-2-assign-a-quarantine-policy-to-supported-features) için varsayılan karantina ilkesi anlamına gelir.

  Yalnızca, belirli istenmeyen posta filtreleme kararının karantinaya alınmış iletilerde varsayılan son kullanıcı özelliklerini değiştirmek istemeniz gerekir.

- PowerShell'de yeni istenmeyen posta önleme ilkesi **, New-HostedContentFilterPolicy cmdlet'ini ve New-HostedContentFilterRule** cmdlet'ini kullanan bir istenmeyen posta filtresi ilkesi (ayarlar) ve **new-HostedContentFilterRule** cmdlet'ini kullanarak özel kullanım istenmeyen posta filtresi kuralı (alıcı filtreleri) gerektirir. Yönergeler için bkz [. PowerShell kullanarak istenmeyen posta önleme ilkeleri oluşturma](configure-your-spam-filter-policies.md#use-powershell-to-create-anti-spam-policies).

Bu örnekte, Research Department adlı yeni bir istenmeyen posta filtresi ilkesi aşağıdaki ayarlarla oluşturur:

- Tüm istenmeyen posta filtreleme kararlarını içeren eylem Karantina'ya ayarlanır.
- Hiçbir erişim izni atamamış olan NoAccess adlı özel  karantina ilkesi, varsayılan olarak Erişim izni yok atamayacağınız tüm varsayılan **karantina ilkelerinin** yerini almaktadır.

```powershell
New-HostedContentFilterPolicy -Name "Research Department" -SpamAction Quarantine -SpamQuarantineTag NoAccess -HighConfidenceSpamAction Quarantine -HighConfidenceSpamQuarantineTag NoAction -PhishSpamAction Quarantine -PhishQuarantineTag NoAction -BulkSpamAction Quarantine -BulkQuarantineTag NoAccess
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [New-HostedContentFilterPolicy](/powershell/module/exchange/new-hostedcontentfilterpolicy).

Bu örnekte, İnsan Kaynakları adlı mevcut istenmeyen posta filtresi ilkesinde değişiklik yapılan bir değişiklik vardır. İstenmeyen posta karantina kararının eylemi Karantina olarak ayarlanır ve NoAccess adlı özel karantina ilkesi atanır.

```powershell
Set-HostedContentFilterPolicy -Identity "Human Resources" -SpamAction Quarantine -SpamQuarantineTag NoAccess
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [Set-HostedContentFilterPolicy](/powershell/module/exchange/set-hostedcontentfilterpolicy).

### <a name="anti-phishing-policies"></a>Kimlik avı önleme ilkeleri

Spoof Intelligence, EOP ve Defender'da akıllı Office 365. Kullanıcı kimliğe bürünme koruması, etki alanı kimliğe bürünme koruması ve posta kutusu zekası özellikleri yalnızca Office 365. Daha fazla bilgi için bkz[. Kimlik avıyla mücadele ilkeleri Microsoft 365](set-up-anti-phishing-policies.md).

1. Microsoft 365 Defender [portalında, İlkeler](https://security.microsoft.com) bölümünde **E-&** \> işbirliği **& kuralları** \>  \> Tehdit ilkeleri **Kimlik** avıyla **mücadele bölümüne** gidin.

   Veya doğrudan **ant-spam ilkeleri sayfasına gitmek için** , kullanın <https://security.microsoft.com/antiphishing>.

2. Kimlik **avı önleme sayfasında** , aşağıdaki adımlardan birini uygulayın:
   - Var olan kimlik avı önleme ilkesi bulun ve seçin.
   - Yeni bir kimlik avı önleme ilkesi oluşturun.

3. Aşağıdaki adımlardan birini yapın:
   - **Var olanı** düzenle: İlkenin adına tıklayarak ilkeyi seçin. İlke ayrıntıları sayfasında Koruma ayarları bölümüne **gidin ve Koruma** ayarlarını **düzenle'ye tıklayın**.
   - **Yeni oluştur**: Yeni ilke sihirbazında Eylemler **sayfasına** gidin.

4. Koruma **ayarları sayfasında** , aşağıdaki ayarların gerekli şekilde açık ve yapılandırılmış olduğunu doğrulayın:
   - **Kullanıcıların korunması etkinleştirildi**: Kullanıcıları belirtin.
   - **Korumak için etki alanları etkinleştirildi**: Sahibim olan etki **alanlarını dahil edin ve** /veya Özel etki **alanlarını dahil** edin'i seçin ve etki alanlarını belirtin.
   - **Posta kutusu zekası etkinleştirme**
   - **Kimliğe bürünme koruması için zekayı etkinleştirme**
   - **Akıllı ifadeyi etkinleştirme**

5. Aşağıdaki adımlardan birini yapın:
   - **Var olanı** düzenle: İlke ayrıntılarında, Eylemler bölümüne **gidin ve eylemleri** **düzenle'ye tıklayın**.
   - **Yeni oluştur**: Yeni ilke sihirbazında Eylemler **sayfasına** gidin.

6. Eylemler **sayfasında**, İletiyi karantinaya alın eylemine  sahip olan her kararda, ilgili karantina  ilkesi seçmeniz için Karantinaya uygula ilkesi kutusu da olur.

   **Not**: Yeni bir ilke seniz, boş bir Karantina **ilkesi** uygula değeri, bu eylemin varsayılan karantina ilkesi kullanılır olduğunu gösterir. İlkeyi daha sonra düzenleyseniz, boş değerlerin yerini önceki tabloda açıklandığı gibi asıl varsayılan karantina ilkesi adları alır.

   ![Kimlik avı önleme ilkesinde ilke seçimlerini karantinaya alın.](../../media/quarantine-tags-in-anti-phishing-policies.png)

Kimlik avı önleme ilkelerini oluşturmaya ve değiştirmeye yönelik tüm yönergeler aşağıdaki konulardan edinebilirsiniz:

- [EOP'de kimlik avı önleme ilkelerini yapılandırma](configure-anti-phishing-policies-eop.md)
- [Kimlik avıyla mücadele ilkelerini Microsoft Defender'da Office 365](configure-mdo-anti-phishing-policies.md)

#### <a name="anti-phishing-policies-in-powershell"></a>PowerShell'de kimlik avı önleme ilkeleri

Kimlik avı koruma ilkeleri içinde karantina ilkeleri atamak için PowerShell kullanmayı tercih ediyorsanız, powershell veya Exchange Online PowerShell'Exchange Online Protection aşağıdaki söz dizimlerini kullanın:

```powershell
<New-AntiPhishPolicy -Name "<Unique name>" | Set-AntiPhishPolicy -Identity "<Policy name>"> [-EnableSpoofIntelligence $true] [-AuthenticationFailAction Quarantine] [-SpoofQuarantineTag <QuarantineTagName>] [-EnableMailboxIntelligence $true] [-EnableMailboxIntelligenceProtection $true] [-MailboxIntelligenceProtectionAction Quarantine] [-MailboxIntelligenceQuarantineTag <QuarantineTagName>] [-EnableOrganizationDomainsProtection $true] [-EnableTargetedDomainsProtection $true] [-TargetedDomainProtectionAction Quarantine] [-TargetedDomainQuarantineTag <QuarantineTagName>] [-EnableTargetedUserProtection $true] [-TargetedUserProtectionAction Quarantine] [-TargetedUserQuarantineTag <QuarantineTagName>] ...
```

**Notlar**:

- Belirli _koruma\*_ özelliklerini açmak için Etkinleştir parametreleri gereklidir. _EnableMailboxIntelligence_ ve _EnableSpoofIntelligence_ parametreleri için varsayılan değer $true'dir, dolayısıyla PowerShell'de yeni kimlik avı ilkeleri irken bu parametreleri kullanmak zorunda değildir. Diğer tüm _Etkinleştir\*_ parametrelerinde, karantina ilkesi $true _\*_ için ilgili Eylem parametrelerinde Karantina değerini ayarlay seçeneği etkin olmalıdır. _*\Action parametrelerinin hiçbirinin_ varsayılan değeri Karantina'dır.

  Var olan kimlik avı önleme ilkelerde önemli parametre değerlerini görmek için aşağıdaki komutu çalıştırın:

  ```powershell
  Get-AntiPhishPolicy | Format-List Name,Enable*Intelligence,Enable*Protection,*Action,*QuarantineTag
  ```

  Varsayılan eylem değerleri ve Standart ve Katı için önerilen eylem değerleri hakkında bilgi için, Office 365 için [Microsoft Defender'da](recommended-settings-for-eop-and-office365.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365), kimlik avı önleme ilkelerinde [EOP](recommended-settings-for-eop-and-office365.md#eop-anti-phishing-policy-settings) kimlik avı koruma ilkesi ayarları ve Kimlik avı önleme ilkelerine kimliğe bürünme ayarları Office 365.

- Kimlik avı önleme ilkeleri seniz, ilgili karantina ilkesi parametresine sahip olmayan kimlik avı önleme eylemi, karar için varsayılan karantina ilkesi [](#step-2-assign-a-quarantine-policy-to-supported-features) anlamına gelir.

  Yalnızca, belirli bir karara göre karantinaya alınmış iletilerde varsayılan son kullanıcı özelliklerini değiştirmek istemeniz gerekirse, varsayılan karantina ilkesiyle değiştirmeniz gerekir.

- PowerShell'de yeni kimlik avı önleme ilkesi, **New-AntiPhishPolicy** cmdlet'ini ve **New-AntiPhishRule** cmdlet'ini kullanan özel bir kimlik avı önleme kuralı (alıcı filtreleri) gerektirir. Yönergeler için aşağıdaki konulara bakın:
  - [EOP'de kimlik avı önleme ilkelerini yapılandırmak için PowerShell kullanma](configure-anti-phishing-policies-eop.md#use-exchange-online-powershell-to-configure-anti-phishing-policies)
  - [Kimlik Exchange Online ilkelerini yapılandırmak için PowerShell'i kullanma](configure-mdo-anti-phishing-policies.md#use-exchange-online-powershell-to-configure-anti-phishing-policies)

Bu örnek, aşağıdaki ayarların yer alan Araştırma Bölümü adlı yeni bir kimlik avı önleme ilkesi oluşturur:

- Tüm istenmeyen posta filtreleme kararlarını içeren eylem Karantina'ya ayarlanır.
- Hiçbir erişim izni atamamış olan NoAccess adlı özel  karantina ilkesi, varsayılan olarak Erişim izni yok atamayacağınız tüm varsayılan **karantina ilkelerinin** yerini almaktadır.

```powershell
New-AntiPhishPolicy -Name "Research Department" -AuthenticationFailAction Quarantine -SpoofQuarantineTag NoAccess -EnableMailboxIntelligenceProtection $true -MailboxIntelligenceProtectionAction Quarantine -MailboxIntelligenceQuarantineTag NoAccess -EnableOrganizationDomainsProtection $true -EnableTargetedDomainsProtection $true -TargetedDomainProtectionAction Quarantine -TargetedDomainQuarantineTag NoAccess -EnableTargetedUserProtection $true -TargetedUserProtectionAction Quarantine -TargetedUserQuarantineTag NoAccess
```

Ayrıntılı söz dizimi ve parametre bilgileri için [bkz. New-AntiPhishPolicy](/powershell/module/exchange/new-antiphishpolicy).

Bu örnekte, İnsan Kaynakları adlı mevcut kimlik avı koruma ilkesinde değişiklik yapılan bir durumla karşıtlık vardır. Kullanıcı kimliğe bürünme ve etki alanı kimliğine bürünme tarafından algılanan iletiler için eylem Karantina olarak ayarlanır ve NoAccess adlı özel karantina ilkesi atanır.

```powershell
Set-AntiPhishPolicy -Identity "Human Resources" -EnableTargetedDomainsProtection $true -TargetedDomainProtectionAction Quarantine -TargetedDomainQuarantineTag NoAccess -EnableTargetedUserProtection $true -TargetedUserProtectionAction Quarantine -TargetedUserQuarantineTag NoAccess
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [AntiPhishPolicy Ayarlama](/powershell/module/exchange/set-antiphishpolicy).

### <a name="anti-malware-policies"></a>Kötü amaçlı yazılımdan koruma ilkeleri

1.  Microsoft 365 Defender [portalında](https://security.microsoft.com), İlkeler bölümünde **E-posta &** \> işbirliği **& kuralları** \> \> İlkeler bölümünde Tehdit ilkeleri **Kötü** amaçlı yazılımdan koruma **ilkeleri'ne** gidin.

   Ya da doğrudan Kötü amaçlı yazılımdan **koruma sayfasına** gitmek için kullanın <https://security.microsoft.com/antimalwarev2>.

2. Kötü **amaçlı yazılımdan koruma** sayfasında, aşağıdaki adımlardan birini uygulayın:
   - Var olan kötü amaçlı yazılımdan koruma ilkesi bulun ve seçin.
   - Yeni kötü amaçlı yazılımdan koruma ilkesi oluşturun.

3. Aşağıdaki adımlardan birini yapın:
   - **Var olanı** düzenle: İlkenin adına tıklayarak ilkeyi seçin. İlke ayrıntıları sayfasında Koruma ayarları bölümüne **gidin ve Koruma** ayarlarını **düzenle'ye tıklayın**.
   - **Yeni oluştur**: Yeni ilke sihirbazında Eylemler **sayfasına** gidin.

4. Koruma ayarları **sayfasında** , Karantina ilkesi kutusunda bir karantina **ilkesi** seçin.

   **Not**: Yeni bir ilke oluşturmada, boş bir **Karantina ilkesi** değeri, kullanılan varsayılan karantina ilkesine işaret verir. İlkeyi daha sonra düzenleyseniz, boş değerin yerini, önceki tabloda açıklandığı gibi asıl varsayılan karantina ilkesi adı alır.

#### <a name="anti-malware-policies-in-powershell"></a>PowerShell'de kötü amaçlı yazılımdan koruma ilkeleri

Kötü amaçlı yazılımdan koruma ilkeleri atamak için PowerShell kullanmayı tercih ediyorsanız, powershell veya Exchange Online PowerShell'e bağlanın Exchange Online Protection söz dizimi kullanın:

```powershell
<New-AntiMalwarePolicy -Name "<Unique name>" | Set-AntiMalwarePolicy -Identity "<Policy name>"> [-QuarantineTag <QuarantineTagName>]
```

**Notlar**:

- Yeni bir kötü amaçlı yazılımdan koruma ilkesi  oluştururken KarantinaTag parametresini kullanmadan yeni kötü amaçlı yazılımdan koruma ilkeleri  oluşturursanız, kötü amaçlı yazılım algılamaları için varsayılan karantina ilkesi kullanılır (AdminOnlyAccessPolicy).

  Yalnızca kötü amaçlı yazılım olarak karantinaya alınmış iletilerde varsayılan son kullanıcı özelliklerini değiştirmek istiyorsanız, varsayılan karantina ilkesiyle özel karantina ilkesiyle değiştirmeniz gerekir.

  Var olan kimlik avı önleme ilkelerde önemli parametre değerlerini görmek için aşağıdaki komutu çalıştırın:

  ```powershell
  Get-MalwareFilterPolicy | Format-Table Name,QuarantineTag
  ```

- PowerShell'de yeni kötü amaçlı yazılımdan koruma ilkesi, **New-MalwareFilterPolicy** cmdlet'ini ve **New-MalwareFilterRule** cmdlet'ini kullanarak özel amaçlı yazılım filtresi kuralı (alıcı filtreleri) kullanan bir kötü amaçlı yazılım filtresi ilkesi (ayarlar) gerektirir. Yönergeler için bkz. [Kötü amaçlı Exchange Online koruma ilkelerini yapılandırmak için PowerShell veya tek başına EOP PowerShell kullanma](configure-anti-malware-policies.md#use-exchange-online-powershell-or-standalone-eop-powershell-to-configure-anti-malware-policies).

Bu örnek, Karantinaya alınan iletilere Erişim izni yok ataan NoAccess adlı özel karantina ilkesi kullanan Araştırma Bölümü  adlı bir kötü amaçlı yazılım filtresi ilkesi oluşturur.

```powershell
New-MalwareFilterPolicy -Name "Research Department" -QuarantineTag NoAccess
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [New-MalwareFilterPolicy](/powershell/module/exchange/new-malwarefilterpolicy).

Bu örnekte, karantinaya alınan iletilere Erişim izni yok ataan NoAccess adlı özel karantina ilkesi atanarak İnsan Kaynakları adlı var olan  kötü amaçlı yazılım filtresi ilkesinde değişiklik olur.

```powershell
New-MalwareFilterPolicy -Identity "Human Resources" -QuarantineTag NoAccess
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [Set-MalwareFilterPolicy](/powershell/module/exchange/set-malwarefilterpolicy).

### <a name="safe-attachments-policies-in-defender-for-office-365"></a>Kasa için Defender'da Ekleri Office 365

1. Microsoft 365 Defender [portalında](https://security.microsoft.com), İlkeler bölümünde **E-posta &** \> işbirliği **& kuralları** \>  \> Tehdit **Kasa ekleri** **gönderme bölümüne** gidin.

   Ya da doğrudan Ekler Kasa **gitmek** için kullanın<https://security.microsoft.com/safeattachmentv2>.

2. Ekleri **Kasa** sayfasında, aşağıdaki adımlardan birini uygulayın:
   - Mevcut E-posta Ekleri Kasa bulun ve seçin.
   - Ekler ilkesi Kasa oluşturun.

3. Aşağıdaki adımlardan birini yapın:
   - **Var olanı** düzenle: İlkenin adına tıklayarak ilkeyi seçin. İlke ayrıntıları uç sayfasında, Ayrıntılar bölümüne **Ayarlar** Ayarları **düzenle'ye tıklayın**.
   - **Yeni oluştur**: Yeni ilke sihirbazında, İlke ve **Ayarlar** gidin.

4. Sayfa **Ayarlar** aşağıdaki adımları uygulayın:
   1. **Kasa bilinmeyen kötü amaçlı yazılım yanıtı**: Engelle, Değiştir **veya** **Dinamik Teslim'i** **seçin**.
   2. Karantina ilkesi kutusunda bir karantina **ilkesi** seçin.

   **Not**: Yeni bir ilke seniz, boş bir **Karantina ilkesi değeri** varsayılan karantina ilkesi kullanılır. İlkeyi daha sonra düzenleyseniz, boş değerin yerini, önceki tabloda açıklandığı gibi asıl varsayılan karantina ilkesi adı alır.

Ekleri oluşturma ve değiştirme Kasa tam yönergeler, Kasa için Microsoft Defender'da Ekler ilkelerini [ayarlama makalesinde Office 365](set-up-safe-attachments-policies.md).

#### <a name="safe-attachments-policies-in-powershell"></a>Kasa PowerShell'de Ekleri Kaydetme

Kasa Ekler ilkeleri içinde karantina ilkeleri atamak için PowerShell kullanmayı tercih ediyorsanız, Exchange Online PowerShell veya Exchange Online Protection PowerShell'e bağlanın ve aşağıdaki söz dizimlerini kullanın:

```powershell
<New-SafeAttachmentPolicy -Name "<Unique name>" | Set-SafeAttachmentPolicy -Identity "<Policy name>"> -Enable $true -Action <Block | Replace | DynamicDelivery> [-QuarantineTag <QuarantineTagName>]
```

**Notlar**:

- Action _parametresi_ değerleri Engelle, Değiştir veya DinamikDelivery karantinaya alınmış iletilere neden olabilir (İzin Ver değeri iletileri karantinaya vermez). Action parametresinin _anlamlı_ olan değeri yalnızca _Enable parametresinin değeri_ şu olduğunda `$true`: .

- QuarantineTag parametresini kullanmadan Kasa Attachments ilkeleri seniz, e-postada Kasa Ekleri algılamaları için varsayılan karantina ilkesi kullanılır (AdminOnlyAccessPolicy).

  Yalnızca, Ek ilkeleri tarafından karantinaya alınmış e-posta iletilerde varsayılan son kullanıcı özelliklerini değiştirmek için, varsayılan karantina Kasa değiştirmelisiniz.

  Önemli parametre değerlerini görmek için aşağıdaki komutu çalıştırın:

  ```powershell
  Get-SafeAttachmentPolicy | Format-List Name,Enable,Action,QuarantineTag
  ```

- Yeni bir Kasa PowerShell Ekleri ilkesi için **New-SafeAttachmentPolicy** cmdlet'ini ve **New-SafeAttachmentRule** cmdlet'ini kullanarak özel bir güvenli ek kuralı (alıcı filtreleri) gerekir. Yönergeler için bkz. Exchange Online ek ilkelerini yapılandırmak [için PowerShell veya tek başına EOP PowerShell Kasa kullanma](set-up-safe-attachments-policies.md#use-exchange-online-powershell-or-standalone-eop-powershell-to-configure-safe-attachments-policies).

Bu örnek, algılanan iletileri engelleyen ve karantinaya alınan iletilere Erişim yok izinleri ataan NoAccess adlı özel karantina ilkesi kullanan Araştırma Bölümü adlı  güvenli bir ek ilkesi oluşturur.

```powershell
New-SafeAttachmentPolicy -Name "Research Department" -Enable $true -Action Block -QuarantineTag NoAccess
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [New-MalwareFilterPolicy](/powershell/module/exchange/new-malwarefilterpolicy).

Bu örnekte, Erişim izni yok ataan NoAccess adlı özel karantina ilkesi atanarak, İnsan Kaynakları adlı mevcut güvenli ek **ilkesinde değişiklik** olur.

```powershell
Set-SafeAttachmentPolicy -Identity "Human Resources" -QuarantineTag NoAccess
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [Set-MalwareFilterPolicy](/powershell/module/exchange/set-malwarefilterpolicy).

## <a name="configure-global-quarantine-notification-settings-in-the-microsoft-365-defender-portal"></a>E-posta portalında genel karantina Microsoft 365 Defender yapılandırma

Karantina ilkelerinin genel ayarları, karantina ilkesinde karantina bildirimleri açıksa, karantina iletileri alıcılarına gönderilen karantina bildirimlerini özelleştirmenize olanak sağlar. Bu bildirimler hakkında daha fazla bilgi için bkz. [Bildirimleri karantinaya alındı.](use-spam-notifications-to-release-and-report-quarantined-messages.md)

1. Microsoft 365 Defender portalında, Kurallar bölümündeki **&-posta** \> ve **& ilkeleri** \>  \> Karantina  **ilkeleri'ne** gidin.

2. Karantina ilkesi **sayfasında Genel** **ayarlar'ı seçin**.

3. Açılan **Karantina bildirim ayarları** açılır sayfasında, aşağıdaki ayarların bir birini veya hepsini yapılandırabilirsiniz:

   - **Görünen ad**: Gönderenin karantina bildirimlerde kullanılan görünen adını özelleştirin.

     Ekley istediğiniz her dil için, ikinci dil kutusunda dili seçin (X'e tıklayın) ve Görünen ad kutusuna istediğiniz **metin değerini** girin.

     Aşağıdaki ekran görüntüsünde, karantina bildiriminde özelleştirilmiş görünen ad gösterilir:

     ![Karantina bildiriminde özelleştirilmiş bir gönderen görünen adı.](../../media/quarantine-tags-esn-customization-display-name.png)

   - **Bildirim:** Karantina bildirimlerinin en altına özel bir bildirim ekleyin. Yerelleştirilmiş metin **(Bir kuruluştan uyarı:** her zaman önce yer alan ve sizin belirttiğiniz metinden sonra gelen uyarıdır).

     Ekley istediğiniz her dil için, ikinci dil kutusunda dili seçin (X'e tıklayın) ve Yasal Uyarı kutusuna **istediğiniz metin değerini** girin.

     Aşağıdaki ekran görüntüsü, karantina bildiriminde özelleştirilmiş bildirimi gösterir:

     ![Karantina bildiriminin en altında özel bir bildirim.](../../media/quarantine-tags-esn-customization-disclaimer.png)

   - **Dili seçin**: Karantina bildirimleri, alıcının dil ayarlarına göre yerelleştirilmiştir. Görünen ad ve Yasal Uyarı değerleri için farklı dillerde **özelleştirilmiş** **metinler belirtebilirsiniz** .

     İlk dil kutusundan en az bir dil seçin ve Ekle'ye **tıklayın**. Her dilin ardından Ekle'ye tıklayarak **birden çok** dil seçin. Bölüm dili kutusunda seçtiğiniz tüm diller görüntülenir:

     ![Karantina ilkelerinin genel karantina bildirimi ayarlarında ikinci dil kutusunda seçilen diller.](../../media/quarantine-tags-esn-customization-selected-languages.png)

   - **Şirket logosunu kullan**: Karantina bildirimlerinin en üstünde kullanılan varsayılan Microsoft logosunu değiştirmek için bu seçeneği belirtin. Bunu yapmak için, Özel logonuzu yüklemek üzere Microsoft 365 için Özel [tema'da](../../admin/setup/customize-your-organization-theme.md) verilen yönergeleri izleyebilirsiniz.

     Aşağıdaki ekran görüntüsünde karantina bildiriminde özel bir logo yer alır:

     ![Karantina bildiriminde özel bir logo.](../../media/quarantine-tags-esn-customization-logo.png)

   - **Son kullanıcı istenmeyen posta bildirimi gönderme sıklığı (gün)**: Karantina bildirimleri için sıklığı seçin.

## <a name="view-quarantine-policies-in-the-microsoft-365-defender-portal"></a>Microsoft 365 Defender portalında karantina Microsoft 365 Defender görüntüleme

1. Microsoft 365 Defender portalında, Kurallar bölümündeki **&-posta** \> ve **& ilkeleri** \>  \> Karantina  **ilkeleri'ne** gidin.

2. Karantina **ilkesi sayfasında** , Ad ve Son güncelleştirme **tarihine göre** **ilkeler listesi** görüntülenir.

3. Yerleşik veya özel karantina ilkelerinin ayarlarını görüntülemek için, adı tıklatarak listeden karantina ilkesi seçin.

4. Genel ayarları görüntülemek için Genel **ayarlar'a tıklayın**.

### <a name="view-quarantine-policies-in-powershell"></a>PowerShell'de karantina ilkelerini görüntüleme

Karantina ilkelerini görüntülemek için PowerShell kullanmayı tercih ediyorsanız, aşağıdaki adımlardan birini uygulayın:

- Tüm yerleşik veya özel ilkelerin özet listesini görüntülemek için, aşağıdaki komutu çalıştırın:

  ```powershell
  Get-QuarantinePolicy | Format-Table Name
  ```

- Yerleşik veya özel karantina ilkelerinin ayarlarını görüntülemek için, \<QuarantinePolicyName\> karantina ilkesi adıyla değiştirin ve aşağıdaki komutu çalıştırın:

  ```powershell
  Get-QuarantinePolicy -Identity "<QuarantinePolicyName>"
  ```

- Karantina bildirimlerinin genel ayarlarını görüntülemek için aşağıdaki komutu çalıştırın:

  ```powershell
  Get-QuarantinePolicy -QuarantinePolicyType GlobalQuarantinePolicy
  ```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [Get-HostedContentFilterPolicy](/powershell/module/exchange/get-hostedcontentfilterpolicy).

## <a name="modify-quarantine-policies-in-the-microsoft-365-defender-portal"></a>Microsoft 365 Defender portalında karantina Microsoft 365 Defender değiştirme

AdminOnlyAccessPolicy veya DefaultFullAccessPolicy adlı yerleşik karantina ilkelerini değiştiremezsiniz. NotificationEnabledPolicy (varsa) adlı yerleşik [ilkeyi ve özel](#full-access-permissions-and-quarantine-notifications) karantina ilkelerini değiştirebilirsiniz.

1. Microsoft 365 Defender portalında, Kurallar bölümündeki **&-posta** \> ve **& ilkeleri** \>  \> Karantina  **ilkeleri'ne** gidin.

2. Karantina **ilkeleri sayfasında** , adına tıklayarak ilkeyi seçin.

3. İlkeyi seçdikten sonra İlkeyi düzenle ![simgesine tıklayın.](../../media/m365-cc-sc-edit-icon.png) **Görüntülenen İlkeyi** düzenle simgesi.

4. Açılan **İlkeyi** düzenle sihirbazı, bu makalenin önceki  kısımlarında yer alan Microsoft 365 Defender [portalında](#step-1-create-quarantine-policies-in-the-microsoft-365-defender-portal) karantina ilkeleri oluşturma bölümünde açıklanan Yeni ilke sihirbazıyla hemen hemen aynıdır.

   En önemli fark, mevcut bir ilkeyi yeniden adlandırılamaz.

5. İlkeyi değiştirmeyi bitirdikten sonra, Özet sayfasına gidin **ve** Gönder'e **tıklayın**.

### <a name="modify-quarantine-policies-in-powershell"></a>PowerShell'de karantina ilkelerini değiştirme

Özel karantina ilkesinde değişiklik yapmak için PowerShell kullanmayı tercih ediyorsanız, \<QuarantinePolicyName\> karantina ilkesi adıyla değiştirin ve aşağıdaki söz dizimlerini kullanın:

```powershell
Set-QuarantinePolicy -Identity "<QuarantinePolicyName>" [Settings]
```

Kullanılabilir ayarlar, bu makalenin önceki sayfalarında açıklanan karantina ilkelerini oluşturmada açıklananla aynıdır.

Ayrıntılı söz dizimi ve parametre bilgileri için bkz [. Set-QuarantinePolicy](/powershell/module/exchange/set-quarantinepolicy).

## <a name="remove-quarantine-policies-in-the-microsoft-365-defender-portal"></a>E-Microsoft 365 Defender portalında karantina Microsoft 365 Defender kaldırma

**Notlar**:

- AdminOnlyAccessPolicy veya DefaultFullAccessPolicy adlı yerleşik karantina ilkelerini kaldırasınız. NotificationEnabledPolicy (varsa) adlı yerleşik ilkeyi [ve özel karantina](#full-access-permissions-and-quarantine-notifications) ilkelerini kaldıramazsınız.
- Karantina ilkesi kaldırmadan önce, kullan olmadığını doğrulayın. Örneğin, PowerShell'de aşağıdaki komutu çalıştırın:

  ```powershell
  Write-Output -InputObject "Anti-spam policies","----------------------";Get-HostedContentFilterPolicy | Format-List Name,*QuarantineTag; Write-Output -InputObject "Anti-phishing policies","----------------------";Get-AntiPhishPolicy | Format-List Name,*QuarantineTag; Write-Output -InputObject "Anti-malware policies","----------------------";Get-MalwareFilterPolicy | Format-List Name,QuarantineTag; Write-Output -InputObject "Safe Attachments policies","---------------------------";Get-SafeAttachmentPolicy | Format-List Name,QuarantineTag
  ```

  Karantina ilkesi kullanılıyorsa, [kaldırmadan önce atanmış karantina](#step-2-assign-a-quarantine-policy-to-supported-features) ilkesiyle değiştirin.

1. Microsoft 365 Defender portalında, Kurallar bölümündeki **&-posta** \> ve **& ilkeleri** \>  \> Karantina  **ilkeleri'ne** gidin.

2. Karantina **ilkesi sayfasında** , adına tıklayarak kaldırmak istediğiniz özel karantina ilkesine tıklayın.

3. İlkeyi seçin ve ardından İlkeyi sil ![simgesine tıklayın.](../../media/m365-cc-sc-delete-icon.png) **Görüntülenen İlkeyi** sil simgesi.

4. Görüntülenen **onay iletişim kutusunda** İlkeyi kaldır'a tıklayın.

### <a name="remove-quarantine-policies-in-powershell"></a>PowerShell'de karantina ilkelerini kaldırma

Özel karantina ilkesi kaldırmak için PowerShell kullanmayı tercih ediyorsanız, \<QuarantinePolicyName\> karantina ilkesi adıyla değiştirin ve aşağıdaki komutu çalıştırın:

```powershell
Remove-QuarantinePolicy -Identity "<QuarantinePolicyName>"
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz [. Remove-QuarantinePolicy](/powershell/module/exchange/remove-quarantinepolicy).

## <a name="system-alerts-for-quarantine-release-requests"></a>Karantina sürüm istekleri için sistem uyarıları

Varsayılan olarak, Kullanıcı karantinaya alınmış iletiyi  serbest bırakmak için istekte bulundu varsayılan uyarı ilkesi, otomatik olarak bir bilgilendirme uyarısı üretir ve kullanıcı karantinaya alınmış iletinin serbest bırak alınmasını her isteğinde olduğunda aşağıdaki rol gruplarının üyelerine bildirim iletileri gönderir:

- Karantina Yöneticisi
- Güvenlik Yöneticisi
- Kuruluş Yönetimi (genel yönetici)

Yöneticiler e-posta bildirimi alıcılarını özelleştirilebilir veya daha fazla seçenek için özel bir uyarı ilkesi oluşturabilir.

Uyarı ilkeleri hakkında daha fazla bilgi için bkz[. İlke ve Microsoft 365](../../compliance/alert-policies.md).

## <a name="quarantine-policy-permission-details"></a>Karantina ilkesi izin ayrıntıları

Aşağıdaki bölümlerde, önceden ayarlanmış izin gruplarının ve karantinaya alınmış iletilerin ayrıntılarında ve karantina bildirimlerinin tek tek izinleri açıklanmaktadır.

### <a name="preset-permissions-groups"></a>Önceden ayarlanmış izin grupları

Önceden ayarlanmış izin gruplarına dahil edilen tek tek izinler, bu makalenin başındaki tabloda listelenir.

#### <a name="no-access"></a>Erişim yok

Karantina ilkesi Erişim izni yok ( **yalnızca** yönetici erişimi) ataıyorsa, kullanıcılar karantinaya alınmış olan iletileri göremz:

- **Karantinaya alınmış ileti** ayrıntıları: Son kullanıcı görünümünde hiçbir ileti göster olmaz.
- **Bildirimleri karantinaya** alın: Bu iletiler için bildirim gönderilmez.

#### <a name="limited-access"></a>Sınırlı erişim

Karantina ilkesi Sınırlı erişim izinleri **atarsa** , kullanıcılar aşağıdaki özelliklere sahip olur:

- **Karantinaya alınmış ileti** ayrıntıları: Aşağıdaki düğmeler kullanılabilir:
  - **Sürüm isteği**
  - **İleti üst bilgilerini görüntüleme**
  - **İletiyi önizleme**
  - **Karantinadan kaldırma**
  - **Göndereni engelle**

  ![Karantina ilkesi kullanıcıya Sınırlı erişim izinleri veriyorsa, karantinaya alınan ileti ayrıntılarında kullanılabilir düğmeler.](../../media/quarantine-tags-quarantined-message-details-limited-access.png)

- **Karantina bildirimleri**: Aşağıdaki düğmeler kullanılabilir:
  - **Göndereni engelle**
  - **Sürüm isteği**
  - **Gözden Geçir**

  ![Karantina ilkesi kullanıcıya Sınırlı erişim izinleri veriyorsa, karantina bildiriminde kullanılabilir düğmeler.](../../media/quarantine-tags-esn-limited-access.png)

#### <a name="full-access"></a>Tam erişim

Karantina ilkesi Tam erişim izinleri ( **tüm kullanılabilir** izinler) atarsa, kullanıcılar aşağıdaki özelliklere sahip olur:

- **Karantinaya alınmış ileti** ayrıntıları: Aşağıdaki düğmeler kullanılabilir:
  - **Sürüm iletisi**
  - **İleti üst bilgilerini görüntüleme**
  - **İletiyi önizleme**
  - **Karantinadan kaldırma**
  - **Göndereni engelle**

  ![Karantina ilkesi kullanıcıya Tam erişim izinleri veriyorsa, karantinaya alınan ileti ayrıntılarında kullanılabilir düğmeler.](../../media/quarantine-tags-quarantined-message-details-full-access.png)

- **Karantina bildirimleri**: Aşağıdaki düğmeler kullanılabilir:
  - **Göndereni engelle**
  - **Sürüm**
  - **Gözden Geçir**

  ![Karantina ilkesi kullanıcıya Tam erişim izinleri veriyorsa, karantina bildiriminde kullanılabilir düğmeler.](../../media/quarantine-tags-esn-full-access.png)

### <a name="individual-permissions"></a>Tek tek izinler

#### <a name="block-sender-permission"></a>Gönderen iznini engelleme

Gönderen **iznini** engelle (_PermissionToBlockSender_) kullanıcıların karantinaya alınmış ileti gönderenini Engellenen Gönderenler listesine rahatça eklemelerine olanak sağlayan düğmeye erişimi denetimler.

- **Karantinaya alınmış ileti ayrıntıları**:
  - **Gönderen iznini** engelleme etkin: **Göndereni engelle** düğmesi kullanılabilir.
  - **Gönderen iznini** engelleme devre dışı **bırakıldı: Göndereni engelle** düğmesi kullanılamaz.

- **Karantina bildirimleri**:
  - **Gönderen iznini** engelleme etkin: **Göndereni engelle** düğmesi kullanılabilir.
  - **Gönderen iznini** engelleme devre dışı **bırakıldı: Göndereni engelle** düğmesi kullanılamaz.

Engellenen Gönderenler listesi hakkında daha fazla bilgi için bkz. Birilerinden gelen iletileri engelleme ve posta Exchange Online güvenilir liste koleksiyonunu yapılandırmak için [Exchange Online PowerShell kullanma](configure-junk-email-settings-on-exo-mailboxes.md#use-exchange-online-powershell-to-configure-the-safelist-collection-on-a-mailbox).[](https://support.microsoft.com/office/274ae301-5db2-4aad-be21-25413cede077#__toc304379667)

#### <a name="delete-permission"></a>Silme izni

Delete **izni** (_PermissionToDelete_) kullanıcıların iletilerini (kullanıcının alıcı olduğu iletileri) karantinadan silebilir.

- **Karantinaya alınmış ileti ayrıntıları**:
  - **silme** izni etkin: **Karantinadan kaldır** düğmesi kullanılabilir.
  - **silme** izni devre dışı: **Karantinadan kaldır** düğmesi kullanılamaz.

- **Bildirimleri karantinaya alın**: Efekt yok.

#### <a name="preview-permission"></a>Önizleme izni

Önizleme **izni** (_PermissionToPreview_), kullanıcıların iletilerini karantinada önizleme olanağını kontrol eder.

- **Karantinaya alınmış ileti ayrıntıları**:
  - **Önizleme** izni etkin: **Önizleme iletisi** düğmesi kullanılabilir.
  - **Önizleme** izni devre dışı: **İletiyi önizleme** düğmesi kullanılamıyor.

- **Bildirimleri karantinaya alın**: Efekt yok.

#### <a name="allow-recipients-to-release-a-message-from-quarantine-permission"></a>Alıcıların iletiyi karantina izninden çıkartırmalarına izin verme

**Alıcıların iletiyi** karantina izninden (_PermissionToRelease_) çıkarabilmeleri, kullanıcıların karantinaya alınmış iletilerini doğrudan ve yöneticinin onayı olmadan serbest bırakmasını sağlar.

- **Karantinaya alınmış ileti ayrıntıları**:
  - İzin etkinleştirildi: **İletiyi** bırak düğmesi kullanılabilir.
  - İzin devre dışı bırakıldı: **İletiyi** bırak düğmesi kullanılamıyor.

- **Karantina bildirimleri**:
  - İzin etkinleştirildi: **Sürüm** düğmesi kullanılabilir.
  - İzin devre dışı bırakıldı: **Sürüm** düğmesi kullanılamıyor.

#### <a name="allow-recipients-to-request-a-message-to-be-released-from-quarantine-permission"></a>Alıcıların bir iletiyi karantina izninden çıkarıılın isteğine izin ver

**Alıcıların karantina** izninden çıkarılmazken bir ileti talep etmelerine izin ver (_PermissionToRequestRelease_), kullanıcıların karantinaya alınmış iletilerinin  serbest bırakılmaz isteği göndermesini sağlar. İleti ancak yönetici isteği onaylar sonra serbest olur.

- **Karantinaya alınmış ileti ayrıntıları**:
  - İzin etkinleştirildi: **Sürüm isteği** düğmesi kullanılabilir.
  - İzin devre dışı bırakıldı: **Sürüm isteği** düğmesi kullanılamıyor.

- **Karantina bildirimleri**:
  - İzin etkinleştirildi: **Sürüm isteği** düğmesi kullanılabilir.
  - İzin devre dışı bırakıldı: **Sürüm isteği** düğmesi kullanılamıyor.
