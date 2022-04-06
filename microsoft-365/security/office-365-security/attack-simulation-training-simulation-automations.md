---
title: Saldırı benzetimi eğitimi için benzetim otomasyonları
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
description: Yöneticiler, Plan 2 için Microsoft Defender'da belirtilen koşullar karşılandıklarında başlatan belirli teknikler ve yüklemeler içeren otomatik benzetimler Office 365 öğrenebilir.
ms.technology: mdo
ms.openlocfilehash: 3ad24a8b6d2be18fb7ef5fd49be7f2197b3be3a7
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2022
ms.locfileid: "63680962"
---
# <a name="simulation-automations-for-attack-simulation-training"></a>Saldırı benzetimi eğitimi için benzetim otomasyonları

 [Office 365 için Microsoft Defender plan 2 için geçerlidir](defender-for-office-365.md)

Saldırı benzetimi eğitimi hakkında bilgi almak için bkz. [Saldırı benzetimi eğitimlerini kullanmaya başlama](attack-simulation-training-get-started.md).

Benzetim otomasyonu oluşturmak için aşağıdaki adımları uygulayın:

1. aşağıdaki Microsoft 365 Defender portalında, <https://security.microsoft.com/>E-posta ve işbirliği **&** \> **benzetim eğitimi Benzetim** \> **otomasyonları sekmesine** gidin.

   Doğrudan Benzetim **otomasyonları sekmesine gitmek** için kullanın <https://security.microsoft.com/attacksimulator?viewid=simulationautomation>.

2. Benzetim **otomasyonları sekmesinde** Otomasyon simgesi oluştur'a ![tıklayın.](../../media/m365-cc-sc-create-icon.png) **Otomasyon oluşturun**.

   ![Proje portalında, Saldırı benzetimi eğitimi'nin Benzetim otomasyonları sekmesindeki Microsoft 365 Defender oluşturun.](../../media/attack-sim-training-sim-automations-create.png)

3. Oluşturma sihirbazı açılır. Bu makalenin kalan kalanında, sayfaları ve bunların içerdiği ayarlar açıklanmıştır.

> [!NOTE]
> Benzetim oluşturma sihirbazının herhangi bir noktasında, ilerlemenizi kaydetmek  ve benzetimi daha sonra yapılandırmaya devam etmek için Kaydet ve kapat'a tıklarsınız. Tamamlanmamış benzetimlerin **Benzetimler** **sekmesinde** Durum değeri **Taslağı** vardır. Benzetimi seçerek ve benzetim simgesini düzenle'ye tıklayarak, kalan yerden ![devamabilirsiniz.](../../media/m365-cc-sc-edit-icon.png) **Benzetimi** düzenleyin.## Benzetimi adla ve açıkların.

## <a name="name-and-describe-the-simulation-automation"></a>Benzetim otomasyonunu adla ve açıklar

Otomasyon **adı sayfasında** aşağıdaki ayarları yapılandırabilirsiniz:

- **Ad**: Benzetim için benzersiz, açıklayıcı bir ad girin.
- **Açıklama**: Benzetim için isteğe bağlı olarak ayrıntılı bir açıklama girin.

Bitirdikten sonra, Sonraki'ne **tıklayın**.

## <a name="select-one-or-more-social-engineering-techniques"></a>Bir veya daha fazla sosyal mühendislik tekniği seçme

Sosyal mühendislik **tekniklerini seçin** sayfasında, [MITRE ATT ve CK® framework'lerinden bir veya daha fazla kullanılabilir sosyal mühendislik&seçin](https://attack.mitre.org/techniques/enterprise/). Farklı teknikler için farklı yük kullanılabilir. Aşağıdaki sosyal mühendislik tekniklerini kullanabilirsiniz:

- **Kimlik bilgileri toplama**: Kullanıcıları bir kullanıcı adı ve parola göndermek üzere giriş kutuları olan iyi bilinen bir web sitesine götürerek kimlik bilgilerini toplamaya çalışır.
- **Kötü amaçlı yazılım** eki: İletiye kötü amaçlı bir ek ekler. Kullanıcı eki açtığında, rastgele kod çalıştırarak saldırgan hedef cihazı tehlikeye atabilir.
- **Ekin bağlantısı**: Karma için bir kimlik bilgisi türü. Bir saldırgan e-posta eke bir URL ekler. Ekin içindeki URL, kimlik bilgisi toplama yöntemiyle aynı teknikten sonra gelir.
- **Kötü amaçlı yazılıma** bağlantı: İyi bilinen bir dosya paylaşım hizmetlerinden barındırılan bir dosyadan bazı rastgele kodlar çalıştırır. Kullanıcıya gönderilen ileti, bu kötü amaçlı dosyanın bağlantısını içerir. Dosyayı açma ve saldırgana hedef cihazı tehlikeye atma konusunda yardımcı olun.
- **Sürücüye Göre URL**: İletide yer alan kötü amaçlı URL, kullanıcıya, kullanıcının cihazında kodu sessiz olarak çalıştıran ve/veya yüken tanıdık görünümlü bir web sitesine alır.

Açıklamada Ayrıntıları **görüntüle bağlantısına** tıklarsanız, tekniğin ve teknikten elde edilen benzetim adımlarını açıklayan bir ayrıntılar açılır.

![Sosyal mühendislik tekniklerini seçin sayfasındaki kimlik bilgisi toplama tekniği ile ilgili ayrıntılar çıktısı.](../../media/attack-sim-training-simulations-select-technique-sim-steps.png)

Bitirdikten sonra, Sonraki'ne **tıklayın**.

## <a name="select-payloads"></a>Yüklerini seçin

Yüklerini **seç sayfasında** aşağıdaki seçeneklerden birini belirleyin:

- **El ile**
- **Rastgele**

Rastgele **Ekle'yi seçtiysanız**, bu sayfada yapılandıracak hiçbir şey yoktur; devam etmek için **Sonraki'ne** tıklayın.

El ile **seç'i** seçerek listeden bir veya daha fazla yük seçmeniz gerekir. Aşağıdaki ayrıntılar, seçime yardımcı olmak için görüntülenir:

- **Yük adı**
- **Teknik**: Önceki sayfada seçtiğiniz teknik başına en az bir yük seçmeniz gerekir.
- **Dil**: Yük içeriğinin dili. Microsoft'un yük kataloğu (genel) 10'dan fazla dilde yük sağlar ve bu da filtre kullanılabilir.
- **Ücrete** tıklayın: Bu yüke kaç kişi tıklamış?
- **Öngörülen güvenlik oranı**: Yük genelindeki yükle ilgili geçmiş veriler Microsoft 365 yükten tehlikeye atacak olan kişi yüzdesini tahmin ediyor.
- **Benzetimler** başlatıldı, bu yüklemenin diğer benzetimlerde kaç kez kullanıldıklarını sayar.

![Ara simgesinde.](../../media/m365-cc-sc-search-icon.png) **Arama** kutusunda, yükün adının bir kısmını yazın ve Enter tuşuna basarak sonuçları filtrelenin.

**Filtre'ye tıklarsanız**, aşağıdaki filtreler kullanılabilir:

- **Karmaşıklık**: Yük yükünde olası bir saldırının (yazım hataları, aciliyet, vb.) olduğunu belirten gösterge sayısına bağlı olarak hesaplanır. Daha fazla gösterge, saldırı olarak tanımlamak daha kolaydır ve daha düşük karmaşıklık gösterir. Kullanılabilir değerler:
  - **Düşük**
  - **Orta**
  - **Yüksek**
- **Kaynak**: Yükün kurumda oluşturularak mı yoksa Microsoft'un önceden var olan yük kataloğunda mı yer alıyor olduğunu gösterir. Geçerli değerler:
  - **Global**
  - **Kiracı**
  - **Hepsi**
- **Dil**: Kullanılabilir **değerler: İngilizce**, **İspanyolca****, Almanca**, **Japonca, Fransızca****,** **Portekizce**, **Felemenkçe****, İtalyanca****, İsveç** dili, **Çince (Basitleştirilmiş)**, **Norveççe Bokmål**, **Lehçe****, Rusça**, **Fince****,** **Kore dili**, Türkçe, **Macarca**, **İbranice**, **Tay** dili, **Arapça**, **Vietnamca**, **Slovakça**, **Yunanca**, **Endonezya Dili**, **Rumence**, **Slovence**, **Hırvatça**, **Katalanca** ve **Diğer**.
- **Etiket ekle**
- **Temaya** göre filtreleme: Kullanılabilir **değerler: Hesap** **etkinleştirme, Hesap** **doğrulama, Faturalama****,** Postayı **temizleme, Alınan** belge, **Gider**, **Faks****, Finans** raporu, **Gelen iletiler**, **Fatura****, Öğeler** **alındı, Oturum** açma uyarısı, **Alınan posta**, **Parola**, **Ödeme**, **Bordro**, **Kişiselleştirilmiş teklif****, Karantina**, **Uzaktan çalışma**, **İletiyi gözden geçir****, Güvenlik** **güncelleştirmesi,** Hizmet askıya alındı, İmza **gerekli**, **Posta kutusu depolamasını yükseltme Posta** kutusunu, **Sesli** mesajı ve Diğer'i **doğrulayın**.
- Markaya göre filtrele **: Kullanılabilir** değerler: **American Express**, **Capital One**, **DHL**, **DocuSign**, **Dropbox**, **Facebook**, **First American**, **Microsoft**, **Netflix**, **Scotiabank**, **SendGrid**, **Title**, **Tgrid**, **Wells Fargo**, **Syrinx Cloud** ve **Other**.
- **Sektöre** göre filtre uygulama: Kullanılabilir **değerler: Bankacılık****, İş** **hizmetleri, Tüketici** hizmetleri, **Eğitim**, **Enerji**, **Inşaat**, **Danışmanlık**, **Finansal** hizmetler, **Kamu****, Hastane**, **Sigorta**, **Yasal**, **Courier** hizmetleri, **IT**, **Sağlık**, **Üretim**, **Perakende**, **Telecom**, **Emlak**, ve **Diğer'i de.**
- **Geçerli olay**: Kullanılabilir değerler Evet **veya** **Hayır'dır**.
- **Neden**: Kullanılabilir değerler Evet **veya** **Hayır'dır**.

Filtreleri yapılandırmayı bitirdikten sonra, Filtreleri Uygula, İptal **et** **veya Temizle'yi** **tıklatın**.

Adı tıklatarak listeden bir yük seçersiniz, yükle ilgili ayrıntılar bir çıkışta gösterilir:

- Genel **Bakış** sekmesi, yük hakkında bir örnek ve diğer ayrıntıları içerir.
- **Benzetimler başlatıldı** sekmesi Benzetim adı, **Tıklama** oranı, Güvenliği **ihlal** **edildi oranı ve** **Eylem'i içerir**.

![Geçiş portalında Saldırı benzetimi eğitimi altında ayrıntıları Microsoft 365 Defender.](../../media/attack-sim-training-simulations-select-payload-details.png)

Bitirdikten sonra, Sonraki'ne **tıklayın**.

## <a name="target-users"></a>Hedef kullanıcılar

Hedef **kullanıcılar sayfasında** benzetimi alacak olan kullanıcıları seçin. Aşağıdaki ayarlardan birini yapılandırma:

- **Organizasyon dahil tüm kullanıcıları dahil:** Etkilenen kullanıcılar 10 listelerinde gösterir. Listede kaydırmak **için kullanıcı** **listesinin** hemen altındaki Sonraki ve Önceki düğmelerini kullanabilirsiniz. Arama simgesini de ![kullanabilirsiniz.](../../media/m365-cc-sc-search-icon.png) **Etkilenen** kullanıcıları bulmak için sayfada Ara simgesi.
- **Yalnızca belirli kullanıcıları ve grupları dahil** etmek için: Aşağıdaki seçeneklerden birini belirleyin:
  - ![Kullanıcı ekle simgesi.](../../media/m365-cc-sc-create-icon.png) **Kullanıcı ekleme**: Görüntülenen **Kullanıcı ekle** açılır yapısında, kullanıcıları ve grupları aşağıdaki ölçütlere göre bulabilirsiniz:
    - **Kullanıcılar veya gruplar**: Kullanıcıları ![ve grupları ara simgesinde.](../../media/m365-cc-sc-search-icon.png) **Kullanıcıları ve grupları ara kutusunda**, Kullanıcının veya grubun Ad veya E-posta adresinin bir kısmını yazarak Enter tuşuna basabilirsiniz.  Sonuçların bir veya hepsini seçin. Bitirdikten sonra X kullanıcı **ekle'ye tıklayın**.

      > [!NOTE]
      > Kullanıcıları **kategorilere göre** filtrele seçeneklerine dönmek  için Filtre ekle düğmesine tıkıldığında, arama sonuçlarında seçtiğiniz tüm kullanıcılar veya gruplar temiz olur.

    - **Kullanıcıları kategorilere göre filtreleme**: Yok, bazıları veya tüm aşağıdaki seçeneklerden birini belirleyin:
      - **Önerilen kullanıcı grupları**: Aşağıdaki değerlerden birini seçin:
        - **Tüm önerilen kullanıcı grupları**
        - **Son üç ay içinde kullanıcılar bir benzetim tarafından hedef kitleye ulaşmdı**
        - **Yinelemelileri yineleme**
      - **Bölüm**: Aşağıdaki seçenekleri kullanın:
        - **Ara**: Departmana ![Göre Ara simgesinde.](../../media/m365-cc-sc-search-icon.png) **Departmana Göre** Ara kutusu; Departman değerinin bir bölümünü yazın ve Enter tuşuna basın. Sonuçların bir veya hepsini seçin.
        - Tüm **Departmanları Seçme**
        - Mevcut Departman değerlerini seçin.
      - **Başlık**: Aşağıdaki seçenekleri kullanın:
        - **Arama**: Başa ![Göre Ara simgesinde.](../../media/m365-cc-sc-search-icon.png) **Başt'a** Göre Ara kutusunda, Başlık değerinin bir bölümünü yazın ve Enter tuşuna basın. Sonuçların bir veya hepsini seçin.
        - Tüm **Başlığı Seç**
        - Mevcut Başlık değerlerini seçin.

      ![Hedef kullanıcılar sayfasındaki Saldırı benzetimi eğitimi sayfasındaki kullanıcı filtrelemesi Microsoft 365 Defender.](../../media/attack-sim-training-simulations-target-users-filter-by-category.png)

      Ölçütlerinizi tanımdikten sonra, etkilenen kullanıcılar görüntülenen Kullanıcı listesi bölümünde gösterilir  ve burada bulunan alıcıların bir bölümünü veya hepsini seçebilirsiniz.

      Bitirdikten sonra Uygula **(x)'e tıklayın** ve sonra da X kullanıcı **ekle'ye tıklayın**.

  Ana Hedef kullanıcılar **sayfasına** dönüp Arama simgesini kullanabilirsiniz ![.](../../media/m365-cc-sc-search-icon.png) **Etkilenen** kullanıcıları bulmak için arama kutusu. Ayrıca Sil simgesine de ![tıkabilirsiniz.](../../media/m365-cc-sc-delete-icon.png) **Belirli** kullanıcıları kaldırmak için silin.

- ![İçeri Aktar simgesi.](../../media/m365-cc-sc-create-icon.png) **İçeri** Aktar: Açılan iletişim kutusunda, satır başına bir e-posta adresi içeren bir CSV dosyası belirtin.

  CSV dosyasını buktan sonra, kullanıcı listesi içeri aktarılır ve Hedefli kullanıcılar **sayfasında** gösterilir. Arama simgesini ![kullanabilirsiniz.](../../media/m365-cc-sc-search-icon.png) **Etkilenen** kullanıcıları bulmak için arama kutusu. Ayrıca Sil simgesine de ![tıkabilirsiniz.](../../media/m365-cc-sc-delete-icon.png) **Belirli** kullanıcıları kaldırmak için silin.

Bitirdikten sonra, Sonraki'ne **tıklayın**.

## <a name="assign-training"></a>Eğitim atama

Eğitim **atama sayfasında** benzetim için eğitimler atabilirsiniz. Eğitimde geçen çalışanlar benzer saldırılara karşı daha az duyarlıklı olduğu için her benzetim için eğitim atamanız önerilir. Aşağıdaki ayarlar kullanılabilir:

- **Eğitim içeriği tercihini** seçin: Aşağıdaki seçeneklerden birini belirleyin:
  - **Microsoft eğitim deneyimi**: Bu, yapılandırmada aşağıdaki ilişkili seçeneklerin yer alan varsayılan değerdir:
    - Aşağıdaki seçeneklerden birini belirleyin:
      - **Benim için eğitim ata**: Bu, varsayılan ve önerilen değerdir. Bir kullanıcının önceki benzetim ve eğitim sonuçlarına göre eğitim atadığınız gibi, sihirbazın sonraki adımlarında da seçimleri gözden geçirebilirsiniz.
      - **Eğitim kursları ve modülleri** kendim seçiyorum: Bu değeri seçersiniz, sihirbazın sonraki adımlarında önerilen içeriği ve kullanılabilir tüm kursları ve modülleri görmeye devam edersiniz.
    - **Son tarih**: Aşağıdaki değerlerden birini seçin:
      - **Benzetim sona erdikten 30 gün** sonra: Bu varsayılan değerdir.
      - **Benzetim sona erdikten 15 gün sonra**
      - **Benzetim sona erdikten 7 gün sonra**
  - **Özel bir URL'ye yeniden yönlendirme**: Bu değerin yapılandırılması için aşağıdaki ilişkili seçenekler vardır:
    - **Özel eğitim URL'si** (gerekli)
    - **Özel eğitim adı** (gerekli)
    - **Özel eğitim açıklaması**
    - **Özel eğitim süresi (dakika olarak)**: Varsayılan değer 0'dır, bu da eğitim için belirtilen sürenin olmadığını anlamına gelir.
    - **Son tarih**: Aşağıdaki değerlerden birini seçin:
      - **Benzetim sona erdikten 30 gün** sonra: Bu varsayılan değerdir.
      - **Benzetim sona erdikten 15 gün sonra**
      - **Benzetim sona erdikten 7 gün sonra**
  - **Eğitim yok**: Bu değeri seçerseniz, sayfada yer alan tek seçenek Giriş sayfası sayfasına sizi  alan Sonraki [**düğmesidir**](#landing-page).

![Yeni portalda Saldırı benzetimi eğitimi'nin Eğitim ödev sayfasına önerilen Microsoft 365 Defender ekleyin.](../../media/attack-sim-training-simulations-assign-training-add-recommended-training.png)

### <a name="training-assignment"></a>Eğitim ödevi

> [!NOTE]
> Eğitim **ödev sayfası** , yalnızca Microsoft eğitim deneyimini **seçtiyken** \> önceki sayfada kendim eğitim **kursları ve modülleri** seçiyorum.

Eğitim **atama sayfasında** , Eğitim ekle simgesine tıklayarak benzetime eklemek istediğiniz ![eğitimleri seçin.](../../media/m365-cc-sc-create-icon.png) **Eğitimler ekleyin**.

Görüntülenen **Eğitim ekle** açılır öğesinin altında, kullanılabilir olan aşağıdaki sekmelerde kullanmak üzere eğitimleri seçin:

- **Önerilen** sekmesi: Benzetim yapılandırmasına dayalı olarak, önerilen yerleşik eğitimleri gösterir. Önceki sayfada Benim için eğitim ata'nın seçili olmasıyla aynı eğitimler atanmıştır.
- **Tüm eğitimler** sekmesi: Kullanılabilen tüm yerleşik eğitimleri gösterir.

  Her eğitim için aşağıdaki bilgiler gösterilir:

  - **Eğitim adı**
  - **Kaynak**: Değer **Genel'dir**.
  - **Süre (mins)**
  - **Önizleme**: Eğitimi **görmek** için Önizleme düğmesine tıklayın.

  ![Ara simgesinde.](../../media/m365-cc-sc-search-icon.png) **Arama** kutusunda, eğitim adının bir bölümünü yazın ve Enter tuşuna basarak geçerli sekmede yer alan sonuçları filtreleyebilirsiniz.

  Geçerli sekmeden eklemek istediğiniz tüm eğitimleri seçin ve Ekle'ye **tıklayın**.

Ana Eğitim atama **sayfasına** geri dönebilirsiniz; seçtiğiniz eğitimler gösterilir. Her eğitim için aşağıdaki bilgiler gösterilir:

- **Eğitim adı**
- **Kaynak**
- **Süre (mins)**

Listede yer alan her eğitim için, Ata sütunundaki değerleri seçerek eğitimi kimlerin **alasınız? öğesini seçmeniz** gerekir:

- **Tüm kullanıcılar**

  ya da aşağıdaki değerlerden birini veya her ikisini birden kullanabilirsiniz:

- **Tıklı yük**
- **Güvenliği ihlal edildi**

Gösterilen bir eğitimi kullanmak istemiyorsanız, Sil simgesine ![tıklayın.](../../media/m365-cc-sc-delete-icon.png) **Sil'i seçin**.

![Geçiş portalında Saldırı benzetimi eğitimi'nin Microsoft 365 Defender sayfası.](../../media/attack-sim-training-training-assignment.png)

Bitirdikten sonra, Sonraki'ne **tıklayın**.

### <a name="landing-page"></a>Giriş sayfası

Giriş **sayfası sayfasında** , yükleme benzetimde bir yük açılırsa kullanıcının ziyarette olduğu web sayfasını yapılandırabilirsiniz.

- **Giriş sayfası tercihini** seçin: Kullanılabilir değerler, aşağıdaki tabloda açıklandığı gibi [Yük](#select-payloads) seçin sayfasındaki önceki seçimlerinize bağlıdır:

  |Yüklemeleri seç sayfasında seçim|Giriş sayfası tercihini seçme için kullanılabilir değerler|
  |---|---|
  |El ile|Microsoft varsayılan giriş sayfasını kullanma <p> Kendi giriş sayfanızı oluşturma <p> Özel URL kullanma <p> **Not**: **Daha önce Sosyal mühendislik** tekniklerini seçin sayfasında Kötü amaçlı yazılım eki veya  Kötü amaçlı yazılıma bağlantı ekle'yi seçtiysanız Özel URL [değeri kullan seçeneği](#select-one-or-more-social-engineering-techniques) kullanılamaz.|
  |Rastgele|Microsoft varsayılan giriş sayfasını kullanma|

  Kullanılabilir Giriş **sayfası tercih değerlerini** ve ilişkili ayarlarını seçin seçeneği aşağıdaki listede açıklanmıştır:

  - **Microsoft varsayılan giriş sayfasını kullanın**. Bu varsayılan değerdir ve tüm yüklerde geçerli olan bir Microsoft varsayılan şablonu, logosu ve yük göstergesi eylemiyle sonuç verir.

    Giriş sayfası sayfasında aşağıdaki ek ayarları **yapılandırmanız** gerekir:

    - **Giriş sayfası düzenini seçin**: Kullanılabilir 5 giriş sayfası şablonudan birini seçin.
    - **Logo ekleme**: Microsoft  tarafından seçilen tüm yüklere eklemek üzere .png, .jpeg veya .gif dosya bulmak ve seçmek için Gözat'a tıklayın. Bozulmayı önlemek için logo boyutu en fazla 210 x 70 olabilir. Logoyu kaldırmak için Kaldır'a **tıklayın**.
    - **Yük göstergeleri: Daha önce** Sosyal mühendislik tekniklerini seçin sayfasında Kötü amaçlı yazılım  eki veya Kötü  amaçlı yazılıma bağlantı ekle'yi seçtiyseniz [bu ayar](#select-one-or-more-social-engineering-techniques) kullanılamaz.

      Kullanıcıların **kimlik avı iletilerini tanımlamayı öğrenmelerine yardımcı olmak için** E-postaya yük göstergeleri ekle'yi seçin.

    Sayfanın ortasındaki Önizleme panelini **aç düğmesine tıklayarak** sonuçların önizlemesini görüntüleyebilirsiniz. Görüntülenen önizleme açılır penceresinde, her yükten nasıl göründüğünü görmek  için Yük seçin öğesini kullanabilirsiniz.

  - **Kendi giriş sayfanızı oluşturma**: Bu değer, seçilen yüklere uygulanan tek bir yük göstergesi eylemiyle sonuç verir.

    Giriş sayfası sayfasında aşağıdaki ek ayarları **yapılandırmanız** gerekir:

    - **Yük göstergeleri**: Bu ayar yalnızca aşağıdaki koşullardan her ikisi de geçerli olduğu zaman kullanılabilir:
      - Sosyal mühendislik **tekniklerini seçin** sayfasında **Daha önce** Kimlik bilgisi toplama, Ek içinde bağlantı veya **Sürücü** [URL'si seçeneğini seçtiniz](#select-one-or-more-social-engineering-techniques) .
      - Sayfa içeriğine **E-posta içeriği** **ekle adlı** Dinamik etiketi eklemenizden sonra.

    - Sayfa içeriği: İki sekme kullanılabilir:

      - **Metin**: Giriş sayfanız oluşturmak için zengin bir metin düzenleyicisi kullanılabilir. Normal yazı tipi ve biçimlendirme ayarlarına ek olarak, aşağıdaki ayarlar da kullanılabilir:
        - **Dinamik etiket**: Aşağıdaki etiketlerden seçim yapın:
          - **Ad ekle**
          - **Gönderen adını ekleme**
          - **Gönderen e-postası ekleme**
          - **E-posta konusu ekleme**
          - **E-posta içeriği ekleme**
          - **Tarih ekle**
        - **Varsayılan olarak kullan**: Başlangıç olarak 5 kullanılabilir giriş sayfası şablonundan birini seçin. Düzenleme alanında metin ve düzeni değiştirebilirsiniz. Giriş sayfasını şablonun varsayılan metnine ve düzenine sıfırlamak için Varsayılana **sıfırla'ya tıklayın**.
        - **Eğitim bağlantısı**: Görüntülenen Eğitim **URL'sini** adla iletişim kutusunda, eğitim bağlantısı için bir bağlantı başlığı girin ve ardından bağlantıyı giriş  sayfasına eklemek için Onayla'ya tıklayın.
      - **Kod**: HTML kodunu doğrudan görüntüp değiştirebilirsiniz.

      Sayfanın ortasındaki Önizleme panelini **aç düğmesine tıklayarak** sonuçların önizlemesini görüntüleyebilirsiniz. Görüntülenen önizleme açılır penceresinde, her yükten nasıl göründüğünü görmek  için Yük seçin öğesini kullanabilirsiniz.

  - **Özel URL kullanın**: Görüntülenen Özel giriş sayfası **URL'sini girin kutusuna URL'yi** ekleyin. Sayfada başka seçenek yoktur.

Bitirdikten sonra, Sonraki'ne **tıklayın**.

## <a name="select-end-user-notification"></a>Son kullanıcı bildirimini seçme

Son **kullanıcı bildirimi seç sayfasında** , aşağıdaki bildirim seçeneklerinden birini belirleyin:

- **Bildirimleri teslim edin: Görüntülenen** uyarı **iletişim kutusunda** Devam'a tıklayın. Bu seçeneği kullanırsanız, Sonraki'ye tıklarsanız [Benzetim](#simulation-schedule) zamanlama sayfasına **olursanız**.

- **Microsoft varsayılan bildirimi (önerilir)**: Sayfada aşağıdaki ek ayarlar kullanılabilir:
  - **Varsayılan dili seçin**: Kullanılabilir değerler: **Çince (Basitleştirilmiş)**, Çince **(Geleneksel)**, **İngilizce****, Fransızca**, **Almanca**, **İtalyanca**, **Japonca**, **Kore dili****, Portekizce**, **Rusça**, **İspanyolca** ve Felemenkçe.
  - Varsayılan olarak, seçilmesi gereken tek bildirim Microsoft tarafından olumlu **bir bildirimdir**. Bildirim için aşağıdaki bilgiler kullanılabilir:
    - **Bildirimler** (ad): Değer **, Microsoft'un varsayılan olarak pozitif bildirim bildirimidir**.
    - **Dil**: Bildirim birden çok çeviri içeriyorsa, ilk iki dil doğrudan gösterilir. Kalan dilleri görmek için sayısal simgenin (örneğin, **+10) üzerine gelin**.
    - **Tür**: Değer Pozitif **pozitif bir gelecektir**.
    - **Teslim tercihleri**: Aşağıdaki değerlerden birini seçin:
      - **Teslim yapma**
      - **Kampanya sona erdikten sonra teslim**
      - **Kampanya sırasında teslim**
    - **Teslim Tarihi**: Değer **uygulanamaz**.
    - **Eylemler**: Görünüm simgesine tıklarsanız ![.](../../media/m365-cc-sc-view-icon.png) **Görüntüle** simgesi, **Bildirim sayfasını** gözden geçir aşağıdaki bilgilerle birlikte görüntülenir:
      - **Önizleme** sekmesi: Bildirim mesajını görüntüleyin. İletiyi farklı dillerde görüntülemek için Dil seçin **kutusunu** kullanın.
      - **Ayrıntılar** sekmesi: Bildirimle ilgili ayrıntıları görüntüleyin:
        - **Bildirim açıklaması**
        - **Kaynak**: Yerleşik bildirimler için değer **Genel'edir**. Özel bildirimler için değer **Kiracı'dır**.
        - **Bildirim türü**
        - **Değiştiren**
        - **Son değiştirme**

        İşlemi tamamladığınızda, **Kapat**'a tıklayın.

  Bu seçeneği kullanırsanız, Sonraki'ye tıklarsanız [Benzetim](#simulation-schedule) zamanlama sayfasına **olursanız**.

- **Özelleştirilmiş son kullanıcı** bildirimleri: Sonraki'ye tıklarsanız **, bir** sonraki bölümde açıklandığı gibi Pozitif  bildirim bildirimleri sayfasına olur ve burada mevcut bildirimlerden seçim veya yeni bildirimler oluşturabilirsiniz.

Bitirdikten sonra, Sonraki'ne **tıklayın**.

### <a name="positive-reinforcement-notification"></a>Olumlu olumlu bildirim

Pozitif **bildirim sayfası** yalnızca önceki sayfada Özelleştirilmiş son kullanıcı **bildirimleri'ne tıklayın** .

- **Teslim tercihleri**: Aşağıdaki değerlerden birini seçin:
  - **Teslim yapma**
  - **Kullanıcı kimlik avı ve kampanyanın sona erdikten sonra teslimi**
  - **Kullanıcı bir kimlik avı bildirdikten hemen sonra teslim edin**

- **Pozitif bir bildirim bildirimi seçin**: Mevcut bir bildirimi seçerek veya kullanmak üzere Pozitif bildirim bildirimi türünde **yeni bir bildirim** oluşturabilirsiniz:
  - Var olan bir bildirimi seçmek için bildirim adının yanındaki boş alana tıklayın. Bildirim adına tıklarsanız bildirim seçilir ve bir önizleme açılır sayfası görüntülenir. Bildirimin seçimini kaldırmak için bildirimin yanındaki onay kutusunu temizleyin.
  - Var olan bir bildirimi aramak için Ara simgesini ![kullanın.](../../media/m365-cc-sc-search-icon.png) **Adı** aramak için Arama kutusu.
  - Yeni bildirim oluşturmak için Yeni simge oluştur'a ![tıklayın.](../../media/m365-cc-sc-create-icon.png) **Yeni oluştur'a.**
  - Var olan bir özel bildirimi değiştirmek için, bildirimi seçin ve ardından Bildirim simgesini düzenle'ye ![tıklayın.](../../media/m365-cc-sc-edit-icon.png) **Bildirimi düzenle'yi seçin**.

#### <a name="create-new-notification-wizard"></a>Yeni bildirim sihirbazı oluşturma

Yeni simge oluştur'a ![tıkladıysanız.](../../media/m365-cc-sc-create-icon.png) **Olumlu bildirim** sayfasında **yeni bir bildirim oluşturma** sihirbazı açılır.

Oluşturma adımları, Son kullanıcı bildirimleri [oluşturma konusunda açıklananla aynıdır](attack-simulation-traning-end-user-notifications.md#create-end-user-notifications).

> [!NOTE]
> Ayrıntıları tanımla **sayfasında** , Bildirim türünü seçin için Pozitif **bildirim bildirimi değerini seçmeye** **emin olun**. Benzetim **bildirimi'yi seçmeyin**.

Bitirdikten sonra, Yeni oluşturduğunuz bildirimin pozitif bir bildirim bildirim seçin  listesinde göründüğü Pozitif bildirim sayfasına **dönersiniz**.

- Yeni bildirim oluşturmak için ![Yeni oluştur simgesi.](../../media/m365-cc-sc-create-icon.png).
- Bildirimi değiştirmek veya başka çeviriler eklemek için listeden bildirimi seçin ve ardından Bildirim simgesini düzenle'ye ![tıklayın.](../../media/m365-cc-sc-edit-icon.png) **Daha önce** açıklandığı gibi (çoğu değer zaten doldurulmuş olarak) bildirim sihirbazını başlatmak için bildirimi düzenleyin. Bildirimde desteklenen 12 dilin çevirileri zaten varsa, daha fazla çeviri ekzzzzsiniz.

Kullanmak istediğiniz bildirimi seçin ve ardından Sonraki'ye **tıklayın**.

## <a name="simulation-schedule"></a>Benzetim zamanlaması

Benzetim **zamanlama** sayfasında aşağıdaki değerlerden birini seçin:

- **Rastgele:** Yine de sonraki sayfada zamanlamayı seçmeniz gerekir, ancak benzetimler zamanlamayla birlikte rastgele başlatılamaz.
- **Düzeltildi**

Bitirdikten sonra, Sonraki'ne **tıklayın**.

## <a name="schedule-details"></a>Zamanlama ayrıntıları

Zamanlama ayrıntıları sayfasında ne **göreceğiniz**, önceki sayfada Rastgele mi yoksa Sabit  mi seçtiğinize  bağlıdır.

- **Rastgele:** Aşağıdaki ayarlar kullanılabilir:
  - **Benzetim** başlangıç bölümü: Aşağıdaki ayarı yapılandırma:
    - **Benzetimlerin başlamalarını istediğiniz tarihi seçin**
  - **Benzetimcoping** bölümü: Aşağıdaki ayarları yapılandırma:
    - **Benzetimlerin başlamasına izin verilen haftanın** günlerini seçin: Haftanın bir veya daha fazla günlerini seçin.
    - **Başlangıç ve bitiş tarihleri arasında başlat yalnızca** benzetim sayısı üst sayısını girin: 1 ile 10 arasında bir değer girin.
    - **Gönderme saatlerini rastgele ayarlama**: Gönderme saatlerini rastgele kullanmak için bu ayarı seçin.
  - **Benzetim** bitiş bölümü: Aşağıdaki ayarı yapılandırma:
    - **Benzetimlerin bitmelerini istediğiniz tarihi seçin**

- **Düzeltildi**: Aşağıdaki ayarlar kullanılabilir:
  - **Benzetim** başlangıç bölümü: Aşağıdaki ayarı yapılandırma:
    - **Benzetimlerin başlamalarını istediğiniz tarihi seçin**
  - **Benzetim yineleme** bölümü: Aşağıdaki ayarları yapılandırma:
    - **Benzetimlerin haftalık veya aylık olarak başlatılmasını istediğiniz zaman seçin**: Aşağıdaki değerlerden birini seçin:
      - **Haftalık**: Bu varsayılan değerdir.
      - **Aylık**
    - **Benzetimlerin hangi sıklıkta tekrarlır? istediğiniz** hafta olarak girin: 1 ile 99 hafta arasında bir değer girin.
    - **Benzetimlerin başlamalarını istediğiniz haftanın günlerini seçin**
  - **Benzetim** bitiş bölümü: Aşağıdaki değerlerden birini seçin:
    - **Benzetimlerin bitmelerini istediğiniz tarihi seçin**
    - **Benzetimlerin bitmeden önce çalıştıracakları** benzetim sayısını girin: 1 ile 10 arasında bir değer girin.

Bitirdikten sonra, Sonraki'ne **tıklayın**.

## <a name="launch-details"></a>Başlatma ayrıntıları

Ayrıntıları **başlat sayfasında** , otomasyon için aşağıdaki ek ayarları yapılandırabilirsiniz:

- **Bir otomasyon içindeki benzetimler genelinde benzersiz yüklemeler kullanın**: Varsayılan olarak, bu ayar seçili değildir.
- **Hedef yinelemeli yinelemeli**: Varsayılan olarak, bu ayar seçili değildir. Bu ayarı ayarlarsanız, görüntülenen aşağıdaki ayarı yapılandırabilirsiniz:
  - **Bu otomasyon içinde bir kullanıcıya en fazla** kaç kez hedeflebileceklerini girin: 1 ile 10 arasında bir değer girin.
- **Bir web uygulamasından kullanıcının geçerli saat dilimi ayarına göre benzetim e-Outlook** gönderin: Varsayılan olarak, bu ayar seçili değildir.
- **Drive-by technique interstitial data toplanmış** sayfasını görüntüleme: Bu ayar yalnızca Sosyal mühendislik tekniklerini seçin sayfasında **Sürücüye göre URL'yi** **[seçtiyseniz](#select-one-or-more-social-engineering-techniques)** kullanılabilir. Varsayılan olarak, ayar açıktır (![Simgeyi açık olarak değiştir).](../../media/scc-toggle-on.png)

## <a name="review-simulation-automation"></a>Benzetim otomasyonunu gözden geçirme

Benzetim **otomasyonunu gözden** geçir sayfasında, benzetim otomasyonu ayrıntılarınızı gözden geçirebilirsiniz.

Bölümün içindeki **ayarları değiştirmek** için her bölümde Düzenle'yi seçebilirsiniz. Geri'ye **tıklar** veya sihirbazda belirli bir sayfayı seçersiniz.

Bitirdikten sonra Gönder'e **tıklayın**.
