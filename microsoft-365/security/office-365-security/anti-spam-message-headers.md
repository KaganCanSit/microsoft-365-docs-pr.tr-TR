---
title: İstenmeyen posta önleme ileti üst bilgileri
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: ITPro
ms.topic: conceptual
ms.localizationpriority: high
search.appverid:
- MET150
ms.assetid: 2e3fcfc5-5604-4b88-ac0a-c5c45c03f1db
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
description: Yöneticiler, EOP (EOP) tarafından iletilere eklenen üst Exchange Online Protection bilgi edinebilirsiniz. Bu üst bilgi alanları ileti ve nasıl işlenmeleri hakkında bilgi sağlar.
ms.custom: seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 8eaf567e4cbceae66a5acd1fa1a45565f15a4804
ms.sourcegitcommit: e09ced3e3628bf2ccb84d205d9699483cbb4b3b0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/09/2021
ms.locfileid: "62990614"
---
# <a name="anti-spam-message-headers-in-microsoft-365"></a>İletide istenmeyen posta önleme ileti Microsoft 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Geçerli olduğu yer:**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [1. plan Office 365 plan 2 için Microsoft Defender](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Tüm Microsoft 365, Exchange Online Protection (EOP) istenmeyen posta, kötü amaçlı yazılım ve diğer tehditlere karşı tüm gelen iletileri tarar. Bu taramaların sonuçları iletilerde aşağıdaki üst bilgi alanlarına eklenir:

- **X-Forefront-Antispam-Report**: İleti ve nasıl işlenmeleri hakkında bilgi içerir.

- **X-Microsoft-Antispam**: Toplu posta ve kimlik avı hakkında ek bilgi içerir.

- **Kimlik doğrulama sonuçları**: SPF, DKIM ve DMARC (e-posta kimlik doğrulaması) sonuçları hakkında bilgi içerir.

Bu makalede, bu üst bilgi alanlarında nelerin kullanılabilir olduğu açıklanmıştır.

Çeşitli e-posta istemcilerinde e-posta iletisi üst bilgilerini görüntüleme hakkında bilgi için bkz. E-posta ileti [üst bilgilerini Outlook](https://support.microsoft.com/office/cd039382-dc6e-4264-ac74-c048563d212c).

> [!TIP]
> İleti üst bilgisi içeriğini kopyalayıp İleti Üst Bilgisi Çözümleyicisi [aracına yapıştırabilirsiniz](https://mha.azurewebsites.net/) . Bu araç, üst bilgileri ayrıştırmanıza ve daha okunabilir bir biçime dönüştürmeye yardımcı olur.

## <a name="x-forefront-antispam-report-message-header-fields"></a>X-Forefront-Antispam-Report ileti üst bilgisi alanları

İleti üst bilgilerini edindikten sonra **X-Forefront-Antispam-Report üst bilgisini** bulun. Bu üst bilgide birden çok alan ve değer çiftleri noktalı virgülle (üç tane;). Örneğin:

`...CTRY:;LANG:hr;SCL:1;SRV:;IPV:NLI;SFV:NSPM;PTR:;CAT:NONE;SFTY:;...`

Ayrı ayrı alanlar ve değerler aşağıdaki tabloda açıklanmıştır.

> [!NOTE]
> **X-Forefront-Antispam-Report üst** bilgisi birçok farklı alan ve değer içerir. Tabloda açık olmayan alanlar tanılama amacıyla Microsoft istenmeyen posta önleme ekibi tarafından özel olarak kullanılır.

****

|Alan|Açıklama|
|---|---|
|`ARC`|Protokolde `ARC` aşağıdaki alanlar vardır: <ul><li>`AAR`: DMARC'dan **Kimlik Doğrulama sonuçları** üst bilgisinde yer alan içeriği kayıtları.</li><li>`AMS`: İletinin şifreleme imzalarını içerir.</li><li>`AS`: İleti üst bilgilerinin şifreleme imzalarını içerir. Bu alan, zincir doğrulamanın sonucunu yok`"cv="`, geçti veya başarısız olarak içeren, , adlı bir **zincir** **doğrulama etiketi** **içerir**.</li></ul>|
|`CAT:`|İletiye uygulanan koruma ilkesi kategorisi: <ul><li>`BULK`: Toplu</li><li>`DIMP`: Etki Alanı Kimliğine Bürünme</li><li>`GIMP`: [Posta kutusu zekası tabanlı kimliğe bürünme](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365)</li><li>`HPHSH` veya `HPHISH` : Yüksek güven amaçlı kimlik avı</li><li>`HSPM`: Yüksek güven istenmeyen posta</li><li>`MALW`: Kötü amaçlı yazılım</li><li>`PHSH`: Kimlik avı</li><li>`SPM`: İstenmeyen posta</li><li>`SPOOF`: Spoofing</li><li>`UIMP`: Kullanıcı Kimliğine Bürünme</li><li>`AMP`: Kötü amaçlı yazılımdan koruma</li><li>`SAP`: Kasa ekleme</li><li>`OSPM`: Giden istenmeyen posta</li></ul> <p> Gelen bir ileti, birden çok koruma formu ve birden çok algılama taramasıyla işaretlenmiş olabilir. İlkelerin farklı öncelikleri vardır ve önce en yüksek önceliğe sahip ilke uygulanır. Daha fazla bilgi için bkz [. Birden çok koruma yöntemi ve algılama taramaları e-postanızı tararsa hangi ilke geçerlidir](how-policies-and-protections-are-combined.md).|
|`CIP:[IP address]`|Bağlantı IP adresi. Bu IP adresini IP İzin Listesi'ne veya IP Engelleme Listesi'ne kullanabilirsiniz. Daha fazla bilgi için bkz [. Bağlantı filtrelemeyi yapılandırma](configure-the-connection-filter-policy.md).|
|`CTRY`|Bağlantı IP adresiyle belirlenen kaynak ülkedir ve bu, gönderen IP adresiyle aynı olabilir.|
|`H:[helostring]`|Bağlantı e-posta sunucusunun HELO veya EHLO dizesi.|
|`IPV:CAL`|Kaynak IP adresi IP İzin Listesi'nin içinde olduğu için ileti istenmeyen posta filtrelemeyi atlandı. Daha fazla bilgi için bkz [. Bağlantı filtrelemeyi yapılandırma](configure-the-connection-filter-policy.md).|
|`IPV:NLI`|IP adresi hiçbir IP itibarı listesinde bulunamadı.|
|`LANG`|İletinin ülke kodunda belirtilen dili (örneğin, Rusça için ru_RU).|
|`PTR:[ReverseDNS]`|Kaynak IP adresinin PTR kaydı (ters DNS araması olarak da bilinir).|
|`SCL`|İletinin istenmeyen posta güven düzeyi (SCL). Daha yüksek bir değer iletinin istenmeyen posta olma olasılığı daha yüksek olduğunu gösterir. Daha fazla bilgi için bkz. [İstenmeyen posta güven düzeyi (SCL)](spam-confidence-levels.md).|
|`SFTY`|İleti kimlik avı olarak tanımlandı ve aşağıdaki değerlerden biri ile de işaretlenir: <ul><li>9.19: Etki alanı kimliğine bürünme. Gönderen etki alanı, korumalı bir etki alanının [kimliğine bürünme girişiminde bulundurdu](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365). Etki güvenlik ipucu kimliğine bürünme özelliği etkinleştirilmişse iletiye eklenir.</li><li>9.20: Kullanıcı kimliğine bürünme. Gönderen kullanıcı, alıcının kuruluşunda bir kullanıcının kimliğine bürünme veya Office 365 için Microsoft [Defender'da](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365) kimlik avı önleme ilkesinde belirtilen korumalı bir kullanıcının kimliğine bürünme girişiminde Office 365. Kullanıcı güvenlik ipucu kimliğine bürünme özelliği etkinleştirilmişse, iletiye eklenir.</li></ul>|
|`SFV:BLK`|Filtreleme atlandı ve ileti, kullanıcının Engellenen Gönderenler listesinde bir adresten gönderildiği için engellendi. <p> Yöneticilerin bir kullanıcının Engellenen Gönderenler listesini nasıl yönetecekleri hakkında daha fazla bilgi için bkz. Posta kutuları üzerinde gereksiz [Exchange Online yapılandırma](configure-junk-email-settings-on-exo-mailboxes.md).|
|`SFV:NSPM`|İstenmeyen posta filtreleme iletiyi istenmeyen posta değil olarak işaretledi ve ileti hedeflenen alıcılara gönderildi.|
|`SFV:SFE`|Filtreleme atlandı ve bir kullanıcının Gönderenler listesinde yer alan bir adresten gönderildiği için iletiye izin Kasa. <p> Yöneticilerin bir kullanıcının Posta Gönderenler listesini nasıl yönetecekleri hakkında daha fazla Kasa için bkz. Posta kutuları üzerinde gereksiz [Exchange Online yapılandırma](configure-junk-email-settings-on-exo-mailboxes.md).|
|`SFV:SKA`|İleti istenmeyen posta filtrelemeyi atlandı ve Gelen Kutusu'na teslim edildi çünkü gönderen, istenmeyen posta önleme ilkesinde izin verilen gönderenler listesinde veya izin verilen etki alanları listesinde yer alıyor. Daha fazla bilgi için bkz [. İstenmeyen posta önleme ilkelerini yapılandırma](configure-your-spam-filter-policies.md).|
|`SFV:SKB`|İleti, istenmeyen posta önleme ilkesinde engellenen gönderenler listesinde yer alan veya engellenen etki alanları listesinde yer alan bir gönderenle eş olduğundan istenmeyen posta olarak işaretlendi. Daha fazla bilgi için bkz [. İstenmeyen posta önleme ilkelerini yapılandırma](configure-your-spam-filter-policies.md).|
|`SFV:SKI`|SFV:SKN'ye benzer şekilde, ileti istenmeyen posta filtrelemeyi başka bir nedenle atlar (örneğin, kiracı içindeki bir şirket içi e-posta).|
|`SFV:SKN`|İleti, istenmeyen posta filtrelemesi tarafından işlenmeden önce istenmeyen posta değil olarak işaretlendi. Örneğin, ileti SCL -1 olarak işaretlenmiş veya **Posta akış kuralıyla istenmeyen posta filtresini** atla olarak işaretlenmiştir.|
|`SFV:SKQ`|İleti karantinadan çıkarıldı ve gönderilmek üzere alıcılara gönderildi.|
|`SFV:SKS`|İleti, istenmeyen posta filtrelemesi tarafından işlenmeden önce istenmeyen posta olarak işaretlenmiştir. Örneğin, ileti bir posta akış kuralı tarafından SCL 5 - 9 arasında olarak işaretlenmiştir.|
|`SFV:SPM`|İleti, istenmeyen posta filtrelemesi ile istenmeyen posta olarak işaretlendi.|
|`SRV:BULK`|İleti, istenmeyen posta filtreleme ve toplu şikayet düzeyi (BCL) eşiği tarafından toplu e-posta olarak tanımlandı. _MarkAsSpamBulkMail_ `On` parametresi (varsayılan olarak açıktır) olduğunda, toplu e-posta iletisi istenmeyen posta (SCL 6) olarak işaretlenir. Daha fazla bilgi için bkz [. İstenmeyen posta önleme ilkelerini yapılandırma](configure-your-spam-filter-policies.md).|
|`X-CustomSpam: [ASFOption]`|İleti, Gelişmiş İstenmeyen Posta Filtresi (ASF) ayarıyla eşdü. Her ASF ayarının X üstbilgisi değerini görmek için bkz. [Gelişmiş İstenmeyen Posta Filtresi (ASF) ayarları](advanced-spam-filtering-asf-options.md).|
|

## <a name="x-microsoft-antispam-message-header-fields"></a>X-Microsoft-Antispam ileti üst bilgisi alanları

Aşağıdaki tabloda, **X-Microsoft-Antispam ileti üst bilgisinde yararlı alanlar** açıklanmıştır. Bu üst bilgide yer alan diğer alanlar tanılama amacıyla Microsoft istenmeyen posta önleme ekibi tarafından özel olarak kullanılır.

****

|Alan|Açıklama|
|---|---|
|`BCL`|İletinin toplu şikayet düzeyi (BCL). Daha yüksek bir BCL, toplu posta iletisinin şikayet oluşturma olasılığı daha yüksek (ve bu nedenle istenmeyen posta olma olasılığı daha yüksek) olduğunu gösterir. Daha fazla bilgi için bkz [. Toplu şikayet düzeyi (BCL)](bulk-complaint-level-values.md).|
|

## <a name="authentication-results-message-header"></a>Kimlik doğrulama sonuçları ileti üst bilgisi

SPF, DKIM ve DMARC için **e-posta** kimlik doğrulaması denetimlerinin sonuçları, gelen iletilerde Kimlik doğrulama sonuçları ileti üst bilgisine kaydedilir (damgalanır).

Aşağıdaki listede, her tür **e-posta** kimlik doğrulaması denetimi için Kimlik Doğrulama Sonuçları üst bilgisinde eklenen metin açıklanmıştır:

- SPF aşağıdaki söz dizimi kullanır:

  ```text
  spf=<pass (IP address)|fail (IP address)|softfail (reason)|neutral|none|temperror|permerror> smtp.mailfrom=<domain>
  ```

  Örneğin:

  ```text
  spf=pass (sender IP is 192.168.0.1) smtp.mailfrom=contoso.com
  spf=fail (sender IP is 127.0.0.1) smtp.mailfrom=contoso.com
  ```

- DKIM aşağıdaki söz dizimi kullanır:

  ```text
  dkim=<pass|fail (reason)|none> header.d=<domain>
  ```

  Örneğin:

  ```text
  dkim=pass (signature was verified) header.d=contoso.com
  dkim=fail (body hash did not verify) header.d=contoso.com
  ```

- VSEÇMARC aşağıdaki söz dizimlerini kullanır:

  ```text
  dmarc=<pass|fail|bestguesspass|none> action=<permerror|temperror|oreject|pct.quarantine|pct.reject> header.from=<domain>
  ```

  Örneğin:

  ```text
  dmarc=pass action=none header.from=contoso.com
  dmarc=bestguesspass action=none header.from=contoso.com
  dmarc=fail action=none header.from=contoso.com
  dmarc=fail action=oreject header.from=contoso.com
  ```

### <a name="authentication-results-message-header-fields"></a>Kimlik doğrulama sonuçları ileti üst bilgisi alanları

Aşağıdaki tabloda, her e-posta kimlik doğrulaması denetimi için alanlar ve olası değerler açık almaktadır.

****

|Alan|Açıklama|
|---|---|
|`action`|DMARC denetimi sonuçlarına dayalı olarak istenmeyen posta filtresi tarafından  alınan eylemi gösterir. Örneğin: <ul><li>**orect veya** **o.reject: Reddetmeyi** geçersiz kılmanın açılımı. Bu durumda Microsoft 365, DMARC TXT kaydı p=reddetme ilkesine sahip bir etki alanında DMARC denetimine başarısız olan bir ileti geldiğinde bu eylemi kullanır. İletiyi silmek veya reddetmek yerine, Microsoft 365 istenmeyen posta olarak işaretler. E-postaların neden Microsoft 365 yapılandırıldı hakkında daha fazla bilgi için bkz. Microsoft 365 [DMARC'da başarısız olan gelen e-postayı işleme](use-dmarc-to-validate-email.md#how-microsoft-365-handles-inbound-email-that-fails-dmarc).</li><li>**pct.karantina**: DMARC'ı geç kullanmayan iletilerin yüzde 100'den az bir yüzdesinin yine de teslim olacağını gösterir. Bu, iletinin DMARC başarısız olduğu ve ilkenin karantinaya alınamadı anlamına gelir, ancak PCT alanı %100 olarak ayarilmemiştir ve sistem belirtilen etki alanının ilkesine göre DMARC eylemlerini uygulamamak üzere rastgele karar verdi.</li><li>**pct.reject**: Yine de DMARC'ı geçemedi iletilerinin yüzde 100'den az bir yüzdesinin teslim olacağını gösterir. Bu, iletinin DMARC başarısız olduğu ve ilkenin reddedecek şekilde ayar olduğu, ancak PCT alanının %100 olarak ayarlanmadlı olduğu ve sistem belirtilen etki alanının ilkesine göre DMARC eyleminin uygulanmayacak şekilde rastgele belirlen ayarlaması anlamına gelir.</li><li>**permerror**: DNS'de yanlış 365 DMARC TXT kaydıyla karşılaşma gibi, DMARC değerlendirme sırasında kalıcı bir hata oluştu. Bu iletiyi yeniden gönderme girişiminin farklı bir sonuçla bit olasılığı yok. Bunun yerine, sorunu çözmek için etki alanının sahibine başvurabilirsiniz.</li><li>**bir hata oluştu**. DMARC değerlendirme sırasında geçici bir hata oluştu. E-postayı düzgün bir şekilde işlemesi için gönderenden daha sonra iletiyi yeniden göndermelerini isteğinizi gönderebilirsiniz.</li></ul>|
|`compauth`|Bileşik kimlik doğrulama sonucu. Kimlik Microsoft 365, iletinin kimliği doğrulanmış olup olmadığını belirlemek üzere SPF, DKIM, DMARC veya iletinin başka herhangi bir bölümü gibi birden çok kimlik doğrulama türü birleştirmek üzere kullanılır. Değerlendirme temeli olarak From: etki alanını kullanır.|
|`dkim`|DKIM denetiminin ileti sonuçlarını açıklar. Olası değerler şunlardır: <ul><li>**geçiş**: DkIM onay kutusunu iletiyle ilgili olarak gösterir.</li><li>**başarısız (neden)**: İletinin başarısız olup başarısız olduğunu DKIM onay kutusunu gösterir. Örneğin, ileti imzalanmamışsa veya imza doğrulanmamışsa.</li><li>**yok**: İletinin imza olmadığını gösterir. Bu, etki alanının bir DKIM kaydı olduğunu veya DKIM kaydının bir sonucu değerlendirme olmadığını, yalnızca bu iletinin imza olmadığını belirtebilirsiniz.</li></ul>|
|`dmarc`|DMARC denetiminin iletiye olan sonuçlarını açıklar. Olası değerler şunlardır: <ul><li>**geçiş**: DMARC denetiminden geçen iletiyi gösterir.</li><li>**başarısız**: İletinin başarısız olduğunu DMARC denetimi gösterir.</li><li>**bestguesspass**: Etki alanı için DMARC TXT kaydının olmadığını belirtir, ama varsa, iletinin DMARC denetimi geçmiş olabilir.</li><li>**yok**: DNS'de gönderen etki alanı için DMARC TXT kaydının olmadığını gösterir.|
|`header.d`|DKIM imzalarında tanımlanan etki alanı (varsa). Bu, ortak anahtar için sorgulanan etki alanıdır.|
|`header.from`|E-posta iletisi üst `5322.From` bilgisinde adresin etki alanı (Gönderen adresi veya P2 gönderen olarak da bilinir). Alıcı, e-posta istemcilerinin Gönderen adresini görüyor.|
|`reason`|Bileşik kimlik doğrulamasının geçen veya başarısız olan nedeni. Değer 3 basamaklı bir koddur. Örneğin: <ul><li>**000**: İleti açık kimlik doğrulaması başarısız oldu (`compauth=fail`). Örneğin, ileti bir DMARC'ı karantina veya reddetme eylemiyle başarısız oldu.</li><li>**001**: İleti örtülü kimlik doğrulaması () başarısız oldu`compauth=fail`. Bu, gönderen etki alanının yayımlanmış e-posta kimlik doğrulama kayıtları olmadığını veya varsa zayıf bir hata ilkesi (SPF yumuşak başarısız veya nötr, DMARC `p=none`ilkesi) olduğu anlamına gelir.</li><li>**002**: Kuruluş, gönderen/etki alanı çifti için, kimliği doğru olmayan e-posta göndermenin açıkça yasak olduğu bir ilkesine sahip. Bu ayar yönetici tarafından el ile ayarlanır.</li><li>**010**: İleti, DMARC'ye reddetme veya karantinaya alınmış bir eylemle başarısız oldu ve gönderen etki alanı da organizasyonlu kabul edilen etki alanlarından biri (kendi kendine yapılan veya kendi kendine yapılan veya kuruluş içi bir hesabın parçasıdır).</li><li>**1xx veya** **7xx**: İleti kimlik doğrulamasını () geçti`compauth=pass`. Son iki rakam, posta kodu tarafından kullanılan Microsoft 365.</li><li>**2xx**: İleti, örtülü kimlik doğrulamasına () yumuşak geçti`compauth=softpass`. Son iki rakam, posta kodu tarafından kullanılan Microsoft 365.</li><li>**3xx**: İleti, bileşik kimlik doğrulaması () için denetlendi`compauth=none`.</li><li>**4xx** veya **9xx**: İleti bileşik kimlik doğrulamasını () atlar`compauth=none`. Son iki rakam, posta kodu tarafından kullanılan Microsoft 365.</li><li>**6xx**: İleti, örtülü e-posta kimlik doğrulaması başarısız oldu ve gönderen etki alanı da organizasyonlu kabul edilen etki alanlarından biri (kendi kendine veya kuruluş kimlik doğrulamasının bir bölümüdür).</li></ul>|
|`smtp.mailfrom`|Adresin etki alanı `5321.MailFrom` (POSTA GÖNDEREN adresi, P1 gönderen veya zarf gönderen olarak da bilinir). Bu, teslim edililmeyen raporlar (NDR'ler veya geri dönen iletiler olarak da bilinir) için kullanılan e-posta adresidir.|
|`spf`|İletiyle ilgili SPF denetimi sonuçlarını açıklar. Olası değerler şunlardır: <ul><li>`pass (IP address)`: İletiyi içeren SPF denetimi, gönderenin IP adresini içerir. İstemci, gönderenin etki alanı adına e-posta gönderme veya geçiş yetkisine sahip.</li><li>`fail (IP address)`: İleti için SPF denetimi başarısız oldu ve gönderenin IP adresini içerir. Buna bazen zor başarısız _denir_.</li><li>`softfail (reason)`: SPF kaydı ana bilgisayarı göndermesine izin verilmedi ancak geçişte olduğunu belirledi.</li><li>`neutral`: SPF kaydı, IP adresinin gönderme yetkisi olup olmadığını açıkça onaylamaz.</li><li>`none`: Etki alanının bir SPF kaydı yok veya SPF kaydı bir sonucu değerlendirmez.</li><li>`temperror`: Geçici bir hata oluştu. Örneğin, bir DNS hatası. Aynı denetim daha sonra başarılı olabilir.</li><li>`permerror`: Kalıcı bir hata oluştu. Örneğin, etki alanının kötü biçimlendirilmiş bir SPF kaydı var.</li></ul>|
|
