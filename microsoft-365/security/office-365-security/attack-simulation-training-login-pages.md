---
title: Saldırı simülasyonu eğitimindeki oturum açma sayfaları
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
description: Yöneticiler, Office 365 için Microsoft Defender Plan 2'de kimlik avı saldırıları simülasyonu için oturum açma sayfaları oluşturmayı ve yönetmeyi öğrenebilir.
ms.technology: mdo
ms.openlocfilehash: 7057f443675cb0715a41f78c80feb69cdc75d22c
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66640312"
---
# <a name="login-pages-in-attack-simulation-training"></a>Saldırı simülasyonu eğitimindeki oturum açma sayfaları

[Office 365 için Microsoft Defender plan 2](defender-for-office-365.md) **için geçerlidir**

Microsoft 365 E5 veya Office 365 için Microsoft Defender Plan 2'de saldırı simülasyonu eğitimi bölümünde oturum açma sayfaları, ek [sosyal mühendislik tekniklerinde](attack-simulation-training.md#select-a-social-engineering-technique) **Kimlik Bilgisi toplama** ve **Bağlama kullanan simülasyonlarda** kullanıcılara görüntülenir.

Kullanılabilir oturum açma sayfalarını görmek için adresinden Microsoft 365 Defender portalını <https://security.microsoft.com>açın **, e-posta & işbirliği** \> **Saldırı simülasyonu eğitimi** \> **Simülasyon içerik kitaplığı** sekmesine \> gidin ve **oturum açma sayfaları'nı** seçin. **Oturum açma sayfaları'nı** seçebileceğiniz **Simülasyon içerik kitaplığı** sekmesine doğrudan gitmek için kullanın<https://security.microsoft.com/attacksimulator?viewid=simulationcontentlibrary>.

**Oturum açma sayfalarında** iki sekme vardır:

- **Genel oturum açma sayfaları**: Yerleşik, değiştirilemeyen oturum açma sayfalarını içerir. 12'nin üzerine dilde yerelleştirilmiş dört yerleşik oturum açma sayfası vardır:
  - **GitHub oturum açma sayfası**
  - **LinkedIn oturum açma sayfası**
  - **Microsoft oturum açma sayfası**
  - **Markalı olmayan oturum açma sayfası**

- **Kiracı oturum açma sayfaları**: Oluşturduğunuz özel oturum açma sayfalarını içerir.

Her oturum açma sayfası için aşağıdaki bilgiler gösterilir:

- **Ad**
- **Dil**
- **Kaynak**: Yerleşik oturum açma sayfaları için değer **Genel'dir**. Özel oturum açma sayfaları için değer **Kiracı'dır**.
- **Durum**: **Hazır** veya **Taslak**.
- **Oluşturan**: Yerleşik oturum açma sayfaları için değer **Microsoft'tur**. Özel oturum açma sayfaları için değer, oturum açma sayfasını oluşturan kullanıcının UPN değeridir.
- **Son değiştirme**

Listede oturum açma sayfası bulmak için Ara simgesini kullanın ![.](../../media/m365-cc-sc-search-icon.png) Oturum açma sayfasının adını bulmak için **arama** kutusu.

Filtre simgesine tıklayın ![.](../../media/m365-cc-sc-filter-icon.png) Oturum açma sayfalarını **Dile** veya Duruma göre filtrelemek için **filtreleyin**.

Görüntülenen bir veya daha fazla sütunu kaldırmak için Sütunları özelleştir simgesine tıklayın ![.](../../media/m365-cc-sc-customize-icon.png) **Sütunları özelleştirin**.

Listeden bir oturum açma sayfası seçtiğinizde, aşağıdaki bilgilerle birlikte bir ayrıntılar açılır öğesi görüntülenir:

- ![Düzenle simgesi.](../../media/m365-cc-sc-edit-icon.png) **Düzenleme** yalnızca **Kiracı oturum açma sayfaları sekmesindeki özel oturum açma sayfalarında** kullanılabilir.
- ![Varsayılan simge olarak işaretle.](../../media/m365-cc-sc-set-as-default-icon.png) Bu oturum açma sayfasını **Kimlik bilgisi toplama** veya Ek [yüklerinde](attack-simulation-training-payloads.md) veya [yük otomasyonlarında](attack-simulation-training-payload-automations.md) **bağla'da** varsayılan seçim yapmak için **varsayılan olarak işaretleyin**. Oturum açma sayfası zaten varsayılansa, ![Varsayılan olarak işaretle simgesi.](../../media/m365-cc-sc-set-as-default-icon.png) **Varsayılan olarak işaretle** seçeneği kullanılamaz.
- **Önizleme** sekmesi: Kullanıcıların göreceği oturum açma sayfasını görüntüleyin. **Sayfa 1** ve **Sayfa 2** bağlantıları, iki sayfalı oturum açma sayfaları için sayfanın alt kısmında yer alır.
- **Ayrıntılar** sekmesi: Oturum açma sayfasıyla ilgili ayrıntıları görüntüleyin:
  - **Açıklama**
  - **Durum**: **Hazır** veya **Taslak**.
  - **Oturum açma sayfası kaynağı**: Yerleşik oturum açma sayfaları için değer **Genel'dir**. Özel oturum açma sayfaları için değer **Kiracı'dır**.
  - **Değiştiren**
  - **Dil**
  - **Son değiştirme**

## <a name="create-login-pages"></a>Oturum açma sayfaları oluşturma

1. konumundaki Microsoft 365 Defender portalında<https://security.microsoft.com>**, E-posta & işbirliği** \> **Saldırı benzetimi eğitimi** \> **Benzetimi içerik kitaplığı** sekmesine \> gidin ve **oturum açma sayfaları'nı** seçin. **Oturum açma sayfaları'nı** seçebileceğiniz **Simülasyon içerik kitaplığı** sekmesine doğrudan gitmek için kullanın<https://security.microsoft.com/attacksimulator?viewid=simulationcontentlibrary>.
Aşağıdaki konumlarda özel oturum açma sayfaları oluşturabilirsiniz:

   Yeni oluştur simgesine tıklayın ![.](../../media/m365-cc-sc-create-icon.png) Son kullanıcı oturum açma sayfası oluşturma sihirbazını başlatmak için **yeni oluşturun**.

   > [!NOTE]
   > ![Yeni simge oluştur'u seçin.](../../media/m365-cc-sc-create-icon.png) **Yeni oluştur** , simülasyon veya simülasyon otomasyonu oluşturmanın yük seçimi adımında da kullanılabilir. Daha fazla bilgi için bkz [. Simülasyon oluşturma: Yük ve oturum açma sayfası seçme ve](attack-simulation-training.md#select-a-payload-and-login-page) [Simülasyon otomasyonu oluşturma: Yük ve oturum açma sayfası seçme](attack-simulation-training-simulation-automations.md#select-a-payload-and-login-page).
   >
   > Oluşturma sihirbazı sırasında herhangi bir noktada Kaydet **ve kapat'a** tıklayarak ilerlemenizi kaydedebilir ve oturum açma sayfasını daha sonra yapılandırmaya devam edebilirsiniz. **Oturum** açma **sayfalarında Kiracı oturum açma sayfaları** sekmesinde oturum açma sayfasını seçip Düzenle simgesine tıklayarak ![kaldığınız yerden devam edebilirsiniz.](../../media/m365-cc-sc-edit-icon.png) **Düzenle'yi seçin**. Kısmen tamamlanmış oturum açma sayfasında **Durum** değeri **Taslak** olacaktır.

2. **Oturum açma ayrıntılarını tanımla sayfasında** aşağıdaki ayarları yapılandırın:
   - **Ad**: Benzersiz bir ad girin.
   - **Açıklama**: İsteğe bağlı bir açıklama girin.

   İşiniz bittiğinde **İleri'ye** tıklayın.

3. **Oturum açmayı yapılandır sayfasında** aşağıdaki ayarları yapılandırın:

   - **Bir dil seçin**: Kullanılabilir değerler şunlardır: **Çince (Basitleştirilmiş)**, **Çince (Geleneksel)**, **İngilizce**, **Fransızca**, **Almanca**, **İtalyanca**, **Japonca**, **Korece**, **Portekizce**, **Rusça**, **İspanyolca** ve **Felemenkçe**.

   - **Bunu varsayılan oturum açma sayfası yap**: Bu seçeneği belirlerseniz, oturum açma sayfası **Kimlik bilgisi toplama** veya Ek [yüklerinde](attack-simulation-training-payloads.md) veya [yük otomasyonlarında](attack-simulation-training-payload-automations.md) **bağlantı sağlama'da** varsayılan seçim olacaktır.

   - **İki sayfalı oturum açma oluşturma**: Bu seçeneği belirlemezseniz, oturum açma sayfası bir sayfadır. Bu seçeneği seçerseniz, ayrı ayrı yapılandırmanız için **Sayfa 1** ve **Sayfa 2** sekmeleri görüntülenir.

     - **Metin** sekmesinde, oturum açma sayfanızı oluşturmanız için zengin bir metin düzenleyicisi sağlanır.

       - Kullanılabilir etiketleri ekleyerek oturum açma sayfasını özelleştirmek için **Dinamik etiket** denetimini kullanın:
         - **Kullanıcı adı ekle**: İleti gövdesine eklenen değerdir `${userName}`.
         - **E-posta ekle**: İleti gövdesine eklenen değer olur `${emailAddress}`.
         - **Ekleme tarihi**: İleti gövdesine eklenen değer olur `${date|MM/dd/yyyy|offset}`.

       - Şablon olarak başlamak üzere yerleşik bir oturum açma sayfası seçmek için **Varsayılandan kullan** denetimini kullanın.

       - **İleri Ekle düğme** denetimi yalnızca iki sayfalı oturum açma bilgilerinin **1. sayfasında** kullanılabilir. Düğmedeki varsayılan metin **İleri'dir** , ancak değiştirebilirsiniz.

       - Tek sayfalı oturum açmalarda veya iki sayfalı oturum açma bilgilerinin 2. **sayfasında** bulunan **Risk ekle düğmesi** denetimi. Düğmedeki varsayılan metin **Gönder'dir**, ancak bunu değiştirebilirsiniz.

     - **Kod** sekmesinde HTML kodunu doğrudan görüntüleyebilir ve değiştirebilirsiniz. **Dinamik etiket** ve **Varsayılandan kullan** veya **Risk ekle düğmesi** gibi biçimlendirme ve diğer denetimler kullanılamaz.

   - Oturum açma sayfasını gözden geçirmek için sayfanın üst kısmındaki Oturum **açma sayfasını önizle** düğmesini kullanın.

   İşiniz bittiğinde **İleri'ye** tıklayın.

4. **Oturum açma sayfasını gözden geçir sayfasında** oturum açma sayfanızın ayrıntılarını gözden geçirebilirsiniz.

   Bölümün içindeki ayarları değiştirmek için her bölümde **Düzenle'yi** seçebilirsiniz. Ya da **Geri'ye** tıklayabilir veya sihirbazdaki belirli bir sayfayı seçebilirsiniz.

   İşiniz bittiğinde **Gönder'e** tıklayın.

5. **Yeni oturum açma sayfası oluşturuldu sayfasında\<Name\>**, bağlantıları kullanarak yeni bir oturum açma sayfası oluşturabilir, simülasyon başlatabilir veya tüm oturum açma sayfalarını görüntüleyebilirsiniz.

   İşiniz bittiğinde **Bitti'ye** tıklayın.

**Oturum** **açma sayfalarında Kiracı oturum açma sayfaları** sekmesine döndüğünüzde, oluşturduğunuz oturum açma sayfası artık listeleniyor.

## <a name="modify-login-pages"></a>Oturum açma sayfalarını değiştirme

Genel oturum açma sayfaları sekmesinde yerleşik **oturum açma sayfalarını** değiştiremezsiniz. Özel oturum açma sayfalarını yalnızca **Kiracı oturum açma sayfaları** sekmesinde değiştirebilirsiniz.

**Kiracı oturum açma sayfaları** sekmesindeki mevcut bir özel oturum açma sayfasını değiştirmek için aşağıdaki adımlardan birini yapın:

- Onay kutusuna tıklayarak listeden oturum açma sayfasını seçin. Düzenle simgesine ![tıklayın.](../../media/m365-cc-sc-edit-icon.png) Görüntülenen **Düzenle** simgesi.
- Listedeki oturum açma sayfasının **Ad** ve **Dil** değerleri arasında **⋮** (**Eylemler**) öğesine tıklayın ve ardından Düzenle simgesi'ni seçin![.](../../media/m365-cc-sc-edit-icon.png) **Düzenle'yi seçin**.
- Ada tıklayarak listeden oturum açma sayfasını seçin. Açılan ayrıntılar açılır listesinde Düzenle simgesine tıklayın ![.](../../media/m365-cc-sc-edit-icon.png) **Düzenle'yi seçin**.

Oturum açma sayfası sihirbazı, seçili oturum açma sayfasının ayarları ve değerleriyle birlikte açılır. Adımlar [, Oturum açma sayfaları oluşturma](#create-login-pages) bölümünde açıklanan adımlarla aynıdır.

## <a name="copy-login-pages"></a>Oturum açma sayfalarını kopyalama

**Kiracı oturum açma sayfaları veya Genel oturum açma sayfaları** sekmelerindeki mevcut oturum **açma** sayfasını kopyalamak için aşağıdaki adımlardan birini yapın:

- Onay kutusuna tıklayarak listeden oturum açma sayfasını seçin ve ardından Kopya oluştur simgesine ![tıklayın.](../../media/m365-cc-sc-edit-icon.png) Görüntülenen **bir kopyalama simgesi oluşturun**.
- Listedeki oturum açma sayfasının **Ad** ve **Dil** değerleri arasında **⋮** (**Eylemler**) öğesine tıklayın ve ardından Kopya oluştur simgesi'ni seçin![.](../../media/m365-cc-sc-edit-icon.png) **Bir kopya oluşturun**.

Oturum açma sayfası sihirbazı, seçili oturum açma sayfasının ayarları ve değerleriyle birlikte açılır. Adımlar [, Oturum açma sayfaları oluşturma](#create-login-pages) bölümünde açıklanan adımlarla aynıdır.

> [!NOTE]
> Genel oturum açma **sayfaları** sekmesindeki yerleşik oturum açma sayfasını kopyaladığınızda **Ad** değerini değiştirdiğinizden emin olun. Bu adım, kopyanın **Kiracı oturum açma sayfaları** sekmesinde özel oturum açma sayfası olarak kaydedilmesini sağlar.
>
> Oturum **açma sayfası sihirbazındaki Oturum açmayı yapılandır sayfasındaki** **Varsayılan denetimden kullan** denetimi, yerleşik oturum açma sayfasının içeriğini kopyalamanıza olanak tanır.

## <a name="remove-login-pages"></a>Oturum açma sayfalarını kaldırma

Genel oturum açma sayfaları sekmesinden yerleşik **oturum açma sayfalarını** kaldıramazsınız. Yalnızca Kiracı oturum açma sayfaları sekmesindeki özel **oturum açma sayfalarını** kaldırabilirsiniz.

**Kiracı oturum açma sayfaları** sekmesinden var olan bir özel oturum açma sayfasını kaldırmak için aşağıdaki adımlardan birini yapın:

- Onay kutusuna tıklayarak listeden oturum açma sayfasını seçin ve ardından Sil simgesine ![tıklayın.](../../media/m365-cc-sc-delete-icon.png) Görüntülenen **Sil** simgesi.
- Listedeki oturum açma sayfasının **Ad** ve **Dil** değerleri arasında **⋮** (**Eylemler**) öğesine tıklayın ve ardından Sil simgesi'ni seçin![.](../../media/m365-cc-sc-delete-icon.png) **Sil'i seçin**.

## <a name="make-a-login-page-the-default"></a>Oturum açma sayfasını varsayılan yapma

Varsayılan oturum açma sayfası, **Kimlik bilgisi toplama** veya Ek [yüklerinde](attack-simulation-training-payloads.md) veya yük **otomasyonlarında bağlantıda** kullanılan varsayılan [seçimdir](attack-simulation-training-payload-automations.md).

**Kiracı oturum açma sayfaları veya Genel oturum açma sayfaları** sekmelerinde oturum **açma** sayfasını varsayılan olarak ayarlamak için aşağıdaki adımlardan birini yapın:

- Onay kutusuna tıklayarak listeden oturum açma sayfasını seçin. Varsayılan olarak işaretle ![simgesine tıklayın.](../../media/m365-cc-sc-set-as-default-icon.png) Görüntülenen **varsayılan simge olarak işaretle**.
- Listedeki oturum açma sayfasının **Ad** ve **Dil** değerleri arasında **⋮** (**Eylemler**) öğesine tıklayın ve ardından Varsayılan simge olarak işaretle'yi seçin![.](../../media/m365-cc-sc-set-as-default-icon.png) **Varsayılan olarak işaretleyin**.
- Ada tıklayarak listeden oturum açma sayfasını seçin. Açılan ayrıntılar açılır listesinde Varsayılan olarak işaretle simgesine tıklayın ![.](../../media/m365-cc-sc-set-as-default-icon.png) **Varsayılan olarak işaretleyin**.
- Oturum **açma sayfası** [oluştururken veya değiştirirken](#create-login-pages) sihirbazdaki **Oturum açmayı yapılandır sayfasında** Bunu varsayılan oturum açma sayfası yap'ı seçin.

> [!NOTE]
> Oturum açma sayfası zaten varsayılansa, önceki yordamlar kullanılamaz.
>
> Varsayılan oturum açma sayfası da listede işaretlenir, ancak bunu görmek için **Ad** sütununu genişletmeniz gerekebilir:
>
> ![Saldırı benzetimi eğitimindeki oturum açma sayfaları listesinde işaretlenmiş varsayılan oturum açma sayfası.](../../media/attack-sim-training-login-pages-default.png)

## <a name="related-links"></a>İlgili bağlantılar

[Saldırı simülasyonu eğitimini kullanmaya başlama](attack-simulation-training-get-started.md)

[Kimlik avı saldırısı simülasyonu oluşturma](attack-simulation-training.md)

[Saldırı simülasyonu eğitimi için simülasyon otomasyonları](attack-simulation-training-simulation-automations.md)
