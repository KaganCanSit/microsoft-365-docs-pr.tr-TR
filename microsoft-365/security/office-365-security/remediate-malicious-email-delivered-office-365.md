---
title: Office 365 teslim edilen kötü amaçlı e-postayı düzeltme
author: msfttracyp
ms.author: tracyp
manager: dansimp
ms.topic: article
ms.collection: M365-security-compliance
audience: admin
f1.keywords:
- NOCSH
ms.localizationpriority: medium
MS.collection: ''
search.appverid: MET150
description: Tehdit düzeltme
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 6102d1e7d3b7e39787c3787b8bc0851eedbdcefb
ms.sourcegitcommit: 18bc521a88b7b521bccb0e69d02deac764218087
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/16/2022
ms.locfileid: "66115553"
---
# <a name="remediate-malicious-email-delivered-in-office-365"></a>Office 365'te teslim edilen kötü amaçlı e-postaları düzeltme

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Uygulandığı öğe**
- [Office 365 için Microsoft Defender plan 2](defender-for-office-365.md)

Düzeltme, bir tehdide karşı belirlenmiş bir eylem gerçekleştirme anlamına gelir. Kuruluşunuza gönderilen kötü amaçlı e-postalar sistem tarafından, sıfır saatlik otomatik temizleme (ZAP) aracılığıyla veya gelen *kutusuna taşıma*, *gereksiz öğeye taşıma*, *silinmiş öğelere taşıma*, *geçici silme* veya *sabit silme* gibi düzeltme eylemleri aracılığıyla güvenlik ekipleri tarafından temizlenebilir. Office 365 için Microsoft Defender Plan 2/E5, güvenlik ekiplerinin el ile ve otomatik araştırma yoluyla e-posta ve işbirliği işlevselliğindeki tehditleri düzeltmesini sağlar.

> [!NOTE]
> Kötü amaçlı e-postayı düzeltmek için güvenlik ekiplerinin kendilerine Atanmış *Arama ve Temizleme* rolüne sahip olması gerekir. Rol ataması[, Microsoft 365 Defender portalındaki izinler](permissions-microsoft-365-security-center.md) aracılığıyla yapılır.

## <a name="what-you-need-to-know-before-you-begin"></a>Başlamadan önce bilmeniz gerekenler

Yöneticiler e-postalar üzerinde gerekli eylemleri gerçekleştirebilir, ancak bu eylemlerin onaylanması için Microsoft 365 Defender portalındaki **E-posta & işbirliği** izinlerinde Kendilerine *Arama ve Temizleme* rolü atanmış olmalıdır. Rol gruplarından birine *Arama ve temizleme"* rolü eklenmeden, eylemi yürütemezler.

E-posta eylemleri arka uçta otomatik araştırma oluşturduğundan *, Otomatik Araştırma'yı* etkinleştirmeniz gerekir. **Ayarlar** \> **Uç Noktalar** \> **Gelişmiş özellikleri'ne** gidin ve **Otomatik Araştırma'yi** açın.

## <a name="manual-and-automated-remediation"></a>El ile ve otomatik düzeltme

Güvenlik ekipleri, Explorer'daki arama ve filtreleme özelliklerini kullanarak tehditleri el ile tanımladığında *el ile avlanma* gerçekleşir. El ile e-posta düzeltmesi, düzeltilmesi gereken bir e-posta kümesi tanımlandıktan sonra herhangi bir e-posta görünümü (*Kötü Amaçlı Yazılım*, *Kimlik Avı* veya *Tüm e-posta*) aracılığıyla tetiklenebilir.

:::image type="content" source="../../media/microsoft-365-defender-threat-explorer-manual-remediation.png" alt-text="Office 365 Gezgini'nde tarihe göre el ile avcılık ekran görüntüsü.":::

Güvenlik ekipleri, e-postaları çeşitli yollarla seçmek için Explorer'ı kullanabilir:

- E-postaları el ile seçme: Çeşitli görünümlerde filtreleri kullanın. Düzeltmek için en fazla 100 e-posta seçin.

- Sorgu seçimi: Üstteki Tümünü seç düğmesini kullanarak sorgunun **tamamını seçin** . aynı sorgu, işlem merkezi posta gönderme ayrıntılarında da gösterilir. Müşteriler tehdit gezgininden en fazla 200.000 e-posta gönderebilir.  

- Dışlama ile sorgu seçimi: Bazen güvenlik operasyonları ekipleri bir sorgunun tamamını seçerek ve belirli e-postaları sorgudan el ile dışlayarak e-postaları düzeltmek isteyebilir. Bunu yapmak için bir yönetici **Tümünü seç** onay kutusunu kullanabilir ve e-postaları el ile dışlamak için aşağı kaydırabilir. Sorgu en fazla 1.000 e-posta içerebilir. En fazla dışlama sayısı 100'dür.

Explorer aracılığıyla e-postalar seçildikten sonra, doğrudan işlem yaparak veya bir eylem için e-postaları kuyruğa alarak düzeltmeye başlayabilirsiniz:

- Doğrudan onay: *Gelen kutusuna taşıma*, *gereksiz öğeye taşıma*, *silinmiş öğelere taşıma*, *geçici silme* veya *sabit silme* gibi eylemler uygun izinlere sahip güvenlik personeli tarafından seçildiğinde ve düzeltmedeki sonraki adımlar izlendiğinde, düzeltme işlemi seçilen eylemi yürütmeye başlar.
> [!NOTE]
> Düzeltme başlatılırken paralel olarak bir uyarı ve araştırma oluşturur. Uyarı, uyarı kuyruğunda güvenlik personelinin varlığı düzeltme eylemini gerçekleştirmesini öneren "Yönetici tarafından gönderilen yönetim eylemi" adıyla gösterilir. Eylemi gerçekleştiren kişinin adı, destekleyici araştırma bağlantısı, zaman vb. gibi ayrıntılar sunar. Varlıklarda düzeltme gibi sert bir eylemin her gerçekleştirildiğini bilmek gerçekten iyi çalışır. Tüm bu eylemler **Eylemler & Gönderimler** \> **İşlem merkezi**  -> **Geçmişi sekmesinde** (genel önizleme) izlenebilir.

- İki adımlı onay: "Düzeltmeye ekle" eylemi, uygun izinlere sahip olmayan veya eylemi yürütmek için beklemesi gereken yöneticiler tarafından yapılabilir. Bu durumda, hedeflenen e-postalar bir düzeltme kapsayıcısına eklenir. Düzeltme yürütülmeden önce onay gerekir.

**Otomatik araştırma ve yanıt** eylemleri uyarılar veya Explorer'dan güvenlik operasyonları ekipleri tarafından tetiklenir. Bunlar, bir güvenlik operasyonları ekibi tarafından onaylanması gereken önerilen düzeltme eylemlerini içerebilir. Bu eylemler otomatik araştırmanın **Eylem** sekmesinde yer alır.

> [!div class="mx-imgBorder"]
> [![Zap yürütme zamanını gösteren "Zapped" sayfasındaki kötü amaçlı yazılım içeren posta.](../../media/tp-RemediationArticle3.png)](../../media/tp-RemediationArticle3.png#lightbox)

Gezgin, Gelişmiş avcılık veya Otomatik araştırma aracılığıyla oluşturulan tüm düzeltmeler (doğrudan onaylar) İşlem Merkezi'nde görüntülenir. Bunlara **Eylemler & Gönderimler** \> **İşlem merkezi**  -> **Geçmişi sekmesinin** altındaki sol gezinti paneli aracılığıyla erişin.

Gezgin veya Gelişmiş avcılık veya Otomatik araştırma aracılığıyla oluşturulan tüm düzeltmeler (doğrudan onaylar) İşlem Merkezi'nde görüntülenir. Bunlara **Eylemler & Gönderimler** \> **İşlem merkezi**  -> **Geçmişi sekmesinin** altındaki sol gezinti paneli aracılığıyla erişin. 

İki aşamalı onay işlemini kullanarak onay bekleyen el ile eylemler (1. bir güvenlik işlemi ekip üyesi tarafından düzeltmeye ekle, 2. başka bir güvenlik işlemi ekip üyesi tarafından gözden geçirilir ve onaylanır) yalnızca eski Office 365 için Defender işlem merkezinde **İnceleme** \> **İşlem merkezi'nde** görünür; olaylar/araştırmalarda ve Birleşik İşlem merkezinde görünmez.

> [!NOTE]
> İki adımlı onay: Yalnızca office işlem merkezinde bulunan eylemler **İşlem Merkezi'ni** **Gözden Geçir** \>

:::image type="content" source="../../media/microsoft-365-defender-action-center-history.png" alt-text="Birleşik İşlem Merkezi size 30 günlük düzeltme eylemleri gösterir.":::

Birleşik İşlem Merkezi son 30 güne ait düzeltme eylemlerini gösterir. Gezgin aracılığıyla gerçekleştirilen eylemler, düzeltme oluşturulduğunda güvenlik operasyonları ekibinin sağladığı ada ve onay kimliğine, Araştırma Kimliği'ne göre listelenir. Otomatik araştırmalarda gerçekleştirilen eylemler, araştırmayı tetikleyen ilgili uyarıyla başlayan *başlıklara (Zap e-posta kümesi* gibi) sahiptir.

Düzeltme adı, onay kimliği, Araştırma Kimliği, oluşturma tarihi, açıklama, durum, eylem kaynağı, eylem türü, karar verme ölçütü, durum gibi ilgili ayrıntıları görüntülemek için herhangi bir düzeltme öğesini açın. Ayrıca eylem ayrıntılarını, e-posta kümesi ayrıntılarını, uyarıyı ve Olay ayrıntılarını içeren bir yan bölme açar.

- *Araştırma sayfasını açın* ; daha az ayrıntı ve sekme içeren bir yönetici Araştırması açılır. Aşağıdaki gibi ayrıntıları gösterir: ilgili uyarı, düzeltme için seçilen varlık, gerçekleştirilen eylem, düzeltme durumu, varlık sayısı, günlükler, eylemi onaylayan. Bu araştırma, yönetici tarafından el ile yapılan araştırmanın kaydını tutar ve yönetici tarafından yapılan seçimlerin ayrıntılarını içerir, bu nedenle yönetici eylem araştırması olarak adlandırılır. Araştırma üzerinde işlem yapmanıza ve zaten onaylanmış durumda olduğunu uyarmanıza gerek yoktur.
- *E-posta sayısı* Tehdit Gezgini aracılığıyla gönderilen e-postaların sayısını görüntüler. Bu e-postalar eyleme dönüştürülebilir veya eyleme dönüştürülemez olabilir.
- *Eylem günlükleri* Başarılı, başarısız ve zaten hedefte gibi düzeltme durumlarının ayrıntılarını gösterin.

:::image type="content" source="../../media/microsoft-365-defender-action-center-history-panel.png" alt-text="Gelen Kutusuna Taşı seçeneğinin açık olduğu İşlem Merkezi.":::

  - **Eyleme dönüştürülebilir**: Aşağıdaki bulut posta kutusu konumlarındaki e-postalar üzerinde işlem yapılabilir ve taşınabilir:
    - Gelen kutusu
    - Önemsiz
    - Klasör silindi
    - Geçici olarak silinen klasör

      > [!NOTE]
      > Şu anda yalnızca posta kutusuna erişimi olan bir kullanıcı geçici olarak silinen bir klasörden öğeleri kurtarabilir.

  - **Eyleme dönüştürülemez**: Aşağıdaki konumlardaki e-postalar üzerinde işlem yapılamaz veya düzeltme eylemlerinde taşınamaz:
    - Karantina
    - Sabit silinmiş klasör
    - Şirket içi/dış
    - Başarısız/bırakıldı

  Şüpheli iletiler düzeltilebilir veya düzeltilemez olarak kategorilere ayrılmıştır. Çoğu durumda, düzeltilebilir ve düzeltilemez iletiler, gönderilen toplam ileti toplamına eşit şekilde birleştirilir. Ancak nadir durumlarda bu doğru olmayabilir. Sistem gecikmeleri, zaman aşımları veya süresi dolmuş iletiler nedeniyle bu durum oluşabilir. İletilerin süresi, kuruluşunuzun Gezgin saklama süresine göre dolar.

  Kuruluşunuzun Explorer saklama döneminden sonra eski iletileri düzeltmediğiniz sürece, sayı tutarsızlıkları görürseniz öğeleri düzeltmeyi denemeniz önerilir. Sistem gecikmeleri için düzeltme güncelleştirmeleri genellikle birkaç saat içinde yenilenir.

  Kuruluşunuzun Explorer'da e-posta saklama süresi 30 günse ve 29-30 gün geriye giden e-postaları düzeltiyorsanız, posta gönderme sayıları her zaman bir şey ifade etmeyebilir. E-postalar bekletme süresinden zaten taşınmaya başlamış olabilir.

  Düzeltmeler bir süre "Sürüyor" durumunda takılırsa, bunun nedeni büyük olasılıkla sistem gecikmeleridir. Düzeltmesi birkaç saat kadar sürebilir. Bazı e-postalar sistem gecikmelerinden dolayı düzeltmenin başlangıcında sorguya dahil edilmeyebileceği için posta gönderme sayılarında varyasyonlar görebilirsiniz. Bu gibi durumlarda düzeltmeyi yeniden denemek iyi bir fikirdir.

  > [!NOTE]
  > En iyi sonuçlar için düzeltme 50.000 veya daha az toplu işlemle yapılmalıdır.

  Düzeltme sırasında yalnızca düzeltilebilir e-postalar üzerinde işlem yapılabilir. Düzeltilemeyen e-postalar, bulut posta kutularında depolanmadıkları için Office 365 e-posta sistemi tarafından düzeltilemez.

  Yöneticiler gerekirse karantinadaki e-postalar üzerinde işlem yapabilir, ancak el ile temizlenmediği takdirde bu e-postaların süresi karantina dışı kalır. Varsayılan olarak, kötü amaçlı içerik nedeniyle karantinaya alınan e-postalara kullanıcılar tarafından erişilemez, bu nedenle güvenlik personeli karantinadaki tehditlerden kurtulmak için herhangi bir işlem yapmak zorunda değildir. E-postalar şirket içinde veya dışındaysa, şüpheli e-postayı ele almak için kullanıcıyla iletişime geçilebilir. Ya da yöneticiler kaldırma için ayrı e-posta sunucusu/güvenlik araçları kullanabilir. Bu e-postalar, Gezgin'de *teslim konumu = şirket içi* dış filtre uygulanarak tanımlanabilir. Başarısız veya bırakılan e-postalarda veya kullanıcılar tarafından erişilemeyen e-postalarda, bu postalar posta kutusuna ulaşmadığından hafifletilecek bir e-posta olmaz.

 
- **Eylem günlükleri**: Düzeltilmiş, başarılı, başarısız, zaten hedefte olan iletileri gösterir.

  Durum şu olabilir:

  - **Başlatıldı**: Düzeltme tetikleniyor.
    - **Kuyruğa alındı**: Düzeltme, e-postaların azaltılması için sıraya alındı.
    - **Devam ediyor**: Azaltma devam ediyor.
    - **Tamamlandı**: Düzeltilebilir tüm e-postalarda azaltma işlemi başarıyla veya bazı hatalarla tamamlandı.
    - **Başarısız**: Hiçbir düzeltme başarılı olmadı.

  Yalnızca düzeltilebilir e-postalar üzerinde işlem yapılabilir olduğundan, her e-postanın temizleme işlemi başarılı veya başarısız olarak gösterilir. Düzeltilebilir e-postaların toplamından başarılı ve başarısız düzeltmeler bildirilir.

  - **Başarılı**: Düzeltilebilir e-postalarda istenen eylem gerçekleştirilir. Örneğin: Bir yönetici posta kutularından e-postaları kaldırmak istediğinden, yönetici e-postaları geçici silme eylemini üstlenir. Eylem gerçekleştirildikten sonra özgün klasörde düzeltilebilir bir e-posta bulunmazsa, durum başarılı olarak gösterilir.

  - **Hata**: Düzeltilebilir e-postalarda istenen eylem başarısız oldu. Örneğin: Bir yönetici posta kutularından e-postaları kaldırmak istediğinden, yönetici e-postaları geçici silme eylemini üstlenir. Eylem gerçekleştirildikten sonra da posta kutusunda düzeltilebilir bir e-posta bulunursa, durum başarısız olarak gösterilir.
  
  - **Zaten hedefte**: İstenen eylem e-postada zaten yapıldı VEYA e-posta hedef konumda zaten mevcuttu. Örneğin: Bir e-posta, yönetici tarafından ilk günde Gezgin aracılığıyla geçici olarak silindi. Daha sonra benzer e-postalar 2. günde gösterilir ve bu e-postalar yine yönetici tarafından geçici olarak silinir. Bu e-postaları seçerken, yönetici ilk günden geçici olarak silinmiş olan bazı e-postaları seçer. Artık bu e-postalar üzerinde bir daha işlem yapılmayacak, yalnızca "zaten hedefte" olarak görünecektir, çünkü hedef konumda mevcut oldukları için bu e-postalar üzerinde hiçbir işlem yapılmamıştır.

  - **Yeni**: Eylem *Günlüğü'ne Zaten var olan bir hedef* sütun eklendi. Bu özellik, postanın zaten düzeltilip düzeltildiğinin sinyalini vermek için Tehdit Gezgini'ndeki en son teslim konumunu kullanır. *Zaten hedefte olan* güvenlik ekiplerinin, hala ele alınması gereken toplam ileti sayısını anlamasına yardımcı olur.

Eylemler yalnızca Tehdit Gezgini'nin Gelen Kutusu, Gereksiz, Silinmiş ve Geçici Olarak Silinmiş klasörlerindeki iletilerde gerçekleştirilebilir. Aşağıda yeni sütunun nasıl çalıştığına ilişkin bir örnek verilmiş. Gelen Kutusu'nda bulunan iletide *geçici silme eylemi* gerçekleştirilir, ardından ileti ilkelere göre işlenir. Bir sonraki geçici silme işlemi gerçekleştirildiğinde, bu ileti 'Zaten hedefte' sütununun altında gösterilir ve yeniden ele alınması gerekmeyen bir işarettir.

Düzeltme ayrıntılarını görüntülemek için eylem günlüğündeki herhangi bir öğeyi seçin. Ayrıntılarda "başarılı" veya "posta kutusunda bulunamadı" ifadesi varsa, bu öğe posta kutusundan zaten kaldırılmıştır. Bazen düzeltme sırasında bir sistem hatası olur. Bu gibi durumlarda, düzeltme eylemini yeniden denemek iyi bir fikirdir.

Büyük toplu e-postaları düzeltme durumunda, Posta Gönderimi yoluyla düzeltme için gönderilen iletileri ve Eylem Günlükleri aracılığıyla düzeltilen iletileri dışarı aktarın. Dışarı aktarma sınırı 100.000 kayda yükseltilir.

 Yöneticiler, e-posta iletilerini Gereksiz, Gelen Kutusu veya Silinmiş öğeler klasörüne taşıma gibi düzeltme eylemleri gerçekleştirebilir ve Gelişmiş Tehdit Avcılığı sayfalarından geçici olarak silinen veya sabit silme gibi eylemleri silebilir.

:::image type="content" source="../../media/microsoft-365-defender-advanced-hunting-actions-pane.png" alt-text="Gelişmiş Tehdit Avcılığı, Eylemleri Gerçekleştir paneli ve istediğiniz eylemleri yapın.":::

Düzeltme, tehditleri azaltır, şüpheli e-postaları giderir ve kuruluşun güvenli kalmasına yardımcı olur.
