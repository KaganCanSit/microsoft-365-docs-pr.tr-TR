---
title: Saldırı simülasyonu eğitimi için simülasyon otomasyonları
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
description: Yöneticiler, Office 365 için Microsoft Defender Plan 2'de belirtilen koşullar karşılandığında başlatılan belirli teknikleri ve yükleri içeren otomatik simülasyonlar oluşturmayı öğrenebilir.
ms.technology: mdo
ms.openlocfilehash: 1efc6faaae0040e37aafac4faa0a10228d76e766
ms.sourcegitcommit: 03543c27c33427ac7f11af4c04fff35a181a2524
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/02/2022
ms.locfileid: "66609424"
---
# <a name="simulation-automations-for-attack-simulation-training"></a>Saldırı simülasyonu eğitimi için simülasyon otomasyonları

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

[Office 365 için Microsoft Defender plan 2](defender-for-office-365.md) **için geçerlidir**

Saldırı simülasyonu eğitimi hakkında başlangıç bilgileri için bkz. [Saldırı simülasyonu eğitimini kullanmaya başlama](attack-simulation-training-get-started.md).

Simülasyon otomasyonu oluşturmak için aşağıdaki adımları uygulayın:

1. konumundaki Microsoft 365 Defender portalında<https://security.microsoft.com/>**, E-posta & işbirliği** \> **Saldırı simülasyonu eğitimi** \> **Otomasyonları** sekmesi **Simülasyon otomasyonları'na**\> gidin.

   Doğrudan **Benzetim otomasyonları'nı** seçebileceğiniz **Otomasyonlar** sekmesine gitmek için kullanın <https://security.microsoft.com/attacksimulator?viewid=automations>.

2. **Simülasyon otomasyonları'nda** Otomasyon oluştur simgesi'ne tıklayın![.](../../media/m365-cc-sc-create-icon.png) **Otomasyon oluşturma**.

   :::image type="content" source="../../media/attack-sim-training-sim-automations-create.png" alt-text="Microsoft 365 Defender portalındaki Saldırı benzetimi eğitimi'ndeki Simülasyon otomasyonları sekmesindeki Simülasyon oluştur düğmesi" lightbox="../../media/attack-sim-training-sim-automations-create.png":::

3. Oluşturma sihirbazı açılır. Bu makalenin geri kalanında sayfalar ve içerdikleri ayarlar açıklanmaktadır.

> [!NOTE]
> Simülasyon oluşturma sihirbazı sırasında herhangi bir noktada Kaydet **ve kapat'a** tıklayarak ilerlemenizi kaydedebilir ve simülasyonu daha sonra yapılandırmaya devam edebilirsiniz. Tamamlanmamış simülasyon, **Simülasyonlar** sekmesinde **Taslak Durum** değerine sahiptir. Simülasyonu seçip Simülasyonu düzenle simgesine tıklayarak ![kaldığınız yerden devam edebilirsiniz.](../../media/m365-cc-sc-edit-icon.png) **Simülasyonu düzenleyin** .## Benzetimi adlandırın ve açıklayın.

## <a name="name-and-describe-the-simulation-automation"></a>Simülasyon otomasyonunu adlandırma ve açıklama

**Otomasyon adı** sayfasında aşağıdaki ayarları yapılandırın:

- **Ad**: Simülasyon için benzersiz, açıklayıcı bir ad girin.
- **Açıklama**: Simülasyon için isteğe bağlı ayrıntılı bir açıklama girin.

İşiniz bittiğinde **İleri'ye** tıklayın.

## <a name="select-one-or-more-social-engineering-techniques"></a>Bir veya daha fazla sosyal mühendislik tekniği seçme

**Sosyal mühendislik tekniklerini seçin** sayfasında, [MITRE ATT&CK® çerçevesinin](https://attack.mitre.org/techniques/enterprise/) seçilmiş olduğu kullanılabilir sosyal mühendislik tekniklerinden birini veya daha fazlasını seçin. Farklı teknikler için farklı yükler kullanılabilir. Aşağıdaki sosyal mühendislik teknikleri mevcuttur:

- **Kimlik bilgisi toplama**: Kullanıcı adı ve parola göndermek için kullanıcıları giriş kutularıyla iyi bilinen bir web sitesine götürerek kimlik bilgilerini toplamaya çalışır.
- **Kötü amaçlı yazılım eki**: İletiye kötü amaçlı bir ek ekler. Kullanıcı eki açtığında, saldırganın hedefin cihazını tehlikeye atılmasına yardımcı olacak rastgele kod çalıştırılır.
- **Ekteki bağlantı**: Kimlik bilgisi toplama karma türü. Saldırgan bir e-posta ekine URL ekler. Ek içindeki URL, kimlik bilgisi toplama ile aynı tekniği izler.
- **Kötü amaçlı yazılım bağlantısı**: İyi bilinen bir dosya paylaşım hizmetinde barındırılan bir dosyadan rastgele kod çalıştırır. Kullanıcıya gönderilen ileti bu kötü amaçlı dosyanın bağlantısını içerir. Dosyayı açın ve saldırganın hedefin cihazını tehlikeye atılmasına yardımcı olun.
- **Sürücü URL'si**: İletideki kötü amaçlı URL, kullanıcıyı sessizce çalışan ve/veya kullanıcının cihazına kod yükleyen tanıdık görünen bir web sitesine götürür.

Açıklamadaki **Ayrıntıları görüntüle** bağlantısına tıklarsanız, tekniği ve teknikten kaynaklanan simülasyon adımlarını açıklayan bir ayrıntı açılır öğesi açılır.

:::image type="content" source="../../media/attack-sim-training-simulations-select-technique-sim-steps.png" alt-text="Sosyal mühendislik tekniklerini seçin sayfasındaki Kimlik bilgisi toplama tekniği için Ayrıntılar açılır öğesi" lightbox="../../media/attack-sim-training-simulations-select-technique-sim-steps.png":::

İşiniz bittiğinde **İleri'ye** tıklayın.

## <a name="select-a-payload-and-login-page"></a>Bir yük ve oturum açma sayfası seçin

**Yükü ve oturum açma bilgilerini seçin** sayfasında, listeden mevcut bir yükü seçmeniz veya yeni bir yük oluşturmanız gerekir.

Ayrıca yükte kullanılan oturum açma sayfasını görüntüleyebilir, kullanılacak farklı bir oturum açma sayfası seçebilir veya kullanmak üzere yeni bir oturum açma sayfası oluşturabilirsiniz.

### <a name="payload"></a>Yükü

**Yükleri seçin** sayfasında aşağıdaki seçeneklerden birini belirleyin:

- **El ile**
- **Rastgele hale**

**Rastgele Seç'i** seçerseniz, bu sayfada yapılandırabileceğiniz bir şey yoktur, bu nedenle devam etmek için **İleri'ye** tıklayın.

**El ile seç'i** seçerseniz, listeden bir veya daha fazla yük seçmeniz gerekir. Her yük için aşağıdaki ayrıntılar gösterilir:

- **Yük adı**
- **Teknik**: Önceki sayfada seçtiğiniz teknik başına en az bir yük seçmeniz gerekir.
- **Dil**: Kullanılabilir değerler şunlardır: **İngilizce**, **İspanyolca**, **Almanca**, **Japonca**, **Fransızca**, **Portekizce**, **Felemenkçe**, **İtalyanca**, **İsveççe**, **Çince (Basitleştirilmiş)**, **Norveççe Bokmål**, **Lehçe**, **Rusça**, **Fince**, **Korece**, **Türkçe**, **Macarca**, **İbranice**, **Tayca**, **Arapça**, **Vietnamca**, **Slovakça**, **Yunanca**, **Endonezya dili**, **Rumence**, **Slovence**, **Hırvat**, **Katalanca** veya **Diğer**.
- **Tıklama oranı**: Bu yüke kaç kişinin tıklamış olduğu.
- **Tahmin edilen risk oranı**: Microsoft 365 genelinde yükün geçmiş verileri, bu yük tarafından tehlikeye atılacak kişilerin yüzdesini tahmin eder.
- **Başlatılan simülasyonlar** , bu yükün diğer simülasyonlarda kaç kez kullanıldığını sayar.

![Ara simgesinde.](../../media/m365-cc-sc-search-icon.png) **Arama** kutusuna yük adının bir kısmını yazabilir ve sonuçları filtrelemek için Enter tuşuna basabilirsiniz.

**Filtre'ye** tıklarsanız aşağıdaki filtreler kullanılabilir:

- **Karmaşıklık**: Yükteki olası bir saldırıyı (yazım hataları, aciliyet vb.) gösteren gösterge sayısına göre hesaplanır. Daha fazla göstergenin saldırı olarak tanımlanması daha kolaydır ve daha düşük karmaşıklığı gösterir. Kullanılabilir değerler şunlardır:

  - **Yüksek**
  - **Orta**
  - **Düşük**

- **Dil**

- **Etiket ekleme**

- **Temaya göre filtrele**: Hesap **etkinleştirme**, **Hesap doğrulama**, **Faturalama**, **Posta temizleme**, **Alınan belge**, **Gider**, **Faks**, **Finans raporu**, **Gelen iletiler**, **Fatura**, **Alınan Öğeler**, **Oturum açma uyarısı**, **Alınan posta**, **Parola**, **Ödeme**, **Bordro**, **Kişiselleştirilmiş teklif**, **Karantina**, **Uzaktan çalışma**, **İletiyi gözden geçirme**, **Güvenlik güncelleştirmesi**, **Hizmet askıya alındı**, **İmza gerekiyor**, **Posta kutusu depolama alanını yükselt Posta kutusunu**, **Sesli mesajı** ve **Diğer'i** doğrulayın.

- **Markaya göre filtrele**: Kullanılabilir değerler şunlardır: **American Express**, **Capital One**, **DHL**, **DocuSign**, **Dropbox**, **Facebook**, **First American**, **Microsoft**, **Netflix**, **Scotiabank**, **SendGrid**, **Stewart Title**, **Tesco**, **Wells Fargo**, **Syrinx Cloud** ve **Diğer**.

- **Sektöre göre filtrele**: **Bankacılık**, **İş hizmetleri**, **Tüketici hizmetleri**, **Eğitim**, **Enerji**, **İnşaat**, **Danışmanlık**, **Finansal hizmetler**, **Kamu**, **Konaklama**, **Sigorta**, **Yasal**, **Kurye hizmetleri**, **BT**, **Sağlık**, **İmalat**, **Perakende**, **Telekom**, **Emlak**, ve **Diğer**.

- **Geçerli olay**: Kullanılabilir değerler **Evet** veya **Hayır'dır**.

- **Tartışmalı**: Kullanılabilir değerler **Evet** veya **Hayır'dır**.

Filtreleri yapılandırmayı bitirdiğinizde **Uygula**, **İptal veya** **Filtreleri temizle'ye** tıklayın.

Listeden onay kutusunun dışındaki herhangi bir yere tıklayarak bir yük seçerseniz, yükle ilgili ayrıntılar açılır pencerede gösterilir:

- **Yük** sekmesi bir örnek ve yükle ilgili diğer ayrıntıları içerir.
- **Oturum açma sayfası** sekmesi sonraki bölümde açıklanmıştır.
- **Başlatılan Simülasyonlar** sekmesi **Benzetimi adı**, **Tıklama oranı**, **Risk altındaki hız** ve **Eylem'i** içerir.

:::image type="content" source="../../media/attack-sim-training-simulations-select-payload-details-payload-tab.png" alt-text="Microsoft 365 Defender portalındaki Saldırı simülasyonu eğitiminde yük ayrıntıları açılır öğesindeki Yük sekmesi" lightbox="../../media/attack-sim-training-simulations-select-payload-details-payload-tab.png":::

### <a name="login-page"></a>Oturum açma sayfası

Ayrıntılar açılır penceresini açmak için, satırda onay kutusu dışında herhangi bir yere tıklayarak yükü listeden seçin.

Yük ayrıntıları açılır öğesindeki **Oturum açma sayfası** sekmesi, yük için seçili olan oturum açma sayfasını gösterir.

Oturum açma sayfasının tamamını görüntülemek için, iki sayfalı oturum açma sayfaları için sayfanın altındaki **Sayfa 1** ve **Sayfa 2** bağlantılarını kullanın.

:::image type="content" source="../../media/attack-sim-training-simulations-select-payload-details-login-page-tab.png" alt-text="Microsoft 365 Defender portalındaki Saldırı simülasyonu eğitimi bölümünde yük ayrıntıları açılır öğesindeki oturum açma sayfası sekmesi" lightbox="../../media/attack-sim-training-simulations-select-payload-details-login-page-tab.png":::

Yükte kullanılan oturum açma sayfasını değiştirmek için Oturum açma sayfasını değiştir simgesine tıklayın ![.](../../media/m365-cc-sc-edit-icon.png) **Oturum açma sayfasını değiştirin**.

Görüntülenen **Oturum açma bilgilerini seçin sayfasında** , her oturum açma sayfası için aşağıdaki bilgiler gösterilir:

- **Ad**
- **Dil**
- **Kaynak**: Yerleşik oturum açma sayfaları için değer **Genel'dir**. Özel oturum açma sayfaları için değer **Kiracı'dır**.
- **Durum**: **Hazır** veya **Taslak**.
- **Oluşturan**: Yerleşik oturum açma sayfaları için değer **Microsoft'tur**. Özel oturum açma sayfaları için değer, oturum açma sayfasını oluşturan kullanıcının UPN değeridir.
- **Son değiştirme**
- **Eylemler**: Önizleme simgesine tıklayın ![.](../../media/m365-cc-sc-eye-icon.png) Oturum açma sayfasının önizlemesini görüntülemek için **önizleme**.

Listede oturum açma sayfası bulmak için Ara simgesini kullanın ![.](../../media/m365-cc-sc-search-icon.png) Oturum açma sayfasının adını bulmak için **arama** kutusu.

Filtre simgesine tıklayın ![.](../../media/m365-cc-sc-filter-icon.png) Oturum açma sayfalarını **Kaynağa** veya Dile göre filtrelemek için **filtreleyin**.

:::image type="content" source="../../media/attack-sim-training-simulations-select-payload-select-login-page.png" alt-text="Microsoft 365 Defender portalındaki Saldırı simülasyonu eğitimi bölümünde yük ayrıntıları açılır öğesindeki Oturum açma sayfası sekmesindeki Oturum açma bilgilerini seçin sayfası" lightbox="../../media/attack-sim-training-simulations-select-payload-select-login-page.png":::

Yeni oturum açma sayfası oluşturmak için [Yeni oluştur simgesine tıklayın.](../../media/m365-cc-sc-create-icon.png) Son kullanıcı oturum açma sayfası oluşturma sihirbazını başlatmak için **yeni oluşturun**. Adımlar **, Saldırı benzetimi eğitimi** \> **Sanal içerik kitaplığı** sekmesindeki **Oturum açma sayfalarıyla** aynıdır. Yönergeler için bkz. [Oturum açma sayfaları oluşturma](attack-simulation-training-login-pages.md#create-login-pages).

**Oturum açma seç sayfasına** geri dönün, oluşturduğunuz yeni oturum açma sayfasının seçili olduğunu doğrulayın ve **kaydet'e** tıklayın.

Yük ayrıntıları açılır menüsüne geri dönüp [Kapat simgesine tıklayın.](../../media/m365-cc-sc-close-icon.png) **Kapat'ı seçin**.

**Yük seçin ve oturum açın sayfasında** işiniz bittiğinde **İleri'ye** tıklayın.

## <a name="target-users"></a>Hedef kullanıcılar

**Hedef kullanıcılar** sayfasında simülasyonu alacak kullanıcıları seçin. Aşağıdaki ayarlardan birini yapılandırın:

- **Kuruluşunuzdaki tüm kullanıcıları dahil et**: Etkilenen kullanıcılar 10'lu listelerde gösterilir. Listede gezinmek için doğrudan kullanıcı listesinin altındaki **İleri** ve **Önceki** düğmelerini kullanabilirsiniz. Arama simgesini de kullanabilirsiniz ![.](../../media/m365-cc-sc-search-icon.png) Etkilenen kullanıcıları bulmak için sayfadaki **arama** simgesi.
- **Yalnızca belirli kullanıcıları ve grupları dahil et**: Aşağıdaki seçeneklerden birini belirleyin:
  - ![Kullanıcı ekle simgesi.](../../media/m365-cc-sc-create-icon.png) **Kullanıcı ekle**: Görüntülenen **Kullanıcı ekle** açılır listesinde, aşağıdaki ölçütlere göre kullanıcıları ve grupları bulabilirsiniz:
    - **Kullanıcılar veya gruplar**: ![Kullanıcı ve grup ara simgesinde.](../../media/m365-cc-sc-search-icon.png) **Kullanıcıları ve grupları ara** kutusuna, kullanıcı veya grubun **Ad** veya **E-posta adresinin** bir bölümünü yazıp Enter tuşuna basabilirsiniz. Sonuçların bir kısmını veya tümünü seçebilirsiniz. İşiniz bittiğinde **X kullanıcı ekle'ye** tıklayın.

      > [!NOTE]
      > **Kullanıcıları kategorilere göre filtrele** seçeneklerine dönmek için **Filtre ekle** düğmesine tıklanması, arama sonuçlarında seçtiğiniz tüm kullanıcıları veya grupları temizler.

    - **Kullanıcıları kategorilere göre filtrele**: Aşağıdaki seçeneklerden hiçbiri, bazıları veya tümü arasından seçim yapın:
      - **Önerilen kullanıcı grupları**: Aşağıdaki değerlerden birini seçin:
        - **Önerilen tüm kullanıcı grupları**
        - **Son üç ay içinde bir simülasyon tarafından hedeflenmemiş kullanıcılar**
        - **Tekrar eden suçlular**
      - **Departman**: Aşağıdaki seçenekleri kullanın:
        - **Arama**: Departmana ![Göre Ara simgesinde.](../../media/m365-cc-sc-search-icon.png) **Departmana göre ara** kutusuna Departman değerinin bir kısmını yazıp Enter tuşuna basabilirsiniz. Sonuçların bir kısmını veya tümünü seçebilirsiniz.
        - **Tüm Departman'ı** seçin
        - Mevcut Departman değerlerini seçin.
      - **Başlık**: Aşağıdaki seçenekleri kullanın:
        - **Arama**: Başlığa ![Göre Ara simgesinde.](../../media/m365-cc-sc-search-icon.png) **Başlığa Göre Ara** kutusuna Başlık değerinin bir kısmını yazıp Enter tuşuna basabilirsiniz. Sonuçların bir kısmını veya tümünü seçebilirsiniz.
        - **Tüm Başlığı** Seç
        - Mevcut Başlık değerlerini seçin.

      :::image type="content" source="../../media/attack-sim-training-simulations-target-users-filter-by-category.png" alt-text="Microsoft 365 Defender portalındaki Saldırı simülasyonu eğitimi sayfasındaki Hedef kullanıcılar sayfasında kullanıcı filtrelemesi" lightbox="../../media/attack-sim-training-simulations-target-users-filter-by-category.png":::

      Ölçütlerinizi belirledikten sonra, etkilenen kullanıcılar görüntülenen **Kullanıcı listesi** bölümünde gösterilir ve burada bulunan alıcılardan bazılarını veya tümünü seçebilirsiniz.

      İşiniz bittiğinde **Uygula(x)**'e ve ardından **X kullanıcı ekle'ye** tıklayın.

  **Ana Hedef kullanıcılar** sayfasına döndüğünüzde ![Ara simgesini kullanabilirsiniz.](../../media/m365-cc-sc-search-icon.png) Etkilenen kullanıcıları bulmak için **arama** kutusu. Sil simgesine de tıklayabilirsiniz ![.](../../media/m365-cc-sc-delete-icon.png) Belirli kullanıcıları kaldırmak için **silin**.

- ![İçeri aktar simgesi.](../../media/m365-cc-sc-create-icon.png) **İçeri Aktarma**: Açılan iletişim kutusunda, satır başına bir e-posta adresi içeren bir CSV dosyası belirtin.

  CSV dosyasını seçtikten sonra, kullanıcı listesi içeri aktarılır ve **Hedeflenen kullanıcılar** sayfasında gösterilir. Arama simgesini kullanabilirsiniz ![.](../../media/m365-cc-sc-search-icon.png) Etkilenen kullanıcıları bulmak için **arama** kutusu. Sil simgesine de tıklayabilirsiniz ![.](../../media/m365-cc-sc-delete-icon.png) Belirli kullanıcıları kaldırmak için **silin**.

İşiniz bittiğinde **İleri'ye** tıklayın.

## <a name="assign-training"></a>Eğitim atama

**Eğitim ata** sayfasında simülasyon için eğitimler atayabilirsiniz. Eğitimden geçen çalışanlar benzer saldırılara daha az duyarlı olduğundan her simülasyon için eğitim atamanızı öneririz. Aşağıdaki ayarlar kullanılabilir:

- **Eğitim içeriği tercihini seçin**: Aşağıdaki seçeneklerden birini belirleyin:
  - **Microsoft eğitim deneyimi**: Bu, yapılandırmak için aşağıdaki ilişkili seçenekleri içeren varsayılan değerdir:
    - Aşağıdaki seçeneklerden birini seçin:
      - **Benim için eğitim ata**: Bu varsayılan ve önerilen değerdir. Kullanıcının önceki simülasyon ve eğitim sonuçlarına göre eğitim atarız ve sihirbazın sonraki adımlarında seçimleri gözden geçirebilirsiniz.
      - **Eğitim kurslarını ve modülleri kendim seçin**: Bu değeri seçerseniz, sihirbazın bir sonraki adımında önerilen içeriğin yanı sıra tüm kullanılabilir kursları ve modülleri görmeye devam edebilirsiniz.
    - **Son tarih**: Aşağıdaki değerlerden birini seçin:
      - **Simülasyon sona erdikten 30 gün sonra**: Bu varsayılan değerdir.
      - **Simülasyon bittikten 15 gün sonra**
      - **Simülasyon bittikten 7 gün sonra**
  - **Özel URL'ye yeniden yönlendirme**: Bu değer, yapılandırmak için aşağıdaki ilişkili seçeneklere sahiptir:
    - **Özel eğitim URL'si** (gerekli)
    - **Özel eğitim adı** (gerekli)
    - **Özel eğitim açıklaması**
    - **Özel eğitim süresi (dakika cinsinden):** Varsayılan değer 0'dır ve bu da eğitim için belirtilen süre olmadığı anlamına gelir.
    - **Son tarih**: Aşağıdaki değerlerden birini seçin:
      - **Simülasyon sona erdikten 30 gün sonra**: Bu varsayılan değerdir.
      - **Simülasyon bittikten 15 gün sonra**
      - **Simülasyon bittikten 7 gün sonra**
  - **Eğitim yok**: Bu değeri seçerseniz sayfadaki tek seçenek, sizi [**Giriş sayfası**](#landing-page) sayfasına götüren **İleri** düğmesidir.

:::image type="content" source="../../media/attack-sim-training-simulations-assign-training-add-recommended-training.png" alt-text="Önerilen eğitimi Microsoft 365 Defender portalındaki Saldırı simülasyonu eğitimi'ndeki Eğitim ataması sayfasına ekleme seçeneği" lightbox="../../media/attack-sim-training-simulations-assign-training-add-recommended-training.png":::

### <a name="training-assignment"></a>Eğitim ataması

> [!NOTE]
> **Eğitim ataması** sayfası yalnızca önceki sayfada Eğitim **kursları ve modüllerini kendim seç** **Microsoft eğitim deneyimini** \> seçtiyseniz kullanılabilir.

**Eğitim ataması** sayfasında Eğitim ekle simgesine tıklayarak ![simülasyona eklemek istediğiniz eğitimleri seçin.](../../media/m365-cc-sc-create-icon.png) **Eğitimler ekleyin**.

Görüntülenen **Eğitim ekle** açılır öğesinde, aşağıdaki sekmelerde kullanılacak eğitimleri seçebilirsiniz:

- **Önerilen** sekmesi: Simülasyon yapılandırmasına göre önerilen yerleşik eğitimleri gösterir. Bunlar, önceki sayfada **Eğitimi benim için ata'yı** seçtiğinizde atanmış olan eğitimlerle aynıdır.
- **Tüm eğitimler** sekmesi: Kullanılabilir olan tüm yerleşik eğitimleri gösterir.

  Her eğitim için aşağıdaki bilgiler gösterilir:

  - **Eğitim adı**
  - **Kaynak**: Değer **Genel'dir**.
  - **Süre (mins)**
  - **Önizleme**: Eğitimi görmek için **Önizleme** düğmesine tıklayın.

  ![Ara simgesinde.](../../media/m365-cc-sc-search-icon.png) **Arama** kutusuna eğitim adının bir kısmını yazabilir ve geçerli sekmedeki sonuçları filtrelemek için Enter tuşuna basabilirsiniz.

  Geçerli sekmeden eklemek istediğiniz tüm eğitimleri seçin ve **ekle'ye** tıklayın.

Ana **Eğitim ödevi** sayfasına döndüğünüzde, seçtiğiniz eğitimler gösterilir. Her eğitim için aşağıdaki bilgiler gösterilir:

- **Eğitim adı**
- **Kaynak**
- **Süre (mins)**

Listedeki her eğitim için, eğitimi kimin aldığını yapılandırmak **için Ata** sütununda aşağıdaki değerlerden birini veya daha fazlasını seçin:

- **Tüm kullanıcılar**
- **Tıklanan yük**
- **Tehlikeye**

Gösterilen bir eğitimi kullanmak istemiyorsanız Sil simgesine tıklayın ![.](../../media/m365-cc-sc-delete-icon.png) **Sil'i seçin**.

:::image type="content" source="../../media/attack-sim-training-training-assignment.png" alt-text="Microsoft 365 Defender portalındaki Saldırı simülasyonu eğitimi'ndeki Eğitim atama sayfası" lightbox="../../media/attack-sim-training-training-assignment.png":::

İşiniz bittiğinde **İleri'ye** tıklayın.

### <a name="landing-page"></a>Giriş sayfası

**Giriş sayfası sayfasında**, simülasyonda yükü açan kullanıcının alındığı web sayfasını yapılandırabilirsiniz.

- **Giriş sayfası tercihini seçin**: Kullanılabilir değerler, aşağıdaki tabloda açıklandığı gibi [Yük seçin ve oturum açma sayfası sayfasındaki önceki yük](#select-a-payload-and-login-page) seçimlerinize bağlıdır:

  |Yük seçimi|Giriş sayfası seçme tercihi için kullanılabilir değerler|
  |---|---|
  |El ile|Microsoft varsayılan giriş sayfasını kullanma <br><br> Kendi giriş sayfanızı oluşturma <p> Özel URL kullanma <p> **Not**: Daha önce [Sosyal mühendislik tekniklerini seçin](#select-one-or-more-social-engineering-techniques) sayfasında **Kötü amaçlı yazılım eki** veya **Kötü amaçlı yazılım bağlantısı'nı** seçtiyseniz **Özel URL kullan** değeri kullanılamaz.|
  |Rastgele hale|Microsoft varsayılan giriş sayfasını kullanma|

  Kullanılabilir **Giriş sayfası tercih** değerlerini seçin ve ilişkili ayarları aşağıdaki listede açıklanmıştır:

  - **Microsoft varsayılan giriş sayfasını kullanın**. Bu varsayılan değerdir ve tüm yükler için geçerli olan bir Microsoft varsayılan şablonu, logosu ve yük göstergesi eylemiyle sonuçlanır.

    **Giriş sayfası** sayfasında aşağıdaki ek ayarları yapılandırmanız gerekir:

    - **Giriş sayfası düzenini seçin**: Kullanılabilir 5 giriş sayfası şablonundan birini seçin.
    - **Logo ekle**: Microsoft tarafından seçilen tüm yüklere eklenecek .png, .jpeg veya .gif dosyasını bulup seçmek için **Gözat'a** tıklayın. Bozulmayı önlemek için logo boyutu en fazla 210 x 70 olmalıdır. Logoyu kaldırmak için **Kaldır'a** tıklayın.
    - **Yük göstergeleri**: Sosyal [mühendislik tekniklerini seçin](#select-one-or-more-social-engineering-techniques) sayfasında daha önce **Kötü amaçlı yazılım eki** veya **Kötü amaçlı yazılım bağlantısı'nı** seçtiyseniz bu ayar kullanılamaz.

      Kullanıcıların kimlik avı iletilerini **tanımlamayı öğrenmesine yardımcı olmak için E-postaya yük göstergeleri ekle'yi** seçin.

    Sayfanın ortasındaki **Önizleme panelini aç** düğmesine tıklayarak sonuçların önizlemesini görüntüleyebilirsiniz. Görüntülenen önizleme açılır öğesinde Yükü seç'i kullanarak her **yükün** nasıl göründüğünü görebilirsiniz.

  - **Kendi giriş sayfanızı oluşturma**: Bu değer, seçilen yüklere uygulanan tek bir yük göstergesi eylemiyle sonuç verir.

    **Giriş sayfası** sayfasında aşağıdaki ek ayarları yapılandırmanız gerekir:

    - **Yük göstergeleri**: Bu ayar yalnızca aşağıdaki koşulların her ikisi de doğruysa seçilebilir:
      - Daha önce [Sosyal mühendislik tekniklerini seçin](#select-one-or-more-social-engineering-techniques) sayfasında **Kimlik bilgisi toplama**, **Ekteki bağlantı** veya **Sürücüye göre URL'yi** seçtiniz.
      - Sayfa **içeriğine e-posta içeriği ekle** adlı **Dinamik etiketi** ekledikten sonra.

    - Sayfa içeriği: İki sekme kullanılabilir:

      - **Metin**: Giriş sayfanızı oluşturmak için zengin bir metin düzenleyicisi kullanılabilir. Tipik yazı tipi ve biçimlendirme ayarlarına ek olarak aşağıdaki ayarlar da kullanılabilir:
        - **Dinamik etiket**: Aşağıdaki etiketler arasından seçim yapın:
          - **Ad ekle**
          - **Gönderen adı ekle**
          - **Gönderen e-postası ekleme**
          - **E-posta konusu ekle**
          - **E-posta içeriği ekleme**
          - **Tarih ekle**
        - **Varsayılandan kullanın**: Başlamak için 5 kullanılabilir giriş sayfası şablonundan birini seçin. Düzenleme alanındaki metni ve düzeni değiştirebilirsiniz. Giriş sayfasını şablonun varsayılan metnine ve düzenine geri döndürmek **için Varsayılana sıfırla'ya** tıklayın.
        - **Eğitim bağlantısı**: Görüntülenen **Eğitim URL'sini adlandır** iletişim kutusunda, eğitim bağlantısı için bir bağlantı başlığı girin ve ardından bağlantıyı giriş sayfasına eklemek için **Onayla'ya** tıklayın.
      - **Kod**: HTML kodunu doğrudan görüntüleyebilir ve değiştirebilirsiniz.

      Sayfanın ortasındaki **Önizleme panelini aç** düğmesine tıklayarak sonuçların önizlemesini görüntüleyebilirsiniz. Görüntülenen önizleme açılır öğesinde Yükü seç'i kullanarak her **yükün** nasıl göründüğünü görebilirsiniz.

  - **Özel URL kullanma**: Görüntülenen **Özel giriş sayfası URL'sini girin** kutusuna URL'yi ekleyin. Sayfada başka seçenek yoktur.

İşiniz bittiğinde **İleri'ye** tıklayın.

## <a name="select-end-user-notification"></a>Son kullanıcı bildirimini seçme

**Son kullanıcı bildirimini seçin** sayfasında aşağıdaki bildirim seçeneklerinden birini belirleyin:

- **Bildirimleri teslim etme**: Görüntülenen uyarı iletişim kutusunda **Devam'a** tıklayın. Bu seçeneği seçerseniz **, İleri'ye** tıkladığınızda [Simülasyon zamanlaması](#simulation-schedule) sayfasına yönlendirilirsiniz.

- **Microsoft varsayılan bildirimi (önerilen)**: Sayfada aşağıdaki ek ayarlar kullanılabilir:

  - **Varsayılan dili seçin**: Kullanılabilir değerler şunlardır: **Çince (Basitleştirilmiş)**, **Çince (Geleneksel)**, **İngilizce**, **Fransızca**, **Almanca**, **İtalyanca**, **Japonca**, **Korece**, **Portekizce**, **Rusça**, **İspanyolca** ve **Felemenkçe**.

  - Varsayılan olarak, aşağıdaki bildirimler dahil edilir:
    - **Microsoft pozitif takviye bildirimi**
    - **Microsoft varsayılan eğitim ataması bildirimi**
    - **Microsoft varsayılan eğitim anımsatıcı bildirimi**

    Her bildirim için aşağıdaki bilgiler sağlanır:
    - **Bildirimler**: Bildirimin adı.
    - **Dil**: Bildirim birden çok çeviri içeriyorsa, ilk iki dil doğrudan gösterilir. Kalan dilleri görmek için, sayısal simgenin üzerine gelin (örneğin, **+10**).
    - **Tür**: Aşağıdaki değerlerden biri:
      - **Pozitif pekiştirme bildirimi**
      - **Eğitim ataması bildirimi**
      - **Eğitim anımsatıcısı bildirimi**
    - **Teslim tercihleri**: **Pozitif pekiştirme bildirimi** ve **Eğitim anımsatıcısı bildirim** türleri için aşağıdaki değerler kullanılabilir
      - **Teslim etme**
      - **Kampanya sona erdikten sonra teslim**
      - **Kampanya sırasında teslim**
    - **Eylemler**: Görünüm simgesine ![tıklarsanız.](../../media/m365-cc-sc-view-icon.png) **Görünüm** simgesi, **Gözden geçir bildirimi** sayfası aşağıdaki bilgilerle birlikte görüntülenir:
      - **Önizleme** sekmesi: Kullanıcıların göreceği şekilde bildirim iletisini görüntüleyin.
        - İletiyi farklı dillerde görüntülemek için **Dil seçin** kutusunu kullanın.
        - Birden çok yük içeren simülasyonlar için bildirim iletisini seçmek için **Önizlemeye yük seçin** kutusunu kullanın.
      - **Ayrıntılar** sekmesi: Bildirimle ilgili ayrıntıları görüntüleyin:
        - **Bildirim açıklaması**
        - **Kaynak**: Yerleşik bildirimler için değer **Genel'dir**. Özel bildirimler için değer **Kiracı'dır**.
        - **Bildirim türü**: Aşağıdaki türlerden biri başlangıçta seçtiğiniz bildirimi temel alır:
          - **Pozitif pekiştirme bildirimi**
          - **Eğitim ataması bildirimi**
          - **Eğitim anımsatıcısı bildirimi**
        - **Değiştiren**
        - **Son değiştirme**

        İşlemi tamamladığınızda, **Kapat**'a tıklayın.

  **İleri'ye** tıkladığınızda [Simülasyon zamanlaması](#simulation-schedule) sayfasına yönlendirilirsiniz.

- **Özelleştirilmiş son kullanıcı bildirimleri**: **İleri'ye** tıkladığınızda, sonraki bölümlerde açıklandığı gibi **Eğitim ataması bildirim** sayfasına yönlendirilirsiniz.

### <a name="training-assignment-notification"></a>Eğitim ataması bildirimi

**Eğitim ataması bildirim** sayfası yalnızca **[Son](#select-end-user-notification)** **kullanıcı bildirimini seçin sayfasında Özelleştirilmiş son kullanıcı bildirimleri'ni** seçtiğinizde kullanılabilir.

Bu sayfada aşağıdaki bildirimler ve yapılandırılan dilleri gösterilir:

- **Microsoft varsayılan eğitim ataması bildirimi**
- Daha önce oluşturduğunuz tüm özel eğitim atama bildirimleri.

  Bu bildirimler, konumundaki Saldırı benzetimi eğitimi'nin **Simülasyon içerik kitaplığı** sekmesindeki **Son kullanıcı bildirimlerinde** <https://security.microsoft.com/attacksimulator?viewid=simulationcontentlibrary>de kullanılabilir. **Microsoft varsayılan eğitim ataması bildirimi** Genel **bildirimler** sekmesinde bulunur. Özel eğitim ataması bildirimleri **Kiracı bildirimleri** sekmesinde bulunur. Daha fazla bilgi için bkz [. Saldırı benzetimi eğitimi için son kullanıcı bildirimleri](attack-simulation-training-end-user-notifications.md).

Var olan bir eğitim ataması bildirimini seçebilir veya kullanmak için yeni bir bildirim oluşturabilirsiniz:

- Mevcut bir bildirimi seçmek için bildirim adının yanındaki boş alana tıklayın. Bildirim adına tıklarsanız bildirim seçilir ve önizleme açılır öğesi görüntülenir. Bildirimin seçimini kaldırmak için bildirimin yanındaki onay kutusunu temizleyin.
- Var olan bir bildirimi aramak için Ara simgesini kullanın ![.](../../media/m365-cc-sc-search-icon.png) Adı aramak için **arama kutusu.**

  Kullanmak istediğiniz bildirimi seçin ve **İleri'ye** tıklayın.

- Yeni bildirim oluşturmak ve kullanmak için Yeni oluştur simgesine tıklayın ![.](../../media/m365-cc-sc-create-icon.png) **Yeni oluşturun**.

#### <a name="create-new-training-assignment-notification-wizard"></a>Yeni eğitim ataması bildirim sihirbazı oluşturma

Yeni oluştur simgesine ![tıkladıysanız.](../../media/m365-cc-sc-create-icon.png) **Eğitim ataması bildirim** sayfasında **yeni oluşturun**; bildirim oluşturma sihirbazı açılır.

Oluşturma adımları [, Son kullanıcı bildirimleri oluşturma](attack-simulation-training-end-user-notifications.md#create-end-user-notifications) bölümünde açıklandığı gibi aynıdır.

> [!NOTE]
> **Ayrıntıları tanımla** sayfasında, **Bildirim türünü seçin** için **Eğitim atama bildirimi** değerini seçtiğinizden emin olun.

İşiniz bittiğinde, yeni oluşturduğunuz **bildirimin listede göründüğü Eğitim ataması bildirim** sayfasına geri dönersiniz.

Kullanmak istediğiniz bildirimi seçin ve **İleri'ye** tıklayın.

### <a name="training-reminder-notification"></a>Eğitim anımsatıcısı bildirimi

**Eğitim anımsatıcısı bildirim** sayfası yalnızca **[Son kullanıcı](#select-end-user-notification)** **bildirimini seçin sayfasında Özelleştirilmiş son kullanıcı bildirimleri'ni** seçtiğinizde kullanılabilir.

- **Anımsatıcı bildirimi için sıklık ayarla**: **Haftalık** (varsayılan) veya **Haftada iki kez'yi** seçin.

- **Anımsatıcı bildirimi seçin**: Bu bölümde aşağıdaki bildirimler ve yapılandırılan dilleri gösterilir:

  - **Microsoft varsayılan eğitim anımsatıcı bildirimi**
  - Daha önce oluşturduğunuz tüm özel eğitim anımsatıcı bildirimleri.

    Bu bildirimler, konumundaki Saldırı benzetimi eğitimi'nin **Simülasyon içerik kitaplığı** sekmesindeki **Son kullanıcı bildirimlerinde** <https://security.microsoft.com/attacksimulator?viewid=simulationcontentlibrary>de kullanılabilir. **Microsoft varsayılan eğitim anımsatıcı bildirimi** Genel **bildirimler** sekmesinde bulunur. Özel eğitim anımsatıcısı bildirimleri **Kiracı bildirimleri** sekmesinde bulunur. Daha fazla bilgi için bkz [. Saldırı benzetimi eğitimi için son kullanıcı bildirimleri](attack-simulation-training-end-user-notifications.md).

  Var olan bir eğitim anımsatıcısı bildirimini seçebilir veya kullanmak için yeni bir bildirim oluşturabilirsiniz:

  - Mevcut bir bildirimi seçmek için bildirim adının yanındaki boş alana tıklayın. Bildirim adına tıklarsanız bildirim seçilir ve önizleme açılır öğesi görüntülenir. Bildirimin seçimini kaldırmak için bildirimin yanındaki onay kutusunu temizleyin.
  - Var olan bir bildirimi aramak için Ara simgesini kullanın ![.](../../media/m365-cc-sc-search-icon.png) Adı aramak için **arama kutusu.**

    Kullanmak istediğiniz bildirimi seçin ve **İleri'ye** tıklayın.

  - Yeni bildirim oluşturmak ve kullanmak için Yeni oluştur simgesine tıklayın ![.](../../media/m365-cc-sc-create-icon.png) **Yeni oluşturun**.

#### <a name="create-new-training-reminder-notification-wizard"></a>Yeni eğitim anımsatıcısı bildirim sihirbazı oluşturma

Yeni oluştur simgesine ![tıkladıysanız.](../../media/m365-cc-sc-create-icon.png) **Eğitim anımsatıcısı bildirim** sayfasında **yeni oluşturun**; bildirim oluşturma sihirbazı açılır.

Oluşturma adımları [, Son kullanıcı bildirimleri oluşturma](attack-simulation-training-end-user-notifications.md#create-end-user-notifications) bölümünde açıklandığı gibi aynıdır.

> [!NOTE]
> **Ayrıntıları tanımla** sayfasında, **Bildirim türünü seçin** için **Eğitim anımsatıcı bildirimi** değerini seçtiğinizden emin olun.

İşiniz bittiğinde, yeni oluşturduğunuz **bildirimin listede göründüğü Eğitim anımsatıcısı bildirim** sayfasına geri dönersiniz.

Kullanmak istediğiniz bildirimi seçin ve **İleri'ye** tıklayın.

### <a name="positive-reinforcement-notification"></a>Pozitif pekiştirme bildirimi

**Pozitif pekiştirme bildirimi** sayfası yalnızca **[Son kullanıcı](#select-end-user-notification)** **bildirimlerini seçin sayfasında Özelleştirilmiş son kullanıcı bildirimleri'ni** seçtiğinizde kullanılabilir.

- **Teslim tercihleri**: Aşağıdaki değerlerden birini seçin:

  - **Teslim etme**: Bu seçeneği belirlediğinizde, **İleri'ye** tıkladığınızda [Simülasyon zamanlaması](#simulation-schedule) sayfasına yönlendirilirsiniz.

  - **Kullanıcı kimlik avı ve kampanya sona erdikten** sonra **teslim etme veya Kullanıcı kimlik avı bildirdikten hemen sonra teslim etme**: Bu bölümlerde, görüntülenen **Pozitif bir pekiştirme bildirimi seçin** bölümünde aşağıdaki bildirimler ve yapılandırılan dilleri gösterilir:

  - **Microsoft varsayılan pozitif takviye bildirimi**
  - Daha önce oluşturduğunuz tüm özel pozitif takviye bildirimleri.

    Bu bildirimler, konumundaki Saldırı benzetimi eğitimi'nin **Simülasyon içerik kitaplığı** sekmesindeki **Son kullanıcı bildirimlerinde** <https://security.microsoft.com/attacksimulator?viewid=simulationcontentlibrary>de kullanılabilir. **Microsoft varsayılan pozitif takviye bildirimi** Genel **bildirimler** sekmesinde bulunur. Kiracı bildirimleri sekmesinde özel pozitif takviye **bildirimleri** bulunur. Daha fazla bilgi için bkz [. Saldırı benzetimi eğitimi için son kullanıcı bildirimleri](attack-simulation-training-end-user-notifications.md).

  Mevcut bir pozitif takviye bildirimi seçebilir veya kullanmak için yeni bir bildirim oluşturabilirsiniz:

  - Mevcut bir bildirimi seçmek için bildirim adının yanındaki boş alana tıklayın. Bildirim adına tıklarsanız bildirim seçilir ve önizleme açılır öğesi görüntülenir. Bildirimin seçimini kaldırmak için bildirimin yanındaki onay kutusunu temizleyin.
  - Var olan bir bildirimi aramak için Ara simgesini kullanın ![.](../../media/m365-cc-sc-search-icon.png) Adı aramak için **arama kutusu.**

    Kullanmak istediğiniz bildirimi seçin ve **İleri'ye** tıklayın.

  - Yeni bildirim oluşturmak ve kullanmak için Yeni oluştur simgesine tıklayın ![.](../../media/m365-cc-sc-create-icon.png) **Yeni oluşturun**.

#### <a name="create-new-positive-reinforcement-notification-wizard"></a>Yeni pozitif takviye bildirimi oluşturma sihirbazı

Yeni oluştur simgesine ![tıkladıysanız.](../../media/m365-cc-sc-create-icon.png) **Pozitif pekiştirme bildirimi** sayfasında **yeni bir oluşturma** sihirbazı açılır.

Oluşturma adımları [, Son kullanıcı bildirimleri oluşturma](attack-simulation-training-end-user-notifications.md#create-end-user-notifications) bölümünde açıklandığı gibi aynıdır.

> [!NOTE]
> **Ayrıntıları tanımla** sayfasında Bildirim **türünü seçin** için **Pozitif destek bildirimi** değerini seçtiğinizden emin olun.

İşiniz bittiğinde, yeni oluşturduğunuz **bildirimin listede göründüğü Pozitif pekiştirme bildirimi** sayfasına geri dönersiniz.

Kullanmak istediğiniz bildirimi seçin ve **İleri'ye** tıklayın.

## <a name="simulation-schedule"></a>Simülasyon zamanlaması

**Simülasyon zamanlaması** sayfasında aşağıdaki değerlerden birini seçin:

- **Rastgele**: Yine de sonraki sayfada zamanlamayı seçmeniz gerekir, ancak simülasyonlar zamanlamayla birlikte rastgele zamanlarda başlatılır.
- **Sabit**

İşiniz bittiğinde **İleri'ye** tıklayın.

## <a name="schedule-details"></a>Zamanlama ayrıntıları

**Zamanlama ayrıntıları** sayfasında ne göreceğiniz, önceki sayfada **Rastgele** mi yoksa **Sabit** mi seçtiğinize bağlıdır.

- **Rastgele**: Aşağıdaki ayarlar kullanılabilir:
  - **Simülasyon başlangıç** bölümü: Aşağıdaki ayarı yapılandırın:
    - **Simülasyonların başlamasını istediğiniz tarihi seçin**
  - **Simülasyon kapsam belirleme** bölümü: Aşağıdaki ayarları yapılandırın:
    - **Simülasyonların başlamasına izin verilen haftanın günlerini seçin**: Haftanın bir veya daha fazla gününü seçin.
    - **Başlangıç ve bitiş tarihleri arasında başlatabileceğiniz en fazla simülasyon sayısını girin**: 1 ile 10 arasında bir değer girin.
    - **Gönderme zamanlarını rastgele seçin: Gönderme** zamanlarını rastgele belirlemek için bu ayarı seçin.
  - **Simülasyon sonu** bölümü: Aşağıdaki ayarı yapılandırın:
    - **Simülasyonların bitmesini istediğiniz tarihi seçin**

- **Düzeltildi**: Aşağıdaki ayarlar kullanılabilir:
  - **Simülasyon başlangıç** bölümü: Aşağıdaki ayarı yapılandırın:
    - **Simülasyonların başlamasını istediğiniz tarihi seçin**
  - **Simülasyon yinelenme** bölümü: Aşağıdaki ayarları yapılandırın:
    - **Simülasyonların haftalık veya aylık olarak başlatılmasını isteyip istemediğinizi seçin**: Aşağıdaki değerlerden birini seçin:
      - **Haftalık**: Bu varsayılan değerdir.
      - **Aylık**
    - **Benzetimi kaç hafta içinde yinelemek istediğinizi girin**: 1 ile 99 hafta arası bir değer girin.
    - **Simülasyonların başlamasını istediğiniz haftanın gününü seçin**
  - **Simülasyon sonu** bölümü: Aşağıdaki değerlerden birini seçin:
    - **Simülasyonların bitmesini istediğiniz tarihi seçin**
    - **Tamamlanmadan önce çalıştırılacak simülasyonların oluşum sayısını girin**: 1 ile 10 arasına bir değer girin.

İşiniz bittiğinde **İleri'ye** tıklayın.

## <a name="launch-details"></a>Başlatma ayrıntıları

**Başlatma ayrıntıları** sayfasında otomasyon için aşağıdaki ek ayarları yapılandırın:

- **Otomasyon içindeki simülasyonlar arasında benzersiz yükleri kullanın**: Varsayılan olarak, bu ayar seçilmez.
- **Hedef yinelenen suçlular**: Varsayılan olarak bu ayar seçili değildir. Bunu seçerseniz, görüntülenen aşağıdaki ayarı yapılandırın:
  - **Bu otomasyonda bir kullanıcının hedeflenebileceği maksimum sayı**: 1 ile 10 arasına bir değer girin.
- **Outlook web uygulamasından kullanıcının geçerli saat dilimi ayarına göre simülasyon e-postası gönder**: Varsayılan olarak, bu ayar seçili değildir.
- **Toplanan sürücüye göre teknik ara verilerini görüntüleme sayfası**: Bu ayar yalnızca **[Sosyal mühendislik tekniklerini seçin](#select-one-or-more-social-engineering-techniques)** sayfasında **Drive-by URL'sini** seçtiyseniz kullanılabilir. Varsayılan olarak, ayar açıktır (![Simgeyi aç/kapat).](../../media/scc-toggle-on.png)).

## <a name="review-simulation-automation"></a>Simülasyon otomasyonlarını gözden geçirme

**Simülasyon otomasyonunu gözden geçir** sayfasında simülasyon otomasyonunuzun ayrıntılarını gözden geçirebilirsiniz.

Bölümün içindeki ayarları değiştirmek için her bölümde **Düzenle'yi** seçebilirsiniz. Ya da **Geri'ye** tıklayabilir veya sihirbazdaki belirli bir sayfayı seçebilirsiniz.

İşiniz bittiğinde **Gönder'e** tıklayın.
