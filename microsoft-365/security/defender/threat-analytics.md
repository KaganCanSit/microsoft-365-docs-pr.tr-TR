---
title: Microsoft 365 Defender'de tehdit analizi
ms.reviewer: ''
description: Yeni ortaya çıkan tehditler ve saldırı teknikleri ve bunların nasıl durdurulacağını öğrenin. Kuruluşunuz üzerindeki etkilerini değerlendirin ve kuruluşunuzun dayanıklılığını değerlendirin.
keywords: tehdit analizi, risk değerlendirmesi, Microsoft 365 Defender, M365D, risk azaltma durumu, güvenli yapılandırma, Office 365 için Microsoft Defender, Office 365 için Microsoft Defender  tehdit analizi, MDO tehdit analizi, tümleşik MDE ve MDO tehdit analizi verileri, tehdit analizi veri tümleştirmesi, tümleşik Microsoft 365 Defender tehdit analizi
ms.prod: microsoft-365-enterprise
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: maccruz
author: schmurky
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: article
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 02d7a1e1d80d7891219c9bcf18076b858f4fb1b8
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2022
ms.locfileid: "64663324"
---
# <a name="threat-analytics-in-microsoft-365-defender"></a>Microsoft 365 Defender'de tehdit analizi

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Şunlar için geçerlidir:**

- Microsoft 365 Defender

> Microsoft 365 Defender mı yaşamak istiyorsunuz? Bunu [bir laboratuvar ortamında değerlendirebilir](m365d-evaluation.md?ocid=cx-docs-MTPtriallab) veya [pilot projenizi üretim ortamında çalıştırabilirsiniz](m365d-pilot.md?ocid=cx-evalpilot).
>

[!INCLUDE [Prerelease](../includes/prerelease.md)]

Tehdit analizi, uzman Microsoft güvenlik araştırmacılarının ürün içi tehdit bilgileri çözümümüzdür. Aşağıdakiler gibi yeni tehditlerle karşı karşıyayken güvenlik ekiplerinin mümkün olduğunca verimli olması için tasarlanmıştır:

- Etkin tehdit aktörleri ve kampanyaları
- Popüler ve yeni saldırı teknikleri
- Kritik güvenlik açıkları
- Yaygın saldırı yüzeyleri
- Yaygın kötü amaçlı yazılım

Tehdit analizinin en son tehditleri izlemenize ve durdurmanıza nasıl yardımcı olabileceği hakkında daha fazla bilgi edinmek için bu kısa videoyu izleyin.

>[!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWwJfU]

Tehdit analizine Microsoft 365 güvenlik portalının gezinti çubuğunun sol üst tarafından veya kuruluşunuza yönelik en önemli tehditleri hem etki açısından hem de açığa çıkarma açısından gösteren ayrılmış bir pano kartından erişebilirsiniz.

:::image type="content" source="../../media/threat-analytics/ta_inlandingpage_mtp.png" alt-text="Tehdit analizi giriş sayfası" lightbox="../../media/threat-analytics/ta_inlandingpage_mtp.png":::

Yüksek etki tehditleri en büyük zarar verme potansiyeline sahipken, varlıklarınızın en savunmasız olduğu tehditler yüksek maruz kalma tehditleridir. Etkin veya devam eden kampanyalar hakkında görünürlük elde etmek ve tehdit analizi aracılığıyla ne yapacağınızı bilmek, güvenlik operasyonları ekibinizin bilinçli kararlar almasına yardımcı olabilir.

_Tehdit analizine nereden erişileceği_

Daha karmaşık saldırganlar ve yaygın olarak ortaya çıkan yeni tehditler sayesinde, hızlı bir şekilde şunları yapabilmek çok önemlidir:

- Yeni ortaya çıkan tehditleri belirleme ve buna tepki verme
- Şu anda saldırı altında olup olmadığınız hakkında bilgi edinin
- Tehditlerin varlıklarınız üzerindeki etkisini değerlendirme
- Tehditlere karşı dayanıklılığınızı veya tehditlere maruz kalma durumunuzu gözden geçirin
- Tehditleri durdurmak veya içermek için gerçekleştirebileceğiniz risk azaltma, kurtarma veya önleme eylemlerini belirleme

Her rapor, izlenen bir tehdidin analizini ve bu tehditlere karşı savunma konusunda kapsamlı rehberlik sağlar. Ayrıca ağınızdaki verileri de içerir ve tehdidin etkin olup olmadığını ve geçerli korumalarınız olup olmadığını belirtir.

## <a name="view-the-threat-analytics-dashboard"></a>Tehdit analizi panosunu görüntüleme

Tehdit analizi panosu ([security.microsoft.com/threatanalytics3](https://security.microsoft.com/threatanalytics3)) kuruluşunuzla en ilgili raporları vurgular. Aşağıdaki bölümlerde tehditleri özetler:

- **En son tehditler**— en son yayımlanan veya güncelleştirilen tehdit raporlarının yanı sıra etkin ve çözümlenmiş uyarı sayısını listeler.
- **Yüksek etkili tehditler**— kuruluşunuz üzerinde en yüksek etkiye sahip olan tehditleri listeler. Bu bölümde, en fazla etkin ve çözümlenmiş uyarı sayısına sahip tehditler listelenir.
- **En yüksek maruz kalma**: En yüksek maruz kalma düzeyine sahip tehditler listelenir. bir tehdidin maruz kalma düzeyi iki bilgi parçası kullanılarak hesaplanır: tehditle ilişkili güvenlik açıklarının ne kadar ciddi olduğu ve kuruluşunuzdaki kaç cihazın bu güvenlik açıklarından yararlanabileceği.

Bu tehdidin raporunu görüntülemek için panodan bir tehdit seçin.

:::image type="content" source="../../media/threat-analytics/ta_dashboard_mtp.png" alt-text="Tehdit analizi panosu" lightbox="../../media/threat-analytics/ta_dashboard_mtp.png":::

_Tehdit analizi panosu. Ayrıca, okumak istediğiniz tehdit analizi raporuyla ilgili bir anahtar sözcüğün anahtar sözcüğünü bulmak için Arama alanını da seçebilirsiniz._

## <a name="view-a-threat-analytics-report"></a>Tehdit analizi raporunu görüntüleme

Her tehdit analizi raporu çeşitli bölümlerde bilgi sağlar:

- [**Genel bakış**](#overview-quickly-understand-the-threat-assess-its-impact-and-review-defenses)
- [**Analist raporu**](#analyst-report-get-expert-insight-from-microsoft-security-researchers)
- [**İlgili olaylar**](#related-incidents-view-and-manage-related-incidents)
- [**Etkilenen varlıklar**](#impacted-assets-get-list-of-impacted-devices-and-mailboxes)
- [**Engellenen e-posta girişimleri**](#prevented-email-attempts-view-blocked-or-junked-threat-emails)
- [**Maruz kalma & risk azaltmaları**](#exposure-and-mitigations-review-list-of-mitigations-and-the-status-of-your-devices)

### <a name="overview-quickly-understand-the-threat-assess-its-impact-and-review-defenses"></a>Genel bakış: Tehdidi hızla anlayın, etkisini değerlendirin ve savunmaları gözden geçirin

**Genel Bakış** bölümünde ayrıntılı analist raporunun önizlemesi sağlanır. Ayrıca, tehdidin kuruluşunuz üzerindeki etkisini ve yanlış yapılandırılmış ve eşleşmeyen cihazlar aracılığıyla açığa çıkarmanızı vurgulayan grafikler de sağlar.

:::image type="content" source="../../media/threat-analytics/ta_overview_mtp.png" alt-text="Tehdit analizi raporunun genel bakış bölümü" lightbox="../../media/threat-analytics/../../media/threat-analytics/ta_overview_mtp.png":::

_Tehdit analizi raporunun genel bakış bölümü_

#### <a name="assess-impact-on-your-organization"></a>Kuruluşunuz üzerindeki etkiyi değerlendirme

Her rapor, bir tehdidin kurumsal etkisi hakkında bilgi sağlamak için tasarlanmış grafikler içerir:

- **İlgili olaylar**— aşağıdaki verilerle izlenen tehdidin kuruluşunuz üzerindeki etkisine genel bir bakış sağlar:
  - Etkin uyarı sayısı ve ilişkili oldukları etkin olay sayısı
  - Etkin olayların önem derecesi
- **Zaman içindeki uyarılar— zaman içinde** ilgili **Etkin** ve **Çözümlenmiş** uyarı sayısını gösterir. Çözümlenen uyarı sayısı, kuruluşunuzun bir tehditle ilişkili uyarılara ne kadar hızlı yanıt verdiğini gösterir. İdeal olan grafikte birkaç gün içinde çözümlenen uyarıların gösterilmesi gerekir.
- **Etkilenen varlıklar**— şu anda izlenen tehditle ilişkilendirilmiş en az bir etkin uyarıya sahip olan ayrı cihazların ve e-posta hesaplarının (posta kutuları) sayısını gösterir. Tehdit e-postaları alan posta kutuları için uyarılar tetiklenir. Tehdit e-postalarının teslim edilmesine neden olan geçersiz kılmalar için hem kuruluş hem de kullanıcı düzeyinde ilkeleri gözden geçirin.
- **Engellenen e-posta denemeleri**— son yedi güne ait teslimden önce engellenen veya gereksiz posta klasörüne teslim edilen e-posta sayısını gösterir.

#### <a name="review-security-resilience-and-posture"></a>Güvenlik dayanıklılığını ve duruşu gözden geçirme

Her rapor, kuruluşunuzun belirli bir tehdide karşı ne kadar dayanıklı olduğuna ilişkin bir genel bakış sağlayan grafikler içerir:

- **Güvenli yapılandırma durumu**— yanlış yapılandırılmış güvenlik ayarlarına sahip cihaz sayısını gösterir. Tehdidi azaltmaya yardımcı olmak için önerilen güvenlik ayarlarını uygulayın. _İzlenen tüm_ ayarları uygulamış olan cihazlar **Güvenli** olarak kabul edilir.
- **Güvenlik açığı düzeltme eki uygulama durumu**— güvenlik açığı bulunan cihazların sayısını gösterir. Tehdit tarafından yararlanılan güvenlik açıklarını gidermek için güvenlik güncelleştirmeleri veya düzeltme ekleri uygulayın.

#### <a name="view-reports-per-threat-tags"></a>Tehdit etiketleri başına raporları görüntüleme

Tehdit raporu listesini filtreleyebilir ve belirli bir tehdit etiketine (kategori) veya rapor türüne göre en uygun raporları görüntüleyebilirsiniz.

- **Tehdit etiketleri**; belirli bir tehdit kategorisine göre en ilgili raporları görüntülemenize yardımcı olabilir. Örneğin fidye yazılımıyla ilgili tüm raporlar.
- **Rapor türleri**: Belirli bir rapor türüne göre en uygun raporları görüntülemenize yardımcı olabilir. Örneğin, araçları ve teknikleri kapsayan tüm raporlar.
- **Filtreler**: Tehdit raporu listesini verimli bir şekilde gözden geçirmenize ve görünümü belirli bir tehdit etiketine veya rapor türüne göre filtrelemenize yardımcı olur. Örneğin fidye yazılımı kategorisiyle ilgili tüm tehdit raporlarını veya güvenlik açıklarını kapsayan tehdit raporlarını gözden geçirin.

##### <a name="how-does-it-work"></a>Nasıl çalışır?

Microsoft Tehdit Bilgileri ekibi, her tehdit raporuna tehdit etiketleri ekledi:

- Dört tehdit etiketi kullanıma sunuldu:
  - Fidye Yazılımı
  - Kimlik Avı
  - Güvenlik Açığı
  - Etkinlik grubu
- Tehdit etiketleri, tehdit analizi sayfasının en üstünde gösterilir. Her etiketin altında kullanılabilir rapor sayısı için sayaçlar vardır.

  :::image type="content" source="../../media/threat-analytics/ta-threattags-mtp.png" alt-text="Tehdit etiketleri" lightbox="../../media/threat-analytics/ta-threattags-mtp.png":::

- Liste tehdit etiketlerine göre de sıralanabilir:

  :::image type="content" source="../../media/threat-analytics//ta-taglist-mtp.png" alt-text="Tehdit etiketleri bölümü" lightbox="../../media/threat-analytics//ta-taglist-mtp.png":::

- Filtreler tehdit etiketi ve rapor türü başına kullanılabilir:

  :::image type="content" source="../../media/threat-analytics/ta-threattag-filters-mtp.png" alt-text="Filtreler sayfası" lightbox="../../media/threat-analytics/ta-threattag-filters-mtp.png":::

### <a name="analyst-report-get-expert-insight-from-microsoft-security-researchers"></a>Analist raporu: Microsoft güvenlik araştırmacılarından uzman içgörüleri alma

**Analist raporu** bölümünde, ayrıntılı uzman yazma işlemini okuyun. Çoğu rapor, MITRE ATT&CK çerçevesine eşlenen taktikler ve teknikler, kapsamlı öneri listeleri ve güçlü [tehdit avcılığı](advanced-hunting-overview.md) yönergeleri dahil olmak üzere saldırı zincirlerinin ayrıntılı açıklamalarını sağlar.

[Analist raporu hakkında daha fazla bilgi edinin](threat-analytics-analyst-reports.md)

### <a name="related-incidents-view-and-manage-related-incidents"></a>İlgili olaylar: İlgili olayları görüntüleme ve yönetme

**İlgili olaylar** sekmesi izlenen tehditle ilgili tüm olayların listesini sağlar. Olaylar atayabilir veya her olaya bağlı uyarıları yönetebilirsiniz. 

:::image type="content" source="../../media/threat-analytics/ta_related_incidents_mtp.png" alt-text="Tehdit analizi raporunun ilgili olaylar bölümü" lightbox="../../media/threat-analytics/ta_related_incidents_mtp.png":::

_Tehdit analizi raporunun ilgili olaylar bölümü_

### <a name="impacted-assets-get-list-of-impacted-devices-and-mailboxes"></a>Etkilenen varlıklar: Etkilenen cihazların ve posta kutularının listesini alma

Bir varlık etkin ve çözümlenmemiş bir uyarıdan etkilenmiş olarak kabul edilir. **Etkilenen varlıklar** sekmesi aşağıdaki etkilenen varlık türlerini listeler:

- **Etkilenen cihazlar**; çözümlenmemiş Uç Nokta için Microsoft Defender uyarıları olan uç noktalar. Bu uyarılar genellikle bilinen tehdit göstergelerini ve etkinliklerini gözlemlerken tetiklenir.
- **Etkilenen posta kutuları**: Office 365 için Microsoft Defender uyarılarını tetikleyen e-posta iletilerini alan posta kutuları. Uyarıları tetikleyen iletilerin çoğu genellikle engellenmiş olsa da, kullanıcı veya kuruluş düzeyinde ilkeler filtreleri geçersiz kılabilir.

:::image type="content" source="../../media/threat-analytics/ta_impacted_assets_mtp.png" alt-text="Tehdit analizi raporunun etkilenen varlıklar bölümü" lightbox="../../media/threat-analytics/ta_impacted_assets_mtp.png":::

_Tehdit analizi raporunun etkilenen varlıklar bölümü_

### <a name="prevented-email-attempts-view-blocked-or-junked-threat-emails"></a>Engellenen e-posta girişimleri: Engellenen veya gereksiz tehdit e-postalarını görüntüleme

Office 365 için Microsoft Defender genellikle kötü amaçlı bağlantılar veya ekler de dahil olmak üzere bilinen tehdit göstergelerine sahip e-postaları engeller. Bazı durumlarda, şüpheli içeriği denetleyecek proaktif filtreleme mekanizmaları bunun yerine gereksiz posta klasörüne tehdit e-postaları gönderir. Her iki durumda da, tehditin cihazda kötü amaçlı yazılım kodu başlatma olasılığı azalır.

**Engellenen e-posta denemeleri** sekmesi, teslimden önce engellenen veya Office 365 için Microsoft Defender tarafından gereksiz posta klasörüne gönderilen tüm e-postaları listeler.

:::image type="content" source="../../media/threat-analytics/ta_prevented_email_attempts_mtp.png" alt-text="Tehdit analizi raporunun engellenen e-posta denemeleri bölümü" lightbox="../../media/threat-analytics/ta_prevented_email_attempts_mtp.png":::

_Tehdit analizi raporunun engellenen e-posta denemeleri bölümü_

### <a name="exposure-and-mitigations-review-list-of-mitigations-and-the-status-of-your-devices"></a>Maruz kalma ve risk azaltmalar: Risk azaltmaların listesini ve cihazlarınızın durumunu gözden geçirin

**Açığa Çıkarma & risk azaltmaları** bölümünde, tehditlere karşı kurumsal dayanıklılığınızı artırmanıza yardımcı olabilecek eyleme dönüştürülebilir öneriler listesini gözden geçirin. İzlenen azaltmalar listesi şunları içerir:

- **Güvenlik güncelleştirmeleri**—eklenen cihazlarda bulunan güvenlik açıkları için desteklenen yazılım güvenlik güncelleştirmelerinin dağıtımı
- **Desteklenen güvenlik yapılandırmaları**
  - Bulut tabanlı koruma  
  - İstenmeyebilecek uygulama (PUA) koruması
  - Gerçek zamanlı koruma

Bu bölümdeki azaltma bilgileri[, rapordaki](/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt) çeşitli bağlantılardan ayrıntılı detaya gitme bilgileri de sağlayan Tehdit ve Güvenlik Açığı Yönetimi verilerini içerir.

:::image type="content" source="../../media/threat-analytics/ta_mitigations_mtp.png" alt-text="Güvenli yapılandırma ayrıntılarını gösteren tehdit analizi raporunun risk azaltmalar bölümü" lightbox="../../media/threat-analytics/ta_mitigations_mtp.png":::

:::image type="content" source="../../media/threat-analytics/ta_mitigations_mtp2.png" alt-text="Güvenlik açığı ayrıntılarını gösteren tehdit analizi raporunun risk azaltmalar bölümü" lightbox="../../media/threat-analytics/ta_mitigations_mtp2.png":::

_Tehdit analizi raporunun açığa çıkarma & azaltmalar bölümü_

## <a name="set-up-email-notifications-for-report-updates"></a>Rapor güncelleştirmeleri için e-posta bildirimlerini ayarlama

Tehdit analizi raporlarında size güncelleştirmeler gönderecek e-posta bildirimleri ayarlayabilirsiniz.

Tehdit analizi raporlarına yönelik e-posta bildirimlerini ayarlamak için aşağıdaki adımları uygulayın:

1. Microsoft 365 Defender kenar çubuğunda **Ayarlar** seçin. Ayarlar listesinden **Microsoft 365 Defender'ı** seçin.
 
![Her ikisi de kırmızıyla vurgulanmış "Ayarlar" ve "Microsoft 365 Defender" ekran görüntüsü](../../media/threat-analytics/ta_create_notification_0.png)

2. **E-posta** **bildirimleriDevre** >  analizi'ni seçin ve **+ Bildirim kuralı oluştur** düğmesini seçin. Bir açılır pencere görünür.

!["+ Bildirim kuralı oluştur" seçeneğinin kırmızıyla vurgulandığı ekran görüntüsü](../../media/threat-analytics/ta_create_notification_1.png)

3. Açılır listede listelenen adımları izleyin. İlk olarak, yeni kuralınıza bir ad verin. Açıklama alanı isteğe bağlıdır, ancak bir ad gereklidir. Açıklama alanının altındaki onay kutusunu kullanarak kuralı açıp kapatabilirsiniz.

> [!NOTE]
> Yeni bildirim kuralının ad ve açıklama alanları yalnızca İngilizce harfleri ve sayıları kabul edebilir. Boşluk, kısa çizgi, alt çizgi veya diğer noktalama işaretlerini kabul etmezler.

![Tüm alanların doldurulduğu ve "Kuralı aç" onay kutusunun işaretli olduğu adlandırma ekranının ekran görüntüsü](../../media/threat-analytics/ta_create_notification_2.png)

4. Hangi tür raporlar hakkında bildirim almak istediğinizi seçin. Yeni yayımlanan veya güncelleştirilen tüm raporlar veya yalnızca belirli bir etikete veya türe sahip olan raporlar hakkında güncelleştirilmeyi seçebilirsiniz.

![Fidye yazılımı etiketlerinin seçili olduğu ve türler için açılan menünün açık olduğu bildirim ekranının ekran görüntüsü](../../media/threat-analytics/ta_create_notification_3.png)

5. Bildirim e-postalarını almak için en az bir alıcı ekleyin. Bu ekranı, bir test e-postası göndererek bildirimlerin nasıl alınacağını denetlemek için de kullanabilirsiniz.

![Alıcılar ekranının ekran görüntüsü. Listede 3 alıcı var ve yeşil onay işaretiyle gösterildiği gibi bir test e-postası gönderildi](../../media/threat-analytics/ta_create_notification_4.png)

6. Yeni kuralınızı gözden geçirin. Değiştirmek istediğiniz bir şey varsa, her alt bölümün sonundaki **Düzenle** düğmesini seçin. Gözden geçirme işleminiz tamamlandıktan sonra **Kural oluştur** düğmesini seçin.

![Gözden geçirme ekranının ekran görüntüsü. Düzenleme düğmesi kırmızı renkle vurgulanmış](../../media/threat-analytics/ta_create_notification_5.png)

7. Tebrikler! Yeni kuralınız başarıyla oluşturuldu. İşlemi tamamlamak ve açılır öğeyi kapatmak için **Bitti** düğmesini seçin.

![Kural oluşturma ekranının ekran görüntüsü. Başarıyla oluşturulan bir kural kenar çubuğu boyunca yeşil onay işaretleri ve ekranın ana alanında büyük bir yeşil onay işareti görüntüler](../../media/threat-analytics/ta_create_notification_6.png)

8. Yeni kuralınız artık Tehdit analizi e-posta bildirimleri listesinde görünür.

![Ayarlar ekranındaki e-posta bildirim kuralları listesinin ekran görüntüsü](../../media/threat-analytics/ta_create_notification_7.png)

## <a name="additional-report-details-and-limitations"></a>Ek rapor ayrıntıları ve sınırlamaları

> [!NOTE]
> Birleşik güvenlik deneyiminin bir parçası olarak tehdit analizi artık yalnızca Uç Nokta için Microsoft Defender için değil, Office E5 lisans sahipleri için Microsoft Defender için de kullanılabilir.
>
> Microsoft 365 güvenlik portalını (Microsoft 365 Defender) kullanmıyorsanız, rapor ayrıntılarını (Office veriler için Microsoft Defender olmadan) Microsoft Defender Güvenlik Merkezi portalında da görebilirsiniz ( Uç Nokta için Microsoft Defender).

Tehdit analizi raporlarına erişmek için belirli rollere ve izinlere ihtiyacınız vardır. Ayrıntılar için Microsoft 365 Defender için bkz. [Rol tabanlı erişim denetiminde özel roller](custom-roles.md).

- Uyarıları, olayları veya etkilenen varlık verilerini görüntülemek için, Office veya Uç Nokta için Microsoft Defender uyarı verileri için Microsoft Defender izinlerine veya her ikisine de sahip olmanız gerekir.
- Engellenen e-posta girişimlerini görüntülemek için, Office tehdit avcılığı verileri için Microsoft Defender izinlerine sahip olmanız gerekir.
- Azaltmaları görüntülemek için Uç Nokta için Microsoft Defender'da verileri Tehdit ve Güvenlik Açığı Yönetimi izinleriniz olmalıdır.

Tehdit analizi verilerine bakarken aşağıdaki faktörleri unutmayın:

- Grafikler yalnızca izlenen azaltmaları yansıtır. Grafiklerde gösterilmeyen ek risk azaltmaları için rapora genel bakış'a bakın.
- Risk azaltmalar tam dayanıklılığı garanti etmez. Sağlanan azaltmalar, dayanıklılığı artırmak için gereken mümkün olan en iyi eylemleri yansıtır.
- Cihazlar hizmete veri iletmediyse "kullanılamaz" olarak sayılır.
- Virüsten korumayla ilgili istatistikler Microsoft Defender Virüsten Koruma ayarlarına bağlıdır. Üçüncü taraf virüsten koruma çözümlerine sahip cihazlar "kullanıma sunuldu" olarak görünebilir.

## <a name="related-articles"></a>İlgili makaleler

- [Gelişmiş avcılık ile tehditleri proaktif olarak bulma](advanced-hunting-overview.md)
- [Analist raporu bölümünü anlama](threat-analytics-analyst-reports.md)
- [Güvenlik zayıflıklarını ve açığa çıkarmaları değerlendirme ve çözme](/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt)
