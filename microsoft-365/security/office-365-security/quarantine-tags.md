---
title: Karantina ilkeleri
ms.author: chrisda
author: chrisda
manager: dansimp
ms.reviewer: ''
ms.date: ''
audience: ITPro
ms.topic: how-to
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: ''
ms.collection:
- M365-security-compliance
ROBOTS: NOINDEX
description: Yöneticiler, kullanıcıların karantinaya alınmış iletilerinde neler yapabileceklerini denetim altına almak için karantina ilkelerini kullanmayı öğrenebilir.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 96dc1e2158787457884ca6a3c6f27bf76e83a369
ms.sourcegitcommit: b3c4816b55657b87ed4a5f6a4abe3d505392218e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/04/2021
ms.locfileid: "62959698"
---
# <a name="quarantine-policies"></a>Karantina ilkeleri

> [!NOTE]
> Bu makalede açıklanan özellikler şu anda Önizleme'dedir, herkes tarafından kullanılamaz ve değişebilir.

Exchange Online Protection'daki (EOP) karantina ilkeleri (daha önce karantina etiketleri olarak bilinirdi) yöneticilerin, iletinin karantinaya nasıl geldiğine bağlı olarak kullanıcılara karantinaya alınmış iletilerinde neler yapabileceklerini denetlemelerine olanak sağlar.

EOP geleneksel olarak karantinada ve son kullanıcı istenmeyen posta bildirimlerinde iletiler için belirli etkileşim [](find-and-release-quarantined-messages-as-a-user.md) [düzeylerine izin verdi veya bunu engelledi](use-spam-notifications-to-release-and-report-quarantined-messages.md). Örneğin, kullanıcılar istenmeyen posta önleme filtresiyle istenmeyen posta veya toplu olarak karantinaya alınmış iletileri  görüntüp serbest bıraksa da, yüksek güvene sahip kimlik avı olarak karantinaya alınmış iletileri görüntüden veya serbest bırakarak görüntüde bırak yayımlanan iletiler (yalnızca yöneticiler bunu yapar).

Desteklenen [koruma özellikleri için](#step-2-assign-a-quarantine-policy-to-supported-features) karantina ilkeleri, son kullanıcı istenmeyen posta bildirim iletilerinde ve karantinaya alınan iletilerde (kullanıcının alıcı olduğu iletiler) kullanıcıların ne yapmalarına izin verilmiyor? Karantinaya alınmış iletilerde kullanıcılar için geçmiş özelliklerini zorunlu tutulacak şekilde varsayılan karantina ilkeleri otomatik olarak atanır. Öte ya da, son kullanıcıların karantinaya alınmış iletilerde belirli eylemler gerçekleştirmesine izin vermek veya bunu engellemek için özel karantina ilkeleri oluşturabilir ve atabilirsiniz.

Tek tek izinler, aşağıdaki önceden ayarlanmış izin gruplarında bir araya olur:

- Erişim yok
- Sınırlı erişim
- Tam erişim

Kullanılabilir tek tek izinler ve önceden ayarlanmış izin gruplarına nelerin dahil olup nelerin dahil olmadığını aşağıdaki tabloda açıklanmıştır:

<br>

****

|İzin|Erişim yok|Sınırlı erişim|Tam erişim|
|---|:---:|:---:|:---:|
|**Gönderene izin** ver (_PermissionToAllowSender_)|||![Onay işareti](../../media/checkmark.png)|
|**Göndereni engelleme** (_PermissionToBlockSender_)||![Onay işareti](../../media/checkmark.png)|![Onay işareti](../../media/checkmark.png)|
|**Delete** (_PermissionToDelete_)||![Onay işareti](../../media/checkmark.png)|![Onay işareti](../../media/checkmark.png)|
|**Önizleme** (_PermissionToPreview_)||![Onay işareti](../../media/checkmark.png)|![Onay işareti](../../media/checkmark.png)|
|**Alıcıların iletiyi karantinadan bırakmasına izin verme** (_PermissionToRelease_)|||![Onay işareti](../../media/checkmark.png)|
|**Alıcıların bir iletinin karantinadan çıkarılmaz** için istekte olmasına izin verme (_PermissionToRequestRelease_)||![Onay işareti](../../media/checkmark.png)||
|

Önceden ayarlanmış izin gruplarında varsayılan izinler sizin için uygun değildir; özel karantina ilkeleri  oluşturmak veya değiştirmek için özel izinleri kullanabilirsiniz. Her iznin ne yaptığı hakkında daha fazla bilgi için, bu [makalenin devam](#quarantine-policy-permission-details) bölümündeki Karantina ilkesi izin ayrıntıları bölümüne bakın.

Microsoft 365 Defender portalında veya PowerShell'de (Exchange Online Microsoft 365 Posta Kutuları olan Microsoft 365 powershell için Exchange Online PowerShell; EOP kuruluşlarında tek başına EOP PowerShell Exchange Online kutularını) kullanın.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Başlamadan önce bilmeniz gerekenler

- Microsoft 365 Defender portalını açın<https://security.microsoft.com>. Ya da doğrudan Karantina ilkeleri **sayfasına gitmek** için, 'i açın <https://security.microsoft.com/quarantineTags>.

- Exchange Online PowerShell'e bağlanmak [için bkz. Bağlan PowerShell Exchange Online e bağlama](/powershell/exchange/connect-to-exchange-online-powershell). Tek başına EOP PowerShell'e bağlanmak [için bkz. Bağlan PowerShell Exchange Online Protection e bağlama](/powershell/exchange/connect-to-exchange-online-protection-powershell).

- Karantina ilkelerini görüntülemek, oluşturmak, değiştirmek veya kaldırmak için, İlke portalında Kuruluş Yönetimi veya Güvenlik Yöneticisi  rollerinin üyesi  Microsoft 365 Defender gerekir. Daha fazla bilgi için [portalda izinler Microsoft 365 Defender bakın](permissions-microsoft-365-security-center.md).

## <a name="step-1-create-quarantine-policies-in-the-microsoft-365-defender-portal"></a>1. Adım: Microsoft 365 Defender portalında karantina ilkeleri oluşturma

1. Microsoft 365 Defender portalında E-posta ve İşbirliği **&** \> tehdit ilkeleri **Kuralları** \>  \> bölümünde Karantina ilkeleri bölümüne gidin ve **sonra Karantina** **ilkeleri'ne tıklayın**.

2. Karantina ilkesi **sayfasında Özel** ilke ekle simgesi ![Özel ilke **ekle'ye**](../../media/m365-cc-sc-create-icon.png) tıklayın.

3. Yeni **ilke sihirbazı** açılır. İlke **adı sayfasında** , İlke adı kutusuna kısa ama benzersiz **bir ad** girin. Önümüzdeki adımlarda, karantina ilkesi tanımlamanız ve adla seçmeniz gerekir. Bitirdikten sonra, Sonraki'ne **tıklayın**.

4. Alıcı **iletisi erişimi sayfasında** , aşağıdaki değerlerden birini seçin:
   - **Erişim yok**
   - **Sınırlı erişim**
   - **Tam erişim**

   Bu izin gruplarında yer alan tek tek izinler bu makalenin önceki sayfalarında açıklanmıştır.

   Özel izinler belirtmek için Belirli **erişimi ayarla (Gelişmiş) seçeneğini** belirtin ve aşağıdaki ayarları yapılandırarak görünür:

     - **Sürüm eylemi tercihini** seçin: Aşağıdaki değerlerden birini seçin:
       - **Sürüm eylemi yok**: Bu varsayılan değerdir.
       - **Alıcıların iletiyi karantinadan bırakmasına izin ver**
       - **Alıcıların bir iletinin karantinadan çıkarılım için istekte olmasına izin ver**
     - **Alıcıların karantinaya alınmış iletilere ek eylemleri seçme**: Aşağıdaki değerlerden birini, hiçbirini veya hiçbirini seçme:
       - **Silme**
       - **Önizleme**
       - **Göndereni engelle**

   Bu izinler ve karantinaya alınmış iletiler üzerindeki etkisi ve son kullanıcı istenmeyen posta bildirimleri, bu makalenin devamın [Karantina ilkesi izin](#quarantine-policy-permission-details) ayrıntıları bölümünde açıklanmıştır.

   Bitirdikten sonra, Sonraki'ne **tıklayın**.

5. Görüntülenen **İlkeyi** gözden geçir sayfasında ayarlarınızı gözden geçirebilirsiniz. Bölümün içindeki **ayarları değiştirmek** için her bölümde Düzenle'yi seçebilirsiniz. Geri'ye **tıklar** veya sihirbazda belirli bir sayfayı seçersiniz.

   Bitirdikten sonra Gönder'e **tıklayın**.

6. Görüntülenen onay sayfasında Bitti'ye **tıklayın**.

Artık, Adım 2 bölümünde açıklandığı gibi karantina ilkesine karantina özelliği [atamaya hazırsınız](#step-2-assign-a-quarantine-policy-to-supported-features) .

### <a name="create-quarantine-policies-in-powershell"></a>PowerShell'de karantina ilkeleri oluşturma

Karantina ilkeleri oluşturmak için PowerShell kullanmayı tercih ediyorsanız, PowerShell'Exchange Online veya PowerShell'Exchange Online Protection **yeni Karantina Etiketi** cmdlet'ini kullanın. İki farklı yönteminiz vardır:

- _EndUserQuarantinePermissionsValue parametresini_ kullanın.
- _EndUserQuarantinePermissions parametresini_ kullanın.

Bu yöntemler aşağıdaki bölümlerde açıklanmıştır.

#### <a name="use-the-enduserquarantinepermissionsvalue-parameter"></a>EndUserQuarantinePermissionsValue parametresini kullanma

_EndUserQuarantinePermissionsValue parametresini_ kullanarak bir karantina ilkesi oluşturmak için, aşağıdaki söz dizimi kullanın:

```powershell
New-QuarantineTag -Name "<UniqueName>" -EndUserQuarantinePermissionsValue <0 to 236>
```

_EndUserQuarantinePermissionsValue_ parametresi, ikili değerden dönüştürülen bir ondalık değer kullanır. İkili değer, kullanılabilir son kullanıcı karantina izinlerine belirli bir sırada karşılık gelen değerdir. Her izin için 1 değeri Doğru'ya ve 0 değeri de Yanlış'a eşittir.

Önceden ayarlanmış izin gruplarında her bir izin için gereken sıra ve değerler aşağıdaki tabloda açıklanmıştır:

<br>

****

|İzin|Erişim yok|Sınırlı erişim|Tam erişim|
|---|:---:|:---:|:---:|
|PermissionToAllowSender|0|0|1|
|PermissionToBlocksender|0|1|1|
|PermissionToDelete|0|1|1|
|PermissionToDownload<sup>\*</sup>|0|0|0|
|PermissionToPreview|0|1|1|
|PermissionToRelease<sup>\*\*</sup>|0|0|1|
|PermissionToRequestRelease<sup>\*\*</sup>|0|1|0|
|PermissionToViewHeader<sup>\*</sup>|0|0|0|
|İkili değer|00000000|01101010|11101100|
|Ondalık değer|0|106|236|
|

<sup>\*</sup> Şu anda, bu değer her zaman 0'dır. PermissionToViewHeader için, 0 değeri karantinaya alınmış iletinin ayrıntılarında  İleti üst bilgilerini görüntüle düğmesini gizlemez (düğme her zaman kullanılabilir).

<sup>\*\*</sup> Bu değerlerin ikisini de 1 olarak ayarlayın. Birini 1,0 olarak ayarlayın veya her ikisini de 0 olarak ayarlayın.

Bu örnekte, önceki tabloda açıklandığı gibi Erişim izni yok ataması için NoAccess yeni bir karantina ilkesi adı oluşturur.

```powershell
New-QuarantineTag -Name NoAccess -EndUserQuarantinePermissionsValue 0
```

Sınırlı erişim izinleri için 106 değerini kullanın. Tam erişim izinleri için 236 değerini kullanın.

Özel izinler için, istediğiniz izinlere karşılık gelen ikili değeri almak için önceki tabloyu kullanın. İkili değeri ondalık değere dönüştürin ve _EndUserQuarantinePermissionsValue parametresi için ondalık değeri_ kullanın.

Ayrıntılı söz dizimi ve parametre bilgileri için bkz [. Yeni Karantina Etiketi](/powershell/module/exchange/new-quarantinetag).

#### <a name="use-the-enduserquarantinepermissions-parameter"></a>EndUserQuarantinePermissions parametresini kullanma

_EndUserQuarantinePermissionsValue parametresini_ kullanarak bir karantina ilkesi oluşturmak için, aşağıdaki adımları izleyin:

C. **New-QuarantinePermissions cmdlet'ini kullanarak bir değişkende karantina izinleri** nesnesi depolar.

<p>

B. Değişkeni, **New-QuarantineTag** _komutunda EndUserQuarantinePermissions_ değeri olarak kullanın.

##### <a name="step-a-store-a-quarantine-permissions-object-in-a-variable"></a>A Adımı: Bir değişkende karantina izinleri nesnesini depolama

Aşağıdaki sözdizimini kullanın:

```powershell
$<VariableName> = New-QuarantinePermissions [-PermissionToAllowSender <$true | $False>] [-PermissionToBlockSender <$true | $False>] [-PermissionToDelete <$true | $False>] [-PermissionToPreview <$true | $False>] [-PermissionToRelease <$true | $False>] [-PermissionToRequestRelease <$true | $False>]
```

Kullanılmamış parametrelerin varsayılan değeri `$false`olarak 'tir, dolayısıyla yalnızca değerini ayarlamak istediğiniz parametreleri kullana gerek vardır `$true`.

Aşağıdaki örneklerde, önceden ayarlanmış izin gruplarına karşılık gelen izin nesnelerinin nasıl oluşturuldiği göster:

- **Erişim yok**:

  ```powershell
  $NoAccess = New-QuarantinePermissions
  ```

- **Sınırlı erişim**:

  ```powershell
  $LimitedAccess = New-QuarantinePermissions -PermissionToBlockSender $true -PermissionToDelete $true -PermissionToPreview $true -PermissionToRequestRelease $true
  ```

- **Tam erişim**:

  ```powershell
  $FullAccess = New-QuarantinePermissions -PermissionToAllowSender $true -PermissionToBlockSender $true -PermissionToDelete $true -PermissionToPreview $true -PermissionToRelease $true
  ```

Ayar değerlerini görmek için, değişken adını komut olarak çalıştırın (örneğin, komutu çalıştırın `$NoAccess`).

Özel izinler için, _permissionToRelease_ ve _PermissionToRequestRelease_ parametrelerini 'a ayarlamayın `$true`. Birini ' olarak `$true` ayarlayın ve diğer olarak bırakın veya `$false`her ikisini de 'olarak bırakın `$false`.

Var olan izin nesnesi değişkenlerini oluşturdukktan sonra, ancak Bunu **Kullan-KarantinaPermissions** cmdlet'ini kullanarak daha önce değiştirebilirsiniz.

Ayrıntılı söz dizimi ve parametre bilgileri için [bkz. New-QuarantinePermissions](/powershell/module/exchange/new-quarantinepermissions) ve [Set-QuarantinePermissions](/powershell/module/exchange/set-quarantinepermissions).

##### <a name="step-b-use-the-variable-in-the-new-quarantinetag-command"></a>B. Adım: Değişken komutunda New-QuarantineTag kullanın

Bir değişkende izinler nesnesini oluşturduktan ve depoladikten sonra, aşağıdaki **New-QuarantineTag** komutunda _EndUserQuarantinePermission_ parametre değeri için değişkeni kullanın:

```powershell
New-QuarantineTag -Name "<UniqueName>" -EndUserQuarantinePermissions $<VariableName>
```

Bu örnek, önceki adımda açıklanan ve oluşturulan izin nesnesini kullanarak LimitedAccess `$LimitedAccess` adlı yeni bir karantina ilkesi oluşturur.

```powershell
New-QuarantineTag -Name LimitedAccess -EndUserQuarantinePermissions $LimitedAccess
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz [. Yeni Karantina Etiketi](/powershell/module/exchange/new-quarantinetag).

## <a name="step-2-assign-a-quarantine-policy-to-supported-features"></a>2. Adım: Desteklenen özelliklere karantina ilkesi atama

_İletileri veya_ dosyaları karantinaya alan (otomatik olarak veya yapılandırılabilir bir eylem olarak) desteklenen koruma özelliklerinde, kullanılabilir karantina eylemlerine bir karantina ilkesi atabilirsiniz. İletileri karantinaya alan özellikler ve karantina ilkelerinin kullanılabilirliği aşağıdaki tabloda açıklanmıştır:

<br>

****

|Özellik|Karantina ilkeleri destekli mi?|Kullanılan varsayılan karantina ilkeleri|
|---|:---:|---|
|[İstenmeyen posta önleme ilkeleri](configure-your-spam-filter-policies.md): <ul><li>**İstenmeyen** Posta (_spamAction_)</li><li>**Yüksek güven istenmeyen** posta (_HighConfidenceSpamAction_)</li><li>**Kimlik Avı** (_PhishSpamAction_)</li><li>**Yüksek güven kimlik avı** (_HighConfidencePhishAction_)</li><li>**Toplu** (_BulkSpamAction_)</li></ul>|Evet|<ul><li>DefaultSpamTag (Tam erişim)</li><li>DefaultHighConfSpamTag (Tam erişim)</li><li>DefaultPhishTag (Tam erişim)</li><li>DefaultHighConfPhishTag (Erişim yok)</li><li>DefaultBulkTag (Tam erişim)</li></ul>
|Kimlik avı önleme ilkeleri: <ul><li>[Kimliksiz zeka koruması](set-up-anti-phishing-policies.md#spoof-settings) (_AuthenticationFailAction_)</li><li>[Kimliğe bürünme koruması](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365):<sup>\*</sup> <ul><li>**İleti kimliğine bürünülen bir kullanıcı olarak algılanırsa** (_TargetedUserProtectionAction_)</li><li>**İleti kimliğine bürünülen bir etki alanı** olarak algılanırsa (_TargetedDomainProtectionAction_)</li><li>**Posta kutusu zekası kimliğine bürünülen kullanıcı algılarsa** (_MailboxIntelligenceProtectionAction_)</li></ul></li></ul></ul>|Hayır|yok|
|[Kötü amaçlı yazılımdan koruma](configure-anti-malware-policies.md) ilkeleri: Tüm algılanan iletiler her zaman karantinaya alınır.|Hayır|yok|
|[Kasa, E-SharePoint, OneDrive için Ekleri Microsoft Teams](mdo-for-spo-odb-and-teams.md)|Hayır|yok|
|[Eylemle birlikte](/exchange/security-and-compliance/mail-flow-rules/mail-flow-rules) posta akışı kuralları (aktarım kuralları olarak da bilinir): **İletiyi** barındırılan karantinaya (Karantina) _teslim._|Hayır|yok|
|

<sup>\*</sup>Kimliğe bürünme koruma ayarları yalnızca kimlik avı önleme ilkeleri için Microsoft Defender'ın Office 365.

Varsayılan karantina ilkeleri tarafından sağlanan son kullanıcı izinlerini memnunsanız, hiçbir şey yapmaya gerek yok. Son kullanıcı istenmeyen posta bildirimlerinin veya karantinaya alınmış ileti ayrıntılarında son kullanıcı özelliklerini (kullanılabilir düğmeler) özelleştirmek için, özel karantina ilkesi atabilirsiniz.

### <a name="assign-quarantine-policies-in-anti-spam-policies-in-the-microsoft-365-defender-portal"></a>Microsoft 365 Defender portalında istenmeyen posta önleme ilkelerine karantina Microsoft 365 Defender atama

İstenmeyen posta önleme ilkelerini oluşturma ve değiştirme yönergelerinin tam yönergeleri [EOP'de istenmeyen posta önleme ilkelerini yapılandırma konusunda açıklanmıştır](configure-your-spam-filter-policies.md).

1. Microsoft 365 Defender portalında, **E-posta** ve **&-posta** \> & **kuralları** \> **İlkeleri** bölümüne \> gidin. Veya açın <https://security.microsoft.com/antispam>.

2. **İstenmeyen posta önleme ilkeleri** sayfasında, aşağıdaki adımlardan birini uygulayın:
   - Var olan bir istenmeyen posta **önleme ilkesi bulun** ve seçin.
   - Yeni bir istenmeyen **posta önleme** ilkesi oluşturun.

3. Aşağıdaki adımlardan birini yapın:
   - **Mevcut istenmeyen posta önleme ilkesi düzenleme**: İlke ayrıntıları ayrıntılarında Eylemler bölümüne gidin ve **Eylemleri** **düzenle'ye tıklayın**.
   - **Yeni istenmeyen posta önleme ilkesi oluşturma**: Yeni ilke sihirbazında, Eylemler **sayfasına** gidin.

4. Eylemler **sayfasında** . Karantina ileti eylemine **sahip olan her** kararda, ilgili karantina **ilkesi** seçmeniz için Karantinayı seç ilke kutusu da yer alır.

   **Not**: Yeni bir ilke seniz, boş bir Karantina ilkesi  seçin değeri, bu karar için varsayılan karantina ilkesi olduğunu gösterir. İlkeyi daha sonra düzenleyseniz, boş değerlerin yerini önceki tabloda açıklandığı gibi asıl varsayılan karantina ilkesi adları alır.

   ![İstenmeyen posta önleme ilkesinde karantina ilkesi seçimleri](../../media/quarantine-tags-in-anti-spam-policies.png)

5. Bitirdiğinizde, **Kaydet**'i tıklatın.

#### <a name="assign-quarantine-policies-in-anti-spam-policies-in-powershell"></a>PowerShell'de istenmeyen posta önleme ilkelerine karantina ilkeleri atama

İstenmeyen posta önleme ilkelerde karantina ilkeleri atamak için PowerShell kullanmayı tercih ediyorsanız, Exchange Online PowerShell'e veya PowerShell'Exchange Online Protection aşağıdaki söz dizimlerini kullanın:

```powershell
<New-HostedContentFilterPolicy -Name "<Unique name>" | Set-HostedContentFilterPolicy -Identity "<Policy name>">  [-SpamAction Quarantine] [-SpamQuarantineTag <QuarantineTagName>] [-HighConfidenceSpamAction Quarantine] [-HighConfidenceSpamQuarantineTag <QuarantineTagName>] [-PhishSpamAction Quarantine] [-PhishQuarantineTag <QuarantineTagName>] [-HighConfidencePhishQuarantineTag <QuarantineTagName>] [-BulkSpamAction Quarantine] [-BulkQuarantineTag <QuarantineTagName>] ...
```

**Notlar**:

- _HighConfidencePhishAction_ parametresi için varsayılan değer Karantina'dır, dolayısıyla yeni istenmeyen posta önleme ilkelerde yüksek güveni olan kimlik avı algılamaları için Karantina eylemlerini ayarlamanız gerekli değildir. Yeni veya mevcut istenmeyen posta önleme ilkeleriyle ilgili diğer tüm istenmeyen posta filtreleme kararlarında, karantina ilkesi ancak eylem değeri Karantina ise geçerli olur. Var olan istenmeyen posta önleme ilkelerde eylem değerlerini görmek için, aşağıdaki komutu çalıştırın:

  ```powershell
  Get-HostedContentFilterPolicy | Format-Table Name,*SpamAction,HighConfidencePhishAction
  ```

  Varsayılan eylem değerleri ve Standart ve Katı için önerilen eylem değerleri hakkında bilgi için bkz. [EOP istenmeyen posta önleme ilkesi ayarları](recommended-settings-for-eop-and-office365.md#eop-anti-spam-policy-settings).

- İstenmeyen posta filtreleme kararını ilgili karantina ilkesi parametresi olmadan almak [, o karar](#step-2-assign-a-quarantine-policy-to-supported-features) için varsayılan karantina ilkesi kullanılacak anlamına gelir.

  Karantinaya alınmış iletilerde varsayılan son kullanıcı özelliklerini değiştirmek için, varsayılan karantina ilkesi yerine özel karantina ilkesi değiştirmeniz gerekir.

- PowerShell'de yeni istenmeyen posta önleme ilkesi, **New-HostedContentFilterPolicy** cmdlet'ini ve **New-HostedContentFilterRule** cmdlet'ini kullanarak yeni bir istenmeyen posta filtresi ilkesi (alıcı filtreleri) gerektirir. Yönergeler için bkz [. PowerShell kullanarak istenmeyen posta önleme ilkeleri oluşturma](configure-your-spam-filter-policies.md#use-powershell-to-create-anti-spam-policies).

Bu örnekte, Research Department adlı yeni bir istenmeyen posta filtresi ilkesi aşağıdaki ayarlarla oluşturur:

- Tüm istenmeyen posta filtreleme kararlarını içeren eylem Karantina'ya ayarlanır.
- Hiçbir erişim izni atamamış olan NoAccess adlı özel  karantina ilkesi, varsayılan olarak Erişim izni yok atamayacağınız tüm varsayılan **karantina ilkelerinin** yerini almaktadır.

```powershell
New-HostedContentFilterPolicy -Name Research Department -SpamAction Quarantine -SpamQuarantineTag NoAccess -HighConfidenceSpamAction Quarantine -HighConfidenceSpamQuarantineTag NoAction -PhishSpamAction Quarantine -PhishQuarantineTag NoAction -BulkSpamAction Quarantine -BulkQuarantineTag NoAccess
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [New-HostedContentFilterPolicy](/powershell/module/exchange/new-hostedcontentfilterpolicy).

Bu örnekte, İnsan Kaynakları adlı mevcut istenmeyen posta filtresi ilkesinde değişiklik yapılan bir değişiklik vardır. İstenmeyen posta karantina kararının eylemi Karantina olarak ayarlanır ve NoAccess adlı özel karantina ilkesi atanır.

```powershell
Set-HostedContentFilterPolicy -Identity "Human Resources" -SpamAction Quarantine -SpamQuarantineTag NoAccess
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [Set-HostedContentFilterPolicy](/powershell/module/exchange/set-hostedcontentfilterpolicy).

## <a name="configure-global-quarantine-notification-settings-in-the-microsoft-365-defender-portal"></a>E-posta portalında genel karantina Microsoft 365 Defender yapılandırma

Karantina ilkelerine yönelik genel ayarlar, karantinaya alınmış iletilerin alıcılarına gönderilen son kullanıcı istenmeyen posta bildirimlerini özelleştirmenizi sağlar. Bu bildirimler hakkında daha fazla bilgi için bkz. [Son kullanıcı istenmeyen posta bildirimleri](use-spam-notifications-to-release-and-report-quarantined-messages.md).

1. Microsoft 365 Defender portalında E-posta ve İşbirliği **&** \> tehdit ilkeleri **Kuralları** \>  \> bölümünde Karantina ilkeleri bölümüne gidin ve **sonra Karantina** **ilkeleri'ne tıklayın**.

2. Karantina ilkesi **sayfasında Genel** **ayarlar'ı seçin**.

3. Açılan **Karantina bildirim ayarları** açılır sayfasında, aşağıdaki ayarların bir birini veya hepsini yapılandırabilirsiniz:

   - **Görünen ad**: Son kullanıcı istenmeyen posta bildirimlerde kullanılan gönderenin görünen adını özelleştirin.

     Ekley istediğiniz her dil için, ikinci dil kutusunda dili seçin (X'e tıklayın) ve Görünen ad kutusuna istediğiniz **metin değerini** girin.

     Aşağıdaki ekran görüntüsü, son kullanıcı istenmeyen posta bildiriminde özelleştirilmiş görünen adı gösterir:

     ![Son kullanıcı istenmeyen posta bildiriminde özelleştirilmiş bir gönderen görünen adı](../../media/quarantine-tags-esn-customization-display-name.png)

   - **Yasal Uyarı**: Son kullanıcı istenmeyen posta bildirimlerinin altına özel bir bildirim ekleyin. Yerelleştirilmiş metin **(Bir kuruluştan uyarı:** her zaman önce yer alan ve sizin belirttiğiniz metinden sonra gelen uyarıdır).

     Ekley istediğiniz her dil için, ikinci dil kutusunda dili seçin (X'e tıklayın) ve Yasal Uyarı kutusuna **istediğiniz metin değerini** girin.

     Aşağıdaki ekran görüntüsü, son kullanıcı istenmeyen posta bildiriminde özelleştirilmiş bildirimi gösterir:

     ![Son kullanıcı istenmeyen posta bildiriminin altında özel bir bildirim](../../media/quarantine-tags-esn-customization-disclaimer.png)

   - **Dili seçin**: Alıcının dil ayarlarına bağlı olarak son kullanıcı istenmeyen posta bildirimleri zaten yerelleştirilmiştir. Görünen ad ve Yasal Uyarı değerleri için farklı dillerde **özelleştirilmiş** **metinler belirtebilirsiniz** .

     İlk dil kutusundan en az bir dil seçin ve Ekle'ye **tıklayın**. Her dilin ardından Ekle'ye tıklayarak **birden çok** dil seçin. Bölüm dili kutusunda seçtiğiniz tüm diller görüntülenir:

     ![Karantina ilkelerinin genel karantina bildirim ayarlarında ikinci dil kutusunda seçilen diller](../../media/quarantine-tags-esn-customization-selected-languages.png)

   - **Şirket logosunu kullan**: Son kullanıcı istenmeyen posta bildirimlerinin en üstünde varsayılan Microsoft logosunu değiştirmek için bu seçeneği belirtin. Bunu yapmak için, Özel logonuzu yüklemek üzere Microsoft 365 için Özel [tema'da](../../admin/setup/customize-your-organization-theme.md) verilen yönergeleri izleyebilirsiniz.

     Aşağıdaki ekran görüntüsü, son kullanıcı istenmeyen posta bildiriminde özel bir logoyu gösterir:

     ![Son kullanıcı istenmeyen posta bildiriminde özel logo](../../media/quarantine-tags-esn-customization-logo.png)

## <a name="view-quarantine-policies-in-the-microsoft-365-defender-portal"></a>Microsoft 365 Defender portalında karantina Microsoft 365 Defender görüntüleme

1. Microsoft 365 Defender portalında E-posta ve İşbirliği **&** \> tehdit ilkeleri **Kuralları** \>  \> bölümünde Karantina ilkeleri bölümüne gidin ve **sonra Karantina** **ilkeleri'ne tıklayın**.

2. Karantina **ilkesi sayfasında** , Ad ve Son güncelleştirme **tarihine göre** **ilkeler listesi** görüntülenir.

3. Yerleşik veya özel karantina ilkelerinin ayarlarını görüntülemek için, adı tıklatarak listeden karantina ilkesi seçin.

4. Genel ayarları görüntülemek için Genel **ayarlar'a tıklayın**.

### <a name="view-quarantine-policies-in-powershell"></a>PowerShell'de karantina ilkelerini görüntüleme

Karantina ilkelerini görüntülemek için PowerShell kullanmayı tercih ediyorsanız, aşağıdaki adımlardan birini uygulayın:

- Tüm yerleşik veya özel ilkelerin özet listesini görüntülemek için, aşağıdaki komutu çalıştırın:

  ```powershell
  Get-QuarantineTag | Format-Table Name
  ```

- Yerleşik veya özel karantina ilkelerinin ayarlarını görüntülemek için, \<QuarantinePolicyName\> karantina ilkesi adıyla değiştirin ve aşağıdaki komutu çalıştırın:

  ```powershell
  Get-QuarantineTag -Identity "<QuarantinePolicyName>"
  ```

- Genel ayarları görüntülemek için aşağıdaki komutu çalıştırın:

  ```powershell
  Get-QuarantineTag -QuarantineTagType GlobalQuarantineTag
  ```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [Get-HostedContentFilterPolicy](/powershell/module/exchange/get-hostedcontentfilterpolicy).

## <a name="modify-quarantine-policies-in-the-microsoft-365-defender-portal"></a>Microsoft 365 Defender portalında karantina Microsoft 365 Defender değiştirme

1. Microsoft 365 Defender portalında E-posta ve İşbirliği **&** \> tehdit ilkeleri **Kuralları** \>  \> bölümünde Karantina ilkeleri bölümüne gidin ve **sonra Karantina** **ilkeleri'ne tıklayın**.

2. Karantina **ilkeleri sayfasında** , adına tıklayarak ilkeyi seçin.

3. İlkeyi seçdikten sonra, görüntülenen İlkeyi ![düzenle **simgesine**](../../media/m365-cc-sc-edit-icon.png) tıklayın.

4. Açılan **İlkeyi** düzenle sihirbazı, bu makalenin önceki  kısımlarında yer alan Microsoft 365 Defender [portalında](#step-1-create-quarantine-policies-in-the-microsoft-365-defender-portal) karantina ilkeleri oluşturma bölümünde açıklanan Yeni ilke sihirbazıyla hemen hemen aynıdır.

   En önemli fark, mevcut bir ilkeyi yeniden adlandırılamaz.

5. İlkeyi değiştirmeyi bitirdikten sonra, Özet sayfasına gidin **ve** Gönder'e **tıklayın**.

### <a name="modify-quarantine-policies-in-powershell"></a>PowerShell'de karantina ilkelerini değiştirme

Özel karantina ilkesinde değişiklik yapmak için PowerShell kullanmayı tercih ediyorsanız, \<QuarantinePolicyName\> karantina ilkesi adıyla değiştirin ve aşağıdaki söz dizimlerini kullanın:

```powershell
Set-QuarantineTag -Identity "<QuarantinePolicyName>" [Settings]
```

Kullanılabilir ayarlar, bu makalenin önceki sayfalarında açıklanan karantina ilkelerini oluşturmada açıklananla aynıdır.

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [Set-Karantina Etiketi](/powershell/module/exchange/set-quarantinetag).

## <a name="remove-quarantine-policies-in-the-microsoft-365-defender-portal"></a>Kullanıcı portalında karantina Microsoft 365 Defender kaldırma

**Notlar**:

- Yerleşik karantina ilkelerini kaldırasınız.
- Özel karantina ilkesi kaldırmadan önce, bu ilkenin kullanılmadı olduğunu doğrulayın. Örneğin, PowerShell'de aşağıdaki komutu çalıştırın:

  ```powershell
  Get-HostedContentFilterPolicy | Format-List Name,*QuarantineTag
  ```

  Karantina ilkesi kullanılıyorsa, [kaldırmadan önce atanmış karantina](#step-2-assign-a-quarantine-policy-to-supported-features) ilkesiyle değiştirin.

1. Microsoft 365 Defender portalında E-posta ve İşbirliği **&** \> tehdit ilkeleri **Kuralları** \>  \> bölümünde Karantina ilkeleri bölümüne gidin ve **sonra Karantina** **ilkeleri'ne tıklayın**.

2. Karantina **ilkesi sayfasında** , adına tıklayarak kaldırmak istediğiniz özel karantina ilkesine tıklayın.

3. İlkeyi seçin ve görüntülenen İlkeyi ![sil **simgesine**](../../media/m365-cc-sc-delete-icon.png) tıklayın.

4. Görüntülenen **onay iletişim kutusunda** İlkeyi kaldır'a tıklayın.

### <a name="remove-quarantine-policies-in-powershell"></a>PowerShell'de karantina ilkelerini kaldırma

Özel karantina ilkesi kaldırmak için PowerShell kullanmayı tercih ediyorsanız, \<QuarantinePolicyName\> karantina ilkesi adıyla değiştirin ve aşağıdaki komutu çalıştırın:

```powershell
Remove-QuarantineTag -Identity "<QuarantinePolicyName>"
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [Karantina Etiketini Kaldırma](/powershell/module/exchange/remove-quarantinetag).

## <a name="quarantine-policy-permission-details"></a>Karantina ilkesi izin ayrıntıları

Aşağıdaki bölümlerde önceden ayarlanmış izin gruplarının ve karantinaya alınmış iletilerin ayrıntılarında ve son kullanıcı istenmeyen posta bildirimlerinin ayrıntılarında tek tek izinlerin etkileri açıklanmaktadır.

### <a name="preset-permissions-groups"></a>Önceden ayarlanmış izin grupları

Önceden ayarlanmış izin gruplarına dahil edilen tek tek izinler, bu makalenin başındaki tabloda listelenir.

#### <a name="no-access"></a>Erişim yok

Karantina ilkesi Erişim izni yok (izin **yok** ) ataıyorsa, kullanıcılar yine de bazı temel özelliklerine sahip olur:

- **Karantinaya alınmış ileti ayrıntıları**: **İleti üst bilgilerini görüntüle** düğmesi her zaman kullanılabilir.

  ![Karantina ilkesi kullanıcıya Erişim izni yok izni veriyorsa, karantinaya alınan ileti ayrıntılarında kullanılabilir düğmeler](../../media/quarantine-tags-quarantined-message-details-no-access.png)

- **Son kullanıcı istenmeyen posta bildirimleri**: **Karantinada** bulunan bir iletiye kullanıcıyı alan Gözden Geçir düğmesi her zaman kullanılabilir.

  ![Karantina ilkesi kullanıcıya Erişim izni yok izni veriyorsa, son kullanıcı istenmeyen posta bildiriminde kullanılabilir düğmeler](../../media/quarantine-tags-esn-no-access.png)

#### <a name="limited-access"></a>Sınırlı erişim

Karantina ilkesi Sınırlı erişim izinleri **atarsa** , kullanıcılar aşağıdaki özelliklere sahip olur:

- **Karantinaya alınmış ileti** ayrıntıları: Aşağıdaki düğmeler kullanılabilir:
  - **Sürüm isteği**
  - **İleti üst bilgilerini görüntüleme**
  - **İletiyi önizleme**
  - **Göndereni engelle**
  - **Karantinadan kaldırma**

  ![Karantina ilkesi kullanıcıya Sınırlı erişim izinleri veriyorsa, karantinaya alınan ileti ayrıntılarında kullanılabilir düğmeler](../../media/quarantine-tags-quarantined-message-details-limited-access.png)

- **Son kullanıcı istenmeyen posta bildirimleri**: Aşağıdaki düğmeler kullanılabilir:
  - **Göndereni engelle**
  - **Gözden Geçir**

  ![Karantina ilkesi kullanıcıya Sınırlı erişim izinleri veriyorsa, son kullanıcı istenmeyen posta bildiriminde kullanılabilir düğmeler](../../media/quarantine-tags-esn-limited-access.png)

#### <a name="full-access"></a>Tam erişim

Karantina ilkesi Tam erişim izinleri ( **tüm kullanılabilir** izinler) atarsa, kullanıcılar aşağıdaki özelliklere sahip olur:

- **Karantinaya alınmış ileti** ayrıntıları: Aşağıdaki düğmeler kullanılabilir:
  - **Sürüm iletisi**
  - **İleti üst bilgilerini görüntüleme**
  - **İletiyi önizleme**
  - **Göndereni engelle**
  - **Gönderene izin ver**
  - **Karantinadan kaldırma**

  ![Karantina ilkesi kullanıcıya Tam erişim izinleri veriyorsa, karantinaya alınan ileti ayrıntılarında kullanılabilir düğmeler](../../media/quarantine-tags-quarantined-message-details-full-access.png)

- **Son kullanıcı istenmeyen posta bildirimleri**: Aşağıdaki düğmeler kullanılabilir:
  - **Göndereni engelle**
  - **Sürüm**
  - **Gözden Geçir**

  ![Karantina ilkesi kullanıcıya Tam erişim izinleri veriyorsa, son kullanıcı istenmeyen posta bildiriminde kullanılabilir düğmeler](../../media/quarantine-tags-esn-full-access.png)

### <a name="individual-permissions"></a>Tek tek izinler

> [!NOTE]
> Kullanıcıların her zaman Erişim yok bölümünde açıklanan düğmeleri [al olduğunu](#no-access) unutmayın. Bu düğmeler tek tek izin açıklamalarında yerlanmaz.

#### <a name="allow-sender-permission"></a>Gönderen iznine izin ver

Gönderen **iznine** izin ver (_PermissionToAllowSender_) kullanıcıların karantinaya alınmış ileti göndereni kendi Kullanıcı Listesi'ne rahatça eklemelerine olanak sağlayan Kasa denetimler.

- **Karantinaya alınmış ileti ayrıntıları**:
  - **Gönderen iznine** izin ver etkin: **Gönderene izin ver** düğmesi kullanılabilir.
  - **Gönderen iznine** izin ver devre dışı: **Gönderene izin ver** düğmesi kullanılamıyor.

- **Son kullanıcı istenmeyen posta bildirimleri**: Hiçbir etkisi yoktur.

Güvenilir Gönderenler listesi Kasa fazla bilgi için bkz. Güvenilen gönderenlerin engellenmiş iletiyi engelleme ve posta kutusunda güvenilir liste koleksiyonunu yapılandırmak için [Exchange Online PowerShell kullanma](configure-junk-email-settings-on-exo-mailboxes.md#use-exchange-online-powershell-to-configure-the-safelist-collection-on-a-mailbox).[](https://support.microsoft.com/office/274ae301-5db2-4aad-be21-25413cede077#__toc304379666)

#### <a name="block-sender-permission"></a>Gönderen iznini engelleme

Gönderen **iznini** engelle (_PermissionToBlockSender_) kullanıcıların karantinaya alınmış ileti gönderenini Engellenen Gönderenler listesine rahatça eklemelerine olanak sağlayan düğmeye erişimi denetimler.

- **Karantinaya alınmış ileti ayrıntıları**:
  - **Gönderen iznini** engelleme etkin: **Göndereni engelle** düğmesi kullanılabilir.
  - **Gönderen iznini** engelleme devre dışı **bırakıldı: Göndereni engelle** düğmesi kullanılamaz.

- **Son kullanıcı istenmeyen posta bildirimleri**:
  - **Gönderen iznini** engelleme devre dışı **bırakıldı: Göndereni engelle** düğmesi kullanılamaz.
  - **Gönderen iznini** engelleme etkin: **Göndereni engelle** düğmesi kullanılabilir.

Engellenen Gönderenler listesi hakkında daha fazla bilgi için bkz. Birilerinden gelen iletileri engelleme [](https://support.microsoft.com/office/274ae301-5db2-4aad-be21-25413cede077#__toc304379667) ve [posta kutusunda güvenilir liste koleksiyonunu yapılandırmak için Exchange Online PowerShell kullanma](configure-junk-email-settings-on-exo-mailboxes.md#use-exchange-online-powershell-to-configure-the-safelist-collection-on-a-mailbox).

#### <a name="delete-permission"></a>Silme izni

Delete **izni** (_PermissionToDelete_) kullanıcıların iletilerini (kullanıcının alıcı olduğu iletileri) karantinadan silebilir.

- **Karantinaya alınmış ileti ayrıntıları**:
  - **silme** izni etkin: **Karantinadan kaldır** düğmesi kullanılabilir.
  - **silme** izni devre dışı: **Karantinadan kaldır** düğmesi kullanılamaz.

- **Son kullanıcı istenmeyen posta bildirimleri**: Hiçbir etkisi yoktur.

#### <a name="preview-permission"></a>Önizleme izni

Önizleme **izni** (_PermissionToPreview_), kullanıcıların iletilerini karantinada önizleme olanağını kontrol eder.

- **Karantinaya alınmış ileti ayrıntıları**:
  - **Önizleme** izni etkin: **Önizleme iletisi** düğmesi kullanılabilir.
  - **Önizleme** izni devre dışı: **İletiyi önizleme** düğmesi kullanılamıyor.

- **Son kullanıcı istenmeyen posta bildirimleri**: Hiçbir etkisi yoktur.

#### <a name="allow-recipients-to-release-a-message-from-quarantine-permission"></a>Alıcıların iletiyi karantina izninden çıkartırmalarına izin verme

**Alıcıların iletiyi** karantina izninden (_PermissionToRelease_) çıkarabilmeleri, kullanıcıların karantinaya alınmış iletilerini doğrudan ve yöneticinin onayı olmadan serbest bırakmasını sağlar.

- **Karantinaya alınmış ileti ayrıntıları**:
  - İzin etkinleştirildi: **İletiyi** bırak düğmesi kullanılabilir.
  - İzin devre dışı bırakıldı: **İletiyi** bırak düğmesi kullanılamıyor.

- **Son kullanıcı istenmeyen posta bildirimleri**:
  - İzin etkinleştirildi: **Sürüm** düğmesi kullanılabilir.
  - İzin devre dışı bırakıldı: **Sürüm** düğmesi kullanılamıyor.

#### <a name="allow-recipients-to-request-a-message-to-be-released-from-quarantine-permission"></a>Alıcıların bir iletiyi karantina izninden çıkarıılın isteğine izin ver

**Alıcıların karantina** izninden çıkarılmazken bir ileti talep etmelerine izin ver (_PermissionToRequestRelease_), kullanıcıların karantinaya alınmış iletilerinin  serbest bırakılmaz isteği göndermesini sağlar. İleti ancak yönetici isteği onaylar sonra serbest olur.

- **Karantinaya alınmış ileti ayrıntıları**:
  - İzin etkinleştirildi: **Sürüm isteği** düğmesi kullanılabilir.
  - İzin devre dışı bırakıldı: **Sürüm isteği** düğmesi kullanılamıyor.

- **Son kullanıcı istenmeyen posta bildirimleri**: **Sürüm** düğmesi kullanılamaz.
