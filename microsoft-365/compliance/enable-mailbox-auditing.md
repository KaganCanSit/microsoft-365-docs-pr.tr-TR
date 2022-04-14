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
description: Posta kutusu denetim günlüğü varsayılan olarak Microsoft 365 ('varsayılan posta kutusu denetimi' veya 'posta kutusu denetimi varsayılan olarak açık' olarak da adlandırılır) etkindir. Bu yapılandırma, posta kutusu sahipleri, temsilciler ve yöneticiler tarafından gerçekleştirilen belirli eylemlerin otomatik olarak posta kutusu denetim günlüğüne kaydedildiği ve burada posta kutusunda gerçekleştirilen etkinlikleri arayabileceğiniz anlamına gelir.
ms.openlocfilehash: e869c705df2943c1781c02362c2c38b6713affc5
ms.sourcegitcommit: e13c8fc28c68422308c9d356109797cfcf6f77be
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/14/2022
ms.locfileid: "64841894"
---
# <a name="manage-mailbox-auditing"></a>Posta kutusu denetimini yönetme

Ocak 2019'da Microsoft, tüm kuruluşlar için posta kutusu denetim günlüğünü varsayılan olarak etkinleştirdi. Bu yapılandırma, posta kutusu sahiplerinin, temsilcilerin ve yöneticilerin belirli eylemlerinin otomatik olarak günlüğe kaydedildiği anlamına gelir. Ayrıca, posta kutusu denetim günlüğünde arama yaptığınızda ilgili posta kutusu denetim kayıtlarının da kullanılabilir olacağı anlamına gelir. Posta kutusu denetimi varsayılan olarak açılmadan önce, bunu kuruluşunuzdaki her kullanıcı posta kutusu için el ile etkinleştirmeniz gerekiyordu.

Posta kutusu denetiminin varsayılan olarak bazı avantajları şunlardır:

- Yeni bir posta kutusu oluşturduğunuzda denetim otomatik olarak etkinleştirilir. Yeni kullanıcılar için el ile etkinleştirmeniz gerekmez.
- Denetlenen posta kutusu eylemlerini yönetmeniz gerekmez. Her oturum açma türü (Yönetici, Temsilci ve Sahip) için önceden tanımlanmış bir posta kutusu eylemleri kümesi varsayılan olarak denetlenmektedir.
- Microsoft yeni bir posta kutusu eylemi yayımladığında, eylem varsayılan olarak denetlenen posta kutusu eylemleri listesine otomatik olarak eklenebilir (uygun lisansa sahip kullanıcıya tabidir). Bu, posta kutularına yeni eylemler ekleme işlemini izlemeniz gerekmeyecek anlamına gelir.
- Kuruluşunuz genelinde tutarlı bir posta kutusu denetim ilkesine sahipsiniz (çünkü tüm posta kutuları için aynı eylemleri denetliıyorsunuz).

> [!NOTE]
>
> - Posta kutusu denetiminin varsayılan olarak açık olarak yayımlanması hakkında hatırlamanız gereken önemli şey şudur: Posta kutusu denetimini yönetmek için hiçbir şey yapmanız gerekmez. Ancak, daha fazla bilgi edinmek, posta kutusu denetimini varsayılan ayarlardan özelleştirmek veya tamamen kapatmak için bu makale size yardımcı olabilir.
> - Varsayılan olarak, Microsoft 365 uyumluluk merkezi veya Office 365 Yönetim Etkinliği API'sinde denetim günlüğü aramalarında yalnızca [Gelişmiş Denetim](advanced-audit.md) özelliğini içeren lisanslara sahip kullanıcılar için posta kutusu denetim olayları kullanılabilir. Bu lisanslar [burada](auditing-solutions-overview.md#advanced-audit-1) açıklanmıştır. Bu makale, kısaca Gelişmiş Denetim'i *E5/A5/G5 lisansları olarak içeren lisanslara* topluca başvuracaktır.
>   Lisanslamanın M365 uyumluluk merkezinde posta kutusu denetim olaylarını nasıl etkilediği hakkında daha fazla bilgi için, bu makalenin devamında yer alan [Daha fazla bilgi](#more-information) bölümüne bakın.

## <a name="verify-mailbox-auditing-on-by-default-is-turned-on"></a>Posta kutusu denetiminin varsayılan olarak açık olduğunu doğrulama

Kuruluşunuzda posta kutusu denetiminin varsayılan olarak açık olduğunu doğrulamak için [Exchange Online PowerShell'de](/powershell/exchange/connect-to-exchange-online-powershell) aşağıdaki komutu çalıştırın:

```PowerShell
Get-OrganizationConfig | Format-List AuditDisabled
```

**False** değeri, kuruluş için varsayılan olarak üzerinde posta kutusu denetiminin etkinleştirildiğini gösterir. Bu, varsayılan olarak kuruluş değeri belirli posta kutularında posta kutusu denetim ayarını geçersiz kılar. Örneğin, posta kutusu denetimi bir posta kutusu için devre dışı bırakıldıysa (posta kutusunda *AuditEnabled* özelliği **False** ise), kuruluş için varsayılan olarak açık posta kutusu denetimi etkinleştirildiğinden, posta kutusu için varsayılan posta kutusu eylemleri denetlenecektir.

Belirli posta kutuları için posta kutusu denetimini devre dışı tutmak için, posta kutusu sahibi ve posta kutusuna erişim yetkisi verilmiş diğer kullanıcılar için posta kutusu denetimi atlamasını yapılandırabilirsiniz. Daha fazla bilgi için bu makalenin devamında [posta kutusu denetim günlüğünü atlama](#bypass-mailbox-audit-logging) bölümüne bakın.

> [!NOTE]
> Kuruluş için posta kutusu denetimi varsayılan olarak açık olduğunda, etkilenen posta kutularının *AuditEnabled* özelliği **False** yerine **True** olarak değiştirilmez. Başka bir deyişle, üzerinde posta kutusu denetimi varsayılan olarak posta kutularındaki *AuditEnabled* özelliğini yoksayar.

## <a name="supported-mailbox-types"></a>Desteklenen posta kutusu türleri

Aşağıdaki tabloda, şu anda varsayılan olarak üzerinde posta kutusu denetimi tarafından desteklenen posta kutusu türleri gösterilmektedir:

|Posta kutusu türü|Destekleniyor|
|---|:---:|
|Kullanıcı posta kutuları|![Onay işareti.](../media/checkmark.png)|
|Paylaşılan posta kutuları|![Onay işareti.](../media/checkmark.png)|
|Microsoft 365 Grubu posta kutuları|![Onay işareti.](../media/checkmark.png)|
|Kaynak posta kutuları||
|Ortak klasör posta kutuları||

## <a name="logon-types-and-mailbox-actions"></a>Oturum açma türleri ve posta kutusu eylemleri

Oturum açma türleri, posta kutusunda denetlenen eylemleri gerçekleştirmiş olan kullanıcıyı sınıflandırır. Aşağıdaki listede, posta kutusu denetim günlüğünde kullanılan oturum açma türleri açıklanmaktadır:

- **Sahip**: Posta kutusu sahibi (posta kutusuyla ilişkili hesap).
- **Temsilci**:
  - Başka bir posta kutusuna SendAs, SendOnBehalf veya FullAccess izni atanmış bir kullanıcı.
  - Kullanıcının posta kutusuna FullAccess izni atanmış bir yönetici.
- **Yönetici**:
  - Posta kutusu aşağıdaki Microsoft eBulma araçlarından biriyle arandı:
    - Uyumluluk merkezinde İçerik Arama.
    - Uyumluluk merkezinde eBulma veya Advanced eDiscovery.
    - Exchange Online'da eKeşif'i In-Place.
  - Posta kutusuna MAPI Düzenleyicisi Microsoft Exchange Server kullanılarak erişilir.

### <a name="mailbox-actions-for-user-mailboxes-and-shared-mailboxes"></a>Kullanıcı posta kutuları ve paylaşılan posta kutuları için posta kutusu eylemleri

Aşağıdaki tabloda, kullanıcı posta kutuları ve paylaşılan posta kutuları için posta kutusu denetim günlüğünde kullanılabilen posta kutusu eylemleri açıklanmaktadır.

- Onay işareti (![Onay işareti.](../media/checkmark.png)), posta kutusu eyleminin oturum açma türü için günlüğe kaydedilebileceğini gösterir (tüm oturum açma türleri için tüm eylemler kullanılamaz).
- Onay işaretinden sonra bir yıldız işareti ( <sup>\*</sup> ) posta kutusu eyleminin oturum açma türü için varsayılan olarak günlüğe kaydedildiğini gösterir.
- Bir posta kutusuna Tam Erişim izni olan bir yöneticinin temsilci olarak kabul edildiğini unutmayın.

|Posta kutusu eylemi|Açıklama|Yönetici|Temsilci|Sahibi|
|---|---|:---:|:---:|:---:|
|**AddFolderPermissions**|Bu değer bir posta kutusu eylemi olarak kabul edilmiş olsa da, **UpdateFolderPermissions** eylemine zaten dahil edilmiş ve ayrı olarak denetlenmiyor. Başka bir deyişle, bu değeri kullanmayın.||||
|**Kayıt Uygula**|Bir öğe kayıt olarak etiketlenmiştir.|![Onay işareti.](../media/checkmark.png)<sup>\*</sup>|![Onay işareti.](../media/checkmark.png)<sup>\*</sup>|![Onay işareti.](../media/checkmark.png)<sup>\*</sup>|
|**Kopya**|İleti başka bir klasöre kopyalandı.|![Onay işareti.](../media/checkmark.png)|||
|**Oluşturma**|Posta kutusunun Takvim, Kişiler, Taslak, Notlar veya Görevler klasöründe bir öğe oluşturulmuştur (örneğin, yeni bir toplantı isteği oluşturulur). İleti oluşturma, gönderme veya alma denetlenmiyor. Ayrıca, posta kutusu klasörü oluşturma işlemi denetlenmiyor.|![Onay işareti.](../media/checkmark.png)<sup>\*</sup>|![Onay işareti.](../media/checkmark.png)<sup>\*</sup>|![Onay işareti.](../media/checkmark.png)|
|**FolderBind**|Bir posta kutusu klasörüne erişildi. Yönetici veya temsilci posta kutusunu açtığında da bu eylem günlüğe kaydedilir. <br/><br/> **Not**: Temsilciler tarafından gerçekleştirilen klasör bağlama eylemleri için denetim kayıtları bir araya getirilir. 24 saatlik bir süre içinde tek tek klasör erişimi için bir denetim kaydı oluşturulur.|![Onay işareti.](../media/checkmark.png)|![Onay işareti.](../media/checkmark.png)||
|**HardDelete**|Kurtarılabilir Öğeler klasöründen bir ileti temizlendi.|![Onay işareti.](../media/checkmark.png)<sup>\*</sup>|![Onay işareti.](../media/checkmark.png)<sup>\*</sup>|![Onay işareti.](../media/checkmark.png)<sup>\*</sup>|
|**MailboxLogin**|Kullanıcı posta kutusunda oturum açtı.|||![Onay işareti](../media/checkmark.png)|
|**MailItemsAccessed**|**Not**: Bu değer yalnızca E5/A5/G5 lisansına sahip kullanıcılar için kullanılabilir. Daha fazla bilgi için bkz. [Microsoft 365'de Gelişmiş Denetimi Ayarlama](set-up-advanced-audit.md). <br/><br/> Posta verilerine posta protokolleri ve istemciler tarafından erişilir.|![Onay işareti.](../media/checkmark.png)<sup>\*</sup>|![Onay işareti.](../media/checkmark.png)<sup>\*</sup>|![Onay işareti](../media/checkmark.png)<sup>\*</sup>|
|**MessageBind**|**Not**: Bu değer yalnızca E5/A5/G5 lisansı *olmayan* kullanıcılar için kullanılabilir. <br/><br/> Önizleme bölmesinde bir ileti görüntülendi veya bir yönetici tarafından açıldı.|![Onay işareti](../media/checkmark.png)|||
|**ModifyFolderPermissions**|Bu değer bir posta kutusu eylemi olarak kabul edilmiş olsa da, **UpdateFolderPermissions** eylemine zaten dahil edilmiş ve ayrı olarak denetlenmiyor. Başka bir deyişle, bu değeri kullanmayın.||||
|**Hareket**|İleti başka bir klasöre taşındı.|![Onay işareti.](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|
|**MoveToDeletedItems**|Bir ileti silindi ve Silinmiş Öğeler klasörüne taşındı.|![Onay işareti.](../media/checkmark.png)<sup>\*</sup>|![Onay işareti.](../media/checkmark.png)<sup>\*</sup>|![Onay işareti](../media/checkmark.png)<sup>\*</sup>|
|**RecordDelete**|Kayıt olarak etiketlenmiş bir öğe geçici olarak silindi (Kurtarılabilir Öğeler klasörüne taşındı). Kayıt olarak etiketlenen öğeler kalıcı olarak silinemez (Kurtarılabilir Öğeler klasöründen temizlenir).|![Onay işareti.](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|
|**RemoveFolderPermissions**|Bu değer bir posta kutusu eylemi olarak kabul edilmiş olsa da, **UpdateFolderPermissions** eylemine zaten dahil edilmiş ve ayrı olarak denetlenmiyor. Başka bir deyişle, bu değeri kullanmayın.||||
|**SearchQueryInitiated**|**Not**: Bu değer yalnızca E5/A5/G5 lisansına sahip kullanıcılar için kullanılabilir. Daha fazla bilgi için bkz. [Microsoft 365'de Gelişmiş Denetimi Ayarlama](set-up-advanced-audit.md). <br/><br/> Bir kişi posta kutusunda öğeleri aramak için Outlook (Windows, Mac, iOS, Android veya Web üzerinde Outlook) veya Windows 10 için Posta uygulamasını kullanır.|||![Onay işareti](../media/checkmark.png)|
|**Gönderin**|**Not**: Bu değer yalnızca E5/A5/G5 lisansına sahip kullanıcılar için kullanılabilir. Daha fazla bilgi için bkz. [Microsoft 365'de Gelişmiş Denetimi Ayarlama](set-up-advanced-audit.md). <br/><br/> Kullanıcı bir e-posta iletisi gönderir, e-posta iletisini yanıtlar veya e-posta iletisini iletir.|![Onay işareti.](../media/checkmark.png)<sup>\*</sup>||![Onay işareti](../media/checkmark.png)<sup>\*</sup>|
|**GöndermeLer**|SendAs izni kullanılarak bir ileti gönderildi. Bu, başka bir kullanıcının iletiyi posta kutusu sahibinden gelmiş gibi gönderdiği anlamına gelir.|![Onay işareti.](../media/checkmark.png)<sup>\*</sup>|![Onay işareti](../media/checkmark.png)<sup>\*</sup>||
|**SendOnBehalf**|SendOnBehalf izni kullanılarak bir ileti gönderildi. Bu, başka bir kullanıcının iletiyi posta kutusu sahibi adına gönderdiği anlamına gelir. İleti, iletinin kimin adına gönderildiğini ve iletiyi gerçekten kimin gönderdiğini alıcıya gösterir.|![Onay işareti.](../media/checkmark.png)<sup>\*</sup>|![Onay işareti](../media/checkmark.png)<sup>\*</sup>||
|**SoftDelete**|İleti kalıcı olarak silinmiş veya Silinmiş Öğeler klasöründen silinmiş. Geçici olarak silinen öğeler Kurtarılabilir Öğeler klasörüne taşınır.|![Onay işareti.](../media/checkmark.png)<sup>\*</sup>|![Onay işareti.](../media/checkmark.png)<sup>\*</sup>|![Onay işareti](../media/checkmark.png)<sup>\*</sup>|
|**Güncelleştirme**|İleti veya özelliklerinden herhangi biri değiştirildi.|![Onay işareti.](../media/checkmark.png)<sup>\*</sup>|![Onay işareti.](../media/checkmark.png)<sup>\*</sup>|![Onay işareti](../media/checkmark.png)<sup>\*</sup>|
|**UpdateCalendarDelegation**|Posta kutusuna takvim temsilcisi atandı. Takvim temsilcisi, aynı kuruluştaki başka birine posta kutusu sahibinin takvimini yönetme izni verir.|![Onay işareti.](../media/checkmark.png)<sup>\*</sup>||![Onay işareti](../media/checkmark.png)<sup>\*</sup>|
|**UpdateComplianceTag**|Posta öğesine farklı bir bekletme etiketi uygulanır (öğeye yalnızca bir bekletme etiketi atanabilir).|![Onay işareti.](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|![Onay işareti](../media/checkmark.png)|
|**UpdateFolderPermissions**|Klasör izni değiştirildi. Klasör izinleri, kuruluşunuzdaki hangi kullanıcıların bir posta kutusundaki klasörlere ve bu klasörlerde bulunan iletilere erişebileceğini denetler.|![Onay işareti.](../media/checkmark.png)<sup>\*</sup>|![Onay işareti.](../media/checkmark.png)<sup>\*</sup>|![Onay işareti](../media/checkmark.png)<sup>\*</sup>|
|**UpdateInboxRules**|Gelen kutusu kuralı eklendi, kaldırıldı veya değiştirildi. Gelen Kutusu kuralları, belirtilen koşullara göre kullanıcının Gelen Kutusu'ndaki iletileri işlemek ve bir kuralın koşulları karşılandığında iletiyi belirtilen klasöre taşıma veya iletiyi silme gibi eylemler yapmak için kullanılır.|![Onay işareti.](../media/checkmark.png)<sup>\*</sup>|![Onay işareti](../media/checkmark.png)<sup>\*</sup>|![Onay işareti](../media/checkmark.png)<sup>\*</sup>|

> [!IMPORTANT]
> Kuruluşunuzda posta kutusu denetimi etkin olmadan *önce* posta kutusu eylemlerini herhangi bir oturum açma türü için denetlemek üzere özelleştirdiyseniz, özelleştirilmiş ayarlar posta kutusunda korunur ve bu bölümde açıklandığı gibi varsayılan posta kutusu eylemleri tarafından üzerine yazılmaz. Denetim posta kutusu eylemlerini varsayılan değerlerine (istediğiniz zaman yapabilirsiniz) geri döndürmek için, bu makalenin devamında [yer alan Varsayılan posta kutusu eylemlerini geri yükleme](#restore-the-default-mailbox-actions) bölümüne bakın.

### <a name="mailbox-actions-for-microsoft-365-group-mailboxes"></a>Microsoft 365 Grubu posta kutuları için posta kutusu eylemleri

Posta kutusu denetimi varsayılan olarak Microsoft 365 Grubu posta kutularına posta kutusu denetim günlüğü getirir, ancak günlüğe kaydedilenleri özelleştiremezsiniz (herhangi bir oturum açma türü için günlüğe kaydedilen posta kutusu eylemlerini ekleyemez veya kaldıramazsınız).

Aşağıdaki tabloda, her oturum açma türü için grup posta kutuları Microsoft 365 varsayılan olarak günlüğe kaydedilen posta kutusu eylemleri açıklanmaktadır.

Microsoft 365 Grubu posta kutusuna Tam Erişim izni olan bir yöneticinin temsilci olarak kabul edildiğini unutmayın.

|Posta kutusu eylemi|Açıklama|Yönetici|Temsilci|Sahibi|
|---|---|:---:|:---:|:---:|
|**Oluşturma**|Takvim Öğesi oluşturma. İleti oluşturma, gönderme veya alma denetlenmiyor.|![Onay işareti](../media/checkmark.png)<sup>\*</sup>|![Onay işareti](../media/checkmark.png)<sup>\*</sup>||
|**HardDelete**|Kurtarılabilir Öğeler klasöründen bir ileti temizlendi.|![Onay işareti.](../media/checkmark.png)<sup>\*</sup>|![Onay işareti](../media/checkmark.png)<sup>\*</sup>|![Onay işareti](../media/checkmark.png)<sup>\*</sup>|
|**MoveToDeletedItems**|Bir ileti silindi ve Silinmiş Öğeler klasörüne taşındı.|![Onay işareti.](../media/checkmark.png)<sup>\*</sup>|![Onay işareti](../media/checkmark.png)<sup>\*</sup>|![Onay işareti](../media/checkmark.png)<sup>\*</sup>|
|**GöndermeLer**|SendAs izni kullanılarak bir ileti gönderildi.|![Onay işareti](../media/checkmark.png)<sup>\*</sup>|![Onay işareti](../media/checkmark.png)<sup>\*</sup>||
|**SendOnBehalf**|SendOnBehalf izni kullanılarak bir ileti gönderildi.|![Onay işareti](../media/checkmark.png)<sup>\*</sup>|![Onay işareti](../media/checkmark.png)<sup>\*</sup>||
|**SoftDelete**|İleti kalıcı olarak silinmiş veya Silinmiş Öğeler klasöründen silinmiş. Geçici olarak silinen öğeler Kurtarılabilir Öğeler klasörüne taşınır.|![Onay işareti.](../media/checkmark.png)<sup>\*</sup>|![Onay işareti](../media/checkmark.png)<sup>\*</sup>|![Onay işareti](../media/checkmark.png)<sup>\*</sup>|
|**Güncelleştirme**|İleti veya özelliğinden herhangi biri değiştirildi.|![Onay işareti.](../media/checkmark.png)<sup>\*</sup>|![Onay işareti](../media/checkmark.png)<sup>\*</sup>|![Onay işareti](../media/checkmark.png)<sup>\*</sup>|

### <a name="verify-that-default-mailbox-actions-are-being-logged-for-each-logon-type"></a>Her oturum açma türü için varsayılan posta kutusu eylemlerinin günlüğe kaydedildiğini doğrulayın

Üzerinde posta kutusu denetimi varsayılan olarak tüm posta kutularına yeni bir *DefaultAuditSet* özelliği ekler. Bu özelliğin değeri, varsayılan posta kutusu eylemlerinin (Microsoft tarafından yönetilen) posta kutusunda denetlenip denetlenmediğini gösterir.

Değeri kullanıcı posta kutularında veya paylaşılan posta kutularında görüntülemek için değerini posta kutusunun adı, diğer adı, e-posta adresi veya kullanıcı asıl adı (kullanıcı adı) ile değiştirin \<MailboxIdentity\> ve PowerShell'Exchange Online aşağıdaki komutu çalıştırın:

```PowerShell
Get-Mailbox -Identity <MailboxIdentity> | Format-List DefaultAuditSet
```

değeri Microsoft 365 grup posta kutularında görüntülemek için değerini paylaşılan posta kutusunun adı, diğer adı veya e-posta adresiyle değiştirin \<MailboxIdentity\> ve powershell'Exchange Online aşağıdaki komutu çalıştırın:

```PowerShell
Get-Mailbox -Identity <MailboxIdentity> -GroupMailbox | Format-List DefaultAuditSet
```

Değer `Admin, Delegate, Owner` aşağıdakileri gösterir:

- Üç oturum açma türünün de varsayılan posta kutusu eylemleri denetleniyor. Microsoft 365 Grubu posta kutularında göreceğiniz tek değer budur.
- Yönetici, kullanıcı posta kutusunda veya paylaşılan posta kutusunda herhangi bir oturum açma türü için denetlenen posta kutusu eylemlerini *değiştirmedi* . Kuruluşunuzda posta kutusu denetimi varsayılan olarak açıldıktan sonra bu varsayılan durumdur.

Yönetici bir oturum açma türü için denetlenen posta kutusu eylemlerini değiştirdiyse (**Set-Mailbox** cmdlet'indeki *AuditAdmin*, *AuditDelegate* veya *AuditOwner* parametrelerini kullanarak), özellik değeri farklı olacaktır.

Örneğin, kullanıcı posta kutusunda veya paylaşılan posta kutusunda *DefaultAuditSet* özelliğinin değeri `Owner` şunları gösterir:

- Posta kutusu sahibi için varsayılan posta kutusu eylemleri denetleniyor.
- ve `Admin` oturum açma türleri için `Delegate` denetlenen posta kutusu eylemleri varsayılan eylemlerden değiştirilmiştir.

*DefaultAuditSet* özelliği için boş bir değer, kullanıcı posta kutusunda veya paylaşılan posta kutusunda üç oturum açma türünün de posta kutusu eylemlerinin değiştirildiğini gösterir.

Daha fazla bilgi için bu makalenin [Varsayılan olarak günlüğe kaydedilen posta kutusu eylemlerini değiştirme veya geri yükleme](#change-or-restore-mailbox-actions-logged-by-default) bölümüne bakın

### <a name="display-the-mailbox-actions-that-are-being-logged-on-mailboxes"></a>Posta kutularında oturum açmakta olan posta kutusu eylemlerini görüntüleme

Kullanıcı posta kutularında veya paylaşılan posta kutularında oturum açmakta olan posta kutusu eylemlerini görmek için yerine \<MailboxIdentity\> posta kutusunun adını, diğer adını, e-posta adresini veya kullanıcı asıl adını (kullanıcı adı) yazın ve Exchange Online PowerShell'de aşağıdaki komutlardan birini veya daha fazlasını çalıştırın.

> [!NOTE]
> Microsoft 365 Grubu posta kutuları için aşağıdaki **Get-Mailbox** komutlarına anahtarı ekleyebilirsiniz `-GroupMailbox` ancak döndürülen değerlere inanmayın. Microsoft 365 Grubu posta kutuları için denetlenen varsayılan ve statik posta kutusu eylemleri, bu makalenin önceki bölümlerindeki [Microsoft 365 Grubu posta kutuları için posta kutusu eylemleri](#mailbox-actions-for-microsoft-365-group-mailboxes) bölümünde açıklanmıştır.

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

## <a name="change-or-restore-mailbox-actions-logged-by-default"></a>Varsayılan olarak günlüğe kaydedilen posta kutusu eylemlerini değiştirme veya geri yükleme

Daha önce açıklandığı gibi, posta kutusu denetiminin varsayılan olarak açık olmasının önemli avantajlarından biri şudur: Denetlenen posta kutuları eylemlerini yönetmeniz gerekmez. Microsoft bunu sizin için yapar ve yayımlandıklarında varsayılan olarak denetlenecek yeni posta kutusu eylemlerini otomatik olarak ekleriz.

Ancak, kuruluşunuzun kullanıcı posta kutuları ve paylaşılan posta kutuları için farklı bir posta kutusu eylemleri kümesini denetlemesi gerekebilir. Bu bölümdeki yordamlarda, her oturum açma türü için denetlenen posta kutusu eylemlerinin nasıl değiştirileceği ve Microsoft tarafından yönetilen varsayılan eylemlere nasıl geri dönüleceği gösterilmektedir.

> [!IMPORTANT]
> Kullanıcı posta kutularında veya paylaşılan posta kutularında oturum açan posta kutusu eylemlerini özelleştirmek için aşağıdaki yordamları kullanırsanız, Microsoft tarafından yayımlanan yeni varsayılan posta kutusu eylemleri bu posta kutularında otomatik olarak denetlenmeyecektir. Özelleştirilmiş eylem listenize yeni posta kutusu eylemlerini el ile eklemeniz gerekir.

### <a name="change-the-mailbox-actions-to-audit"></a>Posta kutusu eylemlerini denetlenecek şekilde değiştirme

Kullanıcı posta kutuları ve paylaşılan posta kutuları için denetlenen posta kutusu eylemlerini değiştirmek için **Set-Mailbox** cmdlet'indeki *AuditAdmin*, *AuditDelegate* veya *AuditOwner* parametrelerini kullanabilirsiniz (Microsoft 365 grup posta kutuları için denetlenen eylemler özelleştirilmez).

Posta kutusu eylemlerini belirtmek için iki farklı yöntem kullanabilirsiniz:

- Var olan posta kutusu eylemlerini şu söz dizimini kullanarak *değiştirin* (üzerine yaz). `action1,action2,...actionN`
- Bu söz dizimini kullanarak diğer mevcut değerleri etkilemeden posta kutusu eylemleri *ekleyin veya kaldırın*: `@{Add="action1","action2",..."actionN"}` veya `@{Remove="action1","action2",..."actionN"}`.

Bu örnek, SoftDelete ve HardDelete ile varsayılan eylemlerin üzerine yazarak "Gabriela Laureano" adlı posta kutusunun yönetici posta kutusu eylemlerini değiştirir.

```PowerShell
Set-Mailbox -Identity "Gabriela Laureano" -AuditAdmin HardDelete,SoftDelete
```

Bu örnek, posta kutusu laura@contoso.onmicrosoft.com MailboxLogin sahip eylemini ekler.

```PowerShell
Set-Mailbox -Identity laura@contoso.onmicrosoft.com -AuditOwner @{Add="MailboxLogin"}
```

Bu örnek, Ekip Tartışması posta kutusu için MoveToDeletedItems temsilci eylemini kaldırır.

```PowerShell
Set-Mailbox -Identity "Team Discussion" -AuditDelegate @{Remove="MoveToDeletedItems"}
```

Kullandığınız yöntemden bağımsız olarak, kullanıcı posta kutularında veya paylaşılan posta kutularında denetlenen posta kutusu eylemlerinin özelleştirilmesi aşağıdaki sonuçlara sahiptir:

- Özelleştirdiğiniz oturum açma türü için, denetlenen posta kutusu eylemleri artık Microsoft tarafından yönetilmeyin.
- Özelleştirdiğiniz oturum açma türü, [daha önce açıklandığı](#verify-that-default-mailbox-actions-are-being-logged-for-each-logon-type) gibi artık posta kutusunun *DefaultAuditSet* özellik değerinde görüntülenmez.

### <a name="restore-the-default-mailbox-actions"></a>Varsayılan posta kutusu eylemlerini geri yükleme

> [!NOTE]
> Aşağıdaki yordamlar Microsoft 365 Grubu posta kutuları için geçerli değildir ([burada](#mailbox-actions-for-microsoft-365-group-mailboxes) açıklandığı gibi varsayılan eylemlerle sınırlıdır).

Kullanıcı posta kutusunda veya paylaşılan posta kutusunda denetlenen posta kutusu eylemlerini özelleştirdiyseniz, bu söz dizimini kullanarak bir veya tüm oturum açma türleri için varsayılan posta kutusu eylemlerini geri yükleyebilirsiniz:

```PowerShell
Set-Mailbox -Identity <MailboxIdentity> -DefaultAuditSet <Admin | Delegate | Owner>
```

Virgülle ayrılmış birden çok *DefaultAuditSet* değeri belirtebilirsiniz

Bu örnek, posta kutusu mark@contoso.onmicrosoft.com tüm oturum açma türleri için varsayılan denetlenen posta kutusu eylemlerini geri yükler.

```PowerShell
Set-Mailbox -Identity mark@contoso.onmicrosoft.com -DefaultAuditSet Admin,Delegate,Owner
```

Bu örnek, posta kutusu chris@contoso.onmicrosoft.com Yönetici oturum açma türü için varsayılan denetlenen posta kutusu eylemlerini geri yükler, ancak Temsilci ve Sahip oturum açma türleri için özelleştirilmiş denetimli posta kutusu eylemlerini bırakır.

```PowerShell
Set-Mailbox -Identity chris@contoso.onmicrosoft.com -DefaultAuditSet Admin
```

Oturum açma türü için varsayılan olarak denetlenen posta kutusu eylemlerinin geri yüklenmesi aşağıdaki sonuçlara sahiptir:

- Geçerli posta kutusu eylemleri listesi, oturum açma türü için varsayılan posta kutusu eylemleriyle değiştirilir.
- Microsoft tarafından yayımlanan tüm yeni posta kutusu eylemleri, oturum açma türü için denetlenen eylemler listesine otomatik olarak eklenir.
- Posta kutusunun *DefaultAuditSet* özellik değeri, geri yüklenen oturum açma türünü içerecek şekilde güncelleştirilir.

## <a name="turn-off-mailbox-auditing-on-by-default-for-your-organization"></a>Kuruluşunuz için posta kutusu denetimini varsayılan olarak kapatma

Exchange Online PowerShell'de aşağıdaki komutu çalıştırarak tüm kuruluşunuz için posta kutusu denetimini varsayılan olarak kapatabilirsiniz:

```PowerShell
Set-OrganizationConfig -AuditDisabled $true
```

Posta kutusu denetiminin varsayılan olarak kapatılması aşağıdaki sonuçlara sahiptir:

- Posta kutusu denetimi kuruluşunuz için devre dışı bırakıldı.
- Posta kutusu denetimini varsayılan olarak devre dışı bırakdığınızdan, bir posta kutusunda denetim etkin olsa bile hiçbir posta kutusu eylemi denetlenmiyor (posta kutusunun *AuditEnabled* özelliği **True'dur**).
- Posta kutusu denetimi yeni posta kutuları için etkinleştirilmez ve yeni veya mevcut bir posta kutusunda *AuditEnabled* özelliğini **True** olarak ayarlamak yoksayılır.
- Tüm posta kutusu denetim atlama ilişkilendirme ayarları ( **Set-MailboxAuditBypassAssociation** cmdlet'i kullanılarak yapılandırılır) yoksayılır.
- Mevcut posta kutusu denetim kayıtları, kaydın denetim günlüğü yaş sınırı sona erene kadar korunur.

### <a name="turn-on-mailbox-auditing-on-by-default"></a>Posta kutusu denetimini varsayılan olarak açma

Kuruluşunuzda posta kutusu denetimini yeniden açmak için Exchange Online PowerShell'de aşağıdaki komutu çalıştırın:

```PowerShell
Set-OrganizationConfig -AuditDisabled $false
```

## <a name="bypass-mailbox-audit-logging"></a>Posta kutusu denetim günlüğünü atlama

Şu anda, kuruluşunuzda posta kutusu denetimi varsayılan olarak açık olduğunda belirli posta kutuları için posta kutusu denetimini devre dışı bırakamazsınız. Örneğin, *AuditEnabled* posta kutusu özelliğini **False** olarak ayarlamak yoksayılır.

Ancak, eylemlerin nerede gerçekleştiğine bakılmaksızın, belirtilen kullanıcıların *tüm posta kutusu* eylemlerinin günlüğe kaydedilmesini önlemek için Exchange Online PowerShell'de **Set-MailboxAuditBypassAssociation** cmdlet'ini kullanmaya devam edebilirsiniz. Örneğin:

- Atlanan kullanıcılar tarafından gerçekleştirilen posta kutusu sahibi eylemleri günlüğe kaydedilmez.
- Diğer kullanıcıların posta kutularında atlanan kullanıcılar tarafından gerçekleştirilen temsilci eylemleri (paylaşılan posta kutuları dahil) günlüğe kaydedilmez.
- Atlanan kullanıcılar tarafından gerçekleştirilen yönetici eylemleri günlüğe kaydedilmez.

Belirli bir kullanıcının posta kutusu denetim günlüğünü atlamak için değerini kullanıcının adı, e-posta adresi, diğer ad veya kullanıcı asıl adı (kullanıcı adı) ile değiştirin \<MailboxIdentity\> ve aşağıdaki komutu çalıştırın:

```PowerShell
Set-MailboxAuditBypassAssociation -Identity <MailboxIdentity> -AuditByPassEnabled $true
```

Belirtilen kullanıcı için denetimin atlandığını doğrulamak için aşağıdaki komutu çalıştırın:

```PowerShell
Get-MailboxAuditBypassAssociation -Identity <MailboxIdentity> | Format-List AuditByPassEnabled
```

**True** değeri, kullanıcı için posta kutusu denetim günlüğünün atlandığını gösterir.

## <a name="more-information"></a>Daha fazla bilgi

- Posta kutusu denetim günlüğü tüm kuruluşlar için varsayılan olarak etkin olsa da, yalnızca [Gelişmiş Denetim özelliğini içeren lisanslara](auditing-solutions-overview.md#advanced-audit-1) sahip kullanıcılar (topluca *E5/A5/G5 lisansları* olarak adlandırılır) Microsoft 365 uyumluluk merkezi veya [Office 365 Yönetim Etkinliği](/office/office-365-management-api/office-365-management-activity-api-reference) [API'sini](search-the-audit-log-in-security-and-compliance.md) **kullanarak denetim günlüğü aramalarında posta kutusu denetim günlüğü olaylarını döndürür varsayılan olarak**.

  E5/A5/G5 lisansı olmayan kullanıcıların posta kutusu denetim günlüğü girdilerini almak için aşağıdaki geçici çözümlerden birini kullanabilirsiniz:

  - Aşağıdaki komutu çalıştırarak etkilenen kullanıcı posta kutularında posta kutusu denetimini el ile etkinleştirin: `Set-Mailbox -Identity <MailboxIdentity> -AuditEnabled $true`. Posta kutusunda posta kutusu denetimini etkinleştirdikten sonra, Microsoft 365 uyumluluk merkezi veya Office 365 Yönetim Etkinliği API'sini kullanarak denetim günlüğü aramalarını kullanabilirsiniz.

    > [!NOTE]
    > Posta kutusu denetimi posta kutusunda zaten etkin görünüyorsa ancak aramalarınız sonuç döndürmezse *AuditEnabled* parametresinin `$false` değerini olarak değiştirin ve sonra öğesine geri dönün `$true`.

  - Exchange Online PowerShell'de aşağıdaki cmdlet'leri kullanın:
    - Belirli kullanıcılar için posta kutusu denetim günlüğünde arama yapmak için [Search-MailboxAuditLog](/powershell/module/exchange/search-mailboxauditlog).
    - Belirli kullanıcılar için posta kutusu denetim günlüğünde arama yapmak ve sonuçların belirtilen alıcılara e-posta yoluyla gönderilmesini sağlamak için [New-MailboxAuditLogSearch](/powershell/module/exchange/new-mailboxauditlogsearch).

  - Aşağıdaki eylemleri gerçekleştirmek için Exchange Online'daki Exchange yönetim merkezini (EAC) kullanın:
    - [Posta kutusu denetim günlüklerini dışarı aktarma](/Exchange/security-and-compliance/exchange-auditing-reports/export-mailbox-audit-logs)
    - [Sahip olmayan posta kutusu erişim raporu çalıştırma](/Exchange/security-and-compliance/exchange-auditing-reports/non-owner-mailbox-access-report)

- Varsayılan olarak, posta kutusu denetim günlüğü kayıtları silinmeden önce 90 gün boyunca saklanır. Exchange Online PowerShell'deki **Set-Mailbox** cmdlet'indeki *AuditLogAgeLimit* parametresini kullanarak denetim günlüğü kayıtlarının yaş sınırını değiştirebilirsiniz. Ancak bu değeri artırmak, denetim günlüğünde 90 günden eski olayları aramanıza izin vermez.

  Yaş sınırını artırırsanız, kullanıcının posta kutusu denetim günlüğünde 90 günden eski kayıtları aramak için Exchange Online PowerShell'de [Search-MailboxAuditLog](/powershell/module/exchange/search-mailboxauditlog) cmdlet'ini kullanmanız gerekir.

- Kuruluş için varsayılan olarak açık olan posta kutusu denetiminden önce bir posta kutusunun *AuditLogAgeLimit* özelliğini değiştirdiyseniz, posta kutusunun mevcut denetim günlüğü yaş sınırı değiştirilmez. Başka bir deyişle, varsayılan olarak üzerinde posta kutusu denetimi, posta kutusu denetim kayıtları için geçerli yaş sınırını etkilemez.

- Microsoft 365 Grubu posta kutusunda *AuditLogAgeLimit* değerini değiştirmek için, anahtarı **Set-Mailbox** komutuna eklemeniz `-GroupMailbox` gerekir.

- Posta kutusu denetim günlüğü kayıtları, her kullanıcının posta kutusunun Kurtarılabilir Öğeler klasöründeki bir alt klasörde ( *Denetimler* olarak adlandırılır) depolanır. Posta kutusu denetim kayıtları ve Kurtarılabilir Öğeler klasörü hakkında aşağıdaki bilgileri aklınızda bulundurun:

  - Posta kutusu denetim kayıtları, Kurtarılabilir Öğeler klasörünün varsayılan olarak 30 GB olan depolama kotası (uyarı kotası 20 GB'tır) karşı sayılır. Depolama kotası aşağıdaki durumlarda otomatik olarak 100 GB'a (90 GB uyarı kotası ile) yükseltilir:
    - Bir posta kutusuna ayrı tutma yerleştirilir.
    - Posta kutusu, Uyumluluk Merkezi'ndeki bir bekletme ilkesine atanır.

  - Posta kutusu denetim kayıtları, [Kurtarılabilir Öğeler klasörünün klasör sınırına](/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits#mailbox-folder-limits) göre de sayılır. Denetimler alt klasöründe en fazla 3 milyon öğe (denetim kaydı) depolanabilir.

    > [!NOTE]
    > Varsayılan olarak üzerinde posta kutusu denetiminin depolama kotasını veya Kurtarılabilir Öğeler klasörünün klasör sınırını etkileme olasılığı düşüktür.

    - Kurtarılabilir Öğeler klasöründeki Denetimler alt klasöründeki öğelerin boyutunu ve sayısını görüntülemek için Exchange Online PowerShell'de aşağıdaki komutu çalıştırabilirsiniz:

      ```PowerShell
      Get-MailboxFolderStatistics -Identity <MailboxIdentity> -FolderScope RecoverableItems | Where-Object {$_.Name -eq 'Audits'} | Format-List FolderPath,FolderSize,ItemsInFolder
      ```

    - Kurtarılabilir Öğeler klasöründeki bir denetim günlüğü kaydına doğrudan erişemezsiniz; bunun yerine, **Search-MailboxAuditLog** cmdlet'ini kullanır veya posta kutusu denetim kayıtlarını bulmak ve görüntülemek için denetim günlüğünde arama yaparsınız.

- Uyumluluk Merkezi'nde bir posta kutusu beklemeye alınırsa veya bekletme ilkesine atanırsa, denetim günlüğü kayıtları posta kutusunun *AuditLogAgeLimit* özelliği (varsayılan olarak 90 gün) tarafından tanımlanan süre boyunca korunur. Beklemedeki posta kutuları için denetim günlüğü kayıtlarını daha uzun süre tutmak için, posta kutusunun *AuditLogAgeLimit* değerini artırmanız gerekir.

- Çok coğrafi bir ortamda, coğrafi bölgeler arası posta kutusu denetimi desteklenmez. Örneğin, kullanıcıya farklı bir coğrafi konumdaki paylaşılan posta kutusuna erişim izinleri atanmışsa, bu kullanıcı tarafından gerçekleştirilen posta kutusu eylemleri paylaşılan posta kutusunun posta kutusu denetim günlüğüne kaydedilmez. Exchange yönetici denetim olayları şu anda yalnızca varsayılan konum için kullanılabilir.
