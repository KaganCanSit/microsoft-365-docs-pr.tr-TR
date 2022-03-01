---
title: Microsoft Defender için Threat Explorer'da tehdit Office 365
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
description: Tehditleri verimli bir şekilde araştırmak ve yanıtlamak için Tehdit Gezgini'Microsoft 365 Defender gerçek zamanlı algılamaları kullanın.
ms.custom:
- seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: de9121320e339ecff2b665737a6b4ccebe5e0fd0
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2022
ms.locfileid: "63021745"
---
# <a name="threat-hunting-in-threat-explorer-for-microsoft-defender-for-office-365"></a>Microsoft Defender için Threat Explorer'da tehdit Office 365

Bu makalede:

- [Threat Explorer adım adım yol görüntüleme](#threat-explorer-walk-through)
- [E-posta soruşturması](#email-investigation)
- [E-posta düzeltme](#email-remediation)
- [Tehdit avı deneyiminde iyileştirmeler](#improvements-to-threat-hunting-experience)

> [!NOTE]
> Bu, **Threat Explorer (Explorer)****,** **e-posta** güvenliği ve Explorer ile Gerçek zamanlı algılamalar (araçlar arasındaki farklar ve bunları çalıştırmak için gereken izinler gibi) hakkında **3** makalelik bir serinin bir bölümüdir. Bu dizide yer alan diğer iki makale de Tehdit Gezgini ve [Tehdit Gezgini](email-security-in-microsoft-defender.md) ile [E-posta güvenliği ve Gerçek zamanlı algılamalardır](real-time-detections.md).


**Geçerli olduğu yer:**
- [1. plan Office 365 plan 2 için Microsoft Defender](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Kuruluşta Tehdit [algılaması için Microsoft Defender Office 365](defender-for-office-365.md) [varsa, tehditleri](#required-licenses-and-permissions) tespit etmek ve düzeltmek için **Explorer'ı** veya Gerçek zamanlı  algılamaları kullanabilirsiniz.

Aşağıdaki Microsoft 365 Defender portalında E-posta ve <https://security.microsoft.com>**& gidin** ve **Gezgin'i** veya **Gerçek zamanlı algılamalar'ı seçin**. Doğrudan sayfaya gitmek için veya kullanın <https://security.microsoft.com/threatexplorer> <https://security.microsoft.com/realtimereports>.

Bu araçlarla şunlarıabilirsiniz:

- Güvenlik özellikleri tarafından algılanan kötü amaçlı Microsoft 365 görme
- Kimlik avı URL'sini görüntüleme ve karar verilerine tıklama
- Gezgin'de görünümden otomatik bir araştırma ve yanıt işlemi başlatma
- Kötü amaçlı e-postaları araştırma ve daha fazlası

Daha fazla bilgi için bkz. [Threat Explorer ile e-posta güvenliği](email-security-in-microsoft-defender.md).

## <a name="threat-explorer-walk-through"></a>Threat Explorer adım adım yol görüntüleme

Abonelikler için Microsoft Defender Office 365 iki abonelik planı vardır: Plan 1 ve Plan 2. El ile işletilen Tehdit arama araçları her iki planda, farklı adlar ve farklı özelliklere sahip olarak mevcuttur.

Plan 1 Office 365 için *Defender, Plan* 2'de *Tehdit* Gezgini (Gezgin olarak da *adlandırılan) arama* aracının bir alt kümesi olan Gerçek zamanlı algılamaları kullanır. Bu dizi makalede, örneklerin çoğu Threat Explorer'ın tamamını kullanarak oluşturulmuş. Yöneticilerin nerede uygulanacaklarını görmek için gerçek zamanlı algılamalarda tüm adımları test olması gerekir.

  Gezgin'e gittikten sonra, varsayılan olarak Kötü Amaçlı Yazılım sayfasına gelirsiniz, ancak seçeneklerinize aşinalık için Görünüm açılan listenizi kullanın. Kimlik avı veya tehdit kampanyasına girdiysanız bu görünümleri seçin.

> [!div class="mx-imgBorder"]
> ![Threat Explorer'da Görünüm açılan listesinde.](../../media/view-drop-down.png)

Bir güvenlik işlemlerinin (Sec Ops) kişi görmek istediğiniz verileri seçmesi, bunun kapsamın kullanıcı Gönderimleri gibi dar bir görünüm mü yoksa Tüm e-posta gibi daha geniş bir görünüm mü olduğunu bir kez seçmesi  **, Gönderen** düğmesini kullanarak filtreyi ileriye doğru kullanabilir. Filtre eylemlerinizi tamamlamak için Yenile'yi seçmeyi unutmayın.

> [!div class="mx-imgBorder"]
> ![Threat Explorer'daki Gönderen düğmesi.](../../media/sender-drop-down.png)

Gezgin'de veya Gerçek zamanlı algılamada odağın iyi vakit olması katmanlar olarak düşünebilirsiniz. İlki **Görünüm'dır**. İkincisi, filtrelenmiş odak olarak *düşün olabilir*. Örneğin, aşağıdaki gibi kararlarınızı kaydederek bir tehdit bulmak için atmış olduğunu adımları yeniden çıkarabilirsiniz: Sorunu Gezgin'de bulmak için, Alıcı filtresi odağıyla Kötü Amaçlı Yazılım **Görünümü'ne karar verdim**. Bu, adımlarınızı daha kolay bir şekilde taşmanızı sağlar.

> [!TIP]
> Sec Ops, yüksek  değerli hedefleri göz önünde bulundurarak hesapları işaretlemek için Etiketler kullanırsa, Etiketler filtresi odağıyla Kimlik Avı Görünümü gibi seçimler (kullanılıyorsa bir tarih aralığı içerir *)*. Bu, bir zaman aralığı (bazı kimlik avı saldırılarının sektörleri için çok fazla yaşanıyor olduğu tarihler gibi) sırasında yüksek değerli kullanıcı hedeflerine yönlendiren tüm kimlik avı girişimlerini gösterir.

Tarih aralığı denetimleri kullanılarak tarih aralıklarında geliştirmeler yapılır. Burada, Gezgin'i **Kötü Amaçlı Yazılım görünümünde** ve Algılama Teknolojisi filtresi **odağıyla** birlikte görüntüebilirsiniz. Ancak, Sn Ops **ekiplerinin derinlere** inlerine girişlerine olanak sağlayan Gelişmiş filtre düğmesidir.

> [!div class="mx-imgBorder"]
> ![Threat Explorer'da gelişmiş filtre.](../../media/advanced-filter.png)

Gelişmiş **filtreye** tıklanan panel, Sec Ops'ın sorguları kendilerinin oluşturmasına ve bu sorguları görmelerine veya dışarıda bırakmalarına izin vererek açılır. Explorer sayfasındaki hem grafik hem de tablo sonuçlarını yansıtacak.

> [!div class="mx-imgBorder"]
> ![Sorgudan sonuçlar.](../../media/threat-explorer-chart-table.png)

Tablo **hakkında en** yararlı olacak bilgi türüne almak için Sütun seçenekleri düğmesini kullanın:

> [!div class="mx-imgBorder"]
> ![Sütun seçenekleri düğmesi vurgulanmış.](../../media/threat-explorer-column-options.png)

> [!div class="mx-imgBorder"]
> ![Sütunlar'daki kullanılabilir seçenekler.](../../media/column-options.png)

Aynı mikrofonda görüntü seçeneklerinizi test etmek için emin olun. Farklı izleyiciler, aynı verilerin farklı sunularına iyi tepkiyi sağlar. Bazı görüntüleyiciler için **E-posta** Kaynak haritası, bir tehdidin hemen yanındaki Kampanya görüntüleme seçeneğine göre daha çabuk ilgi  gördüğünü veya bundan daha hızlı satın alına olduğunu gösterebilir. Sec Ops, bu ekranlardan, eylemlerinin ne kadar etkili olduğunu göstermek üzere güvenlik ve koruma ihtiyacının altını çizen en iyi noktalar elde etmek için veya daha sonraki bir karşılaştırmada kullanabilir.

> [!div class="mx-imgBorder"]
> ![E-posta Kökenleri haritası.](../../media/threat-explorer-email-origin-map.png)

> [!div class="mx-imgBorder"]
> ![Kampanya görüntüleme seçenekleri.](../../media/threat-explorer-campaign-display.png)

### <a name="email-investigation"></a>E-posta soruşturması

Şüpheli bir e-posta gördüğünüzde, sağdan uçan e-postayı genişletmek için bu adı tıklatın. Burada, Sec Ops'in e-posta varlık sayfasını [görmelerini sağlayan](mdo-email-entity-page.md) başlık mevcuttur.

E-posta varlık sayfası Ayrıntılar, **Ekler, Cihazlar** altında **bulunsa da** **daha düzenli** veriler içeren içeriği bir araya toplar. Bunlar, DMARC sonuçları, e-posta üst bilgisinin bir kopya seçeneğiyle düz metin görüntüsü, güvenli bir şekilde düz bir şekilde oluşturulan eklerle ilgili karar bilgilerini ve bırakılan detonasyonları (bağlantı oluşturulan IP adreslerini ve sayfa veya dosyaların ekran görüntülerini içerebilir) içerir. URL'ler ve onların kararları da bildirilen benzer ayrıntılarla listelenmiştir.

Bu aşamaya ulaşabilirsiniz; e-posta varlık sayfası, düzeltmenin son adımı *için kritik öneme sahip olur*.

> [!div class="mx-imgBorder"]
> ![E-posta varlık sayfası.](../../media/threat-explorer-email-entity-page.png)

> [!TIP]
> Çok sayıda Ek, bulunan URL'ler için bulunan bulunanlar ve güvenli  E-posta önizlemesi de içinde olmak üzere, zengin e-posta varlık sayfası (aşağıda Çözümleme sekmesinde gösterilmiştir) hakkında daha fazla bilgi edinmek için buraya [tıklayın](mdo-email-entity-page.md).

> [!div class="mx-imgBorder"]
> ![E-posta varlık sayfasının Çözümleme sekmesi.](../../media/threat-explorer-analysis-tab.png)

### <a name="email-remediation"></a>E-posta düzeltme

Bir Sec Ops kişisi e-postanın bir tehdit olduğunu algılayana kadar, bir sonraki Gezgin veya Gerçek zamanlı algılama adımı tehditle başa çıkışacak ve düzeltecek. Bu işlem Threat Explorer'a dönerek, sorun e-postanın onay kutusunu seçerek ve **Eylemler düğmesi kullanılarak** yapılabilir.

> [!div class="mx-imgBorder"]
> ![Threat Explorer'da Eylemler düğmesi.](../../media/threat-explorer-email-actions-button.png)

Burada, analist postayı İstenmeyen Posta, Kimlik Avı veya Kötü Amaçlı Yazılım olarak raporlama, alıcılarla bağlantı kurma veya Otomatik Soruşturma ve Yanıt (veya AIR) çalışma kitaplarını tetiklemeyi (Plan 2'niz varsa) içerecek başka soruşturmalar gibi eylemler gerçekleştirebilirsiniz. Bunun yanı sıra, posta temiz olarak da bildiriliyor olabilir.

> [!div class="mx-imgBorder"]
> ![Eylemler açılan listesinde.](../../media/threat-explorer-email-actions-drop-down.png)

## <a name="improvements-to-threat-hunting-experience"></a>Tehdit avı deneyiminde iyileştirmeler

### <a name="alert-id"></a>Uyarı Kimliği

Bir uyarıdan Tehdit Gezgini'ne gezinirken, **Görünüm'e** Uyarı Kimliği'ne göre **filtre uygulanmış olur**. Bu durum Gerçek zamanlı algılama için de geçerlidir. Belirli uyarıyla ilgili iletiler ve bir e-posta toplamı (sayı) gösterilir. İletinin bir uyarının parçası olup olduğunu görmenin yanı sıra bu iletiden ilgili uyarıya da gezinebilirsiniz.

Son olarak, URL'ye uyarı kimliği de dahildir; örneğin: `https://https://security.microsoft.com/viewalerts`

> [!div class="mx-imgBorder"]
> ![Uyarı Kimliği için filtreleme.](../../media/AlertID-Filter.png)

> [!div class="mx-imgBorder"]
> ![Ayrıntılar ayrıntılarında uyarı kimliği.](../../media/AlertID-DetailsFlyout.png)

### <a name="extending-explorer-and-real-time-detections-data-retention-and-search-limit-for-trial-tenants"></a>Deneme kiracıları için Gezgini (ve Gerçek zamanlı algılamaları) veri bekletmeyi ve arama sınırını genişletme

Bu değişiklik kapsamında, analistler Tehdit Gezgini'nde 30 gün boyunca (yedi gün içinde artırılmış) e-posta verilerini arayabilir ve filtrelerini, hem Office P1 için Defender hem de P2 deneme kiracıları için Gerçek zamanlı algılamalar için filtreleyabilecektir. Bu, hem P1 hem de P2 E5 müşterileri için üretim kiracılarını etkilememektedir (burada bekletme varsayılanı 30 gündür).

### <a name="updated-export-limit"></a>Güncelleştirilmiş Dışarı Aktarma sınırı

Threat Explorer'dan dışarı aktarabilirsiniz E-posta kayıtlarının sayısı şu anda 200.000'i (9990'dı) oldu. Dışarı aktarabilirsiniz sütun kümesi değişmeden kalır.

### <a name="tags-in-threat-explorer"></a>Threat Explorer'da Etiketler

> [!NOTE]
> Kullanıcı etiketleri özelliği Önizleme'dedir ve herkes tarafından kullanılamıyor olabilir. Ayrıca, Önizlemeler değişebilir. Sürüm zamanlaması hakkında daha fazla bilgi için yol Microsoft 365 bakın.

Kullanıcı etiketleri, Windows için Microsoft Defender'da belirli kullanıcı Office 365. Lisanslama ve yapılandırma gibi etiketler hakkında daha fazla bilgi için bkz. [Kullanıcı etiketleri](user-tags.md).

Threat Explorer'da, kullanıcı etiketleriyle ilgili bilgileri aşağıdaki deneyimlerde edinebilirsiniz.

#### <a name="email-grid-view"></a>E-posta kılavuz görünümü

Analistler e-posta **kılavuzunda** Etiketler sütununa bakarak, gönderen veya alıcı posta kutularına uygulanmış olan tüm etiketleri görüyorlar. Varsayılan olarak, önce öncelik hesapları *gibi sistem* etiketleri gösterilir.

> [!div class="mx-imgBorder"]
> ![E-posta kılavuz görünümünde etiketlere filtre uygulama.](../../media/tags-grid.png)

#### <a name="filtering"></a>Filtreleme

Etiketler filtre olarak kullanılabilir. Yalnızca öncelikli hesaplar arasında arama veya bu şekilde belirli kullanıcı etiketleri senaryoları kullanma. Belirli etiketlerin olduğu sonuçları da hariç tutabilirsiniz. Araştırma kapsamınızı daraltmak için Etiketleri diğer filtreler ve tarih aralıkları ile birleştirin.

[![Filtre etiketleri.](../../media/tags-filter-normal.png)](../../media/tags-filter-normal.png#lightbox)

> [!div class="mx-imgBorder"]
> ![Etiketlere filtre uygulamaz.](../../media/tags-filter-not.png)

#### <a name="email-detail-flyout"></a>E-posta ayrıntısı çıktısı

Gönderen ve alıcının etiketlerini tek tek görüntülemek için, bir e-posta seçerek ileti ayrıntıları açılır öğesini açın. Özet **sekmesinde** , gönderen ve alıcı etiketleri ayrı ayrı gösterilir. Gönderen ve alıcının tek tek etiketleriyle ilgili bilgiler CSV verileri olarak dışarı aktarabilirsiniz.

> [!div class="mx-imgBorder"]
> ![E-posta Ayrıntıları etiketleri.](../../media/tags-flyout.png)

Etiket bilgileri, URL tıklamaları uçarak çıkışta da gösterilir. Bunu görmek için, Kimlik Avı veya Tüm E-posta görünümüne > **URL'ler** veya **URL Tıklamaları sekmesine** gidin. Tek bir URL uç öğesini seçerek bu URL'ye ilişkin tıklamalar hakkında ek ayrıntıları ve bu tıklamayla ilişkili Etiketler'i de görmek için bu URL'yi seçin.

### <a name="updated-timeline-view"></a>Güncelleştirilmiş Zaman Çizelgesi Görünümü

> [!div class="mx-imgBorder"]
> ![URL etiketleri.](../../media/tags-urls.png)
>
Daha fazla bilgi edinmek için [bu videoyu izleyin](https://www.youtube.com/watch?v=UoVzN0lYbfY&list=PL3ZTgFEc7LystRja2GnDeUFqk44k7-KXf&index=4).

## <a name="extended-capabilities"></a>Genişletilmiş özellikler

### <a name="top-targeted-users"></a>En çok hedefli kullanıcılar

En Üst Kötü Amaçlı Yazılım Aileleri **, Kötü Amaçlı Yazılım bölümünde** en çok hedefli kullanıcıları gösterir. En çok hedefli kullanıcılar Kimlik Avı ve Tüm E-posta görünümleri de genişletildi. Analistler, en çok hedefli beş kullanıcıyla birlikte her görünümde her kullanıcı için deneme sayısını görebilir.

Güvenlik işlemleri, kişilerin her e-posta görünümü için çevrimdışı çözümleme yapmak için hedefli kullanıcılar listesini, 3.000'e kadar olan deneme sayısıyla birlikte dışarı aktarabilecektir. Ayrıca, deneme sayısını seçmek (örneğin, aşağıdaki resimde 13 girişim) Tehdit Gezgini'nde filtrelenmiş bir görünüm açar, böylece e-postalar ve o kullanıcı için tehditlere karşı daha fazla ayrıntı görebilirsiniz.

> [!div class="mx-imgBorder"]
> ![En çok hedefli kullanıcılar.](../../media/Top_Targeted_Users.png)

### <a name="exchange-transport-rules"></a>Exchange aktarım kurallarını taşıma

Güvenlik işlemleri ekibi, E-posta kılavuz Exchange iletiye uygulanan tüm aktarım kurallarını (veya Posta akış kurallarını) görebilir. **Kılavuzda Sütun seçenekleri'ne** ve sonra **sütun Exchange Aktarım Kuralı Ekle'ye** tıklayın. Aşağıdaki Exchange aktarım kuralları seçeneği, e-postanın **Ayrıntılar** uç bölmesinde de görünür.

İletiye uygulanan aktarım kurallarının adları ve GUID'leri görüntülenir. Analistler aktarım kuralının adını kullanarak iletileri arayabilir. Bu bir CONTAINS aramasıdır ve bu da kısmi aramalar da yap anlamına gelir.

> [!IMPORTANT]
> Exchange aktarım kuralı arama ve ad kullanılabilirliği, size atanan özel role bağlıdır. Aktarım kuralı adlarını ve aramalarını görüntülemek için aşağıdaki rollerden veya izinlerden biri gerekir. Bununla birlikte, aşağıdaki roller veya izinler olmadan bile, analist E-posta Ayrıntıları'nın aktarım kuralı etiketini ve GUID bilgilerini görebilir. E-posta Kılavuzlarında, E-posta uç uçları, Filtreler ve Dışarı Aktarma'daki diğer kayıt görüntüleme deneyimleri etkilenmez.
>
> - Exchange Online- Veri Kaybını Önleme: Tüm
> - Exchange Online - O365SupportViewConfig: All
> - Microsoft Azure Active Directory veya Exchange Online - Güvenlik Yöneticisi: All
> - Azure Active Directory veya Exchange Online - Güvenlik Okuyucu: All
> - Exchange Online Aktarım Kuralları: Tüm
> - Exchange Online - View-Only Yapılandırma: All
>
> E-posta kılavuzu, Ayrıntılar uçarak çıkış ve Dışarı Aktarıldı CSV içinde ETR'ler aşağıda gösterildiği gibi Ad/GUID ile gösterilir.
>
> > [!div class="mx-imgBorder"]
> > ![Exchange Aktarım Kuralları.](../../media/ETR_Details.png)

### <a name="inbound-connectors"></a>Gelen bağlayıcıları

Bağlayıcılar, e-postanın e-postanız e-postanıza veya Microsoft 365 veya bir Office 365 koleksiyonudur. Bunlar, herhangi bir güvenlik kısıtlaması veya denetimi uygulamana olanak sağlar. Threat Explorer'da, e-postayla ilgili bağlayıcıları ekleyebilirsiniz ve bağlayıcı adlarını kullanarak e-postaları arayabilirsiniz.

Bağlayıcılar için arama bir CONTAINS sorgusudur ve bu da kısmi anahtar sözcük aramalarına yardımcı olduğu anlamına gelir:

> [!div class="mx-imgBorder"]
> ![Bağlayıcı ayrıntıları.](../../media/Connector_Details.png)

## <a name="required-licenses-and-permissions"></a>Gerekli lisanslar ve izinler

Explorer veya [Gerçek zamanlı algılamaları Office 365](defender-for-office-365.md) için Microsoft Defender'a sahipsiniz.

- Explorer, Plan 2 için Defender'Office 365 dahil edilir.
- Gerçek zamanlı algılamalar raporu, Plan 1'den Office 365 Defender'a dahildir.
- Lisans atamayı, lisanslar için Defender ile korunması gereken tüm kullanıcılara Office 365. Gezgin ve Gerçek zamanlı algılamalar lisanslı kullanıcılar için algılama verilerini gösterir.

Gezgin'i veya Gerçek zamanlı algılamaları görüntülemek ve kullanmak için aşağıdaki izinlere sahip olmak gerekir:

- Microsoft 365 Defender portalında:
  - Kuruluş Yönetimi
  - Güvenlik Yöneticisi (bu, Azure Active Directory merkezinden atanabilir)<https://aad.portal.azure.com>
  - Güvenlik Okuyucu
- Exchange Online:
  - Kuruluş Yönetimi
  - View-Only Yönetimi
  - View-Only'i seçin
  - Uyumluluk Yönetimi

Roller ve izinler hakkında daha fazla bilgi edinmek için aşağıdaki kaynaklara bakın:

- [Microsoft 365 Defender portalında izinler](permissions-microsoft-365-security-center.md)
- [Web'de Exchange Online](/exchange/permissions-exo/permissions-exo)
- [Exchange Online PowerShell](/powershell/exchange/exchange-online-powershell)

## <a name="more-information"></a>Daha fazla bilgi

- [Teslim edilen kötü amaçlı e-postaları bulma ve araştırma](investigate-malicious-email-that-was-delivered.md)
- [SharePoint Online, OneDrive ve Microsoft Teams'de algılanan kötü amaçlı dosyaları Microsoft Teams](mdo-for-spo-odb-and-teams.md)
- [Threat Explorer'daki görünümlere genel bakış (ve Gerçek zamanlı algılamalar)](threat-explorer-views.md)
- [Tehdit koruması durum raporu](view-email-security-reports.md#threat-protection-status-report)
- [Microsoft Tehdit Koruması'da otomatik araştırma ve yanıt](automated-investigation-response-office.md)
- [E-posta Varlık Sayfası içeren e-postaları araştırma](mdo-email-entity-page.md)
