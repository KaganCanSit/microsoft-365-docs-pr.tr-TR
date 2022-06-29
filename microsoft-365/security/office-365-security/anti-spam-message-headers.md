---
title: İstenmeyen posta önleme iletisi üst bilgileri
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
description: Yöneticiler, Exchange Online Protection (EOP) tarafından iletilere eklenen üst bilgi alanları hakkında bilgi edinebilir. Bu üst bilgi alanları, ileti ve nasıl işlendiği hakkında bilgi sağlar.
ms.custom: seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 592a583b572c134dd4ecd33dd18f392f6e9b36ce
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/29/2022
ms.locfileid: "66493075"
---
# <a name="anti-spam-message-headers-in-microsoft-365"></a>Microsoft 365'te istenmeyen postadan koruma iletisi üst bilgileri

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Uygulandığı öğe**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Office 365 için Microsoft Defender plan 1 ve plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Tüm Microsoft 365 kuruluşlarında, Exchange Online Protection (EOP) tüm gelen iletileri istenmeyen posta, kötü amaçlı yazılım ve diğer tehditler için tarar. Bu taramaların sonuçları iletilerde aşağıdaki üst bilgi alanlarına eklenir:

- **X-Forefront-Antispam-Report**: İleti ve nasıl işlendiği hakkında bilgi içerir.

- **X-Microsoft-Antispam**: Toplu posta ve kimlik avı hakkında ek bilgiler içerir.

- **Kimlik doğrulama sonuçları**: SPF, DKIM ve DMARC (e-posta kimlik doğrulaması) sonuçları hakkında bilgi içerir.

Bu makalede, bu üst bilgi alanlarında kullanılabilenler açıklanmaktadır.

Çeşitli e-posta istemcilerinde e-posta iletisi üst bilgisini görüntüleme hakkında bilgi için bkz. [Outlook'ta internet iletisi üst bilgilerini görüntüleme](https://support.microsoft.com/office/cd039382-dc6e-4264-ac74-c048563d212c).

> [!TIP]
> İleti üst bilgisinin içeriğini kopyalayıp [İleti Üst Bilgisi Çözümleyicisi](https://mha.azurewebsites.net/) aracına yapıştırabilirsiniz. Bu araç üst bilgileri ayrıştırma ve daha okunabilir bir biçime yerleştirmeye yardımcı olur.

## <a name="x-forefront-antispam-report-message-header-fields"></a>X-Forefront-Antispam-Report ileti üst bilgisi alanları

İleti üst bilgisi bilgilerini aldıktan sonra **X-Forefront-Antispam-Report** üst bilgisini bulun. Bu üst bilgide noktalı virgülle (;)) ayrılmış birden çok alan ve değer çifti olacaktır. Örneğin:

`...CTRY:;LANG:hr;SCL:1;SRV:;IPV:NLI;SFV:NSPM;PTR:;CAT:NONE;SFTY:;...`

Tek tek alanlar ve değerler aşağıdaki tabloda açıklanmıştır.

> [!NOTE]
> **X-Forefront-Antispam-Report** üst bilgisi birçok farklı alan ve değer içerir. Tabloda açıklanmayan alanlar, tanılama amacıyla yalnızca Microsoft istenmeyen posta önleme ekibi tarafından kullanılır.

|Alan|Açıklama|
|---|---|
|`ARC`|Protokol `ARC` aşağıdaki alanlara sahiptir: <ul><li>`AAR`: DMARC'den **Authentication-results** üst bilgisinin içeriğini kaydeder.</li><li>`AMS`: İletinin şifreleme imzalarını içerir.</li><li>`AS`: İleti üst bilgilerinin şifreleme imzalarını içerir. Bu alan, zincir doğrulamasının **sonucunu yok**, **geçti** veya **başarısız** olarak içeren adlı `"cv="`bir zincir doğrulaması etiketi içerir.</li></ul>|
|`CAT:`|İletiye uygulanan koruma ilkesi kategorisi: <ul><li>`BULK`: Toplu</li><li>`DIMP`: Etki Alanı Kimliğe Bürünme</li><li>`GIMP`: [Posta kutusu zekası tabanlı kimliğe bürünme](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365)</li><li>`HPHSH` veya `HPHISH`: Yüksek güvenilirlikli kimlik avı</li><li>`HSPM`: Yüksek güvenilirlikli istenmeyen posta</li><li>`MALW`: Kötü amaçlı yazılım</li><li>`PHSH`: Kimlik avı</li><li>`SPM`: İstenmeyen posta</li><li>`SPOOF`: Sahtekarlık</li><li>`UIMP`: Kullanıcı Kimliğe Bürünme</li><li>`AMP`: Kötü amaçlı yazılımdan koruma</li><li>`SAP`: Güvenli ekler</li><li>`OSPM`: Giden istenmeyen posta</li></ul> <p> Bir gelen ileti, birden çok koruma biçimi ve birden çok algılama taraması ile işaretlenebilir. İlkelerin farklı öncelikleri vardır ve önce en yüksek önceliğe sahip ilke uygulanır. Daha fazla bilgi için bkz [. E-postanızda birden çok koruma yöntemi ve algılama taraması çalıştırıldığında hangi ilke geçerli](how-policies-and-protections-are-combined.md) olur?|
|`CIP:[IP address]`|Bağlanan IP adresi. Bu IP adresini IP İzin Ver Listesi'nde veya IP Engelleme Listesi'nde kullanabilirsiniz. Daha fazla bilgi için bkz. [Bağlantı filtrelemeyi yapılandırma](configure-the-connection-filter-policy.md).|
|`CTRY`|Kaynak ülke, bağlanan IP adresi tarafından belirlenen ve kaynak gönderen IP adresiyle aynı olmayabilir.|
|`H:[helostring]`|Bağlanan e-posta sunucusunun HELO veya EHLO dizesi.|
|`IPV:CAL`|Kaynak IP adresi IP İzin Verme Listesi'nde olduğundan ileti istenmeyen posta filtrelemeyi atladı. Daha fazla bilgi için bkz. [Bağlantı filtrelemeyi yapılandırma](configure-the-connection-filter-policy.md).|
|`IPV:NLI`|IP adresi herhangi bir IP saygınlığı listesinde bulunamadı.|
|`LANG`|Ülke kodu tarafından belirtilen iletinin yazıldığı dil (örneğin, Rusça için ru_RU).|
|`PTR:[ReverseDNS]`|Kaynak IP adresinin PTR kaydı (ters DNS araması olarak da bilinir).|
|`SCL`|İletinin istenmeyen posta güvenilirlik düzeyi (SCL). Daha yüksek bir değer, iletinin istenmeyen posta olma olasılığının daha yüksek olduğunu gösterir. Daha fazla bilgi için bkz. [İstenmeyen posta güvenilirlik düzeyi (SCL)](spam-confidence-levels.md).|
|`SFTY`|İleti kimlik avı olarak tanımlandı ve aşağıdaki değerlerden biriyle işaretlenecek: <ul><li>9.19: Etki alanı kimliğe bürünme. Gönderen etki alanı [korumalı bir etki alanının kimliğine bürünmeye](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365) çalışır. Etki alanı kimliğe bürünme için güvenlik ipucu iletiye eklenir (etkinse).</li><li>9.20: Kullanıcı kimliğine bürünme. Gönderen kullanıcı, alıcının kuruluşundaki bir kullanıcının veya [Office 365 için Microsoft Defender'daki kimlik avı önleme ilkesinde belirtilen korumalı bir kullanıcının](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365) kimliğine bürünmeye çalışır. Kullanıcı kimliğe bürünme için güvenlik ipucu iletiye eklenir (etkinse).</li><li>9.25: İlk temas emniyet ucu. Bu değer şüpheli veya kimlik avı iletisinin göstergesi _olabilir_ . Daha fazla bilgi için bkz. [İlk iletişim güvenliği ipucu](set-up-anti-phishing-policies.md#first-contact-safety-tip).</li></ul>|
|`SFV:BLK`|Filtreleme atlandı ve kullanıcının Engellenen Gönderenler listesindeki bir adresten gönderildiği için ileti engellendi. <p> Yöneticilerin kullanıcının Engellenen Gönderenler listesini nasıl yönetebileceği hakkında daha fazla bilgi için bkz. [Exchange Online posta kutularında gereksiz e-posta ayarlarını yapılandırma](configure-junk-email-settings-on-exo-mailboxes.md).|
|`SFV:NSPM`|İstenmeyen posta filtrelemesi iletiyi istenmeyen posta değil olarak işaretledi ve ileti hedeflenen alıcılara gönderildi.|
|`SFV:SFE`|Filtreleme atlandı ve kullanıcının Güvenilir Gönderenler listesindeki bir adresten gönderildiği için iletiye izin verildi. <p> Yöneticilerin kullanıcının Güvenilir Gönderenler listesini nasıl yönetebileceği hakkında daha fazla bilgi için bkz. [Exchange Online posta kutularında gereksiz e-posta ayarlarını yapılandırma](configure-junk-email-settings-on-exo-mailboxes.md).|
|`SFV:SKA`|İleti istenmeyen posta filtrelemeyi atladı ve gönderen bir istenmeyen posta önleme ilkesinde izin verilen gönderenler listesinde veya izin verilen etki alanları listesinde olduğundan Gelen Kutusu'na teslim edildi. Daha fazla bilgi için bkz. [İstenmeyen posta önleme ilkelerini yapılandırma](configure-your-spam-filter-policies.md).|
|`SFV:SKB`|İleti, istenmeyen posta önleme ilkesindeki engellenen gönderenler listesindeki veya engellenen etki alanları listesindeki bir gönderenle eşleştiğinden istenmeyen posta olarak işaretlendi. Daha fazla bilgi için bkz. [İstenmeyen posta önleme ilkelerini yapılandırma](configure-your-spam-filter-policies.md).|
|`SFV:SKI`|SFV:SKN'ye benzer şekilde, ileti istenmeyen posta filtrelemeyi başka bir nedenle atladı (örneğin, kiracı içindeki kuruluş içi e-posta).|
|`SFV:SKN`|İleti, istenmeyen posta filtrelemesi tarafından işlenmeden önce istenmeyen posta değil olarak işaretlendi. Örneğin, ileti bir posta akışı kuralıyla SCL -1 veya **İstenmeyen posta filtrelemesini atla** olarak işaretlendi.|
|`SFV:SKQ`|İleti karantinadan çıkarıldı ve hedeflenen alıcılara gönderildi.|
|`SFV:SKS`|İleti, istenmeyen posta filtrelemesi tarafından işlenmeden önce istenmeyen posta olarak işaretlendi. Örneğin, ileti bir posta akışı kuralı tarafından SCL 5 ile 9 olarak işaretlendi.|
|`SFV:SPM`|İleti, istenmeyen posta filtrelemesi tarafından istenmeyen posta olarak işaretlendi.|
|`SRV:BULK`|İleti, istenmeyen posta filtreleme ve toplu şikayet düzeyi (BCL) eşiği tarafından toplu e-posta olarak tanımlandı. _MarkAsSpamBulkMail_ parametresi (`On`varsayılan olarak açıktır) olduğunda, toplu e-posta iletisi istenmeyen posta (SCL 6) olarak işaretlenir. Daha fazla bilgi için bkz. [İstenmeyen posta önleme ilkelerini yapılandırma](configure-your-spam-filter-policies.md).|
|`X-CustomSpam: [ASFOption]`|İleti, Gelişmiş İstenmeyen Posta Filtresi (ASF) ayarıyla eşleşmiştir. Her ASF ayarının X üst bilgisi değerini görmek için bkz [. Gelişmiş İstenmeyen Posta Filtresi (ASF) ayarları](advanced-spam-filtering-asf-options.md).|

## <a name="x-microsoft-antispam-message-header-fields"></a>X-Microsoft-Antispam ileti üst bilgisi alanları

Aşağıdaki tabloda **, X-Microsoft-Antispam** ileti üst bilgisindeki yararlı alanlar açıklanmaktadır. Bu üst bilgideki diğer alanlar yalnızca Microsoft istenmeyen posta önleme ekibi tarafından tanılama amacıyla kullanılır.

|Alan|Açıklama|
|---|---|
|`BCL`|İletinin toplu şikayet düzeyi (BCL). Daha yüksek bir BCL, toplu posta iletisinin şikayet oluşturma olasılığının daha yüksek olduğunu gösterir (ve bu nedenle istenmeyen posta olma olasılığı daha yüksektir). Daha fazla bilgi için bkz [. Toplu şikayet düzeyi (BCL)](bulk-complaint-level-values.md).|

## <a name="authentication-results-message-header"></a>Kimlik doğrulama sonuçları ileti üst bilgisi

SPF, DKIM ve DMARC için e-posta kimlik doğrulaması denetimlerinin sonuçları, gelen iletilerde **Kimlik doğrulama sonuçları** ileti üst bilgisine kaydedilir (damgalı).

Aşağıdaki listede, her **e-posta kimlik doğrulaması denetimi türü için Authentication-Results** üst bilgisine eklenen metin açıklanmaktadır:

- SPF aşağıdaki söz dizimini kullanır:

  ```text
  spf=<pass (IP address)|fail (IP address)|softfail (reason)|neutral|none|temperror|permerror> smtp.mailfrom=<domain>
  ```

  Örneğin:

  ```text
  spf=pass (sender IP is 192.168.0.1) smtp.mailfrom=contoso.com
  spf=fail (sender IP is 127.0.0.1) smtp.mailfrom=contoso.com
  ```

- DKIM aşağıdaki söz dizimini kullanır:

  ```text
  dkim=<pass|fail (reason)|none> header.d=<domain>
  ```

  Örneğin:

  ```text
  dkim=pass (signature was verified) header.d=contoso.com
  dkim=fail (body hash did not verify) header.d=contoso.com
  ```

- DMARC aşağıdaki söz dizimini kullanır:

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

Aşağıdaki tabloda, her e-posta kimlik doğrulaması denetimi için alanlar ve olası değerler açıklanmaktadır.

|Alan|Açıklama|
|---|---|
|`action`|DMARC denetiminin sonuçlarına göre istenmeyen posta filtresi tarafından gerçekleştirilen eylemi gösterir. Örneğin: <ul><li>**oreject** veya **o.reject**: Geçersiz kılma reddi anlamına gelir. Bu durumda Microsoft 365, DMARC TXT kaydı p=reject ilkesine sahip olan bir etki alanından DMARC denetiminde başarısız olan bir ileti aldığında bu eylemi kullanır. Microsoft 365 iletiyi silmek veya reddetmek yerine istenmeyen posta olarak işaretler. Microsoft 365'in neden bu şekilde yapılandırıldığı hakkında daha fazla bilgi için bkz. [Microsoft 365, DMARC'de başarısız olan gelen e-postaları nasıl işler](use-dmarc-to-validate-email.md#how-microsoft-365-handles-inbound-email-that-fails-dmarc)?</li><li>**pct.quarantine**: DMARC'den geçmeyen iletilerin %100'den azının yine de teslim edileceğini gösterir. Bu, iletinin DMARC'de başarısız olduğu ve ilkenin karantinaya alınacağı, ancak pct alanının %100 olarak ayarlanmadığı ve sistemin belirtilen etki alanının ilkesine göre DMARC eylemini uygulamadığı rastgele belirlendiği anlamına gelir.</li><li>**pct.reject**: DMARC'den geçmeyen iletilerin %100'den azının yine de teslim edileceğini gösterir. Bu, iletinin DMARC'de başarısız olduğu ve ilkenin reddedilmek üzere ayarlandığı, ancak pct alanının %100 olarak ayarlanmadığı ve sistemin belirtilen etki alanının ilkesine göre DMARC eylemini uygulamamaya rastgele belirlendiği anlamına gelir.</li><li>**permerror**: DNS'de yanlış biçimlendirilmiş bir DMARC TXT kaydıyla karşılaşma gibi DMARC değerlendirmesi sırasında kalıcı bir hata oluştu. Bu iletiyi yeniden gönderme girişiminin farklı bir sonuçla bitmesi olası değildir. Bunun yerine, sorunu çözmek için etki alanının sahibine başvurmanız gerekebilir.</li><li>**temperror**: DMARC değerlendirmesi sırasında geçici bir hata oluştu. E-postayı düzgün bir şekilde işlemek için gönderenden iletiyi daha sonra yeniden göndermesini isteyebilirsiniz.</li></ul>|
|`compauth`|Bileşik kimlik doğrulama sonucu. Microsoft 365 tarafından SPF, DKIM, DMARC veya iletinin başka bir bölümü gibi birden çok kimlik doğrulaması türünü birleştirerek iletinin kimliğinin doğrulanıp doğrulanmadığını belirlemek için kullanılır. Değerlendirmenin temeli olarak Kimden: etki alanını kullanır.|
|`dkim`|İleti için DKIM denetiminin sonuçlarını açıklar. Olası değerler şunlardır: <ul><li>**pass**: Geçirilen ileti için DKIM denetimini gösterir.</li><li>**fail (reason)**: İleti için DKIM denetiminin başarısız olduğunu ve nedenini gösterir. Örneğin, ileti imzalanmamışsa veya imza doğrulanmamışsa.</li><li>**none**: İletinin imzalanmadığını gösterir. Bu, etki alanının DKIM kaydı olduğunu veya DKIM kaydının bir sonuç olarak değerlendirilmediğini, yalnızca bu iletinin imzalanmadığını gösterebilir veya göstermeyebilir.</li></ul>|
|`dmarc`|İleti için DMARC denetiminin sonuçlarını açıklar. Olası değerler şunlardır: <ul><li>**pass**: Geçirilen ileti için DMARC denetimini gösterir.</li><li>**fail**: İleti için DMARC denetiminin başarısız olduğunu gösterir.</li><li>**bestguesspass**: Etki alanı için DMARC TXT kaydı olmadığını gösterir, ancak varsa, ileti için DMARC denetimi geçirilirdi.</li><li>**none**: DNS'de gönderen etki alanı için DMARC TXT kaydı olmadığını gösterir.|
|`header.d`|Varsa DKIM imzasında tanımlanan etki alanı. Bu, ortak anahtar için sorgulanan etki alanıdır.|
|`header.from`|E-posta iletisi üst bilgisindeki adresin `5322.From` etki alanı (Kimden adresi veya P2 göndereni olarak da bilinir). Alıcı e-posta istemcilerinde Kimden adresine bakın.|
|`reason`|Bileşik kimlik doğrulamasının başarılı veya başarısız olmasının nedeni. Değer 3 basamaklı bir koddur. Örneğin: <ul><li>**000**: İleti açık kimlik doğrulaması (`compauth=fail`) başarısız oldu. Örneğin, bir DMARC alınan ileti karantina veya reddetme eylemiyle başarısız olur.</li><li>**001**: İleti örtük kimlik doğrulaması (`compauth=fail`) başarısız oldu. Bu, gönderen etki alanının yayımlanmış e-posta kimlik doğrulama kayıtlarının olmadığı veya varsa daha zayıf bir hata ilkesine (SPF geçici başarısız veya nötr, DMARC ilkesi `p=none`) sahip olduğu anlamına gelir.</li><li>**002**: Kuruluşun gönderen/etki alanı çifti için sahte e-posta göndermesi açıkça yasaklanmış bir ilkesi vardır. Bu ayar bir yönetici tarafından el ile ayarlanır.</li><li>**010**: İleti DMARC'yi reddetme veya karantinaya alma eylemiyle başarısız oldu ve gönderen etki alanı kuruluşunuzun kabul edilen etki alanlarından biridir (bu, kendi kendine veya kuruluş içi kimlik sahtekarlığına ait bir parçasıdır).</li><li>**1xx** veya **7xx**: İleti kimlik doğrulamasından (`compauth=pass`) geçti. Son iki basamak, Microsoft 365 tarafından kullanılan iç kodlardır.</li><li>**2xx**: Geçici olarak geçirilen örtük kimlik doğrulaması (`compauth=softpass`) iletisi. Son iki basamak, Microsoft 365 tarafından kullanılan iç kodlardır.</li><li>**3xx**: İleti bileşik kimlik doğrulaması (`compauth=none`) için denetlenmedi.</li><li>**4xx** veya **9xx**: İleti bileşik kimlik doğrulamasını atladı (`compauth=none`). Son iki basamak, Microsoft 365 tarafından kullanılan iç kodlardır.</li><li>**6xx**: İleti örtük e-posta kimlik doğrulamasında başarısız oldu ve gönderen etki alanı kuruluşunuzun kabul edilen etki alanlarından biridir (bu, kendi kendine veya kuruluş içi kimlik sahtekarlığına yöneliktir).</li></ul>|
|`smtp.mailfrom`|Adresin `5321.MailFrom` etki alanı (POSTA KIMDEN adresi, P1 gönderen veya zarf gönderen olarak da bilinir). Bu, teslim edilemez raporlar (NDR'ler veya geri dönen iletiler olarak da bilinir) için kullanılan e-posta adresidir.|
|`spf`|İleti için SPF denetiminin sonuçlarını açıklar. Olası değerler şunlardır: <ul><li>`pass (IP address)`: Geçirilen ileti için SPF denetimi ve gönderenin IP adresini içerir. İstemci, gönderenin etki alanı adına e-posta gönderme veya aktarma yetkisine sahip.</li><li>`fail (IP address)`: İleti için SPF denetimi başarısız oldu ve gönderenin IP adresini içeriyor. Bu bazen _zor başarısız olarak_ adlandırılır.</li><li>`softfail (reason)`: SPF kaydı, konağı göndermesine izin verilmediğini ancak geçişte olduğunu belirledi.</li><li>`neutral`: SPF kaydı, IP adresinin gönderme yetkisi olup olmadığını açıkça belirtmektedir.</li><li>`none`: Etki alanının SPF kaydı yok veya SPF kaydı bir sonuç olarak değerlendirilmez.</li><li>`temperror`: Geçici bir hata oluştu. Örneğin, bir DNS hatası. Aynı denetim daha sonra başarılı olabilir.</li><li>`permerror`: Kalıcı bir hata oluştu. Örneğin, etki alanının hatalı biçimlendirilmiş bir SPF kaydı vardır.</li></ul>|
