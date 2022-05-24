---
title: Tehdit Gezgini ve Gerçek zamanlı algılamalar
f1.keywords:
- NOCSH
ms.author: tracyp
author: msfttracyp
manager: dansimp
audience: ITPro
ms.topic: article
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.assetid: 82ac9922-939c-41be-9c8a-7c75b0a4e27d
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
description: Tehditleri verimli bir şekilde araştırmak ve yanıtlamak için Microsoft 365 Defender portalında Gezgin ve Gerçek zamanlı algılamaları kullanın.
ms.custom:
- seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 0920439345b026879b86ad3b2ce104d3ea8174d1
ms.sourcegitcommit: 725a92b0b1555572b306b285a0e7a7614d34e5e5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/24/2022
ms.locfileid: "65649449"
---
# <a name="threat-explorer-and-real-time-detections"></a>Tehdit Gezgini ve Gerçek zamanlı algılamalar

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Uygulandığı öğe**
- [Office 365 için Microsoft Defender plan 1 ve plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Kuruluşunuzun [Office 365 için Microsoft Defender](defender-for-office-365.md) varsa ve [gerekli izinlere](#required-licenses-and-permissions) sahipseniz **, Gezgin** veya **Gerçek zamanlı algılamalarınız** (eski *adıyla Gerçek zamanlı raporlar*— [yeniliklere bakın](#new-features-in-threat-explorer-and-real-time-detections)!) vardır. Güvenlik & Uyumluluk Merkezi'nde **Tehdit yönetimi'ne** gidin ve **gezgin** _veya_ **gerçek zamanlı algılamalar'ı** seçin.

|Office 365 için Microsoft Defender Plan 2 ile şunları görürsünüz:|Office 365 için Microsoft Defender Plan 1 ile şunları görürsünüz:|
|---|---|
|![Tehdit gezgini.](../../media/threatmgmt-explorer.png)|![Gerçek zamanlı algılamalar](../../media/threatmgmt-realtimedetections.png)|

Explorer veya Gerçek zamanlı algılamalar, güvenlik operasyonları ekibinizin tehditleri verimli bir şekilde araştırmasına ve yanıtlamasına yardımcı olur. Rapor aşağıdaki görüntüye benzer:

:::image type="content" source="../../media/cab32fa2-66f1-4ad5-bc1d-2bac4dbeb48c.png" alt-text="Güvenlik & Uyumluluk portalındaki Gezgin menü öğesi" lightbox="../../media/cab32fa2-66f1-4ad5-bc1d-2bac4dbeb48c.png":::

Bu raporla şunları yapabilirsiniz:

- [Microsoft 365 güvenlik özellikleri tarafından algılanan kötü amaçlı yazılımlara bakın](#see-malware-detected-in-email-by-technology)
- [Kimlik avı URL'sini görüntüleyin ve karar verilerine tıklayın](#view-phishing-url-and-click-verdict-data)
- [Gezgin'deki bir görünümden otomatik araştırma ve yanıt işlemi başlatma](#start-automated-investigation-and-response) (yalnızca Plan 2 Office 365 için Defender)
- [Kötü amaçlı e-postaları ve daha fazlasını araştırma](#more-ways-to-use-explorer-and-real-time-detections)

## <a name="improvements-to-threat-hunting-experience"></a>Tehdit Avcılığı Deneyiminde İyileştirmeler

### <a name="introduction-of-alert-id-for-defender-for-office-365-alerts-within-explorerreal-time-detections"></a>Gezgin/Gerçek zamanlı algılamalar içindeki Office 365 için Defender uyarıları için Uyarı Kimliği'ne giriş

Bugün bir uyarıdan Tehdit Gezgini'ne giderseniz, gezgin içinde, görünüm Uyarı ilkesi kimliğine göre filtrelenmiş bir görünüm açar (ilke kimliği, Uyarı ilkesi için benzersiz bir tanımlayıcıdır).
Tehdit Gezgini'nde uyarı kimliğini (aşağıdaki uyarı kimliği örneğine bakın) ve belirli bir uyarıyla ilgili iletileri ve e-posta sayısını görebilmeniz için gerçek zamanlı algılamaları tanıtarak bu tümleştirmeyi daha uygun hale getiriyoruz. Ayrıca bir iletinin bir uyarının parçası olup olmadığını görebilir ve bu iletiden belirli bir uyarıya gidebilirsiniz.

Uyarı kimliği, tek bir uyarıyı görüntülerken URL'nin içinde kullanılabilir; örneğidir `https://protection.office.com/viewalerts?id=372c9b5b-a6c3-5847-fa00-08d8abb04ef1`.

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/AlertID-Filter.png" alt-text="Uyarı Kimliği için Filtreleme" lightbox="../../media/AlertID-Filter.png":::

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/AlertID-DetailsFlyout.png" alt-text="Ayrıntılı açılır öğede Uyarı Kimliği" lightbox="../../media/AlertID-DetailsFlyout.png":::

### <a name="extending-the-explorer-and-real-time-detections-data-retention-and-search-limit-for-trial-tenants-from-7-to-30-days"></a>Gezgin (ve Gerçek zamanlı algılamalar) veri saklama ve deneme kiracıları için arama sınırını 7 günden 30 güne genişletme

Bu değişikliğin bir parçası olarak, Hem Office için Defender P1 hem de P2 deneme kiracıları için Tehdit Gezgini'nde/Gerçek zamanlı algılamalarda e-posta verilerini 30 gün boyunca (önceki 7 güne göre bir artış) arayabilir ve filtreleyebilirsiniz.
Bu, hem P1 hem de P2/E5 müşterileri için 30 günlük veri saklama ve arama özelliklerine sahip olan üretim kiracılarını etkilemez.

### <a name="updated-limits-for-export-of-records-for-threat-explorer"></a>Tehdit Gezgini için kayıtları dışarı aktarma sınırları güncelleştirildi

Bu güncelleştirmenin bir parçası olarak, Tehdit Gezgini'nden dışarı aktarılabilir E-posta kayıtlarının satır sayısı 9990'dan 200.000 kayda artırılır. Şu anda dışarı aktarılabilir sütun kümesi aynı kalır, ancak satır sayısı geçerli sınırdan artacaktır.

### <a name="tags-in-threat-explorer"></a>Tehdit Gezgini'ndeki etiketler

> [!NOTE]
> Kullanıcı etiketleri özelliği *Önizleme* aşamasındadır, herkes tarafından kullanılamaz ve değiştirilebilir. Yayın zamanlaması hakkında bilgi için Microsoft 365 yol haritasına göz atın.

Kullanıcı etiketleri, Office 365 için Microsoft Defender'daki belirli kullanıcı gruplarını tanımlar. Lisanslama ve yapılandırma dahil olmak üzere etiketler hakkında daha fazla bilgi için bkz. [Kullanıcı etiketleri](user-tags.md).

Tehdit Gezgini'nde aşağıdaki deneyimlerde kullanıcı etiketleri hakkındaki bilgileri görebilirsiniz.

#### <a name="email-grid-view"></a>E-posta kılavuzu görünümü

E-posta kılavuzundaki **Etiketler** sütunu, gönderen veya alıcı posta kutularına uygulanmış olan tüm etiketleri içerir. Varsayılan olarak, önce öncelik hesapları gibi sistem etiketleri gösterilir.

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/tags-grid.png" alt-text="E-posta kılavuzu görünümünde etiketleri filtrele" lightbox="../../media/tags-grid.png":::

#### <a name="filtering"></a>Filtreleme

Etiketleri filtre olarak kullanabilirsiniz. Öncelikli hesaplarda veya belirli kullanıcı etiketleri senaryolarında avlanır. Ayrıca, belirli etiketlere sahip sonuçları dışlayabilirsiniz. Araştırma kapsamınızı daraltmak için bu işlevi diğer filtrelerle birleştirin.

[![Etiketleri filtreleyin.](../../media/tags-filter-normal.png)](../../media/tags-filter-normal.png#lightbox)

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/tags-filter-not.png" alt-text="Filtrelenmemiş etiketler" lightbox="../../media/tags-filter-not.png":::

#### <a name="email-detail-flyout"></a>E-posta ayrıntıları açılır öğesi

Gönderenin ve alıcının etiketlerini tek tek görüntülemek için konuyu seçerek ileti ayrıntıları açılır öğesini açın. **Özet** sekmesinde, e-posta için varsa gönderen ve alıcı etiketleri ayrı olarak gösterilir.
Gönderen ve alıcıya yönelik tek tek etiketlerle ilgili bilgiler, bu ayrıntıları iki ayrı sütunda görebileceğiniz dışarı aktarılan CSV verilerine de genişletilir.

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/tags-flyout.png" alt-text="E-posta Ayrıntıları etiketleri" lightbox="../../media/tags-flyout.png":::

Etiket bilgileri, URL tıklamaları açılır öğesinde de gösterilir. Bunu görüntülemek için Kimlik Avı veya Tüm E-posta görünümüne ve ardından **URL'ler** veya **URL Tıklamaları** sekmesine gidin. Tek bir URL açılır öğesini seçerek ilgili URL'ye yönelik tıklamalar hakkında, bu tıklamayla ilişkili etiketler de dahil olmak üzere ek ayrıntıları görüntüleyin.

### <a name="updated-timeline-view"></a>Güncelleştirilmiş Zaman Çizelgesi Görünümü

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/tags-urls.png" alt-text="URL etiketleri" lightbox="../../media/tags-urls.png":::
>
[Bu videoyu](https://www.youtube.com/watch?v=UoVzN0lYbfY&list=PL3ZTgFEc7LystRja2GnDeUFqk44k7-KXf&index=4) izleyerek daha fazla bilgi edinin.

## <a name="improvements-to-the-threat-hunting-experience-upcoming"></a>Tehdit avcılığı deneyiminde iyileştirmeler (yaklaşan)

### <a name="updated-threat-information-for-emails"></a>E-postalar için güncelleştirilmiş tehdit bilgileri

E-posta kayıtlarında veri doğruluğunu ve tutarlılığını artırmak için platform ve veri kalitesi iyileştirmelerine odaklandık. geliştirmeler arasında, ZAP işleminin bir parçası olarak bir e-postada yürütülen eylemler gibi teslim öncesi ve teslim sonrası bilgilerin tek bir kayıtta birleştirilmesi yer alır. İstenmeyen posta kararı, varlık düzeyinde tehditler (örneğin, hangi URL'nin kötü amaçlı olduğu) ve en son teslim konumları gibi ek ayrıntılar da dahildir.

Bu güncelleştirmelerden sonra, iletiyi etkileyen farklı teslim sonrası olaylarından bağımsız olarak her ileti için tek bir giriş görürsünüz. Eylemler ARASıNDA ZAP, el ile düzeltme (yönetici eylemi anlamına gelir), [Dinamik Teslim](safe-attachments.md#dynamic-delivery-in-safe-attachments-policies) vb. bulunabilir.

Kötü amaçlı yazılım ve kimlik avı tehditlerini göstermenin yanı sıra, e-postayla ilişkili istenmeyen posta kararını görürsünüz. E-postanın içinde, ilgili algılama teknolojileriyle birlikte e-postayla ilişkili tüm tehditlere bakın. Bir e-postanın sıfır, bir veya birden çok tehdidi olabilir. Geçerli tehditleri e-posta açılır öğesinin **Ayrıntılar** bölümünde görürsünüz. Birden çok tehdit (kötü amaçlı yazılım ve kimlik avı gibi) için **Algılama teknolojisi** alanı, tehdidi tanımlayan algılama teknolojisi olan tehdit algılama eşlemesini gösterir.

Algılama teknolojileri kümesi artık yeni algılama yöntemlerinin yanı sıra istenmeyen posta algılama teknolojilerini de içerir. Sonuçları farklı e-posta görünümlerinde (Kötü Amaçlı Yazılım, Kimlik Avı, Tüm E-postalar) filtrelemek için aynı algılama teknolojileri kümesini kullanabilirsiniz.

> [!NOTE]
> Karar çözümlemesi varlıklara bağlı olmayabilir. Örneğin, bir e-posta kimlik avı veya istenmeyen posta olarak sınıflandırılabilir, ancak kimlik avı/istenmeyen posta kararıyla damgalanmış URL'ler yoktur. Bunun nedeni, filtrelerin bir karar atamadan önce e-postanın içeriğini ve diğer ayrıntılarını da değerlendirmesidir.

#### <a name="threats-in-urls"></a>URL'lerdeki tehditler

Artık e-posta açılır öğesi **Ayrıntıları** sekmesinde url için belirli bir tehdidi görebilirsiniz. Tehdit *kötü amaçlı yazılım*, *kimlik avı*, *istenmeyen posta* veya *hiçbiri* olabilir.)

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/URL_Threats.png" alt-text="URL tehditleri" lightbox="../../media/URL_Threats.png":::

### <a name="updated-timeline-view-upcoming"></a>Güncelleştirilmiş zaman çizelgesi görünümü (yaklaşan)

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/Email_Timeline.png" alt-text="Güncelleştirilmiş Zaman Çizelgesi Görünümü" lightbox="../../media/Email_Timeline.png":::

Zaman çizelgesi görünümü tüm teslim ve teslim sonrası olayları tanımlar. Bu olayların bir alt kümesi için o zaman noktasında tanımlanan tehdit hakkında bilgiler içerir. Zaman çizelgesi görünümü ayrıca gerçekleştirilen ek eylemler (ZAP veya el ile düzeltme gibi) ve bu eylemin sonucu hakkında bilgi sağlar. Zaman çizelgesi görünümü bilgileri şunları içerir:

- **Kaynak:** Olayın kaynağı. Yönetici/sistem/kullanıcı olabilir.
- **Olay:** Orijinal teslimat, el ile düzeltme, ZAP, gönderimler ve Dinamik Teslim gibi üst düzey olayları içerir.
- **Eylem:** ZAP veya yönetici eyleminin bir parçası olarak gerçekleştirilen belirli eylem (örneğin, geçici silme).
- **Tehdit:** Bu noktada tanımlanan tehditleri (kötü amaçlı yazılım, kimlik avı, istenmeyen posta) kapsar.
- **Sonuç/Ayrıntılar:** Eylemin sonucu hakkında daha fazla bilgi, örneğin ZAP/yönetici eyleminin bir parçası olarak gerçekleştirilip gerçekleştirilmediği.

### <a name="original-and-latest-delivery-location"></a>Orijinal ve en son teslimat konumu

Şu anda teslim konumunu e-posta kılavuzunda ve e-posta açılır öğesinde kullanıma sunacağız. **Teslim konumu** alanı **_Özgün teslimat konumu_ _ olarak yeniden adlandırılıyor *. Ve _*_Latest teslimat konumu_ olarak başka bir alan sunuyoruz**.

**Özgün teslimat konumu** , başlangıçta bir e-postanın teslim edildiği yer hakkında daha fazla bilgi verir. **En son teslim konumu** , *ZAP* gibi sistem eylemleri veya *Silinmiş öğelere taşı* gibi yönetici eylemlerinin ardından bir e-postanın geldiği yeri belirtir. En son teslim konumu, iletinin son bilinen konumunu teslim sonrasında veya sistem/yönetici eylemleriyle ilgili olarak yöneticilere bildirmek için tasarlanmıştır. E-postada son kullanıcı eylemleri yoktur. Örneğin, bir kullanıcı bir iletiyi sildiyse veya iletiyi arşive/pst'ye taşıdıysa, iletinin "teslim" konumu güncelleştirilmez. Ancak bir sistem eylemi konumu güncelleştirdiyse (örneğin, ZAP karantinaya alınan bir e-postayla sonuçlanırsa), **en son teslim konumu** "karantina" olarak gösterilir.

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/Updated_Delivery_Location.png" alt-text="Güncelleştirilmiş teslim konumları" lightbox="../../media/Updated_Delivery_Location.png":::

> [!NOTE]
> **Teslim konumu** ve **Teslim eyleminin** "bilinmeyen" olarak gösterebileceği birkaç durum vardır:
>
> - İleti teslim edildiyse **Teslim konumu** "teslim edildi" ve **Teslim konumu** "bilinmiyor" olarak görünebilir, ancak Gelen Kutusu kuralı iletiyi Gelen Kutusu veya Gereksiz E-posta klasörü yerine varsayılan bir klasöre (Taslak veya Arşiv gibi) taşıdı.
>
> - Bir yönetici/sistem eylemi (ZAP gibi) denendiyse ancak ileti bulunamadıysa **en son teslim konumu** bilinmiyor olabilir. Eylem genellikle kullanıcı iletiyi taşıdıktan veya sildikten sonra gerçekleşir. Bu gibi durumlarda, zaman çizelgesi görünümünde **Sonuç/Ayrıntılar** sütununu doğrulayın. "İleti kullanıcı tarafından taşındı veya silindi" deyimini arayın.

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/Updated_Timeline_Delivery_Location.png" alt-text="Zaman çizelgesi için teslim konumları" lightbox="../../media/Updated_Timeline_Delivery_Location.png":::

### <a name="additional-actions"></a>Ek eylemler

E-posta teslim edildikten sonra *ek eylemler* uygulandı. *Zap*, *el ile düzeltme* (geçici silme gibi bir Yönetici tarafından gerçekleştirilen eylem), *Dinamik Teslim* ve *yeniden işlenebilir* (geriye dönük olarak iyi olarak algılanan bir e-posta için).

> [!NOTE]
> Bekleyen değişikliklerin bir parçası olarak, Şu anda Teslim Eylemi filtresinde gösterilen "ZAP tarafından kaldırıldı" değeri kaybolur. **Ek eylemler** aracılığıyla ZAP denemesiyle tüm e-postaları aramanın bir yolunu bulacaksınız.

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/Additional_Actions.png" alt-text="Gezgin'deki ek eylemler" lightbox="../../media/Additional_Actions.png":::

### <a name="system-overrides"></a>Sistem geçersiz kılmaları

*Sistem geçersiz kılmaları* , bir iletinin hedeflenen teslim konumunda özel durumlar oluşturmanıza olanak tanır. Sistem tarafından sağlanan teslim konumunu, filtreleme yığını tarafından tanımlanan tehditlere ve diğer algılamalara göre geçersiz kılarsınız. Sistem geçersiz kılmaları, ilke tarafından önerilen iletiyi teslim etmek için kiracı veya kullanıcı ilkesi aracılığıyla ayarlanabilir. Geçersiz kılmalar, kullanıcı tarafından ayarlanan çok geniş bir Kasa Gönderen ilkesi gibi yapılandırma boşlukları nedeniyle kötü amaçlı iletilerin yanlışlıkla teslimini belirleyebilir. Bu geçersiz kılma değerleri şunlar olabilir:

- Kullanıcı ilkesi tarafından izin verilir: Kullanıcı, etki alanlarına veya gönderenlere izin vermek için posta kutusu düzeyinde ilkeler oluşturur.

- Kullanıcı ilkesi tarafından engellendi: Kullanıcı, etki alanlarını veya gönderenleri engellemek için posta kutusu düzeyinde ilkeler oluşturur.

- Kuruluş ilkesi tarafından izin verilir: Kuruluşun güvenlik ekipleri, kuruluştaki kullanıcılar için gönderenlere ve etki alanlarına izin vermek için ilkeler veya Exchange posta akışı kuralları (taşıma kuralları olarak da bilinir) ayarlar. Bu, bir kullanıcı kümesi veya kuruluşun tamamı için olabilir.

- Kuruluş ilkesi tarafından engellendi: Kuruluşun güvenlik ekipleri, kuruluşlarındaki kullanıcılar için gönderenleri, etki alanlarını, ileti dillerini veya kaynak IP'leri engellemek için ilkeler veya posta akışı kuralları ayarlar. Bu, bir kullanıcı kümesine veya kuruluşun tamamına uygulanabilir.

- Kuruluş ilkesi tarafından engellenen dosya uzantısı: Kuruluşun güvenlik ekibi, kötü amaçlı yazılımdan koruma ilkesi ayarları aracılığıyla bir dosya adı uzantısını engeller. Bu değerler artık araştırmalara yardımcı olmak için e-posta ayrıntılarında görüntülenecektir. Secops ekipleri, engellenen dosya uzantılarını filtrelemek için zengin filtreleme özelliğini de kullanabilir.

[![Gezgin'de Sistem Geçersiz Kılmaları.](../../media/System_Overrides.png)](../../media/System_Overrides.png#lightbox)

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/System_Overrides_Grid.png" alt-text="Explorer'da Sistem Geçersiz Kılma kılavuzu" lightbox="../../media/System_Overrides_Grid.png":::

### <a name="improvements-for-the-url-and-clicks-experience"></a>URL ve tıklama deneyimi için iyileştirmeler

Geliştirmeler şunlardır:

- URL açılır öğesinin **Tıklamalar** bölümünde tam tıklanan URL'yi (URL'nin parçası olan tüm sorgu parametreleri dahil) gösterin. Şu anda URL etki alanı ve yolu başlık çubuğunda görünür. Tüm URL'yi göstermek için bu bilgileri genişletiyoruz.

- URL filtreleri (*URL* ve *URL etki alanı ile URL etki alanı* *ve yolu* arasındaki düzeltmeler): Güncelleştirmeler, URL/tıklama kararı içeren iletileri aramayı etkiler. kullanmadan `http`URL araması yapabilmeniz için protokol belirsiz aramaları için desteği etkinleştirdik. Varsayılan olarak, başka bir değer açıkça belirtilmediği sürece URL araması http ile eşler. Örneğin:
  - **URL**, **URL Etki Alanı ve URL Etki Alanı** ile **Yol** filtresi alanlarında ön ek olmadan `http://` ve ile arama. Aramalar aynı sonuçları göstermelidir.
  - URL'de `https://` ön eki arayın. Değer belirtilmediğinde ön `http://` ek varsayılır.
  - `/`**URL yolu, URL** **Etki Alanı, URL** **etki alanı ve yol** alanlarının başında ve sonunda yoksayılır. `/`**url** alanının sonunda yoksayılır.

### <a name="phish-confidence-level"></a>Kimlik avı güvenilirlik düzeyi

Kimlik avı güvenilirlik düzeyi, bir e-postanın "kimlik avı" olarak kategorize edildiği güven derecesini belirlemeye yardımcı olur. İki olası değer *Yüksek* ve *Normal'dir*. İlk aşamalarda, bu filtre yalnızca Tehdit Gezgini'nin Kimlik Avı görünümünde kullanılabilir.

[![Explorer'da Kimlik Avı Güven Düzeyi.](../../media/Phish_Confidence_Level.png)](../../media/Phish_Confidence_Level.png#lightbox)

### <a name="zap-url-signal"></a>ZAP URL sinyali

ZAP URL sinyali genellikle bir e-postanın Kimlik Avı olarak tanımlandığı ve teslimden sonra kaldırıldığı ZAP Kimlik Avı uyarı senaryoları için kullanılır. Bu sinyal, uyarıyı Gezgin'deki ilgili sonuçlara bağlar. Uyarının GÇC'lerinden biridir.

Tehdit Avcılığı sürecini geliştirmek için Tehdit Gezgini'ni ve Gerçek zamanlı algılamaları, tehdit avcılığı deneyimini daha tutarlı hale getirmek üzere güncelleştirdik. Değişiklikler burada özetlenmiştir:

- [Saat dilimi iyileştirmeleri](#timezone-improvements)
- [Yenileme işleminde güncelleştirme](#update-in-the-refresh-process)
- [Filtrelere eklenecek grafik detayına gitme](#chart-drilldown-to-add-to-filters)
- [Ürün bilgileri güncelleştirmelerinde](#in-product-information-updates)

### <a name="filter-by-user-tags"></a>Kullanıcı etiketlerine göre filtreleme

Artık tehditlerin kapsamını hızla kavramak için sistem veya özel kullanıcı etiketlerini sıralayabilir ve filtreleyebilirsiniz. Daha fazla bilgi için bkz. [Kullanıcı etiketleri](user-tags.md).

> [!IMPORTANT]
> Kullanıcı etiketlerine göre filtreleme ve sıralama şu anda genel önizleme aşamasındadır. Bu işlev ticari olarak piyasaya sürülmeden önce önemli ölçüde değiştirilebilir. Microsoft, bu konuda sağlanan bilgilerle ilgili olarak açık veya zımni hiçbir garanti vermez.

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/threat-explorer-tags.png" alt-text="Gezgin'deki Etiketler sütunu" lightbox="../../media/threat-explorer-tags.png":::

### <a name="timezone-improvements"></a>Saat dilimi iyileştirmeleri

Portalda e-posta kayıtlarının ve dışarı aktarılan verilerin saat dilimini görürsünüz. E-posta Kılavuzu, Ayrıntılar açılır öğesi, E-posta Zaman Çizelgesi ve Benzer E-postalar gibi deneyimlerde görünür, böylece sonuç kümesinin saat dilimi net olur.

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/TimezoneImprovements.png" alt-text="Gezgin'de saat dilimini görüntüleme" lightbox="../../media/TimezoneImprovements.png":::

### <a name="update-in-the-refresh-process"></a>Yenileme işleminde güncelleştirme

Bazı kullanıcılar otomatik yenileme (örneğin, tarihi değiştirdiğiniz anda sayfa yenilenir) ve el ile yenileme (diğer filtreler için) ile ilgili kafa karışıklığı hakkında yorumda bulunmşlardır. Benzer şekilde, filtrelerin kaldırılması otomatik yenilemeye yol açar. Sorguyu değiştirirken filtrelerin değiştirilmesi tutarsız arama deneyimlerine neden olabilir. Bu sorunları çözmek için el ile filtreleme mekanizmasına geçiyoruz.

Deneyim açısından, kullanıcı farklı filtre aralığını (filtre kümesinden ve tarihten) uygulayabilir ve kaldırabilir ve sorguyu tanımladıktan sonra sonuçları filtrelemek için yenile düğmesini seçebilir. Yenile düğmesi de artık ekranda vurgulanmıştır. Ayrıca ilgili araç ipuçlarını ve ürün içi belgeleri güncelleştirdik.

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/ManualRefresh.png" alt-text="Sonuçları filtrelemek için Yenile düğmesi" lightbox="../../media/ManualRefresh.png":::

### <a name="chart-drilldown-to-add-to-filters"></a>Filtrelere eklenecek grafik detayına gitme

Artık gösterge değerlerini filtre olarak eklemek için grafik oluşturabilirsiniz. Sonuçları filtrelemek için **Yenile** düğmesini seçin.

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/ChartDrilldown.png" alt-text="Filtre uygulamak için grafiklerde detaya gitme" lightbox="../../media/ChartDrilldown.png":::

### <a name="in-product-information-updates"></a>Ürün içi bilgi güncelleştirmeleri

Artık ürün içinde, kılavuzdaki arama sonuçlarının toplam sayısı gibi ek ayrıntılar sağlanır (aşağıya bakın). Filtreler, arama deneyimi ve sonuç kümesi hakkında daha fazla bilgi sağlamak için etiketleri, hata iletilerini ve araç ipuçlarını geliştirdik.

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/ProductInfo.png" alt-text="Görüntülenecek ürün içi bilgiler" lightbox="../../media/ProductInfo.png":::

## <a name="extended-capabilities-in-threat-explorer"></a>Tehdit Gezgini'ndeki genişletilmiş özellikler

### <a name="top-targeted-users"></a>En çok hedeflenen kullanıcılar

Bugün, E-postalar için Kötü Amaçlı Yazılım görünümünde en çok hedeflenen kullanıcıların listesini **En İyi Kötü Amaçlı Yazılım Aileleri** bölümünde kullanıma sunun. Bu görünümü Kimlik Avı ve Tüm E-posta görünümlerinde de genişleteceğiz. Hedeflenen ilk beş kullanıcıyı ve ilgili görünüm için her kullanıcı için deneme sayısını görebilirsiniz. Örneğin, Kimlik Avı görünümü için Kimlik Avı denemelerinin sayısını görürsünüz.

Hedeflenen kullanıcıların listesini, her e-posta görünümü için çevrimdışı çözümleme denemelerinin sayısıyla birlikte 3.000 sınırına kadar dışarı aktarabilirsiniz. Buna ek olarak, deneme sayısını seçtiğinizde (örneğin, aşağıdaki resimde 13 deneme) Tehdit Gezgini'nde filtrelenmiş bir görünüm açılır; böylece bu kullanıcıya yönelik e-postalar ve tehditler hakkında daha fazla ayrıntı görebilirsiniz.

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/Top_Targeted_Users.png" alt-text="En çok hedeflenen kullanıcılar" lightbox="../../media/Top_Targeted_Users.png":::

### <a name="exchange-transport-rules"></a>aktarım kurallarını Exchange

Veri zenginleştirmenin bir parçası olarak, iletiye uygulanan tüm farklı Exchange aktarım kurallarını (ETR) görebilirsiniz. Bu bilgiler E-posta kılavuzu görünümünde kullanılabilir. Bunu görüntülemek için kılavuzda **Sütun seçenekleri'ni** ve ardından sütun seçeneklerinden **Exchange Taşıma Kuralı Ekle'yi** seçin. Ayrıca e-postadaki **Ayrıntılar** açılır öğesinde de görünür.

İletiye uygulanan aktarım kurallarının hem GUID'sini hem de adını görebilirsiniz. Aktarım kuralının adını kullanarak iletileri arayabilirsiniz. Bu bir "İçerir" aramasıdır, yani kısmi aramalar da yapabilirsiniz.

> [!IMPORTANT]
> ETR arama ve ad kullanılabilirliği, size atanan belirli role bağlıdır. ETR adlarını görüntülemek ve arama yapmak için aşağıdaki rollerden/izinlerden birine sahip olmanız gerekir. Size bu rollerden herhangi biri atanmamışsa, aktarım kurallarının adlarını göremez veya ETR adlarını kullanarak iletileri arayamazsınız. Ancak E-posta Ayrıntıları'nda ETR etiketini ve GUID bilgilerini görebilirsiniz. E-posta Kılavuzları, E-posta açılırları, Filtreler ve Dışarı Aktarma'daki diğer kayıt görüntüleme deneyimleri etkilenmez.
>
> - Yalnızca EXO - veri kaybı önleme: Tümü
> - Yalnızca EXO - O365SupportViewConfig: Tümü
> - Microsoft Azure Active Directory veya EXO - Güvenlik Yönetici: Tümü
> - AAD veya EXO - Güvenlik Okuyucusu: Tümü
> - Yalnızca EXO - Aktarım Kuralları: Tümü
> - Yalnızca EXO - View-Only Yapılandırması: Tümü
>
> E-posta kılavuzu, Ayrıntılar açılır öğesi ve Dışarı Aktarılan CSV'nin içinde ETR'lere aşağıda gösterildiği gibi bir Ad/GUID gösterilir.
>
> > [!div class="mx-imgBorder"]
> > :::image type="content" source="../../media/ETR_Details.png" alt-text="Exchange aktarım kuralları" lightbox="../../media/ETR_Details.png":::

### <a name="inbound-connectors"></a>Gelen bağlayıcılar

Bağlayıcılar, e-postanızın Microsoft 365 veya Office 365 kuruluşunuzdan nasıl aktığını özelleştiren yönergelerden oluşan bir koleksiyondır. Tüm güvenlik kısıtlamalarını veya denetimlerini uygulamanıza olanak tanır. Tehdit Gezgini'nde artık bir e-postayla ilgili bağlayıcıları görüntüleyebilir ve bağlayıcı adlarını kullanarak e-postaları arayabilirsiniz.

Bağlayıcı aramasının doğası gereği "içerir" olması, kısmi anahtar sözcük aramalarının da işe yaraması gerektiği anlamına gelir. Ana kılavuz görünümünde, Ayrıntılar açılır öğesinde ve Dışarı Aktarılan CSV'de, bağlayıcılar burada gösterildiği gibi Ad/GUID biçiminde gösterilir:

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/Connector_Details.png" alt-text="Bağlayıcı ayrıntıları" lightbox="../../media/Connector_Details.png":::

## <a name="new-features-in-threat-explorer-and-real-time-detections"></a>Tehdit Gezgini'ndeki yeni özellikler ve Gerçek zamanlı algılamalar

- [Kimliğine bürünülen kullanıcılara ve etki alanlarına gönderilen kimlik avı e-postalarını görüntüleme](#view-phishing-emails-sent-to-impersonated-users-and-domains)
- [E-posta üst bilgisini önizleme ve e-posta gövdesini indirme](#preview-email-header-and-download-email-body)
- [E-posta zaman çizelgesi](#email-timeline)
- [URL tıklama verilerini dışarı aktarma](#export-url-click-data)

### <a name="view-phishing-emails-sent-to-impersonated-users-and-domains"></a>Kimliğine bürünülen kullanıcılara ve etki alanlarına gönderilen kimlik avı e-postalarını görüntüleme

Kimliğine bürünülen kullanıcılara ve etki alanlarına yönelik kimlik avı girişimlerini tanımlamak için *, korunacak Kullanıcılar* listesine eklenmelidir. Etki alanları için, yöneticilerin *Kuruluş etki alanlarını* etkinleştirmesi veya *korumak için Etki Alanları'na* bir etki alanı adı eklemesi gerekir. Korunacak etki alanları *Kimliğe Bürünme* bölümündeki *Kimlik Avı önleme ilkesi sayfasında* bulunur.

Kimlik avı iletilerini gözden geçirmek ve kimliğine bürünülen kullanıcıları veya etki alanlarını aramak için [Explorer'ın E-posta > Kimlik Avı görünümünü](threat-explorer-views.md) kullanın.

Bu örnekte Tehdit Gezgini kullanılır.

1. [Güvenlik & Uyumluluk Merkezi'nde](https://protection.office.com) (https://protection.office.com)Tehdit yönetimi > Gezgini'ni (veya Gerçek zamanlı algılamalar) seçin.

2. Görünüm menüsünde E-posta > Kimlik Avı'nı seçin.

   Burada **kimliğine bürünülen etki alanını** veya **kimliğine bürünülen kullanıcıyı** seçebilirsiniz.

3. **Kimliğine** **Bürünülen etki alanı'nı** seçin ve metin kutusuna korumalı bir etki alanı yazın.

   Örneğin *contoso,* *contoso.com* veya *contoso.com.au* gibi korumalı etki alanı adlarını arayın.

4. Kimliğe Bürünülen Etki Alanı / Algılanan konum gibi ek kimliğe bürünme bilgilerini görmek için E-posta sekmesinin > Ayrıntılar sekmesinin altındaki herhangi bir iletinin Konusu'nu seçin.

    **VEYA**

    **Kimliğine Bürünülen kullanıcı'ya** tıklayın ve metin kutusuna korumalı bir kullanıcının e-posta adresini yazın.

    > [!TIP]
    > **En iyi sonuçları elde** etmek için, korumalı kullanıcılarda arama yapmak için *tam e-posta adreslerini* kullanın. Örneğin, kullanıcı kimliğine bürünme işlemini araştırırken *firstname.lastname@contoso.com* ararsanız korunan kullanıcınızı daha hızlı ve daha başarılı bir şekilde bulabilirsiniz. Korumalı bir etki alanı ararken, arama kök etki alanını (örneğin contoso.com) ve etki alanı adını (*contoso*) alır. Kök etki alanı *contoso.com* aranırken hem *contoso.com* kimliğine bürünmeler hem de contoso etki alanı adı *döndürülecektir*.

5. Kullanıcı veya etki alanı hakkında ek kimliğe bürünme bilgilerini ve *Algılanan konumu* görmek için **E-posta** **sekmesiDetails** >  sekmesinin altındaki herhangi bir iletinin **Konusu'nu** seçin.

    :::image type="content" source="../../media/threat-ex-views-impersonated-user-image.png" alt-text="Algılama konumunu ve algılanan tehdidi gösteren korumalı bir kullanıcının Tehdit Gezgini ayrıntılar bölmesi (burada kullanıcının kimlik avı kimliğine bürünülmesi)" lightbox="../../media/threat-ex-views-impersonated-user-image.png":::

> [!NOTE]
> 3. veya 5. adımda **, Algılama Teknolojisi'ni** ve sırasıyla **Kimliğe Bürünme etki alanı** veya **Kimliğe Bürünme kullanıcısı'nı** seçerseniz, **E-posta sekmesinde** >  kullanıcı veya etki alanı hakkındaki **bilgiler Ve** *Algılanan konum* yalnızca *Kimlik Avı önleme ilkesi* sayfasında listelenen kullanıcı veya etki alanıyla ilgili iletilerde gösterilir.

### <a name="preview-email-header-and-download-email-body"></a>E-posta üst bilgisini önizleme ve e-posta gövdesini indirme

Artık bir e-posta üst bilgisini önizleyebilir ve e-posta gövdesini Tehdit Gezgini'nden indirebilirsiniz. Yöneticiler indirilen üst bilgileri/e-posta iletilerini tehditler için analiz edebilir. E-posta iletilerinin indirilmesi bilgilerin açığa çıkarılabileceğinden, bu işlem rol tabanlı erişim denetimi (RBAC) tarafından denetlenmektedir. E-postaları tüm e-posta iletileri görünümünde indirme olanağı vermek için yeni bir *Önizleme* rolü gereklidir. Ancak, e-posta üst bilgisini görüntülemek için ek rol gerekmez (Tehdit Gezgini'nde iletileri görüntülemek için gerekenler dışında). Önizleme rolüyle yeni bir rol grubu oluşturmak için:

1. Veri Araştırmacısı veya eBulma Yöneticisi gibi yalnızca Önizleme rolüne sahip yerleşik bir rol grubu seçin.
2. **Rol grubunu kopyala'yı** seçin.
3. Yeni rol grubunuz için bir ad ve açıklama seçin ve **İleri'yi** seçin.
4. Rolleri gerektiği gibi ekleyip kaldırarak ancak Önizleme rolünden ayrılarak rolleri değiştirin.
5. Üye ekleyin ve ardından **Rol grubu oluştur'u** seçin.

Explorer ve Gerçek zamanlı algılamalar, e-posta iletilerinizin nereye indiğini gösteren daha eksiksiz bir resim sağlayan yeni alanlar da alır. Bu değişiklikler, Güvenlik İşlemleri için avlanmayı kolaylaştırır. Ancak asıl sonuç, sorun e-posta iletilerinin konumunu bir bakışta öğrenebilmenizdir.

Bu nasıl yapılır? Teslim durumu artık iki sütuna ayrılmıştır:

- **Teslim eylemi** - E-postanın durumu.
- **Teslim konumu** - E-postanın yönlendirildiği yer.

*Teslim eylemi* , mevcut ilkeler veya algılamalar nedeniyle bir e-postada gerçekleştirilen eylemdir. E-posta için olası eylemler şunlardır:

|Teslim|Gereksiz|Engellenen|Değiştirilir|
|---|---|---|---|
|E-posta bir kullanıcının gelen kutusuna veya klasörüne teslim edildi ve kullanıcı bu e-postaya erişebilir.|Kullanıcının Gereksiz veya Silinmiş klasörüne e-posta gönderildi ve kullanıcı bu klasöre erişebilir.|Karantinaya alınan, başarısız olan veya bırakılan e-postalar. Bu postalara kullanıcı erişemez.|E-postanın kötü amaçlı ekleri, ekin kötü amaçlı olduğunu belirten .txt dosyalarıyla değiştirildi.|

Kullanıcının görebileceği ve göremeyecekleri şunlardır:

|Son kullanıcılar tarafından erişilebilir|Son kullanıcılara erişilemiyor|
|---|---|
|Teslim|Engellenen|
|Gereksiz|Değiştirilir|

**Teslim konumu** , teslim sonrası çalışan ilkelerin ve algılamaların sonuçlarını gösterir. **_Teslim eylemine_** bağlıdır. Olası değerler şunlardır:

- *Gelen kutusu veya klasör*: E-posta gelen kutusunda veya bir klasördedir (e-posta kurallarınıza göre).
- *Şirket içi veya dış*: Posta kutusu bulutta değil, şirket içindedir.
- *Gereksiz klasör*: E-posta kullanıcının Gereksiz klasöründedir.
- *Silinmiş öğeler klasörü*: Kullanıcının Silinmiş öğeler klasöründeki e-posta.
- *Karantina*: E-posta karantinada ve kullanıcının posta kutusunda değil.
- *Başarısız*: E-posta posta kutusuna ulaşamadı.
- *Bırakılan*: E-posta, posta akışında bir yerde kayboldu.

### <a name="email-timeline"></a>E-posta zaman çizelgesi

**E-posta zaman çizelgesi**, yöneticiler için tehdit avcılığı deneyimini geliştiren yeni bir Gezgin özelliğidir. Olayı anlamaya çalışmak için farklı konumları denetlemek için harcanan süreyi kısar. Bir e-posta geldiğinde birden çok olay gerçekleştiğinde veya yaklaştığında, bu olaylar zaman çizelgesi görünümünde görüntülenir. Teslim sonrası e-postanızda gerçekleşen bazı olaylar **Özel eylem** sütununda yakalanır. Yöneticiler, ilkelerin nasıl çalıştığı, postanın son olarak nereye yönlendirildiği ve bazı durumlarda son değerlendirmenin ne olduğu hakkında içgörü elde etmek için zaman çizelgesindeki bilgileri posta teslimi sonrasında gerçekleştirilen özel eylemle birleştirebilir.

Daha fazla bilgi için bkz[. Office 365'de teslim edilen kötü amaçlı e-postaları araştırma ve düzeltme](investigate-malicious-email-that-was-delivered.md).

### <a name="export-url-click-data"></a>URL tıklama verilerini dışarı aktarma

Artık URL tıklamalarının raporlarını dışarı aktararak Microsoft Excel **ağ iletisi kimliğini** görüntüleyebilir ve **karara tıklayabilirsiniz**. Bu da URL tıklama trafiğinizin nereden kaynaklandığını açıklamaya yardımcı olur. Şu şekilde çalışır: Office 365 hızlı başlatma çubuğundaki Tehdit Yönetimi'nde şu zinciri izleyin:

**Explorer** \> **Kimlik Avı** \> Görüntüle **Tıklama** \> **En çok kullanılan URL'ler** veya **URL Üst Tıklamalar**\>, URL açılır öğesini açmak için herhangi bir kaydı seçer.

Listeden bir URL seçtiğinizde açılır panelde yeni bir **Dışarı Aktar** düğmesi görürsünüz. Daha kolay raporlama için verileri Excel bir elektronik tabloya taşımak için bu düğmeyi kullanın.

Gerçek zamanlı algılamalar raporunda aynı konuma ulaşmak için bu yolu izleyin:

**Explorer** \> **Gerçek zamanlı algılamalar** \> **Kimlik Avı** \> Görüntüle **Url 'leri** \> **Üst URL'ler** veya **İlk Tıklamalar** \> URL açılır \> öğesini açmak için herhangi bir kayıt seçin **, Tıklamalar** sekmesine gidin.

> [!TIP]
> Ağ İletisi Kimliği, Gezgin veya ilişkili üçüncü taraf araçları aracılığıyla kimlikte arama yaptığınızda tıklamayı belirli postalarla eşler. Bu tür aramalar, tıklama sonucuyla ilişkili e-postayı tanımlar. Bağıntılı Ağ İletisi Kimliğinin olması daha hızlı ve daha güçlü bir analiz sağlar.

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/tp_ExportClickResultAndNetworkID.png" alt-text="Gezgin'de Tıklamalar sekmesi" lightbox="../../media/tp_ExportClickResultAndNetworkID.png":::

## <a name="see-malware-detected-in-email-by-technology"></a>Teknolojiye göre e-postada algılanan kötü amaçlı yazılımlara bakın

E-postada kötü amaçlı yazılımların algılanmasını Microsoft 365 teknolojiye göre sıralanmış olarak görmek istediğinizi varsayalım. Bunu yapmak için Explorer'ın (veya Gerçek zamanlı algılamaların) [E-posta > Kötü Amaçlı Yazılım](threat-explorer-views.md#email--malware) görünümünü kullanın.

1. Güvenlik & Uyumluluk Merkezi'nde (<https://protection.office.com> ) **Tehdit yönetimi** \> **Gezgini'ni** (veya **Gerçek zamanlı algılamalar**) seçin. (Bu örnekte Gezgin kullanılır.)

2. **Görünüm** menüsünde **E-posta** \> **Kötü Amaçlı Yazılım'ı** seçin.

   > [!div class="mx-imgBorder"]
   > :::image type="content" source="../../media/ExplorerViewEmailMalwareMenu.png" alt-text="Gezgin için Görünüm menüsü" lightbox="../../media/ExplorerViewEmailMalwareMenu.png":::

3. **Gönderen'e** tıklayın ve temel **algılama teknolojisi'ni** **seçin**\>.

   Algılama teknolojileriniz artık rapor için filtre olarak kullanılabilir.

   > [!div class="mx-imgBorder"]
   > :::image type="content" source="../../media/ExplorerEmailMalwareDetectionTech.png" alt-text="Kötü amaçlı yazılım algılama teknolojileri" lightbox="../../media/ExplorerEmailMalwareDetectionTech.png":::

4. Bir seçenek belirleyin. Ardından, bu filtreyi uygulamak için **Yenile** düğmesini seçin.

   > [!div class="mx-imgBorder"]
   > :::image type="content" source="../../media/ExplorerEmailMalwareDetectionTechATP.png" alt-text="Seçilen algılama teknolojisi" lightbox="../../media/ExplorerEmailMalwareDetectionTechATP.png":::

Rapor, seçtiğiniz teknoloji seçeneğini kullanarak kötü amaçlı yazılımların e-postada algıladığınız sonuçları gösterecek şekilde yenilenir. Buradan daha fazla analiz gerçekleştirebilirsiniz.

## <a name="view-phishing-url-and-click-verdict-data"></a>Kimlik avı URL'sini görüntüleyin ve karar verilerine tıklayın

İzin verilen, engellenen ve geçersiz kılınan URL'lerin listesi de dahil olmak üzere e-postadaki URL'ler aracılığıyla kimlik avı girişimlerini görmek istediğinizi varsayalım. Tıklanan URL'leri tanımlamak için [Kasa Bağlantıların](safe-links.md) yapılandırılması gerekir. [Kasa Bağlantıları ilkelerini](set-up-safe-links-policies.md) tıklama zamanı koruması ve Kasa Bağlantıları ile tıklama kararlarının günlüğe kaydedilmesi için ayarladığınızdan emin olun.

İletilerdeki kimlik avı URL'lerini gözden geçirmek ve kimlik avı iletilerindeki URL'lere tıklamak için Explorer'ın [**EmailPhish** > ](threat-explorer-views.md#email--phish) görünümünü veya Gerçek zamanlı algılamaları kullanın.

1. Güvenlik & Uyumluluk Merkezi'nde (<https://protection.office.com> ) **Tehdit yönetimi** \> **Gezgini'ni** (veya **Gerçek zamanlı algılamalar**) seçin. (Bu örnekte Gezgin kullanılır.)

2. **Görünüm** menüsünde **E-posta** \> **Kimlik Avı'nı** seçin.

   > [!div class="mx-imgBorder"]
   > :::image type="content" source="../../media/ExplorerViewEmailPhishMenu.png" alt-text="Kimlik avı bağlamında Gezgin için Görünüm menüsü" lightbox="../../media/ExplorerViewEmailPhishMenu.png":::

3. **Gönderen'e** tıklayın ve **url'ler** \> **Karara tıklayın'ı** seçin.

4. **Engellendi** ve **Engelle geçersiz kılındı** gibi bir veya daha fazla seçenek belirleyin ve ardından bu filtreyi uygulama seçenekleriyle aynı satırdaki **Yenile** düğmesini seçin. (Tarayıcı pencerenizi yenilemeyin.)

   > [!div class="mx-imgBorder"]
   > :::image type="content" source="../../media/ThreatExplorerEmailPhishClickVerdictOptions.png" alt-text="URL'ler ve tıklama kararları" lightbox="../../media/ThreatExplorerEmailPhishClickVerdictOptions.png":::

   Rapor, raporun altındaki URL sekmesinde iki farklı URL tablosu gösterecek şekilde yenilenir:

   - **En çok kullanılan URL'ler** , filtrelediğiniz iletilerdeki URL'ler ve her URL için e-posta teslim eylemi sayısıdır. Kimlik avı e-posta görünümünde bu liste genellikle geçerli URL'ler içerir. Saldırganlar, teslim etmeye çalışmak için iletilerine iyi ve kötü URL'lerin bir karışımını ekler, ancak kötü amaçlı bağlantıların daha ilginç görünmesini sağlar. URL tablosu toplam e-posta sayısına göre sıralanır, ancak görünümü basitleştirmek için bu sütun gizlenir.

   - **En üstteki tıklamalar**, tıklanan ve toplam tıklama sayımına göre sıralanmış Kasa Bağlantılar sarmalanmış URL'leridir. Görünümü basitleştirmek için bu sütun da görüntülenmez. Sütuna göre toplam sayımlar, tıklanan her URL için Kasa Bağlantıları tıklama kararı sayısını gösterir. Kimlik avı e-posta görünümünde bunlar genellikle şüpheli veya kötü amaçlı URL'lerdir. Ancak görünümde tehdit olmayan ancak kimlik avı iletilerinde bulunan URL'ler yer alabilir. Açılmamış bağlantılarda URL tıklamaları burada gösterilmez.

   İki URL tablosu, teslim eylemine ve konuma göre kimlik avı e-posta iletilerindeki en iyi URL'leri gösterir. Tablolarda uyarıya rağmen engellenen veya ziyaret edilen URL tıklamaları gösterilir, böylece kullanıcılara hangi olası hatalı bağlantıların sunulduğunu ve kullanıcının tıklandığını görebilirsiniz. Buradan daha fazla analiz gerçekleştirebilirsiniz. Örneğin, grafiğin altında, kuruluşunuzun ortamında engellenen e-posta iletilerinde en çok kullanılan URL'leri görebilirsiniz.

   > [!div class="mx-imgBorder"]
   > :::image type="content" source="../../media/ExplorerPhishClickVerdictURLs.png" alt-text="Engellenen Gezgin URL'leri" lightbox="../../media/ExplorerPhishClickVerdictURLs.png":::

   Daha ayrıntılı bilgileri görüntülemek için bir URL seçin.

   > [!NOTE]
   > URL açılır öğesi iletişim kutusunda, e-posta iletilerindeki filtreleme kaldırılarak URL'nin ortamınızda gösterilmesinin tam görünümü gösterilir. Bu, Gezgin'de ilgilendiğiniz e-posta iletilerini filtrelemenize, olası tehditler olan belirli URL'leri bulmanıza ve ardından Gezgin görünümünün kendisine URL filtreleri eklemek zorunda kalmadan ortamınızdaki URL'nin açığa çıkma durumunu (URL ayrıntıları iletişim kutusu aracılığıyla) genişletmenize olanak tanır.

### <a name="interpretation-of-click-verdicts"></a>Tıklama kararlarının yorumlanması

E-posta veya URL açılır listelerinde, İlk Tıklamalar'da ve filtreleme deneyimlerimizde farklı tıklama kararı değerleri görürsünüz:

- **Hiçbiri:** URL için karar alınamadı. Kullanıcı URL'ye tıklaymış olabilir.
- **Izin verilen:** Kullanıcının URL'ye gitmesine izin verildi.
- **Engellenen:** Kullanıcının URL'ye gezinmesi engellendi.
- **Bekleyen karar:** Kullanıcıya patlama bekleniyor sayfası sunuldu.
- **Geçersiz kılınarak engellendi:** Kullanıcının doğrudan URL'ye gezinmesi engellendi. Ancak kullanıcı URL'ye gitmek için bloğun üzerine geçti.
- **Bekleyen karar atlandı:** Kullanıcıya patlama sayfası sunuldu. Ancak kullanıcı URL'ye erişmek için iletinin üzerine geçti.
- **Hata:** Kullanıcıya hata sayfası sunuldu veya karar yakalanırken bir hata oluştu.
- **Başarısızlık:** Karar yakalanırken bilinmeyen bir özel durum oluştu. Kullanıcı URL'ye tıklaymış olabilir.

## <a name="review-email-messages-reported-by-users"></a>Kullanıcılar tarafından bildirilen e-posta iletilerini gözden geçirme

Kuruluşunuzdaki kullanıcıların [Rapor İletisi eklentisi veya Rapor](enable-the-report-message-add-in.md) [Kimlik Avı eklentisi](enable-the-report-phish-add-in.md) aracılığıyla *Gereksiz*, *Gereksiz Değil* veya *Kimlik Avı* olarak bildirdiği e-posta iletilerini görmek istediğinizi varsayalım. Bunları görmek için Explorer'ın [**EmailSubmissions** > ](threat-explorer-views.md#email--submissions) görünümünü (veya Gerçek zamanlı algılamaları) kullanın.

1. Güvenlik & Uyumluluk Merkezi'nde (<https://protection.office.com> ) **Tehdit yönetimi** \> **Gezgini'ni** (veya **Gerçek zamanlı algılamalar**) seçin. (Bu örnekte Gezgin kullanılır.)

2. **Görünüm** menüsünde **E-posta** \> **Gönderimleri'ni** seçin.

   > [!div class="mx-imgBorder"]
   > :::image type="content" source="../../media/explorer-view-menu-email-user-reported.png" alt-text="E-postalar için Explorer'ın Görünüm menüsü" lightbox="../../media/explorer-view-menu-email-user-reported.png":::

3. **Gönderen'e** tıklayın ve temel **rapor türü'nü** **seçin**\>.

4. **Kimlik Avı** gibi bir seçenek belirleyin ve ardından **Yenile** düğmesini seçin.

   > [!div class="mx-imgBorder"]
   > :::image type="content" source="../../media/EmailUserReportedReportType.png" alt-text="Kullanıcı tarafından bildirilen kimlik avı" lightbox="../../media/EmailUserReportedReportType.png":::

Rapor, kuruluşunuzdaki kişilerin kimlik avı girişimi olarak bildirdiği e-posta iletileri hakkındaki verileri göstermek için yenilenir. Daha fazla analiz yapmak ve gerekirse [kimlik avı önleme ilkelerinizi Office 365 için Microsoft Defender](configure-mdo-anti-phishing-policies.md) ayarlamak için bu bilgileri kullanabilirsiniz.

## <a name="start-automated-investigation-and-response"></a>Otomatik araştırma ve yanıt başlatma

> [!NOTE]
> Otomatik araştırma ve yanıt özellikleri *Office 365 için Microsoft Defender Plan 2* ve *Office 365 E5'da* kullanılabilir.

[Otomatik araştırma ve yanıt](automated-investigation-response-office.md) , güvenlik operasyonları ekibinize siber saldırıları araştırmak ve azaltmak için harcanan zamandan ve çabadan tasarruf edebilir. Güvenlik playbook'larını tetikleyebilecek uyarıları yapılandırmaya ek olarak, Gezgin'deki bir görünümden otomatik araştırma ve yanıt işlemi başlatabilirsiniz. Ayrıntılar için bkz [. Örnek: Güvenlik yöneticisi Gezgin'den araştırma tetikler](automated-investigation-response-office.md#example-a-security-administrator-triggers-an-investigation-from-threat-explorer).

## <a name="more-ways-to-use-explorer-and-real-time-detections"></a>Explorer ve Gerçek zamanlı algılamaları kullanmanın diğer yolları

Bu makalede açıklanan senaryolara ek olarak, Gezgin (veya Gerçek zamanlı algılamalar) ile sunulan daha birçok raporlama seçeneğiniz vardır. Aşağıdaki makalelere bakın:

- [Teslim edilen kötü amaçlı e-postayı bulma ve araştırma](investigate-malicious-email-that-was-delivered.md)
- [SharePoint Online, OneDrive ve Microsoft Teams'da algılanan kötü amaçlı dosyaları görüntüleme](./mdo-for-spo-odb-and-teams.md)
- [Tehdit Gezgini'ndeki görünümlere (ve Gerçek zamanlı algılamalara) genel bakış elde edin](threat-explorer-views.md)
- [Tehdit koruması durum raporu](view-email-security-reports.md#threat-protection-status-report)
- [Microsoft 365 Defender'de otomatik araştırma ve yanıt](../defender/m365d-autoir.md)

## <a name="required-licenses-and-permissions"></a>Gerekli lisanslar ve izinler

Explorer veya Gerçek zamanlı algılamaları kullanmak için [Office 365 için Microsoft Defender](defender-for-office-365.md) sahip olmanız gerekir.

- Explorer, Office 365 için Defender Plan 2'ye dahildir.
- Gerçek zamanlı algılamalar raporu Office 365 için Defender Plan 1'e dahildir.
- Office 365 için Defender tarafından korunması gereken tüm kullanıcılara lisans atamayı planlayın. Explorer ve Gerçek zamanlı algılamalar, lisanslı kullanıcılar için algılama verilerini gösterir.

Gezgin veya Gerçek zamanlı algılamaları görüntülemek ve kullanmak için, güvenlik yöneticisine veya güvenlik okuyucuya verilen izinler gibi uygun izinlere sahip olmanız gerekir.

- Güvenlik & Uyumluluk Merkezi için aşağıdaki rollerden birine atanmış olmanız gerekir:

  - Kuruluş Yönetimi
  - Güvenlik Yöneticisi (bu, Azure Active Directory yönetim merkezinde (<https://aad.portal.azure.com>) atanabilir
  - Güvenlik Okuyucusu

- Exchange Online için, Exchange yönetim merkezinde (EAC) veya [PowerShell'i Exchange Online](/powershell/exchange/exchange-online-powershell) aşağıdaki rollerden birine atanmış olmanız gerekir:

  - Kuruluş Yönetimi
  - View-Only Kuruluş Yönetimi
  - alıcıları View-Only
  - Uyumluluk Yönetimi

Roller ve izinler hakkında daha fazla bilgi edinmek için aşağıdaki kaynaklara bakın:

- [Microsoft 365 Defender portalındaki izinler](permissions-microsoft-365-security-center.md)
- [Exchange Online özellik izinleri](/exchange/permissions-exo/feature-permissions)

## <a name="differences-between-threat-explorer-and-real-time-detections"></a>Tehdit Gezgini ile Gerçek zamanlı algılamalar arasındaki farklar

- *Gerçek zamanlı algılamalar* raporu Office 365 için Defender Plan 1'de kullanılabilir. *Tehdit Gezgini*, Office 365 için Defender Plan 2'de kullanılabilir.
- Gerçek zamanlı algılamalar raporu, algılamaları gerçek zamanlı olarak görüntülemenizi sağlar. Tehdit Gezgini bunu da yapar, ancak belirli bir saldırı için ek ayrıntılar da sağlar.
- *Tüm e-posta* görünümü Tehdit Gezgini'nde kullanılabilir ancak Gerçek zamanlı algılamalar raporunda kullanılamaz.
- Tehdit Gezgini'ne daha fazla filtreleme özelliği ve kullanılabilir eylem dahildir. Daha fazla bilgi için bkz. [Office 365 için Microsoft Defender Hizmet Açıklaması: Office 365 için Defender planlarda özellik kullanılabilirliği](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description#feature-availability-across-advanced-threat-protection-atp-plans).

## <a name="other-articles"></a>Diğer makaleler

[E-posta Varlık Sayfası ile e-postaları araştırma](mdo-email-entity-page.md)
