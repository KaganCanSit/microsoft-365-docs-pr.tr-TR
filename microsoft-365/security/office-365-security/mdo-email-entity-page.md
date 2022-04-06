---
title: Office 365 için Microsoft Defender-posta varlık sayfası
f1.keywords:
- NOCSH
ms.author: tracyp
author: msfttracyp
manager: dansimp
ms.date: 04/01/2022
audience: ITPro
ms.topic: article
ms.prod: m365-security
ms.technology: mdo
ms.localizationpriority: medium
search.appverid: ''
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
ms.custom: ''
description: Office 365 için Microsoft Defender E5, P1 ve P2 müşterileri artık e-posta varlık sayfasıyla her e-postayı 360 derecelik bir görünüme sahip olacak.
ms.openlocfilehash: 1b74c4c79d05a4a52434810527c92de801b329f0
ms.sourcegitcommit: adea59259a5900cad5de29ddf46d1ca9e9e1c82f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/04/2022
ms.locfileid: "64634833"
---
# <a name="the-email-entity-page"></a>E-posta varlık sayfası

**Bu makalede:**
- [E-posta varlık sayfasına ulaşma](#reach-the-email-entity-page)
- [E-posta varlık sayfasını okuma](#read-the-email-entity-page)
- [E-posta varlık sayfası sekmelerini kullanma](#use-email-entity-page-tabs)
- [E-posta varlık sayfasında yenisiniz](#new-to-the-email-entity-page)

Office 365 için Microsoft Defender E5, Office P1 ve P2 için Defender yöneticileri E-posta varlık sayfasını kullanarak e-postanın 360 derecelik **görünümünü alır**. Threat Explorer 'e-posta ayrıntıları' sayfasında teslim edilen bilgileri geliştirmek [için bu git e-posta sayfası oluşturulmuştur](threat-explorer-views.md).

## <a name="reach-the-email-entity-page"></a>E-posta varlık sayfasına ulaşma

E-posta varlık sayfası, Microsoft 365 Defender portalında E-posta ve <https://security.microsoft.com> **&** \> **vardır**. Doğrudan Gezgin sayfasına gitmek **için de** bunu kullanın <https://security.microsoft.com/threatexplorer>.

**Gezgin'de**, araştıran bir e-postanın konusunu seçin. Bu posta için dışarı uçan e-postanın üst kısmında altın gibi bir çubuk görüntülenir. Yeni sayfaya davet "Yeni e-posta varlık sayfamızı zenginleştirilmiş verilerle deneyin..." makalesini okur. Yeni sayfayı görüntülemek için öğesini seçin.

:::image type="content" source="../../media/email-entities-1-navigation-to-ee.png" alt-text="Yeni deneyime gitmek için *Zenginleştirilmiş veriler içeren yeni e-posta varlık sayfamızı deneyin* sözcüklerinin yer alan altın başlık" lightbox="../../media/email-entities-1-navigation-to-ee.png":::

:::image type="content" source="../../media/email-entities-2-eep.png" alt-text="Göreceğiniz başlıklara odaklanan e-posta varlık sayfasının grafiği" lightbox="../../media/email-entities-2-eep.png":::

> [!NOTE]
> Bu sayfayı görüntülemek ve kullanmak için gereken izinler, Explorer'ı görüntülemekle **aynıdır**. Yönetici, Genel yönetici veya genel okuyucu ya da Güvenlik yöneticisi veya Güvenlik Okuyucusu üyesi olabilir. Daha fazla bilgi için bkz[. Microsoft 365 Defender portalına.](permissions-microsoft-365-security-center.md)

## <a name="read-the-email-entity-page"></a>E-posta varlık sayfasını okuma

Yapı, kolayca okunması ve bir bakışta gezinmesi için tasarlanmıştır. Sayfanın üst kısmında yer alan çeşitli sekmeler daha ayrıntılı incelemeniz için olanak sağlar. Düzen şöyle çalışır:

1. En gerekli alanlar, uçarak çıkar'ın sol tarafındadır. Bu ayrıntılar 'yapışkan'tır; yani, uçarak girişin geri kalanında gezinmek istediğiniz sekmeden fark etmez; sola sabitleniyorlar.

    :::image type="content" source="../../media/email-entities-3-left-panel.png" alt-text="Sol tarafı vurgulanmış olarak e-posta varlık sayfasının grafiği" lightbox="../../media/email-entities-3-left-panel.png":::

2. Sağ üst köşede, bir e-posta üzerinde  gerçekleştirebilirsiniz. Gezgin aracılığıyla yapılabilecek tüm eylemler, **e-posta** varlık sayfası aracılığıyla da kullanılabilir.

    :::image type="content" source="../../media/email-entities-5-preview.png" alt-text="Sağ tarafı vurgulanmış olarak e-posta varlık sayfasının grafiği" lightbox="../../media/email-entities-5-preview.png":::

3. Daha derin çözümleme, sayfanın geri kalanından sıralama yoluyla yapılabilir. E-posta algılama ayrıntılarını, e-posta kimlik doğrulama durumunu ve üst bilgileri kontrol edin. Bu alan büyük/küçük harfe göre kontrol edilir, ancak bu sekmelerde yer alan bilgiler tüm e-postalarda kullanılabilir.

    :::image type="content" source="../../media/email-entities-4-middle-panel.png" alt-text="Sayfanın e-posta üst bilgilerini ve kimlik doğrulama durumunu içeren ana panel" lightbox="../../media/email-entities-4-middle-panel.png":::

### <a name="use-email-entity-page-tabs"></a>E-posta varlık sayfası sekmelerini kullanma

Varlık sayfasının üst kısmında yer alan sekmeler, e-postaları verimli bir şekilde incelemenizi sağlar.

1. **Zaman** Çizelgesi: Bir e-postanın zaman çizelgesi görünümü ( **Explorer** zaman çizelgesi başına), bir e-postada gerçekleşecek teslim sonrası olaylarda özgün teslimi gösterir. Teslim sonrası eylemleri olmayan e-postalar için görünüm, özgün teslim satırı zaman çizelgesi görünümünde gösterir. Örneğin: Sıfır saatlik otomatik temizleme (ZAP), Düzeltme, URL tıklamaları ve başka kaynaklara benzer kaynaklardan :system, admin ve user, show up here in the order in they occurred.
2. **Çözümleme**: Çözümleme, yöneticilerin bir e-postayı derinlemesine çözümlemelerine yardımcı olan alanları gösterir. Yöneticilerin algılama, gönderen /alıcı ve e-posta kimlik doğrulaması ayrıntıları hakkında daha fazla bilgi edin incelemesi gereken durumlarda Çözümleme sekmesini kullanmaları gerekir. Ekler ve URL'lerin bağlantıları bu sayfada, 'İlgili Varlıklar' altında da bulunur. Hem ekler hem de tanımlanan tehditler burada numaralandı ve tıklatmak sizi doğrudan Ekler ve URL sayfalarına götürmenizi sağlar. Bu sekmede e-posta üst bilgilerini görüntülemek için *Üstbilgiyi görüntüle seçeneği de vardır*. Yöneticiler, netlik sağlamak için e-posta üst bilgilerinden herhangi bir ayrıntıyı ana panelde yer alan bilgilerle yan yana karşılaştırabilir.
3. **Ekler**: Bu, e-postada bulunan ekleri inceler ve eklerde bulunan diğer ayrıntıları içerir. Gösterilen eklerin sayısı şu anda 10 ile sınırlıdır. Kötü amaçlı olduğu bulunan eklere ilişkin detonation ayrıntılarının burada gösterildiğine dikkat edin.
4. **URL'ler**: Bu sekmede, e-postada bulunan URL'ler ve URL'ler ile ilgili diğer ayrıntılar listele. URL'lerin sayısı şu anda 10 ile sınırlıdır, ancak ilk olarak kötü amaçlı URL'leri göstermek için bu *10'a öncelik ve öncelikleri vardır*. Önceliklendirme size zaman ve tahmin çalışması kazandırır. Kötü amaçlı ve detonlu olduğu bulunan URL'ler de burada gösterilir.
5. **Benzer e-postalar**: Bu sekmede, bu e-postaya özgü *ağ ileti kimliği +* alıcı bileşimine benzer tüm e-postalar liste edilir. Benzerlik yalnızca iletinin *gövdesine dayalıdır*. Postalarda bunları 'benzer' olarak kategorilere ayırmak için yapılan benzerlikler, eklerin dikkate *alınmasına neden olur*.

## <a name="new-to-the-email-entity-page"></a>E-posta varlık sayfasında yenisiniz

Bu e-posta varlık sayfasıyla birlikte gelen yeni özellikler vardır. Liste burada.

### <a name="email-preview-for-cloud-mailboxes"></a>Bulut posta kutuları için e-posta önizlemesi

E-postalar hala Bulutta varsa, yöneticiler ***Bulut*** posta kutularında e-postaları önizler. Yazılımdan silme durumunda (yönetici veya kullanıcı tarafından) veya ZAP (karantinaya almak için), e-postalar artık Bulut konumda yoktur. Bu durumda, yöneticiler bu belirli postaların önizlemesini görüntüleyemz. E-postalar atildi veya teslim başarısız oldu; hiçbir zaman posta kutusuna giremedi. Bu nedenle, yöneticiler de bu e-postaların önizlemesini görüntüleyemiyor.

> [!WARNING]
> E-postaları önizlemek için Önizleme adlı özel bir rol **gerekir**. Bu rolü, e-posta Microsoft 365 Defender portalında E-posta ve [& rollerinde açıklandığı Microsoft 365 Defender eklersiniz](permissions-microsoft-365-security-center.md#email--collaboration-roles-in-the-microsoft-365-defender-portal). Burada yeni bir **E-posta &** işbirliği rol grubu oluşturmanız ve bu yeni rol grubuna **Önizleme** rolünü eklemeniz veya bir rol grubuna Önizleme rolünü eklemeniz ve bu rol  grubuna, organizasyon yöneticilerinin **Explorer'da** çalışmalarını sağlayan bir rol grubu eklemeniz gerekir.

### <a name="detonation-details"></a>Detonation details

Bu ayrıntılar e-posta ekleri ve URL'lere özeldir. Kullanıcılar Explorer'a gidip dosya detonasyonu veya URL detonasyonu için ayarlanmış algılama teknolojisi filtresini uygulayarak bu ayrıntıları görebilirler. Dosyanın detonasyonu için filtrelenmiş e-postalar, detonation ayrıntılarına sahip kötü amaçlı bir dosya ve URL'ler için filtrelenmiş olanlar kötü amaçlı bir URL ve bunun detonasyonu ayrıntılarını içerir.

Kullanıcılar, kendi kiracılarının kendi e-postalarında bulunan, bilinen kötü amaçlı ekler veya URL'ler için zenginleştirilmiş detonation ayrıntıları görebilir. Bu, ekin veya URL'nin neden kötü amaçlı ve detonated olarak kabul edildiklerini anlamalarında müşterilere yardımcı olmak için Detonation zinciri, Detonation özeti, Ekran Görüntüsü ve Gözlemlenen davranış ayrıntılarını içerir.

1. *Detonation chain*. Tek bir dosya veya URL'nin detonasyonu birden çok detonasyonu tetikler. Detonation zinciri karara neden olan özgün kötü amaçlı dosya veya URL ve detonasyonun etkilenen diğer tüm dosyaları veya URL'leri de içinde olmak üzere, detonations yolunu izler. Bu URL'ler veya ekli dosyalar doğrudan e-postada yer alamasa da, bu çözümleme dosyanın veya URL'nin neden kötü amaçlı olduğunu belirlemek için önemlidir.  

    > [!NOTE]
    > Bu, buna bağlı varlıkların hiçbiri sorunlu bulunmamışsa veya dedesine sahipse yalnızca üst düzey öğeyi gösterebilir.

1. *Detonation Özeti* , çözümleme *zamanı,* detonasyonun meydana geldiği zaman, işletim sistemi ve uygulama, detonasyonun meydana geldiği işletim sistemi ve uygulama, dosya boyutu ve karar nedeni gibi temel bir özet sağlar.
1. *Ekran görüntüleri* , detonation sırasında yakalanan ekran görüntülerini gösterir. Detonation sırasında birden çok ekran görüntüsü olabilir. için hiçbir ekran görüntüsü yakalanıyor
    - Kapsayıcı türü dosyalar (.zip veya .rar.
    - Bir URL, dosyayı doğrudan indiren bir bağlantı açarsa. Öte yandan, indirilen dosyayı detonation zincirinde görüyorsunuz.
1. *Davranış* Ayrıntıları, tam olarak detonation sırasında olan olaylar ve detonation sırasında bulunan URL'ler, IP'ler, etki alanları ve dosyalar içeren gözlenebilir olaylar gibi davranış ayrıntılarını gösteren bir dışarı aktarmadır (ve sorunlu veya sorunlu olabilir). Aşağıdakiler için davranış ayrıntıları olmadığını fark edin:
    - Başka dosyaları tutan .zip veya .rar kapsayıcı dosyalar.

:::image type="content" source="../../media/email-entities-6-detonation-page.png" alt-text="*Derin Çözümleme* başlığı altındaki zincir, özet, detonation ayrıntılarını ve ekran görüntüsünü gösteren detonation özeti" lightbox="../../media/email-entities-6-detonation-page.png":::

### <a name="other-innovations"></a>Diğer yenilikler

*Etiketler*: Bunlar kullanıcılara uygulanan etiketlerdir. Kullanıcı bir alıcı ise, yöneticiler bir alıcı *etiketi* görebilir. Aynı şekilde, kullanıcı bir gönderense, bir *gönderen* etiketi olur. Bu, e-posta varlıkları sayfasının sol tarafında görüntülenir (yapışkan olarak tanımlanan bölümde ve dolayısıyla sayfaya sabitli).

*En son teslim konumu*: En son teslim konumu, ZAP gibi sistem eylemlerini veya Silinmiş Öğelere Taşı, son gibi yönetici eylemlerini kullanarak e-postanın bulunduğu konum olur. En son teslim konumu, yöneticileri iletinin geçerli konumu hakkında bilgilendirmeyi *hedeflemmiyor* . Örneğin, kullanıcı bir iletiyi silerse veya arşive taşırsa, teslim konumu güncelleştirilmez. Öte yandan, bir sistem eylemi güncelleştirilir ve konumu (e-posta karantinaya alınan bir ZAP gibi) güncelleştirmişse, en son teslim konumunu karantinaya alınacak şekilde güncelleştirebilir.

*E-posta* ayrıntıları: Çözümleme sekmesinde bulunan e-postanın daha ayrıntılı anlaşılması için *gereken* ayrıntılar.

- *Exchange kuralları (* posta akış kuralları veya ETR'ler olarak da bilinir): Bu kurallar aktarım katmanında bir iletiye uygulanır ve kimlik avı ve istenmeyen posta kararlarına göre önceliklidir. Posta akış kuralları, <https://admin.exchange.microsoft.com/#/transportrules>Exchange yönetim merkezinde oluşturulur ve değiştirilir; ancak herhangi bir posta akış kuralı bir ileti için geçerli olursa, kural adı ve GUID burada gösterilir. İzleme amacıyla değerli bilgiler.

- *Sistem Geçersiz Kılmaları*: Bu, sistem tarafından verilen teslim konumunu geçersiz kılarak (tehdit ve algılama teknolojisine göre) bir ileti için hedeflenen teslim konumu üzerinde istisnalar yapmanın bir aracıdır.

- *Toplu Şikayet Düzeyi (BCL)*: İletinin toplu şikayet düzeyi (BCL). Daha yüksek bir BCL, bir toplu posta iletisinin şikayet oluşturma olasılığı daha yüksek olduğunu gösterir (e-postanın istenmeyen posta olma olasılığı varsa doğal sonuç).

- *İstenmeyen Posta Güven düzeyi (SCL)*: İletinin istenmeyen posta güven düzeyi (SCL). Daha yüksek bir değer iletinin istenmeyen posta olma olasılığı daha yüksek olduğunu gösterir.

- *İstemci türü*: E-postanın rest gibi gönderildiği İstemci türünü gösterir.

- *İlerletir*: Autoforwaridng ile senaryolar için, hem iletme kullanıcıyı hem de ETR veya SMTP iletme gibi iletme türünü gösterir. 

- *Dağıtım listesi*: Alıcı e-postayı listenin bir üyesi olarak teslim ettiyseniz, dağıtım listesini gösterir. İç içe dağıtım listeleri söz konusu ise, en üst düzey dağıtım listesini gösterir.  

- *To, Bilgi*: E-postanın Bilgi alanlarında listelenen adresleri gösterir. Bu alanlardaki bilgiler 5000 karakterle sınırlıdır. 

- *Etki Alanı* Adı: Gönderenin etki alanı adıdır.

- *Etki Alanı* Sahibi: Gönderen etki alanının sahibini belirtir.

- *Etki Alanı* Konumu: Gönderen etki alanının konumunu belirtir.

- *Etki Alanı Oluşturulma* Tarihi: Gönderen etki alanının oluşturulma tarihini belirtir. Yeni oluşturulan etki alanı, diğer sinyaller bazı şüpheli davranışlara neden oluyorsa dikkatli olmalısınız.

*E-posta* Kimlik Doğrulaması: SPF, DKIM ve DMARC Microsoft 365 tarafından kullanılan e-posta kimlik doğrulama yöntemleri.

- Sender Policy Framework (**SPF**): İleti için SPF denetimi sonuçlarını açıklar. Olası değerler şöyle olabilir:
  - Pass (IP adresi): Geçen ileti için SPF denetimi ve gönderenin IP adresini içerir. İstemci, gönderenin etki alanı adına e-posta gönderme veya geçiş yetkisine sahip.
  - Başarısız (IP adresi): İletinin SPF denetimi başarısız oldu ve gönderenin IP adresini içerir. Buna bazen zor başarısız denir.
  - Geçici (neden): SPF kaydı ana bilgisayarı göndermesine izin verilmeyecek ancak geçişte olduğu olarak belirledi.
  - Nötr: SPF kaydı, IP adresinin gönderme yetkisi olup olmadığını açıkça onaylamaz.
  - Yok: Etki alanının SPF kaydı yoktur veya SPF kaydı bir sonucu değerlendirmez.
  - Bir hata oluştu. Geçici bir hata oluştu. Örneğin, bir DNS hatası. Aynı denetim daha sonra başarılı olabilir.
  - Permerror: Kalıcı bir hata oluştu. Örneğin, etki alanının kötü biçimlendirilmiş bir SPF kaydı var.

- DomainKeys Identified Mail (**DKIM**):
  - Pass: DkIM onay kutusunu iletiyle ilgili olarak gösterir.
  - Başarısız (neden): İletinin başarısız olup başarısız olduğunu DKIM onay kutusunu gösterir. Örneğin, ileti imzalanmamışsa veya imza doğrulanmamışsa.
  - Yok: İletinin imza olmadığını gösterir. Bu, etki alanının bir DKIM kaydı olduğunu veya DKIM kaydının bir sonucu değerlendirme olmadığını, yalnızca bu iletinin imza olmadığını belirtebilirsiniz.

- Etki Alanı Tabanlı İleti Kimlik Doğrulaması, Raporlama ve Uyum (**DMARC**):
  - Geçti: İletinin DMARC denetimine işaret olduğunu gösterir.
  - Başarısız: İletinin başarısız olduğunu DMARC denetimi gösterir.
  - Bestguesspass: Etki alanı için DMARC TXT kaydının olmadığını belirtir, ama varsa, iletinin DMARC denetimi geçmiş olabilir.
  - Yok: DNS'de gönderen etki alanı için DMARC TXT kaydının olmadığını gösterir.

*Bileşik Kimlik Doğrulaması*: Bu, Microsoft 365 SPF, DKIM ve DMARC gibi e-posta kimlik doğrulamasını birleştirerek iletinin kimlik doğrulaması olup olmadığını belirlemek için kullanılan değerdir. Değerlendirme temeli olarak postanın From *:* etki alanını kullanır.

### <a name="email-summary-panel"></a>E-posta özet paneli

E-posta özet paneli, tam e-posta varlık sayfasının özetlenmiş görünümüdur. E-posta hakkında standart ayrıntıları (ör. algılamalar) ve bağlama özgü bilgilerin (örneğin Karantina veya Gönderimler meta verileri) içerir. E-posta özet paneli geleneksel Gerçek Zamanlı Algılamalar, Tehdit Gezgini, Gönderiler ve Raporlama uçlamalarının yerini alır.

> [!div class="mx-imgBorder"]
> ![E-posta varlık bağlantısını açın.](../../media/open-email-entity-mdo.png)

> [!NOTE]
> Tüm bileşenleri görüntülemek için E-posta varlıklarını aç **bağlantısına** tıklayarak tam e-posta varlık sayfasını açın.  

E-posta özet paneli aşağıdaki bölümlere ayrılır:  

- *Teslim ayrıntıları*: Tehditler ve buna karşılık gelen güven düzeyi, algılama teknolojileri ve özgün ve en son teslim konumu hakkında bilgi içerir.

- *E-posta* ayrıntıları: Gönderen adı, gönderen adresi, alınan saat, kimlik doğrulama ayrıntıları ve diğer bazı diğer ayrıntılar gibi e-posta özellikleri hakkında bilgi içerir.

- *URL'ler*: Varsayılan olarak, 3 URL'yi ve bunların tehditlerini görüyorsunuz. İstediğiniz zaman Tüm **URL'leri görüntüle'yi** tıklatmak ve tüm URL'leri görmek ve dışarı aktarabilirsiniz.  

- *Ekler*: Varsayılan olarak 3 ek vardır. İstediğiniz zaman Tüm **ekleri görüntüle'yi tıklatmak** ve tüm ekleri görmek için genişletebilirsiniz. 

Yukarıdaki bölümlerin yanı sıra, özet paneliyle tümleştirilmiş birkaç deneyime özel bölümleri de görebilirsiniz: 

- Gönderiler: 

    - *Gönderim ayrıntıları*: Belirli gönderiler hakkında aşağıdaki bilgileri içerir:
        - Gönderilme tarihi
        - Konu
        - Gönderme türü
        - Gönderme nedeni
        - Gönderim Kimliği
        - Gönderilen

    - *Sonuç ayrıntıları*: Gönderilen iletiler gözden geçirildi. Gönderinizin sonucuyla birlikte önerilen sonraki adımları da görebilirsiniz.

- Karantina:  

    - *Karantina ayrıntıları*: Karantinaya özgü ayrıntıları içerir. Daha fazla bilgi için bkz [. Karantinaya alınmış iletileri yönetme](manage-quarantined-messages-and-files.md#view-quarantined-message-details).

        - Son kullanma tarihi: İletinin karantinadan otomatik olarak ve kalıcı olarak silinecek olduğu tarih/saat.
        - Yayım tarihi: İletinin yayım tarihi olan tüm e-posta adresleri (varsa).
        - Henüz yayınlanma tarihi: İletinin henüz yayınlanmamış olduğu tüm e-posta adresleri (varsa).

    - *Karantina eylemleri*: Farklı karantina eylemleri hakkında daha fazla bilgi için bkz. [Karantinaya alınmış iletileri yönetme](manage-quarantined-messages-and-files.md#take-action-on-quarantined-email).
