---
title: EOP'de ASF ayarları
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: ITPro
ms.topic: conceptual
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: b286f853-b484-4af0-b01f-281fffd85e7a
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: Yöneticiler, Exchange Online Protection(EOP) içindeki istenmeyen posta önleme ilkelerinde kullanılabilen Gelişmiş İstenmeyen Posta Filtresi (ASF) ayarları hakkında bilgi edinebilir.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 75fca937049e71576e1dd599b4cc0f7fba2a2211
ms.sourcegitcommit: 725a92b0b1555572b306b285a0e7a7614d34e5e5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/24/2022
ms.locfileid: "65647677"
---
# <a name="advanced-spam-filter-asf-settings-in-eop"></a>EOP'de Gelişmiş İstenmeyen Posta Filtresi (ASF) ayarları

**Uygulandığı öğe**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Office 365 için Microsoft Defender plan 1 ve plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Tüm Microsoft 365 kuruluşlarda, EOP'deki istenmeyen posta önleme ilkelerindeki Gelişmiş İstenmeyen Posta Filtresi (ASF) ayarları, yöneticilerin iletileri belirli ileti özelliklerine göre istenmeyen posta olarak işaretlemesine olanak sağlar. ASF, genellikle istenmeyen postalarda bulunduğundan bu özellikleri özellikle hedefler. Özelliğine bağlı olarak ASF algılamaları iletiyi **İstenmeyen Posta** veya **Yüksek güvenilirlikli istenmeyen posta** olarak işaretler.

> [!NOTE]
> ASF ayarlarından birini veya daha fazlasını etkinleştirmek, istenmeyen posta filtrelemeye yönelik agresif bir yaklaşımdır. ASF tarafından yanlış pozitif olarak filtrelenen iletileri raporlayamazsınız. ASF tarafından filtrelenen iletileri şu şekilde tanımlayabilirsiniz:
>
> - İstenmeyen postalardan düzenli karantina bildirimleri ve yüksek güvenilirlikli istenmeyen posta filtresi kararları.
> - Karantinada filtrelenmiş iletilerin varlığı.
> - bu makalede açıklandığı gibi iletilere eklenen belirli `X-CustomSpam:` X üst bilgisi alanları.

Aşağıdaki bölümlerde, Microsoft 365 Defender portalında ve Exchange Online PowerShell veya tek başına EOP PowerShell'de ([New-HostedContentFilterPolicy](/powershell/module/exchange/new-hostedcontentfilterpolicy) ve [Set-HostedContentFilterPolicy](/powershell/module/exchange/set-hostedcontentfilterpolicy)) istenmeyen posta önleme ilkelerinde kullanılabilen ASF ayarları ve seçenekleri açıklanmaktadır. Daha fazla bilgi için bkz. [EOP'de istenmeyen posta önleme ilkelerini yapılandırma](configure-your-spam-filter-policies.md).

## <a name="enable-disable-or-test-asf-settings"></a>ASF ayarlarını etkinleştirme, devre dışı bırakma veya test edin

Her ASF ayarı için istenmeyen posta önleme ilkelerinde aşağıdaki seçenekler kullanılabilir:

- **Açık**: ASF, iletiye karşılık gelen X üst bilgisi alanını ekler ve iletiyi **İstenmeyen Posta** ( [İstenmeyen posta puanı ayarlarını artırmak](#increase-spam-score-settings) için SCL 5 veya 6) veya **Yüksek güvenilirlikli istenmeyen posta** ( [İstenmeyen posta olarak işaretle ayarları](#mark-as-spam-settings) için SCL 9) olarak işaretler.
- **Kapalı**: ASF ayarı devre dışı bırakıldı. Bu varsayılan değerdir ve değiştirmenizi öneririz.
- **Test**: ASF, iletiye karşılık gelen X üst bilgisi alanını ekler. İletiye ne olacağı **Test modu** (*TestModeAction*) değerine göre belirlenir:
  - **Yok**: İleti teslimi ASF algılamadan etkilenmez. İleti yine de EOP'deki diğer filtreleme türlerine ve kurallara tabidir.
  - **Varsayılan X üst bilgi metnini ekle (*AddXHeader*)**: İletiye X üst bilgisi değeri `X-CustomSpam: This message was filtered by the custom spam filter option` eklenir. İletinin teslimini etkilemek için Gelen Kutusu kurallarında veya posta akışı kurallarında (taşıma kuralları olarak da bilinir) bu değeri kullanabilirsiniz.
  - **Gizli ileti gönder (*BccMessage*)**: Belirtilen e-posta adresleri (PowerShell'de *TestModeBccToRecipients* parametre değeri) iletinin Gizli alanına eklenir ve ileti ek Gizli alıcılarına teslim edilir. Microsoft 365 Defender portalında, birden çok e-posta adresini noktalı virgülle (;)) ayırırsınız. PowerShell'de birden çok e-posta adresini virgülle ayırırsınız.

  **Notlar**:

  - Test modu aşağıdaki ASF ayarları için kullanılamaz:
    - **Koşullu Gönderen Kimliği filtreleme: sabit başarısız** (*MarkAsSpamFromAddressAuthFail*)
    - **NDR backscatter**(*MarkAsSpamNdrBackscatter*)
    - **SPF kaydı: sabit başarısız (***MarkAsSpamSpfRecordHardFail*)
  - Aynı test modu eylemi, **Test** olarak ayarlanmış *tüm* ASF ayarlarına uygulanır. Farklı ASF ayarları için farklı test modu eylemleri yapılandıramazsınız.

## <a name="increase-spam-score-settings"></a>İstenmeyen posta puanı ayarlarını artırma

Aşağıdaki **İstenmeyen posta puanını artır** ASF ayarları, algılanan iletilerin istenmeyen posta güvenilirlik düzeyini (SCL) bir **İstenmeyen posta** filtresi kararına ve istenmeyen posta önleme ilkelerindeki ilgili eyleme karşılık gelen 5 veya 6 olarak ayarlar.

|İstenmeyen posta önleme ilkesi ayarı|Açıklama|X üst bilgisi eklendi|
|---|---|---|
|**Uzak web sitelerine resim bağlantıları** <p> *IncreaseScoreWithImageLinks*|Uzak sitelere HTML etiketi bağlantıları içeren `<Img>` iletiler (örneğin, http kullanarak) istenmeyen posta olarak işaretlenir.|`X-CustomSpam: Image links to remote sites`|
|**URL'deki sayısal IP adresi** <p> *IncreaseScoreWithNumericIps*|Sayısal tabanlı URL'ler (genellikle IP adresleri) içeren iletiler istenmeyen posta olarak işaretlenir.|`X-CustomSpam: Numeric IP in URL`|
|**URL'yi başka bir bağlantı noktasına yönlendirme** <p> *IncreaseScoreWithRedirectToOtherPort*|80 (HTTP), 8080 (alternatif HTTP) veya 443 (HTTPS) dışındaki TCP bağlantı noktalarına yönlendiren köprüler içeren ileti istenmeyen posta olarak işaretlenir.|`X-CustomSpam: URL redirect to other port`|
|**.biz veya .info web sitelerine bağlantılar** <p> *IncreaseScoreWithBizOrInfoUrls*|İletinin gövdesindeki veya `.info` bağlantılarını içeren `.biz` iletiler istenmeyen posta olarak işaretlenir.|`X-CustomSpam: URL to .biz or .info websites`|

## <a name="mark-as-spam-settings"></a>İstenmeyen posta ayarları olarak işaretle

Aşağıdaki **İstenmeyen posta olarak işaretle** ASF ayarları, algılanan iletilerin SCL'sini 9 olarak ayarlar ve bu da **Yüksek güvenilirlikli istenmeyen posta** filtresi kararına ve istenmeyen posta önleme ilkelerindeki ilgili eyleme karşılık gelir.

|İstenmeyen posta önleme ilkesi ayarı|Açıklama|X üst bilgisi eklendi|
|---|---|---|
|**Boş iletiler** <p> *MarkAsSpamEmptyMessages*|Konusu olmayan iletiler, ileti gövdesinde içerik yok ve ekleri yüksek güvenilirlikli istenmeyen posta olarak işaretlenmez.|`X-CustomSpam: Empty Message`|
|**HTML'de eklenmiş etiketler** <p> *MarkAsSpamEmbedTagsInHtml*|HTML etiketleri içeren `<embed>` ileti yüksek güvenilirlikli istenmeyen posta olarak işaretlenir. <p> Bu etiket, bir HTML belgesine (sesler, videolar veya resimler gibi) farklı türde belgelerin eklenmesine olanak tanır.|`X-CustomSpam: Embed tag in html`|
|**HTML'de JavaScript veya VBScript** <p> *MarkAsSpamJavaScriptInHtml*|HTML'de JavaScript veya Visual Basic Script Edition kullanan iletiler yüksek güvenilirlikli istenmeyen posta olarak işaretlenir. <p> Bu betik oluşturma dilleri, belirli eylemlerin otomatik olarak gerçekleşmesine neden olmak için e-posta iletilerinde kullanılır.|`X-CustomSpam: Javascript or VBscript tags in HTML`|
|**HTML'de form etiketleri** <p> *MarkAsSpamFormTagsInHtml*|HTML etiketleri içeren `<form>` iletiler yüksek güvenilirlikli istenmeyen posta olarak işaretlenir. <p> Bu etiket web sitesi formları oluşturmak için kullanılır. E-posta reklamları genellikle alıcıdan bilgi istemek için bu etiketi içerir.|`X-CustomSpam: Form tag in html`|
|**HTML'de çerçeve veya iframe etiketleri** <p> *MarkAsSpamFramesInHtml*|veya `<iframe>` HTML etiketleri içeren `<frame>` iletiler yüksek güvenilirlikli istenmeyen posta olarak işaretlenir. <p> Bu etiketler, e-posta iletilerinde sayfayı metin veya grafik görüntülemek üzere biçimlendirmek için kullanılır.|`X-CustomSpam: IFRAME or FRAME in HTML`|
|**HTML'de web hataları** <p> *MarkAsSpamWebBugsInHtml*|*Web hatası* (*web işareti* olarak da bilinir), e-posta iletilerinde iletinin alıcı tarafından okunup okunmadığını belirlemek için kullanılan bir grafik öğesidir (genellikle bir piksel bir piksel kadar küçük). <p> Web hataları içeren iletiler yüksek güvenilirlikli istenmeyen posta olarak işaretlenir. <p> Yasal bültenler web hatalarını kullanabilir, ancak çoğu kişi bunu bir gizlilik ihlali olarak değerlendirmektedir. |`X-CustomSpam: Web bug`|
|**HTML'de nesne etiketleri** <p> *MarkAsSpamObjectTagsInHtml*|HTML etiketleri içeren `<object>` iletiler yüksek güvenilirlikli istenmeyen posta olarak işaretlenir. <p> Bu etiket, eklentilerin veya uygulamaların html penceresinde çalışmasına olanak tanır.|`X-CustomSpam: Object tag in html`|
|**Hassas sözcükler** <p> *MarkAsSpamSensitiveWordList*|Microsoft, rahatsız edici olabilecek iletilerle ilişkili sözcüklerin dinamik ancak düzenlenemez bir listesini tutar. <p> Konu veya ileti gövdesindeki hassas sözcük listesinden sözcükler içeren iletiler yüksek güvenilirlikli istenmeyen posta olarak işaretlenir.|`X-CustomSpam: Sensitive word in subject/body`|
|**SPF kaydı: sabit hata** <p> *MarkAsSpamSpfRecordHardFail*|Kaynak e-posta etki alanı için DNS'deki SPF Sender Policy Framework (SPF) kaydında belirtilmemiş bir IP adresinden gönderilen iletiler yüksek güvenilirlikli istenmeyen posta olarak işaretlenir. <p> Bu ayar için test modu kullanılamaz.|`X-CustomSpam: SPF Record Fail`|

Aşağıdaki **İstenmeyen posta ASF olarak işaretle** ayarları, algılanan iletilerin SCL'sini 6 olarak ayarlar. Bu, **istenmeyen posta** filtresi kararına ve istenmeyen posta önleme ilkelerindeki ilgili eyleme karşılık gelir.

|İstenmeyen posta önleme ilkesi ayarı|Açıklama|X üst bilgisi eklendi|
|---|---|---|
|**Gönderen Kimliği filtrelemesi sabit başarısız oldu** <p> *MarkAsSpamFromAddressAuthFail*|Koşullu Gönderen Kimliği denetiminde başarısız olan iletiler istenmeyen posta olarak işaretlenir. <p> Bu ayar, sahte gönderenleri içeren ileti üst bilgilerinden korunmaya yardımcı olmak için SPF denetimini Gönderen Kimliği denetimiyle birleştirir. <p> Bu ayar için test modu kullanılamaz.|`X-CustomSpam: SPF From Record Fail`|
|**Backscatter** <p> *MarkAsSpamNdrBackscatter*|*Backscatter* , e-posta iletilerindeki sahte gönderenlerin neden olduğu gereksiz teslim dışı raporlardır (NDR'ler veya geri dönen iletiler olarak da bilinir). Daha fazla bilgi için bkz. [Backscatter iletileri ve EOP](backscatter-messages-and-eop.md). <p> Geçerli NDR'ler teslim edildiğinden ve arka plan aracı istenmeyen posta olarak işaretlendiğinden bu ayarı aşağıdaki ortamlarda yapılandırmanız gerekmez: <ul><li>Exchange Online posta kutuları olan kuruluşları Microsoft 365.</li><li>EOP aracılığıyla *giden* e-postayı yönlendirdiğiniz şirket içi e-posta kuruluşları.</li></ul> <p> Şirket içi posta kutularına gelen e-postayı koruyan tek başına EOP ortamlarında, bu ayarı açmak veya kapatmak aşağıdaki sonucu içerir: <ul><li> **Açık**: Meşru NDR'ler teslim edilir ve geri ölçeklendirici istenmeyen posta olarak işaretlenir.</li><li>**Kapalı**: Yasal NDR'ler ve arka ölçeklendirici normal istenmeyen posta filtrelemeden geçer. Geçerli NDR'lerin çoğu özgün ileti gönderenine teslim edilir. Bazıları, ancak tümü değil, geri ölçeklendirici istenmeyen posta olarak işaretlenir. Tanım gereği, geri ölçeklendirici yalnızca sahte gönderene teslim edilebilir, özgün gönderene teslim edilmeyebilir.</li></ul> <p> Bu ayar için test modu kullanılamaz.|`X-CustomSpam: Backscatter NDR`|
