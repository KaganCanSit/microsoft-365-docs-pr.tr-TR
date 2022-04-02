---
title: E-postayı doğrulamak için DMARC kullanma, kurulum adımları
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
manager: dansimp
audience: ITPro
ms.topic: article
ms.date: 05/10/2021
ms.localizationpriority: high
search.appverid:
- MET150
ms.assetid: 4a05898c-b8e4-4eab-bd70-ee912e349737
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
description: Kuruluştan gönderilen iletileri doğrulamak için Etki Alanı Tabanlı İleti Kimlik Doğrulaması, Raporlama ve Uyumluluk'ı (DMARC) yapılandırmayı öğrenin.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: cae3f007cc046bfc2afd6bb7322c65fe047816d5
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64465893"
---
# <a name="use-dmarc-to-validate-email"></a>E-postayı doğrulamak için DMARC kullanma

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Geçerli olduğu yer:**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Office 365 için Microsoft Defender plan 1 ve plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Etki Alanı Tabanlı İleti Kimlik Doğrulaması, Raporlama ve Uyumluluk ([DMARC](https://dmarc.org)), posta gönderenlerin kimliklerini doğrulamak ve hedef e-posta sistemlerinin etki alanınız üzerinden gönderilen iletilere güven olduğundan emin olmak için Sender Policy Framework (SPF) ve DomainKeys Identified Mail (DKIM) ile çalışır. DMARC'ın SPF ve DKIM ile uygulanması kimlik avı ve kimlik avı e-postalarına karşı ek koruma sağlar. DMARC, posta sistemlerinin SPF veya DKIM denetimlerini başarısız olan etki alanınız üzerinden gönderilen iletilerle ne olacağını belirlemesine yardımcı olur.

> [!TIP]
> Microsoft Akıllı [Güvenlik Birliği (MISA) kataloğunu ziyaret](https://www.microsoft.com/misapartnercatalog) edin ve daha fazla bilgi için DMARC raporlaması sunan üçüncü taraf satıcıları Microsoft 365.

## <a name="how-do-spf-and-dmarc-work-together-to-protect-email-in-microsoft-365"></a>SPF ve DMARC, aynı anda e-postaları korumak için Microsoft 365?

 E-posta iletisi birden çok kaynak veya gönderen adresi içerebilir. Bu adresler farklı amaçlar doğrultusunda kullanılır. Örneğin, şu adresleri düşünün:

- **"Posta Gönderen"** adresi: Göndereni tanımlar ve iletinin teslimi sırasında herhangi bir sorun oluşursa (teslime ilgili olmayan bildirimler gibi) iade bildirimlerinin nereye göndern adres olduğunu belirtir. Bu, e-posta iletinin zarf bölümünde gösterilir ve e-posta uygulamanız tarafından görüntülenmez. Bu bazen 5321.MailFrom adresi veya ters yol adresi olarak da adlandırılan bir adrestir.

- **"From" adresi**: Posta uygulamanız tarafından From adresi olarak görüntülenen adres. Bu adres e-postanın yazarını tanımlar. Yani, iletiyi yazmaktan sorumlu kişinin veya sistemin posta kutusudur. Buna bazen 5322.From adresi denir.

SPF, belirli bir etki alanının yetkili IP adreslerinin listesini sağlamak için bir DNS TXT kaydı kullanır. Normalde, SPF denetimleri yalnızca 5321.MailFrom adresiyle gerçekleştirilir. Bu, SPF'yi kendi başına kullanırken 5322.From adresinin kimliği doğrulanmamış demektir. Bu, kullanıcının bir iletiyi alsa bile SPF denetimi geçtikten sonra 5322.Gönderen adresine kimlik bilgisi olan bir senaryoya olanak sağlar. Örneğin, şu SMTP döküm örneğini düşünün:

```console
S: Helo woodgrovebank.com
S: Mail from: phish@phishing.contoso.com
S: Rcpt to: astobes@tailspintoys.com
S: data
S: To: "Andrew Stobes" <astobes@tailspintoys.com>
S: From: "Woodgrove Bank Security" <security@woodgrovebank.com>
S: Subject: Woodgrove Bank - Action required
S:
S: Greetings User,
S:
S: We need to verify your banking details.
S: Please click the following link to verify that Microsoft has the right information for your account.
S:
S: https://short.url/woodgrovebank/updateaccount/12-121.aspx
S:
S: Thank you,
S: Woodgrove Bank
S: .
```

Bu dökümde, gönderenin adresleri aşağıdaki gibidir:

- Posta adresi (5321.MailFrom): phish@phishing.contoso.com

- Adresten (5322.From): security@woodgrovebank.com

SPF'yi yapılandırdıysanız, alıcı sunucu Adres defteri posta kutusu üzerinde bir phish@phishing.contoso.com. İleti, etki alanı için geçerli bir kaynaktan phishing.contoso.com, SPF denetimi geçer. E-posta istemcisi yalnızca From adresini görüntüleyene kadar, kullanıcı bu iletinin postadan geldiğini security@woodgrovebank.com. Tek başına SPF ile, kimlik woodgrovebank.com hiçbir zaman kimlik doğrulamasılanmamıştır.

DMARC kullanırken, alıcı sunucu da Kaynak adresine yönelik bir denetim gerçekleştirir. Yukarıdaki örnekte, bu kayıt için bir DMARC TXT kaydı woodgrovebank.com, From adresine yönelik denetim başarısız olur.

## <a name="what-is-a-dmarc-txt-record"></a>DMARC TXT kaydı nedir?

SPF için DNS kayıtları gibi, DMARC kaydı da kimlik sahtecisini ve kimlik avını önlemeye yardımcı olan bir DNS metni (TXT) kaydıdır. DMARC TXT kayıtlarını DNS'de yayımlarsiniz. DMARC TXT kayıtları e-posta iletilerinin kaynağını doğrulamak için, e-postanın yazarının IP adresini gönderen etki alanının iddia edilen sahibine karşı doğrular. DMARC TXT kaydı, yetkili giden e-posta sunucularını tanımlar. Bundan sonra, hedef e-posta sistemleri iletilerin yetkili giden e-posta sunucularından geldiğini doğrular.

Microsoft'un DMARC TXT kaydı aşağıdakine benzer:

```console
_dmarc.microsoft.com.   3600    IN      TXT     "v=DMARC1; p=none; pct=100; rua=mailto:d@rua.contoso.com; ruf=mailto:d@ruf.contoso.com; fo=1"
```

DMARC raporlama hizmeti sunan diğer üçüncü taraf satıcıları Microsoft 365[, MISA kataloğunu ziyaret edin](https://www.microsoft.com/misapartnercatalog?IntegratedProducts=DMARCReportingforOffice365).

## <a name="set-up-dmarc-for-inbound-mail"></a>DMARC'ı gelen posta için ayarlama

DMARC'ı posta için ayarlamak ve posta yoluyla göndermek için hiçbir şey Microsoft 365. Hepsi bu kadar. DMARC denetimlerimizi geçiramayan postalara ne olduğunu öğrenmek için bkz. Microsoft 365, [DMARC'de](#how-microsoft-365-handles-inbound-email-that-fails-dmarc) başarısız olan gelen e-postaları işleme.

## <a name="set-up-dmarc-for-outbound-mail-from-microsoft-365"></a>Postadan giden posta için DMARC'Microsoft 365

Microsoft 365 kullanıyorsanız ancak özel bir etki alanı kullanmıyorsanız, yani onmicrosoft.com kullanıyorsanız, DMARC'yi organizasyonunız için yapılandırmak veya uygulamak için başka bir şey yapmaya gerek yok. SPF sizin için zaten ayarlanmıştır ve Microsoft 365 postanız için otomatik olarak DKIM imzası üretir. Bu imza hakkında daha fazla bilgi için bkz. [DKIM ve MICROSOFT 365](use-dkim-to-validate-outbound-email.md#DefaultDKIMbehavior).

 Özel bir etki alanınız varsa veya bu etki alanına ek olarak Exchange şirket içi Microsoft 365 kullanıyorsanız, giden postanız için DMARC'ı el ile uygulamanız gerekir. Özel etki alanınız için DMARC uygulamak şu adımları içerir:

- [1. Adım: Etki alanınız için geçerli posta kaynaklarını belirleme](#step-1-identify-valid-sources-of-mail-for-your-domain)

- [2. Adım: Etki alanınız için SPF'yi ayarlama](#step-2-set-up-spf-for-your-domain)

- [3. Adım: Özel etki alanınız için DKIM'i ayarlama](#step-3-set-up-dkim-for-your-custom-domain)

- [4. Adım: Etki alanınız için DMARC TXT kaydını oluşturma](#step-4-form-the-dmarc-txt-record-for-your-domain)

### <a name="step-1-identify-valid-sources-of-mail-for-your-domain"></a>1. Adım: Etki alanınız için geçerli posta kaynaklarını belirleme

SPF'yi önceden kurdıysanız, bu alıştırmanın üzerinden zaten geçiyorsanız. Öte yandan, DMARC için dikkate alınması gereken başka noktalar da vardır. Etki alanınız için posta kaynaklarını belirtirken, yanıtlamanız gereken iki soru vardır:

- Etki alanımdan hangi IP adresleri ileti gönderiyor?

- Üçüncü taraflara benim adıma gönderilen posta için, 5321.MailFrom ve 5322.From etki alanları aynı olacak mı?

### <a name="step-2-set-up-spf-for-your-domain"></a>2. Adım: Etki alanınız için SPF'yi ayarlama

Artık tüm geçerli gönderenlerin listenize sahip olduğunuuza göre, kimlik doğrulamasını önlemeye yardımcı olmak için [SPF'yi ayarlama adımlarını takip edin](set-up-spf-in-office-365-to-help-prevent-spoofing.md).

Örneğin, contoso.com'Exchange Online'den posta gönderdiğini varsayarak, IP adresi 192.168.0.1 olan şirket içi bir Exchange sunucusu ve IP adresi 192.168.100.100 olan bir web uygulaması varsa, SPF TXT kaydı aşağıdakine benzer olur:

```console
contoso.com  IN  TXT  " v=spf1 ip4:192.168.0.1 ip4:192.168.100.100 include:spf.protection.outlook.com -all"
```

En iyi uygulama olarak, SPF TXT kaydınızı üçüncü taraf gönderenleri hesaba katıldıklarından emin olun.

### <a name="step-3-set-up-dkim-for-your-custom-domain"></a>3. Adım: Özel etki alanınız için DKIM'i ayarlama

SPF'yi ayarlaytktan sonra DKIM'yi ayarlaym gerekir. DKIM, ileti üst bilgisinde yer alan e-posta iletilerine dijital imza eklemenize olanak sağlar. DKIM'i ayarlamıyorsanız ve bunun yerine Microsoft 365 alanınız için varsayılan DKIM yapılandırmasını kullanmasına izin vermezse, DMARC başarısız olabilir. Bunun nedeni, varsayılan DKIM yapılandırmasının ilk onmicrosoft.com alanınızı özel etki alanınız olarak değil 5322.From adresi olarak kullanmasıdır. Bu, etki alanınıza gönderilen tüm e-postalarda 5321.MailFrom ile 5322.From adresleri arasında bir eşleşmesi güçler.

Sizin adına posta gönderen üçüncü taraf gönderenler varsa ve onların göndermekte olduğu posta eşleşmez 5321.MailFrom ve 5322.From adreslerinde ise, DMARC bu e-posta için başarısız olur. Bunu önlemek için, özel olarak bu üçüncü taraf gönderenle etki alanınız için DKIM'i ayarlanız gerekir. Bu, Microsoft 365 üçüncü taraf hizmetten gelen e-postanın kimliğini doğrulamanızı sağlar. Bununla birlikte, yahoo, Gmail ve Comcast gibi diğer kullanıcıların, üçüncü taraf tarafından gönderilmiş e-postaları sizin e-postanız gibi doğrulamalarına da olanak sağlar. Bu özellik, müşterilerinize posta kutularının nerede olursa olsun etki alanınıza güven oluşturmasını sağlar ve kimlik doğrulaması nedeniyle Microsoft 365 bir iletiyi kimlik doğrulaması kimlik doğrulaması geçişini geçtiğinden aynı anda istenmeyen posta olarak işaretlemez.

Etki alanınız için DKIM'i ayarlama yönergeleri için, örneğin üçüncü taraf gönderenler için DKIM'i etki alanınıza kimliklerini doğru şekilde ayarlama hakkında yönergeler için bkz. Özel etki alanınıza gönderilen giden e-postayı doğrulamak için [DKIM kullanma](use-dkim-to-validate-outbound-email.md).

### <a name="step-4-form-the-dmarc-txt-record-for-your-domain"></a>4. Adım: Etki alanınız için DMARC TXT kaydını oluşturma

Burada bahsed yer alsa da, bu seçenekler söz dizimleri için en sık kullanılan Microsoft 365. Etki alanınız için DMARC TXT kaydını şu biçimde biçimlendirin:

```console
_dmarc.domain  TTL  IN  TXT  "v=DMARC1; p=policy; pct=100"
```

Burada:

- *etki* alanı, korumak istediğiniz etki alanıdır. Varsayılan olarak, kayıt postayı etki alanı ve tüm alt etki alanlarından korur. Örneğin, etki alanı \_dmarc.contoso.com, DMARC postayı etki alanına ve posta posta iletisi veya etki alanı gibi tüm alt etki housewares.contoso.com plumbing.contoso.com.

- *TTL* her zaman bir saat eşdeğeri olmalı. TTL için kullanılan birim saat (1 saat), dakika (60 dakika) veya saniye (3600 saniye), etki alanı kayıt şirketine bağlı olarak değişir.

- *pct=100* , bu kuralın e-postanın %100'i için kullanılmaları gerektiğini gösterir.

- *ilke* , DMARC başarısız olursa alıcı sunucunun hangi ilkeyi izlemesi istediğini belirtir. İlkeyi yok, karantinaya alı veya reddeden olarak ayarlayın.

Hangi seçeneklerin kullanıla ilgili bilgi için, MICROSOFT 365'de [DMARC](#best-practices-for-implementing-dmarc-in-microsoft-365) uygulamaya yönelik en iyi yöntemler konusunda yer alan kavramları Microsoft 365.

Örnekler:

- Yok olarak ayarlanmış ilke

    ```console
    _dmarc.contoso.com 3600 IN  TXT  "v=DMARC1; p=none"
    ```

- Karantinaya alınmış ilke

    ```console
    _dmarc.contoso.com 3600 IN  TXT  "v=DMARC1; p=quarantine"
    ```

- Reddedilen ilke kümesi

    ```console
    _dmarc.contoso.com  3600 IN  TXT  "v=DMARC1; p=reject"
    ```

Kaydınızı kurduktan sonra, etki alanı kayıt şirketinizin kaydını güncelleştirmeniz gerekir.

## <a name="dmarc-mail-public-preview-feature"></a>DMARC Mail (Genel Önizleme özelliği)

> [!CAUTION]
> Posta her gün gönderilmeyebilirsiniz ve genel önizleme sırasında raporun kendisi değişebilir. DMARC toplam rapor e-postaları Tüketici hesaplarından (örneğin, hotmail.com, outlook.com veya posta live.com beklİr.

Bu örnekte DMARC TXT kaydı: `dmarc.microsoft.com.   3600    IN      TXT     "v=DMARC1; p=none; pct=100; rua=mailto:d@rua.agari.com; ruf=mailto:d@ruf.agari.com; fo=1"`*rua* adresini, bu örnekte üçüncü taraf şirket Agari tarafından işlenmiş olarak bulabilirsiniz. Bu adres çözümleme için 'toplama geri bildirimi' göndermek için kullanılır ve rapor oluşturmak için kullanılır.

> [!TIP]
> DMARC raporlaması sunan diğer üçüncü taraf satıcıları görüntülemek için [MISA](https://www.microsoft.com/misapartnercatalog) kataloğunu ziyaret Microsoft 365. DMARC 'rua' adresleri hakkında daha fazla bilgi için [bkz. IETF.org'un '](https://datatracker.ietf.org/doc/html/rfc7489) Etki Alanı Tabanlı İleti Kimlik Doğrulaması, Raporlama ve Uyum (DMARC)'.


## <a name="best-practices-for-implementing-dmarc-in-microsoft-365"></a>DMARC'ı Microsoft 365'de uygulamak için en Microsoft 365

DMARC'ı, posta akışınızı kalan sürelerden etkilenmeden aşamalı olarak gerçekleştirebilirsiniz. Bu adımları izleyen bir uygulama planı oluşturun ve uygulayın. Bir sonraki adıma ilerlemeden önce, bu adımlardan her biri önce bir alt etki alanı, sonra da diğer alt etki alanları ve son olarak da kuruluşta en üst düzey etki alanı ile uygulayın.

1. DMARC uygulamanın etkisini izleme

    DMARC alıcılarının, bu etki alanını kullanırken size ileti göndermelerini talep etmek üzere bir alt etki alanı veya etki alanı için basit bir izleme modu kaydıyla başlayabilirsiniz. İzleme modu kaydı, ilkesi yok (p=none) olarak ayarlanmış bir DMARC TXT kaydıdır. Birçok şirket P=none içeren bir DMARC TXT kaydı yayımlar, çünkü daha kısıtlayıcı bir DMARC ilkesi yayımlayan e-postanın ne kadarlık bir soruna neden olduğundan emin değildirler.

    Bunu ileti altyapınıza SPF veya DKIM'yi uygulamaya başlamadan önce bile gerçekleştirin. Bununla birlikte, SPF ve DKIM uygulayana kadar DMARC kullanarak postayı etkili bir şekilde karantinaya alama veya reddedebilirsiniz. Siz SPF ve DKIM'yi tanıtacakken, DMARC aracılığıyla oluşturulan raporlar, bu denetimleri geçiren ve geçiremediklerinden ileti sayılarını ve kaynaklarını sağlar. Yasal trafiğinizin ne kadarı olduğunu veya bu trafik kapsamında olmadığını kolayca görebilir ve sorunları giderebilirsiniz. Ayrıca, dolandırıcılık amaçlı iletilerin kaç kez gönderildiğini ve bunların nereden gönderildiğini de görmeye başlarsınız.

2. DMARC'da başarısız olan dış posta sistemlerinin postayı karantinaya alınmasını talep eder

    Yasal trafiğinizin çoğunun veya bir çoğunun SPF ve DKIM tarafından korun olduğuna inanıyor ve DMARC'yi uygulamanın etkisini anlıyoruzsa, karantina ilkesi de  uygulanır. Karantina ilkesi, ilkesi karantina (p=karantina) olarak ayarlanmış bir DMARC TXT kaydıdır. Bunu yaparak, DMARC alıcılarından, etki alanınıza gelen ve DMARC'de başarısız olan iletileri, müşterilerin gelen kutuları yerine istenmeyen posta klasörünün yerel eşdeğerlerine koymalarını istiyor olursunuz.

3. Dış posta sistemlerinin DMARC başarısız olan iletileri kabul etmelerini talep etme

    Son adım, reddetme ilkesi uygulamaktır. Reddetme ilkesi, ilkesinde reddetme ayarı (p=reddet) olan bir DMARC TXT kaydıdır. Bunu yapmak için, DMARC alıcıların DMARC denetimlerini başarısız olan iletileri kabul etmelerini istemeye devam edersiniz.

4. Alt etki alanı için DMARC nasıl ayarlanır?

   DMARC, DNS'de TXT kaydı olarak bir ilke yayımlar ve hiyerarşik olur (örneğin, contoso.com için yayımlanan bir ilke, alt etki alanı için açık olarak farklı bir ilke tanımlanmamışsa sub.domain.contonos.com'e uygulanır). Kuruluşlar daha geniş kapsam için daha az sayıda yüksek düzeyli DMARC kaydı belirteci olarak bu yararlı olur. Alt etki alan adlarının en üst düzey etki alanının DMARC kaydını devralmalarını istemiyorken, açık alt etki alanı DMARC kayıtlarını yapılandırmak için dikkat gerekir.

   Ayrıca, alt etki alanları değeri ekleyerek e-posta göndermeleri gerekmaması gereken bir zamanda DMARC için joker karakter türünde bir ilke de `sp=reject` eklersiniz. Örneğin:

   ```text
   _dmarc.contoso.com. TXT "v=DMARC1; p=reject; sp=reject; ruf=mailto:authfail@contoso.com; rua=mailto:aggrep@contoso.com"
   ```

## <a name="how-microsoft-365-handles-outbound-email-that-fails-dmarc"></a>DMARC Microsoft 365 başarısız olan giden e-postayı nasıl işleyebilirsiniz?

Bir ileti Microsoft 365'den gidense ve DMARC'de başarısız olursa ve ilkeyi p=karantina veya p=reddet olarak ayardınız, ileti giden iletiler için Yüksek riskli teslim havuzu üzerinden [yönlendirildi](high-risk-delivery-pool-for-outbound-messages.md). Giden e-posta için geçersiz kılmaz.

DMARC reddetme ilkesi yayımlarsanız (p=reject), Microsoft 365'daki başka hiçbir müşteri etki alanınızı doğrulayamaz, çünkü iletiler hizmet üzerinden giden bir iletiyi geçişte etki alanınız için SPF veya DKIM'yi geçemez. Öte yandan, DMARC reddetme ilkesi yayımlarsanız ancak tüm e-postanız Microsoft 365 aracılığıyla kimliği doğrulanmamışsa, bir bazıları gelen e-posta için istenmeyen posta olarak işaretlenir (yukarıda açıklandığı gibi) veya SPF yayımlamaz ve bu ilkeyi hizmet üzerinden dışarı aktarmayı denerseniz reddedilir. Örneğin, DMARC TXT kaydınızı ekleyebilirsiniz ve etki alanınız adına posta gönderecek sunucuların ve uygulamaların IP adreslerinden bir birini ekleyebilirsiniz.

## <a name="how-microsoft-365-handles-inbound-email-that-fails-dmarc"></a>DMARC Microsoft 365 başarısız olan gelen e-postayı nasıl işleyebilirsiniz?

Gönderen sunucunun DMARC `p=reject`ilkesi ise, [Exchange Online Protection](exchange-online-protection-overview.md) (EOP) iletiyi reddetmek yerine kimlik işareti olarak işaretler. Başka bir deyişle, gelen e-posta için Microsoft 365 ve `p=reject` aynı `p=quarantine` şekilde davranabilirsiniz. Yöneticiler, kimlik avı önleme ilkesi içinde kimlik sahtesi olarak sınıflandırılmış [iletilerde eylemi tanımlayabilir](set-up-anti-phishing-policies.md).

Microsoft 365 e-posta DMARC başarısız olabilir, çünkü böyle yapılandırılır. Örneğin, bir ileti bir posta listesine gönderilirse ve bu da iletiyi tüm liste katılımcılarına iletirse, DMARC başarısız olabilir. Bu Microsoft 365 reddedilirse, insanlar yasal e-postayı kaybedebilir ve e-postayı alma yolu yoktur. Bunun yerine, bu iletiler yine de DMARC başarısız olur, ancak istenmeyen posta olarak işaretlenir ve reddedilir. İsterseniz, kullanıcılar şu yöntemlerle bu iletileri gelen kutularına almaya devam edebilirsiniz:

- Kullanıcılar, e-posta istemcilerini kullanarak güvenilir gönderenleri tek tek ekler.

- Yöneticiler, kimliği [doğrun burada yer alan](learn-about-spoof-intelligence.md) gönderenden gelen iletilere izin vermek için bilgi oturumları veya Kiracı İzin/Engelleme Listesi'ni kullanabilir.[](tenant-allow-block-list.md)

- Yöneticiler, bu Exchange gönderenler için iletilere izin veren tüm kullanıcılar için bir posta akışı kuralı (aktarım kuralı olarak da bilinir) oluşturabilir.

Daha fazla bilgi için bkz [. Güvenilir gönderen listeleri oluşturma](create-safe-sender-lists-in-office-365.md).

## <a name="how-microsoft-365-utilizes-authenticated-received-chain-arc"></a>Kimliği Microsoft 365 Alınan Zinciri (ARC) nasıl kullanır?

Bu çalışma Microsoft 365 barındırılan tüm posta kutuları, artık iletilerin daha iyi teslim edilebilirliği ve gelişmiş anti-spoofing korumasıyla ARC avantajından yararlanabilir. E-posta kaynak sunucudan alıcı posta kutusuna yönlendirilen zaman, ARC tüm katılımcı aracılardan veya atlamalardan gelen e-posta kimlik doğrulama sonuçlarını korur. ARC'dan önce, iletme kuralları veya otomatik imzalar gibi e-posta yönlendirme aracıları tarafından yapılan değişiklikler, e-posta alıcı posta kutusuna ulaşana kadar DMARC hatalarına neden olabilir. ARC ile, kimlik doğrulama sonuçlarının şifreleme özelliği, Microsoft 365 e-posta gönderenin kimlik doğrulamasını doğrulamaya olanak sağlar.

Microsoft 365 şu anda Microsoft ARC Sealer olduğunda kimlik doğrulama sonuçlarını doğrulamak için ARC kullansa da, gelecekte üçüncü taraf ARC kapaticileri için destek eklemeyi planlıyoruz.

## <a name="troubleshooting-your-dmarc-implementation"></a>DMARC uygulama sorun giderme

Etki alanınıza yapılan MX kayıtlarını ilk girdi EOP değilken yapılandırdıysanız, etki alanınız için DMARC hataları zorlanmaz.

Müşteriysiniz ve etki alanınıza ek olarak etki alanının birincil MX kaydı EOP'ye işaret etse bile, DMARC'nin avantajlarından yararlanamayacaktır. Örneğin, MX kaydını şirket içi posta sunucunuza işaret ediyor ve sonra e-postayı bir bağlayıcı kullanarak EOP'ye yönlendiriyorsanız, DMARC çalışmayacaktır. Bu senaryoda, alıcı etki alanı birincil MX Accepted-Domains EOP değildir. Örneğin, örneğin, contoso.com MX'in kendisine göre olduğunu ve EOP'i ikincil MX kaydı olarak kullandığını varsayalım; contoso.com'un MX kaydı aşağıdaki gibi olur:

```console
contoso.com     3600   IN  MX  0  mail.contoso.com
contoso.com     3600   IN  MX  10 contoso-com.mail.protection.outlook.com
```

E-postanın çoğu veya çoğu birincil MX mail.contoso.com EOP'ye yönlendirilen e-posta olur. Bazı durumlarda, EOP'leri hiç MX kaydı olarak listeleyem ve e-postanızı yönlendiren bağlayıcıları bağlayın. DMARC doğrulamasının yapılması için EOP'nin ilk girdisi olması gerekir. Yalnızca doğrulamayı sağlar; tüm şirket içi/O365 olmayan sunucuların DMARC denetimleri yapmalarını sağlar.  DMARC TXT kaydını ayar takımınız, müşterinin etki alanı için zorunlu tutul almaya (sunucu için değil) uygundur, ancak bu zoru aslında alıcı sunucuya uygulanır.  Alıcı sunucu olarak EOP'i ayardısanız, DMARC zorlaması EOP tarafından esnetir.

:::image type="content" source="../../media/Tp_DMARCTroublehoot.png" alt-text="DMARC için sorun giderme grafiği" lightbox="../../media/Tp_DMARCTroublehoot.png":::

## <a name="for-more-information"></a>Daha fazla bilgi için

DMARC hakkında daha fazla bilgi mi istiyor musunuz? Bu kaynaklar yardımcı olabilir.

- [İstenmeyen posta önleme ileti üst bilgileri](anti-spam-message-headers.md), DMARC denetimleri için Microsoft 365 dizimi ve üst bilgi alanlarını içerir.

- M3AAWG (Mesajlaşma,<sup></sup> Kötü Amaçlı Yazılım, Mobil Kötü Amaçlı Yazılımdan Koruma Çalışma Grubu) ile [DMARC](https://www.m3aawg.org/activities/training/dmarc-training-series) Eğitim Serisini edin.

- Denetim listesini [dmarcian'da kullanın](https://space.dmarcian.com/deployment/).

- Doğrudan dosyanın [kaynağına DMARC.org](https://dmarc.org).

## <a name="see-also"></a>Ayrıca bkz.

[How Microsoft 365 uses Sender Policy Framework (SPF) to prevent spoofing](how-office-365-uses-spf-to-prevent-spoofing.md)

[**SPF'yi Microsoft 365 spoofing'i önlemeye yardımcı olmak için ayarlama**](set-up-spf-in-office-365-to-help-prevent-spoofing.md)

[**Aynı adreste özel etki alanınıza gönderilen giden e-postayı doğrulamak için DKIM Microsoft 365**](use-dkim-to-validate-outbound-email.md)
