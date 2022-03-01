---
title: Posta kutusu denetimini yönetme
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: aaca8987-5b62-458b-9882-c28476a66918
ms.custom:
- seo-marvel-apr2020
- admindeeplinkEXCHANGE
description: Microsoft 365'da posta kutusu denetim günlüğü varsayılan olarak açıktır (varsayılan posta kutusu denetimi veya posta kutusu denetimi varsayılan olarak açık olarak da denir). Bu, posta kutusu sahipleri, temsilciler ve yöneticiler tarafından gerçekleştirilen bazı eylemlerin posta kutusu denetim günlüğüne otomatik olarak günlüğe kaydedileceğini ve burada posta kutusunda gerçekleştirilen etkinlikleri arayabilirsiniz.
ms.openlocfilehash: 957e0a00a480746d6a70bf70ee02d725f43194f8
ms.sourcegitcommit: 986ea76ecaceb5fe6b9616e553003e3c5b0df2e7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/25/2022
ms.locfileid: "63010802"
---
# <a name="manage-mailbox-auditing"></a>Posta kutusu denetimini yönetme

Ocak 2019'dan başlayarak, Microsoft tüm kuruluşlarda posta kutusu denetim günlüğünü varsayılan olarak etkinleştirdi. Bu, posta kutusu sahipleri, temsilciler ve yöneticiler tarafından gerçekleştirilen bazı eylemlerin otomatik olarak günlüğe kaydedileceğini ve posta kutusu denetim günlüğünde ilgili posta kutusu denetim kayıtlarını arayabilirsiniz. Posta kutusu denetimi varsayılan olarak açıkken, önce bunu organizasyonu tüm kullanıcı posta kutuları için el ile etkinleştirmeniz gerekmektedir.

Posta kutusu denetiminin varsayılan olarak bazı avantajları:

- Yeni bir posta kutusu etkinleştirilmiş durumdayken denetim otomatik olarak etkinleştirilir. Yeni kullanıcılar için el ile etkinleştirmeniz gerekmez.
- Denetlenen posta kutusu eylemlerini yönetmenize gerek yoktur. Her oturum açma türü için varsayılan olarak önceden tanımlanmış posta kutusu eylemleri kümesi denetlenr (Yönetici, Temsilci ve Sahip).
- Microsoft yeni bir posta kutusu eylemi yayımlasa da, bu eylem varsayılan olarak denetlenen posta kutusu eylemleri listesine otomatik olarak eklenebilir (uygun lisansa sahip kullanıcıya tabi olabilir). Bu, posta kutularına yeni eylemler ekleme eylemlerini izlemek zorunda olmadığınız anlamına gelir.
- Tüm posta kutuları için aynı eylemleri denetlederek, tüm kuruluş genelinde tutarlı bir posta kutusu denetim ilkeniz vardır.

> [!NOTE]
>
> - Posta kutusu denetiminin varsayılan olarak açık bırak açısından anımsanacak önemli bir konu şudur: Posta kutusu denetimini yönetmek için hiçbir şey yapmaya gerek yoktur. Bununla birlikte, daha fazla bilgi edinmek, varsayılan ayarlardan posta kutusu denetimini özelleştirmek veya tamamen kapatmak için bu makale size yardımcı olabilir.
> - Varsayılan olarak, E5 kullanıcıları için yalnızca E5 kullanıcıları için posta kutusu denetim olayları Microsoft 365 uyumluluk merkezi Yönetim Etkinliği API'sinde veya Office 365 günlüğü aramalarında kullanılabilir. Daha fazla bilgi için, bu [makalenin Daha fazla](#more-information) bilgi bölümüne bakın.

## <a name="verify-mailbox-auditing-on-by-default-is-turned-on"></a>Posta kutusu denetiminin varsayılan olarak açık olduğunu doğrulama

Kuruluşlarınız için posta kutusu denetiminin varsayılan olarak açık olduğunu doğrulamak için, [Exchange Online PowerShell'de çalıştırın](/powershell/exchange/connect-to-exchange-online-powershell):

```PowerShell
Get-OrganizationConfig | Format-List AuditDisabled
```

False değeri **,** kuruluşta posta kutusu denetiminin varsayılan olarak etkinleştirildiğinden emin olduğunu gösterir. Bu ayar, varsayılan olarak kuruluş değeriyle belirli posta kutulerinde posta kutusu denetim ayarını geçersiz kılar. Örneğin, bir posta kutusu için posta kutusu denetimi devre dışı bırakılmışsa ( *posta kutusunda AuditEnabled* özelliği **False** olduğunda), kuruluşta posta kutusu denetimi varsayılan olarak etkinleştirildiğinden posta kutusu için varsayılan posta kutusu eylemleri yine de denetlenecek.

Belirli posta kutularında posta kutusu denetiminin devre dışı bırakıldığından emin olmak için, posta kutusu sahibi ve posta kutusuna erişim temsilciliği olan diğer kullanıcılar için posta kutusu denetimi atlama ayarlarını yapılandırabilirsiniz. Daha fazla bilgi için, bu [makalenin Posta kutusu denetim günlüğünü atlama](#bypass-mailbox-audit-logging) bölümüne bakın.

> [!NOTE]
> Kuruluşta posta kutusu denetimi varsayılan olarak açık olduğunda, etkilenen posta kutuları için *AuditEnabled* özelliği **Yanlış** olan True **olarak değişmez.** Başka bir deyişle, posta kutusu denetiminde varsayılan olarak posta kutusu denetimi, posta kutularında *AuditEnabled* özelliğini yok sayar.

## <a name="supported-mailbox-types"></a>Desteklenen posta kutusu türleri

Aşağıdaki tabloda, şu anda posta kutusu denetimi tarafından varsayılan olarak desteklenen posta kutusu türleri yer alır:

<br>

****

|Posta kutusu türü|Destekleniyor|
|---|:---:|
|Kullanıcı posta kutuları|![Onay işareti.](../media/checkmark.png)|
|Paylaşılan posta kutuları|![Onay işareti.](../media/checkmark.png)|
|Microsoft 365 Posta kutularını grupla|![Onay işareti.](../media/checkmark.png)|
|Kaynak posta kutuları||
|Ortak klasör posta kutuları||
|

## <a name="logon-types-and-mailbox-actions"></a>Oturum açma türleri ve posta kutusu eylemleri

Oturum açma türleri, posta kutusunda denetlenen eylemleri gerçekleştiren kullanıcıya sınıf sağlar. Aşağıdaki listede, posta kutusu denetim günlüğünde kullanılan oturum açma türleri açık almaktadır:

- **Sahip**: Posta kutusu sahibi (posta kutusuyla ilişkilendirilmiş olan hesap).
- **Temsilci**:
  - Başka bir posta kutusuna SendAs, SendOnBehalf veya FullAccess izni atanan bir kullanıcı.
  - Kullanıcının posta kutusuna FullAccess izni atanmış olan yönetici.
- **Yönetici**:
  - Posta kutusunda aşağıdaki Microsoft eBulma araçlarından biri ile arama yapın:
    - Uyumluluk Merkezi'nde İçerik Arama.
    - eKbulma veya Advanced eDiscovery Merkezi'nde eKbulma veya Uyumluluk Merkezi'ne eBulma.
    - In-Place'da eBulma'Exchange Online.
  - Posta kutusuna MAPI Düzenleyicisi'Microsoft Exchange Server erişilir.

### <a name="mailbox-actions-for-user-mailboxes-and-shared-mailboxes"></a>Kullanıcı posta kutuları ve paylaşılan posta kutuları için posta kutusu eylemleri

Aşağıdaki tabloda, kullanıcı posta kutuları ve paylaşılan posta kutuları için posta kutusu denetim günlüğünde kullanılabilen posta kutusu eylemleri açık almaktadır.

- Onay işareti (![Onay işareti.](../media/checkmark.png)) oturum açma türü için posta kutusu eyleminin günlüğe kaydedileceğini gösterir (tüm eylemler tüm oturum açma türlerinde kullanılamaz).
- Onay işareti okundan sonra gelen yıldız işareti ( <sup>\*</sup> ), oturum açma türü için posta kutusu eyleminin varsayılan olarak günlüğe kaydedileceğini gösterir.
- Posta kutusuna Tam Erişim izni olan bir yöneticinin temsilci olarak kabul edilir.

<br>

****

|Posta kutusu eylemi|Açıklama|Yönetici|Temsilci|Sahip|
|---|---|:---:|:---:|:---:|
|**AddFolderPermissions**|Bu değer posta kutusu eylemi olarak kabul edilse de, **UpdateFolderPermissions** eylemine zaten eklidir ve ayrı olarak denetlenz. Başka bir deyişle, bu değeri kullanmayın.||||
|**ApplyRecord**|Öğe kayıt olarak etiketlenmiş.|![Onay işareti.](../media/checkmark.png)<sup>\*</sup>|![Onay işareti.](../media/checkmark.png)<sup>\*</sup>|![Onay işareti.](../media/checkmark.png)<sup>\*</sup>|
|**Kopyala**|İleti başka bir klasöre kopyalandı.|![Onay işareti.](../media/checkmark.png)|||
|**Oluştur**|Posta kutusunun Takvim, Kişiler, Notlar veya Görevler klasöründe bir öğe oluşturulmuş olabilir (örneğin, yeni bir toplantı isteği oluşturulur). İleti oluşturma, gönderme veya alma denetlenz. Ayrıca, posta kutusu klasörü oluşturma denetlenz.|![Onay işareti.](../media/checkmark.png)<sup>\*</sup>|![Onay işareti.](../media/checkmark.png)<sup>\*</sup>|![Onay işareti.](../media/checkmark.png)|
|**FolderBind**|Bir posta kutusu klasörüne erişildi. Yönetici veya temsilci posta kutusunu açtığında da bu eylem günlüğe kaydedilir. <br/><br/> **Not**: Temsilciler tarafından gerçekleştirilen klasör bağlama eylemleri için denetim kayıtları birleştirilmiştir. 24 saatlik bir süre içinde tek tek klasör erişimi için bir denetim kaydı oluşturulur.|![Onay işareti.](../media/checkmark.png)|![Onay işareti.](../media/checkmark.png)||
|**HardDelete**|İleti Kurtarılabilir Öğeler klasöründen temiz edildi.|![Onay işareti.](../media/checkmark.png)<sup>\*</sup>|![Onay işareti.](../media/checkmark.png)<sup>\*</sup>|![Onay işareti.](../media/checkmark.png)<sup>\*</sup>|
|**MailboxLogin**|Kullanıcı posta kutusunda oturum etti.|||![Onay işareti](../media/checkmark.png)|
|**MailItemsAccessed**|**Not**: Bu değer yalnızca E5 veya E5 Uyumluluk eklenti aboneliği kullanıcıları tarafından kullanılabilir. Daha fazla bilgi için bkz[. Gelişmiş Denetim'i Microsoft 365](set-up-advanced-audit.md). <p> Posta verilerine posta protokolleri ve istemciler tarafından erişilebilir.|![Onay işareti.](../media/checkmark.png)<sup>\*</sup>|![Onay işareti.](../media/checkmark.png)<sup>\*</sup>|![Onay işareti](../media/checkmark.png)<sup>\*</sup>|
|**MessageBind**|**Not**: Bu değer yalnızca E3 kullanıcıları için kullanılabilir (E5 veya E5 Uyumluluk eklenti abonelikleri olmayan kullanıcılar). <p> İleti önizleme bölmesinde görüntülendi veya yönetici tarafından açıldı.|![Onay işareti](../media/checkmark.png)|||
|**ModifyFolderPermissions**|Bu değer posta kutusu eylemi olarak kabul edilse de, **UpdateFolderPermissions** eylemine zaten eklidir ve ayrı olarak denetlenz. Başka bir deyişle, bu değeri kullanmayın.||||
|**Taşıma**|İleti başka bir klasöre taşınmış.|![Onay işareti.](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|
|**MoveToDeletedItems**|İleti silinmiştir ve Silinmiş Öğeler klasörüne taşınmış.|![Onay işareti.](../media/checkmark.png)<sup>\*</sup>|![Onay işareti.](../media/checkmark.png)<sup>\*</sup>|![Onay işareti](../media/checkmark.png)<sup>\*</sup>|
|**RecordDelete**|Kayıt olarak etiketlenmiş bir öğe otomatik olarak silinmiştir (Kurtarılabilir Öğeler klasörüne taşınmıştır). Kayıt olarak etiketlenmiş öğeler kalıcı olarak silinemez (Kurtarılabilir Öğeler klasöründen temizlenebilir).|![Onay işareti.](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|
|**RemoveFolderPermissions**|Bu değer posta kutusu eylemi olarak kabul edilse de, **UpdateFolderPermissions** eylemine zaten eklidir ve ayrı olarak denetlenz. Başka bir deyişle, bu değeri kullanmayın.||||
|**SearchQueryInitiated**|**Not**: Bu değer yalnızca E5 veya E5 Uyumluluk eklenti aboneliği kullanıcıları tarafından kullanılabilir. Daha fazla bilgi için bkz[. Gelişmiş Denetim'i Microsoft 365](set-up-advanced-audit.md). <p> Bir kişi Outlook de öğeleri aramak için Windows, Mac, iOS, Android veya Web üzerinde Outlook) ya da Windows 10 için Posta uygulamasını kullanır.|||![Onay işareti](../media/checkmark.png)|
|**Gönderin**|**Not**: Bu değer yalnızca E5 veya E5 Uyumluluk eklenti aboneliği kullanıcıları tarafından kullanılabilir. Daha fazla bilgi için bkz[. Gelişmiş Denetim'i Microsoft 365](set-up-advanced-audit.md). <p> Kullanıcı bir e-posta iletisi gönderir, bir e-posta iletisine yanıt gönderir veya e-posta iletisi iletir.|![Onay işareti.](../media/checkmark.png)<sup>\*</sup>||![Onay işareti](../media/checkmark.png)<sup>\*</sup>|
|**SendAs**|Farklı Gönder izni kullanılarak bir ileti gönderilmiştir. Bu, başka bir kullanıcının iletiyi, posta kutusu sahibinden geliyor gibi gönderdiği anlamına gelir.|![Onay işareti.](../media/checkmark.png)<sup>\*</sup>|![Onay işareti](../media/checkmark.png)<sup>\*</sup>||
|**SendOnBehalf**|SendOnBehalf izni kullanılarak bir ileti gönderilmiştir. Bu, başka bir kullanıcının iletiyi posta kutusu sahibi adına gönderdiği anlamına gelir. İleti, iletinin kimin adına gönderildiğini ve aslında kim tarafından gönderildiğini alıcıya gösterir.|![Onay işareti.](../media/checkmark.png)<sup>\*</sup>|![Onay işareti](../media/checkmark.png)<sup>\*</sup>||
|**SoftDelete**|İleti kalıcı olarak silinmiştir veya Silinmiş Öğeler klasöründen silinmiştir. Otomatik olarak silinen öğeler Kurtarılabilir Öğeler klasörüne taşınır.|![Onay işareti.](../media/checkmark.png)<sup>\*</sup>|![Onay işareti.](../media/checkmark.png)<sup>\*</sup>|![Onay işareti](../media/checkmark.png)<sup>\*</sup>|
|**Güncelleştirme**|İleti veya özellikleri değiştirilmiştir.|![Onay işareti.](../media/checkmark.png)<sup>\*</sup>|![Onay işareti.](../media/checkmark.png)<sup>\*</sup>|![Onay işareti](../media/checkmark.png)<sup>\*</sup>|
|**UpdateCalendarDelegation**|Bir takvim temsilcisi posta kutusuna atanmıştır. Takvim temsilcisi, aynı kuruluşta yer alan başka birine posta kutusu sahibinin takvimini yönetme izni verir.|![Onay işareti.](../media/checkmark.png)<sup>\*</sup>||![Onay işareti](../media/checkmark.png)<sup>\*</sup>|
|**UpdateComplianceTag**|Posta bir öğeye farklı bir bekletme etiketi uygulanır (öğeye yalnızca bir bekletme etiketi atanmış olabilir).|![Onay işareti.](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|
|**UpdateFolderPermissions**|Klasör izni değiştirildi. Klasör izinleri, bir posta kutusu içinde yer alan klasörlere ve bu klasörlerde yer alan iletilere, kuruluşta hangi kullanıcıların eriş erişeni kontrol edin.|![Onay işareti.](../media/checkmark.png)<sup>\*</sup>|![Onay işareti.](../media/checkmark.png)<sup>\*</sup>|![Onay işareti](../media/checkmark.png)<sup>\*</sup>|
|**UpdateInboxRules**|Gelen kutusu kuralı eklendi, kaldırıldı veya değiştirildi. Gelen Kutusu kuralları, belirtilen koşulları temel alarak kullanıcının Gelen Kutusu'na iletileri işlemeye ve bir kuralın koşullarına uyul olduğunda, iletiyi belirtilen klasöre taşıma veya bir iletiyi silme gibi eylemler yapmak için kullanılır.|![Onay işareti.](../media/checkmark.png)<sup>\*</sup>|![Onay işareti](../media/checkmark.png)<sup>\*</sup>|![Onay işareti](../media/checkmark.png)<sup>\*</sup>|
|

> [!IMPORTANT]
> Kurumda posta kutusu denetimi varsayılan olarak etkinleştirilmeden önce herhangi bir oturum  açma türü için denetlenen posta kutusu eylemlerini özelleştirdiyseniz, posta kutusunda özelleştirilmiş ayarlar korunur ve bu bölümde açıklandığı gibi varsayılan posta kutusu eylemleri üzerine yazılmaz. Denetim posta kutusu eylemlerini varsayılan değerlerine geri dönmek için (bunu herhangi bir zamanda da gerçekleştirebilirsiniz), bu makalenin devam bölümündeki Varsayılan [posta kutusu](#restore-the-default-mailbox-actions) eylemlerini geri yükleme bölümüne bakın.

### <a name="mailbox-actions-for-microsoft-365-group-mailboxes"></a>Grup posta kutuları için Microsoft 365 kutusu eylemleri

Posta kutusu denetimi varsayılan olarak Microsoft 365 Grubu posta kutularına posta kutusu denetim günlüğü getirir, ancak günlüğe kaydedilenleri özelleştiresiniz (herhangi bir oturum açma türünde kaydedilen posta kutusu eylemleri ekamaz veya kaldıramazsınız).

Aşağıdaki tabloda, her oturum açma türü için Grup posta kutularına varsayılan Microsoft 365 posta kutusu eylemleri açık almaktadır.

Grup posta kutusuna Tam Erişim izni olan bir Microsoft 365 temsilci olarak kabul edilir.

<br>

****

|Posta kutusu eylemi|Açıklama|Yönetici|Temsilci|Sahip|
|---|---|:---:|:---:|:---:|
|**Oluştur**|Takvim öğesi oluşturma. İleti oluşturma, gönderme veya alma denetlenz.|![Onay işareti](../media/checkmark.png)<sup>\*</sup>|![Onay işareti](../media/checkmark.png)<sup>\*</sup>||
|**HardDelete**|İleti Kurtarılabilir Öğeler klasöründen temiz edildi.|![Onay işareti.](../media/checkmark.png)<sup>\*</sup>|![Onay işareti](../media/checkmark.png)<sup>\*</sup>|![Onay işareti](../media/checkmark.png)<sup>\*</sup>|
|**MoveToDeletedItems**|İleti silinmiştir ve Silinmiş Öğeler klasörüne taşınmış.|![Onay işareti.](../media/checkmark.png)<sup>\*</sup>|![Onay işareti](../media/checkmark.png)<sup>\*</sup>|![Onay işareti](../media/checkmark.png)<sup>\*</sup>|
|**SendAs**|Farklı Gönder izni kullanılarak bir ileti gönderilmiştir.|![Onay işareti](../media/checkmark.png)<sup>\*</sup>|![Onay işareti](../media/checkmark.png)<sup>\*</sup>||
|**SendOnBehalf**|SendOnBehalf izni kullanılarak bir ileti gönderilmiştir.|![Onay işareti](../media/checkmark.png)<sup>\*</sup>|![Onay işareti](../media/checkmark.png)<sup>\*</sup>||
|**SoftDelete**|İleti kalıcı olarak silinmiştir veya Silinmiş Öğeler klasöründen silinmiştir. Otomatik olarak silinen öğeler Kurtarılabilir Öğeler klasörüne taşınır.|![Onay işareti.](../media/checkmark.png)<sup>\*</sup>|![Onay işareti](../media/checkmark.png)<sup>\*</sup>|![Onay işareti](../media/checkmark.png)<sup>\*</sup>|
|**Güncelleştirme**|İleti veya özelliği değiştirilmiştir.|![Onay işareti.](../media/checkmark.png)<sup>\*</sup>|![Onay işareti](../media/checkmark.png)<sup>\*</sup>|![Onay işareti](../media/checkmark.png)<sup>\*</sup>|
|

### <a name="verify-that-default-mailbox-actions-are-being-logged-for-each-logon-type"></a>Her oturum açma türü için varsayılan posta kutusu eylemlerinin günlüğe kaydedileceğini doğrulama

Varsayılan olarak posta kutusu denetimi, tüm posta kutularına *yeni bir DefaultAuditSet* özelliği ekler. Bu özelliğin değeri, posta kutusunda varsayılan posta kutusu eylemlerinin (Microsoft tarafından yönetilen) denetlenip denetlen olmadığını gösterir.

Kullanıcı posta kutularında veya paylaşılan posta kutularında değeri görüntülemek için, posta kutusunun adını, diğer adını, \<MailboxIdentity\> e-posta adresini veya kullanıcı asıl adını (kullanıcı adı) değiştirin ve Exchange Online PowerShell'de şu komutu çalıştırın:

```PowerShell
Get-Mailbox -Identity <MailboxIdentity> | Format-List DefaultAuditSet
```

Değeri grup posta kutularında Microsoft 365 için, paylaşılan posta kutusunun adı, \<MailboxIdentity\> diğer adı veya e-posta adresiyle değiştirin ve Exchange Online PowerShell'de şu komutu çalıştırın:

```PowerShell
Get-Mailbox -Identity <MailboxIdentity> -GroupMailbox | Format-List DefaultAuditSet
```

Değer şunları `Admin, Delegate, Owner` gösterir:

- Bu üç oturum açma türü için de varsayılan posta kutusu eylemleri denetlenen bir işlemdir. Grup posta kutuları üzerinde yalnızca bu Microsoft 365.
- Yönetici, *kullanıcı posta* kutusunda veya paylaşılan posta kutusunda herhangi bir oturum açma türü için denetlenen posta kutusu eylemlerini değiştirmemiştir. Bunun, kurumda posta kutusu denetiminin varsayılan olarak açık olduğu varsayılan durum olduğunu unutmayın.

Yönetici bir oturum açma türü için denetlenen posta kutusu eylemlerini daha önce değiştirmemişse (**Set-Mailbox** cmdlet'inde *AuditAdmin*, *AuditDelegate* veya *AuditOwner* parametreleri kullanılarak), özellik değeri farklı olur.

Örneğin, kullanıcı posta kutusu `Owner` veya paylaşılan posta *kutusunda DefaultAuditSet* özelliğinin değeri şunları gösterir:

- Posta kutusu sahibinin varsayılan posta kutusu eylemleri denetlenen bir eylemdir.
- Ve oturum açma türleri için denetlenen `Delegate` posta `Admin` kutusu eylemleri varsayılan eylemlerden değiştirilmiştir.

*DefaultAuditSet özelliği için boş* bir değer, kullanıcı posta kutusunda veya paylaşılan posta kutusunda üç oturum açma türü için de posta kutusu eylemlerinin değiştirdiğini gösterir.

Daha fazla bilgi için, bu [makalenin Varsayılan olarak kaydedilen posta kutusu eylemlerini değiştirme](#change-or-restore-mailbox-actions-logged-by-default) veya geri yükleme bölümüne bakın.

### <a name="display-the-mailbox-actions-that-are-being-logged-on-mailboxes"></a>Posta kutularda oturum açmış olan posta kutusu eylemlerini görüntüleme

Kullanıcı posta kutularında veya paylaşılan posta kutularında oturum açmış durumda olan posta kutusu eylemlerini görmek için, yerine posta kutusunun adını, \<MailboxIdentity\> diğer adını, e-posta adresini veya kullanıcı asıl adını (kullanıcı adı) girin ve Exchange Online PowerShell'de aşağıdaki komutlardan birini veya birden fazlasını çalıştırın.

> [!NOTE]
> Grup posta kutuları için `-GroupMailbox` aşağıdaki **Posta Kutusu Al** komutlarına geçiş Microsoft 365, ancak döndürülen değerlere inanmıyor olun. Grup posta kutuları için denetlenen varsayılan Microsoft 365 statik posta kutusu eylemleri, bu makalenin başlarındaki [Microsoft 365](#mailbox-actions-for-microsoft-365-group-mailboxes) Grubu posta kutuları için posta kutusu eylemleri bölümünde açıklanmıştır.

#### <a name="owner-actions"></a>Sahip eylemleri

```PowerShell
Get-Mailbox -Identity <MailboxIdentity> | Select-Object -ExpandProperty AuditOwner
```

#### <a name="delegate-actions"></a>Temsilci eylemleri

```PowerShell
Get-Mailbox -Identity <MailboxIdentity> | Select-Object -ExpandProperty AuditDelegate
```

#### <a name="admin-actions"></a>Yönetici eylemleri

```PowerShell
Get-Mailbox -Identity <MailboxIdentity> | Select-Object -ExpandProperty AuditAdmin
```

## <a name="change-or-restore-mailbox-actions-logged-by-default"></a>Varsayılan olarak kaydedilen posta kutusu eylemlerini değiştirme veya geri yükleme

Daha önce de açıklanmıştır; posta kutusu denetimini varsayılan olarak denetlemenin en önemli avantajlarından biri, denetlenen posta kutusu eylemlerini yönetmenize gerek kalmama durumudur. Microsoft bunu sizin için yapar ve yayımlanan posta kutusu eylemlerini varsayılan olarak denetlenen yeni posta kutusu eylemlerini otomatik olarak ekleriz.

Bununla birlikte, kullanıcı posta kutuları ve paylaşılan posta kutuları için farklı bir posta kutusu eylemleri kümesi denetlemesi kuruluş için gerekli olabilir. Bu bölümdeki yordamlarda, her oturum açma türünde denetlenen posta kutusu eylemlerini nasıl değiştiryebilirsiniz ve Microsoft tarafından yönetilen varsayılan eylemlere nasıl geri dönebilirsiniz.

> [!IMPORTANT]
> Kullanıcı posta kutularından veya paylaşılan posta kutularından oturum açan posta kutusu eylemlerini özelleştirmek için aşağıdaki yordamları kullanırsanız, Microsoft tarafından yayımlanan tüm yeni varsayılan posta kutusu eylemleri bu posta kutularda otomatik olarak denetlenz. Özelleştirilmiş eylem listeniz için tüm yeni posta kutusu eylemlerini el ile eklemeniz gerekir.

### <a name="change-the-mailbox-actions-to-audit"></a>Posta kutusu eylemlerini denetlenen olarak değiştirme

Kullanıcı posta kutuları ve paylaşılan posta kutuları için denetlenen posta kutusu eylemlerini değiştirmek için **Set-Mailbox** cmdlet'inde *AuditAdmin*, *AuditDelegate* veya *AuditOwner* parametrelerini kullanabilirsiniz (Microsoft 365 grubu posta kutuları için denetlenen eylemler özelleştirılamaz).

Posta kutusu eylemlerini belirtmek için iki farklı yöntem kullanabilirsiniz:

- *Şu* söz dizimi kullanarak var olan posta kutusu eylemlerini değiştirin (üzerine yaz). `action1,action2,...actionN`
- *Şu söz dizimi* kullanarak diğer mevcut değerleri etkilemeden posta kutusu eylemlerini ekleyin veya kaldırın: `@{Add="action1","action2",..."actionN"}` veya `@{Remove="action1","action2",..."actionN"}`.

Bu örnekte, SoftDelete ve HardDelete ile varsayılan eylemlerin üzerine yazarak "Svana Laureano" adlı posta kutusunun yönetici posta kutusu eylemleri değişir.

```PowerShell
Set-Mailbox -Identity "Gabriela Laureano" -AuditAdmin HardDelete,SoftDelete
```

Bu örnekte, posta kutusuna MailboxLogin sahip laura@contoso.onmicrosoft.com.

```PowerShell
Set-Mailbox -Identity laura@contoso.onmicrosoft.com -AuditOwner @{Add="MailboxLogin"}
```

Bu örnekte, Ekip Tartışması posta kutusu için MoveToDeletedItems temsilci eylemi kaldırılıyor.

```PowerShell
Set-Mailbox -Identity "Team Discussion" -AuditDelegate @{Remove="MoveToDeletedItems"}
```

Hangi yöntemi kullanırsa kullanın, kullanıcı posta kutuları veya paylaşılan posta kutuları üzerinde denetlenen posta kutusu eylemlerini özelleştirmenin sonuçları şöyledir:

- Özelleştirebileceğiniz oturum açma türü için, denetlenen posta kutusu eylemleri artık Microsoft tarafından yönetilmiyor.
- Özelleştirebileceğiniz oturum açma türü artık posta kutusunun *DefaultAuditSet* özellik değerinde daha önce açıklandığı gibi [görüntülenmez](#verify-that-default-mailbox-actions-are-being-logged-for-each-logon-type).

### <a name="restore-the-default-mailbox-actions"></a>Varsayılan posta kutusu eylemlerini geri yükleme

> [!NOTE]
> Aşağıdaki yordamlar, Grup posta Microsoft 365 için geçerli değildir (bunlar burada açıklanan varsayılan eylemlerle [sınırlıdır](#mailbox-actions-for-microsoft-365-group-mailboxes)).

Kullanıcı posta kutusunda veya paylaşılan posta kutusunda denetlenen posta kutusu eylemlerini özelleştirdıysanız, bir veya tüm oturum açma türlerinde varsayılan posta kutusu eylemlerini geri yüklemek için şu söz dizimi kullanabilirsiniz:

```PowerShell
Set-Mailbox -Identity <MailboxIdentity> -DefaultAuditSet <Admin | Delegate | Owner>
```

Virgüllerle ayrılmış birden *çok DefaultAuditSet* değeri belirtebilirsiniz

Bu örnekte, posta kutusunda her oturum açma türü için denetlenen varsayılan posta kutusu eylemleri geri mark@contoso.onmicrosoft.com.

```PowerShell
Set-Mailbox -Identity mark@contoso.onmicrosoft.com -DefaultAuditSet Admin,Delegate,Owner
```

Bu örnekte, posta kutusunda Yönetici oturum açma türü için denetlenen varsayılan posta kutusu eylemleri geri chris@contoso.onmicrosoft.com, ancak Temsilci ve Sahip oturum açma türleri için özelleştirilmiş denetlenen posta kutusu eylemlerini bırakır.

```PowerShell
Set-Mailbox -Identity chris@contoso.onmicrosoft.com -DefaultAuditSet Admin
```

Bir oturum açma türü için varsayılan denetlenen posta kutusu eylemlerini geri yükleme işlemi aşağıdaki sonuçlara neden olur:

- Posta kutusu eylemlerinin geçerli listesi, oturum açma türü için varsayılan posta kutusu eylemleriyle değiştirilir.
- Microsoft tarafından yayımlanan tüm yeni posta kutusu eylemleri, oturum açma türü için denetlenen eylemler listesine otomatik olarak eklenir.
- Posta *kutusunun DefaultAuditSet* özellik değeri, geri yüklenen oturum açma türünü içerecek şekilde güncelleştirilir.

## <a name="turn-off-mailbox-auditing-on-by-default-for-your-organization"></a>Kuruluşta posta kutusu denetimini varsayılan olarak kapatma

Exchange Online PowerShell'de aşağıdaki komutu çalıştırarak, tüm kuruluşta posta kutusu denetimini varsayılan Exchange Online kapatabilirsiniz:

```PowerShell
Set-OrganizationConfig -AuditDisabled $true
```

Posta kutusu denetimini varsayılan olarak kapatmanın sonuçları aşağıdaki şekildedir:

- Posta kutusu denetimi, kurum için devre dışı bırakılır.
- Posta kutusu denetimini varsayılan olarak devre dışı bırakmış olduğunuz zaman, posta kutusunda denetim etkin olsa bile hiçbir posta kutusu eylemi denetlenmz (posta kutusunda *AuditEnabled* özelliği **True olur**).
- Yeni posta kutuları için posta kutusu denetimi etkinleştirilmez ve yeni veya var olan bir *posta kutusunda AuditEnabled* özelliği **True** olarak ayarlanmaz.
- Tüm posta kutusu denetim atlama ilişkilendirme ayarları ( **Set-MailboxAuditBypassAssociation** cmdlet'i kullanılarak yapılandırılır) yoksayılır.
- Var olan posta kutusu denetim kayıtları, kaydın denetim günlüğü yaş sınırı sona erene kadar korunur.

### <a name="turn-on-mailbox-auditing-on-by-default"></a>Posta kutusu denetimini varsayılan olarak açma

Posta kutusu denetimini organizasyonunız için yeniden açmak için, PowerShell'de aşağıdaki Exchange Online çalıştırın:

```PowerShell
Set-OrganizationConfig -AuditDisabled $false
```

## <a name="bypass-mailbox-audit-logging"></a>Posta kutusu denetim günlüğünü atlama

Şu anda, kuruluşta posta kutusu denetimi varsayılan olarak açıkken belirli posta kutuları için posta kutusu denetimini devre dışı bırakaabilirsiniz. Örneğin, *AuditEnabled mailbox özelliğini* False olarak ayarlama **yoksayılır** .

Bununla birlikte, belirtilen kullanıcıların eylemlerinin nerede olduğu bağımsız olarak, belirtilen kullanıcıların tüm posta kutusu eylemlerini ve tüm posta kutusu eylemlerini engellemek için Exchange Online  PowerShell'de **Set-MailboxAuditBypassAssociation** cmdlet'ini kullanmaya devamabilirsiniz. Örneğin:

- Atlayan kullanıcılar tarafından gerçekleştirilen posta kutusu sahibi eylemleri günlüğe kaydedilmez.
- Diğer kullanıcıların posta kutularına (paylaşılan posta kutuları da dahil) atlayan kullanıcılar tarafından gerçekleştirilen temsilci eylemleri günlüğe kaydedilmez.
- Atlayan kullanıcılar tarafından gerçekleştirilen yönetici eylemleri günlüğe kaydedilmez.

Belirli bir kullanıcının posta kutusu denetim günlüğünü atlamak için, kullanıcının adıyla, \<MailboxIdentity\> e-posta adresiyle, diğer adıyla veya kullanıcı asıl adıyla (kullanıcı asıl adı) değiştirin ve aşağıdaki komutu çalıştırın:

```PowerShell
Set-MailboxAuditBypassAssociation -Identity <MailboxIdentity> -AuditByPassEnabled $true
```

Belirtilen kullanıcıda denetimin at çalıştığını doğrulamak için, aşağıdaki komutu çalıştırın:

```PowerShell
Get-MailboxAuditBypassAssociation -Identity <MailboxIdentity> | Format-List AuditByPassEnabled
```

True değeri **,** kullanıcı için posta kutusu denetim günlüğünün atlandı olduğunu gösterir.

## <a name="more-information"></a>Daha fazla bilgi

- Tüm kuruluşlarda posta kutusu denetim günlüğü varsayılan olarak etkinleştirilse de, varsayılan olarak yalnızca E5 lisansı olan kullanıcılar [Microsoft 365 uyumluluk merkezi'ta veya Office 365](search-the-audit-log-in-security-and-compliance.md) Yönetimi Etkinliği [API'si](/office/office-365-management-api/office-365-management-activity-api-reference) aracılığıyla denetim günlüğü aramalarında posta kutusu denetim günlüğü **olaylarını geri dönecektir**.

  E5 lisansı olmayan kullanıcıların posta kutusu denetim günlüğü girdilerini almak için şunları yapın:

  - Tek tek posta kutularda posta kutusu denetimini el ile etkinleştirme (, komutunu çalıştırın `Set-Mailbox -Identity <MailboxIdentity> -AuditEnabled $true`). Bunu tamamladikten sonra, kayıtta veya yönetim yönetimi etkinliği API'sinde Microsoft 365 uyumluluk merkezi günlüğü Office 365 kullanabilirsiniz.

    > [!NOTE]
    > Posta kutusunda posta kutusu denetimi zaten etkinleştirilmiş gibi görünüyorsa, ancak aramanız hiçbir sonuç sonuç getirmiyorsa, _AuditEnabled_ `$false` parametresinin değerini 'a ve sonra yeniden seçin `$true`.

  - Exchange Online PowerShell'de aşağıdaki cmdlet'leri kullanın:
    - [Belirli kullanıcılar için posta kutusu denetim günlüğünde arama yapmak için Search-MailboxAuditLog](/powershell/module/exchange/search-mailboxauditlog) .
    - [New-MailboxAuditLogSearch, belirli](/powershell/module/exchange/new-mailboxauditlogsearch) kullanıcılar için posta kutusu denetim günlüğünde arama yapmak ve sonuçların belirtilen alıcılara e-postayla gönderilmelerini sağlar.

  - Aşağıdaki <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange yapmak için, Exchange Online Yönetim Merkezi'ni (EAC)</a> kullanın:
    - [Posta kutusu denetim günlüklerini dışarı aktarma](/Exchange/security-and-compliance/exchange-auditing-reports/export-mailbox-audit-logs)
    - [Sahipsiz posta kutusu erişim raporunu çalıştırma](/Exchange/security-and-compliance/exchange-auditing-reports/non-owner-mailbox-access-report)

- Varsayılan olarak, posta kutusu denetim günlüğü kayıtları silinmeden önce 90 gün boyunca korunur. Exchange Online PowerShell'de **Set-Mailbox** cmdlet'inde *AuditLogAgeLimit* parametresini kullanarak denetim günlüğü kayıtlarının yaş sınırını değiştirebilirsiniz. Ancak, bu değerin artırılması denetim günlüğünde 90 günlükten daha eski olayları aramanızı vermez.

  Yaş sınırını artırıyorsanız, kullanıcının posta kutusu denetim günlüğünde 90 günlükten eski kayıtları aramak için Exchange Online PowerShell'de [Search-MailboxAuditLog](/powershell/module/exchange/search-mailboxauditlog) cmdlet'ini kullansanız gerekir.

- Kuruluş için posta kutusu denetimi varsayılan olarak açıkken posta kutusu denetimi açıkken posta kutusunun *AuditLogAgeLimit* özelliğini değiştirdiysiniz, posta kutusunun mevcut denetim günlüğü yaş sınırı değişmez. Başka bir deyişle, posta kutusu denetiminin varsayılan olarak açık olması posta kutusu denetim kayıtlarının geçerli yaş sınırını etkilemez.

- Bir Grup posta *kutusunda AuditLogAgeLimit* değerini değiştirmek Microsoft 365 Kutusu `-GroupMailbox` Kutusu komutuna **anahtarı dahil etmek** gerekir.

- Posta kutusu denetim günlüğü kayıtları, her kullanıcının posta kutusunun Kurtarılabilir Öğeler klasöründe bir alt klasörde (Denetimler olarak adlandırılmıştır *) depolanır*. Posta kutusu denetim kayıtları ve Kurtarılabilir Öğeler klasörüyle ilgili olarak aşağıdaki şeyleri unutmayın:

  - Posta kutusu denetim kayıtları, Kurtarılabilir Öğeler klasörünün varsayılan olarak 30 GB olan depolama kotasını (uyarı kotası 20 GB' dir) karşılar. Aşağıdaki olduğunda depolama kotası otomatik olarak 100 GB'a (90 GB uyarı kotası ile) artırılır:
    - Posta kutusuna 10 gün süreyle yerleştirilir.
    - Posta kutusu, Uyumluluk Merkezi'nde bir bekletme ilkesine atanır.

  - Posta kutusu denetim kayıtları, Kurtarılabilir [Öğeler klasörünün klasör sınırını da içerir](/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits#mailbox-folder-limits). Denetimler alt klasörüne en çok 3 milyon öğe (denetim kayıtları) depolanıyor.

    > [!NOTE]
    > Varsayılan olarak posta kutusu denetiminin Kurtarılabilir Öğeler klasörünün depolama kotasını veya klasör sınırını etkileme ihtimali çok düşük olabilir.

    - Kurtarılabilir Öğeler klasöründeki Denetimler alt Exchange Online boyutunu ve sayısını görüntülemek için PowerShell'de aşağıdaki komutu çalıştırabilirsiniz:

      ```PowerShell
      Get-MailboxFolderStatistics -Identity <MailboxIdentity> -FolderScope RecoverableItems | Where-Object {$_.Name -eq 'Audits'} | Format-List FolderPath,FolderSize,ItemsInFolder
      ```

    - Kurtarılabilir Öğeler klasöründe denetim günlüğü kaydına doğrudan erişilemez; bunun yerine, **Search-MailboxAuditLog** cmdlet'ini kullanır veya posta kutusu denetim kayıtlarını bulmak ve görüntülemek için denetim günlüğünde arama yapın.

- Posta kutusu Uyumluluk Merkezi'nde bekletme ilkesine yerleştirilirse veya bir bekletme ilkesine atanmışsa, denetim günlüğü kayıtları posta kutusunun *AuditLogAgeLimit* özelliği tarafından tanımlanan süre boyunca (varsayılan olarak 90 gün) korunur. Posta kutularının denetim günlüğü kayıtlarını daha uzun süre tutmak için, posta kutusunun *AuditLogAgeLimit değerini artırmanız* gerekir.

- Çok coğrafi bir ortamda, coğrafi olarak posta kutusu denetimi desteklanmaz. Örneğin, kullanıcıya farklı bir coğrafi konumdaki paylaşılan posta kutusuna erişim izinleri atanmışsa, o kullanıcı tarafından gerçekleştirilen posta kutusu eylemleri paylaşılan posta kutusunun posta kutusu denetim günlüğüne kaydedilmez. Exchange denetim olayları şu anda yalnızca varsayılan konum için kullanılabilir.
