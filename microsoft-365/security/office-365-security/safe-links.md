---
title: Windows için Kasa Defender ile ilgili tüm bağlantılar'a Office 365
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: Admin
ms.topic: overview
f1_keywords:
- "197503"
ms.date: 09/08/2021
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
- m365initiative-defender-office365
ms.custom:
- seo-marvel-apr2020
search.appverid:
- MET150
- MOE150
- ZVO160
- ZXL160
- ZPP160
- ZWD160
ms.assetid: dd6a1fef-ec4a-4cf4-a25a-bb591c5811e3
description: Bir kuruluşu Kasa ve kötü amaçlı URL'ler kullanan diğer saldırılara karşı korumak için Office 365 için Defender'daki Bağlantılar koruması hakkında bilgi edinebilirsiniz. Bağlantıları Teams Kasa ve Bağlantı iletilerinin Kasa bakın.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: fc043da2763bf6984062bec903e4f2df7bd6d10d
ms.sourcegitcommit: cde34d38bdfb6335b980f1c48c6b218da6a64bf8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/20/2022
ms.locfileid: "63014083"
---
# <a name="safe-links-in-microsoft-defender-for-office-365"></a>Kasa için Microsoft Defender'daki Office 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Geçerli olduğu yer:**
- [1. plan Office 365 plan 2 için Microsoft Defender](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

> [!IMPORTANT]
> Bu makale, Microsoft [Defender'a sahip iş müşterileri için Office 365](defender-for-office-365.md). Outlook.com, Microsoft 365 Aile veya Microsoft 365 Bireysel kullanıyorsanız ve Outlook'de Safelinks hakkında bilgi arıyorsanız, bkz. Gelişmiş [Outlook.com güvenliği](https://support.microsoft.com/office/882d2243-eab9-4545-a58a-b36fee4a46e2).

Kasa Bağlantıları[, Office 365 için Defender'ın](defender-for-office-365.md) posta akışında gelen e-posta iletileri için URL taraması ve yeniden yazma, e-posta iletileri ve diğer konumlarda URL'ler ile bağlantıların zaman tıklamalı doğrulaması sağlayan bir özelliğidir. Kasa Tarama, Exchange Online Protection'de (EOP) gelen [e-posta](anti-spam-and-anti-malware-protection.md) iletisinde normal istenmeyen posta önleme ve kötü amaçlı yazılımdan korumanın yanı sıra gerçekleşir. Kasa Tarama, kimlik avı ve diğer saldırılarda kullanılan kötü amaçlı bağlantılardan korunmanıza yardımcı olabilir.

Kasa Bağlantılar koruması aşağıdaki konumlarda kullanılabilir:

- **E-posta** iletileri: Varsayılan bağlantı Kasa olmasına rağmen, yerleşik koruma önceden ayarlanmış güvenlik ilkesi  tüm alıcılara Kasa Bağlantıları koruması sağlar (özel Bağlantılar ilkeleri içinde tanımlanmamış Kasa kullanıcılar). Daha fazla bilgi için bkz[. İlke için EOP'de ve Microsoft Defender'da önceden Office 365](preset-security-policies.md). Belirli kullanıcılara, Kasa veya etki alanlarına uygulanacak bağlantılar ilkeleri de oluşturabilirsiniz. Yönergeler için bkz[. Kasa Office 365 için Microsoft Defender'da Bağlantılar Office 365](set-up-safe-links-policies.md).

  E-posta iletileri için Kasa koruması hakkında daha fazla bilgi için, [bu makalenin devam Kasa E-posta iletileri](#safe-links-settings-for-email-messages) için bağlantı ayarları bölümüne bakın.
  
  > [!NOTE]
  > Kasa Posta özelliği etkin ortak klasörlerde Bağlantılar çalışmıyor.

- **Microsoft Teams**: Kasa, grup sohbeti Teams kanallarında yer alan bağlantılar için Bağlantılar koruması da Kasa tarafından kontrol edilir.

  E-posta Kasa Bağlantılar Teams hakkında daha fazla bilgi için, bu [Kasa](#safe-links-settings-for-microsoft-teams) sonraki Microsoft Teams Bağlantılar ayarları bölümüne bakın.

- **Office 365: Kasa** uygulamaları için bağlantılar Office 365, desteklenen masaüstü, mobil ve web uygulamaları içinde kullanılabilir. Bağlantılar **Kasa** dışında genel Office 365 ayarları içinde yer alan tüm uygulamalar için **Bağlantılar Kasa** yapılandırabilirsiniz. Yönergeler için bkz. [Windows için Microsoft Defender'Kasa Bağlantılar ayarları için genel Office 365](configure-global-settings-for-safe-links.md).

  Kasa Office 365 için Bağlantılar koruması, kullanıcıların etkin Office 365 Bağlantıları ilkelerine dahil olup olmadığı bağımsız olarak, kuruluşta Office 365 için Defender lisansı olan tüm kullanıcılara Kasa uygulanır.

  Bu uygulamalarda Kasa Bağlantılar Office 365 hakkında daha fazla bilgi için, bu [makalenin](#safe-links-settings-for-office-365-apps) devam Kasa Uygulamaları için Office 365 Bağlantıları ayarları bölümüne bakın.

Bu makale, Bağlantı ayarları için aşağıdaki türlerde Kasa içerir:

- **Ayarlar Bağlantıları Kasa**: Bu ayarlar yalnızca belirli ilkelere dahil olan kullanıcılar için geçerlidir ve ayarlar ilkeler arasında farklı olabilir. Bu ayarlar şunlardır:

  - [Kasa iletileri için bağlantı ayarlarını değiştirme](#safe-links-settings-for-email-messages)
  - [Kasa bağlantıları ayarlarını Microsoft Teams](#safe-links-settings-for-microsoft-teams)
  - [Bağlantılar ilkelerinde "Aşağıdaki URL'leri yeniden Kasa" listeleri](#do-not-rewrite-the-following-urls-lists-in-safe-links-policies)

- **Genel Kasa Bağlantıları ayarları**: Bu ayarlar, Bağlantı ilkeleri içinde değil, Kasa yapılandırılır. Bu ayarlar şunlardır:

  - [Kasa uygulamaları için Bağlantılar Office 365 tıklayın](#safe-links-settings-for-office-365-apps)
  - [Yeni Bağlantılar için "Aşağıdaki URL'leri Kasa engelleme"](#block-the-following-urls-list-for-safe-links)

Aşağıdaki tabloda, Microsoft 365'Kasa ve Office 365 için Defender içeren Office 365 Bağlantıları ile ilgili senaryolar açık almaktadır (örneklerde lisansın olmamasının hiçbir zaman bir sorun olmadığı unutmayın).

<br>

****

|Senaryo|Sonuç|
|---|---|
|Konuşma, pazarlama departmanının bir üyesidir. Kasa için bağlantılar Office 365, Kasa Bağlantıları için genel ayarlarda ve pazarlama bölümü üyeleri için Kasa Bağlantılar ilkesi vardır. Her zaman, PowerPoint bir sunu açar ve ardından sunuda bir URL'ye tıklar.|Her zaman, Tüm bağlantılar Kasa korunur. <p> Ayrıca, her iki Grup Kasa da dahil edilir ve Kasa uygulamaları için Links Office 365 açık olur. <p> Office 365 uygulamalarına bağlantıları koruma Kasa hakkında daha fazla bilgi için, bu [makalenin](#safe-links-settings-for-office-365-apps) devam Kasa Uygulamaları için Office 365 Bağlantıları ayarları bölümüne bakın.|
|Chris'in Microsoft 365 E5 kuruluşunda hiçbir bağlantı Kasa yapılandırılmadı. Chris, sonunda tıklayt olduğu kötü amaçlı bir web sitesinin URL'sini içeren bir dış gönderenden e-posta alır.|Chris, bu sitenin Kasa değildir. <p> Bir yöneticinin, gelen e-Kasa iletilerinden bağlantıları koruma hakkında bilgi edin paylaş diğer tüm kullanıcılar için Kasa bir Bağlantılar ilkesi oluşturması gerekir. Chris'in, Bağlantı korumasını korumak için ilke Kasa olması gerekir.|
|Pat'in kuruluşunda, hiçbir yönetici Kasa Bağlantısı ilkeleri oluşturmaz ama Kasa uygulamaları için Bağlantılar Office 365 açık olur. Pat bir Word belgesi açar ve dosyada bir URL'ye tıklar.|Pat, Diğer Bağlantılar Kasa korunmaz. <p> Her Kasa için Bağlantılar koruması Office 365 genel olarak açık olsa da, Pat etkin Kasa Bağlantıları ilkelerine dahil değildir ve dolayısıyla koruma uygulanamamalıdır.|
|Lee'nin kuruluşunda, `https://tailspintoys.com` Bağlantı Ekleme Bağlantıları için genel ayarlarda yer alan aşağıdaki **URL'leri** engelle Kasa yapılandırılır. Zaten Lee Kasa içeren bir Bağlantı ilkesi var. Lee, URL'yi içeren bir e-posta iletisi alır `https://tailspintoys.com/aboutus/trythispage`. Lee URL'ye tıklar.|URL, Yılan için otomatik olarak engellenmiş olabilir; bu, listede yer alan URL girdisi ve Lee'nin kullandığı e-posta istemcisine bağlıdır. Daha fazla bilgi için, bu makalenin sonraki kısımlarında yer alan [Bağlantılar Kasa "Aşağıdaki URL'leri engelleme"](#block-the-following-urls-list-for-safe-links) listesine bakın.|
|Hem Murat hem de Abd'de contoso.com. Uzun zaman önce, yöneticiler hem Murat Kasa hem de Murat için geçerli olan Bağlantılar ilkelerini yapılandırdı. Can, e-postanın kötü amaçlı bir URL içerdiğini bilmeyebilirsiniz.|Her zaman, **Kasa arasındaki** iletilere uygulanacak şekilde yapılandırılan Kasa Bağlantılar ilkesi Bağlantılar tarafından korunur. Daha fazla bilgi için, bu [makalenin Kasa e-posta iletileri için](#safe-links-settings-for-email-messages) bağlantılar ayarları bölümüne bakın.|
|

## <a name="safe-links-settings-for-email-messages"></a>Kasa iletileri için bağlantı ayarlarını değiştirme

Kasa Bağlantılar, bilinen kötü amaçlı köprüler için gelen e-postaları tarar. Taranan URL'ler Microsoft standart URL ön eki kullanılarak yeniden yazılır: `https://nam01.safelinks.protection.outlook.com`. Bağlantı yeniden yazıldığında, kötü amaçlı olabilecek içerikler için analiz edilir.

Bağlantı Kasa bir URL'yi yeniden yazdikten sonra, ileti el ile iletilir veya yanıtlasa bile (hem iç  hem de dış alıcılara) URL yeniden yazılır. İletilen veya yanıtlandı iletisine eklenen ek bağlantılar yeniden yazılmaz. Bununla birlikte, Gelen Kutusu kuralları  veya SMTP iletme tarafından otomatik iletme durumunda, alıcı Kasa Bağlantıları tarafından korunmadıkça veya daha önceki bir iletişimde URL yeniden yazılmadıkça, son alıcıya yönelik  iletide URL yeniden yazılmaz. Bağlantılar Kasa olduğu sürece, yeniden yazılabilir veya yazılmasa da URL'ler teslim öncesinde taranır. Ayrıca, kaydırılmış URL'ler masaüstü için Outlook sürüm 16.0.12513 veya sonraki sürümlere tıklandırıldıklarında da istemci tarafı API çağrısı tarafından Kasa Bağlantıları tarafından denetlenir.

E-Kasa iletilerine uygulanacak bağlantılar ilkelerinin ayarları aşağıdaki listede açıklanmıştır:

- **İletilerde kötü amaçlı olabilecek bilinmeyen URL'ler için eylemi seçin: E-posta** iletisinde tarama Kasa bağlantılarını devre dışı bırakarak. Önerilen değer, **On'dır**. Bu ayarın açma, aşağıdaki eylemlerle sonuç verir.

  - Kasa Tarama, aynı dosya üzerinde Outlook (C2R) içinde Windows.
  - URL'ler yeniden yazılır ve kullanıcılar iletilerde URL'lere Kasa Bağlantılar koruması aracılığıyla yönlendirildi.
  - Tıklendiğinde, URL'ler bilinen kötü amaçlı URL'ler listesinde ve ["Aşağıdaki URL'leri engelle" listesinde denetlenir](#block-the-following-urls-list-for-safe-links).
  - Geçerli bir itibarı olmayan URL'ler arka planda zaman uyumsuz olarak yer almaktadır.

- **Şüpheli bağlantılar ve dosyaları** işaret alan bağlantılar için gerçek zamanlı URL tarama uygulama: İndirilebilir içeriğe işaret alan e-posta iletileri bağlantıları dahil olmak üzere, bağlantıların gerçek zamanlı olarak taranmalarını sağlar. Önerilen değer etkinleştirilir.
  - **İletiyi teslim etmek için URL tarama işleminin tamamlandıktan önce bekleyin**:
    - Etkin: URL içeren iletiler, tarama işlemi bitene kadar gerçekleştirilene kadar. İletiler ancak URL'lerin güvenli olarak onaylandıktan sonra teslim edilir. Bu, önerilen değerdir.
    - Devre Dışı: URL tarama tamamlanmadı ise iletiyi yine de teslim edin.

- **Posta Kasa Kuruluş** içinde gönderilen e-posta iletilerine bağlantılar: Kasa Bağlantıları, aynı kuruluş içinde iç gönderenler ve iç alıcılar arasında gönderilen iletilerde tarama özelliğini Exchange Online veya devre Exchange Online. Önerilen değer etkinleştirilir.

- **Kullanıcı tıklatmalarını izleme**: Bağlantıların depolanması etkinleştirildi veya Kasa e-posta iletisinde tıklandı URL'ler için verilere tıklayın. Önerilen değer, bu ayarın seçili olmayan (kullanıcı tıklamalarını izlemek için) kullanılmasıdır.

  URL'de, iç gönderenler ve iç alıcılar arasında gönderilen e-posta iletileri bağlantıları için tıklama izleme şu anda desteklenmiyor.

- **Kullanıcıların özgün URL'ye tıklamasına izin verme**: Kullanıcıların uyarı sayfasına özgün URL'ye tıklamalarına [izin verir](#warning-pages-from-safe-links) veya bunu engeller. Önerilen değer etkinleştirilir.

- **Bildirim ve uyarı sayfalarında kuruluşun markasını görüntüleme**: Bu seçenek, uyarı sayfalarında kurum markasını gösterir. Markalama, kullanıcıların yasal uyarıları belirlemelerine yardımcı olur, çünkü varsayılan Microsoft uyarı sayfaları çoğunlukla saldırganlar tarafından kullanılır. Özelleştirilmiş markalama hakkında daha fazla bilgi için bkz[. Microsoft 365 özelleştirme](../../admin/setup/customize-your-organization-theme.md).

- **Aşağıdaki URL'leri yeniden yazma: URL'leri** olduğu gibi bırakır. Taramaya gerek gelmeyen güvenli URL'lerin özel bir listesini tutar. Liste, her grup için benzersiz Kasa ilkedir. Aşağıdaki URL'leri yeniden  yazma listesi hakkında daha fazla bilgi için, bu makalenin devam bölümünde yer alan "Aşağıdaki URL'leri yeniden yazma[" Kasa](#do-not-rewrite-the-following-urls-lists-in-safe-links-policies) Bağlantılar ilkeleri bölümüne bakın.

  Bağlantılar ilkeleri hakkında Standart ve Katı ilke ayarları için önerilen değerler hakkında daha fazla bilgi Kasa bkz. [Bağlantılar Kasa ayarları](recommended-settings-for-eop-and-office365.md#safe-links-policy-settings).

- **URL'leri yeniden yazmadan, yalnızca SafeLinks API'si** üzerinden kontrol edin: Bu ayar etkinleştirilirse URL kaydırma olmaz. Kasa Bağlantılar, URL'nin tık olduğu sırada API'ler aracılığıyla özel olarak ve bu bağlantıları Outlook istemci tarafından çağrılır. Önerilen değer devre dışı bırakılır.
  
- **Alıcı filtreleri**: İlkenin kimlere geçerli olduğunu belirleyen alıcı koşullarını ve özel durumlarını belirtmeniz gerekir. Bu özellikleri koşullar ve özel durumlar için kullanabilirsiniz:
  - **Alıcı**
  - **Alıcı etki alanı:**
  - **Alıcı,**

  Bir koşul veya özel durumu tek bir kez kullanabilirsiniz, ancak koşul veya özel durum birden çok değer içerebilir. Aynı koşul veya özel durum kullanımı VEYA mantığının birden çok değeri (örneğin, _\<recipient1\>_ veya _\<recipient2\>_). Farklı koşullar veya özel durumlar, AND mantığı kullanır (örneğin, _\<recipient1\>_ ve _\<member of group 1\>_).

- **Öncelik**: Birden çok ilke sanız, uygulanma sıralarını belirtsiniz. İki ilke aynı önceliğe sahip olabilir ve ilk ilke uygulandıktan sonra ilke işleme durur.

  Öncelik sırası, birden çok ilkenin nasıl değerlendirilip uygulandığı hakkında daha fazla bilgi için bkz. [E-posta korumasının sırası ve önceliği](how-policies-and-protections-are-combined.md).
  
### <a name="how-safe-links-works-in-email-messages"></a>Bağlantılar Kasa e-posta iletisinde nasıl çalışır?

Üst düzey bir düzeyde, e-posta iletileri Kasa URL'lerde bağlantıların nasıl çalıştığını şöyle sağlar:

1. Tüm e-postalar EOP'den geçerek, burada internet protokolü (IP) ve zarf filtreleri, imza tabanlı kötü amaçlı yazılımdan koruma, istenmeyen postadan koruma ve kötü amaçlı yazılımdan koruma filtreleri ileti alıcının posta kutusuna teslim edilir.

2. Kullanıcı posta kutusunda iletiyi açar ve iletide bir URL'ye tıklar.

3. Kasa Web sitesini açmadan önce Bağlantılar hemen URL'yi denetler:

   - URL, aşağıdaki **URL'leri engelle listesine dahil edilirse** , engellenen [bir URL uyarısı](#blocked-url-warning) açılır.

   - URL kötü amaçlı olduğu belirlenen bir web sitesini gösterirse, kötü amaçlı bir [web](#malicious-website-warning) sitesi uyarı sayfası (veya farklı bir uyarı sayfası) açılır.

   - URL indirilebilir bir dosyayı işaret ediyorsa ve kullanıcıya uygulanan ilkede Şüpheli bağlantıları ve dosyaları işaret alan bağlantıları tarama gerçek zamanlı **URL** tarayın ise, indirilebilir dosya işaretlenir.

   - URL güvenli olarak belirlendi ise, web sitesi açılır.

## <a name="safe-links-settings-for-microsoft-teams"></a>Kasa bağlantıları ayarlarını Microsoft Teams

Bağlantılar ilkeleri altında, Kasa için Bağlantılar korumasını Microsoft Teams Kasa devre dışı bırakabilirsiniz. Özel olarak, Bu **ayarın içindeki Bilinmeyen veya kötü amaçlı olabilecek URL'ler için eylemi Microsoft Teams** kullanırsanız. Önerilen değer, **On'dır**.

> [!NOTE]
> Bu bağlantılar korumasını Kasa bağlantılar korumasını Teams, değişikliğin etkiliksi 24 saate kadar sürebilir.

E-posta Kasa bağlantılarına uygulanacak bağlantılar ilkeleri, E-posta iletileri sayfasındaki bağlantılara da Teams:

- **Dosyaları işaret alan şüpheli bağlantılar ve bağlantılar için gerçek zamanlı URL tarama uygulama**
- **Kullanıcı tıklamalarını izleme**
- **Kullanıcıların özgün URL'ye tıklamasına izin verme**

Bu ayarlar daha önce [E-posta Kasa Bağlantıları ayarlarında açıklanmıştır](#safe-links-settings-for-email-messages).

Microsoft Teams için Kasa Bağlantıları korumasını Microsoft Teams Teams, korumalı kullanıcı bağlantıya tıkladığında (tıklayma süresi) bilinen kötü amaçlı bağlantılar listesinden işaretli olur. URL'ler yeniden yazılmaz. Bağlantı kötü amaçlı olduğu bulunursa, kullanıcılar aşağıdaki deneyimlere sahip olur:

- Bağlantı bir görüşmede, Teams sohbette veya kanallardan tıklandısa, aşağıdaki ekran görüntüsünde gösterildiği gibi uyarı sayfası varsayılan web tarayıcısında görünür.
- Bağlantı sabitlenmiş bir sekmeden tıklandısa, uyarı sayfası o sekme içindeki Teams arabiriminde görünür. Güvenlik nedeniyle, bağlantıyı bir web tarayıcısında açma seçeneği devre dışı bırakılır.
- İlke yapılandırıldığında, kullanıcıların özgün **URL'ye** tıklamasına izin verme ayarına bağlı olarak, kullanıcının ekran görüntüsünde özgün URL'ye tıklamasına izin verilir veya verilmez **(** yine de önerilmez). Kullanıcıların özgün URL'ye tıklaymalarını sağlaymalarını sağlamak için Kullanıcıların özgün **URL'ye** tıklamasına izin verme ayarını etkinleştirmenizi öneririz.

Bağlantıyı gönderen kullanıcı, Teams korumasının etkinleştir olduğu Kasa Bağlantıları ilkesine dahil değilse, kullanıcı kendi bilgisayarına veya cihazına kendi özgün URL'sine tıklamak ücretsizdir.

![Kötü Kasa bir bağlantıyı Teams bir sayfa için bağlantılar.](../../media/tp-safe-links-for-teams-malicious.png)

Uyarı **sayfasında Geri Git** düğmesine tıkıldığında, kullanıcı özgün bağlamına veya URL konumlarına geri döner. Bununla birlikte, özgün bağlantıya yeniden tıklarken YENIDEN Kasa URL'yi yeniden onaylamanız gerekir; dolayısıyla uyarı sayfası yeniden görüntülenir.

### <a name="how-safe-links-works-in-teams"></a>Bağlantılar Kasa çalışma Teams

Üst düzey bir düzeyde, Bağlantılar koruması Kasa url'ler için şu şekilde Microsoft Teams:

1. Kullanıcı Teams başlatır.

2. Microsoft 365 kuruluşunda Office 365 için Microsoft Defender'ın bulunduğu ve kullanıcının Kasa için korumanın etkinleştirildiğinde etkin bir Kasa Bağlantıları ilkesine dahil Microsoft Teams doğrular.

3. Sohbetlerde, grup sohbetlerinde, kanallarda ve sekmelerde kullanıcı için tıklama zamanında URL'ler doğrulanır.

## <a name="safe-links-settings-for-office-365-apps"></a>Kasa uygulamaları için Bağlantılar Office 365 tıklayın

Kasa için Bağlantılar koruması, Office 365 uygulamaları e-posta iletilerine bağlantıları değil Office belge bağlantıları denetler (ancak belge açıldıktan sonra e-posta iletilerine eklenen Office belgelerinin bağlantılarını da denetler).

Kasa uygulamaları için bağlantılar Office 365, aşağıdaki istemci gereksinimlerine sahiptir:

- Microsoft 365 Uygulamaları veya Microsoft 365 İş Ekstra.
  - Word, Excel ve PowerPoint'Windows Mac'te veya bir web tarayıcısında geçerli sürümleri.
  - Office iOS veya Android cihazlarda kullanılabilir.
  - Visio'Windows.
  - OneNote tarayıcıda açın.
  - Outlook EML Windows MSG dosyalarını aken iş için kullanın.

- Office 365 uygulamaları modern kimlik doğrulamayı kullanmak üzere yapılandırılır. Daha fazla bilgi için bkz[. Office 2013, Office 2016 ve Office 2019 istemci uygulamaları için](../../enterprise/modern-auth-for-office-2013-and-2016.md).

- Kullanıcılar, iş veya okul hesaplarını kullanarak oturum açın. Daha fazla bilgi için bkz[. E-Office](https://support.microsoft.com/office/b9582171-fd1f-4284-9846-bdd72bb28426).

Genel ayarlarda Kasa bağlantılar Office 365 için Bağlantılar koruması yapılandırabilirsiniz Kasa Bağlantıları ilkeleri içinde Kasa yapılandırabilirsiniz. Koruma, kullanıcıların etkin Kasa Bağlantıları ilkelerine dahil olup olmadığına bakılmaksızın, Office 365 için Defender lisansına sahip olan tüm kullanıcılara uygulanır.

Aşağıdaki Kasa Bağlantılar ayarları, Office 365 kullanılabilir:

- **Office 365: Desteklenen** uygulamalarda Bağlantılar taramasını Kasa veya devre dışı Office 365. Varsayılan ve önerilen değer **, Açıktır.**

- **Kullanıcılar Kasa** Bağlantıları'Kasa tıklayma: Kasa Bağlantıları'nın depolanması etkinleştirildi veya devre dışı bırakıldı Word, Excel, PowerPoint ve diğer Visio. Önerilen değer **Kapalı'dır**, bu da kullanıcı tıklamalarını izlen olduğu anlamına gelir.

- **Kullanıcıların özgün URL'ye** yönelik güvenli bağlantıları tıklatmasına izin verme: Masaüstü Word, Excel, PowerPoint ve [](#warning-pages-from-safe-links) diğer sürümlerde, kullanıcıların uyarı sayfasını tıklatarak bu sayfayı özgün URL'ye tıklamalarına izin Visio. Varsayılan ve önerilen değer **, Açıktır.**

Bu uygulamaların Kasa Bağlantılar ayarlarını yapılandırmak Office 365 bkz. Kasa [uygulamaları için Bağlantılar korumasını Office 365.](configure-global-settings-for-safe-links.md#configure-safe-links-protection-for-office-365-apps-in-the-microsoft-365-defender-portal)

Standart ve Katı ilke ayarları için önerilen değerler hakkında daha fazla bilgi için bkz. Standart [ve Katı ilke ayarları Kasa.](recommended-settings-for-eop-and-office365.md#global-settings-for-safe-links)

### <a name="how-safe-links-works-in-office-365-apps"></a>Bağlantılar Kasa uygulamalar içinde Office 365 çalışır

Üst düzeyde, bir uygulamanın URL'leri için Kasa Bağlantılar korumasının nasıl Office 365 vardır. Desteklenen Office 365 önceki bölümde açıklanmıştır.

1. Bir kullanıcı, okul veya okul hesabı içeren bir kuruluşta iş veya okul Microsoft 365 Uygulamaları oturum Microsoft 365 İş Ekstra.

2. Kullanıcı bir bağlantıyı açar ve desteklenen bir Office belgeye tık Office uygulaması lar.

3. Kasa Bağlantılar, hedef web sitesini açmadan önce HEMEN URL'yi denetler:

   - URL, bağlantılar taramayı atleyen listeye dahil Kasa (Aşağıdaki URL'leri engelle listesi) engellenen  [bir URL uyarı](#blocked-url-warning) sayfası açılır.

   - URL kötü amaçlı olduğu belirlenen bir web sitesini gösterirse, kötü amaçlı bir [web](#malicious-website-warning) sitesi uyarı sayfası (veya farklı bir uyarı sayfası) açılır.

   - URL indirilebilir bir dosyayı işaret ediyorsa ve kullanıcıya uygulanan Kasa Bağlantıları ilkesi indirilebilir içeriğe bağlantıları tarayacak şekilde yapılandırıldısa (Şüpheli bağlantıları ve dosyaları işaret alan şüpheli bağlantıları gerçek zamanlı tarama için gerçek zamanlı **URL** tarayın), indirilebilir dosya işaretlenir.

   - URL güvenli kabul edilirse, kullanıcı web sitesine alınır.

   - Bağlantılar Kasa tamamlanmadı ise, Bağlantıları Kasa koruması tetikli olmaz. Masaüstü Office istemcilerde, hedef web sitesine devam etmek için kullanıcı uyarıldı.

> [!NOTE]
> Her oturumun başlangıcında kullanıcının Şu bağlantılardan Kasa etkinleştirildiğinden emin Office sürebilir.

## <a name="block-the-following-urls-list-for-safe-links"></a>Yeni Bağlantılar için "Aşağıdaki URL'leri Kasa engelleme"

Aşağıdaki **URL'leri engelle** listesi, şu konumlarda her zaman Kasa Bağlantılar taraması tarafından engellenen bağlantıları tanımlar:

- E-posta iletileri.
- Office 365 Mac'te Windows belgeler.
- iOS ve Android Office belgeler.

Etkin bir Site Bağlantısı Kasa ilkesi desteklenen bir uygulamanın engellenen bağlantısına tıkladığında, Engellenen [URL uyarı sayfasına](#blocked-url-warning) alınır.

Yeni Bağlantılar'ın genel ayarlarında URL'lerin listesini Kasa yapılandırabilirsiniz. Yönergeler için bkz [. "Aşağıdaki URL'leri engelle" listesini yapılandırma](configure-global-settings-for-safe-links.md#configure-the-block-the-following-urls-list-in-the-microsoft-365-defender-portal).

**Notlar**:

- Her yerde engellenen URL'lerin gerçekten evrensel bir listesi için bkz. [Kiracı İzin Ver/Engelleme Listesini Yönetme](tenant-allow-block-list.md).
- Aşağıdaki **URL'leri engelle listesinin** sınırları:
  - En fazla 500 girdi sayısıdır.
  - Bir girişin uzunluğu en çok 128 karakter olabilir.
  - Girdilerin hepsi 10.000 karakteri geçemez.
- URL'nin sonuna eğik çizgi (`/`) dahil etme. Örneğin, değil `https://www.contoso.com`, kullanın `https://www.contoso.com/`.
- Yalnızca etki alanı URL'si (örneğin veya `contoso.com` `tailspintoys.com`) etki alanını içeren tüm URL'leri engelleyebilir.
- Tam etki alanını engellemeden alt etki alanını engelleyebilirsiniz. Örneğin, `toys.contoso.com*` alt etki alanını içeren tüm URL'leri engeller, ancak tam etki alanını içeren URL'leri engellemez `contoso.com`.
- URL girdisi başına en çok üç joker karakter (`*`) içerebilirsiniz.

### <a name="entry-syntax-for-the-block-the-following-urls-list"></a>"Aşağıdaki URL'leri engelle" listesi için giriş söz dizimi

Girebilirsiniz değer örnekleri ve sonuçları aşağıdaki tabloda açıklanmıştır:

<br>

****

|Değer|Sonuç|
|---|---|
|`contoso.com` <p> veya <p> `*contoso.com*`|Etki alanı, alt etki alanları ve yolları engeller. Örneğin, `https://www.contoso.com`, `https://sub.contoso.com`ve `https://contoso.com/abc` engellenir.|
|`https://contoso.com/a`|Engellemeler `https://contoso.com/a` ancak gibi ek alt yolları engellemez `https://contoso.com/a/b`.|
|`https://contoso.com/a*`|Blokları `https://contoso.com/a` ve gibi ek altpath'leri.`https://contoso.com/a/b`|
|`https://toys.contoso.com*`|Alt etki alanını engeller (`toys` bu örnekte), ancak diğer etki alanı URL'lerine (örneğin veya ) tıklamalara izin `https://contoso.com` verme `https://home.contoso.com`.|
|

## <a name="do-not-rewrite-the-following-urls-lists-in-safe-links-policies"></a>Bağlantılar ilkelerinde "Aşağıdaki URL'leri yeniden Kasa" listeleri

> [!NOTE]
> If your organization use Kasa Links policies, the **Do not reriter the URL'ler** lists are only supported method for third party phishing tests.

Her Kasa Bağlantılar ilkesi, Bağlantılar tarama işlemiyle  yeniden yazılmamış URL'leri belirtmek için kullanabileceğiniz aşağıdaki URL'leri yeniden Kasa içerir. Başka bir deyişle, liste ilkeye dahil olan kullanıcıların, belirtilen URL'lere erişmelerine olanak sağlar ve aksi takdirde Bu Bağlantılar tarafından Kasa sağlar. Farklı gruplarda farklı listeler yapılandırabilirsiniz Kasa ilkeleri. İlke işleme, ilk (büyük olasılıkla en yüksek öncelikli) ilke kullanıcıya uygulandıktan sonra durur. Dolayısıyla, Aşağıdaki **URL'ler listesini** yeniden yazma bağlantısı ilkeleri arasında yer alan birden çok etkin URL'ye Kasa uygulanır.

Yeni veya var olan bağlantılar ilkelerinde listeye girişler Kasa için bkz. Yeni Bağlantılar Kasa [oluşturma](set-up-safe-links-policies.md#use-the-microsoft-365-defender-portal-to-create-safe-links-policies) veya [Bağlantılar Kasa değiştirme](set-up-safe-links-policies.md#use-the-microsoft-365-defender-portal-to-modify-safe-links-policies).

**Notlar**:

- Aşağıdaki istemciler, Bağlantılar ilkelerinde aşağıdaki URL'leri **yeniden yazmama** Kasa tanımaz. İlkelere dahil olan kullanıcıların, şu istemcilerde tarama yapılan bağlantıların sonuçlarına Kasa URL'lere erişimi engel olabilir:
  - Microsoft Teams
  - Office web uygulamaları

  Her yerde izin verilen URL'lerin gerçek anlamda evrensel bir listesi için bkz. [Kiracı İzin Verilenler/Engellenenler Listesini yönetme](tenant-allow-block-list.md). Bununla birlikte, oraya eklenen URL'lerin Kasa Bağlantılar ilkesinde yapılması gereken şekilde yeniden yazma Kasa unutmayın.

- Kullanıcı deneyimini geliştirmek için, sık kullanılan iç URL'leri listeye eklemeyi göz önünde bulundurabilirsiniz. Örneğin, şirket içi hizmetlerinize (örneğin, site Skype Kurumsal veya SharePoint) bu URL'leri tarama dışında tutmak için  ekleyin.
- Yeni Bağlantılar **ilkelerinize şu URL'leri** yeniden yazmadıysanız Kasa, listeleri gözden geçirmeyi ve gerektiğinde joker karakterleri eklemeyi unutmayın. Örneğin, listeniz bunun gibi bir girdiye sahip ve `https://contoso.com/a` siz daha sonra bunun gibi alt yolları eklemeye karar verirsiniz `https://contoso.com/a/b`. Yeni girdi eklemek yerine, var olan girdiye joker karakteri ekleyerek bunun haline gelir `https://contoso.com/a/*`.
- URL girdisi başına en çok üç joker karakter (`*`) içerebilirsiniz. Joker karakterler açık olarak önekler veya alt etki alanları içerir. Örneğin, giriş ile `contoso.com` aynı `*.contoso.com/*``*.contoso.com/*` şey değildir çünkü insanların belirtilen etki alanındaki alt etki alanları ve yolları ziyaretine izin verir.
- Bir URL, HTTP' den HTTPS'ye otomatik yeniden yönlendirme (örneğin, 302 `http://www.contoso.com` `https://www.contoso.com`yeniden yönlendirme) kullanıyorsa ve aynı URL için hem HTTP hem de HTTPS girdilerini listeye girmeye çalışmalı, ikinci URL girdisinin ilk URL girdisinin yerini yer alıyor olabilir. URL'nin HTTP ve HTTPS sürümleri tamamen ayrı olursa, bu davranış ortaya çıkar.
- HEM HTTP http:// https:// HTTPS sürümlerini dışlamak için contoso.com veri (başka bir contoso.com) belirtin.
- `*.contoso.com` dahil **contoso.com** , dolayısıyla hem belirtilen etki alanını hem de tüm alt etki alanlarını kapsıyor olmak üzere ikisini hariç tutabilirsiniz.
- `contoso.com/*` yalnızca **contoso.com** olduğu için ikisini de hariç `contoso.com` `contoso.com/*`tutmak zorunda değildir; `contoso.com/*` yalnızca yeterlidir.
- Etki alanının tüm yinelemelerini dışlamak için iki dışlama girdisi gerekir; `contoso.com/*` ve .`*.contoso.com/*` Bunlar hem HTTP hem de HTTPS, ana etki alanı contoso.com alt etki alanlarının yanı sıra herhangi bir kısmını (örneğin, hem HTTP hem de contoso.com etki alanlarını contoso.com/vdir1 dahil) hariç tutmak için kullanılır.

### <a name="entry-syntax-for-the-do-not-rewrite-the-following-urls-list"></a>"Aşağıdaki URL'leri yeniden yazma" listesi için giriş söz dizimi

Girebilirsiniz değer örnekleri ve sonuçları aşağıdaki tabloda açıklanmıştır:

<br>

****

|Değer|Sonuç|
|---|---|
|`contoso.com`|Alt etki alanlarına `https://contoso.com` veya yollara erişime izin verir, ancak bu izinler olmaz.|
|`*.contoso.com/*`|Bir etki alanına, alt etki alanına ve yollara (örneğin, `https://www.contoso.com`, , veya `https://www.contoso.com`) erişime `https://maps.contoso.com`izin verir `https://www.contoso.com/a`. <p> Bu girdi yapısal olarak , veya `*contoso.com*`gibi sahte olabilecek sitelere izin vermemektedir, çünkü `https://www.falsecontoso.com``https://www.false.contoso.completelyfalse.com`|
|`https://contoso.com/a`|erişime izin `https://contoso.com/a`verir, ancak bu gibi altpathlere erişim izni verir `https://contoso.com/a/b`|
|`https://contoso.com/a/*`|Erişime ve `https://contoso.com/a` bunun gibi alt `https://contoso.com/a/b`|
|

## <a name="warning-pages-from-safe-links"></a>Bağlantılardan uyarı Kasa sayfaları

Bu bölümde, bir URL'ye tıklarken Bağlantılar korumasının Kasa çeşitli uyarı sayfaları örnekleri yer almaktadır.

Birkaç uyarı sayfası güncelleştirilmiş olabilir. Güncelleştirilmiş sayfaları henüz görmüyorsanız, yakında görmeye başlayacaktır. Güncelleştirilmiş sayfalar yeni bir renk düzeni, daha fazla ayrıntı ve verilen uyarı ve önerilere rağmen siteye devam etme olanağı içerir.

### <a name="scan-in-progress-notification"></a>Tarama işlemi sürüyor bildirimi

Tıklı URL, Bağlantı Ekle tarafından Kasa. Bağlantıyı yeniden denmeden önce birkaç dakika beklemenız gerekiyor olabilir.

!["Bağlantı taranıyor" bildirimi](../../media/ee8dd5ed-6b91-4248-b054-12b719e8d0ed.png)

Özgün bildirim sayfası şöyle görünür:

![Özgün "Bağlantı taranıyor" bildirimi](../../media/04368763-763f-43d6-94a4-a48291d36893.png)

### <a name="suspicious-message-warning"></a>Şüpheli ileti uyarısı

Tıklı URL, diğer şüpheli iletilere benzer bir e-posta iletisinde yer aldı. Siteye devam etmeden önce e-posta iletisine bir kez daha göznizi göndermenizi öneririz.

!["Şüpheli bir iletiden bağlantı tıklandı" uyarısı](../../media/33f57923-23e3-4b0f-838b-6ad589ba897b.png)

### <a name="phishing-attempt-warning"></a>Kimlik avı girişimi uyarısı

Tıklı URL, kimlik avı saldırısı olarak tanımlanan bir e-posta iletisinde yer alan bir e-posta iletisidir. Sonuç olarak, e-posta iletisine gelen tüm URL'ler engellenir. Siteye devammanizi öneririz.

!["Bağlantı kimlik avı iletisinden tıklandı" uyarısı](../../media/6e544a28-0604-4821-aba6-d5a57bb917e5.png)

### <a name="malicious-website-warning"></a>Kötü amaçlı web sitesi uyarısı

Tıklı URL kötü amaçlı olarak tanımlanan bir siteyi gösterir. Siteye devammanizi öneririz.

!["Bu web sitesi kötü amaçlı olarak sınıflandırılmış" uyarısı](../../media/058883c8-23f0-4672-9c1c-66b084796177.png)

Özgün uyarı sayfası şöyle görünür:

![Özgün "Bu web sitesi kötü amaçlı olarak sınıflandırıldı" uyarısı](../../media/b9efda09-6dd8-46ef-82cb-56e4d538b8f5.png)

### <a name="blocked-url-warning"></a>Engellenmiş URL uyarısı

Tıklı URL, kuruluşta bir yönetici tarafından el ile engellenmiştir (Genel ayarlarda Yer alan Url'leri engelleme Bağlantıları'nın Kasa. Bağlantı, El ile Kasa nedeniyle Bağlantılar tarafından taranmadı.

Yöneticinin belirli URL'leri el ile engellemesi için çeşitli nedenler vardır. Sitenin engellenmiş olması gerektiğini düşünüyorsanız, yöneticinizle iletişime geçin.

!["Bu web sitesi yöneticiniz tarafından engellendi" uyarısı](../../media/6b4bda2d-a1e6-419e-8b10-588e83c3af3f.png)

Özgün uyarı sayfası şöyle görünür:

![Özgün "Bu web sitesi, kuruluş URL ilkesi başına engellendi" uyarısı](../../media/3d6ba028-30bf-45fc-958e-d3aad3defc83.png)

### <a name="error-warning"></a>Hata uyarısı

Bir tür hata oluştu ve URL açılamıyor.

!["Erişmeye istediğiniz sayfa yüklenemiyor" uyarısı](../../media/2f7465a4-1cf4-4c1c-b7d4-3c07e4b795b4.png)

Özgün uyarı sayfası şöyle görünür:

![Özgün "Bu web sayfası yüklenemedi" uyarısı](../../media/9aaa4383-2f23-48be-bdaa-8efbcb2acc70.png)
