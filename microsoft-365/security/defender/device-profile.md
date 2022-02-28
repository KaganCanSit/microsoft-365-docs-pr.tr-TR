---
title: Microsoft 365 güvenlik portalında cihaz profili
description: Kuruluşta bir cihaz için risk ve pozlama düzeylerini görüntüye açın. Geçmişteki ve mevcut tehditleri analiz edin ve en son güncelleştirmelerle cihazı koruyun.
keywords: güvenlik, kötü amaçlı yazılım, Microsoft 365, M365, Microsoft 365 Defender, güvenlik merkezi, Uç Nokta için Microsoft Defender, Office 365 için Microsoft Defender, Kimlik için Microsoft Defender, cihaz sayfası, cihaz profili, makine sayfası, makine profili
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.localizationpriority: medium
ms.author: v-maave
author: martyav
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
search.appverid: met150
ms.technology: m365d
ms.openlocfilehash: 9838d7f3ffed46c62891822c6e3761e36d49baf5
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62985352"
---
# <a name="device-profile-page"></a>Cihaz profili sayfası

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


Mobil Microsoft 365 portalı size cihaz profili sayfaları sağlar, böylece ağ cihazlarınız için sistem durumunu ve durumunu hızlı bir şekilde değerlendirebilirsiniz.

> [!IMPORTANT]
> Cihazın Uç Nokta için Microsoft Defender'a, Kimlik için Microsoft Defender'a veya her iki uygulamaya da kaydolmanıza bağlı olarak, cihaz profil sayfası biraz farklı görünebilir.

Cihaz Uç Nokta için Microsoft Defender'a kayıtlı ise, bazı yaygın güvenlik görevlerini gerçekleştirmek için cihaz profili sayfasını da kullanabilirsiniz.

## <a name="navigating-the-device-profile-page"></a>Cihaz profili sayfasında gezinme

Profil sayfası çeşitli geniş bölümlere ayrılmıştır.

![(1) Sekme alanı (2) Kenar Çubuğu ve (3) Eylemleri'nin kırmızıyla vurgulu olduğu cihaz profili sayfasının görüntüsü.](../../media/mtp-device-profile/hybrid-device-overall.png)

Kenar çubuğu (1) cihazla ilgili temel ayrıntıları listeler.

Ana içerik alanı (2), cihaz hakkında farklı türde bilgileri görüntülemek için geçiş yapmak istediğiniz sekmeleri içerir.

Cihaz Uç Nokta için Microsoft Defender'a kayıtlı ise, yanıt eylemlerinin listesini de (3) alırsınız. Yanıt eylemleri, güvenlikle ilgili sık kullanılan görevleri gerçekleştirmeniz için olanak sağlar.

## <a name="sidebar"></a>Kenar Çubuğu

Cihaz profil sayfasının ana içerik alanında kenar çubuğu yer almaktadır.

![Cihaz profili için kenar çubuğu sekmesinin resmi.](../../media/mtp-device-profile/azure-atp-only-device-sidebar.png)

Kenar çubuğu cihazın tam adını ve pozlama düzeyini listeler. Ayrıca, küçük alt bölümlerde açık veya kapalı olarak değiştir değiştir işletmek için bazı önemli temel bilgiler sağlar; örneğin:

* **Etiketler** - Uç Nokta için Microsoft Defender, Kimlik için Microsoft Defender veya cihazla ilişkilendirilmiş özel etiketler. Kimlik için Microsoft Defender'dan gelen etiketler düzenlenemez.
* **Güvenlik bilgileri** - Olayları ve etkin uyarıları açın. Uç nokta için Microsoft Defender'a kayıtlı cihazlar da pozlama düzeyi ve risk düzeyi görüntüler.

> [!TIP]
> Pozlama düzeyi cihazın güvenlik önerilerine ne kadar uyumlu olduğuyla ilgili olarak, risk düzeyi etkin uyarıların türleri ve önem düzeyi gibi çeşitli faktörlere göre hesaplanır.

* **Cihaz ayrıntıları** - Cihazı ilk kez görülmek için etki alanı, işletim sistemi, zaman damgası, IP adresleri, kaynaklar. Uç nokta için Microsoft Defender'a kaydolan cihazlar da durum durumunu görüntüler. Identity için Microsoft Defender'a kayıtlı cihazlar, SAM adını ve cihazın ilk oluşturulduğunda geçerli olduğu zaman damgasını görüntüler.
* **Ağ etkinliği** - Cihazın ilk ve son kez ağ üzerinde görülme zamanı zaman damgasıdır.
* **Dizin verileri** (*yalnızca Kimlik için Microsoft Defender'a* kayıtlı cihazlar için) - [UAC](/windows/security/identity-protection/user-account-control/user-account-control-overview) bayrakları, [SPN'ler](/windows/win32/ad/service-principal-names) ve grup üyelikleri.

## <a name="response-actions"></a>Yanıt eylemleri

Yanıt eylemleri, tehditlere karşı savunmanın ve tehditleri çözümlemenin hızlı bir yolunu sağlar.

![Cihaz profili için eylem çubuğunun resmi.](../../media/mtp-device-profile/hybrid-device-long-action-bar.png)

> [!IMPORTANT]
> * [Yanıt eylemleri](/windows/security/threat-protection/microsoft-defender-atp/respond-machine-alerts) , yalnızca cihaz Uç Nokta için Microsoft Defender'a kaydedilir.
> * Uç nokta için Microsoft Defender'a kayıtlı cihazlar, cihazın işletim sistemi ve sürüm numarasına bağlı olarak farklı sayıda yanıt eylemi  gösterebilirsiniz.

Cihaz profili sayfasında kullanılabilen eylemler şunlardır:

* **Etiketleri yönet** - Bu cihaza uygulanmış olan özel etiketleri günceller.
* **Cihazı yalıt** - Cihazı uç nokta için Microsoft Defender'a bağlı tutularak kuruluş ağından yalıtır. İletişim amacıyla, cihaz yalıtılmış Outlook, Teams ve Skype Kurumsal çalıştırma izinlerini seçebilirsiniz.
* **İşlem merkezi** - Gönderilen eylemlerin durumunu görüntüleme. Yalnızca başka bir eylem zaten seçilmişse kullanılabilir.
* **Uygulama yürütmeyi** kısıtla - Microsoft tarafından imzası olmayan uygulamaların çalışmasını önler.
* **Virüsten koruma taraması** çalıştırma - Windows Defender Virüsten Koruma ve hemen bir virüsten koruma taraması çalıştırın. Hızlı tarama veya Tam tarama arasında seçim seçin.
* **Araştırma paketini topla** - Cihaz hakkında bilgi toplar. Araştırma tamamlandığında bunu indirebilirsiniz.
* **Canlı Yanıt Oturumunu Başlat** - Ayrıntılı güvenlik soruşturmaları için cihaza [bir uzak kabuk yükler](/microsoft-365/security/defender-endpoint/live-response).
* **Otomatik araştırma başlatma** - Tehditleri [otomatik olarak araştırın ve düzeltin](../office-365-security/office-365-air.md). Bu sayfadan çalıştıracak otomatik soruşturmaları el ile tetikleye bile, bazı [uyarı ilkeleri](../../compliance/alert-policies.md#default-alert-policies) kendi başına otomatik soruşturmaları tetikler.
* **İşlem merkezi** - O anda çalışan tüm yanıt eylemleri hakkında bilgi görüntüler.

## <a name="tabs-section"></a>Sekmeler bölümü

Cihaz profili sekmeleri, cihazla ilgili güvenlik ayrıntılarına ve uyarı listesini içeren tablolara genel bir bakış için geçiş yapma imkanı sağlar.

Uç nokta için Microsoft Defender'a kayıtlı cihazlar ayrıca bir zaman çizelgesi, güvenlik önerileri listesi, yazılım envanteri, bulunan güvenlik açıklarının listesi ve eksik KB'ler (güvenlik güncelleştirmeleri) özelliğine sahip sekmeler de görüntüler.

### <a name="overview-tab"></a>Genel Bakış sekmesi

Varsayılan sekme Genel **Bakış'tır**. Cihazla ilgili en önemli güvenlik bilgilerine hızlı bir bakış sağlar.

![Cihaz profili için genel bakış sekmesinin görüntüsü.](../../media/mtp-device-profile/hybrid-device-tab-overview.png)

Burada, cihazın etkin uyarılarını ve şu anda oturum açmış olan kullanıcıları hızla göz atabilirsiniz.

Cihaz Uç Nokta için Microsoft Defender'a kayıtlı ise, cihazın risk düzeyini ve güvenlik değerlendirmeleri için kullanılabilir tüm verileri de görebilirsiniz. Güvenlik değerlendirmeleri cihazın etkilenme düzeyini açıklar, güvenlik önerileri sağlar ve etkilenen yazılımları listeler ve güvenlik açıkları keşfeder.

### <a name="alerts-tab"></a>Uyarılar sekmesi

Uyarılar **sekmesi** , cihazda hem Kimlik için Microsoft Defender'dan hem de Uç Nokta için Microsoft Defender'dan yükseltilmiş uyarıların listesini içerir.

![Cihaz profili için uyarılar sekmesinin resmi.](../../media/mtp-device-profile/hybrid-device-tab-alerts.png)

Görüntülenen öğe sayısını ve her öğe için görüntülenecek sütunları özelleştirebilirsiniz. Varsayılan davranış, sayfa başına otuz öğenin listelendir.

Bu sekmede yer alan sütunlar, uyarıyı tetikleyen tehdidin önem derecesiyle ilgili bilgilerin yanı sıra durum, soruşturma durumu ve uyarının kime atandığı hakkında bilgi içerir.

Etkilenen *varlıklar sütunu* , şu anda görüntülemekte olduğunuz cihaza (varlık) ve ağ üzerindeki etkilenen diğer tüm cihazları ifade eder.

Bu listeden bir öğe seçildiğinde, seçili uyarı hakkında daha fazla bilgi içeren açılır öğe açılır.

Bu liste önem derecesine, durumuna veya uyarının kime atandığıyla filtrelenmiş olabilir.

### <a name="timeline-tab"></a>Zaman Çizelgesi sekmesi

Zaman **Çizelgesi** sekmesi, cihazda yükseltilmiş tüm olayların etkileşimli, kronolojik grafiğini içerir. Grafiğin vurgulanan alanında sola veya sağa hareket ettirerek, farklı dönemlere göre olayları görüntüebilirsiniz. Ayrıca, etkileşimli grafiğin ve etkinlik listesinin arasındaki açılan menüden özel bir tarih aralığı da seçebilirsiniz.

Grafiğin altında, seçilen tarih aralığı için bir olay listesi yer almaktadır.

![Cihaz profili için zaman çizelgesi sekmesinin resmi.](../../media/mtp-device-profile/hybrid-device-tab-timeline.png)

Görüntülenen öğe sayısı ve listenin sütunlarının her ikisi de özelleştirilebilir. Varsayılan sütunlar olay zamanı, etkin kullanıcı, eylem türü, varlıklar (süreçler) ve olayla ilgili ek bilgileri listelemektedir.

Bu listeden bir öğe seçerek, etkinliğe katılan üst ve alt işlemleri gösteren Etkinlik varlıkları grafiğini görüntüleyen bir açılır öğe açılır.

Liste, etkinliğin belirli bir türe göre filtrelenmiş olabilir; Örneğin, Kayıt Defteri olayları veya Smart Screen Olayları.

Liste, indirilebilir bir CSV dosyasına da aktarabilirsiniz. Dosya olay sayısıyla sınırlı değildir, ancak dışarı aktarmayı seçebilirsiniz en uzun zaman aralığı yedi gündür.

### <a name="security-recommendations-tab"></a>Güvenlik önerileri sekmesi

Güvenlik **önerileri sekmesi** , cihazı korumak için gerçekleştirebilirsiniz eylemleri listeler. Bu listeden bir öğe seçerek, öneriyi uygulamayla ilgili yönergelere buradan bir açılır öğe açılır.

![Cihaz profili için güvenlik önerileri sekmesinin resmi.](../../media/mtp-device-profile/hybrid-device-tab-security-recs.png)

Önceki sekmelerde olduğu gibi, sayfa başına görüntülenen öğe sayısı ve hangi sütunların görüntüleniyor olduğu özelleştirilebilir.

Varsayılan görünüm, ele alınacak güvenlik açıklarını, ilişkili tehdide, tehditten etkilenen ilgili bileşeni veya yazılımı ve daha birçok ayrıntıyı içeren sütunlar içerir. Öğeler önerinin durumuna göre filtrelenmiş olabilir.

### <a name="software-inventory"></a>Yazılım envanteri

Yazılım **envanteri** sekmesinde, cihazda yüklü yazılım listeleri vardır.

![Cihaz profili için yazılım envanteri sekmesinin görüntüsü.](../../media/mtp-device-profile/hybrid-device-tab-software-inventory.png)

Varsayılan görünümde yazılım satıcısı, yüklü sürüm numarası, bilinen yazılım hatalarının sayısı, tehdit öngörüleri, ürün kodu ve etiketler görüntülenir. Görüntülenen öğe sayısı ve görüntülenecek sütunların her ikisi de özelleştirilebilir.

Bu listeden bir öğe seçildiğinde, seçili yazılımla ilgili daha fazla ayrıntının yanı sıra yazılımın son kez bulunduğu yol ve zaman damgasını içeren bir açılır öğe açılır.

Bu liste ürün koduna göre filtrelenmiş olabilir.

### <a name="discovered-vulnerabilities-tab"></a>Bulunan güvenlik açıkları sekmesi

Bulunan **güvenlik açıkları** sekmesi, cihazı etkileyebilecek Tüm Ortak Güvenlik Açıkları ve Açıkları (CVE) listeler.

![Cihaz profili için güvenlik açıkları sekmesinin görüntüsü.](../../media/mtp-device-profile/hybrid-device-tab-discovered-vulnerabilities.png)

Varsayılan görünümDE, ANLİ'nin önem düzeyi, Ortak Güvenlik Açığı Puanı (CVS), YERİNALA'ya ilişkin yazılım, ATL'nin yayım tarihi, DURUMUNUn en son ne zaman güncelleştirilmesi ve YERKarakARAKLA'ya ilişkin tehditler listelenmektedir.

Önceki sekmelerde olduğu gibi, görüntülenen öğe sayısı ve hangi sütunların görünür olduğu özelleştirilebilir.

Bu listeden bir öğe seçilerek BURMİ'yi açıklayan bir açılır öğe açılır.

### <a name="missing-kbs"></a>Eksik KB'ler

Eksik **KBs sekmesi** , cihaza henüz uygulanmamış olan tüm Microsoft Güncelleştirmelerini listeler. Söz konusu "KB"ler, bu [güncelleştirmeleri açıklayan](https://support.microsoft.com/help/242450/how-to-query-the-microsoft-knowledge-base-by-using-keywords-and-query) Bilgi Bankası makaleleridir; örneğin [KB4551762](https://support.microsoft.com/help/4551762/windows-10-update-kb4551762).

![Cihaz profilinde eksik kbs sekmesinin resmi.](../../media/mtp-device-profile/hybrid-device-tab-missing-kbs.PNG)

Varsayılan görünümde, güncelleştirmeler, işletim sistemi sürümü, etkilenen ürünler, CVE'lere adreslenen KB numarası ve etiketler içeren bülten listelenmiştir.

Sayfa başına görüntülenen öğe sayısı ve görüntülenecek sütunlar özelleştirilebilir.

Bir öğe seçerek güncelleştirmeye bağlantı içeren bir açılır öğe açılır.

## <a name="related-topics"></a>İlgili konular

* [Microsoft 365 Defender genel bakış](microsoft-365-defender.md)
* [E-Microsoft 365 Defender](m365d-enable.md)
* [Canlı yanıtı kullanarak cihazlardaki varlıkları araştırma](../defender-endpoint/live-response.md)
* [Web'de otomatik araştırma ve yanıt (AIR) Office 365](../office-365-security/office-365-air.md)
