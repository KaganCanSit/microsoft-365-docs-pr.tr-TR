---
title: DLP ilke koşulları, özel durumlar ve eylemler
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
description: dlp ilkesi koşulları ve özel durumları hakkında bilgi edinin
ms.openlocfilehash: cd252002f2fcef3e3935dd44b1333e801bcba46d
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65090461"
---
# <a name="dlp-policy-conditions-exceptions-and-actions"></a>DLP ilke koşulları, özel durumlar ve eylemler

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

DLP ilkelerindeki koşullar ve özel durumlar, ilkenin uygulandığı hassas öğeleri tanımlar. Eylemler, bir özel durumun karşılanmasının bir sonucu olarak ne olacağını tanımlar.

- Koşullar nelerin dahil olduğunu tanımlar
- Özel durumlar nelerin hariç tutulacaklarını tanımlar.
- Eylemler, koşulun veya özel durumun karşılanmasının bir sonucu olarak ne olacağını tanımlar

Çoğu koşul ve özel durum, bir veya daha fazla değeri destekleyen bir özelliğe sahiptir. Örneğin, DLP ilkesi Exchange e-postalara uygulanıyorsa, **Gönderen** koşulu iletinin gönderenini gerektirir. Bazı koşulların iki özelliği vardır. Örneğin, **A ileti üst bilgisi bu sözcüklerden herhangi birini içerir** koşulu, ileti üst bilgisi alanını belirtmek için bir özellik ve üst bilgi alanında aranacak metni belirtmek için ikinci bir özellik gerektirir. Bazı koşulların veya özel durumların herhangi bir özelliği yoktur. Örneğin, **Ek parola korumalı koşulu yalnızca parola korumalı** iletilerdeki ekleri arar.

Eylemler genellikle ek özellikler gerektirir. Örneğin, DLP ilke kuralı bir iletiyi yeniden yönlendirdiğinde, iletinin nereye yönlendirileceğini belirtmeniz gerekir.
<!-- Some actions have multiple properties that are available or required. For example, when the rule adds a header field to the message header, you need to specify both the name and value of the header. When the rule adds a disclaimer to messages, you need to specify the disclaimer text, but you can also specify where to insert the text, or what to do if the disclaimer can't be added to the message. Typically, you can configure multiple actions in a rule, but some actions are exclusive. For example, one rule can't reject and redirect the same message.-->

## <a name="conditions-and-exceptions-for-dlp-policies"></a>DLP ilkeleri için koşullar ve özel durumlar

Aşağıdaki bölümlerde yer alan tablolar, DLP'de kullanılabilen koşulları ve özel durumları açıklar.

- [Gönderenler](#senders)
- [Alıcı](#recipients)
- [İleti konusu veya gövdesi](#message-subject-or-body)
- [Ekler](#attachments)
- [İleti üst bilgileri](#message-headers)
- [İleti özellikleri](#message-properties)

### <a name="senders"></a>Gönderenler

Gönderen adresini koşul veya özel durum olarak kullanırsanız, değerin arandığı gerçek alan, yapılandırılan gönderen adresi konumuna bağlı olarak değişir. Varsayılan olarak, DLP kuralları gönderen adresi olarak Üst Bilgi adresini kullanır.

![Zarf (P1) adresi ile Üst Bilgi (P2) adresi arasındaki farkı gösteren e-posta üst bilgisinin resmi](../media/dlp-conditions-exceptions-meetinginvite-callouts.png)

Kiracı düzeyinde, tek bir kural tarafından geçersiz kılınmadığı sürece, gönderen adresi konumunu tüm kurallarda kullanılacak şekilde yapılandırabilirsiniz. Tüm kurallar genelinde Zarf'tan gönderen adresini değerlendirmek üzere kiracı DLP ilkesi yapılandırmasını ayarlamak için aşağıdaki komutu çalıştırabilirsiniz:

```PowerShell
Set-PolicyConfig -SenderAddressLocation Envelope
```

Gönderen adresi konumunu DLP kural düzeyinde yapılandırmak için parametresi *SenderAddressLocation* parametresidir. Kullanılabilir değerler şunlardır:

- **Üst bilgi**: Yalnızca ileti üst bilgilerindeki gönderenleri inceleyin (örneğin, **Kimden**, **Gönderen** veya **Yanıtla** alanları). Bu, varsayılan değerdir.

- **Zarf**: Yalnızca ileti zarfından gönderenleri inceleyin (GENELLIKLE **Dönüş Yolu** alanında depolanan SMTP iletiminde kullanılan **MAIL FROM** değeri).

- **Üst bilgi veya zarf** (`HeaderOrEnvelope`) İleti üst bilgisinde ve ileti zarfında gönderenleri inceleyin.

|DLP'de koşul veya özel durum|Microsoft 365 PowerShell'de koşul/özel durum parametreleri|özellik türü|Açıklama|
|---|---|---|---|
|Gönderen|koşul: *Kimden* <br/><br/> özel durum: *ExceptIfFrom*|Adresler|Belirtilen posta kutuları, posta kullanıcıları, posta kişileri veya kuruluştaki Microsoft 365 grupları tarafından gönderilen iletiler.|
|Gönderen, |*FromMemberOf* <br/><br/> *ExceptIfFromMemberOf*|Adresler|Belirtilen dağıtım grubunun, posta özellikli güvenlik grubunun veya Microsoft 365 grubunun bir üyesi tarafından gönderilen iletiler.|
|Gönderen IP adresi|koşul: *SenderIPRanges*<br/><br/> exception: *ExceptIfSenderIPRanges*|IPAddressRanges|Gönderenin IP adresinin belirtilen IP adresiyle eşleştiği veya belirtilen IP adresi aralığı içinde yer aldığı iletiler.|
|Gönderen adresi sözcükler içeriyor|koşul: *FromAddressContainsWords* <br/><br/> exception: *ExceptIfFromAddressContainsWords*|Kelime|Gönderenin e-posta adresinde belirtilen sözcükleri içeren iletiler.|
|Gönderen adresi desenleri eşleştirir|koşul: *FromAddressMatchesPatterns* <br/><br/> özel durum: *ExceptFromAddressMatchesPatterns*|Desen|Gönderenin e-posta adresinin belirtilen normal ifadelerle eşleşen metin desenleri içerdiği iletiler.|
|Gönderen etki alanı|condition: *SenderDomainIs* <br/><br/> özel durum: *ExceptIfSenderDomainIs*|Etkialanıadı|Gönderenin e-posta adresinin etki alanının belirtilen değerle eşleştiği iletiler. Belirtilen etki alanını *içeren* gönderen etki alanlarını bulmanız gerekiyorsa (örneğin, bir etki alanının herhangi bir alt etki alanı), **Gönderen adresi eşleşmeleri** (*FromAddressMatchesPatterns*) koşulunu kullanın ve şu söz dizimini kullanarak etki alanını belirtin: '\.domaincom\.$'.|
|Gönderen kapsamı|koşul: *FromScope* <br/><br/> özel durum: *ExceptIfFromScope*|UserScopeFrom|İç veya dış gönderenler tarafından gönderilen iletiler.|
|Gönderenin belirtilen özellikleri bu sözcüklerden herhangi birini içerir|koşul: *SenderADAttributeContainsWords* <br/><br/> exception: *ExceptIfSenderADAttributeContainsWords*|İlk özellik: `ADAttribute` <br/><br/> İkinci özellik: `Words`|Gönderenin belirtilen Active Directory özniteliğinin belirtilen sözcüklerden herhangi birini içerdiği iletiler.|
|Gönderenin belirtilen özellikleri bu metin desenlerine uyuyor|koşul: *SenderADAttributeMatchesPatterns* <br/><br/> exception: *ExceptIfSenderADAttributeMatchesPatterns*|İlk özellik: `ADAttribute` <br/><br/> İkinci özellik: `Patterns`|Gönderenin belirtilen Active Directory özniteliğinin belirtilen normal ifadelerle eşleşen metin desenleri içerdiği iletiler.|

### <a name="recipients"></a>Alıcı

|DLP'de koşul veya özel durum|Microsoft 365 PowerShell'de koşul/özel durum parametreleri|özellik türü|Açıklama|
|---|---|---|---|
|Alıcı|koşul: *SentTo* <br/><br/> özel durum: *ExceptIfSentTo*|Adresler|Alıcılardan birinin kuruluştaki belirtilen posta kutusu, posta kullanıcısı veya posta kişisi olduğu iletiler. Alıcılar iletinin **Kime**, **Bilgi** veya **Gizli** alanlarında olabilir.|
|Alıcı etki alanı|condition: *RecipientDomainIs* <br/><br/> exception: *ExceptIfRecipientDomainIs*|Etkialanıadı|Alıcının e-posta adresinin etki alanının belirtilen değerle eşleştiği iletiler.|
|Alıcı adresi sözcükler içeriyor|koşul: *AnyOfRecipientAddressContainsWords* <br/><br/> özel durum: *ExceptIfAnyOfRecipientAddressContainsWords*|Kelime|Alıcının e-posta adresinde belirtilen sözcükleri içeren iletiler. <br/><br/>**Not**: Bu koşul, alıcı proxy adreslerine gönderilen iletileri dikkate almaz. Yalnızca alıcının birincil e-posta adresine gönderilen iletilerle eşleşir.|
|Alıcı adresi desenleri eşleştirir|koşul: *AnyOfRecipientAddressMatchesPatterns* <br/><br/> özel durum: *ExceptIfAnyOfRecipientAddressMatchesPatterns*|Desen|Alıcının e-posta adresinin belirtilen normal ifadelerle eşleşen metin desenleri içerdiği iletiler. <br/><br/> **Not**: Bu koşul, alıcı proxy adreslerine gönderilen iletileri dikkate almaz. Yalnızca alıcının birincil e-posta adresine gönderilen iletilerle eşleşir.|
|Üyesine gönderildi|koşul: *SentToMemberOf* <br/><br/> exception: *ExceptIfSentToMemberOf*|Adresler|Belirtilen dağıtım grubunun, posta özellikli güvenlik grubunun veya Microsoft 365 grubunun üyesi olan alıcıları içeren iletiler. Grup iletinin **Kime**, **Bilgi** veya **Gizli** alanlarında olabilir.|
|Alıcının belirtilen özellikleri bu sözcüklerden herhangi birini içerir |*RecipientADAttributeContainsWords* <br/><br/> *ExceptIfRecipientADAttributeContainsWords*|İlk özellik: `ADAttribute` <br/><br/> İkinci özellik: `Words`|Alıcının belirtilen Active Directory özniteliğinin belirtilen sözcüklerden herhangi birini içerdiği iletiler. <br/><br/> **Country** özniteliğinin iki harfli ülke kodu değerini (örneğin, Almanya için DE) gerektirdiğini unutmayın.|
|Alıcının belirtilen özellikleri bu metin desenleri ile eşleşmektedir |*RecipientADAttributeMatchesPatterns* <br/><br/> *ExceptIfRecipientADAttributeMatchesPatterns*|İlk özellik: `ADAttribute` <br/><br/> İkinci özellik: `Patterns`|Alıcının belirtilen Active Directory özniteliğinin belirtilen normal ifadelerle eşleşen metin desenleri içerdiği iletiler.|

### <a name="message-subject-or-body"></a>İleti konusu veya gövdesi

|DLP'de koşul veya özel durum|Microsoft 365 PowerShell'de koşul/özel durum parametreleri|özellik türü|Açıklama|
|---|---|---|---|
|Konu sözcükleri veya tümcecikleri içerir|koşul: *SubjectContainsWords* <br/> exception: *ExceptIf SubjectContainsWords*|Kelime|Konu alanında belirtilen sözcükleri içeren iletiler.|
|Konu desenleri eşleştirir|koşul: *SubjectMatchesPatterns* <br/> exception: *ExceptIf SubjectMatchesPatterns*|Desen|Konu alanının belirtilen normal ifadelerle eşleşen metin desenleri içerdiği iletiler.|
|İçerik içeriği|condition: *ContentContainsSensitiveInformation* <br/> exception *ExceptIfContentContainsSensitiveInformation*|SensitiveInformationTypes|Microsoft Purview Veri Kaybı Önleme (DLP) ilkeleri tarafından tanımlanan hassas bilgiler içeren iletiler veya belgeler.|
|Konu veya Gövde desenle eşleşir|koşul: *SubjectOrBodyMatchesPatterns* <br/> özel durum: *ExceptIfSubjectOrBodyMatchesPatterns*|Desen|Konu alanının veya ileti gövdesinin belirtilen normal ifadelerle eşleşen metin desenleri içerdiği iletiler.|
|Konu veya Gövde sözcükleri içeriyor|koşul: *SubjectOrBodyContainsWords* <br/> özel durum: *ExceptIfSubjectOrBodyContainsWords*|Kelime|Konu alanında veya ileti gövdesinde belirtilen sözcükleri içeren iletiler|
|

### <a name="attachments"></a>Ekler

|DLP'de koşul veya özel durum|Microsoft 365 PowerShell'de koşul/özel durum parametreleri|özellik türü|Açıklama|
|---|---|---|---|
|Ek parola korumalı|koşul: *DocumentIsPasswordProtected* <br/><br/> exception: *ExceptIfDocumentIsPasswordProtected*|Hiçbiri|Ekin parola korumalı olduğu (ve bu nedenle taranamazsınız) iletiler. Parola algılama yalnızca Office belgeler, .zip dosyaları ve .7z dosyaları için çalışır.|
|Ekin dosya uzantısı|condition: *ContentExtensionMatchesWords* <br/><br/> özel durum: *ExceptIfContentExtensionMatchesWords*|Kelime|Ekin dosya uzantısının belirtilen sözcüklerden herhangi biri ile eşleştiği iletiler.|
|E-posta eklerinin içeriği taranamadı|koşul: *DocumentIsUnsupported* <br/><br/>özel durum: *ExceptIf DocumentIsUnsupported*|yok|Ekin Exchange Online tarafından yerel olarak tanınmadığı iletiler.|
|E-posta eklerinin içeriği taramayı tamamlamadı|condition: *ProcessingLimitExceeded* <br/><br/> özel durum: *ExceptIfProcessingLimitExceeded*|yok|Kural altyapısının eklerin taranma işlemini tamamlayamadığı iletiler. İçeriğin tam olarak taranamadığı iletileri tanımlamak ve işlemek için birlikte çalışan kurallar oluşturmak için bu koşulu kullanabilirsiniz.|
|Belge adı sözcükler içeriyor|koşul: *DocumentNameMatchesWords* <br/><br/> exception: *ExceptIfDocumentNameMatchesWords*|Kelime|Ekin dosya adının belirtilen sözcüklerden herhangi biri ile eşleştiği iletiler.|
|Belge adı desenler ile eşleşir|koşul: *DocumentNameMatchesPatterns* <br/><br/> exception: *ExceptIfDocumentNameMatchesPatterns*|Desen|Ekin dosya adının belirtilen normal ifadelerle eşleşen metin desenleri içerdiği iletiler.|
|Belge özelliği şudur:|koşul: *ContentPropertyContainsWords* <br/><br/> exception: *ExceptIfContentPropertyContainsWords*|Kelime|Ekin dosya uzantısının belirtilen sözcüklerden herhangi biri ile eşleştiği iletiler veya belgeler.|
|Belge boyutu eşittir veya büyüktür|koşul: *DocumentSizeOver* <br/><br/> exception: *ExceptIfDocumentSizeOver*|Boyutu|Herhangi bir ekin belirtilen değerden büyük veya buna eşit olduğu iletiler.|
|Eklerin içeriği bu sözcüklerden herhangi birini içerir|koşul: *DocumentContainsWords* <br/><br/> exception: *ExceptIfDocumentContainsWords*|`Words`|Ekin belirtilen sözcükleri içerdiği iletiler.|
|Tüm ekler içeriği bu metin desenleriyle eşleşir|koşul: *DocumentMatchesPatterns* <br/><br/> exception: *ExceptIfDocumentMatchesPatterns*|`Patterns`|Ekin belirtilen normal ifadelerle eşleşen metin desenleri içerdiği iletiler.|

### <a name="message-headers"></a>İleti Üst Bilgileri

|DLP'de koşul veya özel durum|Microsoft 365 PowerShell'de koşul/özel durum parametreleri|özellik türü|Açıklama|
|---|---|---|---|
|Üst bilgi sözcükler veya tümcecikler içeriyor|koşul: *HeaderContainsWords* <br/><br/> özel durum: *ExceptIfHeaderContainsWords*|Karma Tablo|Belirtilen üst bilgi alanını içeren iletiler ve bu üst bilgi alanının değeri belirtilen sözcükleri içerir.|
|Üst bilgi desenleri eşleştirir|koşul: *HeaderMatchesPatterns* <br/><br/> exception: *ExceptIfHeaderMatchesPatterns*|Karma Tablo|Belirtilen üst bilgi alanını içeren iletiler ve bu üst bilgi alanının değeri belirtilen normal ifadeleri içerir.|

### <a name="message-properties"></a>İleti özellikleri

|DLP'de koşul veya özel durum|Microsoft 365 PowerShell'de koşul/özel durum parametreleri|özellik türü|Açıklama|
|---|---|---|---|
|Önem derecesiyle|koşul: *WithImportance* <br/><br/> özel durum: *ExceptIfWithImportance*|Önemi|Belirtilen önem düzeyiyle işaretlenmiş iletiler.|
|İçerik karakter kümesi sözcükler içeriyor|koşul: *ContentCharacterSetContainsWords* <br/><br/> *ExceptIfContentCharacterSetContainsWords*|CharacterSets|Belirtilen karakter kümesi adlarından herhangi birine sahip iletiler.|
|Gönderenin geçersiz kılmış olması|koşul: *HasSenderOverride* <br/><br/> özel durum: *ExceptIfHasSenderOverride*|yok|Gönderenin bir veri kaybı önleme (DLP) ilkesini geçersiz kılmayı seçtiği iletiler. DLP ilkeleri hakkında daha fazla bilgi için bkz. [Veri kaybını önleme hakkında bilgi edinin](./dlp-learn-about-dlp.md)|
|İleti türü eşleşir|condition: *MessageTypeMatches* <br/><br/> exception: *ExceptIfMessageTypeMatches*|Messagetype|Belirtilen türde iletiler. **Not**: Kullanılabilir ileti türleri Otomatik yanıt, Otomatik iletme, Şifrelenmiş (S/MIME), Takvim, İzin denetimi (hak yönetimi), Sesli mesaj, İmzalı, Okundu bilgisi ve Onay isteğidir. |
|İleti boyutu şuna eşit veya daha büyük|koşul: *MessageSizeOver* <br/><br/> exception: *ExceptIfMessageSizeOver*|`Size`|Toplam boyutun (ileti artı ekleri) belirtilen değerden büyük veya buna eşit olduğu iletiler. **Not**: Posta kutularındaki ileti boyutu sınırları, posta akışı kuralları öncesinde değerlendirilir. Bu koşula sahip bir kuralın ileti üzerinde işlem yapabilmesi için posta kutusu için çok büyük bir ileti reddedilir.|

## <a name="actions-for-dlp-policies"></a>DLP ilkeleri için eylemler

Bu tabloda DLP'de kullanılabilen eylemler açıklanmaktadır.

|DLP'de eylem|Microsoft 365 PowerShell'de eylem parametreleri|özellik türü|Açıklama|
|---|---|---|---|
|Üst bilgiyi ayarla|SetHeader|İlk özellik: *Üst Bilgi Adı* <br/><br/> İkinci özellik: *Üst Bilgi Değeri*|SetHeader parametresi, DLP kuralı için ileti üst bilgisine bir üst bilgi alanı ve değer ekleyen veya değiştiren bir eylem belirtir. Bu parametre "HeaderName:HeaderValue" söz dizimini kullanır. Virgülle ayrılmış birden çok üst bilgi adı ve değer çifti belirtebilirsiniz|
|Üst bilgiyi kaldır|RemoveHeader|İlk özellik: *MessageHeaderField*<br/><br/> İkinci özellik: *Dize*|RemoveHeader parametresi, DLP kuralı için ileti üst bilgisinden üst bilgi alanını kaldıran bir eylem belirtir. Bu parametre "HeaderName" veya "HeaderName:HeaderValue" söz dizimini kullanır. Virgülle ayrılmış birden çok üst bilgi adı veya üst bilgi adı ve değer çifti belirtebilirsiniz|
|İletiyi belirli kullanıcılara yeniden yönlendirme|*RedirectMessageTo*|Adresler|İletiyi belirtilen alıcılara yeniden yönlendirir. İleti özgün alıcılara teslim edilmemiştir ve gönderene veya özgün alıcılara bildirim gönderilmez.|
|Onay için iletiyi gönderenin yöneticisine iletme|Orta|İlk özellik: *ModerateMessageByManager*<br/><br/> İkinci özellik: *Boole dili*|Moderate parametresi, E-posta iletisini bir moderatöre gönderen DLP kuralı için bir eylem belirtir. Bu parametre şu söz dizimini kullanır: @{ModerateMessageByManager = <$true \|$false>;|
|Onay için iletiyi belirli onaylayanlara iletme|Orta|İlk özellik: *ModerateMessageByUser*<br/><br/>İkinci özellik: *Adresler*|Moderate parametresi, E-posta iletisini bir moderatöre gönderen DLP kuralı için bir eylem belirtir. Bu parametre şu söz dizimini kullanır: @{ ModerateMessageByUser = @("emailaddress1","emailaddress2",..."emailaddressN")}|
|Alıcı ekle|AddRecipients|İlk özellik: *Alan*<br/><br/>İkinci özellik: *Adresler*|İletinin Kime/Bilgi/Gizli alanına bir veya daha fazla alıcı ekler. Bu parametre şu söz dizimini kullanır: @{<AddToRecipients \<CopyTo \| BlindCopyTo\> = "emailaddress"}|
|Gönderenin yöneticisini alıcı olarak ekleme|AddRecipients|İlk özellik: *AddedManagerAction*<br/><br/>İkinci özellik: *Alan*|Gönderenin yöneticisini belirtilen alıcı türü olarak iletiye ekler (Kime, Bilgi, Gizli) veya gönderene veya alıcıya bildirmeden iletiyi gönderenin yöneticisine yönlendirir. Bu eylem yalnızca gönderenin Yöneticisi özniteliği Active Directory'de tanımlandığında çalışır. Bu parametre şu söz dizimini kullanır: @{AddManagerAsRecipientType = "\<To \| Cc \| Bcc\>"}|
Ekli konu|PrependSubject|Dize|Belirtilen metni iletinin Konu alanının başına ekler. Boşluk veya iki nokta üst üste kullanmayı göz önünde bulundurun (:) özgün konu metninden ayırt etmek için belirtilen metnin son karakteri olarak.<br/><br/>Aynı dizenin konu içindeki metni (örneğin, yanıtlar) içeren iletilere eklenmesini önlemek için kurala "Konu sözcükler içeriyor" (ExceptIfSubjectContainsWords) özel durumunu ekleyin.|
|HTML bildirimi uygulama|ApplyHtmlDisclaimer|İlk özellik: *Metin*<br/><br/>İkinci özellik: *Konum*<br/><br/>Üçüncü özellik: *Geri dönüş eylemi*|Belirtilen HTML bildirimini iletinin gerekli konumuna uygular.<br/><br/>Bu parametre söz dizimini kullanır: @{ Text = " " ; Konum = \<Append \| Prepend\>; FallbackAction = \<Wrap \| Ignore \| Reject\> }|
|İleti şifrelemesini ve hak korumasını kaldırma|RemoveRMSTemplate|yok|E-postaya uygulanan ileti şifrelemesini kaldırır|
|İletiyi barındırılan karantinaya teslim etme |*Karantina*|yok| Bu eylem şu anda **genel önizleme** aşamasındadır. Bu aşamada, DLP ilkeleri tarafından karantinaya alınan e-postalar, ilke türünü ExchangeTransportRule olarak gösterir.<br/><br/> EOP'de iletiyi karantinaya teslim eder. Daha fazla bilgi için bkz. [EOP'de karantinaya alınan e-posta iletileri](/microsoft-365/security/office-365-security/quarantine-email-messages).|
|Konuyu Değiştir|ModifySubject|PswsHashTable | Konu satırından belirli bir desenle eşleşen metni kaldırın ve farklı bir metinle değiştirin. Aşağıdaki örniğe bakın. Şunları yapabilirsiniz: <br/><br/>- Konu içindeki tüm eşleşmeleri değiştirme metniyle **değiştirme** <br/><br/>- Konu içindeki tüm eşleşmeleri kaldırmak için **sonuna ekleyin** ve konunun sonuna yeni metni ekler. <br/><br/>- Tüm eşleşmeleri kaldırmak için **önceden** ekleyin ve konunun başına yeni metni ekler. Bkz. ModifySubject parametresi, /powershell/module/exchange/new-dlpcompliancerule|
