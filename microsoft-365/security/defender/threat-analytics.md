---
title: Yeni Microsoft 365 Defender'de tehdit Microsoft 365 Defender
ms.reviewer: ''
description: Yeni ortaya çıkan tehdit ve saldırı tekniklerini ve bunları nasıl durduracaklarını öğrenin. Organizasyon üzerindeki etkisini değerlendirin ve organizasyona karşı etkilerinızı değerlendirin.
keywords: tehdit analizi, risk değerlendirme, Microsoft 365 Defender, M365D, azaltma durumu, güvenli yapılandırma, Office 365 için Microsoft Defender, Office 365 tehdit analizi için Microsoft Defender, MDO tehdit analizi, tümleşik MDE ve MDO tehdit analizi verileri, tehdit analizi veri tümleştirmesi, tümleşik Microsoft 365 Defender analizini geri edinin
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
ms.openlocfilehash: 5cb9f0db07ad29618e0dc9d053f4904a70ca52f6
ms.sourcegitcommit: 2697938d2d4fec523b501c5e7b0b8ec8f34e59b0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2022
ms.locfileid: "63450170"
---
# <a name="threat-analytics-in-microsoft-365-defender"></a>Yeni Microsoft 365 Defender'de tehdit Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**

- Microsoft 365 Defender

> Bu deneyimi Microsoft 365 Defender? Bunu bir [laboratuvar ortamında değerlendirin veya](m365d-evaluation.md?ocid=cx-docs-MTPtriallab) [üretimde pilot projenizi çalıştırın](m365d-pilot.md?ocid=cx-evalpilot).
>

[!INCLUDE [Prerelease](../includes/prerelease.md)]

Tehdit analizi, uzman Microsoft güvenlik araştırmacısı tarafından alınan ürün için tehdit çözümüdür. Güvenlik ekiplerinin mümkün olduğunca verimli olmasına yardımcı olurken, ortaya çıkan şu tehditlere karşı da yardımcı olmak üzere tasarlanmıştır:

- Etkin tehdit tehditlerini ve onların kampanyalarını tehdit ediyor
- Popüler ve yeni saldırı teknikleri
- Kritik güvenlik açıkları
- Yaygın saldırı yüzeyleri
- Yaygın kötü amaçlı yazılım

Tehdit analizinin en son tehditleri izleme ve bunları durdurma konusunda nasıl yardımcı olduğu hakkında daha fazla bilgi edinmek için bu kısa videoyu izleyin.

>[!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWwJfU]

Tehdit analizine, Microsoft 365 güvenlik portalının gezinti çubuğunun sol üst tarafından veya hem etki hem de etkilenme açısından, kuruluşa yönelik en önemli tehditleri gösteren adanmış bir pano kartından erişebilirsiniz.

![Tehdit analiz panosunun resmi.](../../media/threat-analytics/ta_inlandingpage_mtp.png)

Yüksek etki tehditlerine zarar vermek için en büyük potansiyel tehdit vardır, ancak tehditlere karşı yüksek saldırılar varlıklarınızı en korumasız tehditlere neden olur. Etkin veya devam eden kampanyalar hakkında görünürlük elde etmek ve tehdit analizleri aracılığıyla ne olacağını bilmek, güvenlik işlemleri ekibinizi bilgili kararlar alma konusunda yardımcı olabilir.

_Tehdit analizine erişim nerede olur?_

Sık sık ve yaygın olarak ortaya çıkan daha gelişmiş rakipler ve yeni tehditlerle, hızla devam etmek kritik öneme sahip:

- Ortaya çıkan tehditleri belirleme ve buna tepki verme
- Şu anda saldırıda olup o anda değilken bilgi
- Varlıklarınız için tehdidin etkisini değerlendirme
- Tehditlere karşı olan belki de tehditlere karşı olan korumanızı gözden geçirme
- Tehditlere karşı durarak veya onları içermek için gerçekleştir atabilirsiniz azaltma, kurtarma veya önleme eylemlerini belirleme

Her rapor, bu tehdite karşı savunma konusunda izlemeli bir tehdidin ve kapsamlı bir kılavuzun analizlerini sağlar. Ayrıca, ağınıza gelen, tehdidin etkin olup olmadığını ve geçerli korumalara sahip olup olmadığınızı gösteren verileri de bir almaktadır.

## <a name="view-the-threat-analytics-dashboard"></a>Tehdit analiz panosuyu görüntüleme

Threat Analytics panosu ([security.microsoft.com/threatanalytics3](https://security.microsoft.com/threatanalytics3)), organizasyonunıza en uygun raporları vurgular. Aşağıdaki bölümlerdeki tehditleri özetler:

- **En son** tehdit: En son yayımlanan veya güncelleştirilmiş tehdit raporlarını, ayrıca etkin ve çözümlenmiş uyarıların sayısını listeler.
- **Çok etkili tehditlerin** olduğu, organizasyonlarınızı en çok etkileyen tehditleri listeler. Bu bölümde, öncelikle en yüksek etkin ve çözümlenmiş uyarı sayısına sahip tehdit listeleri listelenir.
- **En yüksek pozlama**; öncelikle en yüksek pozlama düzeyine sahip tehditleri listeler. bir tehdidin maruz kalma düzeyi, iki bilgi kullanılarak hesaplanır: tehditle ilişkilendirilmiş güvenlik açıklarının ne kadar ciddi olduğu ve bu güvenlik açıkları tarafından organizasyonda kaç cihaz sömürül olabilir.

Bu tehdidin raporunu görüntülemek için panodan bir tehdit seçin.

![Tehdit analizi panosunun ekran görüntüsü.](../../media/threat-analytics/ta_dashboard_mtp.png)

_Threat analytics panosu. Ayrıca, okumak istediğiniz tehdit çözümleme raporuyla ilgili bir anahtar sözcükte Arama alanını da seçebilirsiniz._

## <a name="view-a-threat-analytics-report"></a>Tehdit analizi raporunu görüntüleme

Her tehdit çözümleme raporu birkaç bölümde bilgi sağlar:

- [**Genel bakış**](#overview-quickly-understand-the-threat-assess-its-impact-and-review-defenses)
- [**Analist raporu**](#analyst-report-get-expert-insight-from-microsoft-security-researchers)
- [**İlgili olaylar**](#related-incidents-view-and-manage-related-incidents)
- [**Etkide olan varlıklar**](#impacted-assets-get-list-of-impacted-devices-and-mailboxes)
- [**Engelli e-posta girişimleri**](#prevented-email-attempts-view-blocked-or-junked-threat-emails)
- [**Pozlama & azaltmaları**](#exposure-and-mitigations-review-list-of-mitigations-and-the-status-of-your-devices)

### <a name="overview-quickly-understand-the-threat-assess-its-impact-and-review-defenses"></a>Genel bakış: Tehdidi hızlı bir şekilde anlıyoruz, etkisini değerlendirin ve savunmayı gözden geçirme

Genel **Bakış** bölümü, ayrıntılı analist raporunun bir önizlemesini sağlar. Ayrıca, organizasyonunız için tehdidin etkisini vurgulayan grafikler, hatalı ve eşleşmeyen cihazlarla etkilenmenizi de sağlar.

![Tehdit analizi raporunun genel bakış bölümünün görüntüsü.](../../media/threat-analytics/ta_overview_mtp.png)

_Tehdit analizi raporunun genel bakış bölümü_

#### <a name="assess-impact-on-your-organization"></a>Organizasyonu üzerinde etkisini değerlendirme

Her rapor, bir tehdidin kurumsal etkisi hakkında bilgi sağlamak için tasarlanmış grafikler içerir:

- **İlgili olaylar**: Aşağıdaki verilerle, izlenilen tehdidin organizasyonu üzerindeki etkisiyle ilgili genel bir bakış sağlar:
  - Etkin uyarı sayısı ve ilişkilendirilen etkin olay sayısı
  - Etkin olayları önem derecesi
- **Zamanla yapılan uyarılar**— İlgili Etkin ve Zaman **içinde çözülen** uyarıların sayısını gösterir. Çözülen uyarıların sayısı, kuruluşun bir tehditle ilişkilendirilmiş uyarılara ne kadar hızlı yanıt veremediklerine işaret ediyor. İdeal olan, grafiğin birkaç gün içinde çözülen uyarıları göstermesidir.
- **Etkileyen varlıklar—** şu anda izleme tehdidiyle ilişkili en az bir etkin uyarıya sahip olan ayrı cihazların ve e-posta hesaplarının (posta kutuları) sayısını gösterir. Tehdit e-postaları alan posta kutuları için uyarılar tetiklenir. Tehdit e-postalarının teslimi sırasında neden olan geçersiz kılmalar için hem kuruluş hem de kullanıcı düzeyi ilkeleri gözden geçirebilirsiniz.
- **Engellenmiş e-posta** denemeleri— son yedi gündeki e-posta sayısını gösterir. Bu e-posta teslim veya gereksiz posta klasörüne teslim edilmedi.

#### <a name="review-security-resilience-and-posture"></a>Güvenlik inalisini ve şuurlarını gözden geçirme

Her raporda, kuruma yönelik olarak verilen bir tehdite karşı ne kadar uygun olduğuyla ilgili genel bir bakış sağlayan grafikler yer almaktadır:

- **Güvenli yapılandırma durumu**: Hatalı yapılandırılmış güvenlik ayarlarına sahip cihazların sayısını gösterir. Tehdidi azaltmak için önerilen güvenlik ayarlarını uygulama. Tüm izleme **ayarlarını** uyguladıkları cihazlar _Güvenli_ olarak kabul edilir.
- **Güvenlik açığı düzeltme eki durumu**— korumasız cihazların sayısını gösterir. Tehdit tarafından yararlanan güvenlik açıkları için güvenlik güncelleştirmeleri veya düzeltme ekleri uygulayabilirsiniz.

#### <a name="view-reports-per-threat-tags"></a>Tehdit etiketleri başına raporları görüntüleme

Tehdit raporu listesini filtrenin ve belirli bir tehdit etiketine (kategori) veya rapor türüne göre en uygun raporları görüntüebilirsiniz.

- **Tehdit etiketleri**— belirli bir tehdit kategorisine göre en uygun raporları görüntülemede size yardımcı olabilir. Örneğin, fidye yazılımıyla ilgili tüm raporlar.
- **Rapor türleri**— belirli bir rapor türüne göre en uygun raporları görüntülemede size yardımcı olabilir. Örneğin, araçları ve teknikleri kapsaan tüm raporlar.
- **Filtreler**— tehdit raporu listesini etkili bir şekilde gözden geçirme ve belirli bir tehdit etiketi veya rapor türüne göre görünümü filtreleme konusunda size yardımcı olur. Örneğin, fidye yazılımı kategorisiyle ilgili tüm tehdit raporlarını veya güvenlik açıklarını kapsaan tehdit raporlarını gözden geçirebilirsiniz.

##### <a name="how-does-it-work"></a>Nasıl çalışır?

Microsoft Tehdit İstihbaratı ekibi her tehdit raporuna tehdit etiketleri ekledi:

- Dört tehdit etiketi artık kullanılabilir:
  - Fidye yazılımı
  - Kimlik avı
  - Güvenlik Açığı
  - Etkinlik grubu
- Tehdit etiketleri, tehdit çözümleme sayfasının en üstünde görüntülenir. Her etiketin altında kullanılabilir rapor sayısı için sayaçlar vardır.

  ![tehdit etiketleri.](../../media/threat-analytics/ta-threattags-mtp.png)

- Liste ayrıca tehdit etiketlerine göre de sıralandırabilirsiniz:

  ![listeler.](../../media/threat-analytics//ta-taglist-mtp.png)

- Filtreler her tehdit etiketi ve rapor türü için kullanılabilir:

  ![filtrelerini seçin.](../../media/threat-analytics/ta-threattag-filters-mtp.png)

### <a name="analyst-report-get-expert-insight-from-microsoft-security-researchers"></a>Analist raporu: Microsoft güvenlik araştırmacısı'nın uzman içgörülerini alın

Analist **raporu bölümünde** , ayrıntılı uzman yazılarını okuyun. Raporların çoğu, MITRE ATT&CK çerçevesine eşlenen taktikler ve teknikler, çok kapsamlı öneri listeleri ve güçlü tehdit arama kılavuzu dahil olmak üzere saldırı zincirleri hakkında [ayrıntılı açıklamalar sağlar](advanced-hunting-overview.md) .

[Analist raporu hakkında daha fazla bilgi](threat-analytics-analyst-reports.md)

### <a name="related-incidents-view-and-manage-related-incidents"></a>İlgili olaylar: İlgili olayları görüntüleme ve yönetme

İlgili **olaylar sekmesi** , izlenilen tehditle ilgili tüm olayların listesini sağlar. Her olayla bağlantılı olayları atayanın veya uyarıları yönetin.

![Tehdit analizi raporunun ilgili olaylar bölümünün görüntüsü.](../../media/threat-analytics/ta_related_incidents_mtp.png)

_Tehdit analizi raporunun ilgili olaylar bölümü_

### <a name="impacted-assets-get-list-of-impacted-devices-and-mailboxes"></a>Etkiulan varlıklar: Etki etkisi olan cihazların ve posta kutularının listesini alın

Etkin, çözümlenmemiş bir uyarıdan etkilenmesi, bir varlığın etkilendiği kabul edilir. **Etkiulan varlıklar** sekmesi, aşağıdaki etkiyi olan varlık türlerini listeler:

- **Etkilenen** cihazlar: Uç nokta uyarıları için çözümlenmemiş Microsoft Defender uç noktaları. Bu uyarılar genellikle bilinen tehdit göstergeleri ve etkinliklerine karşı bir durumla karşı karşıya olur.
- **Etkilenen posta kutuları**: Posta kutuları, e-posta iletileri almış olan ve bu iletiler için Microsoft Defender'ı tetikleyen Office 365 kutusudur. Uyarıları tetikleyen iletilerin çoğu normalde engellenmiş durumdayken, kullanıcı veya kuruluş düzeyi ilkeleri filtreleri geçersiz kılar.

![Tehdit analizi raporunun etkilenen varlıklar bölümünün resmi.](../../media/threat-analytics/ta_impacted_assets_mtp.png)

_Tehdit analizi raporunun etkili varlıklar bölümü_

### <a name="prevented-email-attempts-view-blocked-or-junked-threat-emails"></a>Engellenmiş e-posta girişimleri: Engellenen veya gereksiz tehdit e-postalarını görüntüleme

Microsoft Defender for Office 365 typically blocks email with known threat indicators, including malicious links or attachments. Bazı durumlarda, şüpheli içeriği denetlemeye yönelik proaktif filtreleme mekanizmaları, tehdit e-postalarını gereksiz posta klasörüne gönderir. Her iki durumda da, cihazda kötü amaçlı yazılım kodunu başlatma tehdidinin olasılığı azaltıldı.

**Engellenmiş e-posta** girişimleri sekmesi, teslimden önce engellenen veya Microsoft Defender tarafından gereksiz posta klasörüne gönderilen tüm e-postaları Office 365.

![Tehdit çözümleme raporunun engellenebilir e-posta girişimleri bölümünün resmi.](../../media/threat-analytics/ta_prevented_email_attempts_mtp.png)

_Tehdit analizi raporunun engelli e-posta girişimleri bölümü_

### <a name="exposure-and-mitigations-review-list-of-mitigations-and-the-status-of-your-devices"></a>Pozlama ve risk azaltma: Risk azaltma listesini ve cihazlarınızı durumunu gözden geçirme

Saldırı **ve risk &** bölümünde, kurumsal olarak tehditlere karşı daha fazla güvenlik ayrıcalığınızı artırmanıza yardımcı olacak işlem önerilerinin listesini gözden geçirebilirsiniz. İzli risk azaltmalar listesi şunları içerir:

- **Güvenlik güncelleştirmeleri**—yerleşik cihazlarda bulunan güvenlik açıkları için desteklenen yazılım güvenlik güncelleştirmeleri dağıtımı
- **Desteklenen güvenlik yapılandırmaları**
  - Bulut teslimi koruma  
  - İstenmeyen olabilecek uygulama (PUA) koruması
  - Gerçek zamanlı koruma

Bu bölümdeki azaltma bilgileri, rapor Tehdit ve Güvenlik Açığı Yönetimi çeşitli bağlantılarından [](/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt)ayrıntılı detaya gitme bilgileri de sağlayan veri bağlantılarını içerir.

![Güvenli yapılandırma ayrıntılarını gösteren bir tehdit analizi raporunun risk azaltma bölümünün görüntüsü.](../../media/threat-analytics/ta_mitigations_mtp.png)

![Bir tehdit analizi raporunun güvenlik açığı ayrıntılarını gösteren risk azaltma bölümünün resmi.](../../media/threat-analytics/ta_mitigations_mtp2.png)

_Tehdit & risk azaltmaları bölümü_

## <a name="set-up-email-notifications-for-report-updates"></a>Rapor güncelleştirmeleri için e-posta bildirimlerini ayarlama

Tehdit analizi raporlarıyla ilgili güncelleştirmeler gönderecek e-posta bildirimleri kurabilirsiniz.

Tehdit analizi raporlarına yönelik e-posta bildirimlerini ayarlamak için aşağıdaki adımları izleyin:

1. Kenar **Ayarlar** kenar Microsoft 365 Defender seçin. Ayarlar **Microsoft 365 Defender** Seçenekler'i seçin.
 
![Hem "Ayarlar" hem de "Microsoft 365 Defender" kırmızıyla vurgulanmış ekran görüntüsü](../../media/threat-analytics/ta_create_notification_0.png)

2. **E-posta bildirimleriThreat** >  **analiz'i** seçin ve + Bildirim kuralı **oluştur düğmesini seçin**. Bir uçarak çıkış görüntülenir.

!["+ Bildirim kuralı oluştur" ifadesinin kırmızı renkle vurgulanmış olduğu ekran görüntüsü](../../media/threat-analytics/ta_create_notification_1.png)

3. Uçarak çıkışta listelenen adımları izleyin. İlk olarak, yeni kuralınıza bir ad girin. Açıklama alanı isteğe bağlıdır, ancak bir ad gereklidir. Açıklama alanı altındaki onay kutusunu kullanarak kuralı açıp kapatebilirsiniz.

> [!NOTE]
> Yeni bildirim kuralının ad ve açıklama alanları yalnızca İngilizce harf ve sayıları kabul eder. Boşluk, tire, alt çizgi veya diğer noktalama işaretlerini kabul etmezler.

![Tüm alanlar doldurulmuş ve "Kuralı aç" onay kutusunun işaretli olduğu adlandırma ekranı ekran görüntüsü](../../media/threat-analytics/ta_create_notification_2.png)

4. Hangi tür raporlar hakkında bilgi almak istediğiniz seçin. Yeni yayımlanan veya güncelleştirilen tüm raporlar hakkında güncelleştirilmesi ya da yalnızca belirli bir etiketi veya türü olan raporların güncelleştirilmesi arasında seçim seçebilirsiniz.

![Fidye yazılımı etiketlerinin seçili olduğu bildirim ekranı ve türler için açılan menü açık ekran görüntüsü](../../media/threat-analytics/ta_create_notification_3.png)

5. Bildirim e-postalarını almak için en az bir alıcı ekleyin. Bir test e-postası göndererek bildirimlerin nasıl alın olacağını kontrol etmek için de bu ekranı kullanabilirsiniz.

![Alıcılar ekranı ekran görüntüsü. Listede 3 alıcı var ve yeşil onay işaretiyle belirtilen bir test e-postası gönderilmiştir](../../media/threat-analytics/ta_create_notification_4.png)

6. Yeni kuralınızı gözden geçirme. Değiştirmek istediğiniz bir şey varsa, **her alt bölüm** sonundaki Düzenle düğmesini seçin. Gözden geçirmeniz tamamlandıktan sonra Kural **oluştur düğmesini** seçin.

![Gözden geçir ekranı ekran görüntüsü. Kırmızı renkle vurgulanmış düzenleme düğmesi](../../media/threat-analytics/ta_create_notification_5.png)

7. Tebrikler! Yeni kuralınız başarıyla oluşturuldu. Işlemi **tamamlamak ve** uçmayı kapatmak için Bitti düğmesini seçin.

![Oluşturulan kuralın ekran görüntüsü. Başarıyla oluşturulan bir kural kenar çubuğu boyunca yeşil onay işaretleri ve ekranın ana alanında da büyük yeşil bir denetim görüntüler](../../media/threat-analytics/ta_create_notification_6.png)

8. Yeni kuralınız artık Tehdit analizi e-posta bildirimleri listesinde görünür.

![Ayarlar ekranında e-posta bildirimi kuralları listesinin ekran görüntüsü](../../media/threat-analytics/ta_create_notification_7.png)

## <a name="additional-report-details-and-limitations"></a>Ek rapor ayrıntıları ve sınırlamaları

> [!NOTE]
> Birleştirilmiş güvenlik deneyiminin bir parçası olarak tehdit çözümlemeleri, artık yalnızca Uç Nokta için Microsoft Defender'da değil, aynı zamanda Microsoft Defender for Office E5 lisans sahipleri için de sağlanmaktadır.
>
> Microsoft 365 güvenlik portalını (Microsoft 365 Defender) kullanmayacaksanız, rapor ayrıntılarını da (Office verileri için Microsoft Defender olmadan) Microsoft Defender Güvenlik Merkezi portalında (Uç nokta için Microsoft Defender) de bulabilirsiniz.

Tehdit analizi raporlarına erişmek için belirli rollere ve izinlere ihtiyacınız vardır. Ayrıntılar [için bkz. Rol tabanlı erişim denetiminde Microsoft 365 Defender](custom-roles.md) roller.

- Uyarıları, olayları veya etkileyen varlık verilerini görüntülemek için, Office için Microsoft Defender veya Uç nokta uyarı verileri için Microsoft Defender veya her ikisini birden kabul etmek için izinlere sahip olmak gerekir.
- Engelli e-posta girişimlerini görüntülemek için, bu denemeler için Microsoft Defender Office izinlere sahip olmak gerekir.
- Risk azaltmaları görüntülemek için, Uç Nokta için Microsoft Defender'Tehdit ve Güvenlik Açığı Yönetimi verileri görüntüleme izinlerine sahip olmak gerekir.

Tehdit çözümleme verilerine bakarak şu faktörleri unutmayın:

- Grafikler yalnızca izlenen risk azaltmalarını yansıttır. Grafiklerde gösterülen ek risk azaltmaları için rapora genel bakış bilgilerine bakın.
- Azaltmalar tam bir teminat garanti etmez. Sağlanan azaltmalar, performansı geliştirmek için gereken en iyi olası eylemleri yansıttır.
- Cihazlar, hizmete veri aktarmışsa "kullanılamaz" olarak sayılır.
- Virüsten korumayla ilgili istatistikler veri Microsoft Defender Virüsten Koruma temel Microsoft Defender Virüsten Koruma temel almaktadır. Üçüncü taraf virüsten koruma çözümlerine sahip cihazlar "açık" olarak görünebilir.

## <a name="related-articles"></a>İlgili makaleler

- [Gelişmiş avla tehditlere karşı önceden bulma](advanced-hunting-overview.md)
- [Analist raporu bölümünü anlama](threat-analytics-analyst-reports.md)
- [Güvenlik açıklarını ve pozlama durumlarını değerlendirin ve çözüm bulun](/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt)
