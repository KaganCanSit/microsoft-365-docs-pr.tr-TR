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
description: Kuruluşunuzdan gönderilen iletileri doğrulamak için Etki Alanı Tabanlı İleti Kimlik Doğrulaması, Raporlama ve Uyumluluk (DMARC) yapılandırmayı öğrenin.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: a3e5cc711aef4e81833540572027b8d06087c510
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/29/2022
ms.locfileid: "66486939"
---
# <a name="use-dmarc-to-validate-email"></a>E-postayı doğrulamak için DMARC kullanma

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Uygulandığı öğe**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Office 365 için Microsoft Defender plan 1 ve plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Etki Alanı Tabanlı İleti Kimlik Doğrulaması, Raporlama ve Uyumluluk ([DMARC](https://dmarc.org)), posta gönderenlerin kimliğini doğrulamak için Sender Policy Framework (SPF) ve DomainKeys Identified Mail (DKIM) ile çalışır.

DMARC, hedef e-posta sistemlerinin etki alanınızdan gönderilen iletilere güvenmesini sağlar. DMARC'yi SPF ve DKIM ile kullanmak, kuruluşlara kimlik sahtekarlığına ve kimlik avı e-postaya karşı daha fazla koruma sağlar. DMARC, posta sistemlerinin etki alanınızdan SPF veya DKIM denetimleri başarısız olan iletilerle ne yapacağına karar vermesine yardımcı olur.

> [!TIP]
> Microsoft 365 için DMARC raporlaması sunan üçüncü taraf satıcıları görüntülemek için Microsoft [Akıllı Güvenlik Birliği (MISA)](https://www.microsoft.com/misapartnercatalog) kataloğunu ziyaret edin.

## <a name="how-do-spf-and-dmarc-work-together-to-protect-email-in-microsoft-365"></a>MICROSOFT 365'te e-postayı korumak için SPF ve DMARC birlikte nasıl çalışır?

 E-posta iletisi birden çok gönderen veya gönderen adresi içerebilir. Bu adresler farklı amaçlar için kullanılır. Örneğin, şu adresleri göz önünde bulundurun:

- **"Posta Kaynağı" adresi**: Göndereni tanımlar ve iletinin tesliminde herhangi bir sorun oluşursa (teslim edilemedi bildirimleri gibi) iade bildirimlerinin gönderileceği yeri belirtir. *Posta Kimden adresi* , e-posta iletisinin zarf bölümünde görünür ve e-posta uygulamanız tarafından görüntülenmez ve bazen *5321.MailFrom adresi* veya *ters yol adresi* olarak adlandırılır.

- **"Kimden" adresi**: Posta uygulamanız tarafından Kimden adresi olarak görüntülenen adres. *Kimden adresi* , e-postanın yazarını tanımlar. Yani, iletiyi yazmaktan sorumlu kişinin veya sistemin posta kutusudur. *Kimden adresi* bazen *5322.Kimden adresi* olarak adlandırılır.

SPF, belirli bir etki alanı için yetkili gönderen IP adreslerini listelemek için dns TXT kaydı kullanır. Normalde SPF denetimleri yalnızca 5321.MailFrom adresinde gerçekleştirilir. 5322.From adresi, SPF'yi tek başına kullandığınızda doğrulanmamıştır. Bu, kullanıcının SPF denetimlerinden geçen ancak sahte 5322 içeren bir ileti aldığı bir senaryoya olanak tanır. Gönderen adresinden. Örneğin, şu SMTP transkriptlerini göz önünde bulundurun:

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

Bu transkriptte gönderen adresleri aşağıdaki gibidir:

- Adresten posta (5321.MailFrom): phish@phishing.contoso.com

- Kimden adresi (5322.Kimden): security@woodgrovebank.com

SPF'yi yapılandırdıysanız, alıcı sunucu posta adresi phish@phishing.contoso.com karşı bir denetim yapar. İleti, etki alanı phishing.contoso.com için geçerli bir kaynaktan geldiyse SPF denetimi geçer. E-posta istemcisi yalnızca Kimden adresini görüntülediğinden, kullanıcı bu iletinin security@woodgrovebank.com'dan geldiğini görür. Yalnızca SPF ile woodgrovebank.com geçerliliği hiçbir zaman doğrulanamadı.

DMARC kullandığınızda, alıcı sunucu Da kimden adresi üzerinde bir denetim gerçekleştirir. Yukarıdaki örnekte, woodgrovebank.com için bir DMARC TXT kaydı varsa Kimden adresiyle ilgili denetim başarısız olur.

## <a name="what-is-a-dmarc-txt-record"></a>DMARC TXT kaydı nedir?

SPF'nin DNS kayıtları gibi, DMARC kaydı da kimlik sahtekarlığı ve kimlik avının önlenmesine yardımcı olan bir DNS metni (TXT) kaydıdır. DMARC TXT kayıtlarını DNS'de yayımlarsınız. DMARC TXT kayıtları, e-posta yazarının IP adresini gönderen etki alanının iddia edilen sahibine karşı doğrulayarak e-posta iletilerinin kaynağını doğrular. DMARC TXT kaydı, yetkili giden e-posta sunucularını tanımlar. Hedef e-posta sistemleri daha sonra aldıkları iletilerin yetkili giden e-posta sunucularından geldiğini doğrulayabilir.

Microsoft'un DMARC TXT kaydı şuna benzer:

```console
_dmarc.microsoft.com.   3600    IN      TXT     "v=DMARC1; p=none; pct=100; rua=mailto:d@rua.contoso.com; ruf=mailto:d@ruf.contoso.com; fo=1"
```

Microsoft 365 için DMARC raporlaması sunan daha fazla üçüncü taraf satıcı için [MISA kataloğunu ziyaret edin](https://www.microsoft.com/misapartnercatalog?IntegratedProducts=DMARCReportingforOffice365).

## <a name="set-up-dmarc-for-inbound-mail"></a>Gelen posta için DMARC'i ayarlama

Microsoft 365'te aldığınız postalar için DMARC'yi ayarlamak için hiçbir şey yapmanız gerekmez. Her şey halledildi. DMARC denetimlerimizi geçemedi postaya ne olduğunu öğrenmek istiyorsanız bkz. [Microsoft 365, DMARC'de başarısız olan gelen e-postaları nasıl işler](#how-microsoft-365-handles-inbound-email-that-fails-dmarc)?

## <a name="set-up-dmarc-for-outbound-mail-from-microsoft-365"></a>Microsoft 365'ten giden postalar için DMARC'i ayarlama

Microsoft 365 kullanıyorsanız ancak özel etki alanı kullanmıyorsanız (onmicrosoft.com kullanıyorsanız) başka bir şey yapmanız gerekmez. SPF sizin için zaten ayarlanmıştır ve Microsoft 365 giden postanız için otomatik olarak bir DKIM imzası oluşturur. Kuruluşunuz için DMARC'yi yapılandırmak için yapılacak başka bir şey yoktur. Bu imza hakkında daha fazla bilgi için bkz. [DKIM ve Microsoft 365 için varsayılan davranış](use-dkim-to-validate-outbound-email.md#DefaultDKIMbehavior).

 Özel bir etki alanınız varsa veya Microsoft 365 ile birlikte şirket içi Exchange sunucuları kullanıyorsanız, giden postanız için DMARC'yi el ile ayarlamanız gerekir. Özel etki alanınız için DMARC'nin ayarlanması şu adımları içerir:

- [1. Adım: Etki alanınız için geçerli posta kaynaklarını belirleme](#step-1-identify-valid-sources-of-mail-for-your-domain)

- [2. Adım: Etki alanınız için SPF'yi ayarlama](#step-2-set-up-spf-for-your-domain)

- [3. Adım: Özel etki alanınız için DKIM'i ayarlama](#step-3-set-up-dkim-for-your-custom-domain)

- [4. Adım: Etki alanınız için DMARC TXT kaydını oluşturma](#step-4-form-the-dmarc-txt-record-for-your-domain)

### <a name="step-1-identify-valid-sources-of-mail-for-your-domain"></a>1. Adım: Etki alanınız için geçerli posta kaynaklarını belirleme

SPF'yi zaten ayarladıysanız, bu alıştırmayı zaten yapmışsınız demektir. DMARC ile ilgili dikkat edilmesi gereken başka noktalar da vardır. Etki alanınız için posta kaynaklarını tanımlarken şu iki soruyu yanıtlayın:

- Hangi IP adresleri etki alanımdan ileti gönderir?

- Benim adıma üçüncü taraflardan gönderilen postalar için 5321.MailFrom ve 5322.From etki alanları eşleşecek mi?

### <a name="step-2-set-up-spf-for-your-domain"></a>2. Adım: Etki alanınız için SPF'yi ayarlama

Artık tüm geçerli gönderenlerinizin listesini oluşturduğunuza göre, kimlik [sahtekarlıklarını önlemeye yardımcı olmak için SPF'yi ayarlama](set-up-spf-in-office-365-to-help-prevent-spoofing.md) adımlarını izleyebilirsiniz.

Örneğin, contoso.com ip adresi 192.168.0.1 olan şirket içi exchange sunucusu Exchange Online ve IP adresi 192.168.100.100 olan bir web uygulamasından posta gönderdiği varsayıldığında SPF TXT kaydı şöyle görünür:

```console
contoso.com  IN  TXT  " v=spf1 ip4:192.168.0.1 ip4:192.168.100.100 include:spf.protection.outlook.com -all"
```

En iyi uygulama olarak, SPF TXT kaydınızın üçüncü taraf gönderenleri dikkate aldığından emin olun.

### <a name="step-3-set-up-dkim-for-your-custom-domain"></a>3. Adım: Özel etki alanınız için DKIM'i ayarlama

SPF'yi ayarladıktan sonra DKIM'i ayarlamanız gerekir. DKIM, ileti üst bilgisindeki e-posta iletilerine dijital imza eklemenizi sağlar. DKIM'yi ayarlamaz ve bunun yerine Microsoft 365'in etki alanınız için varsayılan DKIM yapılandırmasını kullanmasına izin verirseniz, DMARC başarısız olabilir. Varsayılan DKIM yapılandırması özgün *onmicrosoft.com* etki alanınızı *özel* etki alanınız değil *5321.MailFrom* adresi olarak kullandığından bu hata oluşabilir. Bu, etki alanınızdan gönderilen tüm e-postalardaki *5321.MailFrom* ile *5322.From adresleri* arasında bir uyuşmazlık oluşturur.

Sizin yerinize posta gönderen üçüncü taraf gönderenleriniz varsa ve gönderdikleri posta 5321.MailFrom ve 5322.From adreslerinde eşleşmiyorsa, DMARC bu e-posta için başarısız olur. Bunu önlemek için etki alanınız için DKIM'i özellikle üçüncü taraf gönderenle ayarlamanız gerekir. Bu, Microsoft 365'in bu üçüncü taraf hizmetten gelen e-postaların kimliğini doğrulamasını sağlar. Bununla birlikte, yahoo, gmail ve comcast gibi diğer kişilerin üçüncü taraf tarafından gönderilen e-postayı sizin tarafınızdan gönderilmiş gibi doğrulamalarına da olanak tanır. Bu, müşterilerinizin posta kutusu nerede olursa olsun etki alanınızla güven oluşturmasına olanak sağladığından ve aynı zamanda Microsoft 365, etki alanınız için kimlik doğrulama denetimlerinden geçtiği için kimlik sahtekarlığına bağlı olarak bir iletiyi istenmeyen posta olarak işaretlemediğinden yararlıdır.

Etki alanınızda kimlik sahtekarlığına neden olabilecek üçüncü taraf gönderenler için DKIM'i ayarlama da dahil olmak üzere etki alanınız için DKIM'i ayarlama yönergeleri için bkz. [Özel etki alanınızdan gönderilen giden e-postayı doğrulamak için DKIM kullanma](use-dkim-to-validate-outbound-email.md).

### <a name="step-4-form-the-dmarc-txt-record-for-your-domain"></a>4. Adım: Etki alanınız için DMARC TXT kaydını oluşturma

Burada bahsedilmeyen başka söz dizimi seçenekleri olsa da, Microsoft 365 için en yaygın olarak kullanılan seçenekler bunlardır. Etki alanınız için DMARC TXT kaydını şu biçimde oluşturun:

```console
_dmarc.domain  TTL  IN  TXT  "v=DMARC1; p=policy; pct=100"
```

Konum:

- *etki alanı* , korumak istediğiniz etki alanıdır. Varsayılan olarak, kayıt postayı etki alanından ve tüm alt etki alanından korur. Örneğin, dmarc.contoso.com belirtirseniz \_, DMARC postayı etki alanından ve housewares.contoso.com veya plumbing.contoso.com gibi tüm alt etki alanından korur.

- *TTL* her zaman bir saatin eşdeğeri olmalıdır. TTL için saat (1 saat), dakika (60 dakika) veya saniye (3600 saniye) için kullanılan birim, etki alanınızın kayıt şirketine bağlı olarak değişir.

- *pct=100* , bu kuralın e-postanın %100'ünün kullanılması gerektiğini gösterir.

- *policy* , DMARC başarısız olursa alıcı sunucunun hangi ilkeyi izlemesini istediğinizi belirtir. İlkeyi yok, karantinaya alabilir veya reddedebilirsiniz.

Hangi seçeneklerin kullanılacağı hakkında bilgi edinmek [için Microsoft 365'te DMARC'yi uygulamaya yönelik en iyi yöntemler başlığı altında](#best-practices-for-implementing-dmarc-in-microsoft-365) verilen kavramlar hakkında bilgi sahibi olun.

Örnekler:

- İlke yok olarak ayarlandı

    ```console
    _dmarc.contoso.com 3600 IN  TXT  "v=DMARC1; p=none"
    ```

- İlke karantinaya alındı

    ```console
    _dmarc.contoso.com 3600 IN  TXT  "v=DMARC1; p=quarantine"
    ```

- İlke reddedecek şekilde ayarlandı

    ```console
    _dmarc.contoso.com  3600 IN  TXT  "v=DMARC1; p=reject"
    ```

Kaydınızı oluşturduktan sonra, etki alanı kayıt şirketinizde kaydı güncelleştirmeniz gerekir.

## <a name="dmarc-mail-public-preview-feature"></a>DMARC Mail (Genel Önizleme özelliği)

> [!CAUTION]
> Postalar günlük olarak gönderilmeyebilir ve genel önizleme sırasında raporun kendisi değişebilir. DMARC toplu rapor e-postaları Tüketici hesaplarından (hotmail.com, outlook.com veya live.com hesapları gibi) beklenebilir.

Bu örnekte DMARC TXT kaydı: `dmarc.microsoft.com.   3600    IN      TXT     "v=DMARC1; p=none; pct=100; rua=mailto:d@rua.agari.com; ruf=mailto:d@ruf.agari.com; fo=1"`, bu örnekte üçüncü taraf şirket Agari tarafından işlenen *rua* adresini görebilirsiniz. Bu adres analiz için 'toplu geri bildirim' göndermek için kullanılır ve rapor oluşturmak için kullanılır.

> [!TIP]
> Microsoft 365 için DMARC raporlaması sunan daha fazla üçüncü taraf satıcıyı görüntülemek için [MISA kataloğunu](https://www.microsoft.com/misapartnercatalog) ziyaret edin. DMARC 'rua' adresleri hakkında daha fazla bilgi için [IETF.org'un 'Etki Alanı Tabanlı İleti Kimlik Doğrulaması, Raporlama ve Uyumluluk (DMARC)](https://datatracker.ietf.org/doc/html/rfc7489) ' bölümüne bakın.

## <a name="best-practices-for-implementing-dmarc-in-microsoft-365"></a>Microsoft 365'te DMARC uygulamak için en iyi yöntemler

DMARC'yi posta akışınızın geri kalanını etkilemeden aşamalı olarak uygulayabilirsiniz. Bu adımları izleyen bir dağıtım planı oluşturun ve uygulayın. Sonraki adıma geçmeden önce bu adımların her birini önce bir alt etki alanıyla, sonra diğer alt etki alanlarıyla ve son olarak da kuruluşunuzdaki en üst düzey etki alanıyla gerçekleştirin.

1. DMARC'yi uygulamanın etkisini izleme

    DMARC alıcılarının bu etki alanını kullanarak gördükleri iletiler hakkında size istatistik göndermesini isteyen bir alt etki alanı veya etki alanı için basit bir izleme modu kaydıyla başlayın. İzleme modu kaydı, ilkesi yok (p=yok) olarak ayarlanmış bir DMARC TXT kaydıdır. Birçok şirket, daha kısıtlayıcı bir DMARC ilkesi yayımlayarak ne kadar e-posta kaybedecekleri konusunda emin olmadıkları için p=none ile bir DMARC TXT kaydı yayımlar.

    Bunu, mesajlaşma altyapınıza SPF veya DKIM uygulamadan önce bile yapabilirsiniz. Ancak, SPF ve DKIM uygulayana kadar DMARC kullanarak postaları etkili bir şekilde karantinaya alamaz veya reddedemezsiniz. SPF ve DKIM'yi tanıttıkça, DMARC aracılığıyla oluşturulan raporlar, bu denetimleri geçiren iletilerin sayılarını ve kaynaklarını verir ve bunu gerçekleştirmeyenleri verir. Geçerli trafiğinizin ne kadarının bu trafiğin kapsamına alınıp alına olmadığını kolayca görebilir ve sorunları giderebilirsiniz. Ayrıca, kaç sahte ileti gönderildiğini ve bunların nereden gönderildiğini de görmeye başlayacaksınız.

2. Dış posta sistemlerinin DMARC'de başarısız olan postaları karantinaya almalarını isteme

    Geçerli trafiğinizin tamamının veya çoğunun SPF ve DKIM tarafından korunduğunu düşünüyorsanız ve DMARC'yi uygulamanın etkisini anladığınızda, bir karantina ilkesi uygulayabilirsiniz. Karantina ilkesi, ilkesi karantinaya (p=karantina) olarak ayarlanmış bir DMARC TXT kaydıdır. Bunu yaparak, DMARC alıcılarından etki alanınızdan DMARC'den başarısız olan iletileri müşterilerinizin gelen kutuları yerine istenmeyen posta klasörünün yerel eşdeğerine yerleştirmelerini istersiniz.

3. Dış posta sistemlerinin DMARC'de başarısız olan iletileri kabul etmemesi isteği

    Son adım bir reddetme ilkesi uygulamaktır. Reddetme ilkesi, ilkesi reddedecek (p=reddet) olarak ayarlanmış bir DMARC TXT kaydıdır. Bunu yaptığınızda DMARC alıcılarından DMARC denetimlerinde başarısız olan iletileri kabul etmelerini istemeniz gerekir.

4. Alt etki alanı için DMARC nasıl ayarlanır?

   DMARC, DNS'de bir ilkeyi TXT kaydı olarak yayımlayarak uygulanır ve hiyerarşiktir (örneğin, alt etki alanı için farklı bir ilke açıkça tanımlanmadığı sürece sub.domain.contonos.com için contoso.com için yayımlanan bir ilke geçerli olur). Kuruluşlar daha geniş kapsamlı bir kapsama için daha az sayıda üst düzey DMARC kaydı belirtebildiğinden bu yararlı olur. Alt etki alanının en üst düzey etki alanının DMARC kaydını devralmasını istemediğiniz açık alt etki alanı DMARC kayıtlarını yapılandırmaya özen gösterilmelidir.

   Ayrıca, değeri ekleyerek alt etki alanları e-posta göndermemesi gerektiğinde DMARC için joker karakter türü ilkesi `sp=reject` ekleyebilirsiniz. Örneğin:

   ```text
   _dmarc.contoso.com. TXT "v=DMARC1; p=reject; sp=reject; ruf=mailto:authfail@contoso.com; rua=mailto:aggrep@contoso.com"
   ```

## <a name="how-microsoft-365-handles-outbound-email-that-fails-dmarc"></a>Microsoft 365, DMARC'de başarısız olan giden e-postaları nasıl işler?

Microsoft 365'ten giden bir ileti varsa ve DMARC başarısız olursa ve ilkeyi p=quarantine veya p=reject olarak ayarladıysanız, ileti [giden iletiler için Yüksek riskli teslim havuzu](high-risk-delivery-pool-for-outbound-messages.md) üzerinden yönlendirilir. Giden e-posta için geçersiz kılma yoktur.

DMARC reddetme ilkesi (p=reject) yayımlarsanız, hizmetten giden bir iletiyi aktarırken iletiler etki alanınız için SPF veya DKIM geçiremeyeceğinden, Microsoft 365'teki başka hiçbir müşteri etki alanınızı yanıltamaz. Ancak, bir DMARC reddetme ilkesi yayımlıyorsanız ancak e-postanızın tamamı Microsoft 365 aracılığıyla doğrulanmamışsa, bazıları gelen e-posta için istenmeyen posta olarak işaretlenebilir (yukarıda açıklandığı gibi) veya SPF'yi yayımlamaz ve hizmet üzerinden giden geçiş yapmaya çalışırsanız reddedilir. Örneğin, DMARC TXT kaydınızı oluştururken etki alanınız adına posta gönderen sunucular ve uygulamalar için BAZı IP adreslerini eklemeyi unutursanız bu durum ortaya çıkar.

## <a name="how-microsoft-365-handles-inbound-email-that-fails-dmarc"></a>Microsoft 365, DMARC'de başarısız olan gelen e-postaları nasıl işler?

Gönderen sunucunun DMARC ilkesi ise`p=reject`[, Exchange Online Protection](exchange-online-protection-overview.md) (EOP) iletiyi reddetmek yerine sahte olarak işaretler. Başka bir deyişle, gelen e-posta için `p=reject` Microsoft 365 aynı şekilde davranır `p=quarantine` . Yöneticiler [, kimlik avı önleme ilkesi](set-up-anti-phishing-policies.md) içinde kimlik sahtekarlığı olarak sınıflandırılan iletilere yönelik eylemi tanımlayabilir.

Bazı geçerli e-postalar DMARC'de başarısız olabileceği için Microsoft 365 bu şekilde yapılandırılır. Örneğin, bir ileti tüm liste katılımcılarına ileti gönderen bir posta listesine gönderilirse DMARC başarısız olabilir. Microsoft 365 bu iletileri reddettiyse, kişiler geçerli e-postayı kaybedebilir ve bu e-postayı almalarının hiçbir yolu yoktur. Bunun yerine, bu iletiler DMARC'de başarısız olmaya devam eder ancak istenmeyen posta olarak işaretlenir ve reddedılmaz. İstenirse, kullanıcılar bu iletileri şu yöntemlerle gelen kutularına almaya devam edebilir:

- Kullanıcılar, e-posta istemcilerini kullanarak güvenilir gönderenleri tek tek ekler.

- Yöneticiler kimlik sahtekarlığına sahip gönderenden gelen iletilere izin vermek için kimlik [sahtekarlığına ilişkin bilgi sahtekarlık içgörülerini](learn-about-spoof-intelligence.md) veya [Kiracı İzin Ver/Engelle Listesi'ni](tenant-allow-block-list.md) kullanabilir.

- Yöneticiler, söz konusu gönderenler için iletilere izin veren tüm kullanıcılar için bir Exchange posta akışı kuralı (aktarım kuralı olarak da bilinir) oluşturur.

Daha fazla bilgi için bkz. [Güvenilir gönderen listeleri oluşturma](create-safe-sender-lists-in-office-365.md).

## <a name="how-microsoft-365-utilizes-authenticated-received-chain-arc"></a>Microsoft 365, Kimliği Doğrulanmış Alınan Zincir'i (ARC) nasıl kullanır?

Microsoft 365'te barındırılan tüm posta kutuları artık iletilerin daha iyi teslim edilebilirliği ve gelişmiş kimlik sahtekarlığı önleme koruması ile ARC'ın avantajından yararlanacak. ARC, bir e-posta kaynak sunucudan alıcı posta kutusuna yönlendirildiğinde tüm katılan aracıların veya atlamaların e-posta kimlik doğrulama sonuçlarını korur. ARC'ın öncesinde, iletme kuralları veya otomatik imzalar gibi e-posta yönlendirmedeki aracılar tarafından gerçekleştirilen değişiklikler, e-posta alıcı posta kutusuna ulaştığında DMARC hatalarına neden olabilir. ARC ile kimlik doğrulama sonuçlarının şifrelemeyle korunması, Microsoft 365'in e-postayı gönderenin orijinalliğini doğrulamasını sağlar.

Microsoft 365 şu anda ARC Sealer olduğunda kimlik doğrulama sonuçlarını doğrulamak için ARC kullanıyor ancak gelecekte üçüncü taraf ARC sızdırmazları için destek eklemeyi planlıyor.

## <a name="troubleshooting-your-dmarc-implementation"></a>DMARC uygulamanızın sorunlarını giderme

EOP'nin ilk giriş olmadığı durumlarda etki alanınızın MX kayıtlarını yapılandırdıysanız, etki alanınız için DMARC hataları uygulanmaz.

Müşteriyseniz ve etki alanınızın birincil MX kaydı EOP'yi göstermiyorsa DMARC'nin avantajlarından yararlanamazsınız. Örneğin, MX kaydını şirket içi posta sunucunuza yönlendirir ve ardından bağlayıcı kullanarak e-postayı EOP'ye yönlendirirseniz DMARC çalışmaz. Bu senaryoda, alıcı etki alanı Accepted-Domains biridir ancak EOP birincil MX değildir. Örneğin, contoso.com MX'in kendisine işaret edip ikincil MX kaydı olarak EOP kullandığını varsayalım; contoso.com'un MX kaydı aşağıdaki gibi görünür:

```console
contoso.com     3600   IN  MX  0  mail.contoso.com
contoso.com     3600   IN  MX  10 contoso-com.mail.protection.outlook.com
```

Birincil MX olduğundan, e-postaların tümü veya çoğu önce mail.contoso.com yönlendirilir ve ardından posta EOP'ye yönlendirilir. Bazı durumlarda, EOP'yi MX kaydı olarak listelemeyebilir ve e-postanızı yönlendirmek için bağlayıcıları bağlamanız yeterlidir. DMARC doğrulamasının yapılması için EOP'nin ilk giriş olması gerekmez. Tüm şirket içi/O365 dışı sunucuların DMARC denetimleri yapacağından emin olmak için doğrulamayı güvence altına alır.  DMARC TXT kaydını ayarladığınızda DMARC, bir müşterinin etki alanı (sunucu değil) için zorunlu tutulmaya uygundur, ancak uygulamayı gerçekten yapmak alıcı sunucuya aittir.  EOP'yi alıcı sunucu olarak ayarlarsanız EOP, DMARC zorlamasını yapar.

:::image type="content" source="../../media/Tp_DMARCTroublehoot.png" alt-text="DMARC için sorun giderme grafiği" lightbox="../../media/Tp_DMARCTroublehoot.png":::

## <a name="for-more-information"></a>Daha fazla bilgi için

DMARC hakkında daha fazla bilgi mi istiyorsunuz? Bu kaynaklar yardımcı olabilir.

- [İstenmeyen postadan koruma iletisi üst bilgileri](anti-spam-message-headers.md) , DMARC denetimleri için Microsoft 365 tarafından kullanılan söz dizimi ve üst bilgi alanlarını içerir.

- M<sup>3</sup>AAWG'den (Microsoft Mesajlaşma, Kötü Amaçlı Yazılım, Mobil Kötü Amaçlı Yazılımdan Koruma Çalışma Grubu) [DMARC Eğitim Serisi'ni](https://www.m3aawg.org/activities/training/dmarc-training-series) alın.

- [Dmarcian'daki](https://space.dmarcian.com/deployment/) denetim listesini kullanın.

- [Doğrudan DMARC.org'daki](https://dmarc.org) kaynağa gidin.

## <a name="see-also"></a>Ayrıca bkz.

[Microsoft 365, kimlik sahtekarlıklarını önlemek için Sender Policy Framework'i (SPF) nasıl kullanır?](how-office-365-uses-spf-to-prevent-spoofing.md)

[**Sahtekarlık önlemeye yardımcı olmak için Microsoft 365'te SPF'yi ayarlama**](set-up-spf-in-office-365-to-help-prevent-spoofing.md)

[**Microsoft 365'te özel etki alanınızdan gönderilen giden e-postayı doğrulamak için DKIM kullanma**](use-dkim-to-validate-outbound-email.md)

[Güvenilir ARC Gönderenleri'ni geçerli posta akışları için kullanma](/microsoft-365/security/office-365-security/use-arc-exceptions-to-mark-trusted-arc-senders?view=o365-21vianet&branch=tracyp_emailauth)
