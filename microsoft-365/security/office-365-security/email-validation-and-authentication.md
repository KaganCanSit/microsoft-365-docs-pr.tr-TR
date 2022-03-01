---
title: E-posta kimlik doğrulaması Microsoft 365
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: conceptual
search.appverid:
- MET150
ms.assetid: ''
ms.collection:
- M365-security-compliance
- Strat_O365_IP
ms.custom: TopSMBIssues
ms.localizationpriority: high
description: Yöneticiler kimlik avı, kimlik avı ve istenmeyen postayı önlemeye yardımcı olmak için EOP'nin e-posta kimlik doğrulamasını (SPF, DKIM ve DMARC) nasıl kullandığını öğrenebilir.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: c0e7bc2ddd620b454979418735fb6982b71501c3
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2022
ms.locfileid: "63021752"
---
# <a name="email-authentication-in-eop"></a>EOP'de e-posta kimlik doğrulaması

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Geçerli olduğu yer:**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [1. plan Office 365 plan 2 için Microsoft Defender](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)


E-posta kimlik doğrulaması (e-posta doğrulaması olarak da bilinir), kimlik sahtelerini (sahte gönderenlerden gelen e-posta iletileri) engellemeye çalışan bir grup standarttır. EOP, Microsoft 365 e-postayı doğrulamak için aşağıdaki standartları kullanır:

- [SPF](set-up-spf-in-office-365-to-help-prevent-spoofing.md)
- [DKIM](use-dkim-to-validate-outbound-email.md)
- [DMARC](use-dmarc-to-validate-email.md)

E-posta kimlik doğrulaması, gönderenden gelen e-posta iletilerinin (örneğin, laura@contoso.com) geçerli olduğunu ve bu e-posta etki alanının beklenen kaynaklarından (örneğin, contoso.com.)

Bu makalenin kalan bölümü bu teknolojilerin nasıl çalışır ve EOP'nin gelen e-postayı kontrol etmek için bunları nasıl kullandığını açıklar.

## <a name="use-email-authentication-to-help-prevent-spoofing"></a>Kimlik doğrulamasının önlenmesine yardımcı olmak için e-posta kimlik doğrulamasını kullanma

DMARC, iletilerde Yer alan From adresini inceleerek **, düzeçlemi** önlemeye yardımcı olur. Gönderen **adresi** , kullanıcıların e-posta istemcisinde göreceği gönderenin e-posta adresidir. Hedef e-posta kuruluşları da e-posta etki alanının SPF veya DKIM'yi geçir olduğunu doğrular. Başka bir deyişle, etki alanının kimliği doğrulanmış ve dolayısıyla gönderenin e-posta adresi kimlik doğrulamasılanmamıştır.

Bununla birlikte, SPF, DKIM ve DMARC için DNS kayıtları (toplu olarak e-posta kimlik doğrulaması ilkeleri olarak bilinir) isteğe bağlıdır. E-posta kimlik doğrulaması ilkeleri güçlü microsoft.com etki skype.com kimlik doğrulamasından korunur. Ancak, zayıf e-posta kimlik doğrulama ilkelerine sahip veya hiç ilkesi yok olan etki alanları, kimlik doğrulamasının en önemli hedefleridir.

Mart 2018'den sonra Fortune 500'de yer alan şirketlerin etki alanlarının yalnızca %9'si güçlü e-posta kimlik doğrulama ilkeleri yayımlar. Şirketlerin geri kalan %91'i bir saldırgan tarafından yanlış ifade edebiliyor. Başka bir e-posta filtreleme mekanizması yerinde değilse, bu etki alanlarındaki kimliği doğru olmayan gönderenlerden gelen e-posta kullanıcılara teslim edilir.

![Fortune 500 şirketlerin DMARC ilkeleri.](../../media/84e77d34-2073-4a8e-9f39-f109b32d06df.jpg)

Güçlü e-posta kimlik doğrulama ilkeleri yayımlayan küçük ve orta ölçekli şirketlerin oranı daha küçüktür. Kuzey Amerika ve batı Avrupa dışındaki e-posta etki alanları için de bu sayı daha küçüktür.

Güçlü e-posta kimlik doğrulama ilkelerinin olmaması büyük bir sorundur. Kuruluşlar e-posta kimlik doğrulamasının nasıl çalıştığını anlamasa da, saldırganlar tam olarak anlar ve avantajdan faydalanlar. Kimlik avı kaygıları ve güçlü e-posta kimlik doğrulama ilkelerinin sınırlı benimsenmesi  nedeniyle, Microsoft gelen e-postaları kontrol etmek için örtülü e-posta kimlik doğrulaması kullanır.

Örtülü e-posta kimlik doğrulaması, normal e-posta kimlik doğrulama ilkelerinin bir uzantısıdır. Bu uzantılar şunları içerir: gönderen itibarı, gönderen geçmişi, alıcı geçmişi, davranış çözümlemesi ve diğer gelişmiş teknikler. Bu uzantılardan gelen başka sinyaller olmaması durumuyla, e-posta kimlik doğrulama ilkelerini kullanmayan etki alanlarından gönderilen iletiler kimlik doğrulaması olarak işaretlenir.

Microsoft'un genel duyurularını görmek için bkz. Kimlik Avı Bölümü 2 - Kimlik AvıNda İyileştirilmiş [Kimlik Microsoft 365](https://techcommunity.microsoft.com/t5/Security-Privacy-and-Compliance/Schooling-A-Sea-of-Phish-Part-2-Enhanced-Anti-spoofing/ba-p/176209).

## <a name="composite-authentication"></a>Bileşik kimlik doğrulaması

Etki alanının geleneksel SPF, DKIM ve DMARC kayıtları yoksa, bu kayıt denetimleri yeterli kimlik doğrulama durumu bilgilerini iletmiyor. Bu nedenle, Microsoft örtülü e-posta kimlik doğrulaması için bir algoritma geliştirdi. Bu algoritma, birden çok sinyali bileşik kimlik doğrulaması adı verilen veya kısa süreli _olarak_ tek bir değerde `compauth` birleştirir. Değer `compauth` , ileti üst **bilgisinde Kimlik Doğrulama Sonuçları** üst bilgisine damgalanır.

```text
Authentication-Results:
   compauth=<fail | pass | softpass | none> reason=<yyy>
```

Bu değerler, Kimlik doğrulama [sonuçları ileti üst bilgisinde açıklanmıştır](anti-spam-message-headers.md#authentication-results-message-header).

Yöneticiler ve hatta son kullanıcılar ileti üst bilgilerini inceerek gönderenin nasıl Microsoft 365 olduğunu nasıl belirleyecek.

## <a name="why-email-authentication-is-not-always-enough-to-stop-spoofing"></a>Neden e-posta kimlik doğrulaması kimlik doğrulamayı durdurmak için her zaman yeterli değildir?

Gelen iletinin kimlik doğrulamasının doğru olup olmadığını belirlemek için yalnızca e-posta kimlik doğrulama kayıtlarına güvenmek üzere aşağıdaki sınırlamalara sahiptir:

- Gönderen etki alanı gerekli DNS kayıtlarını eksik olabilir veya kayıtlar yanlış yapılandırılmış olabilir.

- Kaynak etki alanı DNS kayıtlarını doğru yapılandırmış ancak bu etki alanı, Kaynak adresli etki alanıyla eşleşmez. SPF ve DKIM, Etki alanının From adresi içinde kullanılmaktadır. Saldırganlar veya yasal hizmetler etki alanını kaydedebiliyor, etki alanı için SPF ve DKIM yapılandırıyor ve Kaynak adreste tamamen farklı bir etki alanı kullanıyor olabilir. Bu etki alanındaki gönderenlerden gelen iletiler SPF ve DKIM'yi geçecektir.

Bileşik kimlik doğrulaması, aksi halde e-posta kimlik doğrulaması denetimlerini geçerek bu sınırlamalara neden olabilir.

Basitlik açısından, aşağıdaki örnekler e-posta kimlik doğrulama sonuçlarına odaklanarak devam ediyor. Diğer arka uç zekası etmenleri e-posta kimlik doğrulamasını kimlik doğrulaması olarak geçen iletileri veya kimlik doğrulaması yasal olarak başarısız olan iletileri tanımlayabilir.

Örneğin, etki fabrikam.com SPF, DKIM veya DMARC kaydı yoktur. Etki alanındaki gönderenlerden gelen fabrikam.com bileşik kimlik doğrulaması başarısız olabilir (değer ve nedenini `compauth` not edin):

```text
Authentication-Results: spf=none (sender IP is 10.2.3.4)
  smtp.mailfrom=fabrikam.com; contoso.com; dkim=none
  (message not signed) header.d=none; contoso.com; dmarc=none
  action=none header.from=fabrikam.com; compauth=fail reason=001
From: chris@fabrikam.com
To: michelle@contoso.com
```

BIRDEN fabrikam.com DKIM kaydı olmayan bir SPF yapılandırıyorsa, ileti bileşik kimlik doğrulamayı geçecektir. SPF denetimlerini geçen etki alanı, İlk adreste yer alan etki alanıyla hizalanır:

```text
Authentication-Results: spf=pass (sender IP is 10.2.3.4)
  smtp.mailfrom=fabrikam.com; contoso.com; dkim=none
  (message not signed) header.d=none; contoso.com; dmarc=bestguesspass
  action=none header.from=fabrikam.com; compauth=pass reason=109
From: chris@fabrikam.com
To: michelle@contoso.com
```

SPF fabrikam.com olmayan bir DKIM kaydı yapılandırıyorsa, ileti bileşik kimlik doğrulamayı geçecektir. DKIM imzası içinde yer alan etki alanı, From adresine göre etki alanıyla hizalanır:

```text
Authentication-Results: spf=none (sender IP is 10.2.3.4)
  smtp.mailfrom=fabrikam.com; contoso.com; dkim=pass
  (signature was verified) header.d=outbound.fabrikam.com;
  contoso.com; dmarc=bestguesspass action=none
  header.from=fabrikam.com; compauth=pass reason=109
From: chris@fabrikam.com
To: michelle@contoso.com
```

SPF veya DKIM imzası'daki etki alanı, From adresi'deki etki alanıyla hizalanmamışsa, ileti bileşik kimlik doğrulaması başarısız olabilir:

```text
Authentication-Results: spf=none (sender IP is 192.168.1.8)
  smtp.mailfrom=maliciousdomain.com; contoso.com; dkim=pass
  (signature was verified) header.d=maliciousdomain.com;
  contoso.com; dmarc=none action=none header.from=contoso.com;
  compauth=fail reason=001
From: chris@contoso.com
To: michelle@fabrikam.com
```

## <a name="solutions-for-legitimate-senders-who-are-sending-unauthenticated-email"></a>Kimliği doğrulanmamış e-posta gönderen geçerli gönderenler için çözümler

Microsoft 365, kimlerin kimliği doğrulanmamış e-postayı kuruluşa gönderdiğini takip eder. Hizmet, gönderenin yasal olmadığını düşünüyorsa, bu gönderenden gelen iletileri bileşik kimlik doğrulama hatası olarak işaretlemektedir. Bu karara engel olmak için bu bölümdeki önerileri kullanabilirsiniz.

### <a name="configure-email-authentication-for-domains-you-own"></a>Sahip olduğunuz etki alanları için e-posta kimlik doğrulamasını yapılandırma

Birden çok kiracıya sahip olduğunuz veya kiracılarla etkileşim kurduğunız durumlarda, bu yöntemi kullanarak kuruluş içi kimlik doğrulamayı ve etki alanı çapraz kimlik doğrulamalarını çözebilirsiniz. Ayrıca, iş yeriz veya başka sağlayıcılar tarafından barındırılan diğer müşterilere veya üçüncü taraflara Microsoft 365 etki alanı adları arasında yapılan ve nerede olduğunu çözümlemeye yardımcı olur.

- [Etki alanlarınız için SPF](set-up-spf-in-office-365-to-help-prevent-spoofing.md) kayıtlarını yapılandırma.
- [Birincil etki alanlarınız için DKIM](use-dkim-to-validate-outbound-email.md) kayıtlarını yapılandırma.
- [Geçerli gönderenlerinizi belirlemek üzere etki alanınız için DMARC](use-dmarc-to-validate-email.md) kayıtlarını ayarlamayı düşünebilirsiniz.

Microsoft, SPF, DKIM ve DMARC kayıtları için ayrıntılı uygulama yönergeleri sağlamaz. Bununla birlikte, çevrimiçi olarak birçok bilgi edinebilirsiniz. Ayrıca, kuruluşun e-posta kimlik doğrulama kayıtlarını ayarlamalarına yardımcı olmak için ayrılmış üçüncü taraf şirketler de yer alır.

#### <a name="you-dont-know-all-sources-for-your-email"></a>E-postanız için tüm kaynakları bilmiyorsanız

Birçok etki alanı SPF kayıtlarını yayımlamaz, çünkü etki alanlarındaki iletilerin tüm e-posta kaynaklarını bilmiyor. Hakkında bilginiz olan tüm e-posta kaynaklarını içeren bir SPF kaydı yayımlayın (özellikle şirket trafiğinizin bulunduğu yerde) ve nötr SPF ilkesi yayımlayın `?all`. Örneğin:

```text
fabrikam.com IN TXT "v=spf1 include:spf.fabrikam.com ?all"
```

Bu örnek, şirket altyapınıza gelen e-postanın e-posta kimlik doğrulamasını geçeceği, ancak bilinmeyen kaynaklardan gelen e-postanın belirsiz olduğu anlamına gelir.

Microsoft 365, şirket altyapıdan gelen e-postayı kimliği doğrulanmış olarak kabul eder. Tanımlanamayan kaynaklardan gelen e-posta, örtülü kimlik doğrulamayı başarısız olursa kimliksiz olarak işaretlenir. Bununla birlikte, bu durum tüm e-postanın e-posta tarafından varsayılan adres olarak işaretlenirken Microsoft 365.

'ın SPF `?all`geri dönüş ilkesiyle çalışmaya başladıktan sonra, iletileriniz için daha fazla e-posta kaynağı bulmak ve eklemek için aşamalı olarak spf kaydınızı daha sıkı bir ilkeyle güncelleştirebilirsiniz.

### <a name="configure-permitted-senders-of-unauthenticated-email"></a>Kimliği doğrulanmamış e-postaların izin verilen gönderenlerini yapılandırma

Ayrıca, gönderenlerin kimliği [doğrulanmamış iletileri](learn-about-spoof-intelligence.md) kuruluşa iletmesine izin vermek için kimliksiz kimlik doğrulaması içgörü ve Kiracı İzinLeri [/](tenant-allow-block-list.md) Engelleme Listesi'ne de izin veebilirsiniz.

Dış etki alanları için kimlik doğrulu kullanıcı Kaynak adresi'nin etki alanıdır; bu sırada gönderme altyapısı kaynak IP adresidir (/24 CIDR aralıklarına ayrılmıştır) veya ters DNS (PTR) kaydının kuruluş etki alanıdır.

### <a name="create-an-allow-entry-for-the-senderrecipient-pair"></a>Gönderen/alıcı çifti için izin girdisi oluşturma

İstenmeyen posta filtrelemesini atlamak, kimlik avı için filtrelemenin bazı bölümleri (ancak belirli gönderenler için kötü amaçlı yazılım filtrelemesi) atlamak için bkz. Kimlik avı için [Microsoft 365.](create-safe-sender-lists-in-office-365.md)

### <a name="ask-the-sender-to-configure-email-authentication-for-domains-you-dont-own"></a>Gönderenden, sahip olmadığınız etki alanları için e-posta kimlik doğrulamasını yapılandırmasını isteme

İstenmeyen posta ve kimlik avı sorunu nedeniyle, Microsoft tüm e-posta kuruluşları için e-posta kimlik doğrulaması önerir. Kurumda elle geçersiz kılmaları yapılandırmak yerine, gönderen etki alanındaki bir yöneticiden e-posta kimlik doğrulama kayıtlarını yapılandırmasını istemeniz gerekir.

- Geçmişte e-posta kimlik doğrulama kayıtlarını yayımlamaları gerekmasa da, Microsoft'a e-posta gönderirken bu kayıtları yayımlamaları gerekir.

- Etki alanının gönderen IP adreslerini yayımlayacak şekilde SPF'yi ayarlayın ve iletileri dijital olarak imzalamak için DKIM (varsa) ayarlayın. DMARC kayıtlarını ayarlamayı da göz önünde bulunduracaklarını düşünebilirsiniz.

- Toplu gönderenleri kendi adına e-posta göndermek için kullanırsa, Kaynak adreste yer alan etki alanının (onlara aitse) SPF veya DMARC'dan geçen etki alanıyla uyumlu olduğunu doğrulayın.

- SPF kaydına şu konumların dahil olduğunu (kullanıyorsa) doğrulayın:

  - Şirket içi e-posta sunucuları.
  - Hizmet olarak yazılım sağlayıcısından (SaaS) gönderilen e-posta.
  - Bulut barındırma hizmetlerinden (Microsoft Azure, GoDaddy, Raf Al, Amazon Web Hizmetleri vb.) gönderilen e-posta.

- ISS tarafından barındırılan küçük etki alanları için SPF kaydını ISS'deki yönergelere göre yapılandırabilirsiniz.

İlk başta etki alanlarını kimlik doğrulamasına göndermek zor olsa da, zamanla, daha fazla e-posta filtresi gereksiz postaya, hatta e-postalarını reddetmeye başlarken, daha iyi teslim sağlamak için doğru kayıtları ayarlamalarına neden olur. Ayrıca, katılımları kimlik avına karşı mücadeleye yardımcı olabilir ve kuruluşunda veya e-posta göndermekte olduğu kuruluşlarda kimlik avı olasılığını düşürebilirsiniz.

#### <a name="information-for-infrastructure-providers-isps-esps-or-cloud-hosting-services"></a>Altyapı sağlayıcıları (ISS'ler, ESP'ler veya bulut barındırma hizmetleri) için bilgiler

Etki alanının e-postalarını barındır ediyorsanız veya e-posta gönderen bir barındırma altyapısı sağlarsanız, aşağıdaki adımları gerçekleştirin:

- Müşterilerinize, müşterilerin SPF kayıtlarını nasıl yapılandırmaları gerektiğini açıklayan belgelere sahip olduğundan emin olmak

- Müşteri bunu açıkça ayarlamasa bile, giden e-postada DKIM imzaları imzalamayı göz önünde bulundurabilirsiniz (varsayılan etki alanıyla oturum açma). Hatta e-postayı DKIM imzaları ile çift imza atabilirsiniz (e-postayı ayarlasa müşterinin etki alanıyla bir kez ve bir kez de şirketin DKIM imzasıyla)

Platformdan kaynaklanan e-postanın kimliğini doğrulasanız bile Microsoft'a teslim edilebilirlik garanti değildir, ancak en azından kimliği doğrulanmamış olduğundan Microsoft'un e-postanızı gereksiz olarak göndermesini sağlamaz.

## <a name="related-links"></a>İlgili bağlantılar

Hizmet sağlayıcılarının en iyi yöntemleri hakkında daha fazla bilgi için bkz. [Hizmet Sağlayıcıları için En İyi M3AAWG Mobil Mesajlaşma Yöntemleri](https://www.m3aawg.org/sites/default/files/m3aawg-mobile-messaging-best-practices-service-providers-2015-08_0.pdf).

SPF'nin Office 365 DKIM doğrulamasını nasıl desteklediğini öğrenin:

- [SPF hakkında daha fazla bilgi](how-office-365-uses-spf-to-prevent-spoofing.md)

- [DKIM hakkında daha fazla bilgi](support-for-validation-of-dkim-signed-messages.md)
