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
description: Yöneticiler, karantinaya alınan iletilere kullanıcıların yapabileceklerini denetlemek için karantina ilkelerini kullanmayı öğrenebilir.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: a3d50debf31f53f75177e7c8cf8c7116ae3789b6
ms.sourcegitcommit: 997eb64f80da99b1099daba62994c722bbb25d72
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/16/2022
ms.locfileid: "66128865"
---
# <a name="quarantine-policies"></a>Karantina ilkeleri

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Şunlar için geçerlidir:**
- [Office 365 için Microsoft Defender plan 1 ve plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Exchange Online Protection(EOP) ve Office 365 için Microsoft Defender'de karantina ilkeleri (eski _adıyla karantina etiketleri_) yöneticilerin, iletilerin neden karantinaya alındığına bağlı olarak kullanıcıların karantinaya alınan iletileri ne yapabileceklerini denetlemesine olanak tanır.

Geleneksel olarak, iletinin neden karantinaya alındığına bağlı olarak, kullanıcılara karantina iletileri için etkileşim düzeyleri izin verilir veya reddedilir. Örneğin, kullanıcılar istenmeyen posta önleme filtrelemesi tarafından karantinaya alınan iletileri istenmeyen posta veya toplu olarak görüntüleyebilir ve yayımlayabilir, ancak yüksek güvenilirlikli kimlik avı veya kötü amaçlı yazılım olarak karantinaya alınan iletileri görüntüleyemez veya yayımlayamaz.

[Desteklenen koruma özellikleri](#step-2-assign-a-quarantine-policy-to-supported-features) için karantina ilkeleri, kullanıcıların karantinada ve karantina _bildirimlerinde_ kendi iletilerine (alıcı oldukları iletiler) ne yapmalarına izin verileceğini belirtir. [Karantina bildirimleri](use-spam-notifications-to-release-and-report-quarantined-messages.md) , son kullanıcı istenmeyen posta bildirimlerinin yerini alır. Bu bildirimler artık karantina ilkeleri tarafından denetlenmektedir ve tüm desteklenen koruma özellikleri (yalnızca istenmeyen posta önleme ilkesi ve kimlik avı önleme ilkesi kararları) için karantinaya alınan iletiler hakkında bilgi içerir.

Geçmiş kullanıcı özelliklerini zorunlu kılan varsayılan karantina ilkeleri, iletileri karantinaya alan desteklenen koruma özelliklerindeki eylemlere otomatik olarak atanır. Ya da özel karantina ilkeleri oluşturabilir ve kullanıcıların bu tür karantinaya alınmış iletilerde belirli eylemler gerçekleştirmesine izin vermek veya bunu engellemek için bunları desteklenen koruma özelliklerine atayabilirsiniz.

Tek tek karantina ilkesi izinleri aşağıdaki önceden ayarlanmış izin gruplarında birleştirilir:

- Erişim yok
- Sınırlı erişim
- Tam erişim

Önceden ayarlanmış izin gruplarında yer alan tek tek karantina ilkesi izinleri aşağıdaki tabloda açıklanmıştır:

|Izni|Erişim yok|Sınırlı erişim|Tam erişim|
|---|:---:|:---:|:---:|
|**Göndereni engelle** (_PermissionToBlockSender_)||![Onay işareti.](../../media/checkmark.png)|![Onay işareti.](../../media/checkmark.png)|
|**Delete** (_PermissionToDelete_)||![Onay işareti.](../../media/checkmark.png)|![Onay işareti.](../../media/checkmark.png)|
|**Önizleme** (_PermissionToPreview_)||![Onay işareti.](../../media/checkmark.png)|![Onay işareti.](../../media/checkmark.png)|
|**Alıcıların karantinadan bir iletiyi serbest bırakmasına izin ver** (_PermissionToRelease_)|||![Onay işareti.](../../media/checkmark.png)|
|**Alıcıların karantinadan çıkarılma isteğinde bulunmalarına izin ver** (_PermissionToRequestRelease_)||![Onay işareti](../../media/checkmark.png)||

Varsayılan karantina ilkeleri, ilişkili izin grupları ve karantina bildirimlerinin etkinleştirilip etkinleştirilmediği aşağıdaki tabloda açıklanmıştır:

|Varsayılan karantina ilkesi|Kullanılan izin grubu|Karantina bildirimleri etkinleştirildi mi?|
|---|:---:|:---:|
|AdminOnlyAccessPolicy|Erişim yok|Hayır|
|DefaultFullAccessPolicy|Tam erişim|Hayır|
|NotificationEnabledPolicy<sup>\*</sup>|Tam erişim|Evet|

Önceden ayarlanmış izin gruplarındaki varsayılan izinleri beğenmezseniz veya karantina bildirimlerini etkinleştirmek istiyorsanız, özel karantina ilkeleri oluşturun ve kullanın. Her iznin ne yaptığı hakkında daha fazla bilgi için bu makalenin devamındaki [Karantina ilkesi izin ayrıntıları](#quarantine-policy-permission-details) bölümüne bakın.

karantina ilkelerini Microsoft 365 Defender portalında veya PowerShell'de (Exchange Online Exchange Online posta kutularına sahip Microsoft 365 kuruluşlar için PowerShell'de; EOP kuruluşlarında tek başına EOP PowerShell'i olmadan oluşturur ve atarsınız Exchange Online posta kutuları).

> [!NOTE]
> Karantinaya alınan iletilerin süresi dolmadan önce karantinada ne kadar süre tutulduğunda, **istenmeyen postaları bu kadar gün boyunca karantinada tut** (_QuarantineRetentionPeriod_) istenmeyen posta önleme ilkeleri tarafından denetleniyor. Daha fazla bilgi için bkz. [EOP'de istenmeyen posta önleme ilkelerini yapılandırma](configure-your-spam-filter-policies.md).
>
> Desteklenen bir koruma özelliğine atanan karantina ilkesini değiştirirseniz, değişiklik siz değişikliği yaptıktan _sonra_ karantinaya alınan iletileri etkiler. Daha önce bu koruma özelliği tarafından karantinaya alınan iletiler, yeni karantina ilkesi atamasının ayarlarından etkilenmez.

## <a name="full-access-permissions-and-quarantine-notifications"></a>Tam erişim izinleri ve karantina bildirimleri

<sup>\*</sup> NotificationEnabledPolicy adlı karantina ilkesi tüm ortamlarda mevcut değildir. Kuruluşunuz aşağıdaki gereksinimlerin ikisini de karşılıyorsa NotificationEnabledPolicy karantina ilkesine sahip olursunuz:

- Karantina ilkesi özelliği açılmadan önce kuruluşunuz mevcuttu (Temmuz sonu/Ağustos 2021'in başı).
- Son kullanıcı [istenmeyen posta bildirimlerini](configure-your-spam-filter-policies.md) etkinleştir ayarının açık olduğu bir veya daha fazla istenmeyen posta önleme ilkeniz (varsayılan istenmeyen posta önleme ilkesi veya özel **istenmeyen posta önleme** ilkeleri) vardı.

Daha önce açıklandığı gibi, karantina ilkelerindeki karantina bildirimleri, istenmeyen posta önleme ilkelerini açmak veya kapatmak için kullandığınız son kullanıcı istenmeyen posta bildirimlerinin yerini alır. DefaultFullAccessPolicy adlı yerleşik karantina ilkesi, karantinaya alınan iletiler için geçmiş _izinleri_ yineler, ancak _karantina ilkesinde karantina bildirimleri_ açılmaz. Yerleşik ilkeyi değiştiremediğiniz için, DefaultFullAccessPolicy'de karantina bildirimlerini açamazsınız.

DefaultFullAccessPolicy izinlerini sağlamak ancak karantina bildirimleri açık durumdayken, gerekli olan kuruluşlar (son kullanıcı istenmeyen posta bildirimlerinin açık olduğu kuruluşlar) için DefaultFullAccessPolicy yerine kullanmak üzere NotificationEnabledPolicy adlı ilkeyi oluşturduk.

İstenmeyen posta önleme ilkelerinde son kullanıcı istenmeyen posta bildirimleri etkinleştirilmemiş olan yeni kuruluşlar veya eski kuruluşlar için NotificationEnabledPolicy adlı karantina ilkesine sahip olmazsınız. Karantina bildirimlerini açmanın yolu, karantina bildirimlerinin açık olduğu özel karantina ilkeleri oluşturmak ve kullanmaktır.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Başlamadan önce bilmeniz gerekenler

- Microsoft 365 Defender portalını adresinde <https://security.microsoft.com>açarsınız. **Doğrudan Karantina ilkeleri** sayfasına gitmek için kullanın<https://security.microsoft.com/quarantinePolicies>.

- Exchange Online PowerShell'e bağlanmak için bkz. [PowerShell'Exchange Online Bağlan](/powershell/exchange/connect-to-exchange-online-powershell). Tek başına EOP PowerShell'e bağlanmak için bkz. [PowerShell'i Exchange Online Protection için Bağlan](/powershell/exchange/connect-to-exchange-online-protection-powershell).

- Karantina ilkelerini görüntülemek, oluşturmak, değiştirmek veya kaldırmak için, Microsoft 365 Defender portalında **Kuruluş Yönetimi**, **Güvenlik Yöneticisi** veya **Karantina Yöneticisi** rollerinin üyesi olmanız gerekir. Daha fazla bilgi için bkz. [Microsoft 365 Defender portalında İzinler](permissions-microsoft-365-security-center.md).

## <a name="step-1-create-quarantine-policies-in-the-microsoft-365-defender-portal"></a>1. Adım: Microsoft 365 Defender portalında karantina ilkeleri oluşturma

1. [Microsoft 365 Defender portalında](https://security.microsoft.com), **Kurallar** bölümündeki **E-posta & işbirliği** \> **İlkeleri & Kurallar** \> **Tehdit ilkeleri** **Karantina ilkeleri'ne** \> gidin. Veya doğrudan **Karantina ilkeleri** sayfasına gitmek için kullanın <https://security.microsoft.com/quarantinePolicies>.

2. **Karantina ilkeleri** sayfasında Özel ilke ekle simgesine tıklayın![.](../../media/m365-cc-sc-create-icon.png) **Özel ilke ekleyin**.

3. **Yeni ilke** sihirbazı açılır. **İlke adı** sayfasında, **İlke** adı kutusuna kısa ama benzersiz bir ad girin. Önümüzdeki adımlarda karantina ilkesini ada göre tanımlamanız ve seçmeniz gerekir. İşiniz bittiğinde **İleri'ye** tıklayın.

4. **Alıcı iletisi erişimi** sayfasında aşağıdaki değerlerden birini seçin:
   - **Sınırlı erişim**: Bu izin grubuna dahil edilen tek tek izinler bu makalenin başlarında açıklanmıştır.
   - **Belirli erişimi ayarlama (Gelişmiş)**: Özel izinleri belirtmek için bu değeri kullanın. Görüntülenen aşağıdaki ayarları yapılandırın:
     - **Yayın eylemi tercihini seçin**: Aşağıdaki değerlerden birini seçin:
       - Boş: Bu varsayılan değerdir.
       - **Alıcıların karantinadan bir iletiyi serbest bırakmasına izin verme**
       - **Alıcıların karantinadan çıkarılma isteğinde bulunmalarına izin ver**
     - **Alıcıların karantinaya alınan iletilerde gerçekleştirebileceği ek eylemleri seçin**: Aşağıdaki değerlerden bazılarını, tümünü veya hiçbirini seçin:
       - **Silme**
       - **Önizleme**
       - **Göndereni engelle**

   Bu izinler ve bunların karantinaya alınan iletiler ve karantina bildirimleri üzerindeki etkisi, bu makalenin devamındaki [Karantina ilkesi izin ayrıntıları](#quarantine-policy-permission-details) bölümünde açıklanmaktadır.

   İşiniz bittiğinde **İleri'ye** tıklayın.

5. **Son kullanıcı istenmeyen posta bildirimi** sayfasında, karantina bildirimlerini (eski adıyla son kullanıcı istenmeyen posta bildirimleri) etkinleştirmek için **Etkinleştir'i** seçin. İşiniz bittiğinde **İleri'ye** tıklayın.

   > [!NOTE]
   > Daha önce açıklandığı gibi, yerleşik ilkelerde (AdminOnlyAccessPolicy veya DefaultFullAccessPolicy) karantinaya alınmış bildirimler açık değildir ve ilkeleri değiştiremezsiniz.

6. **İlkeyi gözden geçir** sayfasında ayarlarınızı gözden geçirin. Bölümün içindeki ayarları değiştirmek için her bölümde **Düzenle'yi** seçebilirsiniz. Ya da **Geri'ye** tıklayabilir veya sihirbazdaki belirli bir sayfayı seçebilirsiniz.

   İşiniz bittiğinde **Gönder'e** tıklayın.

7. Görüntülenen onay sayfasında **Bitti'ye** tıklayın.

Artık [2. Adım](#step-2-assign-a-quarantine-policy-to-supported-features) bölümünde açıklandığı gibi karantina ilkesini bir karantina özelliğine atamaya hazırsınız.

### <a name="create-quarantine-policies-in-powershell"></a>PowerShell'de karantina ilkeleri oluşturma

Karantina ilkeleri oluşturmak için PowerShell'i kullanmayı tercih ederseniz, Exchange Online PowerShell'e bağlanın veya PowerShell'i Exchange Online Protection ve **New-QuarantinePolicy cmdlet'ini** kullanın.

> [!NOTE]
> _ESNEnabled_ parametresini ve değerini `$true`kullanmıyorsanız karantina bildirimleri kapatılır.

#### <a name="use-the-enduserquarantinepermissionsvalue-parameter"></a>EndUserQuarantinePermissionsValue parametresini kullanma

_EndUserQuarantinePermissionsValue_ parametresini kullanarak karantina ilkesi oluşturmak için aşağıdaki söz dizimini kullanın:

```powershell
New-QuarantinePolicy -Name "<UniqueName>" -EndUserQuarantinePermissionsValue <0 to 236> [-EsnEnabled $true]
```

_EndUserQuarantinePermissionsValue_ parametresi, ikili değerden dönüştürülen bir ondalık değer kullanır. İkili değer, belirli bir sırada kullanılabilir son kullanıcı karantina izinlerine karşılık gelir. Her izin için 1 değeri True, 0 değeri ise False değerine eşittir.

Her bir izin için gerekli sıra ve değerler aşağıdaki tabloda açıklanmıştır:

|Izni|Ondalık değer|İkili değer|
|---|:---:|:---:|
|PermissionToViewHeader<sup>\*</sup>|128|10000000|
|PermissionToDownload<sup>\*\*</sup>|64|01000000|
|PermissionToAllowSender<sup>\*\*</sup>|32|00100000|
|PermissionToBlockSender|16|00010000|
|PermissionToRequestRelease<sup>\*\*\*</sup>|8|00001000|
|PermissionToRelease<sup>\*\*\*</sup>|4|00000100|
|PermissionToPreview|2|00000010|
|PermissionToDelete|1|00000001|

<sup>\*</sup> 0 değeri, karantinaya alınan **iletinin ayrıntılarında İleti üst bilgisini görüntüle** düğmesini gizlemez (düğme her zaman kullanılabilir).

<sup>\*\*</sup> Bu ayar kullanılmaz (0 veya 1 değeri hiçbir şey yapmaz).

<sup>\*\*\*</sup> Bu değerlerin ikisini de 1 olarak ayarlamayın. Birini 1, diğerini 0 olarak veya her ikisini de 0 olarak ayarlayın.

Sınırlı erişim izinleri için gerekli değerler şunlardır:

|Izni|Sınırlı erişim|
|---|:--:|
|PermissionToViewHeader|0|
|PermissionToDownload|0|
|PermissionToAllowSender|0|
|PermissionToBlockSender|1|
|PermissionToRequestRelease|1|
|PermissionToRelease|0|
|PermissionToPreview|1|
|PermissionToDelete|1|
|İkili değer|00011011|
|Kullanılacak ondalık değer|27|

Bu örnek, önceki tabloda açıklandığı gibi Sınırlı erişim izinlerini atayan karantina bildirimlerinin açık olduğu LimitedAccess adlı yeni bir karantina ilkesi oluşturur.

```powershell
New-QuarantinePolicy -Name LimitedAccess -EndUserQuarantinePermissionsValue 27 -EsnEnabled $true
```

Özel izinler için, istediğiniz izinlere karşılık gelen ikili değeri almak için önceki tabloyu kullanın. İkili değeri ondalık değere dönüştürün ve _EndUserQuarantinePermissionsValue_ parametresi için ondalık değeri kullanın. Parametre değeri için ikili değeri kullanmayın.

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [New-QuarantinePolicy](/powershell/module/exchange/new-quarantinepolicy).

## <a name="step-2-assign-a-quarantine-policy-to-supported-features"></a>2. Adım: Desteklenen özelliklere karantina ilkesi atama

E-posta iletilerini karantinaya alan _desteklenen_ koruma özelliklerinde, kullanılabilir karantina eylemlerine bir karantina ilkesi atayabilirsiniz. İletileri karantinaya alan özellikler ve karantina ilkelerinin kullanılabilirliği aşağıdaki tabloda açıklanmıştır:

|Özellik|Karantina ilkeleri destekleniyor mu?|Kullanılan varsayılan karantina ilkeleri|
|---|:---:|---|
|[İstenmeyen posta önleme ilkeleri](configure-your-spam-filter-policies.md): <ul><li>**İstenmeyen Posta** (_İstenmeyen Posta)_</li><li>**Yüksek güvenilirlikli istenmeyen posta** (_HighConfidenceSpamAction_)</li><li>**Kimlik Avı** (_PhishSpamAction_)</li><li>**Yüksek güvenilirlikli kimlik avı** (_HighConfidencePhishAction_)</li><li>**Toplu** (_BulkSpamAction_)</li></ul>|Evet|<ul><li>DefaultFullAccessPolicy<sup>\*</sup> (Tam erişim)</li><li>DefaultFullAccessPolicy<sup>\*</sup> (Tam erişim)</li><li>DefaultFullAccessPolicy<sup>\*</sup> (Tam erişim)</li><li>AdminOnlyAccessPolicy (Erişim yok)</li><li>DefaultFullAccessPolicy<sup>\*</sup> (Tam erişim)</li></ul>|
|Kimlik avı önleme ilkeleri: <ul><li>[Kimlik sahtekarlığına karşı koruma](set-up-anti-phishing-policies.md#spoof-settings) (_AuthenticationFailAction_)</li><li>[Office 365 için Defender kimliğe bürünme koruması](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365):<ul><li>**İleti kimliğine bürünülmüş bir kullanıcı olarak algılanırsa** (_TargetedUserProtectionAction_)</li><li>**İleti kimliğine bürünülen bir etki alanı olarak algılanırsa** (_TargetedDomainProtectionAction_)</li><li>**Posta kutusu zekası kullanıcı algılarsa ve kimliğine bürünüldüyse** (_MailboxIntelligenceProtectionAction_)</li></ul></li></ul>|Evet|<ul><li>DefaultFullAccessPolicy<sup>\*</sup> (Tam erişim)</li><li>Kimliğe bürünme koruması:<ul><li>DefaultFullAccessPolicy<sup>\*</sup> (Tam erişim)</li><li>DefaultFullAccessPolicy<sup>\*</sup> (Tam erişim)</li><li>DefaultFullAccessPolicy<sup>\*</sup> (Tam erişim)</li></ul></li></ul>|
|[Kötü amaçlı yazılımdan koruma ilkeleri](configure-anti-malware-policies.md): Algılanan tüm iletiler her zaman karantinaya alınır.|Evet|AdminOnlyAccessPolicy (Erişim yok)|
|[Kasa Ekler koruması](safe-attachments.md): <ul><li>Kasa Ekler ilkeleri (_Etkinleştir_ ve _Eylem_) tarafından kötü amaçlı yazılım olarak karantinaya alınan ekleri içeren e-posta iletileri</li><li>[SharePoint, OneDrive ve Microsoft Teams için Kasa Ekleri](mdo-for-spo-odb-and-teams.md) tarafından kötü amaçlı yazılım olarak karantinaya alınan dosyalar</li></ul>|<ul><li>Evet</li><li>Hayır</li></ul>|<ul><li>AdminOnlyAccessPolicy (Erişim yok)</li><li>yok</li></ul>|
|[Posta akışı kuralları](/exchange/security-and-compliance/mail-flow-rules/mail-flow-rules) (taşıma kuralları olarak da bilinir) eylemiyle birlikte: **İletiyi barındırılan karantinaya (** Karantina) teslim _edin_.|Hayır|yok|

<sup>\*</sup>[Bu makalede daha önce açıklandığı](#full-access-permissions-and-quarantine-notifications) gibi, kuruluşunuz DefaultFullAccessPolicy yerine NotificationEnabledPolicy kullanabilir. Bu iki karantina ilkesi arasındaki tek fark, karantina bildirimlerinin NotificationEnabledPolicy'de açılması ve DefaultFullAccessPolicy'de kapatılmasıdır.

Varsayılan karantina ilkeleri, önceden ayarlanmış izin grupları ve izinler [bu makalenin başında](#quarantine-policies) ve [bu makalenin sonraki bölümlerinde](#preset-permissions-groups) açıklanmıştır.

> [!NOTE]
> Varsayılan karantina ilkeleri tarafından sağlanan (veya sağlanmayan) varsayılan son kullanıcı izinlerinden ve karantina bildirimlerinden memnunsanız, hiçbir şey yapmanız gerekmez. Kullanıcının karantinaya alınan iletileri için son kullanıcı özelliklerini (kullanılabilir düğmeler) eklemek veya kaldırmak ya da karantina bildirimlerini etkinleştirmek ve karantina bildirimlerinde aynı özellikleri eklemek veya kaldırmak istiyorsanız, karantina eylemine farklı bir karantina ilkesi atayabilirsiniz.

## <a name="assign-quarantine-policies-in-supported-policies-in-the-microsoft-365-defender-portal"></a>Microsoft 365 Defender portalında desteklenen ilkelerde karantina ilkeleri atama

> [!NOTE]
> Kullanıcılar, karantina ilkesinin nasıl yapılandırıldığına bakılmaksızın kötü amaçlı yazılım (kötü amaçlı yazılımdan koruma ilkeleri) veya yüksek güvenilirlikli kimlik avı (istenmeyen posta önleme ilkeleri) olarak karantinaya alınan kendi iletilerini yayınlayamaz. Yöneticiler en iyi durumda karantina ilkesini yapılandırarak kullanıcıların karantinaya alınan kötü amaçlı yazılımlarının veya yüksek güvenilirlikli kimlik avı iletilerinin yayınlanmasını isteyebilmesini sağlayabilir.

### <a name="anti-spam-policies"></a>İstenmeyen posta önleme ilkeleri

1. [Microsoft 365 Defender portalında](https://security.microsoft.com), **İlkeler** bölümünde **e-posta & işbirliği** \> **İlkeleri & kuralları** \> **Tehdit ilkeleri** \> **İstenmeyen posta önleme** bölümüne gidin.

   Veya doğrudan **Ant-istenmeyen posta ilkeleri** sayfasına gitmek için kullanın <https://security.microsoft.com/antispam>.

2. **İstenmeyen posta önleme ilkeleri** sayfasında aşağıdaki adımlardan birini yapın:
   - Mevcut **bir gelen** istenmeyen posta önleme ilkesini bulun ve seçin.
   - Yeni bir **gelen** istenmeyen posta önleme ilkesi oluşturun.

3. Aşağıdaki adımlardan birini yapın:
   - **Var olanı düzenle**: İlkenin adına tıklayarak ilkeyi seçin. İlke ayrıntıları açılır öğesinde Eylemler bölümüne gidin ve **Eylemleri** **düzenle'ye** tıklayın.
   - **Yeni oluştur**: Yeni ilke sihirbazında **Eylemler** sayfasına gidin.

4. **Eylemler** sayfasında, **Karantina iletisi** eylemine sahip olan her kararda, karşılık gelen **bir karantina ilkesini seçmeniz için Karantina ilkesi seç** kutusu da bulunur.

   **Not**: Yeni bir ilke oluşturduğunuzda, boş bir **Karantina ilkesi seçin** değeri, bu karar için varsayılan karantina ilkesinin kullanıldığını gösterir. İlkeyi daha sonra düzenlediğinizde, boş değerler önceki tabloda açıklandığı gibi gerçek varsayılan karantina ilkesi adlarıyla değiştirilir.

   :::image type="content" source="../../media/quarantine-tags-in-anti-spam-policies.png" alt-text="İstenmeyen posta önleme ilkesindeki Karantina ilkesi seçimleri" lightbox="../../media/quarantine-tags-in-anti-spam-policies.png":::

İstenmeyen posta önleme ilkelerini oluşturmaya ve değiştirmeye yönelik tüm yönergeler [EOP'de istenmeyen posta önleme ilkelerini yapılandırma başlığı altında](configure-your-spam-filter-policies.md) açıklanmıştır.

#### <a name="anti-spam-policies-in-powershell"></a>PowerShell'de istenmeyen posta önleme ilkeleri

İstenmeyen posta önleme ilkelerine karantina ilkeleri atamak için PowerShell'i kullanmayı tercih ediyorsanız, Exchange Online PowerShell'e bağlanın veya PowerShell'i Exchange Online Protection ve aşağıdaki söz dizimini kullanın:

```powershell
<New-HostedContentFilterPolicy -Name "<Unique name>" | Set-HostedContentFilterPolicy -Identity "<Policy name>"> [-SpamAction Quarantine] [-SpamQuarantineTag <QuarantineTagName>] [-HighConfidenceSpamAction Quarantine] [-HighConfidenceSpamQuarantineTag <QuarantineTagName>] [-PhishSpamAction Quarantine] [-PhishQuarantineTag <QuarantineTagName>] [-HighConfidencePhishQuarantineTag <QuarantineTagName>] [-BulkSpamAction Quarantine] [-BulkQuarantineTag <QuarantineTagName>] ...
```

**Notlar**:

- _PhishSpamAction_ ve _HighConfidencePhishAction parametrelerinin_ varsayılan değeri Karantina'dır, bu nedenle PowerShell'de yeni istenmeyen posta filtresi ilkeleri oluştururken bu parametreleri kullanmanız gerekmez. Yeni veya mevcut istenmeyen posta önleme ilkelerinde _SpamAction_, _HighConfidenceSpamAction_ ve _BulkSpamAction_ parametreleri için, karantina ilkesi yalnızca değer Karantina olduğunda geçerlidir.

  Mevcut istenmeyen posta önleme ilkelerindeki önemli parametre değerlerini görmek için aşağıdaki komutu çalıştırın:

  ```powershell
  Get-HostedContentFilterPolicy | Format-List Name,*SpamAction,HighConfidencePhishAction,*QuarantineTag
  ```

  Standart ve Katı için varsayılan eylem değerleri ve önerilen eylem değerleri hakkında bilgi için bkz. [EOP istenmeyen posta önleme ilkesi ayarları](recommended-settings-for-eop-and-office365.md#eop-anti-spam-policy-settings).

- Yeni istenmeyen posta önleme ilkeleri oluşturduğunuzda, buna karşılık gelen karantina ilkesi parametresi olmayan bir istenmeyen posta filtreleme kararı, bu karar için [varsayılan karantina ilkesinin](#step-2-assign-a-quarantine-policy-to-supported-features) kullanıldığı anlamına gelir.

  Varsayılan karantina ilkesini özel bir karantina ilkesiyle değiştirmeniz gerekir, ancak belirli bir istenmeyen posta filtreleme kararı için karantinaya alınan iletilerde varsayılan son kullanıcı özelliklerini değiştirmek istersiniz.

- PowerShell'de yeni bir istenmeyen posta önleme ilkesi, **New-HostedContentFilterPolicy** cmdlet'ini kullanan bir istenmeyen posta filtresi ilkesi (ayarlar) ve **New-HostedContentFilterRule** cmdlet'ini kullanan özel istenmeyen posta filtresi kuralı (alıcı filtreleri) gerektirir. Yönergeler için bkz. [İstenmeyen posta önleme ilkeleri oluşturmak için PowerShell kullanma](configure-your-spam-filter-policies.md#use-powershell-to-create-anti-spam-policies).

Bu örnek, aşağıdaki ayarlarla Araştırma Bölümü adlı yeni bir istenmeyen posta filtresi ilkesi oluşturur:

- Tüm istenmeyen posta filtreleme kararlarının eylemi Karantina olarak ayarlanır.
- **Erişim izni yok** atayan NoAccess adlı özel karantina ilkesi, varsayılan olarak Erişim izni **yok** atamayan varsayılan karantina ilkelerinin yerini alır.

```powershell
New-HostedContentFilterPolicy -Name "Research Department" -SpamAction Quarantine -SpamQuarantineTag NoAccess -HighConfidenceSpamAction Quarantine -HighConfidenceSpamQuarantineTag NoAction -PhishSpamAction Quarantine -PhishQuarantineTag NoAction -BulkSpamAction Quarantine -BulkQuarantineTag NoAccess
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [New-HostedContentFilterPolicy](/powershell/module/exchange/new-hostedcontentfilterpolicy).

Bu örnek, İnsan Kaynakları adlı mevcut istenmeyen posta filtresi ilkesini değiştirir. İstenmeyen posta karantina kararı için eylem Karantina olarak ayarlanır ve NoAccess adlı özel karantina ilkesi atanır.

```powershell
Set-HostedContentFilterPolicy -Identity "Human Resources" -SpamAction Quarantine -SpamQuarantineTag NoAccess
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [Set-HostedContentFilterPolicy](/powershell/module/exchange/set-hostedcontentfilterpolicy).

### <a name="anti-phishing-policies"></a>Kimlik avından koruma ilkeleri

Kimlik sahtekarlık zekası EOP ve Office 365 için Defender kullanılabilir. Kullanıcı kimliğe bürünme koruması, etki alanı kimliğe bürünme koruması ve posta kutusu zekası yalnızca Office 365 için Defender kullanılabilir. Daha fazla bilgi için bkz. [Microsoft 365'da kimlik avı önleme ilkeleri](set-up-anti-phishing-policies.md).

1. [Microsoft 365 Defender portalında](https://security.microsoft.com), İlkeler **bölümünde** **e-posta & işbirliği** \> **İlkeleri & kuralları** \> **Tehdit ilkeleri** \> **Kimlik avı önleme** bölümüne gidin.

   Veya doğrudan **Ant-istenmeyen posta ilkeleri** sayfasına gitmek için kullanın <https://security.microsoft.com/antiphishing>.

2. **Kimlik avı önleme** sayfasında aşağıdaki adımlardan birini yapın:
   - Mevcut kimlik avı önleme ilkesini bulun ve seçin.
   - Yeni bir kimlik avı önleme ilkesi oluşturun.

3. Aşağıdaki adımlardan birini yapın:
   - **Var olanı düzenle**: İlkenin adına tıklayarak ilkeyi seçin. İlke ayrıntıları açılır öğesinde **Koruma ayarları** bölümüne gidin ve **koruma ayarlarını düzenle'ye** tıklayın.
   - **Yeni oluştur**: Yeni ilke sihirbazında **Eylemler** sayfasına gidin.

4. **Koruma ayarları** sayfasında, aşağıdaki ayarların açık olduğunu ve gerektiği gibi yapılandırıldığını doğrulayın:
   - **Korunacak kullanıcılar etkinleştirildi**: Kullanıcıları belirtin.
   - **Korunacak etkin etki alanları**: **Sahibi olduğum etki alanlarını dahil et** ve/veya **Özel etki alanları ekle'yi** seçin ve etki alanlarını belirtin.
   - **Posta kutusu zekasını etkinleştirme**
   - **Kimliğe bürünme koruması için zekayı etkinleştirme**
   - **Kimlik sahtekarı zekasını etkinleştirme**

5. Aşağıdaki adımlardan birini yapın:
   - **Var olanı düzenle**: İlke ayrıntıları açılır öğesinde **Eylemler** bölümüne gidin ve **Eylemleri düzenle'ye** tıklayın.
   - **Yeni oluştur**: Yeni ilke sihirbazında **Eylemler** sayfasına gidin.

6. **Eylemler** sayfasında, **İletiyi karantinaya al** eylemine sahip her kararda, karşılık gelen **bir karantina ilkesini seçmeniz için Karantina ilkesi uygula** kutusu da bulunur.

   **Not**: Yeni bir ilke oluşturduğunuzda, boş bir **Karantina ilkesi uygula** değeri, bu eylem için varsayılan karantina ilkesinin kullanıldığını gösterir. İlkeyi daha sonra düzenlediğinizde, boş değerler önceki tabloda açıklandığı gibi gerçek varsayılan karantina ilkesi adlarıyla değiştirilir.

   :::image type="content" source="../../media/quarantine-tags-in-anti-phishing-policies.png" alt-text="Kimlik avı önleme ilkesinde Karantina ilkesi seçimleri" lightbox="../../media/quarantine-tags-in-anti-phishing-policies.png":::

Kimlik avı önleme ilkelerini oluşturmaya ve değiştirmeye yönelik tam yönergeler aşağıdaki konularda sağlanır:

- [EOP'de kimlik avı önleme ilkelerini yapılandırma](configure-anti-phishing-policies-eop.md)
- [Office 365 için Microsoft Defender'de kimlik avı önleme ilkelerini yapılandırma](configure-mdo-anti-phishing-policies.md)

#### <a name="anti-phishing-policies-in-powershell"></a>PowerShell'de kimlik avı önleme ilkeleri

Kimlik avı önleme ilkelerine karantina ilkeleri atamak için PowerShell'i kullanmayı tercih ediyorsanız, Exchange Online PowerShell'e bağlanın veya PowerShell'i Exchange Online Protection ve aşağıdaki söz dizimini kullanın:

```powershell
<New-AntiPhishPolicy -Name "<Unique name>" | Set-AntiPhishPolicy -Identity "<Policy name>"> [-EnableSpoofIntelligence $true] [-AuthenticationFailAction Quarantine] [-SpoofQuarantineTag <QuarantineTagName>] [-EnableMailboxIntelligence $true] [-EnableMailboxIntelligenceProtection $true] [-MailboxIntelligenceProtectionAction Quarantine] [-MailboxIntelligenceQuarantineTag <QuarantineTagName>] [-EnableOrganizationDomainsProtection $true] [-EnableTargetedDomainsProtection $true] [-TargetedDomainProtectionAction Quarantine] [-TargetedDomainQuarantineTag <QuarantineTagName>] [-EnableTargetedUserProtection $true] [-TargetedUserProtectionAction Quarantine] [-TargetedUserQuarantineTag <QuarantineTagName>] ...
```

**Notlar**:

- Belirli koruma özelliklerini açmak için _Enable\*_ parametreleri gereklidir. _EnableMailboxIntelligence_ ve _EnableSpoofIntelligence_ parametrelerinin varsayılan değeri $true olduğundan PowerShell'de yeni kimlik avı önleme ilkeleri oluştururken bu parametreleri kullanmanız gerekmez. Diğer tüm _Enable\*_ parametrelerinde değerin $true olması gerekir, böylece ilgili _\*Eylem_ parametrelerindeki Karantina değerini bir karantina ilkesi atamak üzere ayarlayabilirsiniz. _*\Action_ parametrelerinin hiçbiri Varsayılan Karantina değerine sahip değil.

  Mevcut kimlik avı önleme ilkelerindeki önemli parametre değerlerini görmek için aşağıdaki komutu çalıştırın:

  ```powershell
  Get-AntiPhishPolicy | Format-List Name,Enable*Intelligence,Enable*Protection,*Action,*QuarantineTag
  ```

  Standart ve Katı için varsayılan eylem değerleri ve önerilen eylem değerleri hakkında bilgi için bkz. [Office 365 için Microsoft Defender'de kimlik avı önleme ilkelerindeki EOP](recommended-settings-for-eop-and-office365.md#eop-anti-phishing-policy-settings) [kimlik avı önleme ilkesi ayarları ve Kimliğe bürünme ayarları](recommended-settings-for-eop-and-office365.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365).

- Kimlik avı önleme ilkeleri oluşturduğunuzda, buna karşılık gelen karantina ilkesi parametresi olmayan bir kimlik avı önleme eylemi, bu karar için [varsayılan karantina ilkesinin](#step-2-assign-a-quarantine-policy-to-supported-features) kullanıldığı anlamına gelir.

  Varsayılan karantina ilkesini özel bir karantina ilkesiyle değiştirmeniz gerekir, ancak söz konusu karar için karantinaya alınan iletilerde varsayılan son kullanıcı özelliklerini değiştirmek istiyorsanız.

- PowerShell'de yeni bir kimlik avı önleme ilkesi, **New-AntiPhishPolicy** cmdlet'ini kullanan bir kimlik avı önleme ilkesi (ayarlar) ve **New-AntiPhishRule** cmdlet'ini kullanan özel bir kimlik avı önleme kuralı (alıcı filtreleri) gerektirir. Yönergeler için aşağıdaki konulara bakın:
  - [EOP'de kimlik avı önleme ilkelerini yapılandırmak için PowerShell kullanma](configure-anti-phishing-policies-eop.md#use-exchange-online-powershell-to-configure-anti-phishing-policies)
  - [Kimlik avı önleme ilkelerini yapılandırmak için Exchange Online PowerShell kullanma](configure-mdo-anti-phishing-policies.md#use-exchange-online-powershell-to-configure-anti-phishing-policies)

Bu örnek, aşağıdaki ayarlarla Araştırma Bölümü adlı yeni bir kimlik avı önleme ilkesi oluşturur:

- Tüm istenmeyen posta filtreleme kararlarının eylemi Karantina olarak ayarlanır.
- **Erişim izni yok** atayan NoAccess adlı özel karantina ilkesi, varsayılan olarak Erişim izni **yok** atamayan varsayılan karantina ilkelerinin yerini alır.

```powershell
New-AntiPhishPolicy -Name "Research Department" -AuthenticationFailAction Quarantine -SpoofQuarantineTag NoAccess -EnableMailboxIntelligenceProtection $true -MailboxIntelligenceProtectionAction Quarantine -MailboxIntelligenceQuarantineTag NoAccess -EnableOrganizationDomainsProtection $true -EnableTargetedDomainsProtection $true -TargetedDomainProtectionAction Quarantine -TargetedDomainQuarantineTag NoAccess -EnableTargetedUserProtection $true -TargetedUserProtectionAction Quarantine -TargetedUserQuarantineTag NoAccess
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [New-AntiPhishPolicy](/powershell/module/exchange/new-antiphishpolicy).

Bu örnek, İnsan Kaynakları adlı mevcut kimlik avı önleme ilkesini değiştirir. Kullanıcı kimliğe bürünme ve etki alanı kimliğe bürünme tarafından algılanan iletiler için eylem Karantina olarak ayarlanır ve NoAccess adlı özel karantina ilkesi atanır.

```powershell
Set-AntiPhishPolicy -Identity "Human Resources" -EnableTargetedDomainsProtection $true -TargetedDomainProtectionAction Quarantine -TargetedDomainQuarantineTag NoAccess -EnableTargetedUserProtection $true -TargetedUserProtectionAction Quarantine -TargetedUserQuarantineTag NoAccess
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [Set-AntiPhishPolicy](/powershell/module/exchange/set-antiphishpolicy).

### <a name="anti-malware-policies"></a>Kötü amaçlı yazılımdan koruma ilkeleri

1. [Microsoft 365 Defender portalında](https://security.microsoft.com), **İlkeler** bölümünde **e-posta & işbirliği** \> **İlkeleri & kurallar** \> **Tehdit ilkeleri** \> **Kötü amaçlı yazılımdan koruma** bölümüne gidin.

   Ya da doğrudan **Kötü amaçlı yazılımdan koruma** sayfasına gitmek için kullanın <https://security.microsoft.com/antimalwarev2>.

2. **Kötü amaçlı yazılımdan koruma** sayfasında aşağıdaki adımlardan birini yapın:
   - Mevcut kötü amaçlı yazılımdan koruma ilkesini bulun ve seçin.
   - Yeni bir kötü amaçlı yazılımdan koruma ilkesi oluşturun.

3. Aşağıdaki adımlardan birini yapın:
   - **Var olanı düzenle**: İlkenin adına tıklayarak ilkeyi seçin. İlke ayrıntıları açılır öğesinde **Koruma ayarları** bölümüne gidin ve **koruma ayarlarını düzenle'ye** tıklayın.
   - **Yeni oluştur**: Yeni ilke sihirbazında **Eylemler** sayfasına gidin.

4. **Koruma ayarları** sayfasında, Karantina ilkesi kutusunda bir karantina **ilkesi** seçin.

   **Not**: Yeni bir ilke oluşturduğunuzda, boş bir **Karantina ilkesi** değeri bunun için kullanılan varsayılan karantina ilkesini gösterir. İlkeyi daha sonra düzenlediğinizde, boş değer önceki tabloda açıklandığı gibi gerçek varsayılan karantina ilkesi adıyla değiştirilir.

#### <a name="anti-malware-policies-in-powershell"></a>PowerShell'de kötü amaçlı yazılımdan koruma ilkeleri

Kötü amaçlı yazılımdan koruma ilkelerine karantina ilkeleri atamak için PowerShell'i kullanmayı tercih ediyorsanız, Exchange Online PowerShell'e bağlanın veya PowerShell'i Exchange Online Protection ve aşağıdaki söz dizimini kullanın:

```powershell
<New-AntiMalwarePolicy -Name "<Unique name>" | Set-AntiMalwarePolicy -Identity "<Policy name>"> [-QuarantineTag <QuarantineTagName>]
```

**Notlar**:

- Yeni bir kötü amaçlı yazılımdan koruma ilkesi oluştururken QuarantineTag parametresini kullanmadan yeni kötü amaçlı yazılımdan koruma ilkeleri oluşturduğunuzda, kötü amaçlı yazılım algılamaları için varsayılan karantina ilkesi kullanılır (AdminOnlyAccessPolicy).

  Varsayılan karantina ilkesini, yalnızca kötü amaçlı yazılım olarak karantinaya alınan iletilerde varsayılan son kullanıcı özelliklerini değiştirmek istiyorsanız özel bir karantina ilkesiyle değiştirmeniz gerekir.

  Mevcut kimlik avı önleme ilkelerindeki önemli parametre değerlerini görmek için aşağıdaki komutu çalıştırın:

  ```powershell
  Get-MalwareFilterPolicy | Format-Table Name,QuarantineTag
  ```

- PowerShell'de yeni bir kötü amaçlı yazılımdan koruma ilkesi, **New-MalwareFilterPolicy** cmdlet'ini kullanan bir kötü amaçlı yazılım filtresi ilkesi (ayarlar) ve **New-MalwareFilterRule** cmdlet'ini kullanan özel amaçlı yazılım filtresi kuralı (alıcı filtreleri) gerektirir. Yönergeler için bkz. [Kötü amaçlı yazılımdan koruma ilkelerini yapılandırmak için PowerShell veya tek başına EOP PowerShell Exchange Online kullanma](configure-anti-malware-policies.md#use-exchange-online-powershell-or-standalone-eop-powershell-to-configure-anti-malware-policies).

Bu örnek, karantinaya alınan iletilere **Erişim** yok izni atayan NoAccess adlı özel karantina ilkesini kullanan Araştırma Bölümü adlı bir kötü amaçlı yazılım filtresi ilkesi oluşturur.

```powershell
New-MalwareFilterPolicy -Name "Research Department" -QuarantineTag NoAccess
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [New-MalwareFilterPolicy](/powershell/module/exchange/new-malwarefilterpolicy).

Bu örnek, karantinaya alınan iletilere **Erişim** yok izni atayan NoAccess adlı özel karantina ilkesini atayarak İnsan Kaynakları adlı mevcut kötü amaçlı yazılım filtresi ilkesini değiştirir.

```powershell
New-MalwareFilterPolicy -Identity "Human Resources" -QuarantineTag NoAccess
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [Set-MalwareFilterPolicy](/powershell/module/exchange/set-malwarefilterpolicy).

### <a name="safe-attachments-policies-in-defender-for-office-365"></a>Office 365 için Defender'da ek ilkelerini Kasa

1. [Microsoft 365 Defender portalında](https://security.microsoft.com), İlkeler **bölümündeki** **E-posta & işbirliği** \> **İlkeleri & kuralları** \> **Tehdit ilkeleri** \> **Kasa Ekler** bölümüne gidin.

   Veya doğrudan **Kasa Ekler** sayfasına gitmek için kullanın<https://security.microsoft.com/safeattachmentv2>.

2. **Kasa Ekler** sayfasında aşağıdaki adımlardan birini yapın:
   - Var olan bir Kasa Ekler ilkesini bulun ve seçin.
   - Yeni bir Kasa Ekler ilkesi oluşturun.

3. Aşağıdaki adımlardan birini yapın:
   - **Var olanı düzenle**: İlkenin adına tıklayarak ilkeyi seçin. İlke ayrıntıları açılır öğesinde **Ayarlar** bölümüne gidin ve **Ayarları düzenle'ye** tıklayın.
   - **Yeni oluştur**: Yeni ilke sihirbazında **Ayarlar** sayfasına gidin.

4. **Ayarlar** sayfasında aşağıdaki adımları uygulayın:
   1. **Kasa Ekler bilinmeyen kötü amaçlı yazılım yanıtı**: **Engelle**, **Değiştir** veya **Dinamik Teslim'i** seçin.
   2. Karantina ilkesi kutusunda bir **karantina ilkesi** seçin.

   **Not**: Yeni bir ilke oluşturduğunuzda, boş bir **Karantina ilkesi** değeri varsayılan karantina ilkesinin kullanıldığını gösterir. İlkeyi daha sonra düzenlediğinizde, boş değer önceki tabloda açıklandığı gibi gerçek varsayılan karantina ilkesi adıyla değiştirilir.

Kasa Ek ilkelerini oluşturma ve değiştirmeyle ilgili tam yönergeler, [Office 365 için Microsoft Defender'da Ek ilkelerini ayarlama Kasa başlığı altında](set-up-safe-attachments-policies.md) açıklanmıştır.

#### <a name="safe-attachments-policies-in-powershell"></a>PowerShell'de ek ilkelerini Kasa

Kasa Ekler ilkelerine karantina ilkeleri atamak için PowerShell'i kullanmayı tercih ederseniz, Exchange Online PowerShell'e bağlanın veya PowerShell'i Exchange Online Protection ve aşağıdaki söz dizimini kullanın:

```powershell
<New-SafeAttachmentPolicy -Name "<Unique name>" | Set-SafeAttachmentPolicy -Identity "<Policy name>"> -Enable $true -Action <Block | Replace | DynamicDelivery> [-QuarantineTag <QuarantineTagName>]
```

**Notlar**:

- _Eylem_ parametre değerleri Engelle, Değiştir veya DynamicDelivery karantinaya alınmış iletilere neden olabilir (İzin Ver değeri iletileri karantinaya almaz). _Eylem_ parametresinin değeri yalnızca _Enable_ parametresinin değeri olduğunda anlamlı olur`$true`.

- QuarantineTag parametresini kullanmadan yeni Kasa Ekler ilkeleri oluşturduğunuzda, e-postadaki Kasa Ekler algılamaları için varsayılan karantina ilkesi kullanılır (AdminOnlyAccessPolicy).

  Varsayılan karantina ilkesini özel bir karantina ilkesiyle değiştirmeniz gerekir, ancak Kasa Ekler ilkeleri tarafından karantinaya alınan e-posta iletilerindeki varsayılan son kullanıcı özelliklerini değiştirmek istiyorsanız.

  Önemli parametre değerlerini görmek için aşağıdaki komutu çalıştırın:

  ```powershell
  Get-SafeAttachmentPolicy | Format-List Name,Enable,Action,QuarantineTag
  ```

- PowerShell'de yeni bir Kasa Ekler ilkesi, **New-SafeAttachmentPolicy** cmdlet'ini kullanan güvenli bir ek ilkesi (ayarlar) ve **New-SafeAttachmentRule** cmdlet'ini kullanan özel bir güvenli ek kuralı (alıcı filtreleri) gerektirir. Yönergeler için bkz. [Kasa Ekler ilkelerini yapılandırmak için PowerShell Exchange Online veya tek başına EOP PowerShell kullanma](set-up-safe-attachments-policies.md#use-exchange-online-powershell-or-standalone-eop-powershell-to-configure-safe-attachments-policies).

Bu örnek, algılanan iletileri engelleyen Ve karantinaya alınan iletilere **Erişim** yok izni atayan NoAccess adlı özel karantina ilkesini kullanan Araştırma Bölümü adlı güvenli bir ek ilkesi oluşturur.

```powershell
New-SafeAttachmentPolicy -Name "Research Department" -Enable $true -Action Block -QuarantineTag NoAccess
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [New-MalwareFilterPolicy](/powershell/module/exchange/new-malwarefilterpolicy).

Bu örnek, **Erişim** yok izinleri atayan NoAccess adlı özel karantina ilkesini atayarak İnsan Kaynakları adlı mevcut güvenli ek ilkesini değiştirir.

```powershell
Set-SafeAttachmentPolicy -Identity "Human Resources" -QuarantineTag NoAccess
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [Set-MalwareFilterPolicy](/powershell/module/exchange/set-malwarefilterpolicy).

## <a name="configure-global-quarantine-notification-settings-in-the-microsoft-365-defender-portal"></a>Microsoft 365 Defender portalında genel karantina bildirim ayarlarını yapılandırma

Karantina ilkeleri için genel ayarlar, karantinaya alınan iletilerin alıcılarına gönderilen karantina bildirimlerini, karantina ilkesinde karantina bildirimleri açıksa özelleştirmenize olanak sağlar. Bu bildirimler hakkında daha fazla bilgi için bkz [. Karantina bildirimleri](use-spam-notifications-to-release-and-report-quarantined-messages.md).

1. Microsoft 365 Defender portalında **Kurallar bölümündeki** **E-posta & işbirliği** \> **İlkeleri & kurallar** \> **Tehdit ilkeleri** **Karantina ilkeleri'ne** \> gidin. Veya doğrudan **Karantina ilkeleri** sayfasına gitmek için kullanın <https://security.microsoft.com/quarantinePolicies>.

2. **Karantina ilkeleri** sayfasında **Genel ayarlar'ı** seçin.

3. Açılan **Karantina bildirim ayarları** açılır öğesinde aşağıdaki ayarları yapılandırın:

   - Karantina bildirimlerini alıcının diline göre özelleştirin:

     - Aşağıdaki ekran görüntüsünde gösterildiği gibi karantina bildirimlerinde kullanılan gönderenin **görünen adı** .

       :::image type="content" source="../../media/quarantine-tags-esn-customization-display-name.png" alt-text="Karantina bildiriminde özelleştirilmiş bir gönderen görünen adı." lightbox="../../media/quarantine-tags-esn-customization-display-name.png":::

     - Karantina bildirimlerinin altına eklenen **Yasal Uyarı** metni. Yerelleştirilmiş metin( **Kuruluşunuzdan bir bildirim:** her zaman önce dahil edilir ve ardından aşağıdaki ekran görüntüsünde gösterildiği gibi belirttiğiniz metin gösterilir:

       :::image type="content" source="../../media/quarantine-tags-esn-customization-disclaimer.png" alt-text="Karantina bildiriminin alt kısmındaki özel bir bildirim." lightbox="../../media/quarantine-tags-esn-customization-disclaimer.png":::

     - **Görünen ad** ve **Yasal Uyarı** değerlerinin dil tanımlayıcısı. Karantina bildirimleri, alıcının dil ayarlarına göre zaten yerelleştirilmiştir. **Görünen ad** ve **Yasal Uyarı** değerleri, alıcının diline uygulanan karantina bildirimlerinde kullanılır.

       **Görünen ad** ve **Yasal Uyarı** kutularına değer girmeden _önce_ **Dil seç kutusunda dili** seçin. **Dili seç** kutusundaki değeri değiştirdiğinizde Görünen **ad** ve **Uyarı** kutularındaki değerler boşaltılır.

     Karantina bildirimlerini alıcının diline göre özelleştirmek için şu adımları izleyin:

     1. **Dil seç kutusundan dili seçin**. Varsayılan değer **Varsayılan'dır** ve İngilizce anlamına gelir.
     2. **Görünen ad** ve **Yasal Uyarı** değerlerini girin. Değerler her dil için benzersiz olmalıdır. **Bir Görünen adı** veya **Yasal Uyarı** değerini birden çok dil için yeniden kullanmayı denerseniz **Kaydet'e** tıkladığınızda bir hata alırsınız.
     3. **Ekle** düğmesine tıklayın.
     4. Alıcının diline göre en fazla üç özelleştirilmiş karantina bildirimi oluşturmak için önceki adımları yineleyin. Etiketsiz kutu yapılandırdığınız dilleri gösterir:

        :::image type="content" source="../../media/quarantine-tags-esn-customization-selected-languages.png" alt-text="Karantina ilkelerinin genel karantina bildirimi ayarlarında seçilen diller." lightbox="../../media/quarantine-tags-esn-customization-selected-languages.png":::

   - **Şirket logomu kullan**: Karantina bildirimlerinin en üstünde kullanılan varsayılan Microsoft logosunu değiştirmek için bu seçeneği belirleyin. Bu adımı gerçekleştirmeden önce, özel logonuzu karşıya yüklemek [için kuruluşunuzun Microsoft 365 temasını özelleştirme başlığı altında yer alan](../../admin/setup/customize-your-organization-theme.md) yönergeleri izlemeniz gerekir.

     Aşağıdaki ekran görüntüsünde karantina bildiriminde özel bir logo gösterilmektedir:

     :::image type="content" source="../../media/quarantine-tags-esn-customization-logo.png" alt-text="Karantina bildiriminde özel logo" lightbox="../../media/quarantine-tags-esn-customization-logo.png":::

   - **Her (gün) son kullanıcı istenmeyen posta bildirimi gönder**: Karantina bildirimlerinin sıklığını seçin. Varsayılan değer 3 gündür, ancak 1 ile 15 gün arasını seçebilirsiniz.

4. Bitirdiğinizde, **Kaydet**'i tıklatın.

## <a name="view-quarantine-policies-in-the-microsoft-365-defender-portal"></a>Microsoft 365 Defender portalında karantina ilkelerini görüntüleme

1. Microsoft 365 Defender portalında **Kurallar bölümündeki** **E-posta & işbirliği** \> **İlkeleri & kurallar** \> **Tehdit ilkeleri** **Karantina ilkeleri'ne** \> gidin. Veya doğrudan **Karantina ilkeleri** sayfasına gitmek için kullanın <https://security.microsoft.com/quarantinePolicies>.

2. **Karantina ilkeleri** sayfası, **ad** ve **son güncelleştirme** tarihine göre ilkelerin listesini gösterir.

3. Yerleşik veya özel karantina ilkelerinin ayarlarını görüntülemek için, ada tıklayarak listeden karantina ilkesini seçin.

4. Genel ayarları görüntülemek için **Genel ayarlar'a** tıklayın

### <a name="view-quarantine-policies-in-powershell"></a>PowerShell'de karantina ilkelerini görüntüleme

Karantina ilkelerini görüntülemek için PowerShell'i kullanmak isterseniz aşağıdaki adımlardan birini uygulayın:

- Tüm yerleşik veya özel ilkelerin özet listesini görüntülemek için aşağıdaki komutu çalıştırın:

  ```powershell
  Get-QuarantinePolicy | Format-Table Name
  ```

- Yerleşik veya özel karantina ilkelerinin ayarlarını görüntülemek için öğesini karantina ilkesinin adıyla değiştirin \<QuarantinePolicyName\> ve aşağıdaki komutu çalıştırın:

  ```powershell
  Get-QuarantinePolicy -Identity "<QuarantinePolicyName>"
  ```

- Karantina bildirimlerinin genel ayarlarını görüntülemek için aşağıdaki komutu çalıştırın:

  ```powershell
  Get-QuarantinePolicy -QuarantinePolicyType GlobalQuarantinePolicy
  ```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [Get-HostedContentFilterPolicy](/powershell/module/exchange/get-hostedcontentfilterpolicy).

## <a name="modify-quarantine-policies-in-the-microsoft-365-defender-portal"></a>Microsoft 365 Defender portalında karantina ilkelerini değiştirme

AdminOnlyAccessPolicy veya DefaultFullAccessPolicy adlı yerleşik karantina ilkelerini değiştiremezsiniz. NotificationEnabledPolicy adlı yerleşik ilkeyi (varsa) ve özel karantina ilkelerini [değiştirebilirsiniz](#full-access-permissions-and-quarantine-notifications).

1. Microsoft 365 Defender portalında **Kurallar bölümündeki** **E-posta & işbirliği** \> **İlkeleri & kurallar** \> **Tehdit ilkeleri** **Karantina ilkeleri'ne** \> gidin. Veya doğrudan **Karantina ilkeleri** sayfasına gitmek için kullanın <https://security.microsoft.com/quarantinePolicies>.

2. **Karantina ilkeleri** sayfasında, ada tıklayarak ilkeyi seçin.

3. İlkeyi seçtikten sonra İlkeyi düzenle simgesine ![tıklayın.](../../media/m365-cc-sc-edit-icon.png) Görüntülenen **ilkeyi düzenle** simgesi.

4. Açılan **İlkeyi düzenle** sihirbazı, bu makalenin önceki bölümlerinde yer alan [Microsoft 365 Defender portalında karantina ilkeleri oluşturma](#step-1-create-quarantine-policies-in-the-microsoft-365-defender-portal) bölümünde açıklandığı gibi **Yeni ilke** sihirbazıyla neredeyse aynıdır.

   Temel fark şudur: Mevcut bir ilkeyi yeniden adlandıramazsınız.

5. İlkeyi değiştirmeyi bitirdiğinizde **Özet** sayfasına gidin ve **Gönder'e** tıklayın.

### <a name="modify-quarantine-policies-in-powershell"></a>PowerShell'de karantina ilkelerini değiştirme

Özel bir karantina ilkesini değiştirmek için PowerShell'i kullanmayı tercih ederseniz, öğesini karantina ilkesinin adıyla değiştirin \<QuarantinePolicyName\> ve aşağıdaki söz dizimini kullanın:

```powershell
Set-QuarantinePolicy -Identity "<QuarantinePolicyName>" [Settings]
```

Kullanılabilir ayarlar, bu makalenin önceki bölümlerinde karantina ilkeleri oluşturmak için açıklanan ayarlarla aynıdır.

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [Set-QuarantinePolicy](/powershell/module/exchange/set-quarantinepolicy).

## <a name="remove-quarantine-policies-in-the-microsoft-365-defender-portal"></a>Microsoft 365 Defender portalında karantina ilkelerini kaldırma

**Notlar**:

- AdminOnlyAccessPolicy veya DefaultFullAccessPolicy adlı yerleşik karantina ilkelerini kaldıramazsınız. NotificationEnabledPolicy adlı yerleşik ilkeyi ([varsa](#full-access-permissions-and-quarantine-notifications)) ve özel karantina ilkelerini kaldırabilirsiniz.
- Karantina ilkesini kaldırmadan önce kullanılmadığını doğrulayın. Örneğin, PowerShell'de aşağıdaki komutu çalıştırın:

  ```powershell
  Write-Output -InputObject "Anti-spam policies","----------------------";Get-HostedContentFilterPolicy | Format-List Name,*QuarantineTag; Write-Output -InputObject "Anti-phishing policies","----------------------";Get-AntiPhishPolicy | Format-List Name,*QuarantineTag; Write-Output -InputObject "Anti-malware policies","----------------------";Get-MalwareFilterPolicy | Format-List Name,QuarantineTag; Write-Output -InputObject "Safe Attachments policies","---------------------------";Get-SafeAttachmentPolicy | Format-List Name,QuarantineTag
  ```

  Karantina ilkesi kullanılıyorsa, kaldırmadan önce [atanan karantina ilkesini değiştirin](#step-2-assign-a-quarantine-policy-to-supported-features) .

1. Microsoft 365 Defender portalında **Kurallar bölümündeki** **E-posta & işbirliği** \> **İlkeleri & kurallar** \> **Tehdit ilkeleri** **Karantina ilkeleri'ne** \> gidin. Veya doğrudan **Karantina ilkeleri** sayfasına gitmek için kullanın <https://security.microsoft.com/quarantinePolicies>.

2. **Karantina ilkeleri** sayfasında, ada tıklayarak kaldırmak istediğiniz özel karantina ilkesini seçin.

3. İlkeyi seçtikten sonra İlkeyi sil simgesine ![tıklayın.](../../media/m365-cc-sc-delete-icon.png) Görüntülenen **ilkeyi sil** simgesi.

4. Görüntülenen onay iletişim kutusunda **İlkeyi kaldır'a** tıklayın.

### <a name="remove-quarantine-policies-in-powershell"></a>PowerShell'de karantina ilkelerini kaldırma

Özel bir karantina ilkesini kaldırmak için PowerShell'i kullanmayı tercih ederseniz, öğesini karantina ilkesinin adıyla değiştirin \<QuarantinePolicyName\> ve aşağıdaki komutu çalıştırın:

```powershell
Remove-QuarantinePolicy -Identity "<QuarantinePolicyName>"
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [Remove-QuarantinePolicy](/powershell/module/exchange/remove-quarantinepolicy).

## <a name="system-alerts-for-quarantine-release-requests"></a>Karantina yayın istekleri için sistem uyarıları

Varsayılan olarak, **Kullanıcı karantinaya alınmış bir iletiyi serbest bırakmak istedi** adlı varsayılan uyarı ilkesi otomatik olarak bilgilendirici bir uyarı oluşturur ve bir kullanıcı karantinaya alınmış bir iletinin yayımlanmasını istediğinde aşağıdaki rol gruplarının üyelerine bildirim iletileri gönderir:

- Karantina Yöneticisi
- Güvenlik Yöneticisi
- Kuruluş Yönetimi (genel yönetici)

Yöneticiler e-posta bildirimi alıcılarını özelleştirebilir veya daha fazla seçenek için özel bir uyarı ilkesi oluşturabilir.

Uyarı ilkeleri hakkında daha fazla bilgi için bkz[. Microsoft 365 uyarı ilkeleri](../../compliance/alert-policies.md).

## <a name="quarantine-policy-permission-details"></a>Karantina ilkesi izin ayrıntıları

Aşağıdaki bölümlerde, karantinaya alınan iletilerin ayrıntılarında ve karantina bildirimlerinde önceden ayarlanmış izin gruplarının ve tek tek izinlerin etkileri açıklanmaktadır.

### <a name="preset-permissions-groups"></a>Önceden ayarlanmış izin grupları

Önceden ayarlanmış izin gruplarına dahil edilen tek tek izinler, bu makalenin başındaki tabloda listelenmiştir.

#### <a name="no-access"></a>Erişim yok

Karantina ilkesi **Erişim** yok izni atarsa (yalnızca yönetici erişimi), kullanıcılar karantinaya alınan iletileri göremez:

- **Karantinaya alınan ileti ayrıntıları**: Son kullanıcı görünümünde hiçbir ileti gösterilmez.
- **Karantina bildirimleri**: Bu iletiler için hiçbir bildirim gönderilmez.

#### <a name="limited-access"></a>Sınırlı erişim

Karantina ilkesi **Sınırlı erişim** izinleri atarsa, kullanıcılar aşağıdaki özellikleri alır:

- **Karantinaya alınan ileti ayrıntıları**: Aşağıdaki düğmeler kullanılabilir:
  - **Yayın isteği**
  - **İleti üst bilgilerini görüntüleme**
  - **önizleme iletisi**
  - **Karantinadan kaldır**
  - **Göndereni engelle**

  :::image type="content" source="../../media/quarantine-tags-quarantined-message-details-limited-access.png" alt-text="Karantinaya alınan iletideki kullanılabilir düğmeler, karantina ilkesi kullanıcıya sınırlı erişim izinleri verirse ayrıntıları verir" lightbox="../../media/quarantine-tags-quarantined-message-details-limited-access.png":::

- **Karantina bildirimleri**: Aşağıdaki düğmeler kullanılabilir:
  - **Göndereni engelle**
  - **Yayın isteği**
  - **Gözden geçirin**

  :::image type="content" source="../../media/quarantine-tags-esn-limited-access.png" alt-text="Karantina ilkesi kullanıcıya sınırlı erişim izinleri verirse karantina bildirimindeki kullanılabilir düğmeler" lightbox="../../media/quarantine-tags-esn-limited-access.png":::

#### <a name="full-access"></a>Tam erişim

Karantina ilkesi **Tam erişim** izinleri atarsa (tüm kullanılabilir izinler), kullanıcılar aşağıdaki özellikleri alır:

- **Karantinaya alınan ileti ayrıntıları**: Aşağıdaki düğmeler kullanılabilir:
  - **Yayın iletisi**
  - **İleti üst bilgilerini görüntüleme**
  - **önizleme iletisi**
  - **Karantinadan kaldır**
  - **Göndereni engelle**

  :::image type="content" source="../../media/quarantine-tags-quarantined-message-details-full-access.png" alt-text="Karantinaya alınan iletideki kullanılabilir düğmeler, karantina ilkesi kullanıcıya tam erişim izinleri verirse ayrıntıları verir" lightbox="../../media/quarantine-tags-quarantined-message-details-full-access.png":::

- **Karantina bildirimleri**: Aşağıdaki düğmeler kullanılabilir:
  - **Göndereni engelle**
  - **Sürüm**
  - **Gözden geçirin**

  :::image type="content" source="../../media/quarantine-tags-esn-full-access.png" alt-text="Karantina ilkesi kullanıcıya tam erişim izinleri verirse karantina bildirimindeki kullanılabilir düğmeler" lightbox="../../media/quarantine-tags-esn-full-access.png":::

> [!NOTE]
> Daha önce açıklandığı gibi, karantina **ilkesiNde Tam erişim** izin grubu atanmış olsa bile, karantina bildirimleri DefaultFullAccessPolicy adlı varsayılan karantina ilkesinde devre dışı bırakılmıştır. Karantina bildirimleri yalnızca oluşturduğunuz özel karantina ilkelerinde veya NotificationEnabledPolicy adlı varsayılan karantina erişim [ilkesinde (bu ilke kuruluşunuzda kullanılabiliyorsa) kullanılabilir](#full-access-permissions-and-quarantine-notifications).

### <a name="individual-permissions"></a>Bireysel izinler

#### <a name="block-sender-permission"></a>Gönderen iznini engelle

**Göndereni engelle** izni (_PermissionToBlockSender_), kullanıcıların karantinaya alınan iletiyi göndereni Engellenen Gönderenler listesine kolayca eklemesine olanak tanıyan düğmeye erişimi denetler.

- **Karantinaya alınan ileti ayrıntıları**:
  - **Gönderen iznini engelle** etkinleştirildi: **Göndereni engelle** düğmesi kullanılabilir.
  - **Gönderen iznini engelle** devre dışı: **Göndereni engelle** düğmesi kullanılamıyor.

- **Karantina bildirimleri**:
  - **Gönderen iznini engelle** etkinleştirildi: **Göndereni engelle** düğmesi kullanılabilir.
  - **Gönderen iznini engelle** devre dışı: **Göndereni engelle** düğmesi kullanılamıyor.

Engellenen Gönderenler listesi hakkında daha fazla bilgi için bkz. [Birinden gelen iletileri engelleme](https://support.microsoft.com/office/274ae301-5db2-4aad-be21-25413cede077#__toc304379667) ve [Exchange Online PowerShell kullanarak posta kutusunda güvenli liste koleksiyonunu yapılandırma](configure-junk-email-settings-on-exo-mailboxes.md#use-exchange-online-powershell-to-configure-the-safelist-collection-on-a-mailbox).

#### <a name="delete-permission"></a>Silme izni

**Silme** izni (_PermissionToDelete_), kullanıcıların iletilerini (kullanıcının alıcı olduğu iletiler) karantinadan silme yeteneğini denetler.

- **Karantinaya alınan ileti ayrıntıları**:
  - **Silme** izni etkin: **Karantinadan kaldır** düğmesi kullanılabilir.
  - **Silme** izni devre dışı: **Karantinadan kaldır** düğmesi kullanılamıyor.

- **Karantina bildirimleri**: Hiçbir etkisi yoktur.

#### <a name="preview-permission"></a>Önizleme izni

**Önizleme** izni (_PermissionToPreview_), kullanıcıların karantinadaki iletilerini önizleme olanağını denetler.

- **Karantinaya alınan ileti ayrıntıları**:
  - **Önizleme** izni etkin: **Önizleme iletisi** düğmesi kullanılabilir.
  - **Önizleme** izni devre dışı: **Önizleme iletisi** düğmesi kullanılamıyor.

- **Karantina bildirimleri**: Hiçbir etkisi yoktur.

#### <a name="allow-recipients-to-release-a-message-from-quarantine-permission"></a>Alıcıların karantina izinlerinden bir iletiyi serbest bırakmasına izin ver

**Alıcıların karantina izninden bir iletiyi serbest bırakmasına izin ver** (_PermissionToRelease_), kullanıcıların karantinaya alınan iletilerini doğrudan ve yönetici onayı olmadan serbest bırakma yeteneğini denetler.

- **Karantinaya alınan ileti ayrıntıları**:
  - İzin etkinleştirildi: **Yayın iletisi** düğmesi kullanılabilir.
  - İzin devre dışı: **Yayın iletisi** düğmesi kullanılamıyor.

- **Karantina bildirimleri**:
  - İzin etkinleştirildi: **Yayın** düğmesi kullanılabilir.
  - İzin devre dışı: **Serbest Bırak** düğmesi kullanılamıyor.

#### <a name="allow-recipients-to-request-a-message-to-be-released-from-quarantine-permission"></a>Alıcıların karantina izninden serbest bırakılacak bir ileti istemesine izin ver

**Alıcıların karantina izninden serbest bırakılmak üzere bir ileti istemesine izin ver** (_PermissionToRequestRelease_), kullanıcıların karantinaya alınan iletilerinin yayımlanmasını _isteme_ becerisini denetler. İleti yalnızca bir yönetici isteği onayladıktan sonra serbest bırakılır.

- **Karantinaya alınan ileti ayrıntıları**:
  - İzin etkinleştirildi: **Yayın isteği** düğmesi kullanılabilir.
  - İzin devre dışı: **Yayın isteği** düğmesi kullanılamıyor.

- **Karantina bildirimleri**:
  - İzin etkinleştirildi: **Yayın isteği** düğmesi kullanılabilir.
  - İzin devre dışı: **Yayın isteği** düğmesi kullanılamıyor.
