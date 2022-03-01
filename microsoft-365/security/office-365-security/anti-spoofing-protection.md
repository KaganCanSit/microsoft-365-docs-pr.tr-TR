---
title: Anti-spoing protection
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
description: Yöneticiler, Exchange Online Protection'de (EOP) bulunan kimlik avı saldırılarını ve kimlik avı saldırılarını önlemeye yardımcı olan kimlik sahteciliği önleme özellikleri hakkında bilgi edinebilirsiniz.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: b93f2e1543a70ca7b5dde8ab5e83d48fba5f5a5e
ms.sourcegitcommit: e246725b0935067aad886530d5178972c0f895d7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2021
ms.locfileid: "63012862"
---
# <a name="anti-spoofing-protection-in-eop"></a>EOP'de anti-poing protection

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Geçerli olduğu yer:**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [1. plan Office 365 plan 2 için Microsoft Defender](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Microsoft 365 kutusu olmayan Exchange Online ya da tek başına Exchange Online Protection (EOP) kuruluşlarında posta kutusu olan Exchange Online kuruluşlarında, EOP, kurumlarınızı sahte (sahte) gönderenlerden korumaya yardımcı olan özellikler içerir.

Microsoft, kullanıcılarını koruma konusunda kimlik avı tehdidini ciddiye alır. Poofing, saldırganlar tarafından kullanılan yaygın bir tekniktir. **Kodlu iletiler gerçek kaynaktan başka bir yerden veya bir yerden geliyor gibi görünür**. Bu teknik, çoğunlukla kullanıcı kimlik bilgilerini almak için tasarlanmış kimlik avı kampanyalarında kullanılır. EOP'de sahtecilik önleme teknolojisi, özellikle ileti gövdesinde Gönderen üstbilgisi sahtesi inceler (e-posta istemcilerde iletiyi göndereni görüntülemek için kullanılır). EOP'nin, From üstbilgilerinin sahtesi için yüksek bir güveni olduğunda, ileti sahte olarak tanımlanır.

EOP'de şu ifadeyi koruma teknolojileri kullanılabilir:

- **E-posta** kimlik doğrulaması: Kimlik kimlik doğrulaması e-posta kimlik doğrulamasının (e-posta doğrulaması olarak da bilinir) DNS'de SPF, DKIM ve DMARC kayıtları tarafından kullanımı e-posta kimlik doğrulamasının ayrılmaz bir parçasıdır. Etki alanlarınız için bu kayıtları yapılandırarak, hedef e-posta sistemlerinin etki alanlarınız içinde yer alan gönderenlerden olduğunu iddia eden iletilerin geçerliliğini denetlemesi için bunu yapılandırabilirsiniz. Gelen iletiler için, gönderen Microsoft 365 için e-posta kimlik doğrulaması gerekir. Daha fazla bilgi için bkz. [E-posta kimlik doğrulaması Microsoft 365](email-validation-and-authentication.md).

  EOP, standart e-posta kimlik doğrulama yöntemlerini ve gönderen itibarı tekniklerini birlikte kullanarak kimlik doğrulaması yapılamayacak iletileri analiz eder ve engeller.

  ![EOP kimliklerini önleme denetimleri.](../../media/eop-anti-spoofing-protection.png)

- **Akıllı ifade içgörü**: Son 7 gün içinde dahili ve dış etki alanlarındaki gönderenlerden gelen kimliği doğrun gönderilen iletileri gözden geçirme ve bu gönderenlere izin verme veya engelleme. Daha fazla bilgi için bkz [. EOP'de Spoof Intelligence içgörü](learn-about-spoof-intelligence.md).

- Kiracı İzin Ver/Engelleme Listesi'ne yer alan kimliği doğruya sahip gönderenlere izin verme veya engelleme: Bilgi bloğu içgörüsinde kararı geçersiz kıl kılıca, kimliği doğruya sahip gönderen, yalnızca Kiracı İzin Ver **/** Engelleme Listesi'nin Gizli Bilgi sekmesinde görüntülenen bir el ile izin verilen veya engellenen giriş haline gelir. Ayrıca, e-posta gönderenlere yönelik girişlere izin verme veya engellemeyi ayrıca, bu kişi kimliğin kimliği doğrulandığından önce el ile oluşturabilir veya engelleyebilirsiniz. Daha fazla bilgi için bkz [. EOP'de Kiracı İzin Ver/Engelleme Listesini Yönetme](tenant-allow-block-list.md).

- **Kimlik avı önleme ilkeleri**: EOP ve Office 365 için Microsoft Defender'da, kimlik avı önleme ilkeleri aşağıdaki kimlik sahtesi önleme ayarlarını içerir:
  - Akıllı ifadeyi açma veya kapatma.
  - Kimliği doğrulanmamış gönderen kimliğini Outlook veya kapatın.
  - Kimliği doğrun engellenen gönderenler eylemlerini belirtin.

  Daha fazla bilgi için bkz [. Kimlik avı önleme ilkelerde kimlik avı ayarları](set-up-anti-phishing-policies.md#spoof-settings).

  **Not**: Kimlik avı koruması ilkeleri için Defender'Office 365 kimliğe bürünme koruması da dahil olmak üzere ek **korumalar** içerir. Daha fazla bilgi için bkz[. Kimlik avı önleme ilkeleri için Microsoft Defender'da özel Office 365](set-up-anti-phishing-policies.md#exclusive-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365).

- **Spoof algılamaları raporu**: Daha fazla bilgi için bkz. [Spoof Algılamaları raporu](view-email-security-reports.md#spoof-detections-report).

  **Not**: Office 365 için Defender kuruluşlar kimlik avı girişimleriyle ilgili bilgileri görüntülemek üzere Gerçek zamanlı algılamaları (Plan 1) veya Tehdit Gezgini 'ni (Plan 2) de kullanabilir. Daha fazla bilgi için tehdit [Microsoft 365 yanıtını incelemeye bakın](office-365-ti.md).

## <a name="how-spoofing-is-used-in-phishing-attacks"></a>Kimlik avı saldırılarında kimlik sahtesi nasıl kullanılır

E-postalarda, kullanıcıları aşağıdaki negatif sonuçlar doğuran iletiler yer almaktadır:

- **Kandırılan** iletiler kullanıcıları kandırıyor: Kandırılan bir ileti alıcının bir bağlantıya tıklaması ve kimlik bilgilerini vermesi, kötü amaçlı yazılım indirmesi veya hassas içeriği olan bir iletiyi yanıtlaması için sizi aldatmasına neden olabilir (iş e-postası güvenliğinin tehlikeye atması veya BEC olarak bilinir).

  Aşağıdaki ileti, kimlik sahte olan gönderenin kimlik avını kullanan bir kimlik msoutlook94@service.outlook.com:

  ![Kimlik avı iletisi kimliğine bürünen service.outlook.com.](../../media/1a441f21-8ef7-41c7-90c0-847272dc5350.jpg)

  Bu ileti başka bir iletiden service.outlook.com, ancak saldırgan From üst bilgi alanını benzer şekilde yapmak için kopyalanmıştır. Bu, parola değiştirme bağlantısını tıklatması ve kimlik **bilgilerini vermesi için** alıcıyı kandırmaya çalışııydı.

  Aşağıdaki ileti, e-posta etki alanı e-posta adresinin kodlu olduğu e-posta adresini kullanan BEC contoso.com:

  ![Kimlik avı iletisi- iş e-postası tehlikeye at.](../../media/da15adaa-708b-4e73-8165-482fc9182090.jpg)

  İleti geçerli gibi görünüyor, ancak gönderen kimliği doğru değil.

- **Kullanıcılar gerçek iletileri sahte iletilerle karıştırır**: Kimlik avı hakkında bilgi alan kullanıcılar bile gerçek iletiler ile sahte iletiler arasındaki farkları görmekte zor olabilir.

  Aşağıdaki ileti, Microsoft Güvenlik hesabından gelen gerçek parola sıfırlama iletisi örneğidir:

  ![Microsoft'un geçerli parola sıfırlaması.](../../media/58a3154f-e83d-4f86-bcfe-ae9e8c87bd37.jpg)

  bu ileti aslında Microsoft'tan geldi, ancak kullanıcılar şüpheli olarak koşullandı. Gerçek parola sıfırlama iletisiyle sahte ileti arasındaki farkın zor olduğundan, kullanıcılar iletiyi yoksayma, istenmeyen posta olarak bildirme veya gereksiz yere iletiyi kimlik avı olarak Microsoft'a bildirmeyi neden olabilir.

## <a name="different-types-of-spoofing"></a>Farklı türlerdepoylama

Microsoft, iki farklı türki ifadeli e-postayı birbirinden ayırteder:

- **Intra-org'da yapılan bir ifade**: Kendi kendine yapılan _bulamama_ olarak da bilinir. Örneğin:

  - Gönderen ve alıcı aynı etki alanındadır:
    > Buradan: chris@contoso.com <br> Bunu yapmak için: michelle@contoso.com

  - Gönderen ve alıcı aynı etki alanının alt etki alanında yer almaktadır:
    > Buradan: laura@marketing.fabrikam.com <br> Bunu yapmak için: julia@engineering.fabrikam.com

  - Gönderen ve alıcı aynı kuruluşa ait olan farklı etki alanlarında yer alan (yani, her iki etki alanı da aynı kuruluşta [kabul](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains) edilen etki alanları olarak yapılandırılır):
    > Gönderen: gönderen @ microsoft.com <br> To: recipient @ bing.com

    E-posta adreslerinde boşluklar, istenmeyen posta toplamasını önlemek için kullanılır.

  Kuruluş içi [kimlik doğrulaması nedeniyle](email-validation-and-authentication.md#composite-authentication) bileşik kimlik doğrulaması başarısız olan iletiler aşağıdaki üst bilgi değerlerini içerir:

  `Authentication-Results: ... compauth=fail reason=6xx`

  `X-Forefront-Antispam-Report: ...CAT:SPOOF;...SFTY:9.11`

  - `reason=6xx` , şirket içi yapılan e-postalarda yapılan bire bir ifadedir.

  - SFTY, iletinin güvenlik düzeyidir. 9 kimlik avını, 0,11 değeri de kuruluş içi kimlik sahte işaretlerini gösterir.

- **Etki alanları arasında yapılan kimliğin** kimliği: Gönderen ve alıcı etki alanları farklıdır ve bu etki alanlarıyla hiçbir ilişkisi yoktur (dış etki alanları olarak da bilinir). Örneğin:
    > Buradan: chris@contoso.com <br> Bunu yapmak için: michelle@tailspintoys.com

  Etki alanı [kimlik doğrulamasından](email-validation-and-authentication.md#composite-authentication) dolayı bileşik kimlik doğrulaması başarısız olan iletiler aşağıdaki üst bilgi değerlerini içerir:

  `Authentication-Results: ... compauth=fail reason=000/001`

  `X-Forefront-Antispam-Report: ...CAT:SPOOF;...SFTY:9.22`

  - `reason=000` ileti açık e-posta kimlik doğrulamasında başarısız olduğunu gösterir. `reason=001` ileti, örtülü e-posta kimlik doğrulamasının başarısız olduğunu gösterir.

  - `SFTY` iletinin güvenlik düzeyidir. 9 kimlik avını, .22 çapraz etki alanı kimlik avını gösterir.

> [!NOTE]
> ***compauth=fail reason=###** _ gibi bir ileti aldıysanız ve bileşik kimlik doğrulama (compauth) hakkında bilginiz olması ve kimlik doğrulamasıyla ilgili değerler hakkında bilginiz olması gerekirse, [Microsoft 365* üzerinde _Anti-spam](anti-spam-message-headers.md) ileti üstbilgileri konusuna bakın. Doğrudan neden kodlarına [*da gidebilirsiniz*](anti-spam-message-headers.md) .

DMARC hakkında daha fazla bilgi için bkz[. DMARC kullanarak e-postayı doğrulamak için Microsoft 365](use-dmarc-to-validate-email.md).

## <a name="problems-with-anti-spoofing-protection"></a>Poing anti-spoing protection ile ilgili sorunlar

Posta listeleri (tartışma listeleri olarak da bilinir), iletileri iletme ve değiştirme yollarına bağlı olarak, parolayı korumayla ilgili sorunlar olduğu bilinmektedir.

Örneğin, Sila Laureano (glaureano@contoso.com) kuş izleme ile ilgileniyor, birdwatchers@fabrikam.com listesine katılır ve aşağıdaki iletiyi listeye gönderir:

> **Kaynak:** "Gabriela Laureano" \<glaureano@contoso.com\> <br> **Hedef:** Birdwatcher'ın Tartışma Listesi \<birdwatchers@fabrikam.com\> <br> **Konu:** Mt'nin en üstünde mavi koyu koyulardan harika görüntü. Bu hafta Rainier <p> Bu haftayı Mt'den görüntülemek isteyen herkes. Rainier?

Posta listesi sunucusu iletiyi alır, içeriğini değiştiren ve liste üyelerine yeniden gösterir. Yeniden oynatilen iletide Aynı From adresi (glaureano@contoso.com) vardır, ancak konu satırına etiket eklenir ve iletinin en altına bir alt bilgi eklenir. Bu tür değişiklikler posta listelerinde yaygındır ve kimlik sahtesi için hatalı pozitif sonuçlarla sonuçlandırabilirsiniz.

> **Kaynak:** "Gabriela Laureano" \<glaureano@contoso.com\> <br> **Hedef:** Birdwatcher'ın Tartışma Listesi \<birdwatchers@fabrikam.com\> <br> **Konu:** [BIRDWATCHERS] Mt'ın en üstünde mavi mavi koyulardan harika görüntü. Bu hafta Rainier <p> Bu haftayı Mt'den görüntülemek isteyen herkes. Rainier? <p> Bu ileti Birdwatchers Tartışma Listesi'ne gönderildi. Aboneliğinizi her zaman kaldırabilirsiniz.

Posta listesi iletilerinin kimlik kimlik bilgileri denetimlerini geçmesine yardımcı olmak için, posta listesinin denetim altına alındı olup olmadığını temel alarak aşağıdaki adımları uygulayın:

- Posta listesinin sahibi, şu şekildedir:

  - DMARC ile birlikte DMARC.org: Bir posta listesi işletmek ve DMARC ile birlikte olmak istiyorum [, ne yapabilirim?](https://dmarc.org/wiki/FAQ#I_operate_a_mailing_list_and_I_want_to_interoperate_with_DMARC.2C_what_should_I_do.3F) bağlantısında SSS bölümünü inceleyin.

  - Bu blog gönderisi'nde verilen yönergeleri okuyun: Hatalardan kaçınmak için posta listesi işleçleriyle [DMARC'nin birlikte çalışabilmesi için bir ipucu](/archive/blogs/tzink/a-tip-for-mailing-list-operators-to-interoperate-with-dmarc-to-avoid-failures).

  - ARC'i desteklemek için posta listesi sunucunuza güncelleştirmeleri yüklemeyi göz önünde bulundurabilirsiniz, bkz <http://arc-spec.org>.

- Posta listesi, kuruma ait değil:

  - Posta listesinin yöneticisinden, posta listesinin geçiş yapılan etki alanı için e-posta kimlik doğrulamasını yapılandırmasını sorun.

    Yeterli gönderen etki alanı sahiplerine yanıt verdiklerinden, e-posta kimlik doğrulama kayıtlarını ayarlamaları gerekir. Bu, onları önlem almaya teşvik ediyor. Microsoft gerekli kayıtları yayımlamak için etki alanı sahipleriyle birlikte çalışıyor olsa da, tek tek kullanıcılar istekte olduğunda daha da fazla yardımcı olur.

  - İletileri Gelen Kutusu'na taşımak için e-posta istemcisinde gelen kutusu kuralları oluşturun. Ayrıca, yöneticilerinizin [EOP'de Kimlik](learn-about-spoof-intelligence.md) Hesabı bilgisinde ve Kiracı İzin Ver/Engelleme Listesini Yönetme konusunda açıklandığı gibi geçersiz kılmaları [yapılandırmalarını da sebilirsiniz](tenant-allow-block-list.md).

  - Posta listesinin bunu geçerli olarak kabul etmek üzere geçersiz k olmasına neden olacak bir geçersiz kılma oluşturmak için Kiracı İzin Ver/Engelle Listesini kullanın. Daha fazla bilgi için bkz [. Kiracı İzin Ver/Engelleme Listesi'ne izin ekleme](manage-tenant-allows.md).

Diğer her şey başarısız olursa, iletiyi Microsoft'a hatalı bir pozitif sonuç olarak bildirebilirsiniz. Daha fazla bilgi için bkz [. İletileri ve dosyaları Microsoft'a bildirme](report-junk-email-messages-to-microsoft.md).

## <a name="considerations-for-anti-spoofing-protection"></a>Poing protection ile ilgili dikkat edilmesi gereken noktalar

Şu anda e-posta iletileri gönderen bir yöneticiyseniz Microsoft 365 e-posta adresinizin doğru olduğundan emin olun. Aksi takdirde, istenmeyen posta veya kimlik avı olarak işaretlenir. Daha fazla bilgi için bkz [. Kimliği doğrulanmamış e-posta gönderen geçerli gönderenler için çözümler](email-validation-and-authentication.md#solutions-for-legitimate-senders-who-are-sending-unauthenticated-email).

Tek bir kullanıcının (veya yöneticinin) veya yöneticisinin Kasa Gönderenler listesi, kimliksüz koruma da içinde olmak üzere filtreleme yığınının bölümlerini atlar. Daha fazla bilgi için bkz[. Outlook Kasa Gönderenler'e bakın](create-safe-sender-lists-in-office-365.md#use-outlook-safe-senders).

Yöneticiler izin verilen gönderenler listelerini veya izin verilen etki alanı listelerini kullanmaktan kaçınılmalıdır (mümkün olduğunda). Bu gönderenler tüm istenmeyen posta, kimlik sahteciliği ve kimlik avı korumasının yanı sıra gönderen kimlik doğrulamasını (SPF, DKIM, DMARC) atlar. Daha fazla bilgi için bkz [. İzin verilen gönderenler listelerini veya izin verilen etki alanı listelerini kullanma](create-safe-sender-lists-in-office-365.md#use-allowed-sender-lists-or-allowed-domain-lists).
