---
title: Saldırı simülasyonu eğitimi için özel yükler oluşturma
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
description: Yöneticiler, Office 365 için Microsoft Defender Plan 2'de Saldırı simülasyonu eğitimi için özel yük oluşturmayı öğrenebilir.
ms.technology: mdo
ms.openlocfilehash: 8ee202f66d2e9f4fdbf3eba1a1548abd1c3b5524
ms.sourcegitcommit: a8fbaf4b441b5325004f7a2dacd9429ec9d80534
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/26/2022
ms.locfileid: "65739847"
---
# <a name="create-custom-payloads-for-attack-simulation-training-in-defender-for-office-365"></a>Office 365 için Defender'de Saldırı benzetimi eğitimi için özel yük oluşturma

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

[Office 365 için Microsoft Defender plan 2](defender-for-office-365.md) **için geçerlidir**

Saldırı simülasyonu eğitiminde _yük_ , simülasyonlarda kullanıcılara sunulan kimlik avı e-posta iletisi ve web sayfalarıdır. Microsoft 365 E5 veya Office 365 için Microsoft Defender Plan 2'de saldırı simülasyonu eğitimi, kullanılabilir sosyal mühendislik teknikleri için sağlam bir yerleşik yük kataloğu sunar. Ancak, kuruluşunuz için daha iyi çalışacak özel yükler oluşturmak isteyebilirsiniz.

Bu makalede, Saldırı simülasyonu eğitiminde kendi yüklerinizi nasıl oluşturacağınız açıklanmaktadır. Aşağıdaki konumlarda özel yük oluşturabilirsiniz:

- **Payloads**: konumundaki Microsoft 365 Defender portalında<https://security.microsoft.com>**, E-posta & işbirliği** \> **Saldırı benzetimi eğitimi** \> **Simülasyon içerik kitaplığı** sekmesi **Yükleri'ne**\> gidin. **Doğrudan Yükleri** seçebileceğiniz **Simülasyon içerik kitaplığı** sekmesine gitmek için kullanın<https://security.microsoft.com/attacksimulator?viewid=simulationcontentlibrary>.
- Simülasyon oluşturma sırasında: Simülasyon oluşturma sihirbazının **Yük seçin** sayfasında (üçüncü sayfada) özel yükler oluşturabilirsiniz. Daha fazla bilgi için bkz. [Office 365 için Defender'de kimlik avı saldırısı benzetimi](attack-simulation-training.md) yapma.

Saldırı simülasyonu eğitimi hakkında başlangıç bilgileri için bkz. [Saldırı simülasyonu eğitimini kullanarak Kullanmaya başlayın](attack-simulation-training-get-started.md).

> [!NOTE]
> Bazı ticari markalar, logolar, simgeler, insignias ve diğer kaynak tanımlayıcıları, yerel, eyalet ve federal tüzükler ve yasalar kapsamında yüksek koruma alır. Bu tür göstergelerin yetkisiz kullanımı, kullanıcıları cezai para cezaları da dahil olmak üzere cezalara tabi yapabilir. Kapsamlı bir liste olmasa da, buna Başkanlık, Başkan Yardımcısı ve Kongre mühürleri, CIA, FBI, Sosyal Güvenlik, Medicare ve Medicaid, Birleşik Devletler İç Gelir Servisi ve Olimpiyatlar dahildir. Bu ticari marka kategorilerinin ötesinde, herhangi bir üçüncü taraf ticari markanın kullanılması ve değiştirilmesi doğal bir risk taşır. Yükte kendi ticari markalarınızı ve logolarınızı kullanmak, özellikle de kuruluşunuzun kullanıma izin vermesinde daha az riskli olabilir. Yük oluştururken veya yapılandırırken nelerin kullanılması uygun veya uygun olmadığı hakkında başka sorularınız varsa, hukuk danışmanlarınıza danışmanız gerekir.

## <a name="create-a-payload"></a>Yük oluşturma

Yük oluştur simgesine tıkladıktan ![sonra.](../../media/m365-cc-sc-create-icon.png) Saldırı simülasyonu eğitiminin **Simülasyon içerik kitaplığı** sekmesindeki **Yüklerden** **bir yük oluşturun** veya simülasyon oluşturma sihirbazının **[Yük seçin](attack-simulation-training.md#select-a-payload)** sayfasında yük oluşturma sihirbazı başlatılır ve bu bölümde açıklanmaktadır.

### <a name="select-a-payload-type"></a>Yük türü seçme

**Türü seç** sayfasında, şu anda seçebileceğiniz tek değer **E-posta'dır**.

**İleri**'ye tıklayın.

### <a name="select-a-social-engineering-technique"></a>Sosyal mühendislik tekniği seçme

**Tekniği seçin** sayfasında, kullanılabilir seçenekler simülasyon oluşturma sihirbazındaki [Tekniği seç](attack-simulation-training.md#select-a-social-engineering-technique) sayfasındakiyle aynıdır:

- **Kimlik bilgisi toplama**
- **Kötü amaçlı yazılım eki**
- **Ekteki bağlantı**
- **Kötü amaçlı yazılım bağlantısı**
- **Sürücüye göre URL**

İşiniz bittiğinde **İleri'ye** tıklayın.

### <a name="name-and-describe-the-payload"></a>Yükü adlandırma ve açıklama

**Yük adı** sayfasında aşağıdaki ayarları yapılandırın:

- **Ad**: Yük için benzersiz, açıklayıcı bir ad girin.
- **Açıklama**: Yük için isteğe bağlı ayrıntılı bir açıklama girin.

İşiniz bittiğinde **İleri'ye** tıklayın.

## <a name="configure-the-payload"></a>Yükü yapılandırma

**Yükü yapılandır** sayfasında yükünüzü oluşturmanın zamanı geldi. Kullanılabilir ayarların çoğu **, Teknik seçin** sayfasında yaptığınız seçime göre belirlenir (örneğin, bağlantılar ve ekler).

- **Gönderen ayrıntıları** bölümü: Aşağıdaki ayarları yapılandırın:
  - **Kimden adı**
  - **Görünen ad olarak ad kullanın**: Varsayılan olarak, bu ayar seçili değildir.
  - **E-postadan**: Yükünüzün göndereni için bir iç e-posta adresi seçerseniz, yük bir çalışandan geliyor gibi görünür. Bu gönderen e-posta adresi, kullanıcının yüke karşı duyarlılığını artırır ve çalışanları iç tehdit riski konusunda eğitmeye yardımcı olur.
  - **E-posta konusu**

- **Ek ayrıntıları** bölümü: Bu bölüm yalnızca Teknik **seçin** sayfasında **Kötü amaçlı yazılım eki**, **Ekteki bağlantı** veya **Kötü amaçlı yazılıma bağla'yı** seçtiyseniz kullanılabilir. Aşağıdaki ayarları yapılandırın:
  - **Ekinize ad verin**
  - **Bir ek türü seçin**: Şu anda tek kullanılabilir değer **Docx'tir**.

- **Ek bölümü bağlantısı**: Bu bölüm yalnızca **Tekniği seç** sayfasında **Kötü amaçlı yazılıma bağla** seçeneğini belirlediğinizde kullanılabilir. **Kötü amaçlı yazılım eki olmak istediğiniz URL'yi seçin bağlantı** kutusunda, kullanılabilir URL'lerden birini (**Kimlik Avı bağlantısı** bölümünde açıklanan URL'ler) seçin.

  Daha sonra URL'yi iletinin gövdesine ekleyeceksiniz.

- **Kimlik avı bağlantısı** bölümü: Bu bölüm yalnızca, **Teknik seçin** sayfasında **Kimlik bilgisi toplama**, **Ekteki bağlantı** veya **Sürücüye göre URL'yi** seçtiyseniz kullanılabilir.

  **Kimlik bilgisi toplama** veya **Sürüş URL'si** için, kutunun adı **Kimlik avı bağlantınız olmasını istediğiniz URL'yi seçin** şeklindedir. Daha sonra URL'yi iletinin gövdesine ekleyeceksiniz.

  **Ekteki bağlantı** için, kutunun adı **Bu ekte kimlik avı bağlantınız olmasını istediğiniz bir URL seçin** şeklindedir. Daha sonra, URL'yi eke ekleyeceksiniz.

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
  > URL saygınlığı hizmeti, bu URL'lerden birini veya daha fazlasını güvenli olmayan olarak tanımlayabilir. Url'yi simülasyonda kullanmadan önce desteklenen web tarayıcılarınızda URL'nin kullanılabilirliğini denetleyin. Daha fazla bilgi için bkz[. Google Kasa Gözatma tarafından engellenen kimlik avı benzetimi URL'leri](attack-simulation-training-faq.md#phishing-simulation-urls-blocked-by-google-safe-browsing).

- **Ek içeriği** bölümü: Bu bölüm yalnızca **Tekniği seç** sayfasında **Ekte bağla seçeneğini** belirlediğinizde kullanılabilir.

  Dosya eki yükünüzdeki içeriği oluşturmanız için zengin bir metin düzenleyicisi kullanılabilir.

  Eke daha önce seçilen kimlik avı URL'sini eklemek için Kimlik Avı **bağlantısı** denetimini kullanın.

- Genel ayarlar:
  - **Etiket ekleme**
  - **Tema**: Hesap **Etkinleştirme**, **Hesap Doğrulama**, **Faturalama**, **Posta Temizleme**, **Alınan Belge**, **Gider**, **Faks**, **Finans Raporu**, **Gelen İletiler**, **Fatura**, **Alınan Öğe**, **Oturum Açma Uyarısı**, **Alınan Posta**, **Diğer**, **Parola**, **Ödeme**, **Bordro**, **Kişiselleştirilmiş Teklif**, **Karantina** , **Uzaktan Çalışma**, **İletiyi Gözden Geçirme**, **Güvenlik Güncelleştirmesi**, **Hizmet Askıya Alındı**, **İmza Gerekli**, **Posta Kutusunu Yükseltme Depolama**, **Posta kutusunu doğrulama** veya **Sesli mesaj**.
  - **Marka**: Kullanılabilir değerler şunlardır: **American Express**, **Capital One**, **DHL**, **DocuSign**, **Dropbox**, **Facebook**, **First American**, **Microsoft**, **Netflix**, **Scotiabank**, **SendGrid**, **Stewart Title**, **Tesco**, **Wells Fargo**, **Syrinx Cloud** veya **Diğer**.
  - **Endüstri**: Mevcut değerler şunlardır: **Bankacılık**, **İş hizmetleri**, **Tüketici hizmetleri**, **Eğitim**, **Enerji**, **İnşaat**, **Danışmanlık**, **Finansal hizmetler**, **Kamu**, **Konaklama**, **Sigorta**, **Yasal**, **Kurye hizmetleri**, **BT**, **Sağlık**, **Üretim**, **Perakende**, **Telekom**, **Emlak** veya **Diğer**.
  - **Geçerli olay**: Kullanılabilir değerler **Evet** veya **Hayır'dır**.
  - **Tartışmalı**: Kullanılabilir değerler **Evet** veya **Hayır'dır**.

- **Dil** bölümü: Yükün dilini seçin. Kullanılabilir değerler şunlardır: **İngilizce**, **İspanyolca**, **Almanca**, **Japonca**, **Fransızca**, **Portekizce**, **Felemenkçe**, **İtalyanca**, **İsveççe**, **Çince (Basitleştirilmiş)**, **Norveççe Bokmål**, **Lehçe**, **Rusça**, **Fince**, **Korece**, **Türkçe**, **Macarca**, **İbranice**, **Tayca**, **Arapça**, **Vietnamca**, **Slovakça**, **Yunanca**, **Endonezya dili**, **Rumence**, **Slovence**, **Hırvat,** **Katalanca** veya **Diğer**.

- **E-posta iletisi** bölümü:

  - Var olan bir düz metin iletisi dosyasını içeri aktarmak için **E-postayı içeri aktar'a** ve ardından **Dosya seç'e** tıklayabilirsiniz.

  - **Metin** sekmesinde, e-posta iletisi yükünüzü oluşturmanız için zengin bir metin düzenleyicisi sağlanır.

    - Kullanılabilir etiketleri ekleyerek her kullanıcı için e-posta iletisini kişiselleştirmek için **Dinamik etiket** denetimini kullanın:
      - **Ad ekle**: İleti gövdesine eklenen değer olur `${userName}`.
      - **E-posta ekle**: İleti gövdesine eklenen değer olur `${emailAddress}`.

      :::image type="content" source="../../media/attack-sim-training-payloads-configure-payload-email-message.png" alt-text="Office 365 için Microsoft Defender'deki Saldırı benzetimi eğitimi'ndeki yük oluşturma sihirbazının Yükü yapılandır sayfasındaki E-posta iletisi bölümü" lightbox="../../media/attack-sim-training-payloads-configure-payload-email-message.png":::

      **Kimlik avı bağlantısı** denetimi: Bu denetim yalnızca, **Seç tekniği** sayfasında **Kimlik bilgisi toplama**, **Ekteki bağlantı** veya **Sürücüye göre URL'yi** seçtiyseniz kullanılabilir. **Kimlik avı bağlantısı** bölümünde daha önce seçtiğiniz URL'yi eklemek için bu denetimi kullanın.

      **Kötü amaçlı yazılım eki bağlantı** denetimi: Bu denetim, yalnızca **Seç tekniği** sayfasında **Kötü amaçlı yazılıma bağla** seçeneğini belirlediğinizde kullanılabilir. **Ek için bağlantı** bölümünde daha önce seçtiğiniz URL'yi eklemek için bu denetimi kullanın.

      **Kimlik avı bağlantısına** veya **Kötü amaçlı yazılım eki bağlantısına** tıklarsanız, bağlantıyı adlandırmanızı isteyen bir iletişim kutusu açılır. İşiniz bittiğinde **Onayla'ya** tıklayın.

      İleti gövdesine eklenen değerdir (**Kod** sekmesinde görünür).`<a href="${phishingUrl}" target="_blank">Name value you specified</a>`

  - **Kod** sekmesinde HTML kodunu doğrudan görüntüleyebilir ve değiştirebilirsiniz. **Biçimlendirme ve Dinamik etiket** ve **Kimlik Avı bağlantısı** veya **Kötü amaçlı yazılım ek bağlantısı** gibi diğer denetimler kullanılamaz.

  - **E-posta iletisindeki tüm bağlantıları kimlik avı bağlantısıyla değiştir iki durumlu** düğmesi, yalnızca **Teknik seçin** sayfasında **Kimlik bilgisi toplama**, **Kötü amaçlı yazılıma bağlantı** veya **Sürücü URL'sini** seçtiyseniz kullanılabilir. Bu iki durumlu düğme, iletideki tüm bağlantıları önceden seçilen **Kimlik Avı bağlantısı** veya Ek URL'si **için bağlantı** ile değiştirerek zaman kazandırabilir. Bunu yapmak için ayarı ![Açık konuma getirin simgesi..](../../media/scc-toggle-on.png).

İşiniz bittiğinde **İleri'ye** tıklayın.

## <a name="add-indicators-to-phishing-clues"></a>Kimlik avı ipuçlarına gösterge ekleme

> [!NOTE]
> **Teknik seçin** sayfasında **Kötü amaçlı yazılım eki** veya **Kötü amaçlı yazılım bağlantısı'nı** seçtiyseniz göstergeler kullanılamaz.

Göstergeler, çalışanların saldırı simülasyonunu kullanarak kimlik avı iletilerinin hikaye işaretlerini tanımlamalarına yardımcı olur.

**Gösterge ekle** sayfasında **Gösterge ekle'ye** tıklayın. Görüntülenen açılır öğede aşağıdaki ayarları yapılandırın:

- **Gösterge adı** ve **Gösterge konumu**: Bu değerler birbiriyle ilişkilidir. Göstergeyi yerleştirebileceğiniz yer, göstergenin kendisine bağlıdır. Kullanılabilir değerler aşağıdaki tabloda açıklanmıştır:

  |Gösterge adı|Gösterge konumu|
  |---|---|
  |**Ek türü**|İleti gövdesi|
  |**Dikkat dağıtıcı ayrıntı**|İleti gövdesi|
  |**Etki alanı kimlik sahtekarlık**|İleti gövdesi <p> E-posta adresinden|
  |**Genel karşılama**|İleti gövdesi|
  |**İnsani temyizler**|İleti gövdesi|
  |**Tutarsız -lık**|İleti gövdesi|
  |**Gönderen ayrıntılarının olmaması**|İleti gövdesi|
  |**Yasal dil**|İleti gövdesi|
  |**Sınırlı süreli teklif**|İleti gövdesi|
  |**Logo taklit veya tarihli markalama**|İleti gövdesi|
  |**bir iş veya iş sürecini taklit eder**|İleti gövdesi|
  |**Hayır/minimal markalama**|İleti gövdesi|
  |**Arkadaş, iş arkadaşı, gözetmen veya yetkili figürü olarak pozlar**|İleti gövdesi|
  |**Hassas bilgi isteği**|İleti gövdesi|
  |**Güvenlik göstergeleri ve simgeleri**|İleti gövdesi <p> İleti konusu|
  |**Gönderen görünen adı ve e-posta adresi**|Kimden adı <p> E-posta adresinden|
  |**Aciliyet duygusu**|İleti gövdesi <p> İleti konusu|
  |**Yazım ve dil bilgisi düzensizlikleri**|İleti gövdesi <p> İleti konusu|
  |**Tehdit dili**|İleti gövdesi <p> İleti konusu|
  |**Gerçek teklifler olamayacak kadar iyi**|İleti gövdesi|
  |**Profesyonel olmayan görünümlü tasarım veya biçimlendirme**|İleti gövdesi|
  |**URL köprü oluşturma**|İleti gövdesi|
  |**Sen özelsin.**|İleti gövdesi|
  
  Bu liste, kimlik avı iletilerinde görünen en yaygın ipuçlarını içerecek şekilde seçilmiştir.

  Göstergenin konumu olarak e-posta iletisinin konusunu veya ileti gövdesini seçerseniz, **Metin seç** düğmesi kullanılabilir. İleti konusu veya ileti gövdesinde göstergenin görünmesini istediğiniz metni seçmek için bu düğmeye tıklayın. İşiniz bittiğinde **Seç'e** tıklayın.

  :::image type="content" source="../../media/attack-sim-training-payloads-add-indicators-select-location.png" alt-text="Saldırı benzetimi eğitimindeki yük oluşturma sihirbazındaki bir göstergeye eklenecek ileti gövdesindeki Seçili metin konumu" lightbox="../../media/attack-sim-training-payloads-add-indicators-select-location.png":::

  - **Gösterge açıklaması: Gösterge** için varsayılan açıklamayı kabul edebilir veya özelleştirebilirsiniz.

  - **Gösterge önizlemesi**: Geçerli göstergenin nasıl göründüğünü görmek için bu bölümün içine tıklayın.

  İşiniz bittiğinde **Ekle'ye** tıklayın

Birden çok gösterge eklemek için bu bölümdeki adımları yineleyin.

Var olan bir göstergeyi düzenlemek için listeden bu göstergeyi seçin ve göstergeyi düzenle simgesine tıklayın ![.](../../media/m365-cc-sc-edit-icon.png) **Yükü düzenle**.

Var olan bir göstergeyi silmek için listeden seçip Sil simgesine tıklayın ![.](../../media/m365-cc-sc-delete-icon.png) **Sil'i seçin**.

İşiniz bittiğinde **İleri'ye** tıklayın.

## <a name="review-payload"></a>Yükü gözden geçirme

**Yükü gözden geçir** sayfasında yükünüzün ayrıntılarını gözden geçirebilirsiniz.

![Test gönder simgesine tıklayın.](../../media/m365-cc-sc-send-icon.png) Yük e-postasının bir kopyasını inceleme için kendinize (şu anda oturum açmış olan kullanıcı) göndermek için **bir test düğmesi gönderin**.

![Önizleme göstergesi simgesine tıklayın.](../../media/m365-cc-sc-open-icon.png) **Önizleme göstergesi** düğmesi, yükü önizleme açılır penceresinde açar. Önizleme, oluşturduğunuz tüm yük göstergelerini içerir.

Ana **Yükü gözden geçir** sayfasında, bölümdeki ayarları değiştirmek için her bölümde **Düzenle'yi** seçebilirsiniz. Ya da **Geri'ye** tıklayabilir veya sihirbazdaki belirli bir sayfayı seçebilirsiniz.

İşiniz bittiğinde **Gönder'e** tıklayın. Görüntülenen onay sayfasında **Bitti'ye** tıklayın.

:::image type="content" source="../../media/attack-sim-training-payloads-review-payload.png" alt-text="Microsoft 365 Defender portalındaki Saldırı simülasyonu eğitimi sayfasındaki Yükü gözden geçirme sayfası" lightbox="../../media/attack-sim-training-payloads-review-payload.png":::

> [!IMPORTANT]
> Oluşturduğunuz yüklerin **Source** özelliği için **Kiracı** değeri olacaktır. Simülasyonlar oluşturduğunuzda ve yükleri seçtiğinizde **, Kaynak** değeri **Kiracısı'nı** filtrelemediğinizden emin olun.

## <a name="related-links"></a>İlgili bağlantılar

[Saldırı simülasyonu eğitimini kullanmaya başlama](attack-simulation-training-get-started.md)

[Kimlik avı saldırısı simülasyonu oluşturma](attack-simulation-training.md)

[Saldırı simülasyonu eğitimiyle içgörüler elde etme](attack-simulation-training-insights.md)
