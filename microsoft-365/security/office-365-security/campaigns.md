---
title: Kampanya Görünümleri Office 365 için Microsoft Defender Plan
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.reviewer: mcostea
ms.date: ''
audience: ITPro
ms.topic: conceptual
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: ''
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
ms.custom: ''
description: Kampanya Görünümleri hakkında daha fazla bilgi Office 365 için Microsoft Defender.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: eb1e5e6e740accdb9c6102b798df8e60ab47dfff
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64467741"
---
# <a name="campaign-views-in-microsoft-defender-for-office-365"></a>Office 365 için Microsoft Defender'da Saldırı Kampanyası Görünümleri

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Geçerli olduğu yer:**
- [Office 365 için Microsoft Defender plan 2](defender-for-office-365.md)

Kampanya Görünümleri, Plan 2'Office 365 için Microsoft Defender bir özelliktir (örneğin, Microsoft 365 E5 Plan 2 Office 365 için Defender olan kuruluşlar). Kampanya Görünümleri Microsoft 365 Defender portalında kimlik avı saldırılarını tanımlar ve kategorilere ayırmaktadır. Kampanya Görünümleri şunları yapmak için yardımcı olabilir:

- Kimlik avı saldırılarını verimli bir şekilde araştırarak yanıt verin.
- Saldırının kapsamını daha iyi anlıyoruz.
- Karar verenlere değeri göster.

Kampanya Görünümleri bir saldırının büyük resmini herhangi bir insandan daha hızlı ve daha eksiksiz görmenizi sağlar.

## <a name="what-is-a-campaign"></a>Kampanya nedir?

Kampanya, bir veya birçok kuruluşa karşı eşgüdümli bir e-posta saldırısıdır. Kimlik bilgilerini ve şirket verilerini çalan e-posta saldırıları büyük ve olumlu bir endüstridir. Teknolojiler saldırıyı durdurma çabası artarak, başarının devamını sağlamak için saldırganlar yöntemlerinde değişiklik yapacaktır.

Microsoft, kampanyaları tanımlamanıza yardımcı olmak için tüm hizmet genelinde çok miktarda kimlik avı önleme, istenmeyen posta önleme ve kötü amaçlı yazılımdan koruma verilerinden faydalanan bir hizmettir. Saldırı bilgilerini çeşitli faktörlere göre analiz edip sınıflandırmız. Örneğin:

- **Saldırı kaynağı**: Kaynak IP adresleri ve gönderen e-posta etki alanları.
- **İleti özellikleri**: İletilerin içeriği, stili ve tonu.
- **İleti alıcıları**: Alıcılar nasıl ilişkili olur? Örneğin, alıcı etki alanları, alıcı iş işlevleri (yöneticiler, yöneticiler vb.), şirket türleri (büyük, küçük, genel, özel, vb.) ve endüstriler.
- **Saldırı yükü**: İletilerde kötü amaçlı bağlantılar, ekler veya diğer yüklemeler.

Kampanyalar kısa ömürle yaşanıyor olabileceği gibi, etkin ve etkin olmayan dönemlere sahip birkaç gün, hafta veya aya yay yayma da olabilir. Belirli bir kuruluşa karşı bir kampanya başlatıldı veya organizasyonunız birden çok şirket arasında daha büyük bir kampanyanın parçası olabilir.

## <a name="campaign-views-in-the-microsoft-365-defender-portal"></a>Microsoft 365 Defender portalında Kampanya Görünümleri

Kampanya Görünümleri, web portalına Microsoft 365 Defender-posta ve <https://security.microsoft.com> işbirliği **Kampanyaları &** \> **veya** doğrudan üzerinden kullanılabilir<https://security.microsoft.com/campaigns>.

:::image type="content" source="../../media/campaigns-overview.png" alt-text="Kampanyalara genel bakış Microsoft 365 Defender portalı" lightbox="../../media/campaigns-overview.png":::

Kampanya Görünümleri'ne şu sitelerden de çıkabilirsiniz:

- **E-& ve işbirliği** \> **Explorer** \> **Görünüm** \> **Kampanyalar**
- **E-& ve işbirliği** \> **Explorer** \> **Görünüm** \> **Tüm e-posta** \> **Kampanya** sekmesi
- **E-& ve işbirliği** \> **Explorer** \> **Görünüm** \> **Kimlik avı** \> **Kampanya** sekmesi
- **E-& ve işbirliği** \> **Explorer** \> **Görünüm** \> **Kötü amaçlı yazılım** \> **Kampanya** sekmesi

Kampanya Görünümlerine erişmek için, portalda Kuruluş **Yönetimi, Güvenlik** Yöneticisi veya **Güvenlik** Okuyucusu rol gruplarının Microsoft 365 Defender gerekir.  Daha fazla bilgi için bkz[. Microsoft 365 Defender portalına.](permissions-microsoft-365-security-center.md)

## <a name="campaigns-overview"></a>Kampanyalara genel bakış

Genel bakış sayfasında tüm kampanyalar hakkında bilgiler görüntülenir.

Varsayılan Kampanya **sekmesinde** , **Kampanya türü alanında** günde kaç alıcı olduğunu gösteren bir çubuk grafik gösterilir. Varsayılan olarak, grafikte hem Kimlik Avı hem **de Kötü Amaçlı** **Yazılım verileri** gösterilir.

> [!TIP]
> Hiçbir kampanya verisi görmüyorsanız, tarih aralığını veya filtreleri değiştirmeyi [deneyin](#filters-and-settings).

Genel bakış sayfasındaki grafiğin altındaki tablo Kampanya sekmesinde aşağıdaki **bilgileri** gösterir:

- **Ad**

- **Örnek konu**: Kampanyada iletilerden birinin konu satırı. Kampanyada yer alan tüm iletilerin konusu aynı olmayabilir.

- **Hedefli**: Hesaplanan yüzde: (kurumdaki kampanya alıcılarının sayısı) / (hizmet kapsamındaki tüm kuruluşlarda kampanyadaki alıcıların toplam sayısı). Bu değer, kampanyanın yalnızca sizin kuruluşa yönlendirilen dereceyi (daha yüksek bir değer) ve hizmet kapsamındaki diğer kuruluşlara da yönlendirilen dereceyi (daha düşük bir değer) gösterir.

- **Tür**: Bu değer Kimlik Avı veya **Kötü Amaçlı** **Yazılım'dır**.

- **Alt tür**: Bu değer kampanya hakkında daha fazla ayrıntı içerir. Örneğin:
  - **Kimlik** avı: Kullanılabilir durumda, bu kampanya tarafından kimlik avına yapılan markadır. Örneğin, `Microsoft`, `365``Unknown`, veya . `Outlook``DocuSign`
  - **Kötü amaçlı** yazılım: Örneğin, `HTML/PHISH` veya `HTML/<MalwareFamilyName>`.

  Kullanılabilir durumda, bu kampanya tarafından kimlik avına neden olan marka. Algılama bu teknoloji tarafından Office 365 için Defender olduğunda, **alt tür değerine ATP-** öneki eklenir.

- **Alıcılar**: Bu kampanya tarafından hedeflenen kullanıcı sayısı.

- **Gelen Kutusu**: Bu kampanyadan gelen iletileri Kendi Gelen Kutularına alan kullanıcıların sayısı (Önemsiz E-posta klasörlerine teslim edilmedi).

- **Tıklandı**: URL'ye tık kullanan veya kimlik avı iletisinde eki açan kullanıcıların sayısı.

- **Tıklama oranı**: "TıklandıY **kutusu" ile** /  **hesaplanan yüzdedir**. Bu değer, kampanyanın etkisinin bir göstergesidir. Başka bir deyişle, alıcılar iletiyi kimlik avı olarak tanımlayalırsa ve yük URL'sini tıklatmasa.

  Tıklama **oranı'nın** kötü amaçlı yazılım kampanyalarında kullanılma olmadığını unutmayın.

- **Ziyaret** Edildi: Yük web sitesine gerçekten kaç kullanıcı tarafından gönderildi. Tıklı değerler **varsa**, ancak Kasa Web sitesine erişimi engellenen bağlantılar varsa, bu değer sıfır olur.

Kampanya **kaynağı** sekmesi, ileti kaynaklarını dünya haritasında gösterir.

### <a name="filters-and-settings"></a>Filtreler ve ayarlar

Kampanya sayfasının en üstünde **, belirli** kampanyaları bulup ayırmanıza yardımcı olacak çeşitli filtre ve sorgu ayarları vardır.

:::image type="content" source="../../media/campaign-filters-and-settings.png" alt-text="Kampanya filtreleri" lightbox="../../media/campaign-filters-and-settings.png":::

En temel filtreleme, başlangıç tarihi/saati ve bitiş tarihi/saatidir.

Görünümü daha da fazla filtrelemek için Kampanya türü düğmesine tıklar, seçiminizi yapar ve ardından Yenile'ye tıklayarak birden çok değer filtresi içeren tek bir özellik **kullanabilirsiniz**.

Kampanya türü düğmesinde bulunan filtrelenebilir **kampanya özellikleri** aşağıdaki listede açıklanmıştır:

- **Temel**:
  - **Kampanya türü**: Kötü Amaçlı Yazılım **veya Kimlik** **Avı'ı seçin**. Seçimleri temizlemenin sonucu her ikisini de seçmekle aynıdır.
  - **Kampanya adı**
  - **Kampanya alt türü**
  - **Gönderen**
  - **Alıcılar**
  - **Gönderen etki alanı**
  - **Konu**
  - **Ek dosya adı**
  - **Kötü amaçlı yazılım ailesi**
  - **Etiketler**: Belirtilen kullanıcı etiketinin uygulandığı kullanıcılar veya gruplar (öncelik hesapları dahil). Kullanıcı etiketleri hakkında daha fazla bilgi için bkz. [Kullanıcı etiketleri](user-tags.md).
  - **Teslim eylemi**
  - **Ek eylem**
  - **Yön**
  - **Algılama teknolojisi**
  - **Özgün teslim konumu**
  - **En son teslim konumu**
  - **Sistem geçersiz kılar**

- **Gelişmiş**:
  - **İnternet ileti kimliği**: İleti **üst bilgisinde bulunan** İleti Kimliği üst bilgi alanında kullanılabilir. Örnek bir değerdir (köşeli `<08f1e0f6806a47b4ac103961109ae6ef@server.domain>` ayraçlara dikkatin).
  - **Ağ iletisi kimliği**: İleti üst bilgisinde **X-MS-Exchange-Organization-Network-Message-Id** üst bilgi alanında bulunan GUID değeri.
  - **Gönderen IP'si**
  - **Ek SHA256**: Dosyanın SHA256 karma değerini Windows Komut İstemi'ne aşağıdaki komutu çalıştırın: `certutil.exe -hashfile "<Path>\<Filename>" SHA256`.
  - **Küme Kimliği**
  - **Uyarı Kimliği**
  - **Uyarı İlkesi Kimliği**
  - **Kampanya Kimliği**
  - **ZAP URL sinyali**

- **URL'ler**:
  - **URL etki alanı**
  - **URL etki alanı ve yolu**
  - **URL**
  - **URL yolu**
  - **Karara tıklayın**

Birden çok özelikle filtreleme de dahil olmak üzere daha gelişmiş filtreleme için, sorgu **oluşturmak üzere Gelişmiş** filtre düğmesine tıklayabilirsiniz. Aynı kampanya özellikleri kullanılabilir, ancak aşağıdaki geliştirmelerle birlikte:

- Birden çok koşul **seçmek için Koşul ekle'yi** tıklatın.
- Koşullar arasında **Ve veya** **Veya işlecini** seçebilirsiniz.
- Karmaşık bileşik koşullar **oluşturmak için** koşul listesinin en altındaki Koşul grubu öğesini seçebilirsiniz.

Bitirdikten sonra **Sorgu düğmesine tıklayın** .

Temel veya gelişmiş bir filtre oluşturdukktan sonra, Sorguyu kaydet'i veya **Sorguyu farklı** **kaydet'i kullanarak bunu kaydedebilirsiniz**. Daha sonra Kampanyalar sayfasına **geri dönüp** Kaydedilmiş sorgu ayarları'nı tıklatarak kaydedilmiş **bir filtreyi yükleyebilirsiniz**.

Grafiği veya kampanya listesini dışarı aktarma için Dışarı aktar'a tıklayın ve **Grafik** verilerini **dışarı aktar'ı** veya Kampanya listesini **dışarı aktar'ı seçin**.

Uç Nokta için Microsoft Defender aboneliğiniz varsa, kampanyayla ilgili bilgilere bağlantı **Ayarlar bağlantıyı kesmek için MDE Uç Nokta için Microsoft Defender**. Daha fazla bilgi için bkz[. Office 365 için Microsoft Defender'i Uç Nokta için Microsoft Defender](integrate-office-365-ti-with-mde.md).

## <a name="campaign-details"></a>Kampanya ayrıntıları

Bir kampanyanın adını üzerine tıklarken, kampanya ayrıntıları bir çıkışta görünür.

### <a name="campaign-information"></a>Kampanya bilgileri

Kampanya ayrıntıları görünümünün en üstünde, aşağıdaki kampanya bilgileri kullanılabilir:

- **Kampanya Kimliği**: Benzersiz kampanya tanımlayıcısıdır.
- **Etkinlik**: Kampanyanın süresi ve etkinliği.
- Seçtiğiniz (veya zaman çizelgesinde seçtiğiniz) tarih aralığı filtresi için aşağıdaki veriler:
- **Etki**
- **İletiler**: Toplam alıcı sayısıdır.
- **Gelen Kutusu**: Önemsiz E-posta klasörüne değil Gelen Kutusu'na teslim edilen ileti sayısı.
- **Tıklı bağlantı**: Kimlik avı iletisinde URL yüküne kaç kullanıcı tıklandı?
- **Ziyaret edilen bağlantı**: URL'yi kaç kullanıcı ziyaret etti.
- **Hedefli(%)**: Hesaplanan yüzde: (kurumdaki kampanya alıcılarının sayısı) / (hizmet kapsamındaki tüm kuruluşlarda kampanyadaki toplam alıcı sayısı). Bu değerin kampanyanın tüm yaşam süresi boyunca hesaplanmış olduğunu ve tarih filtrelerine göre değişme olmadığını unutmayın.
- Kampanya akışı için başlangıç tarihi/saati ve bitiş verileri/saat filtreleri sonraki bölümde açıklandığı gibi.
- Kampanya etkinliğinin etkileşimli bir zaman çizelgesi: Zaman çizelgesi, kampanyanın tüm ömrü boyunca olan etkinliği gösterir. Algılanan iletilerin miktarını görmek için grafikte veri noktalarının üzerine gelin.

:::image type="content" source="../../media/campaign-details-campaign-info.png" alt-text="Kampanya bilgileri" lightbox="../../media/campaign-details-campaign-info.png":::

### <a name="campaign-flow"></a>Kampanya akışı

Kampanya ayrıntıları görünümünün ortasında, kampanya hakkında önemli ayrıntılar yatay bir akış diyagramında (Sankey diyagramı olarak bilinir _) sunulmaktadır_ . Bu ayrıntılar kampanyanın öğelerini ve organizasyon üzerindeki olası etkiyi anlamanıza yardımcı olur.

> [!TIP]
> Akış diyagramında görüntülenen bilgiler, önceki bölümde açıklandığı gibi zaman çizelgesindeki tarih aralığı filtresi tarafından denetlenmektedir.

:::image type="content" source="../../media/campaign-details-no-recipient-actions.png" alt-text="Kullanıcı URL tıklamaları içermeen Kampanya ayrıntıları" lightbox="../../media/campaign-details-no-recipient-actions.png":::

Diyagramda yatay bir banda gelirsiniz, ilgili iletilerin sayısını (örneğin, belirli bir kaynak IP'den gelen iletiler, belirtilen gönderen etki alanını kullanan kaynak IP'den gelen iletiler vb.) alırsınız.

Diyagram aşağıdaki bilgileri içerir:

- **Gönderen IP'leri**
- **Gönderen etki alanları**
- **Filtre kararları**: Karar değerleri, İstenmeyen posta iletisi önleme üst bilgilerde açıklandığı gibi kullanılabilir kimlik avı ve istenmeyen posta filtreleme [kararlarına yöneliktir](anti-spam-message-headers.md). Kullanılabilir değerler aşağıdaki tabloda açıklanmıştır:

  |Değer|İstenmeyen posta filtresi kararını|Açıklama|
  |---|---|---|
  |**İzin verildi**|`SFV:SKN` <p> `SFV:SKI`|İleti istenmeyen posta değil olarak işaretlendi ve/veya istenmeyen posta filtrelemesi tarafından değerlendirilmeden önce filtreleme atlandı. Örneğin, ileti bir posta akışı kuralı (aktarım kuralı olarak da bilinir) tarafından istenmeyen posta değil olarak işaretlendi. <p> İleti istenmeyen posta filtrelemesi diğer nedenlerle atlandı. Örneğin, gönderen ve alıcı aynı kuruluşta gibi görünür.|
  |**Engellendi**|`SFV:SKS`|İleti, istenmeyen posta filtrelemesi tarafından değerlendirilmeden önce istenmeyen posta olarak işaretlendi. Örneğin, bir posta akışı kuralına göre.|
  |**Algılandı**|`SFV:SPM`|İleti, istenmeyen posta filtrelemesi ile istenmeyen posta olarak işaretlendi.|
  |**Algılanmadı**|`SFV:NSPM`|İleti istenmeyen posta filtresiyle istenmeyen posta değil olarak işaretlendi.|
  |**Yayımlanan**|`SFV:SKQ`|İleti karantinadan çıkarıldı diye istenmeyen posta filtrelemesi atlandı.|
  |**Kiracı İzin Ver**<sup>\*</sup>|`SFV:SKA`|İleti, istenmeyen posta önleme ilkesi ayarları nedeniyle istenmeyen posta filtresini atlandı. Örneğin, gönderen izin verilen gönderenler listesinde veya izin verilen etki alanı listesinde yer alıyor.|
  |**Kiracı Bloğu**<sup>\*\*</sup>|`SFV:SKA`|İleti, istenmeyen posta önleme ilkesi ayarları nedeniyle istenmeyen posta filtrelemesi tarafından engellendi. Örneğin, gönderen izin verilen gönderenler listesinde veya izin verilen etki alanı listesinde yer alıyor.|
  |**Kullanıcı İzin Ver**<sup>\*</sup>|`SFV:SFE`|İleti istenmeyen posta filtrelemesini atlandı çünkü gönderen kullanıcının Posta Gönderenler Kasa içinde yer alıyor.|
  |**Kullanıcı Bloğu**<sup>\*\*</sup>|`SFV:BLK`|İleti, gönderen kullanıcının Engellenen Gönderenler listesinde yer alıyor olduğu için istenmeyen posta filtrelemesi tarafından engellendi.|
  |**ZAP**|yok|[Sıfır saatlik otomatik temizleme (ZAP),](zero-hour-auto-purge.md) teslim edilen iletiyi Gereksiz E-posta klasörüne veya karantinaya taşıdı. Eylemi istenmeyen posta önleme [ilkelerde yapılandırmış oluruz](configure-your-spam-filter-policies.md).|

  <sup>\*</sup> İzin verilen ileti hizmet tarafından engellenmiş olabilir, çünkü istenmeyen posta önleme ilkelerinizi gözden geçirebilirsiniz.

  <sup>\*\*</sup> İstenmeyen posta önleme ilkelerinizi gözden geçirebilirsiniz, çünkü bu iletiler karantinaya alınmalıdır, teslim edilmedi.

- **İleti hedefleri**: Kullanıcılar iletideki yük URL'sini tıklatmasa bile, büyük olasılıkla alıcılara teslim edilen iletileri (Gelen Kutusu'na veya Gereksiz E-posta klasörüne) araştırmanız gerekir. Karantinaya alınmış iletileri karantinadan da kaldırabilirsiniz. Daha fazla bilgi için bkz. [EOP'de e-posta iletileri karantinaya alınmış](quarantine-email-messages.md).
  - **Klasör silindi**
  - **Bırakılan**
  - **Dış**: Alıcı, karma ortamlarda şirket içi e-posta kuruluşta yer alır.
  - **Başarısız**
  - **Iletildi**
  - **Gelen Kutusu**
  - **Gereksiz klasör**
  - **Karantina**
  - **Unknown**

- **URL tıklamaları**: Bu değerler bir sonraki bölümde açıklanmıştır.

> [!NOTE]
> 10'dan fazla öğe içeren tüm katmanlarda ilk 10 öğe gösterilirken, geri kalanı Diğer katmanlarda birlikte **paketleniyor**.

#### <a name="url-clicks"></a>URL tıklamaları

Kimlik avı iletisi alıcının Gelen Kutusu veya Gereksiz E-posta klasörüne teslim edilirken, kullanıcının yük URL'sini tıklatma şansı her zaman vardır. URL'ye tıklamak başarının küçük bir ölçümüdür, ancak kimlik avı iletisine neden posta kutusuna teslim olmadığını belirlemeniz gerekir.

Kullanıcı kimlik avı iletisinde yük URL'sini tıklattığında, eylemler kampanya ayrıntıları görünümünde diyagramın **URL** tıklamaları alanında görüntülenir.

- **İzin verildi**
- **BlockPage**: Alıcı yüklenmiş URL'ye tıklamış ancak kötü amaçlı web sitesine erişimi, Kasa [Bağlantılar](safe-links.md) ilkesi tarafından engellenmiş.
- **BlockPageOverride**: Alıcı iletide yükün URL'sine tıkladı, Kasa Bağlantılar bunları durdurmayı denedi ancak engeli geçersiz kılmasına izin verildi. Kullanıcıların karar [Kasa ve kötü](set-up-safe-links-policies.md) amaçlı web sitesine devam etmek için neden kullanıcıların Yeni Bağlantılar kararını geçersiz k Kasa için Bağlantı ilkelerinizi incelemeniz gerekir.
- **PendingDetonationPage**: Kasa Attachments in Office 365 için Microsoft Defender, sanal bilgisayar ortamında yük URL'sini açma ve inceleme sürecindedir.
- **PendingDetonationPageOverride**: Alıcıya yükün detonasyonu işlemini geçersiz k kullandı ve sonuçları beklemeden URL'yi açtı.

### <a name="tabs"></a>Sekmeler

Kampanya ayrıntıları görünümündeki sekmeler, kampanyayı daha fazla incelemenize olanak sağlayan bir sekmedir.

> [!TIP]
> Sekmelerde görüntülenen bilgiler, Kampanya bilgileri bölümünde açıklandığı gibi zaman çizelgesindeki tarih aralığı filtresi [tarafından denetlenmektedir](#campaign-information) .

- **URL tıklamaları**: Kullanıcılar iletide yükün URL'sine tıklamadı ise bu bölüm boş olur. Kullanıcı URL'ye tıklaysa aşağıdaki değerler doldurulur:
  - **Kullanıcı**<sup>\*</sup>
  - **URL**<sup>\*</sup>
  - **Saat'e tıklayın**
  - **Karara tıklayın**

- **Gönderen IP'leri**
  - **Gönderen IP'si**<sup>\*</sup>
  - **Toplam sayı**
  - **Gelen Kutusu**
  - **Gelen Kutusu Değil**
  - **SPF geçti**: Gönderenin kimliği [Sender Policy Framework (SPF) tarafından doğrulandı](how-office-365-uses-spf-to-prevent-spoofing.md). SPF doğrulamasını geçemeyen bir gönderen kimliği doğrulanmamış bir göndereni veya iletinin yasal bir gönderene kimlik doğrulaması olduğunu gösterir.

- **Gönderenler**
  - **Gönderen**: Bu, SMTP MAIL FROM komutunda yer alan gerçek gönderen adresidir ve bu, kullanıcıların e-posta istemcilerinde göreceği Gönderen: e-posta adresi olmayabilir.
  - **Toplam sayı**
  - **Gelen Kutusu**
  - **Gelen Kutusu Değil**
  - **DKIM passed**: Gönderenin kimliği Etki Alanı Anahtarları Tanımlanan [Posta (DKIM)tarafından doğrulandı](support-for-validation-of-dkim-signed-messages.md). DKIM doğrulamasını geçemeyen bir gönderen kimliği doğrulanmamış bir göndereni veya iletinin yasal bir gönderene yönelik olduğunu gösterir.
  - **DMARC geçti**: Gönderenin kimliği Etki Alanı Tabanlı İleti Kimlik Doğrulaması, Raporlama ve [Uyumluluk (DMARC) tarafından doğrulandı](use-dmarc-to-validate-email.md). DMARC doğrulamasını geçemeyen bir gönderen, kimliği doğrulanmamış bir göndereni veya iletinin yasal bir gönderene kimlik doğrulaması olduğunu gösterir.

- **Ekler**
  - **Dosya adı**
  - **SHA256**
  - **Kötü amaçlı yazılım ailesi**
  - **Toplam sayı**

- **URL**
  - **URL**<sup>\*</sup>
  - **Toplam Sayı**

<sup>\*</sup> Bu değere tıklamak, kampanya ayrıntıları görünümünün üstünde belirtilen öğe (kullanıcı, URL, vb.) hakkında daha fazla ayrıntı içeren yeni bir açılır öğe açar. Kampanya ayrıntıları görünümüne dönmek için, yeni **çıkışta** Bitti'ye tıklayın.

### <a name="buttons"></a>Düğmeler

Kampanya ayrıntıları görünümünün altındaki düğmeler, kampanyayla ilgili ayrıntıları araştırma ve kaydetmeyi sağlar:

- **İletileri inceleme**: Kampanyayı daha fazla araştırmak için Threat Explorer'ın gücünü kullanın:
  - **Tüm iletiler**: Arama filtresi olarak Kampanya Kimliği değerini kullanarak yeni bir **Tehdit** Gezgini arama sekmesi açar.
  - **Gelen kutusu iletileri**: Kampanya Kimliği ve Teslim konumu: Arama filtresi olarak  Gelen Kutusu'na kullanarak yeni **bir** Tehdit Gezgini arama sekmesi açar.
  - **İç iletiler**: Arama filtresi olarak Kampanya Kimliği ve Yön Yönü:  Şirket içi kuruluş'un kullanımıyla yeni **bir Tehdit** Gezgini arama sekmesi açar.

- **Tehdit raporunu indirin**: Kampanya ayrıntılarını bir Word belgesine indirin (varsayılan olarak, Kampanya ayrıntıları CampaignReport.docx). İndirme işlemi, yalnızca seçtiğiniz tarihleri filtrelemek için değil, kampanyanın tüm ömrü boyunca ayrıntıları içerir.
