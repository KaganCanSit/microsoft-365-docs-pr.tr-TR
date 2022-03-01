---
title: Kimlik avı önleme ilkeleri
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: ITPro
ms.topic: how-to
ms.date: ''
ms.localizationpriority: medium
ms.assetid: 5a6f2d7f-d998-4f31-b4f5-f7cbf6f38578
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: Yöneticiler, Exchange Online Protection (EOP) ve Office 365 için Microsoft Defender'da bulunan kimlik avı önleme ilkeleri hakkında bilgi Office 365.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 899a76fac01c6058d5642cb52af5a6e8fb7d11ee
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2022
ms.locfileid: "63032512"
---
# <a name="anti-phishing-policies-in-microsoft-365"></a>E-postada kimlik avı önleme Microsoft 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Geçerli olduğu yer:**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [1. plan Office 365 plan 2 için Microsoft Defender](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Kimlik avı koruma ayarlarını yapılandırmaya yönelik ilkeler Microsoft 365 posta kutuları olan Exchange Online kuruluşlarda, Exchange Online Protection posta kutuları olmayan tek başına Exchange Online Protection (EOP Exchange Online) kuruluşlarında ve Office 365 için.

Bu kuruluşlar için Microsoft Defender Office 365 örnekleri şunlardır:

- Microsoft 365 Kurumsal E5, Microsoft 365 Eğitim A5, vb.
- [Microsoft 365 Kurumsal](https://www.microsoft.com/microsoft-365/enterprise/home)
- [Microsoft 365 İş](https://www.microsoft.com/microsoft-365/business)
- [Eklenti olarak Office 365 için Microsoft Defender](https://products.office.com/exchange/advance-threat-protection)

EOP'de kimlik avı önleme ilkeleri ile Office 365 için Defender'daki kimlik avı ilkeleri arasındaki üst düzey farklar aşağıdaki tabloda açıklanmıştır:

<br>

****

|Özellik|EOP'de kimlik avı önleme ilkeleri|Office 365 için Defender'da kimlik avına karşı koruma Office 365|
|---|:---:|:---:|
|Otomatik olarak oluşturulan varsayılan ilke|![Onay işareti.](../../media/checkmark.png)|![Onay işareti.](../../media/checkmark.png)|
|Özel ilkeler oluşturma|![Onay işareti.](../../media/checkmark.png)|![Onay işareti.](../../media/checkmark.png)|
|Ortak ilke ayarları<sup>\*</sup>|![Onay işareti.](../../media/checkmark.png)|![Onay işareti.](../../media/checkmark.png)|
|Poof ayarları|![Onay işareti.](../../media/checkmark.png)|![Onay işareti.](../../media/checkmark.png)|
|İlk iletişim güvenlik ipucu|![Onay işareti.](../../media/checkmark.png)|![Onay işareti](../../media/checkmark.png)|
|Kimliğe bürünme ayarları||![Onay işareti](../../media/checkmark.png)|
|Gelişmiş kimlik avı eşikleri||![Onay işareti](../../media/checkmark.png)|
|

<sup>\*</sup> Varsayılan ilkede, ilke adı ve açıklaması salt okunur olur (açıklama boştur) ve ilkenin kimlere uygulanacağı belirtemezseniz (varsayılan ilke tüm alıcılar için geçerlidir).

Kimlik avı önleme ilkelerini yapılandırmak için aşağıdaki makalelere bakın:

- [EOP'de kimlik avı önleme ilkelerini yapılandırma](configure-anti-phishing-policies-eop.md)
- [Kimlik avıyla mücadele ilkelerini Microsoft Defender'da Office 365](configure-mdo-anti-phishing-policies.md)

Bu makalenin kalan bölümü, EOP'de kimlik avı ilkeleri ve Kimlik Avı için Defender'da bulunan Office 365.

## <a name="common-policy-settings"></a>Ortak ilke ayarları

Aşağıdaki ilke ayarları EOP'de kimlik avı önleme ilkelerde ve kimlik avı için Defender'da Office 365:

- **Ad**: Varsayılan kimlik avı önleme ilkesi yeniden adlandırılamaz. Özel bir kimlik avı önleme ilkesi oluşturduk sonra, bu ilkeyi Microsoft 365 Defender portalında yeniden Microsoft 365 Defender.

- **Açıklama** Varsayılan kimlik avı önleme ilkesine açıklama ek değildir, ancak kendi özel ilkelerinize açıklama ekleyebilir ve bu ilkeler için açıklamayı değiştirebilirsiniz.

- **Kullanıcılar, gruplar ve etki alanları**: Kimlik avı önleme ilkesine uygulanan iç alıcıları tanımlar. Bu değer özel ilkelerde gereklidir ve varsayılan ilkede kullanılamaz (varsayılan ilke tüm alıcılar için geçerlidir).

  Bir koşulu veya özel durumu yalnızca bir kez kullanabilirsiniz, ancak koşul veya özel durum için birden çok değer belirtebilirsiniz. Aynı koşul veya özel durum kullanımı VEYA mantığının birden çok değeri (örneğin, _\<recipient1\>_ veya _\<recipient2\>_). Farklı koşullar veya özel durumlar, AND mantığı kullanır (örneğin, _\<recipient1\>_ ve _\<member of group 1\>_).

  - **Kullanıcılar**: Bir veya birden çok posta kutusu, posta kullanıcısı veya posta kişileri.
  - **Gruplar**: Kuruluşta bir veya daha fazla grup.
  - **Etki** Alanları: Etki alanı içinde yapılandırılmış kabul [edilen etki alanlarından biri](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains) Microsoft 365.

  - **Bu kullanıcıları, grupları ve etki alanlarını dışla**: İlkeyle ilgili özel durumlar. Ayarlar ve davranış, tam olarak aşağıdaki koşullar gibi olur:
    - **Kullanıcılar**
    - **Gruplar**
    - **Etki alanları**

  > [!NOTE]
  > İlkenin geçerli olduğu ileti alıcılarını belirlemek için, özel kimlik avı ilkeleri içinde Kullanıcılar **,** gruplar ve etki alanı ayarlarında en az bir  <u>seçim gereklidir</u>. Office 365 için Defender'da kimlik avı önleme ilkeleri ayrıca, bu makalenin [](#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365) devamlarında açıklandığı gibi kimliğe bürünme koruması alacak tek tek gönderen e-posta adreslerini veya gönderen etki alanlarını belirtebilirsiniz.<u></u>

## <a name="spoof-settings"></a>Poof ayarları

Kimliği doğrulama, e-posta iletisinden gelen adresin (e-posta istemcilerde gösterilen gönderen adresi) e-posta kaynağının etki alanıyla eşleşmemiş olmasıdır. Bu konuda daha fazla bilgi için bkz. Bu konuda bilgi için bkz. [Microsoft 365](anti-spoofing-protection.md).

Aşağıdaki kimlik sahtesi ayarları EOP'de kimlik avı önleme ilkelerde ve kimlik avı için Defender'da Office 365:

- **Akıllı ifadeyi etkinleştirme**: Akıllı ifadeyi etkinleştirme veya devre dışıdır. Açık bırakmanizi öneririz.

  Akıllı ifadenin kimliği doğrulandığında, ele alınan  kimliği doğrulanmadı bilgisi içgörüleri, otomatik olarak algılandığında ve izin verilen ya da elemli ifadeyle engellenen kimliği doğrulandı gönderenleri gösterir. Bilgi bilgisinde, kimliği doğru tespit edilen göndericilere izin vermek veya bu iletileri engellemek için, ifadeyi el ile geçersiz kılabilirsiniz. Ancak bunu yapmakla, kimliği doğruya sahip olan gönderen kimliği doğru bilgi içgörüsten kaybolur ve artık yalnızca Kiracı İzin Ver/Engelleme  Listesi'nin Bilgi Kimliği sekmesinde görünür. Ayrıca, Kiracı İzin Ver/Engelle Listesinde kimliği doğru hesabı olan gönderenler için girişleri el ile de oluşturabilir veya engelleyebilirsiniz. Daha fazla bilgi için aşağıdaki makalelere bakın:

  - [EOP'de akıllı Spoof Intelligence içgörü](learn-about-spoof-intelligence.md)
  - [EOP'de Kiracı İzin Ver/Engelle Listesini Yönetme](tenant-allow-block-list.md)

  > [!NOTE]
  >
  > - Kimlik sahtesi önleme koruması, varsayılan kimlik avı önleme ilkesinde ve yeni özel kimlik avı önleme ilkelerde varsayılan olarak etkindir.
  > - MX kaydınız Yenile'ye işaret etmek yerine Bağlayıcılar için İyileştirilmiş Filtreleme'yi Microsoft 365' i etkinleştirmeniz gerekir. Yönergeler için bkz. [Exchange Online'ta Bağlayıcılar için İyileştirilmiş Filtreleme](/Exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/enhanced-filtering-for-connectors).
  > - Kimlik kimlik doğrulaması korumasını devre dışı bırakmak yalnızca bileşik kimlik doğrulama  denetimlerinden örtülü kimlik doğrulaması [korumasını devre dışı](email-validation-and-authentication.md#composite-authentication) bıraktır. Gönderen açık  [DMARC başarısız olursa,](use-dmarc-to-validate-email.md) ilkenin karantinaya alınarak veya reddedilecek şekilde ayar bulunduğu yeri denetler; ileti yine de karantinaya alınır veya reddedilir.

- **Kimliği doğrulanmamış gönderen bildirimleri**: Bu bildirimler yalnızca kimliksız kimlik doğrulaması açık olduğunda kullanılabilir. Sonraki bölümde yer alan bilgilere bakın.
- **Eylemler**: Engellenen e-posta gönderenlerden gelen iletiler için (akıllı ifadeyle otomatik olarak engellenen veya Kiracı İzin Ver/Engelle listesinde el ile engellenen iletiler için), iletilere yönelik eylemi de belirtebilirsiniz:
  - **İletileri alıcıların Gereksiz E-posta klasörlerine taşıma**: Bu varsayılan değerdir. İleti posta kutusuna teslim edilir ve Gereksiz E-posta klasörüne taşınır. Daha fazla bilgi için bkz[. Posta kutularında veya posta Exchange Online gereksiz e-posta Microsoft 365](configure-junk-email-settings-on-exo-mailboxes.md).
  - **İletiyi karantinaya** alın: İletiyi, hedeflenen alıcılar yerine karantinaya gönderir. Karantina hakkında bilgi için aşağıdaki makalelere bakın:
    - [E-Microsoft 365'de karantinaya alın](quarantine-email-messages.md)
    - [Karantinaya alınan iletileri ve dosyaları bir yönetici olarak e-posta Microsoft 365](manage-quarantined-messages-and-files.md)
    - [Karantinaya alınan iletileri bir kullanıcı olarak bulma ve Microsoft 365](find-and-release-quarantined-messages-as-a-user.md)

    İletiyi **karantinaya alın'ı** seçerseniz, akıllı belge koruması tarafından karantinaya alınmış iletilere uygulanan karantina ilkesine de sahip olabilir. Karantina ilkeleri, kullanıcıların karantinaya alınmış iletiler için neler yapalır ve kullanıcılar karantina bildirimlerinin alınıp alınamayabileceklerini tanımlar. Daha fazla bilgi için bkz. [Karantina ilkeleri](quarantine-policies.md).

### <a name="unauthenticated-sender"></a>Kimliği doğrulanmamış gönderen

Kimliği doğrulanmamış gönderen bildirimleri, önceki bölümde açıklandığı gibi [](#spoof-settings) EOP ve Office 365 için Defender'da kimlik avı önleme ilkelerde bulunan Kimlik sahtesi ayarlarının bir bölümüdur. Aşağıdaki ayarlar yalnızca bilgi yok ayarı açık olduğunda kullanılabilir:

- Kimliksüz kimlik doğrulaması için kimliği doğrulanmamış gönderenler için **(?)** göster: Bu bildirim, ileti SPF veya DKIM denetimlerinden geçelamasa ve ileti DMARC veya bileşik kimlik doğrulamasını geçese, Gönderen kutusunda gönderenin fotoğrafına bir soru işareti [ekler](email-validation-and-authentication.md#composite-authentication). Bu ayar kapalı olduğunda, soru işareti gönderenin fotoğrafına eklenmez.

- **"Aracılığıyla"** etiketini göster?: Bu bildirim, Gönderen adresi'nin etki alanı (e-posta istemcisinde görüntülenen ileti gönderen) DKIM imzası veya MAIL **FROM** adresi ile farklı ise, aracılığıyla etiketini <u>(chris@contoso.com aracılığıyla</u> fabrikam.com) Gönderen kutusuna ekler. Bu adresler hakkında daha fazla bilgi için bkz [. E-posta iletisi standartlarına genel bakış](how-office-365-validates-the-from-address.md#an-overview-of-email-message-standards).

Soru işaretinin veya etiket aracılığıyla belirli gönderenlerden gelen iletilere eklenmesini önlemek için, aşağıdaki seçenekleriniz vardır:

- Bilgi bilgisinde veya kiracı İzin Ver/Engelleme Listesinde el [ile bilgi sağlayan](learn-about-spoof-intelligence.md) kimliği doğru [gönderene izin ver](tenant-allow-block-list.md). Kimliksiz gönderen kimliği doğrulanmamış gönderen kimliği devre dışı bırakılmıştır, kimlik bilgileri doğrulanmamış gönderenden gelen iletilerde via etiketinin görünmesini engellemektedir.
- [Gönderen etki alanı için e-posta](email-validation-and-authentication.md#configure-email-authentication-for-domains-you-own) kimlik doğrulamasını yapılandırma.
  - Gönderenin fotoğrafına gelen soru işareti için SPF veya DKIM en önemlileridir.
  - Aracılığıyla etiketi için DKIM imzasıyla veya **MAIL FROM** adresiyle eşleşen (veya bir alt etki alanı olan) etki alanının From adresine eş olduğunu onaylayın.

Daha fazla bilgi için bkz[. Outlook.com'da şüpheli iletileri tanımlama ve](https://support.microsoft.com/office/3d44102b-6ce3-4f7c-a359-b623bec82206) Web üzerinde Outlook

## <a name="first-contact-safety-tip"></a>İlk iletişim güvenlik ipucu

İlk **kişi kimliğini göster güvenlik ipucu** ayarları EOP ve Defender'da Office 365 kuruluşlar için kullanılabilir ve kimlik sahteciliğe veya kimliğe bürünme koruma ayarlarına bağımlılığı yoktur. Güvenlik ipucu aşağıdaki senaryolarda alıcılara gösterilir:

- gönderenden ilk kez ileti alan kişiler
- Çoğunlukla gönderenden ileti alırlar.

![Tek alıcılı güvenlik ipucu için ilk kişi adresi.](../../media/safety-tip-first-contact-one-recipient.png)

![Birden çok güvenlik ipucu ileti için ilk iletişim adresi.](../../media/safety-tip-first-contact-multiple-recipients.png)

Bu özellik, olası kimliğe bürünme saldırılarına karşı ek bir güvenlik koruması katmanı ekler; dolayısıyla bu özelliği açmanız önerilir.

İlk kişi güvenlik ipucu **X-MS-Exchange-EnableFirstContactSafetyTip** adlı üstbilgiyi iletilere etkinleştir (yine de bu özellik mevcut olsa da) ekli posta akışı kuralları oluşturma gereğini de değiştirir.

> [!NOTE]
> İletinin birden çok alıcısı varsa, ipucunun göster olup olmadığı ve kimin için bir çoğunluk modelini temel alan bir ipucu olduğu. Alıcıların çoğunluğu asla veya çoğu zaman gönderenden ileti almayacaksa, etkilenen alıcılar bu iletiyi alan bazı kişiler **... ipucunu** alır. Bu davranışın bir alıcının diğer alıcıya iletişim alışkanlıkları konusunda endişeleriniz varsa, ilk iletişim güvenlik ipucu etkinleştirme olmalı ve onun yerine posta akış kurallarını kullanmaya devam edesiniz.

## <a name="exclusive-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365"></a>Kimlik avıyla mücadele ilkeleri için Microsoft Defender'daki özel Office 365

Bu bölümde, yalnızca Office 365 için Defender'daki kimlik avı önleme ilkelerde kullanılabilen ilke ayarları açık Office 365.

> [!NOTE]
> Office 365 için Defender'daki varsayılan kimlik avı koruma ilkesi, tüm alıcılar için kimlik [avı koruması ve](set-up-anti-phishing-policies.md#spoof-settings) posta kutusu zekası sağlar. Bununla birlikte, diğer kullanılabilir [kimliğe bürünme](#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365) koruma [özellikleri ve gelişmiş](set-up-anti-phishing-policies.md#advanced-phishing-thresholds-in-anti-phishing-policies-in-microsoft-defender-for-office-365) ayarlar varsayılan ilkede yapılandırılmaz veya etkinleştirilmez. Tüm koruma özelliklerini etkinleştirmek için, varsayılan kimlik avı önleme ilkesine değişiklik veya ek kimlik avı koruma ilkeleri oluşturun.

### <a name="impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365"></a>Office 365 için Microsoft Defender'da kimlik avı önleme ilkelerinde kimliğe bürünme Office 365

Kimliğe Bürünme, gönderenin veya gönderenin e-posta etki alanının bir iletide gerçek gönderene veya etki alanına benser olduğu durumla benzer:

- Etki alanı kimliğine bürünme örneği contoso.com kimliğine ćóntoso.com.
- Kullanıcı kimliğine bürünme, kullanıcının görünen adının ve e-posta adresinin bileşimidir. Örneğin, Valeria Barrios (vbarrios@contoso.com) Valeria Barrios gibi kimliğine bürünülse de, tamamen farklı bir e-posta adresine sahip olabilir.

> [!NOTE]
> Kimliğe Bürünme koruması da benzer etki alanları için kullanılabilir. Örneğin, etki alanınız başka contoso.com etki alanları (.com, .biz, vb.) için kimliğe bürünme girişimleri, hatta biraz da benzer etki alanları olup adlarını denetlememiz gerekir. Örneğin, contosososo.com veya contoabcdef.com kimliğe bürünme girişimleri olarak contoso.com.

Kimliğine bürünülen bir etki alanı yasal (kayıtlı etki alanı, yapılandırılmış e-posta kimlik doğrulama kayıtları, vb.) kabul edilir, ancak amacı alıcıları kandırmaktır.

Aşağıdaki kimliğe bürünme ayarları yalnızca kimlik avı önleme ilkeleri için Defender'da Office 365:

- **Kullanıcıların korumasını etkinleştirme**: Belirtilen iç veya dış e-posta adreslerinin ileti gönderenleri olarak **kimliğine bürünülmelerini sağlar**. Örneğin, Şirketinizin Başkan Yardımcısı'nın şirket içi bazı bilgilerini göndermenizi isteyen bir e-posta iletisi alırsınız. Bunu yapar mısınız? Birçok kişi düşünmeden yanıtı gönderir.

  Kimliğe bürünmelerden korumak üzere, korumalı kullanıcıları kullanarak iç ve dış gönderen e-posta adreslerini ebilirsiniz. Kullanıcı kimliğe  bürünme tarafından korunan bu gönderenler listesi, ilkenin geçerli olduğu alıcılar listesinden farklıdır (varsayılan ilkenin tüm alıcıları; Ortak ilke ayarları bölümündeki Kullanıcılar **,** gruplar ve etki alanları ayarında yapılandırılan belirli alıcılar). [](#common-policy-settings)

  > [!NOTE]
  >
  > - Her kimlik avı önleme ilkesinde, en çok 350 korumalı kullanıcı (gönderen e-posta adresleri) belirtebilirsiniz. Aynı korumalı kullanıcıyı birden çok ilkede belirtemezseniz. Dolayısıyla, bir alıcıya kaç ilke ekli olduğu önemli değildir; her bir alıcı için en fazla korumalı kullanıcı (gönderen e-posta adresi) sayısı 350'dir. İlke önceliği ve ilk ilke uygulandıktan sonra ilke işlemenin nasıl durduğu hakkında daha fazla bilgi için bkz [. E-posta korumasının sırası ve önceliği](how-policies-and-protections-are-combined.md).
  > - Gönderen ve alıcı daha önce e-posta yoluyla iletişim kursa, kullanıcı kimliğine bürünme koruması işe yaramadı. Gönderen ve alıcı e-postayla hiçbir zaman iletişim kurmadı ise, ileti kimliğe bürünme girişimi olarak tanımlanır.

  Varsayılan olarak, hiçbir gönderen e-posta adresi, korunması için Kullanıcılar'da kimliğe **bürünme koruması için yapılandırılmaz**. Bu nedenle, varsayılan olarak, hiçbir gönderen e-posta adresi varsayılan ilkede veya özel ilkelerde kimliğe bürünme koruması kapsamında değildir.

  Korumak için Kullanıcılar listesine iç veya dış e-posta  adresleri eklerken, bu gönderenlerden gelen  iletiler kimliğe bürünme koruma denetimlerine tabi olur. İleti ilkenin geçerli olduğu bir **alıcıya** gönderilirse, ileti kimliğe  bürünülmek üzere denetlenir (varsayılan ilkenin tüm alıcıları; **Özel ilkelerde kullanıcılar, gruplar** ve etki alanları alıcıları). Gönderenin e-posta adresine kimliğe bürünme algılanırsa, kullanıcılar için kimliğe bürünme koruma eylemleri iletiye uygulanır (iletiyle ne yapılır, kimliğine bürünülen kullanıcıların güvenlik ipuçlarının göster isteyip olmadığı vb.).

- **Korumak için etki alanlarını etkinleştirme**: Belirtilen etki alanlarının ileti gönderenin etki alanında **kimliğine bürünülmelerini sağlar**. Örneğin, sahip olduğunuz tüm etki alanları (kabul edilen [etki](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains) alanları) veya belirli özel etki alanları (sahibisiniz veya iş ortağı etki alanlarınız) olabilir. Kimliğe bürünme tarafından korunan bu gönderen etki alanları listesi, ilkenin geçerli olduğu alıcılar  listesinden farklıdır (varsayılan ilkenin tüm alıcıları; Ortak ilke ayarları bölümündeki Kullanıcılar **,** gruplar ve etki alanları ayarında yapılandırılan belirli alıcılar). [](#common-policy-settings)

  > [!NOTE]
  > Tüm kimlik avı koruma ilkesinde tanımladığınız korumalı etki alanı sayısı üst sayısı 50'dir.

  Varsayılan olarak, Etki alanlarını korumak için etkinleştir altında hiçbir gönderen etki alanı kimliğe **bürünme koruması için yapılandırılmaz**. Bu nedenle, varsayılan olarak hiçbir gönderen etki alanı varsayılan ilkede veya özel ilkelerde kimliğe bürünme koruması kapsamında değildir.

  Etki alanlarını Korumak için etki alanlarını etkinleştir listesine **eklerken** , bu etki alanlarındaki gönderenlerden gelen **iletiler kimliğe** bürünme koruma denetimlerine tabi olur. İleti ilkenin geçerli olduğu bir **alıcıya** gönderilirse, ileti kimliğe  bürünülmek üzere denetlenir (varsayılan ilkenin tüm alıcıları; **Özel ilkelerde kullanıcılar, gruplar** ve etki alanları alıcıları). Gönderenin etki alanında kimliğe bürünme algılanırsa, etki alanları için kimliğe bürünme koruma eylemleri iletiye uygulanır (iletiyle ne yapılır, kimliğine bürünülen kullanıcıların güvenlik ipuçlarının göster isteyip olmadığı, vb.).

- **Eylemler**: Kimliğe bürünme girişimleri içeren gelen iletileri ilkede korumalı kullanıcılara ve korunan etki alanlarına yönelik olarak almak için eylemi seçin. Korumalı kullanıcıların kimliğe bürünme ve korumalı etki alanlarını kimliğe bürünme işlemleri için farklı eylemler belirtebilirsiniz:
  - **Hiçbir eylem uygulama**
  - **İletiyi diğer e-posta adreslerine** yönlendirme: İletiyi, hedeflenen alıcılar yerine belirtilen alıcılara gönderir.
  - **İletileri alıcıların Gereksiz E-posta** klasörlerine taşıma: İleti posta kutusuna teslim edilir ve Gereksiz E-posta klasörüne taşınır. Daha fazla bilgi için bkz[. Posta kutularında veya posta Exchange Online gereksiz e-posta Microsoft 365](configure-junk-email-settings-on-exo-mailboxes.md).
  - **İletiyi karantinaya** alın: İletiyi, hedeflenen alıcılar yerine karantinaya gönderir. Karantina hakkında bilgi için aşağıdaki makalelere bakın:
    - [E-Microsoft 365'de karantinaya alın](quarantine-email-messages.md)
    - [Karantinaya alınan iletileri ve dosyaları bir yönetici olarak e-posta Microsoft 365](manage-quarantined-messages-and-files.md)
    - [Karantinaya alınan iletileri bir kullanıcı olarak bulma ve Microsoft 365](find-and-release-quarantined-messages-as-a-user.md)

    İletiyi **karantinaya alın'ı** seçerseniz, kullanıcı kimliğe bürünme veya etki alanı kimliğe bürünme koruması tarafından karantinaya alınan iletilere uygulanan karantina ilkesine de uygun olur. Karantina ilkeleri, kullanıcıların karantinaya alınmış iletiler için neler yapalarını tanımlar. Daha fazla bilgi için bkz. [Karantina ilkeleri](quarantine-policies.md).

  - **İletiyi teslim etmek ve** diğer adresleri Gizli satırına eklemek: İletiyi hedeflenen alıcılara teslim etmek ve iletiyi sessiz bir şekilde belirtilen alıcılara teslim etmek.
  - **İleti teslim olmadan önce silin**: Tüm ekler dahil olmak üzere iletinin tamamını sessiz bir şekilde siler.

- **Kimliğe bürünme güvenliği** ipuçları: Kimliğe bürünme denetimlerini başarısız olan iletiler görünecek olan aşağıdaki kimliğe bürünme güvenlik ipuçlarını açma veya kapatma:
  - **Kimliğine bürünülen kullanıcılar için** ipucu göster: Kimliğe bürünülen kullanıcılar için bir **Etkinleştirme adresi** vardır. Yalnızca Kullanıcıların **korunmasını etkinleştir seçeneği açık** ve yapılandırılmışsa kullanılabilir.
  - **Kimliğine bürünülen etki alanları** için ipucu göster: Kimliğe bürünülen adres etki alanını **korumak için etki alanlarını etkinleştirin adresini** içerir. Yalnızca Etki alanlarını **korumak için etkinleştir seçeneği** açık ve yapılandırılmışsa kullanılabilir.
  - Alışılmış **dışı** karakterler için ipucu göster: Gönderen adresi, Kullanıcıların göndereni korumalarına izin vermek için etkinleştir veya Gönderen etki alanını korumak için etki alanlarını etkinleştir kısmında olağandışı karakter kümeleri (örneğin, matematik simgeleri ve metinler  ya da büyük ve küçük harflerin karışımı) içerir.  Yalnızca Kullanıcıların **korunmasını etkinleştir veya Korumak için** _etki_ **alanlarını etkinleştir seçeneği açık** ve yapılandırılmışsa kullanılabilir.

- **Posta kutusu zekasını** etkinleştirme: Sık kişileriyle kullanıcı e-posta modellerini belirleyen yapay zekayı (AI) etkinleştirir ya da devre dışı bıraktır. Bu ayar, AI'nın iletileri yasal ve kimliğine bürünülen gönderenlerden ayırt ed etmeye yardımcı olur.

  Örneğin, Gabriela Laureano (glaureano@contoso.com) şirketinizin CEO'su olduğu için, Kullanıcıların ilke ayarlarını korumasını etkinleştirme sayfasında onu korumalı bir gönderen olarak eklersiniz. Ancak, ilkenin uygulandığı bazı alıcılar, aynı zamanda Sila Laureano (abd) olarak da adlandırılmış bir satıcıyla düzenli olarak iletişim glaureano@fabrikam.com. Bu alıcıların glaureano@fabrikam.com ile iletişim geçmişi olduğundan, posta kutusu zekası bu alıcılara kimliğe bürünme girişimi glaureano@fabrikam.com gelen iletileri glaureano@contoso.com tanımlamaz.

  Posta kutusu zekası tarafından öğrenilen (ve olmaması gereken) sık sık kişileri kullanarak kullanıcıları kimliğe bürünme saldırılarından korumaya yardımcı olmak için, Posta  kutusu zekasını etkinleştir'i etkinleştirdikten sonra zeka kimliğe bürünme korumasını **etkinleştir'i açabilirsiniz**.

- **Zeka kimliğe bürünme korumasını** etkinleştirme: Posta kutusu kimliğine bürünme algılamaları için iletilerde işlem yapmak için gereken eylemi belirtmek için bu ayarı etkinleştirin:
  - **Hiçbir eylem uygulamama: Bu** değerin, Posta kutusu zekası'nın yanı sıra,  Zeka kimliğine bürünme korumasını etkinleştir'i kapatmayla aynı sonucu elde **olduğunu unutmayın**.
  - **İletiyi diğer e-posta adreslerine yeniden yönlendirme**
  - **İletiyi alıcıların Gereksiz E-posta klasörlerine taşıma**
  - **İletiyi karantinaya** alın: Bu eylemi seçerseniz, posta kutusu zekası koruması tarafından karantinaya alınan iletilere uygulanan karantina ilkesine de erişebilirsiniz. Karantina ilkeleri, kullanıcıların karantinaya alınmış iletiler için neler yapalır ve kullanıcılar karantina bildirimlerinin alınıp alınamayabileceklerini tanımlar. Daha fazla bilgi için bkz. [Karantina ilkeleri](quarantine-policies.md).
  - **İletiyi teslim etmek ve Gizli satırına başka adresler ekleme**
  - **İleti teslim edilene kadar silin**

- **Güvenilen gönderenleri ve etki alanlarını ekleme**: Kimliğe bürünme koruma ayarlarıyla ilgili özel durumlar. Belirtilen gönderenlerden ve gönderen etki alanlarından gelen iletiler ilke tarafından hiçbir zaman kimliğe bürünme tabanlı saldırılar olarak sınıflandırılmaz. Başka bir deyişle, korumalı gönderenler, korunan etki alanları veya posta kutusu zekası koruması eylemi bu güvenilen gönderenlere veya gönderen etki alanlarına uygulanmaz. Bu listeler için en yüksek sınır 1024 girdidir.

### <a name="advanced-phishing-thresholds-in-anti-phishing-policies-in-microsoft-defender-for-office-365"></a>Office 365 için Microsoft Defender'da kimlik avı önleme ilkelerde gelişmiş kimlik Office 365

Aşağıdaki gelişmiş kimlik avı eşikleri yalnızca Office 365 için Defender'daki kimlik avı önleme ilkelerde Office 365. Bu eşikler kimlik avı kararını belirlemek üzere iletilere makine öğrenme modelleri uygulama duyarlılığını belirler:

- **1 - Standart**: Bu, varsayılan değerdir. İletide iletiyi alan eylemin önem derecesi, iletinin kimlik avı (düşük, orta, yüksek veya çok yüksek güven düzeyi) olduğunu güvenlik derecesine bağlıdır. Örneğin, kimlik avı olarak tanımlanan ve çok yüksek güven derecesine sahip iletilere en ciddi işlemler uygulanırken, kimlik avı olarak tanımlanan ve güven derecesi düşük olan iletilere daha az ciddi eylemler uygulanır.
- **2 - Saldırgan**: Kimlik avı olarak tanımlanan ve yüksek düzeyde güvenen iletiler, çok yüksek güven derecesiyle tanımlandı gibi kabul edilir.
- **3 - Daha agresif**: Orta veya yüksek düzeyde güven derecesiyle kimlik avı olarak tanımlanan iletiler, çok yüksek güven derecesiyle tanımlandı gibi kabul edilir.
- **4 - En saldırgan**: Kimlik avı olarak tanımlanan ve düşük, orta veya yüksek düzeyde güven derecesine sahip iletiler, kimlik avından çok yüksek düzeyde güvenerek tanımlandı gibi kabul edilir.

Bu ayarı artırtıkça hatalı pozitif sonuç (kötü işaretli iyi iletiler) ihtimali artar. Önerilen ayarlar hakkında bilgi için bkz. Kimlik avı ayarları için [Microsoft Defender'da kimlik Office 365.](recommended-settings-for-eop-and-office365.md#anti-phishing-policy-settings-in-microsoft-defender-for-office-365)
