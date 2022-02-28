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
description: Yöneticiler, EOP'de (EOP) istenmeyen posta önleme ilkelerde bulunan Gelişmiş İstenmeyen Posta Filtresi (ASF) Exchange Online Protection bilgi edinebilirsiniz.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 71eeaec20ab64b5faa535ddb2f9e688b9b9192d9
ms.sourcegitcommit: bf3965b46487f6f8cf900dd9a3af8b213a405989
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2021
ms.locfileid: "62989978"
---
# <a name="advanced-spam-filter-asf-settings-in-eop"></a>EOP'de Gelişmiş İstenmeyen Posta Filtresi (ASF) ayarları

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Geçerli olduğu yer:**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [1. plan Office 365 plan 2 için Microsoft Defender](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Tüm Microsoft 365, EOP'de istenmeyen posta önleme ilkelerine yönelik Gelişmiş İstenmeyen Posta Filtresi (ASF) ayarları yöneticilerin belirli ileti özelliklerine göre iletileri istenmeyen posta olarak işaretlemesine olanak sağlar. ASF özellikle bu özellikleri hedefler çünkü bunlar yaygın olarak istenmeyen posta içinde bulunurlar. Özele bağlı olarak ASF algılamaları iletiyi İstenmeyen Posta **veya Yüksek** güveni olmayan **istenmeyen posta olarak işaretlemektedir**.

> [!NOTE]
> ASF ayarlarından birini veya daha fazlasını etkinleştirmek istenmeyen posta filtrelemeye saldırgan bir yaklaşımdır. ASF tarafından filtrelenmiş iletileri hatalı pozitif sonuç olarak bildiresiniz. ASF tarafından filtrelenmiş iletileri tanımlayabilirsiniz:
>
> - İstenmeyen postadan düzenli karantina bildirimleri ve yüksek güven içeren istenmeyen posta filtresi kararlarını.
> - Karantinada filtrelenmiş iletilerin varlığı.
> - İletilere `X-CustomSpam:` eklenen belirli X üstbilgisi alanları bu makalede açıklandığı gibi.

Aşağıdaki bölümlerde, Microsoft 365 Defender portalında ve Exchange Online PowerShell'de veya tek başına EOP PowerShell'de ([New-HostedContentFilterPolicy](/powershell/module/exchange/new-hostedcontentfilterpolicy) ve [Set-HostedContentFilterPolicy](/powershell/module/exchange/set-hostedcontentfilterpolicy)) bulunan ASF ayarları ve seçenekleri açıklanmaktadır. Daha fazla bilgi için bkz. [EOP'de istenmeyen posta önleme ilkelerini yapılandırma](configure-your-spam-filter-policies.md).

## <a name="enable-disable-or-test-asf-settings"></a>ASF ayarlarını etkinleştirme, devre dışı bırakma veya test edin

Her ASF ayarı için, istenmeyen posta önleme ilkelerde aşağıdaki seçenekler kullanılabilir:

- **On**: ASF ilgili X üstbilgi alanını iletiye ekler ve iletiyi İstenmeyen **Posta (** İstenmeyen posta puanı ayarlarını artırmak için SCL 5 veya [6) veya](#increase-spam-score-settings) Yüksek güven içeren istenmeyen **posta (** İstenmeyen posta ayarları olarak işaretle için SCL 9) olarak [işaretler.](#mark-as-spam-settings)
- **Kapalı**: ASF ayarı devre dışı bırakılır. Bu, varsayılan değerdir ve bunu değiştirmenizi önerilmez.
- **Test**: ASF, iletiye karşılık gelen X üstbilgi alanını ekler. İletiye ne olur? Sınama **modu (***TestModeAction) değerine* göre belirlenir:
  - **Yok**: İleti teslimi ASF algılamadan etkilenmez. İleti, EOP'de diğer filtre türlerine ve kurallara tabi olabilir.
  - **Varsayılan X üstbilgisi metnini ekleyin (*AddXHeader*)**: X `X-CustomSpam: This message was filtered by the custom spam filter option` üstbilgisi değeri iletiye eklenir. İletinin teslimi etkilerken Gelen Kutusu kurallarında veya posta akışı kurallarında (aktarım kuralları olarak da bilinir) bu değeri kullanabilirsiniz.
  - **Gizli ileti gönderme (*BccMessage*)**: Belirtilen e-posta adresleri (PowerShell'de *TestModeBccToRecipients* parametre değeri) iletinin Gizli alanına eklenir ve ileti diğer Gizli alıcılara teslim edilir. Microsoft 365 Defender portalında, birden çok e-posta adresini noktalı virgülle (üç ;). PowerShell'de, birden çok e-posta adresini virgülle birbirinden ayırabilirsiniz.

  **Notlar**:

  - Aşağıdaki ASF ayarları için sınama modu kullanılamaz:
    - **Koşullu Gönderen Kimliği filtreleme: zor başarısız (***MarkAsSpamFromAddressAuthFail*)
    - **NDR geri çıktısı**(*MarkAsSpamNdrBackscatter*)
    - **SPF kaydı: sabit başarısız** (*MarkAsSpamSpfRecordFail*)
  - Test olarak ayarlanmış tüm ASF *ayarlarına* aynı sınama modu **eylemi uygulanır**. Farklı ASF ayarları için farklı test modu eylemleri yapılandıramazsınız.

## <a name="increase-spam-score-settings"></a>İstenmeyen posta puanı ayarlarını artırma

Aşağıdaki **İstenmeyen** posta puanı ARTıR ASF ayarları, algılanan iletilerin istenmeyen posta güven düzeyini (SCL) 5 veya 6 olarak ayarlar. Bu, **İstenmeyen** posta filtresi kararını ve istenmeyen posta önleme ilkelerde ilgili eylemi ifade ediyor.

<br>

****

|İstenmeyen posta önleme ilkesi ayarı|Açıklama|X üstbilgisi eklendi|
|---|---|---|
|**Uzak web sitelerine resim bağlantıları** <p> *IncreaseScoreWithImageLinks*|Uzak sitelere `<Img>` (örneğin, http kullanarak) HTML etiketi bağlantıları içeren iletiler istenmeyen posta olarak işaretlenir.|`X-CustomSpam: Image links to remote sites`|
|**URL'de sayısal IP adresi** <p> *IncreaseScoreWithNumericIps*|Sayısal tabanlı URL'ler içeren iletiler (genellikle IP adresleri) istenmeyen posta olarak işaretlenir.|`X-CustomSpam: Numeric IP in URL`|
|**URL başka bir bağlantı noktasına yönlendirme** <p> *IncreaseScoreWithRedirectToOtherPort*|80 (HTTP), 8080 (alternatif HTTP) veya 443 (HTTPS) dışında TCP bağlantı noktalarına yönlendiren köprüler içeren ileti istenmeyen posta olarak işaretlenir.|`X-CustomSpam: URL redirect to other port`|
|**.biz veya .info web sitelerinin bağlantıları** <p> *IncreaseScoreWithBizOrInfoUrls*|İletinin gövdesinde `.biz` `.info` yer alan veya bağlantı bulunan iletiler istenmeyen posta olarak işaretlenir.|`X-CustomSpam: URL to .biz or .info websites`|
|

## <a name="mark-as-spam-settings"></a>İstenmeyen posta ayarları olarak işaretleme

Aşağıdaki **İstenmeyen** posta olarak işaretle ASF ayarları, algılanan iletilerin SCL'sini 9 olarak ayarlar. Bu, Yüksek  güven güveni olan istenmeyen posta filtresi kararını ve istenmeyen posta önleme ilkelerde ilgili eylemi ifade ediyor.

<br>

****

|İstenmeyen posta önleme ilkesi ayarı|Açıklama|X üstbilgisi eklendi|
|---|---|---|
|**Boş iletiler** <p> *MarkAsSpamEmptyMessages*|Konusu olmayan, ileti gövdesinde hiçbir içerik olmayan ve hiçbir eki olmayan iletiler yüksek güveni olmayan istenmeyen posta olarak işaretlenir.|`X-CustomSpam: Empty Message`|
|**HTML'de katıştırılmış etiketler** <p> *MarkAsSpamEmbedTagsInHtml*|HTML etiketleri içeren ileti `<embed>` yüksek güven istenmeyen posta olarak işaretlenir. <p> Bu etiket, HTML belgesine farklı türde belgelerin (örneğin, sesler, videolar veya resimler) katıştırmalarını sağlar.|`X-CustomSpam: Embed tag in html`|
|**HTML'de JavaScript veya VBScript** <p> *MarkAsSpamJavaScriptInHtml*|HTML'de JavaScript veya Visual Basic Script Edition kullanan iletiler yüksek güven istenmeyen posta olarak işaretlenir. <p> Bu betik dilleri, e-posta iletilerinde belirli eylemlerin otomatik olarak gerçekleşmesine neden olmak için kullanılır.|`X-CustomSpam: Javascript or VBscript tags in HTML`|
|**HTML'de form etiketleri** <p> *MarkAsSpamFormTagsInHtml*|HTML etiketleri içeren iletiler `<form>` yüksek güven istenmeyen posta olarak işaretlenir. <p> Bu etiket, web sitesi formları oluşturmak için kullanılır. E-posta tanıtımları genellikle alıcıdan bilgi talep etmek için bu etiketi içerir.|`X-CustomSpam: Form tag in html`|
|**HTML'de çerçeve veya iframe etiketleri** <p> *MarkAsSpamFramesInHtml*|HTML etiketleri içeren `<frame>` iletiler `<iframe>` yüksek güven istenmeyen posta olarak işaretlenir. <p> Bu etiketler, e-posta iletisinde sayfayı metin veya grafikleri görüntülerken biçimlendirmek için kullanılır.|`X-CustomSpam: IFRAME or FRAME in HTML`|
|**HTML'de Web hataları** <p> *MarkAsSpamWebBugsInHtml*|*Web hatası* (*web* işareti olarak da bilinir), e-posta iletisinde iletinin alıcı tarafından okundu olup olmadığını belirlemek için kullanılan bir grafik öğesidir (çoğu zaman bir piksel piksel küçüktür). <p> Web hataları içeren iletiler yüksek güven istenmeyen posta olarak işaretlenir. <p> Yasal bültenlerde web hataları kullanabilir, ancak pek çok kişi bunu bir gizlilik göz önünde bulundursa da. |`X-CustomSpam: Web bug`|
|**HTML'de nesne etiketleri** <p> *MarkAsSpamObjectTagsInHtml*|HTML etiketleri içeren iletiler `<object>` yüksek güven istenmeyen posta olarak işaretlenir. <p> Bu etiket, eklentilerin veya uygulamaların HTML penceresinde çalışmasına olanak sağlar.|`X-CustomSpam: Object tag in html`|
|**Hassas sözcükler** <p> *MarkAsSpamSensitiveWordList*|Microsoft, olası rahatsız edici iletilerle ilişkilendirilmiş, ancak düzenlenilmeyen dinamik bir sözcük listesi sağlar. <p> Konu veya ileti gövdesinde hassas sözcük listesinden sözcükler içeren iletiler yüksek güven istenmeyen posta olarak işaretlenir.|`X-CustomSpam: Sensitive word in subject/body`|
|**SPF kaydı: zor başarısız** <p> *MarkAsSpamSpfRecordFail*|Kaynak e-posta etki alanı için DNS'deki SPF Sender Policy Framework (SPF) kaydında belirtilmemiş bir IP adresinden gönderilen iletiler yüksek güven istenmeyen posta olarak işaretlenir. <p> Bu ayar için sınama modu kullanılamaz.|`X-CustomSpam: SPF Record Fail`|
|

Aşağıdaki **İstenmeyen** posta ASF olarak işaretle ayarları, algılanan iletilerin SCL'sini 6 olarak ayarlar. Bu, **İstenmeyen** posta filtresi karar ve istenmeyen posta önleme ilkelerde ilgili eyleme karşılık gelir.

<br>

****

|İstenmeyen posta önleme ilkesi ayarı|Açıklama|X üstbilgisi eklendi|
|---|---|---|
|**Gönderen Kimliği filtrelemesi zor başarısız** <p> *MarkAsSpamFromAddressAuthFail*|Koşullu Gönderen Kimliği denetimine geçmeyen iletiler istenmeyen posta olarak işaretlenir. <p> Bu ayar, sahte gönderenler içeren ileti üst bilgilerine karşı korunmanıza yardımcı olmak için bir SPF denetimi ile Gönderen Kimliği denetimi birleştirir. <p> Bu ayar için sınama modu kullanılamaz.|`X-CustomSpam: SPF From Record Fail`|
|**Geri geri yayan** <p> *MarkAsSpamNdrBackscatter*|*Geri çıktı, e-posta* iletilerine sahte gönderenler tarafından neden olan, teslim edilemeyen raporlar (NDR'ler veya geri dönen iletiler olarak da bilinir) işe yaramaz. Daha fazla bilgi için bkz [. Geri gelen iletiler ve EOP](backscatter-messages-and-eop.md). <p> Bu ayarı aşağıdaki ortamlarda yapılandırmaya gerek yok, çünkü geçerli NDR'ler teslim edilir ve geri ifade istenmeyen posta olarak işaretlenir: <ul><li>Microsoft 365 posta kutusu olan Exchange Online olabilir.</li><li>Giden e-postayı EOP aracılığıyla *yönlendiren şirket içi* e-posta kuruluşları.</li></ul> <p> Gelen e-postayı şirket içi posta kutularına koruyan tek başına EOP ortamlarında, bu ayarı açma veya kapatmada aşağıdaki sonuç yer alır: <ul><li> **Açık**: Geçerli NDR'ler teslim edilir ve geri ifade istenmeyen posta olarak işaretlenir.</li><li>**Kapalı**: Geçerli NDR'ler ve geri çıktılar normal istenmeyen posta filtrelemesi üzerinden gider. Geçerli NDR'lerin çoğu özgün ileti gönderene teslim edilir. Geri geri ifadelerin hepsi değil, bazıları istenmeyen posta olarak işaretlenir. Tanım olarak, geri çıktı yalnızca orijinal gönderene değil, kimliği doğru olan gönderene teslim edilir.</li></ul> <p> Bu ayar için sınama modu kullanılamaz.|`X-CustomSpam: Backscatter NDR`|
|
