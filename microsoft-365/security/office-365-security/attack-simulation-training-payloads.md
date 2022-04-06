---
title: Saldırı benzetimi eğitimi için özel yüklemeler oluşturun
ms.author: chrisda
author: chrisda
manager: dansimp
audience: ITPro
ms.topic: how-to
ms.prod: m365-security
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
ms.custom: ''
description: Yöneticiler, Plan 2'de Saldırı benzetimi eğitimi için özel Office 365 için Microsoft Defender oluştur yapmayı öğrenebilir.
ms.technology: mdo
ms.openlocfilehash: 8aa81a1940e564e9877af6a1848ff439aea58d8e
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64468511"
---
# <a name="create-custom-payloads-for-attack-simulation-training-in-defender-for-office-365"></a>Yeni bir yıl içinde Saldırı benzetimi eğitimi için özel Office 365 için Defender

**Plan** [2 Office 365 için Microsoft Defender için geçerlidir](defender-for-office-365.md)

Saldırı benzetimi eğitiminde yük, benzetimler ile kullanıcılara sunulan kimlik avı e-posta iletisi ve web sayfalarıdır. Microsoft 365 E5 veya Office 365 için Microsoft Defender Plan 2'de saldırı benzetimi eğitimi, kullanılabilen sosyal mühendislik teknikleri için güçlü bir yerleşik yük kataloğu sunar. Bununla birlikte, organizasyonu için daha iyi çalışacak özel yüklemeler oluşturmak istiyor da olabilirsiniz.

Bu makalede, Saldırı benzetimi eğitimi altında kendi yüklemelerinizi nasıl oluşturabilirsiniz? Aşağıdaki konumlarda özel yük oluşturabilirsiniz:

- Yük **sekmesi:** Microsoft 365 Defender portalında <https://security.microsoft.com>E-posta ve işbirliği **Saldırı benzetimi eğitimi** \>  \> **&'ler sekmesine** gidin. Doğrudan Yükleri **sekmesine gitmek için** kullanın<https://security.microsoft.com/attacksimulator?viewid=payload>.
- Benzetim oluşturma sırasında: Benzetim oluşturma sihirbazının Yük seçme sayfasında  (üçüncü sayfa) özel yüklemeler oluşturabilirsiniz. Daha fazla bilgi için bkz[. Kimlik avı saldırısının benzetimini Office 365 için Defender](attack-simulation-training.md).

Saldırı benzetimi eğitimi hakkında bilgi almak için Saldırı [benzetim Kullanmaya başlayın'i kullanma hakkında daha fazla bilgi için bkz](attack-simulation-training-get-started.md).

> [!NOTE]
> Bazı ticari markalar, logolar, simgeler, insignias ve diğer kaynak tanımlayıcıları yerel, eyalet ve federal yasalara göre daha yüksek koruma sağlar. Bu gibi göstergelerin yetkisiz kullanımı, kullanıcılara cezai para cezaları dahil olmak üzere penceler konur. Kapsamlı bir liste olsa da, bu listede Başkan Yardımcısı, Başkan Yardımcısı ve Uluslararası iş üyeleri, CIA, CIA, Social Security, Medicare ve Medicaid, Birleşik Devletler Internal Revenue Service ve Olimpiyatlar yer almaktadır. Bu ticari marka kategorilerinin ötesinde, üçüncü taraf ticari markaların yapısal bir miktarda risk taşıyan kullanım ve değiştirilmesi. Yüklemede kendi ticari markalarınızı ve logolarınızı kullanmak, özellikle de kuruluş izinli olduğu bir yüklemede daha az riskli olabilir. Yük oluşturma veya yapılandırmada kullanımın ne olduğu veya uygun olmadığınız hakkında başka sorularınız varsa, yasal danışmanlarınıza danışmanız ile görüşmeniz gerekir.

## <a name="create-a-payload"></a>Yük oluşturma

Yükleme simgesi oluştur'a ![tıklarsanız.](../../media/m365-cc-sc-create-icon.png) **Saldırı benzetimi** eğitimi'nin **Yükleri** sekmesinden bir yük oluşturun veya benzetim oluşturma **[](attack-simulation-training.md#select-a-payload)** sihirbazının Yük seçin sayfasında yük oluşturma sihirbazı başlatılır ve bu bölümde açıklanmıştır.

### <a name="select-a-payload-type"></a>Yük türünü seçin

Tür **seçin sayfasında**, şu anda seçebilirsiniz tek değer E-posta'dır.

**İleri**'ye tıklayın.

### <a name="select-a-social-engineering-technique"></a>Bir sosyal mühendislik tekniği seçin

Teknik **seçin sayfasında** , kullanılabilir seçenekler benzetim oluşturma sihirbazının [Select technique](attack-simulation-training.md#select-a-social-engineering-technique) sayfasındaki seçeneklerle aynıdır:

- **Kimlik bilgileri toplama**
- **Kötü amaçlı yazılım eki**
- **Ekin içinde bağlantı**
- **Kötü amaçlı yazılım bağlantısı**
- **Sürücüye göre URL**

Bitirdikten sonra, Sonraki'ne **tıklayın**.

### <a name="name-and-describe-the-payload"></a>Yükü adla ve açıkla

Yük **adı sayfasında** aşağıdaki ayarları yapılandırabilirsiniz:

- **Ad**: Yük için benzersiz, açıklayıcı bir ad girin.
- **Açıklama**: Yük için isteğe bağlı olarak ayrıntılı bir açıklama girin.

Bitirdikten sonra, Sonraki'ne **tıklayın**.

## <a name="configure-the-payload"></a>Yükü yapılandırma

Yük **yapılandır sayfasında** , yüklerinizi oluşturmanın zamanı geldi. Kullanılabilir ayarların birçoğu, Seçme tekniği sayfasında (örneğin, bağlantılar ve ekler) yapmış olduğunuz seçime göre belirlenir.

- **Gönderen ayrıntıları** bölümü: Aşağıdaki ayarları yapılandırma:
  - **From name**
  - **Adı görünen ad olarak kullan**: Varsayılan olarak, bu ayar seçili değildir.
  - **E-postadan**: Yükün göndereni için bir iç e-posta adresi seçerseniz yük, diğer bir çalışandan geliyor gibi görünür. Bu gönderenin e-posta adresi kullanıcının yük yüküne karşı duyarlıklarını artıracak ve çalışanları iç tehdit riski konusunda eğitecektir.
  - **E-posta konusu**

- **Ek ayrıntıları** bölümü: Bu bölüm yalnızca Teknik seçin sayfasında Kötü amaçlı yazılım **eki, Eke** bağlantı veya Kötü amaçlı yazılıma **bağlantı gönder'i** **seçtiysanız** kullanılabilir. Aşağıdaki ayarları yapılandırma:
  - **Ekinizi adla**
  - **Bir ek türü seçin**: Şu anda yalnızca **Docx kullanılabilir değerdir**.

- **Ek bölümü bağlantısı** : Bu bölüm yalnızca Teknik seçin sayfasında Kötü amaçlı **yazılıma** **bağlama'yi seçtiysanız** kullanılabilir. Kötü amaçlı yazılım eki bağlantınız olarak kullanmak istediğiniz **bir URL** seçin bağlantısı kutusunda, kullanılabilir URL'lerden birini (Kimlik avı bağlantısı bölümünde açıklanan URL'ler **)** seçin.

  Daha sonra, iletinin gövdesine URL'yi ekleyeceğiz.

- **Kimlik avı bağlantısı** bölümü: Bu bölüm yalnızca Seçme tekniği sayfasında Kimlik bilgisi **toplama,** Eke bağlantı veya **Sürücü URL'si'ne** tıklayın. 

  Kimlik **bilgileri toplama** veya **Drive-by URL'si** için kutunun adı Kimlik avı bağlantınız olarak kullanmak **istediğiniz URL'yi seçin seçeneğidir**. Daha sonra, iletinin gövdesine URL'yi ekleyeceğiz.

  **Ekin bağlantısı için**, kutunun adı Bu ekte kimlik avı bağlantınız olarak kullanmak **istediğiniz bir URL seçin bağlantısıdır**. Daha sonra, URL'yi eke eklersiniz.

  Kullanılabilir URL değerlerinden birini seçin:
  
  - <https://www.mcsharepoint.com>
  - <https://www.attemplate.com>
  - <https://www.doctricant.com>
  - <https://www.mesharepoint.com>
  - <https://www.officence.com>
  - <https://www.officenced.com>
  - <https://www.officences.com>
  - <https://www.officentry.com>
  - <https://www.officested.com>
  - <https://www.prizegives.com>
  - <https://www.prizemons.com>
  - <https://www.prizewel.com>
  - <https://www.prizewings.com>
  - <https://www.shareholds.com>
  - <https://www.sharepointen.com>
  - <https://www.sharepointin.com>
  - <https://www.sharepointle.com>
  - <https://www.sharesbyte.com>
  - <https://www.sharession.com>
  - <https://www.sharestion.com>
  - <https://www.templateau.com>
  - <https://www.templatent.com>
  - <https://www.templatern.com>
  - <https://www.windocyte.com>

  > [!NOTE]
  > URL saygınlığı hizmeti, bu URL'lerden birini veya birden fazlasını güvenli olmayan olarak tanımlayabilir. URL'yi benzetimde kullanmadan önce, desteklenen web tarayıcıları içinde URL'nin kullanılabilirliğini kontrol edin. Daha fazla bilgi için bkz. [Google tarafından engellenen kimlik avı benzetimi URL'leri Kasa göz atma](attack-simulation-training-faq.md#phishing-simulation-urls-blocked-by-google-safe-browsing).

- **Ek içeriği** bölümü: Bu bölüm yalnızca Seçme tekniği sayfasında **Ekin** içinde bağlantı'ya **tıklayın seçeneğini kullandıysanız** kullanılabilir.

  Dosya ekin yüklemesinde içerik oluşturmak için zengin bir metin düzenleyicisi kullanılabilir.

  Önceden seçilen **kimlik avı URL'sini** eke eklemek için Kimlik Avı bağlantı denetimi'ne tıklayın.

- Ortak ayarlar:
  - **Etiket ekle**
  - **Tema**: Kullanılabilir **değerler: Hesap** **Etkinleştirme, Hesap** **Doğrulama, Faturalama****,** Postayı **Temizleme, Alınan** Belge, **Gider**, **Faks****, Finans** Raporu, **Gelen İletiler**, **Fatura**, **Öğe** **Alındı, Oturum** Açma **Uyarısı, Alınan** Posta, **Diğer**, **Parola**, **Ödeme**, **Bordro**, **Kişiselleştirilmiş** **Teklif**, Karantina , **Uzaktan Çalışma**, İletiyi **Gözden Geçir****, Güvenlik** **Güncelleştirmesi, Hizmet** Askıya **Alındı, İmza** Gerekli, Posta Kutusu Yükseltme **Depolama**, Posta **kutusunu veya** **sesli mesajı doğrula**.
  - Marka **: Kullanılabilir** değerler: **American Express**, **Capital One**, **DHL**, **DocuSign**, **Dropbox**, **Facebook**, **First American**, **Microsoft**, **Netflix**, **Scotiabank**, **SendGrid**, **Title**, **Tgrid**, **Wells Fargo**, **Syrinx Cloud** veya **Other**.
  - **Endüstri**: Kullanılabilir **değerler: Bankacılık**, **İş** hizmetleri, **Tüketici** hizmetleri, **Eğitim**, **Enerji**, **Inşaat**, **Danışmanlık**, **Finansal** hizmetler, **Kamu****, Hastane**, **Sigorta**, **Yasal**, **Courier** hizmetleri, **IT**, **Sağlık**, **Üretim**, **Perakende**, **Telecom**, **Emlak** veya **Diğer.**
  - **Geçerli olay**: Kullanılabilir değerler Evet **veya** **Hayır'dır**.
  - **Neden**: Kullanılabilir değerler Evet **veya** **Hayır'dır**.

- **Dil** bölümü: Yükün dilini seçin. Kullanılabilir **değerler: İngilizce**, **İspanyolca**, **Almanca**, **Japonca****, Fransızca****, Portekizce****,** Felemenkçe, **İtalyanca****, İsveç** dili, Çince **(Basitleştirilmiş)**, **Norveççe Bokmål**, **Lehçe**, **Rusça**, **Fince**, **Korece**, **Türkçe**, **Macarca**, **İbranice**, **Tay** dili, **Arapça**, **Vietnamca**, **Slovakça****, Yunanca**, **Endonezya Dili**, **Rumence**, **Slovence**, **Hırvatça**, **Katalanca** veya **Diğer**.

- **E-posta iletisi** bölümü:

  - Var olan düz metin **iletisi dosyasını içeri** aktar için **E-postayı** içeri aktar'a ve sonra Da Dosya seç'e tıklarsınız.

  - Metin **sekmesinde** , e-posta iletinizin yük yüklerini oluşturmak için zengin bir metin düzenleyicisi kullanılabilir.

    - Kullanılabilir etiketleri **ekerek** her kullanıcının e-posta iletiyi kişiselleştirmek için Dinamik etiket denetimi kullanın:
      - **Ad ekle**: İleti gövdesine eklenen değer: `${userName}`.
      - **E-posta** ekle: İleti gövdesine eklenen değer şöyledir `${emailAddress}`: .

      :::image type="content" source="../../media/attack-sim-training-payloads-configure-payload-email-message.png" alt-text="Yeni hesapta saldırı benzetim eğitimi bölümündeki yük oluşturma sihirbazının Yük yapılandır sayfasındaki E-posta iletisi Office 365 için Microsoft Defender" lightbox="../../media/attack-sim-training-payloads-configure-payload-email-message.png":::

      **Kimlik avı bağlantı** denetimi: Bu denetim yalnızca, Seçme tekniği sayfasında Kimlik bilgisi **toplama, Eke** bağlantı veya **Url** ile sürücü-by'i **seçtiysanız** kullanılabilir.  Daha önce Kimlik Avı bağlantısı bölümüne seçtiğiniz URL'yi eklemek **için bu denetimi** kullanın.

      **Kötü amaçlı yazılım eki** bağlantı denetimi: Bu denetim yalnızca Seçme **tekniği sayfasında Kötü** amaçlı yazılıma **bağlama'yi seçtiysanız** kullanılabilir. Ek bağlantısı bölümünde daha önce seçtiğiniz URL'yi eklemek **için bu denetimi** kullanın.

      Kimlik Avı **bağlantısı'ne veya Kötü** **amaçlı yazılım eki bağlantısına** tıklarsanız, bağlantıyı isimlamanız için bir iletişim kutusu açılır. Bitirdikten sonra Onayla'ya **tıklayın**.

      İleti gövdesine (Kod sekmesinde görünür **) eklenen** değerdir `<a href="${phishingUrl}" target="_blank">Name value you specified</a>`.

  - Kod **sekmesinde** HTML kodunu doğrudan görüntüleyebilirsiniz ve değiştirebilirsiniz. Biçimlendirme ve Dinamik etiket **ve Kimlik avı** bağlantısı **veya Kötü amaçlı** yazılım eki bağlantısı **gibi** diğer denetimler kullanılamaz.

  - **E-posta iletisine** gelen tüm bağlantıları kimlik avı bağlantısıyla değiştir iki durumlu düğme ancak Teknik seçin sayfasında Kimlik bilgisi **toplama, Kötü** amaçlı yazılıma bağlantı bağlantısı veya **Drive-by URL'si'yi** **seçmeniz gerekir.** Bu geçiş, iletide yer alan tüm bağlantıları önceden seçilen Kimlik Avı bağlantısı veya Ek URL'si için Bağlantı **ile değiştirerek zaman kazanmak** sağlar. Bunu yapmak için, ayarı Açık olarak değiştir simgesine ![tıklayın](../../media/scc-toggle-on.png).

Bitirdikten sonra, Sonraki'ne **tıklayın**.

## <a name="add-indicators-to-phishing-clues"></a>Kimlik avı ipuçlarına gösterge ekleme

> [!NOTE]
> Seçme tekniği sayfasında Kötü amaçlı yazılım eki veya **Kötü** amaçlı yazılıma bağlantı **bağlantısı'nın** seçili **olduğu göstergeler** kullanılamaz.

Göstergeler, kimlik avı iletilerinin tell-tale işaretlerini tanımlamak için saldırı benzetimlerinden geçen çalışanların yardımcı olur.

Gösterge ekle **sayfasında Gösterge** **ekle'ye tıklayın**. Görüntülenen açılır listede, aşağıdaki ayarları yapılandırabilirsiniz:

- **Gösterge adı** **ve Gösterge konumu**: Bu değerler birbiriyle ilişkilidir. Göstergeyi nereye ekyersiniz, göstergenin kendisine bağlıdır. Kullanılabilir değerler aşağıdaki tabloda açıklanmıştır:

  |Gösterge adı|Gösterge konumu|
  |---|---|
  |**Ek türü**|İleti gövdesi|
  |**Dikkat dağıtıcı ayrıntılar**|İleti gövdesi|
  |**Etki alanı hesabı**|İleti gövdesi <p> E-posta adresine|
  |**Genel karşılama**|İleti gövdesi|
  |**Çekici çekicilik**|İleti gövdesi|
  |**Tutarsızlık**|İleti gövdesi|
  |**Gönderen ayrıntıları yok**|İleti gövdesi|
  |**Yasal dil**|İleti gövdesi|
  |**Sınırlı süre teklifi**|İleti gövdesi|
  |**Logo takliti veya tarihe sahip markalama**|İleti gövdesi|
  |**İş veya iş sürecini taklit ediyor**|İleti gövdesi|
  |**Hayır/az markalama**|İleti gövdesi|
  |**Arkadaş, iş arkadaşı, gözetmen veya yetkili olarak çalışıyoruz**|İleti gövdesi|
  |**Hassas bilgi isteği**|İleti gövdesi|
  |**Güvenlik göstergeleri ve simgeleri**|İleti gövdesi <p> İleti konusu|
  |**Gönderen görünen adı ve e-posta adresi**|From name <p> E-posta adresine|
  |**Aciliyet hissi**|İleti gövdesi <p> İleti konusu|
  |**Yazım ve dil bilgisi düzensizliği**|İleti gövdesi <p> İleti konusu|
  |**Tehdit dili**|İleti gövdesi <p> İleti konusu|
  |**Gerçek teklifler için çok iyi**|İleti gövdesi|
  |**Profesyonel olmayan görünümlü tasarım veya biçimlendirme**|İleti gövdesi|
  |**URL köprüleri**|İleti gövdesi|
  |**Özelsin**|İleti gövdesi|
  
  Bu liste, kimlik avı iletisinde görünen en yaygın ipuçlarını içeren bir listedir.

  Göstergenin konumu olarak e-posta iletisi konusunu veya ileti gövdesini seçersiniz, Metin **seçin** düğmesi kullanılabilir. İleti konusu veya ileti gövdesinde göstergenin görünmesini istediğiniz metni seçmek için bu düğmeye tıklayın. Bitirdikten sonra Seç'e **tıklayın**.

  :::image type="content" source="../../media/attack-sim-training-payloads-add-indicators-select-location.png" alt-text="Saldırı benzetim eğitimi'nin yük oluşturma sihirbazında bir göstergeye eklemek için ileti gövdesinde seçilen metin konumu" lightbox="../../media/attack-sim-training-payloads-add-indicators-select-location.png":::

  - **Gösterge açıklaması**: Göstergenin varsayılan açıklamasını kabul edilebilir veya bunu özelleştirebilirsiniz.

  - **Gösterge önizlemesi**: Geçerli göstergenin nasıl göründüğünü görmek için bu bölümün içini tıklatın.

  Bitirdikten sonra Ekle'ye **tıklayın.**

Birden çok gösterge eklemek için bu bölümdeki adımları yineler.

Var olan bir göstergeyi düzenlemek için, listeden göstergeyi seçin ve göstergeyi düzenle simgesine ![tıklayın.](../../media/m365-cc-sc-edit-icon.png) **Yükü düzenle'yi seçin**.

Var olan bir göstergeyi silmek için, göstergeyi listeden seçin ve sil simgesine ![tıklayın.](../../media/m365-cc-sc-delete-icon.png) **Sil'i seçin**.

Bitirdikten sonra, Sonraki'ne **tıklayın**.

## <a name="review-payload"></a>Yükü gözden geçirme

Yükü **gözden geçir sayfasında** , yükünizin ayrıntılarını gözden geçirebilirsiniz.

Test gönder ![simgesine tıklayın.](../../media/m365-cc-sc-send-icon.png) **Yüklü e-postanın** bir kopyasını inceleme için kendinize (şu anda oturum açmış olan kullanıcı) göndermek için Test gönder düğmesi.

Önizleme göstergesi ![simgesine tıklayın.](../../media/m365-cc-sc-open-icon.png) **Önizleme göstergesi** düğmesi bir önizleme açılır penceresinde yükü açar. Önizleme, oluşturduğunuz tüm yük göstergelerini içerir.

Ana Yükü **gözden geçir sayfasında** , bölümün içindeki ayarları **değiştirmek** için her bölümde Düzenle'yi seçebilirsiniz. Geri'ye **tıklar** veya sihirbazda belirli bir sayfayı seçersiniz.

Bitirdikten sonra Gönder'e **tıklayın**. Görüntülenen onay sayfasında Bitti'ye **tıklayın**.

:::image type="content" source="../../media/attack-sim-training-payloads-review-payload.png" alt-text="Yeni portalda Saldırı benzetimi eğitimi'nin Yüklerini Microsoft 365 Defender sayfası" lightbox="../../media/attack-sim-training-payloads-review-payload.png":::

> [!IMPORTANT]
> Oluşturduğunuz yüklerde Kaynak özelliği için **Kiracı** **değeri** olur. Benzetimler oluşturmak ve yüklerini seçmek için Kaynak değeri Kiracı'ya filtre **uygulamamayı** **seçin**.

## <a name="related-links"></a>İlgili bağlantılar

[Kullanmaya başlayın benzetimi eğitimlerini kullanma](attack-simulation-training-get-started.md)

[Kimlik avı saldırı benzetimi oluşturma](attack-simulation-training.md)

[Saldırı simülasyonu eğitimiyle içgörüler elde etme](attack-simulation-training-insights.md)
