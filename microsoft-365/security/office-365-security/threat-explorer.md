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
description: Tehditleri verimli bir şekilde araştırmak ve yanıtlamak için, Microsoft 365 Defender portalında Gezgin'i ve Gerçek zamanlı algılamaları kullanın.
ms.custom:
- seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: b3ff79ead1e337bb78772109e57d34836d0f4ec9
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2022
ms.locfileid: "63681622"
---
# <a name="threat-explorer-and-real-time-detections"></a>Tehdit Gezgini ve Gerçek zamanlı algılamalar

**Geçerli olduğu yer:**
- [1. plan Office 365 plan 2 için Microsoft Defender](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

[Kuruluşta Office 365 için Microsoft Defender](defender-for-office-365.md) varsa ve gerekli izinlere sahipsinizse [,](#required-licenses-and-permissions) **Explorer** veya Gerçek zamanlı algılamalar **(eski** adı *Gerçek* zamanlı raporlar) varsa, nelerin yeni olduğunu [bakın](#new-features-in-threat-explorer-and-real-time-detections)!. Güvenlik ve Uyumluluk &'nde Tehdit **yönetimi'ne** gidin ve Gezgin'i veya Gerçek zamanlı   **algılamalar'ı seçin**.

|Microsoft Defender for Office 365 Plan 2 ile şunları görüyorsunuz:|Microsoft Defender for Office 365 Plan 1 ile şunları görüyorsunuz:|
|---|---|
|![Tehdit gezgini.](../../media/threatmgmt-explorer.png)|![Gerçek zamanlı algılamalar](../../media/threatmgmt-realtimedetections.png)|

Gezgin veya Gerçek zamanlı algılamalar, güvenlik işlemleri ekibimizin tehditleri etkili bir şekilde incelemelerine ve yanıtlamalarına yardımcı olur. Rapor aşağıdaki görüntüye benzer:

![Tehdit yönetimi Gezgini'ne \> gidin.](../../media/cab32fa2-66f1-4ad5-bc1d-2bac4dbeb48c.png)

Bu raporla şunlarıabilirsiniz:

- [Güvenlik özellikleri tarafından algılanan kötü amaçlı Microsoft 365 görme](#see-malware-detected-in-email-by-technology)
- [Kimlik avı URL'sini görüntüleme ve karar verilerine tıklama](#view-phishing-url-and-click-verdict-data)
- [Gezgin'de bir görünümden otomatik bir araştırma](#start-automated-investigation-and-response) ve yanıt işlemi başlatın (yalnızca Plan 2 Office 365 Defender)
- [Kötü amaçlı e-postaları araştırma ve daha fazlası](#more-ways-to-use-explorer-and-real-time-detections)

## <a name="improvements-to-threat-hunting-experience"></a>Tehdit Arama Deneyiminde Geliştirmeler


### <a name="introduction-of-alert-id-for-defender-for-office-365-alerts-within-explorerreal-time-detections"></a>Gezgin/Gerçek zamanlı algılamalar içinde Office 365 için Defender Uyarı Kimliği'ne Giriş

Bugün, bir uyarıdan Tehdit Gezgini'ne ilerlerseniz, Gezgin içinde filtrelenmiş bir görünüm açar ve bu görünüm Uyarı ilkesi kimliğine göre filtrelenmiş olarak açılır (Uyarı ilkesi için benzersiz bir tanımlayıcı olan ilke kimliği).
Bu tümleştirmeyi, hem belirli uyarıyla hem de e-posta sayısıyla ilgili iletileri görmeniz için Tehdit Gezgini'nde ve Gerçek zamanlı algılamalarda uyarı kimliğini (aşağıda bir uyarı kimliği örneğine bakın) tanıtarak daha ilgili hale yapıyoruz. Ayrıca, bir iletinin bir uyarının parçası olup olduğunu görmenin yanı sıra bu iletiden belirli bir uyarıya da gezinebilirsiniz.

Tek bir uyarıyı görüntülerken, UYARı Kimliği URL'nin içinde kullanılabilir; bir örnek olarak .`https://protection.office.com/viewalerts?id=372c9b5b-a6c3-5847-fa00-08d8abb04ef1`

> [!div class="mx-imgBorder"]
> ![Uyarı Kimliği için filtreleme.](../../media/AlertID-Filter.png)

> [!div class="mx-imgBorder"]
> ![Ayrıntılar ayrıntılarında uyarı kimliği.](../../media/AlertID-DetailsFlyout.png)

### <a name="extending-the-explorer-and-real-time-detections-data-retention-and-search-limit-for-trial-tenants-from-7-to-30-days"></a>Deneme kiracıları için Gezginin (ve Gerçek zamanlı algılamaların) veri bekletme süresini ve arama sınırını 7 ile 30 gün arasında uzatma

Bu değişiklik kapsamında, hem Office P1 için Defender hem de P2 deneme kiracıları için Tehdit Gezgini/Gerçek zamanlı algılamalarda 30 gün boyunca (önceki 7 gün içinde bir artış) e-posta verilerini arayabilir ve filtreleyebilirsiniz.
Bu durum, zaten 30 günlük veri bekletme ve arama özelliklerine sahip olan P1 ve P2/E5 müşterilerinin üretim kiracılarını etkilenmez.

### <a name="updated-limits-for-export-of-records-for-threat-explorer"></a>Threat Explorer için kayıtların dışarı aktarması için güncelleştirilmiş sınırlar

Bu güncelleştirme kapsamında, Threat Explorer'dan dışarı aktarılabilir E-posta kayıtlarının satır sayısı 9990'dan 200.000 kayıta artırıldı. Dışarı aktarabilir sütun kümesi şu anda aynı kalır, ancak satır sayısı geçerli sınırdan artacaktır.

### <a name="tags-in-threat-explorer"></a>Threat Explorer'da Etiketler

> [!NOTE]
> Kullanıcı etiketleri özelliği *Önizleme'dedir*, herkes tarafından kullanılamaz ve değişebilir. Sürüm zamanlaması hakkında daha fazla bilgi için yol Microsoft 365 bakın.

Kullanıcı etiketleri, Windows için Microsoft Defender'da belirli kullanıcı Office 365. Lisanslama ve yapılandırma gibi etiketler hakkında daha fazla bilgi için bkz. [Kullanıcı etiketleri](user-tags.md).

Threat Explorer'da, kullanıcı etiketleriyle ilgili bilgileri aşağıdaki deneyimlerde edinebilirsiniz.

#### <a name="email-grid-view"></a>E-posta kılavuz görünümü

**E-posta** kılavuzunda Etiketler sütunu, gönderen veya alıcı posta kutularına uygulanmış olan tüm etiketleri içerir. Varsayılan olarak, önce öncelik hesapları gibi sistem etiketleri gösterilir.

> [!div class="mx-imgBorder"]
> ![E-posta kılavuz görünümünde etiketlere filtre uygulama.](../../media/tags-grid.png)

#### <a name="filtering"></a>Filtreleme

Etiketleri filtre olarak kullanabilirsiniz. Öncelik hesapları veya belirli kullanıcı etiketleri senaryoları arasında tek bir aramanın gerçekleşmesi. Belirli etiketlerin olduğu sonuçları da hariç tutabilirsiniz. Araştırma kapsamınızı daraltmak için bu işlevi diğer filtrelerle birleştirin.

[![Filtre etiketleri.](../../media/tags-filter-normal.png)](../../media/tags-filter-normal.png#lightbox)

> [!div class="mx-imgBorder"]
> ![Etiketlere filtre uygulamaz.](../../media/tags-filter-not.png)

#### <a name="email-detail-flyout"></a>E-posta ayrıntısı çıktısı

Gönderen ve alıcının etiketlerini tek tek görüntülemek için, ileti ayrıntıları açılır öğesini açmak istediğiniz konuyu seçin. Özet **sekmesinde** , gönderen ve alıcı etiketleri e-posta için varsa, ayrı ayrı gösterilir.
Gönderen ve alıcının tek tek etiketleriyle ilgili bilgiler de dışarı aktarıldı CSV verilerine genişletildi. Burada bu ayrıntıları iki ayrı sütunda gösterebilirsiniz.

> [!div class="mx-imgBorder"]
> ![E-posta Ayrıntıları etiketleri.](../../media/tags-flyout.png)

Etiket bilgileri, URL tıklamaları uçarak çıkışta da gösterilir. Görüntülemek için Kimlik Avı veya Tüm E-posta görünümüne ve ardından URL'ler veya URL **Tıklamaları** **sekmesine** gidin. Tek bir URL uç öğesini seçerek bu URL'ye ilişkin tıklamalar hakkında ek ayrıntıları (bu tıklamayla ilişkili etiketler dahil) görüntüye ekleyin.

### <a name="updated-timeline-view"></a>Güncelleştirilmiş Zaman Çizelgesi Görünümü

> [!div class="mx-imgBorder"]
> ![URL etiketleri.](../../media/tags-urls.png)
>
Daha fazla bilgi edinmek için [bu videoyu izleyin](https://www.youtube.com/watch?v=UoVzN0lYbfY&list=PL3ZTgFEc7LystRja2GnDeUFqk44k7-KXf&index=4).

## <a name="improvements-to-the-threat-hunting-experience-upcoming"></a>Tehdit avı deneyiminde iyileştirmeler (yaklaşan)

### <a name="updated-threat-information-for-emails"></a>E-postalar için güncelleştirilmiş tehdit bilgileri

E-posta kayıtları için veri doğruluğunu ve tutarlılığını artırmak için platforma ve veri kalitesi geliştirmelere odaklandık. Geliştirmeler arasında, ZAP işleminin bir parçası olarak e-postada tek bir kayıtta yapılan eylemler gibi ön teslim ve teslim sonrası bilgilerini birleştirme vardır. İstenmeyen posta kararları, varlık düzeyindeki tehdit (örneğin, kötü amaçlı URL) ve en son teslim konumları gibi ek ayrıntılar da mevcuttur.

Bu güncelleştirmelerden sonra, iletiyi etkileyen farklı teslim sonrası olaylardan bağımsız olarak her ileti için tek bir girdi gösterilir. Eylemler ZAP, el ile düzeltme (yönetici eylemi, dinamik teslim, başka bir ifadeyle) içerebilir.

Kötü amaçlı yazılım ve kimlik avı tehditlerini göstermenin yanı sıra, bir e-postayla ilişkilendirilmiş istenmeyen posta kararını da görüyorsunuz. E-postanın içinde, ilgili algılama teknolojileriyle birlikte e-postayla ilişkili tüm tehditlere bakın. E-postada sıfır, bir veya birden çok tehdit olabilir. E-posta çıkış bölümünün **Ayrıntılar bölümünde** mevcut tehditleri bulabilirsiniz. Birden çok tehdit (kötü amaçlı yazılım ve kimlik avı gibi)  için Algılama teknik alanı, tehdit algılama eşlemesini gösterir. Bu, tehdide yönelik algılama teknolojisidir.

Algılama teknolojileri kümesi artık yeni algılama yöntemlerini ve istenmeyen posta algılama teknolojilerini de içerir. Farklı e-posta görünümlerde (Kötü Amaçlı Yazılım, Kimlik Avı, Tüm E-posta) sonuçları filtrelemek için aynı algılama teknolojileri kümesi kullanabilirsiniz.

> [!NOTE]
> Karar çözümlemesi varlıklara bağlı olmayabilir. Örnek olarak, bir e-posta kimlik avı veya istenmeyen posta olarak sınıflandırılabilir, ancak kimlik avı/istenmeyen posta kararının damgalanmasına neden olan bir URL yoktur. Bunun nedeni, e-postaya karar atamadan önce filtrelerin e-posta içeriğini ve diğer ayrıntıları da değerlendirmesidir.

#### <a name="threats-in-urls"></a>URL'lerde tehdit

Artık e-posta açılır Ayrıntıları sekmesinde bir URL için belirli tehdide **bakabilirsiniz** . Tehdit kötü amaçlı yazılım, *kimlik* *avı*, *istenmeyen posta veya* yok *olabilir*.)

> [!div class="mx-imgBorder"]
> ![URL'nin tehditleri.](../../media/URL_Threats.png)

### <a name="updated-timeline-view-upcoming"></a>Güncelleştirilmiş zaman çizelgesi görünümü (yaklaşan)

> [!div class="mx-imgBorder"]
> ![Güncelleştirilmiş Zaman Çizelgesi Görünümü.](../../media/Email_Timeline.png)

Zaman Çizelgesi görünümü, tüm teslim ve teslim sonrası olaylarını tanımlar. Bu olayların bir alt kümesi için, o noktada tanımlanan tehdit hakkında bilgi içerir. Zaman Çizelgesi görünümü, söz konusu eylemin sonucuyla birlikte 4 ek eylem (ZAP veya el ile düzeltme gibi) hakkında da bilgi sağlar. Zaman çizelgesi görünümü bilgileri şunları içerir:

- **Kaynak:** Olayın kaynağı. Yönetici/sistem/kullanıcı olabilir.
- **Olay:** Özgün teslim, el ile düzeltme, ZAP, gönderiler ve dinamik teslim gibi en üst düzey olayları içerir.
- **Eylem:** ZAP veya yönetici eyleminin parçası olarak alınan belirli eylem (örneğin, yumuşak silme).
- **Tehdit:** Bu noktada tanımlanan tehditleri (kötü amaçlı yazılım, kimlik avı, istenmeyen posta) kapsar.
- **Sonuç/Ayrıntılar:** Eylemin sonucu hakkında, ZAP/yönetici eyleminin parçası olarak gerçekleştirip gerçekleştiri olmadığı gibi daha fazla bilgi.

### <a name="original-and-latest-delivery-location"></a>Özgün ve en son teslim konumu

Şu anda, teslim konumunu e-posta kılavuzunda ve e-posta uç yüzeyi üzerinde ortaya çıkaralım. Teslim **konumu alanı** Orijinal teslim konumu **_ _olarak yeniden_ *adlandırıldı. Bir de _En son teslim konumu olan başka bir* _alan daha karşınızda._**

**Özgün teslim konumu,** başlangıçta bir e-postanın teslim yeri hakkında daha fazla bilgi verecek. **En son teslim konumu,** ZAP veya Silinmiş öğelere taşı gibi yönetici *eylemleri gibi sistem* eylemlerinin ardından e-postanın *nereye inmiş olduğunu gösterir*. En son teslim konumu, yöneticilere iletinin son bilinen konumunu teslim sonrası veya sistem/yönetici eylemlerini söylemeyi amaçlar. E-postada son kullanıcı eylemleri dahil değildir. Örneğin, kullanıcı bir iletiyi sildi veya iletiyi arşive/pst'ye taşıdı ise, iletinin "teslim" konumu güncelleştirilmez. Ancak bir sistem eylemi konumu güncellerse (örneğin, ZAP e-postanın karantinaya alınmasını sağlarsa), En **son** teslim konumu "karantina" olarak gösterilebilir.

> [!div class="mx-imgBorder"]
> ![Güncelleştirilmiş teslim konumları.](../../media/Updated_Delivery_Location.png)

> [!NOTE]
> Teslim konumu ve Teslim **eyleminin** "bilinmiyor" **olarak** gösteril olabilir birkaç durumda:
>
> - İleti teslim edildi **ise** Teslim konumunu "teslim edildi"  ve Teslim konumu olarak "bilinmiyor" olarak görebilirsiniz, ancak gelen kutusu kuralı iletiyi Gelen Kutusu veya Gereksiz E-posta klasörüne değil varsayılan bir klasöre (Taslak veya Arşiv gibi) taşıdı.
>
> - **En son teslim** konumu, bir yönetici/sistem eylemi (ZAP gibi) denenip denenmese de bilinmeyen bir ileti bulunamıyor. Normalde, eylem, kullanıcı iletiyi taşıdıktan veya sildikten sonra gerçekleşir. Böyle durumlarda, zaman çizelgesi **görünümünde Sonuç/Ayrıntılar** sütununu doğrulayın. "İleti kullanıcı tarafından taşındı veya silindi" ifadesinin nasıl silindiğinde bakın.

> [!div class="mx-imgBorder"]
> ![Zaman çizelgesi için teslim konumları.](../../media/Updated_Timeline_Delivery_Location.png)

### <a name="additional-actions"></a>Ek eylemler

*E-postanın* teslimi yapıldıktan sonra ek eylemler uygulanmıştır. Zap *, el* ile *düzeltme (* yazılımdan silme gibi Bir Yönetici tarafından alınan *eylem), dinamik* teslim ve yeniden *işlem (geriye* dönük olarak iyi algılandı bir e-posta için) içerebilir.

> [!NOTE]
> Bekleyen değişikliklerin bir parçası olarak, Şu anda Teslim Eylemi filtresinde ortaya çıkarılan "ZAP ile Kaldırıldı" değeri yok oluyor. Ek eylemler aracılığıyla ZAP denemesi ile tüm e-postaları aramanın bir **yolunuz olur**.

> [!div class="mx-imgBorder"]
> ![Gezgin'de Ek Eylemler.](../../media/Additional_Actions.png)

### <a name="system-overrides"></a>Sistem geçersiz kılar

*Sistem geçersiz kılmaları* , iletinin hedeflenen teslim konumu için özel durumlar uygulamanızı sağlar. Filtreleme yığını tarafından tanımlanan tehditlere ve diğer algılamalara dayalı olarak sistem tarafından sağlanan teslim konumunu geçersiz kılabilirsiniz. Sistem geçersiz kılmaları, ilkenin önerdiği şekilde iletiyi teslim etmek için kiracı veya kullanıcı ilkesi aracılığıyla ayarlanır. Geçersiz kılmalar, aşırı geniş kapsamlı bir Gönderen ilkesi gibi yapılandırma açıkları nedeniyle kötü amaçlı iletilerin Kasa teslimi tanımlayabilir. Bu geçersiz kılma değerleri şöyle olabilir:

- Kullanıcı ilkesi tarafından izin verildi: Kullanıcı, etki alanlarına veya gönderenlere izin veren ilkeler posta kutusu düzeyinde oluşturur.

- Kullanıcı ilkesi tarafından engellendi: Kullanıcı, etki alanlarını veya gönderenleri engellemek için posta kutusu düzeyinde ilkeler oluşturur.

- Kuruluş ilkesi tarafından izin verildi: Kuruluşun güvenlik ekipleri, kuruluşta kullanıcılara gönderenlere ve etki alanlarına izin vermek için Exchange akışı kuralları (aktarım kuralları olarak da bilinir) ilkeleri veya posta akışı kurallarını (aktarım kuralları olarak da bilinir) sağlar. Bu, bir dizi kullanıcı veya kuruluşun tamamı için olabilir.

- Kuruluş ilkesi tarafından engellendi: Kuruluşun güvenlik ekipleri, kuruluşlarına gelen kullanıcıların gönderenlerini, etki alanlarını, ileti dillerini veya kaynak IP'leri engellemek için ilkeler veya posta akış kuralları sağlar. Bu, bir dizi kullanıcıya veya kuruluşun tamamına uygulanabilir.

- Kuruluş ilkesi tarafından engellenen dosya uzantısı: Kuruluşun güvenlik ekibi, kötü amaçlı yazılımdan koruma ilkesi ayarları aracılığıyla bir dosya adı uzantısını engeller. Araştırmalarda yardımcı olması için artık bu değerler e-posta ayrıntılarında görüntülenir. Ayrıca, ekipler engellenen dosya uzantılarını filtrelemek için zengin filtreleme özelliğini de kullanabilir.

[![Explorer'da Sistem Geçersiz Kılmaları.](../../media/System_Overrides.png)](../../media/System_Overrides.png#lightbox)

> [!div class="mx-imgBorder"]
> ![Sistem Explorer'da Kılavuzu Geçersiz Kılar.](../../media/System_Overrides_Grid.png)

### <a name="improvements-for-the-url-and-clicks-experience"></a>URL ve tıklama deneyimi için iyileştirmeler

Geliştirmeler şunlardır:

- URL uç öğesinin Tıklamalar bölümünde tam tıklı URL'yi (URL'nin parçası olan sorgu **parametreleri de dahil** ) gösterebilirsiniz. Şu anda, başlık çubuğunda URL etki alanı ve yol görünür. Bu bilgileri, tam URL'yi gösterecek şekilde genişlettiriz.

- URL filtreleri genelinde düzeltmeler (*URL* ile *URL* etki alanı *karşılaştırması URL* etki alanı ve yolu): Güncelleştirmeler, URL/tıklama kararını içeren iletileri aramayı etkiler. Protokol-tanılama aramaları desteğini etkinleştirdikten sonra, url'yi kullanmak yerine URL'de aramanızı sağladık `http`. Varsayılan olarak, açıkça başka bir değer belirtilmedi sürece, URL arama http ile eşler. Örneğin:
  - URL, **URL** Etki Alanı `http://` ve **URL** Etki Alanı ve Yol filtresi alanlarında ön eki **olan ve** olmayan alanları arayın. Aramalarda aynı sonuçlar göster gerekir.
  - URL'de öneki `https://` **arayın**. Hiçbir değer belirtilmezse, önek `http://` varsayılır.
  - `/`URL yolu, **URL** Etki Alanı, URL etki **alanı ve yol** alanlarının başında **ve sonunda yoksayılır**. `/`**yok** sayılır.

### <a name="phish-confidence-level"></a>Kimlik avı güven düzeyi

Kimlik avı güven düzeyi, hangi e-postanın "kimlik avı" olarak kategorilere ayrılmış olduğunu güvenlik derecesini belirlemeye yardımcı olur. İki olası değer Yüksek *ve* *Normal değerleridir*. İlk aşamalarda, bu filtre yalnızca Tehdit Gezgini'nin Kimlik Avı görünümünde kullanılabilir.

[![Explorer'da Kimlik Avı Güven Düzeyi.](../../media/Phish_Confidence_Level.png)](../../media/Phish_Confidence_Level.png#lightbox)

### <a name="zap-url-signal"></a>ZAP URL sinyali

ZAP URL sinyali normalde e-postanın Kimlik Avı olarak tanımlandıktan ve teslimden sonra kaldırıldığı ZAP Kimlik Avı uyarı senaryoları için kullanılır. Bu sinyal uyarıyı Gezgin'de ilgili sonuçlara bağlar. Bu, uyarının IOC'lerinden biridir.

Arama sürecini iyileştirmek için Tehdit Gezgini'ni ve Gerçek zamanlı algılamaları, arama deneyiminin daha tutarlı olması için güncelleştirildi. Değişiklikler burada ana hatlarıyla açıklandı:

- [Saat dilimi geliştirmeleri](#timezone-improvements)
- [Yenileme işlemiyle güncelleştirme](#update-in-the-refresh-process)
- [Filtrelere eklemek için grafik detaya gitme](#chart-drilldown-to-add-to-filters)
- [Ürün bilgisi güncelleştirmeleri içinde](#in-product-information-updates)

### <a name="filter-by-user-tags"></a>Kullanıcı etiketlerine göre filtre uygulama

Artık tehdit kapsamını hızlıca kavramak için sistem veya özel kullanıcı etiketlerini sıra olabilir ve filtresini kullanabilirsiniz. Daha fazla bilgi edinmek için bkz. [Kullanıcı etiketleri](user-tags.md).

> [!IMPORTANT]
> Kullanıcı etiketlerine göre filtreleme ve sıralama şu anda genel önizlemede. Bu işlev ticari olarak piyasaya sürmeden önce önemli ölçüde değiştirilmiş olabilir. Microsoft, bu konuda sağlanan bilgilerle ilgili olarak açık veya zımni hiçbir garanti vermez.

> [!div class="mx-imgBorder"]
> ![Gezgin'de Etiketler sütunu.](../../media/threat-explorer-tags.png)

### <a name="timezone-improvements"></a>Saat dilimi geliştirmeleri

Hem Portal'da e-posta kayıtlarının saat dilimini hem de Dışarı Aktarıldı verilerini bulabilirsiniz. E-posta Kılavuzu, Ayrıntılar ayrıntıları, E-posta Zaman Çizelgesi ve Benzer E-postalar gibi deneyimlerde görülebilir, dolayısıyla sonuç kümesi için saat dilimi temiz olur.

> [!div class="mx-imgBorder"]
> ![Saat dilimini Gezgin'de görüntüleme.](../../media/TimezoneImprovements.png)

### <a name="update-in-the-refresh-process"></a>Yenileme işlemiyle güncelleştirme

Bazı kullanıcılar otomatik yenileme (örneğin, tarihi değiştirir değiştirmez) ve elle yenileme (diğer filtreler için) konusunda karışıklığa yorumda bulundular. Benzer şekilde, filtrelerin kaldırılması da otomatik yenilemeye neden olur. Sorguyu değiştirirken filtrelerin değiştirilmesi tutarsız arama deneyimlere neden olabilir. Bu sorunları çözmek için el ile filtreleme mekanizmasına gidiyoruz.

Kullanıcılar farklı filtre aralıklarını (filtre kümesinden ve tarihten) uygulayabilir ve kaldırabilir; sorguyu tanımladikten sonra sonuçları filtrelemek için yenile düğmesini seçer. Yenile düğmesi artık ekranda da vurgulandır. Ayrıca ilgili araç ipucu ve ürünle ilgili belgeleri de güncelleydık.

> [!div class="mx-imgBorder"]
> ![Sonuçları filtrelemek için Yenile'yi seçin.](../../media/ManualRefresh.png)

### <a name="chart-drilldown-to-add-to-filters"></a>Filtrelere eklemek için grafik detaya gitme

Artık filtre olarak eklemek için gösterge değerlerinin grafiğini grafik olarak ekleyebilirsiniz. Sonuçları **filtrelemek** için Yenile düğmesini seçin.

> [!div class="mx-imgBorder"]
> ![Filtrelemek istediğiniz grafiklerde detaya gitme.](../../media/ChartDrilldown.png)

### <a name="in-product-information-updates"></a>Ürün bilgileri güncelleştirmeleri

Artık ürün içinde, kılavuzdaki toplam arama sonucu sayısı gibi ek ayrıntılara bakın (aşağıya bakın). Filtreler, arama deneyimi ve sonuç kümesi hakkında daha fazla bilgi sağlayan etiketler, hata iletileri ve araç ipucu geliştirildi.

> [!div class="mx-imgBorder"]
> ![Ürün için bilgileri görüntüleme.](../../media/ProductInfo.png)

## <a name="extended-capabilities-in-threat-explorer"></a>Threat Explorer'daki genişletilmiş özellikler

### <a name="top-targeted-users"></a>En çok hedefli kullanıcılar

Bugün, Üst Kötü Amaçlı Yazılım Aileleri bölümünde, e-postalar için Kötü Amaçlı Yazılım görünümünde en çok hedefli **kullanıcıların listesini sağlıyoruz** . Bu görünümü Kimlik Avı ve Tüm E-posta görünümlerine de genişlettiriz. en çok hedefli beş kullanıcıyla birlikte, buna karşılık gelen görünümde her kullanıcı için deneme sayısını da görüntüebilirsiniz. Örneğin, Kimlik Avı görünümü için Kimlik avı girişimlerinin sayısını görüyorsunuz.

Her e-posta görünümü için çevrimdışı çözümleme deneme sayısıyla birlikte 3.000'e kadar olan hedefli kullanıcıların listesini dışarı aktarabilirsiniz. Buna ek olarak, deneme sayısını seçmek (örneğin, aşağıdaki resimde 13 girişim) Tehdit Gezgini'nde filtrelenmiş bir görünüm açar, böylece bu kullanıcıya yönelik e-postalar ve tehditlere ilişkin daha fazla ayrıntı görebilirsiniz.

> [!div class="mx-imgBorder"]
> ![En çok hedefli kullanıcılar.](../../media/Top_Targeted_Users.png)

### <a name="exchange-transport-rules"></a>Exchange aktarım kurallarını taşıma

Veri zenginleştirmenin bir parçası olarak, iletiye uygulanmış olan tüm farklı aktarım Exchange aktarım kurallarını (ETR) görebilirler. Bu bilgiler E-posta kılavuz görünümünde kullanılabilir. Bunu görüntülemek için kılavuzdaki **Sütun seçenekleri'ne** ve sonra Sütun **seçeneklerinden Exchange Aktarım** Kuralı Ekle'ye tıklayın. E-postanın **Ayrıntılar** uç bölmesinde de görünür.

İletiye uygulanmış olan aktarım kurallarının hem GUID'lerini hem de adını alabilirsiniz. Aktarım kuralının adını kullanarak iletileri arayabilirsiniz. Bu bir "Içerir" aramasıdır ve bu da kısmi aramalar da yapldır.

> [!IMPORTANT]
> ETR araması ve adı kullanılabilirliği, size atanan role bağlıdır. ETR adlarını ve aramalarını görüntülemek için aşağıdaki rollerden/izinlerden biri gerekir. Bu rollerden herhangi biri size atanmamışsa aktarım kurallarının adlarını göremz veya ETR adlarını kullanarak iletileri arayabilirsiniz. Bununla birlikte, E-posta Ayrıntıları'nın altında ETR etiketi ve GUID bilgilerini de görebilirsiniz. E-posta Kılavuzlarında, E-posta uç uçları, Filtreler ve Dışarı Aktarma'daki diğer kayıt görüntüleme deneyimleri etkilenmez.
>
> - Yalnızca EXO - Veri Kaybını Önleme: All
> - Yalnızca EXO - O365SupportViewConfig: All
> - Microsoft Azure Active Directory veya EXO - Güvenlik Yöneticisi: All
> - AAD veya EXO - Security Reader: All
> - Yalnızca EXO - Aktarım Kuralları: All
> - Yalnızca EXO - View-Only Yapılandırması: All
>
> E-posta kılavuzu, Ayrıntılar uçarak çıkış ve Dışarı Aktarıldı CSV içinde ETR'ler aşağıda gösterildiği gibi Ad/GUID ile gösterilir.
>
> > [!div class="mx-imgBorder"]
> > ![Exchange Aktarım Kuralları.](../../media/ETR_Details.png)

### <a name="inbound-connectors"></a>Gelen bağlayıcıları

Bağlayıcılar, e-postanın e-postanız e-postanıza veya Microsoft 365 veya bir Office 365 koleksiyonudur. Bunlar, herhangi bir güvenlik kısıtlaması veya denetimi uygulamana olanak sağlar. Threat Explorer'ın içinde artık bir e-postayla ilgili bağlayıcıları ekleyebilirsiniz ve bağlayıcı adlarını kullanarak e-postaları arayabilirsiniz.

Bağlayıcı araması doğada "içerir"; bu da kısmi anahtar sözcük aramaların da çalışması gerektiği anlamına gelir. Ana kılavuz görünümü, Ayrıntılar dışarı aktarma aracı ve Dışarı Aktarıldı CSV içinde, bağlayıcılar burada gösterildiği gibi Ad/GUID biçiminde gösterilir:

> [!div class="mx-imgBorder"]
> ![Bağlayıcı ayrıntıları.](../../media/Connector_Details.png)

## <a name="new-features-in-threat-explorer-and-real-time-detections"></a>Threat Explorer ve Gerçek zamanlı algılamalarda yeni özellikler

- [Kimliğine bürünülen kullanıcılara ve etki alanlarına gönderilen kimlik avı e-postalarını görüntüleme](#view-phishing-emails-sent-to-impersonated-users-and-domains)
- [E-posta üst bilgilerini önizleme ve e-posta gövdesini indirme](#preview-email-header-and-download-email-body)
- [E-posta zaman çizelgesi](#email-timeline)
- [URL'yi dışarı aktar tıkla veri](#export-url-click-data)

### <a name="view-phishing-emails-sent-to-impersonated-users-and-domains"></a>Kimliğine bürünülen kullanıcılara ve etki alanlarına gönderilen kimlik avı e-postalarını görüntüleme

Kimliğine bürünülen kullanıcılara ve etki alanlarına yönelik kimlik avı girişimlerini tanımlamak için, korunması gereken Kullanıcılar *listesine eklenmiştir*. Etki alanları için yöneticilerin Kuruluş etki alanlarını *etkinleştirmesi veya* korumak için Etki Alanları'ne bir etki *alanı adı eklemesi gerekir*. Korunmaya yönelik etki alanları Kimliğe *Bürünme bölümündeki Kimlik Avını* Önleme *ilkesi sayfasında* bulunur.

Kimlik avı iletilerini gözden geçirmek ve kimliğine bürünülen kullanıcıları veya etki alanlarını aramak için, [E-posta > Explorer'ın Kimlik Avı](threat-explorer-views.md) görünümünü kullanın.

Bu örnekte Threat Explorer 2013 2013 2013'

1. Güvenlik ve [Uyumluluk & 'nde](https://protection.office.com) (https://protection.office.com)Gezgin için Tehdit yönetimi > (veya Gerçek zamanlı algılamalar) seçin.

2. Görünüm menüsünde, Kimlik Avını E-posta ile > seçin.

   Burada kimliğine **bürünülen etki alanını veya kimliğine** **bürünülen kullanıcıyı seçebilirsiniz**.

3. **YA** DA **Kimliğe Bürünülen** etki alanı'ı seçin ve metin kutusuna korumalı bir etki alanı yazın.

   Örneğin, *contoso*, contoso veya contoso.com gibi korumalı *contoso.com.au**.*

4. Kimliğine Bürünülen Etki Alanı / Algılanan konum gibi ek kimliğe bürünme bilgilerini görmek için E-posta sekmesinin > altında herhangi bir iletinin Konusu'na tıklayın.

    **VEYA**

    **Kimliğine bürünülen** kullanıcı'ya tıklayın ve metin kutusuna korumalı bir kullanıcının e-posta adresini yazın.

    > [!TIP]
    > **En iyi sonuçları elde** etmek için, *korumalı kullanıcılarda arama yapmak üzere* tam e-posta adreslerini kullanın. Örneğin, kullanıcı kimliğe bürünme araştırmalarını araştırırken korumalı kullanıcınızı *daha hızlı firstname.lastname@contoso.com* daha başarılı bir şekilde bulabilirsiniz. Korumalı bir etki alanını ararken, arama kök etki alanını (örneğin, contoso.com) ve etki alanı adını (*contoso) alır*. Kök etki alanı *kimliği contoso.com hem* kullanıcı kimliğine bürünmelerini *contoso.com* contoso etki alanı adını *alır*.

5. Kullanıcı veya **etki** alanı hakkında ek  >  kimliğe bürünme bilgilerini ve Algılandı konumunu görmek için E-posta sekmesiAyrındırmalar sekmesi altında herhangi bir *iletinin Konusu öğesini seçin*.

    :::image type="content" source="../../media/threat-ex-views-impersonated-user-image.png" alt-text="Algılama konumunu ve algılanan tehdidi (burada kullanıcının kimlik avı kimliğine bürünme) gösteren korumalı bir kullanıcı için Tehdit Gezgini ayrıntıları bölmesi.":::

> [!NOTE]
> 3. veya 5. adımda, sırasıyla Algılama Teknolojisi'ne ve Kimliğe Bürünme etki  alanı veya Kimliğe Bürünme kullanıcısı'ı seçerseniz,  > *E-posta*  **sekmesiAyrındırma** Bilgileri sekmesinde kullanıcı veya  etki alanıyla ilgili bilgiler ve Algılandı konumu yalnızca Kimlik Avı Önleme ilkesi sayfasında listelenen kullanıcı veya etki alanıyla ilgili iletilerde gösterilir.

### <a name="preview-email-header-and-download-email-body"></a>E-posta üst bilgilerini önizleme ve e-posta gövdesini indirme

Artık, Threat Explorer'da bir e-posta üst bilgisini önizleyin ve e-posta gövdesini indirin. Yöneticiler indirilen üst bilgileri/e-posta iletilerini tehditlere karşı çözümde bulundurabilirsiniz. E-posta iletilerini indirmek bilgilerin maruz kalma riski olduğundan, bu işlem rol tabanlı erişim denetimi (RBAC) tarafından denetlenmektedir. Tüm e-posta *iletileri* görünümünde posta indirme olanağı vermek için yeni bir önizleme rolü gereklidir. Bununla birlikte, e-posta üst bilgisini görüntülemek için ek rol gerekmez (iletileri Threat Explorer'da görüntülemek için gerekenler dışında). Önizleme rolüyle yeni bir rol grubu oluşturmak için:

1. Veri Yöneticiniz veya eBulma Yöneticisi gibi, yalnızca Önizleme rolüne sahip olan yerleşik bir rol grubu seçin.
2. Rol **grubunu kopyala'ya seçin**.
3. Yeni rol grubunuz için bir ad ve açıklama seçin ve sonra da Sonraki'yi **seçin**.
4. Rolleri gerekli olduğu gibi ekp kaldırarak değiştirebilir, ancak Preview rolüne son ve ardından bırakarak rolleri değiştirebilirsiniz.
5. Üye ekleyin ve ardından Rol grubu **oluştur'a tıklayın**.

Gezgin ve Gerçek zamanlı algılamalar, e-posta iletilerinizin nereye gittiğinin daha eksiksiz bir resmini sağlayan yeni alanlar da alır. Bu değişiklikler, Güvenlik İşlemleri için avı kolaylaştırır. Ancak asıl sonuç, soruna neden olan e-posta iletilerinin konumunu bir bakışta bilmektir.

Bu nasıl yapılır? Teslim durumu şimdi iki sütuna ayrıldı:

- **Teslim eylemi** - E-postanın durumu.
- **Teslim konumu** - E-postanın yönlendirildi olduğu yer.

*Teslim eylemi* , var olan ilkeler veya algılamalar nedeniyle e-posta üzerinde ilen eylemdir. E-posta için olası eylemler şu şekildedir:

|Teslim edildi|Gereksiz|Engellendi|Değiştirildi|
|---|---|---|---|
|E-posta kullanıcının gelen kutusu veya klasörüne teslim edildi ve kullanıcı buna erişebilirsiniz.|E-posta kullanıcının Gereksiz veya Silinmiş klasörüne gönderilmiştir ve kullanıcı buna erişim iznine sahip olabilir.|Karantinaya alınan, başarısız olan veya bırakılan e-postalar. Bu postalara kullanıcı erişemez.|E-postada, ekin kötü amaçlı olduğunu .txt dosyalarla değiştirilmiş kötü amaçlı ekler vardı.|

Kullanıcı şunları görebilir ve göremz:

|Son kullanıcılar için erişilebilir|Son kullanıcılar için erişilemez|
|---|---|
|Teslim edildi|Engellendi|
|Gereksiz|Değiştirildi|

**Teslim konumu** , teslim sonrası çalıştırmayı gösteren ilke ve algılamaların sonuçlarını gösterir. Teslim **_eylemiyle bağlantılıdır_**. Olası değerler bunlardır:

- *Gelen kutusu veya* klasör: E-posta gelen kutusunda veya klasördedir (e-posta kurallarınıza göre).
- *Şirket içi veya dış*: Posta kutusu bulutta yoktur ama şirket içindedir.
- *Gereksiz klasörü*: E-posta, kullanıcının Gereksiz E-posta klasöründedir.
- *Silinmiş öğeler klasörü*: Kullanıcının Silinmiş öğeler klasöründeki e-posta.
- *Karantina*: E-posta, kullanıcının posta kutusunda değil karantinada.
- *Başarısız*: E-posta posta posta kutusuna ulaşamadı.
- *Atildi*: E-posta, posta akışında bir yerde kayboldu.

### <a name="email-timeline"></a>E-posta zaman çizelgesi

**E-posta** zaman çizelgesi, yöneticiler için arama deneyimini geliştiren yeni bir Explorer özelliğidir. Bu, etkinliği anlamak için farklı konumları kontrol etmek için harcanan zamanı keser. Bir e-posta geldiğinde veya ona yakın bir zamanda birden çok olay olduğunda, bu olaylar bir zaman çizelgesi görünümünde görüntülenir. Teslim sonrası e-postanıza gelen bazı olaylar Özel eylem **sütununda yakalanır** . Yöneticiler, ilkelerinin nasıl bulunduğu, postanın son olarak nereye yönlendirildikleri ve bazı durumlarda son değerlendirmenin ne olduğuyla ilgili bilgi almak için, zaman çizelgesinde yer alan bilgileri posta teslimi sırasında  alınan özel eylemle bir araya getirdiler.

Daha fazla bilgi için bkz[. Dosyada teslim edilen kötü amaçlı e-postaları araştırma Office 365](investigate-malicious-email-that-was-delivered.md).

### <a name="export-url-click-data"></a>URL'yi dışarı aktar tıkla veri

Artık, ağ ileti kimliğini görüntülemek ve karart Microsoft Excel için URL tıklamaları için  raporları dışarı aktarabilirsiniz **. Bu**, URL tıklatma trafiğinin nereden geldiğini açıklamaya yardımcı olur. şöyle çalışır: Tehdit Yönetimi'nin hızlı başlatma Office 365 zincirini izleyin:

**Explorer** \> **Kimlik Avını Görüntüle** \> **Tıklamalar** \> **Üst URL'ler** **veya URL'ler** \> En Çok Tıklamalar URL açılır öğesini açmak için herhangi bir kaydı seçin.

Listeden bir URL'yi seçin, dışarı uçan panelde **yeni bir** Dışarı Aktar düğmesi gösterilir. Daha kolay raporlama için bu düğmeyi kullanarak verileri Excel tablolara aktarabilirsiniz.

Gerçek zamanlı algılamalar raporunda aynı konuma almak için bu yolu izleyin:

**Explorer** \> **Gerçek zamanlı algılamalar** \> **Kimlik Avını Görüntüle** \> **URL'ler** \> **En Büyük URL'ler** **veya** \> En Çok Tıklamalar URL açılır öğesini açmak için herhangi bir kaydı seçin, \> **Tıklamalar sekmesine** gidin.

> [!TIP]
> Ağ İleti kimliği, Gezgin veya ilişkili üçüncü taraf araçları aracılığıyla kimlik araması yapmak için tıklayma haritasını belirli postalara eşler. Bu tür aramalar, bir tıklama sonucuyla ilişkilendirilmiş olan e-postayı tanımlamaktadır. Birbiriyle ilişkili Ağ İleti kimliğinin olması daha hızlı ve daha güçlü bir çözümleme sağlar.

> [!div class="mx-imgBorder"]
> ![Gezgin'de Tıklatmalar sekmesi.](../../media/tp_ExportClickResultAndNetworkID.png)

## <a name="see-malware-detected-in-email-by-technology"></a>E-postada teknolojiye göre algılanan kötü amaçlı yazılımları görme

Kötü amaçlı yazılımların e-postada bu teknolojiye göre sıralanmış olarak algılanmış olduğunu Microsoft 365 varsayalım. Bunu yapmak için, Gezgin'in [Kötü amaçlı >-posta](threat-explorer-views.md#email--malware) E-postaSı görünümünü (veya Gerçek zamanlı algılamaları) kullanın.

1. Güvenlik ve Uyumluluk & ()<https://protection.office.com> içinde Tehdit yönetimi **Gezgini'ni** \> **(veya** **Gerçek zamanlı algılamalar) seçin**. (Bu örnekte Explorer 2010 2013 2013 201

2. Görünüm menüsünde, **Kötü Amaçlı** E-posta'ya **E-posta Gönder'i** \> **seçin**.

   > [!div class="mx-imgBorder"]
   > ![Gezgin için Görünüm menüsü.](../../media/ExplorerViewEmailMalwareMenu.png)

3. **Gönderen'e** tıklayın ve Temel Algılama **teknolojisi'ne** \> **tıklayın**.

   Algılama teknolojileriniz artık rapor için filtre olarak kullanılabilir.

   > [!div class="mx-imgBorder"]
   > ![Kötü amaçlı yazılım algılama teknolojileri.](../../media/ExplorerEmailMalwareDetectionTech.png)

4. Bir seçenek belirleyin. Ardından, **filtreyi uygulamak** için Yenile düğmesini seçin.

   > [!div class="mx-imgBorder"]
   > ![Seçili algılama teknolojisi.](../../media/ExplorerEmailMalwareDetectionTechATP.png)

Rapor, seçtiğiniz teknoloji seçeneği kullanılarak, kötü amaçlı yazılımın e-postada algıladık sonuçları gösterecek şekilde yenilenir. Buradan daha fazla analiz yürütesiniz.

## <a name="view-phishing-url-and-click-verdict-data"></a>Kimlik avı URL'sini görüntüleme ve karar verilerine tıklama

İzin verilen, engellenmiş ve geçersiz kılınmış URL'lerin listesi de içinde olmak üzere, e-posta url'leri aracılığıyla kimlik avı girişimlerini görmek istediğiniz varsayalım. Tıkılan URL'leri tanımlamak için, [Kasa yapılandırılması](safe-links.md) gerekir. Yeni Bağlantılar'ın [tıklama Kasa](set-up-safe-links-policies.md) ve tıklama kararlarının günlüğü tutma için Bağlantılar ilkelerini ayarlamayı Kasa.

İletilerde kimlik avı URL'lerini gözden geçirmek ve kimlik avı iletilerinden URL'lere tıklamak için, Gezgin'in [E-postaYdanSif  > ](threat-explorer-views.md#email--phish) görünümünü veya Gerçek zamanlı algılamaları kullanın.

1. Güvenlik ve Uyumluluk & ()<https://protection.office.com> içinde Tehdit yönetimi **Gezgini'ni** \> **(veya** **Gerçek zamanlı algılamalar) seçin**. (Bu örnekte Explorer 2010 2013 2013 201

2. Görünüm menüsünde **E-posta** **Kimlik Avını** \> **seçin**.

   > [!div class="mx-imgBorder"]
   > ![Kimlik avı bağlamında Gezgin için Görünüm menüsü.](../../media/ExplorerViewEmailPhishMenu.png)

3. **Gönderen'e** tıklayın ve karara tıklayın **URL'leri** \> **seçin**.

4. Engellenmiş ve Geçersiz kılınan engelleme gibi bir veya daha fazla seçeneği belirleyin ve sonra filtreyi uygulamak için  seçeneklerle aynı satırda Yenile düğmesini seçin. (Tarayıcı pencerenizi yenilemeyin.)

   > [!div class="mx-imgBorder"]
   > ![URL'ler ve kararlara tıklayın.](../../media/ThreatExplorerEmailPhishClickVerdictOptions.png)

   Rapor, raporun altındaki URL sekmesinde iki farklı URL tablosu gösterecek şekilde yenilenir:

   - **En üst URL'ler** , filtreleyilen iletilerde yer alan URL'ler ve her URL için e-posta teslim eylemi sayılarıdır. Kimlik avı e-posta görünümünde, bu liste normalde geçerli URL'leri içerir. Saldırganlar, iletilerinde iyi ve kötü URL'lerin bir karışımını bulundurarak bunların teslim  kurtarmaya çalışsa da kötü amaçlı bağlantıların daha ilginç bir görünüme sahip olduğunu fark ediyor. URL'ler tablosu toplam e-posta sayısına göre sıralanmış, ancak görünümü basitleştirmek için bu sütun gizlenir.

   - **En çok** tıklamalar, Kasa tıklama sayısına göre sıralanmış, Bağlantıların kaydırılmış URL'leridir. Görünümü basitleştirmek için bu sütun da görüntülenmez. Sütuna göre toplam sayı sayısı, tık Kasa URL için karara tıklama sayısını gösterir. Kimlik avı e-posta görünümünde, bunlar çoğunlukla şüpheli veya kötü amaçlı URL'lerdir. Ancak görünüm, tehdit olmayan ancak kimlik avı iletisinde yer alan URL'leri içerebilir. Kaydırılmış bağlantılarda URL tıklamaları burada göster şey değil.

   İki URL tablosu kimlik avı e-posta iletisinde teslim eylemine ve konuma göre en önemli URL'leri gösterir. Tablolarda, bir uyarıya rağmen engellenen veya ziyaret edilen URL tıklamaları gösterir; böylelikle kullanıcılara hangi olası hatalı bağlantıların sunlarak ve kullanıcıya tık yaptığını görmenizi sağlar. Buradan daha fazla analiz yürütesiniz. Örneğin, grafiğin altında, kuruluşun ortamında engellenmiş e-posta iletilerinde en üst URL'leri görebilirsiniz.

   > [!div class="mx-imgBorder"]
   > ![Engellenmiş olan Gezgin URL'leri.](../../media/ExplorerPhishClickVerdictURLs.png)

   Daha ayrıntılı bilgi görüntülemek için bir URL seçin.

   > [!NOTE]
   > URL uçarak çıkış iletişim kutusunda, e-posta iletilerine filtre uygulama, URL'nin ortamınıza maruz kalma sürenizin tam görünümünü göstermek için kaldırılır. Bu, Gezgin'de kaygı ayarlarınız olan e-posta iletilerine filtre uygulamanıza, olası tehditlere neden olan belirli URL'leri bulmanızı ve ardından Gezgin görünümünün kendisine URL filtreleri eklemek zorunda kalmadan ortamınıza URL'nin açık kalma süresini anlamanızı (URL ayrıntıları iletişim kutusu yoluyla) anlamanızı sağlar.

### <a name="interpretation-of-click-verdicts"></a>Tıklama kararlarının yorumlanması

E-posta veya URL çıkışları, Üst Tıklamalar ve filtreleme deneyimlerimiz içinde farklı tıklama karar değerleri görüyorsunuz:

- **Yok:** URL için karar yakalanamıyor. Kullanıcı URL'ye tıklamış olabilir.
- **İzin verildi:** Kullanıcının URL'ye girmesine izin verili.
- **Engellendi:** Kullanıcının URL'ye gezinmesi engellendi.
- **Bekleyen karar:** Kullanıcıya detonation-pending sayfası sunuldu.
- **Geçersiz kılınan engelleme:** Kullanıcının doğrudan URL'ye gezinmesi engellendi. Ancak kullanıcı URL'ye gitmek için bloğun üzerine atlar.
- **Bekleyen beklemede olan beklemede atlandı:** Kullanıcıya detonation sayfası sunuldu. Ancak kullanıcı URL'ye erişmek için iletinin üzerine atlar.
- **Hata:** Kullanıcıya hata sayfası sunuldu veya karara karar verirken bir hata oluştu.
- **Hata:** Karar yakalama sırasında bilinmeyen bir özel durum oluştu. Kullanıcı URL'ye tıklamış olabilir.

## <a name="review-email-messages-reported-by-users"></a>Kullanıcılar tarafından bildirilen e-posta iletilerini gözden geçirme

Rapor İletisi eklentisinde veya  Rapor Kimlik Avı eklentisinde *, kuruluşta* *gereksiz, Gereksiz* Değil veya Kimlik Avı olarak bildirilen [e-posta](enable-the-report-message-add-in.md) iletilerini görmek istediğiniz [varsayalım](enable-the-report-phish-add-in.md). Bunları görmek için, [**Explorer'ın** **EmailSubmissions** > ](threat-explorer-views.md#email--submissions) görünümünü kullanın (veya Gerçek zamanlı algılamalar).

1. Güvenlik ve Uyumluluk & ()<https://protection.office.com> içinde Tehdit yönetimi **Gezgini'ni** \> **(veya** **Gerçek zamanlı algılamalar) seçin**. (Bu örnekte Explorer 2010 2013 2013 201

2. Görünüm menüsünde **E-posta** **Gönderimleri'ne** \> **tıklayın**.

   > [!div class="mx-imgBorder"]
   > ![E-postalar için Explorer'ın Görünüm menüsü.](../../media/explorer-view-menu-email-user-reported.png)

3. **Gönderen'e** tıklayın ve Temel Rapor **türü'ne** \> **tıklayın**.

4. Kimlik Avı gibi bir **seçenek belirtin** ve sonra Yenile **düğmesini** seçin.

   > [!div class="mx-imgBorder"]
   > ![Kullanıcı tarafından bildirilen kimlik avı.](../../media/EmailUserReportedReportType.png)

Rapor, kuruluşta yer alan kişilerin kimlik avı girişimi olarak bildirilen e-posta iletileriyle ilgili verileri gösterecek şekilde yenilenir. Daha fazla çözümleme yapmak için bu bilgileri kullanabilir ve gerekirse Microsoft Defender'da kimlik avıyla mücadele ilkelerinizi daha [iyi Office 365](configure-mdo-anti-phishing-policies.md).

## <a name="start-automated-investigation-and-response"></a>Otomatik araştırma ve yanıt başlatma

> [!NOTE]
> Plan 2 ve 2'nin son güncelleştirmeleri için *Microsoft Defender'Office 365 otomatik soruşturma* ve *Office 365 E5*.

[Otomatik araştırma ve yanıt,](automated-investigation-response-office.md) güvenlik işlemleri ekip sürenizi ve siber saldırıları araştırma ve azaltma için harcanan çabadan tasarruf sağlar. Güvenlik çalışma kitabını tetikleyen uyarılar yapılandırmaya ek olarak, Gezgin'de görünümden otomatik bir araştırma ve yanıt işlemi de başlatabilirsiniz. Ayrıntılar için bkz [. Örnek: Güvenlik yöneticisi Explorer'dan gelen bir soruşturmayı tetikler](automated-investigation-response-office.md#example-a-security-administrator-triggers-an-investigation-from-threat-explorer).

## <a name="more-ways-to-use-explorer-and-real-time-detections"></a>Explorer'ı ve Gerçek zamanlı algılamaları kullanmanın diğer yolları

Bu makalede ana hatlarıyla açıklanan senaryolara ek olarak, Gezgin'de (veya Gerçek zamanlı algılamalar) kullanılabilen çok daha fazla raporlama seçeneği vardır. Aşağıdaki makalelere bakın:

- [Teslim edilen kötü amaçlı e-postaları bulma ve araştırma](investigate-malicious-email-that-was-delivered.md)
- [SharePoint Online, OneDrive ve Microsoft Teams'de algılanan kötü amaçlı dosyaları Microsoft Teams](./mdo-for-spo-odb-and-teams.md)
- [Threat Explorer'daki görünümlere genel bakış (ve Gerçek zamanlı algılamalar)](threat-explorer-views.md)
- [Tehdit koruması durum raporu](view-email-security-reports.md#threat-protection-status-report)
- [Otomatik araştırma ve yanıt Microsoft 365 Defender](../defender/m365d-autoir.md)

## <a name="required-licenses-and-permissions"></a>Gerekli lisanslar ve izinler

Explorer veya [Gerçek zamanlı algılamaları Office 365](defender-for-office-365.md) için Microsoft Defender'a sahipsiniz.

- Explorer, Plan 2 için Defender'Office 365 dahil edilir.
- Gerçek zamanlı algılamalar raporu, Plan 1'den Office 365 Defender'a dahildir.
- Lisans atamayı, lisanslar için Defender ile korunması gereken tüm kullanıcılara Office 365. Gezgin ve Gerçek zamanlı algılamalar lisanslı kullanıcılar için algılama verilerini gösterir.

Gezgin'i veya Gerçek zamanlı algılamaları görüntülemek ve kullanmak için, güvenlik yöneticisine veya güvenlik okuyucuya verilenler gibi uygun izinlere sahip olmak gerekir.

- Güvenlik ve & Merkezi için, aşağıdaki rollerden biri atanmış olmalı:

  - Kuruluş Yönetimi
  - Güvenlik Yöneticisi (bu, Azure Active Directory merkezinden atanabilir)<https://aad.portal.azure.com>
  - Güvenlik Okuyucu

- Daha Exchange Online için, Exchange yönetim merkezinde (EAC) veya Exchange Online [PowerShell'de atanmış Exchange Online gerekir](/powershell/exchange/exchange-online-powershell):

  - Kuruluş Yönetimi
  - View-Only Yönetimi
  - View-Only'i seçin
  - Uyumluluk Yönetimi

Roller ve izinler hakkında daha fazla bilgi edinmek için aşağıdaki kaynaklara bakın:

- [Microsoft 365 Defender portalında izinler](permissions-microsoft-365-security-center.md)
- [Web'de özellik Exchange Online](/exchange/permissions-exo/feature-permissions)

## <a name="differences-between-threat-explorer-and-real-time-detections"></a>Tehdit Gezgini ile Gerçek zamanlı algılamalar arasındaki farklar

- Gerçek *zamanlı algılamalar raporu*, plan 1'den Office 365 Defender'da kullanılabilir. *Threat Explorer*, Plan 2'nin Office 365 Defender'da kullanılabilir.
- Gerçek zamanlı algılamalar raporu, algılamaları gerçek zamanlı olarak görüntülemeye olanak sağlar. Threat Explorer bunu da yapar, ancak belirli bir saldırı için ek ayrıntılar da sağlar.
- Threat *Explorer'da* Tüm e-posta görünümü kullanılabilir, ancak Gerçek zamanlı algılamalar raporunda kullanılamaz.
- Threat Explorer'da daha fazla filtreleme özelliği ve kullanılabilir eylem bulunmaktadır. Daha fazla bilgi için bkz. [Çevrimiçi Hizmet Office 365 için Microsoft Defender: Yeni planlar için Defender'da Office 365 kullanılabilirliği](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description#feature-availability-across-advanced-threat-protection-atp-plans).

## <a name="other-articles"></a>Diğer makaleler

[E-posta Varlık Sayfası içeren e-postaları araştırma](mdo-email-entity-page.md)
