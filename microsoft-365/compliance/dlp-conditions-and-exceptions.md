---
title: DLP ilkesi koşulları, özel durumlar ve eylemler
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
audience: Admin
ms.topic: reference
ms.service: O365-seccomp
ms.localizationpriority: ''
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
recommendations: false
description: dlp ilkesi koşulları ve özel durumları hakkında bilgi
ms.openlocfilehash: a0354fe6392d739fa1b616e92625b7507cca823f
ms.sourcegitcommit: 6f3bc00a5cf25c48c61eb3835ac069e9f41dc4db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2022
ms.locfileid: "63010732"
---
# <a name="dlp-policy-conditions-exceptions-and-actions"></a>DLP ilkesi koşulları, özel durumlar ve eylemler

DLP ilkelerine uygulanan koşullar ve özel durumlar, ilkenin uygulandığı hassas öğeleri tanımlamaktadır. Eylemler, bir özel durum koşuluna neden olan bir sonuç olduğunu tanımlar.

- Koşullar nelerin dahil olduğunu tanımlar
- Özel durumlar, neyin hariç tutulacaklarını tanımlar.
- Eylemler, bir koşul veya özel durum ile karşılaş karşılaşmanın bir koşul veya özel durum olduğunu tanımlar

Çoğu kural ve özel durumun bir veya birden çok değeri destekleyen tek bir özelliği vardır. Örneğin, DLP ilkesi e-postalara Exchange, Gönderen koşula göre iletinin göndereni  gerektirir. Bazı koşulların iki özelliği vardır. Örneğin, **A ileti** üst bilgisi bu sözcüklerden herhangi birini içerir koşulu, ileti üst bilgisi alanını belirtmek için bir özellik, üst bilgi alanında bakıla metni belirtmek için de ikinci bir özellik gerektirir. Bazı koşulların veya özel durumların hiçbir özelliği yok. Örneğin, Ek **parola korumalı bir koşuldur** ve yalnızca parola korumalı olan iletilerde ekleri okur.

Eylemler genellikle ek özellikler gerektirir. Örneğin, DLP ilke kuralı bir iletiyi yeniden yönlendirse, iletinin nereye yönlendir yönlendirmesi olduğunu belirtmeniz gerekir.
<!-- Some actions have multiple properties that are available or required. For example, when the rule adds a header field to the message header, you need to specify both the name and value of the header. When the rule adds a disclaimer to messages, you need to specify the disclaimer text, but you can also specify where to insert the text, or what to do if the disclaimer can't be added to the message. Typically, you can configure multiple actions in a rule, but some actions are exclusive. For example, one rule can't reject and redirect the same message.-->

## <a name="conditions-and-exceptions-for-dlp-policies"></a>DLP ilkeleri için koşullar ve özel durumlar

Aşağıdaki bölümlerdeki tablolarda, DLP'de kullanılabilen koşullar ve özel durumlar açıklanmaktadır.

- [Gönderenler](#senders)
- [Alıcılar](#recipients)
- [İleti konusu veya gövdesi](#message-subject-or-body)
- [Ekler](#attachments)
- [İleti üst bilgileri](#message-headers)
- [İleti özellikleri](#message-properties)

### <a name="senders"></a>Gönderenler

Gönderen adresini bir koşul veya özel durum olarak kullanırsanız, değerin baktığı gerçek alan kullandığınız kuralın türüne bağlı olarak değişir. DLP tabanlı kurallar için, gönderen adresi olarak Zarf adresi kullanılır. Daha Exchange Aktarım kuralları için, Gönderen adresi olarak Üst bilgi adresi kullanılır.

<!--
> [!NOTE]
> Starting January 20, 2022, the default sender address location will be moved to the Header address along with the availability of the -SenderAddressLocation parameter to configure desired behavior at a DLP rule level.

![image](https://user-images.githubusercontent.com/53205984/145942298-6b435ba6-d146-44fe-a1c5-58babeaf8d7a.png)

At the tenant level, you can configure a sender address location to be used across all rules, unless overridden by a single rule. To revert tenant DLP policy configuration to evaluate the sender address from the Envelope across all rules, you can run the following command:

```PowerShell
Set-PolicyConfig –SenderAddressLocation Envelope
```

To configure the sender address location at a DLP rule level, the parameter is _SenderAddressLocation_. The available values are:

- **Header**: Only examine senders in the message headers (for example, the **From**, **Sender**, or **Reply-To** fields). This is the default value.

- **Envelope**: Only examine senders from the message envelope (the **MAIL FROM** value that was used in the SMTP transmission, which is typically stored in the **Return-Path** field).

- **Header or envelope** (`HeaderOrEnvelope`) Examine senders in the message header and the message envelope.
<br>
-->
|DLP'de koşul veya özel durum|PowerShell'de koşul/özel Microsoft 365 parametreleri|özellik türü|açıklama|
|---|---|---|---|
|Gönderen:|koşul: *Ilk* <br/> özel durum: *ExceptIfFrom*|Adresler|Belirtilen posta kutuları, posta kullanıcıları, posta kişileri veya kuruluş Microsoft 365 tarafından gönderilen iletiler.|
|Gönderen, |_FromMemberOf_ <br/> _ExceptIfFromMemberOf_|Adresler|Belirtilen dağıtım grubunun, posta etkin güvenlik grubunun veya grup grubunun bir üyesi tarafından Microsoft 365.|
|Gönderen IP adresi:|koşul: *SenderIPRanges*<br/> özel durum: *ExceptIfSenderIPRanges*|IPAddressRanges|Gönderenin IP adresi belirtilen IP adresiyle eş eşleşen veya belirtilen IP adresi aralığı içinde yer alan iletiler.|
|Gönderen adresi sözcükler içeriyor|koşul: *FromAddressContainsWords* <br/> özel durum: *ExceptIfFromAddressContainsWords*|Sözcükler|Gönderenin e-posta adresine belirtilen sözcükleri içeren iletiler.|
|Gönderen adresi desenlere eşler|koşul: *FromAddressMatchesPatterns* <br/> özel durum: *ExceptFromAddressMatchesPatterns*|Desenler|Gönderenin e-posta adresinin belirtilen normal ifadeler ile eşleşmesi için metin düzenleri içeren iletiler.|
|Gönderen etki alanı:|koşul: *SenderDomainIs* <br/> özel durum: *ExceptIfSenderDomainIs*|DomainName|Gönderenin e-posta adresinin etki alanının belirtilen değerle eş eş olduğu iletiler. Belirtilen etki alanını içeren gönderen etki alanlarını (örneğin, etki alanının herhangi bir alt etki alanını) bulmanız gerekirse, Gönderen adresi eşleşmeleri **(***FromAddressMatchesPatterns*) koşul işlevini kullanın ve '\.domaincom\.$' söz dizimi kullanarak etki alanını belirtin.|
|Gönderen kapsamı|koşul: *FromScope* <br/> özel durum: *ExceptIfFromScope*|UserScopeFrom|İç veya dış gönderenler tarafından gönderilen iletiler.|
|Gönderenin belirtilen özellikleri, bu sözcüklerden herhangi birini içerir|koşul: *SenderADAttributeContainsWords* <br/> özel durum: *ExceptIfSenderADAttributeContainsWords*|İlk özellik: `ADAttribute` <p> İkinci özellik: `Words`|Gönderenin belirtilen Active Directory özniteliğinin belirtilen sözcüklerden herhangi birini içerdiği iletiler.|
|Gönderenin belirtilen özellikleri bu metin düzenleri ile eşler|koşul: *SenderADAttributeMatchesPatterns* <br/> özel durum: *ExceptIfSenderADAttributeMatchesPatterns*|İlk özellik: `ADAttribute` <p> İkinci özellik: `Patterns`|Gönderenin belirtilen Active Directory özniteliğinde belirtilen normal ifadeler ile eşleşmeye sahip metin düzenleri içeren iletiler.|
|

### <a name="recipients"></a>Alıcılar

<br>

****

|DLP'de koşul veya özel durum|PowerShell'de koşul/özel Microsoft 365 parametreleri|özellik türü|açıklama|
|---|---|---|---|
|Alıcı|koşul: *SentTo* <br/> özel durum: *ExceptIfSentTo*|Adresler|Alıcılardan birinin belirtilen posta kutusu, posta kullanıcısı veya kuruluşta posta kişisi olduğu iletiler. Alıcılar iletinin İlk, **Bilgi** veya **Gizli** alanlarında olabilir.|
|Alıcı etki alanı:|koşul: *RecipientDomainIs* <br/> özel durum: *ExceptIfRecipientDomainIs*|DomainName|Alıcının e-posta adresinin etki alanının belirtilen değerle eş eş olduğu iletiler.|
|Alıcı adresi sözcükler içeriyor|koşul: *AnyOfRecipientAddressContainsWords* <br/> özel durum: *ExceptIfAnyOfRecipientAddressContainsWords*|Sözcükler|Alıcının e-posta adresine belirtilen sözcükleri içeren iletiler. <br/>**Not**: Bu koşul, alıcı ara sunucu adreslerine gönderilen iletileri dikkate alınmaz. Yalnızca alıcının birincil e-posta adresine gönderilen iletiyle eşler.|
|Alıcı adresi desenlere eşler|koşul: *AnyOfRecipientAddressMatchesPatterns* <br/> özel durum: *ExceptIfAnyOfRecipientAddressMatchesPatterns*|Desenler|Alıcının e-posta adresinin belirtilen normal ifadeleri ile eşleşmesi için metin düzenleri içeren iletiler. <br/> **Not**: Bu koşul, alıcı ara sunucu adreslerine gönderilen iletileri dikkate alınmaz. Yalnızca alıcının birincil e-posta adresine gönderilen iletiyle eşler.|
|Şu üyeye gönderildi:|koşul: *SentToMemberOf* <br/> özel durum: *ExceptIfSentToMemberOf*|Adresler|Belirtilen dağıtım grubunun, posta etkin güvenlik grubunun veya bir Grup grubunun üyesi olan alıcıları Microsoft 365 iletiler. Grup, iletinin **İlk**, **Bilgi** **veya Gizli** alanlarında olabilir.|
|Alıcının belirtilen özellikleri arasında bu sözcüklerden herhangi biri vardır |_RecipientADAttributeContainsWords_ <br/> _ExceptIfRecipientADAttributeContainsWords_|İlk özellik: `ADAttribute` <p> İkinci özellik: `Words`|Bir alıcının belirtilen Active Directory özniteliğinin belirtilen sözcüklerden herhangi birini içerdiği iletiler. <p> Ülke özniteliğinin **iki** harfli ülke kodu değerini gerektirdiğini unutmayın (örneğin, Almanya için DE).|
|Alıcının belirtilen özellikleri bu metin düzenleri ile eşler |_RecipientADAttributeMatchesPatterns_ <br/> _ExceptIfRecipientADAttributeMatchesPatterns_|İlk özellik: `ADAttribute` <p> İkinci özellik: `Patterns`|Bir alıcının belirtilen Active Directory özniteliğinde belirtilen normal ifadeler ile eşleşmeye sahip metin düzenleri içeren iletiler.|
|

### <a name="message-subject-or-body"></a>İleti konusu veya gövdesi

<br>

****

|DLP'de koşul veya özel durum|PowerShell'de koşul/özel Microsoft 365 parametreleri|özellik türü|açıklama|
|---|---|---|---|
|Konu sözcük veya tümcecik içeriyor|koşul: *SubjectContainsWords* <br/> özel durum: *ExceptIf SubjectContainsWords*|Sözcükler|Konu alanında belirtilen sözcüklerin yer alan iletiler.|
|Konu eşleşmeleri desenlerini|koşul: *SubjectMatchesPatterns* <br/> özel durum: *ExceptIf SubjectMatchesPatterns*|Desenler|Konu alanında belirtilen normal ifadeler ile eşleşmeye sahip metin düzenleri içeren iletiler.|
|İçerik içeriği|koşul: *ContentContainsSensitiveInformation* <br/> *exceptionIfContentContainsSensitiveInformation*|SensitiveInformationTypes|Veri kaybı önleme (DLP) ilkeleri tarafından tanımlandığı şekilde hassas bilgiler içeren iletiler veya belgeler.|
|Konu veya Gövde eşleşmeleri deseni|koşul: *SubjectOr BirAmatchesPatterns* <br/> özel durum: *ExceptIfSubjectOr BiramatchesPatterns*|Desenler|Konu alanı veya ileti gövdesinin belirtilen normal ifadeler ile eşleşmesi için metin düzenleri içeren iletiler.|
|Konu veya Gövde sözcük içeriyor|koşul: *SubjectOrWordsContainsWords* <br/> özel durum: *ExceptIfSubjectOrContainsWords*|Sözcükler|Konu alanında veya ileti gövdesinde belirtilen sözcüklerin yer alan iletiler|
|

### <a name="attachments"></a>Ekler

<br>

****

|DLP'de koşul veya özel durum|PowerShell'de koşul/özel Microsoft 365 parametreleri|özellik türü|açıklama|
|---|---|---|---|
|Ek parola korumalıdır|koşul: *DocumentIsPasswordProtected* <br/> özel durum: *ExceptIfDocumentIsPasswordProtected*|yok|Ekin parola korumalı olduğu (ve dolayısıyla taranamaz) iletiler. Parola algılama yalnızca Office, dosya .zip .7z dosyalarında çalışır.|
|Ekin dosya uzantısı|koşul: *ContentExtensionMatchesWords* <br/> özel durum: *ExceptIfContentExtensionMatchesWords*|Sözcükler|Ekin dosya uzantısının belirtilen sözcüklerden herhangi biri ile eş eşleşen iletiler.|
|E-posta eklerinin içeriği taranamadı|koşul: *DocumentIsUnsupported* <br/>özel durum: *ExceptIf DocumentIsUnsupported*|yok|Ekin yerel olarak tanınmıyor olduğu iletiler Exchange Online.|
|Herhangi bir e-posta ekin içeriğinin tarama işlemi tamamlanmadı|koşul: *ProcessingLimitExceeded* <br/> özel durum: *ExceptIfProcessingLimitExceeded*|yok|Kural altyapısının ekleri taramayı tamamlayamadım iletileri. İçeriğin tümüyle taranamadığında iletileri tanımlamak ve işlemede birlikte çalışacak kurallar oluşturmak için bu koşulu kullanabilirsiniz.|
|Belge adı sözcük içeriyor|koşul: *DocumentNameMatchesWords* <br/> özel durum: *ExceptIfDocumentNameMatchesWords*|Sözcükler|Ekin dosya adının belirtilen sözcüklerden herhangi biri ile eş eşleşen iletiler.|
|Belge adı desenlere eşler|koşul: *DocumentNameMatchesPatterns* <br/> özel durum: *ExceptIfDocumentNameMatchesPatterns*|Desenler|Bir ekin dosya adının belirtilen normal ifadeleri ile eşleşmesi için metin düzenleri içeren iletiler.|
|Belge özelliği şu şekildedir:|koşul: *ContentPropertyContainsWords* <br/> özel durum: *ExceptIfContentPropertyContainsWords*|Sözcükler|Ekin dosya uzantısının belirtilen sözcüklerden herhangi biri ile eş eşleşen iletiler veya belgeler.|
|Belge boyutu eşit veya büyüktür|koşul: *DocumentSizeOver* <br/> özel durum: *ExceptIfDocumentSizeOver*|Boyut|Herhangi bir ek belirtilen değerden büyük veya eşit olan iletiler.|
|Eklerin içeriğinde bu sözcüklerden herhangi biri yer|koşul: *DocumentContainsWords* <br/> özel durum: *ExceptIfDocumentContainsWords*|`Words`|Ekin belirtilen sözcükleri içerdiği iletiler.|
|Herhangi bir ek içeriği bu metin desenlerini eşler|koşul: *DocumentMatchesPatterns* <br/> özel durum: *ExceptIfDocumentMatchesPatterns*|`Patterns`|Bir ekin belirtilen normal ifadeleri ile eşleşmesi için metin düzenleri içeren iletiler.|
|

### <a name="message-headers"></a>İleti Üst Bilgileri

<br>

****

|DLP'de koşul veya özel durum|PowerShell'de koşul/özel Microsoft 365 parametreleri|özellik türü|açıklama|
|---|---|---|---|
|Üst bilgi sözcük veya tümcecik içeriyor|koşul: *HeaderContainsWords* <br/> özel durum: *ExceptIfHeaderContainsWords*|Karma Tablo|Belirtilen üst bilgi alanını içeren iletiler ve bu üst bilgi alanı değeri de belirtilen sözcükleri içerir.|
|Üst bilgi eşleşme düzenleri|koşul: *HeaderMatchesPatterns* <br/> özel durum: *ExceptIfHeaderMatchesPatterns*|Karma Tablo|Belirtilen üst bilgi alanını içeren iletiler ve bu üst bilgi alanı değeri de belirtilen normal ifadeleri içerir.|

### <a name="message-properties"></a>İleti özellikleri

<br>

****

|DLP'de koşul veya özel durum|PowerShell'de koşul/özel Microsoft 365 parametreleri|özellik türü|açıklama|
|---|---|---|---|
|Öneme sahip|koşul: *WithImportance* <br/> özel durum: *ExceptIfWithImportance*|Önem|Belirtilen önem düzeyiyle işaretlenmiş iletiler.|
|İçerik karakter kümesi sözcükler içeriyor|koşul: *ContentCharacterSetContainsWords* <br/> *ExceptIfContentCharacterSetContainsWords*|Karakter Kümeleri|Belirtilen karakter kümesi adlardan herhangi birini bulunduran iletiler.|
|Gönderen geçersiz k oldu mu|koşul: *HasSenderOverride* <br/> özel durum: *ExceptIfHasSenderOverride*|yok|Gönderenin veri kaybı önleme (DLP) politikasını geçersiz kılmayı seçtiği iletiler. DLP ilkeleri hakkında daha fazla bilgi için bkz [. Veri kaybını önleme hakkında bilgi](./dlp-learn-about-dlp.md)|
|İleti türü eşleşmeleri|koşul: *MessageTypeMatches* <br/> özel durum: *ExceptIfMessageTypeMatches*|MessageType|Belirtilen türde iletiler.|
|İleti boyutu, büyüktür veya eşittir|koşul: *MessageSizeOver* <br/> özel durum: *ExceptIfMessageSizeOver*|`Size`|Toplam boyutu (ileti artı ekleri) belirtilen değerden büyük veya buna eşit olan iletiler. **Not**: Posta kutularına ilişkin ileti boyutu sınırları, posta akışı kurallarında yer alan kurallardan önce değerlendirilir. Posta kutusu için fazla büyük olan bir ileti, bu koşula sahip bir kural ileti üzerinde eyleme geçemeden reddedilir.|
|

## <a name="actions-for-dlp-policies"></a>DLP ilkeleri için eylemler

Bu tabloda, DLP'de kullanılabilen eylemler açık bulunmaktadır.

<br>

****

|DLP'de eylem|Microsoft 365 PowerShell'de eylem parametreleri|özellik türü|açıklama|
|---|---|---|---|
|Üst bilgi ayarla|SetHeader|İlk özellik: *Üst Bilgi Adı* </br> İkinci özellik: *Üst Bilgi Değeri*|SetHeader parametresi, ileti üst bilgisinde üst bilgi alanı ve değer ekleyen veya değiştiren DLP kuralı için bir eylem belirtir. Bu parametre "HeaderName:HeaderValue" söz dizimi kullanılır. Virgülle ayrılmış birden çok üst bilgi adı ve değer çifti belirtebilirsiniz|
|Üst bilgi kaldır|RemoveHeader|İlk özellik: *MessageHeaderField*</br> İkinci özellik: *String*|RemoveHeader parametresi, DLP kuralı için bir eylem belirtir ve bu eylem ileti üst bilgilerinden üst bilgi alanını kaldırır. Bu parametre "Üst BilgiAdı" veya "ÜstbilgiAdı:ÜstbilgiDeğer" söz dizimi kullanılır. Virgülle ayrılmış birden çok üst bilgi adı, üst bilgi adı ve değer çifti belirtebilirsiniz|
|İletiyi belirli kullanıcılara yönlendirme|*RedirectMessageTo*|Adresler|İletiyi belirtilen alıcılara yeniden yönlendirer. İleti orijinal alıcılara teslim olmaz ve gönderene veya özgün alıcılara herhangi bir bildirim gönderilmez.|
|Onay için iletiyi gönderenin yöneticisine iletme|Orta|İlk özellik: *ModerateMessageByManager*</br> İkinci özellik: *Boole*|Moderate parametresi, e-posta iletisinizi moderatöre gönderen DLP kuralı için bir eylem belirtir. Bu parametre şu söz dizimi kullanır: @{ModerateMessageByManager = <$true \|$false>;|
|Onay için iletiyi belirli onaylayanlara iletme|Orta|İlk özellik: *ModerateMessageByUser*</br>İkinci özellik: *Adresler*|Moderate parametresi, e-posta iletisinizi moderatöre gönderen DLP kuralı için bir eylem belirtir. Bu parametre şu söz dizimlerini kullanır: @{ ModerateMessageByUser = @("emailaddress1","epostaadresi2",..."emailaddressN")}|
|Alıcı ekleme|AddRecipients|İlk özellik: *Alan*</br>İkinci özellik: *Adresler*|İletinin To/Bilgi/Gizli alanına bir veya daha fazla alıcı ekler. Bu parametre şu söz dizimlerini kullanır: @{<AddToRecipients \|CopyTo \|BlindCopyTo> = "emailaddress"}|
|Gönderenin yöneticisini alıcı olarak ekleme|AddRecipients|İlk özellik: *AddedManagerAction*</br>İkinci özellik: *Alan*|Gönderenin yöneticisini belirtilen alıcı türü (To, Bilgi, Gizli) olarak iletiye ekler veya gönderene ya da alıcıya bildirmeden iletiyi gönderenin yöneticisine yeniden yönlendirer. Bu eylem yalnızca gönderenin Manager özniteliği Active Directory'de tanımlandığı durumda çalışır. Bu parametre şu söz dizimi kullanır: @{AddManagerAsRecipientType = "<Bilgi \|\|Gizli>"}|
Konu için hazırlık|PrependSubject|Dize|Belirtilen metni iletinin Konu alanına ekler. Boşluk veya iki nokta üst üste (iki nokta üst üste) :) ifadesini özgün konu metninden ayırt etmek için, belirtilen metnin son karakteridir.</br>Aynı dizenin konu metni içeren iletilere (örneğin, yanıtlar) eklenmesini önlemek için, kurala "Konu sözcükler içerir" (ExceptIfSubjectContainsWords) özel durumu ekleyin.|
|HTML yasal uyarı uygulama|ApplyHtmlDisclaimer|Birinci özellik: *Metin*</br>İkinci özellik: *Konum*</br>Üçüncü özellik: *Geri dönüş eylemi*|İletinin gerekli bulunduğu konuma belirtilen HTML tekzlesini uygular.</br>Bu parametre şu söz dizimlerini kullanır: @{ Text = " " ; Konum = <Ekle \|Ekle>; FallbackAction = <Wrap Ignore \|Reject \|> }|
|Kullanıcı Office 365 İleti Şifrelemesi hakları korumasını kaldırma|RemoveRMSTemplate|yok|E-Office 365 uygulanan şifrelemeyi kaldırır|
|İletiyi barındırılan karantinaya teslim |_Karantina_|yok| Bu eylem şu anda genel **önizlemede.** Bu aşama sırasında, DLP ilkeleri tarafından karantinaya alınan e-postalar ilke türünü ExchangeTransportRule olarak gösterir.</br> İletiyi EOP'de karantinaya teslim ediyor. Daha fazla bilgi için bkz. [EOP'de e-posta iletileri karantinaya alınmış](/microsoft-365/security/office-365-security/quarantine-email-messages).|
|

<!--|Modify Subject|ModifySubject|PswsHashTable | Remove text from the subject line that matches a specific pattern and replace it with different text. See the example below. You can: </br>- **Replace** all matches in the subject with the replacement text </br>- **Append** to remove all matches in the subject and inserts the replacement text at the end of the subject. </br>- **Prepend** to remove all matches and inserts the replacement text at the beginning of the subject. See ModifySubject parameter in, /powershell/module/exchange/new-dlpcompliancerule|-->

