---
title: Saldırı simülasyonu eğitimi ile kimlik avı saldırısı simüle etme
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
description: Yöneticiler, Office 365 için Microsoft Defender Plan 2'deki Saldırı benzetimi eğitimini kullanarak kimlik avı saldırılarının simülasyonunu yapmayı ve kullanıcılarını kimlik avı önleme konusunda eğitmeyi öğrenebilir.
ms.technology: mdo
ms.openlocfilehash: 94e002adf3fcdefcb3d2483f4f32ce7b10be8dab
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65077647"
---
# <a name="simulate-a-phishing-attack-with-attack-simulation-training-in-defender-for-office-365"></a>Office 365 için Defender'de Saldırı simülasyonu eğitimi ile kimlik avı saldırısı simülasyonu

[Office 365 için Microsoft Defender plan 2](defender-for-office-365.md) **için geçerlidir**

Office 365 için Microsoft Defender Plan 2 veya Microsoft 365 E5'da saldırı simülasyonu eğitimi, kuruluşunuzda zararsız siber saldırı simülasyonları çalıştırmanıza olanak tanır. Bu simülasyonlar güvenlik ilkelerinizi ve uygulamalarınızı test eder, ayrıca çalışanlarınızı farkındalıklarını artırmaları ve saldırılara karşı duyarlılıklarını azaltmaları için eğitebilir. Bu makalede, Saldırı simülasyonu eğitimini kullanarak sanal kimlik avı saldırısı oluşturma konusunda size yol gösterir.

Saldırı simülasyonu eğitimi hakkında başlangıç bilgileri için bkz. [Saldırı simülasyonu eğitimini kullanarak Kullanmaya başlayın](attack-simulation-training-get-started.md).

Kimlik avı simülasyonu saldırısı başlatmak için aşağıdaki adımları uygulayın:

1. konumundaki Microsoft 365 Defender portalında<https://security.microsoft.com>**, E-posta & işbirliği** \> **Saldırı benzetimi eğitimi** \> **Simülasyonları** sekmesine gidin.

   Doğrudan **Simülasyonlar** sekmesine gitmek için kullanın <https://security.microsoft.com/attacksimulator?viewid=simulations>.

2. **Simülasyonlar sekmesinde Simülasyon** simgesini başlat'ı seçin![.](../../media/m365-cc-sc-create-icon.png) **Simülasyonu başlatın**.

   :::image type="content" source="../../media/attack-sim-training-simulations-launch.png" alt-text="Microsoft 365 Defender portalındaki Saldırı simülasyonu eğitimi'ndeki Simülasyonlar sekmesindeki Simülasyon başlat düğmesi" lightbox="../../media/attack-sim-training-simulations-launch.png":::

3. Simülasyon oluşturma sihirbazı açılır. Bu makalenin geri kalanında sayfalar ve içerdikleri ayarlar açıklanmaktadır.

> [!NOTE]
> Simülasyon oluşturma sihirbazı sırasında herhangi bir noktada Kaydet **ve kapat'a** tıklayarak ilerlemenizi kaydedebilir ve simülasyonu daha sonra yapılandırmaya devam edebilirsiniz. Tamamlanmamış simülasyon, **Simülasyonlar** sekmesinde **Taslak Durum** değerine sahiptir. Simülasyonu seçip Simülasyonu düzenle simgesine tıklayarak ![kaldığınız yerden devam edebilirsiniz.](../../media/m365-cc-sc-edit-icon.png) **Simülasyonu düzenleme** .

## <a name="select-a-social-engineering-technique"></a>Sosyal mühendislik tekniği seçme

**Tekniği seçin** sayfasında, [MITRE ATT&CK® çerçevesinden](https://attack.mitre.org/techniques/enterprise/) seçilen kullanılabilir bir sosyal mühendislik tekniği seçin. Farklı teknikler için farklı yükler kullanılabilir. Aşağıdaki sosyal mühendislik teknikleri mevcuttur:

- **Kimlik bilgisi toplama**: Kullanıcı adı ve parola göndermek için kullanıcıları giriş kutularıyla iyi bilinen bir web sitesine götürerek kimlik bilgilerini toplamaya çalışır.
- **Kötü amaçlı yazılım eki**: İletiye kötü amaçlı bir ek ekler. Kullanıcı eki açtığında, saldırganın hedefin cihazını tehlikeye atılmasına yardımcı olacak rastgele kod çalıştırılır.
- **Ekteki bağlantı**: Kimlik bilgisi toplama karma türü. Saldırgan bir e-posta ekine URL ekler. Ek içindeki URL, kimlik bilgisi toplama ile aynı tekniği izler.
- **Kötü amaçlı yazılım bağlantısı**: İyi bilinen bir dosya paylaşım hizmetinde barındırılan bir dosyadan rastgele kod çalıştırır. Kullanıcıya gönderilen ileti bu kötü amaçlı dosyanın bağlantısını içerir. Dosyayı açmak, saldırganın hedefin cihazını tehlikeye atılmasına yardımcı olur.
- **Sürücü URL'si**: İletideki kötü amaçlı URL, kullanıcıyı sessizce çalışan ve/veya kullanıcının cihazına kod yükleyen tanıdık görünen bir web sitesine götürür.

Açıklamadaki **Ayrıntıları görüntüle** bağlantısına tıklarsanız, tekniği ve teknikten kaynaklanan simülasyon adımlarını açıklayan bir ayrıntı açılır öğesi açılır.

:::image type="content" source="../../media/attack-sim-training-simulations-select-technique-sim-steps.png" alt-text="Seçme tekniği sayfasındaki kimlik bilgisi toplama tekniği için Ayrıntılar açılır öğesi" lightbox="../../media/attack-sim-training-simulations-select-technique-sim-steps.png":::

İşiniz bittiğinde **İleri'ye** tıklayın.

## <a name="name-and-describe-the-simulation"></a>Benzetimi adlandırma ve açıklama

**Ad benzetimi** sayfasında aşağıdaki ayarları yapılandırın:

- **Ad**: Simülasyon için benzersiz, açıklayıcı bir ad girin.
- **Açıklama**: Simülasyon için isteğe bağlı ayrıntılı bir açıklama girin.

İşiniz bittiğinde **İleri'ye** tıklayın.

## <a name="select-a-payload"></a>Yük seçin

**Yükü seçin** sayfasında, listeden mevcut bir yükü seçmeniz veya yeni bir yük oluşturmanız gerekir.

Aşağıdaki ayrıntılar, seçmenize yardımcı olacak yük listesinde görüntülenir:

- **Yük adı**
- **Dil**: Yük içeriğinin dili. Microsoft'un yük kataloğu (genel), filtrelenebilen 10'undan fazla dilde yük sağlar.
- **Tıklama oranı**: Bu yüke kaç kişinin tıklamış olduğu.
- **Tahmin edilen risk oranı**: Microsoft 365 genelinde yükün geçmiş verileri, bu yük tarafından tehlikeye atılacak kişilerin yüzdesini tahmin eder.
- **Başlatılan simülasyonlar** , bu yükün diğer simülasyonlarda kaç kez kullanıldığını sayar.

![Ara simgesinde.](../../media/m365-cc-sc-search-icon.png) **Arama** kutusuna yük adının bir kısmını yazabilir ve sonuçları filtrelemek için Enter tuşuna basabilirsiniz.

**Filtre'ye** tıklarsanız aşağıdaki filtreler kullanılabilir:

- **Kaynak**: Yükün kuruluşunuzda mı oluşturulduğunu yoksa Microsoft'un önceden var olan yük kataloğunun bir parçası mı olduğunu gösterir. Geçerli değerler şunlardır:
  - **Genel** (yerleşik)
  - **Kiracı** (özel)
  - **Tüm**

- **Karmaşıklık**: Yükteki olası bir saldırıyı (yazım hataları, aciliyet vb.) gösteren gösterge sayısına göre hesaplanır. Daha fazla göstergenin saldırı olarak tanımlanması daha kolaydır ve daha düşük karmaşıklığı gösterir. Kullanılabilir değerler şunlardır:
  - **Düşük**
  - **Orta**
  - **Yüksek**

- **Dil**: Kullanılabilir değerler şunlardır: **Çince (Basitleştirilmiş)**, **Çince (Geleneksel)**, **İngilizce**, **Fransızca**, **Almanca**, **İtalyanca**, **Japonca**, **Korece**, **Portekizce**, **Rusça**, **İspanyolca** ve **Felemenkçe**.

- **Etiket ekleme**

- **Temaya göre filtrele**: Hesap **etkinleştirme**, **Hesap doğrulama**, **Faturalama**, **Posta temizleme**, **Alınan belge**, **Gider**, **Faks**, **Finans raporu**, **Gelen iletiler**, **Fatura**, **Alınan Öğeler**, **Oturum açma uyarısı**, **Alınan posta**, **Parola**, **Ödeme**, **Bordro**, **Kişiselleştirilmiş teklif**, **Karantina**, **Uzaktan çalışma**, **İletiyi gözden geçirme**, **Güvenlik güncelleştirmesi**, **Hizmet askıya alındı**, **İmza gerekiyor**, **Posta kutusu depolama alanını yükselt Posta kutusunu**, **Sesli mesajı** ve **Diğer'i** doğrulayın.

- **Markaya göre filtrele**: Kullanılabilir değerler şunlardır: **American Express**, **Capital One**, **DHL**, **DocuSign**, **Dropbox**, **Facebook**, **First American**, **Microsoft**, **Netflix**, **Scotiabank**, **SendGrid**, **Stewart Title**, **Tesco**, **Wells Fargo**, **Syrinx Cloud** ve **Diğer**.

- **Sektöre göre filtrele**: **Bankacılık**, **İş hizmetleri**, **Tüketici hizmetleri**, **Eğitim**, **Enerji**, **İnşaat**, **Danışmanlık**, **Finansal hizmetler**, **Kamu**, **Konaklama**, **Sigorta**, **Yasal**, **Kurye hizmetleri**, **BT**, **Sağlık**, **İmalat**, **Perakende**, **Telekom**, **Emlak**, ve **Diğer**.

- **Geçerli olay**: Kullanılabilir değerler **Evet** veya **Hayır'dır**.

- **Tartışmalı**: Kullanılabilir değerler **Evet** veya **Hayır'dır**.

Filtreleri yapılandırmayı bitirdiğinizde **Uygula**, **İptal veya** **Filtreleri temizle'ye** tıklayın.

:::image type="content" source="../../media/attack-sim-training-simulations-select-payload.png" alt-text="Microsoft 365 Defender portalındaki Saldırı benzetimi eğitimi'ndeki Yük seçin sayfası" lightbox="../../media/attack-sim-training-simulations-select-payload.png":::

Listeden bir yük seçerseniz, yükle ilgili ayrıntılar açılır pencerede gösterilir:

- **Genel Bakış** sekmesi, yükle ilgili bir örnek ve diğer ayrıntıları içerir.
- **Başlatılan Simülasyonlar** sekmesi **Benzetimi adı**, **Tıklama oranı**, **Risk altındaki hız** ve **Eylem'i** içerir.

:::image type="content" source="../../media/attack-sim-training-simulations-select-payload-details.png" alt-text="Microsoft 365 Defender portalındaki Saldırı simülasyonu eğitiminde Yük ayrıntıları açılır öğesi" lightbox="../../media/attack-sim-training-simulations-select-payload-details.png":::

Listeden ada tıklayarak bir yük seçerseniz, Test ![yükü gönder simgesi.](../../media/m365-cc-sc-create-icon.png) Ana sayfada yük e-postasının bir kopyasını inceleme için kendinize (şu anda oturum açmış olan kullanıcı) gönderebileceğiniz **bir test** düğmesi görüntülenir.

Kendi yükünüzü oluşturmak için Yük oluştur simgesine tıklayın ![.](../../media/m365-cc-sc-create-icon.png) **Yük oluşturma**. Daha fazla bilgi için bkz [. Saldırı benzetimi eğitimi için özel yük oluşturma](attack-simulation-training-payloads.md).

İşiniz bittiğinde **İleri'ye** tıklayın.

## <a name="target-users"></a>Hedef kullanıcılar

**Hedef kullanıcılar** sayfasında simülasyonu alacak kullanıcıları seçin. Aşağıdaki ayarlardan birini yapılandırın:

- **Kuruluşunuzdaki tüm kullanıcıları dahil et**: Etkilenen kullanıcılar 10'lu listelerde gösterilir. Listede gezinmek için doğrudan kullanıcı listesinin altındaki **İleri** ve **Önceki** düğmelerini kullanabilirsiniz. Arama simgesini de kullanabilirsiniz ![.](../../media/m365-cc-sc-search-icon.png) Etkilenen kullanıcıları bulmak için sayfadaki **arama** simgesi.

- **Yalnızca belirli kullanıcıları ve grupları dahil et**: Aşağıdaki seçeneklerden birini belirleyin:
  - ![Kullanıcı ekle simgesi.](../../media/m365-cc-sc-create-icon.png) **Kullanıcı ekle**: Görüntülenen **Kullanıcı ekle** açılır listesinde, aşağıdaki ölçütlere göre kullanıcıları ve grupları bulabilirsiniz:

    - **Kullanıcıları veya grupları arayın**: Kutuya, kullanıcı veya grubun **Ad** veya **E-posta adresinin** bir bölümünü yazıp Enter tuşuna basabilirsiniz. Sonuçların bir kısmını veya tümünü seçebilirsiniz. İşiniz bittiğinde **X kullanıcı ekle'ye** tıklayın.

      > [!NOTE]
      > **Kullanıcıları kategorilere göre filtrele** seçeneklerine dönmek için **Filtre ekle** düğmesine tıklanması, arama sonuçlarında seçtiğiniz tüm kullanıcıları veya grupları temizler.

    - **Kullanıcıları kategorilere göre filtrele**: Aşağıdaki seçeneklerden hiçbiri, bazıları veya tümü arasından seçim yapın:

      - **Önerilen kullanıcı grupları**: Aşağıdaki değerlerden birini seçin:
        - **Önerilen tüm kullanıcı grupları**
        - **Son üç ay içinde bir simülasyon tarafından hedeflenmemiş kullanıcılar**
        - **Tekrar eden suçlular**

      - **Kullanıcı etiketleri**: Kullanıcı etiketleri, belirli kullanıcı gruplarının tanımlayıcılarıdır (örneğin, Öncelik hesapları). Daha fazla bilgi için bkz. [Office 365 için Microsoft Defender'de kullanıcı etiketleri](user-tags.md).

          Aşağıdaki seçenekleri kullanın:

        - **Arama**: ![Kullanıcı etiketlerine göre ara simgesi.](../../media/m365-cc-sc-search-icon.png) **Kullanıcı etiketlerine göre arama** yapın, kullanıcı etiketinin bir kısmını yazıp Enter tuşuna basabilirsiniz. Sonuçların bir kısmını veya tümünü seçebilirsiniz.
        - **Tüm kullanıcı etiketlerini** seçin
        - Mevcut kullanıcı etiketlerini seçin.

      - **Departman**: Aşağıdaki seçenekleri kullanın:
        - **Arama**: ![Bölüme Göre Ara simgesinde.](../../media/m365-cc-sc-search-icon.png) **Departmana göre arama** yapın, Bölüm değerinin bir kısmını yazıp Enter tuşuna basabilirsiniz. Sonuçların bir kısmını veya tümünü seçebilirsiniz.
        - **Tüm Departman'ı** seçin
        - Mevcut Departman değerlerini seçin.

      - **Başlık**: Aşağıdaki seçenekleri kullanın:
        - **Arama**: ![Başlığa Göre Ara simgesi.](../../media/m365-cc-sc-search-icon.png) **Başlığa göre arama** yapın, Başlık değerinin bir kısmını yazıp Enter tuşuna basabilirsiniz. Sonuçların bir kısmını veya tümünü seçebilirsiniz.
        - **Tüm Başlığı** Seç
        - Mevcut Başlık değerlerini seçin.

      :::image type="content" source="../../media/attack-sim-training-simulations-target-users-filter-by-category.png" alt-text="Microsoft 365 Defender portalındaki Saldırı simülasyonu eğitimi sayfasındaki Hedef kullanıcılar sayfasında Kullanıcı filtrelemesi" lightbox="../../media/attack-sim-training-simulations-target-users-filter-by-category.png":::

      Ölçütlerinizi belirledikten sonra, etkilenen kullanıcılar görüntülenen **Kullanıcı listesi** bölümünde gösterilir ve burada bulunan alıcılardan bazılarını veya tümünü seçebilirsiniz.

      İşiniz bittiğinde **Uygula(x)**'e ve ardından **X kullanıcı ekle'ye** tıklayın.

  **Ana Hedef kullanıcılar** sayfasına döndüğünüzde ![Ara simgesini kullanabilirsiniz.](../../media/m365-cc-sc-search-icon.png) Etkilenen kullanıcıları bulmak için **arama** kutusu. Kullanıcıları sil simgesine de tıklayabilirsiniz ![.](../../media/m365-cc-sc-search-icon.png) Belirli kullanıcıları kaldırmak için **silin**.

- ![İçeri aktar simgesi.](../../media/m365-cc-sc-create-icon.png) **İçeri Aktarma**: Açılan iletişim kutusunda, satır başına bir e-posta adresi içeren bir CSV dosyası belirtin.

  CSV dosyasını seçtikten sonra, kullanıcı listesi içeri aktarılır ve **Hedeflenen kullanıcılar** sayfasında gösterilir. Arama simgesini kullanabilirsiniz ![.](../../media/m365-cc-sc-search-icon.png) Etkilenen kullanıcıları bulmak için **arama** kutusu. Hedeflenen kullanıcıları sil simgesine de tıklayabilirsiniz ![.](../../media/m365-cc-sc-delete-icon.png) Belirli kullanıcıları kaldırmak için **silin**.

İşiniz bittiğinde **İleri'ye** tıklayın.

## <a name="assign-training"></a>Eğitim atama

**Eğitim ata** sayfasında simülasyon için eğitimler atayabilirsiniz. Eğitimden geçen çalışanlar benzer saldırılara daha az duyarlı olduğundan her simülasyon için eğitim atamanızı öneririz. Aşağıdaki ayarlar kullanılabilir:

- **Eğitim içeriği tercihini seçin**: Aşağıdaki seçeneklerden birini belirleyin:
  - **Microsoft eğitim deneyimi**: Bu, yapılandırmak için aşağıdaki ilişkili seçenekleri içeren varsayılan değerdir:
    - Aşağıdaki seçeneklerden birini belirleyin:
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

Listedeki her eğitim için **, Ata** sütunundaki değerleri seçerek eğitimi kimlerin aldığını seçmeniz gerekir:

- **Tüm kullanıcılar**

  veya aşağıdaki değerlerden biri veya her ikisi:

- **Tıklanan yük**
- **Tehlikeye**

Gösterilen bir eğitimi kullanmak istemiyorsanız Eğitimi sil simgesine tıklayın ![.](../../media/m365-cc-sc-delete-icon.png) **Sil'i seçin**.

:::image type="content" source="../../media/attack-sim-training-training-assignment.png" alt-text="Microsoft 365 Defender portalındaki Saldırı simülasyonu eğitimi'ndeki Eğitim atama sayfası" lightbox="../../media/attack-sim-training-training-assignment.png":::

İşiniz bittiğinde **İleri'ye** tıklayın.

### <a name="landing-page"></a>Giriş sayfası

**Giriş sayfası sayfasında**, simülasyonda yükü açan kullanıcının alındığı web sayfasını yapılandırabilirsiniz.

Microsoft tarafından seçilmiş giriş sayfaları 12 dilde kullanılabilir: Çince (Basitleştirilmiş), Çince (Geleneksel), İngilizce, Fransızca, Almanca, İtalyanca, Japonca, Korece, Portekizce, Rusça, İspanyolca ve Felemenkçe.

- **Giriş sayfası tercihini seçin**: Kullanılabilir değerler şunlardır:
  - **Microsoft varsayılan giriş sayfasını kullan**: Bu, yapılandırmak için aşağıdaki ilişkili seçenekleri içeren varsayılan değerdir:
    - **Giriş sayfası düzenini seçin**: Kullanılabilir şablonlardan birini seçin.
    - **Logo ekle**: .png, .jpeg veya .gif dosyasını bulmak ve seçmek için **Gözat'a** tıklayın. Bozulmayı önlemek için logo boyutu en fazla 210 x 70 olmalıdır. Logoyu kaldırmak için **Kaldır'a** tıklayın.
    - **E-postaya yük göstergeleri ekleme**: Daha önce [Tekniği seç](#select-a-social-engineering-technique) sayfasında **Kötü amaçlı yazılım eki** veya **Kötü amaçlı yazılım bağlantısı'nı** seçtiyseniz bu ayar kullanılamaz.

    Sayfanın alt kısmındaki **Önizleme panelini aç** düğmesine tıklayarak sonuçların önizlemesini görüntüleyebilirsiniz.

  - **Özel URL kullanın**: Daha önce [Teknik seç](#select-a-social-engineering-technique) sayfasında **Kötü amaçlı yazılım eki** veya **Kötü amaçlı yazılım bağlantısı'nı** seçtiyseniz bu ayar kullanılamaz.

    **Özel URL kullan'ı** seçerseniz, görüntülenen **Özel giriş sayfası URL'sini girin** kutusuna URL'yi eklemeniz gerekir. Sayfada başka seçenek yoktur.

  - **Kendi giriş sayfanızı oluşturun**: Bu değer, yapılandırmak için aşağıdaki ilişkili seçeneklere sahiptir:
    - **E-postaya yük göstergeleri ekleme**: Bu ayar yalnızca aşağıdaki koşulların her ikisi de doğruysa seçilebilir:
      - Daha önce [Tekniği seç](#select-a-social-engineering-technique) sayfasında **Kimlik bilgisi toplama**, **Ekteki bağlantı** veya **SürücüYE göre URL'yi** seçtiniz.
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
        - **Varsayılandan kullanın**: Başlamak için kullanılabilir bir şablon seçin. Düzenleme alanındaki metni ve düzeni değiştirebilirsiniz. Giriş sayfasını şablonun varsayılan metnine ve düzenine geri döndürmek **için Varsayılana sıfırla'ya** tıklayın.
    - **Kod**: HTML kodunu doğrudan görüntüleyebilir ve değiştirebilirsiniz.

    Sayfanın ortasındaki **Önizleme panelini aç** düğmesine tıklayarak sonuçların önizlemesini görüntüleyebilirsiniz.

İşiniz bittiğinde **İleri'ye** tıklayın.

> [!NOTE]
> Bazı ticari markalar, logolar, simgeler, insignias ve diğer kaynak tanımlayıcıları, yerel, eyalet ve federal tüzükler ve yasalar kapsamında yüksek koruma alır. Bu tür göstergelerin yetkisiz kullanımı, kullanıcıları cezai para cezaları da dahil olmak üzere cezalara tabi yapabilir. Kapsamlı bir liste olmasa da, buna Başkanlık, Başkan Yardımcısı ve Kongre mühürleri, CIA, FBI, Sosyal Güvenlik, Medicare ve Medicaid, Birleşik Devletler İç Gelir Servisi ve Olimpiyatlar dahildir. Bu ticari marka kategorilerinin ötesinde, herhangi bir üçüncü taraf ticari markanın kullanılması ve değiştirilmesi doğal bir risk taşır. Yükte kendi ticari markalarınızı ve logolarınızı kullanmak, özellikle de kuruluşunuzun kullanıma izin vermesinde daha az riskli olabilir. Yük oluştururken veya yapılandırırken nelerin kullanılması uygun veya uygun olmadığı hakkında başka sorularınız varsa, hukuk danışmanlarınıza danışmanız gerekir.

## <a name="select-end-user-notification"></a>Son kullanıcı bildirimini seçme

**Son kullanıcı bildirimini seçin** sayfasında aşağıdaki bildirim seçeneklerinden birini belirleyin:

- **Bildirimleri teslim etme**: Görüntülenen uyarı iletişim kutusunda **Devam'a** tıklayın. Bu seçeneği seçerseniz **İleri'ye** tıkladığınızda [Başlatma ayrıntıları](#launch-details) sayfasına yönlendirilirsiniz.

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
      - **Önizleme** sekmesi: Bildirim iletisini görüntüleyin.
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

  **İleri'ye** tıkladığınızda [Başlatma ayrıntıları](#launch-details) sayfasına yönlendirilirsiniz.

- **Özelleştirilmiş son kullanıcı bildirimleri**: **İleri'ye** tıkladığınızda, sonraki bölümlerde açıklandığı gibi **Eğitim ataması bildirim** sayfasına yönlendirilirsiniz.

### <a name="training-assignment-notification"></a>Eğitim ataması bildirimi

**Eğitim ataması bildirim** sayfası yalnızca **[Son](#select-end-user-notification)** **kullanıcı bildirimini seçin sayfasında Özelleştirilmiş son kullanıcı bildirimleri'ni** seçtiğinizde kullanılabilir.

Bu sayfada aşağıdaki bildirimler ve yapılandırılan dilleri gösterilir:

- **Microsoft varsayılan eğitim ataması bildirimi**
- Daha önce oluşturduğunuz tüm özel eğitim atama bildirimleri.

  Bu bildirimler, konumundaki Saldırı benzetimi eğitimi'nin <https://security.microsoft.com/attacksimulator?viewid=endUserNotification>**Son kullanıcı bildirimleri** sekmesinde de kullanılabilir. **Microsoft varsayılan eğitim ataması bildirimi** Genel **bildirimler** sekmesinde bulunur. Özel eğitim ataması bildirimleri **Kiracı bildirimleri** sekmesinde bulunur. Daha fazla bilgi için bkz [. Saldırı benzetimi eğitimi için son kullanıcı bildirimleri](attack-simulation-training-end-user-notifications.md).

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

    Bu bildirimler, konumundaki Saldırı benzetimi eğitimi'nin <https://security.microsoft.com/attacksimulator?viewid=endUserNotification>**Son kullanıcı bildirimleri** sekmesinde de kullanılabilir. **Microsoft varsayılan eğitim anımsatıcı bildirimi** Genel **bildirimler** sekmesinde bulunur. Özel eğitim anımsatıcısı bildirimleri **Kiracı bildirimleri** sekmesinde bulunur. Daha fazla bilgi için bkz [. Saldırı benzetimi eğitimi için son kullanıcı bildirimleri](attack-simulation-training-end-user-notifications.md).

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

  - **Teslim etme**: Bu seçeneği seçerseniz **, İleri'ye** tıkladığınızda [Başlatma ayrıntıları](#launch-details) sayfasına yönlendirilirsiniz.

  - **Kullanıcı kimlik avı ve kampanya sona erdikten** sonra **teslim etme veya Kullanıcı kimlik avı bildirdikten hemen sonra teslim etme**: Bu bölümlerde, görüntülenen **Pozitif bir pekiştirme bildirimi seçin** bölümünde aşağıdaki bildirimler ve yapılandırılan dilleri gösterilir:

  - **Microsoft varsayılan pozitif takviye bildirimi**
  - Daha önce oluşturduğunuz tüm özel pozitif takviye bildirimleri.

    Bu bildirimler, konumundaki Saldırı benzetimi eğitimi'nin <https://security.microsoft.com/attacksimulator?viewid=endUserNotification>**Son kullanıcı bildirimleri** sekmesinde de kullanılabilir. **Microsoft varsayılan pozitif takviye bildirimi** Genel **bildirimler** sekmesinde bulunur. Kiracı bildirimleri sekmesinde özel pozitif takviye **bildirimleri** bulunur. Daha fazla bilgi için bkz [. Saldırı benzetimi eğitimi için son kullanıcı bildirimleri](attack-simulation-training-end-user-notifications.md).

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

## <a name="launch-details"></a>Başlatma ayrıntıları

**Başlatma ayrıntıları** sayfasında simülasyonu ne zaman başlatabileceğinizi ve simülasyonu ne zaman sonlandırabileceğinizi seçersiniz. Belirttiğiniz bitiş tarihinden sonra bu simülasyonla etkileşimi yakalamayı durduracağız.

Aşağıdaki ayarlar kullanılabilir:

- Aşağıdaki değerlerden birini seçin:
  - **bitirdiğim anda bu simülasyonu başlat**
  - **Bu simülasyonu daha sonra başlatılacak şekilde zamanlayın**: Bu değer, yapılandırmak için aşağıdaki ilişkili seçeneklere sahiptir:
    - **Başlatma tarihini seçin**
    - **Başlatma zamanını seçin**
- **Benzetimi sona erdirecek gün sayısını yapılandırın**: Varsayılan değer 2'dir.
- **Bölge algılamalı saat dilimi teslimini etkinleştirme**: Çalışanlarınıza bölgelerine göre çalışma saatleri içinde sanal saldırı iletileri iletin.
- **Toplanan sürücüye göre teknik ara verileri görüntüleme sayfası**: Sürücü veri yolu URL'si tekniği saldırıları için ortaya çıkan katmanı gösterebilirsiniz. Yer paylaşımını gizlemek ve doğrudan giriş sayfasına gitmek için bu seçeneği kaldırın.

İşiniz bittiğinde **İleri'ye** tıklayın.

## <a name="review-simulation"></a>Benzetimi gözden geçirme

**Simülasyonu gözden geçir** sayfasında simülasyonunuzun ayrıntılarını gözden geçirebilirsiniz.

![Test gönder simgesine tıklayın.](../../media/m365-cc-sc-send-icon.png) Yük e-postasının bir kopyasını inceleme için kendinize (şu anda oturum açmış olan kullanıcı) göndermek için **bir test düğmesi gönderin**.

Bölümün içindeki ayarları değiştirmek için her bölümde **Düzenle'yi** seçebilirsiniz. Ya da **Geri'ye** tıklayabilir veya sihirbazdaki belirli bir sayfayı seçebilirsiniz.

İşiniz bittiğinde **Gönder'e** tıklayın.

:::image type="content" source="../../media/attack-sim-training-simulations-review-simulation.png" alt-text="Microsoft 365 Defender portalındaki Saldırı simülasyonu eğitiminin Simülasyonu gözden geçirme sayfası" lightbox="../../media/attack-sim-training-simulations-review-simulation.png":::
