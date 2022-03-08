---
title: Saldırı benzetimi eğitimi ile kimlik avı saldırılarını benzetimini uygulama
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
description: Yöneticiler, Plan 2'ye yönelik Microsoft Defender'daki Saldırı benzetimi eğitimini kullanarak kimlik avı saldırılarının benzetimini yapmayı ve kullanıcılarını kimlik avı engellemesi konusunda Office 365 öğrenebilirsiniz.
ms.technology: mdo
ms.openlocfilehash: 31c8fd7b0369e5af522cd79b9bee7c5ee8460cc5
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63329649"
---
# <a name="simulate-a-phishing-attack-with-attack-simulation-training-in-defender-for-office-365"></a>Office 365 için Defender'daki Saldırı benzetimi eğitimi ile kimlik avı saldırılarının benzetimini Office 365

 [Office 365 için Microsoft Defender plan 2 için geçerlidir](defender-for-office-365.md)

2. Plan 2 veya Office 365 Microsoft Defender'daki saldırı benzetim eğitimi, Microsoft 365 E5 siber benzetimler çalıştırmanıza olanak sağlar. Bu benzetimler güvenlik ilkelerinizi ve uygulamalarınızı test edin, ayrıca çalışanlarınızı saldırılara karşı duyarlılıklarını artırmaya ve azaltmaya eğitin. Bu makale, Saldırı benzetimi eğitimini kullanarak sanal bir kimlik avı saldırısı oluşturma konusunda size yol yardımcı oluyor.

Saldırı benzetimi eğitimi hakkında bilgi almak için bkz. [Saldırı benzetimi eğitimlerini kullanmaya başlama](attack-simulation-training-get-started.md).

Sanal bir kimlik avı saldırısı başlatmak için aşağıdaki adımları uygulayın:

1. aşağıdaki Microsoft 365 Defender portalında, E-posta <https://security.microsoft.com>gönder ve **işbirliği &** \> **Saldırı benzetim eğitimi** \> **Benzetimler sekmesine** gidin.

   Doğrudan Benzetimler **sekmesine gitmek** için kullanın <https://security.microsoft.com/attacksimulator?viewid=simulations>.

2. **Benzetimler sekmesinde** Benzetim simgesi ![başlat'ı seçin.](../../media/m365-cc-sc-create-icon.png) **Benzetim başlat.**

   ![Microsoft 365 Defender portalında, Saldırı benzetim eğitimi'nin Benzetimler sekmesinde bir benzetim düğmesi başlatabilirsiniz.](../../media/attack-sim-training-simulations-launch.png)

3. Benzetim oluşturma sihirbazı açılır. Bu makalenin kalan kalanında, sayfaları ve bunların içerdiği ayarlar açıklanmıştır.

> [!NOTE]
> Benzetim oluşturma sihirbazının herhangi bir noktasında, ilerlemenizi kaydetmek  ve benzetimi daha sonra yapılandırmaya devam etmek için Kaydet ve kapat'a tıklarsınız. Tamamlanmamış benzetimlerin **Benzetimler** **sekmesinde** Durum değeri **Taslağı** vardır. Benzetimi seçerek ve benzetim simgesini düzenle'ye tıklayarak, kalan yerden ![devamabilirsiniz.](../../media/m365-cc-sc-edit-icon.png) **Benzetimi** düzenleyin.

## <a name="select-a-social-engineering-technique"></a>Bir sosyal mühendislik tekniği seçin

Select **technique sayfasında** , [MITRE ATT&CK Framework'den&seçin®](https://attack.mitre.org/techniques/enterprise/). Farklı teknikler için farklı yük kullanılabilir. Aşağıdaki sosyal mühendislik tekniklerini kullanabilirsiniz:

- **Kimlik bilgileri toplama**: Kullanıcıları bir kullanıcı adı ve parola göndermek üzere giriş kutuları olan iyi bilinen bir web sitesine götürerek kimlik bilgilerini toplamaya çalışır.
- **Kötü amaçlı yazılım** eki: İletiye kötü amaçlı bir ek ekler. Kullanıcı eki açtığında, rastgele kod çalıştırarak saldırgan hedef cihazı tehlikeye atabilir.
- **Ekin bağlantısı**: Karma için bir kimlik bilgisi türü. Bir saldırgan e-posta eke bir URL ekler. Ekin içindeki URL, kimlik bilgisi toplama yöntemiyle aynı teknikten sonra gelir.
- **Kötü amaçlı yazılıma** bağlantı: İyi bilinen bir dosya paylaşım hizmetlerinden barındırılan bir dosyadan bazı rastgele kodlar çalıştırır. Kullanıcıya gönderilen ileti, bu kötü amaçlı dosyanın bağlantısını içerir. Dosyanın açılması, saldırganin hedef cihazından ödün vermelerine yardımcı olur.
- **Sürücüye Göre URL**: İletide yer alan kötü amaçlı URL, kullanıcıya, kullanıcının cihazında kodu sessiz olarak çalıştıran ve/veya yüken tanıdık görünümlü bir web sitesine alır.

Açıklamada Ayrıntıları **görüntüle bağlantısına** tıklarsanız, tekniğin ve teknikten elde edilen benzetim adımlarını açıklayan bir ayrıntılar açılır.

![Seçme tekniği sayfasında kimlik bilgisi depolama tekniği için ayrıntılar uç sayfası.](../../media/attack-sim-training-simulations-select-technique-sim-steps.png)

Bitirdikten sonra, Sonraki'ne **tıklayın**.

## <a name="name-and-describe-the-simulation"></a>Benzetimi adla ve açıkla

Ad **benzetim sayfasında** aşağıdaki ayarları yapılandırabilirsiniz:

- **Ad**: Benzetim için benzersiz, açıklayıcı bir ad girin.
- **Açıklama**: Benzetim için isteğe bağlı olarak ayrıntılı bir açıklama girin.

Bitirdikten sonra, Sonraki'ne **tıklayın**.

## <a name="select-a-payload"></a>Yük seçin

Yük **seçin sayfasında** , listeden mevcut bir yük seçmeniz veya yeni bir yük oluşturmanız gerekir.

Aşağıdaki ayrıntılar, seçime yardımcı olmak için yük listesinde görüntülenir:

- **Ad**
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
  - **Genel** (yerleşik)
  - **Kiracı** (özel)
  - **Hepsi**
- **Dil**: Kullanılabilir değerler: Çince **(Basitleştirilmiş)**, Çince **(Geleneksel)**, **İngilizce**, **Fransızca****, Almanca**, **İtalyanca**, **Japonca**, **Korece**, **Portekizce****, Rusça**, **İspanyolca** ve Felemenkçe.
- **Etiket ekle**
- **Temaya** göre filtreleme: Kullanılabilir **değerler: Hesap** **etkinleştirme, Hesap** **doğrulama, Faturalama****,** Postayı **temizleme, Alınan** belge, **Gider**, **Faks****, Finans** raporu, **Gelen iletiler**, **Fatura****, Öğeler** **alındı, Oturum** açma uyarısı, **Alınan posta**, **Parola**, **Ödeme**, **Bordro**, **Kişiselleştirilmiş teklif****, Karantina**, **Uzaktan çalışma**, **İletiyi gözden geçir****, Güvenlik** **güncelleştirmesi,** Hizmet askıya alındı, İmza **gerekli**, **Posta kutusu depolamasını yükseltme Posta** kutusunu, **Sesli** mesajı ve Diğer'i **doğrulayın**.
- Markaya göre filtrele **: Kullanılabilir** değerler: **American Express**, **Capital One**, **DHL**, **DocuSign**, **Dropbox**, **Facebook**, **First American**, **Microsoft**, **Netflix**, **Scotiabank**, **SendGrid**, **Title**, **Tgrid**, **Wells Fargo**, **Syrinx Cloud** ve **Other**.
- **Sektöre** göre filtre uygulama: Kullanılabilir **değerler: Bankacılık****, İş** **hizmetleri, Tüketici** hizmetleri, **Eğitim**, **Enerji**, **Inşaat**, **Danışmanlık**, **Finansal** hizmetler, **Kamu****, Hastane**, **Sigorta**, **Yasal**, **Courier** hizmetleri, **IT**, **Sağlık**, **Üretim**, **Perakende**, **Telecom**, **Emlak**, ve **Diğer'i de.**
- **Geçerli olay**: Kullanılabilir değerler Evet **veya** **Hayır'dır**.
- **Neden**: Kullanılabilir değerler Evet **veya** **Hayır'dır**.

Filtreleri yapılandırmayı bitirdikten sonra, Filtreleri Uygula, İptal **et** **veya Temizle'yi** **tıklatın**.

![Geçiş portalında Saldırı benzetimi eğitimi'nin yük Microsoft 365 Defender seçin.](../../media/attack-sim-training-simulations-select-payload.png)

Listeden bir yük seçersiniz, yükle ilgili ayrıntılar bir çıkışta gösterilir:

- Genel **Bakış** sekmesi, yük hakkında bir örnek ve diğer ayrıntıları içerir.
- **Benzetimler başlatıldı** sekmesi Benzetim adı, **Tıklama** oranı, Güvenliği **ihlal** **edildi oranı ve** **Eylem'i içerir**.

![Geçiş portalında Saldırı benzetimi eğitimi altında ayrıntıları Microsoft 365 Defender.](../../media/attack-sim-training-simulations-select-payload-details.png)

Adı tıklatarak listeden bir yük seçin, bir ![Test yüklemesi gönder simgesi.](../../media/m365-cc-sc-create-icon.png) **Yükleme e-postanın** bir kopyasını inceleme için kendinize (şu anda oturum açmış olan kullanıcı) gönderebilirsiniz.

Kendi yüklerinizi oluşturmak için Yükleme simgesi ![oluştur'a tıklayın.](../../media/m365-cc-sc-create-icon.png) **Yük oluşturun**. Daha fazla bilgi için Saldırı [benzetimi eğitimi için özel yüklemeler oluşturma'ya bakın](attack-simulation-training-payloads.md).

Bitirdikten sonra, Sonraki'ne **tıklayın**.

## <a name="target-users"></a>Hedef kullanıcılar

Hedef **kullanıcılar sayfasında** benzetimi alacak olan kullanıcıları seçin. Aşağıdaki ayarlardan birini yapılandırma:

- **Organizasyon dahil tüm kullanıcıları dahil:** Etkilenen kullanıcılar 10 listelerinde gösterir. Listede kaydırmak **için kullanıcı** **listesinin** hemen altındaki Sonraki ve Önceki düğmelerini kullanabilirsiniz. Arama simgesini de ![kullanabilirsiniz.](../../media/m365-cc-sc-search-icon.png) **Etkilenen** kullanıcıları bulmak için sayfada Ara simgesi.

- **Yalnızca belirli kullanıcıları ve grupları dahil** etmek için: Aşağıdaki seçeneklerden birini belirleyin:
  - ![Kullanıcı ekle simgesi.](../../media/m365-cc-sc-create-icon.png) **Kullanıcı ekleme**: Görüntülenen **Kullanıcı ekle** açılır yapısında, kullanıcıları ve grupları aşağıdaki ölçütlere göre bulabilirsiniz:

    - **Kullanıcıları veya grupları arama**: Kutusuna, kullanıcının veya grubun Ad veya E-posta  adresinin  bir kısmını yazarak Enter tuşuna basabilirsiniz. Sonuçların bir veya hepsini seçin. Bitirdikten sonra X kullanıcı **ekle'ye tıklayın**.

      > [!NOTE]
      > Kullanıcıları **kategorilere göre** filtrele seçeneklerine dönmek  için Filtre ekle düğmesine tıkıldığında, arama sonuçlarında seçtiğiniz tüm kullanıcılar veya gruplar temiz olur.

    - **Kullanıcıları kategorilere göre filtreleme**: Yok, bazıları veya tüm aşağıdaki seçeneklerden birini belirleyin:

      - **Önerilen kullanıcı grupları**: Aşağıdaki değerlerden birini seçin:
        - **Tüm önerilen kullanıcı grupları**
        - **Son üç ay içinde kullanıcılar bir benzetim tarafından hedef kitleye ulaşmdı**
        - **Yinelemelileri yineleme**

      - **Kullanıcı etiketleri**: Kullanıcı etiketleri belirli kullanıcı grupları için tanımlayıcılardır (örneğin, Öncelik hesapları). Daha fazla bilgi için bkz[. Windows için Microsoft Defender'da Office 365](user-tags.md).

          Aşağıdaki seçenekleri kullanın:

        - **Ara**: Kullanıcı ![etiketlerine göre ara simgesinde.](../../media/m365-cc-sc-search-icon.png) **Kullanıcı etiketlerine göre** arama yaptıysanız, kullanıcı etiketinin bir kısmını yazarak Enter tuşuna basabilirsiniz. Sonuçların bir veya hepsini seçin.
        - Tüm **kullanıcı etiketleri'yi seçin**
        - Var olan kullanıcı etiketlerini seçin.

      - **Bölüm**: Aşağıdaki seçenekleri kullanın:
        - **Ara**: Departmana ![göre ara simgesinde.](../../media/m365-cc-sc-search-icon.png) **Departmana göre arama** bölümünde Bölüm değerini yazın ve Enter tuşuna basın. Sonuçların bir veya hepsini seçin.
        - Tüm **Departmanları Seçme**
        - Mevcut Departman değerlerini seçin.

      - **Başlık**: Aşağıdaki seçenekleri kullanın:
        - **Arama**: Başa ![Göre Ara simgesinde.](../../media/m365-cc-sc-search-icon.png) **Başt'a** göre arama bölümünde Başlık değerinin bir kısmını yazın ve Enter tuşuna basın. Sonuçların bir veya hepsini seçin.
        - Tüm **Başlığı Seç**
        - Mevcut Başlık değerlerini seçin.

      ![Hedef kullanıcılar sayfasındaki Saldırı benzetimi eğitimi sayfasındaki kullanıcı filtrelemesi Microsoft 365 Defender.](../../media/attack-sim-training-simulations-target-users-filter-by-category.png)

      Ölçütlerinizi tanımdikten sonra, etkilenen kullanıcılar görüntülenen Kullanıcı listesi bölümünde gösterilir  ve burada bulunan alıcıların bir bölümünü veya hepsini seçebilirsiniz.

      Bitirdikten sonra Uygula **(x)'e tıklayın** ve sonra da X kullanıcı **ekle'ye tıklayın**.

  Ana Hedef kullanıcılar **sayfasına** dönüp Arama simgesini kullanabilirsiniz ![.](../../media/m365-cc-sc-search-icon.png) **Etkilenen** kullanıcıları bulmak için arama kutusu. Ayrıca, Kullanıcıları sil simgesine ![de tıkabilirsiniz.](../../media/m365-cc-sc-search-icon.png) **Belirli** kullanıcıları kaldırmak için silin.

- ![İçeri Aktar simgesi.](../../media/m365-cc-sc-create-icon.png) **İçeri** Aktar: Açılan iletişim kutusunda, satır başına bir e-posta adresi içeren bir CSV dosyası belirtin.

  CSV dosyasını buktan sonra, kullanıcı listesi içeri aktarılır ve Hedefli kullanıcılar **sayfasında** gösterilir. Arama simgesini ![kullanabilirsiniz.](../../media/m365-cc-sc-search-icon.png) **Etkilenen** kullanıcıları bulmak için arama kutusu. Ayrıca, Hedefli kullanıcıları ![sil simgesine de tıkabilirsiniz.](../../media/m365-cc-sc-delete-icon.png) **Belirli** kullanıcıları kaldırmak için silin.

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

Gösterilen bir eğitimi kullanmak istemiyorsanız, Eğitim simgesini sil'e ![tıklayın.](../../media/m365-cc-sc-delete-icon.png) **Sil'i seçin**.

![Geçiş portalında Saldırı benzetimi eğitimi'nin Microsoft 365 Defender sayfası.](../../media/attack-sim-training-training-assignment.png)

Bitirdikten sonra, Sonraki'ne **tıklayın**.

### <a name="landing-page"></a>Giriş sayfası

Giriş **sayfası sayfasında** , yükleme benzetimde bir yük açılırsa kullanıcının ziyarette olduğu web sayfasını yapılandırabilirsiniz.

Microsoft tarafından el ile yapılan giriş sayfaları 12 dilde kullanılabilir: Çince (Basitleştirilmiş), Çince (Geleneksel), İngilizce, Fransızca, Almanca, İtalyanca, Japonca, Kore dili, Portekizce, Rusça, İspanyolca ve Felemenkçe.

- **Giriş sayfası tercihini seçin**: Kullanılabilir değerler:
  - **Microsoft varsayılan giriş sayfasını kullanma**: Bu, yapılandırmayla ilgili aşağıdaki seçeneklerin yer alan varsayılan değerdir:
    - **Giriş sayfası düzenini seçin**: Kullanılabilir şablonlardan birini seçin.
    - **Logo ekleme**: Bir dosya **,** .jpeg veya .png bulmak ve seçmek için Gözat'.gif tıklayın. Logoyu kaldırmak için Kaldır'a **tıklayın**.
    - **E-postaya yük göstergeleri ekleme**: Seçme tekniği sayfasında önceden Kötü amaçlı yazılım eki veya  Kötü amaçlı yazılıma bağlantı yükle'yi seçtiyseniz **bu** [ayar](#select-a-social-engineering-technique) kullanılamaz.

      Kullanıcıların **kimlik avı iletilerini tanımlamayı öğrenmelerine yardımcı olmak için** E-postaya yük göstergeleri ekle'yi seçin.

    Sayfanın en altındaki Önizleme panelini **aç düğmesine tıklayarak** sonuçların önizlemesini görüntüleyebilirsiniz.

  - **Özel URL kullanın: Daha** önce Teknik seçin sayfasında Kötü amaçlı yazılım eki veya  Kötü amaçlı yazılıma **bağlantı ekle'yi** seçtiyseniz bu [ayar](#select-a-social-engineering-technique) kullanılamaz.

    Özel BIR **URL kullan'ı seçiyorsanız**, görüntülenen Özel giriş sayfası **URL'sini girin kutusuna URL'yi** eklemeniz gerekir. Sayfada başka seçenek yoktur.

  - **Kendi giriş sayfanızı oluşturma**: Bu değeri yapılandırmak için aşağıdaki ilişkili seçenekler vardır:
    - **E-postaya yük göstergeleri ekleme**: Seçme tekniği sayfasında önceden Kötü amaçlı yazılım eki veya  Kötü amaçlı yazılıma bağlantı yükle'yi seçtiyseniz **bu** [ayar](#select-a-social-engineering-technique) kullanılamaz.

      Kullanıcıların **kimlik avı iletilerini tanımlamayı öğrenmelerine yardımcı olmak için** E-postaya yük göstergeleri ekle'yi seçin.

    - Sayfa içeriği: İki sekme kullanılabilir:
      - **Metin**: Giriş sayfanız oluşturmak için zengin bir metin düzenleyicisi kullanılabilir. Normal yazı tipi ve biçimlendirme ayarlarına ek olarak, aşağıdaki ayarlar da kullanılabilir:
        - **Dinamik etiket**: Aşağıdaki etiketlerden seçim yapın:
          - **Kullanıcı Adı**
          - **E-posta gönderenin adı**
          - **Gönderen e-posta adresi**
          - **E-posta konusu**
          - **E-posta içeriği**
        - **Varsayılan olarak kullan**: Başlamak için kullanılabilir bir şablon seçin. Düzenleme alanında metin ve düzeni değiştirebilirsiniz. Giriş sayfasını şablonun varsayılan metnine ve düzenine sıfırlamak için Varsayılana **sıfırla'ya tıklayın**.
    - **Kod**: HTML kodunu doğrudan görüntüp değiştirebilirsiniz.

    Sayfanın ortasındaki Önizleme panelini **aç düğmesine tıklayarak** sonuçların önizlemesini görüntüleyebilirsiniz.

Bitirdikten sonra, Sonraki'ne **tıklayın**.

> [!NOTE]
> Bazı ticari markalar, logolar, simgeler, insignias ve diğer kaynak tanımlayıcıları yerel, eyalet ve federal yasalara göre daha yüksek koruma sağlar. Bu gibi göstergelerin yetkisiz kullanımı, kullanıcılara cezai para cezaları dahil olmak üzere penceler konur. Kapsamlı bir liste de dahil değil, bu listede Başkan Yardımcısı, Başkan Yardımcısı ve Tayyali üyeleri, CIA, CIA, Social Security, Medicare ve Medicaid, ABD İç Gelir Hizmeti ve Olimpiyatlar yer alıyor. Bu ticari marka kategorilerinin ötesinde, üçüncü taraf ticari markaların yapısal bir miktarda risk taşıyan kullanım ve değiştirilmesi. Yüklemede kendi ticari markalarınızı ve logolarınızı kullanmak, özellikle de kuruluş izinli olduğu bir yüklemede daha az riskli olabilir. Yük oluşturma veya yapılandırmada kullanımın ne olduğu veya uygun olmadığınız hakkında başka sorularınız varsa, yasal danışmanlarınıza danışmanız ile görüşmeniz gerekir.

## <a name="select-end-user-notification"></a>Son kullanıcı bildirimini seçme

Son **kullanıcı bildirimi seç sayfasında** , aşağıdaki bildirim seçeneklerinden birini belirleyin:

- **Bildirimleri teslim edin: Görüntülenen** uyarı **iletişim kutusunda** Devam'a tıklayın. Bu seçeneği tercih ettiyseniz, Sonraki'ye tıklarsanız [Ayrıntıları](#launch-details) başlat sayfasına **olursanız**.

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

        Bitirdikten sonra Kapat'a **tıklayın**.

  Bu seçeneği tercih ettiyseniz, Sonraki'ye tıklarsanız [Ayrıntıları](#launch-details) başlat sayfasına **olursanız**.

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

## <a name="launch-details"></a>Başlatma ayrıntıları

Başlatma **ayrıntıları sayfasında** benzetimi ne zaman başlatmanız ve benzetimi ne zaman bitireceklerini seçersiniz. Belirttiğiniz bitiş sonunda bu benzetimle etkileşimi yakalamayı durdururuz.

Aşağıdaki ayarlar kullanılabilir:

- Aşağıdaki değerlerden birini seçin:
  - **Benzetimi tamamlayacağız**
  - **Bu benzetimi daha sonra başlatacağız şekilde planla**: Bu değer, yapılandırmak için aşağıdaki ilişkili seçeneklere sahiptir:
    - **Başlangıç tarihini seçin**
    - **Başlatma saati seçin**
- **Benzetimi sona erdirecek gün sayısını yapılandırma**: Varsayılan değer 2'dir.
- **Bölgeyi biliyorsanız saat dilimi teslimini** etkinleştirin: Çalışanlarınızı bölgelerine göre çalışma saatleri içinde sanal saldırı iletileri teslim edin.
- **Drive-by technique interstitial data toplanmış** sayfasını görüntüleme: Sürücü-BU URL tekniği saldırılarına yönelik yer paylaşımını gösterebilirsiniz. Yer paylaşımını gizlemek ve doğrudan giriş sayfasına gitmek için, bu seçeneğin de-işaretleyin.

Bitirdikten sonra, Sonraki'ne **tıklayın**.

## <a name="review-simulation"></a>Benzetimi gözden geçirme

Benzetimi **gözden geçir** sayfasında, benzetiminizin ayrıntılarını gözden geçirebilirsiniz.

Test gönder ![simgesine tıklayın.](../../media/m365-cc-sc-send-icon.png) **Yüklü e-postanın** bir kopyasını inceleme için kendinize (şu anda oturum açmış olan kullanıcı) göndermek için Test gönder düğmesi.

Bölümün içindeki **ayarları değiştirmek** için her bölümde Düzenle'yi seçebilirsiniz. Geri'ye **tıklar** veya sihirbazda belirli bir sayfayı seçersiniz.

Bitirdikten sonra Gönder'e **tıklayın**.

![Microsoft 365 Defender portalında Saldırı benzetimi eğitimi'nin benzetim Microsoft 365 Defender gözden geçirebilirsiniz.](../../media/attack-sim-training-simulations-review-simulation.png)
