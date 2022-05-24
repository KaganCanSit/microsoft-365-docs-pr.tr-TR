---
title: Office 365 için Microsoft Defender için Tehdit Gezgini'nde tehdit avcılığı
f1.keywords:
- NOCSH
ms.author: dansimp
author: MSFTTracyp
manager: dansimp
audience: ITPro
ms.topic: article
ms.date: 05/05/2021
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
description: Tehditleri verimli bir şekilde araştırmak ve yanıtlamak için Microsoft 365 Defender portalında Tehdit Gezgini'ni veya Gerçek zamanlı algılamaları kullanın.
ms.custom:
- seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 2c99bc2ce004156320ec8f53f6b956f7989ee056
ms.sourcegitcommit: 725a92b0b1555572b306b285a0e7a7614d34e5e5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/24/2022
ms.locfileid: "65648833"
---
# <a name="threat-hunting-in-threat-explorer-for-microsoft-defender-for-office-365"></a>Office 365 için Microsoft Defender için Tehdit Gezgini'nde tehdit avcılığı

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Şunlar için geçerlidir:**
- [Office 365 için Microsoft Defender plan 1 ve plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Bu makalede:

- [Tehdit Gezgini kılavuzu](#threat-explorer-walk-through)
- [E-posta araştırması](#email-investigation)
- [E-posta düzeltme](#email-remediation)
- [Tehdit avcılığı deneyiminde iyileştirmeler](#improvements-to-threat-hunting-experience)

> [!NOTE]
> Bu, **Tehdit Gezgini (Gezgin)**, **e-posta güvenliği**, **Gezgin ve Gerçek zamanlı algılamalar** (araçlar arasındaki farklar ve bunları çalıştırmak için gereken izinler gibi) ile ilgili **3 makalelik bir serinin** parçasıdır. Bu serideki diğer iki makale, [Tehdit Gezgini ve Tehdit Gezgini ile E-posta güvenliği](email-security-in-microsoft-defender.md) [ve Gerçek zamanlı algılamalardır](real-time-detections.md).

**Uygulandığı öğe**
- [Office 365 için Microsoft Defender plan 1 ve plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Kuruluşunuzun [Office 365 için Microsoft Defender](defender-for-office-365.md) varsa ve [izinleriniz varsa, tehditleri](#required-licenses-and-permissions) algılamak ve düzeltmek için **Gezgin** veya **Gerçek zamanlı algılamaları** kullanabilirsiniz.

konumundaki Microsoft 365 Defender portalında <https://security.microsoft.com>**E-posta & işbirliği'ne** gidin ve **Ardından Gezgin** veya **Gerçek zamanlı algılamalar'ı** seçin. Doğrudan sayfaya gitmek için veya <https://security.microsoft.com/realtimereports>kullanın<https://security.microsoft.com/threatexplorer>.

Bu araçlarla şunları yapabilirsiniz:

- Microsoft 365 güvenlik özellikleri tarafından algılanan kötü amaçlı yazılımlara bakın
- Kimlik avı URL'sini görüntüleyin ve karar verilerine tıklayın
- Gezgin'deki bir görünümden otomatik araştırma ve yanıt işlemi başlatma
- Kötü amaçlı e-postaları ve daha fazlasını araştırma

Daha fazla bilgi için bkz. [Tehdit Gezgini ile e-posta güvenliği](email-security-in-microsoft-defender.md).

Office 365 için Microsoft Defender kullanarak e-posta ve işbirliği tabanlı tehditleri nasıl avlayıp araştıracağınızı öğrenmek için bu kısa videoyu izleyin. 
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWyPRU]

## <a name="threat-explorer-walk-through"></a>Tehdit Gezgini kılavuzu

Office 365 için Microsoft Defender iki abonelik planı vardır: Plan 1 ve Plan 2. El ile çalıştırılan Tehdit avcılığı araçları her iki planda da, farklı adlar altında ve farklı özelliklere sahiptir.

Office 365 için Defender Plan 1, Plan 2'deki *Tehdit Gezgini* (*Gezgin* olarak da adlandırılır) avcılık aracının bir alt kümesi olan *Gerçek zamanlı algılamaları* kullanır. Bu makale dizisinde, örneklerin çoğu tam Tehdit Gezgini kullanılarak oluşturulmuştur. Yöneticiler, nereye başvuracaklarını görmek için gerçek zamanlı algılamalardaki tüm adımları test etmelidir.

**Explorer'a** gittikten sonra, varsayılan olarak **Kötü Amaçlı Yazılım** sayfasına ulaşırsınız, ancak seçeneklerinizi tanımak için **Görünüm** açılan listesini kullanırsınız. Kimlik Avı avlıyorsanız veya bir tehdit kampanyasına girişiyorsanız bu görünümleri seçin.

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/view-drop-down.png" alt-text="Tehdit Gezgini'ndeki Görünüm açılan menüsü" lightbox="../../media/view-drop-down.png":::

Güvenlik işlemleri (Sec Ops) kişisi görmek istediği verileri seçtikten sonra kapsamın kullanıcı **Gönderimleri** gibi dar bir görünüm mü yoksa **Tüm e-postalar** gibi daha geniş bir görünüm mü olduğunu belirlerse, daha fazla filtreleme yapmak için **Gönderen** düğmesini kullanabilir. Filtreleme eylemlerinizi tamamlamak için Yenile'yi seçmeyi unutmayın.

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/sender-drop-down.png" alt-text="Tehdit Gezgini'ndeki Gönderen düğmesi" lightbox="../../media/sender-drop-down.png":::

Gezgin'de veya Gerçek zamanlı algılamada odağı iyileştirme katmanlar halinde düşünülebilir. İlki **Görünüm'dür**. İkincisi *, filtrelenmiş bir odak* olarak düşünülebilir. Örneğin, kararlarınızı şu şekilde kaydederek tehdit bulma konusunda attığınız adımları yeniden izleyebilirsiniz: Explorer'da sorunu bulmak için **Alıcı filtresi odağına sahip Kötü Amaçlı Yazılım Görünümü'nü seçtim**. Bu, adımlarınızı geri çekmeyi kolaylaştırır.

> [!TIP]
> Sec Ops, yüksek değerli hedefleri dikkate aldıkları hesapları işaretlemek için **Etiketler** kullanırsa, *Etiketler filtre odağıyla Kimlik Avı Görünümü gibi seçimler yapabilir (kullanılıyorsa tarih aralığı dahil)* . Bu, onlara bir zaman aralığında yüksek değerli kullanıcı hedeflerine yönlendirilen tüm kimlik avı girişimlerini gösterir (belirli kimlik avı saldırılarının sektörleri için çok fazla gerçekleştiği tarihler gibi).

Tarih aralığı denetimleri kullanılarak tarih aralıklarında iyileştirmeler yapılabilir. Burada **, Kötü Amaçlı Yazılım** görünümünde **, Algılama Teknolojisi** filtre odağıyla Gezgin'i görebilirsiniz. Ancak Bu, Sec Ops ekiplerinin ayrıntılı bir şekilde incelemesini sağlayan **Gelişmiş filtre** düğmesidir.

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/advanced-filter.png" alt-text="Tehdit Gezgini'ndeki Gelişmiş filtre" lightbox="../../media/advanced-filter.png":::

**Gelişmiş filtresine** tıklanması, Sec Ops avcılarının kendi kendilerine sorgu oluşturmasına olanak sağlayan ve görmeleri gereken bilgileri eklemelerine veya dışlamalarına olanak sağlayan bir panel açar. Gezgin sayfasındaki hem grafik hem de tablo sonuçlarını yansıtır.

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/threat-explorer-chart-table.png" alt-text="Sorgudan Alınan Sonuçlar" lightbox="../../media/threat-explorer-chart-table.png":::

Tablodaki en yararlı bilgi türlerini almak için **Sütun seçenekleri** düğmesini kullanın:

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/threat-explorer-column-options.png" alt-text="Sütun seçenekleri düğmesi vurgulanmış" lightbox="../../media/threat-explorer-column-options.png":::

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/column-options.png" alt-text="Sütunlar'daki kullanılabilir seçenekler" lightbox="../../media/column-options.png":::

Aynı mien'de görüntü seçeneklerinizi test edin. Farklı hedef kitleler, aynı verilerin farklı sunularına iyi tepki gösterir. Bazı izleyiciler için **E-posta Kaynakları** haritası, bir tehdidin hemen yanındaki **Kampanya görüntüleme** seçeneğinden daha yaygın veya daha hızlı olduğunu gösterebilir. Sec Ops, güvenlik ve koruma gereksiniminin altını çizen noktaları en iyi şekilde oluşturmak veya eylemlerinin etkinliğini göstermek için daha sonra karşılaştırma yapmak için bu ekranları kullanabilir.

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/threat-explorer-email-origin-map.png" alt-text="E-posta Çıkış Noktaları haritası" lightbox="../../media/threat-explorer-email-origin-map.png":::

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/threat-explorer-campaign-display.png" alt-text="Kampanya görüntüleme seçenekleri" lightbox="../../media/threat-explorer-campaign-display.png":::

### <a name="email-investigation"></a>E-posta araştırması

Şüpheli bir e-posta gördüğünüzde, sağ taraftaki açılır öğeyi genişletmek için ada tıklayın. Burada, Sec Ops'ın [e-posta varlık sayfasını](mdo-email-entity-page.md) görmesine olanak tanıyan başlık kullanılabilir.

E-posta varlığı sayfası **Ayrıntılar**, Ekler, **Cihazlar** altında bulunabilecek içerikleri bir araya **getirerek** daha düzenli veriler içerir. Bu, DMARC sonuçları, kopyalama seçeneğiyle e-posta üst bilgisinin düz metin görüntüsü, güvenli bir şekilde patlatılmış eklerle ilgili karar bilgileri ve bırakılan bu patlamaları içeren dosyaları içerir (bağlantı kurulmuş IP adreslerini ve sayfaların veya dosyaların ekran görüntülerini içerebilir). URL'ler ve bunların kararları da raporlanan benzer ayrıntılarla birlikte listelenir.

Bu aşamaya ulaştığınızda, e-posta varlık sayfası son adım (*düzeltme*) için kritik önem taşır.

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/threat-explorer-email-entity-page.png" alt-text="E-posta varlığı sayfası" lightbox="../../media/threat-explorer-email-entity-page.png":::

> [!TIP]
> Patlatılmış Eklerin sonuçları, eklenen URL'ler için bulgular ve güvenli E-posta önizlemesi de dahil olmak üzere zengin e-posta varlık sayfası (aşağıda **Analiz** sekmesinde görülmektedir) hakkında daha fazla bilgi edinmek için [buraya](mdo-email-entity-page.md) tıklayın.

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/threat-explorer-analysis-tab.png" alt-text="E-posta varlığı sayfasının Analiz sekmesi" lightbox="../../media/threat-explorer-analysis-tab.png":::

### <a name="email-remediation"></a>E-posta düzeltme

Bir Sec Ops kişisi bir e-postanın bir tehdit olduğunu belirledikten sonra, bir sonraki Gezgin veya Gerçek zamanlı algılama adımı tehditle ilgilenir ve bunu düzelter. Bu, Tehdit Gezgini'ne dönüp sorun e-postasının onay kutusunu seçerek ve **Eylemler** düğmesini kullanarak yapılabilir.

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/threat-explorer-email-actions-button.png" alt-text="Tehdit Gezgini'ndeki Eylemler düğmesi" lightbox="../../media/threat-explorer-email-actions-button.png":::

Burada analist, postayı İstenmeyen Posta, Kimlik Avı veya Kötü Amaçlı Yazılım olarak bildirme, alıcılarla iletişim kurma veya Otomatik Araştırma ve Yanıt (veya AIR) playbook'larını tetikleme (Plan 2'niz varsa) gibi daha fazla araştırma gerçekleştirebilir. Ya da, posta temiz olarak bildirilebilir.

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/threat-explorer-email-actions-drop-down.png" alt-text="Eylemler açılan menüsü" lightbox="../../media/threat-explorer-email-actions-drop-down.png":::

## <a name="improvements-to-threat-hunting-experience"></a>Tehdit avcılığı deneyiminde iyileştirmeler

### <a name="alert-id"></a>Uyarı Kimliği

Bir uyarıdan Tehdit Gezgini'ne gezinirken **, Görünüm** **Uyarı Kimliğine** göre filtrelenir. Bu, gerçek zamanlı algılamada da geçerlidir. Belirli bir uyarıyla ilgili iletiler ve e-posta toplamı (sayı) gösterilir. İletinin bir uyarının parçası olup olmadığını görebilir ve bu iletiden ilgili uyarıya gidebilirsiniz.

Son olarak, uyarı kimliği URL'ye eklenir, örneğin: `https://https://security.microsoft.com/viewalerts`

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/AlertID-Filter.png" alt-text="Uyarı Kimliği filtresi" lightbox="../../media/AlertID-Filter.png":::

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/AlertID-DetailsFlyout.png" alt-text="Ayrıntılı açılır öğede Uyarı Kimliği" lightbox="../../media/AlertID-DetailsFlyout.png":::

### <a name="extending-explorer-and-real-time-detections-data-retention-and-search-limit-for-trial-tenants"></a>Deneme kiracıları için Gezgin (ve Gerçek zamanlı algılamalar) veri saklama ve arama sınırını genişletme

Bu değişiklik kapsamında analistler, Tehdit Gezgini'nde 30 gün boyunca (yedi günden daha fazla) e-posta verilerini ve hem Office için Defender P1 hem de P2 deneme kiracıları için gerçek zamanlı algılamaları arayabilir ve filtreleyebilecektir. Bu, hem P1 hem de P2 E5 müşterileri için, bekletme varsayılanı zaten 30 gün olan üretim kiracılarını etkilemez.

### <a name="updated-export-limit"></a>Dışarı aktarma sınırı güncelleştirildi

Tehdit Gezgini'nden dışarı aktarılabilen E-posta kayıtlarının sayısı şu anda 200.000'dir (9990 idi). Dışarı aktarılabilir sütun kümesi değiştirilmez.

### <a name="tags-in-threat-explorer"></a>Tehdit Gezgini'ndeki etiketler

> [!NOTE]
> Kullanıcı etiketleri özelliği Önizleme aşamasındadır ve herkes tarafından kullanılamayabilir. Ayrıca Önizlemeler değiştirilebilir. Yayın zamanlaması hakkında bilgi için Microsoft 365 yol haritasına göz atın.

Kullanıcı etiketleri, Office 365 için Microsoft Defender'daki belirli kullanıcı gruplarını tanımlar. Lisanslama ve yapılandırma dahil olmak üzere etiketler hakkında daha fazla bilgi için bkz. [Kullanıcı etiketleri](user-tags.md).

Tehdit Gezgini'nde aşağıdaki deneyimlerde kullanıcı etiketleri hakkındaki bilgileri görebilirsiniz.

#### <a name="email-grid-view"></a>E-posta kılavuzu görünümü

Analistler e-posta kılavuzundaki **Etiketler** sütununa baktığında, gönderen veya alıcı posta kutularına uygulanmış olan tüm etiketleri görür. Varsayılan olarak, *önce öncelik hesapları* gibi sistem etiketleri gösterilir.

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/tags-grid.png" alt-text="E-posta kılavuzu görünümünde etiketleri filtrele" lightbox="../../media/tags-grid.png":::

#### <a name="filtering"></a>Filtreleme

Etiketler filtre olarak kullanılabilir. Yalnızca öncelikli hesaplar arasında av yapın veya belirli kullanıcı etiketleri senaryolarını bu şekilde kullanın. Ayrıca, belirli etiketlere sahip sonuçları dışlayabilirsiniz. Araştırma kapsamınızı daraltmak için Etiketleri diğer filtreler ve tarih aralıklarıyla birleştirin.

[![Etiketleri filtreleyin.](../../media/tags-filter-normal.png)](../../media/tags-filter-normal.png#lightbox)

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/tags-filter-not.png" alt-text="Filtrelenmemiş etiketler" lightbox="../../media/tags-filter-not.png":::

#### <a name="email-detail-flyout"></a>E-posta ayrıntıları açılır öğesi

Gönderenin ve alıcının etiketlerini tek tek görüntülemek için bir e-posta seçerek ileti ayrıntıları açılır öğesini açın. **Özet** sekmesinde, gönderen ve alıcı etiketleri ayrı ayrı gösterilir. Gönderen ve alıcı için tek tek etiketler hakkındaki bilgiler CSV verileri olarak dışarı aktarılabilir.

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/tags-flyout.png" alt-text="E-posta Ayrıntıları etiketleri" lightbox="../../media/tags-flyout.png":::

Etiket bilgileri, URL tıklamaları açılır öğesinde de gösterilir. Bunu görmek için Url'ler veya **URL Tıklamaları** sekmesi > Kimlik Avı veya  Tüm E-posta görünümü'ne gidin. Tek bir URL açılır öğesini seçerek ilgili URL'ye yönelik tıklamalar hakkında, bu tıklamayla ilişkili etiketler de dahil olmak üzere ek ayrıntıları görebilirsiniz.

### <a name="updated-timeline-view"></a>Güncelleştirilmiş Zaman Çizelgesi Görünümü

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/tags-urls.png" alt-text="URL etiketleri" lightbox="../../media/tags-urls.png":::
>
[Bu videoyu](https://www.youtube.com/watch?v=UoVzN0lYbfY&list=PL3ZTgFEc7LystRja2GnDeUFqk44k7-KXf&index=4) izleyerek daha fazla bilgi edinin.

## <a name="extended-capabilities"></a>Genişletilmiş özellikler

### <a name="top-targeted-users"></a>En çok hedeflenen kullanıcılar

En İyi Kötü Amaçlı Yazılım Aileleri, Kötü Amaçlı Yazılım bölümünde **en çok hedeflenen kullanıcıları** gösterir. En çok hedeflenen kullanıcılar Kimlik Avı ve Tüm E-posta görünümleri aracılığıyla da genişletilir. Analistler, hedeflenen ilk beş kullanıcıyı ve her görünümdeki her kullanıcı için deneme sayısını görebilir.

Her e-posta görünümü için çevrimdışı analiz için hedeflenen kullanıcıların listesini, yapılan deneme sayısıyla birlikte 3.000 sınırına kadar dışarı aktarabilen güvenlik işlemleri. Ayrıca, deneme sayısını seçtiğinizde (örneğin, aşağıdaki görüntüde 13 deneme) Tehdit Gezgini'nde filtrelenmiş bir görünüm açılır; böylece e-postalar ve bu kullanıcıya yönelik tehditler hakkında daha fazla ayrıntı görebilirsiniz.

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/Top_Targeted_Users.png" alt-text="En çok hedeflenen kullanıcılar" lightbox="../../media/Top_Targeted_Users.png":::

### <a name="exchange-transport-rules"></a>aktarım kurallarını Exchange

Güvenlik operasyonları ekibi, bir iletiye uygulanan tüm Exchange aktarım kurallarını (veya Posta akışı kurallarını) E-posta kılavuzu görünümünde görebilir. Kılavuzda **Sütun seçenekleri'ni** ve ardından sütun seçeneklerinden **Exchange Taşıma Kuralı Ekle'yi** seçin. Exchange aktarım kuralları seçeneği, e-postadaki **Ayrıntılar** açılır öğesinde de görünür.

İletiye uygulanan aktarım kurallarının adları ve GUID'leri görüntülenir. Analistler, aktarım kuralının adını kullanarak iletileri arayabilir. Bu bir CONTAINS aramasıdır, yani kısmi aramalar da yapabilirsiniz.

> [!IMPORTANT]
> Exchange aktarım kuralı arama ve ad kullanılabilirliği size atanan role bağlıdır. Aktarım kuralı adlarını görüntülemek ve arama yapmak için aşağıdaki rollerden veya izinlerden birine sahip olmanız gerekir. Ancak, aşağıdaki roller veya izinler olmasa bile, analist E-posta Ayrıntıları'nda aktarım kuralı etiketini ve GUID bilgilerini görebilir. E-posta Kılavuzları, E-posta açılırları, Filtreler ve Dışarı Aktarma'daki diğer kayıt görüntüleme deneyimleri etkilenmez.
>
> - Yalnızca Exchange Online - veri kaybını önleme: Tümü
> - Yalnızca Exchange Online - O365SupportViewConfig: Tümü
> - Microsoft Azure Active Directory veya Exchange Online - Güvenlik Yöneticisi: Tümü
> - Azure Active Directory veya Exchange Online - Güvenlik Okuyucusu: Tümü
> - Yalnızca Exchange Online - Aktarım Kuralları: Tümü
> - Yalnızca Exchange Online - View-Only Yapılandırması: Tümü
>
> E-posta kılavuzu, Ayrıntılar açılır öğesi ve Dışarı Aktarılan CSV'nin içinde ETR'lere aşağıda gösterildiği gibi bir Ad/GUID gösterilir.
>
> > [!div class="mx-imgBorder"]
> > :::image type="content" source="../../media/ETR_Details.png" alt-text="Exchange Aktarım kuralları" lightbox="../../media/ETR_Details.png":::

### <a name="inbound-connectors"></a>Gelen bağlayıcılar

Bağlayıcılar, e-postanızın Microsoft 365 veya Office 365 kuruluşunuzdan nasıl aktığını özelleştiren yönergelerden oluşan bir koleksiyondır. Tüm güvenlik kısıtlamalarını veya denetimlerini uygulamanıza olanak tanır. Tehdit Gezgini'nde, bir e-postayla ilgili bağlayıcıları görüntüleyebilir ve bağlayıcı adlarını kullanarak e-postaları arayabilirsiniz.

Bağlayıcı arama bir CONTAINS sorgusudur ve kısmi anahtar sözcük aramalarının işe yarayabileceği anlamına gelir:

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/Connector_Details.png" alt-text="Bağlayıcı ayrıntıları" lightbox="../../media/Connector_Details.png":::

## <a name="required-licenses-and-permissions"></a>Gerekli lisanslar ve izinler

Explorer veya Gerçek zamanlı algılamaları kullanmak için [Office 365 için Microsoft Defender](defender-for-office-365.md) sahip olmanız gerekir.

- Explorer, Office 365 için Defender Plan 2'ye dahildir.
- Gerçek zamanlı algılamalar raporu Office 365 için Defender Plan 1'e dahildir.
- Office 365 için Defender tarafından korunması gereken tüm kullanıcılara lisans atamayı planlayın. Explorer ve Gerçek zamanlı algılamalar, lisanslı kullanıcılar için algılama verilerini gösterir.

Explorer veya Gerçek zamanlı algılamaları görüntülemek ve kullanmak için aşağıdaki izinlere sahip olmanız gerekir:

- Microsoft 365 Defender portalında:
  - Kuruluş Yönetimi
  - Güvenlik Yöneticisi (bu, Azure Active Directory yönetim merkezinde (<https://aad.portal.azure.com>) atanabilir
  - Güvenlik Okuyucusu
- Exchange Online:
  - Kuruluş Yönetimi
  - View-Only Kuruluş Yönetimi
  - alıcıları View-Only
  - Uyumluluk Yönetimi

Roller ve izinler hakkında daha fazla bilgi edinmek için aşağıdaki kaynaklara bakın:

- [Microsoft 365 Defender portalındaki izinler](permissions-microsoft-365-security-center.md)
- [Exchange Online'de izinler](/exchange/permissions-exo/permissions-exo)
- [PowerShell'i Exchange Online](/powershell/exchange/exchange-online-powershell)

## <a name="more-information"></a>Daha fazla bilgi

- [Teslim edilen kötü amaçlı e-postayı bulma ve araştırma](investigate-malicious-email-that-was-delivered.md)
- [SharePoint Online, OneDrive ve Microsoft Teams'da algılanan kötü amaçlı dosyaları görüntüleme](mdo-for-spo-odb-and-teams.md)
- [Tehdit Gezgini'ndeki görünümlere (ve Gerçek zamanlı algılamalara) genel bakış elde edin](threat-explorer-views.md)
- [Tehdit koruması durum raporu](view-email-security-reports.md#threat-protection-status-report)
- [Microsoft Tehdit Koruması'nda otomatik araştırma ve yanıt](automated-investigation-response-office.md)
- [E-posta Varlık Sayfası ile e-postaları araştırma](mdo-email-entity-page.md)
