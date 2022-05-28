---
title: Microsoft 365'de e-posta kimlik doğrulaması
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
description: Yöneticiler, kimlik sahtekarlığı, kimlik avı ve istenmeyen postaları önlemeye yardımcı olmak için EOP'nin e-posta kimlik doğrulamasını (SPF, DKIM ve DMARC) nasıl kullandığını öğrenebilir.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 2b0a1f1bec76a8dd22bc04502ea7ca09f2c7af66
ms.sourcegitcommit: 38a18b0195d99222c2c6da0c80838d24b5f66b97
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/28/2022
ms.locfileid: "65772784"
---
# <a name="email-authentication-in-eop"></a>EOP'de e-posta kimlik doğrulaması

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Uygulandığı öğe**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Office 365 için Microsoft Defender plan 1 ve plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

E-posta kimlik doğrulaması (e-posta doğrulaması olarak da bilinir), kimlik sahtekarlığına son vermeye çalışan bir standartlar grubudur (sahte gönderenlerden gelen e-posta iletileri). Tüm Microsoft 365 kuruluşlarda EOP, gelen e-postayı doğrulamak için şu standartları kullanır:

- [SPF](set-up-spf-in-office-365-to-help-prevent-spoofing.md)
- [DKIM](use-dkim-to-validate-outbound-email.md)
- [DMARC](use-dmarc-to-validate-email.md)

E-posta kimlik doğrulaması, gönderenden gelen e-posta iletilerinin (örneğin, laura@contoso.com) geçerli olduğunu ve bu e-posta etki alanı için beklenen kaynaklardan (örneğin, contoso.com) geldiğini doğrular.

Bu makalenin geri kalanında bu teknolojilerin nasıl çalıştığı ve EOP'nin gelen e-postayı denetlemek için bunları nasıl kullandığı açıklanmaktadır.

## <a name="use-email-authentication-to-help-prevent-spoofing"></a>Kimlik sahtekarlıklarını önlemeye yardımcı olmak için e-posta kimlik doğrulamasını kullanma

DMARC, iletilerde **Kimden** adresini inceleyerek kimlik sahtekarlığına engel olur. **Kimden** adresi, kullanıcıların e-posta istemcilerinde gördüğü gönderenin e-posta adresidir. Hedef e-posta kuruluşları, e-posta etki alanının SPF veya DKIM'yi geçtiğini de doğrulayabilir. Başka bir deyişle, etki alanının kimliği doğrulanmıştır ve bu nedenle gönderenin e-posta adresi sahte değildir.

Ancak SPF, DKIM ve DMARC (toplu olarak e-posta kimlik doğrulama ilkeleri olarak bilinir) için DNS kayıtları isteğe bağlıdır. microsoft.com ve skype.com gibi güçlü e-posta kimlik doğrulama ilkelerine sahip etki alanları kimlik sahtekarlığına karşı korunur. Ancak, daha zayıf e-posta kimlik doğrulama ilkelerine sahip olan veya hiç ilke içermeyen etki alanları sahte kimlik sahtekarlığı için temel hedeflerdir.

Mart 2018 itibarıyla Fortune 500'deki şirketlerin etki alanlarının yalnızca %9'u güçlü e-posta kimlik doğrulama ilkeleri yayımlar. Şirketlerin kalan %91'i bir saldırgan tarafından sahte olabilir. Başka bir e-posta filtreleme mekanizması yerinde değilse, bu etki alanlarındaki sahte gönderenlerden gelen e-postalar kullanıcılara teslim edilebilir.

![Fortune 500 şirketlerinin DMARC ilkeleri.](../../media/84e77d34-2073-4a8e-9f39-f109b32d06df.jpg)

Güçlü e-posta kimlik doğrulama ilkeleri yayımlayan küçük ve orta ölçekli şirketlerin oranı daha küçüktür. Ayrıca Kuzey Amerika ve batı Avrupa dışındaki e-posta etki alanları için sayı daha da küçüktür.

Güçlü e-posta kimlik doğrulama ilkelerinin olmaması büyük bir sorundur. Kuruluşlar e-posta kimlik doğrulamasının nasıl çalıştığını anlamayabilir, ancak saldırganlar tam olarak anlar ve bundan yararlanırlar. Kimlik avı endişeleri ve güçlü e-posta kimlik doğrulama ilkelerinin sınırlı benimsenmesi nedeniyle, Microsoft gelen *e-postayı denetlemek için örtük e-posta kimlik doğrulamasını* kullanır.

Örtük e-posta kimlik doğrulaması, normal e-posta kimlik doğrulama ilkelerinin bir uzantısıdır. Bu uzantılar şunlardır: gönderenin itibarı, gönderen geçmişi, alıcı geçmişi, davranış analizi ve diğer gelişmiş teknikler. Bu uzantılardan gelen diğer sinyallerin olmaması durumunda, e-posta kimlik doğrulama ilkelerini kullanmayan etki alanlarından gönderilen iletiler sahte olarak işaretlenir.

Microsoft'un genel duyurusunu görmek için bkz. [A Sea of Phish Part 2 - Enhanced Anti-spoofing in Microsoft 365](https://techcommunity.microsoft.com/t5/Security-Privacy-and-Compliance/Schooling-A-Sea-of-Phish-Part-2-Enhanced-Anti-spoofing/ba-p/176209).

## <a name="composite-authentication"></a>Bileşik kimlik doğrulaması

Bir etki alanında geleneksel SPF, DKIM ve DMARC kayıtları yoksa, bu kayıt denetimleri yeterli kimlik doğrulama durumu bilgilerini iletmez. Bu nedenle, Microsoft örtük e-posta kimlik doğrulaması için bir algoritma geliştirmiştir. Bu algoritma, birden çok sinyali _bileşik kimlik doğrulaması_ adı verilen tek bir değerde veya `compauth` kısaca birleştirir. Değer, `compauth` ileti üst bilgilerinde **Authentication-Results** üst bilgisine damgalanır.

```text
Authentication-Results:
   compauth=<fail | pass | softpass | none> reason=<yyy>
```

Bu değerler [Kimlik doğrulama sonuçları ileti üst bilgisinde](anti-spam-message-headers.md#authentication-results-message-header) açıklanmıştır.

yöneticiler ve hatta son kullanıcılar ileti üst bilgilerini inceleyerek Microsoft 365 gönderenin sahte olduğunu nasıl saptadığını belirleyebilir.

## <a name="why-email-authentication-is-not-always-enough-to-stop-spoofing"></a>E-posta kimlik doğrulaması neden sahtekarlık yapmayı durdurmak için her zaman yeterli değildir?

Gelen bir iletinin sahte olup olmadığını belirlemek için yalnızca e-posta kimlik doğrulama kayıtlarına güvenmek aşağıdaki sınırlamalara sahiptir:

- Gönderen etki alanında gerekli DNS kayıtları eksik olabilir veya kayıtlar yanlış yapılandırılmış olabilir.

- Kaynak etki alanı DNS kayıtlarını doğru yapılandırdı, ancak bu etki alanı Kimden adresindeki etki alanıyla eşleşmiyor. SPF ve DKIM, etki alanının Kimden adresinde kullanılmasını gerektirmez. Saldırganlar veya meşru hizmetler bir etki alanı kaydedebilir, etki alanı için SPF ve DKIM yapılandırabilir ve Kimden adresinde tamamen farklı bir etki alanı kullanabilir. Bu etki alanındaki gönderenlerden gelen iletiler SPF ve DKIM'den geçer.

Bileşik kimlik doğrulaması, aksi takdirde e-posta kimlik doğrulaması denetimlerinde başarısız olacak iletiler geçirerek bu sınırlamaları giderebilir.

Kolaylık olması için aşağıdaki örnekler e-posta kimlik doğrulaması sonuçlarına odaklanır. Diğer arka uç zekası faktörleri, e-posta kimlik doğrulamasını sahte olarak geçiren iletileri veya e-posta kimlik doğrulamasında başarısız olan iletileri meşru olarak tanımlayabilir.

Örneğin, fabrikam.com etki alanının SPF, DKIM veya DMARC kaydı yoktur. fabrikam.com etki alanındaki gönderenlerden gelen iletiler bileşik kimlik doğrulamasında başarısız olabilir (değeri ve nedeni not edin `compauth` ):

```text
Authentication-Results: spf=none (sender IP is 10.2.3.4)
  smtp.mailfrom=fabrikam.com; contoso.com; dkim=none
  (message not signed) header.d=none; contoso.com; dmarc=none
  action=none header.from=fabrikam.com; compauth=fail reason=001
From: chris@fabrikam.com
To: michelle@contoso.com
```

fabrikam.com bir SPF'yi DKIM kaydı olmadan yapılandırırsa, ileti bileşik kimlik doğrulamasını geçirebilir. SPF denetimlerini geçen etki alanı, Kimden adresindeki etki alanıyla hizalanır:

```text
Authentication-Results: spf=pass (sender IP is 10.2.3.4)
  smtp.mailfrom=fabrikam.com; contoso.com; dkim=none
  (message not signed) header.d=none; contoso.com; dmarc=bestguesspass
  action=none header.from=fabrikam.com; compauth=pass reason=109
From: chris@fabrikam.com
To: michelle@contoso.com
```

fabrikam.com SPF kaydı olmayan bir DKIM kaydı yapılandırırsa, ileti bileşik kimlik doğrulamasını geçirebilir. DKIM imzasında etki alanı, Kimden adresindeki etki alanıyla hizalanır:

```text
Authentication-Results: spf=none (sender IP is 10.2.3.4)
  smtp.mailfrom=fabrikam.com; contoso.com; dkim=pass
  (signature was verified) header.d=outbound.fabrikam.com;
  contoso.com; dmarc=bestguesspass action=none
  header.from=fabrikam.com; compauth=pass reason=109
From: chris@fabrikam.com
To: michelle@contoso.com
```

SPF'deki etki alanı veya DKIM imzası Kimden adresindeki etki alanıyla uyumlu değilse, ileti bileşik kimlik doğrulamasında başarısız olabilir:

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

Microsoft 365 kuruluşunuza kimlerin kimliği doğrulanmamış e-posta gönderdiğini izler. Hizmet, gönderenin meşru olmadığını düşünüyorsa, bu gönderenden gelen iletileri bileşik kimlik doğrulama hatası olarak işaretler. Bu kararı önlemek için bu bölümdeki önerileri kullanabilirsiniz.

### <a name="configure-email-authentication-for-domains-you-own"></a>Sahip olduğunuz etki alanları için e-posta kimlik doğrulamasını yapılandırma

Birden çok kiracıya sahip olduğunuz veya kiracılarla etkileşimde olduğunuz durumlarda kuruluş içi kimlik sahtekarlığına ve etki alanları arası kimlik sahtekarlığına çözüm getirmek için bu yöntemi kullanabilirsiniz. Ayrıca, Microsoft 365 veya diğer sağlayıcılar tarafından barındırılan üçüncü taraflardaki diğer müşterilere gönderdiğiniz etki alanları arası kimlik sahtekarlıklarının çözülmesine yardımcı olur.

- Etki alanlarınız için [SPF kayıtlarını yapılandırın](set-up-spf-in-office-365-to-help-prevent-spoofing.md).
- Birincil etki alanlarınız için [DKIM kayıtlarını yapılandırın](use-dkim-to-validate-outbound-email.md).
- Geçerli gönderenlerinizi belirlemek için etki alanınız için [DMARC kayıtlarını ayarlamayı göz önünde bulundurun](use-dmarc-to-validate-email.md).

Microsoft SPF, DKIM ve DMARC kayıtları için ayrıntılı uygulama yönergeleri sağlamaz. Ancak, çevrimiçi ortamda birçok bilgi sağlanır. Ayrıca kuruluşunuzun e-posta kimlik doğrulama kayıtlarını ayarlamasına yardımcı olmak için ayrılmış üçüncü taraf şirketler de vardır.

#### <a name="you-dont-know-all-sources-for-your-email"></a>E-postanızın tüm kaynaklarını bilmiyorsunuz

Birçok etki alanı, etki alanlarındaki iletilerin tüm e-posta kaynaklarını bilmediğinden SPF kayıtlarını yayımlamaz. Bildiğiniz tüm e-posta kaynaklarını içeren bir SPF kaydı yayımlayarak (özellikle şirket trafiğinizin bulunduğu yerde) ve nötr SPF ilkesini `?all`yayımlayarak başlayın. Örneğin:

```text
fabrikam.com IN TXT "v=spf1 include:spf.fabrikam.com ?all"
```

Bu örnek, kurumsal altyapınızdan gelen e-postanın e-posta kimlik doğrulamasını geçireceği, ancak bilinmeyen kaynaklardan gelen e-postaların etkisiz hale getirileceği anlamına gelir.

Microsoft 365, kurumsal altyapınızdan gelen e-postaları kimliği doğrulanmış olarak kabul eder. Kimliği belirlenemeyen kaynaklardan gelen e-postalar, örtük kimlik doğrulaması başarısız olursa kimlik sahtekarı olarak işaretlenebilir. Ancak bu, Microsoft 365 tarafından sahte olarak işaretlenen tüm e-postalardan hala bir gelişmedir.

spf geri dönüş ilkesini `?all`kullanmaya başladıktan sonra iletileriniz için daha fazla e-posta kaynağını aşamalı olarak bulabilir ve ekleyebilir ve ardından SPF kaydınızı daha katı bir ilkeyle güncelleştirebilirsiniz.

### <a name="configure-permitted-senders-of-unauthenticated-email"></a>Kimliği doğrulanmamış e-postanın izin verilen gönderenlerini yapılandırma

Ayrıca, gönderenlerin kuruluşunuza kimliği doğrulanmamış iletiler iletmesine izin vermek için kimlik sahtekarlık [bilgileri içgörülerini](learn-about-spoof-intelligence.md) ve [Kiracı İzin Ver/Engelle Listesi'ni](tenant-allow-block-list.md) de kullanabilirsiniz.

Dış etki alanları için kimlik sahtekarlığına sahip kullanıcı Kimden adresindeki etki alanıdır, gönderen altyapı ise aşağıdaki değerlerden biridir:

- Kaynak IP adresi (/24 CIDR aralığına ayrılmıştır)
- Ters DNS (PTR) kaydının kuruluş etki alanı.
- Doğrulanmış bir DKIM etki alanı.

### <a name="create-an-allow-entry-for-the-senderrecipient-pair"></a>Gönderen/alıcı çifti için izin verme girdisi oluşturma

belirli gönderenler için kötü amaçlı yazılım filtreleme yerine kimlik avı filtrelemesinin bazı bölümleri olan istenmeyen posta filtrelemesini atlamak için bkz. [Microsoft 365'da güvenilir gönderen listeleri oluşturma](create-safe-sender-lists-in-office-365.md).

### <a name="ask-the-sender-to-configure-email-authentication-for-domains-you-dont-own"></a>Sahibi olmadığınız etki alanları için gönderenden e-posta kimlik doğrulamasını yapılandırmasını isteyin

İstenmeyen posta ve kimlik avı sorunu nedeniyle Microsoft, tüm e-posta kuruluşları için e-posta kimlik doğrulaması önerir. Kuruluşunuzda el ile geçersiz kılmaları yapılandırmak yerine, gönderen etki alanındaki bir yöneticiden e-posta kimlik doğrulama kayıtlarını yapılandırmasını isteyebilirsiniz.

- Geçmişte e-posta kimlik doğrulama kayıtlarını yayımlamaları gerekmese bile, Microsoft'a e-posta gönderiyorlarsa bunu yapmalıdır.

- Etki alanının gönderen IP adreslerini yayımlamak için SPF'yi ayarlayın ve iletileri dijital olarak imzalamak için DKIM'i (varsa) ayarlayın. Ayrıca DMARC kayıtlarını ayarlamayı da göz önünde bulundurmalıdır.

- Onlar adına e-posta göndermek için toplu gönderenler kullanıyorsa, Kimden adresindeki etki alanının (onlara aitse) SPF veya DMARC geçen etki alanıyla uyumlu olduğunu doğrulayın.

- SPF kaydına aşağıdaki konumların (kullanıyorlarsa) dahil olduğunu doğrulayın:

  - Şirket içi e-posta sunucuları.
  - Hizmet olarak yazılım (SaaS) sağlayıcısından gönderilen e-posta.
  - Bulut barındırma hizmetinden (Microsoft Azure, GoDaddy, Rackspace, Amazon Web Services vb.) gönderilen e-posta.

- ISS tarafından barındırılan küçük etki alanları için SPF kaydını ISS'nin yönergelerine göre yapılandırın.

İlk başta etki alanlarını kimlik doğrulaması için göndermek zor olsa da, zaman içinde daha fazla e-posta filtresi gereksiz olarak çalışmaya ve hatta e-postalarını reddetmeye başladığından, daha iyi teslim sağlamak için uygun kayıtları ayarlamalarına neden olur. Ayrıca, katılımları kimlik avına karşı mücadeleye yardımcı olabilir ve kuruluşlarında veya e-posta gönderdikleri kuruluşlarda kimlik avı olasılığını azaltabilir.

#### <a name="information-for-infrastructure-providers-isps-esps-or-cloud-hosting-services"></a>Altyapı sağlayıcıları (ISS'ler, ESP'ler veya bulut barındırma hizmetleri) için bilgiler

Bir etki alanının e-postasını barındırdıysanız veya e-posta gönderebilen barındırma altyapısı sağlıyorsanız, aşağıdaki adımları uygulamanız gerekir:

- Müşterilerinizin SPF kayıtlarını nasıl yapılandırmaları gerektiğini açıklayan belgelere sahip olduğundan emin olun

- Müşteri bunu açıkça ayarlamasa bile (varsayılan etki alanıyla oturum açın) giden e-postada DKIM imzalarını imzalamayı göz önünde bulundurun. E-postayı DKIM imzalarıyla (ayarladıysa müşterinin etki alanıyla bir kez ve şirketinizin DKIM imzası ile ikinci kez) çift imzalayabilirsiniz

Platformunuzdan gelen e-postaların kimliğini doğrulasanız bile Microsoft'a teslim edilebilirlik garanti değildir, ancak en azından microsoft'un kimlik doğrulaması yapılmadığı için e-postanızı gereksiz hale getirememesini sağlar.

## <a name="related-links"></a>İlgili bağlantılar

Hizmet sağlayıcılarının en iyi yöntemleri hakkında daha fazla bilgi için bkz. [M3AAWG Mobile Microsoft Mesajlaşma Hizmet Sağlayıcıları için En İyi Yöntemler](https://www.m3aawg.org/sites/default/files/m3aawg-mobile-messaging-best-practices-service-providers-2015-08_0.pdf).

Office 365 SPF'yi nasıl kullandığını ve DKIM doğrulamasını nasıl desteklediğini öğrenin:

- [SPF hakkında daha fazla bilgi](how-office-365-uses-spf-to-prevent-spoofing.md)

- [DKIM hakkında daha fazla bilgi](support-for-validation-of-dkim-signed-messages.md)
