---
title: Kimlik sahtekarlığına karşı koruma
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: overview
search.appverid:
- MET150
ms.assetid: d24bb387-c65d-486e-93e7-06a4f1a436c0
ms.collection:
- M365-security-compliance
- Strat_O365_IP
- m365initiative-defender-office365
ms.custom:
- TopSMBIssues
- seo-marvel-apr2020
ms.localizationpriority: high
description: Yöneticiler, kimlik sahtekarlığı yapan gönderenlerden ve etki alanlarından gelen kimlik avı saldırılarına karşı azaltmaya yardımcı olabilecek Exchange Online Protection (EOP) içinde bulunan kimlik sahtekarlığı önleme özellikleri hakkında bilgi edinebilir.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 446b82d668041a476d748956008002c42a92a7f3
ms.sourcegitcommit: 9255a7e8b398f92d8dae09886ae95dc8577bf29a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2022
ms.locfileid: "65435467"
---
# <a name="anti-spoofing-protection-in-eop"></a>EOP'de kimlik sahtekarlığına karşı koruma

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Uygulandığı öğe**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Office 365 için Microsoft Defender plan 1 ve plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Exchange Online posta kutusu olmayan Exchange Online veya tek başına Exchange Online Protection (EOP) kuruluşlarında posta kutuları olan Microsoft 365 kuruluşlarda EOP, kuruluşunuzun sahte (sahte) gönderenlerden korunmasına yardımcı olacak özellikler içerir.

Söz konusu kullanıcılarını korumak olduğunda Microsoft, kimlik avı tehdidini ciddiye alır. Kimlik sahtekarlığına, saldırganlar tarafından kullanılan yaygın bir tekniktir. **Sahte iletiler, gerçek kaynaktan başka bir yerden veya birinden geliyor gibi görünür**. Bu teknik genellikle kullanıcı kimlik bilgilerini almak için tasarlanmış kimlik avı kampanyalarında kullanılır. EOP'deki kimlik sahtekarlığı önleme teknolojisi özellikle ileti gövdesindeki Kimden üst bilgisinin sahteliğini inceler (e-posta istemcilerinde ileti göndereni görüntülemek için kullanılır). EOP, Kimden üst bilgisinin sahte olduğuna yüksek güvene sahip olduğunda, ileti sahte olarak tanımlanır.

Aşağıdaki kimlik sahtekarlığı önleme teknolojileri EOP'de kullanılabilir:

- **E-posta kimlik doğrulaması**: Kimlik sahtekarlığı önleme çalışmalarının ayrılmaz bir parçası, DNS'de SPF, DKIM ve DMARC kayıtları tarafından e-posta kimlik doğrulamasının (e-posta doğrulaması olarak da bilinir) kullanılmasıdır. Hedef e-posta sistemlerinin etki alanlarınızdaki gönderenlerden geldiğini iddia eden iletilerin geçerliliğini denetleyebilmesi için etki alanlarınız için bu kayıtları yapılandırabilirsiniz. Gelen iletiler için Microsoft 365 gönderen etki alanları için e-posta kimlik doğrulaması gerektirir. Daha fazla bilgi için bkz. [Microsoft 365'de e-posta kimlik doğrulaması](email-validation-and-authentication.md).

  EOP, standart e-posta kimlik doğrulama yöntemleri ve gönderen saygınlığı tekniklerinin birleşimiyle kimliği doğrulanamadı iletileri analiz eder ve engeller.

  :::image type="content" source="../../media/eop-anti-spoofing-protection.png" alt-text="EOP kimlik sahtekarlığı önleme denetimleri" lightbox="../../media/eop-anti-spoofing-protection.png":::

- **Sahte zeka içgörüleri**: Son 7 gün içinde iç ve dış etki alanlarındaki gönderenlerden gelen sahte iletileri gözden geçirin ve bu gönderenlere izin verin veya bunları engelleyin. Daha fazla bilgi için bkz [. EOP'de sahte zeka içgörüleri](learn-about-spoof-intelligence.md).

- **Kiracı İzin Ver/Engelle Listesi'nde sahte gönderenlere izin ver veya engelle**: Sahte zeka içgörülerinde kararı geçersiz kıldığınızda, sahtekar gönderen yalnızca Kiracı İzin Ver/Engelle Listesi'ndeki Kimlik **Sahtekarı** sekmesinde görünen el ile izin verme veya engelleme girdisine dönüşür. Ayrıca kimlik sahtekarı gönderenler için kimlik sahtekarı zekası tarafından algılanana kadar el ile izin verme veya engelleme girdileri oluşturabilirsiniz. Daha fazla bilgi için bkz. [EOP'de Kiracı İzin Verme/Engelleme Listesini Yönetme](tenant-allow-block-list.md).

- **Kimlik avı önleme ilkeleri**: EOP ve Office 365 için Microsoft Defender kimlik avı önleme ilkeleri aşağıdaki kimlik sahtekarlığı önleme ayarlarını içerir:
  - Kimlik sahtekarı zekasını açın veya kapatın.
  - Outlook kimliği doğrulanmamış gönderen göstergelerini açın veya kapatın.
  - Engellenen sahte gönderenler için eylemi belirtin.

  Daha fazla bilgi için bkz. [Kimlik avı önleme ilkelerindeki kimlik sahtekarlığı ayarları](set-up-anti-phishing-policies.md#spoof-settings).

  **Not**: Office 365 için Defender kimlik avı önleme ilkeleri, **kimliğe bürünme** koruması dahil olmak üzere ek korumalar içerir. Daha fazla bilgi için bkz[. Office 365 için Microsoft Defender'da kimlik avı önleme ilkelerindeki özel kullanım ayarları](set-up-anti-phishing-policies.md#exclusive-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365).

- **Kimlik sahtekarlık algılamaları raporu**: Daha fazla bilgi için bkz. [Kimlik Sahtekarı Algılamaları raporu](view-email-security-reports.md#spoof-detections-report).

  **Not**: Office 365 için Defender kuruluşlar kimlik avı girişimleri hakkındaki bilgileri görüntülemek için Gerçek zamanlı algılamaları (Plan 1) veya Tehdit Gezgini'ni (Plan 2) de kullanabilir. Daha fazla bilgi için bkz. [tehdit araştırması ve yanıtı Microsoft 365](office-365-ti.md).

## <a name="how-spoofing-is-used-in-phishing-attacks"></a>Kimlik avı saldırılarında kimlik sahtekarlığı nasıl kullanılır?

Kimlik sahtekarlığına neden olan iletiler kullanıcılar için aşağıdaki olumsuz etkilere sahiptir:

- **Sahte iletiler kullanıcıları kandırır**: Sahte bir ileti, alıcıyı bir bağlantıya tıklayıp kimlik bilgilerini vermesi, kötü amaçlı yazılım indirmesi veya hassas içerikli bir iletiyi yanıtlaması (iş e-posta güvenliğinin aşılması veya BEC olarak bilinir) konusunda kandırabilir.

  Aşağıdaki ileti, kimlik sahtekarlığı gönderen msoutlook94@service.outlook.com kullanan bir kimlik avı örneğidir:

  ![service.outlook.com kimliğine bürünen kimlik avı iletisi.](../../media/1a441f21-8ef7-41c7-90c0-847272dc5350.jpg)

  Bu ileti service.outlook.com'den gelmedi, ancak saldırgan bunu yapmış gibi görünmesi için **Kimden** üst bilgi alanını yanıltmış. Bu, alıcıyı **parola değiştir** bağlantısına tıklayıp kimlik bilgilerini vermesi için kandırma girişimiydi.

  Aşağıdaki ileti, sahte e-posta etki alanı contoso.com kullanan bir BEC örneğidir:

  ![Kimlik avı iletisi - iş e-posta güvenliğinin aşılması.](../../media/da15adaa-708b-4e73-8165-482fc9182090.jpg)

  İleti yasal görünüyor, ancak gönderen sahte.

- **Kullanıcılar gerçek iletileri sahte iletilerle karıştırır**: Kimlik avı hakkında bilgi sahibi olan kullanıcılar bile gerçek iletiler ile sahte iletiler arasındaki farkları görmekte zorlanabilir.

  Aşağıdaki ileti, Microsoft Güvenlik hesabından gerçek bir parola sıfırlama iletisi örneğidir:

  ![Microsoft yasal parola sıfırlama.](../../media/58a3154f-e83d-4f86-bcfe-ae9e8c87bd37.jpg)

  İleti gerçekten Microsoft'tan geldi, ancak kullanıcılar şüpheli olmaya şartlandı. Gerçek parola sıfırlama iletisiyle sahte bir ileti arasındaki fark zor olduğundan, kullanıcılar iletiyi yoksayabilir, istenmeyen posta olarak bildirebilir veya iletiyi gereksiz yere kimlik avı olarak Microsoft'a bildirebilir.

## <a name="different-types-of-spoofing"></a>Farklı kimlik sahtekarlık türleri

Microsoft, iki farklı kimlik sahtekarı iletisi türünü birbirinden ayırt eder:

- **Kuruluş içi kimlik sahtekarlık**: _Kendinden kendine_ sahtekarlık olarak da bilinir. Örneğin:

  - Gönderen ve alıcı aynı etki alanındadır:
    > Kimden: chris@contoso.com <br> Son: michelle@contoso.com

  - Gönderen ve alıcı aynı etki alanının alt etki alanındadır:
    > Kimden: laura@marketing.fabrikam.com <br> Son: julia@engineering.fabrikam.com

  - Gönderen ve alıcı aynı kuruluşa ait farklı etki alanlarındadır (diğer bir ifadeyle, her iki etki alanı da aynı kuruluşta [kabul edilen etki alanları](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains) olarak yapılandırılır):
    > Kimden: gönderen @ microsoft.com <br> To: alıcı @ bing.com

    İstenmeyen posta botunun toplanmasını önlemek için e-posta adreslerinde boşluklar kullanılır.

  Kuruluş içi kimlik sahtekarlığına bağlı [olarak bileşik kimlik doğrulaması](email-validation-and-authentication.md#composite-authentication) başarısız olan iletiler aşağıdaki üst bilgi değerlerini içerir:

  `Authentication-Results: ... compauth=fail reason=6xx`

  `X-Forefront-Antispam-Report: ...CAT:SPOOF;...SFTY:9.11`

  - `reason=6xx` kuruluş içi kimlik sahtekarlığına işaret eder.

  - SFTY, iletinin güvenlik düzeyidir. 9 kimlik avı, .11 ise kuruluş içi kimlik sahtekarlığı gösterir.

- **Etki alanları arası kimlik sahtekarlık**: Gönderen ve alıcı etki alanları farklıdır ve birbirleriyle (dış etki alanları olarak da bilinir) hiçbir ilişkisi yoktur. Örneğin:
    > Kimden: chris@contoso.com <br> Son: michelle@tailspintoys.com

  Etki alanları arası kimlik sahtekarlığına bağlı [olarak bileşik kimlik doğrulaması](email-validation-and-authentication.md#composite-authentication) başarısız olan iletiler aşağıdaki üst bilgi değerlerini içerir:

  `Authentication-Results: ... compauth=fail reason=000/001`

  `X-Forefront-Antispam-Report: ...CAT:SPOOF;...SFTY:9.22`

  - `reason=000` , iletinin açık e-posta kimlik doğrulamasının başarısız olduğunu gösterir. `reason=001` , iletinin örtük e-posta kimlik doğrulamasının başarısız olduğunu gösterir.

  - `SFTY` iletinin güvenlik düzeyidir. 9 kimlik avı, .22 ise etki alanları arası kimlik sahtekarlığı gösterir.

> [!NOTE]
> ***compauth=fail reason=###** _ gibi bir ileti aldıysanız ve bileşik kimlik doğrulaması (compauth) ve kimlik sahtekarlığına ilişkin değerleri bilmeniz gerekiyorsa, bkz. [Microsoft 365* içinde _Anti istenmeyen posta iletisi üst bilgileri](anti-spam-message-headers.md). Ya da doğrudan [*neden*](anti-spam-message-headers.md) kodlarına gidin.

DMARC hakkında daha fazla bilgi için bkz. [Microsoft 365'de e-postayı doğrulamak için DMARC kullanma](use-dmarc-to-validate-email.md).

## <a name="problems-with-anti-spoofing-protection"></a>Kimlik sahtekarlığı önleme korumasıyla ilgili sorunlar

Posta listelerinin (tartışma listeleri olarak da bilinir) iletileri iletme ve değiştirme şekli nedeniyle kimlik sahtekarlığı önleme ile ilgili sorunları olduğu bilinmektedir.

Örneğin, Gabriela Laureano (glaureano@contoso.com) kuş izlemekle ilgileniyor, birdwatchers@fabrikam.com posta listesine katılıyor ve listeye aşağıdaki iletiyi gönderiyor:

> **Kaynak:** "Gabriela Laureano" \<glaureano@contoso.com\> <br> **Hedef:** Birdwatcher Tartışma Listesi \<birdwatchers@fabrikam.com\> <br> **Konu:** Mt'nin en üstünde mavi jay'lerin harika bir şekilde görüntülenmesi. Bu hafta daha yağmurlu <p> Bu hafta Mt.'den görüntülemeye göz atmak isteyen herkes Rainier?

Posta listesi sunucusu iletiyi alır, içeriğini değiştirir ve listenin üyelerine yeniden yürüter. Yeniden oynatılan ileti aynı Kimden adresine (glaureano@contoso.com) sahiptir, ancak konu satırına bir etiket eklenir ve iletinin altına bir alt bilgi eklenir. Bu tür değişiklikler posta listelerinde yaygındır ve kimlik sahtekarlığına yönelik hatalı pozitif sonuçlara neden olabilir.

> **Kaynak:** "Gabriela Laureano" \<glaureano@contoso.com\> <br> **Hedef:** Birdwatcher Tartışma Listesi \<birdwatchers@fabrikam.com\> <br> **Konu:** [BIRDWATCHERS] Mt.'nin üst kısmındaki mavi jaylerin harika bir şekilde görüntülenmesi. Bu hafta daha yağmurlu <p> Bu hafta Mt.'den görüntülemeye göz atmak isteyen herkes Rainier? <p> Bu ileti Birdwatchers Tartışma Listesi'ne gönderildi. İstediğiniz zaman abonelikten çıkabilirsiniz.

Posta listesi iletilerinin kimlik sahtekarlığı önleme denetimlerini geçirmesine yardımcı olmak için, posta listesini denetleyıp denetlemediğinize bağlı olarak aşağıdaki adımları uygulayın:

- Posta listesinin sahibi kuruluşunuzdır:

  - DMARC.org:[Posta listesini çalıştırıyorum ve DMARC ile birlikte çalışmak istiyorum, ne yapmalıyım?](https://dmarc.org/wiki/FAQ#I_operate_a_mailing_list_and_I_want_to_interoperate_with_DMARC.2C_what_should_I_do.3F)

  - Bu blog gönderisinde yer alan yönergeleri okuyun: [Hatalardan kaçınmak için posta listesi işleçlerinin DMARC ile birlikte çalışabilmesi için bir ipucu](/archive/blogs/tzink/a-tip-for-mailing-list-operators-to-interoperate-with-dmarc-to-avoid-failures).

  - ARC'ı desteklemek için posta listesi sunucunuza güncelleştirmeleri yüklemeyi göz önünde bulundurun, bkz <http://arc-spec.org>. .

- Kuruluşunuzun posta listesi yok:

  - Posta listesinin bakımcısından, posta listesinin geçiş yaptığı etki alanı için e-posta kimlik doğrulamasını yapılandırmasını isteyin.

    Yeterli gönderen etki alanı sahiplerine e-posta kimlik doğrulama kayıtlarını ayarlamaları gerektiğini yanıtladığında, eyleme geçmelerini sağlar. Microsoft, gerekli kayıtları yayımlamak için etki alanı sahipleriyle birlikte de çalışsa da, tek tek kullanıcılar istediğinde daha da fazla yardımcı olur.

  - İletileri Gelen Kutusu'na taşımak için e-posta istemcinizde gelen kutusu kuralları oluşturun. Ayrıca, yöneticilerinizden [EOP'deki kimlik bilgileri sahtekarlık içgörüleri](learn-about-spoof-intelligence.md) ve [Kiracı İzin Verme/Engelleme Listesini Yönetme](tenant-allow-block-list.md) bölümünde açıklandığı gibi geçersiz kılmaları yapılandırmalarını isteyebilirsiniz.

  - Posta listesinin meşru olarak davranması için geçersiz kılma oluşturmak için Kiracı İzin Ver/Engelle Listesi'ni kullanın. Daha fazla bilgi için bkz. [Kiracı İzin Ver/Engelle Listesi'nde Ekleme izin verir](manage-tenant-allows.md).

Diğer her şey başarısız olursa, iletiyi Microsoft'a hatalı pozitif olarak bildirebilirsiniz. Daha fazla bilgi için bkz. [İletileri ve dosyaları Microsoft'a bildirme](report-junk-email-messages-to-microsoft.md).

## <a name="considerations-for-anti-spoofing-protection"></a>Kimlik sahtekarlığına karşı koruma ile ilgili dikkat edilmesi gerekenler

Şu anda Microsoft 365'a ileti gönderen bir yöneticiyseniz, e-postanızın doğru şekilde doğrulandığından emin olmanız gerekir. Aksi takdirde, istenmeyen posta veya kimlik avı olarak işaretlenebilir. Daha fazla bilgi için bkz. [Kimliği doğrulanmamış e-posta gönderen geçerli gönderenler için çözümler](email-validation-and-authentication.md#solutions-for-legitimate-senders-who-are-sending-unauthenticated-email).

Tek bir kullanıcının (veya yöneticinin) Kasa Gönderenler listesindeki gönderenler, kimlik sahtekarlığına karşı koruma da dahil olmak üzere filtreleme yığınının bölümlerini atlar. Daha fazla bilgi için bkz. [Outlook Kasa Gönderenler](create-safe-sender-lists-in-office-365.md#use-outlook-safe-senders).

Yöneticiler izin verilen gönderen listelerini veya izin verilen etki alanı listelerini kullanmaktan kaçınmalıdır (mümkün olduğunda). Bu gönderenler tüm istenmeyen posta, kimlik sahtekarlığı ve kimlik avı korumasını ve ayrıca gönderen kimlik doğrulamasını (SPF, DKIM, DMARC) atlar. Daha fazla bilgi için bkz. [İzin verilen gönderen listelerini veya izin verilen etki alanı listelerini kullanma](create-safe-sender-lists-in-office-365.md#use-allowed-sender-lists-or-allowed-domain-lists).
