---
title: Kimlik avından koruma ilkeleri
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
description: Yöneticiler, Exchange Online Protection (EOP) ve Office 365 için Microsoft Defender'de kullanılabilen kimlik avı önleme ilkeleri hakkında bilgi edinebilir.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 1a1265e70c0d22182e8ee4db865eeb53ac8168b7
ms.sourcegitcommit: 18bc521a88b7b521bccb0e69d02deac764218087
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/16/2022
ms.locfileid: "66115905"
---
# <a name="anti-phishing-policies-in-microsoft-365"></a>Microsoft 365'de kimlik avı önleme ilkeleri

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Uygulandığı öğe**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Office 365 için Microsoft Defender plan 1 ve plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Kimlik avı koruması ayarlarını yapılandırma ilkeleri, Exchange Online posta kutuları, Exchange Online posta kutusu olmayan tek başına Exchange Online Protection (EOP) kuruluşları ve Microsoft 365 kuruluşlarda kullanılabilir ve Office 365 için Microsoft Defender kuruluşlar.

Office 365 için Microsoft Defender kuruluş örnekleri şunlardır:

- Microsoft 365 Kurumsal E5, Microsoft 365 Eğitim A5 vb.
- [Microsoft 365 Kurumsal](https://www.microsoft.com/microsoft-365/enterprise/home)
- [Microsoft 365 İş](https://www.microsoft.com/microsoft-365/business)
- [Eklenti olarak Office 365 için Microsoft Defender](https://products.office.com/exchange/advance-threat-protection)

EOP'deki kimlik avı önleme ilkeleri ile Office 365 için Defender'deki kimlik avı önleme ilkeleri arasındaki üst düzey farklar aşağıdaki tabloda açıklanmıştır:

|Özellik|EOP'de kimlik avı önleme ilkeleri|Office 365 için Defender'de kimlik avı önleme ilkeleri|
|---|:---:|:---:|
|Otomatik olarak oluşturulan varsayılan ilke|![Onay işareti.](../../media/checkmark.png)|![Onay işareti.](../../media/checkmark.png)|
|Özel ilkeler oluşturma|![Onay işareti.](../../media/checkmark.png)|![Onay işareti.](../../media/checkmark.png)|
|Ortak ilke ayarları<sup>\*</sup>|![Onay işareti.](../../media/checkmark.png)|![Onay işareti.](../../media/checkmark.png)|
|Kimlik sahtekarı ayarları|![Onay işareti.](../../media/checkmark.png)|![Onay işareti.](../../media/checkmark.png)|
|İlk kişi güvenlik ipucu|![Onay işareti.](../../media/checkmark.png)|![Onay işareti](../../media/checkmark.png)|
|Kimliğe bürünme ayarları||![Onay işareti](../../media/checkmark.png)|
|Gelişmiş kimlik avı eşikleri||![Onay işareti](../../media/checkmark.png)|

<sup>\*</sup> Varsayılan ilkede, ilke adı ve açıklaması salt okunurdur (açıklama boş olur) ve ilkenin kime uygulanacağını belirtemezsiniz (varsayılan ilke tüm alıcılar için geçerlidir).

Kimlik avı önleme ilkelerini yapılandırmak için aşağıdaki makalelere bakın:

- [EOP'de kimlik avı önleme ilkelerini yapılandırma](configure-anti-phishing-policies-eop.md)
- [Office 365 için Microsoft Defender'de kimlik avı önleme ilkelerini yapılandırma](configure-mdo-anti-phishing-policies.md)

Bu makalenin geri kalanında EOP ve Office 365 için Defender kimlik avı önleme ilkelerinde kullanılabilen ayarlar açıklanmaktadır.

## <a name="common-policy-settings"></a>Ortak ilke ayarları

Aşağıdaki ilke ayarları EOP ve Office 365 için Defender kimlik avı önleme ilkelerinde kullanılabilir:

- **Ad**: Varsayılan kimlik avı önleme ilkesini yeniden adlandıramazsınız. Özel kimlik avı önleme ilkesi oluşturduktan sonra, ilkeyi Microsoft 365 Defender portalında yeniden adlandıramazsınız.

- **Açıklama** Varsayılan kimlik avı önleme ilkesine açıklama ekleyemezsiniz, ancak oluşturduğunuz özel ilkelerin açıklamasını ekleyip değiştirebilirsiniz.

- **Kullanıcılar, gruplar ve etki alanları**: Kimlik avı önleme ilkesinin geçerli olduğu iç alıcıları tanımlar. Bu değer özel ilkelerde gereklidir ve varsayılan ilkede kullanılamaz (varsayılan ilke tüm alıcılar için geçerlidir).

  Bir koşulu veya özel durumu yalnızca bir kez kullanabilirsiniz, ancak koşul veya özel durum için birden çok değer belirtebilirsiniz. Aynı koşula veya özel duruma ait birden çok değer OR mantığını kullanır (örneğin, _\<recipient1\>_ veya _\<recipient2\>_). Farklı koşullar veya özel durumlar AND mantığını kullanır (örneğin, _\<recipient1\>_ ve _\<member of group 1\>_).

  - **Kullanıcılar**: Kuruluşunuzdaki bir veya daha fazla posta kutusu, posta kullanıcısı veya posta kişisi.
  - **Gruplar**: Kuruluşunuzdaki bir veya daha fazla grup.
  - **Etki alanları**: Microsoft 365'da yapılandırılmış [kabul edilen etki alanlarından](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains) biri veya daha fazlası.

  - **Bu kullanıcıları, grupları ve etki alanlarını dışlayın**: İlke için özel durumlar. Ayarlar ve davranış, koşullarla tam olarak benzerdir:
    - **Kullanıcılar**
    - **Gruplar**
    - **Etki alanları**

  > [!NOTE]
  > İlkenin <u>geçerli</u> olduğu ileti **alıcılarını** tanımlamak için özel kimlik avı önleme ilkelerinde **Kullanıcılar, gruplar ve etki alanları** ayarlarında en az bir seçim yapılması gerekir. Office 365 için Defender'deki kimlik avı önleme ilkeleri, bu makalenin devamında açıklandığı gibi <u>kimliğe bürünme koruması alacak</u> tek tek gönderen e-posta adreslerini veya gönderen etki alanlarını belirtebileceğiniz [kimliğe bürünme ayarlarına](#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365) da sahiptir.
  >
  > Birden çok farklı koşul veya özel durum ek değildir; Onlar kapsayıcı. İlke _yalnızca_ belirtilen alıcı filtrelerinin _tümüyle_ eşleşen alıcılara uygulanır. Örneğin, ilkede aşağıdaki değerlerle bir alıcı filtresi koşulu yapılandırabilirsiniz:
  >
  > - Alıcı: romain@contoso.com
  > - Alıcı şu üyelerin üyesidir: Yöneticiler
  >
  > İlke, _romain@contoso.com yalnızca_ Yönetici gruplarının da üyesiyse uygulanır. Grubun üyesi değilse ilke ona uygulanmaz.
  >
  > Benzer şekilde, ilkenin özel durumu olarak aynı alıcı filtresini kullanırsanız, ilke _romain@contoso.com yalnızca_ Yöneticiler gruplarının da üyesiyse uygulanmaz. Grubun üyesi değilse, ilke hala onun için geçerlidir.

## <a name="spoof-settings"></a>Kimlik sahtekarı ayarları

Kimlik sahtekarlığına, e-posta iletisindeki Kimden adresi (e-posta istemcilerinde gösterilen gönderen adresi) e-posta kaynağının etki alanıyla eşleşmediğinde kullanılır. Kimlik sahtekarlığı hakkında daha fazla bilgi için bkz. [Microsoft 365'de kimlik sahtekarlığı önleme koruması](anti-spoofing-protection.md).

Aşağıdaki kimlik sahtekarlığı ayarları EOP ve Office 365 için Defender kimlik avı önleme ilkelerinde kullanılabilir:

- **Kimlik sahtekarlık zekasını etkinleştirme**: Kimlik sahtekarı zekasını açar veya kapatır. Açık bırakmanızı öneririz.

  Kimlik sahtekarlığı zekası etkinleştirildiğinde, sahte **zeka içgörüleri** , kimlik sahtekarlığı zekası tarafından otomatik olarak algılanan ve izin verilen veya engellenen sahte gönderenleri gösterir. Algılanan sahte gönderenlere içgörü içinden izin vermek veya bunları engellemek için sahte zeka kararını el ile geçersiz kılabilirsiniz. Ancak bunu yaptığınızda, sahte gönderen sahte zeka içgörüsünden kaybolur ve artık yalnızca Kiracı İzin Ver/Engelle Listesi'ndeki **Kimlik Sahtekarı** sekmesinde görünür. Ayrıca Kiracı İzin Ver/Engelle Listesi'nde sahte gönderenler için el ile izin verme veya engelleme girdileri oluşturabilirsiniz. Daha fazla bilgi için aşağıdaki makalelere bakın:

  - [EOP'de sahte zeka içgörüleri](learn-about-spoof-intelligence.md)
  - [EOP'de Kiracı İzin Ver/Engelle Listesini Yönetme](tenant-allow-block-list.md)

  > [!NOTE]
  >
  > - Kimlik sahtekarlığı önleme koruması varsayılan kimlik avı önleme ilkesinde ve oluşturduğunuz yeni özel kimlik avı önleme ilkelerinde varsayılan olarak etkindir.
  > - MX kaydınız Microsoft 365 işaret etmiyorsa kimlik sahtekarlığı önleme korumasını devre dışı bırakmanız gerekmez; bunun yerine Bağlayıcılar için Gelişmiş Filtreleme'yi etkinleştirirsiniz. Yönergeler için bkz. [Exchange Online'da Bağlayıcılar için Gelişmiş Filtreleme](/Exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/enhanced-filtering-for-connectors).
  > - Kimlik sahtekarlığı önleme korumasını devre dışı bırakmak yalnızca [bileşik kimlik doğrulama](email-validation-and-authentication.md#composite-authentication) denetimlerinden _örtük_ kimlik sahtekarlığı korumasını devre dışı bırakır. Gönderen _açık_ [DMARC](use-dmarc-to-validate-email.md) başarısız olursa ilkenin karantinaya alınacağı veya reddedileceği yeri denetler, ileti yine de karantinaya alınır veya reddedilir.

- **Kimliği doğrulanmamış gönderen göstergeleri**: **Güvenlik ipuçları & göstergeler** bölümünde yalnızca kimlik sahtekarı zekası açıkken kullanılabilir. Sonraki bölümdeki ayrıntılara bakın.
- **Eylemler**: Engellenen kimlik sahtekarlığı gönderenlerden gelen iletiler için (kimlik sahtekarlığı zekası tarafından otomatik olarak engellenir veya Kiracı İzin Ver/Engelle listesinde el ile engellenir), iletiler üzerinde gerçekleştireceğiniz eylemi de belirtebilirsiniz:
  - **İletileri alıcıların Gereksiz E-posta klasörlerine taşıma**: Bu varsayılan değerdir. İleti posta kutusuna teslim edilir ve Gereksiz E-posta klasörüne taşınır. Daha fazla bilgi için bkz[. Microsoft 365'da Exchange Online posta kutularında gereksiz e-posta ayarlarını yapılandırma](configure-junk-email-settings-on-exo-mailboxes.md).
  - **İletiyi karantinaya** al: İletiyi hedeflenen alıcılar yerine karantinaya gönderir. Karantina hakkında bilgi için aşağıdaki makalelere bakın:
    - [Microsoft 365'de karantinaya alın](quarantine-email-messages.md)
    - [karantinaya alınan iletileri ve dosyaları Microsoft 365'da yönetici olarak yönetme](manage-quarantined-messages-and-files.md)
    - [karantinaya alınan iletileri Microsoft 365'de kullanıcı olarak bulma ve bırakma](find-and-release-quarantined-messages-as-a-user.md)

    **İletiyi karantinaya al'ı** seçerseniz, kimlik sahtekarlığına karşı koruma tarafından karantinaya alınan iletilere uygulanan karantina ilkesini de seçebilirsiniz. Karantina ilkeleri, kullanıcıların karantinaya alınan iletilere neler yapabileceğini ve kullanıcıların karantina bildirimleri alıp almayacağını tanımlar. Daha fazla bilgi için bkz [. Karantina ilkeleri](quarantine-policies.md).

### <a name="unauthenticated-sender-indicators"></a>Kimliği doğrulanmamış gönderen göstergeleri

Kimliği doğrulanmamış gönderen göstergeleri, hem EOP hem de Office 365 için Defender kimlik avı önleme ilkelerinin **Güvenlik ipuçları & göstergeleri** bölümünde bulunan Kimlik Sahtekarlığı [ayarlarının](#spoof-settings) bir parçasıdır. Aşağıdaki ayarlar yalnızca kimlik sahtekarı zekası açık olduğunda kullanılabilir:

- Kimlik **sahtekarlığına yönelik kimliği doğrulanmamış gönderenler için göster (?):** İleti SPF veya DKIM denetimlerini geçmezse **ve** ileti DMARC veya [bileşik kimlik doğrulamasını](email-validation-and-authentication.md#composite-authentication) geçmezse Kimden kutusuna gönderenin fotoğrafına bir soru işareti ekler. Bu ayar kapatıldığında, soru işareti gönderenin fotoğrafına eklenmez.

- **"via" etiketini göster**: Kimden adresindeki etki alanı (e-posta istemcilerinde görüntülenen ileti gönderen) DKIM imzasında veya **MAIL FROM** adresinden farklıysa, Kimden kutusuna via etiketini (fabrikam.com <u>yoluyla</u> chris@contoso.com) ekler. Bu adresler hakkında daha fazla bilgi için bkz. [E-posta iletisi standartlarına genel bakış](how-office-365-validates-the-from-address.md#an-overview-of-email-message-standards).

Soru işaretinin veya etiketin belirli gönderenlerden gelen iletilere eklenmesini önlemek için aşağıdaki seçeneklere sahipsiniz:

- Kimlik sahtekarlığına sahip gönderene [kimlik bilgileri içgörüsüsünde](learn-about-spoof-intelligence.md) veya [Kiracı İzin Ver/Engelle Listesi'nde](tenant-allow-block-list.md) el ile izin verin. sahte gönderene izin vermek, ilkede **"via" etiketini göster** ayarı açık olsa bile, gönderenden gelen iletilerde via etiketinin görünmesini engeller.
- Gönderen etki alanı için [e-posta kimlik doğrulamasını yapılandırın](email-validation-and-authentication.md#configure-email-authentication-for-domains-you-own).
  - Gönderenin fotoğrafındaki soru işareti için SPF veya DKIM en önemlileridir.
  - via etiketi için DKIM imzasında etki alanını onaylayın veya **MAIL FROM** adresi, Kimden adresindeki etki alanıyla eşleşir (veya bir alt etki alanıdır).

Daha fazla bilgi için bkz. [Outlook.com'da şüpheli iletileri tanımlama ve Web üzerinde Outlook](https://support.microsoft.com/office/3d44102b-6ce3-4f7c-a359-b623bec82206)

## <a name="first-contact-safety-tip"></a>İlk kişi güvenlik ipucu

**İlk kişi güvenlik ipucu ayarlarını göster** EOP ve Office 365 için Defender kuruluşlarında kullanılabilir ve kimlik sahtekarlığı zekası veya kimliğe bürünme koruma ayarlarına bağımlılığı yoktur. güvenlik ipucu aşağıdaki senaryolarda alıcılara gösterilir:

- Gönderenden ilk kez ileti aldıkları zaman
- Genellikle gönderenden ileti alamazlar.

:::image type="content" source="../../media/safety-tip-first-contact-one-recipient.png" alt-text="İlk kişi, bir alıcısı olan iletiler için güvenlik ipucu" lightbox="../../media/safety-tip-first-contact-one-recipient.png":::

:::image type="content" source="../../media/safety-tip-first-contact-multiple-recipients.png" alt-text="İlk kişi, birden çok alıcısı olan iletiler için güvenlik ipucu" lightbox="../../media/safety-tip-first-contact-multiple-recipients.png":::

Bu özellik olası kimliğe bürünme saldırılarına karşı ek bir güvenlik koruması katmanı ekler, bu nedenle etkinleştirmenizi öneririz.

İlk kişi güvenlik ipucu ayrıca iletilerde **etkinleştir** (bu özellik hala kullanılabilse de) değeriyle **X-MS-Exchange-EnableFirstContactSafetyTip** adlı üst bilgiyi ekleyen posta akışı kuralları (aktarım kuralları olarak da bilinir) oluşturma gereksiniminin yerini alır.

> [!NOTE]
> İletinin birden çok alıcısı varsa, ipucunun gösterilip gösterilmediği ve kime çoğunluk modelini temel aldığı. Alıcıların çoğu gönderenden hiçbir zaman ileti almadıysa veya sık sık ileti almıyorsa, etkilenen alıcılar **bu iletiyi alan bazı kişiler...** ipucunu alır. Bu davranışın bir alıcının iletişim alışkanlıklarını başka bir alıcıyla açığa çıkardığından endişeleniyorsanız, ilk kişi güvenlik ipucu etkinleştirmemeli ve bunun yerine posta akışı kurallarını kullanmaya devam etmemelisiniz.

## <a name="exclusive-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365"></a>Office 365 için Microsoft Defender'de kimlik avı önleme ilkelerindeki özel ayarlar

Bu bölümde, yalnızca Office 365 için Defender'daki kimlik avı önleme ilkelerinde kullanılabilen ilke ayarları açıklanmaktadır.

> [!NOTE]
> Office 365 için Defender'daki varsayılan kimlik avı önleme ilkesi, tüm alıcılar için [kimlik sahtekarlığı koruması](set-up-anti-phishing-policies.md#spoof-settings) ve posta kutusu zekası sağlar. Ancak, diğer kullanılabilir [kimliğe bürünme koruması](#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365) özellikleri ve [gelişmiş ayarlar](set-up-anti-phishing-policies.md#advanced-phishing-thresholds-in-anti-phishing-policies-in-microsoft-defender-for-office-365) varsayılan ilkede yapılandırılmaz veya etkinleştirilmez. Tüm koruma özelliklerini etkinleştirmek için varsayılan kimlik avı önleme ilkesini değiştirin veya ek kimlik avı önleme ilkeleri oluşturun.

### <a name="impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365"></a>Office 365 için Microsoft Defender kimlik avı önleme ilkelerindeki kimliğe bürünme ayarları

Kimliğe bürünme, iletideki gönderenin veya gönderenin e-posta etki alanının gerçek bir gönderene veya etki alanına benzediği yerdir:

- Etki alanı contoso.com örnek bir kimliğe bürünme ćóntoso.com.
- Kullanıcı kimliğe bürünme, kullanıcının görünen adıyla e-posta adresinin birleşimidir. Örneğin, Valeria Barrios (vbarrios@contoso.com) Tamamen farklı bir e-posta adresiyle Valeria Barrios kimliğine bürünülebilir.

> [!NOTE]
> Kimliğe bürünme koruması benzer etki alanlarını arar. Örneğin, etki alanınız contoso.com ise, kimliğe bürünme girişimleri olarak farklı üst düzey etki alanlarını (.com, .biz vb.) ve hatta biraz benzer etki alanlarını da denetleriz. Örneğin, contosososo.com veya contoabcdef.com contoso.com kimliğe bürünme girişimi olarak görülebilir.

Kimliğine bürünülen bir etki alanı, alıcıları aldatmak dışında yasal (kayıtlı etki alanı, yapılandırılmış e-posta kimlik doğrulama kayıtları vb.) olarak kabul edilebilir.

Aşağıdaki kimliğe bürünme ayarları yalnızca Office 365 için Defender kimlik avı önleme ilkelerinde kullanılabilir:

- **Kullanıcıların korumasını sağlama**: Belirtilen iç veya dış e-posta adreslerinin **ileti gönderen olarak** kimliğine bürünülmesini engeller. Örneğin, şirketinizin Başkan Yardımcısı'ndan kendisine şirket içi bazı bilgiler göndermenizi isteyen bir e-posta iletisi alırsınız. Yapar mısın? Birçok kişi düşünmeden yanıt gönderirdi.

  Kimliğe bürünmeye karşı korumak amacıyla iç ve dış gönderen e-posta adresleri eklemek için korumalı kullanıcıları kullanabilirsiniz. Kullanıcının kimliğe bürünmesinden korunan **gönderenlerin** bu listesi, ilkenin geçerli olduğu **alıcı** listesinden farklıdır (varsayılan ilkenin tüm alıcıları; [Ortak ilke ayarları](#common-policy-settings) bölümündeki **Kullanıcılar, gruplar ve etki alanları** ayarında yapılandırılan belirli alıcılar).

  > [!NOTE]
  >
  > - Her kimlik avı önleme ilkesinde en fazla 350 korumalı kullanıcı (gönderen e-posta adresleri) belirtebilirsiniz. Birden çok ilkede aynı korumalı kullanıcıyı belirtemezsiniz. Bu nedenle, alıcıya kaç ilke uygulandığından bağımsız olarak, her bir alıcı için en fazla korunan kullanıcı (gönderen e-posta adresi) sayısı 350'dir. İlke önceliği ve ilke işlemenin ilk ilke uygulandıktan sonra nasıl durdurulacağı hakkında daha fazla bilgi için bkz [. E-posta korumasının sırası ve önceliği](how-policies-and-protections-are-combined.md).
  > - Kullanıcı kimliğe bürünme koruması, gönderen ve alıcı daha önce e-posta yoluyla iletişim kurarsa çalışmaz. Gönderen ve alıcı e-posta yoluyla hiç iletişim kurmadıysa, ileti bir kimliğe bürünme girişimi olarak tanımlanır.

  Varsayılan olarak, **Kullanıcılar'da korunacak** kimliğe bürünme koruması için hiçbir gönderen e-posta adresi yapılandırılmaz. Bu nedenle varsayılan olarak, varsayılan ilkede veya özel ilkelerde hiçbir gönderen e-posta adresi kimliğe bürünme koruması kapsamında değildir.

  **Kullanıcılar listesine korumak için** iç veya dış e-posta adresleri eklediğinizde, bu **gönderenlerden** gelen iletiler kimliğe bürünme koruma denetimlerine tabidir. İleti, **ilkenin geçerli** olduğu bir **alıcıya** (varsayılan ilkenin tüm alıcıları; Özel ilkelerdeki **kullanıcılar, gruplar ve etki alanları** alıcıları). Gönderenin e-posta adresinde kimliğe bürünme algılanırsa, kullanıcılar için kimliğe bürünme koruma eylemleri iletiye uygulanır (iletiyle ne yapmalı, kimliğine bürünülen kullanıcıların güvenlik ipuçlarının gösterilip gösterilmeyeceğini vb.).

- **Etki alanlarını korumayı etkinleştir**: Belirtilen etki alanlarının **ileti gönderenin etki alanında kimliğine** bürünülmesini engeller. Örneğin, sahip olduğunuz tüm etki alanları ([kabul edilen etki alanları](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains)) veya belirli özel etki alanları (sahip olduğunuz etki alanları veya iş ortağı etki alanları). Kimliğe bürünmeyle korunan **gönderen etki alanlarının** bu listesi, ilkenin geçerli olduğu **alıcı** listesinden farklıdır (varsayılan ilkenin tüm alıcıları; [Ortak ilke ayarları](#common-policy-settings) bölümündeki **Kullanıcılar, gruplar ve etki alanları** ayarında yapılandırılan belirli alıcılar).

  > [!NOTE]
  > Her kimlik avı önleme ilkesinde en fazla 50 özel etki alanı belirtebilirsiniz.

  Varsayılan olarak, Etki alanlarının **korunmasını etkinleştirme** bölümünde hiçbir gönderen etki alanı kimliğe bürünme koruması için yapılandırılmaz. Bu nedenle varsayılan olarak, varsayılan ilkede veya özel ilkelerde hiçbir gönderen etki alanı kimliğe bürünme koruması kapsamında değildir.

  Etki alanlarını **korumak için etkinleştir listesine etki alanları** eklediğinizde, **bu etki alanlarındaki gönderenlerden** gelen iletiler kimliğe bürünme koruması denetimlerine tabidir. İleti, **ilkenin geçerli** olduğu bir **alıcıya** (varsayılan ilkenin tüm alıcıları; Özel ilkelerdeki **kullanıcılar, gruplar ve etki alanları** alıcıları). Gönderenin etki alanında kimliğe bürünme algılanırsa, etki alanları için kimliğe bürünme koruma eylemleri iletiye uygulanır (iletiyle ne yapmalı, kimliğine bürünülen kullanıcıların güvenlik ipuçlarının gösterilip gösterilmeyeceğini vb.).

- **Eylemler**: İlkedeki korumalı kullanıcılara ve korumalı etki alanlarına karşı kimliğe bürünme girişimleri içeren gelen iletilerde gerçekleştirilen eylemi seçin. Korumalı kullanıcıların kimliğe bürünülmesi ve korumalı etki alanlarının kimliğe bürünülmesi için farklı eylemler belirtebilirsiniz:
  - **Hiçbir eylem uygulama**
  - **İletiyi diğer e-posta adreslerine yeniden yönlendirme**: İletiyi hedeflenen alıcılar yerine belirtilen alıcılara gönderir.
  - **İletileri alıcıların Gereksiz E-posta klasörlerine taşıma**: İleti posta kutusuna teslim edilir ve Gereksiz E-posta klasörüne taşınır. Daha fazla bilgi için bkz[. Microsoft 365'da Exchange Online posta kutularında gereksiz e-posta ayarlarını yapılandırma](configure-junk-email-settings-on-exo-mailboxes.md).
  - **İletiyi karantinaya** al: İletiyi hedeflenen alıcılar yerine karantinaya gönderir. Karantina hakkında bilgi için aşağıdaki makalelere bakın:
    - [Microsoft 365'de karantinaya alın](quarantine-email-messages.md)
    - [karantinaya alınan iletileri ve dosyaları Microsoft 365'da yönetici olarak yönetme](manage-quarantined-messages-and-files.md)
    - [karantinaya alınan iletileri Microsoft 365'de kullanıcı olarak bulma ve bırakma](find-and-release-quarantined-messages-as-a-user.md)

    **İletiyi karantinaya al'ı** seçerseniz, kullanıcı kimliğe bürünme veya etki alanı kimliğe bürünme koruması tarafından karantinaya alınan iletilere uygulanan karantina ilkesini de seçebilirsiniz. Karantina ilkeleri, kullanıcıların karantinaya alınan iletilere neler yapabileceğini tanımlar. Daha fazla bilgi için bkz [. Karantina ilkeleri](quarantine-policies.md).

  - **İletiyi teslim edin ve Gizli satırına başka adresler ekleyin**: İletiyi hedeflenen alıcılara teslim edin ve iletiyi belirtilen alıcılara sessizce teslim edin.
  - **İleti teslim etmeden önce silin**: Tüm ekler dahil olmak üzere iletinin tamamını sessizce siler.

- **Kimliğe bürünme güvenliği ipuçları: Kimliğe** bürünme denetimlerinde başarısız olan iletiler görünecek aşağıdaki kimliğe bürünme güvenliği ipuçlarını açın veya kapatın:
  - **Kimliğine bürünülen kullanıcılar için ipucunu göster**: Kimden adresi **, Kullanıcıların kullanıcıyı korumasını sağla** seçeneğini içerir. Yalnızca **Kullanıcıların korumasını etkinleştir** seçeneği açık ve yapılandırılmışsa kullanılabilir.
  - **Kimliğine bürünülen etki alanları için ipucunu göster**: Kimden adresi etki **alanını korumak için etki alanlarını etkinleştir'i** içerir. Yalnızca **Korumak için etki alanlarını etkinleştir** seçeneği açık ve yapılandırılmışsa kullanılabilir.
  - **Olağan dışı karakterler için ipucu göster**: Kimden adresi, kullanıcıların göndereni **korumasını sağlama** veya **Etki alanlarını** gönderen etki alanını korumak için etkinleştir içindeki olağan dışı karakter kümeleri (örneğin, matematiksel simgeler ve metinler veya büyük ve küçük harf karışımı) içerir.  Yalnızca **Kullanıcıların korumasını etkinleştir** _veya_ **Etki alanlarını korumayı etkinleştir** seçeneği açık ve yapılandırılmışsa kullanılabilir.

- **Posta kutusu zekasını etkinleştirme**: Sık kişileriyle kullanıcı e-posta desenlerini belirleyen yapay zekayı (AI) etkinleştirir veya devre dışı bırakır. Bu ayar, yapay zekanın iletileri meşru ve kimliğine bürünülen gönderenlerden ayırt etmesine yardımcı olur.

  Örneğin, Gabriela Laureano (glaureano@contoso.com) şirketinizin CEO'su olduğundan, **onu Kullanıcıların ilke ayarlarını korumasını sağlama** bölümüne korumalı gönderen olarak eklersiniz. Ancak, ilkenin geçerli olduğu bazı alıcılar aynı zamanda Gabriela Laureano (glaureano@fabrikam.com) adlı bir satıcıyla düzenli olarak iletişim kurmak için geçerlidir. Bu alıcıların glaureano@fabrikam.com ile bir iletişim geçmişi olduğundan, posta kutusu yönetim bilgileri glaureano@fabrikam.com gelen iletileri bu alıcılar için glaureano@contoso.com kimliğe bürünme girişimi olarak tanımlamaz.

  Kullanıcıların kimliğe bürünme saldırılarına karşı korunmasına yardımcı olmak için posta kutusu zekası tarafından öğrenilen (ve olmayan) sık kullanılan kişileri kullanmak için, **Posta kutusu** zekasını etkinleştir'i açtıktan sonra **Akıllı zeka kimliğe bürünme korumasını etkinleştir'i** açabilirsiniz.

- **Akıllı zeka kimliğe bürünme korumasını etkinleştirme**: Posta kutusu yönetim bilgileri sonuçlarından kimliğe bürünme algılamaları için iletilerde gerçekleştirilen eylemi belirtmek için bu ayarı açın:
  - **Herhangi bir eylem uygulamayın**: Bu değerin **, Posta kutusu zekasını** açmakla ancak **Akıllı zeka kimliğe bürünme korumasını etkinleştir'i** kapatmakla aynı sonucu aldığına dikkat edin.
  - **İletiyi diğer e-posta adreslerine yeniden yönlendirme**
  - **İletiyi alıcıların Gereksiz E-posta klasörlerine taşıma**
  - **İletiyi karantinaya al**: Bu eylemi seçerseniz, posta kutusu yönetim bilgileri koruması tarafından karantinaya alınan iletilere uygulanan karantina ilkesini de seçebilirsiniz. Karantina ilkeleri, kullanıcıların karantinaya alınan iletilere neler yapabileceğini ve kullanıcıların karantina bildirimleri alıp almayacağını tanımlar. Daha fazla bilgi için bkz [. Karantina ilkeleri](quarantine-policies.md).
  - **İletiyi teslim etme ve Gizli satırına başka adresler ekleme**
  - **İleti teslim etmeden önce silme**

- **Güvenilen gönderenler ve etki alanları ekleme**: Kimliğe bürünme koruması ayarlarına özel durumlar. Belirtilen gönderenlerden ve gönderen etki alanlarından gelen iletiler hiçbir zaman ilke tarafından kimliğe bürünme tabanlı saldırılar olarak sınıflandırılmamaktadır. Başka bir deyişle, korumalı gönderenler, korumalı etki alanları veya posta kutusu zekası koruması eylemi bu güvenilir gönderenlere veya gönderen etki alanlarına uygulanmaz. Bu listeler için en yüksek sınır 1024 giriştir.

### <a name="advanced-phishing-thresholds-in-anti-phishing-policies-in-microsoft-defender-for-office-365"></a>Office 365 için Microsoft Defender kimlik avı önleme ilkelerindeki gelişmiş kimlik avı eşikleri

Aşağıdaki gelişmiş kimlik avı eşikleri yalnızca Office 365 için Defender kimlik avı önleme ilkelerinde kullanılabilir. Bu eşikler, kimlik avı kararını belirlemek için iletilere makine öğrenmesi modelleri uygulama duyarlılığını denetler:

- **1 - Standart**: Bu varsayılan değerdir. İletide gerçekleştirilen eylemin önem derecesi, iletinin kimlik avı (düşük, orta, yüksek veya çok yüksek güvenilirlik) olduğuna ilişkin güven derecesine bağlıdır. Örneğin, çok yüksek güvenilirlik düzeyine sahip kimlik avı olarak tanımlanan iletiler en ciddi eylemler uygulanırken, düşük güvenilirlik düzeyine sahip kimlik avı olarak tanımlanan iletilere daha az ciddi eylemler uygulanır.
- **2 - Agresif**: Yüksek güvenilirlik düzeyine sahip kimlik avı olarak tanımlanan iletiler, çok yüksek bir güven derecesiyle tanımlanmış gibi ele alınır.
- **3 - Daha agresif**: Orta veya yüksek düzeyde güven ile kimlik avı olarak tanımlanan iletiler, çok yüksek bir güven derecesiyle tanımlanmış gibi ele alınır.
- **4 - En agresif**: Düşük, orta veya yüksek güvenilirlik düzeyine sahip kimlik avı olarak tanımlanan iletiler, çok yüksek bir güven derecesiyle tanımlanmış gibi ele alınır.

Bu ayarı artırdıkça hatalı pozitif sonuçların (iyi iletilerin kötü olarak işaretlenme olasılığı) artar. Önerilen ayarlar hakkında bilgi için Office 365 için Microsoft Defender [ayarlarındaki kimlik avı önleme ilkesine](recommended-settings-for-eop-and-office365.md#anti-phishing-policy-settings-in-microsoft-defender-for-office-365) bakın.
