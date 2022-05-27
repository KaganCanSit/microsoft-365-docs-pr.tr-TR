---
title: Office 365 için Microsoft Defender Planındaki Kampanya Görünümleri
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
description: Office 365 için Microsoft Defender'deki Kampanya Görünümleri hakkında bilgi edinin.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 5308770e4ddb72ead5e4d5dac7506c507aa407f6
ms.sourcegitcommit: a8fbaf4b441b5325004f7a2dacd9429ec9d80534
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/26/2022
ms.locfileid: "65739637"
---
# <a name="campaign-views-in-microsoft-defender-for-office-365"></a>Office 365 için Microsoft Defender'da Saldırı Kampanyası Görünümleri

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Uygulandığı öğe**
- [Office 365 için Microsoft Defender plan 2](defender-for-office-365.md)

Kampanya Görünümleri Office 365 için Microsoft Defender Plan 2'deki bir özelliktir (örneğin, Microsoft 365 E5 veya Office 365 için Defender Plan 2 eklentisi olan kuruluşlar). Microsoft 365 Defender portalındaki Kampanya Görünümleri, hizmetteki kimlik avı saldırılarını tanımlar ve kategorilere ayırır. Kampanya Görünümleri size yardımcı olabilir:

- Kimlik avı saldırılarını verimli bir şekilde araştırın ve yanıt verin.
- Saldırının kapsamını daha iyi anlayın.
- Değeri karar verenlere gösterin.

Kampanya Görünümleri, herhangi bir insandan daha hızlı ve eksiksiz bir saldırının büyük resmini görmenizi sağlar.

kuruluşunuzu hedef alan saldırı kampanyalarını anlamanıza yardımcı olmak Office 365 için Microsoft Defender'deki kampanya görünümlerini gösteren bu kısa videoyu izleyin.  
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWGBL8]

## <a name="what-is-a-campaign"></a>Kampanya nedir?

Kampanya, bir veya birden çok kuruluşa yönelik eşgüdümlü bir e-posta saldırısıdır. Kimlik bilgilerini ve şirket verilerini çalan e-posta saldırıları büyük ve kazançlı bir endüstridir. Saldırıları durdurma çabasında teknolojiler arttıkça, saldırganlar başarının devamını sağlamak için yöntemlerini değiştirir.

Microsoft, kampanyaların tanımlanmasına yardımcı olmak için tüm hizmet genelinde çok miktarda kimlik avı, istenmeyen posta önleme ve kötü amaçlı yazılımdan koruma verilerinden yararlanıyor. Saldırı bilgilerini çeşitli faktörlere göre analiz edip sınıflandırırız. Örneğin:

- **Saldırı kaynağı**: Kaynak IP adresleri ve gönderen e-posta etki alanları.
- **İleti özellikleri**: İletilerin içeriği, stili ve tonu.
- **İleti alıcıları**: Alıcıların ilişkisi. Örneğin, alıcı etki alanları, alıcı iş işlevleri (yöneticiler, yöneticiler vb.), şirket türleri (büyük, küçük, genel, özel vb.) ve sektörler.
- **Saldırı yükü**: İletilerdeki kötü amaçlı bağlantılar, ekler veya diğer yükler.

Kampanya kısa süreli olabileceği gibi, etkin ve etkin olmayan dönemlerle birkaç gün, hafta veya aya yayılabilir. Belirli bir kuruluşunuzda bir kampanya başlatılabilir veya kuruluşunuz birden çok şirket arasında daha büyük bir kampanyanın parçası olabilir.

## <a name="campaign-views-in-the-microsoft-365-defender-portal"></a>Microsoft 365 Defender portalındaki Kampanya Görünümleri

Kampanya Görünümleri, Microsoft 365 Defender portalında <https://security.microsoft.com> **, E-posta & işbirliği** \> **Kampanyaları'nda** veya doğrudan adresinde <https://security.microsoft.com/campaigns>bulunabilir.

:::image type="content" source="../../media/campaigns-overview.png" alt-text="Microsoft 365 Defender portalında Kampanyalara genel bakış" lightbox="../../media/campaigns-overview.png":::

Kampanya Görünümleri'ne şu kaynaklardan da ulaşabilirsiniz:

- **E-posta & işbirliği** \> **Explorer** \> **Görünüm** \> **Kampanya**
- **E-posta & işbirliği** \> **Explorer** \> **Görünüm** \> **Tüm e-postalar** \> **Kampanya** sekmesi
- **E-posta & işbirliği** \> **Explorer** \> **Görünüm** \> **Phish** \> **Kampanya** sekmesi
- **E-posta & işbirliği** \> **Explorer** \> **Görünüm** \> **Malware** \> **Kampanya** sekmesi

Kampanya Görünümleri'ne erişmek için Microsoft 365 Defender portalında **Kuruluş Yönetimi**, **Güvenlik Yöneticisi** veya **Güvenlik Okuyucusu** rol gruplarının üyesi olmanız gerekir. Daha fazla bilgi için bkz. [Microsoft 365 Defender portalında İzinler](permissions-microsoft-365-security-center.md).

## <a name="campaigns-overview"></a>Kampanyalara genel bakış

Genel bakış sayfasında tüm kampanyalarla ilgili bilgiler gösterilir.

Varsayılan **Kampanya** sekmesinde, **Kampanya türü** alanında günlük alıcı sayısını gösteren bir çubuk grafik gösterilir. Grafikte varsayılan olarak **hem Kimlik Avı** hem de **Kötü Amaçlı Yazılım** verileri gösterilir.

> [!TIP]
> Herhangi bir kampanya verisi görmüyorsanız tarih aralığını veya [filtreleri](#filters-and-settings) değiştirmeyi deneyin.

Genel bakış sayfasındaki grafiğin altındaki tabloda **Kampanya** sekmesinde aşağıdaki bilgiler gösterilir:

- **Ad**

- **Örnek konu**: Kampanyadaki iletilerden birinin konu satırı. Kampanyadaki tüm iletilerin aynı konuya sahip olması gerekmediğini unutmayın.

- **Hedeflenen**: Şu şekilde hesaplanan yüzde: (kuruluşunuzdaki kampanya alıcılarının sayısı) / (hizmetteki tüm kuruluşlar genelinde kampanyadaki toplam alıcı sayısı). Bu değer, kampanyanın yalnızca kuruluşunuza (daha yüksek bir değer) ve hizmetteki diğer kuruluşlara (daha düşük bir değer) yönlendirildiği dereceyi gösterir.

- **Tür**: Bu değer **Kimlik Avı** veya **Kötü Amaçlı Yazılımdır**.

- **Alt tür**: Bu değer kampanya hakkında daha fazla ayrıntı içerir. Örneğin:
  - **Kimlik avı**: Kullanılabilir olduğunda, bu kampanya tarafından kimlik avı yapılan markadır. Örneğin, , `Microsoft``365`, `Unknown`, `Outlook`veya `DocuSign`.
  - **Kötü amaçlı yazılım**: Örneğin, `HTML/PHISH` veya `HTML/<MalwareFamilyName>`.

  Mümkün olduğunda, bu kampanya tarafından kimlik avına alınan marka. Algılama Office 365 için Defender teknolojisi tarafından yönlendirildiğinde, **atp**- ön eki alt tür değerine eklenir.

- **Alıcılar**: Bu kampanya tarafından hedeflenen kullanıcı sayısı.

- **Gelen Kutusu: Gelen Kutusu'nda** bu kampanyadan ileti alan kullanıcıların sayısı (Gereksiz E-posta klasörüne teslim edilmedi).

- **Tıklanan**: KIMLIK avı iletisinde URL'ye tıklayan veya eki açan kullanıcıların sayısı.

- **Tıklama oranı**: "**Tıklanan** / **Gelen Kutusu**" tarafından hesaplanan yüzde. Bu değer, kampanyanın etkinliğinin bir göstergesidir. Başka bir deyişle, alıcıların iletiyi kimlik avı olarak tanımlayıp tanımlayamadığı ve yük URL'sine tıklamadıkları.

  **Tıklama oranının** kötü amaçlı yazılım kampanyalarında kullanılmadığını unutmayın.

- **Ziyaret edildi**: Kaç kullanıcının yük web sitesine gerçekten ulaşmış olduğunu. **Tıklanan** değerler varsa, ancak Kasa Bağlantılar web sitesine erişimi engellediyse, bu değer sıfır olur.

**Kampanya kaynağı** sekmesi, ileti kaynaklarını dünya haritasında gösterir.

### <a name="filters-and-settings"></a>Filtreler ve ayarlar

**Kampanya** sayfasının üst kısmında, belirli kampanyaları bulmanıza ve yalıtmanıza yardımcı olacak çeşitli filtre ve sorgu ayarları vardır.

:::image type="content" source="../../media/campaign-filters-and-settings.png" alt-text="Kampanya filtreleri" lightbox="../../media/campaign-filters-and-settings.png":::

Yapabileceğiniz en temel filtreleme başlangıç tarihi/saati ve bitiş tarihi/saatidir.

Görünümü daha fazla filtrelemek için **, Kampanya türü** düğmesine tıklayarak, seçiminizi yaparak ve ardından **Yenile'ye** tıklayarak birden çok değer filtrelemesi içeren tek bir özellik yapabilirsiniz.

**Kampanya türü** düğmesinde kullanılabilen filtrelenebilir kampanya özellikleri aşağıdaki listede açıklanmıştır:

- **Temel**:
  - **Kampanya türü**: **Kötü Amaçlı Yazılım** veya **Kimlik Avı'nı** seçin. Seçimlerin temizlenmesi, her ikisini de seçmekle aynı sonucu elde eder.
  - **Kampanya adı**
  - **Kampanya alt türü**
  - **Gönderen**
  - **Alıcı**
  - **Gönderen etki alanı**
  - **Konu**
  - **Ek dosya adı**
  - **Kötü amaçlı yazılım ailesi**
  - **Etiketler**: Belirtilen kullanıcı etiketi uygulanmış olan kullanıcılar veya gruplar (öncelik hesapları dahil). Kullanıcı etiketleri hakkında daha fazla bilgi için bkz. [Kullanıcı etiketleri](user-tags.md).
  - **Teslim eylemi**
  - **Ek eylem**
  - **Yön**
  - **Algılama teknolojisi**
  - **Özgün teslimat konumu**
  - **En son teslimat konumu**
  - **Sistem geçersiz kılmaları**

- **Gelişmiş**:
  - **İnternet ileti kimliği: İleti** üst bilgisindeki **İleti Kimliği** üst bilgisi alanında kullanılabilir. Örnek bir değerdir `<08f1e0f6806a47b4ac103961109ae6ef@server.domain>` (açılı ayraçlara dikkat edin).
  - **Ağ iletisi kimliği**: İleti üst bilgisindeki **X-MS-Exchange-Organization-Network-Message-Id** üst bilgi alanında bulunan bir GUID değeri.
  - **Gönderen IP'i**
  - **Ek SHA256**: Windows bir dosyanın SHA256 karma değerini bulmak için komut isteminde aşağıdaki komutu çalıştırın: `certutil.exe -hashfile "<Path>\<Filename>" SHA256`.
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

Birden çok özelliğe göre filtreleme de dahil olmak üzere daha gelişmiş **filtreleme için Gelişmiş filtre** düğmesine tıklayarak sorgu oluşturabilirsiniz. Aynı kampanya özellikleri kullanılabilir ancak aşağıdaki geliştirmeler sağlanır:

- Birden çok koşul seçmek için **Koşul ekle'ye** tıklayabilirsiniz.
- Koşullar arasında **Ve** veya **Or** işlecini seçebilirsiniz.
- Karmaşık bileşik koşullar oluşturmak için koşullar listesinin en altındaki **Koşul grubu** öğesini seçebilirsiniz.

İşiniz bittiğinde **Sorgu** düğmesine tıklayın.

Temel veya gelişmiş bir filtre oluşturduktan sonra, **Sorguyu kaydet** veya **Sorguyu farklı kaydet'i kullanarak bu filtreyi kaydedebilirsiniz**. Daha sonra **Kampanyalar** sayfasına döndüğünüzde Kayıtlı **sorgu ayarları'na** tıklayarak kaydedilmiş bir filtre yükleyebilirsiniz.

Grafiği veya kampanya listesini dışarı aktarmak için **Dışarı Aktar'a** tıklayın ve **Grafik verilerini dışarı aktar'ı** veya **Kampanya listesini dışarı aktar'ı** seçin.

Uç Nokta için Microsoft Defender aboneliğiniz varsa, Uç Nokta için Microsoft Defender ile kampanya bilgilerini bağlamak veya bağlantısını kesmek için **MDE** Ayarlar'e tıklayabilirsiniz. Daha fazla bilgi için bkz. [Office 365 için Microsoft Defender Uç Nokta için Microsoft Defender ile tümleştirme](integrate-office-365-ti-with-mde.md).

## <a name="campaign-details"></a>Kampanya ayrıntıları

Bir kampanyanın adına tıkladığınızda, kampanya ayrıntıları açılır öğede görünür.

### <a name="campaign-information"></a>Kampanya bilgileri

Kampanya ayrıntıları görünümünün en üstünde aşağıdaki kampanya bilgileri bulunur:

- **Kampanya Kimliği**: Benzersiz kampanya tanımlayıcısı.
- **Etkinlik**: Kampanyanın süresi ve etkinliği.
- Seçtiğiniz (veya zaman çizelgesinde seçtiğiniz) tarih aralığı filtresi için aşağıdaki veriler:
- **Etki**
- **İletiler**: Alıcıların toplam sayısı.
- **Gelen Kutusu:** Gereksiz E-posta klasörüne değil Gelen Kutusu'na teslim edilen ileti sayısı.
- **Tıklanan bağlantı**: Kimlik avı iletisindeki URL yüküne kaç kullanıcı tıkladı?
- **Ziyaret edilen bağlantı**: Url'yi ziyaret eden kullanıcı sayısı.
- **Hedeflenen(%)**: Şu şekilde hesaplanan yüzde: (kuruluşunuzdaki kampanya alıcılarının sayısı) / (hizmetteki tüm kuruluşlar genelinde kampanyadaki toplam alıcı sayısı). Bu değerin kampanyanın tüm ömrü boyunca hesaplandığını ve tarih filtrelerine göre değişmediğini unutmayın.
- Sonraki bölümde açıklandığı gibi kampanya akışı için başlangıç tarihi/saati ve bitiş verileri/saati filtreleri.
- Kampanya etkinliğinin etkileşimli bir zaman çizelgesi: Zaman çizelgesi, kampanyanın tüm ömrü boyunca etkinliği gösterir. Algılanan ileti miktarını görmek için grafikteki veri noktalarının üzerine gelebilirsiniz.

:::image type="content" source="../../media/campaign-details-campaign-info.png" alt-text="Kampanya bilgileri" lightbox="../../media/campaign-details-campaign-info.png":::

### <a name="campaign-flow"></a>Kampanya akışı

Kampanya ayrıntıları görünümünün ortasında, kampanyayla ilgili önemli ayrıntılar yatay akış diyagramında ( _Sankey_ diyagramı olarak bilinir) gösterilir. Bu ayrıntılar kampanyanın öğelerini ve kuruluşunuzdaki olası etkisini anlamanıza yardımcı olur.

> [!TIP]
> Akış diyagramında görüntülenen bilgiler, önceki bölümde açıklandığı gibi zaman çizelgesindeki tarih aralığı filtresi tarafından denetlenır.

:::image type="content" source="../../media/campaign-details-no-recipient-actions.png" alt-text="Kullanıcı URL'si tıklamalarını içermeyen Kampanya ayrıntıları" lightbox="../../media/campaign-details-no-recipient-actions.png":::

Diyagramda yatay bir bandın üzerine gelirseniz, ilgili ileti sayısını (örneğin, belirli bir kaynak IP'den gelen iletiler, belirtilen gönderen etki alanını kullanan kaynak IP'den gelen iletiler vb.) görürsünüz.

Diyagram aşağıdaki bilgileri içerir:

- **Gönderen IP'leri**
- **Gönderen etki alanları**
- **Filtre kararları**: Karar değerleri, istenmeyen posta önleme [ileti üst bilgilerinde](anti-spam-message-headers.md) açıklandığı gibi kullanılabilir kimlik avı ve istenmeyen posta filtreleme kararlarıyla ilgilidir. Kullanılabilir değerler aşağıdaki tabloda açıklanmıştır:

  |Değer|İstenmeyen posta filtresi kararı|Açıklama|
  |---|---|---|
  |**Izin verilen**|`SFV:SKN` <p> `SFV:SKI`|İleti istenmeyen posta değil olarak işaretlendi ve/veya istenmeyen posta filtrelemesi tarafından değerlendirilmeden önce filtreleme atlandı. Örneğin, ileti bir posta akışı kuralı (aktarım kuralı olarak da bilinir) tarafından istenmeyen posta olarak işaretlenmedi. <p> İleti, istenmeyen posta filtrelemeyi başka nedenlerle atladı. Örneğin, gönderen ve alıcı aynı kuruluşta gibi görünür.|
  |**Engellenen**|`SFV:SKS`|İleti, istenmeyen posta filtrelemesi tarafından değerlendirilmeden önce istenmeyen posta olarak işaretlendi. Örneğin, bir posta akışı kuralına göre.|
  |**Algılandı**|`SFV:SPM`|İleti, istenmeyen posta filtrelemesi tarafından istenmeyen posta olarak işaretlendi.|
  |**Algılanmadı**|`SFV:NSPM`|İleti, istenmeyen posta filtrelemesi tarafından istenmeyen posta değil olarak işaretlendi.|
  |**Yayım -lanan**|`SFV:SKQ`|İleti, karantinadan çıkarıldığı için istenmeyen posta filtrelemeyi atladı.|
  |**Kiracı İzin Ver**<sup>\*</sup>|`SFV:SKA`|İleti, istenmeyen posta önleme ilkesindeki ayarlar nedeniyle istenmeyen posta filtrelemeyi atladı. Örneğin, gönderen izin verilen gönderen listesinde veya izin verilen etki alanı listesindeydi.|
  |**Kiracı Bloğu**<sup>\*\*</sup>|`SFV:SKA`|İleti, istenmeyen posta önleme ilkesindeki ayarlar nedeniyle istenmeyen posta filtrelemesi tarafından engellendi. Örneğin, gönderen izin verilen gönderen listesinde veya izin verilen etki alanı listesindeydi.|
  |**Kullanıcı İzin Ver**<sup>\*</sup>|`SFV:SFE`|Gönderen kullanıcının Kasa Gönderenler listesinde olduğundan ileti istenmeyen posta filtrelemeyi atladı.|
  |**Kullanıcı Bloğu**<sup>\*\*</sup>|`SFV:BLK`|Gönderen kullanıcının Engellenen Gönderenler listesinde olduğundan ileti istenmeyen posta filtrelemesi tarafından engellendi.|
  |**ZAP**|yok|[Sıfır saatlik otomatik temizleme (ZAP),](zero-hour-auto-purge.md) teslim edilen iletiyi Gereksiz E-posta klasörüne veya karantinaya almaya taşıdı. Eylemi [istenmeyen posta önleme ilkelerinde](configure-your-spam-filter-policies.md) yapılandırabilirsiniz.|

  <sup>\*</sup> İzin verilen ileti büyük olasılıkla hizmet tarafından engellenmiş olabileceğinden istenmeyen posta önleme ilkelerinizi gözden geçirin.

  <sup>\*\*</sup> İstenmeyen posta önleme ilkelerinizi gözden geçirin çünkü bu iletiler teslim edilmeden karantinaya alınmalıdır.

- **İleti hedefleri**: Kullanıcılar iletideki yük URL'sine tıklamamış olsalar bile alıcılara (Gelen Kutusu veya Gereksiz E-posta klasörüne) teslim edilen iletileri araştırmak isteyebilirsiniz. Karantinaya alınan iletileri de karantinadan kaldırabilirsiniz. Daha fazla bilgi için bkz. [EOP'de karantinaya alınan e-posta iletileri](quarantine-email-messages.md).
  - **Klasör silindi**
  - **Düştü**
  - **Dış**: Alıcı, karma ortamlarda şirket içi e-posta kuruluşunuzda bulunur.
  - **Başarısız**
  - **Iletilen**
  - **Gelen kutusu**
  - **Gereksiz klasör**
  - **Karantina**
  - **Unknown**

- **URL tıklamaları**: Bu değerler sonraki bölümde açıklanmıştır.

> [!NOTE]
> 10'dan fazla öğe içeren tüm katmanlarda ilk 10 öğe gösterilirken, geri kalanlar **Diğerleri'nde** birlikte paketlenir.

#### <a name="url-clicks"></a>URL tıklamaları

Bir kimlik avı iletisi alıcının Gelen Kutusu veya Gereksiz E-posta klasörüne teslim edildiğinde, kullanıcının yük URL'sine tıklama olasılığı her zaman vardır. URL'ye tıklamamak küçük bir başarı ölçüsüdür, ancak kimlik avı iletisinin neden posta kutusuna teslim edildiğine karar vermeniz gerekir.

Bir kullanıcı kimlik avı iletisindeki yük URL'sine tıkladıysa, eylemler kampanya ayrıntıları görünümünde diyagramın **URL tıklamaları** alanında görüntülenir.

- **Izin verilen**
- **BlockPage**: Alıcı yük URL'sine tıkladı, ancak kötü amaçlı web sitesine erişimi kuruluşunuzdaki [bir Kasa Bağlantıları](safe-links.md) ilkesi tarafından engellendi.
- **BlockPageOverride**: Alıcı iletideki yük URL'sine tıkladı Kasa Bağlantılar bunları durdurmaya çalıştı, ancak bloğu geçersiz kılmalarına izin verildi. Kullanıcıların neden Kasa Bağlantıları kararını geçersiz kılıp kötü amaçlı web sitesine devam etmelerine izin verilip verilmediğini görmek için Kasa [Bağlantıları ilkelerinizi](set-up-safe-links-policies.md) inceleyin.
- **PendingDetonationPage**: Office 365 için Microsoft Defender Kasa Ekleri, sanal bilgisayar ortamında yük URL'sini açma ve araştırma aşamasındadır.
- **PendingDetonationPageOverride**: Alıcının yük boşaltma işlemini geçersiz kılıp sonuçları beklemeden URL'yi açmasına izin verildi.

### <a name="tabs"></a>Sekme

Kampanya ayrıntıları görünümündeki sekmeler, kampanyayı daha fazla araştırmanıza olanak sağlar.

> [!TIP]
> Sekmelerde görüntülenen bilgiler, [Kampanya bilgileri](#campaign-information) bölümünde açıklandığı gibi zaman çizelgesindeki tarih aralığı filtresi tarafından denetlenmektedir.

- **URL tıklamaları**: Kullanıcılar iletideki yük URL'sine tıklamadıysa, bu bölüm boş olur. Kullanıcı URL'ye tıklayabildiyse aşağıdaki değerler doldurulur:
  - **Kullanıcı**<sup>\*</sup>
  - **URL**<sup>\*</sup>
  - **Tıklama zamanı**
  - **Karara tıklayın**

- **Gönderen IP'leri**
  - **Gönderen IP'i**<sup>\*</sup>
  - **Toplam sayı**
  - **Gelen Kutusu**
  - **Gelen Kutusu Yok**
  - **SPF geçti**: Gönderenin kimliği [Sender Policy Framework (SPF)](how-office-365-uses-spf-to-prevent-spoofing.md) tarafından doğrulandı. SPF doğrulamasını geçmeyen bir gönderen kimliği doğrulanmamış bir göndereni veya iletinin geçerli bir göndereni yanılttığını gösterir.

- **Gönderenler**
  - **Gönderen**: Bu, SMTP MAIL FROM komutundaki gerçek gönderen adresidir ve bu, kullanıcıların e-posta istemcilerinde gördüğü Kimden: e-posta adresi olmayabilir.
  - **Toplam sayı**
  - **Gelen Kutusu**
  - **Gelen Kutusu Yok**
  - **DKIM geçirildi**: Gönderenin kimliği [Etki Alanı Anahtarları Tanımlanan Posta (DKIM)](support-for-validation-of-dkim-signed-messages.md) tarafından doğrulandı. DKIM doğrulamasını geçmeyen bir gönderen kimliği doğrulanmamış bir göndereni veya iletinin geçerli bir göndereni yanılttığını gösterir.
  - **DMARC geçti**: Gönderenin kimliği [Etki Alanı Tabanlı İleti Kimlik Doğrulaması, Raporlama ve Uyumluluk (DMARC)](use-dmarc-to-validate-email.md) tarafından doğrulandı. DMARC doğrulamasını geçmeyen bir gönderen kimliği doğrulanmamış bir göndereni veya iletinin geçerli bir göndereni yanılttığını gösterir.

- **Ekler**
  - **Dosyaadı**
  - **SHA256**
  - **Kötü amaçlı yazılım ailesi**
  - **Toplam sayı**

- **URL**
  - **URL**<sup>\*</sup>
  - **Toplam Sayı**

<sup>\*</sup> Bu değere tıklanması, kampanya ayrıntıları görünümünün üstünde belirtilen öğe (kullanıcı, URL vb.) hakkında daha fazla ayrıntı içeren yeni bir açılır öğe açar. Kampanya ayrıntıları görünümüne dönmek için yeni açılır pencerede **Bitti'ye** tıklayın.

### <a name="buttons"></a>Düğme

Kampanya ayrıntıları görünümünün altındaki düğmeler, kampanyayla ilgili ayrıntıları araştırmanıza ve kaydetmenize olanak sağlar:

- **İletileri keşfetme**: Kampanyayı daha fazla araştırmak için Tehdit Gezgini'nin gücünü kullanın:
  - **Tüm iletiler**: Arama filtresi olarak **Kampanya Kimliği** değerini kullanarak yeni bir Tehdit Gezgini arama sekmesi açar.
  - **Gelen kutusu iletileri**: Arama filtresi olarak **Kampanya Kimliği** ve **Teslim konumu: Gelen Kutusu'nu** kullanarak yeni bir Tehdit Gezgini arama sekmesi açar.
  - **İç iletiler**: Arama filtresi olarak **Kampanya Kimliği** ve **Yön: Kuruluş içi'ni** kullanarak yeni bir Tehdit Gezgini arama sekmesi açar.

- **Tehdit raporunu indirme**: Kampanya ayrıntılarını bir Word belgesine indirin (varsayılan olarak CampaignReport.docx adlı). İndirme işleminin kampanyanın tüm ömrü boyunca (yalnızca seçtiğiniz filtre tarihlerine değil) ilişkin ayrıntıları içerdiğini unutmayın.
